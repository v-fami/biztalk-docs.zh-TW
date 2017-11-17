---
title: "轉換，並將訊息路由傳送至多個端點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 544db12c-95fc-4321-b397-ec9e7410e37d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99e30c2d7b095d0b075b98a48f9263abd361b6cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transforming-and-routing-a-message-to-multiple-endpoints"></a><span data-ttu-id="5dfc1-102">轉換，並將訊息路由傳送至多個端點</span><span class="sxs-lookup"><span data-stu-id="5dfc1-102">Transforming and Routing a Message to Multiple Endpoints</span></span>
<span data-ttu-id="5dfc1-103">在此使用案例中，ESB 執行轉換，透過路線 Web 服務上手提交的訊息。</span><span class="sxs-lookup"><span data-stu-id="5dfc1-103">In this use case, the ESB performs a transformation on a message submitted through the Itinerary Web service on-ramp.</span></span> <span data-ttu-id="5dfc1-104">動態解析查閱決定對應名稱，並將轉換輸入的訊息。</span><span class="sxs-lookup"><span data-stu-id="5dfc1-104">A dynamic resolution lookup determines the map name and transforms the inbound message.</span></span> <span data-ttu-id="5dfc1-105">此外，路線指定 n 個行程服務會以動態方式解析並，它會將訊息路由傳送已轉換的目標端點。</span><span class="sxs-lookup"><span data-stu-id="5dfc1-105">Additionally, the itinerary specifies n number of target endpoints that the Itinerary service will dynamically resolve and to which it will route the transformed message.</span></span> <span data-ttu-id="5dfc1-106">所有作業都發生在傳訊層，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="5dfc1-106">All operations occur at the messaging layer, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="5dfc1-107">![轉換多個端點](../esb-toolkit/media/ch3-transformingmultipleendpoints.gif "Ch3 TransformingMultipleEndpoints")</span><span class="sxs-lookup"><span data-stu-id="5dfc1-107">![Transforming Multiple Endpoints](../esb-toolkit/media/ch3-transformingmultipleendpoints.gif "Ch3-TransformingMultipleEndpoints")</span></span>  
  
 <span data-ttu-id="5dfc1-108">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="5dfc1-108">**Figure 1**</span></span>  
  
 <span data-ttu-id="5dfc1-109">**轉換，並將訊息路由傳送至多個端點**</span><span class="sxs-lookup"><span data-stu-id="5dfc1-109">**Transforming and routing a message to multiple endpoints**</span></span>  
  
 <span data-ttu-id="5dfc1-110">動態解析 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="5dfc1-110">The Dynamic Resolution sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="5dfc1-111">它會顯示如何使用 ESB 管線元件，特別是，ESB 分派解譯器元件，以動態解析端點位置、 設定路由的屬性，並解析以及執行[!INCLUDE[prague](../includes/prague-md.md)]對應在訊息層級，而不使用協調流程。</span><span class="sxs-lookup"><span data-stu-id="5dfc1-111">It shows how to use ESB pipeline components, specifically the ESB Dispatch Disassembler component, to dynamically resolve endpoint location, set routing properties, and resolve and execute [!INCLUDE[prague](../includes/prague-md.md)] maps at the messaging level, without using an orchestration.</span></span> <span data-ttu-id="5dfc1-112">它也示範單向和雙向的訊息模式。</span><span class="sxs-lookup"><span data-stu-id="5dfc1-112">It also demonstrates both one-way and two-way messaging patterns.</span></span>  
  
 <span data-ttu-id="5dfc1-113">如需詳細資訊，請參閱[安裝及執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)和[安裝及執行多個 Web 服務範例](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5dfc1-113">For more information, see [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md) and [Installing and Running the Multiple Web Services Sample](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).</span></span>