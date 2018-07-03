---
title: 循序群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- convoy sets
- correlation sets, sequential receive tasks
ms.assetid: f05ff42c-2236-42a3-8166-19700e0c3d97
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a160c8db8f0cff4ad9465e1e19c418fc0831a5d9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971199"
---
# <a name="sequential-convoys"></a><span data-ttu-id="75ab7-102">循序群組</span><span class="sxs-lookup"><span data-stu-id="75ab7-102">Sequential Convoys</span></span>
<span data-ttu-id="75ab7-103">循序群組可讓多個單一訊息聯結在一起，以達成所需的結果。</span><span class="sxs-lookup"><span data-stu-id="75ab7-103">A sequential convoy enables multiple single messages to join together to achieve a required result.</span></span> <span data-ttu-id="75ab7-104">循序群組是具有預先定義順序的相關訊息組。</span><span class="sxs-lookup"><span data-stu-id="75ab7-104">A sequential convoy is a set of related messages that have a predefined order.</span></span> <span data-ttu-id="75ab7-105">雖然訊息不需要完全相同，但 BizTalk Server 必須以循序方式接收這些訊息。</span><span class="sxs-lookup"><span data-stu-id="75ab7-105">Although the messages do not have to be exactly the same, BizTalk Server must receive them in a sequential order.</span></span>  
  
 <span data-ttu-id="75ab7-106">例如，假設線上零售公司在一天當中，接到從直屬客戶以及經銷商傳來的新訂單。</span><span class="sxs-lookup"><span data-stu-id="75ab7-106">For example, suppose that an online retail company receives new orders from direct clients and from dealers throughout the course of the day.</span></span> <span data-ttu-id="75ab7-107">所有在下午 2:00 之前接到的訂單都必須以單一批次傳送給倉庫，且必須保存接收訂單的順序。</span><span class="sxs-lookup"><span data-stu-id="75ab7-107">All orders received before 2:00 PM must go to the warehouse in a single batch, and the sequence of the receipt of the orders must be preserved.</span></span> <span data-ttu-id="75ab7-108">這樣如果倉庫有缺貨的情況，較早接到的訂單將擁有優先權。</span><span class="sxs-lookup"><span data-stu-id="75ab7-108">This enables earlier orders to have priority in case any items are out of stock in the warehouse.</span></span> <span data-ttu-id="75ab7-109">批次訂單的建立方式，是將當天的所有訂單組合到單一檔案中，並附上批次標頭資訊。</span><span class="sxs-lookup"><span data-stu-id="75ab7-109">You build this batch order by assembling all orders for the day in a single file that has batch header information.</span></span> <span data-ttu-id="75ab7-110">在下午 2:00 時，當天所有的訂單都會傳送到倉庫進行處理。</span><span class="sxs-lookup"><span data-stu-id="75ab7-110">At 2:00 PM, all orders for the day go to the warehouse for processing.</span></span> <span data-ttu-id="75ab7-111">在下午 2:00 以後收到的所有訂單都將放入新的批次，等候次日處理。</span><span class="sxs-lookup"><span data-stu-id="75ab7-111">All orders received after 2:00 PM are put into a new batch for processing on the following day.</span></span>  
  
 <span data-ttu-id="75ab7-112">前述的案例是需要對內送訊息進行循序群組處理的範例。</span><span class="sxs-lookup"><span data-stu-id="75ab7-112">The preceding scenario is an example of a business process that requires sequential convoy processing of incoming messages.</span></span> <span data-ttu-id="75ab7-113">根據商務需求指出，在特定日下午 2:00 之前接到的所有單一訂單，都應該合併批次處理。</span><span class="sxs-lookup"><span data-stu-id="75ab7-113">The business requirements state that all single orders received before 2:00 PM for a specific day should batch together.</span></span> <span data-ttu-id="75ab7-114">為此，第一個收到的訊息必須啟動新的協調流程執行個體，並初始化相互關聯集合。</span><span class="sxs-lookup"><span data-stu-id="75ab7-114">This requires the first message received to start a new orchestration instance and initialize a correlation set.</span></span> <span data-ttu-id="75ab7-115">此時，如果收到該訊息類型的其他訂單，都會路由至已經執行的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="75ab7-115">At that point, all other orders received of that message type route to the already-running orchestration instance.</span></span> <span data-ttu-id="75ab7-116">若要達成此目的，您定位**接聽**圖形 (包含**接收**圖形和**延遲**圖形) 內**迴圈**圖形。</span><span class="sxs-lookup"><span data-stu-id="75ab7-116">To accomplish this, you position a **Listen** shape (containing a **Receive** shape and a **Delay** shape) inside a **Loop** shape.</span></span> <span data-ttu-id="75ab7-117">在到達延遲之後，迴圈就會結束。</span><span class="sxs-lookup"><span data-stu-id="75ab7-117">After reaching the delay, the loop ends.</span></span> <span data-ttu-id="75ab7-118">這樣可以在相同的商務程序中接收未知數目的訂單。</span><span class="sxs-lookup"><span data-stu-id="75ab7-118">This allows for the receipt of an unknown number of orders in the same business process.</span></span>  
  
## <a name="implementing-sequential-convoys"></a><span data-ttu-id="75ab7-119">實作循序群組</span><span class="sxs-lookup"><span data-stu-id="75ab7-119">Implementing Sequential Convoys</span></span>  
 <span data-ttu-id="75ab7-120">您可以使用 BizTalk Server 中的「相互關聯的循序接收」傳訊設計模式來實作循序群組。</span><span class="sxs-lookup"><span data-stu-id="75ab7-120">You can implement sequential convoys by using the "sequential correlated receives" messaging design pattern in BizTalk Server.</span></span> <span data-ttu-id="75ab7-121">相互關聯的循序接收是與之前的接收相互關聯的接收行為。</span><span class="sxs-lookup"><span data-stu-id="75ab7-121">Sequential correlated receives are receives that are correlated to previous receives.</span></span>  
  
 <span data-ttu-id="75ab7-122">如果接收的相互關聯集合是由其他接收初始化，就會發生群組處理。</span><span class="sxs-lookup"><span data-stu-id="75ab7-122">Convoy processing takes place for cases in which the correlation sets for a receive are initialized by another receive.</span></span>  
  
 <span data-ttu-id="75ab7-123">對於需要群組處理的接收而言，適用下列的限制：</span><span class="sxs-lookup"><span data-stu-id="75ab7-123">For receives that require convoy processing, the following restrictions apply:</span></span>  
  
- <span data-ttu-id="75ab7-124">構成特定接收之循序群組集合的相互關聯集合必須由之前的接收初始化。</span><span class="sxs-lookup"><span data-stu-id="75ab7-124">The correlation sets that constitute a sequential convoy set for a particular receive must be initialized by one preceding receive.</span></span>  
  
- <span data-ttu-id="75ab7-125">需要循序群組處理之接收的連接埠，必須與初始化群組集合之接收的連接埠相同。</span><span class="sxs-lookup"><span data-stu-id="75ab7-125">The port for a receive that requires sequential convoy processing must be the same as the port for the receive initializing the convoy set.</span></span> <span data-ttu-id="75ab7-126">跨連結埠的群組不受支援。</span><span class="sxs-lookup"><span data-stu-id="75ab7-126">Cross-port convoys are not supported.</span></span>  
  
- <span data-ttu-id="75ab7-127">需要群組處理之接收的訊息類型，必須符合初始化群組集合之接收的訊息類型，除非接收陳述式是在排序的傳遞連接埠上運作。</span><span class="sxs-lookup"><span data-stu-id="75ab7-127">Message types for a receive that requires convoy processing must match the message type for the receive initializing the convoy set, unless the receive statement is operating on an ordered delivery port.</span></span>  
  
- <span data-ttu-id="75ab7-128">參與循序群組的所有接收，都必須遵循由初始化接收所初始化 (或遵循) 的所有相互關聯集合，除非是在排序的傳遞連接埠上運作。</span><span class="sxs-lookup"><span data-stu-id="75ab7-128">All receives participating in a sequential convoy must follow all the correlation sets that are initialized (or followed) by the initializing receive, unless operating on an ordered delivery port.</span></span>  
  
- <span data-ttu-id="75ab7-129">如果循序群組是由啟動接收陳述式所初始化，則啟動接收不能具有篩選條件運算式，除非是在排序的傳遞連接埠上運作。</span><span class="sxs-lookup"><span data-stu-id="75ab7-129">If a sequential convoy is initialized by an activate receive statement, then the activate receive cannot have a filter expression unless operating on an ordered delivery port.</span></span>  
  
- <span data-ttu-id="75ab7-130">如果循序群組是由啟動接收所初始化，則其後的接收不能位在巢狀的協調流程內。</span><span class="sxs-lookup"><span data-stu-id="75ab7-130">If a sequential convoy is initialized by an activate receive, the following receives cannot be inside a nested orchestration.</span></span>  
  
  <span data-ttu-id="75ab7-131">如需循序群組實作的範例，請參閱 <<c0> [ 彙總工具 （BizTalk Server 範例）](../core/aggregator-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="75ab7-131">For an example of sequential convoy implementation, see [Aggregator (BizTalk Server Sample)](../core/aggregator-biztalk-server-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ab7-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75ab7-132">See Also</span></span>  
 <span data-ttu-id="75ab7-133">[使用群組實例](../core/working-with-convoy-scenarios.md) </span><span class="sxs-lookup"><span data-stu-id="75ab7-133">[Working with Convoy Scenarios](../core/working-with-convoy-scenarios.md) </span></span>  
 [<span data-ttu-id="75ab7-134">平行群組</span><span class="sxs-lookup"><span data-stu-id="75ab7-134">Parallel Convoys</span></span>](../core/parallel-convoys.md)