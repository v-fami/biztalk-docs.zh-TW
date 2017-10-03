---
title: "了解 BizTalk Adapter for SQL Server 配接器繫結屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4606f583-da74-4a26-95cb-88915ecafe37
caps.latest.revision: "43"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3d10bd82fa17501920150c6324695ae1cc9834b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties"></a>了解 BizTalk Adapter for SQL Server 配接器繫結屬性
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]呈現數個繫結屬性。 藉由設定這些屬性，您可以控制某些配接器的行為。 本章節描述所公開的繫結屬性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 它也會示範如何存取這些使用.NET 程式設計或上設定屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]實體連接埠繫結。  
  
## <a name="the-adapter-binding-properties"></a>配接器繫結屬性  
 下表顯示[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結屬性依類別目錄分組。 類別目錄指的每個繫結屬性會出現提出以不同的應用程式設定配接器 （或） 繫結 對話方塊中的節點。  
  
|繫結屬性|類別目錄|Description|.NET 型別|  
|----------------------|--------------|-----------------|---------------|  
|**XmlStoredProcedureRootNodeName**|（適用於 XML)|指定 SELECT 陳述式中有 FOR XML 子句的預存程序的回應結構描述的根節點名稱。 此根節點會封裝在執行這類預存程序之後收到來自 SQL Server 的 XML 回應。 您必須將此根節點加入回應結構描述，本主題中所述[執行預存程序在使用 BizTalk Server 的 SQL Server 中具有 FOR XML 子句](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)。<br /><br /> **重要事項：**您必須執行預存程序搭配 FOR XML 子句時設定這個繫結屬性。|string|  
|**XmlStoredProcedureRootNodeNamespace**|（適用於 XML)|指定 SELECT 陳述式中有 FOR XML 子句的預存程序的回應結構描述的根節點的目標命名空間。|string|  
|**CloseTimeout**|(一般)|[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]連線關閉逾時。 預設值是 1 分鐘。|System.TimeSpan|  
|**名稱**|(一般)|傳回所產生的檔案名稱的唯讀值[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來保存[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端類別。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]表單的檔案名稱的值附加 「 用戶端 」**名稱**屬性。 這個屬性的預設值是"SqlAdapterBinding";針對此值，產生的檔案會命名為"SqlAdapterBindingClient"。|string|  
|**OpenTimeout**|(一般)|指定[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]連線開啟逾時。 預設值是 1 分鐘。<br /><br /> **重要事項：** [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]一律會使用**OpenTimeout**時在開啟連線到 SQL Server，設定連接的開啟逾時。 配接器會忽略任何逾時 (**System.TimeSpan**) 參數傳遞，當您開啟通訊物件。 例如，配接器會忽略任何傳遞開啟通道時的逾時參數。|System.TimeSpan|  
|**ReceiveTimeout**|(一般)|指定[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]訊息接收逾時。 基本上，這表示配接器等候傳入訊息的時間的最大數量。 預設為 10 分鐘。<br /><br /> **重要事項：**輸入如輪詢作業，建議您設定在逾時的最大的可能值，也就是 24.20:31:23.6470000 （24 天）。 使用與配接器時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，將逾時設定為較大的值不會影響配接器的功能。|System.TimeSpan|  
|**SendTimeout**|(一般)|指定[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]訊息的傳送逾時。 預設值是 1 分鐘。|System.TimeSpan|  
|**EnableBizTalkCompatibilityMode**|BizTalk|指出配接器與搭配使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]或.NET 應用程式。<br /><br /> -當使用配接器從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]（或產生 BizTalk 專案中使用配接器的 SQL Server 上的作業的中繼資料），您都必須設定屬性**True**。 如此可確保 System.Data.DataSet 相容的格式為產生的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，否則您的 BizTalk 專案將無法編譯。<br /><br /> -當使用配接器從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]在.NET 應用程式中，您必須將屬性設**False**如果您想要使用回應做為資料集。 這可確保 System.Data.DataSet 產生結構描述是在與 WCF DataContractSerializer 相容的格式。|bool (System.Boolean)|  
|**BatchSize**|緩衝|SQL Server 資料庫中指定多個記錄插入、 更新和刪除作業對資料表或檢視表的批次大小。 預設值是 20。 中的值**BatchSize**大於一，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]批次處理到單一呼叫中指定的記錄數目。 較高的值可能會改善效能，但會影響記憶體耗用量。|int (System.Int32)|  
|**ChunkSize**|緩衝|指定用來設定 < column_name > 作業的緩衝區大小。 預設值為 4194304 個位元組。 較高的值可能會改善效能，但會影響記憶體耗用量。<br /><br /> **注意：**如需有關設定 < column_name > 作業的詳細資訊，請參閱[資料表和檢視表，包含大型資料類型使用 SQL 配接器作業](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md)。|int (System.Int32)|  
|**加密**|連接|指定 SQL Server (安裝有效的憑證） 是否會使用 SSL 加密，針對 SQL Server 和用戶端之間的所有資料傳輸。 預設值是**false**。|bool (System.Boolean)|  
|**MaxConnectionPoolSize**|連接|指定連接集區中，針對特定的連接字串允許的連線的數目上限。 預設值為 100。 這個屬性用於效能微調。<br /><br /> **重要事項：**必須設定**MaxConnectionPoolSize**謹慎。 如果此值設定過大，就會耗盡可用，連接數目的可能。|int (System.Int32)|  
|**WorkstationId**|連接|指定工作站 （用戶端電腦） 連線到 SQL Server 資料庫使用的唯一識別碼[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 這個繫結屬性值，如果指定，會用於**工作站 ID** SqlConnection.ConnectionString 屬性的關鍵字。 如需詳細資訊，請參閱[SqlConnection.ConnectionString 屬性](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx)。|string|  
|**EnablePerformanceCounters**|診斷|指定是否要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]效能計數器和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]LOB 延遲效能計數器。 預設值是**False**; 效能計數器已停用。 LOB 延遲效能計數器會測量所花費的時間總計[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在 SQL Server 資料庫的呼叫。<br /><br /> 如需有關效能計數器[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[使用 SQL 配接器的效能計數器](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md)。|int (System.Int32)|  
|**InboundOperationType**|輸入|指定您是否要執行**輪詢**， **TypedPolling**， **XmlPolling**，或**通知**輸入作業。 預設值是**輪詢**。<br /><br /> 如需有關**輪詢**， **TypedPolling**，和**XmlPolling**看到[支援輪詢](https://msdn.microsoft.com/library/dd788416.aspx)。 如需有關**通知**，請參閱[考量接收查詢通知使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)。|列舉|  
|**UseDatabaseNameInXsdNamespace**|中繼資料|指定是否針對特定成品產生 XSD 包含資料庫名稱。 將此設**True**来包含資料庫名稱。 否則，將此設**False**。 預設值是**False**。<br /><br /> 這是在單一應用程式要在不同資料庫中執行具有不同的中繼資料的相同具名成品上作業的情況下很有用。 如果不沒有命名空間中的任何資料庫名稱，產生的中繼資料就會發生衝突。 您藉由設定這個繫結屬性可以包含資料庫名稱在命名空間，使它們唯一。 以下是命名空間中的變更反白顯示的範例。<br /><br /> **UseDatabaseNameInXsdNamespace = False**<br /><br /> `http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee`<br /><br /> **UseDatabaseNameInXsdNamespace = True**<br /><br /> `http://schemas.microsoft.com/Sql/2008/05/TableOp/MyDatabase/dbo/Employee`<br /><br /> 請注意資料庫名稱包含命名空間中，當繫結屬性設定為**True**。|列舉|  
|**AllowIdentityInsert**|其他|指定配接器是否可以在 Insert 和 Update 作業期間插入識別欄位的值。 將此屬性設定為**True**插入或更新識別欄位的值。 否則會將此設**False**。 預設值是**False**。<br /><br /> **注意：**將此屬性設定為**True**會轉譯為配接器使用 「`SET IDENTITY_INSERT <table_name> ON`"。 如需詳細資訊，請參閱[SET IDENTITY_INSERT (TRANSACT-SQL)](https://msdn.microsoft.com/library/ms188059.aspx)。 <br /><br /> 在使用這個繫結屬性時，您必須考慮下列各點：<br /><br /> -配接器不會驗證您要將識別欄位的值。 比方說，如果資料表含有識別欄位到 100 之間的 「 身分識別種子 」 設定 「 識別值增量 」 設定為 1，且配接器用戶端會傳遞的值，假設 95，識別欄位，配接器直接傳以此值到 SQL Server。<br /><br /> -即使您將**AllowIdentityInsert**至**True**，不是必要的配接器用戶端在要求訊息中指定身分識別資料行的值。 如果值為識別資料行存在，則配接器會將它傳遞到 SQL Server。 如果值不存在，SQL Server 會插入識別欄位的規格為基礎的值。|bool (System.Boolean)|  
|**NotificationStatement**|通知 （適用輸入）|指定的 SQL 陳述式 (SELECT 或 EXEC\<預存程序 >) 用於 SQL Server 通知登錄。 請注意，您必須明確指定資料行名稱的陳述式中這個 SELECT 陳述式中所示。<br /><br /> `SELECT Employee_ID,Designation FROM dbo.Employee WHERE Status=0`<br /><br /> **注意：**您必須指定資料庫物件名稱，以及結構描述名稱。 例如， `dbo.Employee`。<br /><br /> 在結果集為指定的 SQL 陳述式變更時，才配接器從 SQL Server 取得通知訊息。|string|  
|**NotifyOnListenerStart**|通知 （適用輸入）|指定給配接器用戶端，通知執行接收位置，接聽程式啟動時，配接器是否要傳送通知訊息。 預設值是**True**。<br /><br /> 您收到的通知訊息看起來如下：<br /><br /> `<?xml version="1.0" encoding="utf-8" ?> <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">   <Info>ListenerStarted</Info>    <Source>SqlBinding</Source>    <Type>Startup</Type>  </Notification>`|bool (System.Boolean)|  
|**PolledDataAvailableStatement**|輪詢 （輸入）|指定 SQL 陳述式執行，以判斷是否可用於輪詢 SQL Server 資料庫中特定資料表的任何資料。 指定的陳述式必須傳回的結果集資料列和資料行所組成。 結果集的第一個資料格中的值會指出是否執行 SQL 陳述式指定的配接器**PollingStatement**繫結屬性。 如果結果的第一個資料格包含正數值時，配接器執行輪詢陳述式。 以下是一些您可以指定這個繫結屬性的有效陳述式的範例：<br /><br /> -如果您要指定 SELECT 陳述式：<br /><br /> `SELECT COUNT(*) from <table_name>`<br /><br /> -如果您指定預存程序時，您的預存程序可能會定義為：<br /><br /> `CREATE PROCEDURE <procedure_name>  AS BEGIN      SELECT COUNT(*) FROM <table_name> END GO`<br /><br /> 或<br /><br /> `CREATE PROCEDURE <procedure_name>  AS BEGIN      DECLARE @count int      SELECT @count = SELECT(*) FROM <table_name>      SELECT @count END GO`<br /><br /> 如果您使用預存程序，您會指定**PolledDataAvailableStatement**為`EXEC <procedure_name>`。<br /><br /> **重要事項：**陳述式指定這個繫結屬性不會執行內的*配接器起始*交易，並可能會多次呼叫執行實際的輪詢陳述式之前 （即使執行陳述式表示有可用的資料列進行輪詢）。|string|  
|**PollingIntervalInSeconds**|輪詢 （輸入）|指定間隔，以秒為單位，此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。 預設值是 30 秒。 輪詢間隔會決定後續輪詢間隔時間。 如果指定的間隔內執行的陳述式，則配接器處於非使用中的剩餘時間間隔。|int (System.Int32)|  
|**PollingStatement**|輪詢 （輸入）|指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。 您可以指定簡單的 SELECT 陳述式或預存程序，輪詢陳述式。 預設值是 **null**。 您必須指定的值**PollingStatement**來啟用輪詢。 輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。<br /><br /> 您可以指定任意數目的 SQL 陳述式以分號隔開。 您可以使用輪詢陳述式來讀取或更新 SQL Server 資料庫資料表中的資料。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行輪詢陳述式內部的一筆交易。 當配接器用於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，相同的交易用來提交到 BizTalk messagebox 的訊息從 SQL Server。|string|  
|**PollWhileDataFound**|輪詢 （輸入）|指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並為指定的 SQL 陳述式會持續執行**PolledDataAvailableStatement**如果輪詢資料表中的資料可繫結屬性。 如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。 預設值是**false**。<br /><br /> 假設的輪詢間隔設定為 60 秒，而針對指定的陳述式**PolledDataAvailableStatement**傳回資料可進行輪詢。 配接器，然後執行陳述式指定**PollingStatement**繫結屬性。 假設配接器需要 10 秒只執行輪詢陳述式，它現在就必須等候 50 秒，然後再執行**PolledDataAvailableStatement**一次，並接著執行輪詢陳述式. 相反地，若要最佳化的效能，您可以設定**PollWhileDataFound**內容繫結至**true**如此配接器可開始執行下次輪詢循環盡在先前的輪詢循環結束。|bool (System.Boolean)|  
|**UseAmbientTransaction**|Transaction|指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用執行作業的呼叫端提供的交易內容。 預設值是**true**，這表示配接器永遠交易內容中執行的作業。 如果參與的交易，其他資源，而且 SQL Server 也會聯結交易，交易取得提高 MSDTC 交易。<br /><br /> 不過，可以是當您不希望配接器在交易內容中執行作業。 例如：<br /><br /> -時執行簡單的選取作業，在 SQL Server 資料庫<br /><br /> -指定的同時輪詢陳述式，以執行選取的作業，並不包含任何資料表的變更來透過 Delete 陳述式或叫用預存程序。<br /><br /> 這些作業不進行任何更新至資料庫資料表和，因此，提升使用 MSDTC 交易的這些作業可以產生的效能負擔。 在這種情況下，您可以設定的繫結屬性為**false**以便[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不會在 交易內容中執行的作業。<br /><br /> **注意：**不在交易內容中執行作業會建議您僅針對不會對資料庫進行變更的作業。 更新資料庫中的資料的作業，我們建議繫結屬性設定為**true**; 否則為是，您可能會遇到訊息遺失或重複的訊息，視您執行的輸入或輸出作業。|bool (System.Boolean)|  
  
## <a name="how-do-i-set-sql-server-binding-properties"></a>如何設定繫結屬性的 SQL Server？  
 當您指定 SQL Server 的連接時，您可以設定 SQL Server 繫結屬性。 如需如何設定繫結屬性的資訊時您：  
  
-   使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到 SQL Server 使用 Windows 驗證與 SQL 配接器](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值是 null，則該繫結屬性將無法使用繫結檔案 （XML 檔案） 或 app.config 檔案中分別。 您必須手動加入的繫結屬性和其值在繫結檔案或 app.config 檔案中，視需要。  
  
-   設定傳送埠或接收埠 （位置） 中的 BizTalk Server 解決方案，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。
  
-   使用程式設計方案中的 WCF 通道模型，請參閱[建立使用 SQL 配接器的通道](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md)。  
  
-   使用 WCF 服務模型程式設計方案中，請參閱[設定 SQL 配接器的 用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)