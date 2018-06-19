---
title: 在 BAM 中定義資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], dimensions
- monitoring business activities [BAM], BAM Activity Wizard
- monitoring business activities [BAM], time intervals
- aggregations [BAM], measurements
- monitoring business activities [BAM], views
- monitoring business activities [BAM], aggregations
- Excel add-in [BAM], collecting data
- aggregations [BAM], scheduling
- monitoring business activities [BAM], milestone groups
- aggregations [BAM], real-time data
ms.assetid: 501a1c08-3979-4a99-94d9-0d1b5ec4266b
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6acbc0ea1d80ec129d691d6c54b6eefd626d0e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242934"
---
# <a name="defining-data-in-bam"></a><span data-ttu-id="ed42d-102">在 BAM 中定義資料</span><span class="sxs-lookup"><span data-stu-id="ed42d-102">Defining Data in BAM</span></span>
<span data-ttu-id="ed42d-103">您可以使用 BAM Excel 增益集來定義想要 BAM 收集的資料，並定義資料共用的方式。</span><span class="sxs-lookup"><span data-stu-id="ed42d-103">You use the BAM Excel Add-in to define the data you want BAM to collect, and define the way in which the data will be shared.</span></span> <span data-ttu-id="ed42d-104">您可以使用 BAM 活動來定義資料，也可以使用 BAM 檢視來定義其他使用者可查看的資料。</span><span class="sxs-lookup"><span data-stu-id="ed42d-104">You use BAM activities to define the data, and you use BAM views to define the data that other users can see.</span></span>  
  
## <a name="activities"></a><span data-ttu-id="ed42d-105">活動</span><span class="sxs-lookup"><span data-stu-id="ed42d-105">Activities</span></span>  
 <span data-ttu-id="ed42d-106">您可以建立 BAM 活動以定義有關您要透過 BAM 監控的商務程序的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ed42d-106">You create a BAM activity to define information about a business process that you want to monitor with BAM.</span></span> <span data-ttu-id="ed42d-107">BAM 活動代表企業中的特定商務程序，如處理訂單或交運產品。</span><span class="sxs-lookup"><span data-stu-id="ed42d-107">A BAM activity represents a specific business process in the business, such as handling purchase orders or shipping a product.</span></span> <span data-ttu-id="ed42d-108">商務程序有一組已定義的里程碑和商務資料。</span><span class="sxs-lookup"><span data-stu-id="ed42d-108">A business process has a defined set of milestones and business data.</span></span> <span data-ttu-id="ed42d-109">例如，訂單活動可能有「已核准」、「已拒絕」和「已傳遞」等里程碑，以及「客戶名稱」和「產品」等商務資料。</span><span class="sxs-lookup"><span data-stu-id="ed42d-109">For example, a purchase order process might have milestones such as Approved, Denied, and Delivered along with business data like Customer Name and Product.</span></span>  
  
 <span data-ttu-id="ed42d-110">BAM 活動的目的是要向資訊工作者顯示關於程序的歷程記錄 (里程碑) 和資料。</span><span class="sxs-lookup"><span data-stu-id="ed42d-110">The intention of a BAM activity is to show the history (milestones) and data about a process to information workers.</span></span> <span data-ttu-id="ed42d-111">BAM 活動是高階的抽象概念，與 BizTalk Server 的實際實作無關。</span><span class="sxs-lookup"><span data-stu-id="ed42d-111">BAM activities are high-level abstractions that are independent of the actual implementation of BizTalk Server.</span></span> <span data-ttu-id="ed42d-112">BAM 的概念概觀，請參閱 < 商務活動監控 > 主題，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="ed42d-112">For a conceptual overview of BAM, see the topic "Business Activity Monitoring" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
 <span data-ttu-id="ed42d-113">您可以使用 「 BAM 活動精靈 」 來定義 BAM 活動包含至少一個活動項目。</span><span class="sxs-lookup"><span data-stu-id="ed42d-113">You use the BAM Activity Wizard to define BAM activities that contain at least one activity item.</span></span> <span data-ttu-id="ed42d-114">您可以將活動中的相關活動項目組成群組，並使用活動項目來描述您要在商務程序中提供的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ed42d-114">You group related activity items in an activity, and you use activity items to describe the type of data you want to make available from a business process.</span></span>  
  
 <span data-ttu-id="ed42d-115">下表說明 BAM 提供的活動項目類型。</span><span class="sxs-lookup"><span data-stu-id="ed42d-115">The following table describes the types of activity items BAM provides.</span></span>  
  
|<span data-ttu-id="ed42d-116">項目類型</span><span class="sxs-lookup"><span data-stu-id="ed42d-116">Item type</span></span>|<span data-ttu-id="ed42d-117">Description</span><span class="sxs-lookup"><span data-stu-id="ed42d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed42d-118">商務里程碑</span><span class="sxs-lookup"><span data-stu-id="ed42d-118">Business Milestone</span></span>|<span data-ttu-id="ed42d-119">日期/時間值。</span><span class="sxs-lookup"><span data-stu-id="ed42d-119">A date/time value.</span></span> <span data-ttu-id="ed42d-120">例如，訂單的核准日期。</span><span class="sxs-lookup"><span data-stu-id="ed42d-120">For example, an approval date for a purchase order.</span></span>|  
|<span data-ttu-id="ed42d-121">商務資料 - TEXT</span><span class="sxs-lookup"><span data-stu-id="ed42d-121">Business Data - Text</span></span>|<span data-ttu-id="ed42d-122">包含任何英數字元的字串。</span><span class="sxs-lookup"><span data-stu-id="ed42d-122">A string containing any alphanumeric characters.</span></span> <span data-ttu-id="ed42d-123">例如，送貨至： 城市、 縣/市和郵遞區號的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed42d-123">For example, Ship to: City, State/Province and Zip/Postal code.</span></span>|  
|<span data-ttu-id="ed42d-124">商務資料 - INTEGER</span><span class="sxs-lookup"><span data-stu-id="ed42d-124">Business Data - Integer</span></span>|<span data-ttu-id="ed42d-125">整數值。</span><span class="sxs-lookup"><span data-stu-id="ed42d-125">A whole number value.</span></span> <span data-ttu-id="ed42d-126">例如，總訂購數。</span><span class="sxs-lookup"><span data-stu-id="ed42d-126">For example, the total number of purchases.</span></span>|  
|<span data-ttu-id="ed42d-127">商務資料 - FLOAT</span><span class="sxs-lookup"><span data-stu-id="ed42d-127">Business Data - Float</span></span>|<span data-ttu-id="ed42d-128">十進位值。</span><span class="sxs-lookup"><span data-stu-id="ed42d-128">A decimal value.</span></span> <span data-ttu-id="ed42d-129">例如 PO 的總金額。</span><span class="sxs-lookup"><span data-stu-id="ed42d-129">For example the total dollar amount of the PO.</span></span>|  
  
 <span data-ttu-id="ed42d-130">例如，在訂單活動中，您可能建立下列表格中的活動項目。</span><span class="sxs-lookup"><span data-stu-id="ed42d-130">For example, in a purchase order activity, you might create the activity items in the following table.</span></span>  
  
|<span data-ttu-id="ed42d-131">活動項目</span><span class="sxs-lookup"><span data-stu-id="ed42d-131">Activity item</span></span>|<span data-ttu-id="ed42d-132">項目類型</span><span class="sxs-lookup"><span data-stu-id="ed42d-132">Item type</span></span>|  
|-------------------|---------------|  
|<span data-ttu-id="ed42d-133">產品</span><span class="sxs-lookup"><span data-stu-id="ed42d-133">Product</span></span>|<span data-ttu-id="ed42d-134">商務資料 - TEXT</span><span class="sxs-lookup"><span data-stu-id="ed42d-134">Business Data — Text</span></span>|  
|<span data-ttu-id="ed42d-135">City</span><span class="sxs-lookup"><span data-stu-id="ed42d-135">City</span></span>|<span data-ttu-id="ed42d-136">商務資料 - TEXT</span><span class="sxs-lookup"><span data-stu-id="ed42d-136">Business Data — Text</span></span>|  
|<span data-ttu-id="ed42d-137">State</span><span class="sxs-lookup"><span data-stu-id="ed42d-137">State</span></span>|<span data-ttu-id="ed42d-138">商務資料 - TEXT</span><span class="sxs-lookup"><span data-stu-id="ed42d-138">Business Data — Text</span></span>|  
|<span data-ttu-id="ed42d-139">Amount</span><span class="sxs-lookup"><span data-stu-id="ed42d-139">Amount</span></span>|<span data-ttu-id="ed42d-140">商務資料 - FLOAT</span><span class="sxs-lookup"><span data-stu-id="ed42d-140">Business Data — Float</span></span>|  
|<span data-ttu-id="ed42d-141">Quantity</span><span class="sxs-lookup"><span data-stu-id="ed42d-141">Quantity</span></span>|<span data-ttu-id="ed42d-142">商務資料 - INTEGER</span><span class="sxs-lookup"><span data-stu-id="ed42d-142">Business Data — Integer</span></span>|  
|<span data-ttu-id="ed42d-143">已核准</span><span class="sxs-lookup"><span data-stu-id="ed42d-143">Approved</span></span>|<span data-ttu-id="ed42d-144">商務里程碑</span><span class="sxs-lookup"><span data-stu-id="ed42d-144">Business Milestone</span></span>|  
|<span data-ttu-id="ed42d-145">已傳遞</span><span class="sxs-lookup"><span data-stu-id="ed42d-145">Delivered</span></span>|<span data-ttu-id="ed42d-146">商務里程碑</span><span class="sxs-lookup"><span data-stu-id="ed42d-146">Business Milestone</span></span>|  
|<span data-ttu-id="ed42d-147">拒絕</span><span class="sxs-lookup"><span data-stu-id="ed42d-147">Denied</span></span>|<span data-ttu-id="ed42d-148">商務里程碑</span><span class="sxs-lookup"><span data-stu-id="ed42d-148">Business Milestone</span></span>|  
|<span data-ttu-id="ed42d-149">已接收</span><span class="sxs-lookup"><span data-stu-id="ed42d-149">Received</span></span>|<span data-ttu-id="ed42d-150">商務里程碑</span><span class="sxs-lookup"><span data-stu-id="ed42d-150">Business Milestone</span></span>|  
  
 <span data-ttu-id="ed42d-151">請注意，「金額」為浮點數，因為它可能會是小數值。</span><span class="sxs-lookup"><span data-stu-id="ed42d-151">Note that Amount is a float because it may be a decimal value.</span></span> <span data-ttu-id="ed42d-152">「數量」為整數，因為它在此例中必定是整數。</span><span class="sxs-lookup"><span data-stu-id="ed42d-152">Quantity is an integer because it will always be a whole number in this example.</span></span> <span data-ttu-id="ed42d-153">「已核准」、「已傳遞」、「已拒絕」和「已接收」是訂單程序中的所有里程碑。</span><span class="sxs-lookup"><span data-stu-id="ed42d-153">Approved, Delivered, Denied, and Received are all milestones in the purchase order process.</span></span>  
  
## <a name="views"></a><span data-ttu-id="ed42d-154">檢視</span><span class="sxs-lookup"><span data-stu-id="ed42d-154">Views</span></span>  
 <span data-ttu-id="ed42d-155">您可以建立檢視，向使用者公開活動中的資料。</span><span class="sxs-lookup"><span data-stu-id="ed42d-155">You create views to expose data from an activity to users.</span></span> <span data-ttu-id="ed42d-156">當您根據訂單活動建立檢視時，您會定義活動項目背後的資料。</span><span class="sxs-lookup"><span data-stu-id="ed42d-156">When you create a view based on the purchase order activity, you define the data behind the activity items.</span></span> <span data-ttu-id="ed42d-157">您可以將 BAM 中的檢視資料定義為維度、量值、持續時間、里程碑群組和進度維度。</span><span class="sxs-lookup"><span data-stu-id="ed42d-157">You define view data in BAM as dimensions, measures, durations, milestone groups, and progress dimensions.</span></span>  
  
 <span data-ttu-id="ed42d-158">檢視包含一或多個檢視項目。</span><span class="sxs-lookup"><span data-stu-id="ed42d-158">A view contains one or more view items.</span></span> <span data-ttu-id="ed42d-159">您可以建立下列類型的檢視項目：</span><span class="sxs-lookup"><span data-stu-id="ed42d-159">You can create the following types of view items:</span></span>  
  
-   <span data-ttu-id="ed42d-160">持續時間</span><span class="sxs-lookup"><span data-stu-id="ed42d-160">Durations</span></span>  
  
-   <span data-ttu-id="ed42d-161">里程碑群組</span><span class="sxs-lookup"><span data-stu-id="ed42d-161">Milestone groups</span></span>  
  
-   <span data-ttu-id="ed42d-162">Aggregations</span><span class="sxs-lookup"><span data-stu-id="ed42d-162">Aggregations</span></span>  
  
### <a name="durations"></a><span data-ttu-id="ed42d-163">持續時間</span><span class="sxs-lookup"><span data-stu-id="ed42d-163">Durations</span></span>  
 <span data-ttu-id="ed42d-164">持續時間是時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ed42d-164">Durations are time intervals.</span></span> <span data-ttu-id="ed42d-165">持續時間可以從定義時間間隔之開始與結束的里程碑角度來描述。</span><span class="sxs-lookup"><span data-stu-id="ed42d-165">Durations are described in terms of the milestones that define the start and end of time intervals.</span></span> <span data-ttu-id="ed42d-166">下表顯示您可以從上表所列里程碑中設定的持續時間。</span><span class="sxs-lookup"><span data-stu-id="ed42d-166">The following table shows the durations you can make from the milestones listed in the previous table.</span></span>  
  
|<span data-ttu-id="ed42d-167">有效期間</span><span class="sxs-lookup"><span data-stu-id="ed42d-167">Duration</span></span>|<span data-ttu-id="ed42d-168">開始里程碑</span><span class="sxs-lookup"><span data-stu-id="ed42d-168">Start milestone</span></span>|<span data-ttu-id="ed42d-169">結束里程碑</span><span class="sxs-lookup"><span data-stu-id="ed42d-169">End milestone</span></span>|  
|--------------|---------------------|-------------------|  
|<span data-ttu-id="ed42d-170">1</span><span class="sxs-lookup"><span data-stu-id="ed42d-170">1</span></span>|<span data-ttu-id="ed42d-171">已接收</span><span class="sxs-lookup"><span data-stu-id="ed42d-171">Received</span></span>|<span data-ttu-id="ed42d-172">已核准</span><span class="sxs-lookup"><span data-stu-id="ed42d-172">Approved</span></span>|  
|<span data-ttu-id="ed42d-173">2</span><span class="sxs-lookup"><span data-stu-id="ed42d-173">2</span></span>|<span data-ttu-id="ed42d-174">已接收</span><span class="sxs-lookup"><span data-stu-id="ed42d-174">Received</span></span>|<span data-ttu-id="ed42d-175">已傳遞</span><span class="sxs-lookup"><span data-stu-id="ed42d-175">Delivered</span></span>|  
|<span data-ttu-id="ed42d-176">3</span><span class="sxs-lookup"><span data-stu-id="ed42d-176">3</span></span>|<span data-ttu-id="ed42d-177">已接收</span><span class="sxs-lookup"><span data-stu-id="ed42d-177">Received</span></span>|<span data-ttu-id="ed42d-178">拒絕</span><span class="sxs-lookup"><span data-stu-id="ed42d-178">Denied</span></span>|  
|<span data-ttu-id="ed42d-179">4</span><span class="sxs-lookup"><span data-stu-id="ed42d-179">4</span></span>|<span data-ttu-id="ed42d-180">已核准</span><span class="sxs-lookup"><span data-stu-id="ed42d-180">Approved</span></span>|<span data-ttu-id="ed42d-181">已傳遞</span><span class="sxs-lookup"><span data-stu-id="ed42d-181">Delivered</span></span>|  
  
 <span data-ttu-id="ed42d-182">在此表格中，您可以看到第一個持續時間 (持續時間 1) 是起始於 BizTalk Server 收到訂單時，而結束於訂單獲得核准時的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ed42d-182">In this table, you can see that the first duration (Duration 1) is the time interval that starts when a purchase order is received by BizTalk Server, and ends when the purchase order is approved.</span></span>  
  
### <a name="milestone-groups"></a><span data-ttu-id="ed42d-183">里程碑群組</span><span class="sxs-lookup"><span data-stu-id="ed42d-183">Milestone groups</span></span>  
 <span data-ttu-id="ed42d-184">您可以建立里程碑群組，將一組里程碑視為單一實體；例如，程序的開始和結束里程碑，可以建立單一里程碑來代表程序的全程期間。</span><span class="sxs-lookup"><span data-stu-id="ed42d-184">You create milestone groups to treat a set of milestones as a single entity, for example, the beginning and ending milestones for a process, which creates a single milestone to represent the entire length of the process.</span></span>  
  
### <a name="aggregations"></a><span data-ttu-id="ed42d-185">Aggregations</span><span class="sxs-lookup"><span data-stu-id="ed42d-185">Aggregations</span></span>  
 <span data-ttu-id="ed42d-186">您可以使用彙總來改善從資料庫重新整理資料的回應時間。</span><span class="sxs-lookup"><span data-stu-id="ed42d-186">You use aggregations to improve the response time for refreshing data from the database.</span></span> <span data-ttu-id="ed42d-187">Excel 將彙總定義為資料的預先計算摘要，可在問題提出之前先備妥答案，以改善查詢回應時間。</span><span class="sxs-lookup"><span data-stu-id="ed42d-187">Excel defines aggregations as pre-calculated summaries of data that improve query response time by having the answers ready before the questions are asked.</span></span> <span data-ttu-id="ed42d-188">例如，當資料倉儲事實資料表包含數以萬計的資料列時，如果要查詢兩個特定產品的出貨排程，其必須掃描事實資料表進行計算，這可能需要花很長時間才能得到結果。</span><span class="sxs-lookup"><span data-stu-id="ed42d-188">For example, when a data warehouse fact table contains hundreds of thousands of rows, a query requesting the shipping schedules for two particular products can take a long time to answer if the fact table has to be scanned to compute the answer.</span></span> <span data-ttu-id="ed42d-189">但是，如果已經預先計算好要回應的摘要資料，就幾乎可以立即做出回應。</span><span class="sxs-lookup"><span data-stu-id="ed42d-189">However, the response can be almost immediate if the summarization data to answer this query has been pre-calculated.</span></span>  
  
 <span data-ttu-id="ed42d-190">下圖是預先計算好彙總資料的範例。</span><span class="sxs-lookup"><span data-stu-id="ed42d-190">The following figure displays an example of pre-calculated aggregation data.</span></span>  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
  
 <span data-ttu-id="ed42d-191">圖中摘要了在兩個月的期間出貨至特定地點之各項產品的數量。</span><span class="sxs-lookup"><span data-stu-id="ed42d-191">The figure summarizes the numbers of each product shipped to specific locations over a two-month time period.</span></span> <span data-ttu-id="ed42d-192">Excel 通常會將此資料定義為量值。</span><span class="sxs-lookup"><span data-stu-id="ed42d-192">Excel typically defines this data as measure.</span></span> <span data-ttu-id="ed42d-193">而用於篩選與分類的資料，Excel 則定義為維度。</span><span class="sxs-lookup"><span data-stu-id="ed42d-193">The data used for filtering and categorization, Excel defines as dimension.</span></span>  
  
 <span data-ttu-id="ed42d-194">您可以在 BAM 活頁簿中定義兩個彙總類型：</span><span class="sxs-lookup"><span data-stu-id="ed42d-194">You can define two types of aggregations in the BAM workbook:</span></span>  
  
-   <span data-ttu-id="ed42d-195">即時彙總</span><span class="sxs-lookup"><span data-stu-id="ed42d-195">Real-time aggregations</span></span>  
  
-   <span data-ttu-id="ed42d-196">排程彙總</span><span class="sxs-lookup"><span data-stu-id="ed42d-196">Scheduled aggregations</span></span>  
  
### <a name="real-time-aggregations"></a><span data-ttu-id="ed42d-197">即時彙總</span><span class="sxs-lookup"><span data-stu-id="ed42d-197">Real-time aggregations</span></span>  
 <span data-ttu-id="ed42d-198">即時彙總 (RTA) 允許您查看商務程序的目前狀態，並且讓您更容易找出程序的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="ed42d-198">Real-time aggregations (RTA) allow you to see the current state of the business process and to easily identify process bottlenecks.</span></span>  
  
 <span data-ttu-id="ed42d-199">BAM 資料會顯示在樞紐分析表中。</span><span class="sxs-lookup"><span data-stu-id="ed42d-199">BAM data is displayed in a pivot table.</span></span> <span data-ttu-id="ed42d-200">您可以為 RTA 或排程彙總定義 BAM 樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="ed42d-200">You can define a BAM pivot table as an RTA or a scheduled aggregation.</span></span> <span data-ttu-id="ed42d-201">RTA 將提供您資料的最新檢視；例如，特定 PO 在出貨程序中的情況。</span><span class="sxs-lookup"><span data-stu-id="ed42d-201">An RTA gives you an up-to-the-minute view of your data, for example, where a particular PO is in the shipping process.</span></span> <span data-ttu-id="ed42d-202">您可以重新整理畫面來更新全天的資料檢視。</span><span class="sxs-lookup"><span data-stu-id="ed42d-202">You can refresh your screen to update the view of the data throughout the day.</span></span>  
  
 <span data-ttu-id="ed42d-203">在某些情況下，多維度彙總的特定配量有時間緊迫性，因此必須可即時取得。</span><span class="sxs-lookup"><span data-stu-id="ed42d-203">In some cases, specific slices of the multidimensional aggregations are so time-sensitive that you want them to be available in real time.</span></span> <span data-ttu-id="ed42d-204">例如，您的業務是銷售容易腐壞的產品，所以希望即時取得各個出貨階段的產品數量彙總。</span><span class="sxs-lookup"><span data-stu-id="ed42d-204">For example, your business is selling perishable products and you want the aggregation of product quantity in different stages of delivery to be available in real time.</span></span> <span data-ttu-id="ed42d-205">同時，您也有其他想要看到的彙總，如典型客戶的年齡彙總，但是這只有在月底進行商業智慧分析時才需要。</span><span class="sxs-lookup"><span data-stu-id="ed42d-205">At the same time, you want other aggregations such as the age of your typical customers, but only at the end of the month for business intelligence analysis.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed42d-206">請勿定義多個使用相同 BAM 活動的 RTA。</span><span class="sxs-lookup"><span data-stu-id="ed42d-206">Do not define multiple RTAs that use the same BAM activity.</span></span> <span data-ttu-id="ed42d-207">若是這麼做，當您封存 BAM 資料時，RTA 資料將是錯誤的資料。</span><span class="sxs-lookup"><span data-stu-id="ed42d-207">If you do so, the RTA data will be incorrect when you archive the BAM data.</span></span>  
  
 <span data-ttu-id="ed42d-208">如需有關瀏覽多維度資料的詳細資訊，請參閱「Excel 說明」中的＜樞紐分析表＞主題。</span><span class="sxs-lookup"><span data-stu-id="ed42d-208">For information about browsing multidimensional data, see the PivotTable topic in Excel Help.</span></span>  
  
### <a name="scheduled-aggregations"></a><span data-ttu-id="ed42d-209">排程彙總</span><span class="sxs-lookup"><span data-stu-id="ed42d-209">Scheduled aggregations</span></span>  
 <span data-ttu-id="ed42d-210">依照預設，所有的 BAM 彙總都是排程彙總。</span><span class="sxs-lookup"><span data-stu-id="ed42d-210">All BAM aggregations are scheduled aggregations by default.</span></span> <span data-ttu-id="ed42d-211">排程彙總代表特定時間的商務快照集；例如，今日上午出貨的摘要。</span><span class="sxs-lookup"><span data-stu-id="ed42d-211">A scheduled aggregation represents a snapshot of the business at a specific time, for example, a summary of this morning's shipments.</span></span> <span data-ttu-id="ed42d-212">請向資料庫管理員詢問您的彙總是在何時處理的，然後您就可以查閱歷史資料。</span><span class="sxs-lookup"><span data-stu-id="ed42d-212">Ask your database administrator when your aggregations are processed, and then you can look at the historical data.</span></span>  
  
### <a name="dimensions-and-measures"></a><span data-ttu-id="ed42d-213">維度和量值</span><span class="sxs-lookup"><span data-stu-id="ed42d-213">Dimensions and Measures</span></span>  
 <span data-ttu-id="ed42d-214">您可以使用維度和量值來建立資料彙總：</span><span class="sxs-lookup"><span data-stu-id="ed42d-214">You use dimensions and measures to create data aggregations:</span></span>  
  
-   <span data-ttu-id="ed42d-215">維度可以描述事實。</span><span class="sxs-lookup"><span data-stu-id="ed42d-215">Dimensions describe a fact.</span></span>  
  
-   <span data-ttu-id="ed42d-216">量值為事實值。</span><span class="sxs-lookup"><span data-stu-id="ed42d-216">Measures are fact values.</span></span>  
  
 <span data-ttu-id="ed42d-217">例如，事實可能是 「 3 輛紅色汽車 」 清查中。</span><span class="sxs-lookup"><span data-stu-id="ed42d-217">For example, a fact could be “3 red cars” in inventory.</span></span> <span data-ttu-id="ed42d-218">產品的描述: 「 汽車 」 和 「 紅色 」 是維度。</span><span class="sxs-lookup"><span data-stu-id="ed42d-218">The description of the product: "car" and "red" are dimensions.</span></span> <span data-ttu-id="ed42d-219">而「3」這個事實值就是量值。</span><span class="sxs-lookup"><span data-stu-id="ed42d-219">The value of the fact "3" is a measure.</span></span> <span data-ttu-id="ed42d-220">如果事實中包含每輛汽車的價格，則汽車價格是維度，而存貨中的汽車平均價格就是量值。</span><span class="sxs-lookup"><span data-stu-id="ed42d-220">If the price of each car is included in the fact, the car price is a dimension, but the average price of cars in inventory is a measure.</span></span> <span data-ttu-id="ed42d-221">《Microsoft SQL Server 線上叢書》將量值描述為「可供彙總和分析的核心值」(The central values that are aggregated and analyzed)。</span><span class="sxs-lookup"><span data-stu-id="ed42d-221">Microsoft SQL Server Books Online describes a measure as "the central values that are aggregated and analyzed."</span></span> <span data-ttu-id="ed42d-222">換言之，如果您能夠加以計數、平均或執行其他數學函式來取得它，那麼它就是一個量值。</span><span class="sxs-lookup"><span data-stu-id="ed42d-222">In other words, if you can count it, average it, or otherwise perform mathematical functions to get it, it is a measure.</span></span>  
  
 <span data-ttu-id="ed42d-223">您可以建立下列維度類型：</span><span class="sxs-lookup"><span data-stu-id="ed42d-223">You can create the following types of dimensions:</span></span>  
  
-   <span data-ttu-id="ed42d-224">進度維度</span><span class="sxs-lookup"><span data-stu-id="ed42d-224">Progress dimension</span></span>  
  
-   <span data-ttu-id="ed42d-225">資料維度</span><span class="sxs-lookup"><span data-stu-id="ed42d-225">Data dimension</span></span>  
  
-   <span data-ttu-id="ed42d-226">時間維度</span><span class="sxs-lookup"><span data-stu-id="ed42d-226">Time dimension</span></span>  
  
-   <span data-ttu-id="ed42d-227">數字範圍維度</span><span class="sxs-lookup"><span data-stu-id="ed42d-227">Numeric range dimension</span></span>  
  
## <a name="progress-dimensions"></a><span data-ttu-id="ed42d-228">進度維度</span><span class="sxs-lookup"><span data-stu-id="ed42d-228">Progress dimensions</span></span>  
 <span data-ttu-id="ed42d-229">BAM 引進新的維度類型： 進度維度。</span><span class="sxs-lookup"><span data-stu-id="ed42d-229">BAM introduces a new type of dimension: the progress dimension.</span></span> <span data-ttu-id="ed42d-230">您可以建立進度維度來建立有關仍在處理中活動之進度的彙總。</span><span class="sxs-lookup"><span data-stu-id="ed42d-230">You create progress dimensions to create aggregations that relate to the progress of activities still in process.</span></span>  
  
 <span data-ttu-id="ed42d-231">例如，請考慮購買的商務程序，您在何處接收 1,000 張 「 訂單。</span><span class="sxs-lookup"><span data-stu-id="ed42d-231">For example, consider a purchasing business process where you receive 1,000 purchase orders.</span></span> <span data-ttu-id="ed42d-232">您可以在資料列使用進度維度來建立下列資料表。</span><span class="sxs-lookup"><span data-stu-id="ed42d-232">You can use the progress dimension on rows to create the following table.</span></span>  
  
|<span data-ttu-id="ed42d-233">OrderProgress_Level1</span><span class="sxs-lookup"><span data-stu-id="ed42d-233">OrderProgress_Level1</span></span>|<span data-ttu-id="ed42d-234">Count</span><span class="sxs-lookup"><span data-stu-id="ed42d-234">Count</span></span>|  
|---------------------------|-----------|  
|<span data-ttu-id="ed42d-235">已接收</span><span class="sxs-lookup"><span data-stu-id="ed42d-235">Received</span></span>|<span data-ttu-id="ed42d-236">1000</span><span class="sxs-lookup"><span data-stu-id="ed42d-236">1000</span></span>|  
  
 <span data-ttu-id="ed42d-237">您可以接著開啟「已接收」程序，進一步檢視有關活動進度的詳細資料，例如：</span><span class="sxs-lookup"><span data-stu-id="ed42d-237">You can then open the Received process to view further details about the progress of the activities, such as:</span></span>  
  
|||<span data-ttu-id="ed42d-238">Count</span><span class="sxs-lookup"><span data-stu-id="ed42d-238">Count</span></span>|  
|------|------|-----------|  
|<span data-ttu-id="ed42d-239">已接收</span><span class="sxs-lookup"><span data-stu-id="ed42d-239">Received</span></span>|<span data-ttu-id="ed42d-240">評估中</span><span class="sxs-lookup"><span data-stu-id="ed42d-240">Evaluating</span></span>|<span data-ttu-id="ed42d-241">300</span><span class="sxs-lookup"><span data-stu-id="ed42d-241">300</span></span>|  
||<span data-ttu-id="ed42d-242">已核准</span><span class="sxs-lookup"><span data-stu-id="ed42d-242">Approved</span></span>|<span data-ttu-id="ed42d-243">500</span><span class="sxs-lookup"><span data-stu-id="ed42d-243">500</span></span>|  
||<span data-ttu-id="ed42d-244">拒絕</span><span class="sxs-lookup"><span data-stu-id="ed42d-244">Denied</span></span>|<span data-ttu-id="ed42d-245">200</span><span class="sxs-lookup"><span data-stu-id="ed42d-245">200</span></span>|  
  
 <span data-ttu-id="ed42d-246">這表示您收到的 1000 張訂單中，500 張已核准、200 張被拒絕，目前還有 300 張正在評估中。</span><span class="sxs-lookup"><span data-stu-id="ed42d-246">This means that from the 1000 purchase orders you received, 500 were approved, 200 were denied, and 300 are currently being evaluated.</span></span>  
  
 <span data-ttu-id="ed42d-247">「已接收」、「已核准」和「已拒絕」代表里程碑。</span><span class="sxs-lookup"><span data-stu-id="ed42d-247">Received, Approved, and Denied represent milestones.</span></span> <span data-ttu-id="ed42d-248">[計數] 資料行中的對應數字顯示有多少訂單已經通過這些里程碑。</span><span class="sxs-lookup"><span data-stu-id="ed42d-248">The corresponding numbers in the Count column show how many orders have passed through these milestones.</span></span> <span data-ttu-id="ed42d-249">「評估中」是指訂單通過「已接收」，但還未到達「已核准」或「已拒絕」里程碑時的階段。</span><span class="sxs-lookup"><span data-stu-id="ed42d-249">Evaluating is a stage that the orders pass through between the Received and Approved or Denied milestones.</span></span>  
  
 <span data-ttu-id="ed42d-250">您可以結合任何其他維度來使用進度維度。</span><span class="sxs-lookup"><span data-stu-id="ed42d-250">You can use progress dimensions in combination with any other dimensions.</span></span> <span data-ttu-id="ed42d-251">例如，在資料列使用進度維度「訂單進度」，而在資料行使用資料維度「產品」，將會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="ed42d-251">For example, by using the progress dimension Order Progress on rows and the data dimension Product on columns, the following results occur:</span></span>  
  
|||<span data-ttu-id="ed42d-252">網球拍</span><span class="sxs-lookup"><span data-stu-id="ed42d-252">Tennis Racquets</span></span>|<span data-ttu-id="ed42d-253">足球</span><span class="sxs-lookup"><span data-stu-id="ed42d-253">Soccer Balls</span></span>|  
|------|------|---------------------|------------------|  
|<span data-ttu-id="ed42d-254">已接收</span><span class="sxs-lookup"><span data-stu-id="ed42d-254">Received</span></span>|<span data-ttu-id="ed42d-255">評估中</span><span class="sxs-lookup"><span data-stu-id="ed42d-255">Evaluating</span></span>|<span data-ttu-id="ed42d-256">250</span><span class="sxs-lookup"><span data-stu-id="ed42d-256">250</span></span>|<span data-ttu-id="ed42d-257">50</span><span class="sxs-lookup"><span data-stu-id="ed42d-257">50</span></span>|  
||<span data-ttu-id="ed42d-258">已核准</span><span class="sxs-lookup"><span data-stu-id="ed42d-258">Approved</span></span>|<span data-ttu-id="ed42d-259">200</span><span class="sxs-lookup"><span data-stu-id="ed42d-259">200</span></span>|<span data-ttu-id="ed42d-260">300</span><span class="sxs-lookup"><span data-stu-id="ed42d-260">300</span></span>|  
||<span data-ttu-id="ed42d-261">拒絕</span><span class="sxs-lookup"><span data-stu-id="ed42d-261">Denied</span></span>|<span data-ttu-id="ed42d-262">150</span><span class="sxs-lookup"><span data-stu-id="ed42d-262">150</span></span>|<span data-ttu-id="ed42d-263">50</span><span class="sxs-lookup"><span data-stu-id="ed42d-263">50</span></span>|  
  
 <span data-ttu-id="ed42d-264">「進度維度」可以為基於即時彙總 (RTA) 的圖表提供特別有用的資訊。</span><span class="sxs-lookup"><span data-stu-id="ed42d-264">Progress dimensions provide especially useful information for charts based on real-time aggregations (RTA).</span></span> <span data-ttu-id="ed42d-265">RTA 允許您查看商務程序的目前狀態，並且讓您更容易找出程序的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="ed42d-265">RTAs allow you to see the current state of the business process and to easily identify process bottlenecks.</span></span>  
  
 <span data-ttu-id="ed42d-266">訂單中的里程碑訂單進度維度可以是循序： 下一個步驟開始之前，先完成第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="ed42d-266">The milestones in a purchase order progress dimension can be sequential: the first step is completed before the next step is started.</span></span> <span data-ttu-id="ed42d-267">或者，可以使用串聯方式完成里程碑。</span><span class="sxs-lookup"><span data-stu-id="ed42d-267">Or milestones can be completed in tandem.</span></span> <span data-ttu-id="ed42d-268">循序步驟是子步驟，串聯步驟則是同層級步驟。</span><span class="sxs-lookup"><span data-stu-id="ed42d-268">Sequential steps are child steps, and tandem steps are sibling steps.</span></span> <span data-ttu-id="ed42d-269">在訂單程序中，只要一收到訂單，就會開始進行驗證。</span><span class="sxs-lookup"><span data-stu-id="ed42d-269">In the purchase order process, verification begins as soon as the purchase order is received.</span></span> <span data-ttu-id="ed42d-270">這是和「已接收」里程碑同時發生的暫時步驟，因此也和接收里程碑同在一個層級。</span><span class="sxs-lookup"><span data-stu-id="ed42d-270">It is a transitory step that occurs at the same time as the received milestone, and is therefore a sibling to the receive milestone.</span></span> <span data-ttu-id="ed42d-271">訂單只有在收到之後才會核准，因此「已核准」是「已接收」的子系。</span><span class="sxs-lookup"><span data-stu-id="ed42d-271">A purchase order is approved only after it is received — approved is a child of received.</span></span>  
  
## <a name="data-dimension"></a><span data-ttu-id="ed42d-272">資料維度</span><span class="sxs-lookup"><span data-stu-id="ed42d-272">Data dimension</span></span>  
 <span data-ttu-id="ed42d-273">您可以定義資料維度，使其在資料列或資料行上使用 BAM 活動中部分文字項目的值。</span><span class="sxs-lookup"><span data-stu-id="ed42d-273">You define a data dimension to use the value of some text items in the BAM activity on rows or columns.</span></span> <span data-ttu-id="ed42d-274">例如，名為產品的資料維度可以用來建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="ed42d-274">For example, a data dimension named Product can be used to create the following table:</span></span>  
  
|<span data-ttu-id="ed42d-275">產品</span><span class="sxs-lookup"><span data-stu-id="ed42d-275">Product</span></span>|<span data-ttu-id="ed42d-276">Count</span><span class="sxs-lookup"><span data-stu-id="ed42d-276">Count</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="ed42d-277">網球拍</span><span class="sxs-lookup"><span data-stu-id="ed42d-277">Tennis racquets</span></span>|<span data-ttu-id="ed42d-278">100</span><span class="sxs-lookup"><span data-stu-id="ed42d-278">100</span></span>|  
|<span data-ttu-id="ed42d-279">足球</span><span class="sxs-lookup"><span data-stu-id="ed42d-279">Soccer balls</span></span>|<span data-ttu-id="ed42d-280">200</span><span class="sxs-lookup"><span data-stu-id="ed42d-280">200</span></span>|  
  
 <span data-ttu-id="ed42d-281">此外，您可以在 「 BAM 檢視精靈 」 中定義多個資料維度。</span><span class="sxs-lookup"><span data-stu-id="ed42d-281">Also, you can define more than one data dimension in the BAM View Wizard.</span></span> <span data-ttu-id="ed42d-282">例如，以「省/州」和「縣/市」的層級定義名為「位置」的資料維度，可以用來建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="ed42d-282">For example, defining a data dimension named Location with levels for State and City can be used to create the following table:</span></span>  
  
|<span data-ttu-id="ed42d-283">產品</span><span class="sxs-lookup"><span data-stu-id="ed42d-283">Product</span></span>|<span data-ttu-id="ed42d-284">Los Angeles</span><span class="sxs-lookup"><span data-stu-id="ed42d-284">Los Angeles</span></span>|<span data-ttu-id="ed42d-285">San Francisco</span><span class="sxs-lookup"><span data-stu-id="ed42d-285">San Francisco</span></span>|<span data-ttu-id="ed42d-286">Seattle</span><span class="sxs-lookup"><span data-stu-id="ed42d-286">Seattle</span></span>|  
|-------------|-----------------|-------------------|-------------|  
|<span data-ttu-id="ed42d-287">網球拍</span><span class="sxs-lookup"><span data-stu-id="ed42d-287">Tennis racquets</span></span>|<span data-ttu-id="ed42d-288">50</span><span class="sxs-lookup"><span data-stu-id="ed42d-288">50</span></span>|<span data-ttu-id="ed42d-289">20</span><span class="sxs-lookup"><span data-stu-id="ed42d-289">20</span></span>|<span data-ttu-id="ed42d-290">30</span><span class="sxs-lookup"><span data-stu-id="ed42d-290">30</span></span>|  
|<span data-ttu-id="ed42d-291">足球</span><span class="sxs-lookup"><span data-stu-id="ed42d-291">Soccer balls</span></span>|<span data-ttu-id="ed42d-292">130</span><span class="sxs-lookup"><span data-stu-id="ed42d-292">130</span></span>|<span data-ttu-id="ed42d-293">50</span><span class="sxs-lookup"><span data-stu-id="ed42d-293">50</span></span>|<span data-ttu-id="ed42d-294">20</span><span class="sxs-lookup"><span data-stu-id="ed42d-294">20</span></span>|  
  
 <span data-ttu-id="ed42d-295">這個資料表使用「產品」維度做為資料列，並使用「位置」維度做為資料行。</span><span class="sxs-lookup"><span data-stu-id="ed42d-295">In this table, the Product dimension was used as the rows, and the Location dimension was used as the columns.</span></span>  
  
## <a name="time-dimension"></a><span data-ttu-id="ed42d-296">時間維度</span><span class="sxs-lookup"><span data-stu-id="ed42d-296">Time dimension</span></span>  
 <span data-ttu-id="ed42d-297">您可以建立時間維度來建立有關時間的彙總。</span><span class="sxs-lookup"><span data-stu-id="ed42d-297">You create a time dimension to create aggregations with respect to time.</span></span> <span data-ttu-id="ed42d-298">例如，時間維度可以用來建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="ed42d-298">For example, a time dimension can be used to create the following table:</span></span>  
  
|<span data-ttu-id="ed42d-299">Year</span><span class="sxs-lookup"><span data-stu-id="ed42d-299">Year</span></span>|<span data-ttu-id="ed42d-300">Month</span><span class="sxs-lookup"><span data-stu-id="ed42d-300">Month</span></span>|<span data-ttu-id="ed42d-301">Count</span><span class="sxs-lookup"><span data-stu-id="ed42d-301">Count</span></span>|  
|----------|-----------|-----------|  
|<span data-ttu-id="ed42d-302">2003</span><span class="sxs-lookup"><span data-stu-id="ed42d-302">2003</span></span>|<span data-ttu-id="ed42d-303">一月</span><span class="sxs-lookup"><span data-stu-id="ed42d-303">January</span></span>|<span data-ttu-id="ed42d-304">120</span><span class="sxs-lookup"><span data-stu-id="ed42d-304">120</span></span>|  
||<span data-ttu-id="ed42d-305">二月</span><span class="sxs-lookup"><span data-stu-id="ed42d-305">February</span></span>|<span data-ttu-id="ed42d-306">230</span><span class="sxs-lookup"><span data-stu-id="ed42d-306">230</span></span>|  
||<span data-ttu-id="ed42d-307">三月</span><span class="sxs-lookup"><span data-stu-id="ed42d-307">March</span></span>|<span data-ttu-id="ed42d-308">350</span><span class="sxs-lookup"><span data-stu-id="ed42d-308">350</span></span>|  
||<span data-ttu-id="ed42d-309">四月</span><span class="sxs-lookup"><span data-stu-id="ed42d-309">April</span></span>|<span data-ttu-id="ed42d-310">280</span><span class="sxs-lookup"><span data-stu-id="ed42d-310">280</span></span>|  
  
 <span data-ttu-id="ed42d-311">您可以將時間維度與任何其他維度結合。</span><span class="sxs-lookup"><span data-stu-id="ed42d-311">You can combine the time dimension with any other dimension.</span></span> <span data-ttu-id="ed42d-312">例如，您可以在資料列使用時間維度，而在資料行使用資料維度，以建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="ed42d-312">For example, you can use the time dimension on rows and the data dimension on columns to create the following table:</span></span>  
  
|<span data-ttu-id="ed42d-313">Month</span><span class="sxs-lookup"><span data-stu-id="ed42d-313">Month</span></span>|<span data-ttu-id="ed42d-314">網球拍</span><span class="sxs-lookup"><span data-stu-id="ed42d-314">Tennis racquets</span></span>|<span data-ttu-id="ed42d-315">足球</span><span class="sxs-lookup"><span data-stu-id="ed42d-315">Soccer balls</span></span>|  
|-----------|---------------------|------------------|  
|<span data-ttu-id="ed42d-316">一月</span><span class="sxs-lookup"><span data-stu-id="ed42d-316">January</span></span>|<span data-ttu-id="ed42d-317">50</span><span class="sxs-lookup"><span data-stu-id="ed42d-317">50</span></span>|<span data-ttu-id="ed42d-318">70</span><span class="sxs-lookup"><span data-stu-id="ed42d-318">70</span></span>|  
|<span data-ttu-id="ed42d-319">二月</span><span class="sxs-lookup"><span data-stu-id="ed42d-319">February</span></span>|<span data-ttu-id="ed42d-320">120</span><span class="sxs-lookup"><span data-stu-id="ed42d-320">120</span></span>|<span data-ttu-id="ed42d-321">110</span><span class="sxs-lookup"><span data-stu-id="ed42d-321">110</span></span>|  
|<span data-ttu-id="ed42d-322">三月</span><span class="sxs-lookup"><span data-stu-id="ed42d-322">March</span></span>|<span data-ttu-id="ed42d-323">300</span><span class="sxs-lookup"><span data-stu-id="ed42d-323">300</span></span>|<span data-ttu-id="ed42d-324">50</span><span class="sxs-lookup"><span data-stu-id="ed42d-324">50</span></span>|  
|<span data-ttu-id="ed42d-325">四月</span><span class="sxs-lookup"><span data-stu-id="ed42d-325">April</span></span>|<span data-ttu-id="ed42d-326">220</span><span class="sxs-lookup"><span data-stu-id="ed42d-326">220</span></span>|<span data-ttu-id="ed42d-327">60</span><span class="sxs-lookup"><span data-stu-id="ed42d-327">60</span></span>|  
  
## <a name="numeric-range-dimension"></a><span data-ttu-id="ed42d-328">數字範圍維度</span><span class="sxs-lookup"><span data-stu-id="ed42d-328">Numeric range dimension</span></span>  
 <span data-ttu-id="ed42d-329">您可以使用數字範圍維度，建立依據易記名稱將數字範圍分類的彙總。</span><span class="sxs-lookup"><span data-stu-id="ed42d-329">You use numeric range dimensions to create aggregations that categorize ranges of numbers by friendly names.</span></span> <span data-ttu-id="ed42d-330">例如，商務分析師可以使用下列範圍來定義名為「PO 大小」的數字範圍維度：</span><span class="sxs-lookup"><span data-stu-id="ed42d-330">For example, a business analyst can define a numeric range dimension named PO Size with the following ranges:</span></span>  
  
 <span data-ttu-id="ed42d-331">小型、 代表訂單金額介於 0 和 100</span><span class="sxs-lookup"><span data-stu-id="ed42d-331">Small, for purchase orders between 0 and $100</span></span>  
  
 <span data-ttu-id="ed42d-332">代表訂單金額介於 $100 到 $1,000 「 中 」</span><span class="sxs-lookup"><span data-stu-id="ed42d-332">Medium, for purchase orders between $100 and $1,000</span></span>  
  
 <span data-ttu-id="ed42d-333">大型的採購訂單超過 $1,000 的</span><span class="sxs-lookup"><span data-stu-id="ed42d-333">Large, for purchase orders exceeding $1,000</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed42d-334">如果訂單金額不在定義的範圍，例如，訂單金額小於 0，則 bam 來配合超出範圍的資料將會自動建立 「 超出範圍 」 資料列。</span><span class="sxs-lookup"><span data-stu-id="ed42d-334">If a purchase order amount is not in the defined ranges, for example, a purchase order amount is less than 0, then an "Out of range" row will be automatically created by BAM to accommodate the out-of-range data.</span></span>  
  
|<span data-ttu-id="ed42d-335">PO 大小</span><span class="sxs-lookup"><span data-stu-id="ed42d-335">PO Size</span></span>|<span data-ttu-id="ed42d-336">Count</span><span class="sxs-lookup"><span data-stu-id="ed42d-336">Count</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="ed42d-337">Small</span><span class="sxs-lookup"><span data-stu-id="ed42d-337">Small</span></span>|<span data-ttu-id="ed42d-338">500</span><span class="sxs-lookup"><span data-stu-id="ed42d-338">500</span></span>|  
|<span data-ttu-id="ed42d-339">中</span><span class="sxs-lookup"><span data-stu-id="ed42d-339">Medium</span></span>|<span data-ttu-id="ed42d-340">350</span><span class="sxs-lookup"><span data-stu-id="ed42d-340">350</span></span>|  
|<span data-ttu-id="ed42d-341">Large</span><span class="sxs-lookup"><span data-stu-id="ed42d-341">Large</span></span>|<span data-ttu-id="ed42d-342">225</span><span class="sxs-lookup"><span data-stu-id="ed42d-342">225</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="ed42d-343">您不可以建立兩個參考相同資料別名的數字範圍維度。</span><span class="sxs-lookup"><span data-stu-id="ed42d-343">You cannot create two numeric range dimensions that reference the same data alias.</span></span>