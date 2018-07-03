---
title: 傳送配接器介面同步 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e1b397a-3a35-4447-8522-d8a5f39a42d7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1602d19bc5b97231a25f5449f5837fce153c037d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008839"
---
# <a name="interfaces-for-a-synchronous-send-adapter"></a><span data-ttu-id="ec209-102">同步傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="ec209-102">Interfaces for a Synchronous Send Adapter</span></span>
<span data-ttu-id="ec209-103">配接器在執行傳送作業當中阻止內送傳訊引擎呼叫執行緒時，它會同步傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="ec209-103">An adapter sends messages synchronously when it blocks the incoming Messaging Engine calling thread while performing its send operation.</span></span> <span data-ttu-id="ec209-104">為了能夠同步傳送訊息，配接器必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="ec209-104">To be able to send messages synchronously, an adapter needs to implement the following interfaces:</span></span>  
  
- <span data-ttu-id="ec209-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="ec209-105">**IBTTransport**</span></span>  
  
- <span data-ttu-id="ec209-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="ec209-106">**IBaseComponent**</span></span>  
  
- <span data-ttu-id="ec209-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="ec209-107">**IBTTransportControl**</span></span>  
  
- <span data-ttu-id="ec209-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="ec209-108">**IPersistPropertyBag**</span></span>  
  
- <span data-ttu-id="ec209-109">**IBTTransmitter**</span><span class="sxs-lookup"><span data-stu-id="ec209-109">**IBTTransmitter**</span></span>  
  
  <span data-ttu-id="ec209-110">在同步傳送中，配接器傳送訊息時封鎖**TransmitMessage**，並傳回成功傳輸之後， `True.`</span><span class="sxs-lookup"><span data-stu-id="ec209-110">In a synchronous send, the adapter sends the message while blocking **TransmitMessage**, and after successful transmission returns `True.`</span></span>  
  
  <span data-ttu-id="ec209-111">下圖顯示建立同步傳送配接器時所包含的物件互動。</span><span class="sxs-lookup"><span data-stu-id="ec209-111">The following figure shows the object interactions involved in creating a synchronous send adapter.</span></span>  
  
  <span data-ttu-id="ec209-112">![](../core/media/ebiz-sdk-devadapter4.gif "ebiz_sdk_devadapter4")</span><span class="sxs-lookup"><span data-stu-id="ec209-112">![](../core/media/ebiz-sdk-devadapter4.gif "ebiz_sdk_devadapter4")</span></span>  
  <span data-ttu-id="ec209-113">同步傳送訊息的工作流程</span><span class="sxs-lookup"><span data-stu-id="ec209-113">Workflow for sending a message synchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec209-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec209-114">See Also</span></span>  
 <span data-ttu-id="ec209-115">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="ec209-115">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="ec209-116">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ec209-116">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="ec209-117">[具現化並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ec209-117">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="ec209-118">[介面的非同步傳送配接器](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ec209-118">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="ec209-119">[同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ec209-119">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="ec209-120">[非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ec209-120">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="ec209-121">[交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ec209-121">[Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="ec209-122">請求-回應傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="ec209-122">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)