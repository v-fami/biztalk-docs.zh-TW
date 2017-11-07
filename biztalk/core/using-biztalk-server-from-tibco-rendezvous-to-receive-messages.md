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
# <a name="using-biztalk-server-from-tibco-rendezvous-to-receive-messages"></a><span data-ttu-id="3f0b2-101">從 TIBCO Rendezvous 使用 BizTalk Server 接收訊息</span><span class="sxs-lookup"><span data-stu-id="3f0b2-101">Using BizTalk Server from TIBCO Rendezvous to Receive Messages</span></span>
<span data-ttu-id="3f0b2-102">Microsoft BizTalk Adapter for TIBCO Rendezvous 會分派事件，從多個執行緒上的佇列。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-102">Microsoft BizTalk Adapter for TIBCO Rendezvous dispatches events from a queue on multiple threads.</span></span> <span data-ttu-id="3f0b2-103">BizTalk Server 接收位置會與一個 TIBCO Rendezvous 事件佇列和它的發送器執行緒集區關聯。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-103">A BizTalk Server receive location is associated with one TIBCO Rendezvous event queue and its pool of dispatcher threads.</span></span>  
  
## <a name="memory-use-and-errors"></a><span data-ttu-id="3f0b2-104">記憶體用量與錯誤</span><span class="sxs-lookup"><span data-stu-id="3f0b2-104">Memory Use and Errors</span></span>  
 <span data-ttu-id="3f0b2-105">處理事件時，配接器會監看使用的資源。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-105">While processing events, the adapter keeps an eye on used resources.</span></span> <span data-ttu-id="3f0b2-106">如果記憶體用量超過配額上限，配接器會停止發送事件，直到回到記憶體用量配額下限為止。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-106">If memory use goes above the high-watermark, the adapter stops dispatching events until it reaches the low-watermark memory consumption.</span></span> <span data-ttu-id="3f0b2-107">請注意，這樣可能會導致遺漏非保證訊息的 TIBCO Rendezvous 訊息 (TIBCO RV 取用者有 60 秒的時間可移除佇列中的訊息)。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-107">Note that this might result in TIBCO Rendezvous messages being missed for non certified messages (a TIBCO RV consumer has 60 seconds to remove messages from a queue).</span></span> <span data-ttu-id="3f0b2-108">遺失此資料會報告為錯誤。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-108">This data loss is reported as an error.</span></span> <span data-ttu-id="3f0b2-109">如果配接器收到 TIBCO Rendezvous 系統通報 NO_MEMORY 訊息，表示訊息已經遺失。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-109">If the adapter receives a TIBCO Rendezvous system advisory NO_MEMORY message, messages have already been lost.</span></span>  
  
 <span data-ttu-id="3f0b2-110">BizTalk Adapter for TIBCO Rendezvous 會維護狀態，並依據該狀態以不同的方式執行工作。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-110">BizTalk Adapter for TIBCO Rendezvous maintains a state, and it executes tasks differently based on that state.</span></span> <span data-ttu-id="3f0b2-111">如果 BizTalk 訊息引擎報告錯誤，且配接器設為保證的接聽程式，它會向 TIBCO Rendezvous 報告錯誤，藉此重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="3f0b2-111">If the BizTalk Message Engine reports an error, and the adapter is configured to be a certified listener, it reports the error to TIBCO Rendezvous so that it can resubmit the message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f0b2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f0b2-112">See Also</span></span>  
 <span data-ttu-id="3f0b2-113">[TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="3f0b2-113">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="3f0b2-114">建立 TIBCO Rendezvous 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="3f0b2-114">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)