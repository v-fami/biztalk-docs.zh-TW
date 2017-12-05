---
title: "叢集主要密碼伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14aa3622-8462-4ed9-abde-40090d4f96ff
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f37997582cbd94d8bbb5eaee829eead0af85ad2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="clustering-the-master-secret-server"></a><span data-ttu-id="890bb-102">叢集主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="890bb-102">Clustering the Master Secret Server</span></span>
<span data-ttu-id="890bb-103">BizTalk Server 應用程式服務會維護硬式編碼相依性會隨企業單一登入 (SSO) 服務[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="890bb-103">The BizTalk Server application service maintains a hard-coded dependency upon the Enterprise Single Sign-On (SSO) service that is installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="890bb-104">SSO 服務必須能夠與啟動主要密碼伺服器進行通訊。</span><span class="sxs-lookup"><span data-stu-id="890bb-104">The SSO service must be able to communicate with the master secret server to start.</span></span> <span data-ttu-id="890bb-105">我們建議您在主要密碼伺服器提供容錯功能的主要密碼伺服器上叢集化 SSO 服務。</span><span class="sxs-lookup"><span data-stu-id="890bb-105">We recommend that you cluster the SSO service on the master secret server to provide fault tolerance for the master secret server.</span></span> <span data-ttu-id="890bb-106">如需詳細資訊，請參閱[高可用性 SSO 安裝選項](http://go.microsoft.com/fwlink/?LinkId=156838)(http://go.microsoft.com/fwlink/?LinkId=156838) 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="890bb-106">For more information, see [High-Availability SSO Installation Options](http://go.microsoft.com/fwlink/?LinkId=156838) (http://go.microsoft.com/fwlink/?LinkId=156838) in BizTalk Server Help.</span></span>  
  
## <a name="preparing-for-clustering-the-master-secret-server"></a><span data-ttu-id="890bb-107">正在準備叢集主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="890bb-107">Preparing for Clustering the Master Secret Server</span></span>  
  
### <a name="deciding-whether-to-use-a-dedicated-cluster-or-the-sql-server-cluster"></a><span data-ttu-id="890bb-108">決定是否要使用專用的叢集或 SQL Server 叢集</span><span class="sxs-lookup"><span data-stu-id="890bb-108">Deciding Whether to Use a Dedicated Cluster or the SQL Server Cluster</span></span>  
 <span data-ttu-id="890bb-109">叢集硬體是高度耗費資源。</span><span class="sxs-lookup"><span data-stu-id="890bb-109">Clustering hardware is expensive.</span></span> <span data-ttu-id="890bb-110">若要減少高度可用的方案的硬體資源，可將主要密碼伺服器新增為叢集資源，您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫叢集。</span><span class="sxs-lookup"><span data-stu-id="890bb-110">To reduce the hardware resources for a highly available solution, you can add the master secret server as a cluster resource in your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database cluster.</span></span> <span data-ttu-id="890bb-111">如果您使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫叢集上，建議您不要讓主要密碼伺服器上的 MessageBox 資料庫相同的作用中節點。</span><span class="sxs-lookup"><span data-stu-id="890bb-111">If you use the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database cluster, we recommend that you do not put the master secret server on the same active node as the MessageBox database.</span></span> <span data-ttu-id="890bb-112">通常與其他資料庫忙碌 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="890bb-112">The MessageBox database is usually busier than other databases.</span></span> <span data-ttu-id="890bb-113">即使主要密碼伺服器不會使用許多硬體資源，最好是將它移至不同的使用中叢集節點中，從使用中的 MessageBox 資料庫節點。</span><span class="sxs-lookup"><span data-stu-id="890bb-113">Even though the master secret server doesn't consume many hardware resources, it is better to move it to a different active cluster node from the active MessageBox database node.</span></span>  
  
### <a name="clustering-the-sso-database"></a><span data-ttu-id="890bb-114">叢集 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="890bb-114">Clustering the SSO Database</span></span>  
 <span data-ttu-id="890bb-115">主要密碼伺服器的 SSO 資料庫而定。</span><span class="sxs-lookup"><span data-stu-id="890bb-115">The master secret server depends on the SSO database.</span></span> <span data-ttu-id="890bb-116">若要建置高可用性 SSO，您必須叢集化 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="890bb-116">To build a high-availability SSO, you must cluster the SSO database.</span></span> <span data-ttu-id="890bb-117">如需叢集化 BizTalk 資料庫的詳細資訊，請參閱[叢集 BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md)。</span><span class="sxs-lookup"><span data-stu-id="890bb-117">For more information about clustering BizTalk databases, see [Clustering the BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md).</span></span>  
  
### <a name="creating-domain-groups-and-accounts"></a><span data-ttu-id="890bb-118">建立網域群組和帳戶</span><span class="sxs-lookup"><span data-stu-id="890bb-118">Creating Domain Groups and Accounts</span></span>  
 <span data-ttu-id="890bb-119">您需要設定下列網域群組和帳戶，再叢集主要密碼伺服器：</span><span class="sxs-lookup"><span data-stu-id="890bb-119">You need to configure the following domain groups and accounts before clustering the master secret server:</span></span>  
  
-   <span data-ttu-id="890bb-120">SSO 系統管理員和 SSO 分支機構系統管理員的名稱建立網域群組。</span><span class="sxs-lookup"><span data-stu-id="890bb-120">Create domain groups with the names SSO Administrators and SSO Affiliate Administrators.</span></span> <span data-ttu-id="890bb-121">若要建立企業單一登入服務的叢集執行個體，您必須建立 「 SSO 系統管理員 」 和 「 SSO 分支機構系統管理員群組做為網域群組。</span><span class="sxs-lookup"><span data-stu-id="890bb-121">To create a clustered instance of the Enterprise SSO service, you must create the SSO Administrators and SSO Affiliate Administrators groups as domain groups.</span></span>  
  
-   <span data-ttu-id="890bb-122">建立或指定的網域帳戶是 SSO 系統管理員的網域群組的成員。</span><span class="sxs-lookup"><span data-stu-id="890bb-122">Create or designate a domain account that is a member of the SSO Administrators domain group.</span></span> <span data-ttu-id="890bb-123">每個節點上的「企業單一登入」服務會設定為以此網域帳戶的身分登入。</span><span class="sxs-lookup"><span data-stu-id="890bb-123">The Enterprise SSO service on each node will be configured to log on as this domain account.</span></span> <span data-ttu-id="890bb-124">此帳戶必須具有 「 以服務方式登入 」 權限，叢集中的每個節點上。</span><span class="sxs-lookup"><span data-stu-id="890bb-124">This account must have the "Log on as a service" right on each node in the cluster.</span></span> <span data-ttu-id="890bb-125">此帳戶必須也授與完全控制叢集存取權。</span><span class="sxs-lookup"><span data-stu-id="890bb-125">This account must also be granted Full Control access to the cluster.</span></span>  
  
## <a name="clustering-the-master-secret-server"></a><span data-ttu-id="890bb-126">叢集主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="890bb-126">Clustering the Master Secret Server</span></span>  
 <span data-ttu-id="890bb-127">以下是供叢集化主要密碼伺服器的基本步驟：</span><span class="sxs-lookup"><span data-stu-id="890bb-127">Here are the basic steps for clustering the master secret server:</span></span>  
  
1.  <span data-ttu-id="890bb-128">安裝和設定叢集節點上的企業單一登入。</span><span class="sxs-lookup"><span data-stu-id="890bb-128">Install and configure Enterprise SSO on the cluster nodes.</span></span>  
  
2.  <span data-ttu-id="890bb-129">建立叢集化 「 企業單一登入資源和相依的資源。</span><span class="sxs-lookup"><span data-stu-id="890bb-129">Create the clustered Enterprise SSO resource and the dependent resources.</span></span>  
  
3.  <span data-ttu-id="890bb-130">還原第二個叢集節點上的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="890bb-130">Restore the master secret on the second cluster node.</span></span> <span data-ttu-id="890bb-131">如果您將主要密碼伺服器移至叢集時，您必須還原第一個叢集節點上的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="890bb-131">If you move the master secret server to the cluster, you must restore the master secret on the first cluster node as well.</span></span>  
  
4.  <span data-ttu-id="890bb-132">將包含 SSO 服務，線上叢集群組。</span><span class="sxs-lookup"><span data-stu-id="890bb-132">Bring the cluster group that contains the SSO service, online.</span></span>  
  
5.  <span data-ttu-id="890bb-133">更新管理資料庫中的主要密碼的名稱。</span><span class="sxs-lookup"><span data-stu-id="890bb-133">Update the master secret name in the Management database.</span></span>  
  
 <span data-ttu-id="890bb-134">如需叢集主要密碼伺服器的詳細步驟，請參閱[如何叢集化主要密碼伺服器](http://go.microsoft.com/fwlink/?LinkId=156839)(http://go.microsoft.com/fwlink/?LinkId=156839) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="890bb-134">For detailed steps on clustering the master secret server, see [How to Cluster the Master Secret Server](http://go.microsoft.com/fwlink/?LinkId=156839) (http://go.microsoft.com/fwlink/?LinkId=156839) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="890bb-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="890bb-135">See Also</span></span>  
 [<span data-ttu-id="890bb-136">手動指定新的主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="890bb-136">Designating a New Master Secret Server Manually</span></span>](../technical-guides/designating-a-new-master-secret-server-manually.md)