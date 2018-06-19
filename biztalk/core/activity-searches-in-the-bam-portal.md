---
title: BAM 入口網站中的活動搜尋 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities [BAM], searching
- queries [BAM], field descriptions
- Query Builder [BAM portal], creating queries
- queries [BAM], activity searches
- Query Builder [BAM portal], about Query Builder
- Query Builder [BAM portal], activity searches
- Query Builder [BAM portal]
- Query Builder [BAM portal], field descriptions
- BAM portal, Query Builder
- BAM portal, activity searches
ms.assetid: 60ab8deb-ebe2-4959-97fd-261ff64d500c
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 723848f61294cc710bd2292758383cf674093265
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966596"
---
# <a name="activity-searches-in-the-bam-portal"></a><span data-ttu-id="00532-102">BAM 入口網站中的活動搜尋</span><span class="sxs-lookup"><span data-stu-id="00532-102">Activity Searches in the BAM Portal</span></span>
<span data-ttu-id="00532-103">活動搜尋可讓您對 BAM 資料執行搜尋，根據 BAM 檢視中的追蹤值和項目尋找符合您指定之準則的活動，並顯示這些活動讓您進行編輯或根據這些活動建立警示。</span><span class="sxs-lookup"><span data-stu-id="00532-103">An activity search allows you to perform searches against BAM data to find activities that match the criteria you specify based on tracked values and items available in a BAM view, and to display these activities so that you can edit them or create alerts based on them.</span></span>  
  
## <a name="parts-of-the-query-builder"></a><span data-ttu-id="00532-104">查詢建立器的組成部分</span><span class="sxs-lookup"><span data-stu-id="00532-104">Parts of the Query Builder</span></span>  
 <span data-ttu-id="00532-105">您可以選取商務資料項目，針對這些項目建立布林值比較來擷取所需的資料，以建置活動搜尋的查詢。</span><span class="sxs-lookup"><span data-stu-id="00532-105">You build queries for your activity search by selecting items of business data against which you will create Boolean comparisons to extract data of interest.</span></span> <span data-ttu-id="00532-106">您選取從 BAM 檢視，啟動**我的檢視**入口網站的框架。</span><span class="sxs-lookup"><span data-stu-id="00532-106">You start by selecting a BAM view from the **My Views** frame of the portal.</span></span> <span data-ttu-id="00532-107">從選取的檢視中，您可以選取要建置查詢的活動。</span><span class="sxs-lookup"><span data-stu-id="00532-107">From the selected view you select an activity on which to build the query.</span></span>  
  
 <span data-ttu-id="00532-108">![](../core/media/bamportalviewschooser.gif "BAMPortalViewsChooser")</span><span class="sxs-lookup"><span data-stu-id="00532-108">![](../core/media/bamportalviewschooser.gif "BAMPortalViewsChooser")</span></span>  
  
 <span data-ttu-id="00532-109">選取活動之後，入口網站的內容框架就會顯示 [查詢建立器]、[欄位選擇器] 和 [結果] 方塊。</span><span class="sxs-lookup"><span data-stu-id="00532-109">When you have selected the activity, the content frame of the portal displays the Query builder, Column Chooser, and Results boxes.</span></span> <span data-ttu-id="00532-110">您可以開啟現有的查詢或建置新的查詢。</span><span class="sxs-lookup"><span data-stu-id="00532-110">You can open an existing query or you can build a new one.</span></span>  
  
 <span data-ttu-id="00532-111">![](../core/media/activitysearchquerybuilder.gif "ActivitySearchQueryBuilder")</span><span class="sxs-lookup"><span data-stu-id="00532-111">![](../core/media/activitysearchquerybuilder.gif "ActivitySearchQueryBuilder")</span></span>  
  
 <span data-ttu-id="00532-112">若要建立新的查詢，您所選取的商務資料的項目從開始**商務資料**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="00532-112">To build a new query you start by selecting a business data item from the **Business Data** drop-down list.</span></span>  
  
 <span data-ttu-id="00532-113">![](../core/media/activitysearchquerybuilderbusinessdatadropdown.gif "ActivitySearchQueryBuilderBusinessDataDropdown")</span><span class="sxs-lookup"><span data-stu-id="00532-113">![](../core/media/activitysearchquerybuilderbusinessdatadropdown.gif "ActivitySearchQueryBuilderBusinessDataDropdown")</span></span>  
  
 <span data-ttu-id="00532-114">接著，您可以在 [運算子] 下拉式清單中選取比較運算子。</span><span class="sxs-lookup"><span data-stu-id="00532-114">Next, you select your comparison operator in the Operator drop-down list.</span></span> <span data-ttu-id="00532-115">比較運算子可讓您精簡查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="00532-115">The comparison operator allows you to refine the results of the query.</span></span>  
  
 <span data-ttu-id="00532-116">![](../core/media/activitysearchcomparisonoperatordropdown.gif "ActivitySearchComparisonOperatorDropDown")</span><span class="sxs-lookup"><span data-stu-id="00532-116">![](../core/media/activitysearchcomparisonoperatordropdown.gif "ActivitySearchComparisonOperatorDropDown")</span></span>  
  
 <span data-ttu-id="00532-117">[值] 下拉式清單會根據商務資料項目所代表的資料類型顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="00532-117">The Value drop-down list is context-sensitive based on the type of data represented by the business data item.</span></span> <span data-ttu-id="00532-118">使用者介面 (UI) 會隨著允取資料的類型變更而變更。</span><span class="sxs-lookup"><span data-stu-id="00532-118">The user interface (UI) changes as the type of permitted data changes.</span></span>  
  
 <span data-ttu-id="00532-119">您可以加入與查詢子句，或 OR 運算子，以形成更複雜的查詢，方法是按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="00532-119">You can join clauses of the query with AND or OR operators to form more complex queries by clicking the **Add** button.</span></span>  
  
 <span data-ttu-id="00532-120">![](../core/media/activitysearchjoiningclauses.gif "ActivitySearchJoiningClauses")</span><span class="sxs-lookup"><span data-stu-id="00532-120">![](../core/media/activitysearchjoiningclauses.gif "ActivitySearchJoiningClauses")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00532-121">您無法群組子句。</span><span class="sxs-lookup"><span data-stu-id="00532-121">You cannot group clauses.</span></span> <span data-ttu-id="00532-122">查詢是由以 AND/OR 運算子加入的個別子句所組成的簡單字串。</span><span class="sxs-lookup"><span data-stu-id="00532-122">A query is a simple string of individual clauses joined by AND/OR operators.</span></span>  
  
 <span data-ttu-id="00532-123">下表說明日期和時間欄位。</span><span class="sxs-lookup"><span data-stu-id="00532-123">The following table describes the date and time fields.</span></span>  
  
|<span data-ttu-id="00532-124">運算子</span><span class="sxs-lookup"><span data-stu-id="00532-124">Operator</span></span>|<span data-ttu-id="00532-125">Description</span><span class="sxs-lookup"><span data-stu-id="00532-125">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="00532-126">**在**</span><span class="sxs-lookup"><span data-stu-id="00532-126">**At**</span></span>|<span data-ttu-id="00532-127">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="00532-127">Specifies an exact match.</span></span> <span data-ttu-id="00532-128">相當於布林值的等於 (=) 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-128">Equivalent to a Boolean Equals (=) operation.</span></span> <span data-ttu-id="00532-129">**注意：** 如果您選取**在**運算子，然後在入口網站會使用午夜做為預設值沒有時間部分指定日期。</span><span class="sxs-lookup"><span data-stu-id="00532-129">**Note:**  If you select the **At** operator and specify a date with no time part the portal uses midnight as the default value.</span></span> <span data-ttu-id="00532-130">如果這不是您的目的，使用**當時或之前**或**在或之後**運算子取得所需的結果。</span><span class="sxs-lookup"><span data-stu-id="00532-130">If this is not your intent, use the **At or before** or the **At or after** operators to obtain the desired results.</span></span>|  
|<span data-ttu-id="00532-131">**在或之前**</span><span class="sxs-lookup"><span data-stu-id="00532-131">**On or before**</span></span>|<span data-ttu-id="00532-132">指定只有在指定日期當天或之前的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="00532-132">Specifies that only transactions on or before the specified date are matched.</span></span> <span data-ttu-id="00532-133">相當於布林值的小於或等於 (≤ 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-133">Equivalent to a Boolean less than or equals (≤) operation.</span></span>|  
|<span data-ttu-id="00532-134">**在或之後**</span><span class="sxs-lookup"><span data-stu-id="00532-134">**On or after**</span></span>|<span data-ttu-id="00532-135">指定只有在指定日期當天或之後的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="00532-135">Specifies that only transactions on or after the specified date are matched.</span></span> <span data-ttu-id="00532-136">相當於布林值的大於或等於 (≥ 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-136">Equivalent to a Boolean greater than or equals (≥) operation.</span></span>|  
|<span data-ttu-id="00532-137">**之前**</span><span class="sxs-lookup"><span data-stu-id="00532-137">**Before**</span></span>|<span data-ttu-id="00532-138">指定只有在指定日期之前的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="00532-138">Specifies that only transactions before the specified date are matched.</span></span> <span data-ttu-id="00532-139">相當於布林值的小於 (<) 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-139">Equivalent to a Boolean less than (<) operation.</span></span>|  
|<span data-ttu-id="00532-140">**After**</span><span class="sxs-lookup"><span data-stu-id="00532-140">**After**</span></span>|<span data-ttu-id="00532-141">指定只有在指定日期之後的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="00532-141">Specifies that only transactions after the specified date are matched.</span></span> <span data-ttu-id="00532-142">相當於布林值的大於 (>) 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-142">Equivalent to a Boolean greater than (>) operation.</span></span>|  
|<span data-ttu-id="00532-143">**在過去**</span><span class="sxs-lookup"><span data-stu-id="00532-143">**In the last**</span></span>|<span data-ttu-id="00532-144">指定只有在先前指定時間週期發生的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="00532-144">Specifies that only transactions that occurred in the previous specified time period are matched.</span></span> <span data-ttu-id="00532-145">時間週期可以秒、分、小時或天為單位指定。</span><span class="sxs-lookup"><span data-stu-id="00532-145">The time period can be specified in seconds, minutes, hours, or days.</span></span>|  
|<span data-ttu-id="00532-146">**最後一個之前**</span><span class="sxs-lookup"><span data-stu-id="00532-146">**Before the last**</span></span>|<span data-ttu-id="00532-147">指定只有在指定時間週期之前發生的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="00532-147">Specifies that only transactions that occurred prior to the specified time period are matched.</span></span> <span data-ttu-id="00532-148">時間週期可以秒、分、小時或天為單位指定。</span><span class="sxs-lookup"><span data-stu-id="00532-148">The time period can be specified in seconds, minutes, hours, or days.</span></span>|  
|<span data-ttu-id="00532-149">**是空的**</span><span class="sxs-lookup"><span data-stu-id="00532-149">**Is empty**</span></span>|<span data-ttu-id="00532-150">指定只有商務資料項目不包含任何資料 (資料欄位的值為空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="00532-150">Specifies that only transactions for which the business data item contains no data (the value of data field is NULL) are returned.</span></span>|  
|<span data-ttu-id="00532-151">**不是空的**</span><span class="sxs-lookup"><span data-stu-id="00532-151">**Is not empty**</span></span>|<span data-ttu-id="00532-152">指定只有商務資料項目包含資料 (資料欄位的值不是空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="00532-152">Specifies that only transactions for which the business data item contains data (the value of data field is not NULL) are returned.</span></span>|  
  
 <span data-ttu-id="00532-153">下表說明數字欄位和持續時間欄位。</span><span class="sxs-lookup"><span data-stu-id="00532-153">The following table describes the numeric fields and the duration fields.</span></span> <span data-ttu-id="00532-154">數字欄位包含如量或貨幣數的資料。</span><span class="sxs-lookup"><span data-stu-id="00532-154">Numeric fields contain data such as quantities or currency amounts.</span></span> <span data-ttu-id="00532-155">持續時間欄位指定時間週期。</span><span class="sxs-lookup"><span data-stu-id="00532-155">Duration fields specify a time period.</span></span>  
  
|<span data-ttu-id="00532-156">運算子</span><span class="sxs-lookup"><span data-stu-id="00532-156">Operator</span></span>|<span data-ttu-id="00532-157">Description</span><span class="sxs-lookup"><span data-stu-id="00532-157">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="00532-158">**等於**</span><span class="sxs-lookup"><span data-stu-id="00532-158">**Equals**</span></span>|<span data-ttu-id="00532-159">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="00532-159">Specifies an exact match.</span></span> <span data-ttu-id="00532-160">相當於布林值的等於 (=) 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-160">Equivalent to a Boolean Equals (=) operation.</span></span>|  
|<span data-ttu-id="00532-161">**大於**</span><span class="sxs-lookup"><span data-stu-id="00532-161">**Greater than**</span></span>|<span data-ttu-id="00532-162">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="00532-162">Specifies an exact match.</span></span> <span data-ttu-id="00532-163">相當於布林值的大於 (>) 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-163">Equivalent to a Boolean Greater Than (>) operation.</span></span>|  
|<span data-ttu-id="00532-164">**大於或等於**</span><span class="sxs-lookup"><span data-stu-id="00532-164">**Greater than or equal**</span></span>|<span data-ttu-id="00532-165">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="00532-165">Specifies an exact match.</span></span> <span data-ttu-id="00532-166">相當於布林值的大於或等於 (≥ 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-166">Equivalent to a Boolean Greater Than or Equals (≥) operation.</span></span>|  
|<span data-ttu-id="00532-167">**小於**</span><span class="sxs-lookup"><span data-stu-id="00532-167">**Less than**</span></span>|<span data-ttu-id="00532-168">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="00532-168">Specifies an exact match.</span></span> <span data-ttu-id="00532-169">相當於布林值的小於 (<) 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-169">Equivalent to a Boolean Less Than (<) operation.</span></span>|  
|<span data-ttu-id="00532-170">**小於或等於**</span><span class="sxs-lookup"><span data-stu-id="00532-170">**Less than or equal**</span></span>|<span data-ttu-id="00532-171">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="00532-171">Specifies an exact match.</span></span> <span data-ttu-id="00532-172">相當於布林值的小於或等於 (≤ 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-172">Equivalent to a Less Than or Equals (≤) operation.</span></span>|  
|<span data-ttu-id="00532-173">**不等於**</span><span class="sxs-lookup"><span data-stu-id="00532-173">**Not Equal**</span></span>|<span data-ttu-id="00532-174">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="00532-174">Specifies an exact match.</span></span> <span data-ttu-id="00532-175">相當於布林值的不等於 (≠) 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-175">Equivalent to a Not Equals (≠) operation.</span></span>|  
|<span data-ttu-id="00532-176">**是空的**</span><span class="sxs-lookup"><span data-stu-id="00532-176">**Is empty**</span></span>|<span data-ttu-id="00532-177">指定只有商務資料項目不包含任何資料 (資料欄位的值為空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="00532-177">Specifies that only transactions for which the business data item contains no data (the value of data field is NULL) are returned.</span></span>|  
|<span data-ttu-id="00532-178">**不是空的**</span><span class="sxs-lookup"><span data-stu-id="00532-178">**Is not empty**</span></span>|<span data-ttu-id="00532-179">指定只有商務資料項目包含資料 (資料欄位的值不是空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="00532-179">Specifies that only transactions for which the business data item contains data (the value of data field is not NULL) are returned.</span></span>|  
  
 <span data-ttu-id="00532-180">下表說明文字欄位。</span><span class="sxs-lookup"><span data-stu-id="00532-180">The following table describes the text fields.</span></span>  
  
|<span data-ttu-id="00532-181">運算子</span><span class="sxs-lookup"><span data-stu-id="00532-181">Operator</span></span>|<span data-ttu-id="00532-182">Description</span><span class="sxs-lookup"><span data-stu-id="00532-182">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="00532-183">**完全**</span><span class="sxs-lookup"><span data-stu-id="00532-183">**Is Exactly**</span></span>|<span data-ttu-id="00532-184">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="00532-184">Specifies an exact match.</span></span> <span data-ttu-id="00532-185">相當於布林值的等於 (=) 運算。</span><span class="sxs-lookup"><span data-stu-id="00532-185">Equivalent to a Boolean Equals (=) operation.</span></span>|  
|<span data-ttu-id="00532-186">**包含**</span><span class="sxs-lookup"><span data-stu-id="00532-186">**Contains**</span></span>|<span data-ttu-id="00532-187">指定商務資料項目中的文字包含指定的值。</span><span class="sxs-lookup"><span data-stu-id="00532-187">Specifies that the text in the business data item contains the specified value.</span></span> <span data-ttu-id="00532-188">這可讓您在資料上執行部分相符。</span><span class="sxs-lookup"><span data-stu-id="00532-188">This allows you to do partial matches on the data.</span></span>|  
|<span data-ttu-id="00532-189">**不包含**</span><span class="sxs-lookup"><span data-stu-id="00532-189">**Does not contain**</span></span>|<span data-ttu-id="00532-190">指定商務資料項目中的文字不包含指定的值。</span><span class="sxs-lookup"><span data-stu-id="00532-190">Specifies that the text in the business data item does not contain the specified value.</span></span>|  
|<span data-ttu-id="00532-191">**是空的**</span><span class="sxs-lookup"><span data-stu-id="00532-191">**Is empty**</span></span>|<span data-ttu-id="00532-192">指定只有商務資料項目不包含任何資料 (資料欄位的值為空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="00532-192">Specifies that only transactions for which the business data item contains no data (the value of data field is NULL) are returned.</span></span>|  
|<span data-ttu-id="00532-193">**不是空的**</span><span class="sxs-lookup"><span data-stu-id="00532-193">**Is not empty**</span></span>|<span data-ttu-id="00532-194">指定只有商務資料項目包含資料 (資料欄位的值不是空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="00532-194">Specifies that only transactions for which the business data item contains data (the value of data field is not NULL) are returned.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="00532-195">本節內容</span><span class="sxs-lookup"><span data-stu-id="00532-195">In This Section</span></span>  
  
-   [<span data-ttu-id="00532-196">如何在活動搜尋中建立查詢</span><span class="sxs-lookup"><span data-stu-id="00532-196">How to Create a Query in Activity Search</span></span>](../core/how-to-create-a-query-in-activity-search.md)  
  
-   [<span data-ttu-id="00532-197">如何設定警示</span><span class="sxs-lookup"><span data-stu-id="00532-197">How to Set an Alert</span></span>](../core/how-to-set-an-alert.md)  
  
-   [<span data-ttu-id="00532-198">如何檢視活動搜尋的結果</span><span class="sxs-lookup"><span data-stu-id="00532-198">How to View the Results of an Activity Search</span></span>](../core/how-to-view-the-results-of-an-activity-search.md)  
  
## <a name="see-also"></a><span data-ttu-id="00532-199">請參閱</span><span class="sxs-lookup"><span data-stu-id="00532-199">See Also</span></span>  
 [<span data-ttu-id="00532-200">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="00532-200">BAM Portal</span></span>](../core/bam-portal.md)