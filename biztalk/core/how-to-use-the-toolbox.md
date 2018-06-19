---
title: 如何使用 [工具箱] |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipeline components, deleting from toolbox
- pipeline components, Pipeline Designer
- pipeline components, adding to toolbox
- Pipeline Designer, toolbox
- pipelines, creating
ms.assetid: 7a60c590-1a38-46fe-addf-0aa2c8b63cf9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3965a063aebcc932f07937fd19c3998412591ea1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257270"
---
# <a name="how-to-use-the-toolbox"></a><span data-ttu-id="2d372-102">如何使用工具箱</span><span class="sxs-lookup"><span data-stu-id="2d372-102">How to Use the Toolbox</span></span>
<span data-ttu-id="2d372-103">從工具箱拖曳元件 (圖形) 至設計介面以建立管線。</span><span class="sxs-lookup"><span data-stu-id="2d372-103">You create a pipeline by dragging components (shapes) from the Toolbox to the design surface.</span></span> <span data-ttu-id="2d372-104">「管線設計工具」藉由在建立程序中設定限制以協助您組合有效的管線。</span><span class="sxs-lookup"><span data-stu-id="2d372-104">Pipeline Designer helps you assemble valid pipelines by placing certain restrictions on the creation process.</span></span> <span data-ttu-id="2d372-105">您只能選取適用於您所建立的管線類型的工具箱元件。</span><span class="sxs-lookup"><span data-stu-id="2d372-105">You can only select Toolbox components that apply to the pipeline type you are creating.</span></span> <span data-ttu-id="2d372-106">例如，接收管線會將解碼器、解譯器和驗證器顯示為有效的工具箱元件，而編碼器和組合器則會停用 (變成灰色)。</span><span class="sxs-lookup"><span data-stu-id="2d372-106">For example, a receive pipeline will show decoders, disassemblers, and validators as valid Toolbox components, while encoders and assemblers will be disabled (dimmed).</span></span>  
  
 <span data-ttu-id="2d372-107">此外，階段只能接受有效的元件。</span><span class="sxs-lookup"><span data-stu-id="2d372-107">In addition, stages can accept only valid components.</span></span> <span data-ttu-id="2d372-108">例如，您無法將編碼器元件拖曳至組合階段。</span><span class="sxs-lookup"><span data-stu-id="2d372-108">For example, you cannot drag an encoder component to an Assemble stage.</span></span> <span data-ttu-id="2d372-109">當您拖曳元件接近有效的放置位置時，會出現箭頭以指示可插入元件的點。</span><span class="sxs-lookup"><span data-stu-id="2d372-109">When you drag a component near a valid drop location, an arrow appears, indicating the point where the component can be inserted.</span></span>  
  
 <span data-ttu-id="2d372-110">若您將有效的元件拖曳至摺疊的階段上，請在階段上暫停滑鼠游標數秒鐘以展開它，然後將元件放置到階段中。</span><span class="sxs-lookup"><span data-stu-id="2d372-110">If you drag a valid component onto a stage that is collapsed, pause the mouse over the stage for a few seconds to expand it, and then drop the component into the stage.</span></span>  
  
 <span data-ttu-id="2d372-111">在「管線設計師」中新增自訂元件至工具箱的動作與標準 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 程序相似。</span><span class="sxs-lookup"><span data-stu-id="2d372-111">Adding a custom component to the Toolbox in Pipeline Designer is similar to the standard Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] procedure.</span></span>  
  
 <span data-ttu-id="2d372-112">**開始和結束圖形**</span><span class="sxs-lookup"><span data-stu-id="2d372-112">**Start and End Shapes**</span></span>  
  
 <span data-ttu-id="2d372-113">**啟動**和**結束**圖形會顯示為在所有管線上的項目符號。</span><span class="sxs-lookup"><span data-stu-id="2d372-113">**Start** and **End** shapes appear as bullets on all pipelines.</span></span> <span data-ttu-id="2d372-114">它們會出現在設計介面上，僅供視覺組織之用。</span><span class="sxs-lookup"><span data-stu-id="2d372-114">They are provided on the design surface for visual organization only.</span></span> <span data-ttu-id="2d372-115">每種圖形只有一個，而且不能新增或刪除它們。</span><span class="sxs-lookup"><span data-stu-id="2d372-115">There is only one of each, and they can neither be added nor deleted.</span></span> <span data-ttu-id="2d372-116">**啟動**和**結束**圖形不會出現在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="2d372-116">The **Start** and **End** shapes do not appear in the Toolbox.</span></span>  
  
### <a name="to-add-a-pipeline-component-to-the-toolbox"></a><span data-ttu-id="2d372-117">新增管線元件至工具箱</span><span class="sxs-lookup"><span data-stu-id="2d372-117">To add a pipeline component to the Toolbox</span></span>  
  
1.  <span data-ttu-id="2d372-118">在 **[工具]** 功能表中按一下 **[選擇工具箱項目]**。</span><span class="sxs-lookup"><span data-stu-id="2d372-118">On the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
     <span data-ttu-id="2d372-119">-或者-</span><span class="sxs-lookup"><span data-stu-id="2d372-119">—Or—</span></span>  
  
     <span data-ttu-id="2d372-120">以滑鼠右鍵按一下 工具箱，然後按一下 **選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="2d372-120">Right-click the Toolbox and then click **Choose Items**.</span></span>  
  
2.  <span data-ttu-id="2d372-121">在**自訂工具箱**對話方塊中，按一下 [ **BizTalk 管線元件**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2d372-121">In the **Customize Toolbox** dialog box, click the **BizTalk Pipeline Components** tab.</span></span>  
  
     <span data-ttu-id="2d372-122">對話方塊會顯示相容的管線元件。</span><span class="sxs-lookup"><span data-stu-id="2d372-122">A dialog box displays the compatible pipeline components.</span></span> <span data-ttu-id="2d372-123">您可以按一下對話方塊上方的索引標籤在類別之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="2d372-123">You can navigate through the categories by clicking the tabs at the top of the dialog box.</span></span>  
  
3.  <span data-ttu-id="2d372-124">選取您要新增至工具箱的元件。</span><span class="sxs-lookup"><span data-stu-id="2d372-124">Select the component you want to add to the Toolbox.</span></span>  
  
4.  <span data-ttu-id="2d372-125">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2d372-125">Click **OK**.</span></span> <span data-ttu-id="2d372-126">此元件將會出現在**BizTalk 管線元件**工具箱索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2d372-126">The component will appear on the **BizTalk Pipeline Components** tab of the Toolbox.</span></span>  
  
### <a name="to-remove-a-pipeline-component-from-the-toolbox"></a><span data-ttu-id="2d372-127">從工具箱移除管線元件</span><span class="sxs-lookup"><span data-stu-id="2d372-127">To remove a pipeline component from the Toolbox</span></span>  
  
-   <span data-ttu-id="2d372-128">開啟**自訂工具箱**對話方塊 （如同前述程序），然後清除要移除的元件。</span><span class="sxs-lookup"><span data-stu-id="2d372-128">Open the **Customize Toolbox** dialog box (as in the preceding procedure) and clear the component to be removed.</span></span>  
  
     <span data-ttu-id="2d372-129">即使元件已從工具箱移除，它仍然保持已註冊狀態。</span><span class="sxs-lookup"><span data-stu-id="2d372-129">A component remains registered even after it has been removed from the Toolbox.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d372-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d372-130">See Also</span></span>  
 <span data-ttu-id="2d372-131">[如何建立新的管線](../core/how-to-create-a-new-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="2d372-131">[How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md) </span></span>  
 <span data-ttu-id="2d372-132">[如何開啟管線](../core/how-to-open-a-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="2d372-132">[How to Open a Pipeline](../core/how-to-open-a-pipeline.md) </span></span>  
 <span data-ttu-id="2d372-133">[如何使用鍵盤巡覽](../core/how-to-navigate-with-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="2d372-133">[How to Navigate with the Keyboard](../core/how-to-navigate-with-the-keyboard.md) </span></span>  
 [<span data-ttu-id="2d372-134">使用管線設計師建立管線</span><span class="sxs-lookup"><span data-stu-id="2d372-134">Creating Pipelines with Pipeline Designer</span></span>](../core/creating-pipelines-with-pipeline-designer.md)