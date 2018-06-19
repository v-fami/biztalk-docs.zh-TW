---
title: 階段 3： 準備評定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d153ed62-f2cc-4080-8912-c98ecdd329f5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 890047f6a13352d89d33d9514883dc20eacd4001
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22301838"
---
# <a name="phase-3-preparing-for-the-assessment"></a><span data-ttu-id="977f4-102">階段 3： 準備進行評估</span><span class="sxs-lookup"><span data-stu-id="977f4-102">Phase 3: Preparing for the Assessment</span></span>
<span data-ttu-id="977f4-103">準備效能評估階段可以視為 「 範圍 」 階段的 「 作法 」 和 「 如何 」 計劃 」 階段的 「 時機 」。</span><span class="sxs-lookup"><span data-stu-id="977f4-103">The Prepare phase of a performance assessment can be thought of as the “how” to the Scope phase’s “what” and the Plan phase’s “when.”</span></span> <span data-ttu-id="977f4-104">此時效能評定，所有專案關係人應該均同意 engagement 和計劃的範圍進行實驗室。</span><span class="sxs-lookup"><span data-stu-id="977f4-104">At this point in the performance assessment, all stakeholders should have agreed upon the scope of the engagement and the plans for conducting the lab.</span></span> <span data-ttu-id="977f4-105">它是在其中執行計畫，而會採取的步驟以準備好的效能實驗室執行效能評定的準備階段。</span><span class="sxs-lookup"><span data-stu-id="977f4-105">It is in the Prepare phase of the performance assessment where the plans are executed and steps are taken to get ready for execution of the performance lab.</span></span>  
  
 <span data-ttu-id="977f4-106">本主題說明 BizTalk Server 效能評定的準備階段的各個層面。</span><span class="sxs-lookup"><span data-stu-id="977f4-106">This topic describes the various aspects of the Prepare phase of a BizTalk Server performance assessment.</span></span>  
  
## <a name="detailed-design-of-the-solution-platform"></a><span data-ttu-id="977f4-107">詳細的方案平台設計</span><span class="sxs-lookup"><span data-stu-id="977f4-107">Detailed design of the solution platform</span></span>  
 <span data-ttu-id="977f4-108">詳細的解決方案設計有助於進行通訊，並避免將來提高靈活度及所有活動的效用的假設。</span><span class="sxs-lookup"><span data-stu-id="977f4-108">A detailed solution design facilitates communications and avoids assumptions, which will improve the agility and effectiveness of all activities.</span></span> <span data-ttu-id="977f4-109">您應該完整記載下列項目：</span><span class="sxs-lookup"><span data-stu-id="977f4-109">You should fully document the following elements:</span></span>  
  
-   <span data-ttu-id="977f4-110">**BizTalk Server 資料庫和如何分散在電腦**-SQL Server 效能是其中一個 BizTalk 伺服器的整體效能的關鍵因素。</span><span class="sxs-lookup"><span data-stu-id="977f4-110">**BizTalk Server databases and how they will be distributed across computers** - SQL Server performance is one of the key factors in overall BizTalk Server performance.</span></span> <span data-ttu-id="977f4-111">如果 SQL Server 發生資源條件約束，這會影響 BizTalk Server 處理訊息的能力。</span><span class="sxs-lookup"><span data-stu-id="977f4-111">If SQL Server is experiencing resource constraints, this will impact the ability of BizTalk Server to process messages.</span></span> <span data-ttu-id="977f4-112">會影響 BizTalk 資料庫效能的主要因素是磁碟上裝載的速度。</span><span class="sxs-lookup"><span data-stu-id="977f4-112">The main factor that influences BizTalk database performance is the speed of disks that they are hosted on.</span></span> <span data-ttu-id="977f4-113">將交易記錄檔和資料庫檔案的每個 BizTalk 資料庫到不同的磁碟機或 SAN LUN 可能會非常改善 BizTalk Server 的整體效能。</span><span class="sxs-lookup"><span data-stu-id="977f4-113">Separating the transaction log and database files for each BizTalk database onto separate drives or SAN LUN’s has been shown to remarkably improve the overall performance of BizTalk Server.</span></span> <span data-ttu-id="977f4-114">因此，很重要，這項資訊會記錄在更容易存取的方式。</span><span class="sxs-lookup"><span data-stu-id="977f4-114">Therefore, it is important that this information be recorded in an easily accessible manner.</span></span> <span data-ttu-id="977f4-115">將用於實際執行環境中的值應該記錄詳細的解決方案設計中。</span><span class="sxs-lookup"><span data-stu-id="977f4-115">The values that will be used in the production environment should be documented in the detailed solution design.</span></span> <span data-ttu-id="977f4-116">下表提供如何完成的範例。</span><span class="sxs-lookup"><span data-stu-id="977f4-116">The following table provides an example of how this can be done.</span></span>  
  
    |<span data-ttu-id="977f4-117">BizTalk 資料庫</span><span class="sxs-lookup"><span data-stu-id="977f4-117">BizTalk Database</span></span>|<span data-ttu-id="977f4-118">磁碟區名稱</span><span class="sxs-lookup"><span data-stu-id="977f4-118">Volume Name</span></span>|<span data-ttu-id="977f4-119">檔案</span><span class="sxs-lookup"><span data-stu-id="977f4-119">Files</span></span>|<span data-ttu-id="977f4-120">LUN # 或 ML_ #</span><span class="sxs-lookup"><span data-stu-id="977f4-120">LUN# or ML_#</span></span>|<span data-ttu-id="977f4-121">實體的 LUN 大小 (GB)</span><span class="sxs-lookup"><span data-stu-id="977f4-121">Physical LUN Size (GB)</span></span>|  
    |----------------------|-----------------|-----------|---------------------|------------------------------|  
    |<span data-ttu-id="977f4-122">MessageBox</span><span class="sxs-lookup"><span data-stu-id="977f4-122">MessageBox</span></span>|<span data-ttu-id="977f4-123">Data_TempDb_1</span><span class="sxs-lookup"><span data-stu-id="977f4-123">Data_TempDb_1</span></span>|<span data-ttu-id="977f4-124">TEMPDB、 主機和 MSDB 資料檔案</span><span class="sxs-lookup"><span data-stu-id="977f4-124">TEMPDB,  MASTER, and MSDB data files</span></span>|<span data-ttu-id="977f4-125">1</span><span class="sxs-lookup"><span data-stu-id="977f4-125">1</span></span>|<span data-ttu-id="977f4-126">134</span><span class="sxs-lookup"><span data-stu-id="977f4-126">134</span></span>|  
    ||<span data-ttu-id="977f4-127">Logs_TempDb_1</span><span class="sxs-lookup"><span data-stu-id="977f4-127">Logs_TempDb_1</span></span>|<span data-ttu-id="977f4-128">TEMPDB、 主機和 MSDB 交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="977f4-128">TEMPDB,  MASTER, and MSDB transaction log files</span></span>|<span data-ttu-id="977f4-129">2</span><span class="sxs-lookup"><span data-stu-id="977f4-129">2</span></span>|<span data-ttu-id="977f4-130">134</span><span class="sxs-lookup"><span data-stu-id="977f4-130">134</span></span>|  
    ||<span data-ttu-id="977f4-131">Data_BtsMsgBox</span><span class="sxs-lookup"><span data-stu-id="977f4-131">Data_BtsMsgBox</span></span>|<span data-ttu-id="977f4-132">BizTalkMsgBoxDb 資料檔案</span><span class="sxs-lookup"><span data-stu-id="977f4-132">BizTalkMsgBoxDb data file</span></span>|<span data-ttu-id="977f4-133">3</span><span class="sxs-lookup"><span data-stu-id="977f4-133">3</span></span>|<span data-ttu-id="977f4-134">134</span><span class="sxs-lookup"><span data-stu-id="977f4-134">134</span></span>|  
    ||<span data-ttu-id="977f4-135">Logs_BtsMsgBox</span><span class="sxs-lookup"><span data-stu-id="977f4-135">Logs_BtsMsgBox</span></span>|<span data-ttu-id="977f4-136">BizTalkMsgBoxDb 交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="977f4-136">BizTalkMsgBoxDb transaction log file</span></span>|<span data-ttu-id="977f4-137">4</span><span class="sxs-lookup"><span data-stu-id="977f4-137">4</span></span>|<span data-ttu-id="977f4-138">134</span><span class="sxs-lookup"><span data-stu-id="977f4-138">134</span></span>|  
    |<span data-ttu-id="977f4-139">BAM</span><span class="sxs-lookup"><span data-stu-id="977f4-139">BAM</span></span>|<span data-ttu-id="977f4-140">Data_TempDb_2</span><span class="sxs-lookup"><span data-stu-id="977f4-140">Data_TempDb_2</span></span>|<span data-ttu-id="977f4-141">TEMPDB、 主機和 MSDB 資料檔案</span><span class="sxs-lookup"><span data-stu-id="977f4-141">TEMPDB, MASTER, and MSDB data files</span></span>|<span data-ttu-id="977f4-142">5</span><span class="sxs-lookup"><span data-stu-id="977f4-142">5</span></span>|<span data-ttu-id="977f4-143">67</span><span class="sxs-lookup"><span data-stu-id="977f4-143">67</span></span>|  
    ||<span data-ttu-id="977f4-144">Logs_TempDb_2</span><span class="sxs-lookup"><span data-stu-id="977f4-144">Logs_TempDb_2</span></span>|<span data-ttu-id="977f4-145">TEMPDB、 主機和 MSDB 交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="977f4-145">TEMPDB, MASTER, and MSDB transaction log files</span></span>|<span data-ttu-id="977f4-146">6</span><span class="sxs-lookup"><span data-stu-id="977f4-146">6</span></span>|<span data-ttu-id="977f4-147">67</span><span class="sxs-lookup"><span data-stu-id="977f4-147">67</span></span>|  
    ||<span data-ttu-id="977f4-148">Data_BAM</span><span class="sxs-lookup"><span data-stu-id="977f4-148">Data_BAM</span></span>|<span data-ttu-id="977f4-149">BAMPrimaryImport 資料檔案</span><span class="sxs-lookup"><span data-stu-id="977f4-149">BAMPrimaryImport data file</span></span>|<span data-ttu-id="977f4-150">7</span><span class="sxs-lookup"><span data-stu-id="977f4-150">7</span></span>|<span data-ttu-id="977f4-151">134</span><span class="sxs-lookup"><span data-stu-id="977f4-151">134</span></span>|  
    ||<span data-ttu-id="977f4-152">Logs_BAM</span><span class="sxs-lookup"><span data-stu-id="977f4-152">Logs_BAM</span></span>|<span data-ttu-id="977f4-153">BAMPrimaryImport 的交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="977f4-153">BAMPrimaryImport transaction log file</span></span>|<span data-ttu-id="977f4-154">8</span><span class="sxs-lookup"><span data-stu-id="977f4-154">8</span></span>|<span data-ttu-id="977f4-155">134</span><span class="sxs-lookup"><span data-stu-id="977f4-155">134</span></span>|  
    |<span data-ttu-id="977f4-156">BizTalk 追蹤、 管理、 單一登入，以及規則引擎資料庫</span><span class="sxs-lookup"><span data-stu-id="977f4-156">BizTalk Tracking, Management, Single Sign-On, and Rule Engine databases</span></span>|<span data-ttu-id="977f4-157">Data_TempDb_3</span><span class="sxs-lookup"><span data-stu-id="977f4-157">Data_TempDb_3</span></span>|<span data-ttu-id="977f4-158">TEMPDB、 MASTER、 MSDB、 BizTalkDTADb、 BizTalkMgmtDb、 ENTSSO 和 BizTalkRuleEngineDb 資料檔案</span><span class="sxs-lookup"><span data-stu-id="977f4-158">TEMPDB,  MASTER, MSDB, BizTalkDTADb, BizTalkMgmtDb, ENTSSO, and BizTalkRuleEngineDb data files</span></span>|<span data-ttu-id="977f4-159">9</span><span class="sxs-lookup"><span data-stu-id="977f4-159">9</span></span>|<span data-ttu-id="977f4-160">67</span><span class="sxs-lookup"><span data-stu-id="977f4-160">67</span></span>|  
    ||<span data-ttu-id="977f4-161">Logs_TempDb_3</span><span class="sxs-lookup"><span data-stu-id="977f4-161">Logs_TempDb_3</span></span>|<span data-ttu-id="977f4-162">TEMPDB、 MASTER、 MSDB、 BizTalkDTADb、 BizTalkMgmtDb、 ENTSSO 和 BizTalkRuleEngineDb 交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="977f4-162">TEMPDB,  MASTER, MSDB, BizTalkDTADb, BizTalkMgmtDb, ENTSSO, and BizTalkRuleEngineDb transaction log files</span></span>|<span data-ttu-id="977f4-163">10</span><span class="sxs-lookup"><span data-stu-id="977f4-163">10</span></span>|<span data-ttu-id="977f4-164">67</span><span class="sxs-lookup"><span data-stu-id="977f4-164">67</span></span>|  
  
-   <span data-ttu-id="977f4-165">**BizTalk 主控件的設計和每個主控件和其執行個體的描述。**</span><span class="sxs-lookup"><span data-stu-id="977f4-165">**BizTalk Host design and descriptions of each host and their instances.**</span></span>  
  
-   <span data-ttu-id="977f4-166">**每個協調流程的描述。**</span><span class="sxs-lookup"><span data-stu-id="977f4-166">**Description of each orchestration.**</span></span>  
  
-   <span data-ttu-id="977f4-167">**每個管線的描述。**</span><span class="sxs-lookup"><span data-stu-id="977f4-167">**Description of each pipeline.**</span></span>  
  
-   <span data-ttu-id="977f4-168">**自訂元件，例如.NET 組件和 COM + 元件的描述。**</span><span class="sxs-lookup"><span data-stu-id="977f4-168">**Description of custom components such as .NET assemblies and COM+ components.**</span></span>  
  
## <a name="detailed-architecture-diagram"></a><span data-ttu-id="977f4-169">詳細的架構圖</span><span class="sxs-lookup"><span data-stu-id="977f4-169">Detailed architecture diagram</span></span>  
 <span data-ttu-id="977f4-170">下圖說明可用於效能評定架構圖表。</span><span class="sxs-lookup"><span data-stu-id="977f4-170">The following diagram illustrates an architecture diagram that could be used for a performance assessment.</span></span>  
  
 <span data-ttu-id="977f4-171">![BizTalk 架構圖](../technical-guides/media/architecturediagram.gif "ArchitectureDiagram")</span><span class="sxs-lookup"><span data-stu-id="977f4-171">![BizTalk Architecture Diagram](../technical-guides/media/architecturediagram.gif "ArchitectureDiagram")</span></span>  
<span data-ttu-id="977f4-172">BizTalk 架構圖</span><span class="sxs-lookup"><span data-stu-id="977f4-172">BizTalk Architecture Diagram</span></span>  
  
## <a name="message-flow-diagrams"></a><span data-ttu-id="977f4-173">訊息流程圖</span><span class="sxs-lookup"><span data-stu-id="977f4-173">Message flow diagrams</span></span>  
 <span data-ttu-id="977f4-174">建立詳細的訊息流程圖表，為了避免混淆或 false 的假設，都應該在處理期間發生狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="977f4-174">Create detailed message flow diagrams to help prevent confusion or false assumptions regarding what is supposed to be happening to messages during processing.</span></span>  
  
 <span data-ttu-id="977f4-175">當而加以進行歷程改善 BizTalk 解決方案，我們會傾向於認為訊息流程通過系統。</span><span class="sxs-lookup"><span data-stu-id="977f4-175">When thinking about a BizTalk solution holistically, we tend to think of the message flow through the system.</span></span> <span data-ttu-id="977f4-176">進行效能測試，因為流程的所有部分必須都視為潛在的瓶頸時，此訊息流程檢視方塊是特別重要。</span><span class="sxs-lookup"><span data-stu-id="977f4-176">This Message Flow perspective is especially important when doing performance testing because all parts of the flow must be considered as potential bottlenecks.</span></span> <span data-ttu-id="977f4-177">訊息流程圖會使任何混淆或 false 的假設，都應該在每個測試期間發生狀況的訊息執行。</span><span class="sxs-lookup"><span data-stu-id="977f4-177">Having a message flow diagram prevents any confusion or false assumptions regarding what is supposed to be happening to messages during each test run.</span></span>  
  
 <span data-ttu-id="977f4-178">在下列範例中，建立使用簡單的 Visio 圖形，不論背景專案上的每個人都可以快速了解訊息如何抵達到系統、 解決方案的哪些部分互動的訊息，和最後其中訊息會落入之後處理程序。</span><span class="sxs-lookup"><span data-stu-id="977f4-178">In the following example, created using simple Visio shapes, everyone on the project regardless of background can quickly understand how a message gets into the system, what parts of the solutions interact with the message, and finally where the message lands after processing.</span></span>  
  
 <span data-ttu-id="977f4-179">![Message Flow Diagram](../technical-guides/media/11c5afac-5c1b-42a5-8947-7c6d0ca4e2df.gif "11c5afac-5c1b-42a5-8947-7c6d0ca4e2df")</span><span class="sxs-lookup"><span data-stu-id="977f4-179">![Message Flow Diagram](../technical-guides/media/11c5afac-5c1b-42a5-8947-7c6d0ca4e2df.gif "11c5afac-5c1b-42a5-8947-7c6d0ca4e2df")</span></span>  
<span data-ttu-id="977f4-180">訊息流程圖</span><span class="sxs-lookup"><span data-stu-id="977f4-180">Message Flow Diagram</span></span>  
  
 <span data-ttu-id="977f4-181">建立訊息流程圖表時，應該考慮下列詳細資料：</span><span class="sxs-lookup"><span data-stu-id="977f4-181">The following details should be considered when creating the message flow diagrams:</span></span>  
  
-   <span data-ttu-id="977f4-182">描述每一種訊息的時間所有產生的訊息會傳送，且所有相關的處理完成，直到到達接收位置的生命週期。</span><span class="sxs-lookup"><span data-stu-id="977f4-182">Describe the lifecycle of each type of message from the time it arrives at a receive location until all resulting messages are sent and all related processing is completed.</span></span>  
  
-   <span data-ttu-id="977f4-183">描述如何處理錯誤狀況的變更時。</span><span class="sxs-lookup"><span data-stu-id="977f4-183">Describe how processing changes for error conditions.</span></span>  
  
-   <span data-ttu-id="977f4-184">包含有關相互關聯、 傳遞通知和通知詳細資料。</span><span class="sxs-lookup"><span data-stu-id="977f4-184">Include details about correlation, delivery notifications, and acknowledgements.</span></span>  
  
-   <span data-ttu-id="977f4-185">包含有關在外部系統上的相依性的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="977f4-185">Include details about dependence on external systems.</span></span>  
  
-   <span data-ttu-id="977f4-186">效能需求的資訊包括延遲和輸送量。</span><span class="sxs-lookup"><span data-stu-id="977f4-186">Include performance requirement information regarding latency and throughput.</span></span>  
  
## <a name="third-party-software-details"></a><span data-ttu-id="977f4-187">第三方軟體詳細資料</span><span class="sxs-lookup"><span data-stu-id="977f4-187">Third-party software details</span></span>  
 <span data-ttu-id="977f4-188">詳細的解決方案設計的一部分，應該完整記錄所使用的所有非 Microsoft 軟體。</span><span class="sxs-lookup"><span data-stu-id="977f4-188">All non-Microsoft software that is used should be fully documented as part of the detailed solution design.</span></span>  
  
## <a name="detailed-lab-hardware-stack"></a><span data-ttu-id="977f4-189">詳細的實驗室硬體堆疊</span><span class="sxs-lookup"><span data-stu-id="977f4-189">Detailed lab hardware stack</span></span>  
 <span data-ttu-id="977f4-190">建置在先前建立的高階硬體圖表上，下列硬體資訊應該是完整記錄：</span><span class="sxs-lookup"><span data-stu-id="977f4-190">Building on the previously created high-level hardware diagram, the following hardware information should be fully documented:</span></span>  
  
-   <span data-ttu-id="977f4-191">處理器</span><span class="sxs-lookup"><span data-stu-id="977f4-191">Processors</span></span>  
  
    -   <span data-ttu-id="977f4-192">類型</span><span class="sxs-lookup"><span data-stu-id="977f4-192">Type</span></span>  
  
    -   <span data-ttu-id="977f4-193">速度</span><span class="sxs-lookup"><span data-stu-id="977f4-193">Speed</span></span>  
  
    -   <span data-ttu-id="977f4-194">核心數目</span><span class="sxs-lookup"><span data-stu-id="977f4-194">Number of cores</span></span>  
  
    -   <span data-ttu-id="977f4-195">超執行緒</span><span class="sxs-lookup"><span data-stu-id="977f4-195">Hyperthreading</span></span>  
  
-   <span data-ttu-id="977f4-196">記憶體</span><span class="sxs-lookup"><span data-stu-id="977f4-196">Memory</span></span>  
  
    -   <span data-ttu-id="977f4-197">Amount</span><span class="sxs-lookup"><span data-stu-id="977f4-197">Amount</span></span>  
  
    -   <span data-ttu-id="977f4-198">速度</span><span class="sxs-lookup"><span data-stu-id="977f4-198">Speed</span></span>  
  
    -   <span data-ttu-id="977f4-199">Parity</span><span class="sxs-lookup"><span data-stu-id="977f4-199">Parity</span></span>  
  
-   <span data-ttu-id="977f4-200">網路</span><span class="sxs-lookup"><span data-stu-id="977f4-200">Network</span></span>  
  
    -   <span data-ttu-id="977f4-201">網路介面卡 (Nic) 數目</span><span class="sxs-lookup"><span data-stu-id="977f4-201">Number of network interface cards (NICs)</span></span>  
  
    -   <span data-ttu-id="977f4-202">網路連線的速度</span><span class="sxs-lookup"><span data-stu-id="977f4-202">Speed of network</span></span>  
  
-   <span data-ttu-id="977f4-203">SAN</span><span class="sxs-lookup"><span data-stu-id="977f4-203">SAN</span></span>  
  
    -   <span data-ttu-id="977f4-204">在每台電腦的 SAN 卡數目</span><span class="sxs-lookup"><span data-stu-id="977f4-204">Number of SAN cards in each computer</span></span>  
  
    -   <span data-ttu-id="977f4-205">針對每個電腦和目的每個 LUN 的邏輯單元編號 (Lun) 的數目</span><span class="sxs-lookup"><span data-stu-id="977f4-205">Number of logical unit numbers (LUNs) for each computer and purpose for each LUN</span></span>  
  
    -   <span data-ttu-id="977f4-206">速度的存放區域網路 (SAN) 卡</span><span class="sxs-lookup"><span data-stu-id="977f4-206">Speed of storage area network (SAN) Cards</span></span>  
  
    -   <span data-ttu-id="977f4-207">SAN 的介面卡的組態詳細資料</span><span class="sxs-lookup"><span data-stu-id="977f4-207">SAN card configuration details</span></span>  
  
    -   <span data-ttu-id="977f4-208">SAN 磁碟配置、 格式化和分割</span><span class="sxs-lookup"><span data-stu-id="977f4-208">SAN disk allocation, formatting, and partitioning</span></span>  
  
-   <span data-ttu-id="977f4-209">磁碟</span><span class="sxs-lookup"><span data-stu-id="977f4-209">Disk</span></span>  
  
    -   <span data-ttu-id="977f4-210">每一部電腦的本機磁碟詳細資料</span><span class="sxs-lookup"><span data-stu-id="977f4-210">Local disk details for each computer</span></span>  
  
    -   <span data-ttu-id="977f4-211">格式設定用於本機磁碟</span><span class="sxs-lookup"><span data-stu-id="977f4-211">Formatting used for local disks</span></span>  
  
    -   <span data-ttu-id="977f4-212">資料分割的本機磁碟的詳細資料</span><span class="sxs-lookup"><span data-stu-id="977f4-212">Partitioning details for local disks</span></span>  
  
-   <span data-ttu-id="977f4-213">Cache</span><span class="sxs-lookup"><span data-stu-id="977f4-213">Cache</span></span>  
  
    -   <span data-ttu-id="977f4-214">L2 快取容量</span><span class="sxs-lookup"><span data-stu-id="977f4-214">L2 Cache amount</span></span>  
  
    -   <span data-ttu-id="977f4-215">L3 快取容量</span><span class="sxs-lookup"><span data-stu-id="977f4-215">L3 Cache amount</span></span>  
  
## <a name="detailed-lab-software-stack"></a><span data-ttu-id="977f4-216">詳細的實驗室軟體堆疊</span><span class="sxs-lookup"><span data-stu-id="977f4-216">Detailed lab software stack</span></span>  
 <span data-ttu-id="977f4-217">應該記錄下列軟體的資訊：</span><span class="sxs-lookup"><span data-stu-id="977f4-217">The following software information should be documented:</span></span>  
  
-   <span data-ttu-id="977f4-218">特定作業系統版本、 版本和架構</span><span class="sxs-lookup"><span data-stu-id="977f4-218">Specific operating system versions, editions, and architecture</span></span>  
  
-   <span data-ttu-id="977f4-219">特定的作業系統功能</span><span class="sxs-lookup"><span data-stu-id="977f4-219">Specific operating system features</span></span>  
  
-   <span data-ttu-id="977f4-220">在每一部電腦上已安裝特定軟體</span><span class="sxs-lookup"><span data-stu-id="977f4-220">Specific software installed on each computer</span></span>  
  
-   <span data-ttu-id="977f4-221">特定驅動程式</span><span class="sxs-lookup"><span data-stu-id="977f4-221">Specific drivers</span></span>  
  
-   <span data-ttu-id="977f4-222">Service Pack 及其他更新</span><span class="sxs-lookup"><span data-stu-id="977f4-222">Service Packs and other updates</span></span>  
  
-   <span data-ttu-id="977f4-223">如果兩者的差異的預設值使用的所有軟體和作業系統功能的組態值</span><span class="sxs-lookup"><span data-stu-id="977f4-223">Configuration values for all software and operating system features used if they vary from default values</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="977f4-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="977f4-224">See Also</span></span>  
 [<span data-ttu-id="977f4-225">效能評定階段</span><span class="sxs-lookup"><span data-stu-id="977f4-225">Phases of a Performance Assessment</span></span>](../technical-guides/phases-of-a-performance-assessment.md)