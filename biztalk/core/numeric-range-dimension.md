---
title: "數字範圍維度 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], Numeric Range dimension
- Numeric Range dimension [BAM]
ms.assetid: a874ce44-b034-498f-ba58-114028dbef2c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fb6d4c21e0a207cfeec3e592569ca0f48f3badf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="numeric-range-dimension"></a><span data-ttu-id="249ab-102">數字範圍維度</span><span class="sxs-lookup"><span data-stu-id="249ab-102">Numeric Range Dimension</span></span>
<span data-ttu-id="249ab-103">您可以使用數字範圍維度，依據指定範圍的易記名稱將彙總分類。</span><span class="sxs-lookup"><span data-stu-id="249ab-103">The numeric range dimension allows aggregations to be categorized based on friendly names of given ranges.</span></span> <span data-ttu-id="249ab-104">例如，商務分析師可以定義名為「PO 大小」的數字範圍維度，以「小」代表訂單金額介於 0 至 $100 的範圍；以「中」代表訂單金額介於 $100 至 $1,000 的範圍；並以「大」代表訂單金額超過 $1,000 的範圍。</span><span class="sxs-lookup"><span data-stu-id="249ab-104">For example, a business analyst can define a numeric range dimension named PO Size with the ranges Small for purchase orders between 0-$100, Medium for purchase orders between $100 to $1,000, and Large for purchase orders exceeding $1,000.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="249ab-105">如果訂單金額不在定義的範圍內 (例如，訂單金額小於 0)，BAM 便會自動建立「超出範圍」資料列來配合超出範圍的資料。</span><span class="sxs-lookup"><span data-stu-id="249ab-105">If a purchase order amount is not in the defined ranges, for example, a purchase order amount is less than 0, and then an "Out of range" row will be automatically created by BAM to accommodate the out-of-range data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="249ab-106">您不可以建立兩個參考相同資料別名的數字範圍維度。</span><span class="sxs-lookup"><span data-stu-id="249ab-106">You cannot create two numeric range dimensions that reference the same data alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="249ab-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="249ab-107">See Also</span></span>  
 <span data-ttu-id="249ab-108">[如何使用樞紐分析表](../core/how-to-use-the-pivottable.md) </span><span class="sxs-lookup"><span data-stu-id="249ab-108">[How to Use the PivotTable](../core/how-to-use-the-pivottable.md) </span></span>  
 <span data-ttu-id="249ab-109">[進度維度](../core/progress-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="249ab-109">[Progress Dimension](../core/progress-dimension.md) </span></span>  
 <span data-ttu-id="249ab-110">[資料維度](../core/data-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="249ab-110">[Data Dimension](../core/data-dimension.md) </span></span>  
 <span data-ttu-id="249ab-111">[時間維度](../core/time-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="249ab-111">[Time Dimension](../core/time-dimension.md) </span></span>  
 [<span data-ttu-id="249ab-112">定義維度</span><span class="sxs-lookup"><span data-stu-id="249ab-112">Defining Dimensions</span></span>](../core/defining-dimensions.md)