---
title: "測試案例伺服器架構 |Microsoft 文件"
ms.custom: 
ms.date: 2015-12-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e3afb57-c3ff-4314-9605-cf9fe936e63f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49a51244b7033c6cebc978a39ad37dd5732fa38d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="test-scenario-server-architecture"></a><span data-ttu-id="d400e-102">測試案例伺服器架構</span><span class="sxs-lookup"><span data-stu-id="d400e-102">Test Scenario Server Architecture</span></span>
<span data-ttu-id="d400e-103">本主題提供在負載測試期間的伺服器和執行負載測試的不同伺服器架構之間的訊息流程的概觀。</span><span class="sxs-lookup"><span data-stu-id="d400e-103">This topic provides an overview of the flow of messages between servers during load testing and the distinct server architectures against which the load test was performed.</span></span>  
  
## <a name="overview-of-message-flow-during-load-testing"></a><span data-ttu-id="d400e-104">在負載測試期間的訊息流程的概觀</span><span class="sxs-lookup"><span data-stu-id="d400e-104">Overview of Message Flow During Load Testing</span></span>  
 <span data-ttu-id="d400e-105">下圖提供用於所有的測試案例和負載測試期間的伺服器之間的訊息流程的伺服器架構的一般概觀。</span><span class="sxs-lookup"><span data-stu-id="d400e-105">The following diagram provides a generic overview of the server architecture used for all test scenarios and the flow of messages between servers during a load test.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d400e-106">節將說明每個已測試的不同伺服器架構**基準伺服器架構**。</span><span class="sxs-lookup"><span data-stu-id="d400e-106">Each distinct server architecture that was tested is described in the section **Baseline Server Architecture**.</span></span>  
  
 <span data-ttu-id="d400e-107">下圖提供的訊息流程的概觀。</span><span class="sxs-lookup"><span data-stu-id="d400e-107">The following figure provides an overview of the message flow.</span></span> <span data-ttu-id="d400e-108">此圖中的數字對應到如下圖所列的步驟。</span><span class="sxs-lookup"><span data-stu-id="d400e-108">The numbers in the figure correspond to the steps listed below the figure.</span></span>  
  
 <span data-ttu-id="d400e-109">![訊息流程概觀](../technical-guides/media/archmsgflow.gif "ArchMsgFlow")</span><span class="sxs-lookup"><span data-stu-id="d400e-109">![Message Flow Overview](../technical-guides/media/archmsgflow.gif "ArchMsgFlow")</span></span>  
<span data-ttu-id="d400e-110">訊息流程概觀</span><span class="sxs-lookup"><span data-stu-id="d400e-110">Message Flow Overview</span></span>  
  
1.  <span data-ttu-id="d400e-111">負載測試的負載代理程式控制器電腦起始**VSTS_TestController**:</span><span class="sxs-lookup"><span data-stu-id="d400e-111">Load testing is initiated by the Load Agent Controller computer **VSTS_TestController**:</span></span>  
  
    -   <span data-ttu-id="d400e-112">上的 Visual Studio 2008 專案**VSTS_TestController**執行。</span><span class="sxs-lookup"><span data-stu-id="d400e-112">A Visual Studio 2008 project on **VSTS_TestController** is executed.</span></span> <span data-ttu-id="d400e-113">專案載入 BizUnit 類別的執行個體，載入指定的 BizUnit XML 組態檔，並開始執行 BizUnit 組態檔中定義的步驟。</span><span class="sxs-lookup"><span data-stu-id="d400e-113">The project loads an instance of the BizUnit class, loads the specified BizUnit XML configuration file, and begins executing the steps defined in the BizUnit configuration file.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d400e-114">BizUnit 所使用的 XML 組態檔的詳細資訊，請參閱主題 < 定義測試使用的 XML 組態檔案 」，在[http://go.microsoft.com/fwlink/?LinkId=143432](http://go.microsoft.com/fwlink/?LinkId=143432)。</span><span class="sxs-lookup"><span data-stu-id="d400e-114">For more information about the XML configuration file used by BizUnit, see the topic “Defining Tests Using an XML Configuration File” at [http://go.microsoft.com/fwlink/?LinkId=143432](http://go.microsoft.com/fwlink/?LinkId=143432).</span></span>  
  
    -   <span data-ttu-id="d400e-115">完成測試的安裝步驟之後，其中一個步驟 BizUnit 專案中執行命令，以顯示對話方塊，提示您啟動 「 忙於活絡"的測試回合來提交忙於活絡訊息至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="d400e-115">After completing the Test Setup steps, one of the steps in the BizUnit project executes a command that displays a dialog box which prompts you to start a “priming” test run to submit priming messages to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
    -   <span data-ttu-id="d400e-116">從個別的 Visual Studio 2008 測試專案上提交忙於活絡訊息**VSTS_TestController**。</span><span class="sxs-lookup"><span data-stu-id="d400e-116">Priming messages are submitted from a separate Visual Studio 2008 Test project on **VSTS_TestController**.</span></span> <span data-ttu-id="d400e-117">忙於活絡訊息會傳送 「 準備 」 的測試環境初始化系統快取。</span><span class="sxs-lookup"><span data-stu-id="d400e-117">Priming messages are sent to “warm up” the test environment by initializing system caches.</span></span>  
  
    -   <span data-ttu-id="d400e-118">處理所有忙於活絡訊息; 之後BizUnit 執行個體載入效能監視器計數器的所有主要的測試回合中測試的電腦，並執行命令，以顯示對話方塊，提示您將訊息提交以主要測試回合。</span><span class="sxs-lookup"><span data-stu-id="d400e-118">After all priming messages have been processed; the BizUnit instance loads Performance Monitor counters for all computers being tested in the main test run and executes a command to display a dialog box which prompts you to submit messages for the main test run.</span></span>  
  
    -   <span data-ttu-id="d400e-119">在 Visual Studio 2008 負載測試專案**VSTS_TestController**指示要將訊息提交以主要測試回合的負載測試代理程式電腦。</span><span class="sxs-lookup"><span data-stu-id="d400e-119">The Visual Studio 2008 Load Test project on **VSTS_TestController** directs the Load Test Agent computers to submit messages for the main test run.</span></span>  
  
2.  <span data-ttu-id="d400e-120">負載測試代理程式電腦送出測試訊息至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]負載測試控制器電腦上 Visual Studio 2008 的負載測試專案的 app.config 檔案中指定的電腦 (**VSTS_TestController**)。</span><span class="sxs-lookup"><span data-stu-id="d400e-120">The Load Test Agent computers submit test messages to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers specified in the app.config file of the Visual Studio 2008 Load Test project on the Load Test Controller computer (**VSTS_TestController**).</span></span>  
  
3.  <span data-ttu-id="d400e-121">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦接收的負載測試代理程式電腦所提交的訊息，為這個負載測試，雙向接收的訊息是要求-回應接收位置。</span><span class="sxs-lookup"><span data-stu-id="d400e-121">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers receive the messages submitted by the Load Test Agent computers, for this load test the messages were received by a two way request-response receive location.</span></span>  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d400e-122">將訊息發佈到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d400e-122"> publishes the message to the MessageBox database.</span></span>  
  
    -   <span data-ttu-id="d400e-123">協調流程所使用的訊息。</span><span class="sxs-lookup"><span data-stu-id="d400e-123">The messages are consumed by an orchestration.</span></span>  
  
    -   <span data-ttu-id="d400e-124">協調流程繫結至雙向請求-回應傳送埠叫用下游計算機服務。</span><span class="sxs-lookup"><span data-stu-id="d400e-124">The orchestration is bound to a two way solicit-response send port which invokes the downstream calculator service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d400e-125">下游計算機服務根據所述的 Windows Communication Foundation 範例[http://go.microsoft.com/fwlink/?LinkId=141762](http://go.microsoft.com/fwlink/?LinkId=141762)。</span><span class="sxs-lookup"><span data-stu-id="d400e-125">The downstream calculator service is based upon Windows Communication Foundation samples described at [http://go.microsoft.com/fwlink/?LinkId=141762](http://go.microsoft.com/fwlink/?LinkId=141762).</span></span> <span data-ttu-id="d400e-126">Windows Communication Foundation 範例可供下載[http://go.microsoft.com/fwlink/?LinkId=87352](http://go.microsoft.com/fwlink/?LinkId=87352)。</span><span class="sxs-lookup"><span data-stu-id="d400e-126">The Windows Communication Foundation samples are available for download at [http://go.microsoft.com/fwlink/?LinkId=87352](http://go.microsoft.com/fwlink/?LinkId=87352).</span></span>  
  
4.  <span data-ttu-id="d400e-127">計算機服務會使用來自要求[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並將回應傳回[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]請求-回應傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d400e-127">The calculator service consumes the request from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and returns a response to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solicit-response send port.</span></span>  
  
5.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d400e-128">處理回應，並保存到 MessageBox 資料庫的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="d400e-128"> processes the response and persists the response message to the MessageBox database.</span></span> <span data-ttu-id="d400e-129">從 MessageBox 資料庫由 BizTalk 要求-回應連接埠，然後擷取來自計算機 web 服務的回應訊息和回應訊息傳遞到負載測試代理程式電腦。</span><span class="sxs-lookup"><span data-stu-id="d400e-129">Then the response message from the Calculator web service is retrieved from the MessageBox database by the BizTalk request-response port, and a response message is delivered back to the Load Test Agent computers.</span></span>  
  
## <a name="baseline-server-architecture"></a><span data-ttu-id="d400e-130">基準伺服器架構</span><span class="sxs-lookup"><span data-stu-id="d400e-130">Baseline Server Architecture</span></span>  
 <span data-ttu-id="d400e-131">對於基準的伺服器架構中，未安裝 HYPER-V 角色，兩者均[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server 已安裝到主機作業系統。</span><span class="sxs-lookup"><span data-stu-id="d400e-131">For the Baseline Server architecture, the Hyper-V role was not installed and Both [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server were installed on to the host operating system.</span></span> <span data-ttu-id="d400e-132">這是要建立 「 數基準 」 效能度量的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在實體硬體環境中的方案。</span><span class="sxs-lookup"><span data-stu-id="d400e-132">This was done to establish “baseline” performance metrics of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution on a physical hardware environment.</span></span>  
  
 <span data-ttu-id="d400e-133">下圖說明實體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和基準伺服器架構的 SQL Server 層。</span><span class="sxs-lookup"><span data-stu-id="d400e-133">The following figure depicts the physical [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server tiers for the Baseline Server Architecture.</span></span>  
  
 <span data-ttu-id="d400e-134">![實體 BizTalk &#47;實體 SQL](../technical-guides/media/archphysicalbts-physicalsql.gif "ArchPhysicalBTS_PhysicalSQL")</span><span class="sxs-lookup"><span data-stu-id="d400e-134">![Physical BizTalk &#47; Physical SQL](../technical-guides/media/archphysicalbts-physicalsql.gif "ArchPhysicalBTS_PhysicalSQL")</span></span>  
<span data-ttu-id="d400e-135">實體 BizTalk 伺服器 / 實體 SQL Server （基準）</span><span class="sxs-lookup"><span data-stu-id="d400e-135">Physical BizTalk Server / Physical SQL Server (Baseline)</span></span>  
  
-   <span data-ttu-id="d400e-136">**BizTalk Server** -2 BizTalk Server 電腦設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d400e-136">**BizTalk Server** - 2 BizTalk Server computers configured as follows:</span></span>  
  
    -   <span data-ttu-id="d400e-137">一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦**6** GB RAM 和**8**可用的處理器核心。</span><span class="sxs-lookup"><span data-stu-id="d400e-137">One [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer with **6** GB RAM and **8** processor cores available.</span></span>  
  
    -   <span data-ttu-id="d400e-138">一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦**3** GB RAM 和**4**可用的處理器核心。</span><span class="sxs-lookup"><span data-stu-id="d400e-138">One [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer with **3** GB RAM and **4** processor cores available.</span></span>  
  
    -   <span data-ttu-id="d400e-139">總計的 6 + 3 = **9**可用 GB RAM 和 8 + 4 = **12**可用的處理器核心[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d400e-139">Total of 6 + 3 = **9** GB RAM available and 8 + 4 = **12** processor cores available for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d400e-140">**SQL Server** -1 的 SQL Server 電腦設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d400e-140">**SQL Server** - 1 SQL Server computer configured as follows:</span></span>  
  
    -   <span data-ttu-id="d400e-141">**8**可用 GB RAM。</span><span class="sxs-lookup"><span data-stu-id="d400e-141">**8** GB RAM available.</span></span>  
  
    -   <span data-ttu-id="d400e-142">**4**可用的處理器核心。</span><span class="sxs-lookup"><span data-stu-id="d400e-142">**4** processor cores available.</span></span>  
  
## <a name="virtual-biztalk-server--physical-sql-server"></a><span data-ttu-id="d400e-143">虛擬 BizTalk Server / 實體 SQL Server</span><span class="sxs-lookup"><span data-stu-id="d400e-143">Virtual BizTalk Server / Physical SQL Server</span></span>  
 <span data-ttu-id="d400e-144">下圖說明虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和實體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]層。</span><span class="sxs-lookup"><span data-stu-id="d400e-144">The following figure depicts the virtual [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and physical [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] tiers.</span></span>  
  
 <span data-ttu-id="d400e-145">![虛擬 BizTalk &#47;實體 SQL](../technical-guides/media/archvirtualbts-physicalsql.gif "ArchVirtualBTS_PhysicalSQL")</span><span class="sxs-lookup"><span data-stu-id="d400e-145">![Virtual BizTalk &#47; Physical SQL](../technical-guides/media/archvirtualbts-physicalsql.gif "ArchVirtualBTS_PhysicalSQL")</span></span>  
<span data-ttu-id="d400e-146">虛擬 BizTalk Server / 實體 SQL Server</span><span class="sxs-lookup"><span data-stu-id="d400e-146">Virtual BizTalk Server / Physical SQL Server</span></span>  
  
 <span data-ttu-id="d400e-147">針對此案例中，執行負載測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器和實體硬體上執行的 SQL Server 上執行。</span><span class="sxs-lookup"><span data-stu-id="d400e-147">For this scenario, the load test was performed against [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] running on Hyper-V virtual machines and SQL Server running on physical hardware.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d400e-148">如下所述的 RAM 和處理器核心的配置是唯一的差異在於特定電腦在 HYPER-V 虛擬機器上，或實體硬體上執行的每個非基準的案例中，相同。</span><span class="sxs-lookup"><span data-stu-id="d400e-148">The allocation of RAM and processor cores described below was identical for each non-baseline scenarios, the only difference being whether certain computers are running on a Hyper-V virtual machine or on physical hardware.</span></span>  
  
-   <span data-ttu-id="d400e-149">**BizTalk Server** -3[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]的電腦設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d400e-149">**BizTalk Server** - 3 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s computers configured as follows:</span></span>  
  
    -   <span data-ttu-id="d400e-150">3 GB 的 RAM 配置給每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦總數 3 x 3 = **9** GB RAM 可供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d400e-150">3 GB RAM allocated to each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer with a total of 3 x 3 = **9** GB RAM available for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="d400e-151">4 顆處理器核心配置給每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦 3 x 4 總數 = **12**可用的處理器核心[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d400e-151">4 processor cores allocated to each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer with a total of 3 x 4 = **12** processor cores available for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d400e-152">**SQL Server** -1 的 SQL Server 電腦設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d400e-152">**SQL Server** - 1 SQL Server computer configured as follows:</span></span>  
  
    -   <span data-ttu-id="d400e-153">**8**可用 GB RAM。</span><span class="sxs-lookup"><span data-stu-id="d400e-153">**8** GB RAM available.</span></span>  
  
    -   <span data-ttu-id="d400e-154">**4**可用的處理器核心。</span><span class="sxs-lookup"><span data-stu-id="d400e-154">**4** processor cores available.</span></span>  
  
## <a name="virtual-biztalk-server--virtual-sql-server"></a><span data-ttu-id="d400e-155">虛擬 BizTalk Server / 虛擬 SQL Server</span><span class="sxs-lookup"><span data-stu-id="d400e-155">Virtual BizTalk Server / Virtual SQL Server</span></span>  
 <span data-ttu-id="d400e-156">下圖說明虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和虛擬 SQL Server 電腦上不同的 HYPER-V 主機電腦。</span><span class="sxs-lookup"><span data-stu-id="d400e-156">The following figure depicts a virtual [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer and a virtual SQL Server computer on separate Hyper-V host computers.</span></span>  
  
 <span data-ttu-id="d400e-157">![虛擬 BizTalk &#47;虛擬 SQL](../technical-guides/media/archvirtualbts-virtualsql.gif "ArchVirtualBTS_VirtualSQL")</span><span class="sxs-lookup"><span data-stu-id="d400e-157">![Virtual BizTalk &#47; Virtual SQL](../technical-guides/media/archvirtualbts-virtualsql.gif "ArchVirtualBTS_VirtualSQL")</span></span>  
<span data-ttu-id="d400e-158">虛擬 BizTalk Server / 虛擬 SQL Server</span><span class="sxs-lookup"><span data-stu-id="d400e-158">Virtual BizTalk Server / Virtual SQL Server</span></span>  
  
 <span data-ttu-id="d400e-159">針對此案例中，執行負載測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器上執行和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器上執行。</span><span class="sxs-lookup"><span data-stu-id="d400e-159">For this scenario, the load test was performed against [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] running on Hyper-V virtual machines and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] running on a Hyper-V virtual machine.</span></span> <span data-ttu-id="d400e-160">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HYPER-V 虛擬機器和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器在不同的 HYPER-V 主機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="d400e-160">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Hyper-V virtual machines and the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Hyper-V virtual machine were run on separate Hyper-V host computers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d400e-161">在此案例的 RAM 和處理器核心的配置是等同的 RAM 和處理器核心的配置**虛擬的 BizTalk Server / 實體 SQL Server**情節、 唯一的差異在於，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]已設定為在 HYPER-V 虛擬機器，而不是實體硬體上執行。</span><span class="sxs-lookup"><span data-stu-id="d400e-161">The allocation of RAM and processor cores for this scenario is identical to the allocation of RAM and processor cores for the **Virtual BizTalk Server / Physical SQL Server** scenario, the only difference being that [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] was configured to run on a Hyper-V virtual machine rather than physical hardware.</span></span>  
  
## <a name="consolidated-environment"></a><span data-ttu-id="d400e-162">合併的環境</span><span class="sxs-lookup"><span data-stu-id="d400e-162">Consolidated Environment</span></span>  
 <span data-ttu-id="d400e-163">下圖說明虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和虛擬的 SQL Server 電腦整合在一部 HYPER-V 主機電腦上。</span><span class="sxs-lookup"><span data-stu-id="d400e-163">The following figure depicts virtual [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers and a virtual SQL Server computer consolidated on one Hyper-V host computer.</span></span>  
  
 <span data-ttu-id="d400e-164">![虛擬 BizTalk &#47;虛擬 SQL &#47;合併](../technical-guides/media/archvirtualbts-virtualsql-consolidated.gif "ArchVirtualBTS_VirtualSQL_Consolidated")</span><span class="sxs-lookup"><span data-stu-id="d400e-164">![Virtual BizTalk &#47; Virtual SQL &#47; Consolidated](../technical-guides/media/archvirtualbts-virtualsql-consolidated.gif "ArchVirtualBTS_VirtualSQL_Consolidated")</span></span>  
<span data-ttu-id="d400e-165">合併的環境</span><span class="sxs-lookup"><span data-stu-id="d400e-165">Consolidated Environment</span></span>  
  
 <span data-ttu-id="d400e-166">針對此案例中，執行負載測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器上執行和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器上執行。</span><span class="sxs-lookup"><span data-stu-id="d400e-166">For this scenario, the load test was performed against [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] running on Hyper-V virtual machines and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] running on a Hyper-V virtual machine.</span></span> <span data-ttu-id="d400e-167">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HYPER-V 虛擬機器和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器所執行相同的 HYPER-V 主機電腦上。</span><span class="sxs-lookup"><span data-stu-id="d400e-167">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Hyper-V virtual machines and the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Hyper-V virtual machine were all run on the same Hyper-V host computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d400e-168">在此案例的 RAM 和處理器核心的配置是等同的 RAM 和處理器核心的配置**虛擬的 BizTalk Server / 虛擬 SQL Server**情節、 唯一的差異在於，這兩個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器已設定為相同的 HYPER-V 主機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="d400e-168">The allocation of RAM and processor cores for this scenario is identical to the allocation of RAM and processor cores for the **Virtual BizTalk Server / Virtual SQL Server** scenario, the only difference being that both the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Hyper-V virtual machines and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Hyper-V virtual machines were configured to run on the same Hyper-V host computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d400e-169">請參閱</span><span class="sxs-lookup"><span data-stu-id="d400e-169">See Also</span></span>  
 [<span data-ttu-id="d400e-170">測試案例概觀</span><span class="sxs-lookup"><span data-stu-id="d400e-170">Test Scenario Overview</span></span>](../technical-guides/test-scenario-overview.md)