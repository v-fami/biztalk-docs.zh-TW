---
title: "管理 BAM 事件匯流排服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MessageBox database, migrating data
- Primary Import database [BAM], migrating data
- migrating, data [BAM]
- managing [BAM], Event Bus Service
- Event Bus Service [BAM], managing
- Tracking Data Decode Service (TDDS)
ms.assetid: 556e7fe2-4a7d-46f6-8e55-f41be4e666dc
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f265201e371a86072c06b336b4d00bb1742f5f6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-the-bam-event-bus-service"></a><span data-ttu-id="278f5-102">管理 BAM 事件匯流排服務</span><span class="sxs-lookup"><span data-stu-id="278f5-102">Managing the BAM Event Bus Service</span></span>
<span data-ttu-id="278f5-103">BAM 事件匯流排服務也稱為「追蹤資料解碼服務」(TDDS)，會處理儲存在來源資料庫中的追蹤資料 (資料流)，並以方便日後查詢的格式保存該資料。</span><span class="sxs-lookup"><span data-stu-id="278f5-103">The BAM Event Bus Service, also known as the Tracking Data Decode Service (TDDS), processes tracking data (streams) stored in a source database and persists that data in such a way that it is easy to query it at a later date.</span></span>  
  
 <span data-ttu-id="278f5-104">BAM 事件匯流排服務會將商務智慧資料移至 BAM 主要匯入資料庫，並將 BizTalk 狀況監控資料移至 DTA 資料庫。</span><span class="sxs-lookup"><span data-stu-id="278f5-104">The BAM Event Bus service moves Business intelligence data to the BAM Primary Import database and BizTalk Health Monitoring data to the DTA database.</span></span> <span data-ttu-id="278f5-105">BAM 事件匯流排服務在 BizTalk 服務中以子服務方式執行。</span><span class="sxs-lookup"><span data-stu-id="278f5-105">The BAM Event Bus service runs as a sub-service within the BizTalk service.</span></span>  
  
 <span data-ttu-id="278f5-106">您可以藉由收集執行期間的事件資料，然後將資料以應用程式狀態暫時儲存在相同資料庫 (例如 MessageBox 資料庫)，以監控交易應用程式的活動，例如 Microsoft BizTalk® Server。</span><span class="sxs-lookup"><span data-stu-id="278f5-106">You monitor the activities of a transactional application, such as Microsoft BizTalk® Server, by collecting event data during execution, and then temporarily storing the data in the same database as the application state—for example, the MessageBox database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="278f5-107">請避免在相同電腦上建立一個以上控制追蹤不同 BizTalk 群組的應用程式執行個體。</span><span class="sxs-lookup"><span data-stu-id="278f5-107">Avoid creating more than one application instance that hosts tracking for different BizTalk Groups on the same computer.</span></span> <span data-ttu-id="278f5-108">如果追蹤不同 BizTalk 群組的執行個體存在同一部電腦上，您將無法辨別哪個事件屬於哪個 BizTalk 群組，在 BizTalk 管理主控台或事件記錄檔中所有的 BizTalk 群組會顯示具有相同名稱。</span><span class="sxs-lookup"><span data-stu-id="278f5-108">If instances that track different BizTalk Groups exist on the same computer, you will not be able to distinguish which events belong to which BizTalk Groups in the BizTalk Administration Console or in the event log because all BizTalk Groups are displayed with the same name.</span></span>  
  
 <span data-ttu-id="278f5-109">BAM 事件匯流排服務可讀取事件資料、將資料解碼並儲存至 Microsoft SQL Server?資料庫，您可以在其中輕鬆地查詢資料。</span><span class="sxs-lookup"><span data-stu-id="278f5-109">The BAM Event Bus service reads the event data, decodes it, and then stores it in a Microsoft SQL Server™ database, where you can easily query the data.</span></span>  
  
 <span data-ttu-id="278f5-110">BAM 事件匯流排服務提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="278f5-110">The BAM Event Bus service provides the following advantages:</span></span>  
  
-   <span data-ttu-id="278f5-111">事件資料永遠符合應用程式的狀態，並且絕不會公開未認可的進度。</span><span class="sxs-lookup"><span data-stu-id="278f5-111">Event data always matches the state of the application, and it never exposes uncommitted progress.</span></span>  
  
-   <span data-ttu-id="278f5-112">對執行中應用程式造成的效能影響最小，因為事件資料會在相同本機交易中儲存如同應用程式狀態變更時所儲存少數的記錄。</span><span class="sxs-lookup"><span data-stu-id="278f5-112">Performance impact on the running application is minimal because the event data saves as few records in the same local transaction as the application state change.</span></span>  
  
-   <span data-ttu-id="278f5-113">應用程式狀態的 SQL Server 儲存體已針對執行效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="278f5-113">SQL Server storage for the application state is further optimized for execution performance.</span></span> <span data-ttu-id="278f5-114">資料是由 TDDS 解碼後儲存至另一個資料庫，可能是 BAM 主要匯入資料庫或 DTA 資料庫。</span><span class="sxs-lookup"><span data-stu-id="278f5-114">The data is decoded by TDDS and stored in a separate database, either the BAM Primary import database or the DTA database.</span></span> <span data-ttu-id="278f5-115">報表的產生則是從此資料庫查詢資料的結果，所以不會影響到儲存應用程式狀態的 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="278f5-115">When reports are generated the data is queried from the database and does impact the Message Box database, which stores the application state.</span></span>  
  
-   <span data-ttu-id="278f5-116">使用您可以查詢的形式儲存事件資料不是在應用程式伺服器和資料庫中完成的，</span><span class="sxs-lookup"><span data-stu-id="278f5-116">The work to store the event data in a form that you can query is not done in the application servers and databases.</span></span> <span data-ttu-id="278f5-117">它被卸載至執行 BAM 事件匯流排服務和目的 SQL Server 資料庫的電腦。</span><span class="sxs-lookup"><span data-stu-id="278f5-117">It is offloaded to the machines that run the BAM Event Bus service and the Destination SQL Server database.</span></span>  
  
-   <span data-ttu-id="278f5-118">事件資料採低延遲的方式處理，以致 TDDS 查詢程序更加迅速。</span><span class="sxs-lookup"><span data-stu-id="278f5-118">Event data is processed with low latency which allows TDDS queries process faster.</span></span> <span data-ttu-id="278f5-119">BAM 事件匯流排服務會協調資源以達到最小的可能延遲。</span><span class="sxs-lookup"><span data-stu-id="278f5-119">The BAM Event Bus services coordinate their resources to achieve the minimum possible latency.</span></span>  
  
 <span data-ttu-id="278f5-120">BAM 事件匯流排伺服器使用包含組態資訊的中央資料庫連線，以協調資源。</span><span class="sxs-lookup"><span data-stu-id="278f5-120">The BAM Event Bus server coordinates its resources by using a connection to a central database, which contains the configuration information.</span></span> <span data-ttu-id="278f5-121">每個作用中的 BAM 事件匯流排服務會每分鐘傳送訊息至中央資料庫，而中央資料庫包含 BAM 事件匯流排服務在該時間點的狀態。</span><span class="sxs-lookup"><span data-stu-id="278f5-121">Every minute, each active BAM Event Bus service sends a message to the central database, which contains the state of the BAM Event Bus service at that point in time.</span></span>  
  
 <span data-ttu-id="278f5-122">此訊息稱為活動訊號訊息。</span><span class="sxs-lookup"><span data-stu-id="278f5-122">This message is referred to as a heartbeat message.</span></span> <span data-ttu-id="278f5-123">每個 BAM 事件匯流排服務也會檢查是否有需要完成的新工作。</span><span class="sxs-lookup"><span data-stu-id="278f5-123">Each BAM Event Bus service also checks for new work that needs to be done.</span></span> <span data-ttu-id="278f5-124">例如，BAM 事件匯流排服務會檢查是否有未歸屬的工作階段，例如已新增的 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="278f5-124">For example, the BAM Event Bus service checks for sessions that are not owned, such as a MessageBox database that has been added.</span></span>  
  
 <span data-ttu-id="278f5-125">BAM 事件匯流排工作階段會將事件來源從來源資料庫 (例如 MessageBox)，移動到包含使用可供查詢格式之事件資料的目的資料庫。</span><span class="sxs-lookup"><span data-stu-id="278f5-125">The BAM Event Bus session is the movement of the event data from the source database, such as the MessageBox, to the destination database that contains the event data in a format that you can query.</span></span> <span data-ttu-id="278f5-126">相同的 BAM 事件匯流排服務可以處理一或多個工作階段。</span><span class="sxs-lookup"><span data-stu-id="278f5-126">The same BAM Event Bus service can process one or more sessions.</span></span>  
  
 <span data-ttu-id="278f5-127">下圖顯示一組 BAM 事件匯流排伺服器，其構成 BAM 事件匯流排伺服器集區。</span><span class="sxs-lookup"><span data-stu-id="278f5-127">The following figure shows a group of BAM Event Bus servers, which make up a BAM Event Bus server pool.</span></span>  
  
 ![](../core/media/ebiz-bam-admin-evntbuspool.gif "ebiz_bam_admin_evntbuspool")  
<span data-ttu-id="278f5-128">BAM 事件匯流排伺服器集區的圖表</span><span class="sxs-lookup"><span data-stu-id="278f5-128">Diagram of a BAM Event Bus server pool</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="278f5-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="278f5-129">In This Section</span></span>  
  
-   [<span data-ttu-id="278f5-130">BAM 效能計數器</span><span class="sxs-lookup"><span data-stu-id="278f5-130">BAM Performance Counters</span></span>](../core/bam-performance-counters.md)  
  
-   [<span data-ttu-id="278f5-131">BAM 事件匯流排服務預存程序</span><span class="sxs-lookup"><span data-stu-id="278f5-131">BAM Event Bus Service Stored Procedures</span></span>](../core/bam-event-bus-service-stored-procedures.md)  
  
-   [<span data-ttu-id="278f5-132">BAM 事件匯流排服務伺服器容錯移轉</span><span class="sxs-lookup"><span data-stu-id="278f5-132">BAM Event Bus Service Server Failover</span></span>](../core/bam-event-bus-service-server-failover.md)  
  
-   [<span data-ttu-id="278f5-133">建立 BAM 事件匯流排服務執行的個體</span><span class="sxs-lookup"><span data-stu-id="278f5-133">Creating Instances of the BAM Event Bus Service</span></span>](../core/creating-instances-of-the-bam-event-bus-service.md)