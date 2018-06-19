---
title: 使用限制機制的簡單型別衍生 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4ca712e-9563-4917-9bfc-1033a36773e8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dda4b8ad64f1edf262446f1633eda109ba7074ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271726"
---
# <a name="simple-type-derivation-using-the-restriction-mechanism"></a><span data-ttu-id="33021-102">使用限制機制的簡單型別衍生</span><span class="sxs-lookup"><span data-stu-id="33021-102">Simple Type Derivation Using the Restriction Mechanism</span></span>

## <a name="overview"></a><span data-ttu-id="33021-103">概觀</span><span class="sxs-lookup"><span data-stu-id="33021-103">Overview</span></span>
<span data-ttu-id="33021-104">當您使用限制機制從現有的簡單型別衍生新簡單型別時，通常會將在該屬性或項目值的執行個體訊息中所允許的值限制為基底簡單型別所允許的值之子集。</span><span class="sxs-lookup"><span data-stu-id="33021-104">When you derive a new simple type from an existing simple type by using the restriction mechanism, you are typically restricting the values allowed in an instance message for that attribute or element value to a subset of those values allowed by the base simple type.</span></span> <span data-ttu-id="33021-105">例如，您可以限制字串類型為數個列舉字串的其中一個。</span><span class="sxs-lookup"><span data-stu-id="33021-105">For example, you can restrict a string type to be one of several enumerated strings.</span></span>  
  
 <span data-ttu-id="33021-106">如需有關使用限制機制來衍生新簡單型別的完整資訊，請參閱 W3C 網站。</span><span class="sxs-lookup"><span data-stu-id="33021-106">For comprehensive information about deriving new simple types by using the restriction mechanism, refer to the W3C website.</span></span> <span data-ttu-id="33021-107">如需各種與其他網站連結，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。</span><span class="sxs-lookup"><span data-stu-id="33021-107">For various links to this and other websites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
## <a name="field-element-and-field-attribute"></a><span data-ttu-id="33021-108">欄位項目及欄位屬性</span><span class="sxs-lookup"><span data-stu-id="33021-108">Field Element and Field Attribute</span></span>
 <span data-ttu-id="33021-109">若要藉由限制衍生簡單類型，選取 相關**欄位項目**節點或**欄位屬性**節點在結構描述樹狀目錄中，然後在 屬性 視窗中，從下拉式清單選取簡單型別列出**基底資料型別**屬性。</span><span class="sxs-lookup"><span data-stu-id="33021-109">To derive a simple type by using restriction, select the relevant **Field Element** node or **Field Attribute** node in the schema tree and then, in the Properties window, select a simple type from the drop-down list for the **Base Data Type** property.</span></span> <span data-ttu-id="33021-110">您已選取值，這個屬性，如**Derived By**屬性會自動從其預設值變更為**限制**，做為型別衍生的預設值。</span><span class="sxs-lookup"><span data-stu-id="33021-110">As soon as you have selected a value for this property, the **Derived By** property automatically changes from its default value to **Restriction**, which serves as the default value for type derivation.</span></span> <span data-ttu-id="33021-111">此外，整個新類別的屬性，稱為**限制**，在 [屬性] 視窗中變成可用。</span><span class="sxs-lookup"><span data-stu-id="33021-111">Also, a whole new category of properties, called **Restriction**, becomes available in the Properties window.</span></span>  
  
 <span data-ttu-id="33021-112">依照您選取的不同基底資料型別，您可以在此新類別中設定不同的屬性。</span><span class="sxs-lookup"><span data-stu-id="33021-112">Depending on the base data type you select, different properties are available to be set in this new category.</span></span> <span data-ttu-id="33021-113">比方說，如果基底資料類型是數值，屬性**MaxFacet Type** (當**MaxFacet Value**設定)， **MaxFacet Value**， **MinFacet Type**(當**MinFacet Value**設定)，和**MinFacet Value**可用來定義允許的值內含或排除範圍。</span><span class="sxs-lookup"><span data-stu-id="33021-113">For example, if the base data type is numeric, the properties **MaxFacet Type** (when **MaxFacet Value** is set), **MaxFacet Value**, **MinFacet Type** (when **MinFacet Value** is set), and **MinFacet Value** are available for defining an inclusive or exclusive range of allowed values.</span></span> <span data-ttu-id="33021-114">如果基底資料類型是字串類型，**長度**，**最大長度**，和**最小長度**屬性可供條件約束字串的長度。</span><span class="sxs-lookup"><span data-stu-id="33021-114">If the base data type is a string type, the **Length**, **Maximum Length**, and **Minimum Length** properties are available for constraining the length of the string.</span></span>  
  
 <span data-ttu-id="33021-115">如需有關欄位節點的各種限制屬性的詳細資訊，請參閱**欄位項目節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="33021-115">For more information about the various restriction properties of field nodes, see the **Field Element Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="33021-116">當您第一次變更**欄位項目**節點或**欄位屬性**節點從具有資料類型具有基底資料型別 （因此開始簡單型別衍生的程序），將保留**衍生的**屬性設定為**限制**，而且提供列舉型別為根據的限制的允許的字串值，您可以觀察 XSD 檢視中的對應片段中的下列變更：</span><span class="sxs-lookup"><span data-stu-id="33021-116">When you first change a **Field Element** node or **Field Attribute** node from having a data type to having a base data type (thereby starting the process of simple type derivation), leave the **Derived By** property set to **Restriction**, and provide an enumeration-based restriction to the allowed string values, you can observe the following changes in the corresponding fragment in the XSD view:</span></span>  
  
-   <span data-ttu-id="33021-117">之前，是使用新插入**欄位項目**節點名為**WestCoastStates**。</span><span class="sxs-lookup"><span data-stu-id="33021-117">Before, with a newly inserted **Field Element** node named **WestCoastStates**.</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="WestCoastStates" type="xs:string" />  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
    ```  
  
-   <span data-ttu-id="33021-118">設定之後**基底資料型別**屬性設為"xs: string"，並保留衍生預設值是**限制**如**Derived By**屬性。</span><span class="sxs-lookup"><span data-stu-id="33021-118">After setting the **Base Data Type** property to "xs:string", and leaving the derivation default of **Restriction** for the **Derived By** property.</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="WestCoastStates" >  
                    <xs:simpleType>  
                        <xs:restriction base="xs:string" />  
                    </xs:simpleType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
    ```  
  
-   <span data-ttu-id="33021-119">設定之後**列舉**美國大陸西岸三種狀態的名稱將限制類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="33021-119">After setting the **Enumeration** property in the Restriction category to the names of the three states on the west coast of the continental United States.</span></span>  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="WestCoastStates">  
                    <xs:simpleType>  
                        <xs:restriction base="xs:string" />  
                            <xs:enumeration value="Washington" />  
                            <xs:enumeration value="Oregon" />  
                            <xs:enumeration value="California" />  
                        </xs:restriction>  
                    </xs:simpleType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="33021-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33021-120">See Also</span></span>  
 [<span data-ttu-id="33021-121">簡單型別衍生</span><span class="sxs-lookup"><span data-stu-id="33021-121">Simple Type Derivation</span></span>](../core/simple-type-derivation.md)