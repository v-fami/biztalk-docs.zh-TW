---
title: "如何建立接續 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities, relating events
- tracking profiles, relating events
- continuations, tracking profiles
- activities, continuations
- events, relating
- orchestrations, business events
- tracking profiles, updating
- activities, tracking profiles
- tracking profiles, continuations
- tracking profiles, connecting activities
ms.assetid: 31d6fc24-676e-418c-8e78-1a46b045905d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e63983b290f0f4d7dff544cd2faea45f6cf46adc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-continuation"></a><span data-ttu-id="5fb7c-102">如何建立接續</span><span class="sxs-lookup"><span data-stu-id="5fb7c-102">How to Create a Continuation</span></span>
<span data-ttu-id="5fb7c-103">您可以建立接續，以指出在一或多個協調流程中，哪些商務事件是經由建構連接的活動而相互關聯。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-103">You create continuations to indicate which business events in one or more orchestrations are related by constructing connected activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5fb7c-104">如果活動包含 BAM 接續，更新追蹤設定檔可能會影響進行中的活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-104">Updating a tracking profile can impact activity instances in progress if the activity includes a BAM continuation.</span></span> <span data-ttu-id="5fb7c-105">特別是，如果更新追蹤設定檔時指定由下游攔截的活動項目資料已有記錄，就可能覆寫原始值。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-105">Specifically, if the update to the tracking profile specifies a downstream interception of data for an activity item already recorded, it is possible that the original value will be overwritten.</span></span> <span data-ttu-id="5fb7c-106">基本上，任何的單一事件資料流都不會受到套用追蹤設定檔更新所影響，因為每個資料流物件均與活動/資料流開始時即已備妥的設定檔特定版本緊密繫結。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-106">In essence, any single event stream will not be affected by the application of tracking profile updates because each stream object is tied to the specific version of the profile which was in place at the time the activity/stream started.</span></span>  <span data-ttu-id="5fb7c-107">但是，由於接續是將多個事件資料流相互關聯的方法，在設定檔更新時還未開始的資料流將會接受更新所指定的變更，以致可能發生上述的資料覆寫情況。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-107">However, because continuations are the means of correlating multiple event streams, streams not yet begun at the time of a profile update will pick up the changes in the update, thus introducing the possible data overwrite described.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fb7c-108">您可以建立接續不會處理訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-108">You can create continuations with orchestrations that do not process messages.</span></span> <span data-ttu-id="5fb7c-109">只要在協調流程之間傳遞執行呼叫參數，並使用 BAM API 處理接續，就能獲得有如處理訊息之協調流程般相同的功能。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-109">You can obtain the same functionality as you can for orchestrations that do process messages by passing parameters in execution calls between orchestrations and by using BAM APIs to process the continuation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5fb7c-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="5fb7c-110">Prerequisites</span></span>  
 <span data-ttu-id="5fb7c-111">若要執行此程序，您必須已部署所要連接的 BAM 活動定義和協調流程。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-111">To perform this procedure, you must have deployed BAM activity definitions and orchestrations that you will connect to.</span></span>  
  
### <a name="to-create-a-continuation"></a><span data-ttu-id="5fb7c-112">建立接續</span><span class="sxs-lookup"><span data-stu-id="5fb7c-112">To create a continuation</span></span>  
  
1.  <span data-ttu-id="5fb7c-113">開啟現有的追蹤設定檔或建立追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-113">Open an existing tracking profile or create a tracking profile.</span></span> <span data-ttu-id="5fb7c-114">如需建立追蹤設定檔的資訊，請參閱[如何建立追蹤設定檔](../core/how-to-create-a-tracking-profile.md)。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-114">For information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).</span></span>  
  
2.  <span data-ttu-id="5fb7c-115">識別*接續 token、*這是一段唯一資訊提供給這兩個活動。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-115">Identify a *continuation token,* which is a piece of unique information that is available to both activities.</span></span> <span data-ttu-id="5fb7c-116">例如，如果**CreditHistory**活動所發出的訊息啟動**LoanProcess**活動內**EquityLoan**協調流程、 的 SSN 欄位訊息可用來當作接續 token，所以這兩個活動通用的。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-116">For example, if a **CreditHistory** activity is activated by a message sent from a **LoanProcess** activity within an **EquityLoan**orchestration, the SSN field of the message can be used as a continuation token because it is common to both activities.</span></span>  
  
3.  <span data-ttu-id="5fb7c-117">以滑鼠右鍵按一下活動，然後選取**新的接續**來建立接續 (CreditHistory)。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-117">Right-click the activity and then select **New Continuation** to create a continuation (CreditHistory).</span></span> <span data-ttu-id="5fb7c-118">請為新建立的接續節點命名。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-118">Name the continuation node you just created.</span></span>  
  
4.  <span data-ttu-id="5fb7c-119">在 [協調流程排程檢視] 下，選取您在步驟 2 所選的接續 Token，例如 SSN (本例是從「傳送」動作選取)，然後將它放置到步驟 3 建立的接續節點上。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-119">From the Orchestration Schedule View, select the continuation token you chose in step 2, such as SSN (in this case from the Send action) and drop it into the continuation node you created in step 3.</span></span>  
  
5.  <span data-ttu-id="5fb7c-120">以滑鼠右鍵按一下活動，然後選取**新 ContinuationID**建立接續識別碼節點。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-120">Right-click the activity and select **New ContinuationID** to create a Continuation ID node.</span></span> <span data-ttu-id="5fb7c-121">請以您在步驟 3 中選擇的名稱為其命名，並將其拖放到含有對應資料項目 (在此情況下為「接收」動作之 SSN) 的節點中。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-121">Name it using the name you chose in step 3, and drop it in the node that contains the corresponding data item (in this case, SSN from the Receive action).</span></span>  
  
6.  <span data-ttu-id="5fb7c-122">在**檔案**功能表上，按一下 **另存新檔**，將追蹤設定檔儲存為 BizTalk 管理資料庫中的.btt 檔案，以免覆寫任何現有的.btt 檔案。</span><span class="sxs-lookup"><span data-stu-id="5fb7c-122">On the **File**menu, click **Save As**to save the tracking profile as a .btt file to the BizTalk Management database and to avoid overwriting any existing .btt file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb7c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fb7c-123">See Also</span></span>  
 <span data-ttu-id="5fb7c-124">[Continuation 和 ContinuationID 節點](../core/continuation-and-continuationid-nodes.md) </span><span class="sxs-lookup"><span data-stu-id="5fb7c-124">[Continuation and ContinuationID Nodes](../core/continuation-and-continuationid-nodes.md) </span></span>  
 [<span data-ttu-id="5fb7c-125">建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="5fb7c-125">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)