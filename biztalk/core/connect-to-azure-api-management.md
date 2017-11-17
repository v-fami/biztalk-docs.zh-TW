---
title: "連接到使用 BizTalk Server 的 Azure API 管理 |Microsoft 文件"
description: "使用 BizTalk 功能組件 1 來連接到 API 管理中，從 BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a87bfb40-7e6f-46aa-8ac7-db6d13ce7eb2
caps.latest.revision: "2"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: d0c5e4cd2a0ebbd7108845ea15de468d0e0a5a34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-azure-api-management"></a><span data-ttu-id="8a72d-103">連接到 Azure API 管理</span><span class="sxs-lookup"><span data-stu-id="8a72d-103">Connect to Azure API Management</span></span>
<span data-ttu-id="8a72d-104">您現在可以輕鬆地公開您的 SOAP 端點，透過從 BizTalk 應用程式開發介面管理。</span><span class="sxs-lookup"><span data-stu-id="8a72d-104">You can now easily expose your SOAP endpoint through API Management from BizTalk.</span></span>

## <a name="what-is-azure-api-management"></a><span data-ttu-id="8a72d-105">什麼是 Azure API 管理</span><span class="sxs-lookup"><span data-stu-id="8a72d-105">What is Azure API Management</span></span>
<span data-ttu-id="8a72d-106">用於 Azure API 管理周全的解決方案為 Api 發佈給外部和內部的客戶。</span><span class="sxs-lookup"><span data-stu-id="8a72d-106">Use Azure API Management as a turnkey solution for publishing APIs to external and internal customers.</span></span> <span data-ttu-id="8a72d-107">快速建立一致和裝載任何地方，現有的後端服務的現代應用程式開發介面閘道保護它們濫用與過度使用，並取得深入了解使用量和健全狀況。</span><span class="sxs-lookup"><span data-stu-id="8a72d-107">Quickly create consistent and modern API gateways for existing back-end services hosted anywhere, secure and protect them from abuse and overuse, and get insights into usage and health.</span></span> <span data-ttu-id="8a72d-108">此外，自動化並調整規模可幫助您的應用程式開發介面程式啟動並執行的開發人員入門訓練。</span><span class="sxs-lookup"><span data-stu-id="8a72d-108">Plus, automate and scale developer onboarding to help get your API program up and running.</span></span> 

<span data-ttu-id="8a72d-109">請參閱[API 管理](https://azure.microsoft.com/en-us/services/api-management/)若要深入了解 API 管理。</span><span class="sxs-lookup"><span data-stu-id="8a72d-109">See [API Management](https://azure.microsoft.com/en-us/services/api-management/) to learn more about API Management.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a72d-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="8a72d-110">Prerequisites</span></span>
* <span data-ttu-id="8a72d-111">設定並設定[Azure API 管理](https://docs.microsoft.com/en-us/azure/api-management/api-management-get-started)</span><span class="sxs-lookup"><span data-stu-id="8a72d-111">Configure and set up [Azure API Management](https://docs.microsoft.com/en-us/azure/api-management/api-management-get-started)</span></span>
* <span data-ttu-id="8a72d-112">建立[虛擬網路](https://docs.microsoft.com/en-us/azure/api-management/api-management-using-with-vnet)BizTalk 電腦與應用程式開發介面管理入口執行個體</span><span class="sxs-lookup"><span data-stu-id="8a72d-112">Create a [virtual network](https://docs.microsoft.com/en-us/azure/api-management/api-management-using-with-vnet) between your BizTalk Machine and the API Managemenet instance</span></span>


1. <span data-ttu-id="8a72d-113">在 Azure 入口網站中，開啟您的 API 管理，然後選取**Api**從功能表：</span><span class="sxs-lookup"><span data-stu-id="8a72d-113">In the Azure portal, open up your API management, and select **APIs** from the menu:</span></span>

    ![選取的 BizTalk 應用程式開發介面](../core/media/select-api-for-biztalk.png)
    
2. <span data-ttu-id="8a72d-115">選取的選項**WSDL**中新的應用程式開發介面 > 一節：</span><span class="sxs-lookup"><span data-stu-id="8a72d-115">Select the option for **WSDL** in the New API section:</span></span>

    ![選取 wsdl biztalk 應用程式開發介面](../core/media/select-wsdl-biztalk-api.png)
    
3. <span data-ttu-id="8a72d-117">若要連接至 BizTalk WSDL 的 API 管理，請將 URL 複製到您的 BizTalk 電腦到 SOAP 端點的完整 uri。</span><span class="sxs-lookup"><span data-stu-id="8a72d-117">To connect to API Management to your BizTalk WSDL, copy the URL to your BizTalk computer with the full URI to your SOAP endpoint.</span></span> <span data-ttu-id="8a72d-118">例如，複製`http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl`:</span><span class="sxs-lookup"><span data-stu-id="8a72d-118">For example, copy `http://10.0.31.22/RestEndPoint/OrderIncome.svc?wsdl`:</span></span>

    ![建立從 WSDL BizTalk 應用程式開發介面](../core/media/create-api-from-wsdl-biztalk.png)

4. <span data-ttu-id="8a72d-120">如果您想要使用，請選取**SOAP 傳遞**，或設定總**REST 的 SOAP**服務。</span><span class="sxs-lookup"><span data-stu-id="8a72d-120">Select if you want to use a **SOAP pass-through**, or set up a **SOAP to REST** service.</span></span>
5. <span data-ttu-id="8a72d-121">輸入**名稱**您 API 的**描述**，而**API Url 尾碼**為您的服務。</span><span class="sxs-lookup"><span data-stu-id="8a72d-121">Enter the **name** of your API, the **Description**, and the **API Url suffix** for your service.</span></span>
6. <span data-ttu-id="8a72d-122">選取**建立**建立您的後端 SOAP 端點的通訊。</span><span class="sxs-lookup"><span data-stu-id="8a72d-122">Select **Create** to create the communication to your backend SOAP endpoint.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a72d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a72d-123">See also</span></span>
[<span data-ttu-id="8a72d-124">設定 Feature Pack</span><span class="sxs-lookup"><span data-stu-id="8a72d-124">Configure the feature pack</span></span>](configure-the-feature-pack.md)