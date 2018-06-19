---
title: 一般類別目錄的結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0e37afa-2329-4691-9fa1-82b8c7bcd59a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f3a45ad66ca10ab829a4cc7279891487124c3cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246254"
---
# <a name="flat-schema-to-catalog"></a>目錄的一般結構描述

## <a name="overview"></a>概觀
您可以使用**迴圈**運算質，將單一記錄對應至多個記錄，將一般結構描述轉換成階層式結構描述。 這是將一般結構描述轉換成 Microsoft Commerce Server 目錄的通用作業。  
  
 以下程式碼顯示目錄清單產品變數的一部分，而每個變數就是其本身的記錄。  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlattening.FlatCatalog">  
    <ProductVariant ListPrice="99.99" ID="45-01" Material="Leather" Color="Black" />  
    <ProductVariant ListPrice="69.99" ID="45-02" Material="Vinyl" Color="Brown" />  
</ns0:Root>  
```  
  
 展開類別目錄的這個部分會將部分或全部轉換**ProductVariant**成記錄的屬性。  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlattening.Catalog">  
    <ProductVariant ListPrice="99.99" ID="45-01">  
        <Feature Name="Material" Value="Leather"/>  
        <Feature Name="Color" Value="Black"/>  
    </ProductVariant>  
    <ProductVariant ListPrice="69.99" ID="45-02">  
        <Feature Name="Material" Value="Vinyl"/>  
        <Feature Name="Color" Value="Brown"/>  
    </ProductVariant>  
</ns0:Root>  
```  
  
 下圖顯示執行此轉換的對應。  
  
 ![顯示使用 「 迴圈 」 運算質的對應。] (../core/media/loopingflattenfunctoid.gif "loopingflattenfunctoid")  
迴圈運算質、一般結構描述對應  

## <a name="set-the-schema"></a>將結構描述  
 針對這類型的對應，才能正確運作，您必須執行下列作業：  
  
-   每個連結連接到**名稱**欄位與目的結構描述中，將來源結構描述連結屬性設複製的名稱。 如需詳細資訊，請參閱[設定連結](../core/configuring-links.md)。 另請參閱**連結屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
-   每個連結連接到**值**欄位與目的結構描述中，將來源結構描述連結屬性設複製的值 （預設值）。  
  
-   連結連接**迴圈**運算質至名為記錄**功能**與目的結構描述中，將目的地結構描述連結屬性設為比對連結由上而。  
  
 此對應的反向，將目錄結構描述轉換成一般結構描述，請參閱[值對應 （簡維） 運算質](../core/value-mapping-flattening-functoid.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何新增迴圈運算質至對應](../core/how-to-add-looping-functoids-to-a-map.md)   
 [迴圈運算質](../core/looping-functoid.md)   
 [值對應 （簡維） 運算質](../core/value-mapping-flattening-functoid.md)