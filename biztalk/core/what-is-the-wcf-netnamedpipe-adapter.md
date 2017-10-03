---
title: "何謂 WCF-NetNamedPipe 配接器？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF-NetNamedPipe adapters, about WCF-NetNamedPipe adapters
ms.assetid: b9f84256-e49d-4ee2-b0fa-d3f692ade1d4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43c73a670139690c4a27d4784c6ad23225492f17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-netnamedpipe-adapter"></a><span data-ttu-id="ae804-103">何謂 WCF-NetNamedPipe 配接器？</span><span class="sxs-lookup"><span data-stu-id="ae804-103">What Is the WCF-NetNamedPipe Adapter?</span></span>
<span data-ttu-id="ae804-104">WCF-NetNamedPipe 配接器可在服務與用戶端皆為 WCF 架構的環境中，提供相同電腦上的跨處理序通訊。</span><span class="sxs-lookup"><span data-stu-id="ae804-104">The WCF-NetNamedPipe adapter provides cross-process communication on the same computer in an environment in which both services and clients are WCF based.</span></span> <span data-ttu-id="ae804-105">它可以完整存取 SOAP 可靠性和交易功能。</span><span class="sxs-lookup"><span data-stu-id="ae804-105">It provides full access to SOAP reliability and transaction features.</span></span> <span data-ttu-id="ae804-106">這個配接器會使用具名管道傳輸，而且訊息具有二進位編碼。</span><span class="sxs-lookup"><span data-stu-id="ae804-106">The adapter uses the named pipe transport, and messages have binary encoding.</span></span> <span data-ttu-id="ae804-107">不過，此配接器無法用於跨電腦的通訊。</span><span class="sxs-lookup"><span data-stu-id="ae804-107">This adapter cannot be used in cross-computer communication.</span></span>  
  
 <span data-ttu-id="ae804-108">下表摘要說明 WCF-NetNamedPipe 配接器的特性。</span><span class="sxs-lookup"><span data-stu-id="ae804-108">The following table summarizes the characteristics for the WCF-NetNamedPipe adapter.</span></span>  
  
|<span data-ttu-id="ae804-109">Description</span><span class="sxs-lookup"><span data-stu-id="ae804-109">Description</span></span>|<span data-ttu-id="ae804-110">特性</span><span class="sxs-lookup"><span data-stu-id="ae804-110">Characteristic</span></span>|  
|-----------------|--------------------|  
|<span data-ttu-id="ae804-111">互通性等級</span><span class="sxs-lookup"><span data-stu-id="ae804-111">Interoperability level</span></span>|<span data-ttu-id="ae804-112">.NET 設定檔</span><span class="sxs-lookup"><span data-stu-id="ae804-112">.NET-Profile</span></span>|  
|<span data-ttu-id="ae804-113">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="ae804-113">Message encoding</span></span>|<span data-ttu-id="ae804-114">二進位</span><span class="sxs-lookup"><span data-stu-id="ae804-114">Binary</span></span>|  
|<span data-ttu-id="ae804-115">界限</span><span class="sxs-lookup"><span data-stu-id="ae804-115">Boundary</span></span>|<span data-ttu-id="ae804-116">跨處理序</span><span class="sxs-lookup"><span data-stu-id="ae804-116">Cross-process</span></span>|  
|<span data-ttu-id="ae804-117">傳輸通訊協定</span><span class="sxs-lookup"><span data-stu-id="ae804-117">Transport protocol</span></span>|<span data-ttu-id="ae804-118">具名管道</span><span class="sxs-lookup"><span data-stu-id="ae804-118">Named pipe</span></span>|  
|<span data-ttu-id="ae804-119">安全性模式</span><span class="sxs-lookup"><span data-stu-id="ae804-119">Security mode</span></span>|<span data-ttu-id="ae804-120">「無」與「傳輸」</span><span class="sxs-lookup"><span data-stu-id="ae804-120">None and Transport</span></span>|  
|<span data-ttu-id="ae804-121">用戶端驗證機制</span><span class="sxs-lookup"><span data-stu-id="ae804-121">Client authentication mechanism</span></span>|<span data-ttu-id="ae804-122">傳輸安全性與訊息安全性</span><span class="sxs-lookup"><span data-stu-id="ae804-122">Transport Security and Message Security</span></span>|  
|<span data-ttu-id="ae804-123">支援 WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="ae804-123">Support for WS-ReliableMessaging</span></span>|<span data-ttu-id="ae804-124">否</span><span class="sxs-lookup"><span data-stu-id="ae804-124">No</span></span>|  
|<span data-ttu-id="ae804-125">支援 WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="ae804-125">Support for WS-AtomicTransaction</span></span>|<span data-ttu-id="ae804-126">是</span><span class="sxs-lookup"><span data-stu-id="ae804-126">Yes</span></span>|  
|<span data-ttu-id="ae804-127">支援單向傳訊</span><span class="sxs-lookup"><span data-stu-id="ae804-127">Support for one-way messaging</span></span>|<span data-ttu-id="ae804-128">是</span><span class="sxs-lookup"><span data-stu-id="ae804-128">Yes</span></span>|  
|<span data-ttu-id="ae804-129">支援雙向傳訊</span><span class="sxs-lookup"><span data-stu-id="ae804-129">Support for two-way messaging</span></span>|<span data-ttu-id="ae804-130">是</span><span class="sxs-lookup"><span data-stu-id="ae804-130">Yes</span></span>|  
|<span data-ttu-id="ae804-131">接收配接器的主控件類型</span><span class="sxs-lookup"><span data-stu-id="ae804-131">Host type for receive adapter</span></span>|<span data-ttu-id="ae804-132">內含式</span><span class="sxs-lookup"><span data-stu-id="ae804-132">In-process</span></span>|  
|<span data-ttu-id="ae804-133">傳送配接器的主控件類型</span><span class="sxs-lookup"><span data-stu-id="ae804-133">Host type for send adapter</span></span>|<span data-ttu-id="ae804-134">內含式</span><span class="sxs-lookup"><span data-stu-id="ae804-134">In-process</span></span>|  
  
 <span data-ttu-id="ae804-135">WCF-NetNamedPipe 配接器是由兩個配接器所組成：接收配接器和傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="ae804-135">The WCF-NetNamedPipe adapter consists of two adapters—a receive adapter and a send adapter.</span></span>  
  
 <span data-ttu-id="ae804-136">**Wcf-netnamedpipe 接收配接器**</span><span class="sxs-lookup"><span data-stu-id="ae804-136">**WCF-NetNamedPipe Receive Adapter**</span></span>  
  
 <span data-ttu-id="ae804-137">您可以使用 WCF-NetNamedPipe 接收配接器，透過具名管道傳輸來接收 Web 服務要求。</span><span class="sxs-lookup"><span data-stu-id="ae804-137">You use the WCF-NetNamedPipe receive adapter to receive WCF service requests over the named pipe transport.</span></span> <span data-ttu-id="ae804-138">使用 WCF-NetNamedPipe 接收配接器的接收位置可以設定為單向或要求-回應 (雙向)。</span><span class="sxs-lookup"><span data-stu-id="ae804-138">A receive location that uses the WCF-NetNamedPipe receive adapter can be configured as one-way or request-response (two-way).</span></span>  
  
 <span data-ttu-id="ae804-139">**Wcf-netnamedpipe 傳送配接器**</span><span class="sxs-lookup"><span data-stu-id="ae804-139">**WCF-NetNamedPipe Send Adapter**</span></span>  
  
 <span data-ttu-id="ae804-140">您可以使用 WCF-NetNamedPipe 傳送配接器，透過具名管道傳輸並經由無類型合約來呼叫 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="ae804-140">You use the WCF-NetNamedPipe send adapter to call a WCF service through the typeless contract over the named pipe transport.</span></span>  
  
 <span data-ttu-id="ae804-141">如需有關 WCF 接收和傳送配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="ae804-141">For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae804-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae804-142">See Also</span></span>  
 <span data-ttu-id="ae804-143">[設定 Wcf-netnamedpipe 配接器](../core/configuring-the-wcf-netnamedpipe-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ae804-143">[Configuring the WCF-NetNamedPipe Adapter](../core/configuring-the-wcf-netnamedpipe-adapter.md) </span></span>  
 [<span data-ttu-id="ae804-144">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="ae804-144">WCF Adapters</span></span>](../core/wcf-adapters.md)