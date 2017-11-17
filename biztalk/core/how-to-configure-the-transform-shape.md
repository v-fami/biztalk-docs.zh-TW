---
title: "如何設定 「 轉換 」 圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Transform shape
- Transform shape [Orchestration Designer]
ms.assetid: ca81d153-77a6-4bcc-b14f-8f48469fffe0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48cdca50620262581469e924fbb2975dde7e91fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-transform-shape"></a><span data-ttu-id="928a1-102">如何設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="928a1-102">How to Configure the Transform Shape</span></span>
![](../core/media/ebiz-orch-transform.gif "ebiz_orch_transform")  
<span data-ttu-id="928a1-103">轉換圖形</span><span class="sxs-lookup"><span data-stu-id="928a1-103">Transform shape</span></span>  
  
 <span data-ttu-id="928a1-104">當您建構訊息，因此時，才會使用轉換程式**轉換**圖形只會出現在**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="928a1-104">Transforms are only used when you construct messages, so your **Transform** shape always appears inside a **Construct Message** shape.</span></span> <span data-ttu-id="928a1-105">您可以卸除**建構訊息**圖形設計介面上，然後再卸除**轉換**圖形內，或者您可以只需卸除**轉換**設計上的圖形介面和建立封入協調流程設計師 」 將**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="928a1-105">You can drop the **Construct Message** shape on the design surface and then drop the **Transform** shape inside it, or you can simply drop the **Transform** shape on the design surface, and Orchestration Designer will create the enclosing **Construct Message** shape for you.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="928a1-106">中的任何來源或目的訊息**轉換**必須根據結構描述。</span><span class="sxs-lookup"><span data-stu-id="928a1-106">Any source or destination message in a **Transform** must be based on a schema.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="928a1-107">程序</span><span class="sxs-lookup"><span data-stu-id="928a1-107">Procedure</span></span>  
  
#### <a name="to-configure-a-transform-shape"></a><span data-ttu-id="928a1-108">設定轉換圖形</span><span class="sxs-lookup"><span data-stu-id="928a1-108">To configure a Transform shape</span></span>  
  
1.  <span data-ttu-id="928a1-109">在 [屬性] 視窗中，按一下**省略**(**...**) 按鈕**輸入訊息**，**輸出訊息**，或**對應名稱**屬性。</span><span class="sxs-lookup"><span data-stu-id="928a1-109">In the Properties Window, click the **Ellipsis** (**...**) button for the **Input Messages**, **Output Messages**, or **Map Name** property.</span></span>  
  
2.  <span data-ttu-id="928a1-110">使用**轉換組態**對話方塊來設定**轉換**圖形。</span><span class="sxs-lookup"><span data-stu-id="928a1-110">Use the **Transform Configuration** dialog box to configure the **Transform** shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="928a1-111">A**轉換**圖形只能存在於**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="928a1-111">A **Transform** shape can exist only within a **Construct Message** shape.</span></span> <span data-ttu-id="928a1-112">如果您拖曳**訊息指派**圖形設計介面上，其他地方新**建構訊息**圖形將會建立。</span><span class="sxs-lookup"><span data-stu-id="928a1-112">If you drag a **Message Assignment** shape anywhere else on the design surface, a new **Construct Message** shape will be created.</span></span>  
  
### <a name="important-performance-considerations"></a><span data-ttu-id="928a1-113">重要的效能考量</span><span class="sxs-lookup"><span data-stu-id="928a1-113">Important Performance Considerations</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="928a1-114"> 藉由在套用轉換時 (而非將整個文件載入記憶體時) 將文件資料流處理至記憶體的方式，最佳化在大型訊息上執行轉換的能力。</span><span class="sxs-lookup"><span data-stu-id="928a1-114"> optimizes the ability to perform transforms on large messages by streaming the document into memory while applying the transform as opposed to loading the entire document into memory at once.</span></span> <span data-ttu-id="928a1-115">這項最佳化能夠對應/轉換比舊版 BizTalk Server 所能處理的更大型文件。</span><span class="sxs-lookup"><span data-stu-id="928a1-115">This optimization permits the mapping/transformation of much larger documents than was possible with earlier versions of BizTalk Server.</span></span> <span data-ttu-id="928a1-116">當協調流程接受轉換圖形的多個輸入及/或輸出時，此最佳化的效果會受到限制。</span><span class="sxs-lookup"><span data-stu-id="928a1-116">A limitation of this optimization occurs when an orchestration accepts multiple inputs and/or outputs to transform shapes.</span></span>  
  
 <span data-ttu-id="928a1-117">如果協調流程接受轉換圖形的多個輸入及/或輸出，便不會執行文件資料流處理，且記憶體用量會增加。</span><span class="sxs-lookup"><span data-stu-id="928a1-117">If an orchestration accepts multiple inputs and/or outputs to transform shapes then document streaming is not performed and memory use is increased considerably.</span></span> <span data-ttu-id="928a1-118">這個問題可行的解決方法之一就是在接收管線套用一或多個轉換，如此一來協調流程將永不接受一個以上的轉換圖形輸入或輸出。</span><span class="sxs-lookup"><span data-stu-id="928a1-118">One possible workaround to this issue would be to apply the transform or transforms in a receive pipeline so that the orchestration never accepts more than a single input or a single output to a transform shape.</span></span>  
  
### <a name="newexisting-map-file"></a><span data-ttu-id="928a1-119">新的/現有的對應檔案？</span><span class="sxs-lookup"><span data-stu-id="928a1-119">New/Existing Map File?</span></span>  
 <span data-ttu-id="928a1-120">在本節中，您可以按一下 **新對應**或**現有對應**選項按鈕，選取要指派給對應**轉換**圖形。</span><span class="sxs-lookup"><span data-stu-id="928a1-120">In this section, you can click either the **New Map** or the **Existing Map** option button to select a map to assign to the **Transform** shape.</span></span>  
  
 <span data-ttu-id="928a1-121">使用**名稱**欄位下方選取的選項按鈕，以指定對應。</span><span class="sxs-lookup"><span data-stu-id="928a1-121">Use the **Name** field below the selected option button to specify a map.</span></span> <span data-ttu-id="928a1-122">如果您選取**新對應**，您可以輸入您想要指派的對應的目的地。</span><span class="sxs-lookup"><span data-stu-id="928a1-122">If you selected **New Map**, you can type a designation for the map you want to assign.</span></span> <span data-ttu-id="928a1-123">當您使用**新對應**選項，您必須在文字方塊中指定對應的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="928a1-123">When you use the **New Map** option, you must specify the fully qualified name of the map in the text box.</span></span> <span data-ttu-id="928a1-124">在文字方塊中預設會顯示這類名稱的範例，因為它是根據專案命名空間的唯一識別項名稱預先填入和**轉換**圖形名稱：\<專案命名空間 >。\<轉換圖形名稱 > _ m a p (例如 MyProject.Transform3_Map)。</span><span class="sxs-lookup"><span data-stu-id="928a1-124">The text box displays an example of such a name by default, because it is pre-populated with a unique identifier name based on the project namespace and **Transform** shape name: \<Project namespace>.\<Transform shape name>_Map (for example, MyProject.Transform3_Map).</span></span>  
  
 <span data-ttu-id="928a1-125">如果您選取**現有對應**，按一下向下的箭號，在**名稱**欄位來選取要使用的對應檔。</span><span class="sxs-lookup"><span data-stu-id="928a1-125">If you selected **Existing Map**, click the Down arrow in the **Name** field to select which map file to use.</span></span> <span data-ttu-id="928a1-126">這個清單方塊會依字母順序顯示專案中所有現有對應的排序清單。</span><span class="sxs-lookup"><span data-stu-id="928a1-126">This list box displays an alphabetically sorted list of all the existing maps available in the project.</span></span> <span data-ttu-id="928a1-127">在此清單中，如果您按一下文字\<從參考組件選取 >，則**選取成品類型**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="928a1-127">In this list, if you click the text \<Select from referenced assembly>, the **Select Artifact Type** dialog box is displayed.</span></span> <span data-ttu-id="928a1-128">多個可用選項的相關資訊，請參閱[如何使用選取成品類型對話方塊](../core/how-to-use-the-select-artifact-type-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="928a1-128">For more information about the selections it makes available, see [How to Use the Select Artifact Type Dialog Box](../core/how-to-use-the-select-artifact-type-dialog-box.md).</span></span>  
  
### <a name="select-source-and-destination-messages"></a><span data-ttu-id="928a1-129">選取來源訊息和目的訊息</span><span class="sxs-lookup"><span data-stu-id="928a1-129">Select Source and Destination Messages</span></span>  
 <span data-ttu-id="928a1-130">使用此部分**轉換組態**對話方塊來設定您在選取的對應**新的/現有對應檔案？** > 一節。</span><span class="sxs-lookup"><span data-stu-id="928a1-130">Use this part of the **Transform Configuration** dialog box to configure the map you selected in the **New/Existing Map File?** section.</span></span> <span data-ttu-id="928a1-131">如果您選取**新對應**在該區段中，您會建立對應藉由設定這一節。</span><span class="sxs-lookup"><span data-stu-id="928a1-131">If you selected **New Map** in that section, you create that map by configuring it in this section.</span></span>  
  
 <span data-ttu-id="928a1-132">如果您選取**現有對應**，您可以使用本節來進行下列兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="928a1-132">If you selected **Existing Map**, you can use this section to do one of two things:</span></span>  
  
-   <span data-ttu-id="928a1-133">選取現有對應，於目前轉換中依原狀重複使用。</span><span class="sxs-lookup"><span data-stu-id="928a1-133">Select an existing map to reuse as-is in the current transform.</span></span>  
  
-   <span data-ttu-id="928a1-134">選取現有對應，變更 (重新設定) 該對應，然後將對應運用在目前轉換的新設定中。</span><span class="sxs-lookup"><span data-stu-id="928a1-134">Select an existing map in order to change (reconfigure) it, and then use it in its new configuration in the current transform.</span></span>  
  
 <span data-ttu-id="928a1-135">使用指定來源和目的訊息**來源訊息**和**目的訊息**方格控制項。</span><span class="sxs-lookup"><span data-stu-id="928a1-135">Specify source and destination messages by using the **Source Messages** and **Destination Messages** grid controls.</span></span> <span data-ttu-id="928a1-136">您可以使用這些方格控制項以數種方式變更對應檔案。</span><span class="sxs-lookup"><span data-stu-id="928a1-136">You can use these grid controls to change the map file in several ways.</span></span> <span data-ttu-id="928a1-137">如果您刪除訊息 (也就是兩個方格控制項中的列)、新增訊息或選取不同類型的訊息，您就改變了對應的結構。</span><span class="sxs-lookup"><span data-stu-id="928a1-137">If you delete a message (a row in either grid control), add a message, or select a message of a different type, you alter the structure of the map.</span></span> <span data-ttu-id="928a1-138">當您改變對應的結構時，必須變更所有其他使用該結構的轉換，以符合對應的新結構。</span><span class="sxs-lookup"><span data-stu-id="928a1-138">When you alter the structure of a map, all other transforms that use it must be changed to match the new structure of the map.</span></span> <span data-ttu-id="928a1-139">其他變更 (例如移除訊息和插入相同類型的訊息) 則不會改變對應的結構。</span><span class="sxs-lookup"><span data-stu-id="928a1-139">Other changes, such as removing a message and inserting in its place a message of the same type, do not alter the structure of the map.</span></span>  
  
 <span data-ttu-id="928a1-140">**來源訊息**和**目的訊息**方格控制項是相同的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="928a1-140">The **Source Messages** and **Destination Messages** grid controls are identical in appearance and behavior.</span></span> <span data-ttu-id="928a1-141">每個方格控制項都有兩個資料行：訊息和類型。</span><span class="sxs-lookup"><span data-stu-id="928a1-141">Each grid control has two columns: Message and Type.</span></span> <span data-ttu-id="928a1-142">您可以選取訊息資料行中的訊息以填入方格控制項</span><span class="sxs-lookup"><span data-stu-id="928a1-142">You populate the grid controls by selecting messages in the Message column.</span></span> <span data-ttu-id="928a1-143">(請只在訊息資料行加入資料，因為類型資料行是唯讀的)。訊息資料行中的儲存格具有下拉式清單，此清單已填入了目前協調流程範圍內的訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="928a1-143">(You add data only into the Message column, because the Type column is read-only.) The cells in the Message column have drop-down lists populated with message instances that are within scope for the current orchestration.</span></span>  
  
 <span data-ttu-id="928a1-144">您也可以按一下任一方格控制項中選取一個資料列*向右箭號*方格控制項左側 (>) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="928a1-144">You can select a row in either grid control by clicking the *right arrow* (>) button at the left side of the grid control.</span></span> <span data-ttu-id="928a1-145">在選取一列之後，您可以按下 DELETE 鍵以刪除列。</span><span class="sxs-lookup"><span data-stu-id="928a1-145">After you have selected a row, you can delete it by pressing the DELETE key.</span></span> <span data-ttu-id="928a1-146">刪除列 (訊息) 會改變包含它之對應檔案的結構。</span><span class="sxs-lookup"><span data-stu-id="928a1-146">Deleting a row (a message) alters the structure of the map file that contained it.</span></span> <span data-ttu-id="928a1-147">您只可以修改對專案而言是本機的對應檔案。</span><span class="sxs-lookup"><span data-stu-id="928a1-147">You can modify only map files that are local to the project.</span></span>  
  
### <a name="when-i-click-ok-launch-the-biztalk-mapper"></a><span data-ttu-id="928a1-148">當我按 [確定] 時，啟動 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="928a1-148">When I click OK, launch the BizTalk Mapper</span></span>  
 <span data-ttu-id="928a1-149">按一下**當我按 [確定] 時，啟動 BizTalk 對應工具**會自動開啟 BizTalk 對應工具，當您按一下**確定**關閉**轉換組態**對話方塊並儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="928a1-149">Clicking **When I click OK, launch the BizTalk Mapper** opens BizTalk Mapper automatically when you click **OK** to close the **Transform Configuration** dialog box and save your changes.</span></span> <span data-ttu-id="928a1-150">但是，如果沒有填寫必要的資訊，您便無法儲存變更。</span><span class="sxs-lookup"><span data-stu-id="928a1-150">You cannot save changes, however, if required information is missing.</span></span> <span data-ttu-id="928a1-151">在此情況下，完成填寫對話方塊中的欄位，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="928a1-151">In this case, finish filling out the fields in the dialog box and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="928a1-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="928a1-152">See Also</span></span>  
 <span data-ttu-id="928a1-153">[關於對應](../core/about-maps.md) </span><span class="sxs-lookup"><span data-stu-id="928a1-153">[About Maps](../core/about-maps.md) </span></span>  
 <span data-ttu-id="928a1-154">[建構訊息](../core/constructing-messages.md) </span><span class="sxs-lookup"><span data-stu-id="928a1-154">[Constructing Messages](../core/constructing-messages.md) </span></span>  
 [<span data-ttu-id="928a1-155">如何使用運算式動態地轉換訊息</span><span class="sxs-lookup"><span data-stu-id="928a1-155">How to Use Expressions to Dynamic Transform Messages</span></span>](../core/how-to-use-expressions-to-dynamic-transform-messages.md)