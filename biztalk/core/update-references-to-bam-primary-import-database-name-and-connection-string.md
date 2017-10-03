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
# <a name="how-to-update-references-to-the-bam-primary-import-database-name-and-connection-string"></a>如何更新 BAM 主要匯入資料庫名稱和連接字串的參考
如果您已備份 BAMPrimaryImport 資料庫發生系統或資料失敗時，可以將該備份還原至不同的電腦，並重新命名此備份。  
  
 BAM 事件匯流排服務會將事件資料從 MessageBox 資料庫移到 BAMPrimaryImport 資料庫。 BAM 事件匯流排服務包含容錯邏輯，可讓它從意外的失敗中復原和重新啟動，而不會遺失任何資料。 如需有關 BAM 事件匯流排服務的詳細資訊，請參閱[管理 BAM 事件匯流排服務](../core/managing-the-bam-event-bus-service.md)。  
  
 若要還原 BAMPrimaryImport 資料庫，執行中的步驟[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。 此外，您也必須執行下列一般步驟，各步驟之後都有詳細說明步驟的程序：  
  
-   更新所有 BAM DTS 封裝中的「SQL 連線 1」，以參考新的資料庫名稱。  
  
-   以新的資料庫名稱更新 web.config 檔案。  
  
-   在所有 BAM Livedata Microsoft Excel 檔案中更新 BAMPrimaryImport 資料庫的參考。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 BizTalk Server 系統管理員群組的成員身分登入，才能執行這個程序。  
  
### <a name="to-update-references-to-the-bamprimaryimport-database-name-and-connection-string"></a>若要更新 BAMPrimaryImport 資料庫的名稱和連接字串的參考  
  
1.  停止任何 BAM cube 更新及資料維護 Data Transformation Services (DTS) 封裝，或防止它們執行，直到您完成 BAMPrimaryImport 資料庫的還原。  
  
2.  停止 BizTalk 應用程式服務 (包括 BAM 事件匯流排服務)，以避免其嘗試將更多資料匯入至資料庫。  
  
    1.  按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。  
  
    2.  以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後按一下**停止**。  
  
3.  BAMPrimaryImport 資料庫，執行中的步驟還原[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。  
  
4.  更新下列 Web.Config 檔案：  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BamManagementService\Web.Config。  
  
         取代 *\<ServerName >*新的伺服器名稱的字串和 *\<DatabaseName >*與新的資料庫名稱。 更新下列連接字串：  
  
         \<appSettings >  
  
         < 新增機碼 ="BamServer"value ="*\<ServerName >*"/\>  
  
         < 新增機碼 ="BamDatabase"value ="*\<DatabaseName >*"/\>  
  
         \<加入機碼 ="MaxResultRows"value ="2000"/ >  
  
         \</appSettings >  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BamQueryService\Web.Config。  
  
         取代 *\<ServerName >*新的伺服器名稱的字串和 *\<DatabaseName >*與新的資料庫名稱。 更新下列連接字串：  
  
         \<appSettings >  
  
         < 新增機碼 ="BamServer"value ="*\<ServerName >*"/\>  
  
         <add key="BamDatabase" value="*<DatabaseName>*" />  
  
         <add key="MaxResultRows" value="2000" />  
  
         </appSettings>  
  
5.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
6.  瀏覽至下列目錄： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore。  
  
7.  以滑鼠右鍵按一下**SampleUpdateInfo.xml**，然後按一下 **編輯**。  
  
    1.  將除了 BizTalkMgmtDb、OldPrimaryImportDatabase、PrimaryImportDatabase、ArchivingDatabase、AnalysisDatabase、StarSchemaDatabase 和 Alert 以外的所有資料庫區段標記為註解。  
  
    2.  BizTalkMgmtDb、 OldPrimaryImportDatabase、 PrimaryImportDatabase、 ArchivingDatabase、 AnalysisDatabase、 StarSchemaDatabase 和 Alert 區段，將**"SourceServer"**和**"Destination Server"**這些資料庫所在的現有伺服器的名稱。  
  
    3.  Primaryimportdatabase 中，設定**"SourceServer"**移動 BAM 主要匯入資料庫伺服器的名稱。  
  
        > [!IMPORTANT]
        >  在來源及目的系統的名稱兩端加上引號。  
  
        > [!NOTE]
        >  如果重新命名了任何 BizTalk Server 資料庫，您也必須視情況適當更新資料庫名稱。  
  
    4.  完成檔案的編輯後，請加以儲存並結束。  
  
8.  在命令提示字元中，輸入：  
  
     **cscript UpdateDatabase.vbs SampleUpdateInfo.xml**  
  
    > [!NOTE]
    >  您只需執行 UpdateDatabase.vbs 一次。  
  
    > [!NOTE]
    >  在 64 位元電腦上，您必須從 64 位元命令提示字元中執行 UpdateDatabase.vbs。  
  
9. 在命令提示字元中，瀏覽至下列目錄：  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
10. 在命令提示字元，編輯 bm.exe.config、將 key="DefaultServer" 的值變更為伺服器名稱，然後儲存檔案。  
  
11. 在所有 BAM Livedata Microsoft Excel 檔案中更新 BAMPrimaryImport 資料庫的參考。 對於每個檔案：  
  
    1.  開啟 Excel 即時資料檔案。 此檔案名稱是以 _LiveData.xls 結尾。  
  
    2.  在**BAM**功能表上，按一下  **BAM DB 連線**。  
  
    3.  在**選取 BAM 資料庫**對話方塊中，輸入 SQL Server 和 BAMPrimaryImport 資料庫，然後按一下**確定**。  
  
    4.  在**檔案**功能表上，按一下 **關閉並返回 Microsoft Excel**。  
  
    5.  在 [檔案] 功能表上，按一下 [儲存]。  
  
12. 重新啟動 BizTalk 應用程式服務。  
  
    1.  按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。  
  
    2.  以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後按一下**啟動**。  
  
13. 啟用任何 BAM Cube 更新和資料維護 DTS 封裝。  
  
14. 若要解決任何不完整的追蹤執行個體，請參閱[如何解析未完成的活動執行個體](../core/how-to-resolve-incomplete-activity-instances.md)。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原 BAM](../core/backing-up-and-restoring-bam.md)