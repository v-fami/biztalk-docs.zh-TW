---
title: 如何處理 Null 和 DBNull |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, NULL
ms.assetid: d235c265-4947-470b-9f2d-9936ae1b88a1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b07ac74828a858b368cac5d401081a58b8602323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-handle-null-and-dbnull"></a><span data-ttu-id="7bc65-102">如何處理 Null 和 DBNull</span><span class="sxs-lookup"><span data-stu-id="7bc65-102">How to Handle Null and DBNull</span></span>
<span data-ttu-id="7bc65-103">本主題描述處理與不同型別關聯之 Null 值時的預期行為，並討論用來檢查特定欄位或成員是否為 Null 或是否存在的選項。</span><span class="sxs-lookup"><span data-stu-id="7bc65-103">This topic describes the expected behaviors when dealing with null values associated with different types, and discusses options for checking null or existence of a particular field or member.</span></span>  
  
## <a name="xml"></a><span data-ttu-id="7bc65-104">XML</span><span class="sxs-lookup"><span data-stu-id="7bc65-104">XML</span></span>  
 <span data-ttu-id="7bc65-105">以下說明適用於 XML：</span><span class="sxs-lookup"><span data-stu-id="7bc65-105">The following applies to XML:</span></span>  
  
-   <span data-ttu-id="7bc65-106">XML 值絕對不會以 Null 從文件傳回。</span><span class="sxs-lookup"><span data-stu-id="7bc65-106">An XML value will never be returned from a document as null.</span></span> <span data-ttu-id="7bc65-107">這是空字串或「不存在」的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7bc65-107">It is either an empty string or a "does not exist" error.</span></span> <span data-ttu-id="7bc65-108">若為空字串，即表示轉換特定型別時可能發生錯誤，例如在建立規則時將欄位指定為整數型別。</span><span class="sxs-lookup"><span data-stu-id="7bc65-108">When it is an empty string, an error may occur for conversion of certain types, for example, fields specified as an integer type when building rules.</span></span>  
  
-   <span data-ttu-id="7bc65-109">「 商務規則編輯器 」 不允許您將欄位設定為 null，或設定欄位的類型**物件**。</span><span class="sxs-lookup"><span data-stu-id="7bc65-109">The Business Rule Composer does not allow you to set a field to null or to set the type of a field to **object**.</span></span>  
  
-   <span data-ttu-id="7bc65-110">您可以透過物件模型將類型設**物件**。</span><span class="sxs-lookup"><span data-stu-id="7bc65-110">Through the object model you can set the type to **Object**.</span></span> <span data-ttu-id="7bc65-111">在此情況下，傳回的值是 XPath 評估結果的類型 — **float**，**布林**，或**字串**，取決於 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="7bc65-111">In this case, the value returned is the type to which the XPath evaluates— **float**, **boolean**, or **string**, depending on the XPath expression.</span></span>  
  
## <a name="net-classes"></a><span data-ttu-id="7bc65-112">.NET 類別</span><span class="sxs-lookup"><span data-stu-id="7bc65-112">.NET classes</span></span>  
 <span data-ttu-id="7bc65-113">以下說明適用於 .NET 類別：</span><span class="sxs-lookup"><span data-stu-id="7bc65-113">The following applies to .NET classes:</span></span>  
  
-   <span data-ttu-id="7bc65-114">不允許您與 null 比較，如果您傳回類型不是**物件**型別。</span><span class="sxs-lookup"><span data-stu-id="7bc65-114">You are not allowed to compare to null if your return type is not an **object** type.</span></span>  
  
-   <span data-ttu-id="7bc65-115">您可以針對不是數值型別的參數傳遞 Null 做為參數，但是依據成員的實作而定，您可能會收到執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="7bc65-115">You can pass null as a parameter for parameters that are not value types, but you may get a runtime error, depending on the implementation of the member.</span></span>  
  
-   <span data-ttu-id="7bc65-116">您可以設定欄位的型別衍生自**物件**為 null。</span><span class="sxs-lookup"><span data-stu-id="7bc65-116">You can set fields of types derived from **Object** to null.</span></span>  
  
## <a name="data-connection"></a><span data-ttu-id="7bc65-117">資料連線</span><span class="sxs-lookup"><span data-stu-id="7bc65-117">Data connection</span></span>  
 <span data-ttu-id="7bc65-118">以下說明適用於資料連線：</span><span class="sxs-lookup"><span data-stu-id="7bc65-118">The following applies to a data connection:</span></span>  
  
-   <span data-ttu-id="7bc65-119">如果資料表允許 null 資料行和資料行類型不是，您可以比較任何資料庫資料表的資料行設為 null，**文字**， **ntext**，和**映像**。</span><span class="sxs-lookup"><span data-stu-id="7bc65-119">You can compare any database table column to null, if the table allows nulls for the column and the column type is not **text**, **ntext**, and **image**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7bc65-120">「 商務規則編輯器 」 可讓您使用的類型，資料行**文字**和**ntext**，條件中。</span><span class="sxs-lookup"><span data-stu-id="7bc65-120">The Business Rule Composer allows you to use columns of type, **text** and **ntext**, in conditions.</span></span> <span data-ttu-id="7bc65-121">不過，執行原則時，您可能會收到錯誤訊息，內容如下：「除了使用 IS NULL 或 LIKE 運算子時之外，無法比較或排序 text、ntext 及 image 資料類型。」</span><span class="sxs-lookup"><span data-stu-id="7bc65-121">However, when you execute the policy, you will receive an error message, which says, "The text, ntext, and image data types cannot be compared or sorted, except when using IS NULL or LIKE operator".</span></span>  
  
-   <span data-ttu-id="7bc65-122">如果資料表允許 Null 資料行，您就可以將任何資料庫資料表資料行設定為 Null。</span><span class="sxs-lookup"><span data-stu-id="7bc65-122">You can set any database table column to null, if the table allows nulls for the column.</span></span>  
  
-   <span data-ttu-id="7bc65-123">「 商務規則編輯器 」 會自動設定成員類型的繫結**物件**，如果您比較，或設為 null 的實值類型; 如果您重設或置換引數變更回原始型別。</span><span class="sxs-lookup"><span data-stu-id="7bc65-123">The Business Rule Composer automatically sets the member type in the binding to **object**, if you compare or set to null for a value type; it changes back to the original type if you reset or replace the argument.</span></span>  
  
-   <span data-ttu-id="7bc65-124">對於字串類型，其型別變更為**物件**如果您將它設定為 null，但是保留為字串，如果與 null 進行比較。</span><span class="sxs-lookup"><span data-stu-id="7bc65-124">For a string type, it changes the type to **object** if you set it to null, but leaves it as a string if you compare against null.</span></span>  
  
-   <span data-ttu-id="7bc65-125">您無法比較或設為**DBNull.Value**從 「 商務規則編輯器 」，因為它不會變更資料行類型**物件**。</span><span class="sxs-lookup"><span data-stu-id="7bc65-125">You cannot compare or set to **DBNull.Value** from the Business Rule Composer, because it will not change the column type to **object**.</span></span>  
  
-   <span data-ttu-id="7bc65-126">此引擎會將 DBNull 值轉換為 Null 以進行比較，而且會將 Null 轉換為 DBNull 值以插入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="7bc65-126">The engine will convert a DBNull value to null for comparison and will convert null to a DBNull value for insertion into the database.</span></span>  
  
-   <span data-ttu-id="7bc65-127">測試會忽略 Null 值 (這是 SQL Server 的運作方式)。</span><span class="sxs-lookup"><span data-stu-id="7bc65-127">Tests will ignore null values (this is the way SQL Server works).</span></span> <span data-ttu-id="7bc65-128">例如，如果您擁有規則 "IF db.column > 5 THEN ."，只會測試在 db.column 中擁有值的資料列，並略過具有 Null 的資料列。</span><span class="sxs-lookup"><span data-stu-id="7bc65-128">For example, if you have the rule "IF db.column > 5 THEN .", only the rows that have a value in db.column are tested—rows with null are skipped.</span></span>  
  
## <a name="typeddatatable-and-typeddatarow"></a><span data-ttu-id="7bc65-129">TypedDataTable 和 TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="7bc65-129">TypedDataTable and TypedDataRow</span></span>  
 <span data-ttu-id="7bc65-130">以下說明適用於 TypedDataTable 和 TypedDataRow：</span><span class="sxs-lookup"><span data-stu-id="7bc65-130">The following applies to TypedDataTable and TypedDataRow:</span></span>  
  
-   <span data-ttu-id="7bc65-131">「 商務規則編輯器 」 欄位型別變更為**物件**以相同方式與**DataConnection**s。</span><span class="sxs-lookup"><span data-stu-id="7bc65-131">The Business Rule Composer changes the field type to **object** in the same manner as with **DataConnection**s.</span></span>  
  
-   <span data-ttu-id="7bc65-132">除非您與 Null 比較，否則 Null 值的測試將會失敗。</span><span class="sxs-lookup"><span data-stu-id="7bc65-132">Tests will fail for null values, unless you are comparing to null.</span></span> <span data-ttu-id="7bc65-133">例如，如果已判斷提示的任何資料列擁有 Null 值，規則 "IF db.column > 5 THEN " 就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7bc65-133">For example, there will be an error in the rule "IF db.column > 5 THEN ", if any row asserted has a null value.</span></span>  
  
     <span data-ttu-id="7bc65-134">請注意，由於條件會同時進行評估，因此諸如 "IF db.column != NULL AND db.column > 5 THEN  " 的測試仍會失敗，原因是這兩項測試可能會在每一個資料列上進行評估。</span><span class="sxs-lookup"><span data-stu-id="7bc65-134">Note that because conditions are evaluated in parallel, tests like "IF db.column != NULL AND db.column > 5 THEN  " will still fail, because both tests are potentially evaluated on every row.</span></span>  
  
## <a name="checking-for-null-or-existence"></a><span data-ttu-id="7bc65-135">檢查 Null 或存在狀況</span><span class="sxs-lookup"><span data-stu-id="7bc65-135">Checking for null or existence</span></span>  
 <span data-ttu-id="7bc65-136">編寫商務規則時，在比較欄位值之前檢查欄位是否存在是理所當然的。</span><span class="sxs-lookup"><span data-stu-id="7bc65-136">When writing business rules, it is natural to check for the existence of a field before comparing its value.</span></span> <span data-ttu-id="7bc65-137">不過，如果欄位是 Null 或不存在，比較值將會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="7bc65-137">However, if the field is null or does not exist, comparing the value will cause an error.</span></span> <span data-ttu-id="7bc65-138">假設您有下列規則：</span><span class="sxs-lookup"><span data-stu-id="7bc65-138">Assume you have the following rule:</span></span>  
  
 <span data-ttu-id="7bc65-139">IF Product/Quantity Exists AND Product/Quantity > 1</span><span class="sxs-lookup"><span data-stu-id="7bc65-139">IF Product/Quantity Exists AND Product/Quantity > 1</span></span>  
  
 <span data-ttu-id="7bc65-140">如果 Product/Quantity 不存在，則會在規則中擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="7bc65-140">An error will be thrown in the rule if Product/Quantity does not exist.</span></span> <span data-ttu-id="7bc65-141">避免這個問題的其中一種方式是將父節點傳遞給協助程式方法；如果項目值存在，協助程式方法就會傳回項目值，如果項目值不存在，則會傳回其他項目。</span><span class="sxs-lookup"><span data-stu-id="7bc65-141">One of the ways to circumvent this problem is to pass a parent node to a helper method that returns the element value if it exists or something else if it does not.</span></span> <span data-ttu-id="7bc65-142">請參閱下列規則。</span><span class="sxs-lookup"><span data-stu-id="7bc65-142">See the following rules.</span></span>  
  
 <span data-ttu-id="7bc65-143">**規則 1**</span><span class="sxs-lookup"><span data-stu-id="7bc65-143">**Rule 1**</span></span>  
  
 <span data-ttu-id="7bc65-144">IF EXISTS(Product/Quantity) THEN ASSERT(CREATEOBJECT(typeof(Helper), Product/Quantity)</span><span class="sxs-lookup"><span data-stu-id="7bc65-144">IF EXISTS(Product/Quantity) THEN ASSERT(CREATEOBJECT(typeof(Helper), Product/Quantity)</span></span>  
  
 <span data-ttu-id="7bc65-145">**規則 2**</span><span class="sxs-lookup"><span data-stu-id="7bc65-145">**Rule 2**</span></span>  
  
 <span data-ttu-id="7bc65-146">IF Helper.Value == X THEN...</span><span class="sxs-lookup"><span data-stu-id="7bc65-146">IF Helper.Value == X THEN...</span></span>  
  
 <span data-ttu-id="7bc65-147">另一種可能的解決方法是建立如下的規則：</span><span class="sxs-lookup"><span data-stu-id="7bc65-147">Another possible solution is to create a rule like the following:</span></span>  
  
 <span data-ttu-id="7bc65-148">IF Product/Quantity Exist Then CheckQuantityAndDoSomething(Product/Quantity)</span><span class="sxs-lookup"><span data-stu-id="7bc65-148">IF Product/Quantity Exist Then CheckQuantityAndDoSomething(Product/Quantity)</span></span>  
  
 <span data-ttu-id="7bc65-149">在上述範例中，CheckQuantityAndDoSomething 函數會檢查參數值，並在符合條件時執行。</span><span class="sxs-lookup"><span data-stu-id="7bc65-149">In the preceding example, the CheckQuantityAndDoSomething function will check the parameter value and execute if the condition is met.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bc65-150">或者，您可以修改 XPath**欄位**來攔截任何錯誤，但它的 XML 事實的屬性不是建議的方法。</span><span class="sxs-lookup"><span data-stu-id="7bc65-150">Alternatively, you can modify the XPath **Field** property for the XML fact to catch any errors, but it is not the recommended approach.</span></span>