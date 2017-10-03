---
title: "訊息結構描述的基本 Insert、 Update、 Delete，然後選取資料表和檢視表上的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations on tables, message actions for
- table operations, message actions for
- table operations, message structure for
- operations on tables, message schemas for
- table operations, message schemas for
- operations on tables, message structure for
ms.assetid: 8228d5e6-14af-49e0-b34b-be03aea59189
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 571a6a192ca85eb0bd3e5abeb8ef8f3715818236
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-basic-insert-update-delete-and-select-operations-on-tables-and-views"></a><span data-ttu-id="8fd69-102">訊息結構描述基本的插入、 更新、 刪除和選取資料表和檢視表上的作業</span><span class="sxs-lookup"><span data-stu-id="8fd69-102">Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views</span></span>
<span data-ttu-id="8fd69-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]介面基本 Insert、 Update、 Delete 和 Select 的作業，每個資料表，並檢視 Oracle 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="8fd69-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces basic Insert, Update, Delete, and Select operations for each table and view in the Oracle database.</span></span> <span data-ttu-id="8fd69-104">這些作業執行適當的 SQL 陳述式 WHERE 子句所限定。</span><span class="sxs-lookup"><span data-stu-id="8fd69-104">These operations perform the appropriate SQL statement qualified by a WHERE clause.</span></span> <span data-ttu-id="8fd69-105">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用這些作業中的強型別記錄和資料錄集。</span><span class="sxs-lookup"><span data-stu-id="8fd69-105">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses strongly-typed records and record sets in these operations.</span></span>  
  
## <a name="message-structure-for-basic-table-operations"></a><span data-ttu-id="8fd69-106">基本的資料表作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="8fd69-106">Message Structure for Basic Table Operations</span></span>  
 <span data-ttu-id="8fd69-107">下表顯示由公開的基本資料表作業的 XML 訊息結構[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]Oracle 資料庫資料表上。</span><span class="sxs-lookup"><span data-stu-id="8fd69-107">The following table shows the XML message structure for the basic table operations exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] on Oracle database tables.</span></span> <span data-ttu-id="8fd69-108">作業的目標資料表中的訊息動作指定，而且也會出現在 目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="8fd69-108">The target table for an operation is specified in the message action and also appears in the target namespace.</span></span>  

### <a name="insert"></a><span data-ttu-id="8fd69-109">Insert</span><span class="sxs-lookup"><span data-stu-id="8fd69-109">Insert</span></span>  
<span data-ttu-id="8fd69-110">有下列類型的插入作業。</span><span class="sxs-lookup"><span data-stu-id="8fd69-110">There are the following types of Insert operations.</span></span> <span data-ttu-id="8fd69-111">訊息可以包含一種插入作業。</span><span class="sxs-lookup"><span data-stu-id="8fd69-111">A message can contain only one kind of Insert operation.</span></span>

- <span data-ttu-id="8fd69-112">多個記錄插入插入目標資料表所提供的記錄組強型別資料。</span><span class="sxs-lookup"><span data-stu-id="8fd69-112">Multiple Record Insert inserts the supplied record set of strongly-typed data into the target table.</span></span>
- <span data-ttu-id="8fd69-113">在多個記錄插入每一筆記錄，您可以指定呼叫的選擇性屬性值**InlineValue**。</span><span class="sxs-lookup"><span data-stu-id="8fd69-113">For each record in a multiple record insert, you can specify value for an optional attribute called **InlineValue**.</span></span> <span data-ttu-id="8fd69-114">如果指定，它會覆寫項目的值。</span><span class="sxs-lookup"><span data-stu-id="8fd69-114">If specified, it overrides the value of the element.</span></span>
- <span data-ttu-id="8fd69-115">Bulk Insert 插入到目標資料表中查詢項目指定的 SELECT 查詢所傳回的記錄集。</span><span class="sxs-lookup"><span data-stu-id="8fd69-115">Bulk Insert inserts the record set returned by a SELECT query specified in the QUERY element into the target table.</span></span> <span data-ttu-id="8fd69-116">這是使用逗號分隔清單指定 COLUMN_NAMES 項目中的資料行。</span><span class="sxs-lookup"><span data-stu-id="8fd69-116">This is done by using the comma-separated list of columns specified in the COLUMN_NAMES element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="8fd69-117">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="8fd69-117">XML message</span></span>  

<span data-ttu-id="8fd69-118">**多個記錄插入**</span><span class="sxs-lookup"><span data-stu-id="8fd69-118">**Multiple record insert**</span></span>  
```
<Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<RECORDSET>     
<[TABLE_NAME]RECORDINSERT>       
<[FIELD1_NAME InlineValue="value"]>value1</[FIELD1_NAME]>       
<[FIELD2_NAME InlineValue="value"]>value2</[FIELD2_NAME]>       
…     
</[TABLE_NAME]RECORDINSERT>       
<[TABLE_NAME]RECORDINSERT >       
<[FIELD1_NAME InlineValue="value"]>value1</[FIELD1_NAME]>       
<[FIELD2_NAME InlineValue="value"]>value2</[FIELD2_NAME]>       
…     
</[TABLE_NAME]RECORDINSERT>     
…   
</RECORDSET> 
</Insert>
```

<span data-ttu-id="8fd69-119">SQL 配接器執行：`INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …)VALUES (value1, value2, …);`</span><span class="sxs-lookup"><span data-stu-id="8fd69-119">SQL executed by the adapter: `INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …)VALUES (value1, value2, …);`</span></span>


<span data-ttu-id="8fd69-120">**大量插入**</span><span class="sxs-lookup"><span data-stu-id="8fd69-120">**Bulk Insert**</span></span>  
```
<Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">
<COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>
<QUERY>[SELECT_query]</QUERY>
</Insert>
```

<span data-ttu-id="8fd69-121">SQL 配接器執行：`INSERT INTO TABLE_NAME (COLUMN_list) SELECT_query;`</span><span class="sxs-lookup"><span data-stu-id="8fd69-121">SQL executed by the adapter: `INSERT INTO TABLE_NAME (COLUMN_list) SELECT_query;`</span></span>

### <a name="insert-response"></a><span data-ttu-id="8fd69-122">插入回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-122">Insert Response</span></span>
<span data-ttu-id="8fd69-123">InsertResult 項目中，會傳回插入的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="8fd69-123">The number of rows inserted is returned in the InsertResult element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="8fd69-124">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="8fd69-124">XML message</span></span>  

```
<InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<InsertResult>[rows inserted]</InsertResult> 
</InsertResponse>
```

### <a name="select"></a><span data-ttu-id="8fd69-125">Select</span><span class="sxs-lookup"><span data-stu-id="8fd69-125">Select</span></span>
<span data-ttu-id="8fd69-126">選取的查詢會使用 WHERE 子句篩選條件的項目中指定的目標資料表上執行。</span><span class="sxs-lookup"><span data-stu-id="8fd69-126">A SELECT query is performed on the target table using the WHERE clause specified in the FILTER element.</span></span> <span data-ttu-id="8fd69-127">結果集包含 COLUMN_NAMES 元素中指定的資料行名稱以逗號分隔清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="8fd69-127">The result set contains the columns in the comma-separated list of column names specified in the COLUMN_NAMES element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="8fd69-128">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="8fd69-128">XML message</span></span>  
```
<Select xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>   
<FILTER>WHERE_clause</FILTER> 
</Select>
```

<span data-ttu-id="8fd69-129">SQL 配接器執行：`SELECT COLUMN_list FROM TABLE_NAME WHERE WHERE_clause;`</span><span class="sxs-lookup"><span data-stu-id="8fd69-129">SQL executed by the adapter: `SELECT COLUMN_list FROM TABLE_NAME WHERE WHERE_clause;`</span></span>

### <a name="select-response"></a><span data-ttu-id="8fd69-130">選取回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-130">Select Response</span></span>
<span data-ttu-id="8fd69-131">SELECT 查詢所產生的結果集。</span><span class="sxs-lookup"><span data-stu-id="8fd69-131">The result set generated by the SELECT query.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="8fd69-132">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="8fd69-132">XML message</span></span>  
```
<SelectResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<SelectResult>     
<[TABLE_NAME]RECORDSELECT>       
<[FIELD1_NAME]>value1</[FIELD1_NAME]>       
<[FIELD2_NAME]>value2</[FIELD2_NAME]>       
…     
</[TABLE_NAME]RECORDSELECT>   
</SelectResult> 
</SelectResponse>
``` 

### <a name="update"></a><span data-ttu-id="8fd69-133">Update</span><span class="sxs-lookup"><span data-stu-id="8fd69-133">Update</span></span>
<span data-ttu-id="8fd69-134">資料列符合 where 子句篩選條件的項目中指定會更新資料錄集中指定的值。</span><span class="sxs-lookup"><span data-stu-id="8fd69-134">Rows that match the where clause specified in the FILTER element are updated to the values specified in the RECORDSET.</span></span> <span data-ttu-id="8fd69-135">每個相符的資料列中，會更新資料錄集中指定的資料行。</span><span class="sxs-lookup"><span data-stu-id="8fd69-135">Only the columns that are specified in the RECORDSET are updated in each matching row.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="8fd69-136">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="8fd69-136">XML message</span></span>  
```
<Update xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<RECORDSET>     
<[FIELD1_NAME]>value1</[FIELD1_NAME]>     
<[FIELD2_NAME]>value2</[FIELD2_NAME]>       
…   
</RECORDSET>   
<FILTER>WHERE_clause</FILTER> </Update>
```

<span data-ttu-id="8fd69-137">SQL 配接器執行：`UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE WHERE_clause;`</span><span class="sxs-lookup"><span data-stu-id="8fd69-137">SQL executed by the adapter: `UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE WHERE_clause;`</span></span>

### <a name="update-response"></a><span data-ttu-id="8fd69-138">更新回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-138">Update Response</span></span>
<span data-ttu-id="8fd69-139">更新資料列數目會傳回 UpdateResult 項目中。</span><span class="sxs-lookup"><span data-stu-id="8fd69-139">The number of rows updated is returned in the UpdateResult element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="8fd69-140">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="8fd69-140">XML message</span></span>  
```
<UpdateResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<UpdateResult>[rows inserted]</UpdateResult> 
</UpdateResponse>
```

### <a name="delete"></a><span data-ttu-id="8fd69-141">DELETE</span><span class="sxs-lookup"><span data-stu-id="8fd69-141">Delete</span></span>
<span data-ttu-id="8fd69-142">刪除資料列符合 WHERE 子句篩選項目所指定。</span><span class="sxs-lookup"><span data-stu-id="8fd69-142">Rows matching the WHERE clause specified by the FILTER element are deleted.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="8fd69-143">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="8fd69-143">XML message</span></span> 
```
<Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<FILTER>WHERE_clause</FILTER> 
</Delete>
```

<span data-ttu-id="8fd69-144">SQL 配接器執行：`DELETE FROM [TABLE_NAME] WHERE WHERE_clause;`</span><span class="sxs-lookup"><span data-stu-id="8fd69-144">SQL executed by the adapter: `DELETE FROM [TABLE_NAME] WHERE WHERE_clause;`</span></span>

### <a name="delete-response"></a><span data-ttu-id="8fd69-145">刪除回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-145">Delete Response</span></span>
<span data-ttu-id="8fd69-146">刪除資料列數目會傳回 DeleteResult 項目中。</span><span class="sxs-lookup"><span data-stu-id="8fd69-146">The number of rows deleted is returned in the DeleteResult element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="8fd69-147">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="8fd69-147">XML message</span></span> 
```
<DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<DeleteResult>[rows inserted]</DeleteResult> 
</DeleteResponse>
```
  
  | <span data-ttu-id="8fd69-148">預留位置的值</span><span class="sxs-lookup"><span data-stu-id="8fd69-148">Placeholder value</span></span>| <span data-ttu-id="8fd69-149">Description</span><span class="sxs-lookup"><span data-stu-id="8fd69-149">Description</span></span> |
  | --- | --- |
  | <span data-ttu-id="8fd69-150">[版本]</span><span class="sxs-lookup"><span data-stu-id="8fd69-150">[VERSION]</span></span> | <span data-ttu-id="8fd69-151">訊息版本字串。例如，`http://Microsoft.LobServices.OracleDB/2007/03`</span><span class="sxs-lookup"><span data-stu-id="8fd69-151">The message version string; for example, `http://Microsoft.LobServices.OracleDB/2007/03`</span></span>|
  | <span data-ttu-id="8fd69-152">[結構描述]</span><span class="sxs-lookup"><span data-stu-id="8fd69-152">[SCHEMA]</span></span> | <span data-ttu-id="8fd69-153">Oracle 成品、 的集合例如，`SCOTT`</span><span class="sxs-lookup"><span data-stu-id="8fd69-153">Collection of Oracle artifacts; for example, `SCOTT`</span></span>|
  | <span data-ttu-id="8fd69-154">[名稱]</span><span class="sxs-lookup"><span data-stu-id="8fd69-154">[TABLE_NAME]</span></span> | <span data-ttu-id="8fd69-155">表格的名稱例如，`EMP`</span><span class="sxs-lookup"><span data-stu-id="8fd69-155">Name of the table; for example, `EMP`</span></span>|
  | <span data-ttu-id="8fd69-156">[FIELD1_NAME]</span><span class="sxs-lookup"><span data-stu-id="8fd69-156">[FIELD1_NAME]</span></span> | <span data-ttu-id="8fd69-157">表格欄位的名稱。例如，`EMPNAME`</span><span class="sxs-lookup"><span data-stu-id="8fd69-157">Table field name; for example, `EMPNAME`</span></span>|
  | <span data-ttu-id="8fd69-158">[COLUMN_list]</span><span class="sxs-lookup"><span data-stu-id="8fd69-158">[COLUMN_list]</span></span> | <span data-ttu-id="8fd69-159">以逗號分隔清單中的資料行。例如，`NAME`</span><span class="sxs-lookup"><span data-stu-id="8fd69-159">Comma-separated list of columns; for example, `NAME`</span></span>|
  | <span data-ttu-id="8fd69-160">[SELECT_query]</span><span class="sxs-lookup"><span data-stu-id="8fd69-160">[SELECT_query]</span></span> | <span data-ttu-id="8fd69-161">Bulk Insert 作業; 查詢元素中指定 SQL SELECT 陳述式例如，`SELECT * from MyTable`</span><span class="sxs-lookup"><span data-stu-id="8fd69-161">A SQL SELECT statement specified in the QUERY element of a Bulk Insert operation; for example, `SELECT * from MyTable`</span></span>|
  | <span data-ttu-id="8fd69-162">[WHERE_clause]</span><span class="sxs-lookup"><span data-stu-id="8fd69-162">[WHERE_clause]</span></span> | <span data-ttu-id="8fd69-163">WHERE_clause 作業; 使用 SELECT 陳述式例如，`ID > 10`</span><span class="sxs-lookup"><span data-stu-id="8fd69-163">WHERE_clause for the SELECT statement used for the operation; for example, `ID > 10`</span></span>|
  
> [!IMPORTANT]
>  <span data-ttu-id="8fd69-164">檢視上的基本資料表作業的訊息結構的相同資料表，但作業的命名空間指定的檢視，而不是資料表： `<Insert xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`。</span><span class="sxs-lookup"><span data-stu-id="8fd69-164">The message structure for the basic table operations on views is the same as that on tables, but the namespace for the operation specifies a view rather than a table: `<Insert xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`.</span></span>  
  
## <a name="message-actions-for-basic-table-operations"></a><span data-ttu-id="8fd69-165">基本的資料表作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="8fd69-165">Message Actions for Basic Table Operations</span></span>  
 <span data-ttu-id="8fd69-166">下表顯示所使用的訊息動作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]基本資料表上的作業資料表。</span><span class="sxs-lookup"><span data-stu-id="8fd69-166">The following table shows the message actions that are used by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] for the basic table operations on tables.</span></span> <span data-ttu-id="8fd69-167">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來判斷作業的目標資料表中使用的訊息動作中指定的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="8fd69-167">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses the table name specified in the message action to determine the target table of the operation.</span></span>  
  
|<span data-ttu-id="8fd69-168">作業</span><span class="sxs-lookup"><span data-stu-id="8fd69-168">Operation</span></span>|<span data-ttu-id="8fd69-169">訊息的動作</span><span class="sxs-lookup"><span data-stu-id="8fd69-169">Message Action</span></span>|<span data-ttu-id="8fd69-170">範例</span><span class="sxs-lookup"><span data-stu-id="8fd69-170">Example</span></span>|  
|---------------|--------------------|-------------|  
|<span data-ttu-id="8fd69-171">Insert</span><span class="sxs-lookup"><span data-stu-id="8fd69-171">Insert</span></span>|<span data-ttu-id="8fd69-172">[版本] / [SCHEMA] /Table/ [TABLE_NAME] / 插入</span><span class="sxs-lookup"><span data-stu-id="8fd69-172">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Insert</span></span>|<span data-ttu-id="8fd69-173">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert</span><span class="sxs-lookup"><span data-stu-id="8fd69-173">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert</span></span>|  
|<span data-ttu-id="8fd69-174">插入回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-174">Insert Response</span></span>|<span data-ttu-id="8fd69-175">[版本] / [SCHEMA] /Table/ [TABLE_NAME] / 插入/回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-175">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Insert/response</span></span>|<span data-ttu-id="8fd69-176">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert/response</span><span class="sxs-lookup"><span data-stu-id="8fd69-176">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert/response</span></span>|  
|<span data-ttu-id="8fd69-177">Select</span><span class="sxs-lookup"><span data-stu-id="8fd69-177">Select</span></span>|<span data-ttu-id="8fd69-178">[版本] / [SCHEMA] /Table/ [TABLE_NAME] 選取 /</span><span class="sxs-lookup"><span data-stu-id="8fd69-178">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Select</span></span>|<span data-ttu-id="8fd69-179">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select</span><span class="sxs-lookup"><span data-stu-id="8fd69-179">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select</span></span>|  
|<span data-ttu-id="8fd69-180">選取回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-180">Select Response</span></span>|<span data-ttu-id="8fd69-181">[版本] / [SCHEMA] /Table/ [TABLE_NAME] / Select/回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-181">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Select/response</span></span>|<span data-ttu-id="8fd69-182">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select/response</span><span class="sxs-lookup"><span data-stu-id="8fd69-182">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select/response</span></span>|  
|<span data-ttu-id="8fd69-183">Update</span><span class="sxs-lookup"><span data-stu-id="8fd69-183">Update</span></span>|<span data-ttu-id="8fd69-184">[版本] / [SCHEMA] /Table/ [TABLE_NAME] / 更新</span><span class="sxs-lookup"><span data-stu-id="8fd69-184">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Update</span></span>|<span data-ttu-id="8fd69-185">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update</span><span class="sxs-lookup"><span data-stu-id="8fd69-185">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update</span></span>|  
|<span data-ttu-id="8fd69-186">更新回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-186">Update Response</span></span>|<span data-ttu-id="8fd69-187">[版本] / [SCHEMA] /Table/ [TABLE_NAME] / 更新/回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-187">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Update/response</span></span>|<span data-ttu-id="8fd69-188">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update/response</span><span class="sxs-lookup"><span data-stu-id="8fd69-188">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update/response</span></span>|  
|<span data-ttu-id="8fd69-189">DELETE</span><span class="sxs-lookup"><span data-stu-id="8fd69-189">Delete</span></span>|<span data-ttu-id="8fd69-190">[版本] / [SCHEMA] /Table/ [TABLE_NAME] / 刪除</span><span class="sxs-lookup"><span data-stu-id="8fd69-190">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Delete</span></span>|<span data-ttu-id="8fd69-191">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete</span><span class="sxs-lookup"><span data-stu-id="8fd69-191">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete</span></span>|  
|<span data-ttu-id="8fd69-192">刪除回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-192">Delete Response</span></span>|<span data-ttu-id="8fd69-193">[版本] / [SCHEMA] /Table/ [TABLE_NAME] / 刪除/回應</span><span class="sxs-lookup"><span data-stu-id="8fd69-193">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Delete/response</span></span>|<span data-ttu-id="8fd69-194">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete/response</span><span class="sxs-lookup"><span data-stu-id="8fd69-194">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete/response</span></span>|  
  
 <span data-ttu-id="8fd69-195">[版本] = 訊息版本字串。例如，http://Microsoft.LobServices.OracleDB/2007/03。</span><span class="sxs-lookup"><span data-stu-id="8fd69-195">[VERSION] = The message version string; for example, http://Microsoft.LobServices.OracleDB/2007/03.</span></span>  
  
 <span data-ttu-id="8fd69-196">[SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="8fd69-196">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="8fd69-197">[TABLE_NAME] = 表格的名稱例如，EMP。</span><span class="sxs-lookup"><span data-stu-id="8fd69-197">[TABLE_NAME] = Name of the table; for example, EMP.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8fd69-198">在檢視上作業的訊息動作不同處在於相同資料表的 「 檢視 」 會取代 「 資料表 」。例如， `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/``View``/EMPVIEW/Insert`。</span><span class="sxs-lookup"><span data-stu-id="8fd69-198">The message action for an operation on a view is the same as that for a table except that "View" replaces "Table"; for example, `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/``View``/EMPVIEW/Insert`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fd69-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fd69-199">See Also</span></span>  
 [<span data-ttu-id="8fd69-200">訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="8fd69-200">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)