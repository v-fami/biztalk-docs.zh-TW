---
title: "XLANG 的變數和運算子 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02512789-2cb9-4ba9-aa78-e59b248e6b24
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c1773b7af3ec029026ee884e6c1161e27a3c330
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="xlang-s-variables-and-operators"></a><span data-ttu-id="35240-102">XLANG 的變數和運算子</span><span class="sxs-lookup"><span data-stu-id="35240-102">XLANG-s Variables and Operators</span></span>
<span data-ttu-id="35240-103">本節討論 XLANG/s 語言中使用的變數和運算子。</span><span class="sxs-lookup"><span data-stu-id="35240-103">This section discusses the variables and operators used in the XLANG/s language.</span></span>  
  
## <a name="xlangs-variables"></a><span data-ttu-id="35240-104">XLANG/s 變數</span><span class="sxs-lookup"><span data-stu-id="35240-104">XLANG/s Variables</span></span>  
 <span data-ttu-id="35240-105">變數代表儲存位置。</span><span class="sxs-lookup"><span data-stu-id="35240-105">Variables represent storage locations.</span></span> <span data-ttu-id="35240-106">每個變數都具有型別，決定該變數可以儲存什麼樣的值。</span><span class="sxs-lookup"><span data-stu-id="35240-106">Every variable has a type that determines what values can be stored in that variable.</span></span> <span data-ttu-id="35240-107">XLANG/s 屬於型別安全的語言，其編譯器保證變數中儲存的值一定會有適當的型別。</span><span class="sxs-lookup"><span data-stu-id="35240-107">XLANG/s is type-safe, and its compiler guarantees that values stored in variables are always of the appropriate type.</span></span> <span data-ttu-id="35240-108">XLANG/s 支援下列變數型別：</span><span class="sxs-lookup"><span data-stu-id="35240-108">XLANG/s supports the following variable types:</span></span>  
  
-   <span data-ttu-id="35240-109">訊息</span><span class="sxs-lookup"><span data-stu-id="35240-109">Messages</span></span>  
  
-   <span data-ttu-id="35240-110">相互關聯集合</span><span class="sxs-lookup"><span data-stu-id="35240-110">Correlation sets</span></span>  
  
-   <span data-ttu-id="35240-111">服務連結</span><span class="sxs-lookup"><span data-stu-id="35240-111">Service links</span></span>  
  
-   <span data-ttu-id="35240-112">連接埠</span><span class="sxs-lookup"><span data-stu-id="35240-112">Ports</span></span>  
  
-   <span data-ttu-id="35240-113">辨別內建實值型別：**布林**，**位元組**， **Char**，**十進位**， **Double**， **Int16**， **Int32**， **Int64**， **SByte**，**單一**，**字串**，**UInt16**， **UInt32**，和**UInt64**</span><span class="sxs-lookup"><span data-stu-id="35240-113">Distinguished built-in value types: **Boolean**, **Byte**, **Char**, **Decimal**, **Double**, **Int16**, **Int32**, **Int64**, **SByte**, **Single**, **String**, **UInt16**, **UInt32**, and **UInt64**</span></span>  
  
-   <span data-ttu-id="35240-114">物件</span><span class="sxs-lookup"><span data-stu-id="35240-114">Objects</span></span>  
  
-   <span data-ttu-id="35240-115">列舉型別</span><span class="sxs-lookup"><span data-stu-id="35240-115">Enumeration types</span></span>  
  
 <span data-ttu-id="35240-116">XLANG/s 為上述每一個型別提供初始化語意。</span><span class="sxs-lookup"><span data-stu-id="35240-116">XLANG/s provides initialization semantics for each of the preceding types.</span></span> <span data-ttu-id="35240-117">這類初始化可以視為對該型別變數的指派。</span><span class="sxs-lookup"><span data-stu-id="35240-117">Such initialization can be viewed as an assignment to a variable of that type.</span></span> <span data-ttu-id="35240-118">在 XLANG/s 中，必須明確指派變數，才能取得或使用其值。</span><span class="sxs-lookup"><span data-stu-id="35240-118">In XLANG/s, a variable must be definitely assigned before its value can be obtained or used.</span></span>  
  
## <a name="xlangs-operators"></a><span data-ttu-id="35240-119">XLANG/s 運算子</span><span class="sxs-lookup"><span data-stu-id="35240-119">XLANG/s Operators</span></span>  
 <span data-ttu-id="35240-120">XLANG/s 支援下列運算子。</span><span class="sxs-lookup"><span data-stu-id="35240-120">XLANG/s supports the following operators.</span></span> <span data-ttu-id="35240-121">這些運算子幾乎完全符合 C# 中對應的運算子的功能。</span><span class="sxs-lookup"><span data-stu-id="35240-121">They adhere closely to the functionality of the corresponding operators in C#.</span></span>  
  
|<span data-ttu-id="35240-122">運算子</span><span class="sxs-lookup"><span data-stu-id="35240-122">Operator</span></span>|<span data-ttu-id="35240-123">Description</span><span class="sxs-lookup"><span data-stu-id="35240-123">Description</span></span>|<span data-ttu-id="35240-124">範例</span><span class="sxs-lookup"><span data-stu-id="35240-124">Example</span></span>|  
|--------------|-----------------|-------------|  
|<span data-ttu-id="35240-125">已選取</span><span class="sxs-lookup"><span data-stu-id="35240-125">checked</span></span>|<span data-ttu-id="35240-126">在算術溢位時引發錯誤</span><span class="sxs-lookup"><span data-stu-id="35240-126">Raises error on arithmetic overflow</span></span>|<span data-ttu-id="35240-127">checked(x = y * 1000)</span><span class="sxs-lookup"><span data-stu-id="35240-127">checked(x = y * 1000)</span></span>|  
|<span data-ttu-id="35240-128">取消選取</span><span class="sxs-lookup"><span data-stu-id="35240-128">unchecked</span></span>|<span data-ttu-id="35240-129">忽略算術溢位</span><span class="sxs-lookup"><span data-stu-id="35240-129">Ignores arithmetic overflow</span></span>|<span data-ttu-id="35240-130">unchecked(x = y * 1000)</span><span class="sxs-lookup"><span data-stu-id="35240-130">unchecked(x = y * 1000)</span></span>|  
|<span data-ttu-id="35240-131">new</span><span class="sxs-lookup"><span data-stu-id="35240-131">new</span></span>|<span data-ttu-id="35240-132">建立類別的執行個體</span><span class="sxs-lookup"><span data-stu-id="35240-132">Creates an instance of a class</span></span>|<span data-ttu-id="35240-133">myObject = new MyClass;</span><span class="sxs-lookup"><span data-stu-id="35240-133">myObject = new MyClass;</span></span>|  
|<span data-ttu-id="35240-134">typeof</span><span class="sxs-lookup"><span data-stu-id="35240-134">typeof</span></span>|<span data-ttu-id="35240-135">擷取型別</span><span class="sxs-lookup"><span data-stu-id="35240-135">Retrieves a type</span></span>|<span data-ttu-id="35240-136">myMapType = typeof(myMap)</span><span class="sxs-lookup"><span data-stu-id="35240-136">myMapType = typeof(myMap)</span></span>|  
|<span data-ttu-id="35240-137">succeeded</span><span class="sxs-lookup"><span data-stu-id="35240-137">succeeded</span></span>|<span data-ttu-id="35240-138">測試交易式範圍或協調流程是否順利完成</span><span class="sxs-lookup"><span data-stu-id="35240-138">Tests for successful completion of transactional scope or orchestration</span></span>|<span data-ttu-id="35240-139">成功 (\<目前範圍或服務的子交易的交易識別碼\>)</span><span class="sxs-lookup"><span data-stu-id="35240-139">succeeded(\<transaction ID for child transaction of current scope or service\>)</span></span>|  
|<span data-ttu-id="35240-140">exists</span><span class="sxs-lookup"><span data-stu-id="35240-140">exists</span></span>|<span data-ttu-id="35240-141">測試訊息內容屬性是否存在</span><span class="sxs-lookup"><span data-stu-id="35240-141">Tests for the existence of a message context property</span></span>|<span data-ttu-id="35240-142">BTS.RetryCount exists Message_In</span><span class="sxs-lookup"><span data-stu-id="35240-142">BTS.RetryCount exists Message_In</span></span>|  
|+|<span data-ttu-id="35240-143">一元加號運算子</span><span class="sxs-lookup"><span data-stu-id="35240-143">Unary plus</span></span>|<span data-ttu-id="35240-144">+(int x)</span><span class="sxs-lookup"><span data-stu-id="35240-144">+(int x)</span></span>|  
|-|<span data-ttu-id="35240-145">一元減號運算子</span><span class="sxs-lookup"><span data-stu-id="35240-145">Unary minus</span></span>|<span data-ttu-id="35240-146">-(int x)</span><span class="sxs-lookup"><span data-stu-id="35240-146">-(int x)</span></span>|  
|<span data-ttu-id="35240-147">!</span><span class="sxs-lookup"><span data-stu-id="35240-147">!</span></span>|<span data-ttu-id="35240-148">邏輯否定</span><span class="sxs-lookup"><span data-stu-id="35240-148">Logical negation</span></span>|<span data-ttu-id="35240-149">!myBool</span><span class="sxs-lookup"><span data-stu-id="35240-149">!myBool</span></span>|  
|~|<span data-ttu-id="35240-150">位元補數</span><span class="sxs-lookup"><span data-stu-id="35240-150">Bitwise complement</span></span>|<span data-ttu-id="35240-151">x = ~y</span><span class="sxs-lookup"><span data-stu-id="35240-151">x = ~y</span></span>|  
|<span data-ttu-id="35240-152">()</span><span class="sxs-lookup"><span data-stu-id="35240-152">()</span></span>|<span data-ttu-id="35240-153">轉換</span><span class="sxs-lookup"><span data-stu-id="35240-153">Cast</span></span>|<span data-ttu-id="35240-154">(bool) myInt</span><span class="sxs-lookup"><span data-stu-id="35240-154">(bool) myInt</span></span>|  
|*|<span data-ttu-id="35240-155">乘</span><span class="sxs-lookup"><span data-stu-id="35240-155">Times</span></span>|<span data-ttu-id="35240-156">Weight = MyMsg.numOrders * 20</span><span class="sxs-lookup"><span data-stu-id="35240-156">Weight = MyMsg.numOrders * 20</span></span>|  
|/|<span data-ttu-id="35240-157">除</span><span class="sxs-lookup"><span data-stu-id="35240-157">Divided by</span></span>|<span data-ttu-id="35240-158">x / y</span><span class="sxs-lookup"><span data-stu-id="35240-158">x / y</span></span>|  
|+|<span data-ttu-id="35240-159">加</span><span class="sxs-lookup"><span data-stu-id="35240-159">Plus</span></span>|<span data-ttu-id="35240-160">x + y</span><span class="sxs-lookup"><span data-stu-id="35240-160">x + y</span></span>|  
|-|<span data-ttu-id="35240-161">減</span><span class="sxs-lookup"><span data-stu-id="35240-161">Minus</span></span>|<span data-ttu-id="35240-162">x - y</span><span class="sxs-lookup"><span data-stu-id="35240-162">x - y</span></span>|  
|<<|<span data-ttu-id="35240-163">左移</span><span class="sxs-lookup"><span data-stu-id="35240-163">Shift left</span></span>|<span data-ttu-id="35240-164">x << 2</span><span class="sxs-lookup"><span data-stu-id="35240-164">x << 2</span></span>|  
|>>|<span data-ttu-id="35240-165">右移</span><span class="sxs-lookup"><span data-stu-id="35240-165">Shift right</span></span>|<span data-ttu-id="35240-166">x >> 2</span><span class="sxs-lookup"><span data-stu-id="35240-166">x >> 2</span></span>|  
|<|<span data-ttu-id="35240-167">小於</span><span class="sxs-lookup"><span data-stu-id="35240-167">Less than</span></span>|<span data-ttu-id="35240-168">If (MyMsg.numOrders < 10)...</span><span class="sxs-lookup"><span data-stu-id="35240-168">If (MyMsg.numOrders < 10)...</span></span>|  
|>|<span data-ttu-id="35240-169">大於</span><span class="sxs-lookup"><span data-stu-id="35240-169">Greater than</span></span>|<span data-ttu-id="35240-170">如果 (MyMsg.numOrders > 10)...</span><span class="sxs-lookup"><span data-stu-id="35240-170">If (MyMsg.numOrders > 10)...</span></span>|  
|<=|<span data-ttu-id="35240-171">小於或等於</span><span class="sxs-lookup"><span data-stu-id="35240-171">Less than or equal to</span></span>|<span data-ttu-id="35240-172">If (MyMsg.numOrders <= 10)...</span><span class="sxs-lookup"><span data-stu-id="35240-172">If (MyMsg.numOrders <= 10)...</span></span>|  
|>=|<span data-ttu-id="35240-173">大於或等於</span><span class="sxs-lookup"><span data-stu-id="35240-173">Greater than or equal to</span></span>|<span data-ttu-id="35240-174">如果 (MyMsg.numOrders > = 10)...</span><span class="sxs-lookup"><span data-stu-id="35240-174">If (MyMsg.numOrders >= 10)...</span></span>|  
|==|<span data-ttu-id="35240-175">等於</span><span class="sxs-lookup"><span data-stu-id="35240-175">Equal to</span></span>|<span data-ttu-id="35240-176">If (MyMsg.numOrders == 10)...</span><span class="sxs-lookup"><span data-stu-id="35240-176">If (MyMsg.numOrders == 10)...</span></span>|  
|<span data-ttu-id="35240-177">!=</span><span class="sxs-lookup"><span data-stu-id="35240-177">!=</span></span>|<span data-ttu-id="35240-178">不等於</span><span class="sxs-lookup"><span data-stu-id="35240-178">Not equal to</span></span>|<span data-ttu-id="35240-179">If (MyMsg.numOrders != 10)...</span><span class="sxs-lookup"><span data-stu-id="35240-179">If (MyMsg.numOrders != 10)...</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35240-180">請參閱</span><span class="sxs-lookup"><span data-stu-id="35240-180">See Also</span></span>  
 <span data-ttu-id="35240-181">[XLANG 的資料型別](../core/xlang-s-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="35240-181">[XLANG-s Data Types](../core/xlang-s-data-types.md) </span></span>  
 <span data-ttu-id="35240-182">[XLANG s 陳述式](../core/xlang-s-statements.md) </span><span class="sxs-lookup"><span data-stu-id="35240-182">[XLANG-s Statements](../core/xlang-s-statements.md) </span></span>  
 <span data-ttu-id="35240-183">[XLANG 的運算式](../core/xlang-s-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="35240-183">[XLANG-s Expressions](../core/xlang-s-expressions.md) </span></span>  
 <span data-ttu-id="35240-184">[XLANG s 保留字](../core/xlang-s-reserved-words.md) </span><span class="sxs-lookup"><span data-stu-id="35240-184">[XLANG-s Reserved Words](../core/xlang-s-reserved-words.md) </span></span>  
 [<span data-ttu-id="35240-185">XLANG-s 至 BPEL4WS 類型轉換</span><span class="sxs-lookup"><span data-stu-id="35240-185">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)