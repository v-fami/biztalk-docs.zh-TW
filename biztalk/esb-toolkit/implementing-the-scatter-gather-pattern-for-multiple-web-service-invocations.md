---
title: "分散-集中模式實作多個 Web 服務引動過程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 912512a4-9649-40df-bb82-b8f4b85c8ca6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2682418922c17fd4c6fbe8a6bffbac51051f7841
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="implementing-the-scatter-gather-pattern-for-multiple-web-service-invocations"></a><span data-ttu-id="8d523-102">分散-集中模式實作多個 Web 服務引動過程</span><span class="sxs-lookup"><span data-stu-id="8d523-102">Implementing the Scatter-Gather Pattern for Multiple Web Service Invocations</span></span>
<span data-ttu-id="8d523-103">在此使用案例中，訊息會包含指定多個 BizTalk Server 應該存取的外部服務路線服務步驟。</span><span class="sxs-lookup"><span data-stu-id="8d523-103">In this use case, a message contains an itinerary service step that specifies more than one external service that BizTalk Server should access.</span></span> <span data-ttu-id="8d523-104">它使用動態解析來判斷服務位置並傳回的資料轉換對應的端點和任何選用的 BizTalk 服務。</span><span class="sxs-lookup"><span data-stu-id="8d523-104">It uses dynamic resolution to determine service locations and endpoints and any optional BizTalk Service maps for transforming the returned data.</span></span> <span data-ttu-id="8d523-105">此服務的協調流程會執行轉換和引動過程，和所有服務引動過程會以非同步方式都發生。</span><span class="sxs-lookup"><span data-stu-id="8d523-105">The orchestration implementing this service performs the transformation and invocations, and all service invocations occur asynchronously.</span></span> <span data-ttu-id="8d523-106">所有服務引動過程都完成之後，路線服務彙總成單一的回應訊息的回應，並將訊息傳送至用戶端透過動態指派的端點。</span><span class="sxs-lookup"><span data-stu-id="8d523-106">After all service invocations complete, the itinerary service aggregates the responses into a single response message and sends the message to the client through a dynamically assigned endpoint.</span></span> <span data-ttu-id="8d523-107">圖 1 說明此使用案例。</span><span class="sxs-lookup"><span data-stu-id="8d523-107">Figure 1 illustrates this use case.</span></span>  
  
 <span data-ttu-id="8d523-108">![實作散佈收集模式](../esb-toolkit/media/ch3-implementingscatter.gif "Ch3 ImplementingScatter")</span><span class="sxs-lookup"><span data-stu-id="8d523-108">![Implementing Scatter Gather Pattern](../esb-toolkit/media/ch3-implementingscatter.gif "Ch3-ImplementingScatter")</span></span>  
  
 <span data-ttu-id="8d523-109">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="8d523-109">**Figure 1**</span></span>  
  
 <span data-ttu-id="8d523-110">**實作多個 Web 服務引動過程的分散-集中模式**</span><span class="sxs-lookup"><span data-stu-id="8d523-110">**Implementing the Scatter-Gather pattern for multiple Web service invocations**</span></span>  
  
 <span data-ttu-id="8d523-111">分散-集中範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="8d523-111">The Scatter-Gather sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span>  
  
 <span data-ttu-id="8d523-112">如需詳細資訊，請參閱[安裝及執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="8d523-112">For more information, see [Installing and Running the Scatter-Gather Sample](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md).</span></span>