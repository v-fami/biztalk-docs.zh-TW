---
title: 檢查清單： 安裝和設定 HYPER-V 上的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b5ddbb5-3752-4294-ae6a-c14363b3ddc9
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb6f268a532eec3c633197320abb99fff563063b
ms.sourcegitcommit: 3371ffd8ceca02e2b3715d53a1e0c0a59045912e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34848998"
---
# <a name="checklist-best-practices-for-installing-and-configuring-biztalk-server-on-hyper-v"></a>檢查清單： 安裝和設定 BizTalk Server 上使用 HYPER-V 的最佳作法
下列各節會摘要說明安裝和設定需求中所述[部署在 HYPER-V 上的 BizTalk Server](../technical-guides/deploying-biztalk-server-on-hyper-v.md)一節。 這些應該用在安裝、 設定及部署時，快速參考[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 HYPER-V 環境中。 如需詳細資訊，會提供相關章節的連結。  
  
## <a name="before-installing-hyper-v"></a>然後再安裝 HYPER-V...  
  
|步驟|參考|  
|----------|---------------|  
|HYPER-V 是適用於 64 位元版本的 Windows Server 的伺服器角色。|請參閱[檢查清單： 安裝和設定 BizTalk Server 上使用 HYPER-V 的最佳作法](../technical-guides/checklist-best-practices-to-install-and-configure-biztalk-server-on-hyper-v.md)|  
|請確定您的處理器支援硬體輔助虛擬化和資料執行防止 (DEP)，而且已啟用這些功能。 這需要與 Intel 虛擬化技術 (Intel VT) 或 AMD 虛擬化 (AMD-V) 相容的處理器。|請參閱[安裝 HYPER-V 角色](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)。|  
|使用 Windows Server Core Edition 的根磁碟分割。 將伺服器的負擔降至最低，並改善 HYPER-V 效能。|請參閱[安裝 Server Core](https://docs.microsoft.com/windows-server/get-started/getting-started-with-server-core)。|  
|在根磁碟分割上執行只 HYPER-V 伺服器角色。|請參閱[效能調整使用 HYPER-V 的伺服器](https://docs.microsoft.com/windows-server/administration/performance-tuning/role/hyper-v-server/):<br />**固定的伺服器角色**<br />根磁碟分割只能專用於虛擬化伺服器角色。 其他伺服器角色可能會影響虛擬化伺服器的效能，特別是當它們會消耗大量 CPU、 記憶體或 I/O 頻寬。 最小化在根磁碟分割中的伺服器角色中還有其他好處，例如減少受攻擊面和更新的頻率。 系統管理員應該請仔細考慮哪些軟體安裝在根磁碟分割中因為部分軟體可能會影響虛擬化伺服器的整體效能。<br/><br/> 請參閱[HYPER-V 設定](https://docs.microsoft.com/windows-server/administration/performance-tuning/role/hyper-v-server/configuration)指導方針。|  
  
## <a name="when-creating-hyper-v-virtual-machines"></a>建立 HYPER-V 虛擬機器...  
  
|步驟|參考|  
|----------|---------------|  
|使用固定的大小虛擬硬碟 (VHD) 可提供更佳的效能相較於動態調整大小的 Vhd，作業系統磁碟機。|請參閱[HYPER-V 存放裝置 I/O 效能](https://docs.microsoft.com/windows-server/administration/performance-tuning/role/hyper-v-server/storage-io-performance)指導方針： <br />**固定大小的 VHD**<br />建立 VHD 檔案時，會先配置空間 VHD。 這種類型的 VHD 是較不容易引起片段，可降低當單一 I/O 分裂成數個 I/o 的 I/O 輸送量。 它有三種 VHD 類型的最低的 CPU 額外負荷，因為讀取和寫入不需要查閱區塊的對應。|  
|用於大量的磁碟 I/O 活動的大小固定虛擬硬碟 (VHD) 磁碟，並設定為使用 SCSI 控制站的資料磁碟區的磁碟。 對於跨越多個資料磁碟機的極大量的儲存體 I/O 工作負載，每個 VHD 應該附加到另一個更佳的整體效能的綜合 SCSI 控制器。 此外，每個 VHD 應該儲存在個別的實體磁碟上。|請參閱[HYPER-V 存放裝置 I/O 效能](https://docs.microsoft.com/windows-server/administration/performance-tuning/role/hyper-v-server/storage-io-performance)指導方針：<br />**綜合 SCSI 控制器**<br />綜合的存放裝置控制站提供具有降低的 CPU 額外負荷比模擬的 IDE 裝置的儲存體 I/o 大幅提升效能。 VM 整合服務包括啟用這個儲存體裝置驅動程式，以及所需的客體作業系統偵測到它。 作業系統磁碟必須裝載在 IDE 裝置作業系統開機正確，但 VM 整合服務載入連接至與綜合的存放裝置的 IDE 裝置 I/o 的篩選器驅動程式。<br />我們強烈建議您掛接直接到綜合 SCSI 控制器的資料磁碟機，因為該組態具有減少 CPU 額外負荷。 如果其預期的 I/O 速率很高，您應該也裝載記錄檔和作業系統分頁檔，直接綜合 SCSI 控制器。<br />對於跨越多個資料磁碟機的極大量的儲存體 I/O 工作負載，每個 VHD 應該附加到另一個更佳的整體效能的綜合 SCSI 控制器。 此外，每個 VHD 應該儲存在個別的實體磁碟上。|  
|將 VHD 磁碟高 I/O 活動，例如，SQL Server 資料和記錄檔中使用的 SCSI 控制器。 **注意：** 不將系統磁碟連接到 SCSI 控制器。 包含作業系統的虛擬硬碟必須連接到 IDE 控制器。|即使 HYPER-V IDE 控制器與 SCSI 控制器提供相當的效能，可以只当已安裝 HYPER-V 整合服務中安裝 SCSI 控制器。 因此，使用連接傳遞磁碟的 SCSI 控制器可確保確認 HYPER-V 整合服務已安裝，接著將確保最佳的磁碟 I/O 效能。|  
|設定虛擬機器的網路時，請使用而不是傳統網路介面卡的網路介面卡。 傳統網路介面卡可供整合元件不支援的作業系統。|**綜合網路介面卡**<br />綜合網路介面卡，特別針對 Vm 來達成大幅降低 CPU 額外負荷的 HYPER-V 功能網路 I/O 的比較來模擬的網路介面卡，以模擬現有硬體時。 之間的子系和根磁碟分割 over VMBus 使用共用的記憶體更有效率的資料傳輸進行通訊的綜合網路介面卡。 模擬的網路介面卡應該透過 VM 的 [設定] 對話方塊來移除並取代的綜合網路介面卡。 客體會需要安裝 VM 整合服務。|  
|請確定 integration services 安裝在任何啟用的客體作業系統上，並確認已安裝最新版的整合服務。 若要檢查最新版本的 integration services，執行**Windows Update**。|請參閱[HYPER-V 處理器效能](https://docs.microsoft.com/windows-server/administration/performance-tuning/role/hyper-v-server/processor-performance)指導方針：<br />**啟用的客體**<br />它可能會建議使用 Windows Server 做為客體作業系統。 強化套件來減少 Windows 在 VM 中執行的 CPU 額外負荷。 Integration services 提供額外的強化套件的 I/O。 根據伺服器負載，它可能適用於裝載伺服器應用程式在 Windows Server 的客體，較佳的效能。|  
|可能的話，設定虛擬處理器給可用的邏輯處理器的 1-1 配置。|如需設定虛擬處理器給可用的邏輯處理器的 1-1 配置的詳細資訊，請參閱中的 < 最佳化處理器效能 > 一節[檢查清單： 在 HYPER-V 上的 最佳化效能](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md)。|  
|轉換或移轉虛擬機器的 Microsoft Virtual PC、 Microsoft Virtual Server 或 HYPER-V 上執行的 VMWare ESX Server 上執行。|使用 System Center Virtual Machine Manager 將轉換或移轉虛擬機器在 HYPER-V 上執行。 <br />-如果有需要，可以手動執行轉換虛擬機器在 Microsoft Virtual PC 或 Microsoft Virtual Server 上執行的程序。 如需詳細資訊，請參閱[虛擬機器移轉指南： 若要移轉的方式從 Virtual Server hyper-v](http://go.microsoft.com/fwlink/?LinkID=137258)。<br />-範例工具**VMC2Hyper V**也可用來將 Microsoft Virtual PC 或 Microsoft Virtual Server 上執行 HYPER-V 的虛擬機器移轉。 如需 VMC2Hyper V 範例工具的詳細資訊，請參閱[設為 HYPER-V 匯入工具使用 VMC](http://go.microsoft.com/fwlink/?LinkID=135683)。 |  
  
## <a name="when-installing-and-configuring-biztalk-server"></a>安裝和設定 BizTalk Server 時...  
 在虛擬環境中安裝 BizTalk Server 時，應遵循相同的作法如所示的實體環境。 安裝時，BizTalk Server 組態期間，應該利用下列資源：  
  
|步驟|參考|  
|----------|---------------|  
|如需有關如何在客體作業系統上安裝 BizTalk Server 的指示，請參閱[BizTalk Server 安裝指南](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。| |  
|執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Best Practices Analyzer (BPA) 工具完成 BizTalk Server 安裝上的。|下載[BPA](https://www.microsoft.com/download/details.aspx?id=43382)|  
|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫裝載在 SQL Server 上。 在 SQL Server 執行個體上執行 Sql Server 最佳做法分析程式 (BPA) 工具，然後再設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。|下載[SQL Server BPA](https://www.microsoft.com/download/details.aspx?id=29302)|  
|Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]操作指南提供操作可以用於確保所有必要的先決條件軟體已安裝的整備檢查清單。 提供的檢查清單[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]過程所需的所有元件都提供特定的組態資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包括作業系統、 IIS 和 SQL Server 的堆疊。 此外，指南會提供關於如何設定 BizTalk Server 高可用性。|讀取 (../technical-guides/BizTalk 作業 Guide](biztalk-server-2010-operations-guide.md)|  
|最佳化您的 BizTalk Server 安裝的效能。|請參閱[BizTalk Server 效能最佳化指南](../technical-guides/biztalk-server-2010-performance-optimization-guide.md)指導方針|  
|安裝並執行 BizTalk 健全狀況監視器來分析和 BizTalk Server MessageBox 資料庫的組態。|下載[BHM](https://www.microsoft.com/download/details.aspx?id=43716)|  
|確定 CPU 會被正確地配置給在 HYPER-V 中執行的客體作業系統。| 請參閱**測量處理器效能**在[檢查清單： HYPER-V 上測量效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。|
