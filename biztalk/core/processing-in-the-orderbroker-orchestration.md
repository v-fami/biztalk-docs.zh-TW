---
title: OrderBroker 協調流程中處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- orchestrations, nested scopes
- nested scopes, performance
- processing, examples
- nested scopes, orchestrations
- orchestrations, performance
- performance, orchestrations
- performance, nested scopes
- examples, orchestration processing [process management solution]
- scopes, nesting
ms.assetid: c296e00c-b3ad-4161-baf7-258899185c34
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c6a6571ece3190b6195b207b4c45969ce25ddec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22266630"
---
# <a name="processing-in-the-orderbroker-orchestration"></a>OrderBroker 協調流程中處理
本章節描述如何**OrderBroker**訂單的協調流程，並準備程序管理員。 這節的開始會討論協調流程的一般工作。 下一部分則會討論協調流程處理訊息的方法。 然後會著重在協調流程如何使用不可部分完成交易來改進效能。  
  
> [!NOTE]
>  由於長度的長度**OrderBroker**程式碼中，您可以閱讀此節與 Microsoft® Visual Studio 中開啟協調流程。  
  
## <a name="why-an-order-broker"></a>為什麼要使用 Order Broker？  
 目的**OrderBroker**協調流程是前置處理訂單，並將其路由至正確的處理序管理員。 這裡的預先處理包含為歷程資料庫及服務系統產生資訊訊息，並確認訂單的接收。 **OrderBroker**也會從客戶服務要求的建立一般的訂單訊息。 這樣的訂單標準化可讓商務程序元件，以一般的方式來使用訂單。  
  
 訂單訊息是一種多部分訊息，其中的路由資訊是與訂單資訊分開的。 路由資訊也是一般性的資訊，設計來讓訂單管理員使用。 這樣，便可輕易的擴充解決方案。 多部分訊息的相關資訊，請參閱[如何使用多部分訊息類型](../core/how-to-use-multi-part-message-types.md)。  
  
 獨立出仲介的功能也可讓您將仲介功能移到其他 BizTalk 群組中。 因為**OrderBroker**發佈到 MessageBox 資料庫，也就是說，它是直接繫結，也可讓您更輕鬆將 broker 放在其他群組可以移動 broker 而不需要變更協調流程。 如需有關放置**OrderBroker**在另一個群組中，請參閱[OrderBroker 與 OrderManager 之間的通訊](../core/communication-between-orderbroker-and-ordermanager.md)。  
  
> [!NOTE]
>  **OrderBroker**協調流程，因為只有一個**OrderManager**與通訊，只要將常數字串至**OrderMgrType**欄位的順序管理員訊息。 一般來說，在具有多個訂單管理員的應用程式中，應用程式會使用商務規則引擎來判斷這個欄位及其他訂單路由的值。 如需 「 商務規則引擎的詳細資訊，請參閱[建立和使用商務規則](../core/creating-and-using-business-rules.md)。  
  
## <a name="order-processing"></a>訂單處理  
 **OrderBroker**具有兩個協調流程會開始**接收**圖形內**接聽**圖形。 一個**接收**圖形接受來自客戶支援; 系統訊息從廠商系統的其他訊息。 來自任一來源的訊息都有相同的結構描述。  
  
 協調流程會從訊息中擷取回覆地址，並使用它來設定動態連接埠，位址**CSRPort**。 協調流程會使用這個連接埠來傳送確認及錯誤訊息。  
  
 接下來的步驟**OrderBroker**協調流程建立歷程訊息、 服務訊息、 確認訊息，以及訂單訊息傳送給**OrderManager**協調流程。 協調流程使用**InsertOrderBody**公用程式函式，將訂單訊息新增至歷程記錄訊息。  
  
> [!NOTE]
>  在某些狀況下，解決方案可能會產生傳送但沒有用的訊息。 Order Broker 協調流程會使用傳送埠將資訊插入歷程資料庫。 這個傳送埠會使用傳遞通知。 組態會將傳送埠對應到包含兩個連接埠的傳送埠群組，有一個測試組態的連接埠 (**HISTORYINSERT-SP-測試**)，另一個用於一般組態 (**HISTORYINSERT-SP**)。 若您讓群組中兩個連接埠同時執行，解決方案會在兩個連接埠上都傳送訊息。 因此它會要求兩個傳遞通知，但只會處理其中一個。  
>   
>  若要避免這種情況下，取消登錄測試連接埠 (**測試-HISTORYINSERT-SP**)，或停止應用程式測試版本**BTSScn.BPM.OrderBrokerApp.Test**。 如需傳遞通知的詳細資訊，請參閱[使用通知](../core/using-acknowledgments.md)。  
  
 建構要傳送到訊息時**OrderManager**協調流程， **OrderBroker**協調流程會使用兩個部分建立多部分訊息。 一個部分包含路由資訊；另一個部分包含訂單本身。 訊息的路由部分**OrderMgrMsg.Routing**，使用 C# 類別中所定義的結構描述**SchemaClasses**組件。 Broker 會將訂單部分當成是一般的訊息或類型不可知的 XML 文件 (**System.Xml.XmlDocument**) 並將其指派給**OrderMgrMsg.Order**。  
  
 有兩個路由資訊中的欄位對訂單管理員來說特別重要**OrderMgrMsg.Routing.OrderMgrType**和**OrderMgrMsg.Routing.Status**。 Broker 集**OrderMgrType**是以處理訂單的訂單管理員類型。 在解決方案中，只有一個訂單管理員，而欄位則設定為 CABLEORDER。 Broker 也會設定**狀態**欄位設為 接受。 這個值會告訴訂單管理員，該訊息為新的訂單。 在方案中，訂單管理員**OrderManager**協調流程，會使用**接收**篩選出訂單類型等於 CABLEORDER 而狀態等於 ACCEPTED 的圖形。  
  
 中的其餘步驟**OrderBroker**協調流程會將不同的訊息傳送至適當的連接埠。  
  
## <a name="improving-performance-with-nested-scopes"></a>使用巢狀範圍改善效能  
 其中一個值得注意的重點有關**OrderBroker**協調流程是它使用巢狀範圍。 這裡的巢狀範圍可限制持續點，因此可改善效能。  
  
 協調流程引擎會在稱為持續點的執行點間，定期地儲存整個協調流程的狀態。 協調流程引擎會自動將數個協調流程圖形，包括**傳送**圖形，視為持續點。 如需持續點的詳細資訊，請參閱[持續性和協調流程引擎](../core/persistence-and-the-orchestration-engine.md)。  
  
 具有五個**傳送**圖形， **OrderBroker**協調流程應該有五個持續點。 不過，當您分組**傳送**不可部分完成交易範圍內的圖形，引擎會認為它只需要一個持續點的範圍。 因為四個**傳送**圖形中**OrderBroker**協調流程並不屬於例外狀況處理常式和傳送之後，才能執行，不需要所以他們可以進入不可部分完成交易範圍。 這樣可減少持續點的數目。 如需不可部分完成交易的詳細資訊，請參閱[不可部分完成交易](../core/atomic-transactions.md)。  
  
 此外，若交易會在同時結束，協調流程引擎會使用單一個持續點來進行巢狀交易。 因此，方式**OrderBroker**協調流程巢狀放置於交易進一步減少持續點： 協調流程有單一個持續點，因為使用**範圍**圖形。  
  
> [!TIP]
>  您可將協調流程中持續點的數目降到最低，來改進效能。 您可以將群組**傳送**圖形的不可部分完成的交易，以產生單一個持續點的所有**傳送**圖形。 在同時結束巢狀交易會產生交易的單一個持續點。  
  
 不可部分完成交易範圍無法擁有例外狀況處理常式。 因此，協調流程會將不可部分完成範圍巢狀嵌入長時間執行的交易內。 這個外部的交易可能例外狀況處理常式，而且它是這個處理常式來處理從例外狀況**傳送**圖形。  
  
> [!TIP]
>  將不可部分完成交易巢狀嵌入長時間執行的交易中，是一種允許例外狀況處理的常見模式。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案中的處理](../core/processing-in-the-business-process-management-solution.md)   
 [程序管理員邏輯](../core/process-manager-logic.md)   
 [中斷商務程序管理解決方案中的處理](../core/interrupt-handling-in-the-business-process-management-solution.md)   
 [ExceptionHandler 協調流程](../core/the-exceptionhandler-orchestration.md)