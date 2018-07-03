---
title: 持續性和協調流程引擎 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestration engine, persistence
- persistence
- orchestration engine, serialization
ms.assetid: 088230ef-13b3-440b-9875-6449f29dd5c6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d61d6665ba0828fb6cf24ef71ffb04fbcb94d5e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022516"
---
# <a name="persistence-and-the-orchestration-engine"></a><span data-ttu-id="11e50-102">持續性及協調流程引擎</span><span class="sxs-lookup"><span data-stu-id="11e50-102">Persistence and the Orchestration Engine</span></span>
<span data-ttu-id="11e50-103">狀態持續性及其管理與還原，構成協調流程引擎許多基本功能的基礎。</span><span class="sxs-lookup"><span data-stu-id="11e50-103">State persistence, its management and restoration form the basis of a lot of fundamental functionalities of the orchestration engine.</span></span> <span data-ttu-id="11e50-104">特別是持續性，對下列功能的運作尤為重要：</span><span class="sxs-lookup"><span data-stu-id="11e50-104">In particular, persistence is critical to the correct functioning of:</span></span>  
  
- <span data-ttu-id="11e50-105">凍結和解除凍結</span><span class="sxs-lookup"><span data-stu-id="11e50-105">Dehydration and rehydration</span></span>  
  
- <span data-ttu-id="11e50-106">與電腦無關的執行和解除凍結</span><span class="sxs-lookup"><span data-stu-id="11e50-106">Machine agnostic execution and rehydration</span></span>  
  
- <span data-ttu-id="11e50-107">補償模型</span><span class="sxs-lookup"><span data-stu-id="11e50-107">Compensation model</span></span>  
  
- <span data-ttu-id="11e50-108">在控制情況下的系統關閉</span><span class="sxs-lookup"><span data-stu-id="11e50-108">Controlled System Shutdown</span></span>  
  
- <span data-ttu-id="11e50-109">復原</span><span class="sxs-lookup"><span data-stu-id="11e50-109">Recovery</span></span>  
  
  <span data-ttu-id="11e50-110">協調流程引擎會在不同點持續儲存執行中協調流程執行個體的整個狀態，這樣就可以在稍後將執行個體完整地還原於記憶體中。</span><span class="sxs-lookup"><span data-stu-id="11e50-110">The orchestration engine saves to persistent storage the entire state of a running orchestration instance at various points, so that the instance can later be completely restored in memory.</span></span> <span data-ttu-id="11e50-111">此狀態包含：</span><span class="sxs-lookup"><span data-stu-id="11e50-111">The state includes:</span></span>  
  
- <span data-ttu-id="11e50-112">引擎的內部狀態，包括其目前的進度。</span><span class="sxs-lookup"><span data-stu-id="11e50-112">The internal state of the engine, including its current progress.</span></span>  
  
- <span data-ttu-id="11e50-113">任何維護狀態資訊且由協調流程所使用之 .NET 元件的狀態。</span><span class="sxs-lookup"><span data-stu-id="11e50-113">The state of any .NET components that maintain state information and are being used by the orchestration.</span></span>  
  
- <span data-ttu-id="11e50-114">訊息和變數值。</span><span class="sxs-lookup"><span data-stu-id="11e50-114">Message and variable values.</span></span>  
  
## <a name="persistence-points"></a><span data-ttu-id="11e50-115">持續點</span><span class="sxs-lookup"><span data-stu-id="11e50-115">Persistence Points</span></span>  
 <span data-ttu-id="11e50-116">協調流程引擎會在不同點儲存執行中協調流程執行個體的狀態。</span><span class="sxs-lookup"><span data-stu-id="11e50-116">The orchestration engine saves the state of a running orchestration instance at various points.</span></span> <span data-ttu-id="11e50-117">若它需要解除凍結協調流程執行個體，請從控制的關閉啟動，或從未預期的關閉復原，它會從最後的持續點執行協調流程執行個體，就像從未發生過任何事一樣。</span><span class="sxs-lookup"><span data-stu-id="11e50-117">If it needs to rehydrate the orchestration instance, start up from a controlled shutdown, or recover from an unexpected shutdown, it will run the orchestration instance from the last persistence point, as though nothing else had occurred.</span></span> <span data-ttu-id="11e50-118">例如，若收到了某個訊息，但在儲存狀態之前發生了未預期的關閉，則引擎將不會記錄它已收到訊息，並會在重新啟動時再次接收該訊息。</span><span class="sxs-lookup"><span data-stu-id="11e50-118">For example, if a message is received but there is an unexpected shutdown before state can be saved, the engine will not record that it has received the message, and will receive it again upon restarting.</span></span> <span data-ttu-id="11e50-119">引擎將會在下列狀況中儲存協調流程的狀態：</span><span class="sxs-lookup"><span data-stu-id="11e50-119">The engine will save the state of an orchestration in the following circumstances:</span></span>  
  
-   <span data-ttu-id="11e50-120">已達交易式範圍的結尾。</span><span class="sxs-lookup"><span data-stu-id="11e50-120">The end of a transactional scope is reached.</span></span>  
  
    -   <span data-ttu-id="11e50-121">引擎會在交易式範圍結束時儲存狀態，這樣就可以明確地定義協調流程應該繼續的點，而且若有需要，還可以正確地執行補償。</span><span class="sxs-lookup"><span data-stu-id="11e50-121">The engine saves state at the end of a transactional scope so that the point at which the orchestration should resume is defined unambiguously, and so that compensation can be carried out correctly if necessary.</span></span>  
  
    -   <span data-ttu-id="11e50-122">若持續性機制是成功的，協調流程將會從範圍結束時繼續執行，否則，會叫用適當的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="11e50-122">The orchestration will continue to run from the end of the scope if persistence was successful; otherwise, the appropriate exception handler will be invoked.</span></span>  
  
    -   <span data-ttu-id="11e50-123">如果範圍是交易式且不可部分完成的，引擎便會在認可時，將狀態儲存在該不可部分完成範圍的結尾。</span><span class="sxs-lookup"><span data-stu-id="11e50-123">If the scope is transactional and atomic, the engine will save state at the end of the atomic scope when it commits.</span></span>  
  
    -   <span data-ttu-id="11e50-124">如果範圍是交易式且長期執行的，則引擎會在範圍完成時，產生新交易並保存完整的執行階段狀態。</span><span class="sxs-lookup"><span data-stu-id="11e50-124">If the scope is transactional and long-running, the engine will generate a new transaction and persist the complete state of the runtime when the scope completes.</span></span>  
  
-   <span data-ttu-id="11e50-125">已達到偵錯中斷點。</span><span class="sxs-lookup"><span data-stu-id="11e50-125">A debugging breakpoint is reached.</span></span>  
  
-   <span data-ttu-id="11e50-126">已傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="11e50-126">A message is sent.</span></span> <span data-ttu-id="11e50-127">唯一的例外是，當訊息是從不可部分完成的交易範圍內所傳送時。</span><span class="sxs-lookup"><span data-stu-id="11e50-127">The only exception to this is when a message is sent from within an atomic transaction scope.</span></span>  
  
-   <span data-ttu-id="11e50-128">協調流程會啟動另一個協調流程以非同步的方式，如同**啟動協調流程**圖形。</span><span class="sxs-lookup"><span data-stu-id="11e50-128">The orchestration starts another orchestration asynchronously, as with the **Start Orchestration** shape.</span></span>  
  
-   <span data-ttu-id="11e50-129">已擱置協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="11e50-129">The orchestration instance is suspended.</span></span>  
  
-   <span data-ttu-id="11e50-130">當協調流程引擎被要求關閉時，它會嘗試儲存控制資訊，以及所有執行中協調流程執行個體的目前狀態，如此，當它再次啟動時，便可以繼續執行它們。</span><span class="sxs-lookup"><span data-stu-id="11e50-130">When the orchestration engine is asked to shut down, it will try to save control information as well as the current state of all running orchestration instances, so that it can resume running them when it is started again.</span></span> <span data-ttu-id="11e50-131">如果引擎無法成功儲存目前狀態，它會從關閉前所發生的最後一個持續點繼續執行協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="11e50-131">If the engine is unsuccessful in saving the current state, the engine will resume the orchestration instance from the last persistence point that occurred before the shutdown.</span></span> <span data-ttu-id="11e50-132">這種方式適用於控制情況下的系統關閉以及不正常終止。</span><span class="sxs-lookup"><span data-stu-id="11e50-132">This applies to the system shutdown in controlled condition as well as abnormal termination.</span></span>  
  
-   <span data-ttu-id="11e50-133">引擎會決定應該凍結的執行個體。</span><span class="sxs-lookup"><span data-stu-id="11e50-133">The engine determines that the instance should be dehydrated.</span></span>  
  
-   <span data-ttu-id="11e50-134">已完成協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="11e50-134">The orchestration instance is finished.</span></span>  
  
## <a name="serialization"></a><span data-ttu-id="11e50-135">序列化</span><span class="sxs-lookup"><span data-stu-id="11e50-135">Serialization</span></span>  
 <span data-ttu-id="11e50-136">協調流程直接或間接 (像是透過其他物件) 參考的所有物件執行個體都必須是可序列化的，這樣協調流程狀態才得以保存。</span><span class="sxs-lookup"><span data-stu-id="11e50-136">All object instances that your orchestration refers to directly or indirectly (as through other objects) must be serializable for your orchestration state to be persisted.</span></span> <span data-ttu-id="11e50-137">以下有兩個例外:</span><span class="sxs-lookup"><span data-stu-id="11e50-137">There are two exceptions:</span></span>  
  
-   <span data-ttu-id="11e50-138">您可以在不可部分完成的交易中宣告不可序列化的物件。</span><span class="sxs-lookup"><span data-stu-id="11e50-138">You can have a nonserializable object declared inside an atomic transaction.</span></span> <span data-ttu-id="11e50-139">您可以這麼做是因為不可部分完成的範圍並不包含持續點。</span><span class="sxs-lookup"><span data-stu-id="11e50-139">You can do this because atomic scopes do not contain persistence points.</span></span>  
  
-   <span data-ttu-id="11e50-140">System.Xml.XmlDocument 不是一個可序列化的類別；它是以特殊案例來處理，且可用於任何地方。</span><span class="sxs-lookup"><span data-stu-id="11e50-140">System.Xml.XmlDocument is not a serializable class; it is handled as a special case and can be used anywhere.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="11e50-141">為了讓 .NET 物件得以保存，它必須標示為可序列化。</span><span class="sxs-lookup"><span data-stu-id="11e50-141">In order for a .NET object to be persisted, it must be marked as serializable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11e50-142">COM 物件不能使用標準 .NET 序列化程序來保存。</span><span class="sxs-lookup"><span data-stu-id="11e50-142">COM objects cannot be persisted using standard .NET serialization procedures.</span></span> <span data-ttu-id="11e50-143">若您想要呼叫不可部分完成交易以外的 COM 物件，則必須將 COM 物件包裝在 .NET 物件中，這個 .NET 物件必須是 .NET 可序列化的，並且知道要如何保存和還原 COM 物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="11e50-143">If you want to call a COM object outside of an atomic transaction, you must wrap the COM object in a .NET object that is .NET serializable and knows how to persist and restore the state of the COM object.</span></span>  
  
## <a name="system-shutdown"></a><span data-ttu-id="11e50-144">系統關閉</span><span class="sxs-lookup"><span data-stu-id="11e50-144">System Shutdown</span></span>  
 <span data-ttu-id="11e50-145">當協調流程引擎被要求關閉時，它會嘗試儲存控制資訊，以及所有執行中協調流程執行個體的目前狀態，如此，當它再次啟動時，便可以繼續執行它們。</span><span class="sxs-lookup"><span data-stu-id="11e50-145">When the orchestration engine is asked to shut down, it will try to save control information as well as the current state of all running orchestration instances, so that it can resume running them when it is started again.</span></span> <span data-ttu-id="11e50-146">如果引擎無法成功儲存目前狀態，它會從關閉前所發生的最後一個持續點繼續執行協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="11e50-146">If the engine is unsuccessful in saving the current state, the engine will resume the orchestration instance from the last persistence point that occurred before the shutdown.</span></span> <span data-ttu-id="11e50-147">這種方式適用於控制情況下的系統關閉以及不正常終止。</span><span class="sxs-lookup"><span data-stu-id="11e50-147">This applies to the system shutdown in controlled condition as well as abnormal termination.</span></span>  
  
## <a name="recovery"></a><span data-ttu-id="11e50-148">復原</span><span class="sxs-lookup"><span data-stu-id="11e50-148">Recovery</span></span>  
 <span data-ttu-id="11e50-149">引擎會將協調流程執行個體的狀態資訊定期儲存至永久儲存體，並會儲存系統關機時的狀態。</span><span class="sxs-lookup"><span data-stu-id="11e50-149">The engine regularly saves to persistent storage the state information of an orchestration instance, and it also saves state in the event of a system shutdown.</span></span>  
  
 <span data-ttu-id="11e50-150">當協調流程執行個體因故發生異常失敗時，可從最後持續的狀態復原該執行個體，並可像沒有中斷過一樣繼續執行。</span><span class="sxs-lookup"><span data-stu-id="11e50-150">When an orchestration instance fails abnormally for whatever reason, the instance can be recovered from the last persisted state, and it can continue to run as if there were no interruption.</span></span> <span data-ttu-id="11e50-151">即使原來執行該執行個體的伺服器因為某種原因而中斷服務，執行個體也能在另一台機器上繼續執行。</span><span class="sxs-lookup"><span data-stu-id="11e50-151">This is true even if the original server that the instance ran on goes out of service for some reason; the instance can simply resume running on a separate machine.</span></span> <span data-ttu-id="11e50-152">因為有了這種多重伺服器的修復模型，所以也就不再需要叢集。</span><span class="sxs-lookup"><span data-stu-id="11e50-152">Because of this multi-server recovery model, you no longer need clustering.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e50-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11e50-153">See Also</span></span>  
 [<span data-ttu-id="11e50-154">協調流程凍結和解除凍結</span><span class="sxs-lookup"><span data-stu-id="11e50-154">Orchestration Dehydration and Rehydration</span></span>](../core/orchestration-dehydration-and-rehydration.md)