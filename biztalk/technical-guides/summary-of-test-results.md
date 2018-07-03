---
title: 測試結果的摘要 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d95fbaa6-0e07-4086-bea2-0577d39ae7cd
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad5550a073101e2a30555f90ad6bd879edff3a79
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997959"
---
# <a name="summary-of-test-results"></a>測試結果摘要
本主題摘要說明的測試案例的結果。  
  
## <a name="summary-of-test-results"></a>測試結果摘要  
 [測試 BizTalk 伺服器虛擬化效能](../technical-guides/testing-biztalk-server-virtualization-performance.md)一節說明如何測試應用程式中使用和設定的各種[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境執行測試應用程式。 比較效能已執行的測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  /  [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]實體硬體上所執行的 HYPER-V 虛擬機器上執行的環境效能的環境。 在測試期間測量關鍵效能指標 (Kpi) 包含下列作業：  
  
1. 訊息輸送量測量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。  
  
2. Visual Studio 測試用戶端提交同步要求上測量要求-回應延遲[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
3. 處理器使用率和每秒的批次要求上觀察不到[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
4. 在上觀察到的網路輸送量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
5. 可用記憶體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
### <a name="throughput-comparison-sample-results"></a>輸送量比較範例結果  
 與所有其他因素相當，輸送量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所測量的解決方案 」 BizTalk： 傳訊/文件 processed/Sec"效能監視器計數器時是從 67%的輸送量如今 94.3%同時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]環境中的電腦已安裝在實體硬體上。  
  
 當[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]環境中的電腦已安裝在 HYPER-V 虛擬機器上，拒絕大幅觀察到解決方案的輸送量，輸送量的縮減可以屬於 HYPER-V 所需的 CPU 額外負荷。  
  
### <a name="latency-comparison-sample-results"></a>延遲的比較範例結果  
 所有其他因素相等，BizTalk Server 解決方案所測量的延遲，HYPER-V 虛擬機器上執行 BizTalk Server 環境中使用的 BizTalk Server 電腦時使用 「 BizTalk： 傳訊延遲/要求-回應延遲 （秒) 」 效能監視器計數器是從 66.9%94.3%如今延遲時 BizTalk Server 環境中使用的 BizTalk Server 電腦已安裝在實體硬體上。  
  
 當[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]環境中的電腦已安裝在 HYPER-V 虛擬機器上，拒絕大幅觀察到解決方案的輸送量，輸送量的縮減可以屬於上的hyper-v所需的CPU額外負荷[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]虛擬機器。  
  
### <a name="sql-server-processor-utilization-and-batch-requests-per-second-sample-results"></a>SQL 伺服器處理器使用率和每個第二個範例的結果批次要求  
 SQL Server 處理器使用率所測量 \SQL\Processor(_Total)\\%Processor Time 計數器大約是在所有測試環境中，範圍從 88%的低到高 90.1%的相同。 沒有不過 \SQL Server:SQL Statistics\Batch 重大差異整合的環境 (4520) 的要求數/秒測量和 \SQL Server:SQL Statistics\Batch 測量實體環境 (6350) 上的要求數/秒。 \SQL Server:SQL Statistics\Batch Requests/sec 效能監視器計數器提供多少工作正在執行的 SQL Server 的良好指標。 Batch Requests/sec 在 HYPER-V 環境中執行 SQL Server 時縮小可歸咎於 HYPER-V 所需的 CPU 額外負荷。  
  
### <a name="biztalk-server-and-sql-server-network-throughput-sample-results"></a>BizTalk Server 和 SQL Server 網路輸送量範例結果  
 HYPER-V 虛擬機器上執行的 BizTalk Server 的網路輸送量發現，範圍從大約 70%到 96%的獲得在實體的 BizTalk 伺服器，根據特定的測試環境上的網路輸送量。 適用於 HYPER-V 虛擬機器上執行的 SQL Server 的網路輸送量發現，範圍從大約 68%到 81%的獲得在實體的 SQL Server，再根據特定的測試環境的網路輸送量。 在觀察到的網路輸送量的差異可歸咎於 HYPER-V Hypervisor 的資源需求。  
  
### <a name="biztalk-server-and-sql-server-available-memory-sample-results"></a>BizTalk Server 和 SQL Server 的可用記憶體範例結果  
 跨所有的測試案例，SQL Server 和 BizTalk Server 以 \Memory\Available mbytes 效能監視器計數器所測量的可用總記憶體是相當一致。