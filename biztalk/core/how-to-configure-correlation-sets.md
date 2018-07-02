---
title: 如何設定相互關聯集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- correlation sets, send activities
- correlation sets, assigning correlation types
- correlation types, correlation sets
- correlation sets, receive activities
- configuring, correlation sets
- correlation sets, configuring
- correlation types, assigning
ms.assetid: 060bf2ba-c173-4dca-a8c4-4c5341e5ceaa
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51c56d7f319023bb0379050452253c65634929c0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968855"
---
# <a name="how-to-configure-correlation-sets"></a><span data-ttu-id="ff48a-102">如何設定相互關聯集</span><span class="sxs-lookup"><span data-stu-id="ff48a-102">How to Configure Correlation Sets</span></span>
<span data-ttu-id="ff48a-103">若要設定相互關聯集，您可以選取現有的相互關聯類型、建立新的相互關聯類型，或修改現有的相互關聯類型。</span><span class="sxs-lookup"><span data-stu-id="ff48a-103">To configure your correlation set, you can select an existing correlation type, create a new correlation type, or modify an existing correlation type.</span></span>  
  
### <a name="to-assign-a-correlation-type-to-a-correlation-set"></a><span data-ttu-id="ff48a-104">指派相互關聯類型至相互關聯集</span><span class="sxs-lookup"><span data-stu-id="ff48a-104">To assign a correlation type to a correlation set</span></span>  
  
- <span data-ttu-id="ff48a-105">選取現有的相互關聯類型。</span><span class="sxs-lookup"><span data-stu-id="ff48a-105">Select an existing correlation type.</span></span>  
  
   <span data-ttu-id="ff48a-106">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="ff48a-106">\- Or -</span></span>  
  
   <span data-ttu-id="ff48a-107">以滑鼠右鍵按一下新的相互關聯類型，然後選取**設定相互關聯屬性**。</span><span class="sxs-lookup"><span data-stu-id="ff48a-107">Right-click the new correlation type and select **Configure Correlation Properties**.</span></span>  
  
   <span data-ttu-id="ff48a-108">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="ff48a-108">\- Or -</span></span>  
  
   <span data-ttu-id="ff48a-109">按一下省略符號 (**...**) 按鈕**相互關聯**中的屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="ff48a-109">Click the Ellipsis (**...**) button on **Correlation** Properties in the **Properties** window.</span></span>  
  
   <span data-ttu-id="ff48a-110">**相互關聯屬性**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ff48a-110">The **Correlation Properties** dialog box comes up.</span></span> <span data-ttu-id="ff48a-111">新增您要包含在相互關聯集內的屬性。</span><span class="sxs-lookup"><span data-stu-id="ff48a-111">Add properties that you want to include in your correlation set.</span></span> <span data-ttu-id="ff48a-112">如果尚未指派相互關聯類型至相互關聯集，便會建立新的相互關聯類型。</span><span class="sxs-lookup"><span data-stu-id="ff48a-112">If a correlation type was not already assigned to your correlation set, a new correlation type will be created.</span></span>  
  
  <span data-ttu-id="ff48a-113">如果相互關聯類型已經存在相互關聯集，而且您新增或移除的屬性**相互關聯屬性**對話方塊中，現有的相互關聯類型將予修改。</span><span class="sxs-lookup"><span data-stu-id="ff48a-113">If a correlation type already exists for your correlation set, and you add or remove properties with the **Correlation Properties** dialog box, the existing correlation type will be modified.</span></span>  
  
#### <a name="to-associate-send-and-receive-activities-with-a-correlation-set"></a><span data-ttu-id="ff48a-114">建立傳送及接收活動與相互關聯集的關聯</span><span class="sxs-lookup"><span data-stu-id="ff48a-114">To associate send and receive activities with a correlation set</span></span>  
  
1.  <span data-ttu-id="ff48a-115">依序展開**相互關聯集**節點。</span><span class="sxs-lookup"><span data-stu-id="ff48a-115">Expand the **Correlation Set** node.</span></span>  
  
2.  <span data-ttu-id="ff48a-116">從下拉式清單中選取傳送或接收活動。</span><span class="sxs-lookup"><span data-stu-id="ff48a-116">Select a send or receive activity from the drop-down.</span></span>  
  
     <span data-ttu-id="ff48a-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="ff48a-117">\- Or -</span></span>  
  
     <span data-ttu-id="ff48a-118">選取相互關聯集合中**初始相互關聯集**屬性或**沿用相互關聯集**中的屬性**屬性**每個視窗**傳送**或是**接收**您想要相互關聯集相關聯的圖形。</span><span class="sxs-lookup"><span data-stu-id="ff48a-118">Select the correlation set in either the **Initializing Correlation Sets** property or the **Following Correlation Sets** property in the **Properties** window for each **Send** or **Receive** shape you want to associate with the correlation set.</span></span>  
  
#### <a name="to-disassociate-send-and-receive-activities-from-a-correlation-set"></a><span data-ttu-id="ff48a-119">取消傳送及接收活動與相互關聯集的關聯</span><span class="sxs-lookup"><span data-stu-id="ff48a-119">To disassociate send and receive activities from a correlation set</span></span>  
  
-   <span data-ttu-id="ff48a-120">在 **協調流程檢視**視窗中，視需要展開相互關聯集節點，以滑鼠右鍵按一下您想要移除此項目，然後按一下 的活動**刪除**。</span><span class="sxs-lookup"><span data-stu-id="ff48a-120">In the **Orchestration View** window, expand the correlation set node if necessary, right-click the activity you want to remove, and then click **Delete**.</span></span>  
  
     <span data-ttu-id="ff48a-121">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="ff48a-121">\- Or -</span></span>  
  
     <span data-ttu-id="ff48a-122">清除 相互關聯集合中**初始相互關聯集**屬性或**沿用相互關聯集**中的屬性**屬性**視窗中的每個**傳送**或是**接收**您想要取消與相互關聯集的形狀。</span><span class="sxs-lookup"><span data-stu-id="ff48a-122">Clear the correlation set in either the **Initializing Correlation Sets** property or the **Following Correlation Sets** property in the **Properties** window for each **Send** or **Receive** shape you want to disassociate from the correlation set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff48a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff48a-123">See Also</span></span>  
 <span data-ttu-id="ff48a-124">[與接收訊息圖形使用篩選器](../core/using-filters-with-the-receive-message-shape.md) </span><span class="sxs-lookup"><span data-stu-id="ff48a-124">[Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md) </span></span>  
 [<span data-ttu-id="ff48a-125">在協調流程中使用相互關聯</span><span class="sxs-lookup"><span data-stu-id="ff48a-125">Using Correlations in Orchestrations</span></span>](../core/using-correlations-in-orchestrations.md)