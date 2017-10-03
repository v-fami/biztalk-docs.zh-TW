---
title: "BizTalk Server 中的 zombie |Microsoft 文件"
description: "BizTalk Server 中的 zombie 訊息的常見原因"
ms.custom: 
ms.date: 03/23/2016
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c684891-e984-442f-b5fd-de5f7cf32b44
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9764522d2ff5265b6f28f2f125cb33b2982a7605
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="zombies-in-biztalk-server"></a><span data-ttu-id="a6900-103">BizTalk Server 中的 Zombie</span><span class="sxs-lookup"><span data-stu-id="a6900-103">Zombies in BizTalk Server</span></span>

## <a name="what-is-a-zombie"></a><span data-ttu-id="a6900-104">何謂 Zombie？</span><span class="sxs-lookup"><span data-stu-id="a6900-104">What is a zombie?</span></span>  
  
-   <span data-ttu-id="a6900-105">Zombie (廢止) 訊息是從 MessageBox 經路由送往執行中協調流程、但是當該協調流程結束時仍「在途中」的訊息。</span><span class="sxs-lookup"><span data-stu-id="a6900-105">A zombie message is a message that was routed to a running orchestration from the messagebox and was "in flight" when the orchestration ended.</span></span> <span data-ttu-id="a6900-106">「在途中」訊息是已經路由送往服務執行個體，然後即處於該服務執行個體之 MessageBox 佇列中的訊息。</span><span class="sxs-lookup"><span data-stu-id="a6900-106">An "in flight" message is a message that has been routed to a service instance and so is in a messagebox queue destined for the service instance.</span></span> <span data-ttu-id="a6900-107">因為訂閱的協調流程執行個體可能不再取用該訊息，所以會擱置此訊息，並以「擱置 (不可繼續)」的 ServiceInstance/State 值標示它。</span><span class="sxs-lookup"><span data-stu-id="a6900-107">Since the message can no longer be consumed by the subscribing orchestration instance, the message is suspended and marked with a ServiceInstance/State value of "Suspended (Non-resumable)".</span></span>  
  
-   <span data-ttu-id="a6900-108">Zombie 服務執行個體是當訊息從 MessageBox 經路由前往協調流程執行個體且仍「在途中」時，即已完成的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="a6900-108">A zombie service instance is an instance of an orchestration which has completed while a message that was routed to the orchestration instance from the messagebox was still "in flight".</span></span> <span data-ttu-id="a6900-109">由於協調流程執行個體已經結束，它便無法取用這個「在途中」訊息，因此訊息會遭到擱置，並且標示「擱置 (不可繼續)」的 ServiceInstance/State 值。</span><span class="sxs-lookup"><span data-stu-id="a6900-109">Since the orchestration instance has ended, it cannot consume the "in flight" messages and so is suspended and marked with a ServiceInstance/State value of "Suspended (Non-resumable)".</span></span>  
  
## <a name="typical-causes"></a><span data-ttu-id="a6900-110">常見的原因</span><span class="sxs-lookup"><span data-stu-id="a6900-110">Typical causes</span></span>
<span data-ttu-id="a6900-111">發生 Zombie 的狀況通常分成以下類別：</span><span class="sxs-lookup"><span data-stu-id="a6900-111">The occurrence of zombies typically falls into one of the following categories:</span></span>  
  
1.  <span data-ttu-id="a6900-112">**終止控制訊息**– 協調流程引擎可讓您控制訊息來取消所有目前正在執行的工作特定的協調流程執行個體中使用。</span><span class="sxs-lookup"><span data-stu-id="a6900-112">**Terminate control messages** – The orchestration engine allows the use of control messages to cancel all currently running work in a specific orchestration instance.</span></span> <span data-ttu-id="a6900-113">由於控制訊息會立即停止執行中的協調流程，所以產生 Zombie 執行個體一點也不意外。</span><span class="sxs-lookup"><span data-stu-id="a6900-113">Since the control message immediately halts the running orchestration, zombie instances are not unexpected.</span></span> <span data-ttu-id="a6900-114">有許多與「人力工作流程」相關的設計經常使用這種機制，而其他某些設計也會採用。</span><span class="sxs-lookup"><span data-stu-id="a6900-114">A number of Human Workflow related designs tend to use this mechanism as well as some other designs.</span></span>  
  
2.  <span data-ttu-id="a6900-115">**平行待命接收**– 在此案例中服務執行個體會等待 n 個訊息的第 1 和當它收到特定訊息會執行一些工作，並終止。</span><span class="sxs-lookup"><span data-stu-id="a6900-115">**Parallel listen receives** – In this scenario the service instance waits for 1 of n messages and when it receives certain messages it does some work and terminates.</span></span> <span data-ttu-id="a6900-116">如果正好於服務執行個體終止時，在平行分支上收到訊息，便會產生 Zombie。</span><span class="sxs-lookup"><span data-stu-id="a6900-116">If messages are received on a parallel branch just as the service instance is terminating, zombies are created.</span></span>  
  
3.  <span data-ttu-id="a6900-117">**循序群組與不具決定性端點**– 在此案例中，主要協調流程排程設計用來處理特定類型的所有訊息，以便滿足特定類型的系統設計需求。</span><span class="sxs-lookup"><span data-stu-id="a6900-117">**Sequential convoys with non-deterministic endpoints** – In this scenario, a master orchestration schedule is designed to handle all messages of a certain type in order to meet some type of system design requirement.</span></span> <span data-ttu-id="a6900-118">這些設計需求可能包括有序傳遞、資源分配程式和批次處理。</span><span class="sxs-lookup"><span data-stu-id="a6900-118">These design requirements may include ordered delivery, resource dispenser, and batching.</span></span> <span data-ttu-id="a6900-119">就此實例而言，比較傾向於定義環繞「待命」的 While 迴圈，而此待命帶有一個含「接收」的分支以及另一個帶有延遲圖形 (其後連接某個用來設定某變數以指示 While 迴圈停止的建構) 的分支。</span><span class="sxs-lookup"><span data-stu-id="a6900-119">For this scenario, the tendency is to define a while loop surrounding a listen with one branch having a receive and the other having a delay shape followed by some construct which sets some variable to indicate that the while loop should stop.</span></span> <span data-ttu-id="a6900-120">因為這可能觸發延遲，所以是非決定性的，但卻仍然會傳遞該訊息。</span><span class="sxs-lookup"><span data-stu-id="a6900-120">This is non-deterministic since the delay could be triggered, but a message could still be delivered.</span></span> <span data-ttu-id="a6900-121">像這樣的非決定性端點就很容產生 Zombie。</span><span class="sxs-lookup"><span data-stu-id="a6900-121">Non-deterministic endpoints like this are prone to generating zombies.</span></span>  
  
 <span data-ttu-id="a6900-122">Zombie 服務執行個體暫停時，會產生下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="a6900-122">When a zombie service instance is suspended,  the following error message is generated:</span></span>  
  
`0xC0C01B4C The instance completed without consuming all of its messages. The instance and its unconsumed messages have been suspended.`  
  
 <span data-ttu-id="a6900-123">您可以使用[BizTalk 結束字元](https://www.microsoft.com/download/details.aspx?id=2846)若要協助移除 zombie。</span><span class="sxs-lookup"><span data-stu-id="a6900-123">You can use the [BizTalk Terminator](https://www.microsoft.com/download/details.aspx?id=2846) to help remove zombies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6900-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6900-124">See Also</span></span>  
 <span data-ttu-id="a6900-125">**移除已擱置的服務執行個體**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="a6900-125">**Removing Suspended Service Instances** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>