---
title: BizTalk SQL 配接器疑難排解操作問題 |Microsoft Docs
description: 常見問題和解決方案的 SQL 配接器在 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c75f85f4-cd03-4c6a-aac9-a6d02d3c3449
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccb3f48fca23825ec98fdc7f38012e44f7b2a00e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994583"
---
# <a name="troubleshoot-operational-issues-with-the-sql-adapter"></a>SQL 配接器疑難排解操作問題
本節討論如何使用以解決使用時可能遭遇的操作錯誤的疑難排解技巧[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]。  
  
## <a name="enabling-tracing"></a>啟用追蹤  
 您必須啟用配接器之間的追蹤[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，並收集任何相關的詳細資訊，發出您的 SQL Server 在使用時遇到[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需有關追蹤中的支援[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 診斷追蹤和訊息記錄中的 SQL 配接器](../../adapters-and-accelerators/adapter-sql/diagnostic-tracing-and-message-logging-in-the-sql-adapter.md)。  
  
## <a name="known-issues"></a>已知問題  
 以下是最常見的錯誤時使用，可能會遇到[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，以及其可能的原因和解決方式。  
  
  
  
###  <a name="BKMK_SQLLoadBinding"></a> 載入配接器繫結時發生錯誤  
 **問題**  
  
 當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，您會收到下列錯誤：  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **原因**  
  
 當您嘗試啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，WCF 會載入所有已安裝的配接器的配接器繫結。 接著，配接器繫結均依存於企業應用程式特定的用戶端軟體。 如果您未安裝中包含的所有配接器的配接器的一般或完整安裝，可能會面臨此問題[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 不過，只有一個企業應用程式可能會安裝 LOB 用戶端程式庫。 如此一來，GUI 無法載入其他配接器的繫結。  
  
 **解決方式**  
  
 請確定您執行自訂安裝來安裝您所需要的介面卡的介面卡。  
  
###  <a name="BKMK_SQLDisplay"></a> SQL 配接器不會顯示在清單中，BizTalk Server 管理主控台中的配接器  
 **問題**  
  
 與舊版隨附的配接器的不同[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，則[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]不會顯示在清單中的配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 **原因**  
  
 最新[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是 WCF 自訂繫結。 因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結，因此，不會顯示以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
 **解決方式**  
  
 您可以明確加入[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]要[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[加入 BizTalk Server 管理主控台中的 SQL 配接器](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。  
  
###  <a name="BKMK_MissingAction"></a> 在 SQL Server 資料庫上執行作業時發生錯誤  
 **問題**  
  
 執行 SQL Server 資料庫使用的任何作業時，配接器會提供下列錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
- **BizTalk server**  
  
  ```  
  System.ArgumentNullException: Value cannot be null.  
  ```  
  
  **原因**  
  
  未指定訊息的 WCF 動作。 WCF 會需要為每個作業，因為它會通知配接器要在 LOB 應用程式上執行的作業指定的 SOAP 動作。  
  
  **解決方式**  
  
  指定的 SOAP 動作，傳送埠中或在 BizTalk 協調流程中的訊息內容屬性。 如需相關指示，請參閱 <<c0> [ 設定 SQL 配接器的 SOAP 動作](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)。 請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)以查看每個作業的動作清單。  
  
###  <a name="BKMK_SQLInvalidOp"></a> 錯誤碼 InvalidOperationException 執行 FILESTREAM 操作時 = 5  
 **問題**  
  
 在使用時收到下列錯誤[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]用於執行 FILESTREAM 操作。  
  
```  
System.InvalidOperationException: OpenSqlFileStream returned error.  
ErrorCode:5  
  
```  
  
 **原因**  
  
 您可能已指定連接到 SQL Server 資料庫的資料庫認證。 若要用於執行 FILESTREAM 操作，您必須一律使用 Windows 驗證。 錯誤碼"5"代表拒絕存取時，是因為不正確的認證。 如需有關不同的錯誤碼的詳細資訊，請參閱[System Error Codes (0-499)](https://msdn.microsoft.com/library/ms681382(VS.85).aspx)。
  
 **解決方式**  
  
 您可以使用 Windows 驗證來連接到 SQL Server 資料庫。 在 [[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，則可以藉由將使用者名稱和密碼欄位留為空白 WCF 自訂] 或 [WCF-SQL 連接埠組態] 對話方塊中。  
  
###  <a name="BKMK_SQLPolling"></a> 輪詢作業不會傳回任何訊息即使 PollingStatement 和 PolledDataAvailableStatement 指定有效的陳述式  
 **問題**  
  
 即使 PollingStatement 和 PolledDataAvailableStatement 繫結屬性已指定有效的值，配接器不會不會收到 SQL Server 的輪詢訊息。  
  
 **原因**  
  
 請確認其他交易是否已在輪詢配接器在資料表上取得鎖定。  
  
 **解決方式**  
  
 如果您想要輪詢的資料表，更新為另一個交易的一部分，您可以考慮 PolledDataAvailableStatement 繫結屬性的指定查詢的過程中使用"with (nolock) 」 參數，以確保即使鎖定會加諸，就會傳回資料另一個交易。 如需詳細資訊，請參閱 < [Database Engine 中鎖定 SQL](https://msdn.microsoft.com/library/ms190615.aspx)。
  
###  <a name="BKMK_SQLSingleOp"></a> 配接器無法插入、 更新或刪除大量資料，在單一作業中使用 BizTalk Server  
 **問題**  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]無法插入、 更新或刪除大量資料，在單一作業中使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 **原因**  
  
 插入、 更新或刪除大量資料可能需要時間和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]或的交易在所執行的作業，可能會逾時。  
  
 **解決方式**  
  
- **BizTalk server**  
  
  1. 在 machine.config 中指定的 WCF 配接器的逾時。瀏覽至 machine.config 檔名\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG 並新增如下所示的摘要。  
  
     ```  
     <configuration>  
      <system.transactions>  
       <machineSettings maxTimeout="02:00:00" />  
      </system.transactions>  
     </configuration>  
     ```  
  
      使用此設定，WCF 配接器逾時是設定為 2 小時。  
  
  2. 在 machine.config 中指定的逾時設定 MSDTC 交易。瀏覽至 machine.config 檔名\<系統磁碟機\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG 並新增如下所示的摘要。  
  
     ```  
     <system.transactions>   
             <defaultSettings distributedTransactionManagerName="<computer_name>" timeout="02:00:00"/>   
         </system.transactions>  
  
     ```  
  
      使用此設定時，MSDTC 逾時設為 2 小時。 MSDTC 逾時的預設值為 10 分鐘。  
  
     > [!IMPORTANT]
     >  您必須執行的配接器用戶端和 SQL Server 的電腦上進行這項變更。 在摘要中，取代執行 SQL Server 與配接器用戶端電腦的名稱為 < 電腦名稱 >。  
  
  3. 設定**SendTimeout**繫結屬性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]相當大的值。 如需有關如何設定繫結屬性的指示，請參閱 <<c0> [ 設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
###  <a name="BKMK_SQLFullSchemaValidate"></a> 包含資料集的回應訊息的 BizTalk Server 中的完整的結構描述驗證會失敗  
 **問題**  
  
 完整的結構描述驗證失敗中作業所傳回的回應訊息，其中包含的資料集，例如 ExecuteReader [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 **解決方式**  
  
 我們建議您執行完整的結構描述驗證，其中包含資料集的回應訊息。 相反地，您可以執行下列作業：  
  
1.  之後，傳回回應訊息的結構描述，請執行此作業。  
  
2.  從回應訊息的結構描述複製到.xsd 檔案，並將這個檔案加入您的 BizTalk 專案。  
  
3.  使用協調流程中的 xpath 查詢，以擷取回應訊息中的資料。  
  
###  <a name="BKMK_SQLRootNode"></a> 在 BizTalk 專案中的根節點類型名稱錯誤  
 **問題**  
  
 在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **解決方式**  
  
1.  以滑鼠右鍵按一下參考錯誤，然後選取 rood 節點**屬性**。  
  
2.  針對**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。  
  
###  <a name="BKMK_SQLMetadataStronglyTyped"></a> 配接器無法產生強型別與暫存資料表的預存程序的中繼資料  
 **問題**  
  
 配接器無法產生強型別的預存程序，在其定義中包含暫存資料表的中繼資料。 配接器會提供下列例外狀況。  
  
```  
Microsoft.ServiceModel.Channels.Common.MetadataException:  
Retrieval of Operation Metadata has failed while building WSDL at 'TypedProcedure/<schema>/<stored_procedure_name>' --->  
System.Data.SqlClient.SqlException: Invalid object name '<temp_table_name>'.  
  
```  
  
 **解決方式**  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]強型別的預存程序包含其定義中的暫存資料表不支援產生的中繼資料。 相反地，您應該在其中產生相同的程序下的中繼資料**程序**時使用的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
###  <a name="BKMK_SQLVS2008"></a> 在 Visual Studio 中使用配接器時，會產生無效的繫結警告。  
 **問題**  
  
 當 Visual Studio 中建立應用程式的情況下，您在使用配接器，並開啟 配接器所產生的組態檔 (app.config) 時，您會看到類似下列的警告：  
  
```  
The element 'bindings' has invalid child element 'sqlBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **原因**  
  
 會出現這個警告，因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結`sqlBinding`，沒有標準繫結隨附[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。  
  
 **解決方式**  
  
 您可以放心地忽略此警告。  
  
###  <a name="BKMK_SQLNotification"></a> 如果您在相同的應用程式中使用一個以上的通知結構描述，或在相同主機上的多個應用程式之間，使用通知結構描述，BizTalk Server 擲回例外狀況  
 **問題**  
  
 XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述符合訊息類型，會擲回 BizTalk Server。  
  
 **原因**  
  
 這是因為下列其中一項：  
  
- 當您產生一個以上的通知結構描述在 BizTalk Server 專案中，將它部署到 BizTalk Server 應用程式，然後執行應用程式以接收通知，從 SQL Server 資料庫。 因為通知結構描述是常見的就會發生衝突之間會部署在 BizTalk Server 應用程式中的結構描述。  
  
- 發生多個專案，方法，您可以有為每個部署的專案，每個專案加入個別的 BizTalk Server 應用程式相同的主機上的 BizTalk Server 產生通知結構描述，並接著執行應用程式或應用程式收到的通知SQL Server 資料庫中。 因為結構描述和組件都是可存取 BizTalk Server 中的應用程式，就會發生衝突之間通用的結構描述部署在各種 BizTalk Server 應用程式和組件。  
  
  **解決方式**  
  
  使用 BizTalk Server 應用程式的單一通知結構描述檔案。 如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用通知結構描述，建立包含單一的通知結構描述中，應用程式，然後使用 BizTalk Server 中的 從其他所有應用程式的通知結構描述。  
  
###  <a name="BKMK_SQLRestoreConn"></a> 配接器用戶端會擲回的例外狀況之後連線已還原配接器用戶端和 SQL Server 資料庫之間執行的作業  
 **問題**  
  
 配接器用戶端會擲回下列例外狀況上執行的 SQL Server 資料庫上的作業：  
  
```  
{System.Data.Common.DbException} = {"A transport-level error has occurred when sending the request to the server. (provider: TCP Provider, error: 0 - An existing connection was forcibly closed by the remote host.)"}  
```  
  
 **原因**  
  
 在執行作業時，配接器會使用 SQL ADO.NET 連接集區連接到 SQL Server 資料庫，並執行作業的連接。 如果配接器用戶端和 SQL Server 資料庫之間的短暫網路中斷，或如果 SQL Server 資料庫已關閉的暫時，SQL ADO.NET 連接集區中的所有連線都會都變成無效。 連線已還原，而且您嘗試執行 SQL Server 資料庫上的作業之後，配接器從 SQL ADO.NET 連接集區中，使用同一個無效的連接，因此配接器用戶端會擲回例外狀況。  
  
 **解決方式**  
  
 配接器用戶端應該實作重試邏輯，在作業執行它們應該在此攔截例外狀況，並指定為"n + 1"的作業重試計數，其中"n"是指定 MaxConnectionPoolSize 繫結屬性的值。 這表示，如果有"n"連接集區中已轉譯不正確的連接數目，理論上配接器用戶端應該重試最多個"n + 1"以取得有效的連接，並因此執行作業的時間。  
  
 例如，若要指定重試計數[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，開啟**屬性**] 對話方塊中的傳送埠的應用程式中，按一下 [**傳輸進階選項**對話方塊中，並在左窗格中**傳輸選項**區域中指定值**重試計數**清單。  
  
###  <a name="BKMK_MemUsage"></a> 記憶體使用量和執行緒計數增加而增加時使用中交易的輸入作業的配接器  
 **問題**  
  
 在交易輸入作業中，輪詢，例如**是否有可用在所輪詢的資料表中的任何資料**和配接器會持續輪詢，經過一段時間中，您遇到增加的記憶體使用量和執行緒計數。  
  
 **原因**  
  
 **如果沒有資料輪詢的資料表中可用**之後，每個接收逾時週期[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]會繁衍新的執行緒，以繼續輪詢作業。 因此，執行緒計數和記憶體使用量會增加一段時間。 不過，如果輪詢的資料表會有一些資料，相同的執行緒會繼續執行所有的後續輪詢。  
  
 **解決方式**  
  
 我們建議您設定**ReceiveTimeout**的最大的可能值，這是 24.20:31:23.6470000 （也就是 24 天），讓新的執行緒會繁衍只能每隔 24 天。 這可確保，記憶體使用量和執行緒計數不會變得太多太快。  
  
> [!NOTE]
>  如果已設定 SqlAdapterInboundTransactionBehavior，請確定 TransactionTimeout 也會設定為 最大可能的值，也就是 24.20:31:23.6470000 （也就是 24 天）。 當使用這個因應措施，我們可以新增 SqlAdapterInboundTransactionBehavior，只有當交易隔離等級必須設。 否則，就移除該行為的最佳作法。  
  
 如需詳細資訊**ReceiveTimeout**繫結屬性，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需指定繫結屬性的指示，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
> [!NOTE]
>  使用的介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，逾時設定為較大的值不會影響配接器的功能。  
  
## <a name="see-also"></a>另請參閱  
[SQL 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)