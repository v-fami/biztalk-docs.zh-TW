---
title: 規劃高可用性和災害復原 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7efba36-6d9c-4ae0-a4f5-893eb5d62a05
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 742073de6f0e992e5fd0155b1939f0680fa7b3bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-high-availability-and-disaster-recovery"></a>規劃高可用性和災害復原
方案開發的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]通常在很重要的企業級應用程式需要最大的可用性。 當這些解決方案會放入生產環境中時，停機時間與相關聯的成本可能被以每秒千美元。 基於這個理由，您應該採用特定的策略來最大化的高可用性和災害復原功能，適用於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相依性的軟體和硬體才能支援[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案。  
  
## <a name="hardware-considerations"></a>硬體考量  
 若要確保高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，為硬體規劃時，請考慮下列：  
  
-   計劃在 BizTalk 群組，以容納所有 BizTalk 伺服器群組中執行多個 BizTalk 主控件執行個體中執行多個 （兩個以上） 的 BizTalk 伺服器。 這可容納在主控件執行個體中執行處理序的負載平衡和容錯的功能。  
  
-   請考慮實作存放區域網路 (SAN) 來保存[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 SAN 的磁碟應設定使用 RAID 1 + 0 （等量磁碟區鏡像組） 拓撲盡可能以最大效能和高可用性。 如需有關使用 SAN 來保存[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[BizTalk Server 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/?LinkID=101578)(http://go.microsoft.com/fwlink/?LinkID=101578)。  
  
-   計劃上安裝多部 SQL server，以容納[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 多部 SQL server 所需的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集 （建議選項） 和/或某些罩[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]個別的實體上的資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]（也建議使用） 的執行個體。  
  
-   請考慮使用虛擬環境控制硬體成本。 Microsoft 提供的虛擬化產品，例如 Microsoft Virtual Server 2005 R2、 Windows Server 2008 HYPER-V 和 Microsoft HYPER-V Server 2008 的範圍。 如需有關使用建議[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在虛擬環境中，請參閱[BizTalk Server 2009 HYPER-V 指南](http://go.microsoft.com/fwlink/?LinkId=151834)(http://go.microsoft.com/fwlink/?LinkId=151834)。  
  
-   一或多個 Windows 伺服器的網域中安裝周邊網路提供網際網路相關服務，為您的組織計劃。 設定多個 Windows 伺服器網域中的周邊網路使用網路負載平衡 (NLB) 解決方案。 如需詳細資訊，請參閱[網路負載平衡部署指南](http://go.microsoft.com/fwlink/?LinkId=153139)(http://go.microsoft.com/fwlink/?LinkId=153139)。  
  
     如需在周邊網路中安裝伺服器的詳細資訊，請參閱[設定您網域時公開傳輸到網際網路](../technical-guides/planning-for-sending-and-receiving.md#BKMK_InternetTrans)。  
  
    > [!NOTE]  
    >  周邊網路。 也稱為 DMZ 和遮蔽式子網路  
  
## <a name="software-considerations"></a>軟體考量  
 若要確保高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，規劃軟體時，請考慮下列：  
  
-   請考慮在 Enterprise 版本中的投資[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，而獲益的 BizTalk 主控件叢集或可從執行多個 MessageBox 資料庫，獲益的案例。 一般而言，您應該叢集化 BizTalk 主控件的唯一理由是某些 BizTalk 配接器提供高可用性。 如需使用主機叢集的 BizTalk 配接器提供高可用性的詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](http://go.microsoft.com/fwlink/?LinkID=151284)(http://go.microsoft.com/fwlink/?LinkID=151284)。  
  
-   實作 Windows Server 叢集所計劃[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫 」 和 「 企業單一登入主要密碼伺服器。 如需有關使用 Windows Server 叢集提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫 」 和 「 企業單一登入主要密碼伺服器，請參閱[資料庫的高可用性](../technical-guides/high-availability-for-databases.md)和[主要密碼伺服器的高可用性](../technical-guides/high-availability-for-the-master-secret-server.md)。  
  
## <a name="high-availability-vs-disaster-recovery"></a>高可用性與災害復原  
 有兩種規定的方法，增加可用性，如[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境： 提供容錯和/或負載平衡，或提供提高的可用性使用災害復原使用的高可用性。 由於每個方法會增加可用性，它們之間的主要差異是該容錯和/或負載平衡通常會提供比嚴重損壞修復的更快速的復原時間。 提供容錯和/或負載平衡**高可用性**提供災害復原而**提高可用性**。 如需實作災害復原的詳細資訊，請參閱[檢查清單： 提高可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)和[嚴重損壞修復](../technical-guides/disaster-recovery.md)。  
  
## <a name="see-also"></a>另請參閱  
 [增加可用性，以便讓 BizTalk Server](../technical-guides/increasing-availability-for-biztalk-server.md)   
 [檢查清單： 提供高可用性與容錯或負載平衡](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)