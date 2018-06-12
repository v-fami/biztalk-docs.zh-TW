---
title: 效能工具 |Microsoft 文件
description: 調查使用 BizUnit、 IOMeter、 協調流程程式碼剖析工具、 記錄檔剖析器、 LoadGen 和 SQL 工具的 BizTalk Server 效能問題
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d26c17a-3eb9-41a5-b0dc-31b974bf3d9b
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5cff86a15aed9a131ed16086d1aebb33739f5f2
ms.sourcegitcommit: 3371ffd8ceca02e2b3715d53a1e0c0a59045912e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34848934"
---
# <a name="performance-tools"></a>效能工具
本主題提供資訊，您可以使用的工具來評估解決方案效能的 BizTalk Server 上。 本主題中所述的工具有不同的用途。某些專為評估端對端效能強調評估的 BizTalk Server 解決方案的特定層面的效能。  
 
## <a name="bizunit-and-bizunit-designer"></a>BizUnit 和 BizUnit 設計工具  
 BizUnit 是專為自動化測試 BizTalk 解決方案設計的架構。 BizUnit 是測試端對端 BizTalk Server 實例的絕佳工具。 執行自動化測試與 BizUnit BizTalk 解決方案時的主要焦點在於[實作自動化的測試](../technical-guides/implementing-automated-testing.md)一節。 請參閱[BizUnit](https://github.com/BizUnit/BizUnit)。
  
 BizUnit 設計工具是可以快速建立可用於單元測試或執行系統測試分散式應用程式的 BizUnit 測試案例的 GUI。 此工具會在[BizUnit 設計師](http://go.microsoft.com/fwlink/?LinkID=117917)。  
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="iometer"></a>IOMeter  
 IOMeter 是開放原始碼工具，可用來測量磁碟 I/O 效能。 請參閱[ http://www.iometer.org ](http://www.iometer.org/)。
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="log-parser"></a>記錄檔剖析器  
 記錄檔剖析器是功能強大、 靈活的工具，提供通用的查詢文字為基礎的資料，例如記錄檔、 XML 檔案和 CSV 檔案，以及索引鍵的資料來源來存取 Windows® 作業系統，例如事件記錄檔、 登錄、 檔案系統和作用中Directory®。 下載[記錄剖析器](https://www.microsoft.com/download/details.aspx?id=24659)。
  
## <a name="microsoft-biztalk-loadgen"></a>Microsoft BizTalk LoadGen  
 BizTalk LoadGen 是用來執行 BizTalk Server 中的效能和壓力測試的負載產生工具。 下載[BizTalk LoadGen 2007 工具](https://www.microsoft.com/download/details.aspx?id=14925)。
  
## <a name="pathping"></a>Pathping  
 Pathping 提供的目標主機的方式，就可能發生資料遺失，在一或多個路由器躍點的相關資訊。 若要這樣做，pathping 會將網際網路控制訊息通訊協定 (ICMP) 封包傳送至路徑中的每個路由器。 自 Windows 2000 Server，Pathping.exe 是適用於所有 Windows 版本。  
  
## <a name="performance-analysis-of-logs-pal"></a>記錄檔 (PAL) 的效能分析  
 PAL 工具用來產生 HTML 為基礎的報表，以圖形方式重要的效能計數器的圖表顯示當超過這些計數器的臨界值時，會產生警示。 PAL 是絕佳的工具來識別在 BizTalk Server 解決方案，以便適當的資源配置時最佳化解決方案的效能瓶頸。  
  
 如需效能分析的記錄檔 (PAL) 工具的詳細資訊，請參閱[效能分析的記錄檔 (PAL) 工具](https://github.com/clinthuffman/PAL)。
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="performance-monitor"></a>效能監視  
 效能監視器能夠以即時或檢閱歷史資料的方式，提供內建 Windows 效能計數器的視覺顯示。  
  
## <a name="relog"></a>Relog  
 重新記錄公用程式會用來擷取效能計數器的效能監視所建立的記錄檔，並將資料轉換成其他格式，例如 tab 鍵分隔文字檔案 (TSV 文字)、 逗號分隔的文字檔案 (CSV 文字)、 二進位檔案和 SQL 資料庫。 這項資料分析，而且查詢使用其他工具，例如記錄檔剖析器，來產生統計資料的關鍵效能指標 (Kpi)。 
  
## <a name="visual-studio---testing-the-application"></a>Visual Studio-測試應用程式  
 Microsoft Visual Studio Ultimate 和 Professional 包含測試，以協助您定義及使用測試計劃中管理您的測試工作。 請參閱[測試應用程式](https://docs.microsoft.com/vsts/manual-test/overview)。
  
## <a name="visual-studio-profiling-tools"></a>Visual Studio 程式碼剖析工具  
 Visual Studio 程式碼剖析工具可讓您分析自訂.NET 元件 （自訂管線元件、 管線和/或協調流程、 自訂運算質叫用的協助程式元件）。 請參閱，[使用程式碼剖析工具分析應用程式效能](https://docs.microsoft.com/visualstudio/profiling/performance-explorer)。
  
## <a name="windows-performance-analysis-tools"></a>Windows 效能分析工具  
Windows 效能工具分析的各種不同的效能問題，包括應用程式啟動時間，開機問題延遲程序呼叫的設計和插斷活動 （Dpc 及 Isr） 系統的回應性問題，應用程式資源使用方式和插斷的衝擊。  
  
請參閱[Windows 效能分析](https://docs.microsoft.com/windows-hardware/test/weg/performance-tools)。
  
## <a name="sql-server-tools-for-performance-monitoring-and-tuning"></a>SQL Server 工具的效能監視與微調  
 SQL Server 提供數個工具，用於監視 SQL Server 中的事件，以及用來微調實體資料庫設計。 請參閱[效能監視與微調工具](https://docs.microsoft.com/sql/relational-databases/performance/performance-monitoring-and-tuning-tools)。 
  
### <a name="sql-profiler"></a>SQL Profiler  
 Microsoft SQL Server Profiler 可以用來擷取傳送至 SQL Server 的 TRANSACT-SQL 陳述式，這些陳述式的 SQL Server 結果集。 SQL Server 與 SQL Server 緊密整合，因為 SQL Server Profiler 追蹤分析可能會很有用的工具，用於分析讀取和寫入至 SQL Server 資料庫時 BizTalk Server 中可能發生的問題。 請參閱[使用 SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions)。
  
> [!IMPORTANT]  
>  沒有與執行 SQL Profiler 相關聯的額外負荷相當大。 因此 SQL Profiler 是最適合用來在測試或開發環境中使用。 如果您可以使用 SQL Profiler，疑難排解實際執行環境，留意相關聯的額外負荷成本，並據此限制使用 SQL Profiler。  
> 
>  當使用 SQL Profiler 來擷取 TRANSACT-SQL 陳述式，設定 SQL Profiler 來產生輸出的本機磁碟機，而不是磁碟機位於遠端網路共用或其他慢速的裝置，例如，本機的 USB 記憶體隨身碟。  
  
### <a name="sql-trace"></a>SQL 追蹤  
 SQL Server 提供的 SQL Server Database Engine 執行個體上建立追蹤的 TRANSACT-SQL 系統預存程序。 這些系統預存程序可從您自己的應用程式中以手動方式，而不是使用 SQL Server Profiler 建立追蹤。 如此一來，就可以依照您的企業需求撰寫自訂的應用程式。 請參閱[SQL 追蹤](https://docs.microsoft.com/sql/relational-databases/sql-trace/sql-trace)。 
  
> [!NOTE]  
>  當使用 SQL 追蹤來擷取 TRANSACT-SQL 陳述式，設定 SQL 追蹤來產生輸出的本機磁碟機，而不是位於遠端網路共用或其他慢速的裝置上的磁碟機時，例如 USB 快閃磁碟機。  
  
### <a name="sql-activity-monitor"></a>SQL 活動監視器  
SQL Server 活動監視器 」 提供 SQL Server 處理序以及這些處理序如何影響目前的 SQL Server 執行個體的相關資訊。 請參閱[活動監視器](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor)，和[如何： 開啟活動監視器 (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio)。 
  
### <a name="sql-server-data-collection"></a>SQL Server 資料收集  
SQL Server 提供您可以使用來取得及儲存從數個來源蒐集資料的資料收集器。 資料收集器可讓您使用資料收集容器，可讓您決定的範圍與執行 SQL Server 的電腦上的資料收集的頻率。 請參閱[資料收集](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection)。
  
### <a name="sqlio"></a>SQLIO  
 SQLIO 工具是由要評估指定組態的 I/O 容量的 Microsoft 開發的。 正如其名的工具，SQLIO 是測量的 SQL Server 效能上的檔案系統 I/O 影響的寶貴工具。 下載[SQLIO](https://www.microsoft.com/download/details.aspx?id=20163)。
  
## <a name="see-also"></a>另請參閱  
 [尋找並排除瓶頸](../technical-guides/finding-and-eliminating-bottlenecks.md)