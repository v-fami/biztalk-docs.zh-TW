---
title: '案例 2: 使用搜尋方塊 web 組件搜尋 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a233772f-7577-4ac5-b55a-cb1ba2f464c7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ac446f83af49d8d2faa06c7b43b1f59d343679b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991703"
---
# <a name="scenario-2--search-using-the-search-box-web-part"></a><span data-ttu-id="97aa0-102">案例 2： 搜尋使用搜尋方塊 web 組件</span><span class="sxs-lookup"><span data-stu-id="97aa0-102">Scenario 2:  Search using the search box web part</span></span>
<span data-ttu-id="97aa0-103">我們將在 Microsoft Office SharePoint Server 來設定使用您可以在同時執行全文檢索搜尋的搜尋應用程式中設定搜尋設定 Oracle E-business Suite 中的 MS_SAMPLE_EMPLOYEE 介面資料表。</span><span class="sxs-lookup"><span data-stu-id="97aa0-103">We will configure the search settings in Microsoft Office SharePoint Server to configure a search application using which you can perform a full text search on the MS_SAMPLE_EMPLOYEE interface table in Oracle E-Business Suite.</span></span> <span data-ttu-id="97aa0-104">稍後，我們會新增搜尋方塊 Web 組件若要從您可以在其中執行搜尋。</span><span class="sxs-lookup"><span data-stu-id="97aa0-104">Later, we will add a Search Box Web Part to from where you can perform the search.</span></span>  
  
 
  
##  <a name="Define"></a> <span data-ttu-id="97aa0-105">定義內容的來源</span><span class="sxs-lookup"><span data-stu-id="97aa0-105">Define the Content Source</span></span>  
 <span data-ttu-id="97aa0-106">本節將討論如何定義內容的來源，從 Microsoft Office SharePoint Server 可以搜耙的資料。</span><span class="sxs-lookup"><span data-stu-id="97aa0-106">This section talks about defining a content source from where Microsoft Office SharePoint Server can crawl the data.</span></span> <span data-ttu-id="97aa0-107">這牽涉到將內容對應至方法的執行個體中建立 Id Enumerator[步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="97aa0-107">This involves mapping the content to the Id Enumerator method instance created in [Step 2: Create an application definition file for the Oracle E-Business Suite artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md).</span></span>  
  
#### <a name="to-define-a-content-source"></a><span data-ttu-id="97aa0-108">若要定義的內容來源</span><span class="sxs-lookup"><span data-stu-id="97aa0-108">To define a content source</span></span>  
  
1.  <span data-ttu-id="97aa0-109">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="97aa0-109">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="97aa0-110">按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="97aa0-110">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="97aa0-111">在左側的導覽窗格中，按一下名稱的共用服務提供者 (SSP) 您要設定搜尋應用程式。</span><span class="sxs-lookup"><span data-stu-id="97aa0-111">In the left navigation pane, click the name of the Shared Service Provider (SSP) where you want to configure the search application.</span></span>  
  
3.  <span data-ttu-id="97aa0-112">在 [首頁] 頁面中，在**搜尋**區段中，按一下**搜尋設定**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-112">On the Home page, in the **Search** section, click **Search settings**.</span></span>  
  
4.  <span data-ttu-id="97aa0-113">在設定搜尋設定 頁面上，在左窗格的下**耙梳**，按一下**預設內容存取帳戶**指定編目內容時，使用做為預設帳戶的帳戶。</span><span class="sxs-lookup"><span data-stu-id="97aa0-113">On the Configure Search Settings page, in the left pane under **Crawling**, click **Default content access account** to specify an account to use as the default account when crawling content.</span></span>  
  
5.  <span data-ttu-id="97aa0-114">在預設內容的存取帳戶] 頁面上，指定使用者名稱和密碼認證，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-114">On the Default Content Access Account page, specify the user name and password credentials, and click **OK**.</span></span> <span data-ttu-id="97aa0-115">您將返回 [搜尋] 頁面。</span><span class="sxs-lookup"><span data-stu-id="97aa0-115">You will return to the Search Administration page.</span></span>  
  
6.  <span data-ttu-id="97aa0-116">在左窗格的下**耙梳**，按一下**內容來源**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-116">In the left pane under **Crawling**, click **Content Sources**.</span></span>  
  
7.  <span data-ttu-id="97aa0-117">在管理內容的來源 頁面上，按一下**新的內容來源**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-117">On the Manage Content Sources page, click **New Content Source**.</span></span>  
  
8.  <span data-ttu-id="97aa0-118">在管理內容的來源 頁面上，按一下**新的內容來源**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-118">On the Manage Content Sources page, click **New Content Source**.</span></span>  
  
9. <span data-ttu-id="97aa0-119">在 [新增內容來源] 頁面中：</span><span class="sxs-lookup"><span data-stu-id="97aa0-119">On the Add Content Source page:</span></span>  
  
    1.  <span data-ttu-id="97aa0-120">型別`MS_SAMPLE_EMPLOYEE`中**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="97aa0-120">Type `MS_SAMPLE_EMPLOYEE` in the **Name** box.</span></span>  
  
    2.  <span data-ttu-id="97aa0-121">在 **內容的來源類型**區域中，按一下**商務資料**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-121">In the **Content Source Type** area, click **Business Data**.</span></span>  
  
    3.  <span data-ttu-id="97aa0-122">在**應用程式**區域中，按一下**搜耙選取應用程式**，然後選取**MS_SAMPLE_EMPLOYEE_Instance**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="97aa0-122">In the **Applications** area, click **Crawl selected applications**, and then select the **MS_SAMPLE_EMPLOYEE_Instance** check box.</span></span>  
  
    4.  <span data-ttu-id="97aa0-123">在 **啟動完整搜耙**區域中，選取**此內容來源啟動完整搜耙**核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-123">In the **Start Full Crawl** area, select the **Start full crawl of this content source** check box, and then click **OK**.</span></span>  
  
         <span data-ttu-id="97aa0-124">![新增內容來源](../../adapters-and-accelerators/adapter-oracle-ebs/media/27-add-content-source.gif "27_Add_Content_Source")</span><span class="sxs-lookup"><span data-stu-id="97aa0-124">![Add content source](../../adapters-and-accelerators/adapter-oracle-ebs/media/27-add-content-source.gif "27_Add_Content_Source")</span></span>  
  
10. <span data-ttu-id="97aa0-125">您會返回 [管理內容來源] 頁面，以加入新的內容來源。</span><span class="sxs-lookup"><span data-stu-id="97aa0-125">You will return to the Manage Content Sources page with the new content source added.</span></span> <span data-ttu-id="97aa0-126">內容的來源將 Oracle E-business Suite 中 MS_SAMPLE_EMPLOYEE 介面資料表中的資料進行編目。</span><span class="sxs-lookup"><span data-stu-id="97aa0-126">The content source will crawl through the data in the MS_SAMPLE_EMPLOYEE interface table in the Oracle E-Business Suite.</span></span> <span data-ttu-id="97aa0-127">等候編目完成。</span><span class="sxs-lookup"><span data-stu-id="97aa0-127">Wait until the crawling is completed.</span></span>  
  
11. <span data-ttu-id="97aa0-128">在左窗格的下**耙梳**，按一下**搜耙記錄檔**，然後確認 記錄檔，以確保編目成功。</span><span class="sxs-lookup"><span data-stu-id="97aa0-128">In the left pane under **Crawling**, click **Crawl Log**, and then verify the log file to ensure that the crawling is successful.</span></span>  
  
##  <a name="Scope"></a> <span data-ttu-id="97aa0-129">定義編目的內容範圍</span><span class="sxs-lookup"><span data-stu-id="97aa0-129">Define a Scope for the Crawled Content</span></span>  
  
1. <span data-ttu-id="97aa0-130">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="97aa0-130">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="97aa0-131">按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="97aa0-131">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2. <span data-ttu-id="97aa0-132">在左側的導覽窗格中，按一下名稱的共用服務提供者 (SSP) 您要設定搜尋應用程式。</span><span class="sxs-lookup"><span data-stu-id="97aa0-132">In the left navigation pane, click the name of the Shared Service Provider (SSP) where you want to configure the search application.</span></span>  
  
3. <span data-ttu-id="97aa0-133">在 [首頁] 頁面中，在**搜尋**區段中，按一下**搜尋設定**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-133">On the Home page, in the **Search** section, click **Search settings**.</span></span>  
  
4. <span data-ttu-id="97aa0-134">在設定搜尋設定 頁面上，在左窗格的下**查詢，並產生**，按一下**範圍**來定義資料的耙梳的範圍。</span><span class="sxs-lookup"><span data-stu-id="97aa0-134">On the Configure Search Settings page, in the left pane under **Queries and Results**, click **Scopes** to define a scope for the crawling of data.</span></span>  
  
5. <span data-ttu-id="97aa0-135">在 檢視領域 頁面中，按一下 **新的範圍**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-135">On the View Scopes page, click **New Scope**.</span></span>  
  
6. <span data-ttu-id="97aa0-136">在 [建立領域] 頁面中，輸入`MS_SAMPLE_EMPLOYEE_Search`中**Title**方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-136">On the Create Scope page, type `MS_SAMPLE_EMPLOYEE_Search` in the **Title** box, and then click **OK**.</span></span>  
  
    <span data-ttu-id="97aa0-137">![建立領域](../../adapters-and-accelerators/adapter-oracle-ebs/media/28-create-scope.gif "28_Create_Scope")</span><span class="sxs-lookup"><span data-stu-id="97aa0-137">![Create a scope](../../adapters-and-accelerators/adapter-oracle-ebs/media/28-create-scope.gif "28_Create_Scope")</span></span>  
  
7. <span data-ttu-id="97aa0-138">您會回到檢視領域 頁面，以新增新範圍。</span><span class="sxs-lookup"><span data-stu-id="97aa0-138">You will return to the View Scopes page with the new scope added.</span></span> <span data-ttu-id="97aa0-139">在 **更新狀態**資料行，新加入的範圍中，按一下**新增規則**連結。</span><span class="sxs-lookup"><span data-stu-id="97aa0-139">In the **Update Status** column for the newly added scope, click the **Add rules** link.</span></span>  
  
8. <span data-ttu-id="97aa0-140">在 新增範圍規則頁面上：</span><span class="sxs-lookup"><span data-stu-id="97aa0-140">On the Add Scope Rule page:</span></span>  
  
   1.  <span data-ttu-id="97aa0-141">在 **範圍規則類型**區域中，按一下**內容來源**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-141">In the **Scope Rule Type** area, click **Content Source**.</span></span>  
  
   2.  <span data-ttu-id="97aa0-142">在 **內容的來源**清單中，按一下**MS_SAMPLE_EMPLOYEE**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-142">In the **Content Source** list, click **MS_SAMPLE_EMPLOYEE**, and then click **OK**.</span></span>  
  
        <span data-ttu-id="97aa0-143">![新增範圍規則](../../adapters-and-accelerators/adapter-oracle-ebs/media/29-add-scope-rule.gif "29_Add_Scope_Rule")</span><span class="sxs-lookup"><span data-stu-id="97aa0-143">![Add a scope rule](../../adapters-and-accelerators/adapter-oracle-ebs/media/29-add-scope-rule.gif "29_Add_Scope_Rule")</span></span>  
  
9. <span data-ttu-id="97aa0-144">新增範圍規則，您會回到檢視領域 頁面。</span><span class="sxs-lookup"><span data-stu-id="97aa0-144">You will return to the View Scopes page with the rule added for the scope.</span></span> <span data-ttu-id="97aa0-145">在左窗格中，按一下**搜尋管理**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-145">In the left pane, click **Search Administration**.</span></span>  
  
10. <span data-ttu-id="97aa0-146">在 [搜尋] 頁面，找出**需要更新的範圍**資料列，然後按一下**立即開始更新**連結。</span><span class="sxs-lookup"><span data-stu-id="97aa0-146">On the Search Administration page, locate the **Scopes needing update** row, and click the **Start update now** link.</span></span>  
  
    <span data-ttu-id="97aa0-147">**範圍的更新狀態**資料列都會顯示範圍更新的狀態。</span><span class="sxs-lookup"><span data-stu-id="97aa0-147">The **Scope update status** row will display the status of the scope update.</span></span> <span data-ttu-id="97aa0-148">等候更新完成。</span><span class="sxs-lookup"><span data-stu-id="97aa0-148">Wait until the update is complete.</span></span> <span data-ttu-id="97aa0-149">更新完成後，範圍是已備妥可用。</span><span class="sxs-lookup"><span data-stu-id="97aa0-149">After the updated is completed, the scope is ready to be used.</span></span>  
  
##  <a name="AddScope"></a> <span data-ttu-id="97aa0-150">將範圍新增至搜尋下拉式清單中</span><span class="sxs-lookup"><span data-stu-id="97aa0-150">Add the Scope to the Search Dropdown</span></span>  
 <span data-ttu-id="97aa0-151">您已建立的搜尋範圍之後，您必須加入範圍在 Microsoft Office SharePoint Server 搜尋下拉式清單中，可以使用。</span><span class="sxs-lookup"><span data-stu-id="97aa0-151">After you have created the search scope, you must add the scope to the search dropdown in Microsoft Office SharePoint Server so that it can be used.</span></span>  
  
#### <a name="to-add-the-scope-to-the-search-dropdown"></a><span data-ttu-id="97aa0-152">若要將範圍新增至搜尋下拉式清單中</span><span class="sxs-lookup"><span data-stu-id="97aa0-152">To add the scope to the search dropdown</span></span>  
  
1.  <span data-ttu-id="97aa0-153">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="97aa0-153">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="97aa0-154">按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="97aa0-154">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="97aa0-155">在左側的導覽窗格中，按一下名稱的共用服務提供者 (SSP) 您要設定搜尋應用程式。</span><span class="sxs-lookup"><span data-stu-id="97aa0-155">In the left navigation pane, click the name of the Shared Service Provider (SSP) where you want to configure the search application.</span></span>  
  
3.  <span data-ttu-id="97aa0-156">在共用服務管理 頁面的右上角，按一下**站台動作**，然後按一下**站台設定**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-156">On the Shared Services Administration page, in the upper-right corner, click **Site Actions**, and then click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="97aa0-157">在站台設定 頁面中**網站集合管理**區段中，按一下**搜尋範圍**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-157">On the Site Settings page, in the **Site Collection Administration** section, click **Search scopes**.</span></span>  
  
5.  <span data-ttu-id="97aa0-158">在 檢視領域 頁面中，按一下 **搜尋下拉式清單中**連結。</span><span class="sxs-lookup"><span data-stu-id="97aa0-158">On the View Scopes page, click the **Search Dropdown** link.</span></span>  
  
     <span data-ttu-id="97aa0-159">![檢視範圍](../../adapters-and-accelerators/adapter-oracle-ebs/media/30-view-scope.gif "30_View_Scope")</span><span class="sxs-lookup"><span data-stu-id="97aa0-159">![View scopes](../../adapters-and-accelerators/adapter-oracle-ebs/media/30-view-scope.gif "30_View_Scope")</span></span>  
  
6.  <span data-ttu-id="97aa0-160">在編輯範圍顯示群組 頁面上：</span><span class="sxs-lookup"><span data-stu-id="97aa0-160">On the Edit Scope Display Group page:</span></span>  
  
    1.  <span data-ttu-id="97aa0-161">在 **領域**區域中，選取**MS_SAMPLE_EMPLOYEE_Search**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="97aa0-161">In the **Scopes** area, select the **MS_SAMPLE_EMPLOYEE_Search** check box.</span></span>  
  
    2.  <span data-ttu-id="97aa0-162">在 **預設範圍**區域中，按一下**MS_SAMPLE_EMPLOYEE_Search**中**預設範圍**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-162">In the **Default Scope** area, click **MS_SAMPLE_EMPLOYEE_Search** in the **Default Scope** list, and then click **OK**.</span></span>  
  
         <span data-ttu-id="97aa0-163">![編輯範圍顯示群組頁面](../../adapters-and-accelerators/adapter-oracle-ebs/media/31-edit-scope-display-group.gif "31_Edit_Scope_Display_Group")</span><span class="sxs-lookup"><span data-stu-id="97aa0-163">![Edit Scope Display Group page](../../adapters-and-accelerators/adapter-oracle-ebs/media/31-edit-scope-display-group.gif "31_Edit_Scope_Display_Group")</span></span>  
  
7.  <span data-ttu-id="97aa0-164">您會回到與 MS_SAMPLE_EMPLOYEE_Search 範圍搜尋下拉式清單中顯示群組中新增的檢視領域 頁面。</span><span class="sxs-lookup"><span data-stu-id="97aa0-164">You will return to the View Scopes page with the MS_SAMPLE_EMPLOYEE_Search scope added in the Search Dropdown display group.</span></span>  
  
##  <a name="SearchWebPart"></a> <span data-ttu-id="97aa0-165">新增搜尋方塊 Web 組件</span><span class="sxs-lookup"><span data-stu-id="97aa0-165">Add the Search Box Web Part</span></span>  
 <span data-ttu-id="97aa0-166">若要啟用使用者執行 Oracle E-business Suite 的 MS_SAMPLE_EMPLOYEE 介面資料表的全文檢索搜尋，，您必須現在建立網頁組件，並在搜尋方塊 Web 組件加入。</span><span class="sxs-lookup"><span data-stu-id="97aa0-166">To enable the users to perform a full-text search on the MS_SAMPLE_EMPLOYEE interface table in Oracle E-Business Suite, you must now create a Web part page, and add a Search Box Web Part to it.</span></span>  
  
#### <a name="to-add-the-search-box-web-part"></a><span data-ttu-id="97aa0-167">若要新增搜尋方塊 Web 組件</span><span class="sxs-lookup"><span data-stu-id="97aa0-167">To add the Search Box Web Part</span></span>  
  
1.  <span data-ttu-id="97aa0-168">建立一個稱為 網頁組件頁面**MS_SAMPLE_EMPLOYEE_Search**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-168">Create a Web Part page called **MS_SAMPLE_EMPLOYEE_Search**.</span></span> <span data-ttu-id="97aa0-169">若要了解建立 Web 組件頁面的步驟，請參閱[案例 1： 使用商務資料清單 web 組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)中[案例 1： 使用商務資料清單 web 組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)。</span><span class="sxs-lookup"><span data-stu-id="97aa0-169">To know the steps for creating a Web Part page, see [Scenario 1: Display data using Business Data List web part](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md) in [Scenario 1: Display data using Business Data List web part](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md).</span></span>  
  
2.  <span data-ttu-id="97aa0-170">在 MS_SAMPLE_EMPLOYEE_Search 頁面上，按一下**新增網頁組件**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-170">On the MS_SAMPLE_EMPLOYEE_Search page, click **Add a Web Part**.</span></span>  
  
3.  <span data-ttu-id="97aa0-171">在**新增網頁組件**對話方塊中，於**搜尋**區段中，選取**搜尋方塊**核取方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="97aa0-171">In the **Add Web Parts** dialog box, in the **Search** section, select the **Search Box** check box, and then click **Add**.</span></span>  
  
     <span data-ttu-id="97aa0-172">![新增搜尋方塊 Web 組件](../../adapters-and-accelerators/adapter-oracle-ebs/media/32-search-web-part.gif "32_Search_Web_Part")</span><span class="sxs-lookup"><span data-stu-id="97aa0-172">![Add the Search Box Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/32-search-web-part.gif "32_Search_Web_Part")</span></span>  
  
4.  <span data-ttu-id="97aa0-173">搜尋方塊 Web 組件會加入 MS_SAMPLE_EMPLOYEE_Search 頁面。</span><span class="sxs-lookup"><span data-stu-id="97aa0-173">The Search Box Web part is added to the MS_SAMPLE_EMPLOYEE_Search page.</span></span>  
  
     <span data-ttu-id="97aa0-174">![搜尋方塊 」 Web 組件](../../adapters-and-accelerators/adapter-oracle-ebs/media/33-search-web-part-final.gif "33_Search_Web_Part_Final")</span><span class="sxs-lookup"><span data-stu-id="97aa0-174">![Search Box Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/33-search-web-part-final.gif "33_Search_Web_Part_Final")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97aa0-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97aa0-175">See Also</span></span>  
 [<span data-ttu-id="97aa0-176">步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料</span><span class="sxs-lookup"><span data-stu-id="97aa0-176">Step 3: Create a SharePoint application to retrieve data from Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)  
 [<span data-ttu-id="97aa0-177">案例 1：使用商務資料清單 Web 組件顯示資料</span><span class="sxs-lookup"><span data-stu-id="97aa0-177">Scenario 1: Display data using Business Data List web part</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)