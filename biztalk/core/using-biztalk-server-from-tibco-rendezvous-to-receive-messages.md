---
redirect_url: /biztalk/core/using-tibco-rendezvous-receive-ports-from-biztalk-server/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: b1738a0933b5f570edfd882778e50ebf7e2ca730
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="using-biztalk-server-from-tibco-rendezvous-to-receive-messages"></a>從 TIBCO Rendezvous 使用 BizTalk Server 接收訊息
Microsoft BizTalk Adapter for TIBCO Rendezvous 會分派事件，從多個執行緒上的佇列。 BizTalk Server 接收位置會與一個 TIBCO Rendezvous 事件佇列和它的發送器執行緒集區關聯。  
  
## <a name="memory-use-and-errors"></a>記憶體用量與錯誤  
 處理事件時，配接器會監看使用的資源。 如果記憶體用量超過配額上限，配接器會停止發送事件，直到回到記憶體用量配額下限為止。 請注意，這樣可能會導致遺漏非保證訊息的 TIBCO Rendezvous 訊息 (TIBCO RV 取用者有 60 秒的時間可移除佇列中的訊息)。 遺失此資料會報告為錯誤。 如果配接器收到 TIBCO Rendezvous 系統通報 NO_MEMORY 訊息，表示訊息已經遺失。  
  
 BizTalk Adapter for TIBCO Rendezvous 會維護狀態，並依據該狀態以不同的方式執行工作。 如果 BizTalk 訊息引擎報告錯誤，且配接器設為保證的接聽程式，它會向 TIBCO Rendezvous 報告錯誤，藉此重新提交訊息。  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md)   
 [建立 TIBCO Rendezvous 接收處理常式](../core/creating-tibco-rendezvous-receive-handlers.md)