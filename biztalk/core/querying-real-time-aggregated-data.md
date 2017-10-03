---
title: "查詢即時彙總資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [BAM], real-time data
- BAM, real-time data
ms.assetid: f60a34a1-ac64-47c7-8f83-1bc301170590
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f02ec8a33fdb050462860efc6c6a0cd5f8fa5650
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="querying-real-time-aggregated-data"></a><span data-ttu-id="9db3e-102">查詢即時彙總資料</span><span class="sxs-lookup"><span data-stu-id="9db3e-102">Querying Real-Time Aggregated Data</span></span>
<span data-ttu-id="9db3e-103">透過 BAM 主要匯入資料庫中動態建立的 SQL 檢視，可以查詢即時彙總 (RTA) 資料。</span><span class="sxs-lookup"><span data-stu-id="9db3e-103">The real-time aggregation (RTA) data is available for queries in a dynamically created SQL View in the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="9db3e-104">這個檢視的名稱為</span><span class="sxs-lookup"><span data-stu-id="9db3e-104">The name of this view is</span></span>  
  
 <span data-ttu-id="9db3e-105">**bam_\<**  *ViewName* **> _\<**  *RTAName* **> _RTAView**</span><span class="sxs-lookup"><span data-stu-id="9db3e-105">**bam_\<** *ViewName* **>_\<** *RTAName* **>_RTAView**</span></span>  
  
 <span data-ttu-id="9db3e-106">位置</span><span class="sxs-lookup"><span data-stu-id="9db3e-106">Where</span></span>  
  
 <span data-ttu-id="9db3e-107">**\<***ViewName*  **>** 是 BAM 定義 XML 中 View 項目的 Name 屬性相同相關 Microsoft Excel 精靈中輸入的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="9db3e-107">**\<** *ViewName* **>** is the Name attribute of the View element in the BAM definition XML, which is the same as the View Name entered in the related Microsoft Excel wizards.</span></span>  
  
 <span data-ttu-id="9db3e-108">**\<***RTAName*  **>**  BAM 產生的唯一 BAM 定義 XML 中 RealTimeAggregation 項目的 Name 屬性根據檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="9db3e-108">**\<** *RTAName* **>** is the Name attribute of the RealTimeAggregation element in the BAM Definition XML, which BAM generates to be unique based on the view name.</span></span>  
  
 <span data-ttu-id="9db3e-109">在查詢即時彙總資料時，請特別注意下列條件：</span><span class="sxs-lookup"><span data-stu-id="9db3e-109">It is important to note the following conditions when querying real-time aggregated data:</span></span>  
  
-   <span data-ttu-id="9db3e-110">即時彙總必須設定成在指定的時間內 (預設值是一天) 保留彙總，並且彙總絕不能變得太大。</span><span class="sxs-lookup"><span data-stu-id="9db3e-110">The real-time aggregations must be configured to keep the aggregations for a given amount of time (the default is one day) and to never grow very large.</span></span> <span data-ttu-id="9db3e-111">OLAP Cube 中應該可以取得較舊的彙總。</span><span class="sxs-lookup"><span data-stu-id="9db3e-111">The older aggregations should be available in the OLAP cubes instead.</span></span>  
  
-   <span data-ttu-id="9db3e-112">針對 RTA 的任何查詢必須包含會在 RTA 資料的線上視窗內的時間維度上篩選。</span><span class="sxs-lookup"><span data-stu-id="9db3e-112">Any query against RTA must include filtering on a time dimension that will be inside the online window for the RTA data.</span></span> <span data-ttu-id="9db3e-113">這是必要的，因為 BAM 會根據 BAM 資料上的時間戳記執行 RTA 資料維護，並經過最佳化以便將資料放置在區塊中。</span><span class="sxs-lookup"><span data-stu-id="9db3e-113">This is necessary because BAM performs data maintenance for RTAs based  on the  timestamp on the BAM dataand is optimized to drop the data in chunks.</span></span> <span data-ttu-id="9db3e-114">因此，如果您只傳送 Transact-SQL 命令 "`select *`"，將無法預期結果。</span><span class="sxs-lookup"><span data-stu-id="9db3e-114">Thus if you simply send the Transact-SQL command "`select *`", the results will fluctuate unpredictably.</span></span>  
  
-   <span data-ttu-id="9db3e-115">如果透過 DirectEventStream 將活動資料傳送至 BAM，即時彙總資料便沒有延遲，也就是說，當呼叫應用程式中的交易認可時，資料就會立即出現。</span><span class="sxs-lookup"><span data-stu-id="9db3e-115">If the activity data is sent to BAM via the DirectEventStream, the real-time aggregated data has no latency – it appears instantaneously when the transaction in the calling Application commits.</span></span>  
  
-   <span data-ttu-id="9db3e-116">如果透過 BufferedEventStream 將活動資料傳送至 BAM，將會根據 BAM 事件匯流排服務的負載，以及裝載 BAM 主要匯入資料庫的 SQL Server，在幾秒鐘後顯示查詢的 RTA 資料。</span><span class="sxs-lookup"><span data-stu-id="9db3e-116">If the activity data is sent to BAM via the BufferedEventStream, the RTA data will show up for queries a few seconds later, depending on the load of the BAM Event Bus service(s) and the SQL server that hosts the BAM Primary Import database.</span></span>  
  
-   <span data-ttu-id="9db3e-117">BAM 會將它使用觸發程序維護與活動資料儲存記錄中變更或插入作業同步的資料表，當做即時彙總的基礎。</span><span class="sxs-lookup"><span data-stu-id="9db3e-117">BAM bases the real-time aggregation on a table that it maintains in synchronization with the changes or insertions in the activity data storage records using triggers.</span></span> <span data-ttu-id="9db3e-118">如需詳細資訊，請參閱[活動資料儲存區](../core/activity-data-storage.md)。</span><span class="sxs-lookup"><span data-stu-id="9db3e-118">For more information, see [Activity Data Storage](../core/activity-data-storage.md).</span></span> <span data-ttu-id="9db3e-119">因此，即時彙總可能對效能有顯著的影響。</span><span class="sxs-lookup"><span data-stu-id="9db3e-119">Thus, the real-time aggregation can have a significant performance impact.</span></span> <span data-ttu-id="9db3e-120">如需詳細資訊，請參閱[即時彙總](../core/real-time-aggregations.md)。</span><span class="sxs-lookup"><span data-stu-id="9db3e-120">For more information, see [Real-Time Aggregations](../core/real-time-aggregations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db3e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9db3e-121">See Also</span></span>  
 <span data-ttu-id="9db3e-122">[查詢排程彙總資料](../core/querying-scheduled-aggregated-data.md) </span><span class="sxs-lookup"><span data-stu-id="9db3e-122">[Querying Scheduled Aggregated Data](../core/querying-scheduled-aggregated-data.md) </span></span>  
 [<span data-ttu-id="9db3e-123">查詢 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="9db3e-123">Querying BAM Data</span></span>](../core/querying-bam-data.md)