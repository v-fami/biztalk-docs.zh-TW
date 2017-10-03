---
title: "使用 BizTalk 傳訊引擎 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, Messaging Engine
- adapters, TransportProxy object
- Messaging Engine, adapters
- Messaging Engine, architecture
- TransportProxy object
- Messaging Engine, how to
- architecture, Messaging Engine
- messages, Messaging Engine
ms.assetid: e6b6d1ec-38cd-4721-9673-ae40da003dec
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 701ed3e82eb75b98a948313a99bb4debc65a8cce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-biztalk-messaging-engine"></a><span data-ttu-id="8a118-102">使用 BizTalk 傳訊引擎</span><span class="sxs-lookup"><span data-stu-id="8a118-102">Using the BizTalk Messaging Engine</span></span>
<span data-ttu-id="8a118-103">下列圖表說明傳訊引擎的架構。</span><span class="sxs-lookup"><span data-stu-id="8a118-103">The following diagram illustrates the architecture of the Messaging Engine.</span></span> <span data-ttu-id="8a118-104">它顯示配接器收到訊息並將它提交至 BizTalk Server 的實例。</span><span class="sxs-lookup"><span data-stu-id="8a118-104">It shows a scenario in which a message is received by an adapter and submitted into BizTalk Server.</span></span>  
  
 ![](../core/media/ebiz-prog-messaging1.gif "ebiz_prog_messaging1")  
<span data-ttu-id="8a118-105">傳訊引擎的架構</span><span class="sxs-lookup"><span data-stu-id="8a118-105">Architecture of the Messaging Engine</span></span>  
  
 <span data-ttu-id="8a118-106">每個配接器都有自己的執行個體**TransportProxy**物件，它會使用與 「 傳訊引擎互動。</span><span class="sxs-lookup"><span data-stu-id="8a118-106">Each adapter has its own instance of a **TransportProxy** object that it uses to interact with the Messaging Engine.</span></span> <span data-ttu-id="8a118-107">配接器會以批次方式在傳訊引擎上執行工作，並且以不可部分完成的方式處理。</span><span class="sxs-lookup"><span data-stu-id="8a118-107">Adapters perform work against the Messaging Engine in batches, which are processed atomically.</span></span> <span data-ttu-id="8a118-108">批次是一個作業集合，其中包括 SubmitMessage、SuspendMessage 或 DeleteMessage。</span><span class="sxs-lookup"><span data-stu-id="8a118-108">A batch is a collection of operations such as SubmitMessage, SuspendMessage, or DeleteMessage.</span></span>  
  
 <span data-ttu-id="8a118-109">下列是配接器提交訊息至傳訊引擎的實例之事件順序：</span><span class="sxs-lookup"><span data-stu-id="8a118-109">The following is the sequence of events for the scenario where an adapter submits a message to the Messaging Engine:</span></span>  
  
1.  <span data-ttu-id="8a118-110">配接器建立新訊息並將資料流連接到訊息。</span><span class="sxs-lookup"><span data-stu-id="8a118-110">The adapter creates a new message and connects the data stream to the message.</span></span>  
  
2.  <span data-ttu-id="8a118-111">配接器從傳訊引擎取得新批次。</span><span class="sxs-lookup"><span data-stu-id="8a118-111">The adapter gets a new batch from the Messaging Engine.</span></span>  
  
3.  <span data-ttu-id="8a118-112">配接器會新增訊息至提交的批次。</span><span class="sxs-lookup"><span data-stu-id="8a118-112">The adapter adds the message to the batch to be submitted.</span></span>  
  
4.  <span data-ttu-id="8a118-113">該批次已認可且已經在傳訊引擎的執行緒集區中排入佇列。</span><span class="sxs-lookup"><span data-stu-id="8a118-113">The batch is committed and queued up on the Messaging Engine thread pool.</span></span>  
  
5.  <span data-ttu-id="8a118-114">傳訊引擎執行緒集區開始處理新批次。</span><span class="sxs-lookup"><span data-stu-id="8a118-114">The Messaging Engine thread pool starts processing the new batch.</span></span>  
  
6.  <span data-ttu-id="8a118-115">在接收管線中處理訊息。</span><span class="sxs-lookup"><span data-stu-id="8a118-115">The message is processed in the receive pipeline.</span></span>  
  
7.  <span data-ttu-id="8a118-116">接收管線產生零或多個訊息。</span><span class="sxs-lookup"><span data-stu-id="8a118-116">The receive pipeline produces zero or more messages.</span></span> <span data-ttu-id="8a118-117">若訊息未傳回任何錯誤，管線就可以取用訊息。</span><span class="sxs-lookup"><span data-stu-id="8a118-117">Pipelines can consume messages providing they do not return any errors.</span></span> <span data-ttu-id="8a118-118">接收管線可以產生一個以上的訊息；這通常發生在解譯器元件將單一交換解譯為多個訊息的情況。</span><span class="sxs-lookup"><span data-stu-id="8a118-118">Receive pipelines can produce more than one message; typically this happens when the dissassembler component disassembles a single interchange into many messages.</span></span> <span data-ttu-id="8a118-119">一般而言，接收管線會將提交到 XML 的訊息正規化。</span><span class="sxs-lookup"><span data-stu-id="8a118-119">Typically the receive pipeline normalizes the submitted message into XML.</span></span>  
  
8.  <span data-ttu-id="8a118-120">若已設定對應，則會在對應工具中處理管線所產生的訊息。</span><span class="sxs-lookup"><span data-stu-id="8a118-120">The message(s) produced by the pipeline will be processed in the mapper if mapping is configured.</span></span>  
  
9. <span data-ttu-id="8a118-121">訊息會發佈到訊息代理程式或發佈到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8a118-121">The message(s) are published to the Message Agent or to the MessageBox database.</span></span>  
  
10. <span data-ttu-id="8a118-122">傳訊引擎會回呼配接器以通知它工作批次的結果。</span><span class="sxs-lookup"><span data-stu-id="8a118-122">The Messaging Engine calls back the adapter to notify it of the outcome of the batch of work.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a118-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="8a118-123">In This Section</span></span>  
  
-   [<span data-ttu-id="8a118-124">可復原交換處理</span><span class="sxs-lookup"><span data-stu-id="8a118-124">Recoverable Interchange Processing</span></span>](../core/recoverable-interchange-processing.md)  
  
-   [<span data-ttu-id="8a118-125">訊息的排序傳遞</span><span class="sxs-lookup"><span data-stu-id="8a118-125">Ordered Delivery of Messages</span></span>](../core/ordered-delivery-of-messages.md)  
  
-   [<span data-ttu-id="8a118-126">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="8a118-126">Error Handling</span></span>](../core/error-handling.md)  
  
## <a name="see-also"></a><span data-ttu-id="8a118-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a118-127">See Also</span></span>  
 <span data-ttu-id="8a118-128">[BizTalk Server 如何處理大型訊息](../core/how-biztalk-server-processes-large-messages.md) </span><span class="sxs-lookup"><span data-stu-id="8a118-128">[How BizTalk Server Processes Large Messages](../core/how-biztalk-server-processes-large-messages.md) </span></span>  
 <span data-ttu-id="8a118-129">[引擎效能特性](../core/engine-performance-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="8a118-129">[Engine Performance Characteristics](../core/engine-performance-characteristics.md) </span></span>  
 <span data-ttu-id="8a118-130">[測量最大持續性引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="8a118-130">[Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md) </span></span>  
 <span data-ttu-id="8a118-131">[測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span><span class="sxs-lookup"><span data-stu-id="8a118-131">[Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span></span>  
 [<span data-ttu-id="8a118-132">使用 Microsoft BizTalk LoadGen 2007 工具</span><span class="sxs-lookup"><span data-stu-id="8a118-132">Using the Microsoft BizTalk LoadGen 2007 Tool</span></span>](../core/using-the-microsoft-biztalk-loadgen-2007-tool.md)