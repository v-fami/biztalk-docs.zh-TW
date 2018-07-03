---
title: 執行路線服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d86d228-da28-494f-85c7-4225b54f9b98
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a85e5c134e9fbbd2d1b6880fdb9e5cd866bc512
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024380"
---
# <a name="executing-an-itinerary-service"></a>執行路線服務
ESB 路線可以包含任何路線的服務，可能是實作為協調流程或傳訊執行下列工作：  
  
- 它可以接收包含路線的訊息。  
  
- 它可以擷取目前的路線步驟。  
  
- 它可以處理服務。  
  
- 它可以藉由呼叫在傳出訊息上前進的路線**提前**方法。  
  
- 它可以將已處理的訊息發行到 Microsoft BizTalk Message Box 資料庫。  
  
  比方說，協調流程可以接收訊息，其中包含實作 「 啟動的接收 」 圖形中，所定義的篩選，如 圖 1 所示的路線[使用協調流程作為路線服務訂閱者](../esb-toolkit/using-an-orchestration-as-an-itinerary-service-subscriber.md)。 不過，訊息會稍有不同： 管線元件呼叫**GetItineraryStep**方法，以判斷內送訊息中是否存在路線。 它也會檢查要檢查是否就應該處理的訊息屬性。  
  
  ![協調流程](../esb-toolkit/media/ch4-orchestration.jpg "第 4 章第協調流程")  
  
  **圖 1**  
  
  **要參與路線身為訂閱者的協調流程的範例篩選條件運算式**  
  
  服務會取得訊息之後，必須呼叫**GetItineraryStep**方法，以傳回的執行個體**ItineraryStep**類別。 下列清單將示範如何呼叫路線 API 的方法，以及在從協調流程和自訂管線元件。 下列程式碼執行**GetItineraryStep**從協調流程運算式 」 圖形的方法。  
  
```  
  
//XLANGs  
// Retrieve the current itinerary step.  
itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
```  
  
 下列程式碼示範如何從自訂管線元件執行訊息的服務方法。  
  
```csharp  
// Execute messaging step.  
public IBaseMessage Execute(IPipelineContext context, IBaseMessage msg, string resolverString, IItineraryStep step)  
{  
    if (null != step  
    && step.ServiceType == "Messaging"  
    && step.ServiceName == "SomeService")  
    {  
        // If the service name matches the required name, process the message here.  
    }  
    else  
    {  
        // Do not process the message.  
        return pInMsg;  
    }  
}  
```  
  
 執行個體**IItineraryStep**類別包含目前的服務，包括目前的服務執行環境的環境屬性的所有中繼資料。 兩個是很好的範例**ServiceInstanceID**和目前**MessageDirection**管線元件屬性。  
  
 服務會呼叫後**GetItineraryStep**方法，它可以擷取所有相關聯的解析程式。 **ResolverCollection**屬性**ItineraryStep**類別傳回的解析程式服務可以透過，如下列範例所示來列舉集合。  
  
```csharp  
Microsoft.Practices.ESB.Itinerary.ResolverCollection resolvers;  
resolvers = step.ItineraryStep.ResolverCollection;  
```  
  
 在每個項目**ResolverCollection**代表符合其中一個型別解析器和配接器架構所支援的解析程式連接字串。 例如，集合中的項目看起來應該像下列的清單。  
  
```idl  
BRE:\\policy=GetCanadaPurchaseEndPoint;version=;useMsg=;  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=OrderFileServiceWBindings;  
STATIC:\\TransportLocation=http://localhost/ESB.CanadianServices/SubmitPOService.asmx;  
TargetNamespace=http://globalbank.esb.dynamicresolution.com/canadianservices/;  
XPATH:\\TransportType=; TransportLocation=/*[local-name()='OrderDoc' and namespace-  
uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*  
[local-name()='ID' and namespace-  
uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];  
TargetNamespace=/*[local-name()='OrderDoc' and namespace-  
uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*  
[local-name()='customerName' and namespace-  
uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];  
```  
  
 在解析程式和配接器提供者架構的解析程式管理員可以解析端點，並設定訊息的端點屬性。 如需有關如何發生這種情況的詳細資訊，請參閱 <<c0> [ 使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)。  
  
 在服務完成處理訊息之後，它必須在傳出訊息上前進的路線，並將訊息發佈回 Messagebox 資料庫。 下列範例會顯示協調流程運算式 」 圖形的程序。  
  
```xml  
  
//XLANGs  
// Copy the context to the outbound message.  
OutboundMessage = InboundMessage;  
OutboundMessage(*) = InboundMessage(*);  
  
// Call the method of the ItinerarySerializableWrapper to advance to the next step.  
itinerary.Itinerary.Advance(OutboundMessage, step.ItineraryStep);  
```  
  
 下列範例示範如何表示[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心引擎應該讓前進的路線的自訂管線元件。  
  
```csharp  
// Advance Itinerary  
// <summary>  
// Signals that the step should be advanced immediately following execution of the service.  
// </summary>  
// <param name="step">Current step</param>  
// <param name="msg">Current message</param>  
// <returns>True to advance the itinerary.</returns>  
public bool ShouldAdvanceStep(IItineraryStep step, IBaseMessage msg)  
{  
    return true;  
}  
```