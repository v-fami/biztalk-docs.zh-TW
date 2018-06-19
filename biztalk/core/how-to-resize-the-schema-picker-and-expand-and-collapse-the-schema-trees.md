---
title: 如何調整結構描述選擇器中，以及展開和摺疊結構描述樹狀結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 267ea17d-54fe-4031-a044-719606489f24
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 972be8ca5f412c39e1eb6fa2c81ccd9a21e65a34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254814"
---
# <a name="how-to-resize-the-schema-picker-and-expand-and-collapse-the-schema-trees"></a><span data-ttu-id="32fc5-102">如何調整結構描述選擇器中，以及展開和摺疊結構描述樹狀結構</span><span class="sxs-lookup"><span data-stu-id="32fc5-102">How to resize the schema picker, and expand and collapse the schema trees</span></span>
<span data-ttu-id="32fc5-103">開發 BizTalk 對應時，您往往需要展開和摺疊來源與目的結構描述樹狀結構，以顯示或隱藏各個結構描述節點。</span><span class="sxs-lookup"><span data-stu-id="32fc5-103">When developing BizTalk maps, you are likely to need to expand and collapse the source and destination schema trees to expose or to hide the various schema nodes.</span></span> <span data-ttu-id="32fc5-104">本主題提供逐步指示，調整結構描述選擇器中，並且將展開和摺疊結構描述樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="32fc5-104">This topic provides step-by-step instructions to resize the schema picker, and to expand and collapse the schema tree.</span></span>  

## <a name="resize-the-schema-picker"></a><span data-ttu-id="32fc5-105">調整結構描述選擇器</span><span class="sxs-lookup"><span data-stu-id="32fc5-105">Resize the schema picker</span></span>

<span data-ttu-id="32fc5-106">當您建立對應時，您可以加入來源結構描述和目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="32fc5-106">When you create a map, you add a source schema, and a destination schema.</span></span> <span data-ttu-id="32fc5-107">當您新增或取代結構描述時，BizTalk 型別選擇器 視窗隨即開啟，並選取您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="32fc5-107">When you add or replace a schema, the BizTalk Type Picker window opens, and you select your schema.</span></span> 

<span data-ttu-id="32fc5-108">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您可以調整此型別選擇器 視窗的大小。</span><span class="sxs-lookup"><span data-stu-id="32fc5-108">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can resize this Type Picker window.</span></span> <span data-ttu-id="32fc5-109">這項功能可讓您查看您的結構描述的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="32fc5-109">This feature allows you to see the full name of your schema.</span></span>

1. <span data-ttu-id="32fc5-110">在對應中，選取**開啟目的結構描述**，或**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="32fc5-110">In your map, select **Open Destination Schema**, or **Open Source Schema**.</span></span>
2. <span data-ttu-id="32fc5-111">在**BizTalk 型別選擇器** 視窗中，拖曳右下角，以增加或減少視窗大小。</span><span class="sxs-lookup"><span data-stu-id="32fc5-111">In the **BizTalk Type Picker** window, drag the bottom-right corner to increase or decrease the window size.</span></span>
  
## <a name="expand-all-or-part-of-a-schema-tree"></a><span data-ttu-id="32fc5-112">展開所有或部分結構描述樹狀結構</span><span class="sxs-lookup"><span data-stu-id="32fc5-112">Expand all or part of a schema tree</span></span>  
  
1.  <span data-ttu-id="32fc5-113">選取要完全展開其結構描述樹狀結構的節點。</span><span class="sxs-lookup"><span data-stu-id="32fc5-113">Select the node under which you want to completely expand the schema tree.</span></span>  
  
     <span data-ttu-id="32fc5-114">選取的節點旁必須有加號 (+) 或減號 (-) 圖示。</span><span class="sxs-lookup"><span data-stu-id="32fc5-114">The selected node must be a node with a plus (+) or minus (-) icon next to it.</span></span>  
  
2.  <span data-ttu-id="32fc5-115">在**BizTalk**功能表上，或在該節點的捷徑功能表，按一下 **展開樹狀結構節點**。</span><span class="sxs-lookup"><span data-stu-id="32fc5-115">On the **BizTalk** menu, or on the shortcut menu for that node, click **Expand Tree Node**.</span></span> <span data-ttu-id="32fc5-116">所選節點下的所有節點都會完全展開。</span><span class="sxs-lookup"><span data-stu-id="32fc5-116">All nodes below the selected node are completely expanded.</span></span>  
  
     <span data-ttu-id="32fc5-117">如果所選節點下的結構描述樹狀結構已經完全展開，**展開樹狀結構節點**已停用功能表項目。</span><span class="sxs-lookup"><span data-stu-id="32fc5-117">If the schema tree below the selected node is already completely expanded, the **Expand Tree Node** menu item is disabled.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="32fc5-118">或者，您也可以按 CTRL+M、E 展開結構描述樹狀節點。</span><span class="sxs-lookup"><span data-stu-id="32fc5-118">Alternatively you can press CTRL+M, E to expand the schema tree nodes.</span></span> <span data-ttu-id="32fc5-119">如需鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="32fc5-119">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="32fc5-120">大型且複雜結構描述中，當您按一下**展開樹狀結構節點**節點上，其中包含複雜型別，結構描述中的某些節點可能會維持在摺疊的狀態。</span><span class="sxs-lookup"><span data-stu-id="32fc5-120">In a large and complex schema, when you click **Expand Tree Node** on a node that contains complex types, some nodes in the schema may remain in the collapsed state.</span></span> <span data-ttu-id="32fc5-121">這是因為此遞迴程序只會展開第一個出現的給定複雜型別，</span><span class="sxs-lookup"><span data-stu-id="32fc5-121">This is because the recursive process expands only the first occurrence of a given complex type.</span></span> <span data-ttu-id="32fc5-122">您必須手動展開之後出現的相同型別。</span><span class="sxs-lookup"><span data-stu-id="32fc5-122">You must manually expand later occurrences of the same type.</span></span> <span data-ttu-id="32fc5-123">這個行為的設計目的是要在大型和複雜結構描述中展開節點時，讓效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="32fc5-123">This behavior is designed to optimize performance when expanding nodes in large and complex schemas.</span></span>  
  
## <a name="collapse-all-or-part-of-a-schema-tree"></a><span data-ttu-id="32fc5-124">摺疊全部或部分結構描述樹狀結構</span><span class="sxs-lookup"><span data-stu-id="32fc5-124">Collapse all or part of a schema tree</span></span>  
  
1.  <span data-ttu-id="32fc5-125">選取要完全摺疊其結構描述樹狀結構的節點。</span><span class="sxs-lookup"><span data-stu-id="32fc5-125">Select the node under which you want to completely collapse the schema tree.</span></span>  
  
     <span data-ttu-id="32fc5-126">選取的節點旁必須有加號 (+) 或減號 (-) 圖示。</span><span class="sxs-lookup"><span data-stu-id="32fc5-126">The selected node must be a node with a plus (+) or minus (-) icon next to it.</span></span>  
  
2.  <span data-ttu-id="32fc5-127">在**BizTalk**功能表上，或在該節點的捷徑功能表，按一下 **摺疊樹狀節點**。</span><span class="sxs-lookup"><span data-stu-id="32fc5-127">On the **BizTalk** menu, or on the shortcut menu for that node, click **Collapse Tree Node**.</span></span>  
  
     <span data-ttu-id="32fc5-128">所選節點下的所有節點都會完全摺疊。</span><span class="sxs-lookup"><span data-stu-id="32fc5-128">All nodes below the selected node are completely collapsed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="32fc5-129">或者，您也可以按 CTRL+M、C 摺疊結構描述樹狀節點。</span><span class="sxs-lookup"><span data-stu-id="32fc5-129">Alternatively you can press CTRL+M, C to collapse the schema tree nodes.</span></span> <span data-ttu-id="32fc5-130">如需鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="32fc5-130">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
     <span data-ttu-id="32fc5-131">如果所選節點下的結構描述樹狀結構已經完全摺疊，**摺疊樹狀節點**已停用功能表項目。</span><span class="sxs-lookup"><span data-stu-id="32fc5-131">If the schema tree below the selected node is already collapsed, the **Collapse Tree Node** menu item is disabled.</span></span>  
  
 <span data-ttu-id="32fc5-132">這項作業不會記得個人在所選節點下做出的節點展開和摺疊設定。</span><span class="sxs-lookup"><span data-stu-id="32fc5-132">This operation will not remember the individual expand and collapse settings of the nodes below the selected node.</span></span> <span data-ttu-id="32fc5-133">當您重新展開已摺疊的節點時，先前的設定會遺失，而您必須依逐個節點展開該點下的結構描述樹狀結構，或完全展開。</span><span class="sxs-lookup"><span data-stu-id="32fc5-133">When you re-expand the collapsed node, previous settings are lost, and you must expand the schema tree below that point node-by-node, or expand it entirely.</span></span>  
  
### <a name="expand-a-node"></a><span data-ttu-id="32fc5-134">展開節點</span><span class="sxs-lookup"><span data-stu-id="32fc5-134">Expand a node</span></span>
  
-   <span data-ttu-id="32fc5-135">按一下要展開之節點旁的加號 (+) 圖示。</span><span class="sxs-lookup"><span data-stu-id="32fc5-135">Click the plus (+) icon next to the node you want to expand.</span></span>  
  
 <span data-ttu-id="32fc5-136">就會展開選取的節點。</span><span class="sxs-lookup"><span data-stu-id="32fc5-136">The selected node is expanded.</span></span> <span data-ttu-id="32fc5-137">其底下的節點是展開還是摺疊，視選取的節點當初摺疊的方式，以及先前的展開和摺疊設定而異。</span><span class="sxs-lookup"><span data-stu-id="32fc5-137">Whether or not its descendent nodes are expanded or collapsed depends on how the selected node was collapsed and their previous expand and collapse settings.</span></span>  
  
### <a name="collapse-a-node"></a><span data-ttu-id="32fc5-138">摺疊節點</span><span class="sxs-lookup"><span data-stu-id="32fc5-138">Collapse a node</span></span>
  
-   <span data-ttu-id="32fc5-139">按一下要摺疊之節點旁的減號 (-) 圖示。</span><span class="sxs-lookup"><span data-stu-id="32fc5-139">Click the minus (-) icon next to the node you want to collapse.</span></span>  
  
 <span data-ttu-id="32fc5-140">就會摺疊選取的節點。</span><span class="sxs-lookup"><span data-stu-id="32fc5-140">The selected node is collapsed.</span></span>  
  
 <span data-ttu-id="32fc5-141">這項作業會記得個人在所選節點下做出的節點展開和摺疊設定。</span><span class="sxs-lookup"><span data-stu-id="32fc5-141">This operation will remember the individual expand and collapse settings of the nodes below the selected node.</span></span> <span data-ttu-id="32fc5-142">當您使用加號 (+) 圖示重新展開已摺疊的節點時，先前的個人設定不會遺失，而該節點下的結構描述樹狀目錄會回到先前的狀態。</span><span class="sxs-lookup"><span data-stu-id="32fc5-142">When you re-expand the collapsed node by using the plus (+) icon, the previous individual settings are not lost, and the schema tree below that point returns to its previous state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fc5-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32fc5-143">See Also</span></span>  
 [<span data-ttu-id="32fc5-144">使用 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="32fc5-144">Using BizTalk Mapper</span></span>](../core/using-biztalk-mapper.md)