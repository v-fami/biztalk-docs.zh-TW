---
title: 配接器訊息互動的商務交換 |Microsoft 文件
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
ms.openlocfilehash: d19e10940e6a83c24e9397f0df94d0fc54e4da38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224598"
---
# <a name="interact-adapter-messages-for-business-exchange"></a><span data-ttu-id="71f05-102">配接器訊息互動的商務交換</span><span class="sxs-lookup"><span data-stu-id="71f05-102">InterAct Adapter Messages for Business Exchange</span></span>
<span data-ttu-id="71f05-103">InterAct 配接器的端對端循環中有四種訊息。</span><span class="sxs-lookup"><span data-stu-id="71f05-103">There are four messages in the InterAct adapter end-to-end cycle.</span></span> <span data-ttu-id="71f05-104">這些訊息是 SWIFTNet 基本型別。</span><span class="sxs-lookup"><span data-stu-id="71f05-104">These messages are SWIFTNet primitives.</span></span> <span data-ttu-id="71f05-105">第一個和最後一個訊息是由用戶端基本型別、 SwInt:ExchangeRequest 與 SwInt:ExchangeResponse 組成。</span><span class="sxs-lookup"><span data-stu-id="71f05-105">The first and last messages comprise the client-side primitives, SwInt:ExchangeRequest and SwInt:ExchangeResponse.</span></span> <span data-ttu-id="71f05-106">伺服器端基本型別、 SwInt:HandleRequest 與 SwInt:HandleResponse 的各構成中間兩個訊息。</span><span class="sxs-lookup"><span data-stu-id="71f05-106">The middle two messages comprise the server-side primitives, SwInt:HandleRequest and SwInt:HandleResponse.</span></span>  
  
 <span data-ttu-id="71f05-107">此層級的簡化，有六個步驟中的端對端訊息週期：</span><span class="sxs-lookup"><span data-stu-id="71f05-107">At this level of simplification, there are six steps in the end-to-end message cycle:</span></span>  
  
1.  <span data-ttu-id="71f05-108">用戶端應用程式會準備要求訊息。</span><span class="sxs-lookup"><span data-stu-id="71f05-108">The client application prepares the request message.</span></span>  
  
2.  <span data-ttu-id="71f05-109">用戶端應用程式會將要求訊息傳遞至 SWIFTNet。</span><span class="sxs-lookup"><span data-stu-id="71f05-109">The client application passes the request message to SWIFTNet.</span></span>  
  
3.  <span data-ttu-id="71f05-110">SWIFTNet 處理要求訊息，並將它傳送至伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="71f05-110">SWIFTNet processes the request message, and sends it to the server application.</span></span>  
  
4.  <span data-ttu-id="71f05-111">伺服器應用程式從 SWIFTNet 接收要求訊息。</span><span class="sxs-lookup"><span data-stu-id="71f05-111">The server application receives the request message from SWIFTNet.</span></span>  
  
5.  <span data-ttu-id="71f05-112">伺服器應用程式會準備回應訊息。</span><span class="sxs-lookup"><span data-stu-id="71f05-112">The server application prepares the response message.</span></span>  
  
6.  <span data-ttu-id="71f05-113">伺服器應用程式會將回應訊息傳遞至 SWIFTNet。</span><span class="sxs-lookup"><span data-stu-id="71f05-113">The server application passes the response message to SWIFTNet.</span></span>  
  
7.  <span data-ttu-id="71f05-114">SWIFTNet 處理回應訊息，並將它傳送至用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="71f05-114">SWIFTNet processes the response message, and sends it to the client application.</span></span>  
  
8.  <span data-ttu-id="71f05-115">用戶端應用程式從 SWIFTNet 接收回應訊息。</span><span class="sxs-lookup"><span data-stu-id="71f05-115">The client application receives the response message from SWIFTNet.</span></span>  
  
 <span data-ttu-id="71f05-116">下圖顯示 InterAct 訊息交換。</span><span class="sxs-lookup"><span data-stu-id="71f05-116">The following figure shows the InterAct message exchange.</span></span>  
  
 <span data-ttu-id="71f05-117">![InterAct 訊息交換](../../adapters-and-accelerators/fileact-interact/media/12fbebc6-5ab7-4d7f-9f94-4069b22161fa.gif "12fbebc6-5ab7-4d7f-9f94-4069b22161fa")</span><span class="sxs-lookup"><span data-stu-id="71f05-117">![InterAct message exchange](../../adapters-and-accelerators/fileact-interact/media/12fbebc6-5ab7-4d7f-9f94-4069b22161fa.gif "12fbebc6-5ab7-4d7f-9f94-4069b22161fa")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f05-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71f05-118">See Also</span></span>  
 <span data-ttu-id="71f05-119">[互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="71f05-119">[InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="71f05-120">[InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span><span class="sxs-lookup"><span data-stu-id="71f05-120">[InterAct Adapter Components](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span></span>  
 <span data-ttu-id="71f05-121">[InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span><span class="sxs-lookup"><span data-stu-id="71f05-121">[InterAct Adapter Client Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span></span>  
 <span data-ttu-id="71f05-122">[InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span><span class="sxs-lookup"><span data-stu-id="71f05-122">[InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span></span>  
 <span data-ttu-id="71f05-123">[配接器儲存與轉送互動](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="71f05-123">[InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="71f05-124">[互動的配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="71f05-124">[InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="71f05-125">[互動配接器端對端可靠傳遞](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span><span class="sxs-lookup"><span data-stu-id="71f05-125">[InterAct Adapter End-to-End Reliable Delivery](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span></span>  
 <span data-ttu-id="71f05-126">[互動的介面卡狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span><span class="sxs-lookup"><span data-stu-id="71f05-126">[InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span></span>  
 [<span data-ttu-id="71f05-127">互動配接器不可否認性</span><span class="sxs-lookup"><span data-stu-id="71f05-127">InterAct Adapter Non-Repudiation</span></span>](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)