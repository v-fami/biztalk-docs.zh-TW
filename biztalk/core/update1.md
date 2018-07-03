---
title: 更新 1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Update function [Business Rules Engine]
- Update function [Business Rules Engine], TypedXMLDocument
- Update function [Business Rules Engine], TypedData table
- Update function [Business Rules Engine], .NET objects
- .NET objects
- Update function [Business Rules Engine], DataConnection
ms.assetid: 939e45dc-6433-42f3-a336-8f3c247417ac
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccb9c8e8b75bc67954c30bf2b4a6e6ff39b3ee01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008823"
---
# <a name="update"></a><span data-ttu-id="d66a6-102">Update</span><span class="sxs-lookup"><span data-stu-id="d66a6-102">Update</span></span>
<span data-ttu-id="d66a6-103">當**更新**函式會叫用物件，該物件判斷提示在引擎重新進行評估，根據新的資料和狀態。</span><span class="sxs-lookup"><span data-stu-id="d66a6-103">When **Update** function is invoked an object, the object is reasserted into the engine to be re-evaluated, based on the new data and state.</span></span> <span data-ttu-id="d66a6-104">物件可以是類型**TypedXmlDocument**或 .NET 類別或**DataConnection**或是**TypedDataTable**。</span><span class="sxs-lookup"><span data-stu-id="d66a6-104">The object can be of type **TypedXmlDocument** or .NET class or **DataConnection** or **TypedDataTable**.</span></span>  
  
 <span data-ttu-id="d66a6-105">您也可以使用**更新**函式來改善引擎效能和避免無止盡迴圈的案例中，本主題中所述。</span><span class="sxs-lookup"><span data-stu-id="d66a6-105">You can also use **Update** function to improve engine performance and prevent endless loop scenarios as described in this topic.</span></span>  
  
 <span data-ttu-id="d66a6-106">一般而言，您可以使用**Assert**放置規則引擎工作記憶體中的新物件，並使用**更新**更新工作記憶體中的現有物件。</span><span class="sxs-lookup"><span data-stu-id="d66a6-106">Typically, you use **Assert** to place a new object in the working memory of the rule engine, and use **Update** to update an already existing object in the working memory.</span></span> <span data-ttu-id="d66a6-107">當您判斷提示新物件時，所有規則中的條件都會受到評估。</span><span class="sxs-lookup"><span data-stu-id="d66a6-107">When you assert a new object, conditions in all the rules are evaluated.</span></span> <span data-ttu-id="d66a6-108">當您更新現有物件時，只有用到已更新事實的條件會受到重新評估，而這些條件若評估為 true，即會在議程中新增動作。</span><span class="sxs-lookup"><span data-stu-id="d66a6-108">When you update an existing object, only conditions that use the updated fact are reevaluated, and actions are added to the agenda if these conditions are evaluated to true.</span></span>  
  
## <a name="using-update-function-on-net-facts"></a><span data-ttu-id="d66a6-109">在 .NET 事實上使用 Update 函式</span><span class="sxs-lookup"><span data-stu-id="d66a6-109">Using Update function on .NET facts</span></span>  
 <span data-ttu-id="d66a6-110">以下兩個規則為範例。</span><span class="sxs-lookup"><span data-stu-id="d66a6-110">Take the two rules that follow as an example.</span></span> <span data-ttu-id="d66a6-111">假設物件**ItemA**並**ItemB**存在於工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="d66a6-111">Suppose that objects **ItemA** and **ItemB** already exist in working memory.</span></span> <span data-ttu-id="d66a6-112">規則 1 評估**識別碼**屬性上的**ItemA**，設定**識別碼**屬性**ItemB**，然後重新判斷提示和**ItemB**變更之後。</span><span class="sxs-lookup"><span data-stu-id="d66a6-112">Rule 1 evaluates the **Id** property on **ItemA**, sets the **Id** property on **ItemB**, and then reasserts **ItemB** after the change.</span></span> <span data-ttu-id="d66a6-113">當**ItemB**重新判斷提示，它會被視為新的物件和引擎重新評估使用物件的所有規則**ItemB**述詞或動作中。</span><span class="sxs-lookup"><span data-stu-id="d66a6-113">When **ItemB** is reasserted, it is treated as a new object and the engine re-evaluates all rules that use object **ItemB** in the predicates or actions.</span></span> <span data-ttu-id="d66a6-114">這可確保 「 規則 2 」 的新值重新評估**ItemB.Id**，規則 1 中所設定。</span><span class="sxs-lookup"><span data-stu-id="d66a6-114">This ensures that Rule 2 is re-evaluated against the new value of **ItemB.Id**, as set in Rule 1.</span></span> <span data-ttu-id="d66a6-115">規則 2 可能會失敗，它已評估，但評估為第一次 **，則為 true**就會評估第二次。</span><span class="sxs-lookup"><span data-stu-id="d66a6-115">Rule 2 may have failed the first time it was evaluated, but evaluates to **true** the second time it is evaluated.</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="d66a6-116">規則 1</span><span class="sxs-lookup"><span data-stu-id="d66a6-116">Rule 1</span></span>  
  
```  
IF ItemA.Id == 1  
THEN ItemB.Id = 2  
Assert(ItemB)  
```  
  
### <a name="rule-2"></a><span data-ttu-id="d66a6-117">規則 2</span><span class="sxs-lookup"><span data-stu-id="d66a6-117">Rule 2</span></span>  
  
```  
IF ItemB.Id == 2  
THEN ItemB.Value = 100  
```  
  
 <span data-ttu-id="d66a6-118">這種在工作記憶體中重新判斷提示的能力，可讓使用者明確控制正向鏈結實例中的行為。</span><span class="sxs-lookup"><span data-stu-id="d66a6-118">This ability to reassert objects into working memory allows the user explicit control over the behavior in forward-chaining scenarios.</span></span> <span data-ttu-id="d66a6-119">不過，此範例中重新判斷提示的副作用是「規則 1」也會重新評估。</span><span class="sxs-lookup"><span data-stu-id="d66a6-119">A side effect of the reassertion in this example, however, is that Rule 1 is also re-evaluated.</span></span> <span data-ttu-id="d66a6-120">因為**ItemA.Id**沒有變更，因此 Rule 1 再次評估為 **，則為 true**並**assert （itemb)** 動作就會引發一次。</span><span class="sxs-lookup"><span data-stu-id="d66a6-120">Because **ItemA.Id** was not changed, Rule 1 again evaluates to **true** and the **Assert(ItemB)** action fires again.</span></span> <span data-ttu-id="d66a6-121">其結果是，規則建立了無止盡迴圈的狀況。</span><span class="sxs-lookup"><span data-stu-id="d66a6-121">As a result, the rule creates an endless loop situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d66a6-122">重新評估規則的預設最大迴圈計數為 2 ^32。</span><span class="sxs-lookup"><span data-stu-id="d66a6-122">The default maximum loop count of re-evaluation of rules is 2^32.</span></span> <span data-ttu-id="d66a6-123">如需特定規則，原則執行可以持續很長的時間。</span><span class="sxs-lookup"><span data-stu-id="d66a6-123">For certain rules, the policy execution could last for a long time.</span></span> <span data-ttu-id="d66a6-124">您可以藉由調整減少計數**最大執行迴圈深度**的原則版本的屬性。</span><span class="sxs-lookup"><span data-stu-id="d66a6-124">You can reduce the count by adjusting the **Maximum Execution Loop Depth** property of the policy version.</span></span>  
  
 <span data-ttu-id="d66a6-125">您必須能夠重新判斷提示物件，而不需要建立無止盡的迴圈，而**更新**函式提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="d66a6-125">You need to be able to reassert objects without creating endless loops, and the **Update** function provides this capability.</span></span> <span data-ttu-id="d66a6-126">像重新判斷提示一樣，**更新**函式會執行**Retract**並**Assert**相關聯的物件執行個體，其中已變更規則的動作，但有兩個主要差異：</span><span class="sxs-lookup"><span data-stu-id="d66a6-126">Like a reassert, the **Update** function performs **Retract** and **Assert** of the associated object instances, which have been changed from rule actions, but there are two key differences:</span></span>  
  
- <span data-ttu-id="d66a6-127">執行個體類型僅用於動作 (而非述詞) 的規則之議程上的動作，將保留在議程上。</span><span class="sxs-lookup"><span data-stu-id="d66a6-127">Actions on the agenda for rules where the instance type is only used in the actions (not the predicates) will remain on the agenda.</span></span>  
  
- <span data-ttu-id="d66a6-128">在動作中僅使用執行個體類型的規則將不會重新評估。</span><span class="sxs-lookup"><span data-stu-id="d66a6-128">Rules that only use the instance type in the actions will not be re-evaluated.</span></span>  
  
  <span data-ttu-id="d66a6-129">因此，僅在述詞或在述詞與動作兩者中使用執行個體類型的規則將會重新評估，而其動作會適當地加入到議程。</span><span class="sxs-lookup"><span data-stu-id="d66a6-129">Therefore, rules that use the instance types in either the predicates only or both the predicates and actions will be re-evaluated and their actions added to the agenda as appropriate.</span></span>  
  
  <span data-ttu-id="d66a6-130">若要使用上述範例變更**更新**函式可確保只有 「 規則 2 會重新評估，因為**ItemB**規則 2 的條件中使用。</span><span class="sxs-lookup"><span data-stu-id="d66a6-130">Changing the preceding example to use the **Update** function ensures that only Rule 2 is re-evaluated because **ItemB** is used in the condition of Rule 2.</span></span> <span data-ttu-id="d66a6-131">規則 1 則不會因為受到**ItemB**只會在規則 1，消除了迴圈實例的動作。</span><span class="sxs-lookup"><span data-stu-id="d66a6-131">Rule 1 is not reevaluated because **ItemB** is only used in the actions of Rule 1, eliminating the looping scenario.</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="d66a6-132">規則 1</span><span class="sxs-lookup"><span data-stu-id="d66a6-132">Rule 1</span></span>  
  
```  
IF ItemA.Id == 1  
THEN ItemB.Id = 2  
Update(ItemB)  
```  
  
### <a name="rule-2"></a><span data-ttu-id="d66a6-133">規則 2</span><span class="sxs-lookup"><span data-stu-id="d66a6-133">Rule 2</span></span>  
  
```  
IF ItemB.Id == 2  
THEN ItemB.Value = 100  
```  
  
 <span data-ttu-id="d66a6-134">不過，仍然可能建立迴圈實例。</span><span class="sxs-lookup"><span data-stu-id="d66a6-134">However, it is still possible to create looping scenarios.</span></span> <span data-ttu-id="d66a6-135">例如，考慮下列規則。</span><span class="sxs-lookup"><span data-stu-id="d66a6-135">For example, consider the following rule.</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="d66a6-136">規則 1</span><span class="sxs-lookup"><span data-stu-id="d66a6-136">Rule 1</span></span>  
  
```  
IF ItemA.Id == 1  
THEN ItemA.Value = 20  
Update(ItemA)  
```  
  
 <span data-ttu-id="d66a6-137">因為**ItemA**會使用述詞，它會重新評估時**更新**上呼叫**ItemA**。</span><span class="sxs-lookup"><span data-stu-id="d66a6-137">Because **ItemA** is used in the predicate, it is re-evaluated when **Update** is called on **ItemA**.</span></span> <span data-ttu-id="d66a6-138">如果的值**ItemA.Id**不會變更其他地方，規則 1 」 會持續評估 **，則為 true**，而導致**更新**再次呼叫於 a。規則設計工具，必須確定不會建立這類的迴圈實例。</span><span class="sxs-lookup"><span data-stu-id="d66a6-138">If the value of **ItemA.Id** is not changed elsewhere, Rule 1 continues to evaluate to **true**, causing **Update** to once again be called on A. The rule designer must ensure that looping scenarios such as this are not created.</span></span>  
  
 <span data-ttu-id="d66a6-139">適用於此的適當方式將依據規則本質而有所差異。</span><span class="sxs-lookup"><span data-stu-id="d66a6-139">The appropriate approach for this will differ based on the nature of the rules.</span></span> <span data-ttu-id="d66a6-140">以下是解決上述範例中之問題的簡單機制。</span><span class="sxs-lookup"><span data-stu-id="d66a6-140">The following is a simple mechanism to solve the problem in the preceding example.</span></span>  
  
 <span data-ttu-id="d66a6-141">**更新**函式可用於商務規則編輯器的參考至類別，如同**Assert**， **Retract**，或**RetractByType**函式。</span><span class="sxs-lookup"><span data-stu-id="d66a6-141">The **Update** function may be used in the Business Rule Composer with a reference to the class, as with the **Assert**, **Retract**, or **RetractByType** functions.</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="d66a6-142">規則 1</span><span class="sxs-lookup"><span data-stu-id="d66a6-142">Rule 1</span></span>  
  
```  
IF ItemA.Id == 1 and ItemA.Value != 20  
THEN ItemA.Value = 20  
Update(ItemA)  
```  
  
 <span data-ttu-id="d66a6-143">上加入檢查**ItemA.Value**防止規則 1 評估 **，則為 true**一次之後第一次執行規則 1 的動作。</span><span class="sxs-lookup"><span data-stu-id="d66a6-143">Adding the check on **ItemA.Value** prevents Rule 1 from evaluating to **true** again after the actions of Rule 1 are executed the first time.</span></span>  
  
## <a name="using-update-function-on-xml-facts"></a><span data-ttu-id="d66a6-144">在 XML 事實上使用 Update 函式</span><span class="sxs-lookup"><span data-stu-id="d66a6-144">Using Update function on XML facts</span></span>  
 <span data-ttu-id="d66a6-145">以下兩個規則為範例。</span><span class="sxs-lookup"><span data-stu-id="d66a6-145">Take the two rules that follow as an example.</span></span> <span data-ttu-id="d66a6-146">假設：</span><span class="sxs-lookup"><span data-stu-id="d66a6-146">Suppose that.</span></span> <span data-ttu-id="d66a6-147">「規則 1」會評估訂單訊息中的項目總數，而「規則 2」會在總數大於或等於 10 時，將狀態設定為「需要核准」。</span><span class="sxs-lookup"><span data-stu-id="d66a6-147">Rule 1 evaluates the total count of the items in a purchase order message, and rule2 sets the status to "Needs approval" if the total count is greater than or equal to 10.</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="d66a6-148">規則 1</span><span class="sxs-lookup"><span data-stu-id="d66a6-148">Rule 1</span></span>  
  
```  
IF 1 == 1  
THEN ProcessPO.Order:/Order/Items/TotalCount = (ProcessPO.Order:/Order/Items/TotalCount + ProcessPO:/Order/Items/Item/Count)  
```  
  
### <a name="rule-2"></a><span data-ttu-id="d66a6-149">規則 2</span><span class="sxs-lookup"><span data-stu-id="d66a6-149">Rule 2</span></span>  
  
```  
IF ProcessPO.Order:/Order/Items/TotalCount >= 10  
THEN ProcessPO.Order:/Order/Status = "Needs approval"  
```  
  
 <span data-ttu-id="d66a6-150">如果您將下列訂單 (PO) 訊息傳遞做為此原則的輸入時，您會發現，狀態未設定為 「 需要核准 」 即使總項目計數為 14。</span><span class="sxs-lookup"><span data-stu-id="d66a6-150">If you pass the following purchase order (PO) message as an input to this policy, you notice that the status is not set to "Needs approval" even though the total item count is 14.</span></span> <span data-ttu-id="d66a6-151">這是因為 rule2 會評估只有在開始時的值**TotalCount**欄位為 0，而且規則不會評估每次可用總數更新時。</span><span class="sxs-lookup"><span data-stu-id="d66a6-151">It is because that the rule2 is evaluated only at the beginning when the value of the **TotalCount** field is 0, and the rule is not evaluated each time the total available count is updated.</span></span> <span data-ttu-id="d66a6-152">若要有條件評估每次**TotalCount**已更新，您必須呼叫**更新**父節點上的函式 (**項目**) 的已修改的節點 (**TotalCount**)。</span><span class="sxs-lookup"><span data-stu-id="d66a6-152">To have the conditions reevaluated each time the **TotalCount** is updated, you need to call the **Update** function on the parent node (**Items**) of the modified node (**TotalCount**).</span></span> <span data-ttu-id="d66a6-153">如果您如下文所示變更「規則 1」，然後再測試一次，您應會看見 [狀態] 欄位的值設定為「需要核准」。</span><span class="sxs-lookup"><span data-stu-id="d66a6-153">If you change the Rule1 as shown below, and test it one more time, you should see the value of the Status field set to "Needs Approval".</span></span>  
  
```  
<ns0:Order xmlns:ns0="http://ProcessPO.Order">  
    <Items>  
        <Item>  
            <Id>ITM1</Id>  
            <Count>2</Count>  
        </Item>  
        <Item>  
            <Id>ITM2</Id>  
            <Count>5</Count>  
        </Item>  
        <Item>  
            <Id>ITM3</Id>  
            <Count>7</Count>  
        </Item>  
        <TotalCount>0</TotalCount>  
    </Items>  
    <Status>No approval needed</Status>  
</ns0:Order>  
```  
  
 <span data-ttu-id="d66a6-154">已修改**規則 1**如下所示：</span><span class="sxs-lookup"><span data-stu-id="d66a6-154">The modified **Rule 1** is as follows:</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="d66a6-155">規則 1</span><span class="sxs-lookup"><span data-stu-id="d66a6-155">Rule 1</span></span>  
  
```  
IF 1 == 1  
THEN ProcessPO.Order:/Order/Items/TotalCount = (ProcessPO.Order:/Order/Items/TotalCount + ProcessPO:/Order/Items/Item/Count) AND  
Update(ProcessPO.Order:/Order/Items)  
```  
  
## <a name="using-update-function-on-database-facts"></a><span data-ttu-id="d66a6-156">在 資料庫事實上使用 Update 函式</span><span class="sxs-lookup"><span data-stu-id="d66a6-156">Using Update function on database facts</span></span>  
  
### <a name="typeddatatable"></a><span data-ttu-id="d66a6-157">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="d66a6-157">TypedDataTable</span></span>  
 <span data-ttu-id="d66a6-158">如果**更新**上呼叫**TypedDataTable**， **Update**所有相關聯引擎會呼叫**TypedDataRows**。</span><span class="sxs-lookup"><span data-stu-id="d66a6-158">If **Update** is called on a **TypedDataTable**, **Update** is called by the engine on all associated **TypedDataRows**.</span></span> <span data-ttu-id="d66a6-159">**更新**也稱為個別**TypedDataRows**。</span><span class="sxs-lookup"><span data-stu-id="d66a6-159">**Update** may also be called on individual **TypedDataRows**.</span></span>  
  
### <a name="dataconnection"></a><span data-ttu-id="d66a6-160">DataConnection</span><span class="sxs-lookup"><span data-stu-id="d66a6-160">DataConnection</span></span>  
 <span data-ttu-id="d66a6-161">更新**DataConnection**不支援。</span><span class="sxs-lookup"><span data-stu-id="d66a6-161">Update of a **DataConnection** is not supported.</span></span> <span data-ttu-id="d66a6-162">使用**Assert**改。</span><span class="sxs-lookup"><span data-stu-id="d66a6-162">Use **Assert** instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d66a6-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d66a6-163">See Also</span></span>  
 [<span data-ttu-id="d66a6-164">引擎控制函式</span><span class="sxs-lookup"><span data-stu-id="d66a6-164">Engine Control Functions</span></span>](../core/engine-control-functions.md)