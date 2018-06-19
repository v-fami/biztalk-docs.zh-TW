---
title: 如何複製、 剪下及貼上連結與運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80b4792a-5ff6-4603-96cd-b3d3d530c12f
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5eec0ddc164af936e1c3739e4da167753a6e58c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250366"
---
# <a name="how-to-copy-cut-and-paste-links-and-functoids"></a><span data-ttu-id="747ea-102">如何複製、剪下與貼上連結和運算質</span><span class="sxs-lookup"><span data-stu-id="747ea-102">How to Copy, Cut, and Paste Links and Functoids</span></span>
<span data-ttu-id="747ea-103">「BizTalk 對應工具」中的複製/剪下/貼上功能可讓人重複使用關係。</span><span class="sxs-lookup"><span data-stu-id="747ea-103">The copy/cut/paste feature in the BizTalk Mapper enables the reusability of a relationship.</span></span> <span data-ttu-id="747ea-104">本主題提供在對應中複製、剪下及貼上運算質和/或連結的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="747ea-104">This topic provides step-by-step instructions to copy, cut, and paste functoids and/or links in a map.</span></span>  
  
 <span data-ttu-id="747ea-105">當您要重複使用一組運算質和/或連結時，可以使用複製/貼上功能。</span><span class="sxs-lookup"><span data-stu-id="747ea-105">You can use the copy/paste feature when you want to reuse a set of functoids and/or links.</span></span> <span data-ttu-id="747ea-106">此外，當您要將選取範圍從現有位置移除並移到新位置時，可以使用剪下/貼上功能。</span><span class="sxs-lookup"><span data-stu-id="747ea-106">And, when you want to remove the selection from the existing location and move it to a new location, you can use the cut/paste feature.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="747ea-107">您是否覺得剪下/貼上功能與移動功能很類似？</span><span class="sxs-lookup"><span data-stu-id="747ea-107">Do you feel cut/paste feature and the move feature are similar?</span></span> <span data-ttu-id="747ea-108">有一個地方不同。</span><span class="sxs-lookup"><span data-stu-id="747ea-108">There is a difference.</span></span> <span data-ttu-id="747ea-109">當您選取剪下時，只有選取範圍中的運算質和/或連結會自來源格線頁中移除。</span><span class="sxs-lookup"><span data-stu-id="747ea-109">When you select cut, only the functoids and/or links in your selection are removed from the source grid page.</span></span> <span data-ttu-id="747ea-110">但是當您選取移動時，關係中的所有運算質和連結 (不論選取範圍為何) 都會依照遞迴結構自來源格線頁中移除。</span><span class="sxs-lookup"><span data-stu-id="747ea-110">But, when you select move, all the functoids and links in the relationship (irrespective of the selection), recursively, are removed from the source grid page.</span></span> <span data-ttu-id="747ea-111">如需移動關係的詳細資訊，請參閱[如何移動關係格線頁之間](../core/how-to-move-a-relationship-between-grid-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="747ea-111">For more information about moving a relationship, see [How to Move a Relationship Between Grid Pages](../core/how-to-move-a-relationship-between-grid-pages.md).</span></span>  
  
 <span data-ttu-id="747ea-112">當您複製/剪下一組運算質和/或連結時，會保留與該集合關聯的運算質、標籤、註解和常數值 (以及正確的預留位置)。</span><span class="sxs-lookup"><span data-stu-id="747ea-112">When you copy/cut a set of functoids and/or links, the functoids, labels, comments, and the constant values (along with the correct place holders) associated with that set are retained.</span></span>  
  
 <span data-ttu-id="747ea-113">您只可以複製/剪下這些對應項目：</span><span class="sxs-lookup"><span data-stu-id="747ea-113">You can copy/cut only these map items:</span></span>  
  
-   <span data-ttu-id="747ea-114">從來源到目標結構描述的連結。</span><span class="sxs-lookup"><span data-stu-id="747ea-114">Link from source to target schema.</span></span>  
  
-   <span data-ttu-id="747ea-115">從運算質到結構描述節點的連結 (只有在同時選取「運算質」和連結時)。</span><span class="sxs-lookup"><span data-stu-id="747ea-115">Link from functoid to schema node, if and only if the “functoid” is also selected along with the link.</span></span>  
  
-   <span data-ttu-id="747ea-116">從運算質到運算質的連結 (只有在同時選取兩個運算質和之間的連結時)。</span><span class="sxs-lookup"><span data-stu-id="747ea-116">Link from functoid to functoid, if and only if both the functoids are selected along with the link.</span></span>  
  
 <span data-ttu-id="747ea-117">您可以從下列位置複製/剪下運算質和/或連結：</span><span class="sxs-lookup"><span data-stu-id="747ea-117">You can copy/cut functoids and/or links from:</span></span>  
  
-   <span data-ttu-id="747ea-118">同一個對應格線頁內</span><span class="sxs-lookup"><span data-stu-id="747ea-118">Within the same grid page of a map</span></span>  
  
-   <span data-ttu-id="747ea-119">同一個對應中的不同格線頁之間</span><span class="sxs-lookup"><span data-stu-id="747ea-119">One grid page to the other in the same map</span></span>  
  
-   <span data-ttu-id="747ea-120">同一個 Visual Studio 執行個體中的不同對應之間</span><span class="sxs-lookup"><span data-stu-id="747ea-120">One map to the other in the same instance of Visual Studio</span></span>  
  
-   <span data-ttu-id="747ea-121">不同的 Visual Studio 執行個體之間</span><span class="sxs-lookup"><span data-stu-id="747ea-121">Across different instances of Visual Studio</span></span>  
  
 <span data-ttu-id="747ea-122">您可以復原或重做剪下與貼上作業。</span><span class="sxs-lookup"><span data-stu-id="747ea-122">You can undo or redo the cut and paste operations.</span></span> <span data-ttu-id="747ea-123">如需詳細資訊，請參閱[如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="747ea-123">For more information, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).</span></span>  
  
 <span data-ttu-id="747ea-124">此外，在貼上連結時，您還必須考慮下列幾點：</span><span class="sxs-lookup"><span data-stu-id="747ea-124">In addition to this, you must consider the following points while pasting links:</span></span>  
  
-   <span data-ttu-id="747ea-125">若要貼上來源與目標結構描述之間的連結，目前對應 (要貼上連結的地方) 必須包含來源節點和目標節點，而且這個來源節點和目標節點的 XPath 必須與所貼連結之來源節點和目標節點的 XPath 相同。</span><span class="sxs-lookup"><span data-stu-id="747ea-125">A link between the source and target schema can be pasted if and only if the current map, where the link is being pasted, contains a source node as well as a target node whose XPath is identical to the XPath of the source and target nodes for the link being pasted.</span></span>  
  
-   <span data-ttu-id="747ea-126">若要貼上來源與目標結構描述之間的連結，上述來源與目標節點之間必須沒有現有連結。</span><span class="sxs-lookup"><span data-stu-id="747ea-126">A link between the source and target schema can be pasted if and only if there is no existing link between the aforesaid source and target nodes.</span></span>  
  
-   <span data-ttu-id="747ea-127">若要貼上從運算質至目標結構描述的連結，目標節點的 XPath 必須與所貼連結之目標節點的 XPath 相同。</span><span class="sxs-lookup"><span data-stu-id="747ea-127">A link from a functoid to target schema can be pasted if and only if there exists a target node whose XPath is same as the XPath of the target node of the link being pasted.</span></span>  
  
-   <span data-ttu-id="747ea-128">若要貼上從來源結構描述至運算質的連結，來源節點的 XPath 必須與所貼連結之來源節點的 XPath 相同。</span><span class="sxs-lookup"><span data-stu-id="747ea-128">A link from a source schema to a functoid can be pasted if and only if there exists a source node whose XPath is same as the XPath of the source node of the link being pasted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="747ea-129">當您選取多個項目 (連結和/或運算質) 以至於無法剪下/複製部分項目時，則在執行剪下/複製命令時，Visual Studio 中的狀態列會顯示「無法剪下/複製部分選取的項目」警告訊息。</span><span class="sxs-lookup"><span data-stu-id="747ea-129">When you select multiple items (links and/or functoids) such that some of them cannot be cut/copied, then on executing the cut/copy command, the status bar in Visual Studio displays a warning message “Some of the selected items could not be cut/copied.”</span></span> <span data-ttu-id="747ea-130">訊息也會顯示相關的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="747ea-130">The message also displays relevant details.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="747ea-131">必要條件</span><span class="sxs-lookup"><span data-stu-id="747ea-131">Prerequisites</span></span>  
 <span data-ttu-id="747ea-132">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="747ea-132">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-copy-and-paste-a-relationship"></a><span data-ttu-id="747ea-133">若要複製並貼上關係</span><span class="sxs-lookup"><span data-stu-id="747ea-133">To copy and paste a relationship</span></span>  
  
1.  <span data-ttu-id="747ea-134">在 [方案總管] 中開啟 BizTalk 專案，然後按兩下對應以在 BizTalk 對應工具中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="747ea-134">In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.</span></span>  
  
2.  <span data-ttu-id="747ea-135">選取運算質和/或您要複製的連結。</span><span class="sxs-lookup"><span data-stu-id="747ea-135">Select the functoids and/or links you want to copy.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="747ea-136">您可以選擇按住 CTRL 鍵，然後選取想要的運算質和/或連結，或者是將滑鼠拖曳過這些連結，以形成矩形選取範圍。</span><span class="sxs-lookup"><span data-stu-id="747ea-136">You can select either by holding down the CTRL key, and then selecting the desired functoids and/or links or by dragging and dropping the mouse across the links to form a rectangular selection.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="747ea-137">您可以使用「功能區選取」作業來選取多個連結和 (或) 運算質。</span><span class="sxs-lookup"><span data-stu-id="747ea-137">You can use the “ribbon select” operation to select multiple link(s) and/or functoid(s).</span></span> <span data-ttu-id="747ea-138">如需詳細資訊，請參閱[如何選取多個連結和運算質](../core/how-to-select-multiple-links-and-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="747ea-138">For more information, see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).</span></span>  
  
3.  <span data-ttu-id="747ea-139">以滑鼠右鍵按一下選取範圍。</span><span class="sxs-lookup"><span data-stu-id="747ea-139">Right-click the selection.</span></span> <span data-ttu-id="747ea-140">然後按一下 **複製**。</span><span class="sxs-lookup"><span data-stu-id="747ea-140">and then click **Copy**.</span></span> <span data-ttu-id="747ea-141">或者，您可以按鍵盤上的 CTRL+C。</span><span class="sxs-lookup"><span data-stu-id="747ea-141">Alternatively, you can press CTRL+C on the keyboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="747ea-142">如需鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="747ea-142">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
4.  <span data-ttu-id="747ea-143">將游標放在您想貼上選取範圍的位置。</span><span class="sxs-lookup"><span data-stu-id="747ea-143">Place the cursor where you wish to paste the selection.</span></span>  
  
5.  <span data-ttu-id="747ea-144">在格線頁中，按一下滑鼠右鍵，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="747ea-144">Right-click on the grid page, and then click **Paste**.</span></span> <span data-ttu-id="747ea-145">或者，您可以選取並按鍵盤上的 CTRL+V。</span><span class="sxs-lookup"><span data-stu-id="747ea-145">Alternatively, you can select and press CTRL+V on the keyboard.</span></span> <span data-ttu-id="747ea-146">選取範圍的複本會出現在新的位置。</span><span class="sxs-lookup"><span data-stu-id="747ea-146">A copy of the selection appears at the new location.</span></span>  
  
### <a name="to-cut-and-paste-a-relationship"></a><span data-ttu-id="747ea-147">若要剪下並貼上關係</span><span class="sxs-lookup"><span data-stu-id="747ea-147">To cut and paste a relationship</span></span>  
  
1.  <span data-ttu-id="747ea-148">在 [方案總管] 中開啟 BizTalk 專案，然後按兩下對應以在 BizTalk 對應工具中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="747ea-148">In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.</span></span>  
  
2.  <span data-ttu-id="747ea-149">選取運算質和/或您要剪下的連結。</span><span class="sxs-lookup"><span data-stu-id="747ea-149">Select the functoids and/or links you want to cut.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="747ea-150">您可以選擇按住 CTRL 鍵，然後選取想要的運算質和/或連結，或者是將滑鼠拖曳過這些連結，以形成矩形選取範圍。</span><span class="sxs-lookup"><span data-stu-id="747ea-150">You can select either by holding down the CTRL key, and then selecting the desired functoids and/or links or by dragging and dropping the mouse across the links to form a rectangular selection.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="747ea-151">您可以使用「功能區選取」作業來選取多個連結和 (或) 運算質。</span><span class="sxs-lookup"><span data-stu-id="747ea-151">You can use the “ribbon select” operation to select multiple link(s) and/or functoid(s).</span></span> <span data-ttu-id="747ea-152">如需詳細資訊，請參閱[如何選取多個連結和運算質](../core/how-to-select-multiple-links-and-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="747ea-152">For more information, see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).</span></span>  
  
3.  <span data-ttu-id="747ea-153">選取範圍，以滑鼠右鍵按一下，然後按一下**剪下**。</span><span class="sxs-lookup"><span data-stu-id="747ea-153">Right-click the selection, and then click **Cut**.</span></span> <span data-ttu-id="747ea-154">或者，您可以按鍵盤上的 CTRL+X。</span><span class="sxs-lookup"><span data-stu-id="747ea-154">Alternatively, you can press CTRL+X on the keyboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="747ea-155">如需鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="747ea-155">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
4.  <span data-ttu-id="747ea-156">將游標放在您想貼上選取範圍的位置。</span><span class="sxs-lookup"><span data-stu-id="747ea-156">Place the cursor where you wish to paste the selection.</span></span>  
  
5.  <span data-ttu-id="747ea-157">在格線頁中，按一下滑鼠右鍵，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="747ea-157">Right-click on the grid page, and then click **Paste**.</span></span> <span data-ttu-id="747ea-158">或者，您可以選取並按鍵盤上的 CTRL+V。</span><span class="sxs-lookup"><span data-stu-id="747ea-158">Alternatively, you can select and press CTRL+V on the keyboard.</span></span> <span data-ttu-id="747ea-159">選取範圍就會從現有位置中刪除，並出現在新的位置。</span><span class="sxs-lookup"><span data-stu-id="747ea-159">The selection is deleted from the existing location and appears at the new location.</span></span>