---
title: 何謂 WCF-NetTcp 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetTcp adapters, about WCF-NetTcp adapters
ms.assetid: 94dc24df-19a1-4701-9012-59d05b0c8abd
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a741d3a4d7b7bcc80405d0fc25e37a31860523b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289406"
---
# <a name="what-is-the-wcf-nettcp-adapter"></a><span data-ttu-id="fd9fd-103">何謂 WCF-NetTcp 配接器？</span><span class="sxs-lookup"><span data-stu-id="fd9fd-103">What Is the WCF-NetTcp Adapter?</span></span>
<span data-ttu-id="fd9fd-104">WCF-NetTcp 配接器可在服務與用戶端皆為 WCF 架構的環境中，提供連線的跨電腦或跨處理序通訊。</span><span class="sxs-lookup"><span data-stu-id="fd9fd-104">The WCF-NetTcp adapter provides connected cross-computer or cross-process communication in an environment in which both services and clients are WCF based.</span></span> <span data-ttu-id="fd9fd-105">該配接器可完整存取 SOAP 安全性、可靠性和交易功能。</span><span class="sxs-lookup"><span data-stu-id="fd9fd-105">It provides full access to SOAP security, reliability, and transaction features.</span></span> <span data-ttu-id="fd9fd-106">此配接器使用 TCP 傳輸，而且訊息具有二進位編碼。</span><span class="sxs-lookup"><span data-stu-id="fd9fd-106">This adapter uses the TCP transport, and messages have binary encoding.</span></span>  
  
 <span data-ttu-id="fd9fd-107">下表摘要描述 WCF-NetTcp 配接器的特性。</span><span class="sxs-lookup"><span data-stu-id="fd9fd-107">The following table summarizes the characteristics of the WCF-NetTcp adapter.</span></span>  
  
|<span data-ttu-id="fd9fd-108">Description</span><span class="sxs-lookup"><span data-stu-id="fd9fd-108">Description</span></span>|<span data-ttu-id="fd9fd-109">特性</span><span class="sxs-lookup"><span data-stu-id="fd9fd-109">Characteristic</span></span>|  
|-----------------|--------------------|  
|<span data-ttu-id="fd9fd-110">互通性等級</span><span class="sxs-lookup"><span data-stu-id="fd9fd-110">Interoperability level</span></span>|<span data-ttu-id="fd9fd-111">.NET 設定檔</span><span class="sxs-lookup"><span data-stu-id="fd9fd-111">.NET-Profile</span></span>|  
|<span data-ttu-id="fd9fd-112">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="fd9fd-112">Message encoding</span></span>|<span data-ttu-id="fd9fd-113">二進位</span><span class="sxs-lookup"><span data-stu-id="fd9fd-113">Binary</span></span>|  
|<span data-ttu-id="fd9fd-114">界限</span><span class="sxs-lookup"><span data-stu-id="fd9fd-114">Boundary</span></span>|<span data-ttu-id="fd9fd-115">跨電腦或跨處理序</span><span class="sxs-lookup"><span data-stu-id="fd9fd-115">Cross-computer or cross-process</span></span>|  
|<span data-ttu-id="fd9fd-116">傳輸通訊協定</span><span class="sxs-lookup"><span data-stu-id="fd9fd-116">Transport protocol</span></span>|<span data-ttu-id="fd9fd-117">TCP</span><span class="sxs-lookup"><span data-stu-id="fd9fd-117">TCP</span></span>|  
|<span data-ttu-id="fd9fd-118">安全性模式</span><span class="sxs-lookup"><span data-stu-id="fd9fd-118">Security mode</span></span>|<span data-ttu-id="fd9fd-119">無 (None)、訊息 (Message)、傳輸 (Transport ) 和 TransportWithMessageCredential。</span><span class="sxs-lookup"><span data-stu-id="fd9fd-119">None, Message, Transport, and TransportWithMessageCredential.</span></span>|  
|<span data-ttu-id="fd9fd-120">用戶端驗證機制</span><span class="sxs-lookup"><span data-stu-id="fd9fd-120">Client authentication mechanism</span></span>|<span data-ttu-id="fd9fd-121">傳輸安全性與訊息安全性</span><span class="sxs-lookup"><span data-stu-id="fd9fd-121">Transport Security and Message Security</span></span>|  
|<span data-ttu-id="fd9fd-122">支援 WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="fd9fd-122">Support for WS-ReliableMessaging</span></span>|<span data-ttu-id="fd9fd-123">否</span><span class="sxs-lookup"><span data-stu-id="fd9fd-123">No</span></span>|  
|<span data-ttu-id="fd9fd-124">支援 WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="fd9fd-124">Support for WS-AtomicTransaction</span></span>|<span data-ttu-id="fd9fd-125">是</span><span class="sxs-lookup"><span data-stu-id="fd9fd-125">Yes</span></span>|  
|<span data-ttu-id="fd9fd-126">支援單向傳訊</span><span class="sxs-lookup"><span data-stu-id="fd9fd-126">Support for one-way messaging</span></span>|<span data-ttu-id="fd9fd-127">是</span><span class="sxs-lookup"><span data-stu-id="fd9fd-127">Yes</span></span>|  
|<span data-ttu-id="fd9fd-128">支援雙向傳訊</span><span class="sxs-lookup"><span data-stu-id="fd9fd-128">Support for two-way messaging</span></span>|<span data-ttu-id="fd9fd-129">是</span><span class="sxs-lookup"><span data-stu-id="fd9fd-129">Yes</span></span>|  
|<span data-ttu-id="fd9fd-130">接收配接器的主控件類型</span><span class="sxs-lookup"><span data-stu-id="fd9fd-130">Host type for receive adapter</span></span>|<span data-ttu-id="fd9fd-131">內含式</span><span class="sxs-lookup"><span data-stu-id="fd9fd-131">In-process</span></span>|  
|<span data-ttu-id="fd9fd-132">傳送配接器的主控件類型</span><span class="sxs-lookup"><span data-stu-id="fd9fd-132">Host type for send adapter</span></span>|<span data-ttu-id="fd9fd-133">內含式</span><span class="sxs-lookup"><span data-stu-id="fd9fd-133">In-process</span></span>|  
  
 <span data-ttu-id="fd9fd-134">WCF-NetTcp 配接器包含兩種配接器，也就是接收配接器和傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="fd9fd-134">The WCF-NetTcp adapter consists of two adapters—a receive adapter and a send adapter.</span></span>  
  
 <span data-ttu-id="fd9fd-135">**Wcf-nettcp 接收配接器**</span><span class="sxs-lookup"><span data-stu-id="fd9fd-135">**WCF-NetTcp Receive Adapter**</span></span>  
  
 <span data-ttu-id="fd9fd-136">使用 WCF-NetTcp 接收配接器透過 TCP 通訊協定接收 WCF 服務要求。</span><span class="sxs-lookup"><span data-stu-id="fd9fd-136">You use the WCF-NetTcp receive adapter to receive WCF service requests through the TCP protocol.</span></span> <span data-ttu-id="fd9fd-137">使用 WCF-NetTcp 接收配接器的接收位置，可以設定為單向或要求-回應 (雙向)。</span><span class="sxs-lookup"><span data-stu-id="fd9fd-137">A receive location that uses the WCF-NetTcp receive adapter can be configured as one-way or request-response (two-way).</span></span>  
  
 <span data-ttu-id="fd9fd-138">**Wcf-nettcp 傳送配接器**</span><span class="sxs-lookup"><span data-stu-id="fd9fd-138">**WCF-NetTcp Send Adapter**</span></span>  
  
 <span data-ttu-id="fd9fd-139">使用 WCF-NetTcp 傳送配接器可使用 TCP 通訊協定，透過無型別合約呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="fd9fd-139">You use the WCF-NetTcp send adapter to call a WCF service through the typeless contract by using the TCP protocol.</span></span>  
  
 <span data-ttu-id="fd9fd-140">如需有關 WCF 接收和傳送配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="fd9fd-140">For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9fd-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd9fd-141">See Also</span></span>  
 <span data-ttu-id="fd9fd-142">[設定 Wcf-nettcp 配接器](../core/configuring-the-wcf-nettcp-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="fd9fd-142">[Configuring the WCF-NetTcp Adapter](../core/configuring-the-wcf-nettcp-adapter.md) </span></span>  
 [<span data-ttu-id="fd9fd-143">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="fd9fd-143">WCF Adapters</span></span>](../core/wcf-adapters.md)