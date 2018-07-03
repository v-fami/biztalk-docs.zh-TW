---
title: 詳細處理指示 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed5d92fb-d53b-49a2-b2c7-8558708d6554
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d867737599369ad8ff07780080b16f5ce0f6f2fe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005575"
---
# <a name="processing-instructions-in-detail"></a><span data-ttu-id="63745-102">在 詳細資料的處理指示</span><span class="sxs-lookup"><span data-stu-id="63745-102">Processing Instructions in Detail</span></span>
<span data-ttu-id="63745-103">本主題描述的格式和系統 Properties.xsd 屬性結構描述，定義數個路線處理所需的內容屬性的結構。</span><span class="sxs-lookup"><span data-stu-id="63745-103">This topic describes the format and structure of the System-Properties.xsd property schema, which defines several context properties required for itinerary processing.</span></span> <span data-ttu-id="63745-104">這些屬性會升級，當訊息接收和處理透過 BizTalk Server 管線;因為它們是升級的屬性時，才能夠存取 BizTalk Server 元件。</span><span class="sxs-lookup"><span data-stu-id="63745-104">These properties are promoted when a message is received and processed through BizTalk Server pipelines; because they are promoted properties, they are accessible to BizTalk Server components.</span></span> <span data-ttu-id="63745-105">系統 Properties.xsd 屬性結構描述中定義下列屬性：</span><span class="sxs-lookup"><span data-stu-id="63745-105">The following properties are defined in the System-Properties.xsd property schema:</span></span>  
  
- <span data-ttu-id="63745-106">**ItineraryHeader。**</span><span class="sxs-lookup"><span data-stu-id="63745-106">**ItineraryHeader.**</span></span> <span data-ttu-id="63745-107">此屬性包含所有的路線資訊和要叫用透過一系列路線步驟路線服務的清單。</span><span class="sxs-lookup"><span data-stu-id="63745-107">This property contains all the itinerary information and a list of itinerary services to be invoked through a sequence of itinerary steps.</span></span> <span data-ttu-id="63745-108">路線 API 會在內部使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="63745-108">The Itinerary API uses this property internally.</span></span>  
  
- <span data-ttu-id="63745-109">**ServiceName。**</span><span class="sxs-lookup"><span data-stu-id="63745-109">**ServiceName.**</span></span> <span data-ttu-id="63745-110">此屬性包含要處理的目前路線服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="63745-110">This property contains the name of the current itinerary service to process.</span></span>  
  
- <span data-ttu-id="63745-111">**ServiceState。**</span><span class="sxs-lookup"><span data-stu-id="63745-111">**ServiceState.**</span></span> <span data-ttu-id="63745-112">此屬性包含目前的路線服務的狀態：**暫止**，**完成**，或**Active**。</span><span class="sxs-lookup"><span data-stu-id="63745-112">This property contains the state of the current itinerary service: **Pending**, **Complete**, or **Active**.</span></span> <span data-ttu-id="63745-113">所有服務都訂閱的路線的步驟，其中包含**ServiceState**的值**暫止**。</span><span class="sxs-lookup"><span data-stu-id="63745-113">All services subscribe to an itinerary step that contains a **ServiceState** value of **Pending**.</span></span>  
  
- <span data-ttu-id="63745-114">**ServiceType。**</span><span class="sxs-lookup"><span data-stu-id="63745-114">**ServiceType.**</span></span> <span data-ttu-id="63745-115">這個屬性會定義路線步驟的類型 (**Messaging**或是**協調流程**)。</span><span class="sxs-lookup"><span data-stu-id="63745-115">This property defines the type of the itinerary step (**Messaging** or **Orchestration**).</span></span>  
  
- <span data-ttu-id="63745-116">**IsRequestResponse。**</span><span class="sxs-lookup"><span data-stu-id="63745-116">**IsRequestResponse.**</span></span> <span data-ttu-id="63745-117">這個屬性會定義訊息類型 (單向或要求-回應)。</span><span class="sxs-lookup"><span data-stu-id="63745-117">This property defines the messaging type (one-way or request-response).</span></span>  
  
  <span data-ttu-id="63745-118">路線服務中其中一種方式，根據的值執行路線的步驟**ServiceType**屬性：</span><span class="sxs-lookup"><span data-stu-id="63745-118">The Itinerary service executes itinerary steps in one of two ways, depending on the value of the **ServiceType** property:</span></span>  
  
- <span data-ttu-id="63745-119">路線的管線元件會執行所有的路線步驟，與**ServiceType**屬性**Messaging**。</span><span class="sxs-lookup"><span data-stu-id="63745-119">Itinerary pipeline components execute all itinerary steps with a **ServiceType** property of **Messaging**.</span></span> <span data-ttu-id="63745-120">開發人員可以擴充使用自訂的管線和路線 API，此程序。</span><span class="sxs-lookup"><span data-stu-id="63745-120">Developers can extend this process using a custom pipeline and the Itinerary API.</span></span>  
  
- <span data-ttu-id="63745-121">當**ServiceType**屬性是**協調流程**，協調流程，由訂用帳戶，路線的內容屬性，以啟動執行路線的步驟。</span><span class="sxs-lookup"><span data-stu-id="63745-121">When the **ServiceType** property is **Orchestration**, an orchestration, activated by a subscription to itinerary context properties, executes the itinerary step.</span></span>  
  
  <span data-ttu-id="63745-122">路線服務處理路線的步驟時，服務會負責前進的路線，並使用發行的進一步處理的新路線內容與將訊息分派-訂閱的 BizTalk Server 的功能。</span><span class="sxs-lookup"><span data-stu-id="63745-122">When an Itinerary service processes an itinerary step, the service is responsible for advancing the itinerary and dispatching the message with a new itinerary context for further processing using the publish-subscribe functionality of BizTalk Server.</span></span> <span data-ttu-id="63745-123">路線服務的訊息內容中路線的完整控制，而且可以前進到其內部邏輯和訊息內容為基礎的適當步驟。</span><span class="sxs-lookup"><span data-stu-id="63745-123">An itinerary service has full control of the itinerary in the message context and can advance to the appropriate step based on its internal logic and the message content.</span></span>  
  
  <span data-ttu-id="63745-124">路線的處理機制會支援單一行程內的傳訊與協調流程路線步驟的組合。</span><span class="sxs-lookup"><span data-stu-id="63745-124">The itinerary processing mechanism supports the combination of messaging and orchestration itinerary steps within a single itinerary.</span></span> <span data-ttu-id="63745-125">開發人員也可以定義自訂路線服務，並設定自訂路線的步驟。</span><span class="sxs-lookup"><span data-stu-id="63745-125">Developers can also define custom itinerary services and configure custom itinerary steps.</span></span>  
  
  <span data-ttu-id="63745-126">如需路線的詳細資訊，請參閱[安裝和執行路線入口範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="63745-126">For more information about itineraries, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span></span>  
  
  <span data-ttu-id="63745-127">如需有關自訂路線服務和自訂的路線步驟的詳細資訊，請參閱[建立自訂路線服務](../esb-toolkit/creating-a-custom-itinerary-service.md)。</span><span class="sxs-lookup"><span data-stu-id="63745-127">For more information about custom itinerary services and custom itinerary steps, see [Creating a Custom Itinerary Service](../esb-toolkit/creating-a-custom-itinerary-service.md).</span></span>