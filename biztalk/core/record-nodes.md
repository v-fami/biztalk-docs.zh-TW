---
title: 記錄節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43af077d-5db8-43ca-8bd0-e3a9e3ebe2b0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ec23dcf604e1bd454ba7e69a57c250cf3b1872f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982343"
---
# <a name="record-nodes"></a>記錄節點
在 「 BizTalk 編輯器 」 中，使用**記錄**節點，代表資訊的集合，其中的個別項目可以是：  

- 簡單資訊類型，像是字串和數字，以子欄位節點表示。 這些子欄位節點可以是**欄位項目**節點或**Field 屬性**節點。 如需這兩種類型的欄位節點的詳細資訊，請參閱[欄位項目節點](../core/field-element-nodes.md)並[欄位屬性節點](../core/field-attribute-nodes.md)。  

- 複雜類型的資訊，表示為子系**記錄**節點或群組節點 (**Sequence 群組**節點， **Choice 群組** 節點，或**All 群組**節點)。  

- 任何未經審視的資訊類型，表示為子系**Any 項目**或是**Any 屬性**節點。  

- 所表示的屬性群組的**屬性群組**節點。  

  當您插入新的子節點插入**記錄**節點、 子節點永遠會插入在目前的子節點結尾處。 中的 XML 結構描述定義 (XSD) 語言表示法中，其對應的區域，這表示非屬性項目會加入至結尾中的項目結尾加入新項目**順序**， **選擇**，**所有**，或**群組**項目和屬性項目加入任何其他的屬性項目，全部都發生之後結束**順序**，**選擇**，**所有**，或**群組**項目。  

## <a name="xsd-representation"></a>XSD 表示法  
 當第一次插入新的 XSD 表示法**記錄**節點包含只有三行，如下列範例所示。  

```  
<xs:element name="Record">  
      <xs:complexType />  
</xs:element>  
```  

 當其中三個屬性節點以外的任何子節點 (**Field 屬性**，**屬性群組**，和**Any 屬性**) 會新增至**記錄**節點，根據預設，它會放置在**順序**內的項目**complexType**項目。 **順序**時加入，並移除所有非屬性子節點也會刪除第一個非屬性子節點，就會加入項目。 所有的三種類型的屬性節點內新增**complexType**項目，外部，但之後**順序**項目。  

 **順序**內的非屬性子節點會加入的項目也可以**選擇**或是**所有**項目，如果您變更**群組順序類型 （節點所有的結構描述的屬性）** 屬性的結構描述樹狀結構中對應的節點**選擇**或是**所有**分別。  

 在下列範例中，**記錄**節點已重新命名的 shipTo。 內的位置**記錄**其中加入屬性和非屬性節點的節點會顯示在括號中。  

```  
<xs:element name="">  
    <xs:complexType>  
        <xs:sequence>  
            [Nonattribute child nodes of the record go here.]  
            [Always add new nonattribute child nodes to the end.]  
        </xs:sequence>  
            [Attribute child nodes of the record go here.]  
            [Always add new attribute child nodes to the end.]  
    </xs:complexType>  
</xs:element>  

```  

## <a name="see-also"></a>另請參閱  
- [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
- [節點屬性](../core/node-properties.md)   
- **記錄節點屬性**和**群組順序類型 （所有結構描述的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
- [如何設定節點屬性](../core/how-to-set-node-properties.md)
