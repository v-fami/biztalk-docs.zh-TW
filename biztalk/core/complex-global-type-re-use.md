---
title: "複雜全域型別重複使用 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d8018-f2c6-44cc-9330-2385ac8887eb
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 492d1c345b1ac540bc2410c554be29996fc52dd6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="complex-global-type-re-use"></a>複雜全域型別重複使用
若要使用複雜全域型別為是，結構描述樹狀結構中的其他位置中開始插入新**記錄**節點所需的位置。 然後設定其**資料結構型別**複雜全域型別名稱的屬性。  
  
 在下列範例中， **BillingAddress**是新插入的名稱**記錄** 節點，和**GlobalAddrType**是其採用的複雜全域類型的名稱。 在結構描述樹狀結構檢視中，重複的節點結構會顯示名為**BillingAddress**、 名為的節點下的相鄰節點結構相同**ShippingAddress**。  
  
-   之前，與新插入的節點名稱為**BillingAddress**。  
  
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
  
-   使用複雜基底類型之後**GlobalAddrType**、 原狀。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [使用複雜全域型別的方式](../core/ways-to-use-complex-global-types.md)