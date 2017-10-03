---
title: "HYPER-V 上的系統資源成本 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f25a76c-1c41-41c0-b28d-d7473dbe1cd1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20f9707b8606e64773d42c480735d3f876f1c3ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="system-resource-costs-on-hyper-v"></a>HYPER-V 上的系統資源成本
## <a name="system-resource-costs-associated-with-running-a-guest-operating-system-on-hyper-v"></a>HYPER-V 上執行客體作業系統與相關聯的系統資源成本  
 伺服器虛擬化軟體，沒有與執行以支援在 HYPER-V 上執行的客體作業系統的虛擬化程式碼相關聯的負擔量。 下列清單摘要說明當 HYPER-V 虛擬機器上執行的客體作業系統相關聯的特定資源的額外負荷：  
  
### <a name="cpu-overhead"></a>CPU 額外負荷  
 CPU 負擔執行客體作業系統的 HYPER-V 虛擬機器中找不到 9 與 12%之間的範圍。  例如，通常在 HYPER-V 虛擬機器上執行客體作業系統必須可用 88 91%可用來在實體硬體上執行相同作業系統的 CPU 資源。  
  
### <a name="memory-overhead"></a>記憶體額外負荷  
 針對 HYPER-V 主機電腦，與 HYPER-V 虛擬機器上執行客體作業系統相關聯的記憶體成本發現是大約 300 MB 的 hypervisor，加上 32 MB 的第一個 GB 的 RAM 配置給每個虛擬機器，加上另一個 8 MB針對每個其他 GB 的 RAM 配置給每個虛擬機器。 如需為 HYPER-V 虛擬機器上執行的客體作業系統的記憶體配置方式的詳細資訊，請參閱中的 < 最佳化記憶體效能 > 一節[檢查清單： 在 HYPER-V 上的 最佳化效能](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md)。  
  
### <a name="network-overhead"></a>網路額外負荷  
 直接能歸因於執行客體作業系統的 HYPER-V 虛擬機器中觀察到的網路延遲是少於 1 毫秒和客體作業系統通常維護網路輸出佇列的長度小於 1。 如需有關測量網路輸出佇列長度的詳細資訊，請參閱中的 < 測量網路效能 > 一節[檢查清單： 在 HYPER-V 上的測量效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。  
  
### <a name="disk-overhead"></a>磁碟的額外負荷  
 使用傳遞磁碟功能時在 HYPER-V 中，找不到磁碟與 HYPER-V 虛擬機器中執行來賓作業系統相關聯的 I/O 額外負荷介於 6 和 8%的範圍。 比方說，通常在 HYPER-V 上執行客體作業系統有可用的 92 94%的磁碟 I/O 可測量的效能評定工具 IOMeter 開放原始碼磁碟效能的實體硬體上執行對等作業系統。  
  
 測量在 HYPER-V 主機或客體作業系統上使用 「 效能監視器的磁碟延遲的相關資訊，請參閱中的 < 測量磁碟 I/O 效能 > 一節[檢查清單： 在 HYPER-V 上的測量效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。  
  
 本節的其餘部分提供 BizTalk Server 上磁碟效能的背景資訊，描述的測試組態參數使用，並提供取得的測試結果的摘要。  
  
#### <a name="disk-performance-when-running-a-biztalk-server-solution-on-hyper-v"></a>HYPER-V 上執行 BizTalk Server 解決方案時，磁碟效能  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]是極資料庫密集的應用程式可能需要建立的 SQL Server 中的多達 13 個資料庫。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]保存到磁碟的資料很棒的頻率，此外，這樣做，MSDTC 交易的內容中。 因此，資料庫效能極為重要的任何 BizTalk Server 解決方案的整體效能。 HYPER-V 提供綜合 SCSI 控制器，而這兩者使用模擬的 IDE 裝置，例如透過提供效能優勢明顯 IDE 篩選器驅動程式隨附 Virtual Server 2005。  
  
 設定為使用 SCSI 控制站的資料磁碟區的磁碟。 這樣會保證會安裝整合服務，因為如果而不需要安裝 HYPER-V 整合服務是使用模擬的 IDE 控制器，已安裝 HYPER-V 整合服務，可以只安裝 SCSI 控制器。 使用 SCSI 控制站或 integration services 提供 IDE 篩選器驅動程式執行磁碟 I/O 是明顯優於磁碟 I/O 效能所提供的模擬的 IDE 控制器。 因此，若要確保最佳的磁碟 I/O 效能中 HYPER-V 虛擬化環境中的資料檔案，在主機和客體作業系統上安裝 integration services 及設定資料磁碟區的磁碟與綜合 SCSI 控制器。 對於跨越多個資料磁碟機的極大量的儲存體 I/O 工作負載，每個 VHD 應該附加到另一個更佳的整體效能的綜合 SCSI 控制器。 此外，每個 VHD 應該儲存在個別的實體磁碟或 Lun 上。  
  
#### <a name="measuring-passthrough-disk-performance"></a>測量穿通磁碟效能  
 任何彙總練習期間是發揮最大可用的資源。 如先前所討論，SQL 資料磁碟區上的儲存體 I/O 扮演重要部分的整體效能[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]方案。 因此本指南中，已通過測試的實體磁碟的 HYPER-V 中的直接存取磁碟效能的相對效能。 Physical_SQL01 中的相對效能的 MessageBox 資料磁碟機和 Virtual_SQL01 測量使用的 IOMeter 開放原始碼工具原本由 Intel Corporation 發展和現在維護由開啟來源開發實驗室 (OSDL)。 如需 IOMeter 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=122412](http://go.microsoft.com/fwlink/?LinkId=122412)。  
  
 下表說明在測試環境、 所使用的 IOMeter 設定選項、 執行、 測試的描述和結果的摘要使用的實體和虛擬的硬體組態。  
  
#### <a name="configuration-used-for-testing"></a>用於測試的組態  
  
### <a name="physicalsql01"></a>Physical_SQL01  
  
|||  
|-|-|  
|**型號**|HP DL580|  
|**處理器**|四處理器，顆四核心 Intel Xeon 2.4 Ghz|  
|**記憶體**|8 GB|  
|**網路功能**|HP NC3T3i 多功能十億位元伺服器的配接器|  
|**SAN 組態**|直接連接的 SAN 存放裝置 （請參閱下表）|  
  
### <a name="physicalsql01--san-configuration"></a>Physical_SQL01 – SAN 組態  
  
|磁碟機代號|Description|LUN 的大小|RAID 組態|  
|------------------|-----------------|--------------|------------------------|  
|G:|Data_Sys|10|RAID 0 + 1|  
|H:|Logs_Sys|10|RAID 0 + 1|  
|I:|Data_TempDb|50|RAID 0 + 1|  
|J:|Logs_TempDb|50|RAID 0 + 1|  
|K:|Data_BtsMsgBox|300|RAID 0 + 1|  
|L:|Logs_BtsMsgBox|100|RAID 0 + 1|  
|M:|MSDTC|5|RAID 0 + 1|  
  
### <a name="hyper-vhostsql01"></a>Hyper-v V_Host_SQL01  
  
|||  
|-|-|  
|**型號**|HP DL580|  
|**處理器**|四處理器，顆四核心 Intel Xeon 2.4 Ghz|  
|**記憶體**|32 GB|  
|**網路功能**|Broadcom BCM5708C NetXtreme II GigEHP DL380 G5|  
  
### <a name="virtualsql01---virtual-machine-configuration"></a>Virtual_SQL01-虛擬機器組態  
  
|||  
|-|-|  
|**虛擬處理器**|配置 4|  
|**記憶體**|8 GB|  
|**網路功能**|虛擬機器的網路連線到：<br />Broadcom BCM5708C NetXtreme II GigE|  
|**硬碟設定**|**IDE 控制器**– 30 GB 的作業系統固定 vhd<br />**SCSI 控制器**-7 直接連接直接存取 SAN Lun （請參閱下表）|  
  
### <a name="virtualsql01--san-configuration"></a>Virtual_SQL01 – SAN 組態  
  
|磁碟機代號|Description|LUN 的大小|RAID 組態|  
|------------------|-----------------|--------------|------------------------|  
|G:|Data_Sys|10|RAID 0 + 1|  
|H:|Logs_Sys|10|RAID 0 + 1|  
|I:|Data_TempDb|50|RAID 0 + 1|  
|J:|Logs_TempDb|50|RAID 0 + 1|  
|K:|Data_BtsMsgBox|300|RAID 0 + 1|  
|L:|Logs_BtsMsgBox|100|RAID 0 + 1|  
|M:|MSDTC|5|RAID 0 + 1|  
  
#### <a name="iometer-configuration"></a>IOMeter 設定  
 IOMeter 工具可用來當作基準測試和疑難排解工具藉由複寫應用程式的讀取/寫入效能。 IOMeter 是效能的一種可設定的工具，可用來模擬許多不同類型。 基於此測試案例的詳細資訊，IOMeter 組態參數已設定為下表中所述的兩個實體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]已測試的電腦和客體作業系統執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在 HYPER-V 虛擬機器:  
  
### <a name="iometer--passthrough-disk-comparison-test-configuration"></a>IOMeter – 穿通磁碟比較測試組態  
  
|||  
|-|-|  
|**測試時間長度**|10 分鐘|  
|**準備時間**|30 秒|  
|**背景工作數目**|4|  
|**傳送要求的大小**|2 KB|  
|**讀取/寫入發佈**|讀取 66%，33%寫入|  
|**高載長度**|1 的 i/o 數目|  
|**目標磁碟機**|K:\|  
  
#### <a name="test-description"></a>測試描述  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]服務已停止，確保 IOMeter 已執行對磁碟 I/O 的唯一程序的兩部伺服器上。 LUN 的使用在這項測試都位於相同的 SAN 專用於此實驗室環境。 任何其他的 I/O 活動時不執行測試，確保結果不有所偏差針對 SAN。 藉由從每個在本機執行 IOMeter 工具再執行測試[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和收集下列效能監視器計數器：  
  
 **收集 Virtual_SQL01 和 Physical_SQL01**:  
  
-   \LogicalDisk(*)\\\*  
  
-   \PhysicalDisk(*)\\\*  
  
 **從虛擬機器 Hyper-v V_02 收集**:  
  
-   \Hyper-V 虛擬存放裝置\\*  
  
### <a name="results"></a>結果  
 傳遞磁碟已達到超過 90%的直接連線到 Physical_SQL01 的 SAN LUN 的輸送量。  總計、 讀取和寫入每秒的 I/o 已全部都在 10%內為每秒傳送的總 MB。  狀況良好的磁碟回應時間應該介於 1-15 毫秒的讀取和寫入。 I/O 的平均回應時間的兩個磁碟小於 4 毫秒。 隨機讀取回應時間為 5.4 ms 實體上和 5.7 ms 傳遞磁碟上。 寫入回應時間為小於 0.5 毫秒在實體和虛擬環境。  
  
 結果會指出，使用已啟用功能的 SCSI 控制器的直接存取磁碟可以提供超過 90%的直接連接的實體磁碟的效能。 I/O 子系統效能非常重要的有效率[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]作業，藉由提供極佳的輸送量和回應時間 HYPER-V 為傑出候選項目合併[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]環境。 下表提供比較效能的實體磁碟將穿通磁碟時，觀察到的磁碟測試結果摘要：  
  
|度量|Physical_SQL01 （實體磁碟）|Virtual_SQL01 (passthrough)|傳遞磁碟的實體磁碟的相對效能|  
|-----------------|---------------------------------------|------------------------------------|-----------------------------------------------------------------|  
|每秒總 I/o|269.73|250.47|92.86%|  
|每秒的讀取 I/o|180.73|167.60|92.74%|  
|每秒寫入 I/o|89.00|82.87|93.11%|  
|每秒的總 Mb|0.53|0.49|92.45%|  
|平均讀取回應時間 （毫秒）|5.4066|5.7797|93.54%|  
|寫入的平均回應時間 （毫秒）|0.2544|0.3716|68.42%**附註：**雖然傳遞磁碟寫入的平均回應時間的相對效能 68.42%的實體磁碟的效能，以及內已傳遞磁碟的平均寫入回應時間建立可接受的限制為 10 毫秒。|  
|平均 I/O 回應時間 （毫秒）|3.7066|3.9904|93.89%|  
  
> [!NOTE]  
>  每秒總 I/o、 每秒的讀取 I/o、 每秒寫入的 I/o 和每秒的總 mb/s 的百分比值會計算除以穿通磁碟值對應的實體磁碟值。  
>   
>  百分比值的平均讀取回應時間 （毫秒），平均寫入回應時間 （毫秒），並計算實體磁碟值對應的傳遞磁碟值再除以出來的平均 I/O 回應時間 （毫秒）。