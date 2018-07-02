---
title: Oracle 資料庫中接收以輪詢為基礎的資料變更訊息的支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- notifications, polling-based
- post-polling
- POLLINGSTMT
- polling interval
- polling
ms.assetid: 9ff29d3f-ebb1-4d82-9106-150f939cbd9e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6c834afac28c441ad058bd7843a2f9e8ebfe678
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972335"
---
# <a name="support-for-receiving-polling-based-data-changed-messages-in-oracle-database"></a>Oracle 資料庫中接收以輪詢為基礎的資料變更訊息的支援
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓用戶端程式來接收通知的 Oracle 資料庫中儲存的資料變更的 Oracle 資料庫中的訊息。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接收 「 以輪詢為基礎 」 的訊息，其中指定的 SELECT 查詢、 預存程序、 函數或程序或函式，在封裝中，而執行配接器的支援擷取資料，並提供結果給一般用戶端時間間隔。 若要這麼做， [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] POLLINGSTMT 作業公開 （expose)。 此外，所有預存程序、 函數和程序和封裝內的函式會公開做為輸入的作業進行輪詢。  

 配接器會提供兩種輪詢 Oracle 資料庫：  

-   **使用 SELECT 陳述式**。 您可以指定要輪詢的資料表和檢視 Oracle 資料庫中的簡單 SELECT 陳述式。 配接器執行 SELECT 陳述式，以指定的間隔，並將結果傳回至配接器用戶端。  

-   **使用預存程序、 函數或程序或函式，在封裝內**。 您可以指定預存程序、 函數或程序或輪詢 Oracle 資料庫在封裝內的函式。 配接器會在指定的時間間隔執行的要求訊息，並將結果傳回至配接器用戶端。  

## <a name="polling-operation-workflow"></a>輪詢作業的工作流程  
 典型的輪詢作業使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]牽涉到下列：  

1. 配接器用戶端必須指定**輪詢**中輸入的作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值是**輪詢**。  

2. 配接器用戶端必須指定的 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷是否有資料可供輪詢。 在執行此陳述式時，傳回的結果集的第一個資料列的第一個資料行包含整數值，如果有可用日期進行輪詢。 根據預設，此繫結屬性的值設為`Select 1 FROM DUAL`，這表示配接器，必須繼續輪詢，無論資料表輪詢是否有資料。  

3. 配接器用戶端必須指定輪詢間隔**PollingInterval**繫結屬性來定義以秒為單位的陳述式中指定的間隔**PolledDataAvailableStatement**執行繫結屬性。 在每個輪詢間隔結束時，輪詢的資料提供陳述式會執行，而且會傳回結果集。  

4. 配接器用戶端必須指定 SELECT 陳述式或預存程序**PollingStatement**繫結屬性。  

   - 如果您想要輪詢的資料表或檢視，您必須指定這個繫結屬性中的 SELECT 查詢。  

   - 如果您想要使用預存程序、 函數或程序或在封裝內的函式進行輪詢，您必須指定這個繫結屬性中的個別作業的整個要求訊息。  

     中的陳述式**PollingStatement**繫結屬性只有當沒有資料可供輪詢，取決於執行**PolledDataAvailableStatement**步驟 1 中的繫結屬性。  

5. 配接器用戶端必須指定在輪詢作業動作**PollingAction**繫結屬性。 輪詢動作特定的作業是從 取用配接器服務增益集所使用的作業產生的中繼資料來決定。  

   > [!NOTE]
   >  如果您正在輪詢資料表或檢視使用中的 SELECT 陳述式**PollingStatement**繫結屬性，您不需要指定任何值**PollingAction**繫結屬性。 預設值，則為 Null 值，在此情況下傳遞。  

6. 配接器用戶端可以使用**PollWhileDataFound**忽略輪詢間隔，並持續輪詢資料，當有可用的屬性繫結。  

   > [!IMPORTANT]
   >  如果您設定的值**PollWhileDataFound**繫結屬性設為 True，配接器用戶端持續輪詢資料從 Oracle 和程序中開啟及關閉連線到 Oracle 資料庫在迴圈中。 因為 ODP.NET 開啟連線的速率大於連線正在關閉，連線會耗盡段時間之後，並擲回例外狀況。 因應之道，請確定值**UseOracleConnectionPool**設定為 True，和適當的值所述**IncrPoolSize**繫結屬性，即可控制連線的數目可以開啟配接器用戶端。  

7. 配接器用戶端可以指定後輪詢陳述式，Oracle 的 PL/SQL 區塊中，如**PostPollStatement**繫結屬性。 這個繫結屬性中指定的陳述式中指定的陳述式之後執行**PollingStatement**屬性繫結會執行。  

   配接器會輪詢陳述式和後輪詢陳述式包裝在交易中和的交易逾時值設定為指定的值**PollingInterval**繫結屬性。 因此，務必指定大於或等於處理內送訊息，並傳送回覆所需的時間的逾時值。 如果用戶端程式，使用訊息，或執行後輪詢查詢所花費的時間超過逾時值，會回復交易。 如果所花費的時間小於逾時值，配接器就會認可交易，並"會進入睡眠狀態 「 輪詢執行下一次輪詢之前的剩餘時間。  

   配接器會隱藏來自 Oracle 資料庫的任何空白的輪詢回應。  

## <a name="differences-between-polling-and-notification"></a>輪詢和通知之間的差異  
 輪詢和通知都是這兩個輸入的作業，而且有關 Oracle 資料庫中的資料變更通知配接器用戶端，但下表說明兩者之間的一些差異。 下列差異將協助您決定的作業，視您的需求而定：  


|                                                                                                                                                                                                                                                      輪詢                                                                                                                                                                                                                                                      |                                                                                                                              通知                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                                          支援的所有 Oracle 資料庫版本都支援輪詢[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。                                                                                                                                                                           |                                                                                               只支援 Oracle 資料庫版本 10.2 和更新版本通知。                                                                                               |
| 您可以設定輪詢間隔，以檢查適用於定期輪詢資料，或立即一樣，當有可用的資料。 **提示：** 輪詢可讓您更佳的輸送量的資料變更會持續發生，並不想為每項變更並發生時收到通知。 相反地，您可以指定之後，您想要的上次變更通知，因為發生錯誤的所有變更的通知的輪詢間隔。 |                                                                                                          資料變更通知是一律在瞬間完成。                                                                                                          |
|                                                                                                                                         輪詢配接器所起始。 若要驗證是否可供輪詢，資料，並藉由執行輪詢陳述式，如果某些資料已可供輪詢起始輪詢 SQL 陳述式執行配接器。                                                                                                                                         | 通知是由 Oracle 資料庫啟動。 只在配接器發出的通知陳述式會指示要起始通知，萬一沒有陳述式的結果集變更的資料庫。 通知是 Oracle 資料庫的功能。 |
|                                                                                                                                                                                                                 您可以使用輪詢陳述式來讀取或更新的 Oracle 資料庫中的資料。                                                                                                                                                                                                                  |                                                                                             您可以使用 notification 陳述式只讀取 Oracle 資料庫中的資料。                                                                                             |
|                                                                                                                                                                                                                            輪詢會告知您已變更的實際資料。                                                                                                                                                                                                                            |                                                                                   通知只會通知的類型變更的資料，例如 Insert、 Update 和 Delete。                                                                                    |

 如需詳細資訊：  

- 如何配接器支援從 Oracle 資料庫接收以輪詢為基礎的訊息，請參閱[接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。  

- 從 Oracle 資料庫使用接收以輪詢為基礎的訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 叫用函式與使用 Biztalk Server 的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md)。  

- 從使用 WCF 服務模型的 Oracle 資料庫接收以輪詢為基礎的訊息，請參閱[從 SQL Server 使用 WCF 通道模型來接收輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)。  

- 從使用 WCF 通道模型的 Oracle 資料庫接收以輪詢為基礎的訊息，請參閱[從 SQL Server 使用 WCF 通道模型來接收輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)。  

- 訊息結構和執行在有輪詢查詢的 SOAP 動作，請參閱[輪詢作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md)。  

## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)