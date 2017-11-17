---
title: "非同步的商務事件追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, BAM
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 6d51fadf-b329-4536-9618-d982d9c17882
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7191d9b0be94b4b089a91e78dd526867171c68a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="asynchronous-business-event-tracking"></a><span data-ttu-id="43d0a-102">非同步的商務事件追蹤</span><span class="sxs-lookup"><span data-stu-id="43d0a-102">Asynchronous Business Event Tracking</span></span>
<span data-ttu-id="43d0a-103">非同步 (使用`BufferedEventStream`)-這種模型提供顯著的效能改進。</span><span class="sxs-lookup"><span data-stu-id="43d0a-103">Asynchronous (using `BufferedEventStream`) - This model offers significant performance improvements.</span></span> <span data-ttu-id="43d0a-104">其所使用的 API 與同步模型相似，唯一的差別在於建構函式不同。</span><span class="sxs-lookup"><span data-stu-id="43d0a-104">This uses a similar API to the synchronous model, using only a different constructor.</span></span> <span data-ttu-id="43d0a-105">BufferedEventStream 並非將資料推送至主要匯入資料庫，而是將事件資料以二進位格式累積到記憶體中，再將之以單一資料表記錄的方式插入過渡資料庫 (MessageBox)。</span><span class="sxs-lookup"><span data-stu-id="43d0a-105">Instead of pushing the data into the primary import database, BufferedEventStream accumulates the event data in memory in binary form, and then inserts it as a single table record into an interim database (MessageBox).</span></span> <span data-ttu-id="43d0a-106">事件匯流排服務會讀取 BizTalk 佇列於 MessageBox 資料庫中的資料，然後匯入至主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="43d0a-106">The Event Bus service reads the data queued in the MessageBox database by BizTalk and imports it into the primary import database.</span></span>  
  
 <span data-ttu-id="43d0a-107">為了設定 BAM 以執行非同步作業，事件匯流排服務和呼叫的應用程式 (例如協調流程主控件) 應該在不同的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="43d0a-107">To configure BAM for asynchronous operation, the Event Bus Service and the calling application (e.g. Orchestration Host) should run on different computers.</span></span> <span data-ttu-id="43d0a-108">藉此，呼叫的應用程式即可直接將事件資料交由另一部電腦的 CPU 處理。</span><span class="sxs-lookup"><span data-stu-id="43d0a-108">This allows the calling application to get rid of the event data immediately to be processed using the CPU on a different computer.</span></span>  
  
 <span data-ttu-id="43d0a-109">這種 BAM 拓樸也是所謂的交易一致。</span><span class="sxs-lookup"><span data-stu-id="43d0a-109">This BAM topology is also transaction-consistent.</span></span> <span data-ttu-id="43d0a-110">您所取得的 BAM 資料絕不包含呼叫的應用程式回復的交易資料，因為事件匯流排服務只會從 MessageBox 資料庫讀取已認可的資料。</span><span class="sxs-lookup"><span data-stu-id="43d0a-110">You will never get BAM data for transactions that rolled back in the calling application, because the Event Bus Service only reads the committed data from the MessageBox database.</span></span> <span data-ttu-id="43d0a-111">已認可交易的 BAM 資料將稍微延遲顯示以供查詢及彙總。</span><span class="sxs-lookup"><span data-stu-id="43d0a-111">The BAM data for the transactions that were committed will show up for query and aggregation with small latency.</span></span>  
  
 <span data-ttu-id="43d0a-112">如果發生錯誤，事件匯流排服務將重試幾次、使用逾時、損毀修復邏輯等等。</span><span class="sxs-lookup"><span data-stu-id="43d0a-112">If errors occur, the Event Bus Service will retry a few times, use timeouts, crash recovery logic, and so on.</span></span> <span data-ttu-id="43d0a-113">但是，格式無效的資料都將存入特殊資料表並結束處理。</span><span class="sxs-lookup"><span data-stu-id="43d0a-113">If however the data is in an invalid format, it ends up in special tables.</span></span> <span data-ttu-id="43d0a-114">事件日誌中記錄的事件會指出這類情況。</span><span class="sxs-lookup"><span data-stu-id="43d0a-114">An event occurs in the event log to indicate this condition.</span></span> <span data-ttu-id="43d0a-115">這類額外的失敗情況增添了系統管理上的困難度。</span><span class="sxs-lookup"><span data-stu-id="43d0a-115">This additional failure point increases the difficulty of managing the system.</span></span>  
  
 <span data-ttu-id="43d0a-116">透過程式碼使用非同步方式通常並不難，只要改用 BufferedEventStream 代替 DirectEventStream，並在建構函式中傳遞 MessageBox 的連接字串，而非 BAM 主要匯入資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="43d0a-116">Using the asynchronous approach from code is usually as simple as replacing the DirectEventStream with BufferedEventStream, and passing the connection string to the Message Box in the constructor, instead of the one for BAM Primary Import.</span></span>  
  
 <span data-ttu-id="43d0a-117">使用程式碼建構非同步的商務事件追蹤時，請依循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="43d0a-117">Use the following guidelines regarding asynchronous business event tracking in your code:</span></span>  
  
-   <span data-ttu-id="43d0a-118">如果活動跨越多個應用程式，而且是以非同步方式將資料傳送至 BAM，則即使將 ActivityID 傳送至所有元件，亦應始終使用接續。</span><span class="sxs-lookup"><span data-stu-id="43d0a-118">Always use continuation when the Activity spans multiple applications and you send the data asynchronously to BAM, even if you propagate the ActivityID to all components.</span></span> <span data-ttu-id="43d0a-119">在此情況下，每個應用程式請使用不同的 ActivityID，以唯一字串做為字首來區別 (例如，加上應用程式名稱)。</span><span class="sxs-lookup"><span data-stu-id="43d0a-119">In this case, use a different ActivityID in each application by prefixing it with a unique string (e.g. Application Name).</span></span> <span data-ttu-id="43d0a-120">需要這麼做是因為不同的應用程式可能以隨機順序將資料送達 BAM，而 BAM 必須管制失序的事件以確保查詢和彙總結果正確。</span><span class="sxs-lookup"><span data-stu-id="43d0a-120">This is necessary because the data from different applications might arrive to BAM in random order, and BAM has to manage the out-of-order events to ensure correct Query and Aggregation results.</span></span>  
  
-   <span data-ttu-id="43d0a-121">一般的事件監控方法 (例如 COM+ 鬆散偶合事件或 WMI 事件) 不適用於 BAM，因為這類事件資料與交易無關。</span><span class="sxs-lookup"><span data-stu-id="43d0a-121">The usual methods of event monitoring (e.g. COM+ Loosely Coupled Events or WMI Events) are not applicable for BAM because the event data is independent of the transaction.</span></span> <span data-ttu-id="43d0a-122">例如，您可能只有一筆訂單收入為 $1000，但因儲存至資料庫時重試了 10 次，所以看似收到 10 筆訂單而總金額為 $10,000。</span><span class="sxs-lookup"><span data-stu-id="43d0a-122">For example, it may look like you received 10 purchase orders for a total of $10,000 while there was only one incoming purchase order for $1000, but the attempt to save it to the database failed 10 times.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43d0a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43d0a-123">See Also</span></span>  

 [<span data-ttu-id="43d0a-124">同步的商務事件追蹤</span><span class="sxs-lookup"><span data-stu-id="43d0a-124">Synchronous Business Event Tracking</span></span>](../core/synchronous-business-event-tracking.md)