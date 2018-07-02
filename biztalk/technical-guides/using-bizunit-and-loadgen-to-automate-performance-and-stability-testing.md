---
title: 使用 BizUnit 和 LoadGen 來自動化效能與穩定性測試 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73c2a97a-6256-4010-8374-433017cb15d4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53dde16a21679e7986f3369a825bc4281ed40f37
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981695"
---
# <a name="using-bizunit-and-loadgen-to-automate-performance-and-stability-testing"></a><span data-ttu-id="1151d-102">使用 BizUnit 和 LoadGen 來自動化效能與穩定性測試</span><span class="sxs-lookup"><span data-stu-id="1151d-102">Using BizUnit and LoadGen to Automate Performance and Stability Testing</span></span>
<span data-ttu-id="1151d-103">本主題提供如何使用 BizUnit 中的 Microsoft BizTalk LoadGen 2007 工具，來自動化效能與穩定性測試 BizTalk Server 解決方案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1151d-103">This topic provides information about how to use the Microsoft BizTalk LoadGen 2007 tool with BizUnit to automate performance and stability testing of a BizTalk Server solution.</span></span>  
  
## <a name="biztalk-server-performance-testing-step-by-step"></a><span data-ttu-id="1151d-104">BizTalk Server 效能測試的逐步</span><span class="sxs-lookup"><span data-stu-id="1151d-104">BizTalk Server performance testing, step-by-step</span></span>  
 <span data-ttu-id="1151d-105">如果之前正在調查要如何將 BizTalk Server 效能測試自動化，最好知道哪些步驟通常會執行效能測試中。</span><span class="sxs-lookup"><span data-stu-id="1151d-105">Before investigating how to automate BizTalk Server performance testing, it is useful to know what steps are typically performed in a performance test.</span></span> <span data-ttu-id="1151d-106">代表 「 一般 」 的 BizTalk Server 效能測試程序的下列步驟︰</span><span class="sxs-lookup"><span data-stu-id="1151d-106">The following steps are representative of a “typical” BizTalk Server performance testing process:</span></span>  
  
1. <span data-ttu-id="1151d-107">建立測試結果目錄來儲存結果和資料收集，例如事件記錄檔、 追蹤記錄檔中，效能監視器資料。</span><span class="sxs-lookup"><span data-stu-id="1151d-107">Create a test results directory to store results and data collected, for example, event logs, trace logs, Performance Monitor data.</span></span>  
  
2. <span data-ttu-id="1151d-108">清除事件記錄檔，在測試環境中的所有伺服器上。</span><span class="sxs-lookup"><span data-stu-id="1151d-108">Clear the event logs on all servers within the test environment.</span></span>  
  
3. <span data-ttu-id="1151d-109">停止所有 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1151d-109">Stop all BizTalk host instances.</span></span>  
  
4. <span data-ttu-id="1151d-110">停止任何正在執行外掛式的 BizTalk 主控件，例如 SOAP 和 HTTP 接收配接器處理常式的 IIS 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1151d-110">Stop any IIS instances that are running isolated BizTalk hosts such as the SOAP and HTTP receive adapter handlers.</span></span>  
  
5. <span data-ttu-id="1151d-111">重新啟動所有執行 BizTalk Server 的電腦所使用的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1151d-111">Restart all instances of SQL Server used by the computers running BizTalk Server.</span></span>  
  
6. <span data-ttu-id="1151d-112">清除 MessageBox 資料庫，以確保沒有任何剩餘的資料，從先前的測試回合。</span><span class="sxs-lookup"><span data-stu-id="1151d-112">Clean up the MessageBox database to ensure that there is no leftover data from previous tests runs.</span></span> <span data-ttu-id="1151d-113">這很重要，因為任何剩餘的資料可能會扭曲測試結果。</span><span class="sxs-lookup"><span data-stu-id="1151d-113">This is important because any leftover data could skew test results.</span></span>  
  
7. <span data-ttu-id="1151d-114">啟動 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1151d-114">Start the BizTalk host instances.</span></span>  
  
8. <span data-ttu-id="1151d-115">在測試環境中的所有伺服器上啟動相關的效能監視器計數器。</span><span class="sxs-lookup"><span data-stu-id="1151d-115">Start the relevant Performance Monitor counters on all servers in the test environment.</span></span>  
  
9. <span data-ttu-id="1151d-116">傳送 「 忙於活絡 」 整個系統中的訊息來初始化系統快取。</span><span class="sxs-lookup"><span data-stu-id="1151d-116">Send “priming” messages through the system to initialize the system caches.</span></span>  
  
10. <span data-ttu-id="1151d-117">忙於活絡訊息處理完成之後，追蹤 SQL Server 測試結果資料庫中的測試開始時間。</span><span class="sxs-lookup"><span data-stu-id="1151d-117">After the priming messages have been processed, track the test start time in a SQL Server test results database.</span></span>  
  
11. <span data-ttu-id="1151d-118">啟動所有的 LoadGen 測試代理程式，以開始效能測試。</span><span class="sxs-lookup"><span data-stu-id="1151d-118">Start the performance test by starting all of the LoadGen test agents.</span></span>  
  
12. <span data-ttu-id="1151d-119">等候測試完成，通常這可以有系統地藉由測量效能監視器計數器等主控件佇列長度的值。</span><span class="sxs-lookup"><span data-stu-id="1151d-119">Wait for the test to complete – often this can be done systematically by measuring the value of a Performance Monitor counter such as host queue length.</span></span>  
  
13. <span data-ttu-id="1151d-120">追蹤測試結束時間的 SQL 測試結果資料庫。</span><span class="sxs-lookup"><span data-stu-id="1151d-120">Track test end time in a SQL test results database.</span></span>  
  
14. <span data-ttu-id="1151d-121">在測試環境中的所有伺服器上停止相關的效能監視器計數器。</span><span class="sxs-lookup"><span data-stu-id="1151d-121">Stop the relevant Performance Monitor counters on all servers in the test environment.</span></span>  
  
15. <span data-ttu-id="1151d-122">將測試資料儲存至稍早建立的測試結果目錄中。</span><span class="sxs-lookup"><span data-stu-id="1151d-122">Save the test data to the test results directory that was created earlier.</span></span>  
  
16. <span data-ttu-id="1151d-123">下一步 的測試回合執行任何必要的清除作業。</span><span class="sxs-lookup"><span data-stu-id="1151d-123">Perform any necessary cleanup for the next test run.</span></span>  
  
    <span data-ttu-id="1151d-124">每一個剛剛提到的步驟，可以使用 BizUnit 自動化。</span><span class="sxs-lookup"><span data-stu-id="1151d-124">Each and every one of the steps just listed can be automated using BizUnit.</span></span> <span data-ttu-id="1151d-125">藉由使用 BizUnit 提供的現有測試步驟資產，您可以快速且輕鬆地產生 BizTalk Server 解決方案自動化的效能測試。</span><span class="sxs-lookup"><span data-stu-id="1151d-125">By utilizing the existing test step assets that BizUnit provides, you can quickly and easily generate an automated performance test for a BizTalk Server solution.</span></span> <span data-ttu-id="1151d-126">自動化使用 BizUnit 測試的效能的主要優點是彈性地執行測試整夜 – 這表示在早上，結果會供分析。</span><span class="sxs-lookup"><span data-stu-id="1151d-126">One of the primary benefits of automating performance testing by using BizUnit is the flexibility to run tests overnight – meaning that the results are ready for analysis in the morning.</span></span> <span data-ttu-id="1151d-127">這可大幅減少測試專案小組的效能的負擔。</span><span class="sxs-lookup"><span data-stu-id="1151d-127">This greatly reduces the burden of performance testing on a project team.</span></span>  
  
## <a name="the-microsoft-biztalk-loadgen-2007-tool"></a><span data-ttu-id="1151d-128">Microsoft BizTalk LoadGen 2007 工具</span><span class="sxs-lookup"><span data-stu-id="1151d-128">The Microsoft BizTalk LoadGen 2007 tool</span></span>  
 <span data-ttu-id="1151d-129">BizTalk LoadGen 2007 工具 (LoadGen) 是負載測試由 BizTalk Server 2006 產品小組的壓力與效能測試小組所開發的工具。</span><span class="sxs-lookup"><span data-stu-id="1151d-129">The BizTalk LoadGen 2007 tool (LoadGen) is a load testing tool that was developed by the Stress and Performance Testing team in the BizTalk Server 2006 product group.</span></span> <span data-ttu-id="1151d-130">LoadGen 被設計成快速、 輕鬆且可靠地定義模擬生產層級的訊息磁碟區的負載測試。</span><span class="sxs-lookup"><span data-stu-id="1151d-130">LoadGen was designed to quickly, easily, and reliably define load tests that simulate production level message volumes.</span></span> <span data-ttu-id="1151d-131">LoadGen 是多執行緒、 組態驅動，並支援多個傳輸。</span><span class="sxs-lookup"><span data-stu-id="1151d-131">LoadGen is multi-threaded, configuration-driven, and supports multiple transports.</span></span> <span data-ttu-id="1151d-132">BizTalk 產品團隊使用 LoadGen 每天;因此，您可以放心，此工具是持久，符合的用途，而且能夠模擬各種 BizTalk 案例的高度。</span><span class="sxs-lookup"><span data-stu-id="1151d-132">The BizTalk product group uses LoadGen on a daily basis; therefore you can have a high degree of confidence that the tool is durable, fit for the purpose, and able to simulate a wide variety of BizTalk scenarios.</span></span>  
  
 <span data-ttu-id="1151d-133">LoadGen 採用模組化的設計，其中包含三個層級：**簡報**， **framework**並**元件**。</span><span class="sxs-lookup"><span data-stu-id="1151d-133">LoadGen employs a modular design that consists of three layers: **presentation**, **framework** and **component**.</span></span> <span data-ttu-id="1151d-134">展示層是由命令列的驅動程式，則負責驅動架構所組成。</span><span class="sxs-lookup"><span data-stu-id="1151d-134">The presentation layer consists of a command-line driver, which is responsible for driving the framework.</span></span> <span data-ttu-id="1151d-135">架構圖層會讀取組態檔，然後執行 其中指定的元件。</span><span class="sxs-lookup"><span data-stu-id="1151d-135">The framework layer reads a configuration file and then executes the components specified therein.</span></span> <span data-ttu-id="1151d-136">元件層是由三種類型的元件所組成：**負載產生器**，**訊息建立者**並**節流控制器**。</span><span class="sxs-lookup"><span data-stu-id="1151d-136">The component layer consists of three types of components: **load generators**, **message creators** and **throttle controllers**.</span></span> <span data-ttu-id="1151d-137">每個元件，所以您可以建立您自己，並插入 LoadGen 來解決您案例的需求。</span><span class="sxs-lookup"><span data-stu-id="1151d-137">Each of these components is extensible, so you can create your own and plug them into LoadGen to address the needs of your scenario.</span></span> <span data-ttu-id="1151d-138">因為 LoadGen 由 BizTalk Server 產品小組所開發，您應該會發現的立即可用的元件都滿足大部分的測試需求。</span><span class="sxs-lookup"><span data-stu-id="1151d-138">Because LoadGen was developed by the BizTalk Server product group, you should find that the out-of-the-box components will fulfill most of your load testing requirements.</span></span> <span data-ttu-id="1151d-139">這裡有更詳細地說明每個元件。</span><span class="sxs-lookup"><span data-stu-id="1151d-139">Each of these components is described in greater detail here.</span></span>  
  
- <span data-ttu-id="1151d-140">**負載產生器**負責傳輸透過特定的傳輸訊息。</span><span class="sxs-lookup"><span data-stu-id="1151d-140">**Load generators** are responsible for transmitting messages via a particular transport.</span></span> <span data-ttu-id="1151d-141">負載產生器可供下列傳輸：</span><span class="sxs-lookup"><span data-stu-id="1151d-141">Load generators are provided for the following transports:</span></span>  
  
  -   <span data-ttu-id="1151d-142">檔案</span><span class="sxs-lookup"><span data-stu-id="1151d-142">File</span></span>  
  
  -   <span data-ttu-id="1151d-143">HTTP</span><span class="sxs-lookup"><span data-stu-id="1151d-143">HTTP</span></span>  
  
  -   <span data-ttu-id="1151d-144">MQSeries</span><span class="sxs-lookup"><span data-stu-id="1151d-144">MQSeries</span></span>  
  
  -   <span data-ttu-id="1151d-145">MSMQLarge</span><span class="sxs-lookup"><span data-stu-id="1151d-145">MSMQLarge</span></span>  
  
  -   <span data-ttu-id="1151d-146">MSMQ</span><span class="sxs-lookup"><span data-stu-id="1151d-146">MSMQ</span></span>  
  
  -   <span data-ttu-id="1151d-147">SOAP</span><span class="sxs-lookup"><span data-stu-id="1151d-147">SOAP</span></span>  
  
  -   <span data-ttu-id="1151d-148">Web Services Enhancements (WSE)</span><span class="sxs-lookup"><span data-stu-id="1151d-148">Web Services Enhancements (WSE)</span></span>  
  
  -   <span data-ttu-id="1151d-149">Windows SharePoint Services (WSS)</span><span class="sxs-lookup"><span data-stu-id="1151d-149">Windows SharePoint Services (WSS)</span></span>  
  
  -   <span data-ttu-id="1151d-150">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="1151d-150">Windows Communication Foundation (WCF)</span></span>  
  
- <span data-ttu-id="1151d-151">**訊息建立者**是可以在您需要產生包含唯一的資料的訊息時所使用的選用元件。</span><span class="sxs-lookup"><span data-stu-id="1151d-151">**Message creators** are an optional component that can be used when you need to generate messages that contain unique data.</span></span> <span data-ttu-id="1151d-152">訊息建立者可使用兩種模式的建立;同步和非同步。</span><span class="sxs-lookup"><span data-stu-id="1151d-152">Message creators use one of two modes of creation; synchronous and asynchronous.</span></span> <span data-ttu-id="1151d-153">如果指定的同步訊息建立模式，則 LoadGen 會使用單一執行緒來建立訊息，以確保每個訊息都包含唯一的內容。</span><span class="sxs-lookup"><span data-stu-id="1151d-153">If the synchronous message creation mode is specified, LoadGen uses only a single thread to create messages to ensure that each message contains a unique payload.</span></span> <span data-ttu-id="1151d-154">同步模式可確保每個訊息內的唯一資料，而此模式也會限制延展性。</span><span class="sxs-lookup"><span data-stu-id="1151d-154">While the synchronous mode guarantees unique data within each message, this mode also limits scalability.</span></span> <span data-ttu-id="1151d-155">LoadGen 也會提供使用多個執行緒; 的非同步訊息建立者這可讓 LoadGen，以符合目標訊息速率 （因為它只可以建立更多的執行緒）。</span><span class="sxs-lookup"><span data-stu-id="1151d-155">LoadGen also provides asynchronous message creators that use multiple execution threads; this enables LoadGen to meet the target message rate (because it can simply create more threads).</span></span> <span data-ttu-id="1151d-156">在非同步模式中，訊息建立者可能會設定為隨機修改每個個別訊息的資料。</span><span class="sxs-lookup"><span data-stu-id="1151d-156">In asynchronous mode, the message creator may be configured to randomly modify data for each individual message.</span></span> <span data-ttu-id="1151d-157">不過，因為它會使用多個執行緒，也不保證在測試期間所產生的所有訊息會都包含唯一的內容。</span><span class="sxs-lookup"><span data-stu-id="1151d-157">However, because it uses multiple threads, it does not guarantee that all message generated during the test will contain a unique payload.</span></span>  
  
- <span data-ttu-id="1151d-158">**節流控制器**確保訊息的傳輸以穩定速率，藉由測試執行時，將負載產生器來控管。</span><span class="sxs-lookup"><span data-stu-id="1151d-158">**Throttle controllers** ensure that messages are transmitted at a steady rate by governing the load generators while the test is running.</span></span> <span data-ttu-id="1151d-159">LoadGen 也會公開自訂的節流，可讓您控制的訊息，根據準則包括：</span><span class="sxs-lookup"><span data-stu-id="1151d-159">LoadGen also exposes custom throttling, which enables you to control the flow of messages based on criteria including:</span></span>  
  
  -   <span data-ttu-id="1151d-160">在資料夾中的檔案數目</span><span class="sxs-lookup"><span data-stu-id="1151d-160">Number of files in a folder</span></span>  
  
  -   <span data-ttu-id="1151d-161">資料庫資料表中的資料列數目</span><span class="sxs-lookup"><span data-stu-id="1151d-161">Number of rows in a database table</span></span>  
  
  -   <span data-ttu-id="1151d-162">MSMQ 或 MQSeries 的訊息佇列的深度</span><span class="sxs-lookup"><span data-stu-id="1151d-162">Depth of an MSMQ or MQSeries message queue</span></span>  
  
  <span data-ttu-id="1151d-163">Microsoft [BizTalk LoadGen 2007 工具](http://go.microsoft.com/fwlink/?LinkId=59841)可供下載[ http://go.microsoft.com/fwlink/?LinkId=59841 ](http://go.microsoft.com/fwlink/?LinkId=59841) (http://go.microsoft.com/fwlink/?LinkId=59841)。</span><span class="sxs-lookup"><span data-stu-id="1151d-163">The Microsoft [BizTalk LoadGen 2007 tool](http://go.microsoft.com/fwlink/?LinkId=59841) is available for download at [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841) (http://go.microsoft.com/fwlink/?LinkId=59841).</span></span>  
  
### <a name="sample-loadgen-configuration-file"></a><span data-ttu-id="1151d-164">LoadGen 組態檔範例</span><span class="sxs-lookup"><span data-stu-id="1151d-164">Sample LoadGen configuration file</span></span>  
 <span data-ttu-id="1151d-165">所有的 LoadGen 組態資訊儲存在 xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="1151d-165">All LoadGen configuration information is stored in an xml file.</span></span> <span data-ttu-id="1151d-166">LoadGen 組態檔包含\<CommonSection\> LoadGen 案例中設定所有 LoadGen 工作的預設設定的項目。</span><span class="sxs-lookup"><span data-stu-id="1151d-166">The LoadGen configuration file contains a \<CommonSection\> element that configures the default settings for all LoadGen tasks in the LoadGen scenario.</span></span> <span data-ttu-id="1151d-167">LoadGen 組態檔也可以包含一或多個\<一節\>提供特定的 LoadGen 工作的組態設定的項目。</span><span class="sxs-lookup"><span data-stu-id="1151d-167">The LoadGen configuration file can also contain one or more \<Section\> elements that provide configuration settings for a specific LoadGen task.</span></span> <span data-ttu-id="1151d-168">中的項目\<一節\>項目取代中指定任何預設值\<CommonSection\>項目。</span><span class="sxs-lookup"><span data-stu-id="1151d-168">Entries in a \<Section\> element supersede any default values specified in the \<CommonSection\> element.</span></span>  
  
 <span data-ttu-id="1151d-169">接下來的範例 LoadGen 組態檔是 FileToFileLG.xml 範例組態檔包含 LoadGen 安裝目錄的 \ConfigFiles\ConsoleConfigFiles 子目錄中的稍經修改的版本。</span><span class="sxs-lookup"><span data-stu-id="1151d-169">The sample LoadGen configuration file that follows is a slightly modified version of the FileToFileLG.xml sample configuration file that is included in the \ConfigFiles\ConsoleConfigFiles subdirectory of the LoadGen installation directory.</span></span> <span data-ttu-id="1151d-170">這項測試將傳送 25 的訊息\<LotSizePerInterval\>每隔 200 毫秒\<SleepInterval\>，每個負載產生器的 5 個執行緒\<NumThreadsperSection\>，將會停止負載測試 5000 訊息之後\<NumFiles\>已傳送。</span><span class="sxs-lookup"><span data-stu-id="1151d-170">This test sends 25 messages \<LotSizePerInterval\> every 200 milliseconds \<SleepInterval\>, 5 threads per load generator \<NumThreadsperSection\>and will stop the load test after 5000 messages \<NumFiles\> have been sent.</span></span>  
  
 <span data-ttu-id="1151d-171">中指定的檔案節流控制器\<ThrottleController\>一節。</span><span class="sxs-lookup"><span data-stu-id="1151d-171">The file throttle controller is specified in the \<ThrottleController\> section.</span></span> <span data-ttu-id="1151d-172">值\<ThresholdRange\>設為 1000年-2000，這表示，如果檔案位置 C:\Scenarios\FileToFile\Receive （參數） 小於 1000年，或超過 2000年的檔案，節流控制器將會節流檔案負載視需要產生器和增加/減少。</span><span class="sxs-lookup"><span data-stu-id="1151d-172">The value for \<ThresholdRange\> is set to 1000-2000, which means that if the file location C:\Scenarios\FileToFile\Receive (Parameters) has less than 1000 or more than 2000 files, the throttle controller will throttle the file generator and increase/decrease load as appropriate.</span></span> <span data-ttu-id="1151d-173">中的檔案位置的檔案數目將會檢查每 1000年毫秒\<SleepInterval\>。</span><span class="sxs-lookup"><span data-stu-id="1151d-173">The number of files in the file location will be checked every 1000 milliseconds \<SleepInterval\>.</span></span> <span data-ttu-id="1151d-174">\<FileSection\>項目會定義負載產生器來傳送訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="1151d-174">The \<FileSection\> element defines the properties for the messages to be sent by the load generators.</span></span> <span data-ttu-id="1151d-175">FileToFileLG.xml 檔案\<SrcFilePath\> LoadGen 會複製到 filedrop C:\Scenarios\FileToFile\Receive \<DstFilePath >。</span><span class="sxs-lookup"><span data-stu-id="1151d-175">The FileToFileLG.xml file \<SrcFilePath\> will be copied by LoadGen to the filedrop C:\Scenarios\FileToFile\Receive \<DstFilePath>.</span></span> <span data-ttu-id="1151d-176">因為這是在指定的預設傳輸這裡使用的檔案傳輸\<傳輸名稱\>內的項目\<CommonSection\>項目。</span><span class="sxs-lookup"><span data-stu-id="1151d-176">The file transport is used here because this is the default transport specified in the \<Transport Name\> element within the \<CommonSection\> element.</span></span>  
  
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
  
### <a name="using-bizunit-to-drive-loadgen"></a><span data-ttu-id="1151d-177">使用 BizUnit LoadGen 的磁碟機</span><span class="sxs-lookup"><span data-stu-id="1151d-177">Using BizUnit to drive LoadGen</span></span>  
 <span data-ttu-id="1151d-178">提供 BizUnit **LoadGenExecuteStep**以便自動化的效能與穩定性測試。</span><span class="sxs-lookup"><span data-stu-id="1151d-178">BizUnit provides the **LoadGenExecuteStep** to facilitate automated performance and stability testing.</span></span> <span data-ttu-id="1151d-179">**TestExecution**階段會使用範例 BizUnit 組態檔**LoadGenExecuteStep**下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="1151d-179">The **TestExecution** stage of a sample BizUnit configuration file that uses **LoadGenExecuteStep** is shown in the following code example.</span></span> <span data-ttu-id="1151d-180">請注意，此步驟會接受單一組態參數，也就是 LoadGen 組態檔的位置。</span><span class="sxs-lookup"><span data-stu-id="1151d-180">Note that this step accepts a single configuration parameter, which is the location of the LoadGen configuration file.</span></span>  
  
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
  
 <span data-ttu-id="1151d-181">本主題的其餘部分說明自動化效能測試使用 LoadGen BizUnit 測試案例的組態檔。</span><span class="sxs-lookup"><span data-stu-id="1151d-181">The remainder of this topic describes the configuration file for a BizUnit test case that automates performance testing with LoadGen.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1151d-182">可以使用此組態檔做為範本，可快速整合 BizUnit 和 LoadGen，作為您的效能測試的一部分。</span><span class="sxs-lookup"><span data-stu-id="1151d-182">This configuration file can be used as a template to quickly integrate BizUnit and LoadGen as part of your performance testing.</span></span> <span data-ttu-id="1151d-183">再執行此測試案例，您必須自訂設定檔，為您的環境。</span><span class="sxs-lookup"><span data-stu-id="1151d-183">Before running this test case, you will need to customize the configuration file for your environment.</span></span> <span data-ttu-id="1151d-184">據以表示必須自訂設定檔的區段。</span><span class="sxs-lookup"><span data-stu-id="1151d-184">Sections of the configuration file that must be customized are indicated accordingly.</span></span>  
  
 <span data-ttu-id="1151d-185">一開始，指定的值**testName**適用於 BizTalk 方案的參數。</span><span class="sxs-lookup"><span data-stu-id="1151d-185">To begin with, specify a value for the **testName** parameter that is appropriate for the BizTalk solution.</span></span>  
  
```  
<TestCase testName="Performance-Guide-Sample-Loadgen-Test">  
```  
  
 <span data-ttu-id="1151d-186">然後新增到的內容變數**TestSetup**階段。</span><span class="sxs-lookup"><span data-stu-id="1151d-186">Then add context variables to the **TestSetup** stage.</span></span> <span data-ttu-id="1151d-187">這些內容變數會在整個測試案例的持續時間參考。</span><span class="sxs-lookup"><span data-stu-id="1151d-187">These context variables will be referenced throughout the duration of the test case.</span></span> <span data-ttu-id="1151d-188">若要使用此組態檔，修改指定的值**TestCaseResultsDir** (C:\Dev Work\Perf 指南 Demos\PerfResults\\) 及**機器**(BIZTALKADMIN01)，以符合您環境。</span><span class="sxs-lookup"><span data-stu-id="1151d-188">To use this configuration file, modify the values specified for **TestCaseResultsDir** (C:\Dev Work\Perf Guide Demos\PerfResults\\) and **Machine** (BIZTALKADMIN01) to match your environment.</span></span>  
  
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
  
 <span data-ttu-id="1151d-189">完成之後**TestSetup**階段中，我們輸入**TestExecution**階段。</span><span class="sxs-lookup"><span data-stu-id="1151d-189">After completing the **TestSetup** stage, we enter the **TestExecution** stage.</span></span> <span data-ttu-id="1151d-190">第一步是停止 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1151d-190">The first step is to stop the BizTalk host instances.</span></span> <span data-ttu-id="1151d-191">個別**BizUnit.HostConductorStep**必須新增區段，每個不同的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1151d-191">A separate **BizUnit.HostConductorStep** section must be added for each distinct host instance.</span></span> <span data-ttu-id="1151d-192">如果您在環境中使用此組態檔，您也必須輸入適當的值，如**HostInstanceName**，**伺服器**，**登入**，和**密碼**。</span><span class="sxs-lookup"><span data-stu-id="1151d-192">If you are using this configuration file in your environment, you will also need to enter the appropriate values for **HostInstanceName**, **Server**, **Logon**, and **Password**.</span></span>  
  
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
  
 <span data-ttu-id="1151d-193">停止所有的主控件執行個體之後, 我們清除 BizTalk MessageBox 資料庫，使用 bts_CleanupMsgBox 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1151d-193">After stopping all of the host instances, we clean up the BizTalk MessageBox database using the bts_CleanupMsgBox stored procedure.</span></span> <span data-ttu-id="1151d-194">若要使用此步驟中，您必須修改的值**ConnectionString**以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="1151d-194">To use this step you must modify the value for **ConnectionString** to match your environment.</span></span>  
  
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
  
 <span data-ttu-id="1151d-195">步驟 3 **TestExecution**階段開始的範本檔案中指定的效能監視器 (PerfMon) 計數器。</span><span class="sxs-lookup"><span data-stu-id="1151d-195">Step 3 of the **TestExecution** stage starts Performance Monitor (PerfMon) counters that are specified in a template file.</span></span> <span data-ttu-id="1151d-196">範例範本檔案會列下範例**BizUnit.PerfmonCountersStep**如下。</span><span class="sxs-lookup"><span data-stu-id="1151d-196">A sample template file is listed underneath the sample **BizUnit.PerfmonCountersStep** below.</span></span> <span data-ttu-id="1151d-197">若要使用的範本檔案，您必須修改指定的值**CountersListFilePath**以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="1151d-197">To use the template file, you must modify the value specified for **CountersListFilePath** to match your environment.</span></span> <span data-ttu-id="1151d-198">修改範例效能監視器計數器範本檔，以包含任何您想要監視，或移除任何與您的案例無關的 PerfMon 計數器。</span><span class="sxs-lookup"><span data-stu-id="1151d-198">Modify the sample performance monitor counter template file to include any PerfMon counters that you would like to monitor or remove any that are not relevant to your scenario.</span></span>  
  
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
  
 <span data-ttu-id="1151d-199">**範例效能監視器計數器範本檔案 (Test_06_PerfCounters.txt BizUnit.PerfmonCountersStep 所參考):**</span><span class="sxs-lookup"><span data-stu-id="1151d-199">**Sample Performance Monitor counter template file (Test_06_PerfCounters.txt referenced by the BizUnit.PerfmonCountersStep):**</span></span>  
  
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
  
 <span data-ttu-id="1151d-200">現在，我們會開始 BizTalk Server 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1151d-200">Now we start the BizTalk Server host instances.</span></span> <span data-ttu-id="1151d-201">個別**BizUnit.HostConductorStep**必須新增區段，每個不同的主控件執行個體 （distinct 包含多個主控件執行個體在伺服器之間）。</span><span class="sxs-lookup"><span data-stu-id="1151d-201">A separate **BizUnit.HostConductorStep** section must be added for each distinct host instance (distinct includes multiple instances of a host across servers).</span></span> <span data-ttu-id="1151d-202">如果您在環境中使用此組態檔，您也必須輸入適當的值，如**HostInstanceName**，**伺服器**，**登入**，和**密碼**。</span><span class="sxs-lookup"><span data-stu-id="1151d-202">If you are using this configuration file in your environment, you will also need to enter the appropriate values for **HostInstanceName**, **Server**, **Logon**, and **Password**.</span></span>  
  
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
  
 <span data-ttu-id="1151d-203">步驟 5 」 會裝填"，系統將幾個訊息傳送至 BizTalk Server 中使用**BizUnit.LoadGenExecuteStep**; 的值變更**LoadGenTestConfig**參數，以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="1151d-203">Step 5 “primes” the system by sending a couple of messages to BizTalk Server using **BizUnit.LoadGenExecuteStep**; change the value of the **LoadGenTestConfig** parameter to match your environment.</span></span>  
  
```  
<!-- Step 5: Send Priming messages -->  
<TestStep assemblyPath="" typeName="BizUnit.LoadGenExecuteStep, BizUnit.LoadGenSteps">  
   <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
</TestStep>  
```  
  
 <span data-ttu-id="1151d-204">步驟 6 將寫入記憶體 LoadGen 組態檔，以便它可以再寫入至測試結果資料庫測試完成時。</span><span class="sxs-lookup"><span data-stu-id="1151d-204">Step 6 writes the LoadGen configuration file to memory so that it can then be written to the test results database when the test is complete.</span></span>  
  
```  
  
      <!-- Step 6: Read loadgen file into context variable -->  
<TestStep assemblyPath="" typeName="BizUnit.FileReadAndLoadToContext">  
   <FilePath>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</FilePath>  
   <ContextPropertyName>LoadGenFileContent</ContextPropertyName>  
</TestStep>  
```  
  
 <span data-ttu-id="1151d-205">現在我們可以撰寫測試開始時間到測試結果資料庫。</span><span class="sxs-lookup"><span data-stu-id="1151d-205">Now we write the test start time to a test results database.</span></span> <span data-ttu-id="1151d-206">修改**ConnectionString**並**RawSQLQuery**參數，以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="1151d-206">Modify the **ConnectionString** and **RawSQLQuery** parameters to match your environment.</span></span>  
  
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
  
 <span data-ttu-id="1151d-207">步驟 8 是其中的實際效能測試是使用起始**BizUnit.LoadGenExecuteStep**。</span><span class="sxs-lookup"><span data-stu-id="1151d-207">Step 8 is where the actual performance test is initiated using **BizUnit.LoadGenExecuteStep**.</span></span> <span data-ttu-id="1151d-208">此步驟中步驟 5： 指定使用 LoadGen 相同組態檔，但是您可以指定任何有效 LoadGen 的設定檔以下。</span><span class="sxs-lookup"><span data-stu-id="1151d-208">This step specifies the same LoadGen configuration file that was used in step 5, but you can specify any valid LoadGen configuration file here.</span></span> <span data-ttu-id="1151d-209">**BizUnit.DelayStep**強加 5 秒的延遲，以便透過系統傳送訊息的時間，以便用於步驟 9。</span><span class="sxs-lookup"><span data-stu-id="1151d-209">**BizUnit.DelayStep** is used in step 9 to impose a 5-second delay to allow time for messages to start flowing through the system.</span></span> <span data-ttu-id="1151d-210">使用計算主控件佇列長度**BizUnit.PerMonCounterMonitorStep**。</span><span class="sxs-lookup"><span data-stu-id="1151d-210">Host queue length is calculated using **BizUnit.PerMonCounterMonitorStep**.</span></span> <span data-ttu-id="1151d-211">當此參數會達到 1 所述的步驟 10 中的值時，就會在測試結束。</span><span class="sxs-lookup"><span data-stu-id="1151d-211">When this parameter reaches a value of 1 as specified in step 10, the test is concluded.</span></span> <span data-ttu-id="1151d-212">變更的值**InstanceName**並**Server**參數，以符合您想要監視您的環境中的伺服器與主控件執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="1151d-212">Change the values for the **InstanceName** and **Server** parameters to match the name of the host instance and server that you would like to monitor in your environment.</span></span>  
  
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
  
 <span data-ttu-id="1151d-213">在我們使用在測試結束時**BizUnit.DBExecuteNonQueryStep**更新測試結果資料庫。</span><span class="sxs-lookup"><span data-stu-id="1151d-213">At the conclusion of the test we use **BizUnit.DBExecuteNonQueryStep** to update the test results database.</span></span> <span data-ttu-id="1151d-214">完成此步驟表示測試執行階段的結尾，則會在結尾所示\</TestExecution\>標記。</span><span class="sxs-lookup"><span data-stu-id="1151d-214">Completion of this step signifies the end of the test execution stage, as indicated by the closing \</TestExecution\> tag.</span></span> <span data-ttu-id="1151d-215">同樣地，您必須修改**ConnectionString**並**RawSQLQuery**參數，以符合您的環境。</span><span class="sxs-lookup"><span data-stu-id="1151d-215">Again, you must modify the **ConnectionString** and **RawSQLQuery** parameters to match your environment.</span></span>  
  
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
  
 <span data-ttu-id="1151d-216">時結束執行階段中，我們輸入的測試清除階段。</span><span class="sxs-lookup"><span data-stu-id="1151d-216">Upon concluding the execution stage we enter the test cleanup stage.</span></span> <span data-ttu-id="1151d-217">此階段會使用**BizUnit.PerfmonCountersStep**停止啟動先前 （在步驟 3) 的效能監視器計數器。</span><span class="sxs-lookup"><span data-stu-id="1151d-217">This stage uses **BizUnit.PerfmonCountersStep** to stop the Performance Monitor counters that were started earlier (in Step 3).</span></span>  
  
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
  
 <span data-ttu-id="1151d-218">此範例說明如何結合 BizUnit 使用 LoadGen 來自動化效能測試。</span><span class="sxs-lookup"><span data-stu-id="1151d-218">This example illustrated how BizUnit can be combined with LoadGen to automate performance testing.</span></span> <span data-ttu-id="1151d-219">BizUnit 組態檔所描述的負載測試可以從 Visual Studio 測試工具執行功能測試相同的方式。</span><span class="sxs-lookup"><span data-stu-id="1151d-219">The load test described by the BizUnit configuration file can be executed from Visual Studio’s testing tools in the same manner as the functional testing.</span></span> <span data-ttu-id="1151d-220">採用這個方法可讓您集中管理、 管理及收集的效能測試的資料。</span><span class="sxs-lookup"><span data-stu-id="1151d-220">Adopting this approach enables you to centrally manage, administer, and collect data for your performance testing.</span></span>  
  
 <span data-ttu-id="1151d-221">使用 BizUnit 和 LoadGen 中自動化方法，就很容易就能排程多個測試回合期間發生停機，可以將提供充分的測試結果分析在正常上班時間期間。</span><span class="sxs-lookup"><span data-stu-id="1151d-221">By using BizUnit and LoadGen in an automated approach, it is very easy to schedule multiple test runs to occur during off hours, which will provide ample test results for analysis during normal working hours.</span></span> <span data-ttu-id="1151d-222">時自動化效能測試，請考慮使用 LoadGen，模型不同整個系統的負載，例如您可能想要模擬不同的程度 （75%、 100%及 125%） 的指令碼的預期實際執行的訊息量。</span><span class="sxs-lookup"><span data-stu-id="1151d-222">When automating performance testing, consider using LoadGen scripts that model different loads through the system, for example you may wish to simulate varying degrees (75%, 100% and 125%) of the expected production message volume.</span></span> <span data-ttu-id="1151d-223">執行負載測試時，它是特別重要，若要測試的多載或 「 不正確的 day 」 案例。</span><span class="sxs-lookup"><span data-stu-id="1151d-223">When performing load testing, it is especially important to test the overload or “bad day” scenario.</span></span> <span data-ttu-id="1151d-224">之前將系統放入生產環境中，您應該知道的最大持續輸送量 (MST) 是 BizTalk Server 環境中的每個測試案例。</span><span class="sxs-lookup"><span data-stu-id="1151d-224">Before placing the system into production, you should know what the maximum sustainable throughput (MST) is for each test case in the BizTalk Server environment.</span></span> <span data-ttu-id="1151d-225">如需最大持續性效能的詳細資訊，請參閱[何謂持續性效能？](http://go.microsoft.com/fwlink/?LinkID=132304)</span><span class="sxs-lookup"><span data-stu-id="1151d-225">For more information about maximum sustainable performance, see [What Is Sustainable Performance?](http://go.microsoft.com/fwlink/?LinkID=132304)</span></span> <span data-ttu-id="1151d-226">(http://go.microsoft.com/fwlink/?LinkID=132304) BizTalk Server 2009 文件中。</span><span class="sxs-lookup"><span data-stu-id="1151d-226">(http://go.microsoft.com/fwlink/?LinkID=132304) in the BizTalk Server 2009 documentation.</span></span>  
  
### <a name="the-complete-bizunit-loadgen-sample-configuration-file"></a><span data-ttu-id="1151d-227">完整的 BizUnit LoadGen 範例組態檔</span><span class="sxs-lookup"><span data-stu-id="1151d-227">The complete BizUnit LoadGen sample configuration file</span></span>  
 <span data-ttu-id="1151d-228">下列清單包含稍早提及的 BizUnit 組態檔的整個內容。</span><span class="sxs-lookup"><span data-stu-id="1151d-228">The following list contains the entire contents of the BizUnit configuration file referenced earlier.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1151d-229">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1151d-229">See Also</span></span>  
 [<span data-ttu-id="1151d-230">使用 BizUnit 促進自動化測試</span><span class="sxs-lookup"><span data-stu-id="1151d-230">Using BizUnit to Facilitate Automated Testing</span></span>](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)