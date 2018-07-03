---
title: 商務規則的原則測試追蹤輸出資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing, business rules
- testing, policies
- business rules, testing
- policies, testing
ms.assetid: 26ff584e-97a1-4d76-a8a9-a55b4c99231f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8795e926d496f586d032bb85fe4a1fddb473ec5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005135"
---
# <a name="policy-test-trace-output-information-for-business-rules"></a><span data-ttu-id="2ee03-102">商務規則的原則測試追蹤輸出資訊</span><span class="sxs-lookup"><span data-stu-id="2ee03-102">Policy Test Trace Output Information for Business Rules</span></span>
<span data-ttu-id="2ee03-103">本節提供在「商務規則編輯器」中測試原則時所顯示的追蹤資訊之相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2ee03-103">This section provides information on the tracking information that is displayed when testing a policy in the Business Rule Composer.</span></span> <span data-ttu-id="2ee03-104">檢視使用 [群組中樞] 頁面上追蹤查詢的訊息事件和服務執行個體的原則執行的追蹤結果時，會看到類似的資訊。</span><span class="sxs-lookup"><span data-stu-id="2ee03-104">Very similar information is seen when viewing tracking results for policy execution using the message event and service instance tracking queries on the Group Hub page.</span></span>  
  
 <span data-ttu-id="2ee03-105">追蹤輸出會顯示下列四種陳述式類型：</span><span class="sxs-lookup"><span data-stu-id="2ee03-105">There are four statement types that are displayed in the tracking output:</span></span>  
  
- <span data-ttu-id="2ee03-106">事實活動</span><span class="sxs-lookup"><span data-stu-id="2ee03-106">Fact Activity</span></span>  
  
- <span data-ttu-id="2ee03-107">條件評估</span><span class="sxs-lookup"><span data-stu-id="2ee03-107">Condition Evaluation</span></span>  
  
- <span data-ttu-id="2ee03-108">議程更新</span><span class="sxs-lookup"><span data-stu-id="2ee03-108">Agenda Update</span></span>  
  
- <span data-ttu-id="2ee03-109">規則被引發</span><span class="sxs-lookup"><span data-stu-id="2ee03-109">Rule Fired</span></span>  
  
  <span data-ttu-id="2ee03-110">下面內容將介紹每種陳述式類型。</span><span class="sxs-lookup"><span data-stu-id="2ee03-110">Each statement type is described below.</span></span>  
  
## <a name="fact-activity"></a><span data-ttu-id="2ee03-111">事實活動</span><span class="sxs-lookup"><span data-stu-id="2ee03-111">Fact Activity</span></span>  
 <span data-ttu-id="2ee03-112">這個陳述式指示引擎的工作記憶體中的事實變更。</span><span class="sxs-lookup"><span data-stu-id="2ee03-112">This statement indicates changes to the facts present in the working memory of the engine.</span></span> <span data-ttu-id="2ee03-113">以下為事實活動項目的範例：</span><span class="sxs-lookup"><span data-stu-id="2ee03-113">The following is an example of a fact activity entry:</span></span>  
  
```  
FACT ACTIVITY 3/16/2004 9:50:28 AM  
Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7  
Ruleset Name: LoanProcessing  
Operation: Assert  
Object Type: MyTest.test  
Object Instance Identifier: 872  
```  
  
### <a name="rule-engine-instance-identifier"></a><span data-ttu-id="2ee03-114">規則引擎執行個體識別項</span><span class="sxs-lookup"><span data-stu-id="2ee03-114">Rule Engine Instance Identifier</span></span>  
 <span data-ttu-id="2ee03-115">唯一識別項**RuleEngine**提供規則引發的執行環境的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2ee03-115">Unique identifier for the **RuleEngine** instance that provides the execution environment for the rule firing.</span></span>  
  
### <a name="ruleset-name"></a><span data-ttu-id="2ee03-116">規則集名稱</span><span class="sxs-lookup"><span data-stu-id="2ee03-116">Ruleset Name</span></span>  
 <span data-ttu-id="2ee03-117">規則集 (原則) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ee03-117">The name of the rule set (policy).</span></span>  
  
### <a name="operation"></a><span data-ttu-id="2ee03-118">作業</span><span class="sxs-lookup"><span data-stu-id="2ee03-118">Operation</span></span>  
 <span data-ttu-id="2ee03-119">事實活動可能會進行以下三種作業：</span><span class="sxs-lookup"><span data-stu-id="2ee03-119">There are three types of operation that can occur in a fact activity:</span></span>  
  
 <span data-ttu-id="2ee03-120">判斷提示</span><span class="sxs-lookup"><span data-stu-id="2ee03-120">Assert</span></span>  
  
 <span data-ttu-id="2ee03-121">事實加入工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="2ee03-121">The fact is being added to the working memory.</span></span>  
  
 <span data-ttu-id="2ee03-122">Update</span><span class="sxs-lookup"><span data-stu-id="2ee03-122">Update</span></span>  
  
 <span data-ttu-id="2ee03-123">事實由規則更新，然後需要重新判斷提示，根據新的日期和狀態在引擎重新評估。</span><span class="sxs-lookup"><span data-stu-id="2ee03-123">The fact is being updated by a rule and then needs to be reasserted into the engine to be re-evaluated, based on the new data and state.</span></span>  
  
 <span data-ttu-id="2ee03-124">撤回</span><span class="sxs-lookup"><span data-stu-id="2ee03-124">Retract</span></span>  
  
 <span data-ttu-id="2ee03-125">事實從工作記憶體移除。</span><span class="sxs-lookup"><span data-stu-id="2ee03-125">The fact is being removed from the working memory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ee03-126">若事實經判斷提示其類型不符合原則中所使用的任何一種類型，「判斷提示」作業將會顯示 [判斷提示 - 事實無法辨識]。</span><span class="sxs-lookup"><span data-stu-id="2ee03-126">If a fact is asserted whose type does not match any of the types used in the policy, the Assert operation will display "Assert – Fact Unrecognized".</span></span>  
  
### <a name="object-type"></a><span data-ttu-id="2ee03-127">物件類型</span><span class="sxs-lookup"><span data-stu-id="2ee03-127">Object Type</span></span>  
 <span data-ttu-id="2ee03-128">特定活動的事實類型：</span><span class="sxs-lookup"><span data-stu-id="2ee03-128">The type of fact for a particular activity:</span></span>  
  
-   <span data-ttu-id="2ee03-129">DataConnection</span><span class="sxs-lookup"><span data-stu-id="2ee03-129">DataConnection</span></span>  
  
-   <span data-ttu-id="2ee03-130">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="2ee03-130">TypedDataTable</span></span>  
  
-   <span data-ttu-id="2ee03-131">TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="2ee03-131">TypedDataRow</span></span>  
  
     <span data-ttu-id="2ee03-132">若判斷提示 TypedDataTable，其中包含的所有資料列都會判斷提示為 TypedDataRow。</span><span class="sxs-lookup"><span data-stu-id="2ee03-132">When a TypedDataTable is asserted all of the contained rows are asserted as TypedDataRows.</span></span>  <span data-ttu-id="2ee03-133">與 DataConnection 關聯的 TypedDataRow 必須等到條件經過評估，而且結果查詢已經執行之後，才會進行判斷提示。</span><span class="sxs-lookup"><span data-stu-id="2ee03-133">TypedDataRows associated with a DataConnection are not asserted until a condition is evaluated and the resulting query is executed.</span></span>  
  
-   <span data-ttu-id="2ee03-134">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="2ee03-134">TypedXmlDocument</span></span>  
  
     <span data-ttu-id="2ee03-135">父系和子系的 TypedXmlDocument 執行個體都可以檢視判斷提示。</span><span class="sxs-lookup"><span data-stu-id="2ee03-135">Assertions will be seen for both parent and child TypedXmlDocument instances.</span></span>  
  
### <a name="object-instance-identifier"></a><span data-ttu-id="2ee03-136">物件執行個體識別項</span><span class="sxs-lookup"><span data-stu-id="2ee03-136">Object Instance Identifier</span></span>  
 <span data-ttu-id="2ee03-137">事實參考的唯一執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="2ee03-137">Unique instance ID of the fact reference.</span></span>  
  
## <a name="condition-evaluation"></a><span data-ttu-id="2ee03-138">條件評估</span><span class="sxs-lookup"><span data-stu-id="2ee03-138">Condition Evaluation</span></span>  
 <span data-ttu-id="2ee03-139">這項活動指示個別述詞的評估結果。</span><span class="sxs-lookup"><span data-stu-id="2ee03-139">This activity indicates the result of evaluating individual predicates.</span></span> <span data-ttu-id="2ee03-140">以下為條件評估項目的範例：</span><span class="sxs-lookup"><span data-stu-id="2ee03-140">The following is an example of a condition evaluation entry:</span></span>  
  
```  
CONDITION EVALUATION TEST (MATCH) 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Test Expression: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:Root.EmploymentType/TimeInMonths >= 18  
Left Operand Value: 31  
Right Operand Value: 18  
Test Result: True  
```  
  
 <span data-ttu-id="2ee03-141">以下內容將描述上述範例提到的一些詞彙：</span><span class="sxs-lookup"><span data-stu-id="2ee03-141">The descriptions for some of the terms in the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="2ee03-142">**測試運算式。**</span><span class="sxs-lookup"><span data-stu-id="2ee03-142">**Test Expression.**</span></span> <span data-ttu-id="2ee03-143">規則中的簡單 (一元或二元) 運算式。</span><span class="sxs-lookup"><span data-stu-id="2ee03-143">A simple (unary or binary) expression within a rule.</span></span>  
  
-   <span data-ttu-id="2ee03-144">**左的運算元值。**</span><span class="sxs-lookup"><span data-stu-id="2ee03-144">**Left Operand Value.**</span></span> <span data-ttu-id="2ee03-145">位於運算式左邊的詞彙值。</span><span class="sxs-lookup"><span data-stu-id="2ee03-145">The value of the term on the left side of an expression.</span></span>  
  
-   <span data-ttu-id="2ee03-146">**右運算元值。**</span><span class="sxs-lookup"><span data-stu-id="2ee03-146">**Right Operand Value.**</span></span> <span data-ttu-id="2ee03-147">位於運算式右邊的詞彙值。</span><span class="sxs-lookup"><span data-stu-id="2ee03-147">The value of the term on the right side of an expression.</span></span>  
  
-   <span data-ttu-id="2ee03-148">**測試結果。**</span><span class="sxs-lookup"><span data-stu-id="2ee03-148">**Test Result.**</span></span> <span data-ttu-id="2ee03-149">評估的結果，結果可為 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="2ee03-149">The result of the evaluation, which is either True or False.</span></span>  
  
## <a name="agenda-update"></a><span data-ttu-id="2ee03-150">議程更新</span><span class="sxs-lookup"><span data-stu-id="2ee03-150">Agenda Update</span></span>  
 <span data-ttu-id="2ee03-151">這項活動指示已加入規則引擎議程以便後續執行的規則。</span><span class="sxs-lookup"><span data-stu-id="2ee03-151">This activity indicates rules that are added to the rule engine agenda for subsequent execution.</span></span> <span data-ttu-id="2ee03-152">以下為議程更新項目的範例：</span><span class="sxs-lookup"><span data-stu-id="2ee03-152">The following is an example of an agenda update entry:</span></span>  
  
```  
AGENDA UPDATE 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Operation: Add  
Rule Name: Employment Status Rule  
Conflict Resolution Criteria: 0  
```  
  
 <span data-ttu-id="2ee03-153">以下內容將描述上述範例提到的一些詞彙：</span><span class="sxs-lookup"><span data-stu-id="2ee03-153">The descriptions for some of the terms in the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="2ee03-154">**作業。**</span><span class="sxs-lookup"><span data-stu-id="2ee03-154">**Operation.**</span></span> <span data-ttu-id="2ee03-155">規則可以新增到議程或是從中移除。</span><span class="sxs-lookup"><span data-stu-id="2ee03-155">Rules can be added or removed from the agenda.</span></span>  
  
-   <span data-ttu-id="2ee03-156">**規則名稱。**</span><span class="sxs-lookup"><span data-stu-id="2ee03-156">**Rule Name.**</span></span> <span data-ttu-id="2ee03-157">將要新增到議程的規則名稱。</span><span class="sxs-lookup"><span data-stu-id="2ee03-157">The name of the rule that is being added to the agenda.</span></span>  
  
-   <span data-ttu-id="2ee03-158">**衝突解決準則。**</span><span class="sxs-lookup"><span data-stu-id="2ee03-158">**Conflict Resolution Criteria.**</span></span> <span data-ttu-id="2ee03-159">規則的優先順序，決定執行動作的相對順序 (較高優先順序的動作會優先執行)。</span><span class="sxs-lookup"><span data-stu-id="2ee03-159">The priority of a rule, which determines the relative order in which actions are executed (higher-priority actions are executed first).</span></span>  
  
## <a name="rule-fired"></a><span data-ttu-id="2ee03-160">規則被引發</span><span class="sxs-lookup"><span data-stu-id="2ee03-160">Rule Fired</span></span>  
 <span data-ttu-id="2ee03-161">這項活動指示規則動作的執行。</span><span class="sxs-lookup"><span data-stu-id="2ee03-161">This activity indicates the execution of a rule's actions.</span></span> <span data-ttu-id="2ee03-162">以下為規則被引發項目的範例：</span><span class="sxs-lookup"><span data-stu-id="2ee03-162">The following is an example of a rule fired entry:</span></span>  
  
```  
RULE FIRED 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Rule Name: Residency Status Rule  
Conflict Resolution Criteria: 10  
```