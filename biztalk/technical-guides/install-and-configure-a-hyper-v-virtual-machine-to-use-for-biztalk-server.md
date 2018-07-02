---
title: 安裝和設定 BizTalk server 的 HYPER-V 虛擬機器使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 86add392-3cde-432d-95d6-c81d68716537
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f350c34949d0cc4f5dd454119b68e488cd0924ba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977303"
---
# <a name="installing-and-configuring-a-hyper-v-virtual-machine-for-use-with-biztalk-server"></a>安裝和設定 HYPER-V 虛擬機器，以便使用與 BizTalk Server
本主題提供安裝和設定 BizTalk Server 在 HYPER-V 環境中，包括安裝及設定 HYPER-V 虛擬機器的建議和建議上安裝 BizTalk Server 的建議HYPER-V 虛擬機器。  

## <a name="installing-and-configuring-hyper-v"></a>安裝和設定 HYPER-V  
 然後再安裝 HYPER-V，請參閱[What's New in Windows Server 2008 R2 中 HYPER-V](http://go.microsoft.com/fwlink/?LinkID=202427)。 "Microsoft HYPER-V Server 2008 R2 Getting Started"本指南提供有關如何安裝和設定詳細資料[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]HYPER-V。 本指南將會位於[ http://go.microsoft.com/fwlink/?LinkID=202431 ](http://go.microsoft.com/fwlink/?LinkID=202431)。  

 」 的效能微調指導方針適用於 Windows Server 2008 R2"的文件會詳述微調[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]並包含特別著重在 HYPER-V 上一節。 文件位於[ http://go.microsoft.com/fwlink/?LinkID=202087 ](http://go.microsoft.com/fwlink/?LinkID=202087)。  

### <a name="hyper-v-platform-prerequisites"></a>HYPER-V 平台的必要條件  
 HYPER-V 是適用於 64 位元和所有版本的伺服器角色[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]僅有 64 位元。 此外，在實體硬體必須支援硬體輔助虛擬化。 這表示處理器必須相容於 Intel Virtualization Technology (Intel VT) 或 AMD 虛擬化 (AMD-V) 技術、 系統 BIOS 必須支援的資料執行防止 (DEP)，而且必須啟用 DEP。 具體來說，您必須啟用 Intel XD 位元 （執行停用位元） 或 AMD NX 位元 （無執行位元）。  

> [!NOTE]  
>  啟用在系統 BIOS 中的這些選項之後, 完全關閉電腦，並再重新啟動電腦以確保這些設定會套用。  

#### <a name="determining-hardware-requirements"></a>判斷硬體需求  
 伺服器彙總的需求，因為會消耗更多的 CPU 和記憶體，HYPER-V 伺服器，並需要更大的磁碟 I/O 頻寬，比使用比較運算的載入的實體伺服器。 若要部署的環境中，將會符合預期，請考慮以判斷實際的硬體需求，您的伺服器的下列各項因素。  

##### <a name="storage-configuration-options"></a>儲存體組態選項  
 存放裝置硬體應該提供足夠 I/O 頻寬和儲存體容量，以符合您打算裝載虛擬機器的目前和未來需求。 選擇適用於 HYPER-V 的存放裝置設定容量使用方式，它可以提供效能時，則需要有所取捨。  

 在規劃儲存體設定，請考慮您要佈建環境的需求。 適用於生產、 進入生產階段前和開發環境的需求可能大幅不同。  

 如果您要部署在 HYPER-V 上的 BizTalk Server 環境的實際執行，效能將會一個關鍵需求。 若要避免磁碟 I/O 競爭，忙碌的生產系統上，主機和客體作業系統上安裝 integration services，並使用綜合 SCSI 控制站設定為資料磁碟區的磁碟。 對於跨越多個資料磁碟機的極大量的儲存體 I/O 工作負載，每個 VHD 應該附加至個別的綜合 SCSI 控制器以提升整體效能。 此外，每個 VHD 應該儲存在個別的實體磁碟上。 如需有關設定資料磁碟與綜合 SCSI 控制站的磁碟區請參閱本主題的 < 最佳化磁碟效能 > 一節[檢查清單： 在 HYPER-V 上的 最佳化效能](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md)。  

 一般而言，開發環境不會有嚴格的效能需求，因為最大化資源使用率通常是主要的優先順序。 用於開發環境提供裝載單一的實體磁碟機上的多個 VHD 檔案時的效能是通常可接受的。  

 HYPER-V 支援許多不同類型的儲存體磁碟選項。 每個儲存體選項可以連接的 IDE 或 SCSI 控制器透過至機器。 透過 IDE 控制器的 SCSI 控制器的潛在優點是，它將僅可正確運作如果客體虛擬機器上已安裝正確版本之作業系統的整合元件。 這是直接的方法，以確保正確的作業系統整合元件會安裝在客體作業系統上。  

> [!NOTE]  
>  不同於舊版的 Microsoft 虛擬化技術，存取虛擬硬碟時，使用虛擬 IDE 控制器或虛擬 SCSI 控制器之間沒有效能差異。  

 針對密集讀取-寫入活動，例如裝載[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫穿通磁碟選項提供持續的效能優點，勝過於固定虛擬硬碟 (VHD) 磁碟。 傳遞選項允許直接存取實體磁碟的虛擬機器和 NTFS 檔案系統根磁碟分割中的會略過，但不支援虛擬磁碟，例如虛擬機器快照集和叢集的特定功能支援。 因此 「 穿通磁碟 」 功能不是建議使用在 BizTalk 或 SQL Server 環境中因為臨界效能優勢會超過偏移缺少的功能。  

 下表摘要說明可用的 HYPER-V 儲存體選項的優缺點:。  


|    **HYPER-V 儲存體類型**     |                                                                                                                                                                                                      **專業人員**                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                              **缺點**                                                                                                                                                                                                                                                                                                                                                                                              |                                                                                                                                                                                                                                                     **BizTalk Server 的考量**                                                                                                                                                                                                                                                      |
|---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **固定的大小磁碟**       | 因為是在其最大可能大小已初始化的 VHD 檔案建立實體硬碟機上時，請執行優於動態 VHD。<br /><br /> 這的確可以減輕可能，因此，可減少單一 I/O 分割成多個 I/o 的處的案例。 這會有 VHD 類型的最低的 CPU 額外負荷，因為讀取和寫入不需要查閱區塊的對應。 |                                                                                                                                                                                                                                                                                                                                                                   需要的磁碟空間預付全額的配置。                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                   用於作業系統磁碟區上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 **重要事項：** HYPER-V 來賓磁碟分割的啟動磁碟必須連接到 IDE 控制器。                                                                                                                   |
| **動態擴充磁碟** |                                                                                                        VHD 檔案的大小會增加時，指定建立磁碟，如需詳細資料會儲存在虛擬機器本身的大小。 這適用於最有效使用可用的儲存體。                                                                                                        | 效能不比固定大小的 VHD。 這是因為磁碟中的區塊開始填零的區塊，但不是受任何實際的空間中的 VHD 檔案。 從傳回這類區塊中讀取的零的區塊。 第一個區塊時寫入，虛擬化堆疊必須配置區塊內的 VHD 檔案的空間，然後更新對應中繼資料。 除了這每次參考現有區塊的區塊對應必須查閱中繼資料中。 這樣可增加的讀取和寫入活動會增加 CPU 使用率。<br /><br /> 動態成長也需要伺服器系統管理員監視以確保沒有足夠的磁碟儲存體作為儲存體需求增加的磁碟容量。 |                                                                                                                               效能不比固定大小的 VHD。<br /><br /> 如果效能不重要的考量，例如在開發環境中，這就可能是最適合的選項，作業系統的硬碟。<br /><br /> 會導致額外的 CPU 額外負荷，因為區塊對應查閱。                                                                                                                                |
|     **差異磁碟**      |                                                                               此父子式組態差異磁碟儲存所有變更，相對於基底 VHD 和基底 VHD 的位置保持不變。 因此也就是從父代的不同區塊必須儲存在差異 VHD 的子系。                                                                               |                                                                                                                                                                                                                                                                                                          因為需要存取固定/動態父 VHD 以及差異磁碟的讀取/寫入，則可能會降低效能。 這會增加 CPU 使用率和磁碟 I/O 額外負荷。                                                                                                                                                                                                                                                                                                           |                                                                                                                     大量機器特定的組態需要的 BizTalk Server 安裝，而且子 VHD 檔可能會變得基本上這會減少使用此磁碟組態的優點。 讀取多個 VHD 在此案例中會產生額外的 CPU 和磁碟 I/O 額外負荷。                                                                                                                     |
|      **穿透式磁碟**      |                                                                                                                               這些是實體磁碟設定為*離線*在根磁碟分割及實體磁碟的獨占讀寫存取的啟用 HYPER-V。                                                                                                                                |                                                                                                                                                                                                                                                                                                        為了讓它配置給虛擬機器需要完全專用的磁碟或 LUN。<br /><br /> 實體磁碟很難比 VHD 檔案在電腦之間移動。                                                                                                                                                                                                                                                                                                         | 如果您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體在 HYPER-V 上執行，您可能會利用透過使用 BizTalk Server 的資料磁碟區的固定虛擬硬碟 (VHD) 的傳遞磁碟取得累加式的效能改進。<br /><br /> 如果您要裝載在本機檔案接收 BizTalk Server 上的位置，或資料流處理大型訊息處理期間的磁碟，您可能會取得使用傳遞磁碟，透過使用固定虛擬硬碟 (VHD) 的累加式的效能改進。 |

 如需實作磁碟和儲存體與 HYPER-V 的詳細資訊，請參閱[實作磁碟和儲存體](http://go.microsoft.com/fwlink/?LinkID=142362)(http://go.microsoft.com/fwlink/?LinkID=142362)。  

##### <a name="networking"></a>網路  
 BizTalk Server 會呈現相當高的網路使用率。 因此，網路效能問題時，請考慮為每個虛擬機器配置不同的實體網路卡。  

 在設定虛擬機器時，請確定您使用網路介面卡，而不是傳統網路介面卡。 傳統網路介面卡被適用於不支援整合元件的作業系統。  

 若要測量使用網路效能 **"\Network 介面 \Bytes Total/sec"** 並**\Network 介面 (\*) \Output 佇列長度**操作主機上的效能監視器計數器若要測量的網路卡的整體效能的系統。 如果實體網路已被識別為忙碌中，使用 **"\Hyper-V 虛擬網路介面卡 (\*) \Bytes/sec"** 是/是主機作業系統，以識別哪些虛擬機器網路介面卡上的計數器正在產生高負載。  

 如需評估網路上的 HYPER-V 環境的效能詳細資訊，請參閱**測量網路效能**一節[檢查清單： 測量 HYPER-V 上的效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。  

##### <a name="cpu"></a>CPU  
 HYPER-V 支援不同數目的虛擬處理器不同的客體作業系統;下表摘要說明。 若要為 BizTalk Server 中配置的最大的 CPU 資源，將它安裝在[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]客體作業系統，可支援每個虛擬機器的四個虛擬處理器。  

 設定虛擬處理器的 1 對 1 配置給主機作業系統，以防止內容切換過多可用的邏輯處理器的客體作業系統中。 過多的處理器之間切換的內容會導致效能降低。 如需有關配置虛擬處理器與邏輯處理器的詳細資訊，請參閱主題的 < 最佳化處理器效能 > 一節[檢查清單： 在 HYPER-V 上的 最佳化效能](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md)。  

 「 \Hyper-V Hypervisor 邏輯 processor （_total)\\%total 執行階段 「 效能監視器計數器會測量所有來賓機器和 HYPER-V 主機上的 hypervisor 的整體資源使用量。 如果此值高於 90%，伺服器正在執行最大容量;在此案例中的虛擬機器的其他虛擬處理器配置可能會降低整體系統效能，應該予以避免。 如需使用 HyperV 效能計數器進一步詳細資訊，請參閱 <<c0> [ 在 HYPER-V 上評估 BizTalk Server 效能](../technical-guides/evaluating-biztalk-server-performance-on-hyper-v.md)一節。  


|                                                                      作業系統                                                                       | 虛擬處理器的限制 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------|
| [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 所有版本的[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]僅有 64 位元。 |            4            |
|                                               [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 64 位元                                               |            4            |
|                                               [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 32 位元                                               |            4            |
|                                                                      Windows 7 64 位元                                                                       |            4            |
|                                                                      Windows 7 32 位元                                                                       |            4            |
|                                                                    Windows Vista 64 位元                                                                     |            2            |
|                                                                    Windows Vista 32 位元                                                                    |            2            |

> [!NOTE]  
>  如需 HYPER-V 上支援的客體作業系統的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkID=118347 ](http://go.microsoft.com/fwlink/?LinkID=118347)。  

##### <a name="memory"></a>記憶體  
 實體伺服器需要足夠的記憶體，根磁碟分割的任何伺服器上執行的虛擬機器。 在測試期間，至少 2 GB 的記憶體配置到根磁碟分割並**記憶體/可用 Mb**效能監視器計數器的監視，以確保已發生記憶體不足的壓力。  

 應配置給每個 BizTalk Server 環境中的虛擬機器的記憶體數量取決於工作負載，並將執行的處理類型。 有許多因素會影響記憶體需求的 BizTalk Server 包括：  

- 處理訊息的大小  

- 訊息輸送量  

- 協調流程設計  

- 管線處理  

- 您打算在虛擬機器內執行的 BizTalk 主控件的數目  

  因素會影響記憶體的完整清單，請參閱 「 效能因素 」 一節的 BizTalk Server 效能最佳化指南 》，網址[ http://go.microsoft.com/fwlink/?LinkId=122587 ](http://go.microsoft.com/fwlink/?LinkId=122587)。  

  主動監視**記憶體/可用 Mb**計數器從每個虛擬機器和根資料分割本身內。 從下列指導方針[檢查清單： 測量 HYPER-V 上的效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)應該用來判斷是否有足夠的可用實體記憶體的虛擬機器，並為根分割：  

- 可用的記憶體的 50%或更 = 狀況良好  

- 25%的可用的記憶體 = 監視  

- 10%的可用的記憶體 = 警告  

- 可用的記憶體低於 5%= 嚴重，效能會受到負面影響  

#### <a name="choosing-root-operating-system-version"></a>選擇根作業系統版本  
 在 Server Core 與完整安裝上支援 HYPER-V [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 根磁碟分割的額外負荷降到最低，請在的 Server Core 安裝上安裝 HYPER-V [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 可以從不同的系統上的 HYPER-V 管理員從遠端管理的 HYPER-V 角色。 Server Core 提供的較小磁碟和記憶體設定檔，因此，保留的虛擬機器，提供更多資源。 如需有關適用於 Server Core 安裝選項[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=202439 ](http://go.microsoft.com/fwlink/?LinkID=202439)。  

 如果您選擇使用的完整安裝[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，請確定根磁碟分割只專用的 HYPER-V 伺服器角色。 執行其他伺服器角色時，會耗用記憶體、 磁碟、 處理器和網路資源，而且會降低效能。  

#### <a name="creating-your-virtual-machines"></a>建立您的虛擬機器  
 您已安裝並設定 HYPER-V 伺服器角色之後，您需要建立虛擬機器。 之前這樣做，最好要回答下列問題：  

- 我要使用何種儲存體設定？  

- 客體作業系統支援多少個虛擬處理器？  

- 將虛擬機器配置多少記憶體？  

- 在 HYPER-V 伺服器上可以執行多少虛擬機器？  

- 如何將會安裝到電腦的作業系統？  

  如需如何建立和設定虛擬機器的詳細資訊，請參閱[建立虛擬機器](http://go.microsoft.com/fwlink/?LinkID=202440)。  

##### <a name="installing-the-base-operating-system"></a>安裝基礎作業系統  
 適用於實體伺服器安裝的所有選項都都可以在 HYPER-V 中使用。 可開機的 CD/DVD-ROM 媒體或 ISO 映像可用來執行手動安裝。 如果已設定虛擬機器網路介面卡連接到裝載的 ISO 映像的伺服器相同的網路，就可以執行網路安裝。  

> [!IMPORTANT]  
>  選擇任何安裝方法，基於效能考量很重要的作業系統的整合元件安裝的每個執行 HYPER-V 的虛擬機器。 整合元件會提供一組驅動程式和服務，可讓客體機器使用綜合裝置來執行。 綜合裝置避免不支援整合元件的作業系統使用的模擬裝置的需求。 模擬的裝置會產生更高的系統負荷相較於綜合裝置。  

 若要安裝及設定本實驗室中使用的電腦，固定大小的 VHD 上建立初始的基底映像。 這項作業需要手動安裝[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 一旦已安裝所有適當的更新基礎的虛擬機器已建立映像使用 sysprep 公用程式會隨 Windows Server 2008、windows %WINDIR%\system32\sysprep 目錄中。  

> [!NOTE]
>  執行 Sysprep，已安裝並在伺服器上設定 BizTalk Server 之後，即可透過 Sysprep 回應檔案和 BizTalk Server 隨附的指令碼使用。 這些範例指令碼上已安裝的 BizTalk server 時，專為[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 如需詳細資訊，請參閱 BizTalk Server 的線上文件。  

## <a name="installing-and-configuring-biztalk-server"></a>安裝和設定 BizTalk Server  

- 若要安裝的虛擬機器所需的時間降到最低，建立只包含客體作業系統和軟體必要條件的基底映像。 使用 SysPrep 來準備重複使用的 VHD 映像，然後根據這個 VHD 中的所有您虛擬機器 (Vm)。  

  > [!NOTE]
  >  使用 BizTalk Server 中，就可以針對基底映像執行 Sysprep*之後*已安裝並在伺服器上設定 BizTalk Server。 這可以透過使用 Sysprep 回應檔案和 BizTalk Server 隨附的指令碼來完成。 這些範例指令碼上已安裝的 BizTalk server 時，專為[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 如需詳細資訊，請參閱 BizTalk Server 的線上文件。  
  > 
  >  自動 Windows 安裝程式參照位於[ http://go.microsoft.com/fwlink/?LinkId=142364 ](http://go.microsoft.com/fwlink/?LinkId=142364)。  

- 依照 [時安裝和設定 BizTalk Server] 主題的章節[檢查清單： 安裝和設定 BizTalk Server 在 HYPER-V 上的最佳作法](../technical-guides/checklist-best-practices-to-install-and-configure-biztalk-server-on-hyper-v.md)。  

- 如需有關的支援能力資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在 HYPER-V 環境中，請參閱[附錄 c: BizTalk Server 和 SQL Server HYPER-V 可支援性](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md)。
