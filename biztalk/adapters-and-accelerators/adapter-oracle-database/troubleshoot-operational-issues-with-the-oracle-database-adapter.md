---
title: "疑難排解與 Oracle 資料庫配接器的操作問題 |Microsoft 文件"
description: "常見的問題與 Oracle 資料庫配接器在 BizTalk 配接器組件 (BAP) 中的解決方案"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fb83245-2b6a-48cc-8601-b923bb009a58
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1de0198d26f804ee8d1974d5dd542387408ea53a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-operational-issues-with-the-oracle-database-adapter"></a>疑難排解與 Oracle 資料庫配接器的操作問題
疑難排解技術來解決您可能會使用的作業錯誤[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。  
  
## <a name="enable-tracing"></a>啟用追蹤  
 如需有關追蹤中的支援資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[診斷追蹤和 Oracle 資料庫配接器的訊息記錄](../../adapters-and-accelerators/adapter-oracle-database/diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter.md)。  
  
## <a name="known-issues"></a>已知問題  
 以下是最常見的錯誤時使用，可能會遇到[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]、 以及它們的可能原因和解決方式。   
  
### <a name="BKMK_OraDBLoading"></a>載入配接器繫結時發生錯誤  
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
  
-   請確定所需的 LOB 用戶端版本已安裝在您安裝的電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 [支援的特定業務 (LOB) 和企業系統](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出支援的用戶端版本。  
  
-   請確定您執行自訂安裝的配接器安裝您所需要的介面卡。  
  
    > [!NOTE]
    >  若要確定您的應用程式的運作方式與 ODP.NET 的最新版本，您必須使用"原則 DLLs"的電腦上安裝並註冊在 GAC 中。 如需詳細資訊，請參閱[適用於.NET 的 Oracle 資料提供者](http://go.microsoft.com/fwlink/p/?LinkId=92834)Oracle 的網站上。  
  
###  <a name="BKMK_OraDBAdapDisplay"></a>Oracle 資料庫配接器不會顯示在 BizTalk Server 管理主控台中的配接器清單  
 **問題**  
  
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]所含與[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]未列在 BizTalk Server 管理主控台中的配接器清單。  
  
 **可能的原因**  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]是 WCF 自訂繫結。 因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結而因此，不會顯示 WCF 基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 **解決方式**  
  
 您可以明確加入[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。  
  
###  <a name="BKMK_OraDBXMLRetrieve"></a>擷取具有超過 65536 節點的 XML 輸出時發生錯誤  
 **問題**  
  
 擷取 XML 輸出，已超過 65536 的節點時，配接器會提供下列的錯誤。  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 **可能的原因**  
  
 配接器無法進行序列化和還原序列化物件，超過 65536 個項目。  
  
 **解決方式**  
  
 您可以設定來修正此問題`maxItemsInObjectGraph`參數。 您可以將它設定在下列兩種方法之一：  
  
-   設定此參數，藉由變更`maxItemsInObjectGraph`中的參數`ServiceBehavior`服務類別上的屬性。  
  
-   將下列加入至您的應用程式的 app.config 檔案。  
  
    ```  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
          <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
 範例 app.config 看起來像這樣。  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  \<system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="NewBehavior">  
         <dataContractSerializer maxItemsInObjectGraph="65536000" />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <client>  
      <endpoint   behaviorConfiguration="NewBehavior" binding="oracleDBBinding"  
       contract="IOutboundContract" name="oracle_ICalculator" />  
    </client>  
  \</system.serviceModel>  
</configuration>  
```  
  
###  <a name="BKMK_OraDBPerfOps"></a>在 Oracle 資料庫上執行作業時發生錯誤  
 **問題**  
  
 執行 Oracle 資料庫使用中的任何作業時，配接器會產生下列錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
-   **針對[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]**  
  
    ```  
    System.ArgumentNullException: Value cannot be null.  
    ```  
  
 **可能的原因**  
  
 未指定訊息的 WCF 動作。 WCF 需要針對每個作業，在 LOB 應用程式上執行作業的相關通知配接器指定的 SOAP 動作。  
  
 **解決方式**  
  
 指定的 SOAP 動作，在傳送埠或 BizTalk 協調流程中的訊息內容屬性。 如需指示，請參閱[設定 Oracle 資料庫的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md)。 請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)若要查看每個作業的動作清單。  
  
###  <a name="BKMK_OraDBXmlParsing"></a>XmlReaderParsingException 由於作業名稱中指定的動作  
 **問題**  
  
 傳送訊息到 Oracle 資料庫時，BizTalk Server 管理主控台就會產生下列錯誤：  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 **可能的原因**  
  
 如果您匯入所建立的連接埠繫結檔來設定 WCF 自訂連接埠[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，以下列格式指定連接埠中的動作：  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 在上述格式中，作業名稱係由您產生結構描述時所選擇的作業。 比方說，如果您產生的資料表上的插入作業結構描述，動作中的作業名稱就是 「 插入 」。 不過，在 BizTalk 協調流程中建立的邏輯連接埠中的作業名稱[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可能會不同。  
  
 **解決方式**  
  
 請確定作業名稱在這兩個邏輯連接埠 (BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) 和 （在 BizTalk Server 管理主控台） 的實體通訊埠都相同。  
  
###  <a name="BKMK_OraDBConnURI"></a>在 BizTalk 中指定連線 URI WCF 自訂連接埠時發生錯誤  
 **問題**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]當您指定 URI 要連接到 Oracle 資料庫的連接，請提供下列的錯誤。  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 **可能的原因**  
  
 連線 URI 並不依循標準編碼格式。 例如，參數的值可能會包含空格。  
  
 **解決方式**  
  
 請確定您指定的 URI 符合標準的編碼格式的連接。 例如，"%20"必須取代的空白區域。  
  
###  <a name="BKMK_OraDBInvalCursor"></a>無效的資料指標時叫用的 REF CURSOR 參數的預存程序的例外狀況  
 **問題**  
  
 當您叫用的程序的 Oracle 資料庫中 REF CURSOR 的輸入時，您可能會收到下列例外狀況：  
  
```  
Microsoft.ServiceModel.Channels.Common.TargetSystemException: ORA-01001: invalid cursor ---> Oracle.DataAccess.Client.OracleException  
```  
  
 **可能的原因**  
  
 所叫用的程序的 PL/SQL 區塊無法使用 REF 資料指標，也就是在 REF CURSOR 無法取得指派給出 REF CURSOR。  
  
 **解決方式**  
  
 PL/SQL 區塊必須不使用管線傳送出 REF 資料指標而不需要適當的處理。  
  
###  <a name="BKMK_OraDBValidateResp"></a>驗證使用 BizTalk Server ReadLOB 作業的回應時發生錯誤  
 **問題**  
  
 執行 ReadLOB 作業使用時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，從 Oracle 資料庫回應驗證對 Web 服務描述語言 (WSDL) 失敗。  
  
 **可能的原因**  
  
 WSDL 會包含定義為執行的服務為基礎的要求，但不需要使用 BizTalk 案例 StreamBody 節點名稱。 因此，當輸出 XML，不包含 StreamBody 節點，相較於 WSDL，驗證將會失敗。  
  
 **解決方式**  
  
 針對使用 BizTalk Server 產生的輸出進行驗證時，請從 WSDL 移除 StreamBody 節點。 執行下列步驟來執行這項操作：  
  
1.  WSDL 包含 StreamBody 節點看起來像這樣。  
  
    ```  
    \<xs:element name="ReadLOBResponse">  
        \<xs:annotation>  
          \<xs:documentation>  
            \<doc:action xmlns:doc="http://schemas.microsoft.com/servicemodel/adapters/metadata/documentation">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/TBL_ALL_DATATYPES/ReadLOB/response\</doc:action>  
          \</xs:documentation>  
        \</xs:annotation>  
        \<xs:complexType>  
          \<xs:sequence>  
            \<xs:element minOccurs="1" maxOccurs="1" name="ReadLOBResult" nillable="true" type="ns3:StreamBody" />  
          \</xs:sequence>  
        \</xs:complexType>  
      \</xs:element>  
    ```  
  
     取代下列前面。  
  
    ```  
    \<xs:element name="ReadLOBResponse">  
     \<xs:annotation>  
     \<xs:documentation>  
      \<doc:action xmlns:doc="http://schemas.microsoft.com/servicemodel/adapters/metadata/documentation">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/TBL_ALL_DATATYPES/ReadLOB/response\</doc:action>   
      \</xs:documentation>  
      \</xs:annotation>  
     \<xs:complexType>  
     \<xs:sequence>  
      \<xs:element minOccurs="1" maxOccurs="1" name="ReadLOBResult" type="xs:base64Binary" />   
      \</xs:sequence>  
      \</xs:complexType>  
      \</xs:element>  
    ```  
  
     您可以在此步驟中，移除型別參考 ="ns3:StreamBody"原始 XSD 中的並取代類型 ="xs: base64binary"。 此外，您會從原始 XSD 移除 nillable ="true"值。  
  
2.  移除下列從 WSDL。  
  
    ```  
    \<xs:complexType name="StreamBody">  
        \<xs:sequence>  
          \<xs:element minOccurs="1" maxOccurs="1" name="Stream">  
            \<xs:simpleType>  
              \<xs:restriction base="xs:base64Binary">  
                \<xs:minLength value="0" />  
              \</xs:restriction>  
            \</xs:simpleType>  
          \</xs:element>  
        \</xs:sequence>  
      \</xs:complexType>  
      \<xs:element name="StreamBody" nillable="true" type="ns3:StreamBody" />  
    ```  
  
    > [!NOTE]
    >  不支援的作業 ReadLOB [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 您應該用來讀取從 LOB 資料的資料表的 Select 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。  
  
###  <a name="BKMK_OraDBSchemaValidateFail"></a>輪詢案例中的結構描述驗證可能會失敗  
 **問題**  
  
 結構描述驗證失敗案例中，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢資料庫資料表，其中包含 ROWID 或 UNROWID 類型的欄位。  
  
 **可能的原因**  
  
 在設計階段時，配接器會產生中繼資料包含 ROWID 或 UNROWID，類型的欄位的資料表結構描述包含"nillable = false"，這表示 ROWID 或 UNROWID 類型的欄位不可為 null。 不過，在執行階段時，配接器擷取的中繼資料，ROWID 或 UNROWID 類型的欄位包含 null 值。 因此，結構描述驗證會失敗。  
  
 **解決方式**  
  
 如果您使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以選擇停用結構描述驗證。 或者，您可以手動編輯來變更結構描述 」 nillbale = true"ROWID 和 UNROWID 資料類型。  
  
###  <a name="BKMK_OraDBUnreasonConv"></a>做為參數 '要求不合理 conversion' 錯誤時執行預存程記錄類型  
 **可能的原因**  
  
 假設其中 Oracle 預存程序會採用記錄類型做為參數。 假設記錄類型宣告為\<資料表名稱 > %的資料列型別，在資料表有 LONG 資料類型的資料行。 當[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]遇到 LONG 資料類型，它會設定資料類型的大小等於指定的值**LongDatatypeColumnSize**繫結屬性。 不過，Oracle 資料庫並未定義 LONG 資料類型的大小。 因此，當配接器會叫用預存程序，它會導致 '要求不合理 conversion' 錯誤。  
  
 **解決方式**  
  
 如果記錄類型具有 LONG 資料類型，必須明確將其定義為封裝的一部分。  
  
###  <a name="BKMK_OraDBAdapRecognize"></a>配接器無法辨識的實體通訊埠上的動作，即使您使用 取用配接器服務增益集所產生的繫結檔案建立連接埠  
 **問題**  
  
 使用之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]若要產生的 Oracle 資料庫上的特定作業的結構描述，增益集也會建立連接埠繫結檔案。 您可以匯入此檔案使用繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 BizTalk Server 中的實體連接埠。 不過，當您將訊息傳送至使用這種連接埠之 Oracle 資料庫時，配接器無法了解指定的連接埠上的動作，並提供類似下面的錯誤：  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
\<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 **可能的原因**  
  
 當您在 BizTalk 協調流程中建立邏輯連接埠時，您指定特定名稱，這些連接埠上的作業，或您只使用類似 Operation_1、 Operation_2 等的預設名稱。不過，在產生的繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，作業名稱會是做為您產生中繼資料的 Oracle 資料庫作業的名稱相同。 比方說，如果您產生 ACCOUNTACTIVITY 資料表上的選取作業的中繼資料的 Oracle 資料庫中，動作會設定下列：  
  
```  
<Operation Name="Select" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
```  
  
 當您匯入繫結檔案時，實體連接埠上設定相同的動作。 因此，邏輯連接埠 （Operation_1、 Operation_2 等） 上的作業名稱不相符造成錯誤之實體通訊埠，在動作中指定的作業名稱。  
  
 **解決方式**  
  
 請確定作業中的名稱的邏輯連接埠是實體連接埠中的動作中指定的作業名稱相同。 執行下列其中之一：  
  
-   從 Operation_1 等變更 BizTalk 協調流程中的邏輯連接埠中的作業名稱，產生中繼資料，例如 Select 作業。  
  
-   將實體連接埠上的動作中的作業名稱變更為中的邏輯連接埠的作業名稱。 例如，您可以變更中實體的通訊埠，如下所示的動作：  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
    ```  
  
###  <a name="BKMK_OraDBOverflowExcep"></a>配接器會擲回上執行作業的溢位例外狀況 (「 System.OverflowException")  
 **問題**  
  
 如果您嘗試執行包含在資料集或弱式類型的 REF CURSOR 的 Oracle 數值資料類型的作業，請使用配接器，配接器可能會發生溢位例外狀況。  
  
 **可能的原因**  
  
 會發生這種情況是如果您提供的 Oracle 數值資料類型，在資料集或弱式類型的 REF CURSOR 無法放入個別的.NET 型別之較大的值。  
  
 **解決方式**  
  
 如果您想要傳遞的資料集或弱式類型的 REF CURSOR 內 Oracle 數值資料類型的較大的值，您必須啟用 「 安全輸入的值設定**EnableSafeTyping**內容繫結至**true**. 啟用 「 安全輸入字串的形式公開在資料集或弱式類型的 REF CURSOR 的 Oracle 數值資料類型。  
  
###  <a name="BKMK_OraDBRootNode"></a>RootNode TypeName 在 BizTalk 專案中的錯誤  
 **問題**  
  
 在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字的**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **解決方式**  
  
1.  以滑鼠右鍵按一下錯誤，然後選取所參照的 rood 節點**屬性**。  
  
2.  如**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。  
  
###  <a name="BKMK_OraDBInvalBinding"></a>在 Visual Studio 中使用配接器時，無效的繫結警告  
 **問題**  
  
 當您建立的應用程式中使用配接器[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]並開啟配接器所產生的組態檔 (app.config)，您會看到類似下列的警告：  
  
```  
The element 'bindings' has invalid child element 'oracleDBBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **可能的原因**  
  
 會出現這個警告，因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結， `oracleDBBinding`，不標準繫結隨附於[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。  
  
 **解決方式**  
  
 您可以放心地忽略此警告。  
  
###  <a name="BKMK_OraDBNotification"></a>如果您使用一個以上的通知結構描述中相同的應用程式或跨多個相同的主機上的應用程式使用通知結構描述，BizTalk Server 擲回例外狀況  
 **問題**  
  
 XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述比對訊息類型，會擲回 BizTalk Server。  
  
 **可能的原因**  
  
 這是因為下列其中一項：  
  
-   產生一個以上的通知結構描述在 BizTalk Server 專案中，部署至 BizTalk Server 應用程式，然後執行應用程式要從 Oracle 資料庫接收通知。 因為通知結構描述是常見的就會發生衝突的 BizTalk Server 應用程式以部署的結構描述之間。  
  
-   發生多個專案，通知結構描述產生的每個 BizTalk 伺服器，每個專案加入相同主機上，個別的 BizTalk Server 應用程式部署的專案，然後執行應用程式或應用程式收到的通知Oracle 資料庫中。 因為結構描述和組件都可存取 BizTalk Server 中的應用程式，就會發生衝突之間常見的結構描述部署在不同的 BizTalk Server 應用程式和組件。  
  
 **解決方式**  
  
 BizTalk Server 應用程式使用單一的通知結構描述檔案。 如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用通知結構描述，建立包含單一通知結構描述時，應用程式，然後再使用 BizTalk Server 中的 從所有其他應用程式的通知結構描述。  
  
###  <a name="BKMK_MemUsage"></a>記憶體使用量和執行緒計數則會增加交易的輸入作業中使用配接器時  
 **問題**  
  
 在交易輸入作業中，例如輪詢，**是否有可用輪詢資料表中的任何資料**和配接器會持續輪詢，經過一段時間，您遇到的增加記憶體使用量和執行緒計數。  
  
 **可能的原因**  
  
 **如果沒有資料輪詢的資料表中可用**，之後每個接收逾時週期[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]需要產生新的執行緒，以繼續輪詢作業。 因此，執行緒計數和記憶體使用量會增加經過一段時間。 不過，如果資料表輪詢有一些資料，在相同的執行緒會繼續執行所有後續輪詢。  
  
 **解決方式**  
  
 我們建議您設定**ReceiveTimeout**的最大的可能值，這是 24.20:31:23.6470000 （24 天），讓新的執行緒未繁衍只能每隔 24 天。 這可確保，記憶體使用量和執行緒計數不會成長得太多太快。  
  
> [!NOTE]
>  如果已設定 SqlAdapterInboundTransactionBehavior，請確定 TransactionTimeout 同時設定為最大可能的值，這是 24.20:31:23.6470000 （24 天）。 當使用這個因應措施，我們可以加入 SqlAdapterInboundTransactionBehavior 才必須設定交易隔離等級。 否則，就移除該行為的最佳作法。  
  
 如需有關**ReceiveTimeout**繫結屬性，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。 如需指定繫結屬性的指示，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
> [!NOTE]
>  使用與配接器時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，將逾時設定為較大的值不會影響配接器的功能。  
  
## <a name="see-also"></a>另請參閱  
[Oracle 資料庫配接器進行疑難排解](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)  
[疑難排解安裝問題的 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-installation-issues-with-the-oracle-database-adapter.md)