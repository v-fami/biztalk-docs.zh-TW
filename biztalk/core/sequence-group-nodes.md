---
title: Sequence 群組節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 139c3daa-a682-4bf7-bbb7-b5694ced0431
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c113d0cfd0f6055d55b0329bba3c1ec60bf835e8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019740"
---
# <a name="sequence-group-nodes"></a><span data-ttu-id="dadad-102">[Sequence 群組] 節點</span><span class="sxs-lookup"><span data-stu-id="dadad-102">Sequence Group Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="dadad-103">概觀</span><span class="sxs-lookup"><span data-stu-id="dadad-103">Overview</span></span>
<span data-ttu-id="dadad-104">在 「 BizTalk 編輯器 」 中，您可以插入**Sequence 群組**節點，以包含其他節點，必須出現在執行個體訊息中出現的順序相同**Sequence 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="dadad-104">In BizTalk Editor, you can insert a **Sequence Group** node to contain other nodes that must appear in an instance message in the same order in which they appear within the **Sequence Group** node.</span></span> <span data-ttu-id="dadad-105">包含的節點必須是對應到 XML 項目的節點，但不能是對應到 XML 屬性的節點。</span><span class="sxs-lookup"><span data-stu-id="dadad-105">The contained nodes must be nodes that correspond to XML elements, but cannot be nodes that correspond to XML attributes.</span></span>  

> [!NOTE]
>  <span data-ttu-id="dadad-106">在 BizTalk 編輯器**Sequence 群組**節點都由預設的字串表示\<順序\>結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="dadad-106">In BizTalk Editor, the **Sequence Group** node is represented by default with the string \<Sequence\> in the schema tree view.</span></span> <span data-ttu-id="dadad-107">如果您將參考設定為**Sequence 群組**節點，例如 x，則會表示為數\<Group: x\>結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="dadad-107">If you set a reference to a **Sequence Group** node, such as x, it is represented as \<Group:x\> in the schema tree view.</span></span>  

 <span data-ttu-id="dadad-108">您可能想要新增**Sequence 群組**宣告全域項目群組。</span><span class="sxs-lookup"><span data-stu-id="dadad-108">You may want to add a **Sequence Group** to declare a global element group.</span></span>  

 <span data-ttu-id="dadad-109">您需要按照下列程式碼來建立 XML 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="dadad-109">You may need to create a schema for XML as follows.</span></span>  

```  
<Root>  
    <Record1>  
        <GroupItem1/>  
        <GroupItem2/>  
        <NotAGroupItem>  
    </Record1>  
    <Record2>  
        <GroupItem1/>  
        <GroupItem2/>  
    </Record2>  
</Root>  

```  

 <span data-ttu-id="dadad-110">因為兩種情形中都有 GroupItem1 與 GroupItem2，所以您可以宣告一個同時為 Record1 及 Record2 之子項的全域序列群組。</span><span class="sxs-lookup"><span data-stu-id="dadad-110">Because GroupItem1 and GroupItem2 exist in both cases, you may declare a global sequence group that is a child of both Record1 and Record2.</span></span> <span data-ttu-id="dadad-111">如需如何宣告全域序列群組的逐步指示，請參閱[另一個節點或類型中建立參考](../core/how-to-create-references-to-another-node-or-type.md)。</span><span class="sxs-lookup"><span data-stu-id="dadad-111">For step-by-step instructions about how to declare a global sequence group, see [Creating References to Another Node or Type](../core/how-to-create-references-to-another-node-or-type.md).</span></span>  

 <span data-ttu-id="dadad-112">使用者可以變更隱藏的群組**Choice 群組** 節點或**All 群組**節點 (因此就不一定要是**Sequence 群組**節點) 藉由變更**群組順序類型**屬性。</span><span class="sxs-lookup"><span data-stu-id="dadad-112">A user can change the hidden group to be a **Choice Group** node or an **All Group** node (so it is not necessarily a **Sequence Group** node) by changing the **Group Order Type** property.</span></span> <span data-ttu-id="dadad-113">這個屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="dadad-113">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="xsd-representation"></a><span data-ttu-id="dadad-114">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="dadad-114">XSD representation</span></span>  
 <span data-ttu-id="dadad-115">當**Sequence 群組**節點插入**記錄**節點，插入內的任何其他子節點結尾處**順序**，**選擇**，或**所有**中的項目**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="dadad-115">When a **Sequence Group** node is inserted into a **Record** node, it is inserted at the end of any other child nodes within the **sequence**, **choice**, or **all** element in the **Record** node.</span></span> <span data-ttu-id="dadad-116">下列範例示範新**Sequence 群組**節點，以粗體的結尾插入**順序**中的項目**記錄**節點 (以具名節點釐清其身分識別）。</span><span class="sxs-lookup"><span data-stu-id="dadad-116">The following example shows a new **Sequence Group** node, in bold type, inserted at the end of the **sequence** element in a **Record** node (with nodes named to clarify their identity).</span></span>  

```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  

```  

## <a name="see-also"></a><span data-ttu-id="dadad-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dadad-117">See Also</span></span>  
- [<span data-ttu-id="dadad-118">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="dadad-118">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
- [<span data-ttu-id="dadad-119">節點屬性</span><span class="sxs-lookup"><span data-stu-id="dadad-119">Node Properties</span></span>](../core/node-properties.md)   
- <span data-ttu-id="dadad-120">**Sequence 群組節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="dadad-120">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
- [<span data-ttu-id="dadad-121">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="dadad-121">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)
