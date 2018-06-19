---
title: 如何最佳化結構描述樹狀結構檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab4ad6b5-5bbd-443b-9041-6cddf9d64735
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aeeddd0893b80c1c7b37b2d0ee5f9f6cd68849d6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22255342"
---
# <a name="how-to-optimize-the-schema-tree-view"></a><span data-ttu-id="1751b-102">如何最佳化結構描述樹狀結構檢視</span><span class="sxs-lookup"><span data-stu-id="1751b-102">How to Optimize the Schema Tree View</span></span>
<span data-ttu-id="1751b-103">您可以使用 **相關性檢視** BizTalk 對應工具最佳化來源和/或目標結構描述樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="1751b-103">You can use the **Relevance View** in BizTalk Mapper to optimize the source and/or target schema trees.</span></span> <span data-ttu-id="1751b-104">本主題提供如何執行此作業的指示。</span><span class="sxs-lookup"><span data-stu-id="1751b-104">This topic provides instructions about how to perform the operation.</span></span>  
  
 <span data-ttu-id="1751b-105">相關性檢視使用同層級結合 (Sibling Coalescence) 將不相關的結構描述項目摺疊起來，以提供更簡潔的結構描述檢視。</span><span class="sxs-lookup"><span data-stu-id="1751b-105">The relevance view uses sibling coalescence to collapse the non-relevant schema elements to provide a more compact view of the schema.</span></span> <span data-ttu-id="1751b-106">這樣可進一步減少捲動需求，協助您將焦點放在使用結構描述與對應時的需求。</span><span class="sxs-lookup"><span data-stu-id="1751b-106">This further reduces the need of scrolling and helps you focus on your requirement for using schemas and maps.</span></span>  
  
 <span data-ttu-id="1751b-107">下圖顯示相關性檢視關閉時的結構描述。</span><span class="sxs-lookup"><span data-stu-id="1751b-107">The following figure shows a schema when the relevance view is turned OFF.</span></span> <span data-ttu-id="1751b-108">不論節點是否參與了任何關係，結構描述窗格都會顯示所有的節點。</span><span class="sxs-lookup"><span data-stu-id="1751b-108">The schema pane displays all nodes, irrespective of whether the nodes are part of any relationship or not.</span></span>  
  
 <span data-ttu-id="1751b-109">![結構描述相關性檢視關閉時](../core/media/off-schema-relevance-view.gif "Off_Schema_Relevance_View")</span><span class="sxs-lookup"><span data-stu-id="1751b-109">![Schema when relevance view is switched off](../core/media/off-schema-relevance-view.gif "Off_Schema_Relevance_View")</span></span>  
  
 <span data-ttu-id="1751b-110">按一下![切換至相關性檢視](../core/media/mapper-intellitree.gif "Mapper_IntelliTree")開啟相關性檢視對應工具公用程式功能區上的圖示。</span><span class="sxs-lookup"><span data-stu-id="1751b-110">Click the ![Switch to relevance view](../core/media/mapper-intellitree.gif "Mapper_IntelliTree") icon on the Mapper utility ribbon to turn the relevance view ON.</span></span> <span data-ttu-id="1751b-111">您可以切換到來源與 (或) 目標結構描述的相關性檢視，只要按一下來源來源與 (或) 目標結構描述的相關圖示即可。</span><span class="sxs-lookup"><span data-stu-id="1751b-111">You can switch to relevance view for any one or both the source schema and the target schema; click the respective icons for source and target schemas.</span></span>  
  
 <span data-ttu-id="1751b-112">切換到結構描述的相關性檢視時：</span><span class="sxs-lookup"><span data-stu-id="1751b-112">When you switch to relevance view for a schema:</span></span>  
  
-   <span data-ttu-id="1751b-113">所有其本身或其子欄位項目沒有相關連結的記錄項目都會呈現摺疊狀態。</span><span class="sxs-lookup"><span data-stu-id="1751b-113">All the record elements that do not have any links either for them or their child field elements are collapsed.</span></span>  
  
-   <span data-ttu-id="1751b-114">沒有任何連結的所有後續節點會結合起來，並會取代![聯合隱藏的節點](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On")圖示。</span><span class="sxs-lookup"><span data-stu-id="1751b-114">All successive nodes that do not have any links are coalesced and are replaced by the ![Coalesced nodes hidden](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") icon.</span></span> <span data-ttu-id="1751b-115">BizTalk 對應工具會尋找至少兩個可以結合的不相關連續節點。</span><span class="sxs-lookup"><span data-stu-id="1751b-115">The BizTalk Mapper looks for a minimum of two successive non-relevant nodes that can be coalesced.</span></span> <span data-ttu-id="1751b-116">您可以將滑鼠移到圖示上以檢視結合節點的清單。</span><span class="sxs-lookup"><span data-stu-id="1751b-116">You can move the mouse over the icon to view the list of coalesced nodes.</span></span> <span data-ttu-id="1751b-117">請注意，infotip 只會列出前三個結合節點的名稱，即使事實上還有其他結合節點也是如此。</span><span class="sxs-lookup"><span data-stu-id="1751b-117">Note that the infotip will only list the names of the first three coalesced nodes, even if there are more coalesced nodes.</span></span> <span data-ttu-id="1751b-118">按一下即可檢視所有節點![聯合隱藏的節點](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On")圖示。</span><span class="sxs-lookup"><span data-stu-id="1751b-118">You can view all the nodes by clicking the ![Coalesced nodes hidden](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") icon.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1751b-119">如需 infotip 的詳細資訊，請參閱[如何檢視資訊提示和工具提示](../core/how-to-view-infotip-and-tooltip.md)。</span><span class="sxs-lookup"><span data-stu-id="1751b-119">For more information about infotip, see [How to View Infotip and Tooltip](../core/how-to-view-infotip-and-tooltip.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1751b-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="1751b-120">Prerequisites</span></span>  
 <span data-ttu-id="1751b-121">此作業需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="1751b-121">This operation requires that BizTalk Mapper is running.</span></span>  
  
## <a name="to-optimize-the-schema-tree-view"></a><span data-ttu-id="1751b-122">若要最佳化結構描述樹狀結構</span><span class="sxs-lookup"><span data-stu-id="1751b-122">To optimize the schema tree view</span></span>  
 <span data-ttu-id="1751b-123">對應工具公用程式功能區中，開啟來源和 （或） 目標結構描述的相關性檢視，即可分別![切換至相關性檢視](../core/media/mapper-intellitree.gif "Mapper_IntelliTree")圖示。</span><span class="sxs-lookup"><span data-stu-id="1751b-123">On the Mapper utility ribbon, turn ON the relevance view for source and/or target schemas by clicking the respective ![Switch to relevance view](../core/media/mapper-intellitree.gif "Mapper_IntelliTree") icons.</span></span> <span data-ttu-id="1751b-124">下圖顯示相關性檢視開啟時的同一個結構描述。</span><span class="sxs-lookup"><span data-stu-id="1751b-124">The following figure shows the same schema when the relevance view is turned ON.</span></span> <span data-ttu-id="1751b-125">所有不相關的節點會以取代![聯合隱藏的節點](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On")圖示，以提供更簡潔的結構描述檢視。</span><span class="sxs-lookup"><span data-stu-id="1751b-125">All the non-relevant nodes are replaced by the ![Coalesced nodes hidden](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") icon to provide a more compact view of the schema.</span></span>  
  
 <span data-ttu-id="1751b-126">![結構描述相關性檢視時 ON](../core/media/on-schema.gif "On_schema")</span><span class="sxs-lookup"><span data-stu-id="1751b-126">![Schema when relevance view is ON](../core/media/on-schema.gif "On_schema")</span></span>  
  
 <span data-ttu-id="1751b-127">當您展開結合的節點，在來源及/或目的結構描述中![聯合隱藏的節點](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On")變為![聯合節點顯示](../core/media/switchoff-mapper-coalesence.jpg "SwitchOff_Mapper_Coalesence")圖示。</span><span class="sxs-lookup"><span data-stu-id="1751b-127">When you expand the coalesced nodes in source and/or destination schemas, the ![Coalesced nodes hidden](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") changes to ![Coalesced nodes shown](../core/media/switchoff-mapper-coalesence.jpg "SwitchOff_Mapper_Coalesence") icon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1751b-128">您可以按下 CTRL+M、CTRL+E 或 CTRL+M、CTRL+C，分別展開或摺疊來源結構描述中的樹狀結構節點。</span><span class="sxs-lookup"><span data-stu-id="1751b-128">You can press CTRL+M, CTRL+E or CTRL+M, CTRL+C to expand or collapse the tree nodes in source schema respectively.</span></span> <span data-ttu-id="1751b-129">同樣地，您可以按下 CTRL+M、CTRL+E 或 CTRL+M、CTRL+C，分別展開或摺疊目的結構描述中的樹狀結構節點。</span><span class="sxs-lookup"><span data-stu-id="1751b-129">Similarly, you can press CTRL+M, CTRL+E or CTRL+M, CTRL+C to expand or collapse the tree nodes in destination schema respectively.</span></span> <span data-ttu-id="1751b-130">您也可以分別按下 Ctrl+M、Ctrl+H 或 Ctrl+M、Ctrl+D，分別進行來源或目標結合。</span><span class="sxs-lookup"><span data-stu-id="1751b-130">You can also press Ctrl+M, Ctrl+H or Ctrl+M, Ctrl+D for source or target coalescing respectively.</span></span> <span data-ttu-id="1751b-131">如需對應工具鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="1751b-131">For a list of Mapper keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1751b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1751b-132">See Also</span></span>  
 [<span data-ttu-id="1751b-133">使用 BizTalk 對應工具中的增強的功能</span><span class="sxs-lookup"><span data-stu-id="1751b-133">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)