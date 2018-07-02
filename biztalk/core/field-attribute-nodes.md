---
title: 欄位屬性節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e964c07-53e5-473f-84f2-05af4796cbbe
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef3cbf401ce5408c59ae164ca528c41a647eba2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972135"
---
# <a name="field-attribute-nodes"></a><span data-ttu-id="b38db-102">欄位屬性節點</span><span class="sxs-lookup"><span data-stu-id="b38db-102">Field Attribute Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="b38db-103">概觀</span><span class="sxs-lookup"><span data-stu-id="b38db-103">Overview</span></span>
<span data-ttu-id="b38db-104">在 「 BizTalk 編輯器 」 中，使用**Field 屬性**節點，以描述性質，例如字串和數字簡單的資訊項目。</span><span class="sxs-lookup"><span data-stu-id="b38db-104">In BizTalk Editor, you use **Field Attribute** nodes to describe items of information that are simple in nature, such as strings and numbers.</span></span> <span data-ttu-id="b38db-105">此外，當上述資訊顯示為實際訊息執行個體中屬性的值，而非顯示為 XML 項目的內容時，也可使用這類節點。</span><span class="sxs-lookup"><span data-stu-id="b38db-105">Further, they are used when the information in question appears as the value of an attribute in an actual instance of a message, as opposed to appearing as the content of an XML element.</span></span> <span data-ttu-id="b38db-106">如需詳細資訊會儲存為項目內容的詳細資訊，請參閱[欄位項目節點](../core/field-element-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="b38db-106">For additional information about information that is stored as element content, see [Field Element Nodes](../core/field-element-nodes.md).</span></span>  

 <span data-ttu-id="b38db-107">雖然最直接的用法**Field 屬性**節點會做為子節點的**記錄**節點，也可以用做為子節點的**屬性群組**節點。</span><span class="sxs-lookup"><span data-stu-id="b38db-107">Although the most straightforward use of **Field Attribute** nodes is as child nodes of **Record** nodes, they can also be used as child nodes of **Attribute Group** nodes.</span></span> <span data-ttu-id="b38db-108">在後者的情況下， **Field 屬性**節點的子系**屬性群組**節點，可做為屬性的任何**記錄**節點，其中包含該**屬性群組**節點。</span><span class="sxs-lookup"><span data-stu-id="b38db-108">In the latter case, the **Field Attribute** nodes that are children of an **Attribute Group** node are available as attributes of any **Record** node that includes that **Attribute Group** node.</span></span> <span data-ttu-id="b38db-109">如需詳細資訊**屬性群組**節點，請參閱[屬性群組節點](../core/attribute-group-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="b38db-109">For more information about **Attribute Group** nodes, see [Attribute Group Nodes](../core/attribute-group-nodes.md).</span></span>  

> [!NOTE]
>  <span data-ttu-id="b38db-110">在 「 BizTalk 編輯器 」 中，項目和屬性項目可以呈現**欄位**節點，但是它們有不同結構描述樹狀檢視中，在 XSD 視窗中，有不同的 XML 表示法中與其相關聯的圖示和在 Visual Studio 的 [屬性] 視窗中的不同屬性。</span><span class="sxs-lookup"><span data-stu-id="b38db-110">In BizTalk Editor, both the element and attribute elements can be represented by a **Field** node, though they have different icons associated with them in the schema tree view, a different XML representation in the XSD window, and different properties in the Visual Studio Properties window.</span></span>  

 <span data-ttu-id="b38db-111">對於 XML 訊息中任一項指定資訊 (此處的資訊是指單一不連續的簡單型別，例如字串或數字) 來說，有個永遠存在的相關問題，就是應將該資訊表示為項目的屬性，還是該項目的子項目。</span><span class="sxs-lookup"><span data-stu-id="b38db-111">For any given item of information in an XML message, where item of information means a single discrete simple type, such as a string or number, there is always a question regarding whether that information should be represented as the attribute of an element, or as a subelement of that element.</span></span> <span data-ttu-id="b38db-112">就一般規則而言，當可能的值為不連續值、數目很少，且可能更改項目本身的語意時，將資訊表示為屬性會較為適當。</span><span class="sxs-lookup"><span data-stu-id="b38db-112">As a general rule, representing an item of information as an attribute tends to be more appropriate when the possible values are discrete, few in number, and tend to modify the semantics of the element itself.</span></span> <span data-ttu-id="b38db-113">當可能的值可根據變數設定重複多次、可能有較大範圍的值、可能很長 (如長字串)，且是順序相關的數個同層級值中的一個時，則將資訊表示為子項目較為適當。</span><span class="sxs-lookup"><span data-stu-id="b38db-113">Representing an item of information as a subelement tends to be more appropriate when the possible values can repeat a variable number of times, are likely to have more widely ranging values, might be long, as in long strings, and are one of several sibling values where their order is relevant.</span></span> <span data-ttu-id="b38db-114">如果您要建立結構描述為現有類型的 XML 文件，您選擇使用**欄位項目**節點或**Field 屬性**，已建立的特定資訊項目 節點和您必須使用符合 XML 的節點。</span><span class="sxs-lookup"><span data-stu-id="b38db-114">If you are creating a schema for an existing type of XML document, your choice of using a **Field Element** node or a **Field Attribute** node for a particular item of information has already been made for you, and you must use the node that matches the XML.</span></span>  

> [!NOTE]
>  <span data-ttu-id="b38db-115">根節點不能有**欄位**屬性。</span><span class="sxs-lookup"><span data-stu-id="b38db-115">Root nodes may not have **Field** attributes.</span></span> <span data-ttu-id="b38db-116">**欄位**屬性附加至**根**節點不會儲存與結構描述。</span><span class="sxs-lookup"><span data-stu-id="b38db-116">**Field** attributes attached to the **Root** node are not saved with the schema.</span></span>  

## <a name="xsd-representation"></a><span data-ttu-id="b38db-117">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="b38db-117">XSD representation</span></span>  
 <span data-ttu-id="b38db-118">當**欄位屬性**節點插入**記錄**節點，它會在任何其他子節點結尾處插入**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="b38db-118">When a **Field Attribute** node is inserted into a **Record** node, it is inserted at the end of any other child nodes in the **Record** node.</span></span> <span data-ttu-id="b38db-119">這包括插**順序**，**選擇**，或**所有**元素，其中包含任何非屬性節點，和先前的任何屬性節點之後插入。</span><span class="sxs-lookup"><span data-stu-id="b38db-119">This includes being inserted after the **sequence**, **choice**, or **all** element containing any nonattribute nodes, and after any attribute nodes that were previously inserted.</span></span> <span data-ttu-id="b38db-120">下列範例示範新**欄位屬性**節點，以粗體顯示，它插在結尾**記錄**（利用命名以釐清其身分識別的節點） 的節點。</span><span class="sxs-lookup"><span data-stu-id="b38db-120">The following example shows a new **Field Attribute** node, in bold, inserted at the end of a **Record** node (with nodes named to clarify their identity).</span></span>  

```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="FieldElement" type="xs:string" />  
            <xs:element name="EmptyNestedRecord">  
                <xs:complexType />  
            </xs:element>  
        </xs:sequence>  
        <xs:attribute name="ExistingFieldAttribute" type="xs:string" />  

    </xs:complexType>  
</xs:element>  

```  

## <a name="see-also"></a><span data-ttu-id="b38db-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b38db-121">See Also</span></span>  
- [<span data-ttu-id="b38db-122">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="b38db-122">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
- [<span data-ttu-id="b38db-123">節點屬性</span><span class="sxs-lookup"><span data-stu-id="b38db-123">Node Properties</span></span>](../core/node-properties.md)   
- <span data-ttu-id="b38db-124">**欄位項目節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="b38db-124">**Field Element Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
- [<span data-ttu-id="b38db-125">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="b38db-125">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)   
- [<span data-ttu-id="b38db-126">Attribute 群組節點</span><span class="sxs-lookup"><span data-stu-id="b38db-126">Attribute Group Nodes</span></span>](../core/attribute-group-nodes.md)
