---
title: 步驟 3： 建立 SharePoint 應用程式來擷取 SAP 資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO application, creating an
- Business Data Catalog Definition Editor
- application definition file, importing
- Web Part
- SSP
- Web Part page, creating a
- Shared Services Provider, creating a
ms.assetid: 7158caec-9dc0-477c-9db3-179e634e5196
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 879a4b48da7645471e53db357f7c0a6260117f99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22219534"
---
# <a name="step-3-create-a-sharepoint-application-to-retrieve-data-from-sap"></a><span data-ttu-id="f72ba-102">步驟 3： 建立 SharePoint 應用程式來擷取 SAP 資料</span><span class="sxs-lookup"><span data-stu-id="f72ba-102">Step 3: Create a SharePoint Application to Retrieve Data from SAP</span></span>
<span data-ttu-id="f72ba-103">![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="f72ba-103">![Step 3 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="f72ba-104">**若要完成的時間：** 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="f72ba-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="f72ba-105">**目標：** 您現在必須接受使用 「 商務資料目錄定義編輯器 」 工具，您建立的應用程式定義檔，並匯入 Microsoft Office SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="f72ba-105">**Objective:** You must now take the application definition file that you created by using the Business Data Catalog Definition Editor tool, and import it into Microsoft Office SharePoint Server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f72ba-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="f72ba-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="f72ba-107">您應已建立的應用程式定義檔中所述[步驟 2： 建立應用程式定義檔 SAP 成品](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="f72ba-107">You should have created an application definition file as described in [Step 2: Create an Application Definition File for the SAP Artifacts](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md).</span></span>  
  
-   <span data-ttu-id="f72ba-108">Microsoft Single sign-on 服務必須執行。</span><span class="sxs-lookup"><span data-stu-id="f72ba-108">The Microsoft Single Sign-on service must be running.</span></span>  
  
## <a name="how-to-create-a-sharepoint-application"></a><span data-ttu-id="f72ba-109">如何建立 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="f72ba-109">How to Create a SharePoint Application</span></span>  
 <span data-ttu-id="f72ba-110">建立 SharePoint 應用程式包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f72ba-110">Creating a SharePoint application involves the following steps:</span></span>  
  
-   <span data-ttu-id="f72ba-111">在 SharePoint 中建立的單一登入 (SSO) 應用程式</span><span class="sxs-lookup"><span data-stu-id="f72ba-111">Create a single sign-on (SSO) application in SharePoint</span></span>  
  
-   <span data-ttu-id="f72ba-112">建立共用服務提供者</span><span class="sxs-lookup"><span data-stu-id="f72ba-112">Create a Shared Services provider</span></span>  
  
-   <span data-ttu-id="f72ba-113">匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="f72ba-113">Import the application definition file</span></span>  
  
-   <span data-ttu-id="f72ba-114">建立 Web 組件頁面，並加入 Web 組件</span><span class="sxs-lookup"><span data-stu-id="f72ba-114">Create a Web Part page, and add Web Parts</span></span>  
  
 <span data-ttu-id="f72ba-115">本主題示範如何執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="f72ba-115">This topic demonstrates how to perform these steps.</span></span>  
  
## <a name="creating-an-sso-application-in-sharepoint"></a><span data-ttu-id="f72ba-116">在 SharePoint 中建立的 SSO 應用程式</span><span class="sxs-lookup"><span data-stu-id="f72ba-116">Creating an SSO Application in SharePoint</span></span>  
 <span data-ttu-id="f72ba-117">若要存取 SAP 系統從 SharePoint 應用程式中的資料，您必須設定 SAP 使用者對應的 SharePoint 使用者的 SSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f72ba-117">To access the data in an SAP system from a SharePoint application, you must set up an SSO application that maps a SharePoint user to an SAP user.</span></span> <span data-ttu-id="f72ba-118">在 SharePoint 中建立的 SSO 應用程式包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f72ba-118">Creating an SSO application in SharePoint involves the following steps:</span></span>  
  
1.  <span data-ttu-id="f72ba-119">**管理伺服器設定的單一登入**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-119">**Manage server settings for single sign-on**.</span></span> <span data-ttu-id="f72ba-120">在此步驟中，您可以指定使用者帳戶可管理和設定單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="f72ba-120">In this step, you specify a user account that can manage and set up the single sign-on service.</span></span> <span data-ttu-id="f72ba-121">您可以在 [管理伺服器設定] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="f72ba-121">You can do so on the Manage Server Settings page.</span></span> <span data-ttu-id="f72ba-122">此選項可從 SharePoint 管理中心主控台。</span><span class="sxs-lookup"><span data-stu-id="f72ba-122">This option is available from the SharePoint Central Administration console.</span></span> <span data-ttu-id="f72ba-123">如需這個步驟的詳細資訊，請參閱 「 設定單一登入 Office SharePoint Server 2007 的 」 一節[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。</span><span class="sxs-lookup"><span data-stu-id="f72ba-123">For more information about this step, refer to the “Configure Single Sign-On for Office SharePoint Server 2007” section at [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span></span>  
  
2.  <span data-ttu-id="f72ba-124">**管理企業應用程式定義設定**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-124">**Manage settings for enterprise application definitions**.</span></span> <span data-ttu-id="f72ba-125">在此步驟中，您會設定企業應用程式定義的設定。</span><span class="sxs-lookup"><span data-stu-id="f72ba-125">In this step, you configure the settings for the enterprise application definition.</span></span> <span data-ttu-id="f72ba-126">您可以從企業應用程式定義 頁面上管理設定。</span><span class="sxs-lookup"><span data-stu-id="f72ba-126">You can do so from the Manage Settings for Enterprise Application Definitions page.</span></span> <span data-ttu-id="f72ba-127">此選項可從 SharePoint 管理中心主控台。</span><span class="sxs-lookup"><span data-stu-id="f72ba-127">This option is available from the SharePoint Central Administration console.</span></span>  
  
    1.  <span data-ttu-id="f72ba-128">在 [管理中心] 的上方導覽列上，按一下**作業**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-128">On Central Administration, on the top navigation bar, click **Operations**.</span></span>  
  
    2.  <span data-ttu-id="f72ba-129">在 [作業] 頁面中**安全性組態**區段中，按一下**管理設定單一登入**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-129">On the Operations page, in the **Security Configuration** section, click  **Manage settings for single sign-on**.</span></span>  
  
    3.  <span data-ttu-id="f72ba-130">在 管理的設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理企業應用程式定義設定**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-130">On the Manage Settings for Single Sign-On page, in the **Enterprise Application Definition Settings** section, click **Manage settings for enterprise application definitions**.</span></span>  
  
    4.  <span data-ttu-id="f72ba-131">在 [管理企業應用程式定義] 頁面提供的值**顯示名稱**，**應用程式名稱**，而**連絡電子郵件地址**欄位。</span><span class="sxs-lookup"><span data-stu-id="f72ba-131">On the Manage Enterprise Application Definitions page, provide values for the **Display name**, **Application name**, and the **Contact e-mail address** fields.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="f72ba-132">如**應用程式名稱**欄位中，請確定您指定相同的 SSO 應用程式名稱所指定**SecondarySsoApplicationId**時建立應用程式定義檔中，做為變數中所述[步驟 2： 建立應用程式定義檔 SAP 成品](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="f72ba-132">For the **Application name** field, make sure you specify the same SSO application name that you specified for the **SecondarySsoApplicationId** variable while creating the application definition file, as described in [Step 2: Create an Application Definition File for the SAP Artifacts](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md).</span></span>  
  
    5.  <span data-ttu-id="f72ba-133">將其他欄位保留為預設值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-133">Leave the other fields as default, and click **OK**.</span></span>  
  
3.  <span data-ttu-id="f72ba-134">**管理企業應用程式定義的帳戶資訊**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-134">**Manage account information for enterprise application definitions**.</span></span> <span data-ttu-id="f72ba-135">在此步驟中，您可以啟用個別使用者或群組，從 SharePoint 連接至企業應用程式。</span><span class="sxs-lookup"><span data-stu-id="f72ba-135">In this step, you enable individual users or groups to connect to an enterprise application from SharePoint.</span></span> <span data-ttu-id="f72ba-136">基本上，在此步驟中您對應個別使用者或群組到使用者在 LOB 系統。</span><span class="sxs-lookup"><span data-stu-id="f72ba-136">Essentially, in this step you map an individual user or group to a user in the LOB system.</span></span> <span data-ttu-id="f72ba-137">您也可以指定要連接至 LOB 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="f72ba-137">You also specify the credentials to connect to the LOB system.</span></span> <span data-ttu-id="f72ba-138">您可以從企業應用程式定義 頁面上的管理帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="f72ba-138">You can do so from the Manage Account Information for Enterprise Application Definitions page.</span></span> <span data-ttu-id="f72ba-139">此選項可從 SharePoint 管理中心主控台。</span><span class="sxs-lookup"><span data-stu-id="f72ba-139">This option is available from the SharePoint Central Administration console.</span></span> <span data-ttu-id="f72ba-140">如需這個步驟的詳細資訊，請參閱 「 管理企業應用程式定義的帳戶資訊 」 一節[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。</span><span class="sxs-lookup"><span data-stu-id="f72ba-140">For more information about this step, refer to the “Manage account information for an enterprise application definition” section at [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span></span>  
  
## <a name="creating-a-shared-services-provider"></a><span data-ttu-id="f72ba-141">建立共用的服務提供者</span><span class="sxs-lookup"><span data-stu-id="f72ba-141">Creating a Shared Services Provider</span></span>  
 <span data-ttu-id="f72ba-142">共用服務提供者是共用的服務和其支援資源的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="f72ba-142">A Shared Service Provider is a logical grouping of shared services and their supporting resources.</span></span> <span data-ttu-id="f72ba-143">您可以使用 SharePoint 管理中心主控台，以建立 SSP。</span><span class="sxs-lookup"><span data-stu-id="f72ba-143">You can create an SSP by using the SharePoint Central Administration console.</span></span>  
  
 <span data-ttu-id="f72ba-144">建立 SSP 時，您必須定義的網站</span><span class="sxs-lookup"><span data-stu-id="f72ba-144">You must define a Web site when creating an SSP.</span></span> <span data-ttu-id="f72ba-145">請記住的連接埠號碼和您所建立的網站位址。</span><span class="sxs-lookup"><span data-stu-id="f72ba-145">Remember the port number and the site address that you create.</span></span> <span data-ttu-id="f72ba-146">您將這個網站來匯入商務資料目錄應用程式定義。</span><span class="sxs-lookup"><span data-stu-id="f72ba-146">You will import the Business Data Catalog application definition to this site.</span></span>  
  
 <span data-ttu-id="f72ba-147">如需建立 SSP 的詳細資訊，請參閱 「 章概觀： 建立及設定共用服務提供者 」 在[http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119)。</span><span class="sxs-lookup"><span data-stu-id="f72ba-147">For more information about creating an SSP, see "Chapter overview: Create and configure Shared Services Providers" at [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).</span></span>  
  
## <a name="importing-the-application-definition-file"></a><span data-ttu-id="f72ba-148">匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="f72ba-148">Importing the Application Definition File</span></span>  
 <span data-ttu-id="f72ba-149">您必須立即匯入應用程式定義檔的 ssp。</span><span class="sxs-lookup"><span data-stu-id="f72ba-149">You must now import the application definition file into the SSP.</span></span>  
  
#### <a name="to-import-the-application-definition-file"></a><span data-ttu-id="f72ba-150">若要匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="f72ba-150">To import the application definition file</span></span>  
  
1.  <span data-ttu-id="f72ba-151">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="f72ba-151">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="f72ba-152">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="f72ba-152">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="f72ba-153">在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="f72ba-153">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3.  <span data-ttu-id="f72ba-154">在**商務資料目錄**區段中，按一下**匯入應用程式定義**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-154">In the **Business Data Catalog** section, click **Import application definition**.</span></span>  
  
4.  <span data-ttu-id="f72ba-155">匯入應用程式定義頁面上，開啟時，請瀏覽至 Customer_Orders.xml，選取檔案，然後**開啟**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-155">On the Import Application Definition page that opens, browse to Customer_Orders.xml, select the file, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="f72ba-156">按一下 **[匯入]**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-156">Click **Import**.</span></span>  
  
6.  <span data-ttu-id="f72ba-157">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-157">Click **OK**.</span></span>  
  
     <span data-ttu-id="f72ba-158">匯入後的應用程式，您可以檢視您的應用程式，請前往**檢視應用程式**連結。</span><span class="sxs-lookup"><span data-stu-id="f72ba-158">After importing the application, you can view your application by going to the **View Applications** link.</span></span> <span data-ttu-id="f72ba-159">按一下 應用程式名稱，以查看應用程式中的實體。</span><span class="sxs-lookup"><span data-stu-id="f72ba-159">Click the application name to see the entities in the application.</span></span>  
  
## <a name="creating-web-parts"></a><span data-ttu-id="f72ba-160">建立 Web 組件</span><span class="sxs-lookup"><span data-stu-id="f72ba-160">Creating Web Parts</span></span>  
 <span data-ttu-id="f72ba-161">您現在必須建立 Web 組件在 SharePoint 網站來檢視和管理將擷取從 SAP 系統的商務資料。</span><span class="sxs-lookup"><span data-stu-id="f72ba-161">You must now create Web Parts in your SharePoint site to view and manage the business data that will be extracted from the SAP system.</span></span> <span data-ttu-id="f72ba-162">Web 組件是資訊的可重複使用的元件，可以包含任何一種 Web 架構，包括分析、 共同作業，和資料庫資訊。</span><span class="sxs-lookup"><span data-stu-id="f72ba-162">Web Parts are reusable components that can contain any kind of Web-based information, including analytical, collaborative, and database information.</span></span>  
  
 <span data-ttu-id="f72ba-163">在此教學課程中，Web 組件會建立所建立的商務資料目錄定義編輯器的方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="f72ba-163">In this tutorial, Web Parts are created for the method instances that were created in the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="f72ba-164">Office SharePoint Server 提供特定使用的不同的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-164">Office SharePoint Server provides different kinds of Web Parts for specific use.</span></span> <span data-ttu-id="f72ba-165">這裡使用下列 Web 組件：</span><span class="sxs-lookup"><span data-stu-id="f72ba-165">The following Web Parts are used here:</span></span>  
  
-   <span data-ttu-id="f72ba-166">**商務資料清單**Web 組件**Finder**方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="f72ba-166">**Business Data List** Web Part for the **Finder** method instance.</span></span> <span data-ttu-id="f72ba-167">此 Web 組件可讓您指定要從 SAP 系統中擷取客戶清單的搜尋運算式。</span><span class="sxs-lookup"><span data-stu-id="f72ba-167">This Web Part enables you to specify a search expression to retrieve a list of customers from the SAP system.</span></span> <span data-ttu-id="f72ba-168">此教學課程中，這稱為搜尋客戶的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-168">For this tutorial, this is called the Search Customers Web Part.</span></span>  
  
-   <span data-ttu-id="f72ba-169">**商務資料項目**Web 組件**特定搜尋工具**方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="f72ba-169">**Business Data Item** Web Part for the **Specific Finder** method instance.</span></span> <span data-ttu-id="f72ba-170">此 Web 組件會顯示您搜尋客戶的 Web 組件從選取的特定客戶的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f72ba-170">This Web Part presents the details for a specific customer that you select from the Search Customers Web Part.</span></span> <span data-ttu-id="f72ba-171">此 Web 組件會對應至搜尋客戶的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-171">This Web Part is mapped to the Search Customer Web Part.</span></span>  <span data-ttu-id="f72ba-172">此教學課程中，這稱為客戶詳細資料 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-172">For this tutorial, this is called the Customer Details Web Part.</span></span>  
  
-   <span data-ttu-id="f72ba-173">**商務資料相關清單**Web 組件**關聯**方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="f72ba-173">**Business Data Related List** Web Part for the **Association** method instance.</span></span> <span data-ttu-id="f72ba-174">此 Web 組件會列出您搜尋客戶的 Web 組件從選取的特定客戶的銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="f72ba-174">This Web Part lists the sales orders for a specific customer that you select from the Search Customers Web Part.</span></span> <span data-ttu-id="f72ba-175">此 Web 組件是搜尋客戶的 Web 組件相關聯。</span><span class="sxs-lookup"><span data-stu-id="f72ba-175">This Web Part is associated with the Search Customer Web Part.</span></span>  <span data-ttu-id="f72ba-176">此教學課程中，這稱為銷售訂單詳細資料 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-176">For this tutorial, this is called the Sales Order Details Web Part.</span></span>  
  
 <span data-ttu-id="f72ba-177">本節中的指示來建立這些 Web 組件，並建立它們之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="f72ba-177">This section provides instructions to create these Web Parts and to create associations between them.</span></span> <span data-ttu-id="f72ba-178">如需建立 Web 組件的詳細資訊，請參閱 < 自訂商務資料清單、 Web 組件和站台 」 在[http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131)。</span><span class="sxs-lookup"><span data-stu-id="f72ba-178">For more information about creating Web Parts, see "Customize business data lists, Web Parts, and sites" at [http://go.microsoft.com/fwlink/?LinkId=104131](http://go.microsoft.com/fwlink/?LinkId=104131).</span></span>  
  
 <span data-ttu-id="f72ba-179">Web 組件將會加入至單一的 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="f72ba-179">The Web Parts will be added to a single Web Part page.</span></span> <span data-ttu-id="f72ba-180">加入 Web 組件之前，您必須建立 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="f72ba-180">You must create a Web Part page before adding the Web Parts.</span></span> <span data-ttu-id="f72ba-181">此教學課程中，此 Web 組件頁面稱為 Customer_SalesOrders。</span><span class="sxs-lookup"><span data-stu-id="f72ba-181">For this tutorial, this Web Part page is called Customer_SalesOrders.</span></span>  
  
### <a name="creating-a-web-part-page"></a><span data-ttu-id="f72ba-182">建立網頁組件</span><span class="sxs-lookup"><span data-stu-id="f72ba-182">Creating a Web Part Page</span></span>  
 <span data-ttu-id="f72ba-183">本節提供建立 Web 組件頁面的指示。</span><span class="sxs-lookup"><span data-stu-id="f72ba-183">This section provides instructions to create a Web Part page.</span></span>  
  
##### <a name="to-create-a-web-part-page"></a><span data-ttu-id="f72ba-184">若要建立 Web 組件頁面</span><span class="sxs-lookup"><span data-stu-id="f72ba-184">To create a Web Part page</span></span>  
  
1.  <span data-ttu-id="f72ba-185">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="f72ba-185">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="f72ba-186">按一下**啟動**，指向**所有程式**，指向 [ **Microsoft Office Server**，然後按一下**SharePoint 3.0 管理中心]**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-186">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="f72ba-187">在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="f72ba-187">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3.  <span data-ttu-id="f72ba-188">在右上角的 共用服務管理 頁面上，按一下 **網站動作**，然後按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-188">On the Shared Services Administration page, in the upper-right corner, click **Site Actions**, and then click **Create**.</span></span>  
  
     <span data-ttu-id="f72ba-189">![若要建立的 web 組件的功能表](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")</span><span class="sxs-lookup"><span data-stu-id="f72ba-189">![Menu to create a web part](../../adapters-and-accelerators/adapter-oracle-ebs/media/a9872c3e-f823-4c47-a538-19242565d2e9.gif "a9872c3e-f823-4c47-a538-19242565d2e9")</span></span>  
  
4.  <span data-ttu-id="f72ba-190">在 [建立] 頁面中**網頁**區段中，按一下**Web 組件頁面**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-190">On the Create page, in the **Web Pages** section, click **Web Part Page**.</span></span>  
  
5.  <span data-ttu-id="f72ba-191">在新的 Web 組件 頁面上，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f72ba-191">On the New Web Part page, do the following:</span></span>  
  
    1.  <span data-ttu-id="f72ba-192">在**名稱**欄位中，輸入頁面的名稱。</span><span class="sxs-lookup"><span data-stu-id="f72ba-192">In the **Name** field, type a name for the page.</span></span> <span data-ttu-id="f72ba-193">此教學課程中，輸入相同的名稱。 **Customer_SalesOrders**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-193">For this tutorial, type the name as **Customer_SalesOrders**.</span></span>  
  
    2.  <span data-ttu-id="f72ba-194">選取**檔案已經存在覆寫**核取方塊，如果您想要覆寫舊的頁面，與您建立新的頁面名稱相同。</span><span class="sxs-lookup"><span data-stu-id="f72ba-194">Select the **Overwrite if file already exists** check box, if you want to overwrite old pages with the same name as the new page you create.</span></span>  
  
    3.  <span data-ttu-id="f72ba-195">在**配置**] 區段中，從**選擇版面配置範本**方塊中，選取 [Web 組件頁面的版面配置。</span><span class="sxs-lookup"><span data-stu-id="f72ba-195">In the **Layout** section, from the **Choose a Layout Template** box, select a layout for the Web Part page.</span></span> <span data-ttu-id="f72ba-196">此教學課程中，選取**標頭，左側資料行中，主體**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-196">For this tutorial, select **Header, Left Column, Body**.</span></span>  
  
    4.  <span data-ttu-id="f72ba-197">在**儲存位置**區段的**文件庫**清單中，按一下**表單範本**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-197">In the **Save Location** section, in the **Document Library** list, click **Form Templates**.</span></span>  
  
    5.  <span data-ttu-id="f72ba-198">按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-198">Click **Create**.</span></span> <span data-ttu-id="f72ba-199">只在建立之後下, 圖顯示 Web 組件頁面。</span><span class="sxs-lookup"><span data-stu-id="f72ba-199">The following figure shows a Web Part page after it is just created.</span></span>  
  
         <span data-ttu-id="f72ba-200">![空的 Web 組件頁面](../../adapters-and-accelerators/adapter-sap/media/6aa68c43-59df-47c4-95a6-453f7c668025.gif "6aa68c43-59df-47c4-95a6-453f7c668025")</span><span class="sxs-lookup"><span data-stu-id="f72ba-200">![Empty Web Part page](../../adapters-and-accelerators/adapter-sap/media/6aa68c43-59df-47c4-95a6-453f7c668025.gif "6aa68c43-59df-47c4-95a6-453f7c668025")</span></span>  
  
    6.  <span data-ttu-id="f72ba-201">您現在必須將不同的 Web 組件加入此頁面。</span><span class="sxs-lookup"><span data-stu-id="f72ba-201">You must now add the different Web Parts to this page.</span></span>  
  
### <a name="adding-a-business-data-list-web-part"></a><span data-ttu-id="f72ba-202">新增商務資料清單網頁組件</span><span class="sxs-lookup"><span data-stu-id="f72ba-202">Adding a Business Data List Web Part</span></span>  
 <span data-ttu-id="f72ba-203">您現在必須新增 Web 組件頁面的商務資料清單網頁組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-203">You must now add a Business Data List Web Part to the Web Part page.</span></span> <span data-ttu-id="f72ba-204">使用此 Web 組件會擷取客戶清單，從 SAP 系統符合搜尋運算式。</span><span class="sxs-lookup"><span data-stu-id="f72ba-204">Using this Web Part you will retrieve a list of customers from the SAP system that matches a search expression.</span></span> <span data-ttu-id="f72ba-205">此 Web 組件會對應至**Finder**方法執行個體 (*GetCustomerByName_Instance*) 建立的商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="f72ba-205">This Web Part corresponds to the **Finder** method instance (*GetCustomerByName_Instance*) that you created in the Business Data Catalog Definition Editor.</span></span>  
  
##### <a name="to-add-a-business-data-list-web-part"></a><span data-ttu-id="f72ba-206">若要加入商務資料清單網頁組件</span><span class="sxs-lookup"><span data-stu-id="f72ba-206">To add a Business Data List Web Part</span></span>  
  
1.  <span data-ttu-id="f72ba-207">在 Customer_SalesOrders 頁面上，在**標頭**區段中，按一下**新增網頁組件**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-207">On the Customer_SalesOrders page, in the **Header** section, click **Add a Web Part**.</span></span>  
  
2.  <span data-ttu-id="f72ba-208">在**新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料清單**核取方塊，然後**新增**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-208">In the **Add Web Parts** dialog box, in the **Business Data** section, select the **Business Data List** check box, and then click **Add**.</span></span>  
  
     <span data-ttu-id="f72ba-209">![若要建立商務資料 Web 組件的選項](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")</span><span class="sxs-lookup"><span data-stu-id="f72ba-209">![Options to create a business data Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/ae7c952c-1592-495f-9452-c1bffd44421c.gif "ae7c952c-1592-495f-9452-c1bffd44421c")</span></span>  
  
3.  <span data-ttu-id="f72ba-210">新增商務資料清單 Web 組件中，按一下 **開啟工具窗格**連結。</span><span class="sxs-lookup"><span data-stu-id="f72ba-210">In the newly added Business Data List Web Part, click the **Open the tool pane** link.</span></span>  
  
     <span data-ttu-id="f72ba-211">![Web 組件中開啟工具窗格](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")</span><span class="sxs-lookup"><span data-stu-id="f72ba-211">![Open the tool pane for Web Part](../../adapters-and-accelerators/adapter-oracle-ebs/media/4e7a1cb1-69dc-4e0d-a211-6a217dc4a549.gif "4e7a1cb1-69dc-4e0d-a211-6a217dc4a549")</span></span>  
  
4.  <span data-ttu-id="f72ba-212">在右窗格中，開啟 [商務資料清單] 工具窗格。</span><span class="sxs-lookup"><span data-stu-id="f72ba-212">The Business Data List tool pane opens in the right pane.</span></span> <span data-ttu-id="f72ba-213">在**商務資料清單** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f72ba-213">In the **Business Data List** section, for the **Type** field, click the **Browse** button.</span></span>  
  
     <span data-ttu-id="f72ba-214">![商務資料清單 工具窗格](../../adapters-and-accelerators/adapter-sap/media/580c58bf-bfc7-4d48-8c62-8ca4eee4ab48.gif "580c58bf-bfc7-4d48-8c62-8ca4eee4ab48")</span><span class="sxs-lookup"><span data-stu-id="f72ba-214">![Business Data List tool pane](../../adapters-and-accelerators/adapter-sap/media/580c58bf-bfc7-4d48-8c62-8ca4eee4ab48.gif "580c58bf-bfc7-4d48-8c62-8ca4eee4ab48")</span></span>  
  
5.  <span data-ttu-id="f72ba-215">在**商務資料型別選擇器**對話方塊中，選取**Customer_Order_Instance**應用程式，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-215">In the **Business Data Type Picker** dialog box, select the **Customer_Order_Instance** application, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f72ba-216">![選取的應用程式執行個體](../../adapters-and-accelerators/adapter-sap/media/79967c27-9c76-4394-89bc-38c63649bdda.gif "79967c27-9c76-4394-89bc-38c63649bdda")</span><span class="sxs-lookup"><span data-stu-id="f72ba-216">![Select the application instance](../../adapters-and-accelerators/adapter-sap/media/79967c27-9c76-4394-89bc-38c63649bdda.gif "79967c27-9c76-4394-89bc-38c63649bdda")</span></span>  
  
6.  <span data-ttu-id="f72ba-217">展開**外觀** 節點，然後在**標題**方塊中，輸入 Web 組件的標題。</span><span class="sxs-lookup"><span data-stu-id="f72ba-217">Expand the **Appearance** node, and in the **Title** box, type a title for the Web Part.</span></span> <span data-ttu-id="f72ba-218">此 Web 組件中，輸入**客戶清單**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-218">For this Web Part, type **Customer List**.</span></span>  
  
7.  <span data-ttu-id="f72ba-219">在 商務資料清單 工具窗格中，按一下 **套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-219">In the Business Data List tool pane, click **Apply**, and then click **OK**.</span></span> <span data-ttu-id="f72ba-220">商務資料清單網頁組件現在看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="f72ba-220">The Business Data List Web Part now looks like the following:</span></span>  
  
     <span data-ttu-id="f72ba-221">![商務資料清單 」 Web 組件](../../adapters-and-accelerators/adapter-sap/media/185fb3f3-98b0-4efe-960d-91312912ad7d.gif "185fb3f3-98b0-4efe-960d-91312912ad7d")</span><span class="sxs-lookup"><span data-stu-id="f72ba-221">![Business Data List Web Part](../../adapters-and-accelerators/adapter-sap/media/185fb3f3-98b0-4efe-960d-91312912ad7d.gif "185fb3f3-98b0-4efe-960d-91312912ad7d")</span></span>  
  
8.  <span data-ttu-id="f72ba-222">Web 組件會列出執行 SD_RFC_CUSTOMER_GET RFC 所傳回的欄位。</span><span class="sxs-lookup"><span data-stu-id="f72ba-222">The Web Part lists the fields that are returned by executing the SD_RFC_CUSTOMER_GET RFC.</span></span> <span data-ttu-id="f72ba-223">您可以移除不想要在 SharePoint 網站上顯示的欄位。</span><span class="sxs-lookup"><span data-stu-id="f72ba-223">You can remove the fields that you do not want to display on the SharePoint portal.</span></span> <span data-ttu-id="f72ba-224">若要移除欄位，請按一下**編輯檢視**右上角的 網頁組件連結。</span><span class="sxs-lookup"><span data-stu-id="f72ba-224">To remove the fields, click the **Edit View** link in the upper-right corner of the Web Part.</span></span>  
  
9. <span data-ttu-id="f72ba-225">在 [編輯檢視] 頁面的資料行區段中，清除核取方塊，針對您不想要顯示的資料行。</span><span class="sxs-lookup"><span data-stu-id="f72ba-225">On the Edit View page, in the Columns section, clear the check boxes against the columns that you do not want to display.</span></span>  
  
     <span data-ttu-id="f72ba-226">![在 SharePoint 中檢視特定資料行](../../adapters-and-accelerators/adapter-sap/media/24213b67-aafe-4534-91a7-06bde7bcbf7c.gif "24213b67-aafe-4534-91a7-06bde7bcbf7c")</span><span class="sxs-lookup"><span data-stu-id="f72ba-226">![View specific columns in SharePoint](../../adapters-and-accelerators/adapter-sap/media/24213b67-aafe-4534-91a7-06bde7bcbf7c.gif "24213b67-aafe-4534-91a7-06bde7bcbf7c")</span></span>  
  
10. <span data-ttu-id="f72ba-227">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-227">Click **OK**.</span></span>  
  
### <a name="adding-a-business-data-item-web-part"></a><span data-ttu-id="f72ba-228">加入商務資料的項目 Web 組件</span><span class="sxs-lookup"><span data-stu-id="f72ba-228">Adding a Business Data Item Web Part</span></span>  
 <span data-ttu-id="f72ba-229">您現在必須新增 Web 組件頁面的商務資料的項目 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-229">You must now add a Business Data Item Web Part to the Web Part page.</span></span> <span data-ttu-id="f72ba-230">您也將連接與商務資料清單 Web 組件您剛才建立的此 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-230">You will also connect this Web Part to the Business Data List Web Part that you just created.</span></span> <span data-ttu-id="f72ba-231">如此一來，您可以查看您在商務資料清單網頁組件中選取客戶的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f72ba-231">By doing so, you will be able to see the details for a customer that you select in the Business Data List Web Part.</span></span> <span data-ttu-id="f72ba-232">此 Web 組件會對應至**特定搜尋工具**方法執行個體 (*GetCustomerByNumber_Instance*) 建立的商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="f72ba-232">This Web Part corresponds to the **Specific Finder** method instance (*GetCustomerByNumber_Instance*) that you created in the Business Data Catalog Definition Editor.</span></span>  
  
##### <a name="to-add-a-business-data-item-web-part"></a><span data-ttu-id="f72ba-233">若要將商務資料的項目 Web 組件</span><span class="sxs-lookup"><span data-stu-id="f72ba-233">To add a Business Data Item Web Part</span></span>  
  
1.  <span data-ttu-id="f72ba-234">在右上角的 Customer_SalesOrders 頁面上，按一下 **網站動作**，然後按一下 **編輯頁面**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-234">On the Customer_SalesOrders page, in the upper-right corner, click **Site Actions**, and then click **Edit Page**.</span></span>  
  
2.  <span data-ttu-id="f72ba-235">在 Customer_SalesOrders 頁面上，在**左欄**區段中，按一下**新增網頁組件**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-235">On the Customer_SalesOrders page, in the **Left Column** section, click **Add a Web Part**.</span></span>  
  
3.  <span data-ttu-id="f72ba-236">在**新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料項目**核取方塊，然後**新增**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-236">In the **Add Web Parts** dialog box, in the **Business Data** section, select the **Business Data Item** check box, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="f72ba-237">新增商務資料的項目 Web 組件中，按一下 **開啟工具窗格**連結。</span><span class="sxs-lookup"><span data-stu-id="f72ba-237">In the newly added Business Data Item Web Part, click the **Open the tool pane** link.</span></span>  
  
5.  <span data-ttu-id="f72ba-238">在右窗格中，開啟 [商務資料項目] 工具窗格。</span><span class="sxs-lookup"><span data-stu-id="f72ba-238">The Business Data Item tool pane opens in the right pane.</span></span> <span data-ttu-id="f72ba-239">在**商務資料項目** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f72ba-239">In the **Business Data Item** section, for the **Type** field, click the **Browse** button.</span></span>  
  
     <span data-ttu-id="f72ba-240">![商務資料項目 工具窗格](../../adapters-and-accelerators/adapter-sap/media/29322df5-4ce3-4c1f-a658-39a355dfe2aa.gif "29322df5-4ce3-4c1f-a658-39a355dfe2aa")</span><span class="sxs-lookup"><span data-stu-id="f72ba-240">![Business Data Item tool pane](../../adapters-and-accelerators/adapter-sap/media/29322df5-4ce3-4c1f-a658-39a355dfe2aa.gif "29322df5-4ce3-4c1f-a658-39a355dfe2aa")</span></span>  
  
6.  <span data-ttu-id="f72ba-241">在**商務資料型別選擇器**對話方塊中，選取**Customer_Order_Instance**應用程式，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-241">In the **Business Data Type Picker** dialog box, select the **Customer_Order_Instance** application, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="f72ba-242">在**檢視**清單中，選取**預設**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-242">In the **View** list, select **Default**.</span></span>  
  
8.  <span data-ttu-id="f72ba-243">保留**項目**空的清單。</span><span class="sxs-lookup"><span data-stu-id="f72ba-243">Leave the **Item** list empty.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f72ba-244">如**項目** 欄位中，您必須指定客戶名稱或客戶編號，您想要查看詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f72ba-244">For the **Item** field, you must specify a customer name or customer number for which you want to see the details.</span></span> <span data-ttu-id="f72ba-245">此 Web 組件當做輸入參數。</span><span class="sxs-lookup"><span data-stu-id="f72ba-245">That serves as an input parameter for this Web Part.</span></span> <span data-ttu-id="f72ba-246">因為您會藉由連接到商務資料清單網頁組件取得的輸入的參數，您不必明確指定項目。</span><span class="sxs-lookup"><span data-stu-id="f72ba-246">Because you will be getting the input parameter by connecting to the Business Data List Web Part, you need not specify an item explicitly.</span></span>  
  
9. <span data-ttu-id="f72ba-247">在**欄位**區段中，按一下**選擇**，選取您想要顯示在頁面上的欄位。</span><span class="sxs-lookup"><span data-stu-id="f72ba-247">In the **Fields** section, click **Choose** to select the fields you want to display on the page.</span></span>  
  
10. <span data-ttu-id="f72ba-248">展開**外觀** 節點，然後在**標題**欄位中，指定 Web 組件的標題。</span><span class="sxs-lookup"><span data-stu-id="f72ba-248">Expand the **Appearance** node, and in the **Title** field, specify a title for the Web Part.</span></span> <span data-ttu-id="f72ba-249">此 Web 組件中，指定**詳細資料，找出特定客戶**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-249">For this Web Part, specify **Details for a Specific Customer**.</span></span>  
  
11. <span data-ttu-id="f72ba-250">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-250">Click **Apply**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="f72ba-251">若要將 Web 組件連接**客戶清單**Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-251">Connect the Web Part to the **Customer List** Web Part.</span></span> <span data-ttu-id="f72ba-252">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="f72ba-252">To do so:</span></span>  
  
    1.  <span data-ttu-id="f72ba-253">按一下**編輯**靠近右上角的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-253">Click **edit** towards the upper-right corner of the Web Part.</span></span>  
  
    2.  <span data-ttu-id="f72ba-254">從內容功能表中指向**連線**，指向 **取得項目從**，然後按一下**客戶清單**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-254">From the context menu point to **Connections**, point to **Get Item From**, and click **Customer List**.</span></span>  
  
         <span data-ttu-id="f72ba-255">![連接兩個 Web 組件](../../adapters-and-accelerators/adapter-sap/media/505aead7-f498-448f-a7cb-55d0a121f91f.gif "505aead7-f498-448f-a7cb-55d0a121f91f")</span><span class="sxs-lookup"><span data-stu-id="f72ba-255">![Connect two Web Parts](../../adapters-and-accelerators/adapter-sap/media/505aead7-f498-448f-a7cb-55d0a121f91f.gif "505aead7-f498-448f-a7cb-55d0a121f91f")</span></span>  
  
### <a name="adding-a-business-data-related-list-web-part"></a><span data-ttu-id="f72ba-256">加入商務資料相關清單 Web 組件</span><span class="sxs-lookup"><span data-stu-id="f72ba-256">Adding a Business Data Related List Web Part</span></span>  
 <span data-ttu-id="f72ba-257">您現在必須新增 Web 組件頁面的商務資料相關清單 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-257">You must now add a Business Data Related List Web Part to the Web Part page.</span></span> <span data-ttu-id="f72ba-258">您也會連接商務資料清單 Web 組件您稍早建立的此 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-258">You will also connect this Web Part to the Business Data List Web Part you created earlier.</span></span> <span data-ttu-id="f72ba-259">如此一來，您將能夠看到您在商務資料清單網頁組件中選取客戶的銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="f72ba-259">By doing so, you will be able to see the sales orders for a customer that you select in the Business Data List Web Part.</span></span> <span data-ttu-id="f72ba-260">此 Web 組件會對應至**關聯**方法執行個體 (*SalesOrderForCustomer_Instance*) 建立的商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="f72ba-260">This Web Part corresponds to the **Association** method instance (*SalesOrderForCustomer_Instance*) you created in the Business Data Catalog Definition Editor.</span></span>  
  
##### <a name="to-add-a-business-data-related-list-web-part"></a><span data-ttu-id="f72ba-261">若要新增商務資料相關清單 Web 組件</span><span class="sxs-lookup"><span data-stu-id="f72ba-261">To add a Business Data Related List Web Part</span></span>  
  
1.  <span data-ttu-id="f72ba-262">在 Customer_SalesOrders 頁面上，在**主體**區段中，按一下**新增網頁組件**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-262">On the Customer_SalesOrders page, in the **Body** section, click **Add a Web Part**.</span></span>  
  
2.  <span data-ttu-id="f72ba-263">在**新增網頁組件**對話方塊中，於**商務資料**區段中，選取**商務資料相關清單**核取方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-263">In the **Add Web Parts** dialog box, in the **Business Data** section, select the **Business Data Related List** check box, and click **Add**.</span></span>  
  
3.  <span data-ttu-id="f72ba-264">新增商務資料相關清單 Web 組件中，按一下 **開啟工具窗格**連結。</span><span class="sxs-lookup"><span data-stu-id="f72ba-264">In the newly added Business Data Related List Web Part, click the **Open the tool pane** link.</span></span>  
  
4.  <span data-ttu-id="f72ba-265">在右窗格中，開啟 [商務資料相關清單] 工具窗格。</span><span class="sxs-lookup"><span data-stu-id="f72ba-265">The Business Data Related List tool pane opens in the right pane.</span></span> <span data-ttu-id="f72ba-266">在**商務資料相關清單** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f72ba-266">In the **Business Data Related List** section, for the **Type** field, click the **Browse** button.</span></span>  
  
     <span data-ttu-id="f72ba-267">![商務資料相關清單](../../adapters-and-accelerators/adapter-sap/media/1914e12d-27f0-4ecb-9605-3177183a2d44.gif "1914e12d-27f0-4ecb-9605-3177183a2d44")</span><span class="sxs-lookup"><span data-stu-id="f72ba-267">![Business Data Related List](../../adapters-and-accelerators/adapter-sap/media/1914e12d-27f0-4ecb-9605-3177183a2d44.gif "1914e12d-27f0-4ecb-9605-3177183a2d44")</span></span>  
  
5.  <span data-ttu-id="f72ba-268">在**商務資料型別選擇器**對話方塊中，選取**Customer_Order_Instance**應用程式，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-268">In the **Business Data Type Picker** dialog box, select the **Customer_Order_Instance** application, and then click **OK**.</span></span> <span data-ttu-id="f72ba-269">**關聯性**清單填入名稱**關聯**方法執行個體 (*SalesOrderForCustomer_Instance*)。</span><span class="sxs-lookup"><span data-stu-id="f72ba-269">The **Relationship** list populates with the name of the **Association** method instance (*SalesOrderForCustomer_Instance*).</span></span>  
  
6.  <span data-ttu-id="f72ba-270">展開**外觀** 節點，然後在**標題**方塊中，輸入 Web 組件的標題。</span><span class="sxs-lookup"><span data-stu-id="f72ba-270">Expand the **Appearance** node, and in the **Title** box, type a title for the Web Part.</span></span> <span data-ttu-id="f72ba-271">此 Web 組件中，輸入**找出特定客戶的銷售訂單**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-271">For this Web Part, type **Sales Order for a Specific Customer**.</span></span>  
  
7.  <span data-ttu-id="f72ba-272">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-272">Click **Apply**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="f72ba-273">Web 組件會列出執行 BAPI_SALESORDER_GETLIST RFC 所傳回的欄位。</span><span class="sxs-lookup"><span data-stu-id="f72ba-273">The Web Part lists the fields that are returned by executing the BAPI_SALESORDER_GETLIST RFC.</span></span> <span data-ttu-id="f72ba-274">您可以移除不想要在 SharePoint 網站上顯示的欄位。</span><span class="sxs-lookup"><span data-stu-id="f72ba-274">You can remove the fields that you do not want to display on the SharePoint portal.</span></span> <span data-ttu-id="f72ba-275">若要移除欄位，請按一下**編輯檢視**右上角的 網頁組件連結。</span><span class="sxs-lookup"><span data-stu-id="f72ba-275">To remove the fields, click the **Edit View** link in the upper-right corner of the Web Part.</span></span>  
  
9. <span data-ttu-id="f72ba-276">在 [編輯檢視] 頁面中**資料行**區段中，清除文字方塊中，針對您不想要顯示的資料行。</span><span class="sxs-lookup"><span data-stu-id="f72ba-276">On the Edit View page, in the **Columns** section, clear the text boxes against the columns that you do not want to display.</span></span>  
  
10. <span data-ttu-id="f72ba-277">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-277">Click **OK**.</span></span>  
  
11. <span data-ttu-id="f72ba-278">若要將 Web 組件連接**客戶清單**Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-278">Connect the Web Part to the **Customer List** Web Part.</span></span> <span data-ttu-id="f72ba-279">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="f72ba-279">To do so:</span></span>  
  
    1.  <span data-ttu-id="f72ba-280">按一下**編輯**靠近右上角**找出特定客戶的銷售訂單**Web 組件。</span><span class="sxs-lookup"><span data-stu-id="f72ba-280">Click **edit** towards the upper-right corner of the **Sales Order for a Specific Customer** Web Part.</span></span>  
  
    2.  <span data-ttu-id="f72ba-281">從內容功能表，指向**連線**，指向 **取得相關項目從**，然後按一下 **客戶清單**。</span><span class="sxs-lookup"><span data-stu-id="f72ba-281">From the context menu, point to **Connections**, point to **Get Related Item From**, and then click **Customer List**.</span></span>  
  
12. <span data-ttu-id="f72ba-282">按一下**結束編輯模式**從頁面的右上角。</span><span class="sxs-lookup"><span data-stu-id="f72ba-282">Click **Exit Edit Mode** from the upper-right corner of the page.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f72ba-283">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f72ba-283">Next Steps</span></span>  
 <span data-ttu-id="f72ba-284">從 SAP 系統中擷取資料來測試 SharePoint 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f72ba-284">Test the SharePoint application by retrieving data from an SAP system.</span></span> <span data-ttu-id="f72ba-285">請參閱[步驟 4： 測試 SharePoint 應用程式](../../adapters-and-accelerators/adapter-sap/step-4-test-your-sharepoint-application1.md)。</span><span class="sxs-lookup"><span data-stu-id="f72ba-285">See [Step 4: Test Your SharePoint Application](../../adapters-and-accelerators/adapter-sap/step-4-test-your-sharepoint-application1.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72ba-286">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f72ba-286">See Also</span></span>  
 [<span data-ttu-id="f72ba-287">教學課程 1： 從 SharePoint 網站上的 SAP 系統中呈現資料</span><span class="sxs-lookup"><span data-stu-id="f72ba-287">Tutorial 1: Presenting Data from an SAP System on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)