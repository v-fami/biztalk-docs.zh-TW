---
title: "XML 組合器管線元件中的 XML 資訊集項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component], processing instructions
- Add XML declaration property
- XMLNorm.AddXMLDeclaration property
- pipeline components, XML Assembler
- XML Assembler [pipeline component], XML information set
ms.assetid: 5a262763-838e-476b-8117-30c94bc1d64a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b194b85c88f63036cd74fcd9838aa99e73de6556
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xml-information-set-elements-in-the-xml-assembler-pipeline-component"></a><span data-ttu-id="8cc91-102">XML 組合器管線元件中的 XML 資訊集項目</span><span class="sxs-lookup"><span data-stu-id="8cc91-102">XML Information Set Elements in the XML Assembler Pipeline Component</span></span>
<span data-ttu-id="8cc91-103">XML 組合器元件處理 XML 資訊集項目的方式如下。</span><span class="sxs-lookup"><span data-stu-id="8cc91-103">The XML Assembler component handles XML information set elements as follows.</span></span>  
  
|<span data-ttu-id="8cc91-104">元素</span><span class="sxs-lookup"><span data-stu-id="8cc91-104">Element</span></span>|<span data-ttu-id="8cc91-105">Description</span><span class="sxs-lookup"><span data-stu-id="8cc91-105">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cc91-106">comment</span><span class="sxs-lookup"><span data-stu-id="8cc91-106">comment</span></span>|<span data-ttu-id="8cc91-107">在文件開頭和結尾的 XML 標記之間的註解會保留。</span><span class="sxs-lookup"><span data-stu-id="8cc91-107">Comments are preserved between opening and closing XML tags in the document.</span></span>|  
|<span data-ttu-id="8cc91-108">CDATA</span><span class="sxs-lookup"><span data-stu-id="8cc91-108">CDATA</span></span>|<span data-ttu-id="8cc91-109">在文件開頭和結尾的 XML 標記之間的 CDATA 會保留。</span><span class="sxs-lookup"><span data-stu-id="8cc91-109">CDATA is preserved between opening and closing XML tags in the document.</span></span> <span data-ttu-id="8cc91-110">CDATA 值不用於屬性升級或辨別欄位。</span><span class="sxs-lookup"><span data-stu-id="8cc91-110">CDATA values are not used for property promotion or distinguished fields.</span></span>|  
|<span data-ttu-id="8cc91-111">處理指示</span><span class="sxs-lookup"><span data-stu-id="8cc91-111">processing instructions</span></span>|<span data-ttu-id="8cc91-112">處理指示位於之前處理文件的 XML 標記會根據其值 (如需詳細資訊，請參閱[XML 組合器管線元件中的處理指示](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md))。</span><span class="sxs-lookup"><span data-stu-id="8cc91-112">Processing instructions located before the document XML tag are handled based on their value (for more information, see [Processing Instructions in the XML Assembler Pipeline Component](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)).</span></span> <span data-ttu-id="8cc91-113">在文件開頭和結尾標記之間的處理指示會保留。</span><span class="sxs-lookup"><span data-stu-id="8cc91-113">Processing instructions between document open and close tags are preserved.</span></span> <span data-ttu-id="8cc91-114">結尾 XML 標記之後的處理指示會忽略，與信封之前、之中或之後的任何指示一樣。</span><span class="sxs-lookup"><span data-stu-id="8cc91-114">Processing instructions after the closing XML tag are ignored, as are any instructions before, in, or after the envelope.</span></span>|  
|<span data-ttu-id="8cc91-115">XML 宣告</span><span class="sxs-lookup"><span data-stu-id="8cc91-115">XML declaration</span></span>|<span data-ttu-id="8cc91-116">XML 宣告字串 (如 `<?xml version='1.0'? encoding='UTF-8'>`) 可由 XML 組合器管線元件保留。</span><span class="sxs-lookup"><span data-stu-id="8cc91-116">The XML declaration string, such as `<?xml version='1.0'? encoding='UTF-8'>`, may be preserved by the XML Assembler pipeline component.</span></span> <span data-ttu-id="8cc91-117">這由控制**新增 XML 宣告**屬性或在訊息內容，其對等項目**XMLNorm.AddXMLDeclaration**。</span><span class="sxs-lookup"><span data-stu-id="8cc91-117">This is controlled by the **Add XML declaration** property, or its equivalent on the message context, **XMLNorm.AddXMLDeclaration**.</span></span><br /><br /> <span data-ttu-id="8cc91-118">如果此選項設定為**True** XML 宣告會加入至文件。</span><span class="sxs-lookup"><span data-stu-id="8cc91-118">If this option is set to **True** then the XML declaration will be added to the document.</span></span> <span data-ttu-id="8cc91-119">若 XML 宣告已經存在，則會將它覆寫。</span><span class="sxs-lookup"><span data-stu-id="8cc91-119">If the XML declaration already existed, it will be overwritten.</span></span><br /><br /> <span data-ttu-id="8cc91-120">如果此選項設定為**False**沒有 XML 宣告會新增，將會移除任何現有的 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="8cc91-120">If this option is set to **False**, no XML declaration will be added and any existing XML declaration will be removed.</span></span> <span data-ttu-id="8cc91-121">訊息內容中的此屬性值優先於管線設計師中所指定的值。</span><span class="sxs-lookup"><span data-stu-id="8cc91-121">The value of this property in the message context takes precedence over the value specified in Pipeline Designer.</span></span><br /><br /> <span data-ttu-id="8cc91-122">預設值： **True** （永遠新增 XML 宣告）</span><span class="sxs-lookup"><span data-stu-id="8cc91-122">Default value: **True** (the XML declaration is always added)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cc91-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cc91-123">See Also</span></span>  
 <span data-ttu-id="8cc91-124">[XML 組合器管線元件](../core/xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="8cc91-124">[XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="8cc91-125">[如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="8cc91-125">[How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="8cc91-126">管線 AssemblerDisassembler （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="8cc91-126">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)