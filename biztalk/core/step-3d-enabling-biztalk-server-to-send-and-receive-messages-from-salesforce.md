---
title: "步驟 3d： 啟用 BizTalk Server 傳送和接收來自 Salesforce 的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 470c4a72-1e97-4493-8958-33a13f793ffd
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c38a58e376bbc8908ff0fe578aa54cbb009c58d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce"></a>步驟 3d： 啟用 BizTalk Server 傳送和接收來自 Salesforce 的訊息
我們必須透過 Salesforce 進行驗證時使用的 REST 介面傳送訊息。 無法使用立即可用的 Wcf-webhttp 配接器，我們將使用來叫用 Salesforce 的 REST 介面支援 Salesforce REST 呼叫的驗證方法。 因此，我們將建立自訂的 WCF 端點行為，然後將它附加到我們稍後會設定要叫用 Salesforce REST 介面的 Wcf-webhttp 傳送配接器。  
  
 同樣地，從 Salesforce 收到的 XML 回應將不會包含任何命名空間。 如[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理回應訊息和回應結構描述，回應訊息必須包含的目標命名空間。 因此，我們將建立自訂管線，使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]將命名空間新增至回應訊息。 然後，我們將使用的接收管線為這個自訂的管線要求-回應 Wcf-webhttp 傳送埠。  
  
## <a name="add-a-custom-wcf-behavior-for-salesforce-authentication"></a>自訂 WCF 將行為加入至 Salesforce 驗證  
 Salesforce 提供不同的選項，用戶端應用程式透過 Salesforce 進行驗證。 我們將使用何種 Salesforce 詞彙做為[使用者名稱密碼](http://go.microsoft.com/fwlink/?LinkId=287082)流程。 在用戶端，WCF 可讓您建立[訊息偵測器](http://msdn.microsoft.com/library/aa717047\(v=VS.90\).aspx)改變傳送之前或之後收到的訊息。 訊息偵測器是用戶端執行階段的延伸模組，並且會設定為行為。 行為，接著，新增至行為延伸項目。 此行為延伸項目會註冊在 machine.config 項目名稱，使其可設定為 WCF 通訊埠上的自訂行為。 如需詳細資訊，請參閱[延伸 WCF 自訂行為](http://msdn.microsoft.com/magazine/cc163302.aspx)。 我們會使用此方法來合併使用 Salesforce 進行驗證的使用者名稱驗證流程。 我們要遵循的概略步驟如下：  
  
-   建立訊息偵測器可讓 HTTP POST 呼叫 Salesforce 驗證端點與接收存取權杖。 訊息偵測器將驗證語彙基元做為查詢訊息傳送至 Salesforce 的授權標頭的值。 訊息偵測器也會將 Accept 標頭加入至要求訊息，以便接收的回應會以 XML 格式。 否則，Salesforce 會以預設的 JSON 格式傳送訊息。  
  
-   建立要套用至用戶端端點的訊息偵測器的端點行為。  
  
-   建立行為延伸項目，若要啟用端點行為的設定。  
  
#### <a name="to-create-a-message-inspector"></a>若要建立訊息偵測器  
  
1.  做為一部分**BtsSalesforceIntegration**方案在 Visual Studio 中建立 C# 類別庫。 命名`Microsoft.BizTalk.Adapter.Behaviors`並加入下列命名空間：  
  
    ```  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Channels;  
    using System.Xml;  
    using System.Net;  
    using System.IO;  
    using System.ServiceModel.Configuration;  
    using System.Configuration;  
    using System.Web.Script.Serialization;  
    ```  
  
2.  從 [方案總管] 中，將參考加入至`System.ServiceModel`， `System.Web.Extensions`，和`System.Configuration`。  
  
3.  將類別加入`SalesforceOAuthToken`具有下列屬性。 此類別代表從 Salesforce 收到的授權 token。  
  
    ```  
    public class SalesforceOAuthToken  
    {  
        public string id { get; set; }  
        public string issued_at { get; set; }  
        public string refresh_token { get; set; }  
        public string instance_url { get; set; }  
        public string signature { get; set; }  
        public string access_token { get; set; }  
    }  
    ```  
  
4.  將類別加入`SalesforceRESTSecurityBehavior`實作`IClientMessageInspector`和`IEndpointBehavior`。 這個類別包含`HttpPost()`和`FetchOAuthToken()`進行 Salesforce 驗證端點的 HTTP POST 呼叫的方法會擷取授權權杖。  
  
     因為`SalesforceRESTSecurityBehavior`類別會實作`IClientMessageInspector`介面，它必須實作兩種方法，`AfterReceiveReply()`和`BeforeSendRequest()`。 此案例中我們不需要執行任何動作的一部分`AfterReceiverReply()`方法。 不過，`BeforeSendRequest()`方法會叫用`FetchOAuthToken()`方法中，依序呼叫`HttpPost()`方法。 `BeforeSendRequest()`方法接著會將授權權杖做為訊息標頭的一部分。 它也會加入**接受**標頭，以確保從 Salesforce 收到的回應是以 XML 格式。  
  
     `IEndpointBehavior`實作只會將訊息偵測器類別新增至用戶端端點行為。  
  
    ```  
    public class SalesforceRESTSecurityBehavior : IClientMessageInspector, IEndpointBehavior  
    {  
        // Some constants  
        private static string SalesforceAuthEndpoint = "https://login.salesforce.com/services/oauth2/token";  
  
        // Configuration Properties  
        private string username_;  
        private string password_;  
        private string consumerKey_;  
        private string consumerSecret_;  
        private int sessionTimeout_;  
  
        // Private Properties  
        private SalesforceOAuthToken token_;  
        private DateTime tokenExpiryTime_;  
  
        public SalesforceRESTSecurityBehavior(  
            string username,  
            string password,  
            string consumerKey,  
            string consumerSecret,  
            int sessionTimeout)  
        {  
            this.username_ = username;  
            this.password_ = password;  
            this.consumerKey_ = consumerKey;  
            this.consumerSecret_ = consumerSecret;  
            this.sessionTimeout_ = sessionTimeout;  
        }  
  
        private void FetchOAuthToken()  
        {  
            if ((tokenExpiryTime_ == null) || (tokenExpiryTime_.CompareTo(DateTime.Now) <= 0))  
            {  
                StringBuilder body = new StringBuilder();  
                body.Append("grant_type=password&")  
                    .Append("client_id=" + consumerKey_ + "&")  
                    .Append("client_secret=" + consumerSecret_ + "&")  
                    .Append("username=" + username_ + "&")  
                    .Append("password=" + password_);  
  
                string result;  
  
                try  
                {  
                    result = HttpPost(SalesforceAuthEndpoint, body.ToString());  
                }  
                catch (WebException)  
                {  
                    // do something  
                    return;  
                }  
  
                // Convert the JSON response into a token object  
                JavaScriptSerializer ser = new JavaScriptSerializer();  
                this.token_ = ser.Deserialize<SalesforceOAuthToken>(result);  
                this.tokenExpiryTime_ = DateTime.Now.AddSeconds(this.sessionTimeout_);  
            }  
        }  
  
        public string HttpPost(string URI, string Parameters)  
        {  
            WebRequest req = WebRequest.Create(URI);  
            req.ContentType = "application/x-www-form-urlencoded";  
            req.Method = "POST";  
  
            // Add parameters to post  
            byte[] data = Encoding.ASCII.GetBytes(Parameters);  
            req.ContentLength = data.Length;  
            System.IO.Stream os = req.GetRequestStream();  
            os.Write(data, 0, data.Length);  
            os.Close();  
  
            // Do the post and get the response.  
            System.Net.WebResponse resp = null;  
            resp = req.GetResponse();  
  
            StreamReader sr = new StreamReader(resp.GetResponseStream());  
            return sr.ReadToEnd().Trim();  
        }  
        #region IClientMessageInspector  
  
        public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
        {  
            // do nothing  
        }  
        public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
        {  
            // We are going to send a request to Salesforce  
            // Overview:  
            // This behavior will do the following:  
            // (1) Fetch Token from Salesforce, if required  
            // (2) Add the token to the message  
            // (3) Insert an Http Accept header so we get XML data in response, instead of JSON, which is default  
            // Reference: http://www.salesforce.com/us/developer/docs/api_rest/index.htm  
            //  
            // (1) Authentication with Salesforce  
            // (2) The token is added to the HTTP Authorization Header   
            // (3) Add the Accept Header  
            //  
  
            HttpRequestMessageProperty httpRequest = null;  
  
            if (request.Properties.ContainsKey(HttpRequestMessageProperty.Name))  
            {  
                httpRequest = request.Properties[HttpRequestMessageProperty.Name] as HttpRequestMessageProperty;  
            }  
  
            if (httpRequest == null)  
            {  
                // NOTE: Ideally, we shouldn’t get here for WebHttp  
                httpRequest = new HttpRequestMessageProperty()  
                {  
                    Method = "GET",  
                    SuppressEntityBody = true  
                };  
                request.Properties.Add(HttpRequestMessageProperty.Name, httpRequest);  
            }  
  
            WebHeaderCollection headers = httpRequest.Headers;  
            FetchOAuthToken();  
  
            headers.Add(HttpRequestHeader.Authorization, "OAuth " + this.token_.access_token);  
            headers.Add(HttpRequestHeader.Accept, "application/xml");  
  
            return null;  
        }  
  
        #endregion IClientMessageInspector  
  
        #region IEndpointBehavior  
  
        public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
        {  
            // do nothing  
        }  
  
        public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
        {  
            clientRuntime.MessageInspectors.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
        {  
            // do nothing  
        }  
  
        public void Validate(ServiceEndpoint endpoint)  
        {  
            // do nothing  
        }  
  
        #endregion IEndpointBehavior  
    }  
    ```  
  
5.  上一個步驟中，我們會建立訊息偵測器套用至用戶端端點行為類別。 我們現在需要將此行為提供給組態經驗 Wcf-webhttp 配接器傳送要求訊息至 Salesforce。 若要讓此行為可進行設定，我們需要如何做兩件事：  
  
    -   建立衍生自類別`BehaviorExtensionElement`  
  
    -   登錄中的您 BehavaiorExtensionElement\<延伸模組 >\\< behaviorExtensions\> machine.config 使用項目名稱中的項目。  
  
     我們也可以加入這個類別組態屬性，使其可從 Wcf-webhttp 配接器組態 UI。  
  
    ```  
    public class SalesforceRESTBehaviorElement : BehaviorExtensionElement  
    {  
        public override Type BehaviorType  
        {  
            get { return typeof(SalesforceRESTSecurityBehavior); }  
        }  
  
        protected override object CreateBehavior()  
        {  
            return new SalesforceRESTSecurityBehavior(Username, Password, ConsumerKey, ConsumerSecret, SessionTimeout);  
        }  
  
        [ConfigurationProperty("username", IsRequired = true)]  
        public string Username  
        {  
            get { return (string)this["username"]; }  
            set { this["username"] = value; }  
        }  
  
        [ConfigurationProperty("password", IsRequired = true)]  
        public string Password  
        {  
            get { return (string)this["password"]; }  
            set { this["password"] = value; }  
        }  
  
        [ConfigurationProperty("consumerKey", IsRequired = true)]  
        public string ConsumerKey  
        {  
            get { return (string)this["consumerKey"]; }  
            set { this["consumerKey"] = value; }  
        }  
  
        [ConfigurationProperty("consumerSecret", IsRequired = true)]  
        public string ConsumerSecret  
        {  
            get { return (string)this["consumerSecret"]; }  
            set { this["consumerSecret"] = value; }  
        }  
  
        [ConfigurationProperty("sessionTimeout", IsRequired = false, DefaultValue = 300)]  
        public int SessionTimeout  
        {  
            get { return (int)this["sessionTimeout"]; }  
            set { this["sessionTimeout"] = value; }  
        }  
    }  
    ```  
  
6.  將強式名稱金鑰檔加入專案，並建置專案。 一旦成功建置專案，加入組件`Microsoft.BizTalk.Adapter.Behaviors`到 GAC。  
  
7.  System.ServiceModel\Extensions\BehaviorExtensions 在 machine.config 中加入下列項目。  
  
    ```  
    <add name="Microsoft.BizTalk.Adapter.Behaviors.Demo.Salesforce" type="Microsoft.BizTalk.Adapter.Behaviors.SalesforceRESTBehaviorElement, Microsoft.BizTalk.Adapter.Behaviors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=45bd7fe67ef032db"/>  
    ```  
  
     您可以擷取從 GAC 的組件公開金鑰語彙基元。 此外，如果您要建立此應用程式在 64 位元電腦上，您必須將此項目加入 machine.config 的 32 位元和 64 位元版本。  
  
## <a name="add-a-custom-pipeline-to-add-namespace-to-the-salesforce-response"></a>新增自訂管線新增至 Salesforce 回應的命名空間  
 從 Salesforce 收到的回應不包含命名空間。 不過，處理回應訊息和回應結構描述 (QueryResult.xsd) 我們必須在 Salesforce 回應中包含命名空間。 在本節中，我們建立的自訂管線，並使用自訂管線元件隨附於[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]將命名空間新增至回應訊息。 此自訂管線已部署具有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式將會做為接收管線設定 Wcf-webhttp 配接器時使用。  
  
 前執行此程序中的步驟，請確認[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]已安裝並設定您要在其中建立此應用程式的電腦上。  
  
#### <a name="to-add-a-custom-pipeline"></a>若要加入自訂管線  
  
1.  內**BtsSalesforceIntegration**方案，建立新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。 將專案命名`CustomPipeline`。  
  
2.  內**CustomPipeline**專案中，加入新的接收管線。 名稱為管線`AddNamespace.btp`。  
  
3.  內**解碼**階段的管線，從工具箱 拖曳和卸除**ESB 加入命名空間**管線元件。 內**解譯**階段、 拖曳和卸除**XML 解譯器**管線元件。  
  
    > [!NOTE]
    >  如果**ESB 加入命名空間**管線元件中沒有列出工具箱 中，您可以將它加入。 以滑鼠右鍵按一下**BizTalk 管線元件**索引標籤，然後再按一下**選擇項目**。 在**選擇工具箱項目**對話方塊中，按一下  **BizTalk 管線元件**索引標籤上，選取核取方塊**ESB 加入命名空間**元件，然後按一下  **確定**。  
  
4.  將強式名稱金鑰檔加入專案，並儲存專案。  
  
5.  以滑鼠右鍵按一下**CustomPipeline**專案，然後選取**屬性**。 在**部署**索引標籤上，針對**應用程式名稱**，輸入`SalesforceIntegration`。  
  
6.  將變更儲存至專案。  
  
 在本主題中，加入自訂的行為，向 Salesforce 和自訂管線新增至 Salesforce 回應的命名空間。 設定中的實體連接埠時，我們會使用這些自訂元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立 Visual Studio 中的 BizTalk Server 解決方案](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)