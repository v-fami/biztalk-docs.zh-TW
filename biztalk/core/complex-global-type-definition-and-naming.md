---
title: 複雜全域型別定義和命名 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5a12956-7b77-4be8-b323-38363d04fcbc
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afe00c68f22dde956279f2dd5ac06d03bf9cb84d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231622"
---
# <a name="complex-global-type-definition-and-naming"></a>複雜全域型別定義和命名
在 [BizTalk 編輯器] 中，您可以在會用到全域型別 (在複雜型別轉換為全域型別後) 的其中一個位置，定義第一個出現的複雜型別，來開始定義複雜全域型別。 接著討論地址範例，您可以在定義結構描述中的出貨地址之過程中，定義複雜地址類型。  
  
 定義複雜型別後，您可以為它指定一個類型名稱，將它轉換成全域複雜型別。 您可以選取 [為複雜型別，通常是對應的節點**記錄**] 節點，並輸入新的型別名稱，到**資料結構型別**該節點的屬性。 雖然任何可見的變更時，會不發生結構描述樹狀結構中指定這個屬性的名稱 (例如， **GlobalAddrType**，如下列範例所示)，如果您檢查結構描述中，基礎 XSD 表示法中發生的事您就會看到下列 （縮寫） 的變更。  
  
 之前，地址結構中初次定義的內容**ShippingAddress**項目下, 發生。  
  
```  
<xs:schema>  
  <xs:element name="Root">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ShippingAddress">  
        [address structure initially defined here.]  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 之後**ShippingAddress**節點具有唯一的名稱其**資料結構型別**屬性，使它成為可為複雜全域型別，而且可能位於多個位置重複使用結構描述中，發生下列情況。  
  
```  
<xs:schema>  
  <xs:element name="Root">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ShippingAddress" type="GlobalAddrType" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="GlobalAddrType">  
  [address structure now defined globally here.]  
  </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>另請參閱  
 [型別重複使用和衍生類別](../core/type-reuse-and-derivations.md)   
 [如何建立其他節點或類型的參考](../core/how-to-create-references-to-another-node-or-type.md)