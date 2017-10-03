---
title: "步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eaa16011-9284-4ccf-8132-9c1e14cc6aa7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fe9d6fc34fa039bb4b3861deb35fb51524180ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-e-business-suite"></a><span data-ttu-id="8b68c-102">步驟 3： 建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料</span><span class="sxs-lookup"><span data-stu-id="8b68c-102">Step 3: Create a SharePoint application to retrieve data from Oracle E-Business Suite</span></span>
<span data-ttu-id="8b68c-103">![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="8b68c-103">![Step 3 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="8b68c-104">**若要完成的時間：** 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="8b68c-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="8b68c-105">**目標：**您現在必須匯入應用程式定義檔，在 Microsoft Office SharePoint Server 中，並在設定應用程式來擷取 Oracle E-business Suite 中的資料。</span><span class="sxs-lookup"><span data-stu-id="8b68c-105">**Objective:** You must now import the application definition file in Microsoft Office SharePoint Server, and set up an application to retrieve data from Oracle E-Business Suite.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8b68c-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="8b68c-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="8b68c-107">您應已建立的應用程式定義檔中所述[步驟 2： 建立應用程式定義檔的 Oracle E-business Suite 成品](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="8b68c-107">You should have created an application definition file as described in [Step 2: Create an Application Definition File for the Oracle E-Business Suite Artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md).</span></span>  
  
-   <span data-ttu-id="8b68c-108">Microsoft Single sign-on 服務必須執行。</span><span class="sxs-lookup"><span data-stu-id="8b68c-108">The Microsoft Single Sign-on service must be running.</span></span>  
  
 
  
##  <span data-ttu-id="8b68c-109"><a name="SSO"></a>在 SharePoint 中建立的 SSO 應用程式</span><span class="sxs-lookup"><span data-stu-id="8b68c-109"><a name="SSO"></a> Creating an SSO Application in SharePoint</span></span>  
 <span data-ttu-id="8b68c-110">若要從 SharePoint 應用程式存取 Oracle E-business Suite 中的資料，您必須設定 Oracle E-business Suite 使用者對應的 SharePoint 使用者的 SSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8b68c-110">To access the data in Oracle E-Business Suite from a SharePoint application, you must set up an SSO application that maps a SharePoint user to an Oracle E-Business Suite user.</span></span> <span data-ttu-id="8b68c-111">在 SharePoint 中建立的 SSO 應用程式包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8b68c-111">Creating an SSO application in SharePoint involves the following steps:</span></span>  
  
1.  <span data-ttu-id="8b68c-112">**管理伺服器設定的單一登入**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-112">**Manage server settings for single sign-on**.</span></span> <span data-ttu-id="8b68c-113">在此步驟中，您可以指定使用者帳戶可管理和設定單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="8b68c-113">In this step, you specify a user account that can manage and set up the single sign-on service.</span></span> <span data-ttu-id="8b68c-114">您可以在 [管理伺服器設定] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="8b68c-114">You can do so on the Manage Server Settings page.</span></span> <span data-ttu-id="8b68c-115">此選項可從 SharePoint 管理中心主控台。</span><span class="sxs-lookup"><span data-stu-id="8b68c-115">This option is available from the SharePoint Central Administration console.</span></span> <span data-ttu-id="8b68c-116">如需這個步驟的詳細資訊，請參閱 「 設定單一登入 Office SharePoint Server 2007 的 」 一節[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。</span><span class="sxs-lookup"><span data-stu-id="8b68c-116">For more information about this step, refer to the “Configure Single Sign-On for Office SharePoint Server 2007” section at [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span></span>  
  
2.  <span data-ttu-id="8b68c-117">**管理企業應用程式定義設定**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-117">**Manage settings for enterprise application definitions**.</span></span> <span data-ttu-id="8b68c-118">在此步驟中，您會設定企業應用程式定義的設定。</span><span class="sxs-lookup"><span data-stu-id="8b68c-118">In this step, you configure the settings for the enterprise application definition.</span></span> <span data-ttu-id="8b68c-119">您可以從企業應用程式定義 頁面上管理設定。</span><span class="sxs-lookup"><span data-stu-id="8b68c-119">You can do so from the Manage Settings for Enterprise Application Definitions page.</span></span> <span data-ttu-id="8b68c-120">此選項可從 SharePoint 管理中心主控台。</span><span class="sxs-lookup"><span data-stu-id="8b68c-120">This option is available from the SharePoint Central Administration console.</span></span>  
  
    1.  <span data-ttu-id="8b68c-121">在 [管理中心] 的上方導覽列上，按一下**作業**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-121">On Central Administration, on the top navigation bar, click **Operations**.</span></span>  
  
    2.  <span data-ttu-id="8b68c-122">在 [作業] 頁面中**安全性組態**區段中，按一下**管理設定單一登入**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-122">On the Operations page, in the **Security Configuration** section, click  **Manage settings for single sign-on**.</span></span>  
  
    3.  <span data-ttu-id="8b68c-123">在 管理的設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理企業應用程式定義設定**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-123">On the Manage Settings for Single Sign-On page, in the **Enterprise Application Definition Settings** section, click **Manage settings for enterprise application definitions**.</span></span>  
  
    4.  <span data-ttu-id="8b68c-124">在 [管理企業應用程式定義] 頁面提供的值**顯示名稱**，**應用程式名稱**，而**連絡電子郵件地址**欄位。</span><span class="sxs-lookup"><span data-stu-id="8b68c-124">On the Manage Enterprise Application Definitions page, provide values for the **Display name**, **Application name**, and the **Contact e-mail address** fields.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="8b68c-125">如**應用程式名稱**欄位中，請確定您指定相同的 SSO 應用程式名稱所指定**SecondarySsoApplicationId**時建立應用程式定義檔中，做為變數中所述[步驟 2： 建立應用程式定義檔的 Oracle E-business Suite 成品](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="8b68c-125">For the **Application name** field, make sure you specify the same SSO application name that you specified for the **SecondarySsoApplicationId** variable while creating the application definition file, as described in [Step 2: Create an Application Definition File for the Oracle E-Business Suite Artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md).</span></span>  
  
    5.  <span data-ttu-id="8b68c-126">將其他欄位保留為預設值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-126">Leave the other fields as default, and click **OK**.</span></span>  
  
3.  <span data-ttu-id="8b68c-127">**管理企業應用程式定義的帳戶資訊**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-127">**Manage account information for enterprise application definitions**.</span></span> <span data-ttu-id="8b68c-128">在此步驟中，您可以啟用個別使用者或群組，從 SharePoint 連接至企業應用程式。</span><span class="sxs-lookup"><span data-stu-id="8b68c-128">In this step, you enable individual users or groups to connect to an enterprise application from SharePoint.</span></span> <span data-ttu-id="8b68c-129">基本上，在此步驟中您對應個別使用者或群組到使用者在 LOB 系統。</span><span class="sxs-lookup"><span data-stu-id="8b68c-129">Essentially, in this step you map an individual user or group to a user in the LOB system.</span></span> <span data-ttu-id="8b68c-130">您也可以指定要連接至 LOB 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="8b68c-130">You also specify the credentials to connect to the LOB system.</span></span> <span data-ttu-id="8b68c-131">您可以從企業應用程式定義 頁面上的管理帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="8b68c-131">You can do so from the Manage Account Information for Enterprise Application Definitions page.</span></span> <span data-ttu-id="8b68c-132">此選項可從 SharePoint 管理中心主控台。</span><span class="sxs-lookup"><span data-stu-id="8b68c-132">This option is available from the SharePoint Central Administration console.</span></span> <span data-ttu-id="8b68c-133">如需這個步驟的詳細資訊，請參閱 「 管理企業應用程式定義的帳戶資訊 」 一節[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。</span><span class="sxs-lookup"><span data-stu-id="8b68c-133">For more information about this step, refer to the “Manage account information for an enterprise application definition” section at [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span></span>  
  
##  <span data-ttu-id="8b68c-134"><a name="SSP"></a>建立共用的服務提供者</span><span class="sxs-lookup"><span data-stu-id="8b68c-134"><a name="SSP"></a> Creating a Shared Services Provider</span></span>  
 <span data-ttu-id="8b68c-135">共用服務提供者是共用的服務和其支援資源的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="8b68c-135">A Shared Service Provider is a logical grouping of shared services and their supporting resources.</span></span> <span data-ttu-id="8b68c-136">您可以使用 SharePoint 管理中心主控台，以建立 SSP。</span><span class="sxs-lookup"><span data-stu-id="8b68c-136">You can create an SSP by using the SharePoint Central Administration console.</span></span>  
  
 <span data-ttu-id="8b68c-137">建立 SSP 時，您必須定義的網站</span><span class="sxs-lookup"><span data-stu-id="8b68c-137">You must define a Web site when creating an SSP.</span></span> <span data-ttu-id="8b68c-138">請記住的連接埠號碼和您所建立的網站位址。</span><span class="sxs-lookup"><span data-stu-id="8b68c-138">Remember the port number and the site address that you create.</span></span> <span data-ttu-id="8b68c-139">您將這個網站來匯入商務資料目錄應用程式定義。</span><span class="sxs-lookup"><span data-stu-id="8b68c-139">You will import the Business Data Catalog application definition to this site.</span></span>  
  
 <span data-ttu-id="8b68c-140">如需建立 SSP 的詳細資訊，請參閱 「 章概觀： 建立及設定共用服務提供者 」 在[http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119)。</span><span class="sxs-lookup"><span data-stu-id="8b68c-140">For more information about creating an SSP, see "Chapter overview: Create and configure Shared Services Providers" at [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).</span></span>  
  
##  <span data-ttu-id="8b68c-141"><a name="Import"></a>匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="8b68c-141"><a name="Import"></a> Importing the Application Definition File</span></span>  
 <span data-ttu-id="8b68c-142">您必須立即匯入應用程式定義檔的 ssp。</span><span class="sxs-lookup"><span data-stu-id="8b68c-142">You must now import the application definition file into the SSP.</span></span>  
  
#### <a name="to-import-the-application-definition-file"></a><span data-ttu-id="8b68c-143">若要匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="8b68c-143">To import the application definition file</span></span>  
  
1.  <span data-ttu-id="8b68c-144">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="8b68c-144">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="8b68c-145">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="8b68c-145">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="8b68c-146">在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="8b68c-146">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3.  <span data-ttu-id="8b68c-147">在**商務資料目錄**區段中，按一下**匯入應用程式定義**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-147">In the **Business Data Catalog** section, click **Import application definition**.</span></span>  
  
4.  <span data-ttu-id="8b68c-148">匯入應用程式定義頁面上，開啟時，請瀏覽至 Employee.xml，選取檔案，然後**開啟**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-148">On the Import Application Definition page that opens, browse to Employee.xml, select the file, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="8b68c-149">按一下 **[匯入]**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-149">Click **Import**.</span></span>  
  
6.  <span data-ttu-id="8b68c-150">應用程式定義檔匯入成功後，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="8b68c-150">After the application definition file is imported successfully, click **OK**.</span></span>  
  
     <span data-ttu-id="8b68c-151">因為匯入應用程式定義檔，MS_SAMPLE_EMPLOYEE，建立的應用程式會出現。</span><span class="sxs-lookup"><span data-stu-id="8b68c-151">The application created as a result of importing the application definition file, MS_SAMPLE_EMPLOYEE, appears.</span></span>  
  
     <span data-ttu-id="8b68c-152">![在 SharePoint 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/media/b0695720-0113-49dc-8eb6-c685aceada6c.gif "b0695720-0113-49dc-8eb6-c685aceada6c")</span><span class="sxs-lookup"><span data-stu-id="8b68c-152">![The application in SharePoint](../../adapters-and-accelerators/adapter-oracle-ebs/media/b0695720-0113-49dc-8eb6-c685aceada6c.gif "b0695720-0113-49dc-8eb6-c685aceada6c")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8b68c-153">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8b68c-153">Next Steps</span></span>  
 <span data-ttu-id="8b68c-154">現在，您就準備好要建立 Web 組件來建立 SharePoint 網站，以檢視及搜尋會從 Oracle E-business Suite 擷取商務資料。</span><span class="sxs-lookup"><span data-stu-id="8b68c-154">Now, you are ready to create Web Parts to create a SharePoint site to view and search the business data that will be extracted from Oracle E-Business Suite.</span></span> <span data-ttu-id="8b68c-155">我們將建立 a:</span><span class="sxs-lookup"><span data-stu-id="8b68c-155">We will create a:</span></span>  
  
-   <span data-ttu-id="8b68c-156">商務資料清單網頁組件顯示 MS_SAMPLE_EMPLOYEE 介面資料表中的員工記錄。</span><span class="sxs-lookup"><span data-stu-id="8b68c-156">Business Data List Web Part to display employee records from the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="8b68c-157">請參閱[案例 1： 使用商務資料清單網頁組件顯示資料](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md)。</span><span class="sxs-lookup"><span data-stu-id="8b68c-157">See [Scenario 1: Display Data Using Business Data List Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-1-display-data-using-business-data-list-web-part.md).</span></span>  
  
-   <span data-ttu-id="8b68c-158">搜尋方塊 」 Web 組件 MS_SAMPLE_EMPLOYEE 介面資料表上執行全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="8b68c-158">Search Box Web Part to perform a full-text search on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="8b68c-159">請參閱[案例 2： 使用搜尋方塊 」 Web 組件搜尋](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md)。</span><span class="sxs-lookup"><span data-stu-id="8b68c-159">See [Scenario 2: Search Using the Search Box Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/scenario-2-search-using-the-search-box-web-part.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b68c-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b68c-160">See Also</span></span>  
 [<span data-ttu-id="8b68c-161">教學課程： 從 SharePoint 網站上的 Oracle E-business Suite 中呈現的資料</span><span class="sxs-lookup"><span data-stu-id="8b68c-161">Tutorial: Present Data from Oracle E-Business Suite on a SharePoint Site</span></span>](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)