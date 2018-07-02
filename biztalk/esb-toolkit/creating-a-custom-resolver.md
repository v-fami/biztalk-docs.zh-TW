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
# <a name="creating-a-custom-resolver"></a><span data-ttu-id="0e90c-102">建立自訂解析程式</span><span class="sxs-lookup"><span data-stu-id="0e90c-102">Creating a Custom Resolver</span></span>
<span data-ttu-id="0e90c-103">中的解析程式和配接器提供者架構實作[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會使用名為發送器的管線元件和名為 ItineraryReceive 和 ItinerarySend 的管線。</span><span class="sxs-lookup"><span data-stu-id="0e90c-103">The Resolver and Adapter Provider Framework implementation in [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses a pipeline component named Dispatcher and pipelines named ItineraryReceive and ItinerarySend.</span></span>  
  
 <span data-ttu-id="0e90c-104">「 發送器 」 管線元件有四個屬性：**驗證、 已啟用、 端點**並**MapName**。</span><span class="sxs-lookup"><span data-stu-id="0e90c-104">The Dispatcher pipeline component has four properties: **Validate, Enabled, EndPoint,** and **MapName**.</span></span> <span data-ttu-id="0e90c-105">**端點**屬性可包含解析程式的連接字串值，如下所示，其中**UDDI:\\ \\** 表示解析型別，若要使用 （根moniker)。</span><span class="sxs-lookup"><span data-stu-id="0e90c-105">The **EndPoint** property can contain resolver connection strings with values such as the following, where **UDDI:\\\\** represents the resolution type to use (the root moniker).</span></span>  
  
```  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=OrderPurchaseToOrderPost;serviceProvider=Microsoft.Practices.ESB  
```  
  
 <span data-ttu-id="0e90c-106">包含其他支援的 moniker **XPATH:\\\\靜態：\\\\，** 並**BRE:\\\\**。</span><span class="sxs-lookup"><span data-stu-id="0e90c-106">Other supported monikers include **XPATH:\\\\, STATIC:\\\\,** and **BRE:\\\\**.</span></span> <span data-ttu-id="0e90c-107">每個 moniker 型別會使用特定類別可實作**IResolveProvider**介面。</span><span class="sxs-lookup"><span data-stu-id="0e90c-107">Each moniker type uses a specific class that implements the **IResolveProvider** interface.</span></span> <span data-ttu-id="0e90c-108">您可以建立自己自訂的解析程式，其他的 moniker 類型，並用於登錄動態解析系統。</span><span class="sxs-lookup"><span data-stu-id="0e90c-108">You can create your own custom resolvers for other moniker types and register them for use by the dynamic resolution system.</span></span>  
  
 <span data-ttu-id="0e90c-109">Moniker 等於解析程式的連接字串。</span><span class="sxs-lookup"><span data-stu-id="0e90c-109">The moniker equates to a resolver connection string.</span></span> <span data-ttu-id="0e90c-110">個別的結構描述定義的參數和其根 moniker。</span><span class="sxs-lookup"><span data-stu-id="0e90c-110">Individual schemas define the parameters and their root moniker.</span></span> <span data-ttu-id="0e90c-111">解析程式會在解析程式的連接字串，驗證，並使用結果，查詢並填入**字典**物件，可用於路由、 轉換、 路線的選取項目或其他用途的特定程式服務。</span><span class="sxs-lookup"><span data-stu-id="0e90c-111">A resolver takes the resolver connection string, validates it, and uses the result to query and populate a **Dictionary** object that can be used for routing, transformation, itinerary selection, or some other purpose specific to your service.</span></span>  
  
## <a name="resolver-configuration"></a><span data-ttu-id="0e90c-112">解析程式組態</span><span class="sxs-lookup"><span data-stu-id="0e90c-112">Resolver Configuration</span></span>  
 <span data-ttu-id="0e90c-113">您必須註冊所有的解析程式 Esb.config 組態檔中。</span><span class="sxs-lookup"><span data-stu-id="0e90c-113">You must register all resolvers in the Esb.config configuration file.</span></span> <span data-ttu-id="0e90c-114">下列 XML 顯示組態檔內容的範例。</span><span class="sxs-lookup"><span data-stu-id="0e90c-114">The following XML shows an example of the configuration file content.</span></span>  
  
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
  
 <span data-ttu-id="0e90c-115">**ResolverConfig** ] 區段的 [解析程式的每個節點可讓您設定您的解析程式可能需要在特定環境中運作的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="0e90c-115">The **resolverConfig** section under each resolver node allows you to configure additional properties that your resolver may require to operate in a specific environment.</span></span> <span data-ttu-id="0e90c-116">若要存取設定，請將解決器必須公開 （expose) 中的型別參數的建構函式**Microsoft.Practices.ESB.Configuration.Resolver**。</span><span class="sxs-lookup"><span data-stu-id="0e90c-116">To have access to the configuration, your resolver must expose a constructor that takes in a parameter of type **Microsoft.Practices.ESB.Configuration.Resolver**.</span></span> <span data-ttu-id="0e90c-117">在解析程式實作中，組態屬性可以接著使用來存取**ReadResolverConfigByKey**方法**ResolverConfigHelper**類別; 若要這樣做，傳遞參數原本傳遞至建構函式，並接著傳入值有問題。</span><span class="sxs-lookup"><span data-stu-id="0e90c-117">In your resolver implementation, configuration properties can then be accessed using the **ReadResolverConfigByKey** method of the **ResolverConfigHelper** class; to do this, pass in the parameter originally passed to the constructor, and then pass in the name of the value in question.</span></span> <span data-ttu-id="0e90c-118">如果沒有名稱 / 值組中指定**resolverConfig**節點中，預設的無參數建構函式會用來具現化您的解析程式。</span><span class="sxs-lookup"><span data-stu-id="0e90c-118">If no name-value pairs are specified in the **resolverConfig** node, the default parameterless constructor will be used to instantiate your resolver.</span></span>  
  
 <span data-ttu-id="0e90c-119">兩個通用描述、 探索與整合 (UDDI) 3 組態中已定義的解析程式： UDDI 3 和 UDDI 3 SOASOFTWARE。</span><span class="sxs-lookup"><span data-stu-id="0e90c-119">Two Universal Description, Discovery, and Integration (UDDI) 3 resolvers have been defined in the configuration: UDDI 3 and UDDI 3-SOASOFTWARE.</span></span> <span data-ttu-id="0e90c-120">這兩個這些解析程式使用相同的基礎組件，但可提供不同的組態，以支援不同的 UDDI 3.0 相容登錄與不同的統一資源識別元 (URI) 格式和安全性需求。</span><span class="sxs-lookup"><span data-stu-id="0e90c-120">Both of these resolvers use the same underlying assembly, but they provide different configurations for supporting different UDDI 3.0–compliant registries with different Uniform Resource Identifier (URI) formats and security requirements.</span></span> <span data-ttu-id="0e90c-121">如果您需要設定 UDDI 3.0 相容的登錄，除了已經支援其他的 moniker，就可以使用下列的組態屬性：</span><span class="sxs-lookup"><span data-stu-id="0e90c-121">If you need to configure an additional moniker for a UDDI 3.0–compliant registry besides those already supported, the following configuration properties can be used:</span></span>  
  
- <span data-ttu-id="0e90c-122">**cacheTimeoutValue**</span><span class="sxs-lookup"><span data-stu-id="0e90c-122">**cacheTimeoutValue**</span></span>  
  
- <span data-ttu-id="0e90c-123">**cacheName**</span><span class="sxs-lookup"><span data-stu-id="0e90c-123">**cacheName**</span></span>  
  
- <span data-ttu-id="0e90c-124">**publisherKey**</span><span class="sxs-lookup"><span data-stu-id="0e90c-124">**publisherKey**</span></span>  
  
- <span data-ttu-id="0e90c-125">**useUddiAuth**</span><span class="sxs-lookup"><span data-stu-id="0e90c-125">**useUddiAuth**</span></span>  
  
- <span data-ttu-id="0e90c-126">**baseUri**</span><span class="sxs-lookup"><span data-stu-id="0e90c-126">**baseUri**</span></span>  
  
- <span data-ttu-id="0e90c-127">**inquireUriSuffix**</span><span class="sxs-lookup"><span data-stu-id="0e90c-127">**inquireUriSuffix**</span></span>  
  
- <span data-ttu-id="0e90c-128">**securityUriSuffix**</span><span class="sxs-lookup"><span data-stu-id="0e90c-128">**securityUriSuffix**</span></span>  
  
- <span data-ttu-id="0e90c-129">**securityMode**。</span><span class="sxs-lookup"><span data-stu-id="0e90c-129">**securityMode**.</span></span> <span data-ttu-id="0e90c-130">如需有效的值，請參閱列舉[System.ServiceModel.BasicHttpSecurityMode](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409) ([http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409))。</span><span class="sxs-lookup"><span data-stu-id="0e90c-130">For valid values, see the enumeration [System.ServiceModel.BasicHttpSecurityMode](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409) ([http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409)).</span></span> <span data-ttu-id="0e90c-131">預設值是**TransportCredentialOnly**。</span><span class="sxs-lookup"><span data-stu-id="0e90c-131">The default value is **TransportCredentialOnly**.</span></span>  
  
- <span data-ttu-id="0e90c-132">**credentialType**。</span><span class="sxs-lookup"><span data-stu-id="0e90c-132">**credentialType**.</span></span> <span data-ttu-id="0e90c-133">如需有效的值，請參閱列舉[System.ServiceModel.HttpClientCredentialType](http://go.microsoft.com/fwlink/?LinkId=188285) ([http://go.microsoft.com/fwlink/?LinkId=188285](http://go.microsoft.com/fwlink/?LinkId=188285))。</span><span class="sxs-lookup"><span data-stu-id="0e90c-133">For valid values, see the enumeration [System.ServiceModel.HttpClientCredentialType](http://go.microsoft.com/fwlink/?LinkId=188285) ([http://go.microsoft.com/fwlink/?LinkId=188285](http://go.microsoft.com/fwlink/?LinkId=188285)).</span></span> <span data-ttu-id="0e90c-134">預設值是**Windows**。</span><span class="sxs-lookup"><span data-stu-id="0e90c-134">The default value is **Windows**.</span></span>  
  
- <span data-ttu-id="0e90c-135">**username**</span><span class="sxs-lookup"><span data-stu-id="0e90c-135">**username**</span></span>  
  
- <span data-ttu-id="0e90c-136">**password**</span><span class="sxs-lookup"><span data-stu-id="0e90c-136">**password**</span></span>  
  
  <span data-ttu-id="0e90c-137">如果您想要建立的解析程式依賴的 Unity Application Block 的相依性插入功能，則需要其他組態。</span><span class="sxs-lookup"><span data-stu-id="0e90c-137">If you want to create a resolver that relies on the dependency injection capabilities of the Unity Application Block, additional configuration is required.</span></span> <span data-ttu-id="0e90c-138">如需詳細資訊，請參閱 <<c0> [ 使用 Unity 容器建立自訂解析程式](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md)。</span><span class="sxs-lookup"><span data-stu-id="0e90c-138">For more information, see [Creating a Custom Resolver with a Unity Container](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md).</span></span>  
  
## <a name="the-iresolveprovider-interface"></a><span data-ttu-id="0e90c-139">IResolveProvider 介面</span><span class="sxs-lookup"><span data-stu-id="0e90c-139">The IResolveProvider Interface</span></span>  
 <span data-ttu-id="0e90c-140">所有的解析程式必須實作**IResolveProvider**介面。</span><span class="sxs-lookup"><span data-stu-id="0e90c-140">All resolvers must implement the **IResolveProvider** interface.</span></span> <span data-ttu-id="0e90c-141">**IResolveProvider**介面，在 Microsoft.Practices.ESB.Resolver 專案中，位於所組成的三個多載**解決**傳回的執行個體的方法**字典**類別，其中包含實體的解析程式類別的執行個體所提供的解析事實。</span><span class="sxs-lookup"><span data-stu-id="0e90c-141">The **IResolveProvider** interface, located in the Microsoft.Practices.ESB.Resolver project, consists of three overloads of the **Resolve** method that return an instance of the **Dictionary** class, which contains resolution facts provided by the instance of concrete resolver class.</span></span> <span data-ttu-id="0e90c-142">下列程式碼範例會示範這些方法多載的簽章。</span><span class="sxs-lookup"><span data-stu-id="0e90c-142">The following code example shows the signature of these method overloads.</span></span>  
  
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
  
 <span data-ttu-id="0e90c-143">**解析度**結構，位在 Microsoft.Practices.ESB.Resolver 專案中，也會定義儲存在名稱/值組**字典**執行個體。</span><span class="sxs-lookup"><span data-stu-id="0e90c-143">The **Resolution** structure, located in Microsoft.Practices.ESB.Resolver project, also defines the name/value pairs stored in the **Dictionary** instance.</span></span> <span data-ttu-id="0e90c-144">**解析度**結構會公開一些屬性下, 表列出其中最相關。</span><span class="sxs-lookup"><span data-stu-id="0e90c-144">The **Resolution** structure exposes several properties; the following table lists the most relevant of these.</span></span> <span data-ttu-id="0e90c-145">**CreateResolverDictionary**方法**ResolutionHelper**類別可以用來產生包含最常使用的索引鍵，以空字串值的解析程式字典。</span><span class="sxs-lookup"><span data-stu-id="0e90c-145">The **CreateResolverDictionary** method of the **ResolutionHelper** class can be used to generate a resolver dictionary that contains the most used keys, with empty string values.</span></span> <span data-ttu-id="0e90c-146">**字典**執行個體支援的自訂解決器名稱/值組，透過的具體實作加法**解析程式**類別。</span><span class="sxs-lookup"><span data-stu-id="0e90c-146">The **Dictionary** instance supports the addition of custom resolver name/value pairs through a concrete implementation of the **Resolver** class.</span></span>  
  
|<span data-ttu-id="0e90c-147">屬性</span><span class="sxs-lookup"><span data-stu-id="0e90c-147">Property</span></span>|<span data-ttu-id="0e90c-148">資料類型</span><span class="sxs-lookup"><span data-stu-id="0e90c-148">Data type</span></span>|<span data-ttu-id="0e90c-149">資料類型</span><span class="sxs-lookup"><span data-stu-id="0e90c-149">Data type</span></span>|<span data-ttu-id="0e90c-150">資料類型</span><span class="sxs-lookup"><span data-stu-id="0e90c-150">Data type</span></span>|  
|--------------|---------------|---------------|---------------|  
|<span data-ttu-id="0e90c-151">**TransformType**</span><span class="sxs-lookup"><span data-stu-id="0e90c-151">**TransformType**</span></span>|<span data-ttu-id="0e90c-152">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-152">String</span></span>|<span data-ttu-id="0e90c-153">**ActionField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-153">**ActionField**</span></span>|<span data-ttu-id="0e90c-154">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-154">String</span></span>|  
|<span data-ttu-id="0e90c-155">**成功**</span><span class="sxs-lookup"><span data-stu-id="0e90c-155">**Success**</span></span>|<span data-ttu-id="0e90c-156">布林</span><span class="sxs-lookup"><span data-stu-id="0e90c-156">Boolean</span></span>|<span data-ttu-id="0e90c-157">**EpmRRCorrelationTokenField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-157">**EpmRRCorrelationTokenField**</span></span>|<span data-ttu-id="0e90c-158">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-158">String</span></span>|  
|<span data-ttu-id="0e90c-159">**TransportNamespace**</span><span class="sxs-lookup"><span data-stu-id="0e90c-159">**TransportNamespace**</span></span>|<span data-ttu-id="0e90c-160">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-160">String</span></span>|<span data-ttu-id="0e90c-161">**InboundTransportLocationField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-161">**InboundTransportLocationField**</span></span>|<span data-ttu-id="0e90c-162">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-162">String</span></span>|  
|<span data-ttu-id="0e90c-163">**TransportType**</span><span class="sxs-lookup"><span data-stu-id="0e90c-163">**TransportType**</span></span>|<span data-ttu-id="0e90c-164">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-164">String</span></span>|<span data-ttu-id="0e90c-165">**InterchangeIDField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-165">**InterchangeIDField**</span></span>|<span data-ttu-id="0e90c-166">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-166">String</span></span>|  
|<span data-ttu-id="0e90c-167">**TransportLocation**</span><span class="sxs-lookup"><span data-stu-id="0e90c-167">**TransportLocation**</span></span>|<span data-ttu-id="0e90c-168">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-168">String</span></span>|<span data-ttu-id="0e90c-169">**ReceiveLocationNameField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-169">**ReceiveLocationNameField**</span></span>|<span data-ttu-id="0e90c-170">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-170">String</span></span>|  
|<span data-ttu-id="0e90c-171">**動作**</span><span class="sxs-lookup"><span data-stu-id="0e90c-171">**Action**</span></span>|<span data-ttu-id="0e90c-172">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-172">String</span></span>|<span data-ttu-id="0e90c-173">**ReceivePortNameField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-173">**ReceivePortNameField**</span></span>|<span data-ttu-id="0e90c-174">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-174">String</span></span>|  
|<span data-ttu-id="0e90c-175">**MessageExchangePattern**</span><span class="sxs-lookup"><span data-stu-id="0e90c-175">**MessageExchangePattern**</span></span>|<span data-ttu-id="0e90c-176">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-176">String</span></span>|<span data-ttu-id="0e90c-177">**InboundTransportTypeField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-177">**InboundTransportTypeField**</span></span>|<span data-ttu-id="0e90c-178">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-178">String</span></span>|  
|<span data-ttu-id="0e90c-179">**EndpointConfig**</span><span class="sxs-lookup"><span data-stu-id="0e90c-179">**EndpointConfig**</span></span>|<span data-ttu-id="0e90c-180">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-180">String</span></span>|<span data-ttu-id="0e90c-181">**IsRequestResponseField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-181">**IsRequestResponseField**</span></span>|<span data-ttu-id="0e90c-182">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-182">String</span></span>|  
|<span data-ttu-id="0e90c-183">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="0e90c-183">**TargetNamespace**</span></span>|<span data-ttu-id="0e90c-184">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-184">String</span></span>|<span data-ttu-id="0e90c-185">**DocumentSpecStrongNameField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-185">**DocumentSpecStrongNameField**</span></span>|<span data-ttu-id="0e90c-186">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-186">String</span></span>|  
|<span data-ttu-id="0e90c-187">**FixJaxRPC**</span><span class="sxs-lookup"><span data-stu-id="0e90c-187">**FixJaxRPC**</span></span>|<span data-ttu-id="0e90c-188">布林</span><span class="sxs-lookup"><span data-stu-id="0e90c-188">Boolean</span></span>|<span data-ttu-id="0e90c-189">**DocumentSpecNameField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-189">**DocumentSpecNameField**</span></span>|<span data-ttu-id="0e90c-190">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-190">String</span></span>|  
|<span data-ttu-id="0e90c-191">**WindowUserField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-191">**WindowUserField**</span></span>|<span data-ttu-id="0e90c-192">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-192">String</span></span>|<span data-ttu-id="0e90c-193">**MessageType**</span><span class="sxs-lookup"><span data-stu-id="0e90c-193">**MessageType**</span></span>|<span data-ttu-id="0e90c-194">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-194">String</span></span>|  
|<span data-ttu-id="0e90c-195">**CacheTimeout**</span><span class="sxs-lookup"><span data-stu-id="0e90c-195">**CacheTimeout**</span></span>|<span data-ttu-id="0e90c-196">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-196">String</span></span>|<span data-ttu-id="0e90c-197">**OutboundTransportCLSID**</span><span class="sxs-lookup"><span data-stu-id="0e90c-197">**OutboundTransportCLSID**</span></span>|<span data-ttu-id="0e90c-198">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-198">String</span></span>|  
|<span data-ttu-id="0e90c-199">**MethodNameField**</span><span class="sxs-lookup"><span data-stu-id="0e90c-199">**MethodNameField**</span></span>|<span data-ttu-id="0e90c-200">String</span><span class="sxs-lookup"><span data-stu-id="0e90c-200">String</span></span>|||  
  
## <a name="creating-a-custom-resolver"></a><span data-ttu-id="0e90c-201">建立自訂解析程式</span><span class="sxs-lookup"><span data-stu-id="0e90c-201">Creating a Custom Resolver</span></span>  
 <span data-ttu-id="0e90c-202">在執行階段，管線擷取的解析程式的連接字串，並呼叫解析程式管理員 (執行個體**ResolverMgr**類別)。</span><span class="sxs-lookup"><span data-stu-id="0e90c-202">At run time, a pipeline retrieves the resolver connection string and calls the resolver manager (an instance of the **ResolverMgr** class).</span></span> <span data-ttu-id="0e90c-203">解析程式管理員會剖析、 填入，並驗證的解析程式的連接字串。</span><span class="sxs-lookup"><span data-stu-id="0e90c-203">The resolver manager parses, populates, and validates the resolver connection string.</span></span> <span data-ttu-id="0e90c-204">它會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0e90c-204">It does this by doing the following:</span></span>  
  
- <span data-ttu-id="0e90c-205">它會剖析連接字串，以判斷哪些**解析程式**来載入型別。</span><span class="sxs-lookup"><span data-stu-id="0e90c-205">It parses the connection string to determine which **Resolver** type to load.</span></span>  
  
- <span data-ttu-id="0e90c-206">它符合此類型定義 （索引鍵是根 moniker，例如 UDDI） 的組態檔中的 moniker。</span><span class="sxs-lookup"><span data-stu-id="0e90c-206">It matches this type to a moniker defined in the configuration file (the key is the root moniker, such as UDDI).</span></span>  
  
- <span data-ttu-id="0e90c-207">它會讀取這個 moniker 解析程式的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="0e90c-207">It reads the assembly name of the resolver for this moniker.</span></span>  
  
- <span data-ttu-id="0e90c-208">它會載入指定的組件。</span><span class="sxs-lookup"><span data-stu-id="0e90c-208">It loads the specified assembly.</span></span>  
  
  <span data-ttu-id="0e90c-209">動態解析機制會快取載入的所有實作**IResolveProvider**介面，以避免重複的讀取組態資訊和數個內送訊息使用的相同時載入的組件解析程式。</span><span class="sxs-lookup"><span data-stu-id="0e90c-209">The dynamic resolution mechanism caches all loaded implementations of the **IResolveProvider** interface to avoid repeated reading of configuration information and assembly loading when several incoming messages use the same resolver.</span></span>  
  
  <span data-ttu-id="0e90c-210">最後，解析程式管理員會執行**解決**方法的具體**IResolveProvider**實作，並傳回已填入**字典**執行個體。</span><span class="sxs-lookup"><span data-stu-id="0e90c-210">Finally, the resolver manager executes the **Resolve** method of the concrete **IResolveProvider** implementation and returns the populated **Dictionary** instance.</span></span>  
  
  <span data-ttu-id="0e90c-211">**若要建立自訂解析程式**</span><span class="sxs-lookup"><span data-stu-id="0e90c-211">**To create a custom resolver**</span></span>  
  
1.  <span data-ttu-id="0e90c-212">建立可實作類別的組件**IResolveProvider**介面，並包含**解決**方法會傳回執行個體的解析程式事實**字典**類別。</span><span class="sxs-lookup"><span data-stu-id="0e90c-212">Create an assembly with a class that implements the **IResolveProvider** interface and contains a **Resolve** method that returns resolver facts as an instance of the **Dictionary** class.</span></span>  
  
2.  <span data-ttu-id="0e90c-213">註冊解析程式新增至 Esb.config 組態檔中使用**\<解析程式\>** 元素，其中包含做為根 moniker**名稱**屬性和完整限定的組件名稱為**型別**屬性。</span><span class="sxs-lookup"><span data-stu-id="0e90c-213">Register the resolver by adding it to the Esb.config configuration file using a **\<resolver\>** element that contains the root moniker as the **name** attribute and the fully qualified assembly name as the **type** attribute.</span></span>  
  
3.  <span data-ttu-id="0e90c-214">（選擇性）建立結構描述中定義的根 moniker 和查詢參數，並再將它儲存在 ESB。Schemas.Resolvers 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0e90c-214">(Optional) Create a schema that defines the root moniker and the query parameters, and then save it in the ESB.Schemas.Resolvers folder.</span></span> <span data-ttu-id="0e90c-215">名稱應該遵循現有的 ESB 命名慣例;這表示它應該使用的名稱加上"_Resolution.xsd"的根 moniker。</span><span class="sxs-lookup"><span data-stu-id="0e90c-215">The name should follow existing ESB naming conventions; this means it should use the name of the root moniker appended with "_Resolution.xsd".</span></span>  
  
4.  <span data-ttu-id="0e90c-216">（選擇性）從新的結構描述產生類別，並將它儲存在自訂解析程式的組件。</span><span class="sxs-lookup"><span data-stu-id="0e90c-216">(Optional) Generate a class from the new schema and save it in the custom resolver assembly.</span></span> <span data-ttu-id="0e90c-217">這會公開自訂解析程式中的型別的參數。</span><span class="sxs-lookup"><span data-stu-id="0e90c-217">This exposes typed parameters in the custom resolver.</span></span>  
  
5.  <span data-ttu-id="0e90c-218">在全域組件快取中註冊新的組件。</span><span class="sxs-lookup"><span data-stu-id="0e90c-218">Register the new assembly in the global assembly cache.</span></span>