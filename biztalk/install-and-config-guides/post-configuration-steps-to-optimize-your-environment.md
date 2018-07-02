---
title: 後續設定步驟進行環境最佳化 |Microsoft Docs
description: 工作完成之後安裝並設定 BizTalk Server 中，包括設定 SQL Agent 作業、 安裝 EDI 結構描述、 建立主控件和主控件執行個體，以及 BizTalk Server 中的其他資訊
ms.custom: ''
ms.prod: biztalk-server
ms.date: 09/27/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0fef6ea-e7cc-4ea9-936d-5d638bc43feb
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51f78d561af0c7ebe1212bffe79c862a16d0a512
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986143"
---
# <a name="post-configuration-steps-to-optimize-your-environment"></a>環境最佳化的後續設定步驟
協助改善效能、維護 BizTalk 環境，以及安裝 EDI 結構描述的設定後續作業步驟。

## <a name="disable-shared-memory-protocol-in-sql-server"></a>停用 SQL Server 的共用記憶體通訊協定

1. 開啟 **SQL Server 組態管理員**。
2. 展開 [SQL Server 網路組態]，然後選取 [Protocols for MSSQLSERVER (MSSQLSERVER 的通訊協定)]。
3. 以滑鼠右鍵按一下 [共用記憶體]，然後選取 [停用]。
4. 選取 [SQL Server 服務]，再用滑鼠右鍵按一下 [SQL Server (MSSQLServer)]，然後選取 [重新啟動]。
5. 關閉 **SQL Server 組態管理員**。

## <a name="configure-the-sql-agent-jobs"></a>設定 SQL Agent 作業

1. **SQL Server Management Studio**，並連接到 **Database Engine**。
2. 展開 [SQL Server Agent]，再展開 [作業]。 設定下列作業：  

    作業名稱  |描述  |為何需要它  
    ---------|---------|---------
    備份 BizTalk Server | 備份 BizTalk Server 資料庫和記錄檔。 設定作業時，您可以決定頻率和檔案位置等參數。<br/><br/>下列連結會說明 SQL Agent 作業和其參數︰<br/><br/>[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)<br/>[如何設定備份 BizTalk Server 作業](../core/how-to-configure-the-backup-biztalk-server-job.md)|此 SQL Agent 作業也會截斷交易記錄檔，有利改善效能。<br/><br/>這項作業不會移除或刪除備份檔案，包括較舊的檔案。 若要刪除備份檔案，請參照 Microsoft BizTalk Server 資料庫伺服器與時俱增的備份檔案中失敗的「備份 BizTalk Server」作業。
    DTA 清除與封存 |截斷並封存 BizTalk Server 追蹤資料庫 (BizTalkDTADb)。 設定作業時，您可以決定已完成執行個體的保留天數以及所有資料的保留天數等參數。<br/><br/>下列連結會說明 SQL Agent 作業和其參數︰ <br/><br/>[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)<br/>[如何設定 DTA 清除與封存作業](../core/how-to-configure-the-dta-purge-and-archive-job.md)|此 SQL Agent 工作維護追蹤主機以及清除追蹤事件，而直接影響效能。

## <a name="maintain-your-backup-files"></a>維護備份檔案

BizTalk Server 不包含任何刪除備份檔案的作業。 所以，如何維護備份檔是由您決定。 許多使用者會建立 sp_DeleteBackupHistoryAndFiles 預存程序，然後直接在備份 BizTalk Server 作業中呼叫此預存程序。 有些使用者則是建立維護計畫。 由您作主。 本主題列出這兩個選項。

#### <a name="option-1-create-the-spdeletebackuphistoryandfiles-stored-procedure"></a>選項 1︰建立 sp_DeleteBackupHistoryAndFiles 預存程序

1. 在 SQL Server Management Studio 中，選取 BizTalk 管理資料庫 (BizTalkMgmtDb)。 
2. 選取 [新增查詢]，並執行下列 T-SQL 指令碼建立 sp_DeleteBackupHistoryAndFiles 預存程序︰ 

    ```
    CREATE PROCEDURE [dbo].[sp_DeleteBackupHistoryAndFiles] @DaysToKeep smallint = null
    AS

    BEGIN
    set nocount on
    IF @DaysToKeep IS NULL OR @DaysToKeep <= 1
    RETURN
    /*
    Only delete full sets
    If a set spans a day in such a way that some items fall into the deleted group and the other does not, do not delete the set
    */

    DECLARE DeleteBackupFiles CURSOR
    FOR SELECT 'del "' + [BackupFileLocation] + '\' + [BackupFileName] + '"' FROM [adm_BackupHistory]
    WHERE  datediff( dd, [BackupDateTime], getdate() ) >= @DaysToKeep
    AND [BackupSetId] NOT IN ( SELECT [BackupSetId] FROM [dbo].[adm_BackupHistory] [h2] WHERE [h2].[BackupSetId] = [BackupSetId] AND datediff( dd, [h2].[BackupDateTime], getdate() ) < @DaysToKeep )

    DECLARE @cmd varchar(400)
    OPEN DeleteBackupFiles
    FETCH NEXT FROM DeleteBackupFiles INTO @cmd
    WHILE (@@fetch_status <> -1)
    BEGIN
        IF (@@fetch_status <> -2)
        BEGIN
            EXEC master.dbo.xp_cmdshell @cmd, NO_OUTPUT
            delete from [adm_BackupHistory] WHERE CURRENT OF DeleteBackupFiles
            print @cmd
        END
        FETCH NEXT FROM DeleteBackupFiles INTO @cmd
    END

    CLOSE DeleteBackupFiles
    DEALLOCATE DeleteBackupFiles
    END
    GO
    ```

3. 開啟 [備份 BizTalk Server] 作業，然後選取 [步驟]。
4. 編輯**清除備份記錄**步驟，讓它呼叫新的 *sp_DeleteBackupHistoryAndFiles* 預存程序，而不是原先的 *sp_DeleteBackupHistory* 預存程序。
5. 選取 [確定] 儲存您的變更。

#### <a name="option-2-create-a-maintenance-plan"></a>選項 2：建立維護計畫

1. 在 SQL Server Management Studio 中，展開 [管理]，以滑鼠右鍵按一下 [維護計畫]，然後選取 [維護計畫精靈]。
2. 命名計劃 (例如，將它命名為「清除備份檔案」)，然後選取 [排程] 旁的 [變更] 按鈕。
3. 選擇您想要的備份檔案清除頻率。 這些設定完全由您決定。 依序選取 [確定] 和 [下一步]。
4. 選取 [維護清除工作]，然後選取 [下一步]。
5. 在 [Cleanup Task (清除工作)] 視窗中，移至 [Search folder and delete files... (搜尋資料夾及刪除檔案)]，選取您的備份資料夾 (可能是 f:\BizTalkBackUps)，然後輸入 **.bak** 副檔名。 您也可以選擇依據檔案存在時間刪除檔案。 例如，如果想要刪除存在時間超過 3 週的檔案，輸入 3。 選取 **[下一步]**。
6. 完成執行精靈，並輸入您想要的任何其他資訊。 選取 [完成]。


## <a name="install-edi-schemas-and-more-edi-as2-configuration"></a>安裝 EDI 結構描述及更多的 EDI AS2 設定
 EANCOM、EDIFACT、HIPAA 和 X12 結構描述檔案都包含在名為 MicrosoftEdiXSDTemplates.exe 的自動解壓縮可執行檔中。 若要建立 EDI 解決方案，請解壓縮這些檔案，並使用您的專案部署。 安裝並解壓縮這些檔案︰  

1. 執行 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] 安裝，然後安裝**開發者工具與 SDK** 元件。 此元件會將 MicrosoftEdiXSDTemplates.exe EDI 結構描述檔案下載至 \XSD_Schema\EDI 資料夾中。  

   > [!NOTE]
   > 如果升級 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，原安裝中的 MicrosoftEdiXSDTemplates.exe 檔案會替換成與升級相關聯的新 MicrosoftEdiXSDTemplates.exe 檔案。 如果需要原先的結構描述，請備份先前的 MicrosoftEdiXSDTemplates.exe 檔案。  
   > 
   > [!NOTE]
   > 如果您在將 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] 升級到更新的組建時升級了訊息結構描述，您可能會在使用更新過的結構描述時遇到問題，或是您可能必須執行其他的更新步驟。 請參閱[更新應用程式的重要考量](../core/important-considerations-for-updating-applications.md)的＜更新結構描述的考量＞一節。

2. 移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\XSD_Schema\EDI，並按兩下 MicrosoftEdiXSDTemplates.exe。  

3. 將結構描述解壓縮至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\XSD_Schema\EDI。 當您解壓縮結構描述時，它們會儲存在 EANCOM、EDIFACT、HIPAA 和 X12 資料夾中。  

#### <a name="add-a-reference-to-the-biztalk-server-edi-application"></a>加入 BizTalk Server EDI 應用程式的參考  
 EDI 結構描述、管線及協調流程會部署在 **BizTalk EDI 應用程式**中。 若要將任何其他應用程式用為 EDI 應用程式，請加入 **BizTalk EDI 應用程式**的參考。 步驟：  

1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，展開 [應用程式]。 以滑鼠右鍵按一下您想要用於 EDI 的應用程式 (例如 *BizTalk Application 1*)，選取 [新增], ，然後選取 [參考]。  

2. 選取 [BizTalk EDI 應用程式]，然後選取 [確定] 儲存變更。  

> [!TIP]
>  若要查看其他應用程式的參考，請以滑鼠右鍵按一下任何應用程式，然後選取 [內容]。 選取 [參考]。 您也可以加入新的參考，然後移除現有的參考。  

> [!NOTE]
>  請勿將自訂成品加入 [BizTalk EDI 應用程式] 中。 此應用程式最好保持原樣。  

#### <a name="start-batch-orchestrations"></a>啟動批次協調流程  
 如果您讓合作對象啟用接收及/或傳送 EDI 批次功能，您就必須啟動批次協調流程。 這些協調流程不會由安裝精靈或組態精靈啟動。 步驟：  

1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，展開 [BizTalk EDI 應用程式]，然後選取 [協調流程]。  

2. 以滑鼠右鍵按一下下列每個協調流程，然後選取 [啟動]：  

   -   Microsoft.BizTalk.Edi.BatchSuspendOrchestration.BatchElementSuspendService (組件：Microsoft.BizTalk.Edi.BatchingOrchestration.dll)  

   -   Microsoft.BizTalk.Edi.BatchingOrchestration.BatchingService (組件：Microsoft.BizTalk.Edi.BatchingOrchestration.dll)  

   -   Microsoft.BizTalk.Edi.RoutingOrchestration.BatchRoutingService (組件：Microsoft.BizTalk.Edi.RoutingOrchestration.dll)  

> [!NOTE]
>  只有在您接收及/或傳送 EDI 批次時，這些 EDI 批次處理協調流程才會啟動。 若是在系統不是正在接收或傳送 EDI 批次時啟動這些協調流程，可能會影響系統效能。  

#### <a name="migrate-edi-artifacts-from-a-previous-biztalk-version"></a>從舊版 BizTalk 移轉 EDI 成品  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 及較新版本已更新在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中管理交易夥伴的方式。 在上一版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，只能為交易夥伴建立合作對象，不能為主控 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的夥伴建立。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 及更新版本中，必須為所有的交易夥伴，包括主控 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的夥伴建立合作對象。 上一版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是在合作對象層級定義編碼 (X12 和 EDIFACT) 與傳輸 (AS2) 通訊協定內容。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 及更新版本是透過協議定義這些內容。  

 若要從舊版移轉合作對象資料，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 要有合作對象移轉工具。 請考慮下列移轉路徑︰  


| [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 版本  |                                                                                                                                                                                                                                                                                                                                     移轉路徑                                                                                                                                                                                                                                                                                                                                      |
|---------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]**       | 升級到 BizTalk Server 2009。 然後，使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2 隨附的合作對象移轉工具移轉至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2。<br /><br /> **或者**，使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2 隨附的合作對象移轉工具移轉至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010。 接著，升級到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2。 |
| **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009** |                                                                                                                                                                                                           使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2 隨附的合作對象移轉工具直接移轉至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2。                                                                                                                                                                                                            |
| **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010** |                                                                                                                                                                                                                                                                                       升級至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2。                                                                                                                                                                                                                                                                                       |

 合作對象移轉工具位於 \PartyMigrationTool 資料夾下的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 媒體中。  


## <a name="install-biztalk-health-monitor-bhm"></a>安裝 BHM 狀況監控 (BHM)

BHM 狀況監控提供儀表板，以建立及檢視 MessageBox 檢視器報表、建立自訂查詢、執行結束字元工作、監視多個 BizTalk 環境等等。 如果您負責 BizTalk 環境，建議您安裝並使用此工具來檢查與維護 BizTalk 環境的狀況。

重要連結：

[下載 BHM](https://www.microsoft.com/download/details.aspx?id=43716)  
[安裝 BHM](http://social.technet.microsoft.com/wiki/contents/articles/26466.biztalk-server-how-to-install-the-new-biztalk-health-monitor-snap-in.aspx)  
[BHM 官方部落格](https://blogs.msdn.microsoft.com/biztalkhealthmonitor/)

## <a name="create-your-hosts-and-host-instances"></a>建立您的主控件與主控件執行個體
建議將重要的工作分成不同的主控件。 例如，一律分別建立專門用於追蹤的主控件。 建立專門接收訊息的另一個主控件/主控件執行個體、傳送訊息的另一個主控件/主控件執行個體，以及用於協調流程的另一個主控件/主控件執行個體。 

有很多關於這方面的建議。 下面這些可以讓您快速上手︰ 

[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)  
[為 BizTalk 主控件提供高可用性](../core/providing-high-availability-for-biztalk-hosts.md)  
[BizTalk Server Best Practices: Create and Configure BizTalk Server Host and Host Instances](http://social.technet.microsoft.com/wiki/contents/articles/19701.biztalk-server-best-practices-create-and-configure-biztalk-server-host-and-host-instances.aspx) (BizTalk 伺服器的最佳做法︰建立與配置 BizTalk Server 主控件和主控件執行個體)  
[BizTalk Server: Running Orchestrations in Multiple Hosts on the Same Computer](http://social.technet.microsoft.com/wiki/contents/articles/31183.biztalk-server-running-orchestrations-in-multiple-hosts-on-the-same-computer.aspx) (在同一部電腦的多個主控件中執行協調流程)  
[PowerShell 建立和設定 BizTalk Server 主控件、 主控件執行個體和處理常式](https://gallery.technet.microsoft.com/PowerShell-to-Configure-43d77916)  
[BizTalk Server Resources on the TechNet Wiki](http://social.technet.microsoft.com/wiki/contents/articles/2240.biztalk-server-resources-on-the-technet-wiki.aspx) (TechNet Wiki 上的 BizTalk Server 資源)
