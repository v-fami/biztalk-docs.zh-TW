---
title: 傳送端處理透過 AS2 外寄非 EDI 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3f19b7df-fe6d-4105-8a44-3d6db0bba451
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 537ff8147d42bce1db7135f38b9b9c5c8f1f160e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987999"
---
# <a name="send-side-processing-of-an-outgoing-non-edi-message-over-as2"></a><span data-ttu-id="5c1da-102">透過 AS2 從傳送端處理外寄非 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="5c1da-102">Send-Side Processing of an Outgoing Non-EDI Message over AS2</span></span>
<span data-ttu-id="5c1da-103">隨附於 AS2 管線[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可用來處理透過 AS2 傳輸的 EDI 訊息或非 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="5c1da-103">The AS2 pipelines shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be used to process an EDI message or a non-EDI message over AS2 transport.</span></span> <span data-ttu-id="5c1da-104">這兩種不同的內容類型會使用不同的管線。</span><span class="sxs-lookup"><span data-stu-id="5c1da-104">Different pipelines are used for the two different types of payloads.</span></span> <span data-ttu-id="5c1da-105">您會使用 AS2EdiSend 管線來處理透過 AS2 外寄的 EDI 訊息，而使用 AS2Receive 管線接收關聯的 MDN (如果有啟用)。</span><span class="sxs-lookup"><span data-stu-id="5c1da-105">You use the AS2EdiSend pipeline to process an outgoing EDI message over AS2, and the AS2Receive pipeline to receive the associated MDN (if enabled).</span></span> <span data-ttu-id="5c1da-106">您會使用 AS2Send 管線來處理透過 AS2 外寄的非 EDI 訊息，而使用 AS2Receive 管線接收關聯的 MDN (如果有啟用)。</span><span class="sxs-lookup"><span data-stu-id="5c1da-106">You use the AS2Send pipeline to process an outgoing non-EDI message over AS2, and the AS2Receive pipeline to receive the associated MDN (if enabled).</span></span> <span data-ttu-id="5c1da-107">非 EDI 訊息可以是任何二進位內容。</span><span class="sxs-lookup"><span data-stu-id="5c1da-107">The non-EDI message can be any binary payload.</span></span>  
  
 <span data-ttu-id="5c1da-108">AS2Send 管線會組合非 EDI 內容並解譯 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="5c1da-108">The AS2Send send pipeline assembles the non-EDI payload and encodes the AS2 message.</span></span> <span data-ttu-id="5c1da-109">AS2Receive 接收管線則會解譯 MDN 回應。</span><span class="sxs-lookup"><span data-stu-id="5c1da-109">The AS2Receive receive pipeline decodes the MDN response.</span></span> <span data-ttu-id="5c1da-110">您可以將這些管線包含在 HTTP 雙向請求-回應傳送埠 (適用同步的 MDN) 中，或是單向的 HTTP 傳送埠和單向的 HTTP 接收埠 (適用非同步的 MDN) 中。</span><span class="sxs-lookup"><span data-stu-id="5c1da-110">You can include these pipelines in an HTTP two-way solicit response send port (for synchronous MDNs), or in a one-way HTTP send port and a one-way HTTP receive port (for asynchronous MDNs).</span></span>  
  
 <span data-ttu-id="5c1da-111">為了透過 AS2 傳送 EDI 交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="5c1da-111">To send an EDI interchange over AS2, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will perform the following steps:</span></span>  
  
-   <span data-ttu-id="5c1da-112">處理要傳送的非 EDI 內容</span><span class="sxs-lookup"><span data-stu-id="5c1da-112">Processing the non-EDI payload for sending</span></span>  
  
-   <span data-ttu-id="5c1da-113">傳送 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="5c1da-113">Sending the AS2 message</span></span>  
  
-   <span data-ttu-id="5c1da-114">接收傳回的 MDN</span><span class="sxs-lookup"><span data-stu-id="5c1da-114">Receiving the returned MDN</span></span>  
  
## <a name="processing-the-non-edi-payload-for-sending"></a><span data-ttu-id="5c1da-115">處理要傳送的非 EDI 內容</span><span class="sxs-lookup"><span data-stu-id="5c1da-115">Processing the Non-EDI Payload for Sending</span></span>  
 <span data-ttu-id="5c1da-116">在建立 AS2 訊息之前，傳送埠必須使用適當的篩選條件運算式訂閱訊息，藉此選取非 EDI 內容。</span><span class="sxs-lookup"><span data-stu-id="5c1da-116">Before creating the AS2 message, a send port must pick up the non-EDI payload, using an appropriate filter expression to subscribe to the messages.</span></span> <span data-ttu-id="5c1da-117">根據 MDN 將會是同步或非同步而定，您可以使用雙向傳送埠或單向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="5c1da-117">You can use a two-way send port or a one-way send port, depending upon whether the MDN will be synchronous or asynchronous.</span></span> <span data-ttu-id="5c1da-118">接著 AS2Send 管線會將非 EDI 內容處理為 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="5c1da-118">The AS2Send pipeline will then process the non-EDI payload into an AS2 message.</span></span>  
  
## <a name="sending-the-as2-message"></a><span data-ttu-id="5c1da-119">傳送 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="5c1da-119">Sending the AS2 Message</span></span>  
 <span data-ttu-id="5c1da-120">AS2 傳送管線中的 AS2 編碼器會先執行協議解析，以判斷要用來處理外寄訊息的協議屬性。</span><span class="sxs-lookup"><span data-stu-id="5c1da-120">The AS2 Encoder in the AS2 send pipeline first performs agreement resolution to determine the agreement properties to be used to process the outgoing message.</span></span> <span data-ttu-id="5c1da-121">如需詳細資訊，請參閱 <<c0> [ 外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="5c1da-121">For more information, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).</span></span>  
  
 <span data-ttu-id="5c1da-122">AS2 編碼器會建置傳送 AS2 訊息時所需的一組 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="5c1da-122">The AS2 Encoder builds the set of HTTP headers required to send an AS2 message.</span></span> <span data-ttu-id="5c1da-123">它會將這些標頭加入至 `HTTP.UserHttpHeaders` 內容屬性 (標頭值的單一字串)。</span><span class="sxs-lookup"><span data-stu-id="5c1da-123">It adds these headers to the `HTTP.UserHttpHeaders` context property, which is a single string of header values.</span></span> <span data-ttu-id="5c1da-124">AS2 編碼器會建置下列位在 HTTP.UserHttpHeaders 中的 AS2 標頭。</span><span class="sxs-lookup"><span data-stu-id="5c1da-124">The AS2 Encoder builds the following AS2 headers in HTTP.UserHttpHeaders.</span></span> <span data-ttu-id="5c1da-125">這些標頭一定會出現在 AS2 訊息中。</span><span class="sxs-lookup"><span data-stu-id="5c1da-125">These headers must be in the AS2 messages.</span></span>  
  
- <span data-ttu-id="5c1da-126">AS2-To</span><span class="sxs-lookup"><span data-stu-id="5c1da-126">AS2-To</span></span>  
  
- <span data-ttu-id="5c1da-127">AS2-From</span><span class="sxs-lookup"><span data-stu-id="5c1da-127">AS2-From</span></span>  
  
- <span data-ttu-id="5c1da-128">AS2-Version</span><span class="sxs-lookup"><span data-stu-id="5c1da-128">AS2-Version</span></span>  
  
- <span data-ttu-id="5c1da-129">MessageID</span><span class="sxs-lookup"><span data-stu-id="5c1da-129">MessageID</span></span>  
  
- <span data-ttu-id="5c1da-130">OriginalMessageID (僅適用於 MDN)</span><span class="sxs-lookup"><span data-stu-id="5c1da-130">OriginalMessageID (for MDNs only)</span></span>  
  
  <span data-ttu-id="5c1da-131">如果**的 要求 MDN**會檢查屬性，管線會將設定配置通知給、 回條傳遞選項，以及簽署-回條-MICalg AS2 標頭，訊息中對應的屬性，以及它的值中如果設定為"pcks7-signature"簽署回條通訊協定 AS2 標頭**要求簽署的 MDN**會檢查屬性。</span><span class="sxs-lookup"><span data-stu-id="5c1da-131">If the **Request MDN** property is checked, the pipeline will set the Disposition-Notification-To, Receipt-Delivery-Option, and Signed-Receipt-MICalg AS2 headers in the message to the values in the corresponding properties; and it will set the Signed-Receipt-Protocol AS2 header to "pcks7-signature" if the **Request signed MDN** property is checked.</span></span>  
  
  <span data-ttu-id="5c1da-132">如果 `HTTP.UserHttpHeaders` 內容屬性不存在，AS2 編碼器會建立它。</span><span class="sxs-lookup"><span data-stu-id="5c1da-132">If the `HTTP.UserHttpHeaders` context property does not exist, the AS2 Encoder will create it.</span></span> <span data-ttu-id="5c1da-133">如果 `HTTP.UserHttpHeaders` 已存在，AS2 編碼器就會使用它，而不重新建立它。</span><span class="sxs-lookup"><span data-stu-id="5c1da-133">If `HTTP.UserHttpHeaders` already exists, the AS2 Encoder will use it, rather than creating it.</span></span> <span data-ttu-id="5c1da-134">如果您建立 `HTTP.UserHttpHeaders`，將標頭寫入其中，然後將此內容屬性寫入訊息內容中，AS2 編碼器就會使用這些標頭，而且這些標頭的優先順序高於其他來源的標頭。</span><span class="sxs-lookup"><span data-stu-id="5c1da-134">If you create `HTTP.UserHttpHeaders`, write headers to it, and then write it to the context of the message, the AS2 Encoder will use those headers, and they will take priority over headers from other sources.</span></span> <span data-ttu-id="5c1da-135">唯一的例外是 AS2-From 標頭，它一定是取自協議屬性。</span><span class="sxs-lookup"><span data-stu-id="5c1da-135">The exception to that is the AS2-From header, which is always taken from the agreement properties.</span></span>  
  
  <span data-ttu-id="5c1da-136">如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中，AS2 編碼器會從單一內容屬性加入它。</span><span class="sxs-lookup"><span data-stu-id="5c1da-136">If an AS2 header is not in `HTTP.UserHttpHeaders`, the AS2 Encoder will add it from single context properties.</span></span> <span data-ttu-id="5c1da-137">這表示，您可以藉由將 AS2 標頭升級或寫入訊息內容中，加入 AS2 標頭 (如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中)。</span><span class="sxs-lookup"><span data-stu-id="5c1da-137">This means that you can add AS2 headers by promoting or writing them to the context of the message (if they are not already in `HTTP.UserHttpHeaders`).</span></span> <span data-ttu-id="5c1da-138">如果 AS2 標頭不在 `HTTP.UserHttpHeaders` 中，也不是內容中的屬性，AS2 編碼器就會從協議屬性將它加入至 `HTTP.UserHttpHeaders` 中。</span><span class="sxs-lookup"><span data-stu-id="5c1da-138">If an AS2 header is neither in `HTTP.UserHttpHeaders`, nor present as a property in the context, the AS2 Encoder will add it from agreement properties into `HTTP.UserHttpHeaders`.</span></span>  
  
  <span data-ttu-id="5c1da-139">在 AS2 編碼器建置 `HTTP.UserHttpHeaders` 屬性中的標頭之後，它會將此屬性加入訊息的內容中。</span><span class="sxs-lookup"><span data-stu-id="5c1da-139">After the AS2 Encoder builds the headers in the `HTTP.UserHttpHeaders` property, it writes it to the context of the message.</span></span> <span data-ttu-id="5c1da-140">HTTP 配接器會收取 `HTTP.UserHttpHeaders`，並將 `HTTP.UserHttpHeaders` 中的標頭值附加到訊息的前面。</span><span class="sxs-lookup"><span data-stu-id="5c1da-140">The HTTP Adapter picks up `HTTP.UserHttpHeaders`, and prepends the header values from `HTTP.UserHttpHeaders` into the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c1da-141">AS2 傳輸只適用於 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="5c1da-141">AS2 transport is intended to work only with the HTTP adapter.</span></span> <span data-ttu-id="5c1da-142">不過，如果您手動設定適當的內容屬性，也可以使用 FILE 配接器傳輸 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="5c1da-142">However, if you manually set the appropriate context properties, you can use the FILE Adapter to transport AS2 messages.</span></span> <span data-ttu-id="5c1da-143">如需詳細資訊，請參閱 <<c0> [ 透過 FILE 傳送埠傳送 AS2 訊息](../core/sending-an-as2-message-over-a-file-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="5c1da-143">For more information, see [Sending an AS2 Message over a FILE Send Port](../core/sending-an-as2-message-over-a-file-send-port.md).</span></span>  
  
## <a name="processing-the-returned-mdn"></a><span data-ttu-id="5c1da-144">處理傳回的 MDN</span><span class="sxs-lookup"><span data-stu-id="5c1da-144">Processing the Returned MDN</span></span>  
 <span data-ttu-id="5c1da-145">如果 MDN 已啟用，與雙向傳送埠相關聯的接收管線就會從接收 AS2 訊息的合作對象接收 MDN。</span><span class="sxs-lookup"><span data-stu-id="5c1da-145">If an MDN is enabled, the receive pipeline associated with the two-way send port receives the MDN from the party that receives the AS2 message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c1da-146">如需有關 AS2 傳送管線對內送 Mdn 執行處理的詳細資訊，請參閱[傳送外寄 MDN](../core/sending-an-outgoing-mdn.md)。</span><span class="sxs-lookup"><span data-stu-id="5c1da-146">For more information about the processing that the AS2 send pipelines perform on incoming MDNs, see [Sending an Outgoing MDN](../core/sending-an-outgoing-mdn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c1da-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c1da-147">See Also</span></span>  
 [<span data-ttu-id="5c1da-148">BizTalk Server 如何傳送 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="5c1da-148">How BizTalk Server Sends AS2 Messages</span></span>](../core/how-biztalk-server-sends-as2-messages.md)