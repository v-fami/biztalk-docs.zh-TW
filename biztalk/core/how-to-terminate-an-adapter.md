---
title: 如何終止配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dfba2b61-b89f-41cd-a014-4e96daec6516
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd2621e15803dd5f6e8f449de530e84df1bc1b9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255990"
---
# <a name="how-to-terminate-an-adapter"></a><span data-ttu-id="b6c5b-102">如何終止配接器</span><span class="sxs-lookup"><span data-stu-id="b6c5b-102">How to Terminate an Adapter</span></span>
<span data-ttu-id="b6c5b-103">下列主題提供正確關閉配接器的指導。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-103">The following topics provide guidance on the proper shutdown of an adapter.</span></span>  
  
## <a name="terminating-an-adapter"></a><span data-ttu-id="b6c5b-104">終止配接器</span><span class="sxs-lookup"><span data-stu-id="b6c5b-104">Terminating an Adapter</span></span>  
 <span data-ttu-id="b6c5b-105">當傳訊引擎關閉時呼叫**IBTTransportControl**。**終止**上每個內含式配接器。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-105">When the Messaging Engine is shutting down it calls **IBTTransportControl**.**Terminate** on each in-process adapter.</span></span> <span data-ttu-id="b6c5b-106">在這個方法傳回之後，BizTalk Server 就會將配接器終結。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-106">After this method returns BizTalk Server will destroy the adapter.</span></span> <span data-ttu-id="b6c5b-107">對於原生配接器而言，這項作業會立即發生，但對於 Managed 配接器來說，這項作業的發生時間就比較不明確，這是因為 .NET 記憶體回收程序使然。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-107">For native adapters this occurs immediately, but for managed adapters exactly when this occurs is less deterministic due to the .NET garbage-collection process.</span></span> <span data-ttu-id="b6c5b-108">此配接器應該封鎖**Terminate**並且進行必要的清除工作，直到它已準備好終結。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-108">The adapter should block in **Terminate** and do any necessary cleanup work until it is ready to be destroyed.</span></span>  
  
## <a name="terminating-isolated-receive-adapters"></a><span data-ttu-id="b6c5b-109">終止外掛式接收配接器</span><span class="sxs-lookup"><span data-stu-id="b6c5b-109">Terminating Isolated Receive Adapters</span></span>  
 <span data-ttu-id="b6c5b-110">外掛式接收配接器沒有**Terminate**上呼叫，因為它們不會裝載在 BizTalk 服務。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-110">Isolated receive adapters do not have **Terminate** called on them because they are not hosted in the BizTalk service.</span></span> <span data-ttu-id="b6c5b-111">請改為呼叫**IBTTransportProxy**。**Ibttransportproxy**通知傳訊引擎它們即將關閉。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-111">Instead, they should call **IBTTransportProxy**.**TerminateIsolatedReceiver** to notify the Messaging Engine that they are about to shut down.</span></span>  
  
## <a name="clean-up-com-objects-by-using-marshalreleasecomobject"></a><span data-ttu-id="b6c5b-112">使用 Marshal.ReleaseComObject 清除 COM 物件</span><span class="sxs-lookup"><span data-stu-id="b6c5b-112">Clean Up COM Objects by Using Marshal.ReleaseComObject</span></span>  
 <span data-ttu-id="b6c5b-113">在寫入使用 COM 物件的 Managed 程式碼時，Common Language Runtime (CLR) 會產生 Proxy 物件以保存 COM 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-113">When writing managed code that uses COM objects, the common language runtime (CLR) generates proxy objects that hold the references to the COM objects.</span></span> <span data-ttu-id="b6c5b-114">Proxy 物件是 Managed 物件，受記憶體回收的一般規則管制。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-114">The proxy objects are managed objects and are subject to the usual rules of garbage collection.</span></span> <span data-ttu-id="b6c5b-115">當記憶體回收行程只看到 .NET 執行階段所配置的記憶體，而不知道有 COM 物件存在時，就會發生問題。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-115">A problem arises in that the garbage collector only sees memory that the .NET runtimes allocated, and is not aware of the COM object.</span></span> <span data-ttu-id="b6c5b-116">因為 Proxy 物件所佔空間很小，所以當 CLR 記憶體回收行程不知道有它的存在時，就可能導致記憶體中保留了所佔空間很大的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-116">Because the proxy objects are small, a large COM object might be left in memory because the CLR garbage collector is not aware of it.</span></span>  
  
 <span data-ttu-id="b6c5b-117">若要避免這個問題，明確釋放基礎 COM 物件時，您已完成，特別是任何**IBTTransportBatch**物件。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-117">To avoid this problem, explicitly release underlying COM objects when you are finished with them, particularly any **IBTTransportBatch** objects.</span></span> <span data-ttu-id="b6c5b-118">您可以呼叫**封送處理**。**ReleaseComObject**。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-118">You do this by calling **Marshal**.**ReleaseComObject**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6c5b-119">**ReleaseComObject**傳回剩餘參考的數目，並只釋放 COM 物件，此傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-119">**ReleaseComObject** returns the number of remaining references and only releases the COM object when this returned value is zero.</span></span> <span data-ttu-id="b6c5b-120">通常**ReleaseComObject**稱為在迴圈中，以確保釋放物件。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-120">Often **ReleaseComObject** is called in a loop to ensure that the object is released.</span></span> <span data-ttu-id="b6c5b-121">完成之後，您應該呼叫**SuppressFinalize**此物件上因為沒有完成的項目。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-121">After that is complete, you should call **SuppressFinalize** on this object because there is nothing to finalize.</span></span> <span data-ttu-id="b6c5b-122">最後一個步驟是檢查這是否真的是 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-122">One last step is to check whether this really is a COM object.</span></span>  
  
 <span data-ttu-id="b6c5b-123">下列的程式碼顯示上述的程序：</span><span class="sxs-lookup"><span data-stu-id="b6c5b-123">The following code shows the process descrjbed above:</span></span>  
  
```  
if (Marshal.IsComObject (batch))  
(  
While (0 <Marshal.ReleaseComObject(batch)  
;  
GC.SuppressFinalize (batch);  
  
```  
  
 <span data-ttu-id="b6c5b-124">明確地釋放**IBTTransportBatch**從傳回的物件**Ibttransportproxy**可大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-124">Explicitly releasing the **IBTTransportBatch** object returned from **GetBatch** can make a significant improvement to performance.</span></span>  
  
## <a name="always-use-terminate-when-closing-an-adapter"></a><span data-ttu-id="b6c5b-125">在關閉配接器時永遠使用終止</span><span class="sxs-lookup"><span data-stu-id="b6c5b-125">Always Use Terminate When Closing an Adapter</span></span>  
 <span data-ttu-id="b6c5b-126">將程式碼辨識為配接器的 BizTalk server，您必須實作介面呼叫**IBTTransportControl**。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-126">For BizTalk Server to recognize your code as an adapter, you must implement an interface called **IBTTransportControl**.</span></span> <span data-ttu-id="b6c5b-127">這個介面會定義 BizTalk Server 如何與您的配接器進行通訊，且定義如下：</span><span class="sxs-lookup"><span data-stu-id="b6c5b-127">This interface defines how BizTalk Server communicates with your adapter, and is defined as follows:</span></span>  
  
```  
public interface IBTTransportControl   
{  
void Initialize(IBTTransportProxy transportProxy);  
void Terminate();  
}  
```  
  
 <span data-ttu-id="b6c5b-128">介面包含兩個方法：**初始化**和**Terminate**。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-128">The interface contains two methods, **Initialize** and **Terminate**.</span></span>  
  
### <a name="initialize"></a><span data-ttu-id="b6c5b-129">[初始化]</span><span class="sxs-lookup"><span data-stu-id="b6c5b-129">Initialize</span></span>  
 <span data-ttu-id="b6c5b-130">BizTalk Server 會呼叫**初始化**方法之後載入配接器組件。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-130">BizTalk Server calls the **Initialize** method after it loads the adapter assembly.</span></span> <span data-ttu-id="b6c5b-131">這麼做可以將傳輸 Proxy (BizTalk Server 的主控點) 傳遞至配接器。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-131">It does this to pass the transport proxy (the main handle to BizTalk Server) to the adapter.</span></span> <span data-ttu-id="b6c5b-132">實作**初始化**只會傳輸 proxy 儲存在成員變數中。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-132">The implementation of **Initialize** simply stores the transport proxy in a member variable.</span></span>  
  
### <a name="terminate"></a><span data-ttu-id="b6c5b-133">Terminate</span><span class="sxs-lookup"><span data-stu-id="b6c5b-133">Terminate</span></span>  
 <span data-ttu-id="b6c5b-134">BizTalk Server 會呼叫**Terminate**方法在服務關閉，可讓配接器的時間完成所有批次的執行。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-134">BizTalk Server calls the **Terminate** method on service shutdown to give the adapter time to finish the execution of all batches.</span></span> <span data-ttu-id="b6c5b-135">這可讓實作**Terminate**方法更能配合。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-135">This makes the implementation of the **Terminate** method much more involved.</span></span>  
  
 <span data-ttu-id="b6c5b-136">配接器都不會傳回**Terminate**它有任何暫止的工作完成之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-136">The adapter should not return from a **Terminate** call until any pending work it has is complete.</span></span> <span data-ttu-id="b6c5b-137">當 BizTalk Server 呼叫**Terminate**，配接器應該嘗試停止所有目前的工作，不會啟動任何新的。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-137">When BizTalk Server calls **Terminate**, the adapter should try to stop all its current tasks and not start any new ones.</span></span>  
  
 <span data-ttu-id="b6c5b-138">因為**Terminate**稱為服務關閉的一部分，服務控制管理員會結束處理序永久地封鎖配接器如果**Terminate**。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-138">Because **Terminate** is called as part of the service shutdown, the service control manager ends the process if the adapter perpetually blocks in **Terminate**.</span></span> <span data-ttu-id="b6c5b-139">在這種情況下，服務控制管理員在停止 BizTalk Server 服務時會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-139">In this case, you see the warning from the service control manager as it stops the BizTalk Server service.</span></span> <span data-ttu-id="b6c5b-140">如有可能，請避免以這種方式永久地終止配接器。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-140">If possible, avoid terminating the adapter prematurely like this.</span></span> <span data-ttu-id="b6c5b-141">如果配接器未正確地處理終止程序，而且在程序開始關閉時仍有執行緒在執行，則您可能會在關閉時偶爾看到發生 BizTalk Server 存取違規的情況。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-141">If the adapter does not handle the termination process appropriately, and still has threads running when the process starts to shut down, then you may occasionally see an access violation from BizTalk Server on shutdown.</span></span>  
  
 <span data-ttu-id="b6c5b-142">因為這個 BizTalk Server 介面具有非同步的本質，所以在負載過低時可能會積存許多批次，因此造成仍有執行緒在執行中。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-142">Because of the asynchronous nature of the interface to BizTalk Server, it is likely that under load there will be many batches and therefore threads still being executed.</span></span> <span data-ttu-id="b6c5b-143">**Terminate**呼叫應該實作成等到配接器已順利在 BizTalk Server 上執行後再繼續每個批次結束時。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-143">The **Terminate** call should be implemented to wait on the conclusion of every batch the adapter has successfully executed on BizTalk Server before proceeding.</span></span> <span data-ttu-id="b6c5b-144">結束批次訊號是**BatchComplete**從 BizTalk Server 的回呼。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-144">The conclusion of the batch is signaled by the **BatchComplete** callback from BizTalk Server.</span></span> <span data-ttu-id="b6c5b-145">**Terminate**呼叫應該等候每個擱置**BatchComplete**發生。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-145">The **Terminate** call should wait on every pending **BatchComplete** to happen.</span></span> <span data-ttu-id="b6c5b-146">不過，批次的執行必須成功才行。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-146">However, the execution of the batch must be successful.</span></span> <span data-ttu-id="b6c5b-147">也就是說，呼叫**IBTTransportBatch**::**完成**絕不能失敗。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-147">That is, the call to **IBTTransportBatch**::**Done** must not fail.</span></span> <span data-ttu-id="b6c5b-148">如果呼叫**IBTTransportBatch**::**完成**失敗，沒有任何批次回呼。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-148">If the call to **IBTTransportBatch**::**Done** fails, there is no batch callback.</span></span>  
  
 <span data-ttu-id="b6c5b-149">在瞭解您必須對配接器新增同步化程式碼之後，實作就相當簡單。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-149">After you realize that you have to add synchronization code to your adapter, the implementation is fairly straightforward.</span></span>  
  
 <span data-ttu-id="b6c5b-150">其中一個簡單的方法為實作複合的同步化物件**輸入**和**保留**工作者執行緒的方法和**終止**方法時，該區塊執行緒目前仍在受保護的執行。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-150">One simple approach is to implement a compound synchronization object with **enter** and **leave** methods for the worker threads and a **terminate** method that blocks while a thread is still within the protected execution.</span></span> <span data-ttu-id="b6c5b-151">(附帶一提，解決方案是非常類似於熟悉的多個讀取器 / 單一寫入器結構所在的工作者執行緒可以視為讀取器和**終止**為寫入器的方法。)</span><span class="sxs-lookup"><span data-stu-id="b6c5b-151">(Incidentally, the solution is very similar to the familiar multiple-reader, single-writer structure where the worker threads can be thought of as readers and the **terminate** method as the writer.)</span></span>  
  
 <span data-ttu-id="b6c5b-152">**終止**方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="b6c5b-152">The **terminate** method is as follows:</span></span>  
  
```  
void terminate ()  
{  
this.control.Terminate();  
}  
```  
  
 <span data-ttu-id="b6c5b-153">對於每個工作者執行緒：</span><span class="sxs-lookup"><span data-stu-id="b6c5b-153">For each worker thread:</span></span>  
  
```  
If (!this.control.Enter())  
return; // we can’t enter because Terminate has been called  
try  
{  
//  create and fill batch  
batch.Done();  
}  
catch (Exception)  
{  
//  we are not expecting a callback  
This.control.Leave();  
}  
```  
  
 <span data-ttu-id="b6c5b-154">在來自 BizTalk Server 的回呼中：</span><span class="sxs-lookup"><span data-stu-id="b6c5b-154">In the callback from BizTalk Server:</span></span>  
  
```  
batchComplete (…)  
{  
//  the callback from BizTalk Server  
//  process results  
this.control.Leave();  
}  
```  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b6c5b-155"> 在「基本配接器」範例中提供 ControlledTermination.cs 範例程式碼，顯示本文所述的同步化機制。</span><span class="sxs-lookup"><span data-stu-id="b6c5b-155"> ships with sample code ControlledTermination.cs in the Base Adapter sample, showing the synchronization mechanism described here.</span></span>