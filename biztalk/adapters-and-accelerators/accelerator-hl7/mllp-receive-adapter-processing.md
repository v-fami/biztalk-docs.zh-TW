---
title: "MLLP 的接收配接器處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, receive adapters
- MLLP adapters, send adapters
- receive adapters
ms.assetid: 03c9a5f6-6f23-454f-8bab-e7c7b6057efa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28713e22c37c12ef6f2cb9f8df8d228759d00c8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mllp-receive-adapter-processing"></a><span data-ttu-id="753d6-102">MLLP 的接收配接器處理</span><span class="sxs-lookup"><span data-stu-id="753d6-102">MLLP Receive Adapter Processing</span></span>
<span data-ttu-id="753d6-103">最小的較低層通訊協定 (MLLP) 接收配接器支援這兩個單向和雙向要求回應模式。</span><span class="sxs-lookup"><span data-stu-id="753d6-103">The Minimal Lower Layer Protocol (MLLP) receive adapter supports both one-way and two-way request response modes.</span></span> <span data-ttu-id="753d6-104">配接器會接聽並接受連線。</span><span class="sxs-lookup"><span data-stu-id="753d6-104">The adapter listens and accepts connections.</span></span>  
  
 <span data-ttu-id="753d6-105">當 MLLP 的接收配接器仍會雙向模式運作，配接器不會收到一封新郵件來自連接直到管線已產生通知 (ACK) 的前一個訊息。</span><span class="sxs-lookup"><span data-stu-id="753d6-105">When the MLLP receive adapter operates in two-way mode, the adapter will not receive a new message from the connection until the pipeline has generated the acknowledgment (ACK) for the previous message.</span></span>  
  
## <a name="configuration-parameters"></a><span data-ttu-id="753d6-106">組態參數</span><span class="sxs-lookup"><span data-stu-id="753d6-106">Configuration Parameters</span></span>  
 <span data-ttu-id="753d6-107">接收處理常式的參數在 BizTalk 主控件層級設定，而且適用於所有與它相關聯的 MLLP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="753d6-107">The parameters for a receive handler are configured at the BizTalk Host level, and apply to all MLLP receive locations associated with it.</span></span>  
  
|<span data-ttu-id="753d6-108">參數</span><span class="sxs-lookup"><span data-stu-id="753d6-108">Parameter</span></span>|<span data-ttu-id="753d6-109">使用</span><span class="sxs-lookup"><span data-stu-id="753d6-109">Use</span></span>|  
|---------------|---------|  
|<span data-ttu-id="753d6-110">*最大接受連線限制*</span><span class="sxs-lookup"><span data-stu-id="753d6-110">*Max Accept Connection Limit*</span></span>|<span data-ttu-id="753d6-111">限制並行接收配接器將會接受的開啟連接數目。</span><span class="sxs-lookup"><span data-stu-id="753d6-111">Limits the number of concurrent open connections that the receive adapter will accept.</span></span>|  
  
## <a name="acknowledgments-with-the-two-way-mllp-receive-adapter"></a><span data-ttu-id="753d6-112">與雙向 MLLP 通知接收配接器</span><span class="sxs-lookup"><span data-stu-id="753d6-112">Acknowledgments with the two-way MLLP receive adapter</span></span>  
 <span data-ttu-id="753d6-113">當收到雙向 MLLP 配接器接收訊息時， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 可以產生下列類型的通知：</span><span class="sxs-lookup"><span data-stu-id="753d6-113">When a two-way MLLP receive adapter receives a message, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) can generate the following types of ACKs:</span></span>  
  
-   <span data-ttu-id="753d6-114">HL7 增強認可 ACK： 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送相同的連接上認可的通知。</span><span class="sxs-lookup"><span data-stu-id="753d6-114">HL7 Enhanced Commit ACK: In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends a Commit ACK on the same connection.</span></span> <span data-ttu-id="753d6-115">它會送出不同的傳送埠上的應用程式接受通知。</span><span class="sxs-lookup"><span data-stu-id="753d6-115">It sends out an Application Accept ACK on a different send port.</span></span>  
  
-   <span data-ttu-id="753d6-116">應用程式接受 ACK： 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送相同的連接上的應用程式接受通知。</span><span class="sxs-lookup"><span data-stu-id="753d6-116">Application Accept ACK: In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an Application Accept ACK on the same connection.</span></span>  
  
-   <span data-ttu-id="753d6-117">靜態 ACK: 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]相同的連接上傳送的通知。</span><span class="sxs-lookup"><span data-stu-id="753d6-117">Static ACK: In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK on the same connection.</span></span>  
  
-   <span data-ttu-id="753d6-118">產生的通知類型取決於[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管設定之合作對象傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="753d6-118">The type of ACK generated depends on the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer settings for the party sending the message.</span></span> <span data-ttu-id="753d6-119">值欄位 MSH 15 16 個別訊息可以覆寫此設定。</span><span class="sxs-lookup"><span data-stu-id="753d6-119">The value in fields MSH 15 and 16 of an individual message can override this setting.</span></span> <span data-ttu-id="753d6-120">不過，對於應用程式必須是靜態的 Ack，組態可以只能透過設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。</span><span class="sxs-lookup"><span data-stu-id="753d6-120">However, for applications expecting Static ACKs, the configuration can only be set through [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="error-conditions"></a><span data-ttu-id="753d6-121">錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="753d6-121">Error Conditions</span></span>  
 <span data-ttu-id="753d6-122">錯誤狀況或非使用狀態時，就會發生下列事件：</span><span class="sxs-lookup"><span data-stu-id="753d6-122">The following events occur when there is an error condition or inactivity:</span></span>  
  
-   <span data-ttu-id="753d6-123">如果已停用接收位置或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]關閉，則發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="753d6-123">If the receive location is disabled or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] shuts down, the following occurs:</span></span>  
  
    -   <span data-ttu-id="753d6-124">接收位置不再接受新連線。</span><span class="sxs-lookup"><span data-stu-id="753d6-124">The receive location will no longer accept new connections.</span></span>  
  
    -   <span data-ttu-id="753d6-125">對於現有的連線，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]完全接收目前的訊息，並關閉連線。</span><span class="sxs-lookup"><span data-stu-id="753d6-125">For existing connections, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] completely receives the current message, and then closes the connection.</span></span>  
  
-   <span data-ttu-id="753d6-126">偵測到無活動時 （在指定的逾時時間內接收位置接收到沒有承載資料），配接器關閉連接。</span><span class="sxs-lookup"><span data-stu-id="753d6-126">When inactivity is detected (no payload data received on the receive location within the specified timeout), the adapter closes the connection.</span></span>  
  
-   <span data-ttu-id="753d6-127">如果[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]收到不完整的訊息時，收到的部分會暫停。</span><span class="sxs-lookup"><span data-stu-id="753d6-127">If [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receives an incomplete message, the portion received is suspended.</span></span> <span data-ttu-id="753d6-128">收到的訊息 （之前在新的連接，EB/CR 和 SB 的下一個訊息之間的第一個 SB) 之外的所有位元組都會被都忽略。</span><span class="sxs-lookup"><span data-stu-id="753d6-128">All bytes received outside of a message (before the first SB on a new connection, between EB/CR and SB of the next message) are ignored.</span></span>  
  
-   <span data-ttu-id="753d6-129">如果管線無法剖析訊息，訊息仍會傳遞至 MessageBox 資料庫，與升級屬性**ParseError = true**。</span><span class="sxs-lookup"><span data-stu-id="753d6-129">If the pipeline fails to parse the message, the message is still delivered to the MessageBox database, with a promoted property **ParseError=true**.</span></span>  
  
-   <span data-ttu-id="753d6-130">如果訊息失敗，因為沒有訂用帳戶，或因結構錯誤，在頁首中，而[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]擱置訊息的原始 「 纜線 」 形式 （如果之前正在剖析）。</span><span class="sxs-lookup"><span data-stu-id="753d6-130">If a message fails due to the absence of a subscription, or due to structural errors in the header, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] suspends the message in its original "wire" form (prior to being parsed).</span></span> <span data-ttu-id="753d6-131">否-訂用帳戶失敗的常見原因是缺少的升級屬性。</span><span class="sxs-lookup"><span data-stu-id="753d6-131">A frequent reason for the no-subscription failure is the lack of promoted properties.</span></span> <span data-ttu-id="753d6-132">因為[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]擱置未剖析的訊息， **BTS。MessageType**會是空白。</span><span class="sxs-lookup"><span data-stu-id="753d6-132">Since [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] suspends the unparsed message, the **BTS.MessageType** will be blank.</span></span>  
  
 <span data-ttu-id="753d6-133">下表列出 MLLP 的接收配接器傳回的錯誤。</span><span class="sxs-lookup"><span data-stu-id="753d6-133">The following table lists the errors that the MLLP receive adapter returns.</span></span>  
  
|<span data-ttu-id="753d6-134">事件</span><span class="sxs-lookup"><span data-stu-id="753d6-134">Event</span></span>|<span data-ttu-id="753d6-135">ID</span><span class="sxs-lookup"><span data-stu-id="753d6-135">ID</span></span>|<span data-ttu-id="753d6-136">錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="753d6-136">Error Condition</span></span>|  
|-----------|--------|---------------------|  
|<span data-ttu-id="753d6-137">**ErrorListening**</span><span class="sxs-lookup"><span data-stu-id="753d6-137">**ErrorListening**</span></span>|<span data-ttu-id="753d6-138">8448</span><span class="sxs-lookup"><span data-stu-id="753d6-138">8448</span></span>|<span data-ttu-id="753d6-139">無法繫結到本機通訊端 （可能有其他本機應用程式正在使用相同的 IP 位址/連接埠編號組合）。</span><span class="sxs-lookup"><span data-stu-id="753d6-139">Could not bind to a local socket (most likely some other local application is using the same IP address/port ID combination).</span></span>|  
|<span data-ttu-id="753d6-140">**ErrorAcceptingConnection**</span><span class="sxs-lookup"><span data-stu-id="753d6-140">**ErrorAcceptingConnection**</span></span>|<span data-ttu-id="753d6-141">8449</span><span class="sxs-lookup"><span data-stu-id="753d6-141">8449</span></span>|<span data-ttu-id="753d6-142">無法建立與遠端合作對象的 TCP 連接。</span><span class="sxs-lookup"><span data-stu-id="753d6-142">Could not establish a TCP connection with the remote party.</span></span> <span data-ttu-id="753d6-143">任一[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]達到最大連接，或資源不足。</span><span class="sxs-lookup"><span data-stu-id="753d6-143">Either [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] reached the maximum connection limit, or the resources were insufficient.</span></span>|  
|<span data-ttu-id="753d6-144">**ErrorSubmittingMessage**</span><span class="sxs-lookup"><span data-stu-id="753d6-144">**ErrorSubmittingMessage**</span></span>|<span data-ttu-id="753d6-145">8452</span><span class="sxs-lookup"><span data-stu-id="753d6-145">8452</span></span>|<span data-ttu-id="753d6-146">MessageBox 資料庫無法接受訊息。</span><span class="sxs-lookup"><span data-stu-id="753d6-146">The MessageBox database could not accept the message.</span></span> <span data-ttu-id="753d6-147">任一[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]已無法使用或資源不足。</span><span class="sxs-lookup"><span data-stu-id="753d6-147">Either [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] was unavailable or the resources were insufficient.</span></span>|  
|<span data-ttu-id="753d6-148">**ErrorSendingAck**</span><span class="sxs-lookup"><span data-stu-id="753d6-148">**ErrorSendingAck**</span></span>|<span data-ttu-id="753d6-149">8454</span><span class="sxs-lookup"><span data-stu-id="753d6-149">8454</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="753d6-150">無法傳回通知，因為連線無法使用。</span><span class="sxs-lookup"><span data-stu-id="753d6-150"> could not return the acknowledgment because the connection was not available.</span></span>|  
  
## <a name="performance-counters"></a><span data-ttu-id="753d6-151">效能計數器</span><span class="sxs-lookup"><span data-stu-id="753d6-151">Performance Counters</span></span>  
 <span data-ttu-id="753d6-152">下表列出 MLLP 配接器會使用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="753d6-152">The following table lists the performance counters that the MLLP adapter uses.</span></span>  
  
|<span data-ttu-id="753d6-153">計數器</span><span class="sxs-lookup"><span data-stu-id="753d6-153">Counter</span></span>|<span data-ttu-id="753d6-154">意義</span><span class="sxs-lookup"><span data-stu-id="753d6-154">Meaning</span></span>|  
|-------------|-------------|  
|<span data-ttu-id="753d6-155">Bytes</span><span class="sxs-lookup"><span data-stu-id="753d6-155">Bytes</span></span>|<span data-ttu-id="753d6-156">所有文件接收或傳送的裝載大小。</span><span class="sxs-lookup"><span data-stu-id="753d6-156">Size of the payload of all documents received or sent.</span></span>|  
|<span data-ttu-id="753d6-157">位元組數/秒</span><span class="sxs-lookup"><span data-stu-id="753d6-157">Bytes/sec</span></span>|<span data-ttu-id="753d6-158">目前裝載接收或傳送的輸送量。</span><span class="sxs-lookup"><span data-stu-id="753d6-158">Current throughput of the payload received or sent.</span></span>|  
|<span data-ttu-id="753d6-159">處理文件數</span><span class="sxs-lookup"><span data-stu-id="753d6-159">Documents processed</span></span>|<span data-ttu-id="753d6-160">**MLLP 接收**:</span><span class="sxs-lookup"><span data-stu-id="753d6-160">**MLLP Receive**:</span></span><br /><br /> <span data-ttu-id="753d6-161">已成功傳送到 MessageBox 資料庫的文件數。</span><span class="sxs-lookup"><span data-stu-id="753d6-161">Number of documents successfully delivered to the MessageBox database.</span></span><br /><br /> <span data-ttu-id="753d6-162">**MLLP 傳送**:</span><span class="sxs-lookup"><span data-stu-id="753d6-162">**MLLP Send**:</span></span><br /><br /> <span data-ttu-id="753d6-163">已成功傳送到遠端應用程式的文件數。</span><span class="sxs-lookup"><span data-stu-id="753d6-163">Number of documents successfully delivered to the remote application.</span></span>|  
|<span data-ttu-id="753d6-164">失敗的文件</span><span class="sxs-lookup"><span data-stu-id="753d6-164">Documents failed</span></span>|<span data-ttu-id="753d6-165">**MLLP 接收**:</span><span class="sxs-lookup"><span data-stu-id="753d6-165">**MLLP Receive**:</span></span><br /><br /> <span data-ttu-id="753d6-166">未成功傳遞到 MessageBox 資料庫的文件數目。</span><span class="sxs-lookup"><span data-stu-id="753d6-166">Number of documents not successfully delivered to the MessageBox database.</span></span><br /><br /> <span data-ttu-id="753d6-167">**MLLP 傳送**:</span><span class="sxs-lookup"><span data-stu-id="753d6-167">**MLLP Send**:</span></span><br /><br /> <span data-ttu-id="753d6-168">未成功傳遞到遠端應用程式的文件數目。</span><span class="sxs-lookup"><span data-stu-id="753d6-168">Number of documents not successfully delivered to the remote application.</span></span>|  
|<span data-ttu-id="753d6-169">連線狀態</span><span class="sxs-lookup"><span data-stu-id="753d6-169">Connection status</span></span>|<span data-ttu-id="753d6-170">配接器連線，狀態 1 或 0 (1 = 連接)。</span><span class="sxs-lookup"><span data-stu-id="753d6-170">The status of the adapter connection, 1 or 0 (1=connected).</span></span>|  
  
 <span data-ttu-id="753d6-171">效能計數器執行個體使用下列命名結構：</span><span class="sxs-lookup"><span data-stu-id="753d6-171">The performance counter instances use the following naming scheme:</span></span>  
  
```  
{recv|trans} : connection name : remote IP address : remote port ID  
```  
  
 <span data-ttu-id="753d6-172">MLLP 的接收配接器使用的 「 接收 」 前置詞，並 MLLP 傳送配接器會使用 「 交易 」。</span><span class="sxs-lookup"><span data-stu-id="753d6-172">Where the MLLP receive adapter uses the "recv" prefix, and the MLLP send adapter uses "trans".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="753d6-173">認可傳送的接收埠 （例如，配接器在雙向模式中操作），並傳送連接埠 （可以接收相同的通訊端連線的 Ack 運作） 都不會計入。</span><span class="sxs-lookup"><span data-stu-id="753d6-173">ACKs sent by receive ports (for example, an adapter operating in a two-way mode) and send ports (operating to receive ACKs on the same socket connection) are not counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753d6-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="753d6-174">See Also</span></span>  
 <span data-ttu-id="753d6-175">[處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md) </span><span class="sxs-lookup"><span data-stu-id="753d6-175">[Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md) </span></span>  
 <span data-ttu-id="753d6-176">[組態參數傳送和接收配接器](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="753d6-176">[Configuration Parameters for Send and Receive Adapters](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md) </span></span>  
 <span data-ttu-id="753d6-177">[MLLP 傳送配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md) </span><span class="sxs-lookup"><span data-stu-id="753d6-177">[MLLP Send Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md) </span></span>  
 [<span data-ttu-id="753d6-178">設定傳送埠來接收通知</span><span class="sxs-lookup"><span data-stu-id="753d6-178">Setting Up a Send Port for Receiving ACKs</span></span>](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)