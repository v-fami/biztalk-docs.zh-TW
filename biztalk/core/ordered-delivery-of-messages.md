---
title: 依序傳遞訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backing up, message order
- file transport, message order
- Messaging Engine, transports
- messages, performance
- dynamic send ports, message order
- BTS.SuspendAsNonResumable message context property
- performance, message order
- Messaging Engine, performance
- Messaging Engine, message order
- MessageBox database, message order
- messages, sorting
- backing up, backup transports
- adapters, custom receive adapters
- adapters, messages
- customizing, receive adapters
ms.assetid: 39e0bba6-81f5-4ae0-af92-837b225bc801
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52798c5f34c1f436d5c55954f61c6e18fcb2a398
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013015"
---
# <a name="ordered-delivery-of-messages"></a><span data-ttu-id="6e6a4-102">訊息的排序傳遞</span><span class="sxs-lookup"><span data-stu-id="6e6a4-102">Ordered Delivery of Messages</span></span>
<span data-ttu-id="6e6a4-103">訊息的排序傳遞可確保以指定順序發佈至 MessageBox 資料庫的訊息是以與發佈至 MessageBox 的相同順序傳遞給每一個相符的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-103">Ordered message delivery ensures that messages that are published to the MessageBox database in a given order are delivered to each matching subscriber in the same order in which they were published to the message box.</span></span>  
  
## <a name="configuring-ordered-message-delivery"></a><span data-ttu-id="6e6a4-104">設定訊息的排序傳遞</span><span class="sxs-lookup"><span data-stu-id="6e6a4-104">Configuring Ordered Message Delivery</span></span>  
 <span data-ttu-id="6e6a4-105">可在下列位置設定訊息的排序傳遞：</span><span class="sxs-lookup"><span data-stu-id="6e6a4-105">Ordered message delivery can be configured in the following places:</span></span>  
  
-   <span data-ttu-id="6e6a4-106">**接收**協調流程中的圖形</span><span class="sxs-lookup"><span data-stu-id="6e6a4-106">**Receive** shape in an orchestration</span></span>  
  
-   <span data-ttu-id="6e6a4-107">傳送埠</span><span class="sxs-lookup"><span data-stu-id="6e6a4-107">Send port</span></span>  
  
## <a name="ordered-delivery-with-existing-transports"></a><span data-ttu-id="6e6a4-108">具備現有傳輸的排序傳遞</span><span class="sxs-lookup"><span data-stu-id="6e6a4-108">Ordered Delivery with Existing Transports</span></span>  
 <span data-ttu-id="6e6a4-109">在特定傳輸之下的通訊協定，像是 FILE 和 HTTP，與排序傳遞的概念並不一致。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-109">The protocols underlying certain transports, such as FILE and HTTP, are not consistent with the notion of ordered delivery.</span></span> <span data-ttu-id="6e6a4-110">不過，即使具備這類傳輸，若與傳輸繫結的連接埠標示為排序的傳遞，則 BizTalk Server 會藉由保證除非已成功傳送目前的輸出訊息，否則傳輸不會取得下一個輸出訊息，以強制排序的傳遞。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-110">However, even with such transports, if the port bound to the transport is marked for ordered delivery, then BizTalk Server enforces ordered delivery by ensuring that the transport does not get the next outbound message until the current one has been successfully sent.</span></span> <span data-ttu-id="6e6a4-111">BizTalk Server 執行這項工作的方法是將每個訊息以單一批次傳遞給傳輸的配接器，並等待配接器成功從 MessageBox 刪除訊息後，再以另一個批次傳遞下一個訊息給配接器。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-111">To achieve this, BizTalk Server passes each message to the transport's adapter in a single batch and waits until the adapter has successfully deleted the message from the message box before delivering the next message, in another batch, to the adapter.</span></span>  
  
### <a name="ordered-delivery-for-custom-adapters"></a><span data-ttu-id="6e6a4-112">自訂配接器的排序傳遞</span><span class="sxs-lookup"><span data-stu-id="6e6a4-112">Ordered Delivery for Custom Adapters</span></span>  
 <span data-ttu-id="6e6a4-113">自訂接收配接器有一些特殊的考量。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-113">There are special considerations for custom receive adapters.</span></span> <span data-ttu-id="6e6a4-114">若您正在撰寫可支援接收時排序傳遞的自訂配接器，則配接器應執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6e6a4-114">It you are writing a custom adapter that supports ordered delivery on receive, the adapter should do the following:</span></span>  
  
- <span data-ttu-id="6e6a4-115">提交訊息批次之後, 您的自訂接收配接器應該等待**BatchComplete**從 BizTalk Server 才能提交下一個批次的回呼。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-115">After submitting a batch of messages, your custom receive adapter should wait for the **BatchComplete** callback from BizTalk Server before submitting the next batch.</span></span> <span data-ttu-id="6e6a4-116">如需詳細資訊，請參閱 < [Batch-Supported 接收配接器介面](../core/interfaces-for-a-batch-supported-receive-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-116">For more details, see [Interfaces for a Batch-Supported Receive Adapter](../core/interfaces-for-a-batch-supported-receive-adapter.md).</span></span>  
  
- <span data-ttu-id="6e6a4-117">若訊息在管線中失敗，應該被擱置，最好標示為不可繼續。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-117">If a message fails in the pipeline, it should be suspended, preferably as nonresumable.</span></span> <span data-ttu-id="6e6a4-118">使用**BTS。SuspendAsNonResumable**訊息中的內容屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]適當地加上旗標的訊息。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-118">Use the **BTS.SuspendAsNonResumable** message context property in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to flag the message appropriately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e6a4-119">若在稍後繼續擱置的訊息，則會中斷訊息順序。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-119">Message order can be broken if a suspended message is later resumed.</span></span> <span data-ttu-id="6e6a4-120">若您不希望中斷順序，請擱置失敗的訊息並設為不可繼續。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-120">If you do not want this behavior, suspend failed messages as nonresumable.</span></span>  
  
 <span data-ttu-id="6e6a4-121">如需建置自訂的配接器的詳細資訊，請參閱 <<c0> [ 開發自訂配接器](../core/developing-custom-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-121">For more details on building a custom adapter, see [Developing Custom Adapters](../core/developing-custom-adapters.md).</span></span>  
  
## <a name="conditions-for-end-to-end-ordered-message-processing"></a><span data-ttu-id="6e6a4-122">端對端排序訊息處理的條件</span><span class="sxs-lookup"><span data-stu-id="6e6a4-122">Conditions for End-to-End Ordered Message Processing</span></span>  
 <span data-ttu-id="6e6a4-123">若要提供端對端排序的傳遞，必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="6e6a4-123">To provide end-to-end ordered delivery the following conditions must be met:</span></span>  
  
- <span data-ttu-id="6e6a4-124">必須以保留提交訊息給 BizTalk Server 的訊息順序之配接器接收訊息。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-124">Messages must be received with an adapter that preserves the order of the messages when submitting them to BizTalk Server.</span></span> <span data-ttu-id="6e6a4-125">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，這類配接器的範例包括 MSMQ 和 MQSeries。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-125">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], examples of such adapters are MSMQ and MQSeries.</span></span> <span data-ttu-id="6e6a4-126">此外，HTTP 或 SOAP 配接器可以用來提交訊息順序，但在此情況下 HTTP 或 SOAP 用戶端必須強制執行一次提交一個訊息的順序。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-126">In addition, HTTP or SOAP adapters can be used to submit messages in order, but in that case the HTTP or SOAP client needs to enforce the order by submitting messages one at a time.</span></span>  
  
- <span data-ttu-id="6e6a4-127">您必須訂閱這些訊息與傳送埠具有**排序的傳遞**選項設定為`True`。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-127">You must subscribe to these messages with a send port that has the **Ordered Delivery** option set to `True`.</span></span>  
  
- <span data-ttu-id="6e6a4-128">如果應該使用的訊息，協調流程中的單一執行個體的程序來協調流程，協調流程應該設定為使用循序群組中，而**排序的傳遞**屬性協調流程的接收埠應該設定為`True`。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-128">If an orchestration is used to process the messages, only a single instance of the orchestration should be used, the orchestration should be configured to use a sequential convoy, and the **Ordered Delivery** property of the orchestration's receive port should be set to `True`.</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="6e6a4-129">限制</span><span class="sxs-lookup"><span data-stu-id="6e6a4-129">Restrictions</span></span>  
 <span data-ttu-id="6e6a4-130">下列各項不支援訊息的排序傳遞：</span><span class="sxs-lookup"><span data-stu-id="6e6a4-130">Ordered delivery of messages is not supported for the following:</span></span>  
  
- <span data-ttu-id="6e6a4-131">動態傳送埠中[!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]與更舊版本</span><span class="sxs-lookup"><span data-stu-id="6e6a4-131">Dynamic send ports in [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] and previous versions</span></span>

- <span data-ttu-id="6e6a4-132">動態傳送連接埠[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]（和任何較新版本） 這些配接器類型**不**靜態傳送埠上的排序傳遞的支援</span><span class="sxs-lookup"><span data-stu-id="6e6a4-132">Dynamic send ports in [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] (and any newer versions) for those adapter types that **don't** support ordered delivery on static send ports</span></span>
  
- <span data-ttu-id="6e6a4-133">備份傳輸</span><span class="sxs-lookup"><span data-stu-id="6e6a4-133">Backup transports</span></span>  

  
## <a name="interactions"></a><span data-ttu-id="6e6a4-134">互動</span><span class="sxs-lookup"><span data-stu-id="6e6a4-134">Interactions</span></span>  
 <span data-ttu-id="6e6a4-135">當傳送埠設定為排序的傳遞時，請注意與 BizTalk Server 中其他設定的行為之下列互動：</span><span class="sxs-lookup"><span data-stu-id="6e6a4-135">When ordered delivery is configured for a send port, be aware of the following interactions with other configured behaviors in BizTalk Server:</span></span>  
  
-   <span data-ttu-id="6e6a4-136">相同傳送埠上的 [目前訊息失敗之後停止傳送後續訊息] 設定：</span><span class="sxs-lookup"><span data-stu-id="6e6a4-136">For the "Stop sending subsequent messages on current message failure" setting on the same send port:</span></span>  
  
    -   <span data-ttu-id="6e6a4-137">**值為 false。**</span><span class="sxs-lookup"><span data-stu-id="6e6a4-137">**False.**</span></span> <span data-ttu-id="6e6a4-138">只會擱置失敗的訊息 (不可繼續) 並繼續處理所有後續訊息。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-138">Only the failed message is suspended (as not resumable) and all subsequent messages continue to be processed.</span></span> <span data-ttu-id="6e6a4-139">這會保留未失敗訊息的順序，但會造成順序的間斷。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-139">This preserves the ordering of the non-failed messages but can result in gaps in the sequence.</span></span> <span data-ttu-id="6e6a4-140">例如，若收到順序 101、102 和 103，並擱置順序 102，則繼續依序處理順序 101 和 103。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-140">For example, if orders 101, 102, and 103 are received and order 102 is suspended, orders 101 and 103 will continue to be processed in order.</span></span>  
  
    -   <span data-ttu-id="6e6a4-141">**則為 true。**</span><span class="sxs-lookup"><span data-stu-id="6e6a4-141">**True.**</span></span> <span data-ttu-id="6e6a4-142">若任何訊息處理失敗，則擱置傳送埠執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-142">The send port instance is suspended if any of the messages fails processing.</span></span> <span data-ttu-id="6e6a4-143">這會造成訊息排序集合中的所有後續訊息被擱置。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-143">This causes all subsequent messages in the ordered set of messages to be suspended.</span></span> <span data-ttu-id="6e6a4-144">這是藉由在失敗的訊息傳遞之前，防止後續訊息的傳遞，以保留訊息順序。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-144">This preserves message order by preventing delivery of subsequent messages before delivery of the failed message.</span></span>  
  
-   <span data-ttu-id="6e6a4-145">若請求-回應傳送埠將 [目前訊息失敗之後停止傳送後續訊息] 屬性設定為 `true`，且回應的接收管線之解譯階段已設定為可復原交換處理，則在解譯回應中發生可復原的錯誤時，傳送埠不會停止傳送訊息 (也就是說，不會擱置執行個體)。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-145">If a solicit-response send port has the "Stop sending subsequent messages on current message failure" property set to `true`, and if recoverable interchange processing is configured for the disassembly stage of the receive pipeline for the response, then the send port does not stop sending messages (that is, the instance is not suspended) if there is a recoverable error in disassembling the response.</span></span>  
  
-   <span data-ttu-id="6e6a4-146">刪除排序的傳送埠之前，請確定沒有與其相關聯的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-146">Before deleting an ordered send port, ensure that there are no instances associated with it.</span></span> <span data-ttu-id="6e6a4-147">若有相關聯的執行個體，應該在刪除傳送埠之前先終止它們。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-147">If there are associated instances, you should terminate them before deleting the send port.</span></span>  
  
## <a name="ordered-delivery-to-file-transport"></a><span data-ttu-id="6e6a4-148">檔案傳輸的排序傳遞</span><span class="sxs-lookup"><span data-stu-id="6e6a4-148">Ordered Delivery to File Transport</span></span>  
 <span data-ttu-id="6e6a4-149">訊息依序到達 FILE 配接器。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-149">Messages arrive at the File adapter in sequence.</span></span> <span data-ttu-id="6e6a4-150">FILE 配接器可能附加訊息到單一檔案或寫出檔案順序，結果如下：</span><span class="sxs-lookup"><span data-stu-id="6e6a4-150">The File adapter may append messages to a single file or write out a sequence of files, with the following results:</span></span>  
  
-   <span data-ttu-id="6e6a4-151">若訊息資料附加到單一檔案，則依序附加個別訊息。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-151">If message data is appended to a single file, individual messages are appended in order.</span></span> <span data-ttu-id="6e6a4-152">在傳送埠上使用 FILE 配接器進行依序傳遞的選項，只有在傳送埠可在附加模式下作用時才有意義。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-152">The ordered delivery option on a send port that uses the FILE adapter only makes sense if the send transport works in append mode</span></span>  
  
-   <span data-ttu-id="6e6a4-153">若訊息寫入個別檔案，則依序命名的檔案名稱可反映順序。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-153">If messages are written to individual files, the order is reflected in the file names, which are sequentially named.</span></span> <span data-ttu-id="6e6a4-154">在此情況下，若是由配接器寫入的檔案，則與時間相關的檔案系統屬性 (例如，檔案建立時間或修改時間) 不一定要反映訊息到達的順序。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-154">In this case, for files written by the adapter, file system properties relating to chronology (for example, file creation time or modification time) do not necessarily reflect the message arrival sequence.</span></span>  
  
## <a name="performance-impact-of-ordered-delivery"></a><span data-ttu-id="6e6a4-155">排序傳遞的效能影響</span><span class="sxs-lookup"><span data-stu-id="6e6a4-155">Performance Impact of Ordered Delivery</span></span>  
 <span data-ttu-id="6e6a4-156">為執行排序的傳遞，BizTalk Server 必須在訊息路徑上的不同點序列化處理排序的訊息。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-156">To achieve ordered delivery, BizTalk Server must serialize processing of ordered messages at various points along the message pathway.</span></span> <span data-ttu-id="6e6a4-157">這是藉由向外延展的技術達成，像是使用多個主控件執行個體以供平行處理訊息。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-157">This works against scale-out techniques, such as the use of multiple host instances for parallel processing of messages.</span></span> <span data-ttu-id="6e6a4-158">使用排序的傳遞時，即使連接埠設定為在多個主控件執行個體上執行，仍然只在單一主控件執行個體上執行，以確保排序的傳遞。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-158">When using ordered delivery, even ports configured to run on multiple host instances run only on a single host instance to ensure ordered delivery.</span></span> <span data-ttu-id="6e6a4-159">不過，在此情況下，還是可以維持高可用性，因為處理訊息的排序傳遞之主控件執行個體的失敗，會使得失敗的訊息在另一個可用的主控件執行個體上重新處理。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-159">However, in this situation, high availability is still maintained because the failure of a host instance that is processing ordered delivery of messages results in reprocessing of the failed message on another available host instance.</span></span>  
  
 <span data-ttu-id="6e6a4-160">啟用排序的傳遞時，預設值**重試間隔**為 5 分鐘。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-160">When Ordered Delivery is enabled, the default **Retry Interval** is 5 minutes.</span></span> <span data-ttu-id="6e6a4-161">若要改善效能，設定的重試間隔的最小的值，也就是 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-161">To improve performance, set the Retry Interval to the lowest value, which is 1 minute.</span></span> <span data-ttu-id="6e6a4-162">**重試間隔**屬性可接受值為零 (0)，但零 (0) 無效。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-162">The **Retry Interval** property may accept a value of zero (0) but zero (0) is not valid.</span></span> <span data-ttu-id="6e6a4-163">**重試計數**也可以微調以所需的重試次數。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-163">The **Retry Count** can also be tuned to the number of retries needed.</span></span> <span data-ttu-id="6e6a4-164">例如，如果您知道要求應該處理中 < 1 分鐘到傳送埠目的地一律可以存取，這兩個值設為 1。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-164">For example, if you know the request should process in <1 minute and the send port destination is always accessible, set both values to 1.</span></span>  
  
 <span data-ttu-id="6e6a4-165">若要變更的重試值，請前往[如何設定傳輸進階選項的傳送埠](http://go.microsoft.com/fwlink/p/?LinkID=267697)。</span><span class="sxs-lookup"><span data-stu-id="6e6a4-165">To change the Retry values, go to [How to Configure Transport Advanced Options for a Send Port](http://go.microsoft.com/fwlink/p/?LinkID=267697).</span></span>  
  
 <span data-ttu-id="6e6a4-166">如需其他有關排序的傳遞的詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="6e6a4-166">For additional information on Ordered Delivery, refer to the following:</span></span>  
  
 [<span data-ttu-id="6e6a4-167">BizTalk： 端對端排序訊息處理選項</span><span class="sxs-lookup"><span data-stu-id="6e6a4-167">BizTalk: End-to-End Ordered Message Processing Options</span></span>](http://social.technet.microsoft.com/wiki/contents/articles/12887.biztalk-end-to-end-ordered-message-processing-options.aspx)  
  
 [<span data-ttu-id="6e6a4-168">BizTalk： 排序的傳遞</span><span class="sxs-lookup"><span data-stu-id="6e6a4-168">BizTalk: Ordered Delivery</span></span>](http://social.technet.microsoft.com/wiki/contents/articles/6681.biztalk-ordered-delivery.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="6e6a4-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e6a4-169">See Also</span></span>  
 <span data-ttu-id="6e6a4-170">[依序傳遞訊息與 MSMQ 配接器](../core/ordered-delivery-of-messages-with-the-msmq-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6e6a4-170">[Ordered Delivery of Messages with the MSMQ Adapter](../core/ordered-delivery-of-messages-with-the-msmq-adapter.md) </span></span>  
 [<span data-ttu-id="6e6a4-171">使用 MQSeries 配接器依序傳遞訊息</span><span class="sxs-lookup"><span data-stu-id="6e6a4-171">Ordered Delivery of Messages with the MQSeries Adapter</span></span>](../core/ordered-delivery-of-messages-with-the-mqseries-adapter.md)