---
title: "傳送配接器介面的非同步 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a214716-8f39-400d-a111-ba1b92a284b4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db156f5a95a088ae706bb2b1c801d8dee89cdece
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-an-asynchronous-send-adapter"></a><span data-ttu-id="b74ed-102">非同步傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="b74ed-102">Interfaces for an Asynchronous Send Adapter</span></span>
<span data-ttu-id="b74ed-103">每次傳送一個訊息的配接器可以同步或非同步地傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="b74ed-103">Adapters sending messages one at a time may send messages either synchronously or asynchronously.</span></span> <span data-ttu-id="b74ed-104">配接器在執行傳送作業期間使用個別執行緒，而不封鎖傳輸 Proxy 執行緒時，它會非同步傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="b74ed-104">An adapter sends messages asynchronously when it does not block the transport proxy thread but rather uses a separate thread while performing the send operations.</span></span> <span data-ttu-id="b74ed-105">為了能夠非同步傳送訊息，配接器必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="b74ed-105">To be able to send messages asynchronously, an adapter needs to implement the following interfaces:</span></span>  
  
-   <span data-ttu-id="b74ed-106">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="b74ed-106">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="b74ed-107">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="b74ed-107">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="b74ed-108">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="b74ed-108">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="b74ed-109">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="b74ed-109">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="b74ed-110">**IBTTransmitter**</span><span class="sxs-lookup"><span data-stu-id="b74ed-110">**IBTTransmitter**</span></span>  
  
 <span data-ttu-id="b74ed-111">下列步驟說明傳送配接器在「傳訊引擎」要求下，為了從伺服器中傳輸訊息，所執行的動作順序：</span><span class="sxs-lookup"><span data-stu-id="b74ed-111">The following steps describe the sequence of actions that the send adapter performs to transmit messages out of the server at the request of the Messaging Engine:</span></span>  
  
1.  <span data-ttu-id="b74ed-112">傳訊引擎會使用傳輸 proxy 將外寄訊息至傳送配接器，藉由呼叫**TransmitMessage**方法**IBTTransmitter**介面。</span><span class="sxs-lookup"><span data-stu-id="b74ed-112">The Messaging Engine uses the transport proxy to pass an outgoing message to a send adapter by calling the **TransmitMessage** method of the **IBTTransmitter** interface.</span></span>  
  
2.  <span data-ttu-id="b74ed-113">配接器會立即傳回從**TransmitMessage**後儲存訊息以傳送到某些內部佇列，並傳回`False`如**bDeleteMessage**。</span><span class="sxs-lookup"><span data-stu-id="b74ed-113">The adapter returns immediately from **TransmitMessage** after storing the message to be sent to some internal queue, and returns `False` for **bDeleteMessage**.</span></span> <span data-ttu-id="b74ed-114">這會告知「傳訊引擎」，訊息將會以非同步方式傳輸。</span><span class="sxs-lookup"><span data-stu-id="b74ed-114">This tells the Messaging Engine the message will be transmitted in an asynchronous manner.</span></span>  
  
3.  <span data-ttu-id="b74ed-115">配接器使用專屬的執行緒集區傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="b74ed-115">The adapter sends the message using its own thread pool.</span></span>  
  
4.  <span data-ttu-id="b74ed-116">在傳送作業完成之後，配接器會從 MessageBox 資料庫刪除原始訊息。</span><span class="sxs-lookup"><span data-stu-id="b74ed-116">After the send operation completes, the adapter deletes the original message from the MessageBox database.</span></span> <span data-ttu-id="b74ed-117">它會從傳訊引擎使用取得批次**IBTTransportBatch.GetBatch**方法的傳輸 proxy，然後呼叫**DeleteMessage**。</span><span class="sxs-lookup"><span data-stu-id="b74ed-117">It obtains a batch from the Messaging Engine using the **IBTTransportBatch.GetBatch** method of the transport proxy, and then calls **DeleteMessage**.</span></span>  
  
     <span data-ttu-id="b74ed-118">下圖顯示建立非同步傳送配接器時所包含的物件互動。</span><span class="sxs-lookup"><span data-stu-id="b74ed-118">The following figure shows the object interactions involved in creating an asynchronous send adapter.</span></span>  
  
     ![](../core/media/ebiz-sdk-devadapter5.gif "ebiz_sdk_devadapter5")  
<span data-ttu-id="b74ed-119">非同步傳送訊息的工作流程</span><span class="sxs-lookup"><span data-stu-id="b74ed-119">Workflow for sending a message asynchronously</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b74ed-120">建議配接器應計算目前處理中訊息的數目。</span><span class="sxs-lookup"><span data-stu-id="b74ed-120">We recommend that the adapter keep a count of the messages currently being processed.</span></span> <span data-ttu-id="b74ed-121">此配接器應封鎖**Terminate**訊息計數達到零以前的方法。</span><span class="sxs-lookup"><span data-stu-id="b74ed-121">The adapter should block the **Terminate** method until the message count has reached zero.</span></span> <span data-ttu-id="b74ed-122">對於傳送配接器而言，應該會以適當方式處理進行中的訊息。</span><span class="sxs-lookup"><span data-stu-id="b74ed-122">For send adapters, messages that are being processed should be handled appropriately.</span></span> <span data-ttu-id="b74ed-123">這表示，已成功非同步傳遞的任何訊息都應該從配接器的私用應用程式訊息佇列中刪除，以免將訊息傳送兩次。</span><span class="sxs-lookup"><span data-stu-id="b74ed-123">This means that any message that was successfully delivered asynchronously should be deleted from the adapter's private application message queue to prevent messages from being sent twice.</span></span> <span data-ttu-id="b74ed-124">一般情況下之後, **Terminate**稱為 「 傳訊引擎不接受發佈新訊息的配接器的要求。</span><span class="sxs-lookup"><span data-stu-id="b74ed-124">In general, after **Terminate** is called by the Messaging Engine it does not accept requests to publish new messages from the adapter.</span></span> <span data-ttu-id="b74ed-125">唯一的例外是請求-回應組相關的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="b74ed-125">The exception to this is response messages related to solicit-response pairs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b74ed-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b74ed-126">See Also</span></span>  
 <span data-ttu-id="b74ed-127">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b74ed-127">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="b74ed-128">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b74ed-128">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="b74ed-129">[具現化，並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b74ed-129">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="b74ed-130">[傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b74ed-130">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="b74ed-131">[同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b74ed-131">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="b74ed-132">[非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b74ed-132">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="b74ed-133">[交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b74ed-133">[Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="b74ed-134">傳送配接器的請求-回應的介面</span><span class="sxs-lookup"><span data-stu-id="b74ed-134">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)