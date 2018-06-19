---
title: 在運算式中使用運算子 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, operators
- XLANG/s, operators
- orchestrations, XLANG/s
ms.assetid: f0948ce2-c508-48aa-af79-d207f577b22f
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5aec9ed6ebecb0b151dbfe9d5c09707b954fdf45
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974300"
---
# <a name="using-operators-in-expressions"></a><span data-ttu-id="3351e-102">在運算式中使用運算子</span><span class="sxs-lookup"><span data-stu-id="3351e-102">Using Operators in Expressions</span></span>
<span data-ttu-id="3351e-103">在協調流程運算式中也可以使用下列的 XLANG/s 運算子。</span><span class="sxs-lookup"><span data-stu-id="3351e-103">The following XLANG/s operators are available for use in orchestration expressions.</span></span> <span data-ttu-id="3351e-104">這些運算子幾乎完全符合 C# 中對應的運算子的功能。</span><span class="sxs-lookup"><span data-stu-id="3351e-104">They adhere closely to the functionality of the corresponding operators in C#.</span></span>  
  
|<span data-ttu-id="3351e-105">運算子</span><span class="sxs-lookup"><span data-stu-id="3351e-105">Operator</span></span>|<span data-ttu-id="3351e-106">Description</span><span class="sxs-lookup"><span data-stu-id="3351e-106">Description</span></span>|<span data-ttu-id="3351e-107">範例</span><span class="sxs-lookup"><span data-stu-id="3351e-107">Example</span></span>|  
|--------------|-----------------|-------------|  
|<span data-ttu-id="3351e-108">checked()</span><span class="sxs-lookup"><span data-stu-id="3351e-108">checked()</span></span>|<span data-ttu-id="3351e-109">在算術溢位時引發錯誤</span><span class="sxs-lookup"><span data-stu-id="3351e-109">raise error on arithmetic overflow</span></span>|<span data-ttu-id="3351e-110">checked(x = y \* 1000)</span><span class="sxs-lookup"><span data-stu-id="3351e-110">checked(x = y \* 1000)</span></span>|  
|<span data-ttu-id="3351e-111">unchecked()</span><span class="sxs-lookup"><span data-stu-id="3351e-111">unchecked()</span></span>|<span data-ttu-id="3351e-112">忽略算術溢位</span><span class="sxs-lookup"><span data-stu-id="3351e-112">ignore arithmetic overflow</span></span>|<span data-ttu-id="3351e-113">unchecked(x = y \* 1000)</span><span class="sxs-lookup"><span data-stu-id="3351e-113">unchecked(x = y \* 1000)</span></span>|  
|<span data-ttu-id="3351e-114">new</span><span class="sxs-lookup"><span data-stu-id="3351e-114">new</span></span>|<span data-ttu-id="3351e-115">建立類別的執行個體</span><span class="sxs-lookup"><span data-stu-id="3351e-115">create an instance of a class</span></span>|<span data-ttu-id="3351e-116">myObject = new MyClass;</span><span class="sxs-lookup"><span data-stu-id="3351e-116">myObject = new MyClass;</span></span>|  
|<span data-ttu-id="3351e-117">typeof</span><span class="sxs-lookup"><span data-stu-id="3351e-117">typeof</span></span>|<span data-ttu-id="3351e-118">類型擷取</span><span class="sxs-lookup"><span data-stu-id="3351e-118">Type retrieval</span></span>|<span data-ttu-id="3351e-119">myMapType = typeof(myMap)</span><span class="sxs-lookup"><span data-stu-id="3351e-119">myMapType = typeof(myMap)</span></span>|  
|<span data-ttu-id="3351e-120">succeeded()</span><span class="sxs-lookup"><span data-stu-id="3351e-120">succeeded()</span></span>|<span data-ttu-id="3351e-121">測試交易式範圍或協調流程是否順利完成</span><span class="sxs-lookup"><span data-stu-id="3351e-121">test for successful completion of transactional scope or orchestration</span></span>|<span data-ttu-id="3351e-122">成功 (\<目前範圍或服務的子交易的交易識別碼\>)</span><span class="sxs-lookup"><span data-stu-id="3351e-122">succeeded(\<transaction ID for child transaction of current scope or service\>)</span></span>|  
|<span data-ttu-id="3351e-123">exists</span><span class="sxs-lookup"><span data-stu-id="3351e-123">exists</span></span>|<span data-ttu-id="3351e-124">測試訊息內容屬性是否存在</span><span class="sxs-lookup"><span data-stu-id="3351e-124">test for the existence of a message context property</span></span>|<span data-ttu-id="3351e-125">BTS.RetryCount exists Message_In</span><span class="sxs-lookup"><span data-stu-id="3351e-125">BTS.RetryCount exists Message_In</span></span>|  
|+|<span data-ttu-id="3351e-126">一元加號</span><span class="sxs-lookup"><span data-stu-id="3351e-126">unary plus</span></span>|<span data-ttu-id="3351e-127">+(int x)</span><span class="sxs-lookup"><span data-stu-id="3351e-127">+(int x)</span></span>|  
|-|<span data-ttu-id="3351e-128">一元減號</span><span class="sxs-lookup"><span data-stu-id="3351e-128">unary minus</span></span>|<span data-ttu-id="3351e-129">-(int x)</span><span class="sxs-lookup"><span data-stu-id="3351e-129">-(int x)</span></span>|  
|<span data-ttu-id="3351e-130">!</span><span class="sxs-lookup"><span data-stu-id="3351e-130">!</span></span>|<span data-ttu-id="3351e-131">邏輯否定</span><span class="sxs-lookup"><span data-stu-id="3351e-131">logical negation</span></span>|<span data-ttu-id="3351e-132">!myBool</span><span class="sxs-lookup"><span data-stu-id="3351e-132">!myBool</span></span>|  
|~|<span data-ttu-id="3351e-133">位元補數</span><span class="sxs-lookup"><span data-stu-id="3351e-133">bitwise complement</span></span>|<span data-ttu-id="3351e-134">x = ~y</span><span class="sxs-lookup"><span data-stu-id="3351e-134">x = ~y</span></span>|  
|<span data-ttu-id="3351e-135">()</span><span class="sxs-lookup"><span data-stu-id="3351e-135">()</span></span>|<span data-ttu-id="3351e-136">強制轉型</span><span class="sxs-lookup"><span data-stu-id="3351e-136">cast</span></span>|<span data-ttu-id="3351e-137">(bool) myInt</span><span class="sxs-lookup"><span data-stu-id="3351e-137">(bool) myInt</span></span>|  
|*|<span data-ttu-id="3351e-138">times</span><span class="sxs-lookup"><span data-stu-id="3351e-138">times</span></span>|<span data-ttu-id="3351e-139">Weight = MyMsg.numOrders \* 20</span><span class="sxs-lookup"><span data-stu-id="3351e-139">Weight = MyMsg.numOrders \* 20</span></span>|  
|/|<span data-ttu-id="3351e-140">除以</span><span class="sxs-lookup"><span data-stu-id="3351e-140">divided by</span></span>|<span data-ttu-id="3351e-141">x / y</span><span class="sxs-lookup"><span data-stu-id="3351e-141">x / y</span></span>|  
|+|<span data-ttu-id="3351e-142">加</span><span class="sxs-lookup"><span data-stu-id="3351e-142">plus</span></span>|<span data-ttu-id="3351e-143">x + y</span><span class="sxs-lookup"><span data-stu-id="3351e-143">x + y</span></span>|  
|-|<span data-ttu-id="3351e-144">減</span><span class="sxs-lookup"><span data-stu-id="3351e-144">minus</span></span>|<span data-ttu-id="3351e-145">x - y</span><span class="sxs-lookup"><span data-stu-id="3351e-145">x - y</span></span>|  
|<<|<span data-ttu-id="3351e-146">左移</span><span class="sxs-lookup"><span data-stu-id="3351e-146">shift left</span></span>|<span data-ttu-id="3351e-147">x << 2</span><span class="sxs-lookup"><span data-stu-id="3351e-147">x << 2</span></span>|  
|>>|<span data-ttu-id="3351e-148">右移</span><span class="sxs-lookup"><span data-stu-id="3351e-148">shift right</span></span>|<span data-ttu-id="3351e-149">x >> 2</span><span class="sxs-lookup"><span data-stu-id="3351e-149">x >> 2</span></span>|  
|<|<span data-ttu-id="3351e-150">小於</span><span class="sxs-lookup"><span data-stu-id="3351e-150">less than</span></span>|<span data-ttu-id="3351e-151">If (MyMsg.numOrders < 10)...</span><span class="sxs-lookup"><span data-stu-id="3351e-151">If (MyMsg.numOrders < 10)...</span></span>|  
|>|<span data-ttu-id="3351e-152">大於</span><span class="sxs-lookup"><span data-stu-id="3351e-152">greater than</span></span>|<span data-ttu-id="3351e-153">如果 (MyMsg.numOrders > 10)...</span><span class="sxs-lookup"><span data-stu-id="3351e-153">If (MyMsg.numOrders > 10)...</span></span>|  
|<=|<span data-ttu-id="3351e-154">小於或等於</span><span class="sxs-lookup"><span data-stu-id="3351e-154">less than or equal to</span></span>|<span data-ttu-id="3351e-155">If (MyMsg.numOrders <= 10)...</span><span class="sxs-lookup"><span data-stu-id="3351e-155">If (MyMsg.numOrders <= 10)...</span></span>|  
|>=|<span data-ttu-id="3351e-156">大於或等於</span><span class="sxs-lookup"><span data-stu-id="3351e-156">greater than or equal to</span></span>|<span data-ttu-id="3351e-157">如果 (MyMsg.numOrders > = 10)...</span><span class="sxs-lookup"><span data-stu-id="3351e-157">If (MyMsg.numOrders >= 10)...</span></span>|  
|==|<span data-ttu-id="3351e-158">等於</span><span class="sxs-lookup"><span data-stu-id="3351e-158">equal to</span></span>|<span data-ttu-id="3351e-159">If (MyMsg.numOrders == 10)...</span><span class="sxs-lookup"><span data-stu-id="3351e-159">If (MyMsg.numOrders == 10)...</span></span>|  
|<span data-ttu-id="3351e-160">!=</span><span class="sxs-lookup"><span data-stu-id="3351e-160">!=</span></span>|<span data-ttu-id="3351e-161">不等於</span><span class="sxs-lookup"><span data-stu-id="3351e-161">not equal to</span></span>|<span data-ttu-id="3351e-162">If (MyMsg.numOrders != 10)...</span><span class="sxs-lookup"><span data-stu-id="3351e-162">If (MyMsg.numOrders != 10)...</span></span>|  
|&|<span data-ttu-id="3351e-163">和</span><span class="sxs-lookup"><span data-stu-id="3351e-163">and</span></span>|<span data-ttu-id="3351e-164">If (myByte & 255)...</span><span class="sxs-lookup"><span data-stu-id="3351e-164">If (myByte & 255)...</span></span>|  
|^|<span data-ttu-id="3351e-165">排除式 or</span><span class="sxs-lookup"><span data-stu-id="3351e-165">exclusive or</span></span>|<span data-ttu-id="3351e-166">If (myByte ^ 1)...</span><span class="sxs-lookup"><span data-stu-id="3351e-166">If (myByte ^ 1)...</span></span>|  
|<span data-ttu-id="3351e-167">&#124;</span><span class="sxs-lookup"><span data-stu-id="3351e-167">&#124;</span></span>|<span data-ttu-id="3351e-168">或</span><span class="sxs-lookup"><span data-stu-id="3351e-168">or</span></span>|<span data-ttu-id="3351e-169">如果 (myByte &#124; 1)...</span><span class="sxs-lookup"><span data-stu-id="3351e-169">If (myByte &#124; 1)...</span></span>|  
|&&|<span data-ttu-id="3351e-170">條件式 and</span><span class="sxs-lookup"><span data-stu-id="3351e-170">conditional and</span></span>|<span data-ttu-id="3351e-171">If (MyMsg.numOrders > 10) && (MyMsg.numOrders < 100)</span><span class="sxs-lookup"><span data-stu-id="3351e-171">If (MyMsg.numOrders > 10) && (MyMsg.numOrders < 100)</span></span>|  
|<span data-ttu-id="3351e-172">&#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="3351e-172">&#124;&#124;</span></span>|<span data-ttu-id="3351e-173">條件式 or</span><span class="sxs-lookup"><span data-stu-id="3351e-173">conditional or</span></span>|<span data-ttu-id="3351e-174">如果 (MyMsg.numOrders < 10) &#124; &#124;(MyMsg.numOrders > 100)</span><span class="sxs-lookup"><span data-stu-id="3351e-174">If (MyMsg.numOrders < 10) &#124;&#124; (MyMsg.numOrders > 100)</span></span>|  
|//|<span data-ttu-id="3351e-175">註解</span><span class="sxs-lookup"><span data-stu-id="3351e-175">commenting</span></span>|<span data-ttu-id="3351e-176">//這是註解</span><span class="sxs-lookup"><span data-stu-id="3351e-176">//This is the comment</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="3351e-177">規則的差異一般運算式和篩選運算式會搭配**接收**圖形。</span><span class="sxs-lookup"><span data-stu-id="3351e-177">The rules differ between general expressions and filter expressions that are used with the **Receive** shape.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3351e-178">請參閱</span><span class="sxs-lookup"><span data-stu-id="3351e-178">See Also</span></span>  
 [<span data-ttu-id="3351e-179">搭配使用篩選與接收訊息圖形</span><span class="sxs-lookup"><span data-stu-id="3351e-179">Using Filters With the Receive Message Shape</span></span>](../core/using-filters-with-the-receive-message-shape.md)