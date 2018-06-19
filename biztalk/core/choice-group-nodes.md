---
title: Choice 群組節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 466b525d-4d8c-4b8e-830d-eee27845c0dc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21d3007897343b7d517c11599a271b72e92d3710
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970396"
---
# <a name="choice-group-nodes"></a>Choice 群組節點
在 [BizTalk 編輯器] 中，您可以插入**Choice 群組**節點，以包含其他節點 （或整個子樹狀結構的節點），其中只有一個可以出現在執行個體訊息。 指定的執行個體訊息若有效，將只有其中一個選擇存在。 包含的節點必須是對應到 XML 項目的節點，但不能是對應到 XML 屬性的節點。  
  
> [!NOTE]
>  在 [BizTalk 編輯器] 中， **Choice 群組**節點以字串表示\<選擇\>結構描述樹狀結構檢視中。 如果您將參考設定至**Choice 群組**節點，例如 x，則會呈現為\<Group: x\>結構描述樹狀結構檢視中。  
  
## <a name="xsd-representation"></a>XSD 表示法  
 當**Choice 群組**節點插入**記錄** 節點，它的任何其他子節點結尾插入**順序**，**選擇**，或**所有**中的項目**記錄**節點。 下列範例所示，以粗體方式新**Choice 群組**節點 XML 結構描述定義 (XSD) 語言表示**選擇**結尾處插入項目的**順序**中的項目**記錄**（利用命名以釐清其識別的節點） 的節點。  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
  
```  
  
 根據預設，**選擇**項目提供**minOccurs**屬性值為零 (0)，表示需要進行任何選擇。 您可以變更此值在 Visual Studio 屬性 視窗時**Choice 群組**結構描述樹狀結構檢視中選取節點。  
  
 下列範例顯示相同**選擇**具有 XSD 項目**元素**項目對應到兩個附屬**記錄**節點。  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
            <xs:choice minOccurs="1" maxOccurs="1">  
                <xs:element name="usAddress">  
                    <xs:complexType>  
                        <xs:sequence>  
                        </xs:sequence>  
                    </xs:complexType>  
                </xs:element>  
                <xs:element name="foreignAddress">  
                    <xs:complexType>  
                        <xs:sequence>  
                        </xs:sequence>  
                    </xs:complexType>  
                </xs:element>  
            </xs:choice>  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
```  
  
 在此範例中，兩個同層級**記錄**節點用來描述事實的執行個體訊息將會有的記錄中包含美國地址資訊或全球地址資訊的記錄。 此外， **minOccurs**和**maxOccurs**屬性**Choice 群組**節點都已設定為一 (1) 在 Visual Studio 屬性視窗中，導致*minOccurs*和*maxOccurs*屬性**選擇**設為一 (1) 之 XSD 表示中的項目。  
  
## <a name="see-also"></a>請參閱  
-  [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
-  [節點屬性](../core/node-properties.md)   
-  **Sequence 群組節點屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]     
-  [如何設定節點屬性](../core/how-to-set-node-properties.md)