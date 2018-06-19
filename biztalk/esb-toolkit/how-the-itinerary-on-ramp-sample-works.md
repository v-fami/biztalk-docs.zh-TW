---
title: 路線上手範例的運作方式 |Microsoft 文件
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
ms.openlocfilehash: b73b4379944db548a30898403239ffcf9704791a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974892"
---
# <a name="how-the-itinerary-on-ramp-sample-works"></a>路線上手範例的運作方式
範例應用程式建置一組 SOAP 標頭包含您在用戶端應用程式視窗中，使用控制項建立路線路線測試用戶端會從磁碟載入指定的訊息檔案、 路線標頭附加至訊息，並請將它提交至 ESB 透過路線上手進行處理。 如果路線，都產生回應，應用程式會收集回應，並顯示在應用程式視窗。  
  
 您可以選擇從數個範例路線的組態檔來查看單向和雙向使用協調流程、 訊息，或兩者的組合的案例。  
  
 為了協助您了解行程服務在訊息中所使用的計劃資訊，下列 XML 會顯示名為 TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml 前面範例中使用的範例路線的組態檔。 這個路線的第一個區段會指定服務引動過程的三個步驟。  
  
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
  
 下列服務引動過程中的步驟路線清單是包含允許以尋找或解析為提供資訊中所定義的每個服務路線服務的解析程式 （連接字串來表示） 的詳細資料區段路線。  
  
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
>  每個實際內容**\<解析程式\>** 項目不包含用來包裝在上述清單中的行泛空白字元。  
  
 以下是路線上述組態中定義的三個步驟：  
  
1.  執行 Microsoft.Practices.ESB.Services.Transform 協調流程將訊息轉換與 ResolverMap 原則使用 BizTalk 商務規則引擎 (BRE)。  
  
2.  執行將已轉換的訊息路由至多個位置使用路由 Microsoft.Practices.ESB.Services.Routing1 Microsoft.Practices.ESB.Services.Routing 協調流程。  **\<ResolverGroups\>** 區段包含**\<解析程式\>** 定義的連接字串，此識別碼的項目。  
  
3.  執行此範例提供的 ProcessAndRespond 協調流程。 傳送為回應此協調流程的實作回到路線測試用戶端要求訊息的複本。  
  
 與每個服務完成之後，服務前進的路線，並會升級為目前的服務執行個體，其狀態設定為與行程中定義的下一個服務**暫止**。  
  
> [!NOTE]
>  行程上手範例會使用動態解析傳送訊息到輸出資料夾。 這是為什麼沒有靜態傳送埠定義此範例。  
  
 測試用戶端應用程式將訊息提交之後發生的事件的順序如下：  
  
-   OnRamp.Itinerary 接收埠接收訊息。  
  
-   ItineraryReceiveXml 管線從 SOAP 標頭擷取路線、 驗證和預先處理、 路線做為訊息內容屬性寫入輸入的訊息，並將訊息發佈到 BizTalk Messagebox 資料庫。  
  
-   Microsoft.Practices.ESB.Services.Transform 服務協調流程的訂閱會觸發此協調流程的引動過程。 協調流程會將目前的訊息傳遞做為參數，如下列程式碼所示，先擷取目前路線的步驟。  
  
    ```csharp  
    itineraryStep =   itinerary.Itinerary.GetItineraryStep(InboundMessage);  
    ```  
  
-   **ItineraryStep**物件包含關於執行、 目前的服務執行個體的所有資訊，以及任何與其相關聯的解析程式。  
  
-   **解析程式**從擷取物件**ItineraryStep**執行個體和 ESB 解析程式架構用來解析的完整名稱的轉換對應，如下列程式碼所示。  
  
    ```csharp  
    resolverDictionary =   
       Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage,  
                                                            resolver);  
  
    // Set the transform type.  
    transformType = resolverDictionary.Item("Resolver.TransformType");  
    ```  
  
-   [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器架構可完成此作業藉由從快取 （在此範例中，「 BizTalk 商務規則引擎解析程式 」），會叫用 ResolverMap 原則，並於其中填入載入適當的解析程式**ResolverDictionary**物件。  
  
-   協調流程完成之後，程式碼會呼叫**AdvanceItinerary**方法，如下列程式碼所示。  
  
    ```csharp  
    // Call the Itinerary helper to advance to the next step.  
    itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
    ```  
  
-   這是由更新其屬性，以及升級下一個服務在路線中定義為下一個要執行的一個前移目前的路線。 方法會將路線複製到傳出的訊息發佈回 Messagebox 資料庫，透過直接繫結傳送埠的服務。  
  
-   Microsoft.Practices.ESB.Services.Delivery 服務協調流程的訂閱會觸發此協調流程的引動過程。 此協調流程與第一個，取得目前行程步驟遵循類似程序。 不過，此協調流程逐一查看集合的解析程式所傳回**ItineraryStep**執行個體。 集合中各解決器，傳送協調流程會使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器架構來解析傳輸位置，並將它們升級為外寄訊息中的內容屬性，如下列程式碼所示。  
  
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
  
-   ProcessAndRespond 協調流程的訂閱會觸發此協調流程的引動過程，因為篩選運算式屬性所定義之訊息內容屬性的相符項目。  
  
    ```  
    (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName == :"ProcessAndRespond")   
    && Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType == "Orchestration")  
    ```  
  
-   ProcessAndRespond 協調流程前進的路線，並將原始要求訊息傳送回上手路線測試用戶端應用程式，以回應服務。