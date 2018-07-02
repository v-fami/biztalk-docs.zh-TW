---
title: 建立自訂路線傳訊服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2de44c21-68ca-4cf1-a117-bcb35af1b4a9
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecb6c6976493e05c9df747de4a358df7fff7809f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983919"
---
# <a name="creating-a-custom-itinerary-messaging-service"></a>建立自訂路線傳訊服務
路線的架構，屬於[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援的路線的步驟，使用實作的類別執行**IMessagingService**執行路線傳訊服務的介面。 當您想要負責下列服務時，您可以實作自訂傳訊服務：  
  
- 路線中設定的自訂訊息驗證  
  
- 路線中設定的自訂訊息轉換  
  
- 自訂訊息處理  
  
  在這些情況下，您實作自訂路線服務做為攔截器，並由 「 發送器 」 管線元件呼叫。  
  
  自訂訊息路線服務或傳訊服務，所有實作**IMessagingService**介面。 此介面會公開**名稱**並**SupportsDisassemble**屬性和**Execute**並**ShouldAdvanceStep**方法。  
  
  **名稱**屬性是它會顯示在路線服務的名稱。 它必須符合路線服務組態中的 Esb.config 檔案中設定的名稱。  
  
  **SupportsDisassemble**屬性會指出是否自訂的傳訊服務，您要建立支援反組譯及多個的解析程式執行。  
  
  **ShouldAdvanceStep**方法會接受目前的路線步驟中和目前的訊息，並傳回布林值，指出服務執行之後，發送器是否應該前進的路線。 在幾乎所有的情況下，這個方法會傳回 **，則為 true**。  
  
  **Execute**方法是將重要性最高的傳訊服務，並包含將於執行階段上執行的邏輯。 它會採用管線內容、 訊息、 解析程式的字串，以及目前的路線步驟;它會傳回更新的訊息。  
  
  參考實作**Execute** ESB RoutingService.cs 檔案中找到方法。Itinerary.Services 專案，如下列程式碼所示。  
  
```csharp  
public IBaseMessage ExecuteRoute(IPipelineContext context, IBaseMessage msg, string resolverString)  
        {  
            if (context == null)  
                throw new ArgumentNullException("context");  
            if (msg == null)  
                throw new ArgumentNullException("msg");  
            if (string.IsNullOrEmpty(resolverString))  
                throw new ArgumentException(Properties.Resources.ArgumentStringRequired, "resolverString");  
            try  
            {  
                ResolverInfo info = ResolverMgr.GetResolverInfo(ResolutionType.Endpoint, resolverString);  
                if (!info.Success)  
                    throw new RoutingException(Properties.Resources.ResolverStringInvalid, resolverString);  
  
                // Resolve configuration for routing.  
                Dictionary<string, string> resolverDictionary = ResolverMgr.Resolve(info, msg, context);  
  
                if (string.IsNullOrEmpty(resolverDictionary["Resolver.TransportLocation"]))  
                    throw new RoutingException(Properties.Resources.TransportLocationNotResolved, resolverString);  
  
                AdapterMgr.SetEndpoint(resolverDictionary, msg.Context);  
  
                return msg;  
            }  
            catch (System.Exception ex)  
            {  
                EventLogger.Write(MethodInfo.GetCurrentMethod(), ex);  
                throw;  
            }        
        }  
```  
  
 **若要實作自訂路線傳訊服務**  
  
1.  建立的組件的類別，衍生自**IMessagingService;** 中**Execute**方法，包含要修改訊息或訊息內容 （如果有的話），您所需的所有邏輯。  
  
2.  中新增項目**itineraryServices** Esb.config 檔案，為您的服務加上一節**\<itineraryService\>** GUID 做為項目**識別碼**屬性，做為服務名稱**名稱**屬性，做為類別的完整的名稱**類型**屬性， **Messaging**作為**範圍**屬性，而允許的階段 (例如**OnRampReceive**， **OnRampSend**， **OffRampSend**， **OffRampReceive**， **AllSend**， **AllReceive**，或**所有**) 做為**階段**屬性。  
  
3.  在全域組件快取中註冊新的組件。