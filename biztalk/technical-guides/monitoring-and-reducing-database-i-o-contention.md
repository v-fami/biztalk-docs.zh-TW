---
title: "監視與降低資料庫的 I/O 競爭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd6d3343-3fa3-469a-9772-e94f22fdf558
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 446a4b512b4f38869637cb3968305fad1e869dae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-and-reducing-database-io-contention"></a><span data-ttu-id="038d4-102">監視和減少資料庫 I/O 競爭</span><span class="sxs-lookup"><span data-stu-id="038d4-102">Monitoring and Reducing Database I/O Contention</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="038d4-103">效能通常取決於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]依次通常預測有磁碟 I/O 效能時的效能。</span><span class="sxs-lookup"><span data-stu-id="038d4-103"> performance is often predicated upon [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance, which in turn is often predicated upon disk I/O performance.</span></span> <span data-ttu-id="038d4-104">因此，您應該監視和效能調整執行的電腦上的磁碟 I/O[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]該馬上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="038d4-104">Therefore, you should monitor and performance-tune disk I/O on the computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
## <a name="monitoring-disk-io"></a><span data-ttu-id="038d4-105">監視磁碟 I/O</span><span class="sxs-lookup"><span data-stu-id="038d4-105">Monitoring Disk I/O</span></span>  
 <span data-ttu-id="038d4-106">由於大量資料庫的本質之故[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、 磁碟 I/O 會變成 messagebox 是效能瓶頸和 BizTalk 追蹤資料庫; 這是 true 即使磁碟 I/O 先前尚未中的資料庫檔案是效能瓶頸您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="038d4-106">Because of the database-intensive nature of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], disk I/O can easily become a bottleneck on the MessageBox and BizTalk Tracking databases; this is true even if disk I/O has not previously been a bottleneck for the database files in your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] environment.</span></span> <span data-ttu-id="038d4-107">因此，我們建議您主動測量存放的資料和交易記錄檔磁碟的磁碟 I/O 效能。</span><span class="sxs-lookup"><span data-stu-id="038d4-107">Thus, we recommend that you proactively measure disk I/O performance for the disks that house the data and transaction log files.</span></span> <span data-ttu-id="038d4-108">如需有關如何監視磁碟 I/O 效能，使用 「 系統監視器的詳細資訊，請參閱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]文章[「 前置部署 I/O 最佳作法 」](http://go.microsoft.com/fwlink/?LinkId=104829) (http://go.microsoft.com/fwlink/?LinkId=104829)。</span><span class="sxs-lookup"><span data-stu-id="038d4-108">For more information about monitoring disk I/O performance using System Monitor, see the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] article ["Predeployment I/O Best Practices"](http://go.microsoft.com/fwlink/?LinkId=104829) (http://go.microsoft.com/fwlink/?LinkId=104829).</span></span> <span data-ttu-id="038d4-109">如果您使用 SAN，您可能也需要 SAN 硬體製造商，來測量磁碟 I/O 效能的特定工具。</span><span class="sxs-lookup"><span data-stu-id="038d4-109">If you are using a SAN, you may also need specific tools from the SAN hardware manufacturer to measure disk I/O performance.</span></span>  
  
## <a name="separating-the-messagebox-and-biztalk-tracking-dta-databases-and-log-files"></a><span data-ttu-id="038d4-110">分隔 MessageBox 和 BizTalk 追蹤 (DTA) 資料庫和記錄檔</span><span class="sxs-lookup"><span data-stu-id="038d4-110">Separating the MessageBox and BizTalk Tracking (DTA) Databases and Log Files</span></span>  
 <span data-ttu-id="038d4-111">由於 MessageBox 和 「 BizTalk 追蹤資料庫是最常使用，我們建議您針對每一種可降低發生問題的磁碟 I/O 競爭的可能性的專用磁碟機上放置資料檔和交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="038d4-111">Since the MessageBox and BizTalk Tracking databases are the most active, we recommend that you place the data files and transaction log files for each of these on dedicated drives to reduce the likelihood of problems with disk I/O contention.</span></span> <span data-ttu-id="038d4-112">例如，您需要四個磁碟機 MessageBox 和 「 BizTalk 追蹤資料庫檔案。一個磁碟機，如下列各項：</span><span class="sxs-lookup"><span data-stu-id="038d4-112">For example, you would need four drives for the MessageBox and BizTalk Tracking database files; one drive for each of the following:</span></span>  
  
-   <span data-ttu-id="038d4-113">MessageBox 資料檔案</span><span class="sxs-lookup"><span data-stu-id="038d4-113">MessageBox data files</span></span>  
  
-   <span data-ttu-id="038d4-114">MessageBox 交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="038d4-114">MessageBox transaction log files</span></span>  
  
-   <span data-ttu-id="038d4-115">BizTalk 追蹤資料檔案</span><span class="sxs-lookup"><span data-stu-id="038d4-115">BizTalk Tracking data files</span></span>  
  
-   <span data-ttu-id="038d4-116">BizTalk 追蹤交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="038d4-116">BizTalk Tracking transaction log files</span></span>  
  
 <span data-ttu-id="038d4-117">區隔 MessageBox 和 「 BizTalk 追蹤資料庫，以及將資料庫檔案和交易記錄檔不同實體磁碟上的會被視為降低磁碟 I/O 競爭的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="038d4-117">Separating the MessageBox and BizTalk Tracking databases and separating the database files and transaction log files on different physical disks are considered best practices for reducing disk I/O contention.</span></span> <span data-ttu-id="038d4-118">請試著儘可能將磁碟 I/O 分散數量的實體磁針。</span><span class="sxs-lookup"><span data-stu-id="038d4-118">Try to spread the disk I/O across as many physical spindles as possible.</span></span> <span data-ttu-id="038d4-119">如需有關如何避免磁碟爭用情況的詳細資訊，請參閱[如何避免磁碟爭用](http://go.microsoft.com/fwlink/?LinkId=158809)(http://go.microsoft.com/fwlink/?LinkId=158809) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南。</span><span class="sxs-lookup"><span data-stu-id="038d4-119">For more information about avoiding disk contention, see [How to Avoid Disk Contention](http://go.microsoft.com/fwlink/?LinkId=158809) (http://go.microsoft.com/fwlink/?LinkId=158809) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Performance Optimization Guide.</span></span>  
  
 <span data-ttu-id="038d4-120">您應該設定之後，手動將檔案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="038d4-120">You should separate the files manually after configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="038d4-121">如需詳細資訊，請參閱[BizTalk Server 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/?LinkId=101578)(http://go.microsoft.com/fwlink/?LinkId=101578)。</span><span class="sxs-lookup"><span data-stu-id="038d4-121">For more information, see the [BizTalk Server Database Optimization white paper](http://go.microsoft.com/fwlink/?LinkId=101578) (http://go.microsoft.com/fwlink/?LinkId=101578).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="038d4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="038d4-122">See Also</span></span>  
 [<span data-ttu-id="038d4-123">使用記錄檔 (PAL) 工具的效能的分析</span><span class="sxs-lookup"><span data-stu-id="038d4-123">Using the Performance Analysis of Logs (PAL) Tool</span></span>](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)