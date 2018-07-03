---
title: 辨別的欄位的解譯器管線元件 |Microsoft Docs
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
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b08a5c3dd6b88351e67f678524a03052e8435439
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012287"
---
# <a name="distinguished-fields-in-disassembler-pipeline-components"></a>辨別的欄位的解譯器管線元件
結構描述中定義的辨別欄位會由「XML 解譯器」、「BizTalk Framework 解譯器」或「一般檔案解譯器」管線元件以下列格式寫入訊息內容：  
  
 *使用名稱*是辨別的欄位 xpath  
  
 *命名空間 URI*是 「<http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields>"  
  
 屬性的值是**System.String**指定 XPath 擷取自 XML 文件使用的值。  
  
 以下範例結構描述具有辨別欄位 Price。  
  
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
  
 對於文件執行個體  
  
```  
<PO>  
            <Item>Bolt</Item>  
            <Price>10</Price>  
<PO>  
```  
  
 XML 解譯器在訊息內容寫入辨別欄位，如下所示：  
  
 在內容上的屬性名稱： `"/*[local-name()='PO' and namespace-uri()='http://SendHtmlMessage.PO']/\*[local-name()='Price' and namespace-uri()='']"`  
  
 屬性的命名空間： http://schemas.microsoft.com/BizTalk/2003/btsDistinguishedFields  
  
 屬性的值： 10  
  
> [!NOTE]
>  若任何 XML 文件項目值的大小超過 85KB，則處理這些文件時可能會發生效能降低的狀況。  
  
## <a name="see-also"></a>另請參閱  
 [一般檔案解譯器管線元件](../core/flat-file-disassembler-pipeline-component.md)   
 [如何設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)
