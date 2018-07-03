---
title: '附錄 b: HYPER-V 架構和功能概觀 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87b6b9a0-a470-43f7-b076-36075477cc34
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9e20add207d9e4303bd823b82b79e8fad6c07c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002143"
---
# <a name="appendix-b-hyper-v-architecture-and-feature-overview"></a>附錄 b: HYPER-V 架構和功能概觀
本主題提供 HYPER-V 架構的概觀，說明 HYPER-V 的優點和缺點。  
  
## <a name="hyper-v-architecture"></a>HYPER-V 架構  
  
 HYPER-V 是 hypervisor 為基礎的虛擬化平台和其中一個 Windows Server 最棒的功能，即時移轉的支援技術。 HYPER-V 與 Windows Server 是能夠快速移轉，可能只要幾秒的停機時間的實體主機之間移動 Vm。 使用即時移轉實體目標之間移動發生毫秒，這表示移轉作業會變得看不到已連線的使用者。 請參閱[的 Windows Server 上的 HYPER-V 新功能](https://docs.microsoft.com/windows-server/virtualization/hyper-v/what-s-new-in-hyper-v-on-windows)。
  
 Hypervisor 是處理器特定虛擬化平台可裝載多部虛擬機器 (Vm) 會彼此隔離，但透過虛擬化的處理器、 記憶體和 I/O 裝置共用的基礎硬體資源。  
  
 HYPER-V 虛擬機器中執行的客體作業系統提供接近實體硬體上執行的作業系統效能的效能*如果*的所需的虛擬伺服器用戶端 (VSC) 驅動程式和服務安裝在客體作業系統上。 HYPER-V 虛擬伺服器用戶端 (VSC) 程式碼，也就是 HYPER-V 啟用 I/O，可讓您直接存取 HYPER-V 「 虛擬機器匯流排 」，並且只適用於 HYPER-V 整合服務的安裝。 VSC 驅動程式所提供的 HYPER-V 整合服務也可供其他用戶端作業系統。  
  
 HYPER-V 支援方面的資料分割的隔離。 資料分割是隔離的由作業系統執行所在的 hypervisor 支援的邏輯單元。 Microsoft hypervisor 必須至少一個父代或根磁碟分割，執行 Windows Server。 虛擬化堆疊會在父磁碟分割中執行，並可直接存取硬體裝置。 根分割區接著會建立子系裝載客體作業系統的資料分割。 根磁碟分割會建立使用 hypercall 應用程式開發介面 (API) 的子磁碟分割。  
  
 資料分割並沒有存取權的實體處理器，也請務必處理處理器插斷。 相反地，它們具有虛擬處理器的檢視，並在私用，每個客體資料分割的虛擬記憶體位址區域中執行。 Hypervisor 會處理處理器的中斷，並將它們重新導向至個別的分割區。 也可以為 HYPER-V 的硬體加速使用輸入輸出記憶體管理單元 （iommu 所致） 的運作獨立 CPU 所使用的記憶體管理硬體的各種來賓虛擬位址空間之間的位址轉譯。 IOMMU 用來重新對應至位址所使用的子磁碟分割的實體記憶體位址。  
  
 子磁碟分割也不需要直接存取其他硬體資源，並顯示虛擬資源中，檢視為虛擬裝置 (VDevs)。 透過 VMBus 或 hypervisor 中的父磁碟分割，用來處理要求的裝置，會被重新導向要求的虛擬裝置。 VMBus 是邏輯間資料分割的通訊通道。 父分割區會裝載虛擬化服務提供者 (Vsp) over VMBus 來處理從子磁碟分割的裝置存取要求進行通訊。 子磁碟分割主機虛擬化服務取用者 (Vsc) 的要求重新導向的裝置到 Vsp 中透過 VMBus 父磁碟分割。 這整個程序是透明客體作業系統。  
  
 虛擬裝置也可以利用 Windows Server 虛擬化功能，稱為啟用 I/O、 儲存體、 網路、 圖形和輸入的子系統。 已啟用的 I/O 是使用 VMBus 直接略過任何裝置的模擬層的高層級的通訊協定 （例如 SCSI) 的特製化感知虛擬化實作。 這會使溝通更有效率，但需要是 hypervisor 和 VMBus 感知的已啟用的客體。 HYPER-V 啟用 I/O 和 hypervisor 知道的核心提供透過 HYPER-V integration services 的安裝。 整合元件，包括虛擬伺服器用戶端 (VSC) 驅動程式，也可供其他用戶端作業系統。 HYPER-V 需要包含硬體輔助虛擬化，例如處理器隨附 Intel VT 或 AMD 虛擬化 (AMD-V) 技術。  
  
 下圖提供 Windows Server 上執行的 HYPER-V 環境的架構的高階概觀。  
  
 ![Hyper&#45;V 架構概觀](../technical-guides/media/eadd2a84-3936-4b48-a0e2-05b94882d848.gif "eadd2a84-3936-4b48-a0e2-05b94882d848")  

  
 縮略字和使用在上圖中的詞彙描述如下：  
  
- **APIC** – 進階可程式化插斷控制器。 會輸出可讓優先權等級指派給它的插斷的裝置。  
  
- **子磁碟分割**– 裝載為客體作業系統的磁碟分割。 透過虛擬機器匯流排 (VMBus) 或 hypervisor 提供所有的存取權的實體記憶體和裝置子磁碟分割。  
  
- **Hypercall** – 與 hypervisor 進行通訊的介面。 Hypercall 介面可容納由 hypervisor 所提供的最佳化功能的存取。  
  
- **Hypervisor** – 位於硬體和一個或多個作業系統之間的軟體層。 其主要工作是要提供稱為 「 磁碟分割的獨立的執行環境。 Hypervisor 控制，並將會進行仲裁基礎硬體的存取權。  
  
- **IC** – 整合元件。 允許子磁碟分割來與其他資料分割和 hypervisor 通訊的元件。  
  
- **I/O 堆疊**– 輸入/輸出堆疊。  
  
- **MSR** – 記憶體服務常式。  
  
- **根磁碟分割**– 管理裝置驅動程式、 電源管理等裝置熱新增/移除電腦層級函式。 根 （或父代） 的資料分割是可直接存取實體記憶體與裝置的唯一資料分割。  
  
- **VID** – 虛擬化基礎結構驅動程式。 提供資料分割管理服務、 虛擬處理器的管理服務及資料分割的記憶體管理服務。  
  
- **VMBus** – 間資料分割有多個作用中的虛擬化分割區的系統上的通訊與裝置列舉所用的通道為基礎的通訊機制。 VMBus 會安裝 HYPER-V 整合服務。  
  
- **VMMS** – 虛擬機器管理服務。 負責管理子磁碟分割內的所有虛擬機器的狀態。  
  
- **VMWP** – 虛擬機器背景工作處理序。 虛擬化堆疊的使用者模式元件。 背景工作處理序提供從 Windows Server 中的執行個體的父磁碟分割至子磁碟分割內的客體作業系統的虛擬機器管理服務。 虛擬機器管理服務會產生不同的背景工作處理序的每個執行中虛擬機器。  
  
- **VSC** – 虛擬化服務用戶端。 綜合裝置執行個體位於子磁碟分割。 Vsc 利用虛擬化服務提供者 (Vsp) 提供在父磁碟分割中的硬體資源。 他們透過與通訊的父磁碟分割中對應的 Vsp VMBus 來滿足子分割裝置 I/O 要求。  
  
- **VSP** – 虛擬化服務提供者。 位於根磁碟分割，並且提供透過虛擬機器匯流排 (VMBus) 的子磁碟分割的綜合裝置支援。  
  
- **WinHv** – Windows Hypervisor 介面程式庫。 WinHv 是本質上分割的作業系統的驅動程式與 hypervisor 可呼叫使用標準 Windows 呼叫慣例 hypervisor 的驅動程式之間的橋樑  
  
- **WMI** – 虛擬機器管理服務會公開一組 Windows Management Instrumentation WMI 為基礎的 Api 來管理和控制虛擬機器。  
  
  中所定義的大部分詞彙[詞彙](../technical-guides/glossary8.md)。  
  
> [!NOTE]  
>  [HYPER-V 技術概觀](https://docs.microsoft.com/windows-server/virtualization/hyper-v/hyper-v-technology-overview)是不錯的資源。 
  
## <a name="advantages"></a>優點
 執行 HYPER-V 的虛擬化環境中的企業級解決方案的優點包括下列各項：  
  
1. **硬體資源的彙總**-多部實體伺服器可輕鬆地合併到相對較少的伺服器藉由實作 hyper-v 虛擬化。 彙總適用於已部署的硬體資源的完整使用權。 在 Windows Server HYPER-V 可存取主機電腦上的最多 64 個邏輯 Cpu。 這項功能不只會充分利用新的多核心系統，這也表示大於每一部實體主機的虛擬機器合併率。  
  
2. **方便管理**:  
  
   -   彙總的資源集中化會簡化管理。  
  
   -   相應增加和相應放大實作以配合多更輕鬆。  
  
3. **節省成本的有效**:  
  
   -   因為多部虛擬機器可以在單一實體機器上執行，可大幅降低硬體成本，因此，在個別的實體機器就不需要每一部電腦。  
  
   -   HYPER-V 授權成本可能會隨附於 Windows Server 授權成本，而且也可能會當做獨立產品購買。
  
   -   藉由將合併到虛擬化的 HYPER-V 環境，因為縮減的實體硬體 「 足跡 」 上的現有應用程式可能會大幅降低電源需求是必要。  
  
4. **錯誤容錯支援透過 HYPER-V 叢集**– 因為 HYPER-V 是感知叢集應用程式、 Windows Server 提供原生的主機叢集的 HYPER-V 虛擬化環境中建立的虛擬機器的支援。  
  
5. **簡化部署和管理**:  
  
   -   彙總較少的實體伺服器至現有的伺服器可簡化部署。  
  
   -   使用 System Center Virtual Machine Manager 具有完整的 HYPER-V 管理解決方案。 [在 System Center VMM 中最新消息](https://docs.microsoft.com/system-center/vmm/whats-new?view=sc-vmm-2016)提供一些指引。
  
6. **索引鍵的 HYPER-V 效能特性**:  
  
   -   **共用架構的改進的硬體**-HYPER-V 提供改善的存取和使用的核心資源，例如磁碟、 網路、 情形，並配備使用感知 hypervisor 的核心及視訊時執行的客體作業系統必要的虛擬伺服器 （稱為 HYPER-V 啟用 I/O） 的用戶端 (VSC) 程式碼。 Enlightenment 是對作業系統，以協助降低成本的特定作業系統功能，例如記憶體管理的增強功能。 整合元件，包括 VSC 驅動程式，也可供其他用戶端作業系統。  
  
        磁碟效能是很重要的磁碟 I/O 密集型的企業應用程式，例如 Microsoft BizTalk Server 和 HYPER-V 除了啟用的 I/O;HYPER-V 提供 「 穿通 」 的磁碟支援，可提供與實體磁碟效能同等的磁碟效能。 請注意 「 穿通 」 的磁碟支援，提供改善的效能，在方便耗費少量成本。 「 傳遞 」 磁碟是本質上實體磁碟/Lun，連接至虛擬機器，並不支援某些虛擬磁碟，例如虛擬機器快照集的功能。  
  
   -   **處理器硬體輔助虛擬化支援**– HYPER-V 可充分使用最近使用的處理器技術的處理器硬體輔助虛擬化支援。  
  
   -   **多核心 (SMP) 的客體作業系統支援**– HYPER-V 讓您能夠在虛擬機器環境中，可讓應用程式，以充分利用多執行緒處理功能，在虛擬機器支援最多四個處理器機器。  
  
   -   **32 位元和 64 位元的客體作業系統支援**– HYPER-V 提供廣泛的支援如同時執行不同類型的作業系統，跨不同的伺服器平台，例如 Windows，包括 32 位元和 64 位元系統Linux®，和其他人。  
  
7. **完整的產品支援**– Microsoft 企業應用程式 （例如 Exchange Server 和 SQL Server） 會在 HYPER-V 中執行，完整測試，因為 Microsoft 的程式碼修正時提供支援這些應用程式已部署並在 HYPER-V 中執行環境。  
  
8. **延展性**– 額外處理能力、 網路頻寬和儲存體容量，可透過快速且輕鬆地 apportioning 其他可用的資源從主機電腦客體虛擬機器。 這可能需要在主機電腦會在升級或客體虛擬機器會移到功能更強大的主機電腦。  
  
   如需詳細的運用虛擬化技術，提供與 HYPER-V 的優點有關的深入資訊，請參閱[HYPER-V 技術概觀](https://docs.microsoft.com/windows-server/virtualization/hyper-v/hyper-v-technology-overview)。 
  
## <a name="disadvantages"></a>缺點
 執行 HYPER-V 的虛擬化環境中的企業級解決方案的缺點可能包括：  
  
-   **硬體需求 –** 伺服器彙總的需求，因為 HYPER-V 虛擬機器會消耗更多的 CPU 和記憶體，而且需要更大的磁碟 I/O 頻寬，比使用比較運算的載入的實體伺服器。 64 位元和 Windows Server 的所有版本的 64 位元只，因為 HYPER-V 伺服器角色只使用實體硬體必須支援硬體輔助虛擬化。 這表示處理器必須相容於 Intel VT 或 AMD 虛擬化 (AMD-V) 技術、 系統 BIOS 必須支援的資料執行防止 (DEP)，而且必須啟用 DEP。  
  
-   **軟體需求 –** 雖然大部分的 Microsoft 軟體都支援 HYPER-V 虛擬機器上執行，某些 Microsoft 軟體正在仍正在測試，以確保與 HYPER-V 虛擬化環境的相容性。 例如，大部分 Microsoft 企業層級應用程式支援在 HYPER-V 上執行，或是在要測試在 HYPER-V 上支援。 BizTalk Server 和 HYPER-V 上的 SQL Server 上可支援性資訊，請參閱[附錄 c: BizTalk Server 和 SQL Server HYPER-V 可支援性](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md)。