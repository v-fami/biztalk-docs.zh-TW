---
title: "BizTalk Server 效能疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dbf21fb9-1ae1-48b5-a65a-e96839b23945
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df98f717c71198d4be6f8d13eaa539e5c1e16786
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-performance"></a><span data-ttu-id="5a1b0-102">BizTalk Server 效能疑難排解</span><span class="sxs-lookup"><span data-stu-id="5a1b0-102">Troubleshooting BizTalk Server Performance</span></span>
<span data-ttu-id="5a1b0-103">本節所包含的一般指導方針，可用於診斷及解決與 BizTalk 傳訊引擎相關的效能問題。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-103">This section contains general guidelines for diagnosing and resolving performance problems related to the BizTalk Messaging Engine.</span></span>  
  
## <a name="estimating-document-processing-requirements"></a><span data-ttu-id="5a1b0-104">估計文件處理需求</span><span class="sxs-lookup"><span data-stu-id="5a1b0-104">Estimating Document Processing Requirements</span></span>  
 <span data-ttu-id="5a1b0-105">在生產環境中部署解決方案之前，請先進行計劃及測試，以決定傳訊引擎的效能需求。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-105">Plan and test to determine your Messaging Engine performance needs before deploying your solution into a production environment.</span></span> <span data-ttu-id="5a1b0-106">這有助於正確地建置 BizTalk Server 和 SQL Server 的環境。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-106">This will help you build out your BizTalk Server and SQL Server environments appropriately.</span></span>  
  
1.  <span data-ttu-id="5a1b0-107">計劃與任何容錯或備份及復原需求相關的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-107">Plan for overhead associated with any fault tolerance or backup and recovery needs</span></span>  
  
    -   <span data-ttu-id="5a1b0-108">SQL Server 磁碟會設定為 RAID 陣列嗎？</span><span class="sxs-lookup"><span data-stu-id="5a1b0-108">Will the SQL Server disks be configured as RAID arrays?</span></span>  
  
    -   <span data-ttu-id="5a1b0-109">會對 BizTalk 主控件、SQL Server 或企業單一登入套用 Windows 叢集嗎？</span><span class="sxs-lookup"><span data-stu-id="5a1b0-109">Will Windows Clustering be used for BizTalk Hosts, SQL Server, or Enterprise Single Sign-On?</span></span> <span data-ttu-id="5a1b0-110">如需詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-110">For more information see [Planning for High Availability](../core/planning-for-high-availability3.md).</span></span>  
  
    -   <span data-ttu-id="5a1b0-111">會使用網路負載平衡嗎？</span><span class="sxs-lookup"><span data-stu-id="5a1b0-111">Will Network Load Balancing be used?</span></span>  
  
    -   <span data-ttu-id="5a1b0-112">環境的備份及復原需求為何？</span><span class="sxs-lookup"><span data-stu-id="5a1b0-112">What are the backup and recovery requirements for the environment?</span></span> <span data-ttu-id="5a1b0-113">如需詳細資訊，請參閱[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-113">For more information, see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md).</span></span>  
  
2.  <span data-ttu-id="5a1b0-114">請依照下列中的指導方針[規劃維持效能](../core/planning-for-sustained-performance.md)計劃、 測試及調整您的 BizTalk Server 和 SQL Server 環境。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-114">Follow the guidelines in [Planning for Sustained Performance](../core/planning-for-sustained-performance.md) to plan, test, and scale your BizTalk Server and SQL Server environment.</span></span>  
  
3.  <span data-ttu-id="5a1b0-115">請依照下列中的指導方針[追蹤效能特性](../core/tracking-performance-characteristics.md)計劃與文件追蹤需求相關的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-115">Follow the guidelines in [Tracking Performance Characteristics](../core/tracking-performance-characteristics.md) to plan for overhead associated with document tracking requirements.</span></span>  
  
## <a name="optimizing-an-existing-biztalk-server-environment"></a><span data-ttu-id="5a1b0-116">最佳化現有的 BizTalk Server 環境</span><span class="sxs-lookup"><span data-stu-id="5a1b0-116">Optimizing an Existing BizTalk Server Environment</span></span>  
 <span data-ttu-id="5a1b0-117">請遵循以下步驟來最佳化現有的 BizTalk Server 環境：</span><span class="sxs-lookup"><span data-stu-id="5a1b0-117">Follow these steps to optimize an existing BizTalk Server environment:</span></span>  
  
1.  <span data-ttu-id="5a1b0-118">請依照下列中的指導方針[識別效能瓶頸](../core/identifying-performance-bottlenecks.md)能找出可能的瓶頸，BizTalk Server 環境中。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-118">Follow the guidelines in [Identifying Performance Bottlenecks](../core/identifying-performance-bottlenecks.md) to pinpoint possible bottlenecks in your BizTalk Server environment.</span></span>  
  
2.  <span data-ttu-id="5a1b0-119">請依照下列中的指導方針[最佳化資源使用量透過主控件節流](../core/optimizing-resource-usage-through-host-throttling.md)至 BizTalk Server 環境的文件輸送量最大化。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-119">Follow the guidelines in [Optimizing Resource Usage Through Host Throttling](../core/optimizing-resource-usage-through-host-throttling.md) to maximize document throughput for the BizTalk Server environment.</span></span>  
  
3.  <span data-ttu-id="5a1b0-120">請考慮修改參數記載於[組態參數會影響配接器效能](../core/configuration-parameters-that-affect-adapter-performance.md)將配接器在某些情況下的效能最大化。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-120">Consider modifying the parameters documented in [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md) to maximize adapter performance in certain scenarios.</span></span>  
  
4.  <span data-ttu-id="5a1b0-121">請依照下列中的指導方針[如何 BizTalk Server 處理大型訊息](../core/how-biztalk-server-processes-large-messages.md)時處理大型訊息 (超過 100 MB) 最佳化傳訊引擎的效能。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-121">Follow the guidelines in [How BizTalk Server Processes Large Messages](../core/how-biztalk-server-processes-large-messages.md) to optimize Messaging Engine performance when processing Large Messages (more than 100 MB).</span></span>  
  
5.  <span data-ttu-id="5a1b0-122">針對傳送配接器、接收配接器和協調流程，建立個別的主控件和主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-122">Create separate hosts and host instances for send adapters, receive adapters, and orchestrations.</span></span> <span data-ttu-id="5a1b0-123">這樣可為每個配接器提供個別的主控件執行個體以在其中執行，並可確保配接器不會對其他的配接器造成不利的影響。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-123">This will give each adapter a separate host instance to run in and will ensure that one adapter does not adversely affect another.</span></span> <span data-ttu-id="5a1b0-124">由於主控件節流設定是設定於主控件層級，所以將處理邏輯區分到不同主控件的做法，也可讓您根據每個主控件的處理需求來設定節流。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-124">Since host throttling settings are configurable at the host level, the separation of processing logic into different hosts will also permit you to configure throttling settings based upon the processing requirements of each host.</span></span>  
  
## <a name="diagnosing-performance-problems-in-an-existing-biztalk-server-environment"></a><span data-ttu-id="5a1b0-125">在現有 BizTalk Server 環境中診斷效能問題</span><span class="sxs-lookup"><span data-stu-id="5a1b0-125">Diagnosing Performance Problems in an Existing BizTalk Server Environment</span></span>  
 <span data-ttu-id="5a1b0-126">一般而言，效能問題可以縮小至下列其中一個 BizTalk Server 環境元件：</span><span class="sxs-lookup"><span data-stu-id="5a1b0-126">Typically a performance problem can be narrowed down to one of the following components of a BizTalk Server environment:</span></span>  
  
-   <span data-ttu-id="5a1b0-127">接收配接器，或是配接器從其接收文件的系統。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-127">A receive adapter or the system that the adapter is receiving documents from.</span></span> <span data-ttu-id="5a1b0-128">例如，如果文件是由 HTTP 配接器以低於最佳速率的方式所接收，則問題可能出在 HTTP 接收配接器，或是張貼到 HTTP 配接器的用戶端。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-128">For example if documents are being received by the HTTP adapter at a suboptimal rate then the problem may be with the HTTP receive adapter or with the client that is posting to the HTTP adapter.</span></span>  
  
-   <span data-ttu-id="5a1b0-129">協調流程服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-129">An orchestration service instance.</span></span>  
  
-   <span data-ttu-id="5a1b0-130">裝載 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫之 Microsoft SQL Server 的效能。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-130">Performance of the Microsoft SQL server that houses the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
-   <span data-ttu-id="5a1b0-131">傳送配接器，或是配接器將文件傳送至的系統。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-131">A send adapter or the system that the adapter is sending documents to.</span></span> <span data-ttu-id="5a1b0-132">例如，如果文件是由 SQL 配接器以低於最佳速率的方式所傳送，則問題可能出在 SQL 傳送配接器，或是執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 而 SQL 配接器正在更新的電腦。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-132">For example if documents are being sent by the SQL adapter at a suboptimal rate then the problem may be with the SQL send adapter or with the computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that the SQL adapter is updating.</span></span>  
  
 <span data-ttu-id="5a1b0-133">請使用下列指導方針，以協助辨識效能不佳的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境元件：</span><span class="sxs-lookup"><span data-stu-id="5a1b0-133">Use the following guidelines to help identify the components of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment that are performing poorly:</span></span>  
  
-   <span data-ttu-id="5a1b0-134">請擷取在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 事件檢視器中產生的警告或錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-134">Capture any warnings or errors generated in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Event Viewer.</span></span>  
  
-   <span data-ttu-id="5a1b0-135">請依照[識別效能瓶頸](../core/identifying-performance-bottlenecks.md)，找出效能瓶頸。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-135">Follow the steps in [Identifying Performance Bottlenecks](../core/identifying-performance-bottlenecks.md) to help identify performance bottlenecks.</span></span>  
  
 <span data-ttu-id="5a1b0-136">一旦辨識出效能不佳的元件後，請遵循正確的指導方針來協助解決問題：</span><span class="sxs-lookup"><span data-stu-id="5a1b0-136">Once the poorly performing component has been identified, follow the appropriate guidelines to help resolve the issue:</span></span>  
  
 <span data-ttu-id="5a1b0-137">**解決與傳送和接收配接器相關的效能問題的指導方針**</span><span class="sxs-lookup"><span data-stu-id="5a1b0-137">**Guidelines for resolving performance problems related to send and receive adapters**</span></span>  
  
-   <span data-ttu-id="5a1b0-138">請參閱[疑難排解 BizTalk Server 配接器](../core/troubleshooting-biztalk-server-adapters.md)以疑難排解問題的一般資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-138">See [Troubleshooting BizTalk Server Adapters](../core/troubleshooting-biztalk-server-adapters.md) for general information to troubleshoot problems with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters.</span></span> <span data-ttu-id="5a1b0-139">本節包含一般的疑難排解資訊，其中包含以下項目的相關資訊：如何設定特定配接器的記錄、可用來診斷網路問題的資訊、MSDTC 問題、登錄問題、檔案系統問題以及 IIS 問題等。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-139">This section contains general troubleshooting information including information about how to set up logging for certain adapters and information that can be used diagnose network problems, problems with MSDTC, problems with the registry, problems with the file system, and problems with IIS.</span></span>  
  
-   <span data-ttu-id="5a1b0-140">請參閱適當的[疑難排解 BizTalk Server 相依性](../core/troubleshooting-biztalk-server-dependencies.md)如需如何疑難排解 MSDTC、 憑證、 企業單一登入，一般資訊和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-140">See the appropriate section of [Troubleshooting BizTalk Server Dependencies](../core/troubleshooting-biztalk-server-dependencies.md) for general information to troubleshoot problems with MSDTC, Certificates, Enterprise Single Sign-On, and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5a1b0-141">**解決與協調流程相關的效能問題的指導方針**</span><span class="sxs-lookup"><span data-stu-id="5a1b0-141">**Guidelines for resolving performance problems related to orchestrations**</span></span>  
  
-   <span data-ttu-id="5a1b0-142">修改 BTSNTSvc.exe.config 檔案中所述之適當章節[協調流程引擎組態](../core/orchestration-engine-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-142">Modify the appropriate sections of the BTSNTSvc.exe.config file documented in [Orchestration Engine Configuration](../core/orchestration-engine-configuration.md).</span></span>  
  
 <span data-ttu-id="5a1b0-143">**解決 SQL Server 相關的效能問題的指導方針**</span><span class="sxs-lookup"><span data-stu-id="5a1b0-143">**Guidelines for resolving performance problems related to SQL Server**</span></span>  
  
-   <span data-ttu-id="5a1b0-144">SQL Server Profiler 可以用來擷取傳送至 SQL Server 的 Transact-SQL 陳述式，以及這些陳述式的 SQL Server 結果集。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-144">SQL Server Profiler can be used to capture Transact-SQL statements that are sent to SQL Server and the SQL Server result sets from these statements.</span></span> <span data-ttu-id="5a1b0-145">由於 BizTalk Server 已緊密地與 SQL Server 整合，因此 SQL Server Profiler 追蹤的分析是相當有用的工具，可用於分析讀取和寫入 SQL Server 資料庫時 BizTalk Server 中可能發生的問題。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-145">Since BizTalk Server is tightly integrated with SQL Server, the analysis of a SQL Server Profile trace can be a useful tool for analyzing problems that may occur in BizTalk Server when reading from and writing to SQL Server databases.</span></span> <span data-ttu-id="5a1b0-146">如需有關如何使用 SQL Server Profiler 的詳細資訊，請參閱 SQL Server 說明文件。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-146">For information about how to use SQL Server Profiler see the SQL Server documentation.</span></span>  
  
-   <span data-ttu-id="5a1b0-147">[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] 查詢編輯器可以用來直接對 SQL Server 資料庫執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-147">The [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] Query Editor can be used to execute SQL statements directly against SQL Server databases.</span></span> <span data-ttu-id="5a1b0-148">在某些情況中，這個功能可能有助於查詢 BizTalk Server 資料庫或更新 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-148">This functionality may be useful for querying the BizTalk Server databases or for updating the BizTalk Server databases in certain scenarios.</span></span> <span data-ttu-id="5a1b0-149">如需查詢編輯器的相關資訊，請參閱 [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] 說明文件。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-149">For more information about Query Editor see the [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] documentation.</span></span>  
  
-   <span data-ttu-id="5a1b0-150">檢閱[疑難排解 SQL Server](../core/troubleshooting-sql-server.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5a1b0-150">Review [Troubleshooting SQL Server](../core/troubleshooting-sql-server.md) for additional information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a1b0-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a1b0-151">See Also</span></span>  
 [<span data-ttu-id="5a1b0-152">疑難排解</span><span class="sxs-lookup"><span data-stu-id="5a1b0-152">Troubleshooting</span></span>](../core/troubleshooting.md)