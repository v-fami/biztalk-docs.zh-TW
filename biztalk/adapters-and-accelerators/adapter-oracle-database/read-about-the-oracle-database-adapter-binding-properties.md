---
title: "閱讀有關 Oracle 資料庫配接器繫結屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding properties
- binding properties, setting
- adapter, binding properties
ms.assetid: d626136e-c6c1-4352-94fc-3c034c423ef4
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2209d38099bcb440bbb836c7107b0cd106e1d596
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="read-about-the-oracle-database-adapter-binding-properties"></a>閱讀有關 Oracle 資料庫配接器繫結屬性資訊
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現數個繫結屬性。 藉由設定這些屬性，您可以控制某些配接器的行為。 本章節描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性。 它也會示範如何存取這些使用.NET 程式設計或上設定屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]實體連接埠繫結。  
  
## <a name="the-adapter-binding-properties"></a>配接器繫結屬性  
 下表顯示[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性依類別目錄分組。 類別目錄指的每個繫結屬性會出現提出以不同的應用程式設定配接器 （或） 繫結 對話方塊中的節點。  
  
|繫結屬性|類別目錄|Description|.NET 型別|  
|----------------------|--------------|-----------------|---------------|  
|**CloseTimeout**|一般|[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]連線關閉逾時。 預設值是 1 分鐘。 不支援。|System.TimeSpan|  
|**EnableBizTalkCompatibilityMode**|一般|設定這個屬性的值繫結至**True**搭配 BizTalk Server 使用配接器時。 否則，您必須設定這個屬性的值繫結至**False**。|bool (System.Boolean)|  
|**InboundOperationType**|一般|指定您是否要執行**輪詢**或**通知**輸入作業。 預設值是**輪詢**。<br /><br /> 如需有關**輪詢**看到[支援 Oracle 資料庫中接收輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md)。 如需有關**通知**，請參閱[接收資料庫變更通知使用 Oracle 資料庫配接器的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)。|列舉|  
|**名稱**|一般|傳回所產生的檔案名稱的唯讀值[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來保存[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端類別。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]表單的檔案名稱的值附加 「 用戶端 」**名稱**屬性。 傳回的值是"OracleDBBinding";針對此值，產生的檔案會命名為"OracleDBBindingClient"。|string|  
|**OpenTimeout**|一般|ODP.NET 屬性。 指定[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]連線開啟逾時。 預設值是 1 分鐘。 使用 ODP.NET 實作這個屬性。<br /><br /> **重要事項：** [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]一律會使用**OpenTimeout**時在開啟連線到 Oracle 資料庫設定連接的開啟逾時。 配接器會忽略任何逾時 (**System.TimeSpan**) 當您開啟通訊物件，例如通道傳遞的參數。|System.TimeSpan|  
|**ReceiveTimeout**|一般|指定[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]訊息接收逾時。 基本上，這表示配接器等候傳入訊息的時間的最大數量。 預設為 10 分鐘。<br /><br /> **重要事項：**輸入如輪詢作業，建議您設定在逾時的最大的可能值，也就是 24.20:31:23.6470000 （24 天）。 使用與配接器時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，將逾時設定為較大的值不會影響配接器的功能。|System.TimeSpan|  
|**SendTimeout**|一般|ODP.NET 屬性。 指定[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]訊息的傳送逾時。 預設值是 1 分鐘。 不支援。|System.TimeSpan|  
|**DataFetchSize**|BufferManagement|ODP.NET 屬性。 指定資料的量，以位元組為單位，從一個伺服器往返中的結果集提取 ODP.NET。 預設值為 65536。 這個屬性用於效能微調。|長時間 (System.Int64)|  
|**InsertBatchSize**|BufferManagement|指定多個記錄插入作業的批次大小。 預設為其中一個。 中的值**InsertBatchSize**大於一，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]批次處理成單一 ODP.NET 呼叫指定的記錄數目。 如果在插入作業的記錄數目不是批次大小的倍數，最後的批次會包含較少的記錄比批次大小值。 例如，如果 insert 訊息有 10 筆記錄和**InsertBatchSize**是設定為 1，配接器讀取個別記錄，並將它們寫入至 Oracle 資料庫。 因此，配接器執行的 Oracle 資料庫上的 10 個個別作業。 同樣地，如果 insert 訊息有 10 筆記錄和**InsertBatchSize**設定為 5，配接器會讀取和寫入的 5 筆記錄一次至 Oracle 資料庫中，因此執行只有 2 插入作業。<br /><br /> 如果記錄結構都不相同批次中**Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException**擲回例外狀況，且交易已回復整個插入作業。 精選值**InsertBatchSize**可大幅改善配接器的多個記錄插入作業的效能。|int (System.Int32)|  
|**LongDatatypeColumnSize**|BufferManagement|以位元組為單位 (32512) Oracle long 資料類型資料行指定大小上限。 預設值是 0。 如果您不執行 long 資料類型上的作業，您必須使用預設值。 若要預先擷取資料，您必須指定**-1**做為這個繫結屬性的值。 如果您是，您必須明確設定為適當的值，這個繫結屬性：<br /><br /> 執行包含 long 資料型別參數的預存程序。<br /><br /> 的執行包含 long 資料類型的資料行和 SELECT 陳述式的資料表上的選取作業不包含主索引鍵資料行。<br /><br /> **注意：**此繫結屬性已被取代。|長時間 (System.Int64)|  
|**MaxOutputAssociativeArrayElements**|BufferManagement|指定的執行在回應中傳回的關聯陣列的作業時，會建立配接器的關聯陣列的大小。 配接器通訊要 ODP.NET，接著會建立一個緩衝區的陣列大小而定之陣列的大小。 預設值為 32。<br /><br /> 執行涉及 PL/SQL 資料表類型的作業時，這個繫結屬性很有用。|int (System.Int32)|  
|**MetadataPooling**|BufferManagement|ODP.NET 屬性。 指定是否 ODP.NET 會快取執行查詢的中繼資料資訊。 預設值是**True**，可讓共用中繼資料。 快取這項資訊改善效能。不過，如果基礎 Oracle 成品的變更發生在 Oracle 系統時，此集區的中繼資料將會同步。這可能會導致傳回非預期的例外狀況的 Oracle 系統上執行的作業。 這個屬性用於效能微調。|bool (System.Boolean)|  
|**StatementCachePurge**|BufferManagement|ODP.NET 屬性。 指定當連接傳回連接集區時，是否會清除 ODP.NET 陳述式快取與連接相關聯。 預設值是**False**，這會停用陳述式快取清除。 這個屬性用於效能微調。|bool (System.Boolean)|  
|**StatementCacheSize**|BufferManagement|ODP.NET 屬性。 指定可以快取每個 ODP.NET 連接的陳述式的最大數目。 將此屬性設為非零值，可讓陳述式快取的連接。 預設值是 10。 這個屬性用於效能微調。|int (System.Int32)|  
|**EnablePerformanceCounters**|診斷|指定是否要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]效能計數器和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]LOB 延遲效能計數器。 預設值是**False**; 效能計數器已停用。 LOB 延遲效能計數器會測量所花費的時間總計[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在 Oracle 資料庫的呼叫。|bool (System.Boolean)|  
|**EnableSafeTyping**|中繼資料|啟用或停用安全的輸入。 預設值是**False**安全; 輸入已停用。 此功能可控制如何配接器會提供諸如某些 Oracle 資料型別。 如需安全輸入 」 的詳細資訊，請參閱[基本的 Oracle 資料 Types1](../../adapters-and-accelerators/adapter-oracle-database/basic-oracle-data-types1.md)。|bool (System.Boolean)|  
|**UseSchemaInNameSpace**|中繼資料|指定作業和其相關聯的類型的 xml 命名空間中是否包含結構描述名稱 （SCOTT、 HR，等等）。 預設值是**True**; 命名空間中包含的結構描述名稱。 優點不是包含命名空間中的配置名稱是，如果沒有具有相同名稱 (例如，EMP) 的資料表中兩個不同的結構描述，然後在相同的 XML 可以用來執行簡單 SQL 作業 (Insert、 Update、 Delete、 Select) 這兩個資料表。<br /><br /> 例如，如果**UseSchemaInNamespace**屬性為 true，SCOTT 這些作業的命名空間。EMP 資料表是 「 http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";如果為 false，命名空間會是"http://Microsoft.LobServices.OracleDB/2007/03/Table/EMP"。<br /><br /> **重要事項：**訊息動作不會受到**UseSchemaInNamesapce**繫結屬性中，永遠會包含結構描述名稱。<br /><br /> **重要事項：**我們強烈建議將此繫結屬性設定為**True**產生中繼資料時。 如果您設定這個屬性為 false 時，Oracle 結構描述名稱 (例如，SCOTT) 將無法使用產生的結構描述的 XML 命名空間中。 因此，如果有兩個資料表具有相同名稱在兩個不同的 Oracle 結構描述，而它們會加入至相同的 BizTalk 專案，將無法在 BizTalk 專案建置和部署。 如果您想要在相同的 BizTalk 專案中包含這類結構描述，您必須手動編輯它們的 XML 命名空間中包含 Oracle 結構描述名稱。|bool (System.Boolean)|  
|**NotificationPort**|通知|指定 ODP.NET 必須開啟從 Oracle 資料庫的資料庫變更通知所接聽的通訊埠編號。 預設值為-1，表示 ODP.NET 使用有效、 隨機、 未使用的連接埠號碼。<br /><br /> **重要事項：**配接器用戶端不會收到資料庫變更通知，如果 Windows 防火牆已開啟。 此外，關閉 Windows 防火牆，以接收通知並不建議。 因此，若要接收通知，而不會危害用戶端電腦的安全性，我們建議指定正整數值做為連接埠號碼，然後將該通訊埠編號加入至 Windows 防火牆例外清單。 如果您設定這個繫結屬性為預設值為-1，ODP.NET 使用隨機的連接埠，而配接器用戶端將不會知道要新增至 Windows 防火牆例外清單的通訊埠。 如需如何將連接埠新增至 Windows 防火牆例外清單的指示，請參閱[http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959)。<br /><br /> **注意：**接收通知使用的應用程式定義域中的多個應用程式是否[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]、 **NotificationPort**所有應用程式必須設定為相同的連接埠繫結屬性數字。 這是因為 ODP.NET 建立只有一個應用程式定義域中的一個通訊埠接聽的接聽程式。|int (System.Int32)|  
|**NotificationStatement**|通知|指定 SELECT 陳述式用於從 Oracle 資料庫取得通知登錄。 SELECT 陳述式無法與下列類似的範例。<br /><br /> `SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’`<br /><br /> **注意：**您必須指定資料庫物件名稱，以及結構描述名稱。 例如， `SCOTT.ACCOUNTACTIVITY`。<br /><br /> 指定 SELECT 陳述式變更的結果集時，才配接器從 Oracle 資料庫取得通知訊息。|string|  
|**NotifyOnListenerStart**|通知|指定給配接器用戶端，通知執行接收位置，接聽程式啟動時，配接器是否要傳送通知訊息。 預設值是**True**。|bool (System.Boolean)|  
|**ConnectionLifetime**|OracleConnectionPool|ODP.NET 屬性。 指定最大持續期限，以秒為單位的連線。 預設值是 0。 這個屬性用於效能微調。|int (System.Int32)|  
|**DecrPoolSize**|OracleConnectionPool|ODP.NET 屬性。 指定當大量建立連線不在使用中關閉的連接數目。 預設值是 1。 這用於進行效能微調。|int (System.Int32)|  
|**IncrPoolSize**|OracleConnectionPool|ODP.NET 屬性。 指定時，系統會要求新的連接，ODP.NET 連接集區中沒有可用的連接建立新的連接數目。 預設為 5。 這個屬性用於效能微調。|int (System.Int32)|  
|**Sqlserversink**|OracleConnectionPool|ODP.NET 屬性。 ODP.NET 連接集區中指定連線的數目上限。 預設值為 100。 這個屬性用於效能微調。<br /><br /> **重要事項：**必須設定**Sqlserversink**謹慎。 如果此值設定過大，就會可能耗盡 ODP.NET，從可用的連接數目。|int (System.Int32)|  
|**MinPoolSize**|OracleConnectionPool|ODP.NET 屬性。 指定 ODP.NET 連接集區中的最小連接數目。 預設值是 1。 這個屬性用於效能微調。|int (System.Int32)|  
|**UseOracleConnectionPool**|OracleConnectionPool|ODP.NET 屬性。 指定是否要使用 ODP.NET 連接集區。 預設值是**True**，可讓連接共用。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]實作連接共用使用 ODP.NET 連接集區。|bool (System.Boolean)|  
|**PolledDataAvailableStatement**|PollingReceive|指定 SELECT 陳述式執行，以判斷是否可用於針對特定資料表輪詢的任何資料。 指定的陳述式必須傳回的結果集資料列和資料行所組成。 結果集的第一個資料格中的值，指出配接器是否會執行指定的值**PollingStatement**繫結屬性。 如果結果的第一個資料格包含正數值時，配接器會執行輪詢陳述式。 例如，會是有效的陳述式，這個繫結屬性：<br /><br /> `Select * from <table_name>`<br /><br /> 這個繫結屬性的預設值設定為：<br /><br /> `SELECT 1 FROM DUAL`<br /><br /> 這表示配接器，必須繼續輪詢無論資料表輪詢是否有資料。<br /><br /> **注意：**您必須指定這個繫結屬性的預存程序。 此外，此陳述式不得修改基礎的 Oracle 資料庫。|string|  
|**PollingAction**|PollingReceive|指定輪詢作業的動作。 您可以判斷特定的作業，從您針對使用配接器服務增益集所使用的作業產生的中繼資料的輪詢動作。|string|  
|**PollingInterval**|PollingReceive|指定交易的輪詢間隔，也就是以秒為單位的間隔[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行輪詢陳述式針對 Oracle 資料庫。 預設值為 500。 配接器使用的輪詢間隔為下列：<br /><br /> 的後續輪詢時間間隔。 此間隔用來執行的輪詢和後輪詢查詢。 如果指定的間隔內執行這些查詢，配接器進入睡眠狀態的剩餘時間間隔中。<br /><br /> -輪詢交易逾時值。 這個值必須設定為夠大，無法包含輪詢陳述式執行階段、 後輪詢陳述式 （如果有指定） 執行時間，以及從認可交易的用戶端應用程式接收回覆的時間。<br /><br /> 如果用戶端應用程式傳送回覆的輪詢間隔到期之前，配接器認可的交易，並等待，直到執行下一次輪詢達到的輪詢間隔。<br /><br /> 如果用戶端應用程式會傳回錯誤，配接器就會終止交易。<br /><br /> 如果輪詢間隔到期，用戶端應用程式傳送回覆之前，異動會逾時。如需如何在輪詢案例中使用繫結屬性的詳細資訊，請參閱[支援 Oracle 資料庫中接收輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md)。|int (System.Int32)|  
|**PollingStatement**|PollingReceive|指定輪詢陳述式。 您可以指定簡單的 SELECT 陳述式或預存程序、 函數或封裝的程序或函式進行輪詢。<br /><br /> -如果您想要輪詢的資料表或檢視，您必須指定這個繫結屬性中的 SELECT 查詢。<br /><br /> -如果您想要輪詢使用預存程序、 函數或程序或函式，在封裝內，您必須指定這個繫結屬性中的個別作業的整個要求訊息。<br /><br /> 輪詢陳述式在所執行的陳述式時，才會執行**PolledDataAvailableStatement**內容繫結傳回一些資料。<br /><br /> **重要事項：** [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行輪詢陳述式和後輪詢陳述式 （如果有指定） 的 Oracle 交易內。 如果您正在使用中的 SELECT 陳述式**PollingStatement**繫結屬性，建議您在 SELECT 陳述式中指定 FOR UPDATE 子句。 這可確保在交易期間會予以鎖定選取的記錄和後輪詢陳述式可以執行任何必要的更新，在選取的記錄。<br /><br /> 如需如何在輪詢案例中使用繫結屬性的詳細資訊，包括使用 FOR UPDATE 子句中;請參閱[支援 Oracle 資料庫中接收輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md)。|string|  
|**PollWhileDataFound**|PollingReceive|指定是否[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]忽略的輪詢間隔，並持續輪詢 Oracle 資料庫，如果輪詢資料表中的可用資料。 如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。 預設值是**False**。<br /><br /> 假設的輪詢間隔設定為 60 秒，而 PolledDataAvailableStatement 針對指定的陳述式傳回的資料可進行輪詢。 配接器，然後執行 PollingInput 繫結屬性中指定的陳述式。 假設配接器會執行陳述式只 10 秒，將現在必須等到執行 PolledDataAvailableStatement 同樣地前, 50 秒，並接著執行輪詢陳述式。 相反地，以最佳化效能，您可以設定繫結屬性為 true，讓配接器可以開始執行下一個輪詢 PollWhileDataFound 週期一旦先前的輪詢週期結束。<br /><br /> **注意：**這個繫結屬性是適用於輪詢資料表和檢視表和輪詢使用預存程序、 函數或封裝的程序或函式。|string|  
|**PostPollStatement**|PollingReceive|指定執行後輪詢陳述式，以及之前 /POLLINGSTMT 訊息傳送給取用者的 PL/SQL 區塊。 預設值是**null**; 沒有後輪詢陳述式會執行。 後輪詢陳述式會在輪詢交易內執行。 後輪詢陳述式的兩個常見的用法如下：<br /><br /> -更新來表示它們已處理和後續輪詢查詢應該排除輪詢陳述式所傳回的資料列中的資料行。<br /><br /> 移動處理記錄，到不同的資料表。<br /><br /> **重要事項：**後輪詢陳述式指定，如果**PollingInterval**應該設定為夠大，PL/SQL 區塊的間隔時間過期之前完成。<br /><br /> 如需如何在輪詢案例中使用繫結屬性的詳細資訊，請參閱[支援 Oracle 資料庫中接收輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md)。|string|  
|**SkipNilNodes**|執行階段行為|指定是否[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]插入或更新要求 XML 中標示為 'nil' 節點的值將會略過。 這個繫結屬性是適用於插入或更新資料表中的記錄，而預存程序的記錄型別參數。 預設值是**True**，這表示配接器傳遞值的節點會標示為 'nil 的'，會略過。 在此情況下，Oracle （如果有指定） 中的預設值是考慮會標示為 'nil 的' 的節點。 如果設定為**False**，配接器將明確傳送至這些節點的 null 值。<br /><br /> **注意：**不存在於要求 XML 的節點，配接器永遠會略過傳遞值，不論值**SkipNilNodes**繫結屬性。對於 PL/SQL 資料表的記錄，配接器一律傳遞 null 值的節點會標示為 'nil 的' 或 XML，而不管值的要求中未出現**SkipNilNodes**繫結屬性。<br /><br /> 下列範例說明您設定此繫結屬性的值為基礎的介面卡組態中的差異。 假設要求 XML 類似下列：<br /><br /> `<EMPNO>1000</EMPNO> <ENAME>John</ENAME> <SAL nil=’true’></SAL>`<br /><br /> 如果**SkipNilNodes**設**True**，配接器會執行下列命令：<br /><br /> `INSERT INTO EMP (EMPNO, ENAME) VALUES (1000, “John”);`<br /><br /> 如果**SkipNilNodes**設**False**，配接器執行下列查詢：<br /><br /> `INSERT INTO EMP (EMPNO, ENAME, SAL) VALUES (1000, “John”, null);`<br /><br /> 請注意，在第二個陳述式中，配接器明確插入 null 值的參數"SAL"。|bool (System.Boolean)|  
|**UseAmbientTransaction**|交易|指定是否[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會執行作業使用呼叫端提供的異動內容。 預設值是**True**，這表示，配接器永遠會執行作業在交易內容中，假設用戶端提供的交易內容。 如果您有參與異動的其他資源，建立的連接會 System.Transaction 中登錄，並會提升為 MSDTC 交易。<br /><br /> 不過，可以是當您不希望配接器在交易內容中執行作業。 例如：<br /><br /> -當執行簡單的選取作業，在 Oracle 資料庫 （在傳送埠）。<br /><br /> 而指定輪詢陳述式可以執行選取的作業，並不會透過 DELETE 陳述式或叫用 （在接收埠） 的預存程序的資料表的任何變更。<br /><br /> 這兩種操作不要對資料庫資料表進行任何更新而因此，提高這些作業使用 MSDTC 交易可能產生的效能負擔。 在這種情況下，您可以設定的繫結屬性為 false，讓[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不在交易內容中執行的作業。<br /><br /> **注意：**不在交易內容中執行作業會建議您僅針對不會對資料庫進行變更的作業。 更新資料庫中的資料的作業，我們建議您將繫結屬性為 true，否則請可能根據您執行的輸入或輸出作業的訊息遺失或重複訊息。|bool (System.Boolean)|  
|**GeneratedUserTypesAssemblyFilePath**|UDT.NET 型別產生設計階段|指定配接器時，產生，產生中繼資料，其中包含所有可用的中繼資料中的 Udt 的 dll 路徑與名稱。 如果您正在產生封裝、 預存程序或使用 Udt 的函式的中繼資料，您必須指定 DLL 名稱。 指定 DLL 名稱是選擇性的資料表和檢視表具有 Udt。 產生的 DLL 會儲存到可執行檔相同的位置。<br /><br /> 這個繫結屬性是必要只在產生中繼資料。<br /><br /> **注意：**您必須指定一個檔案名稱。 為中繼資料中的 Udt，配接器會產生具有指定名稱的單一檔案。 如果您未指定名稱，配接器會產生 GUID 名稱與 DLL。 這個繫結屬性不可以使用 BizTalk Server 中設定時**Wcf-oracledb**接收或傳送埠。|string|  
|**GeneratedUserTypesAssemblyKeyFilePath**|UDT.NET 型別產生設計階段|指定的名稱和配接器用來建立強型別的組件金鑰檔案的路徑。<br /><br /> 這個繫結屬性是選擇性的並產生中繼資料時，只是必要。<br /><br /> **注意：**這個繫結屬性不可以使用 BizTalk Server 中設定時**Wcf-oracledb**接收或傳送埠。|string|  
|**UserAssembliesLoadPath**|UDT.NET 型別產生執行階段|指定的 Dll，並以分號分隔，會產生中繼資料時建立的配接器的名稱。 這些 Dll 會在您指定的位置儲存**GeneratedUserTypesAssemblyFilePath**產生中繼資料時，繫結屬性。 您必須手動將這些 Dll 複製到下列位置：<br /><br /> **對於 BizTalk 專案**： 複製 Dll 在與 BTSNTSvc.exe 相同的位置。 對於 BizTalk Server 中，這是通常在\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。<br /><br /> **.NET 專案**： 將 Dll 複製到您的.NET 專案資料夾內的 \bin\Development 資料夾。<br /><br /> 這個繫結屬性是必要只有時，才能傳送和接收訊息上的 Oracle 資料庫執行作業。|string|  
|**AcceptCredentialsInUri**|由不顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。|指定 Oracle 連線 URI 是否可以包含 Oracle 資料庫的使用者認證。 預設值是**False**，表示停用連線 URI 中的使用者認證。 如果**AcceptCredentialsInUri**是**False**和 Oracle 連接 URI 包含使用者認證[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]擲回例外狀況。 您可以設定**AcceptCredentialsInUri**至**True**如果您必須在 URI 中指定認證。 如需詳細資訊，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。|bool (System.Boolean)|  
  
## <a name="how-do-i-set-oracle-binding-properties"></a>如何設定繫結屬性的 Oracle？  
 當您指定連接到 Oracle 資料庫時，您可以設定 Oracle 繫結屬性。 如需如何設定繫結屬性的資訊時您：  
  
-   使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到 Oracle 資料庫，在 Visual Studio 中使用 取用配接器服務](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md)。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值是 null，則該繫結屬性將無法使用繫結檔案 （XML 檔案） 或 app.config 檔案中分別。 您必須手動加入的繫結屬性和其值在繫結檔案或 app.config 檔案中，視需要。  
  
-   設定傳送埠或接收埠 （位置） 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。  
  
-   使用程式設計方案中的 WCF 通道模型，請參閱[建立使用 Oracle 資料庫的通道](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)。  
  
-   使用 WCF 服務模型程式設計方案中，請參閱[設定 Oracle 資料庫繫結的用戶端](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md)。  
  
-   使用 WCF ServiceModel Metadata Utility Tool (svcutil.exe)，請參閱[Oracle 資料庫與 BizTalk 配接器使用 ServiceModel Metadata Utility Tool](../../adapters-and-accelerators/adapter-oracle-database/use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md)。  
  
## <a name="see-also"></a>請參閱  
 [BizTalk 應用程式部署的開發工作](../../core/development-tasks-for-biztalk-application-deployment.md)