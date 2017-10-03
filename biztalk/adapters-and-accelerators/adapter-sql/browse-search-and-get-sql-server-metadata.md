---
title: "瀏覽、 搜尋及取得 SQL Server 中繼資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 368dd5ca-456c-4cae-9e85-bcf504c4e7ed
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5abb42ff1cae700077c44c391a1112c7309048c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-sql-server-metadata"></a>瀏覽、 搜尋及取得 SQL Server 中繼資料
中繼資料，[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]從 SQL Server 資料庫的介面描述與使用配接器的 SQL Server 資料庫通訊的訊息結構。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援兩個介面來擷取中繼資料。  
  
-   所提供的中繼資料交換[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。 WCF 提供的中繼資料交換端點所有 WCF 繫結，讓用戶端都可以從 SQL Server 資料庫取得中繼資料。  
  
-   所提供的 IMetadataRetrievalContract [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，可支援瀏覽和搜尋功能的介面卡的中繼資料。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]介面 SQL Server 資料庫成品和配接器用戶端可以叫用的個別作業。 配接器也會提供諸如可以用來執行 SQL Server 資料庫上的特定作業的作業 （例如 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar）。 本主題稍後會討論這些作業。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]呈現目前連接的使用者可以存取 SQL Server 資料庫中的所有結構描述中的成品。 這表示，除了預設結構描述 (dbo)，配接器用戶端也可以執行作業在成品上的 SQL Server 資料庫中的其他結構描述中，提供使用者認證會用來連接使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以存取在那些結構描述SQL Server 資料庫。 如需 SQL Server 資料庫中的結構描述資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=130148](http://go.microsoft.com/fwlink/?LinkId=130148)。  
  
 您可以使用配接器用戶端來瀏覽、 搜尋和擷取的中繼資料：  
  
-   Visual Studio 中建立 BizTalk 專案  
  
-   使用 WCF 服務模型  
  
-   使用 WCF 通道模型  
  
 當使用 BizTalk 專案時，您必須使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生您想要在 SQL Server 資料庫上執行作業的中繼資料。 使用 WCF 服務模型時，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 proxy 類別來執行 SQL Server 資料庫上的作業。 如需有關瀏覽、 搜尋和擷取中繼資料使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[取得中繼資料使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)。  
  
## <a name="browsing-metadata"></a>瀏覽中繼資料  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]讓配接器用戶端來瀏覽資料庫資料表、 檢視、 預存程序和 SQL Server 資料庫中所提供的函式。 中繼資料瀏覽作業的一部分，配接器也會提供諸如可以在 SQL Server 資料庫，包括一些自訂的配接器所支援的作業執行的作業。 這些作業都是從[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]呈現下列作業：  
  
-   資料表、 檢視、 程序、 純量函數和資料表值函式上的作業。 例如，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可能介面 Insert、 Update、 Select，並刪除 EMPLOYEE 資料表的作業。  
  
-   集合\<資料行名稱 > 資料表和檢視表可讓大型資料值寫入資料流的方式在配接器用戶端的作業。 設定作業只會針對這些資料表和檢視表包含下列資料類型的任何資料行中傳回： varchar （max）、 nvarchar （max） 或 varbinary （max）。 如需詳細資訊，請參閱[資料表和檢視表包含使用 SQL 配接器的大型資料類型上的作業](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md)。  
  
-   ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業，讓 SQL Server 中執行任意的 SQL 陳述式的配接器用戶端。 如需有關這些作業的詳細資訊，請參閱[ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  
  
-   從 SQL Server 接收傳入的訊息在輪詢及通知作業。 輪詢作業的相關資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md); 如通知作業的相關資訊，請參閱[使用 SQL 接收查詢通知的考量配接器](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)。  
  
 如需中繼資料的分類方式的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md)。  
  
## <a name="searching-metadata"></a>搜尋中繼資料  
 與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，很可能在 SQL Server 資料庫上執行搜尋查詢，使用 LIKE 運算子與相容的 SQL Server 搜尋運算式。 例如，配接器用戶端可以使用搜尋的運算式，例如"EMP %"以取得開頭為 EMP 的資料表。 配接器會將此轉換下列 SQL 查詢：  
  
```  
SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE 'EMP%'  
```  
  
 下表列出可用於搜尋和由其解譯的特殊字元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|_ (底線)|比對一個字元。<br /><br /> 例如，"A_"符合"AB"、"AC"、"AD"。|  
|%（百分比）|比對零個或多個字元。<br /><br /> 例如，"%"符合"A"，"AB"，"ABC"。|  
|[ ]|-逸出 _ 和 %的特殊的意義。<br />-指定的範圍或集合必須存在的字元。<br /><br /> 例如：<br /><br /> -%[%] %符合所有名稱包含 %符號。<br />-[a-f] 會比對字元介於且包含 'a' 和 'f' 擁有的所有名稱。<br />-[abc] 會比對所有的名稱有字元 'a'、 'b' 和 'c'。|  
|[^]|指定的範圍或集合不會出現的字元。<br /><br /> 例如：<br /><br /> -[^ a-f] 會比對所有沒有字元介於且包含 'a' 和 'f' 的名稱。<br />-[^ abc] 會比對所有名稱沒有字元 'a'、 'b' 和 'c'。|  
  
> [!IMPORTANT]
>  在中繼資料的搜尋範圍僅限於正下方的節點，在其中執行搜尋作業層級。 例如，若要搜尋的純量函式，您必須是下搜尋/純量函式 / [Schema]。 不支援多層級的搜尋。  
  
## <a name="retrieving-metadata"></a>擷取中繼資料  
 擷取中繼資料時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以擷取下的結構描述，包括所有的中繼資料，或使用個別的物件和作業的參數物件的資料庫子集。 配接器會顯示從 SQL Server 資料庫的實體當做 XML 中的項目名稱。 因為底線是只允許可以包含特殊字元，是使用底線來編碼所有其他特殊字元的元素名稱。 例如，`emp$name`編碼為`emp_x0024_name`。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for SQL Server 的概觀](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)   
 [瞭解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)   
 [使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業取得中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)