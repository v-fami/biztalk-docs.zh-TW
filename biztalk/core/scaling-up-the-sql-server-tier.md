---
title: "向上擴充 SQL Server 層 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, scaling
- scaling, examples
- SQL Server, scaling
- scaling, scaling up
- scaling, strategies
ms.assetid: 4352c4af-6861-43d9-b433-9ca25668b439
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c654c4a3b1bba166ae8a49918f6ef31827cf041
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-up-the-sql-server-tier"></a><span data-ttu-id="32ecd-102">向上擴充 SQL Server 層</span><span class="sxs-lookup"><span data-stu-id="32ecd-102">Scaling Up the SQL Server Tier</span></span>
<span data-ttu-id="32ecd-103">在此模式中，會將現有的 SQL MessageBox 資料庫升級，使其可依據輸送量或延遲來擴充。</span><span class="sxs-lookup"><span data-stu-id="32ecd-103">In this pattern, the existing SQL MessageBox database is upgraded to scale according to the requirements in throughput or latency.</span></span>  
  
 <span data-ttu-id="32ecd-104">下圖所顯示的實例，是將主要 MessageBox 資料庫從四個程序伺服器升級到八個程序伺服器。</span><span class="sxs-lookup"><span data-stu-id="32ecd-104">The following figure shows a scenario where the master MessageBox database is upgraded from quad processor server to 8 processor server.</span></span>  
  
 <span data-ttu-id="32ecd-105">![小數位數 &#45; 向上擴充 MSGBOX](../core/media/scaleupmsgbox2.gif "ScaleUpMsgBox2")</span><span class="sxs-lookup"><span data-stu-id="32ecd-105">![Scale&#45;up MSGBOX](../core/media/scaleupmsgbox2.gif "ScaleUpMsgBox2")</span></span>  
  
## <a name="when-to-scale-up-the-sql-tier"></a><span data-ttu-id="32ecd-106">向上擴充 SQL 層的時機</span><span class="sxs-lookup"><span data-stu-id="32ecd-106">When to Scale-up the SQL Tier</span></span>  
  
-   <span data-ttu-id="32ecd-107">當您向上擴充主要 MessageBox 資料庫時。</span><span class="sxs-lookup"><span data-stu-id="32ecd-107">When you can scale up the master MessageBox database.</span></span>  
  
-   <span data-ttu-id="32ecd-108">當主要 MessageBox 資料庫成為瓶頸時。</span><span class="sxs-lookup"><span data-stu-id="32ecd-108">When the master MessageBox database becomes the bottleneck.</span></span> <span data-ttu-id="32ecd-109">這些瓶頸可能是：</span><span class="sxs-lookup"><span data-stu-id="32ecd-109">Those bottlenecks can be:</span></span>  
  
    -   <span data-ttu-id="32ecd-110">**CPU**發生非常昂貴和複雜的協調流程實例中，messagebox 會消耗大量的 CPU 資源。</span><span class="sxs-lookup"><span data-stu-id="32ecd-110">**CPU** In case of very expensive and complex orchestration scenarios, Message box consumes heavy CPU resources.</span></span> <span data-ttu-id="32ecd-111">藉由新增更多的 CPU 來向上擴充 SQL Server，應該會擴充此實例。</span><span class="sxs-lookup"><span data-stu-id="32ecd-111">Scaling-up the SQL server by adding more CPUs should scale the scenario.</span></span>  
  
    -   <span data-ttu-id="32ecd-112">**記憶體或 I/O**記憶體或 I/O 可能是瓶頸且可以升級。</span><span class="sxs-lookup"><span data-stu-id="32ecd-112">**Memory or I/O** Memory or I/O can be bottleneck and can be upgraded.</span></span>  
  
-   <span data-ttu-id="32ecd-113">當向上擴充比向外擴充便宜時，向上擴充即可處理該瓶頸。</span><span class="sxs-lookup"><span data-stu-id="32ecd-113">When scaling-up is cheaper than scaling-out and scaling-up can address the bottleneck.</span></span> <span data-ttu-id="32ecd-114">例如，若主要 MessageBox 資料庫有 SQL 鎖定爭用的問題，則此問題無法藉由向上擴充來解決。</span><span class="sxs-lookup"><span data-stu-id="32ecd-114">For example, if the master MessageBox database has an issue with SQL lock contention, this issue cannot be solved by scaling-up.</span></span>  
  
## <a name="when-do-you-decide-sql-cannot-scale-up"></a><span data-ttu-id="32ecd-115">何時決定 SQL 無法向上擴充？</span><span class="sxs-lookup"><span data-stu-id="32ecd-115">When do you decide SQL cannot scale-up?</span></span>  
 <span data-ttu-id="32ecd-116">向上擴充無法處理 SQL 層上的鎖定爭用瓶頸。</span><span class="sxs-lookup"><span data-stu-id="32ecd-116">Scale-up cannot address lock contention bottlenecks on the SQL tier.</span></span> <span data-ttu-id="32ecd-117">若是遇到這類瓶頸，向外擴充是比向上擴充更好的選項。</span><span class="sxs-lookup"><span data-stu-id="32ecd-117">If these kinds of bottlenecks are hit, scale-out is better option than scale-up.</span></span>  
  
## <a name="strategies-and-considerations-for-scaling-up-the-sql-tier"></a><span data-ttu-id="32ecd-118">向上擴充 SQL 層的策略與考量</span><span class="sxs-lookup"><span data-stu-id="32ecd-118">Strategies and Considerations for Scaling Up the SQL Tier</span></span>  
  
-   <span data-ttu-id="32ecd-119">先向上擴充主要 MessageBox 資料庫之後，再向外擴充。</span><span class="sxs-lookup"><span data-stu-id="32ecd-119">Scale-up the master MessageBox database first and then scale-out.</span></span>  
  
-   <span data-ttu-id="32ecd-120">主要 MessageBox 資料庫最後會成為瓶頸。</span><span class="sxs-lookup"><span data-stu-id="32ecd-120">The master MessageBox database will eventually be the bottleneck.</span></span> <span data-ttu-id="32ecd-121">因此，主要 MessageBox 資料庫應該更快且更大 (例如，Itanium 型 64 位元或 x64 型雙核心電腦)。</span><span class="sxs-lookup"><span data-stu-id="32ecd-121">So, the master MessageBox database should be faster and bigger (for example, an Itanium-based 64-bit or x64-based, dual core computer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ecd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32ecd-122">See Also</span></span>  
 <span data-ttu-id="32ecd-123">[向外擴充 BizTalk Server 層](../core/scaling-out-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="32ecd-123">[Scaling Out the BizTalk Server Tier](../core/scaling-out-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="32ecd-124">[向上擴充 BizTalk Server 層](../core/scaling-up-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="32ecd-124">[Scaling Up the BizTalk Server Tier](../core/scaling-up-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="32ecd-125">[向外擴充 SQL Server 層](../core/scaling-out-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="32ecd-125">[Scaling Out the SQL Server Tier](../core/scaling-out-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="32ecd-126">[向外擴充接收主控件](../core/scaled-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="32ecd-126">[Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="32ecd-127">[向外延展處理主控件](../core/scaled-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="32ecd-127">[Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md) </span></span>  
 <span data-ttu-id="32ecd-128">[向外延展傳送主控件](../core/scaled-out-sending-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="32ecd-128">[Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md) </span></span>  
 <span data-ttu-id="32ecd-129">[使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="32ecd-129">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="32ecd-130">[向外延展資料庫](../core/scaled-out-databases.md) </span><span class="sxs-lookup"><span data-stu-id="32ecd-130">[Scaled-Out Databases](../core/scaled-out-databases.md) </span></span>  
 [<span data-ttu-id="32ecd-131">叢集 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="32ecd-131">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)