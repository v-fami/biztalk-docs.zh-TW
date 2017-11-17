---
title: "如何設定啟動協調流程圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Start Orchestration shapes
- Start Orchestration shape [Orchestration Designer], parameters
- Start Orchestration shape [Orchestration Designer], configuring
- orchestrations, starting
- Start Orchestration shape [Orchestration Designer]
- Start Orchestration shape [Orchestration Designer], starting orchestrations
- Start Orchestration shape [Orchestration Designer], about Star Orchestration shape
ms.assetid: 9d01c41e-9bc5-4c1c-a869-b2f0df13036a
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f8181849b700939ba86f55cd372b80ed2ebf70e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-start-orchestration-shape"></a><span data-ttu-id="715ea-102">如何設定啟動協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="715ea-102">How to Configure the Start Orchestration Shape</span></span>
<span data-ttu-id="715ea-103">**啟動協調流程**圖形是類似於**呼叫協調流程**圖形，但您叫用另一個協調流程，以非同步方式與**啟動協調流程**圖形 — 也就是叫用的協調流程中的控制流程會繼續超出引動過程，而不需等待叫用的協調流程完成其工作。</span><span class="sxs-lookup"><span data-stu-id="715ea-103">The **Start Orchestration** shape is similar to the **Call Orchestration** shape, but you invoke another orchestration asynchronously with the **Start Orchestration** shape—that is, the flow of control in the invoking orchestration proceeds beyond the invocation, without waiting for the invoked orchestration to finish its work.</span></span>  
  
 <span data-ttu-id="715ea-104">您可以指定將傳遞給被叫用之協調流程的參數。</span><span class="sxs-lookup"><span data-stu-id="715ea-104">You can specify parameters that will be passed to the invoked orchestration.</span></span> <span data-ttu-id="715ea-105">參數可以是訊息、變數、連接埠參考、角色連結或相互關聯集。</span><span class="sxs-lookup"><span data-stu-id="715ea-105">Parameters can be messages, variables, port references, role links, or correlation sets.</span></span> <span data-ttu-id="715ea-106">**啟動協調流程**圖形只能採用*中*參數; 否則它無法使用*出*或*ref*參數。</span><span class="sxs-lookup"><span data-stu-id="715ea-106">The **Start Orchestration** shape can only take *in* parameters; it cannot take *out* or *ref* parameters.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="715ea-107">如果您將不可序列化的物件 (如 XmlDocument 或 XmlNode) 當做參數傳遞給此協調流程，它將會失敗。</span><span class="sxs-lookup"><span data-stu-id="715ea-107">If you pass non-serializable objects such as XmlDocument or XmlNode as parameters to an orchestration, it will fail.</span></span>  
  
 <span data-ttu-id="715ea-108">**啟動協調流程**圖形是在其中您可以做為參數傳遞的連接埠反轉極性的唯一圖形 — 例如*使用*叫用的協調流程，以將傳入通訊埠 （傳送埠）但在叫用的協調流程可以將它視為*實作*連接埠 （接收埠）。</span><span class="sxs-lookup"><span data-stu-id="715ea-108">The **Start Orchestration** shape is the only shape in which you can reverse the polarity on a port being passed as a parameter—for example a *uses* port (send port) can be passed in to an invoked orchestration, but the invoked orchestration can treat it as an *implements* port (receive port).</span></span> <span data-ttu-id="715ea-109">請注意，只有使用直接繫結的連接埠才可以這樣處理。</span><span class="sxs-lookup"><span data-stu-id="715ea-109">Note that this can only be done with ports that use direct binding.</span></span>  
  
 <span data-ttu-id="715ea-110">**啟動協調流程**圖形也可用來呼叫在另一個專案中參考的協調流程。</span><span class="sxs-lookup"><span data-stu-id="715ea-110">The **Start Orchestration** shape can also be used to call an orchestration that is referenced in another project.</span></span> <span data-ttu-id="715ea-111">如此可在 BizTalk 專案之間重複使用共同的協調流程工作流程模式。</span><span class="sxs-lookup"><span data-stu-id="715ea-111">This allows for reuse of common orchestration workflow patterns across BizTalk projects.</span></span> <span data-ttu-id="715ea-112">為了要能夠呼叫參考的協調流程，請確認**型別修飾詞**呼叫之協調流程屬性設定為**公用**。</span><span class="sxs-lookup"><span data-stu-id="715ea-112">For the referenced orchestration to be callable, ensure that the **Type Modifier** property for the called orchestration is set to **Public**.</span></span> <span data-ttu-id="715ea-113">若要設定**型別修飾詞**協調流程屬性**公用**，開啟協調流程在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按一下綠色開始 」 圖形頂端的顯示協調流程**協調流程屬性**對話方塊，並設定**型別修飾詞**屬性**公用**。</span><span class="sxs-lookup"><span data-stu-id="715ea-113">To set the **Type Modifier** property for an orchestration to **Public**, open the orchestration in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], click the green start shape at the top of the orchestration to display the **Orchestration Properties** dialog and set the **Type Modifier** property to **Public**.</span></span> <span data-ttu-id="715ea-114">預設值為**型別修飾詞**是**私人**。</span><span class="sxs-lookup"><span data-stu-id="715ea-114">The default value for **Type Modifier** is **Private**.</span></span>  
  
 <span data-ttu-id="715ea-115">如需如何使用的範例**啟動協調流程**圖形，請從下載 SDK 範例 「 實作 Scatter and Gather Pattern" [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="715ea-115">For an example of how to use **Start Orchestration** shape, download the SDK sample "Implementing Scatter and Gather Pattern" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
### <a name="to-configure-a-start-orchestration-shape"></a><span data-ttu-id="715ea-116">設定啟動協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="715ea-116">To configure a Start Orchestration shape</span></span>  
  
1.  <span data-ttu-id="715ea-117">使用**協調流程選取**下拉式清單方塊中，選取清單中的協調流程。</span><span class="sxs-lookup"><span data-stu-id="715ea-117">Using the **Orchestration Selection** drop-down list box, select an orchestration from the list.</span></span>  
  
2.  <span data-ttu-id="715ea-118">使用**協調流程參數**方格控制項，指定要傳遞至協調流程的引數 — 如同在中指定**協調流程選取**下拉式清單方塊-啟動的。</span><span class="sxs-lookup"><span data-stu-id="715ea-118">Using the **Orchestration Parameters** grid control, specify arguments to pass to the orchestration—as specified in the **Orchestration Selection** drop-down list box—that is started.</span></span> <span data-ttu-id="715ea-119">您可以輸入變數名稱或按一下儲存格下拉式清單中的變數，在 [變數] 資料行的儲存格中指定這些引數，每個儲存格一個變數。</span><span class="sxs-lookup"><span data-stu-id="715ea-119">You specify these arguments in the cells of the Variable column, one variable per cell, by typing the name of a variable or clicking a variable from a drop-down list in a cell.</span></span>  
  
3.  <span data-ttu-id="715ea-120">若要設定**啟動協調流程**圖形根據服務和您在對話方塊中指定的引數，請按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="715ea-120">To configure the **Start Orchestration** shape according to the service and arguments that you specified in the dialog box, click **OK**.</span></span> <span data-ttu-id="715ea-121">若要關閉**啟動協調流程組態**對話方塊而不進行任何變更**啟動協調流程**圖形，請按一下**取消**。</span><span class="sxs-lookup"><span data-stu-id="715ea-121">To close the **Start Orchestration Configuration** dialog box without making any changes to the **Start Orchestration** shape, click **Cancel**.</span></span>  
  
    > [!CAUTION]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="715ea-122"> 不支援遞迴協調流程。</span><span class="sxs-lookup"><span data-stu-id="715ea-122"> does not support recursive orchestrations.</span></span> <span data-ttu-id="715ea-123">若協調流程 A 呼叫或啟動協調流程 B，則協調流程 B 就不能直接呼叫或啟動協調流程 A，而且它也不能呼叫或啟動直接或間接呼叫協調流程 A 的任何協調流程。</span><span class="sxs-lookup"><span data-stu-id="715ea-123">If Orchestration A calls or starts Orchestration B, then Orchestration B cannot call or start Orchestration A directly, nor can it call or start any orchestration that directly or indirectly calls Orchestration A.</span></span>  
  
## <a name="orchestration-selection-drop-down-list-box"></a><span data-ttu-id="715ea-124">協調流程選取下拉式清單方塊</span><span class="sxs-lookup"><span data-stu-id="715ea-124">Orchestration Selection drop-down list box</span></span>  
 <span data-ttu-id="715ea-125">按一下下拉式清單方塊中的向下箭號，以檢視可用的協調流程並從中選取一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="715ea-125">Click the Down arrow in the drop-down list box to view available orchestrations and select one.</span></span> <span data-ttu-id="715ea-126">此清單包含可以從目前協調流程中啟動的所有協調流程，包含參考的組件。</span><span class="sxs-lookup"><span data-stu-id="715ea-126">This list contains all the orchestrations that can be started from the current orchestration, including referenced assemblies.</span></span>  
  
## <a name="orchestration-parameters-grid-control"></a><span data-ttu-id="715ea-127">協調流程參數方格控制項</span><span class="sxs-lookup"><span data-stu-id="715ea-127">Orchestration Parameters grid control</span></span>  
 <span data-ttu-id="715ea-128">指定要傳遞給參數化的協調流程所使用的引數**協調流程參數**方格控制項。</span><span class="sxs-lookup"><span data-stu-id="715ea-128">You specify the arguments to pass to a parameterized orchestration by using the **Orchestration Parameters** grid control.</span></span> <span data-ttu-id="715ea-129">此方格有四個資料行： 範圍中，參數名稱、 參數類型，以及參數方向中的變數。</span><span class="sxs-lookup"><span data-stu-id="715ea-129">The grid has four columns: Variables in Scope, Parameter Name, Parameter Type, and Parameter Direction.</span></span> <span data-ttu-id="715ea-130">您只能在第一個資料行進行變更，其他是唯讀的資料行。</span><span class="sxs-lookup"><span data-stu-id="715ea-130">You can make changes only in the first column; the other columns are read-only.</span></span>  
  
 <span data-ttu-id="715ea-131">當您選取有效的協調流程時，其參數會填入參數名稱、類型以及方格控制項的方向資料行。</span><span class="sxs-lookup"><span data-stu-id="715ea-131">When you select a valid orchestration, its parameters populate the parameter name, type, and direction columns of the grid control.</span></span> <span data-ttu-id="715ea-132">然後，在每一個資料列中選取要當做引數傳遞的變數。</span><span class="sxs-lookup"><span data-stu-id="715ea-132">You then select the variables in each row to pass as arguments.</span></span> <span data-ttu-id="715ea-133">您可以從 [範圍內的變數] 資料行中每個儲存格的下拉式清單選取這些變數。</span><span class="sxs-lookup"><span data-stu-id="715ea-133">You select these variables from a drop-down list present in each cell in the Variables in Scope column.</span></span> <span data-ttu-id="715ea-134">此清單會顯示相鄰的 [參數類型] 儲存格中所指定之類型的所有可用變數。</span><span class="sxs-lookup"><span data-stu-id="715ea-134">This list displays all the available variables of the type specified in the adjacent Parameter Type cell.</span></span> <span data-ttu-id="715ea-135">若該類型只有一個可用物件，則 [範圍內的變數] 儲存格會自動填入該物件。</span><span class="sxs-lookup"><span data-stu-id="715ea-135">If only one object of that type is available, the Variables in Scope cell is automatically populated with that object.</span></span> <span data-ttu-id="715ea-136">您也可以在 [範圍內的變數] 儲存格中進行輸入，以選取下拉式清單中可用的變數。</span><span class="sxs-lookup"><span data-stu-id="715ea-136">You can also type in a Variables in Scope cell to select a variable that is available in the drop-down list.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="715ea-137">因為**啟動協調流程**圖形啟動協調流程，[協調流程參數] 您在此對話方塊中選取實際上指的協調流程變數。</span><span class="sxs-lookup"><span data-stu-id="715ea-137">Because a **Start Orchestration** shape starts an orchestration, the "Orchestration Parameters" you select in this dialog box actually refer to orchestration variables.</span></span>  
  
 <span data-ttu-id="715ea-138">若您正在執行的協調流程沒有定義的參數，則此對話方塊中的方格控制項無法使用。</span><span class="sxs-lookup"><span data-stu-id="715ea-138">If an orchestration you are executing has no defined parameters, the grid control in this dialog box is unavailable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="715ea-139">本節內容</span><span class="sxs-lookup"><span data-stu-id="715ea-139">In This Section</span></span>  
 [<span data-ttu-id="715ea-140">如何建立接收端叫用的協調流程訂閱</span><span class="sxs-lookup"><span data-stu-id="715ea-140">How to Create Receive Subscriptions at Invoked Orchestrations</span></span>](../core/how-to-create-receive-subscriptions-at-invoked-orchestrations.md) 
  
## <a name="see-also"></a><span data-ttu-id="715ea-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="715ea-141">See Also</span></span>  
 [<span data-ttu-id="715ea-142">如何設定呼叫協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="715ea-142">How to Configure the Call Orchestration Shape</span></span>](../core/how-to-configure-the-call-orchestration-shape.md)