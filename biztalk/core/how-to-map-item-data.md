---
title: "如何對應項目資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data extraction
- orchestrations, data extraction
- orchestrations, tracking profiles
- tracking profiles, orchestrations
- tracking profiles, data extraction
ms.assetid: ae8b395e-152a-4e08-af31-3c9276f52711
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efdfd722e1610be02c06dd6e2a9597e13c0f1e37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-item-data"></a><span data-ttu-id="0987b-102">如何對應項目資料</span><span class="sxs-lookup"><span data-stu-id="0987b-102">How to Map Item Data</span></span>
<span data-ttu-id="0987b-103">對應項目資料，可以定義協調流程中的資料擷取。</span><span class="sxs-lookup"><span data-stu-id="0987b-103">You map item data to define the data extraction from an orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0987b-104">在建立追蹤設定檔時，請務必對應與活動項目相容的資料類型值。</span><span class="sxs-lookup"><span data-stu-id="0987b-104">You must be certain to map data type values that are compatible with the activity items when creating tracking profiles.</span></span> <span data-ttu-id="0987b-105">如果資料類型不相容，您將會收到 BAM 執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="0987b-105">If the data types are not compatible you will receive a BAM runtime error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0987b-106">在對應如日期/時間戳記等里程碑時，要對應的資料必須符合 SQL 字串的日期時間戳記表示法。</span><span class="sxs-lookup"><span data-stu-id="0987b-106">When mapping milestones, such as Date/Time stamps, the data being mapped must conform to the SQL string representation of a date time stamp.</span></span> <span data-ttu-id="0987b-107">YYYY-MM-DDTHH:MM:SS.mmm-HH:MM 這種 XML DateTime 格式的 DateTime 資料則不受支援。</span><span class="sxs-lookup"><span data-stu-id="0987b-107">DateTime data in the XML DateTime format that is formatted in the following manner, YYYY-MM-DDTHH:MM:SS.mmm-HH:MM, is not supported.</span></span>  
>   
>  <span data-ttu-id="0987b-108">例如，這個日期字串 1999-05-31T13:20:00.000-05:00 便不受支援。</span><span class="sxs-lookup"><span data-stu-id="0987b-108">For example, the following date string, 1999-05-31T13:20:00.000-05:00, is not supported.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0987b-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="0987b-109">Prerequisites</span></span>  
 <span data-ttu-id="0987b-110">已部署您將連接的 BAM 活動定義和協調流程。</span><span class="sxs-lookup"><span data-stu-id="0987b-110">Deployed BAM activity definitions and orchestrations that you will connect.</span></span>  
  
### <a name="how-to-map-item-data"></a><span data-ttu-id="0987b-111">如何對應項目資料</span><span class="sxs-lookup"><span data-stu-id="0987b-111">How to map item data</span></span>  
  
1.  <span data-ttu-id="0987b-112">開啟現有的追蹤設定檔或建立新的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="0987b-112">Open an existing tracking profile or create a new tracking profile.</span></span> <span data-ttu-id="0987b-113">如需有關如何建立追蹤設定檔的詳細資訊，請參閱[如何建立追蹤設定檔](../core/how-to-create-a-tracking-profile.md)。</span><span class="sxs-lookup"><span data-stu-id="0987b-113">For more information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).</span></span>  
  
2.  <span data-ttu-id="0987b-114">在此實例中，會匯入名為 LoanProcessBamDef 的活動定義，</span><span class="sxs-lookup"><span data-stu-id="0987b-114">In the scenario, an activity definition called LoanProcessBamDef is imported.</span></span> <span data-ttu-id="0987b-115">它包含**LoanProcess**活動節點，並且以客戶的**SSN**做為 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="0987b-115">It contains the **LoanProcess** activity node, with a customer's **SSN** as an ActivityID.</span></span> <span data-ttu-id="0987b-116">如需詳細資訊，請參閱[Activity 和 ActivityID 節點](../core/activity-and-activityid-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="0987b-116">For more information, see [Activity and ActivityID Nodes](../core/activity-and-activityid-nodes.md).</span></span>  
  
3.  <span data-ttu-id="0987b-117">請確認每個活動都有可以追蹤的 ActivityID 或 ContinuationID 資料項目，例如客戶的 SSN。</span><span class="sxs-lookup"><span data-stu-id="0987b-117">Ensure that every activity has an ActivityID or a ContinuationID data item, such as customer SSN, to track.</span></span>  
  
4.  <span data-ttu-id="0987b-118">將協調流程動作對應到適當的商務事件資料夾，以指示要追蹤的事件。例如，在貸款處理實例中下列項目，和其他項目，拖曳到下**LoanProcess**活動資料夾：</span><span class="sxs-lookup"><span data-stu-id="0987b-118">Map orchestration actions to the appropriate business events folder to indicate the event to track. For example, in a loan processing scenario the following items, among others, would be dragged under the **LoanProcess** activity folder:</span></span>  
  
    -   <span data-ttu-id="0987b-119">**LoanApplicationReceived**</span><span class="sxs-lookup"><span data-stu-id="0987b-119">**LoanApplicationReceived**</span></span>  
  
    -   <span data-ttu-id="0987b-120">**CreditHistoryRequest**</span><span class="sxs-lookup"><span data-stu-id="0987b-120">**CreditHistoryRequest**</span></span>  
  
    -   <span data-ttu-id="0987b-121">**CreditHistoryResponse**</span><span class="sxs-lookup"><span data-stu-id="0987b-121">**CreditHistoryResponse**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0987b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0987b-122">See Also</span></span>  
 <span data-ttu-id="0987b-123">[資料項目節點](../core/data-item-nodes.md) </span><span class="sxs-lookup"><span data-stu-id="0987b-123">[Data Item Nodes](../core/data-item-nodes.md) </span></span>  
 [<span data-ttu-id="0987b-124">建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="0987b-124">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)