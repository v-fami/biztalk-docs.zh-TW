---
title: Attribute 群組 節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea02fae8-4e03-486a-8d9d-185ae230d3a0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7314c14a611096f92c8fd2f95b300832d6b44a0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017262"
---
# <a name="attribute-group-nodes"></a><span data-ttu-id="a52cd-102">[Attribute 群組] 節點</span><span class="sxs-lookup"><span data-stu-id="a52cd-102">Attribute Group Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="a52cd-103">概觀</span><span class="sxs-lookup"><span data-stu-id="a52cd-103">Overview</span></span>
<span data-ttu-id="a52cd-104">在 「 BizTalk 編輯器 」 中，您可以新增**屬性群組**節點，以**記錄**節點或另一個**屬性群組**節點，以包含您要用於多個屬性群組以外**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="a52cd-104">In BizTalk Editor, you can add an **Attribute Group** node to a **Record** node or to another **Attribute Group** node to contain a group of attributes that you expect to use in more than one **Record** node.</span></span> <span data-ttu-id="a52cd-105">新增**屬性群組**節點至另一個**屬性群組**節點，可達成屬性群組巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="a52cd-105">Adding an **Attribute Group** node to another **Attribute Group** node achieves attribute group nesting.</span></span> <span data-ttu-id="a52cd-106">這可讓您定義的屬性群組在一個地方可以用於多個**記錄**或是**屬性群組**節點。</span><span class="sxs-lookup"><span data-stu-id="a52cd-106">This allows you to define a group of attributes in one place that can be used in multiple **Record** or **Attribute Group** nodes.</span></span> <span data-ttu-id="a52cd-107">對屬性群組後續的修改將會傳播至與該屬性群組關聯的所有節點。</span><span class="sxs-lookup"><span data-stu-id="a52cd-107">Subsequent modifications to the attribute group will propagate to all of the nodes with which that attribute group is associated.</span></span> <span data-ttu-id="a52cd-108">不論修改的節點內容為何，都會這麼做。</span><span class="sxs-lookup"><span data-stu-id="a52cd-108">This is true regardless of the node context in which the modifications are made.</span></span>  

> [!NOTE]
>  <span data-ttu-id="a52cd-109">在 BizTalk 編輯器**AttributeGroup**節點都由預設的字串表示\<AttribGroup:attribGroup*N* \>在結構描述樹狀結構檢視中，其中*N*是單純遞增的數字。</span><span class="sxs-lookup"><span data-stu-id="a52cd-109">In BizTalk Editor, the **AttributeGroup** node is represented by default with the string \<AttribGroup:attribGroup*N*\> in the schema tree view, where *N* is a monotonically increasing numeral.</span></span> <span data-ttu-id="a52cd-110">您可以變更 attribGroup*N*部分輸入新的唯一名稱，在其名稱及其**Group Reference**屬性。</span><span class="sxs-lookup"><span data-stu-id="a52cd-110">You can change the attribGroup*N* portion of its name by typing a new unique name in its **Group Reference** property.</span></span>  

 <span data-ttu-id="a52cd-111">一開始建立時**屬性群組**節點，您只需將它插入其中一個**記錄**或是**屬性群組**節點，它將會使用，並選擇性地變更在其名稱與其**Group Reference**屬性。</span><span class="sxs-lookup"><span data-stu-id="a52cd-111">When initially creating an **Attribute Group** node, you simply insert it into one of the **Record** or **Attribute Group** nodes in which it will be used, and optionally change its name in its **Group Reference** property.</span></span> <span data-ttu-id="a52cd-112">有兩種方式可使用相同的屬性群組在另一個**記錄**或是**屬性群組**節點：</span><span class="sxs-lookup"><span data-stu-id="a52cd-112">There are two ways to use the same attribute group in another **Record** or **Attribute Group** node:</span></span>  

- <span data-ttu-id="a52cd-113">您可以複製現有**屬性群組**節點，然後將它貼到另**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="a52cd-113">You can copy the existing **Attribute Group** node and then paste it into that other **Record** node.</span></span>  

- <span data-ttu-id="a52cd-114">您可以插入新**屬性群組**節點插入另**記錄**節點，然後再把**Group Reference**屬性的新**屬性群組**節點，以參考現有**屬性群組**節點。</span><span class="sxs-lookup"><span data-stu-id="a52cd-114">You can insert a new **Attribute Group** node into that other **Record** node, and then set the **Group Reference** property of the new **Attribute Group** node to reference an existing **Attribute Group** node.</span></span>  

  <span data-ttu-id="a52cd-115">之後，您可以在其中修改**屬性群組**節點 — 比方說，藉由新增或刪除**Field 屬性**節點 — 中的任何內容**記錄**或**屬性群組**至您貼上它的節點。</span><span class="sxs-lookup"><span data-stu-id="a52cd-115">Thereafter, you can modify the **Attribute Group** node—for example, by adding or deleting a **Field Attribute** node—in the context of any **Record** or **Attribute Group** node into which you pasted it.</span></span> <span data-ttu-id="a52cd-116">變更會傳播到所有其他**記錄**或是**屬性群組**與屬性群組相關聯的節點。</span><span class="sxs-lookup"><span data-stu-id="a52cd-116">That change will propagate to all other **Record** or **Attribute Group** nodes with which the attribute group is associated.</span></span>  

  <span data-ttu-id="a52cd-117">它會將毫無意義**屬性群組**沒有新增至少一個相關的節點，其中包括相關的節點之節點**欄位屬性**節點， **Any 屬性**節點，以及 （巢狀） **Attribute 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="a52cd-117">It would be pointless to add an **Attribute Group** node without adding at least one relevant node to it, where relevant nodes include **Field Attribute** nodes, **Any Attribute** nodes, and (nested) **Attribute Group** nodes.</span></span> <span data-ttu-id="a52cd-118">事實上，屬性群組僅包含單一屬性有些不妥當，除非您特別計劃在未來新增更多屬性。</span><span class="sxs-lookup"><span data-stu-id="a52cd-118">In fact, an attribute group that contains only a single attribute is somewhat ill-conceived, unless you are making a point of planning for the addition of more attributes in the future.</span></span>  

  <span data-ttu-id="a52cd-119">**屬性群組**節點可以巢狀，允許更多可能性可以如何建構和結合屬性群組。</span><span class="sxs-lookup"><span data-stu-id="a52cd-119">**Attribute Group** nodes can be nested, allowing more possibilities in how groups of attributes can be constructed and combined.</span></span> <span data-ttu-id="a52cd-120">**屬性群組**節點也可以包含**Any 屬性**節點，允許的屬性群組，以包含相關的屬性執行個體，它能容納的萬用字元功能。</span><span class="sxs-lookup"><span data-stu-id="a52cd-120">**Attribute Group** nodes can also contain the **Any Attribute** node, allowing an attribute group to contain wildcard character capabilities with respect to the attribute instances it can accommodate.</span></span>  

## <a name="xsd-representation"></a><span data-ttu-id="a52cd-121">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="a52cd-121">XSD representation</span></span>  
 <span data-ttu-id="a52cd-122">當**屬性群組**節點前加入至**記錄**節點或另一個**屬性群組**節點、 兩個不同區域的相對應的 XML 結構描述定義 (XSD)受影響的結構描述的語言表示法。</span><span class="sxs-lookup"><span data-stu-id="a52cd-122">When an **Attribute Group** node is first added to a **Record** node or to another **Attribute Group** node, two distinct areas of the corresponding XML Schema definition (XSD) language representation of the schema are affected.</span></span> <span data-ttu-id="a52cd-123">在下列範例中，新**屬性群組**節點，在粗體，已新增至現有**記錄**已包含現有的節點**欄位項目**節點。</span><span class="sxs-lookup"><span data-stu-id="a52cd-123">In the following example, a new **Attribute Group** node, in bold, has been added to an existing **Record** node that already contains an existing **Field Element** node.</span></span>  

```  
        ...  
        <xs:element name="ExistingRecord">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ExistingFieldElement" type="xs:string" />  
                </xs:sequence>  
                <xs:attributeGroup ref="attrGroup0" />  
            </xs:complexType>  
        </xs:element>  
        ...   
    <xs:attributeGroup name="attrGroup0" />  
</xs:schema>  
```  

 <span data-ttu-id="a52cd-124">請注意如何**attributeGroup**項目內之 XSD 表示法**記錄**節點參考全域**attributeGroup**加入做為子系的項目**結構描述**項目。</span><span class="sxs-lookup"><span data-stu-id="a52cd-124">Note how the **attributeGroup** element within the XSD representation of the **Record** node references a global **attributeGroup** element that is added as a child of the **schema** element.</span></span> <span data-ttu-id="a52cd-125">這個在結構描述的 XSD 表示法中之屬性群組的全域定義，允許在整個結構描述中的多個位置參考此屬性群組。</span><span class="sxs-lookup"><span data-stu-id="a52cd-125">This global definition of the attribute group within the XSD representation of the schema allows the attribute group to be referenced in multiple locations throughout the schema.</span></span>  

> [!NOTE]
>  <span data-ttu-id="a52cd-126">會自動提供的預設屬性群組名稱格式為 attrgroup*N*，其中*N*是單純遞增的數字。</span><span class="sxs-lookup"><span data-stu-id="a52cd-126">Default attribute group names that are supplied automatically have the form attrGroup*N*, where *N* is a monotonically increasing numeral.</span></span> <span data-ttu-id="a52cd-127">您可以藉由提供新的、 唯一的名稱，在重新命名屬性群組及其**Group Reference**屬性。</span><span class="sxs-lookup"><span data-stu-id="a52cd-127">You can rename an attribute group by providing a new, unique name in its **Group Reference** property.</span></span> <span data-ttu-id="a52cd-128">您不能在結構描述樹狀結構中就地重新命名屬性群組。</span><span class="sxs-lookup"><span data-stu-id="a52cd-128">An attribute group cannot be renamed in place within the schema tree.</span></span>  

## <a name="see-also"></a><span data-ttu-id="a52cd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a52cd-129">See Also</span></span>  
- [<span data-ttu-id="a52cd-130">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="a52cd-130">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
- [<span data-ttu-id="a52cd-131">節點屬性</span><span class="sxs-lookup"><span data-stu-id="a52cd-131">Node Properties</span></span>](../core/node-properties.md)   
- <span data-ttu-id="a52cd-132">**Sequence 群組節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="a52cd-132">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
- [<span data-ttu-id="a52cd-133">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="a52cd-133">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)   
- [<span data-ttu-id="a52cd-134">欄位屬性節點</span><span class="sxs-lookup"><span data-stu-id="a52cd-134">Field Attribute Nodes</span></span>](../core/field-attribute-nodes.md)   
- [<span data-ttu-id="a52cd-135">Any 屬性節點</span><span class="sxs-lookup"><span data-stu-id="a52cd-135">Any Attribute Nodes</span></span>](../core/any-attribute-nodes.md)
