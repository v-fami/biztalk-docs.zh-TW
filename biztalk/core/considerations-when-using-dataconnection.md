---
title: "使用 DataConnection 時的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Retract function [Business Rules Engine], DataConnection
- RetractByType function [Business Rules Engine], DataConnection
- Business Rules Engine, DataConnection tips
- Assert function [Business Rules Engine], DataConnection
- Update function [Business Rules Engine], DataConnection
ms.assetid: 1b4c8aa5-053f-43d7-9f5f-050383405fed
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f99110daafa74cb16b6cc5b98e1382049bbb158
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-using-dataconnection"></a><span data-ttu-id="91d0c-102">使用 DataConnection 時的考量</span><span class="sxs-lookup"><span data-stu-id="91d0c-102">Considerations When Using DataConnection</span></span>
<span data-ttu-id="91d0c-103">使用 DataConnection 與商務規則引擎時請考量以下幾點。</span><span class="sxs-lookup"><span data-stu-id="91d0c-103">Consider the following when using DataConnection with the Business Rule Engine.</span></span>  
  
## <a name="use-primary-keys"></a><span data-ttu-id="91d0c-104">使用主索引鍵</span><span class="sxs-lookup"><span data-stu-id="91d0c-104">Use primary keys</span></span>  
 <span data-ttu-id="91d0c-105">有主索引鍵時，兩個資料列的相等性是由資料列是否具有相同的主索引鍵，而非物件的比較而決定。</span><span class="sxs-lookup"><span data-stu-id="91d0c-105">When there is a primary key, the equality of two rows is determined by whether the rows have the same primary key, rather than by object comparison.</span></span> <span data-ttu-id="91d0c-106">若資料列判定為相同，則記憶體中僅會保留一個複本，並釋出另一個。</span><span class="sxs-lookup"><span data-stu-id="91d0c-106">If the rows are determined to be the same, only one copy is retained in memory, and the other is released.</span></span> <span data-ttu-id="91d0c-107">如此可耗用較少的記憶體。</span><span class="sxs-lookup"><span data-stu-id="91d0c-107">This results in less memory consumption.</span></span>  
  
 <span data-ttu-id="91d0c-108">當**DataConnection**判斷提示至規則引擎第一次，引擎一律試圖找出其主索引鍵資訊，從它的結構描述。</span><span class="sxs-lookup"><span data-stu-id="91d0c-108">When a **DataConnection** is asserted into the rule engine for the first time, the engine always tries to locate its primary key information from its schema.</span></span> <span data-ttu-id="91d0c-109">若是有主索引鍵，即會擷取主索引鍵資訊，然後用於所有後續的評估。</span><span class="sxs-lookup"><span data-stu-id="91d0c-109">If a primary key exists, primary key information is then retrieved and used in all subsequent evaluations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91d0c-110">若是需要變更資料庫，則主索引鍵為必要項目。</span><span class="sxs-lookup"><span data-stu-id="91d0c-110">A primary key is mandatory if changes need to be made to the database.</span></span>  
  
## <a name="provide-a-running-transaction-to-the-dataconnection-whenever-possible"></a><span data-ttu-id="91d0c-111">若是情況許可，儘可能為 DataConnection 提供執行中交易</span><span class="sxs-lookup"><span data-stu-id="91d0c-111">Provide a running transaction to the DataConnection whenever possible</span></span>  
 <span data-ttu-id="91d0c-112">不使用交易，每個查詢和更新在**DataConnection**它自己的本機交易，而不同的查詢可能會傳回不同的初始化會導致不同部分的規則評估。</span><span class="sxs-lookup"><span data-stu-id="91d0c-112">Without a transaction, each query and update on the **DataConnection** initiates its own local transaction, and different queries might return different results in different parts of rule evaluations.</span></span> <span data-ttu-id="91d0c-113">若是基礎資料庫資料表中有所變更，使用者可能會發現處理不一致的情形。</span><span class="sxs-lookup"><span data-stu-id="91d0c-113">Users may experience inconsistent behavior if there are changes in the underlying database table.</span></span>  
  
 <span data-ttu-id="91d0c-114">雖然您可以使用**DataConnection**而不需提供交易，資料表不會隨時間變更時，建議使用的交易，即使**DataConnection**只被用於讀取作業。</span><span class="sxs-lookup"><span data-stu-id="91d0c-114">Although you can use a **DataConnection** without providing a transaction when the table does not change over time, it is recommended that a transaction be used even when the **DataConnection** is only being used for read operations.</span></span>  
  
 <span data-ttu-id="91d0c-115">不過，更新資料時應該永遠會使用交易。</span><span class="sxs-lookup"><span data-stu-id="91d0c-115">However, a transaction should always be used when updating data.</span></span>  
  
## <a name="number-of-queries-may-grow-linearly"></a><span data-ttu-id="91d0c-116">查詢數目可能呈線性增加</span><span class="sxs-lookup"><span data-stu-id="91d0c-116">Number of queries may grow linearly</span></span>  
 <span data-ttu-id="91d0c-117">對做為查詢**DataConnection**由其他聯結的物件，針對執行的查詢數目為參數化**DataConnection**直接對應至的聯結物件數到達**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="91d0c-117">As queries against the **DataConnection** are parameterized by other joined objects, the number of queries executed against the **DataConnection** corresponds directly to the number of joining objects reaching the **DataConnection**.</span></span> <span data-ttu-id="91d0c-118">因此，如果的聯結物件數達到**DataConnection**物件呈線性增加，針對查詢數目**DataConnection**會成長以線性方式以及。</span><span class="sxs-lookup"><span data-stu-id="91d0c-118">Therefore, if the number of joining objects reaching the **DataConnection** object grows linearly, the number of queries against the **DataConnection** will grow linearly as well.</span></span> <span data-ttu-id="91d0c-119">目前並沒有減少查詢數的最佳化方法。</span><span class="sxs-lookup"><span data-stu-id="91d0c-119">Currently, there is no optimization in place to reduce the number of queries.</span></span>  
  
 <span data-ttu-id="91d0c-120">此範例為規則：</span><span class="sxs-lookup"><span data-stu-id="91d0c-120">An example of this is the rule:</span></span>  
  
```  
IF A.x = 7 AND DC.y = A.y  
THEN  
```  
  
 <span data-ttu-id="91d0c-121">代表**ObjectBinding**，DC 代表**DataConnection**，而 x 和 y 代表屬性的 A 和 DC。</span><span class="sxs-lookup"><span data-stu-id="91d0c-121">A represents an **ObjectBinding**, DC represents a **DataConnection**, and x and y represent attributes of A and DC.</span></span>  
  
 <span data-ttu-id="91d0c-122">通過測試的每個執行個體 (x = 7)，查詢會產生使用**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="91d0c-122">For every instance of A that passes the test (x = 7), a query is generated by using the **DataConnection**.</span></span> <span data-ttu-id="91d0c-123">若是有許多相符的執行個體，會產生相同的查詢數。</span><span class="sxs-lookup"><span data-stu-id="91d0c-123">If there are many matching instances, the same number of queries results.</span></span>  
  
## <a name="use-or-conditions-with-caution"></a><span data-ttu-id="91d0c-124">小心使用 OR 條件</span><span class="sxs-lookup"><span data-stu-id="91d0c-124">Use OR conditions with caution</span></span>  
 <span data-ttu-id="91d0c-125">如果此規則會使用僅儘早 (**AND**) 條件、 測試及查詢將會執行儘早，所以將會減少傳遞之物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="91d0c-125">If the rule uses only conjunctive (**AND**) conditions, tests and queries will be executed as early as possible, so instances of objects passing through will be reduced.</span></span> <span data-ttu-id="91d0c-126">如此一來，針對後續的查詢數目**DataConnection**會依比例減少。</span><span class="sxs-lookup"><span data-stu-id="91d0c-126">As a result, the number of queries against the subsequent **DataConnection** will be reduced proportionally.</span></span> <span data-ttu-id="91d0c-127">如果分離 (**或者**) 條件和**DataConnection**在規則中，所有條件的評估會將推送至最終查詢一起使用。</span><span class="sxs-lookup"><span data-stu-id="91d0c-127">If disjunctive (**OR**) conditions and a **DataConnection** are used together in a rule, all condition evaluations will be pushed to the final query.</span></span> <span data-ttu-id="91d0c-128">如果有一個以上**DataConnection**用在規則中，除了最後一個將會有效地變成 SELECT-ALL 查詢陳述式的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="91d0c-128">If more than one **DataConnection** is used in a rule, all queries except the last one will effectively become a Select-ALL query statement.</span></span>  
  
 <span data-ttu-id="91d0c-129">一般而言，最好是將具有 OR 條件的規則分割為兩個或多個不連續規則，因為與多個不可部分完成的規則定義相較，使用 OR 條件的話將會降低效能。</span><span class="sxs-lookup"><span data-stu-id="91d0c-129">In general, it is better to split any rule with an OR condition into two or more discrete rules, because the use of OR conditions will decrease performance compared to the definition of more atomic rules.</span></span> <span data-ttu-id="91d0c-130">無論是否使用 DataConnections 都會發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="91d0c-130">This is true whether DataConnections are used or not.</span></span>  
  
 <span data-ttu-id="91d0c-131">您也可以考慮使用不同的規則，只包含連結的條件，而不是具有一個規則**或**條件。</span><span class="sxs-lookup"><span data-stu-id="91d0c-131">You may also consider using separate rules that consist only of conjunctive conditions instead of one rule with **OR** conditions.</span></span> <span data-ttu-id="91d0c-132">與**或**條件，所有聯結物件之執行個體的倍數速度增加查詢的次數。</span><span class="sxs-lookup"><span data-stu-id="91d0c-132">With **OR** conditions, the number of queries grows at the speed of multiplication of instances of all joining objects.</span></span> <span data-ttu-id="91d0c-133">下列範例會顯示這一點。</span><span class="sxs-lookup"><span data-stu-id="91d0c-133">This is shown in the following example.</span></span>  
  
```  
IF (A.x ==7 OR A.x == 8) AND DC.y == A.y  
THEN DC.z = 10  
```  
  
 <span data-ttu-id="91d0c-134">在此範例中，A 代表**ObjectBinding**;DC 代表**DataConnection**，和 x、 y 和 z 屬性 A 和 DC。</span><span class="sxs-lookup"><span data-stu-id="91d0c-134">In this example, A represents an **ObjectBinding**; DC represents a **DataConnection**, and x, y, and z represent attributes of A and DC.</span></span> <span data-ttu-id="91d0c-135">如果 A 有 100 個執行個體，而 x 是 1 中的第一個物件，第二個物件，到 100 個的第 100 的物件中的 2 100 個查詢都必須對執行**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="91d0c-135">If A has 100 instances, and x is 1 in the first object, 2 in the second object, through 100 in the 100th object, 100 queries have to run against the **DataConnection**.</span></span>  
  
 <span data-ttu-id="91d0c-136">最好是重寫前述規則，將它分割為兩個規則。</span><span class="sxs-lookup"><span data-stu-id="91d0c-136">It is better to rewrite the preceding rule by splitting it in to two rules.</span></span>  
  
 <span data-ttu-id="91d0c-137">**規則 1**</span><span class="sxs-lookup"><span data-stu-id="91d0c-137">**Rule 1**</span></span>  
  
```  
IF A.x =7 AND DC.y = A.y  
THEN DC.z = 10  
```  
  
 <span data-ttu-id="91d0c-138">**規則 2**</span><span class="sxs-lookup"><span data-stu-id="91d0c-138">**Rule 2**</span></span>  
  
```  
IF A.x = 8 AND DC.y = A.y  
THEN DC.z = 10  
```  
  
## <a name="sql-does-not-support-some-predicates-and-functions"></a><span data-ttu-id="91d0c-139">SQL 不支援某些述詞和函式</span><span class="sxs-lookup"><span data-stu-id="91d0c-139">SQL does not support some predicates and functions</span></span>  
 <span data-ttu-id="91d0c-140">某些規則引擎支援的述詞和函式，SQL 是不支援的。</span><span class="sxs-lookup"><span data-stu-id="91d0c-140">Some predicates and functions that the rule engine supports are not supported by SQL.</span></span> <span data-ttu-id="91d0c-141">若在規則條件中使用這些不支援的述詞和函式，就無法併入查詢中。</span><span class="sxs-lookup"><span data-stu-id="91d0c-141">If these unsupported predicates and functions are used in the rule conditions, it cannot be incorporated into the query.</span></span> <span data-ttu-id="91d0c-142">下列詞彙無法最佳化為 SQL 查詢：</span><span class="sxs-lookup"><span data-stu-id="91d0c-142">The following terms cannot be optimized as an SQL query:</span></span>  
  
-   <span data-ttu-id="91d0c-143">某些引擎內建函式在 SQL 查詢中沒有相等函式。</span><span class="sxs-lookup"><span data-stu-id="91d0c-143">Some of the engine built-in functions have no equivalent in an SQL query.</span></span> <span data-ttu-id="91d0c-144">這些是**電源**， **FindFirst**，和**FindAll**。</span><span class="sxs-lookup"><span data-stu-id="91d0c-144">These are **Power**, **FindFirst**, and **FindAll**.</span></span> <span data-ttu-id="91d0c-145">使用**DataConnection**當做其中一個或多個其引數的資料行不能最佳化為查詢的一部分; 例如，Power (2，dc。Column1)。</span><span class="sxs-lookup"><span data-stu-id="91d0c-145">Using a **DataConnection** column as one or more of their arguments cannot be optimized as part of a query; for example, Power( 2, dc.Column1).</span></span>  
  
-   <span data-ttu-id="91d0c-146">內建述詞 Match 使用**DataConnection**做為規則運算式引數 （第一個引數） 的資料行。</span><span class="sxs-lookup"><span data-stu-id="91d0c-146">Built-in predicate Match that uses a **DataConnection** column as its regular expression argument (the first argument).</span></span> <span data-ttu-id="91d0c-147">例如，Match("abc*", dc1.Column2) 是有效的，但是 Match(dc1.Column1, dc1.Column2) 則是無法轉譯的。</span><span class="sxs-lookup"><span data-stu-id="91d0c-147">For example, Match("abc*", dc1.Column2) is valid, but Match(dc1.Column1, dc1.Column2) cannot be translated.</span></span>  
  
-   <span data-ttu-id="91d0c-148">使用的使用者函式具有**DataConnection**做為其中一個參數的資料行。</span><span class="sxs-lookup"><span data-stu-id="91d0c-148">Using a user function that has a **DataConnection** column as one of its parameters.</span></span> <span data-ttu-id="91d0c-149">例如，c1.M(dc.Column1) 無法最佳化，因為無法在資料庫伺服器上執行使用者函式，必須由商務規則引擎來執行。</span><span class="sxs-lookup"><span data-stu-id="91d0c-149">For example, c1.M(dc.Column1) cannot be optimized because the user function cannot execute on the database server, but must be executed by the Business Rule Engine.</span></span>  
  
-   <span data-ttu-id="91d0c-150">表示設定作業的使用者函式**DataConnection**; 例如，dc。Column1(5)。</span><span class="sxs-lookup"><span data-stu-id="91d0c-150">User functions that represent set operations on the **DataConnection**; for example, dc.Column1(5).</span></span>  
  
-   <span data-ttu-id="91d0c-151">函式使用**ObjectReference**至**DataConnection**; 例如，objecref （dc）。</span><span class="sxs-lookup"><span data-stu-id="91d0c-151">Functions that use an **ObjectReference** to the **DataConnection**; for example, ObjecRef(dc).</span></span>  
  
-   <span data-ttu-id="91d0c-152">若是一或多個函式引數是無法轉譯的，函式呼叫也會變成無法轉譯；例如，Add(c1.M(dc.Column1), 5)。</span><span class="sxs-lookup"><span data-stu-id="91d0c-152">If one or more of a function's arguments is untranslatable, the function call becomes untranslatable; for example, Add(c1.M(dc.Column1), 5).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d0c-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91d0c-153">See Also</span></span>  
 [<span data-ttu-id="91d0c-154">商務規則引擎中的資料存取</span><span class="sxs-lookup"><span data-stu-id="91d0c-154">Data Access in the Business Rule Engine</span></span>](../core/data-access-in-the-business-rule-engine.md)