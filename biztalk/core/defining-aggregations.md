---
title: "定義彙總 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], creating
- Excel add-in [BAM], creating aggregations
- aggregations [BAM], Excel add-in
- aggregations [BAM], about aggregations
ms.assetid: d5bf22d5-f491-4b08-a604-c7158e6e282f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3412615d03fc9a9776d86fddfb062ab343c5aaeb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="defining-aggregations"></a><span data-ttu-id="b8c89-102">定義彙總</span><span class="sxs-lookup"><span data-stu-id="b8c89-102">Defining Aggregations</span></span>
<span data-ttu-id="b8c89-103">Excel 則定義**彙總**答案準備在問題提出之前為預先計算的資料摘要，改善查詢回應時間。</span><span class="sxs-lookup"><span data-stu-id="b8c89-103">Excel defines **aggregations** as pre-calculated summaries of data that improve query response time by having the answers ready before the questions are asked.</span></span> <span data-ttu-id="b8c89-104">例如，當資料倉儲事實資料表包含數以萬計的資料列時，如果要查詢兩個特定產品的出貨排程，其必須掃描事實資料表進行計算，這可能需要花很長時間才能得到結果。</span><span class="sxs-lookup"><span data-stu-id="b8c89-104">For example, when a data warehouse fact table contains hundreds of thousands of rows, a query requesting the shipping schedules for two particular products can take a long time to answer if the fact table has to be scanned to compute the answer.</span></span> <span data-ttu-id="b8c89-105">但是，如果已經預先計算好要回應的摘要資料，就幾乎可以立即做出回應。</span><span class="sxs-lookup"><span data-stu-id="b8c89-105">However, the response can be almost immediate if the summarization data to answer this query has been pre-calculated.</span></span>  
  
 <span data-ttu-id="b8c89-106">下圖是預先計算好彙總資料的範例。</span><span class="sxs-lookup"><span data-stu-id="b8c89-106">The following figure displays an example of pre-calculated aggregation data.</span></span>  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
<span data-ttu-id="b8c89-107">預先計算的彙總資料</span><span class="sxs-lookup"><span data-stu-id="b8c89-107">Pre-calculated Aggregation Data</span></span>  
  
 <span data-ttu-id="b8c89-108">上圖摘要了在兩個月的期間出貨至特定地點之各項產品的數量。</span><span class="sxs-lookup"><span data-stu-id="b8c89-108">The above figure summarizes the numbers of each product, shipped to specific locations over a two-month time period.</span></span> <span data-ttu-id="b8c89-109">Excel 通常會定義這項資料當做**量值**。</span><span class="sxs-lookup"><span data-stu-id="b8c89-109">Excel typically defines this data as **measure**.</span></span> <span data-ttu-id="b8c89-110">用於篩選和分類的資料，Excel 則定義為**維度**。</span><span class="sxs-lookup"><span data-stu-id="b8c89-110">The data used for filtering and categorization, Excel defines as **dimension**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8c89-111">BAM 不支援 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services 的具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="b8c89-111">BAM does not support using named instances for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services.</span></span>  
  
 <span data-ttu-id="b8c89-112">如需有關瀏覽多維度資料的使用者經驗，請參閱「Excel 說明」中的＜樞紐分析表＞主題。</span><span class="sxs-lookup"><span data-stu-id="b8c89-112">For the user experience of browsing multidimensional data, see the Pivot table topic in Excel Help.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8c89-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="b8c89-113">In This Section</span></span>  
  
-   [<span data-ttu-id="b8c89-114">如何定義量值</span><span class="sxs-lookup"><span data-stu-id="b8c89-114">How to Define Measures</span></span>](../core/how-to-define-measures.md)  
  
-   [<span data-ttu-id="b8c89-115">定義維度</span><span class="sxs-lookup"><span data-stu-id="b8c89-115">Defining Dimensions</span></span>](../core/defining-dimensions.md)  
  
-   [<span data-ttu-id="b8c89-116">如何使用樞紐分析表</span><span class="sxs-lookup"><span data-stu-id="b8c89-116">How to Use the PivotTable</span></span>](../core/how-to-use-the-pivottable.md)  
  
-   [<span data-ttu-id="b8c89-117">定義即時彙總</span><span class="sxs-lookup"><span data-stu-id="b8c89-117">Defining Real-Time Aggregations</span></span>](../core/defining-real-time-aggregations.md)  
  
## <a name="see-also"></a><span data-ttu-id="b8c89-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8c89-118">See Also</span></span>  
 [<span data-ttu-id="b8c89-119">定義 BAM 檢視</span><span class="sxs-lookup"><span data-stu-id="b8c89-119">Defining a BAM View</span></span>](../core/defining-a-bam-view.md)