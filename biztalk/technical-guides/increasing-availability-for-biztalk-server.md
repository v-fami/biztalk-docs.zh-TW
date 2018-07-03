---
title: 增加 BizTalk Server 的可用性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72d9ce5e-d775-4f8e-b1a4-bf3c7c05f571
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6de74c7efb9aa4f900d555c265318bb17118082
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023700"
---
# <a name="increasing-availability-for-biztalk-server"></a>增加 BizTalk Server 的可用性
本節說明您可以增加的可用性方式您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。  
  
## <a name="strategies-for-increasing-availability"></a>增加可用性策略  
 提高可用性的策略包含下列各項：  
  
- **提供使用 Windows Server 2003 伺服器叢集或 Windows Server 2008 容錯移轉叢集的高可用性**。 伺服器/容錯移轉叢集是一組的獨立電腦系統，稱為 做為單一系統，以確保重要應用程式和資源提供給用戶端一起運作的節點。 如果某個節點因為故障或維護停機時間的需求而無法使用，另一個節點便會立即開始提供服務 （稱為容錯移轉的程序）。  
  
  - 執行 SQL Server 裝載的電腦通常建議使用的伺服器/容錯移轉叢集[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
  - 伺服器叢集可能需要以特定的 BizTalk 配接器提供高可用性。  
  
  - 伺服器叢集通常建議針對企業單一登入主要密碼伺服器。  
  
- **提供使用一種負載平衡的高可用性**。  
  
  - 網路負載平衡 (NLB)。 NLB 會藉由將傳入網路流量重新導向至使用 NLB 叢集主機，如果主機失敗或離線提供高可用性。 不同於伺服器叢集，NLB 不需要特殊硬體。  
  
  - BizTalk 主控件負載平衡。 BizTalk 主控件負載平衡會加上執行的多部伺服器為 BizTalk 主控件提供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組，然後設定 多個這些伺服器上執行內含式主控件執行個體。 這樣可將該主控件中所設定的服務和成品執行作業分散於該主控件的多個執行個體，以提高可用性和擴充性。  
  
    > [!NOTE]  
    >  內含式主控件只使用主應用程式的負載平衡功能。  
  
  - 透過使用 SAN，或藉由新增多個 MessageBox 資料庫的 SQL Server 磁碟提供負載平衡。  
  
- 提供的策略**提高可用性**。 這些策略提供增加的可用性，但通常也需要 系統管理員身分執行在執行階段的一或多個動作。 因此這些策略是通常被認為是提供更高的可用性，而不是高可用性：  
  
  - 增加可用性使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送和災害復原。  
  
  - 提高可用性透過適當的監視和維護策略的實作。  
  
## <a name="difference-between-clustering-and-disaster-recovery"></a>叢集之間的差異和災害復原  
 雖然叢集和嚴重損壞修復增加可用性，它們之間的主要差異是，叢集通常會提供更快速的復原時間比災害復原。 因此在伺服器/容錯移轉叢集上建置的解決方案或負載平衡常被認為是提供高可用性，而不是只提供可用性。  
  
 災害復原可讓您繼續作業失敗的系統，但通常是手動程序，而且需要更多的復原時間，比高可用性的實作。 因此，災害復原實作所提供的可用性，但未針對高可用性。 您應該採用透過 server/容錯移轉叢集和負載平衡、 高可用性和災害復原，在生產環境中透過[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [提供高可用性](../technical-guides/providing-high-availability.md)  
  
-   [災害復原](../technical-guides/disaster-recovery.md)  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 提供高可用性與容錯或負載平衡](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)   
 [檢查清單：利用災害復原功能提高可用性](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)