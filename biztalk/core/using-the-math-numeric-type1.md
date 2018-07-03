---
title: 使用 MATH_NUMERIC 類型 1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters [JD Edwards EnterpriseOne adapters], currency
- JD Edwards EnterpriseOne adapters, exponents
- adapters [JD Edwards EnterpriseOne adapters], exponents
- MATH_NUMERIC type
- currency, values [JD Edwards EnterpriseOne adapters]
- JD Edwards EnterpriseOne adapters, currency
- exponents, values [JD Edwards EnterpriseOne adapters]
ms.assetid: 2a302216-f0a6-4afb-8f7d-bb1475ea1c57
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dba376c1bbbb6e5219969b97393f72380c75d9fa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007527"
---
# <a name="using-the-mathnumeric-type"></a><span data-ttu-id="23bde-102">使用 MATH_NUMERIC 類型</span><span class="sxs-lookup"><span data-stu-id="23bde-102">Using the MATH_NUMERIC Type</span></span>
<span data-ttu-id="23bde-103">本主題說明 MATH_NUMERIC 型別及其指數處理方式、最大位數與最大小數位數等相關細節，</span><span class="sxs-lookup"><span data-stu-id="23bde-103">This topic describes the MATH_NUMERIC type and details how exponents are handled, the maximum number of digits, and the maximum number of decimal digits.</span></span> <span data-ttu-id="23bde-104">其中亦包含下列討論：</span><span class="sxs-lookup"><span data-stu-id="23bde-104">It also includes a discussion on:</span></span>  
  
- <span data-ttu-id="23bde-105">指數</span><span class="sxs-lookup"><span data-stu-id="23bde-105">Exponents</span></span>  
  
- <span data-ttu-id="23bde-106">無效值</span><span class="sxs-lookup"><span data-stu-id="23bde-106">Invalid Values</span></span>  
  
- <span data-ttu-id="23bde-107">運算精確度</span><span class="sxs-lookup"><span data-stu-id="23bde-107">Precision for Operations</span></span>  
  
- <span data-ttu-id="23bde-108">CURRENCY</span><span class="sxs-lookup"><span data-stu-id="23bde-108">Currency</span></span>  
  
  <span data-ttu-id="23bde-109">MATH_NUMERIC 型別是數值字串型別。</span><span class="sxs-lookup"><span data-stu-id="23bde-109">The MATH_NUMERIC type is a numeric string type.</span></span> <span data-ttu-id="23bde-110">若要使用，請輸入下列格式的參數值：</span><span class="sxs-lookup"><span data-stu-id="23bde-110">To use it, enter parameter values of the following format:</span></span>  
  
```  
<OptionalSign><IntegerAndFractionalPart><OptionalExponentPart>  
  
```  
  
 <span data-ttu-id="23bde-111">位置</span><span class="sxs-lookup"><span data-stu-id="23bde-111">Where</span></span>  
  
 <span data-ttu-id="23bde-112">`<OptionalSign>` 可以是`+`或`-`。</span><span class="sxs-lookup"><span data-stu-id="23bde-112">`<OptionalSign>` can be `+` or `-`.</span></span> <span data-ttu-id="23bde-113">`+` 預設值。</span><span class="sxs-lookup"><span data-stu-id="23bde-113">`+` is the default.</span></span>  
  
 <span data-ttu-id="23bde-114">`<IntegerAndFractionalPart>` 最多可有 32 個有效位數，不計入小數點符號。</span><span class="sxs-lookup"><span data-stu-id="23bde-114">`<IntegerAndFractionalPart>` is a maximum of 32 significant digits, not counting the decimal symbol.</span></span> <span data-ttu-id="23bde-115">小數點符號是地區設定特定 JD Edwards EnterpriseOne 安裝 — 通常是句號 （.） 或逗號 （，）。</span><span class="sxs-lookup"><span data-stu-id="23bde-115">The decimal symbol is locale-specific to the JD Edwards EnterpriseOne installation—typically a period (.) or a comma (,).</span></span> <span data-ttu-id="23bde-116">數字可以是全部整數、全部小數或是部分整數部分小數，但是不得超過 32 個位數。</span><span class="sxs-lookup"><span data-stu-id="23bde-116">The digits may be all integer, all fraction, or part integer and part fraction, but they cannot exceed 32.</span></span>  
  
 <span data-ttu-id="23bde-117">`<OptionalExponentPart>` 等於：</span><span class="sxs-lookup"><span data-stu-id="23bde-117">`<OptionalExponentPart>` is equivalent to:</span></span>  
  
```  
'e' <OptionalSign><ExponentDigits>  
```  
  
 <span data-ttu-id="23bde-118">位置</span><span class="sxs-lookup"><span data-stu-id="23bde-118">Where</span></span>  
  
 <span data-ttu-id="23bde-119">`<OptionalSign>` 可以是`+`或`-`。</span><span class="sxs-lookup"><span data-stu-id="23bde-119">`<OptionalSign>` can be `+` or `-`.</span></span> <span data-ttu-id="23bde-120">`+` 預設值。</span><span class="sxs-lookup"><span data-stu-id="23bde-120">`+` is the default.</span></span>  
  
 <span data-ttu-id="23bde-121">`<ExponentDigits>` 最多可有兩位數。</span><span class="sxs-lookup"><span data-stu-id="23bde-121">`<ExponentDigits>` are at most two digits.</span></span> <span data-ttu-id="23bde-122">您可以使用 63 到 -63 之間的值 (0 除外)。</span><span class="sxs-lookup"><span data-stu-id="23bde-122">You are permitted values between 63 and -63 excluding zero.</span></span>  
  
## <a name="valid-values"></a><span data-ttu-id="23bde-123">有效的值</span><span class="sxs-lookup"><span data-stu-id="23bde-123">Valid Values</span></span>  
 <span data-ttu-id="23bde-124">範例**有效**MATH_NUMERIC 值：</span><span class="sxs-lookup"><span data-stu-id="23bde-124">Examples of **valid** MATH_NUMERIC values:</span></span>  
  
-   <span data-ttu-id="23bde-125">123.045</span><span class="sxs-lookup"><span data-stu-id="23bde-125">123.045</span></span>  
  
-   <span data-ttu-id="23bde-126">4089 (請注意，千位處沒有逗號)</span><span class="sxs-lookup"><span data-stu-id="23bde-126">4089 (note there is no comma for thousands)</span></span>  
  
-   <span data-ttu-id="23bde-127">-9084</span><span class="sxs-lookup"><span data-stu-id="23bde-127">-9084</span></span>  
  
-   <span data-ttu-id="23bde-128">-230.75</span><span class="sxs-lookup"><span data-stu-id="23bde-128">-230.75</span></span>  
  
-   <span data-ttu-id="23bde-129">0.010503</span><span class="sxs-lookup"><span data-stu-id="23bde-129">0.010503</span></span>  
  
-   <span data-ttu-id="23bde-130">1.023e-10，這等於 0.0000000001023</span><span class="sxs-lookup"><span data-stu-id="23bde-130">1.023e-10, which is equivalent to 0.0000000001023</span></span>  
  
-   <span data-ttu-id="23bde-131">0.097e5 或 0.097e+5，這等於 9700</span><span class="sxs-lookup"><span data-stu-id="23bde-131">0.097e5 or 0.097e+5, which is equivalent to 9700</span></span>  
  
-   <span data-ttu-id="23bde-132">1.0e-32，這等於 0.00000000000000000000000000000001 (這是有效值，因為在此例中會忽略整數 '0'，有效的小數點後數字位數為 32 個)</span><span class="sxs-lookup"><span data-stu-id="23bde-132">1.0e-32, which is equivalent to 0.00000000000000000000000000000001 (This is valid because in this case, the integral '0' is ignored, 32 significant fractional digits.)</span></span>  
  
## <a name="invalid-values"></a><span data-ttu-id="23bde-133">無效值</span><span class="sxs-lookup"><span data-stu-id="23bde-133">Invalid Values</span></span>  
 <span data-ttu-id="23bde-134">無效值需視值的種類而定。</span><span class="sxs-lookup"><span data-stu-id="23bde-134">Invalid values depend on the kind of value.</span></span> <span data-ttu-id="23bde-135">太小的小數將視為零 (將喪失全部有效位數)。</span><span class="sxs-lookup"><span data-stu-id="23bde-135">A decimal fraction that is too small is interpreted as zero (all significant digits are lost).</span></span> <span data-ttu-id="23bde-136">整數包含太多有效位數會造成無法預期的後果。</span><span class="sxs-lookup"><span data-stu-id="23bde-136">An integer that has too many significant digits causes unexpected results.</span></span> <span data-ttu-id="23bde-137">在此情況下，JD Edwards EnterpriseOne 不一定會引發錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="23bde-137">JD Edwards EnterpriseOne does not always raise an error condition in this case.</span></span> <span data-ttu-id="23bde-138">指數若是太大或太小，也會傳回為無效值。</span><span class="sxs-lookup"><span data-stu-id="23bde-138">An exponent that is too large or too small also returns as an invalid value.</span></span>  
  
 <span data-ttu-id="23bde-139">範例**無效**MATH_NUMERIC 值：</span><span class="sxs-lookup"><span data-stu-id="23bde-139">Examples of **invalid** MATH_NUMERIC values:</span></span>  
  
- <span data-ttu-id="23bde-140">1034.00000000000000000000000000001023 - 有效位數過多</span><span class="sxs-lookup"><span data-stu-id="23bde-140">1034.00000000000000000000000000001023 - too many significant digits</span></span>  
  
- <span data-ttu-id="23bde-141">1.023e-64 - 指數太小</span><span class="sxs-lookup"><span data-stu-id="23bde-141">1.023e-64 - exponent too small</span></span>  
  
- <span data-ttu-id="23bde-142">0.00317e64 - 指數太大</span><span class="sxs-lookup"><span data-stu-id="23bde-142">0.00317e64 - exponent too large</span></span>  
  
  <span data-ttu-id="23bde-143">除正負號與小數符號外的所有其他非數值字元都會造成無效值。</span><span class="sxs-lookup"><span data-stu-id="23bde-143">Any non-numeric characters other than those appropriate for signs and decimal symbols result in an invalid value.</span></span>  
  
## <a name="exponents"></a><span data-ttu-id="23bde-144">指數</span><span class="sxs-lookup"><span data-stu-id="23bde-144">Exponents</span></span>  
 <span data-ttu-id="23bde-145">JD Edwards EnterpriseOne MATH_NUMERIC 提供的指數是為了方便用來輸入值。</span><span class="sxs-lookup"><span data-stu-id="23bde-145">Exponents are provided by the JD Edwards EnterpriseOne MATH_NUMERIC as a convenience for entering values.</span></span> <span data-ttu-id="23bde-146">不過，大多數的傳回值不會包含指數 (32 個有效位數全部顯示出來)。</span><span class="sxs-lookup"><span data-stu-id="23bde-146">However, most values return without exponents (with all 32 significant digits visible).</span></span>  
  
## <a name="precision-for-operations"></a><span data-ttu-id="23bde-147">運算精確度</span><span class="sxs-lookup"><span data-stu-id="23bde-147">Precision for Operations</span></span>  
 <span data-ttu-id="23bde-148">如果運算會導致失去精確度，則會自動四捨五入。</span><span class="sxs-lookup"><span data-stu-id="23bde-148">If an operation results in loss of precision, rounding occurs.</span></span> <span data-ttu-id="23bde-149">例如：</span><span class="sxs-lookup"><span data-stu-id="23bde-149">For example:</span></span>  
  
 <span data-ttu-id="23bde-150">1.9e-31 / 10.0 = 0.00000000000000000000000000000002。</span><span class="sxs-lookup"><span data-stu-id="23bde-150">1.9e-31 / 10.0 = 0.00000000000000000000000000000002.</span></span>  
  
 <span data-ttu-id="23bde-151">1.9e-31 / 100.0 = 0.00000000000000000000000000000000</span><span class="sxs-lookup"><span data-stu-id="23bde-151">1.9e-31 / 100.0 = 0.00000000000000000000000000000000</span></span>  
  
 <span data-ttu-id="23bde-152">在其他情況中，當非常大的正值乘以另一個正值時會出現無法預期的後果。</span><span class="sxs-lookup"><span data-stu-id="23bde-152">In other cases, unpredictable results occur, as when a very large positive value is multiplied by another.</span></span> <span data-ttu-id="23bde-153">1.01e32 \* 2.053e32 不會產生可靠的結果，並不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="23bde-153">1.01e32 \* 2.053e32 does not yield reliable results and does not raise an error.</span></span> <span data-ttu-id="23bde-154">大多數的商務案例都不會超過這些範圍。</span><span class="sxs-lookup"><span data-stu-id="23bde-154">For most business scenarios, these ranges are not exceeded.</span></span>  
  
## <a name="currency"></a><span data-ttu-id="23bde-155">CURRENCY</span><span class="sxs-lookup"><span data-stu-id="23bde-155">Currency</span></span>  
 <span data-ttu-id="23bde-156">當 JD Edwards EnterpriseOne 商務功能需要貨幣值時，商務功能永遠會有一個參數用於四字元貨幣代碼。</span><span class="sxs-lookup"><span data-stu-id="23bde-156">When a JD Edwards EnterpriseOne business function expects a currency value, the business function always has a separate parameter for a four-character currency code.</span></span> <span data-ttu-id="23bde-157">除非您要使用和 JD Edwards EnterpriseOne 系統設定的預設值不同的貨幣，否則並不需要傳遞此代碼。</span><span class="sxs-lookup"><span data-stu-id="23bde-157">It is not necessary to pass in this code unless you are using a currency other than the default configured for the JD Edwards EnterpriseOne system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23bde-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23bde-158">See Also</span></span>  
 [<span data-ttu-id="23bde-159">附錄 B：資料類型</span><span class="sxs-lookup"><span data-stu-id="23bde-159">Appendix B: Data Types</span></span>](../core/appendix-b-data-types.md)