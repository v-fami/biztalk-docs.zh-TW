---
title: "如何插入 Sequence 群組、 Choice 群組或 [All 群組] 節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19aee400-1369-4310-b1b4-1bfeb2643236
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e498eb5ec8e7aa1398cfb58732f978faa9d0b415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-insert-a-sequence-group-choice-group-or-all-group-node"></a>如何插入 Sequence 群組、 Choice 群組或 [All 群組] 節點
BizTalk 編輯器支援三種類型的群組節點的項目： **Sequence 群組**， **Choice 群組**，和**All 群組**。 這些不同類型的群組節點會在對應執行個體訊息中群組的子節點上建立不同的條件約束。 如需不同群組類型之條件約束的詳細資訊，請直接參閱 Web 上有關 XML 結構描述定義 (XSD) 語言的相關資訊。 如需這項資訊的連結，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。  
  
 BizTalk 編輯器也支援群組節點屬性、**屬性群組**節點。 這種類型的節點可讓一組屬性來定義一次，而且有與多個相關聯**記錄**節點在結構描述內。  
  
 當您建置到您的結構描述的結構**記錄**節點依預設，會假設包含子節點的已排序的時序，而由使用**順序**之 XSD 表示法中的項目結構描述。 您可以變更群組節點的類型，藉由變更其**順序類型**屬性。  
  
### <a name="to-insert-a-sequence-group-node-or-a-choice-group-node"></a>插入 Sequence 群組節點或 Choice 群組節點  
  
1.  在結構描述樹狀結構檢視中，選取**記錄**您想要插入的節點**Sequence 群組**節點或**Choice 群組**節點。  
  
2.  在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下  **Sequence 群組**或**Choice 群組**視情況。  
  
### <a name="to-insert-an-all-group-node"></a>插入 All 群組節點  
  
1.  在結構描述樹狀結構檢視中，選取 新**記錄**您想要插入的節點**All 群組**節點。  
  
2.  在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下  **All 群組**。  
  
> [!NOTE]
>  **All 群組**選項才可以使用 [BizTalk （或快顯）] 功能表時相關的父**記錄**節點符合 XSD 會加諸於使用的條件約束**所有**項目。  
  
> [!NOTE]
>  **All 群組**選項要求**記錄**節點具有基底資料型別。 指定節點的資料類型的快速方法是設定它**內容類型**至**複雜**。  
  
### <a name="to-insert-an-attribute-group-node"></a>插入 Attribute 群組節點  
  
1.  在結構描述樹狀結構檢視中，選取**記錄**您想要插入的節點**屬性群組**節點。  
  
2.  在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下 **屬性群組**。  
  
> [!NOTE]
>  如果您想要變更新插入的名稱**屬性群組**節點中，輸入新的名稱在其**群組參考**屬性。  
  
## <a name="see-also"></a>另請參閱  
 [將節點插入結構描述](../core/inserting-nodes-into-a-schema.md)