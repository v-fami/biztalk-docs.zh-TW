---
title: "大量複製運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- anyAttribute node
- Mass Copy functoids, about Mass Copy functoids
- any node
- Mass Copy functoids
ms.assetid: 228ff569-2e21-4e81-b564-6936241cdf6b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fe0a9bc65369327a17591fb6adecb6bd6105333
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mass-copy-functoid"></a>大量複製運算質
**大量複製**運算質可讓您使用包含的結構描述的對應**任何**和**anyAttribute**項目。 這些項目實際上是以 XML 結構描述定義語言提供的萬用字元對應未知的結構或屬性。  
  
 除了處理具有未知結構的資料**大量複製**運算質可讓您簡化結構描述開發： 需要詳細指定只將處理結構描述的部分。  
  
 **大量複製**運算質複製項目對應至來源結構描述節點連接到輸入執行個體訊息中**大量複製**運算質。 運算質也會複製其整個子結構，並在輸出執行個體訊息中，於目的結構描述中連結的節點重新建立子結構。 因此，您也可以使用**大量複製**運算質複製任何具有相同子結構的來源和目的記錄。  
  
 下圖顯示**大量複製**對應中使用的運算質。  
  
 ![大量複製運算質用法的對應](../core/media/masscopyfunctoid.gif "masscopyfunctoid")  
大量複製運算質對應  
  
 假設有下列輸入執行個體訊息。  
  
```  
<ns0:Root xmlns:ns0="http://MassCopy.ComplexDocument">  
    <PurchaseOrder>  
        <From>Kevin F. Browne</From>  
        <To>Northwind Traders</To>  
        <LineItems>  
            <Item>  
                <Product>Laptop Computer</Product>  
                <Description>Thin profile laptop</Description>  
                <Price>1999.95</Price>  
                <Quantity>1</Quantity>  
            </Item>  
        </LineItems>  
    </PurchaseOrder>  
</ns0:Root>  
```  
  
 若是使用上述對應處理此訊息，則輸出執行個體訊息會與輸入執行個體訊息相同。  
  
## <a name="see-also"></a>另請參閱  
 [如何新增大量複製運算質至對應](../core/how-to-add-mass-copy-functoids-to-a-map.md)   
 [進階運算質](../core/advanced-functoids.md)   
 [基本運算質](../core/basic-functoids.md)   
 [連結和從 Any 項目與 anyAttribute 節點](../core/links-to-and-from-the-any-element-and-anyattribute-nodes.md)