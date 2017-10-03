---
title: "值對應 （簡維） 運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Value Mapping (Flattening) functoids
ms.assetid: d30c3ffe-d3ed-46fd-a692-cd26d042033c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d17d5d64409cd434075dfd4c556209864784e4d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="value-mapping-flattening-functoid"></a><span data-ttu-id="f427c-102">值對應 (簡維) 運算質</span><span class="sxs-lookup"><span data-stu-id="f427c-102">Value Mapping (Flattening) Functoid</span></span>
<span data-ttu-id="f427c-103">**值對應 （簡維）**運算質可讓您轉換成單一記錄多筆記錄來簡維輸入執行個體訊息部分。</span><span class="sxs-lookup"><span data-stu-id="f427c-103">The **Value Mapping (Flattening)** functoid enables you to flatten a portion of an input instance message by converting multiple records into a single record.</span></span> <span data-ttu-id="f427c-104">這是轉換 Microsoft Commerce Server 目錄中的一般作業。</span><span class="sxs-lookup"><span data-stu-id="f427c-104">This is a common operation in converting Microsoft Commerce Server catalogs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f427c-105">**值對應 （簡維）**運算質不應與結合**迴圈**運算質或**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="f427c-105">The **Value Mapping (Flattening)** functoid should not be combined with the **Looping** functoid or the **Table Looping** functoid.</span></span> <span data-ttu-id="f427c-106">若將它們合併，則會導致編譯的對應，假設沒有來源迴圈相依性下面的目標節點**迴圈**或**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="f427c-106">If they are combined, it results in a compiled map that assumes there is no source looping dependency for the target nodes that are below the **Looping** or **Table Looping** functoid.</span></span>  
  
 <span data-ttu-id="f427c-107">下列程式碼會顯示一部分列出產品變數的目錄，而變數的每個功能都會列在個別的記錄中。</span><span class="sxs-lookup"><span data-stu-id="f427c-107">The following code shows a portion of a catalog listing product variants with each feature of the variant in a separate record.</span></span>  
  
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
  
 <span data-ttu-id="f427c-108">簡維這部分的類別目錄會將轉換**功能**屬性記錄**ProductVariant**記錄。</span><span class="sxs-lookup"><span data-stu-id="f427c-108">Flattening this portion of the catalog would convert the **Feature** records into attributes of the **ProductVariant** record.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlat.ProductsOut">  
    <ProductVariant ListPrice="99.99" ID="45-01" Material="Leather" Color="Black" />  
    <ProductVariant ListPrice="69.99" ID="45-02" Material="Vinyl" Color="Brown" />  
</ns0:Root>  
```  
  
 <span data-ttu-id="f427c-109">下圖顯示執行此轉換的對應。</span><span class="sxs-lookup"><span data-stu-id="f427c-109">The following figure shows a map that performs this conversion.</span></span>  
  
 <span data-ttu-id="f427c-110">![對應來源記錄使用運算質。] (../core/media/valuemappingflattenfunctoid.gif "valuemappingflattenfunctoid")</span><span class="sxs-lookup"><span data-stu-id="f427c-110">![Map source records using a functoid.](../core/media/valuemappingflattenfunctoid.gif "valuemappingflattenfunctoid")</span></span>  
<span data-ttu-id="f427c-111">值對應 (簡維) 運算質對應</span><span class="sxs-lookup"><span data-stu-id="f427c-111">Value Mapping (Flattening) Functoid Map</span></span>  
  
 <span data-ttu-id="f427c-112">**值對應 （簡維）**運算質會傳回其第二個參數的值，如果第一個參數為 true。</span><span class="sxs-lookup"><span data-stu-id="f427c-112">The **Value Mapping (Flattening)** functoid returns the value of its second parameter if its first parameter is true.</span></span> <span data-ttu-id="f427c-113">在此圖中，第一個**等於**運算質會測試**名稱**屬性等於"Material"。</span><span class="sxs-lookup"><span data-stu-id="f427c-113">In this map, the first **Equal** functoid tests to see if the **Name** attribute is equal to "Material".</span></span> <span data-ttu-id="f427c-114">如果屬性等於"Material"，**等於**運算質會傳回**True**。</span><span class="sxs-lookup"><span data-stu-id="f427c-114">If the attribute is equal to "Material", the **Equal** functoid returns **True**.</span></span> <span data-ttu-id="f427c-115">接著，這會導致**值對應 （簡維）**指派的值，運算質**值**屬性設定為輸出訊息中的欄位。</span><span class="sxs-lookup"><span data-stu-id="f427c-115">In turn, this causes the **Value Mapping (Flattening)** functoid to assign the value of the **Value** attribute to the field in the output message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f427c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f427c-116">See Also</span></span>  
 <span data-ttu-id="f427c-117">[如何新增值對應 （簡維） 運算質至對應](../core/how-to-add-value-mapping-flattening-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="f427c-117">[How to Add Value Mapping (Flattening) Functoids to a Map](../core/how-to-add-value-mapping-flattening-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="f427c-118">[類別目錄的一般結構描述](../core/flat-schema-to-catalog.md) </span><span class="sxs-lookup"><span data-stu-id="f427c-118">[Flat Schema to Catalog](../core/flat-schema-to-catalog.md) </span></span>  
 [<span data-ttu-id="f427c-119">進階運算質</span><span class="sxs-lookup"><span data-stu-id="f427c-119">Advanced Functoids</span></span>](../core/advanced-functoids.md)