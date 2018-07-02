---
title: 在 Oracle 資料庫配接器接收以輪詢為基礎的資料變更訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- polling-base notification, support for
ms.assetid: 043afb88-701c-41d8-8b8e-84702bd0d984
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f8ee32a7907cc37daf4a6b6b7d3971a28cf1b94
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968935"
---
# <a name="receive-polling-based-data-changed-messages-in-oracle-database-adapter"></a>在 Oracle 資料庫配接器接收以輪詢為基礎的資料變更訊息
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援藉由輪詢 Oracle 資料庫接收以輪詢為基礎的資料變更訊息。 配接器會將訊息傳遞到應用程式：  

- 執行 SQL SELECT 查詢來判斷資料是否可供輪詢。 您可以設定配接器以定期或連續執行的 SQL SELECT 查詢。  

- 執行 SQL SELECT 查詢，針對 Oracle 資料表或檢視，或執行預存程序、 函數或封裝的程序和函式。  

- Oracle 資料庫上執行選擇性的後續輪詢 PL/SQL 程式碼區塊。 此程式碼區塊是通常用來更新目標中的查詢記錄中的欄位，或將查詢的記錄移到另一個資料表或檢視表。  

- 在結果中傳回查詢結果，藉由叫用 POLLINGSTMT 作業或預存程序、 函數或封裝的程序和函式公開為輪詢作業設定。  

  執行上述所有作業內的 Oracle 交易配接器。  

  配接器也可讓您接收相同的應用程式中的多個 Oracle 成品的資料變更訊息，藉由公開`PollingId`連線 URI 中的參數。 此參數修改 POLLINGSTMT 作業的目標命名空間。  

## <a name="change-the-target-namespace-of-pollingstmt"></a>變更 POLLINGSTMT 的目標命名空間  
 您可以藉由設定修改 POLLINGSTMT 作業的目標命名空間`PollingId`查詢字串參數，在 連線 URI。 如果`PollingId`中的連線 URI，指定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]中指定的字串會將附加`PollingId`POLLINGSTMT 作業的預設目標命名空間的參數： `http://microsoft.lobservices.oracledb/2007/03/POLLINGSTMT`。 不會修改 POLLINGSTMT 作業的訊息動作。  

 例如，如果指定下列連線 URI: `OracleDb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity`，目標命名空間會`http:/microsoft.lobservices.oracledb/2007/03/POLLINGSTMTAcctActivity`。  

 藉由提供唯一的命名空間的每個 POLLINGSTMT 作業，您可以在您的應用程式中接收多個 Oracle 資料表和檢視表的資料變更訊息。  

 如需詳細資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  

## <a name="receive-data-changed-messages-using-binding-properties"></a>接收資料變更的訊息，使用繫結屬性
 您設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]藉由設定部分或所有下列繫結屬性的接收資料變更的訊息。  


|         繫結屬性         |                                                                                                                                                                                                                                                                                                                                                                   ReplTest1                                                                                                                                                                                                                                                                                                                                                                    |      預設       |                                                                                  必要項目/選用項目                                                                                  |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                                                                                                                                                                                              請確定值設定為**輪詢**。                                                                                                                                                                                                                                                                                                                                               |      輪詢       |                                                           必要。 如果沒有明確設定，預設值會套用。                                                            |
| **PolledDataAvailableStatement** | 指定執行，以判斷是否有任何資料可供輪詢的特定資料表的 SELECT 陳述式。 指定的陳述式必須傳回的結果集資料列和資料行所組成。 結果集的第一個資料格中的值會指出配接器是否要執行指定的值**PollingStatement**繫結屬性。 如果結果的第一個資料格包含正值，配接器會執行輪詢陳述式。 比方說，將會是有效的陳述式，這個繫結屬性：<br /><br /> `Select * from <table_name>`<br /><br /> **注意：** 您必須指定這個繫結屬性的預存程序。 此外，此陳述式不能修改基礎的 Oracle 資料庫。 | 從雙選取 1 | 必要。 如果沒有明確設定，預設值會套用，這表示配接器必須繼續輪詢，無論所輪詢的資料表是否有資料。 |
|        **PollingAction**         |                                                                                                                                                                                                                                        指定輪詢作業的動作。 您可以判斷特定的作業，從您為作業使用產生的中繼資料的輪詢動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。                                                                                                                                                                                                                                         |        null        |                                                   可選擇性地用於資料表和檢視使用 SELECT 陳述式上的輪詢作業。                                                   |
|       **PollingInterval**        |                                                                                                                                         設定的間隔，以秒為單位，要來查詢 Oracle 資料庫配接器。 此屬性指定的輪詢間隔和輪詢交易逾時。值應大於執行查詢和後輪詢陳述式 （如果已指定） 的 Oracle 資料庫上所花費的時間長度再加上的用戶端處理查詢的資料，並傳回輪詢回應訊息所花費的時間量。                                                                                                                                          |        500         |                                                           必要。 如果沒有明確設定，預設值會套用。                                                            |
|       **PollingStatement**       |                                                                                                                                       指定下列其中一項：<br /><br /> 應該針對 Oracle 資料庫執行的 SQL SELECT 陳述式。 這個陳述式應該包含 FOR UPDATE 子句。 在 FOR UPDATE 子句的相關資訊，請參閱[輪詢陳述式中指定 FOR UPDATE 子句](#ForUpdate)本主題稍後的。<br /><br /> -要求訊息的預存程序、 函數或程序或函式在您想要輪詢的封裝。                                                                                                                                        |        null        |                                                     必要。 設定**PollingStatement**為非 null 值會啟用輪詢。                                                     |
|      **PollWhileDataFound**      |                                                                                                                                                                                             指定是否[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會忽略的輪詢間隔，並持續輪詢 Oracle 資料庫，如果在所輪詢的資料表中的資料可用。 如果沒有資料可在資料表中，配接器會還原到執行 SQL 陳述式，在指定的輪詢間隔                                                                                                                                                                                              |       False        |                                                           必要。 如果沒有明確設定，預設值會套用。                                                            |
|      **PostPollStatement**       |                                                                                                                                                                                                                                                                                          設定為選擇性的 PL/SQL 程式碼區塊之後，執行查詢，但資料傳回給用戶端在查詢之前，會將配接器所執行。                                                                                                                                                                                                                                                                                           |        null        |                                                     選擇性。 如果未不指定任何值，不會執行後輪詢陳述式。                                                      |

> [!NOTE]
>  如果您使用 WCF 服務模型或 WCF 通道模型，您也必須設定**AcceptCredentialsInUri**繫結屬性。  

##  <a name="ForUpdate"></a> 輸入輪詢陳述式中的 FOR UPDATE  
 如果您使用 SELECT 陳述式作為輪詢陳述式，並執行後輪詢陳述式會影響指定 SELECT 陳述式中的資料列，您必須使用在 FOR UPDATE 子句中的輪詢陳述式。 指定 FOR UPDATE 子句可確保在交易期間，會鎖定輪詢陳述式所選取的記錄和後輪詢陳述式可以在其上執行任何必要的更新。  

> [!CAUTION]
>  您可以在案例在輪詢和後輪詢陳述式之間的時間範圍，詳細的記錄新增至符合條件後輪詢陳述式的資料表。 在這種情況下後, 輪詢陳述式會更新滿足條件的所有記錄和不只是將輪詢陳述式的過程中選取的記錄。  

 如果後輪詢陳述式指定，且輪詢陳述式不包含 FOR UPDATE 子句，則會發生下列兩項條件的其中一個：  

- 如果**TransactionIsolationLevel**設為**ReadCommitted**，後續的輪詢查詢將不會更新選取的資料列。  

- 如果**TransactionIsolationLevel**設為**Serializable**，下列為目標的系統例外狀況 (**Microsoft.ServiceModel.Channels.Common.TargetSystemException**) 會執行後輪詢陳述式: 「 ora-08177 無法序列化這筆交易的存取權 」。 在此情況下，您必須設定**PollingRetryCount**繫結屬性可定義數字的次數中，您想要重試相同的交易配接器。  

  如需有關如何設定交易隔離等級的指示，請參閱 <<c0> [ 設定與 Oracle 資料庫的交易隔離等級和交易等待時間](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)。  

  如果配接器用戶端已設定為使用交易的值，輪詢和後輪詢陳述式會在交易中執行**UseAmbientTransaction**繫結屬性設定為**True**配接器中。  

  FOR UPDATE 選項在有輪詢查詢的範例為：  

```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE  
```  

### <a name="enter-a-nowait-clause-in-the-polling-statement"></a>輪詢陳述式中，輸入使用 NOWAIT 子句  
 您的案例，並行執行緒存取所輪詢的資料表可能導致資料表中有太多的爭用。 這可能會導致封鎖，若要取得資料表的資料列的鎖定，輪詢查詢。 如果您使用的輪詢陳述式的 SELECT 陳述式，您可能想要在 SELECT 陳述式中指定 NOWAIT 關鍵字與 FOR UPDATE 關鍵字。 這會導致立即傳回，輪詢查詢嘗試選取的資料列上是否有鎖定配接器內的輪詢查詢執行。 在這種情況下通常發生例外狀況由 Oracle。 同樣地，使用配接器用戶端可能**PollingInterval**繫結屬性，以指定的時間間隔之後，配接器用戶端必須重試一次輪詢資料。  

 使用 NOWAIT 選項在有輪詢查詢的範例為：  

```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE NOWAIT  
```  

### <a name="enter-a-skip-locked-clause-in-the-polling-statement"></a>輸入輪詢陳述式中的鎖定略過的子句  
 您可能需要位置存取輪詢該資料表的並行執行緒，因為 WHERE 子句，指定在輪詢查詢結果集中的某些資料列鎖定的案例。 比方說，輪詢查詢會傳回 6 個資料列從一個資料表中;因為有其他交易已鎖定 4 超出這些 6 個資料列。 在此情況下，您可以指定鎖定略過的關鍵字以及 FOR UPDATE 關鍵字，指示要嘗試鎖定 WHERE 子句中，所指定的資料列，並略過已鎖定所找到的任何資料列的資料庫。 WHERE 子句中未鎖定的資料列會在交易期間鎖定和後輪詢陳述式可以執行任何必要的更新在其上，讓這些資料列不會輪詢一次。 這可確保您不需要等候接收輪詢訊息，直到所有資料列可讓您指定由 WHERE 子句會解除鎖定。  

 略過鎖定關鍵字可用於您有下列狀況配接器用戶端會輪詢相同的資料表，在資料庫中的多部電腦上。 您可以在配接器用戶端之間的平衡負載藉由設定輪詢作業的方式，您會收到輪詢為基礎的資料變更會在該點的時間，解除鎖定的資料列的 WHERE 子句所指定的訊息，然後更新 以確保資料列如果由配接器用戶端收到輪詢為基礎的資料變更訊息時，其他用戶端不會取得相同的訊息。  

 在有輪詢查詢，以略過鎖定選項的範例為：  

```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE SKIP LOCKED  
```  

## <a name="support-for-ordered-delivery-fifo"></a>排序的傳遞 (FIFO) 的支援  
 在生產環境中，輪詢可以用於監視 Oracle 資料庫中的資料變更。 這些資料變更訊息接收配接器用戶端使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 根據商務案例，它可能很重要的資料變更訊息接收配接器用戶端，以正確的順序。  

 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援排序的傳遞或後進先出 (FIFO) 來維護從 Oracle 資料庫接收訊息的順序。 以下是幾個考量與支援的輸入案例中的 FIFO [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  

- 如果訊息由協調流程，協調流程必須排序的傳遞設定來自訊息[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接收埠。  

- 如果訊息由傳送連接埠 （以內容為基礎的路由） 案例，傳送埠必須已排序的傳遞設定來自訊息[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接收埠。  

  WCF 自訂] 或 [Wcf-oracledb 配接器都具有屬性**失敗時擱置要求訊息**，指定是否要擱置輸入的處理失敗的要求訊息。 這個屬性可以設定在**訊息**Wcf-custom 或 Wcf-oracledb 索引標籤會收到下的連接埠**錯誤處理**一節。 下表列出描述如何處理內送訊息的案例取決於是否設定這個屬性和狀態訊息的訂閱者 （協調流程或連接埠）。  

|Port 屬性|取消登錄狀態中的訂閱者|在 已登錄的訂閱者 」，但已停止 」 狀態|  
|-------------------|------------------------------------|----------------------------------------------|  
|**擱置失敗的要求訊息**屬性未設定|-路由失敗報告產生為已擱置 （不可繼續訊息）<br /><br /> 為不會擱置實際的訊息<br /><br /> -Post 輪詢查詢不會執行為中止交易。 因此輪詢時，會重複，而且一次提取資料列。<br /><br /> -報告在事件記錄檔，以描述發生的錯誤。|-不被視為 「 失敗 」。 事件記錄檔中有任何錯誤訊息。<br /><br /> -實際的訊息會放入擱置 （可繼續） 的佇列。<br /><br /> -當訂閱的連接埠或協調流程啟動時，訊息就會自動繼續。 如果 「 訂閱者 」 上設定排序的傳遞，它會接受它。<br /><br /> -訊息也會繼續以手動方式。|  
|**擱置失敗的要求訊息**屬性設定|-路由失敗報告產生為已擱置 （不可繼續訊息）<br /><br /> -實際的訊息也會暫止<br /><br /> -Post 輪詢查詢不會執行為中止交易。 因此輪詢時，會重複，而且一次提取資料列。<br /><br /> -報告在事件記錄檔，以描述發生的錯誤。|-不被視為 「 失敗 」。 事件記錄檔中有任何錯誤訊息。<br /><br /> -實際的訊息會放入擱置 （可繼續） 的佇列。<br /><br /> -當訂閱的連接埠或協調流程啟動時，訊息就會自動繼續。 如果 「 訂閱者 」 上設定排序的傳遞，它會接受它。<br /><br /> -訊息也會繼續以手動方式。|  

## <a name="see-also"></a>另請參閱  
[開發您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)  
 [使用 BizTalk Server 輪詢 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-biztalk-server.md)   
 [使用 WCF 服務模型的 Oracle 資料庫中接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md)   
 [使用 WCF 通道模型的 Oracle 資料庫中接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)