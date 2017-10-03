---
title: "高可用性和 Microsoft Operations Framework |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- high availability, managing
- service management functions (SMFs)
- service continuity management
- jobs, scheduling
- MOF, high availability
- change management
- MOF, process model
- high availability, MOF
ms.assetid: 54d8bae3-b241-4371-b8fc-a9cbdca6b495
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ea715e92f7bfaa2f9d3baf3e82223f95328e3da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="high-availability-and-the-microsoft-operations-framework"></a>高可用性與 Microsoft Operations Framework
將 Microsoft Operations Framework (MOF) 處理序模型套用至高度可用的 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 方案之規劃與實作，可協助您確定在發行生命週期的不同階段具有適當的程序。 藉由觀察所有出現高可用性的生命週期階段，您可以讓環境中的安裝、維護和疑難排解可用性問題更為容易。  
  
 本節包含您必須考慮高可用性工作的 MOF 程序資訊。  
  
## <a name="microsoft-operations-framework-process-model"></a>Microsoft Operations Framework 程序模型  
 Microsoft Operations Framework (MOF) 提供可讓組織達成 Microsoft 產品和技術之關鍵系統的可靠性、可用性、支援性以及管理性的指導。 MOF 以下列方式提供操作指導：白皮書、作業指南、評估工具、最佳作法、案例研究、範本、支援工具以及服務。 此指導將討論與複雜、分散式和異質 IT 環境相關的人員、程序、技術和管理問題。 如需 Microsoft Operations Framework 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=31988](http://go.microsoft.com/fwlink/?LinkId=31988)。  
  
 MOF 程序模型可讓公司：  
  
-   促進整個服務方案一致的 IT 服務管理。  
  
-   建立 IT 功能、處理程序，以及程序的結構。  
  
-   代表生命週期的方法。  
  
 MOF 程序模型的中央分為四個象限的操作處理和程序，稱為服務管理功能 (SMF)。 SMF 是操作和維護 IT 環境的基礎層級最佳作法和指示引導。  
  
 下圖顯示您必須考慮高可用性的 MOF 程序。  
  
 ![MOF 程序](../core/media/tdi-highava-mof.gif "TDI_HighAva_MOF")  
  
## <a name="changing-quadrant"></a>變動象限  
 變動象限包括服務管理功能 (SMF)，此功能用以識別、檢視、核准變更，並將變更併入受管理的 IT 環境中。 這包括軟體、硬體、文件、角色和責任的變更，也包括特定的程序變更。  
  
### <a name="change-management"></a>變更管理  
 變更管理負責技術、系統、應用程式、硬體、工具、文件和程序的變更，也負責角色和責任的變更。  
  
 在變更管理程序以做為設計 BizTalk Server 實作部分期間，您可以執行以下動作：  
  
-   決定夥伴或客戶的服務等級協議，是否需要某個層級的可用性、執行時間以及載入處理能力。  
  
-   若您正從 [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] 或 [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] 升級至 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，您必須判斷現有的硬體是否符合 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 的最低硬體需求以及服務等級協議的需求。  
  
-   為您的企業需求決定 BizTalk Server 資料庫的最佳叢集組態。 執行階段程序會寫入 BizTalk 管理資料庫、MessageBox 資料庫、追蹤 Analysis Services 資料庫、BAM 分析資料庫、BAM 星狀結構描述資料庫、BAM 主要匯入資料庫以及 BAM 封存資料庫。 因此，若發生嚴重損毀，這些資料庫就顯得特別重要，而且在決定要叢集哪些資料庫時必須有較高的優先順序。 只有使用者或工具會寫入其他資料庫。 就 MessageBox 資料庫而言，您可以考慮主動/主動/主動/被動的四個伺服器叢集以便將所需的硬體減到最少。  
  
-   決定是否叢集主要密碼伺服器，或是，若在另一個「企業單一登入」伺服器上手動還原主要密碼伺服器是否符合您的實例。 此方案為可用，但不是高度可用。  
  
-   決定您在處理預期的訊息負載並提供高可用性時，需要多少的主控件和主控件執行個體。  
  
-   建立變更管理程序中所需人員的清單。 此清單將包括但不限於網域管理員、資料庫管理員、基礎結構管理員、BizTalk Server 系統管理員以及 IT 作業人員。  
  
### <a name="configuration-management"></a>組態管理  
 組態管理負責在變更管理的控制下識別、控制和追蹤所有版本的軟體、硬體、文件、處理程序、程序以及 IT 環境中所有其他元件。  
  
 在組態管理程序期間，您必須針對如何實作高度可用的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解決方案建立一個詳細的計劃。 您也必須記錄用以建立解決方案的步驟。 簡要說明這些步驟：  
  
-   網域控制站建立將用於 BizTalk Server 環境的網域群組和帳戶。  
  
-   基礎結構管理員為 BizTalk Server 資料庫建立 Windows 叢集，並為主要密碼伺服器建立 Windows 叢集。  
  
-   資料庫系統管理員為 BizTalk Server 資料庫在 Windows 叢集上安裝和設定 Microsoft SQL Server。  
  
-   BizTalk Server 系統管理員設定主要密碼伺服器叢集。  
  
-   BizTalk Server 系統管理員在處理、接收和傳送伺服器時會安裝和設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
-   BizTalk Server 系統管理員建立主控件並在適當的伺服器上安裝主控件執行個體，以提供高可用性、增加容量，或兩者。  
  
## <a name="operating-quadrant"></a>操作象限  
 操作象限包括每日監控、控制和管理服務方案所需的 SMF，以達成和維護預先決定參數中的服務層級。  
  
### <a name="job-scheduling"></a>工作排程  
 工作排程包含以最有效率的順序持續地組織工作和程序，以最大化系統輸送量和使用率以符合服務等級協定的需求。  
  
 請確定您排程計劃的停機，例如，將更新排程在訊息負載很低時 (例如，深夜)，以便將對企業可能的影響降到最低。  
  
## <a name="supporting-quadrant"></a>支援象限  
 支援象限包括識別、指派、診斷、追蹤和解決包含在服務等級協定中已核准的需求內之事件、問題和要求所需的 SMF。  
  
## <a name="optimizing-quadrant"></a>最佳化象限  
 最佳化象限包括可維護企業和 IT合作的 SMF，它的重點在於維護或改善服務層級時能降低 IT 成本。 這包括中斷和事件的檢視、成本結構檢驗、員工評估、可用性和效能分析，以及容量預測。  
  
### <a name="service-level-management"></a>服務層級管理  
 服務層級管理的目標是透過協調和監控服務層級需求的持續循環，以維護和持續改善 IT 服務的品質。 成功的服務層級管理功能將可改善服務品質，提升客戶產能，而且最好能降低提供服務的總成本。  
  
 在服務層級管理程序期間，您可以執行以下動作：  
  
-   評估目前的環境是否符合您的服務等級協定需求。  
  
-   建議新增用於處理、接收或傳送訊息的伺服器以符合需求。  
  
-   若有必要，建議為原本未減輕的失敗點建立高度可用的方案，以符合服務等級協定的可用性需求。  
  
### <a name="availability-management"></a>可用性管理  
 可用性管理只有一個目標，就是確定客戶可以在需要時使用特定的 IT 服務。  
  
 在可用性管理程序中，您可以建立發生硬體失敗時通知 IT 人員的機制，以便他們儘快修復或替換硬體，還可以建立伺服器負載大於特定閾值時通知 IT 人員的機制。  
  
### <a name="service-continuity-management"></a>服務延續性管理  
 服務延續性管理功能的目標是確保一般可用性方案失敗時，指定的 IT 服務可提供價值給客戶。  
  
 在服務延續性功能期間，您必須檢查要實作的高可用性組態，以確保發生計劃或非計劃的停機時，您可以繼續提供客戶所需的服務。 非計劃的停機像是硬體失敗或自然行為。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 高可用性實例範例](../core/sample-biztalk-server-high-availability-scenarios.md)