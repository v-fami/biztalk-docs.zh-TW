---
title: 辨別的欄位在解譯器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, distinquished fields
- Flat File Disassembler [pipeline component], distinquished fields
- BizTalk Framework Disassembler [pipeline component], distinquished fields
- XML Disassembler [pipeline component], distinquished fields
ms.assetid: 7e51d2fe-0004-4a7b-9055-bd41e8a4b7ab
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64e4c8f15d167f5343089c11b92b0f373aa45576
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="distinguished-fields-in-disassembler-pipeline-components"></a><span data-ttu-id="a312c-102">辨別的欄位在解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="a312c-102">Distinguished Fields in Disassembler Pipeline Components</span></span>
<span data-ttu-id="a312c-103">結構描述中定義的辨別欄位會由「XML 解譯器」、「BizTalk Framework 解譯器」或「一般檔案解譯器」管線元件以下列格式寫入訊息內容：</span><span class="sxs-lookup"><span data-stu-id="a312c-103">Distinguished fields defined in a schema are written to the message context by the XML Disassembler, BizTalk Framework Disassembler, or Flat File Disassembler pipeline components in the following format:</span></span>  
  
 <span data-ttu-id="a312c-104">*使用名稱* 是 XPath 中的辨別的欄位</span><span class="sxs-lookup"><span data-stu-id="a312c-104">*name used* is the distinguished field in XPath</span></span>  
  
 <span data-ttu-id="a312c-105">*命名空間 URI*是 「http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields"</span><span class="sxs-lookup"><span data-stu-id="a312c-105">*namespace URI* is "http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields"</span></span>  
  
 <span data-ttu-id="a312c-106">屬性的值是 **System.String** 指定 XPath 擷取自 XML 文件使用的值。</span><span class="sxs-lookup"><span data-stu-id="a312c-106">The value of the property is the **System.String** value extracted from the XML document using specified XPath.</span></span>  
  
 <span data-ttu-id="a312c-107">以下範例結構描述具有辨別欄位 Price。</span><span class="sxs-lookup"><span data-stu-id="a312c-107">The following example schema has a distinguished field Price.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns="http://SendHtmlMessage.PO" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://SendHtmlMessage.PO xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="PO">  
      <xs:annotation>  
         <xs:appinfo>  
            <b:properties>  
               <b:property distinguished="true" xpath="/*[local-name()='PO' and namespace-uri()='http://SendHtmlMessage.PO']/*[local-  
               name()='Price' and namespace-uri()='']" />   
            </b:properties>  
         </xs:appinfo>  
      </xs:annotation>  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="Item" type="xs:string" />   
            <xs:element name="Price" type="xs:string" />   
         </xs:sequence>  
      </xs:complexType>  
   </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="a312c-108">對於文件執行個體</span><span class="sxs-lookup"><span data-stu-id="a312c-108">For the document instance</span></span>  
  
```  
<PO>  
            <Item>Bolt</Item>  
            <Price>10</Price>  
<PO>  
```  
  
 <span data-ttu-id="a312c-109">XML 解譯器在訊息內容寫入辨別欄位，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a312c-109">the XML Disassembler writes a distinguished field on a message context as follows:</span></span>  
  
 <span data-ttu-id="a312c-110">在內容上的屬性名稱:"/ * [local-name = 'PO' and namespace-uri （) ='http://SendHtmlMessage.PO'] /\*[local-name = 'Price' and namespace-uri （) =']"</span><span class="sxs-lookup"><span data-stu-id="a312c-110">Name of the property on the context: "/*[local-name()='PO' and namespace-uri()='http://SendHtmlMessage.PO']/\*[local-name()='Price' and namespace-uri()='']"</span></span>  
  
 <span data-ttu-id="a312c-111">屬性的命名空間： http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields</span><span class="sxs-lookup"><span data-stu-id="a312c-111">Namespace of the property: http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields</span></span>  
  
 <span data-ttu-id="a312c-112">屬性的值︰ 10</span><span class="sxs-lookup"><span data-stu-id="a312c-112">Value of the property: 10</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a312c-113">若任何 XML 文件項目值的大小超過 85KB，則處理這些文件時可能會發生效能降低的狀況。</span><span class="sxs-lookup"><span data-stu-id="a312c-113">If the size of any XML document element values exceeds 85KB, a degradation in the performance of processing those documents may occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a312c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a312c-114">See Also</span></span>  
 <span data-ttu-id="a312c-115">[一般檔案解譯器管線元件](../core/flat-file-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="a312c-115">[Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="a312c-116">如何設定一般檔案解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="a312c-116">How to Configure the Flat File Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)