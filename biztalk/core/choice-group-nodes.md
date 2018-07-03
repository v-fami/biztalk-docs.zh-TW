---
title: Choice 群組節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 466b525d-4d8c-4b8e-830d-eee27845c0dc
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 226a0197f1f66313de994269039107b47ed03b9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002055"
---
# <a name="choice-group-nodes"></a><span data-ttu-id="6da7f-102">Choice 群組節點</span><span class="sxs-lookup"><span data-stu-id="6da7f-102">Choice Group Nodes</span></span>
<span data-ttu-id="6da7f-103">在 「 BizTalk 編輯器 」 中，您可以插入**Choice 群組**節點，以包含其他節點 （或整個子樹狀結構節點），其中只有一個可以出現在執行個體訊息中。</span><span class="sxs-lookup"><span data-stu-id="6da7f-103">In BizTalk Editor, you can insert a **Choice Group** node to contain other nodes (or entire subtrees of nodes), only one of which can appear in an instance message.</span></span> <span data-ttu-id="6da7f-104">指定的執行個體訊息若有效，將只有其中一個選擇存在。</span><span class="sxs-lookup"><span data-stu-id="6da7f-104">A given instance message, if valid, will have only one of the choices present.</span></span> <span data-ttu-id="6da7f-105">包含的節點必須是對應到 XML 項目的節點，但不能是對應到 XML 屬性的節點。</span><span class="sxs-lookup"><span data-stu-id="6da7f-105">The contained nodes must be nodes that correspond to XML elements, but cannot be nodes that correspond to XML attributes.</span></span>  

> [!NOTE]
>  <span data-ttu-id="6da7f-106">在 BizTalk 編輯器**Choice 群組**節點以字串表示\<選擇\>結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="6da7f-106">In BizTalk Editor, the **Choice Group** node is represented with the string \<Choice\> in the schema tree view.</span></span> <span data-ttu-id="6da7f-107">如果您將參考設定為**Choice 群組**節點，例如 x，則會表示為數\<Group: x\>結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="6da7f-107">If you set a reference to a **Choice Group** node, such as x, it is represented as \<Group:x\> in the schema tree view.</span></span>  

## <a name="xsd-representation"></a><span data-ttu-id="6da7f-108">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="6da7f-108">XSD representation</span></span>  
 <span data-ttu-id="6da7f-109">當**Choice 群組**節點插入**記錄**節點，插入內的任何其他子節點結尾處**順序**，**選擇**，或**所有**中的項目**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="6da7f-109">When a **Choice Group** node is inserted into a **Record** node, it is inserted at the end of any other child nodes within the **sequence**, **choice**, or **all** element in the **Record** node.</span></span> <span data-ttu-id="6da7f-110">下列範例所示，以粗體方式的新**Choice 群組**節點會以 XML 結構描述定義 (XSD) 語言，為表示**選擇**結尾處插入的項目**順序**中的項目**記錄**（利用命名以釐清其身分識別的節點） 的節點。</span><span class="sxs-lookup"><span data-stu-id="6da7f-110">The following example shows, in bold type, how a new **Choice Group** node is represented in the XML Schema definition (XSD) language as a **choice** element inserted at the end of the **sequence** element in a **Record** node (with nodes named to clarify their identity).</span></span>  

```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  

```  

 <span data-ttu-id="6da7f-111">根據預設， **choice**項目提供**minOccurs**屬性值為零 (0)，表示需要進行任何選擇。</span><span class="sxs-lookup"><span data-stu-id="6da7f-111">By default, the **choice** element is given a **minOccurs** attribute value of zero (0), indicating that none of the choices need occur.</span></span> <span data-ttu-id="6da7f-112">您可以變更此值，在 Visual Studio 的 [屬性] 視窗時**Choice 群組**結構描述樹狀結構檢視中選取節點。</span><span class="sxs-lookup"><span data-stu-id="6da7f-112">You can change this value in the Visual Studio Properties window when the **Choice Group** node is selected in the schema tree view.</span></span>  

 <span data-ttu-id="6da7f-113">下列範例顯示相同**choice**元素的 xsd**項目**項目對應到兩個附屬**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="6da7f-113">The following example shows the same **choice** element with the XSD **element** elements corresponding to two subordinate **Record** nodes.</span></span>  

```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
            <xs:choice minOccurs="1" maxOccurs="1">  
                <xs:element name="usAddress">  
                    <xs:complexType>  
                        <xs:sequence>  
                        </xs:sequence>  
                    </xs:complexType>  
                </xs:element>  
                <xs:element name="foreignAddress">  
                    <xs:complexType>  
                        <xs:sequence>  
                        </xs:sequence>  
                    </xs:complexType>  
                </xs:element>  
            </xs:choice>  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
```  

 <span data-ttu-id="6da7f-114">在此範例中，兩個同層級**記錄**節點可用來說明，執行個體訊息必須記錄包含美國地址資訊，或是包含全球地址資訊的事實。</span><span class="sxs-lookup"><span data-stu-id="6da7f-114">In this example, two sibling **Record** nodes are used to describe the fact that an instance message will either have a record with United States address information in it, or a record with worldwide address information in it.</span></span> <span data-ttu-id="6da7f-115">此外， **minOccurs**並**maxOccurs**的屬性**Choice 群組**節點都已設定為一 (1) 在 Visual Studio 的 [屬性] 視窗中，導致*minOccurs*並*maxOccurs*屬性**選擇**設為一 (1) 之 XSD 表示中的項目。</span><span class="sxs-lookup"><span data-stu-id="6da7f-115">Further, the **minOccurs** and **maxOccurs** properties of the **Choice Group** node have both been set to one (1) in the Visual Studio Properties window, resulting in the *minOccurs* and *maxOccurs* attributes of the **choice** element being set to one (1) in the XSD representation.</span></span>  

## <a name="see-also"></a><span data-ttu-id="6da7f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6da7f-116">See Also</span></span>  
- [<span data-ttu-id="6da7f-117">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="6da7f-117">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
- [<span data-ttu-id="6da7f-118">節點屬性</span><span class="sxs-lookup"><span data-stu-id="6da7f-118">Node Properties</span></span>](../core/node-properties.md)   
- <span data-ttu-id="6da7f-119">**Sequence 群組節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="6da7f-119">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>     
- [<span data-ttu-id="6da7f-120">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="6da7f-120">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)
