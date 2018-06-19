---
title: 同步批次支援傳送配接器介面 |Microsoft 文件
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
ms.openlocfilehash: 3ab61fd6624468e0464cfe0c648fcc868bd20005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257670"
---
# <a name="interfaces-for-a-synchronous-batch-supported-send-adapter"></a><span data-ttu-id="b2a20-102">同步批次支援傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="b2a20-102">Interfaces for a Synchronous Batch-Supported Send Adapter</span></span>
<span data-ttu-id="b2a20-103">能識別批次的配接器可以同步或非同步地傳送訊息，並能執行交易式的傳送作業。</span><span class="sxs-lookup"><span data-stu-id="b2a20-103">Batch-aware adapters may send messages synchronously or asynchronously, and may perform transacted send operations.</span></span> <span data-ttu-id="b2a20-104">若要傳送訊息的批次，傳送配接器必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="b2a20-104">To send batches of messages, a send adapter must implement the following interfaces:</span></span>  
  
-   <span data-ttu-id="b2a20-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="b2a20-105">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="b2a20-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="b2a20-106">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="b2a20-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="b2a20-107">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="b2a20-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="b2a20-108">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="b2a20-109">**IBTBatchTransmitter**</span><span class="sxs-lookup"><span data-stu-id="b2a20-109">**IBTBatchTransmitter**</span></span>  
  
-   <span data-ttu-id="b2a20-110">**IBTTransmitterBatch**</span><span class="sxs-lookup"><span data-stu-id="b2a20-110">**IBTTransmitterBatch**</span></span>  
  
 <span data-ttu-id="b2a20-111">對於同步批次傳送，傳訊引擎會從配接器取得批次，並將需要傳輸的訊息新增到該批次中。</span><span class="sxs-lookup"><span data-stu-id="b2a20-111">For the synchronous batch send, the Messaging Engine gets a batch from the adapter and adds messages to be transmitted to that batch.</span></span> <span data-ttu-id="b2a20-112">傳訊引擎中新增每個訊息的批次並傳送訊息，它會呼叫時，才**完成**批次的方法。</span><span class="sxs-lookup"><span data-stu-id="b2a20-112">The Messaging Engine adds each message to the batch and sends the messages only when it calls the **Done** method on the batch.</span></span> <span data-ttu-id="b2a20-113">配接器傳回`True`如**bDeleteMessage**對於要以同步方式傳輸每個訊息。</span><span class="sxs-lookup"><span data-stu-id="b2a20-113">The adapter returns `True` for **bDeleteMessage** for each message that it intends to transmit synchronously.</span></span> <span data-ttu-id="b2a20-114">配接器應該將訊息資料，而非訊息指標儲存在其**TransmitMessage**實作。</span><span class="sxs-lookup"><span data-stu-id="b2a20-114">The adapter should save message data, as opposed to a message pointer, in its **TransmitMessage** implementation.</span></span> <span data-ttu-id="b2a20-115">這是因為在傳回 `True` 之後，訊息指標已經不再有效，而且不該再遭到使用，或是存入快取以便稍後使用。</span><span class="sxs-lookup"><span data-stu-id="b2a20-115">This is because the message pointer is no longer valid after `True` is returned, and should not be used or cached for later use.</span></span>  
  
 <span data-ttu-id="b2a20-116">下圖顯示在建立同步批次支援的傳送配接器時所牽涉的物件互動。</span><span class="sxs-lookup"><span data-stu-id="b2a20-116">The following figure shows the object interactions involved in creating a synchronous batch-supported send adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter6.gif "ebiz_sdk_devadapter6")  
<span data-ttu-id="b2a20-117">同步提交訊息的工作流程</span><span class="sxs-lookup"><span data-stu-id="b2a20-117">Workflow for submitting a message synchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a20-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2a20-118">See Also</span></span>  
 <span data-ttu-id="b2a20-119">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b2a20-119">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="b2a20-120">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b2a20-120">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="b2a20-121">[具現化，並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b2a20-121">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="b2a20-122">[傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b2a20-122">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="b2a20-123">[傳送配接器的非同步介面。](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b2a20-123">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="b2a20-124">[非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b2a20-124">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="b2a20-125">[交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b2a20-125">[Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="b2a20-126">傳送配接器的請求-回應的介面</span><span class="sxs-lookup"><span data-stu-id="b2a20-126">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)