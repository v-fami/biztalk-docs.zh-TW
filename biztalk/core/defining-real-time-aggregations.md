---
title: "定義即時彙總 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- real-time data, aggregating
- aggregations [BAM], real-time data
ms.assetid: cb3d7124-1663-4af2-9540-4171cc51568a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2b2df32149f67a002a5a6281b6f1abd848523a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="defining-real-time-aggregations"></a><span data-ttu-id="acc5f-102">定義即時彙總</span><span class="sxs-lookup"><span data-stu-id="acc5f-102">Defining Real-Time Aggregations</span></span>
<span data-ttu-id="acc5f-103">在某些情況下，多維度彙總的特定配量會講求時效而分秒必爭，以致您希望能即時取得該資訊。</span><span class="sxs-lookup"><span data-stu-id="acc5f-103">In some cases, specific slices of the multi-dimensional aggregations are so time- sensitive that you want them to be available in real time.</span></span> <span data-ttu-id="acc5f-104">例如，您的業務是銷售容易腐壞的產品，所以希望即時取得各個出貨階段的產品數量彙總。</span><span class="sxs-lookup"><span data-stu-id="acc5f-104">For example, your business is selling perishable products and you want the aggregation of product quantity in different stages of delivery to be available in real time.</span></span> <span data-ttu-id="acc5f-105">同時，您也有其他想要看到的彙總，如典型客戶的年齡彙總，但是這只有在月底進行商業智慧分析時才需要。</span><span class="sxs-lookup"><span data-stu-id="acc5f-105">At the same time, you want other aggregations such as the age of your typical customers, but only at the end of the month for business intelligence analysis.</span></span>  
  
-   <span data-ttu-id="acc5f-106">使用**樞紐分析表**工具列上，將選取的樞紐分析表標示為即時彙總 (RTA)，，如果適用的話。</span><span class="sxs-lookup"><span data-stu-id="acc5f-106">Using the **PivotTable** toolbar, mark the selected PivotTable as a real-time aggregation (RTA), if applicable.</span></span> <span data-ttu-id="acc5f-107">樞紐分析表所含資料的類型應該可以用來判斷此資料是否需要即時檢視。</span><span class="sxs-lookup"><span data-stu-id="acc5f-107">The type of data contained in the PivotTable should determine whether it needs to be viewed in real time.</span></span> <span data-ttu-id="acc5f-108">例如，每小時追蹤網頁訂單的報告可能就必須即時加以檢視，然而追蹤每日銷售總額的報告則無須即時檢視。</span><span class="sxs-lookup"><span data-stu-id="acc5f-108">For example, a report that tracks hourly Web orders might need to viewed in real time, whereas a report that tracks daily sales totals would not be viewed in real time.</span></span>  
  
     ![](../core/media/ebiz-sdk-sample-bam12.gif "ebiz_sdk_sample_bam12")  
<span data-ttu-id="acc5f-109">RTA 按鈕</span><span class="sxs-lookup"><span data-stu-id="acc5f-109">RTA button</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="acc5f-110">請勿定義多個使用相同 BAM 活動的 RTA。</span><span class="sxs-lookup"><span data-stu-id="acc5f-110">Do not define multiple RTAs that use the same BAM activity.</span></span> <span data-ttu-id="acc5f-111">若是這麼做，當您封存 BAM 資料時，RTA 資料將是錯誤的資料。</span><span class="sxs-lookup"><span data-stu-id="acc5f-111">If you do so, the RTA data will be incorrect when you archive the BAM data.</span></span>  
  
 <span data-ttu-id="acc5f-112">如需有關樞紐分析表的詳細資訊，請參閱 Excel 線上說明。</span><span class="sxs-lookup"><span data-stu-id="acc5f-112">For more information about Pivot tables, see Excel online help.</span></span> <span data-ttu-id="acc5f-113">在建立樞紐分析表之後，您就可以檢視即時 BAM 資料。</span><span class="sxs-lookup"><span data-stu-id="acc5f-113">After you create your Pivot table, you can view your live BAM data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc5f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acc5f-114">See Also</span></span>  
 <span data-ttu-id="acc5f-115">[檢視即時 BAM 資料](../core/viewing-live-bam-data.md) </span><span class="sxs-lookup"><span data-stu-id="acc5f-115">[Viewing Live BAM Data](../core/viewing-live-bam-data.md) </span></span>  
 <span data-ttu-id="acc5f-116">[進度維度](../core/progress-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="acc5f-116">[Progress Dimension](../core/progress-dimension.md) </span></span>  
 <span data-ttu-id="acc5f-117">[資料維度](../core/data-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="acc5f-117">[Data Dimension](../core/data-dimension.md) </span></span>  
 <span data-ttu-id="acc5f-118">[時間維度](../core/time-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="acc5f-118">[Time Dimension](../core/time-dimension.md) </span></span>  
 <span data-ttu-id="acc5f-119">[數字範圍維度](../core/numeric-range-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="acc5f-119">[Numeric Range Dimension](../core/numeric-range-dimension.md) </span></span>  
 [<span data-ttu-id="acc5f-120">定義維度</span><span class="sxs-lookup"><span data-stu-id="acc5f-120">Defining Dimensions</span></span>](../core/defining-dimensions.md)