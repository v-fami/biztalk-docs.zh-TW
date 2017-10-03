---
title: "如何設定 Wcf-wshttp 接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b38cce4a-9c81-4716-b847-1acada4afc15
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f817949b105fa99402db7ca8b9df3a2ba3a0a76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-wshttp-receive-location"></a>如何設定 WCF-WSHttp 接收位置
您可以用程式設計方式或使用「BizTalk 管理」主控台來設定 WCF-WSHttp 接收位置。  
  
## <a name="configuration-properties"></a>組態屬性
  
 「BizTalk 總管物件模型」可讓您以程式設計的方式建立和設定接收位置。 BizTalk 總管物件模型公開**IReceiveLocation**接收位置組態介面具有**TransportTypeData**讀/寫屬性。 這個屬性會以 XML 字串之名稱-值配對的格式接受 WCF-WSHttp 接收位置組態屬性包。 若要在 BizTalk 總管物件模型中設定這個屬性，您必須設定**InboundTransportLocation**屬性**IReceiveLocation**介面。  
  
 **TransportTypeData**屬性**IReceiveLocation**介面沒有設定。 若沒有設定此屬性，WCF-WSHttp 配接器就會針對 WCF-WSHttp 接收位置組態使用預設值，如下表所示。  
  
 下表列出您可以在「BizTalk 總管物件模型」中針對 WCF-WSHttp 接收位置設定的組態屬性。  
  
|屬性名稱|類型|Description|  
|-------------------|----------|-----------------|  
|**識別**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;身分識別&gt;<br /><br /> &lt;userPrincipalName 值 ="username@contoso.com"/&gt;<br /><br /> &lt;/identity&gt;|指定此接收位置所提供服務的識別。 可以針對指定的值**識別**屬性，則根據安全性組態而有所不同。 這些設定可讓用戶端驗證此接收位置。 在用戶端與服務之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別能夠與這個項目的值相符。<br /><br /> 預設為空字串。|  
|**OpenTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道開啟作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**SendTimeout**|**System.TimeSpan**|指定時間值，表示可供完成傳送作業的時間間隔。 如果您使用要求-回應接收埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道關閉作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**MaxReceivedMessageSize**|Integer|指定大小上限，以位元組為單位，可以從網路收到的訊息 （包括標頭）。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> 預設值：65536|  
|**MessageEncoding**|Enum<br /><br /> -   **文字**-使用文字訊息編碼器。<br />-   **Mtom** -使用訊息傳輸最佳化機制 1.0 (MTOM) 編碼器。|指定用來為 SOAP 訊息編碼的編碼器。<br /><br /> 預設值：**文字**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** -Unicode BigEndian 編碼方式。<br />-   **utf-16** -16 位元編碼方式。<br />-   **utf-8** -8 位元編碼方式|指定要使用繫結上發出訊息的字元集編碼方式的字元時**MessageEncoding**屬性設定為**文字**。<br /><br /> 預設值： **utf-8**|  
|**EnableTransaction**|布林|指定是否使用來自用戶端的交易，將訊息提交至 MessageBox 資料庫。 如果這個屬性是`True`，用戶端都必須提交訊息使用**Ws-atomictransaction**通訊協定。 如果用戶端在交易式範圍以外提交訊息，這個接收位置會將例外狀況傳回至用戶端，而不會擱置任何訊息。<br /><br /> 此選項只適用於單向接收位置。 如果用戶端在要求-回應接收位置的交易式內容中提交訊息，則會將例外狀況傳回至用戶端，而不會擱置任何訊息。<br /><br /> 預設值：`False`|  
|**MaxConcurrentCalls**|Integer|指定對單一服務執行個體的並行呼叫數目。 超出上限的呼叫將排入佇列。 此屬性的範圍介於 1 和 Int32.MaxValue 之間。 預設值：200|  
|**SecurityMode**|Enum<br /><br /> -   **無**<br />-   **訊息**<br />-   **傳輸**<br />-   **TransportWithMessageCredential**<br /><br /> 如需有關成員名稱的**SecurityMode**屬性，請參閱**安全性模式**屬性**Wcf-wshttp 傳輸屬性對話方塊、 接收、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 |指定使用的安全性類型。<br /><br /> 預設值：**訊息**|  
|**TransportClientCredentialType**|Enum<br /><br /> -   **無**<br />-   **基本**<br />-   **Ntlm**<br />-   **Windows**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**TransportClientCredentialType**屬性，請參閱**傳輸用戶端認證類型**屬性**Wcf-wshttp 傳輸屬性對話方塊、 接收、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定在執行用戶端驗證時，所要使用的認證類型。<br /><br /> 預設值： **Windows**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **無**<br />-   **Windows**<br />-   **使用者名稱**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**MessageClientCredentialType**屬性，請參閱**訊息用戶端認證類型**屬性**Wcf-wshttp 傳輸屬性對話方塊方塊中，接收、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。<br /><br /> 預設值： **Windows**|  
|**AlgorithmSuite**|Enum<br /><br /> 如需有關成員名稱的**AlgorithmSuite**屬性，請參閱**演算法套件**屬性**Wcf-wshttp 傳輸屬性對話方塊、 接收、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。<br /><br /> 預設值： **Basic256**|  
|**NegotiateServiceCredential**|布林|指定是否會在超出範圍的用戶端提供此服務認證，或是透過交涉程序從此服務取得服務認證給用戶端。 這類交涉是一般訊息交換的先驅。<br /><br /> 如果**MessageClientCredentialType**屬性等於**無**， **Username**，或**憑證**，此屬性設定為**False**意指服務憑證位於超出訊號範圍的用戶端，以及用戶端，必須指定服務憑證。 這個模式可以與 SOAP 堆疊交互運作 (SOAP 堆疊會實作 WS-Trust 和 WS-SecureConversation)。<br /><br /> 如果**MessageClientCredentialType**屬性設定為**Windows**，此屬性設定為**False**指定 Kerberos 驗證。 這表示，用戶端和服務都必須是相同 Kerberos 網域的一部分。 這個模式可以與 SOAP 堆疊交互運作，SOAP 堆疊會實作 Kerberos Token 設定檔 (如 OASIS WSS TC 上所定義) 以及 WS-Trust 和 WS-SecureConversation。<br /><br /> 當這個屬性是**True**，會造成透過 SOAP 訊息以通道連接 SPNego 交換的.NET SOAP 交涉。<br /><br /> 預設值： **，則為 True**|  
|**EstablishSecurityContext**|布林|指定此安全性通道是否會建立安全的工作階段。 安全的工作階段會在交換應用程式訊息之前，先建立安全性內容語彙基元 (SCT)。<br /><br /> 預設值： **，則為 True**|  
|**ServiceCertificate**|字串|針對此接收位置指定用戶端用來驗證服務之 X.509 憑證的憑證指紋。 要用於此屬性的憑證必須安裝到**我**存放**目前使用者**位置。 **注意：**您必須將服務憑證安裝到**目前使用者**裝載此接收位置的接收處理常式的使用者帳戶的位置。 <br /><br /> 預設為空字串。|  
|**UseSSO**|布林|指定是否使用「企業單一登入」(SSO) 來擷取用戶端認證，以便發出 SSO 票證。 如需有關安全性組態支援 SSO，請參閱 「 企業單一登入可支援性的 Wcf-wshttp 接收配接器 > 一節中**Wcf-wshttp 傳輸屬性對話方塊、 接收、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用內容的 SOAP**主體**內送訊息建立 BizTalk 訊息內文部分的項目。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。<br />-   **UseEnvelope** -建立 BizTalk 訊息內文部分的整個 SOAP 從**信封**內送訊息。<br />-   **UseBodyPath** -使用中的內文路徑運算式**InboundBodyPathExpression**屬性以建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 此屬性只對請求-回應連接埠有效。<br /><br /> 如需有關如何使用**InboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍，soap**主體**內送 WCF 訊息的項目。<br /><br /> 預設值： **UseBodyElement**|  
|**InboundBodyPathExpression**|字串<br /><br /> 如需有關如何使用**InboundBodyPathExpression**屬性，請參閱[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。|指定內文路徑運算式來識別用於建立 BizTalk 訊息內文部分之內送訊息的特定部分。 此內文路徑運算式評估的 soap 的直系子元素**主體**節點內送訊息。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果這個屬性，則需要**InboundBodyLocation**屬性設定為**UseBodyPath**。<br /><br /> 預設為空字串。|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -Base64 編碼方式。<br />-   **Hex** ： 十六進位編碼。<br />-   **字串**： 文字編碼-utf-8。<br />-   **XML** -WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml **InboundBodyPathExpression**。|指定的編碼，Wcf-wshttp 接收配接器，用來解碼中指定的內文路徑運算式所識別的節點類型**InboundBodyPathExpression**。 如果這個屬性，則需要**InboundBodyLocation**屬性設定為**UseBodyPath**。<br /><br /> 預設值： **XML**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用 BizTalk 訊息內文部分建立的 soap 內容**主體**外寄回應訊息的項目。<br />-   **UseTemplate** -使用中提供的範本**OutboundXMLTemplate**屬性，建立內容的 SOAP**主體**外寄回應訊息的項目。<br /><br /> 如需有關如何使用**OutboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍，soap**主體**外寄 WCF 訊息的項目。 此屬性只適用於要求-回應接收位置。<br /><br /> 預設值： **UseBodyElement**|  
|**OutboundXMLTemplate**|字串<br /><br /> 如需有關如何使用**OutboundXMLTemplate**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定 XML 格式的範本內容的 SOAP**主體**外寄回應訊息的項目。 如果這個屬性，則需要**OutboundBodyLocation**屬性設定為**UseTemplate**。 此屬性只適用於要求-回應接收位置。<br /><br /> 預設為空字串。|  
|**SuspendMessageOnFailure**|布林|指定是否擱置因接收管線失敗或路由失敗而造成輸入處理失敗的要求訊息。<br /><br /> 預設值： **，則為 True**|  
|**IncludeExceptionDetailInFaults**|布林|指定基於偵錯目的傳回用戶端的 SOAP 錯誤詳細資料中，是否包括 Managed 例外狀況資訊。<br /><br /> 預設值： **False**|  
  
## <a name="configure-a-wcf-wshttp-receive-location-with-the-biztalk-administration-console"></a>設定 Wcf-wshttp 接收位置使用 BizTalk 管理主控台
  
 您可以在「BizTalk 管理」主控台中設定 WCF-WSHttp 接收位置配接器變數。 若接收位置並未設定屬性，系統就會使用 [BizTalk 管理主控台] 中的預設接收處理常式值。  
  
> [!NOTE]
>  完成下列程序之前，您必須已經新增接收埠。 如需詳細資訊，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
## <a name="configure-variables-for-a-wcf-wshttp-receive-location"></a>設定 Wcf-wshttp 接收位置變數  
  
1.  在 BizTalk 管理主控台中，展開  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開您想要在其中建立接收位置的應用程式。  
  
2.  在 [BizTalk 管理主控台] 的左窗格中，按一下 **[接收埠]** 節點。 然後在右窗格中，使用滑鼠右鍵按一下與現有接收位置關聯的接收埠，或是您要與新接收位置關聯的接收埠，然後按一下 **[屬性]**。  
  
3.  在**接收埠屬性**對話方塊的左窗格中，選取**接收位置**，然後在右窗格中，按兩下現有接收位置或按一下**新增**以建立新接收位置。  
  
4.  在**接收位置屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**Wcf-wshttp**從下拉式清單清單，然後再按**設定**。  
  
5.  在**Wcf-wshttp 傳輸屬性**對話方塊**一般**索引標籤上，設定端點位址和服務識別 Wcf-wshttp 接收位置。 如需有關**一般**索引標籤中**Wcf-wshttp 傳輸屬性**對話方塊中，請參閱**Wcf-wshttp 傳輸屬性對話方塊、 接收、 一般** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
6.  在**Wcf-wshttp 傳輸屬性**對話方塊**繫結**索引標籤上，設定逾時、 編碼和交易屬性。 如需有關**繫結**索引標籤中**Wcf-wshttp 傳輸屬性**對話方塊中，請參閱**Wcf-wshttp 傳輸屬性對話方塊、 接收、 繫結** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
7.  在**Wcf-wshttp 傳輸屬性**對話方塊**安全性**索引標籤上，定義的安全性功能的 Wcf-wshttp 接收位置。 如需有關**安全性**索引標籤中**Wcf-wshttp 傳輸屬性**對話方塊中，請參閱**Wcf-wshttp 傳輸屬性對話方塊、 接收、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
8.  在**Wcf-wshttp 傳輸屬性**對話方塊**訊息**索引標籤上，指定 SOAP 資料選取範圍**主體**項目。 如需有關**訊息**索引標籤中**Wcf-wshttp 傳輸屬性**對話方塊中，請參閱**Wcf-wshttp 傳輸屬性對話方塊、 接收、 訊息** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="configure-a-wcf-wshttp-receive-location-programmatically"></a>設定 Wcf-wshttp 接收位置，以程式設計的方式
  
 您可以使用下列格式來設定屬性：  
  
```  
<CustomProps>  
  <InboundBodyPathExpression vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt="11">0</UseSSO>  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">Message</SecurityMode>  
  <TransportClientCredentialType vt="8">Windows</TransportClientCredentialType>  
  <NegotiateServiceCredential vt="11">-1</NegotiateServiceCredential>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <SuspendMessageOnFailure vt="11">0</SuspendMessageOnFailure>  
  <EnableTransaction vt="11">0</EnableTransaction>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <EstablishSecurityContext vt="11">-1</EstablishSecurityContext>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <MaxConcurrentCalls vt="3">16</MaxConcurrentCalls>  
  <ServiceCertificate vt="8" />  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 下列程式碼片段會說明如何建立 WCF-WSHttp 接收位置：  
  
```  
// Use BizTalk Explorer object model to create new WCF-WSHttp receive location   
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
  <InboundBodyLocation vt=""8"">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt=""11"">0</UseSSO>  
  <Identity vt=""8"">  
    <identity>  
    <userPrincipalName value=""username@contoso.com"" />  
    </identity>  
  </Identity>  
</CustomProps>";  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  
// Add a new BizTalk application  
Application application = explorer.AddNewApplication();  
application.Name = "SampleBizTalkApplication1001";  
// Save  
explorer.SaveChanges();  
  
// Add a new one-way receive port  
IReceivePort receivePort = application.AddNewReceivePort(false);  
receivePort.Name = "SampleReceivePort";  
// Add a new one-way receive location  
IReceiveLocation recieveLocation = receivePort.AddNewReceiveLocation();  
recieveLocation.Name = "SampleReceiveLocation";  
// Find a receive handler for WCF-WSHttp   
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-WSHttp" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "/samplepath/sampleservice.svc";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-WSHttp"];  
recieveLocation.TransportTypeData = transportConfigData;  
// Save  
explorer.SaveChanges();   
```  
  
## <a name="see-also"></a>另請參閱  
 [發佈 WCF 服務，利用外掛式 WCF 接收配接器](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)   
 [設定 IIS 的外掛式 WCF 接收配接器](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)   
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [如何變更服務帳戶和密碼](../core/how-to-change-service-accounts-and-passwords.md)   
 [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)   
 [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [設定 Wcf-wshttp 配接器](../core/configuring-the-wcf-wshttp-adapter.md)