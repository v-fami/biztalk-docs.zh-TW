---
title: 如何設定警示 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- alerts, creating
- Query Builder [BAM portal], creating alerts
- queries [BAM], aggregations
- Query Builder [BAM portal], activity searches
- Query Builder [BAM portal], aggregation alerts
- queries [BAM], alerts
- aggregations, alerts
ms.assetid: 8745d2c6-5bc0-4d7a-8c17-361535f5c6e6
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 774fbab86c1da1389b813f621c89f38cf0aa7656
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255702"
---
# <a name="how-to-set-an-alert"></a><span data-ttu-id="6d95e-102">如何設定警示</span><span class="sxs-lookup"><span data-stu-id="6d95e-102">How to Set an Alert</span></span>
<span data-ttu-id="6d95e-103">您可以將警示附加至活動搜尋，或向下切入彙總，以設定警示。</span><span class="sxs-lookup"><span data-stu-id="6d95e-103">You can set an alert by attaching it to an activity search or drilling down through an aggregation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d95e-104">在查詢上設定警示之前，您應該先執行查詢，並評估警示循環時間是否適合所要監控的程序。</span><span class="sxs-lookup"><span data-stu-id="6d95e-104">Before setting an alert on a query, you should run the query and evaluate whether the alert cycle durations are appropriate for the process you are monitoring.</span></span> <span data-ttu-id="6d95e-105">如果警示循環時間太短，可能會出現暫時性的警示條件，而警示系統可能會遺漏該警示條件。</span><span class="sxs-lookup"><span data-stu-id="6d95e-105">If the cycle duration is too short, it is possible for an alert condition to occur in a transient manner and thus be missed by the alerting system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d95e-106">如果您按一下 [上一頁] 按鈕，在這些程序期間，您可能會收到下列訊息: 「 警告： 頁面已經過期。 」</span><span class="sxs-lookup"><span data-stu-id="6d95e-106">If you click the back button during these procedures, you may receive the following message: "Warning: page has expired."</span></span> <span data-ttu-id="6d95e-107">只要按下 F5 就可以重新顯示原本的內容</span><span class="sxs-lookup"><span data-stu-id="6d95e-107">To return to the previous content, press F5.</span></span> <span data-ttu-id="6d95e-108">(您可能必須按下 F5 數次)。</span><span class="sxs-lookup"><span data-stu-id="6d95e-108">(You may have to press F5 several times.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d95e-109">當您在檢視上建立第一個警示時，不會出現任何有關警示的資料。</span><span class="sxs-lookup"><span data-stu-id="6d95e-109">When you create the first alert on a view, there will be no data displayed for the alert.</span></span> <span data-ttu-id="6d95e-110">定義警示不會收集警示資料的時間範圍內建立了警示之前。</span><span class="sxs-lookup"><span data-stu-id="6d95e-110">Defining an alert does not collect alert data from the time frame before the alert was created.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6d95e-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="6d95e-111">Prerequisites</span></span>  
 <span data-ttu-id="6d95e-112">下列是執行本主題所述程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="6d95e-112">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
-   <span data-ttu-id="6d95e-113">您必須具備部署檢視。</span><span class="sxs-lookup"><span data-stu-id="6d95e-113">You must have a deployed view.</span></span>  
  
-   <span data-ttu-id="6d95e-114">您必須具備用於執行個體警示的活動搜尋。</span><span class="sxs-lookup"><span data-stu-id="6d95e-114">You must have an activity search for an instance alert.</span></span>  
  
-   <span data-ttu-id="6d95e-115">您必須具備用於彙總警示的已填入彙總。</span><span class="sxs-lookup"><span data-stu-id="6d95e-115">You must have a populated aggregation for an aggregation alert.</span></span>  
  
### <a name="to-set-an-alert-on-an-activity-search"></a><span data-ttu-id="6d95e-116">在活動搜尋上設定警示</span><span class="sxs-lookup"><span data-stu-id="6d95e-116">To set an alert on an activity search</span></span>  
  
1.  <span data-ttu-id="6d95e-117">在**我的檢視**框架中，按一下要展開之檢視的工作清單的檢視。</span><span class="sxs-lookup"><span data-stu-id="6d95e-117">In the **My Views** frame, click a view to expand the list of tasks for the view.</span></span>  
  
2.  <span data-ttu-id="6d95e-118">按一下**活動搜尋**展開之檢視底下的工作。</span><span class="sxs-lookup"><span data-stu-id="6d95e-118">Click the **Activity Search** task under the view you expanded.</span></span>  
  
3.  <span data-ttu-id="6d95e-119">建立或開啟活動搜尋。</span><span class="sxs-lookup"><span data-stu-id="6d95e-119">Create or open an activity search.</span></span> <span data-ttu-id="6d95e-120">如需如何執行這項操作資訊，請參閱[如何在活動搜尋中建立查詢](../core/how-to-create-a-query-in-activity-search.md)。</span><span class="sxs-lookup"><span data-stu-id="6d95e-120">For information about how to do this, see [How to Create a Query in Activity Search](../core/how-to-create-a-query-in-activity-search.md).</span></span>  
  
4.  <span data-ttu-id="6d95e-121">在 BAM 入口網站內容框架中，按一下 [**設定警示**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d95e-121">In the content frame of the BAM portal, click the **Set Alert** button.</span></span> <span data-ttu-id="6d95e-122">內容框架便會載入警示建立範本。</span><span class="sxs-lookup"><span data-stu-id="6d95e-122">The content frame will load with the alert creation template.</span></span>  
  
5.  <span data-ttu-id="6d95e-123">在**名稱**文字方塊中，輸入警示的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="6d95e-123">In the **Name** text box, type a descriptive name for the alert.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d95e-124">名稱限制為 100 個字元，且不可包含下列字元: ~ ！ @# $%^&amp;\* （); 如果您在名稱中輸入下列任何字元，則會將紅色虛線外的框表示錯誤，才能完成這個動作，您必須更正錯誤的文字欄位周圍會出現。</span><span class="sxs-lookup"><span data-stu-id="6d95e-124">Names are limited to 100 characters and cannot contain the following characters: ~!@#$%^&amp;\*();  If you enter any of these characters in a name, a dashed red border appears around the text field indicating an error that you must correct to complete the action.</span></span>  
  
6.  <span data-ttu-id="6d95e-125">如果您不想在此時間內啟用的警示，清除**啟用警示**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6d95e-125">If you do not want the alert enabled at this time, clear the **Alert Enabled** check box.</span></span>  
  
7.  <span data-ttu-id="6d95e-126">在**訊息**文字方塊中，輸入在警示觸發時傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="6d95e-126">In the **Message** text box, type the message that is delivered when the alert is triggered.</span></span>  
  
8.  <span data-ttu-id="6d95e-127">從**優先順序**下拉式清單中，選擇此警示的優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="6d95e-127">From the **Priority** drop-down list, choose the priority level for this alert.</span></span> <span data-ttu-id="6d95e-128">優先順序設定代表設定警示的問題嚴重性。</span><span class="sxs-lookup"><span data-stu-id="6d95e-128">The priority setting indicates the severity of the issue on which the alert was set.</span></span>  
  
9. <span data-ttu-id="6d95e-129">在**擁有者**文字方塊中，輸入此警示的擁有者的別名。</span><span class="sxs-lookup"><span data-stu-id="6d95e-129">In the **Owners** text box, type the aliases of the owners of this alert.</span></span> <span data-ttu-id="6d95e-130">請使用分號分隔多個使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="6d95e-130">Use semicolons between the names of multiple users.</span></span>  
  
10. <span data-ttu-id="6d95e-131">在**警示安全性**區域中，選取的核取方塊以允許其他使用者查看此警示，並訂閱。</span><span class="sxs-lookup"><span data-stu-id="6d95e-131">In the **Alert Security** area, select the check box to allow other users to see this alert and subscribe to it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d95e-132">您可以隨時將警示安全性變更成私用或公用，警示是否有訂閱者並不會影響這個動作。</span><span class="sxs-lookup"><span data-stu-id="6d95e-132">You can switch the alert security between private and public at any time; the presence of subscribers to the alert does not affect this action.</span></span> <span data-ttu-id="6d95e-133">不過，當您將警示安全性從公用切換至私用時，就應該考慮到警示是否有任何訂閱者。</span><span class="sxs-lookup"><span data-stu-id="6d95e-133">When you switch the alert security from public to private, however, you should consider whether there are any subscribers to the alert.</span></span> <span data-ttu-id="6d95e-134">如果警示有訂閱者，當警示變成私用之後，訂閱者將無法編輯他們的訂閱。</span><span class="sxs-lookup"><span data-stu-id="6d95e-134">If there are subscribers to the alert, they will have no way to edit their subscription when the alert is made private.</span></span>  
  
11. <span data-ttu-id="6d95e-135">在右上角的**警示詳細資料**區域中，按一下 [**儲存警示**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d95e-135">In the upper-right corner of the **Alert Details** area, click the **Save Alert** button.</span></span>  
  
### <a name="to-set-an-alert-on-an-aggregation"></a><span data-ttu-id="6d95e-136">在彙總上設定警示</span><span class="sxs-lookup"><span data-stu-id="6d95e-136">To set an alert on an aggregation</span></span>  
  
1.  <span data-ttu-id="6d95e-137">在**我的檢視**框架中，按一下要展開之檢視的工作清單的檢視。</span><span class="sxs-lookup"><span data-stu-id="6d95e-137">In the **My Views** frame, click a view to expand the list of tasks for the view.</span></span>  
  
2.  <span data-ttu-id="6d95e-138">按一下**彙總**中工作**我的檢視**展開之檢視底下。</span><span class="sxs-lookup"><span data-stu-id="6d95e-138">Click the **Aggregations** task in **My Views** under the view you expanded.</span></span>  
  
3.  <span data-ttu-id="6d95e-139">在 BAM 入口網站的內容框架中，使用滑鼠右鍵按一下樞紐分析表總計欄位中的儲存格。</span><span class="sxs-lookup"><span data-stu-id="6d95e-139">In the content frame of the BAM portal, right-click a cell in the totals column of the PivotTable report.</span></span> <span data-ttu-id="6d95e-140">這會開啟快顯功能表，其中列有可以在彙總總計上執行的功能。</span><span class="sxs-lookup"><span data-stu-id="6d95e-140">This opens a context menu with functions that are available to perform on the aggregation total.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d95e-141">若要在彙總總計的特定元件上設定警示，請展開該明細項目。</span><span class="sxs-lookup"><span data-stu-id="6d95e-141">You can set an alert on a specific component of the aggregation total by expanding that line item.</span></span> <span data-ttu-id="6d95e-142">您可以用相同的方式展開後面的層級，直到抵達您想要設定警示的層級為止。</span><span class="sxs-lookup"><span data-stu-id="6d95e-142">You can expand succeeding levels in this manner until you reach the level at which you want to set your alert.</span></span>  
  
4.  <span data-ttu-id="6d95e-143">在內容功能表的頂端，按一下**建立警示**。</span><span class="sxs-lookup"><span data-stu-id="6d95e-143">At the top of the context menu, click **Create Alert**.</span></span> <span data-ttu-id="6d95e-144">內容框架便會載入警示建立範本。</span><span class="sxs-lookup"><span data-stu-id="6d95e-144">The content frame will load with the alert creation template.</span></span>  
  
5.  <span data-ttu-id="6d95e-145">在**名稱**文字方塊中，輸入警示的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="6d95e-145">In the **Name** text box, type a descriptive name for the alert.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d95e-146">名稱限制為 100 個字元，且不可包含下列字元: ~ ！ @# $%^&amp;\* （); 如果您在名稱中輸入下列任何字元，則會將紅色虛線外的框表示錯誤，才能完成這個動作，您必須更正錯誤的文字欄位周圍會出現。</span><span class="sxs-lookup"><span data-stu-id="6d95e-146">Names are limited to 100 characters and cannot contain the following characters: ~!@#$%^&amp;\*();  If you enter any of these characters in a name, a dashed red border appears around the text field indicating an error that you must correct to complete the action.</span></span>  
  
6.  <span data-ttu-id="6d95e-147">如果您不想在此時間內啟用的警示，清除**啟用警示**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6d95e-147">If you do not want the alert enabled at this time, clear the **Alert Enabled** check box.</span></span>  
  
7.  <span data-ttu-id="6d95e-148">在**訊息**文字方塊中，輸入在警示觸發時傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="6d95e-148">In the **Message** text box, type the message that is delivered when the alert is triggered.</span></span>  
  
8.  <span data-ttu-id="6d95e-149">從**優先順序**下拉式清單中，選擇此警示的優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="6d95e-149">From the **Priority** drop-down list, choose the priority level for this alert.</span></span> <span data-ttu-id="6d95e-150">優先順序設定代表設定警示的問題嚴重性。</span><span class="sxs-lookup"><span data-stu-id="6d95e-150">The priority setting indicates the severity of the issue on which the alert was set.</span></span>  
  
9. <span data-ttu-id="6d95e-151">在**擁有者**文字方塊中，輸入此警示的擁有者的別名。</span><span class="sxs-lookup"><span data-stu-id="6d95e-151">In the **Owners** text box, type the aliases of the owners of this alert.</span></span> <span data-ttu-id="6d95e-152">請使用分號分隔多個使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="6d95e-152">Use semicolons between the names of multiple users.</span></span>  
  
10. <span data-ttu-id="6d95e-153">在**閾值**區域中，選取比較條件從**計數**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="6d95e-153">In the **Threshold** area, select a comparison condition from the **Count** drop-down list.</span></span>  
  
11. <span data-ttu-id="6d95e-154">在**持續時間**文字方塊中，輸入的臨界值的測量的時間單位數。</span><span class="sxs-lookup"><span data-stu-id="6d95e-154">In the **Duration** text box, enter the number of time units across which the threshold is measured.</span></span>  
  
12. <span data-ttu-id="6d95e-155">從**持續時間**下拉式清單中，選取時間單位。</span><span class="sxs-lookup"><span data-stu-id="6d95e-155">From the **Duration** drop-down list, select the unit of time.</span></span>  
  
13. <span data-ttu-id="6d95e-156">在**警示安全性**區域中，選取的核取方塊以允許其他使用者查看此警示，並訂閱。</span><span class="sxs-lookup"><span data-stu-id="6d95e-156">In the **Alert Security** area, select the check box to allow other users to see this alert and subscribe to it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d95e-157">您可以隨時將警示安全性變更成私用或公用，警示是否有訂閱者並不會影響這個動作。</span><span class="sxs-lookup"><span data-stu-id="6d95e-157">You can switch the alert security between private and public at any time; the presence of subscribers to the alert does not affect this action.</span></span> <span data-ttu-id="6d95e-158">不過，當您將警示安全性從公用切換至私用時，就應該考慮到警示是否有任何訂閱者。</span><span class="sxs-lookup"><span data-stu-id="6d95e-158">When you switch the alert security from public to private, however, you should consider whether there are any subscribers to the alert.</span></span> <span data-ttu-id="6d95e-159">如果警示有訂閱者，當警示變成私用之後，訂閱者將無法編輯他們的訂閱。</span><span class="sxs-lookup"><span data-stu-id="6d95e-159">If there are subscribers to the alert, they will have no way to edit their subscription when the alert is made private.</span></span>  
  
14. <span data-ttu-id="6d95e-160">在右上角的**警示詳細資料**區域中，按一下 [**儲存警示**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d95e-160">In the upper-right corner of the **Alert Details** area, click the **Save Alert** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d95e-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d95e-161">See Also</span></span>  
 [<span data-ttu-id="6d95e-162">如何在活動搜尋中建立查詢</span><span class="sxs-lookup"><span data-stu-id="6d95e-162">How to Create a Query in Activity Search</span></span>](../core/how-to-create-a-query-in-activity-search.md)