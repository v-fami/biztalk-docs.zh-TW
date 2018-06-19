---
title: 使用協調流程為路線服務的訂閱者 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 278564f1-de9f-4fbf-8c7f-09b3e607c28b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f496884d0aed8d5f351f681ca8cfe59e05684240
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295318"
---
# <a name="using-an-orchestration-as-an-itinerary-service-subscriber"></a>使用協調流程為路線服務的訂閱者
協調流程也可以當做路線的服務。 若要加入的路線，您必須先設計將協調流程直接繫結。若要這樣做，請使用 類似上一個主題中的傳送埠的篩選條件訂閱[用作路線服務的訂閱者端的傳送埠](../esb-toolkit/using-a-send-port-as-an-itinerary-service-subscriber.md)。 圖 1 顯示適當的協調流程收取符合下列條件的任何訊息篩選條件運算式的範例：  
  
-   **ServiceName = Microsoft.Practices.ESB.Services.Transform**  
  
-   **ServiceState = 暫止**  
  
-   **ServiceType = 協調流程**  
  
 ![協調流程](../esb-toolkit/media/ch4-orchestration.jpg "第 4 章第協調流程")  
  
 **圖 1**  
  
 **要參與行程為訂閱者的協調流程的範例篩選條件運算式**  
  
 當訊息送達 Microsoft BizTalk Server 透過 ESB 上手時，ESB 管線中的驗證步驟會將篩選條件屬性的屬性值寫入至內送訊息; BizTalk 內容屬性這將其提升至訊息內容。 路線服務永遠設定**ServiceName**目前作用中的服務，以處理接下來，並與服務的名稱屬性**ServiceState**屬性值為**暫止**。 訂用帳戶，您必須設定至少第三個下列屬性：  
  
-   **ServiceName。** 這是存放在 ESB 行程中，服務的名稱，而且可以是任何名稱。 路線會使用此名稱來識別要執行的服務。  
  
-   **ServiceState。** 這是要執行之目前路線服務步驟的狀態。 目前的服務步驟 （適用於處理下一步） 一定會值**暫止**、 任一 ESB 路線管線元件，ESB 行程選取器管線元件，來設定或程式碼呼叫**進階**路線應用程式開發介面的方法。  
  
-   **ServiceType。** 此屬性會定義服務，指出它是否來自協調流程 」 或 「 biztalk 傳訊子系統的型別。  
  
-   **IsRequestResponse。** 這個選擇性屬性必須具有相同的值**IsRequestResponse**服務屬性。