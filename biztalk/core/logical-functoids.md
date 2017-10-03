---
title: "邏輯運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e37cdfc3-66de-4333-84eb-a8765afa8407
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7907d1045fde39d5ece963bd78e00d027e8a9da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="logical-functoids"></a><span data-ttu-id="1835a-102">邏輯運算質</span><span class="sxs-lookup"><span data-stu-id="1835a-102">Logical Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="1835a-103">概觀</span><span class="sxs-lookup"><span data-stu-id="1835a-103">Overview</span></span>
<span data-ttu-id="1835a-104">**邏輯**運算質可用以執行下列類型的作業：</span><span class="sxs-lookup"><span data-stu-id="1835a-104">**Logical** functoids are used to perform the following types of operations:</span></span>  
  
-   <span data-ttu-id="1835a-105">在執行階段執行特定邏輯測試。</span><span class="sxs-lookup"><span data-stu-id="1835a-105">Perform specific logical tests at run time.</span></span> <span data-ttu-id="1835a-106">**邏輯 OR**，**邏輯 NOT**和**邏輯和**運算質可以用來判斷是否記錄建立在目的地執行個體訊息中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1835a-106">The **Logical OR**, **Logical NOT** and **Logical AND** functoids can be used to determine whether a record is created in a destination instance message, such as the following:</span></span>  
  
     <span data-ttu-id="1835a-107">如果 ShipTo**或**orderedby 存在，請建立 billto 地址記錄。</span><span class="sxs-lookup"><span data-stu-id="1835a-107">If ShipTo **OR** OrderedBy are present, create BillTo address record.</span></span>  
  
     <span data-ttu-id="1835a-108">您也可以使用這些運算質搭配**迴圈**設定多少次記錄迴圈運算質。</span><span class="sxs-lookup"><span data-stu-id="1835a-108">You can also use these functoids in conjunction with the **Looping** functoid to configure how many times a record loops.</span></span>  
  
-   <span data-ttu-id="1835a-109">控制是否在執行階段於目的執行個體訊息中建立特定記錄。</span><span class="sxs-lookup"><span data-stu-id="1835a-109">Control whether a specific record is created in a destination instance message at run time.</span></span> <span data-ttu-id="1835a-110">這類運算質**IsNil**，**邏輯數字**，**小於**，和**Greater Than**可用來控制是否建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="1835a-110">Functoids such as **IsNil**, **Logical Numeric**, **Less Than**, and **Greater Than** can be used to control whether a record is created.</span></span>  
  
     <span data-ttu-id="1835a-111">如果其中一個這些邏輯運算質的結果會是**True**，就會產生目的地執行個體訊息中對應的記錄。</span><span class="sxs-lookup"><span data-stu-id="1835a-111">If the result of one of these logical functoids is **True**, the corresponding record in the destination instance message is generated.</span></span> <span data-ttu-id="1835a-112">如果結果為**False**，不會產生目的執行個體訊息中的對應記錄。</span><span class="sxs-lookup"><span data-stu-id="1835a-112">If the result is **False**, the corresponding record in the destination instance message is not generated.</span></span>  
  
 <span data-ttu-id="1835a-113">運算質**IsNil**，**邏輯日期**，**存在**，**邏輯 NOT**，**邏輯數字**，和**邏輯字串**只接受一個參數。</span><span class="sxs-lookup"><span data-stu-id="1835a-113">The functoids **IsNil**, **Logical Date**, **Logical Existence**, **Logical NOT**, **Logical Numeric**, and **Logical String** accept only one parameter.</span></span> <span data-ttu-id="1835a-114">運算質**等於**， **Greater Than**， **Greater Than 或 Equal To**，**小於**，**小於或等於**，和**不等於**接受兩個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="1835a-114">The functoids **Equal**, **Greater Than**, **Greater Than or Equal To**, **Less Than**, **Less Than or Equal To**, and **Not Equal** accept two input parameters.</span></span> <span data-ttu-id="1835a-115">而、**邏輯和**和**邏輯 OR**運算質接受 2 到 100 個輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="1835a-115">Whereas, the **Logical AND** and **Logical OR** functoids accept input parameters between 2 and 100.</span></span>  
  
 <span data-ttu-id="1835a-116">輸出**邏輯**運算質也可以接受做為對應中的其他運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="1835a-116">The output of a **Logical** functoid can also be accepted as input to other functoids in a map.</span></span> <span data-ttu-id="1835a-117">如果兩個**邏輯**運算質與迴圈運算質會連結在一起，並接著連結到目的結構描述中的記錄，迴圈運算質時，才**邏輯**運算質的輸出，則為**True**。</span><span class="sxs-lookup"><span data-stu-id="1835a-117">If both a **Logical** functoid and a looping functoid are linked together, and then linked to a record in the destination schema, the looping functoid is used only when the **Logical** functoid output is **True**.</span></span>  
  
 <span data-ttu-id="1835a-118">您也可以使用**邏輯**運算質**值對應**或**值對應 （簡維）**運算質來控制是否在目的執行個體訊息中的記錄會建立。</span><span class="sxs-lookup"><span data-stu-id="1835a-118">You can also use **Logical** functoids with the **Value Mapping** or **Value Mapping (Flattening)** functoids to control whether a record in the destination instance message is created.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1835a-119">如果兩個記錄或欄位在來源結構描述中的連結到兩個不同**邏輯**運算質，然後將每個連結**邏輯**相同記錄與目的結構描述中，運算質的第一個**邏輯**運算質使用中產生可延伸樣式表語言轉換 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="1835a-119">If you link two records or fields in the source schema to two different **Logical** functoids, and then link each of the **Logical** functoids to the same record in the destination schema, only the first **Logical** functoid is used in the generated Extensible Stylesheet Language Transformations (XSLT).</span></span> <span data-ttu-id="1835a-120">第二個連結，第二個**邏輯**運算質，則會忽略。</span><span class="sxs-lookup"><span data-stu-id="1835a-120">The second link, from the second **Logical** functoid, is ignored.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1835a-121">在比較兩個字串時，邏輯運算質是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="1835a-121">Logical functoids are case-sensitive when comparing two strings.</span></span> <span data-ttu-id="1835a-122">例如，"Abc" 與 "abc" 不相等。</span><span class="sxs-lookup"><span data-stu-id="1835a-122">For example, "Abc" and "abc" are not equal.</span></span> <span data-ttu-id="1835a-123">此規則的例外狀況是當**邏輯**運算質代表布林值的字串比較**True**和**False**。</span><span class="sxs-lookup"><span data-stu-id="1835a-123">The exception to this rule is when **Logical** functoids compare strings that represent the Boolean values **True** and **False**.</span></span> <span data-ttu-id="1835a-124">例如，"True" 與 "true" 相等。</span><span class="sxs-lookup"><span data-stu-id="1835a-124">For example, "True" and "true" are equal.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="1835a-125">可用的運算質</span><span class="sxs-lookup"><span data-stu-id="1835a-125">Available functoids</span></span>  
 <span data-ttu-id="1835a-126">**邏輯**運算質為：</span><span class="sxs-lookup"><span data-stu-id="1835a-126">The **Logical** functoids are:</span></span> 

* <span data-ttu-id="1835a-127">等於</span><span class="sxs-lookup"><span data-stu-id="1835a-127">Equal</span></span>
* <span data-ttu-id="1835a-128">大於</span><span class="sxs-lookup"><span data-stu-id="1835a-128">Greater Than</span></span>
* <span data-ttu-id="1835a-129">大於或等於</span><span class="sxs-lookup"><span data-stu-id="1835a-129">Greater Than or Equal To</span></span>
* <span data-ttu-id="1835a-130">IsNil</span><span class="sxs-lookup"><span data-stu-id="1835a-130">IsNil</span></span>
* <span data-ttu-id="1835a-131">小於</span><span class="sxs-lookup"><span data-stu-id="1835a-131">Less Than</span></span>
* <span data-ttu-id="1835a-132">小於或等於</span><span class="sxs-lookup"><span data-stu-id="1835a-132">Less Than or Equal To</span></span>
* <span data-ttu-id="1835a-133">邏輯 AND</span><span class="sxs-lookup"><span data-stu-id="1835a-133">Logical AND</span></span>
* <span data-ttu-id="1835a-134">日期</span><span class="sxs-lookup"><span data-stu-id="1835a-134">Logical Date</span></span>
* <span data-ttu-id="1835a-135">存在</span><span class="sxs-lookup"><span data-stu-id="1835a-135">Logical Existence</span></span>
* <span data-ttu-id="1835a-136">邏輯 NOT</span><span class="sxs-lookup"><span data-stu-id="1835a-136">Logical NOT</span></span>
* <span data-ttu-id="1835a-137">數字</span><span class="sxs-lookup"><span data-stu-id="1835a-137">Logical Numeric</span></span>
* <span data-ttu-id="1835a-138">邏輯 OR</span><span class="sxs-lookup"><span data-stu-id="1835a-138">Logical OR</span></span>
* <span data-ttu-id="1835a-139">字串</span><span class="sxs-lookup"><span data-stu-id="1835a-139">Logical String</span></span>
* <span data-ttu-id="1835a-140">Not Equal</span><span class="sxs-lookup"><span data-stu-id="1835a-140">Not Equal</span></span>

<span data-ttu-id="1835a-141">如需詳細資訊，這些函式[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="1835a-141">More details on these functions are [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1835a-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1835a-142">See Also</span></span>  
-  [<span data-ttu-id="1835a-143">如何新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="1835a-143">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
-  <span data-ttu-id="1835a-144">**邏輯運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="1835a-144">**Logical Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>