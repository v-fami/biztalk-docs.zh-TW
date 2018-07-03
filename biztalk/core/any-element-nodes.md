---
title: Any 項目節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7e30fcf-31bc-4d48-9bc7-0be90e927127
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 905d6c25c5c2021840f4257c29df015d4bcb374e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002431"
---
# <a name="any-element-nodes"></a>Any 項目節點
在 「 BizTalk 編輯器 」 中，您可以使用**Any 項目**節點來指示的位置執行個體訊息中未知的項目可能出現的位置。 這適用於您知道某個項目可能出現在執行個體訊息中的特定位置，但是您不知道項目的名稱，或是它的複雜程度。 如果您將放**Any 項目**BizTalk 結構描述中的適當位置的節點可以處理訊息的這類未知的部分。 唯一的要求是對應的 XML 必須格式正確。  
  
> [!NOTE]
>  在 BizTalk 編輯器**Any 項目**節點以字串表示\<任何\>結構描述樹狀結構檢視中。  
> 
> [!NOTE]
>  您可以控制要訊息未知的部分驗證為語式正確的 XML 所使用的程度**Process Contents**屬性。 在許多情況下，您可能需要設定**Process Contents**屬性設**略過**的位置執行個體訊息的內容**Any 項目**来處理的節點。 保留預設值**Strict** for **Process Contents**屬性會防止執行個體訊息無法通過驗證。  
> 
> 這個屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="xsd-representation"></a>XSD 表示法  
 當**Any 項目**節點新增至**記錄**節點，或另一個節點，它可以加入這類**Sequence 群組**， **Choice 群組**，或**所有群組**單一 XML 標記 節點，會新增到對應 XML 結構描述定義的結構描述 (XSD) 語言表示法。 在下列範例中，新**Any 項目**節點，其 XSD 表示法以粗體顯示，已加入至現有**記錄**節點，其中已包含**欄位項目**節點。  
  
```  
<xs:element name="ExistingRecord">  
    <xs:complexType>  
        <xs:sequence>  
             <xs:element name="ExistingFieldElement" type="xs:string" />  
            <xs:any />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
```  
  
 假設**Process Contents**屬性**Any 項目**節點設定為**略過**，於執行個體訊息會受到此結構描述片段，而**ExistingRecord**項目應該包含 **[existingfieldelement]** 元素，其中包含字串資料，後面接著任意複雜度的任何單一項目。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
 [節點屬性](../core/node-properties.md)   
 [如何設定節點屬性](../core/how-to-set-node-properties.md)   
 [Any 屬性節點](../core/any-attribute-nodes.md)