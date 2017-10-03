---
title: "基本 Types1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, data types
- JD Edwards OneWorld adapters, business functions
- .NET Framework, mapping [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], data types
- adapters [JD Edwards OneWorld adapters], .NET Framework
- JD Edwards OneWorld adapters, .NET Framework
- adapters [JD Edwards OneWorld adapters], business functions
ms.assetid: d306ea1b-fb74-4fa3-9681-405252928df1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e90cda6259567adf5236d0c28e576900d8b25271
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="basic-types"></a><span data-ttu-id="fec7b-102">基本類型</span><span class="sxs-lookup"><span data-stu-id="fec7b-102">Basic Types</span></span>
<span data-ttu-id="fec7b-103">Microsoft BizTalk Adapter for JD Edwards OneWorld 僅提供對 JD Edwards OneWorld 商務功能的存取。</span><span class="sxs-lookup"><span data-stu-id="fec7b-103">Microsoft BizTalk Adapter for JD Edwards OneWorld provides access only to JD Edwards OneWorld business functions.</span></span> <span data-ttu-id="fec7b-104">商務功能中繼資料是透過商務功能介面來讀取，並可用以尋找商務功能與相關資料結構的清單。</span><span class="sxs-lookup"><span data-stu-id="fec7b-104">Business function metadata is read using a business function interface and used to find a list of business functions and associated data structures.</span></span> <span data-ttu-id="fec7b-105">不論什麼情況，所有商務功能方法都會使用強型別的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fec7b-105">Metadata is strongly typed in all cases for all business function methods.</span></span>  
  
 <span data-ttu-id="fec7b-106">所有商務功能方法都具有相同的呼叫慣例： 由系統衍生，三個參數和資料結構的指標。</span><span class="sxs-lookup"><span data-stu-id="fec7b-106">All business function methods have the same calling convention: three parameters that are system derived, and a pointer to a data structure.</span></span> <span data-ttu-id="fec7b-107">下表列出商務功能資料型別的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="fec7b-107">The following table shows how the business function data types are represented.</span></span>  
  
 <span data-ttu-id="fec7b-108">**商務功能資料型別的**</span><span class="sxs-lookup"><span data-stu-id="fec7b-108">**Business function data types**</span></span>  
  
|<span data-ttu-id="fec7b-109">JD Edwards OneWorld 資料型別</span><span class="sxs-lookup"><span data-stu-id="fec7b-109">JD Edwards OneWorld Data Type</span></span>|<span data-ttu-id="fec7b-110">Description</span><span class="sxs-lookup"><span data-stu-id="fec7b-110">Description</span></span>|<span data-ttu-id="fec7b-111">WDSL 轉換</span><span class="sxs-lookup"><span data-stu-id="fec7b-111">WDSL Conversion</span></span>|  
|-----------------------------------|-----------------|---------------------|  
|<span data-ttu-id="fec7b-112">char</span><span class="sxs-lookup"><span data-stu-id="fec7b-112">char</span></span>|<span data-ttu-id="fec7b-113">字元字串。</span><span class="sxs-lookup"><span data-stu-id="fec7b-113">Character string.</span></span>|<span data-ttu-id="fec7b-114">xsd:string 1</span><span class="sxs-lookup"><span data-stu-id="fec7b-114">xsd:string of 1</span></span>|  
|<span data-ttu-id="fec7b-115">int</span><span class="sxs-lookup"><span data-stu-id="fec7b-115">int</span></span>|<span data-ttu-id="fec7b-116">短整數。</span><span class="sxs-lookup"><span data-stu-id="fec7b-116">Short integer.</span></span>|<span data-ttu-id="fec7b-117">xsd:short</span><span class="sxs-lookup"><span data-stu-id="fec7b-117">xsd:short</span></span>|  
|<span data-ttu-id="fec7b-118">long</span><span class="sxs-lookup"><span data-stu-id="fec7b-118">long</span></span>|<span data-ttu-id="fec7b-119">長整數。</span><span class="sxs-lookup"><span data-stu-id="fec7b-119">Long integer.</span></span>|<span data-ttu-id="fec7b-120">xsd:short</span><span class="sxs-lookup"><span data-stu-id="fec7b-120">xsd:short</span></span>|  
|<span data-ttu-id="fec7b-121">字串</span><span class="sxs-lookup"><span data-stu-id="fec7b-121">String</span></span>|<span data-ttu-id="fec7b-122">請參閱[處理字串值](../core/handling-string-values1.md)。</span><span class="sxs-lookup"><span data-stu-id="fec7b-122">See [Handling String Values](../core/handling-string-values1.md).</span></span>|<span data-ttu-id="fec7b-123">xsd:string</span><span class="sxs-lookup"><span data-stu-id="fec7b-123">xsd:string</span></span>|  
|<span data-ttu-id="fec7b-124">JDEDATE</span><span class="sxs-lookup"><span data-stu-id="fec7b-124">JDEDATE</span></span>|<span data-ttu-id="fec7b-125">日期的特殊實作。</span><span class="sxs-lookup"><span data-stu-id="fec7b-125">Special implementation of dates.</span></span>|<span data-ttu-id="fec7b-126">xsd:date</span><span class="sxs-lookup"><span data-stu-id="fec7b-126">xsd:date</span></span>|  
|<span data-ttu-id="fec7b-127">MATH_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="fec7b-127">MATH_NUMERIC</span></span>|<span data-ttu-id="fec7b-128">浮點值的特殊實作，包括貨幣值。</span><span class="sxs-lookup"><span data-stu-id="fec7b-128">Special implementation of floating point numbers, including currency values.</span></span>|<span data-ttu-id="fec7b-129">xsd: string 為 32</span><span class="sxs-lookup"><span data-stu-id="fec7b-129">xsd:string of 32</span></span>|  
|<span data-ttu-id="fec7b-130">Byte</span><span class="sxs-lookup"><span data-stu-id="fec7b-130">Byte</span></span>|<span data-ttu-id="fec7b-131">不帶正負號的單一字元。</span><span class="sxs-lookup"><span data-stu-id="fec7b-131">Single unsigned character.</span></span>|<span data-ttu-id="fec7b-132">xsd:string 1</span><span class="sxs-lookup"><span data-stu-id="fec7b-132">xsd:string of 1</span></span>|  
  
 <span data-ttu-id="fec7b-133">下表包含 JD Edwards OneWorld 中的基本型別清單，及其對應至 Microsoft .NET Framework 的情形。</span><span class="sxs-lookup"><span data-stu-id="fec7b-133">The following table contains the list of basic types in JD Edwards OneWorld and how they map to the Microsoft .NET Framework.</span></span>  
  
 <span data-ttu-id="fec7b-134">**基本類型，以及它們如何對應至 Microsoft.NET Framework**</span><span class="sxs-lookup"><span data-stu-id="fec7b-134">**Basic types and how they map to the Microsoft .NET Framework**</span></span>  
  
|<span data-ttu-id="fec7b-135">JD Edwards OneWorld XE</span><span class="sxs-lookup"><span data-stu-id="fec7b-135">JD Edwards OneWorld XE</span></span>|<span data-ttu-id="fec7b-136">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="fec7b-136">.NET Framework</span></span>|  
|----------------------------|--------------------|  
|<span data-ttu-id="fec7b-137">char</span><span class="sxs-lookup"><span data-stu-id="fec7b-137">char</span></span>|<span data-ttu-id="fec7b-138">字串</span><span class="sxs-lookup"><span data-stu-id="fec7b-138">String</span></span>|  
|<span data-ttu-id="fec7b-139">int</span><span class="sxs-lookup"><span data-stu-id="fec7b-139">int</span></span>|<span data-ttu-id="fec7b-140">Short</span><span class="sxs-lookup"><span data-stu-id="fec7b-140">Short</span></span>|  
|<span data-ttu-id="fec7b-141">long</span><span class="sxs-lookup"><span data-stu-id="fec7b-141">long</span></span>|<span data-ttu-id="fec7b-142">Short</span><span class="sxs-lookup"><span data-stu-id="fec7b-142">Short</span></span>|  
|<span data-ttu-id="fec7b-143">字串</span><span class="sxs-lookup"><span data-stu-id="fec7b-143">String</span></span>|<span data-ttu-id="fec7b-144">字串</span><span class="sxs-lookup"><span data-stu-id="fec7b-144">String</span></span>|  
|<span data-ttu-id="fec7b-145">JDEDATE</span><span class="sxs-lookup"><span data-stu-id="fec7b-145">JDEDATE</span></span>|<span data-ttu-id="fec7b-146">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="fec7b-146">System.DateTime</span></span>|  
|<span data-ttu-id="fec7b-147">MATH_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="fec7b-147">MATH_NUMERIC</span></span>|<span data-ttu-id="fec7b-148">字串</span><span class="sxs-lookup"><span data-stu-id="fec7b-148">String</span></span>|  
|<span data-ttu-id="fec7b-149">Byte</span><span class="sxs-lookup"><span data-stu-id="fec7b-149">Byte</span></span>|<span data-ttu-id="fec7b-150">字串</span><span class="sxs-lookup"><span data-stu-id="fec7b-150">String</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="fec7b-151">如果只有一個引數，且傳回引數為 void，則預留位置會取代為類別，外部部分則會變成傳回值。</span><span class="sxs-lookup"><span data-stu-id="fec7b-151">If there is only one argument, and the return argument is void, the holder is replaced by the class, and the out portion becomes the return value.</span></span> <span data-ttu-id="fec7b-152">例如：</span><span class="sxs-lookup"><span data-stu-id="fec7b-152">For example:</span></span>  
  
```  
org.apache.axis.holders.DateHolder becomes a java.util.Date.   
```  
  
 <span data-ttu-id="fec7b-153">以下是方法簽章的範例：</span><span class="sxs-lookup"><span data-stu-id="fec7b-153">The following is an example of method signatures:</span></span>  
  
```  
void testDate1(org.apache.axis.holders.DateHolder date1  
        org.apache.axis.holders.DateHolder date2);  
  
java.util.Date testDate2(java.util.Date date);  
```  
  
## <a name="character-limited-strings"></a><span data-ttu-id="fec7b-154">有限字元的字串</span><span class="sxs-lookup"><span data-stu-id="fec7b-154">Character-Limited Strings</span></span>  
 <span data-ttu-id="fec7b-155">在 JD Edwards OneWorld 中，有些字串有字元限制。</span><span class="sxs-lookup"><span data-stu-id="fec7b-155">In JD Edwards OneWorld, some strings are character-limited.</span></span> <span data-ttu-id="fec7b-156">任何額外的字元都會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="fec7b-156">Any extra character causes an error.</span></span> <span data-ttu-id="fec7b-157">若要檢視字串中的字元限制，您可以使用 Microsoft 配接器精靈。</span><span class="sxs-lookup"><span data-stu-id="fec7b-157">To see the limit of characters in the strings, you can use the Microsoft Adapter Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fec7b-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fec7b-158">See Also</span></span>  
 <span data-ttu-id="fec7b-159">[使用 MATH_NUMERIC 類型](../core/using-the-math-numeric-type2.md) </span><span class="sxs-lookup"><span data-stu-id="fec7b-159">[Using the MATH_NUMERIC Type](../core/using-the-math-numeric-type2.md) </span></span>  
 <span data-ttu-id="fec7b-160">[處理字串值](../core/handling-string-values1.md) </span><span class="sxs-lookup"><span data-stu-id="fec7b-160">[Handling String Values](../core/handling-string-values1.md) </span></span>  
 [<span data-ttu-id="fec7b-161">附錄 a： 資料類型</span><span class="sxs-lookup"><span data-stu-id="fec7b-161">Appendix A: Data Types</span></span>](../core/appendix-a-data-types.md)