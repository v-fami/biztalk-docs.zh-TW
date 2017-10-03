---
title: "如何設定記錄傳送目的地系統 |Microsoft 文件"
ms.custom: 
ms.date: 2015-12-03
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, log shipping
- system failures, preventing
- log shipping
- databases, backing up
- backing up, databases
- system failures, backing up
- backing up, system failures
ms.assetid: 7b4425f5-b105-4fb2-a503-94ca1e75ad55
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea377f83f6e9c104d1bbd0b2e59923fb11f8fe65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-destination-system-for-log-shipping"></a>如何設定記錄傳送的目的系統
記錄傳送提供待命伺服器功能，發生系統錯誤時可減少停機時間。 記錄傳送可讓您自動從來源系統的交易記錄檔傳送至目的地系統。 在目的系統，交易記錄會還原到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫中，使這些資料庫與來源資料庫緊密同步。  
  
 記錄傳送可同時在單一伺服器和分散式伺服器環境中運作。 包含即時資料的伺服器群組的伺服器稱為來源 （或主要） 系統。 伺服器或用來還原資料庫備份的來源所產生的 （或主要） 系統的伺服器群組就稱為目的地 （或次要） 系統。  
  
 [關於記錄傳送](https://docs.microsoft.com/sql/database-engine/log-shipping/about-log-shipping-sql-server)SQL 中的文件提供的特定詳細資料。  
  
 您可以使用下列步驟來建立包含單一來源系統的一部伺服器的目的地系統。 如果目的系統包含多部伺服器，請在每部目的伺服器上重複這些步驟。  
  
> [!IMPORTANT]
>  請務必在安全的位置保留備份檔案的複本。 即使您擁有記錄檔備份，也無法在沒有備份檔案的情況下還原資料庫。  
  
## <a name="prerequisites"></a>必要條件  
* 成員的身分登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
* 在來源和目的地系統上使用相同版本的 SQL Server。 SQL Server 必須安裝在來源和目的地系統上相同的相對位置。  
  
* 來源系統上 SQL 交易記錄 (.LDF 檔案) 的目錄也必須存在於目的系統上。 如果目的系統上沒有這個目錄，請以和來源系統上相同的名稱和權限來建立此目錄。  
  
### <a name="configure-the-destination-system-for-log-shipping"></a>設定目的系統以進行記錄傳送  
  
1.  在目的地系統上，開啟**SQL Server Management Studio**，並連接到您的 SQL Server。 選取**主要**從可用的資料庫。  
  
2.  在**檔案**功能表上，**開啟**下列 SQL 指令碼：  
  
    ```    
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\LogShipping_Destination_Schema.sql  
    ```  
  
3.  在**查詢**功能表上，選取**Execute**。  
  
     *LogShipping_Destination_Schema*卸除並重新建立用來還原來源資料庫，在目的系統上的資料表。 這些資料表儲存的內容包括所要還原的資料庫清單、從來源系統的 BizTalkMgmtDb 資料庫匯入的備份歷程記錄的複本，以及設定為針對來源資料庫執行的 SQL Server Agent 作業之相關資訊。  
  
4.  在**檔案**功能表上，**開啟**下列 SQL 指令碼：  
  
    ```    
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\LogShipping_Destination_Logic.sql  
    ```  
  
5.  在**查詢**功能表上，選取**Execute**。  
  
6.  在電腦或在已的識別為目的系統中，開啟**SQL Server Management Studio**並連接到 SQL Server。  
  
7.  選取**新查詢**。 在查詢視窗中，貼上下列命令：  
  
    ```  
    exec bts_ConfigureBizTalkLogShipping @nvcDescription = '<MyLogShippingSolution>',  
    @nvcMgmtDatabaseName = '<BizTalkServerManagementDatabaseName>',  
    @nvcMgmtServerName = '<BizTalkServerManagementDatabaseServer>',  
    @SourceServerName = null, -- null indicates that this destination server restores all databases  
    @fLinkServers = 1 -- 1 automatically links the server to the management database  
    ```  
  
     然後：  
  
    1.  在目的地系統上啟用 **[Ad Hoc Distributed Queries](https://docs.microsoft.com/sql/database-engine/configure-windows/server-configuration-options-sql-server)**。  
  
    2.  在查詢視窗中，取代 *\<MyLogShippingSolution >*意義的描述，並以單引號括住。  
  
    3.  在查詢視窗中，取代 *\<BizTalkServerManagementDatabaseName >*和 *\<BizTalkServerManagementDatabaseServer >*具有名稱和位置的程式來源 BizTalk 管理資料庫，以單引號括住。  
  
    > [!NOTE]
    >  如果您有一個以上的來源伺服器，則可以將每個來源伺服器還原到各自的目的伺服器。 每個目的地伺服器上，在 **@SourceServerName = null**參數取代*null*適當來源伺服器的名稱，並以單引號括住 (例如，  **@SourceServerName = 'MySourceServer'**)。  
  
8.  在**查詢**功能表上，選取**Execute**。  
  
    > [!IMPORTANT]
    >  如果查詢失敗，修正查詢的問題之後，您必須啟動在步驟 1 中的這個程序來重新設定目的系統。  
  
    > [!NOTE]
    >  在目的系統上的還原作業嘗試將存在於來源伺服器上重新建立的記錄檔和資料檔中每個已還原資料庫的相同位置。  
  
9. 在目的地系統上**SQL Server Management Studio**，依序展開**SQL Server Agent**，並展開**作業**。  
  
     在 [詳細資料] 窗格中，有三個新的工作：  
  
    -   **BTS 記錄傳送取得備份歷程記錄**  
  
         這個 BizTalk 工作會將備份歷程記錄從來源移至目的地。 此作業依預設排程為每分鐘執行一次。 這項作業會經常不斷執行，將歷程記錄從來源移至目的地。 來源系統的系統失敗，發生在您識別為目的系統的伺服器會繼續處理已經匯入的歷程記錄。  
  
    -   **BTS Server 記錄傳送還原資料庫**  
  
         這個 BizTalk 工作會將來源的指定資料庫的備份檔案還原到目的地伺服器。 此作業依預設排程為每分鐘執行一次。 只要仍然有需要還原的備份檔案，這項作業就會繼續執行而無法完成。 為採取額外的預防措施，您可讓這項作業執行久一點以確保其完成。  
  
    -   **BTS 記錄傳送還原為標示**  
  
         此 BizTalk 作業會將所有的資料庫至標示的最後一個記錄備份中。 這樣可以確保所有的資料庫在交易上處於一致的狀態。 此外，這項作業還會在目的系統上重新建立原本在來源系統上進行的所有 SQL Server Agent 作業。  
  
    > [!IMPORTANT]
    >  請務必監控這些作業以防作業失敗。  
  
10. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請移至下列資料夾：  
  
     32 位元電腦： %SystemDrive%\Program Files\Microsoft BizTalk Server\<版本 > \Schema\Restore  
  
     64 位元電腦： %SystemDrive%\Program Files (x86) \Microsoft BizTalk Server\<版本 > \Bins32\Schema\Restore  
  
11. 以滑鼠右鍵按一下**SampleUpdateInfo.xml**，然後選取**編輯**。 執行下列動作：  
  
    -   所有執行個體**"SourceServer"**來源系統的名稱。  
  
    -   所有執行個體**"DestinationServer"**目的系統的名稱。  
  
    > [!IMPORTANT]
    >  在來源及目的系統的名稱兩端加上引號。  
  
    > [!NOTE]
    >  如果您重新命名任何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，您也必須更新 XML 檔案中的資料庫名稱。  
  
    > [!NOTE]
    >  如果您已設定 BAM，您必須加入下列幾行中的**OtherDatabases**區段**SampleUpdateInfo.xml** BAMAlertsApplication 和 BAMAlertsNSMain 資料庫檔案：   
    > `<Database Name="BAM Alerts Application DB" oldDBName="BAMAlertsApplication" oldDBServer="SourceServer" newDBName=" BAMAlertsApplication" newDBServer="DestinationServer"/>`  
    > `<Database Name="BAM Alerts Instance DB" oldDBName="BAMAlertsNSMain" oldDBServer="SourceServer" newDBName="BAMAlertsNSMain" newDBServer="DestinationServer"/>`  
    >   
    >  如果您變更這兩個資料庫的預設名稱，請使用實際的資料庫名稱。  
  
12. 如果您有一個以上的 MessageBox 資料庫您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統中，加入清單中，加入另一行 MessageBoxDB，然後設定**IsMaster ="0"**非主要資料庫。  
  
13. 如果您使用 BAM 或 「 規則引擎，請視需要這些行取消註解。  
  
14. 如果您有任何自訂資料庫，將它們加入下 **\<OtherDatabases >** > 一節。 請參閱[如何備份自訂資料庫](../core/how-to-back-up-custom-databases.md)。  
  
15. 當您完成編輯檔案時，加以儲存，並結束。  
  
## <a name="next-steps"></a>後續步驟  
 [如何還原資料庫](../core/how-to-restore-your-databases.md)  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md)   
 [如何備份自訂資料庫](../core/how-to-back-up-custom-databases.md)