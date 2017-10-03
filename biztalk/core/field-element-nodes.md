---
title: "欄位項目節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65b5e1f6-283f-4172-9bc2-f04a0ea6753d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74c3732ee315ad307f49760e367449216c3e01da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="field-element-nodes"></a>欄位項目節點

## <a name="overview"></a>概觀
在 「 BizTalk 編輯器 」 中，使用**欄位項目**節點，以描述的資訊是簡單的本質，例如字串和數字的項目。 此外，當使用中的資訊顯示為實際訊息執行個體中的 XML 項目內容，而非顯示為與 XML 項目相關聯的屬性值時，也會使用它們。 其他資訊儲存成屬性值的詳細資訊，請參閱[欄位屬性節點](../core/field-attribute-nodes.md)。  
  
> [!NOTE]
>  在 [BizTalk 編輯器] 中，項目和屬性項目可由**欄位**節點，但是它們具有不同結構描述樹狀檢視中，在 XSD 視窗中，有不同的 XML 表示法中與它們相關聯的圖示和在 Visual Studio 屬性視窗不同的屬性。  
  
 對於 XML 訊息中任一項指定資訊 (此處的資訊是指單一不連續的簡單型別，例如字串或數字) 來說，有個永遠存在的相關問題，就是應將該資訊表示為項目的屬性，還是該項目的子項目。 就一般規則而言，當可能的值為不連續值、數目很少，且可能更改項目本身的語意時，將資訊表示為屬性會較為適當。 當可能的值可根據變數設定重複多次、可能有較大範圍的值、可能很長 (如長字串)，且是順序相關的數個同層級值中的一個時，則將資訊表示為子項目較為適當。 若您剛建立的現有類型的 XML 結構描述文件，您選擇使用**欄位項目**節點或**欄位屬性**已發出的特定資訊項目 節點，而且，您必須使用符合 XML 的節點。  
  
## <a name="xsd-representation"></a>XSD 表示法  
 當**欄位項目**節點插入**記錄** 節點，它的任何其他子節點結尾插入**順序**中的項目**記錄**節點。 下列範例示範新**欄位項目**節點，以粗體顯示、 結尾處插入**順序**中的項目**記錄**（利用命名以釐清其識別節點的節點).  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
            <xs:element name="EmptyNestedRecord">  
                <xs:complexType />  
            </xs:element>  
  
        </xs:sequence>  
        <xs:attribute name="ExistingFieldAttribute" type="xs:string" />  
    </xs:complexType>  
</xs:element>  
  
```  
  
## <a name="see-also"></a>另請參閱  
-  [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
-  [節點屬性](../core/node-properties.md)   
-  **欄位項目節點屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
-  [如何設定節點屬性](../core/how-to-set-node-properties.md)