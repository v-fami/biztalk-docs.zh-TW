---
title: "如何選取多個連結與運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9ae50cb-c212-48f3-9dfb-74df282645c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8885fe33d0c3a2dc081fbca66a398003c3e21913
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-select-multiple-links-and-functoids"></a><span data-ttu-id="8cd8f-102">如何選取多個連結與運算質</span><span class="sxs-lookup"><span data-stu-id="8cd8f-102">How to Select Multiple Links and Functoids</span></span>
<span data-ttu-id="8cd8f-103">當您想要在對應中執行類似的運算質和/或連結的群組上的作業時，您可以選取該運算質和/或連結的群組，所有在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-103">When you want to perform a similar operation on a group of functoids and/or links in a map, you can select that group of functoids and/or links all at the same time.</span></span> <span data-ttu-id="8cd8f-104">本主題提供如何執行此作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-104">This topic provides information about how to perform this operation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8cd8f-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="8cd8f-105">Prerequisites</span></span>  
 <span data-ttu-id="8cd8f-106">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-106">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="why-do-you-need-to-bulk-select-linksfunctoids"></a><span data-ttu-id="8cd8f-107">為什麼會需要大量選取連結/運算質？</span><span class="sxs-lookup"><span data-stu-id="8cd8f-107">Why do you need to bulk-select links/functoids?</span></span>  
 <span data-ttu-id="8cd8f-108">大量選取連結和 (或) 運算質，可讓您執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="8cd8f-108">You can bulk-select links and/or functoids to do any of the following:</span></span>  
  
-   <span data-ttu-id="8cd8f-109">複製/剪下選取範圍並貼到同一個格線頁或是同一個對應中的其他格線頁。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-109">Copy/cut and paste the selection in the same grid page or another grid page in the same map.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8cd8f-110">如需如何剪下、 複製和貼上連結和運算質的資訊，請參閱[如何剪下、 複製和貼上連結和運算質](../core/how-to-copy-cut-and-paste-links-and-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-110">For information on how to copy, cut, and paste links and functoids, see [How to Copy, Cut, and Paste Links and Functoids](../core/how-to-copy-cut-and-paste-links-and-functoids.md).</span></span>  
  
-   <span data-ttu-id="8cd8f-111">在格線頁之間移動選取範圍</span><span class="sxs-lookup"><span data-stu-id="8cd8f-111">Move the selection between grid pages</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8cd8f-112">如需如何將關係從一個格線頁移至另一個資訊，請參閱[如何移動關係格線頁之間](../core/how-to-move-a-relationship-between-grid-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-112">For information on how to move a relationship from one grid page to another, see [How to Move a Relationship Between Grid Pages](../core/how-to-move-a-relationship-between-grid-pages.md).</span></span>  
  
-   <span data-ttu-id="8cd8f-113">編輯選取範圍中運算質和連結的通用屬性</span><span class="sxs-lookup"><span data-stu-id="8cd8f-113">Edit the common properties of functoids and links in the selection</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8cd8f-114">如需如何設定註解和運算質和連結的標籤資訊，請參閱[如何標示連結](../core/how-to-label-a-link.md)或[如何加上標籤與註解的運算質](../core/how-to-label-and-comment-a-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-114">For information on how to set comments and labels for functoids and links, see [How to Label a Link](../core/how-to-label-a-link.md) or [How to Label and Comment a Functoid](../core/how-to-label-and-comment-a-functoid.md).</span></span>  
  
-   <span data-ttu-id="8cd8f-115">以一個步驟刪除多個連結和 (或) 運算質</span><span class="sxs-lookup"><span data-stu-id="8cd8f-115">Deleting multiple link(s) and/or functoid(s) in one step</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8cd8f-116">如需如何刪除運算質的資訊，請參閱[如何刪除運算質](../core/how-to-delete-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-116">For information on how to delete functoids, see [How to Delete Functoids](../core/how-to-delete-functoids.md).</span></span>  
  
## <a name="to-select-multiple-links-and-functoids"></a><span data-ttu-id="8cd8f-117">若要選取多個連結和運算質</span><span class="sxs-lookup"><span data-stu-id="8cd8f-117">To select multiple links and functoids</span></span>  
 <span data-ttu-id="8cd8f-118">您可以任何下列方式大量選取運算質和 (或) 連結：</span><span class="sxs-lookup"><span data-stu-id="8cd8f-118">You can bulk-select functoids and/or links in any of the following ways:</span></span>  
  
-   <span data-ttu-id="8cd8f-119">按一下連結或運算質。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-119">Click the link or the functoid.</span></span> <span data-ttu-id="8cd8f-120">按住 CTRL 鍵，然後按一下您想要選取的其他連結和 (或) 運算質。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-120">Hold down the CTRL key, and then click the other links and/or functoids you want to select.</span></span>  
  
     <span data-ttu-id="8cd8f-121">下圖顯示選取的運算質和連結 (已反白顯示)。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-121">The following figure shows the selected functoids and links highlighted.</span></span>  
  
     <span data-ttu-id="8cd8f-122">![大量選取運算質和連結](../core/media/bulkselect-functois-links.gif "BulkSelect_Functois （& s) 的連結")</span><span class="sxs-lookup"><span data-stu-id="8cd8f-122">![Bulk selecting functoids and links](../core/media/bulkselect-functois-links.gif "BulkSelect_Functois&Links")</span></span>  
  
-   <span data-ttu-id="8cd8f-123">在對應介面上拖曳滑鼠。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-123">Drag the mouse on the map surface.</span></span> <span data-ttu-id="8cd8f-124">選取矩形下的運算質會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-124">The functoids under the selection rectangle are highlighted.</span></span>  
  
     <span data-ttu-id="8cd8f-125">![運算質的矩形選取範圍](../core/media/bulkselect-selectionrectangle.gif "BulkSelect_SelectionRectangle")</span><span class="sxs-lookup"><span data-stu-id="8cd8f-125">![Rectangle selection of functoids](../core/media/bulkselect-selectionrectangle.gif "BulkSelect_SelectionRectangle")</span></span>  
  
-   <span data-ttu-id="8cd8f-126">您可以結合運用拖曳和 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-126">You can use a combination of dragging and CTRL-click.</span></span> <span data-ttu-id="8cd8f-127">在對應介面上拖曳滑鼠，選取該範圍內的運算質和 (或) 連結。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-127">Drag the mouse on the map surface and select the functoids and/or links in that range.</span></span> <span data-ttu-id="8cd8f-128">按住 CTRL 鍵，然後按一下選取範圍外的運算質和 (或) 連結。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-128">Hold down the CTRL key, and then click the functoids and/or links outside the selection range.</span></span>  
  
## <a name="to-select-all-links-and-functoids-on-the-grid-page"></a><span data-ttu-id="8cd8f-129">若要選取格線頁上的所有連結和運算質</span><span class="sxs-lookup"><span data-stu-id="8cd8f-129">To select all links and functoids on the grid page</span></span>  
 <span data-ttu-id="8cd8f-130">您可以使用下列任一方式選取 [對應工具] 格線頁上的所有運算質和連結：</span><span class="sxs-lookup"><span data-stu-id="8cd8f-130">You can select all the functoids and links on the Mapper grid page in any of the following ways:</span></span>  
  
-   <span data-ttu-id="8cd8f-131">以滑鼠右鍵按一下格線頁上的任何位置，然後按一下**全選**。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-131">Right-click anywhere on the grid page and click **Select All**.</span></span>  
  
-   <span data-ttu-id="8cd8f-132">按一下格線頁的任何位置，然後按鍵盤的 CTRL+A。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-132">Click anywhere on the grid page and click press CTRL+A from the keyboard.</span></span>  
  
-   <span data-ttu-id="8cd8f-133">按一下格線頁的任何位置。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-133">Click anywhere on the grid page.</span></span> <span data-ttu-id="8cd8f-134">從 Visual Studio 功能表中，按一下 **編輯**，然後按一下 **全選**。</span><span class="sxs-lookup"><span data-stu-id="8cd8f-134">From the Visual Studio menu, click **Edit**, and then click **Select All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cd8f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cd8f-135">See Also</span></span>  
 [<span data-ttu-id="8cd8f-136">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="8cd8f-136">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)