---
title: 如何設定相互關聯集 |Microsoft 文件
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
ms.openlocfilehash: 52bcb0216fc24e14107c7632df97671b64f2ac1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248166"
---
# <a name="how-to-configure-correlation-sets"></a><span data-ttu-id="d1a7a-102">如何設定相互關聯集</span><span class="sxs-lookup"><span data-stu-id="d1a7a-102">How to Configure Correlation Sets</span></span>
<span data-ttu-id="d1a7a-103">若要設定相互關聯集，您可以選取現有的相互關聯類型、建立新的相互關聯類型，或修改現有的相互關聯類型。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-103">To configure your correlation set, you can select an existing correlation type, create a new correlation type, or modify an existing correlation type.</span></span>  
  
### <a name="to-assign-a-correlation-type-to-a-correlation-set"></a><span data-ttu-id="d1a7a-104">指派相互關聯類型至相互關聯集</span><span class="sxs-lookup"><span data-stu-id="d1a7a-104">To assign a correlation type to a correlation set</span></span>  
  
-   <span data-ttu-id="d1a7a-105">選取現有的相互關聯類型。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-105">Select an existing correlation type.</span></span>  
  
     <span data-ttu-id="d1a7a-106">\-或者-</span><span class="sxs-lookup"><span data-stu-id="d1a7a-106">\- Or -</span></span>  
  
     <span data-ttu-id="d1a7a-107">以滑鼠右鍵按一下新的相互關聯類型，然後選取**設定相互關聯屬性**。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-107">Right-click the new correlation type and select **Configure Correlation Properties**.</span></span>  
  
     <span data-ttu-id="d1a7a-108">\-或者-</span><span class="sxs-lookup"><span data-stu-id="d1a7a-108">\- Or -</span></span>  
  
     <span data-ttu-id="d1a7a-109">按一下省略符號 (**...**) 上的按鈕**相互關聯**中的屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-109">Click the Ellipsis (**...**) button on **Correlation** Properties in the **Properties** window.</span></span>  
  
     <span data-ttu-id="d1a7a-110">**相互關聯屬性**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-110">The **Correlation Properties** dialog box comes up.</span></span> <span data-ttu-id="d1a7a-111">新增您要包含在相互關聯集內的屬性。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-111">Add properties that you want to include in your correlation set.</span></span> <span data-ttu-id="d1a7a-112">如果尚未指派相互關聯類型至相互關聯集，便會建立新的相互關聯類型。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-112">If a correlation type was not already assigned to your correlation set, a new correlation type will be created.</span></span>  
  
 <span data-ttu-id="d1a7a-113">如果相互關聯類型已經存在相互關聯集，而且您加入或移除屬性**相互關聯屬性**對話方塊中，現有的相互關聯類型將予修改。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-113">If a correlation type already exists for your correlation set, and you add or remove properties with the **Correlation Properties** dialog box, the existing correlation type will be modified.</span></span>  
  
#### <a name="to-associate-send-and-receive-activities-with-a-correlation-set"></a><span data-ttu-id="d1a7a-114">建立傳送及接收活動與相互關聯集的關聯</span><span class="sxs-lookup"><span data-stu-id="d1a7a-114">To associate send and receive activities with a correlation set</span></span>  
  
1.  <span data-ttu-id="d1a7a-115">展開**相互關聯集**節點。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-115">Expand the **Correlation Set** node.</span></span>  
  
2.  <span data-ttu-id="d1a7a-116">從下拉式清單中選取傳送或接收活動。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-116">Select a send or receive activity from the drop-down.</span></span>  
  
     <span data-ttu-id="d1a7a-117">\-或者-</span><span class="sxs-lookup"><span data-stu-id="d1a7a-117">\- Or -</span></span>  
  
     <span data-ttu-id="d1a7a-118">選取相互關聯集在**初始化相互關聯集**屬性或**沿用相互關聯集**屬性**屬性**每個視窗**傳送**或**接收**您想要與相互關聯集關聯的圖形。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-118">Select the correlation set in either the **Initializing Correlation Sets** property or the **Following Correlation Sets** property in the **Properties** window for each **Send** or **Receive** shape you want to associate with the correlation set.</span></span>  
  
#### <a name="to-disassociate-send-and-receive-activities-from-a-correlation-set"></a><span data-ttu-id="d1a7a-119">取消傳送及接收活動與相互關聯集的關聯</span><span class="sxs-lookup"><span data-stu-id="d1a7a-119">To disassociate send and receive activities from a correlation set</span></span>  
  
-   <span data-ttu-id="d1a7a-120">在**協調流程檢視**視窗中，視需要展開相互關聯集節點，以滑鼠右鍵按一下您想要移除，然後按一下 的活動**刪除**。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-120">In the **Orchestration View** window, expand the correlation set node if necessary, right-click the activity you want to remove, and then click **Delete**.</span></span>  
  
     <span data-ttu-id="d1a7a-121">\-或者-</span><span class="sxs-lookup"><span data-stu-id="d1a7a-121">\- Or -</span></span>  
  
     <span data-ttu-id="d1a7a-122">清除相互關聯集在**初始化相互關聯集**屬性或**沿用相互關聯集**屬性**屬性**每個視窗**傳送**或**接收**您要取消與相互關聯集的形狀。</span><span class="sxs-lookup"><span data-stu-id="d1a7a-122">Clear the correlation set in either the **Initializing Correlation Sets** property or the **Following Correlation Sets** property in the **Properties** window for each **Send** or **Receive** shape you want to disassociate from the correlation set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a7a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1a7a-123">See Also</span></span>  
 <span data-ttu-id="d1a7a-124">[使用篩選器與接收訊息 」 圖形](../core/using-filters-with-the-receive-message-shape.md) </span><span class="sxs-lookup"><span data-stu-id="d1a7a-124">[Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md) </span></span>  
 [<span data-ttu-id="d1a7a-125">協調流程中使用的相互關聯</span><span class="sxs-lookup"><span data-stu-id="d1a7a-125">Using Correlations in Orchestrations</span></span>](../core/using-correlations-in-orchestrations.md)