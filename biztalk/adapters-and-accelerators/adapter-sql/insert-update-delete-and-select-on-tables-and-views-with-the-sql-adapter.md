---
title: Insert、 Update、 Delete 和選取資料表和檢視表與 SQL 配接器的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0cc39d5-16f2-454a-8e1d-c031592439ae
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cae4dfff287414c4f9b1081face9a33bbf9da545
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225382"
---
# <a name="insert-update-delete-and-select-operations-on-tables-and-views-with-the-sql-adapter"></a>Insert、 Update、 Delete 和選取資料表和檢視表與 SQL 配接器的作業
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]呈現一組標準的作業，針對每個資料表和檢視 SQL Server 資料庫中的。 藉由使用這些作業，您可以執行簡單的 INSERT、 UPDATE、 SELECT 和 DELETE 陳述式的目標資料表或檢視的 WHERE 子句所限定。 這些作業也稱為資料操作語言 (DML) 作業。  
  
 下表顯示對 DML 作業的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援：  
  
|作業|Description|  
|---------------|-----------------|  
|Insert|執行插入作業的目標資料表或檢視。<br /><br /> -插入作業會取得記錄的陣列作為輸入。 每一筆記錄強類型的目標資料表和資料列插入資料表中的對應。<br />-您可以在提供的值的識別資料行中插入值**AllowIdentityInsert**繫結屬性設定為 TRUE。 如需有關**AllowIdentityInsert**繫結屬性，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。<br />的插入作業傳回值是 Long 資料類型的陣列。 如果有的話，這個陣列會儲存插入的資料列的識別值。 如果資料表沒有識別資料行，傳回值會是 NULL。<br /><br /> 依下列方式處理的插入作業的訊息中的某些值的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:<br /><br /> -指定的計算資料行和時間戳記資料行值都會被忽略。<br />-如果識別欄位的節點是 null，則會忽略它。<br /><br /> 如需插入作業的訊息中其他值：<br /><br /> -如果資料行指定值，該值會用於 INSERT 陳述式。<br />-如果特定的資料行的節點是 null，NULL 會用於 INSERT 陳述式。 **注意：** 有特定的記錄，可以使用 INSERT 陳述式中的任何值 （也就是未指定值的任何資料行或所有資料行值已忽略），配接器執行下列 SQL 陳述式：`insert into <table_name> default values`|  
|Select|執行 SELECT 陳述式的目標資料表或檢視的記錄 （資料行） 的陣列和查詢字串，指定 WHERE 子句為基礎。<br /><br /> -如需 SELECT 陳述式中的資料行的清單，就必須指定 a 的值。 如果要擷取資料表或檢視表中的所有資料行有 * 必須指定 SELECT 陳述式中。 如果必須擷取特定資料行，必須逗號分隔並在其中指定相同的順序定義這些資料表或檢視表的資料行名稱。<br />-在 WHERE 子句必須包含在 SELECT 陳述式。 不過，如果您不想在 WHERE 子句中指定的值，您可以刪除`Query`項目，或保持空白。<br />-選取的作業也可讓您執行更新作業。 在此情況下，UPDATE 陳述式放置於`Query`SELECT 陳述式的項目。<br /><br /> 選取作業的傳回值是強型別結果集，其中包含指定的資料行和資料列從目標資料表或檢視表。|  
|Update|執行更新作業的目標資料表或檢視。<br /><br /> -更新作業會做為輸入的記錄組的陣列。 每一筆記錄對記錄的集合，兩個，而每一筆記錄強型別到目標資料表。<br /><br /> -第一筆記錄對應到需要更新的新值，也就是說，它會對應到 UPDATE 陳述式的 SET 子句。 <br />-第二筆記錄對應到資料列的舊值，亦即，它會對應到 UPDATE 陳述式的 WHERE 子句。 **注意：** 配對的記錄特定的記錄組中，沒有任何可用的 SET 子句中的值，如果執行任何 UPDATE 陳述式。 <br />-您可以更新所提供的值的識別資料行中值**AllowIdentityInsert**繫結屬性設定為 TRUE。 如需有關**AllowIdentityInsert**繫結屬性，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 <br />的更新作業傳回值的 Int32 資料型別，並代表更新的資料列的數目。<br /> 依下列方式處理更新作業訊息中的某些值的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:<br /><br /> -指定的計算資料行和訊息的 SET 子句中的時間戳記資料行值都會被忽略。<br />-如果使用者定義型別 (UDT) 不是已排序的 UDT 資料行指定值的位元組在 where 子句會忽略。<br />-如果識別欄位的節點為 null 之訊息的 SET 子句中，則會忽略它。<br />-如果的身分識別或時間戳記資料行的節點為 null 的 WHERE 子句中的訊息，則會忽略它。<br />-如果影像、 XML、 Text 或 Ntext 資料行的節點不是 null 的 WHERE 子句中的訊息，因為無法比較這些值將會忽略為其指定的值。<br /><br /> 如需更新作業訊息中其他值：<br /><br /> -如果 UPDATE 陳述式的 SET 子句中的資料行指定值，陳述式的 SET 子句中，會使用值 (`set <column_name> = <value>`)。<br />-如果特定的資料行的節點為 null 的 SET 子句中，UPDATE 陳述式中使用 NULL (`set <column_name> = null`)。<br />-如果指定的值是資料行在 UPDATE 陳述式的 WHERE 子句，陳述式的 WHERE 子句中使用的值 (`where <column_name> = <value>`)。<br />-如果特定的資料行的節點為 null 的 UPDATE 陳述式的 WHERE 子句中，UPDATE 陳述式中使用 NULL (`where <column_name> is null`)。|  
|DELETE|執行 Delete 作業的目標資料表或檢視的記錄 （資料行名稱清單） 之目標資料表指定 WHERE 子句的篩選字串的強型別陣列為基礎。<br /><br /> 刪除作業的傳回值的 Int32 資料型別，並代表刪除資料列的數目。<br /><br /> 刪除作業的訊息中某些值會視為以下列方式由[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:<br /><br /> -如果影像、 XML、 Text 或 Ntext 資料行的節點不是 null 的 WHERE 子句中的訊息，因為無法比較這些值將會忽略為其指定的值。<br />-如果的身分識別或時間戳記資料行的節點是 null，則會忽略它。<br />-如果 UDT 不是已排序的 UDT 資料行指定值的位元組在 where 子句會忽略。<br /><br /> 如需刪除作業的訊息中其他值：<br /><br /> -在 DELETE 陳述式的 WHERE 子句如果資料行指定值，會使用值 (`where <column_name> = <value>`)。<br />-如果特定的資料行的節點是 null，DELETE 陳述式中使用 NULL (`where <column_name> is null`)。 **注意：** 如果特定的記錄，沒有值可用於 DELETE 陳述式 （也就是未指定值的任何資料行或存在所有資料行值已被忽略），配接器不會執行任何的 DELETE 陳述式。|  
  
 如需詳細資訊：  
  
-   執行這些作業使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[Insert、 update、 delete 或 select 作業使用 BizTalk Server 與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/insert-update-delete-or-select-using-the-sql-adapter-in-biztalk-server.md)。  
  
-   訊息結構和執行 DML 作業的 SOAP 動作，請參閱[Insert、 Update、 Delete 和資料表和檢視表的選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)。  
  
## <a name="see-also"></a>另請參閱  
 [連接至 SAP 系統使用配接器](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)