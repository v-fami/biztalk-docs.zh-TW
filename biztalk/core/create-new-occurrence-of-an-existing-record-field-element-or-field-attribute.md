---
title: 如何建立現有的記錄]、 [欄位項目] 或 [欄位屬性節點的新項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 02380f68-056c-47c4-a0d6-61d599a4685d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64f8974de22b7ee99a02d551553cb5e36f31a0d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238174"
---
# <a name="how-to-create-a-new-occurrence-of-an-existing-record-field-element-or-field-attribute-node"></a><span data-ttu-id="845c3-102">如何建立現有的記錄]、 [欄位項目] 或 [欄位屬性節點的新項目</span><span class="sxs-lookup"><span data-stu-id="845c3-102">How to Create a New Occurrence of an Existing Record, Field Element, or Field Attribute Node</span></span>
<span data-ttu-id="845c3-103">您可以建立新的執行個體的現有**記錄**，**欄位項目**，或**欄位屬性**節點這類的任何執行個體的後續修改會反映在所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="845c3-103">You can create new instances of an existing **Record**, **Field Element**, or **Field Attribute** node such that subsequent modifications to any instance are reflected in all instances.</span></span>  
  
### <a name="to-create-a-new-instance-of-an-existing-record-field-element-or-field-attribute-node"></a><span data-ttu-id="845c3-104">建立現有記錄、欄位項目或欄位屬性節點的新執行個體</span><span class="sxs-lookup"><span data-stu-id="845c3-104">To create a new instance of an existing Record, Field Element, or Field Attribute node</span></span>  
  
1.  <span data-ttu-id="845c3-105">選取原始**記錄**，**欄位項目**，或**欄位屬性** 節點，請確定其**基底資料型別**屬性設定正確，然後在其**資料結構型別**(**記錄**節點) 或其**資料型別**(**欄位項目**和**欄位屬性**節點) 屬性，輸入自訂資料型別名稱。</span><span class="sxs-lookup"><span data-stu-id="845c3-105">Select the original **Record**, **Field Element**, or **Field Attribute** node, make sure its **Base Data Type** property is set correctly, and then in its **Data Structure Type** (**Record** nodes) or its **Data Type** (**Field Element** and **Field Attribute** nodes) property, type a custom data type name.</span></span>  
  
2.  <span data-ttu-id="845c3-106">插入新**記錄**，**欄位項目**，或**欄位屬性**節點，並將下列屬性的自訂資料的其中一個輸入您在步驟 1 中所輸入的名稱。</span><span class="sxs-lookup"><span data-stu-id="845c3-106">Insert the new **Record**, **Field Element**, or **Field Attribute** node and set one of the following properties to the custom data type name you typed in step 1.</span></span>  
  
    -   <span data-ttu-id="845c3-107">資料結構型別 (**記錄**節點)</span><span class="sxs-lookup"><span data-stu-id="845c3-107">Data Structure Type (**Record** nodes)</span></span>  
  
    -   <span data-ttu-id="845c3-108">資料型別 (**欄位項目**和**欄位屬性**節點)</span><span class="sxs-lookup"><span data-stu-id="845c3-108">Data Type (**Field Element** and **Field Attribute** nodes)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="845c3-109">如果新**記錄**或**欄位項目**節點的同層級的原始節點，並給予新節點做為原始節點相同的名稱，您會看到訊息方塊，詢問關於相同範圍中的重複節點具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="845c3-109">If a new **Record** or **Field Element** node is a sibling of the original node, and you give the new node the same name as the original node, you will see a message box asking about duplicate nodes in the same scope with the same name.</span></span> <span data-ttu-id="845c3-110">按一下**是**執行與步驟 2 中選擇的自訂資料類型名稱相同的動作。</span><span class="sxs-lookup"><span data-stu-id="845c3-110">Clicking **Yes** performs the same action as choosing the custom data type name in step 2.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="845c3-111">您已建立的新執行個體的現有**記錄**，**欄位項目**，或**欄位屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="845c3-111">You have created a new instance of the existing **Record**, **Field Element**, or **Field Attribute** node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="845c3-112">某些屬性**記錄**，**欄位項目**，或**欄位屬性**節點執行個體會維持相同 （一個執行個體的變更是所有執行個體的變更），和其他屬性可以分別設定每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="845c3-112">Some properties of **Record**, **Field Element**, or **Field Attribute** node instances remain identical (a change to one instance is a change to all instances), and other properties can be set independently for each instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845c3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="845c3-113">See Also</span></span>  
 [<span data-ttu-id="845c3-114">將節點插入結構描述</span><span class="sxs-lookup"><span data-stu-id="845c3-114">Inserting Nodes into a Schema</span></span>](../core/inserting-nodes-into-a-schema.md)