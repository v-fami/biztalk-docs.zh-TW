---
title: 任何屬性節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa2d25bc-3a8f-4fd9-acad-341b8e80c737
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82490a114149e3d4f71e3598900be5599c8a36e2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964644"
---
# <a name="any-attribute-nodes"></a>Any 屬性節點
在 [BizTalk 編輯器] 中，您可以使用**Any 屬性**節點來指示可能會出現與零或多個未知的屬性執行個體訊息中的 （已知） 項目。 這適用於您知道特定項目將會出現在執行個體訊息中的特定位置之情況，但是您不確定項目確實包括哪些屬性。 如果您將放入**Any 屬性**節點內**記錄**相關項目相關聯的節點，BizTalk 可以處理該項目，與所關聯的屬性唯一的需求語法正確 (attributeName ="attributeValue")。  
  
> [!NOTE]
>  在 [BizTalk 編輯器] 中， **Any 屬性**節點以字串表示\<AnyAttribute\>結構描述樹狀結構檢視中。  
  
> [!NOTE]
>  您可以控制的訊息未知的部分驗證為格式正確的 XML 使用**Process Contents**屬性。 在許多情況下，您可能需要設定**Process Contents**屬性**略過**位置的執行個體訊息的內容**Any 屬性**来處理的節點. 保留預設值的**Strict**如**Process Contents**屬性會防止執行個體訊息無法通過驗證。  
>
> 這個屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="xsd-representation"></a>XSD 表示法  
 當**Any 屬性**節點加入至**記錄**節點或**屬性群組**單一 XML 標記 節點，會新增到對應的 XML 結構描述定義 (XSD) 語言結構描述表示法。 在下列範例中，新**Any 屬性**節點，顯示其 XSD 表示法中粗體、 已新增至現有**記錄**節點已包含**欄位項目**節點。  
  
```  
<xs:element name="ExistingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
        <xs:anyAttribute />  
    </xs:complexType>  
</xs:element  
```  
  
 在上述範例中，新的 XSD 表示法**Any 屬性**節點加入**anyAttribute**包含結尾的項目 (**記錄**節點) **元素**項目、 外部**順序**項目，會在**complexType**項目。 這是 where 所有**屬性**以外使用的項目，**屬性群組**節點中，新增至它們包含**元素**項目。  
  
 現在，並假設**Process Contents**屬性**Any 屬性**節點設定為**略過**內的執行個體訊息是由這個結構描述片段中， **ExistingRecord**預期項目，而且它可以包含任何屬性，只要它們是格式正確 XML 語法。 (若要遵循 XSD 片段，在此範例中，它也必須包含 **[existingfieldelement]** 以及項目。)  
  
## <a name="see-also"></a>請參閱  
 [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
 [節點屬性](../core/node-properties.md)   
 [如何設定節點屬性](../core/how-to-set-node-properties.md)   
 [Any 項目節點](../core/any-element-nodes.md)