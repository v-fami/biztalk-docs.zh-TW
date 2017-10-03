---
title: "BAM 入口網站上的彙總頁面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], alerts
- aggregations [BAM], viewing results
- alerts, aggregations
- Aggregations page [BAM portal]
- BAM portal, aggregations
ms.assetid: 6bc1a6f2-9e9a-4db6-aaa1-188ed2f2641f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a61df22bf5d07bd1b4d955f2baf884459de52998
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="aggregations-on-the-bam-portal-page"></a><span data-ttu-id="674bd-102">BAM 入口網站頁面上的彙總</span><span class="sxs-lookup"><span data-stu-id="674bd-102">Aggregations on the BAM Portal Page</span></span>
<span data-ttu-id="674bd-103">商務使用者、開發人員和商務分析師使用 BAM 入口網站頁面呈現所需的彙總資料，這是預先計算的資料集摘要，可顯示該資料集具代表性的特性。</span><span class="sxs-lookup"><span data-stu-id="674bd-103">Business end users, developers, and business analysts use the BAM portal page when they need to present aggregated data, which are precalculated summaries of a data set that convey representative characteristics of that data set.</span></span> <span data-ttu-id="674bd-104">BAM 入口網站的 [彙總] 頁面能讓您以圖形化圖表和樞紐分析表的形式顯示彙總資料。</span><span class="sxs-lookup"><span data-stu-id="674bd-104">The Aggregations page of the BAM portal allows you to display aggregated data in the form of a graphical chart and accompanying PivotTable report.</span></span>  
  
## <a name="the-aggregations-page"></a><span data-ttu-id="674bd-105">彙總頁面</span><span class="sxs-lookup"><span data-stu-id="674bd-105">The Aggregations page</span></span>  
 <span data-ttu-id="674bd-106">[彙總] 頁面會顯示活動的結果，以共同傳達程序或整體商務的狀況。</span><span class="sxs-lookup"><span data-stu-id="674bd-106">The Aggregations page displays the results of an activity that collectively convey the health of the process or of the overall business.</span></span> <span data-ttu-id="674bd-107">例如，使用者可能只需要簡單的圓形圖，顯示所收到的 1,000 張發票明細，以查看每張發票的處理階段 (400 張還在評估，400 張已拒絕，100 張已付款，100 張還在分配款項)。</span><span class="sxs-lookup"><span data-stu-id="674bd-107">For example, a user may want to see a simple pie chart that shows a breakdown of the 1,000 invoices received in terms of what stage of processing has been reached by each invoice (400 still in "evaluation," 400 rejected, 100 paid, and 100 still in "fund allocation").</span></span>  
  
### <a name="creating-alerts-for-aggregations"></a><span data-ttu-id="674bd-108">建立彙總的警示</span><span class="sxs-lookup"><span data-stu-id="674bd-108">Creating alerts for aggregations</span></span>  
 <span data-ttu-id="674bd-109">您可以使用彙總做為建立警示的基礎 (如果超過 500 張發票在評估階段時通知我)。</span><span class="sxs-lookup"><span data-stu-id="674bd-109">You can use aggregations as the basis for creating an alert ("Notify me if there are ever more than 500 invoices in the "evaluation" stage of the process).</span></span> <span data-ttu-id="674bd-110">若要這樣做，以滑鼠右鍵按一下任何樞紐分析表資料格，然後選取**設定警示**，或按一下資料格，並按一下 **設定警示**按鈕右邊的樞紐分析表報表。</span><span class="sxs-lookup"><span data-stu-id="674bd-110">To do this, you right-click any PivotTable cell and select **Set Alert**, or you click a cell and click the **Set Alert** button to the right of the PivotTable report.</span></span> <span data-ttu-id="674bd-111">如需有關如何建立警示的詳細資訊，請參閱[如何設定警示](../core/how-to-set-an-alert.md)。</span><span class="sxs-lookup"><span data-stu-id="674bd-111">For more information about creating an alert, see [How to Set an Alert](../core/how-to-set-an-alert.md).</span></span>  
  
### <a name="viewing-individual-results-of-aggregations"></a><span data-ttu-id="674bd-112">檢視彙總的個別結果</span><span class="sxs-lookup"><span data-stu-id="674bd-112">Viewing individual results of aggregations</span></span>  
 <span data-ttu-id="674bd-113">您也可以選取任何彙總數量 (例如，400 張發票仍在評估中)，並檢視彙總的個別結果。</span><span class="sxs-lookup"><span data-stu-id="674bd-113">You can also select any aggregate amount (for example, 400 invoices still in "evaluation") and see the individual results for the aggregation.</span></span> <span data-ttu-id="674bd-114">您可以存取個別結果的任何樞紐分析表儲存格上按一下滑鼠右鍵，然後選取**顯示結果**。</span><span class="sxs-lookup"><span data-stu-id="674bd-114">You access the individual results by right-clicking any PivotTable cell and selecting **Show Results**.</span></span> <span data-ttu-id="674bd-115">執行此動作後，將會帶領您前往 [活動搜尋] 頁面，搜尋會自動建構然後顯示結果 (以 400 張發票來說，每張發票都有一筆記錄)。</span><span class="sxs-lookup"><span data-stu-id="674bd-115">In response to this action, you are sent to the Activity Search page, the search itself is automatically constructed, and the results are displayed (in this example, one record for each of the 400 invoices).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="674bd-116">某些 BAM 檢視沒有關聯的彙總，所以根據檢視建立的方式不同，或許未能存取到相關資訊。</span><span class="sxs-lookup"><span data-stu-id="674bd-116">Some BAM views do not have aggregations associated with them, and so there may be no information to access depending on how the view was created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="674bd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="674bd-117">See Also</span></span>  
 <span data-ttu-id="674bd-118">[BAM 入口網站](../core/bam-portal.md) </span><span class="sxs-lookup"><span data-stu-id="674bd-118">[BAM Portal](../core/bam-portal.md) </span></span>  
 <span data-ttu-id="674bd-119">[BAM 入口網站上的活動搜尋頁面](../core/activity-search-on-the-bam-portal-page.md) </span><span class="sxs-lookup"><span data-stu-id="674bd-119">[Activity Search on the BAM Portal Page](../core/activity-search-on-the-bam-portal-page.md) </span></span>  
 [<span data-ttu-id="674bd-120">BAM 入口網站上的警示管理員頁面</span><span class="sxs-lookup"><span data-stu-id="674bd-120">Alert Manager on the BAM Portal Page</span></span>](../core/alert-manager-on-the-bam-portal-page.md)