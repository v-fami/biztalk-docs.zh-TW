---
title: "增加可用性，以便讓 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72d9ce5e-d775-4f8e-b1a4-bf3c7c05f571
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa48d7dada00ebadf089834f5025f3fdfdf25070
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="increasing-availability-for-biztalk-server"></a>增加可用性，以便讓 BizTalk Server
本節說明您可以提高可用性的方法您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。  
  
## <a name="strategies-for-increasing-availability"></a>增加可用性策略  
 增加可用性策略包括下列各項：  
  
-   **提供使用 Windows Server 2003 伺服器叢集或 Windows Server 2008 容錯移轉叢集的高可用性**。 伺服器/容錯移轉叢集是一組獨立電腦系統，稱為節點，做為單一系統可確保重要應用程式和資源中的用戶端能夠一起運作。 如果其中一個節點變成因為失敗或維護停機時間的需求而無法使用，另一個節點便會立即開始提供服務 （稱為容錯移轉的程序）。  
  
    -   伺服器/容錯移轉叢集通常建議使用該所執行 SQL Server 的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
    -   伺服器叢集中可能需要以特定 BizTalk 配接器提供高可用性。  
  
    -   伺服器叢集中，通常建議的企業單一登入主要密碼伺服器。  
  
-   **提供使用一種負載平衡的高可用性**。  
  
    -   網路負載平衡 (NLB)。 NLB 會將連入網路流量重新導向至使用 NLB 叢集主機，若主機失效或離線，以提供高可用性。 不同於伺服器叢集，NLB 不需要特殊硬體。  
  
    -   BizTalk 主控件的負載平衡。 BizTalk 主控件負載平衡新增多個伺服器執行的 BizTalk 主控件提供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中，然後設定這些伺服器上執行內含式主控件的多個執行個體。 這樣可將該主控件中所設定的服務和成品執行作業分散於該主控件的多個執行個體，以提高可用性和擴充性。  
  
        > [!NOTE]  
        >  內含式主控件只可使用主應用程式的負載平衡功能。  
  
    -   透過使用 SAN，或加入多個 MessageBox 資料庫的 SQL Server 磁碟提供負載平衡。  
  
-   提供的策略**提高可用性**。 這些策略提供增加的可用性，但通常也需要 系統管理員身分執行在執行階段的一個或多個動作。 因此這些策略是通常視為提供提高的可用性，而不是高可用性：  
  
    -   增加可用性使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送和災害復原。  
  
    -   增加可用性，透過實作適當的監視和維護策略。  
  
## <a name="difference-between-clustering-and-disaster-recovery"></a>叢集之間的差異和災害復原  
 叢集和災害復原增加可用性，而它們之間的主要差異是叢集通常提供更快速的復原時間比災害復原。 因此在伺服器/容錯移轉叢集上建置方案或負載平衡通常視為提供高可用性而非只提供可用性。  
  
 災害復原可讓您繼續作業失敗的系統，但通常是手動程序也需要更多的復原時間，比的高可用性的實作。 因此，災害復原實作所提供的可用性，但不是高可用性。 您應該採用透過伺服器/容錯移轉叢集和負載平衡，高可用性和災害復原，在生產環境中透過可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [提供高可用性](../technical-guides/providing-high-availability.md)  
  
-   [嚴重損壞修復](../technical-guides/disaster-recovery.md)  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 提供高可用性與容錯或負載平衡](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)   
 [檢查清單： 提高可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)