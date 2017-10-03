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
ms.openlocfilehash: ce0eff1dab6afe81c55f4cffa08c4839762e82ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-configuring-sql-server"></a>檢查清單： 設定 SQL Server
本主題列出當您準備，您應該遵循的步驟[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]或[!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)]用於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實際執行環境。  
  
-   [檢查清單： 設定 SQL Server](../technical-guides/checklist-configuring-sql-server.md)  
  
-   [執行 SQL Server 維護程序](../technical-guides/checklist-configuring-sql-server.md#BKMK_Maintain)  
  
-   [備份 BizTalk Server 資料庫](../technical-guides/checklist-configuring-sql-server.md#BKMK_Backup)  
  
-   [使用 SQL Server 記錄傳送災害復原](../technical-guides/checklist-configuring-sql-server.md#BKMK_Disaster)  
  
-   [監控 BizTalk Server SQL Agent 工作](../technical-guides/checklist-configuring-sql-server.md#BKMK_Jobs)  
  
-   [清除和封存追蹤資料](../technical-guides/checklist-configuring-sql-server.md#BKMK_Purge)  
  
<a name="BKMK_Config"></a>   
## <a name="configuring-sql-server"></a>設定 SQL Server  
  
|步驟|參考|  
|-----------|---------------|  
|監視及降低[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫檔案磁碟 I/O 競爭。|-我們建議您主動監視存放的資料和交易記錄檔磁碟的磁碟 I/O 使用量。<br />-我們建議最好讓資料檔和交易記錄檔的每一種放在專用的磁碟機，以降低磁碟 I/O 競爭變得有問題的可能性。<br />-您可以降低磁碟 I/O 競爭，藉由分隔 MessageBox 和追蹤 (DTA) 資料庫，而且分隔的資料庫檔案和交易記錄檔不同實體磁碟上。<br /><br /> 如需詳細資訊，請參閱[監視及降低資料庫 IO 爭用](~/technical-guides/monitoring-and-reducing-database-i-o-contention.md)|  
|請確定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]上正確對齊的磁碟分割設定|正確對齊的磁碟分割可能會導致明顯降低延遲，藉此改善[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]效能，進而增強[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能。 相反地，非對齊的磁碟分割效能造成負面影響 I/O，因而降低[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能。<br /><br /> 如需有關如何正確對齊的磁碟分割正面可能會影響效能，請參閱 < [「 磁碟分割區對齊最佳作法 for SQL Server"](http://go.microsoft.com/fwlink/?LinkId=154073) (http://go.microsoft.com/fwlink/?LinkId=154073)。|  
|讓您使用 SQL Server Profiler 監視的事件|使用 SQL Server Profiler 來監視只有您感興趣的事件。 如果追蹤變得太大，您可以篩選，收集事件資料的子集，根據您想要的資訊。 監視太多事件會增加伺服器與監視處理序的負擔，且會使得追蹤檔案或追蹤資料表增長過大，尤其是需要花費長時間的監視處理序更是如此。|  
|監視及降低 DTC 記錄檔磁碟 I/O 競爭。|[監視與降低 DTC 記錄檔的磁碟 IO 競爭](~/technical-guides/monitoring-and-reducing-dtc-log-file-disk-i-o-contention.md)|  
|提供的高可用性[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫。|[資料庫可用性規劃](~/technical-guides/planning-for-database-availability.md)|  
|檢閱主動/主動容錯移轉案例的 SQL Server 叢集組態。|[檢閱及測試 SQL Server 叢集組態的容錯移轉案例](~/technical-guides/reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)|  
|使用預設組態設定：<br /><br /> Max Degree of Parallelism (MDOP)。<br />-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]上的統計資料[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫。<br />-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫索引會重建和重組。|[不應該變更的 SQL Server 設定](~/technical-guides/sql-server-settings-that-should-not-be-changed.md)|  
|啟用追蹤旗標 1118 (TF1118) 作為啟動參數的所有執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。|實作 TF1118 有助於減少爭用跨[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]藉由移除幾乎所有的單一頁面配置的執行個體。 如需詳細資訊，請參閱 Microsoft 知識庫文件 328551， ["Tempdb 資料庫的並行存取增強功能"](http://go.microsoft.com/fwlink/?LinkId=153694) (http://go.microsoft.com/fwlink/?LinkId=153694)。 **注意：**的詳細資訊，請參閱 TF1118 ["多疑周圍 TF1118"](http://go.microsoft.com/fwlink/?LinkId=158271) (http://go.microsoft.com/fwlink/?LinkId=158271)。 請注意，在以下連結的內容不 Microsoft 所擁有，Microsoft 不保證內容的正確性。|  
|將 tempdb 資料庫分割成多個資料檔相同大小的每個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]所使用的執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。|確認用於 tempdb 資料檔案都屬於相同大小。 這很重要，因為比例填滿演算法使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]根據資料檔案的大小。 建立資料檔的大小不相等，如果比例填滿演算法會使用全域配置對應 (GAM) 配置，而不是分配之間的所有檔案，藉以定義的目的建立多個配置更多的最大檔案資料檔案。 一般來說，每個 CPU 的伺服器上建立一個資料檔，然後調整的數目視檔案向上或向下。 請注意，雙核心 CPU 被視為兩個 CPU。 在任何情況下，資料檔案的數目不能大於 8，無論電腦上可用的多少額外的核心。 如需 tempdb 檔案的詳細資訊，請參閱[最佳化 tempdb 效能](http://go.microsoft.com/fwlink/?LinkId=158272)(http://go.microsoft.com/fwlink/?LinkId=158272) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]文件。|  
|如果您正在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與裝載您的資料庫執行的電腦上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]具有足夠的實體記憶體，來設定的執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]使用 Address Windowing Extensions (AWE) 記憶體。|在 x86 電腦，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]應該設定為使用 2 GB 以上的實體記憶體。 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]包含支援使用的 Microsoft Windows Address Windowing Extensions (AWE) 來解決 32 GB 的記憶體。 使用 AWE，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可以保留未使用的其他應用程式和作業系統的記憶體。 不過，使用此記憶體中，每個執行個體必須以靜態方式配置記憶體。 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]只能使用此 AWE 配置記憶體的資料快取而非可執行檔、 驅動程式、 Dll 以及其他等等。 如需詳細資訊，請參閱：<br /><br /> Microsoft 知識庫文章 274750， [< 如何設定 SQL Server 使用超過 2 GB 的實體記憶體 >](http://go.microsoft.com/fwlink/?LinkId=153718) (http://go.microsoft.com/fwlink/?LinkId=153718)。<br />-   [使用 AWE](http://go.microsoft.com/fwlink/?LinkId=153720) (http://go.microsoft.com/fwlink/?LinkId=153720) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]文件。<br />-   [適用於 SQL Server 啟用 AWE 記憶體](http://go.microsoft.com/fwlink/?LinkId=158273)(http://go.microsoft.com/fwlink/?LinkId=158273) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]文件。|  
|上設定相同的值的最小值和最大伺服器記憶體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]instance(s) 裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。|執行的電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫只能專用於執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 當執行的電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫**是**專門用來執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，我們建議的最小伺服器記憶體' 和 '最大伺服器記憶體選項，在每個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]設定執行個體，以指定要配置給記憶體固定的量[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 在此情況下，您應該設定的 「 最小伺服器記憶體 」 和 「 最大伺服器記憶體 」 為相同的值 （等於 SQL Server 將使用的實體記憶體的最大數量）。 這會降低額外負荷，否則會使用由[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]以動態方式管理這些值。 在執行每一部電腦上執行下列 T-SQL 命令[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]來指定要配置給記憶體固定的量[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]:<br /><br /> sp_configure 'Max Server memory (MB)'，（以 mb 為單位的最大大小） sp_configure' Min Server memory (MB)' （以 mb 為單位的最小大小）<br /><br /> 在您設定的記憶體數量之前[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，減去總實體記憶體的 Windows Server 所需的記憶體來判斷適當的記憶體設定。 這是您可以指派給記憶體的最大數量[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 **注意：**如果電腦執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫也裝載企業單一登入主要密碼，本主題中所述[叢集主要密碼伺服器](~/technical-guides/clustering-the-master-secret-server.md)然後您可能需要調整此值，以確保有足夠的記憶體可用來執行 「 企業單一登入服務。|  
|BizTalk 追蹤資料庫大小|-在決定 BizTalk 追蹤 (DTA) 資料庫中的訊息大小，如果加上訊息內容的平均大小的訊息大小重大訊息大小相較之下。<br />-若要限制 BizTalk 追蹤資料庫中的訊息大小，請限制您將升級的屬性數目。<br />-如果啟用協調流程偵錯工具選項時，考慮到協調流程中每個圖形的狀態儲存在 「 BizTalk 追蹤資料庫中。|  
  
<a name="BKMK_Maintain"></a>   
## <a name="performing-sql-server-maintenance-procedures"></a>執行 SQL Server 維護程序  
  
|步驟|參考|  
|-----------|---------------|  
|定義自動成長設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。|自動成長的資料庫應該設數量 （mb），而不是百分比，特別是針對 MessageBox 和追蹤資料庫。 根據您的 BizTalk Server 應用程式和輸送量，MessageBox 與追蹤資料庫可以變得很大。 如果自動成長設為百分比，則自動成長也很嚴重。<br />-立即檔案初始化可大幅減少檔案成長作業的效能影響。<br />-在理想情況下，支援的檔案群組的檔案大小應該預先配置，並可能的話，請設定為靜態的大小。<br /><br /> 如需詳細資訊，請參閱[定義資料庫的自動成長設定](~/technical-guides/defining-auto-growth-settings-for-databases.md)。|  
|備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫|-我們建議您執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]備份工作，以避免[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫交易記錄變得無限制的方式。<br />-您必須還原整個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境上定期執行，而且您應該仔細文件程序。<br />-我們建議您封存舊的備份檔案。<br /><br /> 如需詳細資訊，請參閱[備份資料庫](~/technical-guides/backing-up-databases.md)。|  
|監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SQL Agent 作業。|監視的健全狀況，這些作業，並確保它們執行無誤。 如需詳細資訊，請參閱[監視 SQL Server Agent 作業](~/technical-guides/monitoring-sql-server-agent-jobs.md)。|  
|啟用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]追蹤和封存|「 DTA 清除與封存 」 SQL Agent 作業封存和清除 BizTalk 追蹤資料庫，因而使其不會成長到無法控制的舊資料。 這是不可或缺的狀況良好[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。 如需詳細資訊，請參閱[清除和封存追蹤資料](~/technical-guides/purging-and-archiving-tracking-data.md)。|  
  
<a name="BKMK_Backup"></a>   
## <a name="backing-up-the-biztalk-server-databases"></a>備份 BizTalk Server 資料庫  
  
|步驟|參考|  
|-----------|---------------|  
|確認備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定 SQL 代理程式作業。|-了解[< 如何設定 「 備份 BizTalk Server 」 工作 >](http://go.microsoft.com/fwlink/?LinkId=153813) (http://go.microsoft.com/fwlink/?LinkId=153813)。<br />-了解[資料庫分別備份](~/technical-guides/backing-up-databases.md)。|  
|設定備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SQL Agent 作業以刪除比指定天數還舊的備份檔案@DaysToKeep變數。 如果不會刪除備份檔案可以成長 unbounded 經過一段時間，這可能會填滿磁碟上包含備份檔案，並會造成問題，與磁碟空間有限。|請參閱 Microsoft 知識庫文章 982546， [「 備份 BizTalk Server 」 作業失敗時，當備份檔案會累積一段時間，在 Microsoft BizTalk Server 中 Dababase](http://go.microsoft.com/fwlink/?LinkId=202858) (http://go.microsoft.com/fwlink/?LinkId=202858)。|  
|確認備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SQL Agent 作業已啟用且正在執行。|[監視 SQL Server Agent 作業](~/technical-guides/monitoring-sql-server-agent-jobs.md)|  
  
<a name="BKMK_Disaster"></a>   
## <a name="using-sql-server-log-shipping-for-disaster-recovery"></a>使用 SQL Server 記錄傳送災害復原  
  
|步驟|參考|  
|-----------|---------------|  
|請確認嚴重損壞修復伺服器有能力處理生產負載。|請參閱[使用 BizTalk Server 記錄傳送災害復原](~/technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
|請確定您的災害復原常式的細節會完善記載。|請參閱[使用 BizTalk Server 記錄傳送災害復原](~/technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
|一般測試的作法是容錯移轉至災害復原站台的一部分，尤其是以新的 BizTalk 應用程式會放在生產環境中。|請參閱[使用 BizTalk Server 記錄傳送災害復原](~/technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
  
<a name="BKMK_Jobs"></a>   
## <a name="monitoring-biztalk-server-sql-agent-jobs"></a>監控 BizTalk Server SQL Agent 工作  
  
|步驟|參考|  
|-----------|---------------|  
|確認 SQL Server Agent 服務正在執行。|請參閱[監視 SQL Server Agent 作業](~/technical-guides/monitoring-sql-server-agent-jobs.md)|  
|確認 SQL Server Agent 作業安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]啟用，且成功執行。|請參閱[監視 SQL Server Agent 作業](~/technical-guides/monitoring-sql-server-agent-jobs.md)|  
|確認[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SQL 代理程式作業及時完成。|請參閱[監視 SQL Server Agent 作業](~/technical-guides/monitoring-sql-server-agent-jobs.md)|  
  
<a name="BKMK_Purge"></a>   
## <a name="purging-and-archiving-tracking-data"></a>清除和封存追蹤資料  
  
|步驟|參考|  
|-----------|---------------|  
|請確認已正確設定、 啟用以及已成功完成的 SQL Agent 作業 「 DTA 清除與封存 」。|請參閱[< 如何設定 DTA 的清除與封存工作 >](http://go.microsoft.com/fwlink/?LinkId=153814) (http://go.microsoft.com/fwlink/?LinkId=153814)。|  
|請確保工作能夠以最快速度的內送的追蹤資料會產生清除追蹤資料。|請參閱["測量最大持續性追蹤輸送量"](http://go.microsoft.com/fwlink/?LinkId=153815) (http://go.microsoft.com/fwlink/?LinkId=153815)。|  
|檢閱軟清除和硬清除參數，以確保您保持最佳的時間長度的資料。|請參閱[「 封存和清除 BizTalk 追蹤資料庫 」](http://go.microsoft.com/fwlink/?LinkId=153816) (http://go.microsoft.com/fwlink/?LinkId=153816)。|  
|如果您只需要清除舊資料，而不需要封存第一次，變更的 SQL 代理程式作業來呼叫預存程序 」 dtasp_PurgeTrackingDatabase。 」|請參閱[< 如何從 BizTalk 追蹤資料庫清除資料 >](http://go.microsoft.com/fwlink/?LinkId=153817) (http://go.microsoft.com/fwlink/?LinkId=153817)。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [不應該變更的 SQL Server 設定](~/technical-guides/sql-server-settings-that-should-not-be-changed.md)  
  
-   [監視與降低資料庫的 IO 競爭](~/technical-guides/monitoring-and-reducing-database-i-o-contention.md)  
  
-   [檢閱及測試 SQL Server 叢集組態的容錯移轉案例](~/technical-guides/reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)  
  
-   [定義資料庫的自動成長設定](~/technical-guides/defining-auto-growth-settings-for-databases.md)  
  
-   [備份資料庫](~/technical-guides/backing-up-databases.md)  
  
-   [使用 BizTalk Server 記錄傳送災害復原](~/technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)  
  
-   [監視 SQL Server Agent 作業](~/technical-guides/monitoring-sql-server-agent-jobs.md)  
  
-   [清除和封存追蹤資料](~/technical-guides/purging-and-archiving-tracking-data.md)