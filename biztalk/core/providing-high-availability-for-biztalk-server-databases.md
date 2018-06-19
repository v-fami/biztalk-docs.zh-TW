---
title: BizTalk Server 資料庫提供高可用性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- clustering, SQL Servers
- databases, architecture
- SQL Server, clustering
- servers, clustering
- databases, high availability
- architecture
- databases, clustering
- BizTalk Server, architecture
- Windows clustering
- high availability, databases
- clustering, databases
- data, persistence
- SQL Server Analysis Services
ms.assetid: 47fbc402-9e46-41dd-bc12-d1cde1982576
caps.latest.revision: 41
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3648a8f6d48bbfd6cf67995e1d314511b70db7bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269342"
---
# <a name="providing-high-availability-for-biztalk-server-databases"></a><span data-ttu-id="8b4f6-102">為 BizTalk Server 資料庫提供高可用性</span><span class="sxs-lookup"><span data-stu-id="8b4f6-102">Providing High Availability for BizTalk Server Databases</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8b4f6-103"> 高度依賴 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 以保存資料。</span><span class="sxs-lookup"><span data-stu-id="8b4f6-103"> relies heavily on [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] for data persistence.</span></span> <span data-ttu-id="8b4f6-104">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中所有其他元件和主控件在整合不同的商業應用程式的程序中都有特定的角色 (例如，接收、處理或路由訊息)，但是資料庫電腦會擷取此工作並將它保存到磁碟中。</span><span class="sxs-lookup"><span data-stu-id="8b4f6-104">All other components and hosts in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] have specific roles in the process of integrating disparate business applications (for example, receiving, processing, or routing messages), but the database computer captures this work and persists it to disk.</span></span>  
  
 <span data-ttu-id="8b4f6-105">若要提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，來設定執行 SQL Server 建立伺服器叢集的兩個資料庫電腦使用 Windows Server 容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="8b4f6-105">To provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, use Windows Server Failover Clustering to configure two database computers that are running SQL Server to create a server cluster.</span></span> <span data-ttu-id="8b4f6-106">伺服器叢集會為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫提供備援和容錯。</span><span class="sxs-lookup"><span data-stu-id="8b4f6-106">Server clustering provides redundancy and fault tolerance for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span> <span data-ttu-id="8b4f6-107">不像載入平衡叢集是以一組電腦一起運作以增加可用性和延展性，伺服器叢集通常包含兩個一組的主動/被動組態的資料庫電腦，如此，其中一部電腦即可為另一部電腦提供備份資源。</span><span class="sxs-lookup"><span data-stu-id="8b4f6-107">Unlike load-balanced clustering, where a group of computers functions together to increase availability and scalability, server clustering typically involves a pair of database computers in an active/passive configuration so that one computer provides backup resources for the other.</span></span>  
  
 <span data-ttu-id="8b4f6-108">下圖顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫層透過主動/被動伺服器叢集提供高可用性。</span><span class="sxs-lookup"><span data-stu-id="8b4f6-108">The following figure shows a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database tier with high availability through active/passive server clustering.</span></span>  
  
 <span data-ttu-id="8b4f6-109">![BizTalk Server 資料庫層](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")</span><span class="sxs-lookup"><span data-stu-id="8b4f6-109">![BizTalk Server Database Tier](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")</span></span>  
  
 <span data-ttu-id="8b4f6-110">若主動資料庫電腦發生錯誤或失敗，則被動電腦會變成主動並掌控資料庫資源，直到失敗的電腦修復為止。</span><span class="sxs-lookup"><span data-stu-id="8b4f6-110">If the active database computer encounters errors or fails, the passive computer becomes active and assumes control over the database resources until the failed computer is repaired.</span></span> <span data-ttu-id="8b4f6-111">資料庫服務會容錯移轉，並將資料連接還原至新的作用中電腦，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式繼續運作。</span><span class="sxs-lookup"><span data-stu-id="8b4f6-111">The database service fails over and restores data connections to the new active computer and enables the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application to continue functioning.</span></span>  
  
 <span data-ttu-id="8b4f6-112">如需安裝的資料庫資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[BizTalk Server 中的資料庫](../core/databases-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8b4f6-112">For information about the databases that are installed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Databases in BizTalk Server](../core/databases-in-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="8b4f6-113">如需備份您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="8b4f6-113">For information about backing up your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b4f6-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="8b4f6-114">In This Section</span></span>  
  
-   [<span data-ttu-id="8b4f6-115">向外延展資料庫</span><span class="sxs-lookup"><span data-stu-id="8b4f6-115">Scaled-Out Databases</span></span>](../core/scaled-out-databases.md)  
  
-   [<span data-ttu-id="8b4f6-116">叢集 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="8b4f6-116">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)  
  
-   [<span data-ttu-id="8b4f6-117">SQL Server 容錯移轉期間的 BizTalk Server 主控件執行個體的行為</span><span class="sxs-lookup"><span data-stu-id="8b4f6-117">Behavior of BizTalk Server Host Instances during SQL Server Failover</span></span>](../core/behavior-of-biztalk-server-host-instances-during-sql-server-failover.md)  
  
-   [<span data-ttu-id="8b4f6-118">SQL Server 資料庫鏡像磁碟區陰影複製服務和 AlwaysOn</span><span class="sxs-lookup"><span data-stu-id="8b4f6-118">SQL Server database mirroring, Volume Shadow Copy service and AlwaysOn</span></span>](../core/sql-server-database-mirroring-volume-shadow-copy-service-and-alwayson.md)  
  
## <a name="see-also"></a><span data-ttu-id="8b4f6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b4f6-119">See Also</span></span>  
 <span data-ttu-id="8b4f6-120">[為 BizTalk 主控件提供高可用性](../core/providing-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="8b4f6-120">[Providing High Availability for BizTalk Hosts](../core/providing-high-availability-for-biztalk-hosts.md) </span></span>  
 [<span data-ttu-id="8b4f6-121">BizTalk Server 高可用性實例範例</span><span class="sxs-lookup"><span data-stu-id="8b4f6-121">Sample BizTalk Server High Availability Scenarios</span></span>](../core/sample-biztalk-server-high-availability-scenarios.md)