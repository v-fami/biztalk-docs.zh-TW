---
title: 第 4 個階段： 建立評估環境 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b90d7c5-60ca-4a81-b3d9-6d4e9d91e684
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88fa45a17e1475aee989f22d2f8d1ef0d015a9ce
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008671"
---
# <a name="phase-4-building-the-assessment-environment"></a><span data-ttu-id="8e203-102">第 4 個階段： 建立評估環境</span><span class="sxs-lookup"><span data-stu-id="8e203-102">Phase 4: Building the Assessment Environment</span></span>
<span data-ttu-id="8e203-103">建立實驗室效能評估階段用來安裝的硬體和軟體環境中前一個階段中的設計決策的一致性。</span><span class="sxs-lookup"><span data-stu-id="8e203-103">The Build lab phase of a performance assessment is used to install the hardware and software for the environment in conformance to the design decisions made in previous phases.</span></span> <span data-ttu-id="8e203-104">建立實驗室階段可能會很費時，因為它不重疊稍早階段的此階段不尋常。</span><span class="sxs-lookup"><span data-stu-id="8e203-104">Because the Build lab phase can be time consuming, it is not unusual for this phase to overlap earlier phases.</span></span> <span data-ttu-id="8e203-105">在許多情況下，硬體和作業系統可能會先安裝最終決定對於應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="8e203-105">In many scenarios, the hardware and operating system may be installed before a final decision has been made as to the application architecture.</span></span> <span data-ttu-id="8e203-106">效能評定的組建實驗室階段通常包括本主題中討論的工作。</span><span class="sxs-lookup"><span data-stu-id="8e203-106">The Build lab phase of a performance assessment typically includes the tasks discussed in this topic.</span></span>  
  
## <a name="obtain-all-build-lab-infrastructure-at-least-a-week-in-advance-of-the-lab-start-date"></a><span data-ttu-id="8e203-107">取得實驗室開始日期之前至少一週的所有組建實驗室基礎結構</span><span class="sxs-lookup"><span data-stu-id="8e203-107">Obtain all build-lab infrastructure at least a week in advance of the lab start date</span></span>  
 <span data-ttu-id="8e203-108">實驗室開始日期前一週至少有必要的硬體和軟體的所有可用的計劃。</span><span class="sxs-lookup"><span data-stu-id="8e203-108">Plan to have available all of the required hardware and software at least a week before the lab start date.</span></span> <span data-ttu-id="8e203-109">這可確保的必要的基礎結構要為不會浪費寶貴實驗室時間。</span><span class="sxs-lookup"><span data-stu-id="8e203-109">This will ensure that valuable lab time is not wasted for want of the required infrastructure.</span></span>  
  
## <a name="configure-third-party-software-systems"></a><span data-ttu-id="8e203-110">設定第三方軟體系統</span><span class="sxs-lookup"><span data-stu-id="8e203-110">Configure third-party software systems</span></span>  
 <span data-ttu-id="8e203-111">可能需要建立和設定，才能開始進行實驗室的協力廠商系統。</span><span class="sxs-lookup"><span data-stu-id="8e203-111">There may be third-party systems that need to be built out and configured before the lab can begin.</span></span> <span data-ttu-id="8e203-112">如果需要這些系統的相關主題專家 (Sme)，請務必外延展組建和實驗室執行階段排程。</span><span class="sxs-lookup"><span data-stu-id="8e203-112">If subject matter experts (SMEs) are required for these systems, be sure they are scheduled during the build-out and lab execution stages.</span></span> <span data-ttu-id="8e203-113">請確定它們完整記錄其建置出程序。</span><span class="sxs-lookup"><span data-stu-id="8e203-113">Ensure that they thoroughly document their build-out procedures.</span></span>  
  
## <a name="install-and-configure-the-biztalk-server-environment"></a><span data-ttu-id="8e203-114">安裝和設定 BizTalk Server 環境</span><span class="sxs-lookup"><span data-stu-id="8e203-114">Install and configure the BizTalk Server environment</span></span>  
 <span data-ttu-id="8e203-115">中會有安裝 BizTalk Server 和必要的相依性軟體的詳細的指示[安裝和升級指南](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。</span><span class="sxs-lookup"><span data-stu-id="8e203-115">Detailed instructions for installing BizTalk Server and the required dependency software are in the [Installation and Upgrade Guides](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span> <span data-ttu-id="8e203-116">已成功安裝和設定 BizTalk Server 環境之後, 就可以完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="8e203-116">After successfully installing and configuring the BizTalk Server environment, complete the following tasks:</span></span>  
  
-   <span data-ttu-id="8e203-117">請遵循列示的建議[操作的整備檢查清單](operational-readiness-checklists.md)</span><span class="sxs-lookup"><span data-stu-id="8e203-117">Follow the recommendations listed in the [Operational Readiness Checklists](operational-readiness-checklists.md)</span></span>
  
-   <span data-ttu-id="8e203-118">請遵循建議[最佳化效能](../technical-guides/optimizing-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="8e203-118">Follow the recommendations in [Optimizing Performance](../technical-guides/optimizing-performance.md).</span></span>  
  
-   <span data-ttu-id="8e203-119">請確定所有電腦的時間正確同步都處理。</span><span class="sxs-lookup"><span data-stu-id="8e203-119">Ensure all computer times are properly synchronized.</span></span>  
  
-   <span data-ttu-id="8e203-120">請確認在環境中的所有電腦之間的 MSDTC 功能。</span><span class="sxs-lookup"><span data-stu-id="8e203-120">Verify MSDTC functionality between all computers in the environment.</span></span>  
  
-   <span data-ttu-id="8e203-121">請確定任何自訂的追蹤/記錄已停用，除非絕對必要的。</span><span class="sxs-lookup"><span data-stu-id="8e203-121">Ensure any custom tracing/logging is disabled unless absolutely needed.</span></span>  
  
-   <span data-ttu-id="8e203-122">安裝 Visual Studio Ultimate edition 進行負載測試。</span><span class="sxs-lookup"><span data-stu-id="8e203-122">Install the Visual Studio Ultimate edition for load testing.</span></span>  <span data-ttu-id="8e203-123">如需如何執行自動化測試使用 Visual Studio 的詳細資訊，請參閱[有助於自動化測試使用 Visual Studio](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="8e203-123">For more information about how to perform automated testing using Visual Studio, see [Using Visual Studio to Facilitate Automated Testing](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md).</span></span>  
  
-   <span data-ttu-id="8e203-124">安裝程式的效能監視器計數器和記錄檔，視需要。</span><span class="sxs-lookup"><span data-stu-id="8e203-124">Setup Performance Monitor counters and logs, as needed.</span></span>  
  
-   <span data-ttu-id="8e203-125">安裝程式的偵錯的電腦效能評估的範圍內的程式碼變更時，偵錯方案。</span><span class="sxs-lookup"><span data-stu-id="8e203-125">Setup a debugging computer to debug the solution if code changes are within the scope of the performance assessment.</span></span>  
  
-   <span data-ttu-id="8e203-126">所有的硬碟進行磁碟重組。</span><span class="sxs-lookup"><span data-stu-id="8e203-126">Defragment all hard drives.</span></span>  
  
-   <span data-ttu-id="8e203-127">停用防毒即時掃描。</span><span class="sxs-lookup"><span data-stu-id="8e203-127">Disable antivirus real time scanning.</span></span>  
  
-   <span data-ttu-id="8e203-128">備份企業單一登入主要密碼。</span><span class="sxs-lookup"><span data-stu-id="8e203-128">Back up the Enterprise Single Sign-On Master Secret.</span></span>  
  
## <a name="install-the-biztalk-server-application-to-be-tested"></a><span data-ttu-id="8e203-129">安裝 BizTalk Server 應用程式進行測試</span><span class="sxs-lookup"><span data-stu-id="8e203-129">Install the BizTalk Server application to be tested</span></span>  
 <span data-ttu-id="8e203-130">要測試應用程式的安裝通常會包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8e203-130">Installation of the application to be tested will typically include the following steps:</span></span>  
  
1.  <span data-ttu-id="8e203-131">使用 BizTalk Server 管理主控台執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8e203-131">Use the BizTalk Server Administration console to do the following:</span></span>  
  
    -   <span data-ttu-id="8e203-132">建立主控件</span><span class="sxs-lookup"><span data-stu-id="8e203-132">Create Hosts</span></span>  
  
    -   <span data-ttu-id="8e203-133">建立傳送/接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e203-133">Create Send/Receive Handlers.</span></span>  
  
    -   <span data-ttu-id="8e203-134">建立主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8e203-134">Create Host instances.</span></span>  
  
    -   <span data-ttu-id="8e203-135">建立 BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e203-135">Create BizTalk Server Applications.</span></span>  
  
2.  <span data-ttu-id="8e203-136">應用程式安裝：</span><span class="sxs-lookup"><span data-stu-id="8e203-136">Application installation:</span></span>  
  
    1.  <span data-ttu-id="8e203-137">將 BizTalk Server 二進位檔部署到 BizTalk Server 群組。</span><span class="sxs-lookup"><span data-stu-id="8e203-137">Deploy BizTalk Server binaries to the BizTalk Server group.</span></span>  
  
    2.  <span data-ttu-id="8e203-138">繫結匯入至 BizTalk Server 群組。</span><span class="sxs-lookup"><span data-stu-id="8e203-138">Import bindings to the BizTalk Server group.</span></span>  
  
    3.  <span data-ttu-id="8e203-139">GAC BizTalk Server 和非 BizTalk Server 二進位檔的所有方塊。</span><span class="sxs-lookup"><span data-stu-id="8e203-139">GAC BizTalk Server and non-BizTalk Server binaries on all boxes.</span></span>  
  
    4.  <span data-ttu-id="8e203-140">請確定所有的方塊上存在相依性元件。</span><span class="sxs-lookup"><span data-stu-id="8e203-140">Ensure dependency components exist on all boxes.</span></span>  
  
3.  <span data-ttu-id="8e203-141">安裝相依性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e203-141">Install dependency applications.</span></span>  
  
4.  <span data-ttu-id="8e203-142">在 BizTalk Server 管理主控台中設定傳輸與實體端點。</span><span class="sxs-lookup"><span data-stu-id="8e203-142">Configure transports and physical endpoints in the BizTalk Server Administration console.</span></span>  
  
5.  <span data-ttu-id="8e203-143">啟動服務。</span><span class="sxs-lookup"><span data-stu-id="8e203-143">Start services.</span></span>  
  
6.  <span data-ttu-id="8e203-144">執行基本煙霧測試; 煙霧測試端對端功能測試，測試您的解決方案的基本功能。</span><span class="sxs-lookup"><span data-stu-id="8e203-144">Perform basic smoke tests – Smoke tests are end-to-end functional tests that test the basic functionality of your solution.</span></span>  
  
## <a name="implement-automated-build-and-load-testing"></a><span data-ttu-id="8e203-145">實作自動化的建置和負載測試</span><span class="sxs-lookup"><span data-stu-id="8e203-145">Implement automated build and load testing</span></span>  
 <span data-ttu-id="8e203-146">自動化的建置和負載測試處理程序的實作可說是 BizTalk Server 效能評定的基石。</span><span class="sxs-lookup"><span data-stu-id="8e203-146">Implementation of an automated build and load testing process is arguably the cornerstone of a BizTalk Server performance assessment.</span></span> <span data-ttu-id="8e203-147">如果程式碼變更效能評估的範圍內，就應該實作自動化的建置程序。</span><span class="sxs-lookup"><span data-stu-id="8e203-147">An automated build process should be implemented if code changes are within the scope of the performance assessment.</span></span> <span data-ttu-id="8e203-148">自動化的負載測試應該實作所有的負載測試案例。</span><span class="sxs-lookup"><span data-stu-id="8e203-148">Automated load testing should be implemented for all load testing scenarios.</span></span> <span data-ttu-id="8e203-149">實作自動化的建置和負載測試所需的初始時間投資的原因是快速，automation 可容納的人為錯誤受限於一般建置/測試工作的快速、 精確地重複。</span><span class="sxs-lookup"><span data-stu-id="8e203-149">The initial time investment required to implement automated build and load testing is quickly recouped, automation accommodates rapid and precise repetition of mundane build/testing tasks that are subject to human error.</span></span> <span data-ttu-id="8e203-150">如需實作自動化的組建和測試程序的詳細資訊，請參閱[實作自動化的測試](../technical-guides/implementing-automated-testing.md)本指南中。</span><span class="sxs-lookup"><span data-stu-id="8e203-150">For more information about implementing an automated build and testing process, see [Implementing Automated Testing](../technical-guides/implementing-automated-testing.md) in this guide.</span></span>  
  
## <a name="configure-performance-monitoring"></a><span data-ttu-id="8e203-151">設定效能監視</span><span class="sxs-lookup"><span data-stu-id="8e203-151">Configure performance monitoring</span></span>  
 <span data-ttu-id="8e203-152">精確的效能監視成功很重要的效能評估。</span><span class="sxs-lookup"><span data-stu-id="8e203-152">Accurate performance monitoring is critical to the success of the performance assessment.</span></span> <span data-ttu-id="8e203-153">決定應評估的效能計量根據 「 範圍 」 階段中定義的輸送量和延遲目標。</span><span class="sxs-lookup"><span data-stu-id="8e203-153">Determine which performance metrics should be evaluated based on the throughput and latency goals that were defined in the Scope phase.</span></span> <span data-ttu-id="8e203-154">效能監視應在 BizTalk Server 環境中的每一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="8e203-154">Performance monitoring should be performed on each computer in the BizTalk Server environment.</span></span> <span data-ttu-id="8e203-155">請參閱[效能計數器](../core/performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="8e203-155">See [Performance Counters](../core/performance-counters.md).</span></span> <span data-ttu-id="8e203-156">您可以使用效能記錄檔的分析工具 (PAL) 來產生重要的效能計數器的圖表以圖形方式和當超過這些計數器的閾值時產生警示的 HTML 報表。</span><span class="sxs-lookup"><span data-stu-id="8e203-156">Use the Performance Analysis of Logs tool (PAL) to generate HTML reports that graphically chart important performance counters and generate alerts when thresholds for these counters are exceeded.</span></span> <span data-ttu-id="8e203-157">S[效能分析的記錄檔 (PAL) 工具](https://github.com/clinthuffman/PAL)。</span><span class="sxs-lookup"><span data-stu-id="8e203-157">S [Performance Analysis of Logs (PAL) tool](https://github.com/clinthuffman/PAL).</span></span>  
  
## <a name="establish-and-document-the-solutions-baseline-performance"></a><span data-ttu-id="8e203-158">建立與記錄方案的基準效能</span><span class="sxs-lookup"><span data-stu-id="8e203-158">Establish and document the solution’s baseline performance</span></span>  
 <span data-ttu-id="8e203-159">基準效能應該計算，以便您可以測量效能評估期間套用的效能最佳化的效果。</span><span class="sxs-lookup"><span data-stu-id="8e203-159">Baseline performance should be calculated so that the effect of performance optimizations applied during the performance assessment can be measured.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e203-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="8e203-160">See Also</span></span>  
 [<span data-ttu-id="8e203-161">效能評定的階段</span><span class="sxs-lookup"><span data-stu-id="8e203-161">Phases of a Performance Assessment</span></span>](../technical-guides/phases-of-a-performance-assessment.md)