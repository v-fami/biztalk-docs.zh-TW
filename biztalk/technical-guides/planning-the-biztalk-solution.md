---
title: 規劃 BizTalk 解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30d56a04-966a-46b1-861d-f5be4e58b7d2
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f337efa7b72a40c37a4cc3f42a2bd5d846923dc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970951"
---
# <a name="plan-for-your-biztalk-solution"></a><span data-ttu-id="a0ce8-102">規劃 BizTalk 解決方案</span><span class="sxs-lookup"><span data-stu-id="a0ce8-102">Plan for your BizTalk Solution</span></span>
<span data-ttu-id="a0ce8-103">主要設計目標之一[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是為配合多個處理的案例中，盡可能提供最大的彈性。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-103">One of the primary design goals of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is to provide maximum flexibility for accommodating as many processing scenarios as possible.</span></span> <span data-ttu-id="a0ce8-104">這很大的彈性，因為 BizTalk 解決方案的開發人員所面臨的主要挑戰之一是要判斷如何發揮最大功能用於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]最符合其商務需求。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-104">Because of this great flexibility, one of the primary challenges facing developers of a BizTalk solution is to determine how to make best use of the features available in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to best meet their business needs.</span></span> <span data-ttu-id="a0ce8-105">規劃[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以細分成不同的階段，摘要說明如下。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-105">Planning the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be broken down into distinct phases which are summarized below.</span></span>  
  
## <a name="scoping-the-solution"></a><span data-ttu-id="a0ce8-106">範圍的解決方案</span><span class="sxs-lookup"><span data-stu-id="a0ce8-106">Scoping the Solution</span></span>  
  
### <a name="performance-considerations"></a><span data-ttu-id="a0ce8-107">效能考量</span><span class="sxs-lookup"><span data-stu-id="a0ce8-107">Performance Considerations</span></span>  
 <span data-ttu-id="a0ce8-108">設定 BizTalk 方案的範圍時，請考慮下列：</span><span class="sxs-lookup"><span data-stu-id="a0ce8-108">Consider the following when scoping your BizTalk solution:</span></span>  
  
- <span data-ttu-id="a0ce8-109">哪些配接器和/或加速器需要？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-109">Which adapters and/or accelerators are required?</span></span>  
  
- <span data-ttu-id="a0ce8-110">在方案中實作協調流程的需求有哪些？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-110">What are the requirements for implementing orchestrations in the solution?</span></span>  
  
- <span data-ttu-id="a0ce8-111">文件的輸送量需求： 解決方案的最大持續輸送量需求為何？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-111">Document throughput requirements: What are the maximum sustainable throughput requirements for the solution?</span></span>  
  
- <span data-ttu-id="a0ce8-112">延遲需求： 如何回應方案必須請求-回應 」 和 「 要求回應的案例？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-112">Latency requirements: How responsive does the solution need to be for solicit-response and request-response scenarios?</span></span>  
  
- <span data-ttu-id="a0ce8-113">解決方案程度的尖峰文件載入期間從復原？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-113">How well does the solution recover from periods of peak document load?</span></span>  
  
- <span data-ttu-id="a0ce8-114">方案的高可用性需求有哪些？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-114">What are the high availability requirements of the solution?</span></span>  
  
- <span data-ttu-id="a0ce8-115">文件追蹤需求的解決方案有哪些？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-115">What are the document tracking requirements of the solution?</span></span>  
  
- <span data-ttu-id="a0ce8-116">任何相依的應用程式，例如遠端 Web 服務或其他系統的效能特性有哪些？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-116">What are the performance characteristics of any dependent applications such as a remote Web service or other system?</span></span> <span data-ttu-id="a0ce8-117">如果相依的應用程式執行無法跟上必要的負載然後整體系統效能會下降據此。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-117">If dependent applications do not keep up with the required load then the overall system performance will be degraded accordingly.</span></span>  
  
- <span data-ttu-id="a0ce8-118">將 BizTalk 應用程式會使用資料庫無關[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]嗎？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-118">Would the BizTalk application be consuming databases not related to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]?</span></span> <span data-ttu-id="a0ce8-119">例如，如果 BizTalk 應用程式使用 SQL Server 資料庫使用 SQL 配接器中的資料表，資料表有效率地設定？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-119">For example, if the BizTalk application is consuming tables in a SQL Server database using the SQL adapter, are the tables efficiently configured?</span></span>  
  
### <a name="hardware-considerations"></a><span data-ttu-id="a0ce8-120">硬體考量</span><span class="sxs-lookup"><span data-stu-id="a0ce8-120">Hardware Considerations</span></span>  
 <span data-ttu-id="a0ce8-121">範圍的解決方案時，建立包含下列的高階硬體圖表：</span><span class="sxs-lookup"><span data-stu-id="a0ce8-121">When scoping the solution, create a high-level hardware diagram that includes the following:</span></span>  
  
-   <span data-ttu-id="a0ce8-122">電腦架構 （例如 x86、 x64 和 IA64）</span><span class="sxs-lookup"><span data-stu-id="a0ce8-122">Computer architecture (such as x86, x64, and IA64)</span></span>  
  
-   <span data-ttu-id="a0ce8-123">CPU 需求 （例如類型、 速度、 數目、 核心，以及使用超執行緒）</span><span class="sxs-lookup"><span data-stu-id="a0ce8-123">CPU requirements (such as type, speed, number, cores, and use of hyperthreading)</span></span>  
  
-   <span data-ttu-id="a0ce8-124">每一部電腦的 RAM 需求</span><span class="sxs-lookup"><span data-stu-id="a0ce8-124">RAM requirements for each computer</span></span>  
  
-   <span data-ttu-id="a0ce8-125">本機磁碟儲存體 （類型、 大小、 速度）</span><span class="sxs-lookup"><span data-stu-id="a0ce8-125">Local disk storage (type, size, speed)</span></span>  
  
-   <span data-ttu-id="a0ce8-126">SAN (存放裝置需求： 數字的 LUN。SAN 卡片類型）</span><span class="sxs-lookup"><span data-stu-id="a0ce8-126">SAN (storage requirements: number of LUNS; SAN card type)</span></span>  
  
-   <span data-ttu-id="a0ce8-127">網路卡 (在每一部電腦，與 1 Gb 的 100 mb (Mbps) 數字 (1 Gbps)。)</span><span class="sxs-lookup"><span data-stu-id="a0ce8-127">Network cards (number in each computer, 100 megabits (Mbps) versus 1 Gigabit (1 Gbps).)</span></span>  
  
-   <span data-ttu-id="a0ce8-128">防火牆會部署方案中的方式？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-128">How will firewalls be deployed in the solution?</span></span>  
  
-   <span data-ttu-id="a0ce8-129">會使用網路負載平衡硬體嗎？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-129">Will Network Load Balancing hardware be used?</span></span>  
  
-   <span data-ttu-id="a0ce8-130">要叢集化是特定的電腦？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-130">Are specific computers to be clustered?</span></span>  
  
-   <span data-ttu-id="a0ce8-131">將您使用 Microsoft HYPER-V Server 或任何其他虛擬化產品相關的虛擬環境？</span><span class="sxs-lookup"><span data-stu-id="a0ce8-131">Would you be using a virtual environment involving Microsoft Hyper-V Server or any other virtualization products?</span></span>  
  
## <a name="planning-the-solution"></a><span data-ttu-id="a0ce8-132">規劃解決方案</span><span class="sxs-lookup"><span data-stu-id="a0ce8-132">Planning the Solution</span></span>  
  
### <a name="solution-milestones-timeline"></a><span data-ttu-id="a0ce8-133">方案里程碑時間軸</span><span class="sxs-lookup"><span data-stu-id="a0ce8-133">Solution Milestones Timeline</span></span>  
 <span data-ttu-id="a0ce8-134">完成 BizTalk 方案的特定層面的里程碑與建立排程。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-134">Create a schedule with milestones for completing specific aspects of your BizTalk solution.</span></span> <span data-ttu-id="a0ce8-135">設定特定的里程碑將增加解決方案的可能性及時完成。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-135">Setting specific milestones will increase the likelihood that the solution will be completed in a timely manner.</span></span>  
  
### <a name="non-microsoft-software-considerations"></a><span data-ttu-id="a0ce8-136">非 Microsoft 軟體的考量</span><span class="sxs-lookup"><span data-stu-id="a0ce8-136">Non-Microsoft Software Considerations</span></span>  
 <span data-ttu-id="a0ce8-137">解決方案會使用非 Microsoft 軟體時，請考慮下列：</span><span class="sxs-lookup"><span data-stu-id="a0ce8-137">Consider the following when non-Microsoft software will be used with the solution:</span></span>  
  
-   <span data-ttu-id="a0ce8-138">判斷軟體或硬體所需的是如何取得。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-138">Determine how the software or hardware required be obtained.</span></span>  
  
-   <span data-ttu-id="a0ce8-139">規劃容量並調整大小以確保該非 Microsoft 軟體不會成為您的方案中的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-139">Plan for capacity and sizing to ensure that non-Microsoft software does not become a bottleneck in your solution.</span></span>  
  
-   <span data-ttu-id="a0ce8-140">判斷安裝所需的非 Microsoft 軟體的動作計劃。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-140">Determine a plan of action for installing required non-Microsoft software.</span></span>  
  
-   <span data-ttu-id="a0ce8-141">建立計劃的設定和最佳化所需的非 Microsoft 軟體的動作。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-141">Create a plan of action for configuring and optimizing required non-Microsoft software.</span></span>  
  
## <a name="preparing-for-the-solution"></a><span data-ttu-id="a0ce8-142">準備解決方案</span><span class="sxs-lookup"><span data-stu-id="a0ce8-142">Preparing for the Solution</span></span>  
 <span data-ttu-id="a0ce8-143">在準備階段包含下列元素：</span><span class="sxs-lookup"><span data-stu-id="a0ce8-143">Include the following elements in your preparation phase:</span></span>  
  
### <a name="detailed-design-of-the-solution-platform"></a><span data-ttu-id="a0ce8-144">詳細的設計的方案平台</span><span class="sxs-lookup"><span data-stu-id="a0ce8-144">Detailed Design of the Solution Platform</span></span>  
 <span data-ttu-id="a0ce8-145">詳細的解決方案設計有助於通訊，並避免將提升靈活度和效率的所有活動的假設。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-145">A detailed solution design facilitates communications and avoids assumptions, which will improve the agility and effectiveness of all activities.</span></span> <span data-ttu-id="a0ce8-146">您完整應該記錄下列項目：</span><span class="sxs-lookup"><span data-stu-id="a0ce8-146">You should fully document the following elements:</span></span>  
  
- <span data-ttu-id="a0ce8-147">BizTalk Server 資料庫和如何分散到電腦。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-147">BizTalk Server databases and how they will be distributed across computers.</span></span>  
  
- <span data-ttu-id="a0ce8-148">BizTalk 主控件的設計和每一部主機和其執行個體的描述。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-148">BizTalk Host design and descriptions of each host and their instances.</span></span>  
  
- <span data-ttu-id="a0ce8-149">每個協調流程的描述。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-149">Description of each orchestration.</span></span>  
  
- <span data-ttu-id="a0ce8-150">每個管線的描述。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-150">Description of each pipeline.</span></span>  
  
- <span data-ttu-id="a0ce8-151">自訂元件，例如.NET 組件和 COM + 元件的描述。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-151">Description of custom components such as .NET assemblies and COM+ components.</span></span>  
  
  <span data-ttu-id="a0ce8-152">**訊息流程圖**</span><span class="sxs-lookup"><span data-stu-id="a0ce8-152">**Message Flow Diagrams**</span></span>  
  
  <span data-ttu-id="a0ce8-153">建立詳細的訊息流程圖表，以協助您避免任何混淆或 false 的假設，都應該在處理期間發生狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-153">Create detailed message flow diagrams to help avoid any confusion or false assumptions regarding what is supposed to be happening to messages during processing.</span></span> <span data-ttu-id="a0ce8-154">建立訊息流程圖表時，應該考慮下列詳細資料：</span><span class="sxs-lookup"><span data-stu-id="a0ce8-154">The following details should be considered when creating the message flow diagrams:</span></span>  
  
- <span data-ttu-id="a0ce8-155">描述每一種訊息的時間產生的所有訊息都會都傳送，且所有相關的處理完成之前到達接收位置的生命週期。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-155">Describe the lifecycle of each type of message from the time it arrives at a receive location until all resulting messages are sent and all related processing is completed.</span></span>  
  
- <span data-ttu-id="a0ce8-156">描述如何處理變更的錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-156">Describe how processing changes for error conditions.</span></span>  
  
- <span data-ttu-id="a0ce8-157">包含有關相互關聯、 傳遞通知和通知詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-157">Include details about correlation, delivery notifications, and acknowledgements.</span></span>  
  
- <span data-ttu-id="a0ce8-158">效能需求的資訊包括延遲和輸送量。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-158">Include performance requirement information regarding latency and throughput.</span></span>  
  
  <span data-ttu-id="a0ce8-159">**非 Microsoft 軟體的詳細資料**</span><span class="sxs-lookup"><span data-stu-id="a0ce8-159">**Non-Microsoft Software Details**</span></span>  
  
  <span data-ttu-id="a0ce8-160">詳細的解決方案設計一部分都應該詳細記錄所使用的所有非 Microsoft 軟體。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-160">All non-Microsoft software that is used should be fully documented as part of the detailed solution design.</span></span>  
  
  <span data-ttu-id="a0ce8-161">**詳細的硬體堆疊**</span><span class="sxs-lookup"><span data-stu-id="a0ce8-161">**Detailed Hardware Stack**</span></span>  
  
  <span data-ttu-id="a0ce8-162">建置在先前建立的高階硬體圖表上，下列硬體資訊應該詳細記錄：</span><span class="sxs-lookup"><span data-stu-id="a0ce8-162">Building on the previously created high level hardware diagram, the following hardware information should be fully documented:</span></span>  
  
- <span data-ttu-id="a0ce8-163">處理器</span><span class="sxs-lookup"><span data-stu-id="a0ce8-163">Processors</span></span>  
  
  -   <span data-ttu-id="a0ce8-164">類型</span><span class="sxs-lookup"><span data-stu-id="a0ce8-164">Type</span></span>  
  
  -   <span data-ttu-id="a0ce8-165">速度</span><span class="sxs-lookup"><span data-stu-id="a0ce8-165">Speed</span></span>  
  
  -   <span data-ttu-id="a0ce8-166">核心數目</span><span class="sxs-lookup"><span data-stu-id="a0ce8-166">Number of cores</span></span>  
  
  -   <span data-ttu-id="a0ce8-167">超執行緒</span><span class="sxs-lookup"><span data-stu-id="a0ce8-167">Hyperthreading</span></span>  
  
- <span data-ttu-id="a0ce8-168">記憶體</span><span class="sxs-lookup"><span data-stu-id="a0ce8-168">Memory</span></span>  
  
  -   <span data-ttu-id="a0ce8-169">Amount</span><span class="sxs-lookup"><span data-stu-id="a0ce8-169">Amount</span></span>  
  
  -   <span data-ttu-id="a0ce8-170">速度</span><span class="sxs-lookup"><span data-stu-id="a0ce8-170">Speed</span></span>  
  
  -   <span data-ttu-id="a0ce8-171">Parity</span><span class="sxs-lookup"><span data-stu-id="a0ce8-171">Parity</span></span>  
  
- <span data-ttu-id="a0ce8-172">Network</span><span class="sxs-lookup"><span data-stu-id="a0ce8-172">Network</span></span>  
  
  -   <span data-ttu-id="a0ce8-173">網路介面卡 (Nic) 數目</span><span class="sxs-lookup"><span data-stu-id="a0ce8-173">Number of network interface cards (NICs)</span></span>  
  
  -   <span data-ttu-id="a0ce8-174">網路連線的速度</span><span class="sxs-lookup"><span data-stu-id="a0ce8-174">Speed of network</span></span>  
  
- <span data-ttu-id="a0ce8-175">SAN</span><span class="sxs-lookup"><span data-stu-id="a0ce8-175">SAN</span></span>  
  
  -   <span data-ttu-id="a0ce8-176">在每一部電腦中的 SAN 卡數目</span><span class="sxs-lookup"><span data-stu-id="a0ce8-176">Number of SAN cards in each computer</span></span>  
  
  -   <span data-ttu-id="a0ce8-177">針對每個電腦和目的每個 LUN 的邏輯單元編號 (Lun) 的數目</span><span class="sxs-lookup"><span data-stu-id="a0ce8-177">Number of logical unit numbers (LUNs) for each computer and purpose for each LUN</span></span>  
  
  -   <span data-ttu-id="a0ce8-178">速度的存放區域網路 (SAN) 卡</span><span class="sxs-lookup"><span data-stu-id="a0ce8-178">Speed of storage area network (SAN) Cards</span></span>  
  
  -   <span data-ttu-id="a0ce8-179">SAN 卡組態詳細資料</span><span class="sxs-lookup"><span data-stu-id="a0ce8-179">SAN card configuration details</span></span>  
  
  -   <span data-ttu-id="a0ce8-180">SAN 磁碟配置、 格式化和分割</span><span class="sxs-lookup"><span data-stu-id="a0ce8-180">SAN disk allocation, formatting, and partitioning</span></span>  
  
- <span data-ttu-id="a0ce8-181">磁碟</span><span class="sxs-lookup"><span data-stu-id="a0ce8-181">Disk</span></span>  
  
  -   <span data-ttu-id="a0ce8-182">每一部電腦的本機磁碟詳細資料</span><span class="sxs-lookup"><span data-stu-id="a0ce8-182">Local disk details for each computer</span></span>  
  
  -   <span data-ttu-id="a0ce8-183">使用本機的磁碟格式</span><span class="sxs-lookup"><span data-stu-id="a0ce8-183">Formatting used for local disks</span></span>  
  
  -   <span data-ttu-id="a0ce8-184">資料分割的本機磁碟的詳細資料</span><span class="sxs-lookup"><span data-stu-id="a0ce8-184">Partitioning details for local disks</span></span>  
  
- <span data-ttu-id="a0ce8-185">Cache</span><span class="sxs-lookup"><span data-stu-id="a0ce8-185">Cache</span></span>  
  
  -   <span data-ttu-id="a0ce8-186">L2 快取容量</span><span class="sxs-lookup"><span data-stu-id="a0ce8-186">L2 Cache amount</span></span>  
  
  -   <span data-ttu-id="a0ce8-187">L3 快取容量</span><span class="sxs-lookup"><span data-stu-id="a0ce8-187">L3 Cache amount</span></span>  
  
  <span data-ttu-id="a0ce8-188">**詳細的軟體堆疊**</span><span class="sxs-lookup"><span data-stu-id="a0ce8-188">**Detailed Software Stack**</span></span>  
  
  <span data-ttu-id="a0ce8-189">下列的軟體資訊應該加以記錄：</span><span class="sxs-lookup"><span data-stu-id="a0ce8-189">The following software information should be documented:</span></span>  
  
- <span data-ttu-id="a0ce8-190">特定作業系統版本、 版本及架構</span><span class="sxs-lookup"><span data-stu-id="a0ce8-190">Specific operating system versions, editions, and architecture</span></span>  
  
- <span data-ttu-id="a0ce8-191">特定的作業系統功能</span><span class="sxs-lookup"><span data-stu-id="a0ce8-191">Specific operating system features</span></span>  
  
- <span data-ttu-id="a0ce8-192">在每一部電腦上安裝特定軟體</span><span class="sxs-lookup"><span data-stu-id="a0ce8-192">Specific software installed on each computer</span></span>  
  
- <span data-ttu-id="a0ce8-193">特定驅動程式</span><span class="sxs-lookup"><span data-stu-id="a0ce8-193">Specific drivers</span></span>  
  
- <span data-ttu-id="a0ce8-194">Service Pack 及其他更新</span><span class="sxs-lookup"><span data-stu-id="a0ce8-194">Service Packs and other updates</span></span>  
  
- <span data-ttu-id="a0ce8-195">如果兩者的差異從預設值所使用的所有軟體和作業系統功能的組態值</span><span class="sxs-lookup"><span data-stu-id="a0ce8-195">Configuration values for all software and operating system features used if they vary from default values</span></span>  
  
## <a name="building-out-the-environment-for-the-solution"></a><span data-ttu-id="a0ce8-196">建置方案的環境</span><span class="sxs-lookup"><span data-stu-id="a0ce8-196">Building Out the Environment for the Solution</span></span>  
 <span data-ttu-id="a0ce8-197">詳細的安裝指示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和軟體需求[BizTalk Server 安裝指南](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。</span><span class="sxs-lookup"><span data-stu-id="a0ce8-197">Detailed instructions for installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the software requirements are in the [BizTalk Server Installation Guides](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a0ce8-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0ce8-198">See Also</span></span>  
 [<span data-ttu-id="a0ce8-199">規劃 BizTalk Server 層</span><span class="sxs-lookup"><span data-stu-id="a0ce8-199">Planning the BizTalk Server Tier</span></span>](../technical-guides/planning-the-biztalk-server-tier.md)
