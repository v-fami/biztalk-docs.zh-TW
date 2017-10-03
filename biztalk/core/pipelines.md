---
title: "管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines
- deploying, pipelines
- receive pipelines, about receive pipelines
- pipelines, deploying
- send pipelines, about send pipelines
- receive pipelines
- pipelines, about pipelines
- send pipelines, stages
- send pipelines
- pipelines, receive pipelines
- pipelines, send pipelines
- receive pipelines, stages
ms.assetid: 76947dd8-728a-4fa3-bd33-7a708ae82cac
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5fec49dcc9ba21c5d117188f280f7e9b65fe2b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pipelines"></a><span data-ttu-id="da8c3-102">管線</span><span class="sxs-lookup"><span data-stu-id="da8c3-102">Pipelines</span></span>
<span data-ttu-id="da8c3-103">管線是 Microsoft BizTalk Server 的一個元件，可實作「管線」和「篩選條件」整合模式。</span><span class="sxs-lookup"><span data-stu-id="da8c3-103">Pipelines are a component of Microsoft BizTalk Server that provides an implementation of the Pipes and Filters integration pattern.</span></span> <span data-ttu-id="da8c3-104">基於商務因素，在接收和傳送訊息期間，會對訊息執行轉換以準備進入或離開 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="da8c3-104">During the receiving and sending of messages, there are business reasons to perform transformations on messages to prepare them to enter or leave BizTalk Server.</span></span>  
  
 <span data-ttu-id="da8c3-105">常見範例是您需要將逗號分隔的一般檔案轉換成 XML 檔，才能利用 BizTalk Server 的特定功能，像是對應；一般檔案解譯器元件就是以此方式執行。</span><span class="sxs-lookup"><span data-stu-id="da8c3-105">A common example is that you may need to transform a comma-delimited flat file into an XML file in order to take advantage of certain features in BizTalk Server such as maps; the flat file disassembler component does just that.</span></span> <span data-ttu-id="da8c3-106">在接收或傳送訊息之前，需要對訊息執行數種轉換的情況，在整合實例中很常見；而管線可用以滿足此項需求。</span><span class="sxs-lookup"><span data-stu-id="da8c3-106">It is common in integration scenarios to have a need to perform several types of transformations to a message before receiving or sending it; pipelines are used to meet this requirement.</span></span> <span data-ttu-id="da8c3-107">開發人員可以使用管線定義一系列轉換，以在接收或傳送訊息時執行。</span><span class="sxs-lookup"><span data-stu-id="da8c3-107">Pipelines enable the developer to define a series of transformations that will be performed on a message as it is being received or sent.</span></span>  
  
 <span data-ttu-id="da8c3-108">管線有傳送和接收兩種類型，而且與它們執行所在的連接埠相符。</span><span class="sxs-lookup"><span data-stu-id="da8c3-108">There are two types of pipelines, send and receive, and these match the ports in which they execute.</span></span> <span data-ttu-id="da8c3-109">*傳送管線*執行在傳送埠和要求/回應的回應部分中接收埠，而*接收管線*執行在接收位置和請求/回應的回應部分中傳送埠。</span><span class="sxs-lookup"><span data-stu-id="da8c3-109">*Send pipelines* are executed in send ports and in the response portion of a request/response receive port, while *receive pipelines* are executed in receive locations, and in the response portion of a solicit/response send port.</span></span> <span data-ttu-id="da8c3-110">基本上，接收管線是用於轉換要發佈到 MessageBox 資料庫的訊息，而傳送管線是用於已訂閱和要送出 BizTalk Server 的訊息。</span><span class="sxs-lookup"><span data-stu-id="da8c3-110">Essentially, receive pipelines are intended to be used to transform messages that are being published to the MessageBox database, while send pipelines are intended to be used on messages which have been subscribed to and are being sent out of BizTalk Server.</span></span>  
  
 <span data-ttu-id="da8c3-111">每個管線執行時，都會依序執行數個階段。</span><span class="sxs-lookup"><span data-stu-id="da8c3-111">Each pipeline has a set of stages that are executed in order when the pipeline is executed.</span></span> <span data-ttu-id="da8c3-112">每一個階段可以包含零或多個元件。</span><span class="sxs-lookup"><span data-stu-id="da8c3-112">Each stage can contain zero or more components.</span></span> <span data-ttu-id="da8c3-113">元件數目的上限依據各個階段而定。</span><span class="sxs-lookup"><span data-stu-id="da8c3-113">The maximum number of components depends on the stage.</span></span>  
  
## <a name="receive-pipeline-stages"></a><span data-ttu-id="da8c3-114">接收管線階段</span><span class="sxs-lookup"><span data-stu-id="da8c3-114">Receive Pipeline Stages</span></span>  
 <span data-ttu-id="da8c3-115">![接收管線階段](../core/media/arch-pipe-receive.gif "arch_pipe_receive")</span><span class="sxs-lookup"><span data-stu-id="da8c3-115">![Receive pipeline stages](../core/media/arch-pipe-receive.gif "arch_pipe_receive")</span></span>  
  
|<span data-ttu-id="da8c3-116">階段</span><span class="sxs-lookup"><span data-stu-id="da8c3-116">Stage</span></span>|<span data-ttu-id="da8c3-117">目的</span><span class="sxs-lookup"><span data-stu-id="da8c3-117">Purpose</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="da8c3-118">**解碼**</span><span class="sxs-lookup"><span data-stu-id="da8c3-118">**Decode**</span></span>|<span data-ttu-id="da8c3-119">將訊息資料解密或解碼</span><span class="sxs-lookup"><span data-stu-id="da8c3-119">Decrypts or decodes the message data</span></span>|  
|<span data-ttu-id="da8c3-120">**反組譯**</span><span class="sxs-lookup"><span data-stu-id="da8c3-120">**Disassemble**</span></span>|<span data-ttu-id="da8c3-121">將交換解譯為較小的訊息並剖析訊息內容</span><span class="sxs-lookup"><span data-stu-id="da8c3-121">Disassembles an interchange into smaller messages and parses message contents</span></span>|  
|<span data-ttu-id="da8c3-122">**Validate**</span><span class="sxs-lookup"><span data-stu-id="da8c3-122">**Validate**</span></span>|<span data-ttu-id="da8c3-123">通常會針對結構描述驗證訊息資料</span><span class="sxs-lookup"><span data-stu-id="da8c3-123">Validates the message data, generally against a schema</span></span>|  
|<span data-ttu-id="da8c3-124">**解析合作對象**</span><span class="sxs-lookup"><span data-stu-id="da8c3-124">**Resolve Party**</span></span>|<span data-ttu-id="da8c3-125">識別與訊息或訊息內容中某個安全性 Token 相關聯的 BizTalk Server 合作對象</span><span class="sxs-lookup"><span data-stu-id="da8c3-125">Identifies the BizTalk Server party associated with some security token in the message or message context</span></span>|  
  
## <a name="send-pipeline-stages"></a><span data-ttu-id="da8c3-126">傳送管線階段</span><span class="sxs-lookup"><span data-stu-id="da8c3-126">Send Pipeline Stages</span></span>  
 <span data-ttu-id="da8c3-127">![傳送管線階段](../core/media/arch-pipe-send.gif "arch_pipe_send")</span><span class="sxs-lookup"><span data-stu-id="da8c3-127">![Send pipeline stages](../core/media/arch-pipe-send.gif "arch_pipe_send")</span></span>  
  
|<span data-ttu-id="da8c3-128">階段</span><span class="sxs-lookup"><span data-stu-id="da8c3-128">Stage</span></span>|<span data-ttu-id="da8c3-129">目的</span><span class="sxs-lookup"><span data-stu-id="da8c3-129">Purpose</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="da8c3-130">**預先組合**</span><span class="sxs-lookup"><span data-stu-id="da8c3-130">**Pre-assemble**</span></span>|<span data-ttu-id="da8c3-131">在組合訊息之前執行任何必要的訊息處理</span><span class="sxs-lookup"><span data-stu-id="da8c3-131">Performs any message processing necessary before assembling the message</span></span>|  
|<span data-ttu-id="da8c3-132">**組合**</span><span class="sxs-lookup"><span data-stu-id="da8c3-132">**Assemble**</span></span>|<span data-ttu-id="da8c3-133">組合訊息並採取步驟以準備傳送訊息，例如加上信封、將 XML 轉換成一般檔案，或可與接收管線的解譯階段互補的其他工作。</span><span class="sxs-lookup"><span data-stu-id="da8c3-133">Assembles the message and prepares it to be transmitted by taking steps such as adding envelopes, converting XML to flat files, or other tasks complementary to the disassemble stage in a receive pipeline</span></span>|  
|<span data-ttu-id="da8c3-134">**編碼**</span><span class="sxs-lookup"><span data-stu-id="da8c3-134">**Encode**</span></span>|<span data-ttu-id="da8c3-135">在傳遞之前將訊息編碼或加密</span><span class="sxs-lookup"><span data-stu-id="da8c3-135">Encodes or encrypts the message before delivery</span></span>|  
  
 <span data-ttu-id="da8c3-136">在管線階段會有*執行模式*「 全部或第一個相符項目，以控制如果多個元件新增至階段執行的元件。</span><span class="sxs-lookup"><span data-stu-id="da8c3-136">A stage in a pipeline has an *execution mode* of either All or First Match, which controls the components that get executed if more than one component is added to a stage.</span></span> <span data-ttu-id="da8c3-137">對於「全部」模式的階段，會呼叫每個元件以階段中設定的順序來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="da8c3-137">For stages with a mode of All, each component is called to process the message in the order in which they are configured in the stage.</span></span> <span data-ttu-id="da8c3-138">當模式為「第一個符合」時，會輪詢每個元件以指示其是否為正確的元件，直到找到相符的為止，而當下也會執行該相符元件，而不會執行其餘元件。</span><span class="sxs-lookup"><span data-stu-id="da8c3-138">When the mode is First Match, each component is polled to indicate that it is the right component until a match is found, at which point the component that matches is executed, while the remaining components do not get executed.</span></span>  
  
 <span data-ttu-id="da8c3-139">例如此執行模式範例，接收管線的「解譯」階段為「第一個符合」階段，因此會呼叫階段中的每個元件，以查看是否能辨識該訊息並加以處理。</span><span class="sxs-lookup"><span data-stu-id="da8c3-139">As an example of execution modes, the Disassemble stage of a receive pipeline is a First Match stage, thus each component in the stage is called to see if it recognizes the message and can process it.</span></span> <span data-ttu-id="da8c3-140">若某個元件正面回應，便不會再查詢該階段內的其他元件是否也能處理該訊息。</span><span class="sxs-lookup"><span data-stu-id="da8c3-140">If the component responds in the affirmative, then no other components in that stage are queried to see if they can also handle the message.</span></span> <span data-ttu-id="da8c3-141">但接收管線的「解碼」階段為「全部」執行模式時，表示會以設定的順序呼叫此階段中的每個元件來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="da8c3-141">However, the Decode stage of a receive pipeline has an execution mode of All, meaning that each component in this stage is called to process the message in the order in which they were configured.</span></span> <span data-ttu-id="da8c3-142">第一個解碼器可能用來加密訊息，而第二個可能將訊息從壓縮的格式解壓縮。</span><span class="sxs-lookup"><span data-stu-id="da8c3-142">The first decoder might be to decrypt the message, while the second might be to decompress the message from a zipped format.</span></span>  
  
 <span data-ttu-id="da8c3-143">開發人員想要在單一接收管線中使用多個解譯器時，一般會在管線處理中使用執行模式。</span><span class="sxs-lookup"><span data-stu-id="da8c3-143">One common consequence of execution mode in pipeline processing occurs when a developer wants to use multiple disassemblers in a single receive pipeline.</span></span> <span data-ttu-id="da8c3-144">解譯元件通常只有些許不同，例如，兩個類似但結構描述設定不同的一般檔案解譯器。</span><span class="sxs-lookup"><span data-stu-id="da8c3-144">Often the disassembling components differ only slightly, for example two flat file disassemblers with similar but different schemas configured.</span></span> <span data-ttu-id="da8c3-145">在這種情況下，雖然訊息實際上可能會與第二個解譯器中定義的結構描述相符，但第一個解譯器則要透過探查來判定是否能夠處理該訊息。</span><span class="sxs-lookup"><span data-stu-id="da8c3-145">In this case, while the message might actually match the schema defined in the second disassembler, the first disassembler might determine through its probing that it can process the message.</span></span> <span data-ttu-id="da8c3-146">只有在處理訊息之後，才能找出錯誤和擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="da8c3-146">It is only after processing the message that the error is discovered and the message suspended.</span></span> <span data-ttu-id="da8c3-147">在這些情況下，您可能會建立探查邏輯更為明確的新解譯器，或是建立兩個不同的管線，並在不同的接收位置接收不同的訊息。</span><span class="sxs-lookup"><span data-stu-id="da8c3-147">In these cases, you can either create a new disassembler which has more specific probing logic in it, or create two different pipelines and receive the different messages in different receive locations.</span></span>  
  
## <a name="pipeline-deployment"></a><span data-ttu-id="da8c3-148">管線部署</span><span class="sxs-lookup"><span data-stu-id="da8c3-148">Pipeline Deployment</span></span>  
 <span data-ttu-id="da8c3-149">部署包含管線的組件時，管理資料庫會儲存管線。</span><span class="sxs-lookup"><span data-stu-id="da8c3-149">When you deploy an assembly that contains a pipeline, the Management database saves the pipeline.</span></span> <span data-ttu-id="da8c3-150">管線與特定組件版本產生關聯的結果如下：</span><span class="sxs-lookup"><span data-stu-id="da8c3-150">The pipeline is associated with the specific version of the assembly with the following results:</span></span>  
  
-   <span data-ttu-id="da8c3-151">若部署使用相同管線的多個組件，管理資料庫會為每個組件的管線各建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="da8c3-151">If you deploy multiple assemblies that use the same pipeline, the Management database creates one entry for the pipeline for each assembly.</span></span>  
  
-   <span data-ttu-id="da8c3-152">移除包含管線的組件時，管理資料庫會同時移除與該組件相關聯的管線。</span><span class="sxs-lookup"><span data-stu-id="da8c3-152">When you remove an assembly that contains a pipeline, the Management database removes the pipeline that is associated with the assembly.</span></span> <span data-ttu-id="da8c3-153">因為管理資料庫中有每個相關聯組件的管線複本，所以移除一個組件不會影響其他組件。</span><span class="sxs-lookup"><span data-stu-id="da8c3-153">Because there is a copy of the pipeline for each associated assembly in the Management database, removing one assembly does not affect the others.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da8c3-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da8c3-154">See Also</span></span>  
 [<span data-ttu-id="da8c3-155">成品</span><span class="sxs-lookup"><span data-stu-id="da8c3-155">Artifacts</span></span>](../core/artifacts.md)