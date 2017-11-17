---
title: "步驟 3： 建立 SharePoint 應用程式來擷取 Siebel 資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86bde531-2daf-452b-b3e6-5481d66f72e7
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94537b57a731e5d71459518fcbb0a528b6240d19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel"></a><span data-ttu-id="52cfb-102">步驟 3： 建立 SharePoint 應用程式來擷取 Siebel 資料</span><span class="sxs-lookup"><span data-stu-id="52cfb-102">Step 3: Create a SharePoint Application to Retrieve Data from Siebel</span></span>
<span data-ttu-id="52cfb-103">![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="52cfb-103">![Step 3 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="52cfb-104">**若要完成的時間：** 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="52cfb-104">**Time to complete:** 15 minutes.</span></span>  
  
 <span data-ttu-id="52cfb-105">**目標：**您現在必須採用您建立使用商務資料目錄定義編輯器的應用程式定義檔案，並匯入 Office SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="52cfb-105">**Objective:** You must now take the application definition file you created by using the Business Data Catalog Definition Editor, and import it into Office SharePoint Server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="52cfb-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="52cfb-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="52cfb-107">您應已建立應用程式定義檔中所述[步驟 2： 建立應用程式定義檔的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)。</span><span class="sxs-lookup"><span data-stu-id="52cfb-107">You should have created an application definition file, as described in [Step 2: Create an Application Definition File for Siebel Business Component Operations](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md).</span></span>  
  
-   <span data-ttu-id="52cfb-108">Microsoft Single sign-on 服務必須執行。</span><span class="sxs-lookup"><span data-stu-id="52cfb-108">The Microsoft Single Sign-on service must be running.</span></span>  
  
## <a name="how-to-create-a-sharepoint-application"></a><span data-ttu-id="52cfb-109">如何建立 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="52cfb-109">How to Create a SharePoint Application</span></span>  
 <span data-ttu-id="52cfb-110">建立 SharePoint 應用程式包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="52cfb-110">Creating a SharePoint application involves the following steps:</span></span>  
  
-   <span data-ttu-id="52cfb-111">在 SharePoint 中建立的單一登入 (SSO) 應用程式</span><span class="sxs-lookup"><span data-stu-id="52cfb-111">Create a single sign-on (SSO) application in SharePoint</span></span>  
  
-   <span data-ttu-id="52cfb-112">建立共用的服務提供者 (SSP)</span><span class="sxs-lookup"><span data-stu-id="52cfb-112">Create a Shared Services Provider (SSP)</span></span>  
  
-   <span data-ttu-id="52cfb-113">匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="52cfb-113">Import the application definition file</span></span>  
  
-   <span data-ttu-id="52cfb-114">建立 Web 組件頁面，並加入 Web 組件</span><span class="sxs-lookup"><span data-stu-id="52cfb-114">Create a Web Part page, and add Web Parts</span></span>  
  
## <a name="creating-an-sso-application-in-sharepoint"></a><span data-ttu-id="52cfb-115">在 SharePoint 中建立的 SSO 應用程式</span><span class="sxs-lookup"><span data-stu-id="52cfb-115">Creating an SSO Application in SharePoint</span></span>  
 <span data-ttu-id="52cfb-116">若要在 Siebel 系統中，從 SharePoint 應用程式存取資料，您必須設定對應到 Siebel 使用者的 SharePoint 使用者的 SSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="52cfb-116">To access the data in a Siebel system from a SharePoint application, you must set up an SSO application that maps a SharePoint user to a Siebel user.</span></span> <span data-ttu-id="52cfb-117">在 SharePoint 中建立的 SSO 應用程式包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="52cfb-117">Creating an SSO application in SharePoint involves the following steps:</span></span>  
  
1.  <span data-ttu-id="52cfb-118">**管理伺服器設定的單一登入**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-118">**Manage server settings for single sign-on**.</span></span> <span data-ttu-id="52cfb-119">在此步驟中，您可以指定使用者帳戶可管理和設定單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="52cfb-119">In this step, you specify a user account that can manage and set up the single sign-on service.</span></span> <span data-ttu-id="52cfb-120">您可以從 [管理伺服器設定] 頁面。</span><span class="sxs-lookup"><span data-stu-id="52cfb-120">You can do so from the Manage Server Settings page.</span></span> <span data-ttu-id="52cfb-121">此選項可從 SharePoint 管理中心主控台。</span><span class="sxs-lookup"><span data-stu-id="52cfb-121">This option is available from the SharePoint Central Administration console.</span></span> <span data-ttu-id="52cfb-122">如需這個步驟的詳細資訊，請參閱 「 設定單一登入 Office SharePoint Server 2007 的 」 一節[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。</span><span class="sxs-lookup"><span data-stu-id="52cfb-122">For more information about this step, refer to the “Configure Single Sign-On for Office SharePoint Server 2007” section at [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span></span>  
  
2.  <span data-ttu-id="52cfb-123">**管理企業應用程式定義設定**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-123">**Manage settings for enterprise application definitions**.</span></span> <span data-ttu-id="52cfb-124">在此步驟中，您會設定企業應用程式定義的設定。</span><span class="sxs-lookup"><span data-stu-id="52cfb-124">In this step, you configure the settings for the enterprise application definition.</span></span> <span data-ttu-id="52cfb-125">您可以從企業應用程式定義 頁面上管理設定。</span><span class="sxs-lookup"><span data-stu-id="52cfb-125">You can do so from the Manage Settings for Enterprise Application Definitions page.</span></span> <span data-ttu-id="52cfb-126">此選項可從 SharePoint 管理中心主控台。</span><span class="sxs-lookup"><span data-stu-id="52cfb-126">This option is available from the SharePoint Central Administration console.</span></span>  
  
    1.  <span data-ttu-id="52cfb-127">在 [管理中心] 的上方導覽列上，按一下**作業**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-127">On Central Administration, on the top navigation bar, click **Operations**.</span></span>  
  
    2.  <span data-ttu-id="52cfb-128">在 [作業] 頁面中**安全性組態**區段中，按一下**管理設定單一登入**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-128">On the Operations page, in the **Security Configuration** section, click  **Manage settings for single sign-on**.</span></span>  
  
    3.  <span data-ttu-id="52cfb-129">在 管理的設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理企業應用程式定義設定**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-129">On the Manage Settings for Single Sign-On page, in the **Enterprise Application Definition Settings** section, click **Manage settings for enterprise application definitions**.</span></span>  
  
    4.  <span data-ttu-id="52cfb-130">在 [管理企業應用程式定義] 頁面提供的值**顯示名稱**，**應用程式名稱**，而**連絡電子郵件地址**欄位。</span><span class="sxs-lookup"><span data-stu-id="52cfb-130">On the Manage Enterprise Application Definitions page, provide values for the **Display name**, **Application name**, and the **Contact e-mail address** fields.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="52cfb-131">如**應用程式名稱**欄位中，請確定您指定相同的 SSO 應用程式名稱所指定**SecondarySsoApplicationId**時建立應用程式定義檔中，做為變數中所述[步驟 2： 建立應用程式定義檔的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)。</span><span class="sxs-lookup"><span data-stu-id="52cfb-131">For the **Application name** field, make sure you specify the same SSO application name that you specified for the **SecondarySsoApplicationId** variable while creating the application definition file, as described in [Step 2: Create an Application Definition File for Siebel Business Component Operations](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md).</span></span>  
  
    5.  <span data-ttu-id="52cfb-132">將其他欄位保留為預設值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-132">Leave the other fields as default, and click **OK**.</span></span>  
  
3.  <span data-ttu-id="52cfb-133">**管理企業應用程式定義的帳戶資訊**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-133">**Manage account information for enterprise application definitions**.</span></span> <span data-ttu-id="52cfb-134">在此步驟中，您可以啟用個別使用者或群組，從 SharePoint 連接至企業應用程式。</span><span class="sxs-lookup"><span data-stu-id="52cfb-134">In this step, you enable individual users or groups to connect to an enterprise application from SharePoint.</span></span> <span data-ttu-id="52cfb-135">基本上，在此步驟中您對應個別使用者或群組到使用者在 LOB 系統。</span><span class="sxs-lookup"><span data-stu-id="52cfb-135">Essentially, in this step you map an individual user or group to a user in the LOB system.</span></span> <span data-ttu-id="52cfb-136">您也可以指定要連接至 LOB 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="52cfb-136">You also specify the credentials to connect to the LOB system.</span></span> <span data-ttu-id="52cfb-137">您可以從管理帳戶資訊的企業應用程式定義 頁面。</span><span class="sxs-lookup"><span data-stu-id="52cfb-137">You can do so from Manage Account Information for Enterprise Application Definitions page.</span></span> <span data-ttu-id="52cfb-138">此選項可從 SharePoint 管理中心主控台。</span><span class="sxs-lookup"><span data-stu-id="52cfb-138">This option is available from the SharePoint Central Administration console.</span></span> <span data-ttu-id="52cfb-139">如需這個步驟的詳細資訊，請參閱 「 管理企業應用程式定義的帳戶資訊 」 一節[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。</span><span class="sxs-lookup"><span data-stu-id="52cfb-139">For more information about this step, refer to the “Manage account information for an enterprise application definition” section at [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span></span>  
  
## <a name="creating-a-shared-services-provider"></a><span data-ttu-id="52cfb-140">建立共用的服務提供者</span><span class="sxs-lookup"><span data-stu-id="52cfb-140">Creating a Shared Services Provider</span></span>  
 <span data-ttu-id="52cfb-141">SSP 是共用的服務和其支援資源的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="52cfb-141">An SSP is a logical grouping of shared services and their supporting resources.</span></span> <span data-ttu-id="52cfb-142">您可以建立使用 SharePoint 管理中心主控台 SSP。</span><span class="sxs-lookup"><span data-stu-id="52cfb-142">You can create an SSP using the SharePoint Central Administration console.</span></span>  
  
 <span data-ttu-id="52cfb-143">您必須定義的網站時建立的 ssp。</span><span class="sxs-lookup"><span data-stu-id="52cfb-143">You must define a Web site while creating an SSP.</span></span> <span data-ttu-id="52cfb-144">請記住的連接埠號碼和您所建立的網站位址。</span><span class="sxs-lookup"><span data-stu-id="52cfb-144">Remember the port number and the site address you create.</span></span> <span data-ttu-id="52cfb-145">您將這個網站來匯入商務資料目錄應用程式定義。</span><span class="sxs-lookup"><span data-stu-id="52cfb-145">You will import the Business Data Catalog application definition to this site.</span></span>  
  
 <span data-ttu-id="52cfb-146">如需建立 SSP 的詳細資訊，請參閱 「 章概觀： 建立及設定共用服務提供者 」 在[http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119)。</span><span class="sxs-lookup"><span data-stu-id="52cfb-146">For more information about creating an SSP, see "Chapter overview: Create and configure Shared Services Providers" at [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).</span></span>  
  
## <a name="importing-the-application-definition-file"></a><span data-ttu-id="52cfb-147">匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="52cfb-147">Importing the Application Definition File</span></span>  
 <span data-ttu-id="52cfb-148">您必須立即匯入應用程式定義檔的 ssp。</span><span class="sxs-lookup"><span data-stu-id="52cfb-148">You must now import the application definition file into the SSP.</span></span>  
  
#### <a name="to-import-the-application-definition-file"></a><span data-ttu-id="52cfb-149">若要匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="52cfb-149">To import the application definition file</span></span>  
  
1.  <span data-ttu-id="52cfb-150">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="52cfb-150">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="52cfb-151">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="52cfb-151">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="52cfb-152">在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="52cfb-152">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3.  <span data-ttu-id="52cfb-153">在**商務資料目錄**區段中，按一下**匯入應用程式定義**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-153">In the **Business Data Catalog** section, click **Import application definition**.</span></span>  
  
4.  <span data-ttu-id="52cfb-154">匯入應用程式定義頁面上，開啟時，請瀏覽至 Siebel_Account.xml，選取檔案，然後**開啟**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-154">On the Import Application Definition page that opens, browse to Siebel_Account.xml, select the file, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="52cfb-155">按一下 **[匯入]**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-155">Click **Import**.</span></span>  
  
6.  <span data-ttu-id="52cfb-156">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-156">Click **OK**.</span></span>  
  
 <span data-ttu-id="52cfb-157">匯入後的應用程式，您可以看到您的應用程式，請前往**檢視應用程式**連結。</span><span class="sxs-lookup"><span data-stu-id="52cfb-157">After importing the application, you can see your application by going to the **View Applications** link.</span></span> <span data-ttu-id="52cfb-158">按一下 應用程式名稱，以查看應用程式中的實體。</span><span class="sxs-lookup"><span data-stu-id="52cfb-158">Click the application name to see the entities in the application.</span></span>  
  
## <a name="creating-web-parts"></a><span data-ttu-id="52cfb-159">建立 Web 組件</span><span class="sxs-lookup"><span data-stu-id="52cfb-159">Creating Web Parts</span></span>  
 <span data-ttu-id="52cfb-160">您現在必須建立 Web 組件在 SharePoint 網站來檢視和管理將會擷取來自 Siebel 系統的商務資料。</span><span class="sxs-lookup"><span data-stu-id="52cfb-160">You must now create Web Parts in your SharePoint site to view and manage the business data that will be extracted from the Siebel system.</span></span> <span data-ttu-id="52cfb-161">Web 組件是資訊的可重複使用的元件，可以包含任何一種 Web 架構，包括分析、 共同作業，和資料庫資訊。</span><span class="sxs-lookup"><span data-stu-id="52cfb-161">Web Parts are reusable components that can contain any kind of Web-based information, including analytical, collaborative, and database information.</span></span>  
  
 <span data-ttu-id="52cfb-162">在此教學課程中，Web 組件會建立所建立的商務資料目錄定義編輯器的方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="52cfb-162">In this tutorial, Web Parts are created for the method instances that were created in Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="52cfb-163">Office SharePoint Server 提供特定使用的不同的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="52cfb-163">Office SharePoint Server provides different kinds of Web Parts for specific use.</span></span> <span data-ttu-id="52cfb-164">我們將使用 Finder 方法執行個體，**商務資料清單**Web 組件。</span><span class="sxs-lookup"><span data-stu-id="52cfb-164">For the Finder method instance, we will use the **Business Data List** Web Part.</span></span> <span data-ttu-id="52cfb-165">此 Web 組件可讓您指定帳戶商務元件上執行查詢的搜尋運算式。</span><span class="sxs-lookup"><span data-stu-id="52cfb-165">This Web Part enables you to specify a search expression to perform a query on the Account business component.</span></span> <span data-ttu-id="52cfb-166">此教學課程中，我們稱之為**查詢帳戶**Web 組件。</span><span class="sxs-lookup"><span data-stu-id="52cfb-166">For this tutorial, we call this the **Query Accounts** Web Part.</span></span>  
  
 <span data-ttu-id="52cfb-167">本節提供建立這些 Web 組件的指示。</span><span class="sxs-lookup"><span data-stu-id="52cfb-167">This section provides instructions to create these Web Parts.</span></span> <span data-ttu-id="52cfb-168">建立 Web 組件的詳細資訊，請參閱 Microsoft Office SharePoint Server 2007 文件 （「 自訂商務資料清單、 Web 組件，以及網站 」），網址[http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131)。</span><span class="sxs-lookup"><span data-stu-id="52cfb-168">For more information about creating Web Parts, see the Microsoft Office SharePoint Server 2007 document ("Customize business data lists, Web Parts, and sites") at [http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131).</span></span>  
  
 <span data-ttu-id="52cfb-169">Web 組件將會加入至單一的 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="52cfb-169">The Web Parts will be added to a single Web Part page.</span></span> <span data-ttu-id="52cfb-170">加入 Web 組件之前，您必須建立 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="52cfb-170">You must create a Web Part page before adding the Web Parts.</span></span> <span data-ttu-id="52cfb-171">此教學課程中，會呼叫 Web 組件頁面**Siebel 帳戶**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-171">For this tutorial, the Web Part page is called **Siebel Account**.</span></span>  
  
### <a name="creating-a-web-part-page"></a><span data-ttu-id="52cfb-172">建立網頁組件</span><span class="sxs-lookup"><span data-stu-id="52cfb-172">Creating a Web Part Page</span></span>  
 <span data-ttu-id="52cfb-173">本節提供建立 Web 組件頁面的指示。</span><span class="sxs-lookup"><span data-stu-id="52cfb-173">This section provides instructions to create a Web Part page.</span></span>  
  
##### <a name="to-create-a-web-part-page"></a><span data-ttu-id="52cfb-174">若要建立網頁組件</span><span class="sxs-lookup"><span data-stu-id="52cfb-174">To create a web part page</span></span>  
  
1.  <span data-ttu-id="52cfb-175">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="52cfb-175">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="52cfb-176">按一下**啟動**，指向**所有程式**，指向 [ **Microsoft Office Server**，然後按一下**SharePoint 3.0 管理中心]**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-176">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="52cfb-177">在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="52cfb-177">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3.  <span data-ttu-id="52cfb-178">在 共用服務管理頁面上，從右上角，按一下 **網站動作**，然後按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-178">On the Shared Services Administration page, from the top right-hand corner, click **Site Actions**, and then click **Create**.</span></span>  
  
     <span data-ttu-id="52cfb-179">![若要建立的 web 組件的功能表](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")</span><span class="sxs-lookup"><span data-stu-id="52cfb-179">![Menu to create a web part](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")</span></span>  
  
4.  <span data-ttu-id="52cfb-180">在 [建立] 頁面下**網頁**區段中，按一下**Web 組件頁面**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-180">On the Create page, under the **Web Pages** section, click **Web Part Page**.</span></span>  
  
5.  <span data-ttu-id="52cfb-181">在新增 Web 組件 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="52cfb-181">In the New Web Part page, do the following:</span></span>  
  
    1.  <span data-ttu-id="52cfb-182">在**名稱**欄位中，指定頁面名稱。</span><span class="sxs-lookup"><span data-stu-id="52cfb-182">In the **Name** field, specify a name for the page.</span></span> <span data-ttu-id="52cfb-183">此教學課程中，將名稱指定為`Siebel Account`。</span><span class="sxs-lookup"><span data-stu-id="52cfb-183">For this tutorial, specify the name as `Siebel Account`.</span></span>  
  
    2.  <span data-ttu-id="52cfb-184">選取**檔案已經存在覆寫**核取方塊，如果您想要覆寫舊的頁面，具有相同名稱做為您建立的網頁。</span><span class="sxs-lookup"><span data-stu-id="52cfb-184">Select the **Overwrite if file already exists** check box, if you want to overwrite old pages with the same name as the page you create.</span></span>  
  
    3.  <span data-ttu-id="52cfb-185">在**配置**] 區段中，從**選擇版面配置範本**方塊中，選取 [Web 組件頁面的版面配置。</span><span class="sxs-lookup"><span data-stu-id="52cfb-185">In the **Layout** section, from the **Choose a Layout Template** box, select a layout for the Web Part page.</span></span> <span data-ttu-id="52cfb-186">此教學課程中，選取**整頁、 垂直**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-186">For this tutorial, select **Full Page, Vertical**.</span></span>  
  
    4.  <span data-ttu-id="52cfb-187">在**儲存位置**區段的**文件庫**清單中，選取**表單範本**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-187">In **the Save Location** section, in the **Document Library** list, select **Form Templates**.</span></span>  
  
    5.  <span data-ttu-id="52cfb-188">按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-188">Click **Create**.</span></span> <span data-ttu-id="52cfb-189">只在建立之後下, 圖顯示 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="52cfb-189">The following figure shows a Web Part page after it is just created.</span></span>  
  
         <span data-ttu-id="52cfb-190">![空的 Web 組件頁面](../../adapters-and-accelerators/adapter-siebel/media/1fa218f5-de81-43be-b1b1-c46de422f112.gif "1fa218f5-de81-43be-b1b1-c46de422f112")</span><span class="sxs-lookup"><span data-stu-id="52cfb-190">![Empty Web Part page](../../adapters-and-accelerators/adapter-siebel/media/1fa218f5-de81-43be-b1b1-c46de422f112.gif "1fa218f5-de81-43be-b1b1-c46de422f112")</span></span>  
  
     <span data-ttu-id="52cfb-191">您現在必須將不同的 Web 組件加入此頁面。</span><span class="sxs-lookup"><span data-stu-id="52cfb-191">You must now add the different Web Parts to this page.</span></span>  
  
### <a name="adding-a-business-data-list-web-part"></a><span data-ttu-id="52cfb-192">新增商務資料清單網頁組件</span><span class="sxs-lookup"><span data-stu-id="52cfb-192">Adding a Business Data List Web Part</span></span>  
 <span data-ttu-id="52cfb-193">您現在必須新增 Web 組件頁面的商務資料清單網頁組件。</span><span class="sxs-lookup"><span data-stu-id="52cfb-193">You must now add a Business Data List Web Part to the Web Part page.</span></span> <span data-ttu-id="52cfb-194">使用此 Web 組件，您將查詢帳戶商務元件使用的搜尋運算式。</span><span class="sxs-lookup"><span data-stu-id="52cfb-194">Using this Web Part, you will query the Account business component using a search expression.</span></span> <span data-ttu-id="52cfb-195">此 Web 組件會對應至您在商務資料目錄定義編輯器建立 Finder 方法執行個體 (QueryAccount)。</span><span class="sxs-lookup"><span data-stu-id="52cfb-195">This Web Part corresponds to the Finder method instance (QueryAccount) you created in the Business Data Catalog Definition Editor.</span></span>  
  
##### <a name="to-add-a-business-data-list-web-part"></a><span data-ttu-id="52cfb-196">若要加入商務資料清單網頁組件</span><span class="sxs-lookup"><span data-stu-id="52cfb-196">To add a Business Data List Web Part</span></span>  
  
1.  <span data-ttu-id="52cfb-197">在**Siebel 帳戶**頁面上，於**標頭**區段中，按一下**新增網頁組件**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-197">In the **Siebel Account** page, in the **Header** section, click **Add a Web Part**.</span></span>  
  
2.  <span data-ttu-id="52cfb-198">在**新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料清單**核取方塊，然後**新增**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-198">In the **Add Web Parts** dialog box, in the **Business Data** section, select the **Business Data List** check box, and then click **Add**.</span></span>  
  
     <span data-ttu-id="52cfb-199">![若要建立商務資料 Web 組件的選項](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")</span><span class="sxs-lookup"><span data-stu-id="52cfb-199">![Options to create a business data Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")</span></span>  
  
3.  <span data-ttu-id="52cfb-200">新增商務資料清單 Web 組件中，按一下 **開啟工具窗格**連結。</span><span class="sxs-lookup"><span data-stu-id="52cfb-200">In the newly added Business Data List Web Part, click the **Open the tool pane** link.</span></span>  
  
     <span data-ttu-id="52cfb-201">![Web 組件中開啟工具窗格](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")</span><span class="sxs-lookup"><span data-stu-id="52cfb-201">![Open the tool pane for Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")</span></span>  
  
4.  <span data-ttu-id="52cfb-202">在右窗格中，開啟 [商務資料清單] 工具窗格。</span><span class="sxs-lookup"><span data-stu-id="52cfb-202">The Business Data List tool pane opens in the right pane.</span></span> <span data-ttu-id="52cfb-203">在**商務資料清單** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="52cfb-203">In the **Business Data List** section, for the **Type** field, click the **Browse** button.</span></span>  
  
     <span data-ttu-id="52cfb-204">![商務資料清單 工具窗格](../../adapters-and-accelerators/adapter-siebel/media/3b6e1576-03ce-4fc8-bf5a-7b414ef4408c.gif "3b6e1576-03ce-4fc8-bf5a-7b414ef4408c")</span><span class="sxs-lookup"><span data-stu-id="52cfb-204">![Business Data List tool pane](../../adapters-and-accelerators/adapter-siebel/media/3b6e1576-03ce-4fc8-bf5a-7b414ef4408c.gif "3b6e1576-03ce-4fc8-bf5a-7b414ef4408c")</span></span>  
  
5.  <span data-ttu-id="52cfb-205">在**商務資料型別選擇器**對話方塊中，選取**Siebel_Account_Instance**應用程式，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-205">In the **Business Data Type Picker** dialog box, select the **Siebel_Account_Instance** application, and then click **OK**.</span></span>  
  
     <span data-ttu-id="52cfb-206">![選取的應用程式執行個體](../../adapters-and-accelerators/adapter-siebel/media/a658d06a-83a8-4e4b-9451-ce58e7ac3632.gif "a658d06a-83a8-4e4b-9451-ce58e7ac3632")</span><span class="sxs-lookup"><span data-stu-id="52cfb-206">![Select the application instance](../../adapters-and-accelerators/adapter-siebel/media/a658d06a-83a8-4e4b-9451-ce58e7ac3632.gif "a658d06a-83a8-4e4b-9451-ce58e7ac3632")</span></span>  
  
6.  <span data-ttu-id="52cfb-207">展開**外觀** 節點，然後在**標題**欄位中，指定 Web 組件的標題。</span><span class="sxs-lookup"><span data-stu-id="52cfb-207">Expand the **Appearance** node, and in the **Title** field, specify a title for the Web Part.</span></span> <span data-ttu-id="52cfb-208">此 Web 組件中，指定**帳戶清單**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-208">For this Web Part, specify **Account List**.</span></span>  
  
7.  <span data-ttu-id="52cfb-209">在 商務資料清單 工具窗格中，按一下 **套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="52cfb-209">In the Business Data List tool pane, click **Apply**, and then click **OK**.</span></span> <span data-ttu-id="52cfb-210">商務資料清單網頁組件現在看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="52cfb-210">The Business Data List Web Part now looks like the following:</span></span>  
  
     <span data-ttu-id="52cfb-211">![商務資料清單 」 Web 組件](../../adapters-and-accelerators/adapter-siebel/media/06dbb84a-38c3-4ece-b981-5aa7471909ed.gif "06dbb84a-38c3-4ece-b981-5aa7471909ed")</span><span class="sxs-lookup"><span data-stu-id="52cfb-211">![Business Data List Web Part](../../adapters-and-accelerators/adapter-siebel/media/06dbb84a-38c3-4ece-b981-5aa7471909ed.gif "06dbb84a-38c3-4ece-b981-5aa7471909ed")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="52cfb-212">您也可以變更參數資料行出現的順序。</span><span class="sxs-lookup"><span data-stu-id="52cfb-212">You can also change the order in which the parameter columns appear.</span></span> <span data-ttu-id="52cfb-213">您可以按一下**編輯檢視**靠近右上角 Web 組件的連結。</span><span class="sxs-lookup"><span data-stu-id="52cfb-213">You can do so by clicking the **Edit View** link towards the right corner of the Web Part.</span></span>  
  
8.  <span data-ttu-id="52cfb-214">按一下**結束編輯模式**從頁面的右上角。</span><span class="sxs-lookup"><span data-stu-id="52cfb-214">Click **Exit Edit Mode** from the top right corner of the page.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="52cfb-215">後續步驟</span><span class="sxs-lookup"><span data-stu-id="52cfb-215">Next Steps</span></span>  
 <span data-ttu-id="52cfb-216">從 Siebel 系統擷取資料來測試 SharePoint 應用程式。</span><span class="sxs-lookup"><span data-stu-id="52cfb-216">Test the SharePoint application by retrieving data from a Siebel system.</span></span> <span data-ttu-id="52cfb-217">請參閱[步驟 4： 測試 SharePoint 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/step-4-test-your-sharepoint-application.md)。</span><span class="sxs-lookup"><span data-stu-id="52cfb-217">See [Step 4: Test Your SharePoint Application](../../adapters-and-accelerators/adapter-oracle-ebs/step-4-test-your-sharepoint-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cfb-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52cfb-218">See Also</span></span>  
 [<span data-ttu-id="52cfb-219">教學課程 1： 從 SharePoint 網站上的 Siebel 系統中呈現資料</span><span class="sxs-lookup"><span data-stu-id="52cfb-219">Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)