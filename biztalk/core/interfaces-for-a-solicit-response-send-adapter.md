---
title: 傳送配接器介面請求-回應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c54650e8-dbfb-4c66-843b-0b82c8183dd4
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5056092886ad9d73d3db3dcc910038bc7dcd6e4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024132"
---
# <a name="interfaces-for-a-solicit-response-send-adapter"></a><span data-ttu-id="d5d47-102">請求-回應傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="d5d47-102">Interfaces for a Solicit-Response Send Adapter</span></span>
<span data-ttu-id="d5d47-103">傳送配接器使用與接收配接器相同的批次機制，將回應訊息提交回伺服器。</span><span class="sxs-lookup"><span data-stu-id="d5d47-103">Send adapters use the same batch mechanism as receive adapters to submit response messages back into the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5d47-104">建議請求-回應配接器以非同步方式處理訊息。</span><span class="sxs-lookup"><span data-stu-id="d5d47-104">It is recommended that a solicit-response adapter is process messages asynchronously.</span></span> <span data-ttu-id="d5d47-105">如果配接器以同步方式處理訊息，會有訊息重複的風險。</span><span class="sxs-lookup"><span data-stu-id="d5d47-105">If the adapter processes message in a synchronous manner, there is a risk of message duplication.</span></span>  
  
 <span data-ttu-id="d5d47-106">傳送配接器必須實作下列介面，才能以請求-回應模式運作：</span><span class="sxs-lookup"><span data-stu-id="d5d47-106">Send adapters need to implement the following interfaces to work in solicit-response mode:</span></span>  
  
- <span data-ttu-id="d5d47-107">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="d5d47-107">**IBTTransport**</span></span>  
  
- <span data-ttu-id="d5d47-108">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="d5d47-108">**IBaseComponent**</span></span>  
  
- <span data-ttu-id="d5d47-109">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="d5d47-109">**IBTTransportControl**</span></span>  
  
- <span data-ttu-id="d5d47-110">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="d5d47-110">**IPersistPropertyBag**</span></span>  
  
- <span data-ttu-id="d5d47-111">**IBTTransmitter**</span><span class="sxs-lookup"><span data-stu-id="d5d47-111">**IBTTransmitter**</span></span>  
  
- <span data-ttu-id="d5d47-112">**IBTTransmitterBatch**並**IBTBatchTransmitter** （如果您是需要傳送批次處理）</span><span class="sxs-lookup"><span data-stu-id="d5d47-112">**IBTTransmitterBatch** and **IBTBatchTransmitter** (if send batching is required)</span></span>  
  
- <span data-ttu-id="d5d47-113">**IBTBatchCallBack**</span><span class="sxs-lookup"><span data-stu-id="d5d47-113">**IBTBatchCallBack**</span></span>  
  
  <span data-ttu-id="d5d47-114">物件互動包含的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="d5d47-114">The steps involved in the object interaction are as follows:</span></span>  
  
1. <span data-ttu-id="d5d47-115">配接器傳送請求訊息之後，會接收到來自該目的地伺服器的回應訊息，</span><span class="sxs-lookup"><span data-stu-id="d5d47-115">After the adapter sends a solicit message, it receives back a response message from that destination server.</span></span> <span data-ttu-id="d5d47-116">然後，便可從傳輸 Proxy 取得批次。</span><span class="sxs-lookup"><span data-stu-id="d5d47-116">It then obtains a batch from the transport proxy.</span></span>  
  
2. <span data-ttu-id="d5d47-117">配接器新增至批次回應訊息，藉由呼叫**Submitresponsemessage**。</span><span class="sxs-lookup"><span data-stu-id="d5d47-117">The adapter adds the response message to the batch by calling **IBTTransportProxy::SubmitResponseMessage**.</span></span>  
  
3. <span data-ttu-id="d5d47-118">配接器提交批次，藉由呼叫**ibttransportproxy:: Done**傳入的指標，其**IBTBatchComplete**從傳訊引擎回呼介面。</span><span class="sxs-lookup"><span data-stu-id="d5d47-118">The adapter submits the batch by calling **IBTTransportProxy::Done** passing in a pointer to its **IBTBatchComplete** interface for the callback from the Messaging Engine.</span></span>  
  
4. <span data-ttu-id="d5d47-119">傳訊引擎會呼叫的介面卡**ibtbatchcallback:: Batchcomplete**回呼方法，使用傳輸 proxy 通知它提交作業的結果。</span><span class="sxs-lookup"><span data-stu-id="d5d47-119">The Messaging Engine calls the adapter's **IBTBatchCallBack::BatchComplete** callback method using the transport proxy notifying it of the result of submission operation.</span></span>  
  
   <span data-ttu-id="d5d47-120">下圖顯示建立請求-回應傳送配接器時所包含的物件互動。</span><span class="sxs-lookup"><span data-stu-id="d5d47-120">The following figure shows the object interactions involved in creating a solicit-response send adapter.</span></span>  
  
   <span data-ttu-id="d5d47-121">![](../core/media/ebiz-sdk-devadapter13.gif "ebiz_sdk_devadapter13")</span><span class="sxs-lookup"><span data-stu-id="d5d47-121">![](../core/media/ebiz-sdk-devadapter13.gif "ebiz_sdk_devadapter13")</span></span>  
   <span data-ttu-id="d5d47-122">請求-回應傳送配接器的互動圖表</span><span class="sxs-lookup"><span data-stu-id="d5d47-122">Interaction diagram for a solicit-response send adapter</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d47-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5d47-123">See Also</span></span>  
 <span data-ttu-id="d5d47-124">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="d5d47-124">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="d5d47-125">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d5d47-125">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="d5d47-126">[具現化並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d5d47-126">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="d5d47-127">[傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d5d47-127">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="d5d47-128">[介面的非同步傳送配接器](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d5d47-128">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="d5d47-129">[同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d5d47-129">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="d5d47-130">[非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d5d47-130">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="d5d47-131">交易式非同步批次支援傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="d5d47-131">Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter</span></span>](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)