---
title: 所有群組的節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e28d98c-746a-44d8-bed2-ba539b8432aa
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 084b12f16e72507a7d5568bdee022925eca52c0e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989231"
---
# <a name="all-group-nodes"></a>[All 群組] 節點
在 「 BizTalk 編輯器 」 中，您可以插入**All 群組**節點，以包含其他節點將出現零或一次，依任何順序。 在 XML 結構描述定義 (XSD) 語言中，**所有群組**有更多的使用量限制，比**順序**並**選擇**群組，進而轉譯成內的少數情況，BizTalk 編輯器 中，您可以在此處建立**All 群組**節點。  

 若要使用**All 群組**節點在 「 BizTalk 編輯器 」 中，您必須遵循一些額外的步驟： 建立最簡單的方式**All 群組**的值變更為節點**群組順序類型**屬性的父代**記錄**節點，以**所有**。 這可確保所有的附屬節點**記錄**內所包含的節點**All 群組**節點。  請參閱**群組順序類型** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

 若要使用的另一種方式**All 群組**在 [BizTalk 編輯器] 中節點的開頭插入新**記錄**節點。 插入新後**記錄**節點，變更其**內容類型**屬性設**ComplexContent**。 接著您可以插入**All 群組**節點的子系**記錄**節點。 這是必要的因為**All 群組**只有涉及繼承時要插入。 指定包含**記錄** 節點包含複雜內容，其資料類型會變成基礎資料類型**xs: anytype**、 由副檔名衍生。  

> [!NOTE]
>  在 BizTalk 編輯器**All 群組**節點以字串表示\<所有 > 結構描述樹狀結構檢視中。 如果您將參考設定為**All 群組**節點，例如為 x，則表示為\<Group: x > 結構描述樹狀結構檢視中。  

## <a name="xsd-representation"></a>XSD 表示法  
 **All 群組** 節點可插入**記錄**節點，但只有如果它是只有非屬性子節點**記錄**節點。 下列範例所示，在步驟中，新的方式**All 群組**節點會以 XML 結構描述定義 (XSD) 語言，為表示**所有**項目做為在 「 BizTalk 編輯器 」 中的步驟會執行 （利用命名節點若要釐清其身分識別。）  

```  
<xs:element name="NewRecord">  
    <xs:complexType />   
</xs:element>  
```  

 在之後加入新記錄，如所示，在前述 XSD 片段中，其**內容的型別**屬性變更為**ComplexContent**，產生的以下的 XSD 修改。  

```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
             <xs:extension base="xs:anyType" />  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  

 現在**All 群組**節點可以插入新的記錄，之子節點，下列 XSD 片段中所示。  

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

 最後，您可以插入適當的節點，做為新的子系**All 群組**節點。 下列範例所示**記錄**節點並**欄位項目**做為新的子節點插入節點**All 群組**節點。  

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
- [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
- [節點屬性](../core/node-properties.md)   
- **Sequence 群組節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] 
- [如何設定節點屬性](../core/how-to-set-node-properties.md)
