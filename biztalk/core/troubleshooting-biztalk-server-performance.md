---
title: "BizTalk Server 效能疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dbf21fb9-1ae1-48b5-a65a-e96839b23945
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21003c4d3565158945e91371fa760cf97692b472
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="troubleshooting-biztalk-server-performance"></a>BizTalk Server 效能疑難排解
本節所包含的一般指導方針，可用於診斷及解決與 BizTalk 傳訊引擎相關的效能問題。  
  
## <a name="estimating-document-processing-requirements"></a>估計文件處理需求  
 在生產環境中部署解決方案之前，請先進行計劃及測試，以決定傳訊引擎的效能需求。 這有助於正確地建置 BizTalk Server 和 SQL Server 的環境。  
  
1.  計劃與任何容錯或備份及復原需求相關的額外負荷。  
  
    -   SQL Server 磁碟會設定為 RAID 陣列嗎？  
  
    -   會對 BizTalk 主控件、SQL Server 或企業單一登入套用 Windows 叢集嗎？ 如需詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。  
  
    -   會使用網路負載平衡嗎？  
  
    -   環境的備份及復原需求為何？ 如需詳細資訊，請參閱[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)。  
  
2.  請依照下列中的指導方針[規劃維持效能](../core/planning-for-sustained-performance.md)計劃、 測試及調整您的 BizTalk Server 和 SQL Server 環境。  
  
3.  請依照下列中的指導方針[追蹤效能特性](../core/tracking-performance-characteristics.md)計劃與文件追蹤需求相關的額外負荷。  
  
## <a name="optimizing-an-existing-biztalk-server-environment"></a>最佳化現有的 BizTalk Server 環境  
 請遵循以下步驟來最佳化現有的 BizTalk Server 環境：  
  
1.  請依照下列中的指導方針[識別效能瓶頸](../core/identifying-performance-bottlenecks.md)能找出可能的瓶頸，BizTalk Server 環境中。  
  
2.  請依照下列中的指導方針[最佳化資源使用量透過主控件節流](../core/optimizing-resource-usage-through-host-throttling.md)至 BizTalk Server 環境的文件輸送量最大化。  
  
3.  請考慮修改參數記載於[組態參數會影響配接器效能](../core/configuration-parameters-that-affect-adapter-performance.md)將配接器在某些情況下的效能最大化。  
  
4.  請依照下列中的指導方針[如何 BizTalk Server 處理大型訊息](../core/how-biztalk-server-processes-large-messages.md)時處理大型訊息 (超過 100 MB) 最佳化傳訊引擎的效能。  
  
5.  針對傳送配接器、接收配接器和協調流程，建立個別的主控件和主控件執行個體。 這樣可為每個配接器提供個別的主控件執行個體以在其中執行，並可確保配接器不會對其他的配接器造成不利的影響。 由於主控件節流設定是設定於主控件層級，所以將處理邏輯區分到不同主控件的做法，也可讓您根據每個主控件的處理需求來設定節流。  
  
## <a name="diagnosing-performance-problems-in-an-existing-biztalk-server-environment"></a>在現有 BizTalk Server 環境中診斷效能問題  
 一般而言，效能問題可以縮小至下列其中一個 BizTalk Server 環境元件：  
  
-   接收配接器，或是配接器從其接收文件的系統。 例如，如果文件是由 HTTP 配接器以低於最佳速率的方式所接收，則問題可能出在 HTTP 接收配接器，或是張貼到 HTTP 配接器的用戶端。  
  
-   協調流程服務執行個體。  
  
-   裝載 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫之 Microsoft SQL Server 的效能。  
  
-   傳送配接器，或是配接器將文件傳送至的系統。 例如，如果文件是由 SQL 配接器以低於最佳速率的方式所傳送，則問題可能出在 SQL 傳送配接器，或是執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 而 SQL 配接器正在更新的電腦。  
  
 請使用下列指導方針，以協助辨識效能不佳的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境元件：  
  
-   請擷取在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 事件檢視器中產生的警告或錯誤訊息。  
  
-   請依照[識別效能瓶頸](../core/identifying-performance-bottlenecks.md)，找出效能瓶頸。  
  
 一旦辨識出效能不佳的元件後，請遵循正確的指導方針來協助解決問題：  
  
 **解決與傳送和接收配接器相關的效能問題的指導方針**  
  
-   請參閱[疑難排解 BizTalk Server 配接器](../core/troubleshooting-biztalk-server-adapters.md)以疑難排解問題的一般資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。 本節包含一般的疑難排解資訊，其中包含以下項目的相關資訊：如何設定特定配接器的記錄、可用來診斷網路問題的資訊、MSDTC 問題、登錄問題、檔案系統問題以及 IIS 問題等。  
  
-   請參閱適當的[疑難排解 BizTalk Server 相依性](../core/troubleshooting-biztalk-server-dependencies.md)如需如何疑難排解 MSDTC、 憑證、 企業單一登入，一般資訊和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
 **解決與協調流程相關的效能問題的指導方針**  
  
-   修改 BTSNTSvc.exe.config 檔案中所述之適當章節[協調流程引擎組態](../core/orchestration-engine-configuration.md)。  
  
 **解決 SQL Server 相關的效能問題的指導方針**  
  
-   SQL Server Profiler 可以用來擷取傳送至 SQL Server 的 Transact-SQL 陳述式，以及這些陳述式的 SQL Server 結果集。 由於 BizTalk Server 已緊密地與 SQL Server 整合，因此 SQL Server Profiler 追蹤的分析是相當有用的工具，可用於分析讀取和寫入 SQL Server 資料庫時 BizTalk Server 中可能發生的問題。 如需有關如何使用 SQL Server Profiler 的詳細資訊，請參閱 SQL Server 說明文件。  
  
-   SQL Server 查詢編輯器可以用來執行 SQL 陳述式直接對 SQL Server 資料庫。 在某些情況中，這個功能可能有助於查詢 BizTalk Server 資料庫或更新 BizTalk Server 資料庫。 如需查詢編輯器的詳細資訊，請參閱 SQL Server 文件。  
  
-   檢閱[疑難排解 SQL Server](../core/troubleshooting-sql-server.md)如需詳細資訊。  
  
## <a name="see-also"></a>請參閱  
 [疑難排解](../core/troubleshooting.md)