---
title: XML 組合器管線元件中的處理指示 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XMLNorm.ProcessingInstructionOption property
- envelopes, processing instructions
- XML Assembler [pipeline component], processing instructions
- Processing instruction scope property
- XMLNorm.ProcessingInstruction property
- envelopes, XML Assembler [pipeline component]
- pipeline components, XML Assembler
ms.assetid: d8ea453e-3b20-417d-bf25-9d424b0150fd
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df3b56a3703e56dd4b3f474b4846999bae9858f0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016104"
---
# <a name="processing-instructions-in-the-xml-assembler-pipeline-component"></a><span data-ttu-id="ee0ac-102">XML 組合器管線元件中的處理指示</span><span class="sxs-lookup"><span data-stu-id="ee0ac-102">Processing Instructions in the XML Assembler Pipeline Component</span></span>
<span data-ttu-id="ee0ac-103">處理指示提供處理 XML 文件之應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-103">Processing instructions provide information to the application that processes an XML document.</span></span> <span data-ttu-id="ee0ac-104">這類資訊可能包含如何處理文件、如何顯示文件等等的指示。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-104">Such information may include instructions about how to process the document, how to display it, and so on.</span></span>  
  
 <span data-ttu-id="ee0ac-105">處理指示新增至 XML 文件所**新增處理指示**屬性 (或同等權限**XMLNorm.ProcessingInstructionOption**訊息內容屬性)。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-105">Processing instructions are added to an XML document by the **Add processing instructions** property (or the equivalent **XMLNorm.ProcessingInstructionOption** property on the message context).</span></span> <span data-ttu-id="ee0ac-106">處理指示文字會指定**新增處理指示文字**屬性 (或同等權限**XMLNorm.ProcessingInstruction**訊息內容屬性)。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-106">Processing instruction text is specified with the **Add processing instructions text** property (or the equivalent **XMLNorm.ProcessingInstruction** property on the message context).</span></span>  
  
 <span data-ttu-id="ee0ac-107">**新增處理指示**屬性 (或**XMLNorm.ProcessingInstructionOption**屬性) 有三個可能的值下, 表所述。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-107">The **Add processing instructions** property (or **XMLNorm.ProcessingInstructionOption** property) has three possible values, which are described in the following table.</span></span>  
  
|<span data-ttu-id="ee0ac-108">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="ee0ac-108">Value</span></span>|<span data-ttu-id="ee0ac-109">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="ee0ac-109">Value</span></span>|<span data-ttu-id="ee0ac-110">描述</span><span class="sxs-lookup"><span data-stu-id="ee0ac-110">Description</span></span>|  
|-----------|-----------|-----------------|  
|<span data-ttu-id="ee0ac-111">附加</span><span class="sxs-lookup"><span data-stu-id="ee0ac-111">Append</span></span>|<span data-ttu-id="ee0ac-112">0</span><span class="sxs-lookup"><span data-stu-id="ee0ac-112">0</span></span>|<span data-ttu-id="ee0ac-113">來自 XML 組合器的新處理指示會附加至文件開頭的處理指示。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-113">New processing instructions from the XML Assembler are appended to the processing instructions at the beginning of the document.</span></span>|  
|<span data-ttu-id="ee0ac-114">建立新物件</span><span class="sxs-lookup"><span data-stu-id="ee0ac-114">Create new</span></span>|<span data-ttu-id="ee0ac-115">@shouldalert</span><span class="sxs-lookup"><span data-stu-id="ee0ac-115">1</span></span>|<span data-ttu-id="ee0ac-116">來自 XML 組合器的新處理指示會覆寫文件開頭的現有處理指示。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-116">New processing instructions from the XML Assembler overwrite existing processing instructions at the beginning of the document.</span></span>|  
|<span data-ttu-id="ee0ac-117">Ignore</span><span class="sxs-lookup"><span data-stu-id="ee0ac-117">Ignore</span></span>|<span data-ttu-id="ee0ac-118">2</span><span class="sxs-lookup"><span data-stu-id="ee0ac-118">2</span></span>|<span data-ttu-id="ee0ac-119">會移除文件開頭的處理指示。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-119">Processing instructions at the beginning of the document are removed.</span></span>|  
  
 <span data-ttu-id="ee0ac-120">在訊息內容上指定之這組處理指示 (或訊息內容屬性) 的優先順序高於在管線設計師中所指定的屬性組。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-120">The pair of processing instructions (or message context properties) specified on a message context take precedence over the property pair specified in Pipeline Designer.</span></span> <span data-ttu-id="ee0ac-121">比方說，如果**XMLNorm.ProcessingInstructionOption**指定為**新建**(1) 和**XMLNorm.ProcessingInstruction**未指定，則空白處理指示會取代現有的處理指示。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-121">For example, if **XMLNorm.ProcessingInstructionOption** is specified as **Create new** (1) and **XMLNorm.ProcessingInstruction** is not specified, an empty processing instruction will replace an existing processing instruction.</span></span>  
  
 <span data-ttu-id="ee0ac-122">另舉一例，如果**XMLNorm.ProcessingInstruction**指定，但**XMLNorm.ProcessingInstructionOption**不是，不會使用任何來自訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-122">As another example, if **XMLNorm.ProcessingInstruction** is specified but **XMLNorm.ProcessingInstructionOption** is not, none of the properties from the message context are used.</span></span> <span data-ttu-id="ee0ac-123">在此種情況下，會使用來自管線設計師的處理指示。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-123">In this case, the processing instructions from Pipeline Designer are used.</span></span>  
  
 <span data-ttu-id="ee0ac-124">根據預設，**新增處理指示**設為**附加**，並**新增處理指示文字**是空的。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-124">By default, **Add processing instructions** is set to **Append**, and **Add processing instructions text** is empty.</span></span>  
  
## <a name="processing-properties-and-envelopes"></a><span data-ttu-id="ee0ac-125">處理屬性和信封</span><span class="sxs-lookup"><span data-stu-id="ee0ac-125">Processing Properties and Envelopes</span></span>  
 <span data-ttu-id="ee0ac-126">因為處理指示並非保留供信封所使用，所以下列一般檔案組合器設定的組合只會導致具有處理指示的最外層信封：</span><span class="sxs-lookup"><span data-stu-id="ee0ac-126">Because processing instructions are not preserved for the envelopes, the following combination of flat file assembler settings results in only the outermost envelope having the processing instruction:</span></span>  
  
- <span data-ttu-id="ee0ac-127">**處理指示範圍**屬性設定為"Envelope"。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-127">**Processing instruction scope** property set to "Envelope."</span></span>  
  
- <span data-ttu-id="ee0ac-128">**新增處理指示**屬性設定為"Append"。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-128">**Add processing instructions** property set to "Append."</span></span>  
  
  <span data-ttu-id="ee0ac-129">信封將會使用 「 組合器 」 中指定的處理指示**新增處理指示文字**屬性。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-129">The envelope would use the processing instruction specified in the assembler's **Add Processing instructions text** property.</span></span>  
  
  <span data-ttu-id="ee0ac-130">任何在外部或內部信封中的現有處理指示 (如指定在內送訊息中) 都不會出現在輸出訊息中。</span><span class="sxs-lookup"><span data-stu-id="ee0ac-130">Any existing processing instructions in either the outer or inner envelope(s), as specified in the incoming message, will not be present in the output message(s).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee0ac-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee0ac-131">See Also</span></span>  
 <span data-ttu-id="ee0ac-132">[XML 組合器管線元件](../core/xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="ee0ac-132">[XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="ee0ac-133">[如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="ee0ac-133">[How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="ee0ac-134">Pipelines-AssemblerDisassembler (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="ee0ac-134">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)