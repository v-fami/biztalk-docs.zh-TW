---
title: "如何移動格線頁之間的關聯性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.movetopage
ms.assetid: 185add4d-c876-44b6-b6e0-71c15a9b7c26
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5737adcb9159568bfea7c7cdde9dff8015b19706
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-a-relationship-between-grid-pages"></a><span data-ttu-id="a9c41-102">如何在格線頁之間移動關聯性</span><span class="sxs-lookup"><span data-stu-id="a9c41-102">How to Move a Relationship Between Grid Pages</span></span>
<span data-ttu-id="a9c41-103">大型的對應會包含許多運算質與連結的集合，以致於您無法輕易地識別連結多個運算質的連結。</span><span class="sxs-lookup"><span data-stu-id="a9c41-103">Large maps include many sets of functoids and links, which can make it difficult for you to identify the links joining multiple functoids.</span></span> <span data-ttu-id="a9c41-104">碰到這類情況時您可能需要將類似的運算質與連結的集合移至不同的格線頁，讓對應更容易為人所解讀。</span><span class="sxs-lookup"><span data-stu-id="a9c41-104">In such a scenario, you might want to move a similar set of functoids and links to a different grid page to make the map more readable.</span></span> <span data-ttu-id="a9c41-105">本主題提供執行此作業的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="a9c41-105">This topic provides step-by-step instructions to perform the operation.</span></span>  
  
 <span data-ttu-id="a9c41-106">您可以透過下列其中一種方式在格線頁之間移動關係 (但僅限於在同一張對應中)：</span><span class="sxs-lookup"><span data-stu-id="a9c41-106">You can move a relationship from one grid page to another, in the same map only, in one of the following ways:</span></span>  
  
-   <span data-ttu-id="a9c41-107">使用**移動到頁面**對話方塊</span><span class="sxs-lookup"><span data-stu-id="a9c41-107">Using the **Move to Page** dialog box</span></span>  
  
-   <span data-ttu-id="a9c41-108">使用內含功能區選取運算質 (與連結) 之拖放功能</span><span class="sxs-lookup"><span data-stu-id="a9c41-108">Using the drag-and-drop of the ribbon-selected functoid(s) (and links)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9c41-109">您可以移動一或多個運算質與其連結。</span><span class="sxs-lookup"><span data-stu-id="a9c41-109">You can move one or more functoids and their links.</span></span> <span data-ttu-id="a9c41-110">當您移動關係時，所有與該關係關聯的標籤、註解與常數值 (連同正確的預留位置) 都會跟著一起移動。</span><span class="sxs-lookup"><span data-stu-id="a9c41-110">When you move a relationship, the labels, comments, and the constant values (along with the correct place holders) associated with that relationship are retained.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9c41-111">您無法只將連結拖放至另一個格線頁。</span><span class="sxs-lookup"><span data-stu-id="a9c41-111">You cannot drag-and-drop only links to another grid page.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a9c41-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="a9c41-112">Prerequisites</span></span>  
 <span data-ttu-id="a9c41-113">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="a9c41-113">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-move-a-relationship-using-move-to-page-dialog-box"></a><span data-ttu-id="a9c41-114">若要使用移至頁面對話方塊來移動關係</span><span class="sxs-lookup"><span data-stu-id="a9c41-114">To move a relationship using Move To Page dialog box</span></span>  
  
1.  <span data-ttu-id="a9c41-115">在對應上，選取要移動的關係所在的格線頁。</span><span class="sxs-lookup"><span data-stu-id="a9c41-115">On the map, select the grid page from which you want to move a relationship.</span></span>  
  
2.  <span data-ttu-id="a9c41-116">以滑鼠右鍵按一下運算質或連結您想要移動，然後按一下 關聯性中的**移動到頁面**。</span><span class="sxs-lookup"><span data-stu-id="a9c41-116">Right-click a functoid or a link in the relationship you want to move and then click **Move to Page**.</span></span> <span data-ttu-id="a9c41-117">隨即顯示訊息，說明將會移動所有選取的對應項目以及相關的連結和運算質。</span><span class="sxs-lookup"><span data-stu-id="a9c41-117">A message saying that all the selected map items(s), along with related links and functoids, will be moved is displayed.</span></span> <span data-ttu-id="a9c41-118">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a9c41-118">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9c41-119">若要停用快顯訊息，在 Visual Studio 功能表中，移至**工具**，按一下 **選項**，按一下  **BizTalk 對應工具**，按一下 **一般**，然後取消核取**移至頁面**選項。</span><span class="sxs-lookup"><span data-stu-id="a9c41-119">To disable the message popup, in the Visual Studio menu, go to **Tools**, click **Options**, click **BizTalk Mapper**, click **General**, and then uncheck the **Move to page** option.</span></span> <span data-ttu-id="a9c41-120">如需一般選項的詳細資訊，請參閱[如何自訂 BizTalk 對應工具中的一般設定](../core/how-to-customize-general-settings-in-biztalk-mapper.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c41-120">For more information about general options, see [How to Customize General Settings in BizTalk Mapper](../core/how-to-customize-general-settings-in-biztalk-mapper.md).</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="a9c41-121">或者，您可以按 CTRL + M、 CTRL + M 開啟**移動到頁面** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9c41-121">Alternatively, you can press CTRL+M, CTRL+M to open the **Move to Page** dialog box.</span></span> <span data-ttu-id="a9c41-122">如需對應工具快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c41-122">For a list of Mapper shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
     <span data-ttu-id="a9c41-123">![將選取的關聯性移至新頁面](../core/media/moving-a-functoid-new.gif "Moving_a_functoid_new")</span><span class="sxs-lookup"><span data-stu-id="a9c41-123">![Moving selected relationship to a new page](../core/media/moving-a-functoid-new.gif "Moving_a_functoid_new")</span></span>  
  
3.  <span data-ttu-id="a9c41-124">在**移動到頁面**對話方塊方塊中，選取您想要移動關聯性，然後按一下目標格線頁**確定**。</span><span class="sxs-lookup"><span data-stu-id="a9c41-124">In the **Move to Page** dialog box, select the target grid page to which you want to move the relationship, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9c41-125">您也可以建立新的頁面，選取 **\*（加入新的頁面）**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a9c41-125">You can also create a new page by selecting **\*(add new page)**, and then clicking **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9c41-126">或者，您也可以按 CTRL+M、CTRL+A 在對應中新增格線頁。</span><span class="sxs-lookup"><span data-stu-id="a9c41-126">Alternatively, you can press CTRL+M, CTRL+A to add a new grid page in a map.</span></span> <span data-ttu-id="a9c41-127">如需對應工具快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c41-127">For a list of Mapper shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
     <span data-ttu-id="a9c41-128">![選取目標格線頁](../core/media/moving-a-functoid-step4.gif "Moving_a_functoid_Step4")</span><span class="sxs-lookup"><span data-stu-id="a9c41-128">![Selecting the target grid page](../core/media/moving-a-functoid-step4.gif "Moving_a_functoid_Step4")</span></span>  
  
     <span data-ttu-id="a9c41-129">選取的運算質/連結 (連同相關的運算質與連結) 會一起移至新的格線頁。</span><span class="sxs-lookup"><span data-stu-id="a9c41-129">The selected functoid/link, along with the related functoids and links, is moved to the new grid page.</span></span> <span data-ttu-id="a9c41-130">下圖說明如何將選取的關係 (位於第 3 頁) 移至第 1 頁。</span><span class="sxs-lookup"><span data-stu-id="a9c41-130">The figure below shows the selected relationship (which was in Page 3) moved to Page 1.</span></span>  
  
     <span data-ttu-id="a9c41-131">![選取的關聯性移至新頁面](../core/media/moving-a-functoid-new2.gif "Moving_a_functoid_new2")</span><span class="sxs-lookup"><span data-stu-id="a9c41-131">![Selected relationship is moved to a new page](../core/media/moving-a-functoid-new2.gif "Moving_a_functoid_new2")</span></span>  
  
### <a name="to-move-a-relationship-using-drag-and-drop"></a><span data-ttu-id="a9c41-132">若要使用拖放方式來移動關係</span><span class="sxs-lookup"><span data-stu-id="a9c41-132">To move a relationship using drag-and-drop</span></span>  
  
1.  <span data-ttu-id="a9c41-133">在對應上，選取要移動的關係所在的格線頁。</span><span class="sxs-lookup"><span data-stu-id="a9c41-133">On the map, select the grid page from which you want to move a relationship.</span></span>  
  
2.  <span data-ttu-id="a9c41-134">選取要移至另一個格線頁的運算質 (和連結)。</span><span class="sxs-lookup"><span data-stu-id="a9c41-134">Select the functoid(s) (and link(s)) you want to move to another grid page.</span></span> <span data-ttu-id="a9c41-135">這會遞迴選取所有連接至選取範圍內所有運算質的連結。</span><span class="sxs-lookup"><span data-stu-id="a9c41-135">This recursively selects all links that connect to the functoids in the selection.</span></span>  
  
3.  <span data-ttu-id="a9c41-136">將選取範圍拖曳至要將關係移至的頁面 (在頁面索引標籤上)。</span><span class="sxs-lookup"><span data-stu-id="a9c41-136">Drag the selection to the page (on the page tab) where you want to move the relationship.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="a9c41-137">在您執行步驟 4 之前，請不要放開滑鼠。</span><span class="sxs-lookup"><span data-stu-id="a9c41-137">Do not release the mouse till you perform step 4.</span></span>  
  
4.  <span data-ttu-id="a9c41-138">目標格線頁變成焦點時 (在上圖中，第一頁具有焦點)，請在格線頁的空儲存格上放下選取範圍。</span><span class="sxs-lookup"><span data-stu-id="a9c41-138">When the target grid page comes into focus (in the above figure, Page 1 is in focus), drop the selection on an empty cell on the grid page.</span></span> <span data-ttu-id="a9c41-139">這時選取的關係會移至新的格線頁。</span><span class="sxs-lookup"><span data-stu-id="a9c41-139">The selected relationship is moved to the new grid page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c41-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9c41-140">See Also</span></span>  
 [<span data-ttu-id="a9c41-141">使用格線頁</span><span class="sxs-lookup"><span data-stu-id="a9c41-141">Working with Grid Pages</span></span>](../core/working-with-grid-pages.md)