---
title: 如何設定運算質輸入參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bts10.mapper.functoid.inputs
ms.assetid: 2c8f773a-932c-423d-b3fe-724265304b0a
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69048e7ec60ad723a8393c745ccd17c8cdd4bd16
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999791"
---
# <a name="how-to-configure-functoid-input-parameters"></a><span data-ttu-id="1956a-102">如何設定運算質輸入參數</span><span class="sxs-lookup"><span data-stu-id="1956a-102">How to Configure Functoid Input Parameters</span></span>
<span data-ttu-id="1956a-103">正確的設定對應中的運算質輸入參數，是在使用運算質時最重要也是最可能防止發生錯誤的其中一個方式。</span><span class="sxs-lookup"><span data-stu-id="1956a-103">Properly configuring the input parameters to the functoids in your map is one of the most important, and potentially error-prone, aspects of using functoids.</span></span> <span data-ttu-id="1956a-104">您可以設定運算質輸入參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1956a-104">You can configure the functoid input parameters as follows:</span></span>  
  
- <span data-ttu-id="1956a-105">建立藉由連接結構描述節點與個別運算質 （拖放滑鼠從結構描述節點的運算質） 的可見輸入的連結。</span><span class="sxs-lookup"><span data-stu-id="1956a-105">Create visible input links by connecting schema nodes and respective functoids (drag-and-drop the mouse from schema node to the functoid).</span></span>  
  
- <span data-ttu-id="1956a-106">直接編輯輸入參數使用的清單**設定\<運算質\>運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1956a-106">Directly edit the list of input parameters using the **Configure \<Functoid\> Functoid** dialog box.</span></span>  
  
  <span data-ttu-id="1956a-107">此主題會逐步說明使用這些方法設定運算質的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="1956a-107">This topic provides step-by-step instructions for configuring the input parameters for a functoid using these methods.</span></span>  
  
  <span data-ttu-id="1956a-108">使用拖曳方式建立運算質輸入參數，可方便您將與 XPath 規格有關的輸入參數指定給來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="1956a-108">The dragging method of establishing functoid input parameters provides a convenient way to specify input parameters that involve XPath specifications into the source schema.</span></span> <span data-ttu-id="1956a-109">如需建立結構描述節點與運算質的輸入的參數的詳細資訊，請參閱[如何新增基本運算質加入至地圖](../core/how-to-add-basic-functoids-to-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="1956a-109">For information on creating a schema node and functoid input parameters, see [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md).</span></span> <span data-ttu-id="1956a-110">不過，**設定\<運算質\>運算質**對話方塊是用來檢視所有運算質的輸入的參數、 建立和修改任何常數參數，以及決定機制重新排列輸入參數時所需的順序。</span><span class="sxs-lookup"><span data-stu-id="1956a-110">However, the **Configure \<Functoid\> Functoid** dialog box is the definitive mechanism for viewing all the input parameters to a functoid, for creating and modifying any constant parameters, and for re-arranging the order of the input parameters when necessary.</span></span>  
  
  <span data-ttu-id="1956a-111">當您在格線頁上直接設定運算質的輸入參數 (繪製線條、從結構描述節點拖放滑鼠，然後連結至運算質) 時，如果輸入數目達到上限，游標就會變更成「無」狀態。</span><span class="sxs-lookup"><span data-stu-id="1956a-111">When you configure the input parameters for a functoid directly on the grid page (by drawing lines, using the mouse drag-and-drop, from the source schema node and linking it to the functoid), if the number of inputs reaches maximum, the cursor changes to a NO state.</span></span> <span data-ttu-id="1956a-112">此外，狀態列會顯示該原因。</span><span class="sxs-lookup"><span data-stu-id="1956a-112">Also, the status bar displays the reason.</span></span> <span data-ttu-id="1956a-113">下圖顯示只接受一個輸入連結的運算質。</span><span class="sxs-lookup"><span data-stu-id="1956a-113">The figure below shows a functoid which accepts only one input link.</span></span>  
  
  <span data-ttu-id="1956a-114">![設定運算質輸入的參數無狀態](../core/media/configure-input-parameters-no-state.gif "Configure_input_parameters_NO_state")</span><span class="sxs-lookup"><span data-stu-id="1956a-114">![NO state for configuring functoid input parameter](../core/media/configure-input-parameters-no-state.gif "Configure_input_parameters_NO_state")</span></span>  
  
  <span data-ttu-id="1956a-115">您可以設定使用的指令碼處理 」 和 「 表格迴圈運算質**設定\<運算質\>運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1956a-115">You can configure the Scripting and Table Looping functoids using the **Configure \<Functoid\> Functoid** dialog box.</span></span> <span data-ttu-id="1956a-116">如需如何設定運算質的詳細資訊，請參閱[如何設定指令碼處理運算質](../core/how-to-configure-the-scripting-functoid.md)並[如何設定表格迴圈和表格擷取程式運算質](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="1956a-116">For information about how to configure the functoids, see [How to Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md) and [How to Configure the Table Looping and Table Extractor Functoids](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1956a-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="1956a-117">Prerequisites</span></span>  
 <span data-ttu-id="1956a-118">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="1956a-118">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="what-is-an-input-parameter"></a><span data-ttu-id="1956a-119">什麼是輸入參數？</span><span class="sxs-lookup"><span data-stu-id="1956a-119">What is an input parameter?</span></span>  
 <span data-ttu-id="1956a-120">輸入參數可以是下列任何一項：</span><span class="sxs-lookup"><span data-stu-id="1956a-120">An input parameter can be any of the following:</span></span>  
  
-   <span data-ttu-id="1956a-121">從來源結構描述節點連至運算質的連結</span><span class="sxs-lookup"><span data-stu-id="1956a-121">A link from source schema node to a functoid</span></span>  
  
-   <span data-ttu-id="1956a-122">從運算質連至另一個有效運算質的連結</span><span class="sxs-lookup"><span data-stu-id="1956a-122">A link from functoid to another valid functoid</span></span>  
  
-   <span data-ttu-id="1956a-123">常數值</span><span class="sxs-lookup"><span data-stu-id="1956a-123">A constant value</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1956a-124">有幾個運算質的這類**日期**，**時間**，**日期和時間**，以及**Nil**，不需要任何輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="1956a-124">There are a few functoids, such as **Date**, **Time**, **Date and Time**, and **Nil**, which do not need any input parameters.</span></span>  
  
 <span data-ttu-id="1956a-125">下圖顯示的運算質 (以紅色反白顯示) 有兩個輸入參數 (Input[0] 與 Input[1]) 及一個常數參數 (Input[2])。</span><span class="sxs-lookup"><span data-stu-id="1956a-125">The figure below displays a functoid (highlighted in red) with two input parameters (Input[0] and Input[1]) and a constant parameter (Input[2]).</span></span>  
  
 <span data-ttu-id="1956a-126">![顯示運算質的輸入的參數](../core/media/identifying-input-parameters.gif "Identifying_input_parameters")</span><span class="sxs-lookup"><span data-stu-id="1956a-126">![Displaying the input parameters to a functoid](../core/media/identifying-input-parameters.gif "Identifying_input_parameters")</span></span>  
  
## <a name="to-open-the-configure-functoid-functoid-dialog-box"></a><span data-ttu-id="1956a-127">若要開啟 設定\<運算質\>運算質對話方塊</span><span class="sxs-lookup"><span data-stu-id="1956a-127">To open the Configure \<Functoid\> Functoid dialog box</span></span>  
 <span data-ttu-id="1956a-128">您可以開啟**設定\<運算質\>運算質** 對話方塊中的下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="1956a-128">You can open the **Configure \<Functoid\> Functoid** dialog box in one of the following ways:</span></span>  
  
-   <span data-ttu-id="1956a-129">在相關格線頁中，以滑鼠右鍵按一下運算質，然後**設定運算質輸入**。</span><span class="sxs-lookup"><span data-stu-id="1956a-129">In the relevant grid page, right-click the functoid, and then click **Configure Functoid Inputs**.</span></span>  
  
-   <span data-ttu-id="1956a-130">按兩下您要設定輸入參數的運算質。</span><span class="sxs-lookup"><span data-stu-id="1956a-130">Double-click the functoid for which you want to configure the input parameters.</span></span>  
  
-   <span data-ttu-id="1956a-131">選取運算質，然後按一下省略符號 (**...**) 在 Visual Studio**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="1956a-131">Select the functoid and then click the ellipses (**…**) in the Visual Studio’s **Properties** window.</span></span>  
  
-   <span data-ttu-id="1956a-132">選取運算質，然後按鍵盤的 ENTER。</span><span class="sxs-lookup"><span data-stu-id="1956a-132">Select the functoid and then press ENTER from the keyboard.</span></span>  
  
-   <span data-ttu-id="1956a-133">選取運算質，然後按鍵盤的 CTRL+M、CTRL+I。</span><span class="sxs-lookup"><span data-stu-id="1956a-133">Select the functoid and then press CTRL+M, CTRL+I from the keyboard.</span></span> <span data-ttu-id="1956a-134">如需對應工具快速鍵的清單，請參閱 < [BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="1956a-134">For a list of Mapper shortcut keys, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
### <a name="to-insert-constant-input-parameters"></a><span data-ttu-id="1956a-135">插入常數輸入參數</span><span class="sxs-lookup"><span data-stu-id="1956a-135">To insert constant input parameters</span></span>  
  
1.  <span data-ttu-id="1956a-136">在 [**設定\<運算質\>運算質**對話方塊中，選取**運算質輸入**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1956a-136">In the **Configure \<Functoid\> Functoid** dialog box, select the **Functoid Inputs** tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1956a-137">**運算質輸入**預設會選取索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1956a-137">The **Functoid Inputs** tab is selected by default.</span></span>  
  
2.  <span data-ttu-id="1956a-138">按一下 [![常數輸入的參數新增至運算質](../core/media/add-input-parameters.gif "Add_input_parameters") ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1956a-138">Click the ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters") button.</span></span> <span data-ttu-id="1956a-139">新的資料列隨即加入。</span><span class="sxs-lookup"><span data-stu-id="1956a-139">A new row is added.</span></span>  
  
3.  <span data-ttu-id="1956a-140">輸入新的輸入參數的值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1956a-140">Type the value for the new input parameter, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1956a-141">如果未啟用 [新增] 按鈕，運算質就不會接受或要求輸入參數，或者已經達到所允許輸入的最大數目。</span><span class="sxs-lookup"><span data-stu-id="1956a-141">If the add button is not enabled, the functoid does not accept or require input parameters, or may already have the maximum number of allowed inputs.</span></span>  
  
### <a name="to-edit-existing-constant-input-parameters"></a><span data-ttu-id="1956a-142">編輯現有的常數輸入參數</span><span class="sxs-lookup"><span data-stu-id="1956a-142">To edit existing constant input parameters</span></span>  
  
1.  <span data-ttu-id="1956a-143">在 **設定\<運算質\>運算質**對話方塊中，按一下 現有的常數輸入您想要編輯的參數。</span><span class="sxs-lookup"><span data-stu-id="1956a-143">In the **Configure \<Functoid\> Functoid** dialog box, click the existing constant input parameter that you want to edit.</span></span> <span data-ttu-id="1956a-144">目前值為選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1956a-144">The current value is selected.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1956a-145">您只能編輯常數輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="1956a-145">You can edit the parameters of constant inputs only.</span></span> <span data-ttu-id="1956a-146">無法編輯所有其他類型的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="1956a-146">Input parameters of all other types cannot be edited.</span></span> <span data-ttu-id="1956a-147">您只能予以重新排列或刪除。</span><span class="sxs-lookup"><span data-stu-id="1956a-147">They can only be rearranged or deleted.</span></span>  
  
2.  <span data-ttu-id="1956a-148">按一下 [![編輯常數輸入的參數](../core/media/edit-input-parameters.gif "Edit_input_parameters") ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1956a-148">Click the ![Editing constant input parameters](../core/media/edit-input-parameters.gif "Edit_input_parameters") button.</span></span> <span data-ttu-id="1956a-149">常數值，進行適當的變更，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1956a-149">Make the appropriate changes to the constant value, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1956a-150">或者，您也可以按兩下常數輸入參數進行編輯，或按鍵盤的 F2。</span><span class="sxs-lookup"><span data-stu-id="1956a-150">Alternatively, you can double-click the constant input parameter to edit it, or press F2 from the keyboard.</span></span>  
  
## <a name="to-select-multiple-input-parameters"></a><span data-ttu-id="1956a-151">若要選取多個輸入參數</span><span class="sxs-lookup"><span data-stu-id="1956a-151">To select multiple input parameters</span></span>  
 <span data-ttu-id="1956a-152">您可以按住 CTRL 鍵並按一下所要的列以選取多個輸入參數，然後執行下列任何作業。</span><span class="sxs-lookup"><span data-stu-id="1956a-152">You can select multiple input parameters by holding down the CTRL key and clicking the desired rows, and then perform any of the following operations.</span></span> <span data-ttu-id="1956a-153">您可以按鍵盤的 CTRL+A 選取所有列。</span><span class="sxs-lookup"><span data-stu-id="1956a-153">You can press CTRL+A from the keyboard to select all the rows.</span></span>  
  
-   <span data-ttu-id="1956a-154">上下移動選取項目。</span><span class="sxs-lookup"><span data-stu-id="1956a-154">Move the selection up/down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1956a-155">如果大量選取範圍包含所有列中最上方/最下方的列，則您無法上/下移動選取項目。</span><span class="sxs-lookup"><span data-stu-id="1956a-155">If the bulk selection includes either the top-most or the bottom-most row among the other rows, you cannot move the selection up/down respectively.</span></span>  
  
-   <span data-ttu-id="1956a-156">重新排列選取項目。</span><span class="sxs-lookup"><span data-stu-id="1956a-156">Rearrange the selection.</span></span>  
  
-   <span data-ttu-id="1956a-157">刪除選取項目。</span><span class="sxs-lookup"><span data-stu-id="1956a-157">Delete the selection.</span></span>  
  
### <a name="to-change-the-order-of-existing-input-parameters"></a><span data-ttu-id="1956a-158">變更現有輸入參數的順序</span><span class="sxs-lookup"><span data-stu-id="1956a-158">To change the order of existing input parameters</span></span>  
  
1.  <span data-ttu-id="1956a-159">在 [**設定\<運算質\>運算質**] 對話方塊中，按一下現有輸入您想要移至輸入參數的已排序清單中的不同位置的參數。</span><span class="sxs-lookup"><span data-stu-id="1956a-159">In the **Configure \<Functoid\> Functoid** dialog box, click the existing input parameter that you want to move to a different position in the ordered list of input parameters.</span></span>  
  
2.  <span data-ttu-id="1956a-160">按一下 [![在清單中向上移動](../core/media/move-up-button.gif "Move_up_button") ] 按鈕，將參數向上移動參數清單中。</span><span class="sxs-lookup"><span data-stu-id="1956a-160">Click the ![Move up in the list](../core/media/move-up-button.gif "Move_up_button") button to move the parameter up in the parameter list.</span></span> <span data-ttu-id="1956a-161">視需要重複上述步驟，直到選取的輸入參數位於想要的位置。</span><span class="sxs-lookup"><span data-stu-id="1956a-161">Repeat as necessary until the selected input parameter is in the desired position.</span></span> <span data-ttu-id="1956a-162">或者，您也可以按鍵盤的向上鍵。</span><span class="sxs-lookup"><span data-stu-id="1956a-162">Alternatively, you can press the UP ARROW key from the keyboard.</span></span> <span data-ttu-id="1956a-163">如需對應工具快速鍵的清單，請參閱 < [BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="1956a-163">For a list of Mapper shortcut keys, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
     <span data-ttu-id="1956a-164">-或-</span><span class="sxs-lookup"><span data-stu-id="1956a-164">-OR-</span></span>  
  
     <span data-ttu-id="1956a-165">按一下 [![清單中向下移動](../core/media/move-down-button.gif "Move_down_button") ] 按鈕，將參數往 [參數] 清單中。</span><span class="sxs-lookup"><span data-stu-id="1956a-165">Click the ![Moving down in a list](../core/media/move-down-button.gif "Move_down_button") button to move the parameter down in the parameter list.</span></span> <span data-ttu-id="1956a-166">視需要重複上述步驟，直到選取的輸入參數位於想要的位置。</span><span class="sxs-lookup"><span data-stu-id="1956a-166">Repeat as necessary until the selected input parameter is in the desired position.</span></span> <span data-ttu-id="1956a-167">或者，您也可以按鍵盤的向下鍵。</span><span class="sxs-lookup"><span data-stu-id="1956a-167">Alternatively, you can press the DOWN ARROW key from the keyboard.</span></span> <span data-ttu-id="1956a-168">如需對應工具快速鍵的清單，請參閱 < [BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="1956a-168">For a list of Mapper shortcut keys, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1956a-169">您可以將只會從輸入的順序重新排列**設定\<運算質\>運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1956a-169">You can rearrange the sequence of inputs only from the **Configure \<Functoid\> Functoid** dialog box.</span></span> <span data-ttu-id="1956a-170">如果您選取的最上層或最底部資料列![在清單中向上移動](../core/media/move-up-button.gif "Move_up_button")或是![清單中向下移動](../core/media/move-down-button.gif "Move_down_button")按鈕就會停用，分別。</span><span class="sxs-lookup"><span data-stu-id="1956a-170">If you select the top-most or bottom-most row, the ![Move up in the list](../core/media/move-up-button.gif "Move_up_button") or ![Moving down in a list](../core/media/move-down-button.gif "Move_down_button") buttons would be disabled, respectively.</span></span>  
  
### <a name="to-delete-an-input-parameter-by-deleting-the-input-link"></a><span data-ttu-id="1956a-171">刪除輸入連結以刪除輸入參數</span><span class="sxs-lookup"><span data-stu-id="1956a-171">To delete an input parameter by deleting the input link</span></span>  
  
1.  <span data-ttu-id="1956a-172">在相關的格線頁中，按一下與您要刪除的輸入參數對應的輸入連結。</span><span class="sxs-lookup"><span data-stu-id="1956a-172">In the relevant grid page, click the input link corresponding to the input parameter you want to delete.</span></span>  
  
2.  <span data-ttu-id="1956a-173">在 **編輯**功能表上，按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="1956a-173">On the **Edit** menu, click **Delete**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1956a-174">或者，您可以按 DELETE 鍵，或以滑鼠右鍵按一下相關格線頁中中的連結，按一下**刪除**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="1956a-174">Alternatively, you can press the DELETE key, or right-click the link in the relevant grid page, and click **Delete** from the shortcut menu.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1956a-175">就會無訊息地刪除該輸入連結。</span><span class="sxs-lookup"><span data-stu-id="1956a-175">The input link is deleted silently.</span></span> <span data-ttu-id="1956a-176">如果您不確定，可以隨時復原刪除。</span><span class="sxs-lookup"><span data-stu-id="1956a-176">You can always undo delete if you are not sure about it.</span></span> <span data-ttu-id="1956a-177">如需復原/取消復原作業的詳細資訊，請參閱 <<c0> [ 如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="1956a-177">For more information about undo/redo operations, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).</span></span>  
  
### <a name="to-delete-existing-input-parameters-within-the-configure-functoid-functoid-dialog-box"></a><span data-ttu-id="1956a-178">若要刪除的設定中的現有輸入的參數\<運算質\>運算質對話方塊</span><span class="sxs-lookup"><span data-stu-id="1956a-178">To delete existing input parameters within the Configure \<Functoid\> Functoid dialog box</span></span>  
  
1.  <span data-ttu-id="1956a-179">在 [**設定\<運算質\>運算質**] 對話方塊中，按一下現有輸入您想要刪除的參數。</span><span class="sxs-lookup"><span data-stu-id="1956a-179">In the **Configure \<Functoid\> Functoid** dialog box, click the existing input parameter that you want to delete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1956a-180">您可以使用此方式刪除任何輸入參數，甚至是與某輸入連結有關的參數。</span><span class="sxs-lookup"><span data-stu-id="1956a-180">You can delete any input parameter using this technique, even those that correspond to an input link.</span></span>  
  
2.  <span data-ttu-id="1956a-181">按一下 [![刪除選取範圍](../core/media/delete-button.gif "Delete_button") ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1956a-181">Click the ![Deleting the selection](../core/media/delete-button.gif "Delete_button") button.</span></span> <span data-ttu-id="1956a-182">就會從參數清單中刪除選取的現有輸入參數。</span><span class="sxs-lookup"><span data-stu-id="1956a-182">The selected existing input parameter is deleted from the parameter list.</span></span> <span data-ttu-id="1956a-183">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="1956a-183">Click **OK**.</span></span>  
  
     <span data-ttu-id="1956a-184">或者，您可以選取想要刪除的資料列，然後按下鍵盤上的 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="1956a-184">Alternatively, you can select the row you want to delete, and press the DELETE key from the keyboard.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1956a-185">就會無訊息地刪除該輸入參數。</span><span class="sxs-lookup"><span data-stu-id="1956a-185">The input parameter is deleted silently.</span></span> <span data-ttu-id="1956a-186">如果您不確定，可以隨時復原刪除。</span><span class="sxs-lookup"><span data-stu-id="1956a-186">You can always undo delete if you are not sure about it.</span></span> <span data-ttu-id="1956a-187">如需復原/取消復原作業的詳細資訊，請參閱 <<c0> [ 如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="1956a-187">For more information about undo/redo operations, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1956a-188">當參數清單中沒有任何輸入參數時，就不會啟用刪除按鈕。</span><span class="sxs-lookup"><span data-stu-id="1956a-188">The delete button is not enabled when there are no input parameters in the parameter list.</span></span>  
  
## <a name="to-set-labels-and-comments-for-functoids"></a><span data-ttu-id="1956a-189">設定運算質的標籤與註解</span><span class="sxs-lookup"><span data-stu-id="1956a-189">To set labels and comments for functoids</span></span>  
 <span data-ttu-id="1956a-190">您可以設定標籤與註解使用運算質**設定\<運算質\>運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1956a-190">You can set labels and comments for functoids using the **Configure \<Functoid\> Functoid** dialog box.</span></span>  
  
1.  <span data-ttu-id="1956a-191">在 [**設定\<運算質\>運算質**] 對話方塊中，按一下 [**標籤與註解**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1956a-191">In the **Configure \<Functoid\> Functoid** dialog box, click the **Label and Comments** tab.</span></span>  
  
2.  <span data-ttu-id="1956a-192">型別**標籤**並**註解**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1956a-192">Type the **Label** and **Comments**, and then click **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1956a-193">如需如何標籤和註解的運算質和/或連結的詳細資訊，請參閱[如何標示連結](../core/how-to-label-a-link.md)並[加上標籤與註解的運算質如何](../core/how-to-label-and-comment-a-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="1956a-193">For more information about how to label and comment functoids and/or links, see [How to Label a Link](../core/how-to-label-a-link.md) and [How to Label and Comment a Functoid](../core/how-to-label-and-comment-a-functoid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1956a-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1956a-194">See Also</span></span>  
 [<span data-ttu-id="1956a-195">編輯運算質屬性和輸入參數</span><span class="sxs-lookup"><span data-stu-id="1956a-195">Editing Functoid Properties and Input Parameters</span></span>](../core/editing-functoid-properties-and-input-parameters.md)