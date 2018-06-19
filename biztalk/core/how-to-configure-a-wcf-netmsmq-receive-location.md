---
title: 如何設定 Wcf-netmsmq 接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f82b323b-9870-42fb-9992-c23dca909b4d
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16491259826159f18791e35efb226dd159c12c27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250670"
---
# <a name="how-to-configure-a-wcf-netmsmq-receive-location"></a>如何設定 WCF-NetMsmq 接收位置
您可以用程式設計方式或使用 [BizTalk 管理主控台] 來設定 WCF-NetMsmq 接收位置。  
  
## <a name="configuratin-properties"></a>Configuratin 屬性
  
 「BizTalk 總管物件模型」可讓您以程式設計的方式建立和設定接收位置。 BizTalk 總管物件模型公開**IReceiveLocation**接收位置組態介面具有**TransportTypeData**讀/寫屬性。 這項屬性會以 XML 字串之名稱-值配對的格式接受 WCF-NetMsmq 接收位置組態屬性包。 若要在 BizTalk 總管物件模型中設定這個屬性，您必須設定**InboundTransportLocation**屬性**IReceiveLocation**介面。  
  
 **TransportTypeData**屬性**IReceiveLocation**介面沒有設定。 若沒有設定此屬性，WCF-NetMsmq 配接器就會使用 WCF-NetMsmq 接收位置組態的預設值，如下表所示。  
  
 下表列出您可在 BizTalk 總管物件模型中，針對 WCF-NetMsmq 接收位置設定的組態屬性。  
  
|屬性名稱|類型|Description|  
|-------------------|----------|-----------------|  
|**識別**|XML BLOB<br /><br /> 範例：<br /><br /> &lt;身分識別&gt;<br /><br /> &lt;userPrincipalName 值 ="username@contoso.com"/&gt;<br /><br /> &lt;/identity&gt;|指定此接收位置所提供服務的識別。 可以針對指定的值**識別**屬性，則根據安全性組態而有所不同。 這些設定可讓用戶端驗證此接收位置。 在用戶端與服務之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別能夠與這個項目的值相符。<br /><br /> 預設為空字串。|  
|**OpenTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道開啟作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**SendTimeout**|**System.TimeSpan**|指定時間值，表示可供完成傳送作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|指定時間值，表示可供完成通道關閉作業的時間間隔。<br /><br /> 預設值：00:01:00|  
|**MaxReceivedMessageSize**|Integer|指定大小上限，以位元組為單位，可以從網路收到的訊息 （包括標頭）。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> 預設值：65536|  
|**EnableTransaction**|布林|指定訊息佇列的類型：交易式或非交易式。 如果選取這個屬性，則每個訊息只會傳遞一次，而且會通知傳送者傳遞失敗。 若要透過交易式傳送的訊息傳送埠兩者**持久**和**exactlyOnce**繫結項目，用戶端必須設定為**True**。 如果清除這個屬性，便會傳輸訊息而不提供傳遞保證。 **注意：** 如果您使用在此異動式佇列接收位置，必須選取此屬性。 <br /><br /> 預設值： **False**|  
|**OrderedProcessing**|布林|指定是否連續處理訊息。 選取此屬性時，此接收位置的 BizTalk 傳訊 」 或 「 協調流程傳送埠搭配使用時，訊息的排序的傳遞可容納**排序的傳遞**選項設定為`True`。 您可以選取時，這才**EnableTransaction**屬性設定為**True**。<br /><br /> 如需有關**排序的傳遞**選項，請參閱 < 另請參閱中的適當主題。<br /><br /> 當這個屬性設定為**True**，Wcf-netmsmq 接收位置配接器以單一執行緒處理大型訊息時，將資源使用最佳化。<br /><br /> 預設值： **False**|  
|**MaxConcurrentCalls**|Integer|指定對單一服務執行個體的並行呼叫數目。 超出上限的呼叫將排入佇列。 這個屬性的範圍是從 0 到**Int32.MaxValue**。<br /><br /> 預設值：200|  
|**SecurityMode**|Enum<br /><br /> -   **無**<br />-   **訊息**<br />-   **傳輸**<br />-   **兩者**<br /><br /> 如需有關成員名稱的**SecurityMode**屬性，請參閱**安全性模式**屬性**Wcf-netmsmq 傳輸屬性對話方塊、 接收、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定使用的安全性類型。<br /><br /> 預設值：**傳輸**|  
|**MsmqAuthenticationMode**|Enum<br /><br /> -   **無**<br />-   **WindowsDomain**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**MsmqAuthenticationMode**屬性，請參閱**MSMQ 驗證模式**屬性**Wcf-netmsmq 傳輸屬性 對話方塊接收、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定訊息如何由 MSMQ 傳輸進行驗證。<br /><br /> 預設值： **WindowsDomain**|  
|**MsmqProtectionLevel**|Enum<br /><br /> -   **無**： 無保護。<br />-   **符號**： 簽署訊息。<br />-   **EncryptAndSign**： 加密及簽署訊息。 若要使用這個保護等級，您必須啟用**Active Directory 整合**如**MSMQ**。|指定在 MSMQ 傳輸層維持訊息安全的方式。 加密可以確保訊息完整性，簽章和加密則可同時確保訊息的完整性和不可否認性。<br /><br /> 預設值：**符號**|  
|**MsmqSecureHashAlgorithm**|Enum<br /><br /> -   **MD5**<br />-   **SHA1**<br />-   **SHA25**<br />-   **SHA512**|指定用來計算雜湊的雜湊演算法。 這個屬性不可以使用如果**MsmqProtectionLevel**屬性設定為**無**。<br /><br /> 預設值： **SHA1**|  
|**MsmqEncryptionAlgorithm**|Enum<br /><br /> -   **RC4Stream**<br />-   **AES**|指定在訊息佇列管理員之間傳輸訊息時，要在連線上使用之訊息加密的演算法。 這個屬性只有當**MsmqProtectionLevel**屬性設定為**EncryptAndSign**。<br /><br /> 預設值： **RC4Stream**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **無**<br />-   **Windows**<br />-   **使用者名稱**<br />-   **憑證**<br /><br /> 如需有關成員名稱的**MessageClientCredentialType**屬性，請參閱**訊息用戶端認證類型**屬性**Wcf-netmsmq 傳輸屬性對話方塊方塊中，接收、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。<br /><br /> 預設值： **Windows**|  
|**AlgorithmSuite**|Enum<br /><br /> 如需有關成員名稱的**AlgorithmSuite**屬性，請參閱**演算法套件**屬性**Wcf-netmsmq 傳輸屬性對話方塊、 接收、 安全性**  索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。|指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。<br /><br /> 預設值： **Basic256**|  
|**ServiceCertificate**|字串|針對此接收位置指定用戶端用來驗證服務之 X.509 憑證的憑證指紋。 要用於此屬性的憑證必須安裝到**我**存放**目前使用者**位置。 **注意：** 您必須將服務憑證安裝到**目前使用者**裝載此接收位置的接收處理常式的使用者帳戶的位置。 <br /><br /> 預設為空字串。|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -使用內容的 SOAP**主體**內送訊息建立 BizTalk 訊息內文部分的項目。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。<br />-   **UseEnvelope** -建立 BizTalk 訊息內文部分的整個 SOAP 從**信封**內送訊息。<br />-   **UseBodyPath** -使用中的內文路徑運算式**InboundBodyPathExpression**屬性以建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 此屬性只對請求-回應連接埠有效。<br /><br /> 如需有關如何使用**InboundBodyLocation**屬性，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。|指定資料選取範圍，soap**主體**內送 WCF 訊息的項目。<br /><br /> 預設值： **UseBodyElement**|  
|**InboundBodyPathExpression**|字串<br /><br /> 如需有關如何使用**InboundBodyPathExpression**屬性，請參閱[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)。|指定內文路徑運算式來識別用於建立 BizTalk 訊息內文部分之內送訊息的特定部分。 此內文路徑運算式評估的 soap 的直系子元素**主體**節點內送訊息。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果這個屬性，則需要**InboundBodyLocation**屬性設定為**UseBodyPath**。<br /><br /> 預設為空字串。|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -Base64 編碼方式。<br />-   **Hex** ： 十六進位編碼。<br />-   **字串**： 文字編碼-utf-8。<br />-   **XML** -WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml **InboundBodyPathExpression**。|指定的編碼，Wcf-netmsmq 接收配接器，用來解碼中指定的內文路徑運算式所識別的節點類型**InboundBodyPathExpression**。 如果這個屬性，則需要**InboundBodyLocation**屬性設定為**UseBodyPath**。<br /><br /> 預設值： **XML**|  
|**DisableLocationOnFailure**|布林|指定是否停用由於接收管線失敗或路由失敗造成輸入處理失敗的接收位置。<br /><br /> 預設值： **False**|  
|**SuspendMessageOnFailure**|布林|指定是否擱置因接收管線失敗或路由失敗而造成輸入處理失敗的要求訊息。<br /><br /> 預設值： **，則為 True**|  
|**IncludeExceptionDetailInFaults**|布林|指定基於偵錯目的傳回用戶端的 SOAP 錯誤詳細資料中，是否包括 Managed 例外狀況資訊。<br /><br /> 預設值： **False**|  
  
## <a name="configure-a-wcf-netmsmq-receive-location-with-the-biztalk-administration-console"></a>設定 Wcf-netmsmq 接收位置使用 BizTalk 管理主控台
  
 您可以在 [BizTalk 管理主控台] 中設定 WCF-NetMsmq 接收位置配接器變數。 若接收位置並未設定屬性，系統就會使用 [BizTalk 管理主控台] 中的預設接收處理常式值。  
  
> [!NOTE]
>  完成下列程序之前，您必須已經新增接收埠。 如需詳細資訊，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
> [!NOTE]
>  WCF 用戶端和 WCF-NetMsmq 接收位置的繫結組態彼此必須相符。 如果兩者並不相符，WCF-NetMsmq 接收位置便可能會遺失內送訊息。  
  
## <a name="configure-variables-for-a-wcf-netmsmq-receive-location"></a>設定 Wcf-netmsmq 接收位置的變數  
  
1.  在 BizTalk 管理主控台中，展開  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 應用程式您想要在其中建立接收位置。  
  
2.  在 [BizTalk 管理主控台] 的左窗格中，按一下 **[接收埠]** 節點。 然後在右窗格中，使用滑鼠右鍵按一下與現有接收位置關聯的接收埠，或是您要與新接收位置關聯的接收埠，然後按一下 **[屬性]**。  
  
3.  在**接收埠屬性**對話方塊的左窗格中，選取**接收位置**，然後在右窗格中，按兩下現有接收位置或按一下**新增**以建立新接收位置。  
  
4.  在**接收位置屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**Wcf-netmsmq**從下拉式清單，然後按一下**設定**。  
  
5.  在**Wcf-netmsmq 傳輸屬性**對話方塊**一般**索引標籤上，設定端點位址和服務識別的 Wcf-netmsmq 接收位置。 如需有關**一般**索引標籤中**Wcf-netmsmq 傳輸屬性**對話方塊中，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 接收、 一般** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
6.  在**Wcf-netmsmq 傳輸屬性**對話方塊**繫結**索引標籤上，設定逾時和交易屬性。 如需有關**繫結**索引標籤中**Wcf-netmsmq 傳輸屬性**對話方塊中，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 接收、 繫結** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
7.  在**Wcf-netmsmq 傳輸屬性**對話方塊**安全性**索引標籤上，定義的安全性功能的 Wcf-netmsmq 接收位置。 如需有關**安全性**索引標籤中**Wcf-netmsmq 傳輸屬性**對話方塊中，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 接收、 安全性** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
8.  在**Wcf-netmsmq 傳輸屬性**對話方塊**訊息**索引標籤上，指定 SOAP 資料選取範圍**主體**項目。 如需有關**訊息**索引標籤中**Wcf-netmsmq 傳輸屬性**對話方塊中，請參閱**Wcf-netmsmq 傳輸屬性對話方塊、 接收、 訊息** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 
  
## <a name="configure-a-wcf-netmsmq-receive-location-programmatically"></a>設定 Wcf-netmsmq 接收位置，以程式設計的方式
  
 您可以使用下列格式來設定屬性：  
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <InboundBodyPathExpression vt="8" />  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <MaxConcurrentCalls vt="3">16</MaxConcurrentCalls>  
  <SecurityMode vt="8">Transport</SecurityMode>  
  <OrderedProcessing vt="11">0</OrderedProcessing>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <MsmqEncryptionAlgorithm vt="8">RC4Stream</MsmqEncryptionAlgorithm>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <MsmqProtectionLevel vt="8">Sign</MsmqProtectionLevel>  
  <DisableLocationOnFailure vt="11">0</DisableLocationOnFailure>  
  <MsmqSecureHashAlgorithm vt="8">Sha1</MsmqSecureHashAlgorithm>  
  <SuspendMessageOnFailure vt="11">-1</SuspendMessageOnFailure>  
  <EnableTransaction vt="11">-1</EnableTransaction>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <MsmqAuthenticationMode vt="8">WindowsDomain</MsmqAuthenticationMode>  
</CustomProps>  
  
```  
  
 下列程式碼片段說明了如何建立 WCF-NetMsmq 接收位置：  
  
```  
// Use BizTalk Explorer object model to create new WCF-NetMsmq receive location   
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
// Find a receive handler for WCF-NetMsmq   
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-NetMsmq" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "net.msmq://mycomputer/private/sampleQueue";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-NetMsmq"];  
recieveLocation.TransportTypeData = transportConfigData;  
// Save  
explorer.SaveChanges();   
```  
  
## <a name="see-also"></a>另請參閱  
 [發行服務中繼資料之 wcf 接收配接器](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)   
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [如何變更服務帳戶和密碼](../core/how-to-change-service-accounts-and-passwords.md)   
 [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)   
 [指定訊息本文為 WCF 配接器](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [設定 Wcf-netmsmq 配接器](../core/configuring-the-wcf-netmsmq-adapter.md)   
 [依序傳遞訊息](../core/ordered-delivery-of-messages.md)   
 [傳送和擷取在交易內的訊息](http://go.microsoft.com/fwlink/?LinkID=75752)   
 [訊息佇列及 Active Directory](http://go.microsoft.com/fwlink/?LinkID=75769)   
 [公用和私用佇列](http://go.microsoft.com/fwlink/?LinkId=196673)