---
title: 值對應 （簡維） 運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Value Mapping (Flattening) functoids
ms.assetid: d30c3ffe-d3ed-46fd-a692-cd26d042033c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d17d5d64409cd434075dfd4c556209864784e4d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287870"
---
# <a name="value-mapping-flattening-functoid"></a>值對應 (簡維) 運算質
**值對應 （簡維）** 運算質可讓您轉換成單一記錄多筆記錄來簡維輸入執行個體訊息部分。 這是轉換 Microsoft Commerce Server 目錄中的一般作業。  
  
> [!NOTE]
>  **值對應 （簡維）** 運算質不應與結合**迴圈**運算質或**表格迴圈**運算質。 若將它們合併，則會導致編譯的對應，假設沒有來源迴圈相依性下面的目標節點**迴圈**或**表格迴圈**運算質。  
  
 下列程式碼會顯示一部分列出產品變數的目錄，而變數的每個功能都會列在個別的記錄中。  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlat.ProductsIn">  
    <ProductVariant ListPrice="99.99" ID="45-01">  
        <Feature Name="Material" Value="Leather" />  
        <Feature Name="Color" Value="Black" />  
    </ProductVariant>  
    <ProductVariant ListPrice="69.99" ID="45-02">  
        <Feature Name="Material" Value="Vinyl" />  
        <Feature Name="Color" Value="Brown" />  
    </ProductVariant>  
</nso0:Root>  
```  
  
 簡維這部分的類別目錄會將轉換**功能**屬性記錄**ProductVariant**記錄。  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlat.ProductsOut">  
    <ProductVariant ListPrice="99.99" ID="45-01" Material="Leather" Color="Black" />  
    <ProductVariant ListPrice="69.99" ID="45-02" Material="Vinyl" Color="Brown" />  
</ns0:Root>  
```  
  
 下圖顯示執行此轉換的對應。  
  
 ![對應來源記錄使用運算質。](../core/media/valuemappingflattenfunctoid.gif "valuemappingflattenfunctoid")  
值對應 (簡維) 運算質對應  
  
 **值對應 （簡維）** 運算質會傳回其第二個參數的值，如果第一個參數為 true。 在此圖中，第一個**等於**運算質會測試**名稱**屬性等於"Material"。 如果屬性等於"Material"，**等於**運算質會傳回**True**。 接著，這會導致**值對應 （簡維）** 指派的值，運算質**值**屬性設定為輸出訊息中的欄位。  
  
## <a name="see-also"></a>另請參閱  
 [如何新增值對應 （簡維） 運算質至對應](../core/how-to-add-value-mapping-flattening-functoids-to-a-map.md)   
 [類別目錄的一般結構描述](../core/flat-schema-to-catalog.md)   
 [進階運算質](../core/advanced-functoids.md)