---
title: 使用 WCF LOB 配接器 SDK 開發最佳做法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ea3a13b-e41f-4920-bf0d-26f7bb145aa3
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f42980d93c7872811ea26fb9fc21a97f7e4e8e2d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991319"
---
# <a name="development-best-practices-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="943df-102">使用 WCF LOB 配接器 SDK 開發最佳做法</span><span class="sxs-lookup"><span data-stu-id="943df-102">Development best practices using the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="943df-103">您可以使用本主題中的最佳作法，以改善您的應用程式和配接器。</span><span class="sxs-lookup"><span data-stu-id="943df-103">You can use the best practices in this topic to improve your applications and adapters.</span></span>  

## <a name="call-abort-before-close-on-channel-exception"></a><span data-ttu-id="943df-104">呼叫中止前關閉通道例外狀況</span><span class="sxs-lookup"><span data-stu-id="943df-104">Call Abort Before Close on Channel Exception</span></span>  
 <span data-ttu-id="943df-105">當您撰寫的應用程式使用 WCF 通道模型時，您應該呼叫`IRequestChannel.Abort`再呼叫`ChannelFactory.Close`。</span><span class="sxs-lookup"><span data-stu-id="943df-105">When you write an application that uses the WCF channel model, you should call `IRequestChannel.Abort` before calling `ChannelFactory.Close`.</span></span> <span data-ttu-id="943df-106">如果您未這麼做，`ChannelFactory.Close`擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="943df-106">If you do not, `ChannelFactory.Close` throws an exception.</span></span>  

 <span data-ttu-id="943df-107">在下列範例中，嘗試通道作業在 try/catch 區塊內。</span><span class="sxs-lookup"><span data-stu-id="943df-107">In the following example, channel operations are attempted within a try/catch block.</span></span> <span data-ttu-id="943df-108">如果發生例外狀況，則會中止通道。</span><span class="sxs-lookup"><span data-stu-id="943df-108">If an exception occurs, the channel is aborted.</span></span>  

```csharp  
ChannelFactory<IRequestChannel> cf = new  ChannelFactory<IRequestChannel>();  
IRequestChannel channel = null;  
try  
{  
  cf.Open();  
  channel = cf.CreateChannel();  
  channel.Open();  
  channel.Request();// This causes the channel to go into a faulted state.  
  channel.Close();  
}  
catch (Exception e)  
{  
  // Abort the channel if we have one  
  if(channel != null)  
    channel.Abort();  
}  
finally  
{  
  if (cf.State == CommunicationState.Opened)  
  {  
    cf.Close(); // It throws an exception that the channel is in a faulted state.  
  }  
}  
```  

## <a name="implement-both-asynchronous-and-synchronous-handlers"></a><span data-ttu-id="943df-109">實作非同步和同步處理常式</span><span class="sxs-lookup"><span data-stu-id="943df-109">Implement Both Asynchronous and Synchronous Handlers</span></span>  
 <span data-ttu-id="943df-110">可能的話，請在您的配接器實作非同步和同步處理常式。</span><span class="sxs-lookup"><span data-stu-id="943df-110">If possible, implement both asynchronous and synchronous handlers in your adapter.</span></span> <span data-ttu-id="943df-111">如果您的配接器只會實作同步呼叫，您可能會發生封鎖問題時處理的訊息，或配接器用在多執行緒環境中的大型磁碟區。</span><span class="sxs-lookup"><span data-stu-id="943df-111">If your adapter only implements synchronous calls, you may run into blocking issues when processing a large volume of messages or when the adapter is used in a multithreaded environment.</span></span>  

## <a name="use-connection-pooling"></a><span data-ttu-id="943df-112">使用連接共用</span><span class="sxs-lookup"><span data-stu-id="943df-112">Use Connection Pooling</span></span>  
 <span data-ttu-id="943df-113">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]支援預設的連接共用。</span><span class="sxs-lookup"><span data-stu-id="943df-113">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] supports connection pooling by default.</span></span> <span data-ttu-id="943df-114">不過，它是由配接器開發人員判斷哪一個連接共用來公開做為繫結屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="943df-114">However, it is up to the adapter developer to determine which connection pooling properties to expose as binding properties.</span></span> <span data-ttu-id="943df-115">可用的連接集區設定中定義`Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`。</span><span class="sxs-lookup"><span data-stu-id="943df-115">The available Connection Pool settings are defined within `Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`.</span></span>  

 <span data-ttu-id="943df-116">沒有任何選項內[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]輕鬆公開這些介面卡連接屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="943df-116">There are no options within the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to easily expose these properties as adapter connection properties.</span></span> <span data-ttu-id="943df-117">配接器實作中，配接器開發人員必須手動定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="943df-117">The adapter developer must manually define the properties in the adapter implementation.</span></span>  

```csharp  
public CustomAdapter(): base()  
{  
   this.Settings.ConnectionPool.EnablePooling = true;  
   this.Settings.ConnectionPool.HandlersShareSameConnection = true;  
   this.Settings.ConnectionPool.MaxConnectionsPerSystem = 50;  
   this.Settings.ConnectionPool.MaxAvailableConnections = 5;  
}  
```  

## <a name="ensure-that-the-adapter-supports-two-way-operations"></a><span data-ttu-id="943df-118">請確定此配接器支援雙向作業</span><span class="sxs-lookup"><span data-stu-id="943df-118">Ensure That the Adapter Supports Two-Way Operations</span></span>  
 <span data-ttu-id="943df-119">如果您的配接器從 BizTalk Server 呼叫，就必須支援雙向作業，即使傳回的值為 void。</span><span class="sxs-lookup"><span data-stu-id="943df-119">If your adapter is called from BizTalk Server, it must support two-way operations, even if the return value is void.</span></span> <span data-ttu-id="943df-120">這是因為 BizTalk Server 預期任何傳出的要求，從傳回的回應，而且如果您的配接器只會實作單向作業，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="943df-120">This is because BizTalk Server expects a response returned from any outgoing request, and throws an exception if your adapter only implements one-way operations.</span></span>  

 <span data-ttu-id="943df-121">以下是傳回 void 的要求-回應合約的範例。</span><span class="sxs-lookup"><span data-stu-id="943df-121">Here is an example of a request-response contract that returns void.</span></span>  

```csharp  
[ServiceContract(Namespace=”Http:Microsoft.BizTalk.Samples.WCFAdapterSample”)]  
public interface ICalculator  
{  
   [OperationContract]  
   void Add(double n1, double n2);  
}  
```  

## <a name="implement-tracing"></a><span data-ttu-id="943df-122">實作追蹤</span><span class="sxs-lookup"><span data-stu-id="943df-122">Implement Tracing</span></span>  
 <span data-ttu-id="943df-123">在開發週期中，它也許好像不太重要新增至您的配接器的追蹤，因為您可以逐步執行程式碼和偵錯任何問題。</span><span class="sxs-lookup"><span data-stu-id="943df-123">During the development cycle, it might not seem important to add tracing to your adapter, since you can step through the code and debug any problems.</span></span> <span data-ttu-id="943df-124">不過，在生產環境中安裝配接器之後，您可能無法使用執行階段偵錯來隔離問題。</span><span class="sxs-lookup"><span data-stu-id="943df-124">However, once the adapter is installed in a production environment, you might not be able to use run-time debugging to isolate problems.</span></span> <span data-ttu-id="943df-125">如果您已啟用追蹤，在您的配接器，它可用來找出發生失敗的位置。</span><span class="sxs-lookup"><span data-stu-id="943df-125">If you have enabled tracing throughout your adapter, it can be used to isolate where failures are occurring.</span></span>  

 <span data-ttu-id="943df-126">請參閱[追蹤配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/trace-an-adapter-with-the-wcf-lob-adapter-sdk.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="943df-126">See [Trace an adapter with the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/trace-an-adapter-with-the-wcf-lob-adapter-sdk.md) for further details.</span></span>  

## <a name="use-uri-properties-for-frequently-changed-settings"></a><span data-ttu-id="943df-127">URI 屬性用於經常變更的設定</span><span class="sxs-lookup"><span data-stu-id="943df-127">Use URI Properties for Frequently Changed Settings</span></span>  
 <span data-ttu-id="943df-128">在決定是否要將自訂屬性公開為繫結或 URI 屬性，建議使用 URI 屬性，如果值經常變更。</span><span class="sxs-lookup"><span data-stu-id="943df-128">When deciding whether to expose a custom property as a binding or URI property, it is recommended to use a URI property if the value changes often.</span></span> <span data-ttu-id="943df-129">繫結屬性應保留給極少變更的值。</span><span class="sxs-lookup"><span data-stu-id="943df-129">Binding properties should be reserved for values that rarely change.</span></span>  

 <span data-ttu-id="943df-130">繫結屬性範例會使用所有連接的資料庫伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="943df-130">An example binding property would be a database server name that is used by all connections.</span></span> <span data-ttu-id="943df-131">特定資料表或預存程序，以供該特定連線，就會是範例 URI 屬性。</span><span class="sxs-lookup"><span data-stu-id="943df-131">An example URI property would be a specific table or stored procedure to be used by that specific connection.</span></span>  

## <a name="do-not-pass-user-name-or-password-values-in-the-uri"></a><span data-ttu-id="943df-132">不要在 URI 中傳遞使用者名稱或密碼值</span><span class="sxs-lookup"><span data-stu-id="943df-132">Do Not Pass User Name or Password Values in the URI</span></span>  
 <span data-ttu-id="943df-133">如果您的配接器需要呼叫端的認證，則建議使用**ClientCredentials**類別來擷取認證值，而不是傳遞做為 URI 的一部分的用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="943df-133">If your adapter requires the caller’s credentials, it is recommended to use the **ClientCredentials** class to retrieve credential values instead of passing client credentials as part of the URI.</span></span> <span data-ttu-id="943df-134">**ClientCredentials**類別是標準的功能的 WCF，以供將認證資訊從用戶端傳遞至服務，以更安全的方式。</span><span class="sxs-lookup"><span data-stu-id="943df-134">The **ClientCredentials** class is a standard feature of WCF that is intended for passing credential information from the client to the service in a more secure manner.</span></span> <span data-ttu-id="943df-135">URI 字串的一部分傳遞的使用者資訊可能會公開在傳輸過程中的使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="943df-135">Passing the user information as part of the URI string may expose the user information while in transit.</span></span>  

 <span data-ttu-id="943df-136">下表顯示傳遞認證的建議的方法。</span><span class="sxs-lookup"><span data-stu-id="943df-136">The recommended methods of passing credentials are shown in the following table.</span></span>  


|      <span data-ttu-id="943df-137">方法</span><span class="sxs-lookup"><span data-stu-id="943df-137">Method</span></span>       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              <span data-ttu-id="943df-138">描述</span><span class="sxs-lookup"><span data-stu-id="943df-138">Description</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    <span data-ttu-id="943df-139">設計階段</span><span class="sxs-lookup"><span data-stu-id="943df-139">Design time</span></span>    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                <span data-ttu-id="943df-140">當使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您可以指定配接器支援的用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="943df-140">When using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], you can specify the client credential types that the adapter supports.</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|     <span data-ttu-id="943df-141">執行階段</span><span class="sxs-lookup"><span data-stu-id="943df-141">Run time</span></span>      | <span data-ttu-id="943df-142">使用時產生的.NET CLR proxy，您可以透過程式設計方式設定用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="943df-142">When using a generated .NET CLR proxy, you can programmatically set the client credentials.</span></span><br /><br /> `static void Main(string[] args) {    EchoServiceClient client = new EchoServiceClient();    client.ClientCredentials.UserName.UserName = "TestUser";    client.ClientCredentials.UserName.Password = "TestPassword";    string response=client.EchoString("Test String"); }`<br /><br /> <span data-ttu-id="943df-143">或者，如果您需要直接互動的通道，您可以使用 WCF 通道模型來建立通道處理站時，指定用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="943df-143">Alternatively, if you need to interact with the channel directly, you can use the WCF channel model to specify the client credentials when creating a channel factory.</span></span><br /><br /> `EchoAdapterBinding binding = new EchoAdapterBinding(); binding.Count = 3; ClientCredentials clientCredentials = new ClientCredentials(); clientCredentials.UserName.UserName = "TestUser"; clientCredentials.UserName.Password = "TestPassword"; BindingParameterCollection bindingParms = new BindingParameterCollection(); bindingParms.Add(clientCredentials); EndpointAddress address = new EndpointAddress("echo://"); IChannelFactory<IRequestChannel> requestChannelFactory = binding.BuildChannelFactory<IRequestChannel>(bindingParms); requestChannelFactory.Open();` |
| <span data-ttu-id="943df-144">WCF 組態</span><span class="sxs-lookup"><span data-stu-id="943df-144">WCF configuration</span></span> |                                                                                                                                                                                                                                               <span data-ttu-id="943df-145">在 用戶端組態檔中，新增\<endpointBehaviors\>項目，包括\<clientCredentials\>。</span><span class="sxs-lookup"><span data-stu-id="943df-145">In the client configuration file, add an \<endpointBehaviors\> element that includes \<clientCredentials\>.</span></span><br /><br /> `<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">       <system.serviceModel>           . . . . .           <behaviors>             <endpointBehaviors>               <behavior name="clientEndpointCredential">                 <clientCredentials>                   <windows allowNtlm="false" allowedImpersonationLevel="Delegation" />                    </clientCredentials>               </behavior>             </endpointBehaviors>           </behaviors>       </system.serviceModel>   </configuration>`                                                                                                                                                                                                                                               |
|   <span data-ttu-id="943df-146">使用 BizTalk</span><span class="sxs-lookup"><span data-stu-id="943df-146">Using BizTalk</span></span>   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                 <span data-ttu-id="943df-147">當取用您的配接器使用 WCF 配接器，您可以加入**clientCredentials**上的行為延伸模組**行為** 索引標籤。這已新增之後，您可以設定所需的用戶端認證的端點行為。</span><span class="sxs-lookup"><span data-stu-id="943df-147">When using the WCF adapter to consume your adapter, you can add the **clientCredentials** behavior extension on the **Behavior** tab. Once this has been added, you can set the desired client credentials in the endpoint behavior.</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

## <a name="do-not-return-both-strongdatasettype-and-weakdatasettype"></a><span data-ttu-id="943df-148">不會傳回同時 StrongDataSetType 和 WeakDataSetType</span><span class="sxs-lookup"><span data-stu-id="943df-148">Do Not Return Both StrongDataSetType and WeakDataSetType</span></span>  
 <span data-ttu-id="943df-149">如果您的配接器傳回`DataSet`，使用任何一種`Microsoft.ServiceModel.Channels.Common.QualifiedType.StrongDataSetType%2A`或`Microsoft.ServiceModel.Channels.Common.QualifiedType.WeakDataSetType%2A`，但不要兩者同時使用。</span><span class="sxs-lookup"><span data-stu-id="943df-149">If your adapter returns a `DataSet`, use either `Microsoft.ServiceModel.Channels.Common.QualifiedType.StrongDataSetType%2A` or `Microsoft.ServiceModel.Channels.Common.QualifiedType.WeakDataSetType%2A`, but do not use both at the same time.</span></span> <span data-ttu-id="943df-150">所產生的這兩種類型的命名空間與根節點名稱都相同，而且不能同時存在於 WSDL。</span><span class="sxs-lookup"><span data-stu-id="943df-150">The root node name and namespace produced by both types are identical, and cannot exist simultaneously in a WSDL.</span></span>  

 <span data-ttu-id="943df-151">雖然`WeakDataSetType`並`StrongDataSetType`都代表`System.Data.DataSet`，`StrongDataSetType`可以更輕鬆地使用.NET 應用程式中，因為產生的 proxy 會顯示為`System.Data.Dataset`。</span><span class="sxs-lookup"><span data-stu-id="943df-151">While `WeakDataSetType` and `StrongDataSetType` both represent a `System.Data.DataSet`, `StrongDataSetType` is easier to use in .NET applications, since the proxy generated appears as `System.Data.Dataset`.</span></span> <span data-ttu-id="943df-152">所產生的 proxy`WeakDataSetType`是`XmlElement[]`，這是較難在.NET 應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="943df-152">The proxy generated by `WeakDataSetType` is `XmlElement[]`, which is more difficult to use in a .NET application.</span></span>  <span data-ttu-id="943df-153">BizTalk Server 無法使用從傳回的結構描述`StrongDataSet`，但能夠取用`WeakDataSetType`。</span><span class="sxs-lookup"><span data-stu-id="943df-153">BizTalk Server cannot consume the schema returned from `StrongDataSet`, but is able to consume `WeakDataSetType`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="943df-154">`StrongDataSetType` 和`WeakDataSetType`只能控制用戶端應用程式如何解譯配接器所傳遞的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="943df-154">`StrongDataSetType` and `WeakDataSetType` only control how the client application interprets the XML messages passed by the adapter.</span></span> <span data-ttu-id="943df-155">XML 訊息會是相同不論所指定型別。</span><span class="sxs-lookup"><span data-stu-id="943df-155">The XML message is the same regardless of which type is specified.</span></span>  

> [!NOTE]
>  <span data-ttu-id="943df-156">傳回時`StrongDataSetType`，您必須設定`Microsoft.ServiceModel.Channels.Common.MetadataSettings.CompileWsdl%2A`至`false`。</span><span class="sxs-lookup"><span data-stu-id="943df-156">When returning `StrongDataSetType`, you must set `Microsoft.ServiceModel.Channels.Common.MetadataSettings.CompileWsdl%2A` to `false`.</span></span> <span data-ttu-id="943df-157">當設定為`true`，預設值，`XmlSchemaSet::Compile`呼叫中以確保沒有任何錯誤，在 WSDL 中配接器，但是結構描述所產生`StrongDataSetType`會產生例外狀況中的`XmlSchemaSet`。</span><span class="sxs-lookup"><span data-stu-id="943df-157">When set to `true`, the default, `XmlSchemaSet::Compile` is called within the adapter to ensure there are no errors in the WSDL, however the schema produced by `StrongDataSetType` generates an exception in `XmlSchemaSet`.</span></span>  
>   
>  <span data-ttu-id="943df-158">設定`CompileWsdl`至`false`WSDL 內的配接器和驗證的結構描述驗證 proxy 產生期間所發生的許可。</span><span class="sxs-lookup"><span data-stu-id="943df-158">Setting `CompileWsdl` to `false` bypasses WSDL schema validation within the adapter and validation occurs during proxy generation.</span></span>  <span data-ttu-id="943df-159">Svcutil.exe 之類的公用程式可產生兩個 proxy`StrongDataSetType`和`WeakDataSetType`。</span><span class="sxs-lookup"><span data-stu-id="943df-159">Utilities such as svcutil.exe are able to generate a proxy for both `StrongDataSetType` and `WeakDataSetType`.</span></span>  

 <span data-ttu-id="943df-160">若要使用 BizTalk 和.NET 環境，請考慮實作允許切換兩個傳回的型別，如取決於環境的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="943df-160">To work with both BizTalk and .NET environments, consider implementing a binding property that allows switching between the two return types as dictated by the environment.</span></span>  

```csharp  
internal static QualifiedType GetDataSetQualifiedType(MyAdapterBindingProperties bindingProperties)  
{  
   if (bindingProperties.EnableBizTalkCompatibility)  
      return QualifiedType.WeakDataSetType;  
   else  
      return QualifiedType.StrongDataSetType;  
}  
```  

## <a name="create-meaningful-xsd-schema-names-in-biztalk-server"></a><span data-ttu-id="943df-161">BizTalk Server 中建立有意義的 XSD 結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="943df-161">Create Meaningful XSD Schema Names in BizTalk Server</span></span>  
 <span data-ttu-id="943df-162">使用時[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]設計階段工具，建立 BizTalk 專案中產生的 XSD 結構描述的名稱使用`DefaultXsdFileNamePrefix`屬性， `fileNameHint` WSDL 中的註解，並在必要時，唯一的整數值。</span><span class="sxs-lookup"><span data-stu-id="943df-162">When using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] design-time tool, the name of the XSD schema generated in your BizTalk project is created using the `DefaultXsdFileNamePrefix` property, the `fileNameHint` annotation in the WSDL and, if required, a unique integer value.</span></span>  

 <span data-ttu-id="943df-163">例如，如果`DefaultXsdFileNamePrefix`設定為"MyAdapter 」 和`fileNameHint`註解設為"Stream"、 XSD 結構描述，建立名為 MyAdapterStream.xsd。</span><span class="sxs-lookup"><span data-stu-id="943df-163">For example, if `DefaultXsdFileNamePrefix` is set to “MyAdapter” and the `fileNameHint` annotation is set to “Stream”, the XSD schema created is named MyAdapterStream.xsd.</span></span>  

```  
<xs:schema elementFormDefault='qualified' targetNamespace='http://schemas.microsoft.com/Message' xmlns:xs='http://www.w3.org/2001/XMLSchema' xmlns:tns='http://schemas.microsoft.com/Message'>  
<xs:annotation>  
<xs:appinfo>  
<fileNameHint xmlns='http://schemas.microsoft.com/servicemodel/adapters/metadata/xsd'>Stream</fileNameHint>  
</xs:appinfo>  
</xs:annotation>  
<xs:simpleType name='StreamBody'>  
<xs:restriction base='xs:base64Binary' />  
</xs:simpleType>  
</xs:schema>  

```  

> [!NOTE]
>  <span data-ttu-id="943df-164">預設值`DefaultXsdFileNamePrefix`是您的繫結的名稱。</span><span class="sxs-lookup"><span data-stu-id="943df-164">The default value of `DefaultXsdFileNamePrefix` is the name of your binding.</span></span> <span data-ttu-id="943df-165">若要指定不同的值，覆寫`DefaultXsdFileNamePrefix`在您的配接器類別衍生自`Microsoft.ServiceModel.Channels.Common.AdapterBinding`。</span><span class="sxs-lookup"><span data-stu-id="943df-165">To specify a different value, override `DefaultXsdFileNamePrefix` in your Adapter class that is derived from `Microsoft.ServiceModel.Channels.Common.AdapterBinding`.</span></span>  

 <span data-ttu-id="943df-166">有兩種可能的方法，以新增`fileNameHint`結構描述的註釋： 覆寫 匯出...結構描述 OperationMetadata\TypeMetadata 或覆寫 IWsdlRetrieval 實作的介面卡上的方法。</span><span class="sxs-lookup"><span data-stu-id="943df-166">There are two possible methods to add the `fileNameHint` annotation to the schema: override the Export…Schema methods on OperationMetadata\TypeMetadata or override the IWsdlRetrieval implementation of the adapter.</span></span> <span data-ttu-id="943df-167">何種方法，您可以呼叫基底實作，並再將註解新增至結構描述集合中的結構描述。</span><span class="sxs-lookup"><span data-stu-id="943df-167">For either method, you can call the base implementation and then add the annotation to the schemas in the schema collection.</span></span>  

> [!NOTE]
>  <span data-ttu-id="943df-168">當覆寫 匯出...結構描述的方法，可能會有相同的結構描述; 的多個作業/型別定義配接器應該要確定多次`fileNameHints`相同的結構描述的註解不會衝突。</span><span class="sxs-lookup"><span data-stu-id="943df-168">When overriding the Export…Schema methods, there may be multiple operation/type definitions in the same schema; the adapter should make sure that multiple occurrences of the `fileNameHints` annotation in the same schema do not conflict.</span></span> <span data-ttu-id="943df-169">[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會使用第一個出現`fileNameHint`如果結構描述中發生多次。</span><span class="sxs-lookup"><span data-stu-id="943df-169">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] uses the first occurrence of `fileNameHint` if it occurs multiple times within a schema.</span></span>  

 <span data-ttu-id="943df-170">在下列範例中，IWsdlRetrieval 用來新增`fileNameHint`至 WSDL 附註。</span><span class="sxs-lookup"><span data-stu-id="943df-170">In the following example, IWsdlRetrieval is used to add the `fileNameHint` annotation to the WSDL.</span></span>  

```csharp  
sealed class MyAdapterWsdlRetrieval : IWsdlRetrieval  
{  
   IWsdlRetrieval mBaseWsdlRetrieval;  
   public MyAdapterWsdlRetrieval(IWsdlRetrieval baseWsdlRetrieval)  
   {  
      mBaseWsdlRetrieval = baseWsdlRetrieval;  
   }  

   ServiceDescription IWsdlRetrieval.GetWsdl(Microsoft.ServiceModel.Channels.MetadataRetrievalNode[] nodes, Uri uri, TimeSpan timeout)  
   {  
      ServiceDescription baseDesc = mBaseWsdlRetrieval.GetWsdl(nodes, uri, timeout);  
      foreach (XmlSchema schema in baseDesc.Types.Schemas)  
      {  
         CreateFileNameHint(schema);  
      }  
      return baseDesc;  
   }  

   void CreateFileNameHint(XmlSchema schema)  
   {  
      string targetNamespace = schema.TargetNamespace;  
      if (string.IsNullOrEmpty(targetNamespace))  
         return;  
      string fileNameHint = null;  
      //determine the filename based on namespace  
      if (targetNamespace.StartsWith("myadapter:// adapters.samples.myadaptpter/HelloWorld"))  
      {  
         fileNameHint = "HelloWorld";  
      }  
      if (targetNamespace.StartsWith("myadapter:// adapters.samples.myadapter/Hello"))  
      {  
         fileNameHint = "Hello";  
      }  
      //create the annotation and populate it with fileNameHint  
      XmlSchemaAnnotation annotation = new XmlSchemaAnnotation();  
      XmlSchemaAppInfo appInfo = new XmlSchemaAppInfo();  
      XmlDocument doc = new XmlDocument();  
      XmlNode[] fileNameHintNodes = new XmlNode[1];  
      fileNameHintNodes[0] = doc.CreateElement(null, "fileNameHint", "http://schemas.microsoft.com/servicemodel/adapters/metadata/xsd");  
      fileNameHintNodes[0].AppendChild(doc.CreateTextNode(fileNameHint));  
      appInfo.Markup = fileNameHintNodes;  
      annotation.Items.Add(appInfo);  
      schema.Items.Insert(0, annotation);  
   }  
```  

## <a name="do-not-modify-adapterenvironmentsettings-during-processing"></a><span data-ttu-id="943df-171">在處理期間，無法修改 AdapterEnvironmentSettings</span><span class="sxs-lookup"><span data-stu-id="943df-171">Do Not Modify AdapterEnvironmentSettings During Processing</span></span>  
 <span data-ttu-id="943df-172">配接器應該只會設定**AdapterEnvironmentSettings**， **ConnectionPoolManager**，**連接集區**，和**CommonCacheSize**配接器初始化期間，不應該嘗試來修改執行中執行個體的值。</span><span class="sxs-lookup"><span data-stu-id="943df-172">The adapter should only set the **AdapterEnvironmentSettings**, **ConnectionPoolManager**, **ConnectionPool**, and **CommonCacheSize** during adapter initialization and should not attempt to modify the values for a running instance.</span></span>  

 <span data-ttu-id="943df-173">如果目前正在執行的配接器執行個體上修改這些設定，這可能會導致新的連線，並覆寫 針對目前正在執行連線的 組態設定。</span><span class="sxs-lookup"><span data-stu-id="943df-173">If these settings are modified on a currently running adapter instance, this may result in new connections overwriting configuration settings for currently executing connections.</span></span>  

## <a name="see-also"></a><span data-ttu-id="943df-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="943df-174">See Also</span></span>  
 [<span data-ttu-id="943df-175">使用 WCF LOB 配接器 SDK 開發最佳做法</span><span class="sxs-lookup"><span data-stu-id="943df-175">Development best practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)