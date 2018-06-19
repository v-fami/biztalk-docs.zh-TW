---
title: 步驟 4： 測試您的 SharePoint Application1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7ded5a5-88d5-40aa-814b-70bc0a7dcfa3
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b8be51df02bd9796b41201c0495758c281e8f14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216630"
---
# <a name="step-4-test-your-sharepoint-application"></a><span data-ttu-id="6e480-102">步驟 4： 測試 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="6e480-102">Step 4: Test Your SharePoint Application</span></span>
<span data-ttu-id="6e480-103">![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="6e480-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="6e480-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="6e480-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="6e480-105">**目標：** 您 SharePoint 網站中加入 Web 組件，並建立應用程式，您必須測試應用程式擷取從 SAP 系統的一些資料之後。</span><span class="sxs-lookup"><span data-stu-id="6e480-105">**Objective:** After you have added Web Parts in the SharePoint site and created an application, you must test the application by retrieving some data from the SAP system.</span></span> <span data-ttu-id="6e480-106">本主題說明如何使用應用程式從 SAP 系統中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="6e480-106">This topic provides instructions on how to use the application to retrieve the data from the SAP system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6e480-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="6e480-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="6e480-108">您應該建立包含適當的 Web 組件，來擷取商務資料 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="6e480-108">You should have created the Web Part page that contains the appropriate Web Parts to retrieve business data.</span></span> <span data-ttu-id="6e480-109">請參閱[步驟 3： 建立 SharePoint 應用程式來擷取資料，從 SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="6e480-109">See [Step 3: Create a SharePoint Application to Retrieve Data from SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md).</span></span>  
  
### <a name="to-test-the-sharepoint-application"></a><span data-ttu-id="6e480-110">若要測試 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="6e480-110">To test the SharePoint application</span></span>  
  
1.  <span data-ttu-id="6e480-111">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="6e480-111">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="6e480-112">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="6e480-112">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="6e480-113">在左側瀏覽窗格中，按一下您要在其建立應用程式的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="6e480-113">In the left navigation pane, click the name of the SSP under which you created the application.</span></span>  
  
3.  <span data-ttu-id="6e480-114">在左窗格中，按一下 **檢視所有網站內容**。</span><span class="sxs-lookup"><span data-stu-id="6e480-114">In the left pane, click **View All Site Content**.</span></span> <span data-ttu-id="6e480-115">在右窗格中，按一下 **表單範本**。</span><span class="sxs-lookup"><span data-stu-id="6e480-115">In the right pane, click **Form Templates**.</span></span>  
  
4.  <span data-ttu-id="6e480-116">在**表單類別**清單中，按一下**Customer_SalesOrders**。</span><span class="sxs-lookup"><span data-stu-id="6e480-116">In the **Form Category** list, click **Customer_SalesOrders**.</span></span> <span data-ttu-id="6e480-117">當您建立 Web 組件頁面時，您可以指定此名稱。</span><span class="sxs-lookup"><span data-stu-id="6e480-117">You specified this name when you created the Web Part page.</span></span> <span data-ttu-id="6e480-118">下圖顯示您所建立的 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="6e480-118">The following figure shows the Web Part page that you created.</span></span>  
  
     <span data-ttu-id="6e480-119">![已完成的 Web 組件頁面](../../adapters-and-accelerators/adapter-sap/media/3e9f22b1-8285-40f4-a67d-b51173c93671.gif "3e9f22b1-8285-40f4-a67d-b51173c93671")</span><span class="sxs-lookup"><span data-stu-id="6e480-119">![Completed Web Part page](../../adapters-and-accelerators/adapter-sap/media/3e9f22b1-8285-40f4-a67d-b51173c93671.gif "3e9f22b1-8285-40f4-a67d-b51173c93671")</span></span>  
  
5.  <span data-ttu-id="6e480-120">搜尋的搜尋字串為基礎的客戶。</span><span class="sxs-lookup"><span data-stu-id="6e480-120">Search for customers based on a search string.</span></span> <span data-ttu-id="6e480-121">例如，搜尋客戶名稱開頭為"John E"。</span><span class="sxs-lookup"><span data-stu-id="6e480-121">For example, search for customers with names starting with "John E".</span></span> <span data-ttu-id="6e480-122">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="6e480-122">To do so:</span></span>  
  
    1.  <span data-ttu-id="6e480-123">在 客戶清單區段中，從第一個清單中，按一下**CustomerName**。</span><span class="sxs-lookup"><span data-stu-id="6e480-123">In the Customer List section, from the first list, click **CustomerName**.</span></span>  
  
    2.  <span data-ttu-id="6e480-124">從第二個清單中，按一下**開頭**。</span><span class="sxs-lookup"><span data-stu-id="6e480-124">From the second list, click **starts with**.</span></span>  
  
    3.  <span data-ttu-id="6e480-125">在文字方塊中，輸入**John E**。</span><span class="sxs-lookup"><span data-stu-id="6e480-125">In the text box, type **John E**.</span></span>  
  
    4.  <span data-ttu-id="6e480-126">按一下**抓取資料**連結，或按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="6e480-126">Click the **Retrieve Data** link or press ENTER.</span></span> <span data-ttu-id="6e480-127">下圖顯示符合搜尋條件的記錄從 SAP 系統擷取。</span><span class="sxs-lookup"><span data-stu-id="6e480-127">The following figure shows the records retrieved from the SAP system that satisfy the search criteria.</span></span>  
  
         <span data-ttu-id="6e480-128">![搜尋 SAP 系統從結果](../../adapters-and-accelerators/adapter-sap/media/c97e9e2c-0908-46af-9a54-8a4354847c47.gif "c97e9e2c-0908-46af-9a54-8a4354847c47")</span><span class="sxs-lookup"><span data-stu-id="6e480-128">![Search results from the SAP system](../../adapters-and-accelerators/adapter-sap/media/c97e9e2c-0908-46af-9a54-8a4354847c47.gif "c97e9e2c-0908-46af-9a54-8a4354847c47")</span></span>  
  
6.  <span data-ttu-id="6e480-129">您現在可以看到在清單中的任何客戶的詳細資料與銷售訂單的客戶，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="6e480-129">You can now see the details of any customer in the list and the sales orders associated with the customers, if any.</span></span> <span data-ttu-id="6e480-130">若要這樣做，請按一下 [針對客戶編號] 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="6e480-130">To do so, click the option button against a customer number.</span></span> <span data-ttu-id="6e480-131">頁面重新整理呈現和個別的 Web 組件中的特定客戶的銷售訂單的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6e480-131">The page refreshes to present the details and the sales orders for a specific customer in the respective Web Parts.</span></span>  
  
     <span data-ttu-id="6e480-132">![在 SharePoint 上顯示的 SAP 資料](../../adapters-and-accelerators/adapter-sap/media/29fc4a9e-facd-4455-bcfe-5f4d866b2dc7.gif "29fc4a9e-facd-4455-bcfe-5f4d866b2dc7")</span><span class="sxs-lookup"><span data-stu-id="6e480-132">![SAP data presented on SharePoint](../../adapters-and-accelerators/adapter-sap/media/29fc4a9e-facd-4455-bcfe-5f4d866b2dc7.gif "29fc4a9e-facd-4455-bcfe-5f4d866b2dc7")</span></span>  
  
     <span data-ttu-id="6e480-133">如果已正確地顯示客戶及相關聯的銷售訂單的詳細資訊，您已順利完成本教學課程。</span><span class="sxs-lookup"><span data-stu-id="6e480-133">If the details of the customers and the associated sales order are displayed correctly, you have successfully completed the tutorial.</span></span> <span data-ttu-id="6e480-134">如果沒有或不正確的資料會顯示，請仔細檢查您的工作，並確定您正確地執行所有工作。</span><span class="sxs-lookup"><span data-stu-id="6e480-134">If no or incorrect data is displayed, carefully check your work to make sure you performed all the tasks correctly.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="6e480-135">摘要</span><span class="sxs-lookup"><span data-stu-id="6e480-135">Summary</span></span>  
 <span data-ttu-id="6e480-136">在本教學課程，您會建立您想要從 SharePoint 入口網站存取 SAP 成品的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="6e480-136">In this tutorial you created a WCF service for the SAP artifacts you want to access from a SharePoint Portal.</span></span> <span data-ttu-id="6e480-137">您也會建立 SAP 成品的應用程式定義匯入 SharePoint 入口網站來建立 Web 組件來呈現資料的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="6e480-137">You also created an application definition for the SAP artifacts that is imported into a SharePoint portal to create Web Parts to present data from an SAP system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e480-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e480-138">See Also</span></span>  
 [<span data-ttu-id="6e480-139">教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料</span><span class="sxs-lookup"><span data-stu-id="6e480-139">Tutorial 1: Presenting Data from an SAP System on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)