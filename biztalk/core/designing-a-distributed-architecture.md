---
title: 設計分散式的架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- clustering, SQL Servers
- SQL Server, clustering
ms.assetid: 8a8f1710-4d53-42bf-b5e5-2be3b43813b4
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 156c7107abfd0fd140a5e7b07f06d00eabf7c961
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239422"
---
# <a name="designing-a-distributed-architecture"></a><span data-ttu-id="85cd3-102">設計分散式架構</span><span class="sxs-lookup"><span data-stu-id="85cd3-102">Designing a Distributed Architecture</span></span>
<span data-ttu-id="85cd3-103">完成 BizTalk Server 部署的系統架構的詳細資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。</span><span class="sxs-lookup"><span data-stu-id="85cd3-103">For complete information about the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
 <span data-ttu-id="85cd3-104">主題中所提供的架構[大型分散式架構](../core/large-distributed-architecture.md)解決了許多 BizTalk 環境是易受攻擊的潛在安全性威脅。</span><span class="sxs-lookup"><span data-stu-id="85cd3-104">The architecture presented in the topic [Large Distributed Architecture](../core/large-distributed-architecture.md) addresses many of the potential security threats to which a BizTalk environment is vulnerable.</span></span> <span data-ttu-id="85cd3-105">在設計您的架構時，安全性在優先權清單上應該有高優先權，但是在分散式環境中還有其他考量，像是高可用性、延展性及效能。</span><span class="sxs-lookup"><span data-stu-id="85cd3-105">While security should be high on your list of priorities when designing your architecture, there are additional considerations in a distributed environment, such as high-availability, scalability, and performance.</span></span> <span data-ttu-id="85cd3-106">本節提供設計 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 架構時您可以考量的其他選項。</span><span class="sxs-lookup"><span data-stu-id="85cd3-106">This section provides additional options you can consider when designing your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architecture.</span></span>  
  
## <a name="domains"></a><span data-ttu-id="85cd3-107">定義域</span><span class="sxs-lookup"><span data-stu-id="85cd3-107">Domains</span></span>  
 <span data-ttu-id="85cd3-108">若公司大多數是執行外部式網際網路的通訊，則可以從公司網域移除內部網路服務。</span><span class="sxs-lookup"><span data-stu-id="85cd3-108">If your company performs mostly Internet-facing communications, you can remove the intranet services from the corporate domain.</span></span> <span data-ttu-id="85cd3-109">相反地，若您使用 BizTalk Server 來連接透過內部網路連線的其他應用程式或商務夥伴，則可以移除周邊網路。</span><span class="sxs-lookup"><span data-stu-id="85cd3-109">Conversely, if you use BizTalk Server to connect to other applications or business partners that connect through the intranet, you can remove the perimeter network.</span></span> <span data-ttu-id="85cd3-110">如果您的公司網際網路和內部網路對向通訊的夥伴數目很少，您可以考慮將內部網路服務與周邊網路結合。</span><span class="sxs-lookup"><span data-stu-id="85cd3-110">If your company does both Internet and intranet-facing communications with a small number of partners, you may consider combining the intranet services and the perimeter network.</span></span>  
  
 <span data-ttu-id="85cd3-111">若您要使資料網域中處理伺服器與 SQL Server 之間的通訊延遲降到最低，而且內部網路中像是網路探查、竄改封包，以及主控件安全防護等安全性問題不是考量重點時，則可以移除處理與資料網域之間的防火牆，並且合併這些網域。</span><span class="sxs-lookup"><span data-stu-id="85cd3-111">If you want to minimize the latency in the communication between the processing servers and the SQL Servers in the data domain, and security issues such as network sniffing, tampering of packets, and host spoofing in the internal network are not a concern, you can remove the firewall between the processing and data domain, and merge these domains.</span></span> <span data-ttu-id="85cd3-112">建議您使用「網際網路通訊協定安全性」(IPSec) 或「安全通訊端層」(SSL) 來保護伺服器之間傳輸的資料。</span><span class="sxs-lookup"><span data-stu-id="85cd3-112">It is recommended you then use Internet Protocol security (IPSec) or Secure Sockets Layer (SSL) to protect the data as it goes from one server to another.</span></span>  
  
## <a name="sql-server-clustering"></a><span data-ttu-id="85cd3-113">SQL Server 叢集</span><span class="sxs-lookup"><span data-stu-id="85cd3-113">SQL Server clustering</span></span>  
 <span data-ttu-id="85cd3-114">雖然本節並未詳細描述，但是我們仍強烈建議將您的資料庫組成叢集，以獲得容錯移轉保護。</span><span class="sxs-lookup"><span data-stu-id="85cd3-114">Although not described in detail in this section, we strongly recommend clustering your databases for failover protection.</span></span> <span data-ttu-id="85cd3-115">如需有關 SQL Server 2008 容錯移轉叢集的詳細資訊，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/?LinkId=131016](http://go.microsoft.com/fwlink/?LinkId=131016)。</span><span class="sxs-lookup"><span data-stu-id="85cd3-115">For more information about SQL Server 2008 failover clustering, see the Microsoft MSDN Web site at [http://go.microsoft.com/fwlink/?LinkId=131016](http://go.microsoft.com/fwlink/?LinkId=131016).</span></span>  
  
## <a name="messagebox-database"></a><span data-ttu-id="85cd3-116">MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="85cd3-116">MessageBox database</span></span>  
 <span data-ttu-id="85cd3-117">依據貴公司的訊息傳輸量需求，可能需要新增 (或移除) MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="85cd3-117">Depending on the message throughput requirements for your company, you may need to add (or remove) MessageBox databases.</span></span> <span data-ttu-id="85cd3-118">如需多個 messagebox 的詳細資訊，請參閱[Scaled-Out 資料庫](../core/scaled-out-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="85cd3-118">For more information about multiple messagebox, see [Scaled-Out Databases](../core/scaled-out-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85cd3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85cd3-119">See Also</span></span>  
 <span data-ttu-id="85cd3-120">[設計安全架構](../core/designing-a-secure-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="85cd3-120">[Designing a Secure Architecture](../core/designing-a-secure-architecture.md) </span></span>  
 <span data-ttu-id="85cd3-121">[高可用性規劃](../core/planning-for-high-availability3.md) </span><span class="sxs-lookup"><span data-stu-id="85cd3-121">[Planning for High Availability](../core/planning-for-high-availability3.md) </span></span>  
 <span data-ttu-id="85cd3-122">[持續性效能的規劃](../core/planning-for-sustained-performance.md) </span><span class="sxs-lookup"><span data-stu-id="85cd3-122">[Planning for Sustained Performance](../core/planning-for-sustained-performance.md) </span></span>  
 <span data-ttu-id="85cd3-123">[設計 BizTalk Server 的系統架構](../core/designing-the-system-architectures-for-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="85cd3-123">[Designing the System Architectures for BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md) </span></span>  
 [<span data-ttu-id="85cd3-124">BizTalk Server 架構範例</span><span class="sxs-lookup"><span data-stu-id="85cd3-124">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)