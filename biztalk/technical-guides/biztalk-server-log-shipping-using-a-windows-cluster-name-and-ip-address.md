---
title: BizTalk Server 記錄傳送使用 Windows 叢集名稱和 IP 位址 |Microsoft 文件
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
ms.openlocfilehash: 8619ea6c4eea3eefee5b86282a29e0165d0fb074
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22300062"
---
# <a name="biztalk-server-log-shipping-using-a-windows-cluster-name-and-ip-address"></a><span data-ttu-id="7ff73-102">BizTalk Server 記錄傳送使用 Windows 叢集名稱和 IP 位址</span><span class="sxs-lookup"><span data-stu-id="7ff73-102">BizTalk Server Log Shipping Using a Windows Cluster Name and IP Address</span></span>
<span data-ttu-id="7ff73-103">可簡化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用兩個執行個體的記錄傳送[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集中，為來源和目的地伺服器中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送案例。</span><span class="sxs-lookup"><span data-stu-id="7ff73-103">It is possible to simplify [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping by using two instances of a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster as the source and destination servers in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping scenario.</span></span> <span data-ttu-id="7ff73-104">然後，萬一嚴重損壞修復事件發生資料庫復原已簡化藉由只切換的名稱和叢集相關聯的 IP 位址資源[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體，如下所述。</span><span class="sxs-lookup"><span data-stu-id="7ff73-104">Then, in the event of a disaster recovery event, database recovery is simplified by merely switching the name and IP address resources associated with the clustered [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances as described below.</span></span> <span data-ttu-id="7ff73-105">使用這個方式時無須執行 UpdateDatabase.vbs 指令碼，如本主題所述[如何還原資料庫中 「 備份 BizTalk Server 」 工作](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)因為資料庫名稱不會變更。</span><span class="sxs-lookup"><span data-stu-id="7ff73-105">When using this approach there is no need to run the UpdateDatabase.vbs script as described in the topic [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md) because the database name is unchanged.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ff73-106">若要增加的叢集容錯[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體，叢集[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]應該地理分隔執行個體。</span><span class="sxs-lookup"><span data-stu-id="7ff73-106">To increase fault tolerance for the clustered [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances, the clustered [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances should be geographically separated.</span></span>  
  
### <a name="to-implement-biztalk-server-log-shipping-using-a-windows-server-cluster-name-and-ip-address-resource"></a><span data-ttu-id="7ff73-107">為了實作 BizTalk Server 記錄傳送，並使用 Windows Server 叢集名稱和 IP 位址資源</span><span class="sxs-lookup"><span data-stu-id="7ff73-107">To implement BizTalk Server log shipping using a Windows Server Cluster name and IP address resource</span></span>  
  
1.  <span data-ttu-id="7ff73-108">停止生產環境 BizTalk 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7ff73-108">Stop the production BizTalk servers.</span></span>  
  
2.  <span data-ttu-id="7ff73-109">執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送還原至次要資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集。</span><span class="sxs-lookup"><span data-stu-id="7ff73-109">Perform a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping restore to the secondary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster.</span></span>  
  
3.  <span data-ttu-id="7ff73-110">請依照下列主題中所述的步驟[設定 BizTalk Server 記錄傳送](../technical-guides/configuring-biztalk-server-log-shipping.md)重新設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送，讓次要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體現在是來源群組和主要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體現在是目的地群組。</span><span class="sxs-lookup"><span data-stu-id="7ff73-110">Follow the steps described in the topic [Configuring BizTalk Server Log Shipping](../technical-guides/configuring-biztalk-server-log-shipping.md) to reconfigure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping so that the secondary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster instance is now the source group and the primary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster instance is now the destination group.</span></span>  
  
4.  <span data-ttu-id="7ff73-111">停止 IP 和網路名稱資源的主要 PublicSQLClustername[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="7ff73-111">Stop the IP and network name resource PublicSQLClustername on the primary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster instance.</span></span>  
  
5.  <span data-ttu-id="7ff73-112">設定並啟動 PublicSQLClustername IP 和網路名稱叢集資源在次要複本上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="7ff73-112">Configure and start the PublicSQLClustername IP and network name cluster resources on the secondary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster instance.</span></span>  
  
6.  <span data-ttu-id="7ff73-113">啟動實際 BizTalk 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7ff73-113">Start the production BizTalk servers.</span></span>  
  
7.  <span data-ttu-id="7ff73-114">確認記錄傳送還原。</span><span class="sxs-lookup"><span data-stu-id="7ff73-114">Verify the log-shipping restore.</span></span>  
  
8.  <span data-ttu-id="7ff73-115">啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相關將生產站台上的服務。</span><span class="sxs-lookup"><span data-stu-id="7ff73-115">Start [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] related services on the production site.</span></span>  
  
 <span data-ttu-id="7ff73-116">執行這些步驟之後，BizTalk 群組指向次要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集執行個體，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="7ff73-116">After performing these steps, the BizTalk group is pointing to the secondary [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster instance as illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="7ff73-117">下圖說明如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送所使用的兩個叢集執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和移動叢集的名稱和 IP 位址資源。</span><span class="sxs-lookup"><span data-stu-id="7ff73-117">The following figure illustrates how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping by using two clustered instances of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and moving the clustered name and IP address resource.</span></span>  
  
 <span data-ttu-id="7ff73-118">![BizTalk 記錄傳送使用叢集名稱和 IP](../technical-guides/media/5055689e-c26b-4077-a531-74a50fec1393.gif "5055689e-c26b-4077-a531-74a50fec1393")</span><span class="sxs-lookup"><span data-stu-id="7ff73-118">![BizTalk Log Shipping using a Cluster name and IP](../technical-guides/media/5055689e-c26b-4077-a531-74a50fec1393.gif "5055689e-c26b-4077-a531-74a50fec1393")</span></span>  
  
 <span data-ttu-id="7ff73-119">**使用 Windows Server 叢集名稱和 IP 位址資源的 BizTalk Server 記錄傳送實作**</span><span class="sxs-lookup"><span data-stu-id="7ff73-119">**BizTalk Server Log Shipping implementation using Windows Server cluster name and IP address resources**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff73-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ff73-120">See Also</span></span>  
 <span data-ttu-id="7ff73-121">[資料庫的高可用性](../technical-guides/high-availability-for-databases.md) </span><span class="sxs-lookup"><span data-stu-id="7ff73-121">[High Availability for Databases](../technical-guides/high-availability-for-databases.md) </span></span>  
 <span data-ttu-id="7ff73-122">[設定 BizTalk Server 記錄傳送](../technical-guides/configuring-biztalk-server-log-shipping.md) </span><span class="sxs-lookup"><span data-stu-id="7ff73-122">[Configuring BizTalk Server Log Shipping](../technical-guides/configuring-biztalk-server-log-shipping.md) </span></span>  
 [<span data-ttu-id="7ff73-123">如何還原 「 備份 BizTalk Server 」 工作中的資料庫</span><span class="sxs-lookup"><span data-stu-id="7ff73-123">How to Restore Databases in the Backup BizTalk Server Job</span></span>](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)