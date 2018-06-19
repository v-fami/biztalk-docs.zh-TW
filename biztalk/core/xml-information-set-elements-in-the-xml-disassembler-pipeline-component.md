---
title: XML 解譯器管線元件中的 XML 資訊集項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Disassembler [pipeline component], information set
- XML Disassembler [pipeline component], processing instructions
- pipeline components, XML Disassembler
ms.assetid: cc82344c-6c4b-4154-a662-0b7ae5caad30
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90b3140cbe23637160aafabdccb37104efd1d318
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289294"
---
# <a name="xml-information-set-elements-in-the-xml-disassembler-pipeline-component"></a><span data-ttu-id="943cd-102">XML 解譯器管線元件中的 XML 資訊集項目</span><span class="sxs-lookup"><span data-stu-id="943cd-102">XML Information Set Elements in the XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="943cd-103">XML 解譯器處理 XML 資訊設定項目的方式如下。</span><span class="sxs-lookup"><span data-stu-id="943cd-103">The XML Disassembler handles XML information set elements as follows.</span></span>  
  
|<span data-ttu-id="943cd-104">元素</span><span class="sxs-lookup"><span data-stu-id="943cd-104">Element</span></span>|<span data-ttu-id="943cd-105">Description</span><span class="sxs-lookup"><span data-stu-id="943cd-105">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="943cd-106">comment</span><span class="sxs-lookup"><span data-stu-id="943cd-106">comment</span></span>|<span data-ttu-id="943cd-107">註解會保留在文件中，不過 XML 封套中的任何註解都不會保留。</span><span class="sxs-lookup"><span data-stu-id="943cd-107">Comments are preserved in the document; however, any comments in XML envelopes are not preserved.</span></span>|  
|<span data-ttu-id="943cd-108">CDATA</span><span class="sxs-lookup"><span data-stu-id="943cd-108">CDATA</span></span>|<span data-ttu-id="943cd-109">CDATA 會保留在文件中。</span><span class="sxs-lookup"><span data-stu-id="943cd-109">CDATA is preserved in the document.</span></span> <span data-ttu-id="943cd-110">不會保留出現在文件外部 (例如，在信封中) 的 CDATA 項目。</span><span class="sxs-lookup"><span data-stu-id="943cd-110">CDATA elements appearing outside of a document (for example, in an envelope) are not preserved.</span></span>|  
|<span data-ttu-id="943cd-111">處理指示</span><span class="sxs-lookup"><span data-stu-id="943cd-111">processing instructions</span></span>|<span data-ttu-id="943cd-112">XML 解譯器會保留出現在 XML 裡面或前面的處理指示。</span><span class="sxs-lookup"><span data-stu-id="943cd-112">The XML Disassembler preserves processing instructions appearing in or before an XML document.</span></span> <span data-ttu-id="943cd-113">但是不會保留出現在 XML 文件之後或在信封前後的處理指示。</span><span class="sxs-lookup"><span data-stu-id="943cd-113">Processing instructions appearing after an XML document or before or after an envelope are not preserved.</span></span>|  
|<span data-ttu-id="943cd-114">XML 宣告</span><span class="sxs-lookup"><span data-stu-id="943cd-114">XML declaration</span></span>|<span data-ttu-id="943cd-115">會移除任何內送 XML 訊息的 XML 宣告項目。</span><span class="sxs-lookup"><span data-stu-id="943cd-115">The XML declaration element of any incoming XML message is removed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="943cd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="943cd-116">See Also</span></span>  
 <span data-ttu-id="943cd-117">[XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="943cd-117">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="943cd-118">如何設定 XML 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="943cd-118">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)