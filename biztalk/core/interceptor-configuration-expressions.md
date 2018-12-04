---
title: 攔截器組態運算式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2695f509-fece-40b8-aa00-fa3c0c0f19c5
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae6cc008e1e8b6acad53c2fcebd59160931cdc96
ms.sourcegitcommit: be6273d612669adfbb9dc9208aaae0a8437d4017
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2018
ms.locfileid: "52826294"
---
# <a name="interceptor-configuration-expressions"></a><span data-ttu-id="0b74d-102">攔截器組態運算式</span><span class="sxs-lookup"><span data-stu-id="0b74d-102">Interceptor Configuration Expressions</span></span>
<span data-ttu-id="0b74d-103">BAM 攔截器組態檔使用篩選條件運算式識別活動，並使用資料運算式建構資料項目，用於儲存體，做為相互關聯識別碼或接續 token、 或類似的目的。</span><span class="sxs-lookup"><span data-stu-id="0b74d-103">The BAM interceptor configuration file uses filter expressions to identify an activity and uses data expressions to construct a data element for storage, use as a correlation ID or continuation token, or similar purpose.</span></span> <span data-ttu-id="0b74d-104">無論目的為何，個別運算式是透過 `expression` 項目在攔截器組態檔中識別，並且包含一或多項使用 Reverse Polish Notation (亦稱為 Postfix 標記法) 的作業。</span><span class="sxs-lookup"><span data-stu-id="0b74d-104">Regardless of the purpose, individual expressions are identified in the interceptor configuration file by the `expression` element and contain one or more operations using Reverse Polish Notation, also known as postfix notation.</span></span>  
  
## <a name="about-reverse-polish-notation"></a><span data-ttu-id="0b74d-105">關於 Reverse Polish Notation</span><span class="sxs-lookup"><span data-stu-id="0b74d-105">About Reverse Polish Notation</span></span>  
 <span data-ttu-id="0b74d-106">在 Reverse Polish Notation (RPN) 中，運算元優先於運算子，因此不需要使用括號做為優先順序運算子。</span><span class="sxs-lookup"><span data-stu-id="0b74d-106">In Reverse Polish Notation (RPN), operands precede the operator, thereby removing the need to use parentheses as precedence operators.</span></span> <span data-ttu-id="0b74d-107">堆疊是用來保留值和所有作業，包括將值推入堆疊、顯示 (移除) 來自堆疊的值，或是執行推入和顯示的組合動作來完成作業。</span><span class="sxs-lookup"><span data-stu-id="0b74d-107">A stack is used to hold values and all operations either push values onto the stack, pop (remove) values from the stack, or perform a combination of pushes and pops to complete an operation.</span></span>  
  
 <span data-ttu-id="0b74d-108">例如，如果您要評估運算式</span><span class="sxs-lookup"><span data-stu-id="0b74d-108">For example, if you wanted to evaluate the expression</span></span>  
  
 `5 + (10 - 2)`  
  
 <span data-ttu-id="0b74d-109">將此運算式轉換成同等的 RPN 會得出</span><span class="sxs-lookup"><span data-stu-id="0b74d-109">Converting this to the equivalent RPN results in</span></span>  
  
 `5 10 2 - +`  
  
 <span data-ttu-id="0b74d-110">評估結果如下：</span><span class="sxs-lookup"><span data-stu-id="0b74d-110">This would be evaluated as follows:</span></span>  
  
|<span data-ttu-id="0b74d-111">輸入</span><span class="sxs-lookup"><span data-stu-id="0b74d-111">Input</span></span>|<span data-ttu-id="0b74d-112">作業</span><span class="sxs-lookup"><span data-stu-id="0b74d-112">Operation</span></span>|<span data-ttu-id="0b74d-113">堆疊</span><span class="sxs-lookup"><span data-stu-id="0b74d-113">Stack</span></span>|  
|-----------|---------------|-----------|  
|<span data-ttu-id="0b74d-114">5</span><span class="sxs-lookup"><span data-stu-id="0b74d-114">5</span></span>|<span data-ttu-id="0b74d-115">發送</span><span class="sxs-lookup"><span data-stu-id="0b74d-115">Push</span></span>|<span data-ttu-id="0b74d-116">5</span><span class="sxs-lookup"><span data-stu-id="0b74d-116">5</span></span>|  
|<span data-ttu-id="0b74d-117">10</span><span class="sxs-lookup"><span data-stu-id="0b74d-117">10</span></span>|<span data-ttu-id="0b74d-118">發送</span><span class="sxs-lookup"><span data-stu-id="0b74d-118">Push</span></span>|<span data-ttu-id="0b74d-119">5, 10</span><span class="sxs-lookup"><span data-stu-id="0b74d-119">5, 10</span></span>|  
|<span data-ttu-id="0b74d-120">2</span><span class="sxs-lookup"><span data-stu-id="0b74d-120">2</span></span>|<span data-ttu-id="0b74d-121">發送</span><span class="sxs-lookup"><span data-stu-id="0b74d-121">Push</span></span>|<span data-ttu-id="0b74d-122">5, 10, 2</span><span class="sxs-lookup"><span data-stu-id="0b74d-122">5, 10, 2</span></span>|  
|-|<span data-ttu-id="0b74d-123">減</span><span class="sxs-lookup"><span data-stu-id="0b74d-123">Subtract</span></span>|<span data-ttu-id="0b74d-124">5, 8</span><span class="sxs-lookup"><span data-stu-id="0b74d-124">5, 8</span></span>|  
|+|<span data-ttu-id="0b74d-125">加入</span><span class="sxs-lookup"><span data-stu-id="0b74d-125">Add</span></span>|<span data-ttu-id="0b74d-126">13</span><span class="sxs-lookup"><span data-stu-id="0b74d-126">13</span></span>|  
  
 <span data-ttu-id="0b74d-127">假如 RPN 系統支援字串串連作業，那麼您也可以評估運算式</span><span class="sxs-lookup"><span data-stu-id="0b74d-127">Assuming the RPN system supported the string concatenate operation, you could also evaluate the expression</span></span>  
  
 `"The quick brown " + "fox " + "jumped over the lazy " + "dog."`  
  
 <span data-ttu-id="0b74d-128">將此運算式轉換成同等的 RPN 標記法會產生：</span><span class="sxs-lookup"><span data-stu-id="0b74d-128">Converting this to the equivalent RPN notation yields:</span></span>  
  
 `"The quick brown " "fox " "jumped over the lazy " "dog" + + +`  
  
 <span data-ttu-id="0b74d-129">評估結果如下：</span><span class="sxs-lookup"><span data-stu-id="0b74d-129">This would be evaluated as follows:</span></span>  
  
|<span data-ttu-id="0b74d-130">輸入</span><span class="sxs-lookup"><span data-stu-id="0b74d-130">Input</span></span>|<span data-ttu-id="0b74d-131">作業</span><span class="sxs-lookup"><span data-stu-id="0b74d-131">Operation</span></span>|<span data-ttu-id="0b74d-132">堆疊</span><span class="sxs-lookup"><span data-stu-id="0b74d-132">Stack</span></span>|  
|-----------|---------------|-----------|  
|<span data-ttu-id="0b74d-133">"The quick brown"</span><span class="sxs-lookup"><span data-stu-id="0b74d-133">"The quick brown"</span></span>|<span data-ttu-id="0b74d-134">發送</span><span class="sxs-lookup"><span data-stu-id="0b74d-134">Push</span></span>|<span data-ttu-id="0b74d-135">「 快速 brown"</span><span class="sxs-lookup"><span data-stu-id="0b74d-135">"The quick brown "</span></span>|  
|<span data-ttu-id="0b74d-136">"fox"</span><span class="sxs-lookup"><span data-stu-id="0b74d-136">"fox"</span></span>|<span data-ttu-id="0b74d-137">發送</span><span class="sxs-lookup"><span data-stu-id="0b74d-137">Push</span></span>|<span data-ttu-id="0b74d-138">"The quick brown ", "fox "</span><span class="sxs-lookup"><span data-stu-id="0b74d-138">"The quick brown ", "fox "</span></span>|  
|<span data-ttu-id="0b74d-139">"jumped over the lazy"</span><span class="sxs-lookup"><span data-stu-id="0b74d-139">"jumped over the lazy"</span></span>|<span data-ttu-id="0b74d-140">發送</span><span class="sxs-lookup"><span data-stu-id="0b74d-140">Push</span></span>|<span data-ttu-id="0b74d-141">"The quick brown ", "fox ", "jumped over the lazy "</span><span class="sxs-lookup"><span data-stu-id="0b74d-141">"The quick brown ", "fox ", "jumped over the lazy "</span></span>|  
|<span data-ttu-id="0b74d-142">"dog."</span><span class="sxs-lookup"><span data-stu-id="0b74d-142">"dog."</span></span>|<span data-ttu-id="0b74d-143">發送</span><span class="sxs-lookup"><span data-stu-id="0b74d-143">Push</span></span>|<span data-ttu-id="0b74d-144">"The quick brown ", "fox ", "jumped over the lazy ", "dog."</span><span class="sxs-lookup"><span data-stu-id="0b74d-144">"The quick brown ", "fox ", "jumped over the lazy ", "dog."</span></span>|  
|+|<span data-ttu-id="0b74d-145">串連</span><span class="sxs-lookup"><span data-stu-id="0b74d-145">Concatenate</span></span>|<span data-ttu-id="0b74d-146">"The quick brown ", "fox ", "jumped over the lazy dog."</span><span class="sxs-lookup"><span data-stu-id="0b74d-146">"The quick brown ", "fox ", "jumped over the lazy dog."</span></span>|  
|+|<span data-ttu-id="0b74d-147">串連</span><span class="sxs-lookup"><span data-stu-id="0b74d-147">Concatenate</span></span>|<span data-ttu-id="0b74d-148">"The quick brown ", "fox jumped over the lazy dog."</span><span class="sxs-lookup"><span data-stu-id="0b74d-148">"The quick brown ", "fox jumped over the lazy dog."</span></span>|  
|+|<span data-ttu-id="0b74d-149">串連</span><span class="sxs-lookup"><span data-stu-id="0b74d-149">Concatenate</span></span>|<span data-ttu-id="0b74d-150">"The quick brown fox jumped over the lazy dog."</span><span class="sxs-lookup"><span data-stu-id="0b74d-150">"The quick brown fox jumped over the lazy dog."</span></span>|  
  
 <span data-ttu-id="0b74d-151">如您所見，任意數目的作業都可支援，包括比較、布林值作業，以及擷取適合本身所參與作業之值的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="0b74d-151">As you can see, an arbitrary number of operations can be supported, including comparison, Boolean operations, and custom operations that retrieve values appropriate for the operations in which they participate.</span></span> <span data-ttu-id="0b74d-152">值會在堆疊上累積，並且根據個別作業推入和顯示。</span><span class="sxs-lookup"><span data-stu-id="0b74d-152">Values accumulate on the stack and are pushed and popped according to individual operations.</span></span>  
  
## <a name="reverse-polish-notation-in-the-interceptor-configuration-file"></a><span data-ttu-id="0b74d-153">攔截器組態檔中的 Reverse Polish Notation</span><span class="sxs-lookup"><span data-stu-id="0b74d-153">Reverse Polish Notation in the Interceptor Configuration File</span></span>  
 <span data-ttu-id="0b74d-154">您會撰寫兩種類型的運算式中的攔截器組態檔： 篩選運算式和資料運算式。</span><span class="sxs-lookup"><span data-stu-id="0b74d-154">You will write two kinds of expressions in the interceptor configuration file: filter expressions and data expressions.</span></span> <span data-ttu-id="0b74d-155">篩選條件運算式要求 RPN 運算式的結果必須為布林值 `true` 或 `false`，而資料運算式則要求堆疊上只有單一值。</span><span class="sxs-lookup"><span data-stu-id="0b74d-155">Filter expressions expect the result of the RPN expression to be a Boolean `true` or `false` while data expressions expect a single value on the stack.</span></span>  
  
### <a name="filter-expressions"></a><span data-ttu-id="0b74d-156">篩選條件運算式</span><span class="sxs-lookup"><span data-stu-id="0b74d-156">Filter Expressions</span></span>  
 <span data-ttu-id="0b74d-157">篩選條件運算式會評估為布林值 `true` 或 `false`，並且用來識別 WF 或 WFC 應用程式中要追蹤的特定事件。</span><span class="sxs-lookup"><span data-stu-id="0b74d-157">Filter expressions evaluate to Boolean `true` or `false` and are used to identify a specific event to track in the WF or WFC application.</span></span> <span data-ttu-id="0b74d-158">在 WF 應用程式中，通常會根據活動名稱或事件進行篩選。</span><span class="sxs-lookup"><span data-stu-id="0b74d-158">In WF applications, it is common to filter based on activity name and event.</span></span> <span data-ttu-id="0b74d-159">例如，您可能想要選取**FoodAndDrinksPolicy**活動時**Closed**。</span><span class="sxs-lookup"><span data-stu-id="0b74d-159">For example, you may want to select the **FoodAndDrinksPolicy** activity when it is **Closed**.</span></span> <span data-ttu-id="0b74d-160">若使用 WF 作業，您就可以表示篩選條件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0b74d-160">Using WF operations, you could express the filter as:</span></span>  
  
 `(GetActivityName = "FoodAndDrinksPolicy") && (GetActivityEvent = "Closed")`  
  
 <span data-ttu-id="0b74d-161">將此運算式轉換成 RPN 會產生：</span><span class="sxs-lookup"><span data-stu-id="0b74d-161">Converting this to RPN yields:</span></span>  
  
 `GetActivityName "FoodAndDrinksPolicy" == GetActivityEvent "Closed" == &&`  
  
 <span data-ttu-id="0b74d-162">將此運算式轉換成適用攔截器組態檔的同等運算式，會得出下列 XML：</span><span class="sxs-lookup"><span data-stu-id="0b74d-162">Converting this expression to the equivalent expression for the interceptor configuration file results in the following XML:</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="0b74d-163">最後，此運算式會進行評估，如下所示假設**GetActivityName**傳回"DessertPolicy"並**GetActivityEvent**傳回"Closed":</span><span class="sxs-lookup"><span data-stu-id="0b74d-163">Finally, this expression would be evaluated as follows assuming **GetActivityName** returned "DessertPolicy" and **GetActivityEvent** returned "Closed":</span></span>  
  
|<span data-ttu-id="0b74d-164">輸入</span><span class="sxs-lookup"><span data-stu-id="0b74d-164">Input</span></span>|<span data-ttu-id="0b74d-165">作業</span><span class="sxs-lookup"><span data-stu-id="0b74d-165">Operation</span></span>|<span data-ttu-id="0b74d-166">堆疊</span><span class="sxs-lookup"><span data-stu-id="0b74d-166">Stack</span></span>|  
|-----------|---------------|-----------|  
||<span data-ttu-id="0b74d-167">GetActivityName</span><span class="sxs-lookup"><span data-stu-id="0b74d-167">GetActivityName</span></span>|<span data-ttu-id="0b74d-168">"DessertPolicy"</span><span class="sxs-lookup"><span data-stu-id="0b74d-168">"DessertPolicy"</span></span>|  
|<span data-ttu-id="0b74d-169">"FoodAndDrinksPolicy"</span><span class="sxs-lookup"><span data-stu-id="0b74d-169">"FoodAndDrinksPolicy"</span></span>|<span data-ttu-id="0b74d-170">常數</span><span class="sxs-lookup"><span data-stu-id="0b74d-170">Constant</span></span>|<span data-ttu-id="0b74d-171">"DessertPolicy", "FoodAndDrinksPolicy"</span><span class="sxs-lookup"><span data-stu-id="0b74d-171">"DessertPolicy", "FoodAndDrinksPolicy"</span></span>|  
|<span data-ttu-id="0b74d-172">等於</span><span class="sxs-lookup"><span data-stu-id="0b74d-172">Equals</span></span>|<span data-ttu-id="0b74d-173">比較</span><span class="sxs-lookup"><span data-stu-id="0b74d-173">Comparison</span></span>|<span data-ttu-id="0b74d-174">False</span><span class="sxs-lookup"><span data-stu-id="0b74d-174">False</span></span>|  
||<span data-ttu-id="0b74d-175">GetActivityEvent</span><span class="sxs-lookup"><span data-stu-id="0b74d-175">GetActivityEvent</span></span>|<span data-ttu-id="0b74d-176">False, Closed</span><span class="sxs-lookup"><span data-stu-id="0b74d-176">False, Closed</span></span>|  
|<span data-ttu-id="0b74d-177">"Closed"</span><span class="sxs-lookup"><span data-stu-id="0b74d-177">"Closed"</span></span>|<span data-ttu-id="0b74d-178">常數</span><span class="sxs-lookup"><span data-stu-id="0b74d-178">Constant</span></span>|<span data-ttu-id="0b74d-179">False, "Closed", "Closed"</span><span class="sxs-lookup"><span data-stu-id="0b74d-179">False, "Closed", "Closed"</span></span>|  
|<span data-ttu-id="0b74d-180">等於</span><span class="sxs-lookup"><span data-stu-id="0b74d-180">Equals</span></span>|<span data-ttu-id="0b74d-181">比較</span><span class="sxs-lookup"><span data-stu-id="0b74d-181">Comparison</span></span>|<span data-ttu-id="0b74d-182">False, True</span><span class="sxs-lookup"><span data-stu-id="0b74d-182">False, True</span></span>|  
|<span data-ttu-id="0b74d-183">And</span><span class="sxs-lookup"><span data-stu-id="0b74d-183">And</span></span>|<span data-ttu-id="0b74d-184">邏輯 And</span><span class="sxs-lookup"><span data-stu-id="0b74d-184">Logical And</span></span>|<span data-ttu-id="0b74d-185">False</span><span class="sxs-lookup"><span data-stu-id="0b74d-185">False</span></span>|  
  
 <span data-ttu-id="0b74d-186">留在堆疊上的值為布林值 `False`。</span><span class="sxs-lookup"><span data-stu-id="0b74d-186">The value left on the stack is Boolean `False`.</span></span> <span data-ttu-id="0b74d-187">這樣將不會引發對應的事件。</span><span class="sxs-lookup"><span data-stu-id="0b74d-187">This will cause the corresponding event to not fire.</span></span> <span data-ttu-id="0b74d-188">如果活動名稱為 "FoodAndDrinksPolicy"，則可能會評估為布林值 `True`。</span><span class="sxs-lookup"><span data-stu-id="0b74d-188">If the activity name were "FoodAndDrinksPolicy" then it would have evaluated to Boolean `True`.</span></span>  
  
 <span data-ttu-id="0b74d-189">您可以使用 WCF 作業 `GetEndpointName` 和 `GetOperationName`，建構類似的運算式 (與類似的評估)。</span><span class="sxs-lookup"><span data-stu-id="0b74d-189">You can construct a similar expression (with a similar evaluation) by using the WCF operations `GetEndpointName` and `GetOperationName`.</span></span>  
  
### <a name="data-expressions"></a><span data-ttu-id="0b74d-190">資料運算式</span><span class="sxs-lookup"><span data-stu-id="0b74d-190">Data Expressions</span></span>  
 <span data-ttu-id="0b74d-191">資料運算式是用來定義單一字串資料值。</span><span class="sxs-lookup"><span data-stu-id="0b74d-191">Data expressions are used to define a single string data value.</span></span> <span data-ttu-id="0b74d-192">資料運算式是未包含在 `Filter` 項目內的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="0b74d-192">A data expression is any expression that is not enclosed by a `Filter` element.</span></span> <span data-ttu-id="0b74d-193">資料運算式為 `OnEvent` 項目所使用，包括 `CorrelationID`、`ContinuationToken`、`Reference` 和 `Update`。</span><span class="sxs-lookup"><span data-stu-id="0b74d-193">Data expressions are used by the `OnEvent` elements `CorrelationID`, `ContinuationToken`, `Reference`, and `Update`.</span></span>  
  
 <span data-ttu-id="0b74d-194">BAM 活動資料庫通常必須更新並且標示時間戳記。</span><span class="sxs-lookup"><span data-stu-id="0b74d-194">It is a common requirement to update the BAM activity database with a labeled time stamp.</span></span> <span data-ttu-id="0b74d-195">例如，您可能想要擷取事件開始格式化為字串的時間 」 開始： \<EventTime\>"。</span><span class="sxs-lookup"><span data-stu-id="0b74d-195">For example, you might want to capture the time an event starts with a string formatted as "Start: \<EventTime\>".</span></span> <span data-ttu-id="0b74d-196">若要執行這項操作，您必須使用類似下方的運算式 (其中 + 代表串連)：</span><span class="sxs-lookup"><span data-stu-id="0b74d-196">To do this, you need to use an expression similar to the following (where + represents concatenation):</span></span>  
  
 `"Start: " + GetContextProperty(EventTime)`  
  
 <span data-ttu-id="0b74d-197">將此運算式轉換成 RPN 會產生：</span><span class="sxs-lookup"><span data-stu-id="0b74d-197">Converting this to RPN yields:</span></span>  
  
 `"Start: " GetContextProperty(EventTime) +`  
  
 <span data-ttu-id="0b74d-198">將此運算式轉換成適用攔截器組態檔中 `Update` 項目的同等運算式，會得出下列 XML：</span><span class="sxs-lookup"><span data-stu-id="0b74d-198">Converting this expression to the equivalent expression for an `Update` element in the interceptor configuration file results in the following XML:</span></span>  
  
```  
<ic:Update DataItemName="NewOrderCreateTime" Type="NVARCHAR">  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Start:</ic:Argument>  
    </ic:Operation>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:Update>  
```  
  
 <span data-ttu-id="0b74d-199">下表說明事件時間為 "12:00 PM" 時，如何解譯此運算式。</span><span class="sxs-lookup"><span data-stu-id="0b74d-199">The following table shows how this expression would be interpreted if the event time was "12:00 PM".</span></span>  
  
|<span data-ttu-id="0b74d-200">輸入</span><span class="sxs-lookup"><span data-stu-id="0b74d-200">Input</span></span>|<span data-ttu-id="0b74d-201">作業</span><span class="sxs-lookup"><span data-stu-id="0b74d-201">Operation</span></span>|<span data-ttu-id="0b74d-202">堆疊</span><span class="sxs-lookup"><span data-stu-id="0b74d-202">Stack</span></span>|  
|-----------|---------------|-----------|  
|<span data-ttu-id="0b74d-203">「 啟動: 」</span><span class="sxs-lookup"><span data-stu-id="0b74d-203">"Start: "</span></span>|<span data-ttu-id="0b74d-204">常數</span><span class="sxs-lookup"><span data-stu-id="0b74d-204">Constant</span></span>|<span data-ttu-id="0b74d-205">「 啟動: 」</span><span class="sxs-lookup"><span data-stu-id="0b74d-205">"Start: "</span></span>|  
|<span data-ttu-id="0b74d-206">GetContextProperty(EventTime)</span><span class="sxs-lookup"><span data-stu-id="0b74d-206">GetContextProperty(EventTime)</span></span>|<span data-ttu-id="0b74d-207">發送</span><span class="sxs-lookup"><span data-stu-id="0b74d-207">Push</span></span>|<span data-ttu-id="0b74d-208">「 啟動:"，"2006年-09-27T12:00:34.000Z"</span><span class="sxs-lookup"><span data-stu-id="0b74d-208">"Start: ", "2006-09-27T12:00:34.000Z"</span></span>|  
|<span data-ttu-id="0b74d-209">串連</span><span class="sxs-lookup"><span data-stu-id="0b74d-209">Concatenate</span></span>|<span data-ttu-id="0b74d-210">串連</span><span class="sxs-lookup"><span data-stu-id="0b74d-210">Concatenate</span></span>|<span data-ttu-id="0b74d-211">「 啟動： 2006年-09-27T12:00:34.000Z"</span><span class="sxs-lookup"><span data-stu-id="0b74d-211">"Start: 2006-09-27T12:00:34.000Z"</span></span>|  
  
 <span data-ttu-id="0b74d-212">更新命令所使用的值會是 「 啟動： 2006年-09-27T12:00:34.000Z"。</span><span class="sxs-lookup"><span data-stu-id="0b74d-212">The value used by the update command would be "Start: 2006-09-27T12:00:34.000Z".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b74d-213">請不要在資料運算式中使用比較作業 "And" 或 "Equals"。</span><span class="sxs-lookup"><span data-stu-id="0b74d-213">Do not use the comparison operations "And" or "Equals" in data expressions.</span></span> <span data-ttu-id="0b74d-214">如果您使用比較作業的話，將在部署攔截器組態檔時收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="0b74d-214">If you do, you will receive an error when deploying your interceptor configuration file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b74d-215">本節內容</span><span class="sxs-lookup"><span data-stu-id="0b74d-215">In This Section</span></span>  
 [<span data-ttu-id="0b74d-216">攔截器作業</span><span class="sxs-lookup"><span data-stu-id="0b74d-216">Interceptor Operations</span></span>](../core/interceptor-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="0b74d-217">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b74d-217">See Also</span></span>  
 [<span data-ttu-id="0b74d-218">攔截器設定檔的結構</span><span class="sxs-lookup"><span data-stu-id="0b74d-218">Structure of an Interceptor Configuration File</span></span>](../core/structure-of-an-interceptor-configuration-file.md)
