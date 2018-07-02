---
title: 在 XML 組合器和解譯器管線元件中的使用信封 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XMLNorm.EnvelopeSpecNames property
- XML Disassembler [pipeline component], envelopes
- envelopes, nesting
- envelopes, XML Disassembler [pipeline component]
- envelopes, XML Assembler [pipeline component]
- XML Assembler [pipeline component], envelopes
- Envelope Specification Names property
ms.assetid: ccffd2f7-c7b1-4103-a914-ae9b4b19bee3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a435b0f87eb955bc3534c2892894a3a13afdc13
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966455"
---
# <a name="envelope-use-in-the-xml-assembler-and-disassembler-pipeline-components"></a><span data-ttu-id="e3d70-102">在 XML 組合器和解譯器管線元件中使用信封</span><span class="sxs-lookup"><span data-stu-id="e3d70-102">Envelope Use in the XML Assembler and Disassembler Pipeline Components</span></span>
<span data-ttu-id="e3d70-103">XML 訊息可以包含零或更多信封。</span><span class="sxs-lookup"><span data-stu-id="e3d70-103">An XML message can include zero or more envelopes.</span></span> <span data-ttu-id="e3d70-104">下列範例顯示包裝 XML 文件的信封 (粗體)。</span><span class="sxs-lookup"><span data-stu-id="e3d70-104">The following example shows an envelope (in bold) wrapping an XML document.</span></span>  
  
```  
<ns1:document xmlns:ns1="http://myDocumentNamespaceURI.org">  
   <message>Hello</message>  
</ns1:document>  
  
```  
  
 <span data-ttu-id="e3d70-105">信封有兩個用途：</span><span class="sxs-lookup"><span data-stu-id="e3d70-105">Envelopes serve two purposes:</span></span>  
  
- <span data-ttu-id="e3d70-106">它們包含用於屬性升級和降級的欄位值。</span><span class="sxs-lookup"><span data-stu-id="e3d70-106">They can include field values to use for property promotion and demotion.</span></span>  
  
   <span data-ttu-id="e3d70-107">XML 解譯器元件會升級屬性，而 XML 組合器元件則會降級屬性。</span><span class="sxs-lookup"><span data-stu-id="e3d70-107">The XML Disassembler component promotes properties, and the XML Assembler component demotes properties.</span></span> <span data-ttu-id="e3d70-108">屬性升級和降級也可發生在 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="e3d70-108">Property promotion and demotion can also occur in XML documents.</span></span>  
  
- <span data-ttu-id="e3d70-109">它們可以將數個 XML 文件併入單一交換中。</span><span class="sxs-lookup"><span data-stu-id="e3d70-109">They can combine several XML documents into a single interchange.</span></span>  
  
   <span data-ttu-id="e3d70-110">因為格式正確的 XML 文件只能有一個根項目，所以信封可讓您結合多個 XML 文件以共用一個根項目。</span><span class="sxs-lookup"><span data-stu-id="e3d70-110">Because a well-formed XML document can have only one root element, an envelope enables you to combine multiple XML documents to share one root element.</span></span>  
  
  <span data-ttu-id="e3d70-111">您可以藉由指定信封順序，藉由強制使用標準形式**結構描述集合屬性編輯器**的省略符號，即可存取此對話方塊**信封結構描述**在 XML 組合器的設計階段屬性。</span><span class="sxs-lookup"><span data-stu-id="e3d70-111">You can enforce the canonical form by specifying the envelope order by using the **Schema Collection Property Editor** dialog which is accessed by clicking the ellipses for the **Envelope schemas** design-time property in the XML Assembler.</span></span> <span data-ttu-id="e3d70-112">您也可以使用**XMLNORM。EnvelopeSpecNames**執行 XML 組合器之前，訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="e3d70-112">You can also use the **XMLNORM.EnvelopeSpecNames** message context property before the XML Assembler is run.</span></span> <span data-ttu-id="e3d70-113">XML 組合器會在標準形式中產生信封文件。</span><span class="sxs-lookup"><span data-stu-id="e3d70-113">The XML Assembler produces an enveloped document in canonical form.</span></span>  
  
## <a name="nesting-envelopes"></a><span data-ttu-id="e3d70-114">巢狀信封</span><span class="sxs-lookup"><span data-stu-id="e3d70-114">Nesting envelopes</span></span>  
 <span data-ttu-id="e3d70-115">您可以巢狀處理信封以形成複雜的結構，而在此結構中，可將數個信封 XML 文件併入一個更大的交換。</span><span class="sxs-lookup"><span data-stu-id="e3d70-115">You can nest envelopes to form complex document structures where several enveloped XML documents can be combined into a larger interchange.</span></span> <span data-ttu-id="e3d70-116">下列範例顯示由兩個信封所包裝的交換。</span><span class="sxs-lookup"><span data-stu-id="e3d70-116">The following example shows an interchange wrapped by two envelopes.</span></span>  
  
```  
<envelope1>  
   <document1/>  
   <envelope2>  
      <document2/>  
      <document3/>  
   </envelope2>  
   <document4/>  
</envelope1>  
```  
  
 <span data-ttu-id="e3d70-117">前述範例說明一個具彈性的形式，這表示文件可以與信封位在相同的階層層次。</span><span class="sxs-lookup"><span data-stu-id="e3d70-117">The preceding example illustrates a flexible form, which means that a document can be on the same hierarchy level as an envelope.</span></span> <span data-ttu-id="e3d70-118">在解譯信封文件之後，會建立四個分開的文件 (文件1、文件2，以此類推)。</span><span class="sxs-lookup"><span data-stu-id="e3d70-118">After disassembling the enveloped document, four separate documents are created (document1, document2, and so on).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d70-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3d70-119">See Also</span></span>  
 [<span data-ttu-id="e3d70-120">管線元件</span><span class="sxs-lookup"><span data-stu-id="e3d70-120">Pipeline Components</span></span>](../core/pipeline-components.md)