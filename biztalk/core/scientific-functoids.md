---
title: 科學運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0311b7dc-1955-45af-b858-681faccc939b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf7a181f200948335aab0ffa2a06d43d38408afb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977414"
---
# <a name="scientific-functoids"></a><span data-ttu-id="6de7b-102">科學運算質</span><span class="sxs-lookup"><span data-stu-id="6de7b-102">Scientific Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="6de7b-103">概觀</span><span class="sxs-lookup"><span data-stu-id="6de7b-103">Overview</span></span>
<span data-ttu-id="6de7b-104">**科學**運算質用來執行各種標準三角、 對數以及指數計算。</span><span class="sxs-lookup"><span data-stu-id="6de7b-104">**Scientific** functoids are used to perform a variety of standard trigonometric, logarithmic, and exponential calculations.</span></span>  

 <span data-ttu-id="6de7b-105">除了**指定基底對數**並**X ^ Y**運算質接受兩個輸入的參數，**科學**所有的運算質接受單一參數。</span><span class="sxs-lookup"><span data-stu-id="6de7b-105">With the exception of the **Base-Specified Logarithm** and **X^Y** functoids, which each take two input parameters, the **Scientific** functoids all take a single parameter.</span></span>  

 <span data-ttu-id="6de7b-106">四種三角**科學**運算質 (**反正切值**，**餘弦函數**，**正弦**，和**正切函數**) 所有使用弧度為單位，而不是度為單位的相關輸入或輸出參數。</span><span class="sxs-lookup"><span data-stu-id="6de7b-106">The four trigonometric **Scientific** functoids (**Arc Tangent**, **Cosine**, **Sine**, and **Tangent**) all use radians rather than degrees as the units for their relevant input or output parameters.</span></span> <span data-ttu-id="6de7b-107">弧度是一種角度測量單位，例如一個圓為 2π 弧度。</span><span class="sxs-lookup"><span data-stu-id="6de7b-107">A radian is a unit of measure of angles, such that there are 2π radians in a circle.</span></span> <span data-ttu-id="6de7b-108">說明如下：</span><span class="sxs-lookup"><span data-stu-id="6de7b-108">It follows that:</span></span>  

- <span data-ttu-id="6de7b-109">2π 弧度等於 360 度</span><span class="sxs-lookup"><span data-stu-id="6de7b-109">2π radians equals 360 degrees</span></span>  

- <span data-ttu-id="6de7b-110">1 弧度 = 180/π 度</span><span class="sxs-lookup"><span data-stu-id="6de7b-110">1 radian = 180/π degrees</span></span>  

- <span data-ttu-id="6de7b-111">1 度 = π/180 弧度</span><span class="sxs-lookup"><span data-stu-id="6de7b-111">1 degree = π/180 radians</span></span>  

  <span data-ttu-id="6de7b-112">如果您輸入或輸出的執行個體訊息會使用度數作為其測量單位的角度，您必須使用**數學**運算質與三角倂**科學**」 運算質達到正確的結果。</span><span class="sxs-lookup"><span data-stu-id="6de7b-112">If your input or output instance messages use degrees as their unit of measure for angles, you will need to use a **Mathematical** functoid in conjunction with a trigonometric **Scientific** functoid to achieve the correct result.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="6de7b-113">可用的運算質</span><span class="sxs-lookup"><span data-stu-id="6de7b-113">Available functoids</span></span>  
 <span data-ttu-id="6de7b-114">**科學**運算質為：</span><span class="sxs-lookup"><span data-stu-id="6de7b-114">The **Scientific** functoids are:</span></span> 

* <span data-ttu-id="6de7b-115">10^n</span><span class="sxs-lookup"><span data-stu-id="6de7b-115">10^n</span></span>
* <span data-ttu-id="6de7b-116">反正切值</span><span class="sxs-lookup"><span data-stu-id="6de7b-116">Arc Tangent</span></span>
* <span data-ttu-id="6de7b-117">指定基底對數</span><span class="sxs-lookup"><span data-stu-id="6de7b-117">Base-Specified Logarithm</span></span>
* <span data-ttu-id="6de7b-118">常用對數</span><span class="sxs-lookup"><span data-stu-id="6de7b-118">Common Logarithm</span></span>
* <span data-ttu-id="6de7b-119">餘弦函數</span><span class="sxs-lookup"><span data-stu-id="6de7b-119">Cosine</span></span>
* <span data-ttu-id="6de7b-120">自然指數函式</span><span class="sxs-lookup"><span data-stu-id="6de7b-120">Natural Exponential Function</span></span>
* <span data-ttu-id="6de7b-121">自然對數</span><span class="sxs-lookup"><span data-stu-id="6de7b-121">Natural Logarithm</span></span>
* <span data-ttu-id="6de7b-122">正弦函數</span><span class="sxs-lookup"><span data-stu-id="6de7b-122">Sine</span></span>
* <span data-ttu-id="6de7b-123">正切函數</span><span class="sxs-lookup"><span data-stu-id="6de7b-123">Tangent</span></span>
* <span data-ttu-id="6de7b-124">X^Y</span><span class="sxs-lookup"><span data-stu-id="6de7b-124">X^Y</span></span>

## <a name="see-also"></a><span data-ttu-id="6de7b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6de7b-125">See Also</span></span>  
- [<span data-ttu-id="6de7b-126">如何新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="6de7b-126">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
- <span data-ttu-id="6de7b-127">**科學運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="6de7b-127">**Scientific Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
