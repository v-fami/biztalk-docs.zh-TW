---
title: "如何還原您的資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 2016-05-10
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, log shipping
- restoring [BAM], Star Schema database, Star Schema database [BAM], restoring
- restoring, 64-bit environments
- Star Schema database [BAM], restoring
- restoring [BAM], Analysis database
- log shipping
- databases, restoring
- Archive database [BAM], restoring
- backing up, restoring
- Analysis database [BAM], restoring
- restoring [BAM], Archive database
- restoring [BAM], Star Schema database
- databases, restoring [64-bit environment]
- Primary Import database [BAM], restoring
- 64-bit environments, restoring databases
- restoring, databases
ms.assetid: 0176932a-6b3d-4502-975b-a76296189092
caps.latest.revision: "52"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6833fff893a692475e97e7722d9d65658eace0d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-restore-your-databases"></a><span data-ttu-id="3a792-102">如何還原資料庫</span><span class="sxs-lookup"><span data-stu-id="3a792-102">How to Restore Your Databases</span></span>
<span data-ttu-id="3a792-103">您必須將所有資料庫還原為相同的標記，以確保資料庫間的交易狀態一致。</span><span class="sxs-lookup"><span data-stu-id="3a792-103">You must restore all databases to the same mark to ensure a consistent transactional state among the databases.</span></span> <span data-ttu-id="3a792-104">請參閱[標示的交易，完整備份，並記錄備份](../core/marked-transactions-full-backups-and-log-backups.md)。</span><span class="sxs-lookup"><span data-stu-id="3a792-104">See [Marked Transactions, Full Backups, and Log Backups](../core/marked-transactions-full-backups-and-log-backups.md).</span></span>  
  
 <span data-ttu-id="3a792-105">如果目的系統中只有一個伺服器，請確認已還原所有記錄檔備份集 (除了最新的記錄檔備份集以外)。</span><span class="sxs-lookup"><span data-stu-id="3a792-105">If there is only one server in the destination system, make sure that all of the log backup sets (except for the most recent set) have been restored.</span></span> <span data-ttu-id="3a792-106">請參閱[檢視的記錄備份還原](../core/viewing-the-history-of-restored-backups.md)。</span><span class="sxs-lookup"><span data-stu-id="3a792-106">See [Viewing the History of Restored Backups](../core/viewing-the-history-of-restored-backups.md).</span></span> <span data-ttu-id="3a792-107">如果尚未還原所有記錄檔備份集，且目前沒有執行還原作業，請執行還原作業 (如果需要，請以手動執行)。</span><span class="sxs-lookup"><span data-stu-id="3a792-107">If all the log backup sets have not been restored, and the restore job is not currently running, run the restore job (manually if necessary).</span></span> <span data-ttu-id="3a792-108">如果有可還原的未完成備份集，此作業會處理這些備份集，直到全部都還原為止。</span><span class="sxs-lookup"><span data-stu-id="3a792-108">If there are outstanding backup sets that can be restored, the job processes them until they are all restored.</span></span>  
  
 <span data-ttu-id="3a792-109">如果目的系統中有多部伺服器，必須將所有伺服器還原為相同的備份集。</span><span class="sxs-lookup"><span data-stu-id="3a792-109">If there are multiple servers in the destination system, all servers must be restored to the same backup set.</span></span> <span data-ttu-id="3a792-110">檢視每部伺服器上的還原記錄，同時確認所有伺服器上最近所還原的記錄檔備份集皆相同。</span><span class="sxs-lookup"><span data-stu-id="3a792-110">View the restore history on each server and make sure that the most recent log backup set restored is the same on all servers.</span></span> <span data-ttu-id="3a792-111">否則，您必須在每部需要還原最新記錄檔備份集的伺服器上，手動執行還原作業。</span><span class="sxs-lookup"><span data-stu-id="3a792-111">If it is not, you must manually run the restore job on each server that needs the most recent log backup set restored.</span></span>  
  
 <span data-ttu-id="3a792-112">當所有伺服器都位在相同的備份集後，便可手動還原最後的備份集。</span><span class="sxs-lookup"><span data-stu-id="3a792-112">After all of the servers are on the same backup set, the final set can be manually restored.</span></span>  
  
 <span data-ttu-id="3a792-113">adm_BackupHistory 資料表是來源系統中記錄檔傳送程序的中央歷程記錄點。</span><span class="sxs-lookup"><span data-stu-id="3a792-113">The adm_BackupHistory table is the central history point for the log shipping process for the source system.</span></span> <span data-ttu-id="3a792-114">所有執行的備份工作都會記錄到這個資料表中。</span><span class="sxs-lookup"><span data-stu-id="3a792-114">All backup work performed is recorded to this table.</span></span> <span data-ttu-id="3a792-115">您目的系統中的所有伺服器都會讀取這個資料表，以接收執行其還原工作所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="3a792-115">All servers in your destination system read from this table to receive the information needed to perform their restore work.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a792-116">如果您是從備份還原「BAM 主要匯入」資料庫，那麼您也應該使用比 BAM 主要備份還舊的備份，來還原「BAM 封存」、「BAM 星狀結構描述」及「BAM 分析」資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a792-116">If you restore the BAM Primary Import database from a backup, then you should also restore the BAM Archive, BAM Star Schema, and BAM Analysis databases by using a backup older than the BAM Primary backup.</span></span> <span data-ttu-id="3a792-117">請參閱[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)。</span><span class="sxs-lookup"><span data-stu-id="3a792-117">See [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a792-118">如果您要從「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」工作放置來源資料庫之完整或記錄檔備份的位置移動它們，就應該透過在目的系統的 bts_LogShippingDatabases 資料表中，將 LogFileLocation 或 DBFileLocation 設定為目的系統應該讀取完整/記錄檔備份檔案的新位置，更新該資料庫的相關聯資料列。</span><span class="sxs-lookup"><span data-stu-id="3a792-118">If you move the full or log backups for a source database from the location in which the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job put them, you should update the associated row for that database in the bts_LogShippingDatabases table on the destination system by setting the LogFileLocation or DBFileLocation to the new location where the destination system should read the full/log backup files.</span></span> <span data-ttu-id="3a792-119">當您執行 bts_ConfigureBtsLogShipping 預存程序時，便會填入此資料表。</span><span class="sxs-lookup"><span data-stu-id="3a792-119">This table is populated when you run the bts_ConfigureBtsLogShipping stored procedure.</span></span> <span data-ttu-id="3a792-120">依照預設，會將這些資料行設為空值，這表示目的系統應該從 adm_BackupHistory 資料表中儲存的位置讀取備份檔案。</span><span class="sxs-lookup"><span data-stu-id="3a792-120">By default, these columns are set to null, which indicates that the destination system should read the backup files from the location stored in the adm_BackupHistory table.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3a792-121">請務必在安全的位置保留備份檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="3a792-121">Always keep a copy of your backup files in a secure location.</span></span> <span data-ttu-id="3a792-122">即使您擁有記錄檔備份，也無法在沒有備份檔案的情況下還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a792-122">Even if you have log backups, you cannot restore your databases without the backup files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3a792-123">必要條件</span><span class="sxs-lookup"><span data-stu-id="3a792-123">Prerequisites</span></span>  
 <span data-ttu-id="3a792-124">使用系統管理員 SQL Server 角色之成員的帳戶登入 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="3a792-124">Log in to SQL Server using an account that is a member of the sysadmin SQL Server role.</span></span>  
  
### <a name="to-restore-your-databases"></a><span data-ttu-id="3a792-125">還原您的資料庫</span><span class="sxs-lookup"><span data-stu-id="3a792-125">To restore your databases</span></span>  
  
1.  <span data-ttu-id="3a792-126">在目的地系統上，開啟**SQL Server Management Studio**，並連接到您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3a792-126">On the destination system, open **SQL Server Management Studio**, and connect to your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="3a792-127">展開 [SQL Server Agent] ，再展開 [作業] 。</span><span class="sxs-lookup"><span data-stu-id="3a792-127">Expand **SQL Server Agent**, and expand **Jobs**.</span></span> <span data-ttu-id="3a792-128">請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3a792-128">Do the following:</span></span>  
  
    1.  <span data-ttu-id="3a792-129">在 **BTS 記錄傳送 - 取得備份記錄** 作業上按一下滑鼠右鍵，然後選取 [停用] 。</span><span class="sxs-lookup"><span data-stu-id="3a792-129">Right-click the **BTS Log Shipping - Get Backup History** job and select **Disable**.</span></span> <span data-ttu-id="3a792-130">狀態會變更為「成功」。</span><span class="sxs-lookup"><span data-stu-id="3a792-130">The status changes to Success.</span></span>  
  
    2.  <span data-ttu-id="3a792-131">在 **BTS 記錄傳送 - 還原資料庫** 作業上按一下滑鼠右鍵，然後選取 [停用] 。</span><span class="sxs-lookup"><span data-stu-id="3a792-131">Right-click the **BTS Log Shipping - Restore Databases** job and select **Disable**.</span></span> <span data-ttu-id="3a792-132">狀態會變更為「成功」。</span><span class="sxs-lookup"><span data-stu-id="3a792-132">The status changes to Success.</span></span>  
  
    3.  <span data-ttu-id="3a792-133">在 **BTS 檔記錄傳送 - 還原為標示** 上按一下滑鼠右鍵，然後選取 [從下列步驟啟動作業] 。</span><span class="sxs-lookup"><span data-stu-id="3a792-133">Right-click the **BTS Log Shipping - Restore To Mark** and select **Start Job at Step**.</span></span> <span data-ttu-id="3a792-134">選取 [步驟 ID 1]  ，然後選取 [開始] 。</span><span class="sxs-lookup"><span data-stu-id="3a792-134">Select **Step ID 1** and select **Start**.</span></span>  
  
         <span data-ttu-id="3a792-135">當狀態變更為**成功**，SQL Server Agent 作業和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫會還原至目的系統。</span><span class="sxs-lookup"><span data-stu-id="3a792-135">When the status changes to **Success**, the SQL Server Agent jobs and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are restored to the destination system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3a792-136">若 **狀態** 為「錯誤」，請選取 [訊息] 欄位中的連結判斷原因。</span><span class="sxs-lookup"><span data-stu-id="3a792-136">If the **Status** is Error, select the link in the Message field to determine the cause.</span></span> <span data-ttu-id="3a792-137">這些作業的狀態必須都是成功才能繼續。</span><span class="sxs-lookup"><span data-stu-id="3a792-137">These jobs should have a Success status before continuing.</span></span>  
  
3.  <span data-ttu-id="3a792-138">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在您編輯 SampleUpdateInfo.xml 檔案，開啟命令提示字元，並移至：</span><span class="sxs-lookup"><span data-stu-id="3a792-138">On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] where you edited the SampleUpdateInfo.xml file, open a command prompt, and go to:</span></span>  
  
     <span data-ttu-id="3a792-139">32 位元電腦：`%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span><span class="sxs-lookup"><span data-stu-id="3a792-139">32-bit computer: `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span></span>  
  
     <span data-ttu-id="3a792-140">64 位元電腦：`%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`</span><span class="sxs-lookup"><span data-stu-id="3a792-140">64-bit computer: `%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`</span></span>  
  
4.  <span data-ttu-id="3a792-141">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="3a792-141">At the command prompt, type:</span></span>  
  
     `cscript UpdateDatabase.vbs SampleUpdateInfo.xml`  
  
     <span data-ttu-id="3a792-142">這個指令碼會更新所有儲存其他資料庫位置相關資訊的資料表。</span><span class="sxs-lookup"><span data-stu-id="3a792-142">This script updates all tables that store information about the location of other databases.</span></span>  
  
    > [!IMPORTANT]
    >  -   <span data-ttu-id="3a792-143">您只須在 BizTalk 群組中的 **任一部** 伺服器上執行 UpdateDatabase.vbs 即可。</span><span class="sxs-lookup"><span data-stu-id="3a792-143">Run UpdateDatabase.vbs on **one** server in the BizTalk group.</span></span>  
    > -   <span data-ttu-id="3a792-144">在 64 位元電腦上，您必須從 64 位元命令提示字元中執行 UpdateDatabase.vbs。</span><span class="sxs-lookup"><span data-stu-id="3a792-144">On 64-bit computers, you must run UpdateDatabase.vbs from a 64-bit command prompt.</span></span> <span data-ttu-id="3a792-145">請注意，64 位元電腦上的預設命令提示字元是 64 位元的命令提示字元，位於 %systemdrive%\windows\system32\cmd.exe。</span><span class="sxs-lookup"><span data-stu-id="3a792-145">Note that the default command prompt on 64-bit computers is a 64-bit command prompt and is located at %SystemDrive%\windows\System32\cmd.exe.</span></span>  
    > -   <span data-ttu-id="3a792-146">BizTalk EDI 引擎不需要任何 SampleUpdateInfo.xml 自己修改的還原資料庫時。</span><span class="sxs-lookup"><span data-stu-id="3a792-146">The BizTalk EDI engine does not require any of its own modifications to SampleUpdateInfo.xml when restoring databases.</span></span>  <span data-ttu-id="3a792-147">它依賴存取的 EDI 資料表 BizTalkDTADb 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="3a792-147">It relies on connectivity to the BizTalkDTADb database to access the EDI tables.</span></span>  
  
5.  <span data-ttu-id="3a792-148">將編輯的 SampleUpdateInfo.xml 檔案複製到下列資料夾中，在**每**執行電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]此 BizTalk 群組中：</span><span class="sxs-lookup"><span data-stu-id="3a792-148">Copy the edited SampleUpdateInfo.xml file to the following folder on **every** computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in this BizTalk group:</span></span>  
  
     <span data-ttu-id="3a792-149">32 位元電腦： 將複製到`%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span><span class="sxs-lookup"><span data-stu-id="3a792-149">32-bit computer: Copy to `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span></span>  
  
     <span data-ttu-id="3a792-150">64 位元電腦： 將複製到`%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`</span><span class="sxs-lookup"><span data-stu-id="3a792-150">64-bit computer: Copy to `%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`</span></span>  
  
6.  <span data-ttu-id="3a792-151">在**每個**電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組，開啟命令提示字元，並移至：</span><span class="sxs-lookup"><span data-stu-id="3a792-151">On **each** computer in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group, open a command prompt, and go to:</span></span>  
  
     <span data-ttu-id="3a792-152">32 位元電腦：`%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span><span class="sxs-lookup"><span data-stu-id="3a792-152">32-bit computer: `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span></span>  
  
     <span data-ttu-id="3a792-153">64 位元電腦：`%SystemDrive%Program Files (x86)Microsoft BizTalk Server <version>Bins32SchemaRestore`</span><span class="sxs-lookup"><span data-stu-id="3a792-153">64-bit computer: `%SystemDrive%Program Files (x86)Microsoft BizTalk Server <version>Bins32SchemaRestore`</span></span>  
  
7.  <span data-ttu-id="3a792-154">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="3a792-154">At the command prompt, type:</span></span>  
  
     `cscript UpdateRegistry.vbs SampleUpdateInfo.xml`  
  
     <span data-ttu-id="3a792-155">這個指令碼會更新所有儲存其他資料庫位置相關資訊的登錄項目。</span><span class="sxs-lookup"><span data-stu-id="3a792-155">This script updates all registry entries that store information about the location of other databases.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3a792-156">在 BizTalk 群組中的 **每部** 伺服器上執行 UpdateRegistry.vbs。</span><span class="sxs-lookup"><span data-stu-id="3a792-156">Run UpdateRegistry.vbs on **every** server in the BizTalk group.</span></span>  
    >   
    >  <span data-ttu-id="3a792-157">在 64 位元電腦上，您必須從 64 位元命令提示字元中執行 UpdateRegistry.vbs。</span><span class="sxs-lookup"><span data-stu-id="3a792-157">On 64-bit computers, you must run UpdateRegistry.vbs from a 64-bit command prompt.</span></span>  <span data-ttu-id="3a792-158">請注意，64 位元電腦上的預設命令提示字元是 64 位元的命令提示字元，位於 %systemdrive%\windows\system32\cmd.exe。</span><span class="sxs-lookup"><span data-stu-id="3a792-158">Note that the default command prompt on 64-bit computers is a 64-bit command prompt and is located at %SystemDrive%\windows\System32\cmd.exe.</span></span>  
  
8.  <span data-ttu-id="3a792-159">重新啟動所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="3a792-159">Restart all the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="3a792-160">請參閱[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3a792-160">See [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span></span>  
  
9. <span data-ttu-id="3a792-161">還原資料庫後，請重新啟動 Windows Management Instrumentation 服務。</span><span class="sxs-lookup"><span data-stu-id="3a792-161">After restoring your databases, restart the Windows Management Instrumentation service:</span></span>  
  
    1.  <span data-ttu-id="3a792-162">開啟 **services.msc**。</span><span class="sxs-lookup"><span data-stu-id="3a792-162">Open **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="3a792-163">在 [Windows Management Instrumentation] 上按一下滑鼠右鍵，然後按一下 [重新啟動] 。</span><span class="sxs-lookup"><span data-stu-id="3a792-163">Right-click **Windows Management Instrumentation**, and then select **Restart**.</span></span>  
  
10. <span data-ttu-id="3a792-164">開啟 [BizTalk Server 管理] 。</span><span class="sxs-lookup"><span data-stu-id="3a792-164">Open **BizTalk Server Administration**.</span></span> <span data-ttu-id="3a792-165">請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3a792-165">Do the following:</span></span>  
  
    1.  <span data-ttu-id="3a792-166">在 [BizTalk 群組]  上按一下滑鼠右鍵，然後選取 [移除] 。</span><span class="sxs-lookup"><span data-stu-id="3a792-166">Right-click the **BizTalk Group** and select **Remove**.</span></span>  
  
    2.  <span data-ttu-id="3a792-167">在 [BizTalk Server 管理]  節點上按一下滑鼠右鍵，然後選取 [連接至現有的群組] 。</span><span class="sxs-lookup"><span data-stu-id="3a792-167">Right-click **BizTalk Server Administration** and select **Connect to Existing Group**.</span></span>  
  
    3.  <span data-ttu-id="3a792-168">在 [SQL Server 名稱] 中，選取裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a792-168">In **SQL Server name**, select the name of the SQL Server instance that hosts the BizTalk Management database.</span></span> <span data-ttu-id="3a792-169">當您選取 SQL Server 執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會自動偵測[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]該電腦上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a792-169">When you select the SQL Server instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically detects the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases on that computer.</span></span>  
  
    4.  <span data-ttu-id="3a792-170">在 [資料庫名稱] 中選取您的 BizTalk 管理資料庫 (預設是**BizTalkMgmtDb** )，然後選取 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="3a792-170">In **Database name**, select your BizTalk Management database (**BizTalkMgmtDb** by default), and then select **OK**.</span></span>  
  
     <span data-ttu-id="3a792-171">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台將 BizTalk 群組加入至 [管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="3a792-171">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console adds the BizTalk group to the Administration console.</span></span>  
  
     <span data-ttu-id="3a792-172">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 現已還原，並且應該正在執行。</span><span class="sxs-lookup"><span data-stu-id="3a792-172">Your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is now restored and should be running.</span></span> <span data-ttu-id="3a792-173">接下來，設定備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]工作，以開始備份寫入新的目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="3a792-173">Next, configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job to start writing backups to a new destination server.</span></span> <span data-ttu-id="3a792-174">您也應該重新設定新的目的系統。</span><span class="sxs-lookup"><span data-stu-id="3a792-174">You should also reconfigure a new destination system.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3a792-175">如果您要在還原資料庫後使用「規則引擎」，則必須重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組中每個伺服器上的「規則引擎更新服務」。</span><span class="sxs-lookup"><span data-stu-id="3a792-175">If you are using the Rules Engine, after restoring the databases, you must restart the Rule Engine Update Service on every server in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.</span></span> <span data-ttu-id="3a792-176">請參閱[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3a792-176">See [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a792-177">如果您使用 BAM，現在可以還原 BAM 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a792-177">If you are using BAM, this is the time to restore the BAM databases.</span></span> <span data-ttu-id="3a792-178">請參閱[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)。</span><span class="sxs-lookup"><span data-stu-id="3a792-178">See [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3a792-179">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3a792-179">Next Steps</span></span>  
 [<span data-ttu-id="3a792-180">備份和還原 BAM</span><span class="sxs-lookup"><span data-stu-id="3a792-180">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)  
  
## <a name="see-also"></a><span data-ttu-id="3a792-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a792-181">See Also</span></span>  
 <span data-ttu-id="3a792-182">[如何設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="3a792-182">[How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md) </span></span>  
 [<span data-ttu-id="3a792-183">如何設定記錄傳送目的地系統</span><span class="sxs-lookup"><span data-stu-id="3a792-183">How to Configure the Destination System for Log Shipping</span></span>](../core/how-to-configure-the-destination-system-for-log-shipping.md)