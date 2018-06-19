---
title: 建立自訂的路線傳訊服務 |Microsoft 文件
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
ms.openlocfilehash: 5f08168e69e26d56cb39fb5c05cc53c3cbb51202
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973732"
---
# <a name="creating-a-custom-itinerary-messaging-service"></a>建立自訂的路線訊息處理服務
屬於路線 framework[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援路線步驟使用實作類別的執行**IMessagingService**執行路線訊息服務的介面。 當您想要負責下列服務時，您可以實作自訂訊息處理服務：  
  
-   路線中設定的自訂訊息驗證  
  
-   在路線中設定的自訂訊息轉換  
  
-   自訂訊息處理  
  
 在這些情況下，您實作自訂路線服務做為攔截器，並由發送器管線元件呼叫。  
  
 自訂訊息型路線服務或訊息的服務，所有實作**IMessagingService**介面。 此介面會公開**名稱**和**SupportsDisassemble**屬性和**Execute**和**ShouldAdvanceStep**方法。  
  
 **名稱**屬性是服務的名稱，因為它會出現在路線。 它必須符合 Esb.config 檔案中的計劃的服務組態中設定的名稱。  
  
 **SupportsDisassemble**屬性會指出是否自訂的訊息處理服務，您要建立支援反組譯及多個的解析程式執行。  
  
 **ShouldAdvanceStep**方法接受目前的路線步驟和目前的訊息，並傳回布林值，指出發送器是否應該在服務執行之後前進的路線。 在大多數情況下，此方法應傳回**true**。  
  
 **Execute**方法是重要性最高的訊息處理服務，並包含將在執行階段執行的邏輯。 它會在管線內容、 訊息、 解析程式的字串，以及目前路線的步驟。它會傳回更新的訊息。  
  
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
  
 **若要實作自訂路線服務的訊息**  
  
1.  建立組件的類別衍生自**IMessagingService;** 中**Execute**方法，包括可修改訊息或訊息內容 （如果有的話） 所需的所有邏輯。  
  
2.  新增項目中的**itineraryServices** Esb.config 檔案加入您的服務區段 **\<itineraryService\>** 項目以做為 GUID**識別碼**屬性，做為服務的名稱**名稱**屬性，做為類別的完整的名稱**類型**屬性**傳訊**為**範圍**屬性，並允許的階段 (例如， **OnRampReceive**， **OnRampSend**， **OffRampSend**， **OffRampReceive**， **AllSend**， **AllReceive**，或**所有**) 做為**階段**屬性。  
  
3.  在全域組件快取中註冊新的組件。