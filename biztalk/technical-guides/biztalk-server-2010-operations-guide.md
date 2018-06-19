---
title: BizTalk Server 2010 操作指南 |Microsoft 文件
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4dc0d8e9-9ad6-4ce1-8ca7-399b67cb360e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5078cdc0a4b2d28e81daf2247cb0f1f35b3d6288
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010383"
---
# <a name="biztalk-server-2010-operations-guide"></a>BizTalk Server 2010 操作指南
歡迎使用 Microsoft® BizTalk® Server 2010 操作指南。 我們建立了本指南是很寶貴的資源所涉及的實作和管理 BizTalk 方案，特別是 IT 專業人員的任何人。  
  
 若要下載這份指南的 chm、 pdf 或 docx 表單中，移至[Microsoft BizTalk Server 2010 操作指南](http://go.microsoft.com/fwlink/?LinkId=212652)(http://go.microsoft.com/fwlink/?LinkId=212652)。  
  
## <a name="which-versions-of-biztalk-server-does-the-guide-cover"></a>本指南涵蓋的 BizTalk Server 版本？  
 本指南皆代表 BizTalk Server，並提供操作整備狀態資訊可協助您開始使用與您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝程式。  
  
> [!NOTE]
>  若要查看操作指南 》[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]或[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]，請參閱[http://go.microsoft.com/fwlink/?LinkID=130458](http://go.microsoft.com/fwlink/?LinkID=130458)。  
  
## <a name="where-do-i-start"></a>要從何處著手？  
 本指南根據規劃、 部署和管理的功能層面，我們組織[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。 因此您可以讀取它，根據這些功能的層面。 不過，實現，檢查清單會最大 BizTalk Server 作業指南中的資訊之後，我們就已經分類以方便存取範圍的下表中的文件中的所有檢查清單。  
  
|||  
|-|-|  
|**設定 BizTalk 環境**|**設定高可用性和嚴重損壞修復環境**|  
|-   [檢查清單： 開始使用 BizTalk Server](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)<br />-   [檢查清單： 設定 Windows Server](~/technical-guides/checklist-configuring-windows-server.md)<br />-   [檢查清單： 設定 Internet Information Services](~/technical-guides/checklist-configuring-internet-information-services.md)<br />-   [檢查清單： 設定 SQL Server](../technical-guides/checklist-configuring-sql-server.md)<br />-   [檢查清單： 設定 BizTalk Server](~/technical-guides/checklist-configuring-biztalk-server.md)|-   [檢查清單： 提供高可用性與容錯或負載平衡](~/technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)<br />-   [檢查清單： 提高可用性與災害復原](~/technical-guides/checklist-increasing-availability-with-disaster-recovery.md)|  
|**監視、 測試和疑難排解**|**效能及維護**|  
|-   [檢查清單： 監視操作整備](~/technical-guides/checklist-monitoring-operational-readiness.md)<br />-   [檢查清單： 維護和疑難排解 BizTalk Server 資料庫](../technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)<br />-   [檢查清單： 測試操作整備](~/technical-guides/checklist-testing-operational-readiness.md)<br />-   [檢查清單： 監控 BizTalk Server 與 Operations Manager 2007](~/technical-guides/checklist-monitoring-biztalk-server-with-operations-manager-2007.md)<br />-   [檢查清單： 監視 SQL Server](~/technical-guides/checklist-monitoring-sql-servers.md)|維護相關的檢查清單：<br /><br /> -   [檢查清單： 執行每日維護檢查](~/technical-guides/checklist-performing-daily-maintenance-checks.md)<br />-   [檢查清單： 執行每週維護檢查](~/technical-guides/checklist-performing-weekly-maintenance-checks.md)<br />-   [檢查清單： 執行每月維護檢查](~/technical-guides/checklist-performing-monthly-maintenance-checks.md)<br /><br /> 效能相關的檢查清單：<br /><br /> -   [檢查清單： 執行每週效能檢查](~/technical-guides/checklist-performing-weekly-performance-checks.md)<br />-   [檢查清單： 執行每月效能檢查](~/technical-guides/checklist-performing-monthly-performance-checks.md)|  
|**其他重要工作的檢查清單**||  
|-   [檢查清單： 部署應用程式](~/technical-guides/checklist-deploying-an-application.md)<br />-   [檢查清單： 從另一個應用程式匯出繫結](~/technical-guides/checklist-exporting-bindings-from-one-application-to-another.md)<br />-   [檢查清單： 更新組件](~/technical-guides/checklist-updating-an-assembly.md)<br />-   [檢查清單： 更新 BizTalk 應用程式中的成品](~/technical-guides/checklist-updating-artifacts-in-a-biztalk-application.md)|-   [檢查清單： 更新應用程式使用的並存版本控制](~/technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md)<br />-   [檢查清單： 更新協調流程中使用的並存版本控制](~/technical-guides/checklist-updating-an-orchestration-using-side-by-side-versioning.md)<br />-   [檢查清單： 安裝及設定憑證](../technical-guides/checklist-installing-and-configuring-certificates.md)<br />-   [作業的安全環境中規劃檢查清單：](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md)|  
  
 如果您正在執行下列工作，您可以啟動相關的章節：  
  
-   **評估作業整備**： 如果您將焦點放在評估與評估操作整備的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署，然後開始閱讀[作業的檢查清單](~/technical-guides/operations-checklists.md)和[增加可用性，以便讓 BizTalk Server](~/technical-guides/increasing-availability-for-biztalk-server.md)區段。  
  
-   **操作進行**： 為了確保您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]基礎結構和應用程式就緒操作，請參閱[規劃 BizTalk Server 環境](~/technical-guides/planning-the-environment-for-biztalk-server.md)> 一節。  
  
-   **維護操作環境**： 大部分的操作指南中的主題可協助您維護運作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 您會發現最佳作法、 重要的概念和程序來維護下列各節中的操作環境：[增加可用性，以便讓 BizTalk Server](~/technical-guides/increasing-availability-for-biztalk-server.md)，[監控 BizTalk Server](~/technical-guides/monitoring-biztalk-server2.md)，和[維護 BizTalk Server2](~/technical-guides/maintaining-biztalk-server2.md)。  
  
## <a name="whats-in-it"></a>什麼是在它？  
 根據真實世界體驗的指引。 竟是來自 Microsoft 欄位代表、 夥伴組織的客戶和計劃，本指南的作法部署和維護 BizTalk Server 安裝。 此群組的 IT 專業人員已經累積豐富的實際操作經驗與不同 BizTalk 解決方案。 因為他們獲得的經驗建立這些檢查清單、 最佳做法及簡報引導未來[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業。 我們需要收集及組織這項資訊來建立指南。  
  
 本指南的主要部分是新的;不過，相當大的部分是指[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]說明、 白皮書、 知識庫文章，以及其他來源。 它已經仔細檢閱並驗證來自社群的專家[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]IT 專業人員和產品開發團隊，對我們非常感謝了解本主題結尾的成員。 我們認為這裡所呈現的資訊將協助[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用者解決問題，和，避免許多常見部署和維護時可能發生的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。  
  
## <a name="acknowledgments"></a>致謝  
 我們在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用者教育小組非常感謝提供意見反應技術以及大量的內容確認下列人員的未處理的比重[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]操作指南：  
  
-   Paolo Salvatori、 Tim Wieman