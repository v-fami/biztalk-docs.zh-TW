---
title: 如何復原或重做使用者作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cb3708e-a9c2-4795-aba0-9c6d9635e08c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8358fc1624346b90d98fd1f1707dd2bfb02446dd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973396"
---
# <a name="how-to-undo-or-redo-user-operations"></a><span data-ttu-id="8544e-102">如何復原或重做使用者作業</span><span class="sxs-lookup"><span data-stu-id="8544e-102">How to Undo or Redo User Operations</span></span>
<span data-ttu-id="8544e-103">BizTalk 對應工具提供的另一項使用性輔助工具是支援復原/取消復原功能。</span><span class="sxs-lookup"><span data-stu-id="8544e-103">The support for undo/redo is yet another usability aid provided by the BizTalk Mapper.</span></span> <span data-ttu-id="8544e-104">如果您不滿意所做的修改，或不慎做了錯誤的變更，您可以使用復原功能逐步回復至先前的原始狀態，然後再繼續修改。</span><span class="sxs-lookup"><span data-stu-id="8544e-104">If you are not satisfied with modifications you have made, or if you have made a change by mistake, you can use undo to gradually come back to an earlier "untouched" state, and resume from there.</span></span> <span data-ttu-id="8544e-105">取消復原功能可讓您重新套用已復原的編輯動作。</span><span class="sxs-lookup"><span data-stu-id="8544e-105">Redo allows you to reapply the editing actions that have been undone.</span></span> <span data-ttu-id="8544e-106">此主題說明可復原/取消復原之作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8544e-106">This topic provides information about the operations that you can undo/redo.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8544e-107">只有在對應上至少執行一個編輯作業時，才能夠復原作業。</span><span class="sxs-lookup"><span data-stu-id="8544e-107">You can undo an operation only when you have performed at least one edit operation on the map.</span></span> <span data-ttu-id="8544e-108">除非已使用復原命令，否則無法使用取消復原命令。</span><span class="sxs-lookup"><span data-stu-id="8544e-108">Redo is unavailable unless you have used the undo command.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8544e-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="8544e-109">Prerequisites</span></span>  
 <span data-ttu-id="8544e-110">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="8544e-110">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="what-can-you-undoredo"></a><span data-ttu-id="8544e-111">您可以復原/取消復原什麼項目？</span><span class="sxs-lookup"><span data-stu-id="8544e-111">What can you undo/redo?</span></span>  
 <span data-ttu-id="8544e-112">您可以復原/取消復原所有編輯作業。</span><span class="sxs-lookup"><span data-stu-id="8544e-112">You can undo/redo all editing operations.</span></span> <span data-ttu-id="8544e-113">可復原/取消復原的作業如下所示：</span><span class="sxs-lookup"><span data-stu-id="8544e-113">The operations that can be undone/redone are as follows:</span></span>  
  
-   <span data-ttu-id="8544e-114">剪下/複製/貼上運算質和/或連結。</span><span class="sxs-lookup"><span data-stu-id="8544e-114">Cutting/copying/pasting functoids and/or link</span></span>  
  
     <span data-ttu-id="8544e-115">只是選取和複製任意數目的項目 (連結/運算質)，並無法復原或重做它們。</span><span class="sxs-lookup"><span data-stu-id="8544e-115">You cannot undo or redo any number of items (links/functoids) by simply selecting and copying them.</span></span> <span data-ttu-id="8544e-116">複製函數不會變更對應上的任何項目。</span><span class="sxs-lookup"><span data-stu-id="8544e-116">Copy function does not change anything on the map.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8544e-117">如需如何剪下/複製/貼上運算質的資訊，請參閱[如何複製、 剪下和貼上運算質](../core/how-to-copy-cut-and-paste-a-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="8544e-117">For information about how to cut/copy/paste a functoid, see [How to Copy, Cut, and Paste a Functoid](../core/how-to-copy-cut-and-paste-a-functoid.md).</span></span> <span data-ttu-id="8544e-118">如需如何剪下/複製/貼上運算質和連結的詳細資訊，請參閱[如何剪下、 複製和貼上連結和運算質](../core/how-to-copy-cut-and-paste-links-and-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="8544e-118">For more information about how to cut/copy/paste functoid and link, see [How to Copy, Cut, and Paste Links and Functoids](../core/how-to-copy-cut-and-paste-links-and-functoids.md).</span></span>  
  
-   <span data-ttu-id="8544e-119">連結來源節點與目標節點或連結來源節點與運算質，連結運算質與另一個運算質或連結運算質與目標節點</span><span class="sxs-lookup"><span data-stu-id="8544e-119">Linking a source node to a target node, or a source node to a functoid, a functoid to another functoid, or a functoid to a target node</span></span>  
  
-   <span data-ttu-id="8544e-120">刪除運算質和/或連結</span><span class="sxs-lookup"><span data-stu-id="8544e-120">Deleting functoids and/or links</span></span>  
  
-   <span data-ttu-id="8544e-121">將選取的連結與運算質移至另一個格線頁</span><span class="sxs-lookup"><span data-stu-id="8544e-121">Moving selected links and functoids to another grid page</span></span>  
  
-   <span data-ttu-id="8544e-122">新增、移動、重新排序或刪除格線頁</span><span class="sxs-lookup"><span data-stu-id="8544e-122">Adding, moving, reordering, or deleting grid pages</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8544e-123">如需加入資訊，移動、 重新排列或刪除格線頁，請參閱[如何重新排序格線頁](../core/how-to-reorder-grid-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="8544e-123">For information on adding, moving, reordering, or deleting grid pages, see [How to Reorder Grid Pages](../core/how-to-reorder-grid-pages.md).</span></span>  
  
-   <span data-ttu-id="8544e-124">在建立對應時選取來源與目的結構描述</span><span class="sxs-lookup"><span data-stu-id="8544e-124">Selecting source and destination schemas while creating a map</span></span>  
  
-   <span data-ttu-id="8544e-125">取代來源/目的結構描述</span><span class="sxs-lookup"><span data-stu-id="8544e-125">Replacing source/destination schema</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8544e-126">如需如何取代來源/目的結構描述資訊，請參閱[如何取代結構描述](../core/how-to-replace-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="8544e-126">For information on how to replace source/destination schema, see [How to Replace Schemas](../core/how-to-replace-schemas.md).</span></span>  
  
-   <span data-ttu-id="8544e-127">設定運算質的輸入參數</span><span class="sxs-lookup"><span data-stu-id="8544e-127">Configuring input parameters for functoids</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8544e-128">如需詳細資訊，請參閱[如何設定運算質輸入參數](../core/how-to-configure-functoid-input-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="8544e-128">For more information, see [How to Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md).</span></span>  
  
-   <span data-ttu-id="8544e-129">設定/編輯連結的標籤</span><span class="sxs-lookup"><span data-stu-id="8544e-129">Setting/editing labels for links</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8544e-130">如需詳細資訊，請參閱[如何標示連結](../core/how-to-label-a-link.md)。</span><span class="sxs-lookup"><span data-stu-id="8544e-130">For more information, see [How to Label a Link](../core/how-to-label-a-link.md).</span></span>  
  
-   <span data-ttu-id="8544e-131">設定/編輯運算質的標籤和 (或) 註解</span><span class="sxs-lookup"><span data-stu-id="8544e-131">Setting/editing labels and/or comments for functoids</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8544e-132">如需詳細資訊，請參閱[如何加上標籤與註解的運算質](../core/how-to-label-and-comment-a-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="8544e-132">For more information, see [How to Label and Comment a Functoid](../core/how-to-label-and-comment-a-functoid.md).</span></span>  
  
-   <span data-ttu-id="8544e-133">對應工具格線的 [略過連結的命名空間] 和 [指令碼類型優先順序] 屬性。</span><span class="sxs-lookup"><span data-stu-id="8544e-133">Ignore Namespaces for Links and Script Type Precedence properties for Mapper grid.</span></span>  
  
-   <span data-ttu-id="8544e-134">將連結的其中一端從某個節點或運算質拖曳至另一個節點或運算質，以取代連結。</span><span class="sxs-lookup"><span data-stu-id="8544e-134">Replacing a link by dragging one end point of a link from a node or functoid to anther node or functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8544e-135">如需詳細資訊，請參閱[如何建立連結](../core/how-to-create-links.md)。</span><span class="sxs-lookup"><span data-stu-id="8544e-135">For more information, see [How to Create Links](../core/how-to-create-links.md).</span></span>  
  
-   <span data-ttu-id="8544e-136">執行中的多個修改**設定\<運算質\>運算質**對話方塊中，會被視為單一作業。</span><span class="sxs-lookup"><span data-stu-id="8544e-136">Performing multiple modifications in the **Configure \<Functoid\> Functoid** dialog box, which is treated as a single operation.</span></span>  
  
-   <span data-ttu-id="8544e-137">拖曳對應工具格線內的運算質和 (或) 連結。</span><span class="sxs-lookup"><span data-stu-id="8544e-137">Dragging functoid(s) and/or link(s) within the Mapper grid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8544e-138">如需詳細資訊，請參閱[如何移動關係格線頁之間](../core/how-to-move-a-relationship-between-grid-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="8544e-138">For more information, see [How to Move a Relationship Between Grid Pages](../core/how-to-move-a-relationship-between-grid-pages.md).</span></span>  
  
## <a name="how-can-you-undoredo-any-operation"></a><span data-ttu-id="8544e-139">如何復原/取消復原任何作業？</span><span class="sxs-lookup"><span data-stu-id="8544e-139">How can you undo/redo any operation?</span></span>  
 <span data-ttu-id="8544e-140">您可以使用下列其中一種方法來復原/取消復原作業：</span><span class="sxs-lookup"><span data-stu-id="8544e-140">You can undo/redo an operation in one of the following ways:</span></span>  
  
-   <span data-ttu-id="8544e-141">從 Visual Studio**編輯**功能表。</span><span class="sxs-lookup"><span data-stu-id="8544e-141">From the Visual Studio’s **Edit** menu.</span></span>  
  
-   <span data-ttu-id="8544e-142">按一下工具列上的復原與取消復原圖示。</span><span class="sxs-lookup"><span data-stu-id="8544e-142">Clicking the undo and redo icons on the toolbar.</span></span>  
  
-   <span data-ttu-id="8544e-143">按下 CTRL+Z 復原，按下 CTRL+Y 取消復原。</span><span class="sxs-lookup"><span data-stu-id="8544e-143">Pressing CTRL+Z for undo and CTRL+Y for redo.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8544e-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="8544e-144">See Also</span></span>  
 [<span data-ttu-id="8544e-145">使用格線頁</span><span class="sxs-lookup"><span data-stu-id="8544e-145">Working with Grid Pages</span></span>](../core/working-with-grid-pages.md)