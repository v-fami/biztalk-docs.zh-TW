---
title: 叢集主要密碼伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14aa3622-8462-4ed9-abde-40090d4f96ff
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c19702cfa7179399ee89f6799b65f1d2cec27a3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977295"
---
# <a name="clustering-the-master-secret-server"></a><span data-ttu-id="ce7b6-102">叢集主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="ce7b6-102">Clustering the Master Secret Server</span></span>
<span data-ttu-id="ce7b6-103">BizTalk Server 應用程式服務會維護硬式編碼相依性會隨企業單一登入 (SSO) 服務時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-103">The BizTalk Server application service maintains a hard-coded dependency upon the Enterprise Single Sign-On (SSO) service that is installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="ce7b6-104">SSO 服務必須能夠與啟動主要密碼伺服器進行通訊。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-104">The SSO service must be able to communicate with the master secret server to start.</span></span> <span data-ttu-id="ce7b6-105">我們建議您在主要密碼伺服器提供容錯功能的主要密碼伺服器上叢集化 SSO 服務。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-105">We recommend that you cluster the SSO service on the master secret server to provide fault tolerance for the master secret server.</span></span> <span data-ttu-id="ce7b6-106">如需詳細資訊，請參閱 <<c0> [ 高可用性 SSO 安裝選項](http://go.microsoft.com/fwlink/?LinkId=156838)(<http://go.microsoft.com/fwlink/?LinkId=156838>) 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-106">For more information, see [High-Availability SSO Installation Options](http://go.microsoft.com/fwlink/?LinkId=156838) (<http://go.microsoft.com/fwlink/?LinkId=156838>) in BizTalk Server Help.</span></span>  
  
## <a name="preparing-for-clustering-the-master-secret-server"></a><span data-ttu-id="ce7b6-107">正在準備叢集主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="ce7b6-107">Preparing for Clustering the Master Secret Server</span></span>  
  
### <a name="deciding-whether-to-use-a-dedicated-cluster-or-the-sql-server-cluster"></a><span data-ttu-id="ce7b6-108">決定是否要使用專用的叢集或 SQL Server 叢集</span><span class="sxs-lookup"><span data-stu-id="ce7b6-108">Deciding Whether to Use a Dedicated Cluster or the SQL Server Cluster</span></span>  
 <span data-ttu-id="ce7b6-109">叢集硬體很昂貴。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-109">Clustering hardware is expensive.</span></span> <span data-ttu-id="ce7b6-110">若要減少高度可用的方案的硬體資源，可以將主要密碼伺服器新增為叢集資源，您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫叢集。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-110">To reduce the hardware resources for a highly available solution, you can add the master secret server as a cluster resource in your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database cluster.</span></span> <span data-ttu-id="ce7b6-111">如果您使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫叢集，建議您不要讓主要密碼伺服器與 MessageBox 資料庫相同的作用中節點上。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-111">If you use the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database cluster, we recommend that you do not put the master secret server on the same active node as the MessageBox database.</span></span> <span data-ttu-id="ce7b6-112">MessageBox 資料庫會比其他資料庫通常較忙碌。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-112">The MessageBox database is usually busier than other databases.</span></span> <span data-ttu-id="ce7b6-113">即使主要密碼伺服器不會消耗許多硬體資源，最好是將它移至不同的使用中叢集節點中，從 [作用中的 MessageBox 資料庫] 節點。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-113">Even though the master secret server doesn't consume many hardware resources, it is better to move it to a different active cluster node from the active MessageBox database node.</span></span>  
  
### <a name="clustering-the-sso-database"></a><span data-ttu-id="ce7b6-114">叢集 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="ce7b6-114">Clustering the SSO Database</span></span>  
 <span data-ttu-id="ce7b6-115">主要密碼伺服器會取決於 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-115">The master secret server depends on the SSO database.</span></span> <span data-ttu-id="ce7b6-116">若要建置高可用性 SSO，您必須叢集化 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-116">To build a high-availability SSO, you must cluster the SSO database.</span></span> <span data-ttu-id="ce7b6-117">如需叢集化 BizTalk 資料庫的詳細資訊，請參閱[叢集 BizTalk Server 資料庫 2](../technical-guides/clustering-the-biztalk-server-databases2.md)。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-117">For more information about clustering BizTalk databases, see [Clustering the BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md).</span></span>  
  
### <a name="creating-domain-groups-and-accounts"></a><span data-ttu-id="ce7b6-118">建立網域群組和帳戶</span><span class="sxs-lookup"><span data-stu-id="ce7b6-118">Creating Domain Groups and Accounts</span></span>  
 <span data-ttu-id="ce7b6-119">您需要設定下列網域群組和帳戶，再叢集主要密碼伺服器：</span><span class="sxs-lookup"><span data-stu-id="ce7b6-119">You need to configure the following domain groups and accounts before clustering the master secret server:</span></span>  
  
-   <span data-ttu-id="ce7b6-120">以 SSO 系統管理員和 SSO 分支機構系統管理員的名稱建立網域群組。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-120">Create domain groups with the names SSO Administrators and SSO Affiliate Administrators.</span></span> <span data-ttu-id="ce7b6-121">若要建立叢集 「 企業單一登入 」 服務執行個體，您必須建立 「 SSO 系統管理員 」 和 「 SSO 分支機構系統管理員群組做為網域群組。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-121">To create a clustered instance of the Enterprise SSO service, you must create the SSO Administrators and SSO Affiliate Administrators groups as domain groups.</span></span>  
  
-   <span data-ttu-id="ce7b6-122">建立或指定的 SSO 系統管理員網域群組成員的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-122">Create or designate a domain account that is a member of the SSO Administrators domain group.</span></span> <span data-ttu-id="ce7b6-123">每個節點上的「企業單一登入」服務會設定為以此網域帳戶的身分登入。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-123">The Enterprise SSO service on each node will be configured to log on as this domain account.</span></span> <span data-ttu-id="ce7b6-124">這個帳戶必須在叢集中的每個節點上的 「 以服務方式登入 」 權限。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-124">This account must have the "Log on as a service" right on each node in the cluster.</span></span> <span data-ttu-id="ce7b6-125">此帳戶必須也授與完全控制叢集存取權。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-125">This account must also be granted Full Control access to the cluster.</span></span>  
  
## <a name="clustering-the-master-secret-server"></a><span data-ttu-id="ce7b6-126">叢集主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="ce7b6-126">Clustering the Master Secret Server</span></span>  
 <span data-ttu-id="ce7b6-127">以下是供叢集化主要密碼伺服器的基本步驟：</span><span class="sxs-lookup"><span data-stu-id="ce7b6-127">Here are the basic steps for clustering the master secret server:</span></span>  
  
1. <span data-ttu-id="ce7b6-128">安裝及設定企業單一登入叢集節點上。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-128">Install and configure Enterprise SSO on the cluster nodes.</span></span>  
  
2. <span data-ttu-id="ce7b6-129">建立叢集化 「 企業單一登入資源和相依的資源。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-129">Create the clustered Enterprise SSO resource and the dependent resources.</span></span>  
  
3. <span data-ttu-id="ce7b6-130">還原第二個叢集節點上的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-130">Restore the master secret on the second cluster node.</span></span> <span data-ttu-id="ce7b6-131">如果您將主要密碼伺服器移到叢集時，您必須還原主要祕密，第一個叢集節點上。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-131">If you move the master secret server to the cluster, you must restore the master secret on the first cluster node as well.</span></span>  
  
4. <span data-ttu-id="ce7b6-132">將包含 SSO 服務、 線上叢集群組。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-132">Bring the cluster group that contains the SSO service, online.</span></span>  
  
5. <span data-ttu-id="ce7b6-133">更新 「 管理 」 資料庫中的主要祕密名稱。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-133">Update the master secret name in the Management database.</span></span>  
  
   <span data-ttu-id="ce7b6-134">如需叢集主要密碼伺服器的詳細步驟，請參閱[如何叢集化主要密碼伺服器](http://go.microsoft.com/fwlink/?LinkId=156839)(<http://go.microsoft.com/fwlink/?LinkId=156839>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="ce7b6-134">For detailed steps on clustering the master secret server, see [How to Cluster the Master Secret Server](http://go.microsoft.com/fwlink/?LinkId=156839) (<http://go.microsoft.com/fwlink/?LinkId=156839>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce7b6-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce7b6-135">See Also</span></span>  
 [<span data-ttu-id="ce7b6-136">手動指定新的主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="ce7b6-136">Designating a New Master Secret Server Manually</span></span>](../technical-guides/designating-a-new-master-secret-server-manually.md)