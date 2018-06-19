---
title: 管線 （BizTalk Server 範例資料夾） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, examples
- SDK examples
- examples, pipelines
ms.assetid: d1b6d984-ac0d-4149-99fd-93d3b6ed316c
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ec02e774255a9574301a0a59f33fb989b8d0f09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264878"
---
# <a name="pipelines-biztalk-server-samples-folder"></a><span data-ttu-id="007ae-102">管線 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="007ae-102">Pipelines (BizTalk Server Samples Folder)</span></span>
<span data-ttu-id="007ae-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的軟體開發套件 (SDK) 中包含數個管線範例。</span><span class="sxs-lookup"><span data-stu-id="007ae-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes several pipeline samples in its software development kit (SDK).</span></span> <span data-ttu-id="007ae-104">本節會針對每個管線範例所展示功能、可用來建置和執行範例的指示以及您可以預期的結果，提供詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="007ae-104">This section provides detailed information about the functionality that each pipeline sample demonstrates, instructions for building and running the sample, and the results you can expect.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="007ae-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="007ae-105">In This Section</span></span>  
  
-   <span data-ttu-id="007ae-106">[彙總工具 （BizTalk Server 範例）](../core/aggregator-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-106">[Aggregator (BizTalk Server Sample)](../core/aggregator-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-107">示範使用協調流程和管線的訊息彙總功能。</span><span class="sxs-lookup"><span data-stu-id="007ae-107">Demonstrates message aggregation functionality using orchestrations and pipelines.</span></span>  
  
-   <span data-ttu-id="007ae-108">[任意 XPath 屬性處理常式 （BizTalk Server 範例）](../core/arbitrary-xpath-property-handler-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-108">[Arbitrary XPath Property Handler (BizTalk Server Sample)](../core/arbitrary-xpath-property-handler-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-109">示範如何針對提交給 BizTalk Server 之 XML 文件的特定屬性進行升級的作業，撰寫自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="007ae-109">Demonstrates how to write a custom pipeline component to promote specific properties on an XML document submitted to BizTalk Server.</span></span> <span data-ttu-id="007ae-110">屬性升級會透過 XPath 運算式來達成。</span><span class="sxs-lookup"><span data-stu-id="007ae-110">Property promotion is accomplished using an XPath expression.</span></span>  
  
-   [<span data-ttu-id="007ae-111">管線 AssemblerDisassembler （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="007ae-111">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)  
  
    -   <span data-ttu-id="007ae-112">[FlatFileReceive （BizTalk Server 範例）](../core/flatfilereceive-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-112">[FlatFileReceive (BizTalk Server Sample)](../core/flatfilereceive-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-113">示範如何使用 BizTalk Server 管線將分隔一般檔案訊息處理成相等的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="007ae-113">Demonstrates how to process delimited flat file messages into the equivalent XML messages using BizTalk Server pipelines.</span></span>  
  
    -   <span data-ttu-id="007ae-114">[EnvelopeProcessing （BizTalk Server 範例）](../core/envelopeprocessing-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-114">[EnvelopeProcessing (BizTalk Server Sample)](../core/envelopeprocessing-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-115">示範如何使用 BizTalk Server 管線將一般檔案訊息處理成含有信封的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="007ae-115">Demonstrates how to process flat file messages into XML messages with envelopes using BizTalk Server pipelines.</span></span>  
  
    -   <span data-ttu-id="007ae-116">[FlatFileSend （BizTalk Server 範例）](../core/flatfilesend-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-116">[FlatFileSend (BizTalk Server Sample)](../core/flatfilesend-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-117">示範如何使用 BizTalk Server 管線將 XML 訊息處理成相等的位置一般檔案訊息。</span><span class="sxs-lookup"><span data-stu-id="007ae-117">Demonstrates how to process XML messages into the equivalent positional flat file messages using BizTalk Server pipelines.</span></span>  
  
-   <span data-ttu-id="007ae-118">[撰寫訊息處理器 （BizTalk Server 範例）](../core/composed-message-processor-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-118">[Composed Message Processor (BizTalk Server Sample)](../core/composed-message-processor-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-119">示範如何處理彙總使用撰寫的訊息處理的訊息中的個別明細項目。</span><span class="sxs-lookup"><span data-stu-id="007ae-119">Demonstrates how to process individual line items from aggregated messages using composed message processing.</span></span>  
  
-   <span data-ttu-id="007ae-120">[CustomComponent （BizTalk Server 範例）](../core/customcomponent-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-120">[CustomComponent (BizTalk Server Sample)](../core/customcomponent-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-121">示範如何建立和使用會修改資料流處理訊息的自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="007ae-121">Demonstrates how to create and use a custom pipeline component that modifies a streamed message.</span></span>  
  
-   <span data-ttu-id="007ae-122">[自訂合作對象解析 （BizTalk Server 範例）](../core/custom-party-resolution-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-122">[Custom Party Resolution (BizTalk Server Sample)](../core/custom-party-resolution-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-123">示範如何撰寫自訂管線元件來解析自訂合作對象。</span><span class="sxs-lookup"><span data-stu-id="007ae-123">Demonstrates how to write a custom pipeline component to resolve a custom party.</span></span>  
  
-   <span data-ttu-id="007ae-124">[MIME （BizTalk Server 範例）](../core/mime-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-124">[MIME (BizTalk Server Sample)](../core/mime-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-125">示範訊息如何使用 BizTalk 管線來完成 MIME 編碼。</span><span class="sxs-lookup"><span data-stu-id="007ae-125">Demonstrates how messages can be MIME-encoded using BizTalk pipelines.</span></span>  
  
-   <span data-ttu-id="007ae-126">[結構描述解析程式元件 （BizTalk Server 範例）](../core/schema-resolver-component-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-126">[Schema Resolver Component (BizTalk Server Sample)](../core/schema-resolver-component-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-127">示範如何擴充 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 一般檔案解譯器元件的功能。</span><span class="sxs-lookup"><span data-stu-id="007ae-127">Demonstrates how to extend the functionality of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] flat file disassembler component.</span></span>  
  
-   <span data-ttu-id="007ae-128">[XSLT 轉換元件 （BizTalk Server 範例）](../core/xslt-transform-component-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="007ae-128">[XSLT Transform Component (BizTalk Server Sample)](../core/xslt-transform-component-biztalk-server-sample.md).</span></span> <span data-ttu-id="007ae-129">示範如何撰寫將使用 XSLT 來轉換 XML 訊息的自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="007ae-129">Demonstrates how to write a custom pipeline component to transform an XML message using XSLT.</span></span>