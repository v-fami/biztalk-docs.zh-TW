---
title: "解譯器管線元件中的屬性升級 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, promoting properties
- XML Disassembler [pipeline component], properties
- pipeline components, properties
- promoting properties, disassembler pipeline components
- BizTalk Framework Assembler [pipeline component], properties
- Flat File Disassembler [pipeline component], properties
ms.assetid: aa37b308-8aa2-45f4-9383-aca4f2c925ce
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9770b0e66b85dcc41400002e2e0c1780bc51c3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="property-promotion-in-disassembler-pipeline-components"></a>解譯器管線元件中的屬性升級
屬性升級是指一種程序，該程序使用 XPath 運算式從 XML 文件擷取屬性值，然後將該值放在訊息內容上，以便用於訊息路由。  
  
 如果升級的屬性沒有預設值或固定值，該屬性的 XML 欄位已遺失，且驗證文件結構屬性為**False**，不會升級此屬性。  
  
 自訂管線元件可以升級多值屬性，也就是陣列屬性。 含有多值屬性的訊息只受「以內容為基礎的路由」(CBR) 實例的支援，這些訊息不能路由至協調流程，也不能用於追蹤。  
  
 若某個空白項目擁有結尾標記，則 XML 解譯器不會其升級預設值或固定值。 例如， \<field1 > 不會升級下列 xml。  
  
```  
<document>  
   <field1></field1>  
</document>  
```  
  
 然而，不含結尾標記的空白項目 (如下列範例所示) 則可升級。  
  
```  
<document>  
   <field1/>  
</document>  
```  
  
 從文件讀取日期時間資料並將其放至內容屬性時，若資料的格式為 UTC，則會保留該格式。 若日期時間資料的格式為「本地+位移」，則 BizTalk Server 會將位移和本地時間相加，將日期時間格式轉換為 UTC 格式。 若日期時間格式未指定時區或 UTC 格式，則會假設為本地時間，並根據目前時區將其轉換為 UTC。  
  
## <a name="see-also"></a>另請參閱  
 [XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md)   
 [如何設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)