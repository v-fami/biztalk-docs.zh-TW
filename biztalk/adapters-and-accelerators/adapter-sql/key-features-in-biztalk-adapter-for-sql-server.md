---
title: "SQL Server 的主要 BizTalk 配接器中的功能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6beab8d-c2c4-4add-860c-054b9aed8d70
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af3177e3004c81d368eab8738a201e90c95d1b69
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="key-features-in-biztalk-adapter-for-sql-server"></a>BizTalk Adapter for SQL Server 中的重要功能
此區段會列出中的功能[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]。  
  
> [!NOTE]
>  本主題已經使用舊版的[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]幫助。  
  
## <a name="features-in-the-sql-adapter"></a>SQL 配接器中的功能  
 以下是前一版中引進的功能[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
### <a name="technology-related-features"></a>技術相關功能  
  
|功能|註解|  
|-------------|-------------|  
|Windows Communication Foundation (WCF) 的使用|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]建置最上層的[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] ([!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)])。 接著，[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]建置於 WCF 之上。 配接器會公開為 WCF 配接器用戶端通道。 這可讓連線、 中繼資料交換和商務資料交換與外部系統。|  
|WCF 通道模型和 WCF 服務模型的支援|在 WCF 通道模型中，配接器用戶端可以取用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]透過直接傳送和接收 XML 訊息。 在 WCF 服務模型中，配接器用戶端可以產生.NET proxy 類別，從 Web 服務描述語言 (WSDL) 使用來取得[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。|  
|64 位元平台支援。|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]現在是適用於 64 位元平台。|  
  
### <a name="metadata-related-features"></a>中繼資料相關功能  
  
|功能|註解|  
|-------------|-------------|  
|瀏覽、 搜尋及擷取中繼資料|配接器用戶端可以瀏覽和搜尋批次中的中繼資料，藉由指定批次大小。 程式設計到配接器，而非透過取用配接器服務 BizTalk 專案增益集時，才使用這項功能。 中繼資料搜尋支援資料表、 檢視、 程序、 純量函數和資料表值函式層級。 搜尋字串使用直接 SQL 陳述式。|  
|叫用不同的資料庫中相同名稱的成品支援|在[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，包含僅限結構描述名稱，以及在某些情況下，物件名稱的 XML 結構描述定義 (XSD) 檔案中的命名空間。 不過，如果應用程式想要在不同資料庫中執行具有不同的中繼資料的相同具名成品上的作業，就會發生衝突的產生的中繼資料。 區別中繼資料的唯一方式是使用 XSD 命名空間中的資料庫名稱。<br /><br /> 目前版本的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓您指定 XSD 命名空間中的資料庫名稱的值設定**UseDatabaseNameInXsdNamespace**繫結屬性為 TRUE。 繫結屬性的預設值為 false，這表示 XSD 命名空間將不會包含資料庫名稱。 如需有關**UseDatabaseNameInXsdNamespace**繫結屬性，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。|  
  
### <a name="performance-related-features"></a>效能相關的功能  
  
|功能|註解|  
|-------------|-------------|  
|對效能計數器支援|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以供配接器用戶端支援以 WCF 為基礎的效能計數器。 如需有關效能計數器的詳細資訊，請參閱[使用 SQL 配接器的效能計數器](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md)。|  
  
### <a name="operations-related-features"></a>與作業相關的功能  
  
|功能|註解|  
|-------------|-------------|  
|SQL Server 2005 和 SQL Server 2008 的資料類型的支援|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援下列中導入的資料類型：<br /><br /> -   **SQL Server 2005**: XML、 varchar （max） 和 varbinary （max）。<br />-   **SQL Server 2008**： 日期、 時間、 Datetimeoffset、 Datetime2、 Hierarchyid、 Geography、 Geometry、 和 FILESTREAM。|  
|使用者定義型別 (Udt) 的支援|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援資料表和檢視表包含 Udt 上執行的作業。 如需 Udt 的支援資訊，請參閱[資料表和檢視表使用 SQL 配接器的使用者定義類型的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)。|  
|支援執行 TRANSACT-SQL 和 CLR 預存程序和函數|配接器用戶端可以執行 TRANSACT-SQL 和 CLR:<br /><br /> -SQL Server 資料庫中的預存程序。<br />純量和資料表值函式在 SQL Server 資料庫中。<br /><br /> 如需詳細資訊，請參閱[哪些作業可以執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)。|  
|執行預存程序使用或 FOR XML 子句不支援|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓您執行已包含或不 FOR XML 子句的 SELECT 陳述式的預存程序。 舊版配接器的支援只有這些預存程序具有 FOR XML 子句，SELECT 陳述式中。 執行預存程序的相關資訊，請參閱[使用 SQL 配接器的 SQL Server 中執行預存程序](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-the-sql-adapter.md)。|  
|支援的大型物件資料流|配接器用戶端可以進行串流處理大型字元和二進位欄位，使用 設定 SQL Server 資料庫中的\<資料行名稱\>作業，其中 < column_name > 是類型 varchar （max）、 nvarchar （max） 或 varbinary （max） 資料行名稱. 集合\<資料行名稱\>作業也可讓您插入或更新 SQL Server 2008 資料庫中的 FILESTREAM 資料。 如需詳細資訊，請參閱[資料表和檢視表，包含大型資料類型使用 SQL 配接器作業](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md)。 **注意：**讀取字元和二進位欄位，在 SQL Server 資料表和檢視中的，配接器用戶端使用選取的作業。|  
|支援查詢通知|配接器用戶端可以從觸發的 SELECT 陳述式或預存程序為基礎的 SQL Server 接收查詢通知。 做為在配接器用戶端和結果集的 SELECT 陳述式或預存程序變更時，通知會傳送 SQL server。 如需查詢通知的詳細資訊，請參閱[使用 BizTalk Server 接收查詢通知](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)。|  
|執行任意的 SQL 陳述式的支援|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]讓配接器用戶端可以執行任意使用 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的 SQL 陳述式。 如需有關這些作業的詳細資訊，請參閱[ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。|  
|複合作業的支援|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端執行複合操作上的 SQL Server 資料庫。 複合作業可以包含任意數目的下列作業，並以任何順序：<br /><br /> 的資料表和檢視表 Insert、 Update 和 Delete 作業。<br />-預存程序便會顯示為配接器中的作業。<br /><br /> 如需複合操作的詳細資訊，請參閱[複合操作的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)。|  
|增強的輪詢|[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]現在支援兩種其他輪詢： **TypedPolling**和**XmlPolling**。 如需這些輪詢的類型資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。|  
|執行多個結構描述中的成品上的作業的支援|除了預設結構描述 (dbo)，配接器用戶端也可以執行作業在成品上的 SQL Server 資料庫中的其他結構描述中，提供使用者認證會用來連接使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以存取這些結構描述中的 SQL Server資料庫。 如需 SQL Server 資料庫中的結構描述資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=130148](http://go.microsoft.com/fwlink/?LinkId=130148)。|  
  
## <a name="see-also"></a>請參閱  
 [BizTalk Adapter for SQL Server 概觀](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)