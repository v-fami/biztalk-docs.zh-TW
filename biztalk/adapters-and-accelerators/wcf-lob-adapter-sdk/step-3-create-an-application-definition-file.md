---
title: 步驟 3： 建立應用程式定義檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 843fafdb-571e-4da4-ad04-7dc7f23e03ac
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7a5e2919a4cfed649342fda82435211b059206d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988215"
---
# <a name="step-3-create-an-application-definition-file"></a><span data-ttu-id="db03e-102">步驟 3： 建立應用程式定義檔案</span><span class="sxs-lookup"><span data-stu-id="db03e-102">Step 3: Create an Application Definition File</span></span>
<span data-ttu-id="db03e-103">![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="db03e-103">![Step 3 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="db03e-104">**若要完成的時間：** 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="db03e-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="db03e-105">在 Microsoft Office SharePoint Server 的商務資料目錄 」 功能會公開，並從特定業務 (LOB) 應用程式的資料併入入口網站。</span><span class="sxs-lookup"><span data-stu-id="db03e-105">The Business Data Catalog feature in Microsoft Office SharePoint Server exposes and incorporates data from line-of-business (LOB) applications into portals.</span></span> <span data-ttu-id="db03e-106">若要併入您的入口網站中的這項資料，您必須建置可取用 Microsoft Office SharePoint Server 的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="db03e-106">To incorporate this data into your portal site, you must build an application definition file that Microsoft Office SharePoint Server can consume.</span></span>  
  
 <span data-ttu-id="db03e-107">在此步驟中，您可以使用 商務資料目錄定義編輯器工具，適用於 Microsoft Office SharePoint Server 2007 SDK，為商務資料目錄中建立的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="db03e-107">In this step you use the Business Data Catalog Definition Editor tool, available with the Microsoft Office SharePoint Server 2007 SDK, to create an application definition file for the Business Data Catalog.</span></span> <span data-ttu-id="db03e-108">這個定義檔描述 Echo 配接器的 EchoGreetings 方法，並將在稍後步驟中用來啟用 SharePoint 與配接器通訊。</span><span class="sxs-lookup"><span data-stu-id="db03e-108">This definition file describes the EchoGreetings method of the Echo adapter, and will be used in later steps to enable SharePoint to communicate with the adapter.</span></span>  
  
 <span data-ttu-id="db03e-109">Microsoft Office SharePoint Server 應用程式所建立的目的是讓您叫用 Echo 配接器的 EchoGreetings 方法並使用 SharePoint Web 組件的回應。</span><span class="sxs-lookup"><span data-stu-id="db03e-109">The purpose of the Microsoft Office SharePoint Server application that you are creating is to allow you to invoke the EchoGreetings method of the Echo adapter and return the response using a SharePoint Web Part.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="db03e-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="db03e-110">Prerequisites</span></span>  
 <span data-ttu-id="db03e-111">您應已完成[步驟 2： 將 Web 專案部署](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)。</span><span class="sxs-lookup"><span data-stu-id="db03e-111">You should have completed [Step 2: Deploy the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md).</span></span> <span data-ttu-id="db03e-112">您也必須可以存取以商務資料目錄定義編輯器，它會安裝為 Microsoft Office SharePoint Server 2007 SDK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="db03e-112">You must also have access to the Business Data Catalog Definition Editor, which is installed as part of the Microsoft Office SharePoint Server 2007 SDK.</span></span> <span data-ttu-id="db03e-113">您可以下載從 SDK [ http://go.microsoft.com/fwlink/?LinkId=104130 ](http://go.microsoft.com/fwlink/?LinkId=104130)。</span><span class="sxs-lookup"><span data-stu-id="db03e-113">You can download the SDK from [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).</span></span>  
  
## <a name="creating-an-application-definition-file"></a><span data-ttu-id="db03e-114">建立應用程式定義檔案</span><span class="sxs-lookup"><span data-stu-id="db03e-114">Creating an Application Definition File</span></span>  
 <span data-ttu-id="db03e-115">本主題提供逐步指示來建立裝載於 IIS 的 WCF 配接器的連接 SharePoint 商務資料目錄的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="db03e-115">This topic provides step-by-step instructions to create an application definition file for connecting the SharePoint Business Data Catalog with the WCF adapter hosted in IIS.</span></span>  
  
#### <a name="to-connect-to-the-wcf-adapter-service-and-create-entities"></a><span data-ttu-id="db03e-116">連接到 WCF 配接器服務，並建立實體</span><span class="sxs-lookup"><span data-stu-id="db03e-116">To connect to the WCF adapter service and create entities</span></span>  
  
1.  <span data-ttu-id="db03e-117">從 **[開始] 功能表**，指向**所有程式**，然後按一下**Microsoft Business Data Catalog Definition Editor**。</span><span class="sxs-lookup"><span data-stu-id="db03e-117">From the **Start menu**, point to **All Programs**, and then click **Microsoft Business Data Catalog Definition Editor**.</span></span>  
  
2.  <span data-ttu-id="db03e-118">在工具列上，按一下**新增 LOB 系統**。</span><span class="sxs-lookup"><span data-stu-id="db03e-118">On the toolbar, click **Add LOB System**.</span></span>  
  
3.  <span data-ttu-id="db03e-119">在 [新增 LOB 系統] 視窗中，按一下**連接到 web 服務**。</span><span class="sxs-lookup"><span data-stu-id="db03e-119">In the Add LOB System window, click **Connect to Webservice**.</span></span>  
  
4.  <span data-ttu-id="db03e-120">在  **URL**方塊中，輸入 WCF 服務的 URL。</span><span class="sxs-lookup"><span data-stu-id="db03e-120">In the **URL** box, type the URL for the WCF service.</span></span> <span data-ttu-id="db03e-121">這個 URL 必須以下列格式： `https://machinename/EchoWeb/EchoOutboundContract.svc?wsdl`</span><span class="sxs-lookup"><span data-stu-id="db03e-121">The URL must be in the following format: `https://machinename/EchoWeb/EchoOutboundContract.svc?wsdl`</span></span>  
  
5.  <span data-ttu-id="db03e-122">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="db03e-122">Click **Connect**.</span></span>  
  
6.  <span data-ttu-id="db03e-123">若要查看可用的作業，請按一下**新增 Web 方法** 索引標籤。您應該會看到 EchoGreetings 方法。</span><span class="sxs-lookup"><span data-stu-id="db03e-123">To see the available operations, click the **Add Web Method** tab. You should see the EchoGreetings method.</span></span> <span data-ttu-id="db03e-124">將方法拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="db03e-124">Drag the method to the Design Surface.</span></span>  
  
7.  <span data-ttu-id="db03e-125">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="db03e-125">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="db03e-126">在 **輸入 LOB 系統的名稱** 對話方塊中，輸入的名稱，在**LOB 系統名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="db03e-126">In the **Enter the name for the LOB System** dialog box, type a name in the **LOB System Name** box.</span></span> <span data-ttu-id="db03e-127">針對此範例中，輸入**EchoWSLOB**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="db03e-127">For this example, enter **EchoWSLOB**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="db03e-128">依序展開**EchoWSLob**節點，然後展開**實體**節點。</span><span class="sxs-lookup"><span data-stu-id="db03e-128">Expand the **EchoWSLob** node, and then expand the **Entities** node.</span></span> <span data-ttu-id="db03e-129">選取  **Entity0**然後在 屬性窗格中輸入**EchoGreetings**做為值**名稱**屬性。</span><span class="sxs-lookup"><span data-stu-id="db03e-129">Select **Entity0** and in the Properties pane type **EchoGreetings** as the value for the **Name** property.</span></span>  
  
     <span data-ttu-id="db03e-130">![實體名稱](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/942e7853-451e-4cf5-8884-09fb7d8dc19d.gif "942e7853-451e-4cf5-8884-09fb7d8dc19d")</span><span class="sxs-lookup"><span data-stu-id="db03e-130">![Entity Name](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/942e7853-451e-4cf5-8884-09fb7d8dc19d.gif "942e7853-451e-4cf5-8884-09fb7d8dc19d")</span></span>  
  
## <a name="specify-user-name-and-password-headers-for-the-method"></a><span data-ttu-id="db03e-131">指定使用者名稱和密碼標頭方法</span><span class="sxs-lookup"><span data-stu-id="db03e-131">Specify User Name and Password Headers for the Method</span></span>  
 <span data-ttu-id="db03e-132">在呼叫的 WCF 配接器時，您可能必須提供將傳遞至 LOB 系統的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="db03e-132">When calling a WCF adapter, you may have to provide user credentials that will be passed to the LOB system.</span></span> <span data-ttu-id="db03e-133">在 [步驟 1： 建立 Web 專案中使用配接器服務開發精靈](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md)，設定 Echo 配接器需要 MyUserHeader 和 MyPassHeader 欄位中，提供使用者名稱和密碼資訊。</span><span class="sxs-lookup"><span data-stu-id="db03e-133">In [Step 1: Use the Adapter Service Development Wizard to Create the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md), you configured the Echo adapter to require that user name and password information be provided in the MyUserHeader and MyPassHeader fields.</span></span> <span data-ttu-id="db03e-134">您現在必須使用此應用程式定義檔的相同欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="db03e-134">You must now use the same field names for this application definition file.</span></span>  
  
#### <a name="to-specify-user-name-and-password-headers"></a><span data-ttu-id="db03e-135">若要指定使用者名稱和密碼標頭</span><span class="sxs-lookup"><span data-stu-id="db03e-135">To specify user name and password headers</span></span>  
  
1.  <span data-ttu-id="db03e-136">在 [中繼資料物件] 窗格中，依序展開**EchoGreetings**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="db03e-136">In the Metadata Objects pane, expand the **EchoGreetings** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="db03e-137">按一下  **EchoGreetings**節點，然後在 屬性 窗格中，按一下 省略符號 **（...）** 按鈕**屬性**欄位。</span><span class="sxs-lookup"><span data-stu-id="db03e-137">Click the **EchoGreetings** node and, in the Properties pane, click the ellipsis **(…)** button in the **Properties** field.</span></span>  
  
3.  <span data-ttu-id="db03e-138">在 [PropertyView 集合編輯器] 視窗中，按一下 [**新增**，然後在**名稱**欄位屬性] 窗格中輸入**HttpHeaderUserName**。</span><span class="sxs-lookup"><span data-stu-id="db03e-138">In the PropertyView Collection Editor window, click **Add**, and in the **Name** field of the Property pane, type  **HttpHeaderUserName**.</span></span>  
  
     <span data-ttu-id="db03e-139">![指定使用者名稱標頭欄位](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/8da4d1b7-0792-407a-ba93-ba749138dd14.gif "8da4d1b7-0792-407a-ba93-ba749138dd14")</span><span class="sxs-lookup"><span data-stu-id="db03e-139">![Specify Username Header Fields](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/8da4d1b7-0792-407a-ba93-ba749138dd14.gif "8da4d1b7-0792-407a-ba93-ba749138dd14")</span></span>  
  
4.  <span data-ttu-id="db03e-140">在  **PropertyValue**欄位中，輸入**MyUserHeader**。</span><span class="sxs-lookup"><span data-stu-id="db03e-140">In the **PropertyValue**field, type **MyUserHeader**.</span></span>  
  
5.  <span data-ttu-id="db03e-141">按一下 **新增**，然後在 屬性窗格中輸入**HttpHeaderPassword**的 名稱 欄位中，然後輸入**MyPassHeader**如**PropertyValue**欄位。</span><span class="sxs-lookup"><span data-stu-id="db03e-141">Click **Add**, and in the Property pane type **HttpHeaderPassword** for the Name field, then type **MyPassHeader** for the **PropertyValue** field.</span></span>  
  
6.  <span data-ttu-id="db03e-142">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="db03e-142">Click **OK**.</span></span>  
  
## <a name="set-up-single-sign-on-for-connecting-to-the-echo-adapter"></a><span data-ttu-id="db03e-143">連線到 Echo 配接器設定單一登入設定</span><span class="sxs-lookup"><span data-stu-id="db03e-143">Set up Single Sign-On for Connecting to the Echo Adapter</span></span>  
 <span data-ttu-id="db03e-144">SharePoint 會使用從單一登入的資訊以驗證值填入 MyUserHeader 和 MyPassHeader。</span><span class="sxs-lookup"><span data-stu-id="db03e-144">SharePoint uses information from Single Sign-On to populate the MyUserHeader and MyPassHeader with authentication values.</span></span> <span data-ttu-id="db03e-145">若要以單一登入連結此應用程式定義檔，您必須提供 SecondarySsoApplicationId。</span><span class="sxs-lookup"><span data-stu-id="db03e-145">To link this application definition file to Single Sign-On, you must provide a SecondarySsoApplicationId.</span></span>  
  
#### <a name="to-set-the-secondaryssoapplicationid-property"></a><span data-ttu-id="db03e-146">若要設定 SecondarySsoApplicationId 屬性</span><span class="sxs-lookup"><span data-stu-id="db03e-146">To set the SecondarySsoApplicationId property</span></span>  
  
1. <span data-ttu-id="db03e-147">在 [中繼資料物件] 窗格中，依序展開**EchoWSLOB**節點，然後展開**執行個體**節點。</span><span class="sxs-lookup"><span data-stu-id="db03e-147">In the Metadata Objects pane, expand the **EchoWSLOB** node, and then expand the **Instances** node.</span></span>  
  
2. <span data-ttu-id="db03e-148">按一下  **EchoWSLOB_Instance**，在 屬性 窗格中，按一下省略符號<strong>（...）</strong>按鈕**屬性**欄位。</span><span class="sxs-lookup"><span data-stu-id="db03e-148">Click **EchoWSLOB_Instance**, and in the Properties pane, click the ellipsis <strong>(…)</strong>button in the **Properties** field.</span></span>  
  
3. <span data-ttu-id="db03e-149">在 [PropertyView 集合編輯器] 視窗中，按一下**新增**，然後在 [屬性] 窗格中，輸入**SecondarySsoApplicationId**中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="db03e-149">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **SecondarySsoApplicationId** in the **Name** field.</span></span>  
  
4. <span data-ttu-id="db03e-150">在  **PropertyValue**欄位中，輸入**EchoSSO**。</span><span class="sxs-lookup"><span data-stu-id="db03e-150">In the **PropertyValue** field, type **EchoSSO**.</span></span>  
  
    <span data-ttu-id="db03e-151">![設定 SecondarySsoApplicationId](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/68e6be61-77af-46b1-8ff0-b8538c526228.gif "68e6be61-77af-46b1-8ff0-b8538c526228")</span><span class="sxs-lookup"><span data-stu-id="db03e-151">![Set the SecondarySsoApplicationId](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/68e6be61-77af-46b1-8ff0-b8538c526228.gif "68e6be61-77af-46b1-8ff0-b8538c526228")</span></span>  
  
5. <span data-ttu-id="db03e-152">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="db03e-152">Click **OK**.</span></span>  
  
## <a name="create-input-filters-and-default-values"></a><span data-ttu-id="db03e-153">建立輸入篩選器和預設值</span><span class="sxs-lookup"><span data-stu-id="db03e-153">Create Input Filters and Default Values</span></span>  
 <span data-ttu-id="db03e-154">應用程式定義檔必須能夠接受使用者輸入可傳遞至 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="db03e-154">The application definition file must be able to  accept user input that can be passed to a Web service.</span></span> <span data-ttu-id="db03e-155">若要這麼做，您必須執行下列一組工作：</span><span class="sxs-lookup"><span data-stu-id="db03e-155">To accomplish this, you must perform the following set of tasks:</span></span>  
  
#### <a name="to-create-a-filter-and-map-it-to-the-greeting-parameter"></a><span data-ttu-id="db03e-156">若要建立篩選器，並將它對應至問候語參數</span><span class="sxs-lookup"><span data-stu-id="db03e-156">To create a filter, and map it to the greeting parameter</span></span>  
  
1.  <span data-ttu-id="db03e-157">在 [中繼資料物件] 窗格中，依序展開**EchoWSLOB**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="db03e-157">In the Metadata Objects pane, expand the **EchoWSLOB** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="db03e-158">依序展開**EchoGreetings**方法，以滑鼠右鍵按一下**篩選**，然後按一下**加入篩選**。</span><span class="sxs-lookup"><span data-stu-id="db03e-158">Expand the **EchoGreetings** method, right-click **Filters**, and then click **Add Filter**.</span></span>  
  
3.  <span data-ttu-id="db03e-159">在 [屬性] 窗格中，輸入**問候語**中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="db03e-159">In the Properties pane, type **Greeting** in the **Name** field.</span></span>  
  
     <span data-ttu-id="db03e-160">![設定篩選器名稱](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/74036b9e-7eec-4156-b238-840e67a2f00c.gif "74036b9e-7eec-4156-b238-840e67a2f00c")</span><span class="sxs-lookup"><span data-stu-id="db03e-160">![Set the Filter Name](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/74036b9e-7eec-4156-b238-840e67a2f00c.gif "74036b9e-7eec-4156-b238-840e67a2f00c")</span></span>  
  
4.  <span data-ttu-id="db03e-161">在 [中繼資料物件] 窗格中，依序展開**EchoWSLOB**節點，然後展開**方法**節點</span><span class="sxs-lookup"><span data-stu-id="db03e-161">In the Metadata Objects pane, expand the **EchoWSLOB** node, and then expand the **Methods** node</span></span>  
  
5.  <span data-ttu-id="db03e-162">依序展開**EchoGreetings**方法，然後展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="db03e-162">Expand the **EchoGreetings** method, and then expand the **Parameters** node.</span></span>  
  
6.  <span data-ttu-id="db03e-163">依序展開**問候語**節點，然後展開 第二個**問候語**節點。</span><span class="sxs-lookup"><span data-stu-id="db03e-163">Expand the **greeting** node, and then expand the second **greeting** node.</span></span>  
  
7.  <span data-ttu-id="db03e-164">按一下  **greetingText**節點，然後在 屬性 窗格中，選取**問候語**從**FilterDescriptor**清單。</span><span class="sxs-lookup"><span data-stu-id="db03e-164">Click the **greetingText** node, and in the Properties pane, select **Greeting** from the **FilterDescriptor** list.</span></span>  
  
#### <a name="to-create-a-finder-method-instance-for-the-echogreetings-method"></a><span data-ttu-id="db03e-165">若要建立 Finder 方法執行個體 EchoGreetings 方法</span><span class="sxs-lookup"><span data-stu-id="db03e-165">To create a Finder method instance for the EchoGreetings method</span></span>  
  
1.  <span data-ttu-id="db03e-166">在 [中繼資料物件] 窗格中，依序展開**EchoWSLOB**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="db03e-166">In the Metadata Objects pane, expand the **EchoWSLOB** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="db03e-167">依序展開**EchoGreetings**方法，以滑鼠右鍵按一下**執行個體**，然後按一下**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。</span><span class="sxs-lookup"><span data-stu-id="db03e-167">Expand the **EchoGreetings** method, right-click **Instances**, and then click **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
3.  <span data-ttu-id="db03e-168">在 建立方法執行個體 視窗中，按一下  **Finder**如**方法執行個體類型**，然後選取**傳回**的**傳回 TypeDescriptor**.</span><span class="sxs-lookup"><span data-stu-id="db03e-168">In the Create Method Instance window, click **Finder** for **Method Instance Type**, and then select **Return** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="db03e-169">![建立方法執行個體](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a932a7a0-c004-46bf-af5c-cc7392bafa43.gif "a932a7a0-c004-46bf-af5c-cc7392bafa43")</span><span class="sxs-lookup"><span data-stu-id="db03e-169">![Create the Method Instance](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a932a7a0-c004-46bf-af5c-cc7392bafa43.gif "a932a7a0-c004-46bf-af5c-cc7392bafa43")</span></span>  
  
4.  <span data-ttu-id="db03e-170">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="db03e-170">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="db03e-171">在 [屬性] 窗格中，輸入**EchoGreetings_Instance**中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="db03e-171">In the Properties pane, type **EchoGreetings_Instance** in the **Name** field.</span></span>  
  
#### <a name="to-set-default-parameters"></a><span data-ttu-id="db03e-172">若要設定預設參數</span><span class="sxs-lookup"><span data-stu-id="db03e-172">To set default parameters</span></span>  
  
1.  <span data-ttu-id="db03e-173">在 [中繼資料物件] 窗格中，依序展開**EchoWSLOB**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="db03e-173">In the Metadata Objects pane, expand the **EchoWSLOB** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="db03e-174">依序展開**EchoGreetings**方法，然後展開**執行個體**節點。</span><span class="sxs-lookup"><span data-stu-id="db03e-174">Expand the **EchoGreetings** method, and then expand the **Instances** node.</span></span>  
  
3.  <span data-ttu-id="db03e-175">選取  **EchoGreetings_Instance**方法執行個體，並在 屬性 窗格中，按一下 省略符號按鈕 （...），以在**DefaultValues**欄位。</span><span class="sxs-lookup"><span data-stu-id="db03e-175">Select the **EchoGreetings_Instance** method instance, and in the Properties pane, click the ellipsis button (…) in the **DefaultValues** field.</span></span>  
  
4.  <span data-ttu-id="db03e-176">在 編輯 視窗中，依序展開**問候語**節點，然後展開 第二個**問候語**節點。</span><span class="sxs-lookup"><span data-stu-id="db03e-176">In the Edit window, expand the **greeting** node, and then expand the second **greeting** node.</span></span> <span data-ttu-id="db03e-177">依序展開**名稱** 節點，直到完全顯示時的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="db03e-177">Expand the **name** node, until the tree structure is fully displayed.</span></span>  
  
5.  <span data-ttu-id="db03e-178">在 [編輯] 視窗中，設定的欄位值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="db03e-178">In the Edit window, set the field values as follows:</span></span>  
  
    |<span data-ttu-id="db03e-179">設定此項</span><span class="sxs-lookup"><span data-stu-id="db03e-179">Set this</span></span>|<span data-ttu-id="db03e-180">為此值</span><span class="sxs-lookup"><span data-stu-id="db03e-180">To this</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="db03e-181">**id**</span><span class="sxs-lookup"><span data-stu-id="db03e-181">**id**</span></span>|<span data-ttu-id="db03e-182">GUID 值，例如 27829ed4 583a-40 c 4 ad87 fb8cdd9dc98d。</span><span class="sxs-lookup"><span data-stu-id="db03e-182">A GUID value, for example 27829ed4-583a-40c4-ad87-fb8cdd9dc98d.</span></span>|  
    |<span data-ttu-id="db03e-183">**sentDateTime**</span><span class="sxs-lookup"><span data-stu-id="db03e-183">**sentDateTime**</span></span>|<span data-ttu-id="db03e-184">目前的日期和時間，例如 05/15/08 上午 9:12</span><span class="sxs-lookup"><span data-stu-id="db03e-184">The current date and time, for example 05/15/08 9:12 AM</span></span>|  
    |<span data-ttu-id="db03e-185">**firstName**</span><span class="sxs-lookup"><span data-stu-id="db03e-185">**firstName**</span></span>|<span data-ttu-id="db03e-186">第一個</span><span class="sxs-lookup"><span data-stu-id="db03e-186">First</span></span>|  
    |<span data-ttu-id="db03e-187">**middleName**</span><span class="sxs-lookup"><span data-stu-id="db03e-187">**middleName**</span></span>|<span data-ttu-id="db03e-188">Middle</span><span class="sxs-lookup"><span data-stu-id="db03e-188">Middle</span></span>|  
    |<span data-ttu-id="db03e-189">**lastName**</span><span class="sxs-lookup"><span data-stu-id="db03e-189">**lastName**</span></span>|<span data-ttu-id="db03e-190">最後一個</span><span class="sxs-lookup"><span data-stu-id="db03e-190">Last</span></span>|  
  
     <span data-ttu-id="db03e-191">![預設參數](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/70250957-9680-48ce-8bce-420ff18bb47a.gif "70250957-9680-48ce-8bce-420ff18bb47a")</span><span class="sxs-lookup"><span data-stu-id="db03e-191">![Default Parameters](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/70250957-9680-48ce-8bce-420ff18bb47a.gif "70250957-9680-48ce-8bce-420ff18bb47a")</span></span>  
  
6.  <span data-ttu-id="db03e-192">按一下 [ **關閉**]。</span><span class="sxs-lookup"><span data-stu-id="db03e-192">Click **Close**.</span></span>  
  
### <a name="to-export-the-application-definition-file"></a><span data-ttu-id="db03e-193">若要匯出的應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="db03e-193">To export the application definition file</span></span>  
  
1.  <span data-ttu-id="db03e-194">在 [中繼資料物件] 窗格中，以滑鼠右鍵按一下**EchoWSLOB**節點，然後再按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="db03e-194">In the Metadata Objects pane, right-click the **EchoWSLOB** node, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="db03e-195">將檔案儲存為 EchoWS.xml 中。</span><span class="sxs-lookup"><span data-stu-id="db03e-195">Save the file as EchoWS.xml.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="db03e-196">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="db03e-196">What did I just do?</span></span>  
 <span data-ttu-id="db03e-197">您已使用商務資料目錄定義編輯器工具來建立應用程式定義檔，可以匯入 Microsoft Office SharePoint Server 2007 來啟用與您在 IIS 中裝載的配接器的連線。</span><span class="sxs-lookup"><span data-stu-id="db03e-197">You have used the Business Data Catalog Definition Editor tool to create an application definition file that can be imported into Microsoft Office SharePoint Server 2007 to enable connectivity with your adapter that is hosted in IIS.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="db03e-198">後續步驟</span><span class="sxs-lookup"><span data-stu-id="db03e-198">Next Steps</span></span>  
 <span data-ttu-id="db03e-199">您現在必須建立 SharePoint 應用程式根據此步驟中建立的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="db03e-199">You must now create a SharePoint application based on the application definition file created in this step.</span></span> <span data-ttu-id="db03e-200">請參閱[步驟 4： 建立 Sharepoint 應用程式來存取配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-create-a-sharepoint-application-to-access-the-adapter.md)如需相關指示。</span><span class="sxs-lookup"><span data-stu-id="db03e-200">See [Step 4: Create a Sharepoint Application to Access the Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-create-a-sharepoint-application-to-access-the-adapter.md) for instructions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db03e-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db03e-201">See Also</span></span>  
 [<span data-ttu-id="db03e-202">教學課程 3：在 IIS 中裝載 Echo 配接器</span><span class="sxs-lookup"><span data-stu-id="db03e-202">Tutorial 3: Hosting the Echo Adapter in IIS</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)