---
title: "重新產生即時資料活頁簿 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bd3a3fa-a550-4363-bbc0-2153226509ad
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fabecd70c39f7bae14765a35c510f5c62c3814a9
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="regenerate-the-live-data-workbook"></a><span data-ttu-id="65ca1-102">重新產生即時資料活頁簿</span><span class="sxs-lookup"><span data-stu-id="65ca1-102">Regenerate the Live Data Workbook</span></span>
<span data-ttu-id="65ca1-103">在 BAM 即時資料活頁簿所在遺失或損毀的情況下，您可以重新產生活頁簿使用 BAM 管理 utiprolity。</span><span class="sxs-lookup"><span data-stu-id="65ca1-103">In cases where the BAM live data workbook has been lost or corrupted, you can regenerate the workbook using the BAM Management utiprolity.</span></span> <span data-ttu-id="65ca1-104">從升級從舊版 BizTalk Server 時，此程序也很有用。</span><span class="sxs-lookup"><span data-stu-id="65ca1-104">This process is also useful when you are upgrading from from previous BizTalk Server versions.</span></span>
  
 <span data-ttu-id="65ca1-105">一般步驟如下：</span><span class="sxs-lookup"><span data-stu-id="65ca1-105">The general steps are as follows:</span></span>  
  
-   <span data-ttu-id="65ca1-106">使用 BAM 管理公用程式，從 BAM 資料庫擷取 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="65ca1-106">Retrieve the BAM definition from the BAM database using the BAM Management utility.</span></span>  
  
-   <span data-ttu-id="65ca1-107">重新建立樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="65ca1-107">Re-create the PivotTable reports.</span></span> <span data-ttu-id="65ca1-108">由於 get-defxml 命令所擷取的 XML 只包含活動和檢視，您必須使用 Excel 的 BAM 增益集重新建立樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="65ca1-108">Since the XML retrieval by the get-defxml command contains only the activities and views, you must re-create the PivotTable reports using the BAM Add-in for Excel.</span></span>  
  
-   <span data-ttu-id="65ca1-109">重新命名樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="65ca1-109">Rename the PivotTable reports.</span></span> <span data-ttu-id="65ca1-110">此步驟可能需要如果您要升級從舊版 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="65ca1-110">This step may be necessary if you are upgrading from a previous BizTalk Server version.</span></span> <span data-ttu-id="65ca1-111">某些版本中，BAM 會儲存兩組 BAM 活頁簿的名稱： 顯示名稱和內部名稱。</span><span class="sxs-lookup"><span data-stu-id="65ca1-111">With some versions, BAM stores two sets of names for BAM workbooks: a display name and an internal name.</span></span> <span data-ttu-id="65ca1-112">當您擷取 BAM 定義時，XML 將包含活頁簿的內部名稱。</span><span class="sxs-lookup"><span data-stu-id="65ca1-112">When you retrieve the BAM definition, the XML contains the internal name for the workbook.</span></span> <span data-ttu-id="65ca1-113">您必須重新命名樞紐分析表，以確保即時資料活頁簿與資料庫的連線正確。</span><span class="sxs-lookup"><span data-stu-id="65ca1-113">You must rename the PivotTable reports to ensure that the live data workbook has the correct connection to the database.</span></span>  
  
-   <span data-ttu-id="65ca1-114">使用 BAM 管理公用程式重新產生即時資料活頁簿。</span><span class="sxs-lookup"><span data-stu-id="65ca1-114">Regenerate the live data workbook using the BAM Management utility.</span></span>  
  
## <a name="retrieve-the-bam-definition"></a><span data-ttu-id="65ca1-115">擷取 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="65ca1-115">Retrieve the BAM definition</span></span>  
  
1.  <span data-ttu-id="65ca1-116">按一下  **啟動**, ，按一下  **執行**, ，型別 **cmd**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="65ca1-116">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="65ca1-117">在命令提示字元中，瀏覽至下列目錄： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking。</span><span class="sxs-lookup"><span data-stu-id="65ca1-117">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking.</span></span>  
  
3.  <span data-ttu-id="65ca1-118">類型︰ **bm.exe get defxml-FileName:abc.xml**</span><span class="sxs-lookup"><span data-stu-id="65ca1-118">Type: **bm.exe get-defxml -FileName:abc.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65ca1-119">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="65ca1-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="recreate-the-pivottable-reports"></a><span data-ttu-id="65ca1-120">重新建立樞紐分析表報表</span><span class="sxs-lookup"><span data-stu-id="65ca1-120">Recreate the PivotTable reports</span></span>  
  
1.  <span data-ttu-id="65ca1-121">按一下  **啟動**, ，指向  **所有程式**, ，指向  **Microsoft Office**, ，然後按一下  **Microsoft Office Excel**。</span><span class="sxs-lookup"><span data-stu-id="65ca1-121">Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office Excel**.</span></span>  
  
2.  <span data-ttu-id="65ca1-122">按一下  **增益集** 索引標籤，然後選取 **匯入 XML** 從 **BAM** 下拉式清單中的 **功能表命令** 群組。</span><span class="sxs-lookup"><span data-stu-id="65ca1-122">Click the **Add-Ins** tab, and then select **Import XML** from the **BAM** drop-down list in the **Menu Commands** group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65ca1-123">如果**增益集** 索引標籤不存在，請依照下列中的指示[步驟 1： 加入 Microsoft Office Excel 的 BAM 增益集](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)新增 BAM 增益集。</span><span class="sxs-lookup"><span data-stu-id="65ca1-123">If the **Add-Ins** tab is not present, follow the instructions in [Step 1: Add the BAM Add-In to Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448) to add the BAM add-in.</span></span>  
  
3.  <span data-ttu-id="65ca1-124">瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking 資料夾，然後選取 abc.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="65ca1-124">Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking folder and select the abc.xml file.</span></span>  
  
4.  <span data-ttu-id="65ca1-125">根據您的定義重新建立樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="65ca1-125">Re-create your PivotTable reports based on your definition.</span></span>  
  
5.  <span data-ttu-id="65ca1-126">儲存活頁簿。</span><span class="sxs-lookup"><span data-stu-id="65ca1-126">Save the workbook.</span></span> <span data-ttu-id="65ca1-127">若要這樣做，請按一下  **檔案** 功能表，然後再按一下 **另存新檔** 並提示您輸入檔案名稱時輸入 mynewbook.xls。</span><span class="sxs-lookup"><span data-stu-id="65ca1-127">To do this, click the **File** menu, and then click **Save As** and type mynewbook.xls when prompted for a file name.</span></span>  
  
## <a name="rename-the-pivottable-reports-optional"></a><span data-ttu-id="65ca1-128">重新命名樞紐分析表報表 （選擇性）</span><span class="sxs-lookup"><span data-stu-id="65ca1-128">Rename the PivotTable reports (optional)</span></span>  

> [!NOTE]
> <span data-ttu-id="65ca1-129">如果您要升級從舊版的 BizTalk Server，可能才需要此步驟。</span><span class="sxs-lookup"><span data-stu-id="65ca1-129">This step may only be required if you are upgrading from an older version of BizTalk Server.</span></span> 

1.  <span data-ttu-id="65ca1-130">開啟您在擷取 BAM 定義，即可使用 「 記事本 」 時所建立的 abc.xml 檔案**啟動**，然後按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking\abc.xml，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="65ca1-130">Open the abc.xml file that you created when you retrieved the BAM definitions using Notepad by clicking **Start**, clicking **Run**, typing notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking\abc.xml, and then clicking **OK**.</span></span>  
  
2.  <span data-ttu-id="65ca1-131">找出\<標題\>標記下\<<bamdefinition>\<extension>\<owc>\<pivottableview>\<pivottable>\<pivotview>\<label>\>\\< 延伸模組\>\\< OWC\>\\< 樞紐分析表檢視\> \\< 樞紐分析表\>\\< 樞紐分析檢視\>\\< 標籤\>。</span><span class="sxs-lookup"><span data-stu-id="65ca1-131">Locate the \<Caption\> tag under \<BAMDefinition\>\\<Extension\>\\<OWC\>\\<PivotTableView\>\\<PivotTable\>\\<PivotView\>\\<Label\>.</span></span> <span data-ttu-id="65ca1-132">此標記的內容就是其中一份樞紐分析表的內部名稱。</span><span class="sxs-lookup"><span data-stu-id="65ca1-132">The content of this tag is the internal name for one of your PivotTable reports.</span></span> <span data-ttu-id="65ca1-133">您可以找到其他樞紐分析表報表的內部名稱找出下一步，藉以\<標題\>標記。</span><span class="sxs-lookup"><span data-stu-id="65ca1-133">You can find the internal name for the other PivotTable reports by locating the next \<Caption\> tag.</span></span> <span data-ttu-id="65ca1-134">開啟 **mynewbook.xls** ，並使用您位於 重新命名樞紐分析表報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="65ca1-134">Open **mynewbook.xls** and use the names you located to rename your PivotTable reports.</span></span>  
  
3.  <span data-ttu-id="65ca1-135">儲存更新後的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="65ca1-135">Save the updated workbook.</span></span>    
 
  
## <a name="regenerate-the-bam-live-data-workbook"></a><span data-ttu-id="65ca1-136">重新產生 BAM 即時資料活頁簿</span><span class="sxs-lookup"><span data-stu-id="65ca1-136">Regenerate the BAM live data workbook</span></span>  

> [!NOTE]
>  <span data-ttu-id="65ca1-137">以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="65ca1-137">Run this tool with Administrative privileges.</span></span>  


1.  <span data-ttu-id="65ca1-138">按一下  **啟動**, ，按一下  **執行**, ，型別 **cmd**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="65ca1-138">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="65ca1-139">在命令提示字元中，瀏覽至下列目錄： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking。</span><span class="sxs-lookup"><span data-stu-id="65ca1-139">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking.</span></span>  
  
3.  <span data-ttu-id="65ca1-140">類型︰ **bm.exe 重新產生 livedataworkbook-WorkbookName:mynewbook.xls**</span><span class="sxs-lookup"><span data-stu-id="65ca1-140">Type: **bm.exe regenerate-livedataworkbook -WorkbookName:mynewbook.xls**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ca1-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65ca1-141">See Also</span></span>  
 <span data-ttu-id="65ca1-142">[管理 BAM](../core/managing-bam.md) </span><span class="sxs-lookup"><span data-stu-id="65ca1-142">[Managing BAM](../core/managing-bam.md) </span></span>  
 <span data-ttu-id="65ca1-143">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="65ca1-143">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 <span data-ttu-id="65ca1-144">[適用於 Excel 的 BAM 增益集使用的需求](../core/requirements-for-using-the-bam-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="65ca1-144">[Requirements for Using the BAM Add-In for Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="65ca1-145">步驟 1： 新增 BAM 增益集至 Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="65ca1-145">Step 1: Add the BAM Add-In to Microsoft Office Excel</span></span>](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)