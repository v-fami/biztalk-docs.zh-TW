---
title: "傳送管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines, message flow
- send pipelines, about send pipelines
- messages, message flow
- send pipelines, stages
- pipelines, send pipelines
- messages, send pipelines
ms.assetid: c963b2d8-3b2b-4575-8105-c750deae8189
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef08909dbc47e11f5c9fecae6f65e01dbe79441b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="send-pipelines"></a><span data-ttu-id="91622-102">傳送管線</span><span class="sxs-lookup"><span data-stu-id="91622-102">Send Pipelines</span></span>
<span data-ttu-id="91622-103">下圖顯示訊息處理工作流程，其中會反白傳送管線。</span><span class="sxs-lookup"><span data-stu-id="91622-103">The following figure shows the message processing workflow, highlighting the send pipeline.</span></span>  
  
 <span data-ttu-id="91622-104">![為處理訊息的工作流程的圖表。] (../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")</span><span class="sxs-lookup"><span data-stu-id="91622-104">![Diagram of workflow for processing a message.](../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")</span></span>  
<span data-ttu-id="91622-105">描述訊息處理工作流程。</span><span class="sxs-lookup"><span data-stu-id="91622-105">Depicts the message processing workflow.</span></span>  
  
 <span data-ttu-id="91622-106">傳送管線的責任是必須在傳送文件到最終目的地前先處理文件。</span><span class="sxs-lookup"><span data-stu-id="91622-106">A send pipeline is responsible for processing documents before sending them to their final destinations.</span></span> <span data-ttu-id="91622-107">傳送管線會先取得訊息，然後產生要傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="91622-107">The send pipeline takes one message and produces one message to send.</span></span>  
  
 <span data-ttu-id="91622-108">您可以建立新的傳送管線，或者使用 BizTalk Server 中的兩個預設傳送管線的其中一個—通過傳送管線和 XML 傳送管線。</span><span class="sxs-lookup"><span data-stu-id="91622-108">You can create a new send pipeline or you can use one of the two default send pipelines included in BizTalk Server—the pass-through send pipeline and the XML send pipeline.</span></span>  
  
 <span data-ttu-id="91622-109">依照預設，傳送管線包含三個空白階段：預先組合、組合和編碼。</span><span class="sxs-lookup"><span data-stu-id="91622-109">By default, the send pipeline consists of three empty stages: Pre-assemble, Assemble and Encode.</span></span> <span data-ttu-id="91622-110">此主題包含填入這些階段的設計考量。</span><span class="sxs-lookup"><span data-stu-id="91622-110">This topic contains design considerations for populating these stages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91622-111">當耗用元件新增到某傳送管線時，該傳送管線不會產生訊息。</span><span class="sxs-lookup"><span data-stu-id="91622-111">A send pipeline can produce zero messages when a consuming component is added to the pipeline.</span></span>  
  
## <a name="pre-assemble-stage"></a><span data-ttu-id="91622-112">預先組合階段</span><span class="sxs-lookup"><span data-stu-id="91622-112">Pre-assemble stage</span></span>  
  
-   <span data-ttu-id="91622-113">在訊息經序列化之前，有一些自訂元件必須對訊息執行某些動作，而這個階段就是那些自訂元件的預留位置。</span><span class="sxs-lookup"><span data-stu-id="91622-113">This stage is a placeholder for custom components that should perform some action on the message before the message is serialized.</span></span>  
  
-   <span data-ttu-id="91622-114">每個訊息都會執行一次這個階段。</span><span class="sxs-lookup"><span data-stu-id="91622-114">This stage is run once per message.</span></span>  
  
-   <span data-ttu-id="91622-115">此階段可包含 0 至 255 個元件。</span><span class="sxs-lookup"><span data-stu-id="91622-115">This stage can contain between zero and 255 components.</span></span>  
  
-   <span data-ttu-id="91622-116">此階段中的所有元件都可執行。</span><span class="sxs-lookup"><span data-stu-id="91622-116">All components in this stage are run.</span></span>  
  
## <a name="assemble-stage"></a><span data-ttu-id="91622-117">組合階段</span><span class="sxs-lookup"><span data-stu-id="91622-117">Assemble stage</span></span>  
  
-   <span data-ttu-id="91622-118">此階段之元件的責任是對訊息進行組合或序列化，然後將其轉換為 XML 或從 XML 格式轉換回來。</span><span class="sxs-lookup"><span data-stu-id="91622-118">Components in this stage are responsible for assembling or serializing the message and converting it to or from XML.</span></span>  
  
-   <span data-ttu-id="91622-119">此階段不接受任何元件或只接受一個元件。</span><span class="sxs-lookup"><span data-stu-id="91622-119">This stage accepts zero components or one component.</span></span>  
  
-   <span data-ttu-id="91622-120">此階段中的所有元件都可執行。</span><span class="sxs-lookup"><span data-stu-id="91622-120">All components in this stage are run.</span></span>  
  
## <a name="encode-stage"></a><span data-ttu-id="91622-121">編碼階段</span><span class="sxs-lookup"><span data-stu-id="91622-121">Encode stage</span></span>  
  
-   <span data-ttu-id="91622-122">此階段用於對訊息進行編碼或加密的元件。</span><span class="sxs-lookup"><span data-stu-id="91622-122">This stage is used for components that encode or encrypt the message.</span></span>  
  
    -   <span data-ttu-id="91622-123">若需要訊息簽章，請將 MIME/SMIME 編碼器元件或自訂編碼元件放入此階段。</span><span class="sxs-lookup"><span data-stu-id="91622-123">Place the MIME/SMIME Encoder component or a custom encoding component in this stage if message signing is required.</span></span>  
  
-   <span data-ttu-id="91622-124">每個訊息都會執行一次這個階段。</span><span class="sxs-lookup"><span data-stu-id="91622-124">This stage is run once per message.</span></span>  
  
-   <span data-ttu-id="91622-125">此階段可包含 0 至 255 個元件。</span><span class="sxs-lookup"><span data-stu-id="91622-125">This stage can contain between zero and 255 components.</span></span>  
  
-   <span data-ttu-id="91622-126">此階段中的所有元件都可執行。</span><span class="sxs-lookup"><span data-stu-id="91622-126">All components in this stage are executed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91622-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91622-127">See Also</span></span>  
 <span data-ttu-id="91622-128">[接收管線](../core/receive-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="91622-128">[Receive Pipelines](../core/receive-pipelines.md) </span></span>  
 <span data-ttu-id="91622-129">[關於管線、 階段和元件](../core/about-pipelines-stages-and-components.md) </span><span class="sxs-lookup"><span data-stu-id="91622-129">[About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md) </span></span>  
 <span data-ttu-id="91622-130">[類型的管線](../core/types-of-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="91622-130">[Types of Pipelines](../core/types-of-pipelines.md) </span></span>  
 <span data-ttu-id="91622-131">[預設管線](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="91622-131">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 <span data-ttu-id="91622-132">[管線範本](../core/pipeline-templates.md) </span><span class="sxs-lookup"><span data-stu-id="91622-132">[Pipeline Templates](../core/pipeline-templates.md) </span></span>  
 <span data-ttu-id="91622-133">[管線元件](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="91622-133">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 [<span data-ttu-id="91622-134">類型的管線元件</span><span class="sxs-lookup"><span data-stu-id="91622-134">Types of Pipeline Components</span></span>](../core/types-of-pipeline-components.md)