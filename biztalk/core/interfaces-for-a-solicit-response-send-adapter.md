---
title: "介面的請求-回應傳送配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c54650e8-dbfb-4c66-843b-0b82c8183dd4
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb8ce9b625bfea144f9a4a615a604efdbe2a3cb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-solicit-response-send-adapter"></a><span data-ttu-id="63456-102">請求-回應傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="63456-102">Interfaces for a Solicit-Response Send Adapter</span></span>
<span data-ttu-id="63456-103">傳送配接器使用與接收配接器相同的批次機制，將回應訊息提交回伺服器。</span><span class="sxs-lookup"><span data-stu-id="63456-103">Send adapters use the same batch mechanism as receive adapters to submit response messages back into the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63456-104">建議請求-回應配接器以非同步方式處理訊息。</span><span class="sxs-lookup"><span data-stu-id="63456-104">It is recommended that a solicit-response adapter is process messages asynchronously.</span></span> <span data-ttu-id="63456-105">如果配接器以同步方式處理訊息，會有訊息重複的風險。</span><span class="sxs-lookup"><span data-stu-id="63456-105">If the adapter processes message in a synchronous manner, there is a risk of message duplication.</span></span>  
  
 <span data-ttu-id="63456-106">傳送配接器必須實作下列介面，才能以請求-回應模式運作：</span><span class="sxs-lookup"><span data-stu-id="63456-106">Send adapters need to implement the following interfaces to work in solicit-response mode:</span></span>  
  
-   <span data-ttu-id="63456-107">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="63456-107">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="63456-108">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="63456-108">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="63456-109">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="63456-109">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="63456-110">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="63456-110">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="63456-111">**IBTTransmitter**</span><span class="sxs-lookup"><span data-stu-id="63456-111">**IBTTransmitter**</span></span>  
  
-   <span data-ttu-id="63456-112">**IBTTransmitterBatch**和**IBTBatchTransmitter** （如果傳送批次是必要）</span><span class="sxs-lookup"><span data-stu-id="63456-112">**IBTTransmitterBatch** and **IBTBatchTransmitter** (if send batching is required)</span></span>  
  
-   <span data-ttu-id="63456-113">**IBTBatchCallBack**</span><span class="sxs-lookup"><span data-stu-id="63456-113">**IBTBatchCallBack**</span></span>  
  
 <span data-ttu-id="63456-114">物件互動包含的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="63456-114">The steps involved in the object interaction are as follows:</span></span>  
  
1.  <span data-ttu-id="63456-115">配接器傳送請求訊息之後，會接收到來自該目的地伺服器的回應訊息，</span><span class="sxs-lookup"><span data-stu-id="63456-115">After the adapter sends a solicit message, it receives back a response message from that destination server.</span></span> <span data-ttu-id="63456-116">然後，便可從傳輸 Proxy 取得批次。</span><span class="sxs-lookup"><span data-stu-id="63456-116">It then obtains a batch from the transport proxy.</span></span>  
  
2.  <span data-ttu-id="63456-117">配接器新增至批次回應訊息，藉由呼叫**Submitresponsemessage**。</span><span class="sxs-lookup"><span data-stu-id="63456-117">The adapter adds the response message to the batch by calling **IBTTransportProxy::SubmitResponseMessage**.</span></span>  
  
3.  <span data-ttu-id="63456-118">配接器提交批次呼叫**ibttransportproxy:: Done**傳遞指標，其**IBTBatchComplete**從傳訊引擎回呼介面。</span><span class="sxs-lookup"><span data-stu-id="63456-118">The adapter submits the batch by calling **IBTTransportProxy::Done** passing in a pointer to its **IBTBatchComplete** interface for the callback from the Messaging Engine.</span></span>  
  
4.  <span data-ttu-id="63456-119">「 傳訊引擎會呼叫配接器的**ibtbatchcallback:: Batchcomplete**回呼方法使用傳輸 proxy 通知它提交作業的結果。</span><span class="sxs-lookup"><span data-stu-id="63456-119">The Messaging Engine calls the adapter's **IBTBatchCallBack::BatchComplete** callback method using the transport proxy notifying it of the result of submission operation.</span></span>  
  
 <span data-ttu-id="63456-120">下圖顯示建立請求-回應傳送配接器時所包含的物件互動。</span><span class="sxs-lookup"><span data-stu-id="63456-120">The following figure shows the object interactions involved in creating a solicit-response send adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter13.gif "ebiz_sdk_devadapter13")  
<span data-ttu-id="63456-121">請求-回應傳送配接器的互動圖表</span><span class="sxs-lookup"><span data-stu-id="63456-121">Interaction diagram for a solicit-response send adapter</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63456-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63456-122">See Also</span></span>  
 <span data-ttu-id="63456-123">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="63456-123">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="63456-124">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="63456-124">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="63456-125">[具現化，並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="63456-125">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="63456-126">[傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="63456-126">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="63456-127">[傳送配接器的非同步介面。](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="63456-127">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="63456-128">[同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="63456-128">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="63456-129">[非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="63456-129">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="63456-130">交易式非同步批次支援傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="63456-130">Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter</span></span>](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)