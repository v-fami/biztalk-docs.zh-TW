---
title: "檢查清單： 設定 SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edd20f24-8a72-40b7-abee-81fbd3ceefda
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f6c67fcdee26afd6ec9bb1016e86a98b1cf26e8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="checklist-configuring-sql-server"></a>檢查清單： 設定 SQL Server
若要準備的 SQL Server 時，請依照下列步驟使用 BizTalk Server 實際執行環境中。    
 
<a name="BKMK_Config"></a>   
## <a name="configuring-sql-server"></a>設定 SQL Server  
  
|步驟|參考|  
|-----------|---------------|  
|監視並減少 BizTalk Server 資料庫檔案磁碟 I/O 競爭問題。|-我們建議您主動監視存放的資料和交易記錄檔磁碟的磁碟 I/O 使用量。<br />-我們建議最好讓資料檔和交易記錄檔的每一種放在專用的磁碟機，以降低磁碟 I/O 競爭變得有問題的可能性。<br />-您可以降低磁碟 I/O 競爭，藉由分隔 MessageBox 和追蹤 (DTA) 資料庫，而且分隔的資料庫檔案和交易記錄檔不同實體磁碟上。<br /><br /> 如需詳細資訊，請參閱[監視及降低資料庫 IO 爭用](monitoring-and-reducing-database-i-o-contention.md)|  
|請確定 SQL Server 已正確對齊的磁碟分割|適當地對齊資料分割可能會導致明顯的延遲，進而改善 SQL Server 效能，進而增強了 BizTalk Server 效能降低的磁碟。 相反地，非對齊的磁碟分割效能造成負面影響 I/O，因而導致效能變差的 SQL Server 和 BizTalk Server 效能。<br /><br /> 如需有關如何正確對齊的磁碟分割正面可能會影響效能，請參閱 < [for SQL Server 的磁碟分割區對齊最佳作法](http://go.microsoft.com/fwlink/?LinkId=154073)。|  
|讓您使用 SQL Server Profiler 監視的事件|使用 SQL Server Profiler 來監視只有您感興趣的事件。 如果追蹤變得太大，您可以篩選，收集事件資料的子集，根據您想要的資訊。 監視太多事件會增加伺服器與監視處理序的負擔，且會使得追蹤檔案或追蹤資料表增長過大，尤其是需要花費長時間的監視處理序更是如此。|  
|監視及降低 DTC 記錄檔磁碟 I/O 競爭。|[監視與降低 DTC 記錄檔的磁碟 IO 競爭](monitoring-and-reducing-dtc-log-file-disk-i-o-contention.md)|  
|SQL Server 資料庫提供高可用性。|[規劃資料庫可用性](planning-for-database-availability.md)|  
|檢閱主動/主動容錯移轉案例的 SQL Server 叢集組態。|[檢閱及測試容錯移轉案例的 SQL Server 叢集設定](reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)|  
|使用預設組態設定：<br /><br /> Max Degree of Parallelism (MDOP)。<br />BizTalk Server MessageBox 資料庫上的 SQL Server 統計資料。<br />SQL Server 資料庫索引會重建和重組。|[不應該變更的 SQL Server 設定](sql-server-settings-that-should-not-be-changed.md)|  
|所有 SQL Server 執行個體中都啟用追蹤旗標 1118 (TF1118) 作為啟動參數。|實作 TF1118 有助於減少 SQL Server 執行個體之間的競爭，藉由移除幾乎所有的單一頁面配置。 如需詳細資訊，請參閱 Microsoft 知識庫文章[tempdb 資料庫的並行存取增強功能](https://support.microsoft.com/en-us/help/328551/concurrency-enhancements-for-the-tempdb-database)。 <br/><br/>**注意：**的詳細資訊，請參閱 TF1118[周圍 TF1118 多疑](https://www.sqlskills.com/blogs/paul/misconceptions-around-tf-1118/)。 請注意，在以下連結的內容不 Microsoft 所擁有，Microsoft 不保證內容的正確性。|  
|分割成多個資料檔相同大小的 BizTalk Server 使用的每個 SQL Server 執行個體上的 tempdb 資料庫。|確認用於 tempdb 資料檔案都屬於相同大小。 這是重要的因為 SQL Server 所使用的比例式填滿演算法為基礎的資料檔案的大小。 建立資料檔的大小不相等，如果比例填滿演算法會使用全域配置對應 (GAM) 配置，而不是分配之間的所有檔案，藉以定義的目的建立多個配置更多的最大檔案資料檔案。 一般來說，每個 CPU 的伺服器上建立一個資料檔，然後調整的數目視檔案向上或向下。 請注意，雙核心 CPU 被視為兩個 CPU。 在任何情況下，資料檔案的數目不能大於 8，無論電腦上可用的多少額外的核心。 如需 tempdb 檔案的詳細資訊，請參閱[最佳化 tempdb 效能](https://docs.microsoft.com/sql/relational-databases/databases/tempdb-database)。|  
|將最小值和相同的值，SQL Server 上的最大伺服器記憶體 instance(s) 裝載 BizTalk Server 資料庫。|SQL Server 電腦裝載 BizTalk Server 資料庫應該專用於執行 SQL Server。 當 SQL Server 電腦裝載 BizTalk Server 資料庫**是**專門用來執行 SQL Server，我們建議的最小伺服器記憶體 」 和 「 最大伺服器記憶體 」 設定，以指定每個 SQL Server 執行個體上的選項固定配置給 SQL Server 的記憶體數量。 在此情況下，您應該設定的 「 最小伺服器記憶體 」 和 「 最大伺服器記憶體 」 為相同的值 （等於 SQL Server 將使用的實體記憶體的最大數量）。 這會降低額外負荷，否則會以動態方式管理這些值的 SQL Server 所使用。 每個執行 SQL Server，來指定要配置給 SQL Server 記憶體的固定的數量的電腦上執行下列 T-SQL 命令：<br /><br /> sp_configure 'Max Server memory (MB)'，（以 mb 為單位的最大大小） sp_configure' Min Server memory (MB)' （以 mb 為單位的最小大小）<br /><br /> 您為 SQL Server 的記憶體數量之前，判斷適當的記憶體設定減去總實體記憶體的 Windows Server 所需的記憶體。 這是您可以指派給 SQL Server 記憶體的最大數量。 **注意：**如果的裝載 BizTalk Server 資料庫也執行 SQL Server 的電腦裝載的企業單一登入主要密碼，本主題中所述[叢集主要密碼伺服器](clustering-the-master-secret-server.md)則可能需要若要調整此值，以確保有足夠的記憶體可用來執行 「 企業單一登入服務。|  
|BizTalk 追蹤資料庫大小|-在決定 BizTalk 追蹤 (DTA) 資料庫中的訊息大小，如果加上訊息內容的平均大小的訊息大小重大訊息大小相較之下。<br />-若要限制 BizTalk 追蹤資料庫中的訊息大小，請限制您將升級的屬性數目。<br />-如果啟用協調流程偵錯工具選項時，考慮到協調流程中每個圖形的狀態儲存在 「 BizTalk 追蹤資料庫中。|  
  
<a name="BKMK_Maintain"></a>   
## <a name="performing-sql-server-maintenance-procedures"></a>執行 SQL Server 維護程序  
  
|步驟|參考|  
|-----------|---------------|  
|定義 BizTalk Server 資料庫的自動成長設定。|自動成長的資料庫應該設數量 （mb），而不是百分比，特別是針對 MessageBox 和追蹤資料庫。 根據您的 BizTalk Server 應用程式和輸送量，MessageBox 與追蹤資料庫可以變得很大。 如果自動成長設為百分比，則自動成長也很嚴重。<br />-立即檔案初始化可大幅減少檔案成長作業的效能影響。<br />-在理想情況下，支援的檔案群組的檔案大小應該預先配置，並可能的話，請設定為靜態的大小。<br /><br /> 如需詳細資訊，請參閱[定義資料庫的自動成長設定](defining-auto-growth-settings-for-databases.md)。|  
|備份 BizTalk Server 資料庫|-我們建議您執行 備份 BizTalk Server 」 工作可避免 BizTalk Server 資料庫的交易記錄變得無限制的方式。<br />-您必須還原整個 BizTalk Server 環境上定期執行，以及您應該仔細記錄處理程序。<br />-我們建議您封存舊的備份檔案。<br /><br /> 如需詳細資訊，請參閱[備份資料庫](backing-up-databases.md)。|  
|監控 BizTalk Server SQL 代理程式作業。|監視的健全狀況，這些作業，並確保它們執行無誤。 如需詳細資訊，請參閱[監視 SQL Server Agent 作業](monitoring-sql-server-agent-jobs.md)。|  
|啟用 BizTalk Server 追蹤和封存|「 DTA 清除與封存 」 SQL Agent 作業封存和清除 BizTalk 追蹤資料庫，因而使其不會成長到無法控制的舊資料。 這是不可或缺的狀況良好的 BizTalk Server 系統。 如需詳細資訊，請參閱[清除和封存追蹤資料](purging-and-archiving-tracking-data.md)。|  
  
<a name="BKMK_Backup"></a>   
## <a name="backing-up-the-biztalk-server-databases"></a>備份 BizTalk Server 資料庫  
  
|步驟|參考|  
|-----------|---------------|  
|確認已設定備份 BizTalk Server SQL 代理程式作業。|請參閱[設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|設定備份 BizTalk Server SQL Agent 工作以刪除比指定天數還舊的備份檔案@DaysToKeep變數。 如果不會刪除備份檔案可以成長 unbounded 經過一段時間，這可能會填滿磁碟上包含備份檔案，並會造成問題，與磁碟空間有限。|請參閱[設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|請確認備份 BizTalk Server SQL 代理程式作業已啟用且正在執行。|[監視 SQL Server Agent 作業](monitoring-sql-server-agent-jobs.md)|  
  
<a name="BKMK_Disaster"></a>   
## <a name="using-sql-server-log-shipping-for-disaster-recovery"></a>使用 SQL Server 記錄傳送災害復原  
  
|步驟|參考|  
|-----------|---------------|  
|請確認嚴重損壞修復伺服器有能力處理生產負載。|請參閱[使用 BizTalk Server 記錄傳送災害復原](using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
|請確定您的災害復原常式的細節會完善記載。|請參閱[使用 BizTalk Server 記錄傳送災害復原](using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
|一般測試的作法是容錯移轉至災害復原站台的一部分，尤其是以新的 BizTalk 應用程式會放在生產環境中。|請參閱[使用 BizTalk Server 記錄傳送災害復原](using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
  
<a name="BKMK_Jobs"></a>   
## <a name="monitoring-biztalk-server-sql-agent-jobs"></a>監控 BizTalk Server SQL Agent 工作  
  
|步驟|參考|  
|-----------|---------------|  
|確認 SQL Server Agent 服務正在執行。|請參閱[監視 SQL Server Agent 作業](monitoring-sql-server-agent-jobs.md)|  
|請確認 BizTalk Server 所安裝的 SQL Server Agent 作業已啟用且正在執行成功。|請參閱[監視 SQL Server Agent 作業](monitoring-sql-server-agent-jobs.md)|  
|請確認 BizTalk Server SQL 代理程式作業所及時完成。|請參閱[監視 SQL Server Agent 作業](monitoring-sql-server-agent-jobs.md)|  
  
<a name="BKMK_Purge"></a>   
## <a name="purging-and-archiving-tracking-data"></a>清除和封存追蹤資料  
  
|步驟|參考|  
|-----------|---------------|  
|請確認已正確設定、 啟用以及已成功完成的 SQL Agent 作業 「 DTA 清除與封存 」。|請參閱[設定 DTA 的清除與封存工作](../core/how-to-configure-the-dta-purge-and-archive-job.md)。|  
|請確保工作能夠以最快速度的內送的追蹤資料會產生清除追蹤資料。|請參閱[測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)|  
|檢閱軟清除和硬清除參數，以確保您保持最佳的時間長度的資料。|請參閱[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)。|  
|如果您只需要清除舊資料，而不需要封存第一次，變更的 SQL 代理程式作業來呼叫預存程序 」 dtasp_PurgeTrackingDatabase。 」|請參閱[從 BizTalk 追蹤資料庫清除資料](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)。|  
  
## <a name="next"></a>下一個
  
-   [不應該變更的 SQL Server 設定](sql-server-settings-that-should-not-be-changed.md)  
  
-   [監視與降低資料庫的 IO 競爭](monitoring-and-reducing-database-i-o-contention.md)  
  
-   [檢閱及測試容錯移轉案例的 SQL Server 叢集設定](reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)  
  
-   [定義資料庫的自動成長設定](defining-auto-growth-settings-for-databases.md)  
  
-   [備份資料庫](backing-up-databases.md)  
  
-   [使用 BizTalk Server 記錄傳送進行災害復原](using-biztalk-server-log-shipping-for-disaster-recovery.md)  
  
-   [監視 SQL Server Agent 作業](monitoring-sql-server-agent-jobs.md)  
  
-   [清除和封存追蹤資料](purging-and-archiving-tracking-data.md)