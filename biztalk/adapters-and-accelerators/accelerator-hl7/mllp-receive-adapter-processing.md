---
title: MLLP 接收配接器處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, receive adapters
- MLLP adapters, send adapters
- receive adapters
ms.assetid: 03c9a5f6-6f23-454f-8bab-e7c7b6057efa
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbb5932d65bce2b17ebfca3645b8c755549b9a9c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968135"
---
# <a name="mllp-receive-adapter-processing"></a><span data-ttu-id="9f865-102">MLLP 接收配接器處理</span><span class="sxs-lookup"><span data-stu-id="9f865-102">MLLP Receive Adapter Processing</span></span>
<span data-ttu-id="9f865-103">最小的較低層通訊協定 (MLLP) 接收配接器支援這兩個單向和雙向要求回應模式。</span><span class="sxs-lookup"><span data-stu-id="9f865-103">The Minimal Lower Layer Protocol (MLLP) receive adapter supports both one-way and two-way request response modes.</span></span> <span data-ttu-id="9f865-104">配接器會接聽，並接受連線。</span><span class="sxs-lookup"><span data-stu-id="9f865-104">The adapter listens and accepts connections.</span></span>  
  
 <span data-ttu-id="9f865-105">當 MLLP 接收配接器在雙向的模式下運作，配接器將不會收到一封新郵件連接直到管線已產生通知 (ACK) （如先前的訊息。</span><span class="sxs-lookup"><span data-stu-id="9f865-105">When the MLLP receive adapter operates in two-way mode, the adapter will not receive a new message from the connection until the pipeline has generated the acknowledgment (ACK) for the previous message.</span></span>  
  
## <a name="configuration-parameters"></a><span data-ttu-id="9f865-106">組態參數</span><span class="sxs-lookup"><span data-stu-id="9f865-106">Configuration Parameters</span></span>  
 <span data-ttu-id="9f865-107">接收處理常式的參數在 BizTalk 主控件層級設定，並套用至與它相關聯的所有 MLLP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="9f865-107">The parameters for a receive handler are configured at the BizTalk Host level, and apply to all MLLP receive locations associated with it.</span></span>  
  
|<span data-ttu-id="9f865-108">參數</span><span class="sxs-lookup"><span data-stu-id="9f865-108">Parameter</span></span>|<span data-ttu-id="9f865-109">使用</span><span class="sxs-lookup"><span data-stu-id="9f865-109">Use</span></span>|  
|---------------|---------|  
|<span data-ttu-id="9f865-110">*最大可接受的連線限制*</span><span class="sxs-lookup"><span data-stu-id="9f865-110">*Max Accept Connection Limit*</span></span>|<span data-ttu-id="9f865-111">接收配接器會接受同時開啟的連線數目限制。</span><span class="sxs-lookup"><span data-stu-id="9f865-111">Limits the number of concurrent open connections that the receive adapter will accept.</span></span>|  
  
## <a name="acknowledgments-with-the-two-way-mllp-receive-adapter"></a><span data-ttu-id="9f865-112">通知使用雙向 MLLP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="9f865-112">Acknowledgments with the two-way MLLP receive adapter</span></span>  
 <span data-ttu-id="9f865-113">當雙向 MLLP 接收配接器接收訊息時，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 可以產生下列類型的通知：</span><span class="sxs-lookup"><span data-stu-id="9f865-113">When a two-way MLLP receive adapter receives a message, Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) can generate the following types of ACKs:</span></span>  
  
- <span data-ttu-id="9f865-114">HL7 增強認可通知： 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]相同的連接上傳送認可的通知。</span><span class="sxs-lookup"><span data-stu-id="9f865-114">HL7 Enhanced Commit ACK: In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends a Commit ACK on the same connection.</span></span> <span data-ttu-id="9f865-115">它會送出不同的傳送埠上的應用程式接受通知。</span><span class="sxs-lookup"><span data-stu-id="9f865-115">It sends out an Application Accept ACK on a different send port.</span></span>  
  
- <span data-ttu-id="9f865-116">應用程式接受通知： 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送相同的連接上的應用程式接受通知。</span><span class="sxs-lookup"><span data-stu-id="9f865-116">Application Accept ACK: In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an Application Accept ACK on the same connection.</span></span>  
  
- <span data-ttu-id="9f865-117">靜態通知： 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]相同的連接上傳送通知。</span><span class="sxs-lookup"><span data-stu-id="9f865-117">Static ACK: In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK on the same connection.</span></span>  
  
- <span data-ttu-id="9f865-118">產生的通知類型取決於[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管設定的合作對象傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="9f865-118">The type of ACK generated depends on the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer settings for the party sending the message.</span></span> <span data-ttu-id="9f865-119">在欄位 MSH 15 和 16 個別訊息的值可以覆寫此設定。</span><span class="sxs-lookup"><span data-stu-id="9f865-119">The value in fields MSH 15 and 16 of an individual message can override this setting.</span></span> <span data-ttu-id="9f865-120">不過，對於必須是靜態的 Ack 時，應用程式，設定只能設定透過[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。</span><span class="sxs-lookup"><span data-stu-id="9f865-120">However, for applications expecting Static ACKs, the configuration can only be set through [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="error-conditions"></a><span data-ttu-id="9f865-121">錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="9f865-121">Error Conditions</span></span>  
 <span data-ttu-id="9f865-122">錯誤條件或無活動時，就會發生下列事件：</span><span class="sxs-lookup"><span data-stu-id="9f865-122">The following events occur when there is an error condition or inactivity:</span></span>  
  
- <span data-ttu-id="9f865-123">如果已停用接收位置或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]關閉，會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="9f865-123">If the receive location is disabled or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] shuts down, the following occurs:</span></span>  
  
  - <span data-ttu-id="9f865-124">接收位置不再接受新連線。</span><span class="sxs-lookup"><span data-stu-id="9f865-124">The receive location will no longer accept new connections.</span></span>  
  
  - <span data-ttu-id="9f865-125">對於現有的連線，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]完全接收 目前的訊息，並再關閉連線。</span><span class="sxs-lookup"><span data-stu-id="9f865-125">For existing connections, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] completely receives the current message, and then closes the connection.</span></span>  
  
- <span data-ttu-id="9f865-126">偵測到非使用狀態時 （在指定的逾時時間內接收位置接收到沒有承載資料），配接器會關閉連線。</span><span class="sxs-lookup"><span data-stu-id="9f865-126">When inactivity is detected (no payload data received on the receive location within the specified timeout), the adapter closes the connection.</span></span>  
  
- <span data-ttu-id="9f865-127">如果[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]收到未完成訊息時，暫停接收到的部分。</span><span class="sxs-lookup"><span data-stu-id="9f865-127">If [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receives an incomplete message, the portion received is suspended.</span></span> <span data-ttu-id="9f865-128">收到一則訊息 （在之前針對新的連接，EB/CR 和 SB 的下一個訊息之間的第一個 SB) 以外的所有位元組會被都忽略。</span><span class="sxs-lookup"><span data-stu-id="9f865-128">All bytes received outside of a message (before the first SB on a new connection, between EB/CR and SB of the next message) are ignored.</span></span>  
  
- <span data-ttu-id="9f865-129">如果管線無法剖析訊息，訊息仍然會被傳送到 MessageBox 資料庫，與升級的屬性**ParseError = true**。</span><span class="sxs-lookup"><span data-stu-id="9f865-129">If the pipeline fails to parse the message, the message is still delivered to the MessageBox database, with a promoted property **ParseError=true**.</span></span>  
  
- <span data-ttu-id="9f865-130">如果訊息失敗，因為沒有訂用帳戶，或在標題中的結構錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]原始"wire"格式 （如果之前正在剖析） 擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="9f865-130">If a message fails due to the absence of a subscription, or due to structural errors in the header, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] suspends the message in its original "wire" form (prior to being parsed).</span></span> <span data-ttu-id="9f865-131">沒有訂用帳戶失敗的常見原因是缺少的升級屬性。</span><span class="sxs-lookup"><span data-stu-id="9f865-131">A frequent reason for the no-subscription failure is the lack of promoted properties.</span></span> <span data-ttu-id="9f865-132">由於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]擱置未剖析的訊息， **BTS。MessageType**會是空白。</span><span class="sxs-lookup"><span data-stu-id="9f865-132">Since [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] suspends the unparsed message, the **BTS.MessageType** will be blank.</span></span>  
  
  <span data-ttu-id="9f865-133">下表列出 MLLP 接收配接器傳回的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9f865-133">The following table lists the errors that the MLLP receive adapter returns.</span></span>  
  
|            <span data-ttu-id="9f865-134">事件</span><span class="sxs-lookup"><span data-stu-id="9f865-134">Event</span></span>             |  <span data-ttu-id="9f865-135">ID</span><span class="sxs-lookup"><span data-stu-id="9f865-135">ID</span></span>  |                                                                                                          <span data-ttu-id="9f865-136">錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="9f865-136">Error Condition</span></span>                                                                                                           |
|------------------------------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      <span data-ttu-id="9f865-137">**ErrorListening**</span><span class="sxs-lookup"><span data-stu-id="9f865-137">**ErrorListening**</span></span>      | <span data-ttu-id="9f865-138">8448</span><span class="sxs-lookup"><span data-stu-id="9f865-138">8448</span></span> |                                                   <span data-ttu-id="9f865-139">無法繫結至本機通訊端 （最有可能其他本機應用程式使用相同的 IP 位址/連接埠編號組合）。</span><span class="sxs-lookup"><span data-stu-id="9f865-139">Could not bind to a local socket (most likely some other local application is using the same IP address/port ID combination).</span></span>                                                    |
| <span data-ttu-id="9f865-140">**ErrorAcceptingConnection**</span><span class="sxs-lookup"><span data-stu-id="9f865-140">**ErrorAcceptingConnection**</span></span> | <span data-ttu-id="9f865-141">8449</span><span class="sxs-lookup"><span data-stu-id="9f865-141">8449</span></span> | <span data-ttu-id="9f865-142">無法建立與遠端的一方的 TCP 連線。</span><span class="sxs-lookup"><span data-stu-id="9f865-142">Could not establish a TCP connection with the remote party.</span></span> <span data-ttu-id="9f865-143">任一[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]達到連線數上限，或資源不足。</span><span class="sxs-lookup"><span data-stu-id="9f865-143">Either [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] reached the maximum connection limit, or the resources were insufficient.</span></span> |
|  <span data-ttu-id="9f865-144">**ErrorSubmittingMessage**</span><span class="sxs-lookup"><span data-stu-id="9f865-144">**ErrorSubmittingMessage**</span></span>  | <span data-ttu-id="9f865-145">8452</span><span class="sxs-lookup"><span data-stu-id="9f865-145">8452</span></span> |                   <span data-ttu-id="9f865-146">MessageBox 資料庫不可以接受該訊息。</span><span class="sxs-lookup"><span data-stu-id="9f865-146">The MessageBox database could not accept the message.</span></span> <span data-ttu-id="9f865-147">任一[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]變得無法使用或資源不足。</span><span class="sxs-lookup"><span data-stu-id="9f865-147">Either [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] was unavailable or the resources were insufficient.</span></span>                   |
|     <span data-ttu-id="9f865-148">**ErrorSendingAck**</span><span class="sxs-lookup"><span data-stu-id="9f865-148">**ErrorSendingAck**</span></span>      | <span data-ttu-id="9f865-149">8454</span><span class="sxs-lookup"><span data-stu-id="9f865-149">8454</span></span> |                                [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9f865-150"> 無法傳回通知，因為連線無法使用。</span><span class="sxs-lookup"><span data-stu-id="9f865-150"> could not return the acknowledgment because the connection was not available.</span></span>                                 |
  
## <a name="performance-counters"></a><span data-ttu-id="9f865-151">效能計數器</span><span class="sxs-lookup"><span data-stu-id="9f865-151">Performance Counters</span></span>  
 <span data-ttu-id="9f865-152">下表列出使用 MLLP 配接器的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="9f865-152">The following table lists the performance counters that the MLLP adapter uses.</span></span>  
  
|<span data-ttu-id="9f865-153">計數器</span><span class="sxs-lookup"><span data-stu-id="9f865-153">Counter</span></span>|<span data-ttu-id="9f865-154">意義</span><span class="sxs-lookup"><span data-stu-id="9f865-154">Meaning</span></span>|  
|-------------|-------------|  
|<span data-ttu-id="9f865-155">Bytes</span><span class="sxs-lookup"><span data-stu-id="9f865-155">Bytes</span></span>|<span data-ttu-id="9f865-156">已接收或傳送的所有文件的內容的大小。</span><span class="sxs-lookup"><span data-stu-id="9f865-156">Size of the payload of all documents received or sent.</span></span>|  
|<span data-ttu-id="9f865-157">位元組/秒</span><span class="sxs-lookup"><span data-stu-id="9f865-157">Bytes/sec</span></span>|<span data-ttu-id="9f865-158">目前裝載接收或傳送的輸送量。</span><span class="sxs-lookup"><span data-stu-id="9f865-158">Current throughput of the payload received or sent.</span></span>|  
|<span data-ttu-id="9f865-159">處理文件數</span><span class="sxs-lookup"><span data-stu-id="9f865-159">Documents processed</span></span>|<span data-ttu-id="9f865-160">**MLLP 接收**:</span><span class="sxs-lookup"><span data-stu-id="9f865-160">**MLLP Receive**:</span></span><br /><br /> <span data-ttu-id="9f865-161">文件數目成功傳遞到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9f865-161">Number of documents successfully delivered to the MessageBox database.</span></span><br /><br /> <span data-ttu-id="9f865-162">**MLLP 傳送**:</span><span class="sxs-lookup"><span data-stu-id="9f865-162">**MLLP Send**:</span></span><br /><br /> <span data-ttu-id="9f865-163">已成功傳送給遠端應用程式的文件的數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-163">Number of documents successfully delivered to the remote application.</span></span>|  
|<span data-ttu-id="9f865-164">失敗的文件</span><span class="sxs-lookup"><span data-stu-id="9f865-164">Documents failed</span></span>|<span data-ttu-id="9f865-165">**MLLP 接收**:</span><span class="sxs-lookup"><span data-stu-id="9f865-165">**MLLP Receive**:</span></span><br /><br /> <span data-ttu-id="9f865-166">未成功傳遞到 MessageBox 資料庫的文件數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-166">Number of documents not successfully delivered to the MessageBox database.</span></span><br /><br /> <span data-ttu-id="9f865-167">**MLLP 傳送**:</span><span class="sxs-lookup"><span data-stu-id="9f865-167">**MLLP Send**:</span></span><br /><br /> <span data-ttu-id="9f865-168">未成功傳遞到遠端應用程式的文件數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-168">Number of documents not successfully delivered to the remote application.</span></span>|  
|<span data-ttu-id="9f865-169">連線狀態</span><span class="sxs-lookup"><span data-stu-id="9f865-169">Connection status</span></span>|<span data-ttu-id="9f865-170">配接器連線中，狀態 1 或 0 (1 = 連接)。</span><span class="sxs-lookup"><span data-stu-id="9f865-170">The status of the adapter connection, 1 or 0 (1=connected).</span></span>|  
  
 <span data-ttu-id="9f865-171">效能計數器執行個體可以使用下列命名配置：</span><span class="sxs-lookup"><span data-stu-id="9f865-171">The performance counter instances use the following naming scheme:</span></span>  
  
```  
{recv|trans} : connection name : remote IP address : remote port ID  
```  
  
 <span data-ttu-id="9f865-172">MLLP 接收配接器使用的 「 接收 」 前置詞，並 MLLP 傳送配接器會使用 「 交易 」。</span><span class="sxs-lookup"><span data-stu-id="9f865-172">Where the MLLP receive adapter uses the "recv" prefix, and the MLLP send adapter uses "trans".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f865-173">所傳送的通知接收埠 （例如，配接器在雙向模式中操作），並傳送連接埠 （在相同的通訊端連線接收 Ack 操作） 不會計算。</span><span class="sxs-lookup"><span data-stu-id="9f865-173">ACKs sent by receive ports (for example, an adapter operating in a two-way mode) and send ports (operating to receive ACKs on the same socket connection) are not counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f865-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f865-174">See Also</span></span>  
 <span data-ttu-id="9f865-175">[處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md) </span><span class="sxs-lookup"><span data-stu-id="9f865-175">[Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md) </span></span>  
 <span data-ttu-id="9f865-176">[組態參數，傳送和接收配接器](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="9f865-176">[Configuration Parameters for Send and Receive Adapters](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md) </span></span>  
 <span data-ttu-id="9f865-177">[MLLP 傳送配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md) </span><span class="sxs-lookup"><span data-stu-id="9f865-177">[MLLP Send Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md) </span></span>  
 [<span data-ttu-id="9f865-178">設定傳送埠來接收 ACK</span><span class="sxs-lookup"><span data-stu-id="9f865-178">Setting Up a Send Port for Receiving ACKs</span></span>](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)