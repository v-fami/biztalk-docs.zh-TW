---
title: "使用 MATH_NUMERIC Type2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exponents, JD Edwards OneWorld adapters
- currency, JD Edwards OneWorld adapters
- MATH_NUMERIC type
- adapters [JD Edwards OneWorld adapters], currency
ms.assetid: 14d04576-0028-4af4-84bd-92c4ca492126
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac6c96c32244acdcfaf81e8747e381bebd455598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-mathnumeric-type"></a><span data-ttu-id="4b41e-102">使用 MATH_NUMERIC 類型</span><span class="sxs-lookup"><span data-stu-id="4b41e-102">Using the MATH_NUMERIC Type</span></span>
<span data-ttu-id="4b41e-103">本主題說明 MATH_NUMERIC 型別及其指數處理方式、最大位數與最大小數位數等相關細節，</span><span class="sxs-lookup"><span data-stu-id="4b41e-103">This topic describes the MATH_NUMERIC type and details how exponents are handled, the maximum number of digits, and the maximum number of decimal digits.</span></span> <span data-ttu-id="4b41e-104">並包含下列內容的討論：</span><span class="sxs-lookup"><span data-stu-id="4b41e-104">It also includes a discussion on the following:</span></span>  
  
-   <span data-ttu-id="4b41e-105">指數</span><span class="sxs-lookup"><span data-stu-id="4b41e-105">Exponents</span></span>  
  
-   <span data-ttu-id="4b41e-106">無效值</span><span class="sxs-lookup"><span data-stu-id="4b41e-106">Invalid Values</span></span>  
  
-   <span data-ttu-id="4b41e-107">運算精確度</span><span class="sxs-lookup"><span data-stu-id="4b41e-107">Precision for Operations</span></span>  
  
-   <span data-ttu-id="4b41e-108">貨幣</span><span class="sxs-lookup"><span data-stu-id="4b41e-108">Currency</span></span>  
  
 <span data-ttu-id="4b41e-109">MATH_NUMERIC 型別是數值字串型別。</span><span class="sxs-lookup"><span data-stu-id="4b41e-109">The MATH_NUMERIC type is a numeric string type.</span></span> <span data-ttu-id="4b41e-110">若要使用，請輸入下列格式的參數值：</span><span class="sxs-lookup"><span data-stu-id="4b41e-110">To use it, enter parameter values of the following format:</span></span>  
  
```  
<OptionalSign><IntegerAndFractionalPart><OptionalExponentPart>  
```  
  
 <span data-ttu-id="4b41e-111">位置</span><span class="sxs-lookup"><span data-stu-id="4b41e-111">Where</span></span>  
  
-   <span data-ttu-id="4b41e-112">`<OptionalSign>`可以是`+`或`-`。</span><span class="sxs-lookup"><span data-stu-id="4b41e-112">`<OptionalSign>` can be `+` or `-`.</span></span> <span data-ttu-id="4b41e-113">`+`預設值。</span><span class="sxs-lookup"><span data-stu-id="4b41e-113">`+` is the default.</span></span>  
  
-   <span data-ttu-id="4b41e-114">`<IntegerAndFractionalPart>` 最多可有 32 個有效位數，不計入小數點符號。</span><span class="sxs-lookup"><span data-stu-id="4b41e-114">`<IntegerAndFractionalPart>` is a maximum of 32 significant digits, not counting the decimal symbol.</span></span> <span data-ttu-id="4b41e-115">JD Edwards OneWorld 安裝中的小數點符號需依據地區設定而定，一般是使用句點 (.) 或逗點 (,)。</span><span class="sxs-lookup"><span data-stu-id="4b41e-115">The decimal symbol is locale-specific to the JD Edwards OneWorld installation—typically a period (.) or a comma (,).</span></span> <span data-ttu-id="4b41e-116">數字可以是全部整數、全部小數或是部分整數部分小數，但是不得超過 32 個位數。</span><span class="sxs-lookup"><span data-stu-id="4b41e-116">The digits may be all integer, all fraction, or part integer and part fraction, but they cannot exceed 32.</span></span>  
  
-   <span data-ttu-id="4b41e-117">`<OptionalExponentPart>` 等於：</span><span class="sxs-lookup"><span data-stu-id="4b41e-117">`<OptionalExponentPart>` is equivalent to:</span></span>  
  
    ```  
    'e' <OptionalSign><ExponentDigits>  
    ```  
  
 <span data-ttu-id="4b41e-118">位置</span><span class="sxs-lookup"><span data-stu-id="4b41e-118">Where</span></span>  
  
-   <span data-ttu-id="4b41e-119">`<OptionalSign>`可以是`+`或-。</span><span class="sxs-lookup"><span data-stu-id="4b41e-119">`<OptionalSign>` can be `+` or -.</span></span> <span data-ttu-id="4b41e-120">`+`預設值。</span><span class="sxs-lookup"><span data-stu-id="4b41e-120">`+` is the default.</span></span>  
  
-   <span data-ttu-id="4b41e-121">`<ExponentDigits>` 最多可有兩位數。</span><span class="sxs-lookup"><span data-stu-id="4b41e-121">`<ExponentDigits>` are at most two digits.</span></span> <span data-ttu-id="4b41e-122">您可以使用 63 到 -63 之間的值 (0 除外)。</span><span class="sxs-lookup"><span data-stu-id="4b41e-122">You are permitted values between 63 and -63 excluding zero.</span></span>  
  
## <a name="valid-values"></a><span data-ttu-id="4b41e-123">有效的值</span><span class="sxs-lookup"><span data-stu-id="4b41e-123">Valid Values</span></span>  
 <span data-ttu-id="4b41e-124">有效的 MATH_NUMERIC 值範例：</span><span class="sxs-lookup"><span data-stu-id="4b41e-124">Examples of valid MATH_NUMERIC values:</span></span>  
  
-   <span data-ttu-id="4b41e-125">123.045</span><span class="sxs-lookup"><span data-stu-id="4b41e-125">123.045</span></span>  
  
-   <span data-ttu-id="4b41e-126">4089 (請注意，千位處沒有逗號)</span><span class="sxs-lookup"><span data-stu-id="4b41e-126">4089 (note there is no comma for thousands)</span></span>  
  
-   <span data-ttu-id="4b41e-127">-9084</span><span class="sxs-lookup"><span data-stu-id="4b41e-127">-9084</span></span>  
  
-   <span data-ttu-id="4b41e-128">-230.75</span><span class="sxs-lookup"><span data-stu-id="4b41e-128">-230.75</span></span>  
  
-   <span data-ttu-id="4b41e-129">0.010503</span><span class="sxs-lookup"><span data-stu-id="4b41e-129">0.010503</span></span>  
  
-   <span data-ttu-id="4b41e-130">1.023e-10，這等於 0.0000000001023</span><span class="sxs-lookup"><span data-stu-id="4b41e-130">1.023e-10, which is equivalent to 0.0000000001023</span></span>  
  
-   <span data-ttu-id="4b41e-131">0.097e5 或 0.097e+5，這等於 9700</span><span class="sxs-lookup"><span data-stu-id="4b41e-131">0.097e5 or 0.097e+5, which is equivalent to 9700</span></span>  
  
-   <span data-ttu-id="4b41e-132">1.0e-32，等於 0.00000000000000000000000000000001</span><span class="sxs-lookup"><span data-stu-id="4b41e-132">1.0e-32, which is equivalent to 0.00000000000000000000000000000001</span></span>  
  
     <span data-ttu-id="4b41e-133">(此值有效，因為此處忽略整數 "0" 後，總共有 32 個有效的小數位數。)</span><span class="sxs-lookup"><span data-stu-id="4b41e-133">(This is valid because in this case the integral '0' is ignored, 32 significant fractional digits.)</span></span>  
  
## <a name="invalid-values"></a><span data-ttu-id="4b41e-134">無效值</span><span class="sxs-lookup"><span data-stu-id="4b41e-134">Invalid Values</span></span>  
 <span data-ttu-id="4b41e-135">無效值需視值的種類而定。</span><span class="sxs-lookup"><span data-stu-id="4b41e-135">Invalid values depend on the kind of value.</span></span> <span data-ttu-id="4b41e-136">太小的小數將視為零 (將喪失全部有效位數)。</span><span class="sxs-lookup"><span data-stu-id="4b41e-136">A decimal fraction that is too small is interpreted as zero (all significant digits are lost).</span></span> <span data-ttu-id="4b41e-137">整數包含太多有效位數會造成無法預期的後果。</span><span class="sxs-lookup"><span data-stu-id="4b41e-137">An integer that has too many significant digits causes unexpected results.</span></span> <span data-ttu-id="4b41e-138">在此情況下，JD Edwards OneWorld 不一定每次都會報告錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="4b41e-138">JD Edwards OneWorld does not always raise an error condition in this case.</span></span>  
  
 <span data-ttu-id="4b41e-139">太大或太小的指數會傳回無效值。</span><span class="sxs-lookup"><span data-stu-id="4b41e-139">An exponent that is too large or small returns as an invalid value.</span></span>  
  
 <span data-ttu-id="4b41e-140">無效的 MATH_NUMERIC 值範例：</span><span class="sxs-lookup"><span data-stu-id="4b41e-140">Examples of invalid MATH_NUMERIC values:</span></span>  
  
-   <span data-ttu-id="4b41e-141">1034.00000000000000000000000000001023 - 有效位數過多</span><span class="sxs-lookup"><span data-stu-id="4b41e-141">1034.00000000000000000000000000001023 - too many significant digits</span></span>  
  
-   <span data-ttu-id="4b41e-142">1.023e-64 - 指數太小</span><span class="sxs-lookup"><span data-stu-id="4b41e-142">1.023e-64 - exponent too small</span></span>  
  
-   <span data-ttu-id="4b41e-143">0.00317e64 - 指數太大</span><span class="sxs-lookup"><span data-stu-id="4b41e-143">0.00317e64 - exponent too large</span></span>  
  
 <span data-ttu-id="4b41e-144">除正負號與小數符號外的所有其他非數值字元都會造成無效值。</span><span class="sxs-lookup"><span data-stu-id="4b41e-144">Any non-numeric characters other than those appropriate for signs and decimal symbols result in an invalid value.</span></span>  
  
## <a name="exponents"></a><span data-ttu-id="4b41e-145">指數</span><span class="sxs-lookup"><span data-stu-id="4b41e-145">Exponents</span></span>  
 <span data-ttu-id="4b41e-146">為方便輸入值，JD Edwards OneWorld MATH_NUMERIC 特地提供指數功能。</span><span class="sxs-lookup"><span data-stu-id="4b41e-146">Exponents are provided by the JD Edwards OneWorld MATH_NUMERIC as a convenience for entering values.</span></span> <span data-ttu-id="4b41e-147">不過，大多數的傳回值不會包含指數 (32 個有效位數全部顯示出來)。</span><span class="sxs-lookup"><span data-stu-id="4b41e-147">However, most values return without exponents (with all 32 significant digits visible).</span></span>  
  
## <a name="precision-for-operations"></a><span data-ttu-id="4b41e-148">運算精確度</span><span class="sxs-lookup"><span data-stu-id="4b41e-148">Precision for Operations</span></span>  
 <span data-ttu-id="4b41e-149">如果運算會導致失去精確度，則會自動四捨五入。</span><span class="sxs-lookup"><span data-stu-id="4b41e-149">If an operation results in loss of precision, rounding occurs.</span></span> <span data-ttu-id="4b41e-150">例如：</span><span class="sxs-lookup"><span data-stu-id="4b41e-150">For example:</span></span>  
  
 <span data-ttu-id="4b41e-151">1.9e-31 / 10.0 = 0.00000000000000000000000000000002</span><span class="sxs-lookup"><span data-stu-id="4b41e-151">1.9e-31 / 10.0 = 0.00000000000000000000000000000002</span></span>  
  
 <span data-ttu-id="4b41e-152">1.9e-31 / 100.0 = 0.00000000000000000000000000000000</span><span class="sxs-lookup"><span data-stu-id="4b41e-152">1.9e-31 / 100.0 = 0.00000000000000000000000000000000</span></span>  
  
 <span data-ttu-id="4b41e-153">在其他情況中，當非常大的正值乘以另一個正值時會出現無法預期的後果。</span><span class="sxs-lookup"><span data-stu-id="4b41e-153">In other cases, unpredictable results occur, as when a very large positive value is multiplied by another.</span></span>  
  
 <span data-ttu-id="4b41e-154">1.01e32 * 2.053e32 不會產生可靠的結果，並不會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b41e-154">1.01e32 * 2.053e32 does not yield reliable results and does not raise an error.</span></span>  
  
 <span data-ttu-id="4b41e-155">大多數的商務案例都不會超過這些範圍。</span><span class="sxs-lookup"><span data-stu-id="4b41e-155">For most business scenarios, these ranges are not exceeded.</span></span>  
  
## <a name="currency"></a><span data-ttu-id="4b41e-156">貨幣</span><span class="sxs-lookup"><span data-stu-id="4b41e-156">Currency</span></span>  
 <span data-ttu-id="4b41e-157">當某個 JD Edwards OneWorld 商務功能預期收到貨幣值時，該商務功能一律會另外使用一個參數來代表四個字元的貨幣代碼。</span><span class="sxs-lookup"><span data-stu-id="4b41e-157">When a JD Edwards OneWorld business function expects a currency value, the business function always has a separate parameter for a four-character currency code.</span></span> <span data-ttu-id="4b41e-158">除非您使用的貨幣與 JD Edwards OneWorld 系統預設的不同，否則通常不需要傳入此代碼。</span><span class="sxs-lookup"><span data-stu-id="4b41e-158">It is not necessary to pass in this code unless you are using a currency other than the default configured for the JD Edwards OneWorld system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b41e-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b41e-159">See Also</span></span>  
 [<span data-ttu-id="4b41e-160">附錄 a： 資料類型</span><span class="sxs-lookup"><span data-stu-id="4b41e-160">Appendix A: Data Types</span></span>](../core/appendix-a-data-types.md)