---
title: 建立自訂解析程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2775460-8e04-40be-9557-8278336b031c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3752348a5cc9273ad203b78b77b58bde33bd141
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981711"
---
# <a name="creating-a-custom-resolver"></a>建立自訂解析程式
中的解析程式和配接器提供者架構實作[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會使用名為發送器的管線元件和名為 ItineraryReceive 和 ItinerarySend 的管線。  
  
 「 發送器 」 管線元件有四個屬性：**驗證、 已啟用、 端點**並**MapName**。 **端點**屬性可包含解析程式的連接字串值，如下所示，其中**UDDI:\\ \\** 表示解析型別，若要使用 （根moniker)。  
  
```  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=OrderPurchaseToOrderPost;serviceProvider=Microsoft.Practices.ESB  
```  
  
 包含其他支援的 moniker **XPATH:\\\\靜態：\\\\，** 並**BRE:\\\\**。 每個 moniker 型別會使用特定類別可實作**IResolveProvider**介面。 您可以建立自己自訂的解析程式，其他的 moniker 類型，並用於登錄動態解析系統。  
  
 Moniker 等於解析程式的連接字串。 個別的結構描述定義的參數和其根 moniker。 解析程式會在解析程式的連接字串，驗證，並使用結果，查詢並填入**字典**物件，可用於路由、 轉換、 路線的選取項目或其他用途的特定程式服務。  
  
## <a name="resolver-configuration"></a>解析程式組態  
 您必須註冊所有的解析程式 Esb.config 組態檔中。 下列 XML 顯示組態檔內容的範例。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
     <configSections>  
          <section name="esb" type="Microsoft.Practices.ESB.Configuration.ESBConfigurationSection, Microsoft.Practices.ESB.Configuration, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
          <!-- Other Section Definitions Here -->  
     </configSections>  
  
     <esb>  
          <resolvers cacheManager= "Resolver Providers Cache Manager"  absoluteExpiration="3600">  
               <resolver name="UDDI" type="Microsoft.Practices.ESB.Resolver.UDDI.ResolveProvider, Microsoft.Practices.ESB.Resolver.UDDI, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22">  
                    <resolverConfig>  
                         <add name="cacheTimeoutValue" value="120" />  
                         <add name="cacheName" value="UDDI Cache Manager" />  
                    </resolverConfig>  
               </resolver>  
               <resolver name="XPATH" type="Microsoft.Practices.ESB.Resolver.XPATH.ResolveProvider, Microsoft.Practices.ESB.Resolver.XPATH, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
               <!-- Other Resolver Definitions Here -->  
          </resolvers>  
          <!-- Other ESB Configuration Settings Here -->  
     </esb>  
     <!-- Other Configuration Sections Here -->  
</configuration>  
```  
  
 **ResolverConfig** ] 區段的 [解析程式的每個節點可讓您設定您的解析程式可能需要在特定環境中運作的其他屬性。 若要存取設定，請將解決器必須公開 （expose) 中的型別參數的建構函式**Microsoft.Practices.ESB.Configuration.Resolver**。 在解析程式實作中，組態屬性可以接著使用來存取**ReadResolverConfigByKey**方法**ResolverConfigHelper**類別; 若要這樣做，傳遞參數原本傳遞至建構函式，並接著傳入值有問題。 如果沒有名稱 / 值組中指定**resolverConfig**節點中，預設的無參數建構函式會用來具現化您的解析程式。  
  
 兩個通用描述、 探索與整合 (UDDI) 3 組態中已定義的解析程式： UDDI 3 和 UDDI 3 SOASOFTWARE。 這兩個這些解析程式使用相同的基礎組件，但可提供不同的組態，以支援不同的 UDDI 3.0 相容登錄與不同的統一資源識別元 (URI) 格式和安全性需求。 如果您需要設定 UDDI 3.0 相容的登錄，除了已經支援其他的 moniker，就可以使用下列的組態屬性：  
  
- **cacheTimeoutValue**  
  
- **cacheName**  
  
- **publisherKey**  
  
- **useUddiAuth**  
  
- **baseUri**  
  
- **inquireUriSuffix**  
  
- **securityUriSuffix**  
  
- **securityMode**。 如需有效的值，請參閱列舉[System.ServiceModel.BasicHttpSecurityMode](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409) ([http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409))。 預設值是**TransportCredentialOnly**。  
  
- **credentialType**。 如需有效的值，請參閱列舉[System.ServiceModel.HttpClientCredentialType](http://go.microsoft.com/fwlink/?LinkId=188285) ([http://go.microsoft.com/fwlink/?LinkId=188285](http://go.microsoft.com/fwlink/?LinkId=188285))。 預設值是**Windows**。  
  
- **username**  
  
- **password**  
  
  如果您想要建立的解析程式依賴的 Unity Application Block 的相依性插入功能，則需要其他組態。 如需詳細資訊，請參閱 <<c0> [ 使用 Unity 容器建立自訂解析程式](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md)。  
  
## <a name="the-iresolveprovider-interface"></a>IResolveProvider 介面  
 所有的解析程式必須實作**IResolveProvider**介面。 **IResolveProvider**介面，在 Microsoft.Practices.ESB.Resolver 專案中，位於所組成的三個多載**解決**傳回的執行個體的方法**字典**類別，其中包含實體的解析程式類別的執行個體所提供的解析事實。 下列程式碼範例會示範這些方法多載的簽章。  
  
```csharp  
// <summary>  
// This is the main interface that is called from the   
// ResolverMgr class.  
// This interface supports being called from a Microsoft BizTalk   
// Server pipeline component.  
// </summary>  
// <param name="config">Configuration string entered into   
// pipeline component as argument</param>  
// <param name="resolver">Moniker representing the resolver   
// to load</param>.  
// <param name="message">IBaseMessage passed from pipeline</param>.  
// <param name="pipelineContext">IPipelineContext passed from   
// pipeline</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string, string> Resolve(string config, string resolver,  
              IBaseMessage message, IPipelineContext pipelineContext);  
  
// <summary>  
// This is the main interface that is called from the ResolverMgr   
// class.  
// This interface supports being called from a Web service interface.  
// </summary>  
// <param name="config">Configuration string entered into Web   
// service as argument</param>.  
// <param name="resolver">Moniker representing the resolver   
// to load</param>.  
// <param name="message">XML document passed from Web   
// service</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string,string> Resolve(string config, string resolver, System.Xml.XmlDocument message);  
  
// <summary>  
// This is the main interface that is called from the   
// ResolverMgr class.  
// This interface supports being called from an orchestration.  
// </summary>  
// <param name="resolverInfo">Configuration string containing   
// configuration and resolver</param>.  
// <param name="message">XLANGMessage passed from   
// orchestration</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string, string> Resolve(ResolverInfo resolverInfo, XLANGs.BaseTypes.XLANGMessage message);  
```  
  
 **解析度**結構，位在 Microsoft.Practices.ESB.Resolver 專案中，也會定義儲存在名稱/值組**字典**執行個體。 **解析度**結構會公開一些屬性下, 表列出其中最相關。 **CreateResolverDictionary**方法**ResolutionHelper**類別可以用來產生包含最常使用的索引鍵，以空字串值的解析程式字典。 **字典**執行個體支援的自訂解決器名稱/值組，透過的具體實作加法**解析程式**類別。  
  
|屬性|資料類型|資料類型|資料類型|  
|--------------|---------------|---------------|---------------|  
|**TransformType**|String|**ActionField**|String|  
|**成功**|布林|**EpmRRCorrelationTokenField**|String|  
|**TransportNamespace**|String|**InboundTransportLocationField**|String|  
|**TransportType**|String|**InterchangeIDField**|String|  
|**TransportLocation**|String|**ReceiveLocationNameField**|String|  
|**動作**|String|**ReceivePortNameField**|String|  
|**MessageExchangePattern**|String|**InboundTransportTypeField**|String|  
|**EndpointConfig**|String|**IsRequestResponseField**|String|  
|**目標命名空間**|String|**DocumentSpecStrongNameField**|String|  
|**FixJaxRPC**|布林|**DocumentSpecNameField**|String|  
|**WindowUserField**|String|**MessageType**|String|  
|**CacheTimeout**|String|**OutboundTransportCLSID**|String|  
|**MethodNameField**|String|||  
  
## <a name="creating-a-custom-resolver"></a>建立自訂解析程式  
 在執行階段，管線擷取的解析程式的連接字串，並呼叫解析程式管理員 (執行個體**ResolverMgr**類別)。 解析程式管理員會剖析、 填入，並驗證的解析程式的連接字串。 它會執行下列動作：  
  
- 它會剖析連接字串，以判斷哪些**解析程式**来載入型別。  
  
- 它符合此類型定義 （索引鍵是根 moniker，例如 UDDI） 的組態檔中的 moniker。  
  
- 它會讀取這個 moniker 解析程式的組件名稱。  
  
- 它會載入指定的組件。  
  
  動態解析機制會快取載入的所有實作**IResolveProvider**介面，以避免重複的讀取組態資訊和數個內送訊息使用的相同時載入的組件解析程式。  
  
  最後，解析程式管理員會執行**解決**方法的具體**IResolveProvider**實作，並傳回已填入**字典**執行個體。  
  
  **若要建立自訂解析程式**  
  
1.  建立可實作類別的組件**IResolveProvider**介面，並包含**解決**方法會傳回執行個體的解析程式事實**字典**類別。  
  
2.  註冊解析程式新增至 Esb.config 組態檔中使用**\<解析程式\>** 元素，其中包含做為根 moniker**名稱**屬性和完整限定的組件名稱為**型別**屬性。  
  
3.  （選擇性）建立結構描述中定義的根 moniker 和查詢參數，並再將它儲存在 ESB。Schemas.Resolvers 資料夾中。 名稱應該遵循現有的 ESB 命名慣例;這表示它應該使用的名稱加上"_Resolution.xsd"的根 moniker。  
  
4.  （選擇性）從新的結構描述產生類別，並將它儲存在自訂解析程式的組件。 這會公開自訂解析程式中的型別的參數。  
  
5.  在全域組件快取中註冊新的組件。