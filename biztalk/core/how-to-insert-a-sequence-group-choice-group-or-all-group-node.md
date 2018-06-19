---
title: 如何插入 Sequence 群組、 Choice 群組或 [All 群組] 節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19aee400-1369-4310-b1b4-1bfeb2643236
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e498eb5ec8e7aa1398cfb58732f978faa9d0b415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254838"
---
# <a name="how-to-insert-a-sequence-group-choice-group-or-all-group-node"></a><span data-ttu-id="688fa-102">如何插入 Sequence 群組、 Choice 群組或 [All 群組] 節點</span><span class="sxs-lookup"><span data-stu-id="688fa-102">How to Insert a Sequence Group, Choice Group, or All Group Node</span></span>
<span data-ttu-id="688fa-103">BizTalk 編輯器支援三種類型的群組節點的項目： **Sequence 群組**， **Choice 群組**，和**All 群組**。</span><span class="sxs-lookup"><span data-stu-id="688fa-103">BizTalk Editor supports three types of group nodes for elements: **Sequence Group**, **Choice Group**, and **All Group**.</span></span> <span data-ttu-id="688fa-104">這些不同類型的群組節點會在對應執行個體訊息中群組的子節點上建立不同的條件約束。</span><span class="sxs-lookup"><span data-stu-id="688fa-104">These different types of group nodes establish different constraints on the child nodes of the group in corresponding instance messages.</span></span> <span data-ttu-id="688fa-105">如需不同群組類型之條件約束的詳細資訊，請直接參閱 Web 上有關 XML 結構描述定義 (XSD) 語言的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="688fa-105">For information about the constraints of these different types of groups, you should refer directly to information about the XML Schema definition (XSD) language on the Web.</span></span> <span data-ttu-id="688fa-106">如需這項資訊的連結，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。</span><span class="sxs-lookup"><span data-stu-id="688fa-106">For links to this information, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
 <span data-ttu-id="688fa-107">BizTalk 編輯器也支援群組節點屬性、**屬性群組**節點。</span><span class="sxs-lookup"><span data-stu-id="688fa-107">BizTalk Editor also supports a group node for attributes, the **Attribute Group** node.</span></span> <span data-ttu-id="688fa-108">這種類型的節點可讓一組屬性來定義一次，而且有與多個相關聯**記錄**節點在結構描述內。</span><span class="sxs-lookup"><span data-stu-id="688fa-108">This type of node allows a set of attributes to be defined once, and then be associated with more than one **Record** node within the schema.</span></span>  
  
 <span data-ttu-id="688fa-109">當您建置到您的結構描述的結構**記錄**節點依預設，會假設包含子節點的已排序的時序，而由使用**順序**之 XSD 表示法中的項目結構描述。</span><span class="sxs-lookup"><span data-stu-id="688fa-109">When you build structure into your schema, **Record** nodes are assumed to contain ordered sequences of child nodes by default, and are represented by using **sequence** elements in the XSD representation of the schema.</span></span> <span data-ttu-id="688fa-110">您可以變更群組節點的類型，藉由變更其**順序類型**屬性。</span><span class="sxs-lookup"><span data-stu-id="688fa-110">You can change the type of a group node by changing its **Order Type** property.</span></span>  
  
### <a name="to-insert-a-sequence-group-node-or-a-choice-group-node"></a><span data-ttu-id="688fa-111">插入 Sequence 群組節點或 Choice 群組節點</span><span class="sxs-lookup"><span data-stu-id="688fa-111">To insert a Sequence Group node or a Choice Group node</span></span>  
  
1.  <span data-ttu-id="688fa-112">在結構描述樹狀結構檢視中，選取**記錄**您想要插入的節點**Sequence 群組**節點或**Choice 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="688fa-112">In the schema tree view, select the **Record** node in which you want to insert the **Sequence Group** node or the **Choice Group** node.</span></span>  
  
2.  <span data-ttu-id="688fa-113">在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下  **Sequence 群組**或**Choice 群組**視情況。</span><span class="sxs-lookup"><span data-stu-id="688fa-113">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Sequence Group** or **Choice Group**, as appropriate.</span></span>  
  
### <a name="to-insert-an-all-group-node"></a><span data-ttu-id="688fa-114">插入 All 群組節點</span><span class="sxs-lookup"><span data-stu-id="688fa-114">To insert an All Group node</span></span>  
  
1.  <span data-ttu-id="688fa-115">在結構描述樹狀結構檢視中，選取 新**記錄**您想要插入的節點**All 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="688fa-115">In the schema tree view, select the new **Record** node in which you want to insert the **All Group** node.</span></span>  
  
2.  <span data-ttu-id="688fa-116">在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下  **All 群組**。</span><span class="sxs-lookup"><span data-stu-id="688fa-116">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **All Group**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="688fa-117">**All 群組**選項才可以使用 [BizTalk （或快顯）] 功能表時相關的父**記錄**節點符合 XSD 會加諸於使用的條件約束**所有**項目。</span><span class="sxs-lookup"><span data-stu-id="688fa-117">The **All Group** choice is only available on the BizTalk (or shortcut) menu when the relevant parent **Record** node meets the constraints that XSD imposes on the use of the **all** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="688fa-118">**All 群組**選項要求**記錄**節點具有基底資料型別。</span><span class="sxs-lookup"><span data-stu-id="688fa-118">The **All Group** choice requires that the **Record** node have a base data type.</span></span> <span data-ttu-id="688fa-119">指定節點的資料類型的快速方法是設定它**內容類型**至**複雜**。</span><span class="sxs-lookup"><span data-stu-id="688fa-119">A quick way to give the node a data type is to set its **Content Type** to **Complex**.</span></span>  
  
### <a name="to-insert-an-attribute-group-node"></a><span data-ttu-id="688fa-120">插入 Attribute 群組節點</span><span class="sxs-lookup"><span data-stu-id="688fa-120">To insert an Attribute Group node</span></span>  
  
1.  <span data-ttu-id="688fa-121">在結構描述樹狀結構檢視中，選取**記錄**您想要插入的節點**屬性群組**節點。</span><span class="sxs-lookup"><span data-stu-id="688fa-121">In the schema tree view, select the **Record** node in which you want to insert the **Attribute Group** node.</span></span>  
  
2.  <span data-ttu-id="688fa-122">在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下 **屬性群組**。</span><span class="sxs-lookup"><span data-stu-id="688fa-122">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Attribute Group**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="688fa-123">如果您想要變更新插入的名稱**屬性群組**節點中，輸入新的名稱在其**群組參考**屬性。</span><span class="sxs-lookup"><span data-stu-id="688fa-123">If you want to change the name of the newly inserted **Attribute Group** node, type the new name in its **Group Reference** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="688fa-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="688fa-124">See Also</span></span>  
 [<span data-ttu-id="688fa-125">將節點插入結構描述</span><span class="sxs-lookup"><span data-stu-id="688fa-125">Inserting Nodes into a Schema</span></span>](../core/inserting-nodes-into-a-schema.md)