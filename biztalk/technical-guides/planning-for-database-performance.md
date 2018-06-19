---
title: 規劃資料庫效能 |Microsoft 文件
ms.custom: ''
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7212fa37-88e0-4b5f-af97-c72063357645
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 878320cf7c6a5762626087964033430afcf611cf
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009503"
---
# <a name="planning-for-database-performance"></a><span data-ttu-id="0fc42-102">規劃資料庫效能</span><span class="sxs-lookup"><span data-stu-id="0fc42-102">Planning for Database Performance</span></span>

## <a name="overview"></a><span data-ttu-id="0fc42-103">概觀</span><span class="sxs-lookup"><span data-stu-id="0fc42-103">Overview</span></span>
<span data-ttu-id="0fc42-104">Microsoft BizTalk Server 是極資料庫密集的應用程式，可能需要多達 13 個不同的資料庫，Microsoft SQL Server 中建立。</span><span class="sxs-lookup"><span data-stu-id="0fc42-104">Microsoft BizTalk Server is an extremely database intensive application that may require the creation of up to 13 separate databases in Microsoft SQL Server.</span></span> <span data-ttu-id="0fc42-105">BizTalk Server 資料庫大量本質，因為它是非常重要您選擇適當的版本和版本的 SQL Server 將裝載 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0fc42-105">Because of the database intensive nature of BizTalk Server, it is of critical importance that you choose the appropriate version and edition of SQL Server that will house the BizTalk Server databases.</span></span> <span data-ttu-id="0fc42-106">執行 SQL Server 裝載 BizTalk Server 資料庫之電腦的效能最佳化，請遵循本主題中以及在建議[BizTalk Server 資料庫最佳化](optimizing-database-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="0fc42-106">To optimize the performance of the computers running SQL Server that house the BizTalk Server databases, follow the recommendations in this topic and in the [BizTalk Server Database Optimization](optimizing-database-performance.md).</span></span>
  

> [!NOTE]  
>  <span data-ttu-id="0fc42-107">雖然本指南針對 BizTalk Server 和 SQL Server 的其他版本所撰寫，您可能可以在較新版本，使用相同的建議。</span><span class="sxs-lookup"><span data-stu-id="0fc42-107">While this guide is written for other versions of BizTalk Server and SQL Server, you can probably use the same recommendations for newer versions.</span></span>
  
## <a name="considerations-for-sql-server-editions"></a><span data-ttu-id="0fc42-108">SQL Server 版本的考量</span><span class="sxs-lookup"><span data-stu-id="0fc42-108">Considerations for SQL Server Editions</span></span>  
 <span data-ttu-id="0fc42-109">BizTalk Server 資料庫應該設定為在專用 SQL Server 執行個體盡可能上執行。</span><span class="sxs-lookup"><span data-stu-id="0fc42-109">BizTalk Server databases should be configured to run on a dedicated SQL Server instance whenever possible.</span></span> <span data-ttu-id="0fc42-110">BizTalk Server 資料庫大量應用程式，因此 BizTalk Server 電腦，明確劃分且包含 BizTalk Server 資料庫的 SQL Server 電腦將可改善效能，應該考量實際執行 BizTalk Server 中的最佳做法環境。</span><span class="sxs-lookup"><span data-stu-id="0fc42-110">BizTalk Server is a database intensive application, so separation of the BizTalk Server computers and the SQL Server computers that house the BizTalk Server databases will improve performance and should be considered a best practice in a production BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="0fc42-111">各種 SQL Server 版本提供不同功能可能會影響 BizTalk Server 環境的效能。</span><span class="sxs-lookup"><span data-stu-id="0fc42-111">Various editions of SQL Server provide different features which can affect the performance of your BizTalk Server environment.</span></span> <span data-ttu-id="0fc42-112">例如，在高負載情況下可用於 32 位元版本的 SQL Server 可用的資料庫鎖定數目可能會超過，即不利的 BizTalk 方案的效能。</span><span class="sxs-lookup"><span data-stu-id="0fc42-112">For example, under high-load conditions, the number of available database locks that are available for the 32-bit version of SQL Server may be exceeded, which is detrimental to the performance of the BizTalk solution.</span></span> <span data-ttu-id="0fc42-113">請考慮罩上的 SQL Server 64 位元版本的 MessageBox 資料庫，如果您在測試環境中發生 「 鎖定不足 」 錯誤。</span><span class="sxs-lookup"><span data-stu-id="0fc42-113">Consider housing your MessageBox database on a 64-bit version of SQL Server if you are experiencing "out of lock" errors in your test environment.</span></span> <span data-ttu-id="0fc42-114">在 64 位元版本的 SQL Server 上，可用的鎖定數目大幅提高。</span><span class="sxs-lookup"><span data-stu-id="0fc42-114">The number of available locks is significantly higher on the 64-bit version of SQL Server.</span></span>  
  
 <span data-ttu-id="0fc42-115">請考慮下的表決定 database engine 功能時，您必須針對您的 BizTalk 環境。</span><span class="sxs-lookup"><span data-stu-id="0fc42-115">Consider the table below when deciding on the database engine features that you will need for your BizTalk environment.</span></span> <span data-ttu-id="0fc42-116">對於小型的解決方案，例如當執行 BizTalk Server Branch Edition 上，SQL Server Workgroup Edition 應已足夠裝載 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0fc42-116">For small-scale solutions, for example when running BizTalk Server Branch Edition, SQL Server Workgroup Edition may be adequate for housing the BizTalk Server databases.</span></span> <span data-ttu-id="0fc42-117">大型的標尺，需要叢集支援，企業層級方案的 BizTalk 記錄傳送支援或 Analysis Services 支援部門，則需要 SQL Server Enterprise Edition 來主控資料庫。</span><span class="sxs-lookup"><span data-stu-id="0fc42-117">For large scale, enterprise-level solutions that require clustering support, BizTalk log shipping support, or Analysis Services support, then you need SQL Server Enterprise Edition to host the databases.</span></span>  
  
|<span data-ttu-id="0fc42-118">SQL Server 版本</span><span class="sxs-lookup"><span data-stu-id="0fc42-118">Edition of SQL Server</span></span>|<span data-ttu-id="0fc42-119">64 位元支援</span><span class="sxs-lookup"><span data-stu-id="0fc42-119">64-bit support</span></span>|<span data-ttu-id="0fc42-120">多重執行個體的支援</span><span class="sxs-lookup"><span data-stu-id="0fc42-120">Multi-Instance Support</span></span>|<span data-ttu-id="0fc42-121">叢集支援</span><span class="sxs-lookup"><span data-stu-id="0fc42-121">Clustering support</span></span>|<span data-ttu-id="0fc42-122">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="0fc42-122">Analysis Services</span></span>|  
|---|---|---|---|---|  
|<span data-ttu-id="0fc42-123">SQL Server Enterprise Edition</span><span class="sxs-lookup"><span data-stu-id="0fc42-123">SQL Server Enterprise Edition</span></span>|<span data-ttu-id="0fc42-124">是</span><span class="sxs-lookup"><span data-stu-id="0fc42-124">Yes</span></span>|<span data-ttu-id="0fc42-125">是</span><span class="sxs-lookup"><span data-stu-id="0fc42-125">Yes</span></span>|<span data-ttu-id="0fc42-126">是</span><span class="sxs-lookup"><span data-stu-id="0fc42-126">Yes</span></span>|<span data-ttu-id="0fc42-127">是</span><span class="sxs-lookup"><span data-stu-id="0fc42-127">Yes</span></span>|  
|<span data-ttu-id="0fc42-128">SQL Server Standard Edition</span><span class="sxs-lookup"><span data-stu-id="0fc42-128">SQL Server Standard Edition</span></span>|<span data-ttu-id="0fc42-129">是</span><span class="sxs-lookup"><span data-stu-id="0fc42-129">Yes</span></span>|<span data-ttu-id="0fc42-130">是</span><span class="sxs-lookup"><span data-stu-id="0fc42-130">Yes</span></span>|<span data-ttu-id="0fc42-131">是 （節點 2）</span><span class="sxs-lookup"><span data-stu-id="0fc42-131">Yes (2 node)</span></span>|<span data-ttu-id="0fc42-132">是</span><span class="sxs-lookup"><span data-stu-id="0fc42-132">Yes</span></span>|  
|<span data-ttu-id="0fc42-133">SQL Server Workgroup Edition</span><span class="sxs-lookup"><span data-stu-id="0fc42-133">SQL Server Workgroup Edition</span></span>|<span data-ttu-id="0fc42-134">是</span><span class="sxs-lookup"><span data-stu-id="0fc42-134">Yes</span></span>|<span data-ttu-id="0fc42-135">是</span><span class="sxs-lookup"><span data-stu-id="0fc42-135">Yes</span></span>|<span data-ttu-id="0fc42-136">否</span><span class="sxs-lookup"><span data-stu-id="0fc42-136">No</span></span>|<span data-ttu-id="0fc42-137">否</span><span class="sxs-lookup"><span data-stu-id="0fc42-137">No</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="0fc42-138">BAM RTA 需要 SQL Server Enterprise Edition。</span><span class="sxs-lookup"><span data-stu-id="0fc42-138">BAM RTA requires SQL Server Enterprise Edition.</span></span>  
  
 <span data-ttu-id="0fc42-139">版本支援的功能完整清單，請參閱[支援的 SQL Server 的版本功能](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="0fc42-139">For a complete list of the features supported by the editions, see [Features Supported by the Editions of SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016).</span></span>