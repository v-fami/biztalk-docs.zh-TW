---
title: "資料維度 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data dimension [BAM]
- aggregations [BAM], data dimensions
ms.assetid: 07b5e56a-4fd5-4c88-a98a-758e514d0621
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7138cf31a9cb86a9ba949142129ac5c906754b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-dimension"></a><span data-ttu-id="cd893-102">資料維度</span><span class="sxs-lookup"><span data-stu-id="cd893-102">Data Dimension</span></span>
<span data-ttu-id="cd893-103">定義資料維度以允許將 BAM 活動中部分文字項目的值使用在資料列或資料行上。</span><span class="sxs-lookup"><span data-stu-id="cd893-103">Defining a data dimension allows the value of some text items in the BAM activity to be used on rows or columns.</span></span> <span data-ttu-id="cd893-104">例如，名為「產品」的資料維度可以用來建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="cd893-104">For example a data dimension named Product can be used to create the following table:</span></span>  
  
|<span data-ttu-id="cd893-105">產品</span><span class="sxs-lookup"><span data-stu-id="cd893-105">Product</span></span>|<span data-ttu-id="cd893-106">Count</span><span class="sxs-lookup"><span data-stu-id="cd893-106">Count</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="cd893-107">網球拍</span><span class="sxs-lookup"><span data-stu-id="cd893-107">Tennis racquets</span></span>|<span data-ttu-id="cd893-108">100</span><span class="sxs-lookup"><span data-stu-id="cd893-108">100</span></span>|  
|<span data-ttu-id="cd893-109">足球</span><span class="sxs-lookup"><span data-stu-id="cd893-109">Soccer balls</span></span>|<span data-ttu-id="cd893-110">200</span><span class="sxs-lookup"><span data-stu-id="cd893-110">200</span></span>|  
  
 <span data-ttu-id="cd893-111">此外，您也可以在 BAM 檢視精靈中定義一個以上的資料維度。</span><span class="sxs-lookup"><span data-stu-id="cd893-111">Also, more than one data dimension can be defined in the BAM view wizard.</span></span> <span data-ttu-id="cd893-112">例如，定義名為的資料維度**位置**的層級**狀態**和**縣 （市)**可用來建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="cd893-112">For example, defining a data dimension named **Location** with levels for **State** and **City** can be used to create the following table:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="cd893-113">California</span><span class="sxs-lookup"><span data-stu-id="cd893-113">California</span></span>||<span data-ttu-id="cd893-114">Washington</span><span class="sxs-lookup"><span data-stu-id="cd893-114">Washington</span></span>|  
||<span data-ttu-id="cd893-115">Los Angeles</span><span class="sxs-lookup"><span data-stu-id="cd893-115">Los Angeles</span></span>|<span data-ttu-id="cd893-116">San Francisco</span><span class="sxs-lookup"><span data-stu-id="cd893-116">San Francisco</span></span>|<span data-ttu-id="cd893-117">Seattle</span><span class="sxs-lookup"><span data-stu-id="cd893-117">Seattle</span></span>|  
|<span data-ttu-id="cd893-118">網球拍</span><span class="sxs-lookup"><span data-stu-id="cd893-118">Tennis racquets</span></span>|<span data-ttu-id="cd893-119">50</span><span class="sxs-lookup"><span data-stu-id="cd893-119">50</span></span>|<span data-ttu-id="cd893-120">20</span><span class="sxs-lookup"><span data-stu-id="cd893-120">20</span></span>|<span data-ttu-id="cd893-121">30</span><span class="sxs-lookup"><span data-stu-id="cd893-121">30</span></span>|  
|<span data-ttu-id="cd893-122">足球</span><span class="sxs-lookup"><span data-stu-id="cd893-122">Soccer balls</span></span>|<span data-ttu-id="cd893-123">130</span><span class="sxs-lookup"><span data-stu-id="cd893-123">130</span></span>|<span data-ttu-id="cd893-124">50</span><span class="sxs-lookup"><span data-stu-id="cd893-124">50</span></span>|<span data-ttu-id="cd893-125">20</span><span class="sxs-lookup"><span data-stu-id="cd893-125">20</span></span>|  
  
 <span data-ttu-id="cd893-126">這個資料表使用「產品」維度做為資料列，並使用「位置」維度做為資料行。</span><span class="sxs-lookup"><span data-stu-id="cd893-126">In this table, the Product dimension was used as the rows, and the Location dimension was used as the columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd893-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd893-127">See Also</span></span>  
 <span data-ttu-id="cd893-128">[時間維度](../core/time-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="cd893-128">[Time Dimension](../core/time-dimension.md) </span></span>  
 <span data-ttu-id="cd893-129">[進度維度](../core/progress-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="cd893-129">[Progress Dimension](../core/progress-dimension.md) </span></span>  
 <span data-ttu-id="cd893-130">[數字範圍維度](../core/numeric-range-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="cd893-130">[Numeric Range Dimension](../core/numeric-range-dimension.md) </span></span>  
 [<span data-ttu-id="cd893-131">定義維度</span><span class="sxs-lookup"><span data-stu-id="cd893-131">Defining Dimensions</span></span>](../core/defining-dimensions.md)