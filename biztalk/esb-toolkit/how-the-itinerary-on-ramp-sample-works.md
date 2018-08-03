---
title: 路線入口範例運作方式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f4f318c-b955-4a3d-88db-c0d324b63b21
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f282e49b8095059b273bd737d6fb38ff97090f5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966063"
---
# <a name="how-the-itinerary-on-ramp-sample-works"></a><span data-ttu-id="120a5-102">路線入口範例運作方式</span><span class="sxs-lookup"><span data-stu-id="120a5-102">How the Itinerary On-Ramp Sample Works</span></span>
<span data-ttu-id="120a5-103">範例應用程式建置一組包含您在用戶端應用程式視窗中，使用控制項建立路線的 SOAP 標頭的路線測試用戶端會從磁碟載入指定的訊息檔案、 路線的標頭附加至訊息，並請將它提交至路線入口匝處理透過 ESB。</span><span class="sxs-lookup"><span data-stu-id="120a5-103">The sample Itinerary Test Client application builds a set of SOAP headers that contain the itinerary that you create using the controls in the client application window, loads the specified message file from disk, appends the itinerary headers to the message, and submits it to the ESB through an Itinerary on-ramp for processing.</span></span> <span data-ttu-id="120a5-104">如果路線，都產生回應，應用程式會收集回應，並顯示在應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="120a5-104">If the itinerary generates a response, the application collects the response and displays it in the application window.</span></span>  

 <span data-ttu-id="120a5-105">若要查看單向和雙向使用協調流程、 訊息、 或兩者的組合的案例，您可以選擇從數個範例路線的組態檔。</span><span class="sxs-lookup"><span data-stu-id="120a5-105">You can choose from several sample itinerary configuration files to see one-way and two-way scenarios that use orchestrations, messaging, or a combination of both.</span></span>  

 <span data-ttu-id="120a5-106">為了協助您了解路線服務訊息中所使用的路線資訊，下列 XML 會顯示名為 TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml 先前的範例中所使用的範例路線的組態檔。</span><span class="sxs-lookup"><span data-stu-id="120a5-106">To help you understand how the Itinerary service uses the itinerary information in a message, the following XML shows the sample itinerary configuration file named TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml used in the earlier example.</span></span> <span data-ttu-id="120a5-107">此路線的第一個區段會指定服務引動過程的三個步驟。</span><span class="sxs-lookup"><span data-stu-id="120a5-107">The first section of this itinerary specifies three service invocation steps.</span></span>  

```xml  
<Itinerary xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" uuid="" beginTime="" completeTime="" state="Pending" isRequestResponse="false" servicecount="0" xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary">  
  <BizTalkSegment interchangeId="" epmRRCorrelationToken="" receiveInstanceId="" messageId="" xmlns="" />  
  <ServiceInstance name="Microsoft.Practices.ESB.Services.Transform" type="Orchestration" state="Pending" position="0" isRequestResponse="false" xmlns="" />  
  <Services xmlns="">  
    <Service uuid="92d3b293-e6d4-44a1-b27d-c42b48aec667" beginTime="" completeTime="" name="Microsoft.Practices.ESB.Services.Transform" type="Orchestration" state="Pending" isRequestResponse="false" position="0" serviceInstanceId="" />  
  </Services>  
  <Services xmlns="">  
    <Service uuid="774488bc-e5b9-4a4e-9ae7-d25cdf23fd1c" beginTime="" completeTime="" name="Microsoft.Practices.ESB.Services.Routing" type="Orchestration" state="Pending" isRequestResponse="false" position="1" serviceInstanceId="" />  
  </Services>  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="ProcessAndRespond" type="Orchestration" state="Pending" isRequestResponse="true" position="2" serviceInstanceId="" />  
  </Services>  
  ...  
```  

 <span data-ttu-id="120a5-108">下列服務引動過程中的步驟路線清單會包含允許尋找或解析為提供資訊中所定義的每個服務路線服務的解析程式 （由連接字串） 的詳細資料區段路線。</span><span class="sxs-lookup"><span data-stu-id="120a5-108">Following the list of service invocation steps in the itinerary is the section containing details of the resolvers (represented by connection strings) that allow the Itinerary service to locate or provide resolution information for each service defined in the itinerary.</span></span>  

```xml  
  ...  
<ResolverGroups xmlns="">  
    <Resolvers serviceId="Microsoft.Practices.ESB.Services.Transform0"><![CDATA[BRE:\\Policy=ResolveMap;Version=1.0;UseMsg=False;]]></Resolvers>  
    <Resolvers serviceId="Microsoft.Practices.ESB.Services.Routing1"><![CDATA[STATIC:\\TransportType=FILE;TransportLocation=C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\OUt\%MessageID%.xml;Action=;EndpointConfig=;JaxRpcResponse=False;MessageExchangePattern=;TargetNamespace=;TransformType=;]]><![CDATA[UDDI3:\\ServerUrl=http://localhost/uddi;SearchQualifiers=andAllKeys;CategorySearch=;BindingKey=uddi:esb:orderfileservicev3.1;]]></Resolvers>  
    <Resolvers serviceId="ProcessAndRespond2" />  
  </ResolverGroups>  
</Itinerary>  
```  

> [!NOTE]
>  <span data-ttu-id="120a5-109">每個實際的內容**\<解析程式\>** 元素未包含用來包裝在上述清單中的行泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="120a5-109">The actual content of each **\<Resolvers\>** element does not contain the white space characters used to wrap the lines in the preceding listing.</span></span>  

 <span data-ttu-id="120a5-110">路線的上述組態中定義的三個步驟如下：</span><span class="sxs-lookup"><span data-stu-id="120a5-110">The following are the three steps defined in the itinerary preceding configuration:</span></span>  

1. <span data-ttu-id="120a5-111">執行 Microsoft.Practices.ESB.Services.Transform 協調流程將訊息轉換與 ResolverMap 原則使用 BizTalk 商務規則引擎 (BRE)。</span><span class="sxs-lookup"><span data-stu-id="120a5-111">Execute the Microsoft.Practices.ESB.Services.Transform orchestration to transform the message with the ResolverMap policy using BizTalk Business Rules Engine (BRE).</span></span>  

2. <span data-ttu-id="120a5-112">執行轉換的訊息路由至多個位置使用路由 Microsoft.Practices.ESB.Services.Routing1 Microsoft.Practices.ESB.Services.Routing 協調流程。</span><span class="sxs-lookup"><span data-stu-id="120a5-112">Execute the Microsoft.Practices.ESB.Services.Routing orchestration to route the transformed message to multiple locations using the routing Microsoft.Practices.ESB.Services.Routing1.</span></span> <span data-ttu-id="120a5-113">**\<ResolverGroups\>** 一節包含**\<解析程式\>** 與這個識別項定義的連接字串的項目。</span><span class="sxs-lookup"><span data-stu-id="120a5-113">The **\<ResolverGroups\>** section contains a **\<Resolvers\>** element with this identifier, which defines the connection strings.</span></span>  

3. <span data-ttu-id="120a5-114">執行此範例提供的 ProcessAndRespond 協調流程。</span><span class="sxs-lookup"><span data-stu-id="120a5-114">Execute the ProcessAndRespond orchestration provided with this sample.</span></span> <span data-ttu-id="120a5-115">將做為回應此協調流程的實作傳回給路線測試用戶端要求訊息的複本。</span><span class="sxs-lookup"><span data-stu-id="120a5-115">The implementation of this orchestration sends as the response a copy of the request message back to the Itinerary Test Client.</span></span>  

   <span data-ttu-id="120a5-116">與每個服務完成後，服務前進的路線，並將升級為目前的服務執行個體，其狀態設定為使用路線中所定義的下一個服務**暫止**。</span><span class="sxs-lookup"><span data-stu-id="120a5-116">With the completion of each service, the service advances the itinerary and promotes the next service defined in the itinerary to be the current service instance, with its state set to **Pending**.</span></span>  

> [!NOTE]
>  <span data-ttu-id="120a5-117">路線入口範例會使用動態解析，將訊息傳送至輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="120a5-117">The Itinerary On-Ramp sample uses dynamic resolution to send messages to the output folder.</span></span> <span data-ttu-id="120a5-118">這是為什麼不是靜態傳送埠定義為此範例。</span><span class="sxs-lookup"><span data-stu-id="120a5-118">This is why there is no static send port defined for this sample.</span></span>  

 <span data-ttu-id="120a5-119">測試用戶端應用程式將訊息提交之後發生的事件的順序如下：</span><span class="sxs-lookup"><span data-stu-id="120a5-119">The following is the sequence of events that occur after the test client application submits the message:</span></span>  

- <span data-ttu-id="120a5-120">OnRamp.Itinerary 接收埠接收訊息。</span><span class="sxs-lookup"><span data-stu-id="120a5-120">The OnRamp.Itinerary receive port receives the message.</span></span>  

- <span data-ttu-id="120a5-121">ItineraryReceiveXml 管線從 SOAP 標頭擷取路線、 驗證和前置處理它、 以路線為訊息內容屬性寫入輸入的訊息，並將訊息發佈到 BizTalk Messagebox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="120a5-121">The ItineraryReceiveXml pipeline extracts the itinerary from the SOAP header, validates and pre-processes it, writes the itinerary as a message context property into the inbound message, and publishes the message to the BizTalk Message Box database.</span></span>  

- <span data-ttu-id="120a5-122">Microsoft.Practices.ESB.Services.Transform 服務協調流程的訂用帳戶就會觸發此協調流程的引動過程。</span><span class="sxs-lookup"><span data-stu-id="120a5-122">A subscription for the Microsoft.Practices.ESB.Services.Transform service orchestration triggers invocation of this orchestration.</span></span> <span data-ttu-id="120a5-123">協調流程會藉由將目前的訊息傳遞做為參數，如下列程式碼所示，先擷取目前的路線步驟。</span><span class="sxs-lookup"><span data-stu-id="120a5-123">The orchestration first retrieves the current itinerary step by passing the current message as a parameter, as shown in the following code.</span></span>  

  ```csharp  
  itineraryStep =   itinerary.Itinerary.GetItineraryStep(InboundMessage);  
  ```  

- <span data-ttu-id="120a5-124">**ItineraryStep**物件包含有關執行，目前的服務執行個體的所有資訊，以及任何與其相關聯的解析程式。</span><span class="sxs-lookup"><span data-stu-id="120a5-124">The **ItineraryStep** object contains all the information about the current service instance for execution, as well as any resolvers associated with it.</span></span>  

- <span data-ttu-id="120a5-125">**解析**物件擷取自**ItineraryStep**執行個體和 ESB 解析程式架構用來解析的完整名稱的轉換對應，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="120a5-125">The **Resolver** object is retrieved from the **ItineraryStep** instance and the ESB Resolver Framework is used to resolve the full name of the transformation map, as shown in the following code.</span></span>  

  ```csharp  
  resolverDictionary =   
     Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage,  
                                                          resolver);  

  // Set the transform type.  
  transformType = resolverDictionary.Item("Resolver.TransformType");  
  ```  

- <span data-ttu-id="120a5-126">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器架構可完成此作業藉由載入適當的解析程式快取 （在此範例中，BizTalk 商務規則引擎的解析程式），這會叫用 ResolverMap 原則，並於其中填入從**ResolverDictionary**物件。</span><span class="sxs-lookup"><span data-stu-id="120a5-126">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Framework accomplishes this by loading the appropriate resolver from the cache (in this example, the BizTalk Business Rules Engine resolver), which invokes the ResolverMap policy and populates the **ResolverDictionary** object.</span></span>  

- <span data-ttu-id="120a5-127">協調流程完成之後，程式碼會呼叫**AdvanceItinerary**方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="120a5-127">After the orchestration completes, the code calls the **AdvanceItinerary** method, as shown in the following code.</span></span>  

  ```csharp  
  // Call the Itinerary helper to advance to the next step.  
  itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
  ```  

- <span data-ttu-id="120a5-128">這會將目前的路線前移藉由更新其屬性，並升級下一個服務在行程中定義為下一個要執行的一個。</span><span class="sxs-lookup"><span data-stu-id="120a5-128">This advances the current itinerary by updating its properties and promoting the next service defined in the itinerary as the one to execute next.</span></span> <span data-ttu-id="120a5-129">方法會複製到輸出訊息，服務會發佈回 Messagebox 資料庫，透過直接繫結傳送埠的路線。</span><span class="sxs-lookup"><span data-stu-id="120a5-129">The method copies the itinerary into the outbound message, which the service publishes back into the Message Box database through a direct-bound send port.</span></span>  

- <span data-ttu-id="120a5-130">Microsoft.Practices.ESB.Services.Delivery 服務協調流程的訂用帳戶就會觸發此協調流程的引動過程。</span><span class="sxs-lookup"><span data-stu-id="120a5-130">A subscription for the Microsoft.Practices.ESB.Services.Delivery service orchestration triggers invocation of this orchestration.</span></span> <span data-ttu-id="120a5-131">此協調流程會依照類似的程序，第一個，取得目前的行程步驟。</span><span class="sxs-lookup"><span data-stu-id="120a5-131">This orchestration follows a similar process to the first one, obtaining the current Itinerary step.</span></span> <span data-ttu-id="120a5-132">不過，此協調流程逐一查看集合的解析程式所傳回**ItineraryStep**執行個體。</span><span class="sxs-lookup"><span data-stu-id="120a5-132">However, this orchestration iterates through a collection of resolvers returned by the **ItineraryStep** instance.</span></span> <span data-ttu-id="120a5-133">集合中各解決器，傳送協調流程會使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析程式和配接器架構，以解決傳輸位置，然後將它們升級為外寄訊息中的內容屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="120a5-133">For each resolver in the collection, the delivery orchestration uses the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Framework to resolve the transport locations and promote them as context properties within the outgoing message, as shown in the following code.</span></span>  

  ```csharp  
  // Move to retrieve the first resolver.  
  resolver = resolvers.Current;  

  // Pass the resolver configuration to the Resolver Manager   
  // for resolution.  
  resolverDictionary =  
     Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage,  
                                                          resolver);  

  // Set the transport properties.  
  transportLocation =   
     resolverDictionary.Item("Resolver.TransportLocation");  
  transportType =   
     resolverDictionary.Item("Resolver.TransportType");  

  // Call the Adapter Manager to set all necessary properties.  
  Microsoft.Practices.ESB.Adapter.AdapterMgr.SetEndpoint(  
                                  resolverDictionary, DeliveryMessage);  

  // Set the delivery port address and type.  
  DeliveryPort(Microsoft.XLANGs.BaseTypes.Address) = transportLocation;  
  DeliveryPort(Microsoft.XLANGs.BaseTypes.TransportType) = transportType;  
  ```  

- <span data-ttu-id="120a5-134">ProcessAndRespond 協調流程的訂用帳戶會觸發此協調流程的引動過程，因為訊息內容屬性定義的篩選條件運算式屬性的相符項目。</span><span class="sxs-lookup"><span data-stu-id="120a5-134">A subscription for the ProcessAndRespond orchestration triggers invocation of this orchestration because of a match of the message context properties defined for the filter expression properties.</span></span>  

  ```  
  (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName == :"ProcessAndRespond")   
  && Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
  && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType == "Orchestration")  
  ```  

- <span data-ttu-id="120a5-135">ProcessAndRespond 協調流程會前進的路線，並將原始要求訊息傳送回入口匝服務，路線測試用戶端應用程式，做為回應。</span><span class="sxs-lookup"><span data-stu-id="120a5-135">The ProcessAndRespond orchestration advances the itinerary and sends the original request message back to the on-ramp service to the Itinerary Test Client application as the response.</span></span>
