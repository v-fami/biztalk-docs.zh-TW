---
title: "如何設定 「 備份 BizTalk Server 」 工作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, backing up
- backing up, Tracking database
- backing up, user accounts
- backing up, MessageBox database
- databases, backing up
- MessageBox database, backing up
- backing up, databases
- backing up, prerequisites
- configuring, backup jobs
- backing up, warnings
- backing up, backup jobs
- user accounts, backing up
- backing up, configuring
ms.assetid: 026622c9-fcb4-4db0-af48-1379feb30372
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 488e76c3d29c58107e85ad58ed4fad50de671315
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-backup-biztalk-server-job"></a><span data-ttu-id="29b21-102">如何設定備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="29b21-102">How to Configure the Backup BizTalk Server Job</span></span>
<span data-ttu-id="29b21-103">本主題列出設定「備份 BizTalk Server」作業所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="29b21-103">This topic lists the steps necessary to configure the Backup BizTalk Server job.</span></span>  
  
 <span data-ttu-id="29b21-104">您必須先設定「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業，然後才能備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="29b21-104">You must configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job before you can back up [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="29b21-105">若要設定備份，必須執行下列大部分或所有的工作：</span><span class="sxs-lookup"><span data-stu-id="29b21-105">To configure the backup, you need to perform most or all of the following tasks:</span></span>  
  
-   <span data-ttu-id="29b21-106">編輯 SQL Server Agent 的 **備份 BizTalk Server (BizTalkMgmtDb)** 作業，以指定主要與目的地 SQL Server 及其他備份選項。</span><span class="sxs-lookup"><span data-stu-id="29b21-106">Edit the SQL Server Agent **Backup BizTalk Server (BizTalkMgmtDb)** job to identify the primary and destination SQL Servers and other backup options.</span></span>  
  
-   <span data-ttu-id="29b21-107">選擇 Windows 使用者帳戶，以備份資料庫，以及建立此帳戶的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="29b21-107">Choose a Windows user account to back up your databases and create a SQL Server login for this account.</span></span>  
  
-   <span data-ttu-id="29b21-108">將 SQL Server 登入對應到 BizTalk Server 資料庫中的 BTS_BACKUP_USERS 資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="29b21-108">Map SQL Server logins to the BTS_BACKUP_USERS database role in the BizTalk Server databases.</span></span>  
  
-   <span data-ttu-id="29b21-109">確定所有節點上的 MSDTC 服務都在作用中。</span><span class="sxs-lookup"><span data-stu-id="29b21-109">Ensure MSDTC service is active on all nodes.</span></span> <span data-ttu-id="29b21-110">否則，在來源節點與目的節點之間新增連結的伺服器將會失敗。</span><span class="sxs-lookup"><span data-stu-id="29b21-110">Else, adding a linked server between the source node and the destination node fails.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="29b21-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="29b21-111">Before you begin</span></span>  
  
-   <span data-ttu-id="29b21-112">某些組態和備份作業 (例如這一個) 需要有 sysadmin SQL Server 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="29b21-112">Certain configuration and backup operations such as this one require membership in the sysadmin SQL Server role.</span></span> <span data-ttu-id="29b21-113">若要備份您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，您必須在主要伺服器與主要伺服器上的 SQL Server sysadmin 伺服器角色的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="29b21-113">To back up your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must be logged on at the primary server with an account that is a member of the SQL Server sysadmin Server role on the primary server.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="29b21-114">組態會加入名為 BTS_BACKUP_USERS，以便您用來備份您的資料庫使用者帳戶不需要的所有可能包含在備份中，除了 SQL Server 上的系統管理員 （sysadmin SQL Server 角色） 權限的資料庫角色主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="29b21-114"> configuration adds a database role named BTS_BACKUP_USERS so that the user account you use to back up your databases does not require System Administrator (sysadmin SQL Server role) permissions on all of the SQL Servers that may be involved in a backup, except for the primary server.</span></span>  
  
-   <span data-ttu-id="29b21-115">您需要決定哪一個登入帳戶，您用來執行您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="29b21-115">You need to decide which login account you use to perform your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backups.</span></span> <span data-ttu-id="29b21-116">您可以使用本機帳戶，而且可以使用不止一個帳戶，但是針對此用途建立一個專用的 Windows 網域使用者帳戶，通常會更簡單也更安全。</span><span class="sxs-lookup"><span data-stu-id="29b21-116">You can use a local account, and you can use more than one account, but it is generally simpler and more secure to create one dedicated Windows domain user account specifically for this purpose.</span></span> <span data-ttu-id="29b21-117">您必須為此使用者設定 SQL Server 登入帳戶，而且此使用者必須對應到所有參與備份程序的主要 (來源) 或次要 (目的地) SQL Server 的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="29b21-117">You must configure a SQL Server logon account for this user, and the user must be mapped to a SQL Server login for all of the SQL Servers that participate in the backup process, either as primary (source) or secondary (destination) servers.</span></span> <span data-ttu-id="29b21-118">將此使用者指派給 BizTalk BTS_BACKUP_USERS 資料庫角色，每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="29b21-118">Assign this user to the BizTalk BTS_BACKUP_USERS database role for each of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases you back up.</span></span>  
  
-   <span data-ttu-id="29b21-119">備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 作業不會刪除過期的備份檔案，所以您必須手動管理這些備份檔案以回收磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="29b21-119">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job does not delete outdated backup files, so you need to manually manage those backup files to conserve disk space.</span></span> <span data-ttu-id="29b21-120">在為資料庫建立新的完整備份後，您應該將過期的備份檔案移動到封存儲存裝置以回收主要磁碟上的空間。</span><span class="sxs-lookup"><span data-stu-id="29b21-120">After you have created a new full backup of your databases, you should move the outdated backup files onto an archival storage device to reclaim space on the primary disk.</span></span> <span data-ttu-id="29b21-121">「 BizTalk 帳單 」 有可下載[SSIS 封裝](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/)管理這些檔案。</span><span class="sxs-lookup"><span data-stu-id="29b21-121">"BizTalk Bill" has downloadable [SSIS packages](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/) to manage these files.</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="29b21-122"> 不會將追蹤資料直接寫入 BizTalk 追蹤資料庫；它會快取 MessageBox 資料庫中的資料，然後將它移到 BizTalk 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="29b21-122"> does not write tracking data directly to the BizTalk Tracking database; rather it caches the data in the MessageBox database and then moves it to the BizTalk Tracking database.</span></span> <span data-ttu-id="29b21-123">如果發生 MessageBox 資料遺失，可能會遺失部分追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="29b21-123">If MessageBox data loss occurs, some tracking data may also be lost.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="29b21-124">必要條件</span><span class="sxs-lookup"><span data-stu-id="29b21-124">Prerequisites</span></span>  
* <span data-ttu-id="29b21-125">使用屬於 sysadmin SQL Server 角色的成員帳戶的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="29b21-125">Sign in to SQL Server using an account that is a member of the sysadmin SQL Server role.</span></span>  
  
* <span data-ttu-id="29b21-126">您必須將 SQL Server Agent 服務設定成以網域帳戶執行 (雖然可以使用本機帳戶，但建議採用此方式)，並為每個 SQL Server 執行個體上設定一個對應的使用者登入。</span><span class="sxs-lookup"><span data-stu-id="29b21-126">Configure the SQL Server Agent service to run under a domain account (recommended, although local accounts can be used), with a mapped user login on each instance of SQL Server.</span></span>  
  
## <a name="configure-the-backup-biztalk-server-job"></a><span data-ttu-id="29b21-127">設定備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="29b21-127">Configure the Backup BizTalk Server job</span></span>  
  
1.  <span data-ttu-id="29b21-128">在裝載 BizTalk 管理資料庫的 SQL Server 上開啟**SQL Server Management Studio**，並連接到您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="29b21-128">On the SQL Server that hosts the BizTalk Management database, open **SQL Server Management Studio**, and connect to your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="29b21-129">展開 [SQL Server Agent] ，再展開 [作業] 。</span><span class="sxs-lookup"><span data-stu-id="29b21-129">Expand **SQL Server Agent**, and expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="29b21-130">在 [備份 BizTalk Server (BizTalkMgmtDb)]  上按一下滑鼠右鍵，然後選取 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="29b21-130">Right-click **Backup BizTalk Server (BizTalkMgmtDb)** and select **Properties**.</span></span> <span data-ttu-id="29b21-131">在作業屬性中，選取 [步驟] 。</span><span class="sxs-lookup"><span data-stu-id="29b21-131">In the job properties, select **Steps**.</span></span>  
  
4.  <span data-ttu-id="29b21-132">選取 [設定壓縮選項]  步驟，再選取 [編輯] 。</span><span class="sxs-lookup"><span data-stu-id="29b21-132">Select the **Set Compression Option** step and select **Edit**.</span></span> <span data-ttu-id="29b21-133">在 [命令]  方塊中，將此值變更為 1：</span><span class="sxs-lookup"><span data-stu-id="29b21-133">In the **Command** box, change the value to 1:</span></span>  
  
    ```  
    exec [dbo].[sp_SetBackupCompression] @bCompression = 1 /*0 - Do not use Compression, 1 - Use Compression */  
    ```  
  
     <span data-ttu-id="29b21-134">選取 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="29b21-134">Select **OK**.</span></span>  
  
5.  <span data-ttu-id="29b21-135">選取 [BackupFull]  步驟，再選取 [編輯] 。</span><span class="sxs-lookup"><span data-stu-id="29b21-135">Select the **BackupFull** step and select **Edit**.</span></span> <span data-ttu-id="29b21-136">在 [命令]  方塊中編輯參數值：</span><span class="sxs-lookup"><span data-stu-id="29b21-136">In the **Command** box, edit the parameter values:</span></span>  
  
    1.  <span data-ttu-id="29b21-137">**頻率**：預設值為 **d** (每日)。</span><span class="sxs-lookup"><span data-stu-id="29b21-137">**Frequency**: The default is **d** (daily).</span></span> <span data-ttu-id="29b21-138">此為建議設定值。</span><span class="sxs-lookup"><span data-stu-id="29b21-138">This is the recommended setting.</span></span> <span data-ttu-id="29b21-139">其他值包括 **h** (每小時)、 **w** (每週)、 **m** (每月)、或 **y** (每年)。</span><span class="sxs-lookup"><span data-stu-id="29b21-139">Other values include **h** (hourly), **w** (weekly), **m** (monthly), or **y** (yearly).</span></span>  
  
    2.  <span data-ttu-id="29b21-140">**名稱**：預設值是 **[BTS]**。</span><span class="sxs-lookup"><span data-stu-id="29b21-140">**Name**: The default is **BTS**.</span></span> <span data-ttu-id="29b21-141">這個名稱會用來做為備份檔案名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="29b21-141">The name is used as part of the backup file name.</span></span>  
  
    3.  <span data-ttu-id="29b21-142">**備份檔案的位置**： 取代 '*\<目的地路徑 >*' 的電腦與您想要備份的目的地資料夾的完整路徑 （此路徑必須包含單引號） [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="29b21-142">**Location of backup files**: Replace '*\<destination path>*' with the full path (the path must include the single quotes) to the computer and folder where you want to back up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
        > [!IMPORTANT]
        >  -   <span data-ttu-id="29b21-143">如果您指定本機路徑，則每當「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業建立新檔案時，您都必須將所有檔案手動複製到目的系統上的相同資料夾。</span><span class="sxs-lookup"><span data-stu-id="29b21-143">If you specify a local path, then you have to manually copy all the files to the same folder on the destination system whenever the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job creates new files.</span></span>  
        >   
        >      <span data-ttu-id="29b21-144">若要指定遠端路徑，請輸入 UNC 共用例如\\ \\  *\<ServerName >*\\*\<所 >* \\其中 *\<ServerName >*是您要檔案伺服器的名稱和*\<所 >*是共用磁碟機或資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="29b21-144">To specify a remote path, enter a UNC share such as \\\\*\<ServerName>*\\*\<SharedDrive>*\\, where *\<ServerName>* is the name of the server where you want the files, and *\<SharedDrive>* is name of the shared drive or folder.</span></span>  
        >   
        >      <span data-ttu-id="29b21-145">透過網路備份資料可能會因為網路問題而受限。</span><span class="sxs-lookup"><span data-stu-id="29b21-145">Backing up data over a network is subject to any network issues.</span></span> <span data-ttu-id="29b21-146">當使用遠端位置，驗證備份成功時備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業結束。</span><span class="sxs-lookup"><span data-stu-id="29b21-146">When using a remote location, verify the backup succeeded when the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job finishes.</span></span>  
        > -   <span data-ttu-id="29b21-147">若要避免資料遺失，請將備份磁碟設定為資料庫資料與記錄磁碟以外的其他磁碟。</span><span class="sxs-lookup"><span data-stu-id="29b21-147">To avoid potential data loss, configure the backup disk to be a different disk than the database data and log disks.</span></span> <span data-ttu-id="29b21-148">此做法可確保您在資料或記錄磁碟故障時存取備份。</span><span class="sxs-lookup"><span data-stu-id="29b21-148">This is necessary so you can access the backups if the data or log disk fails.</span></span>  
  
    4.  <span data-ttu-id="29b21-149">**在部分備份失敗之後強制完整備份**：沒有指定時，預設值為 **0** ，這表示如果記錄檔備份失敗，在到達下一個完整備份頻率間隔之前，不會進行任何完整備份。</span><span class="sxs-lookup"><span data-stu-id="29b21-149">**Force full backup after partial backup failures**: The default is **0** when not specified, which means that if a log backup fails, no full backups are done until the next full backup frequency interval is reached.</span></span> <span data-ttu-id="29b21-150">如果您想要在每次發生記錄檔備份失敗時進行完整備份，請取代成 **1** 。</span><span class="sxs-lookup"><span data-stu-id="29b21-150">Replace with **1** if you want a full backup to be made whenever a log backup failure occurs.</span></span>  
  
    5.  <span data-ttu-id="29b21-151">**若要執行備份程序的本地小時時間**: 預設值是 NULL 時未指定，這表示備份作業不是與關聯的時區時間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，因此就會在午夜 UTC 時間 (0000)。</span><span class="sxs-lookup"><span data-stu-id="29b21-151">**Local time hour for the backup process to run**: The default is NULL when not specified, which means that backup job is not associated with the time zone of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer and therefore runs at midnight UTC time (0000).</span></span> <span data-ttu-id="29b21-152">如果您想要備份至執行中的時區時間的特定小時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上，輸入一個整數值 0 （午夜） 到 23 （晚上 11 點） 為本地小時時間**BackupHour**參數。</span><span class="sxs-lookup"><span data-stu-id="29b21-152">If you want to backup to run at a particular hour in the time zone of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, enter an integer value from 0 (midnight) to 23 (11 PM) as the local time hour for the **BackupHour** parameter.</span></span>  
  
     <span data-ttu-id="29b21-153">在下列範例中，每日備份會在凌晨 2 時建立，並儲存在 m:\ 磁碟機中：</span><span class="sxs-lookup"><span data-stu-id="29b21-153">In the following example, daily backups are created at 2am and stored in the m:\ drive:</span></span>  
  
    ```  
    exec [dbo].[sp_BackupAllFull_Schedule]   
    'd' /* Frequency */,   
    'BTS' /* Name */,   
    'm:\BizTalkBackups' /* location of backup files */,   
    0 /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */,   
    '2' /* local time hour for the backup process to run */  
    ```  
  
     <span data-ttu-id="29b21-154">選取 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="29b21-154">Select **OK**.</span></span>  
  
6.  <span data-ttu-id="29b21-155">選取 **MarkAndBackupLog** 步驟，再選取 [編輯] 。</span><span class="sxs-lookup"><span data-stu-id="29b21-155">Select the **MarkAndBackupLog** step and select **Edit**.</span></span> <span data-ttu-id="29b21-156">在**命令**方塊中，取代**'***\<目的地路徑 >***'**的完整路徑 （包含單引號）電腦和您要儲存的資料夾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫記錄檔。</span><span class="sxs-lookup"><span data-stu-id="29b21-156">In the **Command** box, replace **'***\<destination path>***'** with the full path (including single quotes) to the computer and folder where you want to store the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database logs.</span></span> <span data-ttu-id="29b21-157">*\<目的地路徑 >*可以是本機或另一部伺服器的 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="29b21-157">The *\<destination path>* may be local or a UNC path to another server.</span></span>  
  
     <span data-ttu-id="29b21-158">MarkAndBackupLog 步驟會標記要備份的記錄檔，然後加以備份。</span><span class="sxs-lookup"><span data-stu-id="29b21-158">The MarkAndBackupLog step marks the logs for backup, and then backs them up.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="29b21-159">若要避免資料遺失， *\<目的地路徑 >*應該指定的電腦不同的電腦與原始資料庫記錄檔來儲存資料庫記錄檔。</span><span class="sxs-lookup"><span data-stu-id="29b21-159">To avoid potential data loss, the *\<destination path>* should specify a computer to store the database logs that is different from the computer with the original database logs.</span></span>  
  
     <span data-ttu-id="29b21-160">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="29b21-160">Select **OK**.</span></span>  
  
7.  <span data-ttu-id="29b21-161">選取 **清除備份歷程記錄** 步驟，再選取 [編輯] 。</span><span class="sxs-lookup"><span data-stu-id="29b21-161">Select the **Clear Backup History** step and select **Edit**.</span></span> <span data-ttu-id="29b21-162">在**命令**方塊中，變更**DaysToKeep =***\<數字 >*您想要保留備份歷程記錄的天數：</span><span class="sxs-lookup"><span data-stu-id="29b21-162">In the **Command** box, change **DaysToKeep=***\<number>* to the number of days you want to keep the backup history:</span></span>  
  
    ```  
    exec [dbo].[sp_DeleteBackupHistory] @DaysToKeep=14  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="29b21-163">**DaysToKeep** 參數指定在 Adm_BackupHistory 資料表中保存備份歷程記錄的時間。</span><span class="sxs-lookup"><span data-stu-id="29b21-163">The **DaysToKeep** parameter specifies how long the backup history is kept in the Adm_BackupHistory table.</span></span> <span data-ttu-id="29b21-164">定期清除備份歷程記錄，有助於保持 Adm_BackupHistory 資料表的適當大小。</span><span class="sxs-lookup"><span data-stu-id="29b21-164">Periodically clearing the backup history helps to maintain the Adm_BackupHistory table at an appropriate size.</span></span> <span data-ttu-id="29b21-165">**DaysToKeep** 參數的預設值為 14 天。</span><span class="sxs-lookup"><span data-stu-id="29b21-165">The default value for the **DaysToKeep** parameter is 14 days.</span></span>  
  
     <span data-ttu-id="29b21-166">選取 [確定]  ，然後關閉所有的屬性視窗。</span><span class="sxs-lookup"><span data-stu-id="29b21-166">Select **OK** and close all property windows.</span></span>  
  
8.  <span data-ttu-id="29b21-167">選擇性。</span><span class="sxs-lookup"><span data-stu-id="29b21-167">Optional.</span></span> <span data-ttu-id="29b21-168">變更備份排程。</span><span class="sxs-lookup"><span data-stu-id="29b21-168">Change the backup schedule.</span></span> <span data-ttu-id="29b21-169">請參閱[如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md)。</span><span class="sxs-lookup"><span data-stu-id="29b21-169">See [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29b21-170">「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業會在您第一次設定時執行。</span><span class="sxs-lookup"><span data-stu-id="29b21-170">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs the first time you configure it.</span></span> <span data-ttu-id="29b21-171">在後續的執行中，「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業依預設會每天執行一次完整備份，並且每 15 分鐘執行一次記錄備份。</span><span class="sxs-lookup"><span data-stu-id="29b21-171">By default, on subsequent runs, the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job performs a full backup once a day and performs log backups every 15 minutes.</span></span>  
  
9. <span data-ttu-id="29b21-172">在 **備份 BizTalk Server** 作業上按一下滑鼠右鍵，然後選取 [啟用] 。</span><span class="sxs-lookup"><span data-stu-id="29b21-172">Right-click the **Backup BizTalk Server** job and select **Enable**.</span></span> <span data-ttu-id="29b21-173">狀態應該變更為 **成功**。</span><span class="sxs-lookup"><span data-stu-id="29b21-173">The status should change to **Success**.</span></span>  
  
## <a name="spforcefullbackup-stored-procedure"></a><span data-ttu-id="29b21-174">sp_ForceFullBackup 預存程序</span><span class="sxs-lookup"><span data-stu-id="29b21-174">sp_ForceFullBackup stored procedure</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29b21-175">BizTalkMgmtDb 資料庫中的 sp_ForceFullBackup 預存程序可用於協助執行資料與記錄檔的特定完整備份。</span><span class="sxs-lookup"><span data-stu-id="29b21-175">The sp_ForceFullBackup stored procedure in the BizTalkMgmtDb database can be used to help perform an ad-hoc full backup of the data and log files.</span></span> <span data-ttu-id="29b21-176">此預存程序會以值 1 更新 adm_ForceFullBackup 資料表。</span><span class="sxs-lookup"><span data-stu-id="29b21-176">The stored procedure updates the adm_ForceFullBackup table with a value 1.</span></span> <span data-ttu-id="29b21-177">在下一次備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行作業時，會建立完整資料庫備份組。</span><span class="sxs-lookup"><span data-stu-id="29b21-177">The next time the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job is ran, a full database backup set is created.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="29b21-178">後續步驟</span><span class="sxs-lookup"><span data-stu-id="29b21-178">Next Steps</span></span>  
 [<span data-ttu-id="29b21-179">如何設定記錄傳送目的地系統</span><span class="sxs-lookup"><span data-stu-id="29b21-179">How to Configure the Destination System for Log Shipping</span></span>](../core/how-to-configure-the-destination-system-for-log-shipping.md)  
  
## <a name="see-also"></a><span data-ttu-id="29b21-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29b21-180">See Also</span></span>  
 [<span data-ttu-id="29b21-181">如何排程 「 備份 BizTalk Server 」 工作</span><span class="sxs-lookup"><span data-stu-id="29b21-181">How to Schedule the Backup BizTalk Server Job</span></span>](../core/how-to-schedule-the-backup-biztalk-server-job.md)