---
title: 使用多個接續 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01a38087-71ee-40b3-a957-6a2653bd6435
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e27a73fae39a55f05650c08397616f3cbe4fa80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288934"
---
# <a name="using-multiple-continuations"></a><span data-ttu-id="9bb27-102">使用多個接續</span><span class="sxs-lookup"><span data-stu-id="9bb27-102">Using Multiple Continuations</span></span>
<span data-ttu-id="9bb27-103">在有多個活動的環境中使用「追蹤設定檔編輯器」(TPE) 時，您必須瞭解追蹤活動所在的實例，才能以正確順序對應接收埠、協調流程和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9bb27-103">Using the Tracking Profile Editor (TPE) in environments in which there are multiple activities requires that you understand the scenario in which the activities are being tracked in order to map the receive ports, orchestrations, and send ports in the proper sequence.</span></span>  
  
 <span data-ttu-id="9bb27-104">在追蹤設定檔中，TPE 會自動評估活動的開始和結束。</span><span class="sxs-lookup"><span data-stu-id="9bb27-104">In a tracking profile, the TPE assesses the beginning and end of the activity automatically.</span></span> <span data-ttu-id="9bb27-105">當收集到第一個資料片段時，此活動會開始，而當收集到最後一個片段時，此活動會結束。</span><span class="sxs-lookup"><span data-stu-id="9bb27-105">The activity starts when the first piece of data is collected and ends when the last piece is collected.</span></span>  
  
 <span data-ttu-id="9bb27-106">在大部分情況下，對開發人員而言，建立單一接續 (例如，兩個協調流程之間的接續) 是很簡單的程序。</span><span class="sxs-lookup"><span data-stu-id="9bb27-106">In most cases creating a single continuation, such as a continuation between two orchestrations, is a straightforward process for developers.</span></span> <span data-ttu-id="9bb27-107">TPE 呈現的複雜度是多個接續的案例。</span><span class="sxs-lookup"><span data-stu-id="9bb27-107">Where TPE exhibits complexity is in the case of multiple continuations.</span></span> <span data-ttu-id="9bb27-108">有多個接續的實例即代表「商務活動監控」(BAM) 活動會跨越多個接收埠、協調流程和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9bb27-108">A multiple continuation scenario  is where a Business Activity Monitoring (BAM) activity spans multiple receive ports, orchestrations, and send ports.</span></span> <span data-ttu-id="9bb27-109">若要收集一筆記錄中的 BAM 資料，您必須在所有 BizTalk Server 排程之間建立接續。</span><span class="sxs-lookup"><span data-stu-id="9bb27-109">In order to collect the BAM data in one record, you must create continuations between all the BizTalk Server schedules.</span></span> <span data-ttu-id="9bb27-110">如果是透過 TPE 使用者介面 (UI) 來完成，這個處理程序可能會很複雜。</span><span class="sxs-lookup"><span data-stu-id="9bb27-110">This process can be complex when completed through the TPE user interface (UI).</span></span>  
  
 <span data-ttu-id="9bb27-111">本主題描述如何在不同的實例中建立單一和多個接續。</span><span class="sxs-lookup"><span data-stu-id="9bb27-111">This topic describes how to create single and multiple continuations in different scenarios.</span></span>  
  
#### <a name="base-scenario-description---multiple-receive-ports-orchestrations-and-send-ports"></a><span data-ttu-id="9bb27-112">基本實例描述 - 多個接收埠、協調流程和傳送埠</span><span class="sxs-lookup"><span data-stu-id="9bb27-112">Base Scenario Description - Multiple Receive Ports, Orchestrations, and Send Ports</span></span>  
 <span data-ttu-id="9bb27-113">這個實例是由含有多個接收埠 (R)、協調流程 (O) 和傳送埠 (S) 的 BizTalk Server 所組成。</span><span class="sxs-lookup"><span data-stu-id="9bb27-113">The scenario consists of a BizTalk server that has a number of receive ports (R), orchestrations (O), and send ports (S).</span></span> <span data-ttu-id="9bb27-114">其中包含用來連結接續的一般 interchangeID 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9bb27-114">There is a generic interchangeID context property that is used to link the continuations.</span></span> <span data-ttu-id="9bb27-115">您可以使用任何內容屬性，例如 activityID 或其他唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="9bb27-115">You can use any context property, such as the activityID or other unique identifier.</span></span> <span data-ttu-id="9bb27-116">特定內容的選擇與實例的探討並無密切關聯。</span><span class="sxs-lookup"><span data-stu-id="9bb27-116">The choice of the specific content is not germane to the discussion of the scenario.</span></span>  
  
 <span data-ttu-id="9bb27-117">基於此實例的目的，暫不詳述從這些連接埠及協調流程中追蹤資料項目/里程碑/內容屬性值的相關議題，</span><span class="sxs-lookup"><span data-stu-id="9bb27-117">For the purposes of the scenario, discussions of the data item/milestone/context-property-value being tracked from these ports and orchestrations are not specified.</span></span> <span data-ttu-id="9bb27-118">而有關對應的部分則特別限定在商務邏輯的範圍。</span><span class="sxs-lookup"><span data-stu-id="9bb27-118">That part of the mapping is specific to the business logic.</span></span> <span data-ttu-id="9bb27-119">我們的目標是使用完成的活動資料表中的單一資料列，從所有連接埠和協調流程中擷取所有 BAM 資料。</span><span class="sxs-lookup"><span data-stu-id="9bb27-119">The goal is to capture all BAM data from all the ports and orchestrations in a single row in the completed activity table.</span></span> <span data-ttu-id="9bb27-120">可供協調流程用於接收和處理訊息的各種方式，帶來了一些有趣的問題和解決方案。</span><span class="sxs-lookup"><span data-stu-id="9bb27-120">The different ways in which a message can be received and processed by orchestrations presents some interesting challenges and solutions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bb27-121">含有一個連接埠或一個協調流程的實例可以視為含有許多連接埠和許多協調流程之實例的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="9bb27-121">The scenario of one port or one orchestration can be considered a special case of the many port and many orchestrations scenario.</span></span>  
  
#### <a name="scenario-solution-1---one-receive-port-and-one-orchestration"></a><span data-ttu-id="9bb27-122">實例解決方案 1 - 一個接收埠和一個協調流程</span><span class="sxs-lookup"><span data-stu-id="9bb27-122">Scenario Solution 1 - One Receive Port and One Orchestration</span></span>  
 <span data-ttu-id="9bb27-123">在這個實例中，訊息只會抵達其中一個接收埠 (R1)，而且只由其中一個協調流程 (O1) 來處理。</span><span class="sxs-lookup"><span data-stu-id="9bb27-123">In this scenario, a message arrives at exactly one of the receive ports (R1) and is processed by exactly one of the orchestrations (O1).</span></span>  
  
 <span data-ttu-id="9bb27-124">建立接續的程序如下：</span><span class="sxs-lookup"><span data-stu-id="9bb27-124">The process to create the continuation is as follows:</span></span>  
  
1.  <span data-ttu-id="9bb27-125">在追蹤設定檔的資料夾活動樹狀檢視中建立接續。</span><span class="sxs-lookup"><span data-stu-id="9bb27-125">Create a continuation in the folder activity tree view of the tracking profile.</span></span>  
  
2.  <span data-ttu-id="9bb27-126">按一下以選擇內容屬性結構描述**選取事件來源** 按鈕，然後按一下**選取內容屬性**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="9bb27-126">Choose the context property schema by clicking the **Select Event Source** button, and then clicking the **Select Context Property** menu item.</span></span>  
  
3.  <span data-ttu-id="9bb27-127">找出**interchangeId 屬性**中**內容屬性名稱**清單，然後加以選取。</span><span class="sxs-lookup"><span data-stu-id="9bb27-127">Locate the **interchangeId property** in the **Context Property Name** list, and then select it.</span></span>  
  
4.  <span data-ttu-id="9bb27-128">從屬性結構描述中，將 interchangeID 對應至您剛才建立的接續資料夾。</span><span class="sxs-lookup"><span data-stu-id="9bb27-128">From the property schema, map the interchangeID to the continuation folder that you just created.</span></span>  
  
5.  <span data-ttu-id="9bb27-129">在活動樹狀結構中新建立的 interchangeID 節點上按一下滑鼠右鍵，然後選取要做為對應起點的連接埠。</span><span class="sxs-lookup"><span data-stu-id="9bb27-129">Right-click the newly created interchangeID node in the activity tree, and then select the ports from which to map.</span></span>  
  
6.  <span data-ttu-id="9bb27-130">在**選取連接埠**對話方塊顯示時，會選取所有**N**接收埠。</span><span class="sxs-lookup"><span data-stu-id="9bb27-130">In the **Select Ports** dialog box that is displayed, select all **N** receive ports.</span></span>  
  
7.  <span data-ttu-id="9bb27-131">在資料夾活動樹狀結構中建立 [continuationID] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9bb27-131">Create a continuationID folder in the folder activity tree.</span></span>  
  
8.  <span data-ttu-id="9bb27-132">按一下以開啟每個協調流程**選取事件來源** 按鈕，然後按一下**選取協調流程排程**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="9bb27-132">Open each orchestration by clicking the **Select Event Source** button, and then clicking the **Select Orchestration Schedule** menu item.</span></span> <span data-ttu-id="9bb27-133">在每個協調流程中的圖形上按一下滑鼠右鍵，然後將 interchangeID 內容屬性對應至新建立的 continuationID。</span><span class="sxs-lookup"><span data-stu-id="9bb27-133">From each orchestration, right-click a shape in the orchestration, and then map the interchangeID context property to the newly created continuationID.</span></span>  
  
 <span data-ttu-id="9bb27-134">在包含三個協調流程的部署中，追蹤設定檔看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="9bb27-134">In a deployment with three orchestrations, your tracking profile would look similar to this:</span></span>  
  
 <span data-ttu-id="9bb27-135">![TPE 多重接續案例 1](../core/media/4761d680-7218-4404-a636-06739f70f344.gif "4761d680-7218-4404-a636-06739f70f344")</span><span class="sxs-lookup"><span data-stu-id="9bb27-135">![TPE multiple continuation scenario 1](../core/media/4761d680-7218-4404-a636-06739f70f344.gif "4761d680-7218-4404-a636-06739f70f344")</span></span>  
  
#### <a name="scenario-solution-2---one-receive-port-and-multiple-orchestrations"></a><span data-ttu-id="9bb27-136">實例解決方案 2 - 一個接收埠和多個協調流程</span><span class="sxs-lookup"><span data-stu-id="9bb27-136">Scenario Solution 2 - One Receive Port and Multiple Orchestrations</span></span>  
 <span data-ttu-id="9bb27-137">在這個實例中，訊息只會抵達其中一個接收埠 (R1)，而且會由每一個協調流程處理。</span><span class="sxs-lookup"><span data-stu-id="9bb27-137">In this scenario, a message arrives at exactly one of the receive ports and is processed by each and every orchestration.</span></span> <span data-ttu-id="9bb27-138">這會在同時傳送訊息給每一個協調流程時發生。</span><span class="sxs-lookup"><span data-stu-id="9bb27-138">This happens as the message is simultaneously sent to each of the orchestrations.</span></span>  
  
 <span data-ttu-id="9bb27-139">在這種情況下，每個協調流程都必須有接續和 continuationID。</span><span class="sxs-lookup"><span data-stu-id="9bb27-139">In this case, we would need a continuation and continuationID for each orchestration.</span></span> <span data-ttu-id="9bb27-140">建立接續的程序會類似於實例解決方案 1 所述的步驟。</span><span class="sxs-lookup"><span data-stu-id="9bb27-140">The process for creating the continuations would be similar to the steps outlined in scenario solution 1.</span></span> <span data-ttu-id="9bb27-141">針對三個協調流程部署，產生的追蹤設定檔看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="9bb27-141">For a three-orchestration deployment, your resulting tracking profile looks something like this:</span></span>  
  
 <span data-ttu-id="9bb27-142">![TPE Multiple 接續案例 2](../core/media/3cebd82f-9192-4d52-84c7-584f24e8ecca.gif "3cebd82f-9192-4d52-84c7-584f24e8ecca")</span><span class="sxs-lookup"><span data-stu-id="9bb27-142">![TPE Multiple continuation scenario 2](../core/media/3cebd82f-9192-4d52-84c7-584f24e8ecca.gif "3cebd82f-9192-4d52-84c7-584f24e8ecca")</span></span>  
  
#### <a name="scenario-solution-3---content-based-routing"></a><span data-ttu-id="9bb27-143">實例解決方案 3 - 以內容為基礎的路由</span><span class="sxs-lookup"><span data-stu-id="9bb27-143">Scenario Solution 3 - Content Based Routing</span></span>  
 <span data-ttu-id="9bb27-144">這個實例定義以內容為基礎的路由 (CBR) 解決方案。</span><span class="sxs-lookup"><span data-stu-id="9bb27-144">This scenario defines a content based routing (CBR) solution.</span></span> <span data-ttu-id="9bb27-145">訊息只會抵達其中一個接收埠，而且只傳送至其中一個傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9bb27-145">A message arrives at exactly one of the receive ports and is sent to exactly one of the send ports.</span></span> <span data-ttu-id="9bb27-146">這種路由會依據訊息中的內容屬性值產生。</span><span class="sxs-lookup"><span data-stu-id="9bb27-146">This routing happens based on a context property value in the message.</span></span> <span data-ttu-id="9bb27-147">在這種情況下，需要一個接續。</span><span class="sxs-lookup"><span data-stu-id="9bb27-147">In this case, we would need one continuation.</span></span> <span data-ttu-id="9bb27-148">對應看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="9bb27-148">The mapping looks something like this:</span></span>  
  
 <span data-ttu-id="9bb27-149">![接續 CBR 案例。] (../core/media/4459a73d-515f-4d6d-a68f-b18eee072df8.gif "4459a73d-515f-4d6d-a68f-b18eee072df8")</span><span class="sxs-lookup"><span data-stu-id="9bb27-149">![Continuation CBR scenario.](../core/media/4459a73d-515f-4d6d-a68f-b18eee072df8.gif "4459a73d-515f-4d6d-a68f-b18eee072df8")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bb27-150">上述對應也適用於只抵達其中一個接收埠、但會傳送給所有傳送埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="9bb27-150">The above mapping is also valid for a message that arrives at exactly one of the receive ports and is sent to all of the send ports.</span></span>  
  
#### <a name="scenario-solution-4---one-orchestration-multiple-send-ports"></a><span data-ttu-id="9bb27-151">實例解決方案 4 - 一個協調流程和多個傳送埠</span><span class="sxs-lookup"><span data-stu-id="9bb27-151">Scenario Solution 4 - One Orchestration, Multiple Send Ports</span></span>  
 <span data-ttu-id="9bb27-152">在此案例中，有多個傳送。</span><span class="sxs-lookup"><span data-stu-id="9bb27-152">In this scenario, there are multiple send.</span></span> <span data-ttu-id="9bb27-153">連接埠。</span><span class="sxs-lookup"><span data-stu-id="9bb27-153">ports.</span></span> <span data-ttu-id="9bb27-154">只由其中一個協調流程，這取決於處理規則的宣告，並且會傳送至所有傳送埠會處理訊息。</span><span class="sxs-lookup"><span data-stu-id="9bb27-154">A message is processed by exactly one of the orchestrations, which is determined by the processing rules, and is sent to all of the send ports.</span></span> <span data-ttu-id="9bb27-155">在這種情況下，需要一個接續。</span><span class="sxs-lookup"><span data-stu-id="9bb27-155">In this case, we would need one continuation.</span></span> <span data-ttu-id="9bb27-156">對應看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="9bb27-156">The mapping looks something like this:</span></span>  
  
 <span data-ttu-id="9bb27-157">![接續案例 4](../core/media/3ab10b51-d306-4ad1-acb6-6731e23394ac.gif "3ab10b51-d306-4ad1-acb6-6731e23394ac")</span><span class="sxs-lookup"><span data-stu-id="9bb27-157">![Coninuation Scenario 4](../core/media/3ab10b51-d306-4ad1-acb6-6731e23394ac.gif "3ab10b51-d306-4ad1-acb6-6731e23394ac")</span></span>  
  
#### <a name="scenario-solution-5---sequential-orchestrations"></a><span data-ttu-id="9bb27-158">實例解決方案 5 - 循序協調流程</span><span class="sxs-lookup"><span data-stu-id="9bb27-158">Scenario Solution 5 - Sequential Orchestrations</span></span>  
 <span data-ttu-id="9bb27-159">在這個實例中，訊息會依序由每個協調流程逐一處理，然後透過接續傳遞給下一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="9bb27-159">In this scenario, a message is processed by each orchestration in sequence, one by one, and is passed to the next orchestration via the continuation.</span></span> <span data-ttu-id="9bb27-160">對應看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="9bb27-160">The mapping looks something like this:</span></span>  
  
 <span data-ttu-id="9bb27-161">![接續案例 5](../core/media/563cacee-104c-4f8a-9836-da90aecb7487.gif "563cacee-104c-4f8a-9836-da90aecb7487")</span><span class="sxs-lookup"><span data-stu-id="9bb27-161">![Continuation scenario 5](../core/media/563cacee-104c-4f8a-9836-da90aecb7487.gif "563cacee-104c-4f8a-9836-da90aecb7487")</span></span>  
  
### <a name="collecting-data-in-an-asynchronous-environment"></a><span data-ttu-id="9bb27-162">收集非同步環境中的資料</span><span class="sxs-lookup"><span data-stu-id="9bb27-162">Collecting Data in an Asynchronous Environment</span></span>  
 <span data-ttu-id="9bb27-163">當您設定接續時，BAM 就會預期有資料抵達。</span><span class="sxs-lookup"><span data-stu-id="9bb27-163">When you set up continuations, BAM expects the data to arrive.</span></span> <span data-ttu-id="9bb27-164">在非同步環境中，您可能接收不到後端程序的回應。</span><span class="sxs-lookup"><span data-stu-id="9bb27-164">In an asynchronous environment you may not receive a response from a backend process.</span></span>  
  
 <span data-ttu-id="9bb27-165">如果收不到回應資料，活動執行個體便會一直等候。</span><span class="sxs-lookup"><span data-stu-id="9bb27-165">If you do not receive the response data, the activity instance waits indefinitely.</span></span> <span data-ttu-id="9bb27-166">活動將永遠無法完成，因此記錄就一直保留在 BAM 主要匯入資料庫的資料表中。</span><span class="sxs-lookup"><span data-stu-id="9bb27-166">The activity will never complete and the records remain in the tables in the BAM Primary Import database.</span></span> <span data-ttu-id="9bb27-167">試想有一個長時間執行的交易，在這種情況下，無法得知剩餘的資料何時會抵達。</span><span class="sxs-lookup"><span data-stu-id="9bb27-167">Consider the case of long-running transactions, where there is no way to tell when the remaining data will arrive.</span></span> <span data-ttu-id="9bb27-168">也沒有所謂的逾時，因為資料是否抵達取決於商務邏輯或程序，而資料抵達之後，就將活動標示為完成。</span><span class="sxs-lookup"><span data-stu-id="9bb27-168">There is no time-out, as data arrival will depend on business logic or processes, after which the activity is marked as complete.</span></span> <span data-ttu-id="9bb27-169">資料可能同一天抵達，或者誇張一點，來年才到。</span><span class="sxs-lookup"><span data-stu-id="9bb27-169">The data could arrive the same day, or in extreme cases, the following year.</span></span>  
  
 <span data-ttu-id="9bb27-170">解決方案是使用相關的活動。</span><span class="sxs-lookup"><span data-stu-id="9bb27-170">The solution is to use related activities.</span></span>  
  
 <span data-ttu-id="9bb27-171">請將您的活動分割成兩個活動。</span><span class="sxs-lookup"><span data-stu-id="9bb27-171">Split your activity into two activities.</span></span> <span data-ttu-id="9bb27-172">讓這兩個活動產生關聯，再將該回應關聯到原始的活動。</span><span class="sxs-lookup"><span data-stu-id="9bb27-172">Relate the two activities, and relate the response to the original activity.</span></span>  
  
 <span data-ttu-id="9bb27-173">如需相關活動的詳細資訊，請參閱[活動關係](../core/activity-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="9bb27-173">For more information about related activities, see [Activity Relationships](../core/activity-relationships.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb27-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bb27-174">See Also</span></span>  
 [<span data-ttu-id="9bb27-175">追蹤設定檔編輯器</span><span class="sxs-lookup"><span data-stu-id="9bb27-175">Tracking Profile Editor</span></span>](../core/tracking-profile-editor.md)