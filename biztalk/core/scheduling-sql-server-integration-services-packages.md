---
title: "排程 SQL Server Integration Services 封裝 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 037ae2cf-c352-4823-95df-9a723f2b5a81
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a531a5d0a2233dba5826f4bff680a3c55403671d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scheduling-sql-server-integration-services-packages"></a><span data-ttu-id="92fb8-102">排程 SQL Server Integration Services 封裝</span><span class="sxs-lookup"><span data-stu-id="92fb8-102">Scheduling SQL Server Integration Services Packages</span></span>
<span data-ttu-id="92fb8-103">使用者可以根據儲存於線上分析處理 (OLAP) Cube 中的資料建立 BAM 檢視。</span><span class="sxs-lookup"><span data-stu-id="92fb8-103">Users create BAM views based on data stored in an online analytical processing (OLAP) cube.</span></span> <span data-ttu-id="92fb8-104">Cube 更新 Integration Services 封裝會重新整理 Cube 中的資料，如此一來，OLAP 檢視就會反映正確的資料。</span><span class="sxs-lookup"><span data-stu-id="92fb8-104">The Cube Update Integration Services package refreshes the data in the cube so that OLAP views reflect the correct data.</span></span>  
  
 <span data-ttu-id="92fb8-105">您至少必須執行一次這個封裝，OLAP 檢視才能運作。</span><span class="sxs-lookup"><span data-stu-id="92fb8-105">You must run this package at least once for the OLAP views to work.</span></span> <span data-ttu-id="92fb8-106">為便於持續維護，您應該排程定期執行封裝。</span><span class="sxs-lookup"><span data-stu-id="92fb8-106">For ongoing maintenance, you should schedule the package to run on a regular basis.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="92fb8-107">如果您在執行 Cube 更新 Integration Services 封裝之前，還原了 BAM 星狀結構描述資料庫或停止了 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，則必須先重新整理 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 分析管理員中的資料來源或重新啟動 OLAP 服務，然後才能順利執行此封裝。</span><span class="sxs-lookup"><span data-stu-id="92fb8-107">If you restored the BAM Star Schema database or stopped [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] before running the Cube Update Integration Services package, you must refresh the data sources in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager or restart the OLAP service before you can run the package successfully.</span></span>  
  
 <span data-ttu-id="92fb8-108">您可以排程儲存的封裝，使其在特定時間執行，或每隔一段時間重複執行。</span><span class="sxs-lookup"><span data-stu-id="92fb8-108">You can schedule a saved package to execute at specific times, either once or at recurring intervals.</span></span> <span data-ttu-id="92fb8-109">例如：</span><span class="sxs-lookup"><span data-stu-id="92fb8-109">For example:</span></span>  
  
-   <span data-ttu-id="92fb8-110">每天午夜。</span><span class="sxs-lookup"><span data-stu-id="92fb8-110">Daily at midnight.</span></span>  
  
-   <span data-ttu-id="92fb8-111">每週日 06:00。</span><span class="sxs-lookup"><span data-stu-id="92fb8-111">Weekly on Sunday at 06:00.</span></span>  
  
-   <span data-ttu-id="92fb8-112">每月第一天或最後一天。</span><span class="sxs-lookup"><span data-stu-id="92fb8-112">The first or last day of the month.</span></span>  
  
 <span data-ttu-id="92fb8-113">已排程的封裝會由 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 當做作業來執行。</span><span class="sxs-lookup"><span data-stu-id="92fb8-113">A scheduled package is executed by [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] as a job.</span></span>  
  
 <span data-ttu-id="92fb8-114">如需有關執行資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]套件，請參閱[http://go.microsoft.com/fwlink/?LinkId=125738](http://go.microsoft.com/fwlink/?LinkId=125738)。</span><span class="sxs-lookup"><span data-stu-id="92fb8-114">For information about running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] packages, see [http://go.microsoft.com/fwlink/?LinkId=125738](http://go.microsoft.com/fwlink/?LinkId=125738).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92fb8-115">根據預設，針對封存和 cube 的 BAM SSIS 封裝的記錄已開啟，而且會儲存在 msdb 資料庫。</span><span class="sxs-lookup"><span data-stu-id="92fb8-115">By default, logging for archiving and cubing BAM SSIS packages is turned on and is stored in the msdb database.</span></span> <span data-ttu-id="92fb8-116">加班，這可能會導致大量的 SSIS 大量的 BAM 活動所造成的事件記錄檔資料，或經常執行 BAM 擁有 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="92fb8-116">Overtime, this may result in a significant volume of SSIS event log data caused by large number of BAM activities or frequent execution of BAM owned SSIS packages.</span></span> <span data-ttu-id="92fb8-117">若要解決此問題，您可以刪除舊的記錄項目，因為這些項目主要用於偵錯。</span><span class="sxs-lookup"><span data-stu-id="92fb8-117">To resolve this, you can delete the old log entries because these entries are used primarily for debugging.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="92fb8-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="92fb8-118">Prerequisites</span></span>  
 <span data-ttu-id="92fb8-119">您必須以 BizTalk Server 系統管理員群組的成員身分登入，才能執行這些程序。</span><span class="sxs-lookup"><span data-stu-id="92fb8-119">You must be logged on as a member of the BizTalk Server Administrators group to perform these procedures.</span></span>  
  
### <a name="to-run-the-cube-update-integration-services-package"></a><span data-ttu-id="92fb8-120">若要執行 Cube 更新 Integration Services 封裝</span><span class="sxs-lookup"><span data-stu-id="92fb8-120">To run the Cube Update Integration Services package</span></span>  
  
1.  <span data-ttu-id="92fb8-121">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP1**或**Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-121">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="92fb8-122">在**連接到伺服器**對話方塊中，於**伺服器類型**下拉式清單中，選取**Integration Services**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-122">In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="92fb8-123">在**伺服器名稱**下拉式清單中，選取 執行封裝的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="92fb8-123">In the **Server name** drop-down list, select the name of the server on which you are running the package.</span></span>  
  
4.  <span data-ttu-id="92fb8-124">在**驗證**下拉式清單中，選取您用來連接到伺服器的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="92fb8-124">In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.</span></span>  
  
5.  <span data-ttu-id="92fb8-125">必要時，請輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="92fb8-125">If necessary, type your user name and password.</span></span>  
  
6.  <span data-ttu-id="92fb8-126">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-126">Click **Connect**.</span></span>  
  
7.  <span data-ttu-id="92fb8-127">在主控台樹狀目錄中，依序展開**Integration Services**，依序展開**存放的封裝**，然後按一下  **MSDB**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-127">In the console tree, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.</span></span>  
  
8.  <span data-ttu-id="92fb8-128">以滑鼠右鍵按一下**BAM_AN_\<檢視名稱 >**封裝，然後按一下 **執行封裝**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-128">Right-click the **BAM_AN_\<View name>** package, and then click **Run Package**.</span></span>  
  
### <a name="to-run-the-maintaining-bam-data-integration-services-package"></a><span data-ttu-id="92fb8-129">若要執行維護 BAM 資料 Integration Services 封裝</span><span class="sxs-lookup"><span data-stu-id="92fb8-129">To run the Maintaining BAM Data Integration Services package</span></span>  
  
1.  <span data-ttu-id="92fb8-130">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP1**或**Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-130">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="92fb8-131">在**連接到伺服器**對話方塊中，於**伺服器類型**下拉式清單中，選取**Integration Services**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-131">In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="92fb8-132">在**伺服器名稱**下拉式清單中，選取 執行封裝的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="92fb8-132">In the **Server name** drop-down list, select the name of the server on which you are running the package.</span></span>  
  
4.  <span data-ttu-id="92fb8-133">在**驗證**下拉式清單中，選取您用來連接到伺服器的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="92fb8-133">In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.</span></span>  
  
5.  <span data-ttu-id="92fb8-134">必要時，請輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="92fb8-134">If necessary, type your user name and password.</span></span>  
  
6.  <span data-ttu-id="92fb8-135">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-135">Click **Connect**.</span></span>  
  
7.  <span data-ttu-id="92fb8-136">在主控台樹狀目錄中，依序展開**Integration Services**，依序展開**存放的封裝**，然後按一下  **MSDB**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-136">In the console tree, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.</span></span>  
  
8.  <span data-ttu-id="92fb8-137">以滑鼠右鍵按一下**BAM_DM_\<活動名稱 >**封裝，然後按一下 **執行封裝**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-137">Right-click the **BAM_DM_\<Activity name>** package, and then click **Run Package**.</span></span>  
  
### <a name="to-schedule-the-packages-to-run-regularly"></a><span data-ttu-id="92fb8-138">若要將這些封裝排程為定期執行</span><span class="sxs-lookup"><span data-stu-id="92fb8-138">To schedule the packages to run regularly</span></span>  
  
1.  <span data-ttu-id="92fb8-139">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP1**或**Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-139">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="92fb8-140">在**連接到伺服器**對話方塊中，於**伺服器類型**下拉式清單中，選取**Database Engine**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-140">In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Database Engine**.</span></span>  
  
3.  <span data-ttu-id="92fb8-141">在**伺服器名稱**下拉式清單中，選取 執行封裝的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="92fb8-141">In the **Server name** drop-down list, select the name of the server on which you are running the package.</span></span>  
  
4.  <span data-ttu-id="92fb8-142">在**驗證**下拉式清單中，選取您用來連接到伺服器的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="92fb8-142">In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.</span></span>  
  
5.  <span data-ttu-id="92fb8-143">必要時，請輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="92fb8-143">If necessary, type your user name and password.</span></span>  
  
6.  <span data-ttu-id="92fb8-144">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-144">Click **Connect**.</span></span>  
  
7.  <span data-ttu-id="92fb8-145">在主控台樹狀目錄中，展開您的伺服器，並選取**SQL Server Agent**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-145">In the console tree, expand your server, and select **SQL Server Agent**.</span></span>  
  
8.  <span data-ttu-id="92fb8-146">如果**SQL Server Agent**是停用，以滑鼠右鍵按一下**SQL Server Agent**，然後選取**啟動**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-146">If **SQL Server Agent** is disabled, right-click **SQL Server Agent**, and then select **Start**.</span></span>  
  
9. <span data-ttu-id="92fb8-147">以滑鼠右鍵按一下**SQL Server Agent**，然後選取**新工作**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-147">Right-click **SQL Server Agent**, and select  **New Job**.</span></span>  
  
10. <span data-ttu-id="92fb8-148">在**新工作**對話方塊中，輸入的名稱中的作業**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="92fb8-148">In the **New Job** dialog box, type a name for the job in the **Name** text box.</span></span>  
  
11. <span data-ttu-id="92fb8-149">在**選取頁面**視窗中，按一下 **步驟**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-149">In the **Select a page** window, click **Steps**, and then click **New**.</span></span> <span data-ttu-id="92fb8-150">這會開啟**新增作業步驟** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="92fb8-150">This opens the **New Job Step** dialog box.</span></span>  
  
12. <span data-ttu-id="92fb8-151">在**步驟名稱**文字方塊中，輸入步驟的識別名稱。</span><span class="sxs-lookup"><span data-stu-id="92fb8-151">In the **Step name** text box, type an identifying name for the step.</span></span>  
  
13. <span data-ttu-id="92fb8-152">在**類型**下拉式清單中，選取**SQL Server Integration Services 封裝**和**套件來源**下拉式清單中，選取**SSIS 封裝存放區**.</span><span class="sxs-lookup"><span data-stu-id="92fb8-152">In the **Type** drop-down list, select **SQL Server Integration Services Package** and in the **Package source** drop-down list, select **SSIS Package Store**.</span></span>  
  
14. <span data-ttu-id="92fb8-153">在**伺服器**下拉式清單中，選取執行作業的伺服器。</span><span class="sxs-lookup"><span data-stu-id="92fb8-153">In the **Server** drop-down list, select the server on which you are running the job.</span></span>  
  
15. <span data-ttu-id="92fb8-154">按一下 檔案選取器按鈕**封裝**文字方塊中，選取要排程的封裝 (任一**BAM_DM_\<活動名稱 >**或**BAM_AN_\<檢視名稱 >**封裝)，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-154">Click the file selector button for the **Package** text box, select the package you are scheduling (either the **BAM_DM_\<Activity name>** or **BAM_AN_\<View name>** package), and then click **OK**.</span></span>  
  
16. <span data-ttu-id="92fb8-155">在**選取頁面**視窗中，按一下 **排程**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="92fb8-155">In the **Select a page** window, click **Schedules**, and then click **New**.</span></span> <span data-ttu-id="92fb8-156">這會開啟**新增作業排程** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="92fb8-156">This opens the **New Job Schedule** dialog box.</span></span>  
  
17. <span data-ttu-id="92fb8-157">在**名稱** 文字方塊中，輸入排程名稱。</span><span class="sxs-lookup"><span data-stu-id="92fb8-157">In the **Name** text box, type a name for the schedule.</span></span>  
  
18. <span data-ttu-id="92fb8-158">使用頻率欄位建立排程。</span><span class="sxs-lookup"><span data-stu-id="92fb8-158">Create your schedule using the frequency fields.</span></span>  
  
19. <span data-ttu-id="92fb8-159">按一下 **[確定]** 以儲存作業。</span><span class="sxs-lookup"><span data-stu-id="92fb8-159">Click **OK** to save the job.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92fb8-160">如果 BAM 是使用非預設的 SQL Server 執行個體來設定，則 BAM_AN_POCube DTSPackage 就無法正確地進行排程/執行。</span><span class="sxs-lookup"><span data-stu-id="92fb8-160">If BAM is configured with a non-default instance of SQL Server, then the BAM_AN_POCube DTSPackage does not get scheduled/executed accurately.</span></span> <span data-ttu-id="92fb8-161">您必須修改組態檔，才能讓封裝繼續執行。</span><span class="sxs-lookup"><span data-stu-id="92fb8-161">You need to modify the configuration file to allow packages to continue running.</span></span> <span data-ttu-id="92fb8-162">如需詳細資訊，請參閱 < 修改組態檔的內容 」 一節[http://go.microsoft.com/fwlink/?LinkId=196768](http://go.microsoft.com/fwlink/?LinkId=196768)。</span><span class="sxs-lookup"><span data-stu-id="92fb8-162">For more information, refer to the "Modifying the Contents of the Configuration File" section at [http://go.microsoft.com/fwlink/?LinkId=196768](http://go.microsoft.com/fwlink/?LinkId=196768).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92fb8-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92fb8-163">See Also</span></span>  
 [<span data-ttu-id="92fb8-164">管理 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="92fb8-164">Managing BAM Databases</span></span>](../core/managing-bam-databases.md)