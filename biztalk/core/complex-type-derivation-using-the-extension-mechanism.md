---
title: 使用延伸模組機制的複雜型別衍生 |Microsoft 文件
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
ms.openlocfilehash: c5d36778b5ad99a0273e6199f59bdd337429a74b
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="complex-type-derivation-using-the-extension-mechanism"></a>使用延伸模組機制的複雜型別衍生
由延伸模組衍生的複雜類型是其基底資料型別的功能超集。 正如其名所示，它的基底資料型別是所定義型別的基礎，與基底型別的差異為附加的。 本主題提供範例，其中兩個項目 **ShippingAddress** 和 **BillingAddress** 複雜全域型別會根據 **GlobalAddrType**。 **ShippingAddress** 只是定義為型別的 **GlobalAddrType**, ，而 **BillingAddress** 則定義為延伸類型 **GlobalAddrType**。 在此範例結束時，其他項目加入至 **BillingAddress**, 具名 **部門**, 、 字串型別與預設值為 Accounts Payable。  
  
 如需有關使用延伸模組機制衍生新的複雜類型之完整資訊，請參閱 W3C 網站。 如需各種與其他網站連結，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。  
  
 若要從複雜全域類型的副檔名，請在結構描述樹狀結構中的其他位置衍生先插入新 **記錄** 節點所需位置。 然後設定其 **基底資料型別** 屬性的複雜全域型別名稱。  
  
 在下列範例中， **BillingAddress** 是新插入的名稱 **記錄** 節點，和 **GlobalAddrType** 從中衍生並延伸複雜全域型別的名稱。 在結構描述樹狀結構檢視中之後, **基底資料型別** 已設定為 **GlobalAddrType**, ，重複的節點結構會顯示名為 **BillingAddress**, 、 名為的節點下相鄰節點結構相同 **ShippingAddress**。 它們之間的差異在於 **BillingAddress** 節點結構將會擴充基底資料型別 **GlobalAddrType**, ，而 **ShippingAddress** 結構則維持相同的基底資料型別 **GlobalAddrType**。  
  
-   之前，與新插入的節點名稱為 **BillingAddress**。  
  
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
  
-   複雜的基底型別衍生之後 **GlobalAddrType**, ，延伸模組。  
  
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
  
 您可以指定基底資料類型的擴充功能透過插入節點至 **BillingAddress** 結構描述樹狀結構中的節點。 下列 XSD 片段會顯示空的延伸項目已展開時 **Sequence 群組** 節點插入為新的子系的 **BillingAddress** 節點，然後 **欄位項目** 節點，名為 **PaymentType**, ，為子節點插入 **Sequence 群組** 節點。  
  
```  
<xs:extension base="GlobalAddrType">  
    <xs:sequence>  
        <xs:element default="Accounts Payable"  
            name="Department" type="xs:string" />  
    </xs:sequence>  
</xs:extension>  
```  
  
## <a name="see-also"></a>另請參閱  
 [複雜全域類型衍生](../core/complex-global-type-derivation.md)