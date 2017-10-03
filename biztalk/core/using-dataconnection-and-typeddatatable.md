---
title: "使用 DataConnection 與 TypedDataTable |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Retract function [Business Rules Engine], TypedData table
- RetractByType function [Business Rules Engine], TypedData table
- Retract function [Business Rules Engine], DataConnection
- RetractByType function [Business Rules Engine], DataConnection
- Assert function [Business Rules Engine], TypedData table
- Business Rules Engine, DataConnection tips
- TypedData table
- Business Rules Engine, TypedData table tips
- Assert function [Business Rules Engine], DataConnection
- Update function [Business Rules Engine], TypedData table
- Update function [Business Rules Engine], DataConnection
ms.assetid: e825803e-6626-4ddd-a77e-75a3ba2b74a4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b5a0a490023d77676cc5d156ad5126ad5d7d6c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-dataconnection-and-typeddatatable"></a><span data-ttu-id="c5806-102">使用 DataConnection 與 TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="c5806-102">Using DataConnection and TypedDataTable</span></span>
<span data-ttu-id="c5806-103">在許多情況下，使用**DataConnection**提供更佳的效能，並耗用較少的記憶體比使用**TypedDataTable**。</span><span class="sxs-lookup"><span data-stu-id="c5806-103">In many scenarios, using **DataConnection** provides better performance and consumes less memory than using **TypedDataTable**.</span></span> <span data-ttu-id="c5806-104">不過， **TypedDataTable**可能需要在某些情況下，因為使用的特定限制**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="c5806-104">However, **TypedDataTable** may be required in some cases because of certain restrictions on using **DataConnection**.</span></span> <span data-ttu-id="c5806-105">在某些其他情況下，使用**TypedDataTable**可能會產生較佳的效能比使用**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="c5806-105">In some other cases, using **TypedDataTable** may yield better performance than using **DataConnection**.</span></span> <span data-ttu-id="c5806-106">本主題描述您在選擇正確方法時應該考量的準則和因素。</span><span class="sxs-lookup"><span data-stu-id="c5806-106">This topic describes the criteria and factors that you should consider for choosing the right approach.</span></span>  
  
## <a name="when-to-use-typeddatatable-instead-of-dataconnection"></a><span data-ttu-id="c5806-107">何時使用 TypedDataTable 而非 DataConnection</span><span class="sxs-lookup"><span data-stu-id="c5806-107">When to use TypedDataTable instead of DataConnection</span></span>  
 <span data-ttu-id="c5806-108">在下列情況下使用 TypedDataTable 代替 DataConnection：</span><span class="sxs-lookup"><span data-stu-id="c5806-108">Use TypedDataTable instead of DataConnection in the following instances:</span></span>  
  
-   <span data-ttu-id="c5806-109">必須進行資料變更但資料表沒有主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c5806-109">Data changes need to be made but the table does not have a primary key.</span></span> <span data-ttu-id="c5806-110">藉由使用讓資料變更**DataConnection**，主索引鍵為必要。</span><span class="sxs-lookup"><span data-stu-id="c5806-110">To make data changes by using **DataConnection**, a primary key is required.</span></span> <span data-ttu-id="c5806-111">因此，如果沒有主索引鍵， **TypedDataTable**是唯一可行的方法。</span><span class="sxs-lookup"><span data-stu-id="c5806-111">Therefore, if there is no primary key, **TypedDataTable** is the only viable approach.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c5806-112">規則引擎只會更新記憶體中的值**TypedDataTable**。</span><span class="sxs-lookup"><span data-stu-id="c5806-112">The rule engine only updates the values in memory for a **TypedDataTable**.</span></span> <span data-ttu-id="c5806-113">由呼叫者決定這些變更是否為永久的。</span><span class="sxs-lookup"><span data-stu-id="c5806-113">It is up to the caller to make those changes permanent.</span></span>  
  
-   <span data-ttu-id="c5806-114">選擇性高時，即代表資料表中大部分的資料列都會通過規則條件所指定的測試。</span><span class="sxs-lookup"><span data-stu-id="c5806-114">Selectivity is high, which means that a large percentage of rows in the table will pass the tests specified as rule conditions.</span></span> <span data-ttu-id="c5806-115">在此情況下， **DataConnection**並未提供很多優點，它可能會執行最糟**TypedDataTable**。</span><span class="sxs-lookup"><span data-stu-id="c5806-115">In this case, **DataConnection** does not provide much benefit and it may perform worse than **TypedDataTable**.</span></span>  
  
-   <span data-ttu-id="c5806-116">資料表很小，通常一個資料表包含的資料列會少於 500 列。</span><span class="sxs-lookup"><span data-stu-id="c5806-116">The table is small, typically, a table that contains fewer than 500 rows.</span></span> <span data-ttu-id="c5806-117">請注意，根據規則圖形與規則引擎可用的記憶體而定，這個數字可能會更大或更小。</span><span class="sxs-lookup"><span data-stu-id="c5806-117">Note that this number could be larger or smaller depending on the rule shape and the memory available to the rule engine.</span></span>  
  
-   <span data-ttu-id="c5806-118">預期在規則集中會有規則鏈結行為。</span><span class="sxs-lookup"><span data-stu-id="c5806-118">Rule-chaining behavior is expected in a rule set.</span></span> <span data-ttu-id="c5806-119">呼叫**更新**函式上**DataConnection**不支援，但您無法叫用**DataConnection.Update**中使用的 helper 方法的規則。</span><span class="sxs-lookup"><span data-stu-id="c5806-119">Calling the **Update** function on a **DataConnection** is not supported, but you could invoke **DataConnection.Update** in a rule using a helper method.</span></span> <span data-ttu-id="c5806-120">需要規則鏈結時**TypedDataTable**是較佳選擇。</span><span class="sxs-lookup"><span data-stu-id="c5806-120">When rule chaining is required, **TypedDataTable** is a better choice.</span></span>  
  
-   <span data-ttu-id="c5806-121">資料表中一或多個資料行會保有規則不需要之非常大量的資料。</span><span class="sxs-lookup"><span data-stu-id="c5806-121">One or more columns in the table hold a very large amount of data that is not required by the rules.</span></span> <span data-ttu-id="c5806-122">影像資料庫就是一個範例，影像資料庫中的資料行會存放影像 (大量資料)、名稱、日期等。</span><span class="sxs-lookup"><span data-stu-id="c5806-122">An example is an image database, where the columns hold the image (large amount of data), name, date, and so on.</span></span> <span data-ttu-id="c5806-123">如果不需要影像，最好只選擇規則所需的資料行。</span><span class="sxs-lookup"><span data-stu-id="c5806-123">If the image is not required, it may be better to select only the columns needed by the rules.</span></span> <span data-ttu-id="c5806-124">例如，發出"SELECT name，Date from TABLE"的查詢可以是更有效率使用**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="c5806-124">For example, issuing a query such as "SELECT Name, Date from TABLE" can be more efficient than using **DataConnection**.</span></span>  
  
-   <span data-ttu-id="c5806-125">如果許多規則需要或更新相同的資料庫資料列，使用**TypedDataTable**，所有規則之間共用的資料列，如果條件為相同 (例如，Table.Column = = 5)，條件評估可以最佳化。</span><span class="sxs-lookup"><span data-stu-id="c5806-125">If many rules need or update the same database row, using a **TypedDataTable**, the row is shared between all rules, and if the condition is the same (for example, Table.Column == 5), the condition evaluation can be optimized.</span></span> <span data-ttu-id="c5806-126">與**DataConnection**，一般情況下，會使用每個規則會產生查詢**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="c5806-126">With a **DataConnection**, in general, a query is generated for each rule that uses the **DataConnection**.</span></span> <span data-ttu-id="c5806-127">雖然資料列會重複使用 (如果資料表有主索引鍵)，每次都可產生多個查詢來取得相同的資料。</span><span class="sxs-lookup"><span data-stu-id="c5806-127">Although the rows are reused (if the table has a primary key), multiple queries could be generated to get the same data each time.</span></span>  
  
## <a name="when-to-use-dataconnection-instead-of-typeddatatable"></a><span data-ttu-id="c5806-128">何時使用 DataConnection 而非 TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="c5806-128">When to use DataConnection instead of TypedDataTable</span></span>  
 <span data-ttu-id="c5806-129">在下列情況下使用 DataConnection 代替 TypedDataTable：</span><span class="sxs-lookup"><span data-stu-id="c5806-129">Use DataConnection instead of TypedDataTable in the following instances:</span></span>  
  
-   <span data-ttu-id="c5806-130">資料表包含大量的資料列，但選擇性很低，即只有少數的資料列符合規則條件。</span><span class="sxs-lookup"><span data-stu-id="c5806-130">The table contains a large number of rows, but selectivity is low—only a small percentage of rows will satisfy the rule conditions.</span></span>  
  
-   <span data-ttu-id="c5806-131">只有一個資料庫資料表是大的，規則中所使用的所有其他物件只擁有少數的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c5806-131">Only one database table is large; all other objects used in the rule have a small number of instances.</span></span> <span data-ttu-id="c5806-132">在最壞的狀況下，對資料庫執行的查詢數目會等於規則中所使用之所有其他執行個體的產品。</span><span class="sxs-lookup"><span data-stu-id="c5806-132">In the worst case, the number of queries executed against the database is equal to the product of all the other instances used in the rule.</span></span>  
  
-   <span data-ttu-id="c5806-133">規則僅由連結的條件所組成，在這些規則中所使用的是資料庫資料表以外的物件。</span><span class="sxs-lookup"><span data-stu-id="c5806-133">Rules consist exclusively of conjunctive conditions and objects other than database table are used in these rules.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5806-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5806-134">See Also</span></span>  
 [<span data-ttu-id="c5806-135">商務規則引擎中的資料存取</span><span class="sxs-lookup"><span data-stu-id="c5806-135">Data Access in the Business Rule Engine</span></span>](../core/data-access-in-the-business-rule-engine.md)