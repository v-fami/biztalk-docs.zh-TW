---
title: "Insert、 Update、 Delete 和 Oracle 資料表和檢視表上的 Select 作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations, on tables and views
- operations, performing
- data manipulation language
- Delete operation
- Insert operation
- Update operation
- DELETE statement
- DML operation
- Select operation
- INSERT statement
- UPDATE statement
ms.assetid: af65fac4-3c16-40c4-ae7a-9c1757223f99
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04770dd5004d46df93da71b910cc228be1751ae7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="insert-update-delete-and-select-operations-on-oracle-tables-and-views"></a>插入、 更新、 刪除和選取 Oracle 資料表和檢視表上的作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現每個 Oracle 資料庫資料表和檢視上的標準作業的一組。 藉由使用這些作業，您可以執行簡單的 SQL INSERT、 UPDATE、 SELECT、 及 DELETE 陳述式 WHERE 子句，在目標資料表 （或檢視） 所限定。 這些作業也稱為資料操作語言 (DML) 作業。 若要執行更複雜的作業，例如 SQL SELECT 查詢，會使用聯結運算子，您可以使用 SQLEXECUTE 操作。 如需 SQLEXECUTE 操作的詳細資訊，請參閱[SQLEXECUTE 操作 Oracle 資料庫中](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md)。  
  
 下表顯示對 DML 作業的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援：  
  
|作業|Description|  
|---------------|-----------------|  
|Insert|執行插入作業的目標資料表或檢視。 插入作業支援多個記錄或大量插入到目標資料表或檢視表：<br /><br /> -多個記錄插入作業會將資料列插入資料表或檢視根據提供的資料錄集。<br /><br /> -在大量插入作業會將資料列插入資料表或檢視根據提供 SQL SELECT 查詢和資料行的清單。 此查詢會傳回記錄插入目標資料表資料行清單為基礎。<br /><br /> 插入作業的傳回值會是插入的資料列數目。<br /><br /> **注意：**這兩個多個記錄插入以及大量插入不能合併在相同的訊息。<br /><br /> **InlineValue**<br /><br /> 在多個記錄插入作業中的所有簡單資料記錄，您可以選擇指定呼叫的選擇性屬性的值來覆寫記錄的值**InlineValue**。 InlineValue 屬性可以用來計算的值插入資料表或檢視表，例如擴展成日期資料行的主索引鍵的資料行使用順序，或插入 （使用 SYSDATE） 的系統日期。 例如，在下列的 INSERT 陳述式：<br /><br /> `<Insert xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY">   <RECORDSET>     <ACCOUNTACTIVITYRECORDINSERT>       <ACCOUNT>10001</ACCOUNT>       <EMPNAME>John</EMPNAME>       <AMOUNT>1500</AMOUNT>       <TRANSDATE InlineValue="SYSDATE">2008-06-21T15:52:19</TRANSDATE>       </ACCOUNTACTIVITYRECORDINSERT >   </RECORDSET> </Insert>`<br /><br /> 即使"2008年-06-21T15:52:19 」 是指定為 TRANSDATE 資料行，InlineValue 屬性，「"SYSDATE，值的值 （系統日期） 會插入至目標資料表。<br /><br /> 同時使用 InlineValue 屬性：<br /><br /> 為避免 InlineValue 屬性使用常數值。 例如，在 INSERT 陳述式，如果您指定`<EMPNAME InlineValue="John"/>`則會導致錯誤。 這是因為 InlineValue 屬性的值會傳遞做為的是 Oracle 中，並在此情況下*John*傳遞至 Oracle 資料庫時，這不是預期的值 (預期的值是*'John'*)。 您必須使用單引號員工名稱。 例如： `<EMPNAME InlineValue="’John’"/>`。<br /><br /> -如果您想要用於 InlineValue 屬性中的 select 查詢，您必須以括號括住 SELECT 陳述式，並也請確定選取的查詢會擷取單一記錄。 例如： `<EMPNAME InlineValue="(SELECT NAME FROM MS_SAMPLE_EMPLOYEES WHERE ID=123)"/>`。<br /><br /> **注意：**如果元素標示為 NOT NULL 的 Oracle 資料庫中，您就必須指定該元素的值，即使您已指定內嵌值。 無法執行此動作將會導致結構描述驗證失敗。|  
|Select|執行 SQL SELECT 查詢目標資料表或檢視根據提供的資料行名稱和指定 SQL WHERE 子句的篩選條件字串清單。<br /><br /> 選取作業的傳回值是強型別結果集，其中包含指定的資料行和資料列。|  
|Update|執行更新作業的目標資料表或檢視。 指定 SQL WHERE 子句的篩選字串會指定要更新的記錄。 更新的值會指定範本記錄。<br /><br /> 更新作業的傳回值是更新的資料列數目。|  
|DELETE|執行刪除作業的目標資料表或 SQL WHERE 子句的篩選條件字串中指定為基礎的檢視。<br /><br /> 刪除作業的傳回值是刪除的資料列數目。|  
  
 如需詳細資訊：  
  
-   執行這些作業使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[Insert、 Update、 Delete 和選取作業使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-using-biztalk-server-with-oracle-db.md)。  
  
-   執行這些作業使用 WCF 服務模型，請參閱[Insert、 Update、 Delete 和選取的作業，所使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md)。  
  
-   執行這些作業使用 WCF 通道模型，請參閱[在使用 WCF 通道模型的 Oracle 資料庫執行插入作業](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)。  
  
-   訊息結構和執行 DML 作業的 SOAP 動作，請參閱[基本 Insert、 Update、 Delete 和資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)