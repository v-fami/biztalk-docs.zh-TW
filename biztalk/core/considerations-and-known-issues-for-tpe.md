---
title: "考量和已知的問題的 TPE |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, known issues
- planning, Tracking Profile Editor
- Tracking Profile Editor, planning
ms.assetid: e96d85e0-e9ae-434a-b54e-5950f4a2b9c6
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d630b2cfa5cca1d7a441796ef8c555d02bb04910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-and-known-issues-for-tpe"></a><span data-ttu-id="34a33-102">TPE 的考量和已知問題</span><span class="sxs-lookup"><span data-stu-id="34a33-102">Considerations and Known Issues for TPE</span></span>
<span data-ttu-id="34a33-103">當您使用追蹤設定檔和 TPE 時，應該考量下列問題。</span><span class="sxs-lookup"><span data-stu-id="34a33-103">You should consider the following issues when you work with tracking profiles and the TPE.</span></span>  
  
## <a name="naming-folders-in-the-tpe"></a><span data-ttu-id="34a33-104">在 TPE 中命名資料夾</span><span class="sxs-lookup"><span data-stu-id="34a33-104">Naming Folders in the TPE</span></span>  
 <span data-ttu-id="34a33-105">在追蹤設定檔編輯器中命名資料夾時，請注意下列命名需求：</span><span class="sxs-lookup"><span data-stu-id="34a33-105">Note the following naming requirements when naming folders in Tracking Profile Editor:</span></span>  
  
-   <span data-ttu-id="34a33-106">資料夾名稱和資料項目執行個體值的組合長度不能超過 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="34a33-106">The length of the combination of folder name and data item instance values must not exceed 128 characters.</span></span>  
  
-   <span data-ttu-id="34a33-107">就 Continuation 和 ContinuationID 資料夾而言，資料夾的命名是讓兩個協調流程相互關聯的關鍵。</span><span class="sxs-lookup"><span data-stu-id="34a33-107">For Continuation and ContinuationID folders, the naming of the folder is the key to correlating two orchestrations.</span></span> <span data-ttu-id="34a33-108">例如，如果協調流程 A 是協調流程 B 的父系，則協調流程 A 包含的接續資料夾名稱，會直接對應至協調流程 B 中的 ContinuationID 資料夾。</span><span class="sxs-lookup"><span data-stu-id="34a33-108">For example, if Orchestration A is the parent of Orchestration B, Orchestration A contains a continuation folder whose name maps directly to the ContinuationID folder in Orchestration B.</span></span>  
  
## <a name="developing-orchestrations-for-the-tpe"></a><span data-ttu-id="34a33-109">開發 TPE 的協調流程</span><span class="sxs-lookup"><span data-stu-id="34a33-109">Developing Orchestrations for the TPE</span></span>  
 <span data-ttu-id="34a33-110">如果協調流程的開頭或結尾是無效圖形，您便無法將協調流程對應至商務活動。</span><span class="sxs-lookup"><span data-stu-id="34a33-110">You cannot map an orchestration to a business activity if it starts or ends with an invalid shape.</span></span> <span data-ttu-id="34a33-111">協調流程引擎不允許追蹤某些圖形。</span><span class="sxs-lookup"><span data-stu-id="34a33-111">The Orchestration engine does not allow tracking for some shapes.</span></span> <span data-ttu-id="34a33-112">其中包括：</span><span class="sxs-lookup"><span data-stu-id="34a33-112">They are:</span></span>  
  
-   <span data-ttu-id="34a33-113">訊息指派</span><span class="sxs-lookup"><span data-stu-id="34a33-113">Message Assignment</span></span>  
  
-   <span data-ttu-id="34a33-114">轉換</span><span class="sxs-lookup"><span data-stu-id="34a33-114">Transform</span></span>  
  
-   <span data-ttu-id="34a33-115">群組 (工作)</span><span class="sxs-lookup"><span data-stu-id="34a33-115">Group (Task)</span></span>  
  
-   <span data-ttu-id="34a33-116">暫止</span><span class="sxs-lookup"><span data-stu-id="34a33-116">Suspend</span></span>  
  
-   <span data-ttu-id="34a33-117">迴圈 (While)</span><span class="sxs-lookup"><span data-stu-id="34a33-117">Loop (While)</span></span>  
  
-   <span data-ttu-id="34a33-118">分支</span><span class="sxs-lookup"><span data-stu-id="34a33-118">Branch</span></span>  
  
-   <span data-ttu-id="34a33-119">Terminate</span><span class="sxs-lookup"><span data-stu-id="34a33-119">Terminate</span></span>  
  
-   <span data-ttu-id="34a33-120">擲回</span><span class="sxs-lookup"><span data-stu-id="34a33-120">Throw</span></span>  
  
-   <span data-ttu-id="34a33-121">Catch</span><span class="sxs-lookup"><span data-stu-id="34a33-121">Catch</span></span>  
  
-   <span data-ttu-id="34a33-122">While 圖形</span><span class="sxs-lookup"><span data-stu-id="34a33-122">While shape</span></span>  
  
 <span data-ttu-id="34a33-123">當對應至商務活動時，請使用下列指導方針，以便讓追蹤設定檔編輯器和其他 BAM 工具能夠使用那些活動：</span><span class="sxs-lookup"><span data-stu-id="34a33-123">Use the following guidelines when mapping to business activities so that the Tracking Profile Editor and other BAM tools can use them:</span></span>  
  
-   <span data-ttu-id="34a33-124">對於「群組」圖形，請使用非交易式「範圍」圖形。</span><span class="sxs-lookup"><span data-stu-id="34a33-124">For the Group shape, use a non-transactional Scope shape.</span></span>  
  
-   <span data-ttu-id="34a33-125">對於 While 圖形，請將圖形包裝在非交易式「範圍」圖形中。</span><span class="sxs-lookup"><span data-stu-id="34a33-125">For the While shape, wrap it in a non-transactional Scope shape.</span></span>  
  
-   <span data-ttu-id="34a33-126">「終止」圖形則沒有解決方法，因為此圖形的結束事件絕不會發生在正常實例中。</span><span class="sxs-lookup"><span data-stu-id="34a33-126">For the Terminate shapes, there is no workaround, because the end event of this shape never occurs in a normal scenario.</span></span>  
  
-   <span data-ttu-id="34a33-127">請勿使用任何不允許拖放作業的圖形來啟動或結束排程。</span><span class="sxs-lookup"><span data-stu-id="34a33-127">Do not start or end schedules with any of the shapes for which drag-and-drop operations are not permitted.</span></span>  
  
## <a name="applying-tracking-profiles-that-monitor-running-processes"></a><span data-ttu-id="34a33-128">套用可監控正在執行之處理程序的追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="34a33-128">Applying Tracking Profiles that Monitor Running Processes</span></span>  
 <span data-ttu-id="34a33-129">如果活動包含 BAM 接續，更新追蹤設定檔可能會影響進行中的活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="34a33-129">Updating a tracking profile can impact activity instances in progress if the activity includes a BAM continuation.</span></span> <span data-ttu-id="34a33-130">特別是，如果更新追蹤設定檔時指定由下游攔截的活動項目資料已有記錄，就可能覆寫原始值。</span><span class="sxs-lookup"><span data-stu-id="34a33-130">Specifically, if the update to the tracking profile specifies a downstream interception of data for an activity item already recorded, it is possible that the original value will be overwritten.</span></span> <span data-ttu-id="34a33-131">基本上，任何的單一事件資料流都不會受到套用追蹤設定檔更新所影響，因為每個資料流物件均與活動/資料流開始時即已備妥的設定檔特定版本緊密繫結。</span><span class="sxs-lookup"><span data-stu-id="34a33-131">In essence, any single event stream will not be affected by the application of tracking profile updates because each stream object is tied to the specific version of the profile which was in place at the time the activity/stream started.</span></span> <span data-ttu-id="34a33-132">但是，由於接續是將多個事件資料流相互關聯的方法，在設定檔更新時還未開始的資料流將會接受更新所指定的變更，以致可能發生上述的資料覆寫情況。</span><span class="sxs-lookup"><span data-stu-id="34a33-132">However, because continuations are the means of correlating multiple event streams, streams not yet begun at the time of a profile update will pick up the changes in the update, thus introducing the possible data overwrite described.</span></span> <span data-ttu-id="34a33-133">如需有關接續的詳細資訊，請參閱[活動接續](../core/activity-continuation.md)和[如何建立接續](../core/how-to-create-a-continuation.md)。</span><span class="sxs-lookup"><span data-stu-id="34a33-133">For more information about continuations, see [Activity Continuation](../core/activity-continuation.md) and [How to Create a Continuation](../core/how-to-create-a-continuation.md).</span></span>  
  
## <a name="tracking-profiles-without-a-send-or-receive-shape-from-which-to-draw-message-properties"></a><span data-ttu-id="34a33-134">追蹤沒有用來繪製訊息屬性之「傳送」或「接收」圖形的設定檔</span><span class="sxs-lookup"><span data-stu-id="34a33-134">Tracking Profiles Without a Send or Receive Shape from Which to Draw Message Properties</span></span>  
 <span data-ttu-id="34a33-135">接續會透過活動之間相同的內容屬性或內容資料追蹤活動。</span><span class="sxs-lookup"><span data-stu-id="34a33-135">Continuations track activities through context properties or payload data that are the same between activities.</span></span> <span data-ttu-id="34a33-136">諸如「訊息識別碼」、「服務識別碼」和「執行個體識別碼」等屬性會變更活動之間的值。</span><span class="sxs-lookup"><span data-stu-id="34a33-136">Properties such as Message ID, Service ID, and Instance ID change value between activities.</span></span>  
  
 <span data-ttu-id="34a33-137">您可以使用下列方法建立追蹤設定檔以處理這種實例：</span><span class="sxs-lookup"><span data-stu-id="34a33-137">You can create tracking profiles to handle this scenario by using the following methods:</span></span>  
  
-   <span data-ttu-id="34a33-138">如果協調流程透過動態繫結傳送訊息至其他協調流程，則接續可以使用全域唯一內容資料值。</span><span class="sxs-lookup"><span data-stu-id="34a33-138">If an orchestration sends a message through a dynamic binding to another orchestration, then a globally unique payload data value can be used for the continuation.</span></span>  
  
-   <span data-ttu-id="34a33-139">如果訊息中沒有唯一的內容資料，可以使用訊息的交換識別碼。</span><span class="sxs-lookup"><span data-stu-id="34a33-139">If there is no unique payload data in the message, then the interchange ID of the message can be used.</span></span> <span data-ttu-id="34a33-140">若要使用交換識別碼，您必須在相同的「接收」圖形上追蹤該識別碼。</span><span class="sxs-lookup"><span data-stu-id="34a33-140">To use the interchange ID, you must track it on the same Receive shape.</span></span> <span data-ttu-id="34a33-141">如果您建立新的訊息，在交換識別碼變更建立新的訊息時，您無法使用的交換識別碼。</span><span class="sxs-lookup"><span data-stu-id="34a33-141">You cannot use the interchange ID if you create a new message, as the interchange ID changes when the new message is created.</span></span> <span data-ttu-id="34a33-142">從「傳送」或「接收」圖形以外的任何圖形追蹤交換識別碼，並不可靠。</span><span class="sxs-lookup"><span data-stu-id="34a33-142">Tracking the interchange ID from any shape other than a Receive or Send shape is not reliable.</span></span>  
  
-   <span data-ttu-id="34a33-143">只要在協調流程中使用從管線接收的完全相同訊息，您也可以使用訊息識別碼，也就是說，協調流程連接埠會繫結至管線，並且從該位置追蹤「接收」圖形和訊息識別碼。</span><span class="sxs-lookup"><span data-stu-id="34a33-143">You can also use message ID as long as the exact same message that is received from the pipeline is used in the orchestration, that is, the orchestration port is bound to a pipeline and a Receive shape and the message ID are tracked from that location.</span></span> <span data-ttu-id="34a33-144">如果您從不同的圖形追蹤訊息識別碼，追蹤到的訊息識別碼將會無效而無法用於接續。</span><span class="sxs-lookup"><span data-stu-id="34a33-144">If you track the message ID from a different shape, then the message ID will be invalid for use in continuations.</span></span>  
  
-   <span data-ttu-id="34a33-145">如果協調流程呼叫另一個協調流程和未傳遞訊息，或協調流程呼叫另一個協調流程，但是被呼叫端沒有任何 「 建構 」、 接收或傳送圖形，可以擷取內容資料值，使用者可以使用執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="34a33-145">If an orchestration calls another orchestration and no message is passed, or an orchestration calls another orchestration but the callee does not have any Construct, Receive, or Send shape where payload data values can be retrieved, the user can use the instance ID.</span></span> <span data-ttu-id="34a33-146">呼叫的協調流程的執行個體識別碼不會變更。</span><span class="sxs-lookup"><span data-stu-id="34a33-146">The instance ID for the called orchestrations does not change.</span></span>  
  
-   <span data-ttu-id="34a33-147">如果協調流程透過執行呼叫 (而不是直接呼叫) 以載入其他協調流程，就無法使用任何靜態訊息屬性追蹤活動。</span><span class="sxs-lookup"><span data-stu-id="34a33-147">If the orchestration loads another orchestration through an execution call rather than calling it directly, then there is no way to use any static message properties to track the activity.</span></span> <span data-ttu-id="34a33-148">使用者無法啟用接續。</span><span class="sxs-lookup"><span data-stu-id="34a33-148">The user cannot enable a continuation.</span></span> <span data-ttu-id="34a33-149">在此執行個體中執行追蹤的唯一方式，是透過包含要執行追蹤之唯一內容資料的管線傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="34a33-149">The only way to perform tracking in this instance is if a message is passed through the pipeline that contains unique payload data on which to perform the tracking.</span></span>  
  
## <a name="you-cannot-use-a-session-id-as-a-continuation-token-for-pass-through-pipelines"></a><span data-ttu-id="34a33-150">您無法使用工作階段識別碼當做通過管線的接續 Token</span><span class="sxs-lookup"><span data-stu-id="34a33-150">You Cannot Use a Session ID as a Continuation Token for Pass-Through Pipelines</span></span>  
 <span data-ttu-id="34a33-151">在追蹤設定檔中，當您從訊息內容選取項目時，追蹤設定檔會繫結至該訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="34a33-151">In a tracking profile, when you select items from a message payload, the tracking profile is bound to the schema of that message.</span></span> <span data-ttu-id="34a33-152">在通過管線中，結構描述的名稱值是空值。</span><span class="sxs-lookup"><span data-stu-id="34a33-152">In a pass-through pipeline, the schema name value is a null value.</span></span> <span data-ttu-id="34a33-153">當 BAM 嘗試根據連接埠名稱和結構描述名稱載入組態時，無法對應至工作階段識別碼結構描述，並且引擎不會追蹤任何資料。</span><span class="sxs-lookup"><span data-stu-id="34a33-153">When BAM attempts to load the configuration by port name and schema name it cannot make the match to the session ID schema and no data is tracked by the engine.</span></span>  
  
 <span data-ttu-id="34a33-154">對於通過管線，如果真的需要追蹤內容資料，您可以從追蹤設定檔移除所有內容追蹤或使用 XML 管線。</span><span class="sxs-lookup"><span data-stu-id="34a33-154">For pass-through pipelines, you can either remove all payload tracking from the tracking profile or use XML pipelines if you do need to track the payload data.</span></span>  
  
## <a name="using-unique-port-names"></a><span data-ttu-id="34a33-155">使用唯一的連接埠名稱</span><span class="sxs-lookup"><span data-stu-id="34a33-155">Using Unique Port Names</span></span>  
 <span data-ttu-id="34a33-156">列舉雙向連接埠時，TPE 會將雙向連接埠顯示為兩個邏輯連接埠 (傳送和接收埠)。</span><span class="sxs-lookup"><span data-stu-id="34a33-156">When enumerating two-way ports, the TPE displays them as two logical ports, a send and a receive port.</span></span> <span data-ttu-id="34a33-157">每個邏輯連接埠會顯示為相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="34a33-157">Each of these logical ports is displayed with the same name.</span></span> <span data-ttu-id="34a33-158">BizTalk Server 可以讓您使用相同的名稱建立單向和雙向連接埠。</span><span class="sxs-lookup"><span data-stu-id="34a33-158">BizTalk Server allows you to create one-way and two-way ports with the same name.</span></span> <span data-ttu-id="34a33-159">例如，您可以建立名為 "Port1" 的雙向連接埠，然後使用相同的名稱建立接收埠。</span><span class="sxs-lookup"><span data-stu-id="34a33-159">For example, you can create a two-way port named "Port1" and then create a receive port with the same name.</span></span> <span data-ttu-id="34a33-160">在這些情況中，TPE 會顯示一次接收埠並顯示兩次雙向連接埠，其中一次是當做接收埠，另一次是當做傳送埠。</span><span class="sxs-lookup"><span data-stu-id="34a33-160">In these cases the TPE displays the receive port once and the two-way port twice, once as a receive port and once as a send port.</span></span>  
  
 <span data-ttu-id="34a33-161">在這個情況中，TPE 會將追蹤設定檔套用至兩個接收埠。</span><span class="sxs-lookup"><span data-stu-id="34a33-161">TPE will apply tracking profiles to both receive ports in this case.</span></span> <span data-ttu-id="34a33-162">我們建議為連接埠提供唯一的名稱以協助正確識別。</span><span class="sxs-lookup"><span data-stu-id="34a33-162">We recommend that ports be given unique names to help identify them properly.</span></span>  
  
## <a name="using-tpe-orchestrations-with-a-parallel-shape-as-the-first-shape"></a><span data-ttu-id="34a33-163">搭配平行圖形使用 TPE 協調流程當做第一個圖形</span><span class="sxs-lookup"><span data-stu-id="34a33-163">Using TPE Orchestrations with a Parallel Shape as the First Shape</span></span>  
 <span data-ttu-id="34a33-164">如果您使用「分叉」、「平行」或「待命」圖形開始協調流程，則無法對應其中一個分支的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="34a33-164">If you begin an orchestration with a Fork, Parallel, or Listen shape, you cannot map an activity ID on one of the branches.</span></span> <span data-ttu-id="34a33-165">在平行處理的情況中，您可以對應「分叉」圖形上的 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="34a33-165">In cases of parallel processing you can map the ActivityID above the Fork shape.</span></span> <span data-ttu-id="34a33-166">您也可以讓 BAM 產生活動識別碼，以避免協調流程的最上層發生平行圖形問題。</span><span class="sxs-lookup"><span data-stu-id="34a33-166">You can also let BAM generate the activity ID to avoid the issue of a parallel shape at the top of the orchestration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34a33-167">將活動對應至一個以上的路徑，並將 ActivityID 對應至「分叉」圖形的一個路徑，會在依照未對應 ActivityID 的路徑進行處理時造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="34a33-167">Mapping an activity to more than one path and also mapping the ActivityID to one path of the Fork shape causes an error when processing follows the path on which the ActivityID is not mapped.</span></span>  
  
## <a name="availability-of-message-properties-at-design-time"></a><span data-ttu-id="34a33-168">設計階段的訊息屬性可用性</span><span class="sxs-lookup"><span data-stu-id="34a33-168">Availability of Message Properties at Design Time</span></span>  
 <span data-ttu-id="34a33-169">建立追蹤設定檔時，並非所有的訊息屬性都可以使用。</span><span class="sxs-lookup"><span data-stu-id="34a33-169">When creating tracking profiles, not all message properties are available.</span></span> <span data-ttu-id="34a33-170">當訊息屬性所對應的圖形位於協調流程最上層時，這是最可能發生的情況。</span><span class="sxs-lookup"><span data-stu-id="34a33-170">This is most likely to be encountered when the shape where the message properties are mapped from is at the top of an orchestration.</span></span> <span data-ttu-id="34a33-171">在這些執行個體中，訊息屬性的值為空值。</span><span class="sxs-lookup"><span data-stu-id="34a33-171">In these instances, the value of the message properties is null.</span></span>  
  
 <span data-ttu-id="34a33-172">舉例來說，「待命」圖形便是協調流程中的第一個圖形。</span><span class="sxs-lookup"><span data-stu-id="34a33-172">An example of this is where the Listen shape is the first shape in an orchestration.</span></span> <span data-ttu-id="34a33-173">當訊息屬性從這個圖形對應，只有下列屬性有值： InstanceID、 ServiceID 和 ServiceClassID。</span><span class="sxs-lookup"><span data-stu-id="34a33-173">When message properties are mapped from this shape, only the following properties have values: InstanceID, ServiceID and ServiceClassID.</span></span> <span data-ttu-id="34a33-174">(此時 MessageID 不在範圍中，並且具有空值)。</span><span class="sxs-lookup"><span data-stu-id="34a33-174">(MessageID is not in scope at this point and has a null value.)</span></span>  
  
## <a name="you-cannot-map-shapes-inside-a-loop-shape-to-report-a-milestone"></a><span data-ttu-id="34a33-175">您無法在「迴圈」圖形內對應圖形以報告里程碑</span><span class="sxs-lookup"><span data-stu-id="34a33-175">You Cannot Map Shapes Inside a Loop Shape to Report a Milestone</span></span>  
 <span data-ttu-id="34a33-176">TPE 區塊會將「迴圈」圖形內的來源對應至活動，而那些活動是對應至迴圈以外的項目。</span><span class="sxs-lookup"><span data-stu-id="34a33-176">The TPE blocks mapping sources contained from within a Loop shape to activities that are mapped to items that are outside of the loop.</span></span>  
  
 <span data-ttu-id="34a33-177">迴圈活動是指，在協調流程中迴圈或重複的動作。</span><span class="sxs-lookup"><span data-stu-id="34a33-177">Looping activities refers to actions that loop, or repeat, within an orchestration.</span></span> <span data-ttu-id="34a33-178">您也許可以從協調流程內迴圈的動作擷取事件。</span><span class="sxs-lookup"><span data-stu-id="34a33-178">It is possible to capture the events from actions that loop within an orchestration.</span></span> <span data-ttu-id="34a33-179">若要執行這項操作，請建立其他活動，並對應迴圈內所有的新活動里程碑和資料。</span><span class="sxs-lookup"><span data-stu-id="34a33-179">To do this, you create another activity and map all of the new activity milestones and data inside the loop.</span></span> <span data-ttu-id="34a33-180">請務必這麼做，因為迴圈中的資料處理將會在每個排程執行發生一次以上。</span><span class="sxs-lookup"><span data-stu-id="34a33-180">This is necessary because the data processing in the loop will occur more than once per scheduled execution.</span></span>  
  
 <span data-ttu-id="34a33-181">例如，如果您有多個明細項目在迴圈中處理採購單，如等問題 「 哪個訂單的項目價格為 $100？ 」</span><span class="sxs-lookup"><span data-stu-id="34a33-181">For example, if you have a purchase order with multiple line items that process in a loop, questions like “Which purchase orders have item prices of $100?"</span></span> <span data-ttu-id="34a33-182">模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="34a33-182">are ambiguous.</span></span> <span data-ttu-id="34a33-183">明確的問題如下：</span><span class="sxs-lookup"><span data-stu-id="34a33-183">Unambiguous questions are:</span></span>  
  
 <span data-ttu-id="34a33-184">哪個訂單的明細項目價格為 $100?</span><span class="sxs-lookup"><span data-stu-id="34a33-184">Which purchase orders have line items with a price of $100?</span></span>  
  
 <span data-ttu-id="34a33-185">哪個訂單的總計/最小/最大項目價格為 $100?</span><span class="sxs-lookup"><span data-stu-id="34a33-185">Which purchase orders have Total/Min/Max item prices of $100?</span></span>  
  
 <span data-ttu-id="34a33-186">建立明確的問題必須將明細項目與訂單當做兩回事來思考。</span><span class="sxs-lookup"><span data-stu-id="34a33-186">Creating unambiguous questions requires thinking of the line items as something separate from the purchase order.</span></span> <span data-ttu-id="34a33-187">在追蹤設定檔編輯器中，根活動 (例如訂單) 會對應至迴圈外的所有動作。</span><span class="sxs-lookup"><span data-stu-id="34a33-187">In the Tracking Profile Editor, the root activity (for example, a purchase order) maps to all actions outside the loop.</span></span> <span data-ttu-id="34a33-188">子活動 (例如明細項目) 會對應至迴圈內的動作。</span><span class="sxs-lookup"><span data-stu-id="34a33-188">The child activity (for example, a line item) maps to the actions inside the loop.</span></span>  
  
 <span data-ttu-id="34a33-189">一般使用這些建構類型的方式是，根據與外部活動相關的內部活動，分解重複的迴圈並具有相關的活動。</span><span class="sxs-lookup"><span data-stu-id="34a33-189">The typical approach to working with these types of constructs is to decompose the repeating loop and to have a related activity based on the inner activity that is related to the outer activity.</span></span>  
  
 <span data-ttu-id="34a33-190">您需要使用內容項目當做根活動的 ActivityID，並讓這個內容項目可以用在迴圈內部的某些訊息中。</span><span class="sxs-lookup"><span data-stu-id="34a33-190">You need to use a payload item as the ActivityID for the root activity and have this payload item available in some of the messages inside the loop.</span></span> <span data-ttu-id="34a33-191">請將活動對應至子活動底下顯示的關係節點，並將該活動命名為根活動。</span><span class="sxs-lookup"><span data-stu-id="34a33-191">Map the activity to the relationship node that displays under the child activity and name it as the root activity.</span></span>  
  
## <a name="tracking-profiles-spanning-multiple-applications"></a><span data-ttu-id="34a33-192">跨越多個應用程式的追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="34a33-192">Tracking Profiles Spanning Multiple Applications</span></span>  
 <span data-ttu-id="34a33-193">如果追蹤設定檔跨越多個應用程式，則必須在部署解決方案的所有應用程式之後，才能部署追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="34a33-193">If a tracking profile spans multiple applications, the tracking profile must be deployed after all applications in the solution are deployed.</span></span> <span data-ttu-id="34a33-194">如果追蹤設定檔不是部署的最後一個項目，您會收到下列訊息，「**找不到對應來源。**「 部署精靈呼叫 BTTDeploy.exe 時。</span><span class="sxs-lookup"><span data-stu-id="34a33-194">If the tracking profile is not the last item deployed, you will receive the following message, "**Mapping source not found.**", when the deployment wizard calls BTTDeploy.exe.</span></span>  
  
## <a name="mapping-multiple-biztalk-server-artifacts-to-a-document-reference-url-or-messageid-nodes"></a><span data-ttu-id="34a33-195">將多個 BizTalk Server 成品對應至文件參考 URL 或 MessageID 節點</span><span class="sxs-lookup"><span data-stu-id="34a33-195">Mapping Multiple BizTalk Server Artifacts to a Document Reference URL or MessageID Nodes</span></span>  
 <span data-ttu-id="34a33-196">TPE 可以讓您從多個 BizTalk Server 成品拖放至相同的文件參考 URL 或 MessageID 節點。</span><span class="sxs-lookup"><span data-stu-id="34a33-196">The TPE allows you to drag and drop from multiple BizTalk Server artifacts onto the same document reference URL or MessageID node.</span></span>  
  
 <span data-ttu-id="34a33-197">在其中的多個來源會對應到相同的項目中的 BAM 活動的情況下，最後一個成品，是 BAM 期間發生處理是指保存在追蹤資料，而且可以檢視 BAM 入口網站中。</span><span class="sxs-lookup"><span data-stu-id="34a33-197">In cases where multiple sources are mapped to the same item in a BAM activity, the last artifact that was encountered during BAM processing is the one that persists in the tracking data and can be viewed in the BAM portal.</span></span>  
  
## <a name="updating-btt-versions-to-match-biztalk-solution-versions"></a><span data-ttu-id="34a33-198">更新 BTT 版本以符合 BizTalk 解決方案版本</span><span class="sxs-lookup"><span data-stu-id="34a33-198">Updating BTT Versions to Match BizTalk Solution Versions</span></span>  
 <span data-ttu-id="34a33-199">BAM 開發人員和系統管理員可以藉由自動化 BTT 檔案的更新，以維護追蹤設定檔和 BizTalk 解決方案之間的版本同步。</span><span class="sxs-lookup"><span data-stu-id="34a33-199">BAM developers and administrators can maintain version synchronization between tracking profiles and BizTalk solutions by automating the update to the BTT file.</span></span> <span data-ttu-id="34a33-200">若要這樣做，請修改**版本**屬性**DataLevel** BTT 檔案項目。</span><span class="sxs-lookup"><span data-stu-id="34a33-200">To do this, modify the **Version** attribute in the **DataLevel** element of the BTT file.</span></span> <span data-ttu-id="34a33-201">在下列範例項目中，您可以修改 TargetAssemblyName 和 SchemaName 屬性中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="34a33-201">In the following sample element, you would modify the version information in the TargetAssemblyName and SchemaName attributes.</span></span>  
  
```  
<DataLevel Name="City" SourceTypeSelected="Messaging Payload" TargetAssemblyName="TheImplementationOfOrderMgmt, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c5b33e44ffa4658b" SchemaName="TheImplementationOfOrderMgmt.PurchaseOrder,TheImplementationOfOrderMgmt, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c5b33e44ffa4658b" SomXPath="/*[local-name()='<Schema>' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='PurchaseOrder' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='Header' and namespace-uri()='']/*[local-name()='ShipTo' and namespace-uri()='']/@*[local-name()='City' and namespace-uri()='']" XPath="/*[local-name()='PurchaseOrder' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='Header' and namespace-uri()='']/*[local-name()='ShipTo' and namespace-uri()='']/@*[local-name()='City' and namespace-uri()='']" IsBeginActivity="true" IsEndActivity="false">  
```  
  
## <a name="some-orchestration-shapes-cannot-be-tracked-in-the-tpe"></a><span data-ttu-id="34a33-202">無法追蹤 TPE 中的某些協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="34a33-202">Some Orchestration Shapes Cannot be Tracked in the TPE</span></span>  
 <span data-ttu-id="34a33-203">協調流程引擎不會針對下列圖形產生事件，因此在 TPE 中無法追蹤或對應這些圖形：</span><span class="sxs-lookup"><span data-stu-id="34a33-203">The orchestration ongine does not generate events for the following shapes and thus these shapes cannot be tracked or mapped in the TPE:</span></span>  
  
-   <span data-ttu-id="34a33-204">工作</span><span class="sxs-lookup"><span data-stu-id="34a33-204">Task</span></span>  
  
-   <span data-ttu-id="34a33-205">所有分支</span><span class="sxs-lookup"><span data-stu-id="34a33-205">All Branches</span></span>  
  
-   <span data-ttu-id="34a33-206">暫止</span><span class="sxs-lookup"><span data-stu-id="34a33-206">Suspend</span></span>  
  
-   <span data-ttu-id="34a33-207">Terminate</span><span class="sxs-lookup"><span data-stu-id="34a33-207">Terminate</span></span>  
  
-   <span data-ttu-id="34a33-208">擲回</span><span class="sxs-lookup"><span data-stu-id="34a33-208">Throw</span></span>  
  
-   <span data-ttu-id="34a33-209">Catch</span><span class="sxs-lookup"><span data-stu-id="34a33-209">Catch</span></span>  
  
-   <span data-ttu-id="34a33-210">MessageAssignment (因為這是「建構」圖形的一部分)</span><span class="sxs-lookup"><span data-stu-id="34a33-210">MessageAssignment (because it is part of the Construct shape)</span></span>  
  
-   <span data-ttu-id="34a33-211">轉換 (因為這是「建構」圖形的一部分)</span><span class="sxs-lookup"><span data-stu-id="34a33-211">Transform (because it is part of the Construct shape)</span></span>  
  
-   <span data-ttu-id="34a33-212">迴圈</span><span class="sxs-lookup"><span data-stu-id="34a33-212">Loop</span></span>  
  
## <a name="tpe-not-retrieving-deployed-tracking-profiles"></a><span data-ttu-id="34a33-213">TPE 未擷取已部署的追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="34a33-213">TPE Not Retrieving Deployed Tracking Profiles</span></span>  
 <span data-ttu-id="34a33-214">在升級或重新部署之後，您可能會在擷取已部署的追蹤設定檔時遭遇困難。</span><span class="sxs-lookup"><span data-stu-id="34a33-214">After an upgrade or redeployment you may experience difficulties in retrieving deployed tracking profiles.</span></span> <span data-ttu-id="34a33-215">這可能是由於 BizTalkMgmtDb 資料庫儲存於登錄中時所使用的伺服器名稱不相符。</span><span class="sxs-lookup"><span data-stu-id="34a33-215">This can be caused by a mismatch in the manner in which the server name on which BizTalkMgmtDb database is stored in the registry.</span></span>  
  
 <span data-ttu-id="34a33-216">BizTalkMgmtDb 會在群組組態期間寫入至登錄。</span><span class="sxs-lookup"><span data-stu-id="34a33-216">The BizTalkMgmtDb is written to the registry during Group configuration.</span></span> <span data-ttu-id="34a33-217">TPE 會使用此項目來尋找主要匯入資料庫，並篩選追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="34a33-217">The TPE uses the entry to find the Primary Import database and to filter the tracking profiles.</span></span>  
  
 <span data-ttu-id="34a33-218">在組態期間可以用數種格式輸入伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="34a33-218">During configuration it is possible to enter the server name in several formats.</span></span> <span data-ttu-id="34a33-219">例如：</span><span class="sxs-lookup"><span data-stu-id="34a33-219">For example:</span></span>  
  
-   <span data-ttu-id="34a33-220">mgmtsvr1316267,15001\inst</span><span class="sxs-lookup"><span data-stu-id="34a33-220">mgmtsvr1316267,15001\inst</span></span>  
  
-   <span data-ttu-id="34a33-221">MGMTSVR1316267\inst,15001</span><span class="sxs-lookup"><span data-stu-id="34a33-221">MGMTSVR1316267\inst,15001</span></span>  
  
 <span data-ttu-id="34a33-222">TPE 會在使用登錄項目時執行基本的字串比較。</span><span class="sxs-lookup"><span data-stu-id="34a33-222">The TPE performs a basic string comparison when using the registry entry.</span></span> <span data-ttu-id="34a33-223">若要擷取部署的追蹤設定檔是為了檢查預存的伺服器和資料庫名稱，並在 TPE 中輸入**設定管理資料庫** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="34a33-223">To retrieve the deployed tracking profiles it is necessary to inspect the stored server and database names and enter them in the TPE **Set Management Database** dialog box.</span></span>  
  
#### <a name="to-determine-the-syntax-for-server-and-database-names-and-enter-it-in-the-biztalk-management-database"></a><span data-ttu-id="34a33-224">判斷伺服器和資料庫名稱的語法，並將其輸入至 BizTalk 管理資料庫</span><span class="sxs-lookup"><span data-stu-id="34a33-224">To determine the syntax for server and database names and enter it in the BizTalk Management database.</span></span>  
  
1.  <span data-ttu-id="34a33-225">開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**自訂組態管理員**。</span><span class="sxs-lookup"><span data-stu-id="34a33-225">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**Custom Configuration Manager**.</span></span> <span data-ttu-id="34a33-226">如需使用**自訂組態管理員**，請參閱[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="34a33-226">For information about using the **Custom Configuration Manager**, see [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span></span>  
  
2.  <span data-ttu-id="34a33-227">瀏覽窗格中，選取**群組**以開啟群組組態頁面。</span><span class="sxs-lookup"><span data-stu-id="34a33-227">In the navigation pane, select **Group** to open the group configuration page.</span></span>  
  
3.  <span data-ttu-id="34a33-228">在**資料存放區**方格中，觀察**伺服器名稱**和**資料庫名稱**。</span><span class="sxs-lookup"><span data-stu-id="34a33-228">In the **Data Stores** grid, observe the formats of the **Server Name** and the **Database Name**.</span></span>  
  
4.  <span data-ttu-id="34a33-229">開啟 TPE，然後選取**工具**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="34a33-229">Open the TPE and select the **Tools** menu item.</span></span>  
  
5.  <span data-ttu-id="34a33-230">選取**設定管理資料庫**功能表項目，以開啟**設定管理資料庫** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="34a33-230">Select the **Set Management Database** menu item to open the **Set Management Database** dialog box.</span></span>  
  
6.  <span data-ttu-id="34a33-231">在**SQL Server**文字方塊中，輸入伺服器名稱用於**伺服器名稱**欄位**資料存放區**gridon**自訂組態管理員**群組頁面。</span><span class="sxs-lookup"><span data-stu-id="34a33-231">In the **SQL Server** text box, enter the server name that was used in the **Server Name** field of the **Data Stores** gridon the **Custom Configuration Manager** group page.</span></span>  
  
7.  <span data-ttu-id="34a33-232">在**資料庫名稱**文字方塊中，輸入資料庫名稱用於**資料庫名稱**欄位**資料存放區**gridon**自訂組態管理員**群組頁面。</span><span class="sxs-lookup"><span data-stu-id="34a33-232">In the **Database name** text box, enter the database name that was used in the **Database Name** field of the **Data Stores** gridon the **Custom Configuration Manager** group page.</span></span>  
  
8.  <span data-ttu-id="34a33-233">按一下**確定**按鈕以儲存項目。</span><span class="sxs-lookup"><span data-stu-id="34a33-233">Click the **OK** button to save the entries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34a33-234">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34a33-234">See Also</span></span>  
 <span data-ttu-id="34a33-235">[使用 TPE](../core/using-the-tpe.md) </span><span class="sxs-lookup"><span data-stu-id="34a33-235">[Using the TPE](../core/using-the-tpe.md) </span></span>  
 [<span data-ttu-id="34a33-236">追蹤設定檔編輯器</span><span class="sxs-lookup"><span data-stu-id="34a33-236">Tracking Profile Editor</span></span>](../core/tracking-profile-editor.md)