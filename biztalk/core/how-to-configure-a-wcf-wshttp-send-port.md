---
title: 如何設定 Wcf-wshttp 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 035d9a62-b8a3-4705-a7bc-b62676437206
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f5fc7b26877f840de491176beab70e7191ad57e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-configure-a-wcf-wshttp-send-port"></a>如何設定 WCF-WSHttp 傳送埠
您可以用程式設計方式或使用 BizTalk 管理主控台來設定 WCF-WSHttp 傳送埠。  
  
## <a name="configuration-properties"></a>組態屬性
  
 BizTalk 總管物件模型公開 （expose) 名為傳送埠的配接器特定介面 **ITransportInfo** 具有 **TransportTypeData** 讀/寫屬性。 這項屬性會以 XML 字串之名稱-值配對的格式接受 WCF-WSHttp 傳送埠組態屬性包。  
  
 **TransportTypeData** 屬性 **ITransportInfo** 介面並非必要。 如果沒有設定此屬性，配接器就會針對 WCF-WSHttp 傳送埠組態使用預設值，如下所示。  
  
 下表將列出您可以在 BizTalk 總管物件模型中針對 WCF-WSHttp 傳送埠設定的組態屬性。  
  
|屬性名稱|유형|Description|  
|-------------------|----------|-----------------|  
|**身分識別**|XML BLOB<br /><br /> 範例︰<br /><br /> &lt;身分識別&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|指定此傳送埠所預期服務的識別。 這些設定可讓此傳送埠驗證服務。 在用戶端與服務之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別能夠與這個項目的值相符。<br /><br /> 預設為空字串。|  
|**StaticAction**|-字串|指定 **SOAPAction** 外寄訊息的 HTTP 標頭欄位。 這個屬性也可以透過訊息內容屬性設定 **WCF。動作** 管線或協調流程中。 您可以將這個值指定兩個不同的方式︰ 單一動作格式和動作對應格式。 如果您在設定此屬性的單一動作格式-例如， http://contoso.com/Svc/Op1- **SOAPAction**標頭外寄訊息一定會設定這個屬性中指定的值。<br /><br /> 如果您設定此屬性以動作對應格式傳出 **SOAPAction** 標頭由 **BTS。作業** 內容屬性。 例如，如果此屬性設定為下列 XML 格式和**BTS。作業**屬性設定為 Op1，WCF 傳送配接器會使用http://contoso.com/Svc/Op1針對外寄**SOAPAction**標頭。<br /><br /> \<BtsActionMapping\><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /\><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /\><br /><br /> \</BtsActionMapping\><br /><br /> 協調流程執行個體如果外寄訊息是來自協調流程連接埠，以動態方式設定 **BTS。作業** 與連接埠的作業名稱的屬性。 如果外寄訊息會路由傳送，以內容為基礎的路由，您可以設定 **BTS。作業** 管線元件中的屬性。<br /><br /> 預設為空字串。|  
|**OpenTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道開啟作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**SendTimeout**|**System.TimeSpan**|指定時間值，表示可供完成傳送作業的時間間隔。 如果您使用請求-回應傳送埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道關閉作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**MaxReceivedMessageSize**|Integer|指定大小上限，以位元組為單位，在網路上可以接收的訊息 （包括標頭）。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> 預設值：65536|  
|**MessageEncoding**|Enum<br /><br /> -   **文字**-使用文字訊息編碼器。<br />-   **Mtom** -使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。|指定用來為 SOAP 訊息編碼的編碼器。<br /><br /> 預設值︰ **文字**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** -Unicode BigEndian 編碼方式。<br />-   **utf-16** -16 位元編碼方式。<br />-   **utf-8** -8 位元編碼方式。|指定字元集的編碼方式來繫結上發出訊息時 **MessageEncoding** 屬性設定為 **文字**。<br /><br /> 預設值︰ **utf-8**|  
|**EnableTransaction**|Boolean|指定訊息時是否傳送至目的地服務，並從在交易內容中使用的 MessageBox 資料庫中刪除 **Ws-atomictransaction** 通訊協定。<br /><br /> 預設值︰ **False**|  
|**SecurityMode**|Enum<br /><br /> -   **無**<br />-   **訊息**<br />-   **傳輸**<br />-   **TransportWithMessageCredential**<br /><br /> 如需有關成員名稱的**SecurityMode**屬性，請參閱**安全性模式**屬性**Wcf-wshttp 傳輸屬性對話方塊、 傳送、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定使用的安全性類型。<br /><br /> 預設值︰ **無**|  
|**TransportClientCredentialType**|Enum<br /><br /> -   **無**<br />-   **基本**<br />-   **Windows**<br />-   **憑證**<br />-   **摘要**<br />-   **Ntlm**<br /><br /> 如需有關成員名稱的**TransportClientCredentialType**屬性，請參閱**傳輸用戶端認證類型**屬性**Wcf-wshttp 傳輸屬性對話方塊、 傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定在執行傳送埠驗證時，所要使用的認證類型。<br /><br /> 預設值︰ **無**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **無**<br />-   **Windows**<br />-   **使用者名稱**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**MessageClientCredentialType**屬性，請參閱**訊息用戶端認證類型**屬性**Wcf-wshttp 傳輸屬性對話方塊方塊中，傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。<br /><br /> 預設值︰ **使用者名稱**|  
|**AlgorithmSuite**|Enum<br /><br /> 如需有關成員名稱的**AlgorithmSuite**屬性，請參閱**演算法套件**屬性**Wcf-wshttp 傳輸屬性對話方塊、 傳送、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。<br /><br /> 預設值︰ **Basic256**|  
|**NegotiateServiceCredential**|布林<br /><br /> 如需有關成員名稱的**NegotiateServiceCredential**屬性，請參閱**交涉服務認證**屬性**Wcf-wshttp 傳輸屬性對話方塊方塊中，傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定是否會在超出範圍的傳送埠提供此服務認證，或是透過交涉程序從此服務取得服務認證給這個傳送埠。 這類交涉是一般訊息交換的先驅。<br /><br /> 預設值︰ **False**|  
|**EnableSecurityContext**|Boolean|指定是否透過建立安全性內容權杖 **Ws-secureconversation** 此傳送埠和服務之間的交換。 如果這個屬性設定為 **True** 目的地服務必須支援 **Ws-secureconversation**。<br /><br /> 預設值︰ **，則為 True**|  
|**ClientCertificate**|字串|指定 X.509 憑證的憑證指紋，以便向服務驗證此傳送埠。 如果這個屬性，則需要 **ClientCredentialsType** 屬性設定為 **憑證**。 要用於此屬性的憑證必須安裝到 **我** 存放 **目前使用者** 位置。<br /><br /> 預設為空字串。|  
|**ServiceCertificate**|字串|指定 X.509 憑證的指紋，以便驗證此傳送埠傳送訊息的目標服務。 要用於此屬性的憑證必須安裝到 **其他人** 存放 **本機** 位置。<br /><br /> 預設為空字串。|  
|**AffiliateApplicationName**|字串|指定要針對企業單一登入 (SSO) 使用的分支機構應用程式。<br /><br /> 預設為空字串。|  
|**UseSSO**|Boolean|指定是否要使用「單一登入」來擷取用戶端認證，以供目的地伺服器驗證。<br /><br /> 預設值︰ **False**|  
|**使用者名稱**|字串|指定要用於目的地伺服器驗證的使用者名稱時 **UseSSO** 屬性設定為 **False**。 您不需要對此屬性使用 domain\user 格式。<br /><br /> 預設為空字串。|  
|**密碼**|字串|指定要用於驗證目的地伺服器的密碼時 **UseSSO** 屬性設定為 **False**。<br /><br /> 預設為空字串。|  
|**ProxyToUse**|Enum<br /><br /> -   **無**-此傳送埠，不使用 proxy 伺服器。<br />-   **預設** -裝載此傳送埠的傳送處理常式中使用的 proxy 設定。<br />-   **UserSpecified** -使用指定的 proxy 伺服器 **ProxyAddress** 屬性。|指定要針對外寄 HTTP 流量使用哪一個 Proxy 伺服器。<br /><br /> 預設值︰ **無**|  
|**ProxyAddress**|字串|指定 Proxy 伺服器的位址。 使用 **https** 或 **http** 根據安全性組態的配置。 這個位址後面可以加上冒號和連接埠編號， 例如 http://127.0.0.1:8080 。<br /><br /> 預設為空字串。|  
|**ProxyUserName**|字串|指定要用於 Proxy 的使用者名稱。 Wcf-wshttp 配接器會利用 [WSHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81206) 與端點進行通訊的緩衝的傳輸模式中。 Proxy 認證 **WSHttpBinding** 都適用於只有當安全性模式是 **傳輸**, ，或 **無**。 如果您設定 **SecurityMode** 屬性 **訊息** 或 **TransportWithMessageCredential**, ，Wcf-wshttp 配接器不會使用在指定的認證 **ProxyUserName** 和 **ProxyPassword** 驗證 proxy 的屬性。 **注意︰**  Wcf-wshttp 傳送配接器會使用 proxy 的基本驗證。 <br /><br /> 預設為空字串。|  
|**ProxyPassword**|字串|指定要用於 Proxy 的密碼。<br /><br /> 預設為空字串。|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用 BizTalk 訊息內文部分建立的 soap 內容**主體**外寄訊息的項目。<br />-   **UseTemplate** -使用中提供的範本 **OutboundXMLTemplate** 屬性來建立的內容的 soap **主體** 外寄訊息的項目。<br /><br /> 如需有關如何使用**OutboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍 soap **主體** 外寄 WCF 訊息的項目。<br /><br /> 預設值︰ **UseBodyElement**|  
|**OutboundXMLTemplate**|字串<br /><br /> 如需有關如何使用**OutboundXMLTemplate**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定 XML 格式的範本內容的 SOAP **主體** 外寄訊息的項目。 如果這個屬性，則需要 **OutboundBodyLocation** 屬性設定為 **UseTemplate**。<br /><br /> 預設為空字串。|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用內容的 SOAP**主體**內送訊息建立 BizTalk 訊息內文部分的項目。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。 此屬性只對請求-回應連接埠有效。<br />-   **UseEnvelope** -從整個 SOAP 建立 BizTalk 訊息內文部分 **信封** 內送訊息。<br />-   **UseBodyPath** -使用中的內文路徑運算式 **InboundBodyPathExpression** 屬性來建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 此屬性只對請求-回應連接埠有效。<br /><br /> 如需有關如何使用**InboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍 soap **主體** 內送 WCF 訊息的項目。<br /><br /> 預設值︰ **UseBodyElement**|  
|**InboundBodyPathExpression**|字串<br /><br /> 如需有關如何使用**InboundBodyPathExpression**屬性，請參閱[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。|指定內文路徑運算式來識別用於建立 BizTalk 訊息內文部分之內送訊息的特定部分。 此內文路徑運算式評估的 soap 的直系子項目 **主體** 內送訊息的節點。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設為空字串。|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -Base64 編碼方式。<br />-   **Hex** ︰ 十六進位編碼方式。<br />-   **字串** ︰ 文字編碼-utf-8。<br />-   **XML** -WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml **InboundBodyPathExpression**。|指定 Wcf-wshttp 傳送配接器中指定的內文路徑所識別的節點用來解碼的編碼類型 **InboundBodyPathExpression**。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值︰ **XML**|  
|**PropagateFaultMessage**|Boolean<br /><br /> -   **True** -路由傳送訊息至訂閱應用程式的輸出處理失敗 （例如其他接收埠或協調流程排程）。<br />-   **False** -擱置失敗的訊息，並產生負值通知 (NACK)。|指定要路由傳送或擱置在輸出處理中失敗的訊息。<br /><br /> 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值︰ **，則為 True**|  
  
## <a name="configure-a-wcf-wshttp-send-port-with-the-biztalk-administration-console"></a>使用 BizTalk 管理主控台中設定 Wcf-wshttp 傳送埠
  
 您可以在 BizTalk 管理主控台中設定 WCF-WSHttp 傳送埠配接器變數。 如果沒有設定傳送埠的屬性，系統就會針對 WCF-WSHttp 傳送埠組態使用預設值，如上表所示。  
  
## <a name="configure-variables-for-a-wcf-wshttp-send-port"></a>設定 Wcf-wshttp 傳送埠的變數  
  
1.  在 [BizTalk 管理主控台] 中建立新的傳送埠，或按兩下現有的傳送埠進行修改。 如需詳細資訊，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有傳送埠選項，並指定 **Wcf-wshttp** 的 **類型** 選項 **傳輸** 區段 **一般**  索引標籤。  
  
2.  在 **一般** 索引標籤的 **傳輸** 區段中，按一下 **設定** 旁 **類型**。  
  
3.  在 **Wcf-wshttp 傳輸屬性** 對話方塊的  **一般** 索引標籤上，設定端點位址、 服務識別和 **SOAPAction** Wcf-wshttp 傳送埠的 HTTP 標頭。 如需有關**一般**索引標籤中**Wcf-wshttp 傳輸屬性**對話方塊中，請參閱**Wcf-wshttp 傳輸屬性對話方塊、 傳送、 一般**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
4.  在 **Wcf-wshttp 傳輸屬性** 對話方塊的  **繫結** 索引標籤上，設定逾時、 編碼和交易屬性。 如需有關**繫結**索引標籤中**Wcf-wshttp 傳輸屬性**對話方塊中，請參閱**Wcf-wshttp 傳輸屬性對話方塊、 傳送、 繫結**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
5.  在 **Wcf-wshttp 傳輸屬性** 對話方塊的  **安全性** 索引標籤上，定義 Wcf-wshttp 傳送埠的安全性功能。 如需有關**安全性**索引標籤中**Wcf-wshttp 傳輸屬性**對話方塊中，請參閱**Wcf-wshttp 傳輸屬性對話方塊、 傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
6.  在 **Wcf-wshttp 傳輸屬性** 對話方塊的  **Proxy** 索引標籤上，設定的 proxy 設定 Wcf-wshttp 傳送埠。 如需有關**Proxy**索引標籤中**Wcf-wshttp 傳輸屬性**對話方塊中，請參閱**Wcf-wshttp 傳輸屬性對話方塊、 傳送、 Proxy**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
7.  在 **Wcf-wshttp 傳輸屬性** 對話方塊的  **訊息** 索引標籤上，指定資料選取範圍 soap **主體** 項目。 如需有關**訊息**索引標籤中**Wcf-wshttp 傳輸屬性**對話方塊中，請參閱**Wcf-wshttp 傳輸屬性對話方塊、 傳送、 訊息** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="configure-a-wcf-wshttp-send-port-programmatically"></a>以程式設計方式設定 Wcf-wshttp 傳送埠
  
 您可以使用下列格式來設定屬性：  

```  
 <CustomProps>    
  <ServiceCertificate vt="8" />  
  <UseSSO vt="11">0</UseSSO>  
  <InboundBodyPathExpression vt="8" />  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <Identity vt="8" />  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">Message</SecurityMode>  
  <TransportClientCredentialType vt="8">Windows</TransportClientCredentialType>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <NegotiateServiceCredential vt="11">-1</NegotiateServiceCredential>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <ClientCertificate vt="8" />  
  <ProxyUserName vt="8" />  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <ProxyToUse vt="8">Default</ProxyToUse>  
  <EnableTransaction vt="11">0</EnableTransaction>  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <EstablishSecurityContext vt="11">-1</EstablishSecurityContext>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
  <ProxyAddress vt="8" />  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 下列程式碼片段會說明如何建立 WCF-WSHttp 傳送埠：  
  
```  
// Use BizTalk Explorer object model to create new WCF-WSHttp send port.  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-WSHttp"];  
sendPort.PrimaryTransport.Address = "http://mycomputer/samplepath";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```  
  
## <a name="see-also"></a>另請參閱  
 [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [設定 Wcf-wshttp 配接器](../core/configuring-the-wcf-wshttp-adapter.md)   
 [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)   
 [使用 WCF 配接器內容屬性設定動態傳送埠](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)