---
title: 如何新增表格迴圈和表格擷取程式運算質至對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c837ab8-55db-471a-af26-9fbd0497d7d4
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4b7844260b7ac5ab29f204a538e61cb99b0d017
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249790"
---
# <a name="how-to-add-table-looping-and-table-extractor-functoids-to-a-map"></a><span data-ttu-id="f8a4f-102">如何新增表格迴圈和表格擷取程式運算質至對應</span><span class="sxs-lookup"><span data-stu-id="f8a4f-102">How to Add Table Looping and Table Extractor Functoids to a Map</span></span>
<span data-ttu-id="f8a4f-103">**表格迴圈**和**表格抽選程式**運算質一起使用。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-103">The **Table Looping** and **Table Extractor** functoids are used together.</span></span> <span data-ttu-id="f8a4f-104">**表格迴圈**運算質有您所設定的內部資料表。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-104">The **Table Looping** functoid has an internal table you configure.</span></span> <span data-ttu-id="f8a4f-105">每個輸入記錄或欄位，**表格迴圈**運算質會輸出一次一個資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-105">For each input record or field, the **Table Looping** functoid outputs the rows of the table, one at a time.</span></span> <span data-ttu-id="f8a4f-106">**表格抽選程式**運算質從一個資料列擷取所需的項目，並將它傳遞到輸出執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-106">The **Table Extractor** functoid extracts the desired item from a row and passes it on to the output instance message.</span></span>  
  
 <span data-ttu-id="f8a4f-107">如需概念資訊**表格迴圈**和**表格抽選程式**運算質，請參閱[表格迴圈和表格擷取程式運算質](../core/table-looping-and-table-extractor-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-107">For conceptual information about the **Table Looping** and **Table Extractor** functoids, see [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md).</span></span>  
  
### <a name="to-add-the-table-looping-and-table-extractor-functoids-to-a-map-and-configure-them"></a><span data-ttu-id="f8a4f-108">新增 「 表格迴圈和表格擷取程式運算質至對應並加以設定</span><span class="sxs-lookup"><span data-stu-id="f8a4f-108">To add the Table Looping and Table Extractor functoids to a map and configure them</span></span>  
  
1.  <span data-ttu-id="f8a4f-109">與[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱作用中，按一下**進階運算質**索引標籤，選取該運算質類別。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-109">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="f8a4f-110">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-110">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="f8a4f-111">拖曳**表格迴圈**運算質 (![](../core/media/advtablelooping.gif "advtablelooping")) 從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-111">Drag the **Table Looping** functoid (![](../core/media/advtablelooping.gif "advtablelooping")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-112">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-112">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="f8a4f-113">如果您想要將運算質放置到不同的格線頁，您需要先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-113">If you want to put the functoid onto a different grid page, you need to display that grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-114">因為輸出**表格迴圈**運算質當做輸入一或多個相關聯**表格抽選程式**運算質，請確定您的右邊預留空間**表格迴圈**運算質**表格抽選程式**運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-114">Because the output of the **Table Looping** functoid serves as input to one or more associated **Table Extractor** functoids, make sure you leave room to the right of the **Table Looping** functoid for the **Table Extractor** functoids.</span></span>  
  
3.  <span data-ttu-id="f8a4f-115">從來源結構描述拖曳記錄或欄位到新增**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-115">Drag a record or field from the source schema to the newly added **Table Looping** functoid.</span></span> <span data-ttu-id="f8a4f-116">第一個輸入參數為**表格迴圈**運算質，此記錄或執行個體訊息中的欄位的發生次數會控制此運算質會產生輸出的次數。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-116">As the first input parameter to the **Table Looping** functoid, the number of occurrences of this record or field in an instance message will control the number of times this functoid produces output.</span></span> <span data-ttu-id="f8a4f-117">例如，如果迴圈記錄拖曳至運算質，並處理有這個記錄的 10 個執行個體訊息時，已有一列的資料行的資料來源的設定表格格線**表格迴圈**運算質會重複 10 次，產生 10 個輸出資料列所擷取的**表格擷取程式**可輕鬆建構記錄的運算質，並允許 10 個目的地。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-117">For example, if a looping record is dragged to the functoid, and an instance message that has 10 occurrences of this record is processed, and the table grid has been configured with one row of sources of column data, the **Table Looping** functoid will iterate 10 times, producing 10 output rows for extraction by a **Table Extractor** functoid, and allowing 10 destination records to be easily constructed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-118">如果您在資料表方格中設定多個資料列，每個這類的資料列會輸出的每個反覆運算**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-118">If you configure multiple rows in the table grid, each such row will be output for each iteration of the **Table Looping** functoid.</span></span> <span data-ttu-id="f8a4f-119">因此，輸入記錄的發生次數乘上表格格線中設定的資料列數會產生可供資料擷取的輸出表格資料列數。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-119">So, the number of occurrences of an input record times the number of rows configured in the table grid yields the number of output table rows available for data extraction.</span></span>  
  
4.  <span data-ttu-id="f8a4f-120">從目的結構描述拖曳記錄或欄位**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-120">Drag a record or field from the destination schema to the **Table Looping** functoid.</span></span> <span data-ttu-id="f8a4f-121">此連結可確保在目的結構描述中建立節點。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-121">This link ensures the creation of the node in the destination schema.</span></span>  
  
5.  <span data-ttu-id="f8a4f-122">選取新加入**表格迴圈**運算質，然後在**屬性**視窗中，按一下省略符號 (**...**) 相關聯的按鈕及其**輸入參數**屬性。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-122">Select the newly added **Table Looping** functoid, and in the **Properties** window, click the ellipsis (**...**) button associated with its **Input Parameters** property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-123">或者，您也可以選取運算質，然後按鍵盤的 CTRL+M、CTRL+T。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-123">Alternatively, you can select the functoid and then press CTRL+M, CTRL+T from the keyboard.</span></span> <span data-ttu-id="f8a4f-124">如需對應工具鍵盤快速鍵請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-124">For a list of Mapper keyboard shortcuts see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
6.  <span data-ttu-id="f8a4f-125">在**設定表格迴圈運算質**對話方塊中，按一下 ![常數輸入的參數新增至運算質](../core/media/add-input-parameters.gif "Add_input_parameters")按鈕以建立第二個輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-125">In the **Configure Table Looping Functoid** dialog box, click the ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters") button to create the second input parameter.</span></span> <span data-ttu-id="f8a4f-126">輸入代表將可在您要建立這個資料表中的資料行數目的數字**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-126">Type a number that represents the number of columns that will be available in the table you are creating for this **Table Looping** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-127">表格中最大的資料行數為 228。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-127">The maximum number of columns in the table is 228.</span></span>  
  
7.  <span data-ttu-id="f8a4f-128">在**設定表格迴圈運算質**對話方塊中，按一下 ![常數輸入的參數新增至運算質](../core/media/add-input-parameters.gif "Add_input_parameters") ] 按鈕，輸入任何常數會出現在 [設定的表格格線的值。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-128">In the **Configure Table Looping Functoid** dialog box, click the ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters") button to enter any constant values that appears in your configured table grid.</span></span> <span data-ttu-id="f8a4f-129">在對話方塊中建立這些常數的順序並不重要，不過要在輸入參數清單的開頭保留第一個和第二個參數值 (分別代表資料列數目和資料欄數目) 的位置。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-129">The order in which you create these constants is not important in this dialog box as long as the first and second parameter values, the number of rows and columns, respectively, retain their positions at the beginning of the input parameter list.</span></span> <span data-ttu-id="f8a4f-130">完成後，按**確定**。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-130">When complete, click **OK**.</span></span>  
  
     <span data-ttu-id="f8a4f-131">**設定表格迴圈運算質**對話框會關閉。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-131">The **Configure Table Looping Functoid** dialog box closes.</span></span>  
  
8.  <span data-ttu-id="f8a4f-132">從來源結構描述拖曳零或多個記錄或欄位節點**表格迴圈**最近新增的運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-132">Drag zero or more record or field nodes from the source schema to the **Table Looping** functoid that you recently added.</span></span> <span data-ttu-id="f8a4f-133">這些記錄和欄位節點每一個都會新增到輸入參數清單的結尾，因此，當後續步驟中設定表格格線時，即可使用這些項目。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-133">Each of these record and field nodes is added to the end of the input parameter list, and therefore will be available when the table grid is configured in a latter step.</span></span> <span data-ttu-id="f8a4f-134">如同先前新增的表格資料常數 (不是資料列和資料行計數常數)，新增這些記錄和欄位節點的順序並不相關。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-134">Like the table data constants added earlier (not the row and column count constants), the order in which these record and field nodes are added is not ultimately relevant.</span></span>  
  
9. <span data-ttu-id="f8a4f-135">若要標記連結，請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f8a4f-135">To label a link, follow these steps:</span></span>  
  
    -   <span data-ttu-id="f8a4f-136">在顯示的格線頁中選取連結。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-136">Select a link in the displayed grid page.</span></span>  
  
    -   <span data-ttu-id="f8a4f-137">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，提供描述性名稱**標籤**屬性。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-137">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, provide a descriptive name for the **Label** property.</span></span> <span data-ttu-id="f8a4f-138">比方說，您可能會從名為 「 第二個 Author"欄位的連結提供的名稱，例如"link2ndAuthor"。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-138">For example, you might give a name like "link2ndAuthor" to a link coming from a field called "Second Author".</span></span>  
  
10. <span data-ttu-id="f8a4f-139">選取新加入**表格迴圈**運算質，然後在**屬性**視窗中，按一下省略符號 (**...**) 相關聯的按鈕**表格迴圈格線**與該運算質相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-139">Select the newly added **Table Looping** functoid, and in the **Properties** window, click the ellipsis (**...**) button associated with the **Table Looping Grid** property associated with that functoid.</span></span>  
  
     <span data-ttu-id="f8a4f-140">**設定表格迴圈運算質** 對話方塊隨即出現，並**表格迴圈格線**選取的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-140">The **Configure Table Looping Functoid** dialog box appears with the **Table Looping Grid** tab selected.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-141">或者，您可以以滑鼠右鍵按一下運算質，然後再按一下**設定表格迴圈格線**內容功能表中。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-141">Alternatively, you can right-click the functoid, and then click **Configure Table Looping Grid** in the context menu.</span></span> <span data-ttu-id="f8a4f-142">**設定表格迴圈運算質** 對話方塊隨即出現，並**表格迴圈格線**選取的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-142">The **Configure Table Looping Functoid** dialog box appears with the **Table Looping Grid** tab selected.</span></span>  
  
11. <span data-ttu-id="f8a4f-143">使用設定至少一個，並可能多、 資料列在方格中的每個表格儲存格相關聯的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-143">Use the drop-down lists associated with each table cell to configure at least one, and possibly multiple, rows in the grid.</span></span> <span data-ttu-id="f8a4f-144">下拉式清單中可用的選項是常數與連結，您已在步驟 6-8 設定做為輸入參數 3 且最高到**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-144">The choices available in the drop-down lists are the constants and links that you have configured in steps 6-8 as input parameters 3 and up to the **Table Looping** functoid.</span></span> <span data-ttu-id="f8a4f-145">(輸入參數 1 和 2 不會顯示在這些下拉式清單中。)完成後，按**確定**。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-145">(Input parameters 1 and 2 do not appear in these drop-down lists.) When complete, click **OK**.</span></span>  
  
     <span data-ttu-id="f8a4f-146">**設定表格迴圈運算質**對話框會關閉。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-146">The **Configure Table Looping Functoid** dialog box closes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-147">每個資料列構成輸出結構，組合的發生次數的記錄或欄位指定為第一個輸入參數的一個反覆項目**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-147">Each row constitutes one iteration of the output structure, in combination with the number of occurrences of the record or field specified as the first input parameter of the **Table Looping** functoid.</span></span> <span data-ttu-id="f8a4f-148">如需詳細資訊，請參閱步驟 3。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-148">For more information, see step 3.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-149">您必須選取您想要存取使用每個資料行的值**表格抽選程式**運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-149">You must select a value for each column you intend to access using a **Table Extractor** functoid.</span></span> <span data-ttu-id="f8a4f-150">如果資料行不是由**表格抽選程式**運算質，您應該考慮移除，而不是保留該資料行。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-150">If a column is not used by a **Table Extractor** functoid, you should consider removing, rather than maintaining, that column.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-151">填寫表格格線的順序不重要。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-151">The order of filling out the table grid is not important.</span></span>  
  
12. <span data-ttu-id="f8a4f-152">最大數量拖曳**表格抽選程式**運算質 (![](../core/media/advtableextractor.gif "advtableextractor")) 從工具箱拖曳至顯示的格線頁所需。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-152">Drag as many **Table Extractor** functoids (![](../core/media/advtableextractor.gif "advtableextractor")) from the Toolbox to the displayed grid page as needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-153">因為這些輸入**表格抽選程式**運算質來自**表格迴圈**運算質加入在先前步驟中，請確定您將**表格抽選程式**運算質的右邊**表格迴圈**顯示的格線頁中運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-153">Because the input of these **Table Extractor** functoids comes from the **Table Looping** functoid added in a previous step, make sure that you place the **Table Extractor** functoids to the right of the **Table Looping** functoid in the displayed grid page.</span></span>  
  
13. <span data-ttu-id="f8a4f-154">若要建立第一個輸入的參數的其中一個**表格抽選程式**步驟 9 中新增的運算質拖曳到相關**表格迴圈**運算質的左邊。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-154">To create the first input parameter for one of the **Table Extractor** functoids added in step 9, drag it to the relevant **Table Looping** functoid to its left.</span></span>  
  
14. <span data-ttu-id="f8a4f-155">若要建立具有相同的第二個輸入的參數**表格抽選程式**運算質，選取的運算質，然後在**屬性**視窗中，按一下省略符號 (**...**) 相關聯的按鈕及其**輸入參數**屬性。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-155">To create the second input parameter for the same **Table Extractor** functoid, select the functoid, and in the **Properties** window, click the ellipsis (**...**) button associated with its **Input parameters** property.</span></span>  
  
     <span data-ttu-id="f8a4f-156">**設定表格抽選程式運算質** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-156">The **Configure Table Extractor Functoid** dialog box appears.</span></span>  
  
15. <span data-ttu-id="f8a4f-157">按一下![常數輸入的參數新增至運算質](../core/media/add-input-parameters.gif "Add_input_parameters")按鈕以建立第二個輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-157">Click the ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters") button to create the second input parameter.</span></span> <span data-ttu-id="f8a4f-158">在資料表方格中的對應輸入資料行數目**表格迴圈**運算質，您要從中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-158">Type the number of the column in the table grid of the corresponding **Table Looping** functoid from which you want to extract data.</span></span> <span data-ttu-id="f8a4f-159">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-159">Click **OK**.</span></span>  
  
     <span data-ttu-id="f8a4f-160">**設定表格抽選程式運算質**對話框會關閉。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-160">The **Configure Table Extractor Functoid** dialog box closes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a4f-161">資料行編號從 1 開始。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-161">Column numbers start at 1.</span></span>  
  
16. <span data-ttu-id="f8a4f-162">若要使用的輸出**表格抽選程式**運算質拖曳**表格抽選程式**運算質至目的結構描述或目的結構描述中的記錄或欄位節點拖曳中記錄或欄位節點**表格抽選程式**運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-162">To use the output of the **Table Extractor** functoid, drag the **Table Extractor**  functoid to a record or field node in the destination schema, or drag a record or field node in the destination schema to the **Table Extractor** functoid.</span></span> <span data-ttu-id="f8a4f-163">目的執行個體訊息中對應到目的結構描述中的此記錄或欄位節點的項目或屬性值，將會填入表格格線中指定儲存格的值 (若為常數) 或指示的值 (若為連結)。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-163">The element or attribute value in a destination instance message corresponding to this record or field node in the destination schema will be populated with the value from (in the case of constants), or the value indicated by (in the case of links), the specified cell in the table grid.</span></span>  
  
17. <span data-ttu-id="f8a4f-164">針對每個重複步驟 12、 13、 14 和 15**表格抽選程式**步驟 11 中新增的運算質。</span><span class="sxs-lookup"><span data-stu-id="f8a4f-164">Repeat steps 12, 13, 14, and 15 for each of the **Table Extractor** functoids added in step 11.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a4f-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8a4f-165">See Also</span></span>  
 [<span data-ttu-id="f8a4f-166">新增進階運算質至對應</span><span class="sxs-lookup"><span data-stu-id="f8a4f-166">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)