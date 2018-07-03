---
title: Any 項目節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7e30fcf-31bc-4d48-9bc7-0be90e927127
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 905d6c25c5c2021840f4257c29df015d4bcb374e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002431"
---
# <a name="any-element-nodes"></a><span data-ttu-id="135c7-102">Any 項目節點</span><span class="sxs-lookup"><span data-stu-id="135c7-102">Any Element Nodes</span></span>
<span data-ttu-id="135c7-103">在 「 BizTalk 編輯器 」 中，您可以使用**Any 項目**節點來指示的位置執行個體訊息中未知的項目可能出現的位置。</span><span class="sxs-lookup"><span data-stu-id="135c7-103">In BizTalk Editor, you can use an **Any Element** node to indicate a location within an instance message where unknown elements may appear.</span></span> <span data-ttu-id="135c7-104">這適用於您知道某個項目可能出現在執行個體訊息中的特定位置，但是您不知道項目的名稱，或是它的複雜程度。</span><span class="sxs-lookup"><span data-stu-id="135c7-104">This accommodates situations in which you know that some element might appear at a particular location within an instance message, but you do not know the name of the element, or how complicated it might be.</span></span> <span data-ttu-id="135c7-105">如果您將放**Any 項目**BizTalk 結構描述中的適當位置的節點可以處理訊息的這類未知的部分。</span><span class="sxs-lookup"><span data-stu-id="135c7-105">If you place an **Any Element** node at the appropriate location within the schema, BizTalk can process such unknown portions of a message.</span></span> <span data-ttu-id="135c7-106">唯一的要求是對應的 XML 必須格式正確。</span><span class="sxs-lookup"><span data-stu-id="135c7-106">The only requirement is that the corresponding XML is well-formed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="135c7-107">在 BizTalk 編輯器**Any 項目**節點以字串表示\<任何\>結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="135c7-107">In BizTalk Editor, the **Any Element** node is represented with the string \<Any\> in the schema tree view.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="135c7-108">您可以控制要訊息未知的部分驗證為語式正確的 XML 所使用的程度**Process Contents**屬性。</span><span class="sxs-lookup"><span data-stu-id="135c7-108">You can control the degree to which the unknown portion of the message is validated as well-formed XML by using the **Process Contents** property.</span></span> <span data-ttu-id="135c7-109">在許多情況下，您可能需要設定**Process Contents**屬性設**略過**的位置執行個體訊息的內容**Any 項目**来處理的節點。</span><span class="sxs-lookup"><span data-stu-id="135c7-109">In many cases you may need to set the **Process Contents** property to **Skip** for the contents of an instance message at the location of the **Any Element** node to be processed.</span></span> <span data-ttu-id="135c7-110">保留預設值**Strict** for **Process Contents**屬性會防止執行個體訊息無法通過驗證。</span><span class="sxs-lookup"><span data-stu-id="135c7-110">Retaining the default value of **Strict** for the **Process Contents** property will prevent instance message validation from passing.</span></span>  
> 
> <span data-ttu-id="135c7-111">這個屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="135c7-111">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="xsd-representation"></a><span data-ttu-id="135c7-112">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="135c7-112">XSD representation</span></span>  
 <span data-ttu-id="135c7-113">當**Any 項目**節點新增至**記錄**節點，或另一個節點，它可以加入這類**Sequence 群組**， **Choice 群組**，或**所有群組**單一 XML 標記 節點，會新增到對應 XML 結構描述定義的結構描述 (XSD) 語言表示法。</span><span class="sxs-lookup"><span data-stu-id="135c7-113">When an **Any Element** node is added to a **Record** node, or to another node to which it can be added such as a **Sequence Group**, **Choice Group**, or **All Group** node, a single XML tag is added to the corresponding XML Schema definition (XSD) language representation of the schema.</span></span> <span data-ttu-id="135c7-114">在下列範例中，新**Any 項目**節點，其 XSD 表示法以粗體顯示，已加入至現有**記錄**節點，其中已包含**欄位項目**節點。</span><span class="sxs-lookup"><span data-stu-id="135c7-114">In the following example, a new **Any Element** node, whose XSD representation is shown in bold type, has been added to an existing **Record** node that already contains a **Field Element** node.</span></span>  
  
```  
<xs:element name="ExistingRecord">  
    <xs:complexType>  
        <xs:sequence>  
             <xs:element name="ExistingFieldElement" type="xs:string" />  
            <xs:any />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="135c7-115">假設**Process Contents**屬性**Any 項目**節點設定為**略過**，於執行個體訊息會受到此結構描述片段，而**ExistingRecord**項目應該包含 **[existingfieldelement]** 元素，其中包含字串資料，後面接著任意複雜度的任何單一項目。</span><span class="sxs-lookup"><span data-stu-id="135c7-115">Assuming that the **Process Contents** property of the **Any Element** node is set to **Skip**, within an instance message governed by this schema fragment, an **ExistingRecord** element is expected to contain an **ExistingFieldElement** element containing string data, followed by any single element of arbitrary complexity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="135c7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="135c7-116">See Also</span></span>  
 <span data-ttu-id="135c7-117">[BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="135c7-117">[BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md) </span></span>  
 <span data-ttu-id="135c7-118">[節點屬性](../core/node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="135c7-118">[Node Properties](../core/node-properties.md) </span></span>  
 <span data-ttu-id="135c7-119">[如何設定節點屬性](../core/how-to-set-node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="135c7-119">[How to Set Node Properties](../core/how-to-set-node-properties.md) </span></span>  
 [<span data-ttu-id="135c7-120">Any 屬性節點</span><span class="sxs-lookup"><span data-stu-id="135c7-120">Any Attribute Nodes</span></span>](../core/any-attribute-nodes.md)