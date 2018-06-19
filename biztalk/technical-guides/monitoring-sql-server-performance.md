---
title: 監視 SQL Server 效能 |Microsoft 文件
description: 監控 BizTalk Server 資料庫時使用 效能工具，活動監視器和資料收集
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
ms.openlocfilehash: 1e4f9db738298ec2a242350faae3ba5bc9da1c92
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007895"
---
# <a name="monitor-sql-server-performance"></a><span data-ttu-id="7aecd-103">監視 SQL Server 效能</span><span class="sxs-lookup"><span data-stu-id="7aecd-103">Monitor SQL Server Performance</span></span>
<span data-ttu-id="7aecd-104">SQL Server 提供數個工具，用於監視 SQL Server 中的事件，以及用來微調實體資料庫設計。</span><span class="sxs-lookup"><span data-stu-id="7aecd-104">SQL Server provides several tools for monitoring events in SQL Server and for tuning the physical database design.</span></span> <span data-ttu-id="7aecd-105">[效能監視和微調工具](https://docs.microsoft.com/en-us/sql/relational-databases/performance/performance-monitoring-and-tuning-tools)描述這些工具。</span><span class="sxs-lookup"><span data-stu-id="7aecd-105">[Tools for Performance Monitoring and Tuning](https://docs.microsoft.com/en-us/sql/relational-databases/performance/performance-monitoring-and-tuning-tools) describes these tools.</span></span> 
  
<span data-ttu-id="7aecd-106">BizTalk Server 是需要大量資料庫的程序。</span><span class="sxs-lookup"><span data-stu-id="7aecd-106">BizTalk Server is a database-intensive process.</span></span> <span data-ttu-id="7aecd-107">當 BizTalk Server 效能問題進行疑難排解，可能很有幫助也請檢查 SQL Server 效能。</span><span class="sxs-lookup"><span data-stu-id="7aecd-107">when troubleshooting BizTalk Server performance issues, it can be beneficial to also check the SQL Server performance.</span></span> <span data-ttu-id="7aecd-108">下列工具可協助。</span><span class="sxs-lookup"><span data-stu-id="7aecd-108">The following tools can help.</span></span>  
  
## <a name="sql-server-activity-monitor"></a><span data-ttu-id="7aecd-109">SQL Server 活動監視器</span><span class="sxs-lookup"><span data-stu-id="7aecd-109">SQL Server Activity Monitor</span></span>  
<span data-ttu-id="7aecd-110">SQL Server 活動監視器 」 提供 SQL Server 處理序以及這些處理序如何影響目前的 SQL Server 執行個體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7aecd-110">SQL Server Activity Monitor provides information about SQL Server processes and how these processes affect the current instance of SQL Server.</span></span> <span data-ttu-id="7aecd-111">如需詳細資訊，請參閱[活動監視器](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor)，和[如何： 開啟活動監視器 (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio)。</span><span class="sxs-lookup"><span data-stu-id="7aecd-111">For more information, see [Activity Monitor](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor), and [How to: Open Activity Monitor (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio).</span></span> 
  
## <a name="sql-serverdata-collection"></a><span data-ttu-id="7aecd-112">SQL ServerData 集合</span><span class="sxs-lookup"><span data-stu-id="7aecd-112">SQL ServerData Collection</span></span>  
<span data-ttu-id="7aecd-113">SQL Server 提供您可以使用來取得及儲存從數個來源蒐集資料的資料收集器。</span><span class="sxs-lookup"><span data-stu-id="7aecd-113">SQL Server provides a data collector that you can use to obtain and save data that is gathered from several sources.</span></span> <span data-ttu-id="7aecd-114">資料收集器可讓您使用資料收集容器，可讓您決定的範圍與執行 SQL Server 的電腦上的資料收集的頻率。</span><span class="sxs-lookup"><span data-stu-id="7aecd-114">The data collector enables you to use data collection containers, which enable you to determine the scope and frequency of data collection on a computer that is running SQL Server.</span></span> <span data-ttu-id="7aecd-115">請參閱[資料收集](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection)。</span><span class="sxs-lookup"><span data-stu-id="7aecd-115">See [Data Collection](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7aecd-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="7aecd-116">See Also</span></span>  
 [<span data-ttu-id="7aecd-117">最佳化資料庫效能</span><span class="sxs-lookup"><span data-stu-id="7aecd-117">Optimizing Database Performance</span></span>](../technical-guides/optimizing-database-performance.md)