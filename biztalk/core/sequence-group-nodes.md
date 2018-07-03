---
title: Sequence 群組節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 139c3daa-a682-4bf7-bbb7-b5694ced0431
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c113d0cfd0f6055d55b0329bba3c1ec60bf835e8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019740"
---
# <a name="sequence-group-nodes"></a>[Sequence 群組] 節點

## <a name="overview"></a>概觀
在 「 BizTalk 編輯器 」 中，您可以插入**Sequence 群組**節點，以包含其他節點，必須出現在執行個體訊息中出現的順序相同**Sequence 群組**節點。 包含的節點必須是對應到 XML 項目的節點，但不能是對應到 XML 屬性的節點。  

> [!NOTE]
>  在 BizTalk 編輯器**Sequence 群組**節點都由預設的字串表示\<順序\>結構描述樹狀結構檢視中。 如果您將參考設定為**Sequence 群組**節點，例如 x，則會表示為數\<Group: x\>結構描述樹狀結構檢視中。  

 您可能想要新增**Sequence 群組**宣告全域項目群組。  

 您需要按照下列程式碼來建立 XML 的結構描述。  

```  
<Root>  
    <Record1>  
        <GroupItem1/>  
        <GroupItem2/>  
        <NotAGroupItem>  
    </Record1>  
    <Record2>  
        <GroupItem1/>  
        <GroupItem2/>  
    </Record2>  
</Root>  

```  

 因為兩種情形中都有 GroupItem1 與 GroupItem2，所以您可以宣告一個同時為 Record1 及 Record2 之子項的全域序列群組。 如需如何宣告全域序列群組的逐步指示，請參閱[另一個節點或類型中建立參考](../core/how-to-create-references-to-another-node-or-type.md)。  

 使用者可以變更隱藏的群組**Choice 群組** 節點或**All 群組**節點 (因此就不一定要是**Sequence 群組**節點) 藉由變更**群組順序類型**屬性。 這個屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

## <a name="xsd-representation"></a>XSD 表示法  
 當**Sequence 群組**節點插入**記錄**節點，插入內的任何其他子節點結尾處**順序**，**選擇**，或**所有**中的項目**記錄**節點。 下列範例示範新**Sequence 群組**節點，以粗體的結尾插入**順序**中的項目**記錄**節點 (以具名節點釐清其身分識別）。  

```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  

```  

## <a name="see-also"></a>另請參閱  
- [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
- [節點屬性](../core/node-properties.md)   
- **Sequence 群組節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
- [如何設定節點屬性](../core/how-to-set-node-properties.md)
