---
title: "附錄 d： 工具以測量效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 024f4a08-f3fd-4786-8549-0da5463c0bb9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19953e021a2416f777d9b28c14b1eb8516c70c81
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="appendix-d-tools-for-measuring-performance"></a>附錄 d： 工具，以測量效能
本主題說明數個工具，可用來監視和評估 BizTalk Server 環境的效能。  
  
## <a name="performance-analysis-of-logs-pal-tool"></a>效能的記錄分析 (PAL) 工具  
 [PAL 工具](https://github.com/clinthuffman/PAL)用來產生 HTML 為基礎的報表，以圖形方式圖表上的重要效能監視器計數器和當超過這些計數器的臨界值時，會產生警示。 PAL 是絕佳的工具來識別在 BizTalk Server 解決方案，以便適當的資源配置時最佳化解決方案的效能瓶頸。 
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="performance-monitor"></a>效能監視  
 效能監視器能夠以即時或檢閱歷史資料的方式，提供內建 Windows 效能計數器的視覺顯示。  
  
## <a name="log-parser"></a>記錄檔剖析器  
 記錄檔剖析器是功能強大、 靈活的工具，提供通用的查詢文字為基礎的資料，例如記錄檔、 XML 檔案和 CSV 檔案，以及索引鍵的資料來源來存取 Windows® 作業系統，例如事件記錄檔、 登錄、 檔案系統和作用中Directory®。 下載[記錄剖析器](https://www.microsoft.com/download/details.aspx?id=24659)。
  
## <a name="relog"></a>Relog  
 重新記錄公用程式會用來擷取效能計數器的效能監視所建立的記錄檔，並將資料轉換成其他格式，例如 tab 鍵分隔文字檔案 (TSV 文字)、 逗號分隔的文字檔案 (CSV 文字)、 二進位檔案和 SQL 資料庫。 這項資料分析，而且查詢使用其他工具，例如記錄檔剖析器，來產生統計資料的關鍵效能指標 (Kpi)。 
  
## <a name="loadgen"></a>LoadGen  
 BizTalk LoadGen 2007 是用來執行 BizTalk Server 中的效能和壓力測試的負載產生工具。 下載[BizTalk LoadGen 2007 工具](https://www.microsoft.com/download/details.aspx?id=14925)。
  
## <a name="visual-studio-team-system-load-testing"></a>Visual Studio Team System 負載測試  
 Visual Studio Team System (VSTS) 提供用來建立和執行負載測試的工具。 請參閱[測試應用程式](https://docs.microsoft.com/vsts/manual-test/overview)。
  
## <a name="bizunit"></a>BizUnit  
 BizUnit 是專為 BizTalk Server 解決方案的測試自動化所設計的架構。 BizUnit 是測試端對端 BizTalk Server 實例的絕佳工具。 請參閱[BizUnit](https://github.com/BizUnit/BizUnit)。
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="iometer"></a>IOMeter  
 IOMeter 是開放原始碼工具，可用來測量磁碟 I/O 效能。 請參閱[http://www.iometer.org](http://www.iometer.org/)。
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  

## <a name="pathping"></a>Pathping  
 Pathping 提供的目標主機的方式，就可能發生資料遺失，在一或多個路由器躍點的相關資訊。 若要這樣做，pathping 會將網際網路控制訊息通訊協定 (ICMP) 封包傳送至路徑中的每個路由器。 
  
## <a name="sql-server-tools-for-performance-monitoring-and-tuning"></a>SQL Server 工具的效能監視與微調  
SQL Server 提供數個工具，用於監視 SQL Server 中的事件，以及用來微調實體資料庫設計。 請參閱[效能監視與微調工具](https://docs.microsoft.com/en-us/sql/relational-databases/performance/performance-monitoring-and-tuning-tools)。 
  
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