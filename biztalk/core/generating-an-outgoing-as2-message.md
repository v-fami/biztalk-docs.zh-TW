---
title: 產生外寄 AS2 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 288c8101-9a96-4f98-ae18-df43c7cdb3a0
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90a0b1e37e96086de7d8901b61afa8dea859a388
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246542"
---
# <a name="generating-an-outgoing-as2-message"></a>產生外寄 AS2 訊息
AS2EDISend 和 AS2Send 傳送管線會產生外寄訊息，如下所述。 每個管線會使用的單向協議索引標籤中的屬性**協議屬性**來產生外寄 AS2 訊息的對話方塊。  
  
## <a name="agreement-destination-and-messageid-determination"></a>協議、 目的地和 MessageID 判斷  
 AS2 傳送管線會判斷傳送 AS2 訊息時要使用的協議和目的地，如下所述：  
  
-   為了判斷處理外寄訊息時使用的協議，AS2 編碼器會嘗試比對訊息中的 AS2-To 屬性與合作對象商務設定檔的 AS2Identity，或是比對訂閱訊息的傳送埠與協議的相關聯傳送埠。 如需這個程序的詳細資訊，請參閱[外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)。  
  
-   為判斷訊息的目的地，動態傳送埠中的傳送管線會使用 OutboundTransportLocation 屬性，該屬性必須由後端應用程式撰寫或升級至內容，動態傳送埠才能運作。 靜態傳送管線中的傳送管線將根據 AS2 協議屬性中的 AS2-From 屬性，以及商務設定檔屬性的識別判斷目的地。  
  
-   AS2 編碼器必須設定外寄 AS2 訊息的 MessageId 標頭。 傳送管線會根據 `EdiIntAS.MessageId` 內容屬性或 `HTTP.UserHttpHeaders` 內容屬性判斷 MessageId。 如果同時設定了這兩個內容屬性，則編碼器會使用 `HTTP.UserHttpHeaders` 內容屬性的值。 如果兩個屬性都未設定，則傳送管線會自動產生 MessageID 的值。  
  
## <a name="outgoing-message-processing"></a>外寄訊息處理  
 AS2 傳送管線處理外寄 AS2 訊息時採取的步驟如下所示：  
  
-   如果已在協議屬性中啟用 AS2 訊息的不可否認性，就以原生格式複製訊息並將複本儲存在不可否認性資料庫中。  
  
-   AS2 編碼器會在 `HTTP.UserHttpHeaders` 內容屬性中建置 HTTP (和 AS2) 標頭。 如需這個程序的詳細資訊，請參閱[傳送端處理透過 AS2 外寄 EDI 訊息](../core/send-side-processing-of-an-outgoing-edi-message-over-as2.md)。  
  
-   將 `HTTP.UserHttpHeaders` 寫入內容。  
  
-   壓縮外寄訊息 (如已啟用)。  
  
-   執行 MIME 處理，包括加密訊息 (如果啟用 在**訊息應該加密**協議屬性) 以及套用數位簽章 (如果啟用 在**訊息應該簽署的**協議屬性)。 AS2Send 管線會根據協議設定，使用 SHA1 或 MD5 來套用簽章。  
  
-   如果已在協議屬性中啟用傳輸檔案名稱，便建立包含指定值的 Content-Disposition MIME 標頭。  
  
-   加密訊息的複本 （電傳格式），並將複本儲存在不可否認性資料庫中，如果在啟用**為輸出的編碼 AS2 訊息啟用 NRR**協議屬性中。  
  
-   如果必須使用 MDN，則計算 MIC 值並將它儲存到資料存放區。  
  
-   將訊息傳遞至 HTTP 配接器，該配接器會從 UserHTTPHeaders 內容屬性將標頭寫入至外寄 AS2 訊息。  
  
-   如果需要可靠的傳訊，就會重新傳送訊息，直到接收 MDN 為止。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 傳送 AS2 訊息的方式](../core/how-biztalk-server-sends-as2-messages.md)   
 [AS2 傳送元件](../core/as2-send-components.md)