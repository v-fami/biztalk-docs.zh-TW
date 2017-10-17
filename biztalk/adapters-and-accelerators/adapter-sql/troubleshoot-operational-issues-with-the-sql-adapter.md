---
title: "在 BizTalk SQL 配接器疑難排解操作問題 |Microsoft 文件"
description: "常見問題和解決方法，SQL 配接器在 BizTalk 配接器組件 (BAP)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c75f85f4-cd03-4c6a-aac9-a6d02d3c3449
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82bfb1782c6bccdafe4f69326cddff0f49974386
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="troubleshoot-operational-issues-with-the-sql-adapter"></a>SQL 配接器疑難排解操作問題
本章節將討論使用來解析作業使用時可能遭遇的錯誤的疑難排解技術[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]。  
  
## <a name="enabling-tracing"></a>啟用追蹤  
 您必須啟用配接器之間的追蹤[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，並使用時所遇到的 SQL Server 來收集更多資訊的相關問題[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需有關追蹤中的支援[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[診斷追蹤和訊息記錄在 SQL 配接器](../../adapters-and-accelerators/adapter-sql/diagnostic-tracing-and-message-logging-in-the-sql-adapter.md)。  
  
## <a name="known-issues"></a>已知問題  
 以下是最常見的錯誤時使用，可能會遇到[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]、 以及它們的可能原因和解決方式。  
  
  
  
###  <a name="BKMK_SQLLoadBinding"></a>載入配接器繫結時發生錯誤  
 **問題**  
  
 當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，收到下列錯誤：  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **可能的原因**  
  
 當您嘗試啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，WCF 會載入所有已安裝的配接器的配接器繫結。 接著，配接器繫結會相依於企業應用程式的特定用戶端軟體。 如果您未安裝中所包含的所有配接器的配接器的一般或完整安裝，您可能會面臨這個問題[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 不過，只有一個企業應用程式可能會安裝 LOB 用戶端程式庫。 如此一來，GUI 無法載入其他配接器的繫結。  
  
 **解決方式**  
  
 請確定您執行自訂安裝的配接器安裝您所需要的介面卡。  
  
###  <a name="BKMK_SQLDisplay"></a>SQL 配接器不會顯示在 BizTalk Server 管理主控台中的配接器清單  
 **問題**  
  
 與舊版隨附的配接器的不同[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]、[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]不會顯示在清單中的配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 **可能的原因**  
  
 最新[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]是 WCF 自訂繫結。 因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結而因此，不會顯示 WCF 基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
 **解決方式**  
  
 您可以明確加入[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[SQL 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)。  
  
###  <a name="BKMK_MissingAction"></a>執行 SQL Server 資料庫上的作業時發生錯誤  
 **問題**  
  
 執行 SQL Server 資料庫使用中的任何作業時，配接器會提供下列的錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
-   **針對[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 **可能的原因**  
  
 未指定訊息的 WCF 動作。 WCF 需要針對每個作業，在 LOB 應用程式上執行作業的相關通知配接器指定的 SOAP 動作。  
  
 **解決方式**  
  
 指定的 SOAP 動作，在傳送埠或 BizTalk 協調流程中的訊息內容屬性。 如需指示，請參閱[設定 SQL 配接器的 SOAP 動作](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)。 請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)若要查看每個作業的動作清單。  
  
###  <a name="BKMK_SQLInvalidOp"></a>InvalidOperationException ErrorCode 與執行 FILESTREAM 操作時 = 5  
 **問題**  
  
 使用時收到下列錯誤[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]用於執行 FILESTREAM 操作。  
  
```  
System.InvalidOperationException: OpenSqlFileStream returned error.  
ErrorCode:5  
  
```  
  
 **可能的原因**  
  
 您可能會指定要連接到 SQL Server 資料庫的資料庫認證。 若要用於執行 FILESTREAM 操作，您必須一律使用 Windows 驗證。 錯誤碼"5"代表拒絕存取時，是因為不正確的認證。 如需不同錯誤碼的詳細資訊，請參閱[系統錯誤碼 (0-499)](https://msdn.microsoft.com/library/ms681382(VS.85).aspx)。
  
 **解決方式**  
  
 您可以使用 Windows 驗證來連接到 SQL Server 資料庫。 在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以透過將使用者名稱和密碼欄位保留空白 Wcf-custom 或 WCF SQL 連接埠組態 對話方塊中。  
  
###  <a name="BKMK_SQLPolling"></a>輪詢作業不會傳回任何訊息即使 PollingStatement 和 PolledDataAvailableStatement 指定了有效的陳述式  
 **問題**  
  
 即使 PollingStatement 和 PolledDataAvailableStatement 繫結屬性指定有效值，則配接器沒有從 SQL Server 收到輪詢訊息。  
  
 **可能的原因**  
  
 請確認其他交易是否已正在輪詢配接器在資料表上取得鎖定。  
  
 **解決方式**  
  
 如果您想要輪詢的資料表，正在更新做為另一個交易的一部分，您可以考慮 PolledDataAvailableStatement 繫結屬性中指定的查詢的一部分使用"with (nolock) 」 參數，以確保即使鎖定會加諸，就會傳回資料另一個交易。 如需詳細資訊，請參閱[Database Engine 中鎖定 SQL](https://msdn.microsoft.com/library/ms190615.aspx)。
  
###  <a name="BKMK_SQLSingleOp"></a>配接器無法插入、 更新或刪除大量使用 BizTalk Server 在單一作業中的資料  
 **問題**  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]無法插入、 更新或刪除大量資料，在單一作業中使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 **可能的原因**  
  
 插入、 更新或刪除大量資料可能會花時間和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]或的交易中正在執行的作業，可能會逾時。  
  
 **解決方式**  
  
-   **針對[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**  
  
    1.  在 machine.config 中指定的 WCF 配接器的逾時。瀏覽至 machine.config 檔名\<系統磁碟機 >: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG 並加入類似如下所示的摘要。  
  
        ```  
        <configuration>  
         \<system.transactions>  
          <machineSettings maxTimeout="02:00:00" />  
         \</system.transactions>  
        </configuration>  
        ```  
  
         使用此設定時，WCF 配接器逾時設為 2 小時。  
  
    2.  在 machine.config 中指定 MSDTC 交易的逾時的設定。瀏覽至 machine.config 檔名\<系統磁碟機 >: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG 並加入類似如下所示的摘要。  
  
        ```  
        \<system.transactions>   
                <defaultSettings distributedTransactionManagerName="<computer_name>" timeout="02:00:00"/>   
            \</system.transactions>  
  
        ```  
  
         使用此設定時，MSDTC 逾時設為 2 小時。 MSDTC 逾時的預設值是 10 分鐘。  
  
        > [!IMPORTANT]
        >  您必須執行的配接器用戶端和 SQL Server 的電腦上進行這項變更。 在摘錄中，以執行配接器用戶端和 SQL Server 的電腦名稱取代 < 電腦名稱 >。  
  
    3.  設定**SendTimeout**繫結屬性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]相當大的值。 如需有關如何設定繫結屬性的指示，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
###  <a name="BKMK_SQLFullSchemaValidate"></a>在 BizTalk Server 中的完整結構描述驗證失敗之回應訊息包含資料集  
 **問題**  
  
 傳回回應訊息包含的資料集，例如 ExecuteReader 作業的完整結構描述驗證失敗[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
 **解決方式**  
  
 我們建議您不會包含資料集的回應訊息的完整結構描述驗證。 相反地，您可以執行下列動作：  
  
1.  一旦傳回回應訊息的結構描述，請執行作業。  
  
2.  從回應訊息的結構描述複製到.xsd 檔案，並將這個檔案加入您的 BizTalk 專案。  
  
3.  在您的協調流程會使用 xpath 查詢從回應訊息中擷取資料。  
  
###  <a name="BKMK_SQLRootNode"></a>RootNode TypeName 在 BizTalk 專案中的錯誤  
 **問題**  
  
 在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字的**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **解決方式**  
  
1.  以滑鼠右鍵按一下錯誤，然後選取所參照的 rood 節點**屬性**。  
  
2.  如**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。  
  
###  <a name="BKMK_SQLMetadataStronglyTyped"></a>配接器無法產生強型別與暫存資料表的預存程序的中繼資料  
 **問題**  
  
 配接器無法產生強型別的預存程序，其定義中包含暫存資料表的中繼資料。 配接器會提供下列例外狀況。  
  
```  
Microsoft.ServiceModel.Channels.Common.MetadataException:  
Retrieval of Operation Metadata has failed while building WSDL at 'TypedProcedure/<schema>/<stored_procedure_name>' --->  
System.Data.SqlClient.SqlException: Invalid object name '<temp_table_name>'.  
  
```  
  
 **解決方式**  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]強型別的預存程序包含其定義中的暫存資料表不支援產生的中繼資料。 相反地，您應該產生中繼資料相同的程序，從下**程序**時使用的節點[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
###  <a name="BKMK_SQLVS2008"></a>在 Visual Studio 中使用配接器時，無效的繫結警告  
 **問題**  
  
 當您使用 Visual Studio 中建立的應用程式的配接器，並開啟配接器所產生的組態檔 (app.config) 時，您會看到類似下列的警告：  
  
```  
The element 'bindings' has invalid child element 'sqlBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **可能的原因**  
  
 會出現這個警告，因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結， `sqlBinding`，不標準繫結隨附於[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。  
  
 **解決方式**  
  
 您可以放心地忽略此警告。  
  
###  <a name="BKMK_SQLNotification"></a>如果您使用一個以上的通知結構描述中相同的應用程式或跨多個相同的主機上的應用程式使用通知結構描述，BizTalk Server 擲回例外狀況  
 **問題**  
  
 XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述比對訊息類型，會擲回 BizTalk Server。  
  
 **可能的原因**  
  
 這是因為下列其中一項：  
  
-   產生一個以上的通知結構描述在 BizTalk Server 專案中，部署至 BizTalk Server 應用程式，，然後執行應用程式要從 SQL Server 資料庫接收通知。 因為通知結構描述是常見的就會發生衝突的 BizTalk Server 應用程式以部署的結構描述之間。  
  
-   發生多個專案，通知結構描述產生的每個 BizTalk 伺服器，每個專案加入相同主機上，個別的 BizTalk Server 應用程式部署的專案，然後執行應用程式或應用程式收到的通知SQL Server 資料庫。 因為結構描述和組件都可存取 BizTalk Server 中的應用程式，就會發生衝突之間常見的結構描述部署在不同的 BizTalk Server 應用程式和組件。  
  
 **解決方式**  
  
 BizTalk Server 應用程式使用單一的通知結構描述檔案。 如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用通知結構描述，建立包含單一通知結構描述時，應用程式，然後再使用 BizTalk Server 中的 從所有其他應用程式的通知結構描述。  
  
###  <a name="BKMK_SQLRestoreConn"></a>配接器用戶端擲回例外狀況在連線恢復配接器用戶端之間的 SQL Server 資料庫後執行的作業  
 **問題**  
  
 配接器用戶端擲回下列例外狀況，在執行 SQL Server 資料庫上的作業：  
  
```  
{System.Data.Common.DbException} = {"A transport-level error has occurred when sending the request to the server. (provider: TCP Provider, error: 0 - An existing connection was forcibly closed by the remote host.)"}  
```  
  
 **可能的原因**  
  
 在執行作業時，配接器會使用連線連接到 SQL Server 資料庫，並執行作業，SQL ADO.NET 連接集區。 如果配接器用戶端和 SQL Server 資料庫之間在短暫的網路中斷，或如果 SQL Server 資料庫已關閉的暫時，SQL ADO.NET 連接集區中的所有連線都會都變成無效。 連線已還原，而且您嘗試執行 SQL Server 資料庫上的作業之後，配接器使用相同的無效連接從 SQL ADO.NET 連接集區，因此配接器用戶端擲回例外狀況。  
  
 **解決方式**  
  
 配接器用戶端應該實作重試邏輯，其作業執行，它們應該在此攔截例外狀況，並指定為"n + 1"的作業重試計數，其中"n"是指定 MaxConnectionPoolSize 繫結屬性的值。 這表示，有"n"連接集區中有已呈現正確的連接數目，如果理論上配接器用戶端應該重試的最大值為"n + 1"以取得有效的連接，並因此執行作業的時間。  
  
 例如，若要指定重試計數[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，開啟**屬性**對話方塊的 傳送埠的應用程式中，按一下 **傳輸進階選項**對話方塊中，然後在左窗格中**傳輸選項**區域中，指定的值**重試計數**清單。  
  
###  <a name="BKMK_MemUsage"></a>記憶體使用量和執行緒計數則會增加交易的輸入作業中使用配接器時  
 **問題**  
  
 在交易輸入作業中，例如輪詢，**是否有可用輪詢資料表中的任何資料**和配接器會持續輪詢，經過一段時間，您遇到的增加記憶體使用量和執行緒計數。  
  
 **可能的原因**  
  
 **如果沒有資料輪詢的資料表中可用**，之後每個接收逾時週期[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]需要產生新的執行緒，以繼續輪詢作業。 因此，執行緒計數和記憶體使用量會增加經過一段時間。 不過，如果資料表輪詢有一些資料，在相同的執行緒會繼續執行所有後續輪詢。  
  
 **解決方式**  
  
 我們建議您設定**ReceiveTimeout**的最大的可能值，這是 24.20:31:23.6470000 （24 天），讓新的執行緒未繁衍只能每隔 24 天。 這可確保，記憶體使用量和執行緒計數不會成長得太多太快。  
  
> [!NOTE]
>  如果已設定 SqlAdapterInboundTransactionBehavior，請確定 TransactionTimeout 同時設定為最大可能的值，這是 24.20:31:23.6470000 （24 天）。 當使用這個因應措施，我們可以加入 SqlAdapterInboundTransactionBehavior 才必須設定交易隔離等級。 否則，就移除該行為的最佳作法。  
  
 如需有關**ReceiveTimeout**繫結屬性，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需指定繫結屬性的指示，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
> [!NOTE]
>  使用與配接器時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，將逾時設定為較大的值不會影響配接器的功能。  
  
## <a name="see-also"></a>另請參閱  
[SQL 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)