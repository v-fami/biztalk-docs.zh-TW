---
title: "如何識別 BAM 主要匯入資料庫中的瓶頸 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0372f1f1-d892-4f7d-b6c4-e0f2b5a02f1c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: decf27009eea6aff0ff5ed9088ae49ef2014b1cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-bam-primary-import-database"></a><span data-ttu-id="1c0fa-102">如何識別 BAM 主要匯入資料庫中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="1c0fa-102">How to Identify Bottlenecks in the BAM Primary Import Database</span></span>
<span data-ttu-id="1c0fa-103">若要識別商務活動監控 (BAM) 資料庫中的瓶頸，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1c0fa-103">To identify bottlenecks in the Business Activity Monitoring (BAM) database, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="1c0fa-104">確定作用中執行個體的計數未上升。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-104">Ensure that the Active Instances count is not climbing.</span></span>  
  
2.  <span data-ttu-id="1c0fa-105">確認 SQL-Agent 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-105">Ensure that the SQL-Agent Service is running.</span></span>  
  
3.  <span data-ttu-id="1c0fa-106">如果已設定 OLAP 分析，請確定 BAM_AN_\<activityname > 作業在定期間隔執行。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-106">If OLAP Analysis is configured, ensure that the BAM_AN_\<activityname> job is running at periodic intervals.</span></span>  
  
4.  <span data-ttu-id="1c0fa-107">請確定該 BAM_DM_\<activityname > (Data Maintenance) 工作排定在定期間隔執行。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-107">Ensure that BAM_DM_\<activityname> (Data Maintenance) job is scheduled to run at periodic intervals.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c0fa-108">在高使用率案例 BAM 資料庫活動可能會影響到其他 BizTalk Server 資料庫，將會影響 BizTalk Server 的整體效能的效能。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-108">In high usage scenarios BAM database activity can impact the performance of other BizTalk Server databases, which will affect overall BizTalk Server performance.</span></span> <span data-ttu-id="1c0fa-109">在此情況下，請考慮採取下列動作：</span><span class="sxs-lookup"><span data-stu-id="1c0fa-109">In this case consider taking the following actions:</span></span>  
    >   
    >  -   <span data-ttu-id="1c0fa-110">請考慮減少從預設值 （6 個月） 的所有 BAM 活動的持續時間為 1 個月或更小。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-110">Consider decreasing the duration of all BAM activities from the default value (6 months) to 1 month or less.</span></span> <span data-ttu-id="1c0fa-111">這會降低其 BAM 資料會保留在 BAMPrimaryImport 資料庫封存之前的時間週期。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-111">This will reduce the time period for which BAM data is maintained in the BAMPrimaryImport database before being archived.</span></span> <span data-ttu-id="1c0fa-112">使用 BAM 管理公用程式`set-activitywindow`命令來修改 BAM 活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-112">Use the BAM Management Utility `set-activitywindow` command to modify the duration of BAM activities.</span></span> <span data-ttu-id="1c0fa-113">如需 BAM 管理公用程式的活動管理命令查看[活動管理命令](http://go.microsoft.com/fwlink/?LinkId=210417)(http://go.microsoft.com/fwlink/?LinkId=210417)。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-113">For more information about the BAM Management Utility activity management commands see [Activity Management Commands](http://go.microsoft.com/fwlink/?LinkId=210417) (http://go.microsoft.com/fwlink/?LinkId=210417).</span></span>  
    > -   <span data-ttu-id="1c0fa-114">將 BAM 封存資料庫移至未裝載任何 BizTalk MessageBox 資料庫的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-114">Move the BAM Archive database to an instance of SQL Server that does not host any BizTalk MessageBox databases.</span></span> <span data-ttu-id="1c0fa-115">這將會競用資源時，防止這些資料庫，並改善整體效能。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-115">This will prevent these databases from competing for resources and improve overall performance.</span></span>  
  
5.  <span data-ttu-id="1c0fa-116">用於追蹤專用的主機，並測量在負載下的主控件佇列長度效能計數器。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-116">Use a dedicated host for tracking and measure the Host Queue Length performance counter when under load.</span></span>  
  
6.  <span data-ttu-id="1c0fa-117">經過一段時間檢查遞增趨勢的多工緩衝處理表格大小效能計數器。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-117">Check the Spool Table size performance counter for an increasing trend over time.</span></span>  
  
7.  <span data-ttu-id="1c0fa-118">請檢查長時間執行的封存/清除作業執行持續時間。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-118">Check the Archive/Purge job execution duration for long execution times.</span></span>  
  
8.  <span data-ttu-id="1c0fa-119">在裝載 「 BizTalk 追蹤資料庫的磁碟，請檢查磁碟回應性 （讀/寫效能計數器每次磁碟秒數）。</span><span class="sxs-lookup"><span data-stu-id="1c0fa-119">Check disk responsiveness (Disk Seconds per Read/Write performance counter) on the disk hosting the BizTalk Tracking database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0fa-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c0fa-120">See Also</span></span>  
 [<span data-ttu-id="1c0fa-121">資料庫層中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="1c0fa-121">Bottlenecks in the Database Tier</span></span>](../technical-guides/bottlenecks-in-the-database-tier.md)