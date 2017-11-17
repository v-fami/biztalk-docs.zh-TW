---
title: "所有群組節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e28d98c-746a-44d8-bed2-ba539b8432aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f51d6420b7d754ffb8706e2bc729a02df00b4338
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="all-group-nodes"></a><span data-ttu-id="4cfb9-102">[All 群組] 節點</span><span class="sxs-lookup"><span data-stu-id="4cfb9-102">All Group Nodes</span></span>
<span data-ttu-id="4cfb9-103">在 [BizTalk 編輯器] 中，您可以插入**All 群組**節點，以包含其他節點將會出現零次或一次，以任何順序。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-103">In BizTalk Editor, you can insert an **All Group** node to contain other nodes that will appear zero or one time, in any order.</span></span> <span data-ttu-id="4cfb9-104">在 XML 結構描述定義 (XSD) 語言中， **All 群組**具有多個使用方式的限制比**順序**和**選擇**群組內的少數情況，轉譯BizTalk 編輯器 中，您可以在此處建立**All 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-104">In XML Schema definition (XSD) language, the **All group** has more usage limitations than **Sequence** and **Choice** groups, which translates to few situations within BizTalk Editor where you will be able to create an **All Group** node.</span></span>  
  
 <span data-ttu-id="4cfb9-105">若要使用**All 群組**節點在 [BizTalk 編輯器] 中，您必須遵循一些額外的步驟： 建立最簡單的方式**All 群組**節點變更的值是**群組順序類型**屬性的父代**記錄**節點**所有**。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-105">To use an **All Group** node in BizTalk Editor, you need to follow some extra steps: The easiest way to create an **All Group** node is to change the value of the **Group Order Type** property of the parent **Record** node to **All**.</span></span> <span data-ttu-id="4cfb9-106">如此可確保所有的附屬節點**記錄**內所包含的節點**All 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-106">This ensures that all of the subordinate nodes of the **Record** node are contained within the **All Group** node.</span></span>  <span data-ttu-id="4cfb9-107">請參閱**群組順序類型** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-107">See **Group Order Type** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="4cfb9-108">若要使用的另一種方式**All 群組**節點在 [BizTalk 編輯器] 中的開頭插入新**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-108">Another way to use an **All Group** node in BizTalk Editor begins with inserting a new **Record** node.</span></span> <span data-ttu-id="4cfb9-109">插入新後**記錄**節點，變更其**內容類型**屬性**ComplexContent**。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-109">After inserting the new **Record** node, change its **Content Type** property to **ComplexContent**.</span></span> <span data-ttu-id="4cfb9-110">接著您可以插入**All 群組**節點的子系**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-110">Then you can insert an **All Group** node as a child of the **Record** node.</span></span> <span data-ttu-id="4cfb9-111">這是必要的因為**All 群組**僅涉及繼承時能插入。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-111">This is required because the **All Group** can only be inserted when inheritance is involved.</span></span> <span data-ttu-id="4cfb9-112">藉由指定包含**記錄**節點包含複雜內容，其資料類型會變成基礎資料型別**xs: anytype**、 延伸模組衍生。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-112">By specifying that the containing **Record** node contains complex content, its data type becomes based on the data type **xs:anyType**, derived by extension.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cfb9-113">在 [BizTalk 編輯器] 中， **All 群組**節點以字串表示\<所有 > 結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-113">In BizTalk Editor, the **All Group** node is represented with the string \<All> in the schema tree view.</span></span> <span data-ttu-id="4cfb9-114">如果您將參考設定至**All 群組** 節點，例如為 x，則會呈現為\<Group: x > 結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-114">If you set a reference to an **All Group** node, such as to x, it is represented as \<Group:x> in the schema tree view.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="4cfb9-115">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="4cfb9-115">XSD representation</span></span>  
 <span data-ttu-id="4cfb9-116">**All 群組**節點可以插入到**記錄**節點，但它的非屬性子節點的**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-116">An **All Group** node can be inserted into a **Record** node, but only if it is the only non-attribute child node of that **Record** node.</span></span> <span data-ttu-id="4cfb9-117">下列範例所示，在步驟中，如何為新**All 群組**節點 XML 結構描述定義 (XSD) 語言表示**所有**（利用命名節點執行幾個步驟在 [BizTalk 編輯器] 中的項目若要釐清其身分識別。）</span><span class="sxs-lookup"><span data-stu-id="4cfb9-117">The following example shows, in steps, how a new **All Group** node is represented in the XML Schema definition (XSD) language as an **all** element as the steps in BizTalk Editor are performed (with nodes named to clarify their identity).</span></span>  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType />   
</xs:element>  
```  
  
 <span data-ttu-id="4cfb9-118">前述 XSD 片段中所示，新增新的記錄後其**內容類型**屬性變更為**ComplexContent**，並產生以下的 XSD 修改。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-118">After adding a new record as shown in the preceding XSD fragment, its **Content Type** property is changed to **ComplexContent**, resulting in the following XSD modifications.</span></span>  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
             <xs:extension base="xs:anyType" />  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="4cfb9-119">現在**All 群組**節點可插入為新的記錄的子系，下列 XSD 片段中所示。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-119">Now the **All Group** node can be inserted as a child of the new record, as shown in the following XSD fragment.</span></span>  
  
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
  
 <span data-ttu-id="4cfb9-120">最後，您可以插入適當的節點，做為新的子系**All 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-120">Finally, you can insert appropriate nodes as children of the new **All Group** node.</span></span> <span data-ttu-id="4cfb9-121">下列範例所示**記錄**節點和**欄位項目**做為新的子節點插入節點**All 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="4cfb9-121">The following example shows a **Record** node and a **Field Element** node inserted as child nodes of the new **All Group** node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4cfb9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cfb9-122">See Also</span></span>  
-  [<span data-ttu-id="4cfb9-123">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="4cfb9-123">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="4cfb9-124">節點屬性</span><span class="sxs-lookup"><span data-stu-id="4cfb9-124">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="4cfb9-125">**Sequence 群組節點屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="4cfb9-125">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span> 
-  [<span data-ttu-id="4cfb9-126">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="4cfb9-126">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)