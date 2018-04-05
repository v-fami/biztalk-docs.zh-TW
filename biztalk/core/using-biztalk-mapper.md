---
title: 使用 BizTalk 對應工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.grid
ms.assetid: 07c69603-ee79-44b2-80b1-6ae4e4c8fb4e
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bf339069f4868aa7c7bff07ae8bdbbb029c5f81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-mapper"></a><span data-ttu-id="c4f9e-102">使用 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="c4f9e-102">Using BizTalk Mapper</span></span>

## <a name="overview"></a><span data-ttu-id="c4f9e-103">概觀</span><span class="sxs-lookup"><span data-stu-id="c4f9e-103">Overview</span></span>
<span data-ttu-id="c4f9e-104">BizTalk 對應工具位於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 中。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-104">The BizTalk Mapper resides in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell.</span></span> <span data-ttu-id="c4f9e-105">「BizTalk 對應工具」中的某些功能依賴 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Shell 的使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-105">Some of the functionality in the BizTalk Mapper relies on the user interface elements of the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell.</span></span> <span data-ttu-id="c4f9e-106">例如，使用**檔案**，**編輯**，和**檢視**功能表，如同您對其他開發中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-106">For example, you use the **File**, **Edit**, and **View** menus just as you would for other development in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="c4f9e-107">會提供此常用功能的相關資訊**協助**功能表。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-107">Information about this common functionality is available from the **Help** menu.</span></span>  
  
 <span data-ttu-id="c4f9e-108">當您新增對應至 BizTalk 專案、開啟現有對應 (.btm 檔案) 或按一下 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主編輯視窗中的索引標籤以重新啟動對應時，「BizTalk 對應工具」會變成作用中。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-108">The BizTalk Mapper becomes active when you add a new map to a BizTalk project, when you open an existing map (a .btm file), or when you reactivate a map by clicking its tab in the main [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4f9e-109">「BizTalk 對應工具」使用 UTF-16 字元編碼來儲存對應檔。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-109">The BizTalk Mapper saves map files using UTF-16 character encoding.</span></span>  
>
>  <span data-ttu-id="c4f9e-110">當您將現有的成品加入至 BizTalk 專案時，建置動作一律會設定為**BtsCompile**。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-110">When you add an existing artifact to a BizTalk project, the build action is always set to **BtsCompile**.</span></span> <span data-ttu-id="c4f9e-111">即使您重新命名現有的成品，其建置動作設定為預設值**BtsCompile**。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-111">Even when you rename an existing artifact, its build action is set to the default value **BtsCompile**.</span></span> <span data-ttu-id="c4f9e-112">因此，新增或重新命名現有的成品時，您必須根據是否要建置該特定成品來適當設定建置動作。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-112">Hence, while adding or renaming an existing artifact, you need to set the build action appropriately depending on whether you want to build that particular artifact or not.</span></span>  

## <a name="parts-of-the-biztalk-mapper"></a><span data-ttu-id="c4f9e-113">組件的 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="c4f9e-113">Parts of the BizTalk Mapper</span></span>  
 <span data-ttu-id="c4f9e-114">下圖顯示 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中 BizTalk 對應工具的各個部分。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-114">The following figure shows various parts of BizTalk Mapper within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c4f9e-115">![BizTalk 對應工具](../core/media/mapper-views.gif "Mapper_Views")</span><span class="sxs-lookup"><span data-stu-id="c4f9e-115">![BizTalk Mapper](../core/media/mapper-views.gif "Mapper_Views")</span></span>  
  
 <span data-ttu-id="c4f9e-116">其中每個檢視的功能如下：</span><span class="sxs-lookup"><span data-stu-id="c4f9e-116">The functionality of each of the views is as follows:</span></span>  
  
-   <span data-ttu-id="c4f9e-117">**Visual Studio 對應工具公用程式功能區。**</span><span class="sxs-lookup"><span data-stu-id="c4f9e-117">**Visual Studio Mapper Utility Ribbon.**</span></span> <span data-ttu-id="c4f9e-118">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Mapper 提供公用程式功能區，以呈現此對應工具的相關命令。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-118">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Mapper provides a utility ribbon to surface Mapper-related commands.</span></span> <span data-ttu-id="c4f9e-119">此功能區會提供來源結構描述資訊、來源與目的結構描述相關性檢視的切換按鈕、用來顯示或隱藏完全在範圍外之連結的切換按鈕、用來開啟或關閉自動捲動功能的切換開關、用來移動瀏覽對應工具介面的按鈕、縮放控制項，以及搜尋文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-119">The ribbon provides source schema information, toggle button for relevance view for source and destination schemas, toggle button to show or hide totally out of scope links, toggle switch to turn auto-scrolling on or off, button to pan the Mapper surface, controls to zoom in or zoom out, and the search text box.</span></span> <span data-ttu-id="c4f9e-120">下圖顯示您可以在格線頁面上方看見的公用程式功能區。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-120">The following figure shows the utility ribbon you can see at the top of the grid page.</span></span>  
  
     <span data-ttu-id="c4f9e-121">![對應工具功能區](../core/media/mapper-ribbon.gif "Mapper_Ribbon")</span><span class="sxs-lookup"><span data-stu-id="c4f9e-121">![Mapper ribbon](../core/media/mapper-ribbon.gif "Mapper_Ribbon")</span></span>  
  
-   <span data-ttu-id="c4f9e-122">**來源結構描述樹狀結構檢視。**</span><span class="sxs-lookup"><span data-stu-id="c4f9e-122">**Source schema tree view.**</span></span> <span data-ttu-id="c4f9e-123">此檢視與目的結構描述樹狀結構檢視和格線檢視共用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主編輯視窗。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-123">This view shares the main [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window with the destination schema tree view and the grid view.</span></span>  
  
     <span data-ttu-id="c4f9e-124">就如其名所示，此檢視會顯示描述執行個體訊息的結構描述，而這些訊息是對應的來源。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-124">As the name suggests, this view displays the schema that describes the instance messages that are the source of mapping.</span></span> <span data-ttu-id="c4f9e-125">定義對應的連結會從來源結構描述樹狀結構檢視引導至格線檢視，最後引導至目的結構描述樹狀結構檢視。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-125">The links that define the mapping lead from the source schema tree view to the grid view, and, ultimately, to the destination schema tree view.</span></span>  
  
     <span data-ttu-id="c4f9e-126">如需 BizTalk 結構描述結構描述樹狀結構檢視中的呈現方式的詳細資訊，請參閱[BizTalk 結構描述的表示法](../core/biztalk-representation-of-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-126">For more information about how BizTalk schemas are represented in a schema tree view, see [BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md).</span></span>  
  
-   <span data-ttu-id="c4f9e-127">**目的結構描述樹狀結構檢視。**</span><span class="sxs-lookup"><span data-stu-id="c4f9e-127">**Destination schema tree view.**</span></span> <span data-ttu-id="c4f9e-128">此檢視與來源結構描述樹狀結構檢視和格線檢視共用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主編輯視窗。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-128">This view shares the main [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window with the source schema tree view and the grid view.</span></span>  
  
     <span data-ttu-id="c4f9e-129">就如其名所示，此檢視會顯示描述執行個體訊息的結構描述，而這些訊息是對應的目的地。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-129">As the name suggests, this view displays the schema that describes the instance messages that are the destination of the mapping.</span></span> <span data-ttu-id="c4f9e-130">定義對應的連結會從格線檢視 (最終是從來源結構描述樹狀結構檢視) 引導至目的結構描述樹狀結構檢視。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-130">The links that define the mapping lead into the destination schema tree view from the grid view, and ultimately from the source schema tree view.</span></span>  
  
     <span data-ttu-id="c4f9e-131">如需 BizTalk 結構描述結構描述樹狀結構檢視中的呈現方式的詳細資訊，請參閱[BizTalk 結構描述的表示法](../core/biztalk-representation-of-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-131">For more information about how BizTalk schemas are represented in a schema tree view, see [BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md).</span></span>  
  
-   <span data-ttu-id="c4f9e-132">**方格檢視。**</span><span class="sxs-lookup"><span data-stu-id="c4f9e-132">**Grid view.**</span></span> <span data-ttu-id="c4f9e-133">此檢視與來源結構描述樹狀結構檢視和目的結構描述樹狀結構檢視共用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主編輯視窗，其中來源結構描述樹狀結構檢視靠左，而目的結構描述樹狀結構檢視靠右。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-133">This view shares the main [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window with the source schema tree view and the destination schema tree view, with the source schema tree view to the left and the destination schema tree view to the right.</span></span>  
  
     <span data-ttu-id="c4f9e-134">就如其名所示，此檢視扮演定義對應時的關鍵角色，其中包含了連結與運算質來控制來源執行個體訊息中的資料如何轉換成符合目的結構描述的執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-134">As the name suggests, this view plays a critical role in the definition of maps, containing the links and functoids that control how data in a source instance message is transformed into an instance message that conforms to the destination schema.</span></span>  
  
     <span data-ttu-id="c4f9e-135">格線檢視可以有多個圖層 (稱為格線頁)，可讓您將複雜的對應組織成對應的邏輯子部分。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-135">The grid view can have multiple layers, called grid pages, allowing you to organize complex maps into logical subdivisions of mappings.</span></span> <span data-ttu-id="c4f9e-136">一般而言，格線頁所使用的空間多過於一次可顯示的空間，有多種有效的方法可讓您在格線頁中捲動。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-136">Grid pages generally use more space than can be displayed at one time, and there are several effective ways to scroll within a grid page.</span></span>  
  
     <span data-ttu-id="c4f9e-137">您可以在此檢視中主動作業以建構對應。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-137">You actively work in this view to construct your map.</span></span>  
  
-   <span data-ttu-id="c4f9e-138">**Visual Studio 工具箱視窗。**</span><span class="sxs-lookup"><span data-stu-id="c4f9e-138">**Visual Studio Toolbox window.**</span></span> <span data-ttu-id="c4f9e-139">您可以使用此檢視以顯示可用於 BizTalk 對應中的運算質，並作為拖放運算質以放置在格線頁中之作業的來源。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-139">You use this view to display the functoids available for use in BizTalk maps, and as the source of the drag-and-drop operations to place functoids in a grid page.</span></span>  
  
     <span data-ttu-id="c4f9e-140">顯示在工具箱中的運算質會根據其類別來組織。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-140">The functoids shown in the Toolbox are organized according to their categories.</span></span> <span data-ttu-id="c4f9e-141">如需可用運算質的詳細資訊，請參閱[運算質在對應中的](../core/functoids-in-maps.md)。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-141">For more information about the available functoids, see [Functoids in Maps](../core/functoids-in-maps.md).</span></span> <span data-ttu-id="c4f9e-142">另請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-142">Also see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
-   <span data-ttu-id="c4f9e-143">**Visual Studio 屬性視窗。**</span><span class="sxs-lookup"><span data-stu-id="c4f9e-143">**Visual Studio Properties window.**</span></span> <span data-ttu-id="c4f9e-144">您可以使用此檢視及其相關的對話方塊，以檢查和設定連結的屬性以及您所建立用以定義對應之運算質的屬性。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-144">You use this view, and its associated dialog boxes, to examine and set the properties of the links and functoids that you create to define your map.</span></span>  
  
     <span data-ttu-id="c4f9e-145">當您在方格檢視中的格線頁中選取連結或運算質時，在來源或目的結構描述樹狀結構檢視中，選取結構描述節點，或選取之對應的**方案總管 中**視窗中，在該連結時，運算質的對應屬性結構描述節點或出現在對應**屬性**視窗使用標準 Visual Studio 慣例。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-145">When you select a link or functoid in a grid page in the Grid view, select a schema node in the source or destination schema tree views, or select a map in the **Solution Explorer** window; the corresponding properties of that link, functoid, schema node, or map appear in the **Properties** window using the standard Visual Studio conventions.</span></span> <span data-ttu-id="c4f9e-146">例如，屬性會分組成不同類別，並可根據這些類別或字母順序來顯示。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-146">For example, the properties are grouped into categories, and can be displayed according to these categories or alphabetically.</span></span>  
  
     <span data-ttu-id="c4f9e-147">如需不同的連結、 運算質、 結構描述節點或對應本身可用的屬性集的詳細資訊，請參閱**對應屬性參考**和**結構描述屬性參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  </span><span class="sxs-lookup"><span data-stu-id="c4f9e-147">For detailed information about the different sets of properties that are available for links, functoids, schema nodes, or the map itself, see the **Map Property Reference** and the **Schema Property Reference**  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
-   <span data-ttu-id="c4f9e-148">**Visual Studio 工作清單和輸出視窗。**</span><span class="sxs-lookup"><span data-stu-id="c4f9e-148">**Visual Studio Task List and Output windows.**</span></span> <span data-ttu-id="c4f9e-149">您可以使用這些檢視以檢查驗證、編譯及測試 BizTalk 對應的結果，其使用方式與在編譯原始程式碼和建置其他專案類型時使用這些檢視的方式相同。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-149">You use these views to examine the results of validating, compiling, and testing your BizTalk maps in much the same way that these views are used when compiling source code and building other types of projects.</span></span>  
  
 <span data-ttu-id="c4f9e-150">除了這些檢視之外，您可以與許多對話方塊互動。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-150">In addition to these views, you can interact with several dialog boxes.</span></span> <span data-ttu-id="c4f9e-151">當您在編輯複雜的屬性 (例如運算質的輸入參數) 時，通常會開啟這些對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-151">You usually open these dialog boxes when you are editing a complex property such as the input parameters to a functoid.</span></span>  
  
 <span data-ttu-id="c4f9e-152">您時常會將 [方案總管] 視窗與「BizTalk 對應工具」搭配使用。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-152">You often use the Solution Explorer window in conjunction with BizTalk Mapper.</span></span> <span data-ttu-id="c4f9e-153">例如，若要建立新的對應，以滑鼠右鍵按一下 BizTalk 專案中的**方案總管] 中**視窗中，按一下**新增**，按一下 [**加入新項目**，然後使用**加入新項目**對話方塊，即可命名和建立新的對應。</span><span class="sxs-lookup"><span data-stu-id="c4f9e-153">For example, to create a new map, right-click the BizTalk project in the **Solution Explorer** window, click **Add**, click **Add New Item**, and then use the **Add New Item** dialog box to name and create a new map.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c4f9e-154">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="c4f9e-154">Next steps</span></span>
  
-   [<span data-ttu-id="c4f9e-155">使用 BizTalk 對應工具命令</span><span class="sxs-lookup"><span data-stu-id="c4f9e-155">Using BizTalk Mapper Commands</span></span>](../core/using-biztalk-mapper-commands.md)  
  
-   [<span data-ttu-id="c4f9e-156">使用格線頁</span><span class="sxs-lookup"><span data-stu-id="c4f9e-156">Working with Grid Pages</span></span>](../core/working-with-grid-pages.md)  
  
-   [<span data-ttu-id="c4f9e-157">如何管理檢視</span><span class="sxs-lookup"><span data-stu-id="c4f9e-157">How to Manage Views</span></span>](../core/how-to-manage-views.md)  
  
-   [<span data-ttu-id="c4f9e-158">如何自訂色彩和字型，在 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="c4f9e-158">How to Customize Colors and Font in BizTalk Mapper</span></span>](../core/how-to-customize-colors-and-font-in-biztalk-mapper.md)  
  
-   [<span data-ttu-id="c4f9e-159">如何展開和摺疊結構描述樹狀結構</span><span class="sxs-lookup"><span data-stu-id="c4f9e-159">How to Expand and Collapse the Schema Trees</span></span>](../core/how-to-resize-the-schema-picker-and-expand-and-collapse-the-schema-trees.md)  
  
-   [<span data-ttu-id="c4f9e-160">如何復原或重做使用者作業</span><span class="sxs-lookup"><span data-stu-id="c4f9e-160">How to Undo or Redo User Operations</span></span>](../core/how-to-undo-or-redo-user-operations.md)  
  
-   [<span data-ttu-id="c4f9e-161">如何搜尋對應項目</span><span class="sxs-lookup"><span data-stu-id="c4f9e-161">How to Search for Map Items</span></span>](../core/how-to-search-for-map-items.md)  
  
-   [<span data-ttu-id="c4f9e-162">使用 BizTalk 對應工具中的增強的功能</span><span class="sxs-lookup"><span data-stu-id="c4f9e-162">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)  
  
-   [<span data-ttu-id="c4f9e-163">如何檢視資訊提示和工具提示</span><span class="sxs-lookup"><span data-stu-id="c4f9e-163">How to View Infotip and Tooltip</span></span>](../core/how-to-view-infotip-and-tooltip.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4f9e-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4f9e-164">See Also</span></span>  
 [<span data-ttu-id="c4f9e-165">如何最佳化連結顯示</span><span class="sxs-lookup"><span data-stu-id="c4f9e-165">How to Optimize the Display of Links</span></span>](../core/how-to-optimize-the-display-of-links.md)