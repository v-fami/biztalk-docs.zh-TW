---
title: "定義自訂協調流程服務執行使用旅 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6089169d-2fa1-4f81-afe1-db9d90a10382
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9336969db2c90168bf7c398276205043b06504ce
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="defining-custom-orchestration-service-execution-using-itineraries"></a><span data-ttu-id="78c02-102">定義自訂協調流程服務執行，使用行程</span><span class="sxs-lookup"><span data-stu-id="78c02-102">Defining Custom Orchestration Service Execution Using Itineraries</span></span>
<span data-ttu-id="78c02-103">在此使用案例，提交進行處理的訊息會包含路線的 SOAP 標頭描述要執行的服務和其解析需求的清單。</span><span class="sxs-lookup"><span data-stu-id="78c02-103">In this use case, a message submitted for processing contains an itinerary SOAP header that describes the list of services to execute and their resolution requirements.</span></span> <span data-ttu-id="78c02-104">路線指定一個或多個自訂協調流程處理序訊息將會用來傳遞處理週期。</span><span class="sxs-lookup"><span data-stu-id="78c02-104">The itinerary specifies one or more custom orchestrations or processes through which the message will pass during the processing cycle.</span></span> <span data-ttu-id="78c02-105">自訂協調流程具有路線和其他訊息內容中公開的自訂屬性的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="78c02-105">Custom orchestrations have full control of the itinerary and other custom properties exposed in the message context.</span></span> <span data-ttu-id="78c02-106">（選擇性） 路線可以包含動態解析資訊會決定轉換需求和端點的訊息。</span><span class="sxs-lookup"><span data-stu-id="78c02-106">Optionally, the itinerary can contain dynamic resolution information that determines transformation requirements and endpoints for the message.</span></span> <span data-ttu-id="78c02-107">圖 1 所示處理程序的圖解的檢視。</span><span class="sxs-lookup"><span data-stu-id="78c02-107">Figure 1 illustrates a schematic view of the process.</span></span>  
  
 <span data-ttu-id="78c02-108">![定義自訂協調流程](../esb-toolkit/media/ch3-definingcustomorchestration.gif "Ch3 DefiningCustomOrchestration")</span><span class="sxs-lookup"><span data-stu-id="78c02-108">![Defining Custom Orchestration](../esb-toolkit/media/ch3-definingcustomorchestration.gif "Ch3-DefiningCustomOrchestration")</span></span>  
  
 <span data-ttu-id="78c02-109">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="78c02-109">**Figure 1**</span></span>  
  
 <span data-ttu-id="78c02-110">**定義自訂協調流程服務執行，使用行程**</span><span class="sxs-lookup"><span data-stu-id="78c02-110">**Defining custom orchestration service execution using itineraries**</span></span>  
  
 <span data-ttu-id="78c02-111">隨附的行程上手範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="78c02-111">The Itinerary On-Ramp sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="78c02-112">它會顯示如何建立包含一系列的路線定義 ESB 和 BizTalk Server 如何處理輸入的訊息的步驟解析、 路由及服務引動過程指示的行程。</span><span class="sxs-lookup"><span data-stu-id="78c02-112">It shows how to create itineraries that contain resolution, routing, and service invocation instructions as a series of itinerary steps that define how the ESB and BizTalk Server will process the input message.</span></span> <span data-ttu-id="78c02-113">單向和要求-回應 」 範例隨附。</span><span class="sxs-lookup"><span data-stu-id="78c02-113">One-way and request-response samples are included.</span></span>  
  
 <span data-ttu-id="78c02-114">如需詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="78c02-114">For more information, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span></span>