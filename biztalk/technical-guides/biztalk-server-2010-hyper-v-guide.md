---
title: "BizTalk Server 2010 HYPER-V 指南 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c38ecdd-de72-41d9-b639-2aa6bbfee917
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0e76fee8ce74f11ec0f1a14334447114f3c4ed0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-2010-hyper-v-guide"></a>BizTalk Server 2010 HYPER-V 指南
本指南的目的是要提供使用 Microsoft 的實用指南[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]與 Microsoft [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] HYPER-V。 重點在於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，但適用於分析的虛擬化的伺服器應用程式效能的一般效能評估方法和測試案例的效能。 本指南會感興趣的 IT 專業人員和開發人員社群。  
  
 若要下載此指南的副本，請移至[http://go.microsoft.com/fwlink/?LinkId=149267](http://go.microsoft.com/fwlink/?LinkId=149267)。  
  
## <a name="introduction"></a>簡介  
 伺服器虛擬化提供的公司有機會在單一實體機器上執行多個作業系統。 這可讓伺服器彚總使用量過低充分利用的電腦數目較少。 藉由實作虛擬化，公司可以降低操作資本費用成本與部署和操作所需的企業應用程式伺服器。  
  
 成本節約有提示您 IT 部門來評估新的和現有的應用程式，來識別適用於伺服器虛擬化候選項目。 若要探索的總成本的虛擬化搜尋最這類的評估。 虛擬化的總成本是貨幣成本的硬體和 IT 操作與虛擬化，相較於未偏離正軌中的實體環境效能的效能成本的總和。 本指南主要著重於虛擬化的效能層面。  
  
 從 Windows Server 2008 開始，使用 HYPER-V 技術的伺服器虛擬化已經作業系統不可或缺的一部分。 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]HYPER-V 提供可靠且最佳化的虛擬化解決方案，可讓組織得以改善伺服器使用率及降低成本。 加上的新功能，例如即時移轉功能、 擴充的處理器和記憶體支援的主機系統，支援動態虛擬機器存放裝置，它能讓組織將合併到單一實體伺服器上的工作負載，而且要合併的伺服器以及開發和測試環境與組織的合適解決方案。  
  
 BizTalk Server 會利用包含最新的虛擬化改善[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]HYPER-V，它可能會導致已將成本減少實際執行伺服器的調節和業務持續性管理，再加上的多個動態建立透過IT 基礎結構。 叢集功能可讓您在沒有其他軟體或硬體的多站叢集環境中部署的 BizTalk Server。 HYPER-V 提供的虛擬化的執行個體上執行數個 BizTalk Server 執行個體的支援[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 伺服器虛擬化可讓 BizTalk 客戶使用量降到最低的硬體 BizTalk 部署的安全的方式合併未使用的資源。  
  
 BizTalk Server 部署通常包含數量的其他元件包括： SQL Server、 Windows Server 和網際網路資訊服務 (IIS)。 HYPER-V 提供支援動態佈建透過 System Center Virtual Machine Manager (VMM) 可佈建視實際的案例。  
  
 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]提供以配合伺服器彙總到單一實體伺服器到多個作業系統執行個體的虛擬化的 HYPER-V 技術。 HYPER-V 提供的核心一部分[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]或請儘可能運用其組織中的虛擬化的客戶輕鬆的獨立產品。 有數個重要案例，實作 Hyper-v:  
  
-   **伺服器彙總**– 最小化操作的伺服器使用量，並藉由將合併到一個方塊的多部實體伺服器中執行應用程式相關聯的資本支出 (TCO)。  
  
-   **測試和開發**– 使用虛擬機器，開發人員和架構設計人員可以快速地佈建新機器試用新的技術和精確地反映之特性的實體環境的安全環境中的案例。 虛擬化可以讓使用者佈建的新機器寬的平台的作業系統上執行而不需要新硬體。 這提供了絕佳的平台測試和開發環境。  
  
-   **業務續航力和災害復原**– HYPER-V 包含功能強大的業務續航力和災害復原功能，例如即時的備份和快速移轉，而這讓企業能夠滿足其服務等級協定。  
  
    > [!NOTE]  
    >  如需如何備份使用 Windows Server Backup 的 HYPER-V 虛擬機器，請參閱 Microsoft 知識庫文章 958662，< 如何備份 HYPER-V 虛擬機器從父分割區的 Windows Server 2008 電腦上使用 Windows伺服器備份 」 在[http://go.microsoft.com/fwlink/?LinkId=131207](http://go.microsoft.com/fwlink/?LinkId=131207)。  
    >   
    >  如何使用 HYPER-V 即時移轉功能，Windows Server 2008 R2 中的資訊，請參閱 「 Hyper-v： 逐步指南來使用即時移轉在 Windows Server 2008 R2 」，網址[http://go.microsoft.com/fwlink/?LinkID=139667](http://go.microsoft.com/fwlink/?LinkID=139667)。  
  
-   **動態資料中心**– 藉由結合 HYPER-V 與 Microsoft System Center 套件的工具，組織可以自動化的虛擬機器設定和監視。 如需詳細資訊，請參閱 「 System Center Virtual Machine Manager 」 在[http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303)。  
  
 本指南中的資訊直接關係到伺服器彙總並測試和開發案例的 HYPER-V。 其他兩個已超出本指南的範圍。  
  
 Hyper-v 的核心案例的相關資訊，請參閱[虛擬化搭配 Hyper-v： 概觀](http://go.microsoft.com/fwlink/?LinkID=202438)和中的主題[Appendices1](../technical-guides/appendices1.md)一節。  
  
### <a name="who-should-read-this"></a>誰應該閱讀這？  
  
-   所有 IT 專業人員使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   IT 專業人員部署、 最佳化及維護的應用程式環境  
  
-   IT 專業人員使用開發團隊評估並最佳化系統架構  
  
-   開發人員建立和維護[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式  
  
-   開發人員想要最佳化效能，並識別效能瓶頸的  
  
### <a name="goals-of-this-guide"></a>本指南的目標  
 本指南的主要目標是提供有關如何判斷指引[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]HYPER-V 上執行很符合效能期望。 本指南也會的值來最佳化的已部署的協助[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。  
  
 這個專案進行下列目標：  
  
-   提供特定指導方針的任何人都評估、 設計，或實作虛擬化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
-   提供的效能監視器計數器和工具可用來測量的虛擬化的伺服器平台的效能功能的簡介。  
  
-   提供的指導方針決定成本的虛擬化成實體和虛擬化伺服器環境之間的效能差異的函數。  
  
-   開發計劃或最佳化虛擬化時使用的最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
-   提供可協助您判斷如何部署的架構指引[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]虛擬化環境中。  
  
-   識別和文件中的虛擬化環境的效能瓶頸。  
  
### <a name="whats-in-this-guide"></a>什麼是本指南中？  
 實作指導方針[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 HYPER-V 虛擬化環境中的方案。 本指南包含：  
  
-   **部署在 HYPER-V 上的 BizTalk Server**:[部署在 HYPER-V 上的 BizTalk Server](../technical-guides/deploying-biztalk-server-on-hyper-v.md)描述來設定用來比較效能的實驗室環境遵循的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案上執行HYPER-V 虛擬機器到相同[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在實體硬體上執行的方案。  
  
-   **評估在 HYPER-V 上的 BizTalk Server 效能**: [HYPER-V 上評估 BizTalk Server 效能](../technical-guides/evaluating-biztalk-server-performance-on-hyper-v.md)測量的效能時，詳細資料的重要考量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 上執行的方案虛擬化的環境。  
  
-   **測試在 HYPER-V 上的 BizTalk Server 效能**:[測試 BizTalk 伺服器虛擬化效能](../technical-guides/testing-biztalk-server-virtualization-performance.md)提供四個不同的測試案例相比較的效能的詳細的結果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器上執行相同的方案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在實體硬體上執行的方案。  
  
-   **附錄**： 中的主題[Appendices1](../technical-guides/appendices1.md)提供重要的參考資料，包括此指南：  
  
    -   [附錄 a： 最佳化套用至測試環境中的電腦](../technical-guides/appendix-a-optimizations-applied-to-computers-in-test-environment.md)– 提供已套用至測試環境中電腦的效能最佳化的詳細的資訊。  
  
    -   [附錄 b: HYPER-V 架構和功能概觀](../technical-guides/appendix-b-hyper-v-architecture-and-feature-overview.md)-提供 HYPER-V 架構的概觀，描述有哪些優缺點的 HYPER-V，以及說明 HYPER-V 與 Virtual Server 2005 之間的差異  
  
    -   [附錄 c: BizTalk Server 和 SQL Server 為 HYPER-V 可支援性](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md)– 描述 HYPER-V 虛擬機器上執行 BizTalk Server 和 SQL Server 支援原則。  
  
    -   [附錄 d： 工具以測量效能](../technical-guides/appendix-d-tools-for-measuring-performance.md)-描述數個工具，可用來監視和評估 BizTalk Server 環境的效能。  
  
-   **詞彙**: [Glossary8](../technical-guides/glossary8.md)本指南所使用的主要詞彙的定義。