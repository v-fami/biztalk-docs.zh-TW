---
title: "何謂活動檢視？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], Activity view [Tracking Profile Editor]
- activities [BAM], definitions
- Tracking Profile Editor, Activity view
- Activity view [Tracking Profile Editor]
ms.assetid: ae6bcdc8-e426-4148-b83d-08a1a5e99ca3
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fd27a4de6b2ac86f94b105aabe679df3c88c06d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-an-activity-view"></a><span data-ttu-id="b1dc6-103">何謂活動檢視？</span><span class="sxs-lookup"><span data-stu-id="b1dc6-103">What Is an Activity View?</span></span>
<span data-ttu-id="b1dc6-104">活動檢視含有匯入的 BAM 活動定義，這是您使用 Excel 的 BAM 增益集所建立的。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-104">An activity view contains the imported BAM activity definition that you create with the BAM Add-In for Excel.</span></span> <span data-ttu-id="b1dc6-105">BAM 活動定義是對於商務程序之追蹤需求的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-105">The BAM activity definition is an abstract of your trace requirements for your business process.</span></span> <span data-ttu-id="b1dc6-106">活動可以跨越多個協調流程與連接埠。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-106">An activity can span multiple orchestrations and ports.</span></span> <span data-ttu-id="b1dc6-107">您可以匯入一次活動定義，然後將活動定義對應至每個符合部分定義的協調流程或傳訊成品。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-107">You import the activity definition once and map it to each orchestration or messaging artifact that fulfills some part of the definition.</span></span>  
  
 <span data-ttu-id="b1dc6-108">[活動檢視] 連結位於追蹤設定檔編輯器 (TPE) 使用者介面的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-108">The Activity View link is on the left pane of Tracking Profile Editor (TPE) user interface.</span></span>  
  
## <a name="activity-view-elements"></a><span data-ttu-id="b1dc6-109">活動檢視項目</span><span class="sxs-lookup"><span data-stu-id="b1dc6-109">Activity view elements</span></span>  
 <span data-ttu-id="b1dc6-110">活動檢視會以樹狀檢視顯示追蹤設定檔的整體結構，並且包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="b1dc6-110">The activity view displays the overall structure of the tracking profile in tree view and includes the following elements:</span></span>  
  
-   <span data-ttu-id="b1dc6-111">里程碑</span><span class="sxs-lookup"><span data-stu-id="b1dc6-111">Milestones</span></span>  
  
-   <span data-ttu-id="b1dc6-112">活動的資料項目</span><span class="sxs-lookup"><span data-stu-id="b1dc6-112">Data items for the activity</span></span>  
  
-   <span data-ttu-id="b1dc6-113">事件來源</span><span class="sxs-lookup"><span data-stu-id="b1dc6-113">Event sources</span></span>  
  
-   <span data-ttu-id="b1dc6-114">資料來源</span><span class="sxs-lookup"><span data-stu-id="b1dc6-114">Data sources</span></span>  
  
 <span data-ttu-id="b1dc6-115">**里程碑**： 里程碑是指定的處理序中定義某個點的物件。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-115">**Milestones**: Milestones are objects which define a point in a given process.</span></span> <span data-ttu-id="b1dc6-116">可以用下列其中一種方式來存取：</span><span class="sxs-lookup"><span data-stu-id="b1dc6-116">Milestones are accessed in one of three ways:</span></span>  
  
-   <span data-ttu-id="b1dc6-117">您可以從協調流程排程拖曳圖形，並且該圖形的執行結束時間會由 BAM 回報做為里程碑的值。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-117">You can drag a shape from an orchestration schedule, and the end-time for that shape’s execution is reported by BAM as the milestone value.</span></span>  
  
-   <span data-ttu-id="b1dc6-118">您可以從右側結構描述表示法拖曳傳訊屬性至目標里程碑。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-118">You can drag a messaging property, from a schematic representation on the right, to a target milestone.</span></span>  
  
-   <span data-ttu-id="b1dc6-119">您可以拖曳含有里程碑值的訊息內容結構描述節點。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-119">You can drag a message payload schema node which contains a milestone value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1dc6-120">DATETIME ONLY 類型結構描述節點是在執行階段評估的。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-120">The DATETIME ONLY type schema nodes are evaluated at run time.</span></span> <span data-ttu-id="b1dc6-121">執行階段發生的任何轉換問題 (Conversion 或 Casting) 都會造成事件日誌中出現追蹤錯誤。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-121">Any conversion or casting problem at run time results in a tracking error being placed in the event log.</span></span>  
  
 <span data-ttu-id="b1dc6-122">**資料項目**： 資料項目會定義特定項目的訊息執行個體、 系統或升級的屬性的 XML 結構描述的物件。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-122">**Data items**: Data items are objects which define a particular element from an XML schema for a message instance, system, or promoted property.</span></span> <span data-ttu-id="b1dc6-123">展開結構描述，找出並選取您想要的項目，然後將該項目拖曳到正確的資料項目類型資料夾，即可存取資料項目。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-123">You access the data item by expanding the schema to find and select the element you are interested in and dragging the element to the correct data item type folder.</span></span> <span data-ttu-id="b1dc6-124">關於資料項目 (例如 XPath) 的詳細資訊會儲存在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-124">Information about the data items (for example, XPath) is stored in the profile.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1dc6-125">TPE 僅支援擁有零對一表示法的資料項目，其表示法如特定資料欄位的訊息結構描述中所定義。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-125">TPE supports only data items that have a zero-to-one representation as defined in the message schema for a particular data field.</span></span> <span data-ttu-id="b1dc6-126">如果有一對多表示法的資料項目，協調流程追蹤可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-126">Errors may occur in orchestration tracking when there are data items that have one-to-many representations.</span></span> <span data-ttu-id="b1dc6-127">在這些情況中，不會將任何資料儲存在 BAM 主要匯入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-127">In these situations no data is stored in the BAM Primary Import database.</span></span> <span data-ttu-id="b1dc6-128">如果沒有發生錯誤，也無法確保追蹤的是哪個資料項目。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-128">If an error does not occur, then there is no guarantee which of the data item is tracked.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1dc6-129">BAM 開發人員必須注意到，屬性是根據 BizTalk Server 程序規則填入的，而不是 BAM。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-129">BAM developers need to be aware that properties are populated according to BizTalk Server process rules, and not BAM.</span></span>  
>   
>  <span data-ttu-id="b1dc6-130">例如，在 SMTP 配接器中，內容屬性 (例如 SMTPServer、CC 和 From) 在明確填入之前，並不會含有任何值。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-130">For example, in the SMTP adapter the context properties, such as SMTPServer, CC, and From, do not contain any values until they are explicitly populated.</span></span> <span data-ttu-id="b1dc6-131">一旦填入之後，它們的值就會出現在 BAM 主要匯入資料庫中，並且也可以用來進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-131">Once they have been populated their values will appear in the BAM Primary Import database and they will be available for tracking.</span></span>  
  
## <a name="activity-view-context-menus"></a><span data-ttu-id="b1dc6-132">活動檢視快顯功能表</span><span class="sxs-lookup"><span data-stu-id="b1dc6-132">Activity view context menus</span></span>  
 <span data-ttu-id="b1dc6-133">活動檢視可用動作的快顯功能表，會依在 [協調流程檢視] 中選取的節點而動態地變更。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-133">The context menus of available actions for the activity view dynamically change depending on the node selected in the Orchestration View.</span></span> <span data-ttu-id="b1dc6-134">例如，如果您選取活動資料夾節點，快速鍵功能表將會包含該活動資料夾的快速鍵功能表項目。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-134">For example, if you select an activity folder node, the shortcut menu will contain the shortcut menu items for that activity folder.</span></span>  
  
 <span data-ttu-id="b1dc6-135">將右側來源事件窗格中的事件和資料拖曳到 [活動] 檢視的事件或資料節點，即可將事件和資料與商務活動中的項目產生關聯。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-135">You associate events and data to the items in the business activity by dragging them from the source event pane on the right to the event or data node in the Activity view.</span></span>  
  
 <span data-ttu-id="b1dc6-136">以滑鼠右鍵按一下活動檢視樹狀結構中的節點，即可在該視窗中看到節點的快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-136">The context menus for the nodes in the activity view are accessible by right-clicking a node in the tree.</span></span> <span data-ttu-id="b1dc6-137">下列畫面顯示活動檢視的根節點。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-137">The following screen shows the root node for activity views.</span></span> <span data-ttu-id="b1dc6-138">下表說明活動檢視中不同節點快顯功能表中的項目。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-138">The following tables describe the items in the context menus for the different nodes for an activity view.</span></span>  
  
 <span data-ttu-id="b1dc6-139">**活動定義樹狀目錄根節點**</span><span class="sxs-lookup"><span data-stu-id="b1dc6-139">**Activity Definition Tree root node**</span></span>  
  
 ![](../core/media/activityviewcontextmenu.gif "activityviewcontextmenu")  
  
|<span data-ttu-id="b1dc6-140">功能表項目</span><span class="sxs-lookup"><span data-stu-id="b1dc6-140">Menu Item</span></span>|<span data-ttu-id="b1dc6-141">使用方式</span><span class="sxs-lookup"><span data-stu-id="b1dc6-141">Usage</span></span>|  
|---------------|-----------|  
|<span data-ttu-id="b1dc6-142">新接續</span><span class="sxs-lookup"><span data-stu-id="b1dc6-142">New Continuation</span></span>|<span data-ttu-id="b1dc6-143">在 [活動] 樹狀結構中插入新的 [Continuation] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-143">Inserts a new Continuation folder into the Activity tree.</span></span> <span data-ttu-id="b1dc6-144">您對應此資料夾從接續的來源區段的值。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-144">You map the value for this folder from the source segment of a continuation.</span></span><br /><br /> <span data-ttu-id="b1dc6-145">與 [ContinuationID] 資料夾搭配使用，提供一種方式讓填入相同活動的多個元件彼此互相轉手處理工作。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-145">Used in conjunction with a ContinuationID folder to provide a means to hand off processing between multiple components that populate the same activity.</span></span> <span data-ttu-id="b1dc6-146">BizTalk 協調流程、連接埠、BufferedEventStreams 和 DirectEventStreams 都是這些元件的例子。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-146">Examples of these components are BizTalk orchestrations, ports, BufferedEventStreams, and DirectEventStreams.</span></span> <span data-ttu-id="b1dc6-147">**注意：**接續資料夾名稱可以包含最多 127 個字元。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-147">**Note:**  Continuation folder names can contain a maximum of 127 characters.</span></span>|  
|<span data-ttu-id="b1dc6-148">新 ContinuationID</span><span class="sxs-lookup"><span data-stu-id="b1dc6-148">New ContinuationID</span></span>|<span data-ttu-id="b1dc6-149">在 [活動] 樹狀結構中插入 [ContinuationID] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-149">Inserts a ContinuationID folder into the Activity tree.</span></span> <span data-ttu-id="b1dc6-150">您可以將這個資料夾對應到接續的 continued-to 區段。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-150">You map this folder to continued-to segment of a continuation.</span></span> <span data-ttu-id="b1dc6-151">例如，如果協調流程 A 接續到協調流程 B，這個資料夾就必須對應到協調流程 B 中的項目。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-151">For example, if orchestration A continues to Orchestration B, this folder must be mapped to an item from Orchestration B.</span></span><br /><br /> <span data-ttu-id="b1dc6-152">與 [Continuation] 資料夾搭配使用，提供一種方式讓填入相同活動的多個元件彼此互相轉手處理工作。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-152">Used in conjunction with a Continuation folder to provide a means to hand off processing between multiple components that populate the same activity.</span></span> <span data-ttu-id="b1dc6-153">BizTalk 協調流程、連接埠、BufferedEventStreams 和 DirectEventStreams 都是這些元件的例子。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-153">Examples of these components are BizTalk orchestrations, ports, BufferedEventStreams, and DirectEventStreams.</span></span> <span data-ttu-id="b1dc6-154">**注意：** continuationid 資料夾可以包含最多 127 個字元。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-154">**Note:**  ContinuationID folder names can contain a maximum of 127 characters.</span></span>|  
|<span data-ttu-id="b1dc6-155">新增關聯性</span><span class="sxs-lookup"><span data-stu-id="b1dc6-155">New Relationship</span></span>|<span data-ttu-id="b1dc6-156">在 [活動] 樹狀結構中插入新的關係資料夾。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-156">Inserts a new relationship folder into the Activity tree.</span></span> <span data-ttu-id="b1dc6-157">用於發佈組成檢視之各個活動之間的關係。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-157">Used to publish the relationship between activities that form a view.</span></span> <span data-ttu-id="b1dc6-158">**注意：**關係資料夾名稱可以包含最多 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-158">**Note:**  Relationship folder names can contain a maximum of 128 characters.</span></span> <span data-ttu-id="b1dc6-159">這包括了伺服器名稱和 BizTalk 管理資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-159">The includes the server name and BizTalk Management database name.</span></span>|  
|<span data-ttu-id="b1dc6-160">新 Document Reference URL</span><span class="sxs-lookup"><span data-stu-id="b1dc6-160">New Document Reference URL</span></span>|<span data-ttu-id="b1dc6-161">在 [活動] 樹狀結構中插入新的 [Document Reference URL] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-161">Inserts a new Document Reference URL folder into the Activity tree.</span></span> <span data-ttu-id="b1dc6-162">用於將參考 URL 設定為含有此活動相關文件的位置。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-162">Used to set a reference URL to a location that contains a document that is related to this activity.</span></span> <span data-ttu-id="b1dc6-163">**注意：** Document Reference URL 資料夾名稱可以包含最多 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-163">**Note:**  Document Reference URL folder names can contain a maximum of 128 characters.</span></span>|  
  
 <span data-ttu-id="b1dc6-164">**屬性節點**</span><span class="sxs-lookup"><span data-stu-id="b1dc6-164">**Property Node**</span></span>  
  
|<span data-ttu-id="b1dc6-165">功能表項目</span><span class="sxs-lookup"><span data-stu-id="b1dc6-165">Menu Item</span></span>|<span data-ttu-id="b1dc6-166">使用方式</span><span class="sxs-lookup"><span data-stu-id="b1dc6-166">Usage</span></span>|  
|---------------|-----------|  
|<span data-ttu-id="b1dc6-167">與所選資料產生關聯</span><span class="sxs-lookup"><span data-stu-id="b1dc6-167">Associate Selected Data</span></span>|<span data-ttu-id="b1dc6-168">用於在訊息內容或內容屬性資料項目與 BAM 活動資料項目資料夾之間建立關聯。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-168">Used to create an association between a message payload or context property data item and the BAM Activity data item folder.</span></span>|  
  
 <span data-ttu-id="b1dc6-169">**事件節點**</span><span class="sxs-lookup"><span data-stu-id="b1dc6-169">**Event node**</span></span>  
  
|<span data-ttu-id="b1dc6-170">功能表項目</span><span class="sxs-lookup"><span data-stu-id="b1dc6-170">Menu Item</span></span>|<span data-ttu-id="b1dc6-171">使用方式</span><span class="sxs-lookup"><span data-stu-id="b1dc6-171">Usage</span></span>|  
|---------------|-----------|  
|<span data-ttu-id="b1dc6-172">與所選動作的結尾產生關聯</span><span class="sxs-lookup"><span data-stu-id="b1dc6-172">Associate with the end of the selected action</span></span>|<span data-ttu-id="b1dc6-173">用來建立協調流程圖形、 DateTime 訊息內容或 DateTime 內容屬性資料項目與 BAM 活動里程碑資料夾之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="b1dc6-173">Used to create an association between an orchestration shape, DateTime message payload, or DateTime context property data item and the BAM Activity milestone folder.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1dc6-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1dc6-174">See Also</span></span>  
 <span data-ttu-id="b1dc6-175">[使用事件資料流實作 BAM 活動](../core/implementing-bam-activities-with-event-streams.md) </span><span class="sxs-lookup"><span data-stu-id="b1dc6-175">[Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md) </span></span>  
 <span data-ttu-id="b1dc6-176">[在 Excel 中定義商務活動和檢視](../core/defining-business-activities-and-views-in-excel.md) </span><span class="sxs-lookup"><span data-stu-id="b1dc6-176">[Defining Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md) </span></span>  
 [<span data-ttu-id="b1dc6-177">TPE 的元件</span><span class="sxs-lookup"><span data-stu-id="b1dc6-177">Components of the TPE</span></span>](../core/components-of-the-tpe.md)