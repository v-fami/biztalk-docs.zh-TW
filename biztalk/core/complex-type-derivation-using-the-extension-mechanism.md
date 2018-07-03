---
title: 使用延伸模組機制的複雜型別衍生 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7125fb5b-f77a-47c9-8000-f2332940df89
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2addaf540407c7b899cc81a7512fead9bb205ad5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022228"
---
# <a name="complex-type-derivation-using-the-extension-mechanism"></a><span data-ttu-id="d19bc-102">使用延伸模組機制的複雜型別衍生</span><span class="sxs-lookup"><span data-stu-id="d19bc-102">Complex Type Derivation Using the Extension Mechanism</span></span>
<span data-ttu-id="d19bc-103">由延伸模組衍生的複雜類型是其基底資料型別的功能超集。</span><span class="sxs-lookup"><span data-stu-id="d19bc-103">A complex type derived by extension is a functional superset of its base data type.</span></span> <span data-ttu-id="d19bc-104">正如其名所示，它的基底資料型別是所定義型別的基礎，與基底型別的差異為附加的。</span><span class="sxs-lookup"><span data-stu-id="d19bc-104">As the name implies, its base data type is the basis for the type being defined, where the differences from the base type are additive.</span></span> <span data-ttu-id="d19bc-105">本主題提供範例，其中的兩個元素**ShippingAddress**並**BillingAddress**為基礎的複雜全域型別**GlobalAddrType**。</span><span class="sxs-lookup"><span data-stu-id="d19bc-105">This topic provides an example in which the two elements **ShippingAddress** and **BillingAddress** are based on the complex global type **GlobalAddrType**.</span></span> <span data-ttu-id="d19bc-106">**ShippingAddress**只會定義為類型**GlobalAddrType**，而**BillingAddress**則定義為延伸類型**GlobalAddrType**。</span><span class="sxs-lookup"><span data-stu-id="d19bc-106">**ShippingAddress** is simply defined to be of type **GlobalAddrType**, whereas **BillingAddress** is defined to extend the type **GlobalAddrType**.</span></span> <span data-ttu-id="d19bc-107">在此範例的結束時，其他項目加入至**BillingAddress**具名**部門**、 字串型別與預設值為 Accounts Payable。</span><span class="sxs-lookup"><span data-stu-id="d19bc-107">At the end of the example, an additional element is added to **BillingAddress**, named **Department**, with a type of string and a default value of Accounts Payable.</span></span>  
  
 <span data-ttu-id="d19bc-108">如需有關使用延伸模組機制衍生新的複雜類型之完整資訊，請參閱 W3C 網站。</span><span class="sxs-lookup"><span data-stu-id="d19bc-108">For comprehensive information about deriving new complex types by using the extension mechanism, refer to the W3C website.</span></span> <span data-ttu-id="d19bc-109">這個資料庫和其他網站的各種連結，請參閱[網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。</span><span class="sxs-lookup"><span data-stu-id="d19bc-109">For various links to this and other websites, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
 <span data-ttu-id="d19bc-110">若要從複雜全域類型的結構描述樹狀結構中的其他位置中的延伸模組，衍生先插入新**記錄**的所需位置的節點。</span><span class="sxs-lookup"><span data-stu-id="d19bc-110">To derive from a complex global type by extension, in another location in the schema tree, begin by inserting a new **Record** node at the desired location.</span></span> <span data-ttu-id="d19bc-111">然後設定其**基底資料型別**複雜全域型別名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="d19bc-111">Then set its **Base Data Type** property to the name of a complex global type.</span></span>  
  
 <span data-ttu-id="d19bc-112">在下列範例中， **BillingAddress**是新插入的名稱**記錄**節點，並**GlobalAddrType**是從它的複雜全域類型名稱衍生，並延伸。</span><span class="sxs-lookup"><span data-stu-id="d19bc-112">In the following example, **BillingAddress** is the name of the newly inserted **Record** node, and **GlobalAddrType** is the name of the complex global type from which it derives, and intends to extend.</span></span> <span data-ttu-id="d19bc-113">在結構描述樹狀結構檢視中之後,**基底資料型別**已設為**GlobalAddrType**，重複的節點結構會顯示在名為節點**BillingAddress**，名為的節點下相鄰節點結構相同**ShippingAddress**。</span><span class="sxs-lookup"><span data-stu-id="d19bc-113">In the schema tree view, after **Base Data Type** has been set to **GlobalAddrType**, a duplicate node structure would be displayed below the node named **BillingAddress**, identical to the adjacent node structure under the node named **ShippingAddress**.</span></span> <span data-ttu-id="d19bc-114">它們之間的差異在於**BillingAddress**節點結構會延伸至基底資料型別超出**GlobalAddrType**，而**ShippingAddress**結構則維持相同的基底資料型別**GlobalAddrType**。</span><span class="sxs-lookup"><span data-stu-id="d19bc-114">The difference between them is that the **BillingAddress** node structure will be extensible beyond the base data type **GlobalAddrType**, and the **ShippingAddress** structure will remain identical to the base data type **GlobalAddrType**.</span></span>  
  
- <span data-ttu-id="d19bc-115">之前，新插入的節點具有名為**BillingAddress**。</span><span class="sxs-lookup"><span data-stu-id="d19bc-115">Before, with a newly inserted node named **BillingAddress**.</span></span>  
  
  ```  
  <xs:schema>  
      <xs:element name="Root">  
          <xs:complexType>  
              <xs:sequence>  
                  <xs:element name="ShippingAddress" type="GlobalAddrType" />  
                  <xs:element name="BillingAddress">  
                      <xs:sequence />  
                  </xs:element>  
              </xs:sequence>  
          </xs:complexType>  
      </xs:element>  
      <xs:complexType name="GlobalAddrType">  
      [Address structure defined globally here.]  
      </xs:complexType>  
  </xs:schema>  
  ```  
  
- <span data-ttu-id="d19bc-116">從複雜的基底型別衍生之後**GlobalAddrType**，由延伸模組。</span><span class="sxs-lookup"><span data-stu-id="d19bc-116">After deriving from the complex base type **GlobalAddrType**, by extension.</span></span>  
  
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
  
  <span data-ttu-id="d19bc-117">您透過插入節點至指定的基底資料類型的延伸模組**BillingAddress**結構描述樹狀結構中的節點。</span><span class="sxs-lookup"><span data-stu-id="d19bc-117">You specify extensions to the base data type by inserting nodes into the **BillingAddress** node in the schema tree.</span></span> <span data-ttu-id="d19bc-118">下列 XSD 片段顯示空的延伸項目會展開何時**Sequence 群組**節點會插入為新的子系**BillingAddress**節點，然後**欄位項目**名為的節點**PaymentType**，為的子節點插入**Sequence 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="d19bc-118">The following XSD fragment shows how the empty extension element is expanded when a **Sequence Group** node is inserted as a new child of the **BillingAddress** node and then a **Field Element** node, named **PaymentType**, is inserted as a child node of the **Sequence Group** node.</span></span>  
  
```  
<xs:extension base="GlobalAddrType">  
    <xs:sequence>  
        <xs:element default="Accounts Payable"  
            name="Department" type="xs:string" />  
    </xs:sequence>  
</xs:extension>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d19bc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d19bc-119">See Also</span></span>  
 [<span data-ttu-id="d19bc-120">複雜全域類型衍生</span><span class="sxs-lookup"><span data-stu-id="d19bc-120">Complex Global Type Derivation</span></span>](../core/complex-global-type-derivation.md)