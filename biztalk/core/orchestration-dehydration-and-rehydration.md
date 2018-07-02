---
title: 協調流程凍結和解除凍結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57d7c0bf-a707-4ebd-afab-e75dd80c3c34
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1906d2d09485c56075fedf0d709cc1bdbbb2dba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973519"
---
# <a name="orchestration-dehydration-and-rehydration"></a><span data-ttu-id="f0e4d-102">協調流程凍結和解除凍結</span><span class="sxs-lookup"><span data-stu-id="f0e4d-102">Orchestration Dehydration and Rehydration</span></span>
<span data-ttu-id="f0e4d-103">當許多長時間執行的商務程序同時執行時，記憶體和效能是可能發生的問題。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-103">When many long-running business processes are running at the same time, memory and performance are potential issues.</span></span> <span data-ttu-id="f0e4d-104">協調流程引擎透過「凍結」和「解除凍結」協調流程執行個體來解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-104">The orchestration engine addresses these issues by "dehydrating" and "rehydrating" orchestration instances.</span></span>  
  
 <span data-ttu-id="f0e4d-105">凍結是將協調流程狀態序列化到 SQL Server 資料庫中的程序。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-105">Dehydration is the process of serializing the state of an orchestration into a SQL Server database.</span></span> <span data-ttu-id="f0e4d-106">解除凍結是此程序的反向： 還原序列化之資料庫的協調流程最後一個執行中狀態。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-106">Rehydration is the reverse of this process: deserializing the last running state of an orchestration from the database.</span></span> <span data-ttu-id="f0e4d-107">凍結是藉由減少必須一次在記憶體中產生的協調流程數目，來將系統資源的使用降至最低。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-107">Dehydration is used to minimize the use of system resources by reducing the number of orchestrations that have to be instantiated in memory at one time.</span></span>  
  
## <a name="dehydration"></a><span data-ttu-id="f0e4d-108">Dehydration</span><span class="sxs-lookup"><span data-stu-id="f0e4d-108">Dehydration</span></span>  
 <span data-ttu-id="f0e4d-109">協調流程引擎可能會判斷協調流程執行個體是否已經閒置相當長的一段時間。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-109">The orchestration engine might determine that an orchestration instance has been idle for a relatively long period of time.</span></span> <span data-ttu-id="f0e4d-110">它會計算閾值以決定各種動作發生之前應等待多久時間，若已超過這些閾值，則會凍結該執行個體。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-110">It calculates thresholds to determine how long it will wait for various actions to take place, and if those thresholds are exceeded, it dehydrates the instance.</span></span> <span data-ttu-id="f0e4d-111">這可能發生在下列情況下：</span><span class="sxs-lookup"><span data-stu-id="f0e4d-111">This can occur under the following circumstances:</span></span>  
  
- <span data-ttu-id="f0e4d-112">當協調流程等待接收訊息，且等待時間超過引擎決定的閾值。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-112">When the orchestration is waiting to receive a message, and the wait is longer than a threshold determined by the engine.</span></span>  
  
- <span data-ttu-id="f0e4d-113">當協調流程 「 接聽 」 訊息，當您使用如同**接聽**圖形與任何分支之前不會觸發引擎決定的閾值。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-113">When the orchestration is "listening" for a message, as it does when you use a **Listen** shape, and no branch is triggered before a threshold determined by the engine.</span></span> <span data-ttu-id="f0e4d-114">唯一的例外是當**接聽**圖形包含啟動接收。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-114">The only exception to this is when the **Listen** shape contains an activation receive.</span></span>  
  
- <span data-ttu-id="f0e4d-115">當協調流程中的延遲超過引擎決定的閾值。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-115">When a delay in the orchestration is longer than a threshold determined by the engine.</span></span>  
  
  <span data-ttu-id="f0e4d-116">引擎會儲存狀態以凍結執行個體，並釋出執行個體所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-116">The engine dehydrates the instance by saving the state, and frees up the memory required by the instance.</span></span> <span data-ttu-id="f0e4d-117">透過凍結休眠的協調流程執行個體，引擎就可以讓大量的長時間執行之商務程序在相同電腦上同時執行。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-117">By dehydrating dormant orchestration instances, the engine makes it possible for a large number of long-running business processes to run concurrently on the same computer.</span></span>  
  
  <span data-ttu-id="f0e4d-118">您可以設定 12 個屬性，設定凍結在 BizTalk Server 中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-118">You can set 12 properties to configure how dehydration works in BizTalk Server.</span></span> <span data-ttu-id="f0e4d-119">本節中的主題會列出並說明屬性及其預設值，也會討論不同的值如何影響凍結的行為。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-119">The topics in this section list and describe these properties and their default values, and discuss how various values affect dehydration behavior.</span></span>  
  
## <a name="rehydration"></a><span data-ttu-id="f0e4d-120">解除凍結</span><span class="sxs-lookup"><span data-stu-id="f0e4d-120">Rehydration</span></span>  
 <span data-ttu-id="f0e4d-121">可透過訊息回條或在「延遲」圖形中指定的逾時過期來觸發協調流程引擎，以解除凍結協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-121">The orchestration engine can be triggered to rehydrate an orchestration instance by the receipt of a message or by the expiration of a time-out specified in a Delay shape.</span></span> <span data-ttu-id="f0e4d-122">然後，該引擎就會將已儲存的協調流程執行個體載入記憶體、還原其狀態，並從原本的停止點執行。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-122">It then loads the saved orchestration instance into memory, restores its state, and runs it from the point where it left off.</span></span> <span data-ttu-id="f0e4d-123">如需協調流程中使用圖形的詳細資訊，請參閱[協調流程圖形](../core/orchestration-shapes.md)。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-123">For more information about using shapes in orchestrations, see [Orchestration Shapes](../core/orchestration-shapes.md).</span></span>  
  
 <span data-ttu-id="f0e4d-124">協調流程可設定為在一個以上的伺服器中執行。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-124">An orchestration can be configured to run on more than one server.</span></span> <span data-ttu-id="f0e4d-125">在某個協調流程執行個體已經凍結之後，可以在這些伺服器中的任何一個將它解除凍結。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-125">After an orchestration instance has been dehydrated, it can be rehydrated on any of these servers.</span></span> <span data-ttu-id="f0e4d-126">如果某個伺服器關閉，則引擎會在其他伺服器中，從它先前的狀態繼續執行協調流程。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-126">If one server goes down, the engine continues to run the orchestration on a different server, continuing from its previous state.</span></span> <span data-ttu-id="f0e4d-127">引擎也會利用此功能，實作伺服器之間的負載平衡。</span><span class="sxs-lookup"><span data-stu-id="f0e4d-127">The engine also takes advantage of this feature to implement load balancing across servers.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f0e4d-128">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="f0e4d-128">Next steps</span></span>
  
-   [<span data-ttu-id="f0e4d-129">凍結預設屬性</span><span class="sxs-lookup"><span data-stu-id="f0e4d-129">Dehydration Default Properties</span></span>](../core/dehydration-default-properties.md)  
  
-   [<span data-ttu-id="f0e4d-130">如何計算凍結</span><span class="sxs-lookup"><span data-stu-id="f0e4d-130">How to Calculate Dehydration</span></span>](../core/how-to-calculate-dehydration.md)  
  
-   [<span data-ttu-id="f0e4d-131">範例凍結計算</span><span class="sxs-lookup"><span data-stu-id="f0e4d-131">Sample Dehydration Calculation</span></span>](../core/sample-dehydration-calculation.md)  
  
-   [<span data-ttu-id="f0e4d-132">協調流程凍結效能計數器</span><span class="sxs-lookup"><span data-stu-id="f0e4d-132">Orchestration Dehydration Performance Counters</span></span>](../core/orchestration-dehydration-performance-counters.md)  
  
-   [<span data-ttu-id="f0e4d-133">BTSNTSvc.exe.config 檔案</span><span class="sxs-lookup"><span data-stu-id="f0e4d-133">BTSNTSvc.exe.config File</span></span>](../core/btsntsvc-exe-config-file.md)  
  
-   [<span data-ttu-id="f0e4d-134">可能影響凍結行為的其他活動</span><span class="sxs-lookup"><span data-stu-id="f0e4d-134">Other Activities That Can Affect Dehydration Behavior</span></span>](../core/other-activities-that-can-affect-dehydration-behavior.md)