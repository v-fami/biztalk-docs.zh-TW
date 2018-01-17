---
title: "訊息結構描述的 Insert、 Update、 Delete，然後選取資料表和檢視表上的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fff9cd3-26c0-4d5c-8162-3fd7966a5020
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73270b3d096a8d72de5b339835737cc74d264c9c
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="message-schemas-for-insert-update-delete-and-select-operations-on-tables-and-views"></a>訊息結構描述，插入、 更新、 刪除和選取資料表和檢視表上的作業
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]呈現 Insert、 Update、 Delete 和 Select 作業的每個資料表和檢視 SQL Server 資料庫中的。 這些作業執行適當的 SQL 陳述式 WHERE 子句所限定。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用這些作業中的強型別記錄和資料錄集。  
  
## <a name="message-structure-for-table-operations"></a>資料表作業的訊息結構  
 下表顯示由公開的基本資料表作業的 XML 訊息結構[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]上 SQL Server 資料庫資料表。 作業的目標資料表中的訊息動作指定，而且也會出現在 目標命名空間。  
  
|運算|XML 訊息|Description|SQL 配接器執行|  
|---------------|-----------------|-----------------|---------------------------------|  
|Insert|`<Insert xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Rows>     <[TABLE_NAME]>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </[TABLE_NAME]>   </Rows> </Insert>`|提供的記錄組強型別資料插入目標資料表。|`INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …) VALUES (value1, value2, …);`|  
|插入回應|`<InsertResponse xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <InsertResult>     <long>[Value]</long>   </InsertResult> </InsertResponse>`|插入的回應訊息包含 Long 資料類型的陣列。 如果有的話，陣列就會儲存插入的資料列的識別值。 如果資料表沒有識別資料行，傳回值會是 NULL。|--|  
|Select|選取所有記錄：<br /><br /> `<Select xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Columns>*</COLUMNS>   <Query></Query> </Select>`<br /><br /> 選取特定資料行中的一組記錄：<br /><br /> `<Select xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Columns>[COLUMN_list]</COLUMNS>   <Query>where [WHERE_clause]</Query> </Select>`<br /><br /> 更新選取的作業記錄：<br /><br /> `<Select xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Columns>[COLUMN_list]</Columns>   <Query>where [WHERE_clause];UPDATE [TABLE_NAME] SET [FIELD1_NAME] = [value1] where [WHERE_clause]</Query> </Select>`|使用指定的項目中的 WHERE 子句的目標資料表執行 SELECT 查詢。 結果集包含以逗號分隔的清單中指定的資料行名稱中的資料行\<資料行\>項目。<br /><br /> 必須提供值\<資料行\>項目。 如果要擷取資料表或檢視表中的所有資料行有 * 中必須指定\<資料行\>項目。 如果必須擷取特定資料行，必須逗號分隔並在其中指定相同的順序定義這些資料表或檢視表的資料行名稱。<br /><br /> 它，才能在 SELECT 陳述式包含 WHERE 子句。 如果您不要指定 WHERE 子句，您可以刪除\<查詢\>項目，或保持空白。<br /><br /> 您可以更新使用選取的作業記錄。 UPDATE 陳述式會置於\<查詢\>選取要求 XML，以分號分隔的 WHERE 子句中的項目。 請注意，UPDATE 陳述式不會不在 SELECT 陳述式的結果集上的作業。|選取所有記錄：<br /><br /> `SELECT * FROM [TABLE_NAME] WHERE [WHERE_clause];`<br /><br /> 選取特定資料行中的一組記錄：<br /><br /> `SELECT [COLUMN_list] FROM [TABLE_NAME] WHERE [WHERE_clause];`<br /><br /> 更新選取的作業記錄：<br /><br /> `SELECT [COLUMN_list] FROM [TABLE_NAME] WHERE [WHERE_clause]; UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1 [WHERE_clause];`|  
|選取回應|`<SelectResponse  xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <SelectResult>     <[TABLE_NAME]>       <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>       <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>       …     </[TABLE_NAME]>   </SelectResult> <SelectResponse>`|強型別產生的結果集所選取的查詢。|--|  
|Update|`<SelectResponse  xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <SelectResult>     <[TABLE_NAME]>       <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>       <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>       …     </[TABLE_NAME]>   </SelectResult> </SelectResponse>`<br /><br /> `<Update xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Rows>     <RowPair>       <After>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>         …       </After>       <Before>         <[FIELD1_NAME]>[value3]</[FIELD1_NAME]>         <[FIELD2_NAME]>[value4]</[FIELD2_NAME]>         …       </Before>     </RowPair>   </Rows> </Update>`|採用做為輸入的記錄組的陣列。 每個記錄組，則為兩個強型別記錄的集合：<br /><br /> 第一次記錄 (在`<After>`元素) 對應到需要更新的新值。<br /><br /> 第二個記錄 (在`<Before>`) 對應至資料列的舊值。|`UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE [FIELD1_NAME] = value3, [FIELD2_NAME] = value4, …;`|  
|更新回應|`<UpdateResponse xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <UpdateResult>[rows updated]</UpdateResult> </UpdateResponse>`|更新資料列數目會傳入**UpdateResult**項目。|--|  
|Delete|`<Delete xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Rows>     <[TABLE_NAME]>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </[TABLE_NAME]>   </Rows> </Delete>`|--|`DELETE FROM [TABLE_NAME] WHERE [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, …;`|  
|刪除回應|`<DeleteResponse xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <DeleteResult>[rows deleted]</DeleteResult> </DeleteResponse>`|刪除資料列數會傳入**DeleteResult**項目。|--|  
  
 [版本] = 訊息版本字串。例如，http://schemas.microsoft.com/Sql/2008/05。  
  
 [SCHEMA] = 集合 SQL Server 成品。例如，dbo。  
  
 [TABLE_NAME] = 表格的名稱例如，員工。  
  
 [FIELD1_NAME] = 表格欄位的名稱。例如，名稱。  
  
 [COLUMN_list] = 以逗號分隔清單的資料行。例如，名稱、 年齡，表示法。  
  
 [SELECT_query] = Bulk Insert 作業; 查詢元素中指定的 SQL SELECT 陳述式例如，"選取 * 從 MyTable"  
  
 [WHERE_clause] = WHERE_clause 作業; 使用 SELECT 陳述式例如，識別碼 > 10。  
  
> [!IMPORTANT]
>  檢視上的基本資料表作業的訊息結構的相同資料表上會有不同之處在於檢視會取代資料表： `Insert xmlns="[VERSION]/ViewOp/[SCHEMA]/[VIEW_NAME]"`。  
  
## <a name="message-actions-for-basic-table-operations"></a>基本的資料表作業的訊息動作  
 下表顯示所使用的訊息動作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]基本資料表上的作業資料表。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]來判斷作業的目標資料表中使用的訊息動作中指定的資料表名稱。  
  
|運算|訊息的動作|範例|  
|---------------|--------------------|-------------|  
|Insert|TableOp/Insert/[SCHEMA]/[TABLE_NAME]|TableOp/Insert/dbo/Employee|  
|插入回應|TableOp/Insert/[SCHEMA]/[TABLE_NAME]/response|TableOp/Insert/dbo/Employee/response|  
|Select|TableOp/Select/[SCHEMA]/[TABLE_NAME]|TableOp/Select/dbo/Employee|  
|選取回應|TableOp/Select/[SCHEMA]/[TABLE_NAME]/response|TableOp/Select/dbo/Employee/response|  
|Update|TableOp/Update/[SCHEMA]/[TABLE_NAME]|TableOp/Update/dbo/Employee|  
|更新回應|TableOp/Update/[SCHEMA]/[TABLE_NAME]/response|TableOp/Update/dbo/Employee/response|  
|Delete|TableOp/Delete/[SCHEMA]/[TABLE_NAME]|TableOp/Delete/dbo/Employee|  
|刪除回應|TableOp/Delete/[SCHEMA]/[TABLE_NAME]/response|TableOp/Delete/dbo/Employee/response|  
  
 [SCHEMA] = 集合 SQL Server 成品。例如，dbo。  
  
 [TABLE_NAME] = 表格的名稱例如，員工。  
  
> [!IMPORTANT]
>  檢視上作業的訊息動作是相同資料表的不同之處在於 「 ViewOp"取代"TableOp";例如， `ViewOp``/Insert/dbo/Employee_View`。  
  
## <a name="see-also"></a>另請參閱  
 [訊息與 BizTalk adapter for SQL Server 的訊息結構描述](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)