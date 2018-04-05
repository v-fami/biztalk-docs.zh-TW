---
title: 何謂 WCF-NetMsmq 配接器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetMsmq adapters, about WCF-NetMsmq adapters
ms.assetid: 506c5e2d-6cbe-4788-8e37-49d009dc559a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1008cc7178c38532f1781890080eacf4b5dfb56c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-netmsmq-adapter"></a><span data-ttu-id="563e4-103">何謂 WCF-NetMsmq 配接器？</span><span class="sxs-lookup"><span data-stu-id="563e4-103">What Is the WCF-NetMsmq Adapter?</span></span>
<span data-ttu-id="563e4-104">WCF-NetMsmq 配接器可在服務與用戶端皆為 WCF 架構的環境中，使用佇列技術提供離線的跨電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="563e4-104">The WCF-NetMsmq adapter provides disconnected cross-computer communication by using queuing technology in an environment where both the services and clients are WCF based.</span></span> <span data-ttu-id="563e4-105">它會使用「訊息佇列」(MSMQ) 傳輸，而且訊息具有二進位編碼。</span><span class="sxs-lookup"><span data-stu-id="563e4-105">It uses the Message Queuing (MSMQ) transport, and messages have binary encoding.</span></span>  
  
 <span data-ttu-id="563e4-106">下表摘要說明 WCF-NetMsmq 配接器的特性。</span><span class="sxs-lookup"><span data-stu-id="563e4-106">The following table summarizes the characteristics for the WCF-NetMsmq adapter.</span></span>  
  
|<span data-ttu-id="563e4-107">Description</span><span class="sxs-lookup"><span data-stu-id="563e4-107">Description</span></span>|<span data-ttu-id="563e4-108">特性</span><span class="sxs-lookup"><span data-stu-id="563e4-108">Characteristic</span></span>|  
|-----------------|--------------------|  
|<span data-ttu-id="563e4-109">互通性等級</span><span class="sxs-lookup"><span data-stu-id="563e4-109">Interoperability level</span></span>|<span data-ttu-id="563e4-110">.NET 設定檔</span><span class="sxs-lookup"><span data-stu-id="563e4-110">.NET-Profile</span></span>|  
|<span data-ttu-id="563e4-111">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="563e4-111">Message encoding</span></span>|<span data-ttu-id="563e4-112">二進位</span><span class="sxs-lookup"><span data-stu-id="563e4-112">Binary</span></span>|  
|<span data-ttu-id="563e4-113">界限</span><span class="sxs-lookup"><span data-stu-id="563e4-113">Boundary</span></span>|<span data-ttu-id="563e4-114">跨電腦</span><span class="sxs-lookup"><span data-stu-id="563e4-114">Cross-computer</span></span>|  
|<span data-ttu-id="563e4-115">傳輸通訊協定</span><span class="sxs-lookup"><span data-stu-id="563e4-115">Transport protocol</span></span>|<span data-ttu-id="563e4-116">MSMQ</span><span class="sxs-lookup"><span data-stu-id="563e4-116">MSMQ</span></span>|  
|<span data-ttu-id="563e4-117">安全性模式</span><span class="sxs-lookup"><span data-stu-id="563e4-117">Security mode</span></span>|<span data-ttu-id="563e4-118">無、訊息、傳輸和兩者。</span><span class="sxs-lookup"><span data-stu-id="563e4-118">None, Message, Transport, and Both.</span></span>|  
|<span data-ttu-id="563e4-119">用戶端驗證機制</span><span class="sxs-lookup"><span data-stu-id="563e4-119">Client authentication mechanism</span></span>|<span data-ttu-id="563e4-120">傳輸安全性與訊息安全性</span><span class="sxs-lookup"><span data-stu-id="563e4-120">Transport Security and Message Security</span></span>|  
|<span data-ttu-id="563e4-121">支援 WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="563e4-121">Support for WS-ReliableMessaging</span></span>|<span data-ttu-id="563e4-122">不適用</span><span class="sxs-lookup"><span data-stu-id="563e4-122">Not applicable</span></span>|  
|<span data-ttu-id="563e4-123">支援 WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="563e4-123">Support for WS-AtomicTransaction</span></span>|<span data-ttu-id="563e4-124">是</span><span class="sxs-lookup"><span data-stu-id="563e4-124">Yes</span></span>|  
|<span data-ttu-id="563e4-125">支援單向傳訊</span><span class="sxs-lookup"><span data-stu-id="563e4-125">Support for one-way messaging</span></span>|<span data-ttu-id="563e4-126">是</span><span class="sxs-lookup"><span data-stu-id="563e4-126">Yes</span></span>|  
|<span data-ttu-id="563e4-127">支援雙向傳訊</span><span class="sxs-lookup"><span data-stu-id="563e4-127">Support for two-way messaging</span></span>|<span data-ttu-id="563e4-128">否</span><span class="sxs-lookup"><span data-stu-id="563e4-128">No</span></span>|  
|<span data-ttu-id="563e4-129">接收配接器的主控件類型</span><span class="sxs-lookup"><span data-stu-id="563e4-129">Host type for receive adapter</span></span>|<span data-ttu-id="563e4-130">內含式</span><span class="sxs-lookup"><span data-stu-id="563e4-130">In-process</span></span>|  
|<span data-ttu-id="563e4-131">傳送配接器的主控件類型</span><span class="sxs-lookup"><span data-stu-id="563e4-131">Host type for send adapter</span></span>|<span data-ttu-id="563e4-132">內含式</span><span class="sxs-lookup"><span data-stu-id="563e4-132">In-process</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="563e4-133">WCF-NetMsmq 接收配接器提取訊息的來源佇列必須先行建立。</span><span class="sxs-lookup"><span data-stu-id="563e4-133">The queues from which the WCF-NetMsmq receive adapter pulls messages must be created in advance.</span></span> <span data-ttu-id="563e4-134">佇列中的訊息必須是 WCF 架構，否則這些訊息會送至無法傳送的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="563e4-134">The messages in the queues must be WCF based; otherwise, these messages will be sent to the dead-letter queue.</span></span>  
  
 <span data-ttu-id="563e4-135">WCF-NetMsmq 配接器是由兩個配接器所組成：接收配接器和傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="563e4-135">The WCF-NetMsmq adapter consists of two adapters—a receive adapter and a send adapter.</span></span>  
  
 <span data-ttu-id="563e4-136">**Wcf-netmsmq 接收配接器**</span><span class="sxs-lookup"><span data-stu-id="563e4-136">**WCF-NetMsmq Receive Adapter**</span></span>  
  
 <span data-ttu-id="563e4-137">您可以使用 WCF-NetMsmq 接收配接器透過 MSMQ 來接收 WCF 服務要求。</span><span class="sxs-lookup"><span data-stu-id="563e4-137">You use the WCF-NetMsmq receive adapter to receive WCF service requests over MSMQ.</span></span> <span data-ttu-id="563e4-138">使用 WCF-NetMsmq 配接器的接收位置只能設定為單向接收。</span><span class="sxs-lookup"><span data-stu-id="563e4-138">A receive location that uses the WCF-NetMsmq receive adapter can only be configured as one-way receive.</span></span>  
  
 <span data-ttu-id="563e4-139">**Wcf-netmsmq 傳送配接器**</span><span class="sxs-lookup"><span data-stu-id="563e4-139">**WCF-NetMsmq Send Adapter**</span></span>  
  
 <span data-ttu-id="563e4-140">您可以使用 WCF-NetMsmq 傳送配接器，透過 MSMQ 傳輸用無類型合約來呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="563e4-140">You use the WCF-NetMsmq send adapter to call a WCF service through the typeless contract over MSMQ.</span></span>  
  
 <span data-ttu-id="563e4-141">如需有關 WCF 接收和傳送配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="563e4-141">For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563e4-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="563e4-142">See Also</span></span>  
 <span data-ttu-id="563e4-143">[設定 Wcf-netmsmq 配接器](../core/configuring-the-wcf-netmsmq-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="563e4-143">[Configuring the WCF-NetMsmq Adapter](../core/configuring-the-wcf-netmsmq-adapter.md) </span></span>  
 [<span data-ttu-id="563e4-144">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="563e4-144">WCF Adapters</span></span>](../core/wcf-adapters.md)