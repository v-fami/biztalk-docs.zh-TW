---
title: 交易式非同步批次支援傳送配接器的介面，|Microsoft 文件
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
ms.openlocfilehash: 948000883c092c8e247b1d4f41fb2bc7e2280e40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257710"
---
# <a name="interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter"></a><span data-ttu-id="b29f7-102">交易式非同步批次支援傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="b29f7-102">Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter</span></span>
<span data-ttu-id="b29f7-103">傳送配接器可以在需要交易式的訊息傳輸時建立及控制交易。</span><span class="sxs-lookup"><span data-stu-id="b29f7-103">A send adapter can create and control transactions when transactional transmission of messages is required.</span></span> <span data-ttu-id="b29f7-104">若要支援交易式的傳送，配接器必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="b29f7-104">To support transactional send, an adapter needs to implement the following interfaces:</span></span>  
  
-   <span data-ttu-id="b29f7-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="b29f7-105">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="b29f7-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="b29f7-106">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="b29f7-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="b29f7-107">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="b29f7-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="b29f7-108">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="b29f7-109">**IBTBatchTransmitter**</span><span class="sxs-lookup"><span data-stu-id="b29f7-109">**IBTBatchTransmitter**</span></span>  
  
-   <span data-ttu-id="b29f7-110">**IBTTransmitterBatch**</span><span class="sxs-lookup"><span data-stu-id="b29f7-110">**IBTTransmitterBatch**</span></span>  
  
-   <span data-ttu-id="b29f7-111">**IBTBatchCallBack**</span><span class="sxs-lookup"><span data-stu-id="b29f7-111">**IBTBatchCallBack**</span></span>  
  
 <span data-ttu-id="b29f7-112">配接器建立 MSDTC 交易，並傳回該物件的呼叫中的指標**BeginBatch**方法**IBTTransmitterBatch**介面。</span><span class="sxs-lookup"><span data-stu-id="b29f7-112">An adapter creates an MSDTC transaction and returns a pointer to that object in the call to the **BeginBatch** method of the **IBTTransmitterBatch** interface.</span></span> <span data-ttu-id="b29f7-113">傳訊引擎會呼叫此方法來取得批次，並透過該批次將外寄訊息公佈至傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="b29f7-113">The Messaging Engine calls this method to obtain a batch with which it posts outgoing messages to the send adapter.</span></span> <span data-ttu-id="b29f7-114">當配接器完成傳送作業並認可或回復交易時，它會使用通知傳訊引擎交易的結果**DTCCommitConfirm**方法**IBTDTCCommitConfirm**介面。</span><span class="sxs-lookup"><span data-stu-id="b29f7-114">When the adapter finishes the send operation and commits or rolls back a transaction, it notifies the Messaging Engine of the result of the transaction by using the **DTCCommitConfirm** method of the **IBTDTCCommitConfirm** interface.</span></span>  
  
 <span data-ttu-id="b29f7-115">下圖顯示在執行交易式傳送作業時，傳輸 Proxy 和傳送配接器之間的互動。</span><span class="sxs-lookup"><span data-stu-id="b29f7-115">The following figure shows the interaction between the transport proxy and the send adapter when performing a transactional send operation.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter8.gif "ebiz_sdk_devadapter8")  
<span data-ttu-id="b29f7-116">非同步傳送交易式訊息的工作流程</span><span class="sxs-lookup"><span data-stu-id="b29f7-116">Workflow for sending a transactional message asynchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29f7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b29f7-117">See Also</span></span>  
 <span data-ttu-id="b29f7-118">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b29f7-118">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="b29f7-119">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b29f7-119">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="b29f7-120">[具現化，並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b29f7-120">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="b29f7-121">[傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b29f7-121">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="b29f7-122">[傳送配接器的非同步介面。](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b29f7-122">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="b29f7-123">[同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b29f7-123">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="b29f7-124">[非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b29f7-124">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="b29f7-125">傳送配接器的請求-回應的介面</span><span class="sxs-lookup"><span data-stu-id="b29f7-125">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)