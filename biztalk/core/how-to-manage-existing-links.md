---
title: "如何管理現有連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0db213b9-df84-4ebd-a59f-7691774d5031
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cdc505f98f61dd7259c8893b526ff094128df42
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-manage-existing-links"></a><span data-ttu-id="4d0c1-102">如何管理現有連結</span><span class="sxs-lookup"><span data-stu-id="4d0c1-102">How to Manage Existing Links</span></span>
<span data-ttu-id="4d0c1-103">您有時可能需要變更連結的來源或目的、命名或重新命名連結，或刪除連結。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-103">Sometimes you may need to change the source or destination of a link, name or rename a link, or delete a link.</span></span> <span data-ttu-id="4d0c1-104">本主題針對執行這些類型的連結作業，提供逐步指示。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-104">This topic provides step-by-step instructions for performing these types of link operations.</span></span>  
  
### <a name="to-change-the-source-or-destination-of-a-link"></a><span data-ttu-id="4d0c1-105">變更連結的來源或目的</span><span class="sxs-lookup"><span data-stu-id="4d0c1-105">To change the source or destination of a link</span></span>  
  
1.  <span data-ttu-id="4d0c1-106">在「BizTalk 對應工具」的格線頁中，按一下連結以選取連結。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-106">In BizTalk Mapper, in a grid page, click a link to select it.</span></span>  
  
     <span data-ttu-id="4d0c1-107">格線頁中所選連結的端點會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-107">The endpoints of a selected link in the grid page are highlighted.</span></span>  
  
2.  <span data-ttu-id="4d0c1-108">將連結的任一端點拖曳至新的結構描述節點或要連接的運算質。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-108">Drag either endpoint of the link to the new schema node or functoid to which you want it to connect it.</span></span>  
  
     <span data-ttu-id="4d0c1-109">當您拖曳端點時，游標會變成十字形狀。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-109">As you drag an endpoint, the cursor becomes a crosshair.</span></span> <span data-ttu-id="4d0c1-110">若您指向不能接受該連結的結構描述節點或運算質 (或其他物件)，則此游標會變成一個有線條劃過的圓圈。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-110">If you point to a schema node or functoid (or other object) which cannot accept the link, the cursor becomes a circle with a line through it.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4d0c1-111">若您有二或多個連接到運算質的輸入連結，且您要將一或多個這些輸入連結重新導向至來源結構描述中的其他節點或其他運算質，則不會保留此原始運算質的輸入參數順序。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-111">If you have two or more input links connected to a functoid and you redirect one or more of those input links to other nodes in the source schema or to other functoids, the order of the input parameters to the original functoid may not be preserved.</span></span> <span data-ttu-id="4d0c1-112">使用**設定\<運算質\>運算質**對話方塊中，檢閱產生的輸入參數的順序，並視需要重新排序它們。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-112">Use the **Configure \<Functoid\> Functoid** dialog box to review the resulting order of the input parameters and to reorder them if necessary.</span></span> <span data-ttu-id="4d0c1-113">如需重新排序運算質的輸入的參數的詳細資訊，請參閱[編輯運算質屬性和輸入參數](../core/editing-functoid-properties-and-input-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-113">For more information about reordering the input parameters of a functoid, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md).</span></span>  
  
### <a name="to-setedit-the-label-of-a-link"></a><span data-ttu-id="4d0c1-114">若要設定/編輯連結的標籤</span><span class="sxs-lookup"><span data-stu-id="4d0c1-114">To set/edit the label of a link</span></span>  
  
1.  <span data-ttu-id="4d0c1-115">在「BizTalk 對應工具」的格線頁中，按一下連結以選取連結。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-115">In BizTalk Mapper, in a grid page, click a link to select it.</span></span>  
  
     <span data-ttu-id="4d0c1-116">格線頁中所選連結的端點會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-116">The endpoints of a selected link in the grid page are highlighted.</span></span>  
  
2.  <span data-ttu-id="4d0c1-117">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中提供的連結使用 （新） 名稱**標籤**屬性。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-117">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, provide a (new) name for the link using the **Label** property.</span></span>  
  
### <a name="to-delete-a-link"></a><span data-ttu-id="4d0c1-118">刪除連結</span><span class="sxs-lookup"><span data-stu-id="4d0c1-118">To delete a link</span></span>  
  
1.  <span data-ttu-id="4d0c1-119">在「BizTalk 對應工具」的格線頁中，按一下連結以選取連結。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-119">In BizTalk Mapper, in a grid page, click a link to select it.</span></span>  
  
     <span data-ttu-id="4d0c1-120">格線頁中所選連結的端點會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-120">The endpoints of a selected link in the grid page are highlighted.</span></span>  
  
2.  <span data-ttu-id="4d0c1-121">在**編輯**功能表上，按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-121">On the **Edit** menu, click **Delete**.</span></span>  
  
     <span data-ttu-id="4d0c1-122">您可以也按 DELETE 鍵，或以滑鼠右鍵按一下連結，然後按一下**刪除**快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-122">You can also press the DELETE key or right-click the link and click **Delete** on the shortcut menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d0c1-123">您可以大量選取多個連結和 (或) 運算質，然後用一道作業加以刪除。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-123">You can bulk-select multiple link(s) and/or functoid(s) and then delete them in one operation.</span></span> <span data-ttu-id="4d0c1-124">您可以復原或重做大量刪除連結和 (或) 運算質的動作。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-124">You can undo or redo the bulk deletion of link(s) and/or functoid(s).</span></span> <span data-ttu-id="4d0c1-125">復原和重做作業的詳細資訊，請參閱[如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="4d0c1-125">For more information about undo and redo operations, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d0c1-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d0c1-126">See Also</span></span>  
 [<span data-ttu-id="4d0c1-127">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="4d0c1-127">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)