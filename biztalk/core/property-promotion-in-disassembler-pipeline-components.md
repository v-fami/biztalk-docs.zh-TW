---
title: 解譯器管線元件中的屬性升級 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, promoting properties
- XML Disassembler [pipeline component], properties
- pipeline components, properties
- promoting properties, disassembler pipeline components
- BizTalk Framework Assembler [pipeline component], properties
- Flat File Disassembler [pipeline component], properties
ms.assetid: aa37b308-8aa2-45f4-9383-aca4f2c925ce
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6c95c58dafe1f7f875232c5b65962e731334f16
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971836"
---
# <a name="property-promotion-in-disassembler-pipeline-components"></a><span data-ttu-id="43e8f-102">解譯器管線元件中的屬性升級</span><span class="sxs-lookup"><span data-stu-id="43e8f-102">Property Promotion in Disassembler Pipeline Components</span></span>
<span data-ttu-id="43e8f-103">屬性升級是指一種程序，該程序使用 XPath 運算式從 XML 文件擷取屬性值，然後將該值放在訊息內容上，以便用於訊息路由。</span><span class="sxs-lookup"><span data-stu-id="43e8f-103">Property promotion is a process by which a property value is extracted from an XML document by using an XPath expression and placed on the message context so that it can be used for message routing.</span></span>  
  
 <span data-ttu-id="43e8f-104">如果升級的屬性沒有預設值或固定值，該屬性的 XML 欄位已遺失，且驗證文件結構屬性為**False**，不會升級此屬性。</span><span class="sxs-lookup"><span data-stu-id="43e8f-104">If a promoted property does not have a default or fixed value, the XML field for that property is missing, and the Validate Document Structure property is **False**, the property is not promoted.</span></span>  
  
 <span data-ttu-id="43e8f-105">自訂管線元件可以升級多值屬性，也就是陣列屬性。</span><span class="sxs-lookup"><span data-stu-id="43e8f-105">A custom pipeline component can promote multivalued (that is, arrayed) properties.</span></span> <span data-ttu-id="43e8f-106">含有多值屬性的訊息只受「以內容為基礎的路由」(CBR) 實例的支援，這些訊息不能路由至協調流程，也不能用於追蹤。</span><span class="sxs-lookup"><span data-stu-id="43e8f-106">Messages that contain multivalued properties are only supported in content-based routing (CBR) scenarios; they cannot be routed to orchestrations or be used for tracking purposes.</span></span>  
  
 <span data-ttu-id="43e8f-107">若某個空白項目擁有結尾標記，則 XML 解譯器不會其升級預設值或固定值。</span><span class="sxs-lookup"><span data-stu-id="43e8f-107">The XML Disassembler does not promote default or fixed values for an empty element if it has a closing tag.</span></span> <span data-ttu-id="43e8f-108">例如， \<field1\>便不會升級下列 xml。</span><span class="sxs-lookup"><span data-stu-id="43e8f-108">For example, \<field1\> is not promoted in the following XML.</span></span>  
  
```  
<document>  
   <field1></field1>  
</document>  
```  
  
 <span data-ttu-id="43e8f-109">然而，不含結尾標記的空白項目 (如下列範例所示) 則可升級。</span><span class="sxs-lookup"><span data-stu-id="43e8f-109">However, an empty element without a closing tag (as shown in the following example) is promoted.</span></span>  
  
```  
<document>  
   <field1/>  
</document>  
```  
  
 <span data-ttu-id="43e8f-110">從文件讀取日期時間資料並將其放至內容屬性時，若資料的格式為 UTC，則會保留該格式。</span><span class="sxs-lookup"><span data-stu-id="43e8f-110">When reading datetime data from a document and placing it into the context property, if the data is in UTC format, that format is preserved.</span></span> <span data-ttu-id="43e8f-111">若日期時間資料的格式為「本地+位移」，則 BizTalk Server 會將位移和本地時間相加，將日期時間格式轉換為 UTC 格式。</span><span class="sxs-lookup"><span data-stu-id="43e8f-111">If the datetime data is in local+offset format, BizTalk Server converts the datetime format to the UTC format that results from adding the offset to the local time.</span></span> <span data-ttu-id="43e8f-112">若日期時間格式未指定時區或 UTC 格式，則會假設為本地時間，並根據目前時區將其轉換為 UTC。</span><span class="sxs-lookup"><span data-stu-id="43e8f-112">If the datetime format does not specify time zone or UTC format, the time is assumed to be local and is converted to UTC based on the current time zone.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e8f-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="43e8f-113">See Also</span></span>  
 <span data-ttu-id="43e8f-114">[XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="43e8f-114">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="43e8f-115">如何設定 XML 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="43e8f-115">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)