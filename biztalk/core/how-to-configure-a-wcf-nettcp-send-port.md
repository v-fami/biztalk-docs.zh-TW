---
title: "如何設定 Wcf-nettcp 傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8fff07e-b08e-4f95-8ce2-27b508674a5c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f46c4b521c754bd2096916a03e356262dfa4d46
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-a-wcf-nettcp-send-port"></a>如何設定 WCF-NetTcp 傳送埠
您可以透過程式設計方式或使用 [BizTalk 管理主控台] 來設定 WCF-NetTcp 傳送埠。  
  
## <a name="configuration-properties"></a>組態屬性
  
 BizTalk 總管物件模型公開 （expose) 名為傳送埠的配接器特定介面**ITransportInfo**具有**TransportTypeData**讀/寫屬性。 這個屬性會以 XML 字串成對的名稱-數值格式接受 WCF-NetTcp 傳送埠組態屬性包。  
  
 **TransportTypeData**屬性**ITransportInfo**介面並非必要。 如果沒有設定此屬性，配接器就會針對 WCF-NetTcp 傳送埠組態使用預設值，如下表所示。  
  
 下表列出您可以在 [BizTalk 總管物件模型] 中針對 WCF-NetTcp 傳送埠設定的組態屬性。  
  
|屬性名稱|類型|Description|  
|-------------------|----------|-----------------|  
|**識別**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;身分識別&gt;<br /><br /> &lt;userPrincipalName 值 ="username@contoso.com"/&gt;<br /><br /> &lt;/identity&gt;|指定此傳送埠所預期服務的識別。 這些設定可讓此傳送埠驗證服務。 在用戶端與服務之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別能夠與這個項目的值相符。<br /><br /> 預設為空字串。|  
|**StaticAction**|字串|指定**SOAPAction**外寄訊息的標頭欄位。 這個屬性也可以透過訊息內容屬性設定**WCF。動作**管線或協調流程中。 您可以將這個值指定兩個不同的方式： 單一動作格式和動作對應格式。 如果您在單一動作格式中設定這個屬性 — 例如，http://contoso.com/Svc/Op1 — **SOAPAction**標頭外寄訊息一定會設定這個屬性中指定的值。<br /><br /> 如果您設定此屬性以動作對應格式，傳出**SOAPAction**標頭由**BTS。作業**內容屬性。 例如，如果此屬性設定為下列 XML 格式和**BTS。作業**屬性設定為 Op1，WCF 傳送配接器使用 http://contoso.com/Svc/Op1 針對外寄**SOAPAction**標頭。<br /><br /> \<B\><br /><br /> \<作業名稱 ="Op1 」 動作 ="http://contoso.com/Svc/Op1"/\><br /><br /> \<作業名稱 ="Op2 」 動作 ="http://contoso.com/Svc/Op2"/\><br /><br /> \</ B\><br /><br /> 如果外寄訊息是來自協調流程連接埠，協調流程執行個體動態設定**BTS。作業**與連接埠的作業名稱的屬性。 如果外寄訊息都會路由傳送，以內容為基礎的路由，您可以設定**BTS。作業**管線元件中的屬性。<br /><br /> 預設為空字串。|  
|**OpenTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道開啟作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**SendTimeout**|**System.TimeSpan**|指定時間值，表示可供完成傳送作業的時間間隔。 如果您使用請求-回應傳送埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道關閉作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**MaxReceivedMessageSize**|Integer|指定大小上限，以位元組為單位，可以從網路收到的訊息 （包括標頭）。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> Wcf-nettcp 配接器會利用[NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087)類別與端點進行通訊的緩衝的傳輸模式中。 緩衝的傳輸模式下， [NetTcpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=81088)屬性會一律等於這個屬性的值。<br /><br /> 預設值：65536|  
|**EnableTransaction**|布林|指定訊息時是否傳送至目的地服務，並從交易內容中指定的交易通訊協定的使用中的 MessageBox 資料庫刪除**TransactionProtocol**屬性。<br /><br /> 預設值： **False**|  
|**TransactionProtocol**|Enum<br /><br /> -   **OleTransaction**<br />-   **Ws-atomictransaction**|指定要搭配此繫結使用的交易通訊協定。<br /><br /> 預設值： **OleTransaction**|  
|**SecurityMode**|Enum<br /><br /> -   **無**<br />-   **訊息**<br />-   **傳輸**<br />-   **TransportWithMessageCredential**<br /><br /> 如需有關成員名稱的**SecurityMode**屬性，請參閱**安全性模式**屬性**Wcf-nettcp 傳輸屬性對話方塊、 傳送、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定使用的安全性類型。<br /><br /> 預設值：**傳輸**|  
|**TransportClientCredentialType**|Enum<br /><br /> -   **無**<br />-   **Windows**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**TransportClientCredentialType**屬性，請參閱**傳輸用戶端認證類型**屬性**Wcf-nettcp 傳輸屬性對話方塊、 傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定在執行傳送埠驗證時，所要使用的認證類型。<br /><br /> 預設值： **Windows**|  
|**TransportProtectionLevel**|Enum<br /><br /> -   **無**-沒有保護。<br />-   **符號**-簽署訊息。<br />-   **EncryptAndSign** -加密及簽署訊息。|指定在 TCP 傳輸層的安全性。 簽署訊息可以降低訊息在傳輸時遭到第三者竄改的風險。 加密可在傳輸時提供資料等級的隱私權。<br /><br /> 預設值： **EncryptAndSign**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **無**<br />-   **Windows**<br />-   **使用者名稱**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**MessageClientCredentialType**屬性，請參閱**訊息用戶端認證類型**屬性**Wcf-nettcp 傳輸屬性對話方塊方塊中，傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。<br /><br /> 預設值： **Windows**|  
|**AlgorithmSuite**|Enum<br /><br /> 如需有關成員名稱的**AlgorithmSuite**屬性，請參閱**演算法套件**屬性**Wcf-nettcp 傳輸屬性對話方塊、 傳送、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。<br /><br /> 預設值： **Basic256**|  
|**ClientCertificate**|字串|指定 X.509 憑證的憑證指紋，以便向服務驗證此傳送埠。 如果這個屬性，則需要**ClientCredentialsType**屬性設定為**憑證**。 要用於此屬性的憑證必須安裝到**我**存放**目前使用者**位置。<br /><br /> 預設為空字串。|  
|**AffiliateApplicationName**|字串|指定要針對企業單一登入 (SSO) 使用的分支機構應用程式。<br /><br /> 預設為空字串。|  
|**UseSSO**|布林|指定是否要使用「單一登入」來擷取用戶端認證，以供目的地伺服器驗證。<br /><br /> 預設值： **False**|  
|**UserName**|字串|指定要用於目的地伺服器驗證的使用者名稱時**UseSSO**屬性設定為**False**。 您不需要對此屬性使用 domain\user 格式。<br /><br /> 預設為空字串。|  
|**密碼**|字串|指定要用於目的地伺服器驗證的密碼時**UseSSO**屬性設定為**False**。<br /><br /> 預設為空字串。|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用 BizTalk 訊息內文部分建立的 soap 內容**主體**外寄訊息的項目。<br />-   **UseTemplate** -使用中提供的範本**OutboundXMLTemplate**屬性，建立內容的 SOAP**主體**外寄訊息的項目。<br /><br /> 如需有關如何使用**OutboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍，soap**主體**外寄 WCF 訊息的項目。<br /><br /> 預設值： **UseBodyElement**|  
|**OutboundXMLTemplate**|字串<br /><br /> 如需有關如何使用**OutboundXMLTemplate**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定 XML 格式的範本內容的 SOAP**主體**外寄訊息的項目。 如果這個屬性，則需要**OutboundBodyLocation**屬性設定為**UseTemplate**。<br /><br /> 預設為空字串。|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用內容的 SOAP**主體**內送訊息建立 BizTalk 訊息內文部分的項目。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。 此屬性只對請求-回應連接埠有效。<br />-   **UseEnvelope** -建立 BizTalk 訊息內文部分的整個 SOAP 從**信封**內送訊息。<br />-   **UseBodyPath** -使用中的內文路徑運算式**InboundBodyPathExpression**屬性以建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 此屬性只對請求-回應連接埠有效。<br /><br /> 如需有關如何使用**InboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍，soap**主體**內送 WCF 訊息的項目。<br /><br /> 預設值： **UseBodyElement**|  
|**InboundBodyPathExpression**|字串<br /><br /> 如需有關如何使用**InboundBodyPathExpression**屬性，請參閱[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。|指定內文路徑運算式來識別用於建立 BizTalk 訊息內文部分之內送訊息的特定部分。 此內文路徑運算式評估的 soap 的直系子元素**主體**節點內送訊息。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果這個屬性，則需要**InboundBodyLocation**屬性設定為**UseBodyPath**。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設為空字串。|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **XML**<br />-   **Base64** -Base64 編碼方式。<br />-   **Hex** ： 十六進位編碼。<br />-   **字串**： 文字編碼-utf-8。<br />-   **XML** -WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml **InboundBodyPathExpression**。|指定 Wcf-nettcp 傳送配接器中指定之 XPath 所識別的節點用來解碼的編碼類型**InboundBodyPathExpression**。 如果這個屬性，則需要**InboundBodyLocation**屬性設定為**UseBodyPath**。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值： **XML**|  
|**PropagateFaultMessage**|布林<br /><br /> -   **True** -路由傳送訊息至訂閱應用程式的輸出處理失敗 （例如其他接收埠或協調流程排程）。<br />-   **False** -擱置失敗的訊息，並產生負值通知 (NACK)。|指定要路由傳送或擱置在輸出處理中失敗的訊息。<br /><br /> 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值： **，則為 True**|  
  
 **如何使用 BizTalk 管理主控台中設定 Wcf-nettcp 傳送埠**  
  
 您可以在 [BizTalk 管理主控台] 中設定 WCF-NetTcp 傳送埠配接器變數。 如果沒有設定傳送埠的屬性，系統就會針對 WCF-NetTcp 傳送埠組態使用預設值，如上表所示。  
  
## <a name="configure-variables-for-a-wcf-nettcp-send-port"></a>設定 Wcf-nettcp 傳送埠的變數  
  
1.  在 [BizTalk 管理主控台] 中建立新的傳送埠，或按兩下現有的傳送埠進行修改。 如需詳細資訊，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有傳送埠選項，並指定**Wcf-nettcp**如**類型**選項**傳輸**區段**一般**索引標籤。  
  
2.  在**一般**索引標籤的**傳輸**區段中，按一下**設定**旁邊**類型**。  
  
3.  在**Wcf-nettcp 傳輸屬性**對話方塊**一般**索引標籤上，設定端點位址、 服務識別和**SOAPAction**標頭Wcf-nettcp 傳送埠。 如需有關**一般**索引標籤中**Wcf-nettcp 傳輸屬性**對話方塊中，請參閱**Wcf-nettcp 傳輸屬性對話方塊、 傳送、 一般**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
4.  在**Wcf-nettcp 傳輸屬性**對話方塊**繫結**索引標籤上，設定逾時和交易屬性。 如需有關**繫結**索引標籤中**Wcf-nettcp 傳輸屬性**對話方塊中，請參閱**Wcf-nettcp 傳輸屬性對話方塊、 傳送、 繫結**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
5.  在**Wcf-nettcp 傳輸屬性**對話方塊**安全性**索引標籤上，定義 Wcf-nettcp 傳送埠的安全性功能。 如需有關**安全性**索引標籤中**Wcf-nettcp 傳輸屬性**對話方塊中，請參閱**Wcf-nettcp 傳輸屬性對話方塊、 傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
6.  在**Wcf-nettcp 傳輸屬性**對話方塊**訊息**索引標籤上，指定 SOAP 資料選取範圍**主體**項目。 如需有關**訊息**索引標籤中**Wcf-nettcp 傳輸屬性**對話方塊中，請參閱**Wcf-nettcp 傳輸屬性對話方塊、 傳送、 訊息** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="configure-a-wcf-nettcp-send-port-programmatically"></a>以程式設計方式設定 Wcf-nettcp 傳送埠
  
 您可以使用下列格式來設定屬性：  
  
 \<CustomProps\>  
  
```  
  <UseSSO vt="11">0</UseSSO>  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <InboundBodyPathExpression vt="8" />  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">Transport</SecurityMode>  
  <TransportClientCredentialType vt="8">Windows</TransportClientCredentialType>  
  <ClientCertificate vt="8" />  
  <TransactionProtocol vt="8">OleTransactions</TransactionProtocol>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <TransportProtectionLevel vt="8">EncryptAndSign</TransportProtectionLevel>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <EnableTransaction vt="11">0</EnableTransaction>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 下列程式碼片段說明如何建立 WCF-NetTcp 傳送埠：  
  
```  
// Use BizTalk Explorer object model to create new WCF-NetTcp send port.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
                                 <StaticAction vt=""8"">http://www.northwindtraders.com/Service/Operation</StaticAction>  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-NetTcp"];  
sendPort.PrimaryTransport.Address = "net.tcp://mycomputer/private/samplequeue";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```  
  
## <a name="see-also"></a>請參閱  
 [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)   
 [設定 Wcf-nettcp 配接器](../core/configuring-the-wcf-nettcp-adapter.md)   
 [使用 WCF 配接器內容屬性設定動態傳送埠](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)