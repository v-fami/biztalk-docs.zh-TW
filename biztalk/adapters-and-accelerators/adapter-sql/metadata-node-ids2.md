---
title: SQL 配接器在 BizTalk Adapter Pack 中的中繼資料節點識別碼 |Microsoft Docs
description: 中繼資料、 搜尋、 擷取節點型別和 SQL 元件，會公開在 SQL Server 配接器-BizTalk 配接器組件 (BAP) 中使用的識別碼
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8601a328-5380-4577-a121-c926e0fd3140
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80dd7d58f220f7c7fdf8c70851373311999927f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022620"
---
# <a name="node-types-and-ids-for-the-sql-server-adapter"></a>節點類型與 SQL Server 配接器的識別碼

## <a name="metadata-node-ids"></a>中繼資料節點識別碼
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]介面 SQL Server 資料庫成品以階層方式。 下表列出節點類型與 SQL Server 資料庫成品的節點識別碼，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]介面。 節點識別碼是使用中節點的絕對路徑**IMetadataRetrievalContractBrowse**，**搜尋**，並**GetMetadata**方法。  


| 成品的顯示名稱  |     節點類型      |                        節點識別碼                         |                    範例                     |                                                                                                                                                    描述                                                                                                                                                    |
|------------------------|--------------------|--------------------------------------------------------|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           --           |      類別目錄      |                           /                            |                       /                        | [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] 根節點。 會傳回所有第一層的節點;這包括 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業節點，並輸出的作業，所有的結構描述節點和輪詢作業節點輸入的作業。 |
|    ExecuteNonQuery     | 輸出的作業 |               GenericOp/ExecuteNonQuery                |           GenericOp/ExecuteNonQuery            |                                                                                                                  ExecuteNonQuery 作業節點。 ExecuteNonQuery 作業會傳回 WSDL。                                                                                                                  |
|     ExecuteReader      | 輸出的作業 |                GenericOp/ExecuteReader                 |            GenericOp/ExecuteReader             |                                                                                                                    ExecuteReader 作業節點。 傳回 ExecuteReader 作業的 WSDL。                                                                                                                    |
|     ExecuteScalar      | 輸出的作業 |                GenericOp/ExecuteScalar                 |            GenericOp/ExecuteScalar             |                                                                                                                    ExecuteScalar 作業節點。 ExecuteScalar 作業會傳回 WSDL。                                                                                                                    |
|        輪詢         | 輸入的作業  |                        輪詢                         |                    輪詢                     |                                                                                                                          輪詢作業節點。 輪詢作業會傳回 WSDL。                                                                                                                          |
|      通知      | 輸入的作業  |                      通知                      |                  通知                  |                                                                                                                     通知作業節點。 傳回通知作業的 WSDL。                                                                                                                     |
|       程序       |      類別目錄      |                      程序 /                       |                  程序 /                   |                                                                                                                     結構描述的程序節點。 傳回指定的結構描述的所有程序。                                                                                                                      |
|     [DB_PROCEDURE]     | 輸出的作業 |         程序 / [DB_SCHEMA] / [程序名稱]         |         程序/dbo/ADD_EMP_DETAILS          |                                                                                                                           程序 節點中。 傳回指定的程序的 WSDL。                                                                                                                           |
|         資料表         |      類別目錄      |                        資料表 /                         |                    資料表 /                     |                                                                                                                       結構描述 [資料表] 節點。 傳回針對指定的結構描述的所有資料表節點。                                                                                                                       |
|       [DB_TABLE]       |      類別目錄      |                           -                            |                       -                        |                   在資料表節點。 會傳回所有作業節點 （Insert、 Select、 Update、 Delete 與集） 指定的資料表。<br /><br /> 設定作業才會傳回包含具有下列資料類型的任何資料行的資料表： varchar （max）、 nvarchar （max） 或 varbinary （max）。                   |
|         Insert         | 輸出的作業 |         TableOp/Insert / [DB_SCHEMA] / [DB_TABLE]          |          TableOp/Insert/dbo/員工           |                                                                                                            資料表插入作業的節點。 傳回指定之資料表的插入作業的 WSDL。                                                                                                            |
|         Select         | 輸出的作業 |         TableOp/選取 / [DB_SCHEMA] / [DB_TABLE]          |          TableOp/Select/dbo/員工           |                                                                                                            資料表選取作業的節點。 傳回指定之資料表的選取作業的 WSDL。                                                                                                            |
|         Update         | 輸出的作業 |         TableOp/更新 / [DB_SCHEMA] / [DB_TABLE]          |          TableOp/更新/dbo/員工           |                                                                                                            資料表更新作業的節點。 傳回指定之資料表的更新作業的 WSDL。                                                                                                            |
|         DELETE         | 輸出的作業 |         TableOp/刪除 / [DB_SCHEMA] / [DB_TABLE]          |          TableOp/Delete/dbo/員工           |                                                                                                            資料表刪除作業的節點。 傳回指定之資料表的刪除作業的 WSDL。                                                                                                            |
|    設定 [COLUMN_NAME]    | 輸出的作業 | TableOp/WriteText / [DB_SCHEMA] / [DB_TABLE] / [COLUMN_NAME] | TableOp/WriteText/dbo/員工/Job_Description |                                          資料表集作業的節點。 傳回資料表中所指定資料行上的設定作業的 WSDL。 (只顯示如果資料表包含任何下列資料類型的資料行: (Max)、 nvarchar （max） 或 varbinary。                                           |
|         檢視          |      類別目錄      |                         檢視 /                         |                     檢視 /                     |                                                                                                                        結構描述檢視 節點。 傳回針對指定的結構描述的所有檢視節點。                                                                                                                        |
|       [DB_VIEW]        |      類別目錄      |                           -                            |                       -                        |                                                                                                        檢視節點。 傳回所有作業節點 （Insert、 Select、 Update 和 Delete） 指定的檢視。                                                                                                        |
|         Insert         | 輸出的作業 |          ViewOp/Insert / [DB_SCHEMA] / [DB_VIEW]           |        ViewOp/Insert/dbo/Employee_View         |                                                                                                             檢視插入作業的節點。 傳回指定之檢視的插入作業的 WSDL。                                                                                                             |
|         Select         | 輸出的作業 |          ViewOp/選取 / [DB_SCHEMA] / [DB_VIEW]           |        ViewOp/Select/dbo/Employee_View         |                                                                                                             檢視選取作業的節點。 傳回指定之檢視的選取作業的 WSDL。                                                                                                             |
|         Update         | 輸出的作業 |          ViewOp/更新 / [DB_SCHEMA] / [DB_VIEW]           |        ViewOp/更新/dbo/Employee_View         |                                                                                                             檢視更新作業的節點。 傳回指定之檢視的更新作業的 WSDL。                                                                                                             |
|         DELETE         | 輸出的作業 |          ViewOp/刪除 / [DB_SCHEMA] / [DB_VIEW]           |        ViewOp/Delete/dbo/Employee_View         |                                                                                                             檢視刪除作業的節點。 傳回指定之檢視的刪除作業的 WSDL。                                                                                                             |
|    純量函數    |      類別目錄      |                    ScalarFunctions /                    |                ScalarFunctions /                |                                                                                                               結構描述的純量函式節點。 傳回指定的結構描述的所有純量函式。                                                                                                                |
|   [DB_SCLR_FUNCTION]   | 輸出的作業 |     ScalarFunction / [DB_SCHEMA] / [DB_SCLR_FUNCTION]      |         ScalarFunction/dbo/GET_EMP_ID          |                                                                                                                     純量函式節點。 傳回指定的純量函式的 WSDL。                                                                                                                     |
| 資料表值函式 |      類別目錄      |                    TableFunctions /                     |                TableFunctions /                 |                                                                                                         結構描述資料表值函式節點。 傳回指定的結構描述的所有資料表值函式。                                                                                                          |
|   [DB_TBL_FUNCTION]    | 輸出的作業 |      Tablefunction 之 / [DB_SCHEMA] / [DB_TBL_FUNCTION]       |         Tablefunction 之/dbo/TVF_EMPLOYEE         |                                                                                                               資料表值函式節點。 傳回指定的資料表值函式的 WSDL。                                                                                                               |

 [DB_SCHEMA] = Collection 的 SQL Server 成品、比方說，dbo。  

 [DB_TABLE] = SQL Server 資料表的名稱例如，員工。  

 [DB_VIEW] = SQL Server 檢視; 的名稱比方說，Employee_View。  

 [DB_PROCEDURE] = SQL Server 預存程序; 的名稱比方說，ADD_EMP_DETAILS。  

 [DB_SCLR_FUNCTION] = SQL Server 純量函式; 的名稱比方說，GET_EMP_ID。  

 [DB_TBL_FUNCTION] = SQL Server 資料表值函式; 的名稱比方說，TVF_EMPLOYEE。  

## <a name="metadata-search-and-node-ids"></a>中繼資料搜尋和節點識別碼  
 中繼資料搜尋是功能強大[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]介面的一部分與其**MetadataRetrievalContract**介面。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]來支援下列 SQL Server 成品的搜尋會使用這項功能。 中繼資料搜尋範圍僅限於在其中執行搜尋作業的節點下的層級。 例如，若要搜尋的純量函式，您必須是下搜尋/純量函式 / [Schema]。 不支援遞迴搜尋。  

|成品|節點識別碼|傳回的節點類型|描述|  
|--------------|-------------|------------------------|-----------------|  
|/ （也就是根節點）|/|類別目錄|傳回符合搜尋運算式的所有結構描述節點。|  
|[DB_PROCEDURE]|/Procedure/ [DB_SCHEMA]|輸出的作業|傳回在指定的結構描述符合搜尋運算式中的程序的所有節點。|  
|[DB_TABLE]|/Table/ [DB_SCHEMA]|類別目錄|傳回資料表的所有節點中符合搜尋運算式指定結構描述。|  
|[DB_VIEW]|/View/ [DB_SCHEMA]|類別目錄|傳回檢視的所有節點中符合搜尋運算式指定結構描述。|  
|[DB_SCLR_FUNCTION]|/ScalarFunction/ [DB_SCHEMA]|輸出的作業|在指定的結構描述符合搜尋運算式中傳回純量函式的所有節點。|  
|[DB_TBL_FUNCTION]|/TableFunction/ [DB_SCHEMA]|輸出的作業|傳回在指定的結構描述符合搜尋運算式中的資料表值函式的所有節點。|  

 [DB_SCHEMA] = Collection 的 SQL Server 成品、比方說，dbo。  

 [DB_TABLE] = SQL Server 資料表的名稱例如，員工。  

 [DB_VIEW] = SQL Server 檢視; 的名稱比方說，Employee_View。  

 [DB_PROCEDURE] = SQL Server 程序; 的名稱比方說，ADD_EMP_DETAILS。  

 [DB_SCLR_FUNCTION] = SQL Server 純量函式; 的名稱比方說，GET_EMP_ID。  

 [DB_TBL_FUNCTION] = SQL Server 資料表值函式; 的名稱比方說，TVF_EMPLOYEE。  

 您可以指定任何有效的運算式，可用於 SQL Server LIKE 運算子與相容的搜尋運算式。 例如，若要執行 結構描述中包含的資料表中的 搜尋[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會執行下列 SQL: `SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE ‘[SEARCH_STR]’`。  

 下表列出特殊字元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]搜尋運算式中支援。  

|特殊字元|解譯|  
|-----------------------|--------------------|  
|%（百分比）|比對零或多個字元。<br /><br /> 例如，"%"會比對"A"、"AB"，"ABC"，等等。|  
|_ (底線)|只有 1 個字元會比對。<br /><br /> 例如，"A_"符合"AB"、"AC"、"AD"，依此類推。|  
|[ ]|-逸出 %_ 的特殊的意義。<br />-指定範圍或集合必須存在的字元。<br /><br /> 例如：<br /><br /> -%[%] %比對所有的名稱包含 %符號。<br />-[-f] 比對所有字元之間，以及包括 'a' 和 'f' 的名稱。<br />-[abc] 比對所有的名稱有字元 'a'、 'b' 和 'c'。|  
|[^]|指定的範圍或集合不會出現的字元。<br /><br /> 例如：<br /><br /> -[^ a-f] 比對所有沒有字元之間，以及包括 'a' 和 'f' 的名稱。<br />-[^ abc] 比對所有的名稱，並沒有字元 'a'、 'b' 和 'c'。|  

## <a name="metadata-retrieval-and-node-ids"></a>擷取中繼資料和節點識別碼  
 下表摘要說明所傳回的中繼資料特性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  

|成品|中繼資料特性|  
|--------------|------------------------------|  
|[資料表或檢視表]|<ul><li>資料表名稱。</li><li>資料表的欄位名稱。</li><li>資料表欄位資料類型會對應到簡單或複雜的 WSDL 類型。</li><li>資料表的欄位長度會對應至 facet maxLength。</li><li>資料表欄位主要索引鍵條件約束會對應至 facet minOccurs = 1。</li><li>資料欄位的 NULL 條件約束會對應至 facet isNillable = true。</li><li>資料表作業<br /><br /> <ul><li>Insert</li><li>SELECT</li><li>UPDATE</li><li>Delete</li><li>設定\<資料行名稱\></li></ul></li></ul>|  
|程序或函式|程序或函式名稱會對應至作業名稱。<br />程序或函式的參數名稱。<br />程序或函式的參數資料類型會對應至 WSDL 類型。<br />程序或函式的參數方向會對應至 WSDL 參數方向。<br />程序參數或函式參數的資料類型的長度會對應至 facet maxLength。<br />程序或函式的參數順序會對應至項目序列。<br />式函會傳回資料類型會對應至 WSDL 類型。<br />式函會傳回資料類型長度會對應至 facet maxLength。|  

 中繼資料的格式的詳細資訊，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開特定的成品和作業上的 SQL Server 資料庫，請參閱[訊息和訊息結構描述，BizTalk adapter for SQL Server](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)。  
