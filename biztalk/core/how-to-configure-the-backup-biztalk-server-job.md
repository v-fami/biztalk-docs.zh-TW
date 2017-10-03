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
# <a name="how-to-configure-the-backup-biztalk-server-job"></a>如何設定備份 BizTalk Server 作業
本主題列出設定「備份 BizTalk Server」作業所需的步驟。  
  
 您必須先設定「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業，然後才能備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 若要設定備份，必須執行下列大部分或所有的工作：  
  
-   編輯 SQL Server Agent 的 **備份 BizTalk Server (BizTalkMgmtDb)** 作業，以指定主要與目的地 SQL Server 及其他備份選項。  
  
-   選擇 Windows 使用者帳戶，以備份資料庫，以及建立此帳戶的 SQL Server 登入。  
  
-   將 SQL Server 登入對應到 BizTalk Server 資料庫中的 BTS_BACKUP_USERS 資料庫角色。  
  
-   確定所有節點上的 MSDTC 服務都在作用中。 否則，在來源節點與目的節點之間新增連結的伺服器將會失敗。  
  
## <a name="before-you-begin"></a>開始之前  
  
-   某些組態和備份作業 (例如這一個) 需要有 sysadmin SQL Server 角色的成員資格。 若要備份您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，您必須在主要伺服器與主要伺服器上的 SQL Server sysadmin 伺服器角色的成員帳戶登入。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態會加入名為 BTS_BACKUP_USERS，以便您用來備份您的資料庫使用者帳戶不需要的所有可能包含在備份中，除了 SQL Server 上的系統管理員 （sysadmin SQL Server 角色） 權限的資料庫角色主要伺服器。  
  
-   您需要決定哪一個登入帳戶，您用來執行您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫備份。 您可以使用本機帳戶，而且可以使用不止一個帳戶，但是針對此用途建立一個專用的 Windows 網域使用者帳戶，通常會更簡單也更安全。 您必須為此使用者設定 SQL Server 登入帳戶，而且此使用者必須對應到所有參與備份程序的主要 (來源) 或次要 (目的地) SQL Server 的 SQL Server 登入。 將此使用者指派給 BizTalk BTS_BACKUP_USERS 資料庫角色，每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您資料庫備份。  
  
-   備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 作業不會刪除過期的備份檔案，所以您必須手動管理這些備份檔案以回收磁碟空間。 在為資料庫建立新的完整備份後，您應該將過期的備份檔案移動到封存儲存裝置以回收主要磁碟上的空間。 「 BizTalk 帳單 」 有可下載[SSIS 封裝](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/)管理這些檔案。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不會將追蹤資料直接寫入 BizTalk 追蹤資料庫；它會快取 MessageBox 資料庫中的資料，然後將它移到 BizTalk 追蹤資料庫。 如果發生 MessageBox 資料遺失，可能會遺失部分追蹤資料。  
  
## <a name="prerequisites"></a>必要條件  
* 使用屬於 sysadmin SQL Server 角色的成員帳戶的 SQL Server 登入。  
  
* 您必須將 SQL Server Agent 服務設定成以網域帳戶執行 (雖然可以使用本機帳戶，但建議採用此方式)，並為每個 SQL Server 執行個體上設定一個對應的使用者登入。  
  
## <a name="configure-the-backup-biztalk-server-job"></a>設定備份 BizTalk Server 作業  
  
1.  在裝載 BizTalk 管理資料庫的 SQL Server 上開啟**SQL Server Management Studio**，並連接到您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
2.  展開 [SQL Server Agent] ，再展開 [作業] 。  
  
3.  在 [備份 BizTalk Server (BizTalkMgmtDb)]  上按一下滑鼠右鍵，然後選取 [屬性] 。 在作業屬性中，選取 [步驟] 。  
  
4.  選取 [設定壓縮選項]  步驟，再選取 [編輯] 。 在 [命令]  方塊中，將此值變更為 1：  
  
    ```  
    exec [dbo].[sp_SetBackupCompression] @bCompression = 1 /*0 - Do not use Compression, 1 - Use Compression */  
    ```  
  
     選取 [確定] 。  
  
5.  選取 [BackupFull]  步驟，再選取 [編輯] 。 在 [命令]  方塊中編輯參數值：  
  
    1.  **頻率**：預設值為 **d** (每日)。 此為建議設定值。 其他值包括 **h** (每小時)、 **w** (每週)、 **m** (每月)、或 **y** (每年)。  
  
    2.  **名稱**：預設值是 **[BTS]**。 這個名稱會用來做為備份檔案名稱的一部分。  
  
    3.  **備份檔案的位置**： 取代 '*\<目的地路徑 >*' 的電腦與您想要備份的目的地資料夾的完整路徑 （此路徑必須包含單引號） [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
        > [!IMPORTANT]
        >  -   如果您指定本機路徑，則每當「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業建立新檔案時，您都必須將所有檔案手動複製到目的系統上的相同資料夾。  
        >   
        >      若要指定遠端路徑，請輸入 UNC 共用例如\\ \\  *\<ServerName >*\\*\<所 >* \\其中 *\<ServerName >*是您要檔案伺服器的名稱和*\<所 >*是共用磁碟機或資料夾的名稱。  
        >   
        >      透過網路備份資料可能會因為網路問題而受限。 當使用遠端位置，驗證備份成功時備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業結束。  
        > -   若要避免資料遺失，請將備份磁碟設定為資料庫資料與記錄磁碟以外的其他磁碟。 此做法可確保您在資料或記錄磁碟故障時存取備份。  
  
    4.  **在部分備份失敗之後強制完整備份**：沒有指定時，預設值為 **0** ，這表示如果記錄檔備份失敗，在到達下一個完整備份頻率間隔之前，不會進行任何完整備份。 如果您想要在每次發生記錄檔備份失敗時進行完整備份，請取代成 **1** 。  
  
    5.  **若要執行備份程序的本地小時時間**: 預設值是 NULL 時未指定，這表示備份作業不是與關聯的時區時間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，因此就會在午夜 UTC 時間 (0000)。 如果您想要備份至執行中的時區時間的特定小時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上，輸入一個整數值 0 （午夜） 到 23 （晚上 11 點） 為本地小時時間**BackupHour**參數。  
  
     在下列範例中，每日備份會在凌晨 2 時建立，並儲存在 m:\ 磁碟機中：  
  
    ```  
    exec [dbo].[sp_BackupAllFull_Schedule]   
    'd' /* Frequency */,   
    'BTS' /* Name */,   
    'm:\BizTalkBackups' /* location of backup files */,   
    0 /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */,   
    '2' /* local time hour for the backup process to run */  
    ```  
  
     選取 [確定] 。  
  
6.  選取 **MarkAndBackupLog** 步驟，再選取 [編輯] 。 在**命令**方塊中，取代**'***\<目的地路徑 >***'**的完整路徑 （包含單引號）電腦和您要儲存的資料夾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫記錄檔。 *\<目的地路徑 >*可以是本機或另一部伺服器的 UNC 路徑。  
  
     MarkAndBackupLog 步驟會標記要備份的記錄檔，然後加以備份。  
  
    > [!IMPORTANT]
    >  若要避免資料遺失， *\<目的地路徑 >*應該指定的電腦不同的電腦與原始資料庫記錄檔來儲存資料庫記錄檔。  
  
     選取 [確定]。  
  
7.  選取 **清除備份歷程記錄** 步驟，再選取 [編輯] 。 在**命令**方塊中，變更**DaysToKeep =***\<數字 >*您想要保留備份歷程記錄的天數：  
  
    ```  
    exec [dbo].[sp_DeleteBackupHistory] @DaysToKeep=14  
    ```  
  
    > [!NOTE]
    >  **DaysToKeep** 參數指定在 Adm_BackupHistory 資料表中保存備份歷程記錄的時間。 定期清除備份歷程記錄，有助於保持 Adm_BackupHistory 資料表的適當大小。 **DaysToKeep** 參數的預設值為 14 天。  
  
     選取 [確定]  ，然後關閉所有的屬性視窗。  
  
8.  選擇性。 變更備份排程。 請參閱[如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md)。  
  
    > [!NOTE]
    >  「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業會在您第一次設定時執行。 在後續的執行中，「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業依預設會每天執行一次完整備份，並且每 15 分鐘執行一次記錄備份。  
  
9. 在 **備份 BizTalk Server** 作業上按一下滑鼠右鍵，然後選取 [啟用] 。 狀態應該變更為 **成功**。  
  
## <a name="spforcefullbackup-stored-procedure"></a>sp_ForceFullBackup 預存程序  
  
> [!NOTE]
>  BizTalkMgmtDb 資料庫中的 sp_ForceFullBackup 預存程序可用於協助執行資料與記錄檔的特定完整備份。 此預存程序會以值 1 更新 adm_ForceFullBackup 資料表。 在下一次備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行作業時，會建立完整資料庫備份組。  
  
## <a name="next-steps"></a>後續步驟  
 [如何設定記錄傳送目的地系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)  
  
## <a name="see-also"></a>另請參閱  
 [如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md)