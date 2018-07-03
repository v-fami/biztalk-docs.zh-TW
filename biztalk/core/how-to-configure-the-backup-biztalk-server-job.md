---
title: 設定 「 備份 BizTalk Server 」 工作 |Microsoft Docs
description: ''
ms.custom: ''
ms.date: 11/22/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 026622c9-fcb4-4db0-af48-1379feb30372
caps.latest.revision: 42
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64a6222ffbabad54d8908a7d8da5517786d9a0cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981087"
---
# <a name="configure-the-backup-biztalk-server-job"></a><span data-ttu-id="eebbb-102">設定備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="eebbb-102">Configure the Backup BizTalk Server Job</span></span>
<span data-ttu-id="eebbb-103">安裝後，當您設定 BizTalk Server 時，設定備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]工作以備份您的資料。</span><span class="sxs-lookup"><span data-stu-id="eebbb-103">After you install and configure BizTalk Server, configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job to back up your data.</span></span> 

<span data-ttu-id="eebbb-104">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，您可以備份資料庫及記錄檔到 Azure blob 儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="eebbb-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, you can backup your databases and log files to an Azure blob storage account.</span></span> 


## <a name="overview"></a><span data-ttu-id="eebbb-105">概觀</span><span class="sxs-lookup"><span data-stu-id="eebbb-105">Overview</span></span>
<span data-ttu-id="eebbb-106">**備份 BizTalk Server (BizTalkMgmtDb)** 作業包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="eebbb-106">The **Backup BizTalk Server (BizTalkMgmtDb)** job includes the following steps:</span></span>

-   <span data-ttu-id="eebbb-107">步驟 1 –**集壓縮選項**： 啟用或停用壓縮備份期間</span><span class="sxs-lookup"><span data-stu-id="eebbb-107">Step 1 – **Set Compression Option**: Enable or disable compression during backup</span></span>

-   <span data-ttu-id="eebbb-108">步驟 2 – **BackupFull**： 執行完整資料庫備份 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="eebbb-108">Step 2 – **BackupFull**: Runs full database backups of the BizTalk Server databases</span></span>

-   <span data-ttu-id="eebbb-109">步驟 3 – **MarkAndBackUpLog**： 備份 BizTalk Server 資料庫記錄檔</span><span class="sxs-lookup"><span data-stu-id="eebbb-109">Step 3 – **MarkAndBackUpLog**: Backs up the BizTalk Server database logs</span></span>

-   <span data-ttu-id="eebbb-110">步驟 4 –**清除備份歷程記錄**： 選擇 備份歷程記錄保留多久</span><span class="sxs-lookup"><span data-stu-id="eebbb-110">Step 4 – **Clear Backup History**: Choose how long the backup history is kept</span></span>

<span data-ttu-id="eebbb-111">若要設定這項作業，您將需要：</span><span class="sxs-lookup"><span data-stu-id="eebbb-111">To configure this job, you'll need to:</span></span>  
  
-   <span data-ttu-id="eebbb-112">識別主要和目的地 SQL Server 和其他備份選項</span><span class="sxs-lookup"><span data-stu-id="eebbb-112">Identify the primary and destination SQL Servers and other backup options</span></span>
  
-   <span data-ttu-id="eebbb-113">選擇 Windows 使用者帳戶，來備份您的資料庫，並建立此帳戶的 SQL Server 登入</span><span class="sxs-lookup"><span data-stu-id="eebbb-113">Choose a Windows user account to back up your databases, and create a SQL Server login for this account</span></span>
  
-   <span data-ttu-id="eebbb-114">將 SQL Server 登入對應至 BizTalk Server 資料庫中的 BTS_BACKUP_USERS 資料庫角色</span><span class="sxs-lookup"><span data-stu-id="eebbb-114">Map SQL Server logins to the BTS_BACKUP_USERS database role in the BizTalk Server databases</span></span>
  
-   <span data-ttu-id="eebbb-115">確定所有節點上的 MSDTC 服務都在作用中。</span><span class="sxs-lookup"><span data-stu-id="eebbb-115">Ensure MSDTC service is active on all nodes.</span></span> <span data-ttu-id="eebbb-116">否則，將來源節點與目的地節點之間的連結的伺服器會失敗。</span><span class="sxs-lookup"><span data-stu-id="eebbb-116">Otherwise, adding a linked server between the source node and the destination node fails.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="eebbb-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="eebbb-117">Before you begin</span></span>  
  
- <span data-ttu-id="eebbb-118">有些組態和備份作業需要 sysadmin SQL Server 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="eebbb-118">Certain configuration and backup operations require membership in the sysadmin SQL Server role.</span></span> <span data-ttu-id="eebbb-119">若要備份您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，登入主要伺服器是 SQL Server sysadmin 伺服器角色的成員的帳戶。</span><span class="sxs-lookup"><span data-stu-id="eebbb-119">To back up your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, sign in the primary server with an account that is a member of the SQL Server sysadmin Server role.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="eebbb-120"> 組態會加入的 BTS_BACKUP_USERS 資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="eebbb-120"> configuration adds the BTS_BACKUP_USERS database role.</span></span> <span data-ttu-id="eebbb-121">您用來備份資料庫的使用者帳戶不需要在備份中，除了主要伺服器可能會牽涉到的所有 SQL Server 上的系統管理員 （sysadmin SQL Server 角色） 權限。</span><span class="sxs-lookup"><span data-stu-id="eebbb-121">The user account you use to back up your databases does not require System Administrator (sysadmin SQL Server role) permissions on all the SQL Servers that may be involved in a backup, except for the primary server.</span></span>  
  
- <span data-ttu-id="eebbb-122">決定哪些登入帳戶您用來執行您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="eebbb-122">Decide which sign in account you use to run your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backups.</span></span> <span data-ttu-id="eebbb-123">您可以使用本機帳戶，以及您可以使用一個以上的帳戶。</span><span class="sxs-lookup"><span data-stu-id="eebbb-123">You can use a local account, and you can use more than one account.</span></span> <span data-ttu-id="eebbb-124">但通常更簡單，而且特別針對此用途建立一個專用的 Windows 網域使用者帳戶更安全。</span><span class="sxs-lookup"><span data-stu-id="eebbb-124">But it is generally simpler and more secure to create one dedicated Windows domain user account specifically for this purpose.</span></span> <span data-ttu-id="eebbb-125">您必須為此使用者設定 SQL Server 登入帳戶，而且此使用者必須對應到所有參與備份程序的主要 (來源) 或次要 (目的地) SQL Server 的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="eebbb-125">You must configure a SQL Server logon account for this user, and the user must be mapped to a SQL Server login for all of the SQL Servers that participate in the backup process, either as primary (source) or secondary (destination) servers.</span></span> <span data-ttu-id="eebbb-126">將此使用者指派給 BizTalk BTS_BACKUP_USERS 資料庫角色中，針對每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="eebbb-126">Assign this user to the BizTalk BTS_BACKUP_USERS database role for each of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases you back up.</span></span>  
  
- <span data-ttu-id="eebbb-127">備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 作業不會刪除過期的備份檔案，所以您必須手動管理這些備份檔案以回收磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="eebbb-127">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job does not delete outdated backup files, so you need to manually manage those backup files to conserve disk space.</span></span> <span data-ttu-id="eebbb-128">在為資料庫建立新的完整備份後，您應該將過期的備份檔案移動到封存儲存裝置以回收主要磁碟上的空間。</span><span class="sxs-lookup"><span data-stu-id="eebbb-128">After you have created a new full backup of your databases, you should move the outdated backup files onto an archival storage device to reclaim space on the primary disk.</span></span> <span data-ttu-id="eebbb-129">請參閱[SSIS 封裝](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/)來管理這些檔案。</span><span class="sxs-lookup"><span data-stu-id="eebbb-129">See the [SSIS packages](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/) to manage these files.</span></span>  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="eebbb-130"> 不會寫入追蹤資料直接到 BizTalk 追蹤資料庫;而是它會快取 MessageBox 資料庫中的資料，然後將它移到 BizTalk 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="eebbb-130"> does not write tracking data directly to the BizTalk Tracking database; rather it caches the data in the MessageBox database, and then moves it to the BizTalk Tracking database.</span></span> <span data-ttu-id="eebbb-131">如果發生 MessageBox 資料遺失，可能會遺失部分追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="eebbb-131">If MessageBox data loss occurs, some tracking data may also be lost.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eebbb-132">必要條件</span><span class="sxs-lookup"><span data-stu-id="eebbb-132">Prerequisites</span></span>  
* <span data-ttu-id="eebbb-133">使用屬於 sysadmin SQL Server 角色的成員帳戶的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="eebbb-133">Sign in to SQL Server using an account that is a member of the sysadmin SQL Server role.</span></span>  
  
* <span data-ttu-id="eebbb-134">您必須將 SQL Server Agent 服務設定成以網域帳戶執行 (雖然可以使用本機帳戶，但建議採用此方式)，並為每個 SQL Server 執行個體上設定一個對應的使用者登入。</span><span class="sxs-lookup"><span data-stu-id="eebbb-134">Configure the SQL Server Agent service to run under a domain account (recommended, although local accounts can be used), with a mapped user login on each instance of SQL Server.</span></span>  

* <span data-ttu-id="eebbb-135">若要使用 Azure blob 儲存體帳戶，您需要[一般用途儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account)，您的 blob 儲存體帳戶內的容器[共用的存取簽章](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#SAS)(SAS)，和[SQL 認證使用 SAS](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#credential)。</span><span class="sxs-lookup"><span data-stu-id="eebbb-135">To use an Azure blob storage account, you need a [general purpose storage account](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account), a container within your blob storage account, a [shared access signature](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#SAS) (SAS), and a [SQL credential using the SAS](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#credential).</span></span> <span data-ttu-id="eebbb-136">建立後，有您 blob 服務端點 URL 準備就緒，也就是類似 https://<em>yourstorageaccount</em>.blob.core.windows.net/*containername*。</span><span class="sxs-lookup"><span data-stu-id="eebbb-136">Once created, have your blob service endpoint URL ready, which is something like https://<em>yourstorageaccount</em>.blob.core.windows.net/*containername*.</span></span> 

    > [!TIP]
    > <span data-ttu-id="eebbb-137">如果您沒有現有的 blob 儲存體帳戶設定 SAS，則[SAS PowerShell 指令碼](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#SAS)可以建立它，和容器。</span><span class="sxs-lookup"><span data-stu-id="eebbb-137">If you don't have an existing blob storage account configured with a SAS, then the [SAS PowerShell script](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#SAS) can create it, and the container.</span></span> <span data-ttu-id="eebbb-138">[SQL Server 備份至 URL](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url)提供概觀，以及特定的步驟。</span><span class="sxs-lookup"><span data-stu-id="eebbb-138">[SQL Server Backup to URL](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url) provides an overview, and the specific steps.</span></span>
  
## <a name="configure-the-job"></a><span data-ttu-id="eebbb-139">設定作業</span><span class="sxs-lookup"><span data-stu-id="eebbb-139">Configure the job</span></span>  
  
1. <span data-ttu-id="eebbb-140">在 SQL 伺服器裝載 BizTalk 管理資料庫上，開啟**SQL Server Management Studio**，並連接到您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eebbb-140">On the SQL Server that hosts the BizTalk Management database, open **SQL Server Management Studio**, and connect to your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
2. <span data-ttu-id="eebbb-141">展開 [SQL Server Agent] ，再展開 [作業] 。</span><span class="sxs-lookup"><span data-stu-id="eebbb-141">Expand **SQL Server Agent**, and expand **Jobs**.</span></span>  
  
3. <span data-ttu-id="eebbb-142">在 [備份 BizTalk Server (BizTalkMgmtDb)]  上按一下滑鼠右鍵，然後選取 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="eebbb-142">Right-click **Backup BizTalk Server (BizTalkMgmtDb)** and select **Properties**.</span></span> <span data-ttu-id="eebbb-143">在作業屬性中，選取 [步驟] 。</span><span class="sxs-lookup"><span data-stu-id="eebbb-143">In the job properties, select **Steps**.</span></span>  
  
4. <span data-ttu-id="eebbb-144">選取 **設定壓縮選項**步驟，然後選取**編輯**:</span><span class="sxs-lookup"><span data-stu-id="eebbb-144">Select the **Set Compression Option** step, and select **Edit**:</span></span>  

   <span data-ttu-id="eebbb-145">此步驟會呼叫`sp_SetBackupCompression`預存程序中設定的值上的 BizTalk 管理資料庫 (BizTalkMgmtDb)`adm_BackupSettings`資料表。</span><span class="sxs-lookup"><span data-stu-id="eebbb-145">This step calls the `sp_SetBackupCompression` stored procedure in the BizTalk management database (BizTalkMgmtDb) to set the value on the `adm_BackupSettings` table.</span></span> <span data-ttu-id="eebbb-146">預存程序中的一個參數： <strong>@bCompression</strong>。</span><span class="sxs-lookup"><span data-stu-id="eebbb-146">The stored procedure has one parameter: <strong>@bCompression</strong>.</span></span> <span data-ttu-id="eebbb-147">根據預設，它設定為**0** （備份壓縮已關閉）。</span><span class="sxs-lookup"><span data-stu-id="eebbb-147">By default, it is set to **0** (backup compression is off).</span></span> <span data-ttu-id="eebbb-148">若要套用壓縮，將值變更為**1**:</span><span class="sxs-lookup"><span data-stu-id="eebbb-148">To apply compression, change the value to **1**:</span></span>  
  
   ```  
   exec [dbo].[sp_SetBackupCompression] @bCompression = 1 /*0 - Do not use Compression, 1 - Use Compression */  
   ```  
  
    <span data-ttu-id="eebbb-149">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="eebbb-149">Select **OK**.</span></span>  
  
5. <span data-ttu-id="eebbb-150">選取  **BackupFull**步驟，然後選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="eebbb-150">Select the **BackupFull** step, and select **Edit**.</span></span> <span data-ttu-id="eebbb-151">在 **命令**方塊中，更新參數值：</span><span class="sxs-lookup"><span data-stu-id="eebbb-151">In the **Command** box, update the parameter values:</span></span>  
  
   1. <span data-ttu-id="eebbb-152">**頻率**： 預設值是**d** （每日）; 這是建議的設定。</span><span class="sxs-lookup"><span data-stu-id="eebbb-152">**Frequency**: The default is **d** (daily); which is the recommended setting.</span></span> <span data-ttu-id="eebbb-153">其他值包括 **h** (每小時)、 **w** (每週)、 **m** (每月)、或 **y** (每年)。</span><span class="sxs-lookup"><span data-stu-id="eebbb-153">Other values include **h** (hourly), **w** (weekly), **m** (monthly), or **y** (yearly).</span></span>  
  
   2. <span data-ttu-id="eebbb-154">**名稱**：預設值是 **[BTS]**。</span><span class="sxs-lookup"><span data-stu-id="eebbb-154">**Name**: The default is **BTS**.</span></span> <span data-ttu-id="eebbb-155">這個名稱會用來做為備份檔案名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="eebbb-155">The name is used as part of the backup file name.</span></span>  
  
   3. <span data-ttu-id="eebbb-156">**備份檔案的位置**： 取代 '*\<目的地路徑\>*' 的電腦與您想要用來備份資料夾的完整路徑（此路徑必須包含單引號）[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫或 Azure blob 儲存體帳戶的 blob 服務端點 URL。</span><span class="sxs-lookup"><span data-stu-id="eebbb-156">**Location of backup files**: Replace '*\<destination path\>*' with the full path (the path must include the single quotes) to the computer and folder where you want to back up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, or the blob service endpoint URL to an Azure blob storage account.</span></span>  

      > [!IMPORTANT]
      > - <span data-ttu-id="eebbb-157">如果您輸入本機路徑，則您必須手動將所有檔案都複製到目的系統上相同的資料夾時備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="eebbb-157">If you enter a local path, then you have to manually copy all the files to the same folder on the destination system whenever the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job creates new files.</span></span>  
      > 
      >      <span data-ttu-id="eebbb-158">若要使用的遠端路徑，請輸入 UNC 共用這類\\ \\  *\<ServerName\>*\\*\<所\>* \\，其中*\<ServerName\>* 是您想要的檔案的伺服器名稱並*\<所\>* 是共用的磁碟機或資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="eebbb-158">To use a remote path, enter a UNC share such as \\\\*\<ServerName\>*\\*\<SharedDrive\>*\\, where *\<ServerName\>* is the name of the server where you want the files, and *\<SharedDrive\>* is name of the shared drive or folder.</span></span>  
      > 
      >      <span data-ttu-id="eebbb-159">透過網路備份資料可能會因為網路問題而受限。</span><span class="sxs-lookup"><span data-stu-id="eebbb-159">Backing up data over a network is subject to any network issues.</span></span> <span data-ttu-id="eebbb-160">當使用遠端位置，請確認備份成功時備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業完成。</span><span class="sxs-lookup"><span data-stu-id="eebbb-160">When using a remote location, verify the backup succeeded when the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job finishes.</span></span>  
      > - <span data-ttu-id="eebbb-161">若要避免資料遺失，請將備份磁碟設定為資料庫資料與記錄磁碟以外的其他磁碟。</span><span class="sxs-lookup"><span data-stu-id="eebbb-161">To avoid potential data loss, configure the backup disk to be a different disk than the database data and log disks.</span></span> <span data-ttu-id="eebbb-162">此做法可確保您在資料或記錄磁碟故障時存取備份。</span><span class="sxs-lookup"><span data-stu-id="eebbb-162">This is necessary so you can access the backups if the data or log disk fails.</span></span>  
      > - <span data-ttu-id="eebbb-163">當備份至 Azure blob 帳戶，輸入**Blob 服務端點**URL 和容器名稱，就會列在您 blob 服務屬性[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="eebbb-163">When backing up to an Azure blob account, enter the **Blob service endpoint** URL and the container name, which are listed in your blob service properties in the [Azure portal](https://portal.azure.com).</span></span>

   4. <span data-ttu-id="eebbb-164">選擇性。</span><span class="sxs-lookup"><span data-stu-id="eebbb-164">Optional.</span></span> <span data-ttu-id="eebbb-165">**部分備份失敗之後強制完整備份**(@ForceFullBackupAfterPartialSetFailure): 預設值是**0**。</span><span class="sxs-lookup"><span data-stu-id="eebbb-165">**Force full backup after partial backup failures** (@ForceFullBackupAfterPartialSetFailure): The default is **0**.</span></span> <span data-ttu-id="eebbb-166">如果記錄檔備份失敗，到達下一個完整備份頻率間隔之前，會不執行任何完整備份。</span><span class="sxs-lookup"><span data-stu-id="eebbb-166">If a log backup fails, no full backups are ran until the next full backup frequency interval is reached.</span></span> <span data-ttu-id="eebbb-167">取代**1**如果您想每次發生記錄檔備份失敗時，執行完整備份。</span><span class="sxs-lookup"><span data-stu-id="eebbb-167">Replace with **1** if you want a full backup ran whenever a log backup failure occurs.</span></span>
    
   5. <span data-ttu-id="eebbb-168">選擇性。</span><span class="sxs-lookup"><span data-stu-id="eebbb-168">Optional.</span></span> <span data-ttu-id="eebbb-169">**若要執行備份程序的本地小時時間**(@BackupHour): 預設值是**NULL**。</span><span class="sxs-lookup"><span data-stu-id="eebbb-169">**Local time hour for the backup process to run** (@BackupHour): The default is **NULL**.</span></span> <span data-ttu-id="eebbb-170">備份作業不是相關聯的時區[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和執行於 UTC 午夜時間 (0000)。</span><span class="sxs-lookup"><span data-stu-id="eebbb-170">The backup job is not associated with the time zone of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, and runs at midnight UTC time (0000).</span></span> <span data-ttu-id="eebbb-171">如果您想要備份以特定時間的時區[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上，輸入一個整數值從 0 （午夜） 到 23 （晚上 11 點） 為本地小時時間。</span><span class="sxs-lookup"><span data-stu-id="eebbb-171">If you want to backup at a specific hour in the time zone of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer, enter an integer value from 0 (midnight) to 23 (11 PM) as the local time hour.</span></span> 

   6. <span data-ttu-id="eebbb-172">選擇性。</span><span class="sxs-lookup"><span data-stu-id="eebbb-172">Optional.</span></span> <span data-ttu-id="eebbb-173">**使用本地時間**(@UseLocalTime): 會指示使用本地時間的程序。</span><span class="sxs-lookup"><span data-stu-id="eebbb-173">**Use local time** (@UseLocalTime): Tells the procedure to use local time.</span></span> <span data-ttu-id="eebbb-174">預設值是**0**，並使用目前的 UTC 時間 – getutcdate （） – 2007年-05-04 01:34:11.933。</span><span class="sxs-lookup"><span data-stu-id="eebbb-174">The default value is **0**, and uses current UTC time – GETUTCDATE() – 2007-05-04 01:34:11.933.</span></span> <span data-ttu-id="eebbb-175">如果設定為**1**，則它會使用當地時間 – getdate （） – 2007年-05-03 18:34:11.933</span><span class="sxs-lookup"><span data-stu-id="eebbb-175">If set to **1**, then it uses local time – GETDATE() – 2007-05-03 18:34:11.933</span></span>
  
   <span data-ttu-id="eebbb-176">在下列範例中，會建立於上午 2 點，每日備份，並將其儲存在 m:\ 磁碟機中：</span><span class="sxs-lookup"><span data-stu-id="eebbb-176">In the following example, daily backups are created at 2am, and stored in the m:\ drive:</span></span>  
  
   ```  
   exec [dbo].[sp_BackupAllFull_Schedule]   
   'd' /* Frequency */,   
   'BTS' /* Name */,   
   'm:\BizTalkBackups' /* location of backup files */,   
   '0' /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */,   
   '2' /* local time hour for the backup process to run */  
   ```  

   <span data-ttu-id="eebbb-177">在下列範例中，會建立在午夜 UTC 時間，每週備份，並將其儲存在您的 Azure blob 帳戶中：</span><span class="sxs-lookup"><span data-stu-id="eebbb-177">In the following example, weekly backups are created at midnight UTC time, and stored in your Azure blob account:</span></span> 

   ```  
   exec [dbo].[sp_BackupAllFull_Schedule]   
   'w' /* Frequency */,   
   'BTS' /* Name */,   
   'http://yourstorageaccount.blob.core.windows.net/yourcontainer/' /* location of backup files */,   
   '1' /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */
   ```  

    <span data-ttu-id="eebbb-178">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="eebbb-178">Select **OK**.</span></span>  
  
6. <span data-ttu-id="eebbb-179">選取  **MarkAndBackupLog**步驟，然後選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="eebbb-179">Select the **MarkAndBackupLog** step, and select **Edit**.</span></span> <span data-ttu-id="eebbb-180">在 **命令**方塊中，更新參數值：</span><span class="sxs-lookup"><span data-stu-id="eebbb-180">In the **Command** box, update the parameter values:</span></span>  
  
   1. <span data-ttu-id="eebbb-181"><strong>@MarkName</strong>： 這是備份檔案的命名慣例的一部分：\<伺服器名稱\>\_\<資料庫名稱\>**\_記錄\_** \<記錄標示名稱\> \_\<時間戳記\></span><span class="sxs-lookup"><span data-stu-id="eebbb-181"><strong>@MarkName</strong>: This is part of the naming convention for backup files: \<Server Name\>\_\<Database Name\>**\_Log\_**\< Log Mark Name \>\_\<Timestamp\></span></span>  
    
   2. <span data-ttu-id="eebbb-182"><strong>@BackupPath</strong>： 完整目的地路徑 （包含單引號） 之電腦和資料夾來儲存[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫記錄檔，或 Azure blob 儲存體帳戶和容器。</span><span class="sxs-lookup"><span data-stu-id="eebbb-182"><strong>@BackupPath</strong>: Full destination path (including single quotes) to the computer and folder to store the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database logs, or the Azure blob storage account and container.</span></span> <span data-ttu-id="eebbb-183">*\<目的地路徑\>* 也可以是本機或 UNC 路徑到另一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="eebbb-183">The *\<destination path\>* can also be local or a UNC path to another server.</span></span>  
  
      <span data-ttu-id="eebbb-184">MarkAndBackupLog 步驟會標記要備份的記錄檔，然後加以備份。</span><span class="sxs-lookup"><span data-stu-id="eebbb-184">The MarkAndBackupLog step marks the logs for backup, and then backs them up.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="eebbb-185">若要避免**潛在資料遺失**以及**效能改善**，則*\<目的地路徑\>* 應該設定為在不同的電腦或硬碟機，不同於用來儲存原始的資料庫記錄檔。</span><span class="sxs-lookup"><span data-stu-id="eebbb-185">To avoid **potential data loss** and for **performance improvement**, the *\<destination path\>* should be set to a different computer, or hard drive, different from what is used to store the original database logs.</span></span>  
  
    <span data-ttu-id="eebbb-186">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="eebbb-186">Select **OK**.</span></span>  
  
7. <span data-ttu-id="eebbb-187">選取 **清除備份歷程記錄**步驟，然後選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="eebbb-187">Select the **Clear Backup History** step, and select **Edit**.</span></span> <span data-ttu-id="eebbb-188">在 **命令**方塊中，更新參數值：</span><span class="sxs-lookup"><span data-stu-id="eebbb-188">In the **Command** box, update the parameter values:</span></span>  
  
   1. <span data-ttu-id="eebbb-189"><strong>@DaysToKeep</strong>： 預設值是**14 天**。</span><span class="sxs-lookup"><span data-stu-id="eebbb-189"><strong>@DaysToKeep</strong>: Default value is **14 days**.</span></span> <span data-ttu-id="eebbb-190">決定備份的歷程記錄保留多久`Adm_BackupHistory`資料表。</span><span class="sxs-lookup"><span data-stu-id="eebbb-190">Determines how long the backup history is kept in the `Adm_BackupHistory` table.</span></span> <span data-ttu-id="eebbb-191">定期清除備份歷程記錄可協助維護`Adm_BackupHistory`資料表來為適當的大小。</span><span class="sxs-lookup"><span data-stu-id="eebbb-191">Periodically clearing the backup history helps maintain the `Adm_BackupHistory` table to an appropriate size.</span></span> 
    
   2. <span data-ttu-id="eebbb-192">選擇性。</span><span class="sxs-lookup"><span data-stu-id="eebbb-192">Optional.</span></span> <span data-ttu-id="eebbb-193"><strong>@UseLocalTime</strong>： 會指示使用本地時間的程序。</span><span class="sxs-lookup"><span data-stu-id="eebbb-193"><strong>@UseLocalTime</strong>: Tells the procedure to use local time.</span></span> <span data-ttu-id="eebbb-194">預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="eebbb-194">The default value is 0.</span></span> <span data-ttu-id="eebbb-195">它會使用目前的 UTC 時間 – getutcdate （） – 2007年-05-04 01:34:11.933。</span><span class="sxs-lookup"><span data-stu-id="eebbb-195">It uses current UTC time – GETUTCDATE() – 2007-05-04 01:34:11.933.</span></span> <span data-ttu-id="eebbb-196">如果設為 1，則它會使用當地時間 – getdate （） – 2007年-05-03 18:34:11.933</span><span class="sxs-lookup"><span data-stu-id="eebbb-196">If set to 1, then it uses local time – GETDATE() – 2007-05-03 18:34:11.933</span></span>
  
   ```  
   exec [dbo].[sp_DeleteBackupHistory] @DaysToKeep=14, @UseLocalTime =1 
   ```  
  
   > [!NOTE]
   >  <span data-ttu-id="eebbb-197">此步驟**則否**刪除備份檔案的目的地路徑。</span><span class="sxs-lookup"><span data-stu-id="eebbb-197">This step **does not** delete backup files from the destination path.</span></span>  
    
    <span data-ttu-id="eebbb-198">選取 [確定]  ，然後關閉所有的屬性視窗。</span><span class="sxs-lookup"><span data-stu-id="eebbb-198">Select **OK** and close all property windows.</span></span>  
  
8. <span data-ttu-id="eebbb-199">選擇性。</span><span class="sxs-lookup"><span data-stu-id="eebbb-199">Optional.</span></span> <span data-ttu-id="eebbb-200">變更備份排程。</span><span class="sxs-lookup"><span data-stu-id="eebbb-200">Change the backup schedule.</span></span> <span data-ttu-id="eebbb-201">請參閱[如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md)。</span><span class="sxs-lookup"><span data-stu-id="eebbb-201">See [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md).</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="eebbb-202">「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業會在您第一次設定時執行。</span><span class="sxs-lookup"><span data-stu-id="eebbb-202">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs the first time you configure it.</span></span> <span data-ttu-id="eebbb-203">根據預設，在後續的執行，備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業完成的完整備份一天一次，並完成記錄備份每隔 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="eebbb-203">By default, on subsequent runs, the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job completes a full backup once a day, and completes log backups every 15 minutes.</span></span>  
  
9. <span data-ttu-id="eebbb-204">以滑鼠右鍵按一下**備份 BizTalk Server**作業，然後選取**啟用**。</span><span class="sxs-lookup"><span data-stu-id="eebbb-204">Right-click the **Backup BizTalk Server** job, and select **Enable**.</span></span> <span data-ttu-id="eebbb-205">狀態應該變更為 **成功**。</span><span class="sxs-lookup"><span data-stu-id="eebbb-205">The status should change to **Success**.</span></span>  

## <a name="execute-backupsetupallprocssql-and-logshippingdestinationlogicsql"></a><span data-ttu-id="eebbb-206">執行 Backup_Setup_All_Procs.sql 和 LogShipping_Destination_Logic.sql</span><span class="sxs-lookup"><span data-stu-id="eebbb-206">Execute Backup_Setup_All_Procs.sql and LogShipping_Destination_Logic.sql</span></span>

<span data-ttu-id="eebbb-207">**[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] 功能 Pack 2 (FP2)** 使用中的 Backup_Setup_All_Procs.sql 和 LogShipping_Destination_Logic.sql 指令碼`\Program Files (x86)\Microsoft BizTalk Server *your version*\Schema`。</span><span class="sxs-lookup"><span data-stu-id="eebbb-207">**[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2 (FP2)** used the Backup_Setup_All_Procs.sql and LogShipping_Destination_Logic.sql scripts in `\Program Files (x86)\Microsoft BizTalk Server *your version*\Schema`.</span></span> 

<span data-ttu-id="eebbb-208">如果已設定備份 BizTalk Server 作業，而且您想要切換以使用 Azure blob （而非磁碟），然後也執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="eebbb-208">If your Backup BizTalk Server job is already configured, and you want to switch to using Azure blob (instead of a disk), then also do the following:</span></span> 

1. <span data-ttu-id="eebbb-209">在 SQL 伺服器上，執行`Backup_Setup_All_Procs.sql`對正在 「 備份 BizTalk Server 」 工作所備份的所有自訂資料庫的指令碼。</span><span class="sxs-lookup"><span data-stu-id="eebbb-209">On the SQL Server, execute the `Backup_Setup_All_Procs.sql` script against all custom databases that are being backed up by the Backup BizTalk Server job.</span></span> <span data-ttu-id="eebbb-210">根據預設，FP2 自動更新 BizTalk 資料庫;它不會更新任何自訂的資料庫 (在這些資料庫`adm_OtherBackupDatabases`附表 BizTalkMgmtDb)。</span><span class="sxs-lookup"><span data-stu-id="eebbb-210">By default, FP2 automatically updates BizTalk databases; it does not update any custom databases (those databases in the `adm_OtherBackupDatabases` table in BizTalkMgmtDb).</span></span>

    <span data-ttu-id="eebbb-211">[回到設定自訂資料庫](how-to-back-up-custom-databases.md)提供自訂的資料庫上的更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="eebbb-211">[Back Up Custom Databases](how-to-back-up-custom-databases.md) provides more details on custom databases.</span></span> 

2. <span data-ttu-id="eebbb-212">**如果您使用[記錄傳送](log-shipping.md)**，SQL Server 中的目的系統上執行 LogShipping_Destination_Logic.sql 指令碼。</span><span class="sxs-lookup"><span data-stu-id="eebbb-212">**If you use [log shipping](log-shipping.md)**, execute the LogShipping_Destination_Logic.sql script on the destination system within SQL Server.</span></span> <span data-ttu-id="eebbb-213">如果您未使用記錄傳送，則不會執行此指令碼。</span><span class="sxs-lookup"><span data-stu-id="eebbb-213">If you don't use log shipping, then do not execute this script.</span></span>

    <span data-ttu-id="eebbb-214">[記錄傳送設定的目的系統](how-to-configure-the-destination-system-for-log-shipping.md)目的系統上提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="eebbb-214">[Configure the Destination System for Log Shipping](how-to-configure-the-destination-system-for-log-shipping.md) provides more details on the destination system.</span></span>

## <a name="spforcefullbackup-stored-procedure"></a><span data-ttu-id="eebbb-215">sp_ForceFullBackup 預存程序</span><span class="sxs-lookup"><span data-stu-id="eebbb-215">sp_ForceFullBackup stored procedure</span></span>  
  
<span data-ttu-id="eebbb-216">**Sp_ForceFullBackup**預存程序中的**BizTalkMgmtDb**資料庫可以用來執行特定的資料和記錄檔的完整備份。</span><span class="sxs-lookup"><span data-stu-id="eebbb-216">The **sp_ForceFullBackup** stored procedure in the **BizTalkMgmtDb** database can be used to run an ad-hoc full backup of the data and log files.</span></span> <span data-ttu-id="eebbb-217">此預存程序會以值 1 更新 adm_ForceFullBackup 資料表。</span><span class="sxs-lookup"><span data-stu-id="eebbb-217">The stored procedure updates the adm_ForceFullBackup table with a value 1.</span></span> <span data-ttu-id="eebbb-218">在下一次備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]工作執行，會建立完整資料庫備份組。</span><span class="sxs-lookup"><span data-stu-id="eebbb-218">The next time the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job is ran, a full database backup set is created.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eebbb-219">後續步驟</span><span class="sxs-lookup"><span data-stu-id="eebbb-219">Next Steps</span></span>  
 <span data-ttu-id="eebbb-220">[設定記錄傳送目的地系統](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span><span class="sxs-lookup"><span data-stu-id="eebbb-220">[Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span></span>  
 [<span data-ttu-id="eebbb-221">排程備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="eebbb-221">Schedule the Backup BizTalk Server Job</span></span>](../core/how-to-schedule-the-backup-biztalk-server-job.md)  
 [<span data-ttu-id="eebbb-222">Azure 儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="eebbb-222">Azure storage accounts</span></span>](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)  
 [<span data-ttu-id="eebbb-223">SQL Server 備份至 URL</span><span class="sxs-lookup"><span data-stu-id="eebbb-223">SQL Server Backup to URL</span></span>](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url)
