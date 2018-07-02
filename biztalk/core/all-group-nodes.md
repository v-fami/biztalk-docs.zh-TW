---
title: 所有群組的節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e28d98c-746a-44d8-bed2-ba539b8432aa
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 084b12f16e72507a7d5568bdee022925eca52c0e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989231"
---
# <a name="all-group-nodes"></a><span data-ttu-id="2a2ef-102">[All 群組] 節點</span><span class="sxs-lookup"><span data-stu-id="2a2ef-102">All Group Nodes</span></span>
<span data-ttu-id="2a2ef-103">在 「 BizTalk 編輯器 」 中，您可以插入**All 群組**節點，以包含其他節點將出現零或一次，依任何順序。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-103">In BizTalk Editor, you can insert an **All Group** node to contain other nodes that will appear zero or one time, in any order.</span></span> <span data-ttu-id="2a2ef-104">在 XML 結構描述定義 (XSD) 語言中，**所有群組**有更多的使用量限制，比**順序**並**選擇**群組，進而轉譯成內的少數情況，BizTalk 編輯器 中，您可以在此處建立**All 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-104">In XML Schema definition (XSD) language, the **All group** has more usage limitations than **Sequence** and **Choice** groups, which translates to few situations within BizTalk Editor where you will be able to create an **All Group** node.</span></span>  

 <span data-ttu-id="2a2ef-105">若要使用**All 群組**節點在 「 BizTalk 編輯器 」 中，您必須遵循一些額外的步驟： 建立最簡單的方式**All 群組**的值變更為節點**群組順序類型**屬性的父代**記錄**節點，以**所有**。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-105">To use an **All Group** node in BizTalk Editor, you need to follow some extra steps: The easiest way to create an **All Group** node is to change the value of the **Group Order Type** property of the parent **Record** node to **All**.</span></span> <span data-ttu-id="2a2ef-106">這可確保所有的附屬節點**記錄**內所包含的節點**All 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-106">This ensures that all of the subordinate nodes of the **Record** node are contained within the **All Group** node.</span></span>  <span data-ttu-id="2a2ef-107">請參閱**群組順序類型** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-107">See **Group Order Type** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

 <span data-ttu-id="2a2ef-108">若要使用的另一種方式**All 群組**在 [BizTalk 編輯器] 中節點的開頭插入新**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-108">Another way to use an **All Group** node in BizTalk Editor begins with inserting a new **Record** node.</span></span> <span data-ttu-id="2a2ef-109">插入新後**記錄**節點，變更其**內容類型**屬性設**ComplexContent**。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-109">After inserting the new **Record** node, change its **Content Type** property to **ComplexContent**.</span></span> <span data-ttu-id="2a2ef-110">接著您可以插入**All 群組**節點的子系**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-110">Then you can insert an **All Group** node as a child of the **Record** node.</span></span> <span data-ttu-id="2a2ef-111">這是必要的因為**All 群組**只有涉及繼承時要插入。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-111">This is required because the **All Group** can only be inserted when inheritance is involved.</span></span> <span data-ttu-id="2a2ef-112">指定包含**記錄** 節點包含複雜內容，其資料類型會變成基礎資料類型**xs: anytype**、 由副檔名衍生。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-112">By specifying that the containing **Record** node contains complex content, its data type becomes based on the data type **xs:anyType**, derived by extension.</span></span>  

> [!NOTE]
>  <span data-ttu-id="2a2ef-113">在 BizTalk 編輯器**All 群組**節點以字串表示\<所有 > 結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-113">In BizTalk Editor, the **All Group** node is represented with the string \<All> in the schema tree view.</span></span> <span data-ttu-id="2a2ef-114">如果您將參考設定為**All 群組**節點，例如為 x，則表示為\<Group: x > 結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-114">If you set a reference to an **All Group** node, such as to x, it is represented as \<Group:x> in the schema tree view.</span></span>  

## <a name="xsd-representation"></a><span data-ttu-id="2a2ef-115">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="2a2ef-115">XSD representation</span></span>  
 <span data-ttu-id="2a2ef-116">**All 群組** 節點可插入**記錄**節點，但只有如果它是只有非屬性子節點**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-116">An **All Group** node can be inserted into a **Record** node, but only if it is the only non-attribute child node of that **Record** node.</span></span> <span data-ttu-id="2a2ef-117">下列範例所示，在步驟中，新的方式**All 群組**節點會以 XML 結構描述定義 (XSD) 語言，為表示**所有**項目做為在 「 BizTalk 編輯器 」 中的步驟會執行 （利用命名節點若要釐清其身分識別。）</span><span class="sxs-lookup"><span data-stu-id="2a2ef-117">The following example shows, in steps, how a new **All Group** node is represented in the XML Schema definition (XSD) language as an **all** element as the steps in BizTalk Editor are performed (with nodes named to clarify their identity).</span></span>  

```  
<xs:element name="NewRecord">  
    <xs:complexType />   
</xs:element>  
```  

 <span data-ttu-id="2a2ef-118">在之後加入新記錄，如所示，在前述 XSD 片段中，其**內容的型別**屬性變更為**ComplexContent**，產生的以下的 XSD 修改。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-118">After adding a new record as shown in the preceding XSD fragment, its **Content Type** property is changed to **ComplexContent**, resulting in the following XSD modifications.</span></span>  

```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
             <xs:extension base="xs:anyType" />  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  

 <span data-ttu-id="2a2ef-119">現在**All 群組**節點可以插入新的記錄，之子節點，下列 XSD 片段中所示。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-119">Now the **All Group** node can be inserted as a child of the new record, as shown in the following XSD fragment.</span></span>  

```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
            <xs:extension base="xs:anyType">  
                <xs:all />   
             </xs:extension>  
          </xs:complexContent>  
     </xs:complexType>  
</xs:element>  
```  

 <span data-ttu-id="2a2ef-120">最後，您可以插入適當的節點，做為新的子系**All 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-120">Finally, you can insert appropriate nodes as children of the new **All Group** node.</span></span> <span data-ttu-id="2a2ef-121">下列範例所示**記錄**節點並**欄位項目**做為新的子節點插入節點**All 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="2a2ef-121">The following example shows a **Record** node and a **Field Element** node inserted as child nodes of the new **All Group** node.</span></span>  

```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
            <xs:extension base="xs:anyType">  
                <xs:all>  
                    <xs:element name="RecordChildOfAllGroup">  
                        <xs:complexType />  
                    </xs:element>  
                    <xs:element name="FieldElementChildOfAllGroup" type="xs:string" />  
                </xs:all>  
            </xs:extension>  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  

## <a name="see-also"></a><span data-ttu-id="2a2ef-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a2ef-122">See Also</span></span>  
- [<span data-ttu-id="2a2ef-123">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="2a2ef-123">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
- [<span data-ttu-id="2a2ef-124">節點屬性</span><span class="sxs-lookup"><span data-stu-id="2a2ef-124">Node Properties</span></span>](../core/node-properties.md)   
- <span data-ttu-id="2a2ef-125">**Sequence 群組節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="2a2ef-125">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span> 
- [<span data-ttu-id="2a2ef-126">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="2a2ef-126">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)
