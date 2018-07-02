---
title: 如何複製、 剪下和貼上運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 825847e4-87db-4b40-8e5d-5b5b1c79c6de
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c99fc624ce76a9bdd8adc4addc4a8be5ab9d035
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965999"
---
# <a name="how-to-copy-cut-and-paste-a-functoid"></a><span data-ttu-id="30014-102">如何複製、剪下與貼上運算質</span><span class="sxs-lookup"><span data-stu-id="30014-102">How to Copy, Cut, and Paste a Functoid</span></span>
<span data-ttu-id="30014-103">「BizTalk 對應工具」中的複製/剪下/貼上功能可讓人重複使用運算質。</span><span class="sxs-lookup"><span data-stu-id="30014-103">The copy/cut/paste feature in the BizTalk Mapper enables the reusability of functoids.</span></span> <span data-ttu-id="30014-104">在對應中，您可以將某個格線頁中的一或多個運算質複製、剪下及貼至另一個格線頁。</span><span class="sxs-lookup"><span data-stu-id="30014-104">In a map, you can copy, cut, and paste one or more functoids from one grid page to another.</span></span> <span data-ttu-id="30014-105">本主題提供執行這些作業的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="30014-105">This topic provides step-by-step instructions to perform these operations.</span></span>  
  
 <span data-ttu-id="30014-106">當您要重複使用運算質時，可以使用複製/貼上功能。</span><span class="sxs-lookup"><span data-stu-id="30014-106">You can use the copy/paste feature when you want to reuse functoids.</span></span> <span data-ttu-id="30014-107">此外，當您要將運算質從現有位置移除並移到新位置時，可以使用剪下/貼上功能。</span><span class="sxs-lookup"><span data-stu-id="30014-107">And, when you want to remove a functoid from the existing location and move it to a new location, you can use the cut/paste feature.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="30014-108">當您選擇複製運算質時，會同時複製運算質、其標籤、註解、常數輸入及預留位置索引。</span><span class="sxs-lookup"><span data-stu-id="30014-108">When you choose to copy a functoid, the functoid, its label, comments, and the constant-inputs, along with the placeholder indices, are copied.</span></span> <span data-ttu-id="30014-109">同樣地，當您選擇剪下運算質時，會同時剪下運算質、其標籤、註解、常數輸入及預留位置索引。</span><span class="sxs-lookup"><span data-stu-id="30014-109">Similarly, when you choose to cut a functoid, the functoid, its label, comments, constant-inputs, along with the placeholder indices, are cut.</span></span> <span data-ttu-id="30014-110">但是，當您貼上 (在選擇剪下之後) 選取範圍時，只會保留運算質並且會刪除被遺棄的連結。</span><span class="sxs-lookup"><span data-stu-id="30014-110">But, when you paste (after choosing to cut) the selection, only the functoid is retained and the orphaned links are deleted.</span></span> <span data-ttu-id="30014-111">標籤、註解、常數輸入和預留位置索引並不會保留。</span><span class="sxs-lookup"><span data-stu-id="30014-111">The label, comments, constant inputs, and placeholder indices are not retained.</span></span>  
  
 <span data-ttu-id="30014-112">如果您只選取已連結至其他運算質或結構描述節點的運算質，則只會剪下或複製該運算質，而不會同時剪下或複製連結。</span><span class="sxs-lookup"><span data-stu-id="30014-112">If you select only a functoid, which is either linked to another functoid or a schema node, only the functoid will be cut or copied, without the links.</span></span> <span data-ttu-id="30014-113">如果您剪下已連結至對應中其他運算質或是結構描述節點的運算質，則會刪除通往所剪下運算質的連結。</span><span class="sxs-lookup"><span data-stu-id="30014-113">If you cut a functoid that is linked to other functoids in the map or to the schema nodes, the links to the functoid that is cut are deleted.</span></span>  
  
 <span data-ttu-id="30014-114">您可以從下列位置複製/剪下運算質：</span><span class="sxs-lookup"><span data-stu-id="30014-114">You can copy/cut functoids from:</span></span>  
  
- <span data-ttu-id="30014-115">同一個對應格線頁內</span><span class="sxs-lookup"><span data-stu-id="30014-115">Within the same grid page of a map</span></span>  
  
- <span data-ttu-id="30014-116">同一個對應中的不同格線頁之間</span><span class="sxs-lookup"><span data-stu-id="30014-116">One grid page to the other in the same map</span></span>  
  
- <span data-ttu-id="30014-117">兩個 Visual Studio 執行個體之間</span><span class="sxs-lookup"><span data-stu-id="30014-117">One instance of Visual Studio to another</span></span>  
  
  <span data-ttu-id="30014-118">您可以復原或重做剪下與貼上作業。</span><span class="sxs-lookup"><span data-stu-id="30014-118">You can undo or redo the cut and paste operations.</span></span> <span data-ttu-id="30014-119">如需詳細資訊，請參閱 <<c0> [ 如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="30014-119">For more information, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="30014-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="30014-120">Prerequisites</span></span>  
 <span data-ttu-id="30014-121">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="30014-121">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-copy-and-paste-a-functoid"></a><span data-ttu-id="30014-122">若要 複製並貼上運算質</span><span class="sxs-lookup"><span data-stu-id="30014-122">To copy and paste a functoid</span></span>  
  
1.  <span data-ttu-id="30014-123">在 [方案總管] 中開啟 BizTalk 專案，然後按兩下對應以在 BizTalk 對應工具中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="30014-123">In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.</span></span>  
  
2.  <span data-ttu-id="30014-124">選取您要複製的 運算質 。</span><span class="sxs-lookup"><span data-stu-id="30014-124">Select the functoid you want to copy.</span></span> <span data-ttu-id="30014-125">若要選取多個運算質，請按其中一個運算質，按住 CTRL 鍵，然後按一下其餘運算質。</span><span class="sxs-lookup"><span data-stu-id="30014-125">To select multiple functoids, click one functoid, hold down the CTRL key, and then click the other functoids.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30014-126">您可以使用「功能區選取」作業來選取多個連結和 (或) 運算質。</span><span class="sxs-lookup"><span data-stu-id="30014-126">You can use the “ribbon select” operation to select multiple link(s) and/or functoid(s).</span></span> <span data-ttu-id="30014-127">如需詳細資訊，請參閱 <<c0> [ 如何選取多個連結和運算質](../core/how-to-select-multiple-links-and-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="30014-127">For more information, see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).</span></span>  
  
3.  <span data-ttu-id="30014-128">選取範圍，以滑鼠右鍵按一下，然後按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="30014-128">Right-click the selection, and then click **Copy**.</span></span> <span data-ttu-id="30014-129">或者，您可以按一下**複製**從 Visual Studio**編輯**功能表或鍵盤上的按下 CTRL + C。</span><span class="sxs-lookup"><span data-stu-id="30014-129">Alternatively, you can either click **Copy** from the Visual Studio’s **Edit** menu or press CTRL+C on the keyboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30014-130">如需鍵盤快速鍵的清單，請參閱 < [BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="30014-130">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
4.  <span data-ttu-id="30014-131">將游標放在您想貼上運算質的位置。</span><span class="sxs-lookup"><span data-stu-id="30014-131">Place the cursor where you wish to paste the functoid.</span></span>  
  
5.  <span data-ttu-id="30014-132">以滑鼠右鍵按一下格線頁，然後**貼上**。</span><span class="sxs-lookup"><span data-stu-id="30014-132">Right-click on the grid page, and then click **Paste**.</span></span> <span data-ttu-id="30014-133">或者，您可以按一下**貼上**從 Visual Studio**編輯**功能表或鍵盤上的按下 CTRL + V 鍵。</span><span class="sxs-lookup"><span data-stu-id="30014-133">Alternatively, you can either click **Paste** from the Visual Studio’s **Edit** menu or press CTRL+V on the keyboard.</span></span> <span data-ttu-id="30014-134">所 選取運算質或運算質群組的複本會出現在新的位置 。</span><span class="sxs-lookup"><span data-stu-id="30014-134">A copy of the selected functoid or group of functoids appears at the new location.</span></span>  
  
### <a name="to-cut-and-paste-a-functoid"></a><span data-ttu-id="30014-135">若要 剪下並貼上運算質</span><span class="sxs-lookup"><span data-stu-id="30014-135">To cut and paste a functoid</span></span>  
  
1.  <span data-ttu-id="30014-136">在 [方案總管] 中開啟 BizTalk 專案，然後按兩下對應以在 BizTalk 對應工具中加以開啟。</span><span class="sxs-lookup"><span data-stu-id="30014-136">In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.</span></span>  
  
2.  <span data-ttu-id="30014-137">選取您要剪下的運算質。</span><span class="sxs-lookup"><span data-stu-id="30014-137">Select the functoid you want to cut.</span></span> <span data-ttu-id="30014-138">若要選取多個運算質，請按其中一個運算質，按住 CTRL 鍵，然後按一下其餘運算質。</span><span class="sxs-lookup"><span data-stu-id="30014-138">To select multiple functoids, click one functoid, hold down the CTRL key, and then click the other functoids.</span></span>  
  
3.  <span data-ttu-id="30014-139">選取範圍，以滑鼠右鍵按一下，然後按一下**剪下**。</span><span class="sxs-lookup"><span data-stu-id="30014-139">Right-click the selection, and then click **Cut**.</span></span> <span data-ttu-id="30014-140">或者，您可以按一下**剪下**從 Visual Studio**編輯**功能表或鍵盤上的按下 CTRL + X。</span><span class="sxs-lookup"><span data-stu-id="30014-140">Alternatively, you can either click **Cut** from the Visual Studio’s **Edit** menu or press CTRL+X on the keyboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30014-141">如需鍵盤快速鍵的清單，請參閱 < [BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="30014-141">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
4.  <span data-ttu-id="30014-142">將游標放在您想貼上運算質的位置。</span><span class="sxs-lookup"><span data-stu-id="30014-142">Place the cursor where you wish to paste the functoid.</span></span>  
  
5.  <span data-ttu-id="30014-143">以滑鼠右鍵按一下格線頁，然後**貼上**。</span><span class="sxs-lookup"><span data-stu-id="30014-143">Right-click on the grid page, and then click **Paste**.</span></span> <span data-ttu-id="30014-144">或者，您可以按一下**貼上**從 Visual Studio**編輯**功能表或鍵盤上的按下 CTRL + V 鍵。</span><span class="sxs-lookup"><span data-stu-id="30014-144">Alternatively, you can either click **Paste** from the Visual Studio’s **Edit** menu or press CTRL+V on the keyboard.</span></span> <span data-ttu-id="30014-145">所 選取運算質或運算質群組會自現有位置刪除，並出現在新的位置 。</span><span class="sxs-lookup"><span data-stu-id="30014-145">The selected functoid or group of functoids are deleted from the existing location and appear at the new location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30014-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30014-146">See Also</span></span>  
 [<span data-ttu-id="30014-147">使用運算質建立更多複雜對應</span><span class="sxs-lookup"><span data-stu-id="30014-147">Using Functoids to Create More Complex Mappings</span></span>](../core/using-functoids-to-create-more-complex-mappings.md)