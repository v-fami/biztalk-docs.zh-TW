---
title: "設定 「 備份 BizTalk Server 」 工作 |Microsoft 文件"
description: 
ms.custom: 
ms.date: 11/22/2017
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
ms.openlocfilehash: f1afb4f28584d65401220761dcee626fe63f913b
ms.sourcegitcommit: f4c0d7bc4b617688c643101a34062db90014851a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2017
---
# <a name="configure-the-backup-biztalk-server-job"></a>設定 「 備份 BizTalk Server 」 工作
安裝和設定 BizTalk Server 之後，設定備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業來備份您的資料。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，您可以備份您的資料庫和記錄檔加入至 Azure blob 儲存體帳戶。 


## <a name="overview"></a>概觀
**備份 BizTalk Server (BizTalkMgmtDb)**工作包含下列步驟：

-   步驟 1 –**集壓縮選項**： 啟用或停用備份期間的壓縮

-   步驟 2 – **BackupFull**： 執行完整資料庫備份 BizTalk Server 資料庫

-   步驟 3 – **MarkAndBackUpLog**： 備份 BizTalk Server 資料庫記錄檔

-   步驟 4 –**清除備份歷程記錄**： 選擇 備份歷程記錄保留的時限

若要設定這項作業，您將需要：  
  
-   識別主要和目的地 SQL 伺服器和其他備份選項
  
-   選擇 Windows 使用者帳戶來備份您的資料庫，並建立此帳戶的 SQL Server 登入
  
-   將 SQL Server 登入對應至 BizTalk Server 資料庫中的 BTS_BACKUP_USERS 資料庫角色
  
-   確定所有節點上的 MSDTC 服務都在作用中。 否則，新增連結的伺服器之間的來源節點與目的節點會失敗。
  
## <a name="before-you-begin"></a>開始之前  
  
-   某些組態和備份作業需要 sysadmin SQL Server 角色的成員資格。 若要備份您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，登入主要伺服器是 SQL Server sysadmin 伺服器角色的成員的帳戶。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態會加入 BTS_BACKUP_USERS 資料庫角色。 您用來備份資料庫的使用者帳戶不需要可能包含在備份中，除了主要伺服器的所有 SQL 伺服器上的系統管理員 （sysadmin SQL Server 角色） 權限。  
  
-   決定哪些登入帳戶您用來執行您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫備份。 您可以使用本機帳戶，您可以使用多個帳戶。 但通常更簡單，而且專用於此用途建立一個專用的 Windows 網域使用者帳戶更安全。 您必須為此使用者設定 SQL Server 登入帳戶，而且此使用者必須對應到所有參與備份程序的主要 (來源) 或次要 (目的地) SQL Server 的 SQL Server 登入。 將此使用者指派給 BizTalk BTS_BACKUP_USERS 資料庫角色，每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您資料庫備份。  
  
-   備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 作業不會刪除過期的備份檔案，所以您必須手動管理這些備份檔案以回收磁碟空間。 在為資料庫建立新的完整備份後，您應該將過期的備份檔案移動到封存儲存裝置以回收主要磁碟上的空間。 請參閱[SSIS 封裝](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/)管理這些檔案。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不會寫入追蹤資料直接 BizTalk 追蹤資料庫;它會快取 MessageBox 資料庫中的資料而然後將它移到 BizTalk 追蹤資料庫。 如果發生 MessageBox 資料遺失，可能會遺失部分追蹤資料。  
  
## <a name="prerequisites"></a>必要條件  
* 使用屬於 sysadmin SQL Server 角色的成員帳戶的 SQL Server 登入。  
  
* 您必須將 SQL Server Agent 服務設定成以網域帳戶執行 (雖然可以使用本機帳戶，但建議採用此方式)，並為每個 SQL Server 執行個體上設定一個對應的使用者登入。  

* 若要使用的 Azure blob 儲存體帳戶，您需要[一般用途儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account)，blob 儲存體帳戶內的容器[共用的存取簽章](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#SAS)(SAS)，和[SQL 認證使用 SAS](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#credential)。 一旦建立之後，擁有 blob 服務端點 URL 好時，這不是像 https://*yourstorageaccount*.blob.core.windows.net/*containername*。 

    > [!TIP]
    > 如果您沒有現有的 blob 儲存體帳戶的 SAS，以設定則[SAS PowerShell 指令碼](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#SAS)可以建立，且容器。 [SQL Server 備份至 URL](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url)提供概觀，以及特定的步驟。
  
## <a name="configure-the-job"></a>設定工作  
  
1.  在裝載 BizTalk 管理資料庫的 SQL Server 上開啟**SQL Server Management Studio**，並連接到您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
2.  展開 [SQL Server Agent] ，再展開 [作業] 。  
  
3.  在 [備份 BizTalk Server (BizTalkMgmtDb)]  上按一下滑鼠右鍵，然後選取 [屬性] 。 在作業屬性中，選取 [步驟] 。  
  
4.  選取**設定壓縮選項**逐步執行和選取**編輯**:  

    這個步驟就會呼叫`sp_SetBackupCompression`預存程序中設定的值上的 BizTalk 管理資料庫 (BizTalkMgmtDb)`adm_BackupSettings`資料表。 預存程序有一個參數：  **@bCompression** 。 根據預設，它設定為**0** （備份壓縮已關閉）。 若要套用壓縮，將值變更為**1**:  
  
    ```  
    exec [dbo].[sp_SetBackupCompression] @bCompression = 1 /*0 - Do not use Compression, 1 - Use Compression */  
    ```  
  
     選取 [確定]。  
  
5.  選取**BackupFull**逐步執行和選取**編輯**。 在**命令**方塊中，更新的參數值：  
  
    1. **頻率**： 預設值是**d** （每日）; 這是建議的設定。 其他值包括 **h** (每小時)、 **w** (每週)、 **m** (每月)、或 **y** (每年)。  
  
    2. **名稱**：預設值是 **[BTS]**。 這個名稱會用來做為備份檔案名稱的一部分。  
  
    3. **備份檔案的位置**： 取代 '*\<目的地路徑 >*' 的電腦與您想要備份的目的地資料夾的完整路徑 （此路徑必須包含單引號） [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫或 Azure blob 儲存體帳戶的 blob 服務端點 URL。  

        > [!IMPORTANT]
        > - 如果您輸入的本機路徑，則您必須手動將所有檔案都複製到目的系統上相同的資料夾時備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業建立新檔案。  
        >   
        >      若要使用遠端路徑，請輸入 UNC 共用例如\\ \\  *\<ServerName >*\\*\<所 >*\\，其中 *\<ServerName >*是您要檔案伺服器的名稱和*\<所 >*是共用磁碟機或資料夾的名稱。  
        >   
        >      透過網路備份資料可能會因為網路問題而受限。 當使用遠端位置，驗證備份成功時備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業結束。  
        > - 若要避免資料遺失，請將備份磁碟設定為資料庫資料與記錄磁碟以外的其他磁碟。 此做法可確保您在資料或記錄磁碟故障時存取備份。  
        > - 當備份至 Azure blob 帳戶中，輸入**Blob 服務端點**URL 和容器名稱，在 blob 服務屬性中所列[Azure 入口網站](https://portal.azure.com)。

    4. 選擇性。 **部分備份失敗之後強制完整備份**(@ForceFullBackupAfterPartialSetFailure): 預設值是**0**。 如果記錄備份失敗時，到達下一個完整備份頻率間隔之前，會不執行任何完整備份。 取代為**1**如果您想要的完整備份執行記錄檔備份失敗時。
    
    5. 選擇性。 **若要執行備份程序的本地小時時間**(@BackupHour): 預設值是**NULL**。 備份作業不是相關聯的時區時間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，並會在午夜 UTC 時間 (0000)。 如果您想要備份的時區中的特定時間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上，輸入一個整數值 0 （午夜） 到 23 （晚上 11 點） 為本地小時時間。 

    6. 選擇性。 **使用本地時間**(@UseLocalTime): 會告知使用本地時間的程序。 預設值是**0**，並使用目前的 UTC 時間 – getutcdate （） – 2007年-05-04 01:34:11.933。 如果設定為**1**，然後它會使用當地時間 – getdate （） – 2007年-05-03 18:34:11.933
  
    在下列範例中，會建立上午 2 執行，每日備份，並將其儲存在 m:\ 磁碟機中：  
  
    ```  
    exec [dbo].[sp_BackupAllFull_Schedule]   
    'd' /* Frequency */,   
    'BTS' /* Name */,   
    'm:\BizTalkBackups' /* location of backup files */,   
    '0' /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */,   
    '2' /* local time hour for the backup process to run */  
    ```  

    在下列範例中，每週備份會在午夜 UTC 時間，建立和儲存在您的 Azure blob 帳戶： 

    ```  
    exec [dbo].[sp_BackupAllFull_Schedule]   
    'w' /* Frequency */,   
    'BTS' /* Name */,   
    'http://yourstorageaccount.blob.core.windows.net/yourcontainer/' /* location of backup files */,   
    '1' /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */
    ```  

     選取 [確定]。  
  
6.  選取**MarkAndBackupLog**逐步執行和選取**編輯**。 在**命令**方塊中，更新的參數值：  
  
    1.  **@MarkName**： 這是備份檔案的命名慣例： <Server Name>  _<Database Name> **_記錄_**< 記錄標示名稱 >_<Timestamp>  
    
    2.  **@BackupPath**： 完整目的地路徑 （包含單引號） 之電腦和資料夾來儲存[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫記錄檔，或 Azure blob 儲存體帳戶和容器。 *\<目的地路徑 >*也可以是本機或另一部伺服器的 UNC 路徑。  
  
     MarkAndBackupLog 步驟會標記要備份的記錄檔，然後加以備份。  
  
    > [!IMPORTANT]
    >  若要避免**潛在資料遺失**和**效能改進**、 *\<目的地路徑 >*應該設定為不同的電腦或硬碟機，不同於並用來儲存原始的資料庫記錄檔。  
  
     選取 [確定]。  
  
7.  選取**清除備份歷程記錄**逐步執行和選取**編輯**。 在**命令**方塊中，更新的參數值：  
  
    1.  **@DaysToKeep**： 預設值是**14 天**。 決定要備份的記錄會保留`Adm_BackupHistory`資料表。 定期清除備份歷程記錄可協助維護`Adm_BackupHistory`資料表，以適當的大小。 
    
    2.  選擇性。 **@UseLocalTime**： 會告知使用本地時間的程序。 預設值是 0。 它會使用目前的 UTC 時間 – getutcdate （） – 2007年-05-04 01:34:11.933。 如果設為 1，然後它會使用當地時間 – getdate （） – 2007年-05-03 18:34:11.933
  
    ```  
    exec [dbo].[sp_DeleteBackupHistory] @DaysToKeep=14, @UseLocalTime =1 
    ```  
  
    > [!NOTE]
    >  此步驟**不**刪除備份檔案的目的地路徑。  
    
     選取 [確定]  ，然後關閉所有的屬性視窗。  
  
8.  選擇性。 變更備份排程。 請參閱[如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md)。  
  
    > [!NOTE]
    >  「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業會在您第一次設定時執行。 根據預設，在後續執行中，備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業完成的完整備份一天一次，並完成每隔 15 分鐘的記錄備份。  
  
9. 以滑鼠右鍵按一下**備份 BizTalk Server**作業，然後選取**啟用**。 狀態應該變更為 **成功**。  

## <a name="execute-backupsetupallprocssql-and-logshippingdestinationlogicsql"></a>執行 Backup_Setup_All_Procs.sql 和 LogShipping_Destination_Logic.sql

**[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]功能 Pack 2 (FP2)**使用中的 Backup_Setup_All_Procs.sql 和 LogShipping_Destination_Logic.sql 指令碼`\Program Files (x86)\Microsoft BizTalk Server *your version*\Schema`。 

如果已設定備份 BizTalk Server 作業，而且您想要切換使用 Azure blob （而不是磁碟），則也請執行下列： 

1. SQL Server 上執行`Backup_Setup_All_Procs.sql`針對所要備份的 「 備份 BizTalk Server 」 工作的所有自訂資料庫的指令碼。 根據預設，FP2 自動更新 BizTalk 資料庫;不會更新任何自訂的資料庫 (在這些資料庫`adm_OtherBackupDatabases`BizTalkMgmtDb 中的資料表)。

    [備份自訂資料庫](how-to-back-up-custom-databases.md)自訂資料庫提供更多詳細資料。 

2. **如果您使用[記錄傳送](log-shipping.md)**，SQL Server 中的目的地系統上執行 LogShipping_Destination_Logic.sql 指令碼。 如果您不使用記錄傳送，則不會執行此指令碼。

    [設定記錄傳送的目的系統](how-to-configure-the-destination-system-for-log-shipping.md)目的系統上提供更多詳細資料。

## <a name="spforcefullbackup-stored-procedure"></a>sp_ForceFullBackup 預存程序  
  
**Sp_ForceFullBackup**預存程序中的**BizTalkMgmtDb**資料庫可以用來執行特定的資料和記錄檔的完整備份。 此預存程序會以值 1 更新 adm_ForceFullBackup 資料表。 在下一次備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行作業時，會建立完整資料庫備份組。  
  
## <a name="next-steps"></a>後續步驟  
 [設定記錄傳送的目的系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)   
 [排程備份 BizTalk Server 作業](../core/how-to-schedule-the-backup-biztalk-server-job.md)  
 [Azure 儲存體帳戶](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)  
 [SQL Server 備份至 URL](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url)
