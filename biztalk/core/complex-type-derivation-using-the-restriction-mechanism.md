---
title: 使用限制機制的複雜型別衍生 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3003d88-6b75-4dcb-834f-1babcf7449cb
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddbd9d8266d9c289b9b4bae9dd7060906e01ebd7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233478"
---
# <a name="complex-type-derivation-using-the-restriction-mechanism"></a><span data-ttu-id="62998-102">使用限制機制的複雜型別衍生</span><span class="sxs-lookup"><span data-stu-id="62998-102">Complex Type Derivation Using the Restriction Mechanism</span></span>
<span data-ttu-id="62998-103">就「BizTalk 編輯器」功能而言，透過限制產生的衍生和透過延伸產生的衍生類似。</span><span class="sxs-lookup"><span data-stu-id="62998-103">Derivation by restriction is similar to derivation by extension, in terms of BizTalk Editor functionality.</span></span> <span data-ttu-id="62998-104">透過限制所衍生的複雜型別與其基底資料型別類似，但其宣告較基底資料型別中對應的宣告受限制。</span><span class="sxs-lookup"><span data-stu-id="62998-104">A complex type derived by restriction is similar to its base data type, except that its declarations are more limited than the corresponding declarations in the base data type.</span></span> <span data-ttu-id="62998-105">事實上，新型別所代表的值，是基底資料型別所代表的值之子集 (與簡單型別的限制相同)。</span><span class="sxs-lookup"><span data-stu-id="62998-105">In fact, the values represented by the new type are a subset of the values represented by the base data type (as is the case with restriction of simple types).</span></span> <span data-ttu-id="62998-106">為基底資料型別值準備的應用程式，應該要能夠順利處理限制型別的任何值。</span><span class="sxs-lookup"><span data-stu-id="62998-106">An application prepared for the values of the base data type ought to be able to successfully process any of the values of the restricted type.</span></span>  
  
 <span data-ttu-id="62998-107">如需有關使用限制機制衍生新複雜型別的完整資訊，請參考 W3C 網站。</span><span class="sxs-lookup"><span data-stu-id="62998-107">For comprehensive information about deriving new complex types by using the restriction mechanism, refer to the W3C website.</span></span> <span data-ttu-id="62998-108">如需各種與其他網站連結，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。</span><span class="sxs-lookup"><span data-stu-id="62998-108">For various links to this and other websites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
 <span data-ttu-id="62998-109">若要衍生自複雜全域型別，由限制，在結構描述樹狀結構中的另一個位置開始插入新**記錄**節點所需的位置。</span><span class="sxs-lookup"><span data-stu-id="62998-109">To derive from a complex global type by restriction, in another location in the schema tree, begin by inserting a new **Record** node at the desired location.</span></span> <span data-ttu-id="62998-110">然後設定其**基底資料型別**複雜全域型別名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="62998-110">Then set its **Base Data Type** property to the name of a complex global type.</span></span> <span data-ttu-id="62998-111">最後，變更的設定**Derived By**屬性的預設值從**延伸**（至少基底資料類型設定時） 至**限制**。</span><span class="sxs-lookup"><span data-stu-id="62998-111">Finally, change the setting of the **Derived By** property from its default value of **Extension** (at least when a base data type is set) to **Restriction**.</span></span>  
  
 <span data-ttu-id="62998-112">在下列範例中， **BillingAddress**是新插入的名稱**記錄** 節點，和**GlobalAddrType**是從它的複雜全域型別名稱衍生，並想要限制。</span><span class="sxs-lookup"><span data-stu-id="62998-112">In the following example, **BillingAddress** is the name of the newly inserted **Record** node, and **GlobalAddrType** is the name of the complex global type from which it derives, and intends to restrict.</span></span> <span data-ttu-id="62998-113">在結構描述樹狀結構檢視中，重複的節點結構會顯示名為**BillingAddress**、 名為的節點下的相鄰節點結構相同**ShippingAddress**。</span><span class="sxs-lookup"><span data-stu-id="62998-113">In the schema tree view, a duplicate node structure would be displayed below the node named **BillingAddress**, identical to the adjacent node structure under the node named **ShippingAddress**.</span></span> <span data-ttu-id="62998-114">它們之間的差異在於**BillingAddress**節點結構，可能限制基底資料型別都會受到**GlobalAddrType**，而**ShippingAddress**結構則維持相同的基底資料型別**GlobalAddrType**。</span><span class="sxs-lookup"><span data-stu-id="62998-114">The difference between them is that the **BillingAddress** node structure will be subject to possible restrictions to the base data type **GlobalAddrType**, and the **ShippingAddress** structure will remain identical to the base data type **GlobalAddrType**.</span></span>  
  
 <span data-ttu-id="62998-115">因為您已選擇限制基底資料型別，因此不允許插入任何新節點，但可變更現有節點的屬性，以進一步限制它們可能的值或行為。</span><span class="sxs-lookup"><span data-stu-id="62998-115">Because you have chosen to restrict the base data type, you are not allowed to insert any new nodes, but you can change the properties of the existing nodes to further restrict their possible values or behavior.</span></span>  
  
-   <span data-ttu-id="62998-116">之前，與**Derived By**屬性仍設為**延伸**。</span><span class="sxs-lookup"><span data-stu-id="62998-116">Before, with the **Derived By** property still set to **Extension**.</span></span>  
  
    ```  
    <xs:schema>  
        <xs:element name="Root">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ShippingAddress" type="GlobalAddrType" />  
                    <xs:element name="BillingAddress">  
                        <xs:complexType>  
                            <xs:complexContent mixed="false">  
                                <xs:extension base="GlobalAddrType" />  
                            </xs:complexContent>  
                        </xs:complexType>  
                    </xs:element>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
        <xs:complexType name="GlobalAddrType">  
        [Address structure defined globally here.]  
        </xs:complexType>  
    </xs:schema>  
    ```  
  
-   <span data-ttu-id="62998-117">切換之後**Derived By**屬性從**延伸**至**限制**。</span><span class="sxs-lookup"><span data-stu-id="62998-117">After switching the **Derived By** property from **Extension** to **Restriction**.</span></span>  
  
    ```  
    <xs:schema>  
        <xs:element name="Root">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ShippingAddress" type="GlobalAddrType" />  
                    <xs:element name="BillingAddress">  
                        <xs:complexType>  
                            <xs:complexContent mixed="false">  
                                <xs:restriction base="GlobalAddrType">  
                   [Duplicate of address structure now appears  
                   here, ready to be restricted with additional  
                   attributes, set using the properties of the  
                   relevant nodes in the schema tree.]  
                                </xs:restriction>  
                            </xs:complexContent>  
                        </xs:complexType>  
                    </xs:element>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
        <xs:complexType name="GlobalAddrType">  
        [Address structure defined globally here.]  
        </xs:complexType>  
    </xs:schema>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="62998-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62998-118">See Also</span></span>  
 [<span data-ttu-id="62998-119">複雜全域型別衍生</span><span class="sxs-lookup"><span data-stu-id="62998-119">Complex Global Type Derivation</span></span>](../core/complex-global-type-derivation.md)