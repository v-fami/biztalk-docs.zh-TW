---
title: 何謂 WCF-WSHttp 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-WSHttp adapters, about WCF-WSHttp adapters
ms.assetid: 183a19e3-10b1-403f-b274-34a441e774d1
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb5d244dcfe26cf10bc4ae10c63374eef0824444
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-wshttp-adapter"></a><span data-ttu-id="af7fc-103">何謂 WCF-WSHttp 配接器？</span><span class="sxs-lookup"><span data-stu-id="af7fc-103">What Is the WCF-WSHttp Adapter?</span></span>
<span data-ttu-id="af7fc-104">您可以使用 WCF-WSHttp 配接器，利用具有文字或 Message Transmission Optimization Mechanism (MTOM) 編碼的 HTTP 或 HTTPS 傳輸，與能夠瞭解下一代 Web 服務標準的服務和用戶端進行跨電腦的通訊。</span><span class="sxs-lookup"><span data-stu-id="af7fc-104">You can use the WCF-WSHttp adapter to do cross-computer communication with services and clients that can understand the next-generation Web service standards, using either the HTTP or HTTPS transport with text or Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="af7fc-105">WCF-WSHttp 配接器可完整存取 SOAP 安全性、可靠性和交易等功能。</span><span class="sxs-lookup"><span data-stu-id="af7fc-105">The WCF-WSHttp adapter provides full access to the SOAP security, reliability, and transaction features.</span></span>  
  
 <span data-ttu-id="af7fc-106">下表摘要說明 WCF-WSHttp 配接器的特性。</span><span class="sxs-lookup"><span data-stu-id="af7fc-106">The following table summarizes the characteristics of the WCF-WSHttp adapter.</span></span>  
  
|<span data-ttu-id="af7fc-107">Description</span><span class="sxs-lookup"><span data-stu-id="af7fc-107">Description</span></span>|<span data-ttu-id="af7fc-108">特性</span><span class="sxs-lookup"><span data-stu-id="af7fc-108">Characteristic</span></span>|  
|-----------------|--------------------|  
|<span data-ttu-id="af7fc-109">互通性等級</span><span class="sxs-lookup"><span data-stu-id="af7fc-109">Interoperability level</span></span>|<span data-ttu-id="af7fc-110">WS-Profile</span><span class="sxs-lookup"><span data-stu-id="af7fc-110">WS-Profile</span></span>|  
|<span data-ttu-id="af7fc-111">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="af7fc-111">Message encoding</span></span>|<span data-ttu-id="af7fc-112">文字或 MTOM</span><span class="sxs-lookup"><span data-stu-id="af7fc-112">Text or MTOM</span></span>|  
|<span data-ttu-id="af7fc-113">界限</span><span class="sxs-lookup"><span data-stu-id="af7fc-113">Boundary</span></span>|<span data-ttu-id="af7fc-114">跨電腦</span><span class="sxs-lookup"><span data-stu-id="af7fc-114">Cross-computer</span></span>|  
|<span data-ttu-id="af7fc-115">傳輸通訊協定</span><span class="sxs-lookup"><span data-stu-id="af7fc-115">Transport protocol</span></span>|<span data-ttu-id="af7fc-116">HTTP 或 HTTPS</span><span class="sxs-lookup"><span data-stu-id="af7fc-116">HTTP or HTTPS</span></span>|  
|<span data-ttu-id="af7fc-117">安全性模式</span><span class="sxs-lookup"><span data-stu-id="af7fc-117">Security mode</span></span>|<span data-ttu-id="af7fc-118">無 (None)、訊息 (Message)、傳輸 (Transport ) 和 TransportWithMessageCredential。</span><span class="sxs-lookup"><span data-stu-id="af7fc-118">None, Message, Transport, and TransportWithMessageCredential.</span></span>|  
|<span data-ttu-id="af7fc-119">用戶端驗證機制</span><span class="sxs-lookup"><span data-stu-id="af7fc-119">Client authentication mechanism</span></span>|<span data-ttu-id="af7fc-120">傳輸安全性與訊息安全性</span><span class="sxs-lookup"><span data-stu-id="af7fc-120">Transport Security and Message Security</span></span>|  
|<span data-ttu-id="af7fc-121">支援 WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="af7fc-121">Support for WS-ReliableMessaging</span></span>|<span data-ttu-id="af7fc-122">否</span><span class="sxs-lookup"><span data-stu-id="af7fc-122">No</span></span>|  
|<span data-ttu-id="af7fc-123">支援 WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="af7fc-123">Support for WS-AtomicTransaction</span></span>|<span data-ttu-id="af7fc-124">是</span><span class="sxs-lookup"><span data-stu-id="af7fc-124">Yes</span></span>|  
|<span data-ttu-id="af7fc-125">支援單向傳訊</span><span class="sxs-lookup"><span data-stu-id="af7fc-125">Support for one-way messaging</span></span>|<span data-ttu-id="af7fc-126">是</span><span class="sxs-lookup"><span data-stu-id="af7fc-126">Yes</span></span>|  
|<span data-ttu-id="af7fc-127">支援雙向傳訊</span><span class="sxs-lookup"><span data-stu-id="af7fc-127">Support for two-way messaging</span></span>|<span data-ttu-id="af7fc-128">是</span><span class="sxs-lookup"><span data-stu-id="af7fc-128">Yes</span></span>|  
|<span data-ttu-id="af7fc-129">接收配接器的主控件類型</span><span class="sxs-lookup"><span data-stu-id="af7fc-129">Host type for receive adapter</span></span>|<span data-ttu-id="af7fc-130">外掛式</span><span class="sxs-lookup"><span data-stu-id="af7fc-130">Isolated</span></span>|  
|<span data-ttu-id="af7fc-131">傳送配接器的主控件類型</span><span class="sxs-lookup"><span data-stu-id="af7fc-131">Host type for send adapter</span></span>|<span data-ttu-id="af7fc-132">內含式</span><span class="sxs-lookup"><span data-stu-id="af7fc-132">In-process</span></span>|  
  
 <span data-ttu-id="af7fc-133">WCF-WSHttp 配接器是由兩個配接器所組成：接收配接器和傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="af7fc-133">The WCF-WSHttp adapter consists of two adapters—a receive adapter and a send adapter.</span></span>  
  
 <span data-ttu-id="af7fc-134">**Wcf-wshttp 接收配接器**</span><span class="sxs-lookup"><span data-stu-id="af7fc-134">**WCF-WSHttp Receive Adapter**</span></span>  
  
 <span data-ttu-id="af7fc-135">您可以使用 WCF-WSHttp 接收配接器，透過 HTTP 或 HTTPS 通訊協定接收 WCF 服務要求。</span><span class="sxs-lookup"><span data-stu-id="af7fc-135">You use the WCF-WSHttp receive adapter to receive WCF service requests through the HTTP or HTTPS protocol.</span></span> <span data-ttu-id="af7fc-136">使用 WCF-WSHttp 接收配接器的接收位置可以設定為單向或要求-回應 (雙向)。</span><span class="sxs-lookup"><span data-stu-id="af7fc-136">A receive location that uses the WCF-WSHttp receive adapter can be configured as one-way or request-response (two-way).</span></span>  
  
 <span data-ttu-id="af7fc-137">**Wcf-wshttp 傳送配接器**</span><span class="sxs-lookup"><span data-stu-id="af7fc-137">**WCF-WSHttp Send Adapter**</span></span>  
  
 <span data-ttu-id="af7fc-138">您可以使用 WCF-WSHttp 傳送配接器，利用 HTTP 或 HTTPS 通訊協定，透過無類型合約來呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="af7fc-138">You use the WCF-WSHttp send adapter to call a WCF service through the typeless contract by using the HTTP or HTTPS protocol.</span></span>  
  
 <span data-ttu-id="af7fc-139">如需有關 WCF 接收和傳送配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="af7fc-139">For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af7fc-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af7fc-140">See Also</span></span>  
 <span data-ttu-id="af7fc-141">[設定 Wcf-wshttp 配接器](../core/configuring-the-wcf-wshttp-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="af7fc-141">[Configuring the WCF-WSHttp Adapter](../core/configuring-the-wcf-wshttp-adapter.md) </span></span>  
 [<span data-ttu-id="af7fc-142">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="af7fc-142">WCF Adapters</span></span>](../core/wcf-adapters.md)