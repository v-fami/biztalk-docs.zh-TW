---
title: 交易式非同步批次支援傳送配接器介面 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5b2dbdf-e6ba-4b58-a0a5-fc78feaf5c35
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c3ad79f09563b3e65ccfab64da5b9ec6ea3033c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982895"
---
# <a name="interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter"></a><span data-ttu-id="85e03-102">交易式非同步批次支援傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="85e03-102">Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter</span></span>
<span data-ttu-id="85e03-103">傳送配接器可以在需要交易式的訊息傳輸時建立及控制交易。</span><span class="sxs-lookup"><span data-stu-id="85e03-103">A send adapter can create and control transactions when transactional transmission of messages is required.</span></span> <span data-ttu-id="85e03-104">若要支援交易式的傳送，配接器必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="85e03-104">To support transactional send, an adapter needs to implement the following interfaces:</span></span>  
  
- <span data-ttu-id="85e03-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="85e03-105">**IBTTransport**</span></span>  
  
- <span data-ttu-id="85e03-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="85e03-106">**IBaseComponent**</span></span>  
  
- <span data-ttu-id="85e03-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="85e03-107">**IBTTransportControl**</span></span>  
  
- <span data-ttu-id="85e03-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="85e03-108">**IPersistPropertyBag**</span></span>  
  
- <span data-ttu-id="85e03-109">**IBTBatchTransmitter**</span><span class="sxs-lookup"><span data-stu-id="85e03-109">**IBTBatchTransmitter**</span></span>  
  
- <span data-ttu-id="85e03-110">**IBTTransmitterBatch**</span><span class="sxs-lookup"><span data-stu-id="85e03-110">**IBTTransmitterBatch**</span></span>  
  
- <span data-ttu-id="85e03-111">**IBTBatchCallBack**</span><span class="sxs-lookup"><span data-stu-id="85e03-111">**IBTBatchCallBack**</span></span>  
  
  <span data-ttu-id="85e03-112">配接器建立 MSDTC 交易，並傳回該物件的呼叫中的指標**Ibttransmitterbatch**方法**IBTTransmitterBatch**介面。</span><span class="sxs-lookup"><span data-stu-id="85e03-112">An adapter creates an MSDTC transaction and returns a pointer to that object in the call to the **BeginBatch** method of the **IBTTransmitterBatch** interface.</span></span> <span data-ttu-id="85e03-113">傳訊引擎會呼叫此方法來取得批次，並透過該批次將外寄訊息公佈至傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="85e03-113">The Messaging Engine calls this method to obtain a batch with which it posts outgoing messages to the send adapter.</span></span> <span data-ttu-id="85e03-114">當配接器完成傳送作業並認可或回復交易時，它會通知傳訊引擎交易的結果使用**DTCCommitConfirm**方法**IBTDTCCommitConfirm**介面。</span><span class="sxs-lookup"><span data-stu-id="85e03-114">When the adapter finishes the send operation and commits or rolls back a transaction, it notifies the Messaging Engine of the result of the transaction by using the **DTCCommitConfirm** method of the **IBTDTCCommitConfirm** interface.</span></span>  
  
  <span data-ttu-id="85e03-115">下圖顯示在執行交易式傳送作業時，傳輸 Proxy 和傳送配接器之間的互動。</span><span class="sxs-lookup"><span data-stu-id="85e03-115">The following figure shows the interaction between the transport proxy and the send adapter when performing a transactional send operation.</span></span>  
  
  <span data-ttu-id="85e03-116">![](../core/media/ebiz-sdk-devadapter8.gif "ebiz_sdk_devadapter8")</span><span class="sxs-lookup"><span data-stu-id="85e03-116">![](../core/media/ebiz-sdk-devadapter8.gif "ebiz_sdk_devadapter8")</span></span>  
  <span data-ttu-id="85e03-117">非同步傳送交易式訊息的工作流程</span><span class="sxs-lookup"><span data-stu-id="85e03-117">Workflow for sending a transactional message asynchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e03-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85e03-118">See Also</span></span>  
 <span data-ttu-id="85e03-119">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="85e03-119">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="85e03-120">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="85e03-120">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="85e03-121">[具現化並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="85e03-121">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="85e03-122">[傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="85e03-122">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="85e03-123">[介面的非同步傳送配接器](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="85e03-123">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="85e03-124">[同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="85e03-124">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="85e03-125">[非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="85e03-125">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="85e03-126">請求-回應傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="85e03-126">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)