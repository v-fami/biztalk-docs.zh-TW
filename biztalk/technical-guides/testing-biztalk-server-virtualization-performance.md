---
title: "測試 BizTalk Server 的虛擬化效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d09121b1-cdd6-4c01-9d69-0f1923464f0e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cec992ab489c63f68ac4d77652209e65eff258a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="testing-biztalk-server-virtualization-performance"></a>測試 BizTalk 伺服器虛擬化的效能
本指南中所述的效能測試案例中每個已部署在 Microsoft 測試實驗室中，實體電腦上，然後在每個不同的系統架構上執行相同的負載測試。 主機上的作業系統每一部實體電腦已完整安裝[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]Enterprise，64 位元版本，安裝 HYPER-V 伺服器角色。 用於測試的虛擬機器[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]設定的[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]Enterprise，做為客體作業系統的 64 位元版本。 用於測試的虛擬機器[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]使用設定[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]Enterprise，做為客體作業系統的 64 位元版本。 用來編寫一系列的最佳做法和指南設計、 實作、 測試案例、 測試方法、 效能測試結果及後續的分析和最佳化虛擬化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
-   **測試案例 1： 基準**– 第一個案例設計用來建立基準效能的 BizTalk Server 環境中只使用實體硬體上執行。 此案例中 BizTalk Server 和 SQL Server 所安裝，並只使用實體硬體上執行。  
  
-   **測試案例 2： 虛擬 BizTalk/實體伺服器的 SQL Server** -第二個案例設計用來判斷多個相同的實體伺服器上的客體虛擬機器上裝載 BizTalk Server 的效能影響。 從多個組態已總數相同的邏輯處理器數目然後比較處理實體機器的虛擬機器的測試結果散佈在所有虛擬機器。  
  
-   **測試案例 3： 虛擬 BizTalk/虛擬伺服器上的 SQL Server 個別實體的 HYPER-V 主機**-執行第三種案例以判斷虛擬化環境中執行 BizTalk Server 和 SQL Server 的效能影響。 用於執行測試，使用與 BizTalk 資料庫裝載於 HYPER-V 虛擬機器上執行的 BizTalk Server [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] HYPER-V 虛擬機器上執行的執行個體。 此案例中，BizTalk Server 虛擬機器和 SQL Server 虛擬機器上裝載不同實體的 HYPER-V 主機。  
  
-   **測試案例 4： 伺服器彙總-合併完整 BizTalk 群組包括 SQL HYPER-V 上的一部實體伺服器到**– 一部實體伺服器上裝載案例中，執行測試應用程式所需所有虛擬機器 (Vm)。 此案例的目的是要判斷主機的效能成本[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]和[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]合併環境中虛擬機器。  
  
 本節提供測試應用程式和伺服器架構會使用每個案例的概觀，並且也會提供在測試期間觀察到的關鍵效能指標 (Kpi)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [測試案例概觀](../technical-guides/test-scenario-overview.md)  
  
-   [測試案例伺服器架構](../technical-guides/test-scenario-server-architecture.md)  
  
-   [測試結果： BizTalk Server 關鍵效能指標](../technical-guides/test-results-biztalk-server-key-performance-indicators.md)  
  
-   [測試結果： SQL Server 的關鍵效能指標](../technical-guides/test-results-sql-server-key-performance-indicators.md)  
  
-   [測試結果： 網路功能關鍵效能指標](../technical-guides/test-results-networking-key-performance-indicators.md)  
  
-   [測試結果： 記憶體關鍵效能指標](../technical-guides/test-results-memory-key-performance-indicators.md)  
  
-   [測試結果摘要](../technical-guides/summary-of-test-results.md)