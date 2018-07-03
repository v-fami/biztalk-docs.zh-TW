---
title: 條件評估與動作執行 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Action stage [Business Rules Engine]
- examples, business rules
- Business Rules Engine, policies
- Match stage [Business Rules Engine]
- business rules, examples
- Business Rules Engine, algorithm
- Business Rules Engine, examples
- conflict resolution [Business Rules Engine]
- Business Rules Engine, stages
ms.assetid: dcaa32c2-3403-4f54-92e2-128686bfc193
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30d4f17fce34f72eed85ca49ecab09a81ce56681
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997223"
---
# <a name="condition-evaluation-and-action-execution"></a><span data-ttu-id="ecb2a-102">條件評估與動作執行</span><span class="sxs-lookup"><span data-stu-id="ecb2a-102">Condition Evaluation and Action Execution</span></span>
<span data-ttu-id="ecb2a-103">「商務規則架構」提供高效率的推斷引擎，可將規則連結至 .NET 物件、XML 文件或是資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-103">The Business Rules Framework provides a highly efficient inference engine capable of linking rules to .NET objects, XML documents, or database tables.</span></span>  
  
 <span data-ttu-id="ecb2a-104">「商務規則引擎」使用三階段的演算法以執行原則。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-104">The Business Rule Engine uses a three-stage algorithm for policy execution.</span></span> <span data-ttu-id="ecb2a-105">這些階段如下所示：</span><span class="sxs-lookup"><span data-stu-id="ecb2a-105">The stages are as follows:</span></span>  
  
- <span data-ttu-id="ecb2a-106">**比對**。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-106">**Match**.</span></span> <span data-ttu-id="ecb2a-107">在比對階段，會使用規則條件中定義的述詞，針對使用事實類型 (物件參考由規則引擎的工作記憶體維護) 的述詞比對事實。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-107">In the match stage, facts are matched against the predicates that use the fact type (object references maintained in the rule engine's working memory) using the predicates defined in the rule conditions.</span></span> <span data-ttu-id="ecb2a-108">基於效率的緣故，模式比對會在原則中的所有規則上執行，而不同規則之間共用的條件則只會比對一次。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-108">For the sake of efficiency, pattern matching occurs over all the rules in the policy, and conditions that are shared across rules are matched only once.</span></span> <span data-ttu-id="ecb2a-109">有可能會將部分條件比對儲存在工作記憶體中，以加速後續的模式比對作業。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-109">Partial condition matches may be stored in working memory to expedite subsequent pattern-matching operations.</span></span> <span data-ttu-id="ecb2a-110">模式比對階段的輸出是由對規則引擎議程的更新所組成。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-110">The output of the pattern-matching phase consists of updates to the rule engine agenda.</span></span>  
  
- <span data-ttu-id="ecb2a-111">**衝突解決**。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-111">**Conflict resolution**.</span></span> <span data-ttu-id="ecb2a-112">在衝突解決階段中，會檢查候選執行的規則，以根據預先決定的解決配置來決定下一組要執行的規則動作。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-112">In the conflict resolution stage, the rules that are candidates for execution are examined to determine the next set of rule actions to execute based on a predetermined resolution scheme.</span></span> <span data-ttu-id="ecb2a-113">在比對階段找到的所有候選規則都會加入規則引擎的議程中。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-113">All candidate rules found during the matching stage are added to the rule engine's agenda.</span></span>  
  
   <span data-ttu-id="ecb2a-114">預設的衝突解決配置是根據原則中的規則優先順序。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-114">The default conflict resolution scheme is based on rule priorities within a policy.</span></span> <span data-ttu-id="ecb2a-115">優先順序是在「商務規則編輯器」中可設定的規則屬性。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-115">The priority is a configurable property of a rule in the Business Rule Composer.</span></span> <span data-ttu-id="ecb2a-116">數目愈大，優先順序就愈高，因此若觸發多個規則，就會先執行較高優先順序的動作。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-116">The larger the number, the higher the priority; therefore if multiple rules are triggered, the higher-priority actions are executed first.</span></span>  
  
- <span data-ttu-id="ecb2a-117">**動作**。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-117">**Action**.</span></span> <span data-ttu-id="ecb2a-118">在動作階段，會執行已解析規則中的動作。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-118">In the action stage, the actions in the resolved rule are executed.</span></span> <span data-ttu-id="ecb2a-119">請注意，規則動作可判斷提示新事實到規則引擎，這會造成週期繼續。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-119">Note that rule actions can assert new facts into the rule engine, which causes the cycle to continue.</span></span> <span data-ttu-id="ecb2a-120">這也稱為正向鏈結。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-120">This is also known as forward chaining.</span></span> <span data-ttu-id="ecb2a-121">請務必注意，演算法永遠無法比目前執行的規則先執行。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-121">It is important to note that the algorithm never preempts the currently executing rule.</span></span> <span data-ttu-id="ecb2a-122">在重複比對階段之前，將會先執行目前引發的規則之所有動作。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-122">All actions for the rule that is currently firing will be executed before the match phase is repeated.</span></span> <span data-ttu-id="ecb2a-123">不過，在比對階段再次開始之前，將不會引發在議程上的其他規則。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-123">However, other rules on the agenda will not be fired before the match phase begins again.</span></span> <span data-ttu-id="ecb2a-124">比對階段可能造成在引發議程上的規則之前，從議程移除它們。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-124">The match phase may cause those rules on the agenda to be removed from the agenda before they ever fire.</span></span>  
  
  <span data-ttu-id="ecb2a-125">下列範例顯示比對衝突解析動作的三階段演算法。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-125">The following example shows the three-stage algorithm of match-conflict resolution-action.</span></span>  
  
  <span data-ttu-id="ecb2a-126">**規則 1： 評估收入**</span><span class="sxs-lookup"><span data-stu-id="ecb2a-126">**Rule 1: Evaluate income**</span></span>  
  
- <span data-ttu-id="ecb2a-127">宣告式表示法：</span><span class="sxs-lookup"><span data-stu-id="ecb2a-127">Declarative representation:</span></span>  
  
   <span data-ttu-id="ecb2a-128">只有在申請者的收入對貸款的比率小於 0.2 時，才取得申請者的信用等級。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-128">An applicant's credit rating should be obtained only if the applicant's income-to-loan ratio is less than 0.2.</span></span>  
  
- <span data-ttu-id="ecb2a-129">使用商務物件的 IF—THEN 表示法：</span><span class="sxs-lookup"><span data-stu-id="ecb2a-129">IF—THEN representation using business objects:</span></span>  
  
  ```  
  IF Application.Income / Property.Price < 0.2    
  THEN Assert new CreditRating( Application)   
  ```  
  
  <span data-ttu-id="ecb2a-130">**規則 2： 評估信用等級**</span><span class="sxs-lookup"><span data-stu-id="ecb2a-130">**Rule 2: Evaluate credit rating**</span></span>  
  
- <span data-ttu-id="ecb2a-131">宣告式表示法：</span><span class="sxs-lookup"><span data-stu-id="ecb2a-131">Declarative representation:</span></span>  
  
   <span data-ttu-id="ecb2a-132">只有當申請者的信用等級大於 725 時才核准申請者。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-132">An applicant should be approved only if the applicant's credit rating is more than 725.</span></span>  
  
- <span data-ttu-id="ecb2a-133">使用商務物件的 IF—THEN 表示法：</span><span class="sxs-lookup"><span data-stu-id="ecb2a-133">IF—THEN Representation using business objects:</span></span>  
  
  ```  
  IF Application.SSN = CreditRating.SSN AND CreditRating.Value > 725    
  THEN SendApprovalLetter(Application)    
  ```  
  
  <span data-ttu-id="ecb2a-134">下表摘要這些事實。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-134">The facts are summarized in the following table.</span></span>  
  
|<span data-ttu-id="ecb2a-135">事實</span><span class="sxs-lookup"><span data-stu-id="ecb2a-135">Fact</span></span>|<span data-ttu-id="ecb2a-136">欄位</span><span class="sxs-lookup"><span data-stu-id="ecb2a-136">Fields</span></span>|  
|----------|------------|  
|<span data-ttu-id="ecb2a-137">Application – 代表房屋貸款申請的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="ecb2a-137">Application – An XML document representing a home loan application</span></span>|<span data-ttu-id="ecb2a-138">-Income = $65,000</span><span class="sxs-lookup"><span data-stu-id="ecb2a-138">-   Income = $65,000</span></span><br /><span data-ttu-id="ecb2a-139">SSN = XXX XX XXXX</span><span class="sxs-lookup"><span data-stu-id="ecb2a-139">-   SSN = XXX-XX-XXXX</span></span>|  
|<span data-ttu-id="ecb2a-140">Property – 代表購買的財產之 XML 文件</span><span class="sxs-lookup"><span data-stu-id="ecb2a-140">Property – An XML document representing the property being purchased</span></span>|<span data-ttu-id="ecb2a-141">-價格 = $225,000</span><span class="sxs-lookup"><span data-stu-id="ecb2a-141">-   Price = $225,000</span></span>|  
|<span data-ttu-id="ecb2a-142">CreditRating – 包含貸款申請者信用等級的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="ecb2a-142">CreditRating – An XML document containing the loan applicant's credit rating</span></span>|<span data-ttu-id="ecb2a-143">-值 = 0-800</span><span class="sxs-lookup"><span data-stu-id="ecb2a-143">-   Value = 0 – 800</span></span><br /><span data-ttu-id="ecb2a-144">SSN = XXX XX XXXX</span><span class="sxs-lookup"><span data-stu-id="ecb2a-144">-   SSN = XXX-XX-XXXX</span></span>|  
  
 <span data-ttu-id="ecb2a-145">在一開始時，規則引擎工作記憶體與議程是空的。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-145">Initially the rule engine working memory and agenda are empty.</span></span> <span data-ttu-id="ecb2a-146">在應用程式新增 Application 與 Property 事實之後，規則引擎工作記憶體與議程就會更新如下。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-146">After the application adds the Application and Property facts, the rule engine working memory and agenda are updated as follows.</span></span>  
  
|<span data-ttu-id="ecb2a-147">工作記憶體</span><span class="sxs-lookup"><span data-stu-id="ecb2a-147">Working memory</span></span>|<span data-ttu-id="ecb2a-148">議程</span><span class="sxs-lookup"><span data-stu-id="ecb2a-148">Agenda</span></span>|  
|--------------------|------------|  
|<span data-ttu-id="ecb2a-149">應用程式</span><span class="sxs-lookup"><span data-stu-id="ecb2a-149">-   Application</span></span><br /><span data-ttu-id="ecb2a-150">-屬性</span><span class="sxs-lookup"><span data-stu-id="ecb2a-150">-   Property</span></span>|<span data-ttu-id="ecb2a-151">規則 1</span><span class="sxs-lookup"><span data-stu-id="ecb2a-151">Rule 1</span></span>|  
  
 <span data-ttu-id="ecb2a-152">規則 1 加入議程，因為其條件 (Application.Income / Property.Price < 0.2) 評估為 **，則為 true**在比對階段。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-152">Rule 1 is added to the agenda because its condition (Application.Income / Property.Price < 0.2) evaluated to **true** during the match phase.</span></span> <span data-ttu-id="ecb2a-153">在工作記憶體中沒有 CreditRating 事實，因此不會評估規則 2 的條件。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-153">There is no CreditRating fact in working memory, so the condition for Rule 2 was not evaluated.</span></span> <span data-ttu-id="ecb2a-154">因為在議程中的唯一規則為規則 1，所以會執行該規則，然後從議程消失。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-154">Because the only rule in the agenda is Rule 1, the rule is executed and then disappears from the agenda.</span></span> <span data-ttu-id="ecb2a-155">為規則 1 定義的單一動件會使得新事實 (申請者的 CreditRating 文件) 加入工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-155">The single action defined for Rule 1 results in a new fact (CreditRating document for the applicant) being added to working memory.</span></span> <span data-ttu-id="ecb2a-156">在完成執行規則 1 之後，控制會返回比對階段。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-156">After the execution of Rule 1 completes, control returns to the match phase.</span></span> <span data-ttu-id="ecb2a-157">因為唯一要比對的新物件是 CreditRating 事實，所以比對階段的結果如下：</span><span class="sxs-lookup"><span data-stu-id="ecb2a-157">Because the only new object to match is the CreditRating fact, the results of the match phase are as follows.</span></span>  
  
|<span data-ttu-id="ecb2a-158">工作記憶體</span><span class="sxs-lookup"><span data-stu-id="ecb2a-158">Working memory</span></span>|<span data-ttu-id="ecb2a-159">議程</span><span class="sxs-lookup"><span data-stu-id="ecb2a-159">Agenda</span></span>|  
|--------------------|------------|  
|<span data-ttu-id="ecb2a-160">應用程式</span><span class="sxs-lookup"><span data-stu-id="ecb2a-160">-   Application</span></span><br /><span data-ttu-id="ecb2a-161">-屬性</span><span class="sxs-lookup"><span data-stu-id="ecb2a-161">-   Property</span></span><br /><span data-ttu-id="ecb2a-162">-CreditRating</span><span class="sxs-lookup"><span data-stu-id="ecb2a-162">-   CreditRating</span></span>|<span data-ttu-id="ecb2a-163">規則 2</span><span class="sxs-lookup"><span data-stu-id="ecb2a-163">Rule 2</span></span>|  
  
 <span data-ttu-id="ecb2a-164">在執行規則 2 時，會造成叫用傳送核准信件給申請者的函式。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-164">At this point Rule 2 is executed, resulting in the invocation of a function that sends an approval letter to the applicant.</span></span> <span data-ttu-id="ecb2a-165">在完成規則 2 之後，正向鏈結演算法的執行會返回比對階段。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-165">After Rule 2 has completed, execution of the forward-chaining algorithm returns to the match phase.</span></span> <span data-ttu-id="ecb2a-166">因為已經沒有要比對的新事實，而且議程是空的，所以正向鏈結會終止並且會完成執行原則。</span><span class="sxs-lookup"><span data-stu-id="ecb2a-166">Because there are no longer new facts to match and the agenda is empty, forward chaining terminates and policy execution is complete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb2a-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecb2a-167">See Also</span></span>  
 [<span data-ttu-id="ecb2a-168">規則引擎</span><span class="sxs-lookup"><span data-stu-id="ecb2a-168">Rule Engine</span></span>](../core/rule-engine.md)