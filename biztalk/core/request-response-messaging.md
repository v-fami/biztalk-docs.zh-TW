---
title: "要求-回應傳訊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- request/response messaging, about request/response messaging
- SOAP adapters, message processing
- SOAP adapters, request/response messaging
- request/response messaging
- patterns, messages
- messages, request/response messaging
- request/response messaging, processing
- request/response messaging, SOAP adapters
- messages, patterns
ms.assetid: 1a2f79b5-1f44-4191-8ce1-b3c9043be4f4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd612d5f41e4648625a2a28398f20ecf74e0a4e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="request-response-messaging"></a><span data-ttu-id="84b1e-102">要求-回應傳訊</span><span class="sxs-lookup"><span data-stu-id="84b1e-102">Request-Response Messaging</span></span>
<span data-ttu-id="84b1e-103">在要求/回應傳訊模式中，一個合作對象會傳送要求訊息，而接收的合作對象則會回傳回應訊息。</span><span class="sxs-lookup"><span data-stu-id="84b1e-103">In a request/response messaging pattern, one party sends a request message and the receiving party returns a response message.</span></span> <span data-ttu-id="84b1e-104">要求/回應處理的兩個典型範例，是瀏覽器與使用 HTTP 配接器的 Web 伺服器之間的互動，以及使用「簡單物件存取通訊協定」(SOAP) 配接器的 Web 服務處理之間的互動。</span><span class="sxs-lookup"><span data-stu-id="84b1e-104">Two typical examples of request/response processing are the interaction that a browser has with a Web server using the HTTP adapter, and Web service processing using the Simple Object Access Protocol (SOAP) adapter.</span></span> <span data-ttu-id="84b1e-105">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，要求與回應訊息都是透過典型的發佈/訂閱方式處理的。</span><span class="sxs-lookup"><span data-stu-id="84b1e-105">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], both the request and the response messages are handled in a typical publish/subscribe fashion.</span></span> <span data-ttu-id="84b1e-106">在您微調 BizTalk 應用程式效能時，這是一個需要瞭解的重要考量，因為對於個別訊息，需要高輸送量的系統與需要低延遲的系統兩者在設定上有所不同。</span><span class="sxs-lookup"><span data-stu-id="84b1e-106">This is an important consideration to understand when you performance-tune a BizTalk application, because a system requiring high throughput might be configured differently than one requiring low latency for individual messages.</span></span>  
  
 <span data-ttu-id="84b1e-107">![要求 &#47;回應傳訊](../core/media/arch-request-response-1.gif "arch_request-回應-1")</span><span class="sxs-lookup"><span data-stu-id="84b1e-107">![Request&#47;Response messaging](../core/media/arch-request-response-1.gif "arch_request-response-1")</span></span>  
  
 <span data-ttu-id="84b1e-108">要求/回應模式的接收配接器收到訊息時，BizTalk Server 會先發佈要求訊息到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="84b1e-108">When a message is received by a request/response style receive adapter, BizTalk Server first publishes the request message to the MessageBox database.</span></span> <span data-ttu-id="84b1e-109">接著，適當的訂閱者會收到此訊息，該訂閱者可能是與接收埠繫結的協調流程。</span><span class="sxs-lookup"><span data-stu-id="84b1e-109">Next this message is received by the appropriate subscriber, which is likely an orchestration bound to a receive port.</span></span> <span data-ttu-id="84b1e-110">此訂閱者會編寫回應訊息，連同屬性發佈到 MessageBox，這個屬性可讓訊息傳回到送來要求的接收埠。</span><span class="sxs-lookup"><span data-stu-id="84b1e-110">This subscriber formulates a response message and publishes it to the MessageBox, along with properties that cause it to be sent back to the receive port from which the request came.</span></span> <span data-ttu-id="84b1e-111">最後，要求的發佈者 (即提交要求的接收配接器) 會拾取回應訊息，並將此訊息傳回到呼叫應用程式。</span><span class="sxs-lookup"><span data-stu-id="84b1e-111">Finally, the response message is picked up by the publisher of the request, the receive adapter that submitted the request, and is returned to the calling application.</span></span> <span data-ttu-id="84b1e-112">下圖提供這些步驟的詳細圖解。</span><span class="sxs-lookup"><span data-stu-id="84b1e-112">The diagram below provides a detailed graphical representation of these steps.</span></span>  
  
 <span data-ttu-id="84b1e-113">![要求 &#47; SOAP 配接器接收的回應訊息](../core/media/arch-request-response-2.gif "arch_request-回應-2")</span><span class="sxs-lookup"><span data-stu-id="84b1e-113">![Request&#47;response message received by SOAP adapter](../core/media/arch-request-response-2.gif "arch_request-response-2")</span></span>  
  
 <span data-ttu-id="84b1e-114">**SOAP 配接器接收的要求/回應訊息的流程**</span><span class="sxs-lookup"><span data-stu-id="84b1e-114">**Flow of request/response message received by SOAP adapter**</span></span>  
  
1.  <span data-ttu-id="84b1e-115">SOAP 配接器提交訊息到結束點管理員。</span><span class="sxs-lookup"><span data-stu-id="84b1e-115">The SOAP adapter submits messages to the Endpoint Manager.</span></span>  
  
2.  <span data-ttu-id="84b1e-116">結束點管理員將訊息發佈到 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="84b1e-116">The Endpoint Manager publishes the message into the MessageBox.</span></span>  
  
3.  <span data-ttu-id="84b1e-117">與接收埠繫結而因此訂閱訊息的協調流程，會接收訊息並進行處理。</span><span class="sxs-lookup"><span data-stu-id="84b1e-117">The orchestration, which is bound to the receive port and therefore has a subscription for the message, receives the message and processes it.</span></span>  
  
4.  <span data-ttu-id="84b1e-118">協調流程傳送發佈到 MessageBox 的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="84b1e-118">The orchestration sends a response message that is published to the MessageBox.</span></span>  
  
5.  <span data-ttu-id="84b1e-119">結束點管理員接收回應訊息。</span><span class="sxs-lookup"><span data-stu-id="84b1e-119">The Endpoint Manager receives the response message.</span></span>  
  
6.  <span data-ttu-id="84b1e-120">結束點管理員將回應傳回到 SOAP 配接器</span><span class="sxs-lookup"><span data-stu-id="84b1e-120">The Endpoint Manager returns the response to the SOAP adapter</span></span>  
  
 <span data-ttu-id="84b1e-121">如果不瞭解內部實作方式，可能會忽略這類行為對效能的影響。</span><span class="sxs-lookup"><span data-stu-id="84b1e-121">The implications of this type of behavior on performance can be overlooked if the internal implementation is not understood.</span></span> <span data-ttu-id="84b1e-122">BizTalk Server 最初是針對高輸送量進行微調，但是它也可以設定給具有較低輸送量且較低延遲的環境使用，特別是要求/回應實例中。</span><span class="sxs-lookup"><span data-stu-id="84b1e-122">BizTalk Server is initially tuned for high throughput scenarios, but it can also be configured for an environment with lower throughput and a need for lower latency, especially in request/response scenarios.</span></span> <span data-ttu-id="84b1e-123">在此實例中的微調需要考量幾項因素。</span><span class="sxs-lookup"><span data-stu-id="84b1e-123">You need to consider several components for tuning in this scenario.</span></span> <span data-ttu-id="84b1e-124">首先，訂閱者是透過輪詢機制發現有發佈的訊息。</span><span class="sxs-lookup"><span data-stu-id="84b1e-124">First, subscribers find out about published messages through a polling mechanism.</span></span> <span data-ttu-id="84b1e-125">若是輪詢間隔設定得太長，可能會造成要求/回應模式的互動延遲比預期還要大。</span><span class="sxs-lookup"><span data-stu-id="84b1e-125">If the polling interval is set too high, this could cause request/response style interactions to have a higher latency than you would want.</span></span>  
  
 <span data-ttu-id="84b1e-126">請注意，在此實例中需要滿足兩個訂閱：初始訊息的訂閱以及回應訊息的訂閱，而這樣會增加對此輪詢間隔的影響。</span><span class="sxs-lookup"><span data-stu-id="84b1e-126">Note that in this scenario, there are two subscriptions to be filled: the subscription for the initial message, as well as the one for the response message, and this increases the impact of this polling interval.</span></span> <span data-ttu-id="84b1e-127">第二，接收配接器的設定是以不同大小的批次方式將訊息插入到 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="84b1e-127">Second, receive adapters are configured to insert messages into the MessageBox in batches of varying sizes.</span></span> <span data-ttu-id="84b1e-128">大部分的配接器可讓您透過一般配接器組態介面或是 BizTalk Server 或登錄中的參數來設定批次大小。</span><span class="sxs-lookup"><span data-stu-id="84b1e-128">Most adapters enable you to configure the batch size through the typical adapter configuration interface or through parameters in BizTalk Server or the registry.</span></span> <span data-ttu-id="84b1e-129">若是批次大小設定得太大，可能會增加個別訊息的延遲。</span><span class="sxs-lookup"><span data-stu-id="84b1e-129">If the batch size is set too high, the latency for individual messages may be increased.</span></span> <span data-ttu-id="84b1e-130">如需有關的效能特性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[規劃維持效能](../core/planning-for-sustained-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="84b1e-130">For more information about the performance characteristics of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Planning for Sustained Performance](../core/planning-for-sustained-performance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b1e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84b1e-131">See Also</span></span>  
 [<span data-ttu-id="84b1e-132">執行階段架構</span><span class="sxs-lookup"><span data-stu-id="84b1e-132">Runtime Architecture</span></span>](../core/runtime-architecture.md)