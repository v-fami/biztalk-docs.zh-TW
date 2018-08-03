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
# <a name="how-the-itinerary-on-ramp-sample-works"></a>路線入口範例運作方式
範例應用程式建置一組包含您在用戶端應用程式視窗中，使用控制項建立路線的 SOAP 標頭的路線測試用戶端會從磁碟載入指定的訊息檔案、 路線的標頭附加至訊息，並請將它提交至路線入口匝處理透過 ESB。 如果路線，都產生回應，應用程式會收集回應，並顯示在應用程式視窗。  

 若要查看單向和雙向使用協調流程、 訊息、 或兩者的組合的案例，您可以選擇從數個範例路線的組態檔。  

 為了協助您了解路線服務訊息中所使用的路線資訊，下列 XML 會顯示名為 TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml 先前的範例中所使用的範例路線的組態檔。 此路線的第一個區段會指定服務引動過程的三個步驟。  

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

 下列服務引動過程中的步驟路線清單會包含允許尋找或解析為提供資訊中所定義的每個服務路線服務的解析程式 （由連接字串） 的詳細資料區段路線。  

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
>  每個實際的內容**\<解析程式\>** 元素未包含用來包裝在上述清單中的行泛空白字元。  

 路線的上述組態中定義的三個步驟如下：  

1. 執行 Microsoft.Practices.ESB.Services.Transform 協調流程將訊息轉換與 ResolverMap 原則使用 BizTalk 商務規則引擎 (BRE)。  

2. 執行轉換的訊息路由至多個位置使用路由 Microsoft.Practices.ESB.Services.Routing1 Microsoft.Practices.ESB.Services.Routing 協調流程。 **\<ResolverGroups\>** 一節包含**\<解析程式\>** 與這個識別項定義的連接字串的項目。  

3. 執行此範例提供的 ProcessAndRespond 協調流程。 將做為回應此協調流程的實作傳回給路線測試用戶端要求訊息的複本。  

   與每個服務完成後，服務前進的路線，並將升級為目前的服務執行個體，其狀態設定為使用路線中所定義的下一個服務**暫止**。  

> [!NOTE]
>  路線入口範例會使用動態解析，將訊息傳送至輸出資料夾。 這是為什麼不是靜態傳送埠定義為此範例。  

 測試用戶端應用程式將訊息提交之後發生的事件的順序如下：  

- OnRamp.Itinerary 接收埠接收訊息。  

- ItineraryReceiveXml 管線從 SOAP 標頭擷取路線、 驗證和前置處理它、 以路線為訊息內容屬性寫入輸入的訊息，並將訊息發佈到 BizTalk Messagebox 資料庫。  

- Microsoft.Practices.ESB.Services.Transform 服務協調流程的訂用帳戶就會觸發此協調流程的引動過程。 協調流程會藉由將目前的訊息傳遞做為參數，如下列程式碼所示，先擷取目前的路線步驟。  

  ```csharp  
  itineraryStep =   itinerary.Itinerary.GetItineraryStep(InboundMessage);  
  ```  

- **ItineraryStep**物件包含有關執行，目前的服務執行個體的所有資訊，以及任何與其相關聯的解析程式。  

- **解析**物件擷取自**ItineraryStep**執行個體和 ESB 解析程式架構用來解析的完整名稱的轉換對應，如下列程式碼所示。  

  ```csharp  
  resolverDictionary =   
     Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage,  
                                                          resolver);  

  // Set the transform type.  
  transformType = resolverDictionary.Item("Resolver.TransformType");  
  ```  

- [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器架構可完成此作業藉由載入適當的解析程式快取 （在此範例中，BizTalk 商務規則引擎的解析程式），這會叫用 ResolverMap 原則，並於其中填入從**ResolverDictionary**物件。  

- 協調流程完成之後，程式碼會呼叫**AdvanceItinerary**方法，如下列程式碼所示。  

  ```csharp  
  // Call the Itinerary helper to advance to the next step.  
  itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
  ```  

- 這會將目前的路線前移藉由更新其屬性，並升級下一個服務在行程中定義為下一個要執行的一個。 方法會複製到輸出訊息，服務會發佈回 Messagebox 資料庫，透過直接繫結傳送埠的路線。  

- Microsoft.Practices.ESB.Services.Delivery 服務協調流程的訂用帳戶就會觸發此協調流程的引動過程。 此協調流程會依照類似的程序，第一個，取得目前的行程步驟。 不過，此協調流程逐一查看集合的解析程式所傳回**ItineraryStep**執行個體。 集合中各解決器，傳送協調流程會使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析程式和配接器架構，以解決傳輸位置，然後將它們升級為外寄訊息中的內容屬性，如下列程式碼所示。  

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

- ProcessAndRespond 協調流程的訂用帳戶會觸發此協調流程的引動過程，因為訊息內容屬性定義的篩選條件運算式屬性的相符項目。  

  ```  
  (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName == :"ProcessAndRespond")   
  && Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
  && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType == "Orchestration")  
  ```  

- ProcessAndRespond 協調流程會前進的路線，並將原始要求訊息傳送回入口匝服務，路線測試用戶端應用程式，做為回應。
