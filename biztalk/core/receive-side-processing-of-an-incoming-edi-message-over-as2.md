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
# <a name="receive-side-processing-of-an-incoming-edi-message-over-as2"></a><span data-ttu-id="5a147-102">透過 AS2 從接收端處理內送 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="5a147-102">Receive-Side Processing of an Incoming EDI Message over AS2</span></span>
<span data-ttu-id="5a147-103">透過 AS2 從接收端處理 EDI 訊息的作業包括接收 AS2 訊息、傳送 MDN、處理 EDI 內容，以及傳送 EDI 通知 (若已啟用)。</span><span class="sxs-lookup"><span data-stu-id="5a147-103">Receive-side processing of an EDI message over AS2 includes receiving the AS2 message, sending an MDN, processing the EDI payload, and sending EDI acknowledgments (if enabled).</span></span>  
  
 <span data-ttu-id="5a147-104">AS2EdiReceive 接收管線會接收 AS2 訊息，並解譯 AS2 訊息內的 EDI 內容。</span><span class="sxs-lookup"><span data-stu-id="5a147-104">The AS2EdiReceive receive pipeline receives the AS2 message, and disassembles the EDI payload within the AS2 message.</span></span> <span data-ttu-id="5a147-105">AS2EDISend 傳送管線會傳送 MDN 以回應 AS2 訊息，並傳回 EDI 通知來回應 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="5a147-105">The AS2EDISend send pipeline sends an MDN in response to the AS2 message, and an EDI acknowledgment returned in response to the EDI message.</span></span> <span data-ttu-id="5a147-106">您可以將這些管線包含在 HTTP 雙向請求-回應傳送埠 (如果 MDN 是同步的) 中，或是單向的 HTTP 傳送埠和單向的 HTTP 接收埠 (如果 MDN 是非同步的) 中。</span><span class="sxs-lookup"><span data-stu-id="5a147-106">You can include these pipelines in an HTTP two-way solicit response send port (if the MDN is synchronous), or in a one-way HTTP send port and a one-way HTTP receive port (if the MDN is asynchronous).</span></span>  
  
 <span data-ttu-id="5a147-107">為了透過 AS2 接收 EDI 交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="5a147-107">To receive an EDI interchange over AS2, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will perform the following steps:</span></span>  
  
-   <span data-ttu-id="5a147-108">處理收到的 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="5a147-108">Processing the received AS2 message</span></span>  
  
-   <span data-ttu-id="5a147-109">傳送 MDN</span><span class="sxs-lookup"><span data-stu-id="5a147-109">Sending an MDN</span></span>  
  
-   <span data-ttu-id="5a147-110">處理收到的 EDI 內容</span><span class="sxs-lookup"><span data-stu-id="5a147-110">Processing the received EDI payload</span></span>  
  
-   <span data-ttu-id="5a147-111">傳送 EDI 通知</span><span class="sxs-lookup"><span data-stu-id="5a147-111">Sending an EDI Acknowledgment</span></span>  
  
## <a name="processing-the-received-as2-message"></a><span data-ttu-id="5a147-112">處理收到的 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="5a147-112">Processing the Received AS2 message</span></span>  
 <span data-ttu-id="5a147-113">AS2EdiReceive 接收管線中的 AS2 解碼器會處理內送的 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="5a147-113">The AS2 Decoder in the AS2EdiReceive receive pipeline processes an incoming AS2 message.</span></span> <span data-ttu-id="5a147-114">這個 AS2 解碼器執行這項作業的方式是使用 `InboundHTTPHeaders` 內容屬性，也就是 HTTP 配接器從 AS2 訊息中 HTTP 標頭所建立的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="5a147-114">It does so using the `InboundHTTPHeaders` context property, which the HTTP adapter creates from the HTTP headers in the AS2 message.</span></span> <span data-ttu-id="5a147-115">這些標頭包括下列 AS2 標頭：</span><span class="sxs-lookup"><span data-stu-id="5a147-115">These headers include the following AS2 headers:</span></span>  
  
-   <span data-ttu-id="5a147-116">AS2-To</span><span class="sxs-lookup"><span data-stu-id="5a147-116">AS2-To</span></span>  
  
-   <span data-ttu-id="5a147-117">AS2-From</span><span class="sxs-lookup"><span data-stu-id="5a147-117">AS2-From</span></span>  
  
-   <span data-ttu-id="5a147-118">AS2-Version</span><span class="sxs-lookup"><span data-stu-id="5a147-118">AS2-Version</span></span>  
  
-   <span data-ttu-id="5a147-119">MessageID</span><span class="sxs-lookup"><span data-stu-id="5a147-119">MessageID</span></span>  
  
-   <span data-ttu-id="5a147-120">OriginalMessageID (僅適用於 MDN)</span><span class="sxs-lookup"><span data-stu-id="5a147-120">OriginalMessageID (for MDNs only)</span></span>  
  
-   <span data-ttu-id="5a147-121">Disposition-Notification-To (如果有要求 MDN)</span><span class="sxs-lookup"><span data-stu-id="5a147-121">Disposition-Notification-To (if an MDN is requested)</span></span>  
  
-   <span data-ttu-id="5a147-122">Receipt-Delivery-Option (如果有要求 MDN)</span><span class="sxs-lookup"><span data-stu-id="5a147-122">Receipt-Delivery-Option (if an MDN is requested)</span></span>  
  
-   <span data-ttu-id="5a147-123">Signed-Receipt-MICalg (如果有要求 MDN)</span><span class="sxs-lookup"><span data-stu-id="5a147-123">Signed-Receipt-MICalg (if an MDN is requested)</span></span>  
  
 <span data-ttu-id="5a147-124">AS2 解碼器會將這些標頭升級至訊息的內容，</span><span class="sxs-lookup"><span data-stu-id="5a147-124">The AS2 Decoder will promote these headers to the context of the message.</span></span> <span data-ttu-id="5a147-125">然後再執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5a147-125">It then does the following:</span></span>  
  
-   <span data-ttu-id="5a147-126">執行協議解析，以便判斷用來處理內送訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="5a147-126">Performs agreement resolution to determine the properties to be used to process the incoming message.</span></span> <span data-ttu-id="5a147-127">如需詳細資訊，請參閱[在內送 AS2 訊息的協議解析](../core/agreement-resolution-for-incoming-as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="5a147-127">For more information, see [Agreement Resolution for Incoming AS2 Messages](../core/agreement-resolution-for-incoming-as2-messages.md).</span></span>  
  
-   <span data-ttu-id="5a147-128">驗證傳送者使用**AS2-從**屬性。</span><span class="sxs-lookup"><span data-stu-id="5a147-128">Authenticates the sender using the **AS2-From** property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a147-129">如需有關處理 AS2 接收管線執行內送 AS2 訊息，請參閱[處理內送 AS2 訊息](../core/processing-an-incoming-as2-message.md)。</span><span class="sxs-lookup"><span data-stu-id="5a147-129">For more information about the processing that the AS2 receive pipelines perform on incoming AS2 messages, see [Processing an Incoming AS2 Message](../core/processing-an-incoming-as2-message.md).</span></span>  
  
## <a name="sending-an-mdn"></a><span data-ttu-id="5a147-130">傳送 MDN</span><span class="sxs-lookup"><span data-stu-id="5a147-130">Sending an MDN</span></span>  
 <span data-ttu-id="5a147-131">如果已啟用 MDN，AS2EdiReceive 管線便會產生 MDN，並將它放入 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="5a147-131">If an MDN was enabled, the AS2EdiReceive pipeline generates an MDN and drops it into the MessageBox.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a147-132">如需有關處理 AS2 接收管線，在外寄 Mdn 上執行，請參閱[產生外寄 MDN](../core/generating-an-outgoing-mdn.md)。</span><span class="sxs-lookup"><span data-stu-id="5a147-132">For more information about the processing that the AS2 receive pipelines perform on outgoing MDNs, see [Generating an Outgoing MDN](../core/generating-an-outgoing-mdn.md).</span></span>  
  
 <span data-ttu-id="5a147-133">**同步模式**</span><span class="sxs-lookup"><span data-stu-id="5a147-133">**Synchronous Mode**</span></span>  
  
 <span data-ttu-id="5a147-134">如果 EDI 訊息是採用同步模式透過 AS2 傳送，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會透過該同步連線傳回 MDN，然後再關閉連線。</span><span class="sxs-lookup"><span data-stu-id="5a147-134">If an EDI message is sent over AS2 in synchronous mode, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will return the MDN over that synchronous connection and then close the connection.</span></span> <span data-ttu-id="5a147-135">因為連線已經關閉，所以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法透過該連線傳回 EDI 通知 (997、TA1 或 CONTRL)。</span><span class="sxs-lookup"><span data-stu-id="5a147-135">Since the connection has been closed, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot return an EDI acknowledgment (997, TA1, or CONTRL) over that connection.</span></span> <span data-ttu-id="5a147-136">EDI 通知永遠都是透過 AS2 以非同步的方式傳送。</span><span class="sxs-lookup"><span data-stu-id="5a147-136">EDI acknowledgments are always sent asynchronously over AS2.</span></span>  
  
 <span data-ttu-id="5a147-137">MDN 將由 AS2EDIReceive 管線產生、由該管線傳送到 MessageBox，然後再由屬於要求回應接收埠一部分的 AS2Send 管線自動加以擷取。</span><span class="sxs-lookup"><span data-stu-id="5a147-137">The MDN will be generated by the AS2EDIReceive pipeline, routed by that pipeline to the MessageBox, and then automatically picked up by the AS2Send pipeline that is part of the request response receive port.</span></span>  
  
 <span data-ttu-id="5a147-138">**非同步模式**</span><span class="sxs-lookup"><span data-stu-id="5a147-138">**Asynchronous Mode**</span></span>  
  
 <span data-ttu-id="5a147-139">如果 EDIINT/AS2 編碼訊息是採用非同步模式透過 HTTP/HTTPS 傳輸來傳送，您必須建立傳送埠以個別傳回 MDN。</span><span class="sxs-lookup"><span data-stu-id="5a147-139">If an EDIINT/AS2-encoded message is sent over HTTP/HTTPS transport in asynchronous mode, you must create a send port to return the MDN separately.</span></span> <span data-ttu-id="5a147-140">您可以設定這個傳送埠，使其同時傳回非同步的 MDN 和 EDI 通知。</span><span class="sxs-lookup"><span data-stu-id="5a147-140">You can configure this send port to return both asynchronous MDNs and EDI acknowledgments.</span></span> <span data-ttu-id="5a147-141">如果它是動態傳送埠，就會使用訊息標頭內 Receipt-Delivery-Notification 一行中的位址，將訊息傳送到交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="5a147-141">If it is a dynamic send port, it will use the address in the Receipt-Delivery-Notification line in the header of the message to route the message to the trading partner.</span></span> <span data-ttu-id="5a147-142">如果它是靜態傳送埠，則會使用連接埠屬性中設定的位址。</span><span class="sxs-lookup"><span data-stu-id="5a147-142">If it is a static send port, it will use the address configured in port properties.</span></span> <span data-ttu-id="5a147-143">這個傳送埠會使用 `EdiIntAS.IsAS2AsynchronousMDN==True` 篩選運算式，訂閱非同步的 MDN。</span><span class="sxs-lookup"><span data-stu-id="5a147-143">This send port subscribes to the asynchronous MDN by using an `EdiIntAS.IsAS2AsynchronousMDN==True` filter expression.</span></span>  
  
 <span data-ttu-id="5a147-144">在非同步處理作業中，除了 MDN 之外，AS2EdiReceive 管線還會產生 HTTP 回應。</span><span class="sxs-lookup"><span data-stu-id="5a147-144">In asynchronous processing, the AS2EdiReceive pipeline will generate an HTTP response in addition to the MDN.</span></span> <span data-ttu-id="5a147-145">接收埠會透過接收埠與傳送合作對象之間的 HTTP 連線，將 HTTP 回應傳回給原始傳送者，以便關閉該連線。</span><span class="sxs-lookup"><span data-stu-id="5a147-145">The receive port returns the HTTP response to the original sender over the HTTP connection between the receive port and the sending party, which closes that connection.</span></span> <span data-ttu-id="5a147-146">因為 MDN 不會關閉同步連線，所以這是必要的動作。</span><span class="sxs-lookup"><span data-stu-id="5a147-146">This is necessary because the synchronous connection is not closed by the MDN.</span></span>  
  
 <span data-ttu-id="5a147-147">如果 BizTalk 透過 HTTP/HTTPS 傳輸 EDIINT/AS2 編碼訊息，但是 EDI 編碼內容的處理作業失敗，原始訊息的傳送者將會同時收到 MDN 和 EDI 通知，前者指出 AS2 處理成功，後者則指出 EDI 處理失敗。</span><span class="sxs-lookup"><span data-stu-id="5a147-147">If BizTalk transports an EDIINT/AS2-encoded message over HTTP/HTTPS, but processing of the EDI-encoded payload fails, the sender of the original message would receive both an MDN indicating successful AS2 processing and an EDI acknowledgment indicating a failure in EDI processing.</span></span> <span data-ttu-id="5a147-148">系統將會擱置 EDI 編碼內容，而且會發佈錯誤。</span><span class="sxs-lookup"><span data-stu-id="5a147-148">The EDI-encoded payload would be suspended and an error would be posted.</span></span>  
  
## <a name="processing-the-received-edi-payload"></a><span data-ttu-id="5a147-149">處理收到的 EDI 內容</span><span class="sxs-lookup"><span data-stu-id="5a147-149">Processing the Received EDI Payload</span></span>  
 <span data-ttu-id="5a147-150">如果**輸入批次處理選項**EDI 協議設定為 **將交換分割**，AS2EdiReceive 接收管線相關聯，與雙向要求回應接收位置的剖析EDI 訊息轉換成個別的 XML 訊息，針對每個 EDI 交易集。</span><span class="sxs-lookup"><span data-stu-id="5a147-150">If the **Inbound batch processing option** for an EDI agreement is set to **Split Interchange**, the AS2EdiReceive receive pipeline associated with the two-way request response receive location parses the EDI message into a separate XML message for each EDI transaction set.</span></span> <span data-ttu-id="5a147-151">如果**輸入批次處理選項**設**保留交換**，接收管線就不會剖析 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="5a147-151">If the **Inbound batch processing option** is set to **Preserve Interchange**, the receive pipeline will not parse the EDI message.</span></span>  
  
 <span data-ttu-id="5a147-152">接收管線會將 XML 交易集或保留的 EDI 交換傳送到 BizTalk MessageBox。</span><span class="sxs-lookup"><span data-stu-id="5a147-152">The receive pipeline routes the XML transaction sets or the preserved EDI interchange to the BizTalk MessageBox.</span></span>  
  
 <span data-ttu-id="5a147-153">如果訊息要傳送到後端應用程式，傳送埠會擷取 XML 訊息，並將它傳送到該應用程式。</span><span class="sxs-lookup"><span data-stu-id="5a147-153">If the message is to be routed to a back-end application, a send port picks up the XML message and routes it to the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a147-154">這個傳送埠可以是任何類型。</span><span class="sxs-lookup"><span data-stu-id="5a147-154">This send port can be of any type.</span></span>  
  
## <a name="sending-the-edi-acknowledgment"></a><span data-ttu-id="5a147-155">傳送 EDI 通知</span><span class="sxs-lookup"><span data-stu-id="5a147-155">Sending the EDI Acknowledgment</span></span>  
 <span data-ttu-id="5a147-156">如果啟用 EDI 通知，AS2EdiReceive 接收管線中的 EDI 解譯器將會產生 EDI 通知 (若已啟用)。</span><span class="sxs-lookup"><span data-stu-id="5a147-156">If an EDI acknowledgment was enabled, the EDI Disassembler in the AS2EdiReceive receive pipeline will generate EDI acknowledgments (if enabled).</span></span> <span data-ttu-id="5a147-157">EDI 通知必須由 AS2EdiSend 傳送管線在個別的單向傳送埠中傳送。</span><span class="sxs-lookup"><span data-stu-id="5a147-157">The EDI acknowledgments must be sent by the AS2EdiSend send pipeline in a separate one-way send port.</span></span>  
  
 <span data-ttu-id="5a147-158">如果您設定雙向要求-回應接收埠同步的 MDN 或 HTTP 回應 （如果是非同步的 MDN)，傳回的 EDI/AS2 訊息的**通知的路由設定為傳送管線在要求-回應接收埠**屬性 (在中設定**本機主機設定**中單向 EDI 協議頁面**協議屬性**對話方塊) 將會被忽略。</span><span class="sxs-lookup"><span data-stu-id="5a147-158">If you set up a two-way request-response receive port for EDI/AS2 messages to return a synchronous MDN or an HTTP response (in the case of an asynchronous MDN), the **Route ACK to send pipeline on request-response receive port** property (set in the **Local Host Settings** page of the one-way EDI agreement in the **Agreement Properties** dialog box) will be ignored.</span></span> <span data-ttu-id="5a147-159">即使核取了這個屬性，傳送管線還是會傳回同步的 MDN 或 HTTP 回應，而不會傳回 EDI 通知。</span><span class="sxs-lookup"><span data-stu-id="5a147-159">Even if this property is checked, the send pipeline will return either a synchronous MDN or an HTTP response, not an EDI acknowledgment.</span></span>  
  
 <span data-ttu-id="5a147-160">如需詳細資訊，請參閱[傳送 EDI 通知](../core/sending-an-edi-acknowledgment.md)。</span><span class="sxs-lookup"><span data-stu-id="5a147-160">For more information, see [Sending an EDI Acknowledgment](../core/sending-an-edi-acknowledgment.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a147-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a147-161">See Also</span></span>  
 [<span data-ttu-id="5a147-162">BizTalk Server 如何接收 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="5a147-162">How BizTalk Server Receives AS2 Messages</span></span>](../core/how-biztalk-server-receives-as2-messages.md)