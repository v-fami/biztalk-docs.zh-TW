---
title: "影響最大持續性效能的因素 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum sustainable throughput (MST), maintenance
- monitoring, maximum sustainable thoughput (MST)
- maintaining, maximum sustainable thoughput (MST)
- maximum sustainable throughput (MST), monitoring
- maximum sustainable throughput (MST), load patterns
- maximum sustainable throughput (MST), sustainable load test
- sustainable performance
ms.assetid: 99b99655-bc77-425c-a133-204781d7c430
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be96ad552abef66e2a401e334da1c27ee0e08cd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="factors-that-affect-maximum-sustainable-performance"></a><span data-ttu-id="8b7f0-102">影響可維持之效能上限的因素</span><span class="sxs-lookup"><span data-stu-id="8b7f0-102">Factors that Affect Maximum Sustainable Performance</span></span>
<span data-ttu-id="8b7f0-103">可維持的最大輸送量直接受廣泛的因素影響，如可用的伺服器資源、解決方案使用的功能類型、訊息大小和整體訊息負載等因素。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-103">Maximum sustainable throughput is directly impacted by a wide range of factors such as available server resources, the type of features used in the solution, message size, and overall message load.</span></span> <span data-ttu-id="8b7f0-104">當然還需考量其他因素，但是並非顯而易見。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-104">There are other factors to be considered though that may not be immediately obvious.</span></span> <span data-ttu-id="8b7f0-105">預估可維持之效能的上限時也應該考慮下列因素：</span><span class="sxs-lookup"><span data-stu-id="8b7f0-105">The following factors should also be considered when estimating maximum sustainable performance:</span></span>  
  
## <a name="load-patterns"></a><span data-ttu-id="8b7f0-106">負載模式</span><span class="sxs-lookup"><span data-stu-id="8b7f0-106">Load Patterns</span></span>  
 <span data-ttu-id="8b7f0-107">訊息不一定會以可預期的一致速率傳送到實際 BizTalk Server 環境。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-107">Messages do not typically flow into a production BizTalk Server environment at a predictable, consistent rate.</span></span> <span data-ttu-id="8b7f0-108">更典型的方式是，商務需求會指定 BizTalk Server 以呈現尖峰期與低峰期的變動速率來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-108">More typically, business needs dictate that BizTalk Server process messages at a variable rate which exhibits peaks and valleys.</span></span> <span data-ttu-id="8b7f0-109">出現高峰時，BizTalk Server 處理要求可能會從閒置狀況快速跳到加速狀況，此時接收訊息的速度會比處理的速度還快。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-109">When peaks occur, the BizTalk Server processing requirements may quickly jump from negligible to an overdrive condition where messages are received faster than they are processed.</span></span> <span data-ttu-id="8b7f0-110">在此實例中，發佈訊息會積存在 MessageBox 資料庫中，直到 BizTalk 將積存訊息傳遞到適當的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-110">In this scenario, published messages are backlogged in the MessageBox database until BizTalk delivers the backlogged messages to the appropriate subscribers.</span></span> <span data-ttu-id="8b7f0-111">只要 BizTalk Server 能夠處理尖峰負載期間累積的積存訊息，就不會產生問題。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-111">As long as BizTalk Server is able to process the backlog of messages accumulated between peak load periods then this is not problematic.</span></span>  
  
 <span data-ttu-id="8b7f0-112">因為通常訊息流到 BizTalk Server 環境的模式會有所變動，所以測試實例應該延長執行時間，以確保解決方案可以無限地保持所需的輸送量，一段時間後可從所有尖峰負載復原。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-112">Because of the typically variable pattern of message flow into a BizTalk Server environment, testing scenarios should be run for an extended period of time to ensure that the solution can sustain the desired throughput indefinitely, recovering from all peak loads over time.</span></span>  
  
## <a name="monitoring-and-maintenance-activities"></a><span data-ttu-id="8b7f0-113">監控和維護活動</span><span class="sxs-lookup"><span data-stu-id="8b7f0-113">Monitoring and Maintenance activities</span></span>  
 <span data-ttu-id="8b7f0-114">在生產環境方案生命週期期間沒有監視的主機和維護活動，可能會影響 BizTalk 效能，所以應該納入任何測試實例。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-114">During the life of a production solution, there is a host of monitoring and maintenance activities that can impact BizTalk performance and so should be factored into any testing scenarios.</span></span> <span data-ttu-id="8b7f0-115">這些活動包括：</span><span class="sxs-lookup"><span data-stu-id="8b7f0-115">These activities include:</span></span>  
  
-   <span data-ttu-id="8b7f0-116">**BizTalk 管理主控台查詢**這些查詢耗用資源並影響整體輸送量取決於型別和查詢的頻率。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-116">**BizTalk Administration Console queries** These queries consume resources and affect overall throughput depending on the type and frequency of the query.</span></span>  
  
-   <span data-ttu-id="8b7f0-117">**備份、 封存和清理活動**這些活動也會耗用資源，並應該納入任何測試實例。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-117">**Backup, archiving, and purging activities** These activities also consume resources and should be factored into any testing scenarios.</span></span> <span data-ttu-id="8b7f0-118">所有 BizTalk Server 資料庫都應定期備份，而其交易記錄會被截斷。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-118">All BizTalk Server databases should be backed up periodically and their transaction logs truncated.</span></span> <span data-ttu-id="8b7f0-119">若是不執行交易記錄，則可能會無限增加，而耗用交易資料庫的所有可用磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-119">If this is not performed the transaction log may grow un-checked and consume all of the available disk space for the transaction database.</span></span> <span data-ttu-id="8b7f0-120">若使用追蹤，則應定期清理追蹤資料庫並選擇性地封存資料，以避免資料庫變得過大。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-120">If tracking is being used, the tracking database must periodically be purged and optionally archived to keep it from growing too large.</span></span> <span data-ttu-id="8b7f0-121">如需維護 BizTalk Server 資料庫的詳細資訊，請參閱[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="8b7f0-121">For more information about maintaining BizTalk Server databases, please see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7f0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b7f0-122">See Also</span></span>  
 [<span data-ttu-id="8b7f0-123">測量最大持續性追蹤輸送量</span><span class="sxs-lookup"><span data-stu-id="8b7f0-123">Measuring Maximum Sustainable Tracking Throughput</span></span>](../core/measuring-maximum-sustainable-tracking-throughput.md)