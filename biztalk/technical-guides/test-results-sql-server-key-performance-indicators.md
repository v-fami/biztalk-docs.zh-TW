---
title: 測試結果： SQL Server 關鍵效能指標 |Microsoft Docs
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
ms.openlocfilehash: ed7f1348a23e6c4b145748ccfc0832c97648bdff
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007511"
---
# <a name="test-results-sql-server-key-performance-indicators"></a>測試結果： SQL Server 關鍵效能指標
本主題摘要說明 SQL Server 關鍵效能指標 (KPI) 內所觀測到的測試案例。 這些測試會評估下列的 SQL Server KPI:  
  
-   所測量的 SQL 的處理器使用率**\SQL\Processor(_Total)\\%Processor Time**效能監視器計數器。  
  
-   每秒所測量的 TRANSACT-SQL 命令批次數目接收**\SQL Server:SQL Statistics\Batch Requests/sec**效能監視器計數器。  
  
## <a name="summary-of-sql-server-key-performance-indicators"></a>SQL Server 關鍵效能指標的摘要  
 每個案例，讓邏輯處理器和虛擬處理器的數目已對等，已限制實體機器。 這是使用 /maxmem 和 /numproc 的 boot.ini 參數。 使用這些參數的詳細資訊，請參閱 < 開機 INI 選項參考 >，網址[ http://go.microsoft.com/fwlink/?LinkId=122139 ](http://go.microsoft.com/fwlink/?LinkId=122139)。  
  
 **比較 SQL Server 關鍵效能指標 –** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]所測量的處理器使用率**\SQL\Processor(_Total)\\%Processor Time**計數器是大約相同的所有測試環境中，範圍從 88%的低到高的 90.1%。   不過沒有明顯差異**\SQL Server:SQL Statistics\Batch Requests/sec**以整合的環境 (4520) 和**\SQL Server:SQL Statistics\Batch Requests/sec**測量實體環境 (6350)。 **\SQL Server:SQL Statistics\Batch Requests/sec**效能監視器計數器提供多少工作正在執行的 SQL Server 的良好指標。 Batch Requests/sec 在 HYPER-V 環境中執行 SQL Server 時縮小可歸咎於 HYPER-V 所需的 CPU 額外負荷。  
  
 差別，不過，重要**\SQL Server:SQL Statistics\Batch Requests/sec**在整合環境 (4520) 上測量而**\SQL Server:SQL Statistics\Batch Requests/sec**測量實體環境 (6350)。 **\SQL Server:SQL Statistics\Batch Requests/sec**效能監視器計數器提供多少工作正在執行的 SQL Server 的良好指標。 Batch Requests/sec 在 HYPER-V 環境中執行 SQL Server 時縮小可歸咎於 HYPER-V 所需的 CPU 額外負荷。  
  
 請遵循下列步驟，以增加所測量的 HYPER-V 虛擬機器上執行的 SQL Server 效能**\SQL Server:SQL Statistics\Batch Requests/sec**效能監視器計數器：  
  
1. **配置額外的固定的 VHD 磁碟，使用專用的虛擬控制站和通道 –** 其他固定的 VHD 磁碟使用的配置專用的虛擬控制器，通道會增加與使用單一的 VHD 磁碟的磁碟輸送量。  
  
2. **最佳化網路效能 –** 依照 < 最佳化網路效能 > 一節中所述的步驟[檢查清單： 在 HYPER-V 上的 最佳化效能](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md)。 在相同的 HYPER-V 主機上執行多部 HYPER-V 虛擬機器時，特別重要，遵循 「 設定相同的 HYPER-V 上執行的 HYPER-V 虛擬機器主機的電腦以使用私人虛擬網路 」 一節中的建議[網路最佳化](../technical-guides/network-optimizations.md)。  
  
   因為無狀態性質[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]其他[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]虛擬機器可以輕鬆地新增到環境為必要項目來提供向外延展，並增加系統的整體效能。  
  
   下圖說明各種測試平台上的 SQL Server 效能：  
  
   ![SQL 關鍵效能指標](../technical-guides/media/sqlkpi.gif "SQLKPI")  
   SQL 關鍵效能指標  
  
   下表說明收集 KPI 的每個組態的相對效能。 每個結果集的計算方式為基準設定 KPI 的百分比  
  
|KPI|虛擬 BizTalk/實體 SQL|在個別主機上的虛擬 BizTalk/虛擬 SQL|在 合併環境上的虛擬 BizTalk/虛擬 SQL|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|\SQL\Processor(_Total)\\%處理器時間|97.7%|98.4%|99.9%|  
|\SQL server: SQL Statistics\Batch Requests/sec|97.1%|83.3%|71.2%|  
  
 如需如何評估磁碟 I/O 效能的詳細資訊，請參閱**測量磁碟 I/O 效能**主題中的一節[檢查清單： 測量 HYPER-V 上的效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。  
  
 如需在 HYPER-V 環境中執行 SQL Server 2008 的最佳作法的詳細資訊，請參閱白皮書 < 執行 SQL Server 2008 in a HYPER-V 環境 – 最佳做法和效能建議 > 下載[ http://go.microsoft.com/fwlink/?LinkId=144622](http://go.microsoft.com/fwlink/?LinkId=144622).