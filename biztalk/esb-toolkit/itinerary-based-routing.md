---
title: "行程為基礎的路由 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28028721-798c-4302-a532-d863ed8ea88b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fbfe8877202a2f691bd30fd2b56fc3032240ee9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="itinerary-based-routing"></a><span data-ttu-id="df18c-102">行程為基礎的路由</span><span class="sxs-lookup"><span data-stu-id="df18c-102">Itinerary-Based Routing</span></span>
<span data-ttu-id="df18c-103">其中一個核心功能的[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]是佈建的行程為基礎的路由，簡化了企業層級的訊息應用程式開發並降低成本的維護大量的靜態傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="df18c-103">One of the core features of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is the provision of itinerary-based routing that simplifies the development of enterprise-level messaging applications and reduces the costs of maintaining a large number of static send ports and receive locations.</span></span>  
  
 <span data-ttu-id="df18c-104">行程所組成 （其中可以包含路由、 轉換及自訂服務） 執行的服務清單和解決每個服務執行所需的中繼資料所需的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="df18c-104">An itinerary consists of the list of services to execute (which can contain routing, transformation, and custom services) and the configuration information required to resolve the metadata necessary to execute each of these services.</span></span> <span data-ttu-id="df18c-105">例如，一個階段的路線可能路由的服務;此服務相關聯的解決方法指示，可能會指示服務来執行會路由傳送的特定目標端點資訊的通用描述、 探索與整合 (UDDI) 或商務規則引擎 (BRE) 查閱訊息。</span><span class="sxs-lookup"><span data-stu-id="df18c-105">For example, one stage of the itinerary may be a routing service; the resolution instructions associated with this service may instruct the service to perform a Universal Description, Discovery, and Integration (UDDI) or Business Rules Engine (BRE) lookup for information about a specific target endpoint to which it will route the message.</span></span>  
  
 <span data-ttu-id="df18c-106">行程可以附加至輸入訊息，以下列方式：</span><span class="sxs-lookup"><span data-stu-id="df18c-106">Itineraries can be attached to an inbound message in the following ways:</span></span>  
  
-   <span data-ttu-id="df18c-107">用戶端提交訊息未包含任何行程相關的資料。</span><span class="sxs-lookup"><span data-stu-id="df18c-107">The message submitted by a client does not contain any itinerary-related data.</span></span> <span data-ttu-id="df18c-108">接收管線會解析、 擷取，並將附加適當訊息內容或內容為基礎的路線。</span><span class="sxs-lookup"><span data-stu-id="df18c-108">The receiving pipeline resolves, retrieves, and attaches the appropriate itinerary based on message content or context.</span></span>  
  
-   <span data-ttu-id="df18c-109">用戶端已提交的郵件可以包含定義路線的參考資料，其中包含計劃的名稱和版本，以及商務活動監控 (BAM) 追蹤的唯一識別碼的 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="df18c-109">The message submitted by a client can contain a SOAP header that defines the itinerary reference data, which contains the itinerary name and version, as well as a unique identifier for Business Activity Monitoring (BAM) tracking.</span></span> <span data-ttu-id="df18c-110">接收管線會評估此資訊，並從 ESBItineraryDb 資料庫擷取適當的路線。</span><span class="sxs-lookup"><span data-stu-id="df18c-110">The receiving pipeline evaluates this information and retrieves the appropriate itinerary from the ESBItineraryDb database.</span></span>  
  
-   <span data-ttu-id="df18c-111">用戶端提交的訊息可以有路線 SOAP 標頭，包含路線的整個內容。</span><span class="sxs-lookup"><span data-stu-id="df18c-111">The message submitted by a client can have an itinerary SOAP header, which contains the entire content of the itinerary.</span></span> <span data-ttu-id="df18c-112">不建議使用這項設計，並應僅用於測試目的使用。</span><span class="sxs-lookup"><span data-stu-id="df18c-112">This design is not recommended and should be used only for testing purposes.</span></span>  
  
 <span data-ttu-id="df18c-113">行程解決用於輸入訊息後，接收管線會升級至訊息內容，因此可用的屬性來存取訂閱這個訊息的任何 Microsoft BizTalk Server 元件的路線資料。</span><span class="sxs-lookup"><span data-stu-id="df18c-113">After an itinerary is resolved for an inbound message, the receive pipeline promotes the itinerary data to the message context, thereby making the properties available to be accessed by any Microsoft BizTalk Server component that subscribes to this message.</span></span> <span data-ttu-id="df18c-114">BizTalk Server 元件可以取得目前的路線步驟的詳細資料，完成必要的處理，及/或路線前進至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="df18c-114">BizTalk Server components can obtain details of the current itinerary step, complete the required processing, and/or advance the itinerary to the next step.</span></span> <span data-ttu-id="df18c-115">這樣會導致下一個服務處理訊息，路線根據發行-訂閱的 BizTalk Server 功能。</span><span class="sxs-lookup"><span data-stu-id="df18c-115">This causes the next service in the itinerary to process the message, according to the publish-subscribe functionality of BizTalk Server.</span></span>  
  
 <span data-ttu-id="df18c-116">ESB 動態解決機制、 轉換、 路線的處理和訊息建立的相關資訊，請參閱[重要案例及開發工作](../esb-toolkit/key-scenarios-and-development-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="df18c-116">For information about the ESB dynamic resolution mechanism, transformations, itinerary processing, and message creation, see [Key Scenarios and Development Tasks](../esb-toolkit/key-scenarios-and-development-tasks.md).</span></span>