---
title: ESB 發送器元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85655b5f-4717-42d1-b005-0a5592d5653b
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16281ff49da6470212e9e8396a051270adf1eef7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982127"
---
# <a name="the-esb-dispatcher-component"></a><span data-ttu-id="00f3e-102">ESB 發送器元件</span><span class="sxs-lookup"><span data-stu-id="00f3e-102">The ESB Dispatcher Component</span></span>
<span data-ttu-id="00f3e-103">以傳訊為基礎的路線服務的 ESB 發送器元件內執行。</span><span class="sxs-lookup"><span data-stu-id="00f3e-103">Messaging-based itinerary services are executed inside the ESB Dispatcher component.</span></span> <span data-ttu-id="00f3e-104">發送器元件可以也會動態地設定為輸出訊息的端點位置屬性，並動態地轉換訊息。</span><span class="sxs-lookup"><span data-stu-id="00f3e-104">The Dispatcher component can also dynamically set endpoint location properties for outbound messages and dynamically transform messages.</span></span>  
  
## <a name="component-properties"></a><span data-ttu-id="00f3e-105">元件屬性</span><span class="sxs-lookup"><span data-stu-id="00f3e-105">Component Properties</span></span>  
 <span data-ttu-id="00f3e-106">發送器元件有六個屬性：</span><span class="sxs-lookup"><span data-stu-id="00f3e-106">The Dispatcher component has six properties:</span></span>  
  
- <span data-ttu-id="00f3e-107">**RoutingServiceName**。</span><span class="sxs-lookup"><span data-stu-id="00f3e-107">**RoutingServiceName**.</span></span> <span data-ttu-id="00f3e-108">此屬性會指定以傳訊為基礎的路由服務的已註冊的名稱。</span><span class="sxs-lookup"><span data-stu-id="00f3e-108">This property specifies the registered name for the messaging-based routing service.</span></span> <span data-ttu-id="00f3e-109">預設值是**Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="00f3e-109">The default value is **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
- <span data-ttu-id="00f3e-110">**TransformServiceName**。</span><span class="sxs-lookup"><span data-stu-id="00f3e-110">**TransformServiceName**.</span></span> <span data-ttu-id="00f3e-111">此屬性會指定訊息為基礎的轉換服務登錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="00f3e-111">This property specifies the registered name for the messaging-based transform service.</span></span> <span data-ttu-id="00f3e-112">預設值是**Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="00f3e-112">The default value is **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
- <span data-ttu-id="00f3e-113">**驗證**。</span><span class="sxs-lookup"><span data-stu-id="00f3e-113">**Validate**.</span></span> <span data-ttu-id="00f3e-114">此屬性會指定訊息是否需要驗證。</span><span class="sxs-lookup"><span data-stu-id="00f3e-114">This property specifies whether a message needs to be validated.</span></span>  
  
- <span data-ttu-id="00f3e-115">**啟用**。</span><span class="sxs-lookup"><span data-stu-id="00f3e-115">**Enabled**.</span></span> <span data-ttu-id="00f3e-116">這個屬性會啟用或停用元件。</span><span class="sxs-lookup"><span data-stu-id="00f3e-116">This property enables or disables the component.</span></span>  
  
- <span data-ttu-id="00f3e-117">**端點**。</span><span class="sxs-lookup"><span data-stu-id="00f3e-117">**Endpoint**.</span></span> <span data-ttu-id="00f3e-118">這個屬性是解析程式的連接字串，以註冊使用 BizTalk ESB 工具組的格式。</span><span class="sxs-lookup"><span data-stu-id="00f3e-118">This property is a resolver connection string in a format registered with BizTalk ESB Toolkit.</span></span>  
  
- <span data-ttu-id="00f3e-119">**將名稱對應**。</span><span class="sxs-lookup"><span data-stu-id="00f3e-119">**Map Name**.</span></span> <span data-ttu-id="00f3e-120">這個屬性是對應的完整的名稱或連接字串格式向[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="00f3e-120">This property is either the fully qualified name of a map or a connection string format registered with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:</span></span>  
  
  -   <span data-ttu-id="00f3e-121">對應名稱的範例如下：</span><span class="sxs-lookup"><span data-stu-id="00f3e-121">The following is an example of a map name:</span></span>  
  
      ```  
      GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN, GlobalBank.ESB.DynamicResolution.Transforms, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c2c8b2b87f54180a  
      ```