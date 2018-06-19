---
title: 大量負載測試 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LoadGen tool, simulating floodgate events
- performance, floodgate peaks
- floodgate events [performance]
ms.assetid: 937f2478-339b-4ae2-b107-56f3a4bfc579
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74954d8b94207832ceee5bbb699a7de1a245f61b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246206"
---
# <a name="floodgate-load-test"></a><span data-ttu-id="2c624-102">大量負載測試</span><span class="sxs-lookup"><span data-stu-id="2c624-102">Floodgate Load Test</span></span>
<span data-ttu-id="2c624-103">本主題中的資訊是指中所說明的測試[測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="2c624-103">The information in this topic refers to the tests explained in [Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md).</span></span>  
  
## <a name="what-causes-floodgate-events"></a><span data-ttu-id="2c624-104">什麼造成了大量事件？</span><span class="sxs-lookup"><span data-stu-id="2c624-104">What Causes Floodgate Events?</span></span>  
 <span data-ttu-id="2c624-105">有許多案例僅少數高尖峰時段 (也稱為**大量事件**) 的訊息抵達系統每一天。</span><span class="sxs-lookup"><span data-stu-id="2c624-105">There are a number of scenarios where just a few large peaks (also known as **floodgate events**) of messages arrive at the system each day.</span></span> <span data-ttu-id="2c624-106">在這些尖峰期間，輸送量可能相當低。</span><span class="sxs-lookup"><span data-stu-id="2c624-106">Between these peaks, the throughput can be very low.</span></span> <span data-ttu-id="2c624-107">這類實例的範例包含：</span><span class="sxs-lookup"><span data-stu-id="2c624-107">Examples of these types of scenarios include:</span></span>  
  
-   <span data-ttu-id="2c624-108">例如，股市開始與結束時的股票交易</span><span class="sxs-lookup"><span data-stu-id="2c624-108">Equity trading, for example, at market open and market close</span></span>  
  
-   <span data-ttu-id="2c624-109">例如，每日交易結束期間進行對帳的銀行系統</span><span class="sxs-lookup"><span data-stu-id="2c624-109">Banking systems, for example, during end of day transaction reconciliation</span></span>  
  
 <span data-ttu-id="2c624-110">其他的事件類型會造成與大量事件類似的積存行為。</span><span class="sxs-lookup"><span data-stu-id="2c624-110">Other types of events can cause backlog behavior similar to floodgate events.</span></span> <span data-ttu-id="2c624-111">例如，若夥伴傳送位址離線而必須重試和 (或) 擱置該位址的訊息，則會導致積存一直累積。</span><span class="sxs-lookup"><span data-stu-id="2c624-111">For example, if a partner send address goes off line so that messages destined for that address must be re-tried and/or suspended, this can result in backlog building up.</span></span> <span data-ttu-id="2c624-112">當夥伴重新上線時，可能就有大量的擱置訊息需要重送，而造成另一種類型的大量事件。</span><span class="sxs-lookup"><span data-stu-id="2c624-112">When the partner comes back on line, there may be a large number of suspended messages that need to be resumed, resulting in another type of floodgate event.</span></span> <span data-ttu-id="2c624-113">以下的系統測試會說明此行為。</span><span class="sxs-lookup"><span data-stu-id="2c624-113">The following test of the system illustrates this behavior.</span></span>  
  
## <a name="simulating-a-floodgate-event"></a><span data-ttu-id="2c624-114">模擬大量事件</span><span class="sxs-lookup"><span data-stu-id="2c624-114">Simulating a Floodgate Event</span></span>  
 <span data-ttu-id="2c624-115">對於此測試，系統一開始的運作大約是可維持之輸送量上限的一半，所以當然是相當穩定。</span><span class="sxs-lookup"><span data-stu-id="2c624-115">For this test, the system was initially driven at around half the maximum sustainable throughput which of course was very stable.</span></span> <span data-ttu-id="2c624-116">接著，若模擬大量事件，負載產生工具會設定在短時間內，以 410 msgs/sec 進行傳送 (與加速測試一樣)。</span><span class="sxs-lookup"><span data-stu-id="2c624-116">Then, to simulate a floodgate event, the load generation tool was configured to send in about 410 msgs/sec for a short period of time (the same as for the overdrive test).</span></span> <span data-ttu-id="2c624-117">以下所示的為測量每秒接收的訊息及多工緩衝處理深度而產生的負載設定檔。</span><span class="sxs-lookup"><span data-stu-id="2c624-117">The resultant load profile measuring messages received per second and spool depth is displayed below.</span></span>  
  
 <span data-ttu-id="2c624-118">**大量負載測試的負載設定檔**</span><span class="sxs-lookup"><span data-stu-id="2c624-118">**Load profile of floodgate load test**</span></span>  
  
 <span data-ttu-id="2c624-119">![大量負載的效能監視器顯示](../core/media/bts06-floodgate-load.gif "BTS06_Floodgate_Load")</span><span class="sxs-lookup"><span data-stu-id="2c624-119">![Performance monitor display of floodgate load](../core/media/bts06-floodgate-load.gif "BTS06_Floodgate_Load")</span></span>  
  
 <span data-ttu-id="2c624-120">請注意，從圖中看到多工緩衝處理資料表在大量事件期間快速累積積存。</span><span class="sxs-lookup"><span data-stu-id="2c624-120">Note from the graph that the spool tables quickly built up a backlog during the floodgate event.</span></span> <span data-ttu-id="2c624-121">不過，由於事件的時間相當短，且事件之後的後續接收速率低於可維持速率的上限，因此清除工作能夠執行並從事件復原，而不用要求系統停止接收。</span><span class="sxs-lookup"><span data-stu-id="2c624-121">However, because the event was relatively short lived and the subsequent receive rate after the event was below the maximum sustainable rate, the cleanup jobs were able to run and recover from the event without requiring a system receive outage.</span></span> <span data-ttu-id="2c624-122">對於這個特殊測試，MessageBox 是位於 SQL Server 2005 上；此測試從開始到結束大約需 45 分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="2c624-122">For this particular test, the MessageBox was housed on SQL Server 2005; the duration of this test from beginning to end was approximately 45 minutes.</span></span>  
  
 <span data-ttu-id="2c624-123">當然，每個系統都是不同的，因此您所需的時間也可能不一樣。</span><span class="sxs-lookup"><span data-stu-id="2c624-123">Of course, every system is different, so "your mileage will vary."</span></span> <span data-ttu-id="2c624-124">確定可以復原的最佳方式是，實際執行前先測試具有代表性的負載。</span><span class="sxs-lookup"><span data-stu-id="2c624-124">The best way to verify that you can recover is to test with a representative load before going into production.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c624-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c624-125">See Also</span></span>  
 <span data-ttu-id="2c624-126">[測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span><span class="sxs-lookup"><span data-stu-id="2c624-126">[Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span></span>  
 <span data-ttu-id="2c624-127">[使用設定儀表板，以便讓 BizTalk Server 效能調整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) </span><span class="sxs-lookup"><span data-stu-id="2c624-127">[Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) </span></span>  
 <span data-ttu-id="2c624-128">[加速負載測試](../core/overdrive-load-test.md) </span><span class="sxs-lookup"><span data-stu-id="2c624-128">[Overdrive Load Test](../core/overdrive-load-test.md) </span></span>  
 [<span data-ttu-id="2c624-129">持續性負載測試</span><span class="sxs-lookup"><span data-stu-id="2c624-129">Sustainable Load Test</span></span>](../core/sustainable-load-test.md)