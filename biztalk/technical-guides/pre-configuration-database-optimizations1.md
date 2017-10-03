---
title: "預先設定資料庫 Optimizations1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebd0b32a-490d-4db2-a1fc-bf3bef93aeea
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c1333f956afc4411ff8b105c777214467155ae7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pre-configuration-database-optimizations"></a>預先設定資料庫最佳化
BizTalk Server 是可能需要多達 13 個不同的資料庫，Microsoft SQL Server 中建立的極大量資料庫的應用程式。 SQL Server 在任何 BizTalk Server 環境中扮演重要的角色，因為它最重要的是 SQL Server 已經設定/調整為適用於最佳效能。 如果 SQL Server 無法執行也微調，BizTalk Server 所使用的資料庫會成為瓶頸，以及 BizTalk Server 環境的整體效能會降低。 本主題說明安裝 BizTalk Server 和設定 BizTalk Server 資料庫之前，應遵循的數個 SQL Server 效能最佳化。  
  
## <a name="set-ntfs-file-allocation-unit"></a>設定 NTFS 檔案配置單位  
 SQL Server 會儲存其資料**範圍**，這是八個 8 千個頁面的群組。 因此，若要最佳化磁碟效能，NTFS 配置單位大小設定為 64 KB 最佳做法文章 「 前置部署 I/O 最佳作法 」 可在 SQL Server 的 「 磁碟組態最佳作法 」 一節中所述[http://go.microsoft.com/fwlink/ 嗎？LinkId = 140818](http://go.microsoft.com/fwlink/?LinkId=140818)。 如需有關 SQL Server 頁面與範圍，請參閱[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]線上叢書 》 主題[了解頁面與範圍](http://go.microsoft.com/fwlink/?LinkId=148939)(超連結"http://go.microsoft.com/fwlink/?LinkId=148939"http://go.microsoft.com/fwlink/?LinkId=148939)。  
  
## <a name="database-planning-considerations"></a>規劃考量的資料庫  
 我們建議您裝載您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]快速存放裝置 （例如，快速 SAN 磁碟或快速 SCSI 磁碟） 上的資料庫。 因為 raid 5 是撰寫速度較慢，建議 RAID 10 (1 + 0)，而不是 RAID 5。 較新的 SAN 磁碟會有非常大量的記憶體快取，因此在這些情況下，RAID 選取範圍不是那麼重要。 若要增加效能，資料庫和記錄檔案可位於不同實體磁碟上。  
  
## <a name="install-the-latest-service-pack-and-cumulative-updates-for-sql-server"></a>安裝 SQL Server 的最新 service pack 和累計更新  
 安裝 SQL Server 2005 和 SQL Server 2008，以及最新的.NET Framework 服務組件的最新的 service pack 和最新累計更新。  
  
## <a name="install-sql-service-packs-on-both-biztalk-server-and-sql-server"></a>安裝 BizTalk Server 和 SQL Server 上的 SQL Service Pack  
 當安裝 service pack for SQL Server，也在 BizTalk Server 電腦上安裝 service pack。 BizTalk Server 會使用由 SQL Server service pack 更新 SQL 用戶端元件。  
  
## <a name="consider-implementing-the-sql-server-2008-data-collector-and-management-data-warehouse"></a>請考慮實作 SQL Server 2008 資料收集器和管理資料倉儲  
 SQL Server 2008 適用於使用新的資料收集器和管理資料倉儲收集環境/資料庫效能的相關資料以供測試和趨勢分析。 資料收集器會保存到指定的管理資料倉儲收集到的所有資料。 雖然這不是一種效能最佳化，這會是用於分析的任何效能問題。  
  
## <a name="grant-the-account-which-is-used-for-sql-server-the-windows-lock-pages-in-memory-privilege"></a>授與帳戶是用於 SQL Server Windows Lock Pages In 記憶體特殊權限  
 SQL Server 服務帳戶的 Windows 「 鎖定記憶體中的分頁 」 權限授與。 這樣應該為了防止出 SQL Server 處理序的緩衝區集區記憶體分頁中的 Windows 作業系統，方法是鎖定實體記憶體中緩衝集區配置的記憶體。 如需詳細資訊，請參閱 Microsoft 知識庫文章 914483 「 如何減少緩衝集區記憶體在 64 位元版本的 SQL Server 2005 中的分頁 」 在[http://go.microsoft.com/fwlink/?LinkId=148948](http://go.microsoft.com/fwlink/?LinkId=148948)。  
  
## <a name="grant-the-semanagevolumename-right-to-the-sql-server-service-account"></a>授與 SE_MANAGE_VOLUME_NAME 由右至 SQL Server 服務帳戶  
 請執行 SQL Server 服務帳戶具有的 「 執行磁碟區維護工作 」 的 Windows 權限，或確定它所屬的安全性群組，並在它。 這可讓確保最佳效能，如果資料庫自動成長的立即檔案初始化。  
  
## <a name="set-min-and-max-server-memory"></a>設定 Min 和 Max Server Memory  
 執行的電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]裝載 BizTalk Server 資料庫只能專用於執行 SQL Server。 我們建議設定的 「 最小伺服器記憶體 」 和 「 最大伺服器記憶體 」 選項，每個 SQL Server 執行個體上的，指定固定配置給 SQL Server 的記憶體數量。 在此情況下，您應該設定的 「 最小伺服器記憶體 」 和 「 最大伺服器記憶體 」 為相同的值 （等於 SQL Server 將使用的實體記憶體的最大數量）。 這會降低額外負荷，否則會以動態方式管理這些值的 SQL Server 所使用。 指定要配置給 SQL Server 記憶體的固定的數量的每個 SQL Server 電腦上執行下列 T-SQL 命令：  
  
```  
sp_configure ‘Max Server memory (MB)’,(max size in MB)  
sp_configure ‘Min Server memory (MB)’,(min size in MB)  
```  
  
 您為 SQL Server 的記憶體數量之前，判斷適當的記憶體設定減去總實體記憶體的 Windows Server 所需的記憶體。 這是您可以指派給 SQL Server 記憶體的最大數量。  
  
> [!NOTE]  
>  如果執行 SQL Server 的主機電腦上 BizTalk Server 資料庫也會主控企業單一登入主要密碼伺服器，則您可能需要調整此值，以確保有足夠的記憶體可用來執行企業單一登入服務。 它不是一般的做法，在 SQL Server 叢集以提供高可用性的主要密碼伺服器上執行 「 企業單一登入服務的叢集執行個體。 如需叢集化企業單一登入主要密碼伺服器的詳細資訊，請參閱主題 「 如何要叢集主要密碼伺服器 」 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]文件，網址[http://go.microsoft.com/fwlink/?LinkID=106874](http://go.microsoft.com/fwlink/?LinkID=106874)。  
  
## <a name="split-the-tempdb-database-into-multiple-data-files-of-equal-size-on-each-sql-server-instance-used-by-biztalk-server"></a>分割成多個資料檔相同大小的 BizTalk Server 使用的每個 SQL Server 執行個體上的 tempdb 資料庫  
 用於 tempdb 資料檔案皆相同大小的很重要，因為比例填滿演算法使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]根據資料檔案的大小。 此演算法會嘗試確認[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]填滿，以便在到達其最大容量在同一時間成比例的可用空間的每個檔案保留在該檔案。 建立資料檔的大小不相等，如果比例填滿演算法會使用最大的多個 GAM 配置，而不是分配的配置之間的所有檔案，藉以定義建立多個資料檔案的目的檔案。 Tempdb 資料庫的資料檔案數目應該設定為至少等於指派為 SQL Server 的處理器數目。  
  
## <a name="enable-trace-flag-t1118-as-a-startup-parameter-for-all-instances-of-sql-server"></a>啟用追蹤旗標 T1118 作為啟動參數，所有執行個體的 SQL Server  
 實作追蹤旗標-T1118 有助於減少 SQL Server 執行個體之間的競爭，藉由移除幾乎所有的單一頁面配置。 如需詳細資訊，請參閱 Microsoft 知識庫文章 328551"PRB: tempdb 資料庫的並行存取增強功能 」 在[http://go.microsoft.com/fwlink/?LinkID=103713](http://go.microsoft.com/fwlink/?LinkID=103713)。  
  
## <a name="do-not-change-default-sql-server-settings-for-max-degree-of-parallelism-sql-server-statistics-or-database-index-rebuilds-and-defragmentation"></a>請勿變更預設 SQL Server 設定平行處理原則、 SQL Server 統計資料，或資料庫索引會重建和重組的最大程度  
 如果 SQL Server 執行個體將裝載 BizTalk Server 資料庫，某些 SQL Server 設定應該不變更。 具體來說，SQL Server max degree of parallelism，MessageBox 資料庫，以及設定資料庫索引的 SQL Server 統計資料會重建，並不能修改磁碟重組。 如需詳細資訊，請參閱 「 SQL Server 設定，不應該變更 」 主題中 BizTalk Server 作業指南 》，網址[http://go.microsoft.com/fwlink/?LinkId=114358](http://go.microsoft.com/fwlink/?LinkId=114358)。