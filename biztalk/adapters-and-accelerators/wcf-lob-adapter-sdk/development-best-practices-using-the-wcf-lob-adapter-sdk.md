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
# <a name="development-best-practices-using-the-wcf-lob-adapter-sdk"></a>使用 WCF LOB 配接器 SDK 開發最佳做法
您可以使用本主題中的最佳作法，以改善您的應用程式和配接器。  

## <a name="call-abort-before-close-on-channel-exception"></a>呼叫中止前關閉通道例外狀況  
 當您撰寫的應用程式使用 WCF 通道模型時，您應該呼叫`IRequestChannel.Abort`再呼叫`ChannelFactory.Close`。 如果您未這麼做，`ChannelFactory.Close`擲回例外狀況。  

 在下列範例中，嘗試通道作業在 try/catch 區塊內。 如果發生例外狀況，則會中止通道。  

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

## <a name="implement-both-asynchronous-and-synchronous-handlers"></a>實作非同步和同步處理常式  
 可能的話，請在您的配接器實作非同步和同步處理常式。 如果您的配接器只會實作同步呼叫，您可能會發生封鎖問題時處理的訊息，或配接器用在多執行緒環境中的大型磁碟區。  

## <a name="use-connection-pooling"></a>使用連接共用  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]支援預設的連接共用。 不過，它是由配接器開發人員判斷哪一個連接共用來公開做為繫結屬性的屬性。 可用的連接集區設定中定義`Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`。  

 沒有任何選項內[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]輕鬆公開這些介面卡連接屬性的屬性。 配接器實作中，配接器開發人員必須手動定義的屬性。  

```csharp  
public CustomAdapter(): base()  
{  
   this.Settings.ConnectionPool.EnablePooling = true;  
   this.Settings.ConnectionPool.HandlersShareSameConnection = true;  
   this.Settings.ConnectionPool.MaxConnectionsPerSystem = 50;  
   this.Settings.ConnectionPool.MaxAvailableConnections = 5;  
}  
```  

## <a name="ensure-that-the-adapter-supports-two-way-operations"></a>請確定此配接器支援雙向作業  
 如果您的配接器從 BizTalk Server 呼叫，就必須支援雙向作業，即使傳回的值為 void。 這是因為 BizTalk Server 預期任何傳出的要求，從傳回的回應，而且如果您的配接器只會實作單向作業，會擲回例外狀況。  

 以下是傳回 void 的要求-回應合約的範例。  

```csharp  
[ServiceContract(Namespace=”Http:Microsoft.BizTalk.Samples.WCFAdapterSample”)]  
public interface ICalculator  
{  
   [OperationContract]  
   void Add(double n1, double n2);  
}  
```  

## <a name="implement-tracing"></a>實作追蹤  
 在開發週期中，它也許好像不太重要新增至您的配接器的追蹤，因為您可以逐步執行程式碼和偵錯任何問題。 不過，在生產環境中安裝配接器之後，您可能無法使用執行階段偵錯來隔離問題。 如果您已啟用追蹤，在您的配接器，它可用來找出發生失敗的位置。  

 請參閱[追蹤配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/trace-an-adapter-with-the-wcf-lob-adapter-sdk.md)如需詳細資訊。  

## <a name="use-uri-properties-for-frequently-changed-settings"></a>URI 屬性用於經常變更的設定  
 在決定是否要將自訂屬性公開為繫結或 URI 屬性，建議使用 URI 屬性，如果值經常變更。 繫結屬性應保留給極少變更的值。  

 繫結屬性範例會使用所有連接的資料庫伺服器名稱。 特定資料表或預存程序，以供該特定連線，就會是範例 URI 屬性。  

## <a name="do-not-pass-user-name-or-password-values-in-the-uri"></a>不要在 URI 中傳遞使用者名稱或密碼值  
 如果您的配接器需要呼叫端的認證，則建議使用**ClientCredentials**類別來擷取認證值，而不是傳遞做為 URI 的一部分的用戶端認證。 **ClientCredentials**類別是標準的功能的 WCF，以供將認證資訊從用戶端傳遞至服務，以更安全的方式。 URI 字串的一部分傳遞的使用者資訊可能會公開在傳輸過程中的使用者資訊。  

 下表顯示傳遞認證的建議的方法。  


|      方法       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    設計階段    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                當使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您可以指定配接器支援的用戶端認證類型。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|     執行階段      | 使用時產生的.NET CLR proxy，您可以透過程式設計方式設定用戶端認證。<br /><br /> `static void Main(string[] args) {    EchoServiceClient client = new EchoServiceClient();    client.ClientCredentials.UserName.UserName = "TestUser";    client.ClientCredentials.UserName.Password = "TestPassword";    string response=client.EchoString("Test String"); }`<br /><br /> 或者，如果您需要直接互動的通道，您可以使用 WCF 通道模型來建立通道處理站時，指定用戶端認證。<br /><br /> `EchoAdapterBinding binding = new EchoAdapterBinding(); binding.Count = 3; ClientCredentials clientCredentials = new ClientCredentials(); clientCredentials.UserName.UserName = "TestUser"; clientCredentials.UserName.Password = "TestPassword"; BindingParameterCollection bindingParms = new BindingParameterCollection(); bindingParms.Add(clientCredentials); EndpointAddress address = new EndpointAddress("echo://"); IChannelFactory<IRequestChannel> requestChannelFactory = binding.BuildChannelFactory<IRequestChannel>(bindingParms); requestChannelFactory.Open();` |
| WCF 組態 |                                                                                                                                                                                                                                               在 用戶端組態檔中，新增\<endpointBehaviors\>項目，包括\<clientCredentials\>。<br /><br /> `<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">       <system.serviceModel>           . . . . .           <behaviors>             <endpointBehaviors>               <behavior name="clientEndpointCredential">                 <clientCredentials>                   <windows allowNtlm="false" allowedImpersonationLevel="Delegation" />                    </clientCredentials>               </behavior>             </endpointBehaviors>           </behaviors>       </system.serviceModel>   </configuration>`                                                                                                                                                                                                                                               |
|   使用 BizTalk   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                 當取用您的配接器使用 WCF 配接器，您可以加入**clientCredentials**上的行為延伸模組**行為** 索引標籤。這已新增之後，您可以設定所需的用戶端認證的端點行為。                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

## <a name="do-not-return-both-strongdatasettype-and-weakdatasettype"></a>不會傳回同時 StrongDataSetType 和 WeakDataSetType  
 如果您的配接器傳回`DataSet`，使用任何一種`Microsoft.ServiceModel.Channels.Common.QualifiedType.StrongDataSetType%2A`或`Microsoft.ServiceModel.Channels.Common.QualifiedType.WeakDataSetType%2A`，但不要兩者同時使用。 所產生的這兩種類型的命名空間與根節點名稱都相同，而且不能同時存在於 WSDL。  

 雖然`WeakDataSetType`並`StrongDataSetType`都代表`System.Data.DataSet`，`StrongDataSetType`可以更輕鬆地使用.NET 應用程式中，因為產生的 proxy 會顯示為`System.Data.Dataset`。 所產生的 proxy`WeakDataSetType`是`XmlElement[]`，這是較難在.NET 應用程式中使用。  BizTalk Server 無法使用從傳回的結構描述`StrongDataSet`，但能夠取用`WeakDataSetType`。  

> [!NOTE]
>  `StrongDataSetType` 和`WeakDataSetType`只能控制用戶端應用程式如何解譯配接器所傳遞的 XML 訊息。 XML 訊息會是相同不論所指定型別。  

> [!NOTE]
>  傳回時`StrongDataSetType`，您必須設定`Microsoft.ServiceModel.Channels.Common.MetadataSettings.CompileWsdl%2A`至`false`。 當設定為`true`，預設值，`XmlSchemaSet::Compile`呼叫中以確保沒有任何錯誤，在 WSDL 中配接器，但是結構描述所產生`StrongDataSetType`會產生例外狀況中的`XmlSchemaSet`。  
>   
>  設定`CompileWsdl`至`false`WSDL 內的配接器和驗證的結構描述驗證 proxy 產生期間所發生的許可。  Svcutil.exe 之類的公用程式可產生兩個 proxy`StrongDataSetType`和`WeakDataSetType`。  

 若要使用 BizTalk 和.NET 環境，請考慮實作允許切換兩個傳回的型別，如取決於環境的繫結屬性。  

```csharp  
internal static QualifiedType GetDataSetQualifiedType(MyAdapterBindingProperties bindingProperties)  
{  
   if (bindingProperties.EnableBizTalkCompatibility)  
      return QualifiedType.WeakDataSetType;  
   else  
      return QualifiedType.StrongDataSetType;  
}  
```  

## <a name="create-meaningful-xsd-schema-names-in-biztalk-server"></a>BizTalk Server 中建立有意義的 XSD 結構描述名稱  
 使用時[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]設計階段工具，建立 BizTalk 專案中產生的 XSD 結構描述的名稱使用`DefaultXsdFileNamePrefix`屬性， `fileNameHint` WSDL 中的註解，並在必要時，唯一的整數值。  

 例如，如果`DefaultXsdFileNamePrefix`設定為"MyAdapter 」 和`fileNameHint`註解設為"Stream"、 XSD 結構描述，建立名為 MyAdapterStream.xsd。  

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
>  預設值`DefaultXsdFileNamePrefix`是您的繫結的名稱。 若要指定不同的值，覆寫`DefaultXsdFileNamePrefix`在您的配接器類別衍生自`Microsoft.ServiceModel.Channels.Common.AdapterBinding`。  

 有兩種可能的方法，以新增`fileNameHint`結構描述的註釋： 覆寫 匯出...結構描述 OperationMetadata\TypeMetadata 或覆寫 IWsdlRetrieval 實作的介面卡上的方法。 何種方法，您可以呼叫基底實作，並再將註解新增至結構描述集合中的結構描述。  

> [!NOTE]
>  當覆寫 匯出...結構描述的方法，可能會有相同的結構描述; 的多個作業/型別定義配接器應該要確定多次`fileNameHints`相同的結構描述的註解不會衝突。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會使用第一個出現`fileNameHint`如果結構描述中發生多次。  

 在下列範例中，IWsdlRetrieval 用來新增`fileNameHint`至 WSDL 附註。  

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

## <a name="do-not-modify-adapterenvironmentsettings-during-processing"></a>在處理期間，無法修改 AdapterEnvironmentSettings  
 配接器應該只會設定**AdapterEnvironmentSettings**， **ConnectionPoolManager**，**連接集區**，和**CommonCacheSize**配接器初始化期間，不應該嘗試來修改執行中執行個體的值。  

 如果目前正在執行的配接器執行個體上修改這些設定，這可能會導致新的連線，並覆寫 針對目前正在執行連線的 組態設定。  

## <a name="see-also"></a>另請參閱  
 [使用 WCF LOB 配接器 SDK 開發最佳做法](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)