---
title: 建立自訂解決器 |Microsoft 文件
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
ms.openlocfilehash: 57fb0073437c32c8a8f064a4c77f267ee6806858
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975900"
---
# <a name="creating-a-custom-resolver"></a>建立自訂的解析程式
中的解析器和配接器提供者架構實作[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會使用名為發送器管線元件和名為 ItineraryReceive 和 ItinerarySend 的管線。  
  
 發送器管線元件會有四個屬性：**驗證、 啟用、 端點、** 和**MapName**。 **端點**屬性可以包含解析程式的連接字串值，如下所示，其中**UDDI:\\ \\** 表示要使用 （根的解析度類型moniker)。  
  
```  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=OrderPurchaseToOrderPost;serviceProvider=Microsoft.Practices.ESB  
```  
  
 其他支援的 moniker 包含**XPATH:\\\\、 靜態：\\\\，** 和**BRE:\\\\**。 每個的 moniker 型別會使用特定類別可實作**IResolveProvider**介面。 您可以建立您自己的自訂解析程式適用於其他 moniker 類型，並用於動態解析系統註冊它們。  
  
 Moniker 等同的解析程式的連接字串。 個別的結構描述定義的參數和其根 moniker。 解析程式會在解析程式的連接字串，驗證，並使用結果查詢，並填入**字典**物件，可用於路由、 轉換、 路線的選取項目或其他用途的特定程式服務。  
  
## <a name="resolver-configuration"></a>解析程式組態  
 您必須登錄所有的解析程式 Esb.config 組態檔中。 下列 XML 顯示組態檔案內容的範例。  
  
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
  
 **ResolverConfig**解析程式的每個節點之下 區段可讓您設定您解決器可能需要在特定的環境中運作的其他屬性。 若要存取設定，請您解決器必須公開接受型別參數的建構函式**Microsoft.Practices.ESB.Configuration.Resolver**。 在解析程式實作中，組態屬性可以接著使用存取**ReadResolverConfigByKey**方法**ResolverConfigHelper**類別; 若要這樣做，傳遞參數原先傳遞至建構函式，並將傳遞值的名稱有問題。 如果沒有名稱 / 值組中指定則**resolverConfig**節點中，預設的無參數建構函式會用來具現化您的解析程式。  
  
 兩個通用描述、 探索與整合 (UDDI) 3 組態中已定義的解析程式： UDDI 3 和 UDDI 3 SOASOFTWARE。 這兩個這些解析程式使用相同的基礎組件，但它們會提供不同的組態支援不同的 UDDI 3.0 相容登錄與不同的統一資源識別元 (URI) 格式和安全性需求。 如果您需要設定 UDDI 3.0 相容的登錄，除了那些已經支援其他 moniker，可以使用下列組態屬性：  
  
-   **cacheTimeoutValue**  
  
-   **cacheName**  
  
-   **publisherKey**  
  
-   **useUddiAuth**  
  
-   **baseUri**  
  
-   **inquireUriSuffix**  
  
-   **securityUriSuffix**  
  
-   **securityMode**。 有效的值，請參閱列舉[System.ServiceModel.BasicHttpSecurityMode](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409) ([http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409))。 預設值是**TransportCredentialOnly**。  
  
-   **credentialType**。 有效的值，請參閱列舉[System.ServiceModel.HttpClientCredentialType](http://go.microsoft.com/fwlink/?LinkId=188285) ([http://go.microsoft.com/fwlink/?LinkId=188285](http://go.microsoft.com/fwlink/?LinkId=188285))。 預設值是**Windows**。  
  
-   **使用者名稱**  
  
-   **密碼**  
  
 如果您想要建立的解析程式所使用的 Unity 應用程式區塊的相依性插入功能，則需要其他組態。 如需詳細資訊，請參閱[與 Unity 容器中建立自訂解析程式](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md)。  
  
## <a name="the-iresolveprovider-interface"></a>IResolveProvider 介面  
 所有的解析程式必須實作**IResolveProvider**介面。 **IResolveProvider**介面，在 Microsoft.Practices.ESB.Resolver 專案中，位於所組成的三個多載**解決**這個方法傳回的執行個體**字典**類別，其中包含解析事實提供具體的解析程式類別的執行個體。 下列程式碼範例示範這些方法多載的簽章。  
  
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
  
 **解析**結構，位於 Microsoft.Practices.ESB.Resolver 專案，也會定義儲存在名稱/值組**字典**執行個體。 **解析**結構會公開一些屬性下, 表列出其中最相關。 **CreateResolverDictionary**方法**ResolutionHelper**類別可以用來產生解析程式字典，其中包含最常使用的索引鍵，以空字串值。 **字典**執行個體支援的自訂解決器名稱/值組的具體實作透過加入**解析程式**類別。  
  
|屬性|資料類型|資料類型|資料類型|  
|--------------|---------------|---------------|---------------|  
|**TransformType**|字串|**ActionField**|字串|  
|**成功**|布林|**EpmRRCorrelationTokenField**|字串|  
|**TransportNamespace**|字串|**InboundTransportLocationField**|字串|  
|**TransportType**|字串|**InterchangeIDField**|字串|  
|**TransportLocation**|字串|**ReceiveLocationNameField**|字串|  
|**動作**|字串|**ReceivePortNameField**|字串|  
|**MessageExchangePattern**|字串|**InboundTransportTypeField**|字串|  
|**EndpointConfig**|字串|**IsRequestResponseField**|字串|  
|**目標命名空間**|字串|**DocumentSpecStrongNameField**|字串|  
|**FixJaxRPC**|布林|**DocumentSpecNameField**|字串|  
|**WindowUserField**|字串|**MessageType**|字串|  
|**CacheTimeout**|字串|**OutboundTransportCLSID**|字串|  
|**MethodNameField**|字串|||  
  
## <a name="creating-a-custom-resolver"></a>建立自訂的解析程式  
 在執行階段，管線擷取解析程式的連接字串，並呼叫解析程式管理員 (執行個體**ResolverMgr**類別)。 解析程式管理員會剖析、 填入，並驗證的解析程式的連接字串。 它會執行下列動作：  
  
-   它會剖析連接字串，來判斷哪一個**解析程式**載入的型別。  
  
-   它符合 moniker （索引鍵是根 moniker，例如 UDDI） 的組態檔中定義此型別。  
  
-   它會讀取這個 moniker 解析程式的組件名稱。  
  
-   它會載入指定的組件。  
  
 動態解析機制會快取載入的所有實作**IResolveProvider**介面，以避免重複的讀取組態資訊和數個內送訊息使用的相同時載入的組件解析程式。  
  
 最後，解析程式管理員執行**解決**方法的具體**IResolveProvider**實作，並傳回已填入**字典**執行個體。  
  
 **若要建立自訂的解析程式**  
  
1.  建立組件實作的類別與**IResolveProvider**介面，並包含**解決**方法會傳回解析程式事實的執行個體形式**字典**類別。  
  
2.  註冊解決器將它加入 Esb.config 組態檔使用**\<解析程式\>** 元素包含做為根 moniker**名稱**屬性和完整限定組件名稱為**類型**屬性。  
  
3.  （選擇性）建立結構描述定義的根 moniker 和查詢參數，並再將它儲存在 ESB。Schemas.Resolvers 資料夾。 名稱應該遵循現有的 ESB 命名慣例。這表示它應使用的名稱加上"_Resolution.xsd"的根 moniker。  
  
4.  （選擇性）從新的結構描述產生類別，並將它儲存在自訂解決器組件中。 這樣會公開自訂解析程式中的型別的參數。  
  
5.  在全域組件快取中註冊新的組件。