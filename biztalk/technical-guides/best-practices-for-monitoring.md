---
title: 監視的最佳作法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5b180e2-bdd3-4081-9531-d96be7dabe1a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bfb2b5575fe46c1104ddc6b852695fb777275ef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981655"
---
# <a name="best-practices-for-monitoring"></a>監視的最佳做法
本主題提供監視您的 Microsoft BizTalk Server 環境和應用程式的最佳做法。  
  
 **建立，然後再實作您的 BizTalk 應用程式和基礎結構的監視計劃**  
  
- 閱讀本指南，以確保更完整的監視解決方案中監視的主題。 要考慮的因素包括：  
  
  -   將由誰執行每日、 每週、 每月，以及所需的監視工作？  
  
  -   有人會通知的事件、 擱置的訊息或 其他系統或應用程式的失敗？  
  
  -   經過篩選，或指定較低的優先順序，則是 「 預期 」 的例外狀況？  
  
  -   是所有的主控件執行個體的監視，以確保它們會繼續執行？  
  
  -   所有的自訂服務、 自訂事件記錄檔和監視的自訂資料庫？  
  
  -   是 SQL Server 電腦和 BizTalk Server SQL 代理程式監視的作業？  
  
  **可能的話，請安裝監視的應用程式，例如[!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)]才能自動監視您的 BizTalk Server 應用程式和基礎結構**  
  
- 使用 Microsoft System Center Operations Manager 是慣用的方法，如自動監視，因為 BizTalk Server 管理組件會提供 BizTalk Server 中的數百個內建規則。  
  
   如需詳細資訊，請參閱下列資源：  
  
  -   [適用於 System Center Operations Manager 2007 的 Microsoft BizTalk Server 管理封包](http://go.microsoft.com/fwlink/?LinkID=190339)(http://go.microsoft.com/fwlink/?LinkID=190339)。  
  
  -   [如何匯入 Operations Manager 2007 中的管理組件](http://go.microsoft.com/fwlink/?LinkID=98348)(http://go.microsoft.com/fwlink/?LinkID=98348)  
  
  -   [如何標示 BizTalk Server 資料庫以進行自訂監視](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)  
  
  **執行 BizTalk Server Best Practices Analyzer**  
  
- BizTalk Server Best Practices Analyzer 會檢查 BizTalk Server 部署，並產生一份最佳實務標準相關的問題。 工具會執行組態層級驗證，以從不同的資訊來源，例如 Windows Management Instrumentation (WMI) 類別、 SQL Server 資料庫和登錄項目收集資料。 資料然後用以評估部署組態。 此工具會讀取和只會報告和不會修改任何系統的設定，並不是自我調整的工具。  
  
   您可以下載 BizTalk Server Best Practices Analyzer 在[ http://go.microsoft.com/fwlink/?LinkId=83317 ](http://go.microsoft.com/fwlink/?LinkId=83317) (http://go.microsoft.com/fwlink/?LinkId=83317)。  
  
  **執行記錄檔的效能分析工具 (PAL)**  
  
- PAL 是可在免費下載[ https://github.com/clinthuffman/PAL ](https://github.com/clinthuffman/PAL)。 重要的安裝資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。  
  
  **執行記錄檔剖析器**  
  
- 記錄檔剖析器是功能強大、 用途廣泛的工具，提供通用查詢存取以文字為基礎的資料，例如記錄檔、 XML 檔案、 CSV 檔案，以及索引鍵的資料來源上 Windows® 作業系統，例如事件記錄檔、 登錄、 檔案系統和 ActiveDirectory®。 若要使用此工具來查詢大量的記錄資訊。 您可以下載 Log Parser 工具 [http://go.microsoft.com/fwlink/?LinkID=85574](http://go.microsoft.com/fwlink/?LinkID=85574)  
  
  **執行 BizTalk MsgBoxViewer 工具**  
  
  執行[BizTalk MsgBoxViewer 工具](http://go.microsoft.com/fwlink/?LinkId=151930)苀[ http://go.microsoft.com/fwlink/?LinkId=151930 ](http://go.microsoft.com/fwlink/?LinkId=151930)。 這項工具會分析 BizTalk MessageBox 和其他資料庫，並產生包含警告的 HTML 報告與資料庫相關的任何，和其他資訊。 您也可以儲存供稍後使用的報表。 與 BizTalk 應用程式的問題進行疑難排解時，這些報表可能會很有用。  
  
  如果 BizTalk MsgBoxViewer 工具會識別任何問題，執行[結束字元 工具](http://go.microsoft.com/fwlink/?LinkId=151931)網址[ http://go.microsoft.com/fwlink/?LinkId=151931 ](http://go.microsoft.com/fwlink/?LinkId=151931)。 這項工具可讓使用者輕鬆地解決 BizTalk MsgBoxViewer 工具所識別的任何問題。 如需結束字元工具如何與 BizTalk MsgBoxViewer 工具整合的詳細資訊，請參閱[若要解決 BizTalk MsgBoxViewer 所識別的問題使用 BizTalk 結束字元](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932)。  
  
> [!NOTE]  
>  Microsoft 不支援使用這些工具，Microsoft 不保證這些程式的適用性。 請自行承擔使用這些程式的一切風險。  
  
 **請監視優先順序**  
  
-   不斷監控 BizTalk Server 應用程式和基礎結構的務必維護狀況良好的環境。  
  
-   定期評估，並調整您的監視工具，經過一段時間，以及您的 BizTalk Server 應用程式和基礎結構變更。