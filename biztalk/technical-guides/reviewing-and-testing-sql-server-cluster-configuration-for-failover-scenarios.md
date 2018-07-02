---
title: 檢閱及測試 SQL Server 叢集的容錯移轉案例的組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dbeb383-5b38-4467-acf8-2a5b244e5fa9
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 981a879a5dad68bfb423a03b82e11fb646f912c1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973255"
---
# <a name="reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios"></a>檢閱和測試容錯移轉案例的 SQL Server 叢集組態
Windows 叢集和 SQL Server 可讓您執行 SQL Server 以主動/主動模式叢集的每個節點的 「 作用中 」 且正在執行一個以上的 SQL Server 執行個體。 這可讓您，比方說，有一個節點和所有其他 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]另一個節點上的資料庫。 這可讓您將叢集的硬體使用量最大化。  
  
 如果您使用此設定，不過，您就必須確認每個節點，可以同時處理所有的 SQL Server 執行個體的負載在 SQL Server 叢集節點容錯移轉。  
  
## <a name="evaluating-failover-for-an-activeactive-cluster"></a>評估為主動/主動叢集的容錯移轉  
 驗證單一節點可以處理 SQL Server 叢集節點容錯移轉時，所有 SQL Server 執行個體的負載時的考量事項包括：  
  
- 容錯移轉節點是否有足夠的 CPU 資源？  
  
- 容錯移轉節點是否有足夠的記憶體？  
  
- 是否有足夠的網路頻寬？  
  
- 容錯移轉節點可以處理更大的磁碟 I/O 競爭？  
  
  測試容錯移轉時，應進行評估的下列案例：  
  
- 在 作用中的伺服器上的電源故障  
  
- 在被動的伺服器上的電源故障  
  
- 磁碟連線中斷  
  
- 中斷作用中節點上的公用網路連線  
  
- 中斷作用中節點上的私人網路連線  
  
- 中斷在被動節點上的公用網路連線  
  
- 中斷在被動節點上的私人網路連線  
  
- 失敗的 SQL Server 服務  
  
- 失敗的 SQL Server Agent 服務  
  
## <a name="using-an-activeactivepassive-cluster"></a>使用主動/主動/被動叢集  
 如果您判斷一個節點無法處理所有的 SQL Server 執行個體在容錯移轉的案例中，替代方法是使用主動/主動/被動叢集模型。 主動/主動/被動叢集模型會大幅增加，必定都有一個被動節點可供容錯移轉案例的可能性。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單：設定 SQL Server](~/technical-guides/checklist-configuring-sql-server.md)