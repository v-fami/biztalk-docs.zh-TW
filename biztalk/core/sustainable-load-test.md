---
title: 持續性負載測試 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sustainable load test
- LoadGen tool, sustainable load test
ms.assetid: a9d752ff-aff1-4445-8af5-8f84609880e2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d17d8d38323f7933c8e60cb2b87e0ec312d270c5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015647"
---
# <a name="sustainable-load-test"></a><span data-ttu-id="72bf2-102">持續性負載測試</span><span class="sxs-lookup"><span data-stu-id="72bf2-102">Sustainable Load Test</span></span>
<span data-ttu-id="72bf2-103">本主題中的資訊是指在所說明的測試[測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="72bf2-103">The information in this topic refers to the tests explained in [Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md).</span></span>  
  
 <span data-ttu-id="72bf2-104">在第一個測試中，系統由 MST 驅動，所以可以觀察狀況良好的系統。</span><span class="sxs-lookup"><span data-stu-id="72bf2-104">For the first test, the system was driven to MST so that observations of a healthy system can be made.</span></span>  
  
 <span data-ttu-id="72bf2-105">下圖顯示使用這個方法來尋找測試系統的最大持續性輸送量之後的幾個主要指示器。</span><span class="sxs-lookup"><span data-stu-id="72bf2-105">The following graph shows key indicators after using this approach to find the maximum sustainable throughput of the test system.</span></span>  
  
 <span data-ttu-id="72bf2-106">**持續性負載測試的負載概述**</span><span class="sxs-lookup"><span data-stu-id="72bf2-106">**Load profile of sustainable load test**</span></span>  
  
 <span data-ttu-id="72bf2-107">![效能監控測量持續性負載](../core/media/bts06-sustainable-load.gif "BTS06_Sustainable_Load")</span><span class="sxs-lookup"><span data-stu-id="72bf2-107">![Performance monitor measuring sustainable load](../core/media/bts06-sustainable-load.gif "BTS06_Sustainable_Load")</span></span>  
  
 <span data-ttu-id="72bf2-108">這個圖表顯示在經過一小時的測試後，多工緩衝處理的深度穩定且未成長。</span><span class="sxs-lookup"><span data-stu-id="72bf2-108">This graph shows that, for the hour of the test, the spool depth was stable and not growing:</span></span>  
  
- <span data-ttu-id="72bf2-109">圖表上方的黑線顯示系統每秒接收的總訊息數 (例如，兩部接收伺服器的每秒總訊息數)。</span><span class="sxs-lookup"><span data-stu-id="72bf2-109">The black lines at the top of the graph show the total messages received per second by the system (for example, for both of the receiving servers).</span></span>  
  
- <span data-ttu-id="72bf2-110">圖表下方的線條表示每部 SQL 伺服器上的 MessageBox 多工緩衝處理深度。</span><span class="sxs-lookup"><span data-stu-id="72bf2-110">The lines at the bottom of the graph indicate the MessageBox spool depth on each of the SQL Servers.</span></span>  
  
  <span data-ttu-id="72bf2-111">一旦系統到達穩定的多工緩衝處理深度上限時，就會用每秒接收的訊息數來測量 MST。</span><span class="sxs-lookup"><span data-stu-id="72bf2-111">Once the system is driven to the point of the maximum stable spool depth, MST is measured by the number of messages received per second.</span></span> <span data-ttu-id="72bf2-112">在此實例所描述的硬體上，會達到每秒 290 個訊息的 MST。</span><span class="sxs-lookup"><span data-stu-id="72bf2-112">For this scenario, on the hardware described, an MST of 290 messages per second was achieved.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72bf2-113">經過一段時間，一旦系統到達多工緩衝處理深度不再穩定的點時，會超過 MST。</span><span class="sxs-lookup"><span data-stu-id="72bf2-113">Once the system is driven to a point where the spool depth is no longer stable over time, MST has been exceeded.</span></span> <span data-ttu-id="72bf2-114">可能需要執行多個不同負載的測試，以評估多工緩衝處理仍為穩定的負載上限，及系統可處理的訊息積存，而不造成其他的訊息積存。</span><span class="sxs-lookup"><span data-stu-id="72bf2-114">Several test runs with varying load may be required to evaluate the maximum load at which spool depth remains stable and your system can handle the message backlog without incurring additional message backlog.</span></span>  
  
 <span data-ttu-id="72bf2-115">任何 BizTalk 部署效能分析都應該要檢查某些主要指示器，以瞭解資源的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="72bf2-115">Part of any analysis of a BizTalk deployment performance should include checking some key indicators to understand resource bottlenecks.</span></span> <span data-ttu-id="72bf2-116">在持續性輸送量上限之下所執行部署使用的主要量值及其值如下：</span><span class="sxs-lookup"><span data-stu-id="72bf2-116">The key measures and their values used for this deployment running under maximum sustainable throughput were as follows:</span></span>  
  
 <span data-ttu-id="72bf2-117">**CPU 使用率**</span><span class="sxs-lookup"><span data-stu-id="72bf2-117">**CPU Utilization**</span></span>  
  
|<span data-ttu-id="72bf2-118">[伺服器]</span><span class="sxs-lookup"><span data-stu-id="72bf2-118">Server</span></span>|<span data-ttu-id="72bf2-119">平均的 CPU 使用</span><span class="sxs-lookup"><span data-stu-id="72bf2-119">Average CPU Utilization</span></span>|  
|------------|-----------------------------|  
|<span data-ttu-id="72bf2-120">BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="72bf2-120">BizTalk Servers</span></span>|<span data-ttu-id="72bf2-121">55%</span><span class="sxs-lookup"><span data-stu-id="72bf2-121">55%</span></span>|  
|<span data-ttu-id="72bf2-122">SQL Server (主要 MessageBox 伺服器)</span><span class="sxs-lookup"><span data-stu-id="72bf2-122">SQL Server (Master MessageBox Server)</span></span>|<span data-ttu-id="72bf2-123">76%</span><span class="sxs-lookup"><span data-stu-id="72bf2-123">76%</span></span>|  
|<span data-ttu-id="72bf2-124">SQL Server (其他 MessageBox 伺服器)</span><span class="sxs-lookup"><span data-stu-id="72bf2-124">SQL Server (Other MessageBox Servers)</span></span>|<span data-ttu-id="72bf2-125">83%</span><span class="sxs-lookup"><span data-stu-id="72bf2-125">83%</span></span>|  
  
 <span data-ttu-id="72bf2-126">**實體磁碟閒置時間**</span><span class="sxs-lookup"><span data-stu-id="72bf2-126">**Physical Disk Idle Time**</span></span>  
  
|<span data-ttu-id="72bf2-127">[伺服器]</span><span class="sxs-lookup"><span data-stu-id="72bf2-127">Server</span></span>|<span data-ttu-id="72bf2-128">平均磁碟閒置時間</span><span class="sxs-lookup"><span data-stu-id="72bf2-128">Average Disk Idle Time</span></span>|  
|------------|----------------------------|  
|<span data-ttu-id="72bf2-129">所有 SQL Server 的平均數</span><span class="sxs-lookup"><span data-stu-id="72bf2-129">Average for all SQL Servers</span></span>|<span data-ttu-id="72bf2-130">69%</span><span class="sxs-lookup"><span data-stu-id="72bf2-130">69%</span></span>|  
  
 <span data-ttu-id="72bf2-131">**SQL Server 上的 SQL 鎖定**</span><span class="sxs-lookup"><span data-stu-id="72bf2-131">**SQL Locks on SQL Server**</span></span>  
  
|<span data-ttu-id="72bf2-132">參數</span><span class="sxs-lookup"><span data-stu-id="72bf2-132">Parameter</span></span>|<span data-ttu-id="72bf2-133">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="72bf2-133">Value</span></span>|  
|---------------|-----------|  
|<span data-ttu-id="72bf2-134">每秒平均封鎖逾時總數 (每部 SQL Server)</span><span class="sxs-lookup"><span data-stu-id="72bf2-134">Average Total Lock Timeouts per second (per SQL Server)</span></span>|<span data-ttu-id="72bf2-135">1980</span><span class="sxs-lookup"><span data-stu-id="72bf2-135">1980</span></span>|  
|<span data-ttu-id="72bf2-136">平均封鎖等候總時數 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="72bf2-136">Average Total Lock Wait Time (ms)</span></span>|<span data-ttu-id="72bf2-137">495</span><span class="sxs-lookup"><span data-stu-id="72bf2-137">495</span></span>|  
  
 <span data-ttu-id="72bf2-138">在這個測試期間，BizTalk 或 SQL Server 應用程式日誌中並未產生任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="72bf2-138">During this test no errors were generated in the BizTalk or SQL Server application log.</span></span>  
  
 <span data-ttu-id="72bf2-139">從這個資料中，我們可以得到下列結論：</span><span class="sxs-lookup"><span data-stu-id="72bf2-139">From this data, we can draw the following conclusions:</span></span>  
  
- <span data-ttu-id="72bf2-140">系統中沒有明顯的資源瓶頸發生。</span><span class="sxs-lookup"><span data-stu-id="72bf2-140">There are no obvious resource bottlenecks in our system.</span></span>  
  
- <span data-ttu-id="72bf2-141">所有的指示器都在狀態良好的限度內。</span><span class="sxs-lookup"><span data-stu-id="72bf2-141">All of these indicators are well within healthy limits.</span></span>  
  
- <span data-ttu-id="72bf2-142">CPU 及磁碟閒置時間顯示有大量的空間，甚至沒有接近限制。</span><span class="sxs-lookup"><span data-stu-id="72bf2-142">CPU and Disk Idle Times show that there is plenty of headroom and they are not even close to being pegged.</span></span>  
  
- <span data-ttu-id="72bf2-143">SQL 鎖定指示器看起來正常， **Lock Timeouts/sec**不是問題開始，直到解決 5000 個 （取決於您的 SQL Server) 的鎖定等候 1 秒的時間也是狀況良好。</span><span class="sxs-lookup"><span data-stu-id="72bf2-143">The SQL lock indicators look good, **Lock Timeouts/sec** doesn’t start to become an issue until around 5000 or so (depending on your SQL Server) and Lock Wait times under 1 second are also healthy.</span></span>  
  
  <span data-ttu-id="72bf2-144">現在我們已經示範如何尋找持續性輸送量上限的方法，並已經看到持續狀態良好的系統主要指示器應該長什麼樣子，現在我們要探討某些與系統相關的行為，該系統接收的速度比處理及回收記憶體要快。</span><span class="sxs-lookup"><span data-stu-id="72bf2-144">Now that we have shown how to find the maximum sustainable throughput and seen what the key indicators look like for a sustainable, healthy system, let’s explore some behavior associated with a system that is receiving faster than it is processing and collecting garbage.</span></span> <span data-ttu-id="72bf2-145">請繼續進行[加速負載測試](../core/overdrive-load-test.md)。</span><span class="sxs-lookup"><span data-stu-id="72bf2-145">Proceed to [Overdrive Load Test](../core/overdrive-load-test.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72bf2-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72bf2-146">See Also</span></span>  
 <span data-ttu-id="72bf2-147">[測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span><span class="sxs-lookup"><span data-stu-id="72bf2-147">[Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span></span>  
 [<span data-ttu-id="72bf2-148">加速負載測試</span><span class="sxs-lookup"><span data-stu-id="72bf2-148">Overdrive Load Test</span></span>](../core/overdrive-load-test.md)