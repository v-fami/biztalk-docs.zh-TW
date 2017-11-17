---
title: "建立高可用性的 BizTalk Server 環境 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, high availability
- architecture, databases
- databases, architecture
- performance
- hosts, multiple
- hosts, architecture
- architecture, hosts
- databases, clustering
- high availability, designing
- BizTalk Server, architecture
- installation, planning
- clustering, databases
- installation, availability
ms.assetid: 758eb3bd-a25b-4863-a4ca-d7a1635f7542
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87044102248d371ea19ed07d676a0e7a0861296e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-highly-available-biztalk-server-environment"></a><span data-ttu-id="e2792-102">建立高度可用的 BizTalk 伺服器環境</span><span class="sxs-lookup"><span data-stu-id="e2792-102">Creating a Highly Available BizTalk Server Environment</span></span>
<span data-ttu-id="e2792-103">本章節描述如何在 Microsoft 通訊與資料提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]整合不同的系統和應用程式時。</span><span class="sxs-lookup"><span data-stu-id="e2792-103">This section describes how to provide high availability for the data and communications in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] when integrating disparate systems and applications.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e2792-104">將資料從處理資料，讓您以解決可用性問題擴充資料庫和裝載獨立的主機。</span><span class="sxs-lookup"><span data-stu-id="e2792-104"> separates the data from the hosts that process the data, enabling you to resolve availability issues by scaling the databases and hosts independently.</span></span>  
  
## <a name="demonstrating-high-availability"></a><span data-ttu-id="e2792-105">顯示高可用性</span><span class="sxs-lookup"><span data-stu-id="e2792-105">Demonstrating High Availability</span></span>  
 <span data-ttu-id="e2792-106">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的高可用性著重於復原可能中斷 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署可用性的功能性元件。</span><span class="sxs-lookup"><span data-stu-id="e2792-106">High availability for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] focuses on recovering functional components that might disrupt availability in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.</span></span>  
  
 <span data-ttu-id="e2792-107">為了顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的高可用性，您必須套用失敗並評量產品在復原方面的有效性。</span><span class="sxs-lookup"><span data-stu-id="e2792-107">To demonstrate high availability in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you have to apply failure and measure the product's effectiveness in recovery.</span></span> <span data-ttu-id="e2792-108">當有錯誤或失敗發生時，高度可用的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署可以讓外部應用程式和系統幾乎感覺不到任何異狀，並且讓所有的服務能夠在最少中斷的情況下繼續正確運作。</span><span class="sxs-lookup"><span data-stu-id="e2792-108">A highly available [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment makes errors and failures transparent to external applications and systems, and makes sure that all services continue functioning correctly with minimal disruption.</span></span>  
  
## <a name="designing-for-high-availability"></a><span data-ttu-id="e2792-109">為高可用性所設計</span><span class="sxs-lookup"><span data-stu-id="e2792-109">Designing for High Availability</span></span>  
 <span data-ttu-id="e2792-110">設計[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供高可用性部署需要實作應用程式處理序整合整合或商務案例中每個功能元件的複本。</span><span class="sxs-lookup"><span data-stu-id="e2792-110">Designing a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment that provides high availability involves implementing redundancy for each functional component involved in an application integration or business process integration scenario.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e2792-111">藉由在概念上分隔資料的主控件處理的資料，可簡化這些案例的實作。</span><span class="sxs-lookup"><span data-stu-id="e2792-111"> simplifies the implementation of these scenarios by conceptually separating the data from the hosts that process the data.</span></span> <span data-ttu-id="e2792-112">因此，為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供高可用性，需要執行多個主控件執行個體並叢集 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e2792-112">So providing high availability for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] involves running multiple host instances and clustering the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, as follows:</span></span>  
  
-   <span data-ttu-id="e2792-113">**BizTalk 主控件的架構**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您將主控件分開並執行以提供高可用性的索引鍵的函式，例如接收訊息、 處理協調流程和傳送訊息的多個主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e2792-113">**Architecture for BizTalk Hosts** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lets you separate hosts and run multiple host instances to provide high availability for key functions such as receiving messages, processing orchestrations, and sending messages.</span></span> <span data-ttu-id="e2792-114">這些主控件不需要任何其他叢集或負載平衡機制，因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會透過主控件執行個體在多部電腦之間自動分散工作負載。</span><span class="sxs-lookup"><span data-stu-id="e2792-114">These hosts do not require any additional clustering or load-balancing mechanism because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically distributes workload across multiple computers through host instances.</span></span> <span data-ttu-id="e2792-115">不過，執行 HTTP 與 SOAP 配接器的接收處理常式之主控件需要負載平衡機制，例如「網路負載平衡」(NLB) 以提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="e2792-115">However, hosts running the receive handler for the HTTP and SOAP adapters require a load-balancing mechanism such as Network Load Balancing (NLB) to provide high availability.</span></span>  
  
-   <span data-ttu-id="e2792-116">**BizTalk Server 資料庫的架構**的高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫通常包含兩個或多個設定為主動/被動伺服器叢集組態的資料庫電腦。</span><span class="sxs-lookup"><span data-stu-id="e2792-116">**Architecture for BizTalk Server databases** High availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases typically consists of two or more database computers configured in an active/passive server cluster configuration.</span></span> <span data-ttu-id="e2792-117">這些電腦可共用一般磁碟資源 (例如，RAID5 SCSI 磁碟陣列或儲存區域網路)，並使用 Windows 叢集提供備份備援和容錯。</span><span class="sxs-lookup"><span data-stu-id="e2792-117">These computers share a common disk resource (such as a RAID5 SCSI disk array or storage area network) and use Windows Clustering to provide backup redundancy and fault tolerance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2792-118">高度可用的環境實際上就是多個電腦的環境。</span><span class="sxs-lookup"><span data-stu-id="e2792-118">Highly-available environments are, by nature, multi-computer environments.</span></span> <span data-ttu-id="e2792-119">在多個電腦的環境中設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，必須使用網域使用者群組和帳戶。</span><span class="sxs-lookup"><span data-stu-id="e2792-119">When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a multi-computer environment you must use domain user groups and accounts.</span></span>  
  
 <span data-ttu-id="e2792-120">因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是建置在 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 或 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 與 Microsoft SQL Server 2008 上，請確定您在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的主控件之前，先將這些產品部署為具有高可用性。</span><span class="sxs-lookup"><span data-stu-id="e2792-120">Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is built on Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], and Microsoft SQL Server 2008, make sure that you deploy these products with high availability before configuring hosts for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="e2792-121">以下連結包括為這些基礎產品提供高可用性的資訊：</span><span class="sxs-lookup"><span data-stu-id="e2792-121">The following links include information about providing high availability for these underlying products:</span></span>  
  
-   <span data-ttu-id="e2792-122">**高度可用性 — 永遠在技術**，可在[http://go.microsoft.com/fwlink/?LinkId=130376](http://go.microsoft.com/fwlink/?LinkId=130376)。</span><span class="sxs-lookup"><span data-stu-id="e2792-122">**High Availability – Always On Technologies**, available at [http://go.microsoft.com/fwlink/?LinkId=130376](http://go.microsoft.com/fwlink/?LinkId=130376).</span></span>  
  
     <span data-ttu-id="e2792-123">此白皮書描述 SQL Server 2008 提供的高度可用性功能。</span><span class="sxs-lookup"><span data-stu-id="e2792-123">This whitepaper describes high availability features that are available with SQL Server 2008.</span></span>  
  
-   <span data-ttu-id="e2792-124">**高可用性解決方案概觀**，可在[http://go.microsoft.com/fwlink/?LinkId=130377](http://go.microsoft.com/fwlink/?LinkId=130377)。</span><span class="sxs-lookup"><span data-stu-id="e2792-124">**High Availability Solutions Overview**, available at [http://go.microsoft.com/fwlink/?LinkId=130377](http://go.microsoft.com/fwlink/?LinkId=130377).</span></span>  
  
     <span data-ttu-id="e2792-125">介紹幾個改善伺服器或資料庫可用性的 SQL Server 2008 高可用性解決方案。</span><span class="sxs-lookup"><span data-stu-id="e2792-125">Introduces several high-availability solutions for SQL Server 2008 that improve the availability of servers or databases.</span></span>  
  
-   <span data-ttu-id="e2792-126">**Windows 部署服務逐步指南**，可在[http://go.microsoft.com/fwlink/?LinkId=130379](http://go.microsoft.com/fwlink/?LinkId=130379)。</span><span class="sxs-lookup"><span data-stu-id="e2792-126">**Windows Deployment Services Step-by-Step Guide**, available at [http://go.microsoft.com/fwlink/?LinkId=130379](http://go.microsoft.com/fwlink/?LinkId=130379).</span></span>  
  
     <span data-ttu-id="e2792-127">包含如何使用 Windows Server 2008 中的 Windows 部署服務角色的逐步指引。</span><span class="sxs-lookup"><span data-stu-id="e2792-127">Contains step-by-step guidance for how to use the Windows Deployment Services role in Windows Server 2008.</span></span>  
  
-   <span data-ttu-id="e2792-128">**Windows Server 2003 Deployment Kit: Planning Server Deployments**，可在[http://go.microsoft.com/fwlink/?LinkId=24433](http://go.microsoft.com/fwlink/?LinkId=24433)。</span><span class="sxs-lookup"><span data-stu-id="e2792-128">**Windows Server 2003 Deployment Kit: Planning Server Deployments**, available at [http://go.microsoft.com/fwlink/?LinkId=24433](http://go.microsoft.com/fwlink/?LinkId=24433).</span></span>  
  
     <span data-ttu-id="e2792-129">本書提供規劃伺服器儲存的資訊，以及設計和部署檔案伺服器、列印伺服器以及中大型組織的終端機伺服器之資訊。</span><span class="sxs-lookup"><span data-stu-id="e2792-129">This book provides information about planning server storage, and information about designing and deploying file servers, print servers, and terminal servers in medium and large organizations.</span></span>  
  
-   <span data-ttu-id="e2792-130">**增加可用性，以便讓 BizTalk Server**，可在[http://go.microsoft.com/fwlink/?LinkId=130457](http://go.microsoft.com/fwlink/?LinkId=130457)。</span><span class="sxs-lookup"><span data-stu-id="e2792-130">**Increasing Availability for BizTalk Server**, available at [http://go.microsoft.com/fwlink/?LinkId=130457](http://go.microsoft.com/fwlink/?LinkId=130457).</span></span>  
  
     <span data-ttu-id="e2792-131">區段[BizTalk Server 作業指南](http://go.microsoft.com/fwlink/?LinkId=130458)描述您可以提高可用性的方式您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。</span><span class="sxs-lookup"><span data-stu-id="e2792-131">Section of the [BizTalk Server Operations Guide](http://go.microsoft.com/fwlink/?LinkId=130458) that describes ways you can increase the availability of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2792-132">本節內容</span><span class="sxs-lookup"><span data-stu-id="e2792-132">In This Section</span></span>  
  
-   [<span data-ttu-id="e2792-133">為 BizTalk 主控件提供高可用性</span><span class="sxs-lookup"><span data-stu-id="e2792-133">Providing High Availability for BizTalk Hosts</span></span>](../core/providing-high-availability-for-biztalk-hosts.md)  
  
-   [<span data-ttu-id="e2792-134">為 BizTalk Server 資料庫提供高可用性</span><span class="sxs-lookup"><span data-stu-id="e2792-134">Providing High Availability for BizTalk Server Databases</span></span>](../core/providing-high-availability-for-biztalk-server-databases.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2792-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2792-135">See Also</span></span>  
 <span data-ttu-id="e2792-136">[BizTalk Server 高可用性實例範例](../core/sample-biztalk-server-high-availability-scenarios.md) </span><span class="sxs-lookup"><span data-stu-id="e2792-136">[Sample BizTalk Server High Availability Scenarios](../core/sample-biztalk-server-high-availability-scenarios.md) </span></span>  
 [<span data-ttu-id="e2792-137">使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2</span><span class="sxs-lookup"><span data-stu-id="e2792-137">Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2</span></span>](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)