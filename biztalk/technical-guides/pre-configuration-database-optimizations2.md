---
title: 預先設定資料庫 Optimizations2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c525c3a-249c-4694-b287-a8c35a6aa524
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f863ae780dd99a7f0aa7d9acc3884f860686c86
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015429"
---
# <a name="pre-configuration-database-optimizations"></a>預先設定資料庫最佳化
SQL Server 在任何 BizTalk Server 環境中扮演重要的角色，因為它最重要的是 SQL Server 是為了達到最佳效能設定/微調。 如果 SQL Server 無法執行也微調，BizTalk Server 所使用的資料庫會成為瓶頸，以及 BizTalk Server 環境的整體效能會降低。 本主題說明安裝 BizTalk Server 和設定 BizTalk Server 資料庫之前，應遵循的數個 SQL Server 效能最佳化。  
  
## <a name="set-ntfs-file-allocation-unit"></a>設定 NTFS 檔案配置單位  
 SQL Server 會儲存其資料**範圍**，而這是八個實體連續 8 千個頁面或 64 KB 的集合。 因此，若要將磁碟效能最佳化，NTFS 配置單位大小為 64 KB 「 磁碟組態最佳作法 」 中所述在設定[前置部署 I/O 最佳作法](https://msdn.microsoft.com/library/cc966412.aspx)。  
  
## <a name="considerations-for-the-version-and-edition-of-sql-server"></a>版本與版本的 SQL Server 的考量  
 各種版本和版別的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供不同的功能可能會影響效能，您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 例如，在高負載情況適用於 32 位元版本的資料庫鎖定數目[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可能超過即不利的 BizTalk 方案的效能。 請考慮罩上的 SQL Server 64 位元版本的 MessageBox 資料庫，如果您在測試環境中發生 「 鎖定不足 」 錯誤。 在 64 位元版本的 SQL Server 上，可用的鎖定數目大幅提高。  
  
 決定您將 BizTalk 環境所需的資料庫引擎功能時，請考慮下列資料表。 針對大規模的企業層級方案需要叢集的支援，BizTalk Server 記錄傳送支援，或 Analysis Services 支援，則您需要 SQL Server Enterprise Edition 主機[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫。   

 如需完整的 SQL Server 版本所支援的功能清單，請參閱[SQL Server 版本和支援的功能](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)。
  
## <a name="database-planning-considerations"></a>規劃考量的資料庫  
 我們建議您裝載您快速存放裝置 （例如，快速 SAN 磁碟或快速 SCSI 磁碟） 上的 SQL Server 資料庫。 因為 raid 5 是撰寫速度較慢，建議 RAID 10 (1 + 0)，而不是 RAID 5。 較新的 SAN 磁碟具有非常大量的記憶體快取，因此在這些情況下 raid 選取範圍不是那麼重要。 若要增加效能，資料庫和記錄檔案可位於不同實體磁碟上。  
  
 也請考慮調整主機匯流排介面卡 (HBA) 佇列深度，如果使用存放區域網路 (SAN)。 可能會大幅影響 I/O 輸送量，而出的值可能不足以執行 SQL Server。 雖然 64 佇列深度通常會獲接受成為很好的起點不存在的任何特定廠商的建議測試，才能決定最佳的值  
  
## <a name="install-the-latest-service-pack-and-cumulative-updates-for-sql-server"></a>安裝 SQL Server 的最新 service pack 和累計更新  
 安裝 SQL Server，以及最新的.NET Framework 服務組件的最新的 service pack 和最新累計更新。  
  
## <a name="install-sql-service-packs-and-cumulative-updates-on-both-biztalk-server-and-sql-server"></a>安裝 BizTalk Server 和 SQL Server 上的 SQL Service Pack 和累計更新  
 當安裝 SQL Server service pack 或累積更新，也安裝 service pack 或累積更新 BizTalk Server 電腦上。 BizTalk Server 使用 SQL Server service pack 和累計更新所更新的 SQL 用戶端元件。  
  
## <a name="consider-using-a-fast-solid-state-drive-ssd-to-house-the-sql-server-tembdb"></a>請考慮使用快速固態硬碟 (SSD) 來包含 SQL Server tembdb  
 請考慮使用一個或多個實心狀態磁碟 (SSD) 磁碟機來存放 TempDB。 SSD 磁碟機提供顯著的效能優於傳統硬碟，並快速地卸除價格進入主要市場。 因為 TempDB 效能通常是針對整體的關鍵因素[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]效能，已新增的初始成本的磁碟機將通常會快速原因所增加整體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]效能，特別在執行企業應用程式其[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]效能非常重要。  
  
## <a name="consider-implementing-the-sql-server-2008-r2-data-collector-and-management-data-warehouse"></a>請考慮實作 SQL Server 2008 R2 資料收集器和管理資料倉儲  
 SQL Server 2008 R2 可容納新的使用資料收集器和管理資料倉儲收集環境/資料庫效能的相關資料以供測試和趨勢分析。 資料收集器會保存到指定的管理資料倉儲收集到的所有資料。 雖然這不是效能最佳化方式，這會是用於分析的任何效能問題。  
  
## <a name="grant-the-account-which-is-used-for-sql-server-the-windows-lock-pages-in-memory-privilege"></a>授與帳戶是用於 SQL Server Windows Lock Pages In 記憶體特殊權限  
 授與 Windows 鎖定記憶體的特殊權限的 SQL Server 服務帳戶中的分頁。 這樣應該為了防止出 SQL Server 處理序的緩衝區集區記憶體分頁中的 Windows 作業系統，方法是鎖定實體記憶體中緩衝集區配置的記憶體。  
  
 在我們的實驗室環境，Windows 原則**鎖定記憶體分頁**選項依預設會啟用。 請參閱[啟用鎖定記憶體分頁選項](https://docs.microsoft.com/sql/database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows)。  
  
> [!IMPORTANT]  
>  Windows 鎖定分頁記憶體特殊權限授與 SQL Server 服務帳戶時，就會套用特定的限制。 請參閱下列內容： 
>   
> - [緩衝集區擴充](https://docs.microsoft.com/sql/database-engine/configure-windows/buffer-pool-extension)  
> - [啟用鎖定記憶體分頁選項](https://docs.microsoft.com/sql/database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows)  
  
## <a name="grant-the-semanagevolumename-right-to-the-sql-server-service-account"></a>由右至 SQL Server 服務帳戶授與 SE_MANAGE_VOLUME_NAME  
 請執行 SQL Server 服務帳戶具有 '執行磁碟區維護工作' Windows 權限，或確定它所屬的群組。 如果資料庫自動成長，這可讓檔案立即初始化確保最佳效能。  
  
## <a name="set-min-and-max-server-memory"></a>設定 Min 和 Max Server Memory  
 SQL Server 電腦裝載 BizTalk Server 資料庫應該專用於執行 SQL Server。 當該主控件執行 SQL Server 之電腦的 BizTalk Server 資料庫專用於執行 SQL Server 時，我們建議的最小伺服器記憶體' 和 '最大伺服器記憶體選項，每個 SQL Server 執行個體上的設定指定的固定的記憶體數量配置給 SQL Server。 在此情況下，您應該設定的 「 最小伺服器記憶體 」 和 「 最大伺服器記憶體 」 為相同的值 （等於 SQL Server 將使用的實體記憶體的最大數量）。 這會降低額外負荷，否則會以動態方式管理這些值的 SQL Server 所使用。 每個執行 SQL Server，來指定要配置給 SQL Server 記憶體的固定的數量的電腦上執行下列 T-SQL 命令：  
  
```  
sp_configure ‘Max Server memory (MB)’,(max size in MB)  
sp_configure ‘Min Server memory (MB)’,(min size in MB)  
```  
  
 您為 SQL Server 的記憶體數量之前，判斷適當的記憶體設定減去總實體記憶體的 Windows Server 所需的記憶體。 這是您可以指派給 SQL Server 記憶體的最大數量。  
  
> [!NOTE]  
>  如果該主控件執行 SQL Server 之電腦的 BizTalk Server 資料庫也會裝載企業單一登入主要密碼伺服器，則您可能需要調整此值，以確保有足夠的記憶體可用來執行企業單一登入服務。 它不是一般的做法，在 SQL Server 叢集以提供高可用性的主要密碼伺服器上執行 「 企業單一登入服務的叢集執行個體。 請參閱[叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)  
  
## <a name="split-the-tempdb-database-into-multiple-data-files-of-equal-size-on-each-sql-server-instance-used-by-biztalk-server"></a>分割成多個資料檔相同大小的 BizTalk Server 使用的每個 SQL Server 執行個體上的 tempdb 資料庫  
 用於 tempdb 資料檔案皆相同大小的很重要，因為 SQL Server 所使用的比例式填滿演算法為基礎的資料檔案的大小。 建立資料檔的大小不相等，如果比例填滿演算法會使用最大的多個 GAM 配置，而不是分配的配置之間的所有檔案，藉以定義建立多個資料檔案的目的檔案。 最佳的 tempdb 資料檔案數目取決於 tempdb 中所見的閂鎖競爭的程度。 為一般的經驗法則，資料檔案數目應該等於數字的處理器核心/Cpu 的 Cpu 數目，為 8 或更少。 針對具有超過 8 個 Cpu 的伺服器，建立資料檔案的一半的 Cpu 數目 （一次，僅有閂鎖競爭）。  
  
 在實驗室環境中，我們可以使用下列指令碼來建立其中每個的檔案大小為 1024 MB，成長 100 MB 的 8 個 TempDB 資料檔案和使用 100 MB 成長 512 MB 的記錄檔。 資料檔案移到磁碟機 H:%M 和記錄檔會移至 i： 磁碟機。  
  
> [!IMPORTANT]  
>  此指令碼為 「 現況，「 僅供示範或教育目的，且提供用於風險自負。 使用此指令碼不支援的 Microsoft，Microsoft 不會對不保證此指令碼的適用性。  
  
```  
--<<<<<<<<<<----------------------------------------------------------------->>>>>>>>>>--  
-- Use of included script samples are subject to the terms specified at   
-- http://www.microsoft.com/info/cpyright.htm  
--<<<<<<<<<<----------------------------------------------------------------->>>>>>>>>>--  
--***Instructions***  
-- 1. If running the script from a remote server, change the context in SSMS to target instance  
-- 2. Enable SQLCMD mode (add & click toolbar button or toggle by clicking Query > SQLCMD Mode)  
-- 3. Commence execution of scripts (recommend running statements discretely to more easily remedy potential problems)  
-- 4. Examine servername & temp configuration  
-- 5. If necessary, 1) Replace instance name in path to reflect target instance *all throughout script*  
      --            2) Modify root drives to reflect drives designated for data & log (folder creation *and* ALTER DB statements)  
-- 6. Resume script execution  
-- 7. If necessary, create new folders  
-- 8. Modify/Add data & log files   
-- 9. Recycle SQL service using sqlservermanager10.msc  
--10. Examine results & if appropriate, delete original tempdb data log files   
 --(if they were "moved", the original files aren't automatically deleted)  
  
--<<<<<<<<<<----------------------------------------------------------------->>>>>>>>>>--  
--1. If running the script from a remote server, change the context in SSMS to target instance  
--2. Enable SQLCMD mode (add & click toolbar button or toggle by clicking Query > SQLCMD Mode)  
--3. Commence execution of scripts (recommend running statements discretely to more easily remedy potential problems)  
--4. Examine servername & temp configuration  
SELECT @@SERVERNAME  
EXEC dbo.sp_helpdb tempdb  
--tempdev   1   C:\tempdb.mdf   PRIMARY  8192 KB  Unlimited  10%  data only  
--templog   2   C:\templog.ldf  NULL      512 KB  Unlimited  10%  log only  
GO  
--5. If necessary, 1) Replace instance name in path to reflect target instance *all throughout script*  
     --            2) Modify root drives to reflect drives designated for data & log (folder creation *and* ALTER DB statements)  
--6. Resume script execution  
--7. If necessary, create new folders  
--!!md H:\MSSQL10.<instance>  
--!!md H:\MSSQL10.<instance>\MSSQL  
--!!md H:\MSSQL10.<instance>\MSSQL\DATA  
GO  
-- 8. Modify/Add data & log files   
 --note: even if the out-of-box mdf is already where it needs to be,   
   --the first command is necessary to modify size & filegrowth  
ALTER DATABASE tempdb MODIFY FILE (NAME = tempdev  , FILENAME = 'H:\tempdb.mdf'   , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat2 , FILENAME = 'H:\tempdat2.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat3 , FILENAME = 'H:\tempdat3.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat4 , FILENAME = 'H:\tempdat4.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat5 , FILENAME = 'H:\tempdat5.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat6 , FILENAME = 'H:\tempdat6.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat7 , FILENAME = 'H:\tempdat7.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat8 , FILENAME = 'H:\tempdat8.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
GO  
ALTER DATABASE tempdb MODIFY FILE (NAME = templog , FILENAME = 'I:\templog.ldf', SIZE =  512MB , FILEGROWTH = 100MB)  
GO  
--8b. Modify log file:  modify drive & instance name to reflect designated destination for tempdb log   
--!!md I:\MSSQL10.<instance>  
--!!md I:\MSSQL10.<instance>\MSSQL  
--!!md I:\MSSQL10.<instance>\MSSQL\DATA  
GO  
-- 9. Recycle SQL service in SQL Server Services node of sqlservermanager10.msc  
    --note, if running script from a UNC share, SSMS will report an error,   
      --but SQL Server Configuration Manager will open if its location is in %path%  
!!sqlservermanager10.msc  
  
--10. Examine results & if appropriate, delete original tempdb data log files   
 --(if they were "moved", the original files aren't automatically deleted)  
EXEC dbo.sp_helpdb tempdb  
--!!del C:\tempdb.mdf     
--!!del C:\templog.ldf  
GO  
  
```  
  
 使用 SQL Server 2008 活動監視器] 或 [SQL Server 2005 績效儀表板報告中所述[監視 SQL Server 效能](../technical-guides/monitoring-sql-server-performance.md)來識別閂鎖競爭問題。  
  
## <a name="manually-set-sql-server-process-affinity"></a>手動設定 SQL Server 處理序相似性  
 處理序相似性選項可以提供高階的企業級非 NUMA 擁有 16 顆以上 Cpu 的電腦上執行的 SQL Server 環境的效能增強功能。 特別是在您共用 MessageBox 資料庫中的資料表有競爭的高輸送量 BizTalk 環境中。 因為我們的實驗室環境中所使用的 SQL Server 電腦未啟用 NUMA 的而且具有 16 個核心，來最佳化效能，我們會用來設定處理序相似性的下列命令：  
  
 **若要手動設定 SQL Server 處理序相似性從 0 到 15**  
  
```  
ALTER SERVER CONFIGURATION  
SET PROCESS AFFINITY CPU = 0 to 15  
```  
  
 如需詳細資訊，請參閱[ALTER SERVER CONFIGURATION (TRANSACT-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-server-configuration-transact-sql)。
  
## <a name="configure-msdtc"></a>設定 MSDTC  
 若要簡化 SQL Server 與 BizTalk Server 之間的交易，您必須啟用 Microsoft 分散式交易協調器 (MS DTC)。 若要在 SQL Server 上設定 MSDTC，請參閱主題[改善作業系統效能的一般指導方針](../technical-guides/general-guidelines-for-improving-operating-system-performance.md)。  
  
## <a name="enable-trace-flag-t1118-as-a-startup-parameter-for-all-instances-of-sql-server"></a>啟用追蹤旗標 T1118 作為啟動參數，所有執行個體的 SQL Server  
 實作追蹤旗標-T1118 有助於減少 SQL Server 執行個體之間的競爭，藉由移除幾乎所有的單一頁面配置。 如需詳細資訊，請參閱[KB 328551: PRB: tempdb 資料庫的並行存取增強功能](https://support.microsoft.com/help/328551/concurrency-enhancements-for-the-tempdb-database)。
  
## <a name="do-not-change-default-sql-server-settings-for-max-degree-of-parallelism-sql-server-statistics-or-database-index-rebuilds-and-defragmentation"></a>請勿變更預設 SQL Server 設定平行處理原則、 SQL Server 統計資料，或資料庫索引會重建和重組的最大程度  
 如果 SQL Server 執行個體將裝載 BizTalk Server 資料庫，會有某些不應該變更的 SQL Server 設定。 具體來說，SQL Server max degree of parallelism，MessageBox 資料庫，以及設定資料庫索引的 SQL Server 統計資料會重建，並不能修改磁碟重組。 請參閱[不應該變更的 SQL Server 設定](../technical-guides/sql-server-settings-that-should-not-be-changed.md)。
  
## <a name="see-also"></a>另請參閱  
 [最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)
