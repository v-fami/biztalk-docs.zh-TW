---
title: "如何： 將服務發行至 UDDI 3.0 登錄 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c3bd0ed-e5f1-43eb-98d1-e3247a565ba2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca41923dc4c392959af9f19cf3b7c32f6bfe7c20
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-publish-a-service-to-the-uddi-30-registry"></a><span data-ttu-id="57797-102">如何： 將服務發行至 UDDI 3.0 登錄</span><span class="sxs-lookup"><span data-stu-id="57797-102">How to: Publish a Service to the UDDI 3.0 Registry</span></span>
## <a name="goal"></a><span data-ttu-id="57797-103">目標</span><span class="sxs-lookup"><span data-stu-id="57797-103">Goal</span></span>  
 <span data-ttu-id="57797-104">本節示範如何使用 「 UDDI 服務網站發佈 Web 服務端點可以從中解析內路線為了 ESB 訊息路由傳送的。</span><span class="sxs-lookup"><span data-stu-id="57797-104">This section demonstrates how to use the UDDI Service site to publish a Web service endpoint that can be resolved from within an itinerary for the purpose of routing an ESB message.</span></span> <span data-ttu-id="57797-105">您將複製現有的 PurchaseOrderSubmitOrderService 服務目前發行至登錄。</span><span class="sxs-lookup"><span data-stu-id="57797-105">You will duplicate the existing PurchaseOrderSubmitOrderService service presently published to the registry.</span></span>  
  
 <span data-ttu-id="57797-106">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="57797-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="57797-107">將服務發行至通用描述、 探索與整合 (UDDI) 3 登錄使用此 「 UDDI 發行者 」 工具。</span><span class="sxs-lookup"><span data-stu-id="57797-107">Publish a service to the Universal Description, Discovery, and Integration (UDDI) 3 registry using the UDDI Publisher tool.</span></span>  
  
-   <span data-ttu-id="57797-108">服務發行集使用路線路由略過的測試解析使用 UDDI3 解析程式的服務端點。</span><span class="sxs-lookup"><span data-stu-id="57797-108">Test the service publication using an itinerary routing slip that resolves the service endpoint using a UDDI3 resolver.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="57797-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="57797-109">Prerequisites</span></span>  
 <span data-ttu-id="57797-110">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)及執行 「 UDDI 發行者 」 工具 （您可以將它安裝在 %esb 安裝 Folder%\Bin\Microsoft.Practices.ESB.UDDIPublisher.exe)。</span><span class="sxs-lookup"><span data-stu-id="57797-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) and the execution of the UDDI Publisher tool (you can install it at %ESB Install Folder%\Bin\Microsoft.Practices.ESB.UDDIPublisher.exe).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="57797-111">步驟</span><span class="sxs-lookup"><span data-stu-id="57797-111">Steps</span></span>  
  
#### <a name="to-create-the-newposervice-in-the-uddi-registry"></a><span data-ttu-id="57797-112">若要建立 NewPOService UDDI 登錄中</span><span class="sxs-lookup"><span data-stu-id="57797-112">To create the NewPOService in the UDDI registry</span></span>  
  
1.  <span data-ttu-id="57797-113">在 Internet Explorer 中，瀏覽至 UDDI 服務網站 （根據預設，這個 URL 是 http://localhost/uddi）。</span><span class="sxs-lookup"><span data-stu-id="57797-113">In Internet Explorer, browse to the UDDI Service site (by default, the URL for this is http://localhost/uddi).</span></span>  
  
2.  <span data-ttu-id="57797-114">在**uddi 服務**頁面上，按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="57797-114">On the **uddi Services** page, click **Publish**.</span></span>  
  
3.  <span data-ttu-id="57797-115">在 發行 窗格中，以滑鼠右鍵按一下**Microsoft.Practices.ESB**，然後按一下 **加入服務**。</span><span class="sxs-lookup"><span data-stu-id="57797-115">In the Publish pane, right-click **Microsoft.Practices.ESB**, and then click **Add Service**.</span></span>  
  
4.  <span data-ttu-id="57797-116">在下列頁面上，選取**指定要使用的金鑰**，然後按一下 **繼續**。</span><span class="sxs-lookup"><span data-stu-id="57797-116">On the following page, select **Specify a key to use**, and then click **Continue**.</span></span>  
  
5.  <span data-ttu-id="57797-117">在下列頁面上，按一下  **esb**資料分割索引鍵。</span><span class="sxs-lookup"><span data-stu-id="57797-117">On the following page, click the **esb** key partition.</span></span> <span data-ttu-id="57797-118">在**機碼後置詞**方塊中，輸入**newposervice**，然後按一下 **繼續**。</span><span class="sxs-lookup"><span data-stu-id="57797-118">In the **Key Suffix** box, type **newposervice**, and then click **Continue**.</span></span>  
  
6.  <span data-ttu-id="57797-119">在下列頁面上，旁邊 (**新的服務名稱**)，按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="57797-119">On the following page, next to (**New Service Name**), click **Edit**.</span></span> <span data-ttu-id="57797-120">為服務名稱**NewPOService**，然後按一下 **更新**。</span><span class="sxs-lookup"><span data-stu-id="57797-120">Name the service **NewPOService**, and then click **Update**.</span></span>  
  
7.  <span data-ttu-id="57797-121">按一下**新增描述**，輸入服務的描述 (例如，**範例服務**)，然後按一下 **更新**。</span><span class="sxs-lookup"><span data-stu-id="57797-121">Click **Add Description**, type a description for the service (for example, **Sample Service**), and then click **Update**.</span></span>  
  
#### <a name="to-add-a-binding-for-the-newposervice"></a><span data-ttu-id="57797-122">若要新增繫結的 NewPOService</span><span class="sxs-lookup"><span data-stu-id="57797-122">To add a binding for the NewPOService</span></span>  
  
1.  <span data-ttu-id="57797-123">按一下**繫結**索引標籤，然後再按一下**新增繫結**。</span><span class="sxs-lookup"><span data-stu-id="57797-123">Click the **Bindings** tab, and then click **Add Binding**.</span></span>  
  
2.  <span data-ttu-id="57797-124">選取**指定要使用的金鑰**，然後按一下 **繼續**。</span><span class="sxs-lookup"><span data-stu-id="57797-124">Select **Specify a key to use**, and then click **Continue**.</span></span>  
  
3.  <span data-ttu-id="57797-125">在下列頁面上，按一下  **esb**資料分割索引鍵。</span><span class="sxs-lookup"><span data-stu-id="57797-125">On the following page, click the **esb** key partition.</span></span> <span data-ttu-id="57797-126">在**機碼後置詞**方塊中，輸入**newposervicebinding**，然後按一下 **繼續**。</span><span class="sxs-lookup"><span data-stu-id="57797-126">In the **Key Suffix** box, type **newposervicebinding**, and then click **Continue**.</span></span>  
  
4.  <span data-ttu-id="57797-127">在下**存取點**，按一下 **編輯**，然後完成下列：</span><span class="sxs-lookup"><span data-stu-id="57797-127">Under **Access Point**, click **Edit**, and then complete the following:</span></span>  
  
    1.  <span data-ttu-id="57797-128">在**存取點**方塊中，輸入**http://localhost/ESB.CanadianServices/SubmitPOService.asmx**。</span><span class="sxs-lookup"><span data-stu-id="57797-128">In the **Access Point** box, type **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.</span></span>  
  
    2.  <span data-ttu-id="57797-129">在**使用型別**下拉式清單中，按一下 **端點**，然後按一下 **更新**。</span><span class="sxs-lookup"><span data-stu-id="57797-129">In the **Use Type** drop-down list, click **endpoint**, and then click **Update**.</span></span>  
  
#### <a name="to-configure-the-binding-instance-information"></a><span data-ttu-id="57797-130">若要設定的繫結執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="57797-130">To configure the binding instance information</span></span>  
  
1.  <span data-ttu-id="57797-131">按一下**例項資訊**索引標籤，然後再按一下**新增例項資訊**。</span><span class="sxs-lookup"><span data-stu-id="57797-131">Click the **Instance Info** tab, and then click **Add Instance Info**.</span></span>  
  
2.  <span data-ttu-id="57797-132">在**搜尋 tModel 名稱中包含**方塊中，輸入**%esb** ，然後按一下 **搜尋**。</span><span class="sxs-lookup"><span data-stu-id="57797-132">In the **Search for tModel names containing** box, type **%esb%** and then click **Search**.</span></span>  
  
3.  <span data-ttu-id="57797-133">找出並按一下**tModel**如**transporttype**。</span><span class="sxs-lookup"><span data-stu-id="57797-133">Locate and click the **tModel** for **transporttype**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57797-134">若要完成此程序中的其餘步驟，您可能必須變更第 1 頁和第 2 頁之間。</span><span class="sxs-lookup"><span data-stu-id="57797-134">To complete the remaining steps in this procedure, you may be required to change between page 1 and page 2.</span></span>  
  
4.  <span data-ttu-id="57797-135">在**描述**區段中，按一下**新增描述**。</span><span class="sxs-lookup"><span data-stu-id="57797-135">In the **Descriptions** section, click **Add Description**.</span></span>  
  
5.  <span data-ttu-id="57797-136">在**描述**方塊中，輸入**ESB 行程使用的傳輸類型**，然後按一下 **更新**。</span><span class="sxs-lookup"><span data-stu-id="57797-136">In the **Description** box, type **Transport Type for ESB Itinerary Use**, and then click **Update**.</span></span>  
  
6.  <span data-ttu-id="57797-137">按一下**執行個體詳細資料**索引標籤，然後再按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="57797-137">Click the **Instance Details** tab, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="57797-138">在**例項參數**方塊中，輸入**Wcf-basichttp**，然後按一下 **更新**。</span><span class="sxs-lookup"><span data-stu-id="57797-138">In the **Instance Parameters** box, type **WCF-BasicHttp**, and then click **Update**.</span></span>  
  
8.  <span data-ttu-id="57797-139">在**描述**區段中，按一下**新增描述**。</span><span class="sxs-lookup"><span data-stu-id="57797-139">In the **Descriptions** section, click **Add Description**.</span></span>  
  
9. <span data-ttu-id="57797-140">在**描述**方塊中，輸入**WCF 基本 HTTP 傳輸**，然後按一下 **更新**。</span><span class="sxs-lookup"><span data-stu-id="57797-140">In the **Description** box, type **WCF Basic HTTP Transport**, and then click **Update**.</span></span>  
  
10. <span data-ttu-id="57797-141">在 發行 窗格中，在**NewPOService**，按一下  **http://localhost/esb.canadianservices/submitposervice.asmx**。</span><span class="sxs-lookup"><span data-stu-id="57797-141">In the Publish pane, under **NewPOService**, click **http://localhost/esb.canadianservices/submitposervice.asmx**.</span></span>  
  
11. <span data-ttu-id="57797-142">在**例項資訊**索引標籤上，按一下 **新增例項資訊**。</span><span class="sxs-lookup"><span data-stu-id="57797-142">On the **Instance Info** tab, click **Add Instance Info**.</span></span>  
  
12. <span data-ttu-id="57797-143">使用稍早所述的步驟，加入下列的執行個體資訊，請根據下表中所顯示的值。</span><span class="sxs-lookup"><span data-stu-id="57797-143">Using the steps described earlier, add the following instance information, according to the values shown in the following table.</span></span>  
  
    |<span data-ttu-id="57797-144">tModel</span><span class="sxs-lookup"><span data-stu-id="57797-144">tModel</span></span>|<span data-ttu-id="57797-145">Description</span><span class="sxs-lookup"><span data-stu-id="57797-145">Description</span></span>|<span data-ttu-id="57797-146">參數</span><span class="sxs-lookup"><span data-stu-id="57797-146">Parameter</span></span>|<span data-ttu-id="57797-147">參數描述</span><span class="sxs-lookup"><span data-stu-id="57797-147">Parameter description</span></span>|  
    |------------|-----------------|---------------|---------------------------|  
    |<span data-ttu-id="57797-148">microsoft-com:esb:runtimeresolution:messageexchangepattern</span><span class="sxs-lookup"><span data-stu-id="57797-148">microsoft-com:esb:runtimeresolution:messageexchangepattern</span></span>|<span data-ttu-id="57797-149">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="57797-149">Message Exchange Pattern</span></span>|<span data-ttu-id="57797-150">雙向</span><span class="sxs-lookup"><span data-stu-id="57797-150">Two-Way</span></span>|<span data-ttu-id="57797-151">雙向作業</span><span class="sxs-lookup"><span data-stu-id="57797-151">Two-way operation</span></span>|  
    |<span data-ttu-id="57797-152">microsoft-com:esb:runtimeresolution:cachetimeout</span><span class="sxs-lookup"><span data-stu-id="57797-152">microsoft-com:esb:runtimeresolution:cachetimeout</span></span>|<span data-ttu-id="57797-153">快取逾時</span><span class="sxs-lookup"><span data-stu-id="57797-153">Cache Timeout</span></span>|<span data-ttu-id="57797-154">-1</span><span class="sxs-lookup"><span data-stu-id="57797-154">-1</span></span>|<span data-ttu-id="57797-155">目前已停用</span><span class="sxs-lookup"><span data-stu-id="57797-155">Currently disabled</span></span>|  
    |<span data-ttu-id="57797-156">microsoft-com:esb:runtimeresolution:jaxrpcresponse</span><span class="sxs-lookup"><span data-stu-id="57797-156">microsoft-com:esb:runtimeresolution:jaxrpcresponse</span></span>|<span data-ttu-id="57797-157">JaxRpcResponse</span><span class="sxs-lookup"><span data-stu-id="57797-157">JaxRpcResponse</span></span>|<span data-ttu-id="57797-158">false</span><span class="sxs-lookup"><span data-stu-id="57797-158">false</span></span>||  
    |<span data-ttu-id="57797-159">microsoft-com:esb:runtimeresolution:action</span><span class="sxs-lookup"><span data-stu-id="57797-159">microsoft-com:esb:runtimeresolution:action</span></span>|<span data-ttu-id="57797-160">服務動作</span><span class="sxs-lookup"><span data-stu-id="57797-160">Service Action</span></span>|<span data-ttu-id="57797-161">submitOrder</span><span class="sxs-lookup"><span data-stu-id="57797-161">submitOrder</span></span>|<span data-ttu-id="57797-162">指定要叫用的服務方法</span><span class="sxs-lookup"><span data-stu-id="57797-162">Specifies the service method to invoke</span></span>|  
    |<span data-ttu-id="57797-163">microsoft-com:esb:runtimeresolution:targetnamespace</span><span class="sxs-lookup"><span data-stu-id="57797-163">microsoft-com:esb:runtimeresolution:targetnamespace</span></span>|<span data-ttu-id="57797-164">服務命名空間</span><span class="sxs-lookup"><span data-stu-id="57797-164">Service Namespace</span></span>|<span data-ttu-id="57797-165">http://globalbank.esb.dynamicresolution.com/canadianservices</span><span class="sxs-lookup"><span data-stu-id="57797-165">http://globalbank.esb.dynamicresolution.com/canadianservices</span></span>|<span data-ttu-id="57797-166">目標命名空間</span><span class="sxs-lookup"><span data-stu-id="57797-166">Target namespace</span></span>|  
  
#### <a name="to-configure-the-binding-categorization"></a><span data-ttu-id="57797-167">若要設定繫結分類</span><span class="sxs-lookup"><span data-stu-id="57797-167">To configure the binding categorization</span></span>  
  
1.  <span data-ttu-id="57797-168">在 發行 窗格中，在**NewPOService**，按一下  **http://localhost/esb.canadianservices/submitposervice.asmx**。</span><span class="sxs-lookup"><span data-stu-id="57797-168">In the Publish pane, under **NewPOService**, click **http://localhost/esb.canadianservices/submitposervice.asmx**.</span></span>  
  
2.  <span data-ttu-id="57797-169">在**類別**索引標籤上，按一下 **新增自訂類別**。</span><span class="sxs-lookup"><span data-stu-id="57797-169">On the **Categories** tab, click **Add Custom Category**.</span></span>  
  
3.  <span data-ttu-id="57797-170">在**搜尋**方塊中，輸入**%esb** ，然後按一下 **搜尋**。</span><span class="sxs-lookup"><span data-stu-id="57797-170">In the **Search** box, type **%esb%** and then click **Search**.</span></span>  
  
4.  <span data-ttu-id="57797-171">找出並按一下**microsoft-com:esb:runtimeresolution:biztalkapplication** tModel。</span><span class="sxs-lookup"><span data-stu-id="57797-171">Locate and click the **microsoft-com:esb:runtimeresolution:biztalkapplication** tModel.</span></span>  
  
5.  <span data-ttu-id="57797-172">在**機碼名稱**方塊中，輸入**BizTalk 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="57797-172">In the **Key Name** box, type **BizTalk Application**.</span></span>  
  
6.  <span data-ttu-id="57797-173">在**鍵值**方塊中，輸入**Microsoft.Practices.ESB**，然後按一下 **新增類別**。</span><span class="sxs-lookup"><span data-stu-id="57797-173">In the **Key Value** box, type **Microsoft.Practices.ESB**, and then click **Add Category**.</span></span>  
  
7.  <span data-ttu-id="57797-174">使用稍早所述的步驟，加入下列自訂分類，根據下表中所顯示的值。</span><span class="sxs-lookup"><span data-stu-id="57797-174">Using the steps described earlier, add the following custom categories, according to the values shown in the following table.</span></span>  
  
    |<span data-ttu-id="57797-175">tModel</span><span class="sxs-lookup"><span data-stu-id="57797-175">tModel</span></span>|<span data-ttu-id="57797-176">機碼名稱</span><span class="sxs-lookup"><span data-stu-id="57797-176">Key name</span></span>|<span data-ttu-id="57797-177">機碼值</span><span class="sxs-lookup"><span data-stu-id="57797-177">Key value</span></span>|  
    |------------|--------------|---------------|  
    |<span data-ttu-id="57797-178">microsoft-com:esb:runtimeresolution:portname</span><span class="sxs-lookup"><span data-stu-id="57797-178">microsoft-com:esb:runtimeresolution:portname</span></span>|<span data-ttu-id="57797-179">連接埠名稱</span><span class="sxs-lookup"><span data-stu-id="57797-179">Port Name</span></span>|<span data-ttu-id="57797-180">NewPOService</span><span class="sxs-lookup"><span data-stu-id="57797-180">NewPOService</span></span>|  
    |<span data-ttu-id="57797-181">microsoft-com:esb:runtimeresolution:transporttype</span><span class="sxs-lookup"><span data-stu-id="57797-181">microsoft-com:esb:runtimeresolution:transporttype</span></span>|<span data-ttu-id="57797-182">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="57797-182">Transport Type</span></span>|<span data-ttu-id="57797-183">WCF-BasicHttp</span><span class="sxs-lookup"><span data-stu-id="57797-183">WCF-BasicHttp</span></span>|  
  
#### <a name="to-locate-the-service-in-the-uddi-registry"></a><span data-ttu-id="57797-184">UDDI 登錄中尋找服務</span><span class="sxs-lookup"><span data-stu-id="57797-184">To locate the service in the UDDI registry</span></span>  
  
1.  <span data-ttu-id="57797-185">在 Internet Explorer 上**uddi 服務**頁面上，按一下**搜尋**。</span><span class="sxs-lookup"><span data-stu-id="57797-185">In Internet Explorer, on the **uddi Services** page, click **Search**.</span></span>  
  
2.  <span data-ttu-id="57797-186">按一下**服務** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="57797-186">Click the **Services** tab.</span></span>  
  
3.  <span data-ttu-id="57797-187">在**服務名稱**方塊中，輸入**%PO%**，然後按一下 **搜尋**。</span><span class="sxs-lookup"><span data-stu-id="57797-187">In the **Service Name** box, type **%PO%**, and then click **Search**.</span></span>  
  
4.  <span data-ttu-id="57797-188">在**搜尋**窗格，請在**結果**索引標籤上，按一下  **NewPOService**。</span><span class="sxs-lookup"><span data-stu-id="57797-188">In the **Search** pane, on the **Results** tab, click **NewPOService**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57797-189">這可確認服務已順利發行至登錄。</span><span class="sxs-lookup"><span data-stu-id="57797-189">This confirms the service was successfully published to the registry.</span></span>  
  
#### <a name="to-create-an-itinerary-model-to-test-the-uddi-service-publication"></a><span data-ttu-id="57797-190">若要建立路線的模型來測試 UDDI 服務發行</span><span class="sxs-lookup"><span data-stu-id="57797-190">To create an itinerary model to test the UDDI service publication</span></span>  
  
1.  <span data-ttu-id="57797-191">在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="57797-191">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="57797-192">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="57797-192">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="57797-193">在**加入新項目**對話方塊中，於**名稱**方塊中，輸入**NewBindingKeySearch**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="57797-193">In the **Add New Item** dialog box, in the **Name** box, type **NewBindingKeySearch**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="57797-194">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="57797-194">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="57797-195">在 Visual Studio 中，按一下設計介面的**NewBindingKeySearch.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="57797-195">In Visual Studio, click the design surface of **NewBindingKeySearch.itinerary**.</span></span> <span data-ttu-id="57797-196">在**NewBindingKeySearch**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="57797-196">In the **NewBindingKeySearch** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="57797-197">在**為要求回應**下拉式清單中，按一下  **True**。</span><span class="sxs-lookup"><span data-stu-id="57797-197">In the **Is Request Response** drop-down list, click **True**.</span></span>  
  
    2.  <span data-ttu-id="57797-198">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="57797-198">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    3.  <span data-ttu-id="57797-199">在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="57797-199">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    4.  <span data-ttu-id="57797-200">在**選取 XML 檔案** 對話方塊中，輸入**C:\HowTos\Itineraries\NewBindingKeySearch**中**檔案名稱**方塊，然後再按一下**儲存**.</span><span class="sxs-lookup"><span data-stu-id="57797-200">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\NewBindingKeySearch** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="57797-201">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="57797-201">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="57797-202">藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="57797-202">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="57797-203">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="57797-203">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="57797-204">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="57797-204">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="57797-205">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="57797-205">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="57797-206">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="57797-206">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="57797-207">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="57797-207">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="57797-208">在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="57797-208">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="57797-209">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="57797-209">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="57797-210">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary.Response**。</span><span class="sxs-lookup"><span data-stu-id="57797-210">In the **Receive Port** drop-down list, click **OnRamp.Itinerary.Response**.</span></span>  
  
2.  <span data-ttu-id="57797-211">從 [工具箱] 拖曳**路線服務**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="57797-211">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="57797-212">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="57797-212">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="57797-213">按一下**名稱**屬性，，然後輸入**TransformNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="57797-213">Click the **Name** property, and then type **TransformNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="57797-214">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="57797-214">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
    3.  <span data-ttu-id="57797-215">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="57797-215">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="57797-216">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="57797-216">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
3.  <span data-ttu-id="57797-217">以滑鼠右鍵按一下**解析程式**集合**TransformNAOrder**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="57797-217">Right-click the **Resolver** collection of the **TransformNAOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="57797-218">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="57797-218">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="57797-219">按一下**名稱**屬性，，然後輸入**NAOrder_to_CNOrder**。</span><span class="sxs-lookup"><span data-stu-id="57797-219">Click the **Name** property, and then type **NAOrder_to_CNOrder**.</span></span>  
  
    2.  <span data-ttu-id="57797-220">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="57797-220">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="57797-221">在**轉換類型**下拉式清單中，按一下  **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。</span><span class="sxs-lookup"><span data-stu-id="57797-221">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  
  
4.  <span data-ttu-id="57797-222">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="57797-222">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="57797-223">拖曳連接**ReceiveNAOrder**模型項目的**TransformNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="57797-223">Drag a connection from the **ReceiveNAOrder** model element to the **TransformNAOrder** model element.</span></span>  
  
5.  <span data-ttu-id="57797-224">從 [工具箱] 拖曳**路線服務**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="57797-224">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="57797-225">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="57797-225">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="57797-226">按一下**名稱**屬性，，然後輸入**BindingKeyRoute**。</span><span class="sxs-lookup"><span data-stu-id="57797-226">Click the **Name** property, and then type **BindingKeyRoute**.</span></span>  
  
    2.  <span data-ttu-id="57797-227">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="57797-227">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
    3.  <span data-ttu-id="57797-228">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="57797-228">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="57797-229">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="57797-229">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
6.  <span data-ttu-id="57797-230">以滑鼠右鍵按一下**解析程式**集合**BindingKeyRoute**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="57797-230">Right-click the **Resolver** collection of the **BindingKeyRoute** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="57797-231">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="57797-231">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="57797-232">按一下**名稱**屬性，，然後輸入**BindingKeySearch**。</span><span class="sxs-lookup"><span data-stu-id="57797-232">Click the **Name** property, and then type **BindingKeySearch**.</span></span>  
  
    2.  <span data-ttu-id="57797-233">在**解析程式實作**下拉式清單中，按一下  **Uddi3 解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="57797-233">In the **Resolver Implementation** drop-down list, click **Uddi3 Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="57797-234">在**解析程式 Moniker**下拉式清單中，按一下  **UDDI3**。</span><span class="sxs-lookup"><span data-stu-id="57797-234">In the **Resolver Moniker** drop-down list, click **UDDI3**.</span></span>  
  
    4.  <span data-ttu-id="57797-235">按一下**繫結索引鍵**屬性，，然後輸入**uddi:esb:newposervicebinding**。</span><span class="sxs-lookup"><span data-stu-id="57797-235">Click the **Binding key** property, and then type **uddi:esb:newposervicebinding**.</span></span> <span data-ttu-id="57797-236">若要尋找的索引鍵值，按一下 http://localhost/ESB.CanadianServices/SubmitPOService.asmx 中的服務 「 UDDI，，然後按一下 更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="57797-236">To find the key value, click the http://localhost/ESB.CanadianServices/SubmitPOService.asmx service in UDDI, and then click More Details.</span></span>  
  
7.  <span data-ttu-id="57797-237">以滑鼠右鍵按一下**BindingKeySearch**解析程式，然後再按一下**測試解析程式組態**。</span><span class="sxs-lookup"><span data-stu-id="57797-237">Right-click the **BindingKeySearch** resolver, and then click **Test Resolver Configuration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57797-238">確認 [輸出] 視窗中顯示的輸出。</span><span class="sxs-lookup"><span data-stu-id="57797-238">Verify the output displayed in the Output window.</span></span>  
  
8.  <span data-ttu-id="57797-239">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="57797-239">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="57797-240">拖曳連接**TransformNAOrder**模型項目的**BindingKeyRoute**模型項目。</span><span class="sxs-lookup"><span data-stu-id="57797-240">Drag a connection from the **TransformNAOrder** model element to the **BindingKeyRoute** model element.</span></span>  
  
9. <span data-ttu-id="57797-241">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**BindingKeyRoute**模型項目。</span><span class="sxs-lookup"><span data-stu-id="57797-241">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **BindingKeyRoute** model element.</span></span> <span data-ttu-id="57797-242">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="57797-242">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="57797-243">按一下**名稱**屬性，，然後輸入**SendCNOrder**。</span><span class="sxs-lookup"><span data-stu-id="57797-243">Click the **Name** property, and then type **SendCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="57797-244">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="57797-244">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="57797-245">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="57797-245">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="57797-246">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionSolicitResp**。</span><span class="sxs-lookup"><span data-stu-id="57797-246">In the **Send Port** drop-down list, click **DynamicResolutionSolicitResp**.</span></span>  
  
10. <span data-ttu-id="57797-247">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**BindingKeyRoute**模型項目和**SendCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="57797-247">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **BindingKeyRoute** model element and the **SendCNOrder** model element.</span></span> <span data-ttu-id="57797-248">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="57797-248">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="57797-249">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="57797-249">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="57797-250">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="57797-250">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="57797-251">在**匝道**下拉式清單中，展開**SendCNOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="57797-251">In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.</span></span>  
  
11. <span data-ttu-id="57797-252">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="57797-252">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="57797-253">拖曳連接**BindingKeyRoute**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="57797-253">Drag a connection from the **BindingKeyRoute** model element to the **SendPortFilter** model element.</span></span>  
  
12. <span data-ttu-id="57797-254">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="57797-254">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="57797-255">拖曳連接**SendPortFilter**模型項目的**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="57797-255">Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="57797-256">若要匯出的行程測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="57797-256">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="57797-257">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**NewBindingKeySearch**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="57797-257">In Visual Studio, right-click the design surface of the **NewBindingKeySearch** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57797-258">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="57797-258">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="57797-259">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="57797-259">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="57797-260">在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (NewBindingKeySearch.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="57797-260">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (NewBindingKeySearch.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="57797-261">若要測試路線</span><span class="sxs-lookup"><span data-stu-id="57797-261">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="57797-262">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="57797-262">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="57797-263">在路線測試用戶端，在**Web 服務選項**群組中，清除**使用 WCF 服務**方塊，然後選取 **雙向服務**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="57797-263">In the Itinerary Test Client, in the **Web Service Options** group, clear the **Use WCF Service** box and then select the **Two-Way Service** check box.</span></span>  
  
3.  <span data-ttu-id="57797-264">按一下**負載路線** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="57797-264">Click the **Load Itinerary** button.</span></span>  
  
4.  <span data-ttu-id="57797-265">在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="57797-265">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="57797-266">選取**NewBindingKeySearch.xml**，然後按一下 **開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="57797-266">Select **NewBindingKeySearch.xml**, and then click **Open** to load the itinerary.</span></span>  
  
5.  <span data-ttu-id="57797-267">按一下**確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="57797-267">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
6.  <span data-ttu-id="57797-268">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="57797-268">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
7.  <span data-ttu-id="57797-269">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="57797-269">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="57797-270">選取**NAOrderDoc.xml**，然後按一下 **開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="57797-270">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
8.  <span data-ttu-id="57797-271">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="57797-271">Click the **Submit Request** button.</span></span> <span data-ttu-id="57797-272">測試完成時，按一下**確定**解除顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="57797-272">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
9. <span data-ttu-id="57797-273">請確認正確的回應訊息出現在**結果**文字方塊**Itineray 測試用戶端**。</span><span class="sxs-lookup"><span data-stu-id="57797-273">Verify that the correct response message appears in the **Result** text box of the **Itineray Test Client**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="57797-274">其他資源</span><span class="sxs-lookup"><span data-stu-id="57797-274">Additional Resources</span></span>  
 <span data-ttu-id="57797-275">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="57797-275">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="57797-276">如何： 解決使用繫結機碼搜尋 UDDI 服務端點</span><span class="sxs-lookup"><span data-stu-id="57797-276">How to: Resolve a Service Endpoint Using a UDDI Binding Key Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
-   [<span data-ttu-id="57797-277">如何： 解決使用 UDDI 類別目錄搜尋之服務端點</span><span class="sxs-lookup"><span data-stu-id="57797-277">How to: Resolve a Service Endpoint Using a UDDI Category Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
-   [<span data-ttu-id="57797-278">開發活動</span><span class="sxs-lookup"><span data-stu-id="57797-278">Development Activities</span></span>](../esb-toolkit/development-activities.md)