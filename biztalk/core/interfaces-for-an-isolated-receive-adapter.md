---
title: 介面的外掛式接收配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c6b195e-76bf-4c3e-a324-5513bc24fed1
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7848e5c808ad2e7517d0e850e449f8a8575ec5da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257766"
---
# <a name="interfaces-for-an-isolated-receive-adapter"></a><span data-ttu-id="d6546-102">外掛式接收配接器介面</span><span class="sxs-lookup"><span data-stu-id="d6546-102">Interfaces for an Isolated Receive Adapter</span></span>
<span data-ttu-id="d6546-103">外掛式接收配接器是裝載於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序之外的程序空間內。</span><span class="sxs-lookup"><span data-stu-id="d6546-103">Isolated receive adapters are hosted in a process space other than the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process.</span></span> <span data-ttu-id="d6546-104">若要與「傳訊引擎」互動，外掛式接收配接器會在啟動時進行註冊，讓引擎能對它進行設定和控制。</span><span class="sxs-lookup"><span data-stu-id="d6546-104">To interact with the Messaging Engine, an isolated receive adapter registers itself on startup so that the engine can configure and control it.</span></span> <span data-ttu-id="d6546-105">配接器會建立傳輸 proxy、 查詢介面**IBTTransportProxy**，並呼叫**IBTTransportProxy.RegisterIsolatedReceiver**註冊其**IBTTransportConfig**與傳訊引擎回呼介面。</span><span class="sxs-lookup"><span data-stu-id="d6546-105">The adapter creates the transport proxy, queries for the interface **IBTTransportProxy**, and calls **IBTTransportProxy.RegisterIsolatedReceiver** to register its **IBTTransportConfig** callback interface with the Messaging Engine.</span></span> <span data-ttu-id="d6546-106">此同步呼叫發生後，配接器才會提交其第一個訊息至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d6546-106">This synchronous call occurs before the adapter submits its first message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d6546-107">這可讓傳訊引擎回呼配接器，告訴它哪些結束點作用中並應接聽是否有內送訊息。</span><span class="sxs-lookup"><span data-stu-id="d6546-107">This allows the Messaging Engine to call back into the adapter and tell it which of its endpoints are active and should be listened on for incoming messages.</span></span> <span data-ttu-id="d6546-108">外掛式配接器必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="d6546-108">Isolated adapters must implement the following interfaces:</span></span>  
  
-   <span data-ttu-id="d6546-109">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="d6546-109">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="d6546-110">**IBTTransportConfig**</span><span class="sxs-lookup"><span data-stu-id="d6546-110">**IBTTransportConfig**</span></span>  
  
-   <span data-ttu-id="d6546-111">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="d6546-111">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="d6546-112">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="d6546-112">**IPersistPropertyBag**</span></span>  
  
 <span data-ttu-id="d6546-113">若要註冊配接器，配接器必須傳遞已設定和啟用的接收位置。</span><span class="sxs-lookup"><span data-stu-id="d6546-113">Registering the adapter requires the adapter to pass a configured and enabled receive location.</span></span> <span data-ttu-id="d6546-114">此配接器的主控件處理序必須是 BizTalk 外掛式主控件使用者群組的成員。</span><span class="sxs-lookup"><span data-stu-id="d6546-114">The adapter's host process must be a member of the BizTalk Isolated Host Users group.</span></span> <span data-ttu-id="d6546-115">此外，也會查詢此配接器，確定它有正確類別識別碼，而且正在已針對該主控件執行個體設定的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="d6546-115">In addition, the adapter is queried to ensure that it has the correct class ID and is running on the computer that was configured for that host instance.</span></span>  
  
 <span data-ttu-id="d6546-116">配接器已成功向傳輸 proxy 之後，傳訊引擎 」 會將組態資訊和其他接收位置傳回至配接器藉由呼叫**負載**方法**IPersistPropertyBag**介面和**AddReceiveEndpoint**方法**IBTTransportConfig**分別介面。</span><span class="sxs-lookup"><span data-stu-id="d6546-116">After the adapter has successfully registered with the transport proxy, the Messaging Engine passes the configuration information and the other receive locations back to the adapter by calling the **Load** method of the **IPersistPropertyBag** interface and the **AddReceiveEndpoint** method of the **IBTTransportConfig** interface respectively.</span></span>  
  
 <span data-ttu-id="d6546-117">當外掛式接收配接器結束訊息處理，且即將結束，則必須呼叫**TerminateIsolatedReceiver**方法**IBTTransportProxy**介面。</span><span class="sxs-lookup"><span data-stu-id="d6546-117">When an isolated receive adapter ends the processing of messages and is going to be terminated, it must call the **TerminateIsolatedReceiver** method of the **IBTTransportProxy** interface.</span></span>  
  
 <span data-ttu-id="d6546-118">下圖顯示在建立外掛式接收配接器時所牽涉的物件互動。</span><span class="sxs-lookup"><span data-stu-id="d6546-118">The following illustration shows the object interactions involved in creating an isolated receive adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter9.gif "ebiz_sdk_devadapter9")  
<span data-ttu-id="d6546-119">初始化外掛式接收配接器的工作流程。</span><span class="sxs-lookup"><span data-stu-id="d6546-119">Workflow for initializing an isolated receive adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6546-120">建議配接器應持續追蹤目前對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行中的要求。</span><span class="sxs-lookup"><span data-stu-id="d6546-120">We recommend that the adapter keep track of currently executing requests to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d6546-121">此配接器應封鎖**Terminate**方法，直到工作計數達到零。</span><span class="sxs-lookup"><span data-stu-id="d6546-121">The adapter should block the **Terminate** method until the work count has reached zero.</span></span> <span data-ttu-id="d6546-122">在接收端，此工作包含尚未發佈至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的任何未完成要求。</span><span class="sxs-lookup"><span data-stu-id="d6546-122">On the receive side, this work includes any outstanding requests that have not been published to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d6546-123">請注意，回應訊息通常不會傳遞至接收配接器之後**Terminate**呼叫。</span><span class="sxs-lookup"><span data-stu-id="d6546-123">Note that response messages are typically not delivered to a receive adapter after **Terminate** is called.</span></span> <span data-ttu-id="d6546-124">一般情況下，配接器呼叫之後**Terminate**方法中，「 傳訊引擎不接受發佈新訊息，除了請求-回應組的回應訊息的要求。</span><span class="sxs-lookup"><span data-stu-id="d6546-124">In general, after the adapter calls the **Terminate** method, the Messaging Engine does not accept requests to publish new messages, with the exception of response messages for solicit-response pairs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6546-125">一個程序可能裝載數個外掛式配接器執行個體，但一個程序只能裝載一個配接器。</span><span class="sxs-lookup"><span data-stu-id="d6546-125">One process may host several instances of isolated adapters, while only one process may host one adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6546-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6546-126">See Also</span></span>  
 <span data-ttu-id="d6546-127">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="d6546-127">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="d6546-128">[開發接收配接器](../core/developing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d6546-128">[Developing a Receive Adapter](../core/developing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="d6546-129">[具現化，並初始化接收配接器](../core/instantiating-and-initializing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d6546-129">[Instantiating and Initializing a Receive Adapter](../core/instantiating-and-initializing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="d6546-130">[介面的內含式接收配接器](../core/interfaces-for-an-in-process-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d6546-130">[Interfaces for an In-Process Receive Adapter](../core/interfaces-for-an-in-process-receive-adapter.md) </span></span>  
 <span data-ttu-id="d6546-131">[接收配接器批次支援的介面](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d6546-131">[Interfaces for a Batch-Supported Receive Adapter](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span></span>  
 <span data-ttu-id="d6546-132">[交易式批次支援接收配接器介面](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d6546-132">[Interfaces for a Transactional Batch-Supported Receive Adapter](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md) </span></span>  
 [<span data-ttu-id="d6546-133">接收配接器同步要求-回應的介面</span><span class="sxs-lookup"><span data-stu-id="d6546-133">Interfaces for a Synchronous Request-Response Receive Adapter</span></span>](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)