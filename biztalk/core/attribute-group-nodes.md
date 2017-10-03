---
title: "Attribute 群組 節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea02fae8-4e03-486a-8d9d-185ae230d3a0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04db816f1209b7cd503b9a162cdd2a030ba86292
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="attribute-group-nodes"></a>[Attribute 群組] 節點

## <a name="overview"></a>概觀
在 [BizTalk 編輯器] 中，您可以加入**屬性群組**節點**記錄**節點或另一個**屬性群組**節點，以包含您要使用更多的屬性群組於其中**記錄**節點。 加入**屬性群組**節點至另一個**屬性群組**節點，可達成屬性群組巢狀化。 這可讓您定義的屬性群組在一個地方可以用於多個**記錄**或**屬性群組**節點。 對屬性群組後續的修改將會傳播至與該屬性群組關聯的所有節點。 不論修改的節點內容為何，都會這麼做。  
  
> [!NOTE]
>  在 [BizTalk 編輯器] 中， **AttributeGroup**節點由與字串的預設\<AttribGroup:attribGroup*N*> 在結構描述樹狀結構檢視中，其中*N*是單純遞增的數字。 您可以變更 attribGroup*N*輸入新的唯一名稱，在其名稱部分其**群組參考**屬性。  
  
 當您開始建立**屬性群組** 節點，您只要將它插入其中**記錄**或**屬性群組**節點，它將會使用，並選擇性地變更其名稱中的其**群組參考**屬性。 有兩種方式，在另一個使用相同的屬性群組**記錄**或**屬性群組**節點：  
  
-   您可以複製現有**屬性群組**節點，然後將它貼到另**記錄**節點。  
  
-   您可以插入新**屬性群組**節點插入另**記錄** 節點，並將其設定**群組參考**屬性的新**屬性群組**節點，以參考現有**屬性群組**節點。  
  
 之後，您可以修改**屬性群組**節點 — 比方說，藉由新增或刪除**欄位屬性**節點 — 在任何內容**記錄**或**屬性群組**到您所貼上它的節點。 變更會傳播到所有其他**記錄**或**屬性群組**屬性群組在相關聯的節點。  
  
 它是毫無意義，以新增**屬性群組**節點卻沒有新增至少一個相關的節點，也就是相關的節點包含**欄位屬性**節點**Any 屬性**節點，以及 （巢狀）**屬性群組**節點。 事實上，屬性群組僅包含單一屬性有些不妥當，除非您特別計劃在未來新增更多屬性。  
  
 **屬性群組**節點可以巢狀，允許更多可以如何建構和結合屬性群組的可能性。 **屬性群組**節點也可以包含**Any 屬性**節點，允許屬性群組包含對於屬性執行個體，它能容納的萬用字元功能。  
  
## <a name="xsd-representation"></a>XSD 表示法  
 當**屬性群組**節點初次加入至**記錄**節點或另一個**屬性群組**節點、 兩個不同區域的相對應的 XML 結構描述定義 (XSD)結構描述的語言表示法會受到影響。 在下列範例中，新**屬性群組** 節點，在粗體、 已新增至現有**記錄**已包含現有的節點**欄位項目**節點。  
  
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
  
 請注意如何**attributeGroup**的 XSD 表示法中的項目**記錄**節點所參考的全域**attributeGroup**加入做為子系的項目**結構描述**項目。 這個在結構描述的 XSD 表示法中之屬性群組的全域定義，允許在整個結構描述中的多個位置參考此屬性群組。  
  
> [!NOTE]
>  自動提供的預設屬性群組名稱格式為 attrgroup*N*，其中*N*是單純遞增的數字。 您可以藉由提供中新的、 唯一的名稱重新命名屬性群組其**群組參考**屬性。 您不能在結構描述樹狀結構中就地重新命名屬性群組。  
  
## <a name="see-also"></a>另請參閱  
-  [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
-  [節點屬性](../core/node-properties.md)   
-  **Sequence 群組節點屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
-  [如何設定節點屬性](../core/how-to-set-node-properties.md)   
-  [欄位屬性節點](../core/field-attribute-nodes.md)   
-  [Any 屬性節點](../core/any-attribute-nodes.md)