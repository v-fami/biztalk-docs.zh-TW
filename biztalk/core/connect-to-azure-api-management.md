---
title: 發行 SOAP 端點 API 管理 |Microsoft 文件
description: 使用 Feature Pack 1 和 Feature Pack 2 公開 BizTalk WCF 基本 HTTP 接收位置為 API 管理中的 SOAP 端點。 您可以使用 BizTalk 管理主控台中，執行此動作，或在 Azure 入口網站中貼上您直接在 API 管理中的端點。
ms.custom: ''
ms.date: 11/21/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a87bfb40-7e6f-46aa-8ac7-db6d13ce7eb2
caps.latest.revision: 2
author: MandiOhlinger
ms.author: valrobb
manager: anneta
ms.openlocfilehash: eb716729dcdbac07c5b17cf267866cf282046a70
ms.sourcegitcommit: 3371ffd8ceca02e2b3715d53a1e0c0a59045912e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34848950"
---
# <a name="publish-biztalk-soap-endpoints-in-api-management"></a><span data-ttu-id="d69ba-104">在 API 管理中發佈 BizTalk SOAP 端點</span><span class="sxs-lookup"><span data-stu-id="d69ba-104">Publish BizTalk SOAP endpoints in API Management</span></span>

<span data-ttu-id="d69ba-105">將 BizTalk SOAP 端點公開為 Azure API 管理中的服務。</span><span class="sxs-lookup"><span data-stu-id="d69ba-105">Expose your BizTalk SOAP endpoints as services within Azure API Management.</span></span> 

<span data-ttu-id="d69ba-106">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]功能組件 1**，您可以公開從 BizTalk 應用程式開發介面管理透過 SOAP 端點。</span><span class="sxs-lookup"><span data-stu-id="d69ba-106">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 1**, you can expose a SOAP endpoint through API Management from BizTalk.</span></span> <span data-ttu-id="d69ba-107">您可以在 Azure 入口網站中使用 API 管理。</span><span class="sxs-lookup"><span data-stu-id="d69ba-107">You can do this using  API Management in the Azure portal.</span></span> 

<span data-ttu-id="d69ba-108">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，您可以公開 Wcf-basichttp 接收位置做為使用 BizTalk 管理 的 Azure API 管理中的端點。</span><span class="sxs-lookup"><span data-stu-id="d69ba-108">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, you can expose a WCF-BasicHTTP receive location as an endpoint within Azure API Management using BizTalk Administration.</span></span> 

> [!TIP]
> <span data-ttu-id="d69ba-109">[什麼是 API 管理？](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)是了解，並深入了解這項 Azure 服務的絕佳資源。</span><span class="sxs-lookup"><span data-stu-id="d69ba-109">[What is API Management?](https://docs.microsoft.com/azure/api-management/api-management-key-concepts) is a great resource to understand and learn more about this Azure service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d69ba-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="d69ba-110">Prerequisites</span></span>
* <span data-ttu-id="d69ba-111">設定並設定[Azure API 管理](https://docs.microsoft.com/azure/api-management/api-management-get-started)</span><span class="sxs-lookup"><span data-stu-id="d69ba-111">Configure and set up [Azure API Management](https://docs.microsoft.com/azure/api-management/api-management-get-started)</span></span>
* <span data-ttu-id="d69ba-112">建立[虛擬網路](https://docs.microsoft.com/azure/api-management/api-management-using-with-vnet)BizTalk 電腦與 API 管理執行個體之間</span><span class="sxs-lookup"><span data-stu-id="d69ba-112">Create a [virtual network](https://docs.microsoft.com/azure/api-management/api-management-using-with-vnet) between your BizTalk computer and the API Management instance</span></span>
* <span data-ttu-id="d69ba-113">安裝[功能套件 2](https://aka.ms/bts2016fp2) BizTalk 伺服器上</span><span class="sxs-lookup"><span data-stu-id="d69ba-113">Install [Feature Pack 2](https://aka.ms/bts2016fp2) on the BizTalk Server</span></span>

## <a name="create-using-api-management-in-azure-portal"></a><span data-ttu-id="d69ba-114">建立在 Azure 入口網站中使用 API 管理</span><span class="sxs-lookup"><span data-stu-id="d69ba-114">Create using API Management in Azure portal</span></span> 
1. <span data-ttu-id="d69ba-115">在[Azure 入口網站](https://portal.azure.com)，開啟您的 API 管理，然後選取**Api**:</span><span class="sxs-lookup"><span data-stu-id="d69ba-115">In the [Azure portal](https://portal.azure.com), open up your API management, and select **APIs**:</span></span>

    ![選取的 BizTalk 應用程式開發介面](../core/media/select-api-for-biztalk.png)
    
2. <span data-ttu-id="d69ba-117">選取**WSDL**:</span><span class="sxs-lookup"><span data-stu-id="d69ba-117">Select **WSDL**:</span></span>

    ![選取 wsdl biztalk 應用程式開發介面](../core/media/select-wsdl-biztalk-api.png)
    
3. <span data-ttu-id="d69ba-119">設定您的 WSDL 內容：</span><span class="sxs-lookup"><span data-stu-id="d69ba-119">Configure your WSDL properties:</span></span> 

    1. <span data-ttu-id="d69ba-120">**WSDL 規格**： 輸入 BizTalk SOAP 端點的完整 URI。</span><span class="sxs-lookup"><span data-stu-id="d69ba-120">**WSDL specification** : Enter the full URI to your BizTalk SOAP endpoint.</span></span> <span data-ttu-id="d69ba-121">例如，輸入類似`http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl`或`http://biztalkfp1.westus.cloudapp.azure.com/RestEndPoint/OrderIncome.svc?wsdl`。</span><span class="sxs-lookup"><span data-stu-id="d69ba-121">For example, enter something like `http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl` or `http://biztalkfp1.westus.cloudapp.azure.com/RestEndPoint/OrderIncome.svc?wsdl`.</span></span>  

    2. <span data-ttu-id="d69ba-122">**SOAP 傳遞**或**REST 的 SOAP** ： 選取您的喜好設定：</span><span class="sxs-lookup"><span data-stu-id="d69ba-122">**SOAP pass-through** or **SOAP to REST** : Select your preference:</span></span> 
        * <span data-ttu-id="d69ba-123">**其餘的 SOAP**： 從現有的 SOAP web 服務建立 REST 架構 HTTP Api</span><span class="sxs-lookup"><span data-stu-id="d69ba-123">**SOAP to REST**: Create REST-based HTTP APIs from an existing SOAP-based web service</span></span>
        * <span data-ttu-id="d69ba-124">**SOAP 傳遞**： 做為 SOAP API 的 proxy</span><span class="sxs-lookup"><span data-stu-id="d69ba-124">**SOAP pass-through**: Acts as a proxy for the SOAP API</span></span> 

    3. <span data-ttu-id="d69ba-125">輸入慣用**顯示名稱**，**名稱**，**描述**， **API Url 尾碼**，**產品**，和**版本**。</span><span class="sxs-lookup"><span data-stu-id="d69ba-125">Enter your preferred **Display Name**, **Name**, **Description**, **API Url suffix**, **Products**, and **Version**.</span></span>

    <span data-ttu-id="d69ba-126">完成時，WSDL 組態看起來像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="d69ba-126">When finished, your WSDL configuration looks something like the following:</span></span> 

    ![建立從 WSDL BizTalk 應用程式開發介面](../core/media/create-api-from-wsdl-biztalk.png)

4. <span data-ttu-id="d69ba-128">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="d69ba-128">Select **Create**.</span></span>

## <a name="create-using-the-biztalk-administration"></a><span data-ttu-id="d69ba-129">建立使用 BizTalk 管理</span><span class="sxs-lookup"><span data-stu-id="d69ba-129">Create using the BizTalk Administration</span></span>

> [!NOTE] 
> <span data-ttu-id="d69ba-130">這項功能支援 Wcf-basichttp 接收位置。</span><span class="sxs-lookup"><span data-stu-id="d69ba-130">This feature is supported with WCF-BasicHTTP receive locations.</span></span> 

1. <span data-ttu-id="d69ba-131">在 BizTalk 管理主控台，以滑鼠右鍵按一下您 Wcf-basichttp 接收位置，然後選取**發行至 API 管理**:</span><span class="sxs-lookup"><span data-stu-id="d69ba-131">In the BizTalk Administration Console, right-click your WCF-BasicHTTP receive location, and select **Publish to API Management**:</span></span>  

    ![發行功能表選項](../core/media/publish-to-api-management-option.png)
 
2. <span data-ttu-id="d69ba-133">設定您的 API 管理內容：</span><span class="sxs-lookup"><span data-stu-id="d69ba-133">Configure your API management properties:</span></span> 

    1. <span data-ttu-id="d69ba-134">**登入**您 Azure 訂用帳戶中，選取**訂用帳戶**和**資源群組**具有您 API 管理服務，然後選取您的服務。</span><span class="sxs-lookup"><span data-stu-id="d69ba-134">**Sign-in** to your Azure subscription, select the **Subscription** and **Resource Group** that has your API management service, and then select your service.</span></span>

    2. <span data-ttu-id="d69ba-135">**WSDL 規格連結**自動填入您的 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="d69ba-135">The **WSDL specification link** is automatically populated with your WSDL file.</span></span> <span data-ttu-id="d69ba-136">取代**localhost** DNS 名稱或 IP 位址的 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="d69ba-136">Replace **localhost** with the DNS name or IP address of the BizTalk Server.</span></span> 

    3. <span data-ttu-id="d69ba-137">選取**SOAP 傳遞**或**REST 的 SOAP**:</span><span class="sxs-lookup"><span data-stu-id="d69ba-137">Select **SOAP pass-through** or **SOAP to REST**:</span></span>  
        * <span data-ttu-id="d69ba-138">**其餘的 SOAP**： 從現有的 SOAP web 服務建立 REST 架構 HTTP Api</span><span class="sxs-lookup"><span data-stu-id="d69ba-138">**SOAP to REST**: Create REST-based HTTP APIs from an existing SOAP-based web services</span></span>
        * <span data-ttu-id="d69ba-139">**SOAP 傳遞**： 做為 SOAP API 的 proxy</span><span class="sxs-lookup"><span data-stu-id="d69ba-139">**SOAP pass-through**: Acts as a proxy for the SOAP API</span></span> 

        <span data-ttu-id="d69ba-140">API 可以藉由變更發佈這兩種方式**API URL 尾碼**，，再發行一次使用不同的應用程式開發介面型別。</span><span class="sxs-lookup"><span data-stu-id="d69ba-140">The API can be published both ways by changing the **API URL suffix**, and then publishing again using a different API type.</span></span>

    4. <span data-ttu-id="d69ba-141">**API 名稱**自動填入接收位置名稱。</span><span class="sxs-lookup"><span data-stu-id="d69ba-141">The **API name** is automatically populated with the receive location name.</span></span>

    5. <span data-ttu-id="d69ba-142">選取**API URL 尾碼**以供取用者的 api。</span><span class="sxs-lookup"><span data-stu-id="d69ba-142">Select an **API URL suffix** that is to be used by consumers of the API.</span></span> 

    <span data-ttu-id="d69ba-143">完成時，您的內容看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="d69ba-143">When finished, your properties look similar to the following:</span></span>  
    ![發行至應用程式開發介面 視窗](../core/media/api-management-publish-window.png)


3. <span data-ttu-id="d69ba-145">選取**發行**。</span><span class="sxs-lookup"><span data-stu-id="d69ba-145">Select **Publish**.</span></span> <span data-ttu-id="d69ba-146">成功時，接收位置會顯示在 API 管理中的服務為[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="d69ba-146">When successful, the receive location is displayed as a service in API Management in the [Azure portal](https://portal.azure.com).</span></span> 

## <a name="do-more"></a><span data-ttu-id="d69ba-147">執行其他動作</span><span class="sxs-lookup"><span data-stu-id="d69ba-147">Do more</span></span>
<span data-ttu-id="d69ba-148">Azure API 管理是功能強大服務會使用有大量的 Azure 服務，包括邏輯應用程式。</span><span class="sxs-lookup"><span data-stu-id="d69ba-148">Azure API Management is a powerful service that is used by a lot of Azure services, including Logic Apps.</span></span> <span data-ttu-id="d69ba-149">API 管理包括許多功能，包括 速率限制和配額，可以存取您的應用程式開發介面，快取，以及更多。</span><span class="sxs-lookup"><span data-stu-id="d69ba-149">API Management includes many features, including rate limits and quotas, who has access to your APIs, caching, and more.</span></span> <span data-ttu-id="d69ba-150">請參閱[API 管理是什麼？](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)若要開始使用。</span><span class="sxs-lookup"><span data-stu-id="d69ba-150">See [What is API Management?](https://docs.microsoft.com/azure/api-management/api-management-key-concepts) to get started.</span></span>

## <a name="see-also"></a><span data-ttu-id="d69ba-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d69ba-151">See also</span></span>
[<span data-ttu-id="d69ba-152">設定 Feature Pack</span><span class="sxs-lookup"><span data-stu-id="d69ba-152">Configure the feature pack</span></span>](configure-the-feature-pack.md)
