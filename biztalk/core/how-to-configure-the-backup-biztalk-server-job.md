---
title: "設定 「 備份 BizTalk Server 」 工作 |Microsoft 文件"
ms.custom: 
ms.date: 11/02/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 026622c9-fcb4-4db0-af48-1379feb30372
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67765cfacc7753d649c14677c5399e9c2c7b1e39
ms.sourcegitcommit: 6095645d541bf84f39ff5f342f782284c22e875b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2017
---
# <a name="configure-the-backup-biztalk-server-job"></a><span data-ttu-id="f70b1-102">設定 「 備份 BizTalk Server 」 工作</span><span class="sxs-lookup"><span data-stu-id="f70b1-102">Configure the Backup BizTalk Server Job</span></span>
<span data-ttu-id="f70b1-103">列出設定 「 備份 BizTalk Server 」 工作所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="f70b1-103">Lists the steps necessary to configure the Backup BizTalk Server job.</span></span>  

## <a name="overview"></a><span data-ttu-id="f70b1-104">概觀</span><span class="sxs-lookup"><span data-stu-id="f70b1-104">Overview</span></span>
<span data-ttu-id="f70b1-105">安裝和設定 BizTalk Server 之後，設定備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業來備份您的資料。</span><span class="sxs-lookup"><span data-stu-id="f70b1-105">After you install and configure BizTalk Server, configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job to back up your data.</span></span> <span data-ttu-id="f70b1-106">**備份 BizTalk Server (BizTalkMgmtDb)**工作包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f70b1-106">The **Backup BizTalk Server (BizTalkMgmtDb)** job includes the following steps:</span></span>

-   <span data-ttu-id="f70b1-107">步驟 1 –**集壓縮選項**： 啟用或停用備份期間的壓縮</span><span class="sxs-lookup"><span data-stu-id="f70b1-107">Step 1 – **Set Compression Option**: Enable or disable compression during backup</span></span>

-   <span data-ttu-id="f70b1-108">步驟 2 – **BackupFull**： 執行完整資料庫備份 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="f70b1-108">Step 2 – **BackupFull**: Runs full database backups of the BizTalk Server databases</span></span>

-   <span data-ttu-id="f70b1-109">步驟 3 – **MarkAndBackUpLog**： 備份 BizTalk Server 資料庫記錄檔</span><span class="sxs-lookup"><span data-stu-id="f70b1-109">Step 3 – **MarkAndBackUpLog**: Backs up the BizTalk Server database logs</span></span>

-   <span data-ttu-id="f70b1-110">步驟 4 –**清除備份歷程記錄**： 選擇 備份歷程記錄保留的時限</span><span class="sxs-lookup"><span data-stu-id="f70b1-110">Step 4 – **Clear Backup History**: Choose how long the backup history is kept</span></span>

<span data-ttu-id="f70b1-111">若要設定這項作業，您將需要：</span><span class="sxs-lookup"><span data-stu-id="f70b1-111">To configure this job, you'll need to:</span></span>  
  
-   <span data-ttu-id="f70b1-112">識別主要和目的地 SQL 伺服器和其他備份選項</span><span class="sxs-lookup"><span data-stu-id="f70b1-112">Identify the primary and destination SQL Servers and other backup options</span></span>
  
-   <span data-ttu-id="f70b1-113">選擇 Windows 使用者帳戶來備份資料庫並建立這個帳戶的 SQL Server 登入</span><span class="sxs-lookup"><span data-stu-id="f70b1-113">Choose a Windows user account to back up your databases and create a SQL Server login for this account</span></span>
  
-   <span data-ttu-id="f70b1-114">將 SQL Server 登入對應至 BizTalk Server 資料庫中的 BTS_BACKUP_USERS 資料庫角色</span><span class="sxs-lookup"><span data-stu-id="f70b1-114">Map SQL Server logins to the BTS_BACKUP_USERS database role in the BizTalk Server databases</span></span>
  
-   <span data-ttu-id="f70b1-115">確定所有節點上的 MSDTC 服務都在作用中。</span><span class="sxs-lookup"><span data-stu-id="f70b1-115">Ensure MSDTC service is active on all nodes.</span></span> <span data-ttu-id="f70b1-116">否則，請新增來源節點與目的節點之間連結的伺服器失敗</span><span class="sxs-lookup"><span data-stu-id="f70b1-116">Else, adding a linked server between the source node and the destination node fails</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="f70b1-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="f70b1-117">Before you begin</span></span>  
  
-   <span data-ttu-id="f70b1-118">某些組態和備份作業需要 sysadmin SQL Server 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="f70b1-118">Certain configuration and backup operations require membership in the sysadmin SQL Server role.</span></span> <span data-ttu-id="f70b1-119">若要備份您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，您必須登入主要伺服器是 SQL Server sysadmin 伺服器角色的成員的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f70b1-119">To back up your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must be signed in the primary server with an account that is a member of the SQL Server sysadmin Server role.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f70b1-120">組態會加入 BTS_BACKUP_USERS 資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="f70b1-120"> configuration adds the BTS_BACKUP_USERS database role.</span></span> <span data-ttu-id="f70b1-121">您用來備份資料庫的使用者帳戶不需要可能包含在備份中，除了主要伺服器的所有 SQL 伺服器上的系統管理員 （sysadmin SQL Server 角色） 權限。</span><span class="sxs-lookup"><span data-stu-id="f70b1-121">The user account you use to back up your databases does not require System Administrator (sysadmin SQL Server role) permissions on all the SQL Servers that may be involved in a backup, except for the primary server.</span></span>  
  
-   <span data-ttu-id="f70b1-122">決定哪些登入帳戶您用來執行您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="f70b1-122">Decide which sign in account you use to run your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backups.</span></span> <span data-ttu-id="f70b1-123">您可以使用本機帳戶，而且可以使用不止一個帳戶，但是針對此用途建立一個專用的 Windows 網域使用者帳戶，通常會更簡單也更安全。</span><span class="sxs-lookup"><span data-stu-id="f70b1-123">You can use a local account, and you can use more than one account, but it is generally simpler and more secure to create one dedicated Windows domain user account specifically for this purpose.</span></span> <span data-ttu-id="f70b1-124">您必須為此使用者設定 SQL Server 登入帳戶，而且此使用者必須對應到所有參與備份程序的主要 (來源) 或次要 (目的地) SQL Server 的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="f70b1-124">You must configure a SQL Server logon account for this user, and the user must be mapped to a SQL Server login for all of the SQL Servers that participate in the backup process, either as primary (source) or secondary (destination) servers.</span></span> <span data-ttu-id="f70b1-125">將此使用者指派給 BizTalk BTS_BACKUP_USERS 資料庫角色，每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="f70b1-125">Assign this user to the BizTalk BTS_BACKUP_USERS database role for each of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases you back up.</span></span>  
  
-   <span data-ttu-id="f70b1-126">備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 作業不會刪除過期的備份檔案，所以您必須手動管理這些備份檔案以回收磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="f70b1-126">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job does not delete outdated backup files, so you need to manually manage those backup files to conserve disk space.</span></span> <span data-ttu-id="f70b1-127">在為資料庫建立新的完整備份後，您應該將過期的備份檔案移動到封存儲存裝置以回收主要磁碟上的空間。</span><span class="sxs-lookup"><span data-stu-id="f70b1-127">After you have created a new full backup of your databases, you should move the outdated backup files onto an archival storage device to reclaim space on the primary disk.</span></span> <span data-ttu-id="f70b1-128">請參閱[SSIS 封裝](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/)管理這些檔案。</span><span class="sxs-lookup"><span data-stu-id="f70b1-128">See the [SSIS packages](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/) to manage these files.</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f70b1-129">不會寫入追蹤資料直接 BizTalk 追蹤資料庫;它會快取 MessageBox 資料庫中的資料而然後將它移到 BizTalk 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="f70b1-129"> does not write tracking data directly to the BizTalk Tracking database; rather it caches the data in the MessageBox database, and then moves it to the BizTalk Tracking database.</span></span> <span data-ttu-id="f70b1-130">如果發生 MessageBox 資料遺失，可能會遺失部分追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="f70b1-130">If MessageBox data loss occurs, some tracking data may also be lost.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f70b1-131">必要條件</span><span class="sxs-lookup"><span data-stu-id="f70b1-131">Prerequisites</span></span>  
* <span data-ttu-id="f70b1-132">使用屬於 sysadmin SQL Server 角色的成員帳戶的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="f70b1-132">Sign in to SQL Server using an account that is a member of the sysadmin SQL Server role.</span></span>  
  
* <span data-ttu-id="f70b1-133">您必須將 SQL Server Agent 服務設定成以網域帳戶執行 (雖然可以使用本機帳戶，但建議採用此方式)，並為每個 SQL Server 執行個體上設定一個對應的使用者登入。</span><span class="sxs-lookup"><span data-stu-id="f70b1-133">Configure the SQL Server Agent service to run under a domain account (recommended, although local accounts can be used), with a mapped user login on each instance of SQL Server.</span></span>  
  
## <a name="configure-the-job"></a><span data-ttu-id="f70b1-134">設定工作</span><span class="sxs-lookup"><span data-stu-id="f70b1-134">Configure the job</span></span>  
  
1.  <span data-ttu-id="f70b1-135">在裝載 BizTalk 管理資料庫的 SQL Server 上開啟**SQL Server Management Studio**，並連接到您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f70b1-135">On the SQL Server that hosts the BizTalk Management database, open **SQL Server Management Studio**, and connect to your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="f70b1-136">展開 [SQL Server Agent] ，再展開 [作業] 。</span><span class="sxs-lookup"><span data-stu-id="f70b1-136">Expand **SQL Server Agent**, and expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="f70b1-137">在 [備份 BizTalk Server (BizTalkMgmtDb)]  上按一下滑鼠右鍵，然後選取 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="f70b1-137">Right-click **Backup BizTalk Server (BizTalkMgmtDb)** and select **Properties**.</span></span> <span data-ttu-id="f70b1-138">在作業屬性中，選取 [步驟] 。</span><span class="sxs-lookup"><span data-stu-id="f70b1-138">In the job properties, select **Steps**.</span></span>  
  
4.  <span data-ttu-id="f70b1-139">選取**設定壓縮選項**逐步執行和選取**編輯**:</span><span class="sxs-lookup"><span data-stu-id="f70b1-139">Select the **Set Compression Option** step, and select **Edit**:</span></span>  

    <span data-ttu-id="f70b1-140">這個步驟就會呼叫`sp_SetBackupCompression`預存程序中設定的值上的 BizTalk 管理資料庫 (BizTalkMgmtDb)`adm_BackupSettings`資料表。</span><span class="sxs-lookup"><span data-stu-id="f70b1-140">This step calls the `sp_SetBackupCompression` stored procedure in the BizTalk management database (BizTalkMgmtDb) to set the value on the `adm_BackupSettings` table.</span></span> <span data-ttu-id="f70b1-141">預存程序有一個參數：  **@bCompression** 。</span><span class="sxs-lookup"><span data-stu-id="f70b1-141">The stored procedure has one parameter: **@bCompression**.</span></span> <span data-ttu-id="f70b1-142">根據預設，它設定為**0** （備份壓縮已關閉）。</span><span class="sxs-lookup"><span data-stu-id="f70b1-142">By default, it is set to **0** (backup compression is off).</span></span> <span data-ttu-id="f70b1-143">若要套用壓縮，將值變更為**1**:</span><span class="sxs-lookup"><span data-stu-id="f70b1-143">To apply compression, change the value to **1**:</span></span>  
  
    ```  
    exec [dbo].[sp_SetBackupCompression] @bCompression = 1 /*0 - Do not use Compression, 1 - Use Compression */  
    ```  
  
     <span data-ttu-id="f70b1-144">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="f70b1-144">Select **OK**.</span></span>  
  
5.  <span data-ttu-id="f70b1-145">選取**BackupFull**逐步執行和選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="f70b1-145">Select the **BackupFull** step, and select **Edit**.</span></span> <span data-ttu-id="f70b1-146">在**命令**方塊中，更新的參數值：</span><span class="sxs-lookup"><span data-stu-id="f70b1-146">In the **Command** box, update the parameter values:</span></span>  
  
    1. <span data-ttu-id="f70b1-147">**頻率**： 預設值是**d** （每日）; 這是建議的設定。</span><span class="sxs-lookup"><span data-stu-id="f70b1-147">**Frequency**: The default is **d** (daily); which is the recommended setting.</span></span> <span data-ttu-id="f70b1-148">其他值包括 **h** (每小時)、 **w** (每週)、 **m** (每月)、或 **y** (每年)。</span><span class="sxs-lookup"><span data-stu-id="f70b1-148">Other values include **h** (hourly), **w** (weekly), **m** (monthly), or **y** (yearly).</span></span>  
  
    2. <span data-ttu-id="f70b1-149">**名稱**：預設值是 **[BTS]**。</span><span class="sxs-lookup"><span data-stu-id="f70b1-149">**Name**: The default is **BTS**.</span></span> <span data-ttu-id="f70b1-150">這個名稱會用來做為備份檔案名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="f70b1-150">The name is used as part of the backup file name.</span></span>  
  
    3. <span data-ttu-id="f70b1-151">**備份檔案的位置**： 取代 '*\<目的地路徑 >*' 的電腦與您想要備份的目的地資料夾的完整路徑 （此路徑必須包含單引號） [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="f70b1-151">**Location of backup files**: Replace '*\<destination path>*' with the full path (the path must include the single quotes) to the computer and folder where you want to back up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  

        > [!IMPORTANT]
        >  - <span data-ttu-id="f70b1-152">如果您輸入的本機路徑，則您必須手動將所有檔案都複製到目的系統上相同的資料夾時備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業建立新檔案。</span><span class="sxs-lookup"><span data-stu-id="f70b1-152">If you enter a local path, then you have to manually copy all the files to the same folder on the destination system whenever the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job creates new files.</span></span>  
        >   
        >      <span data-ttu-id="f70b1-153">若要指定遠端路徑，請輸入 UNC 共用例如\\ \\  *\<ServerName >*\\*\<所 >* \\其中 *\<ServerName >*是您要檔案伺服器的名稱和*\<所 >*是共用磁碟機或資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="f70b1-153">To specify a remote path, enter a UNC share such as \\\\*\<ServerName>*\\*\<SharedDrive>*\\, where *\<ServerName>* is the name of the server where you want the files, and *\<SharedDrive>* is name of the shared drive or folder.</span></span>  
        >   
        >      <span data-ttu-id="f70b1-154">透過網路備份資料可能會因為網路問題而受限。</span><span class="sxs-lookup"><span data-stu-id="f70b1-154">Backing up data over a network is subject to any network issues.</span></span> <span data-ttu-id="f70b1-155">當使用遠端位置，驗證備份成功時備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業結束。</span><span class="sxs-lookup"><span data-stu-id="f70b1-155">When using a remote location, verify the backup succeeded when the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job finishes.</span></span>  
        > - <span data-ttu-id="f70b1-156">若要避免資料遺失，請將備份磁碟設定為資料庫資料與記錄磁碟以外的其他磁碟。</span><span class="sxs-lookup"><span data-stu-id="f70b1-156">To avoid potential data loss, configure the backup disk to be a different disk than the database data and log disks.</span></span> <span data-ttu-id="f70b1-157">此做法可確保您在資料或記錄磁碟故障時存取備份。</span><span class="sxs-lookup"><span data-stu-id="f70b1-157">This is necessary so you can access the backups if the data or log disk fails.</span></span>  

    4. <span data-ttu-id="f70b1-158">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f70b1-158">Optional.</span></span> <span data-ttu-id="f70b1-159">**部分備份失敗之後強制完整備份**(@ForceFullBackupAfterPartialSetFailure): 預設值是**0**。</span><span class="sxs-lookup"><span data-stu-id="f70b1-159">**Force full backup after partial backup failures** (@ForceFullBackupAfterPartialSetFailure): The default is **0**.</span></span> <span data-ttu-id="f70b1-160">如果記錄備份失敗時，到達下一個完整備份頻率間隔之前，會不執行任何完整備份。</span><span class="sxs-lookup"><span data-stu-id="f70b1-160">If a log backup fails, no full backups are ran until the next full backup frequency interval is reached.</span></span> <span data-ttu-id="f70b1-161">取代為**1**如果您想要的完整備份執行記錄檔備份失敗時。</span><span class="sxs-lookup"><span data-stu-id="f70b1-161">Replace with **1** if you want a full backup ran whenever a log backup failure occurs.</span></span>
    
    5. <span data-ttu-id="f70b1-162">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f70b1-162">Optional.</span></span> <span data-ttu-id="f70b1-163">**若要執行備份程序的本地小時時間**: 預設值是 NULL。</span><span class="sxs-lookup"><span data-stu-id="f70b1-163">**Local time hour for the backup process to run**: The default is NULL.</span></span> <span data-ttu-id="f70b1-164">備份作業不是相關聯的時區時間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，並會在午夜 UTC 時間 (0000)。</span><span class="sxs-lookup"><span data-stu-id="f70b1-164">The backup job is not associated with the time zone of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, and runs at midnight UTC time (0000).</span></span> <span data-ttu-id="f70b1-165">如果您想要備份的時區中的特定時間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上，輸入一個整數值 0 （午夜） 到 23 （晚上 11 點） 為本地小時時間**BackupHour**參數。</span><span class="sxs-lookup"><span data-stu-id="f70b1-165">If you want to backup at a specific hour in the time zone of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, enter an integer value from 0 (midnight) to 23 (11 PM) as the local time hour for the **BackupHour** parameter.</span></span> 

    6. <span data-ttu-id="f70b1-166">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f70b1-166">Optional.</span></span> <span data-ttu-id="f70b1-167">**使用本地時間**(@UseLocalTime): 會告知使用本地時間的程序。</span><span class="sxs-lookup"><span data-stu-id="f70b1-167">**Use local time** (@UseLocalTime): Tells the procedure to use local time.</span></span> <span data-ttu-id="f70b1-168">預設值為 0，而且會使用目前的 UTC 時間 – getutcdate （） – 2007年-05-04 01:34:11.933。</span><span class="sxs-lookup"><span data-stu-id="f70b1-168">The default value is 0, and uses current UTC time – GETUTCDATE() – 2007-05-04 01:34:11.933.</span></span> <span data-ttu-id="f70b1-169">如果設為 1，然後它會使用當地時間 – getdate （） – 2007年-05-03 18:34:11.933</span><span class="sxs-lookup"><span data-stu-id="f70b1-169">If set to 1, then it uses local time – GETDATE() – 2007-05-03 18:34:11.933</span></span>
  
    <span data-ttu-id="f70b1-170">在下列範例中，會建立上午 2 執行，每日備份，並將其儲存在 m:\ 磁碟機中：</span><span class="sxs-lookup"><span data-stu-id="f70b1-170">In the following example, daily backups are created at 2am, and stored in the m:\ drive:</span></span>  
  
    ```  
    exec [dbo].[sp_BackupAllFull_Schedule]   
    'd' /* Frequency */,   
    'BTS' /* Name */,   
    'm:\BizTalkBackups' /* location of backup files */,   
    0 /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */,   
    '2' /* local time hour for the backup process to run */  
    ```  
  
     <span data-ttu-id="f70b1-171">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="f70b1-171">Select **OK**.</span></span>  
  
6.  <span data-ttu-id="f70b1-172">選取**MarkAndBackupLog**逐步執行和選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="f70b1-172">Select the **MarkAndBackupLog** step, and select **Edit**.</span></span> <span data-ttu-id="f70b1-173">在**命令**方塊中，更新的參數值：</span><span class="sxs-lookup"><span data-stu-id="f70b1-173">In the **Command** box, update the parameter values:</span></span>  
  
    1.  <span data-ttu-id="f70b1-174">**@MarkName**： 這是備份檔案的命名慣例： <Server Name>  _<Database Name> **_記錄_**< 記錄標示名稱 >_<Timestamp></span><span class="sxs-lookup"><span data-stu-id="f70b1-174">**@MarkName**: This is part of the naming convention for backup files: <Server Name>_<Database Name>**_Log_**< Log Mark Name >_<Timestamp></span></span>  
    
    2.  <span data-ttu-id="f70b1-175">**@BackupPath**： 完整目的地路徑 （包含單引號） 的電腦與您想要用來儲存的資料夾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f70b1-175">**@BackupPath**: Full destination path (including single quotes) to the computer and folder where you want to store the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database logs.</span></span> <span data-ttu-id="f70b1-176">*\<目的地路徑 >*可以是本機或另一部伺服器的 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="f70b1-176">The *\<destination path>* may be local or a UNC path to another server.</span></span>  
  
     <span data-ttu-id="f70b1-177">MarkAndBackupLog 步驟會標記要備份的記錄檔，然後加以備份。</span><span class="sxs-lookup"><span data-stu-id="f70b1-177">The MarkAndBackupLog step marks the logs for backup, and then backs them up.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f70b1-178">若要避免**潛在資料遺失**和**效能改進**、 *\<目的地路徑 >*應該設定為不同的電腦或硬碟機，不同於並用來儲存原始的資料庫記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f70b1-178">To avoid **potential data loss** and for **performance improvement**, the *\<destination path>* should be set to a different computer, or hard drive, different from what is used to store the original database logs.</span></span>  
  
     <span data-ttu-id="f70b1-179">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="f70b1-179">Select **OK**.</span></span>  
  
7.  <span data-ttu-id="f70b1-180">選取**清除備份歷程記錄**逐步執行和選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="f70b1-180">Select the **Clear Backup History** step, and select **Edit**.</span></span> <span data-ttu-id="f70b1-181">在**命令**方塊中，更新的參數值：</span><span class="sxs-lookup"><span data-stu-id="f70b1-181">In the **Command** box, update the parameter values:</span></span>  
  
    1.  <span data-ttu-id="f70b1-182">**@DaysToKeep**： 預設值是**14 天**。</span><span class="sxs-lookup"><span data-stu-id="f70b1-182">**@DaysToKeep**: Default value is **14 days**.</span></span> <span data-ttu-id="f70b1-183">決定要備份的記錄會保留`Adm_BackupHistory`資料表。</span><span class="sxs-lookup"><span data-stu-id="f70b1-183">Determines how long the backup history is kept in the `Adm_BackupHistory` table.</span></span> <span data-ttu-id="f70b1-184">定期清除備份歷程記錄可協助維護`Adm_BackupHistory`資料表，以適當的大小。</span><span class="sxs-lookup"><span data-stu-id="f70b1-184">Periodically clearing the backup history helps maintain the `Adm_BackupHistory` table to an appropriate size.</span></span> 
    
    2.  <span data-ttu-id="f70b1-185">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f70b1-185">Optional.</span></span> <span data-ttu-id="f70b1-186">**@UseLocalTime**： 會告知使用本地時間的程序。</span><span class="sxs-lookup"><span data-stu-id="f70b1-186">**@UseLocalTime**: Tells the procedure to use local time.</span></span> <span data-ttu-id="f70b1-187">預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="f70b1-187">The default value is 0.</span></span> <span data-ttu-id="f70b1-188">它會使用目前的 UTC 時間 – getutcdate （） – 2007年-05-04 01:34:11.933。</span><span class="sxs-lookup"><span data-stu-id="f70b1-188">It uses current UTC time – GETUTCDATE() – 2007-05-04 01:34:11.933.</span></span> <span data-ttu-id="f70b1-189">如果設為 1，然後它會使用當地時間 – getdate （） – 2007年-05-03 18:34:11.933</span><span class="sxs-lookup"><span data-stu-id="f70b1-189">If set to 1, then it uses local time – GETDATE() – 2007-05-03 18:34:11.933</span></span>
  
    ```  
    exec [dbo].[sp_DeleteBackupHistory] @DaysToKeep=14, @UseLocalTime =1 
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f70b1-190">此步驟**不**刪除備份檔案的目的地路徑。</span><span class="sxs-lookup"><span data-stu-id="f70b1-190">This step **does not** delete backup files from the destination path.</span></span>  
    
     <span data-ttu-id="f70b1-191">選取 [確定]  ，然後關閉所有的屬性視窗。</span><span class="sxs-lookup"><span data-stu-id="f70b1-191">Select **OK** and close all property windows.</span></span>  
  
8.  <span data-ttu-id="f70b1-192">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f70b1-192">Optional.</span></span> <span data-ttu-id="f70b1-193">變更備份排程。</span><span class="sxs-lookup"><span data-stu-id="f70b1-193">Change the backup schedule.</span></span> <span data-ttu-id="f70b1-194">請參閱[如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md)。</span><span class="sxs-lookup"><span data-stu-id="f70b1-194">See [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f70b1-195">「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業會在您第一次設定時執行。</span><span class="sxs-lookup"><span data-stu-id="f70b1-195">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs the first time you configure it.</span></span> <span data-ttu-id="f70b1-196">根據預設，在後續執行中，備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業完成的完整備份一天一次，並完成每隔 15 分鐘的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="f70b1-196">By default, on subsequent runs, the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job completes a full backup once a day, and completes log backups every 15 minutes.</span></span>  
  
9. <span data-ttu-id="f70b1-197">以滑鼠右鍵按一下**備份 BizTalk Server**作業，然後選取**啟用**。</span><span class="sxs-lookup"><span data-stu-id="f70b1-197">Right-click the **Backup BizTalk Server** job, and select **Enable**.</span></span> <span data-ttu-id="f70b1-198">狀態應該變更為 **成功**。</span><span class="sxs-lookup"><span data-stu-id="f70b1-198">The status should change to **Success**.</span></span>  
  
## <a name="spforcefullbackup-stored-procedure"></a><span data-ttu-id="f70b1-199">sp_ForceFullBackup 預存程序</span><span class="sxs-lookup"><span data-stu-id="f70b1-199">sp_ForceFullBackup stored procedure</span></span>  
  
<span data-ttu-id="f70b1-200">**Sp_ForceFullBackup**預存程序中的**BizTalkMgmtDb**資料庫可以用來執行特定的資料和記錄檔的完整備份。</span><span class="sxs-lookup"><span data-stu-id="f70b1-200">The **sp_ForceFullBackup** stored procedure in the **BizTalkMgmtDb** database can be used to run an ad-hoc full backup of the data and log files.</span></span> <span data-ttu-id="f70b1-201">此預存程序會以值 1 更新 adm_ForceFullBackup 資料表。</span><span class="sxs-lookup"><span data-stu-id="f70b1-201">The stored procedure updates the adm_ForceFullBackup table with a value 1.</span></span> <span data-ttu-id="f70b1-202">在下一次備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行作業時，會建立完整資料庫備份組。</span><span class="sxs-lookup"><span data-stu-id="f70b1-202">The next time the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job is ran, a full database backup set is created.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f70b1-203">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f70b1-203">Next Steps</span></span>  
 <span data-ttu-id="f70b1-204">[如何設定記錄傳送目的地系統](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span><span class="sxs-lookup"><span data-stu-id="f70b1-204">[How to Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span></span>  
 [<span data-ttu-id="f70b1-205">如何排程 「 備份 BizTalk Server 」 工作</span><span class="sxs-lookup"><span data-stu-id="f70b1-205">How to Schedule the Backup BizTalk Server Job</span></span>](../core/how-to-schedule-the-backup-biztalk-server-job.md)
