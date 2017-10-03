---
title: "基本 Types2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, data types
- adapters [JD Edwards EnterpriseOne adapters], data types
- data types, JD Edwards EnterpriseOne adapters
ms.assetid: 96a70f0d-f7f8-4e3b-9511-59b330910ead
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7e5c47d8760e9743ec11a62598581d9d20b3e53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="basic-types"></a><span data-ttu-id="91707-102">基本類型</span><span class="sxs-lookup"><span data-stu-id="91707-102">Basic Types</span></span>
<span data-ttu-id="91707-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 僅提供對 JD Edwards EnterpriseOne 商務功能的存取。</span><span class="sxs-lookup"><span data-stu-id="91707-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne provides access only to JD Edwards EnterpriseOne business functions.</span></span> <span data-ttu-id="91707-104">商務功能中繼資料是透過商務功能介面來讀取，並可用以尋找商務功能與相關資料結構的清單。</span><span class="sxs-lookup"><span data-stu-id="91707-104">Business function metadata is read using a business function interface and used to find a list of business functions and associated data structures.</span></span> <span data-ttu-id="91707-105">不論什麼情況，所有商務功能方法都會使用強型別的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="91707-105">Metadata is strongly typed in all cases for all business function methods.</span></span>  
  
 <span data-ttu-id="91707-106">所有商務功能方法都具有相同的呼叫慣例： 由系統衍生，三個參數和資料結構的指標。</span><span class="sxs-lookup"><span data-stu-id="91707-106">All business function methods have the same calling convention: three parameters that are system derived, and a pointer to a data structure.</span></span> <span data-ttu-id="91707-107">下表顯示商務功能資料型別的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="91707-107">The following table shows how business function data types are represented.</span></span>  
  
|<span data-ttu-id="91707-108">JD Edwards EnterpriseOne 資料型別</span><span class="sxs-lookup"><span data-stu-id="91707-108">JD Edwards EnterpriseOne Data Type</span></span>|<span data-ttu-id="91707-109">Description</span><span class="sxs-lookup"><span data-stu-id="91707-109">Description</span></span>|<span data-ttu-id="91707-110">WDSL 轉換</span><span class="sxs-lookup"><span data-stu-id="91707-110">WDSL Conversion</span></span>|  
|----------------------------------------|-----------------|---------------------|  
|<span data-ttu-id="91707-111">char</span><span class="sxs-lookup"><span data-stu-id="91707-111">char</span></span>|<span data-ttu-id="91707-112">字元字串。</span><span class="sxs-lookup"><span data-stu-id="91707-112">Character string.</span></span>|<span data-ttu-id="91707-113">xsd:string 1</span><span class="sxs-lookup"><span data-stu-id="91707-113">xsd:string of 1</span></span>|  
|<span data-ttu-id="91707-114">int</span><span class="sxs-lookup"><span data-stu-id="91707-114">int</span></span>|<span data-ttu-id="91707-115">短整數。</span><span class="sxs-lookup"><span data-stu-id="91707-115">Short integer.</span></span>|<span data-ttu-id="91707-116">xsd:short</span><span class="sxs-lookup"><span data-stu-id="91707-116">xsd:short</span></span>|  
|<span data-ttu-id="91707-117">long</span><span class="sxs-lookup"><span data-stu-id="91707-117">long</span></span>|<span data-ttu-id="91707-118">長整數。</span><span class="sxs-lookup"><span data-stu-id="91707-118">Long integer.</span></span>|<span data-ttu-id="91707-119">xsd:short</span><span class="sxs-lookup"><span data-stu-id="91707-119">xsd:short</span></span>|  
|<span data-ttu-id="91707-120">字串</span><span class="sxs-lookup"><span data-stu-id="91707-120">String</span></span>|<span data-ttu-id="91707-121">請參閱[處理字串值](../core/handling-string-values2.md)。</span><span class="sxs-lookup"><span data-stu-id="91707-121">See [Handling String Values](../core/handling-string-values2.md).</span></span>|<span data-ttu-id="91707-122">xsd:string</span><span class="sxs-lookup"><span data-stu-id="91707-122">xsd:string</span></span>|  
|<span data-ttu-id="91707-123">JDEDATE</span><span class="sxs-lookup"><span data-stu-id="91707-123">JDEDATE</span></span>|<span data-ttu-id="91707-124">日期的特殊實作。</span><span class="sxs-lookup"><span data-stu-id="91707-124">Special implementation of dates.</span></span>|<span data-ttu-id="91707-125">xsd:date</span><span class="sxs-lookup"><span data-stu-id="91707-125">xsd:date</span></span>|  
|<span data-ttu-id="91707-126">MATH_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="91707-126">MATH_NUMERIC</span></span>|<span data-ttu-id="91707-127">浮點值的特殊實作，包括貨幣值。</span><span class="sxs-lookup"><span data-stu-id="91707-127">Special implementation of floating point numbers, including currency values.</span></span>|<span data-ttu-id="91707-128">xsd: string 為 32</span><span class="sxs-lookup"><span data-stu-id="91707-128">xsd:string of 32</span></span>|  
|<span data-ttu-id="91707-129">Byte</span><span class="sxs-lookup"><span data-stu-id="91707-129">Byte</span></span>|<span data-ttu-id="91707-130">不帶正負號的單一字元。</span><span class="sxs-lookup"><span data-stu-id="91707-130">Single unsigned character.</span></span>|<span data-ttu-id="91707-131">xsd:string 1</span><span class="sxs-lookup"><span data-stu-id="91707-131">xsd:string of 1</span></span>|  
|<span data-ttu-id="91707-132">JDEUTIME</span><span class="sxs-lookup"><span data-stu-id="91707-132">JDEUTIME</span></span>|<span data-ttu-id="91707-133">同時包括日期和時間元件。</span><span class="sxs-lookup"><span data-stu-id="91707-133">Includes both date and time components.</span></span><br /><br /> <span data-ttu-id="91707-134">資料類型會儲存所有日期/時間，以及依國際標準時間 (Coordinated Universal Time，UTC) 執行所有日期/時間計算。</span><span class="sxs-lookup"><span data-stu-id="91707-134">The data type stores all dates/times and performs all date/time calculations in Coordinated Universal Time (UTC).</span></span>|<span data-ttu-id="91707-135">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="91707-135">xsd:dateTime</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91707-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91707-136">See Also</span></span>  
 <span data-ttu-id="91707-137">[使用 MATH_NUMERIC 類型](../core/using-the-math-numeric-type1.md) </span><span class="sxs-lookup"><span data-stu-id="91707-137">[Using the MATH_NUMERIC Type](../core/using-the-math-numeric-type1.md) </span></span>  
 <span data-ttu-id="91707-138">[處理字串值](../core/handling-string-values2.md) </span><span class="sxs-lookup"><span data-stu-id="91707-138">[Handling String Values](../core/handling-string-values2.md) </span></span>  
 [<span data-ttu-id="91707-139">附錄 b： 資料類型</span><span class="sxs-lookup"><span data-stu-id="91707-139">Appendix B: Data Types</span></span>](../core/appendix-b-data-types.md)