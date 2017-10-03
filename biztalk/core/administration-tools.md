---
title: "系統管理] 和 [效能工具 |Microsoft 文件"
description: "常見的工具來管理工作、 效能和 BizTalk Server 中的追蹤"
ms.custom: 
ms.date: 09/04/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.ops.admintools
ms.assetid: 932814f7-2ab3-45cb-8bbc-eaf00fcb24a0
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc7420fa6bd59e3653f510e96d41015d266bcebc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="administrative-and-performance-tools"></a>系統管理] 和 [效能工具 

## <a name="tools-list"></a>工具清單
您可以使用下列工具，以管理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、管理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組、部署 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式、與交易夥伴互動、以及監控 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的狀態：  
  
-   **BizTalk Server 管理主控台**。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的主要管理工具。 它提供圖形使用者介面，用以執行 BizTalk 應用程式的所有部署作業。 例如，您可以啟動匯入、安裝和匯入精靈，以及新增和移除應用程式的成品，並對應用程式做其他修改。  
  
     使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以使用檢視即時或封存的訊息事件或服務執行個體資料來追蹤的健全狀況程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實作中，找出瓶頸，並監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 您可以檢視特定協調流程、管線或訊息執行個體的技術詳細資料，並查看進入系統之特定訊息的訊息流程。  
  
     如需使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，請參閱[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。  
  
-   **BTSTask 命令列工具**。 BTSTask 可讓您從命令列執行許多管理工作。 如需有關如何使用 BTSTask 的詳細資訊，請參閱[BTSTask 命令列參考](../core/btstask-command-line-reference.md)。  
  
-   **指令碼和程式設計 Api**。 您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
     WMI 物件模型會公開和簡化管理 API。 所有的管理 API 會公開下列某些形式的作業，包括它們所管理、建立、列舉、修改和刪除的每個物件。 WMI 會針對所有 WMI 物件以一致的方式公開此功能。  
  
-   **商務活動監控 (BAM)。** BAM 使用 Microsoft [!INCLUDE[btsOfficeNoVersion](../includes/btsofficenoversion-md.md)] [!INCLUDE[btsExcel](../includes/btsexcel-md.md)]活頁簿，讓商務使用者得以查看商務程序的即時整體檢視。 如需有關 BAM 的詳細資訊，請參閱[使用商務活動監控](../core/using-business-activity-monitoring.md)。  


-   [**BizTalk 健全狀況監視器**](http://blogs.msdn.com/b/biztalkhealthmonitor/ "BizTalk 健全狀況監視器")已由 BizTalk 支援小組建立收集 BizTalk 環境，包括資料表的使用方式和已知的問題的相關資訊。 報表會產生含有潛在的問題區域反白顯示。 請考慮執行這項工具，並檢閱可協助您維護 BizTalk 環境定期輸出。 這會取代 BizTalk MsbBox 檢視器。

-   [**BizTalk 結束字元工具**](https://www.microsoft.com/download/en/details.aspx?id=2846 "BizTalk 結束字元工具")解決資料庫完整性常見問題 BizTalk MsgBox 檢視器輸出中通常出現在 「 BizTalk 支援小組所建立。 一般工作包括移除執行個體，以及清除大型資料表。 如需有關 BizTalk 結束字元工具的詳細資訊，請移至[這篇文章](http://blogs.msdn.com/b/biztalkcpr/archive/2011/02/10/using-biztalk-terminator-to-resolve-issues-identified-by-biztalk-msgboxviewer.aspx)一個 BizTalk 工程師部落格中。

-   [**Microsoft BizTalk LoadGen 2007**](https://www.microsoft.com/downloads/details.aspx?FamilyID=c8af583f-7044-48db-b7b9-969072df1689&displaylang=en "Microsoft BizTalk LoadGen 2007")會產生執行效能和壓力測試您的 Microsoft BizTalk Server 應用程式的訊息傳輸載入和提供效能計數器來監視執行 BizTalk Server 基礎結構的效能。

-   [**BizTalk Server Best Practices Analyzer**](https://www.microsoft.com/downloads/details.aspx?FamilyID=93d432fe-1370-4b6d-aaa8-a0c43c30f5ab "BizTalk Server Best Practices Analyzer")僅讀取和報告，執行組態層級驗證。 最佳做法分析程式會從不同的資訊來源，例如 Windows Management Instrumentation (WMI) 類別、 SQL Server 資料庫和登錄項目收集資料。 最佳做法分析程式評估部署組態使用的資料。 最佳做法分析程式不會修改任何系統設定，並不是自我調整工具。

-   [**效能分析的記錄檔 (PAL)**](http://www.codeplex.com/PAL "效能分析的記錄檔 (PAL)")複雜，但已知是功能強大的工具可讀取效能監視器計數器記錄檔 （任何已知的格式），且會使用分析臨界值 （提供）。 此工具會產生 HTML 報表的圖表上的重要效能計數器以圖形方式和當超過閾值時，會擲回警示。

-   [**DebugView 適用於 Windows 的**](https://technet.microsoft.com/en-us/sysinternals/bb896647.aspx "DebugView 適用於 Windows 的")是可讓您監視您的本機系統上的偵錯輸出或可透過 TCP/IP 存取網路上的任何電腦的應用程式。 它是可顯示核心模式和 Win32 偵錯輸出，因此您不需要的偵錯工具攔截偵錯輸出會產生您的應用程式或裝置驅動程式，也不需要修改您的應用程式或驅動程式来使用非標準的偵錯輸出應用程式開發介面。

-   [**記錄剖析器 2.2**](https://www.microsoft.com/downloads/details.aspx?familyid=890CD06B-ABF8-4C25-91B2-F8D975CF8C07&displaylang=en "記錄檔剖析器 2.2")是功能強大、 靈活的工具，提供 Windows 通用的查詢文字為基礎的資料，例如記錄檔、 XML 檔案和 CSV 檔案，以及索引鍵的資料來源來存取例如在事件記錄檔、 登錄、 檔案系統和 Active Directory 的作業系統。

-   [**處理總管**](https://technet.microsoft.com/en-us/sysinternals/bb896653.aspx "處理序總管")適用於追蹤 DLL 版本問題或控制代碼遺漏，以及提供深入的方式 Windows 和應用程式工作。

-   [**TCP 追蹤**](http://www.pocketsoap.com/tcptrace/ "TCP 追蹤")用來監視用戶端與伺服器之間的文字為基礎網路流量。 使用 SOAP、 HTTP、 POP3 等類似配接器，以查看訊息透過網路移動時很有用。

-   [**DTCPing**](https://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=5e325025-4dcd-4658-a549-1d549ac17644 "DTCPing")設計來協助疑難排解 Microsoft DTC 防火牆問題，您通常會在多伺服器的 BizTalk 部署中看到。

  
## <a name="see-also"></a>另請參閱  
 [應用程式部署和管理工具](../core/application-deployment-and-management-tools.md)