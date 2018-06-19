---
title: 如何插入 記錄、 欄位項目 或 欄位屬性節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c26f2281-f1b8-4788-8593-8d6ad29a53f0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1341a0f2d89070d42620396a8c86d497b5d646ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255094"
---
# <a name="how-to-insert-a-record-field-element-or-field-attribute-node"></a>如何插入 記錄、 欄位項目 或 欄位屬性節點
**記錄**節點 (包括**根**節點)，**欄位屬性**節點，和**欄位項目**節點之所以是唯一的它們可以重新命名，使其名稱代表對應的執行個體訊息中實際、 自訂名稱項目的名稱。 例如，如果您將檔案命名**記錄**節點為 FullName，在名為 FullName 的 XML 項目預期的執行個體訊息中對應的位置。 如果該**記錄**名為 FullName 的節點有子系**欄位屬性**名為 RequireFullMiddleName 的節點 (使用其**Min Occurs**和**Max Occurs**屬性設定為**1**)、 **FullName**需要有名稱為的屬性對應的執行個體訊息中的項目**RequireFullMiddleName**與其相關聯。  
  
 所有**記錄**節點，當最初插入時，表示與 XSD **complexType**項目，但不是含後續**順序**，**選擇**，或**所有**項目。 基於這個理由，**群組順序類型**， **Group Max Occurs**，和**Group Min Occurs**屬性**記錄**節點則無法使用進行修改。  
  
 一旦您新增一個子系**記錄**或**欄位項目**節點**記錄** 節點，**順序**元素會加入至 XSD表示內**complexType**項目來包含此第一個子節點，而**群組順序類型**屬性**記錄**節點會顯示值**順序**。 在大部分情況下，您可以變更**群組順序類型**屬性從**順序**至**選擇**，並在更多限制的情況下，從**順序**至**所有**，藉此變更，其中包含對應子節點為項目組**complexType/choice**或**complexType/all**分別。  
  
 **欄位屬性**節點不能有相同的節點名稱與相同範圍中。  
  
 **記錄**和**欄位項目**節點可以有相同的節點名稱與相同範圍中，只有當符合下列條件：  
  
-   它們的資料型別相同。  
  
-   它們不在**All 群組**節點。  
  
### <a name="to-insert-a-new-child-record-node-field-element-node-or-field-attribute-node-within-the-schema-node-or-an-existing-record-node"></a>在結構描述節點或現有的 [記錄] 節點中插入新的子 [記錄] 節點、[欄位項目] 節點或 [欄位屬性] 節點  
  
1.  選取**結構描述**節點或現有**記錄**節點。  
  
2.  在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下 **子記錄**，**子欄位項目**，或**子欄位屬性**視情況。  
  
    > [!NOTE]
    >  所選類型的子節點加入之後的最後一個節點在結構描述樹狀目錄中 (當插入**結構描述**節點) 或之後所選取的最後一個現有子節點**記錄**節點 （當插入現有**記錄**節點)。  
  
3.  輸入新插入的名稱**記錄**，**欄位項目**，或**欄位屬性**節點，然後再按 ENTER 鍵。  
  
### <a name="to-insert-a-sibling-record-node-field-attribute-node-or-field-element-node-within-an-existing-record-node"></a>在現有的 [記錄] 節點中插入同層級 [記錄] 節點、[欄位屬性] 節點或 [欄位項目] 節點  
  
1.  選取的任何子節點**記錄**要插入同層級節點**記錄**，**欄位屬性**，或**欄位項目**節點。  
  
2.  在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下 **同層級記錄**，**同層級欄位屬性**，或**同層級欄位項目**視情況。  
  
     所選類型的同層級節點便會插入在所選節點同層級的結尾處。  
  
3.  輸入新插入的名稱**記錄**，**欄位屬性**，或**欄位項目**節點，然後再按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [將節點插入結構描述](../core/inserting-nodes-into-a-schema.md)