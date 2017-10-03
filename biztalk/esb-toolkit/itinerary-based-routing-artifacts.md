---
title: "行程為基礎的路由成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cff38ab7-5a16-42cc-9065-075e9db7acd3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ca01cc5313c8ca64418f65cec3fdf18fdbc85df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="itinerary-based-routing-artifacts"></a>行程為基礎的路由成品
行程型路由的功能[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含一組的索引鍵在多個組件中定義的成品。 下表列出這些成品可以協助開發人員使用時與擴充行程為基礎的路由實作與其他 ESB 路線服務實作的類別目錄。  
  
## <a name="esb-itinerary-classes"></a>ESB 路線類別  
 下表列出的組件和 ESB 中所包含的成品。計劃的專案。 包含組件的名稱是**Microsoft.Practices.ESB.Itinerary.dll**。  
  
|索引鍵的成品|Description|  
|------------------|-----------------|  
|**MessageHelper**|包含所有私用函式所呼叫的其他專案成品。|  
|**IItineraryStep**|在公用類別，從傳回**GetItineraryStep**方法。|  
|**ResolverCollection**|實作與服務相關聯的所有解析程式的集合。 這個類別由**IItineraryStep**介面，並會填入**GetItineraryStep**方法。|  
|**IMessagingService**|定義訊息為基礎的路線服務所實作的介面。|  
|**IMessagingService**|建立 factory **IMessagingService** Esb.config 中設定的名稱為基礎的物件。|  
  
## <a name="esb-itinerary-messaging-services"></a>ESB 路線訊息服務  
 下表列出中定義的類別**Microsoft.Practices.ESB.Itinerary.Services.dll**中的組件**Microsoft.Practices.ESB.Itinerary.Services**命名空間。  
  
|索引鍵的成品|Description|  
|------------------|-----------------|  
|**路由**|ESB 路線訊息路由的實作： 使用 Esb.config 檔案中，ESB 發送器解譯元件叫用。|  
|**轉換**|實作訊息轉換服務 ESB 行程： ESB 發送器解譯元件使用 Esb.config 檔案所叫用。|  
  
 下表列出中包含的成品**Microsoft.Practices.ESB.Itinerary.Services.Broker.dll**組件。  
  
|索引鍵的成品|Description|  
|------------------|-----------------|  
|**MessagingBroker**|傳訊服務進行路由訊息內容的 ESB 行程的實作： 使用 Esb.config 檔案中，ESB 發送器解譯元件叫用。|  
  
 這些服務也會定義 BizTalk ESB Toolkit 組態檔中，Esb.config。  
  
## <a name="esb-itinerary-orchestration-services"></a>ESB 路線的協調流程服務  
 下表列出中包含的成品**Microsoft.Practices.ESB.Agents.dll**組件。  
  
|索引鍵的成品|Description|  
|------------------|-----------------|  
|Delivery.odx|路由協調流程路線服務的服務名稱所識別的範例**Microsoft.Practices.ESB.Services.Routing**。|  
|Transform.odx|範例轉換協調流程路線服務的服務名稱識別**Microsoft.Practices.ESB.Services.Transform**。|  
  
## <a name="esb-itinerary-pipeline-components"></a>ESB 路線的管線元件  
 下表列出的組件和成品包含在**Microsoft.Practices.ESB.Itinerary.PipelineComponents.dll**組件。  
  
|索引鍵的成品|Description|  
|------------------|-----------------|  
|**路線**|主要路線處理管線元件會處理及驗證內送訊息的路線。|  
|**ItineraryCache**|計劃快取管線元件，以用於請求-回應傳送埠。|  
|**ItinerarySelector**|解決伺服器端行程中泛型上坡道提升路線的選取器管線元件。|  
  
## <a name="esb-itinerary-pipelines"></a>ESB 路線管線  
 下表列出的組件和成品包含在**Microsoft.Practices.ESB.Itinerary.Pipelines.dll**組件。  
  
|索引鍵的成品|Description|  
|------------------|-----------------|  
|ItineraryReceive|用於路線 Web 服務上手路線的管線。 當做接收管線的接收位置，並包含下列管線元件：<br /><br /> ESB 行程，XML 解譯器中，ESB 發送器|  
|ItineraryReceivePassthrough||  
|ItineraryReceiveXml|用於路線 Web 服務上手路線的管線。 當做接收管線的接收位置內送訊息路由至多個端點，並包含下列管線元件：<br /><br /> ESB 行程，ESB 發送器反組譯工具|  
|ItinerarySend|用於路線匝道路線的管線。 做為傳送管線的傳送埠，並且包含下列管線元件：<br /><br /> ESB 發送器，XML 組合器中，ESB 路線快取|  
|ItinerarySendPassthrough|用於路線匝道路線的管線。 做為傳送管線的傳送埠，並且包含下列管線元件：<br /><br /> ESB 發送器，ESB 路線快取|  
|ItinerarySendReceive|用於路線匝道路線的管線。 當做接收管線的請求-回應傳送埠，並包含下列管線元件：<br /><br /> ESB 路線快取中，XML 解譯器中，ESB 發送器|  
|ItineraryForwarderSendReceive|用於路線匝道路線的管線。 當做接收管線的傳送埠，並包含下列管線元件：<br /><br /> ESB 路線快取中，XML 解譯器中，ESB 發送器，轉寄站|  
|ItineraryForwarderSendReceiveXml|用於路線 Web 服務上手路線的管線。 當做接收管線的傳送埠，並包含下列管線元件：<br /><br /> ESB 路線快取中，ESB 發送器反組譯，轉寄站|  
|ItinerarySelectReceive|用於路線 Web 服務上手路線的管線。 當做接收管線的接收位置，並包含下列管線元件：<br /><br /> ESB 路線的選取器，XML 解譯器中，ESB 發送器|  
|ItinerarySelectReceivePassthrough|用於路線 Web 服務上手路線的管線。 當做接收管線的接收位置，並包含下列管線元件：<br /><br /> ESB 路線選取器，ESB 發送器|  
|ItinerarySelectReceiveXml|用於路線 Web 服務上手路線的管線。 當做接收管線的接收位置，並包含下列管線元件：<br /><br /> XML 解譯器，ESB 路線的選取器，ESB 發送器|  
|ItinerarySelectSendReceive|用於路線匝道路線的管線。 當做接收管線的傳送埠，並包含下列管線元件：<br /><br /> ESB 路線快取中，ESB 路線的選取器，XML 解譯器，ESB 發送器|  
  
## <a name="esb-itinerary-schemas"></a>ESB 路線結構描述  
 下表列出的組件和成品包含在**Microsoft.Practices.ESB.Itinerary.Schemas.dll**組件。  
  
|索引鍵的成品|Description|  
|------------------|-----------------|  
|Itinerary.xsd|定義 ESB 路線 SOAP 標頭中 Windows Communication Foundation WCF 型和 SOAP 型 Web 服務上-坡道提升使用。|  
|ItineraryDescription.xsd|此 scehma 表示路線的參考資料，而且應該用於提交訊息至 WCF 型上-坡道提升。|  
|系統 Properties.xsd|定義 ESB 行程相關 BizTalk 內容屬性。|