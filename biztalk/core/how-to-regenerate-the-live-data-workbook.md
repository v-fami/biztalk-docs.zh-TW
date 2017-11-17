---
title: "如何重新產生即時資料活頁簿 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bd3a3fa-a550-4363-bbc0-2153226509ad
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fcabebb1429fae8531753a8a3aede5595bb148f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-regenerate-the-live-data-workbook"></a><span data-ttu-id="ac09e-102">如何重新產生即時資料活頁簿</span><span class="sxs-lookup"><span data-stu-id="ac09e-102">How to Regenerate the Live Data Workbook</span></span>
<span data-ttu-id="ac09e-103">在 BAM 即時資料活頁簿所在遺失或損毀的情況下，您可以重新產生使用 BAM 管理 utiprolity 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="ac09e-103">In cases where the BAM live data workbook has been lost or corrupted, you can regenerate the workbook using the BAM Management utiprolity.</span></span> <span data-ttu-id="ac09e-104">若您是從 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 升級到 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，這種做法也相當實用，因為 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 的即時資料活頁簿與 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 並不相容。</span><span class="sxs-lookup"><span data-stu-id="ac09e-104">This process is also useful when you are upgrading from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], since live data workbooks for [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] are not compatible with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
 <span data-ttu-id="ac09e-105">一般步驟如下：</span><span class="sxs-lookup"><span data-stu-id="ac09e-105">The general steps are as follows:</span></span>  
  
-   <span data-ttu-id="ac09e-106">使用 BAM 管理公用程式，從 BAM 資料庫擷取 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="ac09e-106">Retrieve the BAM definition from the BAM database using the BAM Management utility.</span></span>  
  
-   <span data-ttu-id="ac09e-107">重新建立樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="ac09e-107">Re-create the PivotTable reports.</span></span> <span data-ttu-id="ac09e-108">由於 get-defxml 命令所擷取的 XML 只包含活動和檢視，您必須使用 Excel 的 BAM 增益集重新建立樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="ac09e-108">Since the XML retrieval by the get-defxml command contains only the activities and views, you must re-create the PivotTable reports using the BAM Add-in for Excel.</span></span>  
  
-   <span data-ttu-id="ac09e-109">重新命名樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="ac09e-109">Rename the PivotTable reports.</span></span> <span data-ttu-id="ac09e-110">若您是從 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 升級到 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，就必須執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="ac09e-110">This step is necessary if you are upgrading from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span> <span data-ttu-id="ac09e-111">這是因為必要的[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]，BAM 會儲存兩組 BAM 活頁簿的名稱： 顯示名稱和內部名稱。</span><span class="sxs-lookup"><span data-stu-id="ac09e-111">This is necessary since in [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)], BAM stores two sets of names for BAM workbooks: a display name and an internal name.</span></span> <span data-ttu-id="ac09e-112">當您擷取 BAM 定義時，XML 將包含活頁簿的內部名稱。</span><span class="sxs-lookup"><span data-stu-id="ac09e-112">When you retrieve the BAM definition, the XML contains the internal name for the workbook.</span></span> <span data-ttu-id="ac09e-113">您必須重新命名樞紐分析表，以確保即時資料活頁簿與資料庫的連線正確。</span><span class="sxs-lookup"><span data-stu-id="ac09e-113">You must rename the PivotTable reports to ensure that the live data workbook has the correct connection to the database.</span></span>  
  
-   <span data-ttu-id="ac09e-114">使用 BAM 管理公用程式重新產生即時資料活頁簿。</span><span class="sxs-lookup"><span data-stu-id="ac09e-114">Regenerate the live data workbook using the BAM Management utility.</span></span>  
  
### <a name="to-retrieve-the-bam-definition"></a><span data-ttu-id="ac09e-115">若要擷取 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="ac09e-115">To retrieve the BAM definition</span></span>  
  
1.  <span data-ttu-id="ac09e-116">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac09e-116">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="ac09e-117">在命令提示字元中，瀏覽至下列目錄：[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="ac09e-117">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="ac09e-118">類型： **bm.exe get defxml-FileName:abc.xml**</span><span class="sxs-lookup"><span data-stu-id="ac09e-118">Type: **bm.exe get-defxml -FileName:abc.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac09e-119">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="ac09e-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-re-create-the-pivottable-reports"></a><span data-ttu-id="ac09e-120">若要重新建立樞紐分析表</span><span class="sxs-lookup"><span data-stu-id="ac09e-120">To re-create the PivotTable reports</span></span>  
  
1.  <span data-ttu-id="ac09e-121">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office**，然後按一下  **Microsoft Office Excel**。</span><span class="sxs-lookup"><span data-stu-id="ac09e-121">Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office Excel**.</span></span>  
  
2.  <span data-ttu-id="ac09e-122">按一下**增益集**索引標籤，然後選取**匯入 XML**從**BAM**下拉式清單中的**功能表命令**群組。</span><span class="sxs-lookup"><span data-stu-id="ac09e-122">Click the **Add-Ins** tab, and then select **Import XML** from the **BAM** drop-down list in the **Menu Commands** group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac09e-123">如果**增益集** 索引標籤不存在，請依照下列中的指示[步驟 1： 加入 Microsoft Office Excel 的 BAM 增益集](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)新增 BAM 增益集。</span><span class="sxs-lookup"><span data-stu-id="ac09e-123">If the **Add-Ins** tab is not present, follow the instructions in [Step 1: Add the BAM Add-In to Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448) to add the BAM add-in.</span></span>  
  
3.  <span data-ttu-id="ac09e-124">瀏覽至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking資料夾並選取 abc.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="ac09e-124">Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking folder and select the abc.xml file.</span></span>  
  
4.  <span data-ttu-id="ac09e-125">根據您的定義重新建立樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="ac09e-125">Re-create your PivotTable reports based on your definition.</span></span>  
  
5.  <span data-ttu-id="ac09e-126">儲存活頁簿。</span><span class="sxs-lookup"><span data-stu-id="ac09e-126">Save the workbook.</span></span> <span data-ttu-id="ac09e-127">若要這樣做，請按一下**檔案**功能表，然後再按一下**存**並提示您輸入檔案名稱時輸入 mynewbook.xls。</span><span class="sxs-lookup"><span data-stu-id="ac09e-127">To do this, click the **File** menu, and then click **Save As** and type mynewbook.xls when prompted for a file name.</span></span>  
  
### <a name="to-rename-the-pivottable-reports-optional"></a><span data-ttu-id="ac09e-128">若要重新命名樞紐分析表 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="ac09e-128">To rename the PivotTable reports (optional)</span></span>  
  
1.  <span data-ttu-id="ac09e-129">開啟您在擷取 BAM 定義，即可使用 「 記事本 」 時所建立的 abc.xml 檔案**啟動**，然後按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\abc.xml，，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="ac09e-129">Open the abc.xml file that you created when you retrieved the BAM definitions using Notepad by clicking **Start**, clicking **Run**, typing notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\abc.xml, and then clicking **OK**.</span></span>  
  
2.  <span data-ttu-id="ac09e-130">找出\<標題 > 標記下方\<c a p >\\< 延伸模組\>\\< OWC\>\\< 樞紐分析表檢視\>\\<樞紐分析表\>\\< 樞紐分析檢視\>\\< 標籤\>。</span><span class="sxs-lookup"><span data-stu-id="ac09e-130">Locate the \<Caption> tag under \<BAMDefinition>\\<Extension\>\\<OWC\>\\<PivotTableView\>\\<PivotTable\>\\<PivotView\>\\<Label\>.</span></span> <span data-ttu-id="ac09e-131">此標記的內容就是其中一份樞紐分析表的內部名稱。</span><span class="sxs-lookup"><span data-stu-id="ac09e-131">The content of this tag is the internal name for one of your PivotTable reports.</span></span> <span data-ttu-id="ac09e-132">您可以找到其他樞紐分析表報表的內部名稱找出下一步，藉以\<標題 > 標記。</span><span class="sxs-lookup"><span data-stu-id="ac09e-132">You can find the internal name for the other PivotTable reports by locating the next \<Caption> tag.</span></span> <span data-ttu-id="ac09e-133">開啟**mynewbook.xls**並用您位於 要重新命名樞紐分析表報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="ac09e-133">Open **mynewbook.xls** and use the names you located to rename your PivotTable reports.</span></span>  
  
3.  <span data-ttu-id="ac09e-134">儲存更新後的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="ac09e-134">Save the updated workbook.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac09e-135">只有當您是從 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 升級到 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 時，才需要執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="ac09e-135">You must follow this procedure only if you are upgrading from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
### <a name="to-regenerate-the-bam-live-data-workbook"></a><span data-ttu-id="ac09e-136">若要重新產生 BAM 即時資料活頁簿</span><span class="sxs-lookup"><span data-stu-id="ac09e-136">To regenerate the BAM live data workbook</span></span>  
  
1.  <span data-ttu-id="ac09e-137">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac09e-137">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="ac09e-138">在命令提示字元中，瀏覽至下列目錄：[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="ac09e-138">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="ac09e-139">類型： **bm.exe regenerate livedataworkbook-WorkbookName:mynewbook.xls**</span><span class="sxs-lookup"><span data-stu-id="ac09e-139">Type: **bm.exe regenerate-livedataworkbook -WorkbookName:mynewbook.xls**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac09e-140">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="ac09e-140">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac09e-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac09e-141">See Also</span></span>  
 <span data-ttu-id="ac09e-142">[管理 BAM](../core/managing-bam.md) </span><span class="sxs-lookup"><span data-stu-id="ac09e-142">[Managing BAM](../core/managing-bam.md) </span></span>  
 <span data-ttu-id="ac09e-143">[BAM 管理公用程式](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ac09e-143">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 <span data-ttu-id="ac09e-144">[適用於 Excel 的 BAM 增益集使用的需求](../core/requirements-for-using-the-bam-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="ac09e-144">[Requirements for Using the BAM Add-In for Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="ac09e-145">步驟 1： 新增 BAM 增益集至 Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="ac09e-145">Step 1: Add the BAM Add-In to Microsoft Office Excel</span></span>](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)