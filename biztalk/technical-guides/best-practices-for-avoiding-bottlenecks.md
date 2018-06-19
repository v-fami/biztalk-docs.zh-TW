---
title: 避免瓶頸的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81da2e31-dce0-43fb-841f-e65ff99e80a7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08f2291d6aa4d16c251a110bc6f94c6288dc5064
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299662"
---
# <a name="best-practices-for-avoiding-bottlenecks"></a>避免瓶頸的最佳作法
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的預設設定會針對許多軟硬體組態提供最佳效能，但有時候修改此設定或部署組態會有助益。 在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，請考慮下列效能指導方針：  
  
-   若要避免資源爭用，隔離接收協調流程和傳送個別主機上。 若要進一步將爭用情形降至最低，請將追蹤服務與其他主控件分離。  
  
-   如果執行 BizTalk Server 的電腦上的 CPU 處理是瓶頸，向上擴充包含額外的 Cpu 或升級至更快速的 Cpu 執行 BizTalk Server 的電腦。  
  
## <a name="sql-server-guidelines"></a>SQL Server 指導方針  
 搭配 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定 Microsoft SQL Server 時，請考慮下列效能指導方針：  
  
-   盡可能搭配 SQL Server 使用快速磁碟子系統。 使用 10 別的獨立磁碟備援陣列 (RAID10 0 + 1) 或存放區域網路 (SAN) 具有備份電源供應器。  
  
-   隔離從 BizTalk 追蹤資料庫 (BizTalkDTADb) 不同的伺服器上每個 MessageBox 資料庫。 較小的部署 CPU 資源時，可能不足以隔離在不同的實體磁碟從 BizTalk 追蹤資料庫上的 MessageBox 資料庫。  
  
-   主要 MessageBox 資料庫可能是由於 CPU 處理器飽和或因磁碟作業 （平均磁碟佇列長度） 延遲瓶頸。 如果 CPU 處理是瓶頸，CPU 處理器加入主要 MessageBox。 否則，請嘗試停用主要 MessageBox 資料庫的發行。 如此一來，主要 MessageBox 資料庫會更有效率地處理傳遞至其他 MessageBox 資料庫的訊息。 若要停用發行選項無效，當您使用多個 MessageBox 資料庫。  
  
-   如果磁碟作業是瓶頸，請將 「 BizTalk 追蹤資料庫移至專用的 SQL Server 電腦和 （或） 專用的磁碟。 如果主要 MessageBox 資料庫上的 CPU 處理和磁碟作業都不是瓶頸，您可以在相同的 SQL Server 電腦，以善用現有硬體上建立新的 MessageBox 資料庫。  
  
-   請依照下列中的建議事項[Databases2 最佳化檔案群組](../technical-guides/optimizing-filegroups-for-the-databases2.md)隔離交易和資料記錄到個別的實體磁碟上的 MessageBox 和 「 BizTalk 追蹤資料庫的檔案。  
  
-   資料和記錄檔配置足夠的儲存空間。 否則 SQL Server 會自動使用所有可用空間的磁碟上存放的記錄檔。 記錄檔的初始大小取決於您的案例中的特定需求。 根據測試結果評估部署時的平均檔案大小，在實作解決方案之前擴充儲存空間。  
  
-   針對高磁碟使用的資料庫，例如 MessageBox、 健全狀況與活動追蹤 (HAT) 及商務活動監控 (BAM) 配置足夠的儲存空間。 如果您的解決方案使用 BizTalk Framework 傳訊通訊協定，請針對 BizTalk 組態資料庫 (BizTalkMgmtDb) 配置足夠的儲存空間。  
  
-   根據商務需求時，例如資料保留期限，以及您的案例中處理的資料磁碟區設定的 「 DTA 封存和清除 「 SQL Server Agent 作業在 HAT 追蹤資料庫上，BizTalk 追蹤資料庫不會變得太大。 此資料庫的成長會降低效能，因為達到資料庫全部容量會加諸的限制資料插入作業的速率。 當一個 BizTalk 追蹤資料庫支援多個 MessageBox 資料庫時，這是特別有用。  
  
-   如果是瓶頸，裝載 MessageBox 和 「 BizTalk 追蹤資料庫的伺服器向上延展。 您可以加入 Cpu、 增加記憶體，升級至更快速的 Cpu，並使用高速專用的磁碟擴充的硬體。  
  
-   將 TempDB 檔案分割到多個檔案，可能可以解決與 I/O 作業相關的效能問題。 一般來說，建立一個檔案資料檔，每個處理器，並建立的所有檔案使用相同的大小。  
  
-   變更資料庫自動成長設定，例如 100-150 MB 的固定值。 根據預設資料庫的成長設定為 10%，這會導致延遲增大較大的資料庫時。  
  
-   SQL Server 記憶體應設為固定值的最小伺服器記憶體和最大伺服器記憶體設為相同的值。 一般情況下，配置的實體記憶體的 75%到 SQL Server，並將其餘部分的作業系統和任何應用程式的 25%。 如果這是專用的 SQL Server，您可以減少保留供作業系統在最小值的 1 GB。  
  
## <a name="see-also"></a>另請參閱  
 [尋找並排除瓶頸](../technical-guides/finding-and-eliminating-bottlenecks.md)