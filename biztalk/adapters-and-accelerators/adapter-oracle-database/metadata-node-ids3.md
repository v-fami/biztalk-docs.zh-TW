---
title: Oracle DB 配接器在 BizTalk Adapter Pack 中的中繼資料節點識別碼 |Microsoft Docs
description: 中繼資料、 搜尋、 擷取節點類型及 Oracle DB 配接器-BizTalk 配接器組件 (BAP) 中所公開的 Oracle 元件中使用的識別碼
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 523c7611-b21f-4598-ac77-ba71075db073
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53fd454b644cea6c509ec167740bd5e3c2bebb1a
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752535"
---
# <a name="node-types-and-ids-for-the-oracle-database-adapter"></a>節點類型與 Oracle 資料庫配接器的識別碼

## <a name="metadata-node-types-and-ids"></a>中繼資料的節點型別和 Id 
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表面 Oracle 資料庫成品以階層方式。 下表列出節點類型與 Oracle 資料庫成品的節點識別碼，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面。 節點識別碼是使用中節點的絕對路徑**IMetadataRetrievalContractBrowse**，**搜尋**，並**GetMetadata**方法。  

**成品的顯示名稱:-**  
節點類型： 類別目錄  
節點識別碼: /  
範例: /  
描述：[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]根節點。 會傳回所有第一層的節點;這包括 SQLEXECUTE 作業節點、 [POLLINGSTMT 作業] 節點中，以及所有的結構描述節點

**成品的顯示名稱： SQLEXECUTE**  
節點型別： 作業  
節點識別碼: [版本] / SQLEXECUTE  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE`  
描述： SQLEXECUTE 作業節點。 SQLEXECUTE 作業會傳回 WSDL。

**成品的顯示名稱： POLLINGSTMT**  
節點型別： 作業  
節點識別碼: [版本] / POLLINGSTMT  
範例 `http://Microsoft.LobServices. OracleDB/2007/03/POLLINGSTMT`  
描述： POLLINGSTMT 作業節點。 傳回 POLLINGSTMT 作業的 WSDL。

**成品的顯示名稱: [DB_SCHEMA]**  
節點類型： 類別目錄  
節點識別碼: [版本] / [DB_SCHEMA]  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT`  
描述： 結構描述節點。 傳回指定的結構描述 （資料表、 檢視、 程序、 函數和封裝） 的一般類別目錄節點。

**成品的顯示名稱： 資料表**  
節點類型： 類別目錄  
節點識別碼: [版本] / [DB_SCHEMA] / 資料表  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table`  
描述： 結構描述資料表節點。 傳回針對指定的結構描述的所有資料表節點。

**成品的顯示名稱: [DB_TABLE]**  
節點類型： 類別目錄  
節點識別碼: [版本] / [DB_SCHEMA] /Table/ [DB_TABLE]  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP`  
描述： 在資料表節點。 會傳回所有作業節點 （Insert、 Select、 Update、 Delete、 ReadLOB，與 UpdateLOB） 指定的資料表。 （ReadLOB 和 UpdateLOB 是只傳回包含 LOB 資料行的資料表）。

**成品的顯示名稱： 插入**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /Table/ [DB_TABLE] / 插入  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert`  
描述： 資料表插入作業的節點。 傳回指定之資料表的插入作業的 WSDL。

**成品的顯示名稱： 選取**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /Table/ [DB_TABLE] / 選取  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select`  
描述： 資料表選取作業的節點。 傳回指定之資料表的選取作業的 WSDL。

**成品的顯示名稱： 更新**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /Table/ [DB_TABLE] / 更新  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update`  
描述： 資料表更新作業的節點。 傳回指定之資料表的更新作業的 WSDL。

**成品的顯示名稱： 刪除**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /Table/ [DB_TABLE] / 刪除  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete`  
描述： 刪除資料表作業的節點。 傳回指定之資料表的刪除作業的 WSDL。

**成品的顯示名稱： ReadLOB**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /Table/ [DB_TABLE] / ReadLOB  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/ReadLOB`  
描述： 資料表 ReadLOB 作業節點。 傳回指定之資料表的 ReadLOB 作業 WSDL。 （只顯示如果資料表包含 LOB 資料行。）

**成品的顯示名稱： UpdateLOB**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /Table/ [DB_TABLE] / UpdateLOB  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/UpdateLOB`  
描述： 資料表 UpdateLOB 作業節點。 傳回指定之資料表的 UpdateLOB 作業 WSDL。 （只顯示如果資料表包含 LOB 資料行。）

**成品的顯示名稱： 檢視**  
節點類型： 類別目錄  
節點識別碼: [版本] / [DB_SCHEMA] / 檢視  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View`  
描述： 結構描述檢視 節點。 傳回針對指定的結構描述的所有檢視節點。

**成品的顯示名稱: [DB_VIEW]**  
節點類型： 類別目錄  
節點識別碼: [版本] / [DB_SCHEMA] /View/ [DB_VIEW]  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW`  
描述: [檢視] 節點。 傳回所有作業節點 （Insert、 Select、 Update、 Delete、 ReadLOB，與 UpdateLOB） 指定的檢視。 （ReadLOB 和 UpdateLOB 是只傳回包含 LOB 資料行的檢視）。

**成品的顯示名稱： 插入**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /View/ [DB_VIEW] / 插入  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/Insert`  
描述： 檢視插入作業的節點。 傳回指定之檢視的插入作業的 WSDL。

**成品的顯示名稱： 選取**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /View/ [DB_VIEW] / 選取  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/Select`  
描述： 檢視選取作業的節點。 傳回指定之檢視的選取作業的 WSDL。

**成品的顯示名稱： 更新**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /View/ [DB_VIEW] / 更新  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/Update`  
描述： 檢視更新作業的節點。 傳回指定之檢視的更新作業的 WSDL。

**成品的顯示名稱： 刪除**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /View/ [DB_VIEW] / 刪除  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/Delete`  
操作說明： 檢視刪除的節點。 傳回指定之檢視的刪除作業的 WSDL。

**成品的顯示名稱： ReadLOB**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /View/ [DB_VIEW] / ReadLOB  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/ReadLOB`  
描述： 檢視 ReadLOB 作業節點。 傳回指定之檢視的 ReadLOB 作業 WSDL。 （只顯示如果檢視包含 LOB 資料行。）

**成品的顯示名稱： UpdateLOB**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /View/ [DB_VIEW] / UpdateLOB  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/UpdateLOB`  
描述： 檢視更新作業的節點。 傳回指定之資料表的 UpdateLOB 作業 WSDL。 （只顯示如果檢視包含 LOB 資料行。）

**成品的顯示名稱： 程序**  
節點類型： 類別目錄  
節點識別碼: [版本] / [DB_SCHEMA] / 程序  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure`  
描述： 結構描述的程序節點。 傳回指定的結構描述的所有程序。

**成品的顯示名稱: [DB_PROCEDURE]**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /Procedure/ [DB_PROCEDURE]  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_GENREPORT`  
描述： 程序節點。 傳回指定的程序的 WSDL。

**成品的顯示名稱： 函式**  
節點類型： 類別目錄  
節點識別碼: [版本] / [DB_SCHEMA] / 函式  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function`  
描述： 結構描述函數節點。 傳回指定的結構描述的所有函式。

**成品的顯示名稱: [DB_FUNCTION]**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /Function/ [DB_FUNCTION]  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function/FN_GETUSERID`  
描述： 函式節點。 傳回指定的函式的 WSDL。

**成品的顯示名稱： 套件**  
節點類型： 類別目錄  
節點識別碼: [版本] / [DB_SCHEMA] / 套件  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package`  
封裝描述： 結構描述的節點。 傳回指定的結構描述的所有封裝。

**成品的顯示名稱: [DB_PACKAGE]**  
節點類型： 類別目錄  
節點識別碼: [版本] / [DB_SCHEMA] /Package/ [DB_PACKAGE]  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG`  
描述: [套件] 節點。 傳回所有的程序和函式，指定封裝。

**成品的顯示名稱: [PACK_PROCEDURE]**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /Package/ [DB_PACKAGE] / [PACK_PROCEDURE]  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT`  
描述： 封裝程序節點。 傳回指定之的封裝程序的 WSDL。

**成品的顯示名稱: [PACK_FUNCTION]**  
節點型別： 作業  
節點識別碼: [版本] / [DB_SCHEMA] /Package/ [DB_PACKAGE] / [PACK_FUNCTION]  
範例 `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT`  
描述： 封裝函式節點。 傳回指定的封裝函式的 WSDL。

[VERSION] = 版本字串;比方說， `http://Microsoft.LobServices.OracleDB/2007/03`。  

[DB_SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。  

[DB_TABLE] = Oracle 資料表的名稱比方說，EMP。  

[DB_VIEW] = [Oracle] 檢視中，名稱比方說，SALES_VIEW。  

[DB_PROCEDURE] = Oracle 程序; 的名稱比方說，SP_GENREPORT。  

[DB_FUNCTION] = Oracle 函式; 的名稱比方說，FN_GETUSERID。  

[DB_PACKAGE] = Oracle package; 的名稱比方說，ACCOUNT_PKG。  

[PACK_PROCEDURE] = 封裝程序; 的名稱比方說，GET_ACCOUNT。  

[PACK_FUNCTION] = 封裝函式; 的名稱比方說，CREATE_ACCOUNT。  

## <a name="metadata-search-and-node-ids"></a>中繼資料搜尋和節點識別碼  
 中繼資料搜尋是功能強大[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]介面的一部分與其**MetadataRetrievalContract**介面。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來支援下列 Oracle 成品搜尋會使用這項功能。 中繼資料搜尋範圍僅限於在其中執行搜尋作業的節點下的層級。 例如，若要搜尋函式，您必須搜尋下\\[Schema] \Functions。 不支援遞迴搜尋。  

|成品|節點識別碼|傳回的節點類型|描述|  
|--------------|-------------|------------------------|-----------------|  
|[DB_SCHEMA]|/ （也就是根節點）|類別目錄|傳回符合搜尋運算式的所有結構描述節點。|  
|[DB_TABLE]|/ [VERSION] / [DB_SCHEMA] / 資料表|類別目錄|傳回資料表的所有節點中符合搜尋運算式指定結構描述。|  
|[DB_VIEW]|/ [VERSION] / [DB_SCHEMA] / 檢視|類別目錄|傳回檢視的所有節點中符合搜尋運算式指定結構描述。|  
|[DB_PROCEDURE]|/ [VERSION] / [DB_SCHEMA] / 程序|OPERATION|傳回在指定的結構描述符合搜尋運算式中的程序的所有節點。|  
|[DB_FUNCTION]|/ [VERSION] / [DB_SCHEMA] / [函式]|OPERATION|傳回在指定的結構描述符合搜尋運算式中的函式的所有節點。|  
|[DB_PACKAGE]|/ [VERSION] / [DB_SCHEMA] / 套件|類別目錄|在指定的結構描述符合搜尋運算式中傳回所有的套件節點 （類別）。|  
|[PACK_PROCEDURE] 和 [PACK_FUNCTION]|/ [VERSION] / [DB_SCHEMA] /Package/ [DB_PACKAGE]|OPERATION|指定套件符合搜尋運算式中傳回所有函式和程序的節點 （作業）。|  

 [VERSION] = 版本字串;比方說， `http://Microsoft.LobServices/2007/03`。  

 [DB_SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。  

 [DB_TABLE] = Oracle 資料表的名稱比方說，EMP。  

 [DB_VIEW] = [Oracle] 檢視中，名稱比方說，SALES_VIEW。  

 [DB_PROCEDURE] = Oracle 程序; 的名稱比方說，SP_GENREPORT。  

 [DB_FUNCTION] = Oracle 函式; 的名稱比方說，FN_GETUSERID。  

 [DB_PACKAGE] = Oracle package; 的名稱比方說，ACCOUNT_PKG。  

 [PACK_PROCEDURE] = 封裝程序; 的名稱比方說，GET_ACCOUNT。  

 [PACK_FUNCTION] = 封裝函式; 的名稱比方說，CREATE_ACCOUNT。  

 您可以指定任何有效的運算式，可用於 Oracle LIKE 運算子與相容的搜尋運算式。 例如，若要執行 結構描述中包含的資料表中的 搜尋[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會執行下列 SQL: `SELECT TABLE_NAME FROM ALL_TABLES WHERE OWNER = '[OWNER_NAME]' AND TABLE_NAME LIKE ‘[SEARCH_STR]’`。  

 下表列出特殊字元[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]搜尋運算式中支援。  

|特殊字元|解譯|  
|-----------------------|--------------------|  
|%（百分比）|比對零或多個字元;例如，"%"會比對"A"、"AB"，"ABC"，等等。|  
|_ (底線)|符合只有 1 個字元;例如，"A_"符合"AB"、"AC"、"AD"，依此類推。|  
|\ （逸出）|逸出的特殊意義的 '%' 和 '_';例如，"A\\_km"符合"A_B 」。|  

## <a name="metadata-retrieval-and-node-ids"></a>擷取中繼資料和節點識別碼  
 下表摘要說明所傳回的中繼資料特性[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  

|成品|中繼資料特性|  
|--------------|------------------------------|  
|[資料表或檢視表]|<ul><li>資料表名稱。</li><li>資料表的欄位名稱。</li><li>資料表欄位資料類型會對應到簡單或複雜的 WSDL 類型。</li><li>資料表的欄位長度會對應至 facet maxLength。</li><li>資料表欄位主要索引鍵條件約束會對應至 facet minOccurs = 1。</li><li>資料欄位的 NULL 條件約束會對應至 facet isNillable = true。</li><li>資料表作業<br /><br /> <ul><li>Insert</li><li>SELECT</li><li>UPDATE</li><li>Delete</li><li>READLOB （如果資料表包含 Oracle LOB 類型 欄位）</li><li>UPDATELOB （如果資料表包含 Oracle LOB 類型 欄位）</li></ul></li></ul>|  
|程序或函式|程序或函式名稱會對應至作業名稱。<br />程序或函式的參數名稱。<br />程序或函式的參數資料類型會對應至 WSDL 類型。<br />程序或函式的參數方向會對應至 WSDL 參數方向。<br />程序參數或函式參數的資料類型的長度會對應至 facet maxLength。<br />程序或函式的參數順序會對應至項目序列。<br />式函會傳回資料類型會對應至 WSDL 類型。<br />式函會傳回資料類型長度會對應至 facet maxLength。|  
|封裝程序或函式。|封裝名稱。<br />-其他程序和函式特性，如上所示。|  

 中繼資料的格式的詳細資訊，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開特定的成品和作業上 Oracle 資料庫時，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)。  

## <a name="see-also"></a>另請參閱  
[在 Visual Studio 中取得 Oracle DB 作業的中繼資料](get-metadata-for-oracle-database-operations-in-visual-studio.md)
