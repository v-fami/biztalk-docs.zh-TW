---
title: "如何更新 BAM 主要匯入資料庫名稱和連接字串參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restoring [BAM], connection strings
- Primary Import database [BAM], updating references
- connection strings, restoring
- connection strings, BAM
- restoring, BAM
- restoring [BAM], Primary Import database
- restoring [BAM], updating references
- Primary Import database [BAM], restoring
- BAM, restoring
- restoring, connection strings
ms.assetid: e3c58db0-f14f-429a-813c-bae29f6950d3
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b56264155ed9f739669da1cb6f646adac0f9db55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-references-to-the-bam-primary-import-database-name-and-connection-string"></a><span data-ttu-id="09c3f-102">如何更新 BAM 主要匯入資料庫名稱和連接字串的參考</span><span class="sxs-lookup"><span data-stu-id="09c3f-102">How to Update References to the BAM Primary Import Database Name and Connection String</span></span>
<span data-ttu-id="09c3f-103">如果您已備份 BAMPrimaryImport 資料庫發生系統或資料失敗時，可以將該備份還原至不同的電腦，並重新命名此備份。</span><span class="sxs-lookup"><span data-stu-id="09c3f-103">If you backed up your BAMPrimaryImport database in the event of a system or data failure, you can restore that backup to a different computer and rename the backup.</span></span>  
  
 <span data-ttu-id="09c3f-104">BAM 事件匯流排服務會將事件資料從 MessageBox 資料庫移到 BAMPrimaryImport 資料庫。</span><span class="sxs-lookup"><span data-stu-id="09c3f-104">The BAM Event Bus service moves event data from the MessageBox database to the BAMPrimaryImport database.</span></span> <span data-ttu-id="09c3f-105">BAM 事件匯流排服務包含容錯邏輯，可讓它從意外的失敗中復原和重新啟動，而不會遺失任何資料。</span><span class="sxs-lookup"><span data-stu-id="09c3f-105">The BAM Event Bus service includes fault tolerance logic that enables it to recover and restart from an unexpected failure without losing any data.</span></span> <span data-ttu-id="09c3f-106">如需有關 BAM 事件匯流排服務的詳細資訊，請參閱[管理 BAM 事件匯流排服務](../core/managing-the-bam-event-bus-service.md)。</span><span class="sxs-lookup"><span data-stu-id="09c3f-106">For more information about the BAM Event Bus service, see [Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md).</span></span>  
  
 <span data-ttu-id="09c3f-107">若要還原 BAMPrimaryImport 資料庫，執行中的步驟[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="09c3f-107">To restore the BAMPrimaryImport database, perform the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span> <span data-ttu-id="09c3f-108">此外，您也必須執行下列一般步驟，各步驟之後都有詳細說明步驟的程序：</span><span class="sxs-lookup"><span data-stu-id="09c3f-108">In addition, you must perform these general steps, which are followed by a procedure that describes the steps in detail:</span></span>  
  
-   <span data-ttu-id="09c3f-109">更新所有 BAM DTS 封裝中的「SQL 連線 1」，以參考新的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="09c3f-109">Update the SQL Connection 1 in all BAM DTS packages to refer to the new database name.</span></span>  
  
-   <span data-ttu-id="09c3f-110">以新的資料庫名稱更新 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="09c3f-110">Update the web.config file with the new database name.</span></span>  
  
-   <span data-ttu-id="09c3f-111">在所有 BAM Livedata Microsoft Excel 檔案中更新 BAMPrimaryImport 資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="09c3f-111">Update the reference to BAMPrimaryImport database in all BAM Livedata Microsoft Excel files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="09c3f-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="09c3f-112">Prerequisites</span></span>  
 <span data-ttu-id="09c3f-113">您必須以 BizTalk Server 系統管理員群組的成員身分登入，才能執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="09c3f-113">You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.</span></span>  
  
### <a name="to-update-references-to-the-bamprimaryimport-database-name-and-connection-string"></a><span data-ttu-id="09c3f-114">若要更新 BAMPrimaryImport 資料庫的名稱和連接字串的參考</span><span class="sxs-lookup"><span data-stu-id="09c3f-114">To update references to the BAMPrimaryImport database name and connection string</span></span>  
  
1.  <span data-ttu-id="09c3f-115">停止任何 BAM cube 更新及資料維護 Data Transformation Services (DTS) 封裝，或防止它們執行，直到您完成 BAMPrimaryImport 資料庫的還原。</span><span class="sxs-lookup"><span data-stu-id="09c3f-115">Stop any BAM cube update and data maintenance Data Transformation Services (DTS) packages, or prevent them from running until you have restored the BAMPrimaryImport database.</span></span>  
  
2.  <span data-ttu-id="09c3f-116">停止 BizTalk 應用程式服務 (包括 BAM 事件匯流排服務)，以避免其嘗試將更多資料匯入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="09c3f-116">Stop the BizTalk Application service (which includes the BAM Event Bus service) so it does not try to import more data into the database.</span></span>  
  
    1.  <span data-ttu-id="09c3f-117">按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。</span><span class="sxs-lookup"><span data-stu-id="09c3f-117">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="09c3f-118">以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="09c3f-118">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Stop**.</span></span>  
  
3.  <span data-ttu-id="09c3f-119">BAMPrimaryImport 資料庫，執行中的步驟還原[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="09c3f-119">Restore the BAMPrimaryImport database, performing the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span>  
  
4.  <span data-ttu-id="09c3f-120">更新下列 Web.Config 檔案：</span><span class="sxs-lookup"><span data-stu-id="09c3f-120">Update the following Web.Config files:</span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="09c3f-121">BAMPortal\BamManagementService\Web.Config。</span><span class="sxs-lookup"><span data-stu-id="09c3f-121">BAMPortal\BamManagementService\Web.Config.</span></span>  
  
         <span data-ttu-id="09c3f-122">取代 *\<ServerName >*新的伺服器名稱的字串和 *\<DatabaseName >*與新的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="09c3f-122">Replace the *\<ServerName>* string with the new server name and *\<DatabaseName>* with the new database name.</span></span> <span data-ttu-id="09c3f-123">更新下列連接字串：</span><span class="sxs-lookup"><span data-stu-id="09c3f-123">Update the following connection strings:</span></span>  
  
         <span data-ttu-id="09c3f-124">\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="09c3f-124">\<appSettings></span></span>  
  
         <span data-ttu-id="09c3f-125">< 新增機碼 ="BamServer"value ="*\<ServerName >*"/\></span><span class="sxs-lookup"><span data-stu-id="09c3f-125"><add key="BamServer" value="*\<ServerName>*" /\></span></span>  
  
         <span data-ttu-id="09c3f-126">< 新增機碼 ="BamDatabase"value ="*\<DatabaseName >*"/\></span><span class="sxs-lookup"><span data-stu-id="09c3f-126"><add key="BamDatabase" value="*\<DatabaseName>*" /\></span></span>  
  
         <span data-ttu-id="09c3f-127">\<加入機碼 ="MaxResultRows"value ="2000"/ ></span><span class="sxs-lookup"><span data-stu-id="09c3f-127">\<add key="MaxResultRows" value="2000" /></span></span>  
  
         <span data-ttu-id="09c3f-128">\</appSettings ></span><span class="sxs-lookup"><span data-stu-id="09c3f-128">\</appSettings></span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="09c3f-129">BAMPortal\BamQueryService\Web.Config。</span><span class="sxs-lookup"><span data-stu-id="09c3f-129">BAMPortal\BamQueryService\Web.Config.</span></span>  
  
         <span data-ttu-id="09c3f-130">取代 *\<ServerName >*新的伺服器名稱的字串和 *\<DatabaseName >*與新的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="09c3f-130">Replace the *\<ServerName>* string with the new server name and *\<DatabaseName>* with the new database name.</span></span> <span data-ttu-id="09c3f-131">更新下列連接字串：</span><span class="sxs-lookup"><span data-stu-id="09c3f-131">Update the following connection strings:</span></span>  
  
         <span data-ttu-id="09c3f-132">\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="09c3f-132">\<appSettings></span></span>  
  
         <span data-ttu-id="09c3f-133">< 新增機碼 ="BamServer"value ="*\<ServerName >*"/\></span><span class="sxs-lookup"><span data-stu-id="09c3f-133"><add key="BamServer" value="*\<ServerName>*" /\></span></span>  
  
         <add key="BamDatabase" value="*<DatabaseName>*" />  
  
         <add key="MaxResultRows" value="2000" />  
  
         </appSettings>  
  
5.  <span data-ttu-id="09c3f-134">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="09c3f-134">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="09c3f-135">瀏覽至下列目錄： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore。</span><span class="sxs-lookup"><span data-stu-id="09c3f-135">Navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore.</span></span>  
  
7.  <span data-ttu-id="09c3f-136">以滑鼠右鍵按一下**SampleUpdateInfo.xml**，然後按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="09c3f-136">Right-click **SampleUpdateInfo.xml**, and then click **Edit**.</span></span>  
  
    1.  <span data-ttu-id="09c3f-137">將除了 BizTalkMgmtDb、OldPrimaryImportDatabase、PrimaryImportDatabase、ArchivingDatabase、AnalysisDatabase、StarSchemaDatabase 和 Alert 以外的所有資料庫區段標記為註解。</span><span class="sxs-lookup"><span data-stu-id="09c3f-137">Comment out all of the database sections except for the BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert.</span></span>  
  
    2.  <span data-ttu-id="09c3f-138">BizTalkMgmtDb、 OldPrimaryImportDatabase、 PrimaryImportDatabase、 ArchivingDatabase、 AnalysisDatabase、 StarSchemaDatabase 和 Alert 區段，將**"SourceServer"**和**"Destination Server"**這些資料庫所在的現有伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="09c3f-138">For the BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert sections, set the **"SourceServer"** and **"Destination Server"** to the name of the existing server where those databases reside.</span></span>  
  
    3.  <span data-ttu-id="09c3f-139">Primaryimportdatabase 中，設定**"SourceServer"**移動 BAM 主要匯入資料庫伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="09c3f-139">For PrimaryImportDatabase, set the **"SourceServer"** to the name of the server where you have moved the BAM Primary Import database.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="09c3f-140">在來源及目的系統的名稱兩端加上引號。</span><span class="sxs-lookup"><span data-stu-id="09c3f-140">Include the quotation marks around the name of the source and destination systems.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="09c3f-141">如果重新命名了任何 BizTalk Server 資料庫，您也必須視情況適當更新資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="09c3f-141">If you renamed any of the BizTalk Server databases, you must also update the database names as appropriate.</span></span>  
  
    4.  <span data-ttu-id="09c3f-142">完成檔案的編輯後，請加以儲存並結束。</span><span class="sxs-lookup"><span data-stu-id="09c3f-142">When you are finished editing the file, save it and exit.</span></span>  
  
8.  <span data-ttu-id="09c3f-143">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="09c3f-143">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="09c3f-144">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span><span class="sxs-lookup"><span data-stu-id="09c3f-144">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09c3f-145">您只需執行 UpdateDatabase.vbs 一次。</span><span class="sxs-lookup"><span data-stu-id="09c3f-145">You only need to run UpdateDatabase.vbs once.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09c3f-146">在 64 位元電腦上，您必須從 64 位元命令提示字元中執行 UpdateDatabase.vbs。</span><span class="sxs-lookup"><span data-stu-id="09c3f-146">On 64-bit computers, you must run UpdateDatabase.vbs from a 64-bit command prompt.</span></span>  
  
9. <span data-ttu-id="09c3f-147">在命令提示字元中，瀏覽至下列目錄：</span><span class="sxs-lookup"><span data-stu-id="09c3f-147">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="09c3f-148">Tracking</span><span class="sxs-lookup"><span data-stu-id="09c3f-148">Tracking</span></span>  
  
10. <span data-ttu-id="09c3f-149">在命令提示字元，編輯 bm.exe.config、將 key="DefaultServer" 的值變更為伺服器名稱，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="09c3f-149">At the command prompt, edit bm.exe.config, change the value of key="DefaultServer" to the new server name, and then save the file.</span></span>  
  
11. <span data-ttu-id="09c3f-150">在所有 BAM Livedata Microsoft Excel 檔案中更新 BAMPrimaryImport 資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="09c3f-150">Update the reference to BAMPrimaryImport database in all BAM Livedata Microsoft Excel files.</span></span> <span data-ttu-id="09c3f-151">對於每個檔案：</span><span class="sxs-lookup"><span data-stu-id="09c3f-151">For each file:</span></span>  
  
    1.  <span data-ttu-id="09c3f-152">開啟 Excel 即時資料檔案。</span><span class="sxs-lookup"><span data-stu-id="09c3f-152">Open the Excel live data file.</span></span> <span data-ttu-id="09c3f-153">此檔案名稱是以 _LiveData.xls 結尾。</span><span class="sxs-lookup"><span data-stu-id="09c3f-153">The file name ends with _LiveData.xls.</span></span>  
  
    2.  <span data-ttu-id="09c3f-154">在**BAM**功能表上，按一下  **BAM DB 連線**。</span><span class="sxs-lookup"><span data-stu-id="09c3f-154">On the **BAM** menu, click **BAM DB Connection**.</span></span>  
  
    3.  <span data-ttu-id="09c3f-155">在**選取 BAM 資料庫**對話方塊中，輸入 SQL Server 和 BAMPrimaryImport 資料庫，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="09c3f-155">In the **Select BAM Database** dialog box, enter the SQL Server and BAMPrimaryImport database, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="09c3f-156">在**檔案**功能表上，按一下 **關閉並返回 Microsoft Excel**。</span><span class="sxs-lookup"><span data-stu-id="09c3f-156">On the **File** menu, click **Close and Return to Microsoft Excel**.</span></span>  
  
    5.  <span data-ttu-id="09c3f-157">在 [檔案] 功能表上，按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="09c3f-157">On the **File** menu, click **Save**.</span></span>  
  
12. <span data-ttu-id="09c3f-158">重新啟動 BizTalk 應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="09c3f-158">Restart the BizTalk Application service.</span></span>  
  
    1.  <span data-ttu-id="09c3f-159">按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。</span><span class="sxs-lookup"><span data-stu-id="09c3f-159">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="09c3f-160">以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="09c3f-160">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Start**.</span></span>  
  
13. <span data-ttu-id="09c3f-161">啟用任何 BAM Cube 更新和資料維護 DTS 封裝。</span><span class="sxs-lookup"><span data-stu-id="09c3f-161">Enable any BAM cube update and data maintenance DTS packages.</span></span>  
  
14. <span data-ttu-id="09c3f-162">若要解決任何不完整的追蹤執行個體，請參閱[如何解析未完成的活動執行個體](../core/how-to-resolve-incomplete-activity-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="09c3f-162">To resolve any incomplete trace instances, see [How to Resolve Incomplete Activity Instances](../core/how-to-resolve-incomplete-activity-instances.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c3f-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09c3f-163">See Also</span></span>  
 [<span data-ttu-id="09c3f-164">備份和還原 BAM</span><span class="sxs-lookup"><span data-stu-id="09c3f-164">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)