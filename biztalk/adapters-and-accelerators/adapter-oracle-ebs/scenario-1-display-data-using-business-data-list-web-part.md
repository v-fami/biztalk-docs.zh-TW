---
title: "案例 1： 使用商務資料清單網頁組件的資料顯示。 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3831814-8b70-4352-b22f-cebd08750ef5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1add974ca3ad0b80b7838b120920f4de47f1650
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-1-display-data-using-business-data-list-web-part"></a><span data-ttu-id="284d5-102">案例 1： 使用商務資料清單網頁組件的顯示資料</span><span class="sxs-lookup"><span data-stu-id="284d5-102">Scenario 1: Display data using Business Data List web part</span></span>
<span data-ttu-id="284d5-103">我們將使用**商務資料清單**Web 組件**Finder**方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="284d5-103">We will use the **Business Data List** Web Part for the **Finder** method instance.</span></span> <span data-ttu-id="284d5-104">此 Web 組件可讓您指定搜尋運算式來擷取 Oracle E-business Suite 中的員工清單。</span><span class="sxs-lookup"><span data-stu-id="284d5-104">This Web Part enables you to specify a search expression to retrieve a list of employees from Oracle E-Business Suite.</span></span> <span data-ttu-id="284d5-105">此教學課程中，這稱為顯示員工 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="284d5-105">For this tutorial, this is called the Display Employees Web Part.</span></span> <span data-ttu-id="284d5-106">本節提供指示來建立此 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="284d5-106">This section provides instructions to create this Web Part.</span></span> <span data-ttu-id="284d5-107">如需建立 Web 組件的詳細資訊，請參閱 < 自訂商務資料清單、 Web 組件和站台 」 在[http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131)。</span><span class="sxs-lookup"><span data-stu-id="284d5-107">For more information about creating Web Parts, see "Customize business data lists, Web Parts, and sites" at [http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131).</span></span>  
  
 <span data-ttu-id="284d5-108">加入 Web 組件之前，您必須建立 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="284d5-108">You must create a Web Part page before adding the Web Parts.</span></span>  
  
## <a name="creating-a-web-part-page"></a><span data-ttu-id="284d5-109">建立網頁組件</span><span class="sxs-lookup"><span data-stu-id="284d5-109">Creating a Web Part Page</span></span>  
 <span data-ttu-id="284d5-110">本節提供建立 Web 組件頁面的指示。</span><span class="sxs-lookup"><span data-stu-id="284d5-110">This section provides instructions to create a Web Part page.</span></span>  
  
###  <a name="WebPart"></a><span data-ttu-id="284d5-111">若要建立 Web 組件頁面</span><span class="sxs-lookup"><span data-stu-id="284d5-111">To create a Web Part page</span></span>  
  
1.  <span data-ttu-id="284d5-112">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="284d5-112">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="284d5-113">按一下**啟動**，指向**所有程式**，指向 [ **Microsoft Office Server**，然後按一下**SharePoint 3.0 管理中心]**。</span><span class="sxs-lookup"><span data-stu-id="284d5-113">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="284d5-114">在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="284d5-114">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3.  <span data-ttu-id="284d5-115">在右上角的 共用服務管理 頁面上，按一下 **網站動作**，然後按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="284d5-115">On the Shared Services Administration page, in the upper-right corner, click **Site Actions**, and then click **Create**.</span></span>  
  
     <span data-ttu-id="284d5-116">![若要建立的 web 組件的功能表](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")</span><span class="sxs-lookup"><span data-stu-id="284d5-116">![Menu to create a web part](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")</span></span>  
  
4.  <span data-ttu-id="284d5-117">在 [建立] 頁面中**網頁**區段中，按一下**Web 組件頁面**。</span><span class="sxs-lookup"><span data-stu-id="284d5-117">On the Create page, in the **Web Pages** section, click **Web Part Page**.</span></span>  
  
5.  <span data-ttu-id="284d5-118">在新的 Web 組件 頁面上，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="284d5-118">On the New Web Part page, do the following:</span></span>  
  
    1.  <span data-ttu-id="284d5-119">在**名稱**欄位中，輸入頁面的名稱。</span><span class="sxs-lookup"><span data-stu-id="284d5-119">In the **Name** field, type a name for the page.</span></span> <span data-ttu-id="284d5-120">此教學課程中，輸入相同的名稱。 **MS_SAMPLE_EMPLOYEE**。</span><span class="sxs-lookup"><span data-stu-id="284d5-120">For this tutorial, type the name as **MS_SAMPLE_EMPLOYEE**.</span></span>  
  
    2.  <span data-ttu-id="284d5-121">選取**檔案已經存在覆寫**核取方塊，如果您想要覆寫舊的頁面，與您建立新的頁面名稱相同。</span><span class="sxs-lookup"><span data-stu-id="284d5-121">Select the **Overwrite if file already exists** check box, if you want to overwrite old pages with the same name as the new page you create.</span></span>  
  
    3.  <span data-ttu-id="284d5-122">在**配置**] 區段中，從**選擇版面配置範本**方塊中，選取 [Web 組件頁面的版面配置。</span><span class="sxs-lookup"><span data-stu-id="284d5-122">In the **Layout** section, from the **Choose a Layout Template** box, select a layout for the Web Part page.</span></span> <span data-ttu-id="284d5-123">此教學課程中，選取**整頁、 垂直**。</span><span class="sxs-lookup"><span data-stu-id="284d5-123">For this tutorial, select **Full Page, Vertical**.</span></span>  
  
    4.  <span data-ttu-id="284d5-124">在**儲存位置**區段的**文件庫**清單中，按一下**表單範本**。</span><span class="sxs-lookup"><span data-stu-id="284d5-124">In the **Save Location** section, in the **Document Library** list, click **Form Templates**.</span></span>  
  
    5.  <span data-ttu-id="284d5-125">按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="284d5-125">Click **Create**.</span></span> <span data-ttu-id="284d5-126">在建立後下, 圖顯示 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="284d5-126">The following figure shows the Web Part page after it is created.</span></span>  
  
         <span data-ttu-id="284d5-127">![新的 WebPart 頁面](../../adapters-and-accelerators/adapter-oracle-ebs/media/23-web-part.gif "23_Web_Part")</span><span class="sxs-lookup"><span data-stu-id="284d5-127">![The new WebPart page](../../adapters-and-accelerators/adapter-oracle-ebs/media/23-web-part.gif "23_Web_Part")</span></span>  
  
    6.  <span data-ttu-id="284d5-128">您現在必須將 Web 組件加入此頁面。</span><span class="sxs-lookup"><span data-stu-id="284d5-128">You must now add the Web Parts to this page.</span></span>  
  
## <a name="adding-a-business-data-list-web-part"></a><span data-ttu-id="284d5-129">新增商務資料清單網頁組件</span><span class="sxs-lookup"><span data-stu-id="284d5-129">Adding a Business Data List Web Part</span></span>  
 <span data-ttu-id="284d5-130">您現在必須新增 Web 組件頁面的商務資料清單網頁組件。</span><span class="sxs-lookup"><span data-stu-id="284d5-130">You must now add a Business Data List Web Part to the Web Part page.</span></span> <span data-ttu-id="284d5-131">使用此 Web 組件會擷取員工記錄的清單，從 MS_SAMPLE_EMPLOYEE 介面資料表中符合搜尋運算式的 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="284d5-131">Using this Web Part you will retrieve a list of employee records from the MS_SAMPLE_EMPLOYEE interface table in Oracle E-Business Suite that matches a search expression.</span></span> <span data-ttu-id="284d5-132">此 Web 組件會對應至**Finder**方法執行個體 (*Finder_Instance*) 建立的商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="284d5-132">This Web Part corresponds to the **Finder** method instance (*Finder_Instance*) that you created in the Business Data Catalog Definition Editor.</span></span>  
  
#### <a name="to-add-a-business-data-list-web-part"></a><span data-ttu-id="284d5-133">若要加入商務資料清單網頁組件</span><span class="sxs-lookup"><span data-stu-id="284d5-133">To add a Business Data List Web Part</span></span>  
  
1.  <span data-ttu-id="284d5-134">在 MS_SAMPLE_EMPLOYEE] 頁面上，按一下 [**新增網頁組件**。</span><span class="sxs-lookup"><span data-stu-id="284d5-134">On the MS_SAMPLE_EMPLOYEE page, click **Add a Web Part**.</span></span>  
  
2.  <span data-ttu-id="284d5-135">在**新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料清單**核取方塊，然後**新增**。</span><span class="sxs-lookup"><span data-stu-id="284d5-135">In the **Add Web Parts** dialog box, in the **Business Data** section, select the **Business Data List** check box, and then click **Add**.</span></span>  
  
     <span data-ttu-id="284d5-136">![若要建立商務資料 Web 組件的選項](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")</span><span class="sxs-lookup"><span data-stu-id="284d5-136">![Options to create a business data Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")</span></span>  
  
3.  <span data-ttu-id="284d5-137">新增商務資料清單 Web 組件中，按一下 **開啟工具窗格**連結。</span><span class="sxs-lookup"><span data-stu-id="284d5-137">In the newly added Business Data List Web Part, click the **Open the tool pane** link.</span></span>  
  
     <span data-ttu-id="284d5-138">![Web 組件中開啟工具窗格](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")</span><span class="sxs-lookup"><span data-stu-id="284d5-138">![Open the tool pane for Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")</span></span>  
  
4.  <span data-ttu-id="284d5-139">在右窗格中，開啟 [商務資料清單] 工具窗格。</span><span class="sxs-lookup"><span data-stu-id="284d5-139">The Business Data List tool pane opens in the right pane.</span></span> <span data-ttu-id="284d5-140">在**商務資料清單** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="284d5-140">In the **Business Data List** section, for the **Type** field, click the **Browse** button.</span></span>  
  
     <span data-ttu-id="284d5-141">![商務資料清單 工具窗格](../../adapters-and-accelerators/adapter-oracle-ebs/media/24-bdc-browse.gif "24_BDC_Browse")</span><span class="sxs-lookup"><span data-stu-id="284d5-141">![Business Data List tool pane](../../adapters-and-accelerators/adapter-oracle-ebs/media/24-bdc-browse.gif "24_BDC_Browse")</span></span>  
  
5.  <span data-ttu-id="284d5-142">在**商務資料型別選擇器**對話方塊中，選取**MS_SAMPLE_EMPLOYEE_Instance**應用程式，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="284d5-142">In the **Business Data Type Picker** dialog box, select the **MS_SAMPLE_EMPLOYEE_Instance** application, and then click **OK**.</span></span>  
  
     <span data-ttu-id="284d5-143">![選取的應用程式執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/25-bdc-picker.gif "25_BDC_Picker")</span><span class="sxs-lookup"><span data-stu-id="284d5-143">![Select the application instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/25-bdc-picker.gif "25_BDC_Picker")</span></span>  
  
6.  <span data-ttu-id="284d5-144">展開**外觀** 節點，然後在**標題**方塊中，輸入 Web 組件的標題。</span><span class="sxs-lookup"><span data-stu-id="284d5-144">Expand the **Appearance** node, and in the **Title** box, type a title for the Web Part.</span></span> <span data-ttu-id="284d5-145">此 Web 組件中，輸入**員工清單**。</span><span class="sxs-lookup"><span data-stu-id="284d5-145">For this Web Part, type **Employee List**.</span></span>  
  
7.  <span data-ttu-id="284d5-146">在 商務資料清單 工具窗格中，按一下 **套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="284d5-146">In the Business Data List tool pane, click **Apply**, and then click **OK**.</span></span> <span data-ttu-id="284d5-147">商務資料清單網頁組件現在看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="284d5-147">The Business Data List Web Part now looks like the following:</span></span>  
  
     <span data-ttu-id="284d5-148">![商務資料清單 」 Web 組件](../../adapters-and-accelerators/adapter-oracle-ebs/media/26-bdc-webpart.gif "26_BDC_WebPart")</span><span class="sxs-lookup"><span data-stu-id="284d5-148">![Business Data List Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/26-bdc-webpart.gif "26_BDC_WebPart")</span></span>  
  
8.  <span data-ttu-id="284d5-149">Web 組件會列出執行 MS_SAMPLE_EMPLOYEE 介面資料表的 Select 作業所傳回的欄位。</span><span class="sxs-lookup"><span data-stu-id="284d5-149">The Web Part lists the fields that are returned by executing the Select operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="284d5-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="284d5-150">See Also</span></span>  
 <span data-ttu-id="284d5-151">[步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md) </span><span class="sxs-lookup"><span data-stu-id="284d5-151">[Step 3: Create a SharePoint Application to Retrieve Data from Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md) </span></span>  
 [<span data-ttu-id="284d5-152">使用搜尋方塊 」 Web 組件搜尋案例 2:</span><span class="sxs-lookup"><span data-stu-id="284d5-152">Scenario 2: Search Using the Search Box Web Part</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md)