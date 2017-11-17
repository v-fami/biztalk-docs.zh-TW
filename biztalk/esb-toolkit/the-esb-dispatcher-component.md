---
title: "ESB 發送器元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85655b5f-4717-42d1-b005-0a5592d5653b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe377221034637eab23b70c50ccf48a8454a23bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-dispatcher-component"></a><span data-ttu-id="b6d05-102">ESB 發送器元件</span><span class="sxs-lookup"><span data-stu-id="b6d05-102">The ESB Dispatcher Component</span></span>
<span data-ttu-id="b6d05-103">傳訊架構路線服務會在 ESB 發送器元件內執行。</span><span class="sxs-lookup"><span data-stu-id="b6d05-103">Messaging-based itinerary services are executed inside the ESB Dispatcher component.</span></span> <span data-ttu-id="b6d05-104">發送器元件可以也會動態地設定輸出訊息的端點位置屬性，並以動態方式將訊息轉換。</span><span class="sxs-lookup"><span data-stu-id="b6d05-104">The Dispatcher component can also dynamically set endpoint location properties for outbound messages and dynamically transform messages.</span></span>  
  
## <a name="component-properties"></a><span data-ttu-id="b6d05-105">元件屬性</span><span class="sxs-lookup"><span data-stu-id="b6d05-105">Component Properties</span></span>  
 <span data-ttu-id="b6d05-106">發送器元件有六個屬性：</span><span class="sxs-lookup"><span data-stu-id="b6d05-106">The Dispatcher component has six properties:</span></span>  
  
-   <span data-ttu-id="b6d05-107">**RoutingServiceName**。</span><span class="sxs-lookup"><span data-stu-id="b6d05-107">**RoutingServiceName**.</span></span> <span data-ttu-id="b6d05-108">此屬性會指定以傳訊為基礎的路由服務為已註冊的名稱。</span><span class="sxs-lookup"><span data-stu-id="b6d05-108">This property specifies the registered name for the messaging-based routing service.</span></span> <span data-ttu-id="b6d05-109">預設值是**Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="b6d05-109">The default value is **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
-   <span data-ttu-id="b6d05-110">**TransformServiceName**。</span><span class="sxs-lookup"><span data-stu-id="b6d05-110">**TransformServiceName**.</span></span> <span data-ttu-id="b6d05-111">此屬性指定已註冊的服務的名稱以傳訊為基礎的轉換。</span><span class="sxs-lookup"><span data-stu-id="b6d05-111">This property specifies the registered name for the messaging-based transform service.</span></span> <span data-ttu-id="b6d05-112">預設值是**Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="b6d05-112">The default value is **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
-   <span data-ttu-id="b6d05-113">**驗證**。</span><span class="sxs-lookup"><span data-stu-id="b6d05-113">**Validate**.</span></span> <span data-ttu-id="b6d05-114">此屬性會指定是否需要驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="b6d05-114">This property specifies whether a message needs to be validated.</span></span>  
  
-   <span data-ttu-id="b6d05-115">**啟用**。</span><span class="sxs-lookup"><span data-stu-id="b6d05-115">**Enabled**.</span></span> <span data-ttu-id="b6d05-116">這個屬性會啟用或停用元件。</span><span class="sxs-lookup"><span data-stu-id="b6d05-116">This property enables or disables the component.</span></span>  
  
-   <span data-ttu-id="b6d05-117">**端點**。</span><span class="sxs-lookup"><span data-stu-id="b6d05-117">**Endpoint**.</span></span> <span data-ttu-id="b6d05-118">這個屬性是向 BizTalk ESB Toolkit 格式的解析程式連接字串。</span><span class="sxs-lookup"><span data-stu-id="b6d05-118">This property is a resolver connection string in a format registered with BizTalk ESB Toolkit.</span></span>  
  
-   <span data-ttu-id="b6d05-119">**對應名稱**。</span><span class="sxs-lookup"><span data-stu-id="b6d05-119">**Map Name**.</span></span> <span data-ttu-id="b6d05-120">這個屬性是完整限定的名稱的對應，或是連接字串格式向[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b6d05-120">This property is either the fully qualified name of a map or a connection string format registered with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:</span></span>  
  
    -   <span data-ttu-id="b6d05-121">對應名稱的範例如下：</span><span class="sxs-lookup"><span data-stu-id="b6d05-121">The following is an example of a map name:</span></span>  
  
        ```  
        GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN, GlobalBank.ESB.DynamicResolution.Transforms, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c2c8b2b87f54180a  
        ```