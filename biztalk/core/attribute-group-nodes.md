---
title: Attribute 群組 節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea02fae8-4e03-486a-8d9d-185ae230d3a0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7314c14a611096f92c8fd2f95b300832d6b44a0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017262"
---
# <a name="attribute-group-nodes"></a>[Attribute 群組] 節點

## <a name="overview"></a>概觀
在 「 BizTalk 編輯器 」 中，您可以新增**屬性群組**節點，以**記錄**節點或另一個**屬性群組**節點，以包含您要用於多個屬性群組以外**記錄**節點。 新增**屬性群組**節點至另一個**屬性群組**節點，可達成屬性群組巢狀結構。 這可讓您定義的屬性群組在一個地方可以用於多個**記錄**或是**屬性群組**節點。 對屬性群組後續的修改將會傳播至與該屬性群組關聯的所有節點。 不論修改的節點內容為何，都會這麼做。  

> [!NOTE]
>  在 BizTalk 編輯器**AttributeGroup**節點都由預設的字串表示\<AttribGroup:attribGroup*N* \>在結構描述樹狀結構檢視中，其中*N*是單純遞增的數字。 您可以變更 attribGroup*N*部分輸入新的唯一名稱，在其名稱及其**Group Reference**屬性。  

 一開始建立時**屬性群組**節點，您只需將它插入其中一個**記錄**或是**屬性群組**節點，它將會使用，並選擇性地變更在其名稱與其**Group Reference**屬性。 有兩種方式可使用相同的屬性群組在另一個**記錄**或是**屬性群組**節點：  

- 您可以複製現有**屬性群組**節點，然後將它貼到另**記錄**節點。  

- 您可以插入新**屬性群組**節點插入另**記錄**節點，然後再把**Group Reference**屬性的新**屬性群組**節點，以參考現有**屬性群組**節點。  

  之後，您可以在其中修改**屬性群組**節點 — 比方說，藉由新增或刪除**Field 屬性**節點 — 中的任何內容**記錄**或**屬性群組**至您貼上它的節點。 變更會傳播到所有其他**記錄**或是**屬性群組**與屬性群組相關聯的節點。  

  它會將毫無意義**屬性群組**沒有新增至少一個相關的節點，其中包括相關的節點之節點**欄位屬性**節點， **Any 屬性**節點，以及 （巢狀） **Attribute 群組**節點。 事實上，屬性群組僅包含單一屬性有些不妥當，除非您特別計劃在未來新增更多屬性。  

  **屬性群組**節點可以巢狀，允許更多可能性可以如何建構和結合屬性群組。 **屬性群組**節點也可以包含**Any 屬性**節點，允許的屬性群組，以包含相關的屬性執行個體，它能容納的萬用字元功能。  

## <a name="xsd-representation"></a>XSD 表示法  
 當**屬性群組**節點前加入至**記錄**節點或另一個**屬性群組**節點、 兩個不同區域的相對應的 XML 結構描述定義 (XSD)受影響的結構描述的語言表示法。 在下列範例中，新**屬性群組**節點，在粗體，已新增至現有**記錄**已包含現有的節點**欄位項目**節點。  

```  
        ...  
        <xs:element name="ExistingRecord">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ExistingFieldElement" type="xs:string" />  
                </xs:sequence>  
                <xs:attributeGroup ref="attrGroup0" />  
            </xs:complexType>  
        </xs:element>  
        ...   
    <xs:attributeGroup name="attrGroup0" />  
</xs:schema>  
```  

 請注意如何**attributeGroup**項目內之 XSD 表示法**記錄**節點參考全域**attributeGroup**加入做為子系的項目**結構描述**項目。 這個在結構描述的 XSD 表示法中之屬性群組的全域定義，允許在整個結構描述中的多個位置參考此屬性群組。  

> [!NOTE]
>  會自動提供的預設屬性群組名稱格式為 attrgroup*N*，其中*N*是單純遞增的數字。 您可以藉由提供新的、 唯一的名稱，在重新命名屬性群組及其**Group Reference**屬性。 您不能在結構描述樹狀結構中就地重新命名屬性群組。  

## <a name="see-also"></a>另請參閱  
- [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
- [節點屬性](../core/node-properties.md)   
- **Sequence 群組節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
- [如何設定節點屬性](../core/how-to-set-node-properties.md)   
- [欄位屬性節點](../core/field-attribute-nodes.md)   
- [Any 屬性節點](../core/any-attribute-nodes.md)
