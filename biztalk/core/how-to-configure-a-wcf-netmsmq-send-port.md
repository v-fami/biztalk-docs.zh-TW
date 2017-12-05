---
title: "如何設定 Wcf-netmsmq 傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13f55e53-12af-473b-b73f-1c98edadfc28
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48ad9e8f7ce806e0570877702fbccb432ca2946a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-a-wcf-netmsmq-send-port"></a>如何設定 WCF-NetMsmq 傳送埠
您可以透過程式設計方式或使用 BizTalk 管理主控台來設定 WCF-NetMsmq 傳送埠。  
  
## <a name="configuration-properties"></a>組態屬性
  
 BizTalk 總管物件模型公開 （expose) 名為傳送埠的配接器特定介面**ITransportInfo**具有**TransportTypeData**讀/寫屬性。 這個屬性會以名稱-值配對的 XML 字串格式接受 WCF-NetMsmq 傳送埠組態屬性包。  
  
 **TransportTypeData**屬性**ITransportInfo**介面並非必要。 如果沒有設定此屬性，配接器就會針對 WCF-NetMsmq 傳送埠組態使用如下表所示的預設值。  
  
 下表列出您可以在 BizTalk 總管物件模型中針對 WCF-NetMsmq 傳送埠設定的組態屬性。  
  
|屬性名稱|類型|Description|  
|-------------------|----------|-----------------|  
|**識別**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;身分識別&gt;<br /><br /> &lt;userPrincipalName 值 ="username@contoso.com"/&gt;<br /><br /> &lt;/identity&gt;|指定此傳送埠所預期服務的識別。 這些設定可讓此傳送埠驗證服務。 在用戶端與服務之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別能夠與這個項目的值相符。<br /><br /> 預設為空字串。|  
|**StaticAction**|字串|指定**SOAPAction**外寄訊息的標頭欄位。 這個屬性也可以透過訊息內容屬性設定**WCF。動作**管線或協調流程中。 您可以將這個值指定兩個不同的方式： 單一動作格式和動作對應格式。 如果您設定這個屬性中的單一動作格式-例如，http://contoso.com/Svc/Op1- **SOAPAction**標頭外寄訊息一定會設定這個屬性中指定的值。<br /><br /> 如果您設定此屬性以動作對應格式，傳出**SOAPAction**標頭由**BTS。作業**內容屬性。 例如，如果此屬性設定為下列 XML 格式和**BTS。作業**屬性設定為 Op1，WCF 傳送配接器使用 http://contoso.com/Svc/Op1 針對外寄**SOAPAction**標頭。<br /><br /> \<B\><br /><br /> \<作業名稱 ="Op1 」 動作 ="http://contoso.com/Svc/Op1"/\><br /><br /> \<作業名稱 ="Op2 」 動作 ="http://contoso.com/Svc/Op2"/\><br /><br /> \</ B\><br /><br /> 如果外寄訊息是來自協調流程連接埠，協調流程執行個體動態設定**BTS。作業**與連接埠的作業名稱的屬性。 如果外寄訊息都會路由傳送，以內容為基礎的路由，您可以設定**BTS。作業**管線元件中的屬性。<br /><br /> 預設為空字串。|  
|**OpenTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道開啟作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**SendTimeout**|**System.TimeSpan**|指定時間值，表示可供完成傳送作業的時間間隔。 如果您使用請求-回應傳送埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道關閉作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**EnableTransactional**|布林|指定目的地服務的訊息佇列的類型： 交易式或非交易式。 如果這個屬性設定為**True**、 每個此傳送埠所處理的訊息只傳遞一次，而且寄件者會通知傳遞失敗。 若要透過交易式傳送的訊息傳送埠兩者**持久**和**exactlyOnce**繫結的服務項目必須設定為**True**。 如果這個屬性設定為**False**，訊息會傳送傳遞保證。<br /><br /> 預設值： **，則為 True**|  
|**DeadLetterQueue**|Enum<br /><br /> -   **無**-沒有寄不出的信件佇列是用來。<br />-   **系統**-使用整個系統的寄不出信件佇列。<br />-   **自訂**-使用自訂的寄不出信件佇列。|指定無法傳遞到應用程式的訊息將會傳輸到的無效信件佇列。 如需有關訊息傳遞至寄不出信件佇列的詳細資訊，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 傳送、 繫結** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。<br/><br/> **請注意**： 自訂寄不出信件佇列支援只在訊息佇列 (MSMQ) 4.0 中，隨著 Windows Vista 發行。 <br /><br /> 預設值：**系統**|  
|**CustomDeadLetterQueue**|字串|指定完整格式的 URI，連同**net.msmq**配置位置的每個應用程式寄不出信件佇列中，已過期、 無法傳輸或傳遞的郵件放置的位置。 例如，net.msmq://localhost/deadLetterQueueName。 無法寄出的信件佇列是傳送端應用程式之佇列管理員上的佇列，適用於傳遞失敗的過期訊息。 如果這個屬性，則需要**DeadLetterQueue**屬性設定為**自訂**。<br /><br /> 預設為空字串。|  
|**TimeToLive**|**System.TimeSpan**|指定訊息在過期並置入無效信件佇列之前的有效時間有多長。 設定這個屬性可確保時間緊迫的訊息，在由此傳送埠處理之前不會已經過時。 在佇列中的訊息，若是沒有在指定的時間間隔內由此傳送埠耗用，便會被視為過期。 過期的訊息會傳送到特殊的佇列，稱為無法寄出的信件佇列。 寄不出信件佇列的位置會設定與**DeadLetterQueue**屬性。<br /><br /> 預設值： 1.00:00:00|  
|**UseSourceJournal**|布林|指定由此傳送埠處理的訊息複本是否應該存放在來源日誌佇列中。<br /><br /> 預設值： **False**|  
|**SecurityMode**|Enum<br /><br /> -   **無**<br />-   **訊息**<br />-   **傳輸**<br />-   **兩者**<br /><br /> 如需有關成員名稱的**SecurityMode**屬性，請參閱**安全性模式**屬性**Wcf-netmsmq 傳輸屬性對話方塊、 傳送、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定使用的安全性類型。<br /><br /> 預設值：**傳輸**|  
|**MsmqAuthenticationMode**|Enum<br /><br /> -   **無**<br />-   **WindowsDomain**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**MsmqAuthenticationMode**屬性，請參閱**MSMQ 驗證模式**屬性**Wcf-netmsmq 傳輸屬性 對話方塊傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定訊息如何由 MSMQ 傳輸進行驗證。<br /><br /> 預設值： **WindowsDomain**|  
|**MsmqProtectionLevel**|Enum<br /><br /> -   **無**： 無保護。<br />-   **符號**： 簽署訊息。<br />-   **EncryptAndSign**： 加密及簽署訊息。 若要使用這個保護等級，您必須啟用**Active Directory 整合**如**MSMQ**。|指定在 MSMQ 傳輸層維持訊息安全的方式。<br /><br /> 預設值：**符號**|  
|**MsmqSecureHashAlgorithm**|Enum<br /><br /> -   **MD5**<br />-   **SHA1**<br />-   **SHA25**<br />-   **SHA512**|指定用來計算雜湊的雜湊演算法。 這個屬性不可以使用如果**MsmqProtectionLevel**屬性設定為**無**。<br /><br /> 預設值： **SHA1**|  
|**MsmqEncryptionAlgorithm**|Enum<br /><br /> -   **RC4Stream**<br />-   **AES**|指定在訊息佇列管理員之間傳輸訊息時，要在連線上使用之訊息加密的演算法。 這個屬性只有當**MsmqProtectionLevel**屬性設定為**EncryptAndSign**。<br /><br /> 預設值： **RC4Stream**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **無**<br />-   **Windows**<br />-   **使用者名稱**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**MessageClientCredentialType**屬性，請參閱**訊息用戶端認證類型**屬性**Wcf-netmsmq 傳輸屬性對話方塊方塊中，傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。<br /><br /> 預設值： **Windows**|  
|**AlgorithmSuite**|Enum<br /><br /> 如需有關成員名稱的**AlgorithmSuite**屬性，請參閱**演算法套件**屬性**Wcf-netmsmq 傳輸屬性對話方塊、 傳送、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。<br /><br /> 預設值： **Basic256**|  
|**ClientCertificate**|字串|指定 X.509 憑證的憑證指紋，以便向服務驗證此傳送埠。 如果這個屬性，則需要**ClientCredentialsType**屬性設定為**憑證**。 要用於此屬性的憑證必須安裝到**我**存放**目前使用者**位置。<br /><br /> 預設為空字串。|  
|**ServiceCertificate**|字串|指定 X.509 憑證的指紋，以便驗證此傳送埠傳送訊息的目標服務。 要用於此屬性的憑證必須安裝到**其他人**存放**本機**位置。<br /><br /> 預設為空字串。|  
|**AffiliateApplicationName**|字串|指定要針對企業單一登入 (SSO) 使用的分支機構應用程式。<br /><br /> 預設為空字串。|  
|**UseSSO**|布林|指定是否要使用「單一登入」來擷取用戶端認證，以供目的地伺服器驗證。<br /><br /> 預設值： **False**|  
|**UserName**|字串|指定要用於目的地伺服器驗證的使用者名稱時**UseSSO**屬性設定為**False**。 您不需要對此屬性使用 domain\user 格式。<br /><br /> 預設為空字串。|  
|**密碼**|字串|指定要用於目的地伺服器驗證的密碼時**UseSSO**屬性設定為**False**。<br /><br /> 預設為空字串。|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用 BizTalk 訊息內文部分建立的 soap 內容**主體**外寄訊息的項目。<br />-   **UseTemplate** -使用中提供的範本**OutboundXMLTemplate**屬性，建立內容的 SOAP**主體**外寄訊息的項目。<br /><br /> 如需有關如何使用**OutboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍，soap**主體**外寄 WCF 訊息的項目。<br /><br /> 預設值： **UseBodyElement**|  
|**OutboundXMLTemplate**|字串<br /><br /> 如需有關如何使用**OutboundXMLTemplate**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定 XML 格式的範本內容的 SOAP**主體**外寄訊息的項目。 如果這個屬性，則需要**OutboundBodyLocation**屬性設定為**UseTemplate**。<br /><br /> 預設為空字串。|  
  
## <a name="configure-a-wcf-netmsmq-send-port-with-the-biztalk-administration-console"></a>使用 BizTalk 管理主控台設定 Wcf-netmsmq 傳送埠
  
 您可以在 BizTalk 管理主控台中設定 WCF-NetMsmq 傳送埠配接器變數。 如果沒有設定傳送埠的屬性，系統就會針對 WCF-NetMsmq 傳送埠組態使用如上表所示的預設值。  
  
## <a name="configure-variables-for-a-wcf-netmsmq-send-port"></a>設定 Wcf-netmsmq 傳送埠的變數  
  
1.  在 [BizTalk 管理主控台] 中建立新的傳送埠，或按兩下現有的傳送埠進行修改。 如需詳細資訊，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有傳送埠選項，並指定**Wcf-netmsmq**如**類型**選項**傳輸**區段**一般**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
2.  在**一般**索引標籤的**傳輸**區段中，按一下**設定**旁邊**類型**。  
  
3.  在**Wcf-netmsmq 傳輸屬性**對話方塊**一般**索引標籤上，設定端點位址、 服務識別和**SOAPAction**標頭Wcf-netmsmq 傳送埠。 如需有關**一般**索引標籤中**Wcf-netmsmq 傳輸屬性**對話方塊中，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 傳送、 一般** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
4.  在**Wcf-netmsmq 傳輸屬性**對話方塊**繫結**索引標籤上，設定逾時和交易屬性，以及佇列設定。 如需有關**繫結**索引標籤中**Wcf-netmsmq 傳輸屬性**對話方塊中，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 傳送、 繫結** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
5.  在**Wcf-netmsmq 傳輸屬性**對話方塊**安全性**索引標籤上，定義 Wcf-netmsmq 傳送埠的安全性功能。 如需有關**安全性**索引標籤中**Wcf-netmsmq 傳輸屬性**對話方塊中，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 傳送、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
6.  在**Wcf-netmsmq 傳輸屬性**對話方塊**訊息**索引標籤上，指定 SOAP 資料選取範圍**主體**項目。 如需有關**訊息**索引標籤中**Wcf-netmsmq 傳輸屬性**對話方塊中，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 傳送、 訊息** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
## <a name="configure-a-wcf-netmsmq-send-port-programmatically"></a>以程式設計方式設定 Wcf-netmsmq 傳送埠
  
 您可以使用下列格式來設定屬性：  
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <UseSSO vt="11">0</UseSSO>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <MsmqProtectionLevel vt="8">Sign</MsmqProtectionLevel>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <UseSourceJournal vt="11">0</UseSourceJournal>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">Transport</SecurityMode>  
  <CustomDeadLetterQueue vt="8" />  
  <ClientCertificate vt="8" />  
  <MsmqEncryptionAlgorithm vt="8">RC4Stream</MsmqEncryptionAlgorithm>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <MsmqSecureHashAlgorithm vt="8">Sha1</MsmqSecureHashAlgorithm>  
  <EnableTransaction vt="11">-1</EnableTransaction>  
  <TimeToLive vt="8">1.00:00:00</TimeToLive>  
  <MsmqAuthenticationMode vt="8">WindowsDomain</MsmqAuthenticationMode>  
  <DeadLetterQueue vt="8">System</DeadLetterQueue>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 下列程式碼片段說明如何建立 WCF-NetMsmq 傳送埠：  
  
```  
// Use BizTalk Explorer object model to create new WCF-NetMsmq send port.  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-NetMsmq"];  
sendPort.PrimaryTransport.Address = "net.msmq://mycomputer/private/samplequeue";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```  
  
## <a name="see-also"></a>請參閱  
 [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)   
 [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [設定 Wcf-netmsmq 配接器](../core/configuring-the-wcf-netmsmq-adapter.md)   
 [使用 WCF 配接器內容屬性設定動態傳送埠](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)