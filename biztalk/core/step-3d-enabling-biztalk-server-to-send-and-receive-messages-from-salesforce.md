---
title: 步驟 3d： 啟用 BizTalk Server 傳送和接收來自 Salesforce 的訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 470c4a72-1e97-4493-8958-33a13f793ffd
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d8489c484bdb88a292b998d31e7c6de90e0937c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975766"
---
# <a name="step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce"></a><span data-ttu-id="e4b33-102">步驟 3d： 啟用 BizTalk Server 傳送和接收來自 Salesforce 的訊息</span><span class="sxs-lookup"><span data-stu-id="e4b33-102">Step 3d: Enabling BizTalk Server to Send and Receive Messages from Salesforce</span></span>
<span data-ttu-id="e4b33-103">我們必須透過 Salesforce 進行驗證時使用的 REST 介面傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="e4b33-103">We must authenticate with Salesforce while sending messages using the REST interface.</span></span> <span data-ttu-id="e4b33-104">無法使用立即可用的 Wcf-webhttp 配接器，我們將使用來叫用 Salesforce 的 REST 介面支援 Salesforce REST 呼叫的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="e4b33-104">The authentication methods for REST calls supported by Salesforce are not available out of the box with the WCF-WebHttp adapter, which we’ll use to invoke Salesforce’s REST interface.</span></span> <span data-ttu-id="e4b33-105">因此，我們將建立自訂的 WCF 端點行為，然後將它附加到我們稍後會設定要叫用 Salesforce REST 介面的 Wcf-webhttp 傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="e4b33-105">So, we’ll create a custom WCF endpoint behavior and then attach it to WCF-WebHttp send adapter that we’ll configure to invoke the Salesforce REST interface.</span></span>  
  
 <span data-ttu-id="e4b33-106">同樣地，從 Salesforce 收到的 XML 回應將不會包含任何命名空間。</span><span class="sxs-lookup"><span data-stu-id="e4b33-106">Similarly, the XML response received from Salesforce will not contain any namespace.</span></span> <span data-ttu-id="e4b33-107">如[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理回應訊息和回應結構描述，回應訊息必須包含的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="e4b33-107">For [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to process the response message against the response schema, the response message must include the target namespace.</span></span> <span data-ttu-id="e4b33-108">因此，我們將建立自訂管線，使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]將命名空間新增至回應訊息。</span><span class="sxs-lookup"><span data-stu-id="e4b33-108">So, we’ll create a custom pipeline using the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] to add a namespace to the response message.</span></span> <span data-ttu-id="e4b33-109">然後，我們將使用的接收管線為這個自訂的管線要求-回應 Wcf-webhttp 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e4b33-109">We’ll then use this custom pipeline as the receive pipeline for request-response WCF-WebHttp send port.</span></span>  
  
## <a name="add-a-custom-wcf-behavior-for-salesforce-authentication"></a><span data-ttu-id="e4b33-110">自訂 WCF 將行為加入至 Salesforce 驗證</span><span class="sxs-lookup"><span data-stu-id="e4b33-110">Add a Custom WCF Behavior for Salesforce Authentication</span></span>  
 <span data-ttu-id="e4b33-111">Salesforce 提供不同的選項，用戶端應用程式透過 Salesforce 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="e4b33-111">Salesforce provides different options for client applications to authenticate with Salesforce.</span></span> <span data-ttu-id="e4b33-112">我們將使用何種 Salesforce 詞彙做為[使用者名稱密碼](http://go.microsoft.com/fwlink/?LinkId=287082)流程。</span><span class="sxs-lookup"><span data-stu-id="e4b33-112">We’ll use what Salesforce terms as the [Username-password](http://go.microsoft.com/fwlink/?LinkId=287082) flow.</span></span> <span data-ttu-id="e4b33-113">在用戶端，WCF 可讓您建立[訊息偵測器](http://msdn.microsoft.com/library/aa717047\(v=VS.90\).aspx)改變傳送之前或之後收到的訊息。</span><span class="sxs-lookup"><span data-stu-id="e4b33-113">On the client side, WCF enables you to create [Message Inspectors](http://msdn.microsoft.com/library/aa717047\(v=VS.90\).aspx) to alter messages before they are sent or after they are received.</span></span> <span data-ttu-id="e4b33-114">訊息偵測器是用戶端執行階段的延伸模組，並且會設定為行為。</span><span class="sxs-lookup"><span data-stu-id="e4b33-114">A message inspector is an extension to the client runtime and is configured as a behavior.</span></span> <span data-ttu-id="e4b33-115">行為，接著，新增至行為延伸項目。</span><span class="sxs-lookup"><span data-stu-id="e4b33-115">A behavior, in turn, is added to a behavior extension element.</span></span> <span data-ttu-id="e4b33-116">此行為延伸項目會註冊在 machine.config 項目名稱，使其可設定為 WCF 通訊埠上的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="e4b33-116">This behavior extension element is registered in the machine.config with an element name, which makes it available to be configured as a custom behavior on a WCF port.</span></span> <span data-ttu-id="e4b33-117">如需詳細資訊，請參閱[延伸 WCF 自訂行為](http://msdn.microsoft.com/magazine/cc163302.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e4b33-117">For more information, see [Extending WCF with Custom Behaviors](http://msdn.microsoft.com/magazine/cc163302.aspx).</span></span> <span data-ttu-id="e4b33-118">我們會使用此方法來合併使用 Salesforce 進行驗證的使用者名稱驗證流程。</span><span class="sxs-lookup"><span data-stu-id="e4b33-118">We are going to use this approach to incorporate the username-authentication flow for authenticating with Salesforce.</span></span> <span data-ttu-id="e4b33-119">我們要遵循的概略步驟如下：</span><span class="sxs-lookup"><span data-stu-id="e4b33-119">The broad steps that we’ll follow are:</span></span>  
  
-   <span data-ttu-id="e4b33-120">建立訊息偵測器可讓 HTTP POST 呼叫 Salesforce 驗證端點與接收存取權杖。</span><span class="sxs-lookup"><span data-stu-id="e4b33-120">Create a message inspector that makes an HTTP POST call to the Salesforce authentication endpoint and receives an access token.</span></span> <span data-ttu-id="e4b33-121">訊息偵測器將驗證語彙基元做為查詢訊息傳送至 Salesforce 的授權標頭的值。</span><span class="sxs-lookup"><span data-stu-id="e4b33-121">The message inspector then adds the authentication token as the value of the Authorization header of the query message being sent to Salesforce.</span></span> <span data-ttu-id="e4b33-122">訊息偵測器也會將 Accept 標頭加入至要求訊息，以便接收的回應會以 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="e4b33-122">The message inspector also adds the Accept header to the request message so that the response received is in an XML format.</span></span> <span data-ttu-id="e4b33-123">否則，Salesforce 會以預設的 JSON 格式傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="e4b33-123">Otherwise, Salesforce sends the message in the default JSON format.</span></span>  
  
-   <span data-ttu-id="e4b33-124">建立要套用至用戶端端點的訊息偵測器的端點行為。</span><span class="sxs-lookup"><span data-stu-id="e4b33-124">Create an endpoint behavior to apply the message inspector to the client endpoint.</span></span>  
  
-   <span data-ttu-id="e4b33-125">建立行為延伸項目，若要啟用端點行為的設定。</span><span class="sxs-lookup"><span data-stu-id="e4b33-125">Create a behavior extension element to enable configuration of the endpoint behavior.</span></span>  
  
#### <a name="to-create-a-message-inspector"></a><span data-ttu-id="e4b33-126">若要建立訊息偵測器</span><span class="sxs-lookup"><span data-stu-id="e4b33-126">To create a message inspector</span></span>  
  
1.  <span data-ttu-id="e4b33-127">做為一部分**BtsSalesforceIntegration**方案在 Visual Studio 中建立 C# 類別庫。</span><span class="sxs-lookup"><span data-stu-id="e4b33-127">As part of the **BtsSalesforceIntegration** solution in Visual Studio, create a C# Class Library.</span></span> <span data-ttu-id="e4b33-128">命名`Microsoft.BizTalk.Adapter.Behaviors`並加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="e4b33-128">Name it `Microsoft.BizTalk.Adapter.Behaviors` and add the following namespaces:</span></span>  
  
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
  
2.  <span data-ttu-id="e4b33-129">從 [方案總管] 中，將參考加入至`System.ServiceModel`， `System.Web.Extensions`，和`System.Configuration`。</span><span class="sxs-lookup"><span data-stu-id="e4b33-129">From the Solution Explorer, add references to `System.ServiceModel`, `System.Web.Extensions`, and `System.Configuration`.</span></span>  
  
3.  <span data-ttu-id="e4b33-130">將類別加入`SalesforceOAuthToken`具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b33-130">Add a class `SalesforceOAuthToken` with the following properties.</span></span> <span data-ttu-id="e4b33-131">此類別代表從 Salesforce 收到的授權 token。</span><span class="sxs-lookup"><span data-stu-id="e4b33-131">This class represents the authorization token that is received from Salesforce.</span></span>  
  
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
  
4.  <span data-ttu-id="e4b33-132">將類別加入`SalesforceRESTSecurityBehavior`實作`IClientMessageInspector`和`IEndpointBehavior`。</span><span class="sxs-lookup"><span data-stu-id="e4b33-132">Add a class `SalesforceRESTSecurityBehavior` that implements the `IClientMessageInspector` and the `IEndpointBehavior`.</span></span> <span data-ttu-id="e4b33-133">這個類別包含`HttpPost()`和`FetchOAuthToken()`進行 Salesforce 驗證端點的 HTTP POST 呼叫的方法會擷取授權權杖。</span><span class="sxs-lookup"><span data-stu-id="e4b33-133">This class includes the `HttpPost()` and `FetchOAuthToken()` methods that make an HTTP POST call to the Salesforce authentication endpoint to retrieve the authorization token.</span></span>  
  
     <span data-ttu-id="e4b33-134">因為`SalesforceRESTSecurityBehavior`類別會實作`IClientMessageInspector`介面，它必須實作兩種方法，`AfterReceiveReply()`和`BeforeSendRequest()`。</span><span class="sxs-lookup"><span data-stu-id="e4b33-134">Because the `SalesforceRESTSecurityBehavior` class implements the `IClientMessageInspector` interface, it must implement the two methods, `AfterReceiveReply()` and `BeforeSendRequest()`.</span></span> <span data-ttu-id="e4b33-135">此案例中我們不需要執行任何動作的一部分`AfterReceiverReply()`方法。</span><span class="sxs-lookup"><span data-stu-id="e4b33-135">For this scenario we do not need to do anything as part of the `AfterReceiverReply()` method.</span></span> <span data-ttu-id="e4b33-136">不過，`BeforeSendRequest()`方法會叫用`FetchOAuthToken()`方法中，依序呼叫`HttpPost()`方法。</span><span class="sxs-lookup"><span data-stu-id="e4b33-136">However, the `BeforeSendRequest()` method invokes the `FetchOAuthToken()` method, which in turn calls the `HttpPost()` method.</span></span> <span data-ttu-id="e4b33-137">`BeforeSendRequest()`方法接著會將授權權杖做為訊息標頭的一部分。</span><span class="sxs-lookup"><span data-stu-id="e4b33-137">The `BeforeSendRequest()` method then adds the authorization token as part of the message header.</span></span> <span data-ttu-id="e4b33-138">它也會加入**接受**標頭，以確保從 Salesforce 收到的回應是以 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="e4b33-138">It also adds the **Accept** header to ensure that that the response received from Salesforce is in an XML format.</span></span>  
  
     <span data-ttu-id="e4b33-139">`IEndpointBehavior`實作只會將訊息偵測器類別新增至用戶端端點行為。</span><span class="sxs-lookup"><span data-stu-id="e4b33-139">The `IEndpointBehavior` implementation simply adds the message inspector class to the client endpoint behavior.</span></span>  
  
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
  
5.  <span data-ttu-id="e4b33-140">上一個步驟中，我們會建立訊息偵測器套用至用戶端端點行為類別。</span><span class="sxs-lookup"><span data-stu-id="e4b33-140">In the previous step we created a behavior class that applies the message inspector to the client endpoint.</span></span> <span data-ttu-id="e4b33-141">我們現在需要將此行為提供給組態經驗 Wcf-webhttp 配接器傳送要求訊息至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="e4b33-141">We now need to make this behavior available to the configuration experience for the WCF-WebHttp adapter that will send the request message to Salesforce.</span></span> <span data-ttu-id="e4b33-142">若要讓此行為可進行設定，我們需要如何做兩件事：</span><span class="sxs-lookup"><span data-stu-id="e4b33-142">To make this behavior available for configuration we need to do two things:</span></span>  
  
    -   <span data-ttu-id="e4b33-143">建立衍生自類別`BehaviorExtensionElement`</span><span class="sxs-lookup"><span data-stu-id="e4b33-143">Create a class that derives from the `BehaviorExtensionElement`</span></span>  
  
    -   <span data-ttu-id="e4b33-144">登錄中的您 BehavaiorExtensionElement\<延伸\>\\< behaviorExtensions\> machine.config 使用項目名稱中的項目。</span><span class="sxs-lookup"><span data-stu-id="e4b33-144">Register your BehavaiorExtensionElement in the \<extensions\>\\<behaviorExtensions\> element in the machine.config using an element name.</span></span>  
  
     <span data-ttu-id="e4b33-145">我們也可以加入這個類別組態屬性，使其可從 Wcf-webhttp 配接器組態 UI。</span><span class="sxs-lookup"><span data-stu-id="e4b33-145">We’ll also add configuration properties to this class so that they are available from the WCF-WebHttp adapter configuration UI.</span></span>  
  
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
  
6.  <span data-ttu-id="e4b33-146">將強式名稱金鑰檔加入專案，並建置專案。</span><span class="sxs-lookup"><span data-stu-id="e4b33-146">Add a strong name key file to the project and build the project.</span></span> <span data-ttu-id="e4b33-147">一旦成功建置專案，加入組件`Microsoft.BizTalk.Adapter.Behaviors`到 GAC。</span><span class="sxs-lookup"><span data-stu-id="e4b33-147">Once the project builds successfully, add the assembly `Microsoft.BizTalk.Adapter.Behaviors` to the GAC.</span></span>  
  
7.  <span data-ttu-id="e4b33-148">System.ServiceModel\Extensions\BehaviorExtensions 在 machine.config 中加入下列項目。</span><span class="sxs-lookup"><span data-stu-id="e4b33-148">Add the following entry in the machine.config under System.ServiceModel\Extensions\BehaviorExtensions.</span></span>  
  
    ```  
    <add name="Microsoft.BizTalk.Adapter.Behaviors.Demo.Salesforce" type="Microsoft.BizTalk.Adapter.Behaviors.SalesforceRESTBehaviorElement, Microsoft.BizTalk.Adapter.Behaviors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=45bd7fe67ef032db"/>  
    ```  
  
     <span data-ttu-id="e4b33-149">您可以擷取從 GAC 的組件公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e4b33-149">You can retrieve the public key token for the assembly from the GAC.</span></span> <span data-ttu-id="e4b33-150">此外，如果您要建立此應用程式在 64 位元電腦上，您必須將此項目加入 machine.config 的 32 位元和 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="e4b33-150">Also, if you are creating this application on a 64-bit computer, you must add this entry to both 32-bit and 64-bit versions of the machine.config.</span></span>  
  
## <a name="add-a-custom-pipeline-to-add-namespace-to-the-salesforce-response"></a><span data-ttu-id="e4b33-151">新增自訂管線新增至 Salesforce 回應的命名空間</span><span class="sxs-lookup"><span data-stu-id="e4b33-151">Add a Custom Pipeline to Add Namespace to the Salesforce Response</span></span>  
 <span data-ttu-id="e4b33-152">從 Salesforce 收到的回應不包含命名空間。</span><span class="sxs-lookup"><span data-stu-id="e4b33-152">The response received from Salesforce does not include a namespace.</span></span> <span data-ttu-id="e4b33-153">不過，處理回應訊息和回應結構描述 (QueryResult.xsd) 我們必須在 Salesforce 回應中包含命名空間。</span><span class="sxs-lookup"><span data-stu-id="e4b33-153">However, to process the response message against the response schema (QueryResult.xsd) we must include the namespace in the Salesforce response.</span></span> <span data-ttu-id="e4b33-154">在本節中，我們建立的自訂管線，並使用自訂管線元件隨附於[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]將命名空間新增至回應訊息。</span><span class="sxs-lookup"><span data-stu-id="e4b33-154">In this section, we create a custom pipeline and use a custom pipeline component shipped with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] to add a namespace to the response message.</span></span> <span data-ttu-id="e4b33-155">此自訂管線已部署具有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式將會做為接收管線設定 Wcf-webhttp 配接器時使用。</span><span class="sxs-lookup"><span data-stu-id="e4b33-155">This custom pipeline is deployed with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application and will be used as the receive pipeline while configuring the WCF-WebHttp adapter.</span></span>  
  
 <span data-ttu-id="e4b33-156">前執行此程序中的步驟，請確認[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]已安裝並設定您要在其中建立此應用程式的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e4b33-156">Before performing the steps in this procedure, ensure that [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is installed and configured on the computer where you are creating this application.</span></span>  
  
#### <a name="to-add-a-custom-pipeline"></a><span data-ttu-id="e4b33-157">若要加入自訂管線</span><span class="sxs-lookup"><span data-stu-id="e4b33-157">To add a custom pipeline</span></span>  
  
1.  <span data-ttu-id="e4b33-158">內**BtsSalesforceIntegration**方案，建立新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="e4b33-158">Within the **BtsSalesforceIntegration** solution, create a new [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="e4b33-159">將專案命名`CustomPipeline`。</span><span class="sxs-lookup"><span data-stu-id="e4b33-159">Name the project `CustomPipeline`.</span></span>  
  
2.  <span data-ttu-id="e4b33-160">內**CustomPipeline**專案中，加入新的接收管線。</span><span class="sxs-lookup"><span data-stu-id="e4b33-160">Within the **CustomPipeline** project, add a new receive pipeline.</span></span> <span data-ttu-id="e4b33-161">名稱為管線`AddNamespace.btp`。</span><span class="sxs-lookup"><span data-stu-id="e4b33-161">Name the pipeline as `AddNamespace.btp`.</span></span>  
  
3.  <span data-ttu-id="e4b33-162">內**解碼**階段的管線，從工具箱 拖曳和卸除**ESB 加入命名空間**管線元件。</span><span class="sxs-lookup"><span data-stu-id="e4b33-162">Within the **Decode** stage of the pipeline, from the toolbox, drag and drop the **ESB Add Namespace** pipeline component.</span></span> <span data-ttu-id="e4b33-163">內**解譯**階段、 拖曳和卸除**XML 解譯器**管線元件。</span><span class="sxs-lookup"><span data-stu-id="e4b33-163">Within the **Disassemble** stage, drag and drop the **XML disassembler** pipeline component.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e4b33-164">如果**ESB 加入命名空間**管線元件中沒有列出工具箱 中，您可以將它加入。</span><span class="sxs-lookup"><span data-stu-id="e4b33-164">If the **ESB Add Namespace** pipeline component is not listed in the toolbox, you can add it.</span></span> <span data-ttu-id="e4b33-165">以滑鼠右鍵按一下**BizTalk 管線元件**索引標籤，然後再按一下**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="e4b33-165">Right-click the **BizTalk Pipeline Components** tab, and then click **Choose Items**.</span></span> <span data-ttu-id="e4b33-166">在**選擇工具箱項目**對話方塊中，按一下  **BizTalk 管線元件**索引標籤上，選取核取方塊**ESB 加入命名空間**元件，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="e4b33-166">In the **Choose Toolbox Items** dialog box, click the **BizTalk Pipeline Components** tab, select the check box for **ESB Add Namespace** component, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e4b33-167">將強式名稱金鑰檔加入專案，並儲存專案。</span><span class="sxs-lookup"><span data-stu-id="e4b33-167">Add a strong name key file to the project and save the project.</span></span>  
  
5.  <span data-ttu-id="e4b33-168">以滑鼠右鍵按一下**CustomPipeline**專案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="e4b33-168">Right-click the **CustomPipeline** project and select **Properties**.</span></span> <span data-ttu-id="e4b33-169">在**部署**索引標籤上，針對**應用程式名稱**，輸入`SalesforceIntegration`。</span><span class="sxs-lookup"><span data-stu-id="e4b33-169">In the **Deployment** tab, for **Application Name**, enter `SalesforceIntegration`.</span></span>  
  
6.  <span data-ttu-id="e4b33-170">將變更儲存至專案。</span><span class="sxs-lookup"><span data-stu-id="e4b33-170">Save changes to the project.</span></span>  
  
 <span data-ttu-id="e4b33-171">在本主題中，加入自訂的行為，向 Salesforce 和自訂管線新增至 Salesforce 回應的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e4b33-171">In this topic, added a custom behavior to authenticate with Salesforce and a custom pipeline to add a namespace to the Salesforce response.</span></span> <span data-ttu-id="e4b33-172">設定中的實體連接埠時，我們會使用這些自訂元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="e4b33-172">We’ll use these custom components while configuring the physical ports in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b33-173">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4b33-173">See Also</span></span>  
 [<span data-ttu-id="e4b33-174">步驟 3：在 Visual Studio 中建立 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="e4b33-174">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)