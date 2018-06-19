---
title: Oracle E-business Suite 配接器疑難排解操作問題 |Microsoft 文件
description: 常見問題和解決方式 Oracle EBS 配接器在 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 667633e0-055a-418a-ab64-d4f6e6c7a898
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4654e228a4ca86c9d89686f826d57777f2353efd
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010199"
---
# <a name="troubleshoot-operational-issues-with-the-oracle-e-business-suite-adapter"></a>Oracle E-business Suite 配接器疑難排解操作問題
本章節將討論使用來解析作業使用時可能遭遇的錯誤的疑難排解技術[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。  
  
## <a name="enabling-tracing"></a>啟用追蹤  
 如需有關追蹤中的支援[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，[診斷追蹤和訊息記錄在 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/diagnostic-tracing-and-message-logging-in-the-oracle-e-business-suite-adapter.md)。  
  
## <a name="known-issues"></a>已知問題  
 以下是最常見的錯誤時使用，可能會遇到[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]、 以及它們的可能原因和解決方式。  
  
  
  
###  <a name="BKMK_LoadBindings"></a>載入配接器繫結時發生錯誤  
 **問題**  
  
 當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，收到下列錯誤：  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **可能的原因**  
  
 當您嘗試啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，WCF 會載入所有已安裝的配接器的配接器繫結。 接著，配接器繫結會相依於企業應用程式的特定用戶端軟體。 您可能會面臨這個問題的一個或兩個原因如下：  
  
-   將介面卡安裝在電腦上未安裝必要的 LOB 用戶端軟體。  
  
-   未安裝中所包含的所有配接器的配接器的一般或完整安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 不過，只有一個企業應用程式可能會安裝 LOB 用戶端程式庫。 如此一來，GUI 無法載入其他配接器的繫結。  
  
 **解決方式**  
  
-   請確定所需的 LOB 用戶端版本已安裝在您安裝的電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 支援的用戶端版本的相關資訊，請參閱安裝指南位於\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。  
  
-   請確定您執行自訂安裝的配接器安裝您所需要的介面卡。  
  
###  <a name="BKMK_Display"></a>Oracle E-business Suite 配接器不會顯示在 BizTalk Server 管理主控台中的配接器清單  
 **問題**  
  
 與舊版隨附的配接器的不同[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]、[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]不會顯示在清單中的配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 **可能的原因**  
  
 最新[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]是 WCF 自訂繫結。 因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結而因此，不會顯示 WCF 基礎[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
 **解決方式**  
  
 您可以明確加入[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[將 Oracle E-business Suite 介面卡新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)。  
  
###  <a name="BKMK_MissingAction"></a>執行 Oracle E-business suite 作業時發生錯誤  
 **問題**  
  
 執行 Oracle E-business Suite 使用中的任何作業時，配接器會提供下列的錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
-   **BizTalk server**  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 **可能的原因**  
  
 未指定訊息的 WCF 動作。 WCF 需要針對每個作業，在 LOB 應用程式上執行作業的相關通知配接器指定的 SOAP 動作。  
  
 **解決方式**  
  
 指定的 SOAP 動作，在傳送埠或 BizTalk 協調流程中的訊息內容屬性。 如需指示，請參閱[設定 Oracle E-business Suite 的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md)。 請參閱[訊息和 Oracle EBS 配接器的訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)若要查看每個作業的動作清單。  
  
###  <a name="BKMK_WrongClient"></a>BizTalk 處理序可能會當機因為不正確的 Oracle 用戶端版本時的要求訊息的接收位置在卸除  
 **問題**  
  
 BizTalk 協調流程中定義的接收位置在卸除要求訊息之後，協調流程取用訊息，BizTalk 主控件 (BTSNTSvc.exe) 損毀並重新啟動。  
  
 **可能的原因**  
  
 安裝 Oracle 用戶端會將最新的用戶端組件參考加入 PATH 變數中。 此外，最新安裝的 Oracle 用戶端組件參考現有的用戶端組件參考之前。 因此，如果最新的 Oracle 用戶端安裝，不支援的用戶端版本的 BizTalk 主控件損毀，然後重新啟動。  
  
 例如，假設已在電腦上安裝支援的 Oracle 用戶端 11.1.0.7，PATH 變數具有下列參考：  
  
```  
C:\oracle\product\11.1.0\client_1\bin;  
```  
  
 如果同一部電腦上安裝不支援的 Oracle 用戶端，例如 10.2.0.3，PATH 變數會有下列參考：  
  
```  
C:\oracle\product\10.2.0\db_2\bin;C:\oracle\product\11.1.0\client_1\bin;  
```  
  
 請注意，不支援用戶端參考的版本是支援的版本之前，因此 BizTalk 主控件的當機。 如果有多個執行的 BizTalk 主控件，裝載配接器的一個損毀。  
  
 **解決方式**  
  
 如果同一部電腦上安裝一個以上的 Oracle 用戶端，請確定參考之前 PATH 變數中的其他 Oracle 用戶端版本支援的 Oracle 用戶端版本。 例如，如果 11.1.0.7 支援的 Oracle 用戶端版本，PATH 變數中的參考必須如下：  
  
```  
  
C:\oracle\product\11.1.0\client_1\bin;C:\oracle\product\10.2.0\db_2\bin;  
```  
  
###  <a name="BKMK_Overflow"></a>配接器可能會擲回於執行作業的溢位例外狀況  
 **問題**  
  
 如果您嘗試執行包含在資料集或弱式類型的 REF CURSOR 的 Oracle 數值資料類型的作業，請使用配接器，配接器可能會發生溢位例外狀況。  
  
 **可能的原因**  
  
 會發生這種情況是如果您提供的 Oracle 數值資料類型，在資料集或弱式類型的 REF CURSOR 無法放入個別的.NET 型別之較大的值。  
  
 **解決方式**  
  
 如果您想要傳遞的資料集或弱式類型的 REF CURSOR 內 Oracle 數值資料類型的較大的值，您必須啟用 「 安全輸入的值設定**EnableSafeTyping**內容繫結至**true**. 啟用 「 安全輸入字串的形式公開在資料集或弱式類型的 REF CURSOR 的 Oracle 數值資料類型。  
  
###  <a name="BKMK_Arithmetic"></a>配接器可能會擲回於執行 ExecuteScalar 作業算術溢位例外狀況  
 **問題**  
  
 使用配接器，如果您嘗試執行 SELECT 陳述式中擷取大量的 ExecuteScalar 作業，配接器會擲回下列例外狀況:"System.OverflowException： 數學運算導致溢位。 」  
  
 **可能的原因**  
  
 這是因為 ODP.NET ExecuteScalar 作業的已知限制。 ODP.NET 會盡量配合.NET 十進位資料類型，將資料中，如果結果太大，無法納入.NET Decimal 型別，擲回例外狀況。  
  
 **解決方式**  
  
 在 ExecuteScalar 作業中的 SELECT 陳述式中使用 TO_CHAR() 轉換以字串形式傳回的資料。  
  
###  <a name="BKMK_AppContext"></a>配接器用戶端可能會擲回下列例外狀況上執行作業: 「 無法擷取使用者識別碼、 責任識別碼、 應用程式識別碼。檢查是否已傳遞正確的值。 」  
 **問題**  
  
 如果您正在執行 Oracle E-business Suite 成品 （介面資料表、 檢視介面、 並行程式和要求） 上的作業，配接器用戶端可能會擲回這個例外狀況。  
  
 **可能的原因**  
  
 會發生這種情況是如果您提供的 Oracle 使用者名稱、 密碼和責任名稱執行介面資料表、 介面檢視、 並行程式，以及要求的作業時使用不正確組合。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]需要這些值，才能設定這些成品的應用程式內容。 如需有關設定應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
 **解決方式**  
  
 您必須指定正確的 Oracle 使用者名稱、 密碼和責任來適當地設定 Oracle E-business Suite 成品的應用程式內容的組合。 若要指定 Oracle 使用者名稱和密碼的值，您必須使用**OracleUserName**和**OraclePassword**繫結屬性。 若要指定 Oracle 責任的值，您可以使用**OracleEBSResponsibilityName**繫結屬性或訊息內容屬性。  
  
###  <a name="BKMK_RootNode"></a>RootNode TypeName 在 BizTalk 專案中的錯誤  
 **問題**  
  
 在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字的**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **解決方式**  
  
1.  以滑鼠右鍵按一下錯誤，然後選取所參照的 rood 節點**屬性**。  
  
2.  如**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。  
  
###  <a name="BKMK_InvalidBinding"></a>在 Visual Studio 中使用配接器時，無效的繫結警告  
 **問題**  
  
 當您建立的應用程式中使用配接器[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]並開啟配接器所產生的組態檔 (app.config)，您會看到類似下列的警告：  
  
```  
The element 'bindings' has invalid child element 'oracleEBSBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **可能的原因**  
  
 會出現這個警告，因為[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結， `oracleEBSBinding`，不標準繫結隨附於[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。  
  
 **解決方式**  
  
 您可以放心地忽略此警告。  
  
###  <a name="BKMK_Notify"></a>如果您使用一個以上的通知結構描述中相同的應用程式或跨多個相同的主機上的應用程式使用通知結構描述，BizTalk Server 擲回例外狀況  
 **問題**  
  
 XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述比對訊息類型，會擲回 BizTalk Server。  
  
 **可能的原因**  
  
 這是因為下列其中一項：  
  
-   產生一個以上的通知結構描述在 BizTalk Server 專案中，部署至 BizTalk Server 應用程式，然後執行應用程式要從 Oracle 資料庫接收通知。 因為通知結構描述是常見的就會發生衝突的 BizTalk Server 應用程式以部署的結構描述之間。  
  
-   發生多個專案，通知結構描述產生的每個 BizTalk 伺服器，每個專案加入相同主機上，個別的 BizTalk Server 應用程式部署的專案，然後執行應用程式或應用程式收到的通知Oracle 資料庫中。 因為結構描述和組件都可存取 BizTalk Server 中的應用程式，就會發生衝突之間常見的結構描述部署在不同的 BizTalk Server 應用程式和組件。  
  
 **解決方式**  
  
 BizTalk Server 應用程式使用單一的通知結構描述檔案。 如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用通知結構描述，建立包含單一通知結構描述時，應用程式，然後再使用 BizTalk Server 中的 從所有其他應用程式的通知結構描述。  
  
###  <a name="BKMK_Timeout"></a>在瀏覽 Visual Studio 中的 Oracle E-business Suite 成品時的逾時例外狀況  
 **問題**  
  
 在瀏覽 Oracle E-business Suite 中的成品時[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]， [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]可能會遇到逾時例外狀況。  
  
 **可能的原因**  
  
 如果裝載 Oracle E-business Suite 的伺服器變慢、 伺服器位於遠端位置，或想要在結構描述有大量的成品，就可能發生這個情形。  
  
 **解決方式**  
  
 您可以選擇增加的值**SendTimeout**內容繫結或搜尋在提供的運算式**類別目錄中的搜尋**文字方塊中，以減少的成品，配接器擷取。  
  
 如需指定繫結屬性的詳細資訊，請參閱[for Oracle E-business Suite 中設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。 如需搜尋 Oracle E-business Suite 中的成品的詳細資訊，請參閱[瀏覽、 搜尋和 Oracle E-business Suite 作業的 get 中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
###  <a name="BKMK_MemUsage"></a>記憶體使用量和執行緒計數則會增加交易的輸入作業中使用配接器時  
 **問題**  
  
 在交易輸入作業中，例如輪詢，**是否有可用輪詢資料表中的任何資料**和配接器會持續輪詢，經過一段時間，您遇到的增加記憶體使用量和執行緒計數。  
  
 **可能的原因**  
  
 **如果沒有資料輪詢的資料表中可用**，之後每個接收逾時週期[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]需要產生新的執行緒，以繼續輪詢作業。 因此，執行緒計數和記憶體使用量會增加經過一段時間。 不過，如果資料表輪詢有一些資料，在相同的執行緒會繼續執行所有後續輪詢。  
  
 **解決方式**  
  
 我們建議您設定**ReceiveTimeout**的最大的可能值，這是 24.20:31:23.6470000 （24 天），讓新的執行緒未繁衍只能每隔 24 天。 這可確保，記憶體使用量和執行緒計數不會成長得太多太快。  
  
 如需有關**ReceiveTimeout**繫結屬性，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需指定繫結屬性的指示，請參閱[for Oracle E-business Suite 中設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。  
  
> [!NOTE]
>  使用與配接器時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，將逾時設定為較大的值不會影響配接器的功能。  
  
## <a name="see-also"></a>請參閱  
[Oracle EBS 配接器疑難排解](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)