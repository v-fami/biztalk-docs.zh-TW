---
title: HYPER-V 上的系統資源成本 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f25a76c-1c41-41c0-b28d-d7473dbe1cd1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6be288e21657d447dd21bff06b5c3294f6f4a2c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003703"
---
# <a name="system-resource-costs-on-hyper-v"></a>HYPER-V 上的系統資源成本
## <a name="system-resource-costs-associated-with-running-a-guest-operating-system-on-hyper-v"></a>相關聯之 HYPER-V 上執行客體作業系統的系統資源成本  
 伺服器虛擬化軟體，沒有與執行才能支援在 HYPER-V 上執行的客體作業系統的虛擬化程式碼相關聯的額外負荷量。 下列清單摘要說明在 HYPER-V 虛擬機器上執行的客體作業系統時，與特定資源相關聯的額外負荷：  
  
### <a name="cpu-overhead"></a>CPU 額外負荷  
 9 與 12%之間的範圍內找不到相關的額外負荷的 HYPER-V 虛擬機器中執行來賓作業系統 CPU。  例如，通常在 HYPER-V 虛擬機器上執行客體作業系統必須可用 88 91%的 CPU 資源可用來在實體硬體上執行相等的作業系統。  
  
### <a name="memory-overhead"></a>記憶體額外負荷  
 對於 HYPER-V 主機電腦中，相關聯的 HYPER-V 虛擬機器上執行客體作業系統的記憶體成本發現是大約 300 MB 的 hypervisor，加上 32MB 的第一個 GB 的 RAM 配置給每部虛擬機器，加上另一個 8 MB針對每個額外 GB 的 RAM 配置給每個虛擬機器。 如需有關如何在 HYPER-V 虛擬機器上執行的客體作業系統的記憶體配置方式的詳細資訊，請參閱中的 < 最佳化記憶體效能 > 一節[檢查清單： 在 HYPER-V 上的 最佳化效能](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md)。  
  
### <a name="network-overhead"></a>網路額外負荷  
 直接能歸因於執行客體作業系統的 HYPER-V 虛擬機器中觀察到的網路延遲是小於 1 毫秒和客體作業系統通常維護的網路輸出佇列長度小於 1。 如需有關測量網路輸出佇列長度的詳細資訊，請參閱中的 < 測量網路效能 > 一節[檢查清單： 測量 HYPER-V 上的效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。  
  
### <a name="disk-overhead"></a>磁碟的額外負荷  
 在 HYPER-V 中使用 「 穿通磁碟 」 功能，當找不到磁碟與 HYPER-V 虛擬機器中執行為客體作業系統相關聯的 I/O 額外負荷介於 6 到 8%之間的範圍。 比方說，通常在 HYPER-V 上執行客體作業系統會有可用的 92 94%的磁碟 I/O 可測量的效能評定工具 IOMeter 的開放原始碼磁碟效能的實體硬體上執行對等作業系統。  
  
 如需測量 HYPER-V 主機或客體作業系統上使用 「 效能監視器的磁碟延遲資訊，請參閱中的 < 測量磁碟 I/O 效能 > 一節[檢查清單： 測量 HYPER-V 上的效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。  
  
 本節的其餘部分會提供 BizTalk Server 上的磁碟效能的背景資訊、 說明測試組態參數使用，並提供取得測試結果的摘要。  
  
#### <a name="disk-performance-when-running-a-biztalk-server-solution-on-hyper-v"></a>HYPER-V 上執行 BizTalk Server 解決方案時的磁碟效能  
 BizTalk Server 是非常資料庫密集應用程式可能需要建立的 SQL Server 中的達 13 個資料庫。 BizTalk Server 將資料保存到磁碟以絕佳的頻率，然後此外，這麼做為 MSDTC 交易的內容中。 因此，資料庫效能是任何 BizTalk Server 解決方案的整體效能最重要的。 HYPER-V 提供綜合 SCSI 控制器，而這兩者提供效能優勢明顯優於在模擬的 IDE 裝置這類 IDE 篩選器驅動程式隨附了 Virtual Server 2005。  
  
 設定為使用 SCSI 控制站的資料磁碟區的磁碟。 這樣會保證會安裝整合服務，因為如果而模擬的 IDE 控制器是可用，而不需要安裝 HYPER-V 整合服務，已安裝 HYPER-V 整合服務，可以只安裝 SCSI 控制器。 使用 SCSI 控制站或 integration services 提供 IDE 篩選器驅動程式執行的磁碟 I/O 是遠優於磁碟 I/O 效能提供模擬的 IDE 控制器。 因此，若要確保最佳的磁碟 I/O 效能，如 HYPER-V 虛擬化環境中的資料檔案，在主機和客體作業系統上安裝 integration services，而且與綜合 SCSI 控制站設定為資料磁碟區的磁碟。 對於跨越多個資料磁碟機的極大量的儲存體 I/O 工作負載，每個 VHD 應該附加至個別的綜合 SCSI 控制器以提升整體效能。 此外，每個 VHD 應該儲存在個別的實體磁碟或 Lun 上。  
  
#### <a name="measuring-passthrough-disk-performance"></a>測量的傳遞磁碟效能  
 在練習中任何彙總期間請務必充分使用可用的資源。 如先前所述，SQL 資料磁碟區上的儲存體 I/O 會在 BizTalk Server 解決方案的整體效能中扮演重要的部分。 因此在本指南中，已通過測試的實體磁碟效能的傳遞磁碟，在 HYPER-V 中的相對效能。 Physical_SQL01 中的相對效能的 MessageBox 資料磁碟機和 Virtual_SQL01 使用測量的 IOMeter 開放原始碼工具原本由 Intel Corporation 發展，現在維護的開放原始檔開發實驗室 (OSDL)。 如需 IOMeter 的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=122412 ](http://go.microsoft.com/fwlink/?LinkId=122412)。  
  
 下表描述的實體和虛擬的硬體組態來在測試環境、 所使用的 IOMeter 設定選項、 執行、 測試的描述，以及結果的摘要。  
  
#### <a name="configuration-used-for-testing"></a>用於測試的組態  
  
### <a name="physicalsql01"></a>Physical_SQL01  
  
|||  
|-|-|  
|**型號**|HP DL580|  
|**處理器**|四個處理器，四核心 Intel Xeon 2.4 Ghz|  
|**記憶體**|8 GB|  
|**網路功能**|HP NC3T3i 多功能 Gigabit Server 配接器|  
|**SAN 組態**|直接連接 SAN 存放裝置 （請參閱下表）|  
  
### <a name="physicalsql01--san-configuration"></a>Physical_SQL01 – SAN 組態  
  
|磁碟機代號|描述|LUN 大小|RAID 設定|  
|------------------|-----------------|--------------|------------------------|  
|G:|Data_Sys|10|RAID 0 + 1|  
|H:|Logs_Sys|10|RAID 0 + 1|  
|I:|Data_TempDb|50|RAID 0 + 1|  
|J:|Logs_TempDb|50|RAID 0 + 1|  
|K:|Data_BtsMsgBox|300|RAID 0 + 1|  
|L:|Logs_BtsMsgBox|100|RAID 0 + 1|  
|M:|MSDTC|5|RAID 0 + 1|  
  
### <a name="hyper-vhostsql01"></a>Hyper-V_Host_SQL01  
  
|||  
|-|-|  
|**型號**|HP DL580|  
|**處理器**|四個處理器，四核心 Intel Xeon 2.4 Ghz|  
|**記憶體**|32 GB|  
|**網路功能**|Broadcom BCM5708C NetXtreme II GigEHP DL380 第 5 代|  
  
### <a name="virtualsql01---virtual-machine-configuration"></a>Virtual_SQL01-虛擬機器組態  
  
|||  
|-|-|  
|**虛擬處理器**|配置 4|  
|**記憶體**|8 GB|  
|**網路功能**|虛擬機器的網路連線到：<br />Broadcom BCM5708C NetXtreme II GigE|  
|**硬碟設定**|**IDE 控制器**– 30 GB，作業系統固定 vhd<br />**SCSI 控制器**-7 直接連接 （請參閱下表） 的傳遞 SAN Lun|  
  
### <a name="virtualsql01--san-configuration"></a>Virtual_SQL01 – SAN 組態  
  
|磁碟機代號|描述|LUN 大小|RAID 設定|  
|------------------|-----------------|--------------|------------------------|  
|G:|Data_Sys|10|RAID 0 + 1|  
|H:|Logs_Sys|10|RAID 0 + 1|  
|I:|Data_TempDb|50|RAID 0 + 1|  
|J:|Logs_TempDb|50|RAID 0 + 1|  
|K:|Data_BtsMsgBox|300|RAID 0 + 1|  
|L:|Logs_BtsMsgBox|100|RAID 0 + 1|  
|M:|MSDTC|5|RAID 0 + 1|  
  
#### <a name="iometer-configuration"></a>IOMeter 設定  
 IOMeter 工具可用來當做基準測試和疑難排解工具藉由複寫應用程式的讀取/寫入效能。 IOMeter 是效能的一種可設定的工具，可用來模擬各種不同。 基於此測試案例的詳細資訊，IOMeter 組態參數已設定為下表中所述，在這兩個實體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]已經過測試的電腦和客體作業系統執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在 HYPER-V 虛擬機器:  
  
### <a name="iometer--passthrough-disk-comparison-test-configuration"></a>IOMeter – 穿通磁碟比較測試組態  
  
|                             |                     |
|-----------------------------|---------------------|
|       **測試時間長度**       |     10 分鐘      |
|      **加快時間**       |     30 秒      |
|    **背景工作角色數目**    |          4          |
|  **傳送要求大小**  |        2 KB         |
| **讀取/寫入散發** | 66%的讀取，33%的寫入 |
|      **高載長度**       |       1 個 I/o        |
|      **目標磁碟機**       |         K:\         |
  
#### <a name="test-description"></a>測試描述  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]服務已停止在這兩個伺服器，以確保 IOMeter 是唯一的程序，對磁碟執行 I/O。 LUN 的已使用這項測試中都位於相同的 SAN，這專用於此實驗室環境。 不受其他 I/O 活動時執行測試，以確保結果已不扭曲針對 SAN。 然後從每個在本機執行 IOMeter 工具執行測試[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和收集下列效能監視器計數器：  
  
 **收集自 Virtual_SQL01 和 Physical_SQL01**:  
  
- \LogicalDisk(*)\\\*  
  
- \PhysicalDisk(*)\\\*  
  
  **收集自虛擬機器的 Hyper-v V_02**:  
  
- \Hyper-V 虛擬存放裝置\\*  
  
### <a name="results"></a>結果  
 傳遞磁碟無法達到超過 90%的直接連線到 Physical_SQL01 SAN LUN 的輸送量。  總計、 讀取和寫入一樣是每秒傳送的總 MB 每秒的 I/o 已全都可在 10%。  狀況良好的磁碟回應時間應介於 1 到 15 毫秒的讀取和寫入。 平均 I/O 回應時間都小於 4 毫秒，這兩個磁碟上。 隨機讀取回應時間是在實體上以及 5.7 ms 傳遞磁碟上的 5.4 毫秒。 寫入回應時間為小於 0.5 毫秒在實體和虛擬環境。  
  
 結果會指出，使用已啟用的 SCSI 控制器的傳遞磁碟可以提供超過 90%的直接連線的實體磁碟的效能。 有效的 BizTalk Server 作業的 I/O 子系統效能至關重要藉由提供極佳的輸送量和回應時間 HYPER-V 是絕佳的候選項目合併 BizTalk Server 環境。 下表提供比較的實體磁碟的傳遞磁碟的效能時，所觀察到磁碟測試結果的摘要：  
  
|度量單位|Physical_SQL01 （實體磁碟）|Virtual_SQL01 (passthrough)|實體磁碟的傳遞磁碟的相對效能|  
|-----------------|---------------------------------------|------------------------------------|-----------------------------------------------------------------|  
|每秒的總 I/o|269.73|250.47|92.86%|  
|每秒的讀取 I/o|180.73|167.60|92.74%|  
|每秒寫入 I/o|89.00|82.87|93.11%|  
|每秒的總 Mb|0.53|0.49|92.45%|  
|平均讀取回應時間 （毫秒）|5.4066|5.7797|93.54%|  
|平均寫入回應時間 （毫秒）|0.2544|0.3716|68.42%**附註：** 雖然傳遞磁碟的平均寫入回應時間的相對效能皆為 68.42%的實體磁碟效能，也仍在已傳遞磁碟的平均寫入回應時間建立可接受的限制為 10 毫秒。|  
|平均 I/O 回應時間 （毫秒）|3.7066|3.9904|93.89%|  
  
> [!NOTE]  
>  每秒的總 I/o、 每秒的讀取 I/o、 每秒寫入的 I/o 和每秒的總 mb/s 的百分比值已計算是將傳遞磁碟值對應的實體磁碟值。  
>   
>  百分比值的平均讀取回應時間 （毫秒），平均寫入回應時間 （毫秒），並除以實體磁碟值相對應的傳遞磁碟值來計算平均 I/O 回應時間 （毫秒）。