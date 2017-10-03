---
title: "驗證 XML 解譯器管線元件中的文件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Validate Document Structure property
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], document validation
- XML Disassembler [pipeline component], warnings
ms.assetid: feb25033-46d3-48ed-8e1f-0cd123e94149
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2dcea790208bf0234c67c8c941e6355fb367d82
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="document-validation-in-the-xml-disassembler-pipeline-component"></a><span data-ttu-id="91760-102">XML 解譯器管線元件中的文件驗證</span><span class="sxs-lookup"><span data-stu-id="91760-102">Document Validation in the XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="91760-103">依照預設，XML 解譯器不會針對結構描述驗證 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="91760-103">By default, the XML Disassembler does not validate XML documents against a schema.</span></span> <span data-ttu-id="91760-104">不過，您可以設定 XML 解譯器來驗證 XML 文件，藉由設定**驗證文件結構**屬性。</span><span class="sxs-lookup"><span data-stu-id="91760-104">However, you can configure the XML Disassembler to validate an XML document by setting the **Validate Document Structure** property.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="91760-105">若以簡單資料型別宣告某個升級欄位，但包含複雜資料，則屬性升級將造成無法預測的結果。</span><span class="sxs-lookup"><span data-stu-id="91760-105">If a field for promotion is declared with a simple data type but contains complex data, the property promotion will cause unpredictable results.</span></span> <span data-ttu-id="91760-106">若要避免這種情況下，設定 XML 解譯器藉由設定執行文件驗證**驗證文件結構**屬性**True**。</span><span class="sxs-lookup"><span data-stu-id="91760-106">To avoid this scenario, configure the XML Disassembler to perform document validation by setting the **Validate Document Structure** property to **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91760-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91760-107">See Also</span></span>  
 <span data-ttu-id="91760-108">[XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="91760-108">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="91760-109">如何設定 XML 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="91760-109">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)