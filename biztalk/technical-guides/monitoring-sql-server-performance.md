---
title: 監視 SQL Server 效能 |Microsoft Docs
description: 監視 BizTalk Server 資料庫使用的效能工具、 活動監視器和資料收集
ms.custom: ''
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 020fa764-968e-467c-b146-d069f5606a0f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 730896dc1cf0a465f68965f812da7311dd8664ab
ms.sourcegitcommit: ed9590dbcd97c12a1fe5ce2cdf8d826492cccdff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39640114"
---
# <a name="monitor-sql-server-performance"></a><span data-ttu-id="72da4-103">監視 SQL Server 效能</span><span class="sxs-lookup"><span data-stu-id="72da4-103">Monitor SQL Server Performance</span></span>
<span data-ttu-id="72da4-104">SQL Server 提供數個工具，用於監視 SQL Server 中的事件，以及用來微調實體資料庫設計。</span><span class="sxs-lookup"><span data-stu-id="72da4-104">SQL Server provides several tools for monitoring events in SQL Server and for tuning the physical database design.</span></span> <span data-ttu-id="72da4-105">[效能監視和微調工具](https://docs.microsoft.com/sql/relational-databases/performance/performance-monitoring-and-tuning-tools)描述這些工具。</span><span class="sxs-lookup"><span data-stu-id="72da4-105">[Tools for Performance Monitoring and Tuning](https://docs.microsoft.com/sql/relational-databases/performance/performance-monitoring-and-tuning-tools) describes these tools.</span></span> 
  
<span data-ttu-id="72da4-106">BizTalk Server 會是需要大量資料庫的程序。</span><span class="sxs-lookup"><span data-stu-id="72da4-106">BizTalk Server is a database-intensive process.</span></span> <span data-ttu-id="72da4-107">BizTalk Server 效能問題進行疑難排解時, 很有幫助也請檢查 SQL Server 效能。</span><span class="sxs-lookup"><span data-stu-id="72da4-107">when troubleshooting BizTalk Server performance issues, it can be beneficial to also check the SQL Server performance.</span></span> <span data-ttu-id="72da4-108">下列工具可以幫助。</span><span class="sxs-lookup"><span data-stu-id="72da4-108">The following tools can help.</span></span>  
  
## <a name="sql-server-activity-monitor"></a><span data-ttu-id="72da4-109">SQL Server 活動監視器</span><span class="sxs-lookup"><span data-stu-id="72da4-109">SQL Server Activity Monitor</span></span>  
<span data-ttu-id="72da4-110">SQL Server 活動監視器 」 提供 SQL Server 處理序以及這些處理序如何影響目前的執行個體的 SQL Server 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="72da4-110">SQL Server Activity Monitor provides information about SQL Server processes and how these processes affect the current instance of SQL Server.</span></span> <span data-ttu-id="72da4-111">如需詳細資訊，請參閱 <<c0> [ 活動監視器](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor)，並[如何： 開啟活動監視器 (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio)。</span><span class="sxs-lookup"><span data-stu-id="72da4-111">For more information, see [Activity Monitor](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor), and [How to: Open Activity Monitor (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio).</span></span> 
  
## <a name="sql-serverdata-collection"></a><span data-ttu-id="72da4-112">SQL ServerData 集合</span><span class="sxs-lookup"><span data-stu-id="72da4-112">SQL ServerData Collection</span></span>  
<span data-ttu-id="72da4-113">SQL Server 提供資料收集器，您可以使用它來取得及儲存從數個來源收集的資料。</span><span class="sxs-lookup"><span data-stu-id="72da4-113">SQL Server provides a data collector that you can use to obtain and save data that is gathered from several sources.</span></span> <span data-ttu-id="72da4-114">資料收集器可讓您使用資料收集容器，可讓您決定的範圍與執行 SQL Server 的電腦上的資料收集的頻率。</span><span class="sxs-lookup"><span data-stu-id="72da4-114">The data collector enables you to use data collection containers, which enable you to determine the scope and frequency of data collection on a computer that is running SQL Server.</span></span> <span data-ttu-id="72da4-115">請參閱[資料收集](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection)。</span><span class="sxs-lookup"><span data-stu-id="72da4-115">See [Data Collection](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="72da4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72da4-116">See Also</span></span>  
 [<span data-ttu-id="72da4-117">最佳化資料庫效能</span><span class="sxs-lookup"><span data-stu-id="72da4-117">Optimizing Database Performance</span></span>](../technical-guides/optimizing-database-performance.md)
