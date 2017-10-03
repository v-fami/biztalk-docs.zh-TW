---
title: "BAM 入口網站中的彙總 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal, pivot tables
- BAM, data analysis
- pivot tables [BAM portal]
- BAM portal, charts
- data, analysis [BAM]
- data, OLAP cubes
- aggregations [BAM], BAM portal
- charts, BAM portal
- BAM portal, aggregations
ms.assetid: 1c689563-714b-4573-9c18-a5b0efe97fb8
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43ef0adfacea0a29ea47584ed545884ffb8fa8bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="aggregations-in-the-bam-portal"></a><span data-ttu-id="5a0ba-102">BAM 入口網站中的彙總</span><span class="sxs-lookup"><span data-stu-id="5a0ba-102">Aggregations in the BAM Portal</span></span>
<span data-ttu-id="5a0ba-103">彙總是預先計算好的資料表格，您可以搭配 OLAP Cube 進行分析處理。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-103">Aggregations are tables of precalculated data you can use for analytical processing with an OLAP cube.</span></span> <span data-ttu-id="5a0ba-104">彙總有助於提升多維度資料庫的查詢效率。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-104">Aggregations facilitate the efficient querying of multidimensional databases.</span></span> <span data-ttu-id="5a0ba-105">當您使用 Excel 的 BAM 增益集建立和部署觀察模型 (商務資料的高階定義) 時，便會建立彙總以利迅速評估與關鍵效能指標 (KPI) 相關的資料集合。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-105">When you create and deploy your observation model (the high-level definition of your business data) using the BAM Add-In for Excel, you create aggregations that you can use to quickly evaluate collections of data relating your Key Performance Indicators (KPIs).</span></span>  
  
## <a name="types-of-aggregations"></a><span data-ttu-id="5a0ba-106">彙總類型</span><span class="sxs-lookup"><span data-stu-id="5a0ba-106">Types of aggregations</span></span>  
 <span data-ttu-id="5a0ba-107">彙總有兩種類型：排程或即時。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-107">Aggregations can be either scheduled or real-time.</span></span> <span data-ttu-id="5a0ba-108">排程彙總是 OLAP Cube，代表您所指定時間上的商務資料快照集。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-108">Scheduled aggregations are OLAP cubes, which represent a snapshot of your business data at a time you specify.</span></span> <span data-ttu-id="5a0ba-109">即時彙總能依據指定的觸發點提供商務資料檢視，讓 BAM 系統得以在達到 KPI 時立即透過警示通知您。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-109">Real-time aggregations allow a view of your business data based on trigger points that you specify, allowing the BAM system to notify you through an alert as soon as a KPI has been reached.</span></span>  
  
## <a name="pivottable-view"></a><span data-ttu-id="5a0ba-110">樞紐分析表檢視</span><span class="sxs-lookup"><span data-stu-id="5a0ba-110">PivotTable View</span></span>  
 <span data-ttu-id="5a0ba-111">[樞紐分析表檢視] 區域顯示使用 Excel 的 BAM 增益集所設計的樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-111">The PivotTable View area displays the PivotTable report that you design using the BAM Add-In for Excel.</span></span> <span data-ttu-id="5a0ba-112">「Office Web 元件」可讓您操控樞紐分析表，以最符合個人需求的方式顯示資料檢視。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-112">The Office Web Components allow you to manipulate the PivotTable report to present the view of the data that best fits your needs..</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a0ba-113">當您檢視樞紐分析表時，如果活動中的里程碑已達到，但進度維度中並未使用這些里程碑，即時彙總 (RTA) 和預先計算彙總 (OLAP 實作) 的某幾列可能都會包含空值資料。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-113">When viewing a PivotTable report it is possible that some rows could contain null data in both real-time aggregations (RTAs) and precalculated aggregations (an OLAP implementation) if the milestones in the activity have been reached but are not used in the progress dimension.</span></span> <span data-ttu-id="5a0ba-114">若在進度維度的內容中使用時間維度並將其錨定至特定里程碑，例如「已通知」而非「已接收」，則某幾列也可能會包含空值資料。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-114">It is also possible to encounter rows with null data if the time dimension is used in the context of a progress dimension and is anchored to a milestone such as "acknowledged" instead of "received."</span></span> <span data-ttu-id="5a0ba-115">在此情況下會接收活動執行個體並觸發已接收里程碑，但因活動尚未觸發通知里程碑，以致時間維度列顯示零值。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-115">In this case an activity instance is received and triggers the received milestone, but the activity has not yet triggered the acknowledge milestone and a zero will appear in the time dimension row.</span></span>  <span data-ttu-id="5a0ba-116">若要避免這種情形，請將時間維度向上連結至已接收里程碑。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-116">To avoid this situation, link the time dimension up to the received milestone.</span></span>  
  
 ![](../core/media/aggregationpivottabletotal.gif "AggregationPivotTableTotal")  
  
 <span data-ttu-id="5a0ba-117">在 BAM 入口網站中使用 Office Web Components 修改樞紐分析表時，請記住下列重點：</span><span class="sxs-lookup"><span data-stu-id="5a0ba-117">Keep these points in mind when using the Office Web Components in the BAM portal to modify your PivotTable report:</span></span>  
  
-   <span data-ttu-id="5a0ba-118">Excel 中的樞紐分析表包含 [頁面] 欄位，您可以在此放置時間配量維度。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-118">PivotTable reports in Excel include a Page field where you can put a time slice dimension.</span></span> <span data-ttu-id="5a0ba-119">BAM 入口網站所使用的 Office Web Components 則沒有 [頁面] 欄位。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-119">The Office Web Components used by the BAM portal do not include a Page field.</span></span> <span data-ttu-id="5a0ba-120">如果 Excel 樞紐分析表對於任一維度都使用了 [頁面] 欄位，則 BAM 入口網站中的樞紐分析表便不會顯示該欄位的資料。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-120">If your Excel PivotTable report uses the Page field for any dimensions, the data for this field is not displayed in your PivotTable report in the BAM portal.</span></span>  
  
-   <span data-ttu-id="5a0ba-121">Office Web Components 會將資料顯示在 BAM 入口網站的內容框架中。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-121">The Office Web Components display data in the content frame of the BAM portal.</span></span> <span data-ttu-id="5a0ba-122">由於此框架有空間限制，從欄位清單將維度新增至欄區域可能導致樞紐分析表所顯示的維度名稱部分或全部超出檢視畫面。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-122">Because of the space limitations of this frame, adding dimensions from the field list to the columns area can cause the display of the PivotTable to move dimension names partly or wholly out of view.</span></span>  
  
 <span data-ttu-id="5a0ba-123">樞紐分析表的詳細資訊，請參閱 < 樞紐分析表詞彙釋疑 」，網址[http://go.microsoft.com/fwlink/?LinkId=55416](http://go.microsoft.com/fwlink/?LinkId=55416)。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-123">For more information about PivotTables, see "PivotTable terminology demystified" at [http://go.microsoft.com/fwlink/?LinkId=55416](http://go.microsoft.com/fwlink/?LinkId=55416).</span></span>  
  
## <a name="chart-view"></a><span data-ttu-id="5a0ba-124">圖表檢視</span><span class="sxs-lookup"><span data-stu-id="5a0ba-124">Chart View</span></span>  
 <span data-ttu-id="5a0ba-125">[圖表檢視] 區域以圖形方式顯示彙總。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-125">The Chart View area displays the aggregation in a graphical manner.</span></span> <span data-ttu-id="5a0ba-126">Office Web Components 可讓您透過圖表檢視操控彙總的詳細資料，以便視需要調整報告的資料。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-126">The Office Web Components allow you to manipulate the details of the aggregation through the chart view to adjust the reported data as needed.</span></span> <span data-ttu-id="5a0ba-127">從 [圖表欄位] 清單拖放資料項目來調整彙總時，彙總的樞紐分析表會自動更新以反映您的變更。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-127">When you adjust the aggregation by dragging and dropping data items from the Chart Field list, the PivotTable report for the aggregation is automatically updated to reflect your changes.</span></span> <span data-ttu-id="5a0ba-128">您可以鑽研樞紐分析表，進而在新的彙總檢視中建立警示。</span><span class="sxs-lookup"><span data-stu-id="5a0ba-128">You can drill through the PivotTable to create an alert on the new aggregation view.</span></span>  
  
 ![](../core/media/aggregationchartview.gif "AggregationChartView")  
  
## <a name="more"></a><span data-ttu-id="5a0ba-129">其他</span><span class="sxs-lookup"><span data-stu-id="5a0ba-129">More</span></span>  
  
-   [<span data-ttu-id="5a0ba-130">如何設定警示</span><span class="sxs-lookup"><span data-stu-id="5a0ba-130">How to Set an Alert</span></span>](../core/how-to-set-an-alert.md)  
  
-   [<span data-ttu-id="5a0ba-131">如何檢視活動搜尋的結果</span><span class="sxs-lookup"><span data-stu-id="5a0ba-131">How to View the Results of an Activity Search</span></span>](../core/how-to-view-the-results-of-an-activity-search.md)  
  
-   [<span data-ttu-id="5a0ba-132">如何修改彙總</span><span class="sxs-lookup"><span data-stu-id="5a0ba-132">How to Modify an Aggregation</span></span>](../core/how-to-modify-an-aggregation.md)  
  
## <a name="see-also"></a><span data-ttu-id="5a0ba-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a0ba-133">See Also</span></span>  
 [<span data-ttu-id="5a0ba-134">什麼是彙總？</span><span class="sxs-lookup"><span data-stu-id="5a0ba-134">What Is an Aggregation?</span></span>](../core/what-is-an-aggregation.md)