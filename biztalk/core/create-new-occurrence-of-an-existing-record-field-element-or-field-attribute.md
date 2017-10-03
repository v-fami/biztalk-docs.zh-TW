---
title: "如何建立現有的記錄]、 [欄位項目] 或 [欄位屬性節點的新項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02380f68-056c-47c4-a0d6-61d599a4685d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64f8974de22b7ee99a02d551553cb5e36f31a0d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-new-occurrence-of-an-existing-record-field-element-or-field-attribute-node"></a>如何建立現有的記錄]、 [欄位項目] 或 [欄位屬性節點的新項目
您可以建立新的執行個體的現有**記錄**，**欄位項目**，或**欄位屬性**節點這類的任何執行個體的後續修改會反映在所有執行個體。  
  
### <a name="to-create-a-new-instance-of-an-existing-record-field-element-or-field-attribute-node"></a>建立現有記錄、欄位項目或欄位屬性節點的新執行個體  
  
1.  選取原始**記錄**，**欄位項目**，或**欄位屬性** 節點，請確定其**基底資料型別**屬性設定正確，然後在其**資料結構型別**(**記錄**節點) 或其**資料型別**(**欄位項目**和**欄位屬性**節點) 屬性，輸入自訂資料型別名稱。  
  
2.  插入新**記錄**，**欄位項目**，或**欄位屬性**節點，並將下列屬性的自訂資料的其中一個輸入您在步驟 1 中所輸入的名稱。  
  
    -   資料結構型別 (**記錄**節點)  
  
    -   資料型別 (**欄位項目**和**欄位屬性**節點)  
  
    > [!NOTE]
    >  如果新**記錄**或**欄位項目**節點的同層級的原始節點，並給予新節點做為原始節點相同的名稱，您會看到訊息方塊，詢問關於相同範圍中的重複節點具有相同的名稱。 按一下**是**執行與步驟 2 中選擇的自訂資料類型名稱相同的動作。  
  
> [!NOTE]
>  您已建立的新執行個體的現有**記錄**，**欄位項目**，或**欄位屬性**節點。  
  
> [!NOTE]
>  某些屬性**記錄**，**欄位項目**，或**欄位屬性**節點執行個體會維持相同 （一個執行個體的變更是所有執行個體的變更），和其他屬性可以分別設定每個執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [將節點插入結構描述](../core/inserting-nodes-into-a-schema.md)