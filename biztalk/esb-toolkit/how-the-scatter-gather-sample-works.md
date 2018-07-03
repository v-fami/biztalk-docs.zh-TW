---
title: 分散-集中範例運作方式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ccfacb7-4fd2-4a1a-bece-27eedd86bbe9
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c675f2c6a9f558be597f7765ec936daf0a5a2dde
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001096"
---
# <a name="how-the-scatter-gather-sample-works"></a><span data-ttu-id="cf74a-102">分散-集中範例運作方式</span><span class="sxs-lookup"><span data-stu-id="cf74a-102">How the Scatter-Gather Sample Works</span></span>
<span data-ttu-id="cf74a-103">範例應用程式建置一組包含從分散-集中路線檔案載入路線的 SOAP 標頭、 從磁碟載入指定的訊息檔案、 路線的標頭附加至訊息，並將它提交至透過匝道的 ESB處理程序。</span><span class="sxs-lookup"><span data-stu-id="cf74a-103">The sample application builds a set of SOAP headers containing the itinerary loaded from the Scatter-Gather itinerary file, loads the specified message file from disk, appends the itinerary headers to the message, and submits it to the ESB through an on-ramp for processing.</span></span> <span data-ttu-id="cf74a-104">如果路線，都產生回應，應用程式會收集這，並顯示在應用程式視窗中。</span><span class="sxs-lookup"><span data-stu-id="cf74a-104">If the itinerary generates a response, the application collects this and displays it in the application window.</span></span>  
  
 <span data-ttu-id="cf74a-105">為了協助您了解路線服務訊息中所使用的路線資訊，下列清單會顯示名為 ScatterGatherItinerary.xml 範例路線的組態檔。</span><span class="sxs-lookup"><span data-stu-id="cf74a-105">To help you understand how the Itinerary service uses the itinerary information in a message, the following listing shows the sample itinerary configuration file named ScatterGatherItinerary.xml.</span></span> <span data-ttu-id="cf74a-106">此路線的第一個區段會指定兩個服務引動過程步驟。</span><span class="sxs-lookup"><span data-stu-id="cf74a-106">The first section of this itinerary specifies two service invocation steps.</span></span>  
  
```xml  
<Itinerary xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema" uuid="" beginTime=""   
    completeTime="" state="Pending" isRequestResponse="false"   
    xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary">  
  <ServiceInstance uuid="" name="ScatterGather" type="Orchestration"  
                   state="Pending" position="0"   
                   isRequestResponse="false" xmlns="" />  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="ScatterGather"  
             type="Orchestration" state="Pending" isRequestResponse="false"  
             position="0" serviceInstanceId="" />  
  </Services>  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="DynamicTest"  
             type="Messaging" state="Pending" isRequestResponse="false"  
             position="1" serviceInstanceId="" />  
  </Services>  
</Itinerary>  
...  
```  
  
 <span data-ttu-id="cf74a-107">下列服務引動過程中的步驟路線清單會包含解析程式和連接字串可讓下列 XML 所示，找出在路線，定義每個服務路線服務的詳細資料區段。</span><span class="sxs-lookup"><span data-stu-id="cf74a-107">Following the list of service invocation steps in the itinerary is the section containing details of the resolvers and connection strings that allow the Itinerary service to locate each service defined in the itinerary, as shown in the following XML.</span></span>  
  
```xml  
<ResolverGroups xmlns="">  
 <Resolvers serviceId="ScatterGather0"><![CDATA[BRE:\\policy=ResolveEndPointScatterGather;version=;useMsg=;]]><![CDATA[UDDI3:\\serverUrl=http://localhost/uddi;bindingKey=uddi:esb:purchaseordersubmitorderservicebinding;credentialType=Ntlm]]></Resolvers>  
<Resolvers serviceId="DynamicTest1"><![CDATA[UDDI3:\\serverUrl=http://localhost/uddi;bindingKey=uddi:esb:orderfileservicebinding;credentialType=Ntlm]]>  
</Resolvers>  
  </ResolverGroups>  
```  
  
 <span data-ttu-id="cf74a-108">在此範例中，應用程式執行 SubmitPOService Web 服務兩次因為兩個解析程式的連接字串解析為此服務的位置時，才 (http://localhost/ESB.CanadianServices/SubmitPOService.asmx)。</span><span class="sxs-lookup"><span data-stu-id="cf74a-108">In this example, the application executes the SubmitPOService Web service twice because both resolver connection strings resolve to the location of this service (http://localhost/ESB.CanadianServices/SubmitPOService.asmx).</span></span> <span data-ttu-id="cf74a-109">訊息內容會指定訊息代理程式協調流程路線的第一個服務，若要啟用，定義在範例中，如下所示。</span><span class="sxs-lookup"><span data-stu-id="cf74a-109">The message context specifies the Broker orchestration as the first itinerary service to activate, defined in the sample as the following.</span></span>  
  
```csharp  
(Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName == "ScatterGather")  
     && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState ==   
    "Pending") && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType   
    == "Orchestration")  
```  
  
 <span data-ttu-id="cf74a-110">訊息代理程式協調流程會分析其路線步驟的設定，並擷取與路線的步驟相關聯的解析程式的集合。</span><span class="sxs-lookup"><span data-stu-id="cf74a-110">The Broker orchestration analyzes the settings for its itinerary step and retrieves a collection of resolvers associated with the itinerary step.</span></span> <span data-ttu-id="cf74a-111">針對每個這些解析程式中，協調流程會使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析程式和配接器架構，來解決服務端點。</span><span class="sxs-lookup"><span data-stu-id="cf74a-111">For each of these resolvers, the orchestration uses the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Framework to resolve the service endpoint.</span></span> <span data-ttu-id="cf74a-112">訊息代理程式協調流程接著會啟動 n 個 ServiceDispatcher 協調流程以非同步方式 （其中 n 是路線 ScatterGather 服務相關聯的解析程式數目） 來分派要求訊息，並指定下列參數：</span><span class="sxs-lookup"><span data-stu-id="cf74a-112">The Broker orchestration then activates n number of ServiceDispatcher orchestrations asynchronously (where n is the number of resolvers associated with the ScatterGather service in the itinerary) to dispatch the request message with following parameters:</span></span>  
  
- <span data-ttu-id="cf74a-113">**TransportLocation**。</span><span class="sxs-lookup"><span data-stu-id="cf74a-113">**TransportLocation**.</span></span> <span data-ttu-id="cf74a-114">解析程式會填入此參數。</span><span class="sxs-lookup"><span data-stu-id="cf74a-114">The resolver populates this parameter.</span></span>  
  
- <span data-ttu-id="cf74a-115">**TransportType**。</span><span class="sxs-lookup"><span data-stu-id="cf74a-115">**TransportType**.</span></span> <span data-ttu-id="cf74a-116">解析程式會填入此參數。</span><span class="sxs-lookup"><span data-stu-id="cf74a-116">The resolver populates this parameter.</span></span>  
  
- <span data-ttu-id="cf74a-117">**ResolverDictionary**。</span><span class="sxs-lookup"><span data-stu-id="cf74a-117">**ResolverDictionary**.</span></span> <span data-ttu-id="cf74a-118">這個參數會包含解析程式事實填入具體的解析程式執行個體的集合。</span><span class="sxs-lookup"><span data-stu-id="cf74a-118">This parameter contains a collection of resolver facts populated by the concrete resolver instance.</span></span>  
  
- <span data-ttu-id="cf74a-119">**InboundMessage**。</span><span class="sxs-lookup"><span data-stu-id="cf74a-119">**InboundMessage**.</span></span> <span data-ttu-id="cf74a-120">這個參數會包含原始訊息包含路線。</span><span class="sxs-lookup"><span data-stu-id="cf74a-120">This parameter contains the original message that contains the itinerary.</span></span>  
  
- <span data-ttu-id="cf74a-121">**ServiceResponsePort**。</span><span class="sxs-lookup"><span data-stu-id="cf74a-121">**ServiceResponsePort**.</span></span> <span data-ttu-id="cf74a-122">這個參數是自我相互關聯會接收來自 ServiceDispatcher 協調流程的執行個體的回應的回應連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="cf74a-122">This parameter is the name of the self-correlating response port that will receive responses from the instances of the ServiceDispatcher orchestration.</span></span>  
  
  <span data-ttu-id="cf74a-123">ServiceDispatcher 協調流程的每個執行個體使用的 ResolveMapScatterGather 原則來要求和回應訊息，根據 Microsoft BizTalk 對應類型解析**TransportType**和**TransportLocation**屬性。</span><span class="sxs-lookup"><span data-stu-id="cf74a-123">Each instance of the ServiceDispatcher orchestration uses the ResolveMapScatterGather policy to resolve the Microsoft BizTalk map types for the request and response message, based on **TransportType** and **TransportLocation** properties.</span></span> <span data-ttu-id="cf74a-124">協調流程執行個體使用的已解析的對應，將輸入的訊息轉換成 Web 服務呼叫的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="cf74a-124">The orchestration instances use the resolved maps to transform the inbound message into the request message for the Web service call.</span></span>  
  
  <span data-ttu-id="cf74a-125">ESB 配接器管理員設定在要求訊息的 BizTalk 則請求-回應連接埠轉送名為 ServiceRequestPort 輸出傳輸內容屬性。</span><span class="sxs-lookup"><span data-stu-id="cf74a-125">The ESB Adapter Manager sets the outbound transport context properties on the request message, which BizTalk then forwards to the solicit-response port named ServiceRequestPort.</span></span>  
  
  <span data-ttu-id="cf74a-126">從服務收到回應訊息，當 ServiceDispatcher 協調流程會使用轉換成標準格式輸入的回應訊息解析的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="cf74a-126">When it receives a response message from a service, the ServiceDispatcher orchestration uses the resolved map information to transform the inbound response message to a canonical format.</span></span> <span data-ttu-id="cf74a-127">然後 ServiceResponse 信封中包裝的已修改的回應，並將它轉送至訊息代理程式協調流程透過自我相互關聯的連接埠。</span><span class="sxs-lookup"><span data-stu-id="cf74a-127">It then wraps the modified response within the ServiceResponse envelope and forwards it to the Broker orchestration through the self-correlating port.</span></span> <span data-ttu-id="cf74a-128">訊息代理程式協調流程會彙總所有的連入回應，並準備使用 GlobalBank.ESB.ScatterGather.Processes.AggregatingPipeline，最後的回應訊息，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cf74a-128">The Broker orchestration aggregates all incoming responses and prepares the final response message using GlobalBank.ESB.ScatterGather.Processes.AggregatingPipeline, as shown in the following code.</span></span>  
  
```csharp  
AggregatedResponse.Body = null;  
AggregatedResponse(*) = InboundMessage(*);  
Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteSendPipeline(  
    typeof(GlobalBank.ESB.ScatterGather.Processes.AggregatingPipeline),  
    messageAggregator,AggregatedResponse);  
```  
  
 <span data-ttu-id="cf74a-129">此程式碼會預先定義的信封中包裝整個批次的回應。</span><span class="sxs-lookup"><span data-stu-id="cf74a-129">This code wraps the entire batch of responses within a predefined envelope.</span></span> <span data-ttu-id="cf74a-130">訊息代理程式協調流程接著前進到路線**DynamicTest**路線的步驟中，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cf74a-130">The Broker orchestration then advances the itinerary to the **DynamicTest** itinerary step, as shown in the following code.</span></span>  
  
```csharp  
// Copy the context and advance the itinerary.  
OutboundMessage = AggregatedResponse.Body;  
OutboundMessage(*) = AggregatedResponse(*);  
// Advance the Itinerary to the next step.  
itinerary.Itinerary.Advance(OutboundMessage, itineraryStep);  
```  
  
 <span data-ttu-id="cf74a-131">因為名稱為服務型別屬性**DynamicTest**設為**Messaging**，則**ItineraryHelper**類別將解析程式的屬性升級至的內容名為訊息**OutboundMessage**。</span><span class="sxs-lookup"><span data-stu-id="cf74a-131">Because the service type attribute named **DynamicTest** is set to **Messaging**, the **ItineraryHelper** class promotes the resolver properties into the context of the message named **OutboundMessage**.</span></span> <span data-ttu-id="cf74a-132">訊息代理程式協調流程會將此訊息傳送至 BizTalk 直接繫結連接埠。</span><span class="sxs-lookup"><span data-stu-id="cf74a-132">The Broker orchestration sends this message to a BizTalk direct-bound port.</span></span> <span data-ttu-id="cf74a-133">BizTalk 然後會將訊息轉送至動態傳送埠所代表**ServiceName**訂用帳戶，也就是**DynamicTest**。</span><span class="sxs-lookup"><span data-stu-id="cf74a-133">BizTalk then forwards the message to the dynamic send port represented by the **ServiceName** subscription, which is **DynamicTest**.</span></span> <span data-ttu-id="cf74a-134">此傳送埠將序列化至 \Source\Samples\DynamicResolution\Test\Filedrop\Out 資料夾最後彙總的回應。</span><span class="sxs-lookup"><span data-stu-id="cf74a-134">This send port serializes the final aggregated response to the \Source\Samples\DynamicResolution\Test\Filedrop\Out folder.</span></span>