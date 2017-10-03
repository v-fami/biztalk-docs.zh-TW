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
ms.openlocfilehash: 887272c841aacc0eaa85c197854067133166f783
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-d-tools-for-measuring-performance"></a>附錄 d： 工具，以測量效能
本主題描述數個工具，可用來監視和評估效能的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
## <a name="performance-analysis-of-logs-pal-tool"></a>效能的記錄分析 (PAL) 工具  
 PAL 工具用來產生 HTML 為基礎的報表，以圖形方式圖重要的效能監視器計數器和當超過這些計數器的臨界值時，會產生警示。 PAL 是識別中的瓶頸的絕佳工具[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]方案，以便適當的資源配置最佳化解決方案的效能時。 如需效能分析的記錄檔 (PAL) 工具的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkID=98098](http://go.microsoft.com/fwlink/?LinkID=98098)。  
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="performance-monitor"></a>效能監視  
 效能監視器能夠以即時或檢閱歷史資料的方式，提供內建 Windows 效能計數器的視覺顯示。  
  
## <a name="log-parser"></a>記錄檔剖析器  
 記錄檔剖析器是功能強大、 靈活的工具，提供通用的查詢文字為基礎的資料，例如記錄檔、 XML 檔案和 CSV 檔案，以及索引鍵的資料來源來存取 Windows® 作業系統，例如事件記錄檔、 登錄、 檔案系統和作用中Directory®。 記錄檔剖析器會下載[http://go.microsoft.com/fwlink/?LinkID=100882](http://go.microsoft.com/fwlink/?LinkID=100882)。  
  
## <a name="relog"></a>Relog  
 重新記錄公用程式會用來擷取效能計數器的效能監視所建立的記錄檔，並將資料轉換成其他格式，例如 tab 鍵分隔文字檔案 (TSV 文字)、 逗號分隔的文字檔案 (CSV 文字)、 二進位檔案和 SQL 資料庫。 這項資料分析，而且查詢使用其他工具，例如記錄檔剖析器，來產生統計資料的關鍵效能指標 (Kpi)。 重新記錄公用程式隨附[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]和後續版本。  
  
## <a name="loadgen"></a>LoadGen  
 BizTalk LoadGen 2007 是用來執行效能和壓力測試負載產生工具[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。 Microsoft BizTalk LoadGen 2007 工具是下載[http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841)。  
  
## <a name="visual-studio-team-system-2008-load-testing"></a>Visual Studio Team System 2008 負載測試  
 Visual Studio Team System (VSTS) 2008年提供用來建立和執行負載測試的工具。 如需有關使用負載測試，請參閱[http://go.microsoft.com/fwlink/?LinkId=141486](http://go.microsoft.com/fwlink/?LinkId=141486)。  
  
## <a name="bizunit"></a>BizUnit  
 BizUnit 是專為自動化測試的設計架構[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]解決方案。 BizUnit 是絕佳的工具進行測試端對端[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]案例。 如需 BizUnit 3.0 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkID=85168](http://go.microsoft.com/fwlink/?LinkID=85168)。  
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="iometer"></a>IOMeter  
 IOMeter 是開放原始碼工具，可用來測量磁碟 I/O 效能。 如需 IOMeter 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=122412](http://go.microsoft.com/fwlink/?LinkId=122412)。  
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="biztalk-server-orchestration-profiler"></a>BizTalk Server 協調流程程式碼剖析工具  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程的程式碼剖析工具用於取得指定的一段時間追蹤資料的協調流程的合併的檢視。 這可以讓開發人員有深入了解如何處理協調流程和套用的測試涵蓋範圍的層級。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程設定檔可協助識別透過反白顯示長時間執行和錯誤容易出錯的協調流程圖形，它會對有效的效能測試而言非常重要的延遲和程式碼的路徑例外狀況的潛在問題。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程分析工具是下載[http://go.microsoft.com/fwlink/?LinkID=102209](http://go.microsoft.com/fwlink/?LinkID=102209)。  
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="pathping"></a>Pathping  
 Pathping 提供的目標主機的方式，就可能發生資料遺失，在一或多個路由器躍點的相關資訊。 若要這樣做，pathping 會將網際網路控制訊息通訊協定 (ICMP) 封包傳送至路徑中的每個路由器。 自 Windows 2000 Server，Pathping.exe 是適用於所有 Windows 版本。  
  
## <a name="sql-server-tools-for-performance-monitoring-and-tuning"></a>SQL Server 工具的效能監視與微調  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供數個工具來監視事件中的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]以及用來微調實體資料庫設計。 在 「 工具的效能監視和微調 」 主題中描述這些工具[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在線上叢書 》 [http://go.microsoft.com/fwlink/?LinkId=146357](http://go.microsoft.com/fwlink/?LinkId=146357)。 用於特定工具的相關資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]下面提供效能監視及調整：  
  
### <a name="sql-profiler"></a>SQL Profiler  
 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler 可以用來擷取傳送至 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 Transact-SQL 陳述式，以及這些陳述式的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 結果集。 因為[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]與緊密整合[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，分析[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]追蹤設定檔可以是有用的工具，分析中可能發生的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]讀取和寫入時[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫。 如需有關如何使用資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]程式碼剖析工具，請參閱中的 「 使用 SQL Server Profiler"[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]在線上叢書 》 [http://go.microsoft.com/fwlink/?linkid=104423](http://go.microsoft.com/fwlink/?linkid=104423)。  
  
> [!IMPORTANT]  
>  沒有與執行 SQL Profiler 相關聯的額外負荷相當大。 因此 SQL Profiler 是最適合用來在測試或開發環境中使用。 如果您可以使用 SQL Profiler，疑難排解實際執行環境，留意相關聯的額外負荷成本，並據此限制使用 SQL Profiler。  
  
> [!NOTE]  
>  當使用 SQL Profiler 來擷取 TRANSACT-SQL 陳述式，設定 SQL Profiler 來產生輸出的本機磁碟機，而不是磁碟機位於遠端網路共用或其他慢速的裝置，例如，本機的 USB 記憶體隨身碟。  
  
### <a name="sql-trace"></a>SQL 追蹤  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供的 SQL Server Database Engine 執行個體上建立追蹤的 TRANSACT-SQL 系統預存程序。 這些系統預存程序可從您自己的應用程式中以手動方式，而不是使用 SQL Server Profiler 建立追蹤。 如此一來，就可以依照您的企業需求撰寫自訂的應用程式。 如需有關如何使用 SQL 追蹤的詳細資訊，請參閱 「 簡介中的 SQL 追蹤[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]在線上叢書 》 [http://go.microsoft.com/fwlink/?LinkId=146354](http://go.microsoft.com/fwlink/?LinkId=146354)。  
  
> [!NOTE]  
>  當使用 SQL 追蹤來擷取 TRANSACT-SQL 陳述式，設定 SQL 追蹤來產生輸出的本機磁碟機，而不是位於遠端網路共用或其他慢速的裝置上的磁碟機時，例如 USB 快閃磁碟機。  
  
### <a name="sql-activity-monitor"></a>SQL 活動監視器  
 [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]活動監視器提供下列相關資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]處理程序以及這些處理序如何影響目前的執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 如需有關[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]活動監視器，請參閱 「 活動監視器 」 中[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]在線上叢書 》 [http://go.microsoft.com/fwlink/?LinkId=146355](http://go.microsoft.com/fwlink/?LinkId=146355)。 如需有關如何開啟活動監視器的資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio，請參閱 「 如何： 開啟活動監視器 ([!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio) 中[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]在線上叢書 》 [http://go.microsoft.com/fwlink/?LinkId=135094](http://go.microsoft.com/fwlink/?LinkId=135094)。  
  
### <a name="sql-server-2008-data-collection"></a>SQL Server 2008 資料收集  
 [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] 提供資料收集器，您可用它來取得及儲存從數個來源蒐集而來的資料。 資料收集器可讓您使用資料收集容器，而這些容器可讓您在執行 [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] 的電腦上決定資料收集的範圍與頻率。 如需有關實作[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]資料收集，請參閱中的 「 資料集合 」[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]在線上叢書 》 [http://go.microsoft.com/fwlink/?LinkId=146356](http://go.microsoft.com/fwlink/?LinkId=146356)。  
  
### <a name="sql-server-2005-performance-dashboard-reports"></a>SQL Server 2005 績效儀表板報告  
 [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)]效能儀表板報告用來監視並解決效能問題，在您[!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)]資料庫伺服器。 如需有關[!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)]效能儀表板報告，請參閱[http://go.microsoft.com/fwlink/?LinkID=118673](http://go.microsoft.com/fwlink/?LinkID=118673)。  
  
### <a name="sqlio"></a>SQLIO  
 SQLIO 工具是由要評估指定組態的 I/O 容量的 Microsoft 開發的。 SQLIO 名所示的工具，是重要的工具，測量上的檔案系統 I/O 影響[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]效能。 您可以從下載 SQLIO [http://go.microsoft.com/fwlink/?LinkId=115176](http://go.microsoft.com/fwlink/?LinkId=115176)。