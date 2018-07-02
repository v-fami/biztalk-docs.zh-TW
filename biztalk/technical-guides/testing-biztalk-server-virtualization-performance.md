---
title: 測試 BizTalk 伺服器虛擬化的效能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d09121b1-cdd6-4c01-9d69-0f1923464f0e
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f07c6bf8371e1db84ed574d7c737d4cc5b3903b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993695"
---
# <a name="testing-biztalk-server-virtualization-performance"></a><span data-ttu-id="39220-102">測試 BizTalk Server 虛擬化效能</span><span class="sxs-lookup"><span data-stu-id="39220-102">Testing BizTalk Server Virtualization Performance</span></span>
<span data-ttu-id="39220-103">本指南中所述的效能測試案例的每個已部署在 Microsoft 測試實驗室中，實體電腦上，然後在每個不同的系統架構上執行相同的負載測試。</span><span class="sxs-lookup"><span data-stu-id="39220-103">Each of the performance test scenarios described in this guide were deployed on physical computers in a Microsoft test lab, and then the same load test was performed on each distinct system architecture.</span></span> <span data-ttu-id="39220-104">每部實體電腦上主機作業系統已完整安裝[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]Enterprise、 64 位元版本，安裝 HYPER-V 伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="39220-104">The host operating system on each physical computer was a full installation of [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] Enterprise, 64-Bit Edition, with the Hyper-V server role installed.</span></span> <span data-ttu-id="39220-105">用於測試 BizTalk Server 的虛擬機器設定的[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]企業，做為客體作業系統的 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="39220-105">The virtual machines used for testing BizTalk Server were set up with [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] Enterprise, 64-Bit Edition as the guest operating system.</span></span> <span data-ttu-id="39220-106">用於測試 SQL Server 的虛擬機器所設定[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]企業，做為客體作業系統的 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="39220-106">The virtual machine used for testing SQL Server was set up with [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] Enterprise, 64-Bit Edition as the guest operating system.</span></span> <span data-ttu-id="39220-107">用來編寫一系列的最佳做法和指引的設計、 實作、 測試案例、 測試方法、 效能測試結果和後續的分析和最佳化虛擬化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="39220-107">The test scenarios, test methods, performance test results, and subsequent analysis were used to formulate a series of best practices and guidance for designing, implementing, and optimizing virtualized [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
- <span data-ttu-id="39220-108">**測試案例 1： 基準**– 第一個案例用意是要建立實體的硬體上執行 BizTalk Server 環境的基準效能。</span><span class="sxs-lookup"><span data-stu-id="39220-108">**Test Scenario 1: Baseline** – The first scenario was designed to establish baseline performance of a BizTalk Server environment running on physical hardware only.</span></span> <span data-ttu-id="39220-109">此案例中 BizTalk Server 和 SQL Server 所安裝，並只使用實體硬體上執行。</span><span class="sxs-lookup"><span data-stu-id="39220-109">For this scenario both BizTalk Server and SQL Server were installed and run on physical hardware only.</span></span>  
  
- <span data-ttu-id="39220-110">**測試案例 2： 虛擬 BizTalk/實體伺服器的 SQL Server** -第二個案例設計用來判斷多個相同的實體伺服器上的客體虛擬機器上裝載 BizTalk Server 的效能影響。</span><span class="sxs-lookup"><span data-stu-id="39220-110">**Test Scenario 2: Virtual BizTalk Server/Physical SQL Server** - The second scenario was designed to determine the performance impact of hosting BizTalk Server on multiple guest virtual machines on the same physical server.</span></span> <span data-ttu-id="39220-111">取自組態已總數相同的邏輯處理器數目然後比較處理實體機器的多個虛擬機器的測試結果散佈於所有的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="39220-111">Test results taken from multiple virtual machine configurations were then compared to a physical machine processing with the same number of logical processors as the total number dispersed across all virtual machines.</span></span>  
  
- <span data-ttu-id="39220-112">**測試案例 3： 虛擬 BizTalk/虛擬伺服器上的 SQL Server 不同的實體 HYPER-V 主機**-第三個案例進行以判斷虛擬化環境中執行 BizTalk Server 和 SQL Server 的效能影響。</span><span class="sxs-lookup"><span data-stu-id="39220-112">**Test Scenario 3: Virtual BizTalk Server/Virtual SQL Server on separate physical Hyper-V hosts** - The third scenario was conducted to determine the performance impact of running both BizTalk Server and SQL Server in a virtualized environment.</span></span> <span data-ttu-id="39220-113">使用 BizTalk Server 與 BizTalk 資料庫裝載在 HYPER-V 虛擬機器上執行的 SQL Server 執行個體上執行 HYPER-V 虛擬機器上執行測試。</span><span class="sxs-lookup"><span data-stu-id="39220-113">Tests were performed using BizTalk Server running on Hyper-V virtual machines with the BizTalk databases hosted on a SQL Server instance running on a Hyper-V virtual machine.</span></span> <span data-ttu-id="39220-114">此案例中，BizTalk Server 虛擬機器和 SQL Server 虛擬機器上裝載不同的實體 HYPER-V 主機。</span><span class="sxs-lookup"><span data-stu-id="39220-114">For this scenario, the BizTalk Server virtual machines and the SQL Server virtual machines were hosted on separate physical Hyper-V hosts.</span></span>  
  
- <span data-ttu-id="39220-115">**測試案例 4： 伺服器彙總-合併完整 BizTalk 群組包括 SQL 在 HYPER-V 上的一部實體伺服器到**– 在此案例中，一部實體伺服器上裝載的所有虛擬機器 (Vm) 執行測試應用程式所需。</span><span class="sxs-lookup"><span data-stu-id="39220-115">**Test Scenario 4: Server consolidation - Consolidating a full BizTalk Group Including SQL onto one Physical Server on Hyper-V** – In the scenario, all virtual machines (VMs) needed to run the test application are hosted on one physical server.</span></span> <span data-ttu-id="39220-116">此案例的目的是要判斷裝載 SQL Server 和 BizTalk Server 整合的環境中的虛擬機器的效能成本。</span><span class="sxs-lookup"><span data-stu-id="39220-116">The purpose of this scenario is to determine the performance costs of hosting SQL Server and BizTalk Server virtual machines in a consolidated environment.</span></span>  
  
  <span data-ttu-id="39220-117">本節提供測試應用程式和伺服器架構，用於每個案例的概觀，並也會提供在測試期間所觀察到的關鍵效能指標 (Kpi)。</span><span class="sxs-lookup"><span data-stu-id="39220-117">This section provides an overview of the test application and the server architecture used for each scenario and also presents key performance indicators (KPIs) observed during testing.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39220-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="39220-118">In This Section</span></span>  
  
-   [<span data-ttu-id="39220-119">測試案例概觀</span><span class="sxs-lookup"><span data-stu-id="39220-119">Test Scenario Overview</span></span>](../technical-guides/test-scenario-overview.md)  
  
-   [<span data-ttu-id="39220-120">測試案例伺服器架構</span><span class="sxs-lookup"><span data-stu-id="39220-120">Test Scenario Server Architecture</span></span>](../technical-guides/test-scenario-server-architecture.md)  
  
-   [<span data-ttu-id="39220-121">測試結果：BizTalk Server 關鍵效能指標</span><span class="sxs-lookup"><span data-stu-id="39220-121">Test Results: BizTalk Server Key Performance Indicators</span></span>](../technical-guides/test-results-biztalk-server-key-performance-indicators.md)  
  
-   [<span data-ttu-id="39220-122">測試結果：SQL Server 關鍵效能指標</span><span class="sxs-lookup"><span data-stu-id="39220-122">Test Results: SQL Server Key Performance Indicators</span></span>](../technical-guides/test-results-sql-server-key-performance-indicators.md)  
  
-   [<span data-ttu-id="39220-123">測試結果：網路功能關鍵效能指標</span><span class="sxs-lookup"><span data-stu-id="39220-123">Test Results: Networking Key Performance Indicators</span></span>](../technical-guides/test-results-networking-key-performance-indicators.md)  
  
-   [<span data-ttu-id="39220-124">測試結果：記憶體關鍵效能指標</span><span class="sxs-lookup"><span data-stu-id="39220-124">Test Results: Memory Key Performance Indicators</span></span>](../technical-guides/test-results-memory-key-performance-indicators.md)  
  
-   [<span data-ttu-id="39220-125">測試結果摘要</span><span class="sxs-lookup"><span data-stu-id="39220-125">Summary of Test Results</span></span>](../technical-guides/summary-of-test-results.md)