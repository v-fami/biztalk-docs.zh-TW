---
title: 接收管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive pipelines, about receive pipelines
- receive pipelines, message flow
- receive pipelines
- messages, receive pipelines
- messages, message flow
- pipelines, receive pipelines
- receive pipelines, stages
ms.assetid: ee75c1d4-00b7-4177-bca3-1447a39d2238
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0a248c69cb96603e9c4883e5d21caa39165da13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268862"
---
# <a name="receive-pipelines"></a><span data-ttu-id="53b53-102">接收管線</span><span class="sxs-lookup"><span data-stu-id="53b53-102">Receive Pipelines</span></span>
<span data-ttu-id="53b53-103">下圖顯示訊息處理工作流程，並以反白顯示接收管線。</span><span class="sxs-lookup"><span data-stu-id="53b53-103">The following figure shows the message processing workflow, highlighting the receive pipeline.</span></span>  
  
 <span data-ttu-id="53b53-104">![訊息處理工作流程的圖表。](../core/media/ebiz-dev-busprcsb.gif "ebiz_dev_busprcsb")</span><span class="sxs-lookup"><span data-stu-id="53b53-104">![Diagram of the message processing workflow.](../core/media/ebiz-dev-busprcsb.gif "ebiz_dev_busprcsb")</span></span>  
<span data-ttu-id="53b53-105">描述訊息處理工作流程。</span><span class="sxs-lookup"><span data-stu-id="53b53-105">Depicts the message processing workflow.</span></span>  
  
 <span data-ttu-id="53b53-106">在接收配接器收到訊息之後，接收管線會在訊息上作業。</span><span class="sxs-lookup"><span data-stu-id="53b53-106">A receive pipeline operates on a message after it is received by the receive adapter.</span></span> <span data-ttu-id="53b53-107">接收管線取得初始訊息，執行部分轉換，然後將原始資料解譯成零個、一個或多個訊息。</span><span class="sxs-lookup"><span data-stu-id="53b53-107">The receive pipeline takes the initial message, performs some transformations, and disassembles the raw data into zero, one, or multiple messages.</span></span> <span data-ttu-id="53b53-108">然後，BizTalk Server 可以處理這些個別訊息。</span><span class="sxs-lookup"><span data-stu-id="53b53-108">These individual messages can then be processed by BizTalk Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53b53-109">若將耗用元件加入管線中，則接收管線可產生零個訊息。</span><span class="sxs-lookup"><span data-stu-id="53b53-109">A receive pipeline can produce zero messages if a consuming component is added to the pipeline.</span></span> <span data-ttu-id="53b53-110">此時，管線元件將取用訊息，而不會產生任何輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="53b53-110">In this case, the pipeline component consumes the message and does not produce any output messages.</span></span> <span data-ttu-id="53b53-111">若耗用元件放在解譯元件之後，則管線會在取用第一個訊息之後停止執行，且不會從解譯元件擷取後續的訊息。</span><span class="sxs-lookup"><span data-stu-id="53b53-111">If a consuming component is placed after a disassembling component, pipeline execution stops after the first message is consumed and no subsequent messages are retrieved from the disassembling component.</span></span>  
  
 <span data-ttu-id="53b53-112">在建立商務程序時，您可以建立新接收管線，或使用 BizTalk Server 所包含的兩個預設接收管線之一：通過接收管線或 XML 接收管線。</span><span class="sxs-lookup"><span data-stu-id="53b53-112">When creating a business process, you can create a new receive pipeline or you can use one of the two default receive pipelines included in BizTalk Server—the pass-through receive pipeline or the XML receive pipeline.</span></span> <span data-ttu-id="53b53-113">如需有關這些預設管線的詳細資訊，請參閱[預設管線](../core/default-pipelines.md)。</span><span class="sxs-lookup"><span data-stu-id="53b53-113">For more information about these default pipelines, see [Default Pipelines](../core/default-pipelines.md).</span></span>  
  
 <span data-ttu-id="53b53-114">接收管線包含四個階段：解碼、解譯、驗證以及解析合作對象。</span><span class="sxs-lookup"><span data-stu-id="53b53-114">The receive pipeline consists of four stages: Decode, Disassemble, Validate, and ResolveParty.</span></span> <span data-ttu-id="53b53-115">此主題包含填入這些階段的設計考量。</span><span class="sxs-lookup"><span data-stu-id="53b53-115">This topic contains design considerations for populating these stages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53b53-116">在此版本中，不支援在管線中變更這些階段的順序或顯示。</span><span class="sxs-lookup"><span data-stu-id="53b53-116">In this release, changing the order or presence of these stages in a pipeline is not supported.</span></span>  
  
## <a name="decode-stage"></a><span data-ttu-id="53b53-117">解碼階段</span><span class="sxs-lookup"><span data-stu-id="53b53-117">Decode stage</span></span>  
  
-   <span data-ttu-id="53b53-118">此階段供解碼或解密訊息的元件使用。</span><span class="sxs-lookup"><span data-stu-id="53b53-118">This stage is used for components that decode or decrypt the message.</span></span>  
  
    -   <span data-ttu-id="53b53-119">若內送訊息需要從某一格式解碼成另一格式，則 [MIME/SMIME 解碼器] 管線元件或自訂解碼元件應放在此階段。</span><span class="sxs-lookup"><span data-stu-id="53b53-119">The MIME/SMIME Decoder pipeline component or a custom decoding component should be placed in this stage if the incoming messages need to be decoded from one format to another.</span></span>  
  
-   <span data-ttu-id="53b53-120">此階段取得一個訊息，然後產生一個訊息。</span><span class="sxs-lookup"><span data-stu-id="53b53-120">This stage takes one message and produces one message.</span></span>  
  
-   <span data-ttu-id="53b53-121">此階段可包含 0 至 255 個元件。</span><span class="sxs-lookup"><span data-stu-id="53b53-121">This stage can contain between zero and 255 components.</span></span>  
  
-   <span data-ttu-id="53b53-122">此階段中的所有元件都可執行。</span><span class="sxs-lookup"><span data-stu-id="53b53-122">All components in this stage are run.</span></span>  
  
## <a name="disassemble-stage"></a><span data-ttu-id="53b53-123">解譯階段</span><span class="sxs-lookup"><span data-stu-id="53b53-123">Disassemble stage</span></span>  
  
-   <span data-ttu-id="53b53-124">此階段供剖析或解譯訊息的元件使用。</span><span class="sxs-lookup"><span data-stu-id="53b53-124">This stage is used for components that parse or disassemble the message.</span></span>  
  
    -   <span data-ttu-id="53b53-125">此階段中的元件會探查訊息，以確認是否可辨識此訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="53b53-125">The components within this stage probe the message to see if the format of the message is recognized.</span></span> <span data-ttu-id="53b53-126">根據格式的辨識結果，其中一個元件將解譯訊息。</span><span class="sxs-lookup"><span data-stu-id="53b53-126">Based on the recognition of the format, one of the components disassembles the message.</span></span>  
  
    -   <span data-ttu-id="53b53-127">若此階段包含一個以上的元件，則只會執行辨識出訊息的第一個元件。</span><span class="sxs-lookup"><span data-stu-id="53b53-127">If this stage contains more than one component, only the first component that recognizes the message format is run.</span></span> <span data-ttu-id="53b53-128">若階段中沒有元件可辨識訊息格式，則訊息處理失敗。</span><span class="sxs-lookup"><span data-stu-id="53b53-128">If none of the components within the stage recognize the message format, the message processing fails.</span></span>  
  
    -   <span data-ttu-id="53b53-129">此階段應包含實作特殊行為以解譯訊息內容的任一自訂元件。</span><span class="sxs-lookup"><span data-stu-id="53b53-129">This stage should include any custom components that implement special behavior to disassemble the message contents.</span></span>  
  
    -   <span data-ttu-id="53b53-130">此階段可包含 0 至 255 個元件。</span><span class="sxs-lookup"><span data-stu-id="53b53-130">This stage can contain between zero and 255 components.</span></span> <span data-ttu-id="53b53-131">若此階段中沒有元件，則訊息會直接通過。</span><span class="sxs-lookup"><span data-stu-id="53b53-131">If there are no components in the stage, the message is passed through.</span></span>  
  
## <a name="validate-stage"></a><span data-ttu-id="53b53-132">驗證階段</span><span class="sxs-lookup"><span data-stu-id="53b53-132">Validate stage</span></span>  
  
-   <span data-ttu-id="53b53-133">此階段供驗證訊息格式的元件使用。</span><span class="sxs-lookup"><span data-stu-id="53b53-133">This stage is used for components that validate the message format.</span></span>  
  
    -   <span data-ttu-id="53b53-134">管線元件只處理符合該元件中指定的結構描述的訊息。</span><span class="sxs-lookup"><span data-stu-id="53b53-134">A pipeline component processes only messages that conform to the schemas specified in that component.</span></span> <span data-ttu-id="53b53-135">若管線接收到其結構描述與管線中任何元件都無關聯的訊息，則不會處理該訊息。</span><span class="sxs-lookup"><span data-stu-id="53b53-135">If a pipeline receives a message whose schema is not associated with any component in the pipeline, that message is not processed.</span></span> <span data-ttu-id="53b53-136">根據提交訊息的配接器的不同，訊息將被擱置或發出錯誤給寄件者。</span><span class="sxs-lookup"><span data-stu-id="53b53-136">Depending on the adapter that submits the message, the message is either suspended or an error is issued to the sender.</span></span>  
  
    -   <span data-ttu-id="53b53-137">此階段中的元件可用來驗證解譯階段所產生的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="53b53-137">Components in this stage are used to validate the XML messages produced by the Disassemble stage.</span></span> <span data-ttu-id="53b53-138">此階段中的元件會指定執行 XML 驗證的結構描述。</span><span class="sxs-lookup"><span data-stu-id="53b53-138">Components in this stage specify schemas to perform the XML validation.</span></span>  
  
-   <span data-ttu-id="53b53-139">此階段可包含 0 至 255 個元件。</span><span class="sxs-lookup"><span data-stu-id="53b53-139">This stage can contain between zero and 255 components.</span></span>  
  
-   <span data-ttu-id="53b53-140">此階段中的所有元件都可執行。</span><span class="sxs-lookup"><span data-stu-id="53b53-140">All components in this stage are run.</span></span>  
  
    -   <span data-ttu-id="53b53-141">此階段可執行一次以上。</span><span class="sxs-lookup"><span data-stu-id="53b53-141">This stage may be run more than once.</span></span> <span data-ttu-id="53b53-142">它會為解譯階段所建立的每個訊息執行一次。</span><span class="sxs-lookup"><span data-stu-id="53b53-142">It runs once per message created by the Disassemble stage.</span></span>  
  
## <a name="resolveparty-stage"></a><span data-ttu-id="53b53-143">解析合作對象階段</span><span class="sxs-lookup"><span data-stu-id="53b53-143">ResolveParty stage</span></span>  
  
-   <span data-ttu-id="53b53-144">這個階段是預留位置[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="53b53-144">This stage is a placeholder for the [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).</span></span>  
  
-   <span data-ttu-id="53b53-145">此階段可執行一次以上。</span><span class="sxs-lookup"><span data-stu-id="53b53-145">This stage may be run more than once.</span></span> <span data-ttu-id="53b53-146">它會為解譯階段所建立的每個訊息執行一次。</span><span class="sxs-lookup"><span data-stu-id="53b53-146">It runs once per message created by the Disassemble stage.</span></span>  
  
-   <span data-ttu-id="53b53-147">此階段可包含 0 至 255 個元件。</span><span class="sxs-lookup"><span data-stu-id="53b53-147">This stage can contain between zero and 255 components.</span></span>  
  
-   <span data-ttu-id="53b53-148">此階段中的所有元件都可執行。</span><span class="sxs-lookup"><span data-stu-id="53b53-148">All components in this stage are run.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b53-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53b53-149">See Also</span></span>  
 <span data-ttu-id="53b53-150">[傳送管線](../core/send-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="53b53-150">[Send Pipelines](../core/send-pipelines.md) </span></span>  
 <span data-ttu-id="53b53-151">[關於管線、 階段和元件](../core/about-pipelines-stages-and-components.md) </span><span class="sxs-lookup"><span data-stu-id="53b53-151">[About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md) </span></span>  
 <span data-ttu-id="53b53-152">[類型的管線元件](../core/types-of-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="53b53-152">[Types of Pipeline Components](../core/types-of-pipeline-components.md) </span></span>  
 <span data-ttu-id="53b53-153">[預設管線](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="53b53-153">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 <span data-ttu-id="53b53-154">[管線範本](../core/pipeline-templates.md) </span><span class="sxs-lookup"><span data-stu-id="53b53-154">[Pipeline Templates](../core/pipeline-templates.md) </span></span>  
 <span data-ttu-id="53b53-155">[管線元件](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="53b53-155">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 [<span data-ttu-id="53b53-156">類型的管線</span><span class="sxs-lookup"><span data-stu-id="53b53-156">Types of Pipelines</span></span>](../core/types-of-pipelines.md)