---
title: "解析器和配接器提供者架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb7ea42e-b32c-40a8-b36b-c349f56f6edd
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b97eec38f868a6d1aa00684d92166bb2759a51d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="the-resolver-and-adapter-provider-framework"></a><span data-ttu-id="7728e-102">解析器和配接器提供者架構</span><span class="sxs-lookup"><span data-stu-id="7728e-102">The Resolver and Adapter Provider Framework</span></span>
<span data-ttu-id="7728e-103">解析器和配接器提供者架構支援路線、 轉換和端點解析和路由。</span><span class="sxs-lookup"><span data-stu-id="7728e-103">The Resolver and Adapter Provider Framework supports itinerary, transformation, and endpoint resolution and routing.</span></span> <span data-ttu-id="7728e-104">架構可以動態地解決端點，並設定輸出配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="7728e-104">The framework can dynamically resolve endpoints and set outbound adapter properties.</span></span> <span data-ttu-id="7728e-105">之後的解析程式元件會解析端點 （例如，傳出的 Web 服務端點上使用通用描述、 探索與整合 [UDDI] 來尋找），配接器提供者元件設定的已註冊的 BizTalk Server 的特定屬性配接器。</span><span class="sxs-lookup"><span data-stu-id="7728e-105">After a resolver component resolves an endpoint (for example, using Universal Description, Discovery, and Integration [UDDI] to look up an outbound Web service endpoint), an adapter provider component sets specific properties of registered BizTalk Server adapters.</span></span> <span data-ttu-id="7728e-106">例如，Wcf-basichttp 配接器提供者負責設定 BizTalk 特定訊息的端點 URI，將會使用特定的 BizTalk 配接器; 內容屬性FTP 配接器提供者會負責設定 FTP 配接器的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="7728e-106">For example, the WCF-BasicHttp adapter provider is responsible for setting the BizTalk-specific message context properties for the endpoint URI that will use the specific BizTalk adapter; the FTP adapter provider is responsible for setting the properties specific to the FTP adapter.</span></span>  
  
 <span data-ttu-id="7728e-107">解析器和配接器提供者架構的其中一個目標是以支援解析度和路由在任一個訊息層級，而不需使用 BizTalk 協調流程，或在協調流程層級。</span><span class="sxs-lookup"><span data-stu-id="7728e-107">One goal of the Resolver and Adapter Provider Framework is to support resolution and routing at either the messaging level, without requiring the use of BizTalk orchestrations, or at the orchestration level.</span></span> <span data-ttu-id="7728e-108">在這兩種情況下，可插式架構會提供簡易的開發、 部署和註冊新的解析程式和配接器提供者。</span><span class="sxs-lookup"><span data-stu-id="7728e-108">In both cases, the pluggable framework provides easy development, deployment, and registration of new resolvers and adapter providers.</span></span> <span data-ttu-id="7728e-109">所有的解析程式和配接器提供者實作妥善定義之介面，並視需要載入執行階段時透過組態檔中註冊。</span><span class="sxs-lookup"><span data-stu-id="7728e-109">All resolvers and adapter providers implement well-defined interfaces and are demand-loaded at run time through registration in the configuration files.</span></span>  
  
 <span data-ttu-id="7728e-110">ESB 發送器和 ESB 發送器解譯管線元件會使用傳遞的連接字串從路線 SOAP 標頭或管線組態至解析程式管理員解析器和配接器提供者架構。</span><span class="sxs-lookup"><span data-stu-id="7728e-110">Both the ESB Dispatcher and ESB Dispatcher Disassemble pipeline components use the Resolver and Adapter Provider Framework by passing the connection string from either the itinerary SOAP header or the pipeline configuration to the Resolver Manager.</span></span>  
  
 <span data-ttu-id="7728e-111">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]組態包含的所有已註冊的解析程式和配接器提供者的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7728e-111">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] configuration contains details of all registered resolvers and adapter providers.</span></span> <span data-ttu-id="7728e-112">在執行的階段，解析程式管理員和配接器管理員從組態檔讀取的已註冊的解析程式和配接器提供者的詳細資料，載入適當的組件，並將其儲存在 BizTalk 主控件層級快取中。</span><span class="sxs-lookup"><span data-stu-id="7728e-112">At run time, the resolver managers and adapter managers read details of the registered resolvers and adapter providers from the configuration files, load the appropriate assemblies, and store them in a BizTalk host–level cache.</span></span> <span data-ttu-id="7728e-113">此快取技術移除重複的組態檔的讀取和載入的組件的每一個提交訊息的需求。</span><span class="sxs-lookup"><span data-stu-id="7728e-113">This caching technique removes the requirement for repeated reading of configuration files and loading of assemblies for every submitted message.</span></span>  
  
 <span data-ttu-id="7728e-114">如需有關如何解析器和配接器提供者架構的運作方式以及如何擴充它藉由建立自訂的解析程式和配接器提供者，請參閱[修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。</span><span class="sxs-lookup"><span data-stu-id="7728e-114">For more information about how the Resolver and Adapter Provider Framework works and how you can extend it by creating custom resolvers and adapter providers, see [Modifying and Extending the BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).</span></span>  
  
## <a name="supported-resolution-mechanisms-resolvers"></a><span data-ttu-id="7728e-115">支援的解析機制 （解析程式）</span><span class="sxs-lookup"><span data-stu-id="7728e-115">Supported Resolution Mechanisms (Resolvers)</span></span>  
 <span data-ttu-id="7728e-116">BizTalk ESB Toolkit 包含下列解析程式：**靜態、 UDDI、 UDDI3、 XPATH，BRE BRI、 路線，路線靜態**和**LDAP**。</span><span class="sxs-lookup"><span data-stu-id="7728e-116">The BizTalk ESB Toolkit includes the following resolvers: **STATIC, UDDI, UDDI3, XPATH, BRE, BRI, ITINERARY, ITINERARY-STATIC** and **LDAP**.</span></span>  
  
 <span data-ttu-id="7728e-117">解析程式的連接字串一律組成**moniker** (例如**BRE**) 後面接著":\\\\」 和連接或處理程序的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7728e-117">A resolver's connection string always consists of a **moniker** (such as **BRE**) followed by ":\\\\" and the connection or processing details.</span></span> <span data-ttu-id="7728e-118">Moniker 符合相關聯的解析程式組態檔中的定義。</span><span class="sxs-lookup"><span data-stu-id="7728e-118">The moniker matches the definition of the associated resolver in the configuration file.</span></span> <span data-ttu-id="7728e-119">每個連接字串相關聯的屬性是唯一的而且並非所有的屬性不需要。</span><span class="sxs-lookup"><span data-stu-id="7728e-119">The properties associated with each connection string are unique, and not all properties are required.</span></span> <span data-ttu-id="7728e-120">每個 「 解決者 」 的結構描述位於 ESB。Resolvers.Schemas 專案。</span><span class="sxs-lookup"><span data-stu-id="7728e-120">The schema for each of the resolvers can be found in the ESB.Resolvers.Schemas project.</span></span>  
  
 <span data-ttu-id="7728e-121">連接字串的範例如下：</span><span class="sxs-lookup"><span data-stu-id="7728e-121">The following are examples of connection strings:</span></span>  
  
-   <span data-ttu-id="7728e-122">**靜態**</span><span class="sxs-lookup"><span data-stu-id="7728e-122">**STATIC**</span></span>  
  
     <span data-ttu-id="7728e-123">靜態：\\\TransportType=;</span><span class="sxs-lookup"><span data-stu-id="7728e-123">STATIC:\\\TransportType=;</span></span>  
  
     <span data-ttu-id="7728e-124">TransportLocation = http://localhost/ESB.CanadianServices/SubmitPOService.asmx;</span><span class="sxs-lookup"><span data-stu-id="7728e-124">TransportLocation=http://localhost/ESB.CanadianServices/SubmitPOService.asmx;</span></span>  
  
     <span data-ttu-id="7728e-125">動作 =;</span><span class="sxs-lookup"><span data-stu-id="7728e-125">Action=;</span></span>  
  
     <span data-ttu-id="7728e-126">EndPointConfig =;</span><span class="sxs-lookup"><span data-stu-id="7728e-126">EndPointConfig=;</span></span>  
  
     <span data-ttu-id="7728e-127">JaxRpcResponse = false;</span><span class="sxs-lookup"><span data-stu-id="7728e-127">JaxRpcResponse=false;</span></span>  
  
     <span data-ttu-id="7728e-128">MessageExchangePattern =;</span><span class="sxs-lookup"><span data-stu-id="7728e-128">MessageExchangePattern=;</span></span>  
  
     <span data-ttu-id="7728e-129">TargetNamespace = http://globalbank.esb.dynamicresolution.com/canadianservices/;</span><span class="sxs-lookup"><span data-stu-id="7728e-129">TargetNamespace=http://globalbank.esb.dynamicresolution.com/canadianservices/;</span></span>  
  
     <span data-ttu-id="7728e-130">TransformType =;</span><span class="sxs-lookup"><span data-stu-id="7728e-130">TransformType=;</span></span>  
  
-   <span data-ttu-id="7728e-131">**UDDI**</span><span class="sxs-lookup"><span data-stu-id="7728e-131">**UDDI**</span></span>  
  
     <span data-ttu-id="7728e-132">UDDI:\\\serverUrl= http://localhost: 9901/rmengine;</span><span class="sxs-lookup"><span data-stu-id="7728e-132">UDDI:\\\serverUrl=http://localhost:9901/rmengine;</span></span>  
  
     <span data-ttu-id="7728e-133">serviceName = OrderPurchaseWebService;</span><span class="sxs-lookup"><span data-stu-id="7728e-133">serviceName=OrderPurchaseWebService;</span></span>  
  
     <span data-ttu-id="7728e-134">serviceProvider = Microsoft 作法 ESB</span><span class="sxs-lookup"><span data-stu-id="7728e-134">serviceProvider=Microsoft Practices ESB</span></span>  
  
-   <span data-ttu-id="7728e-135">**XPATH**</span><span class="sxs-lookup"><span data-stu-id="7728e-135">**XPATH**</span></span>  
  
     <span data-ttu-id="7728e-136">\\\TransportType=;</span><span class="sxs-lookup"><span data-stu-id="7728e-136">\\\TransportType=;</span></span>  
  
     <span data-ttu-id="7728e-137">TransportLocation = /*[local-name = 'OrderDoc' and namespace-uri （) = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/'] /*[local-name = 'ID' and namespace-uri （) = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/']。</span><span class="sxs-lookup"><span data-stu-id="7728e-137">TransportLocation=/*[local-name()='OrderDoc' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*[local-name()='ID' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];</span></span>  
  
     <span data-ttu-id="7728e-138">動作 =;</span><span class="sxs-lookup"><span data-stu-id="7728e-138">Action=;</span></span>  
  
     <span data-ttu-id="7728e-139">EndPointConfig =;</span><span class="sxs-lookup"><span data-stu-id="7728e-139">EndPointConfig=;</span></span>  
  
     <span data-ttu-id="7728e-140">JaxRpcResponse =;</span><span class="sxs-lookup"><span data-stu-id="7728e-140">JaxRpcResponse=;</span></span>  
  
     <span data-ttu-id="7728e-141">MessageExchangePattern =;</span><span class="sxs-lookup"><span data-stu-id="7728e-141">MessageExchangePattern=;</span></span>  
  
     <span data-ttu-id="7728e-142">TargetNamespace = /*[local-name = 'OrderDoc' and namespace-uri （) = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/'] /*[local-name = 'customerName' 和命名空間 uri （） ='http: / /globalbank.esb.dynamicresolution.com/northamericanservices/']。</span><span class="sxs-lookup"><span data-stu-id="7728e-142">TargetNamespace=/*[local-name()='OrderDoc' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*[local-name()='customerName' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];</span></span>  
  
     <span data-ttu-id="7728e-143">TransformType =;</span><span class="sxs-lookup"><span data-stu-id="7728e-143">TransformType=;</span></span>  
  
-   <span data-ttu-id="7728e-144">**BRE**</span><span class="sxs-lookup"><span data-stu-id="7728e-144">**BRE**</span></span>  
  
     <span data-ttu-id="7728e-145">BRE:\\\policy=GetCanadaEndPoint;</span><span class="sxs-lookup"><span data-stu-id="7728e-145">BRE:\\\policy=GetCanadaEndPoint;</span></span>  
  
     <span data-ttu-id="7728e-146">版本 =;</span><span class="sxs-lookup"><span data-stu-id="7728e-146">version=;</span></span>  
  
     <span data-ttu-id="7728e-147">useMsg =;</span><span class="sxs-lookup"><span data-stu-id="7728e-147">useMsg=;</span></span>  
  
-   <span data-ttu-id="7728e-148">**BRI**</span><span class="sxs-lookup"><span data-stu-id="7728e-148">**BRI**</span></span>  
  
     <span data-ttu-id="7728e-149">BRI:\\\policy=ResolveItinerary;</span><span class="sxs-lookup"><span data-stu-id="7728e-149">BRI:\\\policy=ResolveItinerary;</span></span>  
  
     <span data-ttu-id="7728e-150">版本 =;</span><span class="sxs-lookup"><span data-stu-id="7728e-150">version=;</span></span>  
  
     <span data-ttu-id="7728e-151">useMsg =;</span><span class="sxs-lookup"><span data-stu-id="7728e-151">useMsg=;</span></span>  
  
-   <span data-ttu-id="7728e-152">**路線**</span><span class="sxs-lookup"><span data-stu-id="7728e-152">**ITINERARY**</span></span>  
  
     <span data-ttu-id="7728e-153">行程：\\\name=TwoWayTestItinerary;</span><span class="sxs-lookup"><span data-stu-id="7728e-153">ITINERARY:\\\name=TwoWayTestItinerary;</span></span>  
  
     <span data-ttu-id="7728e-154">版本 =;</span><span class="sxs-lookup"><span data-stu-id="7728e-154">version=;</span></span>  
  
-   <span data-ttu-id="7728e-155">**行程靜態**</span><span class="sxs-lookup"><span data-stu-id="7728e-155">**ITINERARY-STATIC**</span></span>  
  
     <span data-ttu-id="7728e-156">行程靜態：\\\name=TwoWayTestItinerary;</span><span class="sxs-lookup"><span data-stu-id="7728e-156">ITINERARY-STATIC:\\\name=TwoWayTestItinerary;</span></span>  
  
     <span data-ttu-id="7728e-157">版本 =;</span><span class="sxs-lookup"><span data-stu-id="7728e-157">version=;</span></span>  
  
-   <span data-ttu-id="7728e-158">**LDAP**</span><span class="sxs-lookup"><span data-stu-id="7728e-158">**LDAP**</span></span>  
  
     <span data-ttu-id="7728e-159">LDAP:\\\TransportType=SMTP;</span><span class="sxs-lookup"><span data-stu-id="7728e-159">LDAP:\\\TransportType=SMTP;</span></span>  
  
     <span data-ttu-id="7728e-160">TransportLocation = {mail}</span><span class="sxs-lookup"><span data-stu-id="7728e-160">TransportLocation={mail}</span></span>  
  
     <span data-ttu-id="7728e-161">篩選 = (&amp;(objectClass = User) (&#124; (userPrincipalName =yourname@domain.com)));</span><span class="sxs-lookup"><span data-stu-id="7728e-161">Filter=(&amp;(objectClass=User)(&#124;(userPrincipalName=yourname@domain.com)));</span></span>  
  
     <span data-ttu-id="7728e-162">SearchRoot =;</span><span class="sxs-lookup"><span data-stu-id="7728e-162">SearchRoot=;</span></span>  
  
     <span data-ttu-id="7728e-163">SearchScope = 樹狀子目錄。</span><span class="sxs-lookup"><span data-stu-id="7728e-163">SearchScope=Subtree;</span></span>  
  
     <span data-ttu-id="7728e-164">EndpointConfig = Subject = {mail} 行程測試訊息&amp;</span><span class="sxs-lookup"><span data-stu-id="7728e-164">EndpointConfig=Subject=Itinerary Test Message to {mail}&amp;</span></span>  
  
     <span data-ttu-id="7728e-165">SMTPAuthenticate = 0&amp;</span><span class="sxs-lookup"><span data-stu-id="7728e-165">SMTPAuthenticate=0&amp;</span></span>  
  
     <span data-ttu-id="7728e-166">SMTPHost = 127.0.0.1&amp;</span><span class="sxs-lookup"><span data-stu-id="7728e-166">SMTPHost=127.0.0.1&amp;</span></span>  
  
     <span data-ttu-id="7728e-167">From =test@globalbank.com&amp;</span><span class="sxs-lookup"><span data-stu-id="7728e-167">From=test@globalbank.com&amp;</span></span>  
  
     <span data-ttu-id="7728e-168">DeliveryReceipt = false&amp;</span><span class="sxs-lookup"><span data-stu-id="7728e-168">DeliveryReceipt=false&amp;</span></span>  
  
     <span data-ttu-id="7728e-169">MessagePartsAttachments = 0&amp;</span><span class="sxs-lookup"><span data-stu-id="7728e-169">MessagePartsAttachments=0&amp;</span></span>  
  
     <span data-ttu-id="7728e-170">ReadReceipt = false;</span><span class="sxs-lookup"><span data-stu-id="7728e-170">ReadReceipt=false;</span></span>  
  
     <span data-ttu-id="7728e-171">ThrowErrorIfNotFound = false;</span><span class="sxs-lookup"><span data-stu-id="7728e-171">ThrowErrorIfNotFound=false;</span></span>  
  
     <span data-ttu-id="7728e-172">動作 =;</span><span class="sxs-lookup"><span data-stu-id="7728e-172">Action=;</span></span>  
  
     <span data-ttu-id="7728e-173">JaxRpcResponse = false;</span><span class="sxs-lookup"><span data-stu-id="7728e-173">JaxRpcResponse=false;</span></span>  
  
     <span data-ttu-id="7728e-174">MessageExchangePattern =;</span><span class="sxs-lookup"><span data-stu-id="7728e-174">MessageExchangePattern=;</span></span>  
  
     <span data-ttu-id="7728e-175">TargetNamespace =;</span><span class="sxs-lookup"><span data-stu-id="7728e-175">TargetNamespace=;</span></span>  
  
     <span data-ttu-id="7728e-176">TransformType =;</span><span class="sxs-lookup"><span data-stu-id="7728e-176">TransformType=;</span></span>  
  
 <span data-ttu-id="7728e-177">並非所有的連接字串中的屬性是必要項。</span><span class="sxs-lookup"><span data-stu-id="7728e-177">Not all attributes in the connection string are mandatory.</span></span> <span data-ttu-id="7728e-178">此外， **EndPointConfig**是可以填入任何解析程式，並將傳回的特殊屬性。</span><span class="sxs-lookup"><span data-stu-id="7728e-178">In addition, **EndPointConfig** is a special attribute that any resolver can populate and return.</span></span> <span data-ttu-id="7728e-179">（選擇性） 在解析程式可以儲存對應至特定的 BizTalk 配接器內容屬性，則亦可以寫入至 BizTalk 訊息內容的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="7728e-179">Optionally, the resolver can store the name/value pairs that correspond to specific BizTalk Adapter Context properties, which it can, in turn, write to the context of the BizTalk message.</span></span>  
  
 <span data-ttu-id="7728e-180">在此情況下， **ResolverDictionary**包含已解決的所有屬性的執行個體所傳回的解析程序則會傳遞配接器管理員。</span><span class="sxs-lookup"><span data-stu-id="7728e-180">In this case, the **ResolverDictionary** instance that contains all the resolved properties returned from the resolution process then passes to the adapter manager.</span></span> <span data-ttu-id="7728e-181">配接器管理員會將字典傳遞給特定配接器提供者，將會設定所有配接器與端點特定 BizTalk 內容訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="7728e-181">The adapter manager passes the dictionary to the specific adapter provider that will set all the adapter-specific and endpoint-specific BizTalk Context properties for the message.</span></span> <span data-ttu-id="7728e-182">解析程式尋找**EndPointConfig**屬性，擷取對應到其各自的配接器 屬性的名稱/值組，並接著在訊息上設定這些值。</span><span class="sxs-lookup"><span data-stu-id="7728e-182">The resolvers look for the **EndPointConfig** property, extract the name/value pairs that correspond to their respective adapter properties, and then set these values on the message.</span></span>  
  
## <a name="supported-adapter-providers"></a><span data-ttu-id="7728e-183">支援的配接器提供者</span><span class="sxs-lookup"><span data-stu-id="7728e-183">Supported Adapter Providers</span></span>  
 <span data-ttu-id="7728e-184">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含下列內建配接器提供者：**檔案、 FTP、 SMTP、 MQSeries、 Wcf-basichttp、 Wcf-wshttp**和**Wcf-custom**。</span><span class="sxs-lookup"><span data-stu-id="7728e-184">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes the following built-in adapter providers: **FILE, FTP, SMTP,MQSeries, WCF-BasicHttp, WCF-WSHttp,** and **WCF-Custom**.</span></span> <span data-ttu-id="7728e-185">每個配接器提供者的名稱是與 BizTalk Server 中的關聯配接器 （傳輸類型） 的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="7728e-185">The name of each adapter provider is identical to the name of the associated adapter (transport type) in BizTalk Server.</span></span>  
  
 <span data-ttu-id="7728e-186">解析器和配接器提供者架構的主要優點是您可以透過建立並註冊您自己的自訂解析程式來解析端點資訊和自訂配接器提供者設定的已註冊的 BizTalk 配接器的特定屬性擴充它。</span><span class="sxs-lookup"><span data-stu-id="7728e-186">A major advantage of the Resolver and Adapter Provider Framework is that you can extend it by creating and registering your own custom resolvers to resolve endpoint information and custom adapter providers to set specific properties of registered BizTalk adapters.</span></span> <span data-ttu-id="7728e-187">如需詳細資訊，請參閱[修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。</span><span class="sxs-lookup"><span data-stu-id="7728e-187">For more information, see [Modifying and Extending the BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).</span></span>