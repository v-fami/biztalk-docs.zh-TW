---
title: 邏輯運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e37cdfc3-66de-4333-84eb-a8765afa8407
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 873e2b0ea1189586f9cabfbcb43c6ef276f34e0f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007591"
---
# <a name="logical-functoids"></a><span data-ttu-id="5ed0a-102">邏輯運算質</span><span class="sxs-lookup"><span data-stu-id="5ed0a-102">Logical Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="5ed0a-103">概觀</span><span class="sxs-lookup"><span data-stu-id="5ed0a-103">Overview</span></span>
<span data-ttu-id="5ed0a-104">**邏輯**運算質用來執行下列類型的作業：</span><span class="sxs-lookup"><span data-stu-id="5ed0a-104">**Logical** functoids are used to perform the following types of operations:</span></span>  

- <span data-ttu-id="5ed0a-105">在執行階段執行特定邏輯測試。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-105">Perform specific logical tests at run time.</span></span> <span data-ttu-id="5ed0a-106">**邏輯 OR**，**邏輯 NOT**並**邏輯和**運算質可用來判斷是否要將記錄建立在目的地執行個體訊息中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5ed0a-106">The **Logical OR**, **Logical NOT** and **Logical AND** functoids can be used to determine whether a record is created in a destination instance message, such as the following:</span></span>  

   <span data-ttu-id="5ed0a-107">若 ShipTo**或**orderedby 存在，請建立 BillTo 地址記錄。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-107">If ShipTo **OR** OrderedBy are present, create BillTo address record.</span></span>  

   <span data-ttu-id="5ed0a-108">您也可以搭配使用這些運算質**迴圈**設定多少次記錄迴圈運算質。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-108">You can also use these functoids in conjunction with the **Looping** functoid to configure how many times a record loops.</span></span>  

- <span data-ttu-id="5ed0a-109">控制是否在執行階段於目的執行個體訊息中建立特定記錄。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-109">Control whether a specific record is created in a destination instance message at run time.</span></span> <span data-ttu-id="5ed0a-110">等運算質**IsNil**，**數字**，**小於**，以及**Greater Than**可用來控制是否建立記錄。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-110">Functoids such as **IsNil**, **Logical Numeric**, **Less Than**, and **Greater Than** can be used to control whether a record is created.</span></span>  

   <span data-ttu-id="5ed0a-111">其中一個這些邏輯運算質的結果是否 **，則為 True**，就會產生目的地執行個體訊息中對應的記錄。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-111">If the result of one of these logical functoids is **True**, the corresponding record in the destination instance message is generated.</span></span> <span data-ttu-id="5ed0a-112">如果結果是**False**，目的地執行個體訊息中對應的記錄不會產生。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-112">If the result is **False**, the corresponding record in the destination instance message is not generated.</span></span>  

  <span data-ttu-id="5ed0a-113">運算質**IsNil**，**邏輯日期**，**存在**，**邏輯 NOT**，**邏輯數字**，並**邏輯字串**只接受一個參數。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-113">The functoids **IsNil**, **Logical Date**, **Logical Existence**, **Logical NOT**, **Logical Numeric**, and **Logical String** accept only one parameter.</span></span> <span data-ttu-id="5ed0a-114">運算質**相等**， **Greater Than**， **Greater Than 或 Equal To**，**小於**，**小於或等於**，並**不等於**接受兩個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-114">The functoids **Equal**, **Greater Than**, **Greater Than or Equal To**, **Less Than**, **Less Than or Equal To**, and **Not Equal** accept two input parameters.</span></span> <span data-ttu-id="5ed0a-115">而，則**邏輯與**並**邏輯 OR**運算質接受 2 到 100 個輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-115">Whereas, the **Logical AND** and **Logical OR** functoids accept input parameters between 2 and 100.</span></span>  

  <span data-ttu-id="5ed0a-116">輸出**邏輯**運算質也可接受做為對應中的其他運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-116">The output of a **Logical** functoid can also be accepted as input to other functoids in a map.</span></span> <span data-ttu-id="5ed0a-117">如果兩個**邏輯**運算質與迴圈運算質連結在一起，並接著連結至目的結構描述中的記錄，則會在使用 「 迴圈 」 運算質時，才**邏輯**運算質的輸出，則**True**。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-117">If both a **Logical** functoid and a looping functoid are linked together, and then linked to a record in the destination schema, the looping functoid is used only when the **Logical** functoid output is **True**.</span></span>  

  <span data-ttu-id="5ed0a-118">您也可以使用**邏輯**運算質**值對應**或是**值對應 （簡維）** 運算質來控制是否在目的執行個體訊息中的記錄會建立。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-118">You can also use **Logical** functoids with the **Value Mapping** or **Value Mapping (Flattening)** functoids to control whether a record in the destination instance message is created.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="5ed0a-119">如果兩個記錄或欄位在來源結構描述中的連結至兩個不同**邏輯**運算質，然後將每個連結**邏輯**目的結構描述中相同的資料錄的運算質的第一個**邏輯**運算質會使用在產生可延伸樣式表語言轉換 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-119">If you link two records or fields in the source schema to two different **Logical** functoids, and then link each of the **Logical** functoids to the same record in the destination schema, only the first **Logical** functoid is used in the generated Extensible Stylesheet Language Transformations (XSLT).</span></span> <span data-ttu-id="5ed0a-120">第二個連結，第二個**邏輯**運算質，則會忽略。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-120">The second link, from the second **Logical** functoid, is ignored.</span></span>  

> [!NOTE]
>  <span data-ttu-id="5ed0a-121">在比較兩個字串時，邏輯運算質是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-121">Logical functoids are case-sensitive when comparing two strings.</span></span> <span data-ttu-id="5ed0a-122">例如，"Abc" 與 "abc" 不相等。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-122">For example, "Abc" and "abc" are not equal.</span></span> <span data-ttu-id="5ed0a-123">此規則的例外狀況是當**邏輯**運算質比較代表布林值的字串 **，則為 True**並**False**。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-123">The exception to this rule is when **Logical** functoids compare strings that represent the Boolean values **True** and **False**.</span></span> <span data-ttu-id="5ed0a-124">例如，"True" 與 "true" 相等。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-124">For example, "True" and "true" are equal.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="5ed0a-125">可用的運算質</span><span class="sxs-lookup"><span data-stu-id="5ed0a-125">Available functoids</span></span>  
 <span data-ttu-id="5ed0a-126">**邏輯**運算質為：</span><span class="sxs-lookup"><span data-stu-id="5ed0a-126">The **Logical** functoids are:</span></span> 

* <span data-ttu-id="5ed0a-127">等於</span><span class="sxs-lookup"><span data-stu-id="5ed0a-127">Equal</span></span>
* <span data-ttu-id="5ed0a-128">大於</span><span class="sxs-lookup"><span data-stu-id="5ed0a-128">Greater Than</span></span>
* <span data-ttu-id="5ed0a-129">大於或等於</span><span class="sxs-lookup"><span data-stu-id="5ed0a-129">Greater Than or Equal To</span></span>
* <span data-ttu-id="5ed0a-130">IsNil</span><span class="sxs-lookup"><span data-stu-id="5ed0a-130">IsNil</span></span>
* <span data-ttu-id="5ed0a-131">小於</span><span class="sxs-lookup"><span data-stu-id="5ed0a-131">Less Than</span></span>
* <span data-ttu-id="5ed0a-132">小於或等於</span><span class="sxs-lookup"><span data-stu-id="5ed0a-132">Less Than or Equal To</span></span>
* <span data-ttu-id="5ed0a-133">邏輯 AND</span><span class="sxs-lookup"><span data-stu-id="5ed0a-133">Logical AND</span></span>
* <span data-ttu-id="5ed0a-134">日期</span><span class="sxs-lookup"><span data-stu-id="5ed0a-134">Logical Date</span></span>
* <span data-ttu-id="5ed0a-135">存在</span><span class="sxs-lookup"><span data-stu-id="5ed0a-135">Logical Existence</span></span>
* <span data-ttu-id="5ed0a-136">邏輯 NOT</span><span class="sxs-lookup"><span data-stu-id="5ed0a-136">Logical NOT</span></span>
* <span data-ttu-id="5ed0a-137">數字</span><span class="sxs-lookup"><span data-stu-id="5ed0a-137">Logical Numeric</span></span>
* <span data-ttu-id="5ed0a-138">邏輯 OR</span><span class="sxs-lookup"><span data-stu-id="5ed0a-138">Logical OR</span></span>
* <span data-ttu-id="5ed0a-139">字串</span><span class="sxs-lookup"><span data-stu-id="5ed0a-139">Logical String</span></span>
* <span data-ttu-id="5ed0a-140">Not Equal</span><span class="sxs-lookup"><span data-stu-id="5ed0a-140">Not Equal</span></span>

<span data-ttu-id="5ed0a-141">更多詳細資料，這些函式[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="5ed0a-141">More details on these functions are [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="5ed0a-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ed0a-142">See Also</span></span>  
- [<span data-ttu-id="5ed0a-143">如何新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="5ed0a-143">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
- <span data-ttu-id="5ed0a-144">**邏輯運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed0a-144">**Logical Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
