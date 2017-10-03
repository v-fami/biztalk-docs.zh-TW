---
title: "效能工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d26c17a-3eb9-41a5-b0dc-31b974bf3d9b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c53894ca4dcf1b1541c020e14a83542a7ce56d56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="performance-tools"></a>效能工具
本主題提供資訊，您可以使用的工具來評估解決方案效能的 BizTalk Server 上。 本主題中所述的工具有不同的用途。某些專為評估端對端效能強調評估的 BizTalk Server 解決方案的特定層面的效能。  
  
## <a name="biztalk-server-orchestration-profiler"></a>BizTalk Server 協調流程程式碼剖析工具  
 BizTalk Server 協調流程分析工具用來檢視追蹤資料的一段指定時間的協調流程，並可用於判斷效能瓶頸存在協調流程中的位置。  
  
 如需 BizTalk Server 協調流程分析工具的詳細資訊，請參閱[BizTalk Server 2006 協調流程 Profiler](http://go.microsoft.com/fwlink/?LinkId=102209) (http://go.microsoft.com/fwlink/?LinkId=102209)。  
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。 也請注意，此公用程式設計來搭配 BizTalk Server 2006，因此可能無法如預期運作 BizTalk Server 2010。  
  
## <a name="bizunit-30-and-bizunit-designer"></a>BizUnit 3.0 和 BizUnit 設計工具  
 BizUnit 是專為自動化測試 BizTalk 解決方案設計的架構。 BizUnit 是測試端對端 BizTalk Server 實例的絕佳工具。 執行自動化測試與 BizUnit BizTalk 解決方案時的主要焦點在於[實作自動化的測試](../technical-guides/implementing-automated-testing.md)一節。 如需 BizUnit 3.0 的詳細資訊，請參閱[BizUnit-自動化分散式系統的測試架構](http://go.microsoft.com/fwlink/?LinkID=85168)(http://go.microsoft.com/fwlink/?LinkID=85168)。  
  
 BizUnit 設計工具是可以快速建立可用於單元測試或執行系統測試分散式應用程式的 BizUnit 測試案例的 GUI。 此工具會在[BizUnit 設計師](http://go.microsoft.com/fwlink/?LinkID=117917)(http://go.microsoft.com/fwlink/?LinkID=117917)。  
  
> [!IMPORTANT]  
>  本指南中，產生的測試案例撰寫 BizUnit 設計工具所 1.x 才相容 BizUnit 2.x。  
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="iometer"></a>IOMeter  
 IOMeter 是開放原始碼工具，可用來測量磁碟 I/O 效能。 如需 IOMeter 的詳細資訊，請參閱[http://www.iometer.org](http://go.microsoft.com/fwlink/?LinkId=122412) (http://go.microsoft.com/fwlink/?LinkId=122412)。  
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="log-parser"></a>記錄檔剖析器  
 記錄檔剖析器是功能強大、 靈活的工具，提供通用的查詢文字為基礎的資料，例如記錄檔、 XML 檔案和 CSV 檔案，以及索引鍵的資料來源來存取 Windows® 作業系統，例如事件記錄檔、 登錄、 檔案系統和作用中Directory®。 記錄檔剖析器會下載[記錄檔剖析器 2.2](http://go.microsoft.com/fwlink/?LinkID=100882) (http://go.microsoft.com/fwlink/?LinkID=100882)。  
  
## <a name="microsoft-biztalk-loadgen-2007"></a>Microsoft BizTalk LoadGen 2007  
 BizTalk LoadGen 2007 是用來執行效能和壓力測試負載產生工具[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。  
  
 如需有關 Microsoft BizTalk LoadGen 2007 工具的詳細資訊，請參閱[Microsoft BizTalk LoadGen 2007 工具](http://go.microsoft.com/fwlink/?LinkId=59841)(http://go.microsoft.com/fwlink/?LinkId=59841)。  
  
## <a name="pathping"></a>Pathping  
 Pathping 提供的目標主機的方式，就可能發生資料遺失，在一或多個路由器躍點的相關資訊。 若要這樣做，pathping 會將網際網路控制訊息通訊協定 (ICMP) 封包傳送至路徑中的每個路由器。 自 Windows 2000 Server，Pathping.exe 是適用於所有 Windows 版本。  
  
## <a name="performance-analysis-of-logs-pal"></a>記錄檔 (PAL) 的效能分析  
 PAL 工具用來產生 HTML 為基礎的報表，以圖形方式重要的效能計數器的圖表顯示當超過這些計數器的臨界值時，會產生警示。 PAL 是絕佳的工具來識別在 BizTalk Server 解決方案，以便適當的資源配置時最佳化解決方案的效能瓶頸。  
  
 如需效能分析的記錄檔 (PAL) 工具的詳細資訊，請參閱[效能分析的記錄檔 (PAL) 工具](http://go.microsoft.com/fwlink/?LinkID=98098)(http://go.microsoft.com/fwlink/?LinkID=98098)。  
  
> [!NOTE]  
>  使用此工具不支援的 Microsoft，Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。  
  
## <a name="performance-monitor"></a>效能監視  
 效能監視器能夠以即時或檢閱歷史資料的方式，提供內建 Windows 效能計數器的視覺顯示。  
  
## <a name="relog"></a>Relog  
 重新記錄公用程式會用來擷取效能計數器的效能監視所建立的記錄檔，並將資料轉換成其他格式，例如 tab 鍵分隔文字檔案 (TSV 文字)、 逗號分隔的文字檔案 (CSV 文字)、 二進位檔案和 SQL 資料庫。 這項資料分析，而且查詢使用其他工具，例如記錄檔剖析器，來產生統計資料的關鍵效能指標 (Kpi)。 重新記錄公用程式隨附[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]和後續版本。  
  
## <a name="visual-studio-2010---testing-the-application"></a>Visual Studio 2010-測試應用程式  
 Microsoft Visual Studio 2010 Ultimate 和 Visual Studio 測試 Professional 2010 現在包含新的應用程式呼叫 Microsoft Test Manager 可協助您定義及使用測試計劃來管理您的測試工作。 如需有關使用負載測試的詳細資訊，請參閱[測試應用程式](http://go.microsoft.com/fwlink/?LinkID=205342)(http://go.microsoft.com/fwlink/?LinkID=205342)。  
  
## <a name="visual-studio-2010-profiling-tools"></a>Visual Studio 2010 程式碼剖析工具  
 Visual Studio 程式碼剖析工具可讓您分析自訂.NET 元件 （自訂管線元件、 管線和/或協調流程、 自訂運算質叫用的協助程式元件）。 如需有關 Visual Studio 程式碼剖析工具，請參閱[使用程式碼剖析工具分析應用程式效能](http://go.microsoft.com/fwlink/?LinkID=210555)(http://go.microsoft.com/fwlink/?LinkID=210555)。  
  
## <a name="windows-performance-analysis-tools"></a>Windows 效能分析工具  
 Windows 效能工具分析的各種不同的效能問題，包括應用程式啟動時間，開機問題延遲程序呼叫的設計和插斷活動 （Dpc 及 Isr） 系統的回應性問題，應用程式資源使用方式和插斷的衝擊。  
  
 如需有關 Windows 效能分析工具的詳細資訊，請參閱[Windows 效能分析](http://go.microsoft.com/fwlink/?LinkId=139763)(http://go.microsoft.com/fwlink/?LinkId=139763)。  
  
## <a name="sql-server-tools-for-performance-monitoring-and-tuning"></a>SQL Server 工具的效能監視與微調  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供數個工具來監視事件中的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]以及用來微調實體資料庫設計。 這些工具，請參閱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 主題[效能監視和微調工具](http://go.microsoft.com/fwlink/?LinkId=146357)(http://go.microsoft.com/fwlink/?LinkId=146357)。 用於特定工具的相關資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]下面提供效能監視及調整：  
  
### <a name="sql-profiler"></a>SQL Profiler  
 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler 可以用來擷取傳送至 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 Transact-SQL 陳述式，以及這些陳述式的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 結果集。 因為[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]與緊密整合[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，分析[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]追蹤設定檔可以是有用的工具，分析中可能發生的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]讀取和寫入時[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫。 如需有關如何使用資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]程式碼剖析工具，請參閱[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]線上叢書 》 主題[使用 SQL Server Profiler](http://go.microsoft.com/fwlink/?linkid=104423) (http://go.microsoft.com/fwlink/?linkid=104423)。  
  
> [!IMPORTANT]  
>  沒有與執行 SQL Profiler 相關聯的額外負荷相當大。 因此 SQL Profiler 是最適合用來在測試或開發環境中使用。 如果您可以使用 SQL Profiler，疑難排解實際執行環境，留意相關聯的額外負荷成本，並據此限制使用 SQL Profiler。  
  
> [!NOTE]  
>  當使用 SQL Profiler 來擷取 TRANSACT-SQL 陳述式，設定 SQL Profiler 來產生輸出的本機磁碟機，而不是磁碟機位於遠端網路共用或其他慢速的裝置，例如，本機的 USB 記憶體隨身碟。  
  
### <a name="sql-trace"></a>SQL 追蹤  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供的 SQL Server Database Engine 執行個體上建立追蹤的 TRANSACT-SQL 系統預存程序。 這些系統預存程序可從您自己的應用程式中以手動方式，而不是使用 SQL Server Profiler 建立追蹤。 如此一來，就可以依照您的企業需求撰寫自訂的應用程式。 如需有關如何使用 SQL 追蹤的詳細資訊，請參閱[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]線上叢書 》 主題[簡介 SQL 追蹤](http://go.microsoft.com/fwlink/?LinkId=146354)(http://go.microsoft.com/fwlink/?LinkId=146354)。  
  
> [!NOTE]  
>  當使用 SQL 追蹤來擷取 TRANSACT-SQL 陳述式，設定 SQL 追蹤來產生輸出的本機磁碟機，而不是位於遠端網路共用或其他慢速的裝置上的磁碟機時，例如 USB 快閃磁碟機。  
  
### <a name="sql-activity-monitor"></a>SQL 活動監視器  
 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]活動監視器提供下列相關資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]處理程序以及這些處理序如何影響目前的執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 如需有關[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]活動監視器，請參閱[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]線上叢書 》 主題[活動監視器](http://go.microsoft.com/fwlink/?LinkId=146355)(http://go.microsoft.com/fwlink/?LinkId=146355)。 如需有關如何開啟活動監視器的資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio，請參閱[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]線上叢書 》 主題[如何： 開啟活動監視器 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=135094) (http://go.microsoft.com/fwlink/?LinkId=135094)。  
  
### <a name="sql-server-2008-r2-data-collection"></a>SQL Server 2008 R2 資料收集  
 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] 提供資料收集器，您可用它來取得及儲存從數個來源蒐集而來的資料。 資料收集器可讓您使用資料收集容器，而這些容器可讓您在執行 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] 的電腦上決定資料收集的範圍與頻率。 如需有關實作[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]資料收集，請參閱[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]線上叢書 》 主題[資料收集](http://go.microsoft.com/fwlink/?LinkId=146356)(http://go.microsoft.com/fwlink/?LinkId=146356)。  
  
### <a name="sqlio"></a>SQLIO  
 SQLIO 工具是由要評估指定組態的 I/O 容量的 Microsoft 開發的。 SQLIO 名所示的工具，是重要的工具，測量上的檔案系統 I/O 影響[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]效能。 您可以從下載 SQLIO [SQLIO 磁碟子系統的基準工具](http://go.microsoft.com/fwlink/?LinkId=115176)(http://go.microsoft.com/fwlink/?LinkId=115176)。  
  
## <a name="see-also"></a>另請參閱  
 [尋找並排除瓶頸](../technical-guides/finding-and-eliminating-bottlenecks.md)