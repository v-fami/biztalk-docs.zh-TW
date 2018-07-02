---
title: 瀏覽、 搜尋及取得 SQL Server 中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 368dd5ca-456c-4cae-9e85-bcf504c4e7ed
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37308bf4f5a1d6bedba061337b2352f198354dd7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994151"
---
# <a name="browse-search-and-get-sql-server-metadata"></a>瀏覽、 搜尋及取得 SQL Server 中繼資料
中繼資料，[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]從 SQL Server 資料庫的介面描述與使用配接器的 SQL Server 資料庫通訊的訊息結構。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援兩個介面，來擷取中繼資料。  
  
- 所提供的 MetadataExchange [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。 WCF 提供的中繼資料交換端點的所有 WCF 繫結，可讓用戶端取得中繼資料從 SQL Server 資料庫。  
  
- 所提供的 IMetadataRetrievalContract [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，其支援的中繼資料瀏覽和搜尋功能的介面卡。  
  
  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]介面 SQL Server 資料庫成品和配接器用戶端可以叫用的個別作業。 配接器也會呈現可用於執行 SQL Server 資料庫上的特定作業的作業 （例如 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar）。 本主題稍後討論這些作業。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]呈現目前連接的使用者可以存取 SQL Server 資料庫中的所有結構描述中的成品。 這表示，除了預設結構描述 (dbo)，配接器用戶端也可以執行作業在成品上的 SQL Server 資料庫中的其他結構描述中，提供使用者認證用來連接使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]存取這些結構描述中的人員SQL Server 資料庫中。 如需 SQL Server 資料庫中的結構描述資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=130148 ](http://go.microsoft.com/fwlink/?LinkId=130148)。  
  
 您可以使用配接器用戶端來瀏覽、 搜尋及擷取中繼資料：  
  
- 在 Visual Studio 中建立的 BizTalk 專案  
  
- 使用 WCF 服務模型  
  
- 使用 WCF 通道模型  
  
  BizTalk 專案時，您必須使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生您想要在 SQL Server 資料庫上執行作業的中繼資料。 使用 WCF 服務模型時，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 proxy 類別上的 SQL Server 資料庫執行作業。 如需有關瀏覽、 搜尋和擷取中繼資料使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或是[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[取得 Visual Studio 中使用 SQL 配接器中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)。  
  
## <a name="browsing-metadata"></a>瀏覽中繼資料  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]讓配接器用戶端來瀏覽資料庫資料表、 檢視、 預存程序和 SQL Server 資料庫中所提供的函式。 中繼資料瀏覽作業的一部分，配接器也會呈現可以在 SQL Server 資料庫，包括一些自訂的配接器所支援的作業執行的作業。 這些作業都是從[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]呈現下列作業：  
  
- 資料表、 檢視、 程序、 純量函數和資料表值函式上的作業。 比方說，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可能介面 Insert、 Update、 Select，並刪除 [員工] 資料表的作業。  
  
- 集合\<資料行名稱\>資料表和檢視表可讓配接器用戶端在資料流處理方式寫入大型資料值的作業。 設定作業才會傳回這些資料表和檢視表包含下列資料類型的任何資料行： varchar （max）、 nvarchar （max） 或 varbinary （max）。 如需詳細資訊，請參閱 <<c0> [ 資料表和檢視表包含使用 SQL 配接器的大型資料類型的作業](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md)。  
  
- ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業，可讓配接器用戶端在 SQL Server 中執行任意的 SQL 陳述式。 如需有關這些作業的詳細資訊，請參閱 <<c0> [ 支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  
  
- 從 SQL Server 接收輸入的訊息 「 輪詢 」 和 「 通知作業。 輪詢作業的相關資訊，請參閱[支援的輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md); 如通知作業的相關資訊，請參閱[使用 SQL 接收查詢通知的考量配接器](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)。  
  
  如需有關如何分類中繼資料的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md)。  
  
## <a name="searching-metadata"></a>搜尋中繼資料  
 使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，就可以對 SQL Server 資料庫中的搜尋查詢，使用 LIKE 運算子與相容的 SQL Server 搜尋運算式。 例如，配接器用戶端可以使用搜尋運算式，例如"EMP %"以取得開頭為 EMP 資料表。 配接器會將此轉換成下列 SQL 查詢：  
  
```  
SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE 'EMP%'  
```  
  
 下表列出可用來搜尋和其解譯的特殊字元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|_ (底線)|比對一個字元。<br /><br /> 例如，"A_"符合"AB"、"AC"、"AD"。|  
|%（百分比）|比對零或多個字元。<br /><br /> 例如，"%"會比對"A"，"AB"，"ABC"。|  
|[ ]|-逸出 %_ 的特殊的意義。<br />-指定範圍或集合必須存在的字元。<br /><br /> 例如：<br /><br /> -%[%] %比對所有的名稱包含 %符號。<br />-[-f] 比對所有字元之間，以及包括 'a' 和 'f' 的名稱。<br />-[abc] 比對所有的名稱有字元 'a'、 'b' 和 'c'。|  
|[^]|指定的範圍或集合不會出現的字元。<br /><br /> 例如：<br /><br /> -[^ a-f] 比對所有沒有字元之間，以及包括 'a' 和 'f' 的名稱。<br />-[^ abc] 比對所有的名稱，並沒有字元 'a'、 'b' 和 'c'。|  
  
> [!IMPORTANT]
>  中繼資料搜尋範圍僅限於在其中執行搜尋作業的節點下的層級。 例如，若要搜尋的純量函式，您必須是下搜尋/純量函式 / [Schema]。 不支援多層級的搜尋。  
  
## <a name="retrieving-metadata"></a>擷取中繼資料  
 擷取中繼資料時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以擷取在結構描述，包括所有的中繼資料，或使用個別的物件和作業參數物件的資料庫的子集。 配接器會顯示 SQL Server 資料庫中的實體當做 XML 中的項目名稱。 因為底線是只允許可以包含特殊字元，使用底線編碼中的項目名稱的其他所有特殊字元。 例如，`emp$name`編碼為`emp_x0024_name`。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for SQL Server 概觀](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)   
 [了解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)   
 [取得在 Visual Studio 中使用 SQL 配接器的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)