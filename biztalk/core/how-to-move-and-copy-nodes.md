---
title: 如何移動和複製節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4f1ec14-c607-4da3-9139-73a61963b819
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a55901e9ba6b27d05dccce0e547df618123ab466
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254766"
---
# <a name="how-to-move-and-copy-nodes"></a><span data-ttu-id="bd999-102">如何移動和複製節點</span><span class="sxs-lookup"><span data-stu-id="bd999-102">How to Move and Copy Nodes</span></span>
<span data-ttu-id="bd999-103">您可能會遇到需要移動現有節點至結構描述樹狀結構中不同位置的情況。</span><span class="sxs-lookup"><span data-stu-id="bd999-103">You will probably encounter situations where you want to move an existing node to a different location in the schema tree.</span></span> <span data-ttu-id="bd999-104">您也可以在結構描述樹狀結構中複製現有的節點，然後將它貼到不同的位置來節省時間。</span><span class="sxs-lookup"><span data-stu-id="bd999-104">You might also be able to save time by making a copy of an existing node and then pasting it into a different location in the schema tree.</span></span> <span data-ttu-id="bd999-105">本主題提供執行這些工作的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="bd999-105">This topic provides step-by-step instructions for performing these tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd999-106">BizTalk 編輯器僅支援在結構描述內複製和貼上節點，而不支援在結構描述之間執行這些動作。</span><span class="sxs-lookup"><span data-stu-id="bd999-106">BizTalk Editor supports copying and pasting nodes only within schemas, not between schemas.</span></span>  
  
### <a name="to-move-a-node-within-a-schema"></a><span data-ttu-id="bd999-107">移動結構描述中的節點</span><span class="sxs-lookup"><span data-stu-id="bd999-107">To move a node within a schema</span></span>  
  
1.  <span data-ttu-id="bd999-108">如有必要，展開結構描述樹狀結構以顯示您要移動的節點以及您要將它移動到的位置。</span><span class="sxs-lookup"><span data-stu-id="bd999-108">If necessary, expand the schema tree to show both the node you are moving and the location to which you want to move it.</span></span> <span data-ttu-id="bd999-109">如需有關展開和摺疊結構描述樹狀檢視的詳細資訊，請參閱[管理結構描述樹狀結構檢視](../core/how-to-manage-the-schema-tree-view.md)。</span><span class="sxs-lookup"><span data-stu-id="bd999-109">For more information about expanding and collapsing the schema tree view, see [Managing the Schema Tree View](../core/how-to-manage-the-schema-tree-view.md).</span></span>  
  
2.  <span data-ttu-id="bd999-110">按住您要移動的節點，將它拖曳到樹狀結構中的另一個位置。</span><span class="sxs-lookup"><span data-stu-id="bd999-110">Click and hold the node that you want to move and drag it to another location in the tree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd999-111">當您開始在結構描述樹狀結構中往上和往下拖曳時，滑鼠指標會變更為向上、向下或是子箭頭。</span><span class="sxs-lookup"><span data-stu-id="bd999-111">When you begin to drag the node up and down the schema tree, the mouse pointer changes to an Up, Down, or child arrow.</span></span> <span data-ttu-id="bd999-112">此箭頭表示當您釋放滑鼠按鈕時要放置節點的位置，也就是節點之前、節點之後或是做為節點的子系。</span><span class="sxs-lookup"><span data-stu-id="bd999-112">This arrow indicates where the node will be placed when you release the mouse button, either before the node, after the node, or as a child of the node.</span></span>  
  
#### <a name="to-copy-a-node-within-a-schema"></a><span data-ttu-id="bd999-113">複製結構描述中的節點</span><span class="sxs-lookup"><span data-stu-id="bd999-113">To copy a node within a schema</span></span>  
  
1.  <span data-ttu-id="bd999-114">以滑鼠右鍵按一下您想要複製，，然後按一下節點**複製**。</span><span class="sxs-lookup"><span data-stu-id="bd999-114">Right-click the node that you want to copy, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="bd999-115">以滑鼠右鍵按一下**記錄**節點或群組節點要插入複製的節點，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="bd999-115">Right-click the **Record** node or group node into which you want to insert the copied node, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="bd999-116">複製的節點複本放置在的子節點結尾處**記錄**節點或您在步驟 2 中選取的群組節點。</span><span class="sxs-lookup"><span data-stu-id="bd999-116">The copy of the copied node is placed at the end of the child nodes of the **Record** node or group node you selected in step 2.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd999-117">您只能在單一結構描述中使用剪下/複製/貼上功能。</span><span class="sxs-lookup"><span data-stu-id="bd999-117">You may only use cut/copy/paste functionality within a single schema.</span></span> <span data-ttu-id="bd999-118">換句話說，您不能從某個結構描述複製節點到另一個結構描述。</span><span class="sxs-lookup"><span data-stu-id="bd999-118">In other words, you cannot copy nodes from one schema into another schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd999-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd999-119">See Also</span></span>  
 [<span data-ttu-id="bd999-120">使用現有的節點</span><span class="sxs-lookup"><span data-stu-id="bd999-120">Working with Existing Nodes</span></span>](../core/working-with-existing-nodes.md)