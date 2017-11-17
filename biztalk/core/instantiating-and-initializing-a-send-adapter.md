---
title: "具現化，並初始化傳送配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f10e6507-3351-4173-95f5-48546ca5f5c4
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07ed590b73d31a03a4b3316a4d84edfc1e39eb0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="instantiating-and-initializing-a-send-adapter"></a><span data-ttu-id="8b9e9-102">產生並初始化傳送配接器</span><span class="sxs-lookup"><span data-stu-id="8b9e9-102">Instantiating and Initializing a Send Adapter</span></span>
<span data-ttu-id="8b9e9-103">根據預設，傳送配接器是在第一個訊息傳遞給它們時才會產生，這項程序稱為「延遲建立」。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-103">By default, send adapters are not instantiated until the first message is delivered to them, a process known as "lazy creation."</span></span> <span data-ttu-id="8b9e9-104">預設的延遲建立方法有助於保存系統資源。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-104">The default lazy creation approach helps to conserve system resources.</span></span> <span data-ttu-id="8b9e9-105">傳送配接器在建立之後，就會存入快取，並維持到 BizTalk Server 服務停止為止。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-105">After the send adapter is created, it is cached and lives until the BizTalk Server service is stopped.</span></span>  
  
 <span data-ttu-id="8b9e9-106">**InitTransmitterOnServiceStart**隸屬**功能**列舉型別指示傳訊引擎，在服務啟動時，而不是使用預設的延遲建立，建立傳送配接器如果這預期。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-106">The **InitTransmitterOnServiceStart** member of the **Capabilities** enumeration directs the Messaging Engine to create the send adapter on service startup, rather than using the default lazy creation, if this is desired.</span></span>  
  
 <span data-ttu-id="8b9e9-107">就訊息批次處理而言，傳送訊息的模型與接收訊息的不同。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-107">Sending a message is a different model than receiving a message with respect to batching of messages.</span></span> <span data-ttu-id="8b9e9-108">在接收時，配接器是將內送訊息插入從傳訊引擎所取得的批次中。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-108">In the receive case the adapter has incoming messages to insert into a batch obtained from the Messaging Engine.</span></span> <span data-ttu-id="8b9e9-109">在傳送時，傳訊引擎則是從配接器取得批次，並將要傳輸的訊息傳送到該配接器。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-109">In the send case the Messaging Engine obtains a batch from the adapter and sends messages to the adapter to be transmitted.</span></span> <span data-ttu-id="8b9e9-110">這兩種作業都使用傳輸 Proxy 來取得訊息批次物件。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-110">Both use the transport proxy to obtain the message batch objects.</span></span>  
  
## <a name="how-a-send-adapter-is-initialized"></a><span data-ttu-id="8b9e9-111">傳送配接器初始化的方式</span><span class="sxs-lookup"><span data-stu-id="8b9e9-111">How a Send Adapter Is Initialized</span></span>  
 <span data-ttu-id="8b9e9-112">若要啟用組態並與傳輸 Proxy 繫結，配接器必須實作下列的組態介面：</span><span class="sxs-lookup"><span data-stu-id="8b9e9-112">To enable configuration and binding to the transport proxy, adapters must implement the following configuration interfaces:</span></span>  
  
-   <span data-ttu-id="8b9e9-113">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="8b9e9-113">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="8b9e9-114">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="8b9e9-114">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="8b9e9-115">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="8b9e9-115">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="8b9e9-116">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="8b9e9-116">**IPersistPropertyBag**</span></span>  
  
 <span data-ttu-id="8b9e9-117">下列步驟描述初始化傳送配接器所涉及的事件順序：</span><span class="sxs-lookup"><span data-stu-id="8b9e9-117">The following steps describe the sequence of events involved in initializing a send adapter:</span></span>  
  
1.  <span data-ttu-id="8b9e9-118">當傳訊引擎在初始化傳送配接器時，會先執行**QueryInterface**如**IPersistPropertyBag**，這是選擇性的介面。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-118">When the Messaging Engine initializes a send adapter, it first performs a **QueryInterface** for **IPersistPropertyBag**, which is an optional interface.</span></span> <span data-ttu-id="8b9e9-119">如果配接器實作此介面，處理常式組態會傳遞給配接器在**負載**方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-119">If the adapter implements the interface, the handler configuration is passed to the adapter in the **Load** method call.</span></span> <span data-ttu-id="8b9e9-120">配接器會使用此資訊，確保其設定正確。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-120">The adapter uses this information to ensure it is configured correctly.</span></span>  
  
2.  <span data-ttu-id="8b9e9-121">傳訊引擎會執行**QueryInterface**如**IBTTransportControl**，這是必要的介面。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-121">The Messaging Engine performs a **QueryInterface** for **IBTTransportControl**, which is a mandatory interface.</span></span>  
  
3.  <span data-ttu-id="8b9e9-122">引擎會呼叫**IBTTransportControl.Initialize**傳遞給配接器傳輸 proxy。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-122">The engine calls **IBTTransportControl.Initialize**, passing in the transport proxy for the adapter.</span></span>  
  
4.  <span data-ttu-id="8b9e9-123">傳訊引擎會執行**QueryInterface**如**IBTTransmitter**。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-123">The Messaging Engine performs a **QueryInterface** for **IBTTransmitter**.</span></span>  
  
     <span data-ttu-id="8b9e9-124">如果傳訊引擎探索這個介面，配接器就會被視為非批次感知的傳輸器。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-124">If the Messaging Engine discovers this interface, the adapter is treated as a batch-unaware transmitter.</span></span>  
  
     <span data-ttu-id="8b9e9-125">如果傳訊引擎不會探索這個介面，「 傳訊引擎會執行**QueryInterface**如**IBTBatchTransmitter**的探索代表配接器是批次感知傳輸器。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-125">If the Messaging Engine does not discover this interface, the Messaging Engine performs a **QueryInterface** for **IBTBatchTransmitter**, discovery of which indicates that the adapter is a batch-aware transmitter.</span></span>  
  
     <span data-ttu-id="8b9e9-126">如果傳訊引擎未探索上述兩種介面，就會產生錯誤狀況，導致初始化失敗。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-126">If the Messaging Engine discovers neither of these interfaces, an error condition results, causing the initialization to fail.</span></span> <span data-ttu-id="8b9e9-127">在未探索任何必要介面時，初始化會失敗。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-127">The initialization fails if any mandatory interfaces are not discovered.</span></span>  
  
 <span data-ttu-id="8b9e9-128">下列圖表說明這個 API 呼叫序列；以藍色顯示的介面是由配接器實作。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-128">The following diagram illustrates this sequence of API calls; the interfaces in blue are implemented by the adapter.</span></span>  
  
 ![](../core/media/transmit-adapter-init.gif "Transmit_adapter_init")  
  
 <span data-ttu-id="8b9e9-129">配接器只要一旦初始化和設定，就可以傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-129">The adapter can send messages as soon as it is initialized and configured.</span></span>  
  
 <span data-ttu-id="8b9e9-130">下圖顯示在初使化傳送配接器時所涉及的物件互動。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-130">The following figure shows the object interactions involved in initializing a send adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter10.gif "ebiz_sdk_devadapter10")  
<span data-ttu-id="8b9e9-131">初始化傳送配接器的工作流程</span><span class="sxs-lookup"><span data-stu-id="8b9e9-131">Workflow for initializing a send adapter</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b9e9-132">介面卡不應該封鎖傳訊引擎中呼叫這類**IBTTransportControl.Initialize**和**IPersistPropertyBag.Load**。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-132">Adapters should not block the Messaging Engine in calls such as **IBTTransportControl.Initialize** and **IPersistPropertyBag.Load**.</span></span> <span data-ttu-id="8b9e9-133">在這些呼叫中執行過多的處理，可能會對服務啟動時間造成影響。</span><span class="sxs-lookup"><span data-stu-id="8b9e9-133">Performing excessive processing in these calls affects service startup time.</span></span>