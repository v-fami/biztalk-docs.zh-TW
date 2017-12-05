---
title: "如何移動 BAM 主要匯入 Database2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc4f2656-2faa-4503-9551-05e1b6eceb1a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd6abeeb04521e95b32b4d6007dcc7f1f532bdbb
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-move-the-bam-primary-import-database"></a><span data-ttu-id="3548c-102">如何移動 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="3548c-102">How to Move the BAM Primary Import Database</span></span>
<span data-ttu-id="3548c-103">您可以使用這個程序，將 BAM 主要匯入資料庫移動到其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="3548c-103">You can use this procedure to move the BAM Primary Import database to another server.</span></span> <span data-ttu-id="3548c-104">端對端案例的觀點而言，移動 BAM 主要匯入資料庫包含兩個主要步驟：</span><span class="sxs-lookup"><span data-stu-id="3548c-104">From an end-to-end scenario perspective, moving the BAM Primary Import database involves two major steps:</span></span>  
  
-   [<span data-ttu-id="3548c-105">移動 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="3548c-105">Moving the BAM Primary Import Database</span></span>](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_MovingBAMPI)  
  
-   [<span data-ttu-id="3548c-106">更新至新的 BAM 主要匯入資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="3548c-106">Updating References to the New BAM Primary Import Database</span></span>](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef)  
  
## <a name="prerequisites"></a><span data-ttu-id="3548c-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="3548c-107">Prerequisites</span></span>  
 <span data-ttu-id="3548c-108">您必須以成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="3548c-108">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
##  <a name="BKMK_MovingBAMPI"></a><span data-ttu-id="3548c-109">移動 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="3548c-109">Moving the BAM Primary Import Database</span></span>  
 <span data-ttu-id="3548c-110">執行下列程序移動 BAM 主要匯入資料庫中的步驟。</span><span class="sxs-lookup"><span data-stu-id="3548c-110">Perform the steps in the following procedure to move the BAM Primary Import database.</span></span>  
  
#### <a name="to-move-the-bam-primary-import-database"></a><span data-ttu-id="3548c-111">移動 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="3548c-111">To move the BAM Primary Import database</span></span>  
  
1.  <span data-ttu-id="3548c-112">停止任何 BAM cube 更新及資料維護 SSIS 封裝，或防止它們執行，直到您完成 BAM 主要匯入資料庫的還原。</span><span class="sxs-lookup"><span data-stu-id="3548c-112">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Primary Import database.</span></span>  
  
2.  <span data-ttu-id="3548c-113">停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="3548c-113">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="3548c-114">如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](http://go.microsoft.com/fwlink/?LinkId=154394)(http://go.microsoft.com/fwlink/?LinkId=154394) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="3548c-114">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
3.  <span data-ttu-id="3548c-115">停止 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="3548c-115">Stop the IIS service.</span></span>  
  
4.  <span data-ttu-id="3548c-116">停止 BAM 警示 Notification service:</span><span class="sxs-lookup"><span data-stu-id="3548c-116">Stop the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="3548c-117">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3548c-117">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="3548c-118">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="3548c-118">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="3548c-119">**Net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="3548c-119">**Net stop NS$BamAlerts**</span></span>  
  
5.  <span data-ttu-id="3548c-120">備份 BAM 主要匯入在舊伺服器上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="3548c-120">Back up the BAM Primary import database on the old server.</span></span> <span data-ttu-id="3548c-121">如需有關備份資料庫的指示，請遵循的指示如何備份的資料庫時[如何： 備份資料庫 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。</span><span class="sxs-lookup"><span data-stu-id="3548c-121">For instructions on backing up a database, follow the instructions on how to back up a database at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online.</span></span>  
  
6.  <span data-ttu-id="3548c-122">將 BAM 主要匯入資料庫複製到新[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="3548c-122">Copy the BAM Primary Import database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
7.  <span data-ttu-id="3548c-123">還原新的伺服器上的 BAM 主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="3548c-123">Restore the BAM Primary import database on the new server.</span></span> <span data-ttu-id="3548c-124">如需在還原資料庫的指示如何還原的資料庫時遵循[如何： 還原資料庫備份 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。</span><span class="sxs-lookup"><span data-stu-id="3548c-124">For instructions on restoring the database, follow the instructions on how to restore a database at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3548c-125">如果您是從備份還原「BAM 主要匯入」資料庫，那麼您也應該使用比 BAM 主要備份還舊的備份，來還原「BAM 封存」、「BAM 星狀結構描述」及「BAM 分析」資料庫。</span><span class="sxs-lookup"><span data-stu-id="3548c-125">If you restore the BAM Primary Import database from a backup, then you should also restore the BAM Archive, BAM Star Schema, and BAM Analysis databases by using a backup older than the BAM Primary backup.</span></span>  
  
##  <a name="BKMK_BAMPIRef"></a><span data-ttu-id="3548c-126">更新至新的 BAM 主要匯入資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="3548c-126">Updating References to the New BAM Primary Import Database</span></span>  
 <span data-ttu-id="3548c-127">移動資料庫之後，您必須更新至新的 BAM 主要匯入資料庫的所有參考。</span><span class="sxs-lookup"><span data-stu-id="3548c-127">After you have moved the database, you must update all the references to the new BAM Primary Import Database.</span></span> <span data-ttu-id="3548c-128">必須更新下列參考：</span><span class="sxs-lookup"><span data-stu-id="3548c-128">The following references must be updated:</span></span>  
  
-   <span data-ttu-id="3548c-129">新的伺服器名稱與更新所有的 BizTalk 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3548c-129">Update all the BizTalk databases with the new server name.</span></span> <span data-ttu-id="3548c-130">您可以使用 UpdateDatabase.vbs 指令碼。</span><span class="sxs-lookup"><span data-stu-id="3548c-130">You can do so by using the UpdateDatabase.vbs script.</span></span> <span data-ttu-id="3548c-131">請參閱[，BizTalk 資料庫更新以新的伺服器名稱](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDB)。</span><span class="sxs-lookup"><span data-stu-id="3548c-131">See [To update BizTalk Databases with the new server name](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDB).</span></span>  
  
-   <span data-ttu-id="3548c-132">更新 BAM 入口網站的 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="3548c-132">Update the Web.config file for the BAM portal.</span></span> <span data-ttu-id="3548c-133">請參閱[更新 BAM 入口網站的 Web.config 檔案](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_Config)。</span><span class="sxs-lookup"><span data-stu-id="3548c-133">See [To update the Web.config file for the BAM portal](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_Config).</span></span>  
  
-   <span data-ttu-id="3548c-134">更新 BAM 主要匯入資料庫中所有 BAM Livedata Microsoft Excel 檔案的參考。</span><span class="sxs-lookup"><span data-stu-id="3548c-134">Update the reference to the BAM Primary Import Database in all BAM Livedata Microsoft Excel files.</span></span> <span data-ttu-id="3548c-135">請參閱[更新 BAM Livedata Microsoft Excel 檔案中的參考](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateExcel)。</span><span class="sxs-lookup"><span data-stu-id="3548c-135">See [To update reference in BAM Livedata Microsoft Excel files](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateExcel).</span></span>  
  
-   <span data-ttu-id="3548c-136">更新所有 BAM 分析 SSIS 封裝中新的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3548c-136">Update the new server and database names in all BAM analysis SSIS packages.</span></span> <span data-ttu-id="3548c-137">請參閱[更新伺服器和資料庫名稱中的所有 BAM SSIS 封裝](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdatePckg)。</span><span class="sxs-lookup"><span data-stu-id="3548c-137">See [To update server and database names in all BAM SSIS packages](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdatePckg).</span></span>  
  
-   <span data-ttu-id="3548c-138">更新的新伺服器和資料庫名稱在資料來源中所有的 OLAP cube。</span><span class="sxs-lookup"><span data-stu-id="3548c-138">Update the new server and database names in data sources for all OLAP cubes.</span></span> <span data-ttu-id="3548c-139">請參閱[更新伺服器和資料來源中所有的 OLAP cube 的資料庫名稱](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDSOLAP)。</span><span class="sxs-lookup"><span data-stu-id="3548c-139">See [To update server and database names in data sources for all OLAP cubes](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDSOLAP).</span></span>  
  
###  <a name="BKMK_UpdateDB"></a><span data-ttu-id="3548c-140">若要使用新的伺服器名稱更新 BizTalk 資料庫</span><span class="sxs-lookup"><span data-stu-id="3548c-140">To update BizTalk Databases with the new server name</span></span>  
  
1.  <span data-ttu-id="3548c-141">在上執行 BizTalk Server 的電腦，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="3548c-141">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
    -   <span data-ttu-id="3548c-142">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="3548c-142">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="3548c-143">**%Programfiles (x86) %\Microsoft BizTalk Server 2010 \ bins32\schema\restore**</span><span class="sxs-lookup"><span data-stu-id="3548c-143">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\bins32\Schema\Restore**</span></span>  
  
    -   <span data-ttu-id="3548c-144">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="3548c-144">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="3548c-145">**%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**</span><span class="sxs-lookup"><span data-stu-id="3548c-145">**%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**</span></span>  
  
2.  <span data-ttu-id="3548c-146">以滑鼠右鍵按一下**SampleUpdateInfo.xml**，然後按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="3548c-146">Right-click **SampleUpdateInfo.xml**, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="3548c-147">將除了 BizTalkMgmtDb、OldPrimaryImportDatabase、PrimaryImportDatabase、ArchivingDatabase、AnalysisDatabase、StarSchemaDatabase 和 Alert 以外的所有資料庫區段標記為註解。</span><span class="sxs-lookup"><span data-stu-id="3548c-147">Comment out all of the database sections except for the BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert.</span></span>  
  
4.  <span data-ttu-id="3548c-148">在`OldPrimaryImportDatabase`檔案區段的`ServerName`屬性，取代**SourceServer**的現有資料庫所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="3548c-148">In the `OldPrimaryImportDatabase` section of the file, for the `ServerName` property, replace **SourceServer** with the name of existing server where the database resides.</span></span>  
  
5.  <span data-ttu-id="3548c-149">在`PrimaryImportDatabase`檔案區段的`ServerName`屬性，取代**DestinationServer**移動 BAM 主要匯入資料庫的伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="3548c-149">In the `PrimaryImportDatabase` section of the file, for the `ServerName` property, replace **DestinationServer** with the name of the server where you have moved the BAM Primary Import database</span></span>  
  
6.  <span data-ttu-id="3548c-150">BizTalkMgmtDb、 ArchivingDatabase、 AnalysisDatabase、 StarSchemaDatabase 和 Alert 區段，如設定"SourceServer"和"Destination Server"的現有的伺服器名稱這些資料庫所在的位置。</span><span class="sxs-lookup"><span data-stu-id="3548c-150">For the BizTalkMgmtDb, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert sections, set the "SourceServer" and "Destination Server" to the name of the existing server where those databases reside.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3548c-151">在來源及目的系統的名稱兩端加上引號。</span><span class="sxs-lookup"><span data-stu-id="3548c-151">Include the quotation marks around the name of the source and destination systems.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3548c-152">如果您重新命名任何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，您也必須更新為適當的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3548c-152">If you renamed any of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must also update the database names as appropriate.</span></span>  
  
7.  <span data-ttu-id="3548c-153">完成檔案的編輯後，請加以儲存並結束。</span><span class="sxs-lookup"><span data-stu-id="3548c-153">When you are finished editing the file, save it and exit.</span></span>  
  
8.  <span data-ttu-id="3548c-154">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3548c-154">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="3548c-155">在命令提示字元中，瀏覽至下列目錄：</span><span class="sxs-lookup"><span data-stu-id="3548c-155">At the command prompt, navigate to the following directory:</span></span>  
  
    -   <span data-ttu-id="3548c-156">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="3548c-156">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="3548c-157">**%Programfiles (x86) %\Microsoft BizTalk Server 2010\Schema\Restore**</span><span class="sxs-lookup"><span data-stu-id="3548c-157">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Schema\Restore**</span></span>  
  
    -   <span data-ttu-id="3548c-158">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="3548c-158">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="3548c-159">**%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**</span><span class="sxs-lookup"><span data-stu-id="3548c-159">**%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**</span></span>  
  
10. <span data-ttu-id="3548c-160">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="3548c-160">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="3548c-161">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span><span class="sxs-lookup"><span data-stu-id="3548c-161">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span></span>  
  
###  <a name="BKMK_Config"></a><span data-ttu-id="3548c-162">若要更新 BAM 入口網站的 Web.config 檔案</span><span class="sxs-lookup"><span data-stu-id="3548c-162">To update the Web.config file for the BAM portal</span></span>  
  
1.  <span data-ttu-id="3548c-163">在電腦上執行 BizTalk Server，更新 Web.config 檔案在**\<磁碟機\>: \Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMManagementService\Web.Config**。更新 Web.config 中的下列章節中的伺服器和資料庫名稱：</span><span class="sxs-lookup"><span data-stu-id="3548c-163">On a computer running BizTalk Server, update the Web.config files under **\<drive\>:\Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMManagementService\Web.Config**. Update the server and database names in the following section in the Web.config:</span></span>  
  
    ```  
    <appSettings>  
      <add key="BamServer" value="<ServerName>" />  
      <add key="BamDatabase" value="<DatabaseName>" />  
    </appSettings>  
    ```  
  
2.  <span data-ttu-id="3548c-164">在電腦上執行 BizTalk Server，更新 Web.config 檔案在**\<磁碟機\>: \Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMQueryService\Web.Config**。更新 Web.config 中的下列章節中的伺服器和資料庫名稱：</span><span class="sxs-lookup"><span data-stu-id="3548c-164">On a computer running BizTalk Server, update the Web.config files under **\<drive\>:\Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMQueryService\Web.Config**. Update the server and database names in the following section in the Web.config:</span></span>  
  
    ```  
    <appSettings>  
      <add key="BamServer" value="<ServerName>" />  
      <add key="BamDatabase" value="<DatabaseName>" />  
      <add key="MaxResultRows" value="2000" />  
    </appSettings>  
    ```  
  
3.  <span data-ttu-id="3548c-165">儲存並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="3548c-165">Save and close the files.</span></span>  
  
###  <a name="BKMK_UpdateExcel"></a><span data-ttu-id="3548c-166">若要更新 BAM Livedata Microsoft Excel 檔案中的參考</span><span class="sxs-lookup"><span data-stu-id="3548c-166">To update reference in BAM Livedata Microsoft Excel files</span></span>  
  
1.  <span data-ttu-id="3548c-167">開啟 Excel 即時資料檔案。</span><span class="sxs-lookup"><span data-stu-id="3548c-167">Open the Excel live data file.</span></span> <span data-ttu-id="3548c-168">此檔案名稱是以 _LiveData.xls 結尾。</span><span class="sxs-lookup"><span data-stu-id="3548c-168">The file name ends with _LiveData.xls.</span></span>  
  
2.  <span data-ttu-id="3548c-169">在**BAM**功能表上，按一下  **BAM DB 連線**。</span><span class="sxs-lookup"><span data-stu-id="3548c-169">On the **BAM** menu, click **BAM DB Connection**.</span></span>  
  
3.  <span data-ttu-id="3548c-170">在**選取 BAM 資料庫**對話方塊方塊中，輸入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦和 BAMPrimaryImport 資料庫，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3548c-170">In the **Select BAM Database** dialog box, enter the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer and the BAMPrimaryImport database, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="3548c-171">在**檔案**功能表上，按一下 **關閉並返回 Microsoft Excel**。</span><span class="sxs-lookup"><span data-stu-id="3548c-171">On the **File** menu, click **Close and Return to Microsoft Excel**.</span></span>  
  
5.  <span data-ttu-id="3548c-172">在 [檔案] 功能表上，按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="3548c-172">On the **File** menu, click **Save**.</span></span>  
  
###  <a name="BKMK_UpdatePckg"></a><span data-ttu-id="3548c-173">若要更新的伺服器和所有 BAM SSIS 封裝中的資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="3548c-173">To update server and database names in all BAM SSIS packages</span></span>  
  
1.  <span data-ttu-id="3548c-174">更新所有 BAM 分析 SSIS 封裝，它會加上"BAM_AN_"或"BAM_DM_"中的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3548c-174">Update the server and database names in all BAM analysis SSIS packages, which are prefixed with "BAM_AN_" or "BAM_DM_".</span></span> <span data-ttu-id="3548c-175">若要這樣做，請按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下**SQL Server Business Intelligence Development Studio**。</span><span class="sxs-lookup"><span data-stu-id="3548c-175">To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Business Intelligence Development Studio**.</span></span>  
  
2.  <span data-ttu-id="3548c-176">在 SQL Server Business Intelligence Development Studio 中建立新專案。</span><span class="sxs-lookup"><span data-stu-id="3548c-176">In SQL Server Business Intelligence Development Studio, create a new project.</span></span> <span data-ttu-id="3548c-177">按一下**檔案**，按一下 **新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="3548c-177">Click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="3548c-178">在**新專案**對話方塊中，於**專案類型**方塊中，按一下**商業智慧專案**。</span><span class="sxs-lookup"><span data-stu-id="3548c-178">In the **New Project** dialog box, in the **Project Types** box, click **Business Intelligence Projects**.</span></span> <span data-ttu-id="3548c-179">在右窗格中，在**範本**方塊中，按一下**Integration Services 專案**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="3548c-179">In the right pane, in the **Templates** box, click **Integration Services Project**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="3548c-180">在**Integration Services 專案**對話方塊中的，在 方案總管 中，以滑鼠右鍵按一下**SSIS 封裝**，然後按一下 **加入現有封裝**。</span><span class="sxs-lookup"><span data-stu-id="3548c-180">In the **Integration Services Project** dialog box, in Solution Explorer, right-click **SSIS Packages**, and then click **Add Existing Package**.</span></span>  
  
5.  <span data-ttu-id="3548c-181">在**加入現有封裝的副本**對話方塊中，於**伺服器**下拉式清單方塊中，選取包含 BAM_AN_ * 和 BAM_DM_ * 封裝的伺服器。</span><span class="sxs-lookup"><span data-stu-id="3548c-181">In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_AN_* and BAM_DM_* packages.</span></span>  
  
6.  <span data-ttu-id="3548c-182">在**封裝路徑**，按一下省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="3548c-182">In **Package Path**, click the ellipses button.</span></span>  
  
7.  <span data-ttu-id="3548c-183">在**SSIS 封裝**對話方塊方塊中，選取您想要更新，請按一下的封裝**確定**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="3548c-183">In the **SSIS Package** dialog box, select the package you want to update, click **OK**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3548c-184">封裝現在會在 [方案總管] 中列出。</span><span class="sxs-lookup"><span data-stu-id="3548c-184">The package is now listed in Solution Explorer.</span></span>  
  
8.  <span data-ttu-id="3548c-185">在 [方案總管] 中，按兩下的封裝您在上一個步驟中加入。</span><span class="sxs-lookup"><span data-stu-id="3548c-185">In Solution Explorer, double-click the package you added in the previous step.</span></span> <span data-ttu-id="3548c-186">在**連接管理員**索引標籤上 （朝向螢幕的下半部提供），請按兩下資料來源數字 1 （BAMPrimaryImport 資料庫）。</span><span class="sxs-lookup"><span data-stu-id="3548c-186">In **Connection Managers** tab (available towards the lower half of the screen), double-click data source number 1 (BAMPrimaryImport database).</span></span>  
  
9. <span data-ttu-id="3548c-187">在**連線管理員**對話方塊中，於**伺服器名稱**方塊中，輸入伺服器的名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3548c-187">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="3548c-188">按一下**封裝總管**索引標籤上，按兩下**變數**資料夾，然後更新的值**PrimaryImportDatabase**和**PrimaryImportServer**變數。</span><span class="sxs-lookup"><span data-stu-id="3548c-188">Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the **PrimaryImportDatabase** and **PrimaryImportServer** variables.</span></span> <span data-ttu-id="3548c-189">您必須更新為指向新的伺服器與資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="3548c-189">You must update the values to point to the new server and database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3548c-190">針對您想要更新的所有封裝重複步驟 4 到 10。</span><span class="sxs-lookup"><span data-stu-id="3548c-190">Repeat step 4 through 10 for all the packages that you want to update.</span></span>  
  
11. <span data-ttu-id="3548c-191">然後按一下**檔案**功能表，然後再按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="3548c-191">Click then **File** menu, and then click **Save All**.</span></span>  
  
12. <span data-ttu-id="3548c-192">啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="3548c-192">Start the SQL Server Management Studio.</span></span> <span data-ttu-id="3548c-193">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="3548c-193">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.</span></span>  
  
13. <span data-ttu-id="3548c-194">在**連接到伺服器**對話方塊中，從**伺服器**類型下拉式清單中，選取**Integration Services**。</span><span class="sxs-lookup"><span data-stu-id="3548c-194">In the **Connect to Server** dialog box, from the **Server** type drop-down list, select **Integration Services**.</span></span>  
  
14. <span data-ttu-id="3548c-195">指定伺服器名稱和認證以連接至伺服器，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3548c-195">Specify the server name and credentials to connect to the server and click **OK**.</span></span>  
  
15. <span data-ttu-id="3548c-196">在**物件總管] 中**，依序展開**Integration Services**，依序展開**存放的封裝**，然後按一下 [ **MSDB**。</span><span class="sxs-lookup"><span data-stu-id="3548c-196">In the **Object Explorer**, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.</span></span>  
  
16. <span data-ttu-id="3548c-197">在**物件總管詳細資料**索引標籤上，以滑鼠右鍵按一下您稍早更新的封裝，然後按一下**匯入封裝**。</span><span class="sxs-lookup"><span data-stu-id="3548c-197">In the **Object Explorer Details** tab, right-click the package that you updated earlier and then click **Import Package**.</span></span>  
  
17. <span data-ttu-id="3548c-198">在**匯入封裝**對話方塊中，從**封裝位置**下拉式清單中，選取**檔案系統**。</span><span class="sxs-lookup"><span data-stu-id="3548c-198">In the **Import Package** dialog box, from the **Package location** drop-down list, select **File System**.</span></span>  
  
18. <span data-ttu-id="3548c-199">在**封裝路徑**、 瀏覽至您儲存的專案中，選取您想要匯入，然後按一下 封裝.dtsx 檔案**開啟**。</span><span class="sxs-lookup"><span data-stu-id="3548c-199">In **Package Path**, navigate to your saved project, select the .dtsx file for the package you want to import, and then click **Open**.</span></span>  
  
19. <span data-ttu-id="3548c-200">按一下 [封裝名稱] 方塊，以自動填入方塊內部。</span><span class="sxs-lookup"><span data-stu-id="3548c-200">Click inside the Package Name box to automatically populate the box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3548c-201">您想要更新的所有封裝重複步驟 19 透過 16。</span><span class="sxs-lookup"><span data-stu-id="3548c-201">Repeat step 16 through 19 for all the packages that you want to update.</span></span>  
  
20. <span data-ttu-id="3548c-202">按一下**確定**，然後按一下 **是**覆寫。</span><span class="sxs-lookup"><span data-stu-id="3548c-202">Click **OK**, and then click **Yes** to overwrite.</span></span>  
  
21. <span data-ttu-id="3548c-203">啟用任何 BAM Cube 更新和資料維護 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="3548c-203">Enable any BAM cube update and data maintenance SSIS packages.</span></span>  
  
###  <a name="BKMK_UpdateDSOLAP"></a><span data-ttu-id="3548c-204">更新伺服器和資料來源中所有的 OLAP cube 的資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="3548c-204">To update server and database names in data sources for all OLAP cubes</span></span>  
  
1.  <span data-ttu-id="3548c-205">更新的伺服器和資料庫名稱在資料來源中所有的 OLAP cube。</span><span class="sxs-lookup"><span data-stu-id="3548c-205">Update the server and database names in data sources for all OLAP cubes.</span></span> <span data-ttu-id="3548c-206">若要這樣做，請按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="3548c-206">To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="3548c-207">在**連接到伺服器**對話方塊中，針對**伺服器類型**下拉式清單中，選取**Analysis Services**、 提供伺服器名稱、 選取驗證方法 （和提供的認證有必要），然後按一下 **連接**。</span><span class="sxs-lookup"><span data-stu-id="3548c-207">In the **Connect to Server** dialog box, for the **Server type** drop-down list select **Analysis Services**, provide the server name, select an authentication method (and provide credentials if required), and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="3548c-208">在 [物件總管] 中，依序展開**資料庫**，依序展開**BAMAnalysis**，依序展開**資料來源**，然後按兩下資料來源。</span><span class="sxs-lookup"><span data-stu-id="3548c-208">In the Object Explorer, expand **Databases**, expand **BAMAnalysis**, expand **Data Sources**, and then double-click a data source.</span></span>  
  
4.  <span data-ttu-id="3548c-209">在**資料來源屬性**對話方塊方塊中，按一下省略符號按鈕**（...）**針對**連接字串**屬性。</span><span class="sxs-lookup"><span data-stu-id="3548c-209">In the **Data Source Properties** dialog box, click the ellipsis button **(…)** against the **Connection String** property.</span></span>  
  
5.  <span data-ttu-id="3548c-210">中**連接管理員**對話方塊中，於**伺服器名稱**方塊中，輸入裝載 BAMPrimaryImport 資料庫的伺服器名稱，按一下**確定**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="3548c-210">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server hosting the BAMPrimaryImport database, click **OK**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="3548c-211">啟動所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="3548c-211">Start all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="3548c-212">如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](http://go.microsoft.com/fwlink/?LinkId=154394)(http://go.microsoft.com/fwlink/?LinkId=154394) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="3548c-212">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
7.  <span data-ttu-id="3548c-213">啟動 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="3548c-213">Start the IIS service.</span></span>  
  
8.  <span data-ttu-id="3548c-214">啟動 BAM 警示 Notification service:</span><span class="sxs-lookup"><span data-stu-id="3548c-214">Start the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="3548c-215">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3548c-215">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="3548c-216">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="3548c-216">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="3548c-217">**Net start NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="3548c-217">**Net start NS$BamAlerts**</span></span>  
  
9. <span data-ttu-id="3548c-218">解決任何不完整的追蹤執行個體。</span><span class="sxs-lookup"><span data-stu-id="3548c-218">Resolve any incomplete trace instances.</span></span>  <span data-ttu-id="3548c-219">如需解決未完成的 BAM 活動執行個體的相關資訊，請參閱[如何解析未完成的活動執行個體](http://go.microsoft.com/fwlink/?LinkId=151475)(http://go.microsoft.com/fwlink/?LinkId=151475)。</span><span class="sxs-lookup"><span data-stu-id="3548c-219">For information about resolving incomplete BAM activity instances, see [How to Resolve Incomplete Activity Instances](http://go.microsoft.com/fwlink/?LinkId=151475) (http://go.microsoft.com/fwlink/?LinkId=151475).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3548c-220">請參閱</span><span class="sxs-lookup"><span data-stu-id="3548c-220">See Also</span></span>  
 [<span data-ttu-id="3548c-221">移動資料庫</span><span class="sxs-lookup"><span data-stu-id="3548c-221">Moving Databases</span></span>](../technical-guides/moving-databases.md)