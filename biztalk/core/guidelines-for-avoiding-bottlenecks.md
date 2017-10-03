---
title: "避免瓶頸的指導方針 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 640ab399-b22d-4f71-b41d-ea8d778e064a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e78f637c2fd6919b4182f2a58b5f16fbd23f0170
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="guidelines-for-avoiding-bottlenecks"></a>避免瓶頸的指導方針
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的預設設定會針對許多軟硬體組態提供最佳效能，但有時候修改此設定或部署組態會有助益。 在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，請考慮下列效能指導方針：  
  
-   為避免資源爭用，請將接收、協調流程和傳送分離至不同的主控件。 若要進一步將爭用情形降至最低，請將追蹤服務與其他主控件分離。  
  
-   如果 BizTalk Server 上的 CPU 處理是瓶頸，請加入其他 CPU 或升級為更快速的 CPU，向上擴充 BizTalk Server。  
  
## <a name="sql-server-guidelines"></a>SQL Server 指導方針  
 搭配 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定 Microsoft SQL Server 時，請考慮下列效能指導方針：  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫應該設定為在專用 SQL Server 執行個體盡可能上執行。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不是資料庫密集的應用程式，因此，明確劃分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦與裝載的 SQL Server 電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫將可改善效能，並且應該視為最佳作法是在生產環境中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
-   盡可能搭配 SQL Server 使用快速磁碟子系統。 使用類型 5 的磁碟陣列 (RAID5/10) 或具有備份電源供應的儲存區域網路 (SAN)。  
  
-   使用 SQL Server 損毀修復程序，定期備份資料庫。 BizTalk Server 服務會自動從 SQL Server 連線失敗復原。  
  
-   將每個 MessageBox 分離至與 BizTalk 追蹤資料庫 (BizTalkDTADb) 不同的伺服器。 針對較小的部署，如果有可用的 CPU 資源，將 MessageBox 分離至與 BizTalkDTADb 資料庫不同的實體磁碟可能就已足夠。  
  
-   由於 CPU 處理器飽和或因磁碟作業所造成的延遲 (平均磁碟佇列長度)，主要 MessageBox 可能成為瓶頸。 如果 CPU 處理是瓶頸，請將 CPU 處理器加入主要 MessageBox。 否則，請嘗試停用主要 MessageBox 的發佈功能，如此一來，主要 MessageBox 會更有效率地處理傳遞至其他 MessageBox 資料庫的訊息。  
  
-   如果磁碟作業是瓶頸，請將 BizTalkDTADb 資料庫移至專用的 SQL Server 電腦和 (或) 專用磁碟。 如果主要 MessageBox 上的 CPU 處理和磁碟作業都不是瓶頸，您可以在相同的 SQL Server 電腦上建立新的 MessageBox 資料庫，善用現有硬體。  
  
-   SQL Server 最佳作法來隔離到個別的實體磁碟上的 MessageBox 和 BizTalkDTADb 資料庫的交易和資料記錄檔。  
  
-   針對資料和記錄檔案配置足夠的儲存空間，否則 SQL Server 會自動取用保存記錄檔所在磁碟上的所有可用空間。 記錄檔的初始大小取決於特定實例的特殊需求。 根據測試結果評估部署時的平均檔案大小，在實作解決方案之前擴充儲存空間。  
  
-   針對高磁碟使用量的資料庫 (例如 MessageBox、追蹤和「商務活動監控」(BAM) 資料庫) 配置足夠的儲存空間。 如果您的解決方案使用 BizTalk Framework 傳訊通訊協定，請針對 BizTalk 組態資料庫 (BizTalkMgmtDb) 配置足夠的儲存空間。  
  
-   根據商務需求 [資料保留期限] 和特定實例中處理的資料量，設定追蹤資料庫的封存/清除工作，以確保 BizTalkDTADb 資料庫不會變得太大。 此資料庫太大會降低效能 (尤其是在 BizTalkDTADb 資料庫支援多個 MessageBox 時)，因為達到資料庫全部容量時會限制資料插入的速率。  
  
-   如果 MessageBox 和 BizTalkDTADb 資料庫是瓶頸，請向上擴充裝載這些資料庫的伺服器。 您可以增加 CPU、增加記憶體、升級為更快速的 CPU，以及使用高速專用磁碟，向上擴充硬體。