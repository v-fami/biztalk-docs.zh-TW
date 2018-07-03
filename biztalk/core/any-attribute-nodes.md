---
title: 任何屬性節點 |Microsoft Docs
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
ms.openlocfilehash: 98cbd0ea288e14b68bc16f5e9a88f636bc229b9d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014479"
---
# <a name="any-attribute-nodes"></a>Any 屬性節點
在 「 BizTalk 編輯器 」 中，您可以使用**Any 屬性**表示 （已知） 的項目，可能會出現與零個或多個未知的屬性執行個體訊息中的節點。 這適用於您知道特定項目將會出現在執行個體訊息中的特定位置之情況，但是您不確定項目確實包括哪些屬性。 如果您將放**Any 屬性**內的節點**記錄**與相關的項目相關聯的節點，BizTalk 可以處理該項目，與在任何相關聯的屬性唯一的需求語法正確 (attributeName ="attributeValue")。  
  
> [!NOTE]
>  在 BizTalk 編輯器**Any 屬性**節點以字串表示\<AnyAttribute\>結構描述樹狀結構檢視中。  
> 
> [!NOTE]
>  您可以控制要訊息未知的部分驗證為語式正確的 XML 所使用的程度**Process Contents**屬性。 在許多情況下，您可能需要設定**Process Contents**屬性設**略過**的位置執行個體訊息的內容**Any 屬性**来處理的節點. 保留預設值**Strict** for **Process Contents**屬性會防止執行個體訊息無法通過驗證。  
> 
> 這個屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="xsd-representation"></a>XSD 表示法  
 當**Any 屬性**節點新增至**記錄**節點，或者**屬性群組**單一 XML 標記 節點，會新增到對應的 XML 結構描述定義 (XSD) 語言結構描述表示法。 在下列範例中，新**Any 屬性**節點，其 XSD 表示法會顯示在粗體，已新增至現有**記錄**節點，其中已包含**欄位項目**節點。  
  
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
  
 在上述範例中，新的 XSD 表示法**Any 屬性**節點會加入**anyAttribute**包含結尾的項目 (**記錄**節點) **項目**項目、 外部**序列**項目，會在**complexType**項目。 這正是所有**屬性**項目，與以外**屬性群組**節點，新增至它們包含**項目**項目。  
  
 到目前為止，並假設**Process Contents**屬性**Any 屬性**節點設定為**略過**，於執行個體訊息會受到此結構描述片段，而**ExistingRecord**預期項目，而且它可以包含任何屬性，因此只要它們是格式正確 XML 語法。 (若要遵循 XSD 片段，在此範例中，它也必須包含 **[existingfieldelement]** 項目。)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
 [節點屬性](../core/node-properties.md)   
 [如何設定節點屬性](../core/how-to-set-node-properties.md)   
 [Any 項目節點](../core/any-element-nodes.md)