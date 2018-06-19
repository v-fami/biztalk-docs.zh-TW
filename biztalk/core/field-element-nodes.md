---
title: 欄位項目節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65b5e1f6-283f-4172-9bc2-f04a0ea6753d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74c3732ee315ad307f49760e367449216c3e01da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245982"
---
# <a name="field-element-nodes"></a><span data-ttu-id="e2bce-102">欄位項目節點</span><span class="sxs-lookup"><span data-stu-id="e2bce-102">Field Element Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="e2bce-103">概觀</span><span class="sxs-lookup"><span data-stu-id="e2bce-103">Overview</span></span>
<span data-ttu-id="e2bce-104">在 「 BizTalk 編輯器 」 中，使用**欄位項目**節點，以描述的資訊是簡單的本質，例如字串和數字的項目。</span><span class="sxs-lookup"><span data-stu-id="e2bce-104">In BizTalk Editor, you use **Field Element** nodes to describe items of information that are simple in nature, such as strings and numbers.</span></span> <span data-ttu-id="e2bce-105">此外，當使用中的資訊顯示為實際訊息執行個體中的 XML 項目內容，而非顯示為與 XML 項目相關聯的屬性值時，也會使用它們。</span><span class="sxs-lookup"><span data-stu-id="e2bce-105">Further, they are used when the information in question appears as the content of an XML element in an actual instance of a message, as opposed to appearing as the value of an attribute associated with an XML element.</span></span> <span data-ttu-id="e2bce-106">其他資訊儲存成屬性值的詳細資訊，請參閱[欄位屬性節點](../core/field-attribute-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="e2bce-106">For additional information about information that is stored as attribute values, see [Field Attribute Nodes](../core/field-attribute-nodes.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2bce-107">在 [BizTalk 編輯器] 中，項目和屬性項目可由**欄位**節點，但是它們具有不同結構描述樹狀檢視中，在 XSD 視窗中，有不同的 XML 表示法中與它們相關聯的圖示和在 Visual Studio 屬性視窗不同的屬性。</span><span class="sxs-lookup"><span data-stu-id="e2bce-107">In BizTalk Editor, both the element and attribute elements can be represented by a **Field** node, although they have different icons associated with them in the schema tree view, a different XML representation in the XSD window, and different properties in the Visual Studio Properties window.</span></span>  
  
 <span data-ttu-id="e2bce-108">對於 XML 訊息中任一項指定資訊 (此處的資訊是指單一不連續的簡單型別，例如字串或數字) 來說，有個永遠存在的相關問題，就是應將該資訊表示為項目的屬性，還是該項目的子項目。</span><span class="sxs-lookup"><span data-stu-id="e2bce-108">For any given item of information in an XML message, where item of information means a single discrete simple type, such as a string or number, there is always a question regarding whether that information should be represented as the attribute of an element, or as a subelement of that element.</span></span> <span data-ttu-id="e2bce-109">就一般規則而言，當可能的值為不連續值、數目很少，且可能更改項目本身的語意時，將資訊表示為屬性會較為適當。</span><span class="sxs-lookup"><span data-stu-id="e2bce-109">As a general rule, representing an item of information as an attribute tends to be more appropriate when the possible values are discrete, few in number, and tend to modify the semantics of the element itself.</span></span> <span data-ttu-id="e2bce-110">當可能的值可根據變數設定重複多次、可能有較大範圍的值、可能很長 (如長字串)，且是順序相關的數個同層級值中的一個時，則將資訊表示為子項目較為適當。</span><span class="sxs-lookup"><span data-stu-id="e2bce-110">Representing an item of information as a subelement tends to be more appropriate when the possible values can repeat a variable number of times, are likely to have more widely ranging values, might be long, as in long strings, and are one of several sibling values where their order is relevant.</span></span> <span data-ttu-id="e2bce-111">若您剛建立的現有類型的 XML 結構描述文件，您選擇使用**欄位項目**節點或**欄位屬性**已發出的特定資訊項目 節點，而且，您必須使用符合 XML 的節點。</span><span class="sxs-lookup"><span data-stu-id="e2bce-111">If you are just creating a schema for an existing type of XML document, your choice of using a **Field Element** node or a **Field Attribute** node for a particular item of information has already been made for you, and you must use the node that matches the XML.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="e2bce-112">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="e2bce-112">XSD representation</span></span>  
 <span data-ttu-id="e2bce-113">當**欄位項目**節點插入**記錄** 節點，它的任何其他子節點結尾插入**順序**中的項目**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="e2bce-113">When a **Field Element** node is inserted into a **Record** node, it is inserted at the end of any other child nodes within the **sequence** element in the **Record** node.</span></span> <span data-ttu-id="e2bce-114">下列範例示範新**欄位項目**節點，以粗體顯示、 結尾處插入**順序**中的項目**記錄**（利用命名以釐清其識別節點的節點).</span><span class="sxs-lookup"><span data-stu-id="e2bce-114">The following example shows a new **Field Element** node, in bold, inserted at the end of the **sequence** element in a **Record** node (with nodes named to clarify their identity).</span></span>  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
            <xs:element name="EmptyNestedRecord">  
                <xs:complexType />  
            </xs:element>  
  
        </xs:sequence>  
        <xs:attribute name="ExistingFieldAttribute" type="xs:string" />  
    </xs:complexType>  
</xs:element>  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2bce-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2bce-115">See Also</span></span>  
-  [<span data-ttu-id="e2bce-116">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="e2bce-116">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="e2bce-117">節點屬性</span><span class="sxs-lookup"><span data-stu-id="e2bce-117">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="e2bce-118">**欄位項目節點屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="e2bce-118">**Field Element Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
-  [<span data-ttu-id="e2bce-119">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="e2bce-119">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)