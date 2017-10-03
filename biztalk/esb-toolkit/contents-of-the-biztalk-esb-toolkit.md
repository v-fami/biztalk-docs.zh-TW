---
title: "BizTalk ESB 工具組的內容 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e7114df-dadf-49ab-b024-44d84e47faa5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3dcfc5bbe761f70269c31294484ee37e7e79f83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="contents-of-the-biztalk-esb-toolkit"></a><span data-ttu-id="258a5-102">BizTalk ESB 工具組的內容</span><span class="sxs-lookup"><span data-stu-id="258a5-102">Contents of the BizTalk ESB Toolkit</span></span>
<span data-ttu-id="258a5-103">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供的架構指引、 模式和作法，以及 BizTalk Server 和.NET Framework 元件，可簡化開發 Microsoft 平台上的企業級解決方案的集合。</span><span class="sxs-lookup"><span data-stu-id="258a5-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides architectural guidance, patterns and practices, and a collection of BizTalk Server and .NET Framework components to simplify the development of enterprise-scale solutions on the Microsoft platform.</span></span> <span data-ttu-id="258a5-104">此工具組也提供功能，可協助開發人員擴充現有的訊息和整合解決方案。</span><span class="sxs-lookup"><span data-stu-id="258a5-104">The toolkit also provides capabilities to help developers extend existing messaging and integration solutions.</span></span> <span data-ttu-id="258a5-105">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]集合間的互通性支援並實作鬆散偶合的傳訊環境，可簡化建立動態的訊息型企業應用程式的程序的元件所組成。</span><span class="sxs-lookup"><span data-stu-id="258a5-105">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] consists of a collection of interoperating components that support and implement a loosely coupled messaging environment that simplifies the process of building dynamic message-based enterprise applications.</span></span>  
  
 <span data-ttu-id="258a5-106">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="258a5-106">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains the following components:</span></span>  
  
-   <span data-ttu-id="258a5-107">[ESB Web 服務](../esb-toolkit/esb-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="258a5-107">[ESB Web Services](../esb-toolkit/esb-web-services.md).</span></span> <span data-ttu-id="258a5-108">這些公開 （expose) 給 ESB 取用者，例如行程為基礎的路由、 例外狀況管理、 動態端點和地圖、 BizTalk 作業通用描述、 探索與整合 (UDDI) 的互通性，解決的重要功能與訊息內容的轉換。</span><span class="sxs-lookup"><span data-stu-id="258a5-108">These expose key capabilities to ESB consumers, such as itinerary-based routing, exception management, dynamic resolution of endpoints and maps, BizTalk operations, Universal Description, Discovery, and Integration (UDDI) interoperability, and transformation of message content.</span></span>  
  
-   <span data-ttu-id="258a5-109">[ESB 管理入口網站](../esb-toolkit/esb-management-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="258a5-109">[ESB Management Portal](../esb-toolkit/esb-management-portal.md).</span></span> <span data-ttu-id="258a5-110">這樣會支援例外狀況和錯誤追蹤訊息重新提交，警示和通知、 UDDI 整合、 報告和分析，和組態功能。</span><span class="sxs-lookup"><span data-stu-id="258a5-110">This provides support for exception and fault tracking, message resubmission, alerts and notifications, UDDI integration, reporting and analytics, and configuration capabilities.</span></span>  
  
-   <span data-ttu-id="258a5-111">[ESB 管線 Interop 元件](../esb-toolkit/esb-pipeline-interop-components.md)。</span><span class="sxs-lookup"><span data-stu-id="258a5-111">[ESB Pipeline Interop Components](../esb-toolkit/esb-pipeline-interop-components.md).</span></span> <span data-ttu-id="258a5-112">這些提供 BizTalk Server 管線元件，以便與外部系統的互通性。</span><span class="sxs-lookup"><span data-stu-id="258a5-112">These provide BizTalk Server pipeline components that facilitate interoperability with external systems.</span></span>  
  
-   <span data-ttu-id="258a5-113">[例外狀況管理架構](../esb-toolkit/exception-management-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="258a5-113">[Exception Management Framework](../esb-toolkit/exception-management-framework.md).</span></span> <span data-ttu-id="258a5-114">這會擷取從 BizTalk 傳訊和協調流程子系統的例外狀況會彙總，並提供單一機制來處理錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="258a5-114">This captures and consolidates exceptions from both BizTalk Messaging and Orchestration subsystems and provides a single mechanism for handling fault messages.</span></span> <span data-ttu-id="258a5-115">它包含例外狀況的 Web 服務、 例外狀況管理 API 和擴充，程序，並傳遞例外狀況詳細資料 ESB 管理入口網站的元件。</span><span class="sxs-lookup"><span data-stu-id="258a5-115">It includes the exception Web service, the exception management API, and components that enrich, process, and pass exception details to the ESB Management Portal.</span></span>  
  
-   <span data-ttu-id="258a5-116">[ESB 解析器和配接器提供者架構](../esb-toolkit/esb-resolver-and-adapter-provider-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="258a5-116">[ESB Resolver and Adapter Provider Framework](../esb-toolkit/esb-resolver-and-adapter-provider-framework.md).</span></span> <span data-ttu-id="258a5-117">這會實作動態解析端點和轉換的需求和訊息路由傳送隨插即用和設定的基礎架構。</span><span class="sxs-lookup"><span data-stu-id="258a5-117">This implements a pluggable and configurable architecture for dynamically resolving endpoints and transform requirements and for routing messages.</span></span>  
  
-   <span data-ttu-id="258a5-118">[路由和處理行程基礎](../esb-toolkit/itinerary-based-routing-and-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="258a5-118">[Itinerary-Based Routing and Processing](../esb-toolkit/itinerary-based-routing-and-processing.md).</span></span> <span data-ttu-id="258a5-119">行程處理機制提供以動態方式描述、 送出，並執行多個服務引動過程或轉換路由要求的輕量級功能。</span><span class="sxs-lookup"><span data-stu-id="258a5-119">The Itinerary Processing mechanism provides a lightweight capability for dynamically describing, submitting, and executing multiple service invocations or routing/transformation requests.</span></span>  
  
-   <span data-ttu-id="258a5-120">[BizTalk ESB 工具組範例應用程式](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="258a5-120">[BizTalk ESB Toolkit Sample Applications](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md).</span></span> <span data-ttu-id="258a5-121">包含的範例應用程式示範的可能實作[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]以及如何使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]自己的 SOA 和 ESB 應用程式中的功能。</span><span class="sxs-lookup"><span data-stu-id="258a5-121">The included sample applications demonstrate possible implementations of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and how you can use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] features in your own SOA and ESB applications.</span></span>