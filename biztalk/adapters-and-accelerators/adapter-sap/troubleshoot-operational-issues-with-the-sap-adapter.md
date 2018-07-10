---
title: SAP 配接器在 BizTalk 中的疑難排解操作問題 |Microsoft Docs
description: 常見的錯誤、 問題和 mySAP 配接器在 BizTalk 配接器組件 (BAP) 中的解決方式
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb0f005b-7548-478b-8243-69e07c29d02c
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c137b60c9c9a8c354baf39b91349e0836c94b91
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998271"
---
# <a name="troubleshoot-operational-issues-with-the-sap-adapter"></a>SAP 配接器的疑難排解操作問題
本節討論如何使用以解決使用時可能遭遇的操作錯誤的疑難排解技巧[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。  
  
### <a name="enable-tracing"></a>啟用追蹤  
 如需有關追蹤中的支援資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱 <<c2> [ 診斷追蹤和訊息記錄 SAP 配接器的](../../adapters-and-accelerators/adapter-sap/diagnostic-tracing-and-message-logging-for-the-sap-adapter.md)。  
  
##  <a name="client_dll"></a> 載入的繫結時發生錯誤  
 **問題**  
  
 當您嘗試啟動[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，GUI 會產生下列錯誤：  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **原因**  
  
 當您啟動[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]載入所有已安裝的配接器的配接器繫結。 接著，配接器繫結均依存於企業應用程式特定的用戶端軟體。 您可能會面臨此問題的一個或兩個原因如下：  
  
- 在您安裝配接器的電腦上未安裝必要的 LOB 用戶端軟體。  
  
- 未安裝中包含的所有配接器的配接器的一般或完整安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 不過，只有一個企業應用程式可能會安裝 LOB 用戶端程式庫。 如此一來，GUI 無法載入其他配接器的繫結。  
  
  **解決方式**  
  
- 請確定您執行自訂安裝來安裝您所需要的介面卡的介面卡。  
  
- 請確定您已安裝在電腦上安裝必要的 LOB 用戶端版本[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 [支援 LOB 系統](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)列出支援的版本。 [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]也需要來與 SAP 系統的特定 Dll。 如需有關在配接器所需的 Dll 的詳細資訊，請參閱[安裝適用於 SAP 的資料提供者的自訂 Rfc](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md)。
  
##  <a name="BKMK_SAPDisplay"></a> SAP 配接器在 BizTalk 管理主控台遺漏  
 **問題**  
  
[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]未顯示在 BizTalk Server 管理主控台中的配接器清單中。  
  
 **原因**  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]是 WCF 自訂繫結。 因此，雖然[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它不會顯示 WCF 自訂繫結，因此，不會顯示以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
 **解決方式**  
  
 您可以明確加入[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]要[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中所述的步驟[SAP 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)。  
  
##  <a name="BKMK_SAPConnOpen"></a> Dll 缺少開啟 SAP 的連線時發生錯誤  
 **問題**  
  
 當您嘗試開啟連線到 SAP 系統時使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，在 SAP 系統中，會出現一個對話方塊通知某些 Dll 會遺失。  
  
 **原因**  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]用以 librfc32u.dll 建立與 SAP 系統的連線。 Librfc32u.dll，相對的需要一組 Dll 才能運作。 如果這些支援的 Dll 不會新增至 PATH 變數的電腦上，您會收到此錯誤其中[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]安裝。  
  
 **解決方式**  
  
 請參閱表提供的解決方案[載入配接器繫結時發生錯誤](#client_dll)問題。 下表列出支援的 Dll，才能與 SAP 系統使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
##  <a name="BKMK_SAPXmlRetrieve"></a> 擷取具有超過 65536 節點的 XML 時發生錯誤  
 **問題**  
  
 配接器會提供擷取有超過 65536 節點的 XML 輸出時發生下列錯誤。  
  
```  
Maximum number of items that can be serialized or deserialized in an object graph is '65536'.  
Change the object graph or increase the MaxItemsInObjectGraph quota.  
```  
  
 **原因**  
  
 配接器無法序列化和還原序列化的物件超過 65536 個項目。  
  
 **解決方式**  
  
 您可以修正此問題，藉由設定`maxItemsInObjectGraph`參數，在下列兩種方式之一：  
  
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
  
  範例 app.config 會如下所示。  
  
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
      <endpoint   behaviorConfiguration="NewBehavior" binding="sapBinding"  
       contract="IOutboundContract" name="sap_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
##  <a name="BKMK_SAPConnURI"></a> 在 BizTalk Server 中輸入 WCF 自訂連接埠的連線 URI 的錯誤  
 **問題**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 當您指定的連接來連接到 SAP 系統的 URI 時，請提供下列的錯誤。  
  
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
  
##  <a name="BKMK_SAPOperate"></a> 完成的作業上 SAP 的 System.ArgumentNullException 時發生  
 **問題**  
  
 執行 SAP 系統使用的任何作業時，配接器會產生下列錯誤[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
```  
System.ArgumentNullException: Value cannot be null.  
```  
  
 **原因**  
  
 未指定訊息的 WCF 動作。 WCF 會需要為每個作業，因為它會通知配接器要在 LOB 應用程式上執行的作業指定的 SOAP 動作。  
  
 **解決方式**  
  
 指定的 SOAP 動作，傳送埠中或在 BizTalk 協調流程中的訊息內容屬性。 如需相關指示，請參閱 <<c0> [ 設定 SAP 系統的 SOAP 動作](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md)。 請參閱[訊息和訊息結構描述](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)以查看每個作業的動作清單。  
  
##  <a name="BKMK_SAPXmlParsing"></a> 因為不正確的作業名稱中指定的動作而 XmlReaderParsingException  
 **問題**  
  
 將訊息傳送至 SAP 系統時，BizTalk Server 管理主控台就會產生下列錯誤：  
  
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
  
 上述的格式，作業名稱係由您選擇在產生結構描述時的作業。 比方說，如果您針對 RFC_CUSTOMER_GET 產生結構描述，動作中的作業名稱會 「 RFC_CUSTOMER_GET"。 不過，作業名稱的邏輯連接埠中建立 BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可能會不同。  
  
 **解決方式**  
  
 請確定作業的名稱在這兩個邏輯連接埠 (BizTalk 協調流程中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]) 和 （在 BizTalk Server 管理主控台） 的實體連接埠都相同。  
  
##  <a name="BKMK_SAPHundredCons"></a> 開啟 SAP 超過 100 個連線時發生錯誤  
 **問題**  
  
 開啟超過 100 個連接到 SAP 系統時，配接器會擲回下列例外狀況。  
  
```  
Microsoft.ServiceModel.Channels.Common.ConnectionException: ErrorCode=RFC_OK. ErrorGroup=RFC_ERROR_COMMUNICATION. SapErrorMessage=Connect to SAP gateway failed  
Connect_PM  GWHOST=<gw_host>, GWSERV=<gw_serv>, SYSNR=<sys_number>  
LOCATION    CPIC (TCP/IP) on local host with Unicode  
ERROR       max no of 100 conversations exceeded  
```  
  
 **原因**  
  
 根據預設，SAP 不會啟用超過 100 個連線到系統。  
  
 **解決方式**  
  
 若要增加的連線數目上限，您必須已安裝，並將它設定為數值的 SAP 用戶端程式庫的電腦上建立環境變數。 您指定這個環境變數的值是可將 SAP 系統的連線數目上限。 建立環境變數詳細資料如下：  
  
- **變數名稱**: CPIC_MAX_CONV  
  
- **變數值**： 任何正數值。 例如，如果要啟用 200 個連接到 SAP 系統，您可以指定值為 200。  
  
  如需建立環境變數的指示，請參閱 「 如何建立在 Windows 2000 的系統變數 」 在[ http://go.microsoft.com/fwlink/?LinkId=95020 ](http://go.microsoft.com/fwlink/?LinkId=95020)。  
  
##  <a name="BKMK_SAPIDOCMetadata"></a> 產生錯誤，或擷取 Idoc 的中繼資料  
 **問題**  
  
 產生的中繼資料時**接收**SAP 系統中 idoc 的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會產生下列錯誤。  
  
```  
Error while retrieving or generating the WSDL.  
Adapter message: Details: ErrorCode=RFC_EXCEPTION.  
ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage= OBJECT_UNKNOWN.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: IDOCTYPE_READ_COMPLETE.  
```  
  
 **原因**  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]擷取的中繼資料會使用 RFC IDOCTYPE_READ_COMPLETE**接收**IDOC 的作業。 叫用這個 RFC SAP 系統中需要特定的使用者權限。 如果您已經連接到 SAP 系統，請使用要叫用 IDOCTYPE_READ_COMPLETE RFC，權限的認證，產生中繼資料，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會產生錯誤。  
  
 **解決方式**  
  
 使用您所使用的配接器的相同認證的 SAP GUI 登入。 瀏覽至交易 SE37，並輸入要執行為 IDOCTYPE_READ_COMPLETE RFC 的名稱。  
  
 對於 PI_IDOCTYP 和 PI_CIMTYP 的輸入參數，輸入的值對應至自訂的 IDoc。 PI_VERSION 和 PI_RELEASE 參數，為選擇配接器中繼資料的 UI 中輸入相同的值。 然後按 f8 鍵來執行。  
  
 您應該取得相同的例外狀況做什麼配接器接收，關於此問題的詳細資訊。  
  
 如果您仍然無法解決問題時，產生的結構描述**ReceiveIdoc**作業，而不是**接收**作業。 在此情況下，SAP 配接器不會使用 IDOCTYPE_READ_COMPLETE，並不會擲回任何錯誤。  
  
##  <a name="BKMK_SAPIDOCReceive"></a> 傳送或接收已釋放區段的 Idoc 的錯誤  
 **問題**  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]提供 XmlReaderParsingException 傳送 Idoc 時 (使用**傳送**作業) 或接收 Idoc (使用**接收**作業)，已釋放區段。  
  
 **原因**  
  
 IDOCs 會構成的區段。 產生中繼資料時[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]擷取會出現在 SAP 系統的所有發行的區段。 不過，當配接器用戶端使用的中繼資料執行的作業，例如接收 IDOC，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]提供 XmlReaderParsingException。 這是因為 SAP 系統接收 IDOC 時，可能會傳送一些未發行的區段，其中的中繼資料未產生配接器。  
  
 **解決方式**  
  
 執行下列其中一項：  
  
-   套用適當的修補程式的未發行區段，以升級您的 SAP 系統。  
  
-   使用**SendIdoc**或是**ReceiveIdoc**分別傳送和接收 Idoc 的作業。 如需有關這些作業的詳細資訊，請參閱 <<c0> [ 對 sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。  
  
##  <a name="BKMK_SAPIDOCSend"></a> 傳送一般檔案 Idoc 到 SAP 使用 SAP FilePort 已收到的錯誤  
 **問題**  
  
 如果您嘗試傳送 (使用**傳送**作業) 的 SAP 系統，使用 SAP FilePort 產生一般檔案 IDOC，BizTalk 協調流程中的一般檔案剖析器無法將 flatf 檔案轉換成 XML 格式，藉此失敗IDOD**傳送**作業。  
  
 **原因**  
  
 當 SAP 系統產生使用 FilePort IDOC 時，它會修剪關閉區段結尾的所有空白空間。 不過，一般檔案剖析器會預期要有成功地將一般檔案轉換成 XML 區段的最後一個欄位的資料。 區段中沒有空白空間，因為一般檔案剖析器無法剖析 XML 至一般檔案。  
  
 **解決方式**  
  
 對於使用 SAP FilePort 產生這類一般檔案 Idoc，使用**SendIdoc**作業改。 如需有關這項作業的詳細資訊，請參閱 <<c0> [ 對 sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。  
  
##  <a name="BKMK_SAPRecIDOCCompat"></a> 錯誤從 SAP 接收 Idoc，如果 EnableBizTalkCompatibilityMode 屬性設定為 true  
 **問題**  
  
 接收的 IDOC 時遇到下列例外狀況**EnableBizTalkCompatibilityMode**屬性組繫結設為 true:  
  
```  
System.Exception: Loading property information list by namespace failed or property not found in the list. Verify that the schema is deployed properly.  
```  
  
 **原因**  
  
 如果繫結屬性**EnableBizTalkCompatibilityMode**設為 **，則為 true**，您必須新增 BizTalk 屬性結構描述 DLL 的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為 BizTalk 應用程式中，也就是資源您的專案部署所在的應用程式。  
  
 **解決方式**  
  
 BizTalk 屬性結構描述的名稱[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]已*Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*。 這會安裝[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]設定之下\<安裝磁碟機\>: \Program Files\Microsoft BizTalk 配接器 Pack\bin。 執行下列工作，以加入這個組件為您的 BizTalk 應用程式中的資源。  
  
#### <a name="add-an-assembly-as-a-resource-in-biztalk-application"></a>將組件新增為 BizTalk 應用程式中的資源  
  
1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，展開**應用程式**，，然後您要新增 BizTalk 組件的應用程式。  
  
3. 依序展開**應用程式**和您要新增 BizTalk 組件的應用程式。  
  
4. 以滑鼠右鍵按一下**資源**，指向**新增**，然後按一下**BizTalk 組件**。  
  
5. 按一下 **新增**，瀏覽至包含 BizTalk 組件檔案的資料夾中，選取 BizTalk 組件檔案，然後按一下**開啟**。  
  
6. 在 **選項**，指定 BizTalk 組件安裝到 GAC 的選項，然後按一下**確定**。  
  
##  <a name="BKMK_SAPIDOCValidate"></a> 從 SAP 系統接收 Idoc 時的驗證錯誤  
 **問題**  
  
 從 SAP 系統接收 IDOC 無法驗證，並出現類似下列錯誤：  
  
```  
There was a failure executing the receive pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLReceive, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=<token>"  
Source: "Pipeline " Receive Port: "ReceiveIdoc" URI: "<connection uri>"  
Reason: The document failed to validate because of the following error:  
"The 'http://Microsoft.LobServices.Sap/2007/03/Types/Idoc/3/CREMAS03//620:TAXBS' element has an invalid value according to its data type."  
```  
  
 **原因**  
  
 產生用於接收 IDOC 的中繼資料包含允許的值，可接收的特定資料行做為接收作業的一部分。 這些值會公開為列舉型別中產生的中繼資料。 不過，實際收到的 IDOC 時，所收到的值可能會不同於列舉值。 因此，接收作業失敗時驗證值。 例如，在上述的錯誤訊息驗證失敗 TAXBS 資料行。  
  
 **解決方式**  
  
 您必須以手動方式會包含從 SAP 系統接收到的值編輯 （適用於 BizTalk 專案） 的結構描述或用戶端 proxy 中列舉型別 （適用於.NET 專案使用 WCF 服務模型）。  
  
##  <a name="BKMK_SAPFFIDOC"></a> 一般檔案 Idoc 之前和之後轉換成 XML，並不相同  
 **問題**  
  
 如果您將轉換 XML 使用結構描述中，一般檔案 IDOC，然後將 XML 轉換回一般檔案 IDOC，透過使用結構描述的管線使用一般檔案剖析器，並不相同的兩個一般檔案 Idoc。  
  
 **原因**  
  
 當一般檔案 IDOC 產生 XML 時，一般檔案剖析器不會產生具有空白值的 XML 節點。 當這個 XML 轉換回一般檔案時，在 XML 中遺失的節點不會反映在一般檔案 IDOC。 因此一般檔案 Idoc 並不相同。  
  
 **解決方式**  
  
 在結構描述中用來將一般檔案轉換成 XML，反之亦然，「 傳送 」 或 「 接收 」 節點在定義內，執行下列作業：  
  
1. 設定**suppress_empty_nodes**屬性設**false**並設定**generate_empty_nodes**屬性設**true**。 根據預設， **suppress_empty_nodes**屬性設定為 **，則為 true**並**generate_empty_nodes**屬性設定為**false**，和因此所有空的節點不會反映在 XML 中。  
  
2. 一般檔案可能包含額外歸位字元結尾。 您可以設定**suppress_trailing_delimiters**屬性設**是**若要避免此額外歸位字元。 這個屬性也會公開成**隱藏尾端分隔符號**屬性，如果您開啟中的結構描述[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
##  <a name="BKMK_SAPAction"></a> 使用與繫結檔案所建立的實體連接埠不正確的動作時發生錯誤  
 **問題**  
  
 使用之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]若要產生結構描述上的 SAP 系統的特定作業，增益集也會建立連接埠繫結檔案。 您可以匯入此檔案使用繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 BizTalk Server 中的實體連接埠。 不過，當您將訊息傳送至 SAP 系統，請使用這類連接埠時，配接器無法了解指定的連接埠上的動作，並提供類似下列的錯誤：  
  
```  
Microsoft.ServiceModel.Channels.Common.UnsupportedOperationException: Incorrect Action   
<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <Operation Name="<op_name>" Action="<action>" />  
</BtsActionMapping>. Correct the specified Action, or refer to the documentation on the allowed formats for the Actions.  
```  
  
 **原因**  
  
 當您在 BizTalk 協調流程中建立邏輯連接埠時，您指定特定名稱，這些連接埠的作業，或您只使用預設名稱，例如 Operation_1、 Operation_2 等。不過，在所產生之繫結檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，作業名稱會是您要為其產生中繼資料作業的名稱相同。 比方說，如果您為 RFC_CUSTOMER_GET 產生中繼資料，動作會設定所示：  
  
```  
<Operation Name="RFC_CUSTOMER_GET" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET" />  
```  
  
 當您匯入繫結檔案時，實體連接埠上設定相同的動作。 因此，邏輯連接埠 （Operation_1、 Operation_2 等） 上的作業名稱不相符的實體連接埠，導致錯誤的動作中指定的作業名稱。  
  
 **解決方式**  
  
 請確定作業中的名稱的邏輯連接埠是與實體連接埠中的動作中指定的作業名稱相同。 執行下列其中之一：  
  
-   從 Operation_1 等變更 BizTalk 協調流程中的邏輯連接埠中的作業名稱，您可以為其產生中繼資料，例如 RFC_CUSTOMER_GET 作業。  
  
-   將邏輯連接埠中的作業名稱的實體連接埠動作中的作業名稱。 例如，您可以變更如下所示的實體連接埠中的動作：  
  
    ```  
    <Operation Name="Operation_1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET" />  
    ```  
  
##  <a name="BKMK_SAPTableParams"></a> 回應訊息的 SAP 上執行的作業不包含任何資料表參數  
 **原因**  
  
 如果您使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]執行 SAP 系統上的作業傳回大量資料表，以及每個資料表有大量的記錄，會相當大型的資料集，從 SAP 系統的回應訊息的一部分傳回。 因此，根據預設，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不會傳回資料表中的任何參數做為回應訊息的一部分。  
  
 **解決方式**  
  
 您可以要求您想要的資料表[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]做為回應的一部分傳回。 您可以藉由提供的空白資料表參數做為要求訊息傳送至 SAP 系統的一部分來這麼做。 例如， `<table_parameter_name />`。  
  
##  <a name="BKMK_SAPIncorrectCreds"></a> 配接器用戶端不從 SAP 接收回應
 **問題**  
  
 使用與介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，如果您的認證，在 WCF 自訂傳送連接埠不正確，不會處理要求訊息。 您指定正確的認證之後，訊息傳送至 SAP 系統，並在收到回應。 不過，回應訊息不適用於輸出連接埠。  
  
 **解決方式**  
  
 重新啟動 BizTalk 主控件執行個體。  
  
##  <a name="BKMK_SAPInboundConn"></a> 從 SAP 伺服器接收傳入的訊息的連線問題  
 **問題**  
  
 您會收到下列錯誤輸入的訊息從 SAP 伺服器使用 Wcf-custom 接收埠的接收時，才[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
```  
The Messaging Engine failed to add a receive location "<location_name>" with URL "<connection URI>" to the adapter "WCF-Custom".  
Reason: "Microsoft.Adapters.SAP.RFCException: Details: ErrorCode=RFC_OK. ErrorGroup=RFC_ERROR_COMMUNICATION. SapErrorMessage=Connect to SAP gateway failed  
Connect_PM  TPNAME=<name>, GWHOST=<host>, GWSERV=<server>  
```  
  
 不過，您可成功地將訊息傳送至 SAP 系統，請使用 Wcf-custom 傳送埠。  
  
 **解決方式**  
  
 在您執行配接器用戶端並再試一次接收內送的訊息的相同電腦上安裝 SAP GUI。 如需如何安裝 SAP GUI 的詳細資訊，請參閱 SAP 文件。  
  
##  <a name="BKMK_SAPRootNode"></a> 在 BizTalk 專案中的根節點類型名稱錯誤  
 **問題**  
  
 在 BizTalk 專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，如果從產生的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]包含無效的字元或保留的字**RootNode TypeName**屬性，編譯專案時，會發生下列錯誤:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **解決方式**  
  
1.  以滑鼠右鍵按一下參考錯誤，然後選取 rood 節點**屬性**。  
  
2.  針對**RootNode TypeName**屬性移除任何不合法的字元或保留字，例如，點 （.）。  
  
##  <a name="BKMK_SAPVS2008"></a> 在 Visual Studio 中使用配接器時，會產生無效的繫結警告。  
 **問題**  
  
 當 Visual Studio 中建立應用程式的情況下，您在使用配接器，並開啟 配接器所產生的組態檔 (app.config) 時，您會看到類似下列的警告：  
  
```  
The element 'bindings' has invalid child element 'sapBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **原因**  
  
 會出現這個警告，因為[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]繫結`sapBinding`，沒有標準繫結隨附[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。  
  
 **解決方式**  
  
 您可以放心地忽略此警告。  
  
##  <a name="BKMK_SAPSimilarSchema"></a> 在 BizTalk Server 的 XLANG 例外狀況
 **問題**  
  
 XLANG 例外狀況或例外狀況，說明應用程式無法尋找文件規格，因為多個結構描述符合訊息類型，會擲回 BizTalk Server。  
  
 **原因**  
  
 這是因為下列其中一項：  
  
- 當您產生一個以上的 BizTalk Server 專案中，泛型作業 （例如 SendIdoc 和 ReceiveIdoc） 的結構描述將它部署到 BizTalk Server 應用程式，然後執行應用程式來執行 SAP 系統上的個別作業。 因為結構描述是常見的就會發生衝突之間會部署在 BizTalk Server 應用程式中的結構描述。  
  
- 如果多個專案，您已為每個 BizTalk Server 專案中產生泛型作業結構描述，部署到個別在相同的 BizTalk Server 應用程式裝載，並再執行應用程式或應用程式執行個別的每個專案對 SAP 系統的作業。 因為結構描述和組件都是可存取 BizTalk Server 中的應用程式，就會發生衝突之間通用的結構描述部署在各種 BizTalk Server 應用程式和組件。  
  
  **解決方式**  
  
  BizTalk Server 應用程式使用單一的一般作業的結構描述檔案。 如果您需要在相同主機上的多個 BizTalk Server 應用程式中使用泛型作業的結構描述，建立內含單一的一般作業的結構描述中，應用程式，然後使用 BizTalk Server 中的 所有其他應用程式的一般作業結構描述。  
  
## <a name="see-also"></a>另請參閱  
[SAP 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)