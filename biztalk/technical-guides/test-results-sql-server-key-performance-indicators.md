---
title: 測試結果： SQL Server 的關鍵效能指標 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2459ee6d-7a75-4338-ba5c-f42ab673ab87
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93e1f1bdef55ad726c308902062dccff67eeb170
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302462"
---
# <a name="test-results-sql-server-key-performance-indicators"></a>測試結果： SQL Server 的關鍵效能指標
本主題摘要說明 SQL Server 關鍵效能指標 (KPI) 內所觀測到的測試案例。 這些測試會評估下列的 SQL Server KPI:  
  
-   SQL 處理器使用率所測量**\SQL\Processor(_Total)\\%Processor Time**效能監視器計數器。  
  
-   每秒所測量的 TRANSACT-SQL 命令批次數目接收**\SQL Server:SQL Statistics\Batch Requests/sec**效能監視器計數器。  
  
## <a name="summary-of-sql-server-key-performance-indicators"></a>SQL Server 的關鍵效能指標的摘要  
 每個案例實體機器已受限制，讓邏輯處理器數目和虛擬處理器的對等。 這項作業完成使用 /maxmem 和 /numproc 的 boot.ini 參數。 使用這些參數的詳細資訊，請參閱 < 開機 INI 選項參考 >，網址[http://go.microsoft.com/fwlink/?LinkId=122139](http://go.microsoft.com/fwlink/?LinkId=122139)。  
  
 **比較 SQL Server 關鍵效能指標 –** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]所測量的處理器使用率**\SQL\Processor(_Total)\\%Processor Time**計數器是大約所有相同測試環境中，範圍從最低的 88%到 90.1%的高效能。   不過這會產生之間有顯著的差異**\SQL Server:SQL Statistics\Batch Requests/sec**測量合併環境 (4520) 和**\SQL Server:SQL Statistics\Batch Requests/sec**測量 (6350) 的實體環境。 **\SQL Server:SQL Statistics\Batch Requests/sec**效能監視器計數器提供多少工作正在執行的 SQL Server 的良好指標。 批次要求數/秒 HYPER-V 環境中執行 SQL Server 時減少可以將歸類為 HYPER-V 所需的 CPU 額外負荷。  
  
 不過，會產生之間有顯著的差異**\SQL Server:SQL Statistics\Batch Requests/sec**測量合併環境 (4520) 和**\SQL Server:SQL Statistics\Batch 要求數/秒**測量 (6350) 的實體環境。 **\SQL Server:SQL Statistics\Batch Requests/sec**效能監視器計數器提供多少工作正在執行的 SQL Server 的良好指標。 批次要求數/秒 HYPER-V 環境中執行 SQL Server 時減少可以將歸類為 HYPER-V 所需的 CPU 額外負荷。  
  
 請遵循下列步驟來提高效能所測量的 HYPER-V 虛擬機器上執行的 SQL Server **\SQL Server:SQL Statistics\Batch Requests/sec**效能監視器計數器：  
  
1.  **配置額外的固定的 VHD 磁碟與固定虛擬的控制站和通道 –** 配置使用的額外固定 VHD 磁碟的專用虛擬控制站和通道將會增加磁碟輸送量，而非使用單一的 VHD 磁碟。  
  
2.  **最佳化網路效能 –** 中的 < 最佳化網路效能 > 一節所述的步驟[檢查清單： 在 HYPER-V 上的 最佳化效能](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md)。 在相同的 HYPER-V 主機上執行多部 HYPER-V 虛擬機器時，特別重要，遵循 「 設定相同的 HYPER-V 上執行的 HYPER-V 虛擬機器主機使用的私人虛擬網路的電腦 」 一節中的建議[網路最佳化](../technical-guides/network-optimizations.md)。  
  
 由於無狀態的本質之故[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]額外[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]虛擬機器可以輕鬆地新增到環境為必要項目來提供向外的延展，並增加系統的整體效能。  
  
 下圖將說明在不同的測試平台上的 SQL Server 效能：  
  
 ![SQL 關鍵效能指標](../technical-guides/media/sqlkpi.gif "SQLKPI")  
SQL 關鍵效能指標  
  
 下表說明收集 KPI 的每個組態的相對效能。 每個結果集的計算方式為基準設定 KPI 的百分比  
  
|KPI|虛擬 BizTalk/實體 SQL|在不同的主機虛擬 BizTalk/虛擬 SQL|合併環境上的虛擬 BizTalk/虛擬 SQL|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|\SQL\Processor(_Total)\\%處理器時間|97.7%|98.4%|99.9%|  
|\SQL server: SQL Statistics\Batch 要求數/秒|97.1%|83.3%|71.2%|  
  
 如需如何評估磁碟 I/O 效能的詳細資訊，請參閱**測量磁碟 I/O 效能**主題的章節[檢查清單： 在 HYPER-V 上的測量效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。  
  
 如需在 HYPER-V 環境中執行 SQL Server 2008 的最佳作法的詳細資訊，請參閱白皮書 < 執行 SQL Server 2008 in a HYPER-V 環境 – 最佳作法和效能建議 > 下載[http: / / go.microsoft.com/fwlink/ 嗎？LinkId = 144622](http://go.microsoft.com/fwlink/?LinkId=144622)。