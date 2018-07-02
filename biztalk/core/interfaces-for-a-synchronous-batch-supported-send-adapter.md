---
title: 同步批次支援傳送配接器介面 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b191c41-ca4f-4d2b-bd15-a93ad87a743d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d14e278869854535695babc9ff8796a833de7217
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968223"
---
# <a name="interfaces-for-a-synchronous-batch-supported-send-adapter"></a><span data-ttu-id="089fe-102">同步批次支援傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="089fe-102">Interfaces for a Synchronous Batch-Supported Send Adapter</span></span>
<span data-ttu-id="089fe-103">能識別批次的配接器可以同步或非同步地傳送訊息，並能執行交易式的傳送作業。</span><span class="sxs-lookup"><span data-stu-id="089fe-103">Batch-aware adapters may send messages synchronously or asynchronously, and may perform transacted send operations.</span></span> <span data-ttu-id="089fe-104">若要傳送訊息的批次，傳送配接器必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="089fe-104">To send batches of messages, a send adapter must implement the following interfaces:</span></span>  
  
- <span data-ttu-id="089fe-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="089fe-105">**IBTTransport**</span></span>  
  
- <span data-ttu-id="089fe-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="089fe-106">**IBaseComponent**</span></span>  
  
- <span data-ttu-id="089fe-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="089fe-107">**IBTTransportControl**</span></span>  
  
- <span data-ttu-id="089fe-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="089fe-108">**IPersistPropertyBag**</span></span>  
  
- <span data-ttu-id="089fe-109">**IBTBatchTransmitter**</span><span class="sxs-lookup"><span data-stu-id="089fe-109">**IBTBatchTransmitter**</span></span>  
  
- <span data-ttu-id="089fe-110">**IBTTransmitterBatch**</span><span class="sxs-lookup"><span data-stu-id="089fe-110">**IBTTransmitterBatch**</span></span>  
  
  <span data-ttu-id="089fe-111">對於同步批次傳送，傳訊引擎會從配接器取得批次，並將需要傳輸的訊息新增到該批次中。</span><span class="sxs-lookup"><span data-stu-id="089fe-111">For the synchronous batch send, the Messaging Engine gets a batch from the adapter and adds messages to be transmitted to that batch.</span></span> <span data-ttu-id="089fe-112">傳訊引擎將批次中的每個訊息，並傳送訊息，它會呼叫時，才**完成**在批次上的方法。</span><span class="sxs-lookup"><span data-stu-id="089fe-112">The Messaging Engine adds each message to the batch and sends the messages only when it calls the **Done** method on the batch.</span></span> <span data-ttu-id="089fe-113">配接器會傳回`True`for **bDeleteMessage**要以同步方式傳輸每個訊息。</span><span class="sxs-lookup"><span data-stu-id="089fe-113">The adapter returns `True` for **bDeleteMessage** for each message that it intends to transmit synchronously.</span></span> <span data-ttu-id="089fe-114">配接器應該將訊息資料，而非訊息指標儲存在其**TransmitMessage**實作。</span><span class="sxs-lookup"><span data-stu-id="089fe-114">The adapter should save message data, as opposed to a message pointer, in its **TransmitMessage** implementation.</span></span> <span data-ttu-id="089fe-115">這是因為在傳回 `True` 之後，訊息指標已經不再有效，而且不該再遭到使用，或是存入快取以便稍後使用。</span><span class="sxs-lookup"><span data-stu-id="089fe-115">This is because the message pointer is no longer valid after `True` is returned, and should not be used or cached for later use.</span></span>  
  
  <span data-ttu-id="089fe-116">下圖顯示在建立同步批次支援的傳送配接器時所牽涉的物件互動。</span><span class="sxs-lookup"><span data-stu-id="089fe-116">The following figure shows the object interactions involved in creating a synchronous batch-supported send adapter.</span></span>  
  
  <span data-ttu-id="089fe-117">![](../core/media/ebiz-sdk-devadapter6.gif "ebiz_sdk_devadapter6")</span><span class="sxs-lookup"><span data-stu-id="089fe-117">![](../core/media/ebiz-sdk-devadapter6.gif "ebiz_sdk_devadapter6")</span></span>  
  <span data-ttu-id="089fe-118">同步提交訊息的工作流程</span><span class="sxs-lookup"><span data-stu-id="089fe-118">Workflow for submitting a message synchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="089fe-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="089fe-119">See Also</span></span>  
 <span data-ttu-id="089fe-120">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="089fe-120">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="089fe-121">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="089fe-121">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="089fe-122">[具現化並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="089fe-122">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="089fe-123">[傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="089fe-123">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="089fe-124">[介面的非同步傳送配接器](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="089fe-124">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="089fe-125">[非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="089fe-125">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="089fe-126">[交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="089fe-126">[Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="089fe-127">請求-回應傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="089fe-127">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)