---
title: "Continuation 和 ContinuationID 節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- continuation tokens
- Continuation nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- BAM, correlating activities
- activities, linking
- activities, continuation tokens
- ContinuationID nodes [Tracking Profile Editor]
ms.assetid: aa050660-66f7-4084-b6bf-b9319ce625af
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8aa8956721d4a44b51b8d2c7776560aaa878f864
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="continuation-and-continuationid-nodes"></a><span data-ttu-id="133d4-102">Continuation 和 ContinuationID 節點</span><span class="sxs-lookup"><span data-stu-id="133d4-102">Continuation and ContinuationID Nodes</span></span>
<span data-ttu-id="133d4-103">接續提供有關下列資訊的 BAM 基礎結構指導：</span><span class="sxs-lookup"><span data-stu-id="133d4-103">Continuations provide guidance to the BAM infrastructure about the following information:</span></span>  
  
-   <span data-ttu-id="133d4-104">預期的事件發生順序</span><span class="sxs-lookup"><span data-stu-id="133d4-104">The order in which events are expected to occur</span></span>  
  
-   <span data-ttu-id="133d4-105">處理唯一識別碼任何變更的方法，此識別碼與事件項目相互關聯</span><span class="sxs-lookup"><span data-stu-id="133d4-105">A way to handle any change in the unique ID to which event items are correlated</span></span>  
  
 <span data-ttu-id="133d4-106">換句話說，接續會定義這項資訊在活動參與者之間的傳輸。</span><span class="sxs-lookup"><span data-stu-id="133d4-106">To state this another way, continuations define the transfer of this information between contributors to an activity.</span></span> <span data-ttu-id="133d4-107">在下列情況中會發生傳輸：</span><span class="sxs-lookup"><span data-stu-id="133d4-107">A transfer occurs in the following situations:</span></span>  
  
-   <span data-ttu-id="133d4-108">從活動開始到結束期間，ActivityID 有所變更。</span><span class="sxs-lookup"><span data-stu-id="133d4-108">There is a change in the ActivityID between the time an activity begins and ends.</span></span> <span data-ttu-id="133d4-109">舉例來說，假設您有兩個相關的訊息，例如訂單編號與銷售訂單編號。</span><span class="sxs-lookup"><span data-stu-id="133d4-109">For example, you have two related messages such as a Purchase Order number and Sales Order number.</span></span> <span data-ttu-id="133d4-110">各自都有指定的唯一編號，例如訂單編號是 123456，銷售訂單編號是 987654。</span><span class="sxs-lookup"><span data-stu-id="133d4-110">Each has a unique number assigned to it, such as 123456 for the Purchase Order number and 987654 for Sales Order number.</span></span> <span data-ttu-id="133d4-111">您可以使用接續使訂單編號與銷售訂單兩者的唯一識別碼相等，如此，無論哪個唯一識別碼與內送事件相關聯，都可以使事件與常用活動相互關聯。</span><span class="sxs-lookup"><span data-stu-id="133d4-111">You would use a continuation to equate the unique identifiers for the Purchase Order and the Sales Order so that events can be correlated to the common activity regardless of which unique identifier is associated with the incoming events.</span></span>  
  
-   <span data-ttu-id="133d4-112">您從一個執行階段環境轉換到另一個執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="133d4-112">You have a transition from one run-time environment to another.</span></span> <span data-ttu-id="133d4-113">例如，假設有一個應用程式提供訂單到 BizTalk Server 傳訊管線，然後叫用協調流程，與協調流程，然後將控制項傳遞至傳送出貨通知的應用程式，在您有兩個環境轉換： 從傳訊管線協調流程與傳訊管線的協調流程。</span><span class="sxs-lookup"><span data-stu-id="133d4-113">For example, in a scenario where you have an application that supplies a purchase order to a BizTalk Server messaging pipeline, which then invokes an orchestration, and the orchestration then passes control to an application that sends a shipping notice, you have two environment transitions: from a messaging pipeline to a an orchestration and from an orchestration to a messaging pipeline.</span></span>  
  
 <span data-ttu-id="133d4-114">當選取用於接續的屬性時，請記得一個要點，就是必須從相同的內容對應這些屬性。</span><span class="sxs-lookup"><span data-stu-id="133d4-114">An important point to remember when selecting a property to use for your continuation is that the properties must be mapped from the same context.</span></span>  
  
 <span data-ttu-id="133d4-115">例如，如果您有屬性 Message.InterchangeID 和 servicecontext.InterchangeID，則您似乎可以使用 InterchangeID 來建立接續。</span><span class="sxs-lookup"><span data-stu-id="133d4-115">For example, if you have the propertiesy Message.InterchangeID and servicecontext.InterchangeID it might appear that you could use the InterchangeID to create your continuation.</span></span> <span data-ttu-id="133d4-116">但是，如果訊息來自於不同的內容，您將無法使用 InterchangeID (或其他屬性) 來可靠地建立接續。</span><span class="sxs-lookup"><span data-stu-id="133d4-116">If the messages come from different contexts you cannot use the InterchangeID (or other property) to reliably create a continuation.</span></span>  
  
## <a name="working-with-continuation-nodes"></a><span data-ttu-id="133d4-117">使用 Continuation 節點</span><span class="sxs-lookup"><span data-stu-id="133d4-117">Working with Continuation nodes</span></span>  
 <span data-ttu-id="133d4-118">Continuation 節點含有指示唯一執行個體識別碼，也稱為資料項目*接續 token*。</span><span class="sxs-lookup"><span data-stu-id="133d4-118">The Continuation node contains data items that indicate a unique instance ID, also called a *continuation token*.</span></span> <span data-ttu-id="133d4-119">利用接續 Token，開發人員就可以使用 ContinuationID 節點與其他活動連結。</span><span class="sxs-lookup"><span data-stu-id="133d4-119">By using the continuation token, developers can link to other activities using the ContinuationID node.</span></span>  
  
 <span data-ttu-id="133d4-120">三種使用 Continuation 和 ContinuationID 節點的基本實例：</span><span class="sxs-lookup"><span data-stu-id="133d4-120">There are three basic scenarios in which Continuation and ContinuationID nodes are used:</span></span>  
  
-   <span data-ttu-id="133d4-121">協調流程到協調流程</span><span class="sxs-lookup"><span data-stu-id="133d4-121">Orchestration to orchestration</span></span>  
  
-   <span data-ttu-id="133d4-122">協調流程到 BizTalk 解決方案</span><span class="sxs-lookup"><span data-stu-id="133d4-122">Orchestration to BizTalk solution</span></span>  
  
-   <span data-ttu-id="133d4-123">BizTalk 解決方案到協調流程</span><span class="sxs-lookup"><span data-stu-id="133d4-123">BizTalk solution to orchestration</span></span>  
  
 <span data-ttu-id="133d4-124">在協調流程實例中，TPE 必須定義 Continuation 節點和 ContinuationID 節點，並且這兩個節點的名稱必須相同，BAM 才能使活動相互關聯。</span><span class="sxs-lookup"><span data-stu-id="133d4-124">In the orchestration scenario the TPE must define a Continuation node, and a ContinuationID node, and the nodes must have the same name in order for BAM to correlate the activities.</span></span>  
  
 <span data-ttu-id="133d4-125">在協調流程到 BizTalk 解決方案的實例中，您會使用 TPE 定義 Continuation 節點，而開發人員會建立使用 BAM API 的解決方案來處理接續的目的部分。</span><span class="sxs-lookup"><span data-stu-id="133d4-125">In the orchestration to BizTalk solution scenario, you use the TPE to define a Continuation node and the developer creates a solution that uses the BAM API to handle the destination portion of the continuation..</span></span>  
  
 <span data-ttu-id="133d4-126">在 BizTalk 解決方案到協調流程的實例中，開發人員會使用 BAM API 提供接續組的起源，而且您會使用 TPE 定義 ContinuationID 節點。</span><span class="sxs-lookup"><span data-stu-id="133d4-126">In the BizTalk solution to orchestration, the developer uses the BAM API to supply the origination of the continuation pair and you use TPE to define a ContinuationID node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="133d4-127">雙向連接埠可以在任何一個方向運作，也就是說，攔截通過連接埠的資料可能需要啟用接續 (視 BizTalk 解決方案的行為而定)。</span><span class="sxs-lookup"><span data-stu-id="133d4-127">Two-way ports can operate in either direction, which means that interception of data that passes through the ports can, depending on the behavior of the BizTalk solution, require enabling of a continuation.</span></span> <span data-ttu-id="133d4-128">舉例來說，如果活動在任一方向記錄 BizTalk Server 傳訊連接埠啟動的 PortEndTime (如果項目的名稱依序是 MessageReceived 和 MessageSent)，您就必須在這兩者之間建立接續。</span><span class="sxs-lookup"><span data-stu-id="133d4-128">For example, if the activity records “PortEndTime” for activation of a BizTalk Server messaging port in either direction (if the item names are, for example, “MessageReceived” and “MessageSent,” in that order), you need to create a continuation between them.</span></span> <span data-ttu-id="133d4-129">只要有一個以上的事件資料流提供給 BAM 活動，並且每個實作碰觸點都有不同的事件資料流 (例如 BTS 內送訊息、BTS 外寄訊息、協調流程、自訂應用程式與 Web 服務)，就需要使用接續。</span><span class="sxs-lookup"><span data-stu-id="133d4-129">A continuation is required any time more than one event stream contributes to a BAM activity, and there are distinct event streams per implementation touch point (such as BTS Messaging in, BTS Messaging out, Orchestration, custom applications, and Web services).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="133d4-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="133d4-130">See Also</span></span>  
 <span data-ttu-id="133d4-131">[如何建立接續](../core/how-to-create-a-continuation.md) </span><span class="sxs-lookup"><span data-stu-id="133d4-131">[How to Create a Continuation](../core/how-to-create-a-continuation.md) </span></span>  
 [<span data-ttu-id="133d4-132">TPE 活動檢視節點</span><span class="sxs-lookup"><span data-stu-id="133d4-132">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)