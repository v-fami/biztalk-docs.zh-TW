---
title: "使用清單機制衍生簡單型別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14f3c7b7-7585-4297-9177-2deaef8355f0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aafc6a540e9595f426858bc16fedfb1f8fe0bc8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="simple-type-derivation-using-the-list-mechanism"></a><span data-ttu-id="9a3d2-102">使用清單機制的簡單型別衍生</span><span class="sxs-lookup"><span data-stu-id="9a3d2-102">Simple Type Derivation Using the List Mechanism</span></span>
<span data-ttu-id="9a3d2-103">當您使用清單機制從現有的簡單型別衍生新的簡單型別時，即是指定此屬性或項目的值做為指定型別之以空格分隔的值清單。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-103">When you derive a new simple type from an existing simple type by using the list mechanism, you are specifying that the value for this attribute or element can be a space-separated list of values of the specified type.</span></span> <span data-ttu-id="9a3d2-104">例如，您可以指定屬性或項目值為以空格分隔的整數清單。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-104">For example, you can specify that an attribute or element value is a space-separated list of integers.</span></span>  
  
 <span data-ttu-id="9a3d2-105">如需使用清單機制衍生新簡單型別的完整資訊，請參閱 W3C 網站。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-105">For comprehensive information about deriving new simple types by using the list mechanism, refer to the W3C Web site.</span></span> <span data-ttu-id="9a3d2-106">這個資料庫和其他網站的各種連結，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-106">For various links to this and other Web sites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
 <span data-ttu-id="9a3d2-107">若要衍生簡單型別做為該類型的清單，選取 相關**欄位項目**節點或**欄位屬性**節點在結構描述樹狀目錄中，然後在 屬性 視窗中，從下拉式清單選取簡單型別列出**基底資料型別**屬性。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-107">To derive a simple type as a list of that type, select the relevant **Field Element** node or **Field Attribute** node in the schema tree and then, in the Properties window, select a simple type from the drop-down list for the **Base Data Type** property.</span></span> <span data-ttu-id="9a3d2-108">您選取的值，這個屬性，如**Derived By**屬性會自動從其預設值變更為**限制**，做為型別衍生的預設值。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-108">As soon as you select a value for this property, the **Derived By** property automatically changes from its default value to **Restriction**, which serves as the default value for type derivation.</span></span> <span data-ttu-id="9a3d2-109">您必須變更**Derived By**屬性從**限制**至**清單**，這會導致**基底資料型別**做為要重新命名屬性**項目類型**屬性 （附帶一提，重新命名的屬性將移至由於屬性的字母順序排序的屬性清單中的不同位置）。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-109">You must change the **Derived By** property from **Restriction** to **List**, which causes the **Base Data Type** property to be renamed as the **Item Type** property (incidentally, the renamed property moves to a different position in the property list due to the alphabetical sorting of the properties).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a3d2-110">您可以一起使用限制及清單機制、使用限制機制來建立具名的簡單型別衍生，接著透過清單機制，使用該衍生項目做為另一個簡單型別衍生中的項目類型。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-110">You can use the restriction and list mechanisms together, creating a named simple type derivation by using the restriction mechanism, and then using that as the item type in another simple type derivation by using the list mechanism.</span></span> <span data-ttu-id="9a3d2-111">舉例來說，這種方式所產生的值會受限為以空格分隔的字串清單，而其會隸屬於特定列舉字串集。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-111">This can result, for example, in a value that is constrained to be a list of space-separated strings belonging to a particular enumerated set of strings.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="9a3d2-112">使用清單機制來衍生簡單型別，在所選擇的項目類型本身可加入空格 (如字串) 時，就會變得相當複雜。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-112">Using the list mechanism for simple type derivation can be complicated when the item type you choose is one that itself allows spaces, such as strings.</span></span> <span data-ttu-id="9a3d2-113">這是因為清單機制是利用空格來分隔清單中允許類型的值。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-113">This is because the list mechanism uses spaces to separate values of the allowed type in the list.</span></span>  
  
 <span data-ttu-id="9a3d2-114">當您第一次變更**欄位項目**節點或**欄位屬性**節點從具有資料類型具有基底資料型別 （因此開始簡單型別衍生的程序），然後設定  **Derived By**屬性**清單**，您可以觀察 XSD 檢視中的對應片段中的下列變更：</span><span class="sxs-lookup"><span data-stu-id="9a3d2-114">When you first change a **Field Element** node or **Field Attribute** node from having a data type to having a base data type (thereby starting the process of simple type derivation), and then set the **Derived By** property to **List**, you can observe the following change in the corresponding fragment in the XSD view:</span></span>  
  
-   <span data-ttu-id="9a3d2-115">之前，是使用新插入**欄位項目**節點名為**ZipCodeList**。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-115">Before, with a newly inserted **Field Element** node named **ZipCodeList**.</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="ZipCodeList" type="xs:string" />  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
-   <span data-ttu-id="9a3d2-116">設定之後**基底資料型別**屬性設為 xs: integer，並設定**Derived By**屬性**清單**(其後**基底資料型別**屬性重新命名為**項目類型**屬性)。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-116">After setting the **Base Data Type** property to xs:integer, and setting the **Derived By** property to **List** (after which the **Base Data Type** property is renamed to be the **Item Type** property).</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="ZipCodeList">  
                    <xs:simpleType>  
               <xs:list itemType="xs:integer" />   
                       </xs:simpleType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="9a3d2-117">在實際的結構描述中，最好是先定義及命名簡單型別衍生的整數，會將整數限制為五位數，然後再衍生**ZipCodeList**自該型別，有效地限制的清單項目具有五位數的整數。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-117">In a real-life schema, it would be better to first define and name a simple type derivation of integer that restricts the integer to five digits, and then to derive the **ZipCodeList** element from that type, effectively limiting the list to integers having five digits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a3d2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a3d2-118">See Also</span></span>  
 [<span data-ttu-id="9a3d2-119">簡單型別衍生</span><span class="sxs-lookup"><span data-stu-id="9a3d2-119">Simple Type Derivation</span></span>](../core/simple-type-derivation.md)