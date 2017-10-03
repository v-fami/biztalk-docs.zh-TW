---
title: "MDN 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16ac6253-0be5-4636-b102-bf5af8956261
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a6600237961b59e440a460263a8f4315b2c4773
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mdn-messages"></a>MDN 訊息
「訊息處理通知」(MDN) 是為了回應 AS2 訊息而傳送的通知。 如果已啟用 MDN，則必須等到接收及驗證 MDN 之後，AS2 傳輸才算完成。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將一律嘗試傳回 MDN 以指出訊息處理的狀態，即使處理 AS2 訊息時發生錯誤。  
  
 MDN 提供下列驗證：  
  
-   **原始訊息已成功接收的合作對象所收到**。 原始訊息的傳送者會比較原始傳送訊息的 MessageID 與接收者包含在 MDN 中的原始訊息識別碼欄位，以驗證這一點。  
  
-   **接收端夥伴已確認交換資料的完整性**。 原始訊息的傳送者會比較從原始傳送訊息內容計算得出的 MIC，以及接收者在所接收訊息內容上計算所得並包含在 MDN 之 Received-content-MIC 欄位 (若已簽署) 的 MIC，以驗證這一點。  
  
-   **是不可否認性回條**。 傳送者採用的方式是使用接收端夥伴的公用金鑰驗證簽署的 MDN，並確認 MDN 中傳回的 MIC 值與儲存在不可否認性資料庫中的原始訊息內容 MIC 相同。  
  
    > [!NOTE]
    >  同步的 MDN 可做為 HTTP 回應，例如 200 OK。  
  
    > [!NOTE]
    >  Mdn 的接收端處理的相關資訊，請參閱[處理內送 MDN](../core/processing-an-incoming-mdn.md)。 Mdn 的傳送端處理的相關資訊，請參閱[傳送外寄 MDN](../core/sending-an-outgoing-mdn.md)。  
  
## <a name="properties-used-to-generate-the-mdn"></a>用來產生 MDN 的屬性  
 AS2Receive 接收管線會產生 MDN 使用合作對象的 AS2 協議屬性，如果**對驗證與 MDN 使用協議設定，而非訊息標頭**單向協議索引標籤上選取屬性**協議屬性** 對話方塊。 在這種情況下，接收管線將會使用訊息標頭中的 AS2-Form 屬性來產生 MDN，但是其他屬性則取自合作對象的 AS2 協議設定。  
  
 如果沒有選取覆寫 AS2 屬性的選項，或者無法使用合作對象 AS2 協議，接收管線將會使用內送訊息中的 AS2 標頭標記來產生 MDN。  
  
 MDN 可以簽署，但是無法加密或壓縮。  
  
## <a name="mdn-context-properties"></a>MDN 內容屬性  
 處理 MDN 訊息時使用的內容屬性包括可以升級的屬性，以及雖然不公開但是可以在擱置和追蹤訊息中檢視的屬性。 如需這些內容屬性的清單，請參閱[AS2 內容屬性](../core/as2-context-properties.md)。  
  
 DispositionMode 和 DispositionType 兩個內容屬性必須同時升級，才能產生 MDN。 如果 AS2 或 EDI 內容出現錯誤，DispositionType 屬性將會指出該項錯誤。 您可以看到這個屬性中的**訊息詳細資料**（透過 [服務詳細資料] 對話方塊中） 從擱置服務執行個體，在顯示的對話方塊**群組中樞**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如果標頭發生錯誤，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會在 DispositionType 屬性中指出這項錯誤，而且會嘗試傳送 MDN，但是也可能因為錯誤的不同，而無法這樣做。  
  
## <a name="mdn-headers"></a>MDN 標頭  
 MDN 包含下列標頭：  
  
-   **HTTP/AS2 標頭**。 如需詳細資訊，請參閱[AS2 訊息](../core/as2-messages.md)。  
  
-   **傳輸層**。 這包括 Content-Type 標頭 (內含已簽署的多部分訊息)、MIC 的演算法、簽章格式通訊協定，以及最外層多部分界限子標頭。  
  
-   **第一個部分**。 多部分簽署訊息的第一個部分是內嵌的 MDN。 這個部分可由人工判讀。  
  
-   **第二個部分**。 多部分簽署訊息的第二個部分包含數位簽章、原始訊息的參考、配置類型和狀態，以及 MIC 值。 這個部分可由電腦判讀。  
  
 AS2-From 標頭、AS2-To 標頭和 MessageID 內容屬性可用來讓 MDN 與其回應的 AS2 訊息產生關聯。 MDN 中的 Original-Message-ID 標頭則來自 MDN 回應之 AS2 的 Message-ID 標頭。  
  
## <a name="mic"></a>MIC  
 訊息完整性檢查 (MIC) 是用來確認 MDN 有和原始傳送的訊息內容相互關聯。 MIC 摘要包含在多部分簽署 MDN 訊息第二個部分的 Received-Content-MIC 延伸模組欄位中。  
  
 如果已啟用 MDN，在 AS2 傳送管線處理輸出訊息時，它會根據訊息內容計算 MICHashValue。 傳送管線會將雜湊值儲存在 BizTalkMsgBoxDb 資料庫的 EdiInt_Mic 資料表中。 AS2 訊息是在這個資料表中加以追蹤，以 AS2From、AS2To 和 MessageID 等值，連同伴隨的 MICHashValue 資料行，做為其唯一識別。 訊息接收者會在處理訊息內容時計算 MIC 雜湊值，並將雜湊值包含在其所傳回的 MDN 中。 原始訊息的傳送者將會比較其接收之 MDN，以及其所儲存的雜湊值。 如果兩者相符，它就會處置 MDN，並刪除 EdiInt_Mic 資料表中的項目，以完成傳輸作業。  
  
 MIC 使用 Base64 編碼。 套用至 MIC 的演算法可以是 SHA1 或 MD5。 取決於**簽署演算法**下拉式清單 (如果已啟用**要求簽署的 MDN**會檢查屬性) 在**傳送者 MDN 設定**頁面的單向協議索引標籤中**協議屬性** 對話方塊。 它也會根據原始訊息的 Signed-Receipt-MICalg AS2 標頭來決定。  
  
## <a name="see-also"></a>另請參閱  
 [AS2 訊息](../core/as2-messages.md)   
 [處理內送 MDN](../core/processing-an-incoming-mdn.md)   
 [傳送外寄 MDN](../core/sending-an-outgoing-mdn.md)