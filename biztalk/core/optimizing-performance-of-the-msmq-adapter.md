---
title: "最佳化效能，MSMQ 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, performance
- performance, MSMQ adapters
- configuring [MSMQ adapters], performance
ms.assetid: f8537ea8-a96e-4874-bcaf-cd1442a50bd4
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c5624eb6cf88f45d1ecad0b68fee3f5f7b8a8ba
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="optimizing-performance-of-the-msmq-adapter"></a><span data-ttu-id="4bd66-102">最佳化 MSMQ 配接器效能</span><span class="sxs-lookup"><span data-stu-id="4bd66-102">Optimizing Performance of the MSMQ Adapter</span></span>
<span data-ttu-id="4bd66-103">MSMQ 配接器的最佳化在傳送端與接收端之間各有不同。</span><span class="sxs-lookup"><span data-stu-id="4bd66-103">Optimization of the MSMQ adapter differs between the send and receive sides.</span></span> <span data-ttu-id="4bd66-104">您可以藉由設定接收位置上的屬性，來控制接收端上的最佳化。</span><span class="sxs-lookup"><span data-stu-id="4bd66-104">You control optimization on the receive side by setting a property on the receive location.</span></span> <span data-ttu-id="4bd66-105">在傳送端上，您可以使用協調流程來控制最佳化。</span><span class="sxs-lookup"><span data-stu-id="4bd66-105">On the send side, you can control optimization by using an orchestration.</span></span>  
  
## <a name="receive-optimization"></a><span data-ttu-id="4bd66-106">接收最佳化</span><span class="sxs-lookup"><span data-stu-id="4bd66-106">Receive Optimization</span></span>  
 <span data-ttu-id="4bd66-107">在接收端上，您可以讓配接器使用單一執行緒。</span><span class="sxs-lookup"><span data-stu-id="4bd66-107">On the receive side, you can have the adapter use a single execution thread.</span></span> <span data-ttu-id="4bd66-108">配接器是使用單一執行緒或多個執行緒，取決於設定的**排序的處理**屬性上接收位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4bd66-108">Whether the adapter uses a single thread or multiple threads depends on the setting of the **Ordered Processing** property on the receive location, as follows:</span></span>  
  
-   <span data-ttu-id="4bd66-109">若屬性是**True**，配接器會在單一執行緒上運作。</span><span class="sxs-lookup"><span data-stu-id="4bd66-109">When the property is **True**, the adapter operates on a single thread.</span></span> <span data-ttu-id="4bd66-110">這將限制配接器一次只能處理一個訊息並節省記憶體。</span><span class="sxs-lookup"><span data-stu-id="4bd66-110">This limits the adapter to one message at a time and conserves memory.</span></span> <span data-ttu-id="4bd66-111">請注意，這實際上是設定**批次大小**為一 (1)，不論屬性工作表中指派給它的值。</span><span class="sxs-lookup"><span data-stu-id="4bd66-111">Notice that this effectively sets **Batch Size** to one (1), regardless of the value assigned to it in the property sheet.</span></span>  
  
-   <span data-ttu-id="4bd66-112">當**排序的處理**是**False**，配接器執行多個執行緒，並可以處理多個訊息一次，因此可提升效能。</span><span class="sxs-lookup"><span data-stu-id="4bd66-112">When **Ordered Processing** is **False**, the adapter runs multiple threads and can process multiple messages at a time, therefore increasing performance.</span></span>  
  
 <span data-ttu-id="4bd66-113">您必須設定**排序的處理**至**True**如果您將在管理伺服器資源的高階，或訊息大小的數目可能會耗盡可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="4bd66-113">You must set **Ordered Processing** to **True** if you put a premium on managing server resources, or if the number or size of messages might exhaust available memory.</span></span>  
  
 <span data-ttu-id="4bd66-114">您也可以藉由減少的值來控制記憶體使用量**批次大小**接收位置上。</span><span class="sxs-lookup"><span data-stu-id="4bd66-114">You can also control memory use by reducing the value of **Batch Size** on the receive location.</span></span> <span data-ttu-id="4bd66-115">批次大小越小，會在記憶體中保留的訊息就越少，因此會用到的記憶體也會比較少。</span><span class="sxs-lookup"><span data-stu-id="4bd66-115">A smaller batch size keeps fewer messages in memory and therefore uses less memory.</span></span>  
  
 <span data-ttu-id="4bd66-116">將傳送埠和接收位置放置在不同的電腦上，也可以減少記憶體的使用。</span><span class="sxs-lookup"><span data-stu-id="4bd66-116">Placing send ports and receive locations on separate computers can also reduce memory use.</span></span>  
  
## <a name="send-optimization"></a><span data-ttu-id="4bd66-117">傳送最佳化</span><span class="sxs-lookup"><span data-stu-id="4bd66-117">Send Optimization</span></span>  
 <span data-ttu-id="4bd66-118">在傳送端上，您可以使用範例協調流程來達成相等的單一訊息處理。</span><span class="sxs-lookup"><span data-stu-id="4bd66-118">On the send side, you can achieve the equivalent single-message processing by using the sample orchestration.</span></span> <span data-ttu-id="4bd66-119">此範例會傳送單一訊息，然後等待傳送下一個訊息，直到它收到通知為止。</span><span class="sxs-lookup"><span data-stu-id="4bd66-119">The sample sends a single message and then waits to send the next message until it receives an acknowledgment.</span></span> <span data-ttu-id="4bd66-120">如需詳細資訊，請參閱[如何建立 MSMQ 接收位置和傳送埠的程式碼](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd66-120">For more information, see [How to Create MSMQ Receive Locations and Send Ports from Code](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md).</span></span>  
  
## <a name="remote-transactional-read-operations"></a><span data-ttu-id="4bd66-121">遠端交易讀取作業</span><span class="sxs-lookup"><span data-stu-id="4bd66-121">Remote Transactional Read Operations</span></span>  
 <span data-ttu-id="4bd66-122">與 BizTalk Server MSMQ 配接器是能夠從交易式 MSMQ 佇列的遠端讀取的作業。</span><span class="sxs-lookup"><span data-stu-id="4bd66-122">With BizTalk Server the MSMQ adapter is capable of making remote read operations from transactional MSMQ queues.</span></span>  <span data-ttu-id="4bd66-123">這是因為 MSMQ 4.0 和更新版本支援遠端交易讀取的作業。</span><span class="sxs-lookup"><span data-stu-id="4bd66-123">This is because MSMQ 4.0 and later versions support remote transactional read operations.</span></span>  <span data-ttu-id="4bd66-124">不過，交易式讀取的作業都是通常很慢的作業。</span><span class="sxs-lookup"><span data-stu-id="4bd66-124">However, transactional read operations are typically slow operations.</span></span> <span data-ttu-id="4bd66-125">若要最佳化效能，則應該只在沒有其他選擇的情況下使用這類作業。</span><span class="sxs-lookup"><span data-stu-id="4bd66-125">To optimize performance they should be used only when there is no other option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd66-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="4bd66-126">See Also</span></span>  
 <span data-ttu-id="4bd66-127">[如何設定 MSMQ 接收位置](../core/how-to-configure-an-msmq-receive-location.md) </span><span class="sxs-lookup"><span data-stu-id="4bd66-127">[How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md) </span></span>  
 <span data-ttu-id="4bd66-128">[如何設定 MSMQ 傳送埠](../core/how-to-configure-an-msmq-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="4bd66-128">[How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md) </span></span>  
 [<span data-ttu-id="4bd66-129">設定 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="4bd66-129">Configuring the MSMQ Adapter</span></span>](../core/configuring-the-msmq-adapter.md)