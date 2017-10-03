---
title: "何謂彙總？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP cubes, BAM
- BAM, aggregations
- BAM, OLAP cubes
- aggregations [BAM], OLAP cubes
- aggregations [BAM], about aggregations
- aggregations [BAM]
ms.assetid: 77d40602-ef56-4a5b-a18f-56ccbff573a4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df24dced4d7075e85b8b002bf90b821ce745f91e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-an-aggregation"></a><span data-ttu-id="8b8a2-103">何謂彙總？</span><span class="sxs-lookup"><span data-stu-id="8b8a2-103">What Is an Aggregation?</span></span>
<span data-ttu-id="8b8a2-104">Excel 將彙總定義為資料的預先計算摘要，可在問題提出之前先備妥答案，以改善查詢回應時間。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-104">Excel defines aggregations as pre-calculated summaries of data that improve query response time by having the answers ready before the questions are asked.</span></span> <span data-ttu-id="8b8a2-105">例如，當資料倉儲事實資料表包含數以萬計的資料列時，如果要查詢兩個特定產品的出貨排程，其必須掃描事實資料表進行計算，這可能需要花很長時間才能得到結果。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-105">For example, when a data warehouse fact table contains hundreds of thousands of rows, a query requesting the shipping schedules for two particular products can take a long time to answer if the fact table has to be scanned to compute the answer.</span></span> <span data-ttu-id="8b8a2-106">但是，如果已經預先計算好要回應的摘要資料，就幾乎可以立即做出回應。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-106">However, the response can be almost immediate if the summarization data to answer this query has been pre-calculated.</span></span>  
  
 <span data-ttu-id="8b8a2-107">下圖是預先計算好彙總資料的範例。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-107">The following figure displays an example of pre-calculated aggregation data.</span></span>  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
<span data-ttu-id="8b8a2-108">BAM OLAP Cube</span><span class="sxs-lookup"><span data-stu-id="8b8a2-108">BAM OLAP Cube</span></span>  
  
 <span data-ttu-id="8b8a2-109">上圖摘要了在兩個月的期間出貨至特定地點之各項產品的數量。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-109">The above figure summarizes the numbers of each product, shipped to specific locations over a two-month time period.</span></span> <span data-ttu-id="8b8a2-110">Excel 通常會將此資料定義為量值。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-110">Excel typically defines this data as measure.</span></span> <span data-ttu-id="8b8a2-111">而用於篩選與分類的資料，Excel 則定義為維度。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-111">The data used for filtering and categorization, Excel defines as dimension.</span></span>  
  
 <span data-ttu-id="8b8a2-112">如需有關瀏覽多維度資料之使用者經驗的詳細資訊，請參閱「Excel 說明」中的＜樞紐分析表＞主題。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-112">For the user experience of browsing multidimensional data, see the PivotTable topic in Excel Help.</span></span>  
  
 <span data-ttu-id="8b8a2-113">您可根據特定檢視中可用的資料，建立多維度活動彙總。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-113">You can create multidimensional activity aggregations based on the data available in a specific view.</span></span> <span data-ttu-id="8b8a2-114">這些彙總包含量值 (要彙總的資料，例如金額) 以及維度 (用以篩選或群組，例如 State 和 City)。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-114">Those aggregations contain measures (data to aggregate, such as dollar amount) and dimensions (used for filtering or grouping, such as State and City).</span></span>  
  
 <span data-ttu-id="8b8a2-115">您可以以線上分析處理 (OLAP) Cube (代表特定時間的商務快照集) 的形式建立彙總，或將彙總建立為即時彙總 (由商務案例決定，您可使用多維度結構即時查看)。</span><span class="sxs-lookup"><span data-stu-id="8b8a2-115">You can create the aggregations in the form of online analytical processing (OLAP) cubes, which represent a snapshot of the business at a specific time, or as real-time aggregations, which the business scenario determines and you see using the multidimensional structure in real time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b8a2-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="8b8a2-116">In This Section</span></span>  
  
-   [<span data-ttu-id="8b8a2-117">排程彙總</span><span class="sxs-lookup"><span data-stu-id="8b8a2-117">Scheduled Aggregations</span></span>](../core/scheduled-aggregations.md)  
  
-   [<span data-ttu-id="8b8a2-118">即時彙總</span><span class="sxs-lookup"><span data-stu-id="8b8a2-118">Real-Time Aggregations</span></span>](../core/real-time-aggregations.md)