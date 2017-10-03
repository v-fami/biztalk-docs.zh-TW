---
title: "步驟 4： 建立 Sharepoint 應用程式存取配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2d8c398-370a-4c62-961d-0eab6066ad5a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3360bbdf5ae5a6a8dde9851c544342ea6a6bc1cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-a-sharepoint-application-to-access-the-adapter"></a><span data-ttu-id="36b1a-102">步驟 4： 建立 Sharepoint 應用程式存取配接器</span><span class="sxs-lookup"><span data-stu-id="36b1a-102">Step 4: Create a Sharepoint Application to Access the Adapter</span></span>
<span data-ttu-id="36b1a-103">![步驟 4 之 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="36b1a-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="36b1a-104">**若要完成的時間：** 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="36b1a-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="36b1a-105">在此步驟中您會需要您使用商務資料目錄定義編輯器工具所建立的應用程式定義檔，並匯入 Microsoft Office SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="36b1a-105">In this step you take the application definition file that you created using the Business Data Catalog Definition Editor tool, and import it into Microsoft Office SharePoint Server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="36b1a-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="36b1a-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="36b1a-107">您應該已經建立應用程式檔案中所述[步驟 3： 建立應用程式定義檔](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)。</span><span class="sxs-lookup"><span data-stu-id="36b1a-107">You should have created an application file as described in [Step 3: Create an Application Definition File](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md).</span></span>  
  
-   <span data-ttu-id="36b1a-108">Microsoft Single Sign-on 服務必須執行。</span><span class="sxs-lookup"><span data-stu-id="36b1a-108">The Microsoft Single Sign-On service must be running.</span></span>  
  
## <a name="how-to-create-a-sharepoint-application"></a><span data-ttu-id="36b1a-109">如何建立 SharePoint 應用程式</span><span class="sxs-lookup"><span data-stu-id="36b1a-109">How to Create a SharePoint Application</span></span>  
 <span data-ttu-id="36b1a-110">建立 SharePoint 應用程式包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="36b1a-110">Creating a SharePoint application involves the following steps:</span></span>  
  
-   <span data-ttu-id="36b1a-111">在 SharePoint 中建立的單一登入 (SSO) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="36b1a-111">Create a Single Sign-On (SSO) application in SharePoint.</span></span>  
  
-   <span data-ttu-id="36b1a-112">建立共用服務提供者，並匯入應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="36b1a-112">Create a Shared Services Provider, and import the application definition file.</span></span>  
  
-   <span data-ttu-id="36b1a-113">建立 Web 組件頁面，並加入 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="36b1a-113">Create a Web Part page, and add Web Parts.</span></span>  
  
 <span data-ttu-id="36b1a-114">本主題示範如何執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="36b1a-114">This topic demonstrates how to perform these steps.</span></span>  
  
## <a name="creating-an-sso-application-in-sharepoint"></a><span data-ttu-id="36b1a-115">在 SharePoint 中建立的 SSO 應用程式</span><span class="sxs-lookup"><span data-stu-id="36b1a-115">Creating an SSO Application in SharePoint</span></span>  
 <span data-ttu-id="36b1a-116">若要從 SharePoint 應用程式回應配接器傳遞使用者認證，您必須設定 SSO 應用程式對應至使用者帳戶或群組。</span><span class="sxs-lookup"><span data-stu-id="36b1a-116">To pass user credentials to the Echo adapter from a SharePoint application, you must set up an SSO application that maps to a user account or group.</span></span>  
  
#### <a name="manage-server-settings-for-single-sign-on"></a><span data-ttu-id="36b1a-117">管理伺服器設定為單一登入</span><span class="sxs-lookup"><span data-stu-id="36b1a-117">Manage server settings for Single Sign-On</span></span>  
  
1.  <span data-ttu-id="36b1a-118">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="36b1a-118">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="36b1a-119">在**啟動**功能表上，指向**所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="36b1a-119">On the **Start** menu, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="36b1a-120">在上方導覽列中，按一下 **作業**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-120">On the top navigation bar, click **Operations**.</span></span>  
  
3.  <span data-ttu-id="36b1a-121">在 [作業] 頁面中**安全性組態**區段中，按一下**管理設定單一登入**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-121">On the Operations page, in the **Security Configuration** section, click **Manage settings for single sign-on**.</span></span>  
  
4.  <span data-ttu-id="36b1a-122">在 管理的設定單一登入頁面上，在**伺服器設定**區段中，按一下**管理伺服器設定**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-122">On the Manage Settings for Single Sign-On page, in the **Server Settings** section, click **Manage Server Settings**.</span></span>  
  
5.  <span data-ttu-id="36b1a-123">請確定此頁面上的資訊正確安裝單一登入。</span><span class="sxs-lookup"><span data-stu-id="36b1a-123">Ensure that the information on this page is correct for your Single Sign-On installation.</span></span> <span data-ttu-id="36b1a-124">如需有關這些作業的詳細資訊，請參閱 「 設定單一登入 (Office SharePoint Server) >，網址[http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291)。</span><span class="sxs-lookup"><span data-stu-id="36b1a-124">For more information about these operations, see “Configure single sign-on (Office SharePoint Server)” at [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span></span>  
  
#### <a name="manage-settings-for-enterprise-application-definitions"></a><span data-ttu-id="36b1a-125">管理企業應用程式定義的設定</span><span class="sxs-lookup"><span data-stu-id="36b1a-125">Manage settings for enterprise application definitions</span></span>  
  
1.  <span data-ttu-id="36b1a-126">在 SharePoint 管理中心 的上方導覽列上，按一下**作業**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-126">In SharePoint Central Administration, on the top navigation bar, click **Operations**.</span></span>  
  
2.  <span data-ttu-id="36b1a-127">在 [作業] 頁面中**安全性組態**區段中，按一下**進行單一登入的管理設定**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-127">On the Operations page, in the **Security Configuration** section, click **Manage Settings for single sign-on**.</span></span>  
  
3.  <span data-ttu-id="36b1a-128">在 管理的設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理企業應用程式定義的設定**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-128">On the Manage Settings for Single Sign-On page, in the **Enterprise Application Definition Settings** section, click **Manage Settings for enterprise application definitions**.</span></span>  
  
4.  <span data-ttu-id="36b1a-129">管理企業應用程式定義] 頁面上，按一下 [**新項目**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-129">On the Manage Enterprise Application Definitions page, click **New Item**.</span></span>  
  
5.  <span data-ttu-id="36b1a-130">建立企業應用程式定義 頁面上，設定**顯示名稱**欄位設為**EchoSSO**，然後設定**應用程式名稱**欄位設為**EchoSSO**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-130">On the Create Enterprise Application Definitions Page, set the **Display name** field to **EchoSSO**, and then set the **Application name** field to **EchoSSO**.</span></span> <span data-ttu-id="36b1a-131">此值應該符合您在中指定的 SecondarySsoApplicationId[步驟 3： 建立應用程式定義檔](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)。</span><span class="sxs-lookup"><span data-stu-id="36b1a-131">This value should match the SecondarySsoApplicationId you specified in [Step 3: Create an Application Definition File](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md).</span></span>  
  
6.  <span data-ttu-id="36b1a-132">在**連絡電子郵件地址**欄位中輸入您的電子郵件地址，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-132">In the **Contact e-mail address** field, enter your e-mail address, and then click **OK**.</span></span>  
  
#### <a name="manage-account-information-for-enterprise-application-definitions"></a><span data-ttu-id="36b1a-133">管理企業應用程式定義的帳戶資訊</span><span class="sxs-lookup"><span data-stu-id="36b1a-133">Manage account information for enterprise application definitions</span></span>  
  
1.  <span data-ttu-id="36b1a-134">在 SharePoint 管理中心 的上方導覽列上，按一下**作業**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-134">In SharePoint Central Administration, on the top navigation bar, click **Operations**.</span></span>  
  
2.  <span data-ttu-id="36b1a-135">在 [作業] 頁面中**安全性組態 > 一節**，按一下**管理設定單一登入**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-135">On the Operations page, in the **Security Configuration Section**, click **Manage settings for single sign-on**.</span></span>  
  
3.  <span data-ttu-id="36b1a-136">在 管理的設定單一登入頁面上，在**企業應用程式定義設定**區段中，按一下**管理的帳戶資訊的企業應用程式定義**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-136">On the Manage Settings for Single Sign-On page, in the **Enterprise Application Definition Settings** section, click **Manage account information for enterprise application definitions**.</span></span>  
  
4.  <span data-ttu-id="36b1a-137">管理帳戶資訊的企業應用程式定義，在選取**EchoSSO**從**企業應用程式定義**清單。</span><span class="sxs-lookup"><span data-stu-id="36b1a-137">On the Manage Account Information for an Enterprise Application Definition, select **EchoSSO** from the **Enterprise application definition** list.</span></span>  
  
5.  <span data-ttu-id="36b1a-138">在**群組帳戶名稱**欄位中，輸入將用來保護此應用程式定義的 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="36b1a-138">In the **Group account name** field, type the Windows group that will be used to secure this application definition.</span></span> <span data-ttu-id="36b1a-139">例如， **DOMAIN\Domain 使用者**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-139">For example, **DOMAIN\Domain Users**.</span></span>  
  
6.  <span data-ttu-id="36b1a-140">按一下 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-140">Click **Set**.</span></span>  
  
7.  <span data-ttu-id="36b1a-141">在提供 EchoSSO 帳戶資訊 頁面上，在**Username**欄位類型**testuser**，然後在**密碼**欄位類型**testpassword**.</span><span class="sxs-lookup"><span data-stu-id="36b1a-141">On the Provide EchoSSO Account Information page, in the **Username** field type **testuser**, and then in the **Password** field type **testpassword**.</span></span>  
  
8.  <span data-ttu-id="36b1a-142">按一下**確定**，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-142">Click **OK**, and then click **Done**.</span></span>  
  
## <a name="creating-a-shared-services-provider-and-importing-the-application-definition-file"></a><span data-ttu-id="36b1a-143">建立共用服務提供者並匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="36b1a-143">Creating a Shared Services Provider and importing the application definition file</span></span>  
 <span data-ttu-id="36b1a-144">共用服務提供者 (SSP) 是共用的服務和其支援資源的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="36b1a-144">A Shared Services Provider (SSP) is a logical grouping of shared services and their supporting resources.</span></span> <span data-ttu-id="36b1a-145">您可以使用 SharePoint 管理中心主控台，以建立 SSP。</span><span class="sxs-lookup"><span data-stu-id="36b1a-145">You can create an SSP by using the SharePoint Central Administration Console.</span></span> <span data-ttu-id="36b1a-146">這個範例適用於任何 ssp。</span><span class="sxs-lookup"><span data-stu-id="36b1a-146">This example will work in any SSP.</span></span> <span data-ttu-id="36b1a-147">如需建立 SSP 的詳細資訊，請參閱 「 章概觀： 建立及設定共用服務提供者 」 在[http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119)。</span><span class="sxs-lookup"><span data-stu-id="36b1a-147">For more information about creating an SSP, see “Chapter overview: Create and Configure Shared Services Providers” at [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).</span></span>  
  
### <a name="to-import-the-application-definition-file"></a><span data-ttu-id="36b1a-148">若要匯入應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="36b1a-148">To import the application definition file</span></span>  
  
1.  <span data-ttu-id="36b1a-149">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="36b1a-149">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="36b1a-150">在**啟動**功能表上，指向**所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="36b1a-150">On the **Start** menu, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="36b1a-151">在左側瀏覽窗格中，按一下您要匯入應用程式定義的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="36b1a-151">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3.  <span data-ttu-id="36b1a-152">在**商務資料目錄**區段中，按一下**匯入應用程式定義**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-152">In the **Business Data Catalog** section, click **Import application definition**.</span></span>  
  
4.  <span data-ttu-id="36b1a-153">在匯入應用程式定義 頁面上，按一下 **瀏覽**，然後選取 EchoWS.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="36b1a-153">On the Import Application Definition page, click **Browse**, and then select the EchoWS.xml file.</span></span>  
  
5.  <span data-ttu-id="36b1a-154">按一下**匯入**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-154">Click **Import**, and then click **OK**.</span></span>  
  
## <a name="creating-web-parts"></a><span data-ttu-id="36b1a-155">建立 Web 組件</span><span class="sxs-lookup"><span data-stu-id="36b1a-155">Creating Web Parts</span></span>  
 <span data-ttu-id="36b1a-156">您現在必須在您要使用編輯器中建立商務資料目錄定義的方法執行個體的 SharePoint 網站中建立 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="36b1a-156">You must now create Web Parts in your SharePoint site to use the method instance created in the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="36b1a-157">Web 組件是資訊的可重複使用的元件，可以包含任何一種 Web 架構，包括分析、 共同作業，和資料庫資訊。</span><span class="sxs-lookup"><span data-stu-id="36b1a-157">Web Parts are reusable components that can contain any kind of Web-based information, including analytical, collaborative, and database information.</span></span>  
  
#### <a name="to-create-a-web-part-page"></a><span data-ttu-id="36b1a-158">若要建立 Web 組件頁面</span><span class="sxs-lookup"><span data-stu-id="36b1a-158">To create a Web Part page</span></span>  
  
1.  <span data-ttu-id="36b1a-159">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="36b1a-159">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="36b1a-160">在**啟動**功能表上，指向**所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="36b1a-160">On the **Start** menu, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="36b1a-161">在左側瀏覽窗格中，按一下您匯入應用程式定義檔的 SSP 的名稱。</span><span class="sxs-lookup"><span data-stu-id="36b1a-161">In the left navigation pane, click the name of the SSP in which you imported the application definition file.</span></span>  
  
3.  <span data-ttu-id="36b1a-162">在右上角的 共用服務管理 頁面上，按一下 **網站動作**，然後按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-162">On the Shared Services Administration page, in the upper-right corner, click **Site Actions**, and then click **Create**.</span></span>  
  
     <span data-ttu-id="36b1a-163">![建立網站動作](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/13f43659-ef61-48db-ac19-2d553367ec7e.gif "13f43659-ef61-48db-ac19-2d553367ec7e")</span><span class="sxs-lookup"><span data-stu-id="36b1a-163">![Create Site Actions](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/13f43659-ef61-48db-ac19-2d553367ec7e.gif "13f43659-ef61-48db-ac19-2d553367ec7e")</span></span>  
  
4.  <span data-ttu-id="36b1a-164">在**建立**頁面上，於**網頁**區段中，按一下**Web 組件頁面**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-164">On the **Create** page, in the **Web Pages** section, click **Web Part Page**.</span></span>  
  
5.  <span data-ttu-id="36b1a-165">在新的 Web 組件 頁面上，在**名稱**欄位中，輸入**EchoPart**，然後選取**整頁、 垂直**從**選擇版面配置範本**清單。</span><span class="sxs-lookup"><span data-stu-id="36b1a-165">On the New Web Part page, in the **Name** field, type **EchoPart**, and then select **Full Page, Vertical** from the **Chose a Layout Template** list.</span></span>  
  
6.  <span data-ttu-id="36b1a-166">按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-166">Click **Create**.</span></span>  
  
#### <a name="to-add-a-business-data-web-part"></a><span data-ttu-id="36b1a-167">若要將商務資料 Web 組件</span><span class="sxs-lookup"><span data-stu-id="36b1a-167">To add a Business Data Web Part</span></span>  
  
1.  <span data-ttu-id="36b1a-168">按一下**新增網頁組件**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-168">Click **Add a Web Part**.</span></span>  
  
2.  <span data-ttu-id="36b1a-169">在**新增網頁組件**對話方塊中，選取**商務資料清單**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-169">In the **Add Web Parts** dialog box, select **Business Data List**, and then click **Add**.</span></span>  
  
     <span data-ttu-id="36b1a-170">![商務資料清單](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cd9e6bc8-c37e-49d2-9eaa-77246bb593df.gif "cd9e6bc8-c37e-49d2-9eaa-77246bb593df")</span><span class="sxs-lookup"><span data-stu-id="36b1a-170">![Business Data List](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cd9e6bc8-c37e-49d2-9eaa-77246bb593df.gif "cd9e6bc8-c37e-49d2-9eaa-77246bb593df")</span></span>  
  
3.  <span data-ttu-id="36b1a-171">按一下**開啟工具窗格**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-171">Click **Open the tool pane**.</span></span>  
  
4.  <span data-ttu-id="36b1a-172">在右窗格中，開啟 [商務資料清單] 工具窗格。</span><span class="sxs-lookup"><span data-stu-id="36b1a-172">The Business Data List tool pane opens in the right pane.</span></span> <span data-ttu-id="36b1a-173">在**商務資料清單** 區段中，針對**類型**欄位中，按一下**瀏覽** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="36b1a-173">In the **Business Data List** section, for the **Type** field, click the **Browse** button.</span></span>  
  
     <span data-ttu-id="36b1a-174">![選取類型](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a054ed0e-0880-4154-9050-a00da356a4f6.gif "a054ed0e-0880-4154-9050-a00da356a4f6")</span><span class="sxs-lookup"><span data-stu-id="36b1a-174">![Select the Type](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a054ed0e-0880-4154-9050-a00da356a4f6.gif "a054ed0e-0880-4154-9050-a00da356a4f6")</span></span>  
  
5.  <span data-ttu-id="36b1a-175">在**商務資料型別選擇器**對話方塊中，選取**EchoWSLob_Instance**應用程式，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-175">In the **Business Data Type Picker** dialog box, select the **EchoWSLob_Instance** application, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="36b1a-176">商務資料清單] 工具窗格中，按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-176">On the Business Data List tool pane, click **OK**.</span></span>  
  
7.  <span data-ttu-id="36b1a-177">您會看到可讓您輸入要傳遞至 EchoGreetings 方法問候語值的欄位。</span><span class="sxs-lookup"><span data-stu-id="36b1a-177">You are presented with a field that allows you to enter a greeting value to pass to the EchoGreetings method.</span></span> <span data-ttu-id="36b1a-178">問候語欄位中輸入資料，然後按一下**抓取資料**。</span><span class="sxs-lookup"><span data-stu-id="36b1a-178">Enter data in the greeting field and click **Retrieve Data**.</span></span> <span data-ttu-id="36b1a-179">這會叫用回應配接器裝載於 IIS 的 EchoGreetings 方法，並傳回回應。</span><span class="sxs-lookup"><span data-stu-id="36b1a-179">This invokes the EchoGreetings method of the Echo adapter hosted in IIS and returns a response.</span></span>  
  
     <span data-ttu-id="36b1a-180">![EchoGreetings 清單](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f5a22fcd-2ae6-4384-9879-f0abd0255325.gif "f5a22fcd-2ae6-4384-9879-f0abd0255325")</span><span class="sxs-lookup"><span data-stu-id="36b1a-180">![EchoGreetings List](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f5a22fcd-2ae6-4384-9879-f0abd0255325.gif "f5a22fcd-2ae6-4384-9879-f0abd0255325")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="36b1a-181">名稱資料行不包含使用者資訊，但只會顯示 BDC。名稱。</span><span class="sxs-lookup"><span data-stu-id="36b1a-181">The name column does not contain the user information, but only displays BDC.Name.</span></span> <span data-ttu-id="36b1a-182">這是因為 BDC 預期只有簡單的記錄結構，並不會顯示 [名稱] 欄位所表示的複雜結構。</span><span class="sxs-lookup"><span data-stu-id="36b1a-182">This occurs because the BDC expects only a simple record structure, and does not display the complex structure represented by the name field.</span></span>  
  
8.  <span data-ttu-id="36b1a-183">按一下**結束編輯模式**從頁面的右上角。</span><span class="sxs-lookup"><span data-stu-id="36b1a-183">Click **Exit Edit Mode** from the upper corner of the page.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="36b1a-184">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="36b1a-184">What did I just do?</span></span>  
 <span data-ttu-id="36b1a-185">您已使用 SharePoint 3.0 管理中心 來匯入應用程式定義，並建立使用這個定義，叫用 EchoGreetings 作業的回應配接器的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="36b1a-185">You have used the SharePoint 3.0 Central Administration to import an application definition, and create Web Parts that use this definition to invoke the EchoGreetings operation of the Echo adapter.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="36b1a-186">後續步驟</span><span class="sxs-lookup"><span data-stu-id="36b1a-186">Next Steps</span></span>  
 <span data-ttu-id="36b1a-187">完成本教學課程。</span><span class="sxs-lookup"><span data-stu-id="36b1a-187">This tutorial is complete.</span></span> <span data-ttu-id="36b1a-188">如需使用商務資料目錄，請參閱 「 商務資料目錄 」 在[http://go.microsoft.com/fwlink/?LinkId=119921](http://go.microsoft.com/fwlink/?LinkId=119921)。</span><span class="sxs-lookup"><span data-stu-id="36b1a-188">For more information using the Business Data Catalog, see “Business Data Catalog” at [http://go.microsoft.com/fwlink/?LinkId=119921](http://go.microsoft.com/fwlink/?LinkId=119921).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b1a-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36b1a-189">See Also</span></span>  
 [<span data-ttu-id="36b1a-190">教學課程 3： 裝載在 IIS 中的回應配接器</span><span class="sxs-lookup"><span data-stu-id="36b1a-190">Tutorial 3: Hosting the Echo Adapter in IIS</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)