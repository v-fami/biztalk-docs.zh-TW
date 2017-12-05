---
title: "詳細資料中的處理指示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed5d92fb-d53b-49a2-b2c7-8558708d6554
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cf0a726d2c8c4f6242ed19a7dcd1e5430775e63
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="processing-instructions-in-detail"></a><span data-ttu-id="791f0-102">詳細資料中的處理指示</span><span class="sxs-lookup"><span data-stu-id="791f0-102">Processing Instructions in Detail</span></span>
<span data-ttu-id="791f0-103">本主題描述的格式和系統 Properties.xsd 屬性結構描述、 定義路線處理所需的數個內容屬性的結構。</span><span class="sxs-lookup"><span data-stu-id="791f0-103">This topic describes the format and structure of the System-Properties.xsd property schema, which defines several context properties required for itinerary processing.</span></span> <span data-ttu-id="791f0-104">收到訊息並處理透過 BizTalk Server 管線; 時，這些屬性會升級因為它們是升級的屬性，都能夠存取 BizTalk Server 元件。</span><span class="sxs-lookup"><span data-stu-id="791f0-104">These properties are promoted when a message is received and processed through BizTalk Server pipelines; because they are promoted properties, they are accessible to BizTalk Server components.</span></span> <span data-ttu-id="791f0-105">系統 Properties.xsd 屬性結構描述中定義下列屬性：</span><span class="sxs-lookup"><span data-stu-id="791f0-105">The following properties are defined in the System-Properties.xsd property schema:</span></span>  
  
-   <span data-ttu-id="791f0-106">**ItineraryHeader。**</span><span class="sxs-lookup"><span data-stu-id="791f0-106">**ItineraryHeader.**</span></span> <span data-ttu-id="791f0-107">此屬性包含所有的路線資訊和透過一系列路線步驟要叫用的路線服務的清單。</span><span class="sxs-lookup"><span data-stu-id="791f0-107">This property contains all the itinerary information and a list of itinerary services to be invoked through a sequence of itinerary steps.</span></span> <span data-ttu-id="791f0-108">行程 API 會在內部使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="791f0-108">The Itinerary API uses this property internally.</span></span>  
  
-   <span data-ttu-id="791f0-109">**ServiceName。**</span><span class="sxs-lookup"><span data-stu-id="791f0-109">**ServiceName.**</span></span> <span data-ttu-id="791f0-110">此屬性包含要處理的目前路線服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="791f0-110">This property contains the name of the current itinerary service to process.</span></span>  
  
-   <span data-ttu-id="791f0-111">**ServiceState。**</span><span class="sxs-lookup"><span data-stu-id="791f0-111">**ServiceState.**</span></span> <span data-ttu-id="791f0-112">此屬性包含目前路線服務的狀態：**暫止**，**完成**，或**Active**。</span><span class="sxs-lookup"><span data-stu-id="791f0-112">This property contains the state of the current itinerary service: **Pending**, **Complete**, or **Active**.</span></span> <span data-ttu-id="791f0-113">所有服務都訂閱包含路線步驟**ServiceState**值**暫止**。</span><span class="sxs-lookup"><span data-stu-id="791f0-113">All services subscribe to an itinerary step that contains a **ServiceState** value of **Pending**.</span></span>  
  
-   <span data-ttu-id="791f0-114">**ServiceType。**</span><span class="sxs-lookup"><span data-stu-id="791f0-114">**ServiceType.**</span></span> <span data-ttu-id="791f0-115">此屬性會定義路線步驟的類型 (**傳訊**或**協調流程**)。</span><span class="sxs-lookup"><span data-stu-id="791f0-115">This property defines the type of the itinerary step (**Messaging** or **Orchestration**).</span></span>  
  
-   <span data-ttu-id="791f0-116">**IsRequestResponse。**</span><span class="sxs-lookup"><span data-stu-id="791f0-116">**IsRequestResponse.**</span></span> <span data-ttu-id="791f0-117">此屬性會定義訊息類型 (單向或要求-回應)。</span><span class="sxs-lookup"><span data-stu-id="791f0-117">This property defines the messaging type (one-way or request-response).</span></span>  
  
 <span data-ttu-id="791f0-118">路線服務的其中一種方式，根據的值執行路線步驟**ServiceType**屬性：</span><span class="sxs-lookup"><span data-stu-id="791f0-118">The Itinerary service executes itinerary steps in one of two ways, depending on the value of the **ServiceType** property:</span></span>  
  
-   <span data-ttu-id="791f0-119">路線的管線元件會執行所有的路線步驟與**ServiceType**屬性**傳訊**。</span><span class="sxs-lookup"><span data-stu-id="791f0-119">Itinerary pipeline components execute all itinerary steps with a **ServiceType** property of **Messaging**.</span></span> <span data-ttu-id="791f0-120">開發人員可以擴充此程序使用自訂管線和行程 API。</span><span class="sxs-lookup"><span data-stu-id="791f0-120">Developers can extend this process using a custom pipeline and the Itinerary API.</span></span>  
  
-   <span data-ttu-id="791f0-121">當**ServiceType**屬性是**協調流程**，協調流程，由訂閱路線內容屬性，以啟用執行路線的步驟。</span><span class="sxs-lookup"><span data-stu-id="791f0-121">When the **ServiceType** property is **Orchestration**, an orchestration, activated by a subscription to itinerary context properties, executes the itinerary step.</span></span>  
  
 <span data-ttu-id="791f0-122">當路線服務處理序路線的步驟時，服務會負責前進的路線，並與新的路線內容使用發佈的進一步處理訊息分派-訂閱的 BizTalk Server 功能。</span><span class="sxs-lookup"><span data-stu-id="791f0-122">When an Itinerary service processes an itinerary step, the service is responsible for advancing the itinerary and dispatching the message with a new itinerary context for further processing using the publish-subscribe functionality of BizTalk Server.</span></span> <span data-ttu-id="791f0-123">路線服務的訊息內容中路線的 完全控制、 可以前進到適當的步驟，根據其內部的邏輯和訊息內容。</span><span class="sxs-lookup"><span data-stu-id="791f0-123">An itinerary service has full control of the itinerary in the message context and can advance to the appropriate step based on its internal logic and the message content.</span></span>  
  
 <span data-ttu-id="791f0-124">路線處理機制支援單一行程內的傳訊和協調流程路線步驟的組合。</span><span class="sxs-lookup"><span data-stu-id="791f0-124">The itinerary processing mechanism supports the combination of messaging and orchestration itinerary steps within a single itinerary.</span></span> <span data-ttu-id="791f0-125">開發人員也可以定義自訂的路線服務和設定自訂路線的步驟。</span><span class="sxs-lookup"><span data-stu-id="791f0-125">Developers can also define custom itinerary services and configure custom itinerary steps.</span></span>  
  
 <span data-ttu-id="791f0-126">如需行程的詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="791f0-126">For more information about itineraries, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span></span>  
  
 <span data-ttu-id="791f0-127">如需自訂路線服務和自訂的路線步驟的詳細資訊，請參閱[建立自訂的行程服務](../esb-toolkit/creating-a-custom-itinerary-service.md)。</span><span class="sxs-lookup"><span data-stu-id="791f0-127">For more information about custom itinerary services and custom itinerary steps, see [Creating a Custom Itinerary Service](../esb-toolkit/creating-a-custom-itinerary-service.md).</span></span>