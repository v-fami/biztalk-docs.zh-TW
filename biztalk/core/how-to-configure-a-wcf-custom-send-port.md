---
title: 如何設定 Wcf-custom 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a195c047-5d5c-478b-accd-252e9dc5cfe8
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c615e2f54e1d7db9115a2607162f6eae1dffc01a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-configure-a-wcf-custom-send-port"></a>如何設定 WCF-Custom 傳送埠
您可以使用程式設計的方式或 [BizTalk 管理主控台] 來設定 WCF-Custom 傳送埠。  
  
## <a name="configuration-properties"></a>組態屬性
  
 BizTalk 總管物件模型公開 （expose) 名為傳送埠的配接器特定介面 **ITransportInfo** 具有 **TransportTypeData** 讀/寫屬性。 這個屬性會以成對的名稱-數值之 XML 字串格式接受 WCF-Custom 傳送埠組態屬性包。  
  
 **TransportTypeData** 屬性 **ITransportInfo** 介面並非必要。 如果沒有設定此屬性，配接器就會針對 WCF-Custom 傳送埠組態使用預設值，如下表所示。  
  
 下表將列出您可以在 BizTalk 總管物件模型中針對 WCF-Custom 傳送埠設定的組態屬性。  
  
|屬性名稱|유형|Description|  
|-------------------|----------|-----------------|  
|**身分識別**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;身分識別&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|指定此傳送埠所預期服務的識別。 這些設定可讓此傳送埠驗證服務。 在用戶端及服務之間的交握程序中，WCF 基礎結構可確保所預期服務的識別符合此項目的值。 您可以指定的值 **識別** 屬性，則根據安全性組態而有所不同。<br /><br /> 預設為空字串。|  
|**StaticAction**|字串|指定 **SOAPAction** 外寄訊息的標頭欄位。 這個屬性也可以透過訊息內容屬性設定 **WCF。動作** 管線或協調流程中。 您可以將這個值指定兩個不同的方式︰ 單一動作格式和動作對應格式。 如果您在設定此屬性的單一動作格式-例如， http://contoso.com/Svc/Op1- **SOAPAction**標頭外寄訊息一定會設定這個屬性中指定的值。<br /><br /> 如果您設定此屬性以動作對應格式傳出 **SOAPAction** 標頭由 **BTS。作業** 內容屬性。 例如，如果此屬性設定為下列 XML 格式和**BTS。作業**屬性設定為 Op1，WCF 傳送配接器會使用http://contoso.com/Svc/Op1針對外寄**SOAPAction**標頭。<br /><br /> \<BtsActionMapping\><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /\><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /\><br /><br /> \</BtsActionMapping\><br /><br /> 協調流程執行個體如果外寄訊息是來自協調流程連接埠，以動態方式設定 **BTS。作業** 與連接埠的作業名稱的屬性。 如果外寄訊息會路由傳送，以內容為基礎的路由，您可以設定 **BTS。作業** 管線元件中的屬性。<br /><br /> 預設為空字串。|  
|**BindingType**|Enum<br /><br /> 如需有關成員名稱的**BindingType**屬性，請參閱**繫結的型別**屬性**Wcf-custom 傳輸屬性對話方塊、 傳送、 繫結** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定此傳送埠所用之端點所要使用的繫結類型。 **注意︰**  如果您使用自訂繫結， **BindingType** 屬性可以使用自訂繫結來設定。 如需如何使用自訂繫結的詳細資訊，請參閱[如何啟用 WCF 擴充性點，WCF 配接器](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)。|  
|**BindingConfiguration**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;繫結名稱 ="p"&gt;&lt;readerQuotas maxDepth ="32"maxStringContentLength ="8192"maxArrayLength ="16384"maxBytesPerRead ="4096"maxNameTableCharCount ="16384"/&gt;&lt;安全性模式 ="None"/&gt;&lt;繫結&gt;|指定的 XML 字串**\<繫結\>**項目來設定不同類型的預先定義 Windows Communication Foundation (WCF) 所提供的繫結。 如需系統提供之繫結與自訂繫結的詳細資訊，請參閱「請參閱」中所列的適當主題。 **注意︰**  BizTalk Server 不支援所有類型的繫結延伸項目，您可以使用設定 **BindingConfiguration** 屬性。 <br /><br /> 預設為空字串。|  
|**EndpointBehaviorConfiguration**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;行為名稱 ="sampleBehavior"&gt;&lt;callbackTimeouts /&gt;&lt;/behavior&gt;|指定的 XML 字串**\<行為\>**元素**\<endpointBehaviors\>**項目來設定的行為設定WCF 端點。 如需有關**\<endpointBehaviors\>**項目，請參閱 < 另請參閱中的適當主題。 **注意︰**  BizTalk Server 不支援所有類型的行為延伸模組項目，您可以使用設定 **EndpointBehaviorConfiguration** 屬性。 <br /><br /> 預設為空字串。|  
|**AffiliateApplicationName**|字串|指定要針對企業單一登入 (SSO) 使用的分支機構應用程式。<br /><br /> 預設為空字串。|  
|**UseSSO**|Boolean|指定是否要使用「單一登入」來擷取用戶端認證，以供目的地伺服器驗證。<br /><br /> 預設值︰ **False**|  
|**使用者名稱**|字串|指定要用於目的地伺服器驗證的使用者名稱時 **UseSSO** 屬性設定為 **False**。 您不需要對此屬性使用 domain\user 格式。<br /><br /> 預設為空字串。|  
|**密碼**|字串|指定要用於驗證目的地伺服器的密碼時 **UseSSO** 屬性設定為 **False**。<br /><br /> 預設為空字串。|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用 BizTalk 訊息內文部分建立的 soap 內容**主體**外寄訊息的項目。<br />-   **UseTemplate** -使用中提供的範本 **OutboundXMLTemplate** 屬性來建立的內容的 soap **主體** 外寄訊息的項目。<br /><br /> 如需有關如何使用**OutboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍 soap **主體** 外寄 WCF 訊息的項目。<br /><br /> 預設值︰ **UseBodyElement**|  
|**OutboundXMLTemplate**|字串<br /><br /> 如需有關如何使用**OutboundXMLTemplate**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定 XML 格式的範本內容的 SOAP **主體** 外寄訊息的項目。 如果這個屬性，則需要 **OutboundBodyLocation** 屬性設定為 **UseTemplate**。<br /><br /> 預設為空字串。|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用內容的 SOAP**主體**內送訊息建立 BizTalk 訊息內文部分的項目。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。 此屬性只對請求-回應連接埠有效。<br />-   **UseEnvelope** -從整個 SOAP 建立 BizTalk 訊息內文部分 **信封** 內送訊息。<br />-   **UseBodyPath** -使用中的內文路徑運算式 **InboundBodyPathExpression** 屬性來建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 此屬性只對請求-回應連接埠有效。<br /><br /> 如需有關如何使用**InboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍 soap **主體** 內送 WCF 訊息的項目。<br /><br /> 預設值︰ **UseBodyElement**|  
|**InboundBodyPathExpression**|字串<br /><br /> 如需有關如何使用**InboundBodyPathExpression**屬性，請參閱[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。|指定內文路徑運算式來識別用於建立 BizTalk 訊息內文部分之內送訊息的特定部分。 此內文路徑運算式評估的 soap 的直系子項目 **主體** 內送訊息的節點。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設為空字串。|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **XML**<br />-   **Base64** -Base64 編碼方式。<br />-   **Hex** ︰ 十六進位編碼方式。<br />-   **字串** ︰ 文字編碼-utf-8。<br />-   **XML** -WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml **InboundBodyPathExpression**。|指定 Wcf-custom 傳送配接器中指定的內文路徑所識別的節點用來解碼的編碼類型 **InboundBodyPathExpression**。 如果這個屬性，則需要 **InboundBodyLocation** 屬性設定為 **UseBodyPath**。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值︰ **XML**|  
|**PropagateFaultMessage**|Boolean<br /><br /> -   **True** -路由傳送訊息至訂閱應用程式的輸出處理失敗 （例如其他接收埠或協調流程排程）。<br />-   **False** -擱置失敗的訊息，並產生負值通知 (NACK)。|指定要路由傳送或擱置在輸出處理中失敗的訊息。<br /><br /> 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值︰ **，則為 True**|  
|**ReferencedBindings**|XML BLOB<br /><br /> 範例：<br /><br /> \<**BindingConfiguration** vt="8"\><br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;繫結名稱 ="sampleBinding"&gt;<br /><br /> &lt;安全性模式 = [訊息]&gt;<br /><br /> &lt;訊息 issuedKeyType ="AsymmetricKey"&gt;<br /><br /> &lt;issuer address="http://www.contoso.com/samplests" binding="wsFederationHttpBinding" bindingConfiguration="**contosoSTSBinding**"/&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/ 繫結&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> \</**BindingConfiguration**\><br /><br /> \<**ReferencedBindings** vt="8"\><br /><br /> &lt;繫結&gt;<br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;繫結名稱 ="**contosoSTSBinding**」&gt;<br /><br /> &lt;安全性模式 = [訊息]&gt;<br /><br /> &lt;訊息 negotiateServiceCredential ="false"&gt;<br /><br /> &lt;issuer address="http://northwind.com/samplests" bindingConfiguration="**northwindBinding**" binding="wsHttpBinding"&gt;<br /><br /> &lt;/issuer&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/ 繫結&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> &lt;wsHttpBinding&gt;<br /><br /> &lt;繫結名稱 ="**northwindBinding**」&gt;<br /><br /> &lt;安全性模式 = [訊息]&gt;<br /><br /> &lt;訊息 clientCredentialType ="Certificate"/&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/ 繫結&gt;<br /><br /> &lt;/wsHttpBinding&gt;<br /><br /> &lt;/bindings&gt;<br /><br /> \</**ReferencedBindings** \> **附註：** **ReferencedBinding**屬性不能包含中使用的繫結組態**BindingConfiguration**屬性。|指定所參考的繫結組態**bindingConfiguration**屬性**\<簽發者\>**元素**wsFederationHttpBinding**和**customBinding**，表示安全性權杖服務 (STS) 發行安全性權杖。 如需詳細資訊**\<簽發者\>**項目，請參閱主題 <"\<簽發者\>」 在[ http://go.microsoft.com/fwlink/?LinkId=83476 ](http://go.microsoft.com/fwlink/?LinkId=83476)。<br /><br /> 繫結資訊，包括**\<簽發者\>**元素**wsFederationHttpBinding**和**customBinding**可以是透過設定**BindingConfiguration** Wcf-custom 和 Wcf-customisolated 配接器的屬性。 所有參考繫結組態，這個屬性必須放置在表單的[\<繫結\>](http://go.microsoft.com/fwlink/?LinkID=80878)項目。 **注意︰**  無法設定此屬性 **繫結** 傳輸屬性 對話方塊中的索引標籤。 您可以匯入和匯出此屬性透過 **匯入/匯出** Wcf-custom 和 Wcf-customisolated 配接器傳輸屬性對話方塊中的索引標籤。 **注意：** **bindingConfiguration**屬性**\<簽發者\>**元素必須參考這個屬性中的有效繫結名稱。 **注意：** **\<簽發者\>**中參考繫結組態項目也可以參考不同的繫結組態中使用該屬性如果這個參考鏈結不會產生循環相依性。 <br /><br /> 預設為空字串。|  
  
## <a name="configure-a-wcf-custom-send-port-with-the-biztalk-administration-console"></a>使用 BizTalk 管理主控台設定 Wcf-custom 傳送埠
  
 您可以在 BizTalk 管理主控台中設定 WCF-Custom 傳送埠配接器變數。 如果沒有設定傳送埠的屬性，系統就會針對 WCF-Custom 傳送埠組態使用預設值，如上表所示。  
  
## <a name="configure-variables-for-a-wcf-custom-send-port"></a>設定 Wcf-custom 傳送埠的變數  
  
1.  如果設定 WCF-Custom 配接器時，您打算使用自訂繫結元素、自訂行為項目和自訂通道元件這類 WCF 擴充性點，必須將實作擴充性點和所有相依組件的組件，同時加入至 BizTalk 處理電腦 (執行階段電腦) 和管理電腦上的全域組件快取。 此外，您必須在 machine.config 檔案註冊延伸模組元件。 如需如何搭配 WCF 自訂配接器使用 WCF 擴充性點的詳細資訊，請參閱[如何啟用 WCF 擴充性點，WCF 配接器](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)。  
  
2.  在 [BizTalk 管理主控台] 中建立新的傳送埠，或按兩下現有的傳送埠進行修改。 如需詳細資訊，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有傳送埠選項，並指定**Wcf-custom**如**類型**選項**傳輸**區段**一般** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
3.  在 **一般** 索引標籤的 **傳輸** 區段中，按一下 **設定** 旁 **類型**。  
  
4.  在 **Wcf-custom 傳輸屬性** 對話方塊的  **一般** 索引標籤上，設定端點位址、 服務識別和 **SOAPAction** WCF 自訂標頭傳送埠。 如需有關**一般**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 傳送、 一般**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
5.  在 **Wcf-custom 傳輸屬性** 對話方塊的  **繫結** 索引標籤上，設定不同類型的 WCF 預先定義或自訂繫結。 如需有關**繫結**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 傳送、 繫結**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
6.  在 **Wcf-custom 傳輸屬性** 對話方塊的  **行為** 索引標籤上，設定此傳送埠的端點行為。 端點行為是一組行為延伸模組項目，會修改或延伸服務或用戶端功能。 如需有關**行為**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 傳送、 行為** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
7.  在 **Wcf-custom 傳輸屬性** 對話方塊的  **認證** 索引標籤上，指定要傳送訊息時使用的認證。 如需有關**認證**索引標籤中**Wcf-custom 傳輸屬性**對話方塊方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 傳送、 認證** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
8.  在 **Wcf-custom 傳輸屬性** 對話方塊的  **訊息** 索引標籤上，指定資料選取範圍 soap **主體** 項目。 如需有關**訊息**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 傳送、 訊息** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
9. 在 **Wcf-custom 傳輸屬性** 對話方塊的  **匯入/匯出**  索引標籤上，匯入和匯出 **位址 (URI)** 和 **端點身分識別** 屬性 **一般**  索引標籤上的繫結資訊 **繫結**  索引標籤，以及端點行為 **行為** 此傳送埠 索引標籤。 如需有關**匯入/匯出**索引標籤中**Wcf-custom 傳輸屬性**對話方塊中，請參閱**Wcf-custom 傳輸屬性對話方塊、 傳送、 匯入匯出**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
## <a name="configure-a-wcf-custom-send-port-programmatically"></a>以程式設計方式設定 Wcf-custom 傳送埠  
  
 您可以使用下列格式來設定屬性：  
  
```  
<CustomProps>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <InboundBodyPathExpression vt="8" />  
  <EndpointBehaviorConfiguration vt="8"><behavior name="sampleBehavior"><callbackTimeouts /></behavior></EndpointBehaviorConfiguration>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <BindingConfiguration vt="8"><binding name="NetNamedPipeOrderProcessService.OrderProcessServieEndpoint"><readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384" /><security mode="None" /></binding></BindingConfiguration>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <UseSSO vt="11">0</UseSSO>  
  <AffiliateApplicationName vt="8" />  
  <BindingType vt="8">netNamedPipeBinding</BindingType>  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UserName vt="8" />  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
</CustomProps>  
  
```  
  
 下列程式碼片段會說明如何建立 WCF-Custom 傳送埠：  
  
```  
// Use BizTalk Explorer object model to create new WCF-Custom send port.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
                                 <StaticAction vt=""8"">http://www.northwindtraders.com/Service/Operation</StaticAction>  
                                 <EndpointBehaviorConfiguration vt=""8""><behavior name=""sampleBehavior""><callbackTimeouts /></behavior></EndpointBehaviorConfiguration>  
                                 <BindingType vt=""8"">netNamedPipeBinding</BindingType>  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-Custom"];  
sendPort.PrimaryTransport.Address = "net.pipe://mycomputer/private/samplequeue";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```  
  
## <a name="see-also"></a>另請參閱  
 [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)   
 [設定 WCF 自訂配接器](../core/configuring-the-wcf-custom-adapter.md)   
 [設定動態傳送埠使用 WCF 配接器內容屬性](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)   
 [\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878)   
 [\<行為\>的\<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879)