---
title: 如何移動 BAM 主要匯入 Database2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc4f2656-2faa-4503-9551-05e1b6eceb1a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe36c4a8b9aa6d081ebde854e6a4c57f9492df67
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50753206"
---
# <a name="how-to-move-the-bam-primary-import-database"></a>如何移動 BAM 主要匯入資料庫
您可以使用這個程序，將 BAM 主要匯入資料庫移動到其他伺服器。 端對端案例的觀點而言，移動 BAM 主要匯入資料庫包含兩個主要步驟：  
  
-   [移動 BAM 主要匯入資料庫](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_MovingBAMPI)  
  
-   [更新至新的 BAM 主要匯入資料庫的參考](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef)  
  
## <a name="prerequisites"></a>先決條件  
 您必須以成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。  
  
##  <a name="BKMK_MovingBAMPI"></a> 移動 BAM 主要匯入資料庫  
 執行下列程序移動 BAM 主要匯入資料庫中的步驟。  
  
#### <a name="to-move-the-bam-primary-import-database"></a>移動 BAM 主要匯入資料庫  
  
1. 停止任何 BAM cube 更新和資料維護 SSIS 封裝，或防止它們執行，直到您完成 BAM 主要匯入資料庫的還原為止。  
  
2. 停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。 如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
3. 停止 IIS 服務。  
  
4. 停止 BAM 警示 Notification service:  
  
   1.  按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
   2.  在命令提示字元中，輸入：  
  
        **net stop NS$ BamAlerts**  
  
5. 備份 BAM 主要匯入舊伺服器上的資料庫。 如需有關備份資料庫的指示，依照如何備份該資料庫是位於[如何： 備份資料庫 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (<http://go.microsoft.com/fwlink/?LinkId=156510>) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。  
  
6. 將 BAM 主要匯入資料庫複製到新[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
7. 還原新的伺服器上的 BAM 主要匯入資料庫。 如需還原資料庫，指示如何還原的資料庫時遵循的指示[如何： 還原資料庫備份 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (<http://go.microsoft.com/fwlink/?LinkId=156511>) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。  
  
   > [!NOTE]  
   >  如果您是從備份還原「BAM 主要匯入」資料庫，那麼您也應該使用比 BAM 主要備份還舊的備份，來還原「BAM 封存」、「BAM 星狀結構描述」及「BAM 分析」資料庫。  
  
##  <a name="BKMK_BAMPIRef"></a> 更新至新的 BAM 主要匯入資料庫的參考  
 移動資料庫之後，您必須更新至新的 BAM 主要匯入資料庫的所有參考。 必須更新下列參考：  
  
-   使用新的伺服器名稱來更新所有的 BizTalk 資料庫。 您可以使用 UpdateDatabase.vbs 指令碼來這樣做。 請參閱[若要使用新的伺服器名稱更新 BizTalk 資料庫](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDB)。  
  
-   更新 BAM 入口網站的 Web.config 檔案。 請參閱[若要更新 BAM 入口網站的 Web.config 檔案](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_Config)。  
  
-   更新 BAM 主要匯入資料庫中所有 BAM Livedata Microsoft Excel 檔案的參考。 請參閱[若要更新 BAM Livedata Microsoft Excel 檔案中的參考](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateExcel)。  
  
-   更新所有 BAM 分析 SSIS 封裝中新的伺服器和資料庫名稱。 請參閱[來更新伺服器和資料庫名稱在所有 BAM SSIS 套件](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdatePckg)。  
  
-   更新的新伺服器和資料庫名稱在資料來源中所有的 OLAP cube。 請參閱[更新伺服器和資料來源中所有的 OLAP cube 的資料庫名稱](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDSOLAP)。  
  
###  <a name="BKMK_UpdateDB"></a> 若要使用新的伺服器名稱更新 BizTalk 資料庫  
  
1. 在執行 BizTalk Server 的電腦，瀏覽至下列資料夾：  
  
   - 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:  
  
      **%Programfiles (x86) %\Microsoft BizTalk Server 2010\bins32\Schema\Restore**  
  
   - 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:  
  
      **%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**  
  
2. 以滑鼠右鍵按一下**SampleUpdateInfo.xml**，然後按一下**編輯**。  
  
3. 將除了 BizTalkMgmtDb、OldPrimaryImportDatabase、PrimaryImportDatabase、ArchivingDatabase、AnalysisDatabase、StarSchemaDatabase 和 Alert 以外的所有資料庫區段標記為註解。  
  
4. 中`OldPrimaryImportDatabase`一節的檔案，如`ServerName`屬性，取代**SourceServer**的現有資料庫所在的伺服器名稱。  
  
5. 中`PrimaryImportDatabase`一節的檔案，如`ServerName`屬性，取代**DestinationServer**您已經在其中移動 BAM 主要匯入資料庫的伺服器名稱  
  
6. BizTalkMgmtDb、 ArchivingDatabase、 AnalysisDatabase、 StarSchemaDatabase 和 Alert 區段，如設定"SourceServer"和"Destination Server"的現有的伺服器名稱這些資料庫所在的位置。  
  
   > [!IMPORTANT]
   >  在來源及目的系統的名稱兩端加上引號。  
   > 
   > [!NOTE]
   >  如果您重新命名任何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，您也必須更新為適當的資料庫名稱。  
  
7. 完成檔案的編輯後，請加以儲存並結束。  
  
8. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
9. 在命令提示字元中，瀏覽至下列目錄：  
  
   - 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:  
  
      **%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Schema\Restore**  
  
   - 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:  
  
      **%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**  
  
10. 在命令提示字元中，輸入：  
  
     **cscript UpdateDatabase.vbs SampleUpdateInfo.xml**  
  
###  <a name="BKMK_Config"></a> 若要更新 BAM 入口網站的 Web.config 檔案  
  
1.  在電腦上執行 BizTalk Server，更新 Web.config 檔案下的**\<磁碟機\>: \Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMManagementService\Web.Config**。更新伺服器和資料庫名稱，在 Web.config 中的下列區段：  
  
    ```  
    <appSettings>  
      <add key="BamServer" value="<ServerName>" />  
      <add key="BamDatabase" value="<DatabaseName>" />  
    </appSettings>  
    ```  
  
2.  在電腦上執行 BizTalk Server，更新 Web.config 檔案下的**\<磁碟機\>: \Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMQueryService\Web.Config**。更新伺服器和資料庫名稱，在 Web.config 中的下列區段：  
  
    ```  
    <appSettings>  
      <add key="BamServer" value="<ServerName>" />  
      <add key="BamDatabase" value="<DatabaseName>" />  
      <add key="MaxResultRows" value="2000" />  
    </appSettings>  
    ```  
  
3.  儲存並關閉檔案。  
  
###  <a name="BKMK_UpdateExcel"></a> 若要更新 BAM Livedata Microsoft Excel 檔案中的參考  
  
1. 開啟 Excel 即時資料檔案。 此檔案名稱是以 _LiveData.xls 結尾。  
  
2. 在  **BAM**功能表上，按一下**BAM DB 連線**。  
  
3. 在 **選取 BAM 資料庫**對話方塊方塊中，輸入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦和 BAMPrimaryImport 資料庫，然後再按一下**確定**。  
  
4. 在 **檔案**功能表上，按一下**關閉並返回 Microsoft Excel**。  
  
5. 在 [檔案] 功能表上，按一下 [儲存]。  
  
###  <a name="BKMK_UpdatePckg"></a> 若要更新伺服器和資料庫名稱在所有 BAM SSIS 套件  
  
1.  更新所有 BAM 分析 SSIS 封裝中，會加上"BAM_AN_"或"BAM_DM_"的伺服器和資料庫名稱。 若要這樣做，請按一下**開始**，按一下**所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下**SQL Server Business Intelligence Development Studio**。  
  
2.  在 SQL Server Business Intelligence Development Studio 中建立新專案。 按一下 **檔案**，按一下**新增**，然後按一下**專案**。  
  
3.  在 **新的專案**對話方塊中，於**專案類型**方塊中，按一下**商業智慧專案**。 在右窗格中，在**範本**方塊中，按一下**Integration Services 專案**，然後按一下**確定**。  
  
4.  在**Integration Services 專案**對話方塊中，在 [方案總管] 中，以滑鼠右鍵按一下**SSIS 封裝**，然後按一下**加入現有封裝**。  
  
5.  中**加入現有封裝的副本**對話方塊中，於**伺服器**下拉式清單方塊中，選取伺服器，其中包含 BAM_AN_\*和 BAM_DM_\*封裝。  
  
6.  在 **封裝路徑**，按一下省略符號按鈕。  
  
7.  在  **SSIS 封裝**對話方塊方塊中，選取您想要更新，請按一下 的套件**確定**，然後按一下  **確定**。  
  
     封裝現在會在 [方案總管] 中列出。  
  
8.  在 [方案總管] 中，按兩下您在上一個步驟中新增的套件。 在 **連接管理員**索引標籤上 （朝向螢幕的下半部提供） 中，按兩下資料來源數字 1 （BAMPrimaryImport 資料庫內）。  
  
9. 在 **連接管理員**對話方塊中，於**伺服器名稱**方塊，輸入伺服器名稱，然後按一下**確定**。  
  
10. 按一下 [**封裝總管]** 索引標籤上，按兩下**變數**資料夾，然後更新的值**PrimaryImportDatabase**並**PrimaryImportServer**變數。 您必須更新為指向新的伺服器與資料庫的值。  
  
    > [!NOTE]  
    >  針對您想要更新的所有封裝重複步驟 4 到 10。  
  
11. 然後按一下**檔案**功能表，然後再按一下**全部儲存**。  
  
12. 啟動 SQL Server Management Studio。 按一下 **開始**，按一下**所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下**SQL Server Management Studio**。  
  
13. 在 [**連接到伺服器**] 對話方塊中，從**伺服器**類型下拉式清單中，選取**Integration Services**。  
  
14. 指定伺服器名稱和認證以連接至伺服器，然後按一下**確定**。  
  
15. 在 **物件總管 中**，展開**Integration Services**，展開**存放的封裝**，然後按一下  **MSDB**。  
  
16. 在 **物件總管詳細資料**索引標籤上，以滑鼠右鍵按一下您在稍早所更新的封裝，然後按一下**匯入封裝**。  
  
17. 在 [**匯入封裝**] 對話方塊中，從**封裝位置**下拉式清單中，選取**檔案系統**。  
  
18. 在 **封裝路徑**、 瀏覽至您儲存的專案中，選取您要匯入，然後按一下 的封裝.dtsx 檔案**開啟**。  
  
19. 按一下以自動填入  方塊中的 封裝名稱 方塊內。  
  
    > [!NOTE]  
    >  針對您想要更新的所有封裝重複步驟 16 到 19。  
  
20. 按一下  **確定**，然後按一下**是**覆寫。  
  
21. 啟用任何 BAM Cube 更新和資料維護 SSIS 封裝。  
  
###  <a name="BKMK_UpdateDSOLAP"></a> 更新伺服器和資料來源中所有的 OLAP cube 的資料庫名稱  
  
1. 更新的伺服器和資料庫名稱在資料來源中所有的 OLAP cube。 若要這樣做，請按一下**開始**，按一下**所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下**SQL Server Management Studio**。  
  
2. 在**連接到伺服器** 對話方塊中，如**伺服器類型**下拉式清單中，選取**Analysis Services**、 提供伺服器名稱、 選取驗證方法 （和提供認證如有必要），然後按一下**Connect**。  
  
3. 在 物件總管 中，依序展開**資料庫**，展開**BAMAnalysis**，展開**Zdroje dat**，然後按兩下 資料來源。  
  
4. 在 **資料來源屬性**對話方塊方塊中，按一下省略符號按鈕 **（...）** 對抗**連接字串**屬性。  
  
5. 在**連接管理員**對話方塊中，於**伺服器名稱**方塊中，輸入裝載 BAMPrimaryImport 資料庫的伺服器名稱，按一下**確定**，然後按一下  **確定**。  
  
6. 啟動所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。 如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
7. 啟動 IIS 服務。  
  
8. 啟動 BAM 警示 Notification service:  
  
   1.  按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
   2.  在命令提示字元中，輸入：  
  
        **Net start NS$ BamAlerts**  
  
9. 解決任何不完整的追蹤執行個體。  如需解決未完成的 BAM 活動執行個體的相關資訊，請參閱 <<c0> [ 如何解析未完成的活動執行個體](http://go.microsoft.com/fwlink/?LinkId=151475)(http://go.microsoft.com/fwlink/?LinkId=151475)。  
  
## <a name="see-also"></a>另請參閱  
 [移動資料庫](../technical-guides/moving-databases.md)