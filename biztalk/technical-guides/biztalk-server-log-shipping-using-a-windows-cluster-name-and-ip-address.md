---
title: BizTalk Server 記錄傳送，並使用 Windows 叢集名稱和 IP 位址 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82ef6908-6009-4d06-8315-0bc85a0aad18
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1b3df08da6753a7f936bfca54ecfb69b86d058c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023420"
---
# <a name="biztalk-server-log-shipping-using-a-windows-cluster-name-and-ip-address"></a><span data-ttu-id="89275-102">BizTalk Server 記錄傳送使用 Windows 叢集名稱和 IP 位址</span><span class="sxs-lookup"><span data-stu-id="89275-102">BizTalk Server Log Shipping Using a Windows Cluster Name and IP Address</span></span>
<span data-ttu-id="89275-103">可簡化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送使用兩個執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集中，為來源和目的地伺服器在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送案例。</span><span class="sxs-lookup"><span data-stu-id="89275-103">It is possible to simplify [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping by using two instances of a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster as the source and destination servers in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping scenario.</span></span> <span data-ttu-id="89275-104">然後，災害復原事件，發生資料庫復原已簡化藉由只切換的名稱和 IP 位址資源與叢集相關聯[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體，如下所述。</span><span class="sxs-lookup"><span data-stu-id="89275-104">Then, in the event of a disaster recovery event, database recovery is simplified by merely switching the name and IP address resources associated with the clustered [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances as described below.</span></span> <span data-ttu-id="89275-105">使用這個方法時不是需要執行 UpdateDatabase.vbs 指令碼，如本主題中所述[如何在 「 備份 BizTalk Server 」 工作中的 還原資料庫](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)因為資料庫名稱是不變。</span><span class="sxs-lookup"><span data-stu-id="89275-105">When using this approach there is no need to run the UpdateDatabase.vbs script as described in the topic [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md) because the database name is unchanged.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89275-106">若要增加的叢集容錯[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體，叢集[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]應該地理上分隔執行個體。</span><span class="sxs-lookup"><span data-stu-id="89275-106">To increase fault tolerance for the clustered [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances, the clustered [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances should be geographically separated.</span></span>  
  
### <a name="to-implement-biztalk-server-log-shipping-using-a-windows-server-cluster-name-and-ip-address-resource"></a><span data-ttu-id="89275-107">若要實作 BizTalk Server 記錄傳送，並使用 Windows Server 叢集名稱和 IP 位址資源</span><span class="sxs-lookup"><span data-stu-id="89275-107">To implement BizTalk Server log shipping using a Windows Server Cluster name and IP address resource</span></span>  
  
1. <span data-ttu-id="89275-108">停止實際執行 BizTalk server。</span><span class="sxs-lookup"><span data-stu-id="89275-108">Stop the production BizTalk servers.</span></span>  
  
2. <span data-ttu-id="89275-109">執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送還原至次要資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集。</span><span class="sxs-lookup"><span data-stu-id="89275-109">Perform a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping restore to the secondary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster.</span></span>  
  
3. <span data-ttu-id="89275-110">請依照下列主題中所述的步驟[設定 BizTalk Server 記錄傳送](../technical-guides/configuring-biztalk-server-log-shipping.md)重新設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送，讓次要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體現在是來源群組和主要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體現在為目的群組。</span><span class="sxs-lookup"><span data-stu-id="89275-110">Follow the steps described in the topic [Configuring BizTalk Server Log Shipping](../technical-guides/configuring-biztalk-server-log-shipping.md) to reconfigure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping so that the secondary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster instance is now the source group and the primary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster instance is now the destination group.</span></span>  
  
4. <span data-ttu-id="89275-111">停止 IP 和網路名稱資源 PublicSQLClustername 主要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="89275-111">Stop the IP and network name resource PublicSQLClustername on the primary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster instance.</span></span>  
  
5. <span data-ttu-id="89275-112">設定並啟動次要複本上的 PublicSQLClustername IP 和網路名稱叢集資源[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="89275-112">Configure and start the PublicSQLClustername IP and network name cluster resources on the secondary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster instance.</span></span>  
  
6. <span data-ttu-id="89275-113">開始在實際執行的 BizTalk 伺服器。</span><span class="sxs-lookup"><span data-stu-id="89275-113">Start the production BizTalk servers.</span></span>  
  
7. <span data-ttu-id="89275-114">確認記錄傳送還原。</span><span class="sxs-lookup"><span data-stu-id="89275-114">Verify the log-shipping restore.</span></span>  
  
8. <span data-ttu-id="89275-115">啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相關生產網站上的服務。</span><span class="sxs-lookup"><span data-stu-id="89275-115">Start [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] related services on the production site.</span></span>  
  
   <span data-ttu-id="89275-116">執行這些步驟之後，BizTalk 群組指向次要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]如下圖所示的叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="89275-116">After performing these steps, the BizTalk group is pointing to the secondary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster instance as illustrated in the following figure.</span></span>  
  
   <span data-ttu-id="89275-117">下圖說明如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送所使用的兩個叢集的執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和移動叢集的名稱和 IP 位址資源。</span><span class="sxs-lookup"><span data-stu-id="89275-117">The following figure illustrates how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping by using two clustered instances of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and moving the clustered name and IP address resource.</span></span>  
  
   <span data-ttu-id="89275-118">![BizTalk 記錄傳送使用叢集名稱和 IP](../technical-guides/media/5055689e-c26b-4077-a531-74a50fec1393.gif "5055689e-c26b-4077-a531-74a50fec1393")</span><span class="sxs-lookup"><span data-stu-id="89275-118">![BizTalk Log Shipping using a Cluster name and IP](../technical-guides/media/5055689e-c26b-4077-a531-74a50fec1393.gif "5055689e-c26b-4077-a531-74a50fec1393")</span></span>  
  
   <span data-ttu-id="89275-119">**BizTalk Server 記錄傳送的實作，使用 Windows Server 叢集名稱和 IP 位址資源**</span><span class="sxs-lookup"><span data-stu-id="89275-119">**BizTalk Server Log Shipping implementation using Windows Server cluster name and IP address resources**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89275-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89275-120">See Also</span></span>  
 <span data-ttu-id="89275-121">[資料庫的高可用性](../technical-guides/high-availability-for-databases.md) </span><span class="sxs-lookup"><span data-stu-id="89275-121">[High Availability for Databases](../technical-guides/high-availability-for-databases.md) </span></span>  
 <span data-ttu-id="89275-122">[設定 BizTalk Server 記錄傳送](../technical-guides/configuring-biztalk-server-log-shipping.md) </span><span class="sxs-lookup"><span data-stu-id="89275-122">[Configuring BizTalk Server Log Shipping](../technical-guides/configuring-biztalk-server-log-shipping.md) </span></span>  
 [<span data-ttu-id="89275-123">如何在備份 BizTalk Server 作業中還原資料庫</span><span class="sxs-lookup"><span data-stu-id="89275-123">How to Restore Databases in the Backup BizTalk Server Job</span></span>](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)