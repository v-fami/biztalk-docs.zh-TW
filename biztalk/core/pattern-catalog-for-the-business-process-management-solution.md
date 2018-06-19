---
title: 模式的商務程序管理解決方案的目錄 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Canonical Message pattern [process management solutions]
- Nested Scopes pattern [process management solutions]
- Filter pattern [process management solutions]
- Per-Instance Pipeline Configuration pattern [process management solutions]
- Translator pattern, process management solutions
- patterns [process management solutions], pattern types
- Interruptible Orchestration pattern [process management solutions]
- Decoupled Orchestration pattern [process management solutions]
- Code Retry and Exception Handling pattern [process management solutions]
- Process Manager pattern [process management solutions]
- Asynchronous Reply pattern [process management solutions]
- Custom Exceptions pattern [process management solutions]
- Message Broker pattern [process management solutions]
- Coordination Using Delivery Notification pattern [process management solutions]
- Convoy pattern [process management solutions]
- Versioning pattern [process management solutions]
- Error Routing pattern [process management solutions]
- Application Reference pattern [process management solutions]
- Inverse Direct Partner Binding pattern [process management solutions]
ms.assetid: 246b109e-6006-404d-88b9-e6324ce3473c
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22b352cce73e45103437407a013691e604b7b959
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22266414"
---
# <a name="pattern-catalog-for-the-business-process-management-solution"></a>商務程序管理解決方案的模式目錄
商務程序管理解決方案中的模式包括以程式語言設計 BizTalk Server 的通用模式，以及之前章節中的企業整合模式。 本節中的清單包括這兩種模式。  
  
## <a name="pattern-types"></a>模式類型  
 下列項目將簡短描述模式，並指出描述解決方案如何使用該模式的其他主題。 如為一般模式 (例如篩選)，項目會指出更為一般的主題。  
  
### <a name="application-reference-patterns"></a>應用程式參考模式  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 讓應用程式可藉由加入其他應用程式的參照，在相同群組的另一個應用程式中使用成品。 商務程序管理解決方案會在設計測試解決方案及主要解決方案中，使用應用程式參照。 如需解決方案中的應用程式參考的詳細資訊，請參閱[商務程序管理解決方案中的部分設計原則](../core/some-design-principles-in-the-business-process-management-solution.md)。  
  
### <a name="asynchronous-reply-patterns"></a>非同步回覆模式  
 訂單管理員與訂單處理階段之間的通訊是非同步的。 也就是說，管理員會繼續處理，直到接收到回覆為止。 階段會使用自我相互關聯的動態連接埠，將回覆傳送給管理員。 自我相互關聯的連接埠可免除訂單管理員要管理相互關聯集的需要。 連接埠的動態層面允許訂單管理員將訂單階段傳送至連接埠的位址，以用於回覆。 如需解決方案中的連接埠的詳細資訊，請參閱[訂單流程的程序管理員透過](../core/order-flow-through-the-process-manager.md)。  
  
### <a name="canonical-message-patterns"></a>標準訊息模式  
 為簡化處理，解決方案通常會將外部訊息轉譯為內部格式。 此格式為標準訊息的範例。 訂單仲介協調流程會將所有的訂單訊息，轉譯為一或多個標準訂單訊息。 訂單管理員協調流程與處理階段會使用這個通用的訂單格式。 如需詳細資訊，請參閱[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)。  
  
### <a name="code-retry-and-exception-handling-patterns"></a>程式碼重試與例外狀況處理模式  
 方案可以集中其例外狀況處理中的許多**ExceptionHandler**協調流程。 如有機會，解決方案便會使用這個協調流程，例如，在網路連線無效時，若使用該協調流程重試，則該作業可能會成功。 協調流程使用**Recaller**重新執行失敗的程式碼的物件。 如需協調流程的詳細資訊，請參閱[商務程序管理解決方案的例外狀況處理](../core/exception-handling-in-the-business-process-management-solution.md)。 另請參閱[ExceptionHandler 協調流程](../core/the-exceptionhandler-orchestration.md)。 如需詳細資訊的使用**Recaller**物件，請參閱[Recaller 物件](../core/the-recaller-object.md)。  
  
### <a name="convoy-pattern"></a>群組模式  
 訂單管理員協調流程 (OrderManager) 會使用群組模式，來攔截和處理對已處理之訂單的後續變更。 如需訂單管理員中群組模式的詳細資訊，請參閱 < 訂單更新 >[訂單流程的程序管理員透過](../core/order-flow-through-the-process-manager.md)。  
  
### <a name="coordination-using-delivery-notification"></a>使用傳遞通知的協調  
 **OrderBroker**協調流程會使用傳遞通知，以確保歷程記錄更新第二個訂單處理階段之前，會記錄資料庫中變更項目 (**CableOrder2**)。 如需詳細資訊，請參閱 「 與階段協調"[訂單流程的程序管理員透過](../core/order-flow-through-the-process-manager.md)。 如需傳遞通知的一般資訊，請參閱[使用通知](../core/using-acknowledgments.md)。  
  
### <a name="custom-exceptions-pattern"></a>自訂例外狀況模式  
 對於無法重試的例外狀況，解決方案會使用通用的 BizTalk Server 例外狀況處理及自訂的例外狀況處理。 自訂的例外狀況處理會提供更特定的例外狀況處理。 它也可做為巢狀範圍之間的旗標，以確定作業的所有部分均會回復。 如需解決方案使用的自訂例外狀況，請參閱[自訂例外狀況](../core/custom-exceptions.md)。 如需範圍的詳細資訊，請參閱[如何設定 「 範圍 」 圖形](../core/how-to-configure-the-scope-shape.md)。  
  
### <a name="decoupled-orchestration-patterns"></a>低耦合的協調流程模式  
 商務程序管理解決方案的設計目的是減少協調流程到達其最大範圍的可能性。 減少協調流程使其可以更容易地進行解決方案之版本管理的部分，並簡化將解決方案移至其他的伺服器或群組的部分。 如需訂單仲介和訂單管理員之間的關聯性的詳細資訊，請參閱[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)和[訂單流程的程序管理員透過](../core/order-flow-through-the-process-manager.md)。  
  
### <a name="error-routing-pattern"></a>錯誤路由模式  
 解決方案會使用新的 BizTalk Server 錯誤報告功能。 此功能會將失敗的訊息路由至訂閱連接埠，以進行報告或處理。 如需錯誤報告的一般資訊，請參閱[使用失敗訊息路由](../core/using-failed-message-routing.md)。  
  
### <a name="filter-pattern"></a>篩選模式  
 篩選模式會選取符合特殊準則的訊息，以進行處理。 在 BizTalk 中，篩選模式幾乎總會成為連接埠上的篩選條件運算式。 如需連接埠篩選器的詳細資訊，請參閱[使用篩選器與接收訊息 」 圖形](../core/using-filters-with-the-receive-message-shape.md)。  
  
### <a name="interruptible-orchestration-pattern"></a>可中斷協調流程模式  
 解決方案會先中斷目前訂單，來處理訂單的更新或取消。 解決方案中的協調流程會使用中斷協調流程，來處理中斷。 如需詳細資訊，請參閱[中斷商務程序管理解決方案中處理](../core/interrupt-handling-in-the-business-process-management-solution.md)。  
  
### <a name="inverse-direct-partner-binding-pattern"></a>反向直接夥伴繫結模式  
 解決方案會反向處理直接繫結的使用，以減少來自訂單管理員的訂單處理階段。 如需反向直接繫結的詳細資訊，請參閱[反向直接夥伴繫結](../core/inverse-direct-partner-binding.md)。  
  
### <a name="message-broker-pattern"></a>訊息仲介模式  
 訊息仲介模式讓解決方案可以判斷訊息的目的地，所以傳送者不需知道其目的地。 商務程序管理解決方案會實作訊息仲介與**OrderBroker**協調流程。 **OrderBroker**協調流程接受訂單，判斷所訂購的服務類型，並將訂單路由至正確的訂單管理員。 如需有關中進行訊息仲介**OrderBroker**，請參閱[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)。  
  
### <a name="nested-scopes-pattern"></a>巢狀範圍模式  
 **OrderBroker**協調流程使用巢狀的範圍，以減少持續點，因此，以改善效率。 如需詳細資訊，請參閱 < 改善效能與巢狀範圍 」 中的[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)。  
  
### <a name="per-instance-pipeline-configuration"></a>個別執行個體管線組態  
 雖然解決方案會使用預設的管線，它能大量使用新的個別執行個體管線組態，以指定訊息的信封。 如需詳細資訊，請參閱[如何部署管線](../core/how-to-deploy-pipelines.md)和[商務程序管理解決方案的元件](../core/components-of-the-business-process-management-solution.md)。  
  
### <a name="process-manager-pattern"></a>程序管理員模式  
 解決方案會使用較一般的訂單管理員，來控制訂單處理階段的流程。 這有助於從訂單程序的管理中將商務邏輯分離出來。 如需 OrderManager 協調流程與程序管理員的運作方式的詳細資訊，請參閱[程序管理員邏輯](../core/process-manager-logic.md)。  
  
### <a name="terminate-shape-at-end-of-orchestration"></a>協調流程結束上的終止圖形  
 數個協調流程會在錯誤上使用「終止」圖形來結束，即使該協調流程已經在該點上正常結束。 「終止」圖形能追蹤已失敗的執行個體與錯誤。 如需詳細資訊，請參閱[自訂例外狀況](../core/custom-exceptions.md)。  
  
### <a name="translator-pattern"></a>轉譯程式模式  
 轉譯程式的企業模式 (亦即將訊息從一個形式轉換為另一個形式) 最常轉譯為 BizTalk 對應。 如需 BizTalk 對應的一般資訊，請參閱[建立對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。  
  
### <a name="versioning-patterns"></a>版本管理模式  
 商務程式管理解決方案是設計來透過減少協調流程，並使用結構描述命名空間中的版本編號，以簡化解決方案元件的版本管理。 如需詳細資訊，請參閱[版本設定商務程序管理解決方案](../core/versioning-the-business-process-management-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案中的模式](../core/patterns-in-the-business-process-management-solution.md)