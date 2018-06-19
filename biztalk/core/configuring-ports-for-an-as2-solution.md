---
title: 設定 AS2 方案的通訊埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715358b1-4226-476b-b0de-2b91434aa24c
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8f02c5de0edd7956f00e10ce8782e4865033076
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233582"
---
# <a name="configuring-ports-for-an-as2-solution"></a><span data-ttu-id="5e7cc-102">設定 AS2 方案的連接埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-102">Configuring Ports for an AS2 Solution</span></span>
<span data-ttu-id="5e7cc-103">您可以使用下列接收埠和傳送埠，透過 AS2 來傳輸 EDI 訊息和非 EDI 訊息：</span><span class="sxs-lookup"><span data-stu-id="5e7cc-103">You can use the following receive and send ports to transmit EDI and non-EDI messages over AS2:</span></span>  
  
 <span data-ttu-id="5e7cc-104">**接收埠**</span><span class="sxs-lookup"><span data-stu-id="5e7cc-104">**Receive Ports**</span></span>  
  
|<span data-ttu-id="5e7cc-105">負責接收</span><span class="sxs-lookup"><span data-stu-id="5e7cc-105">To Receive</span></span>|<span data-ttu-id="5e7cc-106">負責傳送</span><span class="sxs-lookup"><span data-stu-id="5e7cc-106">To Send</span></span>|<span data-ttu-id="5e7cc-107">連接埠類型</span><span class="sxs-lookup"><span data-stu-id="5e7cc-107">Type of Port</span></span>|  
|----------------|-------------|------------------|  
|<span data-ttu-id="5e7cc-108">EDI 或非 EDI 訊息或是通知</span><span class="sxs-lookup"><span data-stu-id="5e7cc-108">An EDI or non-EDI message or acknowledgment</span></span>|<span data-ttu-id="5e7cc-109">MDN 回應 (若是在同步模式下) 或 HTTP 回應 (若是在非同步模式下)</span><span class="sxs-lookup"><span data-stu-id="5e7cc-109">An MDN response (if in synchronous mode) or an HTTP response (if in asynchronous mode)</span></span>|<span data-ttu-id="5e7cc-110">雙向要求-回應 HTTP 接收埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-110">Two-way request-response HTTP receive port</span></span>|  
|<span data-ttu-id="5e7cc-111">MDN 回應</span><span class="sxs-lookup"><span data-stu-id="5e7cc-111">An MDN response</span></span>|-|<span data-ttu-id="5e7cc-112">單向 HTTP 接收埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-112">One-way HTTP receive port</span></span>|  
  
 <span data-ttu-id="5e7cc-113">**傳送埠**</span><span class="sxs-lookup"><span data-stu-id="5e7cc-113">**Send Ports**</span></span>  
  
|<span data-ttu-id="5e7cc-114">負責傳送</span><span class="sxs-lookup"><span data-stu-id="5e7cc-114">To Send</span></span>|<span data-ttu-id="5e7cc-115">負責接收</span><span class="sxs-lookup"><span data-stu-id="5e7cc-115">To Receive</span></span>|<span data-ttu-id="5e7cc-116">連接埠類型</span><span class="sxs-lookup"><span data-stu-id="5e7cc-116">Type of Port</span></span>|  
|-------------|----------------|------------------|  
|<span data-ttu-id="5e7cc-117">EDI 或非 EDI 訊息或是通知</span><span class="sxs-lookup"><span data-stu-id="5e7cc-117">An EDI or non-EDI message or acknowledgment</span></span><br /><br /> <span data-ttu-id="5e7cc-118">(根據協議決定路由)</span><span class="sxs-lookup"><span data-stu-id="5e7cc-118">(agreement-based routing)</span></span>|-|<span data-ttu-id="5e7cc-119">靜態單向 HTTP 傳送埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-119">Static one-way HTTP send port</span></span>|  
|<span data-ttu-id="5e7cc-120">EDI 或非 EDI 訊息或是通知</span><span class="sxs-lookup"><span data-stu-id="5e7cc-120">An EDI or non-EDI message or acknowledgment</span></span><br /><br /> <span data-ttu-id="5e7cc-121">(根據訊息內容決定路由)</span><span class="sxs-lookup"><span data-stu-id="5e7cc-121">(content-based routing)</span></span>|<span data-ttu-id="5e7cc-122">MDN 回應</span><span class="sxs-lookup"><span data-stu-id="5e7cc-122">An MDN response</span></span>|<span data-ttu-id="5e7cc-123">動態雙向請求-回應 HTTP 傳送埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-123">Dynamic two-way solicit-response HTTP send port</span></span>|  
|<span data-ttu-id="5e7cc-124">EDI 或非 EDI 訊息或是通知</span><span class="sxs-lookup"><span data-stu-id="5e7cc-124">An EDI or non-EDI message or acknowledgment</span></span><br /><br /> <span data-ttu-id="5e7cc-125">(根據訊息內容決定路由)</span><span class="sxs-lookup"><span data-stu-id="5e7cc-125">(content-based routing)</span></span>|-|<span data-ttu-id="5e7cc-126">動態單向 HTTP 傳送埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-126">Dynamic one-way HTTP send port</span></span>|  
|<span data-ttu-id="5e7cc-127">非同步 MDN 回應</span><span class="sxs-lookup"><span data-stu-id="5e7cc-127">An asynchronous MDN response</span></span><br /><br /> <span data-ttu-id="5e7cc-128">(根據訊息內容決定路由)</span><span class="sxs-lookup"><span data-stu-id="5e7cc-128">(content-based routing)</span></span>|-|<span data-ttu-id="5e7cc-129">動態單向傳送埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-129">Dynamic one-way send port</span></span>|  
|<span data-ttu-id="5e7cc-130">非同步 MDN 回應</span><span class="sxs-lookup"><span data-stu-id="5e7cc-130">An asynchronous MDN response</span></span>|-|<span data-ttu-id="5e7cc-131">靜態單向傳送埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-131">Static one-way send port</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="5e7cc-132">本節內容</span><span class="sxs-lookup"><span data-stu-id="5e7cc-132">In This Section</span></span>  
  
-   [<span data-ttu-id="5e7cc-133">設定透過 AS2 接收訊息的連接埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-133">Configuring a Receive Port for Messages over AS2</span></span>](../core/configuring-a-receive-port-for-messages-over-as2.md)  
  
-   [<span data-ttu-id="5e7cc-134">設定內送 Mdn 的接收埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-134">Configuring a Receive Port for Incoming MDNs</span></span>](../core/configuring-a-receive-port-for-incoming-mdns.md)  
  
-   [<span data-ttu-id="5e7cc-135">透過 AS2 的訊息設定靜態傳送埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-135">Configuring a Static Send Port for Messages over AS2</span></span>](../core/configuring-a-static-send-port-for-messages-over-as2.md)  
  
-   [<span data-ttu-id="5e7cc-136">透過 AS2 的訊息設定動態傳送埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-136">Configuring a Dynamic Send Port for Messages over AS2</span></span>](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)  
  
-   [<span data-ttu-id="5e7cc-137">設定透過 AS2 之非同步 Mdn 的靜態傳送埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-137">Configuring a Static Send Port for Asynchronous MDNs over AS2</span></span>](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)  
  
-   [<span data-ttu-id="5e7cc-138">設定透過 AS2 之非同步 Mdn 的動態傳送埠</span><span class="sxs-lookup"><span data-stu-id="5e7cc-138">Configuring a Dynamic Send Port for Asynchronous MDNs over AS2</span></span>](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md)  
  
## <a name="see-also"></a><span data-ttu-id="5e7cc-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e7cc-139">See Also</span></span>  
 [<span data-ttu-id="5e7cc-140">開發和設定 BizTalk Server AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="5e7cc-140">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)