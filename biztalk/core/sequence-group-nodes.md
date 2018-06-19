---
title: Sequence 群組節點 |Microsoft 文件
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
ms.openlocfilehash: b92c2165a84e5d539eac434ab140389c145b24b4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974044"
---
# <a name="sequence-group-nodes"></a>[Sequence 群組] 節點

## <a name="overview"></a>概觀
在 [BizTalk 編輯器] 中，您可以插入**Sequence 群組**節點，以包含其他節點，必須出現在執行個體訊息中出現的順序相同**Sequence 群組**節點。 包含的節點必須是對應到 XML 項目的節點，但不能是對應到 XML 屬性的節點。  
  
> [!NOTE]
>  在 [BizTalk 編輯器] 中， **Sequence 群組**節點由與字串的預設\<順序\>結構描述樹狀結構檢視中。 如果您將參考設定至**Sequence 群組**節點，例如 x，則會呈現為\<Group: x\>結構描述樹狀結構檢視中。  
  
 您可能想要加入**Sequence 群組**宣告全域項目群組。  
  
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
  
 因為兩種情形中都有 GroupItem1 與 GroupItem2，所以您可以宣告一個同時為 Record1 及 Record2 之子項的全域序列群組。 如需如何宣告全域序列群組的逐步指示，請參閱[建立參考另一個節點或類型](../core/how-to-create-references-to-another-node-or-type.md)。  
  
 使用者可以變更要隱藏的群組**Choice 群組**節點或**All 群組**節點 (而不一定**Sequence 群組**節點) 藉由變更**群組順序類型**屬性。 這個屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="xsd-representation"></a>XSD 表示法  
 當**Sequence 群組**節點插入**記錄** 節點，它的任何其他子節點結尾插入**順序**，**選擇**，或**所有**中的項目**記錄**節點。 下列範例示範新**Sequence 群組**節點，以粗體的結尾插入**順序**中的項目**記錄**節點 (節點名稱為以釐清其身分識別）。  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
  
```  
  
## <a name="see-also"></a>請參閱  
-  [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
-  [節點屬性](../core/node-properties.md)   
-  **Sequence 群組節點屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
-  [如何設定節點屬性](../core/how-to-set-node-properties.md)