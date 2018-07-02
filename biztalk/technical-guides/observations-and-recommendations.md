---
title: 觀察與建議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 88289080-1a59-4ffc-a0b2-312ec21940c2
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf134382be6086a1a3ab96fa649fa6cbb41d9bad
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980071"
---
# <a name="observations-and-recommendations"></a>觀察與建議
## <a name="test-results-summary"></a>測試結果摘要  
 僅限傳訊案例的結果中未觀察到為 ~ 109,382,400 每天的訊息。 協調流程案例中，結果會指出執行 BizTalk Server 的單一電腦可以處理最多 58,752,000 每天的訊息。 在沙箱環境中使用一般的企業級部署許多 BizTalk Server 解決方案的硬體，已達到這些結果。 因此，這些結果表示 BizTalk Server 效能的型別可透過任何自訂程式碼。 客戶解決方案通常涉及自訂開發的 BizTalk 成品、在許多情況下這會增加處理需求這進而會影響效能。 依照本指南中，所述的建議特別[最佳化 BizTalk Server 應用程式](../technical-guides/optimizing-biztalk-server-applications.md)區段中，實作自訂開發 BizTalk Server 成品可以降到最低的影響。  
  
 下表提供此效能評定的測試結果的摘要。  
  
|狀況|傳訊 (BizTalk KPI – 每秒處理的文件)|傳訊 (SQL KPI – SQL 處理器使用率)|傳訊延遲 （秒）|協調流程 (BizTalk KPI – 每秒處理的文件)|協調流程 (SQL KPI – SQL 處理器使用率)|協調流程的延遲 （秒）|  
|--------------|----------------------------------------------------------------|-------------------------------------------------------|-----------------------------------|--------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------------|  
|單一 MessageBox 1 BizTalk Server 電腦|每秒處理的 1266年文件|59%SQL CPU 使用率|0.06|每秒處理的 680 文件|66.5%SQL CPU 使用率|0.067|  
|單一 MessageBox 2 BizTalk Server 電腦|每秒處理的 1267年文件|59.8%SQL CPU 使用率|0.057|每秒處理的 686 文件|68.5%SQL CPU 使用率|0.067|  
|3 個 MessageBox 1 BizTalk Server 電腦|每秒處理的 2102年文件|41%SQL CPU 使用率|0.077|每秒處理的一份列出 974 文件|48%SQL CPU 使用率|0.11|  
|3 個 MessageBox 2 BizTalk Server 電腦|每秒處理的 2285年文件|第 58%SQL CPU 使用率|0.041|每秒處理的 1065年文件|65%SQL CPU 使用率|0..69|  
|4 個 Messagebox 1 BizTalk Server 電腦|每秒處理的 2125年文件|30%SQL CPU 使用率|0.078|每秒處理的 979 文件|37%SQL CPU 使用率|0.095|  
|4 個 MessageBoxes 2 BizTalk Server 電腦|每秒處理的 2790年文件|50%SQL CPU 使用率|0.052|每秒處理的 1487年文件|63%SQL CPU 使用率|0.15|  
|4 個 MessageBoxes 3 BizTalk Server 電腦|每秒處理的 2656年文件|第 58%SQL CPU 使用率|0.074|每秒處理的 1388年文件|65%SQL CPU 使用率|0.15|  
  
## <a name="comparison-of-performance-statistics-with-biztalk-server-2009"></a>搭配 BizTalk Server 2009 的效能統計資料的比較  
 下表顯示 BizTalk Server 2009 和 BizTalk Server 2010 之間的效能統計資料的比較。 下表所列的 BizTalk Server 2009 效能統計資料是從 BizTalk Server 2009 效能和最佳化指南。  
  
|狀況|BizTalk Server 2009<br /> 最大持續輸送量 (MST) msgs/sec|BizTalk Server 2009<br />BizTalk Server 所需的數目|BizTalk Server 2010<br />最大持續輸送量 (MST) msgs/sec|BizTalk Server 2010<br />BizTalk Server 所需的數目|BizTalk Server 2010 的差異 %從 BizTalk Server 2009|  
|--------------|----------------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------------------------------------|  
|訊息-單一 MessageBox|1291|2|1266|@shouldalert|98.06%|  
|協調流程-單一 MessageBox|676|2|680|@shouldalert|100.59%|  
|訊息-3 個 Messagebox|2103|3|2285|2 （2102年每秒 1 BTS 與）|108.65%|  
|訊息-4 的 Messagebox|不適用|不適用|2790|2|不適用|  
|協調流程-3 個 Messagebox|1005|4|1065|2 （974 每秒 1 BTS 與）|105.97%|  
|協調流程-4 的 Messagebox|不適用|不適用|1487|2|不適用|  
  
 我們在實驗室環境中，使用四個 MessageBox 資料庫時，最大持續輸送量結果如下所示：  
  
- 傳訊案例中，每秒的 2790年文件。  
  
- 協調流程案例中，每秒的 1487年文件。  
  
  **訊息考量**時 BizTalk Server 不會限制訊息大小，和我們所執行的測試，BizTalk Server 2010 使用僅限 2 KB 的訊息所使用的 WCF 配接器的型別為 Wcf-nettcp 配接器。 這符合 BizTalk Server 2009 效能最佳化指南的測試中使用的訊息大小和配接器類型。  
  
  效能改善的驅動程式會：  
  
1.  **硬體已大幅提升**-我們的實驗室中所使用的 SQL Server 電腦是 4 CPU，四核心 （16 核心），@ 2.40 GHz Intel Xeon E7330。 在 2009年測試中，CPU 4 顆四核心 （16 核心），Intel Xeon 2.4 GHz 有人使用。  
  
     在我們的實驗室中使用的 BizTalk Server 電腦是 2-CPU，四核心 （8 核心），Nehalem 超執行緒 (16 個邏輯核心），Intel Xeon X 5570 @ 2.93 GHz。 在 2009年測試中，CPU 2 顆四核心 （8 核心），Intel Xeon 2.33 GHz 有人使用。  
  
2.  **SQL Server 引擎的改進**-2009年中的測試執行 SQL Server 2008，而我們的測試所執行之 SQL Server 2008 R2 為基礎的資料庫平台。  
  
## <a name="recommendations-for-scaling-the-biztalk-server-and-sql-server-tiers"></a>建議用於調整 BizTalk Server 和 SQL Server 層  
 與這些結果中，BizTalk Server 產品小組無法示範，單一的 BizTalk Server 電腦和單一的 SQL Server 電腦可以支援超過 109 百萬封訊息中訊息的案例和 58 百萬個協調流程在 24 小時期間內。 藉由調整最適合我們的環境中可用的設定 BizTalk Server 和 SQL 層，我們可以處理每一天和超過 128 萬個協調流程的 over241 百萬封訊息。 結果執行的沙箱環境中使用的許多企業中部署的硬體類別。 如稍早所述，這些數字代表實際的效能，可透過任何自訂程式碼和最佳化的環境的 BizTalk server。  使用額外的硬體，就可以，更佳的效能可能有已完成。 客戶解決方案通常涉及自訂開發 BizTalk 成品會產生額外的處理需求，因此增加資源使用量，進而降低整體效能。 不過，依照下列指南，特別是在建議中所述的建議[最佳化 BizTalk Server 應用程式](../technical-guides/optimizing-biztalk-server-applications.md)的影響可以降到最低。  
  
 結果會示範，向外擴充 BizTalk Server 的電腦數目是有效的向外延展策略是否 MessageBox SQL Server 電腦不是瓶頸。 導致我們的結果指出，新增 BizTalk Server 電腦會變成無效的向外延展技術因為我們觀察到 MessageBox 資料庫中的共用資料表上發生的爭用點的特定時間點之後, 的效能降低。 為獲得最佳結果，您可以從 BizTalk Server 群組與單一 MessageBox 資料庫取得，您應該套用所述的最佳化[最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)。 特別是，您應該確保快速的儲存體子系統，用於 SQL Server 儲存體和 SQL Server 用來儲存 MessageBox 資料庫檔案的邏輯磁碟回應中最短的時間。 測量可接受的讀/寫效能的常用臨界值是 15 毫秒。通常這被測量 avg.Disk sec/Read 和 avg.可以在邏輯磁碟效能物件下找到的磁碟 sec/Write 計數器。 套用所有可用的最佳化來裝載 MessageBox 資料庫的 SQL Server 電腦之後, 就可以新增其他 MessageBox 資料庫。 相同的最佳化技術套用至主要 MessageBox 資料庫也應該套用至次要資料庫。 我們建議您遵循的指導方針[相應放大 SQL Server 層](http://go.microsoft.com/fwlink/?LinkID=158075)(http://go.microsoft.com/fwlink/?LinkID=158075) BizTalk Server 文件。  
  
 若要獲得最佳結果，整個的硬體和軟體堆疊必須是適當的品質，並也正確設定。 首先，很好的品質硬體應該購買額度，包括但不是限於，gigabit 網路、 快速的儲存體 （SAN 或本機 SQL 磁碟 15-K） 和現代的電腦具有多個具有多個核心每一 CPU 的 Cpu。 SQL Server 電腦只能專用於 BizTalk Server 僅處理。 當執行單一的 SQL Server 電腦時，我們建議在建立兩個 SQL 執行個體，另一個用於 BizTalk MessageBox，另一個用於所有其他資料庫。 這可讓執行個體層級設定，以獲得最佳效能的 MessageBox 設定。 最佳化的建議[最佳化效能](../technical-guides/optimizing-performance.md)應套用逐步解說以下列順序：[最佳化作業系統效能](../technical-guides/optimizing-operating-system-performance.md)，[最佳化的網路效能](../technical-guides/optimizing-network-performance.md)，[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)，[後置設定資料庫 Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)和[一般 BizTalk ServerOptimizations1](../technical-guides/general-biztalk-server-optimizations1.md)。 建立專用的檔案群組的 MessageBox 資料庫和配置 SAN Lun，跨這些中所述[最佳化檔案群組的資料庫 2](../technical-guides/optimizing-filegroups-for-the-databases2.md)，可提供相當大的效能改進，取決於您SAN 組態和 LUN 配置。  
  
 若要有效地判斷如何調整 BizTalk Server 或 SQL 層，我們建議，負載測試會執行使用近似實際的生產環境資料的訊息。 之前調整 BizTalk Server 層，請確定 SQL Server 已不是瓶頸，依照中的建議[監視 SQL Server 效能](../technical-guides/monitoring-sql-server-performance.md)。 如果 SQL Server 不是瓶頸，而且沒有任何 BizTalk Server 電腦上的 CPU 空間，您可以藉由修改您的主控件執行個體配置改善輸送量。 請務必建立四個或五個關鍵效能指標 (Kpi)，這可做為所有測試回合的高階比較點。 遵循此建議中，您將能夠快速量測計是否特定變更會降低解決方案的整體效能。  
  
 再相應放大的 SQL Server 層，套用所有的最佳化[最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)。 在客戶效能實驗室的過程中，以下的觀察是該磁碟的儲存體設定 MessageBox 和 TempDb 資料庫特別的是可以提供超過 30%輸送量改進。 時調整多個 MessageBox 資料庫，因為小的效能優勢時從單一的 MessageBox 資料庫向外延展至兩個 MessageBox 資料庫，就已會使用三或四個 MessageBox 資料庫。 如需有關向外擴充 BizTalk Server MessageBox 的詳細資訊，請參閱 <<c0> [ 相應放大 SQL Server 層](http://go.microsoft.com/fwlink/?LinkID=158075)(http://go.microsoft.com/fwlink/?LinkID=158075) BizTalk Server 文件。  
  
## <a name="implemented-optimizations"></a>實作的最佳化  
 本章節提供所有實驗室測試案例已套用的最佳化檢查的清單。  
  
> [!NOTE]  
>  這些應該經過測試，根據您的變更管理程序才能套用這些實際執行環境中。  
  
 套用系統化、 受控制的方式的最佳化，藉由套用一組最佳化，然後測試影響 — 將會導致的最大的效能優勢。 實際解決方案的效能降低可能會造成未定期測試的最佳化影響套用最佳化。  
  
### <a name="checklists-of-optimizations-applied"></a>套用的最佳化功能的檢查清單  
 **平台和網路最佳化**  
  
|Optimization|參考|  
|------------------|---------------|  
|BIOS： 設定效能設定。|[最佳化作業系統效能](../technical-guides/optimizing-operating-system-performance.md)|  
|停用 SQL Server 檔案上的即時掃描。|[最佳化作業系統效能](../technical-guides/optimizing-operating-system-performance.md)|  
|啟用 「 高效能 」 電源計劃在所有 BizTalk Server 和 SQL Server 的電腦上。|[改善作業系統效能的一般指導方針](../technical-guides/general-guidelines-for-improving-operating-system-performance.md)|  
|所有的 BizTalk Server 和 SQL Server 的電腦上，停用防毒軟體。|[改善作業系統效能的一般指導方針](../technical-guides/general-guidelines-for-improving-operating-system-performance.md)|  
  
 **SQL Server 最佳化： 一般**  
  
|Optimization|參考|  
|------------------|---------------|  
|您可以設定 NTFS 檔案配置單位為 64 KB。|[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|安裝 SQL Server 2008 R2。|[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|設定 SQL Server 2008 R2 的資料收集器/倉儲。|[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|請確定適當的 Windows 權限，已擴充為 SQL Server 服務帳戶。|SQL Server 2008 R2: [C4519ce9d014">setting Up Windows Service](http://go.microsoft.com/fwlink/?LinkID=132144) (http://go.microsoft.com/fwlink/?LinkID=132144)|  
|設定適用於 SQL Server 的最小和最大伺服器記憶體。|[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|使用適用於 SQL Server 的帳戶 Windows 鎖定記憶體中的分頁權限授與。|[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|預先調整適當大小的 BizTalk Server 資料庫大小與多個資料檔案...|[後置設定資料庫 Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|設定 SQL Server 用戶端通訊協定。|[疑難排解 SQL Server](http://go.microsoft.com/fwlink/?LinkID=154250) (http://go.microsoft.com/fwlink/?LinkID=154250)|  
|將 tempdb 資料庫分割成多個資料檔案大小相同的 BizTalk Server 使用的每個 SQL Server 執行個體|[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|手動設定 SQL Server 處理序相似性|[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|設定 MSDTC 和停用 DTC 追蹤|[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|作為啟動參數啟用追蹤旗標 T1118，SQL Server 的所有執行個體|[預先設定資料庫 Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
  
 **SQL Server 最佳化： BizTalk 資料庫**  
  
|Optimization|參考|  
|------------------|---------------|  
|設為固定的值並不是百分比值的自動成長的 BizTalk 資料庫。|[後置設定資料庫 Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|移動/分割 BizTalk 資料庫資料和記錄檔來區隔的 LUN。|[後置設定資料庫 Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|請考慮設定特定的 MessageBox 資料庫資料表上的 'text in row' 資料表選項|[後置設定資料庫 Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
  
 **BizTalk 最佳化**  
  
|Optimization|參考|  
|------------------|---------------|  
|個別接收埠、 傳送埠、 協調流程，以及獨立的專用的主機上的追蹤。|[一般 BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|設定輪詢間隔。|[低延遲案例 Optimizations2](../technical-guides/low-latency-scenario-optimizations2.md)|  
|調整 BizTalk 組態檔的最大連接屬性。|"Increase 藉由變更 maxconnection 參數的值允許的 SOAP 和 HTTP 並行的連線數 」 一節[一般 BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|在 BizTalk Server 中的每個節點上定義的 CLR 裝載每個主控件執行個體的參數：<br /><br /> 最大的 IO 執行緒： 250<br /><br /> 最大工作者執行緒： 100<br /><br /> 最小的 IO 執行緒： 25<br /><br /> 最小的工作者執行緒： 25|"定義的 CLR 裝載執行緒值，BizTalk 主控件執行個體 」 一節[一般 BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|增加到 10000 的內含式訊息和內部訊息佇列大小。|[低延遲案例 Optimizations2](../technical-guides/low-latency-scenario-optimizations2.md)|  
|停用 BizTalk Server 群組層級追蹤。|[一般 BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|管理同時執行的外掛式接收的位置、 後端 Web 服務和 IIS 7.5 和 IIS 7.0 整合模式中執行的 WCF 服務可以裝載的 ASP.NET 4 Web 應用程式的要求的數目|[一般 BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|停用 BizTalk Server 主控件節流|[一般 BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
|設定 MSDTC 和停用 DTC 追蹤|[一般 BizTalk Server Optimizations1](../technical-guides/general-biztalk-server-optimizations1.md)|  
  
 **WCF 組態最佳化**  
  
|Optimization|參考|  
|------------------|---------------|  
|每個 WCF 服務，適用於 serviceThrottling 服務行為，並將**maxConcurrentCalls**並**maxConcurrentSessions**為 200。|[最佳化 BizTalk Server WCF 配接器效能](../technical-guides/optimizing-biztalk-server-wcf-adapter-performance.md)|  
|後端 WCF 服務組態檔中設定 serviceThrottling 行為的使用方式。|[最佳化 WCF Web 服務效能](../technical-guides/optimizing-wcf-web-service-performance.md)|  
  
## <a name="see-also"></a>另請參閱  
 [調整生產 BizTalk Server 環境](../technical-guides/scaling-a-production-biztalk-server-environment.md)