---
title: "詳細資料中的處理指示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed5d92fb-d53b-49a2-b2c7-8558708d6554
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 532721c347189f2e3d4db9e57b2afc3aa45b76db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="processing-instructions-in-detail"></a>詳細資料中的處理指示
本主題描述的格式和系統 Properties.xsd 屬性結構描述、 定義路線處理所需的數個內容屬性的結構。 收到並處理訊息時，這些屬性會升級[!INCLUDE[prague](../includes/prague-md.md)]管線; 因為它們是升級的屬性時，它們都可以存取 BizTalk Server 元件。 系統 Properties.xsd 屬性結構描述中定義下列屬性：  
  
-   **ItineraryHeader。** 此屬性包含所有的路線資訊和透過一系列路線步驟要叫用的路線服務的清單。 行程 API 會在內部使用這個屬性。  
  
-   **ServiceName。** 此屬性包含要處理的目前路線服務的名稱。  
  
-   **ServiceState。** 此屬性包含目前路線服務的狀態：**暫止**，**完成**，或**Active**。 所有服務都訂閱包含路線步驟**ServiceState**值**暫止**。  
  
-   **ServiceType。** 此屬性會定義路線步驟的類型 (**傳訊**或**協調流程**)。  
  
-   **IsRequestResponse。** 此屬性會定義訊息類型 (單向或要求-回應)。  
  
 路線服務的其中一種方式，根據的值執行路線步驟**ServiceType**屬性：  
  
-   路線的管線元件會執行所有的路線步驟與**ServiceType**屬性**傳訊**。 開發人員可以擴充此程序使用自訂管線和行程 API。  
  
-   當**ServiceType**屬性是**協調流程**，協調流程，由訂閱路線內容屬性，以啟用執行路線的步驟。  
  
 當路線服務處理序路線的步驟時，服務會負責前進的路線，並與新的路線內容使用發佈的進一步處理訊息分派-訂閱的 BizTalk Server 功能。 路線服務的訊息內容中路線的 完全控制、 可以前進到適當的步驟，根據其內部的邏輯和訊息內容。  
  
 路線處理機制支援單一行程內的傳訊和協調流程路線步驟的組合。 開發人員也可以定義自訂的路線服務和設定自訂路線的步驟。  
  
 如需行程的詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)。  
  
 如需自訂路線服務和自訂的路線步驟的詳細資訊，請參閱[建立自訂的行程服務](../esb-toolkit/creating-a-custom-itinerary-service.md)。