---
title: "步驟 4： 測試 SharePoint 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a859044e-a28e-477e-a20b-f9bb3c9f7405
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 427235d27e4e783111ccdb60f799c228737cd008
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-your-sharepoint-application"></a><span data-ttu-id="4d72d-102">步驟 4： 測試 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="4d72d-102">Step 4: Test your SharePoint application</span></span>
<span data-ttu-id="4d72d-103">![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="4d72d-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="4d72d-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="4d72d-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="4d72d-105">**目標：**您 SharePoint 網站中加入 Web 組件並建立應用程式，您必須測試應用程式擷取 Oracle E-business Suite 中的一些資料之後。</span><span class="sxs-lookup"><span data-stu-id="4d72d-105">**Objective:** After you have added Web Parts in the SharePoint site and created an application, you must test the application by retrieving some data from the Oracle E-Business Suite.</span></span> <span data-ttu-id="4d72d-106">本主題說明如何使用應用程式來擷取 Oracle E-business Suite 中的資料。</span><span class="sxs-lookup"><span data-stu-id="4d72d-106">This topic provides instructions on how to use the application to retrieve the data from the Oracle E-Business Suite.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4d72d-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="4d72d-107">Prerequisites</span></span>  
 <span data-ttu-id="4d72d-108">您應該建立包含適當的 Web 組件，來擷取商務資料 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="4d72d-108">You should have created the Web Part page that contains the appropriate Web Parts to retrieve business data.</span></span> <span data-ttu-id="4d72d-109">請參閱[步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)。</span><span class="sxs-lookup"><span data-stu-id="4d72d-109">See [Step 3: Create a SharePoint application to retrieve data from Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md).</span></span>  
  
### <a name="scenario-1-to-test-the-sharepoint-application-created-using-business-data-list-web-part"></a><span data-ttu-id="4d72d-110">案例 1： 測試 SharePoint 應用程式，建立使用商務資料清單網頁組件</span><span class="sxs-lookup"><span data-stu-id="4d72d-110">Scenario 1: To test the SharePoint application created using Business Data List Web Part</span></span>  
  
1.  <span data-ttu-id="4d72d-111">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="4d72d-111">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="4d72d-112">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="4d72d-112">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="4d72d-113">在左側瀏覽窗格中，按一下您要在其建立應用程式的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d72d-113">In the left navigation pane, click the name of the SSP under which you created the application.</span></span>  
  
3.  <span data-ttu-id="4d72d-114">在左窗格中，按一下 **檢視所有網站內容**。</span><span class="sxs-lookup"><span data-stu-id="4d72d-114">In the left pane, click **View All Site Content**.</span></span> <span data-ttu-id="4d72d-115">在右窗格中，按一下 **表單範本**。</span><span class="sxs-lookup"><span data-stu-id="4d72d-115">In the right pane, click **Form Templates**.</span></span>  
  
4.  <span data-ttu-id="4d72d-116">在**表單類別**清單中，按一下**MS_SAMPLE_EMPLOYEE**。</span><span class="sxs-lookup"><span data-stu-id="4d72d-116">In the **Form Category** list, click **MS_SAMPLE_EMPLOYEE**.</span></span> <span data-ttu-id="4d72d-117">當您建立 Web 組件頁面中的，指定這個名稱[案例 1： 使用商務資料清單網頁組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)。</span><span class="sxs-lookup"><span data-stu-id="4d72d-117">You specified this name when you created the Web Part page in [Scenario 1: Display data using Business Data List web part](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md).</span></span>  
  
5.  <span data-ttu-id="4d72d-118">搜尋的搜尋字串為基礎的員工。</span><span class="sxs-lookup"><span data-stu-id="4d72d-118">Search for employees based on a search string.</span></span> <span data-ttu-id="4d72d-119">例如，若要搜尋的所有員工，輸入 **%** 在文字方塊中，按一下**抓取資料**。</span><span class="sxs-lookup"><span data-stu-id="4d72d-119">For example, to search for all the employees, type **%** in the text box, and click **Retrieve Data**.</span></span> <span data-ttu-id="4d72d-120">下圖顯示從 Oracle E-business Suite 擷取的記錄：</span><span class="sxs-lookup"><span data-stu-id="4d72d-120">The following figure shows the records retrieved from Oracle E-Business Suite:</span></span>  
  
     <span data-ttu-id="4d72d-121">![搜尋結果](../../adapters-and-accelerators/adapter-oracle-ebs/media/bdc-result.gif "BDC_Result")</span><span class="sxs-lookup"><span data-stu-id="4d72d-121">![Search result](../../adapters-and-accelerators/adapter-oracle-ebs/media/bdc-result.gif "BDC_Result")</span></span>  
  
6.  <span data-ttu-id="4d72d-122">您也可以輸入他們的名字或姓氏來搜尋特定的員工：</span><span class="sxs-lookup"><span data-stu-id="4d72d-122">You can also search for a specific employee by entering their first name or last name:</span></span>  
  
    -   <span data-ttu-id="4d72d-123">使用名字的搜尋，輸入 員工名稱後面接著字母 **%** 符號來傳回符合搜尋準則的所有員工的記錄。</span><span class="sxs-lookup"><span data-stu-id="4d72d-123">To search using the first name, type the initial letters of an employee name followed by the **%** symbol to return records of all the employees matching the search criteria.</span></span>  
  
    -   <span data-ttu-id="4d72d-124">若要搜尋使用的最後一個名稱，請輸入 **%** 後面接著員工的姓氏。</span><span class="sxs-lookup"><span data-stu-id="4d72d-124">To search using the last name, type **%** followed by employee’s last name.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d72d-125">搜尋字串會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4d72d-125">The search string is case sensitive.</span></span>  
  
     <span data-ttu-id="4d72d-126">![依員工名字搜尋](../../adapters-and-accelerators/adapter-oracle-ebs/media/b5044c4d-31ec-46d8-b02c-3b26bfe8178e.gif "b5044c4d-31ec-46d8-b02c-3b26bfe8178e")</span><span class="sxs-lookup"><span data-stu-id="4d72d-126">![Searching by first name of an employee](../../adapters-and-accelerators/adapter-oracle-ebs/media/b5044c4d-31ec-46d8-b02c-3b26bfe8178e.gif "b5044c4d-31ec-46d8-b02c-3b26bfe8178e")</span></span>  
  
### <a name="scenario-2-to-test-the-sharepoint-application-created-to-perform-a-full-text-search"></a><span data-ttu-id="4d72d-127">案例 2： 測試 SharePoint 應用程式，建立要執行全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="4d72d-127">Scenario 2: To test the SharePoint application created to perform a full-text search</span></span>  
  
1.  <span data-ttu-id="4d72d-128">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="4d72d-128">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="4d72d-129">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="4d72d-129">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="4d72d-130">在左側瀏覽窗格中，按一下您要在其建立應用程式的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d72d-130">In the left navigation pane, click the name of the SSP under which you created the application.</span></span>  
  
3.  <span data-ttu-id="4d72d-131">在左窗格中，按一下 **檢視所有網站內容**。</span><span class="sxs-lookup"><span data-stu-id="4d72d-131">In the left pane, click **View All Site Content**.</span></span> <span data-ttu-id="4d72d-132">在右窗格中，按一下 **表單範本**。</span><span class="sxs-lookup"><span data-stu-id="4d72d-132">In the right pane, click **Form Templates**.</span></span>  
  
4.  <span data-ttu-id="4d72d-133">在**表單類別**清單中，按一下**MS_SAMPLE_EMPLOYEE_Search**。</span><span class="sxs-lookup"><span data-stu-id="4d72d-133">In the **Form Category** list, click **MS_SAMPLE_EMPLOYEE_Search**.</span></span> <span data-ttu-id="4d72d-134">當您建立 Web 組件頁面中的，指定這個名稱[案例 2： 使用搜尋方塊 」 Web 組件執行搜尋](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md)中[案例 2： 使用搜尋方塊 」 Web 組件執行搜尋](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md)。</span><span class="sxs-lookup"><span data-stu-id="4d72d-134">You specified this name when you created the Web Part page in [Scenario 2: Perform a Search Using the Search Box Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md) in [Scenario 2: Perform a Search Using the Search Box Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md).</span></span>  
  
5.  <span data-ttu-id="4d72d-135">MS_SAMPLE_EMPLOYEE_Search 頁面會顯示您要執行全文檢索搜尋 MS_SAMPLE 員工資料表的 [搜尋] 方塊。</span><span class="sxs-lookup"><span data-stu-id="4d72d-135">The MS_SAMPLE_EMPLOYEE_Search page displays the search box where you can perform a full-text search on the MS_SAMPLE EMPLOYEE table.</span></span> <span data-ttu-id="4d72d-136">例如，如果您想要搜尋所有位於紐約的員工，輸入`New York`在搜尋方塊中，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="4d72d-136">For example, if you want to search for all the employees who live in New York, type `New York` in the search box, and press ENTER.</span></span>  
  
     <span data-ttu-id="4d72d-137">![指定搜尋參數](../../adapters-and-accelerators/adapter-oracle-ebs/media/34-search-result.gif "34_Search_Result")</span><span class="sxs-lookup"><span data-stu-id="4d72d-137">![Specify a search parameter](../../adapters-and-accelerators/adapter-oracle-ebs/media/34-search-result.gif "34_Search_Result")</span></span>  
  
6.  <span data-ttu-id="4d72d-138">搜尋的結果會顯示頁面。</span><span class="sxs-lookup"><span data-stu-id="4d72d-138">A page appears with the search results.</span></span> <span data-ttu-id="4d72d-139">每個相符的記錄會顯示為搜尋結果頁面中的連結。</span><span class="sxs-lookup"><span data-stu-id="4d72d-139">Each matching records is displayed as a link in the search results page.</span></span>  
  
     <span data-ttu-id="4d72d-140">![搜尋結果](../../adapters-and-accelerators/adapter-oracle-ebs/media/05cc6fdc-8c9f-4312-8579-ef1753d02c63.gif "05cc6fdc-8c9f-4312-8579-ef1753d02c63")</span><span class="sxs-lookup"><span data-stu-id="4d72d-140">![Search results](../../adapters-and-accelerators/adapter-oracle-ebs/media/05cc6fdc-8c9f-4312-8579-ef1753d02c63.gif "05cc6fdc-8c9f-4312-8579-ef1753d02c63")</span></span>  
  
7.  <span data-ttu-id="4d72d-141">按一下要檢視個別的員工記錄的搜尋結果中的連結。</span><span class="sxs-lookup"><span data-stu-id="4d72d-141">Click a link in the search result to view the respective employee record.</span></span>  
  
     <span data-ttu-id="4d72d-142">![詳細的員工記錄](../../adapters-and-accelerators/adapter-oracle-ebs/media/36-search-result2.gif "36_Search_Result2")</span><span class="sxs-lookup"><span data-stu-id="4d72d-142">![Detailed employee record](../../adapters-and-accelerators/adapter-oracle-ebs/media/36-search-result2.gif "36_Search_Result2")</span></span>  
  
## <a name="summary"></a><span data-ttu-id="4d72d-143">摘要</span><span class="sxs-lookup"><span data-stu-id="4d72d-143">Summary</span></span>  
 <span data-ttu-id="4d72d-144">在本教學課程中，您可以建立您想要從 SharePoint 入口網站存取 Oracle E-business Suite 成品的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="4d72d-144">In this tutorial, you created a WCF service for the Oracle E-Business Suite artifacts you want to access from a SharePoint Portal.</span></span> <span data-ttu-id="4d72d-145">您也會建立 Oracle E-business Suite 成品的應用程式定義匯入 SharePoint 入口網站來建立及搜尋 Oracle E-business Suite 中的資料呈現的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="4d72d-145">You also created an application definition for the Oracle E-Business Suite artifacts that is imported into a SharePoint portal to create Web Parts to present and search data in Oracle E-Business Suite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d72d-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d72d-146">See Also</span></span>  
 [<span data-ttu-id="4d72d-147">教學課程： 從 SharePoint 網站上的 Oracle E-business Suite 中呈現的資料</span><span class="sxs-lookup"><span data-stu-id="4d72d-147">Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/tutorial-present-data-from-oracle-e-business-suite-on-a-sharepoint-site.md)