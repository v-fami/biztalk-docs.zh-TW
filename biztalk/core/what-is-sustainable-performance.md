---
title: 何謂持續性效能？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- reliability, sustainable performance
- performance, goals
- performance, sustainable performance
- planning, performance
- performance, planning
- sustainable performance
ms.assetid: 4b18b976-7714-431f-8976-f40a1016d5f3
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc92770921118778cc20edc66dfbbe5a75e3a647
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003695"
---
# <a name="what-is-sustainable-performance"></a><span data-ttu-id="dcd37-103">何謂持續性效能？</span><span class="sxs-lookup"><span data-stu-id="dcd37-103">What Is Sustainable Performance?</span></span>
<span data-ttu-id="dcd37-104">在規劃和評估系統的持續性時，考慮長期持續性是很重要的。</span><span class="sxs-lookup"><span data-stu-id="dcd37-104">When planning for and estimating system sustainability, it is critical to think in terms of sustainability over the long term.</span></span> <span data-ttu-id="dcd37-105">主要考量為：</span><span class="sxs-lookup"><span data-stu-id="dcd37-105">The primary considerations are:</span></span>  
  
- <span data-ttu-id="dcd37-106">**載入設定檔和效能目標**： 談到負載設定檔與效能目標，您不能有太多細節。</span><span class="sxs-lookup"><span data-stu-id="dcd37-106">**Load Profiles and Performance Goals**: You can't have too much detail when it comes to load profiles and performance goals.</span></span> <span data-ttu-id="dcd37-107">測試與整備憑證將會以能夠長期處理這些負載為基礎。</span><span class="sxs-lookup"><span data-stu-id="dcd37-107">Testing and readiness certification will be based on being able to handle these loads long term.</span></span>  
  
- <span data-ttu-id="dcd37-108">**其他活動與競爭伺服器資源的處理序**： 它不只是訊息負載。</span><span class="sxs-lookup"><span data-stu-id="dcd37-108">**Other Activities and Processes that Compete for Server Resources**: It isn’t just about the message load.</span></span> <span data-ttu-id="dcd37-109">伺服器上還有其他程序與活動，會影響像是資料庫維護與 MessageBox 查詢的效能。</span><span class="sxs-lookup"><span data-stu-id="dcd37-109">There are other processes and activities taking place on the servers that affect performance such as database maintenance and MessageBox queries.</span></span>  
  
- <span data-ttu-id="dcd37-110">**規劃與未規劃的系統中斷與停機時間**： 大量事件與訊息待處理項目可以變更有效的負載設定檔。</span><span class="sxs-lookup"><span data-stu-id="dcd37-110">**Planned and Unplanned System Outages and Downtime**: Floodgate events and message backlog can change the effective load profile.</span></span>  
  
  <span data-ttu-id="dcd37-111">在考慮建置持續性系統及測試以認證這些系統時，請確定將這些因素納入考量並加以規劃。</span><span class="sxs-lookup"><span data-stu-id="dcd37-111">When thinking about building sustainable systems and the tests to certify them, be sure to take these factors into account and plan for them.</span></span>  
  
## <a name="is-your-performance-sustainable"></a><span data-ttu-id="dcd37-112">您的效能可持續嗎？</span><span class="sxs-lookup"><span data-stu-id="dcd37-112">Is Your Performance Sustainable?</span></span>  
 <span data-ttu-id="dcd37-113">在討論 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的效能時，我們定義了如下的最大持續性效能：</span><span class="sxs-lookup"><span data-stu-id="dcd37-113">When discussing performance for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], we define maximum sustainable performance as follows:</span></span>  
  
- <span data-ttu-id="dcd37-114">在生產環境中，系統可無限處理的最高負載訊息流量。</span><span class="sxs-lookup"><span data-stu-id="dcd37-114">The highest load of message traffic that a system can handle indefinitely in a production environment.</span></span>  
  
  <span data-ttu-id="dcd37-115">雖然這看起來很簡單，但是當您將解決方案放置於生產環境之後，在評估於特定硬體上執行的解決方案是否可支援每日出入的負載時，必須考慮許多因素。</span><span class="sxs-lookup"><span data-stu-id="dcd37-115">While this seems simple, there are many factors that you must consider when evaluating whether or not a solution - running on a particular set of hardware - will be able to support the loads experienced day in and day out after you put the solution into production.</span></span>  
  
  <span data-ttu-id="dcd37-116">將解決方案放置於生產環境之前，請先考慮下列因素，以評估此解決方案是否可無限處理最高負載訊息流量：</span><span class="sxs-lookup"><span data-stu-id="dcd37-116">Before you put your solution into production, consider the following factors to evaluate whether the solution can handle the highest load of message traffic indefinitely:</span></span>  
  
- <span data-ttu-id="dcd37-117">預期的效能目標與輸送量/延遲設定檔。</span><span class="sxs-lookup"><span data-stu-id="dcd37-117">Desired Performance Goals and Throughput/Latency profiles.</span></span>  
  
- <span data-ttu-id="dcd37-118">在相同硬體上執行的其他程序，例如：</span><span class="sxs-lookup"><span data-stu-id="dcd37-118">Other Processes Running on the Same Hardware such as:</span></span>  
  
  -   <span data-ttu-id="dcd37-119">正常監控與疑難排解</span><span class="sxs-lookup"><span data-stu-id="dcd37-119">Normal Monitoring and Troubleshooting</span></span>  
  
  -   <span data-ttu-id="dcd37-120">作業資料庫維護，例如，記錄傳送、備份、清除、索引維護，以及統計資料更新。</span><span class="sxs-lookup"><span data-stu-id="dcd37-120">Operational database maintenance such as log shipping, backup, purging, index maintenance, and statistics updates.</span></span>  
  
  -   <span data-ttu-id="dcd37-121">其他應用程式</span><span class="sxs-lookup"><span data-stu-id="dcd37-121">Other Applications</span></span>  
  
- <span data-ttu-id="dcd37-122">計劃與非計劃的系統中斷，例如：</span><span class="sxs-lookup"><span data-stu-id="dcd37-122">Planned and Unplanned System Outages such as:</span></span>  
  
  -   <span data-ttu-id="dcd37-123">夥伴網站停機而封鎖傳送或接收訊息</span><span class="sxs-lookup"><span data-stu-id="dcd37-123">Partner sites down which blocks sending or receiving messages</span></span>  
  
  -   <span data-ttu-id="dcd37-124">定期系統維護停機時間</span><span class="sxs-lookup"><span data-stu-id="dcd37-124">Regular system maintenance down time</span></span>  
  
## <a name="know-your-performance-goals"></a><span data-ttu-id="dcd37-125">瞭解您的效能目標</span><span class="sxs-lookup"><span data-stu-id="dcd37-125">Know Your Performance Goals</span></span>  
 <span data-ttu-id="dcd37-126">在評估解決方案的持續性之前，您必須詳細瞭解預期的生產負載。</span><span class="sxs-lookup"><span data-stu-id="dcd37-126">Before you can evaluate your solution for sustainability, you must have a detailed understanding of the expected production loads.</span></span> <span data-ttu-id="dcd37-127">若未詳細瞭解目標，就無法評估整備。</span><span class="sxs-lookup"><span data-stu-id="dcd37-127">Without a well understood goal, you can't evaluate readiness.</span></span> <span data-ttu-id="dcd37-128">良好的效能目標是很重要的，因為它會引導您的系統測試與憑證策略。</span><span class="sxs-lookup"><span data-stu-id="dcd37-128">A well formed set of performance goals is critical as it will drive your strategies around system testing and certification.</span></span> <span data-ttu-id="dcd37-129">您的效能目標應有下列項目：</span><span class="sxs-lookup"><span data-stu-id="dcd37-129">Your performance goals should have the following elements:</span></span>  
  
-   <span data-ttu-id="dcd37-130">以時間函式來定義效能的曲線。</span><span class="sxs-lookup"><span data-stu-id="dcd37-130">A curve that defines performance as a function of time.</span></span> <span data-ttu-id="dcd37-131">這些函式涵蓋的範圍可從極簡單到非常複雜。</span><span class="sxs-lookup"><span data-stu-id="dcd37-131">These functions can range from extremely simple to very complex.</span></span>  
  
-   <span data-ttu-id="dcd37-132">與效能函式關聯的效能需求。</span><span class="sxs-lookup"><span data-stu-id="dcd37-132">A performance requirement associated with the performance function.</span></span>  
  
-   <span data-ttu-id="dcd37-133">檔案大小與類型的散佈。</span><span class="sxs-lookup"><span data-stu-id="dcd37-133">A distribution of file sizes and types.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="dcd37-134">範例 1</span><span class="sxs-lookup"><span data-stu-id="dcd37-134">Example 1</span></span>  
  
-   <span data-ttu-id="dcd37-135">每天的訊息會從上午 8 點的 0 msgs/sec 開始累積，到中午的 80 msgs/sec，然後在下午 9 點回到 0 msgs/sec，大約會是個鐘形曲線。</span><span class="sxs-lookup"><span data-stu-id="dcd37-135">Each day, messages build up from 0 msgs/sec at 8:00AM to 80 msgs/sec at noon and then back down to 0 msgs/sec at 9:00PM, roughly in the form of a bell curve.</span></span>  
  
-   <span data-ttu-id="dcd37-136">系統對每個訊息沒有特定的延遲需求，但它必須可以處理此負載，加上前一天載入的所有訊息 (例如，系統中斷 24 小時的狀況)，而不會有所落後。</span><span class="sxs-lookup"><span data-stu-id="dcd37-136">The system has no specific latency requirement for each message, but it must be able to process this load, plus all of the previous day’s message load (for example, in the event of a 24 hour system outage) without getting behind.</span></span>  
  
-   <span data-ttu-id="dcd37-137">有三種文件類型：「購物籃」、「補貨」及「庫存要求」。</span><span class="sxs-lookup"><span data-stu-id="dcd37-137">There are three document types: Sales Basket, Back Order, and Stock Request.</span></span> <span data-ttu-id="dcd37-138">「購物籃」文件的大小介於 2 到 10 KB 之間，並於任何指定時間中組成 75% 的訊息計數。</span><span class="sxs-lookup"><span data-stu-id="dcd37-138">Sales Basket documents range in size between 2 and 10 kilobytes and make up 75% of the message counts at any given time.</span></span> <span data-ttu-id="dcd37-139">「補貨」與「庫存要求」文件的大小一律會接近 1 KB，並於任何指定時間中分別組成其餘 10% 與 15% 的訊息計數。</span><span class="sxs-lookup"><span data-stu-id="dcd37-139">Back Order and Stock Request documents are always close to 1 Kilobyte in size and make up the remaining, 10% and 15% of the message count at any given time, respectively.</span></span>  
  
### <a name="example-2"></a><span data-ttu-id="dcd37-140">範例 2</span><span class="sxs-lookup"><span data-stu-id="dcd37-140">Example 2</span></span>  
  
-   <span data-ttu-id="dcd37-141">在每天午夜，需要處理一個 500,000 個訊息的批次。</span><span class="sxs-lookup"><span data-stu-id="dcd37-141">Every night at midnight, a batch of 500,000 messages arrive for processing.</span></span>  
  
-   <span data-ttu-id="dcd37-142">必須在 8 小時內處理完批次中的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="dcd37-142">All messages in the batch must be processed to completion in 8 hours.</span></span>  
  
-   <span data-ttu-id="dcd37-143">所有訊息都是相同類型，平均分散於 10 KB 到 50 KB (含) 之間。</span><span class="sxs-lookup"><span data-stu-id="dcd37-143">All messages are of the same type and are evenly distributed between 10 and 50 Kilobytes, inclusive.</span></span> <span data-ttu-id="dcd37-144">此外，該批次一定包含 10 個目錄類型訊息，每個均為 10 MB，而且必須再分成個別的目錄項目才能處理。</span><span class="sxs-lookup"><span data-stu-id="dcd37-144">In addition, the batch always contains 10 catalog type messages that are 10 megabytes each and must be subdivided into individual catalog entries for processing.</span></span>  
  
### <a name="example-3"></a><span data-ttu-id="dcd37-145">範例 3</span><span class="sxs-lookup"><span data-stu-id="dcd37-145">Example 3</span></span>  
  
-   <span data-ttu-id="dcd37-146">4000 位客戶服務代表在每天上午 8 點登入互動系統，平均每位代表每分鐘會執行 4 個查詢，直到下午 5 點關機為止，每週七天都是如此。</span><span class="sxs-lookup"><span data-stu-id="dcd37-146">Every morning at 8:00AM, 4000 customer service representatives log on to the interactive system and perform, on average, 4 inquiries per representative per minute until closing time at 5:00PM, 7 days per week.</span></span>  
  
-   <span data-ttu-id="dcd37-147">所有的查詢都必須在 2 秒內傳回結果。</span><span class="sxs-lookup"><span data-stu-id="dcd37-147">All inquiries must return results in less than 2 seconds.</span></span>  
  
-   <span data-ttu-id="dcd37-148">所有查詢都是相同類型，其大小平均分散於 500 到 1000 個位元組 (含) 之間。</span><span class="sxs-lookup"><span data-stu-id="dcd37-148">All inquiries are the same type and are evenly distributed between 500 and 1000 bytes in size, inclusive.</span></span>  
  
#### <a name="a-performance-requirement-associated-with-the-performance-function"></a><span data-ttu-id="dcd37-149">與效能函式關聯的效能需求</span><span class="sxs-lookup"><span data-stu-id="dcd37-149">A performance requirement associated with the performance function</span></span>  
 <span data-ttu-id="dcd37-150">繼續上述範例：</span><span class="sxs-lookup"><span data-stu-id="dcd37-150">Continuing with the above examples:</span></span>  
  
-   <span data-ttu-id="dcd37-151">**範例 1 （續）**： 系統對每個訊息，沒有特定的延遲需求，但它必須能夠處理此負載，加上前一天的訊息的所有載入 （例如中斷 24 小時系統），而不會有所落後。</span><span class="sxs-lookup"><span data-stu-id="dcd37-151">**Example 1 (continued)**:  The system has no specific latency requirement for each message, but it must be able to process this load, plus all of the previous day’s message load (for example,, in the event of a 24 hour system outage) without getting behind.</span></span>  
  
-   <span data-ttu-id="dcd37-152">**範例 2 （續）**： 必須在 8 小時內完成處理批次中的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="dcd37-152">**Example 2 (continued)**:  All messages in the batch must be processed to completion in 8 hours.</span></span>  
  
-   <span data-ttu-id="dcd37-153">**範例 3 （續）**： 所有的查詢都必須在 2 秒內傳回結果。</span><span class="sxs-lookup"><span data-stu-id="dcd37-153">**Example 3 (continued)**:  All inquiries must return results in less than 2 seconds.</span></span>  
  
#### <a name="a-distribution-of-file-sizes-and-types"></a><span data-ttu-id="dcd37-154">檔案大小與類型的散佈</span><span class="sxs-lookup"><span data-stu-id="dcd37-154">A distribution of file sizes and types</span></span>  
  
-   <span data-ttu-id="dcd37-155">**範例 1 （續）**： 有三種文件類型: 「 購物籃 」、 「 補貨 」 及 「 庫存要求。</span><span class="sxs-lookup"><span data-stu-id="dcd37-155">**Example 1 (continued)**: There are three document types: Sales Basket, Back Order, and Stock Request.</span></span> <span data-ttu-id="dcd37-156">「購物籃」文件的大小介於 2 到 10 KB 之間，並於任何指定時間中組成 75% 的訊息計數。</span><span class="sxs-lookup"><span data-stu-id="dcd37-156">Sales Basket documents range in size between 2 and 10 kilobytes and make up 75% of the message counts at any given time.</span></span> <span data-ttu-id="dcd37-157">「補貨」與「庫存要求」文件的大小一律會接近 1 KB，並於任何指定時間中分別組成其餘 10% 與 15% 的訊息計數。</span><span class="sxs-lookup"><span data-stu-id="dcd37-157">Back Order and Stock Request documents are always close to 1 Kilobyte in size and make up the remaining, 10% and 15% of the message count at any given time, respectively.</span></span>  
  
-   <span data-ttu-id="dcd37-158">**範例 2 （續）**： 所有訊息都屬於相同類型，平均分散於 10 kb 與 50 Kb，（含) 之間。</span><span class="sxs-lookup"><span data-stu-id="dcd37-158">**Example 2 (continued)**: All messages are of the same type and are evenly distributed between 10 and 50 Kilobytes, inclusive.</span></span> <span data-ttu-id="dcd37-159">此外，該批次一定包含 10 個目錄類型訊息，每個均為 10 MB，而且必須再分成個別的目錄項目才能處理。</span><span class="sxs-lookup"><span data-stu-id="dcd37-159">In addition, the batch always contains 10 catalog type messages that are 10 megabytes each and must be subdivided into individual catalog entries for processing.</span></span>  
  
-   <span data-ttu-id="dcd37-160">**範例 3 （續）**： 所有查詢都是相同類型，平均分散於 500 到 1000 個位元組的大小，（含） 之間。</span><span class="sxs-lookup"><span data-stu-id="dcd37-160">**Example 3 (continued)**: All inquiries are the same type and are evenly distributed between 500 and 1000 bytes in size, inclusive.</span></span>  
  
## <a name="accounting-for-other-processes"></a><span data-ttu-id="dcd37-161">說明其他程序</span><span class="sxs-lookup"><span data-stu-id="dcd37-161">Accounting for Other Processes</span></span>  
 <span data-ttu-id="dcd37-162">除了直接透過 BizTalk 引擎傳送的負載設定檔之外，總是會有其他程序競爭相同硬體上的資源。</span><span class="sxs-lookup"><span data-stu-id="dcd37-162">In addition to the load profiles that pass directly through the BizTalk engine, there are always other processes that compete for resources on the same hardware.</span></span>  <span data-ttu-id="dcd37-163">這些程序將降低系統之整體持續性效能的能力。</span><span class="sxs-lookup"><span data-stu-id="dcd37-163">These other processes will reduce the overall sustainable performance capabilities of the system.</span></span> <span data-ttu-id="dcd37-164">資料庫維護可能是這類程序的最常見範例。</span><span class="sxs-lookup"><span data-stu-id="dcd37-164">Database maintenance is probably the most common example of this type of process.</span></span>  
  
 <span data-ttu-id="dcd37-165">每個資料庫 (大型或小型) 都需要定期作業維護，例如，記錄傳送、備份、封存，以及清除。</span><span class="sxs-lookup"><span data-stu-id="dcd37-165">Every database, large or small, requires periodic operational maintenance such as log shipping, backup, archive, and purging.</span></span> <span data-ttu-id="dcd37-166">監控與疑難排解是您在定義和認證何謂持續性時必須考慮的其他作業範例。</span><span class="sxs-lookup"><span data-stu-id="dcd37-166">Monitoring and troubleshooting are other examples of operations that you must take into account when defining and certifying what is sustainable.</span></span> <span data-ttu-id="dcd37-167">例如，查詢 MessageBox (例如，透過管理主控台 [群組中樞] 頁面) 來查看過去 24 小時有多少指定類型的訊息遭到擱置，需要 SQL Server 已用來處理訊息的資源。</span><span class="sxs-lookup"><span data-stu-id="dcd37-167">For example, querying the MessageBox (for example, via the administration console Group Hub page) to see how many messages of a given type have been suspended in the last 24 hours requires resources from SQL Server that could otherwise have been used to process messages.</span></span>  
  
 <span data-ttu-id="dcd37-168">下面是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中通常對整體持續性最有影響的活動清單：</span><span class="sxs-lookup"><span data-stu-id="dcd37-168">Following is a list of activities that will typically have the most effect on overall sustainability in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:</span></span>  
  
- <span data-ttu-id="dcd37-169">**記錄傳送與備份**。</span><span class="sxs-lookup"><span data-stu-id="dcd37-169">**Log Shipping and Backup**.</span></span> <span data-ttu-id="dcd37-170">做為包含 SQL Server 之多數災害復原計劃的一部分，您必須定期對所有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組資料庫執行記錄傳送與備份。</span><span class="sxs-lookup"><span data-stu-id="dcd37-170">As part of most disaster recovery plans involving SQL Server, you must perform log shipping and backup periodically for all of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group databases.</span></span> <span data-ttu-id="dcd37-171">如需詳細資訊，請參閱 <<c0> [ 備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="dcd37-171">For more information, see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md).</span></span> <span data-ttu-id="dcd37-172">另請參閱[記錄傳送](../core/log-shipping.md)。</span><span class="sxs-lookup"><span data-stu-id="dcd37-172">Also see [Log Shipping](../core/log-shipping.md).</span></span>  
  
- <span data-ttu-id="dcd37-173">**封存和清除追蹤資料**。</span><span class="sxs-lookup"><span data-stu-id="dcd37-173">**Archiving and Purging Tracking Data**.</span></span> <span data-ttu-id="dcd37-174">除了整體記錄傳送與備份計劃，「 BizTalk 追蹤 (BizTalkDTADb) 資料庫有它自己的封存和清除區域;如需詳細資訊，請參閱 <<c0> [ 封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)。</span><span class="sxs-lookup"><span data-stu-id="dcd37-174">In addition to the overall log shipping and backup plan, the BizTalk Tracking (BizTalkDTADb) database has its own archive and purge regimes; for more information, see [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md).</span></span> <span data-ttu-id="dcd37-175">從 BizTalk 追蹤資料庫封存和清除資料的速度尤其重要，因為封存和清除 BizTalk 追蹤資料庫通常是使用追蹤時的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="dcd37-175">The speed at which data can be archived and purged from the BizTalk Tracking database is especially important since archiving and purging of the BizTalk Tracking database is typically a bottleneck when tracking is in use.</span></span>  
  
- <span data-ttu-id="dcd37-176">**系統查詢**。</span><span class="sxs-lookup"><span data-stu-id="dcd37-176">**System Queries**.</span></span> <span data-ttu-id="dcd37-177">使用 API 或 BizTalk Server 管理主控台 UI 對系統執行各種類型的查詢，將會影響持續性效能。</span><span class="sxs-lookup"><span data-stu-id="dcd37-177">Using APIs or the BizTalk Server Administration Console UI to run various types of queries against the system will affect sustainable performance.</span></span>  
  
- <span data-ttu-id="dcd37-178">**MessageBox 維護**。</span><span class="sxs-lookup"><span data-stu-id="dcd37-178">**MessageBox Maintenance**.</span></span> <span data-ttu-id="dcd37-179">有許多 SQL 工作是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 核心功能的一部分，可藉由清除已完成處理的訊息與執行個體來維護 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="dcd37-179">There are a number of SQL jobs that are part of the core functionality of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that maintain the MessageBox database by cleaning up messages and instances that have finished processing.</span></span> <span data-ttu-id="dcd37-180">做為核心引擎的一部分，完成這些工作的速度是衡量持續性的關鍵因素。</span><span class="sxs-lookup"><span data-stu-id="dcd37-180">As part of the core engine, the speed at which these jobs can complete is a key factor in gauging sustainability.</span></span> <span data-ttu-id="dcd37-181">如需有關這些作業和其角色的詳細資訊，請參閱 <<c0> [ 維護 BizTalk Server1](../core/maintaining-biztalk-server1.md)。</span><span class="sxs-lookup"><span data-stu-id="dcd37-181">For more information about these jobs and their role, see [Maintaining BizTalk Server1](../core/maintaining-biztalk-server1.md).</span></span>  
  
- <span data-ttu-id="dcd37-182">**解決方案部署活動**。</span><span class="sxs-lookup"><span data-stu-id="dcd37-182">**Solution Deployment Activities**.</span></span> <span data-ttu-id="dcd37-183">在部署、繫結和啟動新應用程式或現有應用程式的新版本時，額外的負載是放置於 BizTalk 上，像是在 MessageBox 資料庫上建立新訂閱。</span><span class="sxs-lookup"><span data-stu-id="dcd37-183">When deploying, binding, and starting new applications or new versions of existing applications, additional load is placed on BizTalk such as the creation of new subscriptions on the MessageBox database(s).</span></span> <span data-ttu-id="dcd37-184">部署應用程式之後，已處理的訊息將競爭資源，因而影響現有應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="dcd37-184">After applications are deployed, the messages being processed will compete for resources and thereby affect the performance of the existing applications.</span></span>  
  
  <span data-ttu-id="dcd37-185">對於其中的每個區域，您必須詢問：若要將這些活動的衝擊最小化，您有何建議？</span><span class="sxs-lookup"><span data-stu-id="dcd37-185">For each of these areas, you need to ask: What is your recommendation to minimize the impact of these activities?</span></span> <span data-ttu-id="dcd37-186">例如，他們應該計劃在凌晨 3 點執行它們嗎？</span><span class="sxs-lookup"><span data-stu-id="dcd37-186">For example, should they plan to run them at 3am?</span></span>  
  
## <a name="considering-planned-and-unplanned-outages"></a><span data-ttu-id="dcd37-187">考慮計劃與非計劃的中斷</span><span class="sxs-lookup"><span data-stu-id="dcd37-187">Considering Planned and Unplanned Outages</span></span>  
 <span data-ttu-id="dcd37-188">中斷對於系統效能的影響，會根據經歷中斷的系統不同而變動，不過，最常見的結果如下：</span><span class="sxs-lookup"><span data-stu-id="dcd37-188">The effects that outages have on the system performance will vary depending on the system experiencing the outage, however the most common consequences are:</span></span>  
  
- <span data-ttu-id="dcd37-189">**大量事件**。</span><span class="sxs-lookup"><span data-stu-id="dcd37-189">**Floodgate Events**.</span></span> <span data-ttu-id="dcd37-190">當系統停機一段長時間時，訊息會累積，然後在系統再次恢復運作時全部同時抵達以進行處理。</span><span class="sxs-lookup"><span data-stu-id="dcd37-190">When systems are down for some length of time, messages can build up and then arrive all at once for processing once the systems are functional again.</span></span>  <span data-ttu-id="dcd37-191">例如，若在 BizTalk 上執行的應用程式會透過 MSMQ 接收訊息，且該應用程式停機一段時間，則訊息會累積在佇列中，以等待收取。</span><span class="sxs-lookup"><span data-stu-id="dcd37-191">For example, if an application running on BizTalk receives messages via MSMQ, and that application is down for some time, messages build up in the queues waiting to be picked up.</span></span> <span data-ttu-id="dcd37-192">當應用程式再度啟動時，就像有大量訊息「全部同時」抵達。</span><span class="sxs-lookup"><span data-stu-id="dcd37-192">When the application is started up again, it is as if a large number of messages arrived "all at once."</span></span>  
  
- <span data-ttu-id="dcd37-193">**訊息待處理項目**。</span><span class="sxs-lookup"><span data-stu-id="dcd37-193">**Message Backlog**.</span></span> <span data-ttu-id="dcd37-194">當訊息要傳送至的系統停機時，通常會有使用其他資源的重試週期。</span><span class="sxs-lookup"><span data-stu-id="dcd37-194">When systems to which messages are sent are down, there is typically a retry cycle that is employed that uses additional resources.</span></span> <span data-ttu-id="dcd37-195">之後重試循環已用盡，則通常會擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="dcd37-195">After the retry cycle is exhausted, then messages are typically suspended.</span></span> <span data-ttu-id="dcd37-196">然後，當停機的系統恢復線上運作時，就會發生大量事件的類型，現在可以繼續和 (或) 成功地傳送大量訊息。</span><span class="sxs-lookup"><span data-stu-id="dcd37-196">Then the downed systems come back on line, a type of floodgate event occurs where large numbers of messages can now be resumed and/or successfully sent.</span></span>  
  
  <span data-ttu-id="dcd37-197">當然，像是定期排程維護的任何計劃中斷，在設計和認證系統時都必須列入考慮。</span><span class="sxs-lookup"><span data-stu-id="dcd37-197">Certainly any planned outages such as regularly scheduled maintenance must be taken into consideration when designing and certifying a system.</span></span> <span data-ttu-id="dcd37-198">同時建議您考慮分析非計劃的中斷及其影響。</span><span class="sxs-lookup"><span data-stu-id="dcd37-198">It is also recommended that an analysis of unplanned outages and their effects be considered.</span></span>  
  
  <span data-ttu-id="dcd37-199">識別可能發生的中斷類型，藉由評估風險層級 (也就是可能性乘以嚴重性) 和較高風險中斷的持續時間與影響 (例如，大量事件、已擱置的訊息數量、積存等) 將它們排列等級，將指示系統可能發生中斷的可能性。</span><span class="sxs-lookup"><span data-stu-id="dcd37-199">Identifying the types of outages that can occur, ranking them by estimated risk level (that is, probability times severity), and estimating the duration and effect (for example, floodgate events, suspended message volume, backlog, etc.) of the higher risk outages will indicate a desired system capability should the outages take place.</span></span> <span data-ttu-id="dcd37-200">任何存放與轉寄、以傳訊為基礎的非同步系統 (如 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)])，必須設計為將處理足以涵蓋計劃與非計劃之中斷的「空餘空間」。</span><span class="sxs-lookup"><span data-stu-id="dcd37-200">Any store-and-forward, messaging-based asynchronous system, such as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], should be designed will processing "headroom" sufficient to cope with planned and unplanned outages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd37-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcd37-201">See Also</span></span>  
 <span data-ttu-id="dcd37-202">[引擎持續性和耐久性](../core/engine-persistence-and-durability.md) </span><span class="sxs-lookup"><span data-stu-id="dcd37-202">[Engine Persistence and Durability](../core/engine-persistence-and-durability.md) </span></span>  
 <span data-ttu-id="dcd37-203">[依階段的專案計劃建議](../core/project-planning-recommendations-by-phase.md) </span><span class="sxs-lookup"><span data-stu-id="dcd37-203">[Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md) </span></span>  
 <span data-ttu-id="dcd37-204">[測量最大持續性引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="dcd37-204">[Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md) </span></span>  
 <span data-ttu-id="dcd37-205">[測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="dcd37-205">[Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md) </span></span>  
 <span data-ttu-id="dcd37-206">[擴充您的解決方案](../core/scaling-your-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="dcd37-206">[Scaling Your Solutions](../core/scaling-your-solutions.md) </span></span>  
 <span data-ttu-id="dcd37-207">[找出效能瓶頸](../core/identifying-performance-bottlenecks.md) </span><span class="sxs-lookup"><span data-stu-id="dcd37-207">[Identifying Performance Bottlenecks](../core/identifying-performance-bottlenecks.md) </span></span>  
 [<span data-ttu-id="dcd37-208">引擎效能和容量</span><span class="sxs-lookup"><span data-stu-id="dcd37-208">Engine Performance and Capacity</span></span>](../core/engine-performance-and-capacity.md)