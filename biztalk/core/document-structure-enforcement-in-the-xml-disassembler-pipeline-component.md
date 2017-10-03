---
title: "文件結構強化 XML 解譯器管線元件中的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Disassembler [pipeline component], document structure
- pipeline components, XML Disassembler
ms.assetid: ac405bf2-f92b-4b45-8256-dd188ec9510a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e14b20292b23a0f50362940e3b873fa37a3f5bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="document-structure-enforcement-in-the-xml-disassembler-pipeline-component"></a><span data-ttu-id="26aea-102">XML 解譯器管線元件中的文件結構強化</span><span class="sxs-lookup"><span data-stu-id="26aea-102">Document Structure Enforcement in the XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="26aea-103">若文件或信封結構描述在 XML 解譯器中明確地參考，則 XML 解譯器所處理的文件只包括其訊息類型符合於結構描述的文件。</span><span class="sxs-lookup"><span data-stu-id="26aea-103">If a document or envelope schema is explicitly referenced in the XML Disassembler, the XML Disassembler processes only those documents with message types conforming to the schema.</span></span> <span data-ttu-id="26aea-104">其他文件都不會經過處理，無論是否有部署結構描述作為其參考。</span><span class="sxs-lookup"><span data-stu-id="26aea-104">No other documents are processed, regardless of whether a deployed schema is referenced for them.</span></span>  
  
 <span data-ttu-id="26aea-105">XML 解譯器會增強信封結構描述的特定順序，但是不會增強文件結構描述的順序。</span><span class="sxs-lookup"><span data-stu-id="26aea-105">The XML Disassembler enforces the specified order of envelope schemas; however, the order of document schemas is not enforced.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26aea-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26aea-106">See Also</span></span>  
 <span data-ttu-id="26aea-107">[XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="26aea-107">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="26aea-108">如何設定 XML 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="26aea-108">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)