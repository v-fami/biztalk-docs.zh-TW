---
title: 凍結預設屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 68c59def-d73b-4880-9884-ccbe5d982f4b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 907bd9f9b47db10a199f5a93a828558dfb3ae210
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981959"
---
# <a name="dehydration-default-properties"></a>凍結預設屬性
以下是凍結屬性名稱及其預設值。 這些屬性可在 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 中設定，也可在 BTSNTSvc.exe.config 檔 (BTSNTSvc.exe.config 或 BTSNTSvc64.exe.config) 中設定為 XML。 BizTalk 組態檔中的值將先套用。 然後 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 設定才會套用。 所有包含協調流程的主控件執行個體啟動時，將讀取凍結屬性。  
  
> [!IMPORTANT]
>  [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]並未完全顯示所有的協調流程設定。 對於這些設定，將使用 BizTalk 組態檔 (BTSNTSvc.exe.config 或 BTSNTSvc64.exe.config)。 使用 BizTalk 組態檔時，許多屬性並未列出。 即使組態檔未明確指定這些屬性及其預設值，仍將套用這些屬性及其預設值。  
  
 若要變更預設值，可以使用 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 或將預設值明確新增至 BizTalk 組態檔。 如需詳細資訊，請參閱 <<c0> [ 使用設定儀表板進行 BizTalk Server 效能調整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)並[BTSNTSvc.exe.config 檔案](../core/btsntsvc-exe-config-file.md)。  
  
 **凍結**  
  
- **MaxThreshold** = 1800年  
  
- **MinThreshold** = 1  
  
- **ConstantThreshold** =-1  
  
  **VirtualMemoryThrottlingCriteria**  
  
- **OptimalUsage** = 900  
  
- **MaximalUsage** = 1300年  
  
- **IsActive** = true  
  
  **PrivateMemoryThrottlingCriteria**  
  
- **OptimalUsage** = 50  
  
- **MaximalUsage** = 350  
  
- **IsActive** = true  
  
  **PhysicalMemoryThrottlingCriteria**  
  
- **OptimalUsage** = 90  
  
- **MaximalUsage**類別 = 95  
  
- **IsActive** = false  
  
  下文將詳細地描述每一個屬性。  
  
## <a name="dehydration"></a>Dehydration  
 **MaxThreshold**並**MinThreshold**是右上角，而範圍中，秒數的協調流程可能會封鎖在訂用帳戶 （也就，封鎖接收、 偵聽或延遲） 被凍結之前的時間。 也會有值，計算在執行階段，稱為**TestThreshold**，且其值，以秒為單位測量之間**MinThreshold**並**MaxThreshold**。  
  
 如果您的設定值，預設值為-1 以外**ConstantThreshold**，則將不會有執行階段值**TestThreshold**。 當協調流程會封鎖在訂用帳戶，並多久該協調流程的所有執行個體已被封鎖在該訂用帳戶的歷程記錄的值大於**TestThreshold**，然後將協調流程凍結。 否則，如果記錄是小於**TestThreshold**就不會凍結協調流程的值。 此外，即使歷程記錄指出凍結不會進行，如果目前的封鎖時間達到 2<em>**TestThreshold</em>*，則會發生凍結。 歷程記錄是根據最後 10 次等候時間的平均 (以秒為單位)，或記錄中許多等候時間 (不到 10 次的等候時間) 的平均而定義。  
  
 當 windows 7 **TestThreshold**傾向**MinThreshold**隨著記憶體使用量增加，它會呼叫 「 記憶體基礎的凍結節流 」。 以記憶體為基礎的凍結節流允許啟動更多協調流程執行個體，因為當其中任何執行個體受阻並等待工作 (也就是說，等待訊息或延遲) 時，它們會遭凍結並從記憶體中移除。 **TestThreshold**是單純遞減的函式的記憶體使用量是記憶體使用量成反比。  
  
 以下是個別 Dehydration 屬性的說明：  
  
-   **MaxThreshold**： 上限，以秒為單位的時間，協調流程可能會封鎖在被凍結之前的訂用帳戶。  
  
-   **MinThreshold**： 下限，以秒為單位的時間，協調流程可能會封鎖在被凍結之前的訂用帳戶。  
  
-   **ConstantThreshold**： 通常指定的最小和最大值之間波動的動態臨界值。 不過，您可以設定這個屬性，將閾值固定。 值 -1 會告知引擎不要使用常數閾值。 請勿將這個屬性設為 -1 以外的值，因為這會停用以凍結為基礎的節流。  
  
## <a name="virtualmemorythrottlingcriteria"></a>VirtualMemoryThrottlingCriteria  
 目前在 32 位元電腦上，由於 Unmanaged 堆積分割，虛擬記憶體可能成為瓶頸，所以您也應該依據這項資源進行節流。 如果已設定 /3GB，或在 64 位元平台上執行主控件，您應該重新設定這個屬性。 最佳和最大使用量都是以 MB 為單位。  
  
 以下是個別 VirtualMemoryThrottlingCriteria 屬性的說明：  
  
-   **OptimalUsage**： 的凍結節流開始生效的虛擬記憶體使用量。 在此時**TestThreshold**具有值**MaxThreshold**和任何的記憶體使用量大於**OptimalUsage**會導致**TestThreshold**為小於**MaxThreshold**。  
  
-   **MaximalUsage**： 的凍結節流時最多的虛擬記憶體使用量。 在此時**TestThreshold**具有值**MinThreshold**和任何的記憶體使用量小於**MaximalUsage**會導致**TestThreshold**必須大於**MinThreshold**。  
  
-   **IsActive**： 布林值，指出虛擬記憶體節流是否為作用。  
  
## <a name="privatememorythrottlingcriteria"></a>PrivateMemoryThrottlingCriteria  
 這個屬性是節流的實用準則，但根據電腦是否正在執行其他 Windows 服務，適用值會不同。 如果電腦有許多記憶體，而且不與其他 Windows 服務共用，您就可以大幅增加這些值。  
  
 以下是個別 PrivateMemoryThrottlingCriteria 屬性的說明：  
  
-   **OptimalUsage**： 的私用記憶體使用量，以 mb 為單位，凍結節流開始生效。 此時**TestThreshold**具有值**MaxThreshold**和任何的記憶體使用量大於**OptimalUsage**造成**TestThreshold**為小於**MaxThreshold**。  
  
-   **MaximalUsage**： 的私用記憶體使用量，以 mb 為單位，凍結節流是最大值。 此時**TestThreshold**具有值**MinThreshold**和任何的記憶體使用量小於**MaximalUsage**造成**TestThreshold**必須大於**MinThreshold**。  
  
-   **IsActive**： 布林值，指出私用記憶體節流是否為作用。  
  
## <a name="physicalmemorythrottlingcriteria"></a>PhysicalMemoryThrottlingCriteria  
 除此之外，也有實體記憶體節流，其數字是以使用的記憶體百分比為單位，而不以 MB 為單位。 預設不會啟用這個屬性，但在必要時您可以啟用它。  
  
 以下是個別 PhysicalMemoryThrottlingCriteria 屬性的說明：  
  
-   **OptimalUsage**： 使用於主控件執行個體的實體記憶體最佳百分比。  
  
-   **MaximalUsage**： 使用於主控件執行個體的實體記憶體的最大百分比。  
  
-   **IsActive**： 布林值，指出實體記憶體節流是否為作用。  
  
## <a name="dehydration-properties-behavior"></a>凍結屬性行為  
 BizTalk Server 會使用這些凍結屬性，決定何時凍結和解除凍結協調流程。 在正常負載下，預設的凍結值就足夠，但在負載過重時，若要變更效能特性，您應該自行微調。  
  
 BizTalk Server 的凍結行為主要取決於可用和使用中的記憶體數量。 根據不同的記憶體數量，以及 32 位元和 64 位元主控件之間的記憶體使用差異，凍結行為會不同。  
  
 凍結屬性會區分協調流程主控件的「私用位元組」和「虛擬位元組」：  
  
-   **虛擬位元組**。 這是其中將填入目前的大小，以位元組為單位的處理序正在使用的虛擬位址空間。 虛擬位址空間的使用不一定表示磁碟或主記憶體頁面的對應使用。 虛擬空間是有限的，而且程序可以限制其載入程式庫的能力。  
  
-   **私用位元組**。 這是目前配置給程序、不能與其他程序共用的記憶體大小 (以位元組為單位)。