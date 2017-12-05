---
title: "任何屬性節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa2d25bc-3a8f-4fd9-acad-341b8e80c737
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82490a114149e3d4f71e3598900be5599c8a36e2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="any-attribute-nodes"></a><span data-ttu-id="1cde4-102">Any 屬性節點</span><span class="sxs-lookup"><span data-stu-id="1cde4-102">Any Attribute Nodes</span></span>
<span data-ttu-id="1cde4-103">在 [BizTalk 編輯器] 中，您可以使用**Any 屬性**節點來指示可能會出現與零或多個未知的屬性執行個體訊息中的 （已知） 項目。</span><span class="sxs-lookup"><span data-stu-id="1cde4-103">In BizTalk Editor, you can use an **Any Attribute** node to indicate a (known) element within an instance message for which zero or more unknown attributes may appear.</span></span> <span data-ttu-id="1cde4-104">這適用於您知道特定項目將會出現在執行個體訊息中的特定位置之情況，但是您不確定項目確實包括哪些屬性。</span><span class="sxs-lookup"><span data-stu-id="1cde4-104">This accommodates situations in which you know that a particular element will be present at a particular location within an instance message, but you are not sure exactly what attributes that element might include.</span></span> <span data-ttu-id="1cde4-105">如果您將放入**Any 屬性**節點內**記錄**相關項目相關聯的節點，BizTalk 可以處理該項目，與所關聯的屬性唯一的需求語法正確 (attributeName ="attributeValue")。</span><span class="sxs-lookup"><span data-stu-id="1cde4-105">If you place an **Any Attribute** node within the **Record** node associated with the relevant element, BizTalk can process that element, with the only requirement being that any associated attributes are syntactically correct (attributeName="attributeValue").</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cde4-106">在 [BizTalk 編輯器] 中， **Any 屬性**節點以字串表示\<AnyAttribute\>結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="1cde4-106">In BizTalk Editor, the **Any Attribute** node is represented with the string \<AnyAttribute\> in the schema tree view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cde4-107">您可以控制的訊息未知的部分驗證為格式正確的 XML 使用**Process Contents**屬性。</span><span class="sxs-lookup"><span data-stu-id="1cde4-107">You can control the degree to which the unknown portion of the message is validated as well-formed XML by using the **Process Contents** property.</span></span> <span data-ttu-id="1cde4-108">在許多情況下，您可能需要設定**Process Contents**屬性**略過**位置的執行個體訊息的內容**Any 屬性**来處理的節點.</span><span class="sxs-lookup"><span data-stu-id="1cde4-108">In many cases you may need to set the **Process Contents** property to **Skip** for the contents of an instance message at the location of the **Any Attribute** node to be processed.</span></span> <span data-ttu-id="1cde4-109">保留預設值的**Strict**如**Process Contents**屬性會防止執行個體訊息無法通過驗證。</span><span class="sxs-lookup"><span data-stu-id="1cde4-109">Retaining the default value of **Strict** for the **Process Contents** property will prevent instance message validation from passing.</span></span>  
>
> <span data-ttu-id="1cde4-110">這個屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="1cde4-110">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="xsd-representation"></a><span data-ttu-id="1cde4-111">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="1cde4-111">XSD representation</span></span>  
 <span data-ttu-id="1cde4-112">當**Any 屬性**節點加入至**記錄**節點或**屬性群組**單一 XML 標記 節點，會新增到對應的 XML 結構描述定義 (XSD) 語言結構描述表示法。</span><span class="sxs-lookup"><span data-stu-id="1cde4-112">When an **Any Attribute** node is added to a **Record** node or to an **Attribute Group** node, a single XML tag is added to the corresponding XML Schema definition (XSD) language representation of the schema.</span></span> <span data-ttu-id="1cde4-113">在下列範例中，新**Any 屬性**節點，顯示其 XSD 表示法中粗體、 已新增至現有**記錄**節點已包含**欄位項目**節點。</span><span class="sxs-lookup"><span data-stu-id="1cde4-113">In the following example, a new **Any Attribute** node, whose XSD representation is shown in bold, has been added to an existing **Record** node that already contains a **Field Element** node.</span></span>  
  
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
  
 <span data-ttu-id="1cde4-114">在上述範例中，新的 XSD 表示法**Any 屬性**節點加入**anyAttribute**包含結尾的項目 (**記錄**節點) **元素**項目、 外部**順序**項目，會在**complexType**項目。</span><span class="sxs-lookup"><span data-stu-id="1cde4-114">In the preceding example, the XSD representation of the new **Any Attribute** node adds an **anyAttribute** element to the end of the containing (**Record** node) **element** element, outside the **sequence** element and within the **complexType** element.</span></span> <span data-ttu-id="1cde4-115">這是 where 所有**屬性**以外使用的項目，**屬性群組**節點中，新增至它們包含**元素**項目。</span><span class="sxs-lookup"><span data-stu-id="1cde4-115">This is where all **attribute** elements, other than those with an **Attribute Group** node, are added to their containing **element** elements.</span></span>  
  
 <span data-ttu-id="1cde4-116">現在，並假設**Process Contents**屬性**Any 屬性**節點設定為**略過**內的執行個體訊息是由這個結構描述片段中， **ExistingRecord**預期項目，而且它可以包含任何屬性，只要它們是格式正確 XML 語法。</span><span class="sxs-lookup"><span data-stu-id="1cde4-116">Now, and assuming that the **Process Contents** property of the **Any Attribute** node is set to **Skip**, within an instance message governed by this schema fragment, an **ExistingRecord** element is expected, and it can contain any attributes so long as they are well-formed with respect to XML syntax.</span></span> <span data-ttu-id="1cde4-117">(若要遵循 XSD 片段，在此範例中，它也必須包含**[existingfieldelement]**以及項目。)</span><span class="sxs-lookup"><span data-stu-id="1cde4-117">(To conform to the XSD fragment in this example, it must also contain the **ExistingFieldElement** element as well.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cde4-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="1cde4-118">See Also</span></span>  
 <span data-ttu-id="1cde4-119">[BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="1cde4-119">[BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md) </span></span>  
 <span data-ttu-id="1cde4-120">[節點屬性](../core/node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1cde4-120">[Node Properties](../core/node-properties.md) </span></span>  
 <span data-ttu-id="1cde4-121">[如何設定節點屬性](../core/how-to-set-node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1cde4-121">[How to Set Node Properties](../core/how-to-set-node-properties.md) </span></span>  
 [<span data-ttu-id="1cde4-122">Any 項目節點</span><span class="sxs-lookup"><span data-stu-id="1cde4-122">Any Element Nodes</span></span>](../core/any-element-nodes.md)