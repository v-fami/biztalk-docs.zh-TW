---
title: 步驟 3： 建立 SharePoint 應用程式來擷取 Siebel 的資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 86bde531-2daf-452b-b3e6-5481d66f72e7
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df6c92b371291f4359c4bbce5e16529700bcc0c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971863"
---
# <a name="step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel"></a><span data-ttu-id="35cc3-102">步驟 3： 建立 SharePoint 應用程式來擷取 Siebel 資料</span><span class="sxs-lookup"><span data-stu-id="35cc3-102">Step 3: Create a SharePoint Application to Retrieve Data from Siebel</span></span>
<span data-ttu-id="35cc3-103">![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="35cc3-103">![Step 3 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="35cc3-104">**若要完成的時間：** 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="35cc3-104">**Time to complete:** 15 minutes.</span></span>  
  
 <span data-ttu-id="35cc3-105">**目標：** 您現在必須使用商務資料目錄定義編輯器中，您建立應用程式定義檔案，然後匯入 Office SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="35cc3-105">**Objective:** You must now take the application definition file you created by using the Business Data Catalog Definition Editor, and import it into Office SharePoint Server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="35cc3-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="35cc3-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="35cc3-107">您應該先建立應用程式定義檔中所述[步驟 2： 建立 Siebel 商務元件操作的應用程式定義檔](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)。</span><span class="sxs-lookup"><span data-stu-id="35cc3-107">You should have created an application definition file, as described in [Step 2: Create an Application Definition File for Siebel Business Component Operations](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md).</span></span>  
  
-   <span data-ttu-id="35cc3-108">必須執行 Microsoft Single sign-on 服務。</span><span class="sxs-lookup"><span data-stu-id="35cc3-108">The Microsoft Single Sign-on service must be running.</span></span>  
  
## <a name="how-to-create-a-sharepoint-application"></a><span data-ttu-id="35cc3-109">如何建立 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="35cc3-109">How to Create a SharePoint Application</span></span>  
 <span data-ttu-id="35cc3-110">建立 SharePoint 應用程式包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="35cc3-110">Creating a SharePoint application involves the following steps:</span></span>  
  
-   <span data-ttu-id="35cc3-111">在 SharePoint 中建立的單一登入 (SSO) 應用程式</span><span class="sxs-lookup"><span data-stu-id="35cc3-111">Create a single sign-on (SSO) application in SharePoint</span></span>  
  
-   <span data-ttu-id="35cc3-112">建立共用的服務提供者 (SSP)</span><span class="sxs-lookup"><span data-stu-id="35cc3-112">Create a Shared Services Provider (SSP)</span></span>  
  
-   <span data-ttu-id="35cc3-113">匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="35cc3-113">Import the application definition file</span></span>  
  
-   <span data-ttu-id="35cc3-114">建立網頁組件頁面上，並新增 Web 組件</span><span class="sxs-lookup"><span data-stu-id="35cc3-114">Create a Web Part page, and add Web Parts</span></span>  
  
## <a name="creating-an-sso-application-in-sharepoint"></a><span data-ttu-id="35cc3-115">在 SharePoint 中建立的 SSO 應用程式</span><span class="sxs-lookup"><span data-stu-id="35cc3-115">Creating an SSO Application in SharePoint</span></span>  
 <span data-ttu-id="35cc3-116">若要在 Siebel 系統中，從 SharePoint 應用程式存取資料，您必須設定對應到 Siebel 使用者的 SharePoint 使用者的 SSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="35cc3-116">To access the data in a Siebel system from a SharePoint application, you must set up an SSO application that maps a SharePoint user to a Siebel user.</span></span> <span data-ttu-id="35cc3-117">在 SharePoint 中建立的 SSO 應用程式包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="35cc3-117">Creating an SSO application in SharePoint involves the following steps:</span></span>  
  
1.  <span data-ttu-id="35cc3-118">**管理伺服器設定單一登入**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-118">**Manage server settings for single sign-on**.</span></span> <span data-ttu-id="35cc3-119">在此步驟中，您可以指定使用者帳戶可管理和設定單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="35cc3-119">In this step, you specify a user account that can manage and set up the single sign-on service.</span></span> <span data-ttu-id="35cc3-120">您可以從管理伺服器設定 頁面來這麼做。</span><span class="sxs-lookup"><span data-stu-id="35cc3-120">You can do so from the Manage Server Settings page.</span></span> <span data-ttu-id="35cc3-121">此選項可從 SharePoint 管理中心 的主控台。</span><span class="sxs-lookup"><span data-stu-id="35cc3-121">This option is available from the SharePoint Central Administration console.</span></span> <span data-ttu-id="35cc3-122">如需此步驟的詳細資訊，請參閱 「 設定單一登入 Office SharePoint server 2007 」 一節[ http://go.microsoft.com/fwlink/?LinkId=105291 ](http://go.microsoft.com/fwlink/?LinkId=105291)。</span><span class="sxs-lookup"><span data-stu-id="35cc3-122">For more information about this step, refer to the “Configure Single Sign-On for Office SharePoint Server 2007” section at [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span></span>  
  
2.  <span data-ttu-id="35cc3-123">**管理企業應用程式定義的設定**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-123">**Manage settings for enterprise application definitions**.</span></span> <span data-ttu-id="35cc3-124">在此步驟中，您可以設定企業應用程式定義的設定。</span><span class="sxs-lookup"><span data-stu-id="35cc3-124">In this step, you configure the settings for the enterprise application definition.</span></span> <span data-ttu-id="35cc3-125">您可以從企業應用程式定義 頁面上的管理設定來這麼做。</span><span class="sxs-lookup"><span data-stu-id="35cc3-125">You can do so from the Manage Settings for Enterprise Application Definitions page.</span></span> <span data-ttu-id="35cc3-126">此選項可從 SharePoint 管理中心 的主控台。</span><span class="sxs-lookup"><span data-stu-id="35cc3-126">This option is available from the SharePoint Central Administration console.</span></span>  
  
    1.  <span data-ttu-id="35cc3-127">在 [管理中心] 的上方導覽列中，按一下**作業**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-127">On Central Administration, on the top navigation bar, click **Operations**.</span></span>  
  
    2.  <span data-ttu-id="35cc3-128">在 [作業] 頁面中，在**安全性設定**區段中，按一下**管理設定單一登入**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-128">On the Operations page, in the **Security Configuration** section, click  **Manage settings for single sign-on**.</span></span>  
  
    3.  <span data-ttu-id="35cc3-129">在 管理設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理企業應用程式定義的設定**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-129">On the Manage Settings for Single Sign-On page, in the **Enterprise Application Definition Settings** section, click **Manage settings for enterprise application definitions**.</span></span>  
  
    4.  <span data-ttu-id="35cc3-130">在管理企業應用程式定義 頁面上，針對提供的值**顯示名稱**，**應用程式名稱**，而**連絡人電子郵件地址**欄位。</span><span class="sxs-lookup"><span data-stu-id="35cc3-130">On the Manage Enterprise Application Definitions page, provide values for the **Display name**, **Application name**, and the **Contact e-mail address** fields.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="35cc3-131">針對**應用程式名稱**欄位中，請確定您指定您為指定的相同 SSO 應用程式名稱**SecondarySsoApplicationId**時建立應用程式定義檔中，做為變數中所述[步驟 2： 建立 Siebel 商務元件操作的應用程式定義檔](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)。</span><span class="sxs-lookup"><span data-stu-id="35cc3-131">For the **Application name** field, make sure you specify the same SSO application name that you specified for the **SecondarySsoApplicationId** variable while creating the application definition file, as described in [Step 2: Create an Application Definition File for Siebel Business Component Operations](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md).</span></span>  
  
    5.  <span data-ttu-id="35cc3-132">將其他欄位保留為預設值，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-132">Leave the other fields as default, and click **OK**.</span></span>  
  
3.  <span data-ttu-id="35cc3-133">**管理企業應用程式定義的帳戶資訊**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-133">**Manage account information for enterprise application definitions**.</span></span> <span data-ttu-id="35cc3-134">在此步驟中，您可以啟用個別使用者或群組，從 SharePoint 連接到企業應用程式。</span><span class="sxs-lookup"><span data-stu-id="35cc3-134">In this step, you enable individual users or groups to connect to an enterprise application from SharePoint.</span></span> <span data-ttu-id="35cc3-135">基本上，在此步驟中對應的個別使用者或群組到使用者 LOB 系統中。</span><span class="sxs-lookup"><span data-stu-id="35cc3-135">Essentially, in this step you map an individual user or group to a user in the LOB system.</span></span> <span data-ttu-id="35cc3-136">您也可以指定要連接至 LOB 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="35cc3-136">You also specify the credentials to connect to the LOB system.</span></span> <span data-ttu-id="35cc3-137">則可以從 [管理帳戶資訊的企業應用程式定義] 頁面。</span><span class="sxs-lookup"><span data-stu-id="35cc3-137">You can do so from Manage Account Information for Enterprise Application Definitions page.</span></span> <span data-ttu-id="35cc3-138">此選項可從 SharePoint 管理中心 的主控台。</span><span class="sxs-lookup"><span data-stu-id="35cc3-138">This option is available from the SharePoint Central Administration console.</span></span> <span data-ttu-id="35cc3-139">如需有關此步驟的詳細資訊，請參閱的 「 管理企業應用程式定義的帳戶資訊 」 一節[ http://go.microsoft.com/fwlink/?LinkId=105291 ](http://go.microsoft.com/fwlink/?LinkId=105291)。</span><span class="sxs-lookup"><span data-stu-id="35cc3-139">For more information about this step, refer to the “Manage account information for an enterprise application definition” section at [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span></span>  
  
## <a name="creating-a-shared-services-provider"></a><span data-ttu-id="35cc3-140">建立共用的服務提供者</span><span class="sxs-lookup"><span data-stu-id="35cc3-140">Creating a Shared Services Provider</span></span>  
 <span data-ttu-id="35cc3-141">SSP 是共用的服務和其支援的資源的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="35cc3-141">An SSP is a logical grouping of shared services and their supporting resources.</span></span> <span data-ttu-id="35cc3-142">您可以建立使用 SharePoint 中央系統管理主控台的 SSP。</span><span class="sxs-lookup"><span data-stu-id="35cc3-142">You can create an SSP using the SharePoint Central Administration console.</span></span>  
  
 <span data-ttu-id="35cc3-143">您必須定義網站時建立的 ssp。</span><span class="sxs-lookup"><span data-stu-id="35cc3-143">You must define a Web site while creating an SSP.</span></span> <span data-ttu-id="35cc3-144">請記得連接埠號碼和您所建立的網站位址。</span><span class="sxs-lookup"><span data-stu-id="35cc3-144">Remember the port number and the site address you create.</span></span> <span data-ttu-id="35cc3-145">您會將商務資料目錄應用程式定義匯入此站台。</span><span class="sxs-lookup"><span data-stu-id="35cc3-145">You will import the Business Data Catalog application definition to this site.</span></span>  
  
 <span data-ttu-id="35cc3-146">如需建立 SSP 的詳細資訊，請參閱 「 章概觀： 建立及設定共用服務提供者 」 在[ http://go.microsoft.com/fwlink/?LinkId=105119 ](http://go.microsoft.com/fwlink/?LinkId=105119)。</span><span class="sxs-lookup"><span data-stu-id="35cc3-146">For more information about creating an SSP, see "Chapter overview: Create and configure Shared Services Providers" at [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).</span></span>  
  
## <a name="importing-the-application-definition-file"></a><span data-ttu-id="35cc3-147">匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="35cc3-147">Importing the Application Definition File</span></span>  
 <span data-ttu-id="35cc3-148">您必須立即將應用程式定義檔案匯入的 ssp。</span><span class="sxs-lookup"><span data-stu-id="35cc3-148">You must now import the application definition file into the SSP.</span></span>  
  
#### <a name="to-import-the-application-definition-file"></a><span data-ttu-id="35cc3-149">若要匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="35cc3-149">To import the application definition file</span></span>  
  
1. <span data-ttu-id="35cc3-150">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="35cc3-150">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="35cc3-151">按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="35cc3-151">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2. <span data-ttu-id="35cc3-152">在左側的導覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="35cc3-152">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3. <span data-ttu-id="35cc3-153">在 **商務資料目錄**區段中，按一下**匯入應用程式定義**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-153">In the **Business Data Catalog** section, click **Import application definition**.</span></span>  
  
4. <span data-ttu-id="35cc3-154">匯入應用程式定義在開啟頁面上，瀏覽至 Siebel_Account.xml，選取檔案，然後**開啟**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-154">On the Import Application Definition page that opens, browse to Siebel_Account.xml, select the file, and then click **Open**.</span></span>  
  
5. <span data-ttu-id="35cc3-155">按一下 **[匯入]**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-155">Click **Import**.</span></span>  
  
6. <span data-ttu-id="35cc3-156">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="35cc3-156">Click **OK**.</span></span>  
  
   <span data-ttu-id="35cc3-157">匯入後應用程式，您可以看到您的應用程式，方法是前往**檢視應用程式**連結。</span><span class="sxs-lookup"><span data-stu-id="35cc3-157">After importing the application, you can see your application by going to the **View Applications** link.</span></span> <span data-ttu-id="35cc3-158">按一下 若要查看應用程式中的實體的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="35cc3-158">Click the application name to see the entities in the application.</span></span>  
  
## <a name="creating-web-parts"></a><span data-ttu-id="35cc3-159">建立 Web 組件</span><span class="sxs-lookup"><span data-stu-id="35cc3-159">Creating Web Parts</span></span>  
 <span data-ttu-id="35cc3-160">您現在必須建立 Web 組件在 SharePoint 網站來檢視和管理會擷取來自 Siebel 系統的商務資料。</span><span class="sxs-lookup"><span data-stu-id="35cc3-160">You must now create Web Parts in your SharePoint site to view and manage the business data that will be extracted from the Siebel system.</span></span> <span data-ttu-id="35cc3-161">Web 組件是資訊的可重複使用的元件，可以包含任何一種 Web 架構，包括分析、 共同作業和資料庫資訊。</span><span class="sxs-lookup"><span data-stu-id="35cc3-161">Web Parts are reusable components that can contain any kind of Web-based information, including analytical, collaborative, and database information.</span></span>  
  
 <span data-ttu-id="35cc3-162">在本教學課程中，Web 組件會針對所建立的商務資料目錄定義編輯器的方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="35cc3-162">In this tutorial, Web Parts are created for the method instances that were created in Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="35cc3-163">Office SharePoint Server 提供針對特定用途的不同類型的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="35cc3-163">Office SharePoint Server provides different kinds of Web Parts for specific use.</span></span> <span data-ttu-id="35cc3-164">我們將使用 Finder 方法執行個體，**商務資料清單**Web 組件。</span><span class="sxs-lookup"><span data-stu-id="35cc3-164">For the Finder method instance, we will use the **Business Data List** Web Part.</span></span> <span data-ttu-id="35cc3-165">此 Web 組件可讓您指定帳戶的商務元件上執行查詢的搜尋運算式。</span><span class="sxs-lookup"><span data-stu-id="35cc3-165">This Web Part enables you to specify a search expression to perform a query on the Account business component.</span></span> <span data-ttu-id="35cc3-166">本教學課程中，我們稱之為**查詢帳戶**Web 組件。</span><span class="sxs-lookup"><span data-stu-id="35cc3-166">For this tutorial, we call this the **Query Accounts** Web Part.</span></span>  
  
 <span data-ttu-id="35cc3-167">本節中的指示來建立這些 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="35cc3-167">This section provides instructions to create these Web Parts.</span></span> <span data-ttu-id="35cc3-168">建立 Web 組件的詳細資訊，請參閱 Microsoft Office SharePoint Server 2007 文件 （「 自訂商務資料清單、 Web 組件，以及網站 」），網址[ http://go.microsoft.com/fwlink/?LinkId=104131 ](http://go.microsoft.com/fwlink/?LinkId=104131)。</span><span class="sxs-lookup"><span data-stu-id="35cc3-168">For more information about creating Web Parts, see the Microsoft Office SharePoint Server 2007 document ("Customize business data lists, Web Parts, and sites") at [http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131).</span></span>  
  
 <span data-ttu-id="35cc3-169">Web 組件會加入一個單一的 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="35cc3-169">The Web Parts will be added to a single Web Part page.</span></span> <span data-ttu-id="35cc3-170">您必須新增網頁組件之前建立的 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="35cc3-170">You must create a Web Part page before adding the Web Parts.</span></span> <span data-ttu-id="35cc3-171">本教學課程中，呼叫網頁組件頁面**Siebel 帳戶**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-171">For this tutorial, the Web Part page is called **Siebel Account**.</span></span>  
  
### <a name="creating-a-web-part-page"></a><span data-ttu-id="35cc3-172">建立網頁組件</span><span class="sxs-lookup"><span data-stu-id="35cc3-172">Creating a Web Part Page</span></span>  
 <span data-ttu-id="35cc3-173">本節中的指示來建立網頁組件頁面。</span><span class="sxs-lookup"><span data-stu-id="35cc3-173">This section provides instructions to create a Web Part page.</span></span>  
  
##### <a name="to-create-a-web-part-page"></a><span data-ttu-id="35cc3-174">若要建立網頁組件</span><span class="sxs-lookup"><span data-stu-id="35cc3-174">To create a web part page</span></span>  
  
1. <span data-ttu-id="35cc3-175">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="35cc3-175">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="35cc3-176">按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下**SharePoint 3.0 管理中心**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-176">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and click **SharePoint 3.0 Central Administration**.</span></span>  
  
2. <span data-ttu-id="35cc3-177">在左側的導覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="35cc3-177">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3. <span data-ttu-id="35cc3-178">在 共用服務管理頁面上，從右上角，按一下 **站台動作**，然後按一下**建立**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-178">On the Shared Services Administration page, from the top right-hand corner, click **Site Actions**, and then click **Create**.</span></span>  
  
    <span data-ttu-id="35cc3-179">![若要建立的 web 組件 功能表](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")</span><span class="sxs-lookup"><span data-stu-id="35cc3-179">![Menu to create a web part](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")</span></span>  
  
4. <span data-ttu-id="35cc3-180">在 [建立] 頁面下**網頁**區段中，按一下**網頁組件頁面**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-180">On the Create page, under the **Web Pages** section, click **Web Part Page**.</span></span>  
  
5. <span data-ttu-id="35cc3-181">在 [新增網頁組件] 頁面中，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="35cc3-181">In the New Web Part page, do the following:</span></span>  
  
   1. <span data-ttu-id="35cc3-182">在 **名稱**欄位中，指定頁面的名稱。</span><span class="sxs-lookup"><span data-stu-id="35cc3-182">In the **Name** field, specify a name for the page.</span></span> <span data-ttu-id="35cc3-183">本教學課程中，將名稱指定為`Siebel Account`。</span><span class="sxs-lookup"><span data-stu-id="35cc3-183">For this tutorial, specify the name as `Siebel Account`.</span></span>  
  
   2. <span data-ttu-id="35cc3-184">選取 **覆寫，如果檔案已經存在**核取方塊，如果您想要覆寫舊的畫面與您建立的網頁名稱相同。</span><span class="sxs-lookup"><span data-stu-id="35cc3-184">Select the **Overwrite if file already exists** check box, if you want to overwrite old pages with the same name as the page you create.</span></span>  
  
   3. <span data-ttu-id="35cc3-185">在 **版面配置**區段中，從**選擇版面配置範本**方塊中，選取 Web 組件頁面的版面配置。</span><span class="sxs-lookup"><span data-stu-id="35cc3-185">In the **Layout** section, from the **Choose a Layout Template** box, select a layout for the Web Part page.</span></span> <span data-ttu-id="35cc3-186">本教學課程中，選取**完整的頁面上，垂直**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-186">For this tutorial, select **Full Page, Vertical**.</span></span>  
  
   4. <span data-ttu-id="35cc3-187">在 **儲存的位置**區段中**文件庫**清單中，選取**表單範本**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-187">In **the Save Location** section, in the **Document Library** list, select **Form Templates**.</span></span>  
  
   5. <span data-ttu-id="35cc3-188">按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-188">Click **Create**.</span></span> <span data-ttu-id="35cc3-189">只要在建立之後下, 圖會顯示 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="35cc3-189">The following figure shows a Web Part page after it is just created.</span></span>  
  
       <span data-ttu-id="35cc3-190">![空的 Web 組件頁面](../../adapters-and-accelerators/adapter-siebel/media/1fa218f5-de81-43be-b1b1-c46de422f112.gif "1fa218f5-de81-43be-b1b1-c46de422f112")</span><span class="sxs-lookup"><span data-stu-id="35cc3-190">![Empty Web Part page](../../adapters-and-accelerators/adapter-siebel/media/1fa218f5-de81-43be-b1b1-c46de422f112.gif "1fa218f5-de81-43be-b1b1-c46de422f112")</span></span>  
  
      <span data-ttu-id="35cc3-191">您現在必須在此頁面中新增不同的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="35cc3-191">You must now add the different Web Parts to this page.</span></span>  
  
### <a name="adding-a-business-data-list-web-part"></a><span data-ttu-id="35cc3-192">新增商務資料清單網頁組件</span><span class="sxs-lookup"><span data-stu-id="35cc3-192">Adding a Business Data List Web Part</span></span>  
 <span data-ttu-id="35cc3-193">您現在必須新增網頁組件頁面的商務資料清單 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="35cc3-193">You must now add a Business Data List Web Part to the Web Part page.</span></span> <span data-ttu-id="35cc3-194">您將使用此 Web 組件，來查詢帳戶商務元件使用的搜尋運算式。</span><span class="sxs-lookup"><span data-stu-id="35cc3-194">Using this Web Part, you will query the Account business component using a search expression.</span></span> <span data-ttu-id="35cc3-195">此 Web 組件會對應至您所建立的商務資料目錄定義編輯器 Finder 方法執行個體 (QueryAccount)。</span><span class="sxs-lookup"><span data-stu-id="35cc3-195">This Web Part corresponds to the Finder method instance (QueryAccount) you created in the Business Data Catalog Definition Editor.</span></span>  
  
##### <a name="to-add-a-business-data-list-web-part"></a><span data-ttu-id="35cc3-196">若要將商務資料清單 Web 組件</span><span class="sxs-lookup"><span data-stu-id="35cc3-196">To add a Business Data List Web Part</span></span>  
  
1.  <span data-ttu-id="35cc3-197">在  **Siebel 帳戶**頁面上，於**標頭**區段中，按一下**新增網頁組件**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-197">In the **Siebel Account** page, in the **Header** section, click **Add a Web Part**.</span></span>  
  
2.  <span data-ttu-id="35cc3-198">在 **新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料清單**核取方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-198">In the **Add Web Parts** dialog box, in the **Business Data** section, select the **Business Data List** check box, and then click **Add**.</span></span>  
  
     <span data-ttu-id="35cc3-199">![若要建立商務資料 Web 組件的選項](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")</span><span class="sxs-lookup"><span data-stu-id="35cc3-199">![Options to create a business data Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")</span></span>  
  
3.  <span data-ttu-id="35cc3-200">新增商務資料清單 Web 組件中，按一下**開啟 [工具] 窗格**連結。</span><span class="sxs-lookup"><span data-stu-id="35cc3-200">In the newly added Business Data List Web Part, click the **Open the tool pane** link.</span></span>  
  
     <span data-ttu-id="35cc3-201">![Web 組件中開啟工具窗格](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")</span><span class="sxs-lookup"><span data-stu-id="35cc3-201">![Open the tool pane for Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")</span></span>  
  
4.  <span data-ttu-id="35cc3-202">在右窗格中，開啟 [商務資料清單] 工具窗格。</span><span class="sxs-lookup"><span data-stu-id="35cc3-202">The Business Data List tool pane opens in the right pane.</span></span> <span data-ttu-id="35cc3-203">在**商務資料清單**區段中，如**型別**欄位中，按一下**瀏覽** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="35cc3-203">In the **Business Data List** section, for the **Type** field, click the **Browse** button.</span></span>  
  
     <span data-ttu-id="35cc3-204">![商務資料清單 工具窗格](../../adapters-and-accelerators/adapter-siebel/media/3b6e1576-03ce-4fc8-bf5a-7b414ef4408c.gif "3b6e1576-03ce-4fc8-bf5a-7b414ef4408c")</span><span class="sxs-lookup"><span data-stu-id="35cc3-204">![Business Data List tool pane](../../adapters-and-accelerators/adapter-siebel/media/3b6e1576-03ce-4fc8-bf5a-7b414ef4408c.gif "3b6e1576-03ce-4fc8-bf5a-7b414ef4408c")</span></span>  
  
5.  <span data-ttu-id="35cc3-205">在 **商務資料型別選擇器**對話方塊中，選取**Siebel_Account_Instance**應用程式，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-205">In the **Business Data Type Picker** dialog box, select the **Siebel_Account_Instance** application, and then click **OK**.</span></span>  
  
     <span data-ttu-id="35cc3-206">![選取的應用程式執行個體](../../adapters-and-accelerators/adapter-siebel/media/a658d06a-83a8-4e4b-9451-ce58e7ac3632.gif "a658d06a-83a8-4e4b-9451-ce58e7ac3632")</span><span class="sxs-lookup"><span data-stu-id="35cc3-206">![Select the application instance](../../adapters-and-accelerators/adapter-siebel/media/a658d06a-83a8-4e4b-9451-ce58e7ac3632.gif "a658d06a-83a8-4e4b-9451-ce58e7ac3632")</span></span>  
  
6.  <span data-ttu-id="35cc3-207">依序展開**外觀**節點，然後在**標題**欄位中，指定 Web 組件的標題。</span><span class="sxs-lookup"><span data-stu-id="35cc3-207">Expand the **Appearance** node, and in the **Title** field, specify a title for the Web Part.</span></span> <span data-ttu-id="35cc3-208">此 Web 組件中，指定**Account List**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-208">For this Web Part, specify **Account List**.</span></span>  
  
7.  <span data-ttu-id="35cc3-209">在 商務資料清單 工具窗格中，按一下 **套用**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="35cc3-209">In the Business Data List tool pane, click **Apply**, and then click **OK**.</span></span> <span data-ttu-id="35cc3-210">商務資料清單 Web 組件現在看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="35cc3-210">The Business Data List Web Part now looks like the following:</span></span>  
  
     <span data-ttu-id="35cc3-211">![商務資料清單 」 Web 組件](../../adapters-and-accelerators/adapter-siebel/media/06dbb84a-38c3-4ece-b981-5aa7471909ed.gif "06dbb84a-38c3-4ece-b981-5aa7471909ed")</span><span class="sxs-lookup"><span data-stu-id="35cc3-211">![Business Data List Web Part](../../adapters-and-accelerators/adapter-siebel/media/06dbb84a-38c3-4ece-b981-5aa7471909ed.gif "06dbb84a-38c3-4ece-b981-5aa7471909ed")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35cc3-212">您也可以變更參數資料行出現的順序。</span><span class="sxs-lookup"><span data-stu-id="35cc3-212">You can also change the order in which the parameter columns appear.</span></span> <span data-ttu-id="35cc3-213">您可以這樣做，即可**編輯檢視**往右上角的 網頁組件的連結。</span><span class="sxs-lookup"><span data-stu-id="35cc3-213">You can do so by clicking the **Edit View** link towards the right corner of the Web Part.</span></span>  
  
8.  <span data-ttu-id="35cc3-214">按一下 **結束編輯模式**從頁面的右上角。</span><span class="sxs-lookup"><span data-stu-id="35cc3-214">Click **Exit Edit Mode** from the top right corner of the page.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="35cc3-215">後續步驟</span><span class="sxs-lookup"><span data-stu-id="35cc3-215">Next Steps</span></span>  
 <span data-ttu-id="35cc3-216">擷取 Siebel 系統中的資料來測試 SharePoint 應用程式。</span><span class="sxs-lookup"><span data-stu-id="35cc3-216">Test the SharePoint application by retrieving data from a Siebel system.</span></span> <span data-ttu-id="35cc3-217">請參閱[步驟 4： 測試 SharePoint 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/step-4-test-your-sharepoint-application.md)。</span><span class="sxs-lookup"><span data-stu-id="35cc3-217">See [Step 4: Test Your SharePoint Application](../../adapters-and-accelerators/adapter-oracle-ebs/step-4-test-your-sharepoint-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35cc3-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35cc3-218">See Also</span></span>  
 [<span data-ttu-id="35cc3-219">教學課程 1：在 SharePoint 網站上呈現 Siebel 系統的資料</span><span class="sxs-lookup"><span data-stu-id="35cc3-219">Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)