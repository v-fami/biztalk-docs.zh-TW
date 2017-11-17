---
title: "增加可用性，以便讓 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72d9ce5e-d775-4f8e-b1a4-bf3c7c05f571
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa48d7dada00ebadf089834f5025f3fdfdf25070
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="increasing-availability-for-biztalk-server"></a><span data-ttu-id="b1c26-102">增加可用性，以便讓 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b1c26-102">Increasing Availability for BizTalk Server</span></span>
<span data-ttu-id="b1c26-103">本節說明您可以提高可用性的方法您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。</span><span class="sxs-lookup"><span data-stu-id="b1c26-103">This section describes ways you can increase the availability of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.</span></span>  
  
## <a name="strategies-for-increasing-availability"></a><span data-ttu-id="b1c26-104">增加可用性策略</span><span class="sxs-lookup"><span data-stu-id="b1c26-104">Strategies for Increasing Availability</span></span>  
 <span data-ttu-id="b1c26-105">增加可用性策略包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="b1c26-105">Strategies for increasing availability include the following:</span></span>  
  
-   <span data-ttu-id="b1c26-106">**提供使用 Windows Server 2003 伺服器叢集或 Windows Server 2008 容錯移轉叢集的高可用性**。</span><span class="sxs-lookup"><span data-stu-id="b1c26-106">**Providing high availability using Windows Server 2003 server clustering or Windows Server 2008 failover clustering**.</span></span> <span data-ttu-id="b1c26-107">伺服器/容錯移轉叢集是一組獨立電腦系統，稱為節點，做為單一系統可確保重要應用程式和資源中的用戶端能夠一起運作。</span><span class="sxs-lookup"><span data-stu-id="b1c26-107">A server/failover cluster is a group of independent computer systems, known as nodes, working together as a single system to ensure that critical applications and resources remain available to clients.</span></span> <span data-ttu-id="b1c26-108">如果其中一個節點變成因為失敗或維護停機時間的需求而無法使用，另一個節點便會立即開始提供服務 （稱為容錯移轉的程序）。</span><span class="sxs-lookup"><span data-stu-id="b1c26-108">If one of the nodes becomes unavailable as a result of failure or maintenance downtime requirements, another node immediately begins providing service (a process known as failover).</span></span>  
  
    -   <span data-ttu-id="b1c26-109">伺服器/容錯移轉叢集通常建議使用該所執行 SQL Server 的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="b1c26-109">A server/failover cluster is typically recommended for the computers running SQL Server that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
    -   <span data-ttu-id="b1c26-110">伺服器叢集中可能需要以特定 BizTalk 配接器提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="b1c26-110">A server cluster may be required to provide high availability for certain BizTalk adapters.</span></span>  
  
    -   <span data-ttu-id="b1c26-111">伺服器叢集中，通常建議的企業單一登入主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="b1c26-111">A server cluster is typically recommended for the Enterprise Single Sign-On master secret server.</span></span>  
  
-   <span data-ttu-id="b1c26-112">**提供使用一種負載平衡的高可用性**。</span><span class="sxs-lookup"><span data-stu-id="b1c26-112">**Providing high availability using a form of load balancing**.</span></span>  
  
    -   <span data-ttu-id="b1c26-113">網路負載平衡 (NLB)。</span><span class="sxs-lookup"><span data-stu-id="b1c26-113">Network load balancing (NLB).</span></span> <span data-ttu-id="b1c26-114">NLB 會將連入網路流量重新導向至使用 NLB 叢集主機，若主機失效或離線，以提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="b1c26-114">NLB delivers high availability by redirecting incoming network traffic to working NLB cluster hosts if a host fails or is offline.</span></span> <span data-ttu-id="b1c26-115">不同於伺服器叢集，NLB 不需要特殊硬體。</span><span class="sxs-lookup"><span data-stu-id="b1c26-115">Unlike server clusters, NLB does not require special hardware.</span></span>  
  
    -   <span data-ttu-id="b1c26-116">BizTalk 主控件的負載平衡。</span><span class="sxs-lookup"><span data-stu-id="b1c26-116">BizTalk host load balancing.</span></span> <span data-ttu-id="b1c26-117">BizTalk 主控件負載平衡新增多個伺服器執行的 BizTalk 主控件提供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中，然後設定這些伺服器上執行內含式主控件的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1c26-117">BizTalk host load balancing is provided for BizTalk Hosts by adding multiple servers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group and then configuring multiple instances of an in-process host to run on these servers.</span></span> <span data-ttu-id="b1c26-118">這樣可將該主控件中所設定的服務和成品執行作業分散於該主控件的多個執行個體，以提高可用性和擴充性。</span><span class="sxs-lookup"><span data-stu-id="b1c26-118">This distributes the execution of services and artifacts configured in that host across multiple instances of the host, which enhances its availability and scalability.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b1c26-119">內含式主控件只可使用主應用程式的負載平衡功能。</span><span class="sxs-lookup"><span data-stu-id="b1c26-119">Host load balancing functionality is available for in-process hosts only.</span></span>  
  
    -   <span data-ttu-id="b1c26-120">透過使用 SAN，或加入多個 MessageBox 資料庫的 SQL Server 磁碟提供負載平衡。</span><span class="sxs-lookup"><span data-stu-id="b1c26-120">Load balancing is provided for SQL Server disks through the use of a SAN or by adding multiple MessageBox databases.</span></span>  
  
-   <span data-ttu-id="b1c26-121">提供的策略**提高可用性**。</span><span class="sxs-lookup"><span data-stu-id="b1c26-121">Strategies for providing **increased availability**.</span></span> <span data-ttu-id="b1c26-122">這些策略提供增加的可用性，但通常也需要 系統管理員身分執行在執行階段的一個或多個動作。</span><span class="sxs-lookup"><span data-stu-id="b1c26-122">These strategies provide increased availability but usually also require that an administrator perform one or more actions at runtime.</span></span> <span data-ttu-id="b1c26-123">因此這些策略是通常視為提供提高的可用性，而不是高可用性：</span><span class="sxs-lookup"><span data-stu-id="b1c26-123">Therefore these strategies are typically thought of as providing increased availability as opposed to high availability:</span></span>  
  
    -   <span data-ttu-id="b1c26-124">增加可用性使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送和災害復原。</span><span class="sxs-lookup"><span data-stu-id="b1c26-124">Increasing availability using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping and disaster recovery.</span></span>  
  
    -   <span data-ttu-id="b1c26-125">增加可用性，透過實作適當的監視和維護策略。</span><span class="sxs-lookup"><span data-stu-id="b1c26-125">Increasing availability through implementation of the appropriate monitoring and maintenance strategies.</span></span>  
  
## <a name="difference-between-clustering-and-disaster-recovery"></a><span data-ttu-id="b1c26-126">叢集之間的差異和災害復原</span><span class="sxs-lookup"><span data-stu-id="b1c26-126">Difference Between Clustering and Disaster Recovery</span></span>  
 <span data-ttu-id="b1c26-127">叢集和災害復原增加可用性，而它們之間的主要差異是叢集通常提供更快速的復原時間比災害復原。</span><span class="sxs-lookup"><span data-stu-id="b1c26-127">While clusters and disaster recovery both increase availability, a key difference between them is that clusters typically provide much faster recovery time than disaster recovery does.</span></span> <span data-ttu-id="b1c26-128">因此在伺服器/容錯移轉叢集上建置方案或負載平衡通常視為提供高可用性而非只提供可用性。</span><span class="sxs-lookup"><span data-stu-id="b1c26-128">Therefore a solution built on server/failover clusters or load balancing is commonly thought of as providing high availability as opposed to merely providing availability.</span></span>  
  
 <span data-ttu-id="b1c26-129">災害復原可讓您繼續作業失敗的系統，但通常是手動程序也需要更多的復原時間，比的高可用性的實作。</span><span class="sxs-lookup"><span data-stu-id="b1c26-129">Disaster recovery allows you to resume operation of a failed system but is typically a manual process and requires more recovery time than a high-availability implementation.</span></span> <span data-ttu-id="b1c26-130">因此，災害復原實作所提供的可用性，但不是高可用性。</span><span class="sxs-lookup"><span data-stu-id="b1c26-130">Therefore, a disaster recovery implementation provides availability but not high availability.</span></span> <span data-ttu-id="b1c26-131">您應該採用透過伺服器/容錯移轉叢集和負載平衡，高可用性和災害復原，在生產環境中透過可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="b1c26-131">You should employ both high availability through server/failover clusters and load balancing, and availability through disaster recovery, in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1c26-132">本節內容</span><span class="sxs-lookup"><span data-stu-id="b1c26-132">In This Section</span></span>  
  
-   [<span data-ttu-id="b1c26-133">提供高可用性</span><span class="sxs-lookup"><span data-stu-id="b1c26-133">Providing High Availability</span></span>](../technical-guides/providing-high-availability.md)  
  
-   [<span data-ttu-id="b1c26-134">嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="b1c26-134">Disaster Recovery</span></span>](../technical-guides/disaster-recovery.md)  
  
## <a name="see-also"></a><span data-ttu-id="b1c26-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1c26-135">See Also</span></span>  
 <span data-ttu-id="b1c26-136">[檢查清單： 提供高可用性與容錯或負載平衡](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md) </span><span class="sxs-lookup"><span data-stu-id="b1c26-136">[Checklist: Providing High Availability with Fault Tolerance or Load Balancing](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md) </span></span>  
 [<span data-ttu-id="b1c26-137">檢查清單： 提高可用性與災害復原</span><span class="sxs-lookup"><span data-stu-id="b1c26-137">Checklist: Increasing Availability with Disaster Recovery</span></span>](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)