---
title: 接收端處理透過 AS2 內送的非 EDI 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fee10cba-8b1a-4d2c-b9d9-efbb74c3f461
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a313c7351f40ba3dbdaf33d15008598dac2ad73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269446"
---
# <a name="receive-side-processing-of-an-incoming-non-edi-message-over-as2"></a>透過 AS2 內送之非 EDI 訊息的接收端處理
隨附於 AS2 管線[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以用來處理透過 AS2 傳輸的 EDI 訊息或非 EDI 訊息。 這兩種不同的內容類型會使用不同的管線。 您會使用 AS2EdiReceive 管線來處理透過 AS2 內送的 EDI 訊息，而使用 AS2Send 管線傳回關聯的 MDN (如果有啟用)。 您會使用 AS2Receive 管線來處理透過 AS2 內送的非 EDI 訊息，而使用 AS2Send 管線來傳回關聯的 MDN (如果有啟用)。 非 EDI 訊息可以是任何二進位內容。  
  
 AS2Receive 接收管線會解碼 AS2 訊息，然後對 AS2 訊息執行解譯。 AS2Send 傳送管線則會編碼 MDN。 您可以將 AS2Receive 和 AS2Send 管線包含在 HTTP 雙向請求-回應傳送埠中 (如果 MDN 是同步的)，或是包含在單向的 HTTP 傳送埠和單向的 HTTP 接收埠中 (如果 MDN 是非同步的)。 如果需要執行非 EDI 內容的解譯，您就必須在另一個接收管線中執行這項解譯，因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只允許一個接收管線存在一個解譯器。 這將需要回送傳送埠和接收位置 (請參閱[處理接收非 EDI 內容](../core/receive-side-processing-of-an-incoming-non-edi-message-over-as2.md#BKMK_NonEDI)下一節)。  
  
 為了透過 AS2 接收非 EDI 交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會執行下列步驟：  
  
-   處理收到的 AS2 訊息  
  
-   傳送 MDN  
  
-   處理收到的非 EDI 內容  
  
## <a name="processing-the-received-as2-message"></a>處理收到的 AS2 訊息  
 AS2Receive 接收管線中的 AS2 解碼器會處理內送的 AS2 訊息。 這個 AS2 解碼器執行這項作業的方式是使用 `InboundHTTPHeaders` 內容屬性，也就是 HTTP 配接器從 AS2 訊息中 HTTP 標頭所建立的內容屬性。 這些標頭包括下列 AS2 標頭：  
  
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
  
-   使用 AS2-From 和 AS2-To 屬性來驗證傳送者。  
  
    > [!NOTE]
    >  如需有關處理 AS2 接收管線執行內送 AS2 訊息，請參閱[處理內送 AS2 訊息](../core/processing-an-incoming-as2-message.md)。  
  
## <a name="sending-an-mdn"></a>傳送 MDN  
 如果已啟用 MDN，AS2Receive 管線便會產生 MDN，並將它放入 MessageBox 中。 MDN 傳回原始訊息之傳送者的方式，將視 AS2 傳輸為同步或非同步來決定。  
  
> [!NOTE]
>  如需有關處理 AS2 接收管線，在外寄 Mdn 上執行，請參閱[產生外寄 MDN](../core/generating-an-outgoing-mdn.md)。  
  
 **同步模式**  
  
 如果非 EDI 訊息是採用同步模式透過 AS2 傳送，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會透過該同步連線傳回 MDN，然後再關閉連線。 MDN 將由 AS2Receive 管線產生並接著傳送到 MessageBox，接著再自動由屬於要求回應接收埠一部分的 AS2Send 管線加以接收。  
  
 **非同步模式**  
  
 如果非 EDI 訊息是透過 HTTP/HTTPS 傳輸以非同步模式來傳送，您就必須建立要個別傳回 MDN 的傳送埠。 如果它是動態傳送埠，就會使用訊息標頭內 Receipt-Delivery-Notification 一行中的位址，將訊息傳送到交易夥伴。 如果它是靜態傳送埠，則會使用連接埠屬性中定義的位址。 這個傳送埠會使用 `EdiIntAS.IsAS2AsynchronousMDN==True` 篩選運算式，訂閱非同步的 MDN。 在非同步處理作業中，除了 MDN 之外，AS2Receive 管線還會產生 HTTP 回應。 接收埠會透過接收埠與傳送合作對象之間的 HTTP 連線，將 HTTP 回應傳回給原始傳送者，以便關閉該連線。 因為 MDN 不會關閉同步連線，所以這是必要的動作。  
  
##  <a name="BKMK_NonEDI"></a>處理收到的非 EDI 內容  
 若是收到透過 AS2 的非 EDI 編碼訊息，而且需要對該內容執行解譯時，您就必須在不同於 AS2Receive 管線的接收管線中進行解譯。 這是必要的做法，因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只允許一個接收管線中存在一個解譯器。 這種實例將需要使用傳送埠和接收位置的回送機制。 在第一個階段中，EDIReceive 管線處理 AS2 訊息，並以其原生格式來傳送訊息到 MessageBox。 在第二次傳遞中，接收管線會從訊息的原生格式產生 XML。  
  
 BizTalk Server 將會對透過 AS2 傳送的非 EDI 訊息執行下列接收端處理：  
  
-   與雙向要求回應接收位置關聯的 AS2Receive 接收管線會剖析非 EDI 訊息的 AS2 標頭，然後將非 EDI 訊息路由至 BizTalk MessageBox。  
  
-   回送傳送埠 (可以是 FILE 或 MSMQ) 會從 MessageBox 擷取非 EDI 訊息，因為它會對 BizTalk 屬性 `IsAS2PayloadMessage == True` 加以篩選。 與此傳送埠關聯的 PassThruTransmit 傳送管線，則會以非 EDI 格式將訊息傳遞下去，進而將訊息路由至資料夾或 MSMQ 佇列。  
  
-   回送接收位置會擷取訊息。 與回送接收位置關聯的接收管線會從非 EDI 訊息產生 XML 訊息，並會將其路由至 MessageBox。  
  
-   如果訊息要傳送到後端應用程式，傳送埠會擷取 XML 訊息，並將它傳送到該應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)   
 [透過 AS2 外寄 EDI 訊息的傳送端處理](../core/send-side-processing-of-an-outgoing-edi-message-over-as2.md)