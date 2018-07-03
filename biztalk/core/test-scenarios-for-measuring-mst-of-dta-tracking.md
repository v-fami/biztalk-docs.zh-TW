---
title: 測量 DAT 追蹤 MST 的測試案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 303dc1d8-baac-4b54-92c8-95c0ce640a76
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3855dfe405e85e33e01642dd1ded5336c8efb892
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994879"
---
# <a name="test-scenarios-for-measuring-mst-of-dta-tracking"></a>測試 DAT 追蹤的測量 MST 案例
為了顯示所有的實際運作方式，並且引進簡單的技術以測量追蹤的最大持續輸送量 (MST)，我們現在會呈現一個已經對其測量追蹤 MST 的測試案例。 我們不僅會提供所牽涉的技術，您也可以使用呈現的資料做為開始預估其他系統追蹤效能的起點。  
  
> [!IMPORTANT]
>  讀者必須注意，本主題包含的資訊代表 Microsoft 在發行日當時對討論之問題的觀點。 由於我們必須回應不斷變化的市場狀況與技術，因此 Microsoft 無法保證發行日之後提出之任何資訊的正確性。  
  
## <a name="test-scenario-topology-and-configuration"></a>測試案例拓撲和組態  
 下圖顯示測試案例的拓撲和組態。  這是可調整大小的增建，其中具有四部 MessageBox 資料庫伺服器、一部專用的 BizTalkDTADb 資料庫伺服器，以及總共七部執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的伺服器。 請注意，在圖中顯示的 BAM 伺服器並沒有在此測試案例中使用。  
  
 **BizTalkDTADb 可持續輸送量**  
  
 ![追蹤效能拓撲](../core/media/trackingperformancetopology.gif "TrackingPerformanceTopology")  
  
 **硬體規格 (BizTalk Server)**  
  
- CPU： 雙重 3 GHz (快取： L2: 512 KB/L3: 1 MB)  
  
- 記憶體： 2 GB 的 RAM  
  
- HDD: 2 X 32 GB/15K 個  
  
  **硬體規格 (SQL Server)**  
  
- CPU： 四個 2 GHz (L2: 512 KB/L3: 1 MB)  
  
- 記憶體︰ 4 GB 的 RAM  
  
- HDD: 2 X 32 GB/15K 個 + SAN  
  
  下圖提供測試案例架構的概觀，其中  
  
- **TP** = 追蹤點，某些項目會追蹤，例如事件或訊息屬性的點。  
  
- **MB** = 訊息內文，訊息內文追蹤目前的點。  
  
  下列解決方案架構顯示具有三個主要組態元件的追蹤組態：  
  
- **預設 DTA 追蹤**。 在已經安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，圖中的所有事件追蹤點都會依預設值開啟。  
  
- **訊息屬性**。 在輸入管線中與解譯器 (DA) 元件關聯的追蹤點，代表從輸入訊息對 10 個屬性的追蹤。 如需如何升級屬性進行追蹤的詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)。  
  
- **訊息主體**。 圖中的兩個訊息內文 (MB) 點，代表會在這些點追蹤訊息內文。 如需有關如何設定訊息內文追蹤的詳細資訊，請參閱 <<c0> [ 設定使用 BizTalk Server 管理主控台追蹤](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef)。  
  
  **測試案例架構**  
  
  ![效能案例](../core/media/performancescenarios.gif "PerformanceScenarios")  
  
## <a name="test-techniques"></a>測試技術  
 FILE 配接器可同時用於接收和傳送。 我們使用負載產生工具 LoadGen 2007，將訊息傳遞到輸入檔案共用。 LoadGen 工具設定為以特定的速率傳遞檔案，因此我們可以在搜尋追蹤 MST 層級時變動負載。 如需使用 LoadGen 工具的詳細資訊，請參閱[使用 Microsoft BizTalk LoadGen 2007 工具](../core/using-the-microsoft-biztalk-loadgen-2007-tool.md)。  
  
 在測試中，我們假設必須在 BizTalkDTADb 資料庫中保留 24 小時。 也就是說，早於 24 小時的任何項目都會從資料庫清除。 封存和清除 SQL 工作的設計，是只要將已封存的資料清除，以便在處理期間不會使任何資料遺失。  
  
 若要完整測試具有此需求的系統，就必須至少執行負載 25 小時，以便包括至少一個封存和清除循環。 我們選擇執行 48 小時整，以便在第一次封存後監視系統 24 小時，進而確定系統能夠持續。 前 24 小時的作用在於建置足以封存 (每 24 小時一次) 的資料以模擬穩定狀態。 系統會在後 24 小時期間受到監視，以決定所有的處理序 (例如，TDDS、封存和清除) 都能跟上輸送量。  
  
 就我們對追蹤行為的瞭解，通常都只需要監視幾個關鍵效能指標 (KPI)，即可決定持續性：  
  
- **實體磁碟閒置的時間，BizTalkDTADb 資料庫資料檔案**。 如果實體磁碟閒置時間接近 0，就是 BizTalkDTADb 資料庫因為追蹤資料、封存活動和 (或) 清除活動的匯和而飽和的良好徵象。  
  
- **Trackingdata 表深度**。 如果 trackingdata 表開始單調地成長 (也就是繼續無限制地成長)，便是清楚的徵象，表示以目前的輸送量速率，TDDS 將資料插入 BizTalkDTADb 資料庫中的速度無法跟上。  
  
- **多工緩衝處理深度**。 有許多原因都會使多工緩衝處理成長。 其中一種會造成多工緩衝處理成長的狀況為：將要追蹤的訊息內文從 MessageBox 資料庫複製到 BizTalkDTADb 資料庫的 SQL 工作落後。 由於在將需要追蹤的訊息成功複製到 BizTalkDTADb 資料庫之前，無法從 MessageBox 資料庫移除這些訊息 (藉由 MessageBox 清除工作達成)，因此，如果複製工作落後，便會造成多工緩衝處理的增加。  
  
  對於大多數的系統而言，只要在負載下監視這三種效能指標，便能提供足夠的資訊以判斷負載是否可以持續。  
  
  **可持續負載下的關鍵效能指標**  
  
  ![追蹤資料庫的效能監視](../core/media/perf-monitor-tracking-db.gif "Perf_Monitor_Tracking_db")  
  
  使用範例案例時，如果每秒鐘接收 20 條訊息的負載，我們便會取得長達 48 小時的關鍵效能指標，如產生之 Perfmon 圖形所示。 請注意在圖形中表示持續性的下列趨勢：  
  
- **BizTalkDTADbdata 深度 （黑線）**。 運用三個發佈的 MessageBox 資料庫，我們可以看到，即使在 24 小時的第一次封存後，trackingdata 資料表的深度也很穩定，而且沒有繼續向上的趨勢。  
  
- **多工緩衝處理深度 （藍線）**。 多工緩衝處理深度在執行時一直都非常穩定，這表示即使封存和清除會消耗資源，所追蹤的訊息 (每則的大小都為 10 KB) 依然能複製到 BizTalkDTADb 資料庫而不落後。  
  
- **BizTalkDTADb 資料庫資料檔案實體的磁碟閒置時間 （紅線）**。 在前 24 小時未進行任何封存和清除工作之前，BizTalkDTADb 資料庫會累積越來越多的資料，這些資料則會隨著 TDDS 插入資料，而造成越來越多的磁碟 I/O (輸入/輸出)。 這點可由實體磁碟閒置時間的穩定下降清楚看出。  
  
   在 24 小時執行清除的卸除 I/O 閒置時間中觀察到，伴隨封存和清除有工作要做的第一次。 之後第一次封存中，清除作業會有工作来執行每分鐘都對早於 24 小時 （請記住，沒有仍在系統上載入），資料會導致接近於零的閒置時間。  
  
   此處的重點在於，當第一次封存發生後，也就是系統已通過第一個「即時 BizTalkDTADb 資料庫資料保留」時間時，磁碟閒置時間便會在系統位於或接近 MST 時變成幾乎為零。 這是因為 BizTalkDTADb 資料庫的瓶頸，幾乎一定會是磁碟 I/O 子系統的速度。  
  
  在許多情況下，測量 MST 時關閉追蹤以做為系統的基準，都會是相當有益的。 例如，在我們的範例中，將所有追蹤關閉時，MST 為每秒 290 則訊息，這是將追蹤開啟時，具有以上所述之功能與 DTA 資料保留時間之系統 MST 的好幾倍。 這告訴我們，將追蹤開啟時，系統很明顯沒有受到充分利用。 也就是說，當追蹤所需要追蹤的事件只支援每秒鐘 20 則訊息的 MST 時，我們就不需要建置能夠支援每秒鐘 290 則訊息的系統。換句話說，假設 BizTalkDTADb 資料庫硬體沒有改變，就只需要比我們的案例中要少得多的 BizTalk 與 MessageBox 資料庫伺服器，即可達成每秒鐘 20 則訊息的輸送量。  
  
## <a name="searching-for-maximum-sustainable-throughput"></a>搜尋最大可持續輸送量  
 既然我們已經看過以 MST 執行之系統的 KPI，讓我們回去討論如何在範例案例中抵達每秒鐘 20 則訊息的 MST。 它是簡單的反覆式 「 二進位搜尋 」 方法，如下所示：  
  
- **挑選起點**。 除非您已經有在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上執行測試的經驗，否則您將需要利用已經在其他系統上達成 MST 的資訊來幫助自己。  
  
   例如，我們已經在此主題中提供適用於範例案例的所有硬體、組態和解決方案架構。 使用該資訊以及我們已經開啟的追蹤類型 (預設值為 + 10 個屬性 + 10KB 的訊息內文)，連同已達成的 MST (每秒 20 則訊息) 和 24 小時的 DTA 資料保留時間，與您的設定和需求比較。  
  
   您應該至少能夠預估自己解決方案的 MST 會高於或低於我們所達成的 MST。 不同的技術案例研究也可以讓您用來與您的系統進行比較。 例如，請參閱提供的案例研究，BizTalk Server 開發人員中心，在[ http://go.microsoft.com/fwlink/?LinkId=49339 ](http://go.microsoft.com/fwlink/?LinkId=49339)。  
  
- **預估的 MST 負載下執行系統，並監視 KPI**。 通常，從預期 MST 的高邊開始，便能縮短尋找 MST 所花費的時間。 藉由從高處開始，您使 KPI 變成飽和 (尤其是磁碟 I/O) 的時間，將會少於發現自己低於 MST 所需要的時間 (也就是至少一個完整的資料保留時間)。  
  
- **改善 MST 預估並重複**。 查看測試執行的結果，改善您的 MST 預估並使用新的預估重複測試。  
  
## <a name="see-also"></a>另請參閱  
 [測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [瞭解 DTA 追蹤效能行為](../core/understanding-dta-tracking-performance-behavior.md)   
 [尋找 DTA 追蹤的 MST 的秘訣和訣竅](../core/tips-and-tricks-for-finding-mst-of-dta-tracking.md)   
 [調整追蹤資料庫大小的指導方針](../core/tracking-database-sizing-guidelines.md)