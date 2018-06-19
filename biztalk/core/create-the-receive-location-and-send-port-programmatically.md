---
title: 建立接收位置和傳送埠，以程式設計的方式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47850e66-ce33-4c6a-8190-168071792c0b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d2f6871ca730e741ca4877907593931fc362a4d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "25976004"
---
# <a name="create-the-receive-location-and-send-port-programmatically"></a>建立接收位置，並以程式設計的方式傳送連接埠
設定 Wcf-basichttp 接收位置和傳送埠，以程式設計的方式。 若要使用 BizTalk 管理主控台，請參閱[Wcf-basichttp 配接器](../core/wcf-basichttp-adapter.md)。 
  
## <a name="configure-the-receive-location-programmatically"></a>以程式設計方式設定的接收位置  
  
 「BizTalk 總管物件模型」可讓您以程式設計的方式建立和設定接收位置。 BizTalk 總管物件模型會公開**IReceiveLocation** 接收位置組態介面具有 **TransportTypeData** 讀/寫屬性。 這項屬性會以 XML 字串之名稱-值配對的格式接受 WCF-BasicHttp 接收位置組態屬性包。 若要在 「 BizTalk 總管物件模型中設定這個屬性，您必須設定 **InboundTransportLocation** 屬性 **IReceiveLocation** 介面。  
  
 **TransportTypeData** 屬性 **IReceiveLocation** 介面並沒有設定。 若沒有設定此屬性，WCF-BasicHttp 配接器就會使用 WCF-BasicHttp 接收位置組態預設值，如下表所示。  
 
 下列程式碼片段說明如何建立 Wcf-basichttp 接收位置使用 BizTalk 總管物件模型︰  
  
```  
// Use BizTalk Explorer object model to create new WCF-BasicHttp receive location   
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
application.Name = "SampleBizTalkApplication";  
// Save  
explorer.SaveChanges();  
// Add a new one-way receive port  
IReceivePort receivePort = application.AddNewReceivePort(false);  
receivePort.Name = "SampleReceivePort";  
// Add a new one-way receive location  
IReceiveLocation recieveLocation = receivePort.AddNewReceiveLocation();  
recieveLocation.Name = "SampleReceiveLocation";  
// Find a receive handler for WCF-BasicHttp  
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-BasicHttp" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "/samplepath/sampleservice.svc";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-BasicHttp"];  
recieveLocation.TransportTypeData = transportConfigData;  
// Save  
explorer.SaveChanges();  
  
```  

您可以使用下列格式來設定屬性 `<CustomProps>`: 
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt="11">0</UseSSO>  
  <MessageClientCredentialType vt="8">UserName</MessageClientCredentialType>  
  <InboundBodyPathExpression vt="8" />  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <Identity vt="8">  
    <identity>  
    <userPrincipalName value="username@contoso.com" />  
    </identity>  
  </Identity>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">None</SecurityMode>  
  <TransportClientCredentialType vt="8">None</TransportClientCredentialType>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <SuspendMessageOnFailure vt="11">0</SuspendMessageOnFailure>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <MaxConcurrentCalls vt="3">16</MaxConcurrentCalls>  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```   
  
下表列出您可以設定接收位置組態屬性︰  
  
|屬性名稱|유형|Description|  
|-------------------|----------|-----------------|  
|**身分識別**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;身分識別&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|指定此接收位置所提供服務的識別。 您可以指定的值 **識別** 屬性，則根據安全性組態而有所不同。 這些設定可讓用戶端驗證此接收位置。 在用戶端與服務之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別能夠與這個項目的值相符。<br /><br /> 預設為空字串。|  
|**OpenTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道開啟作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**SendTimeout**|**System.TimeSpan**|指定時間值，表示可供完成傳送作業的時間間隔。 如果您使用要求-回應接收埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道關閉作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**MaxReceivedMessageSize**|Integer|指定大小上限，以位元組為單位，在網路上可以接收的訊息 （包括標頭）。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> Wcf-basichttp 配接器會利用 [BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086) 與端點進行通訊的緩衝的傳輸模式中的類別。 緩衝的傳輸模式下， [BasicHttpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=80659) 屬性會一律等於這個屬性的值。<br /><br /> 預設值：65536|  
|**MessageEncoding**|Enum<br /><br /> -   **文字**-使用文字訊息編碼器。<br />-   **Mtom** -使用訊息傳輸最佳化機制 1.0 (MTOM) 編碼器。|指定用來為 SOAP 訊息編碼的編碼器。<br /><br /> 預設值︰ **文字**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** -Unicode BigEndian 編碼方式。<br />-   **utf-16** -16 位元編碼方式。<br />-   **utf-8** -8 位元編碼方式|指定字元集的編碼方式來繫結上發出訊息時 **MessageEncoding** 屬性設定為 **文字**。<br /><br /> 預設值︰ **utf-8**|  
|**MaxConcurrentCalls**|Integer|指定對單一服務執行個體的並行呼叫數目。 超出上限的呼叫將排入佇列。 此屬性的範圍是從 1 到 **Int32.MaxValue**。<br /><br /> 預設值：200|  
|**SecurityMode**|Enum<br /><br /> -   **無**<br />-   **訊息**<br />-   **傳輸**<br />-   **TransportWithMessageCredential**<br />-   **TransportCredentialOnly**<br /><br /> 如需有關成員名稱的**SecurityMode**屬性，請參閱**安全性模式**屬性**Wcf-basichttp 傳輸屬性對話方塊、 接收、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定使用的安全性類型。<br /><br /> 預設值︰ **無**|  
|**TransportClientCredentialType**|如需有關成員名稱的**TransportClientCredentialType**屬性，請參閱**傳輸用戶端認證類型**屬性**Wcf-basichttp 傳輸屬性對話方塊、 接收、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定在執行用戶端驗證時，所要使用的認證類型。<br /><br /> 預設值︰ **無**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **使用者名稱**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**MessageClientCredentialType**屬性，請參閱**訊息用戶端認證類型**屬性**Wcf-basichttp 傳輸屬性對話方塊方塊中，接收、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。<br /><br /> 預設值︰ **使用者名稱**|  
|**AlgorithmSuite**|Enum<br /><br /> 如需有關成員名稱的**AlgorithmSuite**屬性，請參閱**演算法套件**屬性**Wcf-basichttp 傳輸屬性對話方塊、 接收、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。<br /><br /> 預設值︰ **Basic256**|  
|**ServiceCertificate**|字串|針對此接收位置指定用戶端用來驗證服務之 X.509 憑證的憑證指紋。 要用於此屬性的憑證必須安裝到 **我** 存放 **目前使用者** 位置。 **注意︰**  您必須將服務憑證安裝到 **目前使用者** 裝載此接收位置的接收處理常式的使用者帳戶的位置。 <br /><br /> 預設為空字串。|  
|**UseSSO**|Boolean|指定是否使用「企業單一登入」(SSO) 來擷取用戶端認證，以便發出 SSO 票證。 如需有關安全性組態支援 SSO，請參閱 「 企業單一登入可支援性的 Wcf-basichttp 接收配接器 > 一節中**Wcf-basichttp 傳輸屬性對話方塊、 接收、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。<br /><br /> 預設值︰ **False**|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用內容的 SOAP**主體**內送訊息建立 BizTalk 訊息內文部分的項目。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。<br />-   **UseEnvelope** -從整個 SOAP 建立 BizTalk 訊息內文部分 **信封** 內送訊息。<br />-   **UseBodyPath** -使用中的內文路徑運算式 **InboundBodyPathExpression** 屬性來建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 此屬性只對請求-回應連接埠有效。<br /><br /> 如需有關如何使用**InboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍 soap **主體** 內送 WCF 訊息的項目。<br /><br /> 預設值︰ **UseBodyElement**|  
|**InboundBodyPathExpression**|字串<br /><br /> 如需有關如何使用**InboundBodyPathExpression**屬性，請參閱[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。|指定內文路徑運算式來識別用於建立 BizTalk 訊息內文部分之內送訊息的特定部分。 此內文路徑運算式評估的 soap 的直系子項目 **主體** 內送訊息的節點。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。<br /><br /> 預設為空字串。|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -Base64 編碼方式。<br />-   **Hex** ︰ 十六進位編碼方式。<br />-   **字串** ︰ 文字編碼-utf-8<br />-   **XML** -WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml **InboundBodyPathExpression**。|指定的編碼 Wcf-basichttp 接收配接器，用來解碼中指定的內文路徑運算式所識別的節點類型 **InboundBodyPathExpression**。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。<br /><br /> 預設值︰ **XML**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用 BizTalk 訊息內文部分建立的 soap 內容**主體**外寄回應訊息的項目。<br />-   **UseTemplate** -使用中提供的範本 **OutboundXMLTemplate** 屬性來建立的內容的 soap **主體** 外寄回應訊息的項目。<br /><br /> 如需有關如何使用**OutboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍 soap **主體** 外寄 WCF 訊息的項目。 此屬性只適用於要求-回應接收位置。<br /><br /> 預設值︰ **UseBodyElement**|  
|**OutboundXMLTemplate**|字串<br /><br /> 如需有關如何使用**OutboundXMLTemplate**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定 XML 格式的範本內容的 SOAP **主體** 外寄回應訊息的項目。 如果這個屬性，則需要 **OutboundBodyLocation** 屬性設定為 **UseTemplate**。 此屬性只適用於要求-回應接收位置。<br /><br /> 預設為空字串。|  
|**SuspendMessageOnFailure**|Boolean|指定是否擱置因接收管線失敗或路由失敗而造成輸入處理失敗的要求訊息。<br /><br /> 預設值︰ **False**|  
|**IncludeExceptionDetailInFaults**|Boolean|指定基於偵錯目的傳回用戶端的 SOAP 錯誤詳細資料中，是否包括 Managed 例外狀況資訊。<br /><br /> 預設值︰ **False**|  
  
## <a name="configure-the-send-port-programmatically"></a>以程式設計方式設定傳送埠   

 下列程式碼片段說明如何建立 Wcf-basichttp 傳送埠使用 BizTalk 總管物件模型︰    
  
```  
// Use BizTalk Explorer object model to create new WCF-BasicHttp send port.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
                                 <StaticAction vt=""8"">http://www.northwindtraders.com/Service/Operation</StaticAction>  
                                 <MessageEncoding vt=""8"">Text</MessageEncoding>  
                                 <TextEncoding vt=""8"">utf-8</TextEncoding>  
                                 <OpenTimeout vt=""8"">00:01:00</OpenTimeout>  
                               </CustomProps>";  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  
// Add a new BizTalk application  
Application application = explorer.AddNewApplication();  
application.Name = "SampleBizTalkApplication";  
// Save  
explorer.SaveChanges();  
  
// Add a new static one-way send port  
SendPort sendPort = application.AddNewSendPort(false, false);   
sendPort.Name = "SampleSendPort";  
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-BasicHttp"];  
sendPort.PrimaryTransport.Address = "http://mycomputer/samplepath";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```    

您可以使用下列格式來設定屬性 `<CustomProps>`: 
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt="11">0</UseSSO>  
  <MessageClientCredentialType vt="8">UserName</MessageClientCredentialType>  
  <InboundBodyPathExpression vt="8" />  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">None</SecurityMode>  
  <TransportClientCredentialType vt="8">None</TransportClientCredentialType>  
  <ClientCertificate vt="8" />  
  <ProxyUserName vt="8" />  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <ProxyToUse vt="8">Default</ProxyToUse>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
  <ProxyAddress vt="8" />  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  

下表列出您可以設定傳送埠的組態屬性︰  
  
|屬性名稱|유형|Description|  
|-------------------|----------|-----------------|  
|**SecurityMode**|Enum<br /><br /> -   **無**<br />-   **訊息**<br />-   **傳輸**<br />-   **TransportWithMessageCredential**<br />-   **TransportCredentialOnly**<br /><br /> 如需有關成員名稱的**SecurityMode**屬性，請參閱**安全性模式**屬性**Wcf-basichttp 傳輸屬性對話方塊、 傳送、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定使用的安全性類型。<br /><br /> 預設值︰ **無**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **使用者名稱**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**MessageClientCredentialType**屬性，請參閱**訊息用戶端認證類型**屬性**Wcf-basichttp 傳輸屬性對話方塊方塊中，傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。<br /><br /> 預設值︰ **使用者名稱**|  
|**TransportClientCredentialType**|Enum<br /><br /> -   **無**<br />-   **基本**<br />-   **Windows**<br />-   **憑證**<br />-   **摘要**<br />-   **Ntlm**<br /><br /> 如需有關成員名稱的**TransportClientCredentialType**屬性，請參閱**傳輸用戶端認證類型**屬性**Wcf-basichttp 傳輸屬性對話方塊、 傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定在執行傳送埠驗證時，所要使用的認證類型。<br /><br /> 預設值︰ **無**|  
|**使用者名稱**|字串|指定要用於目的地伺服器驗證的使用者名稱時 **UseSSO** 屬性設定為 **False**。 您不需要對此屬性使用 domain\user 格式。<br /><br /> 預設為空字串。|  
|**密碼**|字串|指定要用於驗證目的地伺服器的密碼時 **UseSSO** 屬性設定為 **False**。<br /><br /> 預設為空字串。|  
|**AffiliateApplicationName**|字串|指定要針對企業單一登入 (SSO) 使用的分支機構應用程式。<br /><br /> 預設為空字串。|  
|**UseSSO**|Boolean|指定是否要使用「單一登入」來擷取用戶端認證，以供目的地伺服器驗證。<br /><br /> 預設值︰ **False**|  
|**ClientCertificate**|字串|指定 X.509 憑證的憑證指紋，以便向服務驗證此傳送埠。 如果這個屬性，則需要 **ClientCredentialsType** 屬性設定為 **憑證**。 要用於此屬性的憑證必須安裝到 **我** 存放 **目前使用者** 位置。<br /><br /> 預設為空字串。|  
|**ServiceCertificate**|字串|指定 X.509 憑證的指紋，以便驗證此傳送埠傳送訊息的目標服務。 要用於此屬性的憑證必須安裝到 **其他人** 存放 **本機** 位置。<br /><br /> 預設為空字串。|  
|**ProxyToUse**|Enum<br /><br /> -   **無**-此傳送埠，不使用 proxy 伺服器。<br />-   **預設** -裝載此傳送埠的傳送處理常式中使用的 proxy 設定。<br />-   **UserSpecified** -使用指定的 proxy 伺服器 **ProxyAddress** 屬性|指定要針對外寄 HTTP 流量使用哪一個 Proxy 伺服器。<br /><br /> 預設值︰ **無**|  
|**ProxyAddress**|字串|指定 Proxy 伺服器的位址。 使用 **https** 或 **http** 根據安全性組態的配置。 這個位址後面可以加上冒號和連接埠編號， 例如 http://127.0.0.1:8080 。<br /><br /> 預設為空字串。|  
|**ProxyUserName**|字串|指定要用於 Proxy 的使用者名稱。 Wcf-basichttp 配接器會利用 [BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086) 與端點進行通訊的緩衝的傳輸模式中。 Proxy 認證 **BasicHttpBinding** 都適用於只有當安全性模式是 **傳輸**, ，**無**, ，或 **TransportCredentialOnly**。 如果您設定 **SecurityMode** 屬性 **訊息** 或 **TransportWithMessageCredential**, ，Wcf-basichttp 配接器不會使用在指定的認證 **ProxyUserName** 和 **ProxyPassword** 驗證 proxy 的屬性。 **注意︰**  Wcf-basichttp 傳送配接器會使用基本驗證 proxy... <br /><br /> 預設為空字串。|  
|**ProxyPassword**|字串|指定要用於 Proxy 的密碼。<br /><br /> 預設為空字串。|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用內容的 SOAP**主體**內送訊息建立 BizTalk 訊息內文部分的項目。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。 此屬性只對請求-回應連接埠有效。<br />-   **UseEnvelope** -從整個 SOAP 建立 BizTalk 訊息內文部分 **信封** 內送訊息。<br />-   **UseBodyPath** -使用中的內文路徑運算式 **InboundBodyPathExpression** 屬性來建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 此屬性只對請求-回應連接埠有效。<br /><br /> 如需有關如何使用**InboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍 soap **主體** 內送 WCF 訊息的項目。<br /><br /> 預設值︰ **UseBodyElement**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用 BizTalk 訊息內文部分建立的 soap 內容**主體**外寄訊息的項目。<br />-   **UseTemplate** -使用中提供的範本 **OutboundXMLTemplate** 屬性來建立的內容的 soap **主體** 外寄訊息的項目。<br /><br /> 如需有關如何使用**OutboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍 soap **主體** 外寄 WCF 訊息的項目。<br /><br /> 預設值︰ **UseBodyElement**|  
|**InboundBodyPathExpression**|字串<br /><br /> 如需有關如何使用**InboundBodyPathExpression**屬性，請參閱[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。|指定內文路徑運算式來識別用於建立 BizTalk 訊息內文部分之內送訊息的特定部分。 此內文路徑運算式評估的 soap 的直系子項目 **主體** 內送訊息的節點。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設為空字串。|  
|**OutboundXMLTemplate**|字串<br /><br /> 如需有關如何使用**OutboundXMLTemplate**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定 XML 格式的範本內容的 SOAP **主體** 外寄訊息的項目。 如果這個屬性，則需要 **OutboundBodyLocation** 屬性設定為 **UseTemplate**。<br /><br /> 預設為空字串。|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -Base64 編碼方式。<br />-   **Hex** ︰ 十六進位編碼方式。<br />-   **字串** ︰ 文字編碼-utf-8<br />-   **XML** -WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml **InboundBodyPathExpression**。|指定的編碼 Wcf-basichttp 傳送配接器用來解碼中指定的內文路徑運算式所識別的節點類型 **InboundBodyPathExpression**。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值︰ **XML**|  
|**StaticAction**|字串|指定 **SOAPAction** 外寄訊息的 HTTP 標頭欄位。 這個屬性也可以透過訊息內容屬性設定 **WCF。動作** 管線或協調流程中。 您可以將這個值指定兩個不同的方式︰ 單一動作格式和動作對應格式。 如果您在單一動作格式中設定這個屬性 — 例如， http://contoso.com/Svc/Op1— **SOAPAction**標頭外寄訊息一定會設定這個屬性中指定的值。<br /><br /> 如果您設定此屬性以動作對應格式傳出 **SOAPAction** 標頭由 **BTS。作業** 內容屬性。 例如，如果此屬性設定為下列 XML 格式和**BTS。作業**屬性設定為 Op1，WCF 傳送配接器會使用http://contoso.com/Svc/Op1針對外寄**SOAPAction**標頭。<br /><br /> \<BtsActionMapping\><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /\><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /\><br /><br /> \</BtsActionMapping\><br /><br /> 協調流程執行個體如果外寄訊息是來自協調流程連接埠，以動態方式設定 **BTS。作業** 與連接埠的作業名稱的屬性。 如果外寄訊息會路由傳送，以內容為基礎的路由，您可以設定 **BTS。作業** 管線元件中的屬性。<br /><br /> 預設為空字串。|  
|**MaxReceivedMessageSize**|Integer|指定大小上限，以位元組為單位，在網路上可以接收的訊息 （包括標頭）。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> Wcf-basichttp 配接器會利用 [BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086) 與端點進行通訊的緩衝的傳輸模式中的類別。 緩衝的傳輸模式下， [BasicHttpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=80659) 屬性會一律等於這個屬性的值。<br /><br /> 預設值︰ 65536|  
|**MessageEncoding**|Enum<br /><br /> -   **文字**-使用文字訊息編碼器。<br />-   **Mtom** -使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。|指定用來為 SOAP 訊息編碼的編碼器。<br /><br /> 預設值︰ **文字**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** -Unicode BigEndian 編碼方式。<br />-   **utf-16** -16 位元編碼方式。<br />-   **utf-8** -8 位元編碼方式|指定字元集的編碼方式來繫結上發出訊息時 **MessageEncoding** 屬性設定為 **文字**。<br /><br /> 預設值︰ **utf-8**|  
|**SendTimeout**|**System.TimeSpan**|指定時間值，表示可供完成傳送作業的時間間隔。 如果您使用請求-回應傳送埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00|  
|**OpenTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道開啟作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道關閉作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**AlgorithmSuite**|Enum<br /><br /> 如需有關成員名稱的**AlgorithmSuite**屬性，請參閱**演算法套件**屬性**Wcf-basichttp 傳輸屬性對話方塊、 傳送、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。<br /><br /> 預設值︰ **Basic256**|  
|**身分識別**|XML BLOB<br /><br /> 範例︰<br /><br /> &lt;身分識別&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|指定此傳送埠所預期服務的識別。 這些設定可讓此傳送埠驗證服務。 在用戶端與服務之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別能夠與這個項目的值相符。<br /><br /> 預設為空字串。|  
|**PropagateFaultMessage**|Boolean<br /><br /> -   **True** -路由傳送訊息至訂閱應用程式的輸出處理失敗 （例如其他接收埠或協調流程排程）。<br />-   **False** -擱置失敗的訊息，並產生負值通知 (NACK)。|指定要路由傳送或擱置在輸出處理中失敗的訊息。<br /><br /> 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值︰ **，則為 True**|  
  
## <a name="see-also"></a>另請參閱  
 [何謂 WCF 配接器？](../core/what-are-the-wcf-adapters.md)  
 [發佈 WCF 服務，利用外掛式 WCF 接收配接器](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)   
 [設定 IIS 的外掛式 WCF 接收配接器](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)   
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [如何變更服務帳戶和密碼](../core/how-to-change-service-accounts-and-passwords.md)   
 [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)   
 [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)    
  [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [使用 WCF 配接器內容屬性設定動態傳送埠](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)