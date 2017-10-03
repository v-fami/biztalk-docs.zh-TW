---
title: "什麼是量值和維度？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6b12a4c-9be5-4cac-b5b9-ece376d28cb1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdbbd270b5241d25e7ba227c2db886c112f3f4c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-are-measures-and-dimensions"></a><span data-ttu-id="19690-103">什麼是量值和維度？</span><span class="sxs-lookup"><span data-stu-id="19690-103">What Are Measures and Dimensions?</span></span>
<span data-ttu-id="19690-104">維度和量值是資料彙總的實體層面。</span><span class="sxs-lookup"><span data-stu-id="19690-104">Dimensions and measures are the physical aspects of data aggregation.</span></span> <span data-ttu-id="19690-105">本主題使用 BAM 實例提供環境以說明量值和維度的意義。</span><span class="sxs-lookup"><span data-stu-id="19690-105">This topic describes what measures and dimensions are, using a BAM scenario to provide context.</span></span>  
  
## <a name="measures"></a><span data-ttu-id="19690-106">量值</span><span class="sxs-lookup"><span data-stu-id="19690-106">Measures</span></span>  
 <span data-ttu-id="19690-107">假設您以極其簡單的方式，為訂單管理程序定義了包含三個項目的 BAM 活動：</span><span class="sxs-lookup"><span data-stu-id="19690-107">Suppose that you define a BAM activity for an order management process in extremely simple terms consisting of three items:</span></span>  
  
1.  <span data-ttu-id="19690-108">程序開始時間 (現實世界的事件)</span><span class="sxs-lookup"><span data-stu-id="19690-108">Process start time (an event in the real world)</span></span>  
  
2.  <span data-ttu-id="19690-109">程序結束時間 (也是現實世界的事件)</span><span class="sxs-lookup"><span data-stu-id="19690-109">Process end time (also a real-world event)</span></span>  
  
3.  <span data-ttu-id="19690-110">程序持續時間 (#2 - #1 的計算)</span><span class="sxs-lookup"><span data-stu-id="19690-110">Process duration (a calculation of #2 - #1)</span></span>  
  
 <span data-ttu-id="19690-111">在此例中將資料彙總是很容易的；只需將彙總函式 (例如，平均值、最小值、最大值等) 套用到一系列個別的持續時間值 (亦即，每張訂單的持續處理期間)。</span><span class="sxs-lookup"><span data-stu-id="19690-111">Aggregating data in this case is simply a matter of applying an aggregation function (for example, average, minimum, maximum, etc.) to a series of individual duration values (that is, the processing duration for each order).</span></span>  
  
 <span data-ttu-id="19690-112">「平均持續時間」的概念是量值，並且為單一值。</span><span class="sxs-lookup"><span data-stu-id="19690-112">The concept of "average duration" is a measure, and it is a single value.</span></span> <span data-ttu-id="19690-113">這個量值會自行產生與程序管理相關的資訊，藉以指示程序的整體表現 (就適時性/處理能力而言) 是否如預期一般。</span><span class="sxs-lookup"><span data-stu-id="19690-113">By itself, this measure yields information relevant to process management in that it indicates whether or not the process overall is behaving (in terms of timliness/throughput) as expected.</span></span> <span data-ttu-id="19690-114">不過，由於缺少其他的資料 (因為「平均持續時間」是單一值)，要瞭解量值實際值的意義會比較困難；例如，本週的平均持續時間為什麼會突增？</span><span class="sxs-lookup"><span data-stu-id="19690-114">However, in the absence of any other data (because "average duration" is a single value), understanding the meaning of the measure's actual value is harder For example, why did we have a spike in average duration this week?</span></span> <span data-ttu-id="19690-115">是否因為特定的夥伴、計劃或產品而引起？</span><span class="sxs-lookup"><span data-stu-id="19690-115">Was it due to a particular partner, program, product?</span></span>  
  
## <a name="dimensions"></a><span data-ttu-id="19690-116">維度</span><span class="sxs-lookup"><span data-stu-id="19690-116">Dimensions</span></span>  
 <span data-ttu-id="19690-117">維度是協助量值取用者瞭解這些量值意義的內涵。</span><span class="sxs-lookup"><span data-stu-id="19690-117">Dimensions are the context that help the consumer of measures understand the meaning of those measures.</span></span>  
  
 <span data-ttu-id="19690-118">續上例，假設您為訂單管理程序另外新增三個項目到 BAM 活動中：</span><span class="sxs-lookup"><span data-stu-id="19690-118">Continuing the above example, suppose you add three additional items to the BAM activity for the order management process:</span></span>  
  
1.  <span data-ttu-id="19690-119">交易夥伴名稱 (傳送訂單者)</span><span class="sxs-lookup"><span data-stu-id="19690-119">trading partner name (who sent the order)</span></span>  
  
2.  <span data-ttu-id="19690-120">業務經理名稱 (銷售連絡人)</span><span class="sxs-lookup"><span data-stu-id="19690-120">account manager name (who is the sales contact)</span></span>  
  
3.  <span data-ttu-id="19690-121">銷售地區</span><span class="sxs-lookup"><span data-stu-id="19690-121">sales region</span></span>  
  
 <span data-ttu-id="19690-122">因為活動現在包含三個可能的資料樞紐 (夥伴、業務經理、地區)，彙總這項資料的實際結果將會在執行階段建立三維度的 Cube。</span><span class="sxs-lookup"><span data-stu-id="19690-122">Since the activity now includes three possible data pivots (partner, account manager, region), aggregating this data now literally results in the creation of a three-dimensional cube at run-time.</span></span>  
  
 <span data-ttu-id="19690-123">彙總仍然從工作的第一個項目開始進行，結果會建立單一的「平均持續時間」量值。</span><span class="sxs-lookup"><span data-stu-id="19690-123">It still begins with the first item of work, resulting in the creation of a single "average duration" measure.</span></span> <span data-ttu-id="19690-124">當工作的下一個項目 (因另一張訂單的到來而起始) 完成時，如果此項目的交易夥伴、業務經理和地區都和工作第一個項目的完全相同，那麼目前所要進行的，就只是根據兩個項目 (例如，兩個持續時間的平均值) 重新計算「平均持續時間」量值，以取得單一「平均持續時間」量值的值。</span><span class="sxs-lookup"><span data-stu-id="19690-124">When the next item of work (initiated by the arrival of another purchase order) completes, if trading partner, account manager, and region are all the same as they were for the first item of work, then all that happens is that the "average duration" measure is recalculated, based now on two items (for example, the average of the two durations), to achieve a single "average duration" measure value.</span></span>  
  
 <span data-ttu-id="19690-125">但是只要有不同於此前所遇交易夥伴、業務經理或地區的一組項目出現，就會建立「平均持續時間」量值的新值，並與第一個項目分開維護。</span><span class="sxs-lookup"><span data-stu-id="19690-125">As soon as an item comes where any of trading partner, account manager, or region are different than the set encountered so far, a new "average duration" measure value is created and maintained separate from the first one.</span></span>  
  
 <span data-ttu-id="19690-126">例如，如果工作第三個項目的交易夥伴和前兩個項目的不同，結果將會在交易夥伴維度上產生第二個「平均持續時間」量值的值。</span><span class="sxs-lookup"><span data-stu-id="19690-126">For example, if the trading partner on the third item of work was different than the previous two, the result is creation of a second "average duration" measure value along the trading partner dimension.</span></span> <span data-ttu-id="19690-127">您現在可以沿著交易夥伴維度檢視「平均持續時間」值，並且會看到像是「處理 TradingPartnerX 的訂單所花費的平均時間幾乎是處理 TradingPartnerY 的訂單所需時間的兩倍」等的情況。</span><span class="sxs-lookup"><span data-stu-id="19690-127">Now you can review "average duration" values along the trading partner dimension and see things like "it takes us almost twice as long on average to process the orders from TradingPartnerX as it does for TradingPartnerY."</span></span> <span data-ttu-id="19690-128">此外，維度可以摺疊以方便檢視，這樣您就仍然能看見與任何交易夥伴或其他維度無關之程序的整體「平均持續時間」。</span><span class="sxs-lookup"><span data-stu-id="19690-128">And dimensions can be collapsed for viewing so that one can still see the overall "average duration" for the process independent of any trading partner or other dimension.</span></span>  
  
 <span data-ttu-id="19690-129">最後，如果交易夥伴、業務經理和地區各自都有恰好三個不同的值，一旦出現所有的排列組合，產生的結果將會一個 Rubik's® Cube 的資料；使用者可以在產生的 27 個獨立維護的「平均持續時間」值中擇一進行檢視，而其中的維度即是 Cube 三邊上的一邊。</span><span class="sxs-lookup"><span data-stu-id="19690-129">Finally, if trading partner, account manager, and region each have three and only three distinct values, once all permutations have occurred, the result is a Rubik's® Cube of data, where users can view each of 27 independently maintained "average duration" values, and the dimensions are each of three edges on the cube.</span></span>  
  
 <span data-ttu-id="19690-130">如需有關維度和量值的其他資訊，請參閱「Excel 說明」中的＜關於樞紐分析表和樞紐分析圖的 OLAP 資料來源＞。</span><span class="sxs-lookup"><span data-stu-id="19690-130">For additional information about dimensions and measures, see "About OLAP source data in PivotTable and PivotChart reports" in Excel Help.</span></span>