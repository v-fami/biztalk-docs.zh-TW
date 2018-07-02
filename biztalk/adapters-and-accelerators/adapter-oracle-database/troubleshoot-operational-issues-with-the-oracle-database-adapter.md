---
title: 針對使用 Oracle 資料庫配接器的操作問題進行疑難排解 |Microsoft Docs
description: 常見問題和解決方案的 Oracle 資料庫配接器在 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fb83245-2b6a-48cc-8601-b923bb009a58
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13dfe903e897ebc3d26e6dc380233f80253ddfc5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968415"
---
# <a name="troubleshoot-operational-issues-with-the-oracle-database-adapter"></a>針對使用 Oracle 資料庫配接器的操作問題進行疑難排解
疑難排解技術來解決您可能會遇到使用的操作錯誤[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。  
  
## <a name="enable-tracing"></a>啟用追蹤  
 如需有關追蹤中的支援資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 診斷追蹤和訊息記錄的 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter.md)。  
  
## <a name="known-issues"></a>已知問題  
 以下是最常見的錯誤時使用，可能會遇到[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，以及其可能的原因和解決方式。   
  
### <a name="BKMK_OraDBLoading"></a> 載入配接器繫結時發生錯誤  
 **問題**  
  
 當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，您會收到下列錯誤：  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **原因**  
  
 當您嘗試啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，WCF 會載入所有已安裝的配接器的配接器繫結。 接著，配接器繫結均依存於企業應用程式特定的用戶端軟體。 您可能會面臨此問題的一個或兩個原因如下：  
  
- 在您安裝配接器的電腦上未安裝必要的 LOB 用戶端軟體。  
  
- 未安裝中包含的所有配接器的配接器的一般或完整安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 不過，只有一個企業應用程式可能會安裝 LOB 用戶端程式庫。 如此一來，GUI 無法載入其他配接器的繫結。  
  
  **解決方式**  
  
- 請確定所需的 LOB 用戶端版本已安裝在您安裝的電腦上[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 [支援的營運 (LOB) 和企業系統](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出支援的用戶端版本。  
  
- 請確定您執行自訂安裝來安裝您所需要的介面卡的介面卡。  
  
  > [!NOTE]
  >  若要確定您的應用程式會使用 ODP.NET 的最新版本，您必須擁有 「 原則 Dll 」 的電腦上安裝並註冊在 GAC 中。 如需詳細資訊，請參閱 <<c0> [ 適用於.NET 的 Oracle 資料提供者](http://go.microsoft.com/fwlink/p/?LinkId=92834)Oracle 網站上。  
  
###  <a name="BKMK_OraDBAdapDisplay"></a> Oracle 資料庫配接器不會顯示在清單中，BizTalk Server 管理主控台中的配接器  
 **問題**  
  
[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]未列在 BizTalk Server 管理主控台中的配接器清單。  
  
 **原因**  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]是 WCF 自訂繫結。 因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結，因此，不會顯示以 WCF 為基礎[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 **解決方式**  
  
 您可以明確加入[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]要[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。  
  
###  <a name="BKMK_OraDBXMLRetrieve"></a> 擷取具有超過 65536 節點的 XML 輸出時發生錯誤  
 **問題**  
  
 擷取 XML 輸出，具有超過 65536 的節點時，配接器就會產生下列錯誤。  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 **原因**  
  
 配接器無法序列化和還原序列化的物件超過 65536 個項目。  
  
 **解決方式**  
  
 您可以修正此問題，藉由設定`maxItemsInObjectGraph`參數。 您可以將它設定在下列兩種方式之一：  
  
- 設定此參數，進而`maxItemsInObjectGraph`中的參數`ServiceBehavior`服務類別上的屬性。  
  
- 將下列內容新增至您的應用程式的 app.config 檔。  
  
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
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
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
  </system.serviceModel>  
</configuration>  
```  
  
###  <a name="BKMK_OraDBPerfOps"></a> 執行的 Oracle 資料庫上的作業時發生錯誤  
 **問題**  
  
 執行 Oracle 資料庫使用的任何作業時，配接器會提供下列錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
- **BizTalk server**  
  
  ```  
  System.ArgumentNullException: Value cannot be null.  
  ```  
  
  **原因**  
  
  未指定訊息的 WCF 動作。 WCF 會需要為每個作業，因為它會通知配接器要在 LOB 應用程式上執行的作業指定的 SOAP 動作。  
  
  **解決方式**  
  
  指定的 SOAP 動作，傳送埠中或在 BizTalk 協調流程中的訊息內容屬性。 如需相關指示，請參閱 <<c0> [ 設定 Oracle 資料庫的 SOAP 動作](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md)。 請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)以查看每個作業的動作清單。  
  
###  <a name="BKMK_OraDBXmlParsing"></a> 因為不正確的作業名稱中指定的動作而 XmlReaderParsingException  
 **問題**  
  
 傳送訊息到 Oracle 資料庫時，BizTalk Server 管理主控台就會產生下列錯誤：  
  
```  
Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Invalid argument:  
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<operation_name>" Action="<action>" />  
</BtsActionMapping>  
```  
  
 **原因**  
  
 如果您匯入所建立的連接埠繫結檔來設定 WCF 自訂連接埠[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，以下列格式指定連接埠中的動作：  
  
```  
<BtsActionMapping>  
  <Operation Name="Op1" Action="http://MyService/Svc/Op1" />  
</BtsActionMapping>  
```  
  
 上述的格式，作業名稱係由您選擇在產生結構描述時的作業。 比方說，如果您產生結構描述的資料表上的插入作業時，動作中的作業名稱會是 「 插入 」。 不過，作業名稱的邏輯連接埠中建立 BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可能會不同。  
  
 **解決方式**  
  
 請確定作業的名稱在這兩個邏輯連接埠 (BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) 和 （在 BizTalk Server 管理主控台） 的實體連接埠都相同。  
  
###  <a name="BKMK_OraDBConnURI"></a> 在 BizTalk 中指定的 WCF 自訂連接埠的連線 URI 時發生錯誤  
 **問題**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 當您指定的連接來連接到 Oracle 資料庫的 URI 時，請提供下列的錯誤。  
  
```  
Error saving properties.  
(System.ArgumentException) The specified address is invalid.  
(System.ArgumentException) Invalid address;  
"<connection URI>" is not a well-formed absolute uri.  
```  
  
 **原因**  
  
 連線 URI 不會遵守標準的編碼格式。 例如，參數的值可能會包含空格。  
  
 **解決方式**  
  
 請確定您指定的 URI 符合標準的編碼格式的連接。 例如，"%20"必須取代空格。  
  
###  <a name="BKMK_OraDBInvalCursor"></a> 無效的資料指標時叫用使用 REF CURSOR 參數的預存程序的例外狀況  
 **問題**  
  
 當您叫用 Oracle 資料庫中採用 REF CURSOR 輸入的程序時，您可能會收到下列例外狀況：  
  
```  
Microsoft.ServiceModel.Channels.Common.TargetSystemException: ORA-01001: invalid cursor ---> Oracle.DataAccess.Client.OracleException  
```  
  
 **原因**  
  
 您所叫用的程序的 PL/SQL 區塊無法使用 REF 資料指標，也就是在 REF CURSOR，可以取得指派給出 REF CURSOR。  
  
 **解決方式**  
  
 PL/SQL 區塊必須傳送出 REF 資料指標不適當的處理。  
  
###  <a name="BKMK_OraDBValidateResp"></a> 驗證使用 BizTalk Server ReadLOB 作業的回應時的錯誤  
 **問題**  
  
 在執行 ReadLOB 作業使用時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，驗證對 Web 服務描述語言 (WSDL) 的 Oracle 資料庫的回應失敗。  
  
 **原因**  
  
 WSDL 會包含定義執行的服務為基礎的要求，但 BizTalk 案例不需要 StreamBody 節點名稱。 因此，輸出 XML，不包含 StreamBody 節點，是相較於 WSDL，驗證將會失敗。  
  
 **解決方式**  
  
 驗證符合使用 BizTalk Server 所產生的輸出時，則您可以移除 WSDL StreamBody 節點。 執行下列步驟來執行這項操作：  
  
1. WSDL 包含 StreamBody 節點看起來像這樣。  
  
   ```  
   <xs:element name="ReadLOBResponse">  
       <xs:annotation>  
         <xs:documentation>  
           <doc:action xmlns:doc="http://schemas.microsoft.com/servicemodel/adapters/metadata/documentation">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/TBL_ALL_DATATYPES/ReadLOB/response\</doc:action>  
         </xs:documentation>  
       </xs:annotation>  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element minOccurs="1" maxOccurs="1" name="ReadLOBResult" nillable="true" type="ns3:StreamBody" />  
         </xs:sequence>  
       </xs:complexType>  
     </xs:element>  
   ```  
  
    取代下列前面。  
  
   ```  
   <xs:element name="ReadLOBResponse">  
    <xs:annotation>  
    <xs:documentation>  
     <doc:action xmlns:doc="http://schemas.microsoft.com/servicemodel/adapters/metadata/documentation">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/TBL_ALL_DATATYPES/ReadLOB/response\</doc:action>   
     </xs:documentation>  
     </xs:annotation>  
    <xs:complexType>  
    <xs:sequence>  
     <xs:element minOccurs="1" maxOccurs="1" name="ReadLOBResult" type="xs:base64Binary" />   
     </xs:sequence>  
     </xs:complexType>  
     </xs:element>  
   ```  
  
    在此步驟中，您會移除輸入參考 = 原始 XSD 中的 「 ns3:StreamBody"並取代類型 ="xs:base64Binary 」。 此外，您會從原始 XSD 移除 nillable ="true"值。  
  
2. 從 WSDL 中移除下列。  
  
   ```  
   <xs:complexType name="StreamBody">  
       <xs:sequence>  
         <xs:element minOccurs="1" maxOccurs="1" name="Stream">  
           <xs:simpleType>  
             <xs:restriction base="xs:base64Binary">  
               <xs:minLength value="0" />  
             </xs:restriction>  
           </xs:simpleType>  
         </xs:element>  
       </xs:sequence>  
     </xs:complexType>  
     <xs:element name="StreamBody" nillable="true" type="ns3:StreamBody" />  
   ```  
  
   > [!NOTE]
   >  不支援使用 ReadLOB 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 您應該使用資料表的選取作業來讀取從 LOB 資料[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
###  <a name="BKMK_OraDBSchemaValidateFail"></a> 輪詢案例中的結構描述驗證可能會失敗  
 **問題**  
  
 在案例中的結構描述驗證失敗，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢資料庫資料表包含 ROWID 或 UNROWID 類型的欄位。  
  
 **原因**  
  
 在設計階段，當配接器會產生含有 ROWID 或 UNROWID，類型的欄位之資料表的中繼資料結構描述會包含"nillable = false"，這表示 ROWID 或 UNROWID 類型的欄位不可為 null。 不過，在執行階段時，配接器擷取的中繼資料，ROWID 或 UNROWID 類型的欄位包含 null 值。 因此，結構描述驗證會失敗。  
  
 **解決方式**  
  
 如果您使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以選擇停用結構描述驗證。 或者，您可以手動編輯要變更的結構描述"nillbale = true"ROWID 和 UNROWID 資料類型。  
  
###  <a name="BKMK_OraDBUnreasonConv"></a> 做為參數 '要求不合理 conversion' 錯誤時執行預存的記錄類型的程序  
 **原因**  
  
 假設其中 Oracle 預存程序會採用記錄類型做為參數。 記錄類型會宣告為會假設\<資料表名稱\>%資料列型別，在資料表中有很長的資料類型的資料行。 當[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]遇到的長資料型別，它會設定資料類型的大小等於指定的值**LongDatatypeColumnSize**繫結屬性。 不過，Oracle 資料庫不會定義 LONG 資料類型的大小。 因此，當配接器叫用預存程序，它會導致 '要求不合理 conversion' 錯誤。  
  
 **解決方式**  
  
 如果記錄類型有 LONG 資料類型，必須明確將它定義為封裝的一部分。  
  
###  <a name="BKMK_OraDBAdapRecognize"></a> 配接器無法辨識的實體連接埠上的動作，即使您使用 取用配接器服務增益集所產生的繫結檔案建立連接埠  
 **問題**  
  
 使用之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的 Oracle 資料庫上的特定作業的結構描述，增益集也會建立連接埠繫結檔案。 您可以匯入此檔案使用繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 BizTalk Server 中的實體連接埠。 不過，當您將訊息傳送至使用這類連接埠之 Oracle 資料庫時，配接器無法了解指定的連接埠上的動作，並提供類似下列的錯誤：  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 **原因**  
  
 當您在 BizTalk 協調流程中建立邏輯連接埠時，您指定特定名稱，這些連接埠的作業，或您只使用預設名稱，例如 Operation_1、 Operation_2 等。不過，在所產生之繫結檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，作業名稱會是您要為其產生中繼資料的 Oracle 資料庫作業的名稱相同。 比方說，如果您的 Oracle 資料庫中產生 ACCOUNTACTIVITY 資料表上的選取作業的中繼資料，動作會設定如下：  
  
```  
<Operation Name="Select" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
```  
  
 當您匯入繫結檔案時，實體連接埠上設定相同的動作。 因此，邏輯連接埠 （Operation_1、 Operation_2 等） 上的作業名稱不相符的實體連接埠，導致錯誤的動作中指定的作業名稱。  
  
 **解決方式**  
  
 請確定作業中的名稱的邏輯連接埠是與實體連接埠中的動作中指定的作業名稱相同。 執行下列其中之一：  
  
-   變更從 Operation_1 等的 BizTalk 協調流程中的邏輯連接埠中的作業名稱，您要為其產生中繼資料，例如選取作業。  
  
-   將邏輯連接埠中的作業名稱的實體連接埠動作中的作業名稱。 例如，您可以變更如下所示的實體連接埠中的動作：  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />  
    ```  
  
###  <a name="BKMK_OraDBOverflowExcep"></a> 配接器會擲回溢位例外狀況 (「 System.OverflowException") 上執行作業  
 **問題**  
  
 如果您嘗試執行包含 Oracle 資料集或弱式型別 REF 資料指標內的數值資料類型的作業，請使用配接器，配接器可能會擲回溢位例外狀況。  
  
 **原因**  
  
 會發生這種情況是如果您提供 Oracle 數值資料類型資料集或弱式型別 REF CURSOR 無法放入個別的.NET 型別內的較大的值。  
  
 **解決方式**  
  
 如果您想要將大型值傳給資料集或弱式型別 REF 資料指標內的 Oracle 數值資料類型，您必須啟用 「 安全輸入的值設定**EnableSafeTyping**繫結屬性**true**. 啟用 「 安全輸入公開在資料集或弱式型別 REF CURSOR 的 Oracle 數值資料型別為字串。  
  
###  <a name="BKMK_OraDBRootNode"></a> 在 BizTalk 專案中的根節點類型名稱錯誤  
 **問題**  
  
 在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **解決方式**  
  
1.  以滑鼠右鍵按一下參考錯誤，然後選取 rood 節點**屬性**。  
  
2.  針對**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。  
  
###  <a name="BKMK_OraDBInvalBinding"></a> 在 Visual Studio 中使用配接器時，會產生無效的繫結警告。  
 **問題**  
  
 當您建立應用程式中的使用配接器時[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]和開啟配接器所產生的組態檔 (app.config) 時，您會看到類似下列的警告：  
  
```  
The element 'bindings' has invalid child element 'oracleDBBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **原因**  
  
 會出現這個警告，因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結`oracleDBBinding`，沒有標準繫結隨附[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。  
  
 **解決方式**  
  
 您可以放心地忽略此警告。  
  
###  <a name="BKMK_OraDBNotification"></a> 如果您在相同的應用程式中使用一個以上的通知結構描述，或在相同主機上的多個應用程式之間，使用通知結構描述，BizTalk Server 擲回例外狀況  
 **問題**  
  
 XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述符合訊息類型，會擲回 BizTalk Server。  
  
 **原因**  
  
 這是因為下列其中一項：  
  
- 當您產生一個以上的通知結構描述在 BizTalk Server 專案中，將它部署到 BizTalk Server 應用程式，然後執行應用程式要從 Oracle 資料庫接收通知。 因為通知結構描述是常見的就會發生衝突之間會部署在 BizTalk Server 應用程式中的結構描述。  
  
- 發生多個專案，方法，您可以有為每個部署的專案，每個專案加入個別的 BizTalk Server 應用程式相同的主機上的 BizTalk Server 產生通知結構描述，並接著執行應用程式或應用程式收到的通知Oracle 資料庫中。 因為結構描述和組件都是可存取 BizTalk Server 中的應用程式，就會發生衝突之間通用的結構描述部署在各種 BizTalk Server 應用程式和組件。  
  
  **解決方式**  
  
  使用 BizTalk Server 應用程式的單一通知結構描述檔案。 如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用通知結構描述，建立包含單一的通知結構描述中，應用程式，然後使用 BizTalk Server 中的 從其他所有應用程式的通知結構描述。  
  
###  <a name="BKMK_MemUsage"></a> 記憶體使用量和執行緒計數增加而增加時使用中交易的輸入作業的配接器  
 **問題**  
  
 在交易輸入作業中，輪詢，例如**是否有可用在所輪詢的資料表中的任何資料**和配接器會持續輪詢，經過一段時間中，您遇到增加的記憶體使用量和執行緒計數。  
  
 **原因**  
  
 **如果沒有資料輪詢的資料表中可用**之後，每個接收逾時週期[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]會繁衍新的執行緒，以繼續輪詢作業。 因此，執行緒計數和記憶體使用量會增加一段時間。 不過，如果輪詢的資料表會有一些資料，相同的執行緒會繼續執行所有的後續輪詢。  
  
 **解決方式**  
  
 我們建議您設定**ReceiveTimeout**的最大的可能值，這是 24.20:31:23.6470000 （也就是 24 天），讓新的執行緒會繁衍只能每隔 24 天。 這可確保，記憶體使用量和執行緒計數不會變得太多太快。  
  
> [!NOTE]
>  如果已設定 SqlAdapterInboundTransactionBehavior，請確定 TransactionTimeout 也會設定為 最大可能的值，也就是 24.20:31:23.6470000 （也就是 24 天）。 當使用這個因應措施，我們可以新增 SqlAdapterInboundTransactionBehavior，只有當交易隔離等級必須設。 否則，就移除該行為的最佳作法。  
  
 如需詳細資訊**ReceiveTimeout**繫結屬性，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。 如需指定繫結屬性的指示，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
> [!NOTE]
>  使用的介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，逾時設定為較大的值不會影響配接器的功能。  
  
## <a name="see-also"></a>另請參閱  
[Oracle 資料庫配接器進行疑難排解](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)  
[針對使用 Oracle 資料庫配接器的安裝問題進行疑難排解](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-installation-issues-with-the-oracle-database-adapter.md)