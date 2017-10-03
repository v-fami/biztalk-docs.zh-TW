---
title: "規劃您的平台容錯 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- MessageBox database, fault tolerance
- clustering, fault tolerance
- SQL Server RAID
- databases [BAM], fault tolerance
- BizTalk Server, planning
- fault tolerance
- clustering, fail-overs
- planning, fault tolerance
- Primary Import database [BAM]
- BizTalk Server, backing up
- fault tolerance, planning
- planning, BizTalk Server
- Primary Import database [BAM], fault tolerance
- fail-over clustering
ms.assetid: 512ed6b8-db1e-434a-8009-63e952cf5500
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32cb8913ff48ed954e6e57140417966846641f54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-your-platform-for-fault-tolerance"></a><span data-ttu-id="e7406-102">規劃您的平台的容錯功能</span><span class="sxs-lookup"><span data-stu-id="e7406-102">Planning Your Platform for Fault Tolerance</span></span>
<span data-ttu-id="e7406-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是建立在 Microsoft Windows 與 Microsoft SQL Server 平台上。</span><span class="sxs-lookup"><span data-stu-id="e7406-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is built on the Microsoft Windows and Microsoft SQL Server platforms.</span></span> <span data-ttu-id="e7406-104">BizTalk Server 從嚴重損毀存留或復原的能力有賴於基礎平台的存留或復原的能力。</span><span class="sxs-lookup"><span data-stu-id="e7406-104">The ability of BizTalk Server to survive or recover from a disaster depends on the ability of the underlying platform to survive or recover.</span></span>  
  
 <span data-ttu-id="e7406-105">對於「商務活動監控」(BAM) 資料庫和 MessageBox 資料庫，建議您執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="e7406-105">For your Business Activity Monitoring (BAM) databases and your MessageBox database, we recommend you do the following:</span></span>  
  
-   <span data-ttu-id="e7406-106">設定 SQL Server Enterprise Edition 中所提供的容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="e7406-106">Set up fail-over clustering, which is available in SQL Server Enterprise Edition.</span></span> <span data-ttu-id="e7406-107">容錯移轉叢集可讓 SQL Server 從失敗的伺服器將 SQL Server 執行個體的處理自動切換至工作伺服器。</span><span class="sxs-lookup"><span data-stu-id="e7406-107">Fail-over clustering enables SQL Server to automatically switch the processing for an instance of SQL Server from a failed server to a working server.</span></span>  
  
     <span data-ttu-id="e7406-108">「BAM 主要匯入」資料庫收集事件資料。</span><span class="sxs-lookup"><span data-stu-id="e7406-108">The BAM Primary Import database collects event data.</span></span> <span data-ttu-id="e7406-109">在嚴重損毀的事件中，從上次備份寫入「BAM 主要匯入」資料庫中的資料會遺失。</span><span class="sxs-lookup"><span data-stu-id="e7406-109">In the event of a disaster, data that was written to the BAM Primary Import database since the last backup will be lost.</span></span> <span data-ttu-id="e7406-110">因為不可能重新產生遺失的事件，所以在「BAM 主要匯入」資料庫上啟用容錯移轉叢集顯得特別重要。</span><span class="sxs-lookup"><span data-stu-id="e7406-110">Because there is no way to regenerate lost events, it is especially important that you enable fail over clustering on your BAM Primary Import database.</span></span>  
  
-   <span data-ttu-id="e7406-111">使用 SQL Server RAID (獨立磁碟冗餘陣列)，特別是針對 MessageBox 資料庫與「BAM 主要匯入」資料庫。</span><span class="sxs-lookup"><span data-stu-id="e7406-111">Use SQL Server RAID (redundant array of independent disks), especially for the MessageBox database and the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="e7406-112">使用下列資源設計具有容錯功能的 Windows 與 SQL Server 部署。</span><span class="sxs-lookup"><span data-stu-id="e7406-112">Use the following resources to design your Windows and SQL Server deployments for fault tolerance.</span></span> <span data-ttu-id="e7406-113">請用一些時間瞭解硬體與伺服器備援技術，例如叢集和磁碟鏡像，以防止服務中斷和資料遺失。</span><span class="sxs-lookup"><span data-stu-id="e7406-113">Take time to learn about hardware and server redundancy technologies, such as clustering and disk mirroring, to prevent service outages and data loss.</span></span>  
  
-   [<span data-ttu-id="e7406-114">技術白皮書： 高可用性 — 永遠在技術上</span><span class="sxs-lookup"><span data-stu-id="e7406-114">White Paper: High Availability—Always On Technologies</span></span>](http://go.microsoft.com/fwlink/?LinkId=130376)  
  
     <span data-ttu-id="e7406-115">「 高可用性-永遠在線技術 」 白皮書描述 SQL Server 2008 中的可用的高可用性功能。</span><span class="sxs-lookup"><span data-stu-id="e7406-115">The “High Availability – Always On Technologies” whitepaper describes high availability features that are available with SQL Server 2008.</span></span>  
  
-   [<span data-ttu-id="e7406-116">高可用性解決方案概觀</span><span class="sxs-lookup"><span data-stu-id="e7406-116">High Availability Solutions Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=130377)  
  
     <span data-ttu-id="e7406-117">介紹幾個改善伺服器或資料庫可用性的 SQL Server 2008 高可用性解決方案。</span><span class="sxs-lookup"><span data-stu-id="e7406-117">Introduces several high-availability solutions for SQL Server 2008 that improve the availability of servers or databases.</span></span>  
  
-   [<span data-ttu-id="e7406-118">第 15 章-高可用性的選項，SQL Server Resource Kit</span><span class="sxs-lookup"><span data-stu-id="e7406-118">Chapter 15 - High Availability Options, SQL Server Resource Kit</span></span>](http://go.microsoft.com/fwlink/?LinkId=24431)  
  
     <span data-ttu-id="e7406-119">《Microsoft SQL Server Resource Kit》涵蓋廣泛的管理和部署規劃區域。</span><span class="sxs-lookup"><span data-stu-id="e7406-119">The Microsoft SQL Server Resource Kit covers a wide range of administrative and deployment planning areas.</span></span> <span data-ttu-id="e7406-120">第 15 章涵蓋容錯和修復的規劃。</span><span class="sxs-lookup"><span data-stu-id="e7406-120">Chapter 15 covers planning for fault tolerance and recovery.</span></span>  
  
-   [<span data-ttu-id="e7406-121">Windows 部署服務逐步指南</span><span class="sxs-lookup"><span data-stu-id="e7406-121">Windows Deployment Services Step-by-Step Guide</span></span>](http://go.microsoft.com/fwlink/?LinkId=130379)  
  
     <span data-ttu-id="e7406-122">包含如何使用 Windows Server 2008 中的 Windows 部署服務角色的逐步指引。</span><span class="sxs-lookup"><span data-stu-id="e7406-122">Contains step-by-step guidance for how to use the Windows Deployment Services role in Windows Server 2008</span></span>  
  
-   <span data-ttu-id="e7406-123">[Windows Server 2003 Deployment Kit: Planning Server Deployments](http://go.microsoft.com/fwlink/?LinkId=24433)。</span><span class="sxs-lookup"><span data-stu-id="e7406-123">[Windows Server 2003 Deployment Kit: Planning Server Deployments](http://go.microsoft.com/fwlink/?LinkId=24433).</span></span>  
  
     <span data-ttu-id="e7406-124">本書提供規劃伺服器儲存的資訊，以及設計和部署檔案伺服器、列印伺服器以及中大型組織的終端機伺服器之資訊。</span><span class="sxs-lookup"><span data-stu-id="e7406-124">This book provides information about planning server storage, and information about designing and deploying file servers, print servers, and terminal servers in medium and large organizations.</span></span>  
  
     <span data-ttu-id="e7406-125">您也可使用本書中的指導方針來規劃遠端伺服器管理、設計和部署伺服器叢集、以及設計和部署「網路負載平衡叢集」，以最大化伺服器的可用性和擴充性。</span><span class="sxs-lookup"><span data-stu-id="e7406-125">You can also use the guidelines in this book to maximize the availability and scalability of your servers by planning for remote server management, designing and deploying server clusters, and designing and deploying Network Load Balancing clusters.</span></span>  
  
## <a name="backing-up-your-platform"></a><span data-ttu-id="e7406-126">備份平台</span><span class="sxs-lookup"><span data-stu-id="e7406-126">Backing Up Your Platform</span></span>  
 <span data-ttu-id="e7406-127">在您設定系統後，請為伺服器準備完整備份，這樣您才可以在發生資料遺失事件時快速還原完全相同的伺服器。</span><span class="sxs-lookup"><span data-stu-id="e7406-127">After you have configured your system, prepare full backups of your servers so you can quickly restore an identical server in the event of data loss.</span></span>  
  
 <span data-ttu-id="e7406-128">若要備份平台，請為以下每個技術執行記錄的備份程序：</span><span class="sxs-lookup"><span data-stu-id="e7406-128">To back up your platform, perform the documented backup procedures for each of the following technologies:</span></span>  
  
-   <span data-ttu-id="e7406-129">Microsoft Windows Server Standard、Enterprise 或 Datacenter Edition</span><span class="sxs-lookup"><span data-stu-id="e7406-129">Microsoft Windows Server Standard, Enterprise, or Datacenter Edition</span></span>  
  
-   <span data-ttu-id="e7406-130">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="e7406-130">Internet Information Services (IIS)</span></span>  
  
-   <span data-ttu-id="e7406-131">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="e7406-131">Microsoft SQL Server</span></span>  
  
-   <span data-ttu-id="e7406-132">Windows SharePoint Services (由 Windows SharePoint Services 配接器所使用)。</span><span class="sxs-lookup"><span data-stu-id="e7406-132">Windows SharePoint Services, which is used by the Windows SharePoint Services adapter.</span></span>  
  
 <span data-ttu-id="e7406-133">請遵循 「 備份 BizTalk Server 」 可在 「 BizTalk Server 作業指南 》 中的建議[檢查清單： 提高可用性與災害復原](http://go.microsoft.com/fwlink/?LinkId=130498)。</span><span class="sxs-lookup"><span data-stu-id="e7406-133">Follow the recommendations in the “BizTalk Server Operations Guide” for “Backing up BizTalk Server” available at [Checklist: Increasing Availability with Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=130498).</span></span>  
  
 <span data-ttu-id="e7406-134">完整地測試備份和還原程序，並將它們放在安全的遠端位置中。</span><span class="sxs-lookup"><span data-stu-id="e7406-134">Thoroughly test your backup and restore procedures, and put them in a safe, remote location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7406-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7406-135">See Also</span></span>  
 [<span data-ttu-id="e7406-136">備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="e7406-136">Backing Up and Restoring the BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-the-biztalk-server-databases.md)