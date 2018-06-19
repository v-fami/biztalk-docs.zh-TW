---
title: 檢閱及測試 SQL Server 叢集的容錯移轉案例的設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dbeb383-5b38-4467-acf8-2a5b244e5fa9
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8e7bed17960700aee84631801e3e26cb05b25c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302214"
---
# <a name="reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios"></a><span data-ttu-id="717d7-102">檢閱及測試 SQL Server 叢集組態的容錯移轉案例</span><span class="sxs-lookup"><span data-stu-id="717d7-102">Reviewing and Testing SQL Server Cluster Configuration for Failover Scenarios</span></span>
<span data-ttu-id="717d7-103">Windows 叢集和 SQL Server 可讓您執行 SQL Server 以主動/主動模式叢集的每個節點其中是 「 作用中 」 且正在執行一個以上的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="717d7-103">Windows Clustering and SQL Server allow you to run SQL Server in Active/Active mode where each node of the cluster is “active” and running one or more SQL Server instances.</span></span> <span data-ttu-id="717d7-104">這樣可讓您，比方說，有一個節點和所有其他 MessageBox 資料庫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]另一個節點上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="717d7-104">This would allow you, for example, to have the MessageBox database on one node and all other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases on the other node.</span></span> <span data-ttu-id="717d7-105">這可讓您以最大化叢集硬體的使用方式。</span><span class="sxs-lookup"><span data-stu-id="717d7-105">This allows you to maximize cluster hardware usage.</span></span>  
  
 <span data-ttu-id="717d7-106">如果您使用此設定，不過，您就必須確認每個節點，可以同時處理的所有 SQL Server 執行個體載入 SQL Server 叢集節點容錯移轉期間。</span><span class="sxs-lookup"><span data-stu-id="717d7-106">If you use this configuration, however, you must verify that each node can simultaneously handle the load of all SQL Server instances during a SQL Server cluster node failover.</span></span>  
  
## <a name="evaluating-failover-for-an-activeactive-cluster"></a><span data-ttu-id="717d7-107">評估為主動/主動叢集容錯移轉</span><span class="sxs-lookup"><span data-stu-id="717d7-107">Evaluating Failover for an Active/Active Cluster</span></span>  
 <span data-ttu-id="717d7-108">驗證單一節點可以處理的所有 SQL Server 執行個體發生 SQL Server 叢集節點容錯移轉的負載時的考量事項包括：</span><span class="sxs-lookup"><span data-stu-id="717d7-108">Considerations when verifying that a single node can handle the load of all SQL Server instances in the event of a SQL Server cluster node failover include:</span></span>  
  
-   <span data-ttu-id="717d7-109">容錯移轉節點是否有足夠的 CPU 資源？</span><span class="sxs-lookup"><span data-stu-id="717d7-109">Does the failover node have sufficient CPU resources?</span></span>  
  
-   <span data-ttu-id="717d7-110">容錯移轉節點是否有足夠的記憶體？</span><span class="sxs-lookup"><span data-stu-id="717d7-110">Does the failover node have sufficient memory?</span></span>  
  
-   <span data-ttu-id="717d7-111">是否有足夠的網路頻寬？</span><span class="sxs-lookup"><span data-stu-id="717d7-111">Is there sufficient network bandwidth?</span></span>  
  
-   <span data-ttu-id="717d7-112">容錯移轉節點可以處理更大的磁碟 I/O 競爭嗎？</span><span class="sxs-lookup"><span data-stu-id="717d7-112">Can the failover node handle the increased disk I/O contention?</span></span>  
  
 <span data-ttu-id="717d7-113">測試容錯移轉時，應該評估下列案例：</span><span class="sxs-lookup"><span data-stu-id="717d7-113">The following scenarios should be evaluated when testing failover:</span></span>  
  
-   <span data-ttu-id="717d7-114">使用中的伺服器上的電源故障</span><span class="sxs-lookup"><span data-stu-id="717d7-114">Power failure on the active server</span></span>  
  
-   <span data-ttu-id="717d7-115">被動伺服器上的電源故障</span><span class="sxs-lookup"><span data-stu-id="717d7-115">Power failure on the passive server</span></span>  
  
-   <span data-ttu-id="717d7-116">遺失磁碟的連線</span><span class="sxs-lookup"><span data-stu-id="717d7-116">Loss of disk connection</span></span>  
  
-   <span data-ttu-id="717d7-117">中斷作用中節點上的公用網路連線</span><span class="sxs-lookup"><span data-stu-id="717d7-117">Broken public network connection on the Active node</span></span>  
  
-   <span data-ttu-id="717d7-118">在使用中節點上中斷私人網路連線</span><span class="sxs-lookup"><span data-stu-id="717d7-118">Broken private network connection on the Active node</span></span>  
  
-   <span data-ttu-id="717d7-119">在被動節點上中斷公用網路連線</span><span class="sxs-lookup"><span data-stu-id="717d7-119">Broken public network connection on the Passive node</span></span>  
  
-   <span data-ttu-id="717d7-120">在被動節點上中斷私人網路連線</span><span class="sxs-lookup"><span data-stu-id="717d7-120">Broken private network connection on the Passive node</span></span>  
  
-   <span data-ttu-id="717d7-121">失敗的 SQL Server 服務</span><span class="sxs-lookup"><span data-stu-id="717d7-121">Failed SQL Server service</span></span>  
  
-   <span data-ttu-id="717d7-122">失敗的 SQL Server Agent 服務</span><span class="sxs-lookup"><span data-stu-id="717d7-122">Failed SQL Server Agent service</span></span>  
  
## <a name="using-an-activeactivepassive-cluster"></a><span data-ttu-id="717d7-123">使用主動/主動/被動叢集</span><span class="sxs-lookup"><span data-stu-id="717d7-123">Using an Active/Active/Passive Cluster</span></span>  
 <span data-ttu-id="717d7-124">如果您判斷有一個節點無法處理在容錯移轉案例中的所有 SQL Server 執行個體，另一個方法是使用主動/主動/被動叢集模型。</span><span class="sxs-lookup"><span data-stu-id="717d7-124">If you determine that one node cannot handle all SQL Server instances in a failover scenario, an alternative is to use an Active/Active/Passive clustering model.</span></span> <span data-ttu-id="717d7-125">主動/主動/被動叢集模型可大幅增加，永遠都會有一個被動節點可供容錯移轉案例的可能性。</span><span class="sxs-lookup"><span data-stu-id="717d7-125">The Active/Active/Passive clustering model greatly increases the likelihood that there will always be one Passive node available for failover scenarios.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="717d7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="717d7-126">See Also</span></span>  
 [<span data-ttu-id="717d7-127">檢查清單： 設定 SQL Server</span><span class="sxs-lookup"><span data-stu-id="717d7-127">Checklist: Configuring SQL Server</span></span>](~/technical-guides/checklist-configuring-sql-server.md)