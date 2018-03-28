---
title: XLANG-s 至 BPEL4WS 型別轉換 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XLANG/s
- XLANG/s, warning
- XLANG/s, BPEL4WS
- XLANG/s, converting
ms.assetid: a35d4dba-9344-43c8-86e6-a373a4452579
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02412b86b8649b73cadb4715793f085682a1de74
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="xlang-s-to-bpel4ws-type-conversions"></a><span data-ttu-id="74de7-102">XLANG-s 至 BPEL4WS 型別轉換</span><span class="sxs-lookup"><span data-stu-id="74de7-102">XLANG-s to BPEL4WS Type Conversions</span></span>
<span data-ttu-id="74de7-103">下表詳述各種 XLANG/s 建構和 BPEL4WS 建構之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="74de7-103">The following tables detail the conversions between various XLANG/s constructs and BPEL4WS constructs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="74de7-104">XPath 1.1 不支援指數或雙精度浮點數格式的數字。</span><span class="sxs-lookup"><span data-stu-id="74de7-104">XPath 1.1 does not support numbers in exponential or double formats.</span></span> <span data-ttu-id="74de7-105">XLANG/s 協調流程中這些格式的常值數值會使用 %f 格式匯出到 BPEL4WS，而可能會喪失一些精確度。</span><span class="sxs-lookup"><span data-stu-id="74de7-105">Literal values in these formats in XLANG/s orchestrations are exported to BPEL4WS using the %f format, and a loss of precision might result.</span></span>  
  
## <a name="literals-if-the-literal-is-part-of-an-expression"></a><span data-ttu-id="74de7-106">常值 (如果此常值是運算式的一部分)</span><span class="sxs-lookup"><span data-stu-id="74de7-106">Literals (if the literal is part of an expression)</span></span>  
  
|<span data-ttu-id="74de7-107">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="74de7-107">XLANG/s</span></span>|<span data-ttu-id="74de7-108">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="74de7-108">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="74de7-109">字串、字元</span><span class="sxs-lookup"><span data-stu-id="74de7-109">String, character</span></span>|<span data-ttu-id="74de7-110">XPath 字串</span><span class="sxs-lookup"><span data-stu-id="74de7-110">XPath string</span></span>|  
|<span data-ttu-id="74de7-111">整數，真實</span><span class="sxs-lookup"><span data-stu-id="74de7-111">Integer, real</span></span>|<span data-ttu-id="74de7-112">XPath 數字</span><span class="sxs-lookup"><span data-stu-id="74de7-112">XPath number</span></span>|  
|<span data-ttu-id="74de7-113">布林值 "true"、"false"</span><span class="sxs-lookup"><span data-stu-id="74de7-113">Boolean "true", "false"</span></span>|<span data-ttu-id="74de7-114">XPath true()、false() 函式</span><span class="sxs-lookup"><span data-stu-id="74de7-114">XPath true(), false() functions</span></span>|  
  
## <a name="literals-standalone-assignment"></a><span data-ttu-id="74de7-115">常值 (獨立指派)</span><span class="sxs-lookup"><span data-stu-id="74de7-115">Literals (standalone assignment)</span></span>  
  
|<span data-ttu-id="74de7-116">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="74de7-116">XLANG/s</span></span>|<span data-ttu-id="74de7-117">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="74de7-117">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="74de7-118">常值常數</span><span class="sxs-lookup"><span data-stu-id="74de7-118">Literal constant</span></span>|<span data-ttu-id="74de7-119">XSD 同等項目</span><span class="sxs-lookup"><span data-stu-id="74de7-119">XSD equivalent</span></span>|  
  
## <a name="variables"></a><span data-ttu-id="74de7-120">變數</span><span class="sxs-lookup"><span data-stu-id="74de7-120">Variables</span></span>  
  
|<span data-ttu-id="74de7-121">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="74de7-121">XLANG/s</span></span>|<span data-ttu-id="74de7-122">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="74de7-122">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="74de7-123">變數參考</span><span class="sxs-lookup"><span data-stu-id="74de7-123">Variable reference</span></span>|<span data-ttu-id="74de7-124">bpws:getContainerData(%varName%,  part, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="74de7-124">bpws:getContainerData(%varName%,  part, %locationPath%)</span></span>|  
|<span data-ttu-id="74de7-125">訊息參考 (.NET 類型)</span><span class="sxs-lookup"><span data-stu-id="74de7-125">Message reference (.NET type)</span></span>|<span data-ttu-id="74de7-126">bpws:getContainerData(%msgName%, part, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="74de7-126">bpws:getContainerData(%msgName%, part, %locationPath%)</span></span>|  
|<span data-ttu-id="74de7-127">訊息部分參考</span><span class="sxs-lookup"><span data-stu-id="74de7-127">Message-part reference</span></span>|<span data-ttu-id="74de7-128">bpws:getContainerData(%msgName%, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="74de7-128">bpws:getContainerData(%msgName%, %locationPath%)</span></span>|  
|<span data-ttu-id="74de7-129">辨別欄位參考</span><span class="sxs-lookup"><span data-stu-id="74de7-129">Distinguished-field reference</span></span>|<span data-ttu-id="74de7-130">bpws:getContainerData(%msgName%, %partName%, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="74de7-130">bpws:getContainerData(%msgName%, %partName%, %locationPath%)</span></span>|  
|<span data-ttu-id="74de7-131">訊息資料屬性參考</span><span class="sxs-lookup"><span data-stu-id="74de7-131">Message data-property reference</span></span>|<span data-ttu-id="74de7-132">bpws:getContainerProperty(%msgName%, %propertyQName%)</span><span class="sxs-lookup"><span data-stu-id="74de7-132">bpws:getContainerProperty(%msgName%, %propertyQName%)</span></span>|  
  
## <a name="operators"></a><span data-ttu-id="74de7-133">運算子</span><span class="sxs-lookup"><span data-stu-id="74de7-133">Operators</span></span>  
  
|<span data-ttu-id="74de7-134">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="74de7-134">XLANG/s</span></span>|<span data-ttu-id="74de7-135">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="74de7-135">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="74de7-136">一元 +</span><span class="sxs-lookup"><span data-stu-id="74de7-136">Unary +</span></span>|<span data-ttu-id="74de7-137">忽略</span><span class="sxs-lookup"><span data-stu-id="74de7-137">Ignored</span></span>|  
|<span data-ttu-id="74de7-138">一元 -</span><span class="sxs-lookup"><span data-stu-id="74de7-138">Unary -</span></span>|<span data-ttu-id="74de7-139">XPath 一元 -</span><span class="sxs-lookup"><span data-stu-id="74de7-139">XPath unary -</span></span>|  
|<span data-ttu-id="74de7-140">一元 !</span><span class="sxs-lookup"><span data-stu-id="74de7-140">Unary !</span></span>|<span data-ttu-id="74de7-141">XPath not() 函式</span><span class="sxs-lookup"><span data-stu-id="74de7-141">XPath not() function</span></span>|  
|<span data-ttu-id="74de7-142">二進位 & &、 &#124; & #124。</span><span class="sxs-lookup"><span data-stu-id="74de7-142">Binary &&, &#124;&#124;</span></span>|<span data-ttu-id="74de7-143">XPath 'and'、'or' 運算子</span><span class="sxs-lookup"><span data-stu-id="74de7-143">XPath 'and', 'or' operators</span></span>|  
|<span data-ttu-id="74de7-144">二進位 ==、!=、<=、<、>=、></span><span class="sxs-lookup"><span data-stu-id="74de7-144">Binary ==, !=, <=, <, >=, ></span></span>|<span data-ttu-id="74de7-145">XPath '='、'!</span><span class="sxs-lookup"><span data-stu-id="74de7-145">XPath '=', '!</span></span> <span data-ttu-id="74de7-146">='，' < ='，' <'、 ' > ='，' >' 運算子</span><span class="sxs-lookup"><span data-stu-id="74de7-146">=', '<=', '<', '>=', '>' operators</span></span>|  
|<span data-ttu-id="74de7-147">二進位 +、-、\*、% (含兩個整數運算元)</span><span class="sxs-lookup"><span data-stu-id="74de7-147">Binary +, -, \*, % with both integral operands</span></span>|<span data-ttu-id="74de7-148">XPath '+'、'-'、'\*'、'mod' 運算子</span><span class="sxs-lookup"><span data-stu-id="74de7-148">XPath '+', '-', '\*', 'mod' operators</span></span>|  
  
## <a name="xlangs-constructs-that-are-disallowed-in-bpel4ws"></a><span data-ttu-id="74de7-149">BPEL4WS 中不允許的 XLANG/s 建構</span><span class="sxs-lookup"><span data-stu-id="74de7-149">XLANG/s constructs that are disallowed in BPEL4WS</span></span>  
  
-   <span data-ttu-id="74de7-150">訊息內容屬性參考</span><span class="sxs-lookup"><span data-stu-id="74de7-150">Message context-property reference</span></span>  
  
-   <span data-ttu-id="74de7-151">服務屬性參考</span><span class="sxs-lookup"><span data-stu-id="74de7-151">Service-property reference</span></span>  
  
-   <span data-ttu-id="74de7-152">連接埠屬性參考</span><span class="sxs-lookup"><span data-stu-id="74de7-152">Port-property reference</span></span>  
  
-   <span data-ttu-id="74de7-153">服務連結屬性參考</span><span class="sxs-lookup"><span data-stu-id="74de7-153">Service link-property reference</span></span>  
  
-   <span data-ttu-id="74de7-154">一元 -- 非整數類型</span><span class="sxs-lookup"><span data-stu-id="74de7-154">Unary – with non-integral type</span></span>  
  
-   <span data-ttu-id="74de7-155">一元 ~</span><span class="sxs-lookup"><span data-stu-id="74de7-155">Unary ~</span></span>  
  
-   <span data-ttu-id="74de7-156">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="74de7-156">Cast operator</span></span>  
  
-   <span data-ttu-id="74de7-157">二進位 / 含整數運算元</span><span class="sxs-lookup"><span data-stu-id="74de7-157">Binary / with integral operands</span></span>  
  
-   <span data-ttu-id="74de7-158">二進位 +、-、\*、%、/ (含非整數運算元)</span><span class="sxs-lookup"><span data-stu-id="74de7-158">Binary +, -, \*, %, / with non-integral operands</span></span>  
  
-   <span data-ttu-id="74de7-159">二進位 <=、<、>=、> (含非字串運算元)</span><span class="sxs-lookup"><span data-stu-id="74de7-159">Binary <=, <, >=, > with non-string operands</span></span>  
  
-   <span data-ttu-id="74de7-160">位元運算子 &、 ^、 & #124。</span><span class="sxs-lookup"><span data-stu-id="74de7-160">Bitwise operators &, ^, &#124;</span></span>  
  
-   <span data-ttu-id="74de7-161">移位運算子 <<、>></span><span class="sxs-lookup"><span data-stu-id="74de7-161">Shift operators <<, >></span></span>  
  
-   <span data-ttu-id="74de7-162">已檢查的運算式</span><span class="sxs-lookup"><span data-stu-id="74de7-162">Checked expression</span></span>  
  
-   <span data-ttu-id="74de7-163">內建運算式</span><span class="sxs-lookup"><span data-stu-id="74de7-163">Intrinsic expression</span></span>  
  
-   <span data-ttu-id="74de7-164">遞增和遞減前後 ++、--</span><span class="sxs-lookup"><span data-stu-id="74de7-164">Pre- and post- increment and decrement ++, --</span></span>  
  
-   <span data-ttu-id="74de7-165">物件引動過程 (含或不含 and/or 參考參數)</span><span class="sxs-lookup"><span data-stu-id="74de7-165">Object invocation (with our without out and/or ref params)</span></span>  
  
-   <span data-ttu-id="74de7-166">'new' 運算子</span><span class="sxs-lookup"><span data-stu-id="74de7-166">'new' operator</span></span>