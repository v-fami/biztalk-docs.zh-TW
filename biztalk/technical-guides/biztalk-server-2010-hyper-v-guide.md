---
title: BizTalk Server 2010 HYPER-V 指南 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c38ecdd-de72-41d9-b639-2aa6bbfee917
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f07cd5f5406475fad3cfc3b9c1d234c5d93cf1eb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975087"
---
# <a name="biztalk-server-2010-hyper-v-guide"></a>BizTalk Server 2010 HYPER-V 指南
本指南的目的是要提供實務指導方針使用 Microsoft BizTalk Server 與 Microsoft [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] HYPER-V。 重點在於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，但效能評估方式和效能測試案例很適用於一般分析的虛擬化的伺服器應用程式的效能。 本指南會感興趣的 IT 專業人員和開發人員社群。  

 若要下載一份本指南，請前往[ http://go.microsoft.com/fwlink/?LinkId=149267 ](http://go.microsoft.com/fwlink/?LinkId=149267)。  

## <a name="introduction"></a>簡介  
 伺服器虛擬化提供的公司，得以在單一實體機器上執行多個作業系統。 這可讓伺服器彚總未充分利用較少的充分利用的機器。 藉由實作虛擬化，公司可以最小化操作，並與部署和操作所需的企業應用程式伺服器相關聯的資本支出的成本。  

 可能的成本節省系統會提示 IT 部門評估新的和現有的應用程式，來識別適合伺服器虛擬化候選項目。 大部分上述評估搜尋來探索虛擬化的總成本。 總成本的虛擬化是硬體和 IT 作業的金錢成本和相較於效能如今在實際環境中的虛擬化的效能成本的總和。 本指南僅著重於虛擬化的效能層面。  

 從 Windows Server 2008 開始，使用 HYPER-V 技術的伺服器虛擬化已經過作業系統不可或缺的一部分。 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] HYPER-V 提供可靠且經過最佳化的虛擬化解決方案，讓組織得以提高伺服器使用率並降低成本。 加上新的功能，例如即時移轉功能、 擴充的處理器和記憶體的主機系統，支援動態虛擬機器存放裝置，支援的方法，它可以讓組織得以將合併到單一的實體伺服器上的工作負載，而且是要合併以及與開發和測試環境的伺服器對組織很好的解決方案。  

 BizTalk Server 會充分利用最新的虛擬化改進的一部分[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]HYPER-V，它可能會導致降低透過實際執行伺服器整併和商務持續性管理，再加上更多動態建立的成本IT 基礎結構。 [叢集] 功能可讓 BizTalk Server 部署在多站叢集環境中，而不需要其他軟體或硬體。 HYPER-V 提供的虛擬化執行個體上執行數個 BizTalk Server 執行個體支援[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 伺服器虛擬化可讓 BizTalk 客戶藉由合併未使用的資源，以安全的方式將 BizTalk 部署的硬體使用量降到最低。  

 BizTalk Server 部署通常包含數個其他元件包括： SQL Server、 Windows Server 和 Internet Information Services (IIS)。 HYPER-V 提供動態佈建透過 System Center Virtual Machine Manager (VMM) 可佈建隨選實際案例的支援。  

 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 提供 HYPER-V 技術，以容納透過多個作業系統執行個體的單一實體伺服器上的虛擬化伺服器彙總。 HYPER-V 依現狀的核心部分[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]或當做獨立產品，讓客戶利用組織中的虛擬化，盡量簡化。 有數個重要的案例實作 Hyper-v:  

- **伺服器彙總**– 最小化伺服器使用量、 操作及彙總到一個方塊上的多個實體伺服器來執行應用程式相關聯的資本支出 (TCO)。  

- **測試和開發**– 使用虛擬機器，開發人員和架構設計人員可以快速佈建新的機器，若要試用新的技術及案例在安全的環境，以精確地反映實體環境的特性。 虛擬化可讓佈建的新機器的作業系統在各種平台上執行而不需要新硬體。 這對於測試和開發環境提供絕佳的平台。  

- **Business Continuity and Disaster Recovery** – HYPER-V 包含功能強大的商務持續性和災害復原功能，例如即時的備份和快速移轉可讓企業以符合其服務等級協定。  

  > [!NOTE]  
  >  如需如何備份 HYPER-V 虛擬機器使用 Windows Server Backup，請參閱 Microsoft 知識庫文章 958662，「 如何備份 HYPER-V 虛擬機器從父磁碟分割與 Windows Server 2008 為基礎的電腦上使用 Windows在伺服器備份 」 [ http://go.microsoft.com/fwlink/?LinkId=131207 ](http://go.microsoft.com/fwlink/?LinkId=131207)。  
  >   
  >  如何使用 HYPER-V 即時移轉功能，Windows Server 2008 R2 中的資訊，請參閱 「 Hyper-v： 逐步指南來使用即時移轉在 Windows Server 2008 R2"，網址[ http://go.microsoft.com/fwlink/?LinkID=139667 ](http://go.microsoft.com/fwlink/?LinkID=139667)。  

- **動態資料中心**– 您可以結合 HYPER-V 與 Microsoft System Center 套件的工具，組織可讓您自動化虛擬機器設定和監視。 詳細資訊，請參閱"System Center Virtual Machine Manager 」，網址[ http://go.microsoft.com/fwlink/?LinkID=111303 ](http://go.microsoft.com/fwlink/?LinkID=111303)。  

  本指南中的資訊與直接相關的伺服器彙總及測試與開發案例的 HYPER-V。 其他兩個已超出本指南的討論範圍。  

  HYPER-V 的核心案例的相關資訊，請參閱[虛擬化與 Hyper-v： 概觀](http://go.microsoft.com/fwlink/?LinkID=202438)中的主題[Appendices1](../technical-guides/appendices1.md)一節。  

### <a name="who-should-read-this"></a>誰應該閱讀這？  

- 所有 IT 專業人員使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  

- IT 專業人員部署、 最佳化及維護應用程式環境  

- IT 專業人員與開發團隊，來評估並最佳化系統架構  

- 開發人員建立和維護[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式  

- 開發人員想要讓效能最佳化以及找出效能瓶頸  

### <a name="goals-of-this-guide"></a>本指南的目標  
 本指南的主要目標是提供有關如何判斷是否應該可以滿足效能期望在 HYPER-V 上執行的 BizTalk Server 的指引。 本指南也會屬於值的已部署的最佳化是協助[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。  

 這個專案進行下列目標：  

- 提供特定指引，任何人都是評估、 設計，或實作虛擬化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  

- 提供的效能監視器計數器和用來測量虛擬化的伺服器平台的效能功能的工具的簡介。  

- 提供的指導方針來判斷虛擬化的成本做為實體和虛擬化伺服器環境的效能差異。  

- 開發用於，當您規劃或最佳化虛擬化的最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  

- 提供架構指引，協助您判斷如何部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]虛擬化環境中。  

- 識別，並記錄在虛擬環境的效能瓶頸。  

### <a name="whats-in-this-guide"></a>什麼是本指南中？  
 實作指導方針[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上的 HYPER-V 虛擬化環境的解決方案。 本指南包含：  

- **部署在 HYPER-V 上的 BizTalk Server**:[部署在 HYPER-V 上的 BizTalk Server](../technical-guides/deploying-biztalk-server-on-hyper-v.md)描述設定實驗室環境，用來比較效能已遵循的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上執行的解決方案HYPER-V 虛擬機器的相同[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實體硬體上執行的解決方案。  

- **評估 HYPER-V 上的 BizTalk Server 效能**:[在 HYPER-V 上評估 BizTalk Server 效能](../technical-guides/evaluating-biztalk-server-performance-on-hyper-v.md)測量的效能時，詳細說明重要的考量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 上執行的解決方案虛擬化的環境。  

- **測試 HYPER-V 上的 BizTalk Server 效能**:[測試 BizTalk 伺服器虛擬化效能](../technical-guides/testing-biztalk-server-virtualization-performance.md)提供的四個不同的測試案例的效能做比較的詳細的結果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器上執行相同的方案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實體硬體上執行的解決方案。  

- **附錄**： 中的主題[Appendices1](../technical-guides/appendices1.md)提供重要的參考資料，包括在本指南：  

  -   [附錄 a： 最佳化套用至測試環境中的電腦](../technical-guides/appendix-a-optimizations-applied-to-computers-in-test-environment.md)– 提供已套用至測試環境中電腦的效能最佳化的詳細的資訊。  

  -   [附錄 b: HYPER-V 架構和功能概觀](../technical-guides/appendix-b-hyper-v-architecture-and-feature-overview.md)-提供 HYPER-V 架構的概觀，說明優點和缺點的 HYPER-V，並說明 HYPER-V 和 Virtual Server 2005 之間的差異  

  -   [附錄 c: BizTalk Server 和 SQL Server HYPER-V 可支援性](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md)– 描述 HYPER-V 虛擬機器上執行 BizTalk Server 和 SQL Server 的支援原則。  

  -   [附錄 d： 工具測量效能](../technical-guides/appendix-d-tools-for-measuring-performance.md)-描述數個工具，可用來監視和評估 BizTalk Server 環境的效能。  

- **字彙**: [Glossary8](../technical-guides/glossary8.md)定義本指南所使用的重要詞彙。
