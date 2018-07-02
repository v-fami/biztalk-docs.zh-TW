---
title: 以路線為基礎的路由 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 28028721-798c-4302-a532-d863ed8ea88b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13be8ab9078a2c12e110c5d80b65b2930d805952
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970879"
---
# <a name="itinerary-based-routing"></a><span data-ttu-id="313ce-102">以路線為基礎的路由</span><span class="sxs-lookup"><span data-stu-id="313ce-102">Itinerary-Based Routing</span></span>
<span data-ttu-id="313ce-103">核心功能的其中一個[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]是佈建的路線為基礎的路由，來簡化開發企業級傳訊應用程式，並降低成本的維護大量的靜態傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="313ce-103">One of the core features of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is the provision of itinerary-based routing that simplifies the development of enterprise-level messaging applications and reduces the costs of maintaining a large number of static send ports and receive locations.</span></span>  
  
 <span data-ttu-id="313ce-104">路線是由執行的服務清單 （其中可以包含路由、 轉換和自訂的服務） 和解決每項服務的執行時所需的中繼資料所需的組態資訊所組成。</span><span class="sxs-lookup"><span data-stu-id="313ce-104">An itinerary consists of the list of services to execute (which can contain routing, transformation, and custom services) and the configuration information required to resolve the metadata necessary to execute each of these services.</span></span> <span data-ttu-id="313ce-105">例如，一個階段的路線可能路由的服務;此服務相關聯的解決方法指示可能指示來執行通用描述、 探索與整合 (UDDI) 或商務規則引擎 (BRE) 查閱特定的目標端點，它會將路由的相關資訊的服務訊息。</span><span class="sxs-lookup"><span data-stu-id="313ce-105">For example, one stage of the itinerary may be a routing service; the resolution instructions associated with this service may instruct the service to perform a Universal Description, Discovery, and Integration (UDDI) or Business Rules Engine (BRE) lookup for information about a specific target endpoint to which it will route the message.</span></span>  
  
 <span data-ttu-id="313ce-106">路線可以附加至輸入訊息，以下列方式：</span><span class="sxs-lookup"><span data-stu-id="313ce-106">Itineraries can be attached to an inbound message in the following ways:</span></span>  
  
- <span data-ttu-id="313ce-107">用戶端提交的訊息不包含任何行程相關的資料。</span><span class="sxs-lookup"><span data-stu-id="313ce-107">The message submitted by a client does not contain any itinerary-related data.</span></span> <span data-ttu-id="313ce-108">接收管線會解析、 擷取，並會附加適當的路線，根據訊息內容或內容。</span><span class="sxs-lookup"><span data-stu-id="313ce-108">The receiving pipeline resolves, retrieves, and attaches the appropriate itinerary based on message content or context.</span></span>  
  
- <span data-ttu-id="313ce-109">用戶端所提交的郵件可以包含 SOAP 標頭，以定義路線的參考資料，其中包含路線的名稱和版本，以及商務活動監控 (BAM) 追蹤的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="313ce-109">The message submitted by a client can contain a SOAP header that defines the itinerary reference data, which contains the itinerary name and version, as well as a unique identifier for Business Activity Monitoring (BAM) tracking.</span></span> <span data-ttu-id="313ce-110">接收管線會評估這項資訊，並從 ESBItineraryDb 資料庫擷取適當的路線。</span><span class="sxs-lookup"><span data-stu-id="313ce-110">The receiving pipeline evaluates this information and retrieves the appropriate itinerary from the ESBItineraryDb database.</span></span>  
  
- <span data-ttu-id="313ce-111">用戶端提交的訊息可以有路線 SOAP 標頭，包含路線的整個內容。</span><span class="sxs-lookup"><span data-stu-id="313ce-111">The message submitted by a client can have an itinerary SOAP header, which contains the entire content of the itinerary.</span></span> <span data-ttu-id="313ce-112">這項設計不建議，並應僅用於測試目的。</span><span class="sxs-lookup"><span data-stu-id="313ce-112">This design is not recommended and should be used only for testing purposes.</span></span>  
  
  <span data-ttu-id="313ce-113">路線解析用於輸入訊息之後，接收管線會升級至訊息內容，因此可用的屬性來存取此訊息會訂閱任何 Microsoft BizTalk Server 元件的路線資料。</span><span class="sxs-lookup"><span data-stu-id="313ce-113">After an itinerary is resolved for an inbound message, the receive pipeline promotes the itinerary data to the message context, thereby making the properties available to be accessed by any Microsoft BizTalk Server component that subscribes to this message.</span></span> <span data-ttu-id="313ce-114">BizTalk Server 元件可以取得目前的路線步驟的詳細資料，完成必要的處理，及/或前進至下一個步驟的路線。</span><span class="sxs-lookup"><span data-stu-id="313ce-114">BizTalk Server components can obtain details of the current itinerary step, complete the required processing, and/or advance the itinerary to the next step.</span></span> <span data-ttu-id="313ce-115">這將導致下一個服務來處理訊息，路線根據發行-訂閱的 BizTalk Server 的功能。</span><span class="sxs-lookup"><span data-stu-id="313ce-115">This causes the next service in the itinerary to process the message, according to the publish-subscribe functionality of BizTalk Server.</span></span>  
  
  <span data-ttu-id="313ce-116">ESB 動態解析機制、 轉換、 路線的處理和訊息建立的相關資訊，請參閱[重要案例及開發工作](../esb-toolkit/key-scenarios-and-development-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="313ce-116">For information about the ESB dynamic resolution mechanism, transformations, itinerary processing, and message creation, see [Key Scenarios and Development Tasks](../esb-toolkit/key-scenarios-and-development-tasks.md).</span></span>