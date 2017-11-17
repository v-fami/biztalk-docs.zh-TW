---
title: "步驟 4： 測試 SharePoint 應用程式使用 Siebel 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec1392fa-fdc1-42be-b4dc-75a55d8fa400
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85cebcafcdf768686ed3f7382a0838db5062d96b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-your-sharepoint-application-with-the-siebel-adapter"></a><span data-ttu-id="8fe76-102">步驟 4： 測試 SharePoint 應用程式使用 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="8fe76-102">Step 4: Test Your SharePoint Application with the Siebel adapter</span></span>
<span data-ttu-id="8fe76-103">![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="8fe76-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="8fe76-104">**若要完成的時間：** 5 分鐘。</span><span class="sxs-lookup"><span data-stu-id="8fe76-104">**Time to complete:** 5 minutes.</span></span>  
  
 <span data-ttu-id="8fe76-105">**目標：**您 SharePoint 網站中加入 Web 組件，並建立應用程式，您必須測試應用程式擷取來自 Siebel 系統的一些資料之後。</span><span class="sxs-lookup"><span data-stu-id="8fe76-105">**Objective:** After you have added Web Parts in the SharePoint site and created an application, you must test the application by retrieving some data from the Siebel system.</span></span> <span data-ttu-id="8fe76-106">本節提供有關如何使用來自 Siebel 系統擷取資料的應用程式的指示。</span><span class="sxs-lookup"><span data-stu-id="8fe76-106">This section provides instructions on how to use the application to retrieve the data from the Siebel system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8fe76-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="8fe76-107">Prerequisites</span></span>  
 <span data-ttu-id="8fe76-108">您應該建立包含適當的 Web 組件，來擷取商務資料的 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="8fe76-108">You should have created the Web Part page containing the appropriate Web Parts to retrieve business data.</span></span> <span data-ttu-id="8fe76-109">請參閱[步驟 3： 建立 SharePoint 應用程式資料擷取 Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md)。</span><span class="sxs-lookup"><span data-stu-id="8fe76-109">See [Step 3: Create a SharePoint Application to Retrieve Data from Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md).</span></span>  
  
### <a name="to-test-the-sharepoint-application"></a><span data-ttu-id="8fe76-110">若要測試 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="8fe76-110">To test the SharePoint application</span></span>  
  
1.  <span data-ttu-id="8fe76-111">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="8fe76-111">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="8fe76-112">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="8fe76-112">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="8fe76-113">在左側瀏覽窗格中，按一下您要在其建立應用程式的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="8fe76-113">In the left navigation pane, click the name of the SSP under which you created the application.</span></span>  
  
3.  <span data-ttu-id="8fe76-114">在左窗格中，按一下 **檢視所有網站內容**。</span><span class="sxs-lookup"><span data-stu-id="8fe76-114">In the left pane, click **View All Site Content**.</span></span> <span data-ttu-id="8fe76-115">從右窗格中，按一下**表單範本**。</span><span class="sxs-lookup"><span data-stu-id="8fe76-115">From the right pane, click **Form Templates**.</span></span>  
  
4.  <span data-ttu-id="8fe76-116">在**表單類別**清單中，按一下**Siebel 帳戶**。</span><span class="sxs-lookup"><span data-stu-id="8fe76-116">In the **Form Category** list, click **Siebel Account**.</span></span> <span data-ttu-id="8fe76-117">您建立 Web 組件頁面時指定此名稱。</span><span class="sxs-lookup"><span data-stu-id="8fe76-117">You specified this name while creating the Web Part page.</span></span> <span data-ttu-id="8fe76-118">下圖顯示您所建立的 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="8fe76-118">The following figure shows the Web Part page that you created.</span></span>  
  
     <span data-ttu-id="8fe76-119">![已完成的 Web 組件頁面](../../adapters-and-accelerators/adapter-siebel/media/a0bfe7af-0246-4f0b-aa0d-0ee084456003.gif "a0bfe7af-0246-4f0b-aa0d-0ee084456003")</span><span class="sxs-lookup"><span data-stu-id="8fe76-119">![Completed Web Part page](../../adapters-and-accelerators/adapter-siebel/media/a0bfe7af-0246-4f0b-aa0d-0ee084456003.gif "a0bfe7af-0246-4f0b-aa0d-0ee084456003")</span></span>  
  
5.  <span data-ttu-id="8fe76-120">查詢搜尋字串為基礎的商務帳戶元件。</span><span class="sxs-lookup"><span data-stu-id="8fe76-120">Query the Account business component based on a search string.</span></span> <span data-ttu-id="8fe76-121">例如，指定搜尋運算式`[Name] LIKE ‘W*’`。</span><span class="sxs-lookup"><span data-stu-id="8fe76-121">For example, specify the search expression `[Name] LIKE ‘W*’`.</span></span> <span data-ttu-id="8fe76-122">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="8fe76-122">To do so:</span></span>  
  
    1.  <span data-ttu-id="8fe76-123">在**帳戶清單**區段中的，從第一個清單中，選取**SearchExpression**，然後選取**等於**。</span><span class="sxs-lookup"><span data-stu-id="8fe76-123">In the **Account List** section, from the first list, select **SearchExpression**, and then select **is equal to**.</span></span>  
  
    2.  <span data-ttu-id="8fe76-124">在文字欄位中，輸入`[Name] LIKE ‘W*’`。</span><span class="sxs-lookup"><span data-stu-id="8fe76-124">In the text field, type `[Name] LIKE ‘W*’`.</span></span>  
  
    3.  <span data-ttu-id="8fe76-125">按一下**抓取資料**連結，或按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="8fe76-125">Click **Retrieve Data** link, or press ENTER.</span></span> <span data-ttu-id="8fe76-126">下圖顯示符合搜尋條件的記錄擷取來自 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="8fe76-126">The following figure shows the records retrieved from the Siebel system that satisfy the search criteria.</span></span>  
  
         <span data-ttu-id="8fe76-127">![搜尋結果來自 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/media/6c4721ac-c7bc-4626-9ee0-55cf322026cf.gif "6c4721ac-c7bc-4626-9ee0-55cf322026cf")</span><span class="sxs-lookup"><span data-stu-id="8fe76-127">![Search results from the Siebel system](../../adapters-and-accelerators/adapter-siebel/media/6c4721ac-c7bc-4626-9ee0-55cf322026cf.gif "6c4721ac-c7bc-4626-9ee0-55cf322026cf")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe76-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fe76-128">See Also</span></span>  
 [<span data-ttu-id="8fe76-129">教學課程 1： 從 SharePoint 網站上的 Siebel 系統中呈現資料</span><span class="sxs-lookup"><span data-stu-id="8fe76-129">Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)