---
title: "具現化，並初始化接收配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5cb5ba7-e2b5-49d2-adf5-a8df0bb81def
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 565712faecf11b728c4f552798b1e3daebf962f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="instantiating-and-initializing-a-receive-adapter"></a><span data-ttu-id="173e6-102">產生並初始化接收配接器</span><span class="sxs-lookup"><span data-stu-id="173e6-102">Instantiating and Initializing a Receive Adapter</span></span>
<span data-ttu-id="173e6-103">接收配接器一旦產生，便會立即由傳訊引擎初始化，此引擎會呼叫 IBTTransportControl 的 QueryInteraface。</span><span class="sxs-lookup"><span data-stu-id="173e6-103">Immediately after a receive adapter is instantiated it is initialized by the Messaging Engine, the engine calls QueryInteraface for IBTTransportControl.</span></span> <span data-ttu-id="173e6-104">然後它會呼叫 IBTTransportControl**。初始化**配接器的傳輸 proxy，它會保存在成員變數中的配接器中傳遞。</span><span class="sxs-lookup"><span data-stu-id="173e6-104">It then calls IBTTransportControl**.Initialize** passing in the adapter's transport proxy, which the adapter persists in a member variable.</span></span> <span data-ttu-id="173e6-105">接著，引擎會呼叫**QueryInterface**如**IPersistPropertyBag**。</span><span class="sxs-lookup"><span data-stu-id="173e6-105">Next the engine calls **QueryInterface** for **IPersistPropertyBag**.</span></span> <span data-ttu-id="173e6-106">這是選擇性的介面。如果配接器實作，處理常式組態會傳遞給配接器在**負載**方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="173e6-106">This is an optional interface; if the adapter implements it, the handler configuration is passed to the adapter in the **Load** method call.</span></span> <span data-ttu-id="173e6-107">初始化接收配接器的最後階段需要將結束點組態傳遞到配接器。</span><span class="sxs-lookup"><span data-stu-id="173e6-107">The final stage of initializing a receive adapter involves passing the endpoint configuration to the adapter.</span></span> <span data-ttu-id="173e6-108">在這個階段，引擎會呼叫**IBTTransportConfig.AddReceiveEndpoint**一次是針對每個作用中的端點，在 URI 中傳遞之端點、 端點，配接器特定組態和 BizTalk 組態該端點。</span><span class="sxs-lookup"><span data-stu-id="173e6-108">During this phase the engine calls **IBTTransportConfig.AddReceiveEndpoint** once for each active endpoint, passing in the URI for the endpoint, the adapter specific configuration for the endpoint, and the BizTalk configuration for that endpoint.</span></span>  
  
 <span data-ttu-id="173e6-109">下圖顯示 API 呼叫的順序。</span><span class="sxs-lookup"><span data-stu-id="173e6-109">The following figure illustrates this sequence of API calls.</span></span> <span data-ttu-id="173e6-110">配接器會實作標示為藍色的介面。</span><span class="sxs-lookup"><span data-stu-id="173e6-110">The adapter implements the interfaces shown in blue.</span></span>  
  
 ![](../core/media/sequence-of-init-calls.gif "Sequence_of_init_calls")  
  
 <span data-ttu-id="173e6-111">**實作秘訣：**一般情況下，配接器應該不會封鎖傳訊引擎中呼叫這類**IBTTransportControl.Initialize**， **IPersistPropertyBag.Load**，和**IBTTransportConfig.AddReceiveEndpoint**。</span><span class="sxs-lookup"><span data-stu-id="173e6-111">**Implementation Tip:** In general, adapters should not block the Messaging Engine in calls such as **IBTTransportControl.Initialize**, **IPersistPropertyBag.Load**, and **IBTTransportConfig.AddReceiveEndpoint**.</span></span> <span data-ttu-id="173e6-112">在這些呼叫中執行過多的處理，可能對服務啟動時間會有負面影響。</span><span class="sxs-lookup"><span data-stu-id="173e6-112">Performing excessive processing in these calls can have a negative impact on service startup time.</span></span>  
  
 <span data-ttu-id="173e6-113">具有一或多個相關接收位置的所有接收配接器都是在服務啟動時建立的。</span><span class="sxs-lookup"><span data-stu-id="173e6-113">All receive adapters that have one or more associated receive locations are created at service startup.</span></span> <span data-ttu-id="173e6-114">所有接收配接器都是非同步且支援批次處理的，</span><span class="sxs-lookup"><span data-stu-id="173e6-114">All receive adapters are asynchronous and support batching.</span></span> <span data-ttu-id="173e6-115">可能屬於內含式或外掛式。</span><span class="sxs-lookup"><span data-stu-id="173e6-115">They can be in-process or isolated.</span></span> <span data-ttu-id="173e6-116">如需有關接收配接器變數，請參閱[配接器變數](../core/adapter-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="173e6-116">For additional information about receive adapter variables, see [Adapter Variables](../core/adapter-variables.md).</span></span>