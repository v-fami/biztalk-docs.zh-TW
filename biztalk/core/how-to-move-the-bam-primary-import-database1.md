---
title: 如何移動 BAM 主要匯入 Database1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migrating, Primary Import database [BAM]
- Primary Import database [BAM], migrating
ms.assetid: fab13fea-5c35-4a9f-977d-cc45545c54b2
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff5caa9120be64e919ab4b6050f8df0c62fa33a6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010607"
---
# <a name="how-to-move-the-bam-primary-import-database"></a>如何移動 BAM 主要匯入資料庫
您可以使用這個程序，將 BAM 主要匯入資料庫移動到其他伺服器。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-move-the-bam-primary-import-database"></a>移動 BAM 主要匯入資料庫  
  
1. 停止所有 BizTalk Server 服務。 如需詳細資訊，請參閱 <<c0> [ 如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。  
  
2. 停止 IIS 服務。  
  
3. 停止 BAM 警示 Notification Service：  
  
   1.  按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
   2.  在命令提示字元中，輸入：  
  
       ```  
       Net stop NS$BamAlerts  
       ```  
  
4. 依照 SQL Server 線上叢書 》 中的指示，備份舊伺服器上的 BAM 主要匯入資料庫。  
  
5. 將 BAM 主要匯入資料庫複製到新的 SQL Server。  
  
6. 依照 SQL Server 線上叢書 》 中的指示，將 BAM 主要匯入資料庫，新的伺服器上還原。  
  
7. 在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的電腦中，瀏覽至下列資料夾：  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore  
  
8. 以滑鼠右鍵按一下**SampleUpdateInfo.xml**，然後按一下**編輯**。  
  
9. 在主要匯入資料庫區段中的檔案，取代 **"SourceServer"** 然後取代與來源系統的名稱取代 **"DestinationServer"** 目的系統的名稱。  
  
    > [!IMPORTANT]
    >  在來源及目的系統的名稱兩端加上引號。  
  
    > [!NOTE]
    >  如果重新命名了任何 BizTalk Server 資料庫，您也必須視情況適當更新資料庫名稱。  
  
10. 取消在 XML 檔案中下列幾行的註解標記：  
  
    ```  
    - <UpdateConfiguration>  
      <MessageBoxDB oldDBName="BizTalkMsgboxDb" oldDBServer="Server01" newDBName="BizTalkMsgboxDb" newDBServer="Server01" IsMaster="1" />   
      <TrackingDB oldDBName="BizTalkDTADb" oldDBServer="Server01" newDBName="BizTalkDTADb" newDBServer="Server01" />   
      <ManagementDB oldDBName="BizTalkMgmtDb" oldDBServer="Server01" newDBName="BizTalkMgmtDb" newDBServer="Server01" />   
    - <BAM>  
    - <DeploymentUnit Name="OldPrimaryImportDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMPrimaryImport</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="PrimaryImportDatabase">  
      <Property Name="ServerName">Server02</Property>   
      <Property Name="DatabaseName">BAMPrimaryImport</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="ArchivingDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMArchive</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="AnalysisDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMAnalysis</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="StarSchemaDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMStarSchema</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="Alert">  
      <Property Name="DBServer">Server01</Property>   
      <Property Name="InstanceDatabaseName">BAMAlerts</Property>   
      </DeploymentUnit>  
      </BAM>  
    - <OtherDatabases>  
      <Database Name="SSO" oldDBName="SSODB" oldDBServer="Server01" newDBName="SSODB" newDBServer="Server01" />   
      </OtherDatabases>  
      </UpdateConfiguration>  
    ```  
  
11. 完成檔案的編輯後，請加以儲存並結束。  
  
12. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
13. 在命令提示字元中，瀏覽至下列目錄：  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore  
  
14. 在命令提示字元中，輸入：  
  
     **cscript UpdateDatabase.vbs SampleUpdateInfo.xml**  
  
15. 更新 BAM 主要匯入資料庫在所有 BAM Livedata Microsoft Excel 檔案中的參考。 對於每個檔案：  
  
    1.  開啟 Excel 即時資料檔案。 此檔案名稱是以 _LiveData.xls 結尾。  
  
    2.  在  **BAM**功能表上，按一下**BAM DB 連線**。  
  
    3.  在 [**選取 BAM 資料庫**] 對話方塊中，輸入 SQL Server 和 BAMPrimaryImport 資料庫，然後按一下**確定**。  
  
    4.  在 **檔案**功能表上，按一下**關閉並返回 Microsoft Excel**。  
  
    5.  在 [檔案] 功能表上，按一下 [儲存]。  
  
16. 依照下列步驟，更新所有 BAM 分析 DTS 封裝中的伺服器及資料庫名稱，這些名稱會加上 "BAM_AN_" 或 "BAM_DM_" 做為前置詞：  
  
    1.  在裝載 BAM 的伺服器上，開啟 SQL Server Enterprise Manager。  
  
    2.  開啟**Data Transformation Services**資料夾。  
  
    3.  開啟**本機封裝**資料夾，然後開啟 DTS 封裝。  
  
    4.  在 **封裝**功能表上，按一下**屬性**。  
  
    5.  在 **全域變數**索引標籤上，更新主要匯入伺服器和資料庫的值。  
  
    6.  變更下列幾行以符合新的伺服器和資料庫：  
  
         PrimaryImportServer ="*\<ServerName\>*"  
  
         PrimaryImportDatabase ="*\<DatabaseName\>*"  
  
17. 啟動所有的 BizTalk Server 服務。 如需詳細資訊，請參閱 <<c0> [ 如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。  
  
18. 啟動 IIS 服務。  
  
19. 啟動 BAM 警示 Notification Service：  
  
    1.  按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
    2.  在命令提示字元中，輸入：  
  
        ```  
        Net start NS$BamAlerts  
        ```  
  
## <a name="see-also"></a>另請參閱  
 [移動 BizTalk Server 資料庫](../core/moving-biztalk-server-databases.md)