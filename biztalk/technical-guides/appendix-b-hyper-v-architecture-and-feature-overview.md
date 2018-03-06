---
title: "附錄 b： 使用 HYPER-V 的架構和功能概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87b6b9a0-a470-43f7-b076-36075477cc34
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 613c0a28d9aaf3f8a07b34b65345979d69223668
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="appendix-b-hyper-v-architecture-and-feature-overview"></a>附錄 b： 使用 HYPER-V 的架構和功能概觀
本主題提供 HYPER-V 架構的概觀，說明優點和缺點的 HYPER-V。  
  
## <a name="hyper-v-architecture"></a>HYPER-V 架構  
  
 HYPER-V 是以 hypervisor 為基礎的虛擬化平台和技術的其中一項 Windows Server 跑馬燈功能、 即時移轉。 HYPER-V 與 Windows Server 是能夠快速移轉，可能只有幾秒鐘的停機時間與實體主機之間移動 Vm。 即時移轉與目標實體之間移動，就可能發生毫秒，這表示看不到已連線的使用者變得移轉作業中。 請參閱[的 Windows Server 上的 HYPER-V 新功能](https://docs.microsoft.com/windows-server/virtualization/hyper-v/what-s-new-in-hyper-v-on-windows)。
  
 Hypervisor 是可以裝載多個虛擬機器 (Vm) 與彼此隔離，但透過虛擬化的處理器、 記憶體和 I/O 裝置共用的基礎硬體資源的特定處理器的虛擬化平台。  
  
 HYPER-V 虛擬機器中執行的客體作業系統提供效能接近在實體硬體上執行的作業系統效能*如果*必要的虛擬伺服器用戶端 (VSC) 驅動程式和服務會安裝在客體作業系統上。 HYPER-V 虛擬伺服器用戶端 (VSC) 程式碼，也稱為 HYPER-V I/O 的應用、 可讓您直接存取 HYPER-V 」 虛擬機器匯流排 」 和適用於安裝 HYPER-V 整合服務。 提供 VSC 驅動程式的 HYPER-V 整合服務也可供其他用戶端作業系統。  
  
 HYPER-V 支援的資料分割方面的隔離。 資料分割是隔離的支援的 hypervisor，作業系統執行所在的邏輯單元。 Microsoft hypervisor 必須至少一個父系或根磁碟分割，執行 Windows Server。 虛擬化堆疊會在父分割區且可直接存取硬體裝置。 根磁碟分割然後建立子主控客體作業系統的磁碟分割。 根磁碟分割會建立使用 hypercall 應用程式開發介面 (API) 的子磁碟分割。  
  
 資料分割不需要存取實體的處理器，也不要處理處理器插斷。 相反地，他們擁有的虛擬處理器檢視和執行每個客體資料分割的私人虛擬記憶體位址區域中。 Hypervisor 會處理插斷處理器，並重新導向至個別資料分割。 HYPER-V 也可以硬體加速各種客體的虛擬位址空間使用輸入輸出記憶體管理單位 （iommu 所致） 的運作獨立 CPU 所使用的記憶體管理硬體之間的位址轉譯。 IOMMU 用來重新對應至位址的子資料分割所使用的實體記憶體位址。  
  
 子資料分割也沒有其他硬體資源的直接存取，並會顯示為虛擬裝置 (VDevs) 的虛擬檢視的資源。 透過 VMBus 或父分割區，用來處理要求中的裝置以 hypervisor 的虛擬裝置的要求重新導向。 VMBus 是邏輯資料分割間的通訊通道。 父分割區裝載虛擬化服務提供者 (VSPs) 來處理從子分割的裝置存取要求 VMBus 透過通訊。 子分割裝載虛擬化服務取用者 (VSCs) 的裝置將要求重新導向 VSPs 透過 VMBus 父分割區中。 這整個程序會感覺到客體作業系統。  
  
 虛擬裝置也可以利用 Windows 伺服器虛擬化功能，稱為啟發 I/O，儲存體、 網路功能、 圖形及輸入的子系統。 啟發的 I/O 是利用 VMBus 直接，略過任何裝置的模擬層的高層級的通訊協定 （例如 SCSI) 的特製化感知虛擬化的實作。 這樣可以更有效率的通訊，但是需要是 hypervisor，並注意 VMBus 啟用的客體。 HYPER-V 架構 I/O 和 hypervisor 知道的核心提供透過 HYPER-V 整合服務的安裝。 整合元件，包括虛擬伺服器用戶端 (VSC) 驅動程式，也可供其他用戶端作業系統。 HYPER-V 需要包含硬體輔助虛擬化，例如處理器隨附 Intel VT 或 AMD 虛擬化 (AMD-V) 技術。  
  
 下圖提供 Windows Server 上執行的 HYPER-V 環境的架構的高階概觀。  
  
 ![Hyper-v &#45;HYPER-V 架構概觀](../technical-guides/media/eadd2a84-3936-4b48-a0e2-05b94882d848.gif "eadd2a84-3936-4b48-a0e2-05b94882d848")  

  
 縮略字和使用在上圖中的詞彙描述如下：  
  
-   **APIC** – 進階可程式化插斷控制器。 會輸出可讓優先權等級指派給它的插斷的裝置。  
  
-   **子分割**– 裝載為客體作業系統的磁碟分割。 透過虛擬機器匯流排 (VMBus) 或 hypervisor 提供所有的存取權的實體記憶體並由子分割的裝置。  
  
-   **Hypercall** – 以便與 hypervisor 進行通訊的介面。 Hypercall 介面可容納由 hypervisor 所提供的最佳化作業的存取。  
  
-   **Hypervisor** – 位於之間的硬體和一或多個作業系統的軟體層。 其主要工作是要提供隔離的執行環境稱為 「 磁碟分割。 Hypervisor 可控制和 arbitrates 基礎硬體的存取權。  
  
-   **IC** – 整合元件。 允許子資料分割與其他資料分割和 hypervisor 通訊的元件。  
  
-   **I/O 堆疊**– 輸入/輸出堆疊。  
  
-   **MSR** – 記憶體服務例行工作。  
  
-   **根磁碟分割**– 管理電腦層級功能，例如裝置驅動程式、 電源管理，以及裝置熱新增/移除。 根 （或父系） 磁碟分割是可直接存取實體記憶體和裝置的唯一資料分割。  
  
-   **VID** – 虛擬化基礎結構驅動程式。 提供資料分割管理服務、 虛擬處理器管理服務和分割區的記憶體管理服務。  
  
-   **VMBus** – 間的分割區在多個作用中的虛擬化資料分割的系統上的通訊和裝置列舉所用的通道為基礎的通訊機制。 VMBus 安裝 HYPER-V 整合服務。  
  
-   **VMMS** – 虛擬機器管理服務。 負責管理子資料分割中的所有虛擬機器的狀態。  
  
-   **VMWP** – 虛擬機器背景工作處理序。 使用者模式虛擬化堆疊的元件。 工作者處理序提供從 Windows Server 中的執行個體的父分割至子資料分割中的客體作業系統的虛擬機器管理服務。 虛擬機器管理服務會產生不同的背景工作處理序的每個執行中虛擬機器。  
  
-   **VSC** – 虛擬化服務用戶端。 綜合裝置執行個體所在的子資料分割。 VSCs 利用虛擬化服務提供者 (VSPs) 所提供的父分割中的硬體資源。 透過與通訊父分割區中對應的 VSPs VMBus 滿足子分割的裝置 I/O 要求。  
  
-   **VSP** – 虛擬化服務提供者。 位於根磁碟分割，並且透過虛擬機器匯流排 (VMBus) 提供子分割的綜合裝置支援。  
  
-   **WinHv** – Windows Hypervisor 介面程式庫。 WinHv 是基本上之間分割的作業系統的驅動程式和可呼叫使用標準 Windows 呼叫慣例在 hypervisor 中的驅動程式 hypervisor 橋接器  
  
-   **WMI** – 虛擬機器管理服務會公開一組 Windows Management Instrumentation WMI 為基礎的 Api 管理和控制虛擬機器。  
  
 大部分的這些授權條款中所定義[詞彙](../technical-guides/glossary8.md)。  
  
> [!NOTE]  
>  [HYPER-V 技術概觀](https://docs.microsoft.com/windows-server/virtualization/hyper-v/hyper-v-technology-overview)是很好的資源。 
  
## <a name="advantages"></a>優點
 在 HYPER-V 虛擬化環境中執行企業層級方案的優點包括：  
  
1.  **硬體資源的彙總**-多部實體伺服器可輕易地合併到相對較少的伺服器藉由實作與 HYPER-V 虛擬化。 彙總可容納已部署的硬體資源的完整使用權。 Windows Server 中的 HYPER-V 可存取主機電腦上的最多 64 個邏輯 Cpu。 這項功能不只會利用新的多核心系統，這也表示大於每個實體主機的虛擬機器彙總比例。  
  
2.  **輕鬆管理**:  
  
    -   彙總的資源集中化會簡化管理。  
  
    -   向上延展和向外的延展的實作被容納多更輕鬆。  
  
3.  **節省成本的有效**:  
  
    -   因為多部虛擬機器可以在單一實體機器上執行，可大幅降低硬體成本，因此，不需要每一部個別的實體機器。  
  
    -   HYPER-V 授權成本可能會包含與 Windows Server 授權成本，而且也可以當做獨立產品購買。
  
    -   藉由將合併到虛擬化的 HYPER-V 環境，因為 「 足跡 」 減少實體硬體上的現有應用程式可能會大幅降低電源需求，並在需要。  
  
4.  **錯誤容錯支援透過 HYPER-V 叢集**– 因為 HYPER-V 是感知叢集應用程式、 Windows Server 提供原生的主機叢集為 HYPER-V 虛擬化環境中建立的虛擬機器的支援。  
  
5.  **簡化部署和管理**:  
  
    -   現有伺服器合併到較少的實體伺服器可以簡化部署。  
  
    -   使用 System Center Virtual Machine Manager 完整的 HYPER-V 管理方案。 [在 System Center VMM 中最新消息](https://docs.microsoft.com/system-center/vmm/whats-new?view=sc-vmm-2016)提供一些指引。
  
6.  **索引鍵 HYPER-V 效能特性**:  
  
    -   **改善的硬體共用架構**-HYPER-V 提供改善的存取和使用率的核心資源，例如磁碟、 網路功能，並配備感知 hypervisor 的核心和使用的視訊時執行的來賓作業系統必要的虛擬伺服器用戶端 (VSC) 程式碼 （稱為 HYPER-V 啟發 I/O）。 強化套件是為了協助降低成本的記憶體管理等特定的作業系統函式對作業系統的增強功能。 整合元件，包括 VSC 驅動程式，也可供其他用戶端作業系統。  
  
         磁碟效能非常重要的磁碟 I/O 密集的企業應用程式，例如 Microsoft BizTalk Server 和 HYPER-V 除了啟發的 I/O;HYPER-V 提供 「 通過 」 磁碟支援，可提供與實體磁碟效能同等的磁碟效能。 請注意 「 通過 」 磁碟支援，提供在方便的小型成本，改善的效能。 「 通過 」 磁碟是本質上實體磁碟/Lun，連接至虛擬機器，並不支援某些功能的虛擬磁碟，例如虛擬機器快照。  
  
    -   **處理器硬體輔助虛擬化支援**– HYPER-V 可充分利用可用的最近使用的處理器技術的處理器硬體輔助虛擬化支援。  
  
    -   **多核心 (SMP) 客體作業系統支援**– HYPER-V 能夠在虛擬機器環境中，以便利用完整的多執行緒處理功能中的虛擬應用程式可支援最多四個處理器機器。  
  
    -   **32 位元和 64 位元的客體作業系統支援**– HYPER-V 同時執行不同類型的作業系統，包括跨不同的伺服器平台，例如視窗中，32 位元和 64 位元系統提供廣泛的支援Linux®，和其他人。  
  
8.  **完整的產品支援**– Microsoft 企業應用程式 （例如 Exchange Server 和 SQL Server） 全面測試在 HYPER-V 中執行，因為 Microsoft 程式碼修正時提供支援這些應用程式已部署並在 HYPER-V 中執行環境。  
  
9. **延展性**– 額外處理電源、 網路頻寬和儲存體容量，可透過快速且輕鬆地 apportioning 其他可用的資源從主機電腦的客體虛擬機器。 這可能需要在主機電腦會在升級或客體虛擬機器會移至更適用的主機電腦。  
  
 如需有關優點的運用提供與 HYPER-V 虛擬化技術的深入資訊，請參閱[HYPER-V 技術概觀](https://docs.microsoft.com/windows-server/virtualization/hyper-v/hyper-v-technology-overview)。 
  
## <a name="disadvantages"></a>缺點
 執行 HYPER-V 的虛擬化環境中的企業級解決方案的缺點可能包括：  
  
-   **硬體需求 –**伺服器彙總的要求，因為 HYPER-V 虛擬機器會消耗更多的 CPU 和記憶體，而且需要更大的磁碟 I/O 頻寬比可比較運算的載入與實體伺服器。 64 位元和 Windows Server 的所有版本的 64 位元只才可用 HYPER-V 伺服器角色，因為實體硬體必須支援硬體輔助虛擬化。 這表示處理器必須相容於 Intel VT 或 AMD 虛擬化 (AMD-V) 技術、 在系統 BIOS 必須支援的資料執行防止 (DEP)，而且必須啟用 DEP。  
  
-   **軟體需求 –**雖然大部分的 Microsoft 軟體支援 HYPER-V 虛擬機器上執行，某些 Microsoft 軟體正在仍然正在測試以確保與 HYPER-V 虛擬化環境的相容性。 例如，大部分 Microsoft 企業層級的應用程式支援在 HYPER-V 上執行，或是正在支援在 HYPER-V 上的測試良好與否。 BizTalk Server 和 HYPER-V 上的 SQL Server 上可支援性資訊，請參閱[附錄 c: BizTalk Server 和 SQL Server 為 HYPER-V 可支援性](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md)。