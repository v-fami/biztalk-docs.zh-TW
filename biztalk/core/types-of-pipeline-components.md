---
title: 類型的管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, components
ms.assetid: 9b493758-6b0f-4223-94bb-8f077ee735a9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9ba18aed137380f6b3d491ad52cfcee94bf111a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="types-of-pipeline-components"></a><span data-ttu-id="e8ccb-102">類型的管線元件</span><span class="sxs-lookup"><span data-stu-id="e8ccb-102">Types of Pipeline Components</span></span>
<span data-ttu-id="e8ccb-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含三種管線元件類型：一般、組合和解譯。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-103">Three types of pipeline components are included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]: general, assembling, and disassembling.</span></span> <span data-ttu-id="e8ccb-104">這三種類型也能實作探查功能。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-104">Any of these three types can also implement probing functionality.</span></span> <span data-ttu-id="e8ccb-105">此主題描述每種元件類型以及通常會使用各個元件的階段。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-105">This topic describes each type of component and the stages in which each component is generally used.</span></span>  
  
## <a name="general"></a><span data-ttu-id="e8ccb-106">一般</span><span class="sxs-lookup"><span data-stu-id="e8ccb-106">General</span></span>  
 <span data-ttu-id="e8ccb-107">一般元件會取得一個訊息、處理該訊息，然後產生零或一個訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-107">General components take one message, process the message, and produce zero or one message.</span></span>  
  
 <span data-ttu-id="e8ccb-108">一般元件包含 MIME/SMIME 解碼器、MIME/SMIME 編碼器、合作對象解析以及驗證器元件。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-108">The MIME/SMIME Decoder, MIME/SMIME Encoder, Party Resolution, and Validator components are the included general components.</span></span> <span data-ttu-id="e8ccb-109">您可能必須在傳送之前建立自訂的一般元件以壓縮訊息大小，或是在等待其他資訊以處理訊息時使用該訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-109">You may need to create custom general components to compress the size of a message before sending, or to consume a message while waiting for additional information to process it.</span></span>  
  
 <span data-ttu-id="e8ccb-110">一般元件應置於解碼、編碼、預先組合、合作對象解析與驗證階段。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-110">General components should be placed in the Decode, Encode, Pre-assemble, ResolveParty, or Validate stages.</span></span>  
  
 <span data-ttu-id="e8ccb-111">如需開發一般管線元件的詳細資訊，請參閱[開發一般管線元件](../core/developing-a-general-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-111">For information about developing general pipeline components, see [Developing a General Pipeline Component](../core/developing-a-general-pipeline-component.md).</span></span>  
  
## <a name="assembling"></a><span data-ttu-id="e8ccb-112">組合</span><span class="sxs-lookup"><span data-stu-id="e8ccb-112">Assembling</span></span>  
 <span data-ttu-id="e8ccb-113">組合元件負責多項責任以準備要傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-113">Assembling components have numerous responsibilities to prepare the message to be sent.</span></span> <span data-ttu-id="e8ccb-114">首先，元件會根據結構描述中設定的組合器與屬性，將 XML 訊息轉換成適當的 XML 或非 XML 原生格式訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-114">First, the component converts the XML message to the appropriate XML or non-XML native format of the message, based on the type of assembler and properties set in the schema.</span></span> <span data-ttu-id="e8ccb-115">此外，組合元件還會組合和包裝信封中的訊息，或將標頭或結尾 (或兩者) 新增至訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-115">In addition, assembling components assemble and wrap the message in an envelope, or add a header or trailer (or both) to the message.</span></span> <span data-ttu-id="e8ccb-116">在組合期間，部分屬性會從訊息內容移至文件內文或信封。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-116">During assembly, some properties are moved from the message context to the body of the document or to the envelope.</span></span>  
  
 <span data-ttu-id="e8ccb-117">BizTalk Framework 組合器、一般檔案組合器以及 XML 組合器元件都是預設的組合元件。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-117">The BizTalk Framework Assembler, Flat File Assembler, and XML Assembler components are the default assembling components.</span></span>  
  
 <span data-ttu-id="e8ccb-118">組合元件應置於傳送管線的組合階段。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-118">Assembling components should be placed in the Assemble stage of send pipelines.</span></span>  
  
 <span data-ttu-id="e8ccb-119">如需開發組合管線元件的詳細資訊，請參閱[開發組合管線元件](../core/developing-an-assembling-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-119">For information about developing assembling pipeline components, see [Developing an Assembling Pipeline Component](../core/developing-an-assembling-pipeline-component.md).</span></span>  
  
## <a name="disassembling"></a><span data-ttu-id="e8ccb-120">解譯</span><span class="sxs-lookup"><span data-stu-id="e8ccb-120">Disassembling</span></span>  
 <span data-ttu-id="e8ccb-121">解譯元件會根據要在 BizTalk Server 內使用的信封與文件結構描述，完成許多工作以準備將訊息分割成個別的文件。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-121">Disassembling components complete many tasks to prepare the message to be split up into individual documents according to envelope and document schemas for use within BizTalk Server.</span></span> <span data-ttu-id="e8ccb-122">首先，解譯元件可將非 XML 訊息轉換成 XML 表示法，這是供 BizTalk Server 處理的必要條件。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-122">First, the disassembling component may convert non-XML messages into their XML representation, which is required for processing by BizTalk Server.</span></span> <span data-ttu-id="e8ccb-123">接下來，會將訊息解譯為可傳送給不同協調流程的單一訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-123">Next, the message is disassembled into singular messages that can be sent to separate orchestrations.</span></span> <span data-ttu-id="e8ccb-124">解譯訊息是藉由移除信封、根據信封及訊息結構描述將訊息分割成個別文件，然後將屬性從信封移至個別訊息內容。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-124">The message is disassembled by removing the envelope, splitting the message up into individual documents according to envelope and message schemas, and then moving properties from the envelope to the individual message contexts.</span></span> <span data-ttu-id="e8ccb-125">此外，部分屬性可能會從訊息內文升級成標頭。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-125">Additionally, some properties may be promoted from the body of the message to the header.</span></span> <span data-ttu-id="e8ccb-126">升級的屬性是由結構描述所決定。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-126">The promoted properties are determined by the schema.</span></span>  
  
 <span data-ttu-id="e8ccb-127">解譯元件還必須設定訊息類型屬性，以便用於適當地路由訊息。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-127">The disassembling component must also set the message type property, which is used for routing messages appropriately.</span></span> <span data-ttu-id="e8ccb-128">訊息類型屬性是訊息內文的 Namespace#RootElement。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-128">The message type property is the Namespace#RootElement of the message body.</span></span> <span data-ttu-id="e8ccb-129">其他屬性如內容類型與字元集等都會設為內容屬性的一部分。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-129">Other properties, such as the content type and character set are set as part of the context property.</span></span>  
  
 <span data-ttu-id="e8ccb-130">BizTalk Framework 解譯器 」、 「 一般檔案解譯器 」 和 「 XML 解譯器元件會解譯元件隨附於 BizTalk Server 的預設值。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-130">The BizTalk Framework Disassembler, Flat File Disassembler, and XML Disassembler components are the default disassembling components included with BizTalk Server.</span></span>  
  
 <span data-ttu-id="e8ccb-131">解譯元件應該用於接收管線的解譯階段。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-131">Disassembling components should be used in the Disassemble stage of receive pipelines.</span></span>  
  
 <span data-ttu-id="e8ccb-132">如需開發解譯管線元件的詳細資訊，請參閱[開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-132">For information about developing disassembling pipeline components, see [Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md).</span></span>  
  
## <a name="probing"></a><span data-ttu-id="e8ccb-133">探查</span><span class="sxs-lookup"><span data-stu-id="e8ccb-133">Probing</span></span>  
 <span data-ttu-id="e8ccb-134">探查元件會檢查訊息的第一個部分，查看它是否使用元件可辨識的格式。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-134">A probing component checks the first portion of the message to see if it is in a format that the component understands.</span></span> <span data-ttu-id="e8ccb-135">若為已知的格式，則會將整個訊息傳送給此元件進行處理。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-135">If the format is known, the whole message is given to this component for processing.</span></span>  
  
 <span data-ttu-id="e8ccb-136">如需有關開發探查管線元件，請參閱[開發探查管線元件](../core/developing-a-probing-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ccb-136">For information about developing probing pipeline components, see [Developing a Probing Pipeline Component](../core/developing-a-probing-pipeline-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ccb-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8ccb-137">See Also</span></span>  
 <span data-ttu-id="e8ccb-138">[類型的管線](../core/types-of-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="e8ccb-138">[Types of Pipelines](../core/types-of-pipelines.md) </span></span>  
 <span data-ttu-id="e8ccb-139">[預設管線](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="e8ccb-139">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 <span data-ttu-id="e8ccb-140">[管線範本](../core/pipeline-templates.md) </span><span class="sxs-lookup"><span data-stu-id="e8ccb-140">[Pipeline Templates](../core/pipeline-templates.md) </span></span>  
 <span data-ttu-id="e8ccb-141">[管線元件](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="e8ccb-141">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 [<span data-ttu-id="e8ccb-142">關於管線、 階段和元件</span><span class="sxs-lookup"><span data-stu-id="e8ccb-142">About Pipelines, Stages, and Components</span></span>](../core/about-pipelines-stages-and-components.md)