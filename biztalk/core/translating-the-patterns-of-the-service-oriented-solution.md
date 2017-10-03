---
title: "轉譯模式的服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- patterns [service solutions], translating patterns to orchestration shapes
- artifacts, patterns
- orchestrations, patterns
- patterns [process management solutions], connections
- patterns [service solutions], orchestration boundaries
- patterns [process management solutions], translating patterns to orchestrations
- orchestrations, boundaries
- patterns [service solutions], translating patterns to artifacts
ms.assetid: ff17cc41-2a7b-4304-b5bd-96b1174cea7f
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95285c93bdb290adbee988305dbcd365e4e729a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="translating-the-patterns-of-the-service-oriented-solution"></a>轉譯模式的服務導向解決方案
本節描述解決方案如何將模式圖轉譯為 BizTalk Server 成品。  
  
 ![服務 &#45; 導向的解決方案模式](../core/media/service-oriented-solution-patterns.gif "Service_Oriented_Solution_Patterns")  
  
## <a name="connections-and-completeness-conditions"></a>連線與完整性條件  
 我們可以在任何地方開始將模式轉譯為 BizTalk Server 元件。 不過實際上，元件之間的連線是元件的基礎結構，如此一來，這似乎是開始的好地方。 此外，在整合者模式的狀況下，我們必須考量要如何分辨它具有所有需要的資訊。 這會影響到它對其他元件的連線，以及它的設計。  
  
 解決方案必須提供一個方便使用且一致的方法。 服務介面會指定其他應用程式如何使用它。 因為解決方案必須與使用 IBM WebSphere MQ 的傳統應用程式進行通訊，所以 IBM WebSphere MQ 必須是服務介面的一部分。 不過，對於新的應用程式而言，Web 服務介面似乎是很明確的選擇。 Web 服務介面會對其他使用服務的應用程式提供最大的彈性。 在此，我們可以使用 BizTalk Server 的彈性來享有雙重服務介面。 公開為 Web 服務的協調流程的相關資訊，請參閱[如何對應至 Web 服務的協調流程](../core/how-to-map-orchestrations-to-web-services.md)。  
  
 其他連線是服務介面與收件者清單之間的連線、收件者清單與後端應用程式之間的連線，以及在後端應用程式、整合者和服務介面之間的連線。  
  
 若連接到收件者清單的連線是同步的，解決方案不需要使用相互關聯，以確保已傳送和接收所有傳送到收件者清單的訊息。 基於相同理由，所以後端應用程式和整合者之間的連線可以同步。 整合者需要來自全部三個後端應用程式的回應，以完成查詢回應。 回應時間應該要短一點，這樣同步連線才適用，並可簡化解決方案。  
  
 在整合者模式中，通常會有完整性條件。 在有多部後端伺服器且回應時間很慢的狀況下，例如，完整性條件可能在指定的時期內接收至少一個回應。 這個服務導向解決方案需要全部三個回應，才能建構最後的訊息。 因此，此處的完整性條件就是接收全部三個回應。  
  
> [!NOTE]
>  時接收透過 IBM WebSphere MQ 的要求，方案會將相互關聯識別項複製**MQMD_MsgId**值設定為**MQMD_CorrelId**回應訊息。 這是在要求-回應中使用 MQSeries 配接器，以避免可能的競爭條件之標準方法的一部分。 如需詳細資訊，請參閱[相互關聯訊息使用要求-回覆](../core/correlating-messages-using-request-reply.md)。  
  
## <a name="determining-orchestration-boundaries"></a>判斷協調流程界限  
 這個解決方案必須允許來自 IBM WebSphere MQ 佇列以及透過 Web 服務介面的要求。 將服務介面放入一個協調流程中、將 IBM WebSphere MQ 輸入到另一個協調流程中，並將大量處理放入第三個協調流程中，讓外部通訊與處理保持分開的狀態。  
  
## <a name="translating-the-components-into-orchestration-shapes"></a>將元件轉譯為協調流程圖形  
 在最後的解決方案中，轉譯為圖形的模式將會在單一協調流程中。 有很多種方式可以在 BizTalk Server 中建立以內容為基礎的路由器，包括建立 MessageBox 訂閱。 在這個解決方案中，路由會使用 MessageBox 訂閱。 運算式圖形會評估訊息是否包括所需欄位的值。 決策圖形會評估運算式圖形中的變數集，並透過協調流程來選取路徑。  
  
 **CustomerService**協調流程會使用平行圖形，將訊息傳送至後端應用程式並同步接收回應。 在提出下一個要求以前，不需要等待某一個應用程式完成。 若應用程式的數目經常變更，或者連接到應用程式的連線並不可靠，那麼協調流程必須以不同的方式來轉譯模式。  
  
 在這個解決方案中，整合者必須結合來自三個回應訊息的項目。 使用平行圖形，以確保與後端系統的通訊是平行的。 此外，因為圖形在接收所有回應或逾時以前不會終止，整合者一定會知道它可以繼續執行的時機。 協調流程會使用一個轉換圖形，該圖形會將來自三個後端回應訊息和原始要求訊息的項目，對應至回應訊息中的項目。  
  
> [!NOTE]
>  與後端系統的通訊可能也逾時。您可以設定逾時期限封入**接收**成形**範圍**形狀和設定**逾時**範圍的屬性。  
  
 如需協調流程圖形的完整清單，請參閱[協調流程圖形](../core/orchestration-shapes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [模式在服務導向解決方案](../core/patterns-in-the-service-oriented-solution.md)   
 [元件的服務導向解決方案](../core/components-of-the-service-oriented-solution.md)