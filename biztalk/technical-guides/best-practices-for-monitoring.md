---
title: 監視的最佳作法 |Microsoft 文件
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
ms.openlocfilehash: 51b3d4761c32123db53ea35daf91d0f13d9a2488
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008527"
---
# <a name="best-practices-for-monitoring"></a>監視的最佳作法
本主題提供監視您的 Microsoft BizTalk Server 環境和應用程式的最佳作法。  
  
 **建立，然後實作您的 BizTalk 應用程式和基礎結構的監視計劃**  
  
-   閱讀本指南，以確保更完整的監視解決方案的監視。 要考慮的因素包括：  
  
    -   誰可以執行每日、 每週、 每月，以及所需的監視工作？  
  
    -   有人會通知的事件、 擱置的訊息或其他系統或應用程式失敗？  
  
    -   為 「 預期 」 例外狀況篩選或指定較低的優先權？  
  
    -   是所有的主控件執行個體的監視，以確保它們會繼續執行？  
  
    -   所有的自訂服務、 自訂的事件記錄檔和監視的自訂資料庫？  
  
    -   是 SQL Server 電腦和 BizTalk Server SQL 代理程式監視的工作？  
  
 **可能的話，請安裝監視的應用程式，例如[!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)]才能自動監視您的 BizTalk Server 應用程式和基礎結構**  
  
-   使用 Microsoft System Center Operations Manager 會自動監視，因為 BizTalk Server 管理組件提供數百個內建規則，以便讓 BizTalk Server 的慣用的方法。  
  
     如需詳細資訊，請參閱下列資源：  
  
    -   [System Center Operations Manager 2007 的 Microsoft BizTalk Server 管理組件](http://go.microsoft.com/fwlink/?LinkID=190339)(http://go.microsoft.com/fwlink/?LinkID=190339)。  
  
    -   [如何匯入 Operations Manager 2007 中的管理組件](http://go.microsoft.com/fwlink/?LinkID=98348)(http://go.microsoft.com/fwlink/?LinkID=98348)  
  
    -   [如何標示 BizTalk Server 資料庫以進行自訂監視](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)  
  
 **執行 BizTalk Server Best Practices Analyzer**  
  
-   BizTalk Server Best Practices Analyzer 會檢查 BizTalk Server 部署，並產生一份與最佳做法標準相關問題。 工具會執行組態層級驗證，以從不同的資訊來源，例如 Windows Management Instrumentation (WMI) 類別、 SQL Server 資料庫和登錄項目收集資料。 將資料再用於評估的部署組態。 工具讀取然後只會報告不會修改任何系統設定，並不是自我調整工具。  
  
     您可以下載 BizTalk Server Best Practices Analyzer 在[http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317) (http://go.microsoft.com/fwlink/?LinkId=83317)。  
  
 **執行記錄檔的效能分析工具 (PAL)**  
  
-   PAL 是在免費下載[https://github.com/clinthuffman/PAL](https://github.com/clinthuffman/PAL)。 重要的安裝資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。  
  
 **執行記錄檔剖析器**  
  
-   記錄檔剖析器是功能強大、 靈活的工具，提供通用的查詢文字為基礎的資料，例如記錄檔、 XML 檔案和 CSV 檔案，以及索引鍵的資料來源來存取 Windows® 作業系統，例如事件記錄檔、 登錄、 檔案系統和作用中Directory®。 若要使用此工具來查詢大量的記錄資訊。 您可以下載記錄檔剖析器工具在[http://go.microsoft.com/fwlink/?LinkID=85574](http://go.microsoft.com/fwlink/?LinkID=85574)  
  
 **執行 BizTalk MsgBoxViewer 工具**  
  
 執行[BizTalk MsgBoxViewer 工具](http://go.microsoft.com/fwlink/?LinkId=151930)可從[http://go.microsoft.com/fwlink/?LinkId=151930](http://go.microsoft.com/fwlink/?LinkId=151930)。 此工具會分析 BizTalk MessageBox 資料庫與其他資料庫，並會產生 HTML 報表包含警告，如果與資料庫相關的任何，和其他資訊。 您也可以儲存供稍後使用的報表。 與 BizTalk 應用程式的問題進行疑難排解時，這些報表可能會有用。  
  
 如果 BizTalk MsgBoxViewer 工具識別任何問題，請執行[結束字元工具](http://go.microsoft.com/fwlink/?LinkId=151931)位於[http://go.microsoft.com/fwlink/?LinkId=151931](http://go.microsoft.com/fwlink/?LinkId=151931)。 此工具可讓使用者輕鬆地解決 BizTalk MsgBoxViewer 工具所識別的任何問題。 如需結束字元工具如何與 BizTalk MsgBoxViewer 工具整合的詳細資訊，請參閱[解決 BizTalk MsgBoxViewer 所識別的問題使用 BizTalk 結束字元](http://go.microsoft.com/fwlink/?LinkId=151932)(http://go.microsoft.com/fwlink/?LinkId=151932)。  
  
> [!NOTE]  
>  使用這些工具不支援的 Microsoft，Microsoft 並不保證這些程式的適用性。 請自行承擔使用這些程式的一切風險。  
  
 **請監視優先順序**  
  
-   BizTalk Server 應用程式和基礎結構的一致監視務必維護狀況良好的環境。  
  
-   定期評估，並調整您的監視工具經過一段時間，以及您的 BizTalk Server 應用程式和基礎結構變更。