---
title: "步驟 1： 建立 Web 專案中使用配接器服務開發精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ea0e33c-0d8d-4656-a6f0-3008b90f93f8
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1144b7e6827882b37f6f9991a7315cdc3cdbb88d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-use-the-adapter-service-development-wizard-to-create-the-web-project"></a><span data-ttu-id="b8b8b-102">步驟 1： 建立 Web 專案中使用配接器服務開發精靈</span><span class="sxs-lookup"><span data-stu-id="b8b8b-102">Step 1: Use the Adapter Service Development Wizard to Create the Web Project</span></span>
<span data-ttu-id="b8b8b-103">![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span><span class="sxs-lookup"><span data-stu-id="b8b8b-103">![Step 1 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span></span>  
  
 <span data-ttu-id="b8b8b-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="b8b8b-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="b8b8b-105">在此步驟中，您會建立使用 Visual Studio 專案和[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-105">In this step, you create a project using Visual Studio and the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)].</span></span> <span data-ttu-id="b8b8b-106">[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]會收集介面卡、 作業和端點組態的相關資訊，並產生可部署至 IIS 的 Web 專案。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-106">The [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] collects information about the adapter, operations, and endpoint configurations, and generates a Web project that can then be deployed to IIS.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b8b8b-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="b8b8b-107">Prerequisites</span></span>  
 <span data-ttu-id="b8b8b-108">您必須建置和部署 Echo 範例中所述[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)再開始本教學課程。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-108">You must build and deploy the Echo sample described in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) before beginning this tutorial.</span></span>  
  
### <a name="to-start-the-adapter-service-development-wizard"></a><span data-ttu-id="b8b8b-109">若要啟動配接器服務開發精靈</span><span class="sxs-lookup"><span data-stu-id="b8b8b-109">To start the Adapter Service Development Wizard</span></span>  
  
1.  <span data-ttu-id="b8b8b-110">啟動 Visual Studio，然後在**檔案**功能表上，指向**新增**，然後按一下 **網站**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-110">Start Visual Studio and then on the **File** menu, point to **New**, and then click **Web Site**.</span></span>  
  
2.  <span data-ttu-id="b8b8b-111">在**新網站**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b8b8b-111">In the **New Web Site** dialog box, perform the following actions:</span></span>  
  
    |<span data-ttu-id="b8b8b-112">使用</span><span class="sxs-lookup"><span data-stu-id="b8b8b-112">Use this</span></span>|<span data-ttu-id="b8b8b-113">動作</span><span class="sxs-lookup"><span data-stu-id="b8b8b-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b8b8b-114">**語言**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-114">**Language**</span></span>|<span data-ttu-id="b8b8b-115">按一下**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-115">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="b8b8b-116">**範本**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-116">**Templates**</span></span>|<span data-ttu-id="b8b8b-117">按一下**WCF 配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-117">Click **WCF Adapter Service**.</span></span>|  
    |<span data-ttu-id="b8b8b-118">**位置**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-118">**Location**</span></span>|<span data-ttu-id="b8b8b-119">選取**檔案系統**，然後輸入**C:\Tutorials\EchoWeb**做為路徑。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-119">Select **File System**, and then type **C:\Tutorials\EchoWeb** as the path.</span></span>|  
  
3.  <span data-ttu-id="b8b8b-120">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-120">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="b8b8b-121">在**歡迎頁面**，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-121">On the **Welcome page**, click **Next**.</span></span>  
  
### <a name="to-select-the-adapter-and-uri"></a><span data-ttu-id="b8b8b-122">若要選取的配接器和 URI</span><span class="sxs-lookup"><span data-stu-id="b8b8b-122">To select the adapter and URI</span></span>  
  
1.  <span data-ttu-id="b8b8b-123">在**選擇要產生服務合約的作業**頁面上，選取**echoAdapterBindingV2**從**選取繫結**下拉式清單，然後再按**設定**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-123">On the **Choose the operations to generate a service contract** page, select **echoAdapterBindingV2** from the **Select a binding** drop-down list, and then click **Configure**.</span></span>  
  
2.  <span data-ttu-id="b8b8b-124">上**安全性** 索引標籤**設定配接器** 對話方塊中，將**用戶端認證類型**至**Username**，然後設定  **使用者名稱認證**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b8b8b-124">On the **Security** tab of the **Configure Adapter** dialog box, set **Client Credential type** to **Username**, and then set the **User name credentials** as follows:</span></span>  
  
    |<span data-ttu-id="b8b8b-125">屬性</span><span class="sxs-lookup"><span data-stu-id="b8b8b-125">Property</span></span>|<span data-ttu-id="b8b8b-126">值</span><span class="sxs-lookup"><span data-stu-id="b8b8b-126">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b8b8b-127">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-127">**User name**</span></span>|<span data-ttu-id="b8b8b-128">username</span><span class="sxs-lookup"><span data-stu-id="b8b8b-128">username</span></span>|  
    |<span data-ttu-id="b8b8b-129">**密碼**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-129">**Password**</span></span>|<span data-ttu-id="b8b8b-130">密碼</span><span class="sxs-lookup"><span data-stu-id="b8b8b-130">password</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="b8b8b-131">使用者名稱和密碼，在此輸入只會用來連接至配接器時執行的步驟，在精靈中，並不會保留在精靈完成之後。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-131">The user name and password entered here are only used to connect to the adapter while performing the steps in the wizard, and are not preserved after the wizard completes.</span></span>  
  
3.  <span data-ttu-id="b8b8b-132">按一下**URI 屬性**索引標籤，然後再設定的屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b8b8b-132">Click the **URI Properties** tab, and then set the properties as follows:</span></span>  
  
    |<span data-ttu-id="b8b8b-133">屬性</span><span class="sxs-lookup"><span data-stu-id="b8b8b-133">Property</span></span>|<span data-ttu-id="b8b8b-134">值</span><span class="sxs-lookup"><span data-stu-id="b8b8b-134">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b8b8b-135">**應用程式**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-135">**Application**</span></span>|<span data-ttu-id="b8b8b-136">LobApplication</span><span class="sxs-lookup"><span data-stu-id="b8b8b-136">LobApplication</span></span>|  
    |<span data-ttu-id="b8b8b-137">**EnableAuthentication**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-137">**EnableAuthentication**</span></span>|<span data-ttu-id="b8b8b-138">True</span><span class="sxs-lookup"><span data-stu-id="b8b8b-138">True</span></span>|  
    |<span data-ttu-id="b8b8b-139">**主機名稱**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-139">**Hostname**</span></span>|<span data-ttu-id="b8b8b-140">lobhostname</span><span class="sxs-lookup"><span data-stu-id="b8b8b-140">lobhostname</span></span>|  
    |<span data-ttu-id="b8b8b-141">**EchoInUpperCase**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-141">**EchoInUpperCase**</span></span>|<span data-ttu-id="b8b8b-142">False</span><span class="sxs-lookup"><span data-stu-id="b8b8b-142">False</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="b8b8b-143">在這裡選取的 URI 屬性將用來建立\<**用戶端**\>\<**端點**\> web.config 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-143">The URI properties selected here will be used to create the \<**client**\>\<**endpoint**\> elements in the web.config file.</span></span>  
  
4.  <span data-ttu-id="b8b8b-144">按一下**繫結屬性**] 索引標籤。預設值，請注意，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-144">Click the **Binding Properties** tab. Note the default values, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8b8b-145">繫結值將會用來產生\<**繫結**\>\<**echoAdapterBindingV2** \> web.config 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-145">The binding values will be used to generate the \<**bindings**\>\<**echoAdapterBindingV2**\> elements in the web.config file.</span></span>  
  
### <a name="to-select-the-contract-and-operations"></a><span data-ttu-id="b8b8b-146">若要選取的合約和作業</span><span class="sxs-lookup"><span data-stu-id="b8b8b-146">To select the contract and operations</span></span>  
  
1.  <span data-ttu-id="b8b8b-147">在**選擇要產生服務合約的作業**頁面上，按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-147">On the **Choose the operations to generate a service contract** page, click **Connect**.</span></span>  
  
2.  <span data-ttu-id="b8b8b-148">在**選取類別目錄**樹狀目錄中，選取**主要類別**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-148">In the **Select a category** tree, select **Main Category**.</span></span> <span data-ttu-id="b8b8b-149">如此即會填入**可用的類別和作業**清單。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-149">This populates the **Available categories and operations** list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8b8b-150">您也可以輸入中的搜尋詞彙**類別目錄中的搜尋**欄位以尋找包含搜尋詞彙的任何作業。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-150">You can also enter a search term in the **Search in category** field to find any operations that contain the search term.</span></span>  
  
3.  <span data-ttu-id="b8b8b-151">在**可用的類別和作業**清單中，選取**EchoGreetings**按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-151">In the **Available categories and operations** list, select **EchoGreetings** and click **Add**.</span></span> <span data-ttu-id="b8b8b-152">這會將 EchoGreetings 作業**加入的類別和作業**清單。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-152">This moves the EchoGreetings operation to the **Added categories and operations** list.</span></span> <span data-ttu-id="b8b8b-153">在這裡選取的作業將會公開給用戶端應用程式可以透過精靈所產生的用戶端 proxy 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-153">The operations selected here will be exposed to client applications through the client proxy code generated by the wizard.</span></span>  
  
     <span data-ttu-id="b8b8b-154">![選取合約與操作](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/de497b32-c820-480f-84f3-a9d0d2ded86b.gif "de497b32-c820-480f-84f3-a9d0d2ded86b")</span><span class="sxs-lookup"><span data-stu-id="b8b8b-154">![Select Contract and Operations](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/de497b32-c820-480f-84f3-a9d0d2ded86b.gif "de497b32-c820-480f-84f3-a9d0d2ded86b")</span></span>  
  
4.  <span data-ttu-id="b8b8b-155">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-155">Click **Next**.</span></span>  
  
### <a name="to-configure-service-and-endpoint-behavior"></a><span data-ttu-id="b8b8b-156">若要設定服務與端點行為</span><span class="sxs-lookup"><span data-stu-id="b8b8b-156">To configure service and endpoint behavior</span></span>  
  
1.  <span data-ttu-id="b8b8b-157">在**設定服務與端點行為**頁面上，輸入下列值**服務行為組態**:</span><span class="sxs-lookup"><span data-stu-id="b8b8b-157">On the **Configure service and endpoint behaviors** page, enter the following values for **Service Behavior Configuration**:</span></span>  
  
    |<span data-ttu-id="b8b8b-158">屬性</span><span class="sxs-lookup"><span data-stu-id="b8b8b-158">Property</span></span>|<span data-ttu-id="b8b8b-159">值</span><span class="sxs-lookup"><span data-stu-id="b8b8b-159">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b8b8b-160">**EnableMetadataExchange**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-160">**EnableMetadataExchange**</span></span>|<span data-ttu-id="b8b8b-161">True</span><span class="sxs-lookup"><span data-stu-id="b8b8b-161">True</span></span>|  
    |<span data-ttu-id="b8b8b-162">**IncludeExceptionDetailsinFault**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-162">**IncludeExceptionDetailsinFault**</span></span>|<span data-ttu-id="b8b8b-163">True</span><span class="sxs-lookup"><span data-stu-id="b8b8b-163">True</span></span>|  
    |<span data-ttu-id="b8b8b-164">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-164">**Name**</span></span>|<span data-ttu-id="b8b8b-165">customServiceBehavior</span><span class="sxs-lookup"><span data-stu-id="b8b8b-165">customServiceBehavior</span></span>|  
    |<span data-ttu-id="b8b8b-166">**UseServiceCertificate**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-166">**UseServiceCertificate**</span></span>|<span data-ttu-id="b8b8b-167">False</span><span class="sxs-lookup"><span data-stu-id="b8b8b-167">False</span></span>|  
  
     <span data-ttu-id="b8b8b-168">這些值可用來填入\< **serviceBehaviors**\>。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-168">These values are used to populate the \<**serviceBehaviors**\>.</span></span>  
  
2.  <span data-ttu-id="b8b8b-169">輸入下列值**端點行為組態**:</span><span class="sxs-lookup"><span data-stu-id="b8b8b-169">Enter the following values for **Endpoint Behavior Configuration**:</span></span>  
  
    |<span data-ttu-id="b8b8b-170">屬性</span><span class="sxs-lookup"><span data-stu-id="b8b8b-170">Property</span></span>|<span data-ttu-id="b8b8b-171">值</span><span class="sxs-lookup"><span data-stu-id="b8b8b-171">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b8b8b-172">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-172">**Name**</span></span>|<span data-ttu-id="b8b8b-173">customEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="b8b8b-173">customEndpointBehavior</span></span>|  
    |<span data-ttu-id="b8b8b-174">**AuthenticationType**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-174">**AuthenticationType**</span></span>|<span data-ttu-id="b8b8b-175">**HTTPUsernamePassword**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-175">**HTTPUsernamePassword**</span></span>|  
    |<span data-ttu-id="b8b8b-176">**UsernameHeader**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-176">**UsernameHeader**</span></span>|<span data-ttu-id="b8b8b-177">MyUserHeader</span><span class="sxs-lookup"><span data-stu-id="b8b8b-177">MyUserHeader</span></span>|  
    |<span data-ttu-id="b8b8b-178">**PasswordHeader**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-178">**PasswordHeader**</span></span>|<span data-ttu-id="b8b8b-179">MyPassHeader</span><span class="sxs-lookup"><span data-stu-id="b8b8b-179">MyPassHeader</span></span>|  
  
     <span data-ttu-id="b8b8b-180">這些值會用來指定**adapterSecurityBridgeType**中 <**endpointBehaviors** web.confg 中的項目。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-180">These values will be used to specify the **adapterSecurityBridgeType** in the <**endpointBehaviors** element in web.confg.</span></span>  
  
     <span data-ttu-id="b8b8b-181">![端點組態](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3fd5784c-64e5-47c1-9a6f-10f12f77f726.gif "3fd5784c-64e5-47c1-9a6f-10f12f77f726")</span><span class="sxs-lookup"><span data-stu-id="b8b8b-181">![Endpoint Configuration](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3fd5784c-64e5-47c1-9a6f-10f12f77f726.gif "3fd5784c-64e5-47c1-9a6f-10f12f77f726")</span></span>  
  
3.  <span data-ttu-id="b8b8b-182">按 **[下一步]**</span><span class="sxs-lookup"><span data-stu-id="b8b8b-182">Click **Next**</span></span>  
  
### <a name="to-configure-the-binding"></a><span data-ttu-id="b8b8b-183">若要設定的繫結</span><span class="sxs-lookup"><span data-stu-id="b8b8b-183">To configure the binding</span></span>  
  
1.  <span data-ttu-id="b8b8b-184">在**設定服務端點繫結與位址**頁面上，選取**BindingConfiguration**中的項目**設定的位址和合約繫結**，和然後按一下省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-184">On the **Configure the service endpoint binding and address** page, select the **BindingConfiguration** entry in **Configure the address and binding for the contract**, and then click the ellipsis (**…**) button.</span></span>  
  
2.  <span data-ttu-id="b8b8b-185">中**自訂繫結**] 對話方塊中，將**模式**至**TransportWithMessageCredential**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-185">In the **Customize Binding** dialog box, set **Mode** to **TransportWithMessageCredential**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b8b8b-186">按一下**套用**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-186">Click **Apply**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="b8b8b-187">在**摘要**頁面上，檢閱的合約和作業對於此專案中，選取，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-187">On the **Summary** page, review the contracts and operations selected for this project, and then click **Finish**.</span></span> <span data-ttu-id="b8b8b-188">您會看到有 EchoWeb 解決方案，其中包含所建立的專案檔案[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8b8b-188">You will be presented with the EchoWeb solution, which contains the project files created by the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="b8b8b-189">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="b8b8b-189">What did I just do?</span></span>  
 <span data-ttu-id="b8b8b-190">在此步驟中，您已經使用[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]產生 Web 專案，當發行至 IIS，將回應配接器開發中的主機[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)在 IIS 中處理。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-190">In this step, you used the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] to generate a Web project that, when published to IIS, will host the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) in the IIS process.</span></span> <span data-ttu-id="b8b8b-191">產生的 Web 專案可讓 Web 服務和 WCF 用戶端存取選取的作業。</span><span class="sxs-lookup"><span data-stu-id="b8b8b-191">The resulting Web project allows Web Services and WCF clients to access the selected operations.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b8b8b-192">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b8b8b-192">Next Steps</span></span>  
 <span data-ttu-id="b8b8b-193">若要建置及部署 Web 專案，請到[步驟 2： 部署 Web 專案](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)</span><span class="sxs-lookup"><span data-stu-id="b8b8b-193">To build and deploy the Web project, proceed to [Step 2: Deploy the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b8b-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="b8b8b-194">See Also</span></span>  
 [<span data-ttu-id="b8b8b-195">教學課程 1：開發 Echo 配接器</span><span class="sxs-lookup"><span data-stu-id="b8b8b-195">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)