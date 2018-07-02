---
title: 逐步解說： 從文件執行個體建立一般檔案結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5e1453f-0380-4505-97a9-9d3526db0923
caps.latest.revision: 47
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faa79ea6784df39bb2f06b32b289837093a04919
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983423"
---
# <a name="walkthrough-creating-a-flat-file-schema-from-a-document-instance"></a><span data-ttu-id="8103e-102">逐步解說：從文件執行個體建立一般檔案結構描述</span><span class="sxs-lookup"><span data-stu-id="8103e-102">Walkthrough: Creating a Flat File Schema From a Document Instance</span></span>
<span data-ttu-id="8103e-103">此逐步解說為您顯示如何根據下列範例訂單，使用 BizTalk 一般檔案結構描述精靈從文件執行個體建立一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="8103e-103">This walkthrough shows you how to create a flat file schema from a document instance using the BizTalk Flat File Schema Wizard based on the following sample purchase order.</span></span> <span data-ttu-id="8103e-104">BizTalk 一般檔案結構描述精靈的簡介，請參閱 <<c0> [ 如何使用 BizTalk 一般檔案結構描述精靈](../core/how-to-use-biztalk-flat-file-schema-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="8103e-104">For an introduction to the BizTalk Flat File Schema Wizard, see [How to Use BizTalk Flat File Schema Wizard](../core/how-to-use-biztalk-flat-file-schema-wizard.md).</span></span>  

 <span data-ttu-id="8103e-105">![範例採購單](../core/media/flatfileschema-samplepurchaseorder.gif "FlatFileSchema_SamplePurchaseOrder")</span><span class="sxs-lookup"><span data-stu-id="8103e-105">![Sample Purchase Order](../core/media/flatfileschema-samplepurchaseorder.gif "FlatFileSchema_SamplePurchaseOrder")</span></span>  

 <span data-ttu-id="8103e-106">訂單的每一行都會以標示為綠色的歸位換行字元 (CRLF) 結尾。</span><span class="sxs-lookup"><span data-stu-id="8103e-106">Each line of the purchase order ends with a carriage return line feed (CRLF), marked in green.</span></span> <span data-ttu-id="8103e-107">訂單會以顯示為紅色的 PO 標記開頭，後面加上日期。</span><span class="sxs-lookup"><span data-stu-id="8103e-107">The purchase order starts with a PO tag shown in red and followed by a date.</span></span> <span data-ttu-id="8103e-108">兩個重複的固定位置欄位包含客戶資訊，並顯示為紫色。</span><span class="sxs-lookup"><span data-stu-id="8103e-108">Two repeating fixed positional fields contain customer information and are shown in purple.</span></span> <span data-ttu-id="8103e-109">註解 欄位中之後, 就沒有重複的欄位，從包含多個以逗號 （，） 分隔的記錄和以管道分隔的資料值的項目標籤 (&#124;)，其中會以藍色顯示。</span><span class="sxs-lookup"><span data-stu-id="8103e-109">After the comment field, there is a repeating field starting with an ITEMS tag that contains multiple records delimited by commas (,) and data values separated by pipes (&#124;), which are shown in blue.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="8103e-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="8103e-110">Prerequisites</span></span>  
 <span data-ttu-id="8103e-111">執行此逐步解說之前，請確定已在您的伺服器上安裝和設定下列軟體：</span><span class="sxs-lookup"><span data-stu-id="8103e-111">Before exercising this walkthrough, make sure the following software is installed and configured on your server:</span></span>  

- <span data-ttu-id="8103e-112">Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8103e-112">Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]</span></span>  

- <span data-ttu-id="8103e-113">Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]具有**開發人員工具**安裝</span><span class="sxs-lookup"><span data-stu-id="8103e-113">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with the **Developer tools** installed</span></span>

  <span data-ttu-id="8103e-114">若要準備本逐步解說中的文件執行個體，以下內容複製到文字編輯器，並將它儲存為文字檔。</span><span class="sxs-lookup"><span data-stu-id="8103e-114">To prepare the document instance for the walkthrough, copy the following into a text editor, and save it as a text file.</span></span> <span data-ttu-id="8103e-115">請務必複製所有列摘要和換行。</span><span class="sxs-lookup"><span data-stu-id="8103e-115">Be sure to copy all line feeds and carriage returns.</span></span>  

```
PO1999-10-20
US        Alice Smith         123 Maple Street    Mill Valley    CA 90952
US        Robert Smith        8 Oak Avenue        Old Town       PA 95819
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric
```


## <a name="start-the-wizard"></a><span data-ttu-id="8103e-116">啟動精靈</span><span class="sxs-lookup"><span data-stu-id="8103e-116">Start the wizard</span></span>  

1. <span data-ttu-id="8103e-117">在 [ [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟**方案總管] 中**。</span><span class="sxs-lookup"><span data-stu-id="8103e-117">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the **Solution Explorer**.</span></span>  

2. <span data-ttu-id="8103e-118">若要加入新的一般檔案結構描述，以滑鼠右鍵按一下專案，然後選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="8103e-118">To add the new flat file schema, right-click the project, and select **Add**.</span></span> <span data-ttu-id="8103e-119">按一下 **新的項目**。</span><span class="sxs-lookup"><span data-stu-id="8103e-119">Click **New Item**.</span></span>  

3. <span data-ttu-id="8103e-120">在 [**加入新項目**] 視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8103e-120">In the **Add New Item** window, do the following:</span></span>  

   1.  <span data-ttu-id="8103e-121">在 **分類**區段中，選取**結構描述檔案**。</span><span class="sxs-lookup"><span data-stu-id="8103e-121">In the **Categories** section, select **Schema Files**.</span></span>  

   2.  <span data-ttu-id="8103e-122">在 **範本**區段中，選取**一般檔案結構描述精靈**。</span><span class="sxs-lookup"><span data-stu-id="8103e-122">In the **Templates** section, select **Flat File Schema Wizard**.</span></span>  

   3.  <span data-ttu-id="8103e-123">在 **名稱**欄位中，輸入**PurchaseOrder.xsd**新的結構描述。</span><span class="sxs-lookup"><span data-stu-id="8103e-123">In the **Name** field, enter **PurchaseOrder.xsd** for the new schema.</span></span>  

   4.  <span data-ttu-id="8103e-124">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="8103e-124">Click **Add**.</span></span>  

4. <span data-ttu-id="8103e-125">當 BizTalk 一般檔案結構描述精靈開啟時，會出現歡迎頁面。</span><span class="sxs-lookup"><span data-stu-id="8103e-125">When the BizTalk Flat File Schema Wizard opens, the Welcome Page appears.</span></span>   
   <span data-ttu-id="8103e-126">若要在未來執行精靈時，請跳過這個畫面，請選取**不要再顯示此簡介頁面** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="8103e-126">To skip this screen when running the wizard in the future, select the **Do not show this introduction page again** box.</span></span> <span data-ttu-id="8103e-127">按 **[下一步]** ，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8103e-127">Click **Next** to continue.</span></span>  

## <a name="selecting-purchase-order-instance"></a><span data-ttu-id="8103e-128">選取訂單執行個體</span><span class="sxs-lookup"><span data-stu-id="8103e-128">Selecting purchase order instance</span></span>  

-   <span data-ttu-id="8103e-129">在 **一般檔案結構描述資訊**畫面上，選取您的執行個體並輸入下列資訊。</span><span class="sxs-lookup"><span data-stu-id="8103e-129">On the **Flat File Schema Information** screen, select your instance and enter the following information.</span></span> <span data-ttu-id="8103e-130">當您完成之後時，按一下**下一步**以繼續。</span><span class="sxs-lookup"><span data-stu-id="8103e-130">When you are done, click **Next** to continue.</span></span>  

    -   <span data-ttu-id="8103e-131">**執行個體檔案：** 按一下 **瀏覽**按鈕找出一般檔案將會產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="8103e-131">**Instance file:** Click the **Browse** button to locate the flat file from which the schema will be generated.</span></span> <span data-ttu-id="8103e-132">瀏覽至包含您在逐步解說必要條件一節中建立文字檔案的資料夾： 建立一般檔案結構描述的文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8103e-132">Browse to the folder containing the text file you created in the Prerequisites section of Walkthrough: Creating a Flat File Schema From a Document Instance.</span></span>  

    -   <span data-ttu-id="8103e-133">**記錄名稱：** 型別**PO**因為到時將是結構描述根名稱。</span><span class="sxs-lookup"><span data-stu-id="8103e-133">**Record name:** Type **PO** as it will be the schema root name.</span></span>  

    -   <span data-ttu-id="8103e-134">**目標命名空間：** 型別**http://Flat_File_Project.PurchaseOrder**結構描述目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="8103e-134">**Target namespace:** Type **http://Flat_File_Project.PurchaseOrder** for schema target namespace.</span></span>  

    -   <span data-ttu-id="8103e-135">**字碼頁：** 選取  **utf-8 (65001)** 從下拉式清單選取項目清單。</span><span class="sxs-lookup"><span data-stu-id="8103e-135">**Code page:** Select **UTF-8 (65001)** from the drop down selection list.</span></span>  

    -   <span data-ttu-id="8103e-136">**計算以位元組為單位的位置：** 核取此方塊，如果您想要以位元組為單位計算位置資料欄位。</span><span class="sxs-lookup"><span data-stu-id="8103e-136">**Count positions in bytes:** Check this box if you wish to count the positional data fields by bytes.</span></span> <span data-ttu-id="8103e-137">依預設值，位置資料欄位會以字元為單位計算。</span><span class="sxs-lookup"><span data-stu-id="8103e-137">By default, the positional data fields are counted in characters.</span></span> <span data-ttu-id="8103e-138">在此逐步解說中，保留**計算以位元組為單位的位置**核取方塊未核取。</span><span class="sxs-lookup"><span data-stu-id="8103e-138">In this walkthrough, leave the **Count positions in bytes** check box unchecked.</span></span>  

## <a name="select-purchase-order-data"></a><span data-ttu-id="8103e-139">選取訂單資料</span><span class="sxs-lookup"><span data-stu-id="8103e-139">Select purchase order data</span></span>  

-   <span data-ttu-id="8103e-140">在 [**選取文件資料**] 畫面中，一般檔案的內容會顯示。</span><span class="sxs-lookup"><span data-stu-id="8103e-140">On the **Select Document Data** screen, the contents of the flat file are displayed.</span></span> <span data-ttu-id="8103e-141">選取 [建立結構描述中，所需的資料，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8103e-141">Select the data needed for creating the schema, and then click **Next**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8103e-142">如果您想要使用的整份文件執行個體，您可以按下**CTRL-A**全部選取。</span><span class="sxs-lookup"><span data-stu-id="8103e-142">If you would like to use the entire document instance, you can press **Ctrl-A** to select all.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8103e-143">請檢查**長行換行**方塊，如果您想要檢視整份文件執行個體內容包裝在整個精靈在編輯方塊。</span><span class="sxs-lookup"><span data-stu-id="8103e-143">Check **Wrap long lines** box if you want to view the entire document instance content wrapped into the edit box throughout the wizard.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8103e-144">如果您從交換執行個體建立結構描述，只要選取表示個別文件結構的部分。</span><span class="sxs-lookup"><span data-stu-id="8103e-144">If you are creating the schema from an interchange instance, select only the part that represents the individual document structure.</span></span>  

## <a name="delimit-purchase-order-record"></a><span data-ttu-id="8103e-145">分隔訂單記錄</span><span class="sxs-lookup"><span data-stu-id="8103e-145">Delimit purchase order record</span></span>  

-   <span data-ttu-id="8103e-146">因為訂單的每一行結尾歸位換行字元 (CRLF) 中，選取**依分隔符號**，然後按一下**下一步**上**選取記錄格式**螢幕。</span><span class="sxs-lookup"><span data-stu-id="8103e-146">As each line of the purchase order ends with a carriage return line feed (CRLF), select **By delimiter symbol**, and then click **Next** on **Select Record Format** screen.</span></span>  

## <a name="specify-purchase-order-record-property"></a><span data-ttu-id="8103e-147">指定訂單記錄屬性</span><span class="sxs-lookup"><span data-stu-id="8103e-147">Specify purchase order record property</span></span>  

- <span data-ttu-id="8103e-148">在 [**分隔記錄**畫面上，輸入下列命令來定義結構描述的第一層，完成之後，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8103e-148">On the **Delimited Record** screen, enter the following to define the first level of the schema and when you are done, click **Next**.</span></span>  

  - <span data-ttu-id="8103e-149">**子分隔符號：** 選取  **{CR} {LF}**。</span><span class="sxs-lookup"><span data-stu-id="8103e-149">**Child delimiter:** Select **{CR}{LF}**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8103e-150">**子分隔符號**屬性是具有下拉式選擇清單的編輯方塊包含一組預設值。</span><span class="sxs-lookup"><span data-stu-id="8103e-150">**Child delimiter** property is an editable box with drop down selection list contains a set of default values.</span></span> <span data-ttu-id="8103e-151">**Child delimiter**可以指定為字元或十六進位值。</span><span class="sxs-lookup"><span data-stu-id="8103e-151">The **Child delimiter** can be specified as a character or as a hexadecimal value.</span></span> <span data-ttu-id="8103e-152">例如，  **\\{** 或是 **{0x0D0A}**。</span><span class="sxs-lookup"><span data-stu-id="8103e-152">For example, **\\{** or **{0x0D0A}**.</span></span>  

  - <span data-ttu-id="8103e-153">**逸出字元：** 逸出字元是單一字元，抑制跟隨在它後面之字元的任何特殊意義。</span><span class="sxs-lookup"><span data-stu-id="8103e-153">**Escape character:** An escape character is a single character that suppresses any special meaning of the character that follows it.</span></span> <span data-ttu-id="8103e-154">請參閱[逸出字元](../core/escape-characters.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8103e-154">See [Escape Characters](../core/escape-characters.md) for more information.</span></span> <span data-ttu-id="8103e-155">在此逐步解說中，將它留白。</span><span class="sxs-lookup"><span data-stu-id="8103e-155">Leave it blank for the walkthrough.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8103e-156">使用時**\\**， **{，** 並 **}** 如**子分隔符號**或**逸出字元**、您必須使用反斜線。</span><span class="sxs-lookup"><span data-stu-id="8103e-156">When using **\\**, **{,** and **}** for **Child delimiter** or **Escape character**, a back slash must be used.</span></span> <span data-ttu-id="8103e-157">例如，  **\\ \\，** 並 **\\{**。</span><span class="sxs-lookup"><span data-stu-id="8103e-157">For example, **\\\\,** and **\\{**.</span></span>  

  - <span data-ttu-id="8103e-158">請檢查**記錄具有標記識別項**方塊，然後輸入**PO**中**標記**。</span><span class="sxs-lookup"><span data-stu-id="8103e-158">Check **Record has a tag identifier** box and type **PO** in **Tag**.</span></span> <span data-ttu-id="8103e-159">在多個記錄檔中， **PO**會用來識別每個個別的記錄。</span><span class="sxs-lookup"><span data-stu-id="8103e-159">In a multiple records file, **PO** will be used to identify each individual record.</span></span> <span data-ttu-id="8103e-160">按 **[下一步]** ，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8103e-160">Click **Next** to continue.</span></span>  

    <span data-ttu-id="8103e-161">![分隔的記錄畫面](../core/media/flatfileschemawizard-delimitedrecord1.gif "FlatFileSchemaWizard_DelimitedRecord1")</span><span class="sxs-lookup"><span data-stu-id="8103e-161">![Delimited Record screen](../core/media/flatfileschemawizard-delimitedrecord1.gif "FlatFileSchemaWizard_DelimitedRecord1")</span></span>  

## <a name="define-the-element-in-the-purchase-order-record"></a><span data-ttu-id="8103e-162">定義訂單記錄中的項目</span><span class="sxs-lookup"><span data-stu-id="8103e-162">Define the element in the purchase order record</span></span>  

1.  <span data-ttu-id="8103e-163">精靈已在訂單記錄中識別四個項目；您現在必須定義項目屬性。</span><span class="sxs-lookup"><span data-stu-id="8103e-163">The wizard has identified four elements in the purchase order record; you must now define the element property.</span></span> <span data-ttu-id="8103e-164">在第一個資料列中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8103e-164">In the first row, do the following:</span></span>  

    1.  <span data-ttu-id="8103e-165">型別**日期**for**項目名稱**。</span><span class="sxs-lookup"><span data-stu-id="8103e-165">Type **date** for the **Element Name**.</span></span>  

    2.  <span data-ttu-id="8103e-166">選取 **欄位項目**for**項目型別**。</span><span class="sxs-lookup"><span data-stu-id="8103e-166">Select **Field element** for **Element Type**.</span></span>  

    3.  <span data-ttu-id="8103e-167">選取 **日期**從下拉式清單選取項目清單**資料型別**。</span><span class="sxs-lookup"><span data-stu-id="8103e-167">Select **date** from the drop-down selection list for **Data Type**.</span></span>  

2.  <span data-ttu-id="8103e-168">對下列項目重複步驟 a 到 c。</span><span class="sxs-lookup"><span data-stu-id="8103e-168">Repeat Steps a to c for the following elements.</span></span> <span data-ttu-id="8103e-169">當您完成之後時，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8103e-169">When you are done, click **Next**.</span></span>  

    |<span data-ttu-id="8103e-170">元素名稱</span><span class="sxs-lookup"><span data-stu-id="8103e-170">Element Name</span></span>|<span data-ttu-id="8103e-171">項目類型</span><span class="sxs-lookup"><span data-stu-id="8103e-171">Element Type</span></span>|<span data-ttu-id="8103e-172">資料類型</span><span class="sxs-lookup"><span data-stu-id="8103e-172">Data Type</span></span>|  
    |------------------|------------------|---------------|  
    |<span data-ttu-id="8103e-173">**客戶**</span><span class="sxs-lookup"><span data-stu-id="8103e-173">**customer**</span></span>|<span data-ttu-id="8103e-174">**重複記錄**</span><span class="sxs-lookup"><span data-stu-id="8103e-174">**Repeating record**</span></span>||  
    ||<span data-ttu-id="8103e-175">**略過**</span><span class="sxs-lookup"><span data-stu-id="8103e-175">**Ignore**</span></span>||  
    |<span data-ttu-id="8103e-176">**項目**</span><span class="sxs-lookup"><span data-stu-id="8103e-176">**items**</span></span>|<span data-ttu-id="8103e-177">**記錄**</span><span class="sxs-lookup"><span data-stu-id="8103e-177">**Record**</span></span>||  

     <span data-ttu-id="8103e-178">![子元素畫面](../core/media/flatfileschemawizard-childelements.gif "FlatFileSchemaWizard_ChildElements")</span><span class="sxs-lookup"><span data-stu-id="8103e-178">![Child Elements screen](../core/media/flatfileschemawizard-childelements.gif "FlatFileSchemaWizard_ChildElements")</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8103e-179">您可以選取多個資料列，然後變更其**項目型別**成單一的型別，使用滑鼠和 SHIFT 或 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="8103e-179">You can select multiple rows and then change their **Element Type** to a single type by using the mouse and the SHIFT or CTRL key.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="8103e-180">按一下 [之後**下一步**上**子項目**] 畫面中，您將無法再按一下**回**要重新定義，或對子項目中的任何變更。</span><span class="sxs-lookup"><span data-stu-id="8103e-180">After you click **Next** on the **Child Elements** screen, you will not be able to click **Back** to redefine or make any changes to the child elements.</span></span> <span data-ttu-id="8103e-181">您必須關閉精靈再加以重新啟動，才能定義一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="8103e-181">You may need to close the wizard and launch the wizard again to define the flat file schema.</span></span>  

3.  <span data-ttu-id="8103e-182">當您完成此程序中的步驟之後，就會產生結構描述的第一個層級，如下列擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="8103e-182">After you complete the steps in this procedure, the first level of the schema is generated as shown in the following screenshot.</span></span> <span data-ttu-id="8103e-183">已定義三個唯一項目，您將繼續進一步為訂單記錄中的項目定義子記錄。</span><span class="sxs-lookup"><span data-stu-id="8103e-183">Three unique elements are defined, and you will continue to further define the child records for the elements in the purchase order record.</span></span> <span data-ttu-id="8103e-184">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="8103e-184">Click **Next**.</span></span>  

     <span data-ttu-id="8103e-185">![範例結構描述的螢幕畫面](../core/media/flatfileschemawizard-schema1.gif "FlatFileSchemaWizard_Schema1")</span><span class="sxs-lookup"><span data-stu-id="8103e-185">![Sample Schema screen](../core/media/flatfileschemawizard-schema1.gif "FlatFileSchemaWizard_Schema1")</span></span>  

## <a name="define-the-customer-record"></a><span data-ttu-id="8103e-186">定義客戶記錄</span><span class="sxs-lookup"><span data-stu-id="8103e-186">Define the customer record</span></span>  

1.  <span data-ttu-id="8103e-187">因為我們已經定義**客戶**項目做為**重複記錄**類型並**項目**項目做為**記錄**輸入時，BizTalk一般檔案結構描述精靈現在會繼續進一步定義這兩個元素。</span><span class="sxs-lookup"><span data-stu-id="8103e-187">Because we defined the **customer** element as the **Repeating record** type and the **items** element as the **Record** type, the BizTalk Flat File Schema Wizard now continues to further define these two elements.</span></span> <span data-ttu-id="8103e-188">在上**結構描述檢視**畫面上，選取**客戶**，然後按一下**下一步**以繼續。</span><span class="sxs-lookup"><span data-stu-id="8103e-188">On the **Schema View** screen, select **customer**, and then click **Next** to continue.</span></span>  

2.  <span data-ttu-id="8103e-189">若要使用客戶記錄，您必須選取表示該項目的資料。</span><span class="sxs-lookup"><span data-stu-id="8103e-189">To work with the customer record, you need to select the data that represents that element.</span></span> <span data-ttu-id="8103e-190">因為它是重複記錄，所以任一行都可以用來定義記錄。</span><span class="sxs-lookup"><span data-stu-id="8103e-190">Because it is a repeating record, either of the lines can be used to define the record.</span></span> <span data-ttu-id="8103e-191">選取 [客戶資料的第一行，然後按一下**下一步]** 以繼續。</span><span class="sxs-lookup"><span data-stu-id="8103e-191">Select the first line of customer data and click **Next** to continue.</span></span>  

3.  <span data-ttu-id="8103e-192">在 [**選取記錄格式**頁面上，選取**依相對位置**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8103e-192">On the **Select Record Format** page, select **By relative positions**, and then click **Next**.</span></span>  

4.  <span data-ttu-id="8103e-193">精靈會提供視覺化工具，以顯示和計算欄位之間的距離。</span><span class="sxs-lookup"><span data-stu-id="8103e-193">The wizard provides a visual tool for showing and calculating the distance between the fields.</span></span> <span data-ttu-id="8103e-194">在 **位置記錄**頁面上，使用滑鼠左鍵按一下位置標示 10 來表示的 名稱 欄位的開始位置。</span><span class="sxs-lookup"><span data-stu-id="8103e-194">On the **Positional Record** page, use the left mouse button to click the position marker 10 to represent where the name field begins.</span></span> <span data-ttu-id="8103e-195">按一下下列位置標示，來表示其他的資料欄位：</span><span class="sxs-lookup"><span data-stu-id="8103e-195">Click the following position markers to represent the rest of the data fields:</span></span>  

    |<span data-ttu-id="8103e-196">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="8103e-196">Field Name</span></span>|<span data-ttu-id="8103e-197">位置標示</span><span class="sxs-lookup"><span data-stu-id="8103e-197">Position Marker</span></span>|  
    |----------------|---------------------|  
    |<span data-ttu-id="8103e-198">街道</span><span class="sxs-lookup"><span data-stu-id="8103e-198">street</span></span>|<span data-ttu-id="8103e-199">30</span><span class="sxs-lookup"><span data-stu-id="8103e-199">30</span></span>|  
    |<span data-ttu-id="8103e-200">城市</span><span class="sxs-lookup"><span data-stu-id="8103e-200">city</span></span>|<span data-ttu-id="8103e-201">50</span><span class="sxs-lookup"><span data-stu-id="8103e-201">50</span></span>|  
    |<span data-ttu-id="8103e-202">state</span><span class="sxs-lookup"><span data-stu-id="8103e-202">state</span></span>|<span data-ttu-id="8103e-203">65</span><span class="sxs-lookup"><span data-stu-id="8103e-203">65</span></span>|  
    |<span data-ttu-id="8103e-204">postalcode</span><span class="sxs-lookup"><span data-stu-id="8103e-204">postalcode</span></span>|<span data-ttu-id="8103e-205">68</span><span class="sxs-lookup"><span data-stu-id="8103e-205">68</span></span>|  

     <span data-ttu-id="8103e-206">按 **[下一步]** ，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8103e-206">Click **Next** to continue.</span></span>  

     <span data-ttu-id="8103e-207">![位置記錄畫面](../core/media/flatfileschemawizard-positionalrecord.gif "FlatFileSchemaWizard_PositionalRecord")</span><span class="sxs-lookup"><span data-stu-id="8103e-207">![Positional Record screen](../core/media/flatfileschemawizard-positionalrecord.gif "FlatFileSchemaWizard_PositionalRecord")</span></span>  

5.  <span data-ttu-id="8103e-208">在 [**子項目**] 頁面上，您指定的子元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="8103e-208">On the **Child Elements** page, you specify the properties of the child elements.</span></span> <span data-ttu-id="8103e-209">選取第一個資料列，然後輸入**國家/地區**作為**項目名稱**。</span><span class="sxs-lookup"><span data-stu-id="8103e-209">Select the first row and type **country** as the **Element Name**.</span></span> <span data-ttu-id="8103e-210">保留其他欄位的預設值。</span><span class="sxs-lookup"><span data-stu-id="8103e-210">Leave the default values in the other columns.</span></span> <span data-ttu-id="8103e-211">輸入下列值的其他屬性**項目名稱**:</span><span class="sxs-lookup"><span data-stu-id="8103e-211">Type the following values for the other properties for the **Element Name**:</span></span>  

    |<span data-ttu-id="8103e-212">元素名稱</span><span class="sxs-lookup"><span data-stu-id="8103e-212">Element Name</span></span>|<span data-ttu-id="8103e-213">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="8103e-213">Value</span></span>|  
    |------------------|-----------|  
    |<span data-ttu-id="8103e-214">**customer_Child2**</span><span class="sxs-lookup"><span data-stu-id="8103e-214">**customer_Child2**</span></span>|<span data-ttu-id="8103e-215">**fullName**</span><span class="sxs-lookup"><span data-stu-id="8103e-215">**fullName**</span></span>|  
    |<span data-ttu-id="8103e-216">**customer_Child3**</span><span class="sxs-lookup"><span data-stu-id="8103e-216">**customer_Child3**</span></span>|<span data-ttu-id="8103e-217">**街道**</span><span class="sxs-lookup"><span data-stu-id="8103e-217">**street**</span></span>|  
    |<span data-ttu-id="8103e-218">**customer_Child4**</span><span class="sxs-lookup"><span data-stu-id="8103e-218">**customer_Child4**</span></span>|<span data-ttu-id="8103e-219">**縣 （市)**</span><span class="sxs-lookup"><span data-stu-id="8103e-219">**city**</span></span>|  
    |<span data-ttu-id="8103e-220">**customer_Child5**</span><span class="sxs-lookup"><span data-stu-id="8103e-220">**customer_Child5**</span></span>|<span data-ttu-id="8103e-221">**state**</span><span class="sxs-lookup"><span data-stu-id="8103e-221">**state**</span></span>|  
    |<span data-ttu-id="8103e-222">**customer_Child6**</span><span class="sxs-lookup"><span data-stu-id="8103e-222">**customer_Child6**</span></span>|<span data-ttu-id="8103e-223">**郵遞區號**</span><span class="sxs-lookup"><span data-stu-id="8103e-223">**postalcode**</span></span>|  

     <span data-ttu-id="8103e-224">按 **[下一步]** ，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8103e-224">Click **Next** to continue.</span></span>  

     <span data-ttu-id="8103e-225">![子元素畫面](../core/media/flatfileschemawizard-childelements2.gif "FlatFileSchemaWizard_ChildElements2")</span><span class="sxs-lookup"><span data-stu-id="8103e-225">![Child Elements screen](../core/media/flatfileschemawizard-childelements2.gif "FlatFileSchemaWizard_ChildElements2")</span></span>  

6.  <span data-ttu-id="8103e-226">客戶記錄的子項目會被建立，如下列擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="8103e-226">The child elements of the customer record are created as shown in the following screenshot.</span></span> <span data-ttu-id="8103e-227">按一下 [**下一步]** 來定義項目記錄的子元素。</span><span class="sxs-lookup"><span data-stu-id="8103e-227">Click **Next** to define the child elements for the items record.</span></span>  

     <span data-ttu-id="8103e-228">![範例結構描述的螢幕畫面](../core/media/flatfileschemawizard-schema2.gif "FlatFileSchemaWizard_Schema2")</span><span class="sxs-lookup"><span data-stu-id="8103e-228">![Sample Schema screen](../core/media/flatfileschemawizard-schema2.gif "FlatFileSchemaWizard_Schema2")</span></span>  

#### <a name="define-the-items-record"></a><span data-ttu-id="8103e-229">定義項目記錄</span><span class="sxs-lookup"><span data-stu-id="8103e-229">Define the items record</span></span>  

1. <span data-ttu-id="8103e-230">在 [**結構描述檢視**頁面上，選取**項目**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8103e-230">On the **Schema View** page, select **items**, and then click **Next**.</span></span>  

2. <span data-ttu-id="8103e-231">在 [**選取文件資料**頁面上，選取整行開頭的項目，然後按一下**下一步]** 以定義其子項目。</span><span class="sxs-lookup"><span data-stu-id="8103e-231">On the **Select Document Data** page, select the entire line begins with ITEMS, and then click **Next** to define its child elements.</span></span>  

3. <span data-ttu-id="8103e-232">在 [**選取記錄格式**頁面上，選取**依分隔符號**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8103e-232">On the **Select Record Format** page, select **By delimiter symbol**, and then click **Next**.</span></span>  

4. <span data-ttu-id="8103e-233">在 [項目] 記錄中，會使用逗號來分隔個別的項目。</span><span class="sxs-lookup"><span data-stu-id="8103e-233">In the Items record, commas are used to delimit the individual items.</span></span> <span data-ttu-id="8103e-234">因此，在**分隔記錄**頁面上，輸入下列命令來定義項目記錄。</span><span class="sxs-lookup"><span data-stu-id="8103e-234">Therefore, on the **Delimited Record** page, enter the following to define the items record.</span></span> <span data-ttu-id="8103e-235">當您完成之後時，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8103e-235">When you are done, click **Next**.</span></span>  

   -   <span data-ttu-id="8103e-236">選取  **，** 從**Child delimiter**下拉式選擇清單。</span><span class="sxs-lookup"><span data-stu-id="8103e-236">Select **,** from **Child delimiter** drop-down selection list.</span></span>  

   -   <span data-ttu-id="8103e-237">離開**逸出字元**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="8103e-237">Leave the **Escape character** text box blank.</span></span>  

   -   <span data-ttu-id="8103e-238">選取 **記錄具有標記識別項**並輸入**項目**中**標記**。</span><span class="sxs-lookup"><span data-stu-id="8103e-238">Select **Record has a tag identifier** and type **ITEMS** in **Tag**.</span></span>  

        <span data-ttu-id="8103e-239">在多個項目記錄中，**項目**用來識別每個個別的記錄。</span><span class="sxs-lookup"><span data-stu-id="8103e-239">In a multiple items record, **ITEMS** is used to identify each individual record.</span></span>  

5. <span data-ttu-id="8103e-240">使用來自**分隔記錄**頁面上，精靈會識別兩個子項目。</span><span class="sxs-lookup"><span data-stu-id="8103e-240">Using the values from the **Delimited Record** page, the wizard identifies two child elements.</span></span> <span data-ttu-id="8103e-241">因為其中一個是重複記錄時，選取第一個項目，並輸入**項目**作為項目名稱，然後選取**重複記錄**從下拉式清單選取項目清單**項目類型**.</span><span class="sxs-lookup"><span data-stu-id="8103e-241">Because one of them is a repeating record, select the first element and enter **item** for Element Name, and then select **Repeating Record** from the drop down selection list for **Element Type**.</span></span> <span data-ttu-id="8103e-242">請保留欄位中的其他預設值。</span><span class="sxs-lookup"><span data-stu-id="8103e-242">Leave the rest of the default values in the columns.</span></span> <span data-ttu-id="8103e-243">選取第二個資料列，然後選取**略過**從**項目型別**清單。</span><span class="sxs-lookup"><span data-stu-id="8103e-243">Select the second row and select the **Ignore** from **Element Type** list.</span></span> <span data-ttu-id="8103e-244">當您按一下 [**下一步]**，結構描述中建立項目記錄的下一個層級。</span><span class="sxs-lookup"><span data-stu-id="8103e-244">When you click **Next**, the next level for the items record is created in the schema.</span></span> <span data-ttu-id="8103e-245">您可以繼續定義訂單結構描述的最後一個部分。</span><span class="sxs-lookup"><span data-stu-id="8103e-245">You continue to define the final part of the purchase order schema.</span></span>  

6. <span data-ttu-id="8103e-246">選取 [**項目**，然後按一下**下一步]** 繼續**結構描述檢視**頁面。</span><span class="sxs-lookup"><span data-stu-id="8103e-246">Select **item** and then click **Next** to continue on the **Schema View** page.</span></span>  

7. <span data-ttu-id="8103e-247">在 **選取文件資料**頁面上，選取**ITEM872-AA&#124;割草機&#124;1&#124;148.95&#124;確認這是電動**。</span><span class="sxs-lookup"><span data-stu-id="8103e-247">On the **Select Document Data** page, select **ITEM872-AA&#124;Lawnmower&#124;1&#124;148.95&#124;Confirm this is electric**.</span></span> <span data-ttu-id="8103e-248">按 **[下一步]** ，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8103e-248">Click **Next** to continue.</span></span>  

8. <span data-ttu-id="8103e-249">在 **選取記錄格式**頁面上，選取**依分隔符號**選項，因為個別的項目以管道分隔 (&#124;)。</span><span class="sxs-lookup"><span data-stu-id="8103e-249">On the **Select Record Format** page, select the **By delimiter symbol** option because the individual item is delimited by a pipe (&#124;).</span></span>  

9. <span data-ttu-id="8103e-250">在 **分隔記錄**頁面上，輸入下列命令來定義項目記錄。</span><span class="sxs-lookup"><span data-stu-id="8103e-250">On the **Delimited Record** page, enter the following to define the item record.</span></span> <span data-ttu-id="8103e-251">當您完成之後時，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8103e-251">When you are done, click **Next**.</span></span>  

    -   <span data-ttu-id="8103e-252">選取  **&#124;** 從**子分隔符號**下拉式清單選取項目清單。</span><span class="sxs-lookup"><span data-stu-id="8103e-252">Select **&#124;** from the **Child delimiter** drop down selection list.</span></span>  

    -   <span data-ttu-id="8103e-253">離開**逸出字元**空白的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="8103e-253">Leave the **Escape character** text box blank.</span></span>  

10. <span data-ttu-id="8103e-254">在 **子項目**頁面上，此精靈已識別五個子項目。</span><span class="sxs-lookup"><span data-stu-id="8103e-254">On the **Child Elements** page, the wizard has identified five child elements.</span></span> <span data-ttu-id="8103e-255">選取第一個資料列，並輸入**productCode** for**項目名稱**。</span><span class="sxs-lookup"><span data-stu-id="8103e-255">Select the first row and enter **productCode** for **Element name**.</span></span> <span data-ttu-id="8103e-256">請保留其他欄位中的預設值。</span><span class="sxs-lookup"><span data-stu-id="8103e-256">Leave the default values in the rest of the columns.</span></span> <span data-ttu-id="8103e-257">在其餘**項目名稱屬性**，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="8103e-257">For the rest of the **Element Name properties**, type the following:</span></span>  

    |<span data-ttu-id="8103e-258">元素名稱</span><span class="sxs-lookup"><span data-stu-id="8103e-258">Element Name</span></span>|<span data-ttu-id="8103e-259">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="8103e-259">Value</span></span>|  
    |------------------|-----------|  
    |<span data-ttu-id="8103e-260">**item_Child2**</span><span class="sxs-lookup"><span data-stu-id="8103e-260">**item_Child2**</span></span>|<span data-ttu-id="8103e-261">**description**</span><span class="sxs-lookup"><span data-stu-id="8103e-261">**description**</span></span>|  
    |<span data-ttu-id="8103e-262">**item_Child3**</span><span class="sxs-lookup"><span data-stu-id="8103e-262">**item_Child3**</span></span>|<span data-ttu-id="8103e-263">**數量**</span><span class="sxs-lookup"><span data-stu-id="8103e-263">**quantity**</span></span>|  
    |<span data-ttu-id="8103e-264">**item_Child4**</span><span class="sxs-lookup"><span data-stu-id="8103e-264">**item_Child4**</span></span>|<span data-ttu-id="8103e-265">**單價**</span><span class="sxs-lookup"><span data-stu-id="8103e-265">**unitPrice**</span></span>|  
    |<span data-ttu-id="8103e-266">**item_Child5**</span><span class="sxs-lookup"><span data-stu-id="8103e-266">**item_Child5**</span></span>|<span data-ttu-id="8103e-267">**附註**</span><span class="sxs-lookup"><span data-stu-id="8103e-267">**notes**</span></span>|  

     <span data-ttu-id="8103e-268">按 **[下一步]** ，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8103e-268">Click **Next** to continue.</span></span>  

11. <span data-ttu-id="8103e-269">您已定義訂單結構描述的所有節點。</span><span class="sxs-lookup"><span data-stu-id="8103e-269">You have defined all the nodes for the purchase order schema.</span></span> <span data-ttu-id="8103e-270">在 **結構描述檢視**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="8103e-270">On the **Schema View** page, click **Finish**.</span></span>  

12. <span data-ttu-id="8103e-271">您現在可以檢視最後的訂單結構描述。</span><span class="sxs-lookup"><span data-stu-id="8103e-271">You can now view the final purchase order schema.</span></span> <span data-ttu-id="8103e-272">您也可以使用 BizTalk 結構描述編輯器修改此結構描述。</span><span class="sxs-lookup"><span data-stu-id="8103e-272">You can also refine the schema by using the BizTalk Schema Editor.</span></span> <span data-ttu-id="8103e-273">一般檔案屬性名稱資料表及屬性資料表中的，請參閱 <<c0>  **結構描述節點屬性**。</span><span class="sxs-lookup"><span data-stu-id="8103e-273">See Flat file property name table and the Property tables in **Schema Node Properties**.</span></span> <span data-ttu-id="8103e-274">這個屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="8103e-274">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="summary"></a><span data-ttu-id="8103e-275">摘要</span><span class="sxs-lookup"><span data-stu-id="8103e-275">Summary</span></span>  
 <span data-ttu-id="8103e-276">在此逐步解說中，您學習到如何使用 BizTalk 一般檔案結構描述精靈，從文件執行個體建立一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="8103e-276">In this walkthrough you have learned how to use the BizTalk Flat File Schema Wizard to create a flat file schema from a document instance.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="8103e-277">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8103e-277">Next Steps</span></span>  

### <a name="validate-po-instance"></a><span data-ttu-id="8103e-278">驗證 PO 執行個體</span><span class="sxs-lookup"><span data-stu-id="8103e-278">Validate PO Instance</span></span>  
 <span data-ttu-id="8103e-279">若要確定 PurchaseOrder.xsd 結構描述可以正確剖析 PO 執行個體，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8103e-279">To ensure that the PurchaseOrder.xsd schema can correctly parse the PO instance, do the following:</span></span>  

1.  <span data-ttu-id="8103e-280">在 [方案總管] 中，以滑鼠右鍵按一下**PurchaseOrder.xsd** ，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8103e-280">In Solution Explorer, right-click the **PurchaseOrder.xsd** and then select **Properties**.</span></span>  

2.  <span data-ttu-id="8103e-281">在 **屬性頁**，請確定**輸入執行個體檔案名稱**欄位指向您在逐步解說必要條件一節中建立的 PO 執行個體的位置： 建立一般檔案從文件執行個體的結構描述。</span><span class="sxs-lookup"><span data-stu-id="8103e-281">In the **Property Pages**, make sure that the **Input Instance Filename** field is pointing to the location of the PO instance you created in the Prerequisites section of Walkthrough: Creating a Flat File Schema From a Document Instance.</span></span> <span data-ttu-id="8103e-282">按一下 **確定**以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8103e-282">Click **OK** to close the dialog.</span></span>  

3.  <span data-ttu-id="8103e-283">在 [方案總管] 中，以滑鼠右鍵按一下**PurchaseOrder.xsd**，然後選取**驗證執行個體**。</span><span class="sxs-lookup"><span data-stu-id="8103e-283">In Solution Explorer, right-click **PurchaseOrder.xsd**, and then select **Validate Instance**.</span></span> <span data-ttu-id="8103e-284">驗證元件就會開啟。</span><span class="sxs-lookup"><span data-stu-id="8103e-284">The validation component opens.</span></span>  

4.  <span data-ttu-id="8103e-285">驗證完成後，會提供一個連結，讓您根據使用 PurchaseOrder.xsd 結構描述所得到的 PO 執行個體剖析結果來檢視 XML 輸出。</span><span class="sxs-lookup"><span data-stu-id="8103e-285">After validation is completed, a link is provided to you for viewing the XML output based on parsing result on PO instance using the PurchaseOrder.xsd schema.</span></span> <span data-ttu-id="8103e-286">若要檢視 XML 輸出，請按住 Ctrl 並按一下該連結。</span><span class="sxs-lookup"><span data-stu-id="8103e-286">To view the XML output, press Ctrl and click the link.</span></span>  

### <a name="create-pipelines-for-the-schema"></a><span data-ttu-id="8103e-287">結構描述中建立管線</span><span class="sxs-lookup"><span data-stu-id="8103e-287">Create Pipelines for the Schema</span></span>  
 <span data-ttu-id="8103e-288">現在您可根據 PurchaseOrder.xsd 結構描述建立接收或傳送管線，以搭配 BizTalk 應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="8103e-288">Now you can create a receive or send pipeline based on the PurchaseOrder.xsd schema to use with your BizTalk application.</span></span>  

 <span data-ttu-id="8103e-289">若要建立新的管線，請參閱[如何建立新管線](../core/how-to-create-a-new-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="8103e-289">To create a new pipeline, see [How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md).</span></span> <span data-ttu-id="8103e-290">若要設定一般檔案管線元件，請參閱[如何設定一般檔案組合器管線元件](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)並[如何設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8103e-290">To configure the Flat File Pipeline components, see [How to Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md) and [How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="8103e-291">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8103e-291">See Also</span></span>  
 <span data-ttu-id="8103e-292">[如何使用 BizTalk 一般檔案結構描述精靈](../core/how-to-use-biztalk-flat-file-schema-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="8103e-292">[How to Use BizTalk Flat File Schema Wizard](../core/how-to-use-biztalk-flat-file-schema-wizard.md) </span></span>  
 [<span data-ttu-id="8103e-293">使用 BizTalk 一般檔案結構描述精靈建立結構描述</span><span class="sxs-lookup"><span data-stu-id="8103e-293">Creating Schemas Using BizTalk Flat File Schema Wizard</span></span>](../core/creating-schemas-using-biztalk-flat-file-schema-wizard.md)