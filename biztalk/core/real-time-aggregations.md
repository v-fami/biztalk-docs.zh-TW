---
title: "即時彙總 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, aggregations
- aggregations [BAM], real-time data
ms.assetid: 0ef44641-e067-4108-b318-f4373ca8fa8f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1bc335c1c53fe106c460b7dcb5a27b803db97b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="real-time-aggregations"></a><span data-ttu-id="81f01-102">即時彙總</span><span class="sxs-lookup"><span data-stu-id="81f01-102">Real-Time Aggregations</span></span>
<span data-ttu-id="81f01-103">在某些情況下，多維度彙總的特定配量有時間緊迫性，因此必須可即時取得。</span><span class="sxs-lookup"><span data-stu-id="81f01-103">In some cases, specific slices of the multidimensional aggregations are so time-sensitive that you want them to be available in real time.</span></span> <span data-ttu-id="81f01-104">例如，您的業務是銷售容易腐壞的產品，所以希望即時取得各個出貨階段的產品數量彙總。</span><span class="sxs-lookup"><span data-stu-id="81f01-104">For example, your business is selling perishable products and you want the aggregation of product quantity in different stages of delivery to be available in real time.</span></span> <span data-ttu-id="81f01-105">同時，您也有其他想要看到的彙總，如典型客戶的年齡彙總，但是這只有在月底進行商業智慧分析時才需要。</span><span class="sxs-lookup"><span data-stu-id="81f01-105">At the same time, you want other aggregations such as the age of your typical customers, but only at the end of the month for business intelligence analysis.</span></span>  
  
 <span data-ttu-id="81f01-106">BAM 實作即時彙總 (RTA)，這是由活動儲存區資料表的觸發程序所維護的資料表。</span><span class="sxs-lookup"><span data-stu-id="81f01-106">BAM implements real-time aggregation (RTA) as a table maintained by triggers from the activity storage tables.</span></span> <span data-ttu-id="81f01-107">就上述商務處理採購單 (PO) 的情況而言，RTA 檢視將如下圖的範例所示。</span><span class="sxs-lookup"><span data-stu-id="81f01-107">In the case when your business deals with purchase orders (PO), the RTA view may look like the example in the following figure.</span></span>  
  
 ![](../core/media/bam-realtime-aggregations.gif "bam_realtime_aggregations")  
<span data-ttu-id="81f01-108">BAM 即時彙總</span><span class="sxs-lookup"><span data-stu-id="81f01-108">BAM Real-time Aggregations</span></span>  
  
 <span data-ttu-id="81f01-109">在此圖中，如果收到 Redmond $100 的新 PO，BAM 將帳目加入對應的資料列中的資料格 {redmond，InProcess} 上執行的作業，例如`Count=Count+1`和`Amount=Amount+$100`。</span><span class="sxs-lookup"><span data-stu-id="81f01-109">In this figure, if a new PO of $100 from Redmond is received, BAM adds a contribution to the cells in the corresponding row for {Redmond, InProcess} by performing an operation like `Count=Count+1` and `Amount=Amount+$100`.</span></span>  
  
 <span data-ttu-id="81f01-110">更新版本中，如果相同訂單出貨，BAM 從 {Redmond，InProcess} 的資料列移除其帳目，然後將它加入 {Redmond，Shipped} 資料列。</span><span class="sxs-lookup"><span data-stu-id="81f01-110">Later, if the same order ships, then BAM removes this contribution from the row {Redmond, InProcess} and adds it to the row {Redmond, Shipped}.</span></span>  
  
 <span data-ttu-id="81f01-111">BAM 會在 RTA 中保存指定線上視窗的資料，然後予以刪除。</span><span class="sxs-lookup"><span data-stu-id="81f01-111">BAM maintains the data inside RTA for a given online window, and then deletes it.</span></span> <span data-ttu-id="81f01-112">您可以藉由變更對應的資料列的資料表設定線上視窗**bam_Metadata_RealTimeAggregations**。</span><span class="sxs-lookup"><span data-stu-id="81f01-112">You can configure the online window by changing the corresponding row of the table **bam_Metadata_RealTimeAggregations**.</span></span>  
  
 <span data-ttu-id="81f01-113">下列陳述式也適用於即時彙總：</span><span class="sxs-lookup"><span data-stu-id="81f01-113">The following statements also apply to real-time aggregations:</span></span>  
  
-   <span data-ttu-id="81f01-114">即時彙總會大幅影響 BAM 可以在其中寫入資料的速度。</span><span class="sxs-lookup"><span data-stu-id="81f01-114">Real-time aggregations significantly affect the speed at which BAM can write data.</span></span> <span data-ttu-id="81f01-115">因此，您應該只將彙總結構中最重要的配量定義成 RTA。</span><span class="sxs-lookup"><span data-stu-id="81f01-115">Thus, you should only define the most important slices of the aggregation structure as RTA.</span></span>  
  
-   <span data-ttu-id="81f01-116">即時彙總的維度層級的限制為 14。</span><span class="sxs-lookup"><span data-stu-id="81f01-116">The limitation of the dimension levels for real-time aggregations is 14.</span></span> <span data-ttu-id="81f01-117">例如，如果您建立資料維度位置的狀態和縣 （市），這也算是兩個層級 （State 和 City）。</span><span class="sxs-lookup"><span data-stu-id="81f01-117">For example, if you create a Data Dimension Location for State and City, this counts as two levels (State and City).</span></span> <span data-ttu-id="81f01-118">進度維度的層級數目是樹狀結構的深度，而時間維度則是所有的子單位計數。</span><span class="sxs-lookup"><span data-stu-id="81f01-118">For Progress Dimensions the number of levels is the depth of the tree, and for Time Dimensions it is the count of all sub-units.</span></span> <span data-ttu-id="81f01-119">例如，時間維度 「 年、 月、 日、 小時 」 算成四個層級。</span><span class="sxs-lookup"><span data-stu-id="81f01-119">For example, a Time Dimension for Year, Month, Day, Hour will count as four levels.</span></span>  
  
-   <span data-ttu-id="81f01-120">BAM 不支援的型別即時彙總**Min**和**Max**。</span><span class="sxs-lookup"><span data-stu-id="81f01-120">BAM does not support real-time aggregations of type **Min** and **Max**.</span></span> <span data-ttu-id="81f01-121">BAM 支援的彙總是**計數**，**總和**，和**平均**。</span><span class="sxs-lookup"><span data-stu-id="81f01-121">The aggregations that BAM supports are **Count**, **Sum**, and **Average**.</span></span>  
  
-   <span data-ttu-id="81f01-122">您必須一律為 RTA 建立時間維度並始終應用在所有的資料配量，因為 RTA 中的資料過時根據伺服器的時間戳記，而非特定的商務里程碑。</span><span class="sxs-lookup"><span data-stu-id="81f01-122">You must always create a time dimension for RTA and always use it in all data slices, because the data in RTA is aged based on the server time stamp, and not on any specific business milestone.</span></span>  
  
-   <span data-ttu-id="81f01-123">請勿定義多個使用相同 BAM 活動的 RTA。</span><span class="sxs-lookup"><span data-stu-id="81f01-123">Do not define multiple RTAs that use the same BAM activity.</span></span> <span data-ttu-id="81f01-124">若是這麼做，當您封存 BAM 資料時，RTA 資料將是錯誤的資料。</span><span class="sxs-lookup"><span data-stu-id="81f01-124">If you do so, the RTA data will be incorrect when you archive the BAM data.</span></span>  
  
 <span data-ttu-id="81f01-125">即時彙總會大幅影響 BAM 可以在其中寫入資料的速度。</span><span class="sxs-lookup"><span data-stu-id="81f01-125">Real-time aggregations significantly affect the speed at which BAM can write data.</span></span> <span data-ttu-id="81f01-126">因此，您應該只將彙總結構中最重要的配量定義成 RTA。</span><span class="sxs-lookup"><span data-stu-id="81f01-126">Thus, you should only define the most important slices of the aggregation structure as RTA.</span></span>  
  
 <span data-ttu-id="81f01-127">即時彙總的維度層級的限制為 14。</span><span class="sxs-lookup"><span data-stu-id="81f01-127">The limitation of the dimension levels for real-time aggregations is 14.</span></span> <span data-ttu-id="81f01-128">例如，如果您建立資料維度位置的狀態和縣 （市），這也算是兩個層級 （State 和 City）。</span><span class="sxs-lookup"><span data-stu-id="81f01-128">For example, if you create a Data Dimension Location for State and City, this counts as two levels (State and City).</span></span> <span data-ttu-id="81f01-129">進度維度的層級數目是樹狀結構的深度，而時間維度則是所有的子單位計數。</span><span class="sxs-lookup"><span data-stu-id="81f01-129">For Progress Dimensions the number of levels is the depth of the tree, and for Time Dimensions it is the count of all sub-units.</span></span> <span data-ttu-id="81f01-130">例如，時間維度 「 年、 月、 日、 小時 」 算成四個層級。</span><span class="sxs-lookup"><span data-stu-id="81f01-130">For example, a Time Dimension for Year, Month, Day, Hour will count as four levels.</span></span>  
  
 <span data-ttu-id="81f01-131">BAM 不支援的型別即時彙總**Min**和**Max**。</span><span class="sxs-lookup"><span data-stu-id="81f01-131">BAM does not support real-time aggregations of type **Min** and **Max**.</span></span> <span data-ttu-id="81f01-132">BAM 支援的彙總是**計數**，**總和**，和**平均**。</span><span class="sxs-lookup"><span data-stu-id="81f01-132">The aggregations that BAM supports are **Count**, **Sum**, and **Average**.</span></span>  
  
 <span data-ttu-id="81f01-133">請勿定義多個使用相同 BAM 活動的 RTA。</span><span class="sxs-lookup"><span data-stu-id="81f01-133">Do not define multiple RTAs that use the same BAM activity.</span></span> <span data-ttu-id="81f01-134">若是這麼做，當您封存 BAM 資料時，RTA 資料將是錯誤的資料。</span><span class="sxs-lookup"><span data-stu-id="81f01-134">If you do so, the RTA data will be incorrect when you archive the BAM data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f01-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81f01-135">See Also</span></span>  
 [<span data-ttu-id="81f01-136">什麼是彙總？</span><span class="sxs-lookup"><span data-stu-id="81f01-136">What Is an Aggregation?</span></span>](../core/what-is-an-aggregation.md)