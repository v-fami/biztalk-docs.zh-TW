---
title: 工具和公用程式用於疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c817384f-e328-439d-9c41-a94ed75670ce
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15030040702b8c9150681b5ff31449d6c4c299d0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008415"
---
# <a name="tools-and-utilities-to-use-for-troubleshooting"></a>疑難排解使用的工具和公用程式
本章節描述數個工具和公用程式，可用於診斷中的 Microsoft BizTalk Server 元件或相依性問題的根本原因。  
  
## <a name="event-viewer"></a>事件檢視器  
 BizTalk Server 記錄檔的詳細資訊，警告，以及錯誤記錄到事件記錄，BizTalk Server 的電腦。 疑難排解 BizTalk Server 元件或相依性中的問題，事件記錄檔應該尋找可協助您診斷問題的資訊的第一個位置。 
  
## <a name="network-monitor"></a>網路監視器  
 您可以使用網路監視器公用程式來擷取 BizTalk Server 和遠端用戶端或伺服器之間的網路流量。 分析擷取到的網路監視器即可診斷和網路相關的問題。  
  
 Windows Server 上使用網路監視器。  
  
 Windows XP 所提供的網路監視器功能，需透過和 Windows 支援工具 (位在 Windows XP CD 上) 一起安裝的 NETCAP.exe 公用程式才能使用。 如需有關此 NETCAP.exe 公用程式，請參閱[網路監視器擷取公用程式的說明](http://go.microsoft.com/fwlink/?LinkId=66227)。  
  
 如需如何使用網路監視器擷取網路傳輸的資訊，請參閱[如何使用網路監視器擷取網路傳輸](http://go.microsoft.com/fwlink/?LinkId=66230)。  
  
## <a name="fiddler-tool"></a>Fiddler 工具  
 您可以使用 Fiddler 可以記錄 BizTalk Server 和遠端用戶端或伺服器之間的所有 HTTP 流量。 Fiddler 與 Visual Studio Team Edition for Testers 相容，而且可以讓您將記錄項目儲存成 Web 測試檔案，以便加入至 Visual Studio Team Edition for Testers 專案中。  
  
 Fiddler 的缺點是目前無法支援 SSL、無法自動追蹤隱藏欄位 (例如 ViewState)，而且無法篩選相依要求。  
  
 Fiddler 會位於[http://www.fiddlertool.com](http://go.microsoft.com/fwlink/?LinkId=119605)。 
  
## <a name="sql-server-profiler"></a>SQL Server Profiler  
 Microsoft SQL Server Profiler 可以用來擷取傳送至 SQL Server 的 TRANSACT-SQL 陳述式，這些陳述式的 SQL Server 結果集。 由於 BizTalk Server 已緊密地與 SQL Server 整合，因此 SQL Server Profiler 追蹤的分析是相當有用的工具，可用於分析讀取和寫入 SQL Server 資料庫時 BizTalk Server 中可能發生的問題。 
  
## <a name="sql-server-query-editor"></a>SQL Server 查詢編輯器  
 SQL Server 查詢編輯器可以用來直接對 SQL Server 資料庫執行 SQL 陳述式。 在某些情況中，這個功能可能有助於查詢 BizTalk Server 資料庫或更新 BizTalk Server 資料庫。 
  
## <a name="dtctester"></a>DTCTester  
 大部分 BizTalk Server 執行階段作業都需要 Microsoft 分散式交易協調器 (MSDTC) 支援，以確保作業在交易上的一致。 如果沒有 MSDTC 交易支援，則關聯的 BizTalk Server 執行階段作業將無法繼續。 使用 DTCTester 工具可以跨防火牆或針對網路檢查是否有分散式交易支援。 DTCTester 公用程式會使用 ODBC 針對 SQL Server 資料庫檢查是否有交易支援，因此，要進行測試的其中一台電腦上必須安裝 SQL Server。 如需 DTCTester 的詳細資訊，請參閱[如何使用 DTCTester 工具](http://support.microsoft.com/kb/293799)。  
  
## <a name="dtcping"></a>DTCPing  
 使用 DTCPing 工具可以跨防火牆或針對網路檢查是否有分散式交易支援。 用戶端和伺服器電腦都必須安裝 DTCPing 工具，當其中一台電腦沒有安裝 SQL Server 時，這是代替 DTCTester 公用程式的不錯方法。 如需使用 DTCPing 來驗證分散式的交易支援的詳細資訊，請參閱[如何疑難排解 MS DTC 防火牆問題](https://support.microsoft.com/help/306843/how-to-troubleshoot-ms-dtc-firewall-issues)。  
  
## <a name="performance-console"></a>效能主控台  
 使用效能主控台可以擷取您 BizTalk Server 環境中的效能監控資料。 請參閱[效能計數器](../core/performance-counters.md)如 BizTalk Server 隨附之效能計數器的完整清單。 
  
## <a name="regmon-filemon-and-debugview"></a>RegMon、FileMon 和 DebugView  
 RegMon 能夠即時顯示登錄存取活動、接聽應用程式對登錄發出的每個呼叫，並記錄結果。 這個工具可讓您識別應用程式無法存取登錄機碼的狀況。 同樣地，FileMon 能夠即時顯示檔案系統活動、接聽應用程式發出的每個系統呼叫並註冊結果。 Debugview 可讓您監控本機系統或網路上任何可透過 TCP/IP 存取之電腦的偵錯輸出。  
  
 RegMon 和 FileMon 都可讓系統管理員測試應用程式，以及識別應用程式對登錄或檔案系統發出的任何呼叫是否發生失敗。 然後系統管理員可以透過變更檔案系統或登錄機碼權限等方式，減緩該失敗所造成的影響。  
  
 DebugView 可讓系統管理員測試應用程式，以及監控本機系統或網路上任何可透過 TCP/IP 存取之電腦的偵錯輸出。  
  
 如需有關這些公用程式的詳細資訊，請參閱[Windows Sysinternals](https://docs.microsoft.com/sysinternals/)。 
  
## <a name="debug-diagnostics-tool-of-the-iis-diagnostics-toolkit"></a>IIS Diagnostics Toolkit 的偵錯診斷工具  
 IIS Diagnostics Toolkit 的偵錯診斷工具可以針對失敗的處理程序產生記憶體傾印，並且對產生的傾印檔案執行基本的分析。 如需使用 IIS Diagnostic Toolkit 偵錯診斷工具擷取記憶體傾印的詳細資訊，請參閱[如何擷取 BizTalk 程序的記憶體傾印](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md)。