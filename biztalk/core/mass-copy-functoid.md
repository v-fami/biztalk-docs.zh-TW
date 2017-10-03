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
# <a name="mass-copy-functoid"></a><span data-ttu-id="ebcde-102">大量複製運算質</span><span class="sxs-lookup"><span data-stu-id="ebcde-102">Mass Copy Functoid</span></span>
<span data-ttu-id="ebcde-103">**大量複製**運算質可讓您使用包含的結構描述的對應**任何**和**anyAttribute**項目。</span><span class="sxs-lookup"><span data-stu-id="ebcde-103">The **Mass Copy** functoid enables your maps to use schemas that include **any** and **anyAttribute** elements.</span></span> <span data-ttu-id="ebcde-104">這些項目實際上是以 XML 結構描述定義語言提供的萬用字元對應未知的結構或屬性。</span><span class="sxs-lookup"><span data-stu-id="ebcde-104">These elements are, in essence, wildcards provided in the XML Schema definition language to match unknown structures or attributes.</span></span>  
  
 <span data-ttu-id="ebcde-105">除了處理具有未知結構的資料**大量複製**運算質可讓您簡化結構描述開發： 需要詳細指定只將處理結構描述的部分。</span><span class="sxs-lookup"><span data-stu-id="ebcde-105">In addition to handling data with unknown structure, the **Mass Copy** functoid enables you to simplify schema development: only the portions of a schema that will be processed need to be specified in detail.</span></span>  
  
 <span data-ttu-id="ebcde-106">**大量複製**運算質複製項目對應至來源結構描述節點連接到輸入執行個體訊息中**大量複製**運算質。</span><span class="sxs-lookup"><span data-stu-id="ebcde-106">The **Mass Copy** functoid copies the element in the input instance message corresponding to the source schema node connected to the **Mass Copy** functoid.</span></span> <span data-ttu-id="ebcde-107">運算質也會複製其整個子結構，並在輸出執行個體訊息中，於目的結構描述中連結的節點重新建立子結構。</span><span class="sxs-lookup"><span data-stu-id="ebcde-107">The functoid also copies any and all of its substructure, and re-creates it in the output instance message at the linked node in the destination schema.</span></span> <span data-ttu-id="ebcde-108">因此，您也可以使用**大量複製**運算質複製任何具有相同子結構的來源和目的記錄。</span><span class="sxs-lookup"><span data-stu-id="ebcde-108">Thus, you can also use the **Mass Copy** functoid to copy any source and destination records having identical substructures.</span></span>  
  
 <span data-ttu-id="ebcde-109">下圖顯示**大量複製**對應中使用的運算質。</span><span class="sxs-lookup"><span data-stu-id="ebcde-109">The following figure shows the **Mass Copy** functoid used in a map.</span></span>  
  
 <span data-ttu-id="ebcde-110">![大量複製運算質用法的對應](../core/media/masscopyfunctoid.gif "masscopyfunctoid")</span><span class="sxs-lookup"><span data-stu-id="ebcde-110">![Map illustrating the use of the mass copy functoid](../core/media/masscopyfunctoid.gif "masscopyfunctoid")</span></span>  
<span data-ttu-id="ebcde-111">大量複製運算質對應</span><span class="sxs-lookup"><span data-stu-id="ebcde-111">Mass Copy Functoid Map</span></span>  
  
 <span data-ttu-id="ebcde-112">假設有下列輸入執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="ebcde-112">Consider the following input instance message.</span></span>  
  
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
  
 <span data-ttu-id="ebcde-113">若是使用上述對應處理此訊息，則輸出執行個體訊息會與輸入執行個體訊息相同。</span><span class="sxs-lookup"><span data-stu-id="ebcde-113">If the preceding map were used to process this message, the output instance message would be identical to the input instance message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebcde-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebcde-114">See Also</span></span>  
 <span data-ttu-id="ebcde-115">[如何新增大量複製運算質至對應](../core/how-to-add-mass-copy-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="ebcde-115">[How to Add Mass Copy Functoids to a Map](../core/how-to-add-mass-copy-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="ebcde-116">[進階運算質](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="ebcde-116">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="ebcde-117">[基本運算質](../core/basic-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="ebcde-117">[Basic Functoids](../core/basic-functoids.md) </span></span>  
 [<span data-ttu-id="ebcde-118">連結和從 Any 項目與 anyAttribute 節點</span><span class="sxs-lookup"><span data-stu-id="ebcde-118">Links To and From the Any Element and anyAttribute Nodes</span></span>](../core/links-to-and-from-the-any-element-and-anyattribute-nodes.md)