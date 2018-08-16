---
title: 訊息結構描述的 Insert、 Update、 Delete 和選取作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b8de271-67db-4279-8f95-0b4dd92fa3c4
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15bb515eee9a052852952f0ec245f8c954953a9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218230"
---
# <a name="message-schemas-for-insert-update-delete-and-select-operations"></a>訊息結構描述，插入、 更新、 刪除和選取作業
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]呈現基本 Insert、 Update、 Delete 和 Oracle E-business Suite 中的每個介面資料表和基礎資料庫中的每個資料表的 Select 作業。 配接器也會提供諸如 Oracle E-business Suite 中的每個介面檢視和基礎資料庫中的每個檢視的選取作業。 這些作業執行適當的 SQL 陳述式 WHERE 子句所限定。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用這些作業中的強型別記錄和資料錄集。  
  
## <a name="message-structure-for-basic-operations"></a>訊息結構的基本作業  
 下表顯示所公開的基本作業的 XML 訊息結構[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]Oracle E-business Suite 介面資料表與介面檢視和基礎資料庫資料表和檢視表。 作業的目標物件的訊息動作中指定，而且也會出現在 目標命名空間。  
  
> [!NOTE]
>  資料表之後，請參閱屬性描述。  
  
|作業|XML 訊息|Description|SQL 配接器執行|  
|---------------|-----------------|-----------------|---------------------------------|  
|Insert|`<Insert xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <RECORDSET>     <InsertRecord>       <[FIELD1_NAME] InlineValue="value">[value1]</[FIELD1_NAME]>       <[FIELD2_NAME] InlineValue="value">[value2]</[FIELD2_NAME]>       …     </InsertRecord>   </RECORDSET> </Insert>`|值**InlineValue**屬性，如果指定，會覆寫項目的值。|`INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …) VALUES (value1, value2, …);`|  
|插入回應|`<InsertResponse xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <InsertResult>[rows inserted]</InsertResult> </InsertResponse>`|插入的資料列數會傳入**InsertResult**項目。|--|  
|Select|`<Select xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>   <FILTER>WHERE_clause</FILTER> </Select>`|選取的查詢會使用 WHERE 子句篩選條件的項目中指定的目標資料表上執行。 結果集包含以逗號分隔的清單中指定的資料行名稱中的資料行**COLUMN_NAMES**項目。<br /><br /> **重要事項：** 這是唯一適用於介面檢視和資料庫檢視的作業。|`SELECT COLUMN_list FROM TABLE_NAME WHERE WHERE_clause;`|  
|選取回應|`<SelectResponse  xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <SelectResult>     <SelectRecord>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </SelectRecord>   </SelectResult> </SelectResponse>`|SELECT 查詢所產生的結果集。|--|  
|Update|`<Update xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <RECORDSET>     <[FIELD1_NAME]>value1</[FIELD1_NAME]>     <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …   </RECORDSET>   <FILTER>WHERE_clause</FILTER> </Update>`|資料列符合 where 子句中指定**篩選**更新項目中指定的值為**資料錄集**。 中所指定的資料行**資料錄集**項目會在每個相符的資料列中更新。|`UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE WHERE_clause;`|  
|更新回應|`<UpdateResponse xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <UpdateResult>[rows inserted]</UpdateResult> </UpdateResponse>`|更新資料列數目會傳入**UpdateResult**項目。|--|  
|DELETE|`<Delete xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <FILTER>WHERE_clause</FILTER> </Delete>`|資料列符合 WHERE 子句所指定**篩選**會刪除項目。|`DELETE FROM [TABLE_NAME] WHERE WHERE_clause;`|  
|刪除回應|`<DeleteResponse xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <DeleteResult>[rows deleted]</DeleteResult> </DeleteResponse>`|刪除資料列數會傳入**DeleteResult**項目。|--|  
  
 屬性描述：  
  
 [版本] = 訊息版本字串。例如， http://schemas.microsoft.com/OracleEBS/2008/05 。  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [APP_NAME] = 應用程式簡短名稱。  
  
 [INTERFACETABLE_NAME] = 介面資料表的名稱。  
  
 [FIELD1_NAME] = 表格欄位名稱。  
  
 [COLUMN_list] = 資料行的逗號分隔的清單。  
  
 [WHERE_clause] = WHERE_clause 作業; 使用 SELECT 陳述式例如，識別碼 > 10。  
  
> [!IMPORTANT]
>  介面檢視、 資料庫資料表和資料庫檢視上的基本作業的訊息結構介面資料表上會有相同，但作業的命名空間指定介面檢視、 資料庫資料表或資料庫檢視，而非介面資料表。  
  
## <a name="message-actions-for-basic-operations"></a>基本作業的訊息動作  
 下表顯示的訊息動作[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]介面資料表並在 Oracle E-business Suite 中，介面檢視、 資料表和基礎資料庫中的檢視上的基本作業使用。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用的介面資料表、 檢視介面、 資料庫資料表時或訊息動作中指定的資料庫檢視來判斷作業的目標。  
  
> [!NOTE]
>  資料表之後，請參閱實體描述。  
  
|作業|訊息的動作|範例|  
|---------------|--------------------|-------------|  
|Insert|**應用程式**: InterfaceTables/Insert / [SHORT_NAME] / [APP_NAME] / [TABLE_NAME]<br /><br /> **資料庫**： 資料表/Insert / [SCHEMA] / [TABLE_NAME]|**應用程式**: InterfaceTables/插入/SQLGL/GL/GL_ALLOC_HISTORY<br /><br /> **資料庫**： 資料表/插入/GL/GL_ALLOC_HISTORY|  
|插入回應|**應用程式**: InterfaceTables/Insert / [SHORT_NAME] / [APP_NAME] / [TABLE_NAME] / 回應<br /><br /> **資料庫**： 資料表/Insert / [SCHEMA] / [TABLE_NAME] / 回應|**應用程式**: InterfaceTables/插入/SQLGL/GL/GL_ALLOC_HISTORY/回應<br /><br /> **資料庫**： 資料表/插入/GL/GL_ALLOC_HISTORY/回應|  
|Select|**應用程式**: InterfaceTables/Select / [SHORT_NAME] / [APP_NAME] / [TABLE_NAME]<br /><br /> **資料庫**： 選取的資料表 / / [SCHEMA] / [TABLE_NAME]|**應用程式**: InterfaceTables/Select/SQLGL/GL/GL_ALLOC_HISTORY<br /><br /> **資料庫**： 資料表/Select/GL/GL_ALLOC_HISTORY|  
|選取回應|**應用程式**: InterfaceTables/Select / [SHORT_NAME] / [APP_NAME] / [TABLE_NAME] / 回應<br /><br /> **資料庫**： 選取的資料表 / / [SCHEMA] / [TABLE_NAME] / 回應|**應用程式**: InterfaceTables/Select/SQLGL/GL/GL_ALLOC_HISTORY/回應<br /><br /> **資料庫**： 資料表/Select/GL/GL_ALLOC_HISTORY/回應|  
|Update|**應用程式**: InterfaceTables/更新 / [SHORT_NAME] / [APP_NAME] / [TABLE_NAME]<br /><br /> **資料庫**： 資料表/更新 / [SCHEMA] / [TABLE_NAME]|**應用程式**: InterfaceTables/更新/SQLGL/GL/GL_ALLOC_HISTORY<br /><br /> **資料庫**： 資料表/更新/GL/GL_ALLOC_HISTORY|  
|更新回應|**應用程式**: InterfaceTables/更新 / [SHORT_NAME] / [APP_NAME] / [TABLE_NAME] / 回應<br /><br /> **資料庫**： 資料表/更新 / [SCHEMA] / [TABLE_NAME] / 回應|**應用程式**: InterfaceTables/更新/SQLGL/GL/GL_ALLOC_HISTORY/回應<br /><br /> **資料庫**： 資料表/更新/GL/GL_ALLOC_HISTORY/回應|  
|DELETE|**應用程式**: InterfaceTables/刪除 / [SHORT_NAME] / [APP_NAME] / [TABLE_NAME]<br /><br /> **資料庫**： 資料表/刪除 / [SCHEMA] / [TABLE_NAME]|**應用程式**: InterfaceTables/刪除/SQLGL/GL/GL_ALLOC_HISTORY<br /><br /> **資料庫**： 資料表/刪除/GL/GL_ALLOC_HISTORY|  
|刪除回應|**應用程式**: InterfaceTables/刪除 / [SHORT_NAME] / [APP_NAME] / [TABLE_NAME] / 回應<br /><br /> **資料庫**： 資料表/刪除 / [SCHEMA] / [TABLE_NAME] / 回應|**應用程式**: InterfaceTables/刪除/SQLGL/GL/GL_ALLOC_HISTORY/回應<br /><br /> **資料庫**： 資料表/刪除/GL/GL_ALLOC_HISTORY/回應|  
  
 實體描述：  
  
-   [結構描述]-集合的 Oracle 成品 (例如，GL)。  
  
-   [名稱]-資料表 (例如，GL_ALLOC_HISTORY) 的名稱。  
  
> [!IMPORTANT]
>  介面檢視的選取作業的訊息動作不同處在於相同的介面資料表中，「 InterfaceViews"取代"InterfaceTables。 」 同樣地，資料庫檢視的選取作業的訊息動作是相同的資料庫資料表中，不同之處在於 「 檢視 」 會取代"Tables"。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)