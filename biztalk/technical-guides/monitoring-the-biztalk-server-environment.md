---
title: 監控 BizTalk Server 環境 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baae51cf-0284-429b-8335-bc1ac3e63f4c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57abd599c10ead5084eae59c9f7dbe1746be346a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299110"
---
# <a name="monitoring-the-biztalk-server-environment"></a>監控 BizTalk Server 環境
您可以監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]基礎結構和應用程式，以手動或自動程序或兩個方法下, 表所示，使用工具的組合。  
  
|手動或自動化監視|工具|  
|------------------------------------|-----------|  
|自動化監視|Microsoft System Center Operations Manager (Operations Manager)|  
|手動監視|-**群組中樞**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台<br />-效能分析的記錄檔 (PAL) 工具<br />事件檢視器|  
  
 不論您實作監視的應用程式，您應該使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來監視的健全狀況程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式，並執行根本原因分析，以識別任何問題的根本原因。  
  
 當監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請記住下列幾點：  
  
-   您的基礎結構可能狀況良好，但應用程式可能不是 (例如，應用程式收到無效的訊息，而且無法處理這些訊息)。  
  
-   您的基礎結構可能狀況不好，但應用程式可能正常運作 (例如，如果某部伺服器停機，但是有指派足夠的伺服器給主控件來接管負載)。  
  
-   基礎結構問題可能會以應用程式問題的形式出現 (例如，由於伺服器停機，造成訊息的處理速度不夠快)。  
  
## <a name="monitoring-types"></a>監視類型  
 監視您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和應用程式可分為四個主要類別：  
  
-   可用性監控  
  
-   健康情況監控  
  
-   效能監控  
  
-   閾值監視  
  
### <a name="availability-monitoring"></a>可用性監控  
 這個問題的答案可用性監視 」 是無法使用的系統或應用程式資源防止您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以最佳方式執行的應用程式嗎？ 」 這些問題大多是系統層級所特有，例如服務和連接的可用性。 例如，如果因為企業單一登入服務停止而造成配接器失敗，這就是可用性問題。 如果指派給主控件的其中一部伺服器失敗了，而應用程式在處理訊息上發生落後，這也是可用性問題。 同樣地，如果應用程式已停止且無法處理訊息，這也是可用性問題。 下表列出可用性監控工具。  
  
|工具|工作|  
|----------|----------|  
|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台|請檢查**群組中樞**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台，以查看應用程式或其元件 （連接埠/協調流程） 已停止。|  
|Operations Manager 2007|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件及 Operations Manager Operations 主控台會顯示警示如果介面卡等重要的低階服務無法使用。 若要有效監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須監視非[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式而定，例如資料庫和伺服器的資源。 此外，您也必須安裝並使用 SQL Server、 Internet Information Services 和 Windows Base 作業系統管理組件。 Operations Manager 將彙總從事件記錄檔、 WMI 和其他事件提供者的感興趣的事件。 如需安裝所有相關的管理組件的詳細資訊，請參閱[檢查清單： 使用 Operations Manager 2007 監視 BizTalk Server](../technical-guides/checklist-monitoring-biztalk-server-with-operations-manager-2007.md)。|  
|事件檢視器|尋找配接器連接問題、停止的服務等等。|  
  
### <a name="health-monitoring"></a>健全狀況監視  
 健康情況監控可解答以下問題：「有任何應用程式或資源處於不良健康情況嗎？」 例如，目前有任何應用程式或其構成成品遇到例外狀況嗎？ 或者，是否因為訊息內容中的無效資料造成訊息擱置？ 下表列出健康情況監控工具。  
  
|工具|工作|  
|----------|----------|  
|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台|您使用**群組中樞**頁面和中的查詢頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來識別應用程式健全狀況問題，並分析其原因。|  
|Operations Manager|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件是您第一次的第一線，它會通知您，您有擱置的訊息及/或服務執行個體中的您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。 在從 Operations Manager 收到通知，您可以轉換至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來疑難排解問題。|  
|事件檢視器|偵測訊息和協調流程的處理期間所發生的問題。|  
  
### <a name="performance-monitoring"></a>效能監控  
 效能監控會解答以下問題：「系統執行工作的效率如何？」 這種監控主要著重於實體資源 (如資料庫和磁碟) 的負載。 例如，如果 CPU 使用率持續維持在百分之 90 和 100，而且形成了訊息的積存，這就是電腦層級的效能問題。 下表列出效能監控工具。  
  
|工具|工作|  
|----------|----------|  
|SQL Query Analyzer|監控資料庫大小及內容，以診斷系統問題。|  
|Operations Manager|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]顯示重大警示，則可以設定管理組件和 Operations Manager Operations 主控台[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能計數器，例如訊息方塊佇列大小或主控件佇列大小超出定義的閾值。 若要監視的非效能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資源，取決於您的應用程式，例如資料庫和伺服器，您也必須安裝並且使用 SQL Server、 Internet Information Services 和 Windows Base 作業系統管理組件。 如需安裝所有相關的管理組件的詳細資訊，請參閱[檢查清單： 使用 Operations Manager 2007 監視 BizTalk Server](../technical-guides/checklist-monitoring-biztalk-server-with-operations-manager-2007.md)。<br /><br /> 您也可以使用效能分析的記錄檔 (PAL) 工具來擷取從測試中的臨界值規則中使用的處理能力的臨界值[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件。 如需 PAL 工具的詳細資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)。|  
|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台|**群組中樞**頁面會顯示關鍵效能度量資訊，例如服務執行個體數目目前作用中、 已凍結，並準備好執行，排程，暫止，等中您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。|  
|商務活動監控 (BAM)|您可以在商務程序中指定特定的階段，而您想要針對這些階段來追蹤與商務應用程式有關的關鍵效能指標。 使用 BAM，您可以監控商務度量，以及 IT 度量 （例如，SLA 和執行時間）。|  
  
### <a name="threshold-monitoring"></a>閾值監視  
 自訂的臨界值規則是不可或缺的要素成熟的作業環境。 您可以在 Operations Manager 中建立許多這些閾值規則。 這些閾值規則通常會根據 BizTalk 應用程式的需求。 效能分析的記錄檔 (PAL) 工具可以簡化程序可決定您的環境的這些臨界值的正確值。 PAL 工具隨附於某些基底的臨界值可做為適用於 Microsoft System Center Operations Manager 資料的核心。 在 Operations Manager 中實作這些臨界值規則可讓您自動化的監視。 此外，系統管理員可以設定通知規則，而且可以根據執行動作的觸發臨界值規則 （例如執行指令碼，呼叫.NET 程式碼、 傳送電子郵件等）。 下表列出閾值監控工具。  
  
|工具|工作|  
|----------|----------|  
|效能的記錄分析 (PAL) 工具|效能計數器已超過臨界值時，會自動報告 PAL 工具。 臨界值動態地變更為適用於伺服器的環境。 比方說，核心記憶體集區的臨界值變更為基礎的 32 位元/64 位元架構，實體記憶體數量，以及 /3GB 參數相關的使用者提供的答案。 PAL 工具可以免費下載在[http://www.codeplex.com/PAL](http://www.codeplex.com/PAL)。|  
|Operations Manager|若要顯示的警示，如果關鍵，則可以設定 BizTalk Server 管理組件和 Operation Manager Operations 主控台[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]計數器超出定義的閾值。|  
  
## <a name="troubleshooting"></a>疑難排解  
 一旦您察覺的健全狀況問題您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式，您可以使用**群組中樞**頁面和**查詢**中的分頁[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來分析問題。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台提供整合式的組態、 部署和疑難排解體驗，以及您可以修正組態和部署相關之後指出它們的管理主控台中的問題。 一般來說，大多數的應用程式問題都是因為未得到預期的訊息 (這可以呈現為擱置的服務執行個體或重試連接埠，或是尚未重新啟動的已凍結執行個體等等)。  
  
 您可以使用**群組中樞**頁面和**查詢**頁面來群組您的服務執行個體 (不論其狀態為： 執行已擱置、 已凍結等) 由應用程式錯誤類型、 服務類型、 主控件等。，若要找出不同的錯誤，請調查一一，並加以修正。