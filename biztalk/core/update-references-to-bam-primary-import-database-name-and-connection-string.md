---
title: 更新 BAM 主要匯入資料庫名稱和連接字串 |Microsoft Docs
ms.custom: ''
ms.date: 02/01/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e3c58db0-f14f-429a-813c-bae29f6950d3
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 846aa3b08ce6cce9b2334da72440cf5ba918e5d9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003135"
---
# <a name="update-references-to-the-bam-primary-import-database-name-and-connection-string"></a><span data-ttu-id="94a78-102">更新 BAM 主要匯入資料庫名稱和連接字串的參考</span><span class="sxs-lookup"><span data-stu-id="94a78-102">Update References to the BAM Primary Import Database Name and Connection String</span></span>
<span data-ttu-id="94a78-103">如果您備份 BAMPrimaryImport 資料庫發生系統或資料錯誤時，您可以將該備份還原至不同的電腦，並重新命名此備份。</span><span class="sxs-lookup"><span data-stu-id="94a78-103">If you backed up your BAMPrimaryImport database in the event of a system or data failure, you can restore that backup to a different computer and rename the backup.</span></span>  
  
 <span data-ttu-id="94a78-104">BAM 事件匯流排服務會將事件資料從 MessageBox 資料庫移到 BAMPrimaryImport 資料庫。</span><span class="sxs-lookup"><span data-stu-id="94a78-104">The BAM Event Bus service moves event data from the MessageBox database to the BAMPrimaryImport database.</span></span> <span data-ttu-id="94a78-105">BAM 事件匯流排服務包含容錯邏輯，可讓它從意外的失敗中復原和重新啟動，而不會遺失任何資料。</span><span class="sxs-lookup"><span data-stu-id="94a78-105">The BAM Event Bus service includes fault tolerance logic that enables it to recover and restart from an unexpected failure without losing any data.</span></span> <span data-ttu-id="94a78-106">如需有關 BAM 事件匯流排服務的詳細資訊，請參閱 <<c0> [ 管理 BAM 事件匯流排服務](../core/managing-the-bam-event-bus-service.md)。</span><span class="sxs-lookup"><span data-stu-id="94a78-106">For more information about the BAM Event Bus service, see [Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md).</span></span>  
  
 <span data-ttu-id="94a78-107">若要還原 BAMPrimaryImport 資料庫，執行中的步驟[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="94a78-107">To restore the BAMPrimaryImport database, perform the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span> <span data-ttu-id="94a78-108">此外，您也必須執行下列一般步驟，各步驟之後都有詳細說明步驟的程序：</span><span class="sxs-lookup"><span data-stu-id="94a78-108">In addition, you must perform these general steps, which are followed by a procedure that describes the steps in detail:</span></span>  
  
-   <span data-ttu-id="94a78-109">更新所有 BAM DTS 封裝中的「SQL 連線 1」，以參考新的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="94a78-109">Update the SQL Connection 1 in all BAM DTS packages to refer to the new database name.</span></span>  
  
-   <span data-ttu-id="94a78-110">以新的資料庫名稱更新 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="94a78-110">Update the web.config file with the new database name.</span></span>  
  
-   <span data-ttu-id="94a78-111">在所有 BAM Livedata Microsoft Excel 檔案中更新 BAMPrimaryImport 資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="94a78-111">Update the reference to BAMPrimaryImport database in all BAM Livedata Microsoft Excel files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="94a78-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="94a78-112">Prerequisites</span></span>  
<span data-ttu-id="94a78-113">BizTalk Server 系統管理員群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="94a78-113">Sign in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="update-the-references"></a><span data-ttu-id="94a78-114">更新參考</span><span class="sxs-lookup"><span data-stu-id="94a78-114">Update the references</span></span>  
  
1. <span data-ttu-id="94a78-115">停止任何 BAM cube 更新和資料維護 Data Transformation Services (DTS) 封裝，或防止它們執行，直到您完成 BAMPrimaryImport 資料庫的還原為止。</span><span class="sxs-lookup"><span data-stu-id="94a78-115">Stop any BAM cube update and data maintenance Data Transformation Services (DTS) packages, or prevent them from running until you have restored the BAMPrimaryImport database.</span></span>  
  
2. <span data-ttu-id="94a78-116">停止 BizTalk 應用程式服務 (包括 BAM 事件匯流排服務)，以避免其嘗試將更多資料匯入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="94a78-116">Stop the BizTalk Application service (which includes the BAM Event Bus service) so it does not try to import more data into the database.</span></span>  
  
   1.  <span data-ttu-id="94a78-117">從**開始**功能表中，輸入**services.msc**，然後開啟**Services**。</span><span class="sxs-lookup"><span data-stu-id="94a78-117">From the **Start** menu, type **services.msc**, and open **Services**.</span></span>  
  
   2.  <span data-ttu-id="94a78-118">以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後**停止**。</span><span class="sxs-lookup"><span data-stu-id="94a78-118">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service, and then **Stop**.</span></span>  
  
3. <span data-ttu-id="94a78-119">BAMPrimaryImport 資料庫還原 (中的步驟[如何還原您的資料庫](../core/how-to-restore-your-databases.md))。</span><span class="sxs-lookup"><span data-stu-id="94a78-119">Restore the BAMPrimaryImport database (steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md)).</span></span>  
  
4. <span data-ttu-id="94a78-120">更新下列 Web.Config 檔案：</span><span class="sxs-lookup"><span data-stu-id="94a78-120">Update the following Web.Config files:</span></span>  
  
   - [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="94a78-121">\BAMPortal\BamManagementService\Web.Config。</span><span class="sxs-lookup"><span data-stu-id="94a78-121">\BAMPortal\BamManagementService\Web.Config.</span></span>  
  
      <span data-ttu-id="94a78-122">取代*\<ServerName\>* 字串取代新的伺服器名稱，並*\<DatabaseName\>* 與新的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="94a78-122">Replace the *\<ServerName\>* string with the new server name, and *\<DatabaseName\>* with the new database name.</span></span> <span data-ttu-id="94a78-123">更新下列連接字串：</span><span class="sxs-lookup"><span data-stu-id="94a78-123">Update the following connection strings:</span></span>  
  
      <span data-ttu-id="94a78-124">\<appSettings\></span><span class="sxs-lookup"><span data-stu-id="94a78-124">\<appSettings\></span></span>  
  
      <span data-ttu-id="94a78-125"><add key="BamServer" value="*\<ServerName\>*" /\></span><span class="sxs-lookup"><span data-stu-id="94a78-125"><add key="BamServer" value="*\<ServerName\>*" /\></span></span>  
  
      <span data-ttu-id="94a78-126">< 新增機碼 ="BamDatabase"value ="*\<DatabaseName\>*"/\></span><span class="sxs-lookup"><span data-stu-id="94a78-126"><add key="BamDatabase" value="*\<DatabaseName\>*" /\></span></span>  
  
      <span data-ttu-id="94a78-127">\<add key="MaxResultRows" value="2000" /\></span><span class="sxs-lookup"><span data-stu-id="94a78-127">\<add key="MaxResultRows" value="2000" /\></span></span>  
  
      <span data-ttu-id="94a78-128">\</appSettings\></span><span class="sxs-lookup"><span data-stu-id="94a78-128">\</appSettings\></span></span>  
  
   - [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="94a78-129">\BAMPortal\BamQueryService\Web.Config。</span><span class="sxs-lookup"><span data-stu-id="94a78-129">\BAMPortal\BamQueryService\Web.Config.</span></span>  
  
      <span data-ttu-id="94a78-130">取代*\<ServerName\>* 新的伺服器名稱的字串並*\<DatabaseName\>* 與新的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="94a78-130">Replace the *\<ServerName\>* string with the new server name and *\<DatabaseName\>* with the new database name.</span></span> <span data-ttu-id="94a78-131">更新下列連接字串：</span><span class="sxs-lookup"><span data-stu-id="94a78-131">Update the following connection strings:</span></span>  
  
      <span data-ttu-id="94a78-132">\<appSettings\></span><span class="sxs-lookup"><span data-stu-id="94a78-132">\<appSettings\></span></span>  
  
      <span data-ttu-id="94a78-133">\<add key="BamServer" value="*\<ServerName\>*" /\></span><span class="sxs-lookup"><span data-stu-id="94a78-133">\<add key="BamServer" value="*\<ServerName\>*" /\></span></span>  
  
      <span data-ttu-id="94a78-134">\<新增機碼 ="BamDatabase"value ="*\<DatabaseName\>*"/\></span><span class="sxs-lookup"><span data-stu-id="94a78-134">\<add key="BamDatabase" value="*\<DatabaseName\>*" /\></span></span>  
  
      <span data-ttu-id="94a78-135">\<add key="MaxResultRows" value="2000" /\></span><span class="sxs-lookup"><span data-stu-id="94a78-135">\<add key="MaxResultRows" value="2000" /\></span></span>  
  
      <span data-ttu-id="94a78-136">\</appSettings\></span><span class="sxs-lookup"><span data-stu-id="94a78-136">\</appSettings\></span></span>  
  
5. <span data-ttu-id="94a78-137">開啟命令提示字元 ([開始] 功能表 > 命令提示字元)，並瀏覽至下列目錄： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Schema\Restore。</span><span class="sxs-lookup"><span data-stu-id="94a78-137">Open a command prompt (Start menu > Command Prompt), and navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Schema\Restore.</span></span>  
  
6. <span data-ttu-id="94a78-138">以滑鼠右鍵按一下**SampleUpdateInfo.xml**，並**編輯**。</span><span class="sxs-lookup"><span data-stu-id="94a78-138">Right-click **SampleUpdateInfo.xml**, and **Edit**.</span></span>  
  
   1.  <span data-ttu-id="94a78-139">標記為註解所有除了 OldPrimaryImportDatabase、 PrimaryImportDatabase、 ArchivingDatabase、 AnalysisDatabase、 StarSchemaDatabase 和警示的資料庫區段。</span><span class="sxs-lookup"><span data-stu-id="94a78-139">Comment out all of the database sections except for the  OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert.</span></span> 
   2.  <span data-ttu-id="94a78-140">對於 OldPrimaryImportDatabase、 PrimaryImportDatabase、 ArchivingDatabase、 AnalysisDatabase、 StarSchemaDatabase 和 Alert 區段，來設定**SourceServer**並**目的地伺服器**至這些資料庫所在的現有伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="94a78-140">For the OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert sections, set the **SourceServer** and **Destination Server** to the name of the existing server where those databases reside.</span></span>  
  
   3.  <span data-ttu-id="94a78-141">Primaryimportdatabase 中，設定 **"SourceServer"** 您已經在其中移動 BAM 主要匯入資料庫的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="94a78-141">For PrimaryImportDatabase, set the **"SourceServer"** to the name of the server where you have moved the BAM Primary Import database.</span></span>  
  
       > [!IMPORTANT]
       >  <span data-ttu-id="94a78-142">在來源及目的系統的名稱兩端加上引號。</span><span class="sxs-lookup"><span data-stu-id="94a78-142">Include the quotation marks around the name of the source and destination systems.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="94a78-143">如果您重新命名任何 BizTalk Server 資料庫，請務必一併更新資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="94a78-143">If you renamed any of the BizTalk Server databases, be sure to also update the database names.</span></span>  
  
   4.  <span data-ttu-id="94a78-144">當您完成編輯檔案時，加以儲存，並結束。</span><span class="sxs-lookup"><span data-stu-id="94a78-144">When you are finished editing the file, save it, and exit.</span></span>  
  
7. <span data-ttu-id="94a78-145">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="94a78-145">At the command prompt, type:</span></span>  
  
    <span data-ttu-id="94a78-146">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span><span class="sxs-lookup"><span data-stu-id="94a78-146">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="94a78-147">只執行 UpdateDatabase.vbs 一次。</span><span class="sxs-lookup"><span data-stu-id="94a78-147">Only run UpdateDatabase.vbs once.</span></span>  
   > 
   >  <span data-ttu-id="94a78-148">在 64 位元電腦上的 64 位元命令提示字元中執行 UpdateDatabase.vbs。</span><span class="sxs-lookup"><span data-stu-id="94a78-148">On 64-bit computers, run UpdateDatabase.vbs from a 64-bit command prompt.</span></span>  
  
8. <span data-ttu-id="94a78-149">在命令提示字元中，瀏覽至下列目錄：</span><span class="sxs-lookup"><span data-stu-id="94a78-149">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="94a78-150">\Tracking</span><span class="sxs-lookup"><span data-stu-id="94a78-150">\Tracking</span></span>  
  
9. <span data-ttu-id="94a78-151">在命令提示字元，編輯 bm.exe.config、將 key="DefaultServer" 的值變更為伺服器名稱，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="94a78-151">At the command prompt, edit bm.exe.config, change the value of key="DefaultServer" to the new server name, and then save the file.</span></span>  
  
10. <span data-ttu-id="94a78-152">在所有 BAM Livedata Microsoft Excel 檔案中更新 BAMPrimaryImport 資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="94a78-152">Update the reference to BAMPrimaryImport database in all BAM Livedata Microsoft Excel files.</span></span> <span data-ttu-id="94a78-153">對於每個檔案：</span><span class="sxs-lookup"><span data-stu-id="94a78-153">For each file:</span></span>  
  
    1.  <span data-ttu-id="94a78-154">開啟 Excel 即時資料檔案。</span><span class="sxs-lookup"><span data-stu-id="94a78-154">Open the Excel live data file.</span></span> <span data-ttu-id="94a78-155">此檔案名稱是以 _LiveData.xls 結尾。</span><span class="sxs-lookup"><span data-stu-id="94a78-155">The file name ends with _LiveData.xls.</span></span>  
  
    2.  <span data-ttu-id="94a78-156">在  **BAM**功能表上，按一下**BAM DB 連線**。</span><span class="sxs-lookup"><span data-stu-id="94a78-156">On the **BAM** menu, click **BAM DB Connection**.</span></span>  
  
    3.  <span data-ttu-id="94a78-157">在 [**選取 BAM 資料庫**] 對話方塊中，輸入 SQL Server 和 BAMPrimaryImport 資料庫，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="94a78-157">In the **Select BAM Database** dialog box, enter the SQL Server and BAMPrimaryImport database, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="94a78-158">在 **檔案**功能表上，按一下**關閉並返回 Microsoft Excel**。</span><span class="sxs-lookup"><span data-stu-id="94a78-158">On the **File** menu, click **Close and Return to Microsoft Excel**.</span></span>  
  
    5.  <span data-ttu-id="94a78-159">在 [檔案] 功能表上，按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="94a78-159">On the **File** menu, click **Save**.</span></span>  
  
11. <span data-ttu-id="94a78-160">重新啟動 BizTalk 應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="94a78-160">Restart the BizTalk Application service.</span></span>  
  
    1.  <span data-ttu-id="94a78-161">開啟 **services.msc**。</span><span class="sxs-lookup"><span data-stu-id="94a78-161">Open **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="94a78-162">以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後**開始**。</span><span class="sxs-lookup"><span data-stu-id="94a78-162">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service, and then **Start**.</span></span>  
  
12. <span data-ttu-id="94a78-163">啟用任何 BAM Cube 更新和資料維護 DTS 封裝。</span><span class="sxs-lookup"><span data-stu-id="94a78-163">Enable any BAM cube update and data maintenance DTS packages.</span></span>  
  
13. <span data-ttu-id="94a78-164">若要解決任何不完整的追蹤執行個體，請參閱[解析未完成的活動執行個體](../core/how-to-resolve-incomplete-activity-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="94a78-164">To resolve any incomplete trace instances, see [Resolve Incomplete Activity Instances](../core/how-to-resolve-incomplete-activity-instances.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a78-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94a78-165">See Also</span></span>  
 [<span data-ttu-id="94a78-166">備份和還原 BAM</span><span class="sxs-lookup"><span data-stu-id="94a78-166">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)
