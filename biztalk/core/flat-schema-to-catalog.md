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
# <a name="flat-schema-to-catalog"></a><span data-ttu-id="2e25c-102">目錄的一般結構描述</span><span class="sxs-lookup"><span data-stu-id="2e25c-102">Flat Schema to Catalog</span></span>

## <a name="overview"></a><span data-ttu-id="2e25c-103">概觀</span><span class="sxs-lookup"><span data-stu-id="2e25c-103">Overview</span></span>
<span data-ttu-id="2e25c-104">您可以使用**迴圈**運算質，將單一記錄對應至多個記錄，將一般結構描述轉換成階層式結構描述。</span><span class="sxs-lookup"><span data-stu-id="2e25c-104">You can use the **Looping** functoid to convert a flat schema to an hierarchical schema by mapping a single record to multiple records.</span></span> <span data-ttu-id="2e25c-105">這是將一般結構描述轉換成 Microsoft Commerce Server 目錄的通用作業。</span><span class="sxs-lookup"><span data-stu-id="2e25c-105">This is a common operation in converting flat schemas to Microsoft Commerce Server catalogs.</span></span>  
  
 <span data-ttu-id="2e25c-106">以下程式碼顯示目錄清單產品變數的一部分，而每個變數就是其本身的記錄。</span><span class="sxs-lookup"><span data-stu-id="2e25c-106">The following code shows a portion of a catalog listing product variants with each variant as its own record.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlattening.FlatCatalog">  
    <ProductVariant ListPrice="99.99" ID="45-01" Material="Leather" Color="Black" />  
    <ProductVariant ListPrice="69.99" ID="45-02" Material="Vinyl" Color="Brown" />  
</ns0:Root>  
```  
  
 <span data-ttu-id="2e25c-107">展開類別目錄的這個部分會將部分或全部轉換**ProductVariant**成記錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="2e25c-107">Expanding this portion of the catalog would convert some or all of the **ProductVariant** attributes into records.</span></span>  
  
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
  
 <span data-ttu-id="2e25c-108">下圖顯示執行此轉換的對應。</span><span class="sxs-lookup"><span data-stu-id="2e25c-108">The following figure shows a map that performs this conversion.</span></span>  
  
 <span data-ttu-id="2e25c-109">![顯示使用 「 迴圈 」 運算質的對應。] (../core/media/loopingflattenfunctoid.gif "loopingflattenfunctoid")</span><span class="sxs-lookup"><span data-stu-id="2e25c-109">![Map showing the use of the looping functoid.](../core/media/loopingflattenfunctoid.gif "loopingflattenfunctoid")</span></span>  
<span data-ttu-id="2e25c-110">迴圈運算質、一般結構描述對應</span><span class="sxs-lookup"><span data-stu-id="2e25c-110">Looping Functoid, Flat Schema Map</span></span>  

## <a name="set-the-schema"></a><span data-ttu-id="2e25c-111">將結構描述</span><span class="sxs-lookup"><span data-stu-id="2e25c-111">Set the schema</span></span>  
 <span data-ttu-id="2e25c-112">針對這類型的對應，才能正確運作，您必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="2e25c-112">For this type of map to work correctly, you must do the following:</span></span>  
  
-   <span data-ttu-id="2e25c-113">每個連結連接到**名稱**欄位與目的結構描述中，將來源結構描述連結屬性設複製的名稱。</span><span class="sxs-lookup"><span data-stu-id="2e25c-113">For each link connecting to the **Name** field in the destination schema, set the source-schema link properties to copy the name.</span></span> <span data-ttu-id="2e25c-114">如需詳細資訊，請參閱[設定連結](../core/configuring-links.md)。</span><span class="sxs-lookup"><span data-stu-id="2e25c-114">For more information, see [Configuring Links](../core/configuring-links.md).</span></span> <span data-ttu-id="2e25c-115">另請參閱**連結屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="2e25c-115">Also see **Link Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
-   <span data-ttu-id="2e25c-116">每個連結連接到**值**欄位與目的結構描述中，將來源結構描述連結屬性設複製的值 （預設值）。</span><span class="sxs-lookup"><span data-stu-id="2e25c-116">For each link connecting to the **Value** field in the destination schema, set the source-schema link properties to copy the value (the default).</span></span>  
  
-   <span data-ttu-id="2e25c-117">連結連接**迴圈**運算質至名為記錄**功能**與目的結構描述中，將目的地結構描述連結屬性設為比對連結由上而。</span><span class="sxs-lookup"><span data-stu-id="2e25c-117">For the link connecting the **Looping** functoid to the record named **Feature** in the destination schema, set the destination-schema link properties to match links top-down.</span></span>  
  
 <span data-ttu-id="2e25c-118">此對應的反向，將目錄結構描述轉換成一般結構描述，請參閱[值對應 （簡維） 運算質](../core/value-mapping-flattening-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="2e25c-118">For the inverse of this mapping, converting a catalog schema to a flat schema, see [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e25c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e25c-119">See Also</span></span>  
 <span data-ttu-id="2e25c-120">[如何新增迴圈運算質至對應](../core/how-to-add-looping-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="2e25c-120">[How to Add Looping Functoids to a Map](../core/how-to-add-looping-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="2e25c-121">[迴圈運算質](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="2e25c-121">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="2e25c-122">值對應 （簡維） 運算質</span><span class="sxs-lookup"><span data-stu-id="2e25c-122">Value Mapping (Flattening) Functoid</span></span>](../core/value-mapping-flattening-functoid.md)