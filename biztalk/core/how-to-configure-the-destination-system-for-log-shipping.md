---
title: "如何設定記錄傳送目的地系統 |Microsoft 文件"
ms.custom: 
ms.date: 2015-12-03
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, log shipping
- system failures, preventing
- log shipping
- databases, backing up
- backing up, databases
- system failures, backing up
- backing up, system failures
ms.assetid: 7b4425f5-b105-4fb2-a503-94ca1e75ad55
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 611544e77de738c904fa673b56dbec75fd17d4bd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-the-destination-system-for-log-shipping"></a><span data-ttu-id="9052e-102">如何設定記錄傳送的目的系統</span><span class="sxs-lookup"><span data-stu-id="9052e-102">How to Configure the Destination System for Log Shipping</span></span>
<span data-ttu-id="9052e-103">記錄傳送提供待命伺服器功能，發生系統錯誤時可減少停機時間。</span><span class="sxs-lookup"><span data-stu-id="9052e-103">Log shipping provides standby server capabilities to reduce downtime in the event of a system failure.</span></span> <span data-ttu-id="9052e-104">記錄傳送可讓您自動從來源系統的交易記錄檔傳送至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="9052e-104">Log shipping allows you to automatically send transaction logs from the source system to the destination system.</span></span> <span data-ttu-id="9052e-105">在目的系統，交易記錄會還原到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫中，使這些資料庫與來源資料庫緊密同步。</span><span class="sxs-lookup"><span data-stu-id="9052e-105">At the destination system, the transaction logs are restored to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases; keeping them closely synchronized with the source databases.</span></span>  
  
 <span data-ttu-id="9052e-106">記錄傳送可同時在單一伺服器和分散式伺服器環境中運作。</span><span class="sxs-lookup"><span data-stu-id="9052e-106">Log shipping works in both single server and distributed server environments.</span></span> <span data-ttu-id="9052e-107">包含即時資料的伺服器群組的伺服器稱為來源 （或主要） 系統。</span><span class="sxs-lookup"><span data-stu-id="9052e-107">The server or group of servers that contain live data is known as the source (or primary) system.</span></span> <span data-ttu-id="9052e-108">伺服器或用來還原資料庫備份的來源所產生的 （或主要） 系統的伺服器群組就稱為目的地 （或次要） 系統。</span><span class="sxs-lookup"><span data-stu-id="9052e-108">The server or group of servers that are used to restore the database backups produced by the source (or primary) system is known as the destination (or secondary) system.</span></span>  
  
 <span data-ttu-id="9052e-109">[關於記錄傳送](https://docs.microsoft.com/sql/database-engine/log-shipping/about-log-shipping-sql-server)SQL 中的文件提供的特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9052e-109">[About Log Shipping](https://docs.microsoft.com/sql/database-engine/log-shipping/about-log-shipping-sql-server) in the SQL documentation provides specific details.</span></span>  
  
 <span data-ttu-id="9052e-110">您可以使用下列步驟來建立包含單一來源系統的一部伺服器的目的地系統。</span><span class="sxs-lookup"><span data-stu-id="9052e-110">You can use the following steps to create a destination system that consists of one server for a single source system.</span></span> <span data-ttu-id="9052e-111">如果目的系統包含多部伺服器，請在每部目的伺服器上重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="9052e-111">If the destination system contains multiple servers, repeat the steps on each destination server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9052e-112">請務必在安全的位置保留備份檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="9052e-112">Always keep a copy of your backup files in a secure location.</span></span> <span data-ttu-id="9052e-113">即使您擁有記錄檔備份，也無法在沒有備份檔案的情況下還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="9052e-113">Even if you have log backups, you cannot restore your databases without the backup files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9052e-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="9052e-114">Prerequisites</span></span>  
* <span data-ttu-id="9052e-115">成員的身分登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="9052e-115">Sign in as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
* <span data-ttu-id="9052e-116">在來源和目的地系統上使用相同版本的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="9052e-116">Use the same version of SQL Server on the source and destination systems.</span></span> <span data-ttu-id="9052e-117">SQL Server 必須安裝在來源和目的地系統上相同的相對位置。</span><span class="sxs-lookup"><span data-stu-id="9052e-117">SQL Server must be installed in the same relative location on the source and destination systems.</span></span>  
  
* <span data-ttu-id="9052e-118">來源系統上 SQL 交易記錄 (.LDF 檔案) 的目錄也必須存在於目的系統上。</span><span class="sxs-lookup"><span data-stu-id="9052e-118">The directory for SQL transaction log (.LDF files) on the source system must also exist on the destination system.</span></span> <span data-ttu-id="9052e-119">如果目的系統上沒有這個目錄，請以和來源系統上相同的名稱和權限來建立此目錄。</span><span class="sxs-lookup"><span data-stu-id="9052e-119">If this directory is not on the destination system, create the directory with the same name and permissions as on the source system.</span></span>  
  
### <a name="configure-the-destination-system-for-log-shipping"></a><span data-ttu-id="9052e-120">設定目的系統以進行記錄傳送</span><span class="sxs-lookup"><span data-stu-id="9052e-120">Configure the destination system for log shipping</span></span>  
  
1.  <span data-ttu-id="9052e-121">在目的地系統上，開啟**SQL Server Management Studio**，並連接到您的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="9052e-121">On the destination system, open **SQL Server Management Studio**, and connect to your SQL Server.</span></span> <span data-ttu-id="9052e-122">選取**主要**從可用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="9052e-122">Select **master** from Available Databases.</span></span>  
  
2.  <span data-ttu-id="9052e-123">在**檔案**功能表上，**開啟**下列 SQL 指令碼：</span><span class="sxs-lookup"><span data-stu-id="9052e-123">On the **File** menu, **Open** the following SQL script:</span></span>  
  
    ```    
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\LogShipping_Destination_Schema.sql  
    ```  
  
3.  <span data-ttu-id="9052e-124">在**查詢**功能表上，選取**Execute**。</span><span class="sxs-lookup"><span data-stu-id="9052e-124">On the **Query** menu, select **Execute**.</span></span>  
  
     <span data-ttu-id="9052e-125">*LogShipping_Destination_Schema*卸除並重新建立用來還原來源資料庫，在目的系統上的資料表。</span><span class="sxs-lookup"><span data-stu-id="9052e-125">The *LogShipping_Destination_Schema* drops and recreates the tables used for restoring the source databases on the destination system.</span></span> <span data-ttu-id="9052e-126">這些資料表儲存的內容包括所要還原的資料庫清單、從來源系統的 BizTalkMgmtDb 資料庫匯入的備份歷程記錄的複本，以及設定為針對來源資料庫執行的 SQL Server Agent 作業之相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9052e-126">This includes tables to store the list of databases being recovered, copies of the backup history imported from the source system's BizTalkMgmtDb database, and information about SQL Server Agent jobs configured to run against the source databases.</span></span>  
  
4.  <span data-ttu-id="9052e-127">在**檔案**功能表上，**開啟**下列 SQL 指令碼：</span><span class="sxs-lookup"><span data-stu-id="9052e-127">On the **File** menu, **Open** the following SQL script:</span></span>  
  
    ```    
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\LogShipping_Destination_Logic.sql  
    ```  
  
5.  <span data-ttu-id="9052e-128">在**查詢**功能表上，選取**Execute**。</span><span class="sxs-lookup"><span data-stu-id="9052e-128">On the **Query** menu, select **Execute**.</span></span>  
  
6.  <span data-ttu-id="9052e-129">在電腦或在已的識別為目的系統中，開啟**SQL Server Management Studio**並連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="9052e-129">On the computer or computers you have identified as the destination system, open **SQL Server Management Studio** and connect to the SQL Server.</span></span>  
  
7.  <span data-ttu-id="9052e-130">選取**新查詢**。</span><span class="sxs-lookup"><span data-stu-id="9052e-130">Select **New Query**.</span></span> <span data-ttu-id="9052e-131">在查詢視窗中，貼上下列命令：</span><span class="sxs-lookup"><span data-stu-id="9052e-131">In the query window, paste the following command:</span></span>  
  
    ```  
    exec bts_ConfigureBizTalkLogShipping @nvcDescription = '<MyLogShippingSolution>',  
    @nvcMgmtDatabaseName = '<BizTalkServerManagementDatabaseName>',  
    @nvcMgmtServerName = '<BizTalkServerManagementDatabaseServer>',  
    @SourceServerName = null, -- null indicates that this destination server restores all databases  
    @fLinkServers = 1 -- 1 automatically links the server to the management database  
    ```  
  
     <span data-ttu-id="9052e-132">然後：</span><span class="sxs-lookup"><span data-stu-id="9052e-132">Then:</span></span>  
  
    1.  <span data-ttu-id="9052e-133">在目的地系統上啟用 **[Ad Hoc Distributed Queries](https://docs.microsoft.com/sql/database-engine/configure-windows/server-configuration-options-sql-server)**。</span><span class="sxs-lookup"><span data-stu-id="9052e-133">On the destination system, enable **[Ad Hoc Distributed Queries](https://docs.microsoft.com/sql/database-engine/configure-windows/server-configuration-options-sql-server)**.</span></span>  
  
    2.  <span data-ttu-id="9052e-134">在查詢視窗中，取代 *\<MyLogShippingSolution\>* 意義的描述，並以單引號括住。</span><span class="sxs-lookup"><span data-stu-id="9052e-134">In the query window, replace *\<MyLogShippingSolution\>* with a meaningful description, surrounded by single quotes.</span></span>  
  
    3.  <span data-ttu-id="9052e-135">在查詢視窗中，取代 *\<BizTalkServerManagementDatabaseName\>* 和 *\<BizTalkServerManagementDatabaseServer\>* 與名稱和位置的來源 BizTalk 管理資料庫，以單引號括住。</span><span class="sxs-lookup"><span data-stu-id="9052e-135">In the query window, replace *\<BizTalkServerManagementDatabaseName\>* and *\<BizTalkServerManagementDatabaseServer\>* with the name and location of your source BizTalk Management database, surrounded by single quotes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9052e-136">如果您有一個以上的來源伺服器，則可以將每個來源伺服器還原到各自的目的伺服器。</span><span class="sxs-lookup"><span data-stu-id="9052e-136">If you have more than one source server, you can restore each source server to its own destination server.</span></span> <span data-ttu-id="9052e-137">每個目的地伺服器上，在 **@SourceServerName = null**參數取代*null*適當來源伺服器的名稱，並以單引號括住 (例如，  **@SourceServerName = 'MySourceServer'**)。</span><span class="sxs-lookup"><span data-stu-id="9052e-137">On each destination server, in the **@SourceServerName = null** parameter, replace *null* with the name of the appropriate source server, surrounded by single quotes (for example, **@SourceServerName = 'MySourceServer',**).</span></span>  
  
8.  <span data-ttu-id="9052e-138">在**查詢**功能表上，選取**Execute**。</span><span class="sxs-lookup"><span data-stu-id="9052e-138">On the **Query** menu, select **Execute**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9052e-139">如果查詢失敗，修正查詢的問題之後，您必須啟動在步驟 1 中的這個程序來重新設定目的系統。</span><span class="sxs-lookup"><span data-stu-id="9052e-139">If the query fails, after you fix the problem with the query, you must start over from step 1 of this procedure to reconfigure the destination system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9052e-140">在目的系統上的還原作業嘗試將存在於來源伺服器上重新建立的記錄檔和資料檔中每個已還原資料庫的相同位置。</span><span class="sxs-lookup"><span data-stu-id="9052e-140">The restore jobs on the destination system attempt to recreate the log and data files for each restored database in the same location as they existed on the source database server.</span></span>  
  
9. <span data-ttu-id="9052e-141">在目的地系統上**SQL Server Management Studio**，依序展開**SQL Server Agent**，並展開**作業**。</span><span class="sxs-lookup"><span data-stu-id="9052e-141">On the destination system in **SQL Server Management Studio**, expand **SQL Server Agent**, and expand **Jobs**.</span></span>  
  
     <span data-ttu-id="9052e-142">在 [詳細資料] 窗格中，有三個新的工作：</span><span class="sxs-lookup"><span data-stu-id="9052e-142">In the details pane, there are three new jobs:</span></span>  
  
    -   <span data-ttu-id="9052e-143">**BTS 記錄傳送取得備份歷程記錄**</span><span class="sxs-lookup"><span data-stu-id="9052e-143">**BTS Log Shipping Get Backup History**</span></span>  
  
         <span data-ttu-id="9052e-144">這個 BizTalk 工作會將備份歷程記錄從來源移至目的地。</span><span class="sxs-lookup"><span data-stu-id="9052e-144">This BizTalk job moves backup history records from the source to the destination.</span></span> <span data-ttu-id="9052e-145">此作業依預設排程為每分鐘執行一次。</span><span class="sxs-lookup"><span data-stu-id="9052e-145">It is scheduled by default to run every minute.</span></span> <span data-ttu-id="9052e-146">這項作業會經常不斷執行，將歷程記錄從來源移至目的地。</span><span class="sxs-lookup"><span data-stu-id="9052e-146">This job runs as frequently as possible in order to move history records from the source to the destination.</span></span> <span data-ttu-id="9052e-147">來源系統的系統失敗，發生在您識別為目的系統的伺服器會繼續處理已經匯入的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="9052e-147">In the event of a system failure to the source system, the server that you identified as the destination system continues to process the history records that have already been imported.</span></span>  
  
    -   <span data-ttu-id="9052e-148">**BTS Server 記錄傳送還原資料庫**</span><span class="sxs-lookup"><span data-stu-id="9052e-148">**BTS Server Log Shipping Restore Databases**</span></span>  
  
         <span data-ttu-id="9052e-149">這個 BizTalk 工作會將來源的指定資料庫的備份檔案還原到目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="9052e-149">This BizTalk job restores backup files for the given databases for the source to the destination server.</span></span> <span data-ttu-id="9052e-150">此作業依預設排程為每分鐘執行一次。</span><span class="sxs-lookup"><span data-stu-id="9052e-150">It is scheduled by default to run every minute.</span></span> <span data-ttu-id="9052e-151">只要仍然有需要還原的備份檔案，這項作業就會繼續執行而無法完成。</span><span class="sxs-lookup"><span data-stu-id="9052e-151">This job runs continuously without completing as long as there are backup files to restore.</span></span> <span data-ttu-id="9052e-152">為採取額外的預防措施，您可讓這項作業執行久一點以確保其完成。</span><span class="sxs-lookup"><span data-stu-id="9052e-152">As an extra precaution, you can run this job an additional time to ensure that it is complete.</span></span>  
  
    -   <span data-ttu-id="9052e-153">**BTS 記錄傳送還原為標示**</span><span class="sxs-lookup"><span data-stu-id="9052e-153">**BTS Log Shipping Restore To Mark**</span></span>  
  
         <span data-ttu-id="9052e-154">此 BizTalk 作業會將所有的資料庫至標示的最後一個記錄備份中。</span><span class="sxs-lookup"><span data-stu-id="9052e-154">This BizTalk job restores all of the databases to a mark in the last log backup.</span></span> <span data-ttu-id="9052e-155">這樣可以確保所有的資料庫在交易上處於一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="9052e-155">This ensures that all of the databases are in a transactionally consistent state.</span></span> <span data-ttu-id="9052e-156">此外，這項作業還會在目的系統上重新建立原本在來源系統上進行的所有 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="9052e-156">In addition, this job re-creates all of the SQL Server Agent jobs on the destination system that had been on the source system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9052e-157">請務必監控這些作業以防作業失敗。</span><span class="sxs-lookup"><span data-stu-id="9052e-157">You should monitor these jobs to ensure that they do not fail.</span></span>  
  
10. <span data-ttu-id="9052e-158">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請移至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="9052e-158">On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], go to the following folder:</span></span>  
  
     <span data-ttu-id="9052e-159">32 位元電腦： %SystemDrive%\Program Files\Microsoft BizTalk Server\<版本\>\Schema\Restore</span><span class="sxs-lookup"><span data-stu-id="9052e-159">32-bit computer: %SystemDrive%\Program Files\Microsoft BizTalk Server \<version\>\Schema\Restore</span></span>  
  
     <span data-ttu-id="9052e-160">64 位元電腦： %SystemDrive%\Program Files (x86) \Microsoft BizTalk Server\<版本\>\Bins32\Schema\Restore</span><span class="sxs-lookup"><span data-stu-id="9052e-160">64-bit computer: %SystemDrive%\Program Files (x86)\Microsoft BizTalk Server \<version\>\Bins32\Schema\Restore</span></span>  
  
11. <span data-ttu-id="9052e-161">以滑鼠右鍵按一下**SampleUpdateInfo.xml**，然後選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="9052e-161">Right-click **SampleUpdateInfo.xml**, and select **Edit**.</span></span> <span data-ttu-id="9052e-162">執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9052e-162">Do the following:</span></span>  
  
    -   <span data-ttu-id="9052e-163">所有執行個體**"SourceServer"**來源系統的名稱。</span><span class="sxs-lookup"><span data-stu-id="9052e-163">Replace all instances of **"SourceServer"** with the name of the source system.</span></span>  
  
    -   <span data-ttu-id="9052e-164">所有執行個體**"DestinationServer"**目的系統的名稱。</span><span class="sxs-lookup"><span data-stu-id="9052e-164">Replace all instances of **"DestinationServer"** with the name of the destination system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9052e-165">在來源及目的系統的名稱兩端加上引號。</span><span class="sxs-lookup"><span data-stu-id="9052e-165">Include the quotation marks around the name of the source and destination systems.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9052e-166">如果您重新命名任何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，您也必須更新 XML 檔案中的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="9052e-166">If you renamed any of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must also update the database names within the XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9052e-167">如果您已設定 BAM，您必須加入下列幾行中的**OtherDatabases**區段**SampleUpdateInfo.xml** BAMAlertsApplication 和 BAMAlertsNSMain 資料庫檔案：</span><span class="sxs-lookup"><span data-stu-id="9052e-167">If you have configured BAM, you must add the following lines in the **OtherDatabases** section of the **SampleUpdateInfo.xml** file for the BAMAlertsApplication and BAMAlertsNSMain databases:</span></span>   
    > `<Database Name="BAM Alerts Application DB" oldDBName="BAMAlertsApplication" oldDBServer="SourceServer" newDBName=" BAMAlertsApplication" newDBServer="DestinationServer"/>`  
    > `<Database Name="BAM Alerts Instance DB" oldDBName="BAMAlertsNSMain" oldDBServer="SourceServer" newDBName="BAMAlertsNSMain" newDBServer="DestinationServer"/>`  
    >   
    >  <span data-ttu-id="9052e-168">如果您變更這兩個資料庫的預設名稱，請使用實際的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="9052e-168">If you changed the default name for these two databases, please use the actual database names.</span></span>  
  
12. <span data-ttu-id="9052e-169">如果您有一個以上的 MessageBox 資料庫您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統中，加入清單中，加入另一行 MessageBoxDB，然後設定**IsMaster ="0"**非主要資料庫。</span><span class="sxs-lookup"><span data-stu-id="9052e-169">If you have more than one MessageBox database in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system, add another MessageBoxDB line to the list, and then set **IsMaster="0"** for the non-master databases.</span></span>  
  
13. <span data-ttu-id="9052e-170">如果您使用 BAM 或 「 規則引擎，請視需要這些行取消註解。</span><span class="sxs-lookup"><span data-stu-id="9052e-170">If you are using BAM or the Rules Engine, uncomment these lines as appropriate.</span></span>  
  
14. <span data-ttu-id="9052e-171">如果您有任何自訂資料庫，將它們加入下 **\<OtherDatabases\>**  > 一節。</span><span class="sxs-lookup"><span data-stu-id="9052e-171">If you have any custom databases, add them under the **\<OtherDatabases\>** section.</span></span> <span data-ttu-id="9052e-172">請參閱[如何備份自訂資料庫](../core/how-to-back-up-custom-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="9052e-172">See [How to Back Up Custom Databases](../core/how-to-back-up-custom-databases.md).</span></span>  
  
15. <span data-ttu-id="9052e-173">當您完成編輯檔案時，加以儲存，並結束。</span><span class="sxs-lookup"><span data-stu-id="9052e-173">When you are finished editing the file, save it, and exit.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9052e-174">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9052e-174">Next Steps</span></span>  
 [<span data-ttu-id="9052e-175">如何還原資料庫</span><span class="sxs-lookup"><span data-stu-id="9052e-175">How to Restore Your Databases</span></span>](../core/how-to-restore-your-databases.md)  
  
## <a name="see-also"></a><span data-ttu-id="9052e-176">請參閱</span><span class="sxs-lookup"><span data-stu-id="9052e-176">See Also</span></span>  
 <span data-ttu-id="9052e-177">[如何設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="9052e-177">[How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md) </span></span>  
 <span data-ttu-id="9052e-178">[如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="9052e-178">[How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md) </span></span>  
 [<span data-ttu-id="9052e-179">如何備份自訂資料庫</span><span class="sxs-lookup"><span data-stu-id="9052e-179">How to Back Up Custom Databases</span></span>](../core/how-to-back-up-custom-databases.md)