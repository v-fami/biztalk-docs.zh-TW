---
title: 訊息結構描述的基本 Insert、 Update、 Delete，然後選取資料表和檢視表上的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations on tables, message actions for
- table operations, message actions for
- table operations, message structure for
- operations on tables, message schemas for
- table operations, message schemas for
- operations on tables, message structure for
ms.assetid: 8228d5e6-14af-49e0-b34b-be03aea59189
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7f815f88144c2cb3659614c517fdc224c601e27
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989191"
---
# <a name="message-schemas-for-the-basic-insert-update-delete-and-select-operations-on-tables-and-views"></a><span data-ttu-id="3514f-102">訊息結構描述的基本插入、 更新、 刪除和選取資料表和檢視上的作業</span><span class="sxs-lookup"><span data-stu-id="3514f-102">Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views</span></span>
<span data-ttu-id="3514f-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]介面基本 Insert、 Update、 Delete 和 Select 的作業，每個資料表，並檢視 Oracle 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="3514f-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces basic Insert, Update, Delete, and Select operations for each table and view in the Oracle database.</span></span> <span data-ttu-id="3514f-104">這些作業會執行適當的 SQL 陳述式的 WHERE 子句所限定。</span><span class="sxs-lookup"><span data-stu-id="3514f-104">These operations perform the appropriate SQL statement qualified by a WHERE clause.</span></span> <span data-ttu-id="3514f-105">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]這些作業中使用強型別記錄和記錄集。</span><span class="sxs-lookup"><span data-stu-id="3514f-105">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses strongly-typed records and record sets in these operations.</span></span>  

## <a name="message-structure-for-basic-table-operations"></a><span data-ttu-id="3514f-106">基本的資料表作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="3514f-106">Message Structure for Basic Table Operations</span></span>  
 <span data-ttu-id="3514f-107">下表顯示基本的資料表作業所公開的 XML 訊息結構[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]Oracle 資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="3514f-107">The following table shows the XML message structure for the basic table operations exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] on Oracle database tables.</span></span> <span data-ttu-id="3514f-108">作業的目標資料表中的訊息動作指定，也會出現在 目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="3514f-108">The target table for an operation is specified in the message action and also appears in the target namespace.</span></span>  

### <a name="insert"></a><span data-ttu-id="3514f-109">Insert</span><span class="sxs-lookup"><span data-stu-id="3514f-109">Insert</span></span>  
<span data-ttu-id="3514f-110">有下列類型的插入作業。</span><span class="sxs-lookup"><span data-stu-id="3514f-110">There are the following types of Insert operations.</span></span> <span data-ttu-id="3514f-111">訊息可以包含一種插入作業。</span><span class="sxs-lookup"><span data-stu-id="3514f-111">A message can contain only one kind of Insert operation.</span></span>

- <span data-ttu-id="3514f-112">多個記錄插入，是在目標資料表中插入的記錄提供強型別資料集。</span><span class="sxs-lookup"><span data-stu-id="3514f-112">Multiple Record Insert inserts the supplied record set of strongly-typed data into the target table.</span></span>
- <span data-ttu-id="3514f-113">在多個記錄插入每一筆記錄，您可以指定呼叫的選擇性屬性的值**InlineValue**。</span><span class="sxs-lookup"><span data-stu-id="3514f-113">For each record in a multiple record insert, you can specify value for an optional attribute called **InlineValue**.</span></span> <span data-ttu-id="3514f-114">如果指定，它會覆寫元素的值。</span><span class="sxs-lookup"><span data-stu-id="3514f-114">If specified, it overrides the value of the element.</span></span>
- <span data-ttu-id="3514f-115">Bulk Insert 插入目標資料表的查詢項目中指定的 SELECT 查詢所傳回的記錄集。</span><span class="sxs-lookup"><span data-stu-id="3514f-115">Bulk Insert inserts the record set returned by a SELECT query specified in the QUERY element into the target table.</span></span> <span data-ttu-id="3514f-116">這是由使用 COLUMN_NAMES 元素中指定的資料行的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="3514f-116">This is done by using the comma-separated list of columns specified in the COLUMN_NAMES element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="3514f-117">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="3514f-117">XML message</span></span>  

<span data-ttu-id="3514f-118">**多個記錄插入**</span><span class="sxs-lookup"><span data-stu-id="3514f-118">**Multiple record insert**</span></span>  
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

<span data-ttu-id="3514f-119">SQL 配接器所執行： `INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …)VALUES (value1, value2, …);`</span><span class="sxs-lookup"><span data-stu-id="3514f-119">SQL executed by the adapter: `INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …)VALUES (value1, value2, …);`</span></span>


<span data-ttu-id="3514f-120">**大量插入**</span><span class="sxs-lookup"><span data-stu-id="3514f-120">**Bulk Insert**</span></span>  
```
<Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">
<COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>
<QUERY>[SELECT_query]</QUERY>
</Insert>
```

<span data-ttu-id="3514f-121">SQL 配接器所執行： `INSERT INTO TABLE_NAME (COLUMN_list) SELECT_query;`</span><span class="sxs-lookup"><span data-stu-id="3514f-121">SQL executed by the adapter: `INSERT INTO TABLE_NAME (COLUMN_list) SELECT_query;`</span></span>

### <a name="insert-response"></a><span data-ttu-id="3514f-122">插入回應</span><span class="sxs-lookup"><span data-stu-id="3514f-122">Insert Response</span></span>
<span data-ttu-id="3514f-123">InsertResult 項目中，會傳回插入的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="3514f-123">The number of rows inserted is returned in the InsertResult element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="3514f-124">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="3514f-124">XML message</span></span>  

```
<InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<InsertResult>[rows inserted]</InsertResult> 
</InsertResponse>
```

### <a name="select"></a><span data-ttu-id="3514f-125">Select</span><span class="sxs-lookup"><span data-stu-id="3514f-125">Select</span></span>
<span data-ttu-id="3514f-126">使用 WHERE 子句篩選項目中指定的目標資料表執行 SELECT 查詢。</span><span class="sxs-lookup"><span data-stu-id="3514f-126">A SELECT query is performed on the target table using the WHERE clause specified in the FILTER element.</span></span> <span data-ttu-id="3514f-127">結果集包含 COLUMN_NAMES 元素中指定的資料行名稱的逗號分隔清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="3514f-127">The result set contains the columns in the comma-separated list of column names specified in the COLUMN_NAMES element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="3514f-128">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="3514f-128">XML message</span></span>  
```
<Select xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>   
<FILTER>WHERE_clause</FILTER> 
</Select>
```

<span data-ttu-id="3514f-129">SQL 配接器所執行： `SELECT COLUMN_list FROM TABLE_NAME WHERE WHERE_clause;`</span><span class="sxs-lookup"><span data-stu-id="3514f-129">SQL executed by the adapter: `SELECT COLUMN_list FROM TABLE_NAME WHERE WHERE_clause;`</span></span>

### <a name="select-response"></a><span data-ttu-id="3514f-130">選取回應</span><span class="sxs-lookup"><span data-stu-id="3514f-130">Select Response</span></span>
<span data-ttu-id="3514f-131">SELECT 查詢所產生的結果集。</span><span class="sxs-lookup"><span data-stu-id="3514f-131">The result set generated by the SELECT query.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="3514f-132">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="3514f-132">XML message</span></span>  
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

### <a name="update"></a><span data-ttu-id="3514f-133">Update</span><span class="sxs-lookup"><span data-stu-id="3514f-133">Update</span></span>
<span data-ttu-id="3514f-134">資料列符合 where 子句篩選項目中指定更新資料錄集中指定的值。</span><span class="sxs-lookup"><span data-stu-id="3514f-134">Rows that match the where clause specified in the FILTER element are updated to the values specified in the RECORDSET.</span></span> <span data-ttu-id="3514f-135">在每個相符的資料列中，會更新資料錄集中指定的資料行。</span><span class="sxs-lookup"><span data-stu-id="3514f-135">Only the columns that are specified in the RECORDSET are updated in each matching row.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="3514f-136">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="3514f-136">XML message</span></span>  
```
<Update xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<RECORDSET>     
<[FIELD1_NAME]>value1</[FIELD1_NAME]>     
<[FIELD2_NAME]>value2</[FIELD2_NAME]>       
…   
</RECORDSET>   
<FILTER>WHERE_clause</FILTER> </Update>
```

<span data-ttu-id="3514f-137">SQL 配接器所執行： `UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE WHERE_clause;`</span><span class="sxs-lookup"><span data-stu-id="3514f-137">SQL executed by the adapter: `UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE WHERE_clause;`</span></span>

### <a name="update-response"></a><span data-ttu-id="3514f-138">更新回應</span><span class="sxs-lookup"><span data-stu-id="3514f-138">Update Response</span></span>
<span data-ttu-id="3514f-139">更新資料列數目傳回 UpdateResult 項目中。</span><span class="sxs-lookup"><span data-stu-id="3514f-139">The number of rows updated is returned in the UpdateResult element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="3514f-140">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="3514f-140">XML message</span></span>  
```
<UpdateResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<UpdateResult>[rows inserted]</UpdateResult> 
</UpdateResponse>
```

### <a name="delete"></a><span data-ttu-id="3514f-141">DELETE</span><span class="sxs-lookup"><span data-stu-id="3514f-141">Delete</span></span>
<span data-ttu-id="3514f-142">刪除資料列符合 WHERE 子句篩選項目所指定。</span><span class="sxs-lookup"><span data-stu-id="3514f-142">Rows matching the WHERE clause specified by the FILTER element are deleted.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="3514f-143">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="3514f-143">XML message</span></span> 
```
<Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<FILTER>WHERE_clause</FILTER> 
</Delete>
```

<span data-ttu-id="3514f-144">SQL 配接器所執行： `DELETE FROM [TABLE_NAME] WHERE WHERE_clause;`</span><span class="sxs-lookup"><span data-stu-id="3514f-144">SQL executed by the adapter: `DELETE FROM [TABLE_NAME] WHERE WHERE_clause;`</span></span>

### <a name="delete-response"></a><span data-ttu-id="3514f-145">刪除回應</span><span class="sxs-lookup"><span data-stu-id="3514f-145">Delete Response</span></span>
<span data-ttu-id="3514f-146">刪除資料列數目傳回 DeleteResult 項目中。</span><span class="sxs-lookup"><span data-stu-id="3514f-146">The number of rows deleted is returned in the DeleteResult element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="3514f-147">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="3514f-147">XML message</span></span> 
```
<DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<DeleteResult>[rows inserted]</DeleteResult> 
</DeleteResponse>
```

  | <span data-ttu-id="3514f-148">預留位置的值</span><span class="sxs-lookup"><span data-stu-id="3514f-148">Placeholder value</span></span>| <span data-ttu-id="3514f-149">描述</span><span class="sxs-lookup"><span data-stu-id="3514f-149">Description</span></span> |
  | --- | --- |
  | <span data-ttu-id="3514f-150">[版本]</span><span class="sxs-lookup"><span data-stu-id="3514f-150">[VERSION]</span></span> | <span data-ttu-id="3514f-151">訊息版本字串;比方說， `http://Microsoft.LobServices.OracleDB/2007/03`</span><span class="sxs-lookup"><span data-stu-id="3514f-151">The message version string; for example, `http://Microsoft.LobServices.OracleDB/2007/03`</span></span>|
  | <span data-ttu-id="3514f-152">[結構描述]</span><span class="sxs-lookup"><span data-stu-id="3514f-152">[SCHEMA]</span></span> | <span data-ttu-id="3514f-153">Oracle 成品、 的集合比方說， `SCOTT`</span><span class="sxs-lookup"><span data-stu-id="3514f-153">Collection of Oracle artifacts; for example, `SCOTT`</span></span>|
  | <span data-ttu-id="3514f-154">[名稱]</span><span class="sxs-lookup"><span data-stu-id="3514f-154">[TABLE_NAME]</span></span> | <span data-ttu-id="3514f-155">資料表的名稱比方說， `EMP`</span><span class="sxs-lookup"><span data-stu-id="3514f-155">Name of the table; for example, `EMP`</span></span>|
  | <span data-ttu-id="3514f-156">[FIELD1_NAME]</span><span class="sxs-lookup"><span data-stu-id="3514f-156">[FIELD1_NAME]</span></span> | <span data-ttu-id="3514f-157">資料表的欄位名稱;比方說， `EMPNAME`</span><span class="sxs-lookup"><span data-stu-id="3514f-157">Table field name; for example, `EMPNAME`</span></span>|
  | <span data-ttu-id="3514f-158">[COLUMN_list]</span><span class="sxs-lookup"><span data-stu-id="3514f-158">[COLUMN_list]</span></span> | <span data-ttu-id="3514f-159">以逗號分隔清單中的資料行;比方說， `NAME`</span><span class="sxs-lookup"><span data-stu-id="3514f-159">Comma-separated list of columns; for example, `NAME`</span></span>|
  | <span data-ttu-id="3514f-160">[SELECT_query]</span><span class="sxs-lookup"><span data-stu-id="3514f-160">[SELECT_query]</span></span> | <span data-ttu-id="3514f-161">Bulk Insert 作業; 的查詢項目中指定 SQL SELECT 陳述式比方說， `SELECT * from MyTable`</span><span class="sxs-lookup"><span data-stu-id="3514f-161">A SQL SELECT statement specified in the QUERY element of a Bulk Insert operation; for example, `SELECT * from MyTable`</span></span>|
  | <span data-ttu-id="3514f-162">[W]</span><span class="sxs-lookup"><span data-stu-id="3514f-162">[WHERE_clause]</span></span> | <span data-ttu-id="3514f-163">W 作業; 所使用的 SELECT 陳述式比方說， `ID > 10`</span><span class="sxs-lookup"><span data-stu-id="3514f-163">WHERE_clause for the SELECT statement used for the operation; for example, `ID > 10`</span></span>|

> [!IMPORTANT]
>  <span data-ttu-id="3514f-164">在檢視上的基本資料表作業的訊息結構相同資料表，但是作業的命名空間指定檢視，而不是資料表： `<Insert xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`。</span><span class="sxs-lookup"><span data-stu-id="3514f-164">The message structure for the basic table operations on views is the same as that on tables, but the namespace for the operation specifies a view rather than a table: `<Insert xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`.</span></span>  

## <a name="message-actions-for-basic-table-operations"></a><span data-ttu-id="3514f-165">基本的資料表作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="3514f-165">Message Actions for Basic Table Operations</span></span>  
 <span data-ttu-id="3514f-166">下表顯示所使用的訊息動作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]資料表的基本資料表作業。</span><span class="sxs-lookup"><span data-stu-id="3514f-166">The following table shows the message actions that are used by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] for the basic table operations on tables.</span></span> <span data-ttu-id="3514f-167">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]用以判斷作業的目標資料表中的訊息動作指定的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="3514f-167">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses the table name specified in the message action to determine the target table of the operation.</span></span>  


|    <span data-ttu-id="3514f-168">作業</span><span class="sxs-lookup"><span data-stu-id="3514f-168">Operation</span></span>    |                    <span data-ttu-id="3514f-169">訊息的動作</span><span class="sxs-lookup"><span data-stu-id="3514f-169">Message Action</span></span>                     |                                    <span data-ttu-id="3514f-170">範例</span><span class="sxs-lookup"><span data-stu-id="3514f-170">Example</span></span>                                    |
|-----------------|-------------------------------------------------------|-------------------------------------------------------------------------------|
|     <span data-ttu-id="3514f-171">Insert</span><span class="sxs-lookup"><span data-stu-id="3514f-171">Insert</span></span>      |     <span data-ttu-id="3514f-172">[VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 插入</span><span class="sxs-lookup"><span data-stu-id="3514f-172">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Insert</span></span>      |     http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert      |
| <span data-ttu-id="3514f-173">插入回應</span><span class="sxs-lookup"><span data-stu-id="3514f-173">Insert Response</span></span> | <span data-ttu-id="3514f-174">[VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 插入/回應</span><span class="sxs-lookup"><span data-stu-id="3514f-174">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Insert/response</span></span> | http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert/response |
|     <span data-ttu-id="3514f-175">Select</span><span class="sxs-lookup"><span data-stu-id="3514f-175">Select</span></span>      |     <span data-ttu-id="3514f-176">[VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 選取</span><span class="sxs-lookup"><span data-stu-id="3514f-176">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Select</span></span>      |     http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select      |
| <span data-ttu-id="3514f-177">選取回應</span><span class="sxs-lookup"><span data-stu-id="3514f-177">Select Response</span></span> | <span data-ttu-id="3514f-178">[VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / Select/回應</span><span class="sxs-lookup"><span data-stu-id="3514f-178">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Select/response</span></span> | http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select/response |
|     <span data-ttu-id="3514f-179">Update</span><span class="sxs-lookup"><span data-stu-id="3514f-179">Update</span></span>      |     <span data-ttu-id="3514f-180">[VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 更新</span><span class="sxs-lookup"><span data-stu-id="3514f-180">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Update</span></span>      |     http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update      |
| <span data-ttu-id="3514f-181">更新回應</span><span class="sxs-lookup"><span data-stu-id="3514f-181">Update Response</span></span> | <span data-ttu-id="3514f-182">[VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 更新/回應</span><span class="sxs-lookup"><span data-stu-id="3514f-182">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Update/response</span></span> | http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update/response |
|     <span data-ttu-id="3514f-183">DELETE</span><span class="sxs-lookup"><span data-stu-id="3514f-183">Delete</span></span>      |     <span data-ttu-id="3514f-184">[VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 刪除</span><span class="sxs-lookup"><span data-stu-id="3514f-184">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Delete</span></span>      |     http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete      |
| <span data-ttu-id="3514f-185">刪除回應</span><span class="sxs-lookup"><span data-stu-id="3514f-185">Delete Response</span></span> | <span data-ttu-id="3514f-186">[VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / Delete/回應</span><span class="sxs-lookup"><span data-stu-id="3514f-186">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Delete/response</span></span> | http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete/response |

 <span data-ttu-id="3514f-187">[VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.OracleDB/2007/03。</span><span class="sxs-lookup"><span data-stu-id="3514f-187">[VERSION] = The message version string; for example, http://Microsoft.LobServices.OracleDB/2007/03.</span></span>  

 <span data-ttu-id="3514f-188">[SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="3514f-188">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  

 <span data-ttu-id="3514f-189">[TABLE_NAME] = 資料表的名稱比方說，EMP。</span><span class="sxs-lookup"><span data-stu-id="3514f-189">[TABLE_NAME] = Name of the table; for example, EMP.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="3514f-190">檢視作業的訊息動作是相同的資料表不同之處在於 「 檢視 」 取代 「 資料表 」;比方說， `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/``View``/EMPVIEW/Insert`。</span><span class="sxs-lookup"><span data-stu-id="3514f-190">The message action for an operation on a view is the same as that for a table except that "View" replaces "Table"; for example, `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/``View``/EMPVIEW/Insert`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3514f-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3514f-191">See Also</span></span>  
 [<span data-ttu-id="3514f-192">BizTalk Adapter for Oracle Database 的訊息和訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="3514f-192">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)