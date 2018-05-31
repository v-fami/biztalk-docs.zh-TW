---
title: SAP 中的 SELECT 陳述式的語法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SELECT statement, syntax for
ms.assetid: 47120d74-bf41-4622-a6bc-7b8ddc959305
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 343e96bb25a062bd524f25c770137bc64227063d
ms.sourcegitcommit: ba3c4876acc1bf3ee2961ca80c18d930a42c6696
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32320958"
---
# <a name="syntax-for-a-select-statement-in-sap"></a><span data-ttu-id="ca8a3-102">SAP 中的 SELECT 陳述式的語法</span><span class="sxs-lookup"><span data-stu-id="ca8a3-102">Syntax for a SELECT Statement in SAP</span></span>
<span data-ttu-id="ca8a3-103">下列章節說明實作針對 SELECT 查詢的文法規格[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-103">The following sections describe grammar specifications for implementing SELECT queries against the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span> <span data-ttu-id="ca8a3-104">請注意，在數個情況下，語法與基底的 TRANSACT-SQL 語法稍有不同。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-104">Notice that in several cases, the syntax is somewhat different from the base Transact-SQL syntax.</span></span>  
  
```  
SELECT {TOP <const> }[0,1] <select_list>  {INTO FILE [‘file_name’ | “file_name”]   
{DELIMITED}[0,1]}[0,1]  FROM table_name  {AS alias_name }[0,1]    
{INNER JOIN table_name {AS alias_name}[0,1] ON  <Join_Condition>}[0,1]  
{ WHERE <predicate> } [0,1] {;}[0,1]   
[OPTION 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'  
```  
  
 <span data-ttu-id="ca8a3-105">其中：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-105">Where:</span></span>  
  
-   <span data-ttu-id="ca8a3-106">**<select_list>** = `[ {table_name.}[0,1]column_name { AS alias_name } [0,1] } [ 1, …n ]`</span><span class="sxs-lookup"><span data-stu-id="ca8a3-106">**<select_list>** = `[ {table_name.}[0,1]column_name { AS alias_name } [0,1] } [ 1, …n ]`</span></span>  
  
-   <span data-ttu-id="ca8a3-107">**<Join_Condition>** = `[Alias_name.|table_name.]column_name <expr> [Alias_name.|table_name.]column_name`</span><span class="sxs-lookup"><span data-stu-id="ca8a3-107">**<Join_Condition>** = `[Alias_name.|table_name.]column_name <expr> [Alias_name.|table_name.]column_name`</span></span>  
  
-   <span data-ttu-id="ca8a3-108">**\<predicate\>** = `[ predicate [AND|OR] predicate [between|not between] predicate |  NOT predicate |  ‘(‘ predicate ‘)’ | condition ]`</span><span class="sxs-lookup"><span data-stu-id="ca8a3-108">**\<predicate\>** = `[ predicate [AND|OR] predicate [between|not between] predicate |  NOT predicate |  ‘(‘ predicate ‘)’ | condition ]`</span></span>  
  
 <span data-ttu-id="ca8a3-109">支援的條件運算式和運算式為：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-109">The supported conditions and expressions are:</span></span>  
  
-   <span data-ttu-id="ca8a3-110">**\<條件\>** = `[ expr | expr [NOT | ] BETWEEN const AND const | expr [NOT | ] LIKE const ]`</span><span class="sxs-lookup"><span data-stu-id="ca8a3-110">**\<condition\>** = `[ expr | expr [NOT | ] BETWEEN const AND const | expr [NOT | ] LIKE const ]`</span></span>  
  
-   <span data-ttu-id="ca8a3-111">**\<expr\>** = `[ const | column_name [= | ! = | > | > = | ! > | < | < = | ! < ] const | column_name | - const  | const | column_name ]`</span><span class="sxs-lookup"><span data-stu-id="ca8a3-111">**\<expr\>** = `[ const | column_name [= | ! = | > | > = | ! > | < | < = | ! < ] const | column_name | - const  | const | column_name ]`</span></span>  
  
 <span data-ttu-id="ca8a3-112">其中 **\<const\>** = `integer | real | string | ? | NULL | xml_element`。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-112">Where **\<const\>** = `integer | real | string | ? | NULL | xml_element`.</span></span>  
  
 <span data-ttu-id="ca8a3-113">**OPTION 關鍵字的值**</span><span class="sxs-lookup"><span data-stu-id="ca8a3-113">**Values for the OPTION Keyword**</span></span>  
  
 <span data-ttu-id="ca8a3-114">您可以指定為選項`OPTION '<option>'`，其中 `<option> = 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'`</span><span class="sxs-lookup"><span data-stu-id="ca8a3-114">You can specify the options as `OPTION '<option>'`, where `<option> = 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'`</span></span>  
  
-   <span data-ttu-id="ca8a3-115">**No_conversion**選項：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-115">The **no_conversion** option:</span></span>  
  
    -   <span data-ttu-id="ca8a3-116">如果**no_conversion**選項使用，然後使用對等的.NET 型別公開的資料表中的欄位。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-116">If the **no_conversion** option is used then the fields in the table are exposed using the equivalent .NET types.</span></span> <span data-ttu-id="ca8a3-117">SAP 資料類型的.NET 同等的相關資訊，請參閱[基本的 SAP 資料型別](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-117">For information about the .NET equivalent of the SAP data types, see [Basic SAP Data Types](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md).</span></span>  
  
    -   <span data-ttu-id="ca8a3-118">如果**no_conversion**未使用選項，如果欄位不需要轉換，並結束定義，然後使用對等的.NET 型別公開的資料表中的欄位。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-118">If the **no_conversion** option is not used, and if a field does not have a conversion exit defined then those fields in the table are exposed using the equivalent .NET types.</span></span> <span data-ttu-id="ca8a3-119">SAP 資料類型的.NET 同等的相關資訊，請參閱[基本的 SAP 資料型別](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-119">For information about the .NET equivalent of the SAP data types, see [Basic SAP Data Types](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md).</span></span>  
  
    -   <span data-ttu-id="ca8a3-120">當**no_conversion**未使用選項，如果欄位有轉換，並結束定義，則資料表中的欄位會公開為.NET 字串。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-120">When the **no_conversion** option is not used, and if a field has a conversion exit defined then those fields in the table are exposed as .NET String.</span></span>  
  
-   <span data-ttu-id="ca8a3-121">當設定為**batchsize\<大小\>**，執行 SELECT 陳述式會導致多個呼叫進行至 SAP 系統，並在每個呼叫中，只有\<大小\>的記錄數目擷取。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-121">When set to **batchsize \<size\>**, the execution of the SELECT statement causes multiple calls to be made to the SAP system, and in each call, only \<size\> number of records are retrieved.</span></span> <span data-ttu-id="ca8a3-122">例如，如果您指定 ' batchsize 100' 的 SELECT 查詢會擷取 100 筆記錄只能在每次呼叫 SAP 系統中的。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-122">For example, if you specify 'batchsize 100', the SELECT query retrieves 100 records only in each call to the SAP system.</span></span> <span data-ttu-id="ca8a3-123">如果**batchsize\<大小\>** 未指定，10000 的預設值會假設批次大小。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-123">If **batchsize \<size\>** is not specified, the default value of 10,000 is assumed for the batch size.</span></span> <span data-ttu-id="ca8a3-124">請注意，您應該指定根據 SAP 系統中的電腦和資料列數目的實體記憶體的批次大小的最佳值。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-124">Note that you should specify an optimum value for the batch size based on the physical memory of the computer and the number of rows in the SAP system.</span></span> <span data-ttu-id="ca8a3-125">在指定批次大小的最佳值可能會導致記憶體不足例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-125">Failure in specifying an optimum value for batch size may result in out of memory exceptions.</span></span>  
  
-   <span data-ttu-id="ca8a3-126">當設定為**disabledatavalidation**、[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不會驗證 DATS、 TIMS 和 NUMC 資料行中存在的值，但改為將其公開成字串。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-126">When set to **disabledatavalidation**, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not validate the values present in the DATS, TIMS, and NUMC columns but instead exposes them as string.</span></span>  
  
     <span data-ttu-id="ca8a3-127">這是適用於 ADO.NET 用戶端無法從 SAP 資料表在 DATS、 TIMS 和 NUMC 資料行中包含無效的資料擷取資料的情況。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-127">This is useful in scenarios where ADO.NET clients fail to retrieve data from an SAP table having invalid data in DATS, TIMS, and NUMC columns.</span></span> <span data-ttu-id="ca8a3-128">因為 SAP 允許 DATS、 TIMS 和 NUMC 資料行中有無效的資料，所以嘗試讀取資料的 ADO.NET 用戶端無法剖析無效的資料，並將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-128">Because SAP allows invalid data to be present in DATS, TIMS, and NUMC columns, ADO.NET clients attempting to read the data will not be able to parse the invalid data and will throw an exception.</span></span> <span data-ttu-id="ca8a3-129">如果**disabledatavalidation**上執行 SELECT 查詢中，設定選項[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不會剖析無效的資料，但它們擷取為字串。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-129">If the **disabledatavalidation** option is set on the SELECT query, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not parse the invalid data but extracts them as strings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ca8a3-130">您必須一律提供的值選項關鍵字在單引號中，例如，'*disabledatavalidation*'。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-130">You must always provide the values for the OPTION keyword within single quotes, for example, '*disabledatavalidation*'.</span></span>  
  
 <span data-ttu-id="ca8a3-131">如需範例陳述式，請參閱[SELECT 陳述式的範例](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-131">For example statements, see [Examples for SELECT Statement](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md).</span></span>  
  
## <a name="predicates-syntax"></a><span data-ttu-id="ca8a3-132">述詞的語法</span><span class="sxs-lookup"><span data-stu-id="ca8a3-132">Predicates Syntax</span></span>  
 <span data-ttu-id="ca8a3-133">下列指定 SELECT 陳述式中使用述詞的文法：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-133">The following specifies the grammar for using predicates in a SELECT statement:</span></span>  
  
 <span data-ttu-id="ca8a3-134">`Predicate`：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-134">`Predicate`:</span></span>  
  
```  
Predicates [AND | OR] Predicates [between|not between] Predicates | [NOT] Predicates | '(' Predicates ')' | Condition  
```  
  
 <span data-ttu-id="ca8a3-135">`Condition`：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-135">`Condition`:</span></span>  
  
```  
Expr | LExpr [NOT] BETWEEN RExpr AND RExpr | LExpr [NOT] LIKE Const  
```  
  
 <span data-ttu-id="ca8a3-136">`Expr`：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-136">`Expr`:</span></span>  
  
```  
LExpr [=|!=|>|>=|!>|<|<=|!<] RExpr>  
```  
  
 <span data-ttu-id="ca8a3-137">`LExpr`：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-137">`LExpr`:</span></span>  
  
```  
ColumnName  
```  
  
 <span data-ttu-id="ca8a3-138">`RExpr`：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-138">`RExpr`:</span></span>  
  
```  
Const | PlaceHolder  
```  
  
 <span data-ttu-id="ca8a3-139">`ColumnName`：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-139">`ColumnName`:</span></span>  
  
```  
Column | TableName.Column | '['Column']'  
```  
  
 <span data-ttu-id="ca8a3-140">`Tablename`：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-140">`Tablename`:</span></span>  
  
```  
Table | '['Table']'  
```  
  
## <a name="considerations-when-calling-a-select-statement"></a><span data-ttu-id="ca8a3-141">呼叫 SELECT 陳述式時的考量</span><span class="sxs-lookup"><span data-stu-id="ca8a3-141">Considerations When Calling a SELECT Statement</span></span>  
 <span data-ttu-id="ca8a3-142">此區段會列出使用 SELECT 陳述式時，您必須謹記在心的點[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-142">This section lists the points that you must keep in mind when using the SELECT statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
-   <span data-ttu-id="ca8a3-143">指定日期時間值時的參數或查詢中，提供的值做為字串。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-143">When specifying date-time values in parameters or queries, provide the values as a string.</span></span> <span data-ttu-id="ca8a3-144">提供 SAP 日期時間格式的日期時間字串。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-144">Provide date-time strings in the SAP date-time format.</span></span>  
  
    -   <span data-ttu-id="ca8a3-145">`SAP date format`: YYYYMMDD</span><span class="sxs-lookup"><span data-stu-id="ca8a3-145">`SAP date format`: YYYYMMDD</span></span>  
  
         <span data-ttu-id="ca8a3-146">例如，日期 2004 年 11 月 10 SAP 查詢中是表示 '20041110'。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-146">For example, the date 2004 November 10 in a SAP query is expressed '20041110'.</span></span>  
  
         <span data-ttu-id="ca8a3-147">2004 年 11 月 10 SAPParameter p1 中為日期字串 p1。值 = '20041110'。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-147">The date 2004 November 10 in a SAPParameter p1 is the string p1.Value='20041110'.</span></span>  
  
    -   <span data-ttu-id="ca8a3-148">`SAP time format`: HHMMSS</span><span class="sxs-lookup"><span data-stu-id="ca8a3-148">`SAP time format`: HHMMSS</span></span>  
  
         <span data-ttu-id="ca8a3-149">例如，時間 10:34:32 SAP 查詢中是表示 '103432'。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-149">For example, the time 10:34:32 in a SAP query is expressed '103432'.</span></span>  
  
         <span data-ttu-id="ca8a3-150">時間 10:34:32 SAPParameter p2 中是字串 p2。值 = '103432'。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-150">The time 10:34:32 in a SAPParameter p2 is the string p2.Value='103432'.</span></span>  
  
     <span data-ttu-id="ca8a3-151">SELECT 陳述式，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]傳回`DATE`欄位值為.NET`System.DateTime`物件，並傳回`TIME`欄位值為`System.TimeSpan`物件。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-151">For a SELECT statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `DATE` field values as .NET `System.DateTime` objects, and returns `TIME` field values as `System.TimeSpan` objects.</span></span> <span data-ttu-id="ca8a3-152">如果 SAP 值`DATE`物件是否小於最小的可允許 SQL Server 的值 (`1/1/1753`)、[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]傳回此最小值， `1/1/1753`。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-152">If the value of the SAP `DATE` object is less than the minimum allowable SQL Server value (`1/1/1753`), the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns this minimum value, `1/1/1753`.</span></span>  
  
-   <span data-ttu-id="ca8a3-153">在 TOP 子句的 SELECT 查詢，當使用特殊字元"#"、"^"，"&"和"%"之前或之後的整數中，特殊字元會被忽略，雖然任何錯誤訊息，就會不引發。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-153">In the TOP clause of a SELECT query, when using the special characters "#", "^", "&", and "%" before or after an integer, the special characters are ignored, although no error message is raised.</span></span> <span data-ttu-id="ca8a3-154">例如，下列會忽略 TOP 子句的 SELECT 查詢中：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-154">For example, the following are ignored in the TOP clause of a SELECT query:</span></span>  
  
     <span data-ttu-id="ca8a3-155">\#5，5 ^，%5%或 & 5</span><span class="sxs-lookup"><span data-stu-id="ca8a3-155">\#5, 5^, %5%, or &5</span></span>  
  
     <span data-ttu-id="ca8a3-156">不過，使用這些字元之間的整數，5 $5，的確會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-156">However, using these characters between integers, as in 5$5, does throw an error.</span></span>  
  
-   <span data-ttu-id="ca8a3-157">傳回資料表的結構描述中的資料行名稱會傳回為所有大寫字元。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-157">Column names returned in a schema for a table are returned as all uppercase characters.</span></span> <span data-ttu-id="ca8a3-158">例如，查詢結果集的欄位`Last Name`傳回的資料行標題`LAST NAME`。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-158">For example, a query result set on the field `Last Name` returns the column heading `LAST NAME`.</span></span> <span data-ttu-id="ca8a3-159">若要避免唯一性建議使用全部大寫的 SELECT 陳述式中的衝突。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-159">To avoid uniqueness conflicts, using all uppercase in SELECT statements is recommended.</span></span>  
  
-   <span data-ttu-id="ca8a3-160">LIKE 子句的 SELECT 查詢，在只百分比符號、"%"（適用於任何零或多個字元字串） 和底線， **"_"** （適用於任何單一字元），是允許的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-160">In the LIKE clause of a SELECT query, only the percent sign, "%" (for any string of zero or more characters), and underscore, **"_"** (for any single character), are allowable special characters.</span></span> <span data-ttu-id="ca8a3-161">所有其他特殊字元會被視為字串值，而且會被忽略。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-161">All other special characters are considered string values and are ignored.</span></span>  
  
-   <span data-ttu-id="ca8a3-162">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]用於 Z_EXTRACT_DATA_OO RFC SAP 系統上執行 SELECT 查詢。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-162">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses the Z_EXTRACT_DATA_OO RFC to perform SELECT queries on the SAP system.</span></span> <span data-ttu-id="ca8a3-163">RFC 支援讀取資料的資料表，其滿足下列條件：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-163">The RFC supports reading data from tables that satisfy the following conditions:</span></span>  
  
    -   <span data-ttu-id="ca8a3-164">TabClass 資料表是 TRANSP、 叢集或集區。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-164">TabClass for the table is TRANSP, CUSTER, or POOL.</span></span>  
  
    -   <span data-ttu-id="ca8a3-165">TabClass 檢視，而 ViewClass D 或 p。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-165">TabClass is VIEW and ViewClass is either D or P.</span></span>  
  
     <span data-ttu-id="ca8a3-166">請確定在 SELECT 陳述式會從符合這些條件的資料表讀取資料。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-166">Make sure the SELECT statement reads data from tables that satisfy these conditions.</span></span>  
  
-   <span data-ttu-id="ca8a3-167">可能需要超過 255 個字元，例如字串、 RAWSTRING、 LRAW、 VARC 和 LCHAR 的資料類型的值不能在選取的查詢。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-167">Values of data types that can take more than 255 characters, for example STRING, RAWSTRING, LRAW, VARC, and LCHAR cannot be used in a SELECT query.</span></span> <span data-ttu-id="ca8a3-168">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]使用隨附的自訂 RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，Z_EXTRACT_DATA_OO，在 SAP 系統上執行 SELECT 查詢。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-168">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC shipped with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], Z_EXTRACT_DATA_OO, to perform SELECT queries on the SAP system.</span></span> <span data-ttu-id="ca8a3-169">這個自訂 RFC 不支援任何可能需要超過 255 個字元的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-169">This custom RFC does not support any data type that can take more than 255 characters.</span></span>  
  
-   <span data-ttu-id="ca8a3-170">支援在 SELECT 陳述式中的欄位或資料行的最大數目是 1000年。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-170">The maximum number of columns or fields that are supported in a SELECT statement is 1000.</span></span>  
  
-   <span data-ttu-id="ca8a3-171">支援在 WHERE 子句中的述詞的最大數目為 100。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-171">The maximum number of predicates supported in a WHERE clause is 100.</span></span>  
  
-   <span data-ttu-id="ca8a3-172">不支援選取的相同欄位多次相同的 SELECT 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-172">Selecting the same field multiple times in the same SELECT statement is not supported.</span></span> <span data-ttu-id="ca8a3-173">自訂 RFC (Z_EXTRACT_DATA_OO) 所使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]之前執行的陳述式中移除重複的欄位。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-173">The custom RFC (Z_EXTRACT_DATA_OO) used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] removes the duplicate fields from the statement before executing.</span></span> <span data-ttu-id="ca8a3-174">例如，此陳述式：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-174">For example, this statement:</span></span>  
  
     `SELECT BUKRS, BUKRS, BUKRS from T001`  
  
     <span data-ttu-id="ca8a3-175">執行類似此陳述式撰寫：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-175">executes as though written like this statement:</span></span>  
  
     `SELECT BUKRS from T001`  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="ca8a3-176"> SELECT 陳述式中不支援重複的別名名稱。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-176"> does not support duplicate alias names in a SELECT statement.</span></span> <span data-ttu-id="ca8a3-177">因此，下列 SELECT 陳述式會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-177">Therefore, the following SELECT statement throws an error:</span></span>  
  
    ```  
    SELECT KUNNR AS [MYKNA1], JMJAH AS MYKNA1 from KNA1 where KUNNR LIKE 'T-S62A08' AND JMJAH=1995  
    ```  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="ca8a3-178"> 不支援重複的資料行名稱的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-178"> does not support a SELECT statement with duplicate column names.</span></span> <span data-ttu-id="ca8a3-179">因此，下列 SELECT 陳述式會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-179">Therefore, the following SELECT statement throws an error:</span></span>  
  
    ```  
    SELECT KUNNR AS [MYKNA1], KUNNR AS MYKNA2 from KNA1 where MYKNA2='T-S62A08'  
    ```  
  
-   <span data-ttu-id="ca8a3-180">SAP 不會儲存在資料表中的 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-180">SAP does not store NULL values in the tables.</span></span> <span data-ttu-id="ca8a3-181">如此一來，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援 SELECT 陳述式中的"IS NULL"值。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-181">As a result, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support an "IS NULL" value in a SELECT statement.</span></span> <span data-ttu-id="ca8a3-182">因此，下列 SELECT 陳述式會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-182">Therefore, the following SELECT statement throws an error:</span></span>  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where CITY IS NULL AND NAME1 LIKE '%MODE%'  
    ```  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="ca8a3-183"> 不支援 ORDER BY 子句的 SELECT 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-183"> does not support an ORDER BY clause in a SELECT statement.</span></span> <span data-ttu-id="ca8a3-184">因此，下列 SELECT 陳述式會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-184">Therefore, the following SELECT statement throws an error:</span></span>  
  
    ```  
    SELECT NAME1  AS [MYNAME],  LAND1, KUNNR  from KNA1 where NAME1 LIKE '%MODE%'  ORDER BY NAME1  ASC  
    ```  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="ca8a3-185"> 不支援指定星號 （\*） 來選取 SAP 資料表中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-185"> does not support specifying an asterisk (\*) to select all the fields in an SAP table.</span></span> <span data-ttu-id="ca8a3-186">因此，下列 SELECT 陳述式會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-186">Therefore, the following SELECT statement throws an error:</span></span>  
  
    ```  
    SELECT spfli.* from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
     <span data-ttu-id="ca8a3-187">若要選取所有的欄位，您必須指定個別的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-187">To select all the fields, you must specify the field names individually.</span></span>  
  
-   <span data-ttu-id="ca8a3-188">SELECT 陳述式的一部分，您可以指定 SELECT 陳述式的輸出寫入的檔案。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-188">As part of the SELECT statement, you can specify a file to which the output of the SELECT statement will be written.</span></span> <span data-ttu-id="ca8a3-189">不過，如果輸出檔位於網路共用，請確定 SAP 服務執行的 SAP 服務帳戶具有網路共用的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-189">However, if the output file is on a network share, make sure the SAP service account under which the SAP service is running has write permission to the network share.</span></span> <span data-ttu-id="ca8a3-190">例如：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-190">For example:</span></span>  
  
    ```  
    SELECT * into file '\\share\output.txt' from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
     <span data-ttu-id="ca8a3-191">在上述範例中，SAP 服務帳戶必須具有名稱的 「 共用。 」 的網路共用的寫入權限</span><span class="sxs-lookup"><span data-stu-id="ca8a3-191">In the preceding example, the SAP service account must have write permission to the network share with the name "share."</span></span>  
  
-   <span data-ttu-id="ca8a3-192">SELECT 陳述式使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]SELECT 查詢中支援的引數值參數名稱。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-192">A SELECT statement using [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports parameter names for argument values in a SELECT query.</span></span> <span data-ttu-id="ca8a3-193">不過，請確定您遵循這些規則相對於參數名稱：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-193">However, make sure you follow these rules with respect to parameter names:</span></span>  
  
    -   <span data-ttu-id="ca8a3-194">在選取的查詢中，「\@"符號必須在參數名稱前面。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-194">In the SELECT query, an "\@" symbol must precede the parameter name.</span></span>  
  
    -   <span data-ttu-id="ca8a3-195">「\@"符號後面必須接著字母字元 （A 到 Z 或 a 到 z）。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-195">The "\@" symbol must be followed by an alphabetic character (A-Z or a-z).</span></span>  
  
    -   <span data-ttu-id="ca8a3-196">參數名稱只能包含英數字元 (A-Z、 a-z 或 0-9) 和特殊字元。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-196">The parameter name can contain alphanumeric characters (A-Z, a-z, or 0-9) and special characters.</span></span> <span data-ttu-id="ca8a3-197">可以包含在參數名稱的唯一特殊字元是底線"_"、"#"的雜湊。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-197">The only special characters that can be included in the parameter name are underscore "_" and hash "#".</span></span>  
  
-   <span data-ttu-id="ca8a3-198">當您在檢視上執行 SELECT 查詢時，請確定基底資料表的所有主索引鍵資料行也會出現在檢視中。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-198">When you run a SELECT query on a View, make sure that all the primary key columns of the base table are also present in the View.</span></span> <span data-ttu-id="ca8a3-199">此外，作法是，您必須將標記資料行在檢視中的主索引鍵資料行也。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-199">Also, as a practice, you must mark the columns as primary key columns in the View also.</span></span>  
  
     <span data-ttu-id="ca8a3-200">如果主索引鍵資料行不存在於檢視，在檢視上的 SELECT 查詢將會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-200">If the primary key columns are not present in the View, a SELECT query on the View will result in an exception.</span></span>  
  
-   <span data-ttu-id="ca8a3-201">當您選取的型別 LRAW 欄位的資料表上執行 SELECT 查詢時，請確定您選取對應的 PREC 欄位。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-201">When you run a SELECT query on a table to select fields of type LRAW, make sure you select the corresponding PREC field.</span></span> <span data-ttu-id="ca8a3-202">此外，PREC 欄位必須在 SELECT 子句中的 LRAW 欄位之前，立即出現。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-202">Also, the PREC field must appear immediately before the LRAW field in the SELECT clause.</span></span>  
  
     <span data-ttu-id="ca8a3-203">資料表中的每個 LRAW 欄位有相對應的 PREC 欄位 LRAW 欄位中儲存資料的長度。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-203">Every LRAW field in a table has a corresponding PREC field that stores the length of data in the LRAW field.</span></span> <span data-ttu-id="ca8a3-204">明確 PREC 欄位之 SELECT 子句中指定 LRAW 欄位可能會導致不正確所擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-204">Specifying just the LRAW field in the SELECT clause without the PREC field may result in incorrect data being extracted.</span></span>  
  
-   <span data-ttu-id="ca8a3-205">在 SAP 系統中，字元的比較會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-205">In an SAP system, character comparisons are case sensitive.</span></span> <span data-ttu-id="ca8a3-206">因此，下列兩項查詢可能傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-206">So, the following two queries may return different results.</span></span>  
  
    ```  
    SELECT * FROM KNA1 WHERE LAND1 LIKE 'D%'  
    ```  
  
     <span data-ttu-id="ca8a3-207">And</span><span class="sxs-lookup"><span data-stu-id="ca8a3-207">And</span></span>  
  
    ```  
    SELECT * FROM KNA1 WHERE LAND1 LIKE 'd%'  
    ```  
  
     <span data-ttu-id="ca8a3-208">請確定您在框架的 select 查詢時使用正確的情況。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-208">Make sure you use the right cases when framing a select query.</span></span> <span data-ttu-id="ca8a3-209">此外，在 SAP 系統中，並非所有資料行只能包含小寫或大寫字元。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-209">Also, in an SAP system, not all columns can contain lowercase or uppercase characters.</span></span> <span data-ttu-id="ca8a3-210">您可以使用 SAP GUI，若要找出資料表中的資料行是否儲存大寫或小寫字元。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-210">You can use the SAP GUI to find out whether a column in a table stores lowercase or uppercase characters.</span></span> <span data-ttu-id="ca8a3-211">如需有關使用 SAP GUI 的指示，請參閱[判斷是否資料行存放區小寫或大寫值](../../adapters-and-accelerators/adapter-sap/determining-whether-a-column-stores-lowercase-or-uppercase-values.md)。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-211">For instructions on using the SAP GUI, see [Determining Whether a Column Stores Lowercase or Uppercase Values](../../adapters-and-accelerators/adapter-sap/determining-whether-a-column-stores-lowercase-or-uppercase-values.md).</span></span>  
  
-   <span data-ttu-id="ca8a3-212">WHERE 條件僅支援某些資料值，欄位值的比較和*不*與其他資料表欄位值。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-212">The WHERE condition is supported only for comparison of a field value with some data value, and *not* with some other table field value.</span></span> <span data-ttu-id="ca8a3-213">因為[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援只有一個資料表選取查詢、 資料表欄位的查詢中聯結條件應該使用支援相同的聯結條件。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-213">Because the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports only one table SELECT query, table field queries in join conditions should use the join condition to support the same.</span></span>  
  
-   <span data-ttu-id="ca8a3-214">聯結條件必須包含資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-214">A join condition must contain a table name.</span></span>  
  
     <span data-ttu-id="ca8a3-215">以下是正確的 SELECT 陳述式</span><span class="sxs-lookup"><span data-stu-id="ca8a3-215">The following is a correct SELECT statement</span></span>  
  
    ```  
    select A.x, B.y from A inner join B on A.m = B.n  
    ```  
  
     <span data-ttu-id="ca8a3-216">以下是不正確的 SELECT 陳述式</span><span class="sxs-lookup"><span data-stu-id="ca8a3-216">The following is an incorrect SELECT statement</span></span>  
  
    ```  
    select A.x, B.y from A inner join B on m = n  
    ```  
  
-   <span data-ttu-id="ca8a3-217">聯結條件，左側的資料表中聯結條件應該左邊條件，而且聯結條件的右側資料表應指定聯結條件右側。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-217">In a join condition, the left table in a join condition should be on the left side of the condition, and the right table of the join condition should be specified on the right side of the join condition.</span></span>  
  
     <span data-ttu-id="ca8a3-218">以下是正確的方式來指定聯結條件：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-218">The following is the correct way of specifying a join condition:</span></span>  
  
    ```  
    select A.x, B.y from A inner join B on A.m = B.n  
    ```  
  
     <span data-ttu-id="ca8a3-219">以下是不正確的方式來指定聯結條件：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-219">The following is an incorrect way of specifying a join condition:</span></span>  
  
    ```  
    select A.x, B.y from A inner join B on B.n = A.m  
    ```  
  
-   <span data-ttu-id="ca8a3-220">SELECT 陳述式只能包含聯結子句中的 「 等於 」 狀況。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-220">A SELECT statement can only contain an “equal to” condition in a JOIN clause.</span></span> <span data-ttu-id="ca8a3-221">例如：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-221">For example:</span></span>  
  
    ```  
    select * from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
-   <span data-ttu-id="ca8a3-222">SELECT 陳述式不會擷取從 SAP 系統的字串類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-222">A SELECT statement does not retrieve columns of type STRING from the SAP system.</span></span>  
  
-   <span data-ttu-id="ca8a3-223">SELECT 陳述式必須包含單一聯結。</span><span class="sxs-lookup"><span data-stu-id="ca8a3-223">A SELECT statement must contain only a single JOIN.</span></span> <span data-ttu-id="ca8a3-224">例如：</span><span class="sxs-lookup"><span data-stu-id="ca8a3-224">For example:</span></span>  
  
    ```  
    select * from spfli inner join sflight on spfli.carrid = sflight.carrid  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ca8a3-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca8a3-225">See Also</span></span>  
 [<span data-ttu-id="ca8a3-226">關於 .NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="ca8a3-226">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)
