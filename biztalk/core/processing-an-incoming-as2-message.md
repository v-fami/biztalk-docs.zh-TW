---
title: 處理內送 AS2 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 998ff334-71e2-4686-b2b7-44940a0ebed1
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b221ea3697180c27e347250570b0e96105a50f08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22266390"
---
# <a name="processing-an-incoming-as2-message"></a>處理內送 AS2 訊息
AS2 接收管線會透過 AS2 處理內送訊息。 AS2EdiReceive 接收管線會使用 EDI 解譯器處理 EDI 編碼的訊息。 AS2Receive 接收管線會使用 AS2 解譯器處理非 EDI 編碼的訊息。 這兩種管線會處理 AS2 訊息的內容並以不同的方式產生 MDN，然而兩種接收管線都是使用 AS2 解碼器處理 AS2 訊息。  
  
 AS2EdiReceivePipeline 處理含 EDI 內容的 AS2 訊息時，會先完成所接收訊息的 AS2 處理再執行 EDI 處理。 管線產生 AS2 訊息之 EDI 內容的 EDI 通知時，必須以非同步方式傳回 EDI 通知，因為 AS2 回應已關閉連線。  
  
## <a name="the-receive-port"></a>接收埠  
 HTTP 接收埠是用於接收含 EDI 或非 EDI 內容的 AS2 訊息。 如果 MDN 必須以同步方式傳回，接收埠就必須是要求-回應連接埠。  
  
 MDN 可以用同步或非同步的方式傳回。 這取決於配置通知至標頭的 AS2 訊息，除非**對驗證與 MDN 使用協議設定，而非訊息標頭**的單向AS2協議索引標籤中選取屬性**協議屬性** 對話方塊。 如果選取屬性，則傳回 MDN 的方式取決於**要求非同步 MDN**屬性**傳送者 MDN 設定**頁面的單向 AS2 協議索引標籤的**協議屬性** 對話方塊。 如需詳細資訊，請參閱[AS2 訊息](../core/as2-messages.md)和[MDN 訊息](../core/mdn-messages.md)。  
  
 若 MDN 將以同步方式傳回，則 MDN 就會透過雙向接收位置的傳送埠傳回。 這個 MDN 是做為 HTTP 回應，例如 200OK 表示成功接收訊息。  
  
 若 MDN 將以非同步方式傳回，MDN 就必須透過不同的傳送埠傳回。 如果使用動態傳送埠，MDN 將會傳送給 Disposition-notification-to 標頭中包含的位址。  
  
> [!NOTE]
>  用來接收 AS2 訊息的雙向接收埠不應該用來接收 MDN 訊息。 MDN 訊息應該透過靜態單向接收埠接收。 針對以非同步方式傳回的 MDN 使用要求/回應接收埠，會讓 200OK 訊息無法在回應內送 MDN 時傳回，導致系統不必要重試 MDN 傳輸作業。  
  
## <a name="how-the-as2-receive-pipelines-work"></a>AS2 接收管線如何運作  
 AS2 接收管線處理內送 AS2 訊息時的步驟，如下所示：  
  
-   藉由比對 AS2 判斷傳送合作對象-訊息的 AS2 標頭的值與 AS2 的值從-從清單中**識別碼**頁面的單向 AS2 協議索引標籤的**協議屬性**  對話方塊。 若比對失敗，就會嘗試比對針對內送訊息設定的 AS2-From 內容屬性和合作對象名稱，藉此判斷傳送合作對象。 如果找到相符項目，而**對驗證與 MDN 使用協議設定，而非訊息標頭**的單向 AS2 協議索引標籤中選取屬性**協議屬性**對話方塊中， [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用來處理 AS2 訊息相關聯的協議的合作對象的 AS2 屬性。 若未選取此屬性，接收管線將會使用內送訊息中的 AS2 標頭標記。 若未找到協議，則管線會中止處理、擱置訊息，並引發例外狀況。  
  
    > [!NOTE]
    >  **對驗證與 MDN 使用協議設定，而非訊息標頭**屬性可讓您驗證內送訊息已簽署、 加密和壓縮屬性 (如果在指定這些屬性中的協議**驗證**單向協議 索引標籤)，如果沒有的話，擱置訊息並發佈錯誤。 這些變更必須與傳送端合作對象的協議交涉。 如需詳細資訊，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。  
  
-   若已決定傳送端合作對象的協議，但接收管線試圖處理 AS2 訊息時發生錯誤，則管線會將 AS2 訊息的內容屬性 MessageDestination 設定為 SuspendQueue。 接收管線接著會擱置 MessageBox 內的訊息。 接收管線也會設定`EdiIntAS.IsAS2FailedMessage`內容屬性設定為 True。 如果已啟用 MDN，藉由設定**要求 MDN**中**傳送者 MDN 設定**頁面的單向 AS2 協議索引標籤的**協議屬性**對話方塊中，管線將然後返回寄件者適合的 MDN。 管線只要收到要求就一定會傳回 MDN。  
  
-   判斷訊息是否重複出現，如果**檢查是否有重複的訊息內**中選取選項**驗證**頁面的單向 AS2 協議索引標籤的**協議屬性** 對話方塊。 重複訊息偵測透過比對 AS2-從 AS2-，以及先前接收的訊息上的值的傳入訊息上的訊息識別碼值。 如果所有三個值都相符，接收管線會將 `EdiIntAs.IsAS2MessageDuplicate` 內容屬性的值設定為 true。 如果**擱置重複訊息**選項也會選取上**驗證** 頁面上，將會擱置訊息，並記錄錯誤。  
  
-   擷取每一個附件的檔案名稱 (如果有的話)，並將其升級為內容屬性。  
  
-   若已在單向 AS2 協議屬性中啟用，則複製訊息 (以電傳格式) 並將複本儲存在不可否認性的接收資料庫中。  
  
-   執行 MIME 處理，包含驗證簽章並將訊息解密 (以標頭標記為基礎)。  
  
-   若所接收的是壓縮訊息，請解壓縮。  
  
-   產生 HTTP 回應，再以同步要求-回應的模式附加於 MDN，或以非同步的模式當成獨立式回應傳送。  
  
-   若經請求，請產生 MDN 回應。 如果管線將會產生根據協議屬性，MDN**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性設定，或內容屬性，如果未設定該屬性。 若組態設定和內送訊息的標頭不一致，管線就會產生負 MDN。  
  
-   若訊息為 EDI 編碼且已啟用通知，AS2EdiReceive 接收管線內的 EDI 解譯器就會產生 EDI 通知。 管線會將 EDI 通知路由至 MessageBox，動態傳送埠從 MessageBox 收取通知後，再以非同步的方式將它傳送出去。 EDI 通知永遠都是透過 AS2 傳輸以非同步的方式傳送出去，因為 MDN 或 HTTP 回應都是以同步的方式傳送。  
  
-   若已在單向 AS2 協議屬性中啟用，就複製 MDN 並將它儲存在不可否認性的接收資料庫中。  
  
-   若已在單向 AS2 協議屬性中啟用，則複製解碼的訊息，並將複本儲存在不可否認性的接收資料庫中。  
  
 若發生 AS2 錯誤，則不會進一步處理接收的訊息。 然而接收管線仍會產生 MDN 回應。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)   
 [AS2 訊息](../core/as2-messages.md)   
 [MDN 訊息](../core/mdn-messages.md)