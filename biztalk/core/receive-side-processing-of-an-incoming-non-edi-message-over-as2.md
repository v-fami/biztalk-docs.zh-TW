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
# <a name="receive-side-processing-of-an-incoming-non-edi-message-over-as2"></a><span data-ttu-id="38f08-102">透過 AS2 內送之非 EDI 訊息的接收端處理</span><span class="sxs-lookup"><span data-stu-id="38f08-102">Receive-Side Processing of an Incoming Non-EDI Message over AS2</span></span>
<span data-ttu-id="38f08-103">隨附於 AS2 管線[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以用來處理透過 AS2 傳輸的 EDI 訊息或非 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="38f08-103">The AS2 pipelines shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be used to process an EDI message or a non-EDI message over AS2 transport.</span></span> <span data-ttu-id="38f08-104">這兩種不同的內容類型會使用不同的管線。</span><span class="sxs-lookup"><span data-stu-id="38f08-104">Different pipelines are used for the two different types of payloads.</span></span> <span data-ttu-id="38f08-105">您會使用 AS2EdiReceive 管線來處理透過 AS2 內送的 EDI 訊息，而使用 AS2Send 管線傳回關聯的 MDN (如果有啟用)。</span><span class="sxs-lookup"><span data-stu-id="38f08-105">You use the AS2EdiReceive pipeline to process an incoming EDI message over AS2, and the AS2Send pipeline to return the associated MDN (if enabled).</span></span> <span data-ttu-id="38f08-106">您會使用 AS2Receive 管線來處理透過 AS2 內送的非 EDI 訊息，而使用 AS2Send 管線來傳回關聯的 MDN (如果有啟用)。</span><span class="sxs-lookup"><span data-stu-id="38f08-106">You use the AS2Receive pipeline to process an incoming non-EDI message over AS2, and the AS2Send pipeline to return the associated MDN (if enabled).</span></span> <span data-ttu-id="38f08-107">非 EDI 訊息可以是任何二進位內容。</span><span class="sxs-lookup"><span data-stu-id="38f08-107">The non-EDI message can be any binary payload.</span></span>  
  
 <span data-ttu-id="38f08-108">AS2Receive 接收管線會解碼 AS2 訊息，然後對 AS2 訊息執行解譯。</span><span class="sxs-lookup"><span data-stu-id="38f08-108">The AS2Receive receive pipeline decodes the AS2 message, and then performs disassembly on the AS2 message.</span></span> <span data-ttu-id="38f08-109">AS2Send 傳送管線則會編碼 MDN。</span><span class="sxs-lookup"><span data-stu-id="38f08-109">An AS2Send send pipeline encodes the MDN.</span></span> <span data-ttu-id="38f08-110">您可以將 AS2Receive 和 AS2Send 管線包含在 HTTP 雙向請求-回應傳送埠中 (如果 MDN 是同步的)，或是包含在單向的 HTTP 傳送埠和單向的 HTTP 接收埠中 (如果 MDN 是非同步的)。</span><span class="sxs-lookup"><span data-stu-id="38f08-110">You can include the AS2Receive and AS2Send pipelines in an HTTP two-way solicit response send port (if the MDN is synchronous), or in a one-way HTTP send port and a one-way HTTP receive port (if the MDN is asynchronous).</span></span> <span data-ttu-id="38f08-111">如果需要執行非 EDI 內容的解譯，您就必須在另一個接收管線中執行這項解譯，因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只允許一個接收管線存在一個解譯器。</span><span class="sxs-lookup"><span data-stu-id="38f08-111">If you need to perform disassembly of a non-EDI payload, you will have to do that in another receive pipeline, because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] only allows one disassembler in a receive pipeline.</span></span> <span data-ttu-id="38f08-112">這將需要回送傳送埠和接收位置 (請參閱[處理接收非 EDI 內容](../core/receive-side-processing-of-an-incoming-non-edi-message-over-as2.md#BKMK_NonEDI)下一節)。</span><span class="sxs-lookup"><span data-stu-id="38f08-112">This will require a loopback send port and receive location (see the [Processing the Received Non-EDI Payload](../core/receive-side-processing-of-an-incoming-non-edi-message-over-as2.md#BKMK_NonEDI) section below).</span></span>  
  
 <span data-ttu-id="38f08-113">為了透過 AS2 接收非 EDI 交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="38f08-113">To receive a non-EDI interchange over AS2, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will perform the following steps:</span></span>  
  
-   <span data-ttu-id="38f08-114">處理收到的 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="38f08-114">Processing the received AS2 message</span></span>  
  
-   <span data-ttu-id="38f08-115">傳送 MDN</span><span class="sxs-lookup"><span data-stu-id="38f08-115">Sending an MDN</span></span>  
  
-   <span data-ttu-id="38f08-116">處理收到的非 EDI 內容</span><span class="sxs-lookup"><span data-stu-id="38f08-116">Processing the received non-EDI payload</span></span>  
  
## <a name="processing-the-received-as2-message"></a><span data-ttu-id="38f08-117">處理收到的 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="38f08-117">Processing the Received AS2 message</span></span>  
 <span data-ttu-id="38f08-118">AS2Receive 接收管線中的 AS2 解碼器會處理內送的 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="38f08-118">The AS2 Decoder in the AS2Receive receive pipeline processes an incoming AS2 message.</span></span> <span data-ttu-id="38f08-119">這個 AS2 解碼器執行這項作業的方式是使用 `InboundHTTPHeaders` 內容屬性，也就是 HTTP 配接器從 AS2 訊息中 HTTP 標頭所建立的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="38f08-119">It does so using the `InboundHTTPHeaders` context property, which the HTTP adapter creates from the HTTP headers in the AS2 message.</span></span> <span data-ttu-id="38f08-120">這些標頭包括下列 AS2 標頭：</span><span class="sxs-lookup"><span data-stu-id="38f08-120">These headers include the following AS2 headers:</span></span>  
  
-   <span data-ttu-id="38f08-121">AS2-To</span><span class="sxs-lookup"><span data-stu-id="38f08-121">AS2-To</span></span>  
  
-   <span data-ttu-id="38f08-122">AS2-From</span><span class="sxs-lookup"><span data-stu-id="38f08-122">AS2-From</span></span>  
  
-   <span data-ttu-id="38f08-123">AS2-Version</span><span class="sxs-lookup"><span data-stu-id="38f08-123">AS2-Version</span></span>  
  
-   <span data-ttu-id="38f08-124">MessageID</span><span class="sxs-lookup"><span data-stu-id="38f08-124">MessageID</span></span>  
  
-   <span data-ttu-id="38f08-125">OriginalMessageID (僅適用於 MDN)</span><span class="sxs-lookup"><span data-stu-id="38f08-125">OriginalMessageID (for MDNs only)</span></span>  
  
-   <span data-ttu-id="38f08-126">Disposition-Notification-To (如果有要求 MDN)</span><span class="sxs-lookup"><span data-stu-id="38f08-126">Disposition-Notification-To (if an MDN is requested)</span></span>  
  
-   <span data-ttu-id="38f08-127">Receipt-Delivery-Option (如果有要求 MDN)</span><span class="sxs-lookup"><span data-stu-id="38f08-127">Receipt-Delivery-Option (if an MDN is requested)</span></span>  
  
-   <span data-ttu-id="38f08-128">Signed-Receipt-MICalg (如果有要求 MDN)</span><span class="sxs-lookup"><span data-stu-id="38f08-128">Signed-Receipt-MICalg (if an MDN is requested)</span></span>  
  
 <span data-ttu-id="38f08-129">AS2 解碼器會將這些標頭升級至訊息的內容，</span><span class="sxs-lookup"><span data-stu-id="38f08-129">The AS2 Decoder will promote these headers to the context of the message.</span></span> <span data-ttu-id="38f08-130">然後再執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="38f08-130">It then does the following:</span></span>  
  
-   <span data-ttu-id="38f08-131">執行協議解析，以便判斷用來處理內送訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="38f08-131">Performs agreement resolution to determine the properties to be used to process the incoming message.</span></span> <span data-ttu-id="38f08-132">如需詳細資訊，請參閱[在內送 AS2 訊息的協議解析](../core/agreement-resolution-for-incoming-as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="38f08-132">For more information, see [Agreement Resolution for Incoming AS2 Messages](../core/agreement-resolution-for-incoming-as2-messages.md).</span></span>  
  
-   <span data-ttu-id="38f08-133">使用 AS2-From 和 AS2-To 屬性來驗證傳送者。</span><span class="sxs-lookup"><span data-stu-id="38f08-133">Authenticates the sender using the AS2-From and AS2-To properties.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38f08-134">如需有關處理 AS2 接收管線執行內送 AS2 訊息，請參閱[處理內送 AS2 訊息](../core/processing-an-incoming-as2-message.md)。</span><span class="sxs-lookup"><span data-stu-id="38f08-134">For more information about the processing that the AS2 receive pipelines perform on incoming AS2 messages, see [Processing an Incoming AS2 Message](../core/processing-an-incoming-as2-message.md).</span></span>  
  
## <a name="sending-an-mdn"></a><span data-ttu-id="38f08-135">傳送 MDN</span><span class="sxs-lookup"><span data-stu-id="38f08-135">Sending an MDN</span></span>  
 <span data-ttu-id="38f08-136">如果已啟用 MDN，AS2Receive 管線便會產生 MDN，並將它放入 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="38f08-136">If an MDN was enabled, the AS2Receive pipeline generates an MDN and drops it into the MessageBox.</span></span> <span data-ttu-id="38f08-137">MDN 傳回原始訊息之傳送者的方式，將視 AS2 傳輸為同步或非同步來決定。</span><span class="sxs-lookup"><span data-stu-id="38f08-137">How the MDN is returned to the sender of the original message depends upon whether the AS2 transport is synchronous or asynchronous.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38f08-138">如需有關處理 AS2 接收管線，在外寄 Mdn 上執行，請參閱[產生外寄 MDN](../core/generating-an-outgoing-mdn.md)。</span><span class="sxs-lookup"><span data-stu-id="38f08-138">For more information about the processing that the AS2 receive pipelines perform on outgoing MDNs, see [Generating an Outgoing MDN](../core/generating-an-outgoing-mdn.md).</span></span>  
  
 <span data-ttu-id="38f08-139">**同步模式**</span><span class="sxs-lookup"><span data-stu-id="38f08-139">**Synchronous Mode**</span></span>  
  
 <span data-ttu-id="38f08-140">如果非 EDI 訊息是採用同步模式透過 AS2 傳送，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會透過該同步連線傳回 MDN，然後再關閉連線。</span><span class="sxs-lookup"><span data-stu-id="38f08-140">If a non-EDI message is sent over AS2 in synchronous mode, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will return the MDN over that synchronous connection and then close the connection.</span></span> <span data-ttu-id="38f08-141">MDN 將由 AS2Receive 管線產生並接著傳送到 MessageBox，接著再自動由屬於要求回應接收埠一部分的 AS2Send 管線加以接收。</span><span class="sxs-lookup"><span data-stu-id="38f08-141">The MDN will be generated by the AS2Receive pipeline, routed by that pipeline to the MessageBox, and then automatically picked up by the AS2Send pipeline that is part of the request response receive port.</span></span>  
  
 <span data-ttu-id="38f08-142">**非同步模式**</span><span class="sxs-lookup"><span data-stu-id="38f08-142">**Asynchronous Mode**</span></span>  
  
 <span data-ttu-id="38f08-143">如果非 EDI 訊息是透過 HTTP/HTTPS 傳輸以非同步模式來傳送，您就必須建立要個別傳回 MDN 的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="38f08-143">If a non-EDI message is sent over HTTP/HTTPS transport in asynchronous mode, you must create a send port to return the MDN separately.</span></span> <span data-ttu-id="38f08-144">如果它是動態傳送埠，就會使用訊息標頭內 Receipt-Delivery-Notification 一行中的位址，將訊息傳送到交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="38f08-144">If it is a dynamic send port, it will use the address in the Receipt-Delivery-Notification line in the header of the message to route the message to the trading partner.</span></span> <span data-ttu-id="38f08-145">如果它是靜態傳送埠，則會使用連接埠屬性中定義的位址。</span><span class="sxs-lookup"><span data-stu-id="38f08-145">If it is a static send port, it will use the address defined in port properties.</span></span> <span data-ttu-id="38f08-146">這個傳送埠會使用 `EdiIntAS.IsAS2AsynchronousMDN==True` 篩選運算式，訂閱非同步的 MDN。</span><span class="sxs-lookup"><span data-stu-id="38f08-146">This send port subscribes to the asynchronous MDN by using an `EdiIntAS.IsAS2AsynchronousMDN==True` filter expression.</span></span> <span data-ttu-id="38f08-147">在非同步處理作業中，除了 MDN 之外，AS2Receive 管線還會產生 HTTP 回應。</span><span class="sxs-lookup"><span data-stu-id="38f08-147">In asynchronous processing, the AS2Receive pipeline will generate an HTTP response in addition to the MDN.</span></span> <span data-ttu-id="38f08-148">接收埠會透過接收埠與傳送合作對象之間的 HTTP 連線，將 HTTP 回應傳回給原始傳送者，以便關閉該連線。</span><span class="sxs-lookup"><span data-stu-id="38f08-148">The receive port returns the HTTP response to the original sender over the HTTP connection between the receive port and the sending party, which closes that connection.</span></span> <span data-ttu-id="38f08-149">因為 MDN 不會關閉同步連線，所以這是必要的動作。</span><span class="sxs-lookup"><span data-stu-id="38f08-149">This is necessary because the synchronous connection is not closed by the MDN.</span></span>  
  
##  <a name="BKMK_NonEDI"></a><span data-ttu-id="38f08-150">處理收到的非 EDI 內容</span><span class="sxs-lookup"><span data-stu-id="38f08-150">Processing the Received Non-EDI Payload</span></span>  
 <span data-ttu-id="38f08-151">若是收到透過 AS2 的非 EDI 編碼訊息，而且需要對該內容執行解譯時，您就必須在不同於 AS2Receive 管線的接收管線中進行解譯。</span><span class="sxs-lookup"><span data-stu-id="38f08-151">When a message that is not encoded in EDI is received over AS2, and you need to perform disassembly on the payload, you will have to do that in a different receive pipeline than the AS2Receive pipeline.</span></span> <span data-ttu-id="38f08-152">這是必要的做法，因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只允許一個接收管線中存在一個解譯器。</span><span class="sxs-lookup"><span data-stu-id="38f08-152">This is required because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] only allows one disassembler in a receive pipeline.</span></span> <span data-ttu-id="38f08-153">這種實例將需要使用傳送埠和接收位置的回送機制。</span><span class="sxs-lookup"><span data-stu-id="38f08-153">This scenario will require a loopback mechanism using a send port and receive location.</span></span> <span data-ttu-id="38f08-154">在第一個階段中，EDIReceive 管線處理 AS2 訊息，並以其原生格式來傳送訊息到 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="38f08-154">In the first pass, the EDIReceive pipeline processes the AS2 message and sends the message in its native format to the MessageBox.</span></span> <span data-ttu-id="38f08-155">在第二次傳遞中，接收管線會從訊息的原生格式產生 XML。</span><span class="sxs-lookup"><span data-stu-id="38f08-155">In the second pass, a receive pipeline generates XML from the message's native format.</span></span>  
  
 <span data-ttu-id="38f08-156">BizTalk Server 將會對透過 AS2 傳送的非 EDI 訊息執行下列接收端處理：</span><span class="sxs-lookup"><span data-stu-id="38f08-156">BizTalk Server will perform the following receive-side processing on a non-EDI message over AS2 BizTalk Server:</span></span>  
  
-   <span data-ttu-id="38f08-157">與雙向要求回應接收位置關聯的 AS2Receive 接收管線會剖析非 EDI 訊息的 AS2 標頭，然後將非 EDI 訊息路由至 BizTalk MessageBox。</span><span class="sxs-lookup"><span data-stu-id="38f08-157">The AS2Receive receive pipeline associated with the two-way request response receive location parses the AS2 headers from the non-EDI message, and then routes the non-EDI message to the BizTalk MessageBox.</span></span>  
  
-   <span data-ttu-id="38f08-158">回送傳送埠 (可以是 FILE 或 MSMQ) 會從 MessageBox 擷取非 EDI 訊息，因為它會對 BizTalk 屬性 `IsAS2PayloadMessage == True` 加以篩選。</span><span class="sxs-lookup"><span data-stu-id="38f08-158">A loopback send port (either FILE or MSMQ) picks the non-EDI message up from the MessageBox, because it filters on the BizTalk property `IsAS2PayloadMessage == True`.</span></span> <span data-ttu-id="38f08-159">與此傳送埠關聯的 PassThruTransmit 傳送管線，則會以非 EDI 格式將訊息傳遞下去，進而將訊息路由至資料夾或 MSMQ 佇列。</span><span class="sxs-lookup"><span data-stu-id="38f08-159">The PassThruTransmit send pipeline associated with this send port passes the message through in its non-EDI format, routing the message to either a folder or an MSMQ queue.</span></span>  
  
-   <span data-ttu-id="38f08-160">回送接收位置會擷取訊息。</span><span class="sxs-lookup"><span data-stu-id="38f08-160">A loopback receive location picks up the message.</span></span> <span data-ttu-id="38f08-161">與回送接收位置關聯的接收管線會從非 EDI 訊息產生 XML 訊息，並會將其路由至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="38f08-161">The receive pipeline associated with the loopback receive location generates an XML message from the non-EDI message, and routes it to the MessageBox.</span></span>  
  
-   <span data-ttu-id="38f08-162">如果訊息要傳送到後端應用程式，傳送埠會擷取 XML 訊息，並將它傳送到該應用程式。</span><span class="sxs-lookup"><span data-stu-id="38f08-162">If the message is to be routed to a back-end application, a send port picks up the XML message and routes it to the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f08-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38f08-163">See Also</span></span>  
 <span data-ttu-id="38f08-164">[BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="38f08-164">[How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md) </span></span>  
 [<span data-ttu-id="38f08-165">透過 AS2 外寄 EDI 訊息的傳送端處理</span><span class="sxs-lookup"><span data-stu-id="38f08-165">Send-Side Processing of an Outgoing EDI Message over AS2</span></span>](../core/send-side-processing-of-an-outgoing-edi-message-over-as2.md)