---
title: "如何移動 BAM 封存 Database1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e371321c-6b8d-4be6-a6d2-926f6218db01
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 383aef74519f7527383d9f681f83ace2e515eba7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-move-the-bam-archive-database"></a><span data-ttu-id="c1126-102">如何移動 BAM 封存資料庫</span><span class="sxs-lookup"><span data-stu-id="c1126-102">How to Move the BAM Archive Database</span></span>
<span data-ttu-id="c1126-103">您可以使用這個程序，將 BAM 封存資料庫移動到其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="c1126-103">You can use this procedure to move the BAM Archive database to another server.</span></span>  <span data-ttu-id="c1126-104">端對端案例的觀點而言，移動 BAM 封存資料庫包含兩個主要步驟：</span><span class="sxs-lookup"><span data-stu-id="c1126-104">From an end-to-end scenario perspective, moving the BAM Archive database involves two major steps:</span></span>  
  
-   [<span data-ttu-id="c1126-105">移動 BAM 封存資料庫</span><span class="sxs-lookup"><span data-stu-id="c1126-105">Moving the BAM Archive Database</span></span>](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_MovingArch)  
  
-   [<span data-ttu-id="c1126-106">更新至新的 BAM 封存資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="c1126-106">Updating References to the New BAM Archive Database</span></span>](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArch)  
  
## <a name="prerequisites"></a><span data-ttu-id="c1126-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="c1126-107">Prerequisites</span></span>  
 <span data-ttu-id="c1126-108">您必須以成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="c1126-108">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
##  <a name="BKMK_MovingArch"></a><span data-ttu-id="c1126-109">移動 BAM 封存資料庫</span><span class="sxs-lookup"><span data-stu-id="c1126-109">Moving the BAM Archive Database</span></span>  
 <span data-ttu-id="c1126-110">執行下列程序移動 BAM 封存資料庫中的步驟。</span><span class="sxs-lookup"><span data-stu-id="c1126-110">Perform the steps in the following procedure to move the BAM Archive database.</span></span>  
  
#### <a name="to-move-the-bam-archive-database"></a><span data-ttu-id="c1126-111">移動 BAM 封存資料庫</span><span class="sxs-lookup"><span data-stu-id="c1126-111">To move the BAM Archive database</span></span>  
  
1.  <span data-ttu-id="c1126-112">停止任何 BAM cube 更新及資料維護 SSIS 封裝，或防止它們執行，直到您還原 BAM 封存資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1126-112">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Archive database.</span></span>  
  
2.  <span data-ttu-id="c1126-113">停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="c1126-113">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="c1126-114">如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](http://go.microsoft.com/fwlink/?LinkId=154394)(http://go.microsoft.com/fwlink/?LinkId=154394) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="c1126-114">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
3.  <span data-ttu-id="c1126-115">停止 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="c1126-115">Stop the IIS service.</span></span>  
  
4.  <span data-ttu-id="c1126-116">停止 BAM 警示 Notification service:</span><span class="sxs-lookup"><span data-stu-id="c1126-116">Stop the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="c1126-117">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c1126-117">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="c1126-118">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="c1126-118">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="c1126-119">**Net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="c1126-119">**Net stop NS$BamAlerts**</span></span>  
  
5.  <span data-ttu-id="c1126-120">在舊伺服器上備份 BAM 封存資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1126-120">Back up the BAM Archive database on the old server.</span></span> <span data-ttu-id="c1126-121">如需有關備份資料庫的指示，請遵循指示[如何： 備份資料庫 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何備份資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1126-121">For instructions on backing up a database, follow the instructions at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to back up a database.</span></span>  
  
6.  <span data-ttu-id="c1126-122">將 BAM 封存資料庫複製到新[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="c1126-122">Copy the BAM Archive database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
7.  <span data-ttu-id="c1126-123">還原 BAM 封存資料庫，新的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="c1126-123">Restore the BAM Archive database on the new server.</span></span> <span data-ttu-id="c1126-124">如需在還原資料庫的指示，請遵循的指示[如何： 還原資料庫備份 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1126-124">For instructions on restoring the database, follow the instructions at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to restore a database.</span></span>  
  
##  <a name="BKMK_UpdateArch"></a><span data-ttu-id="c1126-125">更新至新的 BAM 封存資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="c1126-125">Updating References to the New BAM Archive Database</span></span>  
 <span data-ttu-id="c1126-126">移動資料庫之後，您必須更新至新的 BAM 封存資料庫的所有參考。</span><span class="sxs-lookup"><span data-stu-id="c1126-126">After you have moved the database, you must update all the references to the new BAM Archive Database.</span></span> <span data-ttu-id="c1126-127">必須更新下列參考：</span><span class="sxs-lookup"><span data-stu-id="c1126-127">The following references must be updated:</span></span>  
  
-   <span data-ttu-id="c1126-128">以新的資料庫和伺服器名稱更新 BAM 組態。</span><span class="sxs-lookup"><span data-stu-id="c1126-128">Update the BAM configuration with the new database and server names.</span></span> <span data-ttu-id="c1126-129">請參閱[更新 BAM 組態](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArchConfig)。</span><span class="sxs-lookup"><span data-stu-id="c1126-129">See [To update the BAM configuration](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArchConfig).</span></span>  
  
-   <span data-ttu-id="c1126-130">更新所有 BAM 分析 SSIS 封裝中新的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="c1126-130">Update the new server and database names in all BAM analysis SSIS packages.</span></span> <span data-ttu-id="c1126-131">請參閱[更新伺服器和資料庫名稱中的所有 BAM SSIS 封裝](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArchSSIS)。</span><span class="sxs-lookup"><span data-stu-id="c1126-131">See [To update server and database names in all BAM SSIS packages](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArchSSIS).</span></span>  
  
###  <a name="BKMK_UpdateArchConfig"></a><span data-ttu-id="c1126-132">若要更新 BAM 組態</span><span class="sxs-lookup"><span data-stu-id="c1126-132">To update the BAM configuration</span></span>  
  
1.  <span data-ttu-id="c1126-133">取得用來還原 BAM 的 .xml 檔案複本：</span><span class="sxs-lookup"><span data-stu-id="c1126-133">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="c1126-134">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c1126-134">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="c1126-135">在上執行 BizTalk Server 的電腦，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="c1126-135">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
        -   <span data-ttu-id="c1126-136">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="c1126-136">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="c1126-137">**%Programfiles (x86) %\Microsoft BizTalk Server 2010 \tracking**</span><span class="sxs-lookup"><span data-stu-id="c1126-137">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
        -   <span data-ttu-id="c1126-138">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="c1126-138">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="c1126-139">**%ProgramFiles%\Microsoft BizTalk Server 2010 \tracking**</span><span class="sxs-lookup"><span data-stu-id="c1126-139">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    3.  <span data-ttu-id="c1126-140">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="c1126-140">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="c1126-141">**Bm.exe get-config –filename:BAMConfiguration.xml-server:\<servername\> -資料庫：\<資料庫\>**</span><span class="sxs-lookup"><span data-stu-id="c1126-141">**Bm.exe get-config –filename:BAMConfiguration.xml -server:\<servername\> -database:\<database\>**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c1126-142">當執行此命令，以取代要取得組態資訊的來源伺服器的實際名稱\<servername\> ，並以要從中取得組態資訊的資料庫的實際名稱取代\<資料庫\>。</span><span class="sxs-lookup"><span data-stu-id="c1126-142">When running this command, substitute the actual name of the server from which to get the configuration information for \<servername\> and substitute the actual name of the database from which to get the configuration information for \<database\>.</span></span> <span data-ttu-id="c1126-143">如需有關如何使用 BAM 管理 (BM) 公用程式的詳細資訊，請參閱[基礎結構管理命令](http://go.microsoft.com/fwlink/?LinkId=156516)(http://go.microsoft.com/fwlink/?LinkId=156516) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="c1126-143">For more information about using the BAM Management (BM) utility, see [Infrastructure Management Commands](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
2.  <span data-ttu-id="c1126-144">編輯 BAMConfiguration.xml 檔案，並變更**ServerName**中`<DeploymentUnit Name="ArchivingDatabase">`區段，以新的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="c1126-144">Edit the BAMConfiguration.xml file and change the **ServerName** in the `<DeploymentUnit Name="ArchivingDatabase">` section to the new server name.</span></span>  
  
3.  <span data-ttu-id="c1126-145">儲存並關閉 BAMConfiguration.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="c1126-145">Save and close the BAMConfiguration.xml file.</span></span>  
  
4.  <span data-ttu-id="c1126-146">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c1126-146">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c1126-147">在上執行 BizTalk Server 的電腦，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="c1126-147">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
    -   <span data-ttu-id="c1126-148">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="c1126-148">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="c1126-149">**%Programfiles (x86) %\Microsoft BizTalk Server 2010 \tracking**</span><span class="sxs-lookup"><span data-stu-id="c1126-149">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    -   <span data-ttu-id="c1126-150">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="c1126-150">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="c1126-151">**%ProgramFiles%\Microsoft BizTalk Server 2010 \tracking**</span><span class="sxs-lookup"><span data-stu-id="c1126-151">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
6.  <span data-ttu-id="c1126-152">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="c1126-152">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="c1126-153">**bm.exe 更新-config-FileName:BAMConfiguration.xml**</span><span class="sxs-lookup"><span data-stu-id="c1126-153">**bm.exe update-config -FileName:BAMConfiguration.xml**</span></span>  
  
###  <a name="BKMK_UpdateArchSSIS"></a><span data-ttu-id="c1126-154">若要更新的伺服器和所有 BAM SSIS 封裝中的資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="c1126-154">To update server and database names in all BAM SSIS packages</span></span>  
  
1.  <span data-ttu-id="c1126-155">更新所有 BAM 分析 SSIS 封裝，以"bam_dm_"作為前置詞中的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="c1126-155">Update the server and database names in all BAM analysis SSIS packages, which are prefixed with "BAM_DM_".</span></span> <span data-ttu-id="c1126-156">若要這樣做，請按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下**SQL Server Business Intelligence Development Studio**。</span><span class="sxs-lookup"><span data-stu-id="c1126-156">To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Business Intelligence Development Studio**.</span></span>  
  
2.  <span data-ttu-id="c1126-157">在 SQL Server Business Intelligence Development Studio 中建立新專案。</span><span class="sxs-lookup"><span data-stu-id="c1126-157">In SQL Server Business Intelligence Development Studio, create a new project.</span></span> <span data-ttu-id="c1126-158">按一下**檔案**，按一下 **新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="c1126-158">Click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="c1126-159">在**新專案**對話方塊中，於**專案類型**方塊中，按一下**商業智慧專案**。</span><span class="sxs-lookup"><span data-stu-id="c1126-159">In the **New Project** dialog box, in the **Project Types** box, click **Business Intelligence Projects**.</span></span> <span data-ttu-id="c1126-160">在右窗格中，在**範本**方塊中，按一下**Integration Services 專案**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c1126-160">On the right pane, in the **Templates** box, click **Integration Services Project**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="c1126-161">在**Integration Services 專案**對話方塊中的，在 方案總管 中，以滑鼠右鍵按一下**SSIS 封裝**，然後按一下 **加入現有封裝**。</span><span class="sxs-lookup"><span data-stu-id="c1126-161">In the **Integration Services Project** dialog box, in Solution Explorer, right-click **SSIS Packages**, and then click **Add Existing Package**.</span></span>  
  
5.  <span data-ttu-id="c1126-162">在**加入現有封裝的副本**對話方塊中，於**伺服器**下拉式清單方塊中，選取包含 BAM_DM_ * 封裝的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c1126-162">In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_DM_* packages.</span></span>  
  
6.  <span data-ttu-id="c1126-163">在**封裝路徑**，按一下省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="c1126-163">In **Package Path**, click the ellipses button.</span></span>  
  
7.  <span data-ttu-id="c1126-164">在**SSIS 封裝**對話方塊方塊中，選取您想要更新，請按一下的封裝**確定**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="c1126-164">In the **SSIS Package** dialog box, select the package you want to update, click **OK**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c1126-165">封裝現在會在 [方案總管] 中列出。</span><span class="sxs-lookup"><span data-stu-id="c1126-165">The package is now listed in Solution Explorer.</span></span>  
  
8.  <span data-ttu-id="c1126-166">在 [方案總管] 中，按兩下的封裝您在上一個步驟中加入。</span><span class="sxs-lookup"><span data-stu-id="c1126-166">In Solution Explorer, double-click the package you added in the previous step.</span></span> <span data-ttu-id="c1126-167">在**連接管理員**索引標籤上 （朝向螢幕的下半部提供），請按兩下資料來源數字 2 （BAMArchive 資料庫）。</span><span class="sxs-lookup"><span data-stu-id="c1126-167">In **Connection Managers** tab (available towards the lower half of the screen), double-click data source number 2 (BAMArchive database).</span></span>  
  
9. <span data-ttu-id="c1126-168">在**連線管理員**對話方塊中，於**伺服器名稱**方塊中，輸入伺服器的名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c1126-168">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1126-169">重複此步驟的資料來源數字 3 （MSDB 資料庫）。</span><span class="sxs-lookup"><span data-stu-id="c1126-169">Repeat this for data source number 3 (MSDB database).</span></span>  
  
10. <span data-ttu-id="c1126-170">按一下**封裝總管**索引標籤上，按兩下**變數**資料夾，然後更新的值**ArchivingDatabase**， **ArchivingServer**， **PrimaryImportDatabase**，和**PrimaryImportServer**變數。</span><span class="sxs-lookup"><span data-stu-id="c1126-170">Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the **ArchivingDatabase**, **ArchivingServer**, **PrimaryImportDatabase**, and **PrimaryImportServer** variables.</span></span> <span data-ttu-id="c1126-171">您必須更新為指向新的伺服器與資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="c1126-171">You must update the values to point to the new server and database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1126-172">針對您想要更新的所有封裝重複步驟 4 到 10。</span><span class="sxs-lookup"><span data-stu-id="c1126-172">Repeat step 4 through 10 for all the packages that you want to update.</span></span>  
  
11. <span data-ttu-id="c1126-173">然後按一下**檔案**功能表，然後再按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="c1126-173">Click then **File** menu, and then click **Save All**.</span></span>  
  
12. <span data-ttu-id="c1126-174">啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="c1126-174">Start the SQL Server Management Studio.</span></span> <span data-ttu-id="c1126-175">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="c1126-175">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.</span></span>  
  
13. <span data-ttu-id="c1126-176">在**連接到伺服器**對話方塊中，從**伺服器**類型下拉式清單中，選取**Integration Services**。</span><span class="sxs-lookup"><span data-stu-id="c1126-176">In the **Connect to Server** dialog box, from the **Server** type drop-down list, select **Integration Services**.</span></span>  
  
14. <span data-ttu-id="c1126-177">指定伺服器名稱和認證以連接至伺服器，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c1126-177">Specify the server name and credentials to connect to the server and click **OK**.</span></span>  
  
15. <span data-ttu-id="c1126-178">在**物件總管] 中**，依序展開**Integration Services**，依序展開**存放的封裝**，然後按一下 [ **MSDB**。</span><span class="sxs-lookup"><span data-stu-id="c1126-178">In the **Object Explorer**, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.</span></span>  
  
16. <span data-ttu-id="c1126-179">在**物件總管詳細資料**索引標籤上，以滑鼠右鍵按一下您稍早更新的封裝，然後按一下**匯入封裝**。</span><span class="sxs-lookup"><span data-stu-id="c1126-179">In the **Object Explorer Details** tab, right-click the package that you updated earlier and then click **Import Package**.</span></span>  
  
17. <span data-ttu-id="c1126-180">在**匯入封裝**對話方塊中，從**封裝位置**下拉式清單中，選取**檔案系統**。</span><span class="sxs-lookup"><span data-stu-id="c1126-180">In the **Import Package** dialog box, from the **Package location** drop-down list, select **File System**.</span></span>  
  
18. <span data-ttu-id="c1126-181">在**封裝路徑**、 瀏覽至您儲存的專案中，選取您想要匯入，然後按一下 封裝.dtsx 檔案**開啟**。</span><span class="sxs-lookup"><span data-stu-id="c1126-181">In **Package Path**, navigate to your saved project, select the .dtsx file for the package you want to import, and then click **Open**.</span></span>  
  
19. <span data-ttu-id="c1126-182">按一下 [封裝名稱] 方塊，以自動填入方塊內部。</span><span class="sxs-lookup"><span data-stu-id="c1126-182">Click inside the Package Name box to automatically populate the box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1126-183">您想要更新的所有封裝重複步驟 19 透過 16。</span><span class="sxs-lookup"><span data-stu-id="c1126-183">Repeat step 16 through 19 for all the packages that you want to update.</span></span>  
  
20. <span data-ttu-id="c1126-184">按一下**確定**，然後按一下 **是**覆寫。</span><span class="sxs-lookup"><span data-stu-id="c1126-184">Click **OK**, and then click **Yes** to overwrite.</span></span>  
  
21. <span data-ttu-id="c1126-185">啟動所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="c1126-185">Start all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="c1126-186">如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](http://go.microsoft.com/fwlink/?LinkId=154394)(http://go.microsoft.com/fwlink/?LinkId=154394) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="c1126-186">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
22. <span data-ttu-id="c1126-187">啟動 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="c1126-187">Start the IIS service.</span></span>  
  
23. <span data-ttu-id="c1126-188">啟動 BAM 警示 Notification service:</span><span class="sxs-lookup"><span data-stu-id="c1126-188">Start the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="c1126-189">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c1126-189">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="c1126-190">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="c1126-190">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="c1126-191">**Net start NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="c1126-191">**Net start NS$BamAlerts**</span></span>  
  
24. <span data-ttu-id="c1126-192">啟用任何 BAM Cube 更新和資料維護 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="c1126-192">Enable any BAM cube update and data maintenance SSIS packages.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="c1126-193">最好的作法是，您也應該主控 BAMArchive 資料庫的伺服器，移動 BAM_DM_ * SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="c1126-193">As a good practice, you should also move the BAM_DM_* SSIS packages to the server hosting the BAMArchive database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1126-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="c1126-194">See Also</span></span>  
 [<span data-ttu-id="c1126-195">移動資料庫</span><span class="sxs-lookup"><span data-stu-id="c1126-195">Moving Databases</span></span>](../technical-guides/moving-databases.md)