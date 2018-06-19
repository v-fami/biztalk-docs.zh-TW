---
title: EDI 接收元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d3b82e8-1168-4c2c-bf1a-886b43ff8108
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc53f4c592b767c8061fb1ed8134636322b35b9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241694"
---
# <a name="edi-receive-components"></a><span data-ttu-id="c4632-102">EDI 接收元件</span><span class="sxs-lookup"><span data-stu-id="c4632-102">EDI Receive Components</span></span>
<span data-ttu-id="c4632-103">本主題所介紹的管線和管線元件，會處理不屬於 EDI/AS2 訊息的 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="c4632-103">The pipeline and pipeline components described in this topic process EDI messages that are not EDI/AS2 messages.</span></span> <span data-ttu-id="c4632-104">收到的 EDI/AS2 或非 EDI/AS2 訊息的處理程序的相關資訊，請參閱[AS2 接收元件](../core/as2-receive-components.md)。</span><span class="sxs-lookup"><span data-stu-id="c4632-104">For information about the processing of received EDI/AS2 or non-EDI/AS2 messages, see [AS2 Receive Components](../core/as2-receive-components.md).</span></span> <span data-ttu-id="c4632-105">請注意，除了執行 AS2 處理之外，AS2 接收元件也會執行 EDI 處理。</span><span class="sxs-lookup"><span data-stu-id="c4632-105">Note that AS2 receive components perform EDI processing in addition to AS2 processing.</span></span>  
  
## <a name="edi-receive-pipeline"></a><span data-ttu-id="c4632-106">EDI 接收管線</span><span class="sxs-lookup"><span data-stu-id="c4632-106">EDI Receive Pipeline</span></span>  
 <span data-ttu-id="c4632-107">EDI 接收處理是在 EDI 接收管線中執行。</span><span class="sxs-lookup"><span data-stu-id="c4632-107">EDI receive processing is performed in the EDI Receive pipeline.</span></span> <span data-ttu-id="c4632-108">這個管線會安裝在 Microsoft.BizTalk.Edi.EdiPipelines.dll 中[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4632-108">This pipeline is installed in Microsoft.BizTalk.Edi.EdiPipelines.dll in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span> <span data-ttu-id="c4632-109">這個管線會處理透過任何傳輸接的 EDI 訊息，</span><span class="sxs-lookup"><span data-stu-id="c4632-109">This pipeline processes EDI messages received over any transport.</span></span> <span data-ttu-id="c4632-110">它不會處理透過 HTTP 接收的 AS2 編碼 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="c4632-110">It does not process AS2-encoded EDI messages received over HTTP.</span></span> <span data-ttu-id="c4632-111">AS2 編碼 EDI 訊息的處理是由 AS2 管線執行的。</span><span class="sxs-lookup"><span data-stu-id="c4632-111">Processing of AS2-encoded EDI messages is performed by the AS2 pipelines.</span></span> <span data-ttu-id="c4632-112">AS2 接收管線會使用 EDI 管線所使用的相同元件來處理 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="c4632-112">The AS2 receive pipelines use the same components to process EDI messages as the EDI pipeline uses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4632-113">若您建立使用 EDIReceive 管線並具有 HTTP 傳輸類型的接收位置，可能會發生安全性問題。</span><span class="sxs-lookup"><span data-stu-id="c4632-113">A security issue could occur if you create a receive location that uses the EDIReceive pipeline and has a transport type of HTTP.</span></span> <span data-ttu-id="c4632-114">EDIReceive 管線不會產生 HTTP "200 OK" 通知。</span><span class="sxs-lookup"><span data-stu-id="c4632-114">The EdiReceive pipeline will not generate an HTTP "200 OK" acknowledgment.</span></span> <span data-ttu-id="c4632-115">若並未傳回 EDI 通知，則不會順利終止連線，而是會維持開啟。</span><span class="sxs-lookup"><span data-stu-id="c4632-115">If no EDI acknowledgment is returned, the connection will not be terminated gracefully, but will remain open.</span></span> <span data-ttu-id="c4632-116">如果超過逾時期間，則連線會逾時。</span><span class="sxs-lookup"><span data-stu-id="c4632-116">The connection will time out when the time-out period has expired.</span></span>  
  
 <span data-ttu-id="c4632-117">EDIReceive 管線包含下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="c4632-117">The EDIReceive pipeline consists of the following pipeline components:</span></span>  
  
-   <span data-ttu-id="c4632-118">EDI 解譯器</span><span class="sxs-lookup"><span data-stu-id="c4632-118">EDI Disassembler</span></span>  
  
-   <span data-ttu-id="c4632-119">BatchMarker</span><span class="sxs-lookup"><span data-stu-id="c4632-119">BatchMarker.</span></span>  
  
## <a name="edi-receive-pipeline-components"></a><span data-ttu-id="c4632-120">EDI 接收管線元件</span><span class="sxs-lookup"><span data-stu-id="c4632-120">EDI Receive Pipeline Components</span></span>  
 <span data-ttu-id="c4632-121">EDIReceive 接收管線會使用下列管線元件。</span><span class="sxs-lookup"><span data-stu-id="c4632-121">The EDIReceive pipeline use the following pipeline components.</span></span> <span data-ttu-id="c4632-122">這些元件安裝在中的 microsoft.biztalk.edi.pipelinecomponents.dll 內[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]管線元件\\。</span><span class="sxs-lookup"><span data-stu-id="c4632-122">These components are installed in Microsoft.BizTalk.Edi.PipelineComponents.dll in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Pipeline Components\\.</span></span>  
  
### <a name="edi-disassembler"></a><span data-ttu-id="c4632-123">EDI 解譯器</span><span class="sxs-lookup"><span data-stu-id="c4632-123">EDI Disassembler</span></span>  
 <span data-ttu-id="c4632-124">EDI 解譯器會執行 EDIReceive 管線中針對收到之 EDI 編碼交換的大多數處理作業。</span><span class="sxs-lookup"><span data-stu-id="c4632-124">The EDI Disassembler performs most processing of received EDI-encoded interchanges in the EDIReceive Pipeline.</span></span> <span data-ttu-id="c4632-125">EDI 解譯器如何處理 EDI 訊息的詳細資訊，請參閱[EDI 解譯器的運作方式](../core/how-the-edi-disassembler-works.md)。</span><span class="sxs-lookup"><span data-stu-id="c4632-125">For information about how the EDI Disassembler processes EDI messages, see [How the EDI Disassembler Works](../core/how-the-edi-disassembler-works.md).</span></span>  
  
### <a name="batchmarker"></a><span data-ttu-id="c4632-126">BatchMarker</span><span class="sxs-lookup"><span data-stu-id="c4632-126">BatchMarker</span></span>  
 <span data-ttu-id="c4632-127">BatchMarker 管線元件會準備交換批次處理升級，將批次識別碼，ToBeBatched 和 ToBeRouted 內容屬性所需的處理批次的交換。</span><span class="sxs-lookup"><span data-stu-id="c4632-127">The BatchMarker pipeline component prepares an interchange for batching by promoting the BatchId, ToBeBatched, and ToBeRouted context properties that are required for processing a batched interchange.</span></span> <span data-ttu-id="c4632-128">BatchMarker 元件設定這些屬性的方式，取決於多少交易夥伴協議訂閱批次項目。</span><span class="sxs-lookup"><span data-stu-id="c4632-128">How the BatchMarker component sets these properties depends upon how many trading partner agreements subscribes to the batch element.</span></span>  
  
-   <span data-ttu-id="c4632-129">如果只有一個協議訂閱批次項目，BatchMarker 元件將 ToBeBatched 內容屬性設為 True，如此批次處理協調流程才能收取批次項目。</span><span class="sxs-lookup"><span data-stu-id="c4632-129">If only one agreement subscribes to the batch element, the BatchMarker component sets the ToBeBatched context property to True, so that the batching orchestration picks up the batch element.</span></span>  
  
-   <span data-ttu-id="c4632-130">如果一個以上的協議訂閱批次項目，BatchMarker 元件 ToBeRouted 內容屬性設定為 True，如此路由協調流程才能收取批次項目。</span><span class="sxs-lookup"><span data-stu-id="c4632-130">If more than one agreement subscribes to a batch element, the BatchMarker component sets the ToBeRouted context property to True, so that the routing orchestration picks up the batch element.</span></span> <span data-ttu-id="c4632-131">它也設定 Batchid 內容屬性，以空格分隔批次識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="c4632-131">It also sets the BatchIds context property to a space delimited list of batch IDs.</span></span> <span data-ttu-id="c4632-132">路由協調流程將會讓批次項目的一個複本的每個批次識別碼，然後將 ToBeBatched 屬性設定為 True 的批次項目，每個複本上，讓批次處理協調流程會收取所有複本。</span><span class="sxs-lookup"><span data-stu-id="c4632-132">The routing orchestration will then make one copy of the batch element for each batch ID, and set the ToBeBatched property to True on each copy of the batch element, so that the batching orchestration will pick up all copies.</span></span>  
  
 <span data-ttu-id="c4632-133">BatchMarker 元件會包含在 EDIReceive 管線的最後一個階段 （交易夥伴協議解析）。</span><span class="sxs-lookup"><span data-stu-id="c4632-133">The BatchMarker component is included in the last stage (trading partner agreement resolution) of the EDIReceive pipeline.</span></span> <span data-ttu-id="c4632-134">所有將處理 EDI 訊息的管線都應該包含 BatchMarker 管線元件。</span><span class="sxs-lookup"><span data-stu-id="c4632-134">All pipelines that will process EDI messages should include the BatchMarker pipeline component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4632-135">BatchMarker 元件可以包含在不包含 EDI 解譯器，才能執行交易夥伴協議解析，而不剖析 EDI 訊息的接收管線。</span><span class="sxs-lookup"><span data-stu-id="c4632-135">The BatchMarker component can be included in a receive pipeline that does not include the EDI Dissassembler, in order to perform trading partner agreement resolution without parsing the EDI message.</span></span>  
  
 <span data-ttu-id="c4632-136">您可以使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 BatchMarker 元件來批次處理非 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="c4632-136">You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the BatchMarker component to batch non-EDI messages.</span></span> <span data-ttu-id="c4632-137">如需詳細資訊，請參閱 「 非 EDI 訊息在 BatchMarker 元件處理 > 一節[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。</span><span class="sxs-lookup"><span data-stu-id="c4632-137">For more information, see the "Processing Non-EDI Messages in the BatchMarker Component" section of [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4632-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4632-138">See Also</span></span>  
 [<span data-ttu-id="c4632-139">BizTalk Server 如何接收 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="c4632-139">How BizTalk Server Receives EDI Messages</span></span>](../core/how-biztalk-server-receives-edi-messages.md)