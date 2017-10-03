---
title: "BAM 入口網站中的活動搜尋 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 617461b104f3188c14bb7c5b6eb5eb0bd329693f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="activity-searches-in-the-bam-portal"></a><span data-ttu-id="37d10-102">BAM 入口網站中的活動搜尋</span><span class="sxs-lookup"><span data-stu-id="37d10-102">Activity Searches in the BAM Portal</span></span>
<span data-ttu-id="37d10-103">活動搜尋可讓您對 BAM 資料執行搜尋，根據 BAM 檢視中的追蹤值和項目尋找符合您指定之準則的活動，並顯示這些活動讓您進行編輯或根據這些活動建立警示。</span><span class="sxs-lookup"><span data-stu-id="37d10-103">An activity search allows you to perform searches against BAM data to find activities that match the criteria you specify based on tracked values and items available in a BAM view, and to display these activities so that you can edit them or create alerts based on them.</span></span>  
  
## <a name="parts-of-the-query-builder"></a><span data-ttu-id="37d10-104">查詢建立器的組成部分</span><span class="sxs-lookup"><span data-stu-id="37d10-104">Parts of the Query Builder</span></span>  
 <span data-ttu-id="37d10-105">您可以選取商務資料項目，針對這些項目建立布林值比較來擷取所需的資料，以建置活動搜尋的查詢。</span><span class="sxs-lookup"><span data-stu-id="37d10-105">You build queries for your activity search by selecting items of business data against which you will create Boolean comparisons to extract data of interest.</span></span> <span data-ttu-id="37d10-106">您選取從 BAM 檢視，啟動**我的檢視**入口網站的框架。</span><span class="sxs-lookup"><span data-stu-id="37d10-106">You start by selecting a BAM view from the **My Views** frame of the portal.</span></span> <span data-ttu-id="37d10-107">從選取的檢視中，您可以選取要建置查詢的活動。</span><span class="sxs-lookup"><span data-stu-id="37d10-107">From the selected view you select an activity on which to build the query.</span></span>  
  
 ![](../core/media/bamportalviewschooser.gif "BAMPortalViewsChooser")  
  
 <span data-ttu-id="37d10-108">選取活動之後，入口網站的內容框架就會顯示 [查詢建立器]、[欄位選擇器] 和 [結果] 方塊。</span><span class="sxs-lookup"><span data-stu-id="37d10-108">When you have selected the activity, the content frame of the portal displays the Query builder, Column Chooser, and Results boxes.</span></span> <span data-ttu-id="37d10-109">您可以開啟現有的查詢或建置新的查詢。</span><span class="sxs-lookup"><span data-stu-id="37d10-109">You can open an existing query or you can build a new one.</span></span>  
  
 ![](../core/media/activitysearchquerybuilder.gif "ActivitySearchQueryBuilder")  
  
 <span data-ttu-id="37d10-110">若要建立新的查詢，您所選取的商務資料的項目從開始**商務資料**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="37d10-110">To build a new query you start by selecting a business data item from the **Business Data** drop-down list.</span></span>  
  
 ![](../core/media/activitysearchquerybuilderbusinessdatadropdown.gif "ActivitySearchQueryBuilderBusinessDataDropdown")  
  
 <span data-ttu-id="37d10-111">接著，您可以在 [運算子] 下拉式清單中選取比較運算子。</span><span class="sxs-lookup"><span data-stu-id="37d10-111">Next, you select your comparison operator in the Operator drop-down list.</span></span> <span data-ttu-id="37d10-112">比較運算子可讓您精簡查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="37d10-112">The comparison operator allows you to refine the results of the query.</span></span>  
  
 ![](../core/media/activitysearchcomparisonoperatordropdown.gif "ActivitySearchComparisonOperatorDropDown")  
  
 <span data-ttu-id="37d10-113">[值] 下拉式清單會根據商務資料項目所代表的資料類型顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="37d10-113">The Value drop-down list is context-sensitive based on the type of data represented by the business data item.</span></span> <span data-ttu-id="37d10-114">使用者介面 (UI) 會隨著允取資料的類型變更而變更。</span><span class="sxs-lookup"><span data-stu-id="37d10-114">The user interface (UI) changes as the type of permitted data changes.</span></span>  
  
 <span data-ttu-id="37d10-115">您可以加入與查詢子句，或 OR 運算子，以形成更複雜的查詢，方法是按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="37d10-115">You can join clauses of the query with AND or OR operators to form more complex queries by clicking the **Add** button.</span></span>  
  
 ![](../core/media/activitysearchjoiningclauses.gif "ActivitySearchJoiningClauses")  
  
> [!NOTE]
>  <span data-ttu-id="37d10-116">您無法群組子句。</span><span class="sxs-lookup"><span data-stu-id="37d10-116">You cannot group clauses.</span></span> <span data-ttu-id="37d10-117">查詢是由以 AND/OR 運算子加入的個別子句所組成的簡單字串。</span><span class="sxs-lookup"><span data-stu-id="37d10-117">A query is a simple string of individual clauses joined by AND/OR operators.</span></span>  
  
 <span data-ttu-id="37d10-118">下表說明日期和時間欄位。</span><span class="sxs-lookup"><span data-stu-id="37d10-118">The following table describes the date and time fields.</span></span>  
  
|<span data-ttu-id="37d10-119">運算子</span><span class="sxs-lookup"><span data-stu-id="37d10-119">Operator</span></span>|<span data-ttu-id="37d10-120">Description</span><span class="sxs-lookup"><span data-stu-id="37d10-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="37d10-121">**在**</span><span class="sxs-lookup"><span data-stu-id="37d10-121">**At**</span></span>|<span data-ttu-id="37d10-122">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="37d10-122">Specifies an exact match.</span></span> <span data-ttu-id="37d10-123">相當於布林值的等於 (=) 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-123">Equivalent to a Boolean Equals (=) operation.</span></span> <span data-ttu-id="37d10-124">**注意：**如果您選取**在**運算子，然後在入口網站會使用午夜做為預設值沒有時間部分指定日期。</span><span class="sxs-lookup"><span data-stu-id="37d10-124">**Note:**  If you select the **At** operator and specify a date with no time part the portal uses midnight as the default value.</span></span> <span data-ttu-id="37d10-125">如果這不是您的目的，使用**當時或之前**或**在或之後**運算子取得所需的結果。</span><span class="sxs-lookup"><span data-stu-id="37d10-125">If this is not your intent, use the **At or before** or the **At or after** operators to obtain the desired results.</span></span>|  
|<span data-ttu-id="37d10-126">**在或之前**</span><span class="sxs-lookup"><span data-stu-id="37d10-126">**On or before**</span></span>|<span data-ttu-id="37d10-127">指定只有在指定日期當天或之前的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="37d10-127">Specifies that only transactions on or before the specified date are matched.</span></span> <span data-ttu-id="37d10-128">相當於布林值的小於或等於 (≤ 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-128">Equivalent to a Boolean less than or equals (≤) operation.</span></span>|  
|<span data-ttu-id="37d10-129">**在或之後**</span><span class="sxs-lookup"><span data-stu-id="37d10-129">**On or after**</span></span>|<span data-ttu-id="37d10-130">指定只有在指定日期當天或之後的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="37d10-130">Specifies that only transactions on or after the specified date are matched.</span></span> <span data-ttu-id="37d10-131">相當於布林值的大於或等於 (≥ 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-131">Equivalent to a Boolean greater than or equals (≥) operation.</span></span>|  
|<span data-ttu-id="37d10-132">**之前**</span><span class="sxs-lookup"><span data-stu-id="37d10-132">**Before**</span></span>|<span data-ttu-id="37d10-133">指定只有在指定日期之前的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="37d10-133">Specifies that only transactions before the specified date are matched.</span></span> <span data-ttu-id="37d10-134">相當於布林值少於 (\<) 作業。</span><span class="sxs-lookup"><span data-stu-id="37d10-134">Equivalent to a Boolean less than (\<) operation.</span></span>|  
|<span data-ttu-id="37d10-135">**After**</span><span class="sxs-lookup"><span data-stu-id="37d10-135">**After**</span></span>|<span data-ttu-id="37d10-136">指定只有在指定日期之後的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="37d10-136">Specifies that only transactions after the specified date are matched.</span></span> <span data-ttu-id="37d10-137">相當於布林值的大於 (>) 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-137">Equivalent to a Boolean greater than (>) operation.</span></span>|  
|<span data-ttu-id="37d10-138">**在過去**</span><span class="sxs-lookup"><span data-stu-id="37d10-138">**In the last**</span></span>|<span data-ttu-id="37d10-139">指定只有在先前指定時間週期發生的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="37d10-139">Specifies that only transactions that occurred in the previous specified time period are matched.</span></span> <span data-ttu-id="37d10-140">時間週期可以秒、分、小時或天為單位指定。</span><span class="sxs-lookup"><span data-stu-id="37d10-140">The time period can be specified in seconds, minutes, hours, or days.</span></span>|  
|<span data-ttu-id="37d10-141">**最後一個之前**</span><span class="sxs-lookup"><span data-stu-id="37d10-141">**Before the last**</span></span>|<span data-ttu-id="37d10-142">指定只有在指定時間週期之前發生的交易才符合。</span><span class="sxs-lookup"><span data-stu-id="37d10-142">Specifies that only transactions that occurred prior to the specified time period are matched.</span></span> <span data-ttu-id="37d10-143">時間週期可以秒、分、小時或天為單位指定。</span><span class="sxs-lookup"><span data-stu-id="37d10-143">The time period can be specified in seconds, minutes, hours, or days.</span></span>|  
|<span data-ttu-id="37d10-144">**是空的**</span><span class="sxs-lookup"><span data-stu-id="37d10-144">**Is empty**</span></span>|<span data-ttu-id="37d10-145">指定只有商務資料項目不包含任何資料 (資料欄位的值為空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="37d10-145">Specifies that only transactions for which the business data item contains no data (the value of data field is NULL) are returned.</span></span>|  
|<span data-ttu-id="37d10-146">**不是空的**</span><span class="sxs-lookup"><span data-stu-id="37d10-146">**Is not empty**</span></span>|<span data-ttu-id="37d10-147">指定只有商務資料項目包含資料 (資料欄位的值不是空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="37d10-147">Specifies that only transactions for which the business data item contains data (the value of data field is not NULL) are returned.</span></span>|  
  
 <span data-ttu-id="37d10-148">下表說明數字欄位和持續時間欄位。</span><span class="sxs-lookup"><span data-stu-id="37d10-148">The following table describes the numeric fields and the duration fields.</span></span> <span data-ttu-id="37d10-149">數字欄位包含如量或貨幣數的資料。</span><span class="sxs-lookup"><span data-stu-id="37d10-149">Numeric fields contain data such as quantities or currency amounts.</span></span> <span data-ttu-id="37d10-150">持續時間欄位指定時間週期。</span><span class="sxs-lookup"><span data-stu-id="37d10-150">Duration fields specify a time period.</span></span>  
  
|<span data-ttu-id="37d10-151">運算子</span><span class="sxs-lookup"><span data-stu-id="37d10-151">Operator</span></span>|<span data-ttu-id="37d10-152">Description</span><span class="sxs-lookup"><span data-stu-id="37d10-152">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="37d10-153">**等於**</span><span class="sxs-lookup"><span data-stu-id="37d10-153">**Equals**</span></span>|<span data-ttu-id="37d10-154">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="37d10-154">Specifies an exact match.</span></span> <span data-ttu-id="37d10-155">相當於布林值的等於 (=) 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-155">Equivalent to a Boolean Equals (=) operation.</span></span>|  
|<span data-ttu-id="37d10-156">**大於**</span><span class="sxs-lookup"><span data-stu-id="37d10-156">**Greater than**</span></span>|<span data-ttu-id="37d10-157">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="37d10-157">Specifies an exact match.</span></span> <span data-ttu-id="37d10-158">相當於布林值的大於 (>) 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-158">Equivalent to a Boolean Greater Than (>) operation.</span></span>|  
|<span data-ttu-id="37d10-159">**大於或等於**</span><span class="sxs-lookup"><span data-stu-id="37d10-159">**Greater than or equal**</span></span>|<span data-ttu-id="37d10-160">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="37d10-160">Specifies an exact match.</span></span> <span data-ttu-id="37d10-161">相當於布林值的大於或等於 (≥ 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-161">Equivalent to a Boolean Greater Than or Equals (≥) operation.</span></span>|  
|<span data-ttu-id="37d10-162">**小於**</span><span class="sxs-lookup"><span data-stu-id="37d10-162">**Less than**</span></span>|<span data-ttu-id="37d10-163">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="37d10-163">Specifies an exact match.</span></span> <span data-ttu-id="37d10-164">相當於布林值的小於 (<) 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-164">Equivalent to a Boolean Less Than (<) operation.</span></span>|  
|<span data-ttu-id="37d10-165">**小於或等於**</span><span class="sxs-lookup"><span data-stu-id="37d10-165">**Less than or equal**</span></span>|<span data-ttu-id="37d10-166">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="37d10-166">Specifies an exact match.</span></span> <span data-ttu-id="37d10-167">相當於布林值的小於或等於 (≤ 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-167">Equivalent to a Less Than or Equals (≤) operation.</span></span>|  
|<span data-ttu-id="37d10-168">**不等於**</span><span class="sxs-lookup"><span data-stu-id="37d10-168">**Not Equal**</span></span>|<span data-ttu-id="37d10-169">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="37d10-169">Specifies an exact match.</span></span> <span data-ttu-id="37d10-170">相當於布林值的不等於 (≠) 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-170">Equivalent to a Not Equals (≠) operation.</span></span>|  
|<span data-ttu-id="37d10-171">**是空的**</span><span class="sxs-lookup"><span data-stu-id="37d10-171">**Is empty**</span></span>|<span data-ttu-id="37d10-172">指定只有商務資料項目不包含任何資料 (資料欄位的值為空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="37d10-172">Specifies that only transactions for which the business data item contains no data (the value of data field is NULL) are returned.</span></span>|  
|<span data-ttu-id="37d10-173">**不是空的**</span><span class="sxs-lookup"><span data-stu-id="37d10-173">**Is not empty**</span></span>|<span data-ttu-id="37d10-174">指定只有商務資料項目包含資料 (資料欄位的值不是空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="37d10-174">Specifies that only transactions for which the business data item contains data (the value of data field is not NULL) are returned.</span></span>|  
  
 <span data-ttu-id="37d10-175">下表說明文字欄位。</span><span class="sxs-lookup"><span data-stu-id="37d10-175">The following table describes the text fields.</span></span>  
  
|<span data-ttu-id="37d10-176">運算子</span><span class="sxs-lookup"><span data-stu-id="37d10-176">Operator</span></span>|<span data-ttu-id="37d10-177">Description</span><span class="sxs-lookup"><span data-stu-id="37d10-177">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="37d10-178">**完全**</span><span class="sxs-lookup"><span data-stu-id="37d10-178">**Is Exactly**</span></span>|<span data-ttu-id="37d10-179">指定完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="37d10-179">Specifies an exact match.</span></span> <span data-ttu-id="37d10-180">相當於布林值的等於 (=) 運算。</span><span class="sxs-lookup"><span data-stu-id="37d10-180">Equivalent to a Boolean Equals (=) operation.</span></span>|  
|<span data-ttu-id="37d10-181">**包含**</span><span class="sxs-lookup"><span data-stu-id="37d10-181">**Contains**</span></span>|<span data-ttu-id="37d10-182">指定商務資料項目中的文字包含指定的值。</span><span class="sxs-lookup"><span data-stu-id="37d10-182">Specifies that the text in the business data item contains the specified value.</span></span> <span data-ttu-id="37d10-183">這可讓您在資料上執行部分相符。</span><span class="sxs-lookup"><span data-stu-id="37d10-183">This allows you to do partial matches on the data.</span></span>|  
|<span data-ttu-id="37d10-184">**不包含**</span><span class="sxs-lookup"><span data-stu-id="37d10-184">**Does not contain**</span></span>|<span data-ttu-id="37d10-185">指定商務資料項目中的文字不包含指定的值。</span><span class="sxs-lookup"><span data-stu-id="37d10-185">Specifies that the text in the business data item does not contain the specified value.</span></span>|  
|<span data-ttu-id="37d10-186">**是空的**</span><span class="sxs-lookup"><span data-stu-id="37d10-186">**Is empty**</span></span>|<span data-ttu-id="37d10-187">指定只有商務資料項目不包含任何資料 (資料欄位的值為空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="37d10-187">Specifies that only transactions for which the business data item contains no data (the value of data field is NULL) are returned.</span></span>|  
|<span data-ttu-id="37d10-188">**不是空的**</span><span class="sxs-lookup"><span data-stu-id="37d10-188">**Is not empty**</span></span>|<span data-ttu-id="37d10-189">指定只有商務資料項目包含資料 (資料欄位的值不是空值) 的交易才會傳回。</span><span class="sxs-lookup"><span data-stu-id="37d10-189">Specifies that only transactions for which the business data item contains data (the value of data field is not NULL) are returned.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="37d10-190">本節內容</span><span class="sxs-lookup"><span data-stu-id="37d10-190">In This Section</span></span>  
  
-   [<span data-ttu-id="37d10-191">如何在活動搜尋中建立查詢</span><span class="sxs-lookup"><span data-stu-id="37d10-191">How to Create a Query in Activity Search</span></span>](../core/how-to-create-a-query-in-activity-search.md)  
  
-   [<span data-ttu-id="37d10-192">如何設定警示</span><span class="sxs-lookup"><span data-stu-id="37d10-192">How to Set an Alert</span></span>](../core/how-to-set-an-alert.md)  
  
-   [<span data-ttu-id="37d10-193">如何檢視活動搜尋的結果</span><span class="sxs-lookup"><span data-stu-id="37d10-193">How to View the Results of an Activity Search</span></span>](../core/how-to-view-the-results-of-an-activity-search.md)  
  
## <a name="see-also"></a><span data-ttu-id="37d10-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37d10-194">See Also</span></span>  
 [<span data-ttu-id="37d10-195">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="37d10-195">BAM Portal</span></span>](../core/bam-portal.md)