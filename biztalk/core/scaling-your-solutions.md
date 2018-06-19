---
title: 擴充您的解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance, scaling
- scaling, scaling out
- scaling, performance
- scaling, about scaling
- scaling, scaling up
- scaling
ms.assetid: e2acbaa4-29d3-4c89-ac1f-c0641cfa0442
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5417e303ea8486ef5bdee8e57c66d4783fb197ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269974"
---
# <a name="scaling-your-solutions"></a><span data-ttu-id="554e9-102">擴充您的解決方案</span><span class="sxs-lookup"><span data-stu-id="554e9-102">Scaling Your Solutions</span></span>
<span data-ttu-id="554e9-103">BizTalk Server 架構針對擴充性提供非常良好的支援。</span><span class="sxs-lookup"><span data-stu-id="554e9-103">BizTalk Server architecture provides a very good support for scalability.</span></span> <span data-ttu-id="554e9-104">您所選擇的擴充模式，則會根據實例的複雜度、硬體，以及輸送量/延遲需求而定。</span><span class="sxs-lookup"><span data-stu-id="554e9-104">The scaling patterns that you choose depend on complexity of your scenario, hardware and the throughput/Latency requirements.</span></span> <span data-ttu-id="554e9-105">您應該從較小的拓樸開始，然後根據本節的指導方針嘗試擴充或縮小。</span><span class="sxs-lookup"><span data-stu-id="554e9-105">You should start with a smaller topology initially and try to scale-up or down based on the guidelines in this section.</span></span>  
  
## <a name="scaling-out-and-scaling-up"></a><span data-ttu-id="554e9-106">向外擴充和向上擴充</span><span class="sxs-lookup"><span data-stu-id="554e9-106">Scaling Out and Scaling Up</span></span>  
 <span data-ttu-id="554e9-107">有兩種方式可以擴充您的 BizTalk Server 系統：</span><span class="sxs-lookup"><span data-stu-id="554e9-107">There are two ways to scale your BizTalk Server system:</span></span>  
  
-   <span data-ttu-id="554e9-108">向外擴充是新增其他電腦的程序。</span><span class="sxs-lookup"><span data-stu-id="554e9-108">Scaling-out is the process of adding additional computers.</span></span> <span data-ttu-id="554e9-109">例如，若 BizTalk Server 的瓶頸是來自 CPU 資源，則新增其他伺服器可提供雙倍的 CPU 資源，進而提供雙倍的輸送量。</span><span class="sxs-lookup"><span data-stu-id="554e9-109">For example, if BizTalk Server is bottlenecked by CPU resources, adding another server provides double the CPU resources which may provide double the throughput.</span></span>  
  
-   <span data-ttu-id="554e9-110">向上擴充是升級現有電腦的程序。</span><span class="sxs-lookup"><span data-stu-id="554e9-110">Scaling-up is process of upgrading the existing computer.</span></span> <span data-ttu-id="554e9-111">例如，您可以將 BizTalk Server 電腦從擁有四個處理器的電腦升級為擁有八個處理器的電腦。</span><span class="sxs-lookup"><span data-stu-id="554e9-111">For example, you can upgrade a BizTalk Server computer from a 4 processor machine to an 8 processor.</span></span>  
  
 <span data-ttu-id="554e9-112">BizTalk Server 系統有兩層：BizTalk Server 層，以及包含 MessageBox 資料庫的 SQL Server 層。</span><span class="sxs-lookup"><span data-stu-id="554e9-112">A BizTalk Server system has two tiers: the BizTalk Server tier and the SQL Server tier, which contains your MessageBox databases.</span></span> <span data-ttu-id="554e9-113">在任何實例中，您都可以向外擴充或向上擴充每一層。</span><span class="sxs-lookup"><span data-stu-id="554e9-113">In any scenario, you can scale out or scale up each tier.</span></span> <span data-ttu-id="554e9-114">也就是說，您可以向外擴充 BizTalk Server 和 MessageBox 資料庫，或是向上擴充這兩者。</span><span class="sxs-lookup"><span data-stu-id="554e9-114">That is, you can scale-out BizTalk Server and the MessageBox database, or scale up both of them.</span></span>  
  
 <span data-ttu-id="554e9-115">在大部分情況下，BizTalk 層會先成為瓶頸，而您可以使其向外擴充以便開始改善效能。不過，在某個時點，視您所使用的系統和硬體複雜度而定，您將無法繼續向外擴充 BizTalk 層，而 SQL Server 層會變成瓶頸。</span><span class="sxs-lookup"><span data-stu-id="554e9-115">In most cases, the BizTalk tier becomes a bottleneck first, and you start improving performance by scaling it out. But, at some point, depending on complexity of your system and the hardware you use, you can’t scale out the BizTalk tier anymore and the SQL Server tier becomes the bottleneck.</span></span> <span data-ttu-id="554e9-116">接著，您可以向上擴充 SQL Server 層，然後新增更多 MessageBox 資料庫來使其向外擴充。</span><span class="sxs-lookup"><span data-stu-id="554e9-116">Then, you scale up the SQL Server tier, and next scale it out by adding more MessageBox databases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="554e9-117">在此處，新的 MessageBox 資料庫不一定代表有其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="554e9-117">A new MessageBox database does not necessarily mean another server here.</span></span> <span data-ttu-id="554e9-118">單一 SQL 伺服器可以有多個 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="554e9-118">A single SQL server can have multiple MessageBox databases.</span></span> <span data-ttu-id="554e9-119">此外，若資料庫位於不同的電腦上，多個 MessageBox 資料庫會產生 DTC 成本和網路躍點。</span><span class="sxs-lookup"><span data-stu-id="554e9-119">Also, multiple MessageBox databases incur DTC cost and network hop if the databases are on different computers.</span></span>  
  
 <span data-ttu-id="554e9-120">理論上，只要主要 MessageBox 資料庫尚未飽和，SQL Server 層就可以無限向外擴充。</span><span class="sxs-lookup"><span data-stu-id="554e9-120">In theory, the SQL Server tier can scale out indefinitely as long as the master MessageBox database is not saturated.</span></span>  
  
 <span data-ttu-id="554e9-121">本節中的主題會更詳細地描述這些擴充模式。</span><span class="sxs-lookup"><span data-stu-id="554e9-121">The topics in this section describe these scaling patterns in more detail.</span></span> <span data-ttu-id="554e9-122">這些主題也會說明如何擴充每個模式，以及如何判定您何時無法再使用該模式來擴充系統。</span><span class="sxs-lookup"><span data-stu-id="554e9-122">They also explain how to scale each pattern and how to determine when you can no longer use that pattern to scale your system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="554e9-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="554e9-123">In This Section</span></span>  
  
-   [<span data-ttu-id="554e9-124">什麼是擴充性？</span><span class="sxs-lookup"><span data-stu-id="554e9-124">What Is Scalability?</span></span>](../core/what-is-scalability.md)  
  
-   [<span data-ttu-id="554e9-125">向外擴充 BizTalk Server 層</span><span class="sxs-lookup"><span data-stu-id="554e9-125">Scaling Out the BizTalk Server Tier</span></span>](../core/scaling-out-the-biztalk-server-tier.md)  
  
-   [<span data-ttu-id="554e9-126">向上擴充 BizTalk Server 層</span><span class="sxs-lookup"><span data-stu-id="554e9-126">Scaling Up the BizTalk Server Tier</span></span>](../core/scaling-up-the-biztalk-server-tier.md)  
  
-   [<span data-ttu-id="554e9-127">向外擴充 SQL Server 層</span><span class="sxs-lookup"><span data-stu-id="554e9-127">Scaling Out the SQL Server Tier</span></span>](../core/scaling-out-the-sql-server-tier.md)  
  
-   [<span data-ttu-id="554e9-128">向上擴充 SQL Server 層</span><span class="sxs-lookup"><span data-stu-id="554e9-128">Scaling Up the SQL Server Tier</span></span>](../core/scaling-up-the-sql-server-tier.md)  
  
## <a name="see-also"></a><span data-ttu-id="554e9-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="554e9-129">See Also</span></span>  
 <span data-ttu-id="554e9-130">[向外擴充接收主控件](../core/scaled-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="554e9-130">[Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="554e9-131">[向外延展處理主控件](../core/scaled-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="554e9-131">[Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md) </span></span>  
 <span data-ttu-id="554e9-132">[向外延展傳送主控件](../core/scaled-out-sending-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="554e9-132">[Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md) </span></span>  
 <span data-ttu-id="554e9-133">[使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="554e9-133">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="554e9-134">[向外延展資料庫](../core/scaled-out-databases.md) </span><span class="sxs-lookup"><span data-stu-id="554e9-134">[Scaled-Out Databases](../core/scaled-out-databases.md) </span></span>  
 [<span data-ttu-id="554e9-135">叢集 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="554e9-135">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)