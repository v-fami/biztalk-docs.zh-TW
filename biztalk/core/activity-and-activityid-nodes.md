---
title: "Activity 和 ActivityID 節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActivityID nodes [Tracking Profile Editor]
- Activity nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- activities [BAM], definitions
ms.assetid: 94d4130a-53c5-4cd5-916a-4a6bd9acbf23
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d100c88eec5f5a05db2bb651968aa987e3ec4e33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="activity-and-activityid-nodes"></a><span data-ttu-id="a7863-102">Activity 和 ActivityID 節點</span><span class="sxs-lookup"><span data-stu-id="a7863-102">Activity and ActivityID Nodes</span></span>
<span data-ttu-id="a7863-103">Activity 和 ActivityID 節點是用以包含和識別活動定義。</span><span class="sxs-lookup"><span data-stu-id="a7863-103">Activity and ActivityID nodes are used to contain and identify an activity definition.</span></span> <span data-ttu-id="a7863-104">Activity 節點是活動定義中之項目的父資料夾。</span><span class="sxs-lookup"><span data-stu-id="a7863-104">The Activity node is the parent folder for the items in the activity definition.</span></span> <span data-ttu-id="a7863-105">所有的資料項目和商務事件節點都附屬和包含在關聯的活動節點中。</span><span class="sxs-lookup"><span data-stu-id="a7863-105">All data items and business event nodes are subordinate to and contained within the associated activity node.</span></span> <span data-ttu-id="a7863-106">Activity 節點的命稱應該反映活動本身的名稱。</span><span class="sxs-lookup"><span data-stu-id="a7863-106">The name of the Activity node should reflect the name of the activity itself.</span></span>  
  
 <span data-ttu-id="a7863-107">ActivityID 節點是在活動定義中自動產生的項目，應包含活動的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="a7863-107">The ActivityID node is an automatically generated item in the activity definition and is intended to hold a unique identifier for the activity.</span></span> <span data-ttu-id="a7863-108">ActivityID 節點可用以追蹤使用者提供的識別碼或系統產生的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a7863-108">The ActivityID node can be used to track user supplied identifiers or identifiers that are system generated.</span></span> <span data-ttu-id="a7863-109">例如，在將訂單編號做為系統中所有訂單之唯一識別碼的案例中，您可使用此編號做為 ActivityID，在此情況下，您將從一些事件來源 (例如訂單結構描述中的 PO 編號欄位) 對應 ActivityID 的值。</span><span class="sxs-lookup"><span data-stu-id="a7863-109">For example, in a scenario in which you have purchase order number as a unique identifier across all purchase orders in the system, you can use it as the ActivityID, in which case you will map the value of the ActivityID from some event source, such as the PO number field in the purchase order schema.</span></span> <span data-ttu-id="a7863-110">另一方面，如果訂單值不是唯一的，則您可以不要對應節點，BAM 會在執行階段自動產生唯一的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a7863-110">On the other hand, if the purchase order value is not unique, then you can leave the node unmapped, and BAM will automatically generate unique identifiers at run-time.</span></span>  
  
 <span data-ttu-id="a7863-111">活動可能和其他活動相關。</span><span class="sxs-lookup"><span data-stu-id="a7863-111">Activities can be related to other activities.</span></span> <span data-ttu-id="a7863-112">在某些案例中，這些關係明確屬於觀察模型的一部分。</span><span class="sxs-lookup"><span data-stu-id="a7863-112">In some scenarios these relationships are explicitly part of the observation model.</span></span>  <span data-ttu-id="a7863-113">特別是，當任何使用者檢視包含兩個以上的活動時，這些活動之間就自動具有關係。</span><span class="sxs-lookup"><span data-stu-id="a7863-113">Specifically, when any user view includes two or more activities, there is an automatic relationship between those activities.</span></span>  <span data-ttu-id="a7863-114">當這樣的關係存在時，在活動樹狀目錄的 Activity 節點下就會為每個已知的對等活動自動建立關係節點。</span><span class="sxs-lookup"><span data-stu-id="a7863-114">When such a relationship exists, a relationship node is automatically created in the activity tree, under the Activity node, for each known peer activity.</span></span> <span data-ttu-id="a7863-115">在有資料關係但沒有擴展的檢視時，您可以手動將關係節點新增到活動樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="a7863-115">In scenarios where there  is a data relationship and no spanning view exists, you can manually add a relationship node to  the activity tree.</span></span>  
  
 <span data-ttu-id="a7863-116">在任一情況下，關係節點的目的都是為相關的活動提供識別碼。</span><span class="sxs-lookup"><span data-stu-id="a7863-116">In either case, the purpose of the relationship node is to provide an identifier for the related activity.</span></span> <span data-ttu-id="a7863-117">例如，訂單和出貨可能有多對多的關係 (一張 PO 可能包含多次出貨；一次出貨所裝載的產品可能滿足許多 PO)。</span><span class="sxs-lookup"><span data-stu-id="a7863-117">For example, purchase orders and shipments can have a many-to-many relationship (one PO is fulfilled by multiple shipments; one shipment can carry a product satisfying many POs).</span></span>  <span data-ttu-id="a7863-118">每張訂單的活動記錄可能有多個相關之出貨的指標，每次出貨活動記錄可能指向一或多張訂單。</span><span class="sxs-lookup"><span data-stu-id="a7863-118">The activity record for each purchase order can have multiple pointers to related shipments, and each shipment activity record could point to one or more Purchase Orders.</span></span>  <span data-ttu-id="a7863-119">以資料庫的方式來說，關係節點的值就是資料表中另一個活動的外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a7863-119">In database terms, the value of the relationship node is the foreign key into the table for the other activity.</span></span>  
  
## <a name="working-with-activity-id-nodes"></a><span data-ttu-id="a7863-120">使用 Activity ID 節點</span><span class="sxs-lookup"><span data-stu-id="a7863-120">Working with Activity ID nodes</span></span>  
 <span data-ttu-id="a7863-121">例如，請考慮下列案例： EquityLoan 協調流程包含 LoanProcess 活動資料夾。</span><span class="sxs-lookup"><span data-stu-id="a7863-121">For example, consider the following scenario: the EquityLoan orchestration contains the activity folder LoanProcess.</span></span> <span data-ttu-id="a7863-122">它參考下列商務事件：</span><span class="sxs-lookup"><span data-stu-id="a7863-122">It references business events including the following:</span></span>  
  
-   <span data-ttu-id="a7863-123">LoanApplicationReceived</span><span class="sxs-lookup"><span data-stu-id="a7863-123">LoanApplicationReceived</span></span>  
  
-   <span data-ttu-id="a7863-124">CHRequest</span><span class="sxs-lookup"><span data-stu-id="a7863-124">CHRequest</span></span>  
  
-   <span data-ttu-id="a7863-125">CHResponse</span><span class="sxs-lookup"><span data-stu-id="a7863-125">CHResponse</span></span>  
  
-   <span data-ttu-id="a7863-126">AppraisalRequest</span><span class="sxs-lookup"><span data-stu-id="a7863-126">AppraisalRequest</span></span>  
  
-   <span data-ttu-id="a7863-127">AppraisalResponse</span><span class="sxs-lookup"><span data-stu-id="a7863-127">AppraisalResponse</span></span>  
  
-   <span data-ttu-id="a7863-128">已核准</span><span class="sxs-lookup"><span data-stu-id="a7863-128">Approved</span></span>  
  
-   <span data-ttu-id="a7863-129">拒絕</span><span class="sxs-lookup"><span data-stu-id="a7863-129">Denied</span></span>  
  
 <span data-ttu-id="a7863-130">ActivityID 節點可讓方案開發人員擷取唯一識別活動的資料，例如訂單編號或是訊息的 SSN 欄位 (在範本案例的情況中)。</span><span class="sxs-lookup"><span data-stu-id="a7863-130">The ActivityID node enables the solution developer to extract data that uniquely identifies the activity, such as a purchase order number, or, in the case of the sample scenario, the SSN field of the message.</span></span> <span data-ttu-id="a7863-131">如果您未將任何資料拖曳到 ActivityID 節點，自動產生的 GUID 就會識別商務活動。</span><span class="sxs-lookup"><span data-stu-id="a7863-131">If you do not drag any data to the ActivityID node, an automatically generated GUID identifies the business activities.</span></span>  
  
 <span data-ttu-id="a7863-132">若要定義不同協調流程中之商務事件或里程碑之間的關係，目標協調流程就必須參考 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="a7863-132">To define the relationship between business events or milestones in different orchestrations, the target orchestration must reference the ActivityID.</span></span> <span data-ttu-id="a7863-133">如需如何使用 TPE 實作關係的詳細資訊，請參閱[關係節點](../core/relationship-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="a7863-133">For more information about how to implement relationships using TPE, see [Relationship Nodes](../core/relationship-nodes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7863-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7863-134">See Also</span></span>  
 [<span data-ttu-id="a7863-135">TPE 活動檢視節點</span><span class="sxs-lookup"><span data-stu-id="a7863-135">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)