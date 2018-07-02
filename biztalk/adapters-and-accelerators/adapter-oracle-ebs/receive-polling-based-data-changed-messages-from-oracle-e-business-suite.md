---
title: 從 Oracle E-business Suite 接收以輪詢為基礎的資料變更訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cbcb23d0-508d-4601-91b4-c674d76cd063
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba602119a6143aae83e72b5c230f91f33a4eb5bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977615"
---
# <a name="receive-polling-based-data-changed-messages-from-oracle-e-business-suite"></a>從 Oracle E-business Suite 接收以輪詢為基礎的資料變更訊息
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]支援藉由輪詢介面資料表、 介面檢視、 資料表及檢視接收以輪詢為基礎的資料變更訊息。 配接器會將訊息傳遞到應用程式：  

- 執行 SQL SELECT 查詢來判斷資料是否可供輪詢。 您可以設定配接器以定期或連續執行的 SQL SELECT 查詢。  

- 執行 SQL SELECT 查詢，針對 Oracle 資料表或檢視，或執行預存程序、 函數或封裝的程序和函式。  

- 在 Oracle E-business Suite 上執行選擇性的後續輪詢 PL/SQL 程式碼區塊。 此程式碼區塊是通常用來更新目標中的查詢記錄中的欄位，或將查詢的記錄移到另一個資料表或檢視表。  

- 在結果中傳回查詢結果，來設定輪詢作業或預存程序、 函數或封裝的程序和函式公開為輪詢作業叫用。  

  所有這些作業在 Oracle 交易內執行配接器。  

## <a name="how-do-i-configure-the-oracle-e-business-adapter-for-receiving-data-changed-messages-using-binding-properties"></a>如何設定 Oracle E-business 配接器的接收資料變更的訊息，使用繫結屬性中？  
 您設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]藉由設定部分或所有下列繫結屬性的接收資料變更的訊息。  


|         繫結屬性         |                                                                                                                                                                                                                                                                                                                                                                                     ReplTest1                                                                                                                                                                                                                                                                                                                                                                                     | 預設 |                                必要項目/選用項目                                |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|---------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                                                                                                                                                                                                                請確定值設定為**輪詢**。                                                                                                                                                                                                                                                                                                                                                                | 輪詢 |         必要。 如果沒有明確設定，預設值會套用。          |
| **PolledDataAvailableStatement** | 指定執行，以判斷是否有任何資料可供輪詢的特定資料表的 SELECT 陳述式。 指定的陳述式必須傳回的結果集資料列和資料行所組成。 結果集的第一個資料格中的值會指出配接器是否要執行指定的值**PollingInput**繫結屬性。 如果結果的第一個資料格包含正值，配接器會執行輪詢陳述式。 比方說，將會是有效的陳述式，這個繫結屬性：<br /><br /> `Select * from <table_name>`<br /><br /> **注意：** 您必須指定這個繫結屬性的預存程序。 此外，此陳述式必須修改 Oracle E-business Suite 或基礎的 Oracle 資料庫中的資料。 |  null   |                                    必要。                                    |
|        **PollingAction**         |                                                                                                                                                                                                                                                          指定輪詢作業的動作。 您可以判斷特定的作業，從您為作業使用產生的中繼資料的輪詢動作[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。                                                                                                                                                                                                                                                          |  null   | 可選擇性地用於資料表和檢視使用 SELECT 陳述式上的輪詢作業。 |
|         **PollingInput**         |                                                                                                                                                       指定下列其中一項：<br /><br /> 應對其執行 Oracle E-business Suite 的 SQL SELECT 陳述式。 這個陳述式應該包含 FOR UPDATE 子句。 在 FOR UPDATE 子句的相關資訊，請參閱[輪詢陳述式中指定 FOR UPDATE 子句](#ForUpdate)本主題稍後的。<br /><br /> -要求訊息的預存程序、 函數或程序或函式在您想要輪詢的封裝。                                                                                                                                                       |  null   |     必要。 設定**PollingInput**為非 null 值會啟用輪詢。     |
|       **PollingInterval**        |                                                                                                                                                       設定的間隔，以秒為單位，您想要查詢 Oracle E-business Suite 配接器。 此屬性指定的輪詢間隔和輪詢交易逾時。值應大於 （如果已指定） 在 Oracle E-business Suite 上執行的查詢和後輪詢陳述式所花費的時間長度再加上的用戶端處理查詢的資料，並傳回輪詢回應訊息所花費的時間量。                                                                                                                                                       |   30    |         必要。 如果沒有明確設定，預設值會套用。          |
|      **PollWhileDataFound**      |                                                                                                                                                                                                      指定是否[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會忽略的輪詢間隔，並持續輪詢 Oracle E-business Suite，如果資料可在所輪詢的資料表中。 如果沒有資料可在資料表中，配接器會還原到執行 SQL 陳述式，在指定的輪詢間隔                                                                                                                                                                                                      |  False  |         必要。 如果沒有明確設定，預設值會套用。          |
|      **PostPollStatement**       |                                                                                                                                                                                                                                                                                                            設定為選擇性的 PL/SQL 程式碼區塊之後，執行查詢，但資料傳回給用戶端在查詢之前，會將配接器所執行。                                                                                                                                                                                                                                                                                                            |  null   |   選擇性。 如果未不指定任何值，不會執行後輪詢陳述式。    |

> [!NOTE]
>  如果您使用 WCF 服務模型或 WCF 通道模型，您也必須設定**AcceptCredentialsInUri**繫結屬性。  

##  <a name="ForUpdate"></a> 指定 FOR 更新輪詢陳述式中的子句  
 如果您使用 SELECT 陳述式作為輪詢陳述式，並執行後輪詢陳述式會影響指定 SELECT 陳述式中的資料列，您必須使用在 FOR UPDATE 子句中的輪詢陳述式。 指定 FOR UPDATE 子句可確保在交易期間，會鎖定輪詢陳述式所選取的記錄和後輪詢陳述式可以在其上執行任何必要的更新。  

> [!CAUTION]
>  您可以在案例在輪詢和後輪詢陳述式之間的時間範圍，詳細的記錄新增至符合條件後輪詢陳述式的資料表。 在這種情況下後, 輪詢陳述式會更新滿足條件的所有記錄和不只是將輪詢陳述式的過程中選取的記錄。  

 如果後輪詢陳述式指定，且輪詢陳述式不包含 FOR UPDATE 子句，則會發生下列兩項條件的其中一個：  

- 如果**TransactionIsolationLevel**設為**ReadCommitted**，後續的輪詢查詢將不會更新選取的資料列。  

- 如果**TransactionIsolationLevel**設為**Serializable**，下列為目標的系統例外狀況 (**Microsoft.ServiceModel.Channels.Common.TargetSystemException**) 會執行後輪詢陳述式: 「 ora-08177 無法序列化這筆交易的存取權 」。 在此情況下，您必須設定**PollingRetryCount**繫結屬性可定義數字的次數中，您想要重試相同的交易配接器。  

  如需有關如何設定交易隔離等級的指示，請參閱 <<c0> [ 使用 Oracle E-business Suite 設定交易隔離等級和交易等待時間](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)。  

  如果配接器用戶端已設定為使用交易的值，輪詢和後輪詢陳述式會在交易中執行**UseAmbientTransaction**繫結屬性設定為**True**配接器中。  

  FOR UPDATE 選項在有輪詢查詢的範例為：  

```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE  
```  

### <a name="specifying-a-nowait-clause-in-the-polling-statement"></a>輪詢陳述式中指定 NOWAIT 子句  
 您的案例，並行執行緒存取所輪詢的資料表可能導致資料表中有太多的爭用。 這可能會導致封鎖，若要取得資料表的資料列的鎖定，輪詢查詢。 如果您使用的輪詢陳述式的 SELECT 陳述式，您可能想要在 SELECT 陳述式中指定 NOWAIT 關鍵字與 FOR UPDATE 關鍵字。 這會導致立即傳回，輪詢查詢嘗試選取的資料列上是否有鎖定配接器內的輪詢查詢執行。 在這種情況下通常發生例外狀況由 Oracle。 同樣地，使用配接器用戶端可能**PollingInterval**繫結屬性，以指定的時間間隔之後，配接器用戶端必須重試一次輪詢資料。  

 使用 NOWAIT 選項在有輪詢查詢的範例為：  

```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE NOWAIT  
```  

### <a name="specifying-a-skip-locked-clause-in-the-polling-statement"></a>輪詢陳述式中指定略過已鎖定子句  
 您可能需要位置存取輪詢該資料表的並行執行緒，因為 WHERE 子句，指定在輪詢查詢結果集中的某些資料列鎖定的案例。 比方說，輪詢查詢會傳回 6 個資料列從一個資料表中;因為有其他交易已鎖定 4 超出這些 6 個資料列。 在此情況下，您可以指定鎖定略過的關鍵字以及 FOR UPDATE 關鍵字，指示要嘗試鎖定 WHERE 子句中，所指定的資料列，並略過已鎖定所找到的任何資料列的資料庫。 WHERE 子句中未鎖定的資料列會在交易期間鎖定和後輪詢陳述式可以執行任何必要的更新在其上，讓這些資料列不會輪詢一次。 這可確保您不需要等候接收輪詢訊息，直到所有資料列可讓您指定由 WHERE 子句會解除鎖定。  

 略過鎖定關鍵字可用於您有下列狀況配接器用戶端會輪詢相同的資料表，在資料庫中的多部電腦上。 您可以在配接器用戶端之間的平衡負載藉由設定輪詢作業的方式，您會收到輪詢為基礎的資料變更會在該點的時間，解除鎖定的資料列的 WHERE 子句所指定的訊息，然後更新 以確保資料列如果由配接器用戶端收到輪詢為基礎的資料變更訊息時，其他用戶端不會取得相同的訊息。  

 在有輪詢查詢，以略過鎖定選項的範例為：  

```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE SKIP LOCKED  
```  

## <a name="support-for-ordered-delivery-fifo"></a>排序的傳遞 (FIFO) 的支援  
 在生產環境中，輪詢可以用於監視 Oracle E-business Suite 中的資料變更。 這些資料變更訊息接收配接器用戶端使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 根據商務案例，它可能很重要的資料變更訊息接收配接器用戶端，以正確的順序。  

 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援排序的傳遞或後進先出 (FIFO) 來維護從 Oracle E-business Suite 接收訊息的順序。 以下是幾個考量與支援的輸入案例中的 FIFO [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  

- 如果訊息由協調流程，協調流程必須排序的傳遞設定來自訊息[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收埠。  

- 如果訊息由傳送連接埠 （以內容為基礎的路由） 案例，傳送埠必須已排序的傳遞設定來自訊息[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收埠。  

  WCF 自訂] 或 [Wcf-oracleebs 配接器都具有屬性**失敗時擱置要求訊息**，指定是否要擱置輸入的處理失敗的要求訊息。 這個屬性可以設定在**訊息**Wcf-custom 或 Wcf-oracleebs 索引標籤會收到下的連接埠**錯誤處理**一節。 下表列出描述如何處理內送訊息的案例取決於是否設定這個屬性和狀態訊息的訂閱者 （協調流程或連接埠）。  

|WCF 自訂連接埠，屬性|取消登錄狀態中的訂閱者|在 已登錄的訂閱者 」，但已停止 」 狀態|  
|-------------------------------|------------------------------------|----------------------------------------------|  
|**擱置失敗的要求訊息**屬性未設定|-路由失敗報告產生為已擱置 （不可繼續訊息）<br /><br /> 為不會擱置實際的訊息<br /><br /> -Post 輪詢查詢不會執行為中止交易。 因此輪詢時，會重複，而且一次提取資料列。<br /><br /> -報告在事件記錄檔，以描述發生的錯誤。|-不被視為 「 失敗 」。 事件記錄檔中有任何錯誤訊息。<br /><br /> -實際的訊息會放入擱置 （可繼續） 的佇列。<br /><br /> -當訂閱的連接埠或協調流程啟動時，訊息就會自動繼續。 如果 「 訂閱者 」 上設定排序的傳遞，它會接受它。<br /><br /> -訊息也會繼續以手動方式。|  
|**擱置失敗的要求訊息**屬性設定|-路由失敗報告產生為已擱置 （不可繼續訊息）<br /><br /> -實際的訊息也會暫止<br /><br /> -Post 輪詢查詢不會執行為中止交易。 因此輪詢時，會重複，而且一次提取資料列。<br /><br /> -報告在事件記錄檔，以描述發生的錯誤。|-不被視為 「 失敗 」。 事件記錄檔中有任何錯誤訊息。<br /><br /> -實際的訊息會放入擱置 （可繼續） 的佇列。<br /><br /> -當訂閱的連接埠或協調流程啟動時，訊息就會自動繼續。 如果 「 訂閱者 」 上設定排序的傳遞，它會接受它。<br /><br /> -訊息也會繼續以手動方式。|  

## <a name="see-also"></a>另請參閱  
 [開發活動](../../esb-toolkit/development-activities.md)   
 [使用 BizTalk Server 輪詢 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)