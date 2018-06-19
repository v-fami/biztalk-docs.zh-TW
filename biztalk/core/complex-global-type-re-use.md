---
title: 複雜全域型別重複使用 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d0d8018-f2c6-44cc-9330-2385ac8887eb
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 492d1c345b1ac540bc2410c554be29996fc52dd6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231766"
---
# <a name="complex-global-type-re-use"></a><span data-ttu-id="02262-102">複雜全域型別重複使用</span><span class="sxs-lookup"><span data-stu-id="02262-102">Complex Global Type Re-use</span></span>
<span data-ttu-id="02262-103">若要使用複雜全域型別為是，結構描述樹狀結構中的其他位置中開始插入新**記錄**節點所需的位置。</span><span class="sxs-lookup"><span data-stu-id="02262-103">To use a complex global type as is, in another location in the schema tree, begin by inserting a new **Record** node at the desired location.</span></span> <span data-ttu-id="02262-104">然後設定其**資料結構型別**複雜全域型別名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="02262-104">Then set its **Data Structure Type** property to the name of a complex global type.</span></span>  
  
 <span data-ttu-id="02262-105">在下列範例中， **BillingAddress**是新插入的名稱**記錄** 節點，和**GlobalAddrType**是其採用的複雜全域類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="02262-105">In the following example, **BillingAddress** is the name of the newly inserted **Record** node, and **GlobalAddrType** is the name of the complex global type that it adopts.</span></span> <span data-ttu-id="02262-106">在結構描述樹狀結構檢視中，重複的節點結構會顯示名為**BillingAddress**、 名為的節點下的相鄰節點結構相同**ShippingAddress**。</span><span class="sxs-lookup"><span data-stu-id="02262-106">In the schema tree view, a duplicate node structure would be displayed below the node named **BillingAddress**, identical to the adjacent node structure under the node named **ShippingAddress**.</span></span>  
  
-   <span data-ttu-id="02262-107">之前，與新插入的節點名稱為**BillingAddress**。</span><span class="sxs-lookup"><span data-stu-id="02262-107">Before, with a newly inserted node named **BillingAddress**.</span></span>  
  
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
  
-   <span data-ttu-id="02262-108">使用複雜基底類型之後**GlobalAddrType**、 原狀。</span><span class="sxs-lookup"><span data-stu-id="02262-108">After using the complex base type **GlobalAddrType**, as is.</span></span>  
  
    ```  
    <xs:schema>  
        <xs:element name="Root">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ShippingAddress" type="GlobalAddrType" />  
                    <xs:element name="BillingAddress" type="GlobalAddrType" />  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
        <xs:complexType name="GlobalAddrType">  
        [Address structure defined globally here.]  
        </xs:complexType>  
    </xs:schema>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="02262-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02262-109">See Also</span></span>  
 [<span data-ttu-id="02262-110">使用複雜全域型別的方式</span><span class="sxs-lookup"><span data-stu-id="02262-110">Ways to Use Complex Global Types</span></span>](../core/ways-to-use-complex-global-types.md)