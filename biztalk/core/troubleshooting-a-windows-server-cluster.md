---
title: 疑難排解 Windows Server 叢集 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 283cf4cd-ce40-48b7-8549-9ab17d7d2c34
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da1159bafc42f6cfbf47621e3b846764e50e5267
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279958"
---
# <a name="troubleshooting-a-windows-server-cluster"></a><span data-ttu-id="9360e-102">疑難排解 Windows Server 叢集</span><span class="sxs-lookup"><span data-stu-id="9360e-102">Troubleshooting a Windows Server Cluster</span></span>
<span data-ttu-id="9360e-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援 Windows Server 叢集的使用，以提供主控件叢集的支援、提供企業單一登入 (SSO) 主要密碼的高可用性，並提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的高可用性。</span><span class="sxs-lookup"><span data-stu-id="9360e-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports the use of Windows Server cluster for host cluster support, to provide high availability for the Enterprise Single Sign-On (SSO) Master Secret, and to provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span> <span data-ttu-id="9360e-104">本主題提供一些在 Windows Server 叢集環境中使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的一般指導方針，並討論在 Windows Server 叢集環境中使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時可能會發生的一些已知問題。</span><span class="sxs-lookup"><span data-stu-id="9360e-104">This topic provides some general guidelines for using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a Windows Server cluster environment and discusses some known issues that may occur when using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a Windows Server cluster environment.</span></span>  
  
## <a name="general-guidelines"></a><span data-ttu-id="9360e-105">一般指導方針</span><span class="sxs-lookup"><span data-stu-id="9360e-105">General Guidelines</span></span>  
 <span data-ttu-id="9360e-106">請依照這些一般指導方針來最大化 Windows Server 叢集的產能，並且疑難排解可能會影響到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 Windows Server 叢集問題。</span><span class="sxs-lookup"><span data-stu-id="9360e-106">Follow these general guidelines to maximize productivity with Windows Server cluster and to troubleshoot Windows Server cluster problems that may affect [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
1.  <span data-ttu-id="9360e-107">完成[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]證明概念與 Windows Server 叢集虛擬的伺服器環境中的工作。</span><span class="sxs-lookup"><span data-stu-id="9360e-107">Complete [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] proof of concept work with a Windows Server cluster in a virtualized server environment.</span></span>  
  
     <span data-ttu-id="9360e-108">**適用於 Windows Server 2008 HYPER-V 角色可用來建立虛擬的伺服器環境。**</span><span class="sxs-lookup"><span data-stu-id="9360e-108">**The Hyper-V role available with Windows Server 2008 can be used to create a virtualized server environment.**</span></span>  
  
    -   <span data-ttu-id="9360e-109">關於 Windows Server 2008 HYPER-V 的詳細資訊，請參閱 「 虛擬化與合併 >，網址[http://go.microsoft.com/fwlink/?LinkID=121187](http://go.microsoft.com/fwlink/?LinkID=121187)。</span><span class="sxs-lookup"><span data-stu-id="9360e-109">For more information about Windows Server 2008 Hyper-V, see “Virtualization and Consolidation” at [http://go.microsoft.com/fwlink/?LinkID=121187](http://go.microsoft.com/fwlink/?LinkID=121187).</span></span>  
  
    -   <span data-ttu-id="9360e-110">如需有關優點的運用提供與 HYPER-V 虛擬化技術的深入資訊，請參閱 「 進階虛擬化優點的 Windows Server 2008 版本的 Enterprise 」 可以從下載技術白皮書[http://go.microsoft.com/fwlink/?LinkId=123530](http://go.microsoft.com/fwlink/?LinkId=123530)。</span><span class="sxs-lookup"><span data-stu-id="9360e-110">For more in depth information about the benefits of leveraging virtualization technology provided with Hyper-V, see the whitepaper "Advanced Virtualization Benefits of Windows Server 2008 Editions for the Enterprise" available for download at [http://go.microsoft.com/fwlink/?LinkId=123530](http://go.microsoft.com/fwlink/?LinkId=123530).</span></span>  
  
    -   <span data-ttu-id="9360e-111">使用 HYPER-V 建立的 Windows Server 2008 叢集的步驟時使用[http://go.microsoft.com/fwlink/?LinkId=129680](http://go.microsoft.com/fwlink/?LinkId=129680)。</span><span class="sxs-lookup"><span data-stu-id="9360e-111">Steps for using Hyper-V to create a Windows Server 2008 cluster are available at [http://go.microsoft.com/fwlink/?LinkId=129680](http://go.microsoft.com/fwlink/?LinkId=129680).</span></span>  
  
     <span data-ttu-id="9360e-112">執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]證明概念與 Windows Server 叢集虛擬的伺服器環境中的工作，可提供絕佳的彈性，並使用遠少於比所需的 Windows Server 叢集的硬體資源。</span><span class="sxs-lookup"><span data-stu-id="9360e-112">Doing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] proof of concept work with a Windows Server cluster in a virtualized server environment offers great flexibility and uses considerably fewer hardware resources than required for a Windows Server cluster.</span></span> <span data-ttu-id="9360e-113">如果使用這項做法，請對在主機電腦上同時執行的每部虛擬機器，都配置至少 512 MB 的記憶體，並對主機作業系統配置額外的 512 MB 記憶體。</span><span class="sxs-lookup"><span data-stu-id="9360e-113">If this approach is used, allocate at least 512 MB of memory for each virtual machine that is concurrently running on the host computer and an additional 512 MB of memory for the host operating system.</span></span> <span data-ttu-id="9360e-114">例如，針對使用五部虛擬機器之 Windows Server 叢集 (兩個 BizTalk Server 叢集節點、兩個 Microsoft SQL Server 叢集節點和一個網域控制站) 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解決方案，您應該規劃將 3 GB 的記憶體安裝在主機電腦上。</span><span class="sxs-lookup"><span data-stu-id="9360e-114">For example, for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution with a Windows Server cluster that uses five virtual machines (two BizTalk Server cluster nodes, two Microsoft SQL Server cluster nodes, and one domain controller), you would plan to have 3 GB of memory installed on the host computer.</span></span> <span data-ttu-id="9360e-115">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]概念證明環境需要超過 2 GB 的記憶體，請考慮 （HYPER-V 角色所需） 在主機電腦上安裝 64 位元版本的 Windows，以確保所有已安裝的記憶體是由主機作業系統可存取。</span><span class="sxs-lookup"><span data-stu-id="9360e-115">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] proof of concept environment requires more than 2 GB of memory, consider installing a 64-bit version of Windows on the host computer (required for the Hyper-V role) to ensure that all installed memory is accessible by the host operating system.</span></span>  
  
## <a name="troubleshooting-resources"></a><span data-ttu-id="9360e-116">疑難排解資源</span><span class="sxs-lookup"><span data-stu-id="9360e-116">Troubleshooting Resources</span></span>  
 <span data-ttu-id="9360e-117">**疑難排解 Windows Server 2008 容錯移轉叢集的資源**</span><span class="sxs-lookup"><span data-stu-id="9360e-117">**Resources for troubleshooting Windows Server 2008 failover clustering**</span></span>  
  
-   <span data-ttu-id="9360e-118">檢閱[容錯移轉叢集驗證及疑難排解 Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=129729) Microsoft TechNet 網站上的 TechNet 網路廣播。</span><span class="sxs-lookup"><span data-stu-id="9360e-118">Review the [Failover Cluster Validation and Troubleshooting with Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=129729) TechNet Webcast on the Microsoft TechNet Web site.</span></span> <span data-ttu-id="9360e-119">這個網路廣播說明如何疑難排解容錯移轉叢集驗證及疑難排解 Windows Server 2008。</span><span class="sxs-lookup"><span data-stu-id="9360e-119">This web cast describes how to troubleshoot failover cluster validation and troubleshooting with Windows Server 2008.</span></span>  
  
-   <span data-ttu-id="9360e-120">如需有關如何分析問題與 Windows Server 2008 容錯移轉叢集的詳細資訊，請檢閱本主題[檢視事件和記錄檔，容錯移轉叢集](http://go.microsoft.com/fwlink/?LinkId=129730)Microsoft TechNet 網站上。</span><span class="sxs-lookup"><span data-stu-id="9360e-120">For more information about analyzing problems with Windows Server 2008 failover clustering, review the topic [View Events and Logs for a Failover Cluster](http://go.microsoft.com/fwlink/?LinkId=129730) on the Microsoft TechNet Web site.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="9360e-121">已知問題</span><span class="sxs-lookup"><span data-stu-id="9360e-121">Known Issues</span></span>  
  
#### <a name="any-attempt-to-bring-a-clustered-msdtc-resource-online-fails-which-causes-dependent-biztalk-server-services-to-fail"></a><span data-ttu-id="9360e-122">嘗試將叢集的 MSDTC 資源連到線上結果失敗，進而造成相依的 BizTalk Server 服務失敗</span><span class="sxs-lookup"><span data-stu-id="9360e-122">Any attempt to bring a clustered MSDTC resource online fails which causes dependent BizTalk Server services to fail</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="9360e-123">問題</span><span class="sxs-lookup"><span data-stu-id="9360e-123">Problem</span></span>  
 <span data-ttu-id="9360e-124">叢集的分散式交易協調器 (MSDTC) 資源無法上線**上線**選項在叢集系統管理員，這會導致[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]依賴 MSDTC 的執行階段作業失敗的交易支援。</span><span class="sxs-lookup"><span data-stu-id="9360e-124">A clustered Distributed Transaction Coordinator (MSDTC) resource cannot be brought online through the **Bring Online** option in Cluster Administrator, which causes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time operations that are dependent upon MSDTC transaction support to fail.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="9360e-125">原因</span><span class="sxs-lookup"><span data-stu-id="9360e-125">Cause</span></span>  
 <span data-ttu-id="9360e-126">叢集 MSDTC 資源失敗可能因為下列數種原因而發生：</span><span class="sxs-lookup"><span data-stu-id="9360e-126">Clustered MSDTC resource failure can occur for a number of reasons including the following:</span></span>  
  
-   <span data-ttu-id="9360e-127">沒有以正確的「磁碟」和「網路名稱」資源相依性設定叢集 MSDTC 資源，或是資源相依性失敗。</span><span class="sxs-lookup"><span data-stu-id="9360e-127">The clustered MSDTC resource is not configured with the correct Disk and Network Name resource dependencies or the resource dependencies are failing.</span></span>  
  
-   <span data-ttu-id="9360e-128">權限問題阻止叢集 MSDTC 資源啟動。</span><span class="sxs-lookup"><span data-stu-id="9360e-128">Permissions problems are preventing the clustered MSDTC resource from being activated.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="9360e-129">解決方案</span><span class="sxs-lookup"><span data-stu-id="9360e-129">Resolution</span></span>  
 <span data-ttu-id="9360e-130">**完成 Windows Server 2008 叢集上的下列步驟：**</span><span class="sxs-lookup"><span data-stu-id="9360e-130">**Complete the following steps on a Windows Server 2008 cluster:**</span></span>  
  
-   <span data-ttu-id="9360e-131">請依照[檢查清單： Windows Server 2008 容錯移轉叢集中建立 MS DTC 資源](http://go.microsoft.com/fwlink/?LinkId=129677)Windows Server 2008 容錯移轉叢集上建立一或多個叢集的 MSDTC 資源。</span><span class="sxs-lookup"><span data-stu-id="9360e-131">Follow the steps in [Checklist: Creating an MS DTC Resource in a Windows Server 2008 Failover Cluster](http://go.microsoft.com/fwlink/?LinkId=129677) for creating one or more clustered MSDTC resources on a Windows Server 2008 failover cluster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9360e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9360e-132">See Also</span></span>  
 <span data-ttu-id="9360e-133">[使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="9360e-133">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="9360e-134">[叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md) </span><span class="sxs-lookup"><span data-stu-id="9360e-134">[Clustering the BizTalk Server Databases](../core/clustering-the-biztalk-server-databases1.md) </span></span>  
 <span data-ttu-id="9360e-135">[BizTalk Server 高可用性實例範例](../core/sample-biztalk-server-high-availability-scenarios.md) </span><span class="sxs-lookup"><span data-stu-id="9360e-135">[Sample BizTalk Server High Availability Scenarios](../core/sample-biztalk-server-high-availability-scenarios.md) </span></span>  
 [<span data-ttu-id="9360e-136">高可用性 SSO 安裝選項</span><span class="sxs-lookup"><span data-stu-id="9360e-136">High-Availability SSO Installation Options</span></span>](../core/high-availability-sso-installation-options.md)