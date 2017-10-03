---
title: "模式目錄服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Calling Pipelines from Code pattern [service solutions]
- Recipient List pattern [service solutions]
- filters, design patterns
- Filter pattern [service solutions]
- caching, patterns [service solutions]
- Service Interface pattern [service solutions]
- Content-Based Routing pattern [service solutions]
- Inline Invocation of Back-End Processes pattern [service solutions]
- content-based routing, patterns [service solutions]
- messages, Translator pattern [service solutions]
- aggregations, patterns [service solutions]
- Translator pattern, service solutions
- Caching pattern [service solutions]
- Aggregation pattern [service solutions]
- patterns [service solutions], pattern types
- back-end processes
- services, interface pattern [service solutions]
ms.assetid: 5d8135c5-d5de-4e61-b3e8-2aa7f6de98c8
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9441ead974cdcaba66dd9d038e786a5a8c7b156e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pattern-catalog-for-the-service-oriented-solution"></a>模式目錄服務導向解決方案
服務導向解決方案中的模式包括 BizTalk Server 特定的程式設計慣例，以及前幾節中的企業整合模式。 本節中的清單包括這兩種模式。  
  
## <a name="pattern-types"></a>模式類型  
 下列主題所描述的項目簡短地描述模式，並指向其他描述解決方案如何使用模式的主題。 如為一般模式 (例如篩選)，項目會指出更為一般的主題。  
  
### <a name="aggregation-pattern"></a>彙總模式  
 彙總是從多個來源接收資訊，並將它併入單一訊息的模式。 服務導向解決方案會將三個不同來源的信用資訊結合成單一回應。 視您撰寫之解決方案的本質而定，可以用數種方式來進行彙總。 在某些情況下，您可能需要等待所有的回應。 在其他情況下 (例如貸款報價)，只要您有某個最小數目，那麼您可能會想先獲得回應。 服務導向解決方案會等到它有全部的三個回應，因為它需要全部三個才能傳回完整的信用報告。 如需詳細資訊，請參閱[轉譯服務導向解決方案的模式](../core/translating-the-patterns-of-the-service-oriented-solution.md)。  
  
### <a name="calling-pipelines-from-code-pattern"></a>從程式碼模式呼叫管線  
 您現在可以從程式碼和協調流程呼叫管線。 這允許重複使用管線並協助維護管線階段的協調流程解離。 如需詳細資訊，請參閱[從服務導向解決方案使用的管線](../core/using-pipelines-from-the-service-oriented-solution.md)。  
  
### <a name="caching-pattern"></a>快取模式  
 快取是儲存資訊而不需每次要求時都要從資料存放區擷取它的一般策略。 從「企業單一登入」系統擷取參考或組態資料已證明是解決方案的限制因素。 解決方案會快取資訊並定期重新整理快取。 如需詳細資訊，請參閱[使用 SSO 有效率地在服務導向解決方案](../core/using-sso-efficiently-in-the-service-oriented-solution.md)。 商務程序管理解決方案也會快取 SSO 資訊，雖然它會使用稍微不同的程序。 如需詳細資訊，請參閱[使用 SSO 有效率地在商務程序管理解決方案中](../core/using-sso-efficiently-in-the-business-process-management-solution.md)。  
  
### <a name="content-based-routing-pattern"></a>以內容為基礎的路由模式  
 在企業整合模式中，以內容為基礎的路由在 BizTalk 中較廣為接受。 在企業整合模式中，以內容為基礎的路由會根據訊息內容的某些部分來決定訊息的收件者。 服務導向解決方案會使用非常簡單之以內容為基礎的路由形式，即協調流程中的單一決策圖形會將訊息傳送至兩個地方的其中之一。 如需詳細資訊，請參閱 「 轉譯元件到協調流程圖形 > 中的[轉譯服務導向解決方案的模式](../core/translating-the-patterns-of-the-service-oriented-solution.md)。  
  
### <a name="filter-pattern"></a>篩選模式  
 篩選模式會選取符合特殊準則的訊息，以進行處理。 在 BizTalk Server 中，篩選模式幾乎一定會成為連接埠上的篩選條件運算式。 如需連接埠篩選器的詳細資訊，請參閱[使用篩選器與接收訊息 」 圖形](../core/using-filters-with-the-receive-message-shape.md)。  
  
### <a name="inline-invocation-of-back-end-processes-pattern"></a>後端程序模式的內嵌叫用  
 解決方案的內嵌版本會透過自訂組件來使用後端程序的內嵌叫用。 它具有可大幅改善效能的優點。 不過，它也具有將協調流程與傳輸通訊協定緊密耦合的缺點。 如需詳細資訊，請參閱[內嵌後端叫用](../core/inlining-back-end-invocation.md)。  
  
### <a name="recipient-list-pattern"></a>收件者清單模式  
 就抽象意義而言，服務導向解決方案會實作收件者清單，因為它會傳送訊息給三個不同的系統。 就實際層面而言，已部署的應用程式會將邏輯連接埠對應到特定位置，以決定收件者。 在應用程式內嵌版本的例子中，連線會透過 SSO 中的組態資訊來進行連線。 如需詳細資訊，請參閱[轉譯服務導向解決方案的模式](../core/translating-the-patterns-of-the-service-oriented-solution.md)。  
  
### <a name="service-interface-pattern"></a>服務介面模式  
 服務導向解決方案會以 Web 服務的方式來呈現自己，在許多方法中只有以服務來執行的方式是可行的。 如需使用協調流程做為 Web 服務的詳細資訊，請參閱[使用 Web Services](../core/using-web-services.md)。  
  
### <a name="translator-pattern"></a>轉譯程式模式  
 轉譯器的企業模式 (亦即將訊息從一個形式轉換為另一個形式) 最常轉譯為 BizTalk Server 對應。 如需 BizTalk Server 對應的一般資訊，請參閱[建立對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。  
  
## <a name="see-also"></a>另請參閱  
 [模式在服務導向解決方案](../core/patterns-in-the-service-oriented-solution.md)