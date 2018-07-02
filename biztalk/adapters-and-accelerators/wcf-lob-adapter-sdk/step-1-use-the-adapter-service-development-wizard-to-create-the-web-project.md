---
title: 步驟 1： 使用配接器服務開發精靈來建立 Web 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ea0e33c-0d8d-4656-a6f0-3008b90f93f8
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fb8737f51f9e0b6afe3d61218f69015c1cd5d72
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984031"
---
# <a name="step-1-use-the-adapter-service-development-wizard-to-create-the-web-project"></a><span data-ttu-id="aa7b0-102">步驟 1： 使用配接器服務開發精靈來建立 Web 專案</span><span class="sxs-lookup"><span data-stu-id="aa7b0-102">Step 1: Use the Adapter Service Development Wizard to Create the Web Project</span></span>
<span data-ttu-id="aa7b0-103">![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span><span class="sxs-lookup"><span data-stu-id="aa7b0-103">![Step 1 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span></span>  
  
 <span data-ttu-id="aa7b0-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="aa7b0-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="aa7b0-105">在此步驟中，您會建立使用 Visual Studio 專案和[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-105">In this step, you create a project using Visual Studio and the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)].</span></span> <span data-ttu-id="aa7b0-106">[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]會收集介面卡、 作業和端點組態的相關資訊，並產生可部署至 IIS 的 Web 專案。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-106">The [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] collects information about the adapter, operations, and endpoint configurations, and generates a Web project that can then be deployed to IIS.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="aa7b0-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="aa7b0-107">Prerequisites</span></span>  
 <span data-ttu-id="aa7b0-108">您必須建置並部署 Echo 範例中所述[教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)再開始本教學課程。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-108">You must build and deploy the Echo sample described in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) before beginning this tutorial.</span></span>  
  
### <a name="to-start-the-adapter-service-development-wizard"></a><span data-ttu-id="aa7b0-109">若要啟動配接器服務開發精靈</span><span class="sxs-lookup"><span data-stu-id="aa7b0-109">To start the Adapter Service Development Wizard</span></span>  
  
1.  <span data-ttu-id="aa7b0-110">啟動 Visual Studio，然後在**檔案**功能表上，指向**新增**，然後按一下**網站**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-110">Start Visual Studio and then on the **File** menu, point to **New**, and then click **Web Site**.</span></span>  
  
2.  <span data-ttu-id="aa7b0-111">在 **新的網站**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="aa7b0-111">In the **New Web Site** dialog box, perform the following actions:</span></span>  
  
    |<span data-ttu-id="aa7b0-112">使用</span><span class="sxs-lookup"><span data-stu-id="aa7b0-112">Use this</span></span>|<span data-ttu-id="aa7b0-113">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="aa7b0-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="aa7b0-114">**語言**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-114">**Language**</span></span>|<span data-ttu-id="aa7b0-115">按一下  **Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-115">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="aa7b0-116">**範本**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-116">**Templates**</span></span>|<span data-ttu-id="aa7b0-117">按一下  **WCF 配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-117">Click **WCF Adapter Service**.</span></span>|  
    |<span data-ttu-id="aa7b0-118">**位置**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-118">**Location**</span></span>|<span data-ttu-id="aa7b0-119">選取 **檔案系統**，然後輸入**C:\Tutorials\EchoWeb**作為路徑。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-119">Select **File System**, and then type **C:\Tutorials\EchoWeb** as the path.</span></span>|  
  
3.  <span data-ttu-id="aa7b0-120">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-120">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="aa7b0-121">在 [**歡迎頁面**，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-121">On the **Welcome page**, click **Next**.</span></span>  
  
### <a name="to-select-the-adapter-and-uri"></a><span data-ttu-id="aa7b0-122">若要選取的配接器和 URI</span><span class="sxs-lookup"><span data-stu-id="aa7b0-122">To select the adapter and URI</span></span>  
  
1.  <span data-ttu-id="aa7b0-123">在上**選擇要產生服務合約作業**頁面上，選取**echoAdapterBindingV2**從**選取的繫結**下拉式清單，然後再按**設定**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-123">On the **Choose the operations to generate a service contract** page, select **echoAdapterBindingV2** from the **Select a binding** drop-down list, and then click **Configure**.</span></span>  
  
2.  <span data-ttu-id="aa7b0-124">上**安全性**索引標籤**設定介面卡**] 對話方塊中，將**用戶端認證類型**至**使用者名稱**，然後將 [ **使用者名稱認證**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa7b0-124">On the **Security** tab of the **Configure Adapter** dialog box, set **Client Credential type** to **Username**, and then set the **User name credentials** as follows:</span></span>  
  
    |<span data-ttu-id="aa7b0-125">屬性</span><span class="sxs-lookup"><span data-stu-id="aa7b0-125">Property</span></span>|<span data-ttu-id="aa7b0-126">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="aa7b0-126">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="aa7b0-127">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-127">**User name**</span></span>|<span data-ttu-id="aa7b0-128">username</span><span class="sxs-lookup"><span data-stu-id="aa7b0-128">username</span></span>|  
    |<span data-ttu-id="aa7b0-129">**密碼**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-129">**Password**</span></span>|<span data-ttu-id="aa7b0-130">密碼</span><span class="sxs-lookup"><span data-stu-id="aa7b0-130">password</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="aa7b0-131">使用者名稱和密碼，在此輸入只會用來連接至配接器時執行的步驟，在精靈中，並在精靈完成之後，不會保留。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-131">The user name and password entered here are only used to connect to the adapter while performing the steps in the wizard, and are not preserved after the wizard completes.</span></span>  
  
3.  <span data-ttu-id="aa7b0-132">按一下  **URI 屬性**索引標籤，然後再設定屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa7b0-132">Click the **URI Properties** tab, and then set the properties as follows:</span></span>  
  
    |<span data-ttu-id="aa7b0-133">屬性</span><span class="sxs-lookup"><span data-stu-id="aa7b0-133">Property</span></span>|<span data-ttu-id="aa7b0-134">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="aa7b0-134">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="aa7b0-135">**應用程式**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-135">**Application**</span></span>|<span data-ttu-id="aa7b0-136">LobApplication</span><span class="sxs-lookup"><span data-stu-id="aa7b0-136">LobApplication</span></span>|  
    |<span data-ttu-id="aa7b0-137">**EnableAuthentication**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-137">**EnableAuthentication**</span></span>|<span data-ttu-id="aa7b0-138">True</span><span class="sxs-lookup"><span data-stu-id="aa7b0-138">True</span></span>|  
    |<span data-ttu-id="aa7b0-139">**主機名稱**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-139">**Hostname**</span></span>|<span data-ttu-id="aa7b0-140">lobhostname</span><span class="sxs-lookup"><span data-stu-id="aa7b0-140">lobhostname</span></span>|  
    |<span data-ttu-id="aa7b0-141">**EchoInUpperCase**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-141">**EchoInUpperCase**</span></span>|<span data-ttu-id="aa7b0-142">False</span><span class="sxs-lookup"><span data-stu-id="aa7b0-142">False</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="aa7b0-143">此處所選取的 URI 屬性將用來建立\<**用戶端**\>\<**端點**\> web.config 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-143">The URI properties selected here will be used to create the \<**client**\>\<**endpoint**\> elements in the web.config file.</span></span>  
  
4.  <span data-ttu-id="aa7b0-144">按一下 [**繫結屬性**] 索引標籤。請注意預設值，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-144">Click the **Binding Properties** tab. Note the default values, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aa7b0-145">繫結值將用來產生\<**繫結**\>\<**echoAdapterBindingV2** \> web.config 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-145">The binding values will be used to generate the \<**bindings**\>\<**echoAdapterBindingV2**\> elements in the web.config file.</span></span>  
  
### <a name="to-select-the-contract-and-operations"></a><span data-ttu-id="aa7b0-146">若要選取的合約和作業</span><span class="sxs-lookup"><span data-stu-id="aa7b0-146">To select the contract and operations</span></span>  
  
1.  <span data-ttu-id="aa7b0-147">在 **選擇要產生服務合約作業**頁面上，按一下**Connect**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-147">On the **Choose the operations to generate a service contract** page, click **Connect**.</span></span>  
  
2.  <span data-ttu-id="aa7b0-148">在 **選取類別目錄**樹狀目錄中，選取**主要類別**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-148">In the **Select a category** tree, select **Main Category**.</span></span> <span data-ttu-id="aa7b0-149">這會填入**可用的類別和作業**清單。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-149">This populates the **Available categories and operations** list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aa7b0-150">您也可以輸入中的搜尋詞彙**分類中的搜尋**欄位，以尋找包含搜尋詞彙的任何作業。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-150">You can also enter a search term in the **Search in category** field to find any operations that contain the search term.</span></span>  
  
3.  <span data-ttu-id="aa7b0-151">在 **可用的類別和作業**清單中，選取**EchoGreetings** ，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-151">In the **Available categories and operations** list, select **EchoGreetings** and click **Add**.</span></span> <span data-ttu-id="aa7b0-152">這會將 EchoGreetings 作業移**新增的類別和作業**清單。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-152">This moves the EchoGreetings operation to the **Added categories and operations** list.</span></span> <span data-ttu-id="aa7b0-153">此處所選取的作業將會公開用戶端應用程式，透過精靈所產生的用戶端 proxy 程式碼。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-153">The operations selected here will be exposed to client applications through the client proxy code generated by the wizard.</span></span>  
  
     <span data-ttu-id="aa7b0-154">![選取合約與操作](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/de497b32-c820-480f-84f3-a9d0d2ded86b.gif "de497b32-c820-480f-84f3-a9d0d2ded86b")</span><span class="sxs-lookup"><span data-stu-id="aa7b0-154">![Select Contract and Operations](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/de497b32-c820-480f-84f3-a9d0d2ded86b.gif "de497b32-c820-480f-84f3-a9d0d2ded86b")</span></span>  
  
4.  <span data-ttu-id="aa7b0-155">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-155">Click **Next**.</span></span>  
  
### <a name="to-configure-service-and-endpoint-behavior"></a><span data-ttu-id="aa7b0-156">若要設定服務和端點行為</span><span class="sxs-lookup"><span data-stu-id="aa7b0-156">To configure service and endpoint behavior</span></span>  
  
1.  <span data-ttu-id="aa7b0-157">在 **設定服務與端點行為**頁面上，輸入下列值**服務行為組態**:</span><span class="sxs-lookup"><span data-stu-id="aa7b0-157">On the **Configure service and endpoint behaviors** page, enter the following values for **Service Behavior Configuration**:</span></span>  
  
    |<span data-ttu-id="aa7b0-158">屬性</span><span class="sxs-lookup"><span data-stu-id="aa7b0-158">Property</span></span>|<span data-ttu-id="aa7b0-159">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="aa7b0-159">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="aa7b0-160">**EnableMetadataExchange**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-160">**EnableMetadataExchange**</span></span>|<span data-ttu-id="aa7b0-161">True</span><span class="sxs-lookup"><span data-stu-id="aa7b0-161">True</span></span>|  
    |<span data-ttu-id="aa7b0-162">**IncludeExceptionDetailsinFault**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-162">**IncludeExceptionDetailsinFault**</span></span>|<span data-ttu-id="aa7b0-163">True</span><span class="sxs-lookup"><span data-stu-id="aa7b0-163">True</span></span>|  
    |<span data-ttu-id="aa7b0-164">**名稱**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-164">**Name**</span></span>|<span data-ttu-id="aa7b0-165">customServiceBehavior</span><span class="sxs-lookup"><span data-stu-id="aa7b0-165">customServiceBehavior</span></span>|  
    |<span data-ttu-id="aa7b0-166">**UseServiceCertificate**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-166">**UseServiceCertificate**</span></span>|<span data-ttu-id="aa7b0-167">False</span><span class="sxs-lookup"><span data-stu-id="aa7b0-167">False</span></span>|  
  
     <span data-ttu-id="aa7b0-168">這些值會用來填入\< **serviceBehaviors**\>。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-168">These values are used to populate the \<**serviceBehaviors**\>.</span></span>  
  
2.  <span data-ttu-id="aa7b0-169">輸入下列值**端點行為組態**:</span><span class="sxs-lookup"><span data-stu-id="aa7b0-169">Enter the following values for **Endpoint Behavior Configuration**:</span></span>  
  
    |<span data-ttu-id="aa7b0-170">屬性</span><span class="sxs-lookup"><span data-stu-id="aa7b0-170">Property</span></span>|<span data-ttu-id="aa7b0-171">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="aa7b0-171">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="aa7b0-172">**名稱**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-172">**Name**</span></span>|<span data-ttu-id="aa7b0-173">customEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="aa7b0-173">customEndpointBehavior</span></span>|  
    |<span data-ttu-id="aa7b0-174">**AuthenticationType**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-174">**AuthenticationType**</span></span>|<span data-ttu-id="aa7b0-175">**HTTPUsernamePassword**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-175">**HTTPUsernamePassword**</span></span>|  
    |<span data-ttu-id="aa7b0-176">**UsernameHeader**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-176">**UsernameHeader**</span></span>|<span data-ttu-id="aa7b0-177">MyUserHeader</span><span class="sxs-lookup"><span data-stu-id="aa7b0-177">MyUserHeader</span></span>|  
    |<span data-ttu-id="aa7b0-178">**PasswordHeader**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-178">**PasswordHeader**</span></span>|<span data-ttu-id="aa7b0-179">MyPassHeader</span><span class="sxs-lookup"><span data-stu-id="aa7b0-179">MyPassHeader</span></span>|  
  
     <span data-ttu-id="aa7b0-180">這些值將用來指定**adapterSecurityBridgeType**中 <**endpointBehaviors** web.confg 中的項目。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-180">These values will be used to specify the **adapterSecurityBridgeType** in the <**endpointBehaviors** element in web.confg.</span></span>  
  
     <span data-ttu-id="aa7b0-181">![端點組態](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3fd5784c-64e5-47c1-9a6f-10f12f77f726.gif "3fd5784c-64e5-47c1-9a6f-10f12f77f726")</span><span class="sxs-lookup"><span data-stu-id="aa7b0-181">![Endpoint Configuration](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3fd5784c-64e5-47c1-9a6f-10f12f77f726.gif "3fd5784c-64e5-47c1-9a6f-10f12f77f726")</span></span>  
  
3.  <span data-ttu-id="aa7b0-182">按 **[下一步]**</span><span class="sxs-lookup"><span data-stu-id="aa7b0-182">Click **Next**</span></span>  
  
### <a name="to-configure-the-binding"></a><span data-ttu-id="aa7b0-183">若要設定繫結</span><span class="sxs-lookup"><span data-stu-id="aa7b0-183">To configure the binding</span></span>  
  
1. <span data-ttu-id="aa7b0-184">在上**設定的服務端點繫結和位址**頁面上，選取**BindingConfiguration**中的項目**設定的位址和合約繫結**，及然後按一下省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-184">On the **Configure the service endpoint binding and address** page, select the **BindingConfiguration** entry in **Configure the address and binding for the contract**, and then click the ellipsis (**…**) button.</span></span>  
  
2. <span data-ttu-id="aa7b0-185">中**自訂繫結** 對話方塊中，將**模式**來**TransportWithMessageCredential**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-185">In the **Customize Binding** dialog box, set **Mode** to **TransportWithMessageCredential**, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="aa7b0-186">按一下 [**套用**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-186">Click **Apply**, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="aa7b0-187">在 **摘要**頁面上，檢閱的合約和作業為此專案中，選取，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-187">On the **Summary** page, review the contracts and operations selected for this project, and then click **Finish**.</span></span> <span data-ttu-id="aa7b0-188">您會看到 EchoWeb 方案，其中包含所建立的專案檔案 [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa7b0-188">You will be presented with the EchoWeb solution, which contains the project files created by the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="aa7b0-189">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="aa7b0-189">What did I just do?</span></span>  
 <span data-ttu-id="aa7b0-190">在此步驟中，您已使用[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]來產生 Web 專案，當發行至 IIS，會在開發 Echo 配接器的主機[教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)在 IIS 程序。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-190">In this step, you used the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] to generate a Web project that, when published to IIS, will host the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) in the IIS process.</span></span> <span data-ttu-id="aa7b0-191">產生的 Web 專案可讓 Web 服務和 WCF 用戶端存取選取的作業。</span><span class="sxs-lookup"><span data-stu-id="aa7b0-191">The resulting Web project allows Web Services and WCF clients to access the selected operations.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="aa7b0-192">後續步驟</span><span class="sxs-lookup"><span data-stu-id="aa7b0-192">Next Steps</span></span>  
 <span data-ttu-id="aa7b0-193">若要建置和部署 Web 專案，請繼續到[步驟 2： 部署 Web 專案](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)</span><span class="sxs-lookup"><span data-stu-id="aa7b0-193">To build and deploy the Web project, proceed to [Step 2: Deploy the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa7b0-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa7b0-194">See Also</span></span>  
 [<span data-ttu-id="aa7b0-195">教學課程 1：開發 Echo 配接器</span><span class="sxs-lookup"><span data-stu-id="aa7b0-195">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)