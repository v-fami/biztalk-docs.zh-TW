---
title: 處理內送 MDN |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd78e84c-4989-47e4-b95b-80582084ddec
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e599e9ebbc7a05a466cc047d891699222c2dabac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265262"
---
# <a name="processing-an-incoming-mdn"></a>處理內送 MDN
AS2 接收管線 （AS2EDIReceive 和 AS2Receive） 處理內送 MDN 做為 AS2 訊息接收者的合作對象根據協議屬性。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]自動將 MDN 與外寄 AS2 訊息相互關聯。  
  
 以下是每個管線所執行的步驟：  
  
-   藉由比對 AS2 判斷傳送合作對象-訊息的 AS2 標頭的值與 AS2 的值從-從清單中**識別碼**頁面的單向 AS2 協議索引標籤的**協議屬性**  對話方塊。 如果找不到符合項，管線就會中止處理並引發例外狀況。  
  
-   將下列 AS2 屬性升級至內容：  
  
    -   IsAS2FailedMessage  
  
    -   DispositionType  
  
    -   GenerateAsynchronous200OKOnly  
  
    -   IsAS2MdnResponseMessage  
  
    -   IsAS2MessageSigned  
  
    -   OriginalMessageId  
  
    -   ReceivedContentMic  
  
    -   DispositionMode  
  
    -   MessageId  
  
-   將訊息的所有 HTTP 標頭設定成 InboundHttpHeaders 屬性，並將其升級至訊息的內容。  
  
-   如果已在單向 AS2 協議屬性中啟用，則產生 MDN 的複本 (電傳格式)，並將此複本儲存在不可否認性資料庫中 (BizTalkDTADb 資料庫的 EdiMessageContent 資料表)。  
  
-   在已簽署 MDN 的情況下，執行 MIME 處理，其中包括驗證簽章。  
  
-   比較 MDN 中的 MIC (訊息完整性檢查)，以及當 AS2Send 管線傳送出原始訊息時所計算出之資料存放區中的 MIC (如果適用)。 如需詳細資訊，請參閱[MDN 訊息](../core/mdn-messages.md)。  
  
-   在不可否認性的資料庫中建立相互關聯項目。  
  
-   刪除 MDN，除非**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**屬性設定**傳送者 MDN 設定**頁面的單向 AS2 協議索引標籤的**協議屬性** 對話方塊。  
  
-   如果**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**屬性設定**傳送者 MDN 設定**頁面的單向 AS2 協議索引標籤的**協議屬性**對話方塊中，接收管線將 MDN 路由至 AS2 解碼器當做通過訊息的電傳格式，並放入 MessageBox。 電傳格式的 MDN 包含所有的 HTTP 標頭。  
  
    > [!NOTE]
    >  您可以將傳送埠設定成訂閱已放入 MessageBox 中的已接收 MDN。 若要訂閱接收的 MDN，請將傳送埠篩選條件設定為 `IsAS2MdnResponseMessage==True`。  
  
    > [!NOTE]
    >  如果您使用 AS2EdiReceive 管線來處理收到的 MDN，您無法將 MDN 路由至 MessageBox 設定**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**屬性**傳送者 MDN設定**頁面的單向 AS2 協議索引標籤的**協議屬性** 對話方塊。 嘗試這樣做會造成 EDI 錯誤，因為這樣 MDN 會傳遞至 EDI 解碼器，但是該解碼器無法處理 MDN。 如果 MDN 沒有傳送至 MessageBox，AS2Decoder 便會使用 MDN，這樣 MDN 便不會傳遞至 EDI 解碼器。  
  
## <a name="message-integrity-check"></a>訊息完整性檢查  
 訊息完整性檢查 (MIC) 是用來確認 MDN 有和原始傳送的訊息相互關聯。 AS2Send 傳送管線會在產生原始 AS2 訊息時依據訊息內容計算 MIC，並將 MIC 儲存在資料存放區中。 當需要 MDN 時，原始訊息的接收者會產生 MIC 並將它加入至 MDN 中。 當 AS2MdnReceive 接收管線接收 MDN 時，如果有要求簽署的 MDN，這項檢查就會比較 MDN 中的 MIC 與資料存放區中的 MIC。  
  
 MDN 中的 MIC 與資料存放區中 MIC 若是不相符，就表示在傳輸期間或訊息由接收合作對象接收時有發生錯誤。 以下是發生這種失敗時所報告的值：  
  
-   AS2DispositionType：失敗  
  
-   AS2DispositionModifierExtensionType：錯誤  
  
-   AS2DispositionModifierExtensionDescription：完整性檢查失敗  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)   
 [MDN 訊息](../core/mdn-messages.md)