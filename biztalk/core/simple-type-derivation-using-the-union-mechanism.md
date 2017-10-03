---
title: "使用聯集機制的簡單型別衍生 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e51ae390-78f5-4fb9-9163-2a8023aea1ec
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1414fa506f824415de8e8449e8b2b27befd2fc76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="simple-type-derivation-using-the-union-mechanism"></a><span data-ttu-id="d9d3f-102">使用聯集機制的簡單型別衍生</span><span class="sxs-lookup"><span data-stu-id="d9d3f-102">Simple Type Derivation Using the Union Mechanism</span></span>
<span data-ttu-id="d9d3f-103">當您使用聯集機制從現有簡單型別衍生新的簡單型別時，是根據您指定的型別清單指定此屬性或項目的值可為一個以上的型別。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-103">When you derive a new simple type from an existing simple type by using the union mechanism, you are specifying that the value for this attribute or element can be of more than one type, according to a list of types that you specify.</span></span> <span data-ttu-id="d9d3f-104">例如，您可以指定屬性或項目值為 [日期]、[時間] 或 [日期/時間] 值。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-104">For example, you can specify that an attribute or element value is either a date, a time, or a date/time value.</span></span>  
  
 <span data-ttu-id="d9d3f-105">如需有關使用聯集機制來衍生新簡單型別的完整資訊，請參閱 W3C 網站。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-105">For comprehensive information about deriving new simple types by using the union mechanism, refer to the W3C website.</span></span> <span data-ttu-id="d9d3f-106">如需各種與其他網站連結，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-106">For various links to this and other websites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
 <span data-ttu-id="d9d3f-107">若要衍生簡單型別於數個可能的類型聯集，選取 相關**欄位項目**節點或**欄位屬性**節點在結構描述樹狀目錄中，然後在 屬性 視窗中選取簡單型別從下拉式清單，如**基底資料型別**屬性。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-107">To derive a simple type as a union of several possible types, select the relevant **Field Element** node or **Field Attribute** node in the schema tree and then, in the Properties window, select a simple type from the drop-down list for the **Base Data Type** property.</span></span> <span data-ttu-id="d9d3f-108">您已選取值，這個屬性，如**Derived By**屬性會自動從其預設值變更為**限制**，做為型別衍生的預設值。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-108">As soon as you have selected a value for this property, the **Derived By** property automatically changes from its default value to **Restriction**, which serves as the default value for type derivation.</span></span> <span data-ttu-id="d9d3f-109">您必須變更**Derived By**屬性從**限制**至**Union**，這會導致**基底資料型別**屬性來重新命名為**成員型別**屬性 （附帶一提，重新命名的屬性將移至由於屬性的字母順序排序的屬性清單中的不同位置）。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-109">You must change the **Derived By** property from **Restriction** to **Union**, which causes the **Base Data Type** property to be renamed as the **Member Types** property (incidentally, the renamed property moves to a different position in the property list due to the alphabetical sorting of the properties).</span></span>  
  
 <span data-ttu-id="d9d3f-110">最後，您可以使用中的核取方塊**成員型別**下拉式檢查清單來選取其他的型別，以供執行個體訊息中對應值。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-110">Finally, you can use the check boxes in the **Member Types** drop-down checklist to select additional types to allow for corresponding values in instance messages.</span></span>  
  
 <span data-ttu-id="d9d3f-111">當您第一次變更**欄位項目**節點或**欄位屬性**節點從具有資料類型具有基底資料型別 （因此開始簡單型別衍生的程序），然後設定  **Derived By**屬性**Union**，您可以觀察下列變更 XSD 檢視中的對應片段中。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-111">When you first change a **Field Element** node or **Field Attribute** node from having a data type to having a base data type (thereby starting the process of simple type derivation), and then set the **Derived By** property to **Union**, you can observe the following change in the corresponding fragment in the XSD view.</span></span>  
  
-   <span data-ttu-id="d9d3f-112">之前，是使用新插入**欄位項目**節點名為**DatesAndOrTimes**。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-112">Before, with a newly inserted **Field Element** node named **DatesAndOrTimes**.</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
-   <span data-ttu-id="d9d3f-113">設定之後**基底資料型別**屬性**xs: date**，和設定**Derived By**屬性**聯集**(其後**基底資料型別**屬性重新命名為**成員型別**屬性)，然後也選取**xs: datetime**和**xs: time**為其他允許的類型中的**成員型別**下拉式檢查清單。</span><span class="sxs-lookup"><span data-stu-id="d9d3f-113">After setting the **Base Data Type** property to **xs:date**, and setting the **Derived By** property to **Union** (after which the **Base Data Type** property is renamed to be the **Member Types** property), and then also selecting **xs:datetime** and **xs:time** as additional allowed types in the **Member Types** drop-down checklist.</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d9d3f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9d3f-114">See Also</span></span>  
 [<span data-ttu-id="d9d3f-115">簡單型別衍生</span><span class="sxs-lookup"><span data-stu-id="d9d3f-115">Simple Type Derivation</span></span>](../core/simple-type-derivation.md)