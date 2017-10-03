---
title: "如何最佳化連結顯示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a9e16ff-01d3-4b7d-91c4-59d17266ee6d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 689ab4c67bfe8cabc8109c373e899d391fdd56a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-optimize-the-display-of-links"></a><span data-ttu-id="0fa1a-102">如何最佳化連結的顯示</span><span class="sxs-lookup"><span data-stu-id="0fa1a-102">How to Optimize the Display of Links</span></span>
<span data-ttu-id="0fa1a-103">當結構描述很大時，對應中可能包括來源與目的結構描述間的大量連結。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-103">When the schemas are big, your maps might include a large number of links between the source and the destination schemas.</span></span> <span data-ttu-id="0fa1a-104">對應介面中若有許多連結，您會發現難以追蹤您需要使用的連結或物件。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-104">With many links across the map surface, you may find it difficult to track a link or an object you need to work on.</span></span> <span data-ttu-id="0fa1a-105">此外，您不容易追蹤來源結構描述、連結、運算質以及目的結構描述之間的端對端關係。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-105">Also, it can be difficult for you to track an end-to-end relationship between a source schema, the links, the functoids, and the destination schema.</span></span> <span data-ttu-id="0fa1a-106">在 BizTalk 對應工具中，您可以更妥善地管理複雜和大型的結構描述，並讓對應中的連結顯示呈現最佳狀態。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-106">In the BizTalk Mapper, you can better manage complex and large schemas, and bring out an optimized display of links in the map.</span></span> <span data-ttu-id="0fa1a-107">此主題提供如何檢視連結的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-107">This topic provides details about how to view links.</span></span>  
  
 <span data-ttu-id="0fa1a-108">您可以將連結分類如下：</span><span class="sxs-lookup"><span data-stu-id="0fa1a-108">You can categorize the links as follows:</span></span>  
  
-   <span data-ttu-id="0fa1a-109">部分在範圍中</span><span class="sxs-lookup"><span data-stu-id="0fa1a-109">Partially in scope</span></span>  
  
-   <span data-ttu-id="0fa1a-110">完全在範圍中</span><span class="sxs-lookup"><span data-stu-id="0fa1a-110">Completely in scope</span></span>  
  
-   <span data-ttu-id="0fa1a-111">完全不在範圍中</span><span class="sxs-lookup"><span data-stu-id="0fa1a-111">Completely out of scope</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0fa1a-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="0fa1a-112">Prerequisites</span></span>  
 <span data-ttu-id="0fa1a-113">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-113">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="to-view-the-links-partially-in-scope"></a><span data-ttu-id="0fa1a-114">檢視部分在範圍中的連結</span><span class="sxs-lookup"><span data-stu-id="0fa1a-114">To view the links partially in scope</span></span>  
 <span data-ttu-id="0fa1a-115">至少有一端可在格線介面上看見的連結就稱為「部分在範圍中」。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-115">Links that have at least one end visible on the grid surface are called “partially in scope.”</span></span>  
  
 <span data-ttu-id="0fa1a-116">下圖顯示「部分在範圍中」的連結。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-116">The figure below shows a link that is “partially in scope.”</span></span> <span data-ttu-id="0fa1a-117">格線頁上會以虛線的形式顯示這些連結。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-117">These links are shown as dashed lines on the grid page.</span></span>  
  
 <span data-ttu-id="0fa1a-118">在格線介面上，按一下部分可見的連結，然後格線頁就會自動向上/向下移動，以讓該關係進入目前的檢視。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-118">Click the link that is partially visible on the grid surface, and the grid page automatically moves up/down to bring the relationship into the current view.</span></span>  
  
 <span data-ttu-id="0fa1a-119">![部分在範圍中的對應工具連結](../core/media/mapper-partiallyinscope.gif "Mapper_PartiallyInScope")</span><span class="sxs-lookup"><span data-stu-id="0fa1a-119">![Mapper links partially in scope](../core/media/mapper-partiallyinscope.gif "Mapper_PartiallyInScope")</span></span>  
  
## <a name="to-view-the-links-completely-in-scope"></a><span data-ttu-id="0fa1a-120">檢視完全在範圍中的連結</span><span class="sxs-lookup"><span data-stu-id="0fa1a-120">To view the links completely in scope</span></span>  
 <span data-ttu-id="0fa1a-121">兩端 (節點對節點、節點對運算質、運算質對運算質，或運算質對節點) 都可以在格線介面上看見的連結稱為「完全在範圍中」。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-121">A link that has both ends (node to node, node to functoid, functoid-to-functoid, or functoid to node) visible on the grid surface is called “completely in scope.”</span></span>  
  
 <span data-ttu-id="0fa1a-122">下圖顯示 "DataCollection1" 與 "ST01" 之間 (完全在範圍中) 的連結。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-122">The figure below shows a link between “DataCollection1” and “ST01” that is completely in scope.</span></span>  
  
 <span data-ttu-id="0fa1a-123">按一下該連結，就會選取從來源節點至目標節點的關係。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-123">Click the link, and the relationship from source node to target node is selected.</span></span>  
  
 <span data-ttu-id="0fa1a-124">![完全在範圍中的對應工具連結](../core/media/mapper-completelyinscope.gif "Mapper_CompletelyInScope")</span><span class="sxs-lookup"><span data-stu-id="0fa1a-124">![Mapper links completely in scope](../core/media/mapper-completelyinscope.gif "Mapper_CompletelyInScope")</span></span>  
  
## <a name="to-view-the-links-completely-out-of-scope"></a><span data-ttu-id="0fa1a-125">檢視完全不在範圍中的連結</span><span class="sxs-lookup"><span data-stu-id="0fa1a-125">To view the links completely out of scope</span></span>  
 <span data-ttu-id="0fa1a-126">在目前的對應檢視中，看不到其任一端結束點的連結，稱為「完全不在範圍中」。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-126">A link that has neither of its end points visible in the current map view is called “completely out of scope.”</span></span>  
  
 <span data-ttu-id="0fa1a-127">下圖顯示「完全不在範圍中」的連結。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-127">The figure below shows a link that is completely out of scope.</span></span>  
  
 <span data-ttu-id="0fa1a-128">如果您不想顯示這些連結，在地圖上的介面 （因為不連結會顯示），您可以選擇將其關閉，依序按一下![顯示所有連結](../core/media/mapper-showhideoutscopelinks.gif "Mapper_ShowHideOutScopeLinks")在對應工具公用程式功能區。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-128">If you do not want to display these links on the map surface (because none of the links are visible), you may choose to turn them off by clicking ![Show all links](../core/media/mapper-showhideoutscopelinks.gif "Mapper_ShowHideOutScopeLinks") on the Mapper utility ribbon.</span></span> <span data-ttu-id="0fa1a-129">這樣可以降低格線檢視上可看見的連結數量。</span><span class="sxs-lookup"><span data-stu-id="0fa1a-129">This reduces the amount of links that are visible on the grid view.</span></span>  
  
 <span data-ttu-id="0fa1a-130">![完全超出範圍的對應工具連結](../core/media/mapper-completelyoutscope.gif "Mapper_CompletelyOutScope")</span><span class="sxs-lookup"><span data-stu-id="0fa1a-130">![Mapper links completely out of scope](../core/media/mapper-completelyoutscope.gif "Mapper_CompletelyOutScope")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fa1a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fa1a-131">See Also</span></span>  
 [<span data-ttu-id="0fa1a-132">使用 BizTalk 對應工具中的增強的功能</span><span class="sxs-lookup"><span data-stu-id="0fa1a-132">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)