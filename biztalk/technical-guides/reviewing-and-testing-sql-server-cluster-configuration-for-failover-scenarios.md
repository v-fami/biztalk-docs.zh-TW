---
title: 檢閱及測試 SQL Server 叢集的容錯移轉案例的設定 |Microsoft 文件
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
ms.openlocfilehash: d8e7bed17960700aee84631801e3e26cb05b25c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302214"
---
# <a name="reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios"></a>檢閱及測試 SQL Server 叢集組態的容錯移轉案例
Windows 叢集和 SQL Server 可讓您執行 SQL Server 以主動/主動模式叢集的每個節點其中是 「 作用中 」 且正在執行一個以上的 SQL Server 執行個體。 這樣可讓您，比方說，有一個節點和所有其他 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]另一個節點上的資料庫。 這可讓您以最大化叢集硬體的使用方式。  
  
 如果您使用此設定，不過，您就必須確認每個節點，可以同時處理的所有 SQL Server 執行個體載入 SQL Server 叢集節點容錯移轉期間。  
  
## <a name="evaluating-failover-for-an-activeactive-cluster"></a>評估為主動/主動叢集容錯移轉  
 驗證單一節點可以處理的所有 SQL Server 執行個體發生 SQL Server 叢集節點容錯移轉的負載時的考量事項包括：  
  
-   容錯移轉節點是否有足夠的 CPU 資源？  
  
-   容錯移轉節點是否有足夠的記憶體？  
  
-   是否有足夠的網路頻寬？  
  
-   容錯移轉節點可以處理更大的磁碟 I/O 競爭嗎？  
  
 測試容錯移轉時，應該評估下列案例：  
  
-   使用中的伺服器上的電源故障  
  
-   被動伺服器上的電源故障  
  
-   遺失磁碟的連線  
  
-   中斷作用中節點上的公用網路連線  
  
-   在使用中節點上中斷私人網路連線  
  
-   在被動節點上中斷公用網路連線  
  
-   在被動節點上中斷私人網路連線  
  
-   失敗的 SQL Server 服務  
  
-   失敗的 SQL Server Agent 服務  
  
## <a name="using-an-activeactivepassive-cluster"></a>使用主動/主動/被動叢集  
 如果您判斷有一個節點無法處理在容錯移轉案例中的所有 SQL Server 執行個體，另一個方法是使用主動/主動/被動叢集模型。 主動/主動/被動叢集模型可大幅增加，永遠都會有一個被動節點可供容錯移轉案例的可能性。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 設定 SQL Server](~/technical-guides/checklist-configuring-sql-server.md)