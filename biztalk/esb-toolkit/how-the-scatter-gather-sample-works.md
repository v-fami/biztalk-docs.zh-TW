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
# <a name="how-the-scatter-gather-sample-works"></a>分散-集中範例運作方式
範例應用程式建置一組包含從分散-集中路線檔案載入路線的 SOAP 標頭、 從磁碟載入指定的訊息檔案、 路線的標頭附加至訊息，並將它提交至透過匝道的 ESB處理程序。 如果路線，都產生回應，應用程式會收集這，並顯示在應用程式視窗中。  
  
 為了協助您了解路線服務訊息中所使用的路線資訊，下列清單會顯示名為 ScatterGatherItinerary.xml 範例路線的組態檔。 此路線的第一個區段會指定兩個服務引動過程步驟。  
  
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
  
 下列服務引動過程中的步驟路線清單會包含解析程式和連接字串可讓下列 XML 所示，找出在路線，定義每個服務路線服務的詳細資料區段。  
  
```xml  
<ResolverGroups xmlns="">  
 <Resolvers serviceId="ScatterGather0"><![CDATA[BRE:\\policy=ResolveEndPointScatterGather;version=;useMsg=;]]><![CDATA[UDDI3:\\serverUrl=http://localhost/uddi;bindingKey=uddi:esb:purchaseordersubmitorderservicebinding;credentialType=Ntlm]]></Resolvers>  
<Resolvers serviceId="DynamicTest1"><![CDATA[UDDI3:\\serverUrl=http://localhost/uddi;bindingKey=uddi:esb:orderfileservicebinding;credentialType=Ntlm]]>  
</Resolvers>  
  </ResolverGroups>  
```  
  
 在此範例中，應用程式執行 SubmitPOService Web 服務兩次因為兩個解析程式的連接字串解析為此服務的位置時，才 (http://localhost/ESB.CanadianServices/SubmitPOService.asmx)。 訊息內容會指定訊息代理程式協調流程路線的第一個服務，若要啟用，定義在範例中，如下所示。  
  
```csharp  
(Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName == "ScatterGather")  
     && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState ==   
    "Pending") && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType   
    == "Orchestration")  
```  
  
 訊息代理程式協調流程會分析其路線步驟的設定，並擷取與路線的步驟相關聯的解析程式的集合。 針對每個這些解析程式中，協調流程會使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析程式和配接器架構，來解決服務端點。 訊息代理程式協調流程接著會啟動 n 個 ServiceDispatcher 協調流程以非同步方式 （其中 n 是路線 ScatterGather 服務相關聯的解析程式數目） 來分派要求訊息，並指定下列參數：  
  
- **TransportLocation**。 解析程式會填入此參數。  
  
- **TransportType**。 解析程式會填入此參數。  
  
- **ResolverDictionary**。 這個參數會包含解析程式事實填入具體的解析程式執行個體的集合。  
  
- **InboundMessage**。 這個參數會包含原始訊息包含路線。  
  
- **ServiceResponsePort**。 這個參數是自我相互關聯會接收來自 ServiceDispatcher 協調流程的執行個體的回應的回應連接埠的名稱。  
  
  ServiceDispatcher 協調流程的每個執行個體使用的 ResolveMapScatterGather 原則來要求和回應訊息，根據 Microsoft BizTalk 對應類型解析**TransportType**和**TransportLocation**屬性。 協調流程執行個體使用的已解析的對應，將輸入的訊息轉換成 Web 服務呼叫的要求訊息。  
  
  ESB 配接器管理員設定在要求訊息的 BizTalk 則請求-回應連接埠轉送名為 ServiceRequestPort 輸出傳輸內容屬性。  
  
  從服務收到回應訊息，當 ServiceDispatcher 協調流程會使用轉換成標準格式輸入的回應訊息解析的對應資訊。 然後 ServiceResponse 信封中包裝的已修改的回應，並將它轉送至訊息代理程式協調流程透過自我相互關聯的連接埠。 訊息代理程式協調流程會彙總所有的連入回應，並準備使用 GlobalBank.ESB.ScatterGather.Processes.AggregatingPipeline，最後的回應訊息，如下列程式碼所示。  
  
```csharp  
AggregatedResponse.Body = null;  
AggregatedResponse(*) = InboundMessage(*);  
Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteSendPipeline(  
    typeof(GlobalBank.ESB.ScatterGather.Processes.AggregatingPipeline),  
    messageAggregator,AggregatedResponse);  
```  
  
 此程式碼會預先定義的信封中包裝整個批次的回應。 訊息代理程式協調流程接著前進到路線**DynamicTest**路線的步驟中，如下列程式碼所示。  
  
```csharp  
// Copy the context and advance the itinerary.  
OutboundMessage = AggregatedResponse.Body;  
OutboundMessage(*) = AggregatedResponse(*);  
// Advance the Itinerary to the next step.  
itinerary.Itinerary.Advance(OutboundMessage, itineraryStep);  
```  
  
 因為名稱為服務型別屬性**DynamicTest**設為**Messaging**，則**ItineraryHelper**類別將解析程式的屬性升級至的內容名為訊息**OutboundMessage**。 訊息代理程式協調流程會將此訊息傳送至 BizTalk 直接繫結連接埠。 BizTalk 然後會將訊息轉送至動態傳送埠所代表**ServiceName**訂用帳戶，也就是**DynamicTest**。 此傳送埠將序列化至 \Source\Samples\DynamicResolution\Test\Filedrop\Out 資料夾最後彙總的回應。