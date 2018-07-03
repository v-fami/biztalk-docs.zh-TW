---
title: 預先設定資料庫 Optimizations1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebd0b32a-490d-4db2-a1fc-bf3bef93aeea
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c59c396534d6c555cfd133e949e3a5becb5375b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998831"
---
# <a name="pre-configuration-database-optimizations"></a>預先設定資料庫最佳化
BizTalk Server 是極大量資料庫的應用程式可能需要建立的 Microsoft SQL Server 中達 13 個不同的資料庫。 SQL Server 在任何 BizTalk Server 環境中扮演重要的角色，因為它最重要的是 SQL Server 會以獲得最佳效能設定/調整。 如果 SQL Server 未正確執行微調，BizTalk Server 所使用的資料庫會成為瓶頸，和 BizTalk Server 環境的整體效能會受到影響。 本主題說明 BizTalk Server 安裝和設定 BizTalk Server 資料庫之前，應遵循的數個 SQL Server 效能最佳化。  
  
## <a name="set-ntfs-file-allocation-unit"></a>設定 NTFS 檔案配置單位  
 SQL Server 會儲存其資料**範圍**，這是八個 8k 頁面的群組。 因此，為了最佳化磁碟效能，設定 NTFS 配置單位大小為 64 KB 最佳做法文章 「 前置部署 I/O 最佳作法 」 可在 SQL Server 的 「 磁碟組態最佳作法 」 一節中所述[ http://go.microsoft.com/fwlink/?LinkId=140818](http://go.microsoft.com/fwlink/?LinkId=140818). 如需有關 SQL Server 頁面與範圍請參閱 SQL Server 線上叢書 》 主題[了解頁面與範圍](http://go.microsoft.com/fwlink/?LinkId=148939)(HYPERLINK"<http://go.microsoft.com/fwlink/?LinkId=148939>" <http://go.microsoft.com/fwlink/?LinkId=148939>)。  
  
## <a name="database-planning-considerations"></a>規劃考量的資料庫  
 我們建議您裝載您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]快速存放裝置 （例如，快速 SAN 磁碟或快速 SCSI 磁碟） 上的資料庫。 我們會建議 RAID 10 (1 + 0)，而不是 RAID 5，因為 raid 5 是在撰寫更慢。 較新的 SAN 磁碟會有非常大的記憶體快取，因此在這些情況下，RAID 選取項目並不重要。 若要增加效能，資料庫和其記錄檔可以位於不同實體磁碟上。  
  
## <a name="install-the-latest-service-pack-and-cumulative-updates-for-sql-server"></a>適用於 SQL Server 安裝最新版 service pack 和累計更新  
 安裝 SQL Server 2005 和 SQL Server 2008，以及最新的.NET Framework service pack 的最新的 service pack 和最新的累計更新。  
  
## <a name="install-sql-service-packs-on-both-biztalk-server-and-sql-server"></a>安裝 BizTalk Server 和 SQL Server 上的 SQL Service Pack  
 當安裝 service pack for SQL Server，也在 BizTalk Server 電腦上安裝 service pack。 BizTalk Server 會使用 SQL Server service pack 更新 SQL 用戶端元件。  
  
## <a name="consider-implementing-the-sql-server-2008-data-collector-and-management-data-warehouse"></a>請考慮實作 SQL Server 2008 資料收集器和管理資料倉儲  
 SQL Server 2008 適用於使用新的資料收集器和管理資料倉儲，以收集環境/資料庫效能相關資料以供測試和趨勢分析。 資料收集器收集到的所有資料保存到指定的管理資料倉儲。 雖然這不是一種效能最佳化，這是用於分析的任何效能問題。  
  
## <a name="grant-the-account-which-is-used-for-sql-server-the-windows-lock-pages-in-memory-privilege"></a>授與帳戶用於 SQL Server 的 Windows 鎖定記憶體的權限中的分頁  
 SQL Server 服務帳戶的 Windows 「 鎖定記憶體中的分頁 」 權限授與。 這應該是為了防止出 SQL Server 處理序的緩衝區集區記憶體分頁中的 Windows 作業系統，方法是鎖定實體記憶體中緩衝集區配置的記憶體。 詳細資訊，請參閱 Microsoft 知識庫文件 914483 < 如何降低分頁的 64 位元版本的 SQL Server 2005 中的緩衝集區記憶體 >，網址[ http://go.microsoft.com/fwlink/?LinkId=148948 ](http://go.microsoft.com/fwlink/?LinkId=148948)。  
  
## <a name="grant-the-semanagevolumename-right-to-the-sql-server-service-account"></a>授與由右至 SQL Server 服務帳戶的 SE_MANAGE_VOLUME_NAME  
 請確定執行 SQL Server 服務帳戶具有 「 執行磁碟區維護工作 」 的 Windows 權限，或確定其所屬的安全性群組，並在它。 這可確保最佳效能，如果資料庫具有自動成長的檔案立即初始化。  
  
## <a name="set-min-and-max-server-memory"></a>設定最小和最大伺服器記憶體  
 執行的電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]裝載 BizTalk Server 資料庫應該專門用來執行 SQL Server。 我們建議的 「 最小伺服器記憶體 」 和 「 最大伺服器記憶體 」 選項，每個 SQL Server 執行個體上的設定指定的固定配置給 SQL Server 的記憶體數量。 在此情況下，您應該設定的 「 最小伺服器記憶體 」 和 「 最大伺服器記憶體 」 為相同的值 （等於 SQL Server 會使用的實體記憶體的最大數量）。 這會減少，否則會以動態方式管理這些值的 SQL Server 所使用的額外負荷。 指定要配置給 SQL Server 的記憶體固定的量的每個 SQL Server 電腦上執行下列 T-SQL 命令：  
  
```  
sp_configure ‘Max Server memory (MB)’,(max size in MB)  
sp_configure ‘Min Server memory (MB)’,(min size in MB)  
```  
  
 適用於 SQL Server 設定的記憶體數量之前，判斷適當的記憶體設定，並減去總實體記憶體，適用於 Windows Server 所需的記憶體。 這是記憶體的您可以指派給 SQL Server 最大數量。  
  
> [!NOTE]  
>  如果該主控件執行 SQL Server 的電腦的 BizTalk Server 資料庫也會裝載企業單一登入主要密碼伺服器，則您可能需要調整此值以確定有足夠的記憶體可用來執行企業單一登入服務。 它就不是常見的做法，以提供高可用性的主要密碼伺服器的 SQL Server 叢集上執行 「 企業單一登入服務的叢集執行個體。 更多叢集 「 企業單一登入主要密碼伺服器的詳細資訊，請參閱主題 「 如何以叢集主要密碼伺服器 」，以在 BizTalk Serverdocumentation [ http://go.microsoft.com/fwlink/?LinkID=106874 ](http://go.microsoft.com/fwlink/?LinkID=106874)。  
  
## <a name="split-the-tempdb-database-into-multiple-data-files-of-equal-size-on-each-sql-server-instance-used-by-biztalk-server"></a>將 tempdb 資料庫分割成多個資料檔案大小相同的 BizTalk Server 使用的每個 SQL Server 執行個體  
 用來將 tempdb 資料檔案皆相同大小的很重要，因為依比例填入演算法使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]根據資料檔案的大小。 此演算法會嘗試確保[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]比例的可用空間的每個檔案會停留在該檔案，以便達到大約相同的時間在其最大容量的填滿。 如果建立的資料檔案大小不相等，則依比例填入演算法會使用最大的檔案進行 GAM 配置，而不是所有的檔案，藉此廢除建立多個資料檔案的目的之間散佈配置更多。 Tempdb 資料庫的資料檔案數目應該設定為至少等於指派給 SQL Server 的處理器數目。  
  
## <a name="enable-trace-flag-t1118-as-a-startup-parameter-for-all-instances-of-sql-server"></a>作為啟動參數啟用追蹤旗標 T1118，SQL Server 的所有執行個體  
 實作追蹤旗標-T1118 有助於減少在 SQL Server 執行個體之間的競爭，藉由移除幾乎所有的單一頁面配置。 如需詳細資訊，請參閱 Microsoft 知識庫文章 328551"PRB: tempdb 資料庫的並行存取增強功能 」 在[ http://go.microsoft.com/fwlink/?LinkID=103713 ](http://go.microsoft.com/fwlink/?LinkID=103713)。  
  
## <a name="do-not-change-default-sql-server-settings-for-max-degree-of-parallelism-sql-server-statistics-or-database-index-rebuilds-and-defragmentation"></a>請勿變更預設 SQL Server 平行處理原則、 SQL Server 的統計資料，或資料庫索引重建和重組的最大程度設定  
 如果 SQL Server 執行個體將裝載 BizTalk Server 資料庫，某些 SQL Server 設定應該不變更。 具體來說，SQL Server 的最大程度的平行處理原則，在 MessageBox 資料庫，以及資料庫索引的設定上的 SQL Server 統計資料重建，並且不應該修改磁碟重組。 詳細資訊，請參閱 「 SQL Server 設定，不應變更 」 主題，在 BizTalk Server 作業指南 》，網址[ http://go.microsoft.com/fwlink/?LinkId=114358 ](http://go.microsoft.com/fwlink/?LinkId=114358)。