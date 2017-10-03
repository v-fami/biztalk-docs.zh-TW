---
title: "進階運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bf2547-5e44-45f8-b577-97e5760a0339
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5002b639df79ece1019c2d013c128f615517ae5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="advanced-functoids"></a><span data-ttu-id="78250-102">進階運算質</span><span class="sxs-lookup"><span data-stu-id="78250-102">Advanced Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="78250-103">概觀</span><span class="sxs-lookup"><span data-stu-id="78250-103">Overview</span></span>
<span data-ttu-id="78250-104">根據進階運算質的用途，它們可分屬五個群組：</span><span class="sxs-lookup"><span data-stu-id="78250-104">Advanced functoids fall into five groups, according to their use:</span></span>  
  
-   <span data-ttu-id="78250-105">**管理迴圈記錄。**</span><span class="sxs-lookup"><span data-stu-id="78250-105">**Managing looping records.**</span></span> <span data-ttu-id="78250-106">**索引**，**反覆項目**，**迴圈**， **「 Nil 值**，**記錄計數**，**資料表擷取程式**，和**表格迴圈**各種組合使用運算質時輸入執行個體訊息包含區段具有無法預測數目所表示的迴圈，重複項目，來源結構描述中的記錄。</span><span class="sxs-lookup"><span data-stu-id="78250-106">The **Index**, **Iteration**, **Looping**, **Nil Value**, **Record Count**, **Table Extractor**, and **Table Looping** functoids are used in various combinations when the input instance message contains sections with an unpredictable number of repeating elements, as represented by looping records in the source schema.</span></span>  
  
-   <span data-ttu-id="78250-107">**條件式對應。**</span><span class="sxs-lookup"><span data-stu-id="78250-107">**Conditional mapping.**</span></span> <span data-ttu-id="78250-108">**值對應**和**值對應 （簡維）**運算質可用以提供從輸入執行個體訊息到輸出執行個體訊息的條件式對應。</span><span class="sxs-lookup"><span data-stu-id="78250-108">The **Value Mapping** and **Value Mapping (Flattening)** functoids are used to provide conditional mapping from an input instance message to an output instance message.</span></span> <span data-ttu-id="78250-109">當第一個輸入參數為 True 時，第二個輸入參數會被放入輸出執行個體訊息中的特定項目或屬性；否則，該項目或屬性不會在輸出執行個體訊息中建立。</span><span class="sxs-lookup"><span data-stu-id="78250-109">When their first input parameter is true, the second input parameter is put into the specified element or attribute in the output instance message; otherwise, that element or attribute is not created in the output instance message.</span></span>  
  
-   <span data-ttu-id="78250-110">**任意指令碼。**</span><span class="sxs-lookup"><span data-stu-id="78250-110">**Arbitrary scripting.**</span></span> <span data-ttu-id="78250-111">**指令碼處理**運算質可用來執行任意指令碼，或輸入執行個體訊息對應到輸出執行個體訊息時，已編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="78250-111">The **Scripting** functoid is used to run arbitrary script or compiled code when an input instance message is being mapped to an output instance message.</span></span> <span data-ttu-id="78250-112">此種指令碼或已編譯的程式碼可以建立，以便接受來自來源執行個體訊息、來自設定的常數值、來自其他運算質的輸出或這些組合的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="78250-112">Such script or compiled code can be created so that it accepts input parameters from the source instance message, from configured constant values, from the output of another functoid, or some combination thereof.</span></span>  
  
-   <span data-ttu-id="78250-113">**簡單對應。**</span><span class="sxs-lookup"><span data-stu-id="78250-113">**Simple mapping.**</span></span> <span data-ttu-id="78250-114">**大量複製**運算質可以用來複製到任意深度，包括它的子元素，從輸入執行個體訊息到輸出執行個體訊息的整個項目。</span><span class="sxs-lookup"><span data-stu-id="78250-114">The **Mass Copy** functoid can be used to copy an entire element, including its subelements to an arbitrary depth, from an input instance message to an output instance message.</span></span>  
  
-   <span data-ttu-id="78250-115">**疑難排解**。</span><span class="sxs-lookup"><span data-stu-id="78250-115">**Troubleshooting**.</span></span> <span data-ttu-id="78250-116">**Assert**運算質可以用來測試項目值的相關假設。</span><span class="sxs-lookup"><span data-stu-id="78250-116">The **Assert** functoid can be used to test your assumptions about element values.</span></span>  
  
## <a name="available-functoids"></a><span data-ttu-id="78250-117">可用的運算質</span><span class="sxs-lookup"><span data-stu-id="78250-117">Available functoids</span></span>
  
 <span data-ttu-id="78250-118">**進階**運算質為：</span><span class="sxs-lookup"><span data-stu-id="78250-118">The **Advanced** functoids are:</span></span> 

* <span data-ttu-id="78250-119">判斷提示運算質</span><span class="sxs-lookup"><span data-stu-id="78250-119">Assert Functoid</span></span>
* <span data-ttu-id="78250-120">索引運算質</span><span class="sxs-lookup"><span data-stu-id="78250-120">Index Functoid</span></span> 
* <span data-ttu-id="78250-121">重複項目運算質</span><span class="sxs-lookup"><span data-stu-id="78250-121">Iteration Functoid</span></span> 
* <span data-ttu-id="78250-122">迴圈運算質</span><span class="sxs-lookup"><span data-stu-id="78250-122">Looping Functoid</span></span> 
* <span data-ttu-id="78250-123">大量複製運算質</span><span class="sxs-lookup"><span data-stu-id="78250-123">Mass Copy Functoid</span></span> 
* <span data-ttu-id="78250-124">Nil 值運算質</span><span class="sxs-lookup"><span data-stu-id="78250-124">Nil Value Functoid</span></span>
* <span data-ttu-id="78250-125">記錄計數運算質</span><span class="sxs-lookup"><span data-stu-id="78250-125">Record Count Functoid</span></span> 
* <span data-ttu-id="78250-126">指令碼處理運算質</span><span class="sxs-lookup"><span data-stu-id="78250-126">Scripting Functoid</span></span> 
* <span data-ttu-id="78250-127">表格迴圈和表格擷取程式運算質</span><span class="sxs-lookup"><span data-stu-id="78250-127">Table Looping and Table Extractor Functoids</span></span>
* <span data-ttu-id="78250-128">值對應運算質</span><span class="sxs-lookup"><span data-stu-id="78250-128">Value Mapping Functoid</span></span>
* <span data-ttu-id="78250-129">值對應 (簡維) 運算質</span><span class="sxs-lookup"><span data-stu-id="78250-129">Value Mapping (Flattening) Functoid</span></span>

<span data-ttu-id="78250-130">這些運算質上的更多詳細資料位於**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="78250-130">More details on these functoids are in the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="78250-131">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="78250-131">Next steps</span></span>
  
-   [<span data-ttu-id="78250-132">判斷提示運算質</span><span class="sxs-lookup"><span data-stu-id="78250-132">Assert Functoid</span></span>](../core/assert-functoid.md)  
  
-   [<span data-ttu-id="78250-133">索引運算質</span><span class="sxs-lookup"><span data-stu-id="78250-133">Index Functoid</span></span>](../core/index-functoid.md)  
  
-   [<span data-ttu-id="78250-134">反覆項目運算質</span><span class="sxs-lookup"><span data-stu-id="78250-134">Iteration Functoid</span></span>](../core/iteration-functoid.md)  
  
-   [<span data-ttu-id="78250-135">迴圈運算質</span><span class="sxs-lookup"><span data-stu-id="78250-135">Looping Functoid</span></span>](../core/looping-functoid.md)  
  
-   [<span data-ttu-id="78250-136">大量複製運算質</span><span class="sxs-lookup"><span data-stu-id="78250-136">Mass Copy Functoid</span></span>](../core/mass-copy-functoid.md)  
  
-   [<span data-ttu-id="78250-137">Nil 值運算質</span><span class="sxs-lookup"><span data-stu-id="78250-137">Nil Value Functoid</span></span>](../core/nil-value-functoid.md)  
  
-   [<span data-ttu-id="78250-138">記錄計數運算質</span><span class="sxs-lookup"><span data-stu-id="78250-138">Record Count Functoid</span></span>](../core/record-count-functoid.md)  
  
-   [<span data-ttu-id="78250-139">表格迴圈和表格擷取程式運算質</span><span class="sxs-lookup"><span data-stu-id="78250-139">Table Looping and Table Extractor Functoids</span></span>](../core/table-looping-and-table-extractor-functoids.md)  
  
-   [<span data-ttu-id="78250-140">值對應運算質</span><span class="sxs-lookup"><span data-stu-id="78250-140">Value Mapping Functoid</span></span>](../core/value-mapping-functoid.md)  
  
-   [<span data-ttu-id="78250-141">值對應 （簡維） 運算質</span><span class="sxs-lookup"><span data-stu-id="78250-141">Value Mapping (Flattening) Functoid</span></span>](../core/value-mapping-flattening-functoid.md)  
  
-   [<span data-ttu-id="78250-142">指令碼處理運算質</span><span class="sxs-lookup"><span data-stu-id="78250-142">Scripting Functoid</span></span>](../core/scripting-functoid.md)