---
title: "安裝和設定 BizTalk Server 與 HYPER-V 虛擬機器使用 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86add392-3cde-432d-95d6-c81d68716537
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62e612ed35a20646f686bd178fad01771dbd2cce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-a-hyper-v-virtual-machine-for-use-with-biztalk-server"></a>安裝和設定 BizTalk Server 與 HYPER-V 虛擬機器使用
本主題提供安裝和設定 BizTalk Server 在 HYPER-V 環境中，包括進行安裝和設定 HYPER-V 虛擬機器的建議和建議上安裝 BizTalk Server 的建議HYPER-V 虛擬機器。  
  
## <a name="installing-and-configuring-hyper-v"></a>安裝和設定 HYPER-V  
 然後再安裝 HYPER-V，請參閱[What's New in Windows Server 2008 R2 中 HYPER-V](http://go.microsoft.com/fwlink/?LinkID=202427)。 "Microsoft HYPER-V Server 2008 R2 Getting Started"本指南提供如何安裝和設定詳細資料[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]HYPER-V。 本指南將會位於[http://go.microsoft.com/fwlink/?LinkID=202431](http://go.microsoft.com/fwlink/?LinkID=202431)。  
  
 「 效能調整指導方針適用於 Windows Server 2008 R2"文件提供詳細資料，調整[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]並包含特別著重在 HYPER-V 上的區段。 文件位於[http://go.microsoft.com/fwlink/?LinkID=202087](http://go.microsoft.com/fwlink/?LinkID=202087)。  
  
### <a name="hyper-v-platform-prerequisites"></a>HYPER-V 平台的必要條件  
 HYPER-V 是適用於 64 位元和所有版本的伺服器角色[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]僅有 64 位元。 此外，實體硬體必須支援硬體輔助虛擬化。 這表示處理器必須相容於 Intel 虛擬化技術 (Intel VT) 或 AMD 虛擬化 (AMD-V) 技術、 在系統 BIOS 必須支援的資料執行防止 (DEP)，而且必須啟用 DEP。 具體來說，您必須啟用 Intel XD 位元 （執行停用位元） 或 AMD NX 位元 （無執行位元）。  
  
> [!NOTE]  
>  啟用在系統 BIOS 中的這些選項之後, 完全關閉電腦，然後重新啟動電腦，以確保這些設定會套用。  
  
#### <a name="determining-hardware-requirements"></a>判斷硬體需求  
 伺服器彙總的要求，因為會消耗更多的 CPU 和記憶體，HYPER-V 伺服器，並需要更大的磁碟 I/O 頻寬比可比較運算的載入與實體伺服器。 若要部署的環境，將會符合預期，請考慮下列來判斷您伺服器的實際的硬體需求的因素。  
  
##### <a name="storage-configuration-options"></a>儲存體組態選項  
 存放裝置硬體應該提供足夠 I/O 頻寬和儲存體容量，以符合您計劃裝載虛擬機器的目前和未來需求。 選擇容量使用方式，它可提供效能 HYPER-V 的存放裝置設定時，沒有一項取捨考量。  
  
 在規劃存放裝置設定時，請考慮您要佈建的環境的需求。 生產環境，進入生產階段前和開發環境的需求可能大幅不同。  
  
 如果您要部署生產[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]HYPER-V，效能上的環境會是一個關鍵需求。 若要避免磁碟忙碌實際系統上的 I/O 競爭，主機和客體作業系統上安裝 integration services 和資料磁碟區的磁碟設定使用綜合 SCSI 控制器。 對於跨越多個資料磁碟機的極大量的儲存體 I/O 工作負載，每個 VHD 應該附加到另一個更佳的整體效能的綜合 SCSI 控制器。 此外，每個 VHD 應該儲存在個別的實體磁碟上。 如需有關設定資料的磁碟綜合 SCSI 控制器的磁碟區。 請參閱主題的 < 最佳化磁碟效能 > 一節[檢查清單： 在 HYPER-V 上的 最佳化效能](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md)。  
  
 一般而言，開發環境不會有嚴格效能需求，因為資源使用量最大化多半會是主要的優先順序。 開發環境中裝載多個單一的實體磁碟機上的 VHD 檔案時所提供的效能通常是可接受。  
  
 HYPER-V 支援多種不同類型的儲存體磁碟的選項。 每個儲存體選項可以連接透過 IDE 或 SCSI 控制站至機器。 使用 SCSI 控制站上的 IDE 控制器的潛在好處是，它才正確客體虛擬機器上已安裝正確版本之作業系統的整合元件。 這是直接的方法，可確保正確的作業系統整合元件會安裝在客體作業系統上。  
  
> [!NOTE]  
>  不同於舊版的 Microsoft 虛擬化技術，沒有任何存取虛擬硬碟時，使用虛擬 IDE 控制器或虛擬 SCSI 控制站之間的效能差異。  
  
 若為大量讀取寫入活動，例如裝載[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫穿通磁碟選項提供持續的效能優點，勝過於固定虛擬硬碟 (VHD) 磁碟。 傳遞選項允許虛擬機器能夠直接存取實體磁碟和 NTFS 檔案系統中的根磁碟分割會略過，但不支援某些功能的虛擬磁碟，例如虛擬機器的快照集和叢集支援。 因此穿通磁碟功能不是建議使用 BizTalk 或 SQL Server 環境中因為邊際效能優點是多個遺漏的功能，位移。  
  
 下表摘要說明可用 HYPER-V 存放裝置選項的優缺點:。  
  
|**使用 HYPER-V 的儲存類型**|**專業人員**|**缺點**|**BizTalk Server 的考量**|  
|-------------------------------|--------------|--------------|-------------------------------------------|  
|**固定的大小磁碟**|因為是在其最大可能大小已初始化的 VHD 檔案建立實體硬碟機上時其效能優於動態 VHD。<br /><br /> 這會讓分散程度小於可能與，因此、 降低的案例單一 I/O 分裂成數個 I/o 的位置。 這有 VHD 類型的最低的 CPU 額外負荷，因為讀取和寫入不需要查閱區塊的對應。|需要完整的磁碟空間足夠的事前量配置。|使用對作業系統磁碟區進行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 **重要事項：**啟動磁碟的 HYPER-V 客體磁碟分割必須連接到 IDE 控制器。|  
|**動態擴充磁碟**|VHD 檔案的大小會增加至指定建立磁碟時，為虛擬機器本身上儲存更多資料的大小。 這適用於最有效地使用可用的存放裝置。|效能不比固定大小的 VHD。 這是因為磁碟的區塊開始為歸區塊，但不是受任何實際的空間放在 VHD 檔案。 從這類區塊傳回讀取零的區塊。 第一個區塊時寫入，虛擬化堆疊必須配置區塊的 VHD 檔案內的空間，然後更新對應的中繼資料。 除了這每次參考現有區塊的區塊對應必須查閱中繼資料中。 這會增加的讀取和寫入活動，也會導致增加 CPU 使用量。<br /><br /> 動態成長，也需要伺服器系統管理員監視以確保足夠的磁碟儲存體與儲存體需求增加的磁碟容量。|效能不比固定大小的 VHD。<br /><br /> 如果效能不是問題，例如在開發環境中，這就可能是作業系統的硬碟最適合的選項。<br /><br /> 會造成額外的 CPU 額外負荷，因為區塊對應查閱。|  
|**差異磁碟**|此差異磁碟儲存所有變更，相對於基底 VHD 和基底 VHD 的父-子系組態保持不變。 因此必須儲存在差異 VHD 的子系也就是從父不同區塊。|因為需要存取固定/動態父 VHD 以及差異磁碟的讀取/寫入，則可能會降低效能。 這會增加 CPU 使用率和磁碟 I/O 額外負荷。|大量電腦特定的組態是為了[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]安裝以及子 VHD 檔案可以增長本質上這會使用此磁碟組態的優點最小化。 讀取多個 VHD 在此案例中會產生額外的 CPU 和磁碟 I/O 額外負荷。|  
|**傳遞磁碟**|這些是實體磁碟設定為*離線*根磁碟分割和啟用 HYPER-V 具有獨佔的讀寫存取權的實體磁碟中。|需要完全專用的磁碟或 LUN，才能讓它可配置給虛擬機器。<br /><br /> 實體磁碟是更難比 VHD 檔案的電腦之間移動。|如果您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體在 HYPER-V 上執行，您可能會透過使用固定虛擬硬碟 (VHD) 以傳遞磁碟的必須取得累加式的效能改進[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]資料磁碟區。<br /><br /> 如果您裝載本機檔案接收位置的上[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]或大型訊息串流至磁碟，在處理期間，您可能會取得使用傳遞磁碟，透過使用固定虛擬硬碟 (VHD) 的累加效能改進。|  
  
 如需實作磁碟及存放裝置搭配使用 HYPER-V 的詳細資訊，請參閱[實作磁碟和儲存體](http://go.microsoft.com/fwlink/?LinkID=142362)(http://go.microsoft.com/fwlink/?LinkID=142362)。  
  
##### <a name="networking"></a>網路  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]通常會出現高的網路使用率。 因此，網路效能問題時，請考慮每個虛擬機器配置不同的實體網路介面卡。  
  
 在設定虛擬機器時，請確定您使用網路介面卡，而不是傳統網路介面卡。 傳統網路介面卡被供作業系統不支援整合元件。  
  
 若要測量使用網路效能**"\Network 介面 \Bytes Total/sec"**和**\Network 介面 (\*) \Output 佇列長度**操作主機上的效能監視器計數器要測量的網路卡的整體效能的系統。 如果實體的網路已被識別為忙碌中，使用**"\Hyper-V 虛擬網路介面卡 (\*) \Bytes/sec"**是/是在主機作業系統，以識別哪些虛擬機器網路介面卡上的計數器正在產生高負載。  
  
 如需有關評估在 HYPER-V 環境中的網路效能，請參閱**測量網路效能**區段[檢查清單： 測量的效能，在 HYPER-V 上](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。  
  
##### <a name="cpu"></a>CPU  
 HYPER-V 支援不同的客體作業系統; 不同的虛擬處理器數目下表將摘要說明。 若要配置的最大 CPU 資源[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，將它安裝在[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]客體作業系統，可支援每個虛擬機器的四個虛擬處理器。  
  
 設定虛擬處理器的 1-1 配置在客體作業系統，提供給主機作業系統，以防止內容切換過多的邏輯處理器。 過度內容切換處理器之間會導致效能降低。 如需有關配置的邏輯處理器的虛擬處理器的詳細資訊，請參閱本主題的 < 最佳化處理器效能 > 一節[檢查清單： 在 HYPER-V 上的 最佳化效能](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md)。  
  
 「 \Hyper-V Hypervisor 邏輯 processor （_total)\\%total 執行階段 「 效能監視器計數器會測量所有來賓機器上 HYPER-V 主機的 hypervisor 的整體資源使用量。 如果此值高於 90%，伺服器正在執行最大容量。在此案例中的虛擬機器配置額外的虛擬處理器可能會降低整體系統效能，應該予以避免。 如需詳細資訊使用 HyperV 效能計數器，請參閱[HYPER-V 上評估 BizTalk Server 效能](../technical-guides/evaluating-biztalk-server-performance-on-hyper-v.md)一節。  
  
|作業系統|虛擬處理器限制|  
|----------------------|-----------------------------|  
|[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 所有版本的[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]僅有 64 位元。|4|  
|[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]64 位元|4|  
|[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]32 位元|4|  
|Windows 7 64 位元|4|  
|Windows 7 32 位元|4|  
|Windows Vista 64 位元|2|  
|Windows Vista 32 位元|2|  
  
> [!NOTE]  
>  如需 HYPER-V 上支援的客體作業系統的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkID=118347](http://go.microsoft.com/fwlink/?LinkID=118347)。  
  
##### <a name="memory"></a>記憶體  
 實體伺服器的根磁碟分割和任何在伺服器上執行的虛擬機器需要足夠的記憶體。 在測試期間，最少 2 GB 的記憶體配置到根磁碟分割和**記憶體/可用 Mb**效能監視器計數器受到監視，以確保已發生記憶體不足的壓力。  
  
 應配置給每個虛擬機器的記憶體數量[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]環境取決於工作負載，以及將執行的處理類型。 有許多因素會影響記憶體需求[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]包括：  
  
-   處理訊息的大小  
  
-   訊息輸送量  
  
-   協調流程設計  
  
-   管線處理  
  
-   您計劃執行虛擬機器內的 BizTalk 主控件的數目  
  
 因素會影響記憶體的完整清單，請參閱 「 效能因素 」 一節的 BizTalk Server 效能最佳化指南 》，網址[http://go.microsoft.com/fwlink/?LinkId=122587](http://go.microsoft.com/fwlink/?LinkId=122587)。  
  
 主動監視**記憶體/可用 Mb**計數器從每個虛擬機器和根磁碟分割本身內。 從下列指導方針[檢查清單： 在 HYPER-V 上的測量效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)應該用來判斷是否有足夠的可用實體記憶體的虛擬機器和根磁碟分割：  
  
-   可用的記憶體的 50%或更 = 狀況良好  
  
-   25%的可用的記憶體 = 監視器  
  
-   可用的記憶體的 10%= 警告  
  
-   可用的記憶體低於 5%= 重大，效能會受到負面影響  
  
#### <a name="choosing-root-operating-system-version"></a>選擇根作業系統版本  
 HYPER-V 支援在 Server Core 與完整安裝上[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 根磁碟分割的額外負荷降到最低，請在的 Server Core 安裝上安裝 HYPER-V [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 可以從不同的系統上的 HYPER-V 管理員從遠端管理的 HYPER-V 角色。 Server Core 提供較小的磁碟和記憶體設定檔，因此，留下較多資源可供虛擬機器。 如需有關適用於 Server Core 安裝選項[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，請參閱[http://go.microsoft.com/fwlink/?LinkID=202439](http://go.microsoft.com/fwlink/?LinkID=202439)。  
  
 如果您選擇要使用的完整安裝[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，請確定根磁碟分割只專用的 HYPER-V 伺服器角色。 執行其他伺服器角色時，會耗用記憶體、 磁碟、 處理器和網路資源，而且會降低效能。  
  
#### <a name="creating-your-virtual-machines"></a>建立虛擬機器  
 您已安裝並設定 HYPER-V 伺服器角色之後，您需要建立虛擬機器。 執行此操作之前會很有用回答下列問題：  
  
-   將使用何種儲存體設定？  
  
-   客體作業系統支援的虛擬處理器數目？  
  
-   將虛擬機器配置多少記憶體？  
  
-   在 HYPER-V 伺服器上可以執行多少虛擬機器？  
  
-   如何將會安裝到電腦上的作業系統？  
  
 如需如何建立和設定虛擬機器的詳細資訊，請參閱[建立虛擬機器](http://go.microsoft.com/fwlink/?LinkID=202440)。  
  
##### <a name="installing-the-base-operating-system"></a>安裝基礎作業系統  
 在 HYPER-V 中使用所有可用的實體伺服器安裝的選項。 若要執行手動安裝可用的可開機 CD/DVD-ROM 媒體或 ISO 映像。 如果已設定虛擬機器網路介面卡連線至裝載的 ISO 映像的伺服器相同的網路，可以執行的網路安裝。  
  
> [!IMPORTANT]  
>  選擇何種安裝方法，基於效能很重要的作業系統整合元件安裝在 HYPER-V 執行每個虛擬機器。 整合元件會提供一組驅動程式和服務，可讓客體機器使用綜合裝置來執行。 綜合裝置避免針對模擬裝置，不支援整合元件的作業系統可用的需求。 模擬的裝置會更高的系統負擔，相較於綜合裝置。  
  
 安裝和設定本實驗室使用的機器，初始的基底映像建立固定大小的 VHD 上。 這牽涉到手動安裝的[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 一旦所有適當的更新已安裝基底的虛擬機器已建立映像使用 sysprep 公用程式與 Windows Server 2008 安裝的 %WINDIR%\system32\sysprep 目錄。  
  
> [!NOTE]  
>  執行 Sysprep[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]已安裝並設定在伺服器即可透過 Sysprep 回應檔案使用，以及指令碼提供[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。 這些範例指令碼專為搭配[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]上安裝[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 如需詳細資訊，請參閱[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]線上文件。  
  
## <a name="installing-and-configuring-biztalk-server"></a>安裝和設定 BizTalk Server  
  
-   若要安裝虛擬機器所需的時間降到最低，建立只包含客體作業系統和軟體必要條件的基底映像。 使用 SysPrep 準備的 VHD 映像，供重複使用，，然後根據此 VHD 中的所有虛擬機器 (Vm)。  
  
    > [!NOTE]  
    >  與[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，便可針對基底映像執行 Sysprep*之後*[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]已安裝並設定在伺服器上。 這可以透過使用 Sysprep 回應檔案來達成，以及指令碼提供[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。 這些範例指令碼專為搭配[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]上安裝[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。 如需詳細資訊，請參閱[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]線上文件。  
    >   
    >  Windows 自動安裝參照位於[http://go.microsoft.com/fwlink/?LinkId=142364](http://go.microsoft.com/fwlink/?LinkId=142364)。  
  
-   請遵循建議 [時安裝和設定 BizTalk Server] 主題的章節[檢查清單： 安裝和設定 BizTalk Server 在 HYPER-V 上的最佳作法](../technical-guides/checklist-best-practices-to-install-and-configure-biztalk-server-on-hyper-v.md)。  
  
-   如需有關的支援能力資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在 HYPER-V 環境中，請參閱[附錄 c: BizTalk Server 和 SQL Server 為 HYPER-V 可支援性](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md)。