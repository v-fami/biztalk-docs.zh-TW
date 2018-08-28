---
title: 如何在活動搜尋中建立查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Query Builder [BAM portal], creating queries
- queries [BAM], saving
- queries [BAM], creating
- queries [BAM], executing
- Query Builder [BAM portal], executing queries
- Query Builder [BAM portal], opening queries
- Query Builder [BAM portal], saving queries
- queries [BAM], opening
ms.assetid: 7940e47d-10e4-4eb1-b4e6-a8b98461e3a8
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fd89ec71319a70c0330ebef80c7c8165cacf6c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989743"
---
# <a name="how-to-create-a-query-in-activity-search"></a><span data-ttu-id="24338-102">如何在活動搜尋中建立查詢</span><span class="sxs-lookup"><span data-stu-id="24338-102">How to Create a Query in Activity Search</span></span>
<span data-ttu-id="24338-103">商務使用者與其他需要接收商務事件和狀態等相關通知的使用者，可以使用查詢建立活動搜尋，然後據以發出警示。</span><span class="sxs-lookup"><span data-stu-id="24338-103">Business end users and other users who need to receive notification of events and status pertaining to their business use queries to create activity searches on which to base alerts.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="24338-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="24338-104">Prerequisites</span></span>  
 <span data-ttu-id="24338-105">您必須具備部署檢視。</span><span class="sxs-lookup"><span data-stu-id="24338-105">You must have a deployed view.</span></span>  
  
### <a name="to-open-a-query"></a><span data-ttu-id="24338-106">若要開啟查詢</span><span class="sxs-lookup"><span data-stu-id="24338-106">To open a query</span></span>  
  
1. <span data-ttu-id="24338-107">按一下 **開始**，指向**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BAM 入口網站**。</span><span class="sxs-lookup"><span data-stu-id="24338-107">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BAM Portal Web Site**.</span></span>  
  
2. <span data-ttu-id="24338-108">在 **我的檢視**框架的入口網站中，按一下 現有的檢視，以展開該檢視所提供的功能表。</span><span class="sxs-lookup"><span data-stu-id="24338-108">In the **My Views** frame of the portal, click an existing view to expand the menus available to that view.</span></span>  
  
3. <span data-ttu-id="24338-109">按一下 **活動搜尋**，展開檢視可用的活動清單。</span><span class="sxs-lookup"><span data-stu-id="24338-109">Click **Activity Search** to expand the list of activities available for the view.</span></span>  
  
4. <span data-ttu-id="24338-110">按一下清單中的活動，</span><span class="sxs-lookup"><span data-stu-id="24338-110">Click an activity from the list.</span></span> <span data-ttu-id="24338-111">這樣會載入所選取活動的 [活動搜尋] 頁面。</span><span class="sxs-lookup"><span data-stu-id="24338-111">This will load the Activity Search page for the selected activity.</span></span>  
  
5. <span data-ttu-id="24338-112">在內容框架中，頂端的頁面上，按一下**瀏覽** 按鈕以開啟**選擇檔案** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="24338-112">In the content frame, at the top of the page, click the **Browse** button to open the **Choose file** dialog box.</span></span>  
  
6. <span data-ttu-id="24338-113">瀏覽至您先前儲存查詢的資料夾。</span><span class="sxs-lookup"><span data-stu-id="24338-113">Browse to the folder where you have previously saved queries.</span></span>  
  
7. <span data-ttu-id="24338-114">按一下儲存的查詢。</span><span class="sxs-lookup"><span data-stu-id="24338-114">Click a save query.</span></span>  
  
8. <span data-ttu-id="24338-115">按一下 [**開啟**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="24338-115">Click the **Open** button.</span></span> <span data-ttu-id="24338-116">這樣會載入在左邊的文字方塊中查詢的路徑**瀏覽** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="24338-116">This will load the path to the query in the text box to the left of the **Browse** button.</span></span> <span data-ttu-id="24338-117">您也可以直接在文字方塊中輸入查詢的路徑。</span><span class="sxs-lookup"><span data-stu-id="24338-117">You can also type the path to the query directly into the text box.</span></span>  
  
9. <span data-ttu-id="24338-118">按一下 [**開啟查詢**右邊的按鈕**瀏覽**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="24338-118">Click the **Open Query** button to the right of the **Browse** button.</span></span>  
  
### <a name="to-construct-a-query"></a><span data-ttu-id="24338-119">建構查詢</span><span class="sxs-lookup"><span data-stu-id="24338-119">To construct a query</span></span>  
  
1. <span data-ttu-id="24338-120">按一下 **開始**，指向**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BAM 入口網站**。</span><span class="sxs-lookup"><span data-stu-id="24338-120">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BAM Portal Web Site**.</span></span>  
  
2. <span data-ttu-id="24338-121">在 **我的檢視**入口網站的清單目前沒有框架設定檢視。</span><span class="sxs-lookup"><span data-stu-id="24338-121">In the **My Views** frame of the portal there is a list of currently configured views.</span></span> <span data-ttu-id="24338-122">每個檢視底下都會列出三項可以在檢視上執行的工作。</span><span class="sxs-lookup"><span data-stu-id="24338-122">Under each view there are three tasks that can be performed on the view.</span></span> <span data-ttu-id="24338-123">如果檢視目前為摺疊狀態，按一下檢視即可展開工作清單。</span><span class="sxs-lookup"><span data-stu-id="24338-123">If the view is currently collapsed, click the existing view to expand the list of tasks.</span></span>  
  
3. <span data-ttu-id="24338-124">按一下 **活動搜尋**，展開檢視可用的活動清單。</span><span class="sxs-lookup"><span data-stu-id="24338-124">Click **Activity Search** to expand the list of activities available for the view.</span></span>  
  
4. <span data-ttu-id="24338-125">按一下清單中的活動，</span><span class="sxs-lookup"><span data-stu-id="24338-125">Click an activity from the list.</span></span> <span data-ttu-id="24338-126">這樣會載入所選取活動的 [活動搜尋] 頁面。</span><span class="sxs-lookup"><span data-stu-id="24338-126">This will load the Activity Search page for the selected activity.</span></span>  
  
5. <span data-ttu-id="24338-127">在內容框架中，在**查詢**方塊中，選擇從欄位**商務資料**下拉式清單，用於在查詢中的比較。</span><span class="sxs-lookup"><span data-stu-id="24338-127">In the content frame, in the **Query** box, choose a field from the **Business Data** drop-down list to use for a comparison in the query.</span></span>  
  
6. <span data-ttu-id="24338-128">從**運算子**下拉式清單中，選取要使用的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="24338-128">From the **Operator** drop-down list, select the comparison operator to use.</span></span>  
  
7. <span data-ttu-id="24338-129">在 **值**方塊中，輸入要比較的值。</span><span class="sxs-lookup"><span data-stu-id="24338-129">In the **Value** box, enter the value to compare against.</span></span> <span data-ttu-id="24338-130">您只能輸入可用於比較欄位的適當值</span><span class="sxs-lookup"><span data-stu-id="24338-130">You will only be able to enter a value appropriate to the field to which you are comparing.</span></span> <span data-ttu-id="24338-131">(如果商務資料項目是日期欄位，則比較資料即是適用於您的文化特性設定格式的日期或日期時間)。</span><span class="sxs-lookup"><span data-stu-id="24338-131">(If the business data item is a date field, then the comparison data is a date or date time formatted as appropriate for your culture settings.)</span></span>  
  
8. <span data-ttu-id="24338-132">如果您有更多子句來加入至查詢時，按一下**新增**查詢方塊右邊的按鈕。</span><span class="sxs-lookup"><span data-stu-id="24338-132">If you have more clauses to add to the query, click the **Add** button to the right of the query box.</span></span> <span data-ttu-id="24338-133">這樣會為下一個子句新增新的一行。</span><span class="sxs-lookup"><span data-stu-id="24338-133">This will add a new line for the next clause.</span></span> <span data-ttu-id="24338-134">您可以選擇是否要使用 AND 或 OR 以聯結子句。</span><span class="sxs-lookup"><span data-stu-id="24338-134">You can select whether the clauses are join by using an AND or an OR.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="24338-135">您無法將子句分組成更複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="24338-135">You cannot group clauses to form more complex queries.</span></span> <span data-ttu-id="24338-136">查詢是由 AND 或 OR 運算子聯結而成的一組簡單子句。</span><span class="sxs-lookup"><span data-stu-id="24338-136">A query is a simple set of clauses joined by an AND or an OR operator.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="24338-137">如果您在這些程序期間按 上一頁 按鈕，並收到 「 警告： 頁面已經過期，「 您可以按 F5 來取回原來的內容。</span><span class="sxs-lookup"><span data-stu-id="24338-137">If you click the back button during these procedures and receive a "warning: page has expired," you can press F5 to get your original contents back.</span></span> <span data-ttu-id="24338-138">您可能必須按數次 F5。</span><span class="sxs-lookup"><span data-stu-id="24338-138">You may have to press F5 several times.</span></span>  
  
9. <span data-ttu-id="24338-139">在資料行選擇器選取資料或從里程碑**可用的資料和里程碑**查詢以傳回做為資料的清單方塊。</span><span class="sxs-lookup"><span data-stu-id="24338-139">In the Column Chooser select the data or milestones from the **Available Data and Milestones** list box for the query to return as data.</span></span> <span data-ttu-id="24338-140">您可以按住 SHIFT 鍵，再按一下所要傳回之群組的第一個和最後一個項目，以選取多個項目。</span><span class="sxs-lookup"><span data-stu-id="24338-140">You can select multiple items by holding down the SHIFT key and clicking the first and last items in the group you want to return.</span></span> <span data-ttu-id="24338-141">您也可以按住 CTRL 鍵，再一一選取清單中要傳回的項目，以選取多個項目。</span><span class="sxs-lookup"><span data-stu-id="24338-141">You can also select multiple items from the list by holding down the CTRL key and selecting the items to return.</span></span>  
  
10. <span data-ttu-id="24338-142">使用**>>** 按鈕以移至選取的項目**項目可顯示**清單方塊。</span><span class="sxs-lookup"><span data-stu-id="24338-142">Use the **>>** button to move the selected items to the **Items to show** list box.</span></span> <span data-ttu-id="24338-143">您可以從這份清單移除項目，藉由選取並使用**<<** 按鈕，移回資料和里程碑清單方塊。</span><span class="sxs-lookup"><span data-stu-id="24338-143">You can remove items from this list by selecting them and using the **<<** button to move them back to the data and milestones list box.</span></span>  
  
11. <span data-ttu-id="24338-144">選取查詢要傳回的所有項目之後，您可以重新排列結果，以決定各欄位的顯示順序。</span><span class="sxs-lookup"><span data-stu-id="24338-144">Once you have selected all the items that the query will return, you can rearrange the results to determine in what order the columns are shown.</span></span> <span data-ttu-id="24338-145">若要將資料行移至所傳回的資料集中的第一個位置中，選取該按一下它，然後按一下**下移**按鈕，直到它位於最上層的項目清單。</span><span class="sxs-lookup"><span data-stu-id="24338-145">To move a column to the first position in the returned data set, select it by clicking it and clicking the **Move Up** button until it is at the top of the list of items.</span></span> <span data-ttu-id="24338-146">同樣地，若要移動項目中傳回的資料集的更新位置，選取的項目按一下它，然後按一下**下移**按鈕，直到它是在您要它顯示的位置。</span><span class="sxs-lookup"><span data-stu-id="24338-146">Similarly, to move an item to a later position in the returned data set, select the item by clicking it and then clicking the **Move Down** button until it is in the position in which you want it to display.</span></span>  
  
### <a name="to-save-a-query"></a><span data-ttu-id="24338-147">若要儲存查詢</span><span class="sxs-lookup"><span data-stu-id="24338-147">To save a query</span></span>  
  
1.  <span data-ttu-id="24338-148">在內容框架中，頂端的頁面上，按一下**另存查詢** 按鈕以開啟**儲存檔案** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="24338-148">In the content frame, at the top of the page, click the **Save Query** button to open the **Save File** dialog box.</span></span>  
  
2.  <span data-ttu-id="24338-149">在 **檔案下載** 對話方塊中，按一下**儲存** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="24338-149">On the **File Download** dialog box, click the **Save** button.</span></span>  
  
3.  <span data-ttu-id="24338-150">瀏覽至您要儲存查詢的位置。</span><span class="sxs-lookup"><span data-stu-id="24338-150">Browse to the location where you want to save the query.</span></span>  
  
4.  <span data-ttu-id="24338-151">您可以接受查詢提供的預設名稱，或者您可以輸入新的名稱，在**檔案名**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="24338-151">You can accept the default name provided for the query or you can enter a new name in the **File Name** text box.</span></span>  
  
5.  <span data-ttu-id="24338-152">按一下 [**儲存**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="24338-152">Click the **Save** button.</span></span>  
  
### <a name="to-execute-a-query"></a><span data-ttu-id="24338-153">若要執行查詢</span><span class="sxs-lookup"><span data-stu-id="24338-153">To execute a query</span></span>  
  
1. <span data-ttu-id="24338-154">按一下 **開始**，指向**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BAM 入口網站**。</span><span class="sxs-lookup"><span data-stu-id="24338-154">Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BAM Portal Web Site**.</span></span>  
  
2. <span data-ttu-id="24338-155">在 **我的檢視**框架的入口網站中，按一下 現有的檢視，以展開該檢視所提供的功能表。</span><span class="sxs-lookup"><span data-stu-id="24338-155">In the **My Views** frame of the portal, click an existing view to expand the menus available to that view.</span></span>  
  
3. <span data-ttu-id="24338-156">按一下 **活動搜尋**，展開檢視可用的活動清單。</span><span class="sxs-lookup"><span data-stu-id="24338-156">Click **Activity Search** to expand the list of activities available for the view.</span></span>  
  
4. <span data-ttu-id="24338-157">按一下清單中的活動，</span><span class="sxs-lookup"><span data-stu-id="24338-157">Click an activity from the list.</span></span> <span data-ttu-id="24338-158">這樣會載入所選取活動的 [活動搜尋] 頁面。</span><span class="sxs-lookup"><span data-stu-id="24338-158">This will load the Activity Search page for the selected activity.</span></span>  
  
5. <span data-ttu-id="24338-159">開啟現有的查詢，或建立新的查詢。</span><span class="sxs-lookup"><span data-stu-id="24338-159">Either open an existing query or build a new query.</span></span>  
  
6. <span data-ttu-id="24338-160">在入口網站的內容框架中，按一下**執行查詢** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="24338-160">In the content frame of the portal, click the **Execute Query** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24338-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24338-161">See Also</span></span>  
 [<span data-ttu-id="24338-162">BAM 入口網站中的活動搜尋</span><span class="sxs-lookup"><span data-stu-id="24338-162">Activity Searches in the BAM Portal</span></span>](../core/activity-searches-in-the-bam-portal.md)