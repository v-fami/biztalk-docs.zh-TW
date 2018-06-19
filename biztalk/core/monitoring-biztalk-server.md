---
title: 監視的健全狀況和效能，使用內建的工具 |Microsoft 文件
description: 可用性、 健全狀況和效能監視在 BizTalk Server 和監視 SQL Agent 工作
ms.custom: ''
ms.date: 01/14/2016
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96e244dc-b826-4a9f-a4e1-6dabc41eb144
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6652c962d8ef522128dfb4c9febeca55ce42669
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22265358"
---
# <a name="monitoring-biztalk-server"></a><span data-ttu-id="5cd31-103">監控 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="5cd31-103">Monitoring BizTalk Server</span></span>
<span data-ttu-id="5cd31-104">定期監控 BizTalk Server 應用程式和基礎結構並解決所發現的任何問題，有助於維持您的 BizTalk Server 應用程式讓使用者存取。</span><span class="sxs-lookup"><span data-stu-id="5cd31-104">Monitoring your BizTalk Server applications and infrastructure on a regular basis and resolving any issues that you find helps to keep your BizTalk Server applications accessible to your users.</span></span> <span data-ttu-id="5cd31-105">監控的目標是要讓例外情形未獲得偵測 (亦即未解決) 的時間減至最少。</span><span class="sxs-lookup"><span data-stu-id="5cd31-105">The goal of monitoring is to minimize the amount of time that an exception goes undetected and, therefore, unresolved.</span></span> <span data-ttu-id="5cd31-106">此外，您也可以使用監控來偵測可能造成例外情形的狀況。</span><span class="sxs-lookup"><span data-stu-id="5cd31-106">Additionally, you can use monitoring to help detect situations that might cause an exception.</span></span>  
  
 <span data-ttu-id="5cd31-107">當您監控 BizTalk Server 時，您應該尋找任何非預期或異常的行為。</span><span class="sxs-lookup"><span data-stu-id="5cd31-107">When monitoring BizTalk Server, you should look for any unexpected or anomalous behavior.</span></span> <span data-ttu-id="5cd31-108">監控可以是手動或自動程序。</span><span class="sxs-lookup"><span data-stu-id="5cd31-108">Monitoring can be either a manual or automatic process.</span></span> <span data-ttu-id="5cd31-109">您可以監視使用 BizTalk Server 基礎結構使用 BizTalk Server 管理主控台的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="5cd31-109">You can monitor use the health of your BizTalk Server infrastructure using the BizTalk Server Administration Console.</span></span> <span data-ttu-id="5cd31-110">您可以使用 BizTalk Server 管理主控台來監視 BizTalk Server 應用程式的健全狀況和執行根本原因分析，以識別任何問題的根本原因。</span><span class="sxs-lookup"><span data-stu-id="5cd31-110">You can use the BizTalk Server Administration Console to monitor the health of your BizTalk Server applications and perform root-cause analysis to identify the underlying cause of any problems.</span></span> <span data-ttu-id="5cd31-111">。</span><span class="sxs-lookup"><span data-stu-id="5cd31-111">.</span></span> <span data-ttu-id="5cd31-112">當監控 BizTalk Server 時，請牢記下列幾個要點：</span><span class="sxs-lookup"><span data-stu-id="5cd31-112">When monitoring BizTalk Server, keep these points in mind:</span></span>  
  
-   <span data-ttu-id="5cd31-113">您的基礎結構可能狀況良好，但應用程式可能不是 (例如，應用程式收到無效的訊息，而且無法處理這些訊息)。</span><span class="sxs-lookup"><span data-stu-id="5cd31-113">Your infrastructure could be healthy, but your applications might not be (for example, they are receiving invalid messages and are unable to process them).</span></span>  
  
-   <span data-ttu-id="5cd31-114">您的基礎結構可能狀況不好，但應用程式可能正常運作 (例如，如果某部伺服器停機，但是有指派足夠的伺服器給主控件來接管負載)。</span><span class="sxs-lookup"><span data-stu-id="5cd31-114">Your infrastructure could be unhealthy, but your applications might be running fine (for example, if a server is down, but there are enough servers assigned to the host to take over the load).</span></span>  
  
-   <span data-ttu-id="5cd31-115">基礎結構問題可能會以應用程式問題的形式出現 (例如，由於伺服器停機，造成訊息的處理速度不夠快)。</span><span class="sxs-lookup"><span data-stu-id="5cd31-115">An infrastructure problem could surface as an application problem (for example, messages are not being processed fast enough because a server is down).</span></span>  
  
 <span data-ttu-id="5cd31-116">BizTalk Server 和應用程式的監控分成三個主要類別：</span><span class="sxs-lookup"><span data-stu-id="5cd31-116">Monitoring your BizTalk Server and Applications falls into three main categories:</span></span>  
  
-   <span data-ttu-id="5cd31-117">可用性監控</span><span class="sxs-lookup"><span data-stu-id="5cd31-117">Availability monitoring</span></span>  
  
-   <span data-ttu-id="5cd31-118">健康情況監控</span><span class="sxs-lookup"><span data-stu-id="5cd31-118">Health monitoring</span></span>  
  
-   <span data-ttu-id="5cd31-119">效能監控</span><span class="sxs-lookup"><span data-stu-id="5cd31-119">Performance monitoring</span></span>  
  
## <a name="availability-monitoring"></a><span data-ttu-id="5cd31-120">可用性監控</span><span class="sxs-lookup"><span data-stu-id="5cd31-120">Availability Monitoring</span></span>  
 <span data-ttu-id="5cd31-121">可用性監控會解答以下問題：「無法使用某項系統或應用程式資源是否會讓 BizTalk Server 應用程式無法以最佳方式執行？」</span><span class="sxs-lookup"><span data-stu-id="5cd31-121">Availability monitoring answers the question "Is the inavailability of a system or application resource preventing your BizTalk Server applications from running optimally?"</span></span> <span data-ttu-id="5cd31-122">這些問題大多是系統層級所特有，例如服務和連接的可用性。</span><span class="sxs-lookup"><span data-stu-id="5cd31-122">These issues are almost exclusively system-level, such as availability of services and connections.</span></span> <span data-ttu-id="5cd31-123">例如，如果因為企業單一登入服務停止而造成配接器失敗，這就是可用性問題。</span><span class="sxs-lookup"><span data-stu-id="5cd31-123">For example, if an adapter is failing because the Enterprise Single Sign-On service is stopped, this is an availability issue.</span></span> <span data-ttu-id="5cd31-124">如果指派給主控件的其中一部伺服器失敗了，而應用程式在處理訊息上發生落後，這也是可用性問題。</span><span class="sxs-lookup"><span data-stu-id="5cd31-124">If one of the servers assigned to a host has failed and your application is falling behind on processing messages, you have an availability issue.</span></span> <span data-ttu-id="5cd31-125">同樣地，如果應用程式已停止且無法處理訊息，這也是可用性問題。</span><span class="sxs-lookup"><span data-stu-id="5cd31-125">Likewise, if an application is stopped and is unable to process messages, you have an availability issue.</span></span> <span data-ttu-id="5cd31-126">下表列出可用性監控工具。</span><span class="sxs-lookup"><span data-stu-id="5cd31-126">The following table shows availability monitoring tools.</span></span>  
  
|<span data-ttu-id="5cd31-127">工具</span><span class="sxs-lookup"><span data-stu-id="5cd31-127">Tool</span></span>|<span data-ttu-id="5cd31-128">工作</span><span class="sxs-lookup"><span data-stu-id="5cd31-128">Task</span></span>|  
|----------|----------|  
|<span data-ttu-id="5cd31-129">BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="5cd31-129">BizTalk Server Administration Console</span></span>|<span data-ttu-id="5cd31-130">您應該在 BizTalk Server 管理主控台中查看 [群組中樞] 頁面，以瞭解應用程式或其元件 (連接埠/協調流程) 是否停止。</span><span class="sxs-lookup"><span data-stu-id="5cd31-130">You should look at the Group Hub page in the BizTalk Server Administration Console to see if applications or their components (ports/orchestrations) are stopped.</span></span>|  
|<span data-ttu-id="5cd31-131">事件檢視器</span><span class="sxs-lookup"><span data-stu-id="5cd31-131">Event Viewer</span></span>|<span data-ttu-id="5cd31-132">尋找配接器連接問題、停止的服務等等。</span><span class="sxs-lookup"><span data-stu-id="5cd31-132">Look for adapter connection issues, stopped services, and so on.</span></span>|  
  
## <a name="health-monitoring"></a><span data-ttu-id="5cd31-133">健全狀況監視</span><span class="sxs-lookup"><span data-stu-id="5cd31-133">Health Monitoring</span></span>  
 <span data-ttu-id="5cd31-134">健康情況監控可解答以下問題：「有任何應用程式或資源處於不良健康情況嗎？」</span><span class="sxs-lookup"><span data-stu-id="5cd31-134">Health monitoring helps you answer the question, "Are any of my applications or resources in bad health?"</span></span> <span data-ttu-id="5cd31-135">例如，目前有任何應用程式或其構成成品遇到例外狀況嗎？</span><span class="sxs-lookup"><span data-stu-id="5cd31-135">For example, are any of my applications or their constituent artifacts currently experiencing exception conditions?</span></span> <span data-ttu-id="5cd31-136">或者，是否因為訊息內容中的無效資料造成訊息擱置？</span><span class="sxs-lookup"><span data-stu-id="5cd31-136">Or, are messages suspended because of invalid data in the message payload?</span></span> <span data-ttu-id="5cd31-137">下表列出健康情況監控工具。</span><span class="sxs-lookup"><span data-stu-id="5cd31-137">The following table shows health-monitoring tools.</span></span>  
  
|<span data-ttu-id="5cd31-138">工具</span><span class="sxs-lookup"><span data-stu-id="5cd31-138">Tool</span></span>|<span data-ttu-id="5cd31-139">工作</span><span class="sxs-lookup"><span data-stu-id="5cd31-139">Task</span></span>|  
|----------|----------|  
|<span data-ttu-id="5cd31-140">BizTalk 健全狀況監視工具 (BHM)</span><span class="sxs-lookup"><span data-stu-id="5cd31-140">BizTalk Health Monitor tool (BHM)</span></span>|<span data-ttu-id="5cd31-141">MMC 嵌入式管理單元的使用者來監視 BizTalk Server 環境的健全狀況偵測重大和非重大問題，並執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="5cd31-141">An MMC snap-in for users to monitor the health of BizTalk Server environments, detect critical and non-critical issues, and execute maintenance tasks.</span></span>  <span data-ttu-id="5cd31-142">[下載 BizTalk 健全狀況監視器](https://www.microsoft.com/download/details.aspx?id=43716)。</span><span class="sxs-lookup"><span data-stu-id="5cd31-142">[Download BizTalk Health Monitor](https://www.microsoft.com/download/details.aspx?id=43716).</span></span>|  
|<span data-ttu-id="5cd31-143">BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="5cd31-143">BizTalk Server Administration Console</span></span>|<span data-ttu-id="5cd31-144">您將會在 BizTalk Server 管理主控台中使用 [群組中樞] 頁面和 [查詢] 頁面，以識別應用程式健康情況問題，並分析其原因。</span><span class="sxs-lookup"><span data-stu-id="5cd31-144">You will use the Group Hub page and query pages in the BizTalk Server Administration Console to identify application health problems and analyze their cause(s).</span></span>|  
|<span data-ttu-id="5cd31-145">事件檢視器</span><span class="sxs-lookup"><span data-stu-id="5cd31-145">Event Viewer</span></span>|<span data-ttu-id="5cd31-146">偵測訊息和協調流程的處理期間所發生的問題。</span><span class="sxs-lookup"><span data-stu-id="5cd31-146">Detect problems that occur during the processing of messages and orchestrations.</span></span>|  
  
## <a name="performance-monitoring"></a><span data-ttu-id="5cd31-147">效能監控</span><span class="sxs-lookup"><span data-stu-id="5cd31-147">Performance Monitoring</span></span>  
 <span data-ttu-id="5cd31-148">效能監控會解答以下問題：「系統執行工作的效率如何？」</span><span class="sxs-lookup"><span data-stu-id="5cd31-148">Performance monitoring answers the question, "How efficiently is the system performing its work?"</span></span> <span data-ttu-id="5cd31-149">這種監控主要著重於實體資源 (如資料庫和磁碟) 的負載。</span><span class="sxs-lookup"><span data-stu-id="5cd31-149">This kind of monitoring focuses primarily on the load on physical resources like databases and disks.</span></span> <span data-ttu-id="5cd31-150">例如，如果 CPU 使用率持續維持在百分之 90 和 100，而且形成了訊息的積存，這就是電腦層級的效能問題。</span><span class="sxs-lookup"><span data-stu-id="5cd31-150">For example, if the CPU utilization is consistently at 90 to 100 percent and a backlog of messages is forming, this is a performance issue at the computer level.</span></span> <span data-ttu-id="5cd31-151">下表列出效能監控工具。</span><span class="sxs-lookup"><span data-stu-id="5cd31-151">The following table shows performance-monitoring tools.</span></span>  
  
|<span data-ttu-id="5cd31-152">工具</span><span class="sxs-lookup"><span data-stu-id="5cd31-152">Tool</span></span>|<span data-ttu-id="5cd31-153">工作</span><span class="sxs-lookup"><span data-stu-id="5cd31-153">Task</span></span>|  
|----------|----------|  
|<span data-ttu-id="5cd31-154">SQL Query Analyzer</span><span class="sxs-lookup"><span data-stu-id="5cd31-154">SQL Query Analyzer</span></span>|<span data-ttu-id="5cd31-155">監控資料庫大小及內容，以診斷系統問題。</span><span class="sxs-lookup"><span data-stu-id="5cd31-155">Monitor database size and content to diagnose system problems.</span></span>|  
|<span data-ttu-id="5cd31-156">BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="5cd31-156">BizTalk Server Administration Console</span></span>|<span data-ttu-id="5cd31-157">[群組中樞] 頁面會顯示 BizTalk Server 應用程式中的重要效能度量，例如目前使用中、已凍結、準備要執行、已排程、已擱置等情況的服務執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="5cd31-157">The Group Hub Page shows key performance metrics such as the number of service instances currently active, dehydrated, ready to run, scheduled, suspended, etc. in your BizTalk Server applications.</span></span>|  
|<span data-ttu-id="5cd31-158">商務活動監控 (BAM)</span><span class="sxs-lookup"><span data-stu-id="5cd31-158">Business Activity Monitoring (BAM)</span></span>|<span data-ttu-id="5cd31-159">您可以在商務程序中指定特定的階段，而您想要針對這些階段來追蹤與商務應用程式有關的關鍵效能指標。</span><span class="sxs-lookup"><span data-stu-id="5cd31-159">You can specify specific stages in your business process for which you want to track key performance indicators pertinent to your business application.</span></span>|  
  
## <a name="biztalk-server-monitoring"></a><span data-ttu-id="5cd31-160">BizTalk Server 監控</span><span class="sxs-lookup"><span data-stu-id="5cd31-160">BizTalk Server Monitoring</span></span>  
 <span data-ttu-id="5cd31-161">您可以執行 **監控 BizTalk Server** SQL Agent 工作來識別管理、 訊息方塊或 DTA 資料庫中的任何已知的問題。</span><span class="sxs-lookup"><span data-stu-id="5cd31-161">You can run the **Monitor BizTalk Server** SQL Agent job to identify any known issues in Management, Message Box, or DTA databases.</span></span> <span data-ttu-id="5cd31-162">當您在 BizTalk Server 管理主控台中設定 BizTalk 群組或從舊版本升級 BizTalk 時，就會建立此工作。</span><span class="sxs-lookup"><span data-stu-id="5cd31-162">The job is created when you configure a BizTalk group in BizTalk Server Administration console or upgrade BizTalk from the previous version.</span></span>  
  
 <span data-ttu-id="5cd31-163">[監控 BizTalk Server] 作業會在管理、訊息方塊或 DTA 資料庫中掃描下列問題：</span><span class="sxs-lookup"><span data-stu-id="5cd31-163">The Monitor BizTalk Server job scans for the following issues in Management, Message Box, and DTA databases:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cd31-164">[監控 BizTalk Server] 工作只會掃描問題。</span><span class="sxs-lookup"><span data-stu-id="5cd31-164">The Monitor BizTalk Server job only scans for issues.</span></span> <span data-ttu-id="5cd31-165">並不會修正找到的問題。</span><span class="sxs-lookup"><span data-stu-id="5cd31-165">It does not fix the issues found.</span></span>  
  
-   <span data-ttu-id="5cd31-166">不具任何參考的訊息</span><span class="sxs-lookup"><span data-stu-id="5cd31-166">Messages without any references</span></span>  
  
-   <span data-ttu-id="5cd31-167">不具參考計數的訊息</span><span class="sxs-lookup"><span data-stu-id="5cd31-167">Messages without reference counts</span></span>  
  
-   <span data-ttu-id="5cd31-168">參考計數小於 0 的訊息</span><span class="sxs-lookup"><span data-stu-id="5cd31-168">Messages with reference count less than 0</span></span>  
  
-   <span data-ttu-id="5cd31-169">不具多工緩衝處理列的訊息參考</span><span class="sxs-lookup"><span data-stu-id="5cd31-169">Message references without spool rows</span></span>  
  
-   <span data-ttu-id="5cd31-170">不具執行個體的訊息參考</span><span class="sxs-lookup"><span data-stu-id="5cd31-170">Message references without instances</span></span>  
  
-   <span data-ttu-id="5cd31-171">不具執行個體的執行個體狀態</span><span class="sxs-lookup"><span data-stu-id="5cd31-171">Instance state without instances</span></span>  
  
-   <span data-ttu-id="5cd31-172">不具對應執行個體的執行個體訂閱</span><span class="sxs-lookup"><span data-stu-id="5cd31-172">Instance subscriptions without corresponding instances</span></span>  
  
-   <span data-ttu-id="5cd31-173">被遺棄的 DTA 服務執行個體</span><span class="sxs-lookup"><span data-stu-id="5cd31-173">Orphaned DTA service instances</span></span>  
  
-   <span data-ttu-id="5cd31-174">被遺棄的 DTA 服務執行個體例外狀況</span><span class="sxs-lookup"><span data-stu-id="5cd31-174">Orphaned DTA service instance exceptions</span></span>  
  
-   <span data-ttu-id="5cd31-175">啟用全域追蹤選項時，TDDS 沒有在任何主控件執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="5cd31-175">TDDS is not running on any host instance when global tracking option is enabled.</span></span>  
  
 <span data-ttu-id="5cd31-176">已設定 [監控 BizTalk Server] 工作，而且已自動化成一週執行一次。</span><span class="sxs-lookup"><span data-stu-id="5cd31-176">The Monitor BizTalk Server job is configured and automated to run once in a week.</span></span> <span data-ttu-id="5cd31-177">因為工作會進行密集計算，所以建議您排程它在關閉/低流量期間進行。</span><span class="sxs-lookup"><span data-stu-id="5cd31-177">Since the job is computationally intensive, we recommended you to schedule it during downtime/low traffic.</span></span>  
  
 <span data-ttu-id="5cd31-178">工作只要發生任何問題就會失敗；錯誤字串會包含找到的問題數。</span><span class="sxs-lookup"><span data-stu-id="5cd31-178">The job fails if it encounters any issues; error string contains the number of issues found.</span></span> <span data-ttu-id="5cd31-179">否則表示已順利執行。</span><span class="sxs-lookup"><span data-stu-id="5cd31-179">Else, it runs successfully.</span></span> <span data-ttu-id="5cd31-180">您可以在工作記錄中查看詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5cd31-180">You can see the details in the job history.</span></span> <span data-ttu-id="5cd31-181">如果您使用系統管理員權限執行工作，則也會將錯誤字串記錄至 [事件檢視器] \(和工作記錄)。</span><span class="sxs-lookup"><span data-stu-id="5cd31-181">If you run the job with Administrator privileges, error string will be logged to Event Viewer also (along with the job history).</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5cd31-182">疑難排解</span><span class="sxs-lookup"><span data-stu-id="5cd31-182">Troubleshooting</span></span>  
 <span data-ttu-id="5cd31-183">一旦您察覺 BizTalk Server 應用程式 (而不是基礎結構) 有健康情況問題時，您可以在 BizTalk Server 管理主控台中使用 [群組中樞] 頁面和 [查詢] 頁面來分析問題。</span><span class="sxs-lookup"><span data-stu-id="5cd31-183">Once you are aware of a health problem with your BizTalk Server applications (not infrastructure), you can use the Group Hub page and Query pages in the BizTalk Server Administration Console to analyze the problem.</span></span> <span data-ttu-id="5cd31-184">BizTalk Server 管理主控台會提供整合式組態、部署和疑難排解體驗，而且當您指出組態和部署相關的問題之後，可以在管理主控台中加以修正。</span><span class="sxs-lookup"><span data-stu-id="5cd31-184">The BizTalk Server Administration Console provides an integrated configuration, deployment and troubleshooting experience, and you can fix configuration and deployment related problems within the Administration Console after you have pinpointed them.</span></span> <span data-ttu-id="5cd31-185">一般來說，大多數的應用程式問題都是因為未得到預期的訊息 (這可以呈現為擱置的服務執行個體或重試連接埠，或是尚未重新啟動的已凍結執行個體等等)。</span><span class="sxs-lookup"><span data-stu-id="5cd31-185">Typically, most application problems are due to messages not getting through as expected (this can manifest as suspended service instances, or retrying ports, or dehydrated instances that have not been reactivated, etc.)</span></span>  
  
 <span data-ttu-id="5cd31-186">您可以使用 [群組中樞] 頁面和查詢頁面將您的服務執行個體 (不論其狀態為︰ 執行暫止、 已凍結，等) 由應用程式錯誤類型，服務類型、 主機等，以找出不同的錯誤、 調查它們一一加以修正。</span><span class="sxs-lookup"><span data-stu-id="5cd31-186">You can use the Group Hub page and Query pages to group your service instances (whatever state they are in: running, suspended, dehydrated, etc) by Application, Error type, Service Type, Host, etc, to isolate the different errors, investigate them one by one, and fix them.</span></span> <span data-ttu-id="5cd31-187">您也可以從 BizTalk Server 管理主控台監控追蹤資料，以調查訊息流程的記錄或是協調流程或規則集的執行記錄。</span><span class="sxs-lookup"><span data-stu-id="5cd31-187">You can also monitor tracking data from within the BizTalk Server Administration Console, to investigate the history of a message flow, or the history of execution of an orchestration or rule set.</span></span> <span data-ttu-id="5cd31-188">這個追蹤資料包含有關 BizTalk Server 應用程式的歷程記錄資料。</span><span class="sxs-lookup"><span data-stu-id="5cd31-188">This tracking data contains historical data about your BizTalk Server applications.</span></span>  
  
 <span data-ttu-id="5cd31-189">如果您已啟用追蹤，在 BizTalk 管理主控台中，您可以使用追蹤來找出訊息流程和服務執行個體使用的查詢。</span><span class="sxs-lookup"><span data-stu-id="5cd31-189">If you have enabled tracking in the BizTalk Administration Console, you can use tracking to locate message flow and service instances using a query.</span></span> <span data-ttu-id="5cd31-190">當您想要尋找訊息，而且只知道訊息類型 (結構描述)、屬性和它的值 (如客戶名稱) 等資料時，這樣的處理方式會很有用處。</span><span class="sxs-lookup"><span data-stu-id="5cd31-190">This is useful when you want to locate a message and know only, for example, the message type (schema), a property and its value (for example, customer name), etc.</span></span>  
  
 <span data-ttu-id="5cd31-191">下列主題將討論使用 BizTalk Server 管理主控台、[群組中樞] 頁面和 [查詢] 頁面進行監控和疑難排解的相關內容。</span><span class="sxs-lookup"><span data-stu-id="5cd31-191">The following topics discuss monitoring and troubleshooting using the BizTalk Server Administration Console, Group Hub page, and Query pages.</span></span> <span data-ttu-id="5cd31-192">本章節也討論追蹤，您可以使用它來協助疑難排解和根本原因分析。</span><span class="sxs-lookup"><span data-stu-id="5cd31-192">This section also discusses tracking, which you can use as an aid in troubleshooting and root-cause analysis.</span></span>  
  
## <a name="more-good-stuff"></a><span data-ttu-id="5cd31-193">其他不錯的工具</span><span class="sxs-lookup"><span data-stu-id="5cd31-193">More good stuff</span></span>  
  
-   [<span data-ttu-id="5cd31-194">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="5cd31-194">Using the BizTalk Server Administration Console</span></span>](../core/using-the-biztalk-server-administration-console.md)  
  
-   [<span data-ttu-id="5cd31-195">檢視追蹤的訊息和執行個體資料</span><span class="sxs-lookup"><span data-stu-id="5cd31-195">Viewing Tracked Message and Instance Data</span></span>](../core/viewing-tracked-message-and-instance-data.md)  
  
-   [<span data-ttu-id="5cd31-196">監控 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="5cd31-196">Monitoring EDI and AS2 Solutions</span></span>](../core/monitoring-edi-and-as2-solutions.md)  
  
-   [<span data-ttu-id="5cd31-197">追蹤 BizTalk Server 應用程式中成品之間的依存性</span><span class="sxs-lookup"><span data-stu-id="5cd31-197">Tracking Dependencies Between Artifacts in a BizTalk Server Application</span></span>](../core/tracking-dependencies-between-artifacts-in-a-biztalk-server-application.md)

- [<span data-ttu-id="5cd31-198">效能計數器</span><span class="sxs-lookup"><span data-stu-id="5cd31-198">Performance Counters</span></span>](performance-counters.md)