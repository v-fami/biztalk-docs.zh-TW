---
title: 記錄節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43af077d-5db8-43ca-8bd0-e3a9e3ebe2b0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ec23dcf604e1bd454ba7e69a57c250cf3b1872f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982343"
---
# <a name="record-nodes"></a><span data-ttu-id="cbdb6-102">記錄節點</span><span class="sxs-lookup"><span data-stu-id="cbdb6-102">Record Nodes</span></span>
<span data-ttu-id="cbdb6-103">在 「 BizTalk 編輯器 」 中，使用**記錄**節點，代表資訊的集合，其中的個別項目可以是：</span><span class="sxs-lookup"><span data-stu-id="cbdb6-103">In BizTalk Editor, you use a **Record** node to represent a collection of information, the individual items of which can be:</span></span>  

- <span data-ttu-id="cbdb6-104">簡單資訊類型，像是字串和數字，以子欄位節點表示。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-104">Simple types of information, such as strings and numbers, represented as child field nodes.</span></span> <span data-ttu-id="cbdb6-105">這些子欄位節點可以是**欄位項目**節點或**Field 屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-105">These child field nodes can be either **Field Element** nodes or **Field Attribute** nodes.</span></span> <span data-ttu-id="cbdb6-106">如需這兩種類型的欄位節點的詳細資訊，請參閱[欄位項目節點](../core/field-element-nodes.md)並[欄位屬性節點](../core/field-attribute-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-106">For additional information about these two types of field nodes, see [Field Element Nodes](../core/field-element-nodes.md) and [Field Attribute Nodes](../core/field-attribute-nodes.md).</span></span>  

- <span data-ttu-id="cbdb6-107">複雜類型的資訊，表示為子系**記錄**節點或群組節點 (**Sequence 群組**節點， **Choice 群組** 節點，或**All 群組**節點)。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-107">Complex types of information, represented as child **Record** nodes or as a group node (**Sequence Group** node, **Choice Group** node, or **All Group** node).</span></span>  

- <span data-ttu-id="cbdb6-108">任何未經審視的資訊類型，表示為子系**Any 項目**或是**Any 屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-108">Any unexamined type of information, represented as child **Any Element** or **Any Attribute** nodes.</span></span>  

- <span data-ttu-id="cbdb6-109">所表示的屬性群組的**屬性群組**節點。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-109">Groups of attributes represented by an **Attribute Group** node.</span></span>  

  <span data-ttu-id="cbdb6-110">當您插入新的子節點插入**記錄**節點、 子節點永遠會插入在目前的子節點結尾處。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-110">When you insert a new child node into a **Record** node, the child node is always inserted at the end of the current child nodes.</span></span> <span data-ttu-id="cbdb6-111">中的 XML 結構描述定義 (XSD) 語言表示法中，其對應的區域，這表示非屬性項目會加入至結尾中的項目結尾加入新項目**順序**， **選擇**，**所有**，或**群組**項目和屬性項目加入任何其他的屬性項目，全部都發生之後結束**順序**，**選擇**，**所有**，或**群組**項目。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-111">Within the XML Schema definition (XSD) language representation, new elements are added to the end of their corresponding areas, meaning that nonattribute elements are added to the end of the elements within the **sequence**, **choice**, **all**, or **group** element, and attribute elements are added to the end of any other attribute elements, all of which occur after the **sequence**, **choice**, **all**, or **group** element.</span></span>  

## <a name="xsd-representation"></a><span data-ttu-id="cbdb6-112">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="cbdb6-112">XSD representation</span></span>  
 <span data-ttu-id="cbdb6-113">當第一次插入新的 XSD 表示法**記錄**節點包含只有三行，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-113">When first inserted, the XSD representation of a new **Record** node consists of only three lines, as shown in the following example.</span></span>  

```  
<xs:element name="Record">  
      <xs:complexType />  
</xs:element>  
```  

 <span data-ttu-id="cbdb6-114">當其中三個屬性節點以外的任何子節點 (**Field 屬性**，**屬性群組**，和**Any 屬性**) 會新增至**記錄**節點，根據預設，它會放置在**順序**內的項目**complexType**項目。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-114">When any child node other than one of the three attribute nodes (**Field Attribute**, **Attribute Group**, and **Any Attribute**) is added to a **Record** node, by default it is placed within a **sequence** element within the **complexType** element.</span></span> <span data-ttu-id="cbdb6-115">**順序**時加入，並移除所有非屬性子節點也會刪除第一個非屬性子節點，就會加入項目。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-115">The **sequence** element is added when the first nonattribute child node is added, and removed if all the nonattribute child nodes are deleted.</span></span> <span data-ttu-id="cbdb6-116">所有的三種類型的屬性節點內新增**complexType**項目，外部，但之後**順序**項目。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-116">All three types of attribute nodes are added within the **complexType** element, but outside and after any **sequence** element.</span></span>  

 <span data-ttu-id="cbdb6-117">**順序**內的非屬性子節點會加入的項目也可以**選擇**或是**所有**項目，如果您變更**群組順序類型 （節點所有的結構描述的屬性）** 屬性的結構描述樹狀結構中對應的節點**選擇**或是**所有**分別。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-117">The **sequence** element within which nonattribute child nodes are added can also be a **choice** or **all** element if you change the **Group Order Type (Node Property of All Schemas)** property of the corresponding node in the schema tree to **Choice** or **All**, respectively.</span></span>  

 <span data-ttu-id="cbdb6-118">在下列範例中，**記錄**節點已重新命名的 shipTo。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-118">In the following example, the **Record** node has been renamed shipTo.</span></span> <span data-ttu-id="cbdb6-119">內的位置**記錄**其中加入屬性和非屬性節點的節點會顯示在括號中。</span><span class="sxs-lookup"><span data-stu-id="cbdb6-119">The locations within the **Record** node where attribute and nonattribute nodes are added are shown in brackets.</span></span>  

```  
<xs:element name="">  
    <xs:complexType>  
        <xs:sequence>  
            [Nonattribute child nodes of the record go here.]  
            [Always add new nonattribute child nodes to the end.]  
        </xs:sequence>  
            [Attribute child nodes of the record go here.]  
            [Always add new attribute child nodes to the end.]  
    </xs:complexType>  
</xs:element>  

```  

## <a name="see-also"></a><span data-ttu-id="cbdb6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbdb6-120">See Also</span></span>  
- [<span data-ttu-id="cbdb6-121">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="cbdb6-121">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
- [<span data-ttu-id="cbdb6-122">節點屬性</span><span class="sxs-lookup"><span data-stu-id="cbdb6-122">Node Properties</span></span>](../core/node-properties.md)   
- <span data-ttu-id="cbdb6-123">**記錄節點屬性**和**群組順序類型 （所有結構描述的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="cbdb6-123">**Record Node Properties** and **Group Order Type (Node Property of All Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
- [<span data-ttu-id="cbdb6-124">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="cbdb6-124">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)
