---
title: 若要建立報表伺服器專案中使用的 Data Provider for SAP |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fe985b5-ba67-4179-a31c-4f41106c32be
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9c7905fc7114feeca8b53589e1aa32a09495ca1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962756"
---
# <a name="use-the-data-provider-for-sap-to-create-a-report-server-project"></a><span data-ttu-id="6480c-102">若要建立報表伺服器專案中使用 SAP 的資料提供者</span><span class="sxs-lookup"><span data-stu-id="6480c-102">Use the Data Provider for SAP to Create a Report Server Project</span></span>
<span data-ttu-id="6480c-103">您必須建立報表伺服器專案、 使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，以產生報告的 SAP 系統中可用的資料。</span><span class="sxs-lookup"><span data-stu-id="6480c-103">You must create a Report Server project, using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], to generate reports for the data available in an SAP system.</span></span> <span data-ttu-id="6480c-104">本主題說明如何建立報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="6480c-104">This topic provides instructions on how to create a Report Server project.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6480c-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="6480c-105">Prerequisites</span></span>  
 <span data-ttu-id="6480c-106">然後再執行本主題提供的程序，請確定您安裝[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]安裝時[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]一部分[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="6480c-106">Before performing the procedures provided in this topic, make sure you installed the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] while installing the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as part of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation.</span></span> <span data-ttu-id="6480c-107">如需有關[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝，請參閱安裝指南位於\<*安裝磁碟機*\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。</span><span class="sxs-lookup"><span data-stu-id="6480c-107">For more information about [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, refer to the installation guide available at \<*installation drive*\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span></span>  
  
### <a name="to-create-a-report-server-project"></a><span data-ttu-id="6480c-108">若要建立報表伺服器專案</span><span class="sxs-lookup"><span data-stu-id="6480c-108">To create a Report Server project</span></span>  
  
1.  <span data-ttu-id="6480c-109">啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並建立報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="6480c-109">Start [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and create a Report Server project.</span></span> <span data-ttu-id="6480c-110">若要建立報表伺服器專案時，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="6480c-110">To create a Report Server project, do the following:</span></span>  
  
    1.  <span data-ttu-id="6480c-111">按一下**檔案**功能表上，按一下 **新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="6480c-111">Click the **File** menu, click **New**, and then click **Project**.</span></span>  
  
    2.  <span data-ttu-id="6480c-112">在**新專案**對話方塊中，從**專案類型**清單中，選取**商業智慧專案**。</span><span class="sxs-lookup"><span data-stu-id="6480c-112">In the **New Project** dialog box, from the **Project types** list, select **Business Intelligence Projects**.</span></span> <span data-ttu-id="6480c-113">從**Visual Studio 安裝的範本**清單中，選取**報表伺服器專案**。</span><span class="sxs-lookup"><span data-stu-id="6480c-113">From **the Visual Studio installed templates** list, select **Report Server Project**.</span></span>  
  
    3.  <span data-ttu-id="6480c-114">指定的名稱和專案的位置，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6480c-114">Specify a name and location of the project and click **OK**.</span></span> <span data-ttu-id="6480c-115">本主題中，指定專案名稱做為`SAP_ Report`。</span><span class="sxs-lookup"><span data-stu-id="6480c-115">For this topic, specify the name of the project as `SAP_ Report`.</span></span>  
  
2.  <span data-ttu-id="6480c-116">加入新的資料來源：</span><span class="sxs-lookup"><span data-stu-id="6480c-116">Add a new data source:</span></span>  
  
    1.  <span data-ttu-id="6480c-117">從 [方案總管] 中，以滑鼠右鍵按一下**共用資料來源**，然後按一下**加入新資料來源**。</span><span class="sxs-lookup"><span data-stu-id="6480c-117">From the Solution Explorer, right-click **Shared Data Sources**, and click **Add New Data Source**.</span></span>  
  
    2.  <span data-ttu-id="6480c-118">在**共用資料來源**對話方塊中，於**一般**索引標籤上，指定資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="6480c-118">In the **Shared Data Source** dialog box, in the **General** tab, specify a name for the data source.</span></span> <span data-ttu-id="6480c-119">如本主題中，將名稱指定為`SAPDataSource`。</span><span class="sxs-lookup"><span data-stu-id="6480c-119">For this topic, specify the name as `SAPDataSource`.</span></span>  
  
    3.  <span data-ttu-id="6480c-120">從**類型**清單中，選取**Data Provider for SAP**。</span><span class="sxs-lookup"><span data-stu-id="6480c-120">From the **Type** list, select **Data Provider for SAP**.</span></span>  
  
    4.  <span data-ttu-id="6480c-121">在**連接字串**方塊中，指定的連接字串[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6480c-121">In the **Connection String** box, specify the connection string for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span> <span data-ttu-id="6480c-122">如需有關資訊[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連接字串，請參閱[閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="6480c-122">For information about the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] connection string, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
         <span data-ttu-id="6480c-123">![建立資料來源](../../adapters-and-accelerators/adapter-sap/media/8494c1a5-5e68-4178-a005-a6ea56d97ad7.gif "8494c1a5-5e68-4178-a005-a6ea56d97ad7")</span><span class="sxs-lookup"><span data-stu-id="6480c-123">![Create a data source](../../adapters-and-accelerators/adapter-sap/media/8494c1a5-5e68-4178-a005-a6ea56d97ad7.gif "8494c1a5-5e68-4178-a005-a6ea56d97ad7")</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6480c-124">您可以選擇隨連接字串中指定的認證，或者在下一個步驟中所述的方式指定。</span><span class="sxs-lookup"><span data-stu-id="6480c-124">You can choose to specify the credentials as part of the connection string or specify them as described in the next step.</span></span>  
  
    5.  <span data-ttu-id="6480c-125">在**認證**索引標籤上，選擇下列其中一種，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="6480c-125">In the **Credentials** tab, choose one of the following, and then click **OK**:</span></span>  
  
        |<span data-ttu-id="6480c-126">使用</span><span class="sxs-lookup"><span data-stu-id="6480c-126">Use this</span></span>|<span data-ttu-id="6480c-127">動作</span><span class="sxs-lookup"><span data-stu-id="6480c-127">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="6480c-128">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="6480c-128">**Use a specific user name and password**</span></span>|<span data-ttu-id="6480c-129">指定使用者名稱和密碼以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="6480c-129">Specify a user name and password to connect to the SAP system.</span></span>|  
        |<span data-ttu-id="6480c-130">**提示認證**</span><span class="sxs-lookup"><span data-stu-id="6480c-130">**Prompt for credentials**</span></span>|<span data-ttu-id="6480c-131">產生報表時，輸入 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="6480c-131">Enter the credentials for the SAP system while the report is generated.</span></span> <span data-ttu-id="6480c-132">**注意：** 認證您指定這個選項會覆寫認證，如果指定，做為連接字串的一部分。</span><span class="sxs-lookup"><span data-stu-id="6480c-132">**Note:**  The credentials you specify for this option will override the credentials, if specified, as part of the connection string.</span></span>|  
        |<span data-ttu-id="6480c-133">**無認證**</span><span class="sxs-lookup"><span data-stu-id="6480c-133">**No credentials**</span></span>|<span data-ttu-id="6480c-134">如果您要提供使用者名稱和密碼做為連接字串的一部分，請選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="6480c-134">Choose this option if you are providing the user name and password as part of the connection string.</span></span>|  
  
        > [!NOTE]
        >  <span data-ttu-id="6480c-135">Windows 驗證模式不支援報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="6480c-135">The Windows Authentication mode is not supported for Report Server projects.</span></span>  
  
3.  <span data-ttu-id="6480c-136">加入新的報表：</span><span class="sxs-lookup"><span data-stu-id="6480c-136">Add a new report:</span></span>  
  
    1.  <span data-ttu-id="6480c-137">從 方案總管 中，以滑鼠右鍵按一下**報表**，然後按一下 **加入新的報表**。</span><span class="sxs-lookup"><span data-stu-id="6480c-137">From the Solution Explorer, right-click **Reports**, and then click **Add New Report**.</span></span>  
  
         <span data-ttu-id="6480c-138">這樣會啟動 [報表精靈]。</span><span class="sxs-lookup"><span data-stu-id="6480c-138">This starts the Report Wizard.</span></span>  
  
    2.  <span data-ttu-id="6480c-139">閱讀 [歡迎] 畫面上的資訊，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6480c-139">Read the information on the welcome screen, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="6480c-140">在**選取資料來源**對話方塊方塊中，選擇**共用資料來源**選項，然後選取**SAPDataSource**您在上一個步驟中建立，然後按一下  **下一步**。</span><span class="sxs-lookup"><span data-stu-id="6480c-140">In the **Select the Data Source** dialog box, choose the **Shared data source** option, select the **SAPDataSource** you created in the previous step, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="6480c-141">如果您選擇**提示認證**選項來建立資料來源時指定的使用者認證**輸入資料來源認證** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="6480c-141">If you chose the **Prompt for credentials** option to specify the user credentials while creating the data source, an **Enter Data Source Credentials** dialog box appears.</span></span> <span data-ttu-id="6480c-142">指定使用者名稱和密碼以連接至 SAP 系統，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6480c-142">Specify the user name and password to connect to the SAP system, and then click **OK**.</span></span>  
  
         <span data-ttu-id="6480c-143">如果您選擇任何其他選項來指定認證，此精靈會繼續下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="6480c-143">If you chose any other option for specifying credentials, the wizard proceeds to the next step.</span></span>  
  
    5.  <span data-ttu-id="6480c-144">在**設計查詢**對話方塊方塊中，指定用來產生報表的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="6480c-144">In the **Design the Query** dialog box, specify a query string that is used to generate a report.</span></span> <span data-ttu-id="6480c-145">例如：</span><span class="sxs-lookup"><span data-stu-id="6480c-145">For example:</span></span>  
  
        ```  
        SELECT TOP 2 KUNNR, NAME1 FROM KNA1 WHERE NAME1 LIKE @PARAM  
        ```  
  
         <span data-ttu-id="6480c-146">此查詢會從 NAME1 其中是產生報表時，您將指定的名稱 KNA1 資料表中擷取前兩筆記錄。</span><span class="sxs-lookup"><span data-stu-id="6480c-146">This query will retrieve the top two records from the KNA1 table where the NAME1 is the name that you will specify while generating the report.</span></span>  
  
         <span data-ttu-id="6480c-147">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="6480c-147">Click **Next**.</span></span>  
  
    6.  <span data-ttu-id="6480c-148">在後續的對話方塊中，您可以設計想要顯示報表的格式。</span><span class="sxs-lookup"><span data-stu-id="6480c-148">In the subsequent dialog boxes you can design the format in which you want the report to appear.</span></span> <span data-ttu-id="6480c-149">如果您想要使用的預設格式，請按一下**完成 >> &#124;** ，直接移至**完成** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6480c-149">If you want to use the default format, click **Finish >>&#124;** to directly go to the **Finish** dialog box.</span></span>  
  
    7.  <span data-ttu-id="6480c-150">在**正在完成精靈**對話方塊中，指定報表的名稱，檢閱 [摘要]，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="6480c-150">In the **Completing the Wizard** dialog box, specify a name for the report, review the summary, and then click **Finish**.</span></span> <span data-ttu-id="6480c-151">本主題中，指定做為報表名稱`SAPReport`。</span><span class="sxs-lookup"><span data-stu-id="6480c-151">For this topic, specify the name of the report as `SAPReport`.</span></span>  
  
     <span data-ttu-id="6480c-152">您現在可以檢視報表。</span><span class="sxs-lookup"><span data-stu-id="6480c-152">You can now view the report.</span></span> <span data-ttu-id="6480c-153">如需有關如何檢視報表的指示，請參閱[檢視適用於 SAP 報表](../../adapters-and-accelerators/adapter-sap/view-the-reports-for-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="6480c-153">For instructions about how to view the report, see [view the Reports for SAP](../../adapters-and-accelerators/adapter-sap/view-the-reports-for-sap.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6480c-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="6480c-154">See Also</span></span>  
 [<span data-ttu-id="6480c-155">搭配使用 Data Provider for SAP 與 SSRS</span><span class="sxs-lookup"><span data-stu-id="6480c-155">Use the Data Provider for SAP with SSRS</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssrs.md)