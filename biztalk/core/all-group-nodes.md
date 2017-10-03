---
title: "所有群組節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e28d98c-746a-44d8-bed2-ba539b8432aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f51d6420b7d754ffb8706e2bc729a02df00b4338
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="all-group-nodes"></a>[All 群組] 節點
在 [BizTalk 編輯器] 中，您可以插入**All 群組**節點，以包含其他節點將會出現零次或一次，以任何順序。 在 XML 結構描述定義 (XSD) 語言中， **All 群組**具有多個使用方式的限制比**順序**和**選擇**群組內的少數情況，轉譯BizTalk 編輯器 中，您可以在此處建立**All 群組**節點。  
  
 若要使用**All 群組**節點在 [BizTalk 編輯器] 中，您必須遵循一些額外的步驟： 建立最簡單的方式**All 群組**節點變更的值是**群組順序類型**屬性的父代**記錄**節點**所有**。 如此可確保所有的附屬節點**記錄**內所包含的節點**All 群組**節點。  請參閱**群組順序類型** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
 若要使用的另一種方式**All 群組**節點在 [BizTalk 編輯器] 中的開頭插入新**記錄**節點。 插入新後**記錄**節點，變更其**內容類型**屬性**ComplexContent**。 接著您可以插入**All 群組**節點的子系**記錄**節點。 這是必要的因為**All 群組**僅涉及繼承時能插入。 藉由指定包含**記錄**節點包含複雜內容，其資料類型會變成基礎資料型別**xs: anytype**、 延伸模組衍生。  
  
> [!NOTE]
>  在 [BizTalk 編輯器] 中， **All 群組**節點以字串表示\<所有 > 結構描述樹狀結構檢視中。 如果您將參考設定至**All 群組** 節點，例如為 x，則會呈現為\<Group: x > 結構描述樹狀結構檢視中。  
  
## <a name="xsd-representation"></a>XSD 表示法  
 **All 群組**節點可以插入到**記錄**節點，但它的非屬性子節點的**記錄**節點。 下列範例所示，在步驟中，如何為新**All 群組**節點 XML 結構描述定義 (XSD) 語言表示**所有**（利用命名節點執行幾個步驟在 [BizTalk 編輯器] 中的項目若要釐清其身分識別。）  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType />   
</xs:element>  
```  
  
 前述 XSD 片段中所示，新增新的記錄後其**內容類型**屬性變更為**ComplexContent**，並產生以下的 XSD 修改。  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
             <xs:extension base="xs:anyType" />  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  
  
 現在**All 群組**節點可插入為新的記錄的子系，下列 XSD 片段中所示。  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
            <xs:extension base="xs:anyType">  
                <xs:all />   
             </xs:extension>  
          </xs:complexContent>  
     </xs:complexType>  
</xs:element>  
```  
  
 最後，您可以插入適當的節點，做為新的子系**All 群組**節點。 下列範例所示**記錄**節點和**欄位項目**做為新的子節點插入節點**All 群組**節點。  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
            <xs:extension base="xs:anyType">  
                <xs:all>  
                    <xs:element name="RecordChildOfAllGroup">  
                        <xs:complexType />  
                    </xs:element>  
                    <xs:element name="FieldElementChildOfAllGroup" type="xs:string" />  
                </xs:all>  
            </xs:extension>  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  
  
## <a name="see-also"></a>另請參閱  
-  [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
-  [節點屬性](../core/node-properties.md)   
-  **Sequence 群組節點屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] 
-  [如何設定節點屬性](../core/how-to-set-node-properties.md)