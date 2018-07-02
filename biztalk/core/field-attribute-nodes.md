---
title: 欄位屬性節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e964c07-53e5-473f-84f2-05af4796cbbe
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef3cbf401ce5408c59ae164ca528c41a647eba2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972135"
---
# <a name="field-attribute-nodes"></a>欄位屬性節點

## <a name="overview"></a>概觀
在 「 BizTalk 編輯器 」 中，使用**Field 屬性**節點，以描述性質，例如字串和數字簡單的資訊項目。 此外，當上述資訊顯示為實際訊息執行個體中屬性的值，而非顯示為 XML 項目的內容時，也可使用這類節點。 如需詳細資訊會儲存為項目內容的詳細資訊，請參閱[欄位項目節點](../core/field-element-nodes.md)。  

 雖然最直接的用法**Field 屬性**節點會做為子節點的**記錄**節點，也可以用做為子節點的**屬性群組**節點。 在後者的情況下， **Field 屬性**節點的子系**屬性群組**節點，可做為屬性的任何**記錄**節點，其中包含該**屬性群組**節點。 如需詳細資訊**屬性群組**節點，請參閱[屬性群組節點](../core/attribute-group-nodes.md)。  

> [!NOTE]
>  在 「 BizTalk 編輯器 」 中，項目和屬性項目可以呈現**欄位**節點，但是它們有不同結構描述樹狀檢視中，在 XSD 視窗中，有不同的 XML 表示法中與其相關聯的圖示和在 Visual Studio 的 [屬性] 視窗中的不同屬性。  

 對於 XML 訊息中任一項指定資訊 (此處的資訊是指單一不連續的簡單型別，例如字串或數字) 來說，有個永遠存在的相關問題，就是應將該資訊表示為項目的屬性，還是該項目的子項目。 就一般規則而言，當可能的值為不連續值、數目很少，且可能更改項目本身的語意時，將資訊表示為屬性會較為適當。 當可能的值可根據變數設定重複多次、可能有較大範圍的值、可能很長 (如長字串)，且是順序相關的數個同層級值中的一個時，則將資訊表示為子項目較為適當。 如果您要建立結構描述為現有類型的 XML 文件，您選擇使用**欄位項目**節點或**Field 屬性**，已建立的特定資訊項目 節點和您必須使用符合 XML 的節點。  

> [!NOTE]
>  根節點不能有**欄位**屬性。 **欄位**屬性附加至**根**節點不會儲存與結構描述。  

## <a name="xsd-representation"></a>XSD 表示法  
 當**欄位屬性**節點插入**記錄**節點，它會在任何其他子節點結尾處插入**記錄**節點。 這包括插**順序**，**選擇**，或**所有**元素，其中包含任何非屬性節點，和先前的任何屬性節點之後插入。 下列範例示範新**欄位屬性**節點，以粗體顯示，它插在結尾**記錄**（利用命名以釐清其身分識別的節點） 的節點。  

```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="FieldElement" type="xs:string" />  
            <xs:element name="EmptyNestedRecord">  
                <xs:complexType />  
            </xs:element>  
        </xs:sequence>  
        <xs:attribute name="ExistingFieldAttribute" type="xs:string" />  

    </xs:complexType>  
</xs:element>  

```  

## <a name="see-also"></a>另請參閱  
- [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
- [節點屬性](../core/node-properties.md)   
- **欄位項目節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
- [如何設定節點屬性](../core/how-to-set-node-properties.md)   
- [Attribute 群組節點](../core/attribute-group-nodes.md)
