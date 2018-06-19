---
title: 協調流程偵錯工具使用者介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.hat.orchdebugger
helpviewer_keywords:
- Orchestration Debugger, debug mode
- Orchestration Debugger, Interactive mode
ms.assetid: ca18f1e2-63b7-4177-82ba-4accc3369a2a
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4663a642ffc960d969c994b5471d866a80fde828
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265654"
---
# <a name="orchestration-debugger-user-interface"></a><span data-ttu-id="9127f-102">協調流程偵錯工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="9127f-102">Orchestration Debugger User Interface</span></span>
<span data-ttu-id="9127f-103">在互動 (偵錯) 模式下，[協調流程偵錯工具] 檢視包含三個區域：[服務] 窗格、[追蹤的事件] 窗格以及 [協調流程] 窗格。</span><span class="sxs-lookup"><span data-stu-id="9127f-103">In interactive (debug) mode, the Orchestration Debugger view contains three areas: Service pane, Tracked Events pane, and the Orchestration pane.</span></span> <span data-ttu-id="9127f-104">此外，在互動模式下，「變數」清單和「變數」屬性會顯示在檢視的下方。</span><span class="sxs-lookup"><span data-stu-id="9127f-104">In addition, in interactive mode, the Variable list and Variable properties display across the bottom of the view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9127f-105">協調流程偵錯工具無法顯示服務的狀態，則為 true，除非它會出現在**在中斷點**模式，而且您已將它附加至執行個體。</span><span class="sxs-lookup"><span data-stu-id="9127f-105">The Orchestration Debugger cannot display the true state of the service unless it appears in **In Breakpoint** mode and you have attached it to the instance.</span></span>  
  
## <a name="service-pane-in-orchestration-debugger"></a><span data-ttu-id="9127f-106">協調流程偵錯工具中的服務窗格</span><span class="sxs-lookup"><span data-stu-id="9127f-106">Service Pane in Orchestration Debugger</span></span>  
 <span data-ttu-id="9127f-107">[協調流程偵錯工具] 視窗中最上面的窗格會顯示下列資訊。</span><span class="sxs-lookup"><span data-stu-id="9127f-107">The top pane of the Orchestration Debugger window displays the following information.</span></span>  
  
|<span data-ttu-id="9127f-108">標記</span><span class="sxs-lookup"><span data-stu-id="9127f-108">Tag</span></span>|<span data-ttu-id="9127f-109">Detail</span><span class="sxs-lookup"><span data-stu-id="9127f-109">Detail</span></span>|  
|---------|------------|  
|<span data-ttu-id="9127f-110">名稱</span><span class="sxs-lookup"><span data-stu-id="9127f-110">Name</span></span>|<span data-ttu-id="9127f-111">指出目前的檢視 (協調流程偵錯工具)，並允許您瀏覽至 [訊息流程] 檢視。</span><span class="sxs-lookup"><span data-stu-id="9127f-111">Indicates the current view (Orchestration Debugger), and allows you to navigate to the Message Flow view.</span></span>|  
|<span data-ttu-id="9127f-112">執行個體詳細資料</span><span class="sxs-lookup"><span data-stu-id="9127f-112">Instance Details</span></span>|<span data-ttu-id="9127f-113">顯示服務名稱，以及可唯一識別目前協調流程執行個體的 GUID。</span><span class="sxs-lookup"><span data-stu-id="9127f-113">Displays the service name and the GUID that uniquely identifies the current orchestration instance.</span></span>|  
|<span data-ttu-id="9127f-114">模式</span><span class="sxs-lookup"><span data-stu-id="9127f-114">Modes</span></span>|<span data-ttu-id="9127f-115">偵錯模式 (重新執行/即時)、協調流程狀態 (已啟動、已擱置、已完成等等)、已連接 (是或否)，以及中斷點模式 (在類別或在執行個體)。</span><span class="sxs-lookup"><span data-stu-id="9127f-115">Debug mode (Replay/Live), Orchestration state (Started, Suspended, Completed, etc.), Attached (Yes or No), and Breakpoint mode (On Class or On Instance).</span></span>|  
|<span data-ttu-id="9127f-116">服務選項</span><span class="sxs-lookup"><span data-stu-id="9127f-116">Service Options</span></span>|<span data-ttu-id="9127f-117">根據偵錯工具與執行個體的狀態，您可以執行之動作的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="9127f-117">Drop-down list of actions that you can perform based on the state of the debugger and the instance.</span></span>|  
  
 <span data-ttu-id="9127f-118">下面這項資訊，協調流程偵錯工具有兩個窗格： 左邊的 [追蹤的事件] 窗格和右邊的 [協調流程] 窗格。</span><span class="sxs-lookup"><span data-stu-id="9127f-118">Below this information, the Orchestration Debugger has two panes—the Tracked Events pane on the left, and the Orchestration pane on the right.</span></span>  
  
## <a name="tracked-events-pane-in-orchestration-debugger"></a><span data-ttu-id="9127f-119">協調流程偵錯工具中追蹤的事件窗格</span><span class="sxs-lookup"><span data-stu-id="9127f-119">Tracked Events Pane in Orchestration Debugger</span></span>  
 <span data-ttu-id="9127f-120">[追蹤的事件] 窗格會列出在協調流程中執行之每個動作的狀態，例如，它是否已啟動或已完成。</span><span class="sxs-lookup"><span data-stu-id="9127f-120">The Tracked Events pane lists the status of every action performed in the orchestration, such as whether it started or completed.</span></span> <span data-ttu-id="9127f-121">您在此窗格中選取每個資料列，對應的圖形 [協調流程] 窗格中會出現以綠色反白顯示圖形啟動和藍色完成圖形時。</span><span class="sxs-lookup"><span data-stu-id="9127f-121">As you select each of the rows in this pane, the corresponding shape in the Orchestration pane appears highlighted in green when the shape starts and blue when the shape finishes.</span></span>  
  
 <span data-ttu-id="9127f-122">[追蹤的事件] 窗格會顯示下列幾欄。</span><span class="sxs-lookup"><span data-stu-id="9127f-122">The Tracked Events pane shows the following columns.</span></span>  
  
|<span data-ttu-id="9127f-123">選項</span><span class="sxs-lookup"><span data-stu-id="9127f-123">Option</span></span>|<span data-ttu-id="9127f-124">動作</span><span class="sxs-lookup"><span data-stu-id="9127f-124">Action</span></span>|  
|------------|------------|  
|<span data-ttu-id="9127f-125">動作狀態 (左欄)</span><span class="sxs-lookup"><span data-stu-id="9127f-125">Action Status (left column)</span></span>|<span data-ttu-id="9127f-126">特定動作的狀態。</span><span class="sxs-lookup"><span data-stu-id="9127f-126">Status of the particular action.</span></span> <span data-ttu-id="9127f-127">箭頭表示已啟動該動作，而終止圖形則表示它已完成。</span><span class="sxs-lookup"><span data-stu-id="9127f-127">An arrow indicates the action has started and a termination shape indicates it has completed.</span></span>|  
|<span data-ttu-id="9127f-128">動作名稱</span><span class="sxs-lookup"><span data-stu-id="9127f-128">Action Name</span></span>|<span data-ttu-id="9127f-129">協調流程中的動作名稱。</span><span class="sxs-lookup"><span data-stu-id="9127f-129">Name of the action in the orchestration.</span></span>|  
|<span data-ttu-id="9127f-130">動作類型</span><span class="sxs-lookup"><span data-stu-id="9127f-130">Action Type</span></span>|<span data-ttu-id="9127f-131">代表動作的圖形類型。</span><span class="sxs-lookup"><span data-stu-id="9127f-131">Type of shape that represents the action.</span></span> <span data-ttu-id="9127f-132">箭頭表示已啟動該動作，而終止圖形則表示它已完成。</span><span class="sxs-lookup"><span data-stu-id="9127f-132">An arrow indicates that the action has started and a termination shape indicates it has completed.</span></span>|  
|<span data-ttu-id="9127f-133">Time</span><span class="sxs-lookup"><span data-stu-id="9127f-133">Time</span></span>|<span data-ttu-id="9127f-134">動作已執行的時間。</span><span class="sxs-lookup"><span data-stu-id="9127f-134">Time the action was performed.</span></span>|  
|<span data-ttu-id="9127f-135">日期</span><span class="sxs-lookup"><span data-stu-id="9127f-135">Date</span></span>|<span data-ttu-id="9127f-136">動作已執行的日期。</span><span class="sxs-lookup"><span data-stu-id="9127f-136">Date the action was performed.</span></span>|  
  
## <a name="orchestration-pane-in-orchestration-debugger"></a><span data-ttu-id="9127f-137">協調流程偵錯工具中的協調流程窗格</span><span class="sxs-lookup"><span data-stu-id="9127f-137">Orchestration Pane in Orchestration Debugger</span></span>  
 <span data-ttu-id="9127f-138">訊息事件和服務執行個體中追蹤輸出中 [群組中樞] 頁面的 [協調流程] 窗格是與所有圖形的協調流程執行個體的都呈現位置的區域。</span><span class="sxs-lookup"><span data-stu-id="9127f-138">The Orchestration pane in message event and service instance tracking output in the Group Hub page is the area where the orchestration instance renders with all of its shapes.</span></span> <span data-ttu-id="9127f-139">下表顯示 [協調流程] 窗格的快顯功能表動作。</span><span class="sxs-lookup"><span data-stu-id="9127f-139">The following table shows the Context menu actions for the Orchestration pane.</span></span>  
  
|<span data-ttu-id="9127f-140">選項</span><span class="sxs-lookup"><span data-stu-id="9127f-140">Option</span></span>|<span data-ttu-id="9127f-141">動作</span><span class="sxs-lookup"><span data-stu-id="9127f-141">Action</span></span>|  
|------------|------------|  
|<span data-ttu-id="9127f-142">在類別上設定中斷點</span><span class="sxs-lookup"><span data-stu-id="9127f-142">Set Breakpoint on Class</span></span>|<span data-ttu-id="9127f-143">以滑鼠右鍵按一下形狀**在類別上設定中斷點**選項。</span><span class="sxs-lookup"><span data-stu-id="9127f-143">Right-click a shape for the **Set Breakpoint on Class** option.</span></span> <span data-ttu-id="9127f-144">出現在圖形上的紅點表示已經設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="9127f-144">A red dot appears on the shape indicating the breakpoint has been set.</span></span>|  
|<span data-ttu-id="9127f-145">設定執行個體上的中斷點</span><span class="sxs-lookup"><span data-stu-id="9127f-145">Set Breakpoint on Instance</span></span>|<span data-ttu-id="9127f-146">以滑鼠右鍵按一下形狀**在執行個體上設定中斷點**選項。</span><span class="sxs-lookup"><span data-stu-id="9127f-146">Right-click a shape for the **Set Breakpoint on Instance** option.</span></span> <span data-ttu-id="9127f-147">出現在圖形上的紅點表示已經設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="9127f-147">A red dot appears on the shape indicating the breakpoint has been set.</span></span>|  
|<span data-ttu-id="9127f-148">移除類別上的中斷點</span><span class="sxs-lookup"><span data-stu-id="9127f-148">Remove Breakpoint on Class</span></span>|<span data-ttu-id="9127f-149">以滑鼠右鍵按一下形狀**移除中斷點**選項。</span><span class="sxs-lookup"><span data-stu-id="9127f-149">Right-click a shape for the **Remove Breakpoint** option.</span></span> <span data-ttu-id="9127f-150">紅點從圖形消失表示中斷點已移除。</span><span class="sxs-lookup"><span data-stu-id="9127f-150">The red dot disappears from the shape indicating the breakpoint has been removed.</span></span>|  
|<span data-ttu-id="9127f-151">移除執行個體上的中斷點</span><span class="sxs-lookup"><span data-stu-id="9127f-151">Remove Breakpoint on Instance</span></span>|<span data-ttu-id="9127f-152">以滑鼠右鍵按一下形狀**在執行個體上設定中斷點**選項。</span><span class="sxs-lookup"><span data-stu-id="9127f-152">Right-click a shape for the **Set Breakpoint on Instance** option.</span></span> <span data-ttu-id="9127f-153">紅點從圖形消失表示中斷點已移除。</span><span class="sxs-lookup"><span data-stu-id="9127f-153">The red dot disappears from the shape indicating the breakpoint has been removed.</span></span>|  
  
### <a name="variable-list-and-variable-properties-panes"></a><span data-ttu-id="9127f-154">變數清單與變數屬性窗格</span><span class="sxs-lookup"><span data-stu-id="9127f-154">Variable List and Variable Properties panes</span></span>  
 <span data-ttu-id="9127f-155">這些窗格只會出現的互動式偵錯時附加到協調流程執行階段使用**附加**服務選項。</span><span class="sxs-lookup"><span data-stu-id="9127f-155">These panes only appear for interactive debugging when attached to the Orchestration runtime using the **Attach** service option.</span></span> <span data-ttu-id="9127f-156">這些窗格會出現在畫面的底端。</span><span class="sxs-lookup"><span data-stu-id="9127f-156">These panes appear at the bottom of the screen.</span></span>  
  
 <span data-ttu-id="9127f-157">變數清單會顯示變數的名稱、值和類型。</span><span class="sxs-lookup"><span data-stu-id="9127f-157">The Variable List displays the Name, Value, and Type of the variable.</span></span> <span data-ttu-id="9127f-158">「值」指出變數是否為空值，若不是，就會顯示其包含的物件類型。</span><span class="sxs-lookup"><span data-stu-id="9127f-158">The Value indicates if the variable is Null or, if not, then what kind of object it contains.</span></span> <span data-ttu-id="9127f-159">型別是**Assembly.Namespace.Name**的物件。</span><span class="sxs-lookup"><span data-stu-id="9127f-159">Type is the **Assembly.Namespace.Name** of the object.</span></span>  
  
 <span data-ttu-id="9127f-160">[變數屬性] 窗格顯示的變數屬性隨物件類型而異。</span><span class="sxs-lookup"><span data-stu-id="9127f-160">The Variable Properties pane displays properties for the variable that vary according to the type of object.</span></span> <span data-ttu-id="9127f-161">例如，連接埠的屬性包括位址、名稱、範圍、類型和值。</span><span class="sxs-lookup"><span data-stu-id="9127f-161">For example, for ports this includes Address, Name, Scope, Type, and Value.</span></span> <span data-ttu-id="9127f-162">訊息會顯示捷徑，至於訊息中的每個部分，有其名稱、大小、屬性、類型和值。</span><span class="sxs-lookup"><span data-stu-id="9127f-162">Messages show the shortcut; for each part in the message, there is Name, Size, Properties, Type, and Value.</span></span> <span data-ttu-id="9127f-163">內容和屬性這類集合會顯示在快顯功能表中。</span><span class="sxs-lookup"><span data-stu-id="9127f-163">Collections such as Context and Properties display in a pop-up.</span></span> <span data-ttu-id="9127f-164">值的部分顯示會顯示為「工具提示」。</span><span class="sxs-lookup"><span data-stu-id="9127f-164">A partial display of the Value appears as a ToolTip.</span></span>  
  
 <span data-ttu-id="9127f-165">使用者透過排程依中斷點檢查這些變數的狀態。</span><span class="sxs-lookup"><span data-stu-id="9127f-165">The user advances through the schedule from breakpoint to breakpoint and examines the state of these variables.</span></span>  
  
 <span data-ttu-id="9127f-166">下表顯示 [變數清單] 的快顯功能表動作。</span><span class="sxs-lookup"><span data-stu-id="9127f-166">The following table shows the Context menu actions for the Variable List.</span></span>  
  
|<span data-ttu-id="9127f-167">選項</span><span class="sxs-lookup"><span data-stu-id="9127f-167">Option</span></span>|<span data-ttu-id="9127f-168">動作</span><span class="sxs-lookup"><span data-stu-id="9127f-168">Action</span></span>|  
|------------|------------|  
|<span data-ttu-id="9127f-169">儲存訊息</span><span class="sxs-lookup"><span data-stu-id="9127f-169">Save Message</span></span>|<span data-ttu-id="9127f-170">以滑鼠右鍵按一下 [非 null 的訊息中的變數清單] 窗格**儲存訊息**選項。</span><span class="sxs-lookup"><span data-stu-id="9127f-170">Right-click a Message that is non-null in the Variable List pane for the **Save Message** option.</span></span> <span data-ttu-id="9127f-171">會出現訊息提示您選取要儲存它的目錄。</span><span class="sxs-lookup"><span data-stu-id="9127f-171">A message appears prompting you to select a directory to which to save it.</span></span>|  
  
### <a name="service-options-drop-down-list"></a><span data-ttu-id="9127f-172">服務選項下拉式清單</span><span class="sxs-lookup"><span data-stu-id="9127f-172">Service Options drop-down list</span></span>  
 <span data-ttu-id="9127f-173">[服務選項] 下拉式清單會根據執行個體與偵錯工具的狀態顯示有效的動作。</span><span class="sxs-lookup"><span data-stu-id="9127f-173">The Service Options drop-down list shows you the valid actions based on the state of the instance and the debugger.</span></span> <span data-ttu-id="9127f-174">下表顯示 [服務選項] 下拉式清單中的可用動作。</span><span class="sxs-lookup"><span data-stu-id="9127f-174">The following table shows the available actions in the Service Options drop-down list.</span></span>  
  
|<span data-ttu-id="9127f-175">選項</span><span class="sxs-lookup"><span data-stu-id="9127f-175">Option</span></span>|<span data-ttu-id="9127f-176">動作</span><span class="sxs-lookup"><span data-stu-id="9127f-176">Action</span></span>|  
|------------|------------|  
|<span data-ttu-id="9127f-177">繼續服務</span><span class="sxs-lookup"><span data-stu-id="9127f-177">Continue Service</span></span>|<span data-ttu-id="9127f-178">若您附加服務，繼續執行在中斷點停止的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="9127f-178">Continues an orchestration instance that stopped at a breakpoint if you attached the service.</span></span>|  
|<span data-ttu-id="9127f-179">在偵錯模式下繼續</span><span class="sxs-lookup"><span data-stu-id="9127f-179">Resume in Debug mode</span></span>|<span data-ttu-id="9127f-180">在偵錯模式下繼續已擱置的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="9127f-180">Resumes a suspended orchestration instance in debug mode.</span></span> <span data-ttu-id="9127f-181">這可讓您進入互動模式、附加到執行個體，然後以互動方式加以偵錯。</span><span class="sxs-lookup"><span data-stu-id="9127f-181">This enables you to go into interactive mode, attach to the instance, and debug it interactively.</span></span><br /><br /> <span data-ttu-id="9127f-182">在作業檢視與協調流程偵錯工具中都可使用。</span><span class="sxs-lookup"><span data-stu-id="9127f-182">Available from the Operations views and the Orchestration Debugger.</span></span> <span data-ttu-id="9127f-183">它只適用於協調流程。</span><span class="sxs-lookup"><span data-stu-id="9127f-183">It only applies to orchestrations.</span></span>|  
|<span data-ttu-id="9127f-184">終止服務</span><span class="sxs-lookup"><span data-stu-id="9127f-184">Terminate Service</span></span>|<span data-ttu-id="9127f-185">終止協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="9127f-185">Terminates an orchestration instance.</span></span>|  
|<span data-ttu-id="9127f-186">附加</span><span class="sxs-lookup"><span data-stu-id="9127f-186">Attach</span></span>|<span data-ttu-id="9127f-187">附加服務至協調流程執行個體，然後擷取目前的狀態與變數。</span><span class="sxs-lookup"><span data-stu-id="9127f-187">Attaches the service to the orchestration instance and retrieves the current state and variables</span></span>|  
|<span data-ttu-id="9127f-188">移除類別上的所有中斷點</span><span class="sxs-lookup"><span data-stu-id="9127f-188">Remove all Breakpoints on Class</span></span>|<span data-ttu-id="9127f-189">移除協調流程類別中的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="9127f-189">Removes all the breakpoints in the orchestration class.</span></span> <span data-ttu-id="9127f-190">只有未附加時才可使用。</span><span class="sxs-lookup"><span data-stu-id="9127f-190">Only available when not attached.</span></span>|  
|<span data-ttu-id="9127f-191">移除所有中斷點</span><span class="sxs-lookup"><span data-stu-id="9127f-191">Remove all Breakpoints</span></span>|<span data-ttu-id="9127f-192">移除協調流程執行個體中的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="9127f-192">Removes all the breakpoints in the orchestration instance.</span></span> <span data-ttu-id="9127f-193">只有附加時才可使用。</span><span class="sxs-lookup"><span data-stu-id="9127f-193">Only available when attached.</span></span>|  
|<span data-ttu-id="9127f-194">儲存所有訊息</span><span class="sxs-lookup"><span data-stu-id="9127f-194">Save All Messages</span></span>|<span data-ttu-id="9127f-195">只要您選取追蹤所有輸入/輸出訊息，就會儲存與協調流程執行個體相關的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="9127f-195">Saves all the messages associated with the orchestration instance as long as you have selected to track all inbound/outbound messages.</span></span>|  
|<span data-ttu-id="9127f-196">在中斷點顯示動作</span><span class="sxs-lookup"><span data-stu-id="9127f-196">Show Action in Breakpoint</span></span>|<span data-ttu-id="9127f-197">將中斷前執行最後動作的圖形標示為黃色。</span><span class="sxs-lookup"><span data-stu-id="9127f-197">Highlights the shape as yellow for the last action executed before breaking.</span></span>|  
|<span data-ttu-id="9127f-198">檢視呼叫協調流程</span><span class="sxs-lookup"><span data-stu-id="9127f-198">View Calling Orchestration</span></span>|<span data-ttu-id="9127f-199">將檢視傳回建立呼叫的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="9127f-199">Returns the view to the orchestration instance that made the call.</span></span> <span data-ttu-id="9127f-200">也就是說，會將您帶回父協調流程。</span><span class="sxs-lookup"><span data-stu-id="9127f-200">That is, it takes you back to the parent orchestration.</span></span><br /><br /> <span data-ttu-id="9127f-201">只有在呼叫的協調流程執行個體上可以使用。</span><span class="sxs-lookup"><span data-stu-id="9127f-201">Only available on a called orchestration instance.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="9127f-202">本節內容</span><span class="sxs-lookup"><span data-stu-id="9127f-202">In This Section</span></span>  
  
-   [<span data-ttu-id="9127f-203">協調流程偵錯工具中的報告模式</span><span class="sxs-lookup"><span data-stu-id="9127f-203">Reporting Mode in Orchestration Debugger</span></span>](../core/reporting-mode-in-orchestration-debugger.md)  
  
-   [<span data-ttu-id="9127f-204">協調流程偵錯工具中的互動模式</span><span class="sxs-lookup"><span data-stu-id="9127f-204">Interactive Mode in Orchestration Debugger</span></span>](../core/interactive-mode-in-orchestration-debugger.md)  
  
## <a name="see-also"></a><span data-ttu-id="9127f-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9127f-205">See Also</span></span>  
 [<span data-ttu-id="9127f-206">偵錯協調流程</span><span class="sxs-lookup"><span data-stu-id="9127f-206">Debugging an Orchestration</span></span>](../core/debugging-an-orchestration.md)