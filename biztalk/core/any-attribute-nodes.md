---
title: 任何屬性節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa2d25bc-3a8f-4fd9-acad-341b8e80c737
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98cbd0ea288e14b68bc16f5e9a88f636bc229b9d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014479"
---
# <a name="any-attribute-nodes"></a><span data-ttu-id="9e9e0-102">Any 屬性節點</span><span class="sxs-lookup"><span data-stu-id="9e9e0-102">Any Attribute Nodes</span></span>
<span data-ttu-id="9e9e0-103">在 「 BizTalk 編輯器 」 中，您可以使用**Any 屬性**表示 （已知） 的項目，可能會出現與零個或多個未知的屬性執行個體訊息中的節點。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-103">In BizTalk Editor, you can use an **Any Attribute** node to indicate a (known) element within an instance message for which zero or more unknown attributes may appear.</span></span> <span data-ttu-id="9e9e0-104">這適用於您知道特定項目將會出現在執行個體訊息中的特定位置之情況，但是您不確定項目確實包括哪些屬性。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-104">This accommodates situations in which you know that a particular element will be present at a particular location within an instance message, but you are not sure exactly what attributes that element might include.</span></span> <span data-ttu-id="9e9e0-105">如果您將放**Any 屬性**內的節點**記錄**與相關的項目相關聯的節點，BizTalk 可以處理該項目，與在任何相關聯的屬性唯一的需求語法正確 (attributeName ="attributeValue")。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-105">If you place an **Any Attribute** node within the **Record** node associated with the relevant element, BizTalk can process that element, with the only requirement being that any associated attributes are syntactically correct (attributeName="attributeValue").</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e9e0-106">在 BizTalk 編輯器**Any 屬性**節點以字串表示\<AnyAttribute\>結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-106">In BizTalk Editor, the **Any Attribute** node is represented with the string \<AnyAttribute\> in the schema tree view.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="9e9e0-107">您可以控制要訊息未知的部分驗證為語式正確的 XML 所使用的程度**Process Contents**屬性。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-107">You can control the degree to which the unknown portion of the message is validated as well-formed XML by using the **Process Contents** property.</span></span> <span data-ttu-id="9e9e0-108">在許多情況下，您可能需要設定**Process Contents**屬性設**略過**的位置執行個體訊息的內容**Any 屬性**来處理的節點.</span><span class="sxs-lookup"><span data-stu-id="9e9e0-108">In many cases you may need to set the **Process Contents** property to **Skip** for the contents of an instance message at the location of the **Any Attribute** node to be processed.</span></span> <span data-ttu-id="9e9e0-109">保留預設值**Strict** for **Process Contents**屬性會防止執行個體訊息無法通過驗證。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-109">Retaining the default value of **Strict** for the **Process Contents** property will prevent instance message validation from passing.</span></span>  
> 
> <span data-ttu-id="9e9e0-110">這個屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-110">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="xsd-representation"></a><span data-ttu-id="9e9e0-111">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="9e9e0-111">XSD representation</span></span>  
 <span data-ttu-id="9e9e0-112">當**Any 屬性**節點新增至**記錄**節點，或者**屬性群組**單一 XML 標記 節點，會新增到對應的 XML 結構描述定義 (XSD) 語言結構描述表示法。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-112">When an **Any Attribute** node is added to a **Record** node or to an **Attribute Group** node, a single XML tag is added to the corresponding XML Schema definition (XSD) language representation of the schema.</span></span> <span data-ttu-id="9e9e0-113">在下列範例中，新**Any 屬性**節點，其 XSD 表示法會顯示在粗體，已新增至現有**記錄**節點，其中已包含**欄位項目**節點。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-113">In the following example, a new **Any Attribute** node, whose XSD representation is shown in bold, has been added to an existing **Record** node that already contains a **Field Element** node.</span></span>  
  
```  
<xs:element name="ExistingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
        <xs:anyAttribute />  
    </xs:complexType>  
</xs:element  
```  
  
 <span data-ttu-id="9e9e0-114">在上述範例中，新的 XSD 表示法**Any 屬性**節點會加入**anyAttribute**包含結尾的項目 (**記錄**節點) **項目**項目、 外部**序列**項目，會在**complexType**項目。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-114">In the preceding example, the XSD representation of the new **Any Attribute** node adds an **anyAttribute** element to the end of the containing (**Record** node) **element** element, outside the **sequence** element and within the **complexType** element.</span></span> <span data-ttu-id="9e9e0-115">這正是所有**屬性**項目，與以外**屬性群組**節點，新增至它們包含**項目**項目。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-115">This is where all **attribute** elements, other than those with an **Attribute Group** node, are added to their containing **element** elements.</span></span>  
  
 <span data-ttu-id="9e9e0-116">到目前為止，並假設**Process Contents**屬性**Any 屬性**節點設定為**略過**，於執行個體訊息會受到此結構描述片段，而**ExistingRecord**預期項目，而且它可以包含任何屬性，因此只要它們是格式正確 XML 語法。</span><span class="sxs-lookup"><span data-stu-id="9e9e0-116">Now, and assuming that the **Process Contents** property of the **Any Attribute** node is set to **Skip**, within an instance message governed by this schema fragment, an **ExistingRecord** element is expected, and it can contain any attributes so long as they are well-formed with respect to XML syntax.</span></span> <span data-ttu-id="9e9e0-117">(若要遵循 XSD 片段，在此範例中，它也必須包含 **[existingfieldelement]** 項目。)</span><span class="sxs-lookup"><span data-stu-id="9e9e0-117">(To conform to the XSD fragment in this example, it must also contain the **ExistingFieldElement** element as well.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e9e0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e9e0-118">See Also</span></span>  
 <span data-ttu-id="9e9e0-119">[BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="9e9e0-119">[BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md) </span></span>  
 <span data-ttu-id="9e9e0-120">[節點屬性](../core/node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="9e9e0-120">[Node Properties](../core/node-properties.md) </span></span>  
 <span data-ttu-id="9e9e0-121">[如何設定節點屬性](../core/how-to-set-node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="9e9e0-121">[How to Set Node Properties](../core/how-to-set-node-properties.md) </span></span>  
 [<span data-ttu-id="9e9e0-122">Any 項目節點</span><span class="sxs-lookup"><span data-stu-id="9e9e0-122">Any Element Nodes</span></span>](../core/any-element-nodes.md)