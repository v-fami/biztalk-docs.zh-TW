---
title: "傳送配接器介面同步 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e1b397a-3a35-4447-8522-d8a5f39a42d7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1012b52bf5c6ab564cc219926b97445e43f60dd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-synchronous-send-adapter"></a><span data-ttu-id="ce6c2-102">同步傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="ce6c2-102">Interfaces for a Synchronous Send Adapter</span></span>
<span data-ttu-id="ce6c2-103">配接器在執行傳送作業當中阻止內送傳訊引擎呼叫執行緒時，它會同步傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="ce6c2-103">An adapter sends messages synchronously when it blocks the incoming Messaging Engine calling thread while performing its send operation.</span></span> <span data-ttu-id="ce6c2-104">為了能夠同步傳送訊息，配接器必須實作下列介面：</span><span class="sxs-lookup"><span data-stu-id="ce6c2-104">To be able to send messages synchronously, an adapter needs to implement the following interfaces:</span></span>  
  
-   <span data-ttu-id="ce6c2-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="ce6c2-105">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="ce6c2-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="ce6c2-106">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="ce6c2-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="ce6c2-107">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="ce6c2-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="ce6c2-108">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="ce6c2-109">**IBTTransmitter**</span><span class="sxs-lookup"><span data-stu-id="ce6c2-109">**IBTTransmitter**</span></span>  
  
 <span data-ttu-id="ce6c2-110">在同步傳送中，配接器傳送訊息時封鎖**TransmitMessage**，和傳輸成功而傳回之後`True.`</span><span class="sxs-lookup"><span data-stu-id="ce6c2-110">In a synchronous send, the adapter sends the message while blocking **TransmitMessage**, and after successful transmission returns `True.`</span></span>  
  
 <span data-ttu-id="ce6c2-111">下圖顯示建立同步傳送配接器時所包含的物件互動。</span><span class="sxs-lookup"><span data-stu-id="ce6c2-111">The following figure shows the object interactions involved in creating a synchronous send adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter4.gif "ebiz_sdk_devadapter4")  
<span data-ttu-id="ce6c2-112">同步傳送訊息的工作流程</span><span class="sxs-lookup"><span data-stu-id="ce6c2-112">Workflow for sending a message synchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6c2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce6c2-113">See Also</span></span>  
 <span data-ttu-id="ce6c2-114">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="ce6c2-114">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="ce6c2-115">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ce6c2-115">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="ce6c2-116">[具現化，並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ce6c2-116">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="ce6c2-117">[傳送配接器的非同步介面。](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ce6c2-117">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="ce6c2-118">[同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ce6c2-118">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="ce6c2-119">[非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ce6c2-119">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="ce6c2-120">[交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ce6c2-120">[Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="ce6c2-121">傳送配接器的請求-回應的介面</span><span class="sxs-lookup"><span data-stu-id="ce6c2-121">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)