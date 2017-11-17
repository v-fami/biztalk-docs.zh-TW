---
title: "時間維度 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Time dimension [BAM]
- aggregations [BAM], Time dimension
ms.assetid: 8f83b758-09a1-4efb-ae0e-32753f56c4e4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 418afdc5b7507aba9a564628341c10495b2a740a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="time-dimension"></a><span data-ttu-id="a9bd9-102">時間維度</span><span class="sxs-lookup"><span data-stu-id="a9bd9-102">Time Dimension</span></span>
<span data-ttu-id="a9bd9-103">時間維度可用來建立與時間相關的彙總。</span><span class="sxs-lookup"><span data-stu-id="a9bd9-103">The time dimension allows aggregations to be created with respect to time.</span></span> <span data-ttu-id="a9bd9-104">例如，時間維度可以用來建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="a9bd9-104">For example a time dimension can be used to create the following table:</span></span>  
  
|<span data-ttu-id="a9bd9-105">Year</span><span class="sxs-lookup"><span data-stu-id="a9bd9-105">Year</span></span>|<span data-ttu-id="a9bd9-106">Month</span><span class="sxs-lookup"><span data-stu-id="a9bd9-106">Month</span></span>|<span data-ttu-id="a9bd9-107">Count</span><span class="sxs-lookup"><span data-stu-id="a9bd9-107">Count</span></span>|  
|----------|-----------|-----------|  
|<span data-ttu-id="a9bd9-108">2003</span><span class="sxs-lookup"><span data-stu-id="a9bd9-108">2003</span></span>|<span data-ttu-id="a9bd9-109">一月</span><span class="sxs-lookup"><span data-stu-id="a9bd9-109">January</span></span>|<span data-ttu-id="a9bd9-110">120</span><span class="sxs-lookup"><span data-stu-id="a9bd9-110">120</span></span>|  
||<span data-ttu-id="a9bd9-111">二月</span><span class="sxs-lookup"><span data-stu-id="a9bd9-111">February</span></span>|<span data-ttu-id="a9bd9-112">230</span><span class="sxs-lookup"><span data-stu-id="a9bd9-112">230</span></span>|  
||<span data-ttu-id="a9bd9-113">三月</span><span class="sxs-lookup"><span data-stu-id="a9bd9-113">March</span></span>|<span data-ttu-id="a9bd9-114">350</span><span class="sxs-lookup"><span data-stu-id="a9bd9-114">350</span></span>|  
||<span data-ttu-id="a9bd9-115">四月</span><span class="sxs-lookup"><span data-stu-id="a9bd9-115">April</span></span>|<span data-ttu-id="a9bd9-116">280</span><span class="sxs-lookup"><span data-stu-id="a9bd9-116">280</span></span>|  
  
 <span data-ttu-id="a9bd9-117">時間維度可以和任何其他維度結合。</span><span class="sxs-lookup"><span data-stu-id="a9bd9-117">The time dimension can be combined with any other dimension.</span></span> <span data-ttu-id="a9bd9-118">例如，您可以在資料列使用時間維度，而在資料行使用資料維度，以建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="a9bd9-118">For example, you can use the time dimension on rows and the data dimension on columns to create the following table:</span></span>  
  
|||<span data-ttu-id="a9bd9-119">網球拍</span><span class="sxs-lookup"><span data-stu-id="a9bd9-119">Tennis racquets</span></span>|<span data-ttu-id="a9bd9-120">足球</span><span class="sxs-lookup"><span data-stu-id="a9bd9-120">Soccer balls</span></span>|  
|------|------|---------------------|------------------|  
||<span data-ttu-id="a9bd9-121">一月</span><span class="sxs-lookup"><span data-stu-id="a9bd9-121">January</span></span>|<span data-ttu-id="a9bd9-122">50</span><span class="sxs-lookup"><span data-stu-id="a9bd9-122">50</span></span>|<span data-ttu-id="a9bd9-123">70</span><span class="sxs-lookup"><span data-stu-id="a9bd9-123">70</span></span>|  
||<span data-ttu-id="a9bd9-124">二月</span><span class="sxs-lookup"><span data-stu-id="a9bd9-124">February</span></span>|<span data-ttu-id="a9bd9-125">120</span><span class="sxs-lookup"><span data-stu-id="a9bd9-125">120</span></span>|<span data-ttu-id="a9bd9-126">110</span><span class="sxs-lookup"><span data-stu-id="a9bd9-126">110</span></span>|  
||<span data-ttu-id="a9bd9-127">三月</span><span class="sxs-lookup"><span data-stu-id="a9bd9-127">March</span></span>|<span data-ttu-id="a9bd9-128">300</span><span class="sxs-lookup"><span data-stu-id="a9bd9-128">300</span></span>|<span data-ttu-id="a9bd9-129">50</span><span class="sxs-lookup"><span data-stu-id="a9bd9-129">50</span></span>|  
||<span data-ttu-id="a9bd9-130">四月</span><span class="sxs-lookup"><span data-stu-id="a9bd9-130">April</span></span>|<span data-ttu-id="a9bd9-131">220</span><span class="sxs-lookup"><span data-stu-id="a9bd9-131">220</span></span>|<span data-ttu-id="a9bd9-132">60</span><span class="sxs-lookup"><span data-stu-id="a9bd9-132">60</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9bd9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9bd9-133">See Also</span></span>  
 <span data-ttu-id="a9bd9-134">[數字範圍維度](../core/numeric-range-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="a9bd9-134">[Numeric Range Dimension](../core/numeric-range-dimension.md) </span></span>  
 <span data-ttu-id="a9bd9-135">[進度維度](../core/progress-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="a9bd9-135">[Progress Dimension](../core/progress-dimension.md) </span></span>  
 <span data-ttu-id="a9bd9-136">[資料維度](../core/data-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="a9bd9-136">[Data Dimension](../core/data-dimension.md) </span></span>  
 [<span data-ttu-id="a9bd9-137">定義維度</span><span class="sxs-lookup"><span data-stu-id="a9bd9-137">Defining Dimensions</span></span>](../core/defining-dimensions.md)