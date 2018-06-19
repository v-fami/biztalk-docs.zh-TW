---
title: 組態後資料庫 Optimizations2 |Microsoft 文件
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
ms.openlocfilehash: 168323f1e7dfdbb796fe29e0025c5d2a6f40c957
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302662"
---
# <a name="post-configuration-database-optimizations"></a>組態後資料庫最佳化
除了下列中的建議[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)，應該遵循幾個步驟來最佳化 SQL Server 上的 BizTalk Server 資料庫效能*之後*已安裝 BizTalk Server，且已設定 BizTalk Server 資料庫。 本主題提供這些最佳化的清單。  
  
## <a name="consider-setting-the-text-in-row-table-option-on-specific-messagebox-database-tables"></a>請考慮設定特定的 MessageBox 資料庫資料表上的 'text in row' 資料表選項  
 SQL Server 提供的呼叫選項的資料表**資料列中的文字**宣告之類型的欄位內容**文字**， **ntext**，或**映像**維度的小於所 (8 Kb) 的資料頁的資料必須儲存在資料列。 藉由設定這個選項在 BizTalkMsgBoxDb 資料表 （Parts 資料表、 多工緩衝處理資料表和 DynamicStateInfo 資料表），您可以在使用較小的訊息有小型的內容和小型的持續性大小的協調流程時，增加訊息輸送量。  
  
-   **組件資料表**： 訊息大小小於 8 kb 的維度中的資料頁時，套用**資料列中的文字**Parts 資料表的資料表選項可能會導致 BizTalk Server 效能改進。 組件資料表包含下列欄位：  
  
    -   **ImgPart**： 包含訊息部分或訊息部分片段。  
  
    -   **ImgPropBag**： 包含訊息部分的屬性包。  
  
     如此一來，MessageBox 中，針對迴圈時執行 BizTalk 主控件中的訊息代理程式可以擷取一批訊息從 Parts 資料表讀取小型的分頁數量。 根據特定案例和硬體組態，這項技術可以降低 CPU 使用率，同時在 SQL Server 與 BizTalk Server 中，並提供顯著的改善，以延遲和輸送量。  
  
-   **資料表多工緩衝處理**： 當訊息內容的平均大小小於 8 kb 時，啟用**資料列中的文字**多工緩衝處理資料表的資料表選項可協助您降低的存取次數，沿著 MessageBox 中讀取訊息時連同其內容。 若要將此選項套用至多工緩衝處理資料表，您必須排除不必要的內容屬性和辨別的欄位，以減少成低於 8 Kb 的訊息內容的大小。  
  
-   **DynamicStateInfo 資料表**這些資料表中，一個用於每個主機，包含的類型為 image 呼叫 imgData 包含二進位序列化協調流程狀態，其執行期間遇到保存點時的欄位。 內部狀態的協調流程主控件 HostA 中很小，一次序列化其大小會小於 8 kb 時**資料列中的文字**技術可以成功地套用至 DynamicStateInfo_HostA 資料表。 因此我們建議您保留的協調流程的內部狀態越小越好。 這項技術可以大幅降低 XLANG 引擎來序列化、 保存、 還原序列化和還原的協調流程持續點發生內部狀態所花費的時間。  
  
 我們在我們的測試實驗室中使用下列設定：  
  
-   EXEC sp_tableoption N'Spool'，'text in row'，'6000'  
  
-   EXEC sp_tableoption N'Parts'，'text in row'，'6000'  
  
## <a name="define-auto-growth-settings-for-biztalk-server-databases-to-a-fixed-value-instead-of-a-percentage-value"></a>定義 BizTalk Server 資料庫的自動成長設定為固定的值，而不是百分比值  
  
-   SQL Server 資料庫自動成長是封鎖作業，會妨礙 BizTalk Server 資料庫效能。 因此務必配置足夠的空間，BizTalk Server 資料庫，事先來減少資料庫自動成長的相符項目。  
  
-   自動成長的資料庫應該設為固定數目的 mb，而不是百分比 (指定的檔案成長**以 mb 為單位**)。 這應完成，因此，如果自動成長，就會發生，它會以測量的方式。 這會減少過多資料庫成長的可能性。 BizTalk Server 資料庫的成長遞增通常應該不低於 100 MB。  
  
## <a name="pre-size-biztalk-server-databases-to-appropriate-size-with-multiple-data-files"></a>預先搭配多個資料檔大小為適當大小的 BizTalk Server 資料庫  
 當 SQL Server 會增加檔案大小時，它必須先初始化新的空間，才能使用。 這是封鎖作業，包括新的空間中填入空白頁。 SQL Server 2005 或更新版本執行 Windows Server 2003 或更新版本可支援立即檔案初始化。 」 這可大幅減少檔案成長作業的效能影響。 如需詳細資訊，請參閱[資料庫檔案初始化](http://go.microsoft.com/fwlink/?LinkId=132063)(http://go.microsoft.com/fwlink/?LinkId=132063) SQL Server 線上叢書中。 本主題提供步驟啟用立即檔案初始化。  
  
 下列清單說明我們的測試實驗室中使用的 BizTalk Server 資料庫設定：  
  
-   **BizTalk DTADB （BizTalk 追蹤資料庫檔案）：** 有 2048 MB，成長 100 MB 的檔案大小和 1024 MB 的記錄檔，具有 100 MB 成長的資料檔案。  
  
-   **BizTalkMgmtdb （BizTalk 管理資料庫檔案）：** 有 100 MB 成長 512 MB 的檔案大小和為 100 MB 成長 512 MB 的記錄檔的資料檔案。  
  
-   **SSODB:** 有 100 MB 成長 512 MB 的檔案大小和為 100 MB 成長 512 MB 的記錄檔的資料檔案。  
  
-   **BizTalkMsgBoxDb （BizTalk MessageBox 資料庫）：** 8 個資料檔案，每個皆為 100 MB 成長的 2 gb 檔案大小和 20 GB 的記錄檔，具有 100 MB 的成長。 因為 BizTalk MessageBox 資料庫是最常使用，我們建議您將資料檔案和交易記錄檔，在專用的磁碟機，以降低磁碟 I/O 競爭問題的可能性。 在實驗室環境中，我們會使用一部磁碟機的下列各項：  
  
    -   MessageBox 資料檔案  
  
    -   MessageBox 交易記錄檔  
  
 下列 SQL 指令碼可用來預先調整大小 BizTalkMsgBoxDb 最初有磁碟機 J (J:\BizTalkMsgBoxDb.mdf) 上的資料檔案和記錄檔磁碟機 K (K:\BizTalkMsgBoxDb_log。LDF):  
  
> [!IMPORTANT]  
>  此指令碼為 「 現況，「 僅供示範或教育目的，且提供用於風險自負。 使用此指令碼不支援的 Microsoft，Microsoft 不會對不保證此指令碼的適用性。  
  
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
  
## <a name="move-the-backup-biztalk-server-output-directory-to-a-dedicated-lun"></a>將備份 BizTalk Server 的輸出目錄移至的專用 LUN  
 將備份 BizTalk （完整和記錄備份） 的輸出目錄移至專用的 LUN，然後編輯 備份 BizTalk Server 作業，以指向專用的 LUN。 移動 備份 BizTalk Server 輸出目錄的專用 LUN 會減少磁碟 I/O 競爭，當工作正在執行工作與不同的磁碟寫入正在讀取。 如需設定 「 備份 BizTalk Server 」 工作的詳細資訊，請參閱[如何設定 「 備份 BizTalk Server 」 工作](http://go.microsoft.com/fwlink/?LinkID=153813)(http://go.microsoft.com/fwlink/?LinkID=153813) BizTalk Server 2010 說明中。  
  
## <a name="verify-that-the-biztalk-server-sql-agent-jobs-are-running"></a>確認執行 BizTalk Server SQL Agent 工作  
 BizTalk Server 包含數個 SQL Server Agent 作業執行重要功能以維持伺服器運作且狀況良好。 您應該監視這些作業的狀況，並確保它們正在執行不會發生錯誤。 在 BizTalk Server 中的效能問題的最常見的原因之一是 BizTalk Server SQL Agent 作業不會執行，這種情況會導致 MessageBox 以及追蹤資料庫成長未核取。 請遵循這些步驟，以確保 BizTalk Server SQL Agent 工作正在執行不會有問題：  
  
1.  **確認 SQL Server Agent 服務正在執行**。  
  
2.  **確認 BizTalk Server 安裝的 SQL Server Agent 作業已啟用且正在執行成功**。  
    BizTalk Server SQL Server Agent 作業很重要： 如果它們未執行，一段時間，將會降低系統效能。  
  
3.  **確認 BizTalk Server SQL Server Agent 作業所完成及時**。   
    設定最新版的 Microsoft System Center Operations Manager 監視作業。  
    您應留意某些工作特定的排程：  
  
    -   MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作預設會持續執行。 監視軟體，應該考量此排程，而不會產生警告。  
  
    -   未啟用 MessageBox_Message_Cleanup_BizTalkMsgBoxDb 作業或排程，但它由 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作啟動每隔 10 秒。 因此，此作業應該不啟用、 排程，或手動啟動。  
  
4.  **確認已正確設定 SQL Server Agent 服務的啟動類型**。  
    確認 SQL Server Agent 服務已設定使用**啟動類型**的**自動**除非 SQL Server Agent 服務已設定為 Windows Server 叢集上叢集資源。 如果 SQL Server Agent 服務設定為叢集資源，則您應該設定**啟動類型**為**手動**因為服務會受叢集服務。  
  
## <a name="configure-purging-and-archiving-of-tracking-data"></a>設定清除和封存的追蹤資料  
 請遵循這些步驟，以確保清除和封存的追蹤資料已正確設定：  
  
1.  確定 SQL Agent 作業 「 DTA 清除與封存 」 已正確設定、 啟用以及已成功完成。 如需詳細資訊，請參閱[如何設定 DTA 清除與封存工作](http://go.microsoft.com/fwlink/?LinkID=153814)(http://go.microsoft.com/fwlink/?LinkID=153814) 中的 BizTalk Server 文件。  
  
2.  請確定作業能夠以最快速度的內送的追蹤資料會產生清除追蹤資料。 如需詳細資訊，請參閱[測量最大持續性追蹤輸送量](http://go.microsoft.com/fwlink/?LinkID=153815)(http://go.microsoft.com/fwlink/?LinkID=153815) 中的 BizTalk Server 文件。  
  
3.  檢閱軟清除和硬清除參數，以確保您保持最佳的時間長度的資料。 如需詳細資訊，請參閱[封存和清除 BizTalk 追蹤資料庫](http://go.microsoft.com/fwlink/?LinkID=153816)(http://go.microsoft.com/fwlink/?LinkID=153816) 中的 BizTalk Server 文件。  
  
4.  如果您只需要清除舊資料，而不需要封存第一次，變更的 SQL 代理程式作業來呼叫預存程序 」 dtasp_PurgeTrackingDatabase。 」 如需詳細資訊，請參閱[如何從 BizTalk 追蹤資料庫清除資料](http://go.microsoft.com/fwlink/?LinkID=153817)(http://go.microsoft.com/fwlink/?LinkID=153817) 中的 BizTalk Server 文件。  
  
## <a name="monitor-and-reduce-dtc-log-file-disk-io-contention"></a>監視及降低 DTC 記錄檔磁碟 I/O 競爭  
 分散式交易協調器 (DTC) 記錄檔可以成為在交易密集的環境中的磁碟 I/O 瓶頸。 使用支援交易，例如 SQL Server、 MSMQ 或 MQSeries，或在多個 MessageBox 的環境中的介面卡時，這是特別有用。 交易式配接器使用 DTC 交易，並多 MessageBox 環境會大量使用 DTC 交易。 若要確保 DTC 記錄檔不會發生磁碟 I/O 瓶頸，您應監視磁碟 I/O 使用量 DTC 記錄檔所在的 SQL Server 資料庫伺服器上的磁碟。 如果磁碟 I/O 使用量 DTC 記錄檔所在的磁碟變成過多，請考慮將 DTC 記錄檔移到更快速的磁碟。 在環境中，SQL Server 已叢集化，這是不太多的主要考量因為記錄檔，就會共用的磁碟機，可能會有多個磁針的快速 SAN 磁碟機上。 不過，仍然，您應監視磁碟 I/O 使用量。 這是因為可能會成為瓶頸，以在非叢集環境或與其他需要大量的磁碟檔案的共用磁碟上的 DTC 記錄檔時。  
  
## <a name="separate-the-messagebox-and-tracking-databases"></a>分隔 MessageBox 和追蹤資料庫  
 因為 BizTalk MessageBox 和 「 BizTalk 追蹤資料庫是最常使用，我們建議您針對每一種可降低發生問題的磁碟 I/O 競爭的可能性的專用磁碟機上放置資料檔和交易記錄檔。 比方說，您需要四個 MessageBox 和 「 BizTalk 追蹤資料庫檔案的磁碟機、 一部磁碟機的下列各項：  
  
-   MessageBox 資料檔案  
  
-   MessageBox 交易記錄檔  
  
-   BizTalk 追蹤 (DTA) 資料檔案  
  
-   BizTalk 追蹤 (DTA) 交易記錄檔  
  
 分隔 BizTalk MessageBox 和 「 BizTalk 追蹤資料庫，以及將資料庫檔案和交易記錄檔不同實體磁碟上的會被視為降低磁碟 I/O 競爭的最佳作法。 請試著儘可能將磁碟 I/O 分散數量的實體磁針。 您也可以降低磁碟 I/O 競爭，將 BizTalk 追蹤資料庫放置在專用的 SQL Server;不過，您仍應該遵循上述作法，有關分隔資料檔和交易記錄檔。  
  
## <a name="optimize-filegroups-for-the-biztalk-server-databases"></a>最佳化檔案群組的 BizTalk Server 資料庫  
 請依照[Databases2 最佳化檔案群組](../technical-guides/optimizing-filegroups-for-the-databases2.md)和[BizTalk Server 資料庫最佳化](http://go.microsoft.com/fwlink/?LinkId=101578)白皮書 ([http://go.microsoft.com/fwlink/?LinkId = 101578](http://go.microsoft.com/fwlink/?LinkId=101578)) 才能建立其他檔案群組和 BizTalk Server 資料庫的檔案。 這會大幅增加 BizTalk Server 資料庫，從單一磁碟設定的效能。  
  
## <a name="see-also"></a>另請參閱  
 [最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)