---
title: 測試的工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9b71f02-86df-4b03-bd2c-4d4d2014db02
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e88bfee5d45cc1cc7bdc93d8dd50aeb1841e3a28
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009687"
---
# <a name="tools-for-testing"></a>測試的工具
下表列出可用來執行測試的操作的整備狀態相關聯的工具[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
|測試|工具|使用|  
|-------------|----------|---------|  
|**單位和功能測試**|Microsoft Visual Studio|用於測試.NET 程式碼的單元。 如需適用於 Visual Studio 的測試功能的詳細資訊，請參閱[測試應用程式](http://go.microsoft.com/fwlink/?LinkId=159595)(http://go.microsoft.com/fwlink/?LinkId=159595)。|  
||BizUnit|架構，以便進行自動化測試 BizTalk 解決方案是設計。 **注意：** 使用此工具不支援的 Microsoft 和 Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。 <br /><br /> 如需 BizUnit 的詳細資訊，請參閱[BizUnit-自動化分散式系統的測試架構](http://go.microsoft.com/fwlink/?LinkID=85168)(http://go.microsoft.com/fwlink/?LinkID=85168)。|  
||NUnit|用於測試.NET 程式碼的單元。 **注意：** 使用此工具不支援的 Microsoft 和 Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。 <br /><br /> 如需 NUnit 的詳細資訊，請參閱[Nunit](http://go.microsoft.com/fwlink/?LinkID=47931) (http://go.microsoft.com/fwlink/?LinkID=47931)。|  
|**程式碼涵蓋範圍測試**|Visual Studio 2010 程式碼涵蓋範圍|用來確保，透過您的應用程式的所有執行路徑都可以充分地都執行，以及識別無作用的函式或程式碼中的類別。 一般情況下，您應該移除無法連線或從未執行的程式碼。 Microsoft Visual Studio 2010 的程式碼涵蓋範圍功能的詳細資訊請參閱[使用程式碼涵蓋範圍來決定程式碼是正在測試的數量](http://go.microsoft.com/fwlink/?LinkId=210624)(http://go.microsoft.com/fwlink/?LinkId=210624)。|  
|**效能測試**|記錄檔 (PAL) 工具的效能分析|分析效能計數器記錄檔的工具。<br /><br /> 如需效能分析的記錄檔 (PAL) 工具的詳細資訊，請參閱[效能分析的記錄檔 (PAL) 工具](https://github.com/clinthuffman/PAL)。|  
||Microsoft BizTalk LoadGen 2007 工具|用來執行效能和壓力測試的負載產生工具[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。<br /><br /> 下載[LoadGen](https://www.microsoft.com/download/details.aspx?id=14925)|  
||Visual Studio 2010 負載測試|適用於 Visual Studio 2010 Ultimate 版本中，可讓您模擬負載最多 250 個使用者，根據預設，與使用 Visual Studio 負載測試虛擬使用者組件的超過 250 位使用者。 如需有關執行使用 Visual Studio 負載測試，請參閱[測試應用程式效能和壓力](http://go.microsoft.com/fwlink/?LinkId=203129)(http://go.microsoft.com/fwlink/?LinkId=203129)。|  
||[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]協調流程的程式碼剖析工具|用來檢視協調流程追蹤資料的一段指定的時間;有助於判斷效能瓶頸存在協調流程中的位置。 **注意：** 使用此工具不支援的 Microsoft 和 Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。 <br /><br /> 如需有關[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]協調流程程式碼剖析工具，請參閱[BizTalk Server 2006 協調流程 Profiler](http://go.microsoft.com/fwlink/?LinkId=102209) (http://go.microsoft.com/fwlink/?LinkId=102209)。|  
|**Web 服務測試**|soapUI|開放原始碼公用程式可以用來測試 Web 服務。 **注意：** 使用此工具不支援的 Microsoft 和 Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。 <br /><br /> 如需 soapUI 的詳細資訊，請參閱[soapUI.org](http://go.microsoft.com/fwlink/?LinkId=102196) (http://go.microsoft.com/fwlink/?LinkId=102196)。|  
||Fiddler|適合用來查看 HTTP 流量 」 纜線。 」 如需有關如何使用 Fiddler 工具進行偵錯 HTTP 的詳細資訊，請參閱[Fiddler PowerToy-第 1 部分： HTTP 偵錯](http://go.microsoft.com/fwlink/?LinkID=84796)(http://go.microsoft.com/fwlink/?LinkID=84796)。 **注意：** 使用此工具不支援的 Microsoft 和 Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。 <br /><br /> Fiddler 工具可以從下載[簡介 Fiddler](http://go.microsoft.com/fwlink/?LinkID=99357) (http://go.microsoft.com/fwlink/?LinkID=99357)。|  
|**偵錯**|DebugView|核心模式以及 Win32 偵錯輸出，在本機或遠端監視工具。<br /><br /> 如需 DebugView 的詳細資訊，請參閱[DebugView 適用於 Windows 的](http://go.microsoft.com/fwlink/?LinkId=102210)(http://go.microsoft.com/fwlink/?LinkId=102210)。|  
||BizTalk MsgBoxViewer|分析 BizTalk MessageBox 資料庫與其他資料庫，並會產生 HTML 報表包含警告，如果與資料庫相關的任何，和其他資訊。 **注意：** 使用此工具不支援的 Microsoft 和 Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。 <br /><br /> BizTalk MsgBoxViewer 工具可以從下載[BizTalk MsgBoxViewer-從這裡下載最新版本的工具](http://go.microsoft.com/fwlink/?LinkId=151930)(http://go.microsoft.com/fwlink/?LinkId=151930)。|  
||結束字元|解決任何 BizTalk MsgBoxViewer 工具所識別的問題。 如需有關結束字元工具如何與 BizTalk MsgBoxViewer 工具整合的詳細資訊，請參閱[解決 BizTalk MsgBoxViewer 所識別的問題使用 BizTalk 結束字元](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932)。 **注意：** 使用此工具不支援的 Microsoft 和 Microsoft 並不保證此程式的適用性。 請自行承擔使用這個程式的一切風險。 <br /><br /> 結束字元工具可以從下載[結束字元](http://go.microsoft.com/fwlink/?LinkId=151931)(http://go.microsoft.com/fwlink/?LinkId=151931)。|  
||BizTalk Server Best Practices Analyzer|BizTalk Server Best Practices Analyzer 會檢查 BizTalk Server 部署，並產生一份與最佳做法標準相關問題。 工具會執行組態層級驗證，以從不同的資訊來源，例如 Windows Management Instrumentation (WMI) 類別、 SQL Server 資料庫和登錄項目收集資料。 將資料再用於評估的部署組態。 工具讀取然後只會報告不會修改任何系統設定，並不是自我調整工具。<br /><br /> BizTalk Server Best Practices Analyzer 工具可以從下載[BizTalk Server Best Practices Analyzer](http://go.microsoft.com/fwlink/?LinkId=83317) (http://go.microsoft.com/fwlink/?LinkId=83317)。|  
  
## <a name="see-also"></a>請參閱  
 [檢查清單：測試作業整備](~/technical-guides/checklist-testing-operational-readiness.md)