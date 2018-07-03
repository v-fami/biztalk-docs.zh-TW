---
title: 後置設定資料庫 Optimizations2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 609eda22-8399-4b7c-b860-21b495d2f68d
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8489d69489a23d6c81efb8443cccbb40c7a357ea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993791"
---
# <a name="post-configuration-database-optimizations"></a>後置設定資料庫最佳化
除了遵循中的建議[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)，應該遵循數個步驟，才能將 SQL Server 上的 BizTalk Server 資料庫效能最佳化*之後*在安裝 BizTalk Server，而且已設定 BizTalk Server 資料庫。 本主題提供這些最佳化的清單。  
  
## <a name="consider-setting-the-text-in-row-table-option-on-specific-messagebox-database-tables"></a>請考慮設定特定的 MessageBox 資料庫資料表上的 'text in row' 資料表選項  
 SQL Server 提供資料表的選項，稱為**資料列中的文字**宣告的型別欄位的內容**文字**， **ntext**，或**映像**維度會小於所資料頁 (8 Kb) 的資料必須儲存在資料列。 藉由設定這個選項在 BizTalkMsgBoxDb 資料表 （Parts 資料表、 多工緩衝處理資料表和 DynamicStateInfo 資料表），您可以使用較小的訊息具有為小型的內容，而且有小型的保存性大小的協調流程時，增加訊息輸送量。  
  
- **組件資料表**： 訊息大小小於 8 kb 的資料頁的維度時，套用**資料列中的文字**Parts 資料表上的資料表選項可能會導致 BizTalk Server 效能改進。 組件資料表包含下列欄位：  
  
  - **ImgPart**： 包含訊息部分或訊息部分片段。  
  
  - **ImgPropBag**： 包含訊息部分的屬性包。  
  
    如此一來，當迴圈跑在 MessageBox 中，針對執行 BizTalk 主控件中的訊息代理程式可以擷取一批訊息 Parts 資料表，請閱讀少量的頁面。 根據特定案例和硬體組態，可以減少 CPU 使用率，同時在 SQL Server 與 BizTalk Server 中，這項技術，並將其提供延遲和輸送量方面的重大改進中。  
  
- **多工緩衝處理表格**： 當訊息內容的平均大小小於 8 kb 時，啟用**資料列中的文字**資料表多工緩衝處理資料表上的選項可協助您降低存取數目，以及在 MessageBox 中讀取訊息時連同其內容。 若要將此選項套用至多工緩衝處理資料表，您必須排除不必要的內容屬性和辨別的欄位，以減少大小小於 8 Kb 的訊息內容。  
  
- **DynamicStateInfo 資料表**這些資料表中，每個主控件，其中包含稱為，其中包含二進位序列化的協調流程狀態，在執行期間遇到保存點 imgData 映像類型的欄位。 協調流程主控件 HostA 中的內部狀態很小，它一次序列化的大小是小於 8 kb 時**資料列中的文字**技術可以成功地套用至 DynamicStateInfo_HostA 資料表。 因此我們建議您保留協調流程的內部狀態越小越好。 這項技術可以大幅降低 XLANG 引擎來序列化、 保存、 還原序列化和還原的持續點發生協調流程的內部狀態所花的時間。  
  
  我們在我們的實驗室測試中使用下列設定：  
  
- EXEC sp_tableoption N'Spool'，'text in row'，'6000'  
  
- EXEC sp_tableoption N'Parts'，'text in row'，'6000'  
  
## <a name="define-auto-growth-settings-for-biztalk-server-databases-to-a-fixed-value-instead-of-a-percentage-value"></a>定義 BizTalk Server 資料庫的自動成長設定為固定的值，而不是百分比值  
  
-   SQL Server 資料庫自動成長是封鎖作業，這會防礙 BizTalk Server 資料庫效能。 因此務必配置足夠的空間，BizTalk Server 資料庫，以減少資料庫自動成長的相符項目。  
  
-   資料庫自動成長應該設定為固定數目的 mb，而不是百分比 (指定的檔案成長**以 mb 為單位**)。 這應該這麼一來，如果自動成長，就會發生，它會測量方式。 這會減少過多的資料庫成長的可能性。 BizTalk Server 資料庫的成長遞增通常應該不會低於 100 MB。  
  
## <a name="pre-size-biztalk-server-databases-to-appropriate-size-with-multiple-data-files"></a>預先調整成適當大小的 BizTalk Server 資料庫大小與多個資料檔案  
 當 SQL Server 會增加檔案大小時，它必須先初始化新的空間，才能使用。 這是牽涉到新的空間中填入空白頁的封鎖作業。 SQL Server 2005 或更新版本執行 Windows Server 2003 或更新版本支援 「 立即檔案初始化 」。 這可以大幅降低檔案成長作業的效能影響。 如需詳細資訊，請參閱 <<c0> [ 資料庫檔案初始化](http://go.microsoft.com/fwlink/?LinkId=132063)(http://go.microsoft.com/fwlink/?LinkId=132063) SQL Server 線上叢書中。 本主題提供步驟啟用檔案立即初始化。  
  
 下列清單說明我們的實驗室測試中使用的 BizTalk Server 資料庫設定：  
  
- **BizTalk DTADB （BizTalk 追蹤資料庫檔案）：** 2048 MB，成長 100 MB 的檔案大小和 1024 MB 的記錄檔成長 100 MB 的資料檔案。  
  
- **BizTalkMgmtdb （BizTalk 管理資料庫檔案）：** 100MB 成長 512 mb 的檔案大小和 512 MB 的記錄檔成長 100 MB 的資料檔案。  
  
- **SSODB:** 100MB 成長 512 mb 的檔案大小和 512 MB 的記錄檔成長 100 MB 的資料檔案。  
  
- **BizTalkMsgBoxDb （BizTalk MessageBox 資料庫）：** 8 資料檔案，每個皆有 100 MB 的成長的 2 gb 檔案大小和 20 GB 的記錄檔成長 100 MB。 因為 BizTalk MessageBox 資料庫是最常使用，我們建議您將資料檔案和交易記錄檔，以減少磁碟 I/O 競爭問題的可能性的專用磁碟機上。 在我們的實驗室環境中，我們會使用一個磁碟機的下列各項：  
  
  -   MessageBox 資料檔案  
  
  -   MessageBox 交易記錄檔  
  
  下列 SQL 指令碼可用來預先調整大小 BizTalkMsgBoxDb 這一開始會有磁碟機 J (J:\BizTalkMsgBoxDb.mdf) 上的資料檔案和記錄檔在磁碟機 K (K:\BizTalkMsgBoxDb_log。LDF):  
  
> [!IMPORTANT]  
>  此指令碼會提供 「 依現況，」 僅適用於示範或教育目的之用，並使用自行承擔風險。 Microsoft 不支援使用此指令碼，Microsoft 不保證此指令碼的適用性。  
  
```  
EXEC dbo.sp_helpdb BizTalkMsgBoxDb  
ALTER DATABASE BizTalkMsgBoxDb MODIFY FILE (NAME = BizTalkMsgBoxDb , FILENAME = 'J:\BizTalkMsgBoxDb.mdf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_2 , FILENAME = 'J:\BizTalkMsgBoxDb_2.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_3 , FILENAME = 'J:\BizTalkMsgBoxDb_3.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_4 , FILENAME = 'J:\BizTalkMsgBoxDb_4.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_5 , FILENAME = 'J:\BizTalkMsgBoxDb_5.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_6 , FILENAME = 'J:\BizTalkMsgBoxDb_6.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_7 , FILENAME = 'J:\BizTalkMsgBoxDb_7.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_8 , FILENAME = 'J:\BizTalkMsgBoxDb_8.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
GO  
ALTER DATABASE BizTalkMsgBoxDb MODIFY FILE (NAME = BizTalkMsgBoxDb_log , FILENAME = 'K:\BizTalkMsgBoxDb_log.LDF', SIZE =  20GB , FILEGROWTH = 100MB)  
GO  
```  
  
## <a name="move-the-backup-biztalk-server-output-directory-to-a-dedicated-lun"></a>將備份 BizTalk Server 的輸出目錄移至專用的 LUN  
 移至的專用 LUN 中的 備份 BizTalk （完整和記錄備份） 的輸出目錄，然後編輯 備份 BizTalk Server 作業，以指向專用的 LUN。 從讀取移動備份 BizTalk Server 的輸出目錄的專用 lun 會減少磁碟 I/O 競爭，當工作正在執行寫入作業與不同的磁碟。 如需設定 「 備份 BizTalk Server 」 工作的詳細資訊，請參閱[如何設定 「 備份 BizTalk Server 」 工作](http://go.microsoft.com/fwlink/?LinkID=153813)(http://go.microsoft.com/fwlink/?LinkID=153813) BizTalk Server 2010 說明中。  
  
## <a name="verify-that-the-biztalk-server-sql-agent-jobs-are-running"></a>確認執行 BizTalk Server SQL Agent 工作  
 BizTalk Server 包含數個 SQL Server Agent 作業可執行以維持伺服器運作中且狀況良好的重要功能。 您應該監視這些作業的狀況，並確保它們正在執行無誤。 在 BizTalk Server 中的效能問題的最常見的原因之一是 BizTalk Server SQL Agent 作業不會執行，又會導致 MessageBox 和追蹤來抑制地成長的資料庫。 請遵循下列步驟以確保 BizTalk Server SQL Agent 作業皆正常地執行：  
  
1.  **確認 SQL Server Agent 服務正在執行**。  
  
2.  **確認 BizTalk Server 所安裝的 SQL Server Agent 作業已啟用且正在執行成功**。  
    BizTalk Server SQL Server Agent 作業而言十分重要： 如果它們並未執行，經過一段時間，會降低系統效能。  
  
3.  **確認 BizTalk Server SQL Server Agent 作業所完成及時**。   
    設定 Microsoft System Center Operations Manager 的最新版本，以監視作業。  
    您應該注意的是專門針對特定工作的排程：  
  
    -   預設會持續 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作執行。 監視軟體，請考量此排程，並不會產生警告。  
  
    -   MessageBox_Message_Cleanup_BizTalkMsgBoxDb 作業未啟用或排程，但它由 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作開始每隔 10 秒。 因此，這項作業不應啟用、 排程，或以手動方式啟動。  
  
4.  **確認已正確設定 SQL Server Agent 服務的啟動類型**。  
    確認 SQL Server Agent 服務已設有**啟動類型**的**自動**除非 SQL Server Agent 服務設定為 Windows Server 叢集上叢集資源。 如果 SQL Server Agent 服務設定為叢集資源，則您應該設定**啟動類型**作為**手動**因為服務將受叢集服務。  
  
## <a name="configure-purging-and-archiving-of-tracking-data"></a>設定清除和封存的追蹤資料  
 請遵循下列步驟以確保清除和封存的追蹤資料已正確設定：  
  
1.  請確定 SQL Agent 作業 「 DTA 清除與封存 」 是已正確設定、 啟用以及成功完成。 如需詳細資訊，請參閱 <<c0> [ 如何設定 DTA 清除與封存工作](http://go.microsoft.com/fwlink/?LinkID=153814)(http://go.microsoft.com/fwlink/?LinkID=153814) BizTalk Server 文件。  
  
2.  請確定作業已能夠以最快速度的內送的追蹤資料會產生清除追蹤資料。 如需詳細資訊，請參閱 <<c0> [ 測量最大持續性追蹤輸送量](http://go.microsoft.com/fwlink/?LinkID=153815)(http://go.microsoft.com/fwlink/?LinkID=153815) BizTalk Server 文件。  
  
3.  檢閱軟清除和硬清除參數，以確保您會將最佳的時間長度的資料保留。 如需詳細資訊，請參閱 <<c0> [ 封存和清除 BizTalk 追蹤資料庫](http://go.microsoft.com/fwlink/?LinkID=153816)(http://go.microsoft.com/fwlink/?LinkID=153816) BizTalk Server 文件。  
  
4.  如果您只需要清除舊資料，也不需要將它保存第一次，變更的 SQL 代理程式作業來呼叫預存程序 」 dtasp_PurgeTrackingDatabase。 」 如需詳細資訊，請參閱 <<c0> [ 如何從 BizTalk 追蹤資料庫清除資料](http://go.microsoft.com/fwlink/?LinkID=153817)(http://go.microsoft.com/fwlink/?LinkID=153817) BizTalk Server 文件。  
  
## <a name="monitor-and-reduce-dtc-log-file-disk-io-contention"></a>監視及降低 DTC 記錄檔的磁碟 I/O 競爭  
 Distributed Transaction Coordinator (DTC) 記錄檔會在交易密集的環境中的磁碟 I/O 瓶頸。 使用支援交易，例如 SQL Server、 MSMQ 或 MQSeries，或在多個 MessageBox 的環境中的配接器時，這是特別有用。 交易式配接器使用 DTC 交易，以及多個 MessageBox 環境會大量使用 DTC 交易。 若要確保 DTC 記錄檔不會成為磁碟 I/O 瓶頸，您應該監視 SQL Server 資料庫伺服器上的 DTC 記錄檔所在位置的磁碟 I/O 使用量的磁碟。 如果磁碟 DTC 記錄檔所在的磁碟 I/O 使用量變得過長，請考慮將 DTC 記錄檔移至磁碟速度更快。 在環境中已在叢集化 SQL Server，這是不太多無關緊要的因為記錄檔會在共用的磁碟機，可能會有多個磁針的快速 SAN 磁碟機上。 儘管如此，還是，您應該監視的磁碟 I/O 使用量。 這是因為它可能會變成非叢集環境中或當 DTC 記錄檔與其他需要大量磁碟的檔案的共用磁碟上的瓶頸。  
  
## <a name="separate-the-messagebox-and-tracking-databases"></a>分隔 MessageBox 和追蹤資料庫  
 因為 BizTalk MessageBox 和 「 BizTalk 追蹤資料庫是最常使用，我們建議您針對每一種可降低磁碟 I/O 競爭問題的可能性的專用磁碟機上放置資料檔和交易記錄檔。 比方說，您需要四個 MessageBox 和 「 BizTalk 追蹤資料庫檔案的磁碟機、 一個磁碟機的下列各項：  
  
- MessageBox 資料檔案  
  
- MessageBox 交易記錄檔  
  
- BizTalk 追蹤 (DTA) 資料檔案  
  
- BizTalk 追蹤 (DTA) 交易記錄檔  
  
  分隔 BizTalk MessageBox 和 「 BizTalk 追蹤資料庫，並將資料庫檔案和交易記錄檔，在不同的實體磁碟上會被視為減少磁碟 I/O 競爭的最佳作法。 請試著盡可能分散多個實體磁針的磁碟 I/O。 您也可以減少磁碟 I/O 競爭，藉由將 「 BizTalk 追蹤資料庫放在專用的 SQL Server;不過，您仍然應該遵循上述作法，關於用來分隔資料檔和交易記錄檔。  
  
## <a name="optimize-filegroups-for-the-biztalk-server-databases"></a>最佳化 BizTalk Server 資料庫檔案群組  
 請依照下列中的步驟[最佳化檔案群組的資料庫 2](../technical-guides/optimizing-filegroups-for-the-databases2.md)而[BizTalk Server 資料庫最佳化](http://go.microsoft.com/fwlink/?LinkId=101578)白皮書 （英文） ([http://go.microsoft.com/fwlink/?LinkId=101578](http://go.microsoft.com/fwlink/?LinkId=101578)) 若要建立其他檔案群組和 BizTalk Server 資料庫檔案。 這會大幅增加 BizTalk Server 資料庫，從單一磁碟設定的效能。  
  
## <a name="see-also"></a>另請參閱  
 [最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)