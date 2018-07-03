---
title: BizTalk ESB 工具組的內容 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e7114df-dadf-49ab-b024-44d84e47faa5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af25a536152544f26d55eebab1d11ee76493187c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009431"
---
# <a name="contents-of-the-biztalk-esb-toolkit"></a><span data-ttu-id="9f7cd-102">BizTalk ESB 工具組的內容</span><span class="sxs-lookup"><span data-stu-id="9f7cd-102">Contents of the BizTalk ESB Toolkit</span></span>
<span data-ttu-id="9f7cd-103">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供架構指引、 模式和作法，以及 BizTalk Server 和.NET Framework 元件，可簡化 Microsoft 平台上的企業級解決方案的開發工作的集合。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides architectural guidance, patterns and practices, and a collection of BizTalk Server and .NET Framework components to simplify the development of enterprise-scale solutions on the Microsoft platform.</span></span> <span data-ttu-id="9f7cd-104">此工具組也提供功能，可協助開發人員擴充現有的訊息和整合方案。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-104">The toolkit also provides capabilities to help developers extend existing messaging and integration solutions.</span></span> <span data-ttu-id="9f7cd-105">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]集合間的互通性支援，並實作鬆散偶合的傳訊環境，可簡化建置動態訊息為基礎的企業應用程式的程序的元件所組成。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-105">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] consists of a collection of interoperating components that support and implement a loosely coupled messaging environment that simplifies the process of building dynamic message-based enterprise applications.</span></span>  

 <span data-ttu-id="9f7cd-106">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="9f7cd-106">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains the following components:</span></span>  

- <span data-ttu-id="9f7cd-107">[ESB Web 服務](../esb-toolkit/esb-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-107">[ESB Web Services](../esb-toolkit/esb-web-services.md).</span></span> <span data-ttu-id="9f7cd-108">這些重要功能，ESB 取用者，例如以路線為基礎的路由、 例外狀況管理、 動態解析端點和地圖、 BizTalk 作業通用描述、 探索與整合 (UDDI) 互通性，以公開 （expose) 和訊息內容的轉換。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-108">These expose key capabilities to ESB consumers, such as itinerary-based routing, exception management, dynamic resolution of endpoints and maps, BizTalk operations, Universal Description, Discovery, and Integration (UDDI) interoperability, and transformation of message content.</span></span>  

- <span data-ttu-id="9f7cd-109">[ESB 管理入口網站](../esb-toolkit/esb-management-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-109">[ESB Management Portal](../esb-toolkit/esb-management-portal.md).</span></span> <span data-ttu-id="9f7cd-110">這提供例外狀況和錯誤追蹤訊息重新提交，警示和通知、 UDDI 整合、 報告和分析，和組態功能的支援。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-110">This provides support for exception and fault tracking, message resubmission, alerts and notifications, UDDI integration, reporting and analytics, and configuration capabilities.</span></span>  

- <span data-ttu-id="9f7cd-111">[ESB 管線 Interop 元件](../esb-toolkit/esb-pipeline-interop-components.md)。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-111">[ESB Pipeline Interop Components](../esb-toolkit/esb-pipeline-interop-components.md).</span></span> <span data-ttu-id="9f7cd-112">這些提供 BizTalk Server 管線元件，以便與外部系統的互通性。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-112">These provide BizTalk Server pipeline components that facilitate interoperability with external systems.</span></span>  

- <span data-ttu-id="9f7cd-113">[例外狀況管理架構](../esb-toolkit/exception-management-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-113">[Exception Management Framework](../esb-toolkit/exception-management-framework.md).</span></span> <span data-ttu-id="9f7cd-114">這會擷取與 BizTalk 傳訊與協調流程的子系統中的例外狀況會彙總，並提供單一機制來處理錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-114">This captures and consolidates exceptions from both BizTalk Messaging and Orchestration subsystems and provides a single mechanism for handling fault messages.</span></span> <span data-ttu-id="9f7cd-115">其中包括例外狀況 Web 服務、 例外狀況管理 API，以及豐富、 處理和傳遞給 ESB 管理入口網站的 例外狀況詳細資料的元件。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-115">It includes the exception Web service, the exception management API, and components that enrich, process, and pass exception details to the ESB Management Portal.</span></span>  

- <span data-ttu-id="9f7cd-116">[ESB 解析程式和配接器提供者架構](../esb-toolkit/esb-resolver-and-adapter-provider-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-116">[ESB Resolver and Adapter Provider Framework](../esb-toolkit/esb-resolver-and-adapter-provider-framework.md).</span></span> <span data-ttu-id="9f7cd-117">這會實作可外掛且可設定的架構，用於動態解析端點和轉換需求和傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-117">This implements a pluggable and configurable architecture for dynamically resolving endpoints and transform requirements and for routing messages.</span></span>  

- <span data-ttu-id="9f7cd-118">[以路線為基礎的路由和處理](../esb-toolkit/itinerary-based-routing-and-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-118">[Itinerary-Based Routing and Processing](../esb-toolkit/itinerary-based-routing-and-processing.md).</span></span> <span data-ttu-id="9f7cd-119">路線處理機制，提供以動態方式描述、 送出和執行多個服務引動過程或轉換路由要求的輕量級功能。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-119">The Itinerary Processing mechanism provides a lightweight capability for dynamically describing, submitting, and executing multiple service invocations or routing/transformation requests.</span></span>  

- <span data-ttu-id="9f7cd-120">[BizTalk ESB 工具組範例應用程式](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-120">[BizTalk ESB Toolkit Sample Applications](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md).</span></span> <span data-ttu-id="9f7cd-121">包含的範例應用程式中示範的可能實作[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，以及如何使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]自己的 SOA 和 ESB 應用程式中的功能。</span><span class="sxs-lookup"><span data-stu-id="9f7cd-121">The included sample applications demonstrate possible implementations of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and how you can use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] features in your own SOA and ESB applications.</span></span>
