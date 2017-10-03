---
title: "支援 Oracle 資料庫中接收輪詢基礎資料變更的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- notifications, polling-based
- post-polling
- POLLINGSTMT
- polling interval
- polling
ms.assetid: 9ff29d3f-ebb1-4d82-9106-150f939cbd9e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d8a29901672ba11f3ac48220f7096b2c355fc2e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-receiving-polling-based-data-changed-messages-in-oracle-database"></a>支援 Oracle 資料庫中接收輪詢基礎資料變更的訊息
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓用戶端程式來告知他們對 Oracle 資料庫中儲存資料的 Oracle 資料庫接收訊息。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接收 「 輪詢基礎 」 的訊息，其中指定選取的查詢、 預存程序、 函數或程序或函式，在封裝中，而執行配接器支援擷取資料，並提供在一般用戶端的結果時間間隔。 若要啟用此功能，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 POLLINGSTMT 作業。 此外，所有預存程序、 函數和程序和封裝內的函式會公開做為輸入的作業來輪詢。  
  
 配接器會提供兩種輪詢 Oracle 資料庫：  
  
-   **使用 SELECT 陳述式**。 您可以指定要輪詢的資料表和檢視 Oracle 資料庫中的簡單 SELECT 陳述式。 配接器執行 SELECT 陳述式，以指定的間隔，並將結果傳回至配接器用戶端。  
  
-   **使用預存程序、 函數或程序或函式，在封裝內**。 您可以指定預存程序、 函數或程序或函式，以輪詢 Oracle 資料庫在封裝內。 配接器指定的間隔執行的要求訊息，並將結果傳回至配接器用戶端。  
  
## <a name="polling-operation-workflow"></a>輪詢作業的工作流程  
 使用一般輪詢作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]牽涉到下列：  
  
1.  配接器用戶端必須指定**輪詢**為中的輸入作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值是**輪詢**。  
  
2.  配接器用戶端必須指定 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性來判斷是否有資料可用來輪詢。 執行這個陳述式時，傳回的結果集的第一個資料列的第一個資料行包含正整數值，如果有可用日期進行輪詢。 根據預設，此繫結屬性的值設定為`Select 1 FROM DUAL`，這表示配接器，必須繼續輪詢無論資料表輪詢是否有資料。  
  
3.  配接器用戶端必須指定輪詢間隔**PollingInterval**內容繫結至定義陳述式中指定的秒數間隔**PolledDataAvailableStatement**執行繫結屬性。 在每個輪詢間隔結束時，輪詢的資料可用陳述式會執行，而且會傳回結果集。  
  
4.  配接器用戶端必須指定 SELECT 陳述式或預存程序**PollingStatement**繫結屬性。  
  
    -   如果您想要輪詢的資料表或檢視，您必須指定這個繫結屬性中的 SELECT 查詢。  
  
    -   如果您想要輪詢使用預存程序、 函數或程序或函式，在封裝內，您必須指定這個繫結屬性中的個別作業的整個要求訊息。  
  
     中的陳述式**PollingStatement**繫結屬性不會執行沒有資料可用於輪詢，取決於**PolledDataAvailableStatement**步驟 1 中的繫結屬性。  
  
5.  配接器用戶端必須指定動作中的輪詢作業**PollingAction**繫結屬性。 針對特定作業的輪詢動作會從使用配接器服務增益集所使用的作業產生的中繼資料來決定。  
  
    > [!NOTE]
    >  如果您正在輪詢資料表或檢視使用中的 SELECT 陳述式**PollingStatement**繫結屬性，您不需要指定任何值作為**PollingAction**繫結屬性。 預設值，Null，會在此情況下傳遞。  
  
6.  配接器用戶端可以使用**PollWhileDataFound**內容繫結至忽略的輪詢間隔，並持續輪詢資料，以及可用時。  
  
    > [!IMPORTANT]
    >  如果您設定的值**PollWhileDataFound**繫結屬性設定為 True，配接器用戶端持續輪詢資料從 Oracle 和程序中開啟和關閉連接到 Oracle 資料庫在迴圈中。 因為 ODP.NET 開啟連線的速度大於關閉的連線，連線一段時間後可能會耗盡，並擲回例外狀況。 為因應措施，請確定值**UseOracleConnectionPool**設為 True，和適當的值中有提及**IncrPoolSize**內容繫結至控制連接數目您可以開啟配接器用戶端。  
  
7.  配接器用戶端可以指定後輪詢陳述式，Oracle 的 PL/SQL 區塊，如**PostPollStatement**繫結屬性。 這個繫結屬性中指定陳述式中指定的陳述式之後**PollingStatement**執行繫結屬性。  
  
 配接器會輪詢陳述式和後輪詢陳述式包裝在交易中與交易逾時值設定為指定的值為**PollingInterval**繫結屬性。 因此，務必指定大於或等於處理內送訊息並傳送回覆所需的時間的逾時值。 如果用戶端程式使用的訊息或執行後輪詢查詢所花費的時間超過逾時的值，會回復交易。 如果所花費的時間的逾時值，配接器就會認可交易，並 「 睡眠 」 投票，然後再執行下一次輪詢的剩餘時間。  
  
 配接器會抑制來自 Oracle 資料庫的任何空白輪詢回應。  
  
## <a name="differences-between-polling-and-notification"></a>通知輪詢之間的差異  
 雖然輪詢通知都是這兩個輸入的作業，且配接器用戶端通知有關 Oracle 資料庫中的資料變更下, 表將說明兩者之間的一些差異。 下列差異，可協助您決定在針對作業，視您的需求而定：  
  
|輪詢|通知|  
|-------------|------------------|  
|支援的所有 Oracle 資料庫版本都支援輪詢[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|通知是支援僅針對 Oracle 資料庫版本 10.2 和更新版本。|  
|您可以設定輪詢間隔，以檢查適用於定期輪詢資料，或立即一樣，當有可用的資料。 **提示：**輪詢可讓您更佳的輸送量持續發生資料變更並不想為每項變更，並發生時加以通知。 相反地，您可以指定您要在其後發生是因為最後一個變更通知的所有變更的通知輪詢間隔。|資料變更通知是一律在瞬間完成。|  
|輪詢配接器所起始。 若要驗證是否資料適用於輪詢，並以起始輪詢執行輪詢陳述式，如果某些資料可用於輪詢 SQL 陳述式執行配接器。|通知是由 Oracle 資料庫啟動。 只在配接器發出的通知陳述式會指示資料庫在陳述式的結果集變更的情況下起始通知。 通知是 Oracle 資料庫的功能。|  
|您可以使用輪詢陳述式來讀取或更新的 Oracle 資料庫中的資料。|您可以使用通知陳述式只讀取 Oracle 資料庫中的資料。|  
|輪詢會通知您有關已變更的實際資料。|通知會告知中插入，例如資料的變更類型的相關更新和刪除。|  
  
 如需詳細資訊：  
  
-   如何配接器支援從 Oracle 資料庫接收以輪詢為基礎的訊息，請參閱[收到輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。  
  
-   接收從 Oracle 資料庫使用的輪詢訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[叫用函數及使用 Biztalk Server 的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md)。  
  
-   從 Oracle 資料庫使用 WCF 服務模型收到輪詢訊息時，請參閱[收到輪詢資料變更訊息從 SQL Server 使用的 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)。  
  
-   從 Oracle 資料庫使用 WCF 通道模型收到輪詢訊息時，請參閱[收到輪詢資料變更訊息從 SQL Server 使用的 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)。  
  
-   訊息結構和執行在有輪詢查詢的 SOAP 動作，請參閱[輪詢作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)