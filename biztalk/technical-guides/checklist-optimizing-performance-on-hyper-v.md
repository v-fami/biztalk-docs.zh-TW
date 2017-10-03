---
title: "檢查清單： HYPER-V 上最佳化效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 942a61eb-0fdd-4c8b-b0ad-d32951f0f631
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87591ef1467608dfc17e8d9802d11456213c6947
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-optimizing-performance-on-hyper-v"></a>檢查清單： HYPER-V 上最佳化效能
執行時，適用下列考量[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]及/或[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]擁有的執行個體[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]HYPER-V 虛擬機器上的資料庫。  
  
## <a name="allocate-110125-of-cpu-and-disk-resources-to-the-hyper-v-virtual-machines"></a>110%-125%的 CPU 和磁碟資源配置到 HYPER-V 虛擬機器  
 計劃配置 110%到 125%的 CPU 資源和 105%-110%的方案用的 HYPER-V 虛擬機器的實體硬體解決方案所需的磁碟資源。 藉由設定 HYPER-V 虛擬機器與其他資源，您要確定它可以提供與實體硬體同等的效能，同時配合任何 HYPER-V 虛擬化技術所需的額外負荷。  
  
|步驟|參考|  
|----------|---------------|  
|範圍的硬體需求[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案。|-請遵循 < 規劃環境的 BizTalk Server > 一節中的指引[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]操作指南 》，網址[http://go.microsoft.com/fwlink/?LinkId=122399](http://go.microsoft.com/fwlink/?LinkId=122399)範圍解決方案的硬體需求。<br />對範圍版並將此方案所需的 BizTalk 伺服器數目檢閱的規劃考量記載於 「 規劃 BizTalk Server 層 」 的 BizTalk Server [http://go.microsoft.com/fwlink/?LinkId=122401](http://go.microsoft.com/fwlink/?LinkId=122401)。<br />-若要界定範圍的版本和數目[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]將此方案中，所需的電腦在檢閱的規劃考量記載於 「 規劃資料庫層 」 的資料庫[http://go.microsoft.com/fwlink/?LinkId = 122402](http://go.microsoft.com/fwlink/?LinkId=122402)以及 「 效能額外負荷的執行 SQL Server 中 HYPER-V 」 的章節，可在 「 執行 SQL Server 2008 in a HYPER-V 環境最佳作法和效能考量 > 技術白皮書[http://go.microsoft.com/fwlink/ 嗎？LinkId = 144622](http://go.microsoft.com/fwlink/?LinkId=144622)。<br />-若要完成規劃開發、 測試、 預備及生產環境檢閱 「 規劃開發、 測試、 預備及實際執行環境 」 在[http://go.microsoft.com/fwlink/?LinkId=122403](http://go.microsoft.com/fwlink/?LinkId=122403)。|  
|範圍的硬體需求之後您[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]方案中，若要設定的 HYPER-V 機器的計劃**110%-125%**的 CPU 和磁碟資源的話。|例如，如果實體的硬體需求[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]判斷方案所使用的電腦為 2 GB RAM，2 GHZ 和 2 x 500 GB 的實體磁碟，在執行雙核心 CPU，則 HYPER-V 虛擬機器使用的方案會是理想的情況下，使用 2 個或更多虛擬處理器的執行設定 > = 2.2 GHZ，以及更快的實體磁碟 （通常是藉由增加主軸或使用較快速的磁碟）。|  
  
## <a name="optimize-hyper-v-performance"></a>使用 HYPER-V 的效能最佳化  
 使用下列指導方針來設定 HYPER-V 以獲得最佳效能。  
  
|步驟|參考|  
|----------|---------------|  
|適用於效能調整的虛擬化伺服器建議的指引。 **注意：**的測試案例所述[測試 BizTalk 伺服器虛擬化效能](~/technical-guides/testing-biztalk-server-virtualization-performance.md)，已套用的組態選項所述 」 實體基礎結構細節"和"虛擬化的詳細資料 」 區段[測試案例概觀](~/technical-guides/test-scenario-overview.md)主題。|「 效能調整指導方針的 Windows Server 2008 R2"文件可在 「 虛擬化伺服器的效能微調 」 區段[http://go.microsoft.com/fwlink/?LinkID=202087](http://go.microsoft.com/fwlink/?LinkID=202087)。|  
|關閉不會使用任何虛擬機器連線視窗。|按兩下 HYPER-V 管理員中的虛擬機器名稱時顯示的虛擬機器連線視窗耗用無法否則過低的資源。|  
|最小化 HYPER-V 管理員或關閉。|HYPER-V 管理員會藉由持續輪詢每個執行中虛擬機器的 CPU 使用率和執行時間消耗資源。 關閉或最小化 HYPER-V 管理員可釋放這些資源。|  
  
## <a name="optimize-performance-of-disk-memory-network-and-processor-in-a-hyper-v-environment"></a>最佳化效能的磁碟、 記憶體、 網路及 HYPER-V 環境中的處理器  
 使用下列指導方針來最佳化效能的磁碟、 記憶體、 網路及 HYPER-V 的虛擬環境中的處理器。  
  
### <a name="optimize-processor-performance"></a>處理器效能最佳化  
 請遵循下列指導方針來最佳化的 HYPER-V 虛擬環境中執行的客體作業系統的處理器效能：  
  
-   **設定 1 到 1 的配置虛擬處理器給可用的邏輯處理器，為了達到最佳效能-**的最佳組態時執行 CPU 密集的應用程式，是 1-1 至客體作業系統中的虛擬處理器的比例主機作業系統可使用的邏輯處理器。 任何其他設定 2:1 或 1:2 例如沒有效率。 下圖說明在客體作業系統，到主機作業系統可使用的邏輯處理器的虛擬處理器核心的 1-1 配置：  
  
     ![一對一實體與虛擬處理器比率](../technical-guides/media/90f98f0d-a223-404c-b419-81369dc92970.gif "一對一實體與虛擬處理器比率")  
虛擬與邏輯處理器比例  
  
-   **請注意，不同的客體作業系統的虛擬處理器限制，並據此-規劃**HYPER-V 虛擬機器中執行的客體作業系統可用的處理器核心的數目可能會影響整體裝載的應用程式的效能。 因此，應考慮對於哪些客體作業系統將安裝在 HYPER-V 虛擬機器主機上[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]及/或[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]instance(s) 裝載[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]資料庫。 HYPER-V 可容納下列指定的客體作業系統的虛擬處理器的數目：  
  
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
  
### <a name="optimize-disk-performance"></a>最佳化磁碟效能  
 請遵循下列指導方針來最佳化磁碟效能的 HYPER-V 虛擬環境中執行的客體作業系統：  
  
|步驟|參考|  
|----------|---------------|  
|使用的虛擬磁碟包含 HYPER-V 虛擬機器設定使用固定大小的虛擬硬碟 (VHD) 選項。 固定大小的 VHD 提供的實體磁碟的功能，例如叢集支援，以及快照集磁碟支援彈性以及效能。|在 HYPER-V 環境中的磁碟儲存體是透過虛擬 IDE 控制器或虛擬 SCSI 控制器。 不同於舊版的 Microsoft 虛擬化技術，沒有任何存取虛擬硬碟時，使用虛擬 IDE 控制器或虛擬 SCSI 控制站之間的效能差異。 在 HYPER-V 環境中使用有下列的磁碟儲存體選項：<br /><br /> -   **固定大小磁碟-**大小固定虛擬硬碟 (VHD) 是其中一個資料區塊是根據在建立時定義的最大磁碟大小的實體磁碟上預先配置。 比方說，如果您建立一個 100 GB 的大小固定 VHD，HYPER-V 會配置所有 100 GB 的資料區塊儲存區，除了在建立新的 VHD 時，所需的 VHD 頁首和頁尾的額外負荷。<br />-   **動態擴充磁碟-**動態擴充的 VHD 是其中一個為其初始的虛擬硬碟包含任何資料區塊。 而是在資料寫入至 VHD，到建立 VHD 時所指定的大小上限，會以動態方式配置空間。 例如，100 GB 的動態擴充磁碟一開始包含只有 VHD 標頭，且需要不超過 2 MB 的實體儲存體空間。 新的資料寫入虛擬機器的動態擴充的 VHD 時，其他實體的資料區塊會配置 2 MB 增量的 VHD 檔案，最大值 100 gb。<br />-   **差異磁碟-**差異磁碟是一種特殊的動態擴充 「 父 」 VHD 相關聯的 VHD 檔案。 在這個父子式存放裝置拓撲中，父磁碟仍維持不變，「 子 」 差異磁碟只對所做的任何寫入作業。 任何讀取的作業會先檢查對差異磁碟，以查看更新的內容是否已寫入差異磁碟。如果內容不在差異磁碟，從父 VHD 讀取內容。 差異磁碟可用於需要維護的特定基準設定，而且想要輕鬆地進行測試，然後再復原變更基準的案例。 適用於測試的父子式存放裝置拓撲，透過差異磁碟提供彈性時，這不是效能最適合的設定，所以與維護的父子式拓撲相關聯的額外負荷需要： 當使用差異磁碟。<br />-   **傳遞磁碟 –**穿通磁碟功能可讓客體作業系統，略過 HYPER-V 主機檔案系統，並直接存取磁碟。 磁碟可供傳遞透過客體作業系統必須設定為 「 離線 」 狀態中 HYPER-V 主機，以確保主機和客體作業系統執行不會嘗試同時存取磁碟。 傳遞磁碟的確有提供邊際效能的優勢其他磁碟儲存體選項，但不支援虛擬磁碟，例如虛擬機器的快照集和叢集支援的特定功能。 因此穿通磁碟功能不是建議使用 BizTalk 或 SQL Server 環境中因為邊際效能優點是多個遺漏的功能，位移。<br /><br /> 多個磁碟儲存體選項，提供與 HYPER-V 的相對效能的詳細資訊，請參閱部落格文章: 「 HYPER-V 儲存體分析 」，網址[http://go.microsoft.com/fwlink/?LinkID=132848](http://go.microsoft.com/fwlink/?LinkID=132848)。|  
|設定為使用 SCSI 控制站的資料磁碟區的磁碟|這被建議因為如果而不需要安裝 HYPER-V 整合服務是使用模擬的 IDE 控制器，已安裝 HYPER-V 整合服務，可以只安裝 SCSI 控制器。 使用 integration services 提供 IDE 篩選器驅動程式執行磁碟 I/O 是明顯優於磁碟 I/O 效能所提供的模擬的 IDE 控制器。 因此，若要確保最佳的磁碟 I/O 效能中 HYPER-V 虛擬化環境中的資料檔案，在主機和客體作業系統上安裝 integration services 及設定資料磁碟區的磁碟與綜合 SCSI 控制器。 對於跨越多個資料磁碟機的極大量的儲存體 I/O 工作負載，每個 VHD 應該附加到另一個更佳的整體效能的綜合 SCSI 控制器。 此外，每個 VHD 應該儲存在個別的實體磁碟上。 **重要事項：**不將系統磁碟連接到 SCSI 控制器。 包含作業系統的虛擬硬碟必須連接到 IDE 控制器。|  
  
### <a name="optimize-memory-performance"></a>記憶體效能最佳化  
 請遵循下列指導方針來最佳化記憶體的 HYPER-V 虛擬環境中執行的客體作業系統的效能：  
  
|步驟|參考|  
|----------|---------------|  
|請確認有足夠的記憶體裝載 HYPER-V 虛擬機器的實體電腦上安裝|提供的實體記憶體通常是最重要的效能因素，如[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]HYPER-V 虛擬機器上執行。 這是因為每個虛擬機器必須位在非-分頁集區記憶體或無法分頁至磁碟的記憶體。 因為非-分頁集區記憶體無法分頁至磁碟時，裝載虛擬機器的實體電腦應該有可用的實體記憶體的記憶體總和等於配置給每個虛擬機器以及下列所述：<br />     300 MB 的 Hypervisor，加上 32 MB 的第一個 GB 的 RAM 配置給每個虛擬機器加上另一個 8 MB 的每個其他 GB 的 RAM 配置給每個虛擬機器加上主機的 512 MB在根磁碟分割上執行的作業系統<br />     例如，如果 HYPER-V 虛擬機器會配置 2 GB 的記憶體在 HYPER-V 管理員中，當執行這個 HYPER-V 虛擬機器可能會大約 2388 MB 時所使用的實際實體記憶體 (300 MB 的 hypervisor 的虛擬機器配置 + 2 GB +32 MB + 8 MB = 2388 MB)。 Hypervisor 只必須載入一次，因為初始設定後續的虛擬機器不會造成載入 hypervisor 與相關聯的 300 MB 額外負荷。 因此，如果兩個 HYPER-V 虛擬機器配置 2 記憶體每 GB 的 [HYPER-V 管理員] 中，執行這些 HYPER-V 虛擬機器時所使用的實際實體記憶體會大約 4476 MB （300 MB 的 hypervisor + 4 GB 配置給虛擬機器 + 64 MB + 16 MB = 4476 MB)。 **注意：**為一般的經驗法則，計劃配置至少 512 MB 的記憶體，以提供服務，例如 I/O 虛擬化、 快照集檔案支援和子資料分割管理根磁碟分割。<br />-   **使用 64 位元的客體作業系統盡可能**– 請考慮使用針對每個客體作業系統的 64 位元作業系統。 這應該會完成，因為根據預設，32 位元 Windows 作業系統可以只處理 2 GB 的每個處理序虛擬位址空間。 64 位元作業系統的安裝可讓應用程式利用完整裝載 HYPER-V 虛擬機器的實體電腦上安裝的記憶體。|  
  
### <a name="optimize-network-performance"></a>將網路效能最佳化  
 HYPER-V 虛擬機器中支援的綜合和模擬網路介面卡，但綜合裝置提供大幅提升效能並減少 CPU 額外負荷。 每張介面卡會連接至虛擬網路交換器，如果需要外部網路連線可以連接至實體網路介面卡。 遵循本節中的建議，以最佳化網路效能的 HYPER-V 虛擬環境中執行的客體作業系統。  
  
> [!NOTE]
>  這些建議都是從 「 效能調整指導方針的 Windows Server 2008 R2 」 白皮書下載的 「 效能調整的虛擬化伺服器 」 一節[http://go.microsoft.com/fwlink/?LinkID=202087](http://go.microsoft.com/fwlink/?LinkID=202087)。 如需瞭解如何微調根磁碟分割，包括插斷仲裁中的網路介面卡，請參閱本指南的 「 效能調整的網路子系統 」 一節。 應套用 TCP tunings，在該區段中，如果所需的子資料分割。  
  
|步驟|參考|  
|----------|---------------|  
|設定要使用私人虛擬網路相同的 HYPER-V 主機電腦執行的 HYPER-V 虛擬機器|請遵循 「 設定相同的 HYPER-V 上執行的 HYPER-V 虛擬機器主機使用的私人虛擬網路的電腦 」 一節中的建議[網路最佳化](~/technical-guides/network-optimizations.md)。|  
|停用 TCP 卸載，以將虛擬機器網路卡|請遵循 「 停用 TCP 卸載的虛擬機器網路卡數 」 一節中的建議[網路最佳化](~/technical-guides/network-optimizations.md)。|  
|設定為使用 HYPER-V 綜合網路介面卡的客體作業系統。|綜合網路介面卡，特別針對 Vm 來達成大幅降低 CPU 額外負荷的 HYPER-V 功能網路 I/O 的比較來模擬的網路介面卡，以模擬現有硬體時。 綜合網路介面卡會透過使用共用的記憶體更有效率的資料傳輸 VMBus 子系和根資料分割之間進行通訊。 <br />模擬的網路介面卡應該透過 VM 的 [設定] 對話方塊來移除並取代的綜合網路介面卡。 客體會需要安裝 VM 整合服務。|  
|如果有的話，啟用卸載功能的根磁碟分割的實體網路介面卡驅動程式。|因為原生的案例中，以卸載實體網路介面卡中的功能，減少 CPU 使用量 VM 案例中的網路 I/o。 HYPER-V 目前使用 LSOv1 TCPv4 總和檢查碼卸載和。 在根磁碟分割中的實體網路介面卡的驅動程式，必須啟用卸載功能。 如需中網路介面卡卸載功能的詳細資訊，請參閱適用於 「 效能調整指導方針的 Windows Server 2008 R2"技術白皮書的 「 效能調整的虛擬化伺服器 」 一節的 「 選擇網路介面卡 」 一節從下列網址下載[http://go.microsoft.com/fwlink/?LinkID=202087](http://go.microsoft.com/fwlink/?LinkID=202087)。<br />驅動程式特定網路介面卡停用 LSOv1，但依預設會啟用 LSOv2。 系統管理員必須明確使用驅動程式啟用 LSOv1**屬性**對話方塊的 [裝置管理員] 中。|  
|設定網路交換器拓撲，讓使用多個網路介面卡。|HYPER-V 支援建立多個虛擬網路交換器，其中每個可附加至實體網路介面卡有需要。 在 VM 中的每個網路介面卡可以連接至虛擬網路交換器。 如果實體伺服器有多張網路介面卡，Vm 網路需要大量載入可以發揮不必連接至不同的虛擬交換器，更有效地使用實體網路介面卡。|  
|如果安裝多張實體網路卡的 HYPER-V 主機電腦上，在一個邏輯處理器每張網路卡的繫結裝置中斷。|在某些工作負載，繫結至一個邏輯處理器的單一網路介面卡的裝置中斷可以改進效能 HYPER-V。 我們建議此進階微調，只以解決特定問題的完整使用網路頻寬。 系統管理員可以使用 IntPolicy 工具，將繫結至特定處理器的裝置插斷。 如需 IntPolicy 工具的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkID=129773](http://go.microsoft.com/fwlink/?LinkID=129773)。|  
|可能的話，請啟用 VLAN 標記 HYPER-V 綜合網路介面卡。|HYPER-V 的綜合網路介面卡支援 VLAN 標記。 如果實體網路介面卡支援的 NDIS_ENCAPSULATION_IEEE_802_3_P_AND_Q_IN_OOB 封裝大型傳送與總和檢查碼卸載，它可以提供大幅提升網路效能。 如果沒有這項支援，HYPER-V 需要 VLAN 標記的封包不能使用硬體卸載，可以減少網路效能。|  
|在 HYPER-V 主機電腦上安裝適當的高速網路介面卡，並設定最大效能。|請考慮安裝在 HYPER-V 主機電腦上的 1 GB 網路介面卡，並使用固定的速度，而不是使用 「 自動交涉 」 設定的網路介面卡-它是非常重要的網路速度、 雙工和流程控制參數設定為對應交換器上設定它們所連接。|  
|請遵循網路效能最佳化最佳的作法。|本主題[網路最佳化](~/technical-guides/network-optimizations.md)提供網路效能最佳化的一般指導方針。 雖然本主題不提供的效能最佳化的特定建議[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 HYPER-V 虛擬化環境中，則適用於任何技術[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案中，是否在實體硬體上，或在 HYPER-V 上執行虛擬化的環境。|  
  
## <a name="optimize-sql-server-performance"></a>最佳化 SQL Server 效能  
 請依照下列主題中的建議[SQL Server 最佳化](~/technical-guides/sql-server-optimizations.md)至 BizTalk Server 解決方案的 SQL Server 效能最佳化。 雖然本主題不提供的效能最佳化的特定建議[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 HYPER-V 虛擬化環境中，則適用於任何技術[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案中，是否在實體硬體上，或在 HYPER-V 上執行虛擬化的環境。  
  
## <a name="optimize-biztalk-server-solution"></a>最佳化 BizTalk Server 解決方案  
 請依照下列主題中的建議[BizTalk Server 最佳化](~/technical-guides/biztalk-server-optimizations.md)最佳化 BizTalk Server 解決方案的效能。 雖然本主題不提供的效能最佳化的特定建議[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 HYPER-V 虛擬化環境中，則適用於任何技術[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案中，是否在實體硬體上，或在 HYPER-V 上執行虛擬化的環境。