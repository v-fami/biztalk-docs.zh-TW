---
title: 非同步批次支援傳送配接器介面 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d38b8b87-508a-499b-86b2-846938050b44
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc579995821a97dc588b2221f8a7dd2e9cd1e136
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993015"
---
# <a name="interfaces-for-an-asynchronous-batch-supported-send-adapter"></a><span data-ttu-id="b1db0-102">非同步批次支援傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="b1db0-102">Interfaces for an Asynchronous Batch-Supported Send Adapter</span></span>
<span data-ttu-id="b1db0-103">批次感知的配接器可以同步或非同步地傳送訊息，而且可以執行交易式的傳送作業。</span><span class="sxs-lookup"><span data-stu-id="b1db0-103">Batch-aware adapters may send messages synchronously or asynchronously, and may perform transacted sends.</span></span> <span data-ttu-id="b1db0-104">若要傳送訊息的批次，傳送配接器必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="b1db0-104">To send batches of messages, a send adapter must implement the following interfaces:</span></span>  
  
- <span data-ttu-id="b1db0-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="b1db0-105">**IBTTransport**</span></span>  
  
- <span data-ttu-id="b1db0-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="b1db0-106">**IBaseComponent**</span></span>  
  
- <span data-ttu-id="b1db0-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="b1db0-107">**IBTTransportControl**</span></span>  
  
- <span data-ttu-id="b1db0-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="b1db0-108">**IPersistPropertyBag**</span></span>  
  
- <span data-ttu-id="b1db0-109">**IBTBatchTransmitter**</span><span class="sxs-lookup"><span data-stu-id="b1db0-109">**IBTBatchTransmitter**</span></span>  
  
- <span data-ttu-id="b1db0-110">**IBTTransmitterBatch**</span><span class="sxs-lookup"><span data-stu-id="b1db0-110">**IBTTransmitterBatch**</span></span>  
  
  <span data-ttu-id="b1db0-111">對於非同步批次傳送，傳訊引擎會從配接器取得批次，並將需要傳輸的訊息新增到該批次中。</span><span class="sxs-lookup"><span data-stu-id="b1db0-111">For the asynchronous batch send, the Messaging Engine gets a batch from the adapter and adds messages to be transmitted to that batch.</span></span> <span data-ttu-id="b1db0-112">當傳訊引擎會呼叫時，才會傳送訊息**完成**在批次上的方法。</span><span class="sxs-lookup"><span data-stu-id="b1db0-112">The messages are only sent when the Messaging Engine calls the **Done** method on the batch.</span></span> <span data-ttu-id="b1db0-113">對於要以非同步方式傳輸的每個訊息，配接器都會傳回 `False`。</span><span class="sxs-lookup"><span data-stu-id="b1db0-113">The adapter returns `False` for each message that it intends to transmit asynchronously.</span></span> <span data-ttu-id="b1db0-114">接著配接器會從配接器 Proxy 取得批次，並刪除它已成功傳輸的訊息。</span><span class="sxs-lookup"><span data-stu-id="b1db0-114">The adapter then gets a batch from the adapter proxy and deletes those messages that it successfully transmitted.</span></span>  
  
  <span data-ttu-id="b1db0-115">下圖顯示在建立非同步批次支援的傳送配接器時所牽涉的物件互動。</span><span class="sxs-lookup"><span data-stu-id="b1db0-115">The following figure shows the object interactions involved in creating an asynchronous batch-supported send adapter.</span></span>  
  
  <span data-ttu-id="b1db0-116">![](../core/media/ebiz-sdk-devadapter7.gif "ebiz_sdk_devadapter7")</span><span class="sxs-lookup"><span data-stu-id="b1db0-116">![](../core/media/ebiz-sdk-devadapter7.gif "ebiz_sdk_devadapter7")</span></span>  
  <span data-ttu-id="b1db0-117">非同步傳送訊息的工作流程</span><span class="sxs-lookup"><span data-stu-id="b1db0-117">Workflow for sending a message asynchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1db0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1db0-118">See Also</span></span>  
 <span data-ttu-id="b1db0-119">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b1db0-119">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="b1db0-120">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b1db0-120">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="b1db0-121">[具現化並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b1db0-121">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="b1db0-122">[傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b1db0-122">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="b1db0-123">[介面的非同步傳送配接器](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b1db0-123">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="b1db0-124">[同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b1db0-124">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="b1db0-125">[交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b1db0-125">[Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="b1db0-126">請求-回應傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="b1db0-126">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)