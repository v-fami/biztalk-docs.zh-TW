---
title: "Any 項目節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7e30fcf-31bc-4d48-9bc7-0be90e927127
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c24eb75020f715245fc2b17f4bc1f81a7e34cd35
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="any-element-nodes"></a>Any 項目節點
在 [BizTalk 編輯器] 中，您可以使用**Any 項目**節點來指示的位置執行個體訊息中未知的項目可能出現的位置。 這適用於您知道某個項目可能出現在執行個體訊息中的特定位置，但是您不知道項目的名稱，或是它的複雜程度。 如果您將放入**Any 項目**BizTalk 結構描述內的適當位置的節點可以處理訊息的這類未知的部分。 唯一的要求是對應的 XML 必須格式正確。  
  
> [!NOTE]
>  在 [BizTalk 編輯器] 中， **Any 項目**節點以字串表示\<任何 > 結構描述樹狀結構檢視中。  
  
> [!NOTE]
>  您可以控制的訊息未知的部分驗證為格式正確的 XML 使用**Process Contents**屬性。 在許多情況下，您可能需要設定**Process Contents**屬性**略過**位置的執行個體訊息的內容**Any 項目**来處理的節點。 保留預設值的**Strict**如**Process Contents**屬性會防止執行個體訊息無法通過驗證。  
> 
> 這個屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="xsd-representation"></a>XSD 表示法  
 當**Any 項目**節點加入至**記錄** 節點，或另一個節點，它可以在其中新增這類**Sequence 群組**， **Choice 群組**，或**All 群組**單一 XML 標記 節點，會新增到對應 XML 結構描述定義的結構描述 (XSD) 語言表示法。 在下列範例中，新**Any 項目**節點，其 XSD 表示法會以粗體類型顯示，已加入至現有**記錄**節點已包含**欄位項目**節點。  
  
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
  
 假設**Process Contents**屬性**Any 項目**節點設定為**略過**內的執行個體訊息是由這個結構描述片段中， **ExistingRecord**元素必須包含**[existingfieldelement]**項目，包含字串資料，後面接著任意複雜度的任何單一項目。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
 [節點屬性](../core/node-properties.md)   
 [如何設定節點屬性](../core/how-to-set-node-properties.md)   
 [Any 屬性節點](../core/any-attribute-nodes.md)