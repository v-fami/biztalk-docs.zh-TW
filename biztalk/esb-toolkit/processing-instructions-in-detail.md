---
title: 詳細處理指示 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed5d92fb-d53b-49a2-b2c7-8558708d6554
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d867737599369ad8ff07780080b16f5ce0f6f2fe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005575"
---
# <a name="processing-instructions-in-detail"></a>在 詳細資料的處理指示
本主題描述的格式和系統 Properties.xsd 屬性結構描述，定義數個路線處理所需的內容屬性的結構。 這些屬性會升級，當訊息接收和處理透過 BizTalk Server 管線;因為它們是升級的屬性時，才能夠存取 BizTalk Server 元件。 系統 Properties.xsd 屬性結構描述中定義下列屬性：  
  
- **ItineraryHeader。** 此屬性包含所有的路線資訊和要叫用透過一系列路線步驟路線服務的清單。 路線 API 會在內部使用這個屬性。  
  
- **ServiceName。** 此屬性包含要處理的目前路線服務的名稱。  
  
- **ServiceState。** 此屬性包含目前的路線服務的狀態：**暫止**，**完成**，或**Active**。 所有服務都訂閱的路線的步驟，其中包含**ServiceState**的值**暫止**。  
  
- **ServiceType。** 這個屬性會定義路線步驟的類型 (**Messaging**或是**協調流程**)。  
  
- **IsRequestResponse。** 這個屬性會定義訊息類型 (單向或要求-回應)。  
  
  路線服務中其中一種方式，根據的值執行路線的步驟**ServiceType**屬性：  
  
- 路線的管線元件會執行所有的路線步驟，與**ServiceType**屬性**Messaging**。 開發人員可以擴充使用自訂的管線和路線 API，此程序。  
  
- 當**ServiceType**屬性是**協調流程**，協調流程，由訂用帳戶，路線的內容屬性，以啟動執行路線的步驟。  
  
  路線服務處理路線的步驟時，服務會負責前進的路線，並使用發行的進一步處理的新路線內容與將訊息分派-訂閱的 BizTalk Server 的功能。 路線服務的訊息內容中路線的完整控制，而且可以前進到其內部邏輯和訊息內容為基礎的適當步驟。  
  
  路線的處理機制會支援單一行程內的傳訊與協調流程路線步驟的組合。 開發人員也可以定義自訂路線服務，並設定自訂路線的步驟。  
  
  如需路線的詳細資訊，請參閱[安裝和執行路線入口範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。  
  
  如需有關自訂路線服務和自訂的路線步驟的詳細資訊，請參閱[建立自訂路線服務](../esb-toolkit/creating-a-custom-itinerary-service.md)。