---
title: 檢測解決方案： 逐步 API 用量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9e027ab-1927-4905-8970-8061ac55d591
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73c59ab28c228c779fd9e6e84d836b87415d6386
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22258230"
---
# <a name="instrumenting-a-solution-step-by-step-api-usage"></a><span data-ttu-id="70ef8-102">檢測解決方案： 逐步 API 使用方式</span><span class="sxs-lookup"><span data-stu-id="70ef8-102">Instrumenting a Solution: Step-by-Step API Usage</span></span>
<span data-ttu-id="70ef8-103">這個主題會說明如何使用重要的 BAM API 類別來檢測應用程式。</span><span class="sxs-lookup"><span data-stu-id="70ef8-103">This topic describes how to instrument an application using the key BAM API class.</span></span> <span data-ttu-id="70ef8-104">在下列的程式碼片段中，我們藉由使用常數以及檢測應用程式所需的最少程式碼，將範例程式碼簡化。</span><span class="sxs-lookup"><span data-stu-id="70ef8-104">In the following code snippets we have simplified the sample code by using constants and by using the minimum code necessary to instrument an application.</span></span>  
  
 <span data-ttu-id="70ef8-105">下列程式碼片段將示範如何建立新的 [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) 物件，亦即 [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx)。</span><span class="sxs-lookup"><span data-stu-id="70ef8-105">The following code snippet demonstrates how you create a new [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) object, specifically a [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx).</span></span> <span data-ttu-id="70ef8-106">在這個程式碼片段中，第一個參數指定 BAM 主要匯入資料庫之資料存放區的連接字串，第二個參數則指定將事件寫入資料存放區的頻率。</span><span class="sxs-lookup"><span data-stu-id="70ef8-106">In this snippet, the first parameter specifies the connection string to the data store of the BAM Primary Import database and the second parameter specifies the frequency with which the events are written to the data store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70ef8-107">BAM 僅支援與 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料存放區的連接。</span><span class="sxs-lookup"><span data-stu-id="70ef8-107">BAM supports connections only to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] data stores.</span></span> <span data-ttu-id="70ef8-108">這裡的範例連接字串代表建立連接所需的最少連接字串。</span><span class="sxs-lookup"><span data-stu-id="70ef8-108">The sample connection string represents the minimal connection string required to establish a connection.</span></span> <span data-ttu-id="70ef8-109">您的組態可能需要在連接字串中指定其他的參數。</span><span class="sxs-lookup"><span data-stu-id="70ef8-109">Your configuration may require additional parameters to be specified in the connection string.</span></span>  
  
 <span data-ttu-id="70ef8-110">*FlushThreshold* 值為 0 時，指定不會自動寫入事件，您必須呼叫 Flush 方法來寫入事件。</span><span class="sxs-lookup"><span data-stu-id="70ef8-110">A *FlushThreshold* value of 0 specifies that events are not automatically written and that you must call the Flush method to write the events.</span></span> <span data-ttu-id="70ef8-111">值為 1 時，每個事件在發生時即會寫入。</span><span class="sxs-lookup"><span data-stu-id="70ef8-111">A value of one causes each event to be written when it occurs.</span></span> <span data-ttu-id="70ef8-112">值大於 1 時，指定會在發生指定的累積量時寫入事件。</span><span class="sxs-lookup"><span data-stu-id="70ef8-112">Values of greater than one specify that events are written when a batch of the specified accumulation has occurred.</span></span> <span data-ttu-id="70ef8-113">使用大於 1 的值時，對於提升效能很有用。</span><span class="sxs-lookup"><span data-stu-id="70ef8-113">Using a value of greater than one can be useful to enhance performance.</span></span>  
  
```  
// Specify the DES connection string.  
const string connBAMPIT =  
   "Integrated Security=SSPI;server=.;database=BAMPrimaryImport";  
// Write the activity update data on every call.  
int flushThreshold = 1;  
// Create a DES instance  
EventStream es =   
   new DirectEventStream(connBAMPIT, flushThreshold);  
```  
  
 <span data-ttu-id="70ef8-114">一旦建立了 [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) 物件，您就可以開始活動，並使用收集到的里程碑和資料開始更新活動資料表。</span><span class="sxs-lookup"><span data-stu-id="70ef8-114">Once the [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) object has been created, you can begin the activity and start updating the activity table with the collected milestones and data.</span></span> <span data-ttu-id="70ef8-115">在部署 BAM 活動時，會在 BAM 主要匯入資料庫中建立 5 個資料表。</span><span class="sxs-lookup"><span data-stu-id="70ef8-115">When the BAM activity was deployed, five tables were created in the BAM Primary Import database.</span></span> <span data-ttu-id="70ef8-116">如需開發程序的詳細資訊，請參閱[BAM 開發程序概觀](../core/overview-of-the-bam-development-process.md)。</span><span class="sxs-lookup"><span data-stu-id="70ef8-116">For more information about the development process, see [Overview of the BAM Development Process](../core/overview-of-the-bam-development-process.md).</span></span>  
  
 <span data-ttu-id="70ef8-117">呼叫 [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) 方法，就會將記錄加入 bam_ PurchaseOrder_Activity 資料表。</span><span class="sxs-lookup"><span data-stu-id="70ef8-117">Calling the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method adds a record to the bam_ PurchaseOrder_Activity table.</span></span> <span data-ttu-id="70ef8-118">第一個參數包含正在更新之活動的名稱，第二個參數則包含這個活動執行個體的識別碼。</span><span class="sxs-lookup"><span data-stu-id="70ef8-118">The first parameter contains the name of the activity being updated and the second parameter contains an identifier for this instance of the activity.</span></span> <span data-ttu-id="70ef8-119">識別碼可以是任何字串，但是在活動的記錄集中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="70ef8-119">The identifier can be any string, but it must be unique in the record set for the activity.</span></span>  
  
 <span data-ttu-id="70ef8-120">此時該記錄不包含任何資料。</span><span class="sxs-lookup"><span data-stu-id="70ef8-120">At this point the record does not contain any data.</span></span> <span data-ttu-id="70ef8-121">[Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) 方法會使用擷取的事件資料來更新記錄。</span><span class="sxs-lookup"><span data-stu-id="70ef8-121">The [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) method updates the record with the captured event data.</span></span> <span data-ttu-id="70ef8-122">請再次指定活動以及活動執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="70ef8-122">Once again you specify an activity and the activity instance identifier.</span></span> <span data-ttu-id="70ef8-123">您可傳遞在活動中所定義之資料項目和里程碑的 [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) 方法名稱值組。</span><span class="sxs-lookup"><span data-stu-id="70ef8-123">You pass the [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) method name value pairs of data items and milestones you defined in the activity.</span></span> <span data-ttu-id="70ef8-124">例如，我們的活動定義了名為 MS_Received 的里程碑。</span><span class="sxs-lookup"><span data-stu-id="70ef8-124">For example, our activity defined a milestone MS_Received.</span></span> <span data-ttu-id="70ef8-125">在部署活動時，會在 bam_ PurchaseOrder_Activity 資料表中建立里程碑的資料行。</span><span class="sxs-lookup"><span data-stu-id="70ef8-125">When the activity was deployed, a column in the bam_ PurchaseOrder_Activity table was created for the milestone.</span></span> <span data-ttu-id="70ef8-126">呼叫 [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) 方法可指定 MS_Received 和 DateTime.UtcNow 的名稱值組，以使用收到訂購單的日期來更新活動。</span><span class="sxs-lookup"><span data-stu-id="70ef8-126">The call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) method specifies the name value pair of MS_Received and DateTime.UtcNow to update the activity with received date for the purchase order.</span></span>  
  
```  
// When a purchase order is received, you call the  
// BeginActivity method in the receive application.  
// You can then capture the event data by calling   
// the UpdateActivity method.  
es.BeginActivity ("PurchaseOrder", "PO123");  
es.UpdateActivity ("PurchaseOrder", "PO123",  
                    "MS_Received", DateTime.UtcNow,   
                    "T_Customer", "Joe");  
```  
  
 <span data-ttu-id="70ef8-127">在這個範例中，我們繼續進行第二個活動。</span><span class="sxs-lookup"><span data-stu-id="70ef8-127">In this sample we continue to a second activity.</span></span> <span data-ttu-id="70ef8-128">如需有關接續的詳細資訊，請參閱[活動接續](../core/activity-continuation.md)。</span><span class="sxs-lookup"><span data-stu-id="70ef8-128">For more information about continuations, see [Activity Continuation](../core/activity-continuation.md).</span></span>  
  
 <span data-ttu-id="70ef8-129">若要讓其他已檢測的應用程式更新 PurchaseOrder 活動，您可以在 [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) 方法中加入呼叫。</span><span class="sxs-lookup"><span data-stu-id="70ef8-129">To enable other instrumented applications to update the PurchaseOrder activity, you include a call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method.</span></span> <span data-ttu-id="70ef8-130">此呼叫會指定其他應用程式可以提供的活動、所追蹤之活動執行個體的識別碼，以及其他應用程式會用來更新活動的接續 Token。</span><span class="sxs-lookup"><span data-stu-id="70ef8-130">The call specifies the activity to which other applications can contribute, the identifier for the instance of the activity being tracked, and the continuation token that other applications will use to update the activity.</span></span> <span data-ttu-id="70ef8-131">記錄會寫入 bam_ PurchaseOrder_continuations 資料表以追蹤接續的狀態。</span><span class="sxs-lookup"><span data-stu-id="70ef8-131">A record is written to the bam_ PurchaseOrder_continuations table to track the status of the continuation.</span></span> <span data-ttu-id="70ef8-132">如果活動繼續執行其他處理序，便會使用唯一的接續 Token，針對 [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) 方法的每個呼叫寫入記錄。</span><span class="sxs-lookup"><span data-stu-id="70ef8-132">If the activity continues to other processes, a record is written for each call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method with a unique continuation token.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="70ef8-133">在接續狀況中的每個程式碼片段必須有自己的 [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) 方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="70ef8-133">Every code segment in a continuation scenario must have its own [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method call.</span></span> <span data-ttu-id="70ef8-134">不這麼做會導致活動記錄懸空/被遺棄。</span><span class="sxs-lookup"><span data-stu-id="70ef8-134">Failing to do so will result in a dangling/orphaned activity record.</span></span>  
>   
>  <span data-ttu-id="70ef8-135">不過，只有第一個區段 (使用實際活動識別碼) 具有 [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) 方法；所有其他區段 (使用自己的唯一 Token 識別碼) 都不得呼叫 [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="70ef8-135">However, only the first segment (that uses the actual activity ID) has the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method; all the other segments (that use their own unique token ID) must not call the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method.</span></span>  
  
 <span data-ttu-id="70ef8-136">呼叫 [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) 方法後，其他元件可以使用指定接續 Token 而非活動識別碼的 [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) 來更新訂購單活動。</span><span class="sxs-lookup"><span data-stu-id="70ef8-136">After the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method is called, other components can update the purchase order activity using [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) specifying the continuation token instead of the activity ID.</span></span> <span data-ttu-id="70ef8-137">當其他元件完成其工作時，每個元件都必須使用接續 Token 呼叫 [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) ，通知未預期其他事件的 BAM 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="70ef8-137">When the other components have completed their tasks, each of the components must call [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) with the continuation token to inform the BAM infrastructure that no more events are expected.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="70ef8-138">一旦呼叫了 [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) 方法，如果繼續執行活動的處理序一直沒有使用接續 Token 呼叫 [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) 方法，活動就可能被遺棄。</span><span class="sxs-lookup"><span data-stu-id="70ef8-138">Once the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method is called, it is possible for an activity to become orphaned if the process in which the activity is continued never calls an [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method with the continuation token.</span></span>  
  
```  
// Continue the activity to the next process that has been  
// instrumented to handle the continuation.  
es.EnableContinuation("PurchaseOrder", “PO123”, “AP123”);  
```  
  
 <span data-ttu-id="70ef8-139">最後，會呼叫指定活動名稱和活動識別碼的 [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) 方法來完成活動。</span><span class="sxs-lookup"><span data-stu-id="70ef8-139">Finally, the activity is finalized by calling the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method specifying the activity name and the activity identifier.</span></span> <span data-ttu-id="70ef8-140">如果沒有未完成的接續活動，活動就會移到 bam_ PurchaseOrder _completed 資料表。</span><span class="sxs-lookup"><span data-stu-id="70ef8-140">If there are no unfinished continuations, the activity is moved to the bam_ PurchaseOrder _completed table.</span></span> <span data-ttu-id="70ef8-141">如果接續活動無法完成，活動就可能被遺棄。</span><span class="sxs-lookup"><span data-stu-id="70ef8-141">It is possible for activities to become orphaned if continuation activities fail to complete.</span></span>  
  
```  
// Activity from this segment (PO submission) is completed  
es.EndActivity("PurchaseOrder", “PO123”);  
```  
  
 <span data-ttu-id="70ef8-142">當活動繼續分隔處理序時，會藉由呼叫指定在 [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) 方法呼叫中宣告之活動名稱和接續 Token的 [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) ，來檢測應用程式以更新活動資料表。</span><span class="sxs-lookup"><span data-stu-id="70ef8-142">When the activity continues to separate process, the application is instrumented to update the activity table by calling [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) specifying the activity name and the continuation token declared in the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70ef8-143">處理接續活動的處理序不會呼叫 [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="70ef8-143">The process handling the continued activity does not call the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method.</span></span> <span data-ttu-id="70ef8-144">[Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) 方法會在 BAM 主要匯入資料庫中建立資料表，以建立活動的執行個體。</span><span class="sxs-lookup"><span data-stu-id="70ef8-144">The [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method creates an instance of the activity by creating the tables in the BAM Primary Import database.</span></span> <span data-ttu-id="70ef8-145">接續活動的程序會更新已存在活動的執行個體。</span><span class="sxs-lookup"><span data-stu-id="70ef8-145">The process to which the activity is continued is updating the instance of the already existing activity.</span></span>  
  
```  
// update when the order is approved  
es.UpdateActivity ("PurchaseOrder", “AP123”, "MS_Approved",  
                    DateTime.UtcNow, "T_Product", "Widget");  
  
// update when the product is ready for shipment  
es.UpdateActivity ("PurchaseOrder", “AP123”,  
                   "MS_Ready", DateTime.UtcNow);  
```  
  
 <span data-ttu-id="70ef8-146">在此範例的部分工作流程中程式碼指定了參考，在此例中是一種特定的參考類型，也就是相關活動。</span><span class="sxs-lookup"><span data-stu-id="70ef8-146">Part of the workflow for this sample the code specifies a reference, in this case a specific type of reference - a related activity.</span></span> <span data-ttu-id="70ef8-147">藉由指定相關的活動，您可以從主要活動建立與其他活動的連結，而這些活動是在 BAM 入口網站中檢視活動的使用者感興趣的活動。</span><span class="sxs-lookup"><span data-stu-id="70ef8-147">By specifying a related activity you create a link from your primary activity to other activities that are of interest to a user viewing the activity in the BAM portal.</span></span>  
  
 <span data-ttu-id="70ef8-148">呼叫 [Microsoft.BizTalk.Bam.EventObservation.EventStream.AddRelatedActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.addrelatedactivity.aspx) 方法會將記錄寫入連結活動的 bam_ PurchaseOrder_ActiveRelationships。</span><span class="sxs-lookup"><span data-stu-id="70ef8-148">The call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.AddRelatedActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.addrelatedactivity.aspx) method writes a record to the bam_ PurchaseOrder_ActiveRelationships linking the activities.</span></span>  
  
```  
// These are shipped in two shipments.  
// Relates the current purchase order   
// instance to two shippings.  
// Note: only one direction  
es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                       "Shipping", “UPS101”);  
es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                       "Shipping", “UPS102”);  
```  
  
 <span data-ttu-id="70ef8-149">若要結束接續活動，請呼叫 [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) 方法，指定要結束之接續活動的接續 Token。</span><span class="sxs-lookup"><span data-stu-id="70ef8-149">To end the continued activity you call the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method specifying the continuation token for the continuation that is ending.</span></span> <span data-ttu-id="70ef8-150">如果沒有其他未完成的接續活動，訂單活動就會移到已完成的資料表。</span><span class="sxs-lookup"><span data-stu-id="70ef8-150">If there are no other unfinished continuations, the purchase order activity is moved to the completed table.</span></span>  
  
```  
// Activity from this segment (ApprovalProcess) is completed  
es.EndActivity("PurchaseOrder", “AP123”);  
```  
  
## <a name="complete-code-sample"></a><span data-ttu-id="70ef8-151">完整的程式碼範例</span><span class="sxs-lookup"><span data-stu-id="70ef8-151">Complete Code Sample</span></span>  
  
```  
//---------------------------------------------------------------------  
// File:BAMMinimalSample.cs  
//   
// Summary: Demonstrates how to instrument an application   
//using BAM APIs to track useful information.  
//  
// Sample: BAM Api Sample  
//  
//---------------------------------------------------------------------  
// This file is part of the Microsoft BizTalk Server SDK  
//  
// Copyright (c) Microsoft Corporation. All rights reserved.  
//  
// This source code is intended only as a supplement to Microsoft   
// BizTalk Server release and/or on-line documentation. See   
// these other materials for detailed information regarding Microsoft // code samples.  
//  
// THIS CODE AND INFORMATION ARE PROVIDED "AS IS" WITHOUT WARRANTY OF  
// ANY KIND, WHETHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO // THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A   
// PARTICULAR PURPOSE.  
//---------------------------------------------------------------------  
// This sample requires that you add the     
// Microsoft.BizTalk.Bam.EventObservation.dll to the   
// references in the Visual Studio Solution.  
  
using System;  
using System.Text;  
using Microsoft.BizTalk.Bam.EventObservation;  
  
namespace EventStreamSample  
{  
  
    static void Main(string[] args)  
    {  
        //   
  // The following code would appear in a purchase order  
   // receipt application.  
        //  
  
        // Specify the DES connection string.  
        const string connBAMPIT =  
            "Integrated Security=SSPI;server=.;database=BAMPrimaryImport";  
  
        // Write the activity update data on every call.  
        int flushThreshold = 1;  
  
        // Create an instance of the DirectEventStream.  
        EventStream es =   
               new DirectEventStream(connBAMPIT, flushThreshold);  
  
        // When a purchase order is received, you call the  
       // BeginActivity method in the receive application.  
  // You can then capture the event data by calling   
        // the UpdateActivity method.  
        es.BeginActivity ("PurchaseOrder", "PO123");  
        es.UpdateActivity ("PurchaseOrder", "PO123",  
                    "MS_Received", DateTime.UtcNow,   
                    "T_Customer", "Joe");  
  
   // Continue the activity to the next process that has been  
   // instrumented to handle the continuation.  
        es.EnableContinuation("PurchaseOrder", “PO123”, “AP123”);  
  
        // Activity from this segment (PO submission) is completed  
        // end activity is synonymous to IsCompleted = 1  
        es.EndActivity("PurchaseOrder", “PO123”);  
  
        //  
        // The following code would typically appear in a separate   
        // application that monitors the approval process  
        // (ApprovalProcess.exe)  
        //  
  
        // update when the order is approved  
        es.UpdateActivity ("PurchaseOrder", “AP123”, "MS_Approved",  
                            DateTime.UtcNow, "T_Product", "Widget");  
  
        // update when the product is ready for shipment  
        es.UpdateActivity ("PurchaseOrder", “AP123”,  
                            "MS_Ready", DateTime.UtcNow);  
  
        // These are shipped in two shipments.  
        // Relates the current purchase order  
        // instance to two shippings.  
        // Note: only one direction  
        es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                                "Shipping", “UPS101”);  
        es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                                "Shipping", “UPS102”);  
  
        // Activity from this segment (ApprovalProcess) is completed  
        es.EndActivity("PurchaseOrder", “AP123”);  
  
        // In another Shipping application, two shipments with  
            ID’s UPS101 and UPS102 will be created.  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="70ef8-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70ef8-152">See Also</span></span>  
 [<span data-ttu-id="70ef8-153">使用事件資料流實作 BAM 活動</span><span class="sxs-lookup"><span data-stu-id="70ef8-153">Implementing BAM Activities with Event Streams</span></span>](../core/implementing-bam-activities-with-event-streams.md)