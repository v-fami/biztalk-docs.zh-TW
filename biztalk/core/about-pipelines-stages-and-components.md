---
title: 關於管線、 階段和元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Microsoft.BizTalk.Component.Interop namespace
- pipelines, about pipelines
ms.assetid: a98e1c93-f264-4577-bd12-4430a5859e3c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 070c785924021f8e398a547c01afe969fa6430cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225462"
---
# <a name="about-pipelines-stages-and-components"></a><span data-ttu-id="1fe7f-102">關於管線、階段和元件</span><span class="sxs-lookup"><span data-stu-id="1fe7f-102">About Pipelines, Stages, and Components</span></span>
<span data-ttu-id="1fe7f-103">管線是軟體基礎結構的一部分，其中包含的 .NET 或 COM 元件組可根據預先定義的順序來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-103">A pipeline is a piece of software infrastructure that contains a set of .NET or COM components that process messages in a predefined sequence.</span></span> <span data-ttu-id="1fe7f-104">管線會將處理程序分割成數個工作類別，稱之為階段，然後決定這些階段的執行順序。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-104">A pipeline divides processing into categories of work called stages, and determines the sequence in which the stages are performed.</span></span> <span data-ttu-id="1fe7f-105">各個階段都會定義邏輯工作群組、決定將於階段中使用的元件，然後指定管線元件在階段中的執行方式。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-105">Each stage defines logical work groups, determines which components can go in that stage, and specifies how the pipeline components in the stage are run.</span></span>  
  
 <span data-ttu-id="1fe7f-106">在各個階段中，管線元件都會執行特定的工作。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-106">Within each stage, pipeline components perform specific tasks.</span></span> <span data-ttu-id="1fe7f-107">例如，接收管線階段中的元件可以解碼、解譯，然後將文件從其他的格式轉換為 XML。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-107">For example, components within stages of a receive pipeline may decode, disassemble, and then convert documents from other formats to XML.</span></span> <span data-ttu-id="1fe7f-108">傳送管線的工作剛好相反：這個工作會將文件從 XML 轉換為其他格式，並進行組合和加密；每個管線元件都負責執行整個程序中的部分工作。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-108">Send pipelines do essentially the opposite: convert documents from XML to other formats, assemble, and encrypt, with each pipeline component performing a portion of the entire process.</span></span> <span data-ttu-id="1fe7f-109">雖然階段是數個元件的容器，但是各階段本身都是一個附有中繼資料的元件。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-109">Although a stage is a container of components, each stage is itself a component with metadata.</span></span> <span data-ttu-id="1fe7f-110">階段沒有執行碼；相反地，管線元件則有執行碼。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-110">Stages have no execution code, as opposed to pipeline components, which do have execution code.</span></span>  
  
 <span data-ttu-id="1fe7f-111">下圖顯示管線設計介面的管線說明。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-111">The following figure shows how the pipeline design surface illustrates pipelines.</span></span> <span data-ttu-id="1fe7f-112">此管線有兩個階段：「組合」階段和「編碼」階段。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-112">This pipeline has two stages, the Assemble stage and the Encode stage.</span></span> <span data-ttu-id="1fe7f-113">XML 組合器管線元件已加入至 「 組合 」 階段，但 「 編碼 」 階段仍為空白，因為它仍顯示**放置到此處 ！**</span><span class="sxs-lookup"><span data-stu-id="1fe7f-113">The XML Assembler pipeline component was added to the Assemble stage, but the Encode stage is still empty, because it still shows **Drop Here!**</span></span> <span data-ttu-id="1fe7f-114">表示管線元件，可以新增至階段。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-114">to indicate that a pipeline component can be added to the stage.</span></span>  
  
 <span data-ttu-id="1fe7f-115">![階段與 BizTalk 管線中的元件](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")</span><span class="sxs-lookup"><span data-stu-id="1fe7f-115">![Stages and components in a BizTalk pipeline](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")</span></span>  
<span data-ttu-id="1fe7f-116">說明 BizTalk 管線中的階段和元件。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-116">Illustrates stages and components in a BizTalk pipeline.</span></span>  
  
 <span data-ttu-id="1fe7f-117">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含一組管線範本、管線元件和預設管線。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-117">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contains a set of pipeline templates, pipeline components, and default pipelines.</span></span> <span data-ttu-id="1fe7f-118">您可以建立並使用管線設計師使用者介面; 設定管線使用中的 API 實作管線**Microsoft.BizTalk.Component.Interop**命名空間。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-118">You can create and configure pipelines by using the Pipeline Designer user interface; you implement pipelines by using the API in the **Microsoft.BizTalk.Component.Interop** namespace.</span></span> <span data-ttu-id="1fe7f-119">您無法修改管線範本。</span><span class="sxs-lookup"><span data-stu-id="1fe7f-119">You cannot modify the pipeline templates.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1fe7f-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="1fe7f-120">In This Section</span></span>  
  
-   [<span data-ttu-id="1fe7f-121">類型的管線</span><span class="sxs-lookup"><span data-stu-id="1fe7f-121">Types of Pipelines</span></span>](../core/types-of-pipelines.md)  
  
-   [<span data-ttu-id="1fe7f-122">類型的管線元件</span><span class="sxs-lookup"><span data-stu-id="1fe7f-122">Types of Pipeline Components</span></span>](../core/types-of-pipeline-components.md)  
  
-   [<span data-ttu-id="1fe7f-123">管線階段</span><span class="sxs-lookup"><span data-stu-id="1fe7f-123">Pipeline Stages</span></span>](../core/pipeline-stages.md)  
  
-   [<span data-ttu-id="1fe7f-124">預設管線</span><span class="sxs-lookup"><span data-stu-id="1fe7f-124">Default Pipelines</span></span>](../core/default-pipelines.md)  
  
-   [<span data-ttu-id="1fe7f-125">管線範本</span><span class="sxs-lookup"><span data-stu-id="1fe7f-125">Pipeline Templates</span></span>](../core/pipeline-templates.md)  
  
-   [<span data-ttu-id="1fe7f-126">管線元件</span><span class="sxs-lookup"><span data-stu-id="1fe7f-126">Pipeline Components</span></span>](../core/pipeline-components.md)  
  
-   [<span data-ttu-id="1fe7f-127">管線元件中的結構描述解析</span><span class="sxs-lookup"><span data-stu-id="1fe7f-127">Schema Resolution in Pipeline Components</span></span>](../core/schema-resolution-in-pipeline-components.md)  
  
-   [<span data-ttu-id="1fe7f-128">XML 組合器和解譯器管線元件中使用的信封</span><span class="sxs-lookup"><span data-stu-id="1fe7f-128">Envelope Use in the XML Assembler and Disassembler Pipeline Components</span></span>](../core/envelope-use-in-the-xml-assembler-and-disassembler-pipeline-components.md)  
  
-   [<span data-ttu-id="1fe7f-129">組合器管線元件中的屬性降級</span><span class="sxs-lookup"><span data-stu-id="1fe7f-129">Property Demotion in Assembler Pipeline Components</span></span>](../core/property-demotion-in-assembler-pipeline-components.md)  
  
-   [<span data-ttu-id="1fe7f-130">解譯器管線元件中的屬性升級</span><span class="sxs-lookup"><span data-stu-id="1fe7f-130">Property Promotion in Disassembler Pipeline Components</span></span>](../core/property-promotion-in-disassembler-pipeline-components.md)  
  
-   [<span data-ttu-id="1fe7f-131">辨別的欄位在解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="1fe7f-131">Distinguished Fields in Disassembler Pipeline Components</span></span>](../core/distinguished-fields-in-disassembler-pipeline-components.md)