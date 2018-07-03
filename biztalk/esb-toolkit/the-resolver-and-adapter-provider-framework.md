---
title: ESB 解析程式和配接器提供者架構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb7ea42e-b32c-40a8-b36b-c349f56f6edd
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95134a1f806398f14a5596149eb605e2de20cac2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002799"
---
# <a name="the-resolver-and-adapter-provider-framework"></a><span data-ttu-id="37ea3-102">解析程式和配接器提供者架構</span><span class="sxs-lookup"><span data-stu-id="37ea3-102">The Resolver and Adapter Provider Framework</span></span>
<span data-ttu-id="37ea3-103">解析程式和配接器提供者架構支援路線、 轉換和端點解析和路由。</span><span class="sxs-lookup"><span data-stu-id="37ea3-103">The Resolver and Adapter Provider Framework supports itinerary, transformation, and endpoint resolution and routing.</span></span> <span data-ttu-id="37ea3-104">架構可以動態地解析端點，並設定輸出配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="37ea3-104">The framework can dynamically resolve endpoints and set outbound adapter properties.</span></span> <span data-ttu-id="37ea3-105">之後的解析程式元件會解析端點 （例如，使用通用描述、 探索與整合 [UDDI] 來查看輸出的 Web 服務端點），配接器提供者元件會設定已註冊的 BizTalk Server 的特定屬性配接器。</span><span class="sxs-lookup"><span data-stu-id="37ea3-105">After a resolver component resolves an endpoint (for example, using Universal Description, Discovery, and Integration [UDDI] to look up an outbound Web service endpoint), an adapter provider component sets specific properties of registered BizTalk Server adapters.</span></span> <span data-ttu-id="37ea3-106">比方說，Wcf-basichttp 配接器提供者負責設定 BizTalk 特定訊息的端點 URI，將會使用特定的 BizTalk 配接器; 的內容屬性FTP 配接器提供者會負責設定的 FTP 配接器的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="37ea3-106">For example, the WCF-BasicHttp adapter provider is responsible for setting the BizTalk-specific message context properties for the endpoint URI that will use the specific BizTalk adapter; the FTP adapter provider is responsible for setting the properties specific to the FTP adapter.</span></span>  
  
 <span data-ttu-id="37ea3-107">解析程式和配接器提供者架構的其中一個目標是支援解析和路由在任一個傳訊層級，而不需使用 BizTalk 協調流程，或在協調流程層級。</span><span class="sxs-lookup"><span data-stu-id="37ea3-107">One goal of the Resolver and Adapter Provider Framework is to support resolution and routing at either the messaging level, without requiring the use of BizTalk orchestrations, or at the orchestration level.</span></span> <span data-ttu-id="37ea3-108">在這兩種情況下，隨插即用的架構會提供簡易的開發、 部署和註冊新的解析程式和配接器提供者。</span><span class="sxs-lookup"><span data-stu-id="37ea3-108">In both cases, the pluggable framework provides easy development, deployment, and registration of new resolvers and adapter providers.</span></span> <span data-ttu-id="37ea3-109">所有的解析程式和配接器提供者實作定義完善的介面，並會在執行階段透過組態檔中註冊的需求載入。</span><span class="sxs-lookup"><span data-stu-id="37ea3-109">All resolvers and adapter providers implement well-defined interfaces and are demand-loaded at run time through registration in the configuration files.</span></span>  
  
 <span data-ttu-id="37ea3-110">ESB 發送器和 ESB 發送器解譯管線元件使用的解析程式和配接器提供者架構，藉由傳遞路線 SOAP 標頭或管線組態到解析程式管理員的連接字串。</span><span class="sxs-lookup"><span data-stu-id="37ea3-110">Both the ESB Dispatcher and ESB Dispatcher Disassemble pipeline components use the Resolver and Adapter Provider Framework by passing the connection string from either the itinerary SOAP header or the pipeline configuration to the Resolver Manager.</span></span>  
  
 <span data-ttu-id="37ea3-111">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]組態包含的所有已註冊的解析程式和配接器提供者的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="37ea3-111">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] configuration contains details of all registered resolvers and adapter providers.</span></span> <span data-ttu-id="37ea3-112">在執行的階段、 解析程式管理員和配接器管理員讀取組態檔中的已註冊的解析程式和配接器提供者的詳細資料的內容，載入適當的組件，並將它們儲存在 BizTalk 主控件層級快取檔案。</span><span class="sxs-lookup"><span data-stu-id="37ea3-112">At run time, the resolver managers and adapter managers read details of the registered resolvers and adapter providers from the configuration files, load the appropriate assemblies, and store them in a BizTalk host–level cache.</span></span> <span data-ttu-id="37ea3-113">此快取技術中移除重複的組態檔的讀取和載入之組件的每個已提交之訊息的需求。</span><span class="sxs-lookup"><span data-stu-id="37ea3-113">This caching technique removes the requirement for repeated reading of configuration files and loading of assemblies for every submitted message.</span></span>  
  
 <span data-ttu-id="37ea3-114">如需有關如何解析器和配接器提供者架構的運作方式以及如何擴充它藉由建立自訂解析程式和配接器提供者，請參閱[修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。</span><span class="sxs-lookup"><span data-stu-id="37ea3-114">For more information about how the Resolver and Adapter Provider Framework works and how you can extend it by creating custom resolvers and adapter providers, see [Modifying and Extending the BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).</span></span>  
  
## <a name="supported-resolution-mechanisms-resolvers"></a><span data-ttu-id="37ea3-115">支援的解析機制 （解析程式）</span><span class="sxs-lookup"><span data-stu-id="37ea3-115">Supported Resolution Mechanisms (Resolvers)</span></span>  
 <span data-ttu-id="37ea3-116">BizTalk ESB 工具組包含下列的解析程式：**靜態、 UDDI、 UDDI3、 XPATH，BRE、 BRI、 路線，路線靜態**並**LDAP**。</span><span class="sxs-lookup"><span data-stu-id="37ea3-116">The BizTalk ESB Toolkit includes the following resolvers: **STATIC, UDDI, UDDI3, XPATH, BRE, BRI, ITINERARY, ITINERARY-STATIC** and **LDAP**.</span></span>  
  
 <span data-ttu-id="37ea3-117">永遠包含解析程式的連接字串**moniker** (例如**BRE**) 後面接著":\\\\」 和連接或處理程序的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="37ea3-117">A resolver's connection string always consists of a **moniker** (such as **BRE**) followed by ":\\\\" and the connection or processing details.</span></span> <span data-ttu-id="37ea3-118">Moniker 會比對相關聯的解析程式組態檔中的定義。</span><span class="sxs-lookup"><span data-stu-id="37ea3-118">The moniker matches the definition of the associated resolver in the configuration file.</span></span> <span data-ttu-id="37ea3-119">每個連接字串相關聯的屬性是唯一的而且需要不是所有屬性。</span><span class="sxs-lookup"><span data-stu-id="37ea3-119">The properties associated with each connection string are unique, and not all properties are required.</span></span> <span data-ttu-id="37ea3-120">解析程式的每個結構描述位於 ESB。Resolvers.Schemas 專案。</span><span class="sxs-lookup"><span data-stu-id="37ea3-120">The schema for each of the resolvers can be found in the ESB.Resolvers.Schemas project.</span></span>  
  
 <span data-ttu-id="37ea3-121">連接字串的範例如下：</span><span class="sxs-lookup"><span data-stu-id="37ea3-121">The following are examples of connection strings:</span></span>  
  
- <span data-ttu-id="37ea3-122">**靜態**</span><span class="sxs-lookup"><span data-stu-id="37ea3-122">**STATIC**</span></span>  
  
   <span data-ttu-id="37ea3-123">STATIC:\\\TransportType=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-123">STATIC:\\\TransportType=;</span></span>  
  
   <span data-ttu-id="37ea3-124">TransportLocation =<http://localhost/ESB.CanadianServices/SubmitPOService.asmx>;</span><span class="sxs-lookup"><span data-stu-id="37ea3-124">TransportLocation=<http://localhost/ESB.CanadianServices/SubmitPOService.asmx>;</span></span>  
  
   <span data-ttu-id="37ea3-125">Action=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-125">Action=;</span></span>  
  
   <span data-ttu-id="37ea3-126">EndPointConfig=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-126">EndPointConfig=;</span></span>  
  
   <span data-ttu-id="37ea3-127">JaxRpcResponse=false;</span><span class="sxs-lookup"><span data-stu-id="37ea3-127">JaxRpcResponse=false;</span></span>  
  
   <span data-ttu-id="37ea3-128">MessageExchangePattern=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-128">MessageExchangePattern=;</span></span>  
  
   <span data-ttu-id="37ea3-129">TargetNamespace=<http://globalbank.esb.dynamicresolution.com/canadianservices/>;</span><span class="sxs-lookup"><span data-stu-id="37ea3-129">TargetNamespace=<http://globalbank.esb.dynamicresolution.com/canadianservices/>;</span></span>  
  
   <span data-ttu-id="37ea3-130">TransformType=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-130">TransformType=;</span></span>  
  
- <span data-ttu-id="37ea3-131">**UDDI**</span><span class="sxs-lookup"><span data-stu-id="37ea3-131">**UDDI**</span></span>  
  
   <span data-ttu-id="37ea3-132">UDDI:\\\serverUrl=<http://localhost:9901/rmengine>;</span><span class="sxs-lookup"><span data-stu-id="37ea3-132">UDDI:\\\serverUrl=<http://localhost:9901/rmengine>;</span></span>  
  
   <span data-ttu-id="37ea3-133">serviceName=OrderPurchaseWebService;</span><span class="sxs-lookup"><span data-stu-id="37ea3-133">serviceName=OrderPurchaseWebService;</span></span>  
  
   <span data-ttu-id="37ea3-134">serviceProvider=Microsoft Practices ESB</span><span class="sxs-lookup"><span data-stu-id="37ea3-134">serviceProvider=Microsoft Practices ESB</span></span>  
  
- <span data-ttu-id="37ea3-135">**XPATH**</span><span class="sxs-lookup"><span data-stu-id="37ea3-135">**XPATH**</span></span>  
  
   <span data-ttu-id="37ea3-136">XPATH:\\\TransportType=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-136">XPATH:\\\TransportType=;</span></span>  
  
   `TransportLocation=/*[local-name()='OrderDoc' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*[local-name()='ID' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];`  
  
   <span data-ttu-id="37ea3-137">Action=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-137">Action=;</span></span>  
  
   <span data-ttu-id="37ea3-138">EndPointConfig=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-138">EndPointConfig=;</span></span>  
  
   <span data-ttu-id="37ea3-139">JaxRpcResponse=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-139">JaxRpcResponse=;</span></span>  
  
   <span data-ttu-id="37ea3-140">MessageExchangePattern=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-140">MessageExchangePattern=;</span></span>  
  
   `TargetNamespace=/*[local-name()='OrderDoc' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*[local-name()='customerName' and namespace-uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];`  
  
   <span data-ttu-id="37ea3-141">TransformType=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-141">TransformType=;</span></span>  

- <span data-ttu-id="37ea3-142">**BRE**</span><span class="sxs-lookup"><span data-stu-id="37ea3-142">**BRE**</span></span>  
  
   <span data-ttu-id="37ea3-143">BRE:\\\policy=GetCanadaEndPoint;</span><span class="sxs-lookup"><span data-stu-id="37ea3-143">BRE:\\\policy=GetCanadaEndPoint;</span></span>  
  
   <span data-ttu-id="37ea3-144">version=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-144">version=;</span></span>  
  
   <span data-ttu-id="37ea3-145">useMsg=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-145">useMsg=;</span></span>  
  
- <span data-ttu-id="37ea3-146">**BRI**</span><span class="sxs-lookup"><span data-stu-id="37ea3-146">**BRI**</span></span>  
  
   <span data-ttu-id="37ea3-147">BRI:\\\policy=ResolveItinerary;</span><span class="sxs-lookup"><span data-stu-id="37ea3-147">BRI:\\\policy=ResolveItinerary;</span></span>  
  
   <span data-ttu-id="37ea3-148">version=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-148">version=;</span></span>  
  
   <span data-ttu-id="37ea3-149">useMsg=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-149">useMsg=;</span></span>  
  
- <span data-ttu-id="37ea3-150">**路線**</span><span class="sxs-lookup"><span data-stu-id="37ea3-150">**ITINERARY**</span></span>  
  
   <span data-ttu-id="37ea3-151">ITINERARY:\\\name=TwoWayTestItinerary;</span><span class="sxs-lookup"><span data-stu-id="37ea3-151">ITINERARY:\\\name=TwoWayTestItinerary;</span></span>  
  
   <span data-ttu-id="37ea3-152">version=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-152">version=;</span></span>  
  
- <span data-ttu-id="37ea3-153">**路線-靜態**</span><span class="sxs-lookup"><span data-stu-id="37ea3-153">**ITINERARY-STATIC**</span></span>  
  
   <span data-ttu-id="37ea3-154">路線靜態：\\\name=TwoWayTestItinerary;</span><span class="sxs-lookup"><span data-stu-id="37ea3-154">ITINERARY-STATIC:\\\name=TwoWayTestItinerary;</span></span>  
  
   <span data-ttu-id="37ea3-155">version=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-155">version=;</span></span>  
  
- <span data-ttu-id="37ea3-156">**LDAP**</span><span class="sxs-lookup"><span data-stu-id="37ea3-156">**LDAP**</span></span>  
  
   <span data-ttu-id="37ea3-157">LDAP:\\\TransportType=SMTP;</span><span class="sxs-lookup"><span data-stu-id="37ea3-157">LDAP:\\\TransportType=SMTP;</span></span>  
  
   <span data-ttu-id="37ea3-158">TransportLocation={mail}</span><span class="sxs-lookup"><span data-stu-id="37ea3-158">TransportLocation={mail}</span></span>  
  
   <span data-ttu-id="37ea3-159">篩選 = (&(objectClass=User) (| (userPrincipalName =yourname@domain.com)));</span><span class="sxs-lookup"><span data-stu-id="37ea3-159">Filter=(&(objectClass=User)(|(userPrincipalName=yourname@domain.com)));</span></span>  
  
   <span data-ttu-id="37ea3-160">SearchRoot=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-160">SearchRoot=;</span></span>  
  
   <span data-ttu-id="37ea3-161">SearchScope=Subtree;</span><span class="sxs-lookup"><span data-stu-id="37ea3-161">SearchScope=Subtree;</span></span>  
  
   <span data-ttu-id="37ea3-162">EndpointConfig = Subject = {郵件} 路線測試訊息 （& s)</span><span class="sxs-lookup"><span data-stu-id="37ea3-162">EndpointConfig=Subject=Itinerary Test Message to {mail}&</span></span> 
  
   <span data-ttu-id="37ea3-163">SMTPAuthenticate = 0 （& s)</span><span class="sxs-lookup"><span data-stu-id="37ea3-163">SMTPAuthenticate=0&</span></span>
  
   <span data-ttu-id="37ea3-164">SMTPHost = 127.0.0.1 （& s)</span><span class="sxs-lookup"><span data-stu-id="37ea3-164">SMTPHost=127.0.0.1&</span></span>
  
   <span data-ttu-id="37ea3-165">From =test@globalbank.com（& s)</span><span class="sxs-lookup"><span data-stu-id="37ea3-165">From=test@globalbank.com&</span></span>
  
   <span data-ttu-id="37ea3-166">DeliveryReceipt = false （& s)</span><span class="sxs-lookup"><span data-stu-id="37ea3-166">DeliveryReceipt=false&</span></span>
  
   <span data-ttu-id="37ea3-167">MessagePartsAttachments = 0 （& s)</span><span class="sxs-lookup"><span data-stu-id="37ea3-167">MessagePartsAttachments=0&</span></span>
  
   <span data-ttu-id="37ea3-168">ReadReceipt=false;</span><span class="sxs-lookup"><span data-stu-id="37ea3-168">ReadReceipt=false;</span></span>  
  
   <span data-ttu-id="37ea3-169">ThrowErrorIfNotFound=false;</span><span class="sxs-lookup"><span data-stu-id="37ea3-169">ThrowErrorIfNotFound=false;</span></span>  
  
   <span data-ttu-id="37ea3-170">Action=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-170">Action=;</span></span>  
  
   <span data-ttu-id="37ea3-171">JaxRpcResponse=false;</span><span class="sxs-lookup"><span data-stu-id="37ea3-171">JaxRpcResponse=false;</span></span>  
  
   <span data-ttu-id="37ea3-172">MessageExchangePattern=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-172">MessageExchangePattern=;</span></span>  
  
   <span data-ttu-id="37ea3-173">TargetNamespace=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-173">TargetNamespace=;</span></span>  
  
   <span data-ttu-id="37ea3-174">TransformType=;</span><span class="sxs-lookup"><span data-stu-id="37ea3-174">TransformType=;</span></span>  
  
  <span data-ttu-id="37ea3-175">並非所有的連接字串中的屬性是必要項目。</span><span class="sxs-lookup"><span data-stu-id="37ea3-175">Not all attributes in the connection string are mandatory.</span></span> <span data-ttu-id="37ea3-176">颾魤 ㄛ **EndPointConfig**是特殊的屬性，可以填入任何解析程式，並將其傳回。</span><span class="sxs-lookup"><span data-stu-id="37ea3-176">In addition, **EndPointConfig** is a special attribute that any resolver can populate and return.</span></span> <span data-ttu-id="37ea3-177">（選擇性） 在解析程式可以儲存對應至特定的 BizTalk 配接器內容屬性，它反而可以寫入 BizTalk 訊息內容的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="37ea3-177">Optionally, the resolver can store the name/value pairs that correspond to specific BizTalk Adapter Context properties, which it can, in turn, write to the context of the BizTalk message.</span></span>  
  
  <span data-ttu-id="37ea3-178">在此情況下， **ResolverDictionary**包含已解析的所有屬性的執行個體解析程序然後傳遞回到配接器管理員。</span><span class="sxs-lookup"><span data-stu-id="37ea3-178">In this case, the **ResolverDictionary** instance that contains all the resolved properties returned from the resolution process then passes to the adapter manager.</span></span> <span data-ttu-id="37ea3-179">配接器管理員會將字典傳遞至會設定所有配接器與端點特定 BizTalk 內容訊息屬性的特定配接器提供者。</span><span class="sxs-lookup"><span data-stu-id="37ea3-179">The adapter manager passes the dictionary to the specific adapter provider that will set all the adapter-specific and endpoint-specific BizTalk Context properties for the message.</span></span> <span data-ttu-id="37ea3-180">解析程式尋找**EndPointConfig**屬性，擷取對應到其各自的配接器 屬性的名稱/值組，並接著在訊息上設定這些值。</span><span class="sxs-lookup"><span data-stu-id="37ea3-180">The resolvers look for the **EndPointConfig** property, extract the name/value pairs that correspond to their respective adapter properties, and then set these values on the message.</span></span>  
  
## <a name="supported-adapter-providers"></a><span data-ttu-id="37ea3-181">支援的配接器提供者</span><span class="sxs-lookup"><span data-stu-id="37ea3-181">Supported Adapter Providers</span></span>  
 <span data-ttu-id="37ea3-182">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包括下列的內建配接器提供者：**檔案、 FTP、 SMTP、 MQSeries、 Wcf-basichttp、 Wcf-wshttp**並**Wcf-custom**。</span><span class="sxs-lookup"><span data-stu-id="37ea3-182">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes the following built-in adapter providers: **FILE, FTP, SMTP,MQSeries, WCF-BasicHttp, WCF-WSHttp,** and **WCF-Custom**.</span></span> <span data-ttu-id="37ea3-183">每個配接器提供者的名稱完全相同的 BizTalk Server 中的相關聯配接器 （傳輸類型） 的名稱。</span><span class="sxs-lookup"><span data-stu-id="37ea3-183">The name of each adapter provider is identical to the name of the associated adapter (transport type) in BizTalk Server.</span></span>  
  
 <span data-ttu-id="37ea3-184">解析程式和配接器提供者架構的主要優點是您可以藉由建立並註冊您自己自訂的解析程式，以解析端點資訊和設定的已註冊的 BizTalk 配接器的特定屬性的自訂配接器提供者擴充它。</span><span class="sxs-lookup"><span data-stu-id="37ea3-184">A major advantage of the Resolver and Adapter Provider Framework is that you can extend it by creating and registering your own custom resolvers to resolve endpoint information and custom adapter providers to set specific properties of registered BizTalk adapters.</span></span> <span data-ttu-id="37ea3-185">如需詳細資訊，請參閱 <<c0> [ 修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。</span><span class="sxs-lookup"><span data-stu-id="37ea3-185">For more information, see [Modifying and Extending the BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).</span></span>
