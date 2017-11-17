---
title: "預先設定資料庫 Optimizations2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c525c3a-249c-4694-b287-a8c35a6aa524
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f863ae780dd99a7f0aa7d9acc3884f860686c86
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="pre-configuration-database-optimizations"></a><span data-ttu-id="8e510-102">預先設定資料庫最佳化</span><span class="sxs-lookup"><span data-stu-id="8e510-102">Pre-Configuration Database Optimizations</span></span>
<span data-ttu-id="8e510-103">SQL Server 在任何 BizTalk Server 環境中扮演重要的角色，因為它最重要的是 SQL Server 是為了達到最佳效能設定/微調。</span><span class="sxs-lookup"><span data-stu-id="8e510-103">Because of the critical role that SQL Server plays in any BizTalk Server environment, it is of paramount importance that SQL Server be configured/tuned for optimal performance.</span></span> <span data-ttu-id="8e510-104">如果 SQL Server 無法執行也微調，BizTalk Server 所使用的資料庫會成為瓶頸，以及 BizTalk Server 環境的整體效能會降低。</span><span class="sxs-lookup"><span data-stu-id="8e510-104">If SQL Server is not tuned to perform well, then the databases used by BizTalk Server will become a bottleneck and the overall performance of the BizTalk Server environment will suffer.</span></span> <span data-ttu-id="8e510-105">本主題說明安裝 BizTalk Server 和設定 BizTalk Server 資料庫之前，應遵循的數個 SQL Server 效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="8e510-105">This topic describes several SQL Server performance optimizations that should be followed before installing BizTalk Server and configuring the BizTalk Server databases.</span></span>  
  
## <a name="set-ntfs-file-allocation-unit"></a><span data-ttu-id="8e510-106">設定 NTFS 檔案配置單位</span><span class="sxs-lookup"><span data-stu-id="8e510-106">Set NTFS File Allocation Unit</span></span>  
 <span data-ttu-id="8e510-107">SQL Server 會儲存其資料**範圍**，而這是八個實體連續 8 千個頁面或 64 KB 的集合。</span><span class="sxs-lookup"><span data-stu-id="8e510-107">SQL Server stores its data in **Extents**, which are collections of eight physically contiguous 8K pages, or 64 KB.</span></span> <span data-ttu-id="8e510-108">因此，若要將磁碟效能最佳化，NTFS 配置單位大小為 64 KB 「 磁碟組態最佳作法 」 中所述在設定[前置部署 I/O 最佳作法](https://msdn.microsoft.com/library/cc966412.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8e510-108">Therefore, to optimize disk performance, set the NTFS Allocation Unit size to 64KB as described in the “Disk Configuration Best Practices” at  [Predeployment I/O Best Practices](https://msdn.microsoft.com/library/cc966412.aspx).</span></span>  
  
## <a name="considerations-for-the-version-and-edition-of-sql-server"></a><span data-ttu-id="8e510-109">版本與版本的 SQL Server 的考量</span><span class="sxs-lookup"><span data-stu-id="8e510-109">Considerations for the version and edition of SQL Server</span></span>  
 <span data-ttu-id="8e510-110">各種版本和版別的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供不同的功能可能會影響效能，您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="8e510-110">Various versions and editions of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provide different features that can affect the performance of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="8e510-111">例如，在高負載情況適用於 32 位元版本的資料庫鎖定數目[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可能超過即不利的 BizTalk 方案的效能。</span><span class="sxs-lookup"><span data-stu-id="8e510-111">For example, under high-load conditions, the number of database locks that are available for the 32-bit version of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] might be exceeded, which is detrimental to the performance of the BizTalk solution.</span></span> <span data-ttu-id="8e510-112">請考慮罩上的 SQL Server 64 位元版本的 MessageBox 資料庫，如果您在測試環境中發生 「 鎖定不足 」 錯誤。</span><span class="sxs-lookup"><span data-stu-id="8e510-112">Consider housing your MessageBox database on a 64-bit version of SQL Server if you are experiencing "out of lock" errors in your test environment.</span></span> <span data-ttu-id="8e510-113">在 64 位元版本的 SQL Server 上，可用的鎖定數目大幅提高。</span><span class="sxs-lookup"><span data-stu-id="8e510-113">The number of available locks is significantly higher on the 64-bit version of SQL Server.</span></span>  
  
 <span data-ttu-id="8e510-114">決定您將 BizTalk 環境所需的資料庫引擎功能時，請考慮下列資料表。</span><span class="sxs-lookup"><span data-stu-id="8e510-114">Consider the following table when deciding on the database engine features that you will need for your BizTalk environment.</span></span> <span data-ttu-id="8e510-115">針對大規模的企業層級方案需要叢集的支援，BizTalk Server 記錄傳送支援，或 Analysis Services 支援，則您需要 SQL Server Enterprise Edition 主機[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="8e510-115">For large scale, enterprise-level solutions that require clustering support, BizTalk Server log shipping support, or Analysis Services support, then you need SQL Server Enterprise Edition to host the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases.</span></span>   

 <span data-ttu-id="8e510-116">如需完整的 SQL Server 版本所支援的功能清單，請參閱[SQL Server 版本和支援的功能](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="8e510-116">For a complete list of the features supported by the SQL Server editions, see [SQL Server Editions and supported features](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016).</span></span>
  
## <a name="database-planning-considerations"></a><span data-ttu-id="8e510-117">規劃考量的資料庫</span><span class="sxs-lookup"><span data-stu-id="8e510-117">Database planning considerations</span></span>  
 <span data-ttu-id="8e510-118">我們建議您裝載您快速存放裝置 （例如，快速 SAN 磁碟或快速 SCSI 磁碟） 上的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8e510-118">We recommend that you host your SQL Server databases on fast storage (for example, fast SAN disks or fast SCSI disks).</span></span> <span data-ttu-id="8e510-119">因為 raid 5 是撰寫速度較慢，建議 RAID 10 (1 + 0)，而不是 RAID 5。</span><span class="sxs-lookup"><span data-stu-id="8e510-119">We recommend RAID 10 (1+0) instead of RAID 5 since raid 5 is slower at writing.</span></span> <span data-ttu-id="8e510-120">較新的 SAN 磁碟具有非常大量的記憶體快取，因此在這些情況下 raid 選取範圍不是那麼重要。</span><span class="sxs-lookup"><span data-stu-id="8e510-120">Newer SAN disks have very large memory caches, so in these cases the raid selection is not as important.</span></span> <span data-ttu-id="8e510-121">若要增加效能，資料庫和記錄檔案可位於不同實體磁碟上。</span><span class="sxs-lookup"><span data-stu-id="8e510-121">To increase performance, databases and their log files can reside on different physical disks.</span></span>  
  
 <span data-ttu-id="8e510-122">也請考慮調整主機匯流排介面卡 (HBA) 佇列深度，如果使用存放區域網路 (SAN)。</span><span class="sxs-lookup"><span data-stu-id="8e510-122">Also consider tuning the host bus adapter (HBA) queue depth if using a storage area network (SAN).</span></span> <span data-ttu-id="8e510-123">可能會大幅影響 I/O 輸送量，而出的值可能不足以執行 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="8e510-123">This can significantly impact I/O throughput and out-of-the box values can be insufficient for SQL Server.</span></span> <span data-ttu-id="8e510-124">雖然 64 佇列深度通常會獲接受成為很好的起點不存在的任何特定廠商的建議測試，才能決定最佳的值</span><span class="sxs-lookup"><span data-stu-id="8e510-124">Testing is required to determine optimal value, although queue depth of 64 is generally accepted as a good starting point in the absence of any specific vendor recommendations</span></span>  
  
## <a name="install-the-latest-service-pack-and-cumulative-updates-for-sql-server"></a><span data-ttu-id="8e510-125">安裝 SQL Server 的最新 service pack 和累計更新</span><span class="sxs-lookup"><span data-stu-id="8e510-125">Install the latest service pack and cumulative updates for SQL Server</span></span>  
 <span data-ttu-id="8e510-126">安裝 SQL Server，以及最新的.NET Framework 服務組件的最新的 service pack 和最新累計更新。</span><span class="sxs-lookup"><span data-stu-id="8e510-126">Install the latest service packs and the latest cumulative updates for SQL Server as well as the latest .NET Framework service packs.</span></span>  
  
## <a name="install-sql-service-packs-and-cumulative-updates-on-both-biztalk-server-and-sql-server"></a><span data-ttu-id="8e510-127">安裝 BizTalk Server 和 SQL Server 上的 SQL Service Pack 和累計更新</span><span class="sxs-lookup"><span data-stu-id="8e510-127">Install SQL Service Packs and cumulative updates on both BizTalk Server and SQL Server</span></span>  
 <span data-ttu-id="8e510-128">當安裝 SQL Server service pack 或累積更新，也安裝 service pack 或累積更新 BizTalk Server 電腦上。</span><span class="sxs-lookup"><span data-stu-id="8e510-128">When installing service packs or cumulative updates for SQL Server, also install the service pack or cumulative update on the BizTalk Server computer.</span></span> <span data-ttu-id="8e510-129">BizTalk Server 使用 SQL Server service pack 和累計更新所更新的 SQL 用戶端元件。</span><span class="sxs-lookup"><span data-stu-id="8e510-129">BizTalk Server uses SQL Client components that are updated by SQL Server service packs and cumulative updates.</span></span>  
  
## <a name="consider-using-a-fast-solid-state-drive-ssd-to-house-the-sql-server-tembdb"></a><span data-ttu-id="8e510-130">請考慮使用快速固態硬碟 (SSD) 來包含 SQL Server tembdb</span><span class="sxs-lookup"><span data-stu-id="8e510-130">Consider using a fast solid state drive (SSD) to house the SQL Server tembdb</span></span>  
 <span data-ttu-id="8e510-131">請考慮使用一個或多個實心狀態磁碟 (SSD) 磁碟機來存放 TempDB。</span><span class="sxs-lookup"><span data-stu-id="8e510-131">Consider using one or more Solid State Disk (SSD) drives to house the TempDB.</span></span> <span data-ttu-id="8e510-132">SSD 磁碟機提供顯著的效能優於傳統硬碟，並快速地卸除價格進入主要市場。</span><span class="sxs-lookup"><span data-stu-id="8e510-132">SSD drives offer significant performance advantages over traditional hard drives and are quickly dropping in price as they enter mainstream markets.</span></span> <span data-ttu-id="8e510-133">因為 TempDB 效能通常是針對整體的關鍵因素[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]效能，已新增的初始成本的磁碟機將通常會快速原因所增加整體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]效能，特別在執行企業應用程式其[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]效能非常重要。</span><span class="sxs-lookup"><span data-stu-id="8e510-133">Because TempDB performance is often a key factor for overall [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance, the added initial cost of the drives will often be quickly recouped by the overall increased [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance, especially when running enterprise applications for which [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance is critical.</span></span>  
  
## <a name="consider-implementing-the-sql-server-2008-r2-data-collector-and-management-data-warehouse"></a><span data-ttu-id="8e510-134">請考慮實作 SQL Server 2008 R2 資料收集器和管理資料倉儲</span><span class="sxs-lookup"><span data-stu-id="8e510-134">Consider implementing the SQL Server 2008 R2 Data Collector and Management Data Warehouse</span></span>  
 <span data-ttu-id="8e510-135">SQL Server 2008 R2 可容納新的使用資料收集器和管理資料倉儲收集環境/資料庫效能的相關資料以供測試和趨勢分析。</span><span class="sxs-lookup"><span data-stu-id="8e510-135">SQL Server 2008 R2 accommodates the use of the new Data Collector and Management Data Warehouse to collect environment/database performance related data for test and trend analysis.</span></span> <span data-ttu-id="8e510-136">資料收集器會保存到指定的管理資料倉儲收集到的所有資料。</span><span class="sxs-lookup"><span data-stu-id="8e510-136">The Data Collector persists all collected data to the specified Management Data Warehouse.</span></span> <span data-ttu-id="8e510-137">雖然這不是效能最佳化方式，這會是用於分析的任何效能問題。</span><span class="sxs-lookup"><span data-stu-id="8e510-137">While this is not a performance optimization this will be useful for analysis of any performance issues.</span></span>  
  
## <a name="grant-the-account-which-is-used-for-sql-server-the-windows-lock-pages-in-memory-privilege"></a><span data-ttu-id="8e510-138">授與帳戶是用於 SQL Server Windows Lock Pages In 記憶體特殊權限</span><span class="sxs-lookup"><span data-stu-id="8e510-138">Grant the account which is used for SQL Server the Windows Lock Pages In Memory privilege</span></span>  
 <span data-ttu-id="8e510-139">授與 Windows 鎖定記憶體的特殊權限的 SQL Server 服務帳戶中的分頁。</span><span class="sxs-lookup"><span data-stu-id="8e510-139">Grant the Windows Lock Pages in Memory privilege to the SQL Server service account.</span></span> <span data-ttu-id="8e510-140">這樣應該為了防止出 SQL Server 處理序的緩衝區集區記憶體分頁中的 Windows 作業系統，方法是鎖定實體記憶體中緩衝集區配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8e510-140">This should be done to prevent the Windows operating system from paging out the buffer pool memory of the SQL Server process by locking memory that is allocated for the buffer pool in physical memory.</span></span>  
  
 <span data-ttu-id="8e510-141">在我們的實驗室環境，Windows 原則**鎖定記憶體分頁**選項依預設會啟用。</span><span class="sxs-lookup"><span data-stu-id="8e510-141">In our lab environment, the Windows policy **Lock Pages in Memory** option was enabled by default.</span></span> <span data-ttu-id="8e510-142">請參閱[啟用鎖定記憶體分頁選項](https://docs.microsoft.com/sql/database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows)。</span><span class="sxs-lookup"><span data-stu-id="8e510-142">See [Enable the Lock Pages in Memory Option](https://docs.microsoft.com/sql/database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8e510-143">Windows 鎖定分頁記憶體特殊權限授與 SQL Server 服務帳戶時，就會套用特定的限制。</span><span class="sxs-lookup"><span data-stu-id="8e510-143">Certain limitations apply when granting the SQL Server service account the Windows Lock Pages in Memory privilege.</span></span> <span data-ttu-id="8e510-144">請參閱下列內容：</span><span class="sxs-lookup"><span data-stu-id="8e510-144">See the following:</span></span> 
>   
> - [<span data-ttu-id="8e510-145">緩衝集區擴充</span><span class="sxs-lookup"><span data-stu-id="8e510-145">Buffer Pool Extension</span></span>](https://docs.microsoft.com/sql/database-engine/configure-windows/buffer-pool-extension)  
> - [<span data-ttu-id="8e510-146">啟用鎖定記憶體分頁選項</span><span class="sxs-lookup"><span data-stu-id="8e510-146">Enable the Lock Pages in Memory Option </span></span>](https://docs.microsoft.com/sql/database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows)  
  
## <a name="grant-the-semanagevolumename-right-to-the-sql-server-service-account"></a><span data-ttu-id="8e510-147">由右至 SQL Server 服務帳戶授與 SE_MANAGE_VOLUME_NAME</span><span class="sxs-lookup"><span data-stu-id="8e510-147">Grant the SE_MANAGE_VOLUME_NAME right to the SQL Server Service Account</span></span>  
 <span data-ttu-id="8e510-148">請執行 SQL Server 服務帳戶具有 '執行磁碟區維護工作' Windows 權限，或確定它所屬的群組。</span><span class="sxs-lookup"><span data-stu-id="8e510-148">Ensure the account running the SQL Server service has the ‘Perform Volume Maintenance Tasks’ Windows privilege or ensure it belongs to a group that does.</span></span> <span data-ttu-id="8e510-149">如果資料庫自動成長，這可讓檔案立即初始化確保最佳效能。</span><span class="sxs-lookup"><span data-stu-id="8e510-149">This will allow instant file Initialization ensuring optimum performance if a database has to Auto-grow.</span></span>  
  
## <a name="set-min-and-max-server-memory"></a><span data-ttu-id="8e510-150">設定 Min 和 Max Server Memory</span><span class="sxs-lookup"><span data-stu-id="8e510-150">Set Min and Max Server Memory</span></span>  
 <span data-ttu-id="8e510-151">SQL Server 電腦裝載 BizTalk Server 資料庫應該專用於執行 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="8e510-151">The computers running SQL Server that host the BizTalk Server databases should be dedicated to running SQL Server.</span></span> <span data-ttu-id="8e510-152">當該主控件執行 SQL Server 之電腦的 BizTalk Server 資料庫專用於執行 SQL Server 時，我們建議的最小伺服器記憶體' 和 '最大伺服器記憶體選項，每個 SQL Server 執行個體上的設定指定的固定的記憶體數量配置給 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="8e510-152">When the computers running SQL Server that host the BizTalk Server databases are dedicated to running SQL Server, we recommend that the 'min server memory' and 'max server memory' options on each SQL Server instance are set to specify the fixed amount of memory to allocate to SQL Server.</span></span> <span data-ttu-id="8e510-153">在此情況下，您應該設定的 「 最小伺服器記憶體 」 和 「 最大伺服器記憶體 」 為相同的值 （等於 SQL Server 將使用的實體記憶體的最大數量）。</span><span class="sxs-lookup"><span data-stu-id="8e510-153">In this case, you should set the “min server memory” and “max server memory” to the same value (equal to the maximum amount of physical memory that SQL Server will use).</span></span> <span data-ttu-id="8e510-154">這會降低額外負荷，否則會以動態方式管理這些值的 SQL Server 所使用。</span><span class="sxs-lookup"><span data-stu-id="8e510-154">This will reduce overhead that would otherwise be used by SQL Server dynamically managing these values.</span></span> <span data-ttu-id="8e510-155">每個執行 SQL Server，來指定要配置給 SQL Server 記憶體的固定的數量的電腦上執行下列 T-SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="8e510-155">Run the following T-SQL commands on each computer running SQL Server to specify the fixed amount of memory to allocate to SQL Server:</span></span>  
  
```  
sp_configure ‘Max Server memory (MB)’,(max size in MB)  
sp_configure ‘Min Server memory (MB)’,(min size in MB)  
```  
  
 <span data-ttu-id="8e510-156">您為 SQL Server 的記憶體數量之前，判斷適當的記憶體設定減去總實體記憶體的 Windows Server 所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8e510-156">Before you set the amount of memory for SQL Server, determine the appropriate memory setting by subtracting the memory required for Windows Server from the total physical memory.</span></span> <span data-ttu-id="8e510-157">這是您可以指派給 SQL Server 記憶體的最大數量。</span><span class="sxs-lookup"><span data-stu-id="8e510-157">This is the maximum amount of memory you can assign to SQL Server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e510-158">如果該主控件執行 SQL Server 之電腦的 BizTalk Server 資料庫也會裝載企業單一登入主要密碼伺服器，則您可能需要調整此值，以確保有足夠的記憶體可用來執行企業單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="8e510-158">If the computers running SQL Server that host the BizTalk Server databases also host the Enterprise Single Sign-On Master Secret Server, then you may need to adjust this value to ensure that there is sufficient memory available to run the Enterprise Single Sign-On Service.</span></span> <span data-ttu-id="8e510-159">它不是一般的做法，在 SQL Server 叢集以提供高可用性的主要密碼伺服器上執行 「 企業單一登入服務的叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="8e510-159">It is not an uncommon practice to run a clustered instance of the Enterprise Single Sign-On service on a SQL Server cluster to provide high availability for the Master Secret Server.</span></span> <span data-ttu-id="8e510-160">請參閱[叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)</span><span class="sxs-lookup"><span data-stu-id="8e510-160">See [Clustering the Master Secret Server](../technical-guides/clustering-the-master-secret-server.md)</span></span>  
  
## <a name="split-the-tempdb-database-into-multiple-data-files-of-equal-size-on-each-sql-server-instance-used-by-biztalk-server"></a><span data-ttu-id="8e510-161">分割成多個資料檔相同大小的 BizTalk Server 使用的每個 SQL Server 執行個體上的 tempdb 資料庫</span><span class="sxs-lookup"><span data-stu-id="8e510-161">Split the tempdb database into multiple data files of equal size on each SQL Server instance used by BizTalk Server</span></span>  
 <span data-ttu-id="8e510-162">用於 tempdb 資料檔案皆相同大小的很重要，因為 SQL Server 所使用的比例式填滿演算法為基礎的資料檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="8e510-162">Ensuring that the data files used for the tempdb are of equal size is critical because the proportional fill algorithm used by SQL Server is based on the size of the data files.</span></span> <span data-ttu-id="8e510-163">建立資料檔的大小不相等，如果比例填滿演算法會使用最大的多個 GAM 配置，而不是分配的配置之間的所有檔案，藉以定義建立多個資料檔案的目的檔案。</span><span class="sxs-lookup"><span data-stu-id="8e510-163">If data files are created with unequal sizes, the proportional fill algorithm will use the largest file more for GAM allocations rather than spreading the allocations between all the files, thereby defeating the purpose of creating multiple data files.</span></span> <span data-ttu-id="8e510-164">最佳的 tempdb 資料檔案數目取決於 tempdb 中所見的閂鎖競爭的程度。</span><span class="sxs-lookup"><span data-stu-id="8e510-164">The optimal number of tempdb data files depends on the degree of latch contention seen in tempdb.</span></span> <span data-ttu-id="8e510-165">為一般的經驗法則，資料檔案數目應該等於數字的處理器核心/Cpu 的 Cpu 數目，為 8 或更少。</span><span class="sxs-lookup"><span data-stu-id="8e510-165">As a general rule of thumb, the number of data files should be equal to number of processor cores/CPUs where number of CPUs is 8 or less.</span></span> <span data-ttu-id="8e510-166">針對具有超過 8 個 Cpu 的伺服器，建立資料檔案的一半的 Cpu 數目 （一次，僅有閂鎖競爭）。</span><span class="sxs-lookup"><span data-stu-id="8e510-166">For servers with more than 8 CPUs, create data files for half the number of CPUs (again, only you have latch contention).</span></span>  
  
 <span data-ttu-id="8e510-167">在實驗室環境中，我們可以使用下列指令碼來建立其中每個的檔案大小為 1024 MB，成長 100 MB 的 8 個 TempDB 資料檔案和使用 100 MB 成長 512 MB 的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8e510-167">In our lab environment, we used the script below to create 8 TempDB data files each of which had a file size of 1024 MB with 100 MB growth and a log file of 512 MB with 100 MB growth.</span></span> <span data-ttu-id="8e510-168">資料檔案移到磁碟機 H:%M 和記錄檔會移至 i： 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8e510-168">The data files are moved to drive H: and log file are moved to drive I:.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8e510-169">此指令碼為 「 現況，「 僅供示範或教育目的，且提供用於風險自負。</span><span class="sxs-lookup"><span data-stu-id="8e510-169">This script is provided “as is,” is intended for demo or educational purposes only, and is to be used at your own risk.</span></span> <span data-ttu-id="8e510-170">使用此指令碼不支援的 Microsoft，Microsoft 不會對不保證此指令碼的適用性。</span><span class="sxs-lookup"><span data-stu-id="8e510-170">Use of this script is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this script.</span></span>  
  
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
  
 <span data-ttu-id="8e510-171">使用 SQL Server 2008 活動監視器] 或 [SQL Server 2005 績效儀表板報告中所述[監視 SQL Server 效能](../technical-guides/monitoring-sql-server-performance.md)來識別閂鎖競爭問題。</span><span class="sxs-lookup"><span data-stu-id="8e510-171">Use the SQL Server 2008 Activity Monitor or the SQL Server 2005 Performance Dashboard Reports described in [Monitoring SQL Server Performance](../technical-guides/monitoring-sql-server-performance.md) to identify problems with latch contention.</span></span>  
  
## <a name="manually-set-sql-server-process-affinity"></a><span data-ttu-id="8e510-172">手動設定 SQL Server 處理序相似性</span><span class="sxs-lookup"><span data-stu-id="8e510-172">Manually set SQL Server Process Affinity</span></span>  
 <span data-ttu-id="8e510-173">處理序相似性選項可以提供高階的企業級非 NUMA 擁有 16 顆以上 Cpu 的電腦上執行的 SQL Server 環境的效能增強功能。</span><span class="sxs-lookup"><span data-stu-id="8e510-173">The Process Affinity option can provide performance enhancements in high-end, enterprise-level SQL Server environments that are running on non-NUMA computers with 16 or more CPUs.</span></span> <span data-ttu-id="8e510-174">特別是在您共用 MessageBox 資料庫中的資料表有競爭的高輸送量 BizTalk 環境中。</span><span class="sxs-lookup"><span data-stu-id="8e510-174">This is especially true in high-throughput BizTalk environments where you have contention on shared tables in the MessageBox database.</span></span> <span data-ttu-id="8e510-175">因為我們的實驗室環境中所使用的 SQL Server 電腦未啟用 NUMA 的而且具有 16 個核心，來最佳化效能，我們會用來設定處理序相似性的下列命令：</span><span class="sxs-lookup"><span data-stu-id="8e510-175">Because the SQL Server computers that were used in our lab environment were not NUMA-enabled and had 16 cores, to optimize performance, we used the commands below to set process affinity:</span></span>  
  
 <span data-ttu-id="8e510-176">**若要手動設定 SQL Server 處理序相似性從 0 到 15**</span><span class="sxs-lookup"><span data-stu-id="8e510-176">**To manually set the SQL Server Process Affinity from 0 to 15**</span></span>  
  
```  
ALTER SERVER CONFIGURATION  
SET PROCESS AFFINITY CPU = 0 to 15  
```  
  
 <span data-ttu-id="8e510-177">如需詳細資訊，請參閱[ALTER SERVER CONFIGURATION (TRANSACT-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-server-configuration-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8e510-177">For more information, see [ALTER SERVER CONFIGURATION (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-server-configuration-transact-sql).</span></span>
  
## <a name="configure-msdtc"></a><span data-ttu-id="8e510-178">設定 MSDTC</span><span class="sxs-lookup"><span data-stu-id="8e510-178">Configure MSDTC</span></span>  
 <span data-ttu-id="8e510-179">若要簡化 SQL Server 與 BizTalk Server 之間的交易，您必須啟用 Microsoft 分散式交易協調器 (MS DTC)。</span><span class="sxs-lookup"><span data-stu-id="8e510-179">To facilitate transactions between SQL Server and BizTalk Server, you must enable Microsoft Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="8e510-180">若要在 SQL Server 上設定 MSDTC，請參閱主題[改善作業系統效能的一般指導方針](../technical-guides/general-guidelines-for-improving-operating-system-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="8e510-180">To configure MSDTC on SQL Server, see the topic [General Guidelines for Improving Operating System Performance](../technical-guides/general-guidelines-for-improving-operating-system-performance.md).</span></span>  
  
## <a name="enable-trace-flag-t1118-as-a-startup-parameter-for-all-instances-of-sql-server"></a><span data-ttu-id="8e510-181">啟用追蹤旗標 T1118 作為啟動參數，所有執行個體的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="8e510-181">Enable Trace Flag T1118 as a startup parameter for all instances of SQL Server</span></span>  
 <span data-ttu-id="8e510-182">實作追蹤旗標-T1118 有助於減少 SQL Server 執行個體之間的競爭，藉由移除幾乎所有的單一頁面配置。</span><span class="sxs-lookup"><span data-stu-id="8e510-182">Implementing Trace Flag –T1118 helps reduce contention across the SQL Server instances by removing almost all single page allocations.</span></span> <span data-ttu-id="8e510-183">如需詳細資訊，請參閱[KB 328551: PRB: tempdb 資料庫的並行存取增強功能](https://support.microsoft.com/help/328551/concurrency-enhancements-for-the-tempdb-database)。</span><span class="sxs-lookup"><span data-stu-id="8e510-183">For more information, see [KB 328551: PRB: Concurrency enhancements for the tempdb database](https://support.microsoft.com/help/328551/concurrency-enhancements-for-the-tempdb-database).</span></span>
  
## <a name="do-not-change-default-sql-server-settings-for-max-degree-of-parallelism-sql-server-statistics-or-database-index-rebuilds-and-defragmentation"></a><span data-ttu-id="8e510-184">請勿變更預設 SQL Server 設定平行處理原則、 SQL Server 統計資料，或資料庫索引會重建和重組的最大程度</span><span class="sxs-lookup"><span data-stu-id="8e510-184">Do not change default SQL Server settings for max degree of parallelism, SQL Server statistics, or database index rebuilds and defragmentation</span></span>  
 <span data-ttu-id="8e510-185">如果 SQL Server 執行個體將裝載 BizTalk Server 資料庫，會有某些不應該變更的 SQL Server 設定。</span><span class="sxs-lookup"><span data-stu-id="8e510-185">If a SQL Server instance will house BizTalk Server databases, then there are certain SQL Server settings that should not be changed.</span></span> <span data-ttu-id="8e510-186">具體來說，SQL Server max degree of parallelism，MessageBox 資料庫，以及設定資料庫索引的 SQL Server 統計資料會重建，並不能修改磁碟重組。</span><span class="sxs-lookup"><span data-stu-id="8e510-186">Specifically, the SQL Server max degree of parallelism, the SQL Server statistics on the MessageBox database, and the settings for the database index rebuilds and defragmentation should not be modified.</span></span> <span data-ttu-id="8e510-187">請參閱[不應該變更的 SQL Server 設定](../technical-guides/sql-server-settings-that-should-not-be-changed.md)。</span><span class="sxs-lookup"><span data-stu-id="8e510-187">See [SQL Server Settings That Should Not Be Changed](../technical-guides/sql-server-settings-that-should-not-be-changed.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8e510-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e510-188">See Also</span></span>  
 [<span data-ttu-id="8e510-189">最佳化資料庫效能</span><span class="sxs-lookup"><span data-stu-id="8e510-189">Optimizing Database Performance</span></span>](../technical-guides/optimizing-database-performance.md)
