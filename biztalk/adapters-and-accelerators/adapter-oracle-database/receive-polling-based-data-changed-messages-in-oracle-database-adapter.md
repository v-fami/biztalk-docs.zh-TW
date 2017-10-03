---
title: "在 Oracle 資料庫配接器收到輪詢基礎資料變更的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: polling-base notification, support for
ms.assetid: 043afb88-701c-41d8-8b8e-84702bd0d984
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f234e57353d22c785dc57271add297e7a6d2c9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-in-oracle-database-adapter"></a>在 Oracle 資料庫配接器收到輪詢基礎資料變更的訊息
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援藉由輪詢 Oracle 資料庫接收輪詢基礎資料變更的訊息。 配接器會將訊息傳遞至應用程式：  
  
-   執行 SQL SELECT 查詢，以判定資料是否可用於輪詢。 您可以設定執行 SQL SELECT 查詢，定期或連續執行配接器。  
  
-   執行 SQL SELECT 查詢，對 Oracle 資料表或檢視表，或執行預存程序、 函數或封裝的程序和函式。  
  
-   Oracle 資料庫上執行選擇性的後續輪詢 PL/SQL 程式碼區塊。 這個程式碼區塊常用來更新目標中的查詢記錄中的欄位，或將查詢的記錄移到另一個資料表或檢視表。  
  
-   在結果中傳回查詢結果來設定 POLLINGSTMT 作業或預存程序、 函數或封裝的程序和函式公開為輪詢作業叫用。  
  
 執行配接器的所有 Oracle 交易內的這些作業。  
  
 配接器也可讓您接收相同的應用程式中的 Oracle 的多個成品的資料變更訊息，藉由公開`PollingId`連線 URI 中的參數。 這個參數會修改 POLLINGSTMT 作業的目標命名空間。  
  
## <a name="change-the-target-namespace-of-pollingstmt"></a>變更 POLLINGSTMT 的目標命名空間  
 您可以藉由設定修改 POLLINGSTMT 作業的目標命名空間`PollingId`查詢字串參數，在 連線 URI。 如果`PollingId`連接 URI 中指定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]將中所指定的字串附加`PollingId`POLLINGSTMT 作業的預設目標命名空間的參數： `http://microsoft.lobservices.oracledb/2007/03/POLLINGSTMT`。 不會修改 POLLINGSTMT 作業的訊息動作。  
  
 例如，如果指定下列連線 URI: `OracleDb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity`，目標命名空間將`http:/microsoft.lobservices.oracledb/2007/03/POLLINGSTMTAcctActivity`。  
  
 每個 POLLINGSTMT 作業提供唯一的命名空間，即可在您的應用程式中接收多個 Oracle 資料表和檢視表的資料變更的訊息。  
  
 如需有關[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]連線 URI，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  
  
## <a name="receive-data-changed-messages-using-binding-properties"></a>接收資料變更的訊息，使用繫結屬性
 您設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]来接收的資料變更訊息的部分或所有下列繫結屬性的設定。  
  
|繫結屬性|值|預設值|必要項目/選用項目|  
|----------------------|-----------|-------------|------------------------|  
|**InboundOperationType**|請確定值設定為**輪詢**。|輪詢|必要。 如果沒有明確設定，預設值會套用。|  
|**PolledDataAvailableStatement**|指定 SELECT 陳述式執行，以判斷是否可用於針對特定資料表輪詢的任何資料。 指定的陳述式必須傳回的結果集資料列和資料行所組成。 結果集的第一個資料格中的值，指出配接器是否會執行指定的值**PollingStatement**繫結屬性。 如果結果的第一個資料格包含正數值時，配接器會執行輪詢陳述式。 例如，會是有效的陳述式，這個繫結屬性：<br /><br /> `Select * from <table_name>`<br /><br /> **注意：**您必須指定這個繫結屬性的預存程序。 此外，此陳述式不得修改基礎的 Oracle 資料庫。|從雙選取 1|必要。 如果沒有明確設定，預設值會套用，這表示配接器必須繼續輪詢無論資料表輪詢是否有資料。|  
|**PollingAction**|指定輪詢作業的動作。 您可以判斷您的作業使用產生的中繼資料從特定作業的輪詢動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。|null|選擇性的資料表和檢視表使用 SELECT 陳述式的輪詢作業。|  
|**PollingInterval**|設定的間隔，以秒為單位，用來查詢 Oracle 資料庫配接器。 此屬性指定的輪詢間隔，輪詢交易逾時時間。值必須大於查詢和後輪詢陳述式 （如果已指定） 的 Oracle 資料庫上執行所花費的時間量再加上的用戶端處理的查詢資料，並傳回輪詢回應訊息所花費的時間量。|500|必要。 如果沒有明確設定，預設值會套用。|  
|**PollingStatement**|指定下列其中一項：<br /><br /> 應該針對 Oracle 資料庫執行的 SQL SELECT 陳述式。 這個陳述式應該包含 FOR UPDATE 子句。 FOR UPDATE 子句的相關資訊，請參閱[輪詢陳述式中指定 FOR UPDATE 子句](#ForUpdate)本主題稍後。<br /><br /> -要求的預存程序、 函數或程序或函式內的封裝，您想要輪詢的訊息。|null|必要。 設定**PollingStatement**為非 null 值可讓輪詢。|  
|**PollWhileDataFound**|指定是否[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]忽略的輪詢間隔，並持續輪詢 Oracle 資料庫，如果輪詢資料表中的可用資料。 如果沒有資料可在資料表中，配接器會還原到執行 SQL 陳述式，在指定的輪詢間隔|False|必要。 如果沒有明確設定，預設值會套用。|  
|**PostPollStatement**|設定為選擇性的 PL/SQL 程式碼區塊所執行的配接器之後，會執行查詢，但在查詢之前資料傳回至用戶端。|null|選擇性。 如果未不指定任何值，不會執行後輪詢陳述式。|  
  
> [!NOTE]
>  如果您使用 WCF 服務模型或 WCF 通道模型，您也必須設定**AcceptCredentialsInUri**繫結屬性。  
  
##  <a name="ForUpdate"></a>輪詢陳述式中輸入的更新  
 如果您使用 SELECT 陳述式以及輪詢陳述式執行後輪詢陳述式會影響指定 SELECT 陳述式中的資料列，您必須在輪詢陳述式中使用 FOR UPDATE 子句。 指定 FOR UPDATE 子句可確保在交易期間鎖定了輪詢陳述式所選取的記錄和後輪詢陳述式，可以在其上執行任何必要的更新。  
  
> [!CAUTION]
>  您可以在案例的輪詢和後輪詢陳述式之間的時間間隔，記錄會加入至符合的條件後輪詢陳述式的資料表。 在這種情況下後, 輪詢陳述式會更新滿足條件的所有記錄和不只是輪詢陳述式的過程中選取的記錄。  
  
 如果後輪詢陳述式指定，且輪詢陳述式不包含 FOR UPDATE 子句，就會發生下列兩種情況的其中一個：  
  
-   如果**TransactionIsolationLevel**設**ReadCommitted**，後續輪詢查詢不會更新選取的資料列。  
  
-   如果**TransactionIsolationLevel**設**Serializable**下, 目標系統例外狀況 (**Microsoft.ServiceModel.Channels.Common.TargetSystemException**) 執行後輪詢陳述式時，會發生:"ora-08177 無法序列化這筆交易的存取 」。 在此情況下，您必須設定**PollingRetryCount**繫結屬性可定義數字的次數中，您想要重試相同的交易配接器。  
  
 如需有關如何設定交易隔離等級的指示，請參閱[設定 Oracle 資料庫的交易隔離等級和交易逾時](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)。  
  
 如果配接器用戶端已設定為使用交易，而在交易中執行的輪詢和後輪詢陳述式**UseAmbientTransaction**繫結屬性設定為**True**配接器中。  
  
 FOR UPDATE 選項在有輪詢查詢的範例是：  
  
```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE  
```  
  
### <a name="enter-a-nowait-clause-in-the-polling-statement"></a>輪詢陳述式中輸入 NOWAIT 子句  
 您可能需要存取的並行執行緒輪詢，資料表的案例資料表中有太多的爭用所導致。 這可能會造成輪詢查詢，以取得資料表的資料列的鎖定封鎖。 如果您使用 SELECT 陳述式與輪詢陳述式，您可以在 SELECT 陳述式中指定 NOWAIT 關鍵字與 FOR UPDATE 關鍵字。 這會導致輪詢查詢內執行配接器的輪詢查詢嘗試選取的資料列上是否有鎖定立即傳回。 擲回例外狀況通常是由 Oracle 這種情況下。 同樣地，使用配接器用戶端可能**PollingInterval**內容繫結至指定的時間間隔之後的配接器用戶端必須重試輪詢資料。  
  
 使用 NOWAIT 選項在有輪詢查詢的範例是：  
  
```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE NOWAIT  
```  
  
### <a name="enter-a-skip-locked-clause-in-the-polling-statement"></a>輪詢陳述式中輸入鎖定 SKIP 子句  
 您可能需要其中並行執行緒存取輪詢資料表，因為 WHERE 子句，指定在輪詢查詢結果集中的某些資料列鎖定的案例。 例如，輪詢查詢會傳回 6 個資料列從資料表;因為其他交易已鎖定 4 超出這些 6 個資料列。 在此情況下，您可以指定 FOR UPDATE 關鍵字會指示資料庫在嘗試鎖定 WHERE 子句所指定的資料列，並略過已鎖定所找到的任何資料列，以及略過鎖定的關鍵字。 WHERE 子句中未鎖定的資料列會在交易期間鎖定和後輪詢陳述式可以執行任何必要的更新其上，讓這些資料列不會輪詢一次。 這可確保您不需要等候所有資料列指定由 WHERE 子句會解除鎖定之前，接收的輪詢訊息。  
  
 略過鎖定關鍵字中很有用的案例，其中您的配接器用戶端輪詢資料庫中的相同資料表的多部電腦。 您可以藉由設定輪詢作業的方式收到輪詢基礎資料變更會解除鎖定的時間，在該點的資料列的 WHERE 子句所指定的訊息進行負載平衡所有配接器用戶端，並再更新以確保資料列如果由配接器用戶端收到訊息以輪詢為基礎的資料變更時，其他用戶端不會收到相同的訊息。  
  
 在有輪詢查詢，以略過鎖定選項的範例是：  
  
```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE SKIP LOCKED  
```  
  
## <a name="support-for-ordered-delivery-fifo"></a>支援排序的傳遞 (FIFO)  
 在生產環境中，輪詢可以用於監視 Oracle 資料庫中的資料變更。 這些資料變更訊息接收配接器用戶端使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 根據商務案例，它可能很重要的資料變更的訊息接收配接器用戶端，以正確的順序。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援排序傳遞或先進先出 (FIFO) 維持從 Oracle 資料庫接收訊息的順序。 以下是幾個考量與支援中的輸入案例的 FIFO [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
-   如果訊息由協調流程，協調流程必須排序的傳遞設定來自訊息[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接收埠。  
  
-   如果訊息由傳送連接埠 （以內容為基礎的路由） 案例，傳送埠必須已排序的傳遞設定來自訊息[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接收埠。  
  
 Wcf-custom 或 Wcf-oracledb 配接器都具有屬性**擱置失敗的要求訊息**，指定是否要擱置輸入的處理失敗的要求訊息。 這個屬性可以設定上**訊息**Wcf-custom 或 Wcf-oracledb 索引標籤上接收連接埠之下**錯誤處理**> 一節。 下表列出的案例描述處理內送訊息的方式取決於是否設定這個屬性和狀態訊息訂閱者 （協調流程或連接埠）。  
  
|Port 屬性|訂閱者 」 中取消登錄狀態|在登錄中的訂閱者 」，但已停止 」 狀態|  
|-------------------|------------------------------------|----------------------------------------------|  
|**擱置失敗的要求訊息**屬性未設定|-路由失敗報告，會產生為擱置 （不可繼續擱置的訊息）<br /><br /> 為不會擱置實際的訊息<br /><br /> -Post 輪詢查詢不會執行為取得中止交易。 因此輪詢會重複，而且一次提取資料列。<br /><br /> -報告在事件記錄檔，以描述發生錯誤。|-不會視為 「 失敗 」。 事件記錄檔中有任何錯誤訊息。<br /><br /> -實際訊息會放入擱置 （可繼續） 佇列。<br /><br /> -訂閱的連接埠或協調流程啟動時，訊息就會自動繼續。 如果 「 訂閱者 」 上設定排序的傳遞，就會生效。<br /><br /> 也可以手動方式恢復-訊息。|  
|**擱置失敗的要求訊息**屬性設定|-路由失敗報告，會產生為擱置 （不可繼續擱置的訊息）<br /><br /> 的也會暫止實際訊息<br /><br /> -Post 輪詢查詢不會執行為取得中止交易。 因此輪詢會重複，而且一次提取資料列。<br /><br /> -報告在事件記錄檔，以描述發生錯誤。|-不會視為 「 失敗 」。 事件記錄檔中有任何錯誤訊息。<br /><br /> -實際訊息會放入擱置 （可繼續） 佇列。<br /><br /> -訂閱的連接埠或協調流程啟動時，訊息就會自動繼續。 如果 「 訂閱者 」 上設定排序的傳遞，就會生效。<br /><br /> 也可以手動方式恢復-訊息。|  
  
## <a name="see-also"></a>另請參閱  
[開發應用程式的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)  
 [使用 BizTalk Server 輪詢 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-biztalk-server.md)   
 [在 Oracle 資料庫中使用 WCF 服務模型收到輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md)   
 [使用 WCF 通道模型的 Oracle 資料庫中收到輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)