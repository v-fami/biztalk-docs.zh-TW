---
title: "開發 BizTalk Server 在 Siebel 應用程式 |Microsoft 文件"
description: "建立使用 WCF，Siebel 應用程式或 BizTalk Server 與 BizTalk 配接器組件 (BAP) 中"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bc04906-6d64-433c-b357-797ec5883279
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c1535a3aa7861effdad998d4d997fbcdfced02c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-your-siebel-applications"></a><span data-ttu-id="d6ba7-103">開發 Siebel 應用程式</span><span class="sxs-lookup"><span data-stu-id="d6ba7-103">Develop your Siebel applications</span></span>

## <a name="overview"></a><span data-ttu-id="d6ba7-104">概觀</span><span class="sxs-lookup"><span data-stu-id="d6ba7-104">Overview</span></span>
<span data-ttu-id="d6ba7-105">[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-105">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="d6ba7-106">用戶端應用程式可以取用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]到 Siebel 成品上叫用作業。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-106">Client applications can consume the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to invoke operations on Siebel artifacts.</span></span> <span data-ttu-id="d6ba7-107">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可以取用：</span><span class="sxs-lookup"><span data-stu-id="d6ba7-107">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] can be consumed:</span></span>  
  
-   <span data-ttu-id="d6ba7-108">透過 BizTalk Server 解決方案中的實體連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-108">Through a physical port binding in a BizTalk Server solution.</span></span>  
  
-   <span data-ttu-id="d6ba7-109">藉由叫用用戶端 proxy 的執行個體上的方法。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-109">By invoking methods on an instance of a client proxy.</span></span>  
  
-   <span data-ttu-id="d6ba7-110">為託管的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-110">As a hosted WCF service.</span></span>  
  
-   <span data-ttu-id="d6ba7-111">傳送 SOAP 訊息中使用 WCF 通道模型的程式碼是通道執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-111">By sending SOAP messages over a channel instance in code that uses the WCF channel model.</span></span>  
  
-   <span data-ttu-id="d6ba7-112">透過 ADO.NET 介面。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-112">Through an ADO.NET interface.</span></span>  
  
## <a name="biztalk-vs-wcf-service-vs-wcf-channel-vs-adonet"></a><span data-ttu-id="d6ba7-113">BizTalk 與 WCF 服務與 WCF 通道 vs ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d6ba7-113">BizTalk vs WCF service vs WCF channel vs ADO.NET</span></span>
 <span data-ttu-id="d6ba7-114">下表：</span><span class="sxs-lookup"><span data-stu-id="d6ba7-114">The following table:</span></span>  
  
-   <span data-ttu-id="d6ba7-115">列出可對使用 Siebel 系統的不同作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-115">Lists the different operations that can be performed on a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
-   <span data-ttu-id="d6ba7-116">指出哪些方法 ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型、 WCF 通道模型或 ADO.NET 介面) 可以用來執行作業。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-116">Indicates which of the approaches ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], WCF service model, WCF channel model, or ADO.NET interface) can be used to perform the operations.</span></span>  
  
-   <span data-ttu-id="d6ba7-117">提供有關執行工作，使用所選的方法的詳細資訊連結。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-117">Provides links to more information about performing the task using the chosen approach.</span></span>  
  
|<span data-ttu-id="d6ba7-118">工作</span><span class="sxs-lookup"><span data-stu-id="d6ba7-118">Task</span></span>|<span data-ttu-id="d6ba7-119">BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d6ba7-119">BizTalk Server</span></span>|<span data-ttu-id="d6ba7-120">WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="d6ba7-120">WCF Service Model</span></span>|<span data-ttu-id="d6ba7-121">WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="d6ba7-121">WCF Channel Model</span></span>|<span data-ttu-id="d6ba7-122">ADO.NET 介面</span><span class="sxs-lookup"><span data-stu-id="d6ba7-122">ADO.NET Interface</span></span>|  
|----------|--------------------|-----------------------|-----------------------|-----------------------|  
|<span data-ttu-id="d6ba7-123">商務元件的基本 Insert、 Update、 Delete 和查詢作業</span><span class="sxs-lookup"><span data-stu-id="d6ba7-123">Basic Insert, Update, Delete, and Query operations on business components</span></span>|[<span data-ttu-id="d6ba7-124">在商務元件使用 BizTalk Server 和 Siebel 配接器上執行作業</span><span class="sxs-lookup"><span data-stu-id="d6ba7-124">Run Operations on Business Components Using BizTalk Server and the Siebel adapter</span></span>](run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md)|[<span data-ttu-id="d6ba7-125">使用 Siebel 配接器使用 WCF 服務模型執行商務元件上的作業</span><span class="sxs-lookup"><span data-stu-id="d6ba7-125">Run Operations on Business Components with the Siebel adapter using the WCF Service Model</span></span>](run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)|[<span data-ttu-id="d6ba7-126">使用 Siebel 配接器使用 WCF 通道模型執行商務元件上的作業</span><span class="sxs-lookup"><span data-stu-id="d6ba7-126">Run Operations on Business Components with the Siebel adapter using the WCF Channel Model</span></span>](run-tasks-on-business-components-with-the-siebel-adapter-using-a-wcf-channel.md)|<span data-ttu-id="d6ba7-127">[Siebel 商務元件上執行選取查詢](run-a-select-query-on-business-components-with-siebel.md)**附註：**您只能執行 SELECT 作業使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-127">[Run a SELECT Query on Business Components with Siebel](run-a-select-query-on-business-components-with-siebel.md) **Note:**  You can only perform a SELECT operation using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].</span></span>|  
|<span data-ttu-id="d6ba7-128">MVG 欄位的商務元件上的作業</span><span class="sxs-lookup"><span data-stu-id="d6ba7-128">Operations on business components with MVG fields</span></span>|[<span data-ttu-id="d6ba7-129">使用 MVG 欄位使用 BizTalk Server 和 Siebel 配接器執行商務元件上的作業</span><span class="sxs-lookup"><span data-stu-id="d6ba7-129">Run Operations on Business Components with MVG Fields Using BizTalk Server and the Siebel adapter</span></span>](run-operations-on-business-components-with-mvg-fields-using-the-siebel-adapter.md)|[<span data-ttu-id="d6ba7-130">使用 Siebel 配接器使用 WCF 服務模型執行 MVG 欄位的商務元件上的作業</span><span class="sxs-lookup"><span data-stu-id="d6ba7-130">Run Operations on Business Components with MVG Fields with the Siebel adapter using the WCF Service Model</span></span>](work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)|||  
|<span data-ttu-id="d6ba7-131">在挑選清單欄位的商務元件上的作業</span><span class="sxs-lookup"><span data-stu-id="d6ba7-131">Operations on business components with picklist fields</span></span>|[<span data-ttu-id="d6ba7-132">使用挑選清單欄位使用 BizTalk Server 和 Siebel 配接器執行商務元件上的作業</span><span class="sxs-lookup"><span data-stu-id="d6ba7-132">Run Operations on Business Components with Picklist Fields Using BizTalk Server and the Siebel adapter</span></span>](run-tasks-on-business-components-with-picklist-fields-using-the-siebel-adapter.md)||||  
|<span data-ttu-id="d6ba7-133">叫用商務服務</span><span class="sxs-lookup"><span data-stu-id="d6ba7-133">Invoking business services</span></span>|[<span data-ttu-id="d6ba7-134">叫用商務服務方法使用 BizTalk Server 和 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="d6ba7-134">Invoke Business Service Methods Using BizTalk Server and the Siebel adapter</span></span>](invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)|||[<span data-ttu-id="d6ba7-135">執行與 Siebel 商務服務上的執行作業</span><span class="sxs-lookup"><span data-stu-id="d6ba7-135">Run an EXECUTE Operation on Business Services with Siebel</span></span>](run-an-execute-operation-on-business-services-with-siebel.md)|  
|<span data-ttu-id="d6ba7-136">使用整合物件叫用商務服務</span><span class="sxs-lookup"><span data-stu-id="d6ba7-136">Invoking business services with integration objects</span></span>|[<span data-ttu-id="d6ba7-137">叫用商務服務方法使用整合物件使用 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="d6ba7-137">Invoke Business Service Methods with Integration Objects using the Siebel adapter</span></span>](run-business-service-methods-with-integration-objects-using-the-siebel-adapter.md)||||  

## <a name="next-steps"></a><span data-ttu-id="d6ba7-138">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="d6ba7-138">Next steps</span></span>  
 <span data-ttu-id="d6ba7-139">本節中的主題提供資訊、 程序和範例，以協助您開發應用程式取用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]程式設計方案。</span><span class="sxs-lookup"><span data-stu-id="d6ba7-139">The topics in this section provide information, procedures, and examples to help you develop applications that consume the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in both [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] programming solutions.</span></span> 

- [<span data-ttu-id="d6ba7-140">建立連接至 Siebel 系統</span><span class="sxs-lookup"><span data-stu-id="d6ba7-140">Create a connection to the Siebel system</span></span>](create-a-connection-to-the-siebel-system.md)
- [<span data-ttu-id="d6ba7-141">取得 Visual Studio 中的 Siebel 作業的中繼資料</span><span class="sxs-lookup"><span data-stu-id="d6ba7-141">Get Metadata for Siebel Operations in Visual Studio</span></span>](get-metadata-for-siebel-operations-in-visual-studio.md)
- [<span data-ttu-id="d6ba7-142">中繼資料節點識別碼</span><span class="sxs-lookup"><span data-stu-id="d6ba7-142">Metadata Node IDs</span></span>](metadata-node-ids1.md)
- [<span data-ttu-id="d6ba7-143">使用繫結屬性</span><span class="sxs-lookup"><span data-stu-id="d6ba7-143">Working with the binding properties</span></span>](read-about-biztalk-adapter-for-siebel-binding-properties.md)
- [<span data-ttu-id="d6ba7-144">開發 BizTalk 應用程式使用 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="d6ba7-144">Develop BizTalk applications using the Siebel adapter</span></span>](develop-biztalk-applications-using-the-siebel-adapter.md)
- [<span data-ttu-id="d6ba7-145">開發應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="d6ba7-145">Develop applications using the WCF Service Model</span></span>](develop-siebel-applications-using-the-wcf-service-model.md)
- [<span data-ttu-id="d6ba7-146">開發應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="d6ba7-146">Develop applications using the WCF Channel Model</span></span>](develop-siebel-applications-using-the-wcf-channel-model3.md)
- [<span data-ttu-id="d6ba7-147">使用.NET Framework Data Provider for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="d6ba7-147">Use the .NET Framework Data Provider for Siebel eBusiness Applications</span></span>](use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)
- [<span data-ttu-id="d6ba7-148">搭配 SharePoint 使用 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="d6ba7-148">Use the Siebel Adapter with SharePoint</span></span>](use-the-siebel-adapter-with-sharepoint.md)
- [<span data-ttu-id="d6ba7-149">範例</span><span class="sxs-lookup"><span data-stu-id="d6ba7-149">Samples</span></span>](samples-for-the-siebel-adapter.md)
- [<span data-ttu-id="d6ba7-150">使用 BizTalk adapter 的 ServiceModel Metadata Utility Tool for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="d6ba7-150">Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Siebel eBusiness Applications</span></span>](use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md)