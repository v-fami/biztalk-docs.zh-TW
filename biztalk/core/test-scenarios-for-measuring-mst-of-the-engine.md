---
title: 測量引擎 MST 的測試案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e54667b9-7262-43c8-a013-9242eb062daf
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd5b9a2697cb96bb2d042b9fee6a15317f35971c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008015"
---
# <a name="test-scenarios-for-measuring-mst-of-the-engine"></a><span data-ttu-id="8ab4b-102">測量引擎 MST 的測試實例</span><span class="sxs-lookup"><span data-stu-id="8ab4b-102">Test Scenarios for Measuring MST of the Engine</span></span>
<span data-ttu-id="8ab4b-103">本節描述一個測試實例，實作此實例以測量在三個不同負載層級驅動 BizTalk 系統的效果：</span><span class="sxs-lookup"><span data-stu-id="8ab4b-103">This section describes a test scenario that was implemented to measure the effect of driving a BizTalk system at three different levels of load:</span></span>  
  
-   <span data-ttu-id="8ab4b-104">[持續性負載測試](../core/sustainable-load-test.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-104">[Sustainable Load Test](../core/sustainable-load-test.md).</span></span> <span data-ttu-id="8ab4b-105">基於這些測試的詳細資訊，持續性負載主題會說明[何謂持續性效能？](../core/what-is-sustainable-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-105">For purposes of these tests, sustainable load is described in the topic [What Is Sustainable Performance?](../core/what-is-sustainable-performance.md).</span></span>  
  
-   <span data-ttu-id="8ab4b-106">[加速負載測試](../core/overdrive-load-test.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-106">[Overdrive Load Test](../core/overdrive-load-test.md).</span></span> <span data-ttu-id="8ab4b-107">加速負載的定義超過 MST 的一致性負載。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-107">Overdrive load is defined as a consistent load that exceeds MST.</span></span>  
  
-   <span data-ttu-id="8ab4b-108">[大量負載測試](../core/floodgate-load-test.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-108">[Floodgate Load Test](../core/floodgate-load-test.md).</span></span> <span data-ttu-id="8ab4b-109">大量載入會定義為低負載間歇尖峰的負載超過 MST 之使用。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-109">Floodgate load is defined as low load with intermittent peaks of load that exceed MST.</span></span>  
  
 <span data-ttu-id="8ab4b-110">本主題描述測試硬體組態、測試實例，並討論這些測試的每一個發現。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-110">This topic describes the test hardware configuration, the test scenarios, and discusses the findings of each of these tests.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ab4b-111">讀者必須注意，本節包含的資訊代表 Microsoft 在發行日當時對討論之問題的觀點。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-111">Readers should be aware that the information contained in this section represents the current view of Microsoft on the issues discussed as of the date of publication.</span></span> <span data-ttu-id="8ab4b-112">由於我們必須回應不斷變化的市場狀況與技術，因此 Microsoft 無法保證發行日之後提出之任何資訊的正確性。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-112">Because we must respond to changing market conditions and technologies, Microsoft cannot guarantee the accuracy of any information presented after the date of publication.</span></span>  
  
## <a name="test-system-configuration"></a><span data-ttu-id="8ab4b-113">測試系統組態</span><span class="sxs-lookup"><span data-stu-id="8ab4b-113">Test System Configuration</span></span>  
 <span data-ttu-id="8ab4b-114">這個測試實例是使用下列硬體：</span><span class="sxs-lookup"><span data-stu-id="8ab4b-114">The following hardware was used for this test scenario:</span></span>  
  
-   <span data-ttu-id="8ab4b-115">**六部 BizTalk Server**。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-115">**Six BizTalk Servers**.</span></span> <span data-ttu-id="8ab4b-116">每部都配備了兩個 3GHz 處理器和 2GB 的 RAM。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-116">Each equipped with dual 3GHz processors and 2GB of RAM.</span></span> <span data-ttu-id="8ab4b-117">每部伺服器都使用本機磁碟。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-117">Each server is using local disks.</span></span> <span data-ttu-id="8ab4b-118">兩部 BizTalk Server 是使用接收主控件的執行個體來設定，另外兩部是使用傳送主控件的執行個體來設定，而剩下的兩部是以用於處理協調流程的主控件執行個體來設定。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-118">Two of the BizTalk Servers are configured with an instance of the receiving host, two are configured with an instance of the sending host, and two are configured with an instance of the host used for processing orchestrations.</span></span>  
  
-   <span data-ttu-id="8ab4b-119">**一個主要 MessageBox 資料庫和非 MessageBox 資料庫的 SQL Server**。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-119">**One SQL Server for the master MessageBox database and the non-MessageBox databases**.</span></span> <span data-ttu-id="8ab4b-120">配備八個 2GHz 處理器和 4 GB 的 RAM。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-120">Equipped with eight 2GHz processors and 4 GB of RAM.</span></span> <span data-ttu-id="8ab4b-121">此伺服器是透過光纖連線到快速 SAN 磁碟子系統。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-121">This server is connected to a fast SAN disk subsystem via fiber.</span></span> <span data-ttu-id="8ab4b-122">已停用訊息發佈。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-122">Message publication is disabled.</span></span>  
  
-   <span data-ttu-id="8ab4b-123">**要發佈到 Messagebox 資料庫的三部 SQL Server**。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-123">**Three SQL Servers for the Messagebox databases that are being published to**.</span></span> <span data-ttu-id="8ab4b-124">配備四個 2GHz 處理器和 4GB 的 RAM。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-124">Equipped with four 2GHz processors and 4GB of RAM.</span></span> <span data-ttu-id="8ab4b-125">這些伺服器均是透過光纖連線到快速 SAN 磁碟子系統。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-125">These servers are each connected to a fast SAN disk subsystem via fiber.</span></span> <span data-ttu-id="8ab4b-126">MessageBox 資料庫的資料和交易記錄檔是位於個別的儲存區域網路 (SAN) 邏輯單位數 (LUN) 中。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-126">The data and transaction log files for the MessageBox database are on separate storage area network (SAN) logical unit numbers (LUNs).</span></span>  
  
-   <span data-ttu-id="8ab4b-127">**載入驅動程式用戶端機器**。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-127">**Load driver client machine**.</span></span> <span data-ttu-id="8ab4b-128">配備兩個 3GHz 處理器和 2GB 的 RAM。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-128">Equipped with dual 3GHz processors and 2GB of RAM.</span></span> <span data-ttu-id="8ab4b-129">此伺服器是用來產生用於測試 BizTalk 系統的負載。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-129">This server was used to generate the load for testing the BizTalk system.</span></span>  
  
 <span data-ttu-id="8ab4b-130">以下會說明用於負載測試的拓樸。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-130">The topology used for the load tests is illustrated below.</span></span>  
  
 <span data-ttu-id="8ab4b-131">**用於負載測試的拓樸**</span><span class="sxs-lookup"><span data-stu-id="8ab4b-131">**Topology used for load tests**</span></span>  
  
 <span data-ttu-id="8ab4b-132">![BizTalk Server 負載測試的硬體拓撲](../core/media/bts06-msttopology.gif "BTS06_MSTTopology")</span><span class="sxs-lookup"><span data-stu-id="8ab4b-132">![Hardware topology for BizTalk Server load testing](../core/media/bts06-msttopology.gif "BTS06_MSTTopology")</span></span>  
  
## <a name="the-test-scenario"></a><span data-ttu-id="8ab4b-133">測試實例</span><span class="sxs-lookup"><span data-stu-id="8ab4b-133">The Test Scenario</span></span>  
 <span data-ttu-id="8ab4b-134">測試實例非常簡單。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-134">The test scenario is very simple.</span></span> <span data-ttu-id="8ab4b-135">負載產生工具 LoadGen 2007 是安裝在負載驅動程式伺服器上，可用來將檔案複本傳送到檔案配接器所監控的共用。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-135">The load generation tool, LoadGen 2007, was installed on the load driver server and was used to send copies of a file to shares monitored by the file adapter.</span></span> <span data-ttu-id="8ab4b-136">負載生產工具會將輸入檔案執行個體的複本，平均分散到各個檔案共用。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-136">The load generation tool distributes copies of the input file instance evenly across the file shares.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ab4b-137">下載[LoadGen](https://www.microsoft.com/download/details.aspx?id=14925)。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-137">Download [LoadGen](https://www.microsoft.com/download/details.aspx?id=14925).</span></span> <span data-ttu-id="8ab4b-138">此工具的舊版，BizTalk Server 2004 負載產生工具是下載[http://go.microsoft.com/fwlink/?linkid=108999](http://go.microsoft.com/fwlink/?linkid=108999)。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-138">The previous version of this tool, the BizTalk Server 2004 Load Generation Tool is available for download at [http://go.microsoft.com/fwlink/?linkid=108999](http://go.microsoft.com/fwlink/?linkid=108999).</span></span> <span data-ttu-id="8ab4b-139">如需有關使用 LoadGen 搭配 MSMQ 配接器的資訊，請參閱[搭配 MSMQ 使用 LoadGen 2007](../core/using-loadgen-2007-with-msmq.md)。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-139">For information about using LoadGen with the MSMQ adapter, see [Using LoadGen 2007 with MSMQ](../core/using-loadgen-2007-with-msmq.md).</span></span>  
  
 <span data-ttu-id="8ab4b-140">BizTalk 檔案配接器是設定來監控檔案共用，並將訊息發佈至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-140">The BizTalk File adapter is configured to monitor the file shares and publish the messages into the MessageBox.</span></span> <span data-ttu-id="8ab4b-141">只包含接收圖形與傳送圖型的簡單型協調流程會訂閱已發佈的訊息。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-141">A simple orchestration that contains only a receive shape and a send shape subscribes to the published message.</span></span> <span data-ttu-id="8ab4b-142">由協調流程發佈回 MessageBox 的訊息會被檔案傳送埠所拾取，並傳送到 SAN 中所定義的一般共用。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-142">Messages that are published back into the MessageBox by the orchestration are picked up by a file send port and sent to a common share, defined on the SAN.</span></span> <span data-ttu-id="8ab4b-143">抵達輸出 SAN 共用的檔案會立即刪除，以防止長期測試執行期間在該共用上建置檔案。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-143">Files arriving on the output SAN share are immediately deleted in order to avoid file buildup on that share during long test runs.</span></span>  
  
 <span data-ttu-id="8ab4b-144">這個實例已定義四個主控件，各別用於接收位置、協調流程、傳送埠和追蹤。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-144">Four hosts were defined for the scenario, one each for the receive location, the orchestrations, the send port, and for tracking.</span></span> <span data-ttu-id="8ab4b-145">為了觀察引擎積存的行為，在測試執行期間會完全關閉追蹤。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-145">For the purposes of observing engine backlog behavior, tracking is completely turned off during the test runs.</span></span> <span data-ttu-id="8ab4b-146">依照預設，只會針對管線和協調流程啟動追蹤，所以在 BizTalk 系統管理員中，會針對所使用的協調流程和管線明確地關閉追蹤。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-146">Tracking is only enabled for pipelines and orchestrations by default so tracking was explicitly turned off in the BizTalk Administrator for the orchestration and pipeline that was used.</span></span>  
  
 <span data-ttu-id="8ab4b-147">關閉追蹤之後，就不會建立追蹤主控件的執行個體，以隔離這些測試的核心 MessageBox 行為。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-147">No instances of the tracking host were created since tracking was turned off to isolate core MessageBox behavior for these tests.</span></span>  
  
 <span data-ttu-id="8ab4b-148">會使用一個簡單的結構描述，且用於測試的所有執行個體檔案的大小總共為 10KB。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-148">A simple schema was used and the instance files used for the test were all 10KB in size.</span></span> <span data-ttu-id="8ab4b-149">輸入文件會使用 XMLReceive 管線，而不會使用對應元件或輸出元件，這是為了讓測試實例維持簡單，並將觀察重心放在 MessageBox 的行為。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-149">The XMLReceive pipeline was used for inbound documents and no mapping components or outbound components were used in order to keep the test scenario simple and focus observations on the behavior of the MessageBox.</span></span>  
  
## <a name="parameters-measured-in-the-test"></a><span data-ttu-id="8ab4b-150">測試中所測量的參數</span><span class="sxs-lookup"><span data-stu-id="8ab4b-150">Parameters Measured in the Test</span></span>  
 <span data-ttu-id="8ab4b-151">測試中所測量的參數如下：</span><span class="sxs-lookup"><span data-stu-id="8ab4b-151">The parameters measured in this test are as follows:</span></span>  
  
 <span data-ttu-id="8ab4b-152">**測量的主要測試參數**</span><span class="sxs-lookup"><span data-stu-id="8ab4b-152">**Primary test parameters measured**</span></span>  
  
 <span data-ttu-id="8ab4b-153">下列參數是測量 MST 時所使用的主要指標：</span><span class="sxs-lookup"><span data-stu-id="8ab4b-153">The following parameters are the primary indicators used when measuring MST:</span></span>  
  
-   <span data-ttu-id="8ab4b-154">所測量的 MessageBox 積存**多工緩衝處理大小**所提供的計數器**biztalk: messagebox： 計數器**效能物件。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-154">The MessageBox backlog as measured by the **Spool Size** counter that is available with the **BizTalk:MessageBox:General Counters** performance object.</span></span> <span data-ttu-id="8ab4b-155">Messagebox 積存是維持性的關鍵指標。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-155">Messagebox backlog is a key indicator of sustainability.</span></span> <span data-ttu-id="8ab4b-156">很顯然地，MessageBox 積存不可能無限地繼續成長而不會遭遇任何問題。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-156">Clearly, MessageBox backlog cannot continue to grow indefinitely without eventually running into problems.</span></span> <span data-ttu-id="8ab4b-157">因此，一直以來所監控的 MessageBox 資料庫積存的深度，是用來評估維持性。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-157">So, the depth of the MessageBox database backlog, monitored over time, is used to evaluate sustainability.</span></span>  
  
     <span data-ttu-id="8ab4b-158">命名的 MessageBox 表格**多工緩衝處理**包含系統中的每個訊息的記錄 (作用中或等待被記憶體回收收集)。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-158">The MessageBox table named **spool** contains a record for each message in the system (active or waiting to be garbage collected).</span></span> <span data-ttu-id="8ab4b-159">監控此資料表中的資料列數目，以及每秒所接收的訊息數目，而不斷增加的系統負載提供了一個輕鬆的方法，來測量可維持的輸送量上限。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-159">Monitoring the number of rows in this table, and the number of messages received per second, while increasing system load provides an easy way to measure the maximum sustainable throughput.</span></span> <span data-ttu-id="8ab4b-160">這個度量單位也稱為**多工緩衝處理表深度**或**多工緩衝處理深度**。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-160">This measurement is also referred to as the **spool table depth** or **spool depth**.</span></span>  
  
-   <span data-ttu-id="8ab4b-161">每秒所測量接收的文件數目**文件數/秒**所提供的計數器**BizTalk： 傳訊**效能物件。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-161">The number of documents received per second as measured by the **Documents received/Sec** counter that is available with the **BizTalk:Messaging** performance object.</span></span>  
  
 <span data-ttu-id="8ab4b-162">**測量的次要測試參數**</span><span class="sxs-lookup"><span data-stu-id="8ab4b-162">**Secondary test parameters measured**</span></span>  
  
 <span data-ttu-id="8ab4b-163">下列參數是測量 MST 時可以評估的次要指標。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-163">The following parameters are secondary indicators that can be evaluated when measuring MST.</span></span> <span data-ttu-id="8ab4b-164">這些參數可能會影響多工緩衝處理深度的主要指標，以及每秒鐘接收的文件數目。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-164">These parameters may impact the primary indicators of spool depth and the number of documents received per second.</span></span>  
  
-   <span data-ttu-id="8ab4b-165">實體磁碟閒置時間的 MessageBox 資料和交易檔案磁碟所測量 **%閒置時間**計數器適用於**LogicalDisk**效能物件。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-165">The physical disk idle time for the MessageBox data and transaction file disk as measured by the **%Idle Time** counter available with the **LogicalDisk** performance object.</span></span>  
  
-   <span data-ttu-id="8ab4b-166">CPU 使用率 （%） 所測量的 MessageBox 伺服器 **%Processor Time**計數器適用於**處理器**效能物件。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-166">The CPU utilization (%) for the MessageBox server as measured by the **%Processor Time** counter available with the **Processor** performance object.</span></span>  
  
-   <span data-ttu-id="8ab4b-167">MessageBox 上每秒鎖定逾時的資料庫所測量**Lock Timeouts/sec**計數器適用於**sqlserver: Locks**效能物件。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-167">The lock timeouts per second on the MessageBox database as measured by the **Lock Timeouts/sec** counter available with the **SQLServer:Locks** performance object.</span></span>  
  
-   <span data-ttu-id="8ab4b-168">負責清除與已移除訊息相關聯之訊息方塊表的 SQL 代理程式，最近執行的時間 (秒)。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-168">The time in seconds for the most recent run of the SQL agent job that cleans up message box tables associated with removed messages.</span></span> <span data-ttu-id="8ab4b-169">這所測量**MsgBox 訊息 Cleanup(Purge Jobs)** 計數器適用於**biztalk: messagebox： 計數器**效能物件。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-169">This is measured by the **MsgBox Msg Cleanup(Purge Jobs)** counter available with the **BizTalk:MessageBox:General Counters** performance object.</span></span>  
  
-   <span data-ttu-id="8ab4b-170">負責清除與已移除訊息部分相關聯之訊息方塊表的 SQL 代理程式，最近執行的時間 (秒)。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-170">The time in seconds for the most recent run of the SQL agent job which cleans up message box tables associated with removed message parts.</span></span> <span data-ttu-id="8ab4b-171">這所測量**MsgBox 部分 Cleanup(Purge Jobs)** 計數器適用於**biztalk: messagebox： 計數器**效能物件。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-171">This is measured by the **MsgBox Parts Cleanup(Purge Jobs)** counter available with the **BizTalk:MessageBox:General Counters** performance object.</span></span>  
  
 <span data-ttu-id="8ab4b-172">在測試以判斷最大持續輸送量時，輸入負載會增加到多工緩衝處理表格開始無限成長的點。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-172">When testing to determine the maximum sustainable throughput, input load was increased up to the point that the spool table started to grow indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ab4b-173">若您無法產生足夠的負載，讓多工緩衝處理表可以無限地成長，這只是表示系統最慢的部分是在接收端，而非處理/傳送端。</span><span class="sxs-lookup"><span data-stu-id="8ab4b-173">If you are unable to generate enough load to cause the spool table to grow indefinitely, it simply means that the slowest part of your system is on the receive side, rather than the processing/send side.</span></span>  
  

## <a name="next"></a><span data-ttu-id="8ab4b-174">下一個</span><span class="sxs-lookup"><span data-stu-id="8ab4b-174">Next</span></span>
  
-   [<span data-ttu-id="8ab4b-175">使用 Microsoft BizTalk LoadGen 2007 工具</span><span class="sxs-lookup"><span data-stu-id="8ab4b-175">Using the Microsoft BizTalk LoadGen 2007 Tool</span></span>](../core/using-the-microsoft-biztalk-loadgen-2007-tool.md)  
  
-   [<span data-ttu-id="8ab4b-176">持續性負載測試</span><span class="sxs-lookup"><span data-stu-id="8ab4b-176">Sustainable Load Test</span></span>](../core/sustainable-load-test.md)  
  
-   [<span data-ttu-id="8ab4b-177">加速負載測試</span><span class="sxs-lookup"><span data-stu-id="8ab4b-177">Overdrive Load Test</span></span>](../core/overdrive-load-test.md)  
  
-   [<span data-ttu-id="8ab4b-178">大量負載測試</span><span class="sxs-lookup"><span data-stu-id="8ab4b-178">Floodgate Load Test</span></span>](../core/floodgate-load-test.md)