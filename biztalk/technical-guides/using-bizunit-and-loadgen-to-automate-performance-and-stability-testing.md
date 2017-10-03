---
title: "若要自動化效能與穩定性測試使用 BizUnit 和 LoadGen |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c2a97a-6256-4010-8374-433017cb15d4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 538e47f481f0817acfbd26477866a3d45a0d285b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-bizunit-and-loadgen-to-automate-performance-and-stability-testing"></a><span data-ttu-id="13634-102">使用 BizUnit 和 LoadGen 來自動化效能與穩定性測試</span><span class="sxs-lookup"><span data-stu-id="13634-102">Using BizUnit and LoadGen to Automate Performance and Stability Testing</span></span>
<span data-ttu-id="13634-103">本主題提供如何使用 Microsoft BizTalk LoadGen 2007 工具 BizUnit 自動化效能與穩定性測試 BizTalk Server 解決方案的資訊。</span><span class="sxs-lookup"><span data-stu-id="13634-103">This topic provides information about how to use the Microsoft BizTalk LoadGen 2007 tool with BizUnit to automate performance and stability testing of a BizTalk Server solution.</span></span>  
  
## <a name="biztalk-server-performance-testing-step-by-step"></a><span data-ttu-id="13634-104">BizTalk Server 效能測試，逐步</span><span class="sxs-lookup"><span data-stu-id="13634-104">BizTalk Server performance testing, step-by-step</span></span>  
 <span data-ttu-id="13634-105">如果之前正在研究如何自動化 BizTalk Server 效能測試，會很有用知道哪些步驟通常在效能測試中執行。</span><span class="sxs-lookup"><span data-stu-id="13634-105">Before investigating how to automate BizTalk Server performance testing, it is useful to know what steps are typically performed in a performance test.</span></span> <span data-ttu-id="13634-106">下列步驟表示有 「 一般 」 的 BizTalk Server 效能測試程序：</span><span class="sxs-lookup"><span data-stu-id="13634-106">The following steps are representative of a “typical” BizTalk Server performance testing process:</span></span>  
  
1.  <span data-ttu-id="13634-107">建立測試結果目錄來儲存結果和資料收集，例如事件記錄檔、 追蹤記錄的效能監視器資料。</span><span class="sxs-lookup"><span data-stu-id="13634-107">Create a test results directory to store results and data collected, for example, event logs, trace logs, Performance Monitor data.</span></span>  
  
2.  <span data-ttu-id="13634-108">清除測試環境內的所有伺服器上的事件日誌。</span><span class="sxs-lookup"><span data-stu-id="13634-108">Clear the event logs on all servers within the test environment.</span></span>  
  
3.  <span data-ttu-id="13634-109">停止所有 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="13634-109">Stop all BizTalk host instances.</span></span>  
  
4.  <span data-ttu-id="13634-110">停止任何正在執行外掛式的 BizTalk 主控件，例如 SOAP 和 HTTP 接收配接器處理常式的 IIS 執行個體。</span><span class="sxs-lookup"><span data-stu-id="13634-110">Stop any IIS instances that are running isolated BizTalk hosts such as the SOAP and HTTP receive adapter handlers.</span></span>  
  
5.  <span data-ttu-id="13634-111">重新啟動所有執行 BizTalk Server 之電腦所使用的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="13634-111">Restart all instances of SQL Server used by the computers running BizTalk Server.</span></span>  
  
6.  <span data-ttu-id="13634-112">清除 MessageBox 資料庫，以確保沒有任何剩餘的資料，從先前的測試回合。</span><span class="sxs-lookup"><span data-stu-id="13634-112">Clean up the MessageBox database to ensure that there is no leftover data from previous tests runs.</span></span> <span data-ttu-id="13634-113">這是很重要，因為任何剩餘的資料會扭曲測試結果。</span><span class="sxs-lookup"><span data-stu-id="13634-113">This is important because any leftover data could skew test results.</span></span>  
  
7.  <span data-ttu-id="13634-114">啟動 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="13634-114">Start the BizTalk host instances.</span></span>  
  
8.  <span data-ttu-id="13634-115">在測試環境中的所有伺服器上啟動相關的效能監視器計數器。</span><span class="sxs-lookup"><span data-stu-id="13634-115">Start the relevant Performance Monitor counters on all servers in the test environment.</span></span>  
  
9. <span data-ttu-id="13634-116">傳送 「 忙於活絡"透過系統中的訊息來初始化系統快取。</span><span class="sxs-lookup"><span data-stu-id="13634-116">Send “priming” messages through the system to initialize the system caches.</span></span>  
  
10. <span data-ttu-id="13634-117">忙於活絡訊息處理完成之後，追蹤 SQL Server 測試結果資料庫中的測試開始時間。</span><span class="sxs-lookup"><span data-stu-id="13634-117">After the priming messages have been processed, track the test start time in a SQL Server test results database.</span></span>  
  
11. <span data-ttu-id="13634-118">啟動所有 LoadGen 測試代理程式的都啟動效能測試。</span><span class="sxs-lookup"><span data-stu-id="13634-118">Start the performance test by starting all of the LoadGen test agents.</span></span>  
  
12. <span data-ttu-id="13634-119">等候完成測試 – 通常即可做到這有系統地藉由測量例如主控件佇列長度效能監視器計數器的值。</span><span class="sxs-lookup"><span data-stu-id="13634-119">Wait for the test to complete – often this can be done systematically by measuring the value of a Performance Monitor counter such as host queue length.</span></span>  
  
13. <span data-ttu-id="13634-120">追蹤測試結束時間的 SQL 測試結果資料庫。</span><span class="sxs-lookup"><span data-stu-id="13634-120">Track test end time in a SQL test results database.</span></span>  
  
14. <span data-ttu-id="13634-121">在測試環境中的所有伺服器上停止相關的效能監視器計數器。</span><span class="sxs-lookup"><span data-stu-id="13634-121">Stop the relevant Performance Monitor counters on all servers in the test environment.</span></span>  
  
15. <span data-ttu-id="13634-122">將測試資料儲存至稍早建立的測試結果目錄。</span><span class="sxs-lookup"><span data-stu-id="13634-122">Save the test data to the test results directory that was created earlier.</span></span>  
  
16. <span data-ttu-id="13634-123">下一個測試回合執行任何必要的清除作業。</span><span class="sxs-lookup"><span data-stu-id="13634-123">Perform any necessary cleanup for the next test run.</span></span>  
  
 <span data-ttu-id="13634-124">每一個步驟只會列出可以使用 BizUnit 自動化。</span><span class="sxs-lookup"><span data-stu-id="13634-124">Each and every one of the steps just listed can be automated using BizUnit.</span></span> <span data-ttu-id="13634-125">藉由使用 BizUnit 提供的現有測試步驟資產，您可以快速且輕鬆地產生自動化的效能測試 BizTalk Server 解決方案。</span><span class="sxs-lookup"><span data-stu-id="13634-125">By utilizing the existing test step assets that BizUnit provides, you can quickly and easily generate an automated performance test for a BizTalk Server solution.</span></span> <span data-ttu-id="13634-126">若要執行測試過一個晚上 – 這表示結果已準備進行分析，在早上彈性自動化使用 BizUnit 測試的效能的主要優點的其中一個。</span><span class="sxs-lookup"><span data-stu-id="13634-126">One of the primary benefits of automating performance testing by using BizUnit is the flexibility to run tests overnight – meaning that the results are ready for analysis in the morning.</span></span> <span data-ttu-id="13634-127">這可大幅減少專案小組測試的效能的負擔。</span><span class="sxs-lookup"><span data-stu-id="13634-127">This greatly reduces the burden of performance testing on a project team.</span></span>  
  
## <a name="the-microsoft-biztalk-loadgen-2007-tool"></a><span data-ttu-id="13634-128">Microsoft BizTalk LoadGen 2007 工具</span><span class="sxs-lookup"><span data-stu-id="13634-128">The Microsoft BizTalk LoadGen 2007 tool</span></span>  
 <span data-ttu-id="13634-129">BizTalk LoadGen 2007 工具 (LoadGen) 是負載測試由 BizTalk Server 2006 產品群組中壓力和效能測試的小組開發的工具。</span><span class="sxs-lookup"><span data-stu-id="13634-129">The BizTalk LoadGen 2007 tool (LoadGen) is a load testing tool that was developed by the Stress and Performance Testing team in the BizTalk Server 2006 product group.</span></span> <span data-ttu-id="13634-130">LoadGen 被設計成快速、 輕鬆地且可靠地定義模擬實際執行等級的訊息的磁碟區的負載測試。</span><span class="sxs-lookup"><span data-stu-id="13634-130">LoadGen was designed to quickly, easily, and reliably define load tests that simulate production level message volumes.</span></span> <span data-ttu-id="13634-131">LoadGen 是多執行緒、 組態導向，並支援多個傳輸。</span><span class="sxs-lookup"><span data-stu-id="13634-131">LoadGen is multi-threaded, configuration-driven, and supports multiple transports.</span></span> <span data-ttu-id="13634-132">BizTalk 產品團隊使用 LoadGen 採每日。因此，您可以有較高程度的信心，此工具是持久，適合用途，以及可以模擬各種 BizTalk 案例。</span><span class="sxs-lookup"><span data-stu-id="13634-132">The BizTalk product group uses LoadGen on a daily basis; therefore you can have a high degree of confidence that the tool is durable, fit for the purpose, and able to simulate a wide variety of BizTalk scenarios.</span></span>  
  
 <span data-ttu-id="13634-133">LoadGen 採用模組化的設計，其中包含三個層級：**簡報**， **framework**和**元件**。</span><span class="sxs-lookup"><span data-stu-id="13634-133">LoadGen employs a modular design that consists of three layers: **presentation**, **framework** and **component**.</span></span> <span data-ttu-id="13634-134">展示層包含命令列的驅動程式，負責驅動的架構。</span><span class="sxs-lookup"><span data-stu-id="13634-134">The presentation layer consists of a command-line driver, which is responsible for driving the framework.</span></span> <span data-ttu-id="13634-135">架構圖層會讀取組態檔，然後執行 其中指定的元件。</span><span class="sxs-lookup"><span data-stu-id="13634-135">The framework layer reads a configuration file and then executes the components specified therein.</span></span> <span data-ttu-id="13634-136">元件圖層包含三種類型的元件：**負載產生器**，**訊息建立者**和**節流控制器**。</span><span class="sxs-lookup"><span data-stu-id="13634-136">The component layer consists of three types of components: **load generators**, **message creators** and **throttle controllers**.</span></span> <span data-ttu-id="13634-137">每個元件，所以您可以建立您自己，並插入 LoadGen 解決您的案例的需求。</span><span class="sxs-lookup"><span data-stu-id="13634-137">Each of these components is extensible, so you can create your own and plug them into LoadGen to address the needs of your scenario.</span></span> <span data-ttu-id="13634-138">因為 LoadGen 由 BizTalk Server 產品小組所開發，您應該會發現的方塊外元件都滿足大部分的測試需求。</span><span class="sxs-lookup"><span data-stu-id="13634-138">Because LoadGen was developed by the BizTalk Server product group, you should find that the out-of-the-box components will fulfill most of your load testing requirements.</span></span> <span data-ttu-id="13634-139">這裡會更詳細地說明每個元件。</span><span class="sxs-lookup"><span data-stu-id="13634-139">Each of these components is described in greater detail here.</span></span>  
  
-   <span data-ttu-id="13634-140">**負載產生器**負責傳輸透過特定傳輸的訊息。</span><span class="sxs-lookup"><span data-stu-id="13634-140">**Load generators** are responsible for transmitting messages via a particular transport.</span></span> <span data-ttu-id="13634-141">負載產生器可供下列傳輸：</span><span class="sxs-lookup"><span data-stu-id="13634-141">Load generators are provided for the following transports:</span></span>  
  
    -   <span data-ttu-id="13634-142">檔案</span><span class="sxs-lookup"><span data-stu-id="13634-142">File</span></span>  
  
    -   <span data-ttu-id="13634-143">HTTP</span><span class="sxs-lookup"><span data-stu-id="13634-143">HTTP</span></span>  
  
    -   <span data-ttu-id="13634-144">MQSeries</span><span class="sxs-lookup"><span data-stu-id="13634-144">MQSeries</span></span>  
  
    -   <span data-ttu-id="13634-145">MSMQLarge</span><span class="sxs-lookup"><span data-stu-id="13634-145">MSMQLarge</span></span>  
  
    -   <span data-ttu-id="13634-146">MSMQ</span><span class="sxs-lookup"><span data-stu-id="13634-146">MSMQ</span></span>  
  
    -   <span data-ttu-id="13634-147">SOAP</span><span class="sxs-lookup"><span data-stu-id="13634-147">SOAP</span></span>  
  
    -   <span data-ttu-id="13634-148">Web Services Enhancements (WSE)</span><span class="sxs-lookup"><span data-stu-id="13634-148">Web Services Enhancements (WSE)</span></span>  
  
    -   <span data-ttu-id="13634-149">Windows SharePoint Services (WSS)</span><span class="sxs-lookup"><span data-stu-id="13634-149">Windows SharePoint Services (WSS)</span></span>  
  
    -   <span data-ttu-id="13634-150">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="13634-150">Windows Communication Foundation (WCF)</span></span>  
  
-   <span data-ttu-id="13634-151">**訊息建立者**是您需要產生訊息包含唯一的資料時可用的選用元件。</span><span class="sxs-lookup"><span data-stu-id="13634-151">**Message creators** are an optional component that can be used when you need to generate messages that contain unique data.</span></span> <span data-ttu-id="13634-152">訊息的建立者使用兩種模式的建立。同步和非同步。</span><span class="sxs-lookup"><span data-stu-id="13634-152">Message creators use one of two modes of creation; synchronous and asynchronous.</span></span> <span data-ttu-id="13634-153">如果指定的同步訊息建立模式，則 LoadGen 會使用單一執行緒來建立訊息，以確保每個訊息都包含唯一的內容。</span><span class="sxs-lookup"><span data-stu-id="13634-153">If the synchronous message creation mode is specified, LoadGen uses only a single thread to create messages to ensure that each message contains a unique payload.</span></span> <span data-ttu-id="13634-154">同步模式可確保每個訊息內的唯一資料，而這個模式也會限制可調適性。</span><span class="sxs-lookup"><span data-stu-id="13634-154">While the synchronous mode guarantees unique data within each message, this mode also limits scalability.</span></span> <span data-ttu-id="13634-155">LoadGen 也提供使用多個執行緒; 的非同步訊息建立者這可讓 LoadGen，以符合目標訊息速率 （因為它只可以建立更多的執行緒）。</span><span class="sxs-lookup"><span data-stu-id="13634-155">LoadGen also provides asynchronous message creators that use multiple execution threads; this enables LoadGen to meet the target message rate (because it can simply create more threads).</span></span> <span data-ttu-id="13634-156">在非同步模式中，訊息建立者可能會設定為隨機修改每個個別訊息的資料。</span><span class="sxs-lookup"><span data-stu-id="13634-156">In asynchronous mode, the message creator may be configured to randomly modify data for each individual message.</span></span> <span data-ttu-id="13634-157">不過，它會使用多個執行緒，因為它並不保證在測試期間所產生的所有訊息會都包含唯一的內容。</span><span class="sxs-lookup"><span data-stu-id="13634-157">However, because it uses multiple threads, it does not guarantee that all message generated during the test will contain a unique payload.</span></span>  
  
-   <span data-ttu-id="13634-158">**節流控制器**確保訊息的傳輸速率穩定所控管負載產生器，當測試正在執行。</span><span class="sxs-lookup"><span data-stu-id="13634-158">**Throttle controllers** ensure that messages are transmitted at a steady rate by governing the load generators while the test is running.</span></span> <span data-ttu-id="13634-159">LoadGen 也會公開自訂節流，可讓您控制流程的訊息，根據準則包括：</span><span class="sxs-lookup"><span data-stu-id="13634-159">LoadGen also exposes custom throttling, which enables you to control the flow of messages based on criteria including:</span></span>  
  
    -   <span data-ttu-id="13634-160">在資料夾中的檔案數目</span><span class="sxs-lookup"><span data-stu-id="13634-160">Number of files in a folder</span></span>  
  
    -   <span data-ttu-id="13634-161">資料庫資料表中的資料列數目</span><span class="sxs-lookup"><span data-stu-id="13634-161">Number of rows in a database table</span></span>  
  
    -   <span data-ttu-id="13634-162">MSMQ 或 MQSeries 的訊息佇列的深度</span><span class="sxs-lookup"><span data-stu-id="13634-162">Depth of an MSMQ or MQSeries message queue</span></span>  
  
 <span data-ttu-id="13634-163">Microsoft [BizTalk LoadGen 2007 工具](http://go.microsoft.com/fwlink/?LinkId=59841)適用於下載[http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841) (http://go.microsoft.com/fwlink/?LinkId=59841)。</span><span class="sxs-lookup"><span data-stu-id="13634-163">The Microsoft [BizTalk LoadGen 2007 tool](http://go.microsoft.com/fwlink/?LinkId=59841) is available for download at [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841) (http://go.microsoft.com/fwlink/?LinkId=59841).</span></span>  
  
### <a name="sample-loadgen-configuration-file"></a><span data-ttu-id="13634-164">LoadGen 組態檔範例</span><span class="sxs-lookup"><span data-stu-id="13634-164">Sample LoadGen configuration file</span></span>  
 <span data-ttu-id="13634-165">LoadGen 的所有組態資訊都儲存在 xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="13634-165">All LoadGen configuration information is stored in an xml file.</span></span> <span data-ttu-id="13634-166">LoadGen 組態檔包含\<CommonSection > 設定的預設設定來執行所有 LoadGen 工作 LoadGen 案例中的項目。</span><span class="sxs-lookup"><span data-stu-id="13634-166">The LoadGen configuration file contains a \<CommonSection> element that configures the default settings for all LoadGen tasks in the LoadGen scenario.</span></span> <span data-ttu-id="13634-167">LoadGen 組態檔也可以包含一或多個\<區段 > 項目，提供特定的 LoadGen 工作的組態設定。</span><span class="sxs-lookup"><span data-stu-id="13634-167">The LoadGen configuration file can also contain one or more \<Section> elements that provide configuration settings for a specific LoadGen task.</span></span> <span data-ttu-id="13634-168">中的項目\<區段 > 項目中指定任何預設值會取代\<CommonSection > 項目。</span><span class="sxs-lookup"><span data-stu-id="13634-168">Entries in a \<Section> element supersede any default values specified in the \<CommonSection> element.</span></span>  
  
 <span data-ttu-id="13634-169">遵循範例 LoadGen 組態檔是稍微修改的 FileToFileLG.xml 範例組態檔包含 \ConfigFiles\ConsoleConfigFiles 子目錄 LoadGen 安裝目錄中的版本。</span><span class="sxs-lookup"><span data-stu-id="13634-169">The sample LoadGen configuration file that follows is a slightly modified version of the FileToFileLG.xml sample configuration file that is included in the \ConfigFiles\ConsoleConfigFiles subdirectory of the LoadGen installation directory.</span></span> <span data-ttu-id="13634-170">這項測試將 25 的訊息傳送\<LotSizePerInterval > 每隔 200 毫秒\<SleepInterval >，每個負載產生器的 5 個執行緒\<NumThreadsperSection > 5000 訊息後將會停止在負載測試和\<NumFiles > 已傳送。</span><span class="sxs-lookup"><span data-stu-id="13634-170">This test sends 25 messages \<LotSizePerInterval> every 200 milliseconds \<SleepInterval>, 5 threads per load generator \<NumThreadsperSection>and will stop the load test after 5000 messages \<NumFiles> have been sent.</span></span>  
  
 <span data-ttu-id="13634-171">中指定檔案節流控制器\<ThrottleController > 一節。</span><span class="sxs-lookup"><span data-stu-id="13634-171">The file throttle controller is specified in the \<ThrottleController> section.</span></span> <span data-ttu-id="13634-172">值\<ThresholdRange > 設為 1000年-2000，這表示，如果檔案位置 （參數） C:\Scenarios\FileToFile\Receive 少於 1000年，或是超過 2000年檔案，節流控制器將會啟用節流設定檔產生器和視需要增加/減少負載。</span><span class="sxs-lookup"><span data-stu-id="13634-172">The value for \<ThresholdRange> is set to 1000-2000, which means that if the file location C:\Scenarios\FileToFile\Receive (Parameters) has less than 1000 or more than 2000 files, the throttle controller will throttle the file generator and increase/decrease load as appropriate.</span></span> <span data-ttu-id="13634-173">中的檔案位置的檔案數目將會檢查每 1000年毫秒\<SleepInterval >。</span><span class="sxs-lookup"><span data-stu-id="13634-173">The number of files in the file location will be checked every 1000 milliseconds \<SleepInterval>.</span></span> <span data-ttu-id="13634-174">\<FileSection > 元素可定義負載產生器來傳送訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="13634-174">The \<FileSection> element defines the properties for the messages to be sent by the load generators.</span></span> <span data-ttu-id="13634-175">FileToFileLG.xml 檔案\<SrcFilePath > 將會 LoadGen 複製到 filedrop C:\Scenarios\FileToFile\Receive \<DstFilePath >。</span><span class="sxs-lookup"><span data-stu-id="13634-175">The FileToFileLG.xml file \<SrcFilePath> will be copied by LoadGen to the filedrop C:\Scenarios\FileToFile\Receive \<DstFilePath>.</span></span> <span data-ttu-id="13634-176">因為這是預設的傳輸中指定這裡使用的檔案傳輸\<傳輸名稱 > 內的項目\<CommonSection > 項目。</span><span class="sxs-lookup"><span data-stu-id="13634-176">The file transport is used here because this is the default transport specified in the \<Transport Name> element within the \<CommonSection> element.</span></span>  
  
```  
<LoadGenFramework>  
   <CommonSection>  
      <LoadGenVersion>2</LoadGenVersion>  
      <OptimizeLimitFileSize>204800</OptimizeLimitFileSize>  
      <NumThreadsPerSection>5</NumThreadsPerSection>  
      <SleepInterval>200</SleepInterval>  
      <LotSizePerInterval>25</LotSizePerInterval>  
      <RetryInterval>10000</RetryInterval>  
      <StopMode Mode="Files">  
         <NumFiles>5000</NumFiles>  
      </StopMode>  
      <Transport Name="FILE">  
         <Assembly>FileTransport.dll/FileTransport.FileTransport</Assembly>  
      </Transport>  
      <ThrottleController Mode="Custom">  
         <Monitor Name="File">  
            <Assembly>FileMonitor.dll/DropLocationFileMonitor.DropLocationFileMonitor</Assembly>  
            <ThresholdRange>1000-2000</ThresholdRange>  
            <SleepInterval>1000</SleepInterval>  
            <Parameters>C:\Scenarios\FileToFile\Receive</Parameters>  
         </Monitor>  
         <ThrottleCondition>File</ThrottleCondition>  
      </ThrottleController>  
   </CommonSection>  
   <Section Name="FileSection">  
      <SrcFilePath>C:\LoadGen\ConfigFiles\ConsoleConfigFiles\FileToFileLG.xml</SrcFilePath>  
      <DstLocation>  
         <Parameters>  
            <DstFilePath>C:\Scenarios\FileToFile\Receive</DstFilePath>  
         </Parameters>  
      </DstLocation>  
   </Section>  
</LoadGenFramework>  
```  
  
### <a name="using-bizunit-to-drive-loadgen"></a><span data-ttu-id="13634-177">使用磁碟機 LoadGen BizUnit</span><span class="sxs-lookup"><span data-stu-id="13634-177">Using BizUnit to drive LoadGen</span></span>  
 <span data-ttu-id="13634-178">BizUnit 提供**LoadGenExecuteStep** ，以協助自動化的效能與穩定性測試。</span><span class="sxs-lookup"><span data-stu-id="13634-178">BizUnit provides the **LoadGenExecuteStep** to facilitate automated performance and stability testing.</span></span> <span data-ttu-id="13634-179">**TestExecution**範例 BizUnit 組態檔會使用階段**LoadGenExecuteStep**下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="13634-179">The **TestExecution** stage of a sample BizUnit configuration file that uses **LoadGenExecuteStep** is shown in the following code example.</span></span> <span data-ttu-id="13634-180">請注意，這個步驟會接受單一組態參數，而是 LoadGen 組態檔的位置。</span><span class="sxs-lookup"><span data-stu-id="13634-180">Note that this step accepts a single configuration parameter, which is the location of the LoadGen configuration file.</span></span>  
  
```  
<TestCase testName="Test_LoadGen">  
   <TestSetup>  
   </TestSetup>  
   <TestExecution>  
      <TestStep assemblyPath="" typeName="BizUnit.LoadGenExecuteStep, BizUnit.LoadGenSteps">  
         <LoadGenTestConfig>..\..\..\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
      </TestStep>  
   </TestExecution>  
   <!-- Test cleanup: test cases should always leave the system in the state they found it -->  
   <TestCleanup>  
   </TestCleanup>  
</TestCase>  
```  
  
 <span data-ttu-id="13634-181">本主題的其餘部分描述的組態檔會自動執行效能測試使用 LoadGen BizUnit 測試案例。</span><span class="sxs-lookup"><span data-stu-id="13634-181">The remainder of this topic describes the configuration file for a BizUnit test case that automates performance testing with LoadGen.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13634-182">此組態檔可以用做為範本，來快速將 BizUnit 和 LoadGen 一部分效能測試的整合。</span><span class="sxs-lookup"><span data-stu-id="13634-182">This configuration file can be used as a template to quickly integrate BizUnit and LoadGen as part of your performance testing.</span></span> <span data-ttu-id="13634-183">然後再執行此測試案例，您必須自訂設定檔，為您的環境。</span><span class="sxs-lookup"><span data-stu-id="13634-183">Before running this test case, you will need to customize the configuration file for your environment.</span></span> <span data-ttu-id="13634-184">也會據以指出必須自訂組態檔的區段。</span><span class="sxs-lookup"><span data-stu-id="13634-184">Sections of the configuration file that must be customized are indicated accordingly.</span></span>  
  
 <span data-ttu-id="13634-185">一開始指定的值**testName**適用於 BizTalk 解決方案的參數。</span><span class="sxs-lookup"><span data-stu-id="13634-185">To begin with, specify a value for the **testName** parameter that is appropriate for the BizTalk solution.</span></span>  
  
```  
<TestCase testName="Performance-Guide-Sample-Loadgen-Test">  
```  
  
 <span data-ttu-id="13634-186">然後將內容的變數加入**TestSetup**階段。</span><span class="sxs-lookup"><span data-stu-id="13634-186">Then add context variables to the **TestSetup** stage.</span></span> <span data-ttu-id="13634-187">測試案例的期間，將會參考這些內容變數。</span><span class="sxs-lookup"><span data-stu-id="13634-187">These context variables will be referenced throughout the duration of the test case.</span></span> <span data-ttu-id="13634-188">若要使用此組態檔，修改為指定的值**TestCaseResultsDir** (C:\Dev Work\Perf 指南 Demos\PerfResults\\) 和**機器**(BIZTALKADMIN01)，以符合您環境。</span><span class="sxs-lookup"><span data-stu-id="13634-188">To use this configuration file, modify the values specified for **TestCaseResultsDir** (C:\Dev Work\Perf Guide Demos\PerfResults\\) and **Machine** (BIZTALKADMIN01) to match your environment.</span></span>  
  
```  
<TestSetup>  
   <!-- Context property: name of test run -->  
   <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
      <ContextItem contextKey="TestRunName">  
         <ItemTest takeFromCtx="BizUnitTestCaseName"></ItemTest>  
         <ItemTest>_%DateTime%</ItemTest>  
      </ContextItem>  
   </TestStep>  
   <!-- Context property: name of test directory to store results -->  
   <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
      <ContextItem contextKey="TestCaseResultsDir">  
         <ItemTest>C:\Dev Work\Perf Guide Demos\PerfResults\</ItemTest>  
         <ItemTest takeFromCtx="TestRunName"></ItemTest>  
      </ContextItem>  
   </TestStep>  
   <!-- Context property: perfmon log file -->  
   <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
      <ContextItem contextKey="PerfMonFilePath">  
         <ItemTest takeFromCtx="TestCaseResultsDir"></ItemTest>  
         <ItemTest>\PerfCounters.blg</ItemTest>  
      </ContextItem>  
   </TestStep>  
   <!-- Context property: destintation for app event log on test computer -->  
   <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
      <ContextItem contextKey="DestPath- BIZTALKADMIN01-AppEventLog">  
         <ItemTest takeFromCtx="TestCaseResultsDir"></ItemTest>  
         <ItemTest> BIZTALKADMIN01_ApplicationLog.evt</ItemTest>  
      </ContextItem>  
   </TestStep>  
   <!-- Clear the application event log on test computer -->  
   <TestStep assemblyPath="" typeName="BizUnit.EventLogClearStep">  
      <Machine>BIZTALKADMIN01</Machine>  
      <EventLog>Application</EventLog>  
   </TestStep>  
   <!-- Create the directory to save all the test results -->  
   <TestStep assemblyPath="" typeName="BizUnit.CreateDirectory">  
      <DirectoryName takeFromCtx="TestCaseResultsDir" ></DirectoryName>  
   </TestStep>  
</TestSetup>  
```  
  
 <span data-ttu-id="13634-189">完成之後**TestSetup**階段中，我們輸入**TestExecution**階段。</span><span class="sxs-lookup"><span data-stu-id="13634-189">After completing the **TestSetup** stage, we enter the **TestExecution** stage.</span></span> <span data-ttu-id="13634-190">第一個步驟是停止 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="13634-190">The first step is to stop the BizTalk host instances.</span></span> <span data-ttu-id="13634-191">個別**BizUnit.HostConductorStep**區段必須加入每個不同的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="13634-191">A separate **BizUnit.HostConductorStep** section must be added for each distinct host instance.</span></span> <span data-ttu-id="13634-192">如果您在環境中使用此組態檔，您也必須輸入適當的值**HostInstanceName**，**伺服器**，**登入**，和**密碼**。</span><span class="sxs-lookup"><span data-stu-id="13634-192">If you are using this configuration file in your environment, you will also need to enter the appropriate values for **HostInstanceName**, **Server**, **Logon**, and **Password**.</span></span>  
  
```  
<TestExecution>  
   <!-- Step 1: Stop BizTalk Hosts -->  
   <TestStep assemblyPath="" typeName="BizUnit.HostConductorStep, BizUnit.BizTalkSteps">  
      <Action>stop</Action>  
      <HostInstanceName>BizTalkServerApplication</HostInstanceName>  
      <Server>BizTalkAdmin01</Server>  
      <Logon>ServerName\Administrator</Logon>  
      <PassWord>Pass@word1</PassWord>  
      <GrantLogOnAsService>true</GrantLogOnAsService>  
   </TestStep>  
```  
  
 <span data-ttu-id="13634-193">停止所有主控件執行個體之後, 我們清除 BizTalk MessageBox 資料庫，使用 bts_CleanupMsgBox 預存程序。</span><span class="sxs-lookup"><span data-stu-id="13634-193">After stopping all of the host instances, we clean up the BizTalk MessageBox database using the bts_CleanupMsgBox stored procedure.</span></span> <span data-ttu-id="13634-194">若要使用此步驟中，您必須修改的值**ConnectionString**以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="13634-194">To use this step you must modify the value for **ConnectionString** to match your environment.</span></span>  
  
```  
<!-- Step 2: Clean Up MessageBox -->  
<TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
   <DelayBeforeExecution>1</DelayBeforeExecution>  
   <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=BizTalkMsgBoxDb;server=BIZTALKADMIN01;Connect Timeout=30</ConnectionString>  
   <SQLQuery>  
      <RawSQLQuery>[dbo].[bts_CleanupMsgbox]</RawSQLQuery>  
   </SQLQuery>  
</TestStep>  
```  
  
 <span data-ttu-id="13634-195">步驟 3 **TestExecution**階段開始範本檔案中指定的效能監視器 (PerfMon) 計數器。</span><span class="sxs-lookup"><span data-stu-id="13634-195">Step 3 of the **TestExecution** stage starts Performance Monitor (PerfMon) counters that are specified in a template file.</span></span> <span data-ttu-id="13634-196">範例範本檔案會列出下方範例**BizUnit.PerfmonCountersStep**下方。</span><span class="sxs-lookup"><span data-stu-id="13634-196">A sample template file is listed underneath the sample **BizUnit.PerfmonCountersStep** below.</span></span> <span data-ttu-id="13634-197">若要使用的範本檔案，您必須修改指定的值**CountersListFilePath**以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="13634-197">To use the template file, you must modify the value specified for **CountersListFilePath** to match your environment.</span></span> <span data-ttu-id="13634-198">修改範例效能監視器計數器範本檔案，包括任何您想要監視，或移除任何不是適用於您案例的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="13634-198">Modify the sample performance monitor counter template file to include any PerfMon counters that you would like to monitor or remove any that are not relevant to your scenario.</span></span>  
  
```  
<!-- Step 3: Start Perfmon counters -->  
<TestStep assemblyPath="" typeName="BizUnit.PerfmonCountersStep">  
   <PerfmonAction>Start</PerfmonAction>  
   <CounterSetName>PerfGuidePerfmonCounters</CounterSetName>  
   <CountersListFilePath>C:\Dev Work\Perf Guide Demos\Test_06_PerfCounters.txt</CountersListFilePath>  
   <SampleInterval>5</SampleInterval>  
   <PerfmonLogFilePath takeFromCtx="PerfMonFilePath"></PerfmonLogFilePath>  
</TestStep>  
```  
  
 <span data-ttu-id="13634-199">**範例效能監視器計數器範本檔 (Test_06_PerfCounters.txt BizUnit.PerfmonCountersStep 所參考):**</span><span class="sxs-lookup"><span data-stu-id="13634-199">**Sample Performance Monitor counter template file (Test_06_PerfCounters.txt referenced by the BizUnit.PerfmonCountersStep):**</span></span>  
  
```  
\Processor(*)\*  
\Process(*)\*  
\Memory\*  
\PhysicalDisk(*)\*  
\System\Context Switches/sec  
\System\Processor Queue Length  
\BizTalk:FILE Receive Adapter(*)\*  
\BizTalk:File Send Adapter(*)\*  
\BizTalk:FTP Receive Adapter(*)\*  
\BizTalk:FTP Send Adapter(*)\*  
\BizTalk:HTTP Receive Adapter(*)\*  
\BizTalk:HTTP Send Adapter(*)\*  
\BizTalk:Message Agent(*)\*  
\BizTalk:Messaging(*)\*  
\BizTalk:Message Box:General Counters(*)\*  
\BizTalk:Message Box:Host Counters(*)\*  
\BizTalk:Messaging Latency(*)\*  
\BizTalk:SOAP Receive Adapter(*)\*  
\BizTalk:SOAP Send Adapter(*)\*  
\BizTalk:TDDS(*)\*  
\XLANG/s Orchestrations(*)\*  
```  
  
 <span data-ttu-id="13634-200">現在，我們會開始 BizTalk Server 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="13634-200">Now we start the BizTalk Server host instances.</span></span> <span data-ttu-id="13634-201">個別**BizUnit.HostConductorStep**區段必須加入每個不同的主控件執行個體 （distinct 包含多個主控件執行個體跨伺服器）。</span><span class="sxs-lookup"><span data-stu-id="13634-201">A separate **BizUnit.HostConductorStep** section must be added for each distinct host instance (distinct includes multiple instances of a host across servers).</span></span> <span data-ttu-id="13634-202">如果您在環境中使用此組態檔，您也必須輸入適當的值**HostInstanceName**，**伺服器**，**登入**，和**密碼**。</span><span class="sxs-lookup"><span data-stu-id="13634-202">If you are using this configuration file in your environment, you will also need to enter the appropriate values for **HostInstanceName**, **Server**, **Logon**, and **Password**.</span></span>  
  
```  
<!-- Step 4: Start BizTalk Hosts -->  
<TestStep assemblyPath="" typeName="BizUnit.BizTalkSteps.HostConductorStep, BizUnit.BizTalkSteps, Version=3.0.0.0, Culture=neutral, PublicKeyToken=7eb7d82981ae5162">  
   <Action>start</Action>  
   <HostInstanceName>BizTalkServerApplication</HostInstanceName>  
   <Server>BizTalkAdmin01</Server>  
   <Logon>ServerName\Administrator</Logon>  
   <PassWord>Pass@word1</PassWord>  
   <GrantLogOnAsService>true</GrantLogOnAsService>  
</TestStep>  
```  
  
 <span data-ttu-id="13634-203">步驟 5 」 primes"系統傳送至 BizTalk Server 使用的幾個訊息**BizUnit.LoadGenExecuteStep**; 的值變更**LoadGenTestConfig**參數，以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="13634-203">Step 5 “primes” the system by sending a couple of messages to BizTalk Server using **BizUnit.LoadGenExecuteStep**; change the value of the **LoadGenTestConfig** parameter to match your environment.</span></span>  
  
```  
<!-- Step 5: Send Priming messages -->  
<TestStep assemblyPath="" typeName="BizUnit.LoadGenExecuteStep, BizUnit.LoadGenSteps">  
   <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
</TestStep>  
```  
  
 <span data-ttu-id="13634-204">步驟 6 LoadGen 組態檔案寫入記憶體，讓它可以再寫入至測試結果資料庫測試完成時。</span><span class="sxs-lookup"><span data-stu-id="13634-204">Step 6 writes the LoadGen configuration file to memory so that it can then be written to the test results database when the test is complete.</span></span>  
  
```  
  
      <!-- Step 6: Read loadgen file into context variable -->  
<TestStep assemblyPath="" typeName="BizUnit.FileReadAndLoadToContext">  
   <FilePath>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</FilePath>  
   <ContextPropertyName>LoadGenFileContent</ContextPropertyName>  
</TestStep>  
```  
  
 <span data-ttu-id="13634-205">現在我們可以撰寫測試開始時間到測試結果資料庫。</span><span class="sxs-lookup"><span data-stu-id="13634-205">Now we write the test start time to a test results database.</span></span> <span data-ttu-id="13634-206">修改**ConnectionString**和**RawSQLQuery**參數以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="13634-206">Modify the **ConnectionString** and **RawSQLQuery** parameters to match your environment.</span></span>  
  
```  
<!-- Step 7: Update test results DB with test start time -->  
<TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
   <DelayBeforeExecution>1</DelayBeforeExecution>  
   <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=TestResults;server=BizTalkAdmin01;Connect Timeout=30</ConnectionString>  
   <SQLQuery>  
      <RawSQLQuery>INSERT INTO tblPerformanceResults (Test_ID, StartTime,LoadGenFile) VALUES ('{0}',GetDate(),'{1}' )</RawSQLQuery>  
      <SQLQueryParams>  
         <SQLQueryParam takeFromCtx="TestRunName"></SQLQueryParam>  
         <SQLQueryParam takeFromCtx="LoadGenFileContent"></SQLQueryParam>  
      </SQLQueryParams>  
   </SQLQuery>  
</TestStep>  
```  
  
 <span data-ttu-id="13634-207">步驟 8 情況是在實際的效能測試使用起始**BizUnit.LoadGenExecuteStep**。</span><span class="sxs-lookup"><span data-stu-id="13634-207">Step 8 is where the actual performance test is initiated using **BizUnit.LoadGenExecuteStep**.</span></span> <span data-ttu-id="13634-208">此步驟在步驟 5 中指定相同的 LoadGen 組態檔所使用，但是您可以指定任何有效 LoadGen 的設定檔以下。</span><span class="sxs-lookup"><span data-stu-id="13634-208">This step specifies the same LoadGen configuration file that was used in step 5, but you can specify any valid LoadGen configuration file here.</span></span> <span data-ttu-id="13634-209">**BizUnit.DelayStep**在步驟 9 中用來強制執行 5 秒的延遲，等待啟動流經系統的訊息。</span><span class="sxs-lookup"><span data-stu-id="13634-209">**BizUnit.DelayStep** is used in step 9 to impose a 5-second delay to allow time for messages to start flowing through the system.</span></span> <span data-ttu-id="13634-210">主控件佇列長度使用計算**BizUnit.PerMonCounterMonitorStep**。</span><span class="sxs-lookup"><span data-stu-id="13634-210">Host queue length is calculated using **BizUnit.PerMonCounterMonitorStep**.</span></span> <span data-ttu-id="13634-211">當此參數達到 1 步驟 10 中所指定的值時，會結束測試。</span><span class="sxs-lookup"><span data-stu-id="13634-211">When this parameter reaches a value of 1 as specified in step 10, the test is concluded.</span></span> <span data-ttu-id="13634-212">變更的值**InstanceName**和**伺服器**參數以符合您想要監視您的環境中的伺服器與主控件執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="13634-212">Change the values for the **InstanceName** and **Server** parameters to match the name of the host instance and server that you would like to monitor in your environment.</span></span>  
  
```  
<!-- Step 8: LoadGen: Load actual perf test -->  
<TestStep assemblyPath="" typeName="BizUnit.LoadGenSteps.LoadGenExecuteStep, BizUnit.LoadGenSteps , Version=3.0.0.0, Culture=neutral, PublicKeyToken=7eb7d82981ae5162">  
   <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
</TestStep>  
<!-- Step 9: Delay for 5 secs to allow msgs to start flowing -->  
<TestStep assemblyPath="" typeName="BizUnit.DelayStep">  
   <Delay>5000</Delay>  
</TestStep>  
<!-- Step 10: Wait for Orch Host Queue depth to reach one -->  
<TestStep assemblyPath="" typeName="BizUnit.PerfMonCounterMonitorStep">  
   <CategoryName>BizTalk:Message Box:Host Counters</CategoryName>  
   <CounterName>Host Queue - Length</CounterName>  
   <InstanceName>BizTalkServerApplication:biztalkmsgboxdb:BizTalkAdmin01</InstanceName>  
   <Server>BizTalkAdmin01</Server>  
   <CounterTargetValue>1</CounterTargetValue>  
</TestStep>  
```  
  
 <span data-ttu-id="13634-213">在測試結束時，我們使用**BizUnit.DBExecuteNonQueryStep**更新測試結果資料庫。</span><span class="sxs-lookup"><span data-stu-id="13634-213">At the conclusion of the test we use **BizUnit.DBExecuteNonQueryStep** to update the test results database.</span></span> <span data-ttu-id="13634-214">完成此步驟結尾所示，表示測試執行階段中，結尾\</TestExecution > 標記。</span><span class="sxs-lookup"><span data-stu-id="13634-214">Completion of this step signifies the end of the test execution stage, as indicated by the closing \</TestExecution> tag.</span></span> <span data-ttu-id="13634-215">同樣地，您必須修改**ConnectionString**和**RawSQLQuery**參數以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="13634-215">Again, you must modify the **ConnectionString** and **RawSQLQuery** parameters to match your environment.</span></span>  
  
```  
   <!-- Step 11: Update test results DB with test stop time -->  
   <TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
      <DelayBeforeExecution>1</DelayBeforeExecution>  
      <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=TestResults;server=BIZTALKADMIN01;Connect Timeout=30</ConnectionString>  
      <SQLQuery>  
         <RawSQLQuery>UPDATE tblPerformanceResults SET EndTime = GetDate() WHERE Test_ID = '{0}'</RawSQLQuery>  
         <SQLQueryParams>  
            <SQLQueryParam takeFromCtx="TestRunName"></SQLQueryParam>  
         </SQLQueryParams>  
      </SQLQuery>  
   </TestStep>  
</TestExecution>  
```  
  
 <span data-ttu-id="13634-216">完成的執行階段時，我們會輸入測試清除階段。</span><span class="sxs-lookup"><span data-stu-id="13634-216">Upon concluding the execution stage we enter the test cleanup stage.</span></span> <span data-ttu-id="13634-217">這個階段會使用**BizUnit.PerfmonCountersStep**停止稍早 （步驟 3) 中啟動效能監視器計數器。</span><span class="sxs-lookup"><span data-stu-id="13634-217">This stage uses **BizUnit.PerfmonCountersStep** to stop the Performance Monitor counters that were started earlier (in Step 3).</span></span>  
  
```  
<TestCleanup>  
      <!-- Return system to state prior to test -->  
      <!-- Stop perfmon counters -->  
      <TestStep assemblyPath="" typeName="BizUnit.PerfmonCountersStep" failOnError="false">  
         <PerfmonAction>Stop</PerfmonAction>  
         <CounterSetName>PerfGuidePerfmonCounters</CounterSetName>  
      </TestStep>  
   </TestCleanup>  
</TestCase>  
```  
  
 <span data-ttu-id="13634-218">此範例中所述 BizUnit 如何結合 LoadGen 自動化效能測試。</span><span class="sxs-lookup"><span data-stu-id="13634-218">This example illustrated how BizUnit can be combined with LoadGen to automate performance testing.</span></span> <span data-ttu-id="13634-219">BizUnit 組態檔所描述的負載測試可以從 Visual Studio 測試工具執行功能測試相同的方式。</span><span class="sxs-lookup"><span data-stu-id="13634-219">The load test described by the BizUnit configuration file can be executed from Visual Studio’s testing tools in the same manner as the functional testing.</span></span> <span data-ttu-id="13634-220">採用這個方法可讓您集中管理、 管理及收集的效能測試資料。</span><span class="sxs-lookup"><span data-stu-id="13634-220">Adopting this approach enables you to centrally manage, administer, and collect data for your performance testing.</span></span>  
  
 <span data-ttu-id="13634-221">使用 BizUnit LoadGen 中與自動化方法，是很容易就能排程在離峰時間，將會提供很大的測試結果分析在正常上班時間發生的多個測試回合。</span><span class="sxs-lookup"><span data-stu-id="13634-221">By using BizUnit and LoadGen in an automated approach, it is very easy to schedule multiple test runs to occur during off hours, which will provide ample test results for analysis during normal working hours.</span></span> <span data-ttu-id="13634-222">當將自動化測試的效能，請考慮使用 LoadGen，模型不同整個系統的負載，例如您可能想要模擬不同的程度 （75%、 100%和 125%） 的指令碼的預期實際執行的訊息量。</span><span class="sxs-lookup"><span data-stu-id="13634-222">When automating performance testing, consider using LoadGen scripts that model different loads through the system, for example you may wish to simulate varying degrees (75%, 100% and 125%) of the expected production message volume.</span></span> <span data-ttu-id="13634-223">在執行負載測試時，它是要測試的多載或 [錯誤天] 案例特別重要。</span><span class="sxs-lookup"><span data-stu-id="13634-223">When performing load testing, it is especially important to test the overload or “bad day” scenario.</span></span> <span data-ttu-id="13634-224">先將系統放入實際執行環境中，您應該知道最大持續輸送量 (MST) 是 BizTalk Server 環境中的每個測試案例。</span><span class="sxs-lookup"><span data-stu-id="13634-224">Before placing the system into production, you should know what the maximum sustainable throughput (MST) is for each test case in the BizTalk Server environment.</span></span> <span data-ttu-id="13634-225">如需最大持續性效能的詳細資訊，請參閱[何謂持續性效能？](http://go.microsoft.com/fwlink/?LinkID=132304)</span><span class="sxs-lookup"><span data-stu-id="13634-225">For more information about maximum sustainable performance, see [What Is Sustainable Performance?](http://go.microsoft.com/fwlink/?LinkID=132304)</span></span> <span data-ttu-id="13634-226">(http://go.microsoft.com/fwlink/?LinkID=132304) 中的 BizTalk Server 2009 文件。</span><span class="sxs-lookup"><span data-stu-id="13634-226">(http://go.microsoft.com/fwlink/?LinkID=132304) in the BizTalk Server 2009 documentation.</span></span>  
  
### <a name="the-complete-bizunit-loadgen-sample-configuration-file"></a><span data-ttu-id="13634-227">完整的 BizUnit LoadGen 範例組態檔</span><span class="sxs-lookup"><span data-stu-id="13634-227">The complete BizUnit LoadGen sample configuration file</span></span>  
 <span data-ttu-id="13634-228">下列清單包含先前已參考 BizUnit 組態檔的整個內容。</span><span class="sxs-lookup"><span data-stu-id="13634-228">The following list contains the entire contents of the BizUnit configuration file referenced earlier.</span></span>  
  
```  
<TestCase testName="Performance-Guide-Sample-Loadgen-Test">  
   <TestSetup>  
      <!-- Context property: name of test run -->  
      <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
         <ContextItem contextKey="TestRunName">  
            <ItemTest takeFromCtx="BizUnitTestCaseName"></ItemTest>  
            <ItemTest>_%DateTime%</ItemTest>  
         </ContextItem>  
      </TestStep>  
      <!-- Context property: name of test directory to store results -->  
      <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
         <ContextItem contextKey="TestCaseResultsDir">  
            <ItemTest>C:\Dev Work\Perf Guide Demos\PerfResults\</ItemTest>  
            <ItemTest takeFromCtx="TestRunName"></ItemTest>  
         </ContextItem>  
      </TestStep>  
      <!-- Context property: perfmon log file -->  
      <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
         <ContextItem contextKey="PerfMonFilePath">  
            <ItemTest takeFromCtx="TestCaseResultsDir"></ItemTest>  
            <ItemTest>\PerfCounters.blg</ItemTest>  
         </ContextItem>  
      </TestStep>  
      <!-- Context property: destintation for app event log on BTSSVR-001 -->  
      <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
         <ContextItem contextKey="DestPath-BTSSVR-001-AppEventLog">  
            <ItemTest takeFromCtx="TestCaseResultsDir"></ItemTest>  
            <ItemTest>BTSSVR-001_ApplicationLog.evt</ItemTest>  
         </ContextItem>  
      </TestStep>  
      <!-- Clear the application event log on BTSSVR-001 -->  
      <TestStep assemblyPath="" typeName="BizUnit.EventLogClearStep">  
         <Machine>BIZTALKADMIN01</Machine>  
         <EventLog>Application</EventLog>  
      </TestStep>  
      <!-- Create the directory to save all the test results -->  
      <TestStep assemblyPath="" typeName="BizUnit.CreateDirectory">  
         <DirectoryName takeFromCtx="TestCaseResultsDir" ></DirectoryName>  
      </TestStep>  
   </TestSetup>  
  
   <TestExecution>  
      <!-- Step 1: Stop BizTalk Hosts -->  
      <TestStep assemblyPath="" typeName="BizUnit.HostConductorStep, BizUnit.BizTalkSteps">  
         <Action>stop</Action>  
         <HostInstanceName>BizTalkServerApplication</HostInstanceName>  
         <Server>BizTalkAdmin01</Server>  
         <Logon>ServerName\Administrator</Logon>  
         <PassWord>Pass@word1</PassWord>  
         <GrantLogOnAsService>true</GrantLogOnAsService>  
      </TestStep>  
      <!-- Step 2: Clean Up MessageBox -->  
      <TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
         <DelayBeforeExecution>1</DelayBeforeExecution>  
         <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=BizTalkMsgBoxDb;server=BIZTALKADMIN01;Connect Timeout=30</ConnectionString>  
         <SQLQuery>  
            <RawSQLQuery>[dbo].[bts_CleanupMsgbox]</RawSQLQuery>  
         </SQLQuery>  
      </TestStep>  
      <!-- Step 3: Start Perfmon counters -->  
      <TestStep assemblyPath="" typeName="BizUnit.PerfmonCountersStep">  
         <PerfmonAction>Start</PerfmonAction>  
         <CounterSetName>PerfGuidePerfmonCounters</CounterSetName>  
         <CountersListFilePath>C:\Dev Work\Perf Guide Demos\Test_06_PerfCounters.txt</CountersListFilePath>  
         <SampleInterval>5</SampleInterval>  
         <PerfmonLogFilePath takeFromCtx="PerfMonFilePath"></PerfmonLogFilePath>  
      </TestStep>  
      <!-- Step 4: Start BizTalk Hosts -->  
      <TestStep assemblyPath="" typeName="BizUnit.BizTalkSteps.HostConductorStep, BizUnit.BizTalkSteps, Version=3.0.0.0, Culture=neutral, PublicKeyToken=7eb7d82981ae5162">  
         <Action>start</Action>  
         <HostInstanceName>BizTalkServerApplication</HostInstanceName>  
         <Server>BizTalkAdmin01</Server>  
         <Logon>ServerName\Administrator</Logon>  
         <PassWord>Pass@word1</PassWord>  
         <GrantLogOnAsService>true</GrantLogOnAsService>  
      </TestStep>  
      <!-- Step 5: Send Priming messages -->  
      <TestStep assemblyPath="" typeName="BizUnit.LoadGenExecuteStep, BizUnit.LoadGenSteps">  
         <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
      </TestStep>  
      <!-- Step 6: Read loadgen file into context variable -->  
      <TestStep assemblyPath="" typeName="BizUnit.FileReadAndLoadToContext">  
         <FilePath>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</FilePath>  
         <ContextPropertyName>LoadGenFileContent</ContextPropertyName>  
      </TestStep>  
      <!-- Step 7: Update test results DB with test start time -->  
      <TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
         <DelayBeforeExecution>1</DelayBeforeExecution>  
         <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=TestResults;server=BizTalkAdmin01;Connect Timeout=30</ConnectionString>  
         <SQLQuery>  
            <RawSQLQuery>INSERT INTO tblPerformanceResults (Test_ID, StartTime,LoadGenFile) VALUES ('{0}',GetDate(),'{1}' )</RawSQLQuery>  
            <SQLQueryParams>  
               <SQLQueryParam takeFromCtx="TestRunName"></SQLQueryParam>  
               <SQLQueryParam takeFromCtx="LoadGenFileContent"></SQLQueryParam>  
            </SQLQueryParams>  
         </SQLQuery>  
      </TestStep>  
      <!-- Step 8: LoadGen: Load actual perf test -->  
      <TestStep assemblyPath="" typeName="BizUnit.LoadGenSteps.LoadGenExecuteStep, BizUnit.LoadGenSteps , Version=3.0.0.0, Culture=neutral, PublicKeyToken=7eb7d82981ae5162">  
        <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
      </TestStep>  
      <!-- Step 9: Delay for 5 secs to allow msgs to start flowing -->  
      <TestStep assemblyPath="" typeName="BizUnit.DelayStep">  
         <Delay>5000</Delay>  
      </TestStep>  
      <!-- Step 10: Wait for Orch Host Queue depth to reach one -->  
      <TestStep assemblyPath="" typeName="BizUnit.PerfMonCounterMonitorStep">  
         <CategoryName>BizTalk:Message Box:Host Counters</CategoryName>  
         <CounterName>Host Queue - Length</CounterName>  
         <InstanceName>BizTalkServerApplication:biztalkmsgboxdb:BizTalkAdmin01</InstanceName>  
         <Server>BizTalkAdmin01</Server>  
         <CounterTargetValue>1</CounterTargetValue>  
      </TestStep>  
      <!-- Step 11: Update test results DB with test stop time -->  
      <TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
         <DelayBeforeExecution>1</DelayBeforeExecution>  
         <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=TestResults;server=BIZTALKADMIN01;Connect Timeout=30</ConnectionString>  
         <SQLQuery>  
            <RawSQLQuery>UPDATE tblPerformanceResults SET EndTime = GetDate() WHERE Test_ID = '{0}'</RawSQLQuery>  
            <SQLQueryParams>  
               <SQLQueryParam takeFromCtx="TestRunName"></SQLQueryParam>  
            </SQLQueryParams>  
         </SQLQuery>  
      </TestStep>  
   </TestExecution>  
  
   <TestCleanup>  
      <!-- Return system to state prior to test -->  
      <!-- Stop perfmon counters -->  
      <TestStep assemblyPath="" typeName="BizUnit.PerfmonCountersStep" failOnError="false">  
         <PerfmonAction>Stop</PerfmonAction>  
         <CounterSetName>PerfGuidePerfmonCounters</CounterSetName>  
      </TestStep>  
   </TestCleanup>  
</TestCase>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13634-229">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13634-229">See Also</span></span>  
 [<span data-ttu-id="13634-230">使用 BizUnit 促進自動化測試</span><span class="sxs-lookup"><span data-stu-id="13634-230">Using BizUnit to Facilitate Automated Testing</span></span>](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)