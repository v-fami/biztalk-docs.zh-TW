---
title: "傳送配接器的交換模式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ad65fb5-640d-4bd2-aabe-946210f58a22
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 997aaa9a92f90f30bdaaeb59cc9cecb0c454496f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="exchange-patterns-for-send-adapters"></a><span data-ttu-id="86374-102">傳送配接器的交換模式</span><span class="sxs-lookup"><span data-stu-id="86374-102">Exchange Patterns for Send Adapters</span></span>
<span data-ttu-id="86374-103">BizTalk 傳訊引擎是透過網路傳輸，將訊息傳遞給傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="86374-103">Send adapters are delivered messages from the BizTalk Messaging Engine to be transmitted over the wire.</span></span> <span data-ttu-id="86374-104">這些訊息可能採用單向或雙向的訊息交換模式來傳送。</span><span class="sxs-lookup"><span data-stu-id="86374-104">These messages may be sent by using a one-way or two-way message exchange pattern.</span></span> <span data-ttu-id="86374-105">處理這類雙向訊息交換模式的配接器稱為「請求-回應」配接器。</span><span class="sxs-lookup"><span data-stu-id="86374-105">An adapter that handles this two-way message exchange pattern is called a Solicit-Response adapter.</span></span>  
  
## <a name="blocking-vs-non-blocking-transmissions"></a><span data-ttu-id="86374-106">封鎖 vs。非封鎖式傳輸</span><span class="sxs-lookup"><span data-stu-id="86374-106">Blocking vs. Non-Blocking Transmissions</span></span>  
 <span data-ttu-id="86374-107">「 傳訊引擎將訊息傳遞至傳送配接器使用**IBTTransmitter.TransmitMessage**方法或**IBTTransmitterBatch.TransmitMessage**方法，取決於是否配接器是批次感知的。</span><span class="sxs-lookup"><span data-stu-id="86374-107">The Messaging Engine delivers messages to the send adapter by using either the **IBTTransmitter.TransmitMessage** method or the **IBTTransmitterBatch.TransmitMessage** method, depending on whether the adapter is batch-aware.</span></span> <span data-ttu-id="86374-108">這兩種方法的傳回值都是布林值，指出配接器傳輸訊息的情形。</span><span class="sxs-lookup"><span data-stu-id="86374-108">Both versions of the method have a Boolean return value that indicates how the adapter transmitted the message.</span></span> <span data-ttu-id="86374-109">如果配接器傳回 `true`，表示配接器是在完整送出訊息後才傳回。</span><span class="sxs-lookup"><span data-stu-id="86374-109">If the adapter returns `true`, it has completely sent the message before returning.</span></span> <span data-ttu-id="86374-110">在此情況下，傳訊引擎會替配接器代為從 MessageBox 資料庫刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="86374-110">In this case the Messaging Engine deletes the message from the MessageBox database on behalf of the adapter.</span></span> <span data-ttu-id="86374-111">如果配接器傳回 `false`，表示配接器已開始進行訊息傳輸，且於傳輸完成前即傳回。</span><span class="sxs-lookup"><span data-stu-id="86374-111">If the adapter returns `false`, it started message transmission and returned before the transmission completed.</span></span> <span data-ttu-id="86374-112">在此情況下，配接器不僅要負責從應用程式佇列刪除訊息，還得處理傳輸失敗而必須重試傳輸或擱置訊息的狀況。</span><span class="sxs-lookup"><span data-stu-id="86374-112">In this case, the adapter is responsible not only for deleting the message from its application queue but also for handling transmission failures that require the message to be retried for transmission or suspended.</span></span>  
  
 <span data-ttu-id="86374-113">配接器傳回`false`是未封鎖的呼叫，表示**TransmitMessage**實作程式碼不會封鎖呼叫執行緒，「 傳訊引擎。</span><span class="sxs-lookup"><span data-stu-id="86374-113">The adapter returning `false` is a nonblocking call, meaning that the **TransmitMessage** implementation code does not block the calling thread of the Messaging Engine.</span></span> <span data-ttu-id="86374-114">配接器只是將訊息放入記憶體中的佇列以準備傳輸，然後再傳回。</span><span class="sxs-lookup"><span data-stu-id="86374-114">The adapter simply adds the message to an in-memory queue ready to be transmitted and then returns.</span></span> <span data-ttu-id="86374-115">配接器本身應有自己的執行緒集區，用於維護記憶體中的佇列、傳輸訊息，然後將傳輸結果通知引擎。</span><span class="sxs-lookup"><span data-stu-id="86374-115">The adapter should have its own thread pool that services the in-memory queue, transmits the message, and then notifies the engine of the outcome of the transmission.</span></span>  
  
 <span data-ttu-id="86374-116">傳訊引擎的執行緒通常比用來透過網路傳送資料的執行緒更受限於 CPU 處理能力。</span><span class="sxs-lookup"><span data-stu-id="86374-116">The Messaging Engine’s threads are typically more CPU bound than the threads used to send data over the wire.</span></span> <span data-ttu-id="86374-117">混用這兩種執行緒會對效能造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="86374-117">Mixing these two types of threads has a negative impact on performance.</span></span> <span data-ttu-id="86374-118">非封鎖式傳送能分離這兩種執行緒，相較於封鎖式呼叫而言可獲得顯著的效能改善。</span><span class="sxs-lookup"><span data-stu-id="86374-118">Non-blocking sends enable the decoupling of these two types of threads and yield a significant performance improvement over blocking calls.</span></span>  
  
 <span data-ttu-id="86374-119">下圖顯示配接器的執行緒集區，其受限的因素偏向於 I/O 作業。</span><span class="sxs-lookup"><span data-stu-id="86374-119">The following diagram shows the adapter's thread pool which can tend to be bound by I/O operations.</span></span> <span data-ttu-id="86374-120">BizTalk Server 傳訊引擎的執行緒集區則大多受限於 CPU 處理能力。</span><span class="sxs-lookup"><span data-stu-id="86374-120">The BizTalk Server Messaging Engine's thread pool is more bound by the CPU processing.</span></span> <span data-ttu-id="86374-121">若是保持兩種不同的執行緒集區且不混用相同類型的執行緒，系統運作就會更有效率。</span><span class="sxs-lookup"><span data-stu-id="86374-121">By keeping two different thread pools and not mixing the same type of threads the system can operate more efficiently.</span></span>  
  
 ![](../core/media/io-cpu-bound-threadpools.gif "Io_cpu_bound_threadpools")  
  
 <span data-ttu-id="86374-122">**效能提示：**為了達到最佳效能，傳送配接器應封鎖可識別批次。</span><span class="sxs-lookup"><span data-stu-id="86374-122">**Performance Tip:** For the best performance, send adapters should be nonblocking and batch aware.</span></span> <span data-ttu-id="86374-123">BizTalk 傳送配接器若從不能識別批次的封鎖式變更為可識別批次的非封鎖式，效能將顯著提升三倍。</span><span class="sxs-lookup"><span data-stu-id="86374-123">When the BizTalk File adapter was changed from blocking and non-batch aware to nonblocking and batch aware, a threefold performance gain was realized.</span></span>  
  
 <span data-ttu-id="86374-124">**疑難排解秘訣：**封鎖傳輸可能會導致整個主控件執行個體的效能降低。</span><span class="sxs-lookup"><span data-stu-id="86374-124">**Troubleshooting Tip:** Blocking transmits can cause a performance degradation of an entire host instance.</span></span> <span data-ttu-id="86374-125">如果配接器過度封鎖了**TransmitMessage**它將使得引擎執行緒無法傳遞訊息給其他配接器。</span><span class="sxs-lookup"><span data-stu-id="86374-125">If the adapter does excessive blocking in **TransmitMessage** it will prevent engine threads from delivering messages to other adapters.</span></span>  
  
## <a name="non-batched-sends"></a><span data-ttu-id="86374-126">非批次傳送</span><span class="sxs-lookup"><span data-stu-id="86374-126">Non-Batched Sends</span></span>  
 <span data-ttu-id="86374-127">不是批次的配接器應該實作**IBTTransmitter**中所詳述[非同步傳送配接器的介面](../core/interfaces-for-an-asynchronous-send-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="86374-127">Adapters that are not batch aware should implement **IBTTransmitter** as detailed in [Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md).</span></span> <span data-ttu-id="86374-128">針對每個訊息，配接器需要傳輸，傳訊引擎會呼叫**IBTTransmitter.TransmitMessage**。</span><span class="sxs-lookup"><span data-stu-id="86374-128">For each message that the adapter needs to transmit the Messaging Engine calls **IBTTransmitter.TransmitMessage**.</span></span> <span data-ttu-id="86374-129">底下的物件互動示意圖詳盡說明慣常的訊息傳輸方式，其中包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="86374-129">The object interaction diagram below details the typical approach for transmitting messages, which consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="86374-130">引擎傳遞訊息給配接器。</span><span class="sxs-lookup"><span data-stu-id="86374-130">The engine delivers the message to the adapter.</span></span>  
  
2.  <span data-ttu-id="86374-131">配接器將訊息放入記憶體中的佇列以準備傳輸。</span><span class="sxs-lookup"><span data-stu-id="86374-131">The adapter enqueues the message to an in-memory queue ready to be transmitted.</span></span>  
  
3.  <span data-ttu-id="86374-132">配接器的執行緒集區中某個執行緒從佇列取出訊息、讀取訊息的組態，然後透過網路傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="86374-132">A thread from the adapter's thread pool dequeues the message from the queue, reads the configuration for the message, and transmits the message over the wire.</span></span>  
  
4.  <span data-ttu-id="86374-133">配接器從引擎取得新批次。</span><span class="sxs-lookup"><span data-stu-id="86374-133">The adapter gets a new batch from the engine.</span></span>  
  
5.  <span data-ttu-id="86374-134">配接器呼叫**DeleteMessage**批次，傳入剛才傳輸出去的訊息。</span><span class="sxs-lookup"><span data-stu-id="86374-134">The adapter calls **DeleteMessage** on the batch, passing in the message that it has just transmitted.</span></span>  
  
6.  <span data-ttu-id="86374-135">配接器呼叫**完成**批次。</span><span class="sxs-lookup"><span data-stu-id="86374-135">The adapter calls **Done** on the batch.</span></span>  
  
7.  <span data-ttu-id="86374-136">引擎處理該批次並從應用程式佇列刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="86374-136">The engine processes the batch and deletes the message from the application queue.</span></span>  
  
8.  <span data-ttu-id="86374-137">引擎回呼配接器以通知它的結果**DeleteMessage**作業。</span><span class="sxs-lookup"><span data-stu-id="86374-137">The engine calls back the adapter to notify it of the outcome of the **DeleteMessage** operation.</span></span>  
  
 ![](../core/media/deleting-from-message-queue.gif "Deleting_from_message_queue")  
  
 <span data-ttu-id="86374-138">上面的物件互動示意圖顯示配接器從應用程式佇列刪除單一訊息的情形。</span><span class="sxs-lookup"><span data-stu-id="86374-138">The preceding object interaction diagram shows the adapter deleting a single message from the application queue.</span></span> <span data-ttu-id="86374-139">理想情況下，配接器會批次執行多項訊息作業，而不是一次只對一個訊息進行作業。</span><span class="sxs-lookup"><span data-stu-id="86374-139">Ideally the adapter batches up message operations as opposed to operating on a single message at a time.</span></span>  
  
## <a name="batched-sends"></a><span data-ttu-id="86374-140">批次傳送</span><span class="sxs-lookup"><span data-stu-id="86374-140">Batched Sends</span></span>  
 <span data-ttu-id="86374-141">批次的配接器應該實作**IBTBatchTransmitter**和**IBTTransmitterBatch**中所詳述[傳送配接器的介面](../core/interfaces-for-send-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="86374-141">Adapters that are batch aware should implement **IBTBatchTransmitter** and **IBTTransmitterBatch** as detailed in [Interfaces for Send Adapters](../core/interfaces-for-send-adapters.md).</span></span> <span data-ttu-id="86374-142">當引擎有訊息傳輸的配接器時，引擎取得新批次從配接器藉由呼叫**IBTBatchTransmitter.GetBatch**。</span><span class="sxs-lookup"><span data-stu-id="86374-142">When the engine has messages for the adapter to transmit, the engine gets a new batch from the adapter by calling **IBTBatchTransmitter.GetBatch**.</span></span> <span data-ttu-id="86374-143">配接器會傳回新的批次物件實作**IBTTransmitterBatch**。</span><span class="sxs-lookup"><span data-stu-id="86374-143">The adapter returns a new batch object that implements **IBTTransmitterBatch**.</span></span> <span data-ttu-id="86374-144">然後藉由呼叫啟動批次的引擎**IBTTransmitterBatch.BeginBatch**。</span><span class="sxs-lookup"><span data-stu-id="86374-144">The engine then starts the batch by calling **IBTTransmitterBatch.BeginBatch**.</span></span> <span data-ttu-id="86374-145">此 API 具有輸出參數，讓配接器能夠指定批次中可接受的訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="86374-145">This API has an out parameter that allows the adapter to specify the maximum number of messages that it will accept on the batch.</span></span> <span data-ttu-id="86374-146">配接器亦可能選擇性地傳回 DTC 交易。</span><span class="sxs-lookup"><span data-stu-id="86374-146">The adapter may optionally return a DTC transaction.</span></span> <span data-ttu-id="86374-147">則引擎會呼叫**IBTTransmitterBatch.TransmitMessage**批次中加入每個外寄訊息一次。</span><span class="sxs-lookup"><span data-stu-id="86374-147">The engine then calls **IBTTransmitterBatch.TransmitMessage** once for each outgoing message to be added to the batch.</span></span> <span data-ttu-id="86374-148">其呼叫次數大於零，但小於或等於配接器所指定的批次大小上限。</span><span class="sxs-lookup"><span data-stu-id="86374-148">The number of times this is called is greater than zero but less than or equal to the maximum size of the batch as indicated by the adapter.</span></span> <span data-ttu-id="86374-149">當所有訊息都已加入至批次時，配接器會呼叫**IBTTransmitterBatch.Done**。</span><span class="sxs-lookup"><span data-stu-id="86374-149">When all the messages have been added to the batch, the adapter calls **IBTTransmitterBatch.Done**.</span></span> <span data-ttu-id="86374-150">這時，配接器通常會將批次中的訊息全部放入記憶體中的佇列。</span><span class="sxs-lookup"><span data-stu-id="86374-150">At this point the adapter typically enqueues all the messages in the batch to its in-memory queue.</span></span> <span data-ttu-id="86374-151">配接器透過本身執行緒集區內一或多個執行緒來傳輸訊息，就像不能識別批次的配接器一樣。</span><span class="sxs-lookup"><span data-stu-id="86374-151">The adapter transmits the messages from a thread or threads in its own thread pool as in the case of non-batch-aware adapters.</span></span> <span data-ttu-id="86374-152">最後，配接器會向引擎通知其傳輸結果。</span><span class="sxs-lookup"><span data-stu-id="86374-152">The adapter then notifies the engine of the outcome of the transmission.</span></span>  
  
 <span data-ttu-id="86374-153">底下的物件互動示意圖說明批次傳送配接器如何傳輸兩個訊息。</span><span class="sxs-lookup"><span data-stu-id="86374-153">The following object interaction diagram illustrates the transmission of two messages by a batched send adapter.</span></span>  
  
 ![](../core/media/batchedsends.gif "BatchedSends")  
  
## <a name="handling-transmission-failures"></a><span data-ttu-id="86374-154">處理傳輸失敗</span><span class="sxs-lookup"><span data-stu-id="86374-154">Handling Transmission Failures</span></span>  
 <span data-ttu-id="86374-155">傳輸失敗時的建議做法如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="86374-155">The recommended semantics for transmission failures are illustrated in the figure below.</span></span> <span data-ttu-id="86374-156">這些只是建議事項，並非傳訊引擎強制限定的做法。</span><span class="sxs-lookup"><span data-stu-id="86374-156">These are only recommendations and are not enforced by the Messaging Engine.</span></span> <span data-ttu-id="86374-157">只要理由合理，您可以跳脫這些指導方針自行開發配接器，但屆時務必留意若干常規。</span><span class="sxs-lookup"><span data-stu-id="86374-157">You can develop an adapter that deviates from these guidelines if there are valid reasons for doing so but you should be careful in this case.</span></span> <span data-ttu-id="86374-158">例如，一般來說，當重試次數已達上限之後，配接器都應該將訊息移至備份傳輸。</span><span class="sxs-lookup"><span data-stu-id="86374-158">For example, in general an adapter should always move messages to the backup transport after all retries have been exhausted.</span></span>  
  
 <span data-ttu-id="86374-159">通常，傳輸的重試次數可能必須高於設定值。</span><span class="sxs-lookup"><span data-stu-id="86374-159">More commonly a transport may need to use more retries than are configured.</span></span> <span data-ttu-id="86374-160">兩者雖稍有差距卻仍屬合理，因為傳輸層的回復性已有增進。</span><span class="sxs-lookup"><span data-stu-id="86374-160">While this is slightly different it is considered acceptable because the resilience of the transport layer is being increased.</span></span> <span data-ttu-id="86374-161">傳訊引擎所公開的 API 通常設計成盡量賦予配接器最多的控制權。</span><span class="sxs-lookup"><span data-stu-id="86374-161">In general the APIs exposed by the Messaging Engine are designed to give the adapter maximum control where possible.</span></span> <span data-ttu-id="86374-162">這種控制方式提供了更完善的責任制度。</span><span class="sxs-lookup"><span data-stu-id="86374-162">With this control comes a greater level of responsibility.</span></span>  
  
 ![](../core/media/handlingerrors.gif "HandlingErrors")  
  
 <span data-ttu-id="86374-163">配接器藉由檢查系統內容屬性決定訊息可重試次數**RetryCount**。</span><span class="sxs-lookup"><span data-stu-id="86374-163">The adapter determines the number of retries available on a message by checking the system context property **RetryCount**.</span></span> <span data-ttu-id="86374-164">配接器呼叫**重新提交**API 一次針對每個重試嘗試並傳入要重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="86374-164">The adapter calls the **Resubmit** API once for each retry attempt and passes in the message to be resubmitted.</span></span> <span data-ttu-id="86374-165">隨訊息一併傳入的還有時間戳記，指示引擎應於何時將訊息傳回配接器。</span><span class="sxs-lookup"><span data-stu-id="86374-165">Along with the message it passes the time stamp indicating when the engine should deliver the message back to the adapter.</span></span> <span data-ttu-id="86374-166">這個值通常是目前的時間加上值**RetryInterval**。</span><span class="sxs-lookup"><span data-stu-id="86374-166">This value should typically be the current time plus the value of **RetryInterval**.</span></span> <span data-ttu-id="86374-167">**RetryInterval**是系統的內容屬性的單位是分鐘。</span><span class="sxs-lookup"><span data-stu-id="86374-167">**RetryInterval** is a system context property whose units are minutes.</span></span> <span data-ttu-id="86374-168">這兩個**RetryCount**和**RetryInterval**訊息內容中是 傳送埠所設定的值。</span><span class="sxs-lookup"><span data-stu-id="86374-168">Both the **RetryCount** and **RetryInterval** in the message context are the values that are configured on the send port.</span></span> <span data-ttu-id="86374-169">以向外擴充部署為例，假設有一個 BizTalk 主控件將各執行個體部署至多部電腦。</span><span class="sxs-lookup"><span data-stu-id="86374-169">Consider a scaled-out deployment with instances of the same BizTalk Host deployed on multiple computers.</span></span> <span data-ttu-id="86374-170">如果訊息是在重試間隔過後傳遞，則訊息可能會傳遞給設定要在其中執行之任何一部電腦上的任一主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="86374-170">If the message is delivered after the retry interval has expired, the message may be delivered to the any one of the host instances on any of the computers where they are configured to run.</span></span> <span data-ttu-id="86374-171">所以配接器不應保留任何與試圖重試之訊息關聯的狀態，因為無法保證稍後仍會由配接器的相同執行個體負責傳輸。</span><span class="sxs-lookup"><span data-stu-id="86374-171">For this reason the adapter should not hold any state associated with a message to be used on the retry attempt because there is no guarantee that same instance of the adapter will be responsible for the transmission at a later time.</span></span>  
  
 <span data-ttu-id="86374-172">一旦重試計數小於或等於零，配接器就只能嘗試將訊息移至備份傳輸。</span><span class="sxs-lookup"><span data-stu-id="86374-172">The adapter should only attempt to move the message to the backup transport after the retry count is less than or equal to zero.</span></span> <span data-ttu-id="86374-173">如果連接埠沒有設定備份傳輸，嘗試將訊息移至備份傳輸便會失敗。</span><span class="sxs-lookup"><span data-stu-id="86374-173">An attempt to move the message to the backup transport will fail if there is no backup transport configured for the port.</span></span> <span data-ttu-id="86374-174">在此情況下應當擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="86374-174">In this case the message should be suspended.</span></span>  
  
 <span data-ttu-id="86374-175">下列程式碼片段示範如何從訊息內容判斷重試計數和重試間隔，並決定隨後應重新提交或是移至備份傳輸。</span><span class="sxs-lookup"><span data-stu-id="86374-175">The following code fragment illustrates how to determine the retry count and interval from the message context, and the subsequent resubmit or move to the backup transport.</span></span>  
  
```  
using Microsoft.XLANGs.BaseTypes;  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.BizTalk.TransportProxy.Interop;  
 …  
// RetryCount and RetyInterval are system context properties...  
private static readonly PropertyBase RetryCountProperty =   
 new BTS.RetryCount();  
private static readonly PropertyBase RetryIntervalProperty =   
 new BTS.RetryInterval();  
  
public void HandleRetry(IBaseMessage msg, IBTTransportBatch batch)  
{  
int retryCount = 0;  
int retryInterval = 0;  
  
// Get the RetryCount and RetryInterval off the msg ctx...  
 GetMessageRetryState(msg, out retryCount, out retryInterval);  
  
// If we have retries available resubmit, else move to   
 // backup transport...  
 if ( retryCount > 0 )  
batch.Resubmit(  
 msg, DateTime.Now.AddMinutes(retryInterval));  
else  
batch.MoveToNextTransport(msg);  
}  
  
public void GetMessageRetryState(  
 IBaseMessage msg,   
 out int retryCount,   
 out int retryInterval )  
{  
retryCount = 0;  
retryInterval = 0;  
  
object obj =  msg.Context.Read(  
RetryCountProperty.Name.Name,    
RetryCountProperty.Name.Namespace);   
  
if ( null != obj )  
retryCount = (int)obj;  
  
obj =  msg.Context.Read(  
RetryIntervalProperty.Name.Name,    
RetryIntervalProperty.Name.Namespace);   
  
if ( null != obj )  
retryInterval = (int)obj;  
}  
```  
  
## <a name="throwing-an-exception-from-transmitmessage"></a><span data-ttu-id="86374-176">從 TransmitMessage 擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="86374-176">Throwing an Exception from TransmitMessage</span></span>  
 <span data-ttu-id="86374-177">如果配接器會擲回例外狀況上任何 Api **IBTTransmitter.TransmitMessage**， **IBTTransmitterBatch.TransmitMessage**， **IBTTransmitterBatch.Done**，引擎相關的訊息傳輸視為傳輸失敗，並採取適當的動作訊息中所述[如何處理配接器失敗](../core/how-to-handle-adapter-failures.md)。</span><span class="sxs-lookup"><span data-stu-id="86374-177">If the adapter throws an exception on any of the APIs **IBTTransmitter.TransmitMessage**, **IBTTransmitterBatch.TransmitMessage**, **IBTTransmitterBatch.Done**, the engine treats the transmission of the messages involved as transmission failures and takes the appropriate action for the message, as detailed in [How to Handle Adapter Failures](../core/how-to-handle-adapter-failures.md).</span></span>  
  
 <span data-ttu-id="86374-178">可識別批次的傳送配接器若在 TransmitMessage API 執行期間擲回例外狀況，就會清除整個批次，並對該批次中的所有訊息執行傳輸失敗時的預設動作。</span><span class="sxs-lookup"><span data-stu-id="86374-178">For batch-aware send adapters, throwing an exception on the TransmitMessage API results in the entire batch being cleared and the default transmit failure actions being performed for all messages in that batch.</span></span>  
  
## <a name="solicit-response"></a><span data-ttu-id="86374-179">請求-回應</span><span class="sxs-lookup"><span data-stu-id="86374-179">Solicit-Response</span></span>  
 <span data-ttu-id="86374-180">雙向傳送配接器通常同時支援單向和雙向傳輸。</span><span class="sxs-lookup"><span data-stu-id="86374-180">Two-way send adapters typically support both one-way and two-way transmissions.</span></span> <span data-ttu-id="86374-181">傳送配接器會決定是否將訊息應該傳送為單向或雙向傳送藉由檢查**IsSolicitResponse**訊息內容中的系統內容屬性。</span><span class="sxs-lookup"><span data-stu-id="86374-181">The send adapter determines whether the message should be transmitted as a one-way or two-way send by inspecting the **IsSolicitResponse** system context property in the message context.</span></span>  
  
 <span data-ttu-id="86374-182">下列程式碼片段示範如何進行：</span><span class="sxs-lookup"><span data-stu-id="86374-182">The following code fragment demonstrates this:</span></span>  
  
```  
private bool portIsTwoWay = false;  
private static readonly PropertyBase IsSolicitResponseProperty= new BTS.IsSolicitResponse();  
  
...  
  
 // Port is one way or two way...  
 object obj =  this.message.Context.Read(  
 IsSolicitResponseProperty.Name.Name,    
 IsSolicitResponseProperty.Name.Namespace);   
  
if ( null != obj )  
 this.portIsTwoWay = (bool)obj;  
```  
  
 <span data-ttu-id="86374-183">在請求-回應傳輸期間，配接器會傳輸請求訊息。</span><span class="sxs-lookup"><span data-stu-id="86374-183">During a solicit-response transmission the adapter transmits the solicit message.</span></span> <span data-ttu-id="86374-184">完成此步驟後，配接器會提交關聯的回應，並指示傳訊引擎從 MessageBox 資料庫刪除原始請求訊息。</span><span class="sxs-lookup"><span data-stu-id="86374-184">After this completed it submits the associated response and tells the Messaging Engine to delete the original solicit message from the MessageBox database.</span></span> <span data-ttu-id="86374-185">從應用程式佇列刪除訊息與提交回應訊息的動作應該在同一批次的傳輸 Proxy 中執行。</span><span class="sxs-lookup"><span data-stu-id="86374-185">The action of deleting the message from the application queue should be performed in the same transport proxy batch as the submission of the response message.</span></span> <span data-ttu-id="86374-186">這可確保回應的刪除與提交為不可部分完成的作業。</span><span class="sxs-lookup"><span data-stu-id="86374-186">This ensures atomicity of the deletion and submission of the response.</span></span> <span data-ttu-id="86374-187">為達到完全不可部分完成性，配接器應使用 DTC 交易，以一致在相同的 DTC 交易環境下將請求訊息傳輸至可識別交易的資源、提交回應訊息及刪除請求訊息。</span><span class="sxs-lookup"><span data-stu-id="86374-187">For complete atomicity the adapter should use a DTC transaction whereby the transmission of the solicit message to a transaction-aware resource, submission of the response message, and deletion of the solicit message are all in the context of the same DTC transaction.</span></span> <span data-ttu-id="86374-188">一如既往地建議您，傳遞請求訊息請採用非封鎖式傳送。</span><span class="sxs-lookup"><span data-stu-id="86374-188">As always, we recommend that the solicit message is transmitted using a non-blocking send.</span></span>  
  
 <span data-ttu-id="86374-189">下列程式碼片段示範雙向傳送的主要概念。</span><span class="sxs-lookup"><span data-stu-id="86374-189">The following code fragment illustrates the main aspects of a two-way send.</span></span> <span data-ttu-id="86374-190">當引擎呼叫**IBTTransmitter.TransmitMessage**配接器將訊息傳送給記憶體中的佇列。</span><span class="sxs-lookup"><span data-stu-id="86374-190">When the engine calls **IBTTransmitter.TransmitMessage** the adapter enqueues the message to be transmitted to an in-memory queue.</span></span> <span data-ttu-id="86374-191">配接器傳回 `false` 以表示會執行非封鎖式傳送。</span><span class="sxs-lookup"><span data-stu-id="86374-191">The adapter returns `false` to indicate that it is performing a non-blocking send.</span></span> <span data-ttu-id="86374-192">配接器的執行緒集區 (**WorkerThreadThunk**) 記憶體中的佇列，並從佇列取出訊息遞交給 helper 方法。</span><span class="sxs-lookup"><span data-stu-id="86374-192">The adapter's thread pool (**WorkerThreadThunk**) services the in-memory queue and dequeues a message to hand it off to a helper method.</span></span> <span data-ttu-id="86374-193">該方法負責傳送請求訊息及接收回應訊息</span><span class="sxs-lookup"><span data-stu-id="86374-193">This method is responsible for sending the solicit message and receiving the response message.</span></span> <span data-ttu-id="86374-194">(此協助程式方法的實作已超出本主題的討論範圍)。回應訊息將提交至引擎，請求訊息則會從應用程式佇列刪除。</span><span class="sxs-lookup"><span data-stu-id="86374-194">(The implementation of this helper method is outside the scope of this topic.) The response message is submitted into the engine, and the solicit message is deleted from the application queue.</span></span>  
  
```  
using System.Collections;  
using Microsoft.XLANGs.BaseTypes;  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.BizTalk.TransportProxy.Interop;  
  
     static private Queue _transmitQueue = new Queue();  
  static private IBTTransportProxy _transportProxy = null;   
// IBTTransmitter...  
 public bool TransmitMessage(IBaseMessage msg)  
{  
// Add message to the transmit queue...  
lock(_transmitQueue.SyncRoot)  
 {  
_transmitQueue.Enqueue(msg);  
 }  
  
 return false;  
}  
  
 // Threadpool worker thread...   
private void WorkerThreadThunk()  
{  
try  
{  
 IBaseMessage solicitMsg = null;  
  
 lock(_transmitQueue.SyncRoot)  
 {  
 solicitMsg =   
 (IBaseMessage)_transmitQueue.Dequeue();  
}  
  
 IBaseMessage responseMsg = SendSolicitResponse(   
 solicitMsg );  
Callback cb = new Callback();  
  
IBTTransportBatch batch = _transportProxy.GetBatch(  
 cb, null);  
batch.SubmitResponseMessage( solicitMsg, responseMsg );  
batch.DeleteMessage( solicitMsg );  
batch.Done(null);  
}  
catch(Exception)  
{  
// Handle failure....  
}  
}  
  
static private IBaseMessage SendSolicitResponse(  
 IBaseMessage solicitMsg )  
{  
// Helper method to send solicit message and receive   
 // response message...  
IBaseMessage responseMsg = null;  
return responseMsg;  
}  
```  
  
## <a name="dynamic-sends"></a><span data-ttu-id="86374-195">動態傳送</span><span class="sxs-lookup"><span data-stu-id="86374-195">Dynamic Sends</span></span>  
 <span data-ttu-id="86374-196">動態傳送埠沒有配接器組態與其相關聯。</span><span class="sxs-lookup"><span data-stu-id="86374-196">Dynamic send ports do not have adapter configuration associated with them.</span></span> <span data-ttu-id="86374-197">反之，這類傳送埠使用處理常式組態，為配接器提供在動態連接埠上傳輸訊息所需的任何預設屬性。</span><span class="sxs-lookup"><span data-stu-id="86374-197">Instead they use handler configuration for any default properties that the adapter needs to transmit messages on a dynamic port.</span></span> <span data-ttu-id="86374-198">例如，HTTP 配接器可能需要使用 Proxy 且必須提供憑證。</span><span class="sxs-lookup"><span data-stu-id="86374-198">For example, an HTTP adapter may need to use a proxy and need to provide credentials.</span></span> <span data-ttu-id="86374-199">使用者名稱、密碼和連接埠可指定於處理常式組態中，而由配接器在執行階段予以快取。</span><span class="sxs-lookup"><span data-stu-id="86374-199">The user name, password, and port could be specified in the handler configuration that the adapter caches at run time.</span></span>  
  
 <span data-ttu-id="86374-200">引擎來判斷是，透過傳送動態訊息的傳輸**OutboundTransportLocation**加上配接器的別名。</span><span class="sxs-lookup"><span data-stu-id="86374-200">For the engine to determine the transport that a dynamic message is to be sent over, the **OutboundTransportLocation** is prefixed with the adapter's alias.</span></span> <span data-ttu-id="86374-201">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝期間，配接器可註冊一或多個別名。</span><span class="sxs-lookup"><span data-stu-id="86374-201">An adapter can register one or more aliases with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] at install time.</span></span> <span data-ttu-id="86374-202">剖析引擎**OutboundTransportLocation**在執行階段尋找相符項目。</span><span class="sxs-lookup"><span data-stu-id="86374-202">The engine parses the **OutboundTransportLocation** at run time to find a match.</span></span> <span data-ttu-id="86374-203">配接器會負責處理**OutboundTransportLocation** ，不論前面會加上別名。</span><span class="sxs-lookup"><span data-stu-id="86374-203">The adapter is responsible for handling the **OutboundTransportLocation** with or without the alias prepended to it.</span></span> <span data-ttu-id="86374-204">下表所示為現成的 BizTalk 配接器註冊的若干別名範例。</span><span class="sxs-lookup"><span data-stu-id="86374-204">The following table shows some examples of aliases registered for out-of-the-box BizTalk adapters.</span></span>  
  
|<span data-ttu-id="86374-205">配接器別名</span><span class="sxs-lookup"><span data-stu-id="86374-205">Adapter alias</span></span>|<span data-ttu-id="86374-206">配接器</span><span class="sxs-lookup"><span data-stu-id="86374-206">Adapter</span></span>|<span data-ttu-id="86374-207">OutboundTransportLocation 範例</span><span class="sxs-lookup"><span data-stu-id="86374-207">OutboundTransportLocation example</span></span>|  
|-------------------|-------------|---------------------------------------|  
|<span data-ttu-id="86374-208">HTTP://</span><span class="sxs-lookup"><span data-stu-id="86374-208">HTTP://</span></span>|<span data-ttu-id="86374-209">HTTP</span><span class="sxs-lookup"><span data-stu-id="86374-209">HTTP</span></span>|<span data-ttu-id="86374-210">http://www.</span><span class="sxs-lookup"><span data-stu-id="86374-210">http://www.</span></span> <span data-ttu-id="86374-211">MyCompany.com/bar</span><span class="sxs-lookup"><span data-stu-id="86374-211">MyCompany.com/bar</span></span>|  
|<span data-ttu-id="86374-212">HTTPS://</span><span class="sxs-lookup"><span data-stu-id="86374-212">HTTPS://</span></span>|<span data-ttu-id="86374-213">HTTP</span><span class="sxs-lookup"><span data-stu-id="86374-213">HTTP</span></span>|<span data-ttu-id="86374-214">https://www.</span><span class="sxs-lookup"><span data-stu-id="86374-214">https://www.</span></span> <span data-ttu-id="86374-215">MyCompany.com/bar</span><span class="sxs-lookup"><span data-stu-id="86374-215">MyCompany.com/bar</span></span>|  
|<span data-ttu-id="86374-216">mailto:</span><span class="sxs-lookup"><span data-stu-id="86374-216">mailto:</span></span>|<span data-ttu-id="86374-217">SMTP</span><span class="sxs-lookup"><span data-stu-id="86374-217">SMTP</span></span>|mailto:A.User@MyCompany.com|  
|<span data-ttu-id="86374-218">FILE://</span><span class="sxs-lookup"><span data-stu-id="86374-218">FILE://</span></span>|<span data-ttu-id="86374-219">FILE</span><span class="sxs-lookup"><span data-stu-id="86374-219">FILE</span></span>|<span data-ttu-id="86374-220">FILE://C:\MyCompany \\%MessageID%.xml</span><span class="sxs-lookup"><span data-stu-id="86374-220">FILE://C:\ MyCompany \\%MessageID%.xml</span></span>|