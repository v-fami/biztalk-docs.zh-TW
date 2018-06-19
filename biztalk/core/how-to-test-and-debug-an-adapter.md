---
title: 如何測試和偵錯配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6563ea-b4ea-4617-b3da-d31250d002ab
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 508f0b5a5ee7b29ed6e2fbde9a94b352d645e550
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256862"
---
# <a name="how-to-test-and-debug-an-adapter"></a><span data-ttu-id="82980-102">如何測試和偵錯配接器</span><span class="sxs-lookup"><span data-stu-id="82980-102">How to Test and Debug an Adapter</span></span>
<span data-ttu-id="82980-103">偵錯執行階段的問題時通常需要使用多重 Facet 的方法。</span><span class="sxs-lookup"><span data-stu-id="82980-103">Debugging run-time problems often requires a multifaceted approach.</span></span> <span data-ttu-id="82980-104">您必須從多個來源 (例如軟體追蹤、效能計數器、事件日誌項目、Windows Management Instrumentation (WMI) 事件和偵錯原始程式碼) 收集資料，才能確定問題或軟體 Bug 的原因。</span><span class="sxs-lookup"><span data-stu-id="82980-104">Data must be gathered from multiple sources such as software tracing, performance counters, event log entries, Windows Management Instrumentation (WMI) events, and debugging source code to determine the cause of problems or software bugs.</span></span>  
  
 <span data-ttu-id="82980-105">由於接收埠和傳送配接器都是在 BizTalk 服務的位址空間中執行，因此必須將偵錯工具連接到 BtsNtSvc.exe 處理序，才能對配接器進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="82980-105">Because receive and send adapters run in the address space of the BizTalk service the debugger needs to be attached to the BtsNtSvc.exe process to debug an adapter.</span></span> <span data-ttu-id="82980-106">不過外掛式接收配接器，都必須連接至裝載配接器的處理序偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="82980-106">However for isolated receive adapters, the debugger needs to be attached to the process that hosts the adapter.</span></span>  
  
 <span data-ttu-id="82980-107">您應該使用追蹤程式碼來檢測配接器執行階段程式碼，以擷取執行階段的疑難排解診斷。</span><span class="sxs-lookup"><span data-stu-id="82980-107">The adapter run-time code should be instrumented with tracing code to capture run-time diagnostics for troubleshooting.</span></span> <span data-ttu-id="82980-108">您可以使用 Microsoft Enterprise Instrumentation Framework (EIF) 完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="82980-108">You can do this by using the Microsoft Enterprise Instrumentation Framework (EIF).</span></span> <span data-ttu-id="82980-109">通常，加入不同嚴重性層級的追蹤陳述式會很有幫助；例如，只追蹤錯誤情況、追蹤錯誤和警告，以及最後再追蹤錯誤、警告和參考陳述式。</span><span class="sxs-lookup"><span data-stu-id="82980-109">Typically it is useful to add trace statements for different levels of severity, for example, tracing for error conditions only, tracing for errors and warnings, and finally tracing for errors, warnings, and informational statements.</span></span> <span data-ttu-id="82980-110">此外，較複雜的配接器可能有個別的子系統需要彼此分開追蹤。</span><span class="sxs-lookup"><span data-stu-id="82980-110">Further, more complex adapters may have separate subsystems that need to be traced in isolation from each other.</span></span> <span data-ttu-id="82980-111">例如，配接器可能有一個網路子系統和一個核心子系統；在某些情況下，啟用所有子系統的追蹤功能可能會產生過多的「干擾」。</span><span class="sxs-lookup"><span data-stu-id="82980-111">For example, an adapter may have a network subsubsystem and a core subsystem; enabling tracing for all subsystems may generate an excessive amount of "noise" in some scenarios.</span></span>  
  
 <span data-ttu-id="82980-112">在執行階段時，應該加入效能計數器來擷取速率和值，以提供更多有關配接器執行階段行為的資訊。</span><span class="sxs-lookup"><span data-stu-id="82980-112">Performance counters should be added to capture rates and values at run time to give more information about the run-time behavior of the adapter.</span></span> <span data-ttu-id="82980-113">例如，配接器可能會發佈效能計數器，以收集每個端點傳送的訊息原始數目，以及每秒傳送的訊息速率。</span><span class="sxs-lookup"><span data-stu-id="82980-113">For example, an adapter might publish performance counters for the raw numbers of messages sent on a per-endpoint basis as well as the rate of messages sent per second.</span></span>  
  
 <span data-ttu-id="82980-114">WMI 事件也可用於某些嚴重的錯誤情況。</span><span class="sxs-lookup"><span data-stu-id="82980-114">WMI events may also be useful for some critical error scenarios.</span></span>  <span data-ttu-id="82980-115">例如，如果配接器發生嚴重錯誤，使它關閉接收位置，則引發 WMI 事件將可讓系統管理員接聽該事件，並採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="82980-115">For instance if an adapter hits a critical error that causes it to shut down a receive location, firing a WMI event allows an administrator to listen on that event and take appropriate action.</span></span>  
  
## <a name="adapter-testing"></a><span data-ttu-id="82980-116">配接器測試</span><span class="sxs-lookup"><span data-stu-id="82980-116">Adapter Testing</span></span>  
 <span data-ttu-id="82980-117">當您為 BizTalk Server 開發自訂配接器時，請記住，您應該依照企業軟體品質的標準來開發它。</span><span class="sxs-lookup"><span data-stu-id="82980-117">When you develop a custom adapter for BizTalk Server, remember that it should be developed to enterprise software quality.</span></span> <span data-ttu-id="82980-118">這表示您必須在發送配接器之前，進行徹底的測試。</span><span class="sxs-lookup"><span data-stu-id="82980-118">This means that you need to test the adapter thoroughly before shipping it.</span></span> <span data-ttu-id="82980-119">本節並未完整詳述配接器的測試方式，但提供了應該執行的測試內容。</span><span class="sxs-lookup"><span data-stu-id="82980-119">While it does not completely detail how adapters should be tested, this section gives an idea of what needs to be done.</span></span> <span data-ttu-id="82980-120">一般測試執行階段程式碼，例如配接器應該的涵蓋下列三大類別： 功能測試、 壓力測試和效能測試。</span><span class="sxs-lookup"><span data-stu-id="82980-120">In general the testing of run-time code such as adapters should cover three broad categories: functional testing, stress testing, and performance testing.</span></span>  
  
### <a name="function-testing"></a><span data-ttu-id="82980-121">功能測試</span><span class="sxs-lookup"><span data-stu-id="82980-121">Function Testing</span></span>  
 <span data-ttu-id="82980-122">配接器應該經過所有功能排列的測試，包括正向測試與負向測試。</span><span class="sxs-lookup"><span data-stu-id="82980-122">The adapter should be tested for all permutations of its functionality, including both positive tests and negative tests.</span></span> <span data-ttu-id="82980-123">正向測試應該包括 (但不限於) 下列實例：</span><span class="sxs-lookup"><span data-stu-id="82980-123">Positive tests should include but not be limited to the following scenarios:</span></span>  
  
-   <span data-ttu-id="82980-124">接收訊息</span><span class="sxs-lookup"><span data-stu-id="82980-124">Receive a message(s)</span></span>  
  
-   <span data-ttu-id="82980-125">傳輸訊息</span><span class="sxs-lookup"><span data-stu-id="82980-125">Transmit a message(s)</span></span>  
  
-   <span data-ttu-id="82980-126">使用動態連接埠傳輸訊息</span><span class="sxs-lookup"><span data-stu-id="82980-126">Transmit a message using a dynamic port</span></span>  
  
-   <span data-ttu-id="82980-127">停用接收位置</span><span class="sxs-lookup"><span data-stu-id="82980-127">Disable receive locations</span></span>  
  
-   <span data-ttu-id="82980-128">更新組態</span><span class="sxs-lookup"><span data-stu-id="82980-128">Update configuration</span></span>  
  
-   <span data-ttu-id="82980-129">確認接收配接器和傳送配接器都能使用服務視窗</span><span class="sxs-lookup"><span data-stu-id="82980-129">Ensure service windows are working for both receive and send adapters</span></span>  
  
-   <span data-ttu-id="82980-130">確認交易配接器的交易完整性</span><span class="sxs-lookup"><span data-stu-id="82980-130">Ensure transactional integrity for transacted adapters</span></span>  
  
 <span data-ttu-id="82980-131">負向測試應該包括 (但不限於) 下列實例：</span><span class="sxs-lookup"><span data-stu-id="82980-131">Negative tests should include but not be limited to:</span></span>  
  
-   <span data-ttu-id="82980-132">接收錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="82980-132">Receive a bad message(s)</span></span>  
  
-   <span data-ttu-id="82980-133">接收部分正確、部分錯誤的混合訊息批次</span><span class="sxs-lookup"><span data-stu-id="82980-133">Receive a mixed batch of messages, some good and some bad</span></span>  
  
-   <span data-ttu-id="82980-134">傳輸失敗</span><span class="sxs-lookup"><span data-stu-id="82980-134">Transmit failure</span></span>  
  
-   <span data-ttu-id="82980-135">重試成功</span><span class="sxs-lookup"><span data-stu-id="82980-135">Retry successful</span></span>  
  
-   <span data-ttu-id="82980-136">重試失敗，成功移到下一個傳輸</span><span class="sxs-lookup"><span data-stu-id="82980-136">Retry fails, move to next transport successful</span></span>  
  
-   <span data-ttu-id="82980-137">移到下一個傳輸失敗，擱置訊息</span><span class="sxs-lookup"><span data-stu-id="82980-137">Move to next transport fails, suspend message</span></span>  
  
-   <span data-ttu-id="82980-138">傳輸混合的訊息批次</span><span class="sxs-lookup"><span data-stu-id="82980-138">Transmit a mixed batch of messages</span></span>  
  
-   <span data-ttu-id="82980-139">資料庫容錯移轉</span><span class="sxs-lookup"><span data-stu-id="82980-139">Database failover</span></span>  
  
### <a name="stress-testing"></a><span data-ttu-id="82980-140">壓力測試</span><span class="sxs-lookup"><span data-stu-id="82980-140">Stress Testing</span></span>  
 <span data-ttu-id="82980-141">配接器是執行階段元件，因此應該符合執行階段軟體的嚴格需求。</span><span class="sxs-lookup"><span data-stu-id="82980-141">Adapters are run-time components and as such should meet the stringent requirements for run-time software.</span></span> <span data-ttu-id="82980-142">壓力測試通常是透過執行已在負載下一段時間的實例來進行。</span><span class="sxs-lookup"><span data-stu-id="82980-142">Typically stress testing is carried out by running scenarios under load for a period of time.</span></span> <span data-ttu-id="82980-143">您應該在兩次失敗測試之間，進一步執行高壓力及低壓力標準時間，使配接器在負載下執行一段經過測量的時間。</span><span class="sxs-lookup"><span data-stu-id="82980-143">Further high-stress and low-stress mean time between failure tests should be performed, whereby the adapter is run under load for a measured time period.</span></span>  
  
 <span data-ttu-id="82980-144">這些測試的某些概略方針可能會在高壓力下執行配接器 72 個小時左右的時間，而讓通過配接器的訊息數目產生約 80% 到 90% 的 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="82980-144">Some rough guidelines for these tests might be running the adapter at high stress for around 72 hours, where the number of messages through the adapter causes the CPU utilization to be around of 80 to 90 percent.</span></span> <span data-ttu-id="82980-145">在低壓力的情況下，如果執行時間為 120 個小時左右，則 CPU 使用率約為 30% 到 40% 左右。</span><span class="sxs-lookup"><span data-stu-id="82980-145">For low stress, the CPU utilization would be around 30 to 40 percent for around 120 hours.</span></span>  
  
### <a name="performance-testing"></a><span data-ttu-id="82980-146">效能測試</span><span class="sxs-lookup"><span data-stu-id="82980-146">Performance Testing</span></span>  
 <span data-ttu-id="82980-147">開發配接器時應留意效能的問題。</span><span class="sxs-lookup"><span data-stu-id="82980-147">Adapters should be developed with performance in mind.</span></span> <span data-ttu-id="82980-148">發行配接器之前，您應該先驗證其效能。</span><span class="sxs-lookup"><span data-stu-id="82980-148">Before releasing an adapter you should validate its performance.</span></span> <span data-ttu-id="82980-149">請務必確認配接器的效能能夠向上及向外擴充，也就是說，新增更多 CPU 與新增更多電腦一樣，都能提升效能。</span><span class="sxs-lookup"><span data-stu-id="82980-149">It is important to ensure that its performance scales up and scales out; that is, adding more CPUs leads to a performance increase as does adding more computers.</span></span> <span data-ttu-id="82980-150">對程式碼進行分析可協助解決效能瓶頸問題。</span><span class="sxs-lookup"><span data-stu-id="82980-150">Profiling the code can help to eliminate performance bottlenecks.</span></span>