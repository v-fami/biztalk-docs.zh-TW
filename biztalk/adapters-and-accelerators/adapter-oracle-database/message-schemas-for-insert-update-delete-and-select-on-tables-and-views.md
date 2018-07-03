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
# <a name="message-schemas-for-the-basic-insert-update-delete-and-select-operations-on-tables-and-views"></a>訊息結構描述的基本插入、 更新、 刪除和選取資料表和檢視上的作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]介面基本 Insert、 Update、 Delete 和 Select 的作業，每個資料表，並檢視 Oracle 資料庫中。 這些作業會執行適當的 SQL 陳述式的 WHERE 子句所限定。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]這些作業中使用強型別記錄和記錄集。  

## <a name="message-structure-for-basic-table-operations"></a>基本的資料表作業的訊息結構  
 下表顯示基本的資料表作業所公開的 XML 訊息結構[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]Oracle 資料庫資料表。 作業的目標資料表中的訊息動作指定，也會出現在 目標命名空間。  

### <a name="insert"></a>Insert  
有下列類型的插入作業。 訊息可以包含一種插入作業。

- 多個記錄插入，是在目標資料表中插入的記錄提供強型別資料集。
- 在多個記錄插入每一筆記錄，您可以指定呼叫的選擇性屬性的值**InlineValue**。 如果指定，它會覆寫元素的值。
- Bulk Insert 插入目標資料表的查詢項目中指定的 SELECT 查詢所傳回的記錄集。 這是由使用 COLUMN_NAMES 元素中指定的資料行的逗號分隔清單。

#### <a name="xml-message"></a>XML 訊息  

**多個記錄插入**  
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

SQL 配接器所執行： `INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …)VALUES (value1, value2, …);`


**大量插入**  
```
<Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">
<COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>
<QUERY>[SELECT_query]</QUERY>
</Insert>
```

SQL 配接器所執行： `INSERT INTO TABLE_NAME (COLUMN_list) SELECT_query;`

### <a name="insert-response"></a>插入回應
InsertResult 項目中，會傳回插入的資料列數目。

#### <a name="xml-message"></a>XML 訊息  

```
<InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<InsertResult>[rows inserted]</InsertResult> 
</InsertResponse>
```

### <a name="select"></a>Select
使用 WHERE 子句篩選項目中指定的目標資料表執行 SELECT 查詢。 結果集包含 COLUMN_NAMES 元素中指定的資料行名稱的逗號分隔清單中的資料行。

#### <a name="xml-message"></a>XML 訊息  
```
<Select xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>   
<FILTER>WHERE_clause</FILTER> 
</Select>
```

SQL 配接器所執行： `SELECT COLUMN_list FROM TABLE_NAME WHERE WHERE_clause;`

### <a name="select-response"></a>選取回應
SELECT 查詢所產生的結果集。

#### <a name="xml-message"></a>XML 訊息  
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

### <a name="update"></a>Update
資料列符合 where 子句篩選項目中指定更新資料錄集中指定的值。 在每個相符的資料列中，會更新資料錄集中指定的資料行。

#### <a name="xml-message"></a>XML 訊息  
```
<Update xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<RECORDSET>     
<[FIELD1_NAME]>value1</[FIELD1_NAME]>     
<[FIELD2_NAME]>value2</[FIELD2_NAME]>       
…   
</RECORDSET>   
<FILTER>WHERE_clause</FILTER> </Update>
```

SQL 配接器所執行： `UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE WHERE_clause;`

### <a name="update-response"></a>更新回應
更新資料列數目傳回 UpdateResult 項目中。

#### <a name="xml-message"></a>XML 訊息  
```
<UpdateResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<UpdateResult>[rows inserted]</UpdateResult> 
</UpdateResponse>
```

### <a name="delete"></a>DELETE
刪除資料列符合 WHERE 子句篩選項目所指定。

#### <a name="xml-message"></a>XML 訊息 
```
<Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<FILTER>WHERE_clause</FILTER> 
</Delete>
```

SQL 配接器所執行： `DELETE FROM [TABLE_NAME] WHERE WHERE_clause;`

### <a name="delete-response"></a>刪除回應
刪除資料列數目傳回 DeleteResult 項目中。

#### <a name="xml-message"></a>XML 訊息 
```
<DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<DeleteResult>[rows inserted]</DeleteResult> 
</DeleteResponse>
```

  | 預留位置的值| 描述 |
  | --- | --- |
  | [版本] | 訊息版本字串;比方說， `http://Microsoft.LobServices.OracleDB/2007/03`|
  | [結構描述] | Oracle 成品、 的集合比方說， `SCOTT`|
  | [名稱] | 資料表的名稱比方說， `EMP`|
  | [FIELD1_NAME] | 資料表的欄位名稱;比方說， `EMPNAME`|
  | [COLUMN_list] | 以逗號分隔清單中的資料行;比方說， `NAME`|
  | [SELECT_query] | Bulk Insert 作業; 的查詢項目中指定 SQL SELECT 陳述式比方說， `SELECT * from MyTable`|
  | [W] | W 作業; 所使用的 SELECT 陳述式比方說， `ID > 10`|

> [!IMPORTANT]
>  在檢視上的基本資料表作業的訊息結構相同資料表，但是作業的命名空間指定檢視，而不是資料表： `<Insert xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`。  

## <a name="message-actions-for-basic-table-operations"></a>基本的資料表作業的訊息動作  
 下表顯示所使用的訊息動作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]資料表的基本資料表作業。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]用以判斷作業的目標資料表中的訊息動作指定的資料表名稱。  


|    作業    |                    訊息的動作                     |                                    範例                                    |
|-----------------|-------------------------------------------------------|-------------------------------------------------------------------------------|
|     Insert      |     [VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 插入      |     http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert      |
| 插入回應 | [VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 插入/回應 | http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert/response |
|     Select      |     [VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 選取      |     http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select      |
| 選取回應 | [VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / Select/回應 | http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select/response |
|     Update      |     [VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 更新      |     http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update      |
| 更新回應 | [VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 更新/回應 | http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update/response |
|     DELETE      |     [VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / 刪除      |     http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete      |
| 刪除回應 | [VERSION] / [SCHEMA] /Table/ [TABLE_NAME] / Delete/回應 | http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete/response |

 [VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.OracleDB/2007/03。  

 [SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。  

 [TABLE_NAME] = 資料表的名稱比方說，EMP。  

> [!IMPORTANT]
>  檢視作業的訊息動作是相同的資料表不同之處在於 「 檢視 」 取代 「 資料表 」;比方說， `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/``View``/EMPVIEW/Insert`。  

## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 的訊息和訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)