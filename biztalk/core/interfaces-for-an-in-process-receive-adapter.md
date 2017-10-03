---
title: "介面的內含式接收配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ed668d9-7512-4026-a8f3-df05aeed4df6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7135471700cf640f61b56506ad159b5c47c7d877
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-an-in-process-receive-adapter"></a><span data-ttu-id="31041-102">內含式接收配接器的介面</span><span class="sxs-lookup"><span data-stu-id="31041-102">Interfaces for an In-Process Receive Adapter</span></span>
<span data-ttu-id="31041-103">「傳訊引擎」會具現化和設定內含式配接器，並傳入傳輸 Proxy 以允許配接器存取其功能。</span><span class="sxs-lookup"><span data-stu-id="31041-103">The Messaging Engine instantiates and configures in-process adapters, passing in the transport proxy to allow the adapter to access its functionality.</span></span> <span data-ttu-id="31041-104">若要啟用組態並與傳輸 Proxy 繫結，配接器必須實作下列的組態介面：</span><span class="sxs-lookup"><span data-stu-id="31041-104">To enable configuration and binding to the transport proxy, adapters must implement the following configuration interfaces:</span></span>  
  
-   <span data-ttu-id="31041-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="31041-105">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="31041-106">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="31041-106">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="31041-107">**IBTTransportConfig**</span><span class="sxs-lookup"><span data-stu-id="31041-107">**IBTTransportConfig**</span></span>  
  
-   <span data-ttu-id="31041-108">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="31041-108">**IBaseComponent**</span></span>  
  
 <span data-ttu-id="31041-109">（選擇性） 如果配接器想要接收處理常式資訊初始化期間，需要實作**IPersistPropertyBag**。</span><span class="sxs-lookup"><span data-stu-id="31041-109">Optionally if the adapter wants to receive handler information during initialization it needs to implement **IPersistPropertyBag**.</span></span>  
  
 <span data-ttu-id="31041-110">「傳訊引擎」會建立配接器的執行個體、初始化該執行個體，然後設定接收位置的組態。</span><span class="sxs-lookup"><span data-stu-id="31041-110">The Messaging Engine creates an instance of an adapter, initializes it, and sets the configuration of receive locations.</span></span> <span data-ttu-id="31041-111">傳訊引擎傳送至配接器的屬性包**AddReceiveEndpoint**方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="31041-111">The Messaging Engine passes a property bag to an adapter on the **AddReceiveEndpoint** method call.</span></span> <span data-ttu-id="31041-112">該屬性包含有接收位置和接收處理常式的組態。</span><span class="sxs-lookup"><span data-stu-id="31041-112">The property bag contains the configuration for the receive location and receive handler.</span></span> <span data-ttu-id="31041-113">組態是以 XML 樣式屬性包的形式儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="31041-113">The configuration is stored in the database in the form of an XML-styled property bag.</span></span> <span data-ttu-id="31041-114">「傳訊引擎」會從 XML 讀取 XML 並解除凍結屬性包。</span><span class="sxs-lookup"><span data-stu-id="31041-114">The Messaging Engine reads the XML and rehydrates a property bag from the XML.</span></span> <span data-ttu-id="31041-115">在至少新增一個端點 (接收位置) 後，配接器便會開始提交訊息。</span><span class="sxs-lookup"><span data-stu-id="31041-115">After at least one endpoint (receive location) is added, the adapter can start submitting messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31041-116">配接器應該不會封鎖傳訊引擎會呼叫這類**IBTTransportControl.Initialize**， **IPersistPropertyBag.Load**，和**IBTTransportConfig.AddReceiveEndpoint**.</span><span class="sxs-lookup"><span data-stu-id="31041-116">Adapters should not block Messaging Engine calls such as **IBTTransportControl.Initialize**, **IPersistPropertyBag.Load**, and **IBTTransportConfig.AddReceiveEndpoint**.</span></span> <span data-ttu-id="31041-117">在這些呼叫中執行過多的處理，便會對服務啟動時間造成影響。</span><span class="sxs-lookup"><span data-stu-id="31041-117">Performing excessive processing in these calls will affect service startup time.</span></span>  
  
 <span data-ttu-id="31041-118">下圖顯示在建立內含式接收配接器時所牽涉的物件互動。</span><span class="sxs-lookup"><span data-stu-id="31041-118">The following figure shows the object interactions involved in creating an in-process receive adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter11.gif "ebiz_sdk_devadapter11")  
<span data-ttu-id="31041-119">內含式接收配接器的工作流程</span><span class="sxs-lookup"><span data-stu-id="31041-119">Workflow for an in-process receive adapter</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31041-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31041-120">See Also</span></span>  
 <span data-ttu-id="31041-121">[配接器變數](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="31041-121">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="31041-122">[開發接收配接器](../core/developing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="31041-122">[Developing a Receive Adapter](../core/developing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="31041-123">[具現化，並初始化接收配接器](../core/instantiating-and-initializing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="31041-123">[Instantiating and Initializing a Receive Adapter](../core/instantiating-and-initializing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="31041-124">[介面的外掛式接收配接器](../core/interfaces-for-an-isolated-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="31041-124">[Interfaces for an Isolated Receive Adapter](../core/interfaces-for-an-isolated-receive-adapter.md) </span></span>  
 <span data-ttu-id="31041-125">[接收配接器批次支援的介面](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="31041-125">[Interfaces for a Batch-Supported Receive Adapter](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span></span>  
 <span data-ttu-id="31041-126">[交易式批次支援接收配接器介面](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="31041-126">[Interfaces for a Transactional Batch-Supported Receive Adapter](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md) </span></span>  
 [<span data-ttu-id="31041-127">接收配接器同步要求-回應的介面</span><span class="sxs-lookup"><span data-stu-id="31041-127">Interfaces for a Synchronous Request-Response Receive Adapter</span></span>](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)