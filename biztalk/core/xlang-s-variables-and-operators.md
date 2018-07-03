---
title: Xlang-s 變數和運算子 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 02512789-2cb9-4ba9-aa78-e59b248e6b24
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f47ee6f69c1a69d0686bdb75b5dcaffc4a7c60a4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023844"
---
# <a name="xlang-s-variables-and-operators"></a><span data-ttu-id="371a1-102">Xlang-s 變數和運算子</span><span class="sxs-lookup"><span data-stu-id="371a1-102">XLANG-s Variables and Operators</span></span>
<span data-ttu-id="371a1-103">本節討論 XLANG/s 語言中使用的變數和運算子。</span><span class="sxs-lookup"><span data-stu-id="371a1-103">This section discusses the variables and operators used in the XLANG/s language.</span></span>  
  
## <a name="xlangs-variables"></a><span data-ttu-id="371a1-104">XLANG/s 變數</span><span class="sxs-lookup"><span data-stu-id="371a1-104">XLANG/s Variables</span></span>  
 <span data-ttu-id="371a1-105">變數代表儲存位置。</span><span class="sxs-lookup"><span data-stu-id="371a1-105">Variables represent storage locations.</span></span> <span data-ttu-id="371a1-106">每個變數都具有型別，決定該變數可以儲存什麼樣的值。</span><span class="sxs-lookup"><span data-stu-id="371a1-106">Every variable has a type that determines what values can be stored in that variable.</span></span> <span data-ttu-id="371a1-107">XLANG/s 屬於型別安全的語言，其編譯器保證變數中儲存的值一定會有適當的型別。</span><span class="sxs-lookup"><span data-stu-id="371a1-107">XLANG/s is type-safe, and its compiler guarantees that values stored in variables are always of the appropriate type.</span></span> <span data-ttu-id="371a1-108">XLANG/s 支援下列變數型別：</span><span class="sxs-lookup"><span data-stu-id="371a1-108">XLANG/s supports the following variable types:</span></span>  
  
- <span data-ttu-id="371a1-109">訊息</span><span class="sxs-lookup"><span data-stu-id="371a1-109">Messages</span></span>  
  
- <span data-ttu-id="371a1-110">相互關聯集合</span><span class="sxs-lookup"><span data-stu-id="371a1-110">Correlation sets</span></span>  
  
- <span data-ttu-id="371a1-111">服務連結</span><span class="sxs-lookup"><span data-stu-id="371a1-111">Service links</span></span>  
  
- <span data-ttu-id="371a1-112">連接埠</span><span class="sxs-lookup"><span data-stu-id="371a1-112">Ports</span></span>  
  
- <span data-ttu-id="371a1-113">辨別內建實值型別：**布林**，**位元組**， **Char**， **Decimal**， **Double**， **Int16**， **Int32**， **Int64**， **SByte**，**單一**，**字串**，**UInt16**， **UInt32**，和**UInt64**</span><span class="sxs-lookup"><span data-stu-id="371a1-113">Distinguished built-in value types: **Boolean**, **Byte**, **Char**, **Decimal**, **Double**, **Int16**, **Int32**, **Int64**, **SByte**, **Single**, **String**, **UInt16**, **UInt32**, and **UInt64**</span></span>  
  
- <span data-ttu-id="371a1-114">物件</span><span class="sxs-lookup"><span data-stu-id="371a1-114">Objects</span></span>  
  
- <span data-ttu-id="371a1-115">列舉型別</span><span class="sxs-lookup"><span data-stu-id="371a1-115">Enumeration types</span></span>  
  
  <span data-ttu-id="371a1-116">XLANG/s 為上述每一個型別提供初始化語意。</span><span class="sxs-lookup"><span data-stu-id="371a1-116">XLANG/s provides initialization semantics for each of the preceding types.</span></span> <span data-ttu-id="371a1-117">這類初始化可以視為對該型別變數的指派。</span><span class="sxs-lookup"><span data-stu-id="371a1-117">Such initialization can be viewed as an assignment to a variable of that type.</span></span> <span data-ttu-id="371a1-118">在 XLANG/s 中，必須明確指派變數，才能取得或使用其值。</span><span class="sxs-lookup"><span data-stu-id="371a1-118">In XLANG/s, a variable must be definitely assigned before its value can be obtained or used.</span></span>  
  
## <a name="xlangs-operators"></a><span data-ttu-id="371a1-119">XLANG/s 運算子</span><span class="sxs-lookup"><span data-stu-id="371a1-119">XLANG/s Operators</span></span>  
 <span data-ttu-id="371a1-120">XLANG/s 支援下列運算子。</span><span class="sxs-lookup"><span data-stu-id="371a1-120">XLANG/s supports the following operators.</span></span> <span data-ttu-id="371a1-121">這些運算子幾乎完全符合 C# 中對應的運算子的功能。</span><span class="sxs-lookup"><span data-stu-id="371a1-121">They adhere closely to the functionality of the corresponding operators in C#.</span></span>  
  
|<span data-ttu-id="371a1-122">運算子</span><span class="sxs-lookup"><span data-stu-id="371a1-122">Operator</span></span>|<span data-ttu-id="371a1-123">描述</span><span class="sxs-lookup"><span data-stu-id="371a1-123">Description</span></span>|<span data-ttu-id="371a1-124">範例</span><span class="sxs-lookup"><span data-stu-id="371a1-124">Example</span></span>|  
|--------------|-----------------|-------------|  
|<span data-ttu-id="371a1-125">已選取</span><span class="sxs-lookup"><span data-stu-id="371a1-125">checked</span></span>|<span data-ttu-id="371a1-126">在算術溢位時引發錯誤</span><span class="sxs-lookup"><span data-stu-id="371a1-126">Raises error on arithmetic overflow</span></span>|<span data-ttu-id="371a1-127">checked(x = y \* 1000)</span><span class="sxs-lookup"><span data-stu-id="371a1-127">checked(x = y \* 1000)</span></span>|  
|<span data-ttu-id="371a1-128">取消選取</span><span class="sxs-lookup"><span data-stu-id="371a1-128">unchecked</span></span>|<span data-ttu-id="371a1-129">忽略算術溢位</span><span class="sxs-lookup"><span data-stu-id="371a1-129">Ignores arithmetic overflow</span></span>|<span data-ttu-id="371a1-130">unchecked(x = y \* 1000)</span><span class="sxs-lookup"><span data-stu-id="371a1-130">unchecked(x = y \* 1000)</span></span>|  
|<span data-ttu-id="371a1-131">new</span><span class="sxs-lookup"><span data-stu-id="371a1-131">new</span></span>|<span data-ttu-id="371a1-132">建立類別的執行個體</span><span class="sxs-lookup"><span data-stu-id="371a1-132">Creates an instance of a class</span></span>|<span data-ttu-id="371a1-133">myObject = new MyClass;</span><span class="sxs-lookup"><span data-stu-id="371a1-133">myObject = new MyClass;</span></span>|  
|<span data-ttu-id="371a1-134">typeof</span><span class="sxs-lookup"><span data-stu-id="371a1-134">typeof</span></span>|<span data-ttu-id="371a1-135">擷取型別</span><span class="sxs-lookup"><span data-stu-id="371a1-135">Retrieves a type</span></span>|<span data-ttu-id="371a1-136">myMapType = typeof(myMap)</span><span class="sxs-lookup"><span data-stu-id="371a1-136">myMapType = typeof(myMap)</span></span>|  
|<span data-ttu-id="371a1-137">succeeded</span><span class="sxs-lookup"><span data-stu-id="371a1-137">succeeded</span></span>|<span data-ttu-id="371a1-138">測試交易式範圍或協調流程是否順利完成</span><span class="sxs-lookup"><span data-stu-id="371a1-138">Tests for successful completion of transactional scope or orchestration</span></span>|<span data-ttu-id="371a1-139">成功 (\<的子交易的目前範圍或服務的交易識別碼\>)</span><span class="sxs-lookup"><span data-stu-id="371a1-139">succeeded(\<transaction ID for child transaction of current scope or service\>)</span></span>|  
|<span data-ttu-id="371a1-140">exists</span><span class="sxs-lookup"><span data-stu-id="371a1-140">exists</span></span>|<span data-ttu-id="371a1-141">測試訊息內容屬性是否存在</span><span class="sxs-lookup"><span data-stu-id="371a1-141">Tests for the existence of a message context property</span></span>|<span data-ttu-id="371a1-142">BTS.RetryCount exists Message_In</span><span class="sxs-lookup"><span data-stu-id="371a1-142">BTS.RetryCount exists Message_In</span></span>|  
|+|<span data-ttu-id="371a1-143">一元加號運算子</span><span class="sxs-lookup"><span data-stu-id="371a1-143">Unary plus</span></span>|<span data-ttu-id="371a1-144">+(int x)</span><span class="sxs-lookup"><span data-stu-id="371a1-144">+(int x)</span></span>|  
|-|<span data-ttu-id="371a1-145">一元減號運算子</span><span class="sxs-lookup"><span data-stu-id="371a1-145">Unary minus</span></span>|<span data-ttu-id="371a1-146">-(int x)</span><span class="sxs-lookup"><span data-stu-id="371a1-146">-(int x)</span></span>|  
|<span data-ttu-id="371a1-147">!</span><span class="sxs-lookup"><span data-stu-id="371a1-147">!</span></span>|<span data-ttu-id="371a1-148">邏輯否定</span><span class="sxs-lookup"><span data-stu-id="371a1-148">Logical negation</span></span>|<span data-ttu-id="371a1-149">!myBool</span><span class="sxs-lookup"><span data-stu-id="371a1-149">!myBool</span></span>|  
|~|<span data-ttu-id="371a1-150">位元補數</span><span class="sxs-lookup"><span data-stu-id="371a1-150">Bitwise complement</span></span>|<span data-ttu-id="371a1-151">x = ~y</span><span class="sxs-lookup"><span data-stu-id="371a1-151">x = ~y</span></span>|  
|<span data-ttu-id="371a1-152">()</span><span class="sxs-lookup"><span data-stu-id="371a1-152">()</span></span>|<span data-ttu-id="371a1-153">轉換</span><span class="sxs-lookup"><span data-stu-id="371a1-153">Cast</span></span>|<span data-ttu-id="371a1-154">(bool) myInt</span><span class="sxs-lookup"><span data-stu-id="371a1-154">(bool) myInt</span></span>|  
|*|<span data-ttu-id="371a1-155">乘</span><span class="sxs-lookup"><span data-stu-id="371a1-155">Times</span></span>|<span data-ttu-id="371a1-156">Weight = MyMsg.numOrders \* 20</span><span class="sxs-lookup"><span data-stu-id="371a1-156">Weight = MyMsg.numOrders \* 20</span></span>|  
|/|<span data-ttu-id="371a1-157">除</span><span class="sxs-lookup"><span data-stu-id="371a1-157">Divided by</span></span>|<span data-ttu-id="371a1-158">x / y</span><span class="sxs-lookup"><span data-stu-id="371a1-158">x / y</span></span>|  
|+|<span data-ttu-id="371a1-159">加</span><span class="sxs-lookup"><span data-stu-id="371a1-159">Plus</span></span>|<span data-ttu-id="371a1-160">x + y</span><span class="sxs-lookup"><span data-stu-id="371a1-160">x + y</span></span>|  
|-|<span data-ttu-id="371a1-161">減</span><span class="sxs-lookup"><span data-stu-id="371a1-161">Minus</span></span>|<span data-ttu-id="371a1-162">x - y</span><span class="sxs-lookup"><span data-stu-id="371a1-162">x - y</span></span>|  
|<<|<span data-ttu-id="371a1-163">左移</span><span class="sxs-lookup"><span data-stu-id="371a1-163">Shift left</span></span>|<span data-ttu-id="371a1-164">x << 2</span><span class="sxs-lookup"><span data-stu-id="371a1-164">x << 2</span></span>|  
|>>|<span data-ttu-id="371a1-165">右移</span><span class="sxs-lookup"><span data-stu-id="371a1-165">Shift right</span></span>|<span data-ttu-id="371a1-166">x >> 2</span><span class="sxs-lookup"><span data-stu-id="371a1-166">x >> 2</span></span>|  
|<|<span data-ttu-id="371a1-167">小於</span><span class="sxs-lookup"><span data-stu-id="371a1-167">Less than</span></span>|<span data-ttu-id="371a1-168">If (MyMsg.numOrders < 10)...</span><span class="sxs-lookup"><span data-stu-id="371a1-168">If (MyMsg.numOrders < 10)...</span></span>|  
|>|<span data-ttu-id="371a1-169">大於</span><span class="sxs-lookup"><span data-stu-id="371a1-169">Greater than</span></span>|<span data-ttu-id="371a1-170">如果 (MyMsg.numOrders > 10)...</span><span class="sxs-lookup"><span data-stu-id="371a1-170">If (MyMsg.numOrders > 10)...</span></span>|  
|<=|<span data-ttu-id="371a1-171">小於或等於</span><span class="sxs-lookup"><span data-stu-id="371a1-171">Less than or equal to</span></span>|<span data-ttu-id="371a1-172">If (MyMsg.numOrders <= 10)...</span><span class="sxs-lookup"><span data-stu-id="371a1-172">If (MyMsg.numOrders <= 10)...</span></span>|  
|>=|<span data-ttu-id="371a1-173">大於或等於</span><span class="sxs-lookup"><span data-stu-id="371a1-173">Greater than or equal to</span></span>|<span data-ttu-id="371a1-174">如果 (MyMsg.numOrders > = 10)...</span><span class="sxs-lookup"><span data-stu-id="371a1-174">If (MyMsg.numOrders >= 10)...</span></span>|  
|==|<span data-ttu-id="371a1-175">等於</span><span class="sxs-lookup"><span data-stu-id="371a1-175">Equal to</span></span>|<span data-ttu-id="371a1-176">If (MyMsg.numOrders == 10)...</span><span class="sxs-lookup"><span data-stu-id="371a1-176">If (MyMsg.numOrders == 10)...</span></span>|  
|<span data-ttu-id="371a1-177">!=</span><span class="sxs-lookup"><span data-stu-id="371a1-177">!=</span></span>|<span data-ttu-id="371a1-178">不等於</span><span class="sxs-lookup"><span data-stu-id="371a1-178">Not equal to</span></span>|<span data-ttu-id="371a1-179">If (MyMsg.numOrders != 10)...</span><span class="sxs-lookup"><span data-stu-id="371a1-179">If (MyMsg.numOrders != 10)...</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="371a1-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="371a1-180">See Also</span></span>  
 <span data-ttu-id="371a1-181">[Xlang-s 資料類型](../core/xlang-s-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="371a1-181">[XLANG-s Data Types](../core/xlang-s-data-types.md) </span></span>  
 <span data-ttu-id="371a1-182">[Xlang-s 陳述式](../core/xlang-s-statements.md) </span><span class="sxs-lookup"><span data-stu-id="371a1-182">[XLANG-s Statements](../core/xlang-s-statements.md) </span></span>  
 <span data-ttu-id="371a1-183">[Xlang-s 運算式](../core/xlang-s-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="371a1-183">[XLANG-s Expressions](../core/xlang-s-expressions.md) </span></span>  
 <span data-ttu-id="371a1-184">[Xlang-s 保留字](../core/xlang-s-reserved-words.md) </span><span class="sxs-lookup"><span data-stu-id="371a1-184">[XLANG-s Reserved Words](../core/xlang-s-reserved-words.md) </span></span>  
 [<span data-ttu-id="371a1-185">XLANG-s 至 BPEL4WS 類型轉換</span><span class="sxs-lookup"><span data-stu-id="371a1-185">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)