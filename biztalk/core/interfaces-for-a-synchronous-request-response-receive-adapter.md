---
title: 接收配接器介面同步要求-回應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c60832-52b5-4d2c-81ec-94c46c375b15
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c78be6c80937367b9ae3572125331d6c7e1b20bc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981431"
---
# <a name="interfaces-for-a-synchronous-request-response-receive-adapter"></a><span data-ttu-id="4894a-102">同步要求-回應接收配接器介面</span><span class="sxs-lookup"><span data-stu-id="4894a-102">Interfaces for a Synchronous Request-Response Receive Adapter</span></span>
<span data-ttu-id="4894a-103">所有的接收配接器都必須實作下列介面，才能以要求-回應模式運作：</span><span class="sxs-lookup"><span data-stu-id="4894a-103">All receive adapters need to implement the following interfaces to work in request-response mode:</span></span>  
  
- <span data-ttu-id="4894a-104">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="4894a-104">**IBTTransport**</span></span>  
  
- <span data-ttu-id="4894a-105">**IBTTransportControl** （只有一般配接器）</span><span class="sxs-lookup"><span data-stu-id="4894a-105">**IBTTransportControl** (regular adapters only)</span></span>  
  
- <span data-ttu-id="4894a-106">**IBTTransportConfig**</span><span class="sxs-lookup"><span data-stu-id="4894a-106">**IBTTransportConfig**</span></span>  
  
- <span data-ttu-id="4894a-107">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="4894a-107">**IBaseComponent**</span></span>  
  
- <span data-ttu-id="4894a-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="4894a-108">**IPersistPropertyBag**</span></span>  
  
- <span data-ttu-id="4894a-109">**IBTBatchCallBack**</span><span class="sxs-lookup"><span data-stu-id="4894a-109">**IBTBatchCallBack**</span></span>  
  
- <span data-ttu-id="4894a-110">**IBTTransmitter**</span><span class="sxs-lookup"><span data-stu-id="4894a-110">**IBTTransmitter**</span></span>  
  
  <span data-ttu-id="4894a-111">支援要求-回應通訊協定的接收配接器 (例如 HTTP 接收配接器) 在提交要求訊息時都會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4894a-111">Receive adapters that support request-response protocols (for example, the HTTP receive adapter) perform the following actions when submitting request messages:</span></span>  
  
1. <span data-ttu-id="4894a-112">接收配接器接收內送要求訊息。</span><span class="sxs-lookup"><span data-stu-id="4894a-112">The receive adapter receives incoming request messages.</span></span> <span data-ttu-id="4894a-113">它從傳輸 proxy 取得批次呼叫**Ibttransportproxy**方法**IBTTransportProxy**介面。</span><span class="sxs-lookup"><span data-stu-id="4894a-113">It obtains a batch from the transport proxy by calling the **GetBatch** method of the **IBTTransportProxy** interface.</span></span> <span data-ttu-id="4894a-114">在這個呼叫配接器用來傳遞回呼指標的其實作**IBTBatchCallBack.BatchComplete**方法。</span><span class="sxs-lookup"><span data-stu-id="4894a-114">In this call the adapter passes in a callback pointer to its implementation of the **IBTBatchCallBack.BatchComplete** method.</span></span>  
  
2. <span data-ttu-id="4894a-115">配接器新增到批次要求訊息，藉由呼叫**SubmitRequestMessage**方法**IBTTransportBatch**介面，針對每個要求訊息一次。</span><span class="sxs-lookup"><span data-stu-id="4894a-115">The adapter adds request messages into the batch by calling the **SubmitRequestMessage** method of the **IBTTransportBatch** interface, once for each request message.</span></span>  
  
3. <span data-ttu-id="4894a-116">新增之後的所有訊息，配接器會呼叫**完成**方法**IBTTransportBatch**介面，提交給傳訊引擎，透過傳輸 proxy 批次。</span><span class="sxs-lookup"><span data-stu-id="4894a-116">When all the messages have been added, the adapter calls the **Done**method of the **IBTTransportBatch** interface, which submits the batch to the Messaging Engine through the transport proxy.</span></span>  
  
4. <span data-ttu-id="4894a-117">批次經過處理之後，傳訊引擎會叫用的介面卡**IBTBatchCallBack.BatchComplete**透過傳輸 proxy 的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="4894a-117">After the batch has been processed, the Messaging Engine invokes the adapter's **IBTBatchCallBack.BatchComplete** callback method through the transport proxy.</span></span> <span data-ttu-id="4894a-118">提交的狀態將以對應於批次中各個訊息的 HRESULT 值陣列，傳送至配接器。</span><span class="sxs-lookup"><span data-stu-id="4894a-118">The status of the submission is passed to the adapter as an array of HRESULT values corresponding to each message in the batch.</span></span> <span data-ttu-id="4894a-119">如果批次在管線或協調流程中失敗，則會將 SOAP 錯誤訊息傳回給配接器，以做為回應。</span><span class="sxs-lookup"><span data-stu-id="4894a-119">If the batch fails, either in the pipeline or in the orchestration, the SOAP fault message is returned to the adapter as a response.</span></span>  
  
5. <span data-ttu-id="4894a-120">內送要求訊息可能有協調流程訂閱者。</span><span class="sxs-lookup"><span data-stu-id="4894a-120">The incoming request messages may have orchestration subscribers.</span></span> <span data-ttu-id="4894a-121">在協調流程完成且已處理的要求訊息之後，傳訊引擎會傳送透過傳輸 proxy 將回應訊息給配接器藉由呼叫配接器的**TransmitMessage** 方法**IBTTransmitter**介面。</span><span class="sxs-lookup"><span data-stu-id="4894a-121">After the orchestration completes and the request message has been processed, the Messaging Engine sends the response message through the transport proxy to the adapter by calling the adapter's **TransmitMessage** method from the **IBTTransmitter** interface.</span></span>  
  
6. <span data-ttu-id="4894a-122">配接器會傳送回應訊息，並刪除 MessageBox 資料庫中的原始訊息。</span><span class="sxs-lookup"><span data-stu-id="4894a-122">The adapter sends a response message and deletes the original message from the MessageBox database.</span></span>  
  
   <span data-ttu-id="4894a-123">下圖顯示在建立同步要求-回應接收配接器時所牽涉的物件互動。</span><span class="sxs-lookup"><span data-stu-id="4894a-123">The following figure shows the object interactions involved in creating a synchronous request-response receive adapter.</span></span>  
  
   <span data-ttu-id="4894a-124">![](../core/media/ebiz-sdk-devadapter3.gif "ebiz_sdk_devadapter3")</span><span class="sxs-lookup"><span data-stu-id="4894a-124">![](../core/media/ebiz-sdk-devadapter3.gif "ebiz_sdk_devadapter3")</span></span>  
   <span data-ttu-id="4894a-125">接收配接器提交同步訊息的工作流程</span><span class="sxs-lookup"><span data-stu-id="4894a-125">Workflow for a receive adapter submitting a synchronous message</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4894a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4894a-126">See Also</span></span>  
 <span data-ttu-id="4894a-127">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="4894a-127">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="4894a-128">[開發接收配接器](../core/developing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="4894a-128">[Developing a Receive Adapter](../core/developing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="4894a-129">[具現化並初始化接收配接器](../core/instantiating-and-initializing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="4894a-129">[Instantiating and Initializing a Receive Adapter](../core/instantiating-and-initializing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="4894a-130">[接收配接器的內含式介面](../core/interfaces-for-an-in-process-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="4894a-130">[Interfaces for an In-Process Receive Adapter](../core/interfaces-for-an-in-process-receive-adapter.md) </span></span>  
 <span data-ttu-id="4894a-131">[接收配接器的外掛式的介面](../core/interfaces-for-an-isolated-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="4894a-131">[Interfaces for an Isolated Receive Adapter](../core/interfaces-for-an-isolated-receive-adapter.md) </span></span>  
 <span data-ttu-id="4894a-132">[接收配接器批次支援的介面](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="4894a-132">[Interfaces for a Batch-Supported Receive Adapter](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span></span>  
 [<span data-ttu-id="4894a-133">交易式批次支援接收配接器介面</span><span class="sxs-lookup"><span data-stu-id="4894a-133">Interfaces for a Transactional Batch-Supported Receive Adapter</span></span>](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)