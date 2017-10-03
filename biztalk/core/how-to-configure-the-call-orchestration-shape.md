---
title: "如何設定呼叫協調流程圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Orchestration shape [Orchestration Designer], parameters
- Call Orchestration shape [Orchestration Designer], configuring
- Call Orchestration shape [Orchestration Designer], about Call Orchestration shapes
- configuring [Orchestration Designer], Call Orchestration shapes
- Call Orchestration shape [Orchestration Designer]
- nonserializable objects
- orchestrations, nonserializable objects
- Call Orchestration shape [Orchestration Designer], referencing orchestrations
- orchestrations, parameters
ms.assetid: 718ce2a0-ac08-4662-8b4e-1be279dbc749
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dabb73b3bed616f17c69923799169a7c6ca2b6d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-call-orchestration-shape"></a><span data-ttu-id="2961c-102">如何設定呼叫協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="2961c-102">How to Configure the Call Orchestration Shape</span></span>
<span data-ttu-id="2961c-103">**呼叫協調流程**圖形可以用來同步呼叫另一個專案中參考的協調流程。</span><span class="sxs-lookup"><span data-stu-id="2961c-103">The **Call Orchestration** shape can be used to synchronously call an orchestration that is referenced in another project.</span></span> <span data-ttu-id="2961c-104">如此可在 BizTalk 專案之間重複使用共同的協調流程工作流程模式。</span><span class="sxs-lookup"><span data-stu-id="2961c-104">This allows for reuse of common orchestration workflow patterns across BizTalk projects.</span></span> <span data-ttu-id="2961c-105">當您叫用另一個巢狀的協調流程的狀況下同步**呼叫協調流程**圖形封閉式協調流程會等待巢狀協調流程完成後再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="2961c-105">When you invoke another nested orchestration synchronously with the **Call Orchestration** shape the enclosing orchestration waits for the nested orchestration to finish before continuing.</span></span>  
  
 <span data-ttu-id="2961c-106">您可以指定將傳遞給巢狀協調流程的參數。</span><span class="sxs-lookup"><span data-stu-id="2961c-106">You can specify parameters that will be passed to the nested orchestration.</span></span> <span data-ttu-id="2961c-107">參數可以是訊息、變數、連接埠參考、角色連結或相互關聯集。</span><span class="sxs-lookup"><span data-stu-id="2961c-107">Parameters can be messages, variables, port references, role links, or correlation sets.</span></span> <span data-ttu-id="2961c-108">傳入的連接埠參考、 角色連結和相互關聯集的所有執行像自我定址信封相同： 他們提供它可以用來將資訊傳送回封閉式協調流程的巢狀協調流程資訊。</span><span class="sxs-lookup"><span data-stu-id="2961c-108">Passed-in port references, role links, and correlation sets all perform like self-addressed envelopes: they supply the nested orchestration information it can use to send information back to the enclosing orchestration.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2961c-109">如果您將不可序列化的物件 (如 XmlDocument 或 XmlNode) 當做參數傳遞給協調流程，它將會失敗。</span><span class="sxs-lookup"><span data-stu-id="2961c-109">If you pass nonserializable objects such as XmlDocument or XmlNode as parameters to an orchestration, it will fail.</span></span>  
  
 <span data-ttu-id="2961c-110">如需如何使用的範例**呼叫協調流程**圖形，請參閱[CallOrchestration （BizTalk Server 範例）](../core/callorchestration-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="2961c-110">For an example of how to use **Call Orchestration** shape, see [CallOrchestration (BizTalk Server Sample)](../core/callorchestration-biztalk-server-sample.md).</span></span>  
  
### <a name="to-configure-a-call-orchestration-shape"></a><span data-ttu-id="2961c-111">若要設定呼叫協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="2961c-111">To configure a Call Orchestration shape</span></span>  
  
1.  <span data-ttu-id="2961c-112">使用**協調流程選取**下拉式清單方塊中，選取清單中的協調流程。</span><span class="sxs-lookup"><span data-stu-id="2961c-112">Using the **Orchestration Selection** drop-down list box, select an orchestration from the list.</span></span>  
  
2.  <span data-ttu-id="2961c-113">使用**協調流程參數**方格控制項，指定要傳遞至協調流程的引數 — 如同在中指定**協調流程選取**下拉式清單方塊-，而呼叫。</span><span class="sxs-lookup"><span data-stu-id="2961c-113">Using the **Orchestration Parameters** grid control, specify arguments to pass to the orchestration—as specified in the **Orchestration Selection** drop-down list box—that is called.</span></span> <span data-ttu-id="2961c-114">您可以輸入變數名稱或按一下儲存格下拉式清單中的變數，在 [變數] 資料行的儲存格中指定這些引數，每個儲存格一個變數。</span><span class="sxs-lookup"><span data-stu-id="2961c-114">You specify these arguments in the cells of the Variable column, one variable per cell, by typing the name of a variable or clicking a variable from a drop-down list in a cell.</span></span>  
  
3.  <span data-ttu-id="2961c-115">若要設定**呼叫協調流程**圖形根據服務和您在對話方塊中指定的引數，請按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2961c-115">To configure the **Call Orchestration** shape according to the service and arguments that you specified in the dialog box, click **OK**.</span></span> <span data-ttu-id="2961c-116">若要關閉**呼叫協調流程組態**對話方塊而不進行任何變更**呼叫協調流程**圖形，請按一下**取消**。</span><span class="sxs-lookup"><span data-stu-id="2961c-116">To close the **Call Orchestration Configuration** dialog box without making any changes to the **Call Orchestration** shape, click **Cancel**.</span></span>  
  
    > [!CAUTION]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2961c-117"> 不支援遞迴協調流程。</span><span class="sxs-lookup"><span data-stu-id="2961c-117"> does not support recursive orchestrations.</span></span> <span data-ttu-id="2961c-118">若協調流程 A 呼叫或啟動協調流程 B，則協調流程 B 就不能直接呼叫或啟動協調流程 A，而且它也不能呼叫或啟動直接或間接呼叫協調流程 A 的任何協調流程。</span><span class="sxs-lookup"><span data-stu-id="2961c-118">If Orchestration A calls or starts Orchestration B, then Orchestration B cannot call or start Orchestration A directly, nor can it call or start any orchestration that directly or indirectly calls Orchestration A.</span></span>  
  
## <a name="referenced-orchestrations"></a><span data-ttu-id="2961c-119">被參考的協調流程</span><span class="sxs-lookup"><span data-stu-id="2961c-119">Referenced Orchestrations</span></span>  
 <span data-ttu-id="2961c-120">為了要能夠呼叫被參考的協調流程，請確保已經設定被呼叫端協調流程的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="2961c-120">For the referenced orchestration to be callable, ensure that the following properties have been configured for the called orchestration:</span></span>  
  
-   <span data-ttu-id="2961c-121">設定**型別修飾詞**屬性**公用**呼叫之協調流程。</span><span class="sxs-lookup"><span data-stu-id="2961c-121">Set the **Type Modifier** property to **Public** for the called orchestration.</span></span> <span data-ttu-id="2961c-122">若要設定**型別修飾詞**協調流程屬性**公用**，開啟協調流程在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按一下綠色開始 」 圖形頂端的顯示協調流程**協調流程屬性**對話方塊，並設定**型別修飾詞**屬性**公用**。</span><span class="sxs-lookup"><span data-stu-id="2961c-122">To set the **Type Modifier** property for an orchestration to **Public**, open the orchestration in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], click the green start shape at the top of the orchestration to display the **Orchestration Properties** dialog and set the **Type Modifier** property to **Public**.</span></span>  
  
-   <span data-ttu-id="2961c-123">設定**Activate**中初始接收圖形的協調流程屬性**False**。</span><span class="sxs-lookup"><span data-stu-id="2961c-123">Set the **Activate** property of the initial receive shape in the orchestration to **False**.</span></span>  
  
## <a name="orchestration-selection-drop-down-list-box"></a><span data-ttu-id="2961c-124">協調流程選取下拉式清單方塊</span><span class="sxs-lookup"><span data-stu-id="2961c-124">Orchestration Selection drop-down list box</span></span>  
 <span data-ttu-id="2961c-125">按一下下拉式清單方塊中的向下箭號，檢視可用的服務並從中選取一個服務。</span><span class="sxs-lookup"><span data-stu-id="2961c-125">Click the Down arrow in the drop-down list box to view available services and select one.</span></span> <span data-ttu-id="2961c-126">此清單包含可以從目前協調流程中呼叫的所有服務，包含被參考的組件。</span><span class="sxs-lookup"><span data-stu-id="2961c-126">This list contains all the services that can be called from the current orchestration, including referenced assemblies.</span></span>  
  
## <a name="orchestration-parameters-grid-control"></a><span data-ttu-id="2961c-127">協調流程參數方格控制項</span><span class="sxs-lookup"><span data-stu-id="2961c-127">Orchestration Parameters grid control</span></span>  
 <span data-ttu-id="2961c-128">指定要傳遞給參數化的協調流程所使用的引數**協調流程參數**方格控制項。</span><span class="sxs-lookup"><span data-stu-id="2961c-128">You specify the arguments to pass to a parameterized orchestration by using the **Orchestration Parameters** grid control.</span></span> <span data-ttu-id="2961c-129">此方格有四個資料行： 範圍中，參數名稱、 參數類型，以及參數方向中的變數。</span><span class="sxs-lookup"><span data-stu-id="2961c-129">The grid has four columns: Variables in Scope, Parameter Name, Parameter Type, and Parameter Direction.</span></span> <span data-ttu-id="2961c-130">您只能在第一個資料行進行變更，其他是唯讀的資料行。</span><span class="sxs-lookup"><span data-stu-id="2961c-130">You can make changes only in the first column; the other columns are read-only.</span></span>  
  
 <span data-ttu-id="2961c-131">當您選取有效的協調流程時，其參數會填入方格控制項的參數名稱、類型及方向欄。</span><span class="sxs-lookup"><span data-stu-id="2961c-131">When you select a valid orchestration, its parameters populate the parameter name, type and direction columns of the grid control.</span></span> <span data-ttu-id="2961c-132">然後，在每一個資料列中選取要當做引數傳遞的變數。</span><span class="sxs-lookup"><span data-stu-id="2961c-132">You then select the variables in each row to pass as arguments.</span></span> <span data-ttu-id="2961c-133">您可以從 [範圍內的變數] 資料行中每個儲存格的下拉式清單選取這些變數。</span><span class="sxs-lookup"><span data-stu-id="2961c-133">You select these variables from a drop-down list present in each cell in the Variables in Scope column.</span></span> <span data-ttu-id="2961c-134">此清單會顯示相鄰的 [參數類型] 儲存格中所指定之類型的所有可用變數。</span><span class="sxs-lookup"><span data-stu-id="2961c-134">This list displays all the available variables of the type specified in the adjacent Parameter Type cell.</span></span> <span data-ttu-id="2961c-135">若該類型只有一個可用物件，則 [範圍內的變數] 儲存格會自動填入該物件。</span><span class="sxs-lookup"><span data-stu-id="2961c-135">If only one object of that type is available, the Variables in Scope cell is automatically populated with that object.</span></span> <span data-ttu-id="2961c-136">您也可以在 [範圍內的變數] 儲存格中進行輸入，以選取下拉式清單中可用的變數。</span><span class="sxs-lookup"><span data-stu-id="2961c-136">You can also type in a Variables in Scope cell to select a variable that is available in the drop-down list.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2961c-137">因為**呼叫協調流程**圖形會呼叫協調流程中，[協調流程參數] 您在此對話方塊中選取實際上指的協調流程變數。</span><span class="sxs-lookup"><span data-stu-id="2961c-137">Because a **Call Orchestration** shape calls an orchestration, the "Orchestration Parameters" you select in this dialog box actually refer to orchestration variables.</span></span>  
  
 <span data-ttu-id="2961c-138">如果您正在呼叫的協調流程沒有已定義的參數，則此對話方塊中的方格控制項無法使用。</span><span class="sxs-lookup"><span data-stu-id="2961c-138">If an orchestration you are calling has no defined parameters, the grid control in this dialog box is unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2961c-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2961c-139">See Also</span></span>  
 [<span data-ttu-id="2961c-140">如何設定啟動協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="2961c-140">How to Configure the Start Orchestration Shape</span></span>](../core/how-to-configure-the-start-orchestration-shape.md)