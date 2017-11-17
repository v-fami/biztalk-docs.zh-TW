---
title: "在運算式中使用運算子 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, operators
- XLANG/s, operators
- orchestrations, XLANG/s
ms.assetid: f0948ce2-c508-48aa-af79-d207f577b22f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 155aad11ecddd021b8e16892b5a5294087fedd4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-operators-in-expressions"></a><span data-ttu-id="f790f-102">在運算式中使用運算子</span><span class="sxs-lookup"><span data-stu-id="f790f-102">Using Operators in Expressions</span></span>
<span data-ttu-id="f790f-103">在協調流程運算式中也可以使用下列的 XLANG/s 運算子。</span><span class="sxs-lookup"><span data-stu-id="f790f-103">The following XLANG/s operators are available for use in orchestration expressions.</span></span> <span data-ttu-id="f790f-104">這些運算子幾乎完全符合 C# 中對應的運算子的功能。</span><span class="sxs-lookup"><span data-stu-id="f790f-104">They adhere closely to the functionality of the corresponding operators in C#.</span></span>  
  
|<span data-ttu-id="f790f-105">運算子</span><span class="sxs-lookup"><span data-stu-id="f790f-105">Operator</span></span>|<span data-ttu-id="f790f-106">Description</span><span class="sxs-lookup"><span data-stu-id="f790f-106">Description</span></span>|<span data-ttu-id="f790f-107">範例</span><span class="sxs-lookup"><span data-stu-id="f790f-107">Example</span></span>|  
|--------------|-----------------|-------------|  
|<span data-ttu-id="f790f-108">checked()</span><span class="sxs-lookup"><span data-stu-id="f790f-108">checked()</span></span>|<span data-ttu-id="f790f-109">在算術溢位時引發錯誤</span><span class="sxs-lookup"><span data-stu-id="f790f-109">raise error on arithmetic overflow</span></span>|<span data-ttu-id="f790f-110">checked(x = y * 1000)</span><span class="sxs-lookup"><span data-stu-id="f790f-110">checked(x = y * 1000)</span></span>|  
|<span data-ttu-id="f790f-111">unchecked()</span><span class="sxs-lookup"><span data-stu-id="f790f-111">unchecked()</span></span>|<span data-ttu-id="f790f-112">忽略算術溢位</span><span class="sxs-lookup"><span data-stu-id="f790f-112">ignore arithmetic overflow</span></span>|<span data-ttu-id="f790f-113">unchecked(x = y * 1000)</span><span class="sxs-lookup"><span data-stu-id="f790f-113">unchecked(x = y * 1000)</span></span>|  
|<span data-ttu-id="f790f-114">new</span><span class="sxs-lookup"><span data-stu-id="f790f-114">new</span></span>|<span data-ttu-id="f790f-115">建立類別的執行個體</span><span class="sxs-lookup"><span data-stu-id="f790f-115">create an instance of a class</span></span>|<span data-ttu-id="f790f-116">myObject = new MyClass;</span><span class="sxs-lookup"><span data-stu-id="f790f-116">myObject = new MyClass;</span></span>|  
|<span data-ttu-id="f790f-117">typeof</span><span class="sxs-lookup"><span data-stu-id="f790f-117">typeof</span></span>|<span data-ttu-id="f790f-118">類型擷取</span><span class="sxs-lookup"><span data-stu-id="f790f-118">Type retrieval</span></span>|<span data-ttu-id="f790f-119">myMapType = typeof(myMap)</span><span class="sxs-lookup"><span data-stu-id="f790f-119">myMapType = typeof(myMap)</span></span>|  
|<span data-ttu-id="f790f-120">succeeded()</span><span class="sxs-lookup"><span data-stu-id="f790f-120">succeeded()</span></span>|<span data-ttu-id="f790f-121">測試交易式範圍或協調流程是否順利完成</span><span class="sxs-lookup"><span data-stu-id="f790f-121">test for successful completion of transactional scope or orchestration</span></span>|<span data-ttu-id="f790f-122">成功 (\<目前範圍或服務的子交易的交易識別碼 >)</span><span class="sxs-lookup"><span data-stu-id="f790f-122">succeeded(\<transaction ID for child transaction of current scope or service>)</span></span>|  
|<span data-ttu-id="f790f-123">exists</span><span class="sxs-lookup"><span data-stu-id="f790f-123">exists</span></span>|<span data-ttu-id="f790f-124">測試訊息內容屬性是否存在</span><span class="sxs-lookup"><span data-stu-id="f790f-124">test for the existence of a message context property</span></span>|<span data-ttu-id="f790f-125">BTS.RetryCount exists Message_In</span><span class="sxs-lookup"><span data-stu-id="f790f-125">BTS.RetryCount exists Message_In</span></span>|  
|+|<span data-ttu-id="f790f-126">一元加號</span><span class="sxs-lookup"><span data-stu-id="f790f-126">unary plus</span></span>|<span data-ttu-id="f790f-127">+(int x)</span><span class="sxs-lookup"><span data-stu-id="f790f-127">+(int x)</span></span>|  
|-|<span data-ttu-id="f790f-128">一元減號</span><span class="sxs-lookup"><span data-stu-id="f790f-128">unary minus</span></span>|<span data-ttu-id="f790f-129">-(int x)</span><span class="sxs-lookup"><span data-stu-id="f790f-129">-(int x)</span></span>|  
|<span data-ttu-id="f790f-130">!</span><span class="sxs-lookup"><span data-stu-id="f790f-130">!</span></span>|<span data-ttu-id="f790f-131">邏輯否定</span><span class="sxs-lookup"><span data-stu-id="f790f-131">logical negation</span></span>|<span data-ttu-id="f790f-132">!myBool</span><span class="sxs-lookup"><span data-stu-id="f790f-132">!myBool</span></span>|  
|~|<span data-ttu-id="f790f-133">位元補數</span><span class="sxs-lookup"><span data-stu-id="f790f-133">bitwise complement</span></span>|<span data-ttu-id="f790f-134">x = ~y</span><span class="sxs-lookup"><span data-stu-id="f790f-134">x = ~y</span></span>|  
|<span data-ttu-id="f790f-135">()</span><span class="sxs-lookup"><span data-stu-id="f790f-135">()</span></span>|<span data-ttu-id="f790f-136">強制轉型</span><span class="sxs-lookup"><span data-stu-id="f790f-136">cast</span></span>|<span data-ttu-id="f790f-137">(bool) myInt</span><span class="sxs-lookup"><span data-stu-id="f790f-137">(bool) myInt</span></span>|  
|*|<span data-ttu-id="f790f-138">times</span><span class="sxs-lookup"><span data-stu-id="f790f-138">times</span></span>|<span data-ttu-id="f790f-139">Weight = MyMsg.numOrders * 20</span><span class="sxs-lookup"><span data-stu-id="f790f-139">Weight = MyMsg.numOrders * 20</span></span>|  
|/|<span data-ttu-id="f790f-140">除以</span><span class="sxs-lookup"><span data-stu-id="f790f-140">divided by</span></span>|<span data-ttu-id="f790f-141">x / y</span><span class="sxs-lookup"><span data-stu-id="f790f-141">x / y</span></span>|  
|+|<span data-ttu-id="f790f-142">加</span><span class="sxs-lookup"><span data-stu-id="f790f-142">plus</span></span>|<span data-ttu-id="f790f-143">x + y</span><span class="sxs-lookup"><span data-stu-id="f790f-143">x + y</span></span>|  
|-|<span data-ttu-id="f790f-144">減</span><span class="sxs-lookup"><span data-stu-id="f790f-144">minus</span></span>|<span data-ttu-id="f790f-145">x - y</span><span class="sxs-lookup"><span data-stu-id="f790f-145">x - y</span></span>|  
|<<|<span data-ttu-id="f790f-146">左移</span><span class="sxs-lookup"><span data-stu-id="f790f-146">shift left</span></span>|<span data-ttu-id="f790f-147">x <\< 2</span><span class="sxs-lookup"><span data-stu-id="f790f-147">x <\< 2</span></span>|  
|>>|<span data-ttu-id="f790f-148">右移</span><span class="sxs-lookup"><span data-stu-id="f790f-148">shift right</span></span>|<span data-ttu-id="f790f-149">x >> 2</span><span class="sxs-lookup"><span data-stu-id="f790f-149">x >> 2</span></span>|  
|<|<span data-ttu-id="f790f-150">小於</span><span class="sxs-lookup"><span data-stu-id="f790f-150">less than</span></span>|<span data-ttu-id="f790f-151">如果 (MyMsg.numOrders \< 10)...</span><span class="sxs-lookup"><span data-stu-id="f790f-151">If (MyMsg.numOrders \< 10)...</span></span>|  
|>|<span data-ttu-id="f790f-152">大於</span><span class="sxs-lookup"><span data-stu-id="f790f-152">greater than</span></span>|<span data-ttu-id="f790f-153">如果 (MyMsg.numOrders > 10)...</span><span class="sxs-lookup"><span data-stu-id="f790f-153">If (MyMsg.numOrders > 10)...</span></span>|  
|<=|<span data-ttu-id="f790f-154">小於或等於</span><span class="sxs-lookup"><span data-stu-id="f790f-154">less than or equal to</span></span>|<span data-ttu-id="f790f-155">如果 (MyMsg.numOrders \<= 10)...</span><span class="sxs-lookup"><span data-stu-id="f790f-155">If (MyMsg.numOrders \<= 10)...</span></span>|  
|>=|<span data-ttu-id="f790f-156">大於或等於</span><span class="sxs-lookup"><span data-stu-id="f790f-156">greater than or equal to</span></span>|<span data-ttu-id="f790f-157">如果 (MyMsg.numOrders > = 10)...</span><span class="sxs-lookup"><span data-stu-id="f790f-157">If (MyMsg.numOrders >= 10)...</span></span>|  
|==|<span data-ttu-id="f790f-158">等於</span><span class="sxs-lookup"><span data-stu-id="f790f-158">equal to</span></span>|<span data-ttu-id="f790f-159">If (MyMsg.numOrders == 10)...</span><span class="sxs-lookup"><span data-stu-id="f790f-159">If (MyMsg.numOrders == 10)...</span></span>|  
|<span data-ttu-id="f790f-160">!=</span><span class="sxs-lookup"><span data-stu-id="f790f-160">!=</span></span>|<span data-ttu-id="f790f-161">不等於</span><span class="sxs-lookup"><span data-stu-id="f790f-161">not equal to</span></span>|<span data-ttu-id="f790f-162">If (MyMsg.numOrders != 10)...</span><span class="sxs-lookup"><span data-stu-id="f790f-162">If (MyMsg.numOrders != 10)...</span></span>|  
|&|<span data-ttu-id="f790f-163">和</span><span class="sxs-lookup"><span data-stu-id="f790f-163">and</span></span>|<span data-ttu-id="f790f-164">If (myByte & 255)...</span><span class="sxs-lookup"><span data-stu-id="f790f-164">If (myByte & 255)...</span></span>|  
|^|<span data-ttu-id="f790f-165">排除式 or</span><span class="sxs-lookup"><span data-stu-id="f790f-165">exclusive or</span></span>|<span data-ttu-id="f790f-166">If (myByte ^ 1)...</span><span class="sxs-lookup"><span data-stu-id="f790f-166">If (myByte ^ 1)...</span></span>|  
|<span data-ttu-id="f790f-167">&#124;</span><span class="sxs-lookup"><span data-stu-id="f790f-167">&#124;</span></span>|<span data-ttu-id="f790f-168">或</span><span class="sxs-lookup"><span data-stu-id="f790f-168">or</span></span>|<span data-ttu-id="f790f-169">如果 (myByte &#124; 1)...</span><span class="sxs-lookup"><span data-stu-id="f790f-169">If (myByte &#124; 1)...</span></span>|  
|&&|<span data-ttu-id="f790f-170">條件式 and</span><span class="sxs-lookup"><span data-stu-id="f790f-170">conditional and</span></span>|<span data-ttu-id="f790f-171">If (MyMsg.numOrders > 10) && (MyMsg.numOrders < 100)</span><span class="sxs-lookup"><span data-stu-id="f790f-171">If (MyMsg.numOrders > 10) && (MyMsg.numOrders < 100)</span></span>|  
|<span data-ttu-id="f790f-172">&#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="f790f-172">&#124;&#124;</span></span>|<span data-ttu-id="f790f-173">條件式 or</span><span class="sxs-lookup"><span data-stu-id="f790f-173">conditional or</span></span>|<span data-ttu-id="f790f-174">如果 (MyMsg.numOrders \< 10) &#124; &#124;(MyMsg.numOrders > 100)</span><span class="sxs-lookup"><span data-stu-id="f790f-174">If (MyMsg.numOrders \< 10) &#124;&#124; (MyMsg.numOrders > 100)</span></span>|  
|//|<span data-ttu-id="f790f-175">註解</span><span class="sxs-lookup"><span data-stu-id="f790f-175">commenting</span></span>|<span data-ttu-id="f790f-176">//這是註解</span><span class="sxs-lookup"><span data-stu-id="f790f-176">//This is the comment</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f790f-177">規則的差異一般運算式和篩選運算式會搭配**接收**圖形。</span><span class="sxs-lookup"><span data-stu-id="f790f-177">The rules differ between general expressions and filter expressions that are used with the **Receive** shape.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f790f-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f790f-178">See Also</span></span>  
 [<span data-ttu-id="f790f-179">使用篩選器與接收訊息 」 圖形</span><span class="sxs-lookup"><span data-stu-id="f790f-179">Using Filters With the Receive Message Shape</span></span>](../core/using-filters-with-the-receive-message-shape.md)