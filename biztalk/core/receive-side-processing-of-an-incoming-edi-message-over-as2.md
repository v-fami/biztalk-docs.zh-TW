---
title: 接收端處理透過 AS2 內送的 EDI 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 118451ab-d847-4f87-80ab-3cf812d71ac3
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fc9069dddf8a8b58ad439ed915fc9afa539c2a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270062"
---
# <a name="receive-side-processing-of-an-incoming-edi-message-over-as2"></a>透過 AS2 從接收端處理內送 EDI 訊息
透過 AS2 從接收端處理 EDI 訊息的作業包括接收 AS2 訊息、傳送 MDN、處理 EDI 內容，以及傳送 EDI 通知 (若已啟用)。  
  
 AS2EdiReceive 接收管線會接收 AS2 訊息，並解譯 AS2 訊息內的 EDI 內容。 AS2EDISend 傳送管線會傳送 MDN 以回應 AS2 訊息，並傳回 EDI 通知來回應 EDI 訊息。 您可以將這些管線包含在 HTTP 雙向請求-回應傳送埠 (如果 MDN 是同步的) 中，或是單向的 HTTP 傳送埠和單向的 HTTP 接收埠 (如果 MDN 是非同步的) 中。  
  
 為了透過 AS2 接收 EDI 交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會執行下列步驟：  
  
-   處理收到的 AS2 訊息  
  
-   傳送 MDN  
  
-   處理收到的 EDI 內容  
  
-   傳送 EDI 通知  
  
## <a name="processing-the-received-as2-message"></a>處理收到的 AS2 訊息  
 AS2EdiReceive 接收管線中的 AS2 解碼器會處理內送的 AS2 訊息。 這個 AS2 解碼器執行這項作業的方式是使用 `InboundHTTPHeaders` 內容屬性，也就是 HTTP 配接器從 AS2 訊息中 HTTP 標頭所建立的內容屬性。 這些標頭包括下列 AS2 標頭：  
  
-   AS2-To  
  
-   AS2-From  
  
-   AS2-Version  
  
-   MessageID  
  
-   OriginalMessageID (僅適用於 MDN)  
  
-   Disposition-Notification-To (如果有要求 MDN)  
  
-   Receipt-Delivery-Option (如果有要求 MDN)  
  
-   Signed-Receipt-MICalg (如果有要求 MDN)  
  
 AS2 解碼器會將這些標頭升級至訊息的內容， 然後再執行下列作業：  
  
-   執行協議解析，以便判斷用來處理內送訊息的屬性。 如需詳細資訊，請參閱[在內送 AS2 訊息的協議解析](../core/agreement-resolution-for-incoming-as2-messages.md)。  
  
-   驗證傳送者使用**AS2-從**屬性。  
  
    > [!NOTE]
    >  如需有關處理 AS2 接收管線執行內送 AS2 訊息，請參閱[處理內送 AS2 訊息](../core/processing-an-incoming-as2-message.md)。  
  
## <a name="sending-an-mdn"></a>傳送 MDN  
 如果已啟用 MDN，AS2EdiReceive 管線便會產生 MDN，並將它放入 MessageBox 中。  
  
> [!NOTE]
>  如需有關處理 AS2 接收管線，在外寄 Mdn 上執行，請參閱[產生外寄 MDN](../core/generating-an-outgoing-mdn.md)。  
  
 **同步模式**  
  
 如果 EDI 訊息是採用同步模式透過 AS2 傳送，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會透過該同步連線傳回 MDN，然後再關閉連線。 因為連線已經關閉，所以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法透過該連線傳回 EDI 通知 (997、TA1 或 CONTRL)。 EDI 通知永遠都是透過 AS2 以非同步的方式傳送。  
  
 MDN 將由 AS2EDIReceive 管線產生、由該管線傳送到 MessageBox，然後再由屬於要求回應接收埠一部分的 AS2Send 管線自動加以擷取。  
  
 **非同步模式**  
  
 如果 EDIINT/AS2 編碼訊息是採用非同步模式透過 HTTP/HTTPS 傳輸來傳送，您必須建立傳送埠以個別傳回 MDN。 您可以設定這個傳送埠，使其同時傳回非同步的 MDN 和 EDI 通知。 如果它是動態傳送埠，就會使用訊息標頭內 Receipt-Delivery-Notification 一行中的位址，將訊息傳送到交易夥伴。 如果它是靜態傳送埠，則會使用連接埠屬性中設定的位址。 這個傳送埠會使用 `EdiIntAS.IsAS2AsynchronousMDN==True` 篩選運算式，訂閱非同步的 MDN。  
  
 在非同步處理作業中，除了 MDN 之外，AS2EdiReceive 管線還會產生 HTTP 回應。 接收埠會透過接收埠與傳送合作對象之間的 HTTP 連線，將 HTTP 回應傳回給原始傳送者，以便關閉該連線。 因為 MDN 不會關閉同步連線，所以這是必要的動作。  
  
 如果 BizTalk 透過 HTTP/HTTPS 傳輸 EDIINT/AS2 編碼訊息，但是 EDI 編碼內容的處理作業失敗，原始訊息的傳送者將會同時收到 MDN 和 EDI 通知，前者指出 AS2 處理成功，後者則指出 EDI 處理失敗。 系統將會擱置 EDI 編碼內容，而且會發佈錯誤。  
  
## <a name="processing-the-received-edi-payload"></a>處理收到的 EDI 內容  
 如果**輸入批次處理選項**EDI 協議設定為 **將交換分割**，AS2EdiReceive 接收管線相關聯，與雙向要求回應接收位置的剖析EDI 訊息轉換成個別的 XML 訊息，針對每個 EDI 交易集。 如果**輸入批次處理選項**設**保留交換**，接收管線就不會剖析 EDI 訊息。  
  
 接收管線會將 XML 交易集或保留的 EDI 交換傳送到 BizTalk MessageBox。  
  
 如果訊息要傳送到後端應用程式，傳送埠會擷取 XML 訊息，並將它傳送到該應用程式。  
  
> [!NOTE]
>  這個傳送埠可以是任何類型。  
  
## <a name="sending-the-edi-acknowledgment"></a>傳送 EDI 通知  
 如果啟用 EDI 通知，AS2EdiReceive 接收管線中的 EDI 解譯器將會產生 EDI 通知 (若已啟用)。 EDI 通知必須由 AS2EdiSend 傳送管線在個別的單向傳送埠中傳送。  
  
 如果您設定雙向要求-回應接收埠同步的 MDN 或 HTTP 回應 （如果是非同步的 MDN)，傳回的 EDI/AS2 訊息的**通知的路由設定為傳送管線在要求-回應接收埠**屬性 (在中設定**本機主機設定**中單向 EDI 協議頁面**協議屬性**對話方塊) 將會被忽略。 即使核取了這個屬性，傳送管線還是會傳回同步的 MDN 或 HTTP 回應，而不會傳回 EDI 通知。  
  
 如需詳細資訊，請參閱[傳送 EDI 通知](../core/sending-an-edi-acknowledgment.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)