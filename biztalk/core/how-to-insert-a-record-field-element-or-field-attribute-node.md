---
title: "如何插入 記錄、 欄位項目 或 欄位屬性節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c26f2281-f1b8-4788-8593-8d6ad29a53f0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1341a0f2d89070d42620396a8c86d497b5d646ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-insert-a-record-field-element-or-field-attribute-node"></a><span data-ttu-id="33aed-102">如何插入 記錄、 欄位項目 或 欄位屬性節點</span><span class="sxs-lookup"><span data-stu-id="33aed-102">How to Insert a Record, Field Element, or Field Attribute Node</span></span>
<span data-ttu-id="33aed-103">**記錄**節點 (包括**根**節點)，**欄位屬性**節點，和**欄位項目**節點之所以是唯一的它們可以重新命名，使其名稱代表對應的執行個體訊息中實際、 自訂名稱項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="33aed-103">**Record** nodes (including the **Root** node), **Field Attribute** nodes, and **Field Element** nodes are unique in that they can be renamed so that their names represent the names of the actual, custom-named elements in a corresponding instance message.</span></span> <span data-ttu-id="33aed-104">例如，如果您將檔案命名**記錄**節點為 FullName，在名為 FullName 的 XML 項目預期的執行個體訊息中對應的位置。</span><span class="sxs-lookup"><span data-stu-id="33aed-104">For example, if you name a **Record** node FullName, at the corresponding location in an instance message an XML element named FullName is expected.</span></span> <span data-ttu-id="33aed-105">如果該**記錄**名為 FullName 的節點有子系**欄位屬性**名為 RequireFullMiddleName 的節點 (使用其**Min Occurs**和**Max Occurs**屬性設定為**1**)、 **FullName**需要有名稱為的屬性對應的執行個體訊息中的項目**RequireFullMiddleName**與其相關聯。</span><span class="sxs-lookup"><span data-stu-id="33aed-105">If that **Record** node named FullName has a child **Field Attribute** node named RequireFullMiddleName (with its **Min Occurs** and **Max Occurs** properties set to **1**), the **FullName** element in a corresponding instance message will need to have an attribute named **RequireFullMiddleName** associated with it.</span></span>  
  
 <span data-ttu-id="33aed-106">所有**記錄**節點，當最初插入時，表示與 XSD **complexType**項目，但不是含後續**順序**，**選擇**，或**所有**項目。</span><span class="sxs-lookup"><span data-stu-id="33aed-106">All **Record** nodes, when initially inserted, are represented in the XSD as with a **complexType** element, but not with a subsequent **sequence**, **choice**, or **all** element.</span></span> <span data-ttu-id="33aed-107">基於這個理由，**群組順序類型**， **Group Max Occurs**，和**Group Min Occurs**屬性**記錄**節點則無法使用進行修改。</span><span class="sxs-lookup"><span data-stu-id="33aed-107">For this reason, the **Group Order Type**, **Group Max Occurs**, and **Group Min Occurs** properties of the **Record** node are not available for modification.</span></span>  
  
 <span data-ttu-id="33aed-108">一旦您新增一個子系**記錄**或**欄位項目**節點**記錄** 節點，**順序**元素會加入至 XSD表示內**complexType**項目來包含此第一個子節點，而**群組順序類型**屬性**記錄**節點會顯示值**順序**。</span><span class="sxs-lookup"><span data-stu-id="33aed-108">As soon as you add a child **Record** or **Field Element** node to the **Record** node, a **sequence** element is added to the XSD representation within the **complexType** element to contain this first child node, and the **Group Order Type** property of the **Record** node shows a value of **Sequence**.</span></span> <span data-ttu-id="33aed-109">在大部分情況下，您可以變更**群組順序類型**屬性從**順序**至**選擇**，並在更多限制的情況下，從**順序**至**所有**，藉此變更，其中包含對應子節點為項目組**complexType/choice**或**complexType/all**分別。</span><span class="sxs-lookup"><span data-stu-id="33aed-109">In most circumstances, you can change the **Group Order Type** property from **Sequence** to **Choice**, and in more limited circumstances, from **Sequence** to **All**, thereby changing the element pair that contains the corresponding child nodes to either **complexType/choice** or **complexType/all**, respectively.</span></span>  
  
 <span data-ttu-id="33aed-110">**欄位屬性**節點不能有相同的節點名稱與相同範圍中。</span><span class="sxs-lookup"><span data-stu-id="33aed-110">**Field Attribute** nodes cannot have the same node names while in the same scope.</span></span>  
  
 <span data-ttu-id="33aed-111">**記錄**和**欄位項目**節點可以有相同的節點名稱與相同範圍中，只有當符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="33aed-111">**Record** and **Field Element** nodes can have the same node names while in the same scope only if the following conditions are met:</span></span>  
  
-   <span data-ttu-id="33aed-112">它們的資料型別相同。</span><span class="sxs-lookup"><span data-stu-id="33aed-112">They have the same data type.</span></span>  
  
-   <span data-ttu-id="33aed-113">它們不在**All 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="33aed-113">They are not within an **All Group** node.</span></span>  
  
### <a name="to-insert-a-new-child-record-node-field-element-node-or-field-attribute-node-within-the-schema-node-or-an-existing-record-node"></a><span data-ttu-id="33aed-114">在結構描述節點或現有的 [記錄] 節點中插入新的子 [記錄] 節點、[欄位項目] 節點或 [欄位屬性] 節點</span><span class="sxs-lookup"><span data-stu-id="33aed-114">To insert a new child Record node, Field Element node, or Field Attribute node within the Schema node or an existing Record node</span></span>  
  
1.  <span data-ttu-id="33aed-115">選取**結構描述**節點或現有**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="33aed-115">Select the **Schema** node or an existing **Record** node.</span></span>  
  
2.  <span data-ttu-id="33aed-116">在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下 **子記錄**，**子欄位項目**，或**子欄位屬性**視情況。</span><span class="sxs-lookup"><span data-stu-id="33aed-116">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Child Record**, **Child Field Element**, or **Child Field Attribute**, as appropriate.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33aed-117">所選類型的子節點加入之後的最後一個節點在結構描述樹狀目錄中 (當插入**結構描述**節點) 或之後所選取的最後一個現有子節點**記錄**節點 （當插入現有**記錄**節點)。</span><span class="sxs-lookup"><span data-stu-id="33aed-117">A child node of the chosen type is added after either the last node in the schema tree (when inserting within the **Schema** node) or after the last existing child node of the selected **Record** node (when inserting within an existing **Record** node).</span></span>  
  
3.  <span data-ttu-id="33aed-118">輸入新插入的名稱**記錄**，**欄位項目**，或**欄位屬性**節點，然後再按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="33aed-118">Type a name for the newly inserted **Record**, **Field Element**, or **Field Attribute** node, and then press ENTER.</span></span>  
  
### <a name="to-insert-a-sibling-record-node-field-attribute-node-or-field-element-node-within-an-existing-record-node"></a><span data-ttu-id="33aed-119">在現有的 [記錄] 節點中插入同層級 [記錄] 節點、[欄位屬性] 節點或 [欄位項目] 節點</span><span class="sxs-lookup"><span data-stu-id="33aed-119">To insert a sibling Record node, Field Attribute node, or Field Element node within an existing Record node</span></span>  
  
1.  <span data-ttu-id="33aed-120">選取的任何子節點**記錄**要插入同層級節點**記錄**，**欄位屬性**，或**欄位項目**節點。</span><span class="sxs-lookup"><span data-stu-id="33aed-120">Select any child node of the **Record** node into which you want to insert the sibling **Record**, **Field Attribute**, or **Field Element** node.</span></span>  
  
2.  <span data-ttu-id="33aed-121">在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下 **同層級記錄**，**同層級欄位屬性**，或**同層級欄位項目**視情況。</span><span class="sxs-lookup"><span data-stu-id="33aed-121">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Sibling Record**, **Sibling Field Attribute**, or **Sibling Field Element**, as appropriate.</span></span>  
  
     <span data-ttu-id="33aed-122">所選類型的同層級節點便會插入在所選節點同層級的結尾處。</span><span class="sxs-lookup"><span data-stu-id="33aed-122">A sibling node of the chosen type is inserted at the end of the siblings of the selected node.</span></span>  
  
3.  <span data-ttu-id="33aed-123">輸入新插入的名稱**記錄**，**欄位屬性**，或**欄位項目**節點，然後再按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="33aed-123">Type a name for the newly inserted **Record**, **Field Attribute**, or **Field Element** node, and then press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33aed-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33aed-124">See Also</span></span>  
 [<span data-ttu-id="33aed-125">將節點插入結構描述</span><span class="sxs-lookup"><span data-stu-id="33aed-125">Inserting Nodes into a Schema</span></span>](../core/inserting-nodes-into-a-schema.md)