---
title: "測試結果的摘要 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d95fbaa6-0e07-4086-bea2-0577d39ae7cd
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2eebcdef457716cab9ad61415bf3fe46db301b55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="summary-of-test-results"></a>測試結果摘要
本主題摘要說明測試案例的結果。  
  
## <a name="summary-of-test-results"></a>測試結果摘要  
 [測試 BizTalk 伺服器虛擬化效能](../technical-guides/testing-biztalk-server-virtualization-performance.md)本指南中的章節說明使用的測試應用程式和設定的各種[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境執行測試應用程式。 要比較的效能測試已執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  /  [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]實體硬體上執行的 HYPER-V 虛擬機器上執行的環境效能的環境。 在測試期間測量關鍵效能指標 (Kpi) 包含下列工作;  
  
1.  訊息輸送量測量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。  
  
2.  在 Visual Studio 測試用戶端提交同步要求，以測量要求-回應延遲[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
3.  處理器使用率及每秒批次要求上觀察[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
4.  在觀察到的網路輸送量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
5.  可用記憶體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
### <a name="throughput-comparison-sample-results"></a>輸送量比較範例結果  
 與所有其他因素相等，輸送量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案所測量"BizTalk： 傳訊/文件 processed/Sec"效能監視器計數器時是從 67%的未偏離正軌輸送量 94.3%同時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]環境中的電腦已安裝在實體硬體上。  
  
 當[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]環境中的電腦已安裝在 HYPER-V 虛擬機器上，輸送量的方案已大幅拒絕觀察到，則輸送量縮減可以歸類為 HYPER-V 所需的 CPU 額外負荷。  
  
### <a name="latency-comparison-sample-results"></a>延遲的比較範例結果  
 與所有其他因素，BizTalk Server 環境中使用的 BizTalk Server 電腦執行 HYPER-V 的虛擬機器上的 BizTalk Server 解決方案所測量延遲時正在相等，「 BizTalk： 傳訊延遲/要求-回應延遲 （秒) 「 效能監視器計數器是從 66.9%94.3%的未偏離正軌延遲時 BizTalk Server 環境中使用的 BizTalk Server 電腦已安裝在實體硬體上。  
  
 當[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]環境中的電腦已安裝在 HYPER-V 虛擬機器上，輸送量的方案已大幅拒絕觀察到，則輸送量縮減可以歸類為上的hyper-v所需的CPU額外負荷[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]虛擬機器。  
  
### <a name="sql-server-processor-utilization-and-batch-requests-per-second-sample-results"></a>SQL 伺服器處理器使用量和每個第二個範例的結果批次要求  
 SQL 伺服器處理器使用率測量 \SQL\Processor(_Total)\\%Processor Time 計數器大約是相同的所有測試環境，範圍從最低的 88%到 90.1%的高效能。 沒有不過 \SQL Server:SQL Statistics\Batch 之間有顯著的差異 (4520) 的合併環境的要求數/秒測量和 \SQL Server:SQL Statistics\Batch 實體環境 (6350) 的要求數/秒測量。 \SQL Server:SQL Statistics\Batch Requests/sec 效能監視器計數器提供多少工作正在執行的 SQL Server 的良好指標。 批次要求數/秒 HYPER-V 環境中執行 SQL Server 時減少可以將歸類為 HYPER-V 所需的 CPU 額外負荷。  
  
### <a name="biztalk-server-and-sql-server-network-throughput-sample-results"></a>BizTalk Server 和 SQL Server 網路輸送量範例結果  
 HYPER-V 虛擬機器上執行的 BizTalk Server 的網路輸送量發現，範圍從大約 70%到 96%達成實體 BizTalk 伺服器上，根據特定的測試環境上的網路輸送量。 HYPER-V 虛擬機器上執行的 SQL Server 的網路輸送量發現，範圍從大約 68%到 81%達成實體的 SQL Server，再根據特定的測試環境上的網路輸送量。 在觀察到的網路輸送量差異可以屬於 HYPER-V Hypervisor 的資源需求。  
  
### <a name="biztalk-server-and-sql-server-available-memory-sample-results"></a>BizTalk Server 和 SQL Server 的可用記憶體範例結果  
 總記憶體可供 SQL Server 與 BizTalk Server \Memory\Available mbytes 效能監視器計數器所測量出相當一致的所有測試案例。