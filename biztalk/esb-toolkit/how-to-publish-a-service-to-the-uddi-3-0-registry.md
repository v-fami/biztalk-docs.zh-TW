---
title: 如何： 將服務發佈至 UDDI 3.0 登錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2c3bd0ed-e5f1-43eb-98d1-e3247a565ba2
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb5ab38da9c78831b319d8c64e789b442fb6eef5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008015"
---
# <a name="how-to-publish-a-service-to-the-uddi-30-registry"></a><span data-ttu-id="77db6-102">如何： 將服務發佈至 UDDI 3.0 登錄</span><span class="sxs-lookup"><span data-stu-id="77db6-102">How to: Publish a Service to the UDDI 3.0 Registry</span></span>
## <a name="goal"></a><span data-ttu-id="77db6-103">目標</span><span class="sxs-lookup"><span data-stu-id="77db6-103">Goal</span></span>  
 <span data-ttu-id="77db6-104">本節示範如何使用 「 UDDI 服務網站來發佈 Web 服務端點可用於路由訊息，ESB 路線內解析從。</span><span class="sxs-lookup"><span data-stu-id="77db6-104">This section demonstrates how to use the UDDI Service site to publish a Web service endpoint that can be resolved from within an itinerary for the purpose of routing an ESB message.</span></span> <span data-ttu-id="77db6-105">您將複製現有的 PurchaseOrderSubmitOrderService 服務目前發行至登錄。</span><span class="sxs-lookup"><span data-stu-id="77db6-105">You will duplicate the existing PurchaseOrderSubmitOrderService service presently published to the registry.</span></span>  

 <span data-ttu-id="77db6-106">在本使用說明主題中，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="77db6-106">In this How-to topic, you will complete the following steps:</span></span>  

-   <span data-ttu-id="77db6-107">將服務發佈至通用描述、 探索與整合 (UDDI) 3 使用 「 UDDI 發行者 」 工具的登錄。</span><span class="sxs-lookup"><span data-stu-id="77db6-107">Publish a service to the Universal Description, Discovery, and Integration (UDDI) 3 registry using the UDDI Publisher tool.</span></span>  

-   <span data-ttu-id="77db6-108">測試使用路線傳閱解析使用 UDDI3 解析程式服務端點的服務發行集。</span><span class="sxs-lookup"><span data-stu-id="77db6-108">Test the service publication using an itinerary routing slip that resolves the service endpoint using a UDDI3 resolver.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="77db6-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="77db6-109">Prerequisites</span></span>  
 <span data-ttu-id="77db6-110">本使用說明主題中的程序必須完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)及執行 （您可以在安裝 %esb 安裝 Folder%\Bin\ 此 「 UDDI 發行者 」 工具Microsoft.Practices.ESB.UDDIPublisher.exe)。</span><span class="sxs-lookup"><span data-stu-id="77db6-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) and the execution of the UDDI Publisher tool (you can install it at %ESB Install Folder%\Bin\Microsoft.Practices.ESB.UDDIPublisher.exe).</span></span>  

## <a name="steps"></a><span data-ttu-id="77db6-111">步驟</span><span class="sxs-lookup"><span data-stu-id="77db6-111">Steps</span></span>  

#### <a name="to-create-the-newposervice-in-the-uddi-registry"></a><span data-ttu-id="77db6-112">若要在 UDDI 登錄中建立 NewPOService</span><span class="sxs-lookup"><span data-stu-id="77db6-112">To create the NewPOService in the UDDI registry</span></span>  

1.  <span data-ttu-id="77db6-113">在 Internet Explorer 中，瀏覽至 UDDI 服務站台 (根據預設，此 URL 是http://localhost/uddi)。</span><span class="sxs-lookup"><span data-stu-id="77db6-113">In Internet Explorer, browse to the UDDI Service site (by default, the URL for this is http://localhost/uddi).</span></span>  

2.  <span data-ttu-id="77db6-114">在  **uddi 服務站**頁面上，按一下**發佈**。</span><span class="sxs-lookup"><span data-stu-id="77db6-114">On the **uddi Services** page, click **Publish**.</span></span>  

3.  <span data-ttu-id="77db6-115">在 [發行] 窗格中，以滑鼠右鍵按一下**Microsoft.Practices.ESB**，然後按一下**加入服務**。</span><span class="sxs-lookup"><span data-stu-id="77db6-115">In the Publish pane, right-click **Microsoft.Practices.ESB**, and then click **Add Service**.</span></span>  

4.  <span data-ttu-id="77db6-116">在下列頁面上，選取**指定要使用的金鑰**，然後按一下**繼續**。</span><span class="sxs-lookup"><span data-stu-id="77db6-116">On the following page, select **Specify a key to use**, and then click **Continue**.</span></span>  

5.  <span data-ttu-id="77db6-117">在下列頁面上，按一下**esb**主要磁碟分割。</span><span class="sxs-lookup"><span data-stu-id="77db6-117">On the following page, click the **esb** key partition.</span></span> <span data-ttu-id="77db6-118">在 **機碼後置詞**方塊中，輸入**newposervice**，然後按一下**繼續**。</span><span class="sxs-lookup"><span data-stu-id="77db6-118">In the **Key Suffix** box, type **newposervice**, and then click **Continue**.</span></span>  

6.  <span data-ttu-id="77db6-119">在下列頁面上，旁邊 (**新的服務名稱**)，按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="77db6-119">On the following page, next to (**New Service Name**), click **Edit**.</span></span> <span data-ttu-id="77db6-120">將服務命名**NewPOService**，然後按一下**更新**。</span><span class="sxs-lookup"><span data-stu-id="77db6-120">Name the service **NewPOService**, and then click **Update**.</span></span>  

7.  <span data-ttu-id="77db6-121">按一下 **新增描述**，輸入服務的描述 (例如**範例服務**)，然後按一下 **更新**。</span><span class="sxs-lookup"><span data-stu-id="77db6-121">Click **Add Description**, type a description for the service (for example, **Sample Service**), and then click **Update**.</span></span>  

#### <a name="to-add-a-binding-for-the-newposervice"></a><span data-ttu-id="77db6-122">若要加入 NewPOService 繫結</span><span class="sxs-lookup"><span data-stu-id="77db6-122">To add a binding for the NewPOService</span></span>  

1.  <span data-ttu-id="77db6-123">按一下 **繫結**索引標籤，然後再按一下**新增繫結**。</span><span class="sxs-lookup"><span data-stu-id="77db6-123">Click the **Bindings** tab, and then click **Add Binding**.</span></span>  

2.  <span data-ttu-id="77db6-124">選取 **指定要使用的金鑰**，然後按一下**繼續**。</span><span class="sxs-lookup"><span data-stu-id="77db6-124">Select **Specify a key to use**, and then click **Continue**.</span></span>  

3.  <span data-ttu-id="77db6-125">在下列頁面上，按一下**esb**主要磁碟分割。</span><span class="sxs-lookup"><span data-stu-id="77db6-125">On the following page, click the **esb** key partition.</span></span> <span data-ttu-id="77db6-126">在 **機碼後置詞**方塊中，輸入**newposervicebinding**，然後按一下**繼續**。</span><span class="sxs-lookup"><span data-stu-id="77db6-126">In the **Key Suffix** box, type **newposervicebinding**, and then click **Continue**.</span></span>  

4.  <span data-ttu-id="77db6-127">底下**存取點**，按一下**編輯**，然後完成下列：</span><span class="sxs-lookup"><span data-stu-id="77db6-127">Under **Access Point**, click **Edit**, and then complete the following:</span></span>  

    1.  <span data-ttu-id="77db6-128">在 **存取點**方塊中，輸入**http://localhost/ESB.CanadianServices/SubmitPOService.asmx**。</span><span class="sxs-lookup"><span data-stu-id="77db6-128">In the **Access Point** box, type **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.</span></span>  

    2.  <span data-ttu-id="77db6-129">在**使用型別**下拉式清單中，按一下**端點**，然後按一下**Update**。</span><span class="sxs-lookup"><span data-stu-id="77db6-129">In the **Use Type** drop-down list, click **endpoint**, and then click **Update**.</span></span>  

#### <a name="to-configure-the-binding-instance-information"></a><span data-ttu-id="77db6-130">若要設定的繫結執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="77db6-130">To configure the binding instance information</span></span>  

1. <span data-ttu-id="77db6-131">按一下 **例項資訊**索引標籤，然後再按一下**新增例項資訊**。</span><span class="sxs-lookup"><span data-stu-id="77db6-131">Click the **Instance Info** tab, and then click **Add Instance Info**.</span></span>  

2. <span data-ttu-id="77db6-132">在 **搜尋 tModel 名稱中包含**方塊中，輸入**esb %** ，然後按一下 **搜尋**。</span><span class="sxs-lookup"><span data-stu-id="77db6-132">In the **Search for tModel names containing** box, type **%esb%** and then click **Search**.</span></span>  

3. <span data-ttu-id="77db6-133">找出並按一下**tModel** for **transporttype**。</span><span class="sxs-lookup"><span data-stu-id="77db6-133">Locate and click the **tModel** for **transporttype**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="77db6-134">若要完成此程序的其餘步驟，您可能必須變更第 1 頁和第 2 頁之間。</span><span class="sxs-lookup"><span data-stu-id="77db6-134">To complete the remaining steps in this procedure, you may be required to change between page 1 and page 2.</span></span>  

4. <span data-ttu-id="77db6-135">在 **描述**區段中，按一下**新增描述**。</span><span class="sxs-lookup"><span data-stu-id="77db6-135">In the **Descriptions** section, click **Add Description**.</span></span>  

5. <span data-ttu-id="77db6-136">在 **描述**方塊中，輸入**ESB 路線使用的傳輸類型**，然後按一下**更新**。</span><span class="sxs-lookup"><span data-stu-id="77db6-136">In the **Description** box, type **Transport Type for ESB Itinerary Use**, and then click **Update**.</span></span>  

6. <span data-ttu-id="77db6-137">按一下 **執行個體詳細資料**索引標籤，然後再按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="77db6-137">Click the **Instance Details** tab, and then click **Edit**.</span></span>  

7. <span data-ttu-id="77db6-138">在 **例項參數**方塊中，輸入**Wcf-basichttp**，然後按一下**Update**。</span><span class="sxs-lookup"><span data-stu-id="77db6-138">In the **Instance Parameters** box, type **WCF-BasicHttp**, and then click **Update**.</span></span>  

8. <span data-ttu-id="77db6-139">在 **描述**區段中，按一下**新增描述**。</span><span class="sxs-lookup"><span data-stu-id="77db6-139">In the **Descriptions** section, click **Add Description**.</span></span>  

9. <span data-ttu-id="77db6-140">在 **描述**方塊中，輸入**基本 HTTP 傳輸 WCF**，然後按一下**更新**。</span><span class="sxs-lookup"><span data-stu-id="77db6-140">In the **Description** box, type **WCF Basic HTTP Transport**, and then click **Update**.</span></span>  

10. <span data-ttu-id="77db6-141">在 [發行] 窗格中，在**NewPOService**，按一下**http://localhost/esb.canadianservices/submitposervice.asmx**。</span><span class="sxs-lookup"><span data-stu-id="77db6-141">In the Publish pane, under **NewPOService**, click **http://localhost/esb.canadianservices/submitposervice.asmx**.</span></span>  

11. <span data-ttu-id="77db6-142">在 **例項資訊**索引標籤上，按一下**新增例項資訊**。</span><span class="sxs-lookup"><span data-stu-id="77db6-142">On the **Instance Info** tab, click **Add Instance Info**.</span></span>  

12. <span data-ttu-id="77db6-143">使用稍早所述的步驟，加入下列的執行個體資訊，根據下表所示的值。</span><span class="sxs-lookup"><span data-stu-id="77db6-143">Using the steps described earlier, add the following instance information, according to the values shown in the following table.</span></span>  


    |                           <span data-ttu-id="77db6-144">tModel</span><span class="sxs-lookup"><span data-stu-id="77db6-144">tModel</span></span>                           |       <span data-ttu-id="77db6-145">描述</span><span class="sxs-lookup"><span data-stu-id="77db6-145">Description</span></span>        |                          <span data-ttu-id="77db6-146">參數</span><span class="sxs-lookup"><span data-stu-id="77db6-146">Parameter</span></span>                           |         <span data-ttu-id="77db6-147">參數描述</span><span class="sxs-lookup"><span data-stu-id="77db6-147">Parameter description</span></span>          |
    |------------------------------------------------------------|--------------------------|--------------------------------------------------------------|----------------------------------------|
    | <span data-ttu-id="77db6-148">microsoft-com:esb:runtimeresolution:messageexchangepattern</span><span class="sxs-lookup"><span data-stu-id="77db6-148">microsoft-com:esb:runtimeresolution:messageexchangepattern</span></span> | <span data-ttu-id="77db6-149">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="77db6-149">Message Exchange Pattern</span></span> |                           <span data-ttu-id="77db6-150">雙向</span><span class="sxs-lookup"><span data-stu-id="77db6-150">Two-Way</span></span>                            |           <span data-ttu-id="77db6-151">雙向作業</span><span class="sxs-lookup"><span data-stu-id="77db6-151">Two-way operation</span></span>            |
    |      <span data-ttu-id="77db6-152">microsoft-com:esb:runtimeresolution:cachetimeout</span><span class="sxs-lookup"><span data-stu-id="77db6-152">microsoft-com:esb:runtimeresolution:cachetimeout</span></span>      |      <span data-ttu-id="77db6-153">快取逾時</span><span class="sxs-lookup"><span data-stu-id="77db6-153">Cache Timeout</span></span>       |                              <span data-ttu-id="77db6-154">-1</span><span class="sxs-lookup"><span data-stu-id="77db6-154">-1</span></span>                              |           <span data-ttu-id="77db6-155">目前已停用</span><span class="sxs-lookup"><span data-stu-id="77db6-155">Currently disabled</span></span>           |
    |     <span data-ttu-id="77db6-156">microsoft-com:esb:runtimeresolution:jaxrpcresponse</span><span class="sxs-lookup"><span data-stu-id="77db6-156">microsoft-com:esb:runtimeresolution:jaxrpcresponse</span></span>     |      <span data-ttu-id="77db6-157">JaxRpcResponse</span><span class="sxs-lookup"><span data-stu-id="77db6-157">JaxRpcResponse</span></span>      |                            <span data-ttu-id="77db6-158">false</span><span class="sxs-lookup"><span data-stu-id="77db6-158">false</span></span>                             |                                        |
    |         <span data-ttu-id="77db6-159">microsoft-com:esb:runtimeresolution:action</span><span class="sxs-lookup"><span data-stu-id="77db6-159">microsoft-com:esb:runtimeresolution:action</span></span>         |      <span data-ttu-id="77db6-160">服務動作</span><span class="sxs-lookup"><span data-stu-id="77db6-160">Service Action</span></span>      |                         <span data-ttu-id="77db6-161">submitOrder</span><span class="sxs-lookup"><span data-stu-id="77db6-161">submitOrder</span></span>                          | <span data-ttu-id="77db6-162">指定要叫用服務方法</span><span class="sxs-lookup"><span data-stu-id="77db6-162">Specifies the service method to invoke</span></span> |
    |    <span data-ttu-id="77db6-163">microsoft-com:esb:runtimeresolution:targetnamespace</span><span class="sxs-lookup"><span data-stu-id="77db6-163">microsoft-com:esb:runtimeresolution:targetnamespace</span></span>     |    <span data-ttu-id="77db6-164">服務命名空間</span><span class="sxs-lookup"><span data-stu-id="77db6-164">Service Namespace</span></span>     | http://globalbank.esb.dynamicresolution.com/canadianservices |            <span data-ttu-id="77db6-165">目標命名空間</span><span class="sxs-lookup"><span data-stu-id="77db6-165">Target namespace</span></span>            |

#### <a name="to-configure-the-binding-categorization"></a><span data-ttu-id="77db6-166">若要設定繫結分類</span><span class="sxs-lookup"><span data-stu-id="77db6-166">To configure the binding categorization</span></span>  

1.  <span data-ttu-id="77db6-167">在 [發行] 窗格中，在**NewPOService**，按一下**http://localhost/esb.canadianservices/submitposervice.asmx**。</span><span class="sxs-lookup"><span data-stu-id="77db6-167">In the Publish pane, under **NewPOService**, click **http://localhost/esb.canadianservices/submitposervice.asmx**.</span></span>  

2.  <span data-ttu-id="77db6-168">在 **分類**索引標籤上，按一下**新增自訂類別**。</span><span class="sxs-lookup"><span data-stu-id="77db6-168">On the **Categories** tab, click **Add Custom Category**.</span></span>  

3.  <span data-ttu-id="77db6-169">在 **搜尋**方塊中，輸入**esb %** ，然後按一下 **搜尋**。</span><span class="sxs-lookup"><span data-stu-id="77db6-169">In the **Search** box, type **%esb%** and then click **Search**.</span></span>  

4.  <span data-ttu-id="77db6-170">找出並按一下**microsoft-com:esb:runtimeresolution:biztalkapplication** tModel。</span><span class="sxs-lookup"><span data-stu-id="77db6-170">Locate and click the **microsoft-com:esb:runtimeresolution:biztalkapplication** tModel.</span></span>  

5.  <span data-ttu-id="77db6-171">在  **Key-name**方塊中，輸入**BizTalk 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="77db6-171">In the **Key Name** box, type **BizTalk Application**.</span></span>  

6.  <span data-ttu-id="77db6-172">在 **資料索引鍵值**方塊中，輸入**Microsoft.Practices.ESB**，然後按一下 **新增類別**。</span><span class="sxs-lookup"><span data-stu-id="77db6-172">In the **Key Value** box, type **Microsoft.Practices.ESB**, and then click **Add Category**.</span></span>  

7.  <span data-ttu-id="77db6-173">使用稍早所述的步驟，加入下列的自訂類別，根據下表所示的值。</span><span class="sxs-lookup"><span data-stu-id="77db6-173">Using the steps described earlier, add the following custom categories, according to the values shown in the following table.</span></span>  

    |<span data-ttu-id="77db6-174">tModel</span><span class="sxs-lookup"><span data-stu-id="77db6-174">tModel</span></span>|<span data-ttu-id="77db6-175">機碼名稱</span><span class="sxs-lookup"><span data-stu-id="77db6-175">Key name</span></span>|<span data-ttu-id="77db6-176">機碼值</span><span class="sxs-lookup"><span data-stu-id="77db6-176">Key value</span></span>|  
    |------------|--------------|---------------|  
    |<span data-ttu-id="77db6-177">microsoft-com:esb:runtimeresolution:portname</span><span class="sxs-lookup"><span data-stu-id="77db6-177">microsoft-com:esb:runtimeresolution:portname</span></span>|<span data-ttu-id="77db6-178">連接埠名稱</span><span class="sxs-lookup"><span data-stu-id="77db6-178">Port Name</span></span>|<span data-ttu-id="77db6-179">NewPOService</span><span class="sxs-lookup"><span data-stu-id="77db6-179">NewPOService</span></span>|  
    |<span data-ttu-id="77db6-180">microsoft-com:esb:runtimeresolution:transporttype</span><span class="sxs-lookup"><span data-stu-id="77db6-180">microsoft-com:esb:runtimeresolution:transporttype</span></span>|<span data-ttu-id="77db6-181">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="77db6-181">Transport Type</span></span>|<span data-ttu-id="77db6-182">WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="77db6-182">WCF-BasicHttp</span></span>|  

#### <a name="to-locate-the-service-in-the-uddi-registry"></a><span data-ttu-id="77db6-183">若要在 UDDI 登錄中找出服務</span><span class="sxs-lookup"><span data-stu-id="77db6-183">To locate the service in the UDDI registry</span></span>  

1.  <span data-ttu-id="77db6-184">在 Internet Explorer 上**uddi 服務站**頁面上，按一下**搜尋**。</span><span class="sxs-lookup"><span data-stu-id="77db6-184">In Internet Explorer, on the **uddi Services** page, click **Search**.</span></span>  

2.  <span data-ttu-id="77db6-185">按一下 [ **Services** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="77db6-185">Click the **Services** tab.</span></span>  

3.  <span data-ttu-id="77db6-186">在 **服務名稱**方塊中，輸入 **%po**，然後按一下**搜尋**。</span><span class="sxs-lookup"><span data-stu-id="77db6-186">In the **Service Name** box, type **%PO%**, and then click **Search**.</span></span>  

4.  <span data-ttu-id="77db6-187">在 **搜尋**窗格上**結果**索引標籤上，按一下  **NewPOService**。</span><span class="sxs-lookup"><span data-stu-id="77db6-187">In the **Search** pane, on the **Results** tab, click **NewPOService**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="77db6-188">這可確認服務已成功發行至登錄。</span><span class="sxs-lookup"><span data-stu-id="77db6-188">This confirms the service was successfully published to the registry.</span></span>  

#### <a name="to-create-an-itinerary-model-to-test-the-uddi-service-publication"></a><span data-ttu-id="77db6-189">若要建立路線的模型，以測試 「 UDDI 服務發行</span><span class="sxs-lookup"><span data-stu-id="77db6-189">To create an itinerary model to test the UDDI service publication</span></span>  

1.  <span data-ttu-id="77db6-190">在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。</span><span class="sxs-lookup"><span data-stu-id="77db6-190">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  

2.  <span data-ttu-id="77db6-191">在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。</span><span class="sxs-lookup"><span data-stu-id="77db6-191">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  

3.  <span data-ttu-id="77db6-192">在 **加入新項目**對話方塊中，於**名稱**方塊中，輸入**NewBindingKeySearch**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="77db6-192">In the **Add New Item** dialog box, in the **Name** box, type **NewBindingKeySearch**, and then click **Add**.</span></span>  

#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="77db6-193">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="77db6-193">To configure the properties of the itinerary</span></span>  

1.  <span data-ttu-id="77db6-194">在 Visual Studio 中，按一下設計介面**NewBindingKeySearch.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="77db6-194">In Visual Studio, click the design surface of **NewBindingKeySearch.itinerary**.</span></span> <span data-ttu-id="77db6-195">在 [ **NewBindingKeySearch**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="77db6-195">In the **NewBindingKeySearch** Properties window, configure the following properties:</span></span>  

    1.  <span data-ttu-id="77db6-196">在 **是要求回應**下拉式清單中，按一下 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="77db6-196">In the **Is Request Response** drop-down list, click **True**.</span></span>  

    2.  <span data-ttu-id="77db6-197">在 **模型匯出工具**下拉式清單中，按一下**XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="77db6-197">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  

    3.  <span data-ttu-id="77db6-198">在  **Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="77db6-198">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  

    4.  <span data-ttu-id="77db6-199">在 [**選取 XML 檔案**] 對話方塊中，輸入**C:\HowTos\Itineraries\NewBindingKeySearch**中**檔名**方塊，然後再按一下**儲存**.</span><span class="sxs-lookup"><span data-stu-id="77db6-199">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\NewBindingKeySearch** in the **File name** box, and then click **Save**.</span></span>  

        > [!NOTE]
        >  <span data-ttu-id="77db6-200">此步驟可讓您將匯出為 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="77db6-200">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="77db6-201">而不是匯出至本機檔案位置，路線，路線資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="77db6-201">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="77db6-202">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="77db6-202">You will complete this process later in this How-to topic.</span></span>  

#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="77db6-203">若要定義的路線結構</span><span class="sxs-lookup"><span data-stu-id="77db6-203">To define the structure of the itinerary</span></span>  

1.  <span data-ttu-id="77db6-204">從 [工具箱] 拖曳**匝道**模型項目到設計介面。</span><span class="sxs-lookup"><span data-stu-id="77db6-204">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="77db6-205">在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="77db6-205">In the **OnRamp1** Properties window, configure the following properties:</span></span>  

    1.  <span data-ttu-id="77db6-206">按一下 **名稱**屬性，然後按**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="77db6-206">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  

    2.  <span data-ttu-id="77db6-207">在  **Extender**下拉式清單中，按一下**匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="77db6-207">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  

    3.  <span data-ttu-id="77db6-208">在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="77db6-208">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  

    4.  <span data-ttu-id="77db6-209">在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary.Response**。</span><span class="sxs-lookup"><span data-stu-id="77db6-209">In the **Receive Port** drop-down list, click **OnRamp.Itinerary.Response**.</span></span>  

2.  <span data-ttu-id="77db6-210">從 [工具箱] 拖曳**路線服務**模型項目到設計介面。</span><span class="sxs-lookup"><span data-stu-id="77db6-210">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="77db6-211">在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="77db6-211">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  

    1.  <span data-ttu-id="77db6-212">按一下 **名稱**屬性，然後按**TransformNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="77db6-212">Click the **Name** property, and then type **TransformNAOrder**.</span></span>  

    2.  <span data-ttu-id="77db6-213">在 **路線服務的擴充項**下拉式清單中，按一下**傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="77db6-213">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  

    3.  <span data-ttu-id="77db6-214">在 **容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="77db6-214">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  

    4.  <span data-ttu-id="77db6-215">在 **服務名稱**下拉式清單中，按一下**Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="77db6-215">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  

3.  <span data-ttu-id="77db6-216">以滑鼠右鍵按一下**解析**的集合**TransformNAOrder**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="77db6-216">Right-click the **Resolver** collection of the **TransformNAOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="77db6-217">在 [ **Resolver1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="77db6-217">In the **Resolver1** Properties window, configure the following properties:</span></span>  

    1.  <span data-ttu-id="77db6-218">按一下 **名稱**屬性，然後按**NAOrder_to_CNOrder**。</span><span class="sxs-lookup"><span data-stu-id="77db6-218">Click the **Name** property, and then type **NAOrder_to_CNOrder**.</span></span>  

    2.  <span data-ttu-id="77db6-219">在 **解析程式實作**下拉式清單中，按一下**靜態的解析程式擴充**。</span><span class="sxs-lookup"><span data-stu-id="77db6-219">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  

    3.  <span data-ttu-id="77db6-220">在 **轉換的型別**下拉式清單中，按一下**GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。</span><span class="sxs-lookup"><span data-stu-id="77db6-220">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  

4.  <span data-ttu-id="77db6-221">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="77db6-221">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="77db6-222">拖曳連接，以從**ReceiveNAOrder**模型項目**TransformNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="77db6-222">Drag a connection from the **ReceiveNAOrder** model element to the **TransformNAOrder** model element.</span></span>  

5.  <span data-ttu-id="77db6-223">從 [工具箱] 拖曳**路線服務**模型項目到設計介面。</span><span class="sxs-lookup"><span data-stu-id="77db6-223">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="77db6-224">在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="77db6-224">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  

    1.  <span data-ttu-id="77db6-225">按一下 **名稱**屬性，然後按**BindingKeyRoute**。</span><span class="sxs-lookup"><span data-stu-id="77db6-225">Click the **Name** property, and then type **BindingKeyRoute**.</span></span>  

    2.  <span data-ttu-id="77db6-226">在 **路線服務的擴充項**下拉式清單中，按一下**傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="77db6-226">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  

    3.  <span data-ttu-id="77db6-227">在 **容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="77db6-227">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  

    4.  <span data-ttu-id="77db6-228">在 **服務名稱**下拉式清單中，按一下**Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="77db6-228">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  

6.  <span data-ttu-id="77db6-229">以滑鼠右鍵按一下**解析**的集合**BindingKeyRoute**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="77db6-229">Right-click the **Resolver** collection of the **BindingKeyRoute** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="77db6-230">在 [ **Resolver1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="77db6-230">In the **Resolver1** Properties window, configure the following properties:</span></span>  

    1.  <span data-ttu-id="77db6-231">按一下 **名稱**屬性，然後按**BindingKeySearch**。</span><span class="sxs-lookup"><span data-stu-id="77db6-231">Click the **Name** property, and then type **BindingKeySearch**.</span></span>  

    2.  <span data-ttu-id="77db6-232">在 **解析程式實作**下拉式清單中，按一下**Uddi3 解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="77db6-232">In the **Resolver Implementation** drop-down list, click **Uddi3 Resolver Extension**.</span></span>  

    3.  <span data-ttu-id="77db6-233">在 **解析 Moniker**下拉式清單中，按一下**UDDI3**。</span><span class="sxs-lookup"><span data-stu-id="77db6-233">In the **Resolver Moniker** drop-down list, click **UDDI3**.</span></span>  

    4.  <span data-ttu-id="77db6-234">按一下 **繫結索引鍵**屬性，然後按**uddi:esb:newposervicebinding**。</span><span class="sxs-lookup"><span data-stu-id="77db6-234">Click the **Binding key** property, and then type **uddi:esb:newposervicebinding**.</span></span> <span data-ttu-id="77db6-235">若要尋找的索引鍵值，請按一下http://localhost/ESB.CanadianServices/SubmitPOService.asmxUDDI 中的服務，然後按一下 更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="77db6-235">To find the key value, click the http://localhost/ESB.CanadianServices/SubmitPOService.asmx service in UDDI, and then click More Details.</span></span>  

7.  <span data-ttu-id="77db6-236">以滑鼠右鍵按一下**BindingKeySearch**解析程式，然後再按一下**測試解析程式組態**。</span><span class="sxs-lookup"><span data-stu-id="77db6-236">Right-click the **BindingKeySearch** resolver, and then click **Test Resolver Configuration**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="77db6-237">確認 [輸出] 視窗中顯示的輸出。</span><span class="sxs-lookup"><span data-stu-id="77db6-237">Verify the output displayed in the Output window.</span></span>  

8.  <span data-ttu-id="77db6-238">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="77db6-238">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="77db6-239">拖曳連接，以從**TransformNAOrder**模型項目**BindingKeyRoute**模型項目。</span><span class="sxs-lookup"><span data-stu-id="77db6-239">Drag a connection from the **TransformNAOrder** model element to the **BindingKeyRoute** model element.</span></span>  

9. <span data-ttu-id="77db6-240">從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**BindingKeyRoute**模型項目。</span><span class="sxs-lookup"><span data-stu-id="77db6-240">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **BindingKeyRoute** model element.</span></span> <span data-ttu-id="77db6-241">在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="77db6-241">In the **OffRamp1** Properties window, configure the following properties:</span></span>  

    1.  <span data-ttu-id="77db6-242">按一下 **名稱**屬性，然後按**SendCNOrder**。</span><span class="sxs-lookup"><span data-stu-id="77db6-242">Click the **Name** property, and then type **SendCNOrder**.</span></span>  

    2.  <span data-ttu-id="77db6-243">在  **Extender**下拉式清單中，按一下**出口匝 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="77db6-243">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  

    3.  <span data-ttu-id="77db6-244">在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="77db6-244">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  

    4.  <span data-ttu-id="77db6-245">在 **傳送埠**下拉式清單中，按一下**DynamicResolutionSolicitResp**。</span><span class="sxs-lookup"><span data-stu-id="77db6-245">In the **Send Port** drop-down list, click **DynamicResolutionSolicitResp**.</span></span>  

10. <span data-ttu-id="77db6-246">從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**BindingKeyRoute**模型項目和**SendCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="77db6-246">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **BindingKeyRoute** model element and the **SendCNOrder** model element.</span></span> <span data-ttu-id="77db6-247">在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="77db6-247">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  

    1.  <span data-ttu-id="77db6-248">按一下 **名稱**屬性，然後按**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="77db6-248">Click the **Name** property, and then type **SendPortFilter**.</span></span>  

    2.  <span data-ttu-id="77db6-249">在 **路線服務的擴充項**下拉式清單中，按一下**出口匝 Extender**。</span><span class="sxs-lookup"><span data-stu-id="77db6-249">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  

    3.  <span data-ttu-id="77db6-250">在 **出口匝**下拉式清單中，展開**SendCNOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="77db6-250">In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.</span></span>  

11. <span data-ttu-id="77db6-251">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="77db6-251">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="77db6-252">拖曳連接，以從**BindingKeyRoute**模型項目**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="77db6-252">Drag a connection from the **BindingKeyRoute** model element to the **SendPortFilter** model element.</span></span>  

12. <span data-ttu-id="77db6-253">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="77db6-253">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="77db6-254">拖曳連接，以從**SendPortFilter**模型項目**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="77db6-254">Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.</span></span>  

#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="77db6-255">若要匯出使用路線測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="77db6-255">To export the model for use with the Itinerary Test Client</span></span>  

1.  <span data-ttu-id="77db6-256">在 Visual Studio 中，以滑鼠右鍵按一下設計介面**NewBindingKeySearch**路線，，然後按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="77db6-256">In Visual Studio, right-click the design surface of the **NewBindingKeySearch** itinerary, and then click **Export Model**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="77db6-257">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="77db6-257">The XML version of the itinerary opens in Visual Studio.</span></span>  

2.  <span data-ttu-id="77db6-258">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="77db6-258">Save all project artifacts.</span></span>  

3.  <span data-ttu-id="77db6-259">在 Windows 檔案總管中，瀏覽至 C:\HowTos\Itineraries 並注意您的路線 XML (NewBindingKeySearch.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="77db6-259">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (NewBindingKeySearch.xml).</span></span>  

#### <a name="to-test-the-itinerary"></a><span data-ttu-id="77db6-260">若要測試的路線</span><span class="sxs-lookup"><span data-stu-id="77db6-260">To test the itinerary</span></span>  

1.  <span data-ttu-id="77db6-261">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="77db6-261">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  

2.  <span data-ttu-id="77db6-262">在路線測試用戶端，在**Web 服務選項**群組中，清除**使用 WCF 服務**方塊，然後選取**雙向服務**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="77db6-262">In the Itinerary Test Client, in the **Web Service Options** group, clear the **Use WCF Service** box and then select the **Two-Way Service** check box.</span></span>  

3.  <span data-ttu-id="77db6-263">按一下 [**負載路線**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="77db6-263">Click the **Load Itinerary** button.</span></span>  

4.  <span data-ttu-id="77db6-264">在 [**開啟路線檔案**] 對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="77db6-264">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="77db6-265">選取  **NewBindingKeySearch.xml**，然後按一下**開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="77db6-265">Select **NewBindingKeySearch.xml**, and then click **Open** to load the itinerary.</span></span>  

5.  <span data-ttu-id="77db6-266">按一下  **確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="77db6-266">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  

6.  <span data-ttu-id="77db6-267">在路線測試用戶端中，按一下 [旁的省略符號按鈕 （...）**載入訊息**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="77db6-267">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  

7.  <span data-ttu-id="77db6-268">在 [**選取要載入的 XML 文件**] 對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="77db6-268">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="77db6-269">選取  **NAOrderDoc.xml**，然後按一下**開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="77db6-269">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  

8.  <span data-ttu-id="77db6-270">按一下 [**送出要求**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="77db6-270">Click the **Submit Request** button.</span></span> <span data-ttu-id="77db6-271">測試完成時，按一下**確定**關閉顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="77db6-271">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  

9. <span data-ttu-id="77db6-272">確認正確的回應訊息會出現在**結果**的文字方塊**Itineray 測試用戶端**。</span><span class="sxs-lookup"><span data-stu-id="77db6-272">Verify that the correct response message appears in the **Result** text box of the **Itineray Test Client**.</span></span>  

## <a name="additional-resources"></a><span data-ttu-id="77db6-273">其他資源</span><span class="sxs-lookup"><span data-stu-id="77db6-273">Additional Resources</span></span>  
 <span data-ttu-id="77db6-274">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="77db6-274">For more information, see the following related topics:</span></span>  

-   [<span data-ttu-id="77db6-275">如何：使用 UDDI 繫結索引鍵搜尋解決服務端點</span><span class="sxs-lookup"><span data-stu-id="77db6-275">How to: Resolve a Service Endpoint Using a UDDI Binding Key Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  

-   [<span data-ttu-id="77db6-276">如何：使用 UDDI 類別搜尋解決服務端點</span><span class="sxs-lookup"><span data-stu-id="77db6-276">How to: Resolve a Service Endpoint Using a UDDI Category Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  

-   [<span data-ttu-id="77db6-277">開發活動</span><span class="sxs-lookup"><span data-stu-id="77db6-277">Development Activities</span></span>](../esb-toolkit/development-activities.md)