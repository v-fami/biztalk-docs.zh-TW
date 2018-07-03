---
title: InterAct 配接器訊息進行商務交換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b443b8a-4e56-47f1-8d91-5c807fd54ccc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea8e7d4f4ed8397c88a3cf21280352b446d629c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020150"
---
# <a name="interact-adapter-messages-for-business-exchange"></a><span data-ttu-id="08065-102">商務交換的 interAct 配接器訊息</span><span class="sxs-lookup"><span data-stu-id="08065-102">InterAct Adapter Messages for Business Exchange</span></span>
<span data-ttu-id="08065-103">InterAct 配接器端對端循環中有四個訊息。</span><span class="sxs-lookup"><span data-stu-id="08065-103">There are four messages in the InterAct adapter end-to-end cycle.</span></span> <span data-ttu-id="08065-104">這些訊息是 SWIFTNet 基本型別。</span><span class="sxs-lookup"><span data-stu-id="08065-104">These messages are SWIFTNet primitives.</span></span> <span data-ttu-id="08065-105">第一個和最後一個訊息會包含用戶端的基本項目、 SwInt:ExchangeRequest 和 SwInt:ExchangeResponse。</span><span class="sxs-lookup"><span data-stu-id="08065-105">The first and last messages comprise the client-side primitives, SwInt:ExchangeRequest and SwInt:ExchangeResponse.</span></span> <span data-ttu-id="08065-106">中間的兩個訊息包含的伺服器端基本類型、 SwInt:HandleRequest 和 SwInt:HandleResponse。</span><span class="sxs-lookup"><span data-stu-id="08065-106">The middle two messages comprise the server-side primitives, SwInt:HandleRequest and SwInt:HandleResponse.</span></span>  
  
 <span data-ttu-id="08065-107">在此層級的簡化方式，有六個步驟中的端對端訊息週期：</span><span class="sxs-lookup"><span data-stu-id="08065-107">At this level of simplification, there are six steps in the end-to-end message cycle:</span></span>  
  
1. <span data-ttu-id="08065-108">用戶端應用程式會準備要求訊息。</span><span class="sxs-lookup"><span data-stu-id="08065-108">The client application prepares the request message.</span></span>  
  
2. <span data-ttu-id="08065-109">用戶端應用程式會將要求訊息給 SWIFTNet。</span><span class="sxs-lookup"><span data-stu-id="08065-109">The client application passes the request message to SWIFTNet.</span></span>  
  
3. <span data-ttu-id="08065-110">SWIFTNet 處理要求訊息，並將它傳送至伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="08065-110">SWIFTNet processes the request message, and sends it to the server application.</span></span>  
  
4. <span data-ttu-id="08065-111">伺服器應用程式從 SWIFTNet 接收要求訊息。</span><span class="sxs-lookup"><span data-stu-id="08065-111">The server application receives the request message from SWIFTNet.</span></span>  
  
5. <span data-ttu-id="08065-112">伺服器應用程式會準備回應訊息。</span><span class="sxs-lookup"><span data-stu-id="08065-112">The server application prepares the response message.</span></span>  
  
6. <span data-ttu-id="08065-113">伺服器應用程式會將回應訊息給 SWIFTNet。</span><span class="sxs-lookup"><span data-stu-id="08065-113">The server application passes the response message to SWIFTNet.</span></span>  
  
7. <span data-ttu-id="08065-114">SWIFTNet 處理回應訊息，並將它傳送至用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="08065-114">SWIFTNet processes the response message, and sends it to the client application.</span></span>  
  
8. <span data-ttu-id="08065-115">用戶端應用程式從 SWIFTNet 接收回應訊息。</span><span class="sxs-lookup"><span data-stu-id="08065-115">The client application receives the response message from SWIFTNet.</span></span>  
  
   <span data-ttu-id="08065-116">下圖顯示 InterAct 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="08065-116">The following figure shows the InterAct message exchange.</span></span>  
  
   <span data-ttu-id="08065-117">![InterAct 訊息交換](../../adapters-and-accelerators/fileact-interact/media/12fbebc6-5ab7-4d7f-9f94-4069b22161fa.gif "12fbebc6-5ab7-4d7f-9f94-4069b22161fa")</span><span class="sxs-lookup"><span data-stu-id="08065-117">![InterAct message exchange](../../adapters-and-accelerators/fileact-interact/media/12fbebc6-5ab7-4d7f-9f94-4069b22161fa.gif "12fbebc6-5ab7-4d7f-9f94-4069b22161fa")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08065-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08065-118">See Also</span></span>  
 <span data-ttu-id="08065-119">[InterAct 配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="08065-119">[InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="08065-120">[InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span><span class="sxs-lookup"><span data-stu-id="08065-120">[InterAct Adapter Components](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span></span>  
 <span data-ttu-id="08065-121">[InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span><span class="sxs-lookup"><span data-stu-id="08065-121">[InterAct Adapter Client Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span></span>  
 <span data-ttu-id="08065-122">[InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span><span class="sxs-lookup"><span data-stu-id="08065-122">[InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span></span>  
 <span data-ttu-id="08065-123">[InterAct 配接器儲存和轉寄](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="08065-123">[InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="08065-124">[InterAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="08065-124">[InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="08065-125">[互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span><span class="sxs-lookup"><span data-stu-id="08065-125">[InterAct Adapter End-to-End Reliable Delivery](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span></span>  
 <span data-ttu-id="08065-126">[InterAct 配接器狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span><span class="sxs-lookup"><span data-stu-id="08065-126">[InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span></span>  
 [<span data-ttu-id="08065-127">InterAct 配接器不可否認性</span><span class="sxs-lookup"><span data-stu-id="08065-127">InterAct Adapter Non-Repudiation</span></span>](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)