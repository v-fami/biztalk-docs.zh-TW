---
title: 處理交易 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d360742-e969-4651-b364-9edc6a93b8d4
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 954d0e91e078c7f973bddc22961c760aa4080941
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248150"
---
# <a name="handling-transactions"></a><span data-ttu-id="8c6d0-102">處理交易</span><span class="sxs-lookup"><span data-stu-id="8c6d0-102">Handling Transactions</span></span>
## <a name="transacted-receivers"></a><span data-ttu-id="8c6d0-103">交易接收方</span><span class="sxs-lookup"><span data-stu-id="8c6d0-103">Transacted Receivers</span></span>  
 <span data-ttu-id="8c6d0-104">交易接收方與非交易接收方之間主要的差異，在於交易接收方會建立和使用明確的 MSDTC 交易，來確保其資料來源與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox 資料庫之間的不可部分完成性。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-104">The main difference between transacted receivers and nontransacted receivers is that transacted receivers create and use an explicit MSDTC transaction to ensure atomicity between their data source and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database.</span></span> <span data-ttu-id="8c6d0-105">就配接器的其他部分而言，通常都是相同的。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-105">In general every other aspect of the adapter is the same.</span></span>  
  
 <span data-ttu-id="8c6d0-106">應注意的是，要求-回應接收配接器只有在提交原始要求訊息至傳訊引擎時才會使用交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-106">It should be noted that a request-response receive adapter only uses a transaction for submitting the original request message to the Messaging Engine.</span></span> <span data-ttu-id="8c6d0-107">從傳訊引擎傳送至配接器的回應傳輸必須使用不同的交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-107">A different transaction is needed for the transmission of the response sent from the Messaging Engine to the adapter.</span></span> <span data-ttu-id="8c6d0-108">這是因為第一個交易的範圍是介於配接器與 MessageBox 資料庫之間。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-108">This is because the scope of the first transaction is between the adapter and the MessageBox database.</span></span> <span data-ttu-id="8c6d0-109">後續的要求訊息要等到原始要求訊息的交易認可後，才會從傳訊引擎傳送至配接器。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-109">The subsequent request message is not sent to the adapter from the Messaging Engine until the transaction for the original request message commits.</span></span>  
  
 <span data-ttu-id="8c6d0-110">底下的物件互動示意圖說明交易式提交內送訊息期間，配接器與傳訊引擎之間的互動。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-110">The following object interaction diagram illustrates the interaction between the adapter and the Messaging Engine during a transactional submission of incoming messages.</span></span> <span data-ttu-id="8c6d0-111">在此範例中，會依序發生下列互動：</span><span class="sxs-lookup"><span data-stu-id="8c6d0-111">In this example, the following sequence of interactions takes place:</span></span>  
  
1.  <span data-ttu-id="8c6d0-112">配接器從引擎取得新批次。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-112">The adapter gets a new batch from the engine.</span></span>  
  
2.  <span data-ttu-id="8c6d0-113">配接器建立新的 MSDTC 交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-113">The adapter creates a new MSDTC transaction.</span></span>  
  
3.  <span data-ttu-id="8c6d0-114">配接器對已經登錄於交易中的資料來源進行破壞性讀取。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-114">The adapter does a destructive read from its data source that has been enlisted in the transaction.</span></span>  
  
4.  <span data-ttu-id="8c6d0-115">配接器提交訊息。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-115">The adapter submits the message.</span></span>  
  
5.  <span data-ttu-id="8c6d0-116">配接器呼叫**完成**批次，並傳入其 MSDTC 交易並將其**BatchComplete**回呼指標。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-116">The adapter calls **Done** on the batch, passing in its MSDTC transaction and its **BatchComplete** callback pointer.</span></span> <span data-ttu-id="8c6d0-117">引擎傳回**IBTDTCCommitConfirm**介面。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-117">The engine returns an **IBTDTCCommitConfirm** interface.</span></span>  
  
6.  <span data-ttu-id="8c6d0-118">引擎會處理批次、 回呼配接器在其**BatchComplete**實作中，並傳達其訊息給配接器處理狀態。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-118">The engine processes the batch, calls the adapter back on its **BatchComplete** implementation, and conveys the status of its message processing to the adapter.</span></span>  
  
7.  <span data-ttu-id="8c6d0-119">如果批次成功的配接器會認同交易並呼叫**IBTDTCCommitConfirm.DTCCommitConfirm** API`true`認可的值。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-119">If the batch was successful the adapter commits the transaction and calls the **IBTDTCCommitConfirm.DTCCommitConfirm** API with a `true` value signifying commit.</span></span>  
  
 ![](../core/media/transactedreceiver.gif "TransactedReceiver")  
  
## <a name="transacted-transmitters"></a><span data-ttu-id="8c6d0-120">交易傳輸器</span><span class="sxs-lookup"><span data-stu-id="8c6d0-120">Transacted Transmitters</span></span>  
 <span data-ttu-id="8c6d0-121">交易配接器絕大部分都和非交易配接器非常相似。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-121">Transacted adapters are for the most part very similar to nontransacted adapters.</span></span> <span data-ttu-id="8c6d0-122">主要的差異，在於交易配接器會將訊息中的資料傳送至已經登錄於 MSDTC 交易中的資源。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-122">The main difference is that the transacted adapter sends the data in the message to a resource that it has enlisted in an MSDTC transaction.</span></span>  
  
 <span data-ttu-id="8c6d0-123">**實作秘訣：** 對於交易傳送，配接器應該使用相同的 MSDTC 交易將資料寫入目的地，以及刪除它透過**IBTTransportBatch.DeleteMessage**方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-123">**Implementation Tip:** For transacted sends, the adapter should use the same MSDTC transaction for writing the data to the destination and for deleting it through the **IBTTransportBatch.DeleteMessage** method call.</span></span> <span data-ttu-id="8c6d0-124">只需要交易這兩項作業即可。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-124">Only these two operations need to be transacted.</span></span> <span data-ttu-id="8c6d0-125">任何其他作業，例如**IBTTransportBatch.Resubmit**， **IBTTransportBatch.MoveToNextTransport**，和**IBTTransportBatch.MoveToSuspendQ**不需要是交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-125">Any other operations, such as **IBTTransportBatch.Resubmit**, **IBTTransportBatch.MoveToNextTransport**, and **IBTTransportBatch.MoveToSuspendQ** do not need to be transacted.</span></span> <span data-ttu-id="8c6d0-126">這是因為引擎會隱含地使用交易，而這些作業類型對目的地而言，不必是不可部分完成的。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-126">This is because the engine implicitly uses a transaction and these types of operations do not need to be atomic with respect to the destination.</span></span>  
  
 <span data-ttu-id="8c6d0-127">底下的物件互動示意圖說明配接器與引擎之間的互動。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-127">The following object interaction diagram illustrates the interactions between the adapter and the engine.</span></span> <span data-ttu-id="8c6d0-128">事件的順序如下：</span><span class="sxs-lookup"><span data-stu-id="8c6d0-128">The sequence of events is as follows:</span></span>  
  
1.  <span data-ttu-id="8c6d0-129">引擎從配接器取得新的批次。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-129">The engine gets a new batch from the adapter.</span></span>  
  
2.  <span data-ttu-id="8c6d0-130">引擎將兩個訊息加入至新批次。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-130">The engine adds two messages to the new batch.</span></span>  
  
3.  <span data-ttu-id="8c6d0-131">引擎會呼叫**完成**批次，促使配接器服務的內部傳輸佇列的批次張貼其執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-131">The engine calls **Done** on the batch, causing the adapter to post the batch to its internal transmit queue that is serviced by its thread pool.</span></span>  
  
4.  <span data-ttu-id="8c6d0-132">配接器建立新的 MSDTC 交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-132">The adapter creates a new MSDTC transaction.</span></span>  
  
5.  <span data-ttu-id="8c6d0-133">配接器傳輸訊息，將目的地登錄在 MSDTC 交易中。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-133">The adapter transmits the messages enlisting the destination in the MSDTC transaction.</span></span> <span data-ttu-id="8c6d0-134">例如，可能會是寫入 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-134">For example, this could be writing to a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database.</span></span>  
  
6.  <span data-ttu-id="8c6d0-135">在傳輸之後，配接器從引擎取得新的批次。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-135">After transmission, the adapter gets a new batch from the engine.</span></span>  
  
7.  <span data-ttu-id="8c6d0-136">配接器呼叫**DeleteMessage**已經成功傳輸的訊息。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-136">The adapter calls **DeleteMessage** for the messages that it has successfully transmitted.</span></span>  
  
8.  <span data-ttu-id="8c6d0-137">配接器呼叫**完成**傳入其 DTC 交易批次。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-137">The adapter calls **Done** on the batch passing in its DTC transaction.</span></span> <span data-ttu-id="8c6d0-138">引擎傳回**IBTDTCCommitConfirm**介面。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-138">The engine returns an **IBTDTCCommitConfirm** interface.</span></span>  
  
9. <span data-ttu-id="8c6d0-139">引擎處理該批次並從應用程式佇列刪除訊息。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-139">The engine processes the batch, deleting the messages from the application queue.</span></span>  
  
10. <span data-ttu-id="8c6d0-140">引擎回呼配接器的**IBTBatchCallback**成功刪除作業的相關資訊的介面。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-140">The engine calls back the adapter's **IBTBatchCallback** interface with information on the success of its deletion operations.</span></span>  
  
11. <span data-ttu-id="8c6d0-141">如果批次成功，配接器隨即認可交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-141">If the batch was successful, the adapter commits the transactions.</span></span>  
  
12. <span data-ttu-id="8c6d0-142">配接器呼叫**IBTDTCCommitConfirm.DTCCommitConfirm** ，告知引擎已成功認可交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-142">The adapter calls **IBTDTCCommitConfirm.DTCCommitConfirm** to inform the engine that the transaction was successfully committed.</span></span>  
  
 ![](../core/media/transactedtransmitter.gif "Transactedtransmitter")  
  
### <a name="transacted-solicit-response-adapters"></a><span data-ttu-id="8c6d0-143">交易請求-回應配接器</span><span class="sxs-lookup"><span data-stu-id="8c6d0-143">Transacted Solicit-Response Adapters</span></span>  
 <span data-ttu-id="8c6d0-144">與雙向接收不同，雙向傳送可以使用同一筆 DTC 交易來執行。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-144">Unlike two-way receives, two-way sends may be performed by using the same DTC transaction.</span></span> <span data-ttu-id="8c6d0-145">交易請求-回應配接器應該使用相同**IBTTransportBatch**如**SubmitResponseMessage**和**DeleteMessage**作業。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-145">Transacted solicit-response adapters should use the same **IBTTransportBatch** for the **SubmitResponseMessage** and **DeleteMessage** operations.</span></span> <span data-ttu-id="8c6d0-146">這個批次應該使用與用於傳送和接收請求-回應訊息組相同的 MSDTC 交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-146">This batch should use the same MSDTC transaction that is used to send and receive the solicit-response message pair.</span></span> <span data-ttu-id="8c6d0-147">這樣可以確保「請求-回應訊息交換」的不可部份完成性。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-147">This ensures atomicity for the solicit-response message exchange.</span></span>  
  
## <a name="service-components-and-byot"></a><span data-ttu-id="8c6d0-148">服務元件和 BYOT</span><span class="sxs-lookup"><span data-stu-id="8c6d0-148">Service Components and BYOT</span></span>  
 <span data-ttu-id="8c6d0-149">使用傳訊引擎 API 時，必須提供 MSDTC 交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-149">The Messaging Engine APIs require an MSDTC transaction to be supplied.</span></span> <span data-ttu-id="8c6d0-150">但有些 .NET 元件是設計用來當做服務元件，不允許透過程式設計方式認可或中止交易，</span><span class="sxs-lookup"><span data-stu-id="8c6d0-150">However some .NET components are designed to be used as serviced components and do not allow the transaction to be programmatically committed or aborted.</span></span> <span data-ttu-id="8c6d0-151">而是由該平台上的 COM+ 執行階段自動認可交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-151">Instead, the transaction is automatically committed by the COM+ runtime on that platform.</span></span>  
  
 <span data-ttu-id="8c6d0-152">在這些實例中，配接器應該使用 Bring Your Own Transaction (BYOT)。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-152">For these scenarios, the adapter should use Bring Your Own Transaction (BYOT).</span></span> <span data-ttu-id="8c6d0-153">這可以讓配接器建立 MSDTC 交易、產生使用交易的 .NET 元件，以及允許該元件繼承已建立的交易而不要建立它自己的交易。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-153">This allows the adapter to create an MSDTC transaction, instantiate the .NET component that uses the transaction, and allow that component to inherit the created transaction rather than create its own transaction.</span></span> <span data-ttu-id="8c6d0-154">.NET Framework 提供**System.EnterpriseServices.BYOT**針對此目的。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-154">The .NET Framework provides **System.EnterpriseServices.BYOT** for this purpose.</span></span> <span data-ttu-id="8c6d0-155">SDK BaseAdapter 提供 helper 類別， **BYOTTransaction**，針對此目的。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-155">The SDK BaseAdapter provides a helper class, **BYOTTransaction**, for this purpose.</span></span>  
  
## <a name="avoiding-race-conditions"></a><span data-ttu-id="8c6d0-156">避免競爭條件</span><span class="sxs-lookup"><span data-stu-id="8c6d0-156">Avoiding Race Conditions</span></span>  
 <span data-ttu-id="8c6d0-157">當您撰寫建立交易物件的配接器，並將它交付至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，您就有責任要撰寫執行以下工作的程式碼：</span><span class="sxs-lookup"><span data-stu-id="8c6d0-157">When you write an adapter that creates a transaction object and hands it to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you are accepting responsibility for writing code that does the following:</span></span>  
  
-   <span data-ttu-id="8c6d0-158">在與批次關聯的訊息中解決錯誤。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-158">Resolves errors in messages associated with the batch.</span></span>  
  
-   <span data-ttu-id="8c6d0-159">決定與批次作業關聯之交易的最後結果。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-159">Decides the final outcome of the transaction associated with the batch operation.</span></span>  
  
 <span data-ttu-id="8c6d0-160">配接器必須通知 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 關於交易的最後結果，以維護其內部追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-160">The adapter must inform [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] about the final outcome of the transaction to maintain its internal tracking data.</span></span> <span data-ttu-id="8c6d0-161">配接器會[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]藉由呼叫結果的**DTCConfirmCommit**。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-161">The adapter informs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] of the outcome by calling **DTCConfirmCommit**.</span></span> <span data-ttu-id="8c6d0-162">如果配接器不這麼做，就會發生嚴重的記憶體遺漏。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-162">If the adapter does not do this, a significant memory leak occurs.</span></span>  
  
 <span data-ttu-id="8c6d0-163">以上所列的兩個工作 （解決錯誤，並決定最終的結果） 似乎相當簡單，但事實上它們依賴從不同執行緒的資訊：</span><span class="sxs-lookup"><span data-stu-id="8c6d0-163">The two tasks listed above (resolve errors and decide the final outcome) seem simple enough, but in fact they rely on information from different threads:</span></span>  
  
-   <span data-ttu-id="8c6d0-164">配接器處理所傳遞的資訊為基礎的錯誤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至**BatchComplete**配接器中的回呼。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-164">The adapter processes errors based on information passed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the **BatchComplete** callback in the adapter.</span></span> <span data-ttu-id="8c6d0-165">這個回呼位於配接器的執行緒上。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-165">This callback is on the adapter's thread.</span></span>  
  
-   <span data-ttu-id="8c6d0-166">**DTCConfirmCommit**上是一種方法**IBTDTCCommitConfirm**物件。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-166">**DTCConfirmCommit** is a method on the **IBTDTCCommitConfirm** object.</span></span> <span data-ttu-id="8c6d0-167">執行個體**IBTDTCCommitConfirm**批次所傳回物件**ibttransportbatch:: Done**呼叫。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-167">An instance of the **IBTDTCCommitConfirm** object is returned by the batch **IBTTransportBatch::Done** call.</span></span> <span data-ttu-id="8c6d0-168">這個執行個體位於相同的執行緒**ibttransportbatch:: Done**呼叫，這是配接器的執行緒不同。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-168">This instance is on the same thread as the **IBTTransportBatch::Done** call, which is different from the adapter's thread.</span></span>  
  
-   <span data-ttu-id="8c6d0-169">配接器對每次呼叫**ibttransportbatch:: Done**沒有對應的回呼**BatchComplete**，也就是呼叫，傳訊引擎不同的執行緒中報告的結果批次提交。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-169">For every call that the adapter makes to **IBTTransportBatch::Done** there is a corresponding callback, **BatchComplete**, that is called by the Messaging Engine in a separate thread to report the result of the batch submission.</span></span> <span data-ttu-id="8c6d0-170">在**BatchComplete**批次的配接器必須認可或回復交易根據是否成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-170">In **BatchComplete** the adapter needs to commit or roll back the transaction based on whether the batch passed or failed.</span></span> <span data-ttu-id="8c6d0-171">在任一情況下，配接器應該都會接著呼叫**DTCConfirmCommit**回報給傳訊引擎交易的狀態。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-171">In either case, the adapter should then call **DTCConfirmCommit** to report the status of the transaction to the Messaging Engine.</span></span>  
  
 <span data-ttu-id="8c6d0-172">可能的競爭情形存在是因為配接器的實作**BatchComplete**可能會假設**IBTDTCCommitConfirm**所傳回物件**ibttransportbatch:: Done**時一律可以使用**BatchComplete**執行。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-172">A possible race condition exists because the adapter’s implementation of **BatchComplete** can assume that the **IBTDTCCommitConfirm** object returned by **IBTTransportBatch::Done** is always available when **BatchComplete** executes.</span></span> <span data-ttu-id="8c6d0-173">不過， **BatchComplete**時，才能呼叫個別的傳訊引擎執行緒，即使之前**ibttransportbatch:: Done**傳回。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-173">However, **BatchComplete** can be called in a separate Messaging Engine thread, even before **IBTTransportBatch::Done** returns.</span></span> <span data-ttu-id="8c6d0-174">可能的配接器嘗試存取**IBTDTCCommitConfirm**物件的一部分**BatchComplete**實作中，沒有發生存取違規。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-174">It is possible that when the adapter tries to access the **IBTDTCCommitConfirm** object as a part of the **BatchComplete** implementation, there is an access violation.</span></span>  
  
 <span data-ttu-id="8c6d0-175">在下列範例中，將使用事件來解決問題。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-175">The problem is solved with an event in the following example.</span></span> <span data-ttu-id="8c6d0-176">這裡會使用事件的屬性來存取介面指標。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-176">Here the interface pointer is accessed through a property that uses the event.</span></span> <span data-ttu-id="8c6d0-177">Get 方法永遠會等候 Set 方法完成。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-177">The get always waits for the set.</span></span>  
  
```  
protected IBTDTCCommitConfirm CommitConfirm  
{  
   set  
   {  
       this.commitConfirm = value;  
       this.commitConfirmEvent.Set();  
   }  
   get  
   {  
       this.commitConfirmEvent.WaitOne();  
       return this.commitConfirm;  
   }  
}  
protected IBTDTCCommitConfirm commitConfirm = null;  
private ManualResetEvent commitConfirmEvent = new ManualResetEvent(false);  
```  
  
 <span data-ttu-id="8c6d0-178">現在將指派的傳回值**ibttransportbatch:: Done**給這個屬性，並使用它在**BatchComplete**呼叫。</span><span class="sxs-lookup"><span data-stu-id="8c6d0-178">Now assign the return value from **IBTTransportBatch::Done** to this property and use it in the **BatchComplete** call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6d0-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c6d0-179">See Also</span></span>  
 [<span data-ttu-id="8c6d0-180">交易式訊息批次</span><span class="sxs-lookup"><span data-stu-id="8c6d0-180">Transactional Message Batches</span></span>](../core/transactional-message-batches.md)