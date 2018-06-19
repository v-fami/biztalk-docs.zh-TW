---
title: 外寄 EDI 訊息處理透過 AS2 傳送端 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dfb63b22-6e2e-4d4f-b028-301c8d4d53b0
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b893f7a5732bf204764bf7377ee39a8e628f3747
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271870"
---
# <a name="send-side-processing-of-an-outgoing-edi-message-over-as2"></a><span data-ttu-id="b06f6-102">透過 AS2 外寄之 EDI 訊息的傳送端處理</span><span class="sxs-lookup"><span data-stu-id="b06f6-102">Send-Side Processing of an Outgoing EDI Message over AS2</span></span>
<span data-ttu-id="b06f6-103">透過 AS2 外寄之 EDI 訊息的傳送端處理的作業，包括透過 EDI 內容來傳送 AS2 訊息，以及接收 MDN 和 EDI 通知 (若已啟用)。</span><span class="sxs-lookup"><span data-stu-id="b06f6-103">Send-side processing of an EDI message over AS2 includes sending an AS2 message with the EDI payload and receiving MDN and EDI acknowledgments (if enabled).</span></span>  
  
 <span data-ttu-id="b06f6-104">AS2EDISend 傳送管線會透過 HTTP/HTTPS，將組合的 EDI/AS2 訊息傳送至接收端的交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="b06f6-104">The AS2EDISend send pipeline sends an assembled EDI/AS2 message to the receiving trading partner over HTTP/HTTPS.</span></span> <span data-ttu-id="b06f6-105">AS2EDIReceive 接收管線會接收為了回應 AS2 訊息而傳回的 MDN，以及為了回應 EDI 訊息而傳回的 EDI 通知。</span><span class="sxs-lookup"><span data-stu-id="b06f6-105">The AS2EDIReceive receive pipeline receives an MDN returned in response to the AS2 message, and an EDI acknowledgment returned in response to the EDI message.</span></span> <span data-ttu-id="b06f6-106">這些管線每一個都會處理 AS2 訊息，並處理 AS2 訊息內的 EDI 內容。</span><span class="sxs-lookup"><span data-stu-id="b06f6-106">Each of these pipelines processes an AS2 message and processes the EDI payload within an AS2 message.</span></span> <span data-ttu-id="b06f6-107">您可以將這些管線包含在 HTTP 雙向請求-回應傳送埠中，或是單向的 HTTP 傳送埠和單向的 HTTP 接收埠中。</span><span class="sxs-lookup"><span data-stu-id="b06f6-107">You can include these pipelines in an HTTP two-way solicit response send port, or in a one-way HTTP send port and a one-way HTTP receive port.</span></span>  
  
 <span data-ttu-id="b06f6-108">為了透過 AS2 傳送 EDI 交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b06f6-108">To send an EDI interchange over AS2, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will perform the following steps:</span></span>  
  
-   <span data-ttu-id="b06f6-109">處理要傳送的 EDI 內容</span><span class="sxs-lookup"><span data-stu-id="b06f6-109">Processing the EDI payload for sending</span></span>  
  
-   <span data-ttu-id="b06f6-110">傳送 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="b06f6-110">Sending the AS2 message</span></span>  
  
-   <span data-ttu-id="b06f6-111">接收傳回的 MDN</span><span class="sxs-lookup"><span data-stu-id="b06f6-111">Receiving the returned MDN</span></span>  
  
-   <span data-ttu-id="b06f6-112">接收傳回的 EDI 通知</span><span class="sxs-lookup"><span data-stu-id="b06f6-112">Receiving the returned EDI acknowledgment</span></span>  
  
## <a name="processing-the-edi-payload-for-sending"></a><span data-ttu-id="b06f6-113">處理要傳送的 EDI 內容</span><span class="sxs-lookup"><span data-stu-id="b06f6-113">Processing the EDI Payload for Sending</span></span>  
 <span data-ttu-id="b06f6-114">建立 AS2 訊息之前，AS2EdiSend 管線必須先處理 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="b06f6-114">Before creating an AS2 message, the AS2EdiSend pipeline must process the EDI interchange.</span></span> <span data-ttu-id="b06f6-115">中所述，如果啟用輸出批次處理時，會批次處理交易集[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。</span><span class="sxs-lookup"><span data-stu-id="b06f6-115">If outbound batching is enabled, transaction sets will be batched as described in [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).</span></span> <span data-ttu-id="b06f6-116">EDI 組合器將會建立 EDI 交換中所述[EDI 組合器的運作方式](../core/how-the-edi-assembler-works.md)。</span><span class="sxs-lookup"><span data-stu-id="b06f6-116">The EDI Assembler will create the EDI interchange as described in [How the EDI Assembler Works](../core/how-the-edi-assembler-works.md).</span></span>  
  
## <a name="sending-the-as2-message"></a><span data-ttu-id="b06f6-117">傳送 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="b06f6-117">Sending the AS2 Message</span></span>  
 <span data-ttu-id="b06f6-118">AS2 傳送管線中的 AS2 編碼器會先執行協議解析，以判斷要用來處理外寄訊息的協議屬性。</span><span class="sxs-lookup"><span data-stu-id="b06f6-118">The AS2 Encoder in the AS2 send pipeline first performs agreement resolution to determine the agreement properties to be used to process the outgoing message.</span></span> <span data-ttu-id="b06f6-119">如需詳細資訊，請參閱[外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="b06f6-119">For more information, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).</span></span>  
  
 <span data-ttu-id="b06f6-120">AS2 編碼器會建置傳送 AS2 訊息時所需的一組 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="b06f6-120">The AS2 Encoder builds the set of HTTP headers required to send an AS2 message.</span></span> <span data-ttu-id="b06f6-121">它會將這些標頭加入至 `HTTP.UserHttpHeaders` 內容屬性 (標頭值的單一字串)。</span><span class="sxs-lookup"><span data-stu-id="b06f6-121">It adds these headers to the `HTTP.UserHttpHeaders` context property, which is a single string of header values.</span></span> <span data-ttu-id="b06f6-122">AS2 編碼器會建置下列位在 `HTTP.UserHttpHeaders` 中的 AS2 標頭。</span><span class="sxs-lookup"><span data-stu-id="b06f6-122">The AS2 Encoder builds the following AS2 headers in `HTTP.UserHttpHeaders`.</span></span> <span data-ttu-id="b06f6-123">這些標頭一定會出現在 AS2 訊息中。</span><span class="sxs-lookup"><span data-stu-id="b06f6-123">These headers must be in the AS2 messages.</span></span>  
  
-   <span data-ttu-id="b06f6-124">AS2-To</span><span class="sxs-lookup"><span data-stu-id="b06f6-124">AS2-To</span></span>  
  
-   <span data-ttu-id="b06f6-125">AS2-From</span><span class="sxs-lookup"><span data-stu-id="b06f6-125">AS2-From</span></span>  
  
-   <span data-ttu-id="b06f6-126">AS2-Version</span><span class="sxs-lookup"><span data-stu-id="b06f6-126">AS2-Version</span></span>  
  
-   <span data-ttu-id="b06f6-127">MessageID</span><span class="sxs-lookup"><span data-stu-id="b06f6-127">MessageID</span></span>  
  
-   <span data-ttu-id="b06f6-128">OriginalMessageID (僅適用於 MDN)</span><span class="sxs-lookup"><span data-stu-id="b06f6-128">OriginalMessageID (for MDNs only)</span></span>  
  
 <span data-ttu-id="b06f6-129">如果**要求 MDN**屬性已核取，則管線會將配置通知給、 回條傳遞選項，以及簽章-回條-MICalg AS2 標頭中的訊息中對應的屬性和它的值如果設定以 「 pcks7 簽章 」 之簽署回條通訊協定 AS2 標頭**要求簽署的 MDN**會檢查屬性。</span><span class="sxs-lookup"><span data-stu-id="b06f6-129">If the **Request MDN** property is checked, the pipeline will set the Disposition-Notification-To, Receipt-Delivery-Option, and Signed-Receipt-MICalg AS2 headers in the message to the values in the corresponding properties; and it will set the Signed-Receipt-Protocol AS2 header to "pcks7-signature" if the **Request signed MDN** property is checked.</span></span>  
  
 <span data-ttu-id="b06f6-130">如果 `HTTP.UserHttpHeaders` 內容屬性不存在，AS2 編碼器會建立它。</span><span class="sxs-lookup"><span data-stu-id="b06f6-130">If the `HTTP.UserHttpHeaders` context property does not exist, the AS2 Encoder will create it.</span></span> <span data-ttu-id="b06f6-131">如果 `HTTP.UserHttpHeaders` 已存在，AS2 編碼器就會使用它，而不重新建立它。</span><span class="sxs-lookup"><span data-stu-id="b06f6-131">If `HTTP.UserHttpHeaders` already exists, the AS2 Encoder will use it, rather than creating it.</span></span> <span data-ttu-id="b06f6-132">如果您建立 `HTTP.UserHttpHeaders`，將標頭寫入其中，然後將此內容屬性寫入訊息內容中，AS2 編碼器就會使用這些標頭，而且這些標頭的優先順序高於其他來源的標頭。</span><span class="sxs-lookup"><span data-stu-id="b06f6-132">If you create `HTTP.UserHttpHeaders`, write headers to it, and then write it to the context of the message, the AS2 Encoder will use those headers, and they will take priority over headers from other sources.</span></span> <span data-ttu-id="b06f6-133">唯一的例外是 AS2-From 標頭，它一定是取自協議屬性。</span><span class="sxs-lookup"><span data-stu-id="b06f6-133">The exception to that is the AS2-From header, which is always taken from the agreement properties.</span></span>  
  
 <span data-ttu-id="b06f6-134">如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中，AS2 編碼器會從單一內容屬性加入它。</span><span class="sxs-lookup"><span data-stu-id="b06f6-134">If an AS2 header is not in `HTTP.UserHttpHeaders`, the AS2 Encoder will add it from single context properties.</span></span> <span data-ttu-id="b06f6-135">這表示，您可以藉由將 AS2 標頭升級或寫入訊息內容中，加入 AS2 標頭 (如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中)。</span><span class="sxs-lookup"><span data-stu-id="b06f6-135">This means that you can add AS2 headers by promoting or writing them to the context of the message (if they are not already in `HTTP.UserHttpHeaders`).</span></span> <span data-ttu-id="b06f6-136">如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中，也不是內容中的屬性，AS2 編碼器就會從協議屬性將它加入至 `HTTP.UserHttpHeaders` 中。</span><span class="sxs-lookup"><span data-stu-id="b06f6-136">If an AS2 header is neither in `HTTP.UserHttpHeaders`, nor present as a property in the context, the AS2 Encoder will add it from agreement properties into `HTTP.UserHttpHeaders`.</span></span>  
  
 <span data-ttu-id="b06f6-137">在 AS2 編碼器建置 `HTTP.UserHttpHeaders` 屬性中的標頭之後，它會將此屬性加入訊息的內容中。</span><span class="sxs-lookup"><span data-stu-id="b06f6-137">After the AS2 Encoder builds the headers in the `HTTP.UserHttpHeaders` property, it writes it to the context of the message.</span></span> <span data-ttu-id="b06f6-138">HTTP 配接器會收取 `HTTP.UserHttpHeaders`，並將 `HTTP.UserHttpHeaders` 中的標頭值附加到訊息的前面。</span><span class="sxs-lookup"><span data-stu-id="b06f6-138">The HTTP Adapter picks up `HTTP.UserHttpHeaders`, and prepends the header values from `HTTP.UserHttpHeaders` into the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b06f6-139">AS2 傳輸只適用於 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="b06f6-139">AS2 transport is intended to work only with the HTTP adapter.</span></span> <span data-ttu-id="b06f6-140">不過，如果您手動設定適當的內容屬性，也可以使用 FILE 配接器傳輸 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="b06f6-140">However, if you manually set the appropriate context properties, you can use the FILE Adapter to transport AS2 messages.</span></span> <span data-ttu-id="b06f6-141">如需詳細資訊，請參閱[透過 FILE 傳送埠傳送 AS2 訊息](../core/sending-an-as2-message-over-a-file-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="b06f6-141">For more information, see [Sending an AS2 Message over a FILE Send Port](../core/sending-an-as2-message-over-a-file-send-port.md).</span></span>  
  
## <a name="processing-the-returned-mdn"></a><span data-ttu-id="b06f6-142">處理傳回的 MDN</span><span class="sxs-lookup"><span data-stu-id="b06f6-142">Processing the Returned MDN</span></span>  
 <span data-ttu-id="b06f6-143">如果 MDN 已啟用，與雙向傳送埠相關聯的接收管線就會從接收 AS2 訊息的合作對象接收 MDN。</span><span class="sxs-lookup"><span data-stu-id="b06f6-143">If an MDN is enabled, the receive pipeline associated with the two-way send port receives the MDN from the party that receives the AS2 message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b06f6-144">如需 AS2 傳送管線對內送 Mdn 執行處理的詳細資訊，請參閱[傳送外寄 MDN](../core/sending-an-outgoing-mdn.md)。</span><span class="sxs-lookup"><span data-stu-id="b06f6-144">For more information about the processing that the AS2 send pipelines perform on incoming MDNs, see [Sending an Outgoing MDN](../core/sending-an-outgoing-mdn.md).</span></span>  
  
## <a name="processing-the-returned-edi-acknowledgment"></a><span data-ttu-id="b06f6-145">處理傳回的 EDI 通知</span><span class="sxs-lookup"><span data-stu-id="b06f6-145">Processing the Returned EDI Acknowledgment</span></span>  
 <span data-ttu-id="b06f6-146">如果 EDI 通知已啟用，與雙向傳送埠相關聯的接收管線也會從 EDI 訊息接收者接收 EDI 通知 (因為它會篩選 BizTalk EDI 通知訊息類型)。</span><span class="sxs-lookup"><span data-stu-id="b06f6-146">If an EDI acknowledgment is enabled, the receive pipeline associated with the two-way send port also receives an EDI acknowledgment from the receiver of the EDI message (because it filters on the BizTalk EDI ACK message type).</span></span> <span data-ttu-id="b06f6-147">如需詳細資訊，請參閱[處理收到的通知](../core/processing-a-received-acknowledgment.md)。</span><span class="sxs-lookup"><span data-stu-id="b06f6-147">For more information, see [Processing a Received Acknowledgment](../core/processing-a-received-acknowledgment.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06f6-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b06f6-148">See Also</span></span>  
 [<span data-ttu-id="b06f6-149">BizTalk Server 傳送 AS2 訊息的方式</span><span class="sxs-lookup"><span data-stu-id="b06f6-149">How BizTalk Server Sends AS2 Messages</span></span>](../core/how-biztalk-server-sends-as2-messages.md)