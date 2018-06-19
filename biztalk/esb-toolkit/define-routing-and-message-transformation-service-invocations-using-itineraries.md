---
title: 定義路由和訊息轉換服務引動過程使用旅 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e6f2448e-a5a7-496c-86d3-47f12e6f1251
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 975c830f73e0de362b25f312a8d41c4b15368cfd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294278"
---
# <a name="defining-routing-and-message-transformation-service-invocations-using-itineraries"></a><span data-ttu-id="e54b1-102">定義路由和訊息轉換服務使用旅的引動過程</span><span class="sxs-lookup"><span data-stu-id="e54b1-102">Defining Routing and Message Transformation Service Invocations Using Itineraries</span></span>
<span data-ttu-id="e54b1-103">在此使用案例，提交進行處理的訊息會包含路線的 SOAP 標頭描述要執行的服務和其解析需求的清單。</span><span class="sxs-lookup"><span data-stu-id="e54b1-103">In this use case, a message submitted for processing contains an itinerary SOAP header that describes the list of services to execute and their resolution requirements.</span></span> <span data-ttu-id="e54b1-104">具體而言，轉換和路由服務會定義，每個選擇性需要透過通用描述、 探索與整合 (UDDI)、 商務規則引擎原則、 XML 路徑語言 (XPath) 或靜態查閱解析。</span><span class="sxs-lookup"><span data-stu-id="e54b1-104">Specifically, a transformation and routing service are defined, each optionally requiring resolution through a Universal Description, Discovery, and Integration (UDDI), Business Rules Engine Policy, XML Path Language (XPath), or STATIC lookup.</span></span> <span data-ttu-id="e54b1-105">此使用案例可以透過在發行訊息時，將其他服務加入至路線擴充。</span><span class="sxs-lookup"><span data-stu-id="e54b1-105">This use case can be extended by adding other services to the itinerary at the time of message publication.</span></span>  
  
 <span data-ttu-id="e54b1-106">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供兩種類型的路線上坡道提升： 支援單向通訊及支援要求-回應實例。</span><span class="sxs-lookup"><span data-stu-id="e54b1-106">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides two types of itinerary on-ramps: those that support one-way communication and those that support request-response scenarios.</span></span> <span data-ttu-id="e54b1-107">動態解析機制可以使用在路線資訊，來查閱端點或動態地繫結至端點，因為沒有為 Microsoft BizTalk Server 包含特定端點的路由詳細資料的需求。</span><span class="sxs-lookup"><span data-stu-id="e54b1-107">Because the dynamic resolution mechanism can use information in the itinerary to look up endpoints or bind dynamically to endpoints, there is no requirement for Microsoft BizTalk Server to contain specific endpoint routing details.</span></span> <span data-ttu-id="e54b1-108">圖 1 所示處理程序的圖解的檢視。</span><span class="sxs-lookup"><span data-stu-id="e54b1-108">Figure 1 illustrates a schematic view of the process.</span></span>  
  
 <span data-ttu-id="e54b1-109">![定義路由服務引動過程](../esb-toolkit/media/ch3-definingroutingserviceinvocation.gif "Ch3 DefiningRoutingServiceInvocation")</span><span class="sxs-lookup"><span data-stu-id="e54b1-109">![Defining Routing service Invocation](../esb-toolkit/media/ch3-definingroutingserviceinvocation.gif "Ch3-DefiningRoutingServiceInvocation")</span></span>  
  
 <span data-ttu-id="e54b1-110">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="e54b1-110">**Figure 1**</span></span>  
  
 <span data-ttu-id="e54b1-111">**定義路由和訊息轉換服務引動過程使用旅**</span><span class="sxs-lookup"><span data-stu-id="e54b1-111">**Defining routing and message transformation service invocations using itineraries**</span></span>  
  
 <span data-ttu-id="e54b1-112">隨附的行程上手範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="e54b1-112">The Itinerary On-Ramp sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="e54b1-113">它會顯示如何建立包含解析，路由的行程和服務驗證為一系列的路線步驟定義的引動過程指示如何[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]和 BizTalk Server 會處理訊息使用發行-訂閱的功能BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="e54b1-113">It shows how to create itineraries that contain resolution, routing, and service invocation instructions as a series of itinerary steps that define how the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and BizTalk Server will process the message using the publish-subscribe functionality of BizTalk Server.</span></span> <span data-ttu-id="e54b1-114">單向和要求-回應 」 範例隨附。</span><span class="sxs-lookup"><span data-stu-id="e54b1-114">One-way and request-response samples are included.</span></span>  
  
 <span data-ttu-id="e54b1-115">如需詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="e54b1-115">For more information, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span></span>