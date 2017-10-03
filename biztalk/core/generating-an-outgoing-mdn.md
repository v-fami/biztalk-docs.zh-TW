---
title: "產生外寄 MDN |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12d7da1c-0d3c-42d4-9388-29f499353d13
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a903cc72a41362f6843449a4d635878706f2ea1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="generating-an-outgoing-mdn"></a>產生外寄 MDN
AS2 接收管線會針對內送訊息產生 MDN (訊息處理通知) 回應。 這項工作是由 AS2EDIReceive 接收管線中的 EDI 解譯器 (回應 EDI 編碼的訊息) 或 AS2Receive 接收管線中的 AS2 解譯器 (回應非 EDI 編碼的訊息) 負責執行。  
  
## <a name="when-and-how-an-mdn-is-generated"></a>何時及如何產生 MDN  
 MDN 通常是根據原始 AS2 訊息中的 AS2 標頭而產生，如下所示：  
  
-   如果 AS2 訊息中出現 Disposition-Notification-To 標頭，將會傳送 MDN。  
  
-   如果訊息中出現 Disposition-Notification-To 標頭和 Receipt-Delivery-Option 標頭，則會以非同步的方式傳送 MDN。 它會透過與原始訊息不同的連線，傳送到 Receipt-Delivery-Option 標頭中的 URL。  
  
-   如果訊息中出現 Disposition-Notification-To 標頭，但是沒有 Receipt-Delivery-Option 標頭，則會以同步的方式，透過與原始訊息相同的連線傳送 MDN。  
  
 解譯器會從收到的 AS2 訊息中的 AS2-To 標頭，在 MDN 中建立 AS2-From 標頭，並從收到的 AS2 訊息中的 AS2-From 標頭，在 MDN 中建立 AS2-To 標頭。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可讓您覆寫這些設定，包括根據合作對象的 AS2 協議屬性，指定是否產生 MDN 及其產生方式。 您覆寫訊息中的 AS2 標頭設定**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性的單向 AS2 協議索引標籤中**協議屬性** 對話方塊。 這個屬性可讓您傳送 MDN (即使 AS2 標頭未呼叫它也一樣)，或是在 AS2 標頭指定同步連線時非同步傳送 MDN。  
  
 如果您設定**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性中的值**要求 MDN**區段**傳送者 MDN 設定**頁面在單向 AS2 協議索引標籤的**協議屬性**對話方塊將會用於 MDN，如下所示：  
  
-   如果會傳送 MDN**要求 MDN**選取屬性。  
  
-   如果**要求 MDN**選取屬性，而**要求非同步 MDN**屬性，將會以非同步方式傳送 MDN。 MDN 會傳送到的 URL，**回條傳遞選項 (URL)**屬性設定為，透過與原始訊息不同的連線。  
  
-   如果**要求 MDN**選取屬性，但**要求非同步 MDN**未選取屬性，將以同步方式傳送 MDN，透過與原始訊息相同的連線。  
  
 如果**對驗證與 MDN 使用協議設定，而非訊息標頭**設定屬性，AS2-從訊息中的屬性標頭會用來產生 MDN，但是 AS2-若要將取自協議屬性中，並管線會簽署 MDN 根據**要求簽署的 MDN**屬性。 AS2 標頭會依照下列方式對應至協議屬性：  
  
|協議屬性|訊息中的 AS2 標頭|  
|------------------------|-------------------------------|  
|產生 MDN|Disposition-Notification-To|  
|簽署 MDN|Signed-Receipt-Protocol|  
|Receipt-Delivery-Option|Receipt-Delivery-Option|  
  
 如果 MDN 已啟用，接收管線將會升級下列內容屬性：  
  
-   `EdiIntAS.DispositionMode`  
  
-   `EdiIntAS.DispositionType`  
  
 這兩個內容屬性都必須升級，才能產生 MDN。 如需有關這些內容屬性的詳細資訊，請參閱[AS2 內容屬性](../core/as2-context-properties.md)。  
  
 若組態設定和內送訊息的標頭不一致，管線就會產生負 MDN。  
  
 如果在協議屬性中要求 MDN，則即使 AS2 處理中發生錯誤，接收管線也會嘗試傳送 MDN。  
  
## <a name="how-the-receive-pipeline-processes-a-generated-mdn"></a>接收管線如何處理產生的 MDN  
 如果 MDN 產生根據上述規則 AS2EDIReceive 或 AS2Receive 接收管線就會以下列方式處理 MDN:  
  
-   如果已在單向 AS2 協議屬性中啟用，就複製 MDN (採用電傳格式) 並將它儲存在不可否認性資料庫中。  
  
-   如果已在單向 AS2 協議屬性中啟用，則執行 MIME 處理，包括套用數位簽章。  
  
-   計算 AS2 訊息內容的 MIC (訊息完整性檢查)，並將它附加到 MDN 的 Received-content-MIC 延伸模組欄位。 要套用的 MIC 由內送訊息的簽署回條 micalg 標頭的演算法或**簽署演算法**屬性**傳送者 MDN 設定**頁面的單向協議索引標籤的**協議屬性**對話方塊 （當輸入的訊息屬性會覆寫）。 它可以是 SHA1 或 MD5。 演算法的值也會包括在 MDN 中。  
  
-   在不可否認性的資料庫中建立相互關聯項目。  
  
-   建立 MDN 訊息的複本。  
  
-   若要採同步方式傳輸 MDN，管線會將 `EdiIntAS.IsAS2AsynchronousMDN` 屬性設定為 False；若採非同步方式，則會將 Async 屬性設定為 True。  
  
-   若要採同步方式傳輸 MDN，與雙向接收埠關聯的 AS2Send 傳送管線將會依據 `EdiIntAS.IsAS2AsynchronousMDN` 屬性 (設定為 False) 和相互關聯 Token 來接受 MDN。  
  
    > [!NOTE]
    >  您也可以設定訂閱外寄同步 MDN 的傳送埠。 若要這樣做，請將傳送埠篩選條件設定為 `EdiIntAS.IsAS2MdnResponseMessage==True`。  
  
-   若要採非同步方式傳輸 MDN，接收管線會將 MDN 傳送至 MessageBox。 您必須將傳送埠設定為訂閱 MDN，並將傳送埠篩選條件設定為 `IsAS2AsynchronousMdn==True`。 AS2Send 傳送管線會依據該屬性和相互關聯 Token 來接受訊息。 如果傳送埠是動態的，它會依據訊息標頭內 Receipt-Delivery-Notification 一行中的位址來傳送 MDN。 如果傳送埠是靜態的，它會依據傳送埠的 [傳輸 URI] 屬性來路由訊息。  
  
## <a name="mdn-generation-rules"></a>MDN 產生規則  
 下列規則適用於 MDN 的產生：  
  
-   當訊息傳送者明確要求簽署回條，但處理訊息內容卻發生錯誤時，即使交易本身可能無效，訊息接收者仍然必須傳回簽署回條。 必須在 "disposition-field" 中設定處理訊息內容時發生錯誤的原因。  
  
-   當 MDN 回條的要求中明確指定簽署回條，但是原始訊息的接收者卻無法支援要求的通訊協定格式或要求的 MIC 演算法時，則應該會傳回已簽署或未簽署的回條。  
  
-   如果未明確要求簽章，或接收方合作對象的協議無法辨識簽署回條要求參數，則接收方合作對象可能會傳回未簽署的回條、簽署的回條或是不傳回回條。  
  
## <a name="mic-generation"></a>MIC 產生  
 在需要 MDN 時，原始訊息的接收者會產生 MIC (訊息完整性檢查) 並將它加入至 MDN 中。 當 EDI 交換屬於多部分 MIME 內容類型的一部分時，必須針對整個多部分內容來計算 MIC，包括 EDI 交換和 MIME 標頭。 針對經過加密的未簽署訊息，則會在解密的 MIME 標頭和內容上計算要傳回的 MIC。 針對未簽署、未加密的訊息，則必須計算不含 MIME 標頭之訊息內容的 MIC。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)