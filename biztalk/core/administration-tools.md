---
title: 系統管理] 和 [效能工具 |Microsoft Docs
description: 常用的工具來管理工作、 效能和 BizTalk Server 中的追蹤
ms.custom: ''
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 932814f7-2ab3-45cb-8bbc-eaf00fcb24a0
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e345e001d354cf925a68bc33d43f09bb42ad2761
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980495"
---
# <a name="administrative-and-performance-tools"></a>系統管理] 和 [效能工具 

## <a name="tools-list"></a>工具清單
您可以使用下列工具來管理 BizTalk ServerBizTalk 伺服器，來管理 BizTalk Server 群組，來部署 BizTalk Server 應用程式，以與企業合作夥伴互動並監視 BizTalk Server 的狀態：  
  
- **BizTalk Server 管理主控台**。 BizTalk Server 管理主控台是 BizTalk Server 的主要管理工具。 它提供圖形使用者介面，用以執行 BizTalk 應用程式的所有部署作業。 例如，您可以啟動匯入、安裝和匯入精靈，以及新增和移除應用程式的成品，並對應用程式做其他修改。  
  
   使用 BizTalk Server 管理主控台，您可以使用檢視即時或封存的訊息事件或服務執行個體資料追蹤的 BizTalk Server 實作健全狀況、 找出瓶頸，並監視 BizTalk Server 環境。 您可以檢視特定協調流程、管線或訊息執行個體的技術詳細資料，並查看進入系統之特定訊息的訊息流程。  
  
   如需使用 BizTalk Server 管理主控台的資訊，請參閱[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。  
  
- **BTSTask 命令列工具**。 BTSTask 可讓您從命令列執行許多管理工作。 如需使用 BTSTask 的詳細資訊，請參閱[BTSTask 命令列參考](../core/btstask-command-line-reference.md)。  
  
- **指令碼處理和可程式性 Api**。 您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
   WMI 物件模型會公開和簡化管理 API。 所有的管理 API 會公開下列某些形式的作業，包括它們所管理、建立、列舉、修改和刪除的每個物件。 WMI 會針對所有 WMI 物件以一致的方式公開此功能。  
  
- **商務活動監控 (BAM)。** BAM 會使用 Microsoft Office Excel 活頁簿，讓商務使用者得以查看商務程序的即時整體檢視。 如需有關 BAM 的詳細資訊，請參閱 <<c0> [ 使用商務活動監控](../core/using-business-activity-monitoring.md)。  


- [**Bhm 狀況監控**](http://blogs.msdn.com/b/biztalkhealthmonitor/ "Bhm 狀況監控")建立由 BizTalk 支援小組，以收集 BizTalk 環境，包括資料表使用方式和已知的問題的相關資訊。 報表會產生含有潛在的問題區域反白顯示。 請考慮執行這項工具，並檢閱輸出，定期執行，以協助維護 BizTalk 環境。 這會取代 BizTalk MsbBox 檢視器。

- [**BizTalk 結束字元工具**](https://www.microsoft.com/download/en/details.aspx?id=2846 "BizTalk 結束字元工具")BizTalk 支援小組，若要解決常見的資料庫完整性問題，通常位於 BizTalk MsgBox 檢視器輸出所建立。 一般工作包括移除執行個體，以及清除大型資料表。 如需有關 BizTalk 結束字元工具的詳細資訊，請移至[這篇文章](http://blogs.msdn.com/b/biztalkcpr/archive/2011/02/10/using-biztalk-terminator-to-resolve-issues-identified-by-biztalk-msgboxviewer.aspx)中 BizTalk 工程師部落格。

- [**Microsoft BizTalk LoadGen 2007** ](https://www.microsoft.com/download/details.aspx?id=14925)產生訊息傳輸負載執行效能和壓力測試您的 Microsoft BizTalk Server 應用程式，並提供效能計數器，可監視的效能執行 BizTalk Server 基礎結構。

- [**BizTalk Server Best Practices Analyzer**](https://www.microsoft.com/downloads/details.aspx?FamilyID=93d432fe-1370-4b6d-aaa8-a0c43c30f5ab "BizTalk Server Best Practices Analyzer")讀取和報告只會執行組態層級驗證。 Best Practices Analyzer 會從不同的資訊來源，例如 Windows Management Instrumentation (WMI) 類別、 SQL Server 資料庫和登錄項目收集資料。 Best Practices Analyzer 會評估部署組態使用的資料。 Best Practices Analyzer 不會修改任何系統的設定，並不是自我調整的工具。

- [**效能分析的記錄檔 (PAL)** ](https://github.com/clinthuffman/PAL)是功能強大的工具可讀取效能監視器計數器記錄檔 （任何已知的格式），且會分析使用複雜，但是已知的臨界值 （提供）。 此工具會產生 HTML 報告，而以圖形方式圖表上的重要效能計數器已超過閾值時，會擲回警示。

- [**針對 Windows DebugView** ](https://docs.microsoft.com/sysinternals/downloads/debugview)是可讓您監視您的本機系統上的偵錯輸出或任何您可以透過 TCP/IP 連線到網路電腦的應用程式。 就能夠顯示核心模式和 Win32 偵錯輸出，因此您不需要偵錯工具攔截您的應用程式或裝置驅動程式產生，偵錯輸出，也不需要修改您的應用程式或驅動程式，若要使用非標準的偵錯輸出的 Api。

- [**記錄剖析器 2.2** ](https://www.microsoft.com/download/details.aspx?id=24659)是功能強大、 用途廣泛的工具，提供 Windows 作業系統，例如事件記錄檔，以文字為基礎的資料，例如記錄檔、 XML 檔案、 CSV 檔案，以及索引鍵的資料來源的通用查詢存取登錄、 檔案系統和 Active Directory 的內容。

- [**處理序總管**](https://docs.microsoft.com/sysinternals/downloads/process-explorer)適合用來追蹤 DLL 版本問題或控制代碼流失，並提供深入的方式 Windows 和應用程式的運作。

- [**TCP 追蹤**](http://www.pocketsoap.com/tcptrace/ "TCP 追蹤")用來監視用戶端與伺服器之間的文字為基礎網路流量。 使用 SOAP、 HTTP、 POP3 等類似的配接器，以查看訊息透過網路移動時很有用。

- [**DTCPing** ](https://www.microsoft.com/download/details.aspx?id=2868)旨在協助進行疑難排解 Microsoft DTC 防火牆問題，您通常會在多伺服器的 BizTalk 部署中看到。

  
## <a name="see-also"></a>另請參閱  
 [應用程式部署和管理工具](../core/application-deployment-and-management-tools.md)