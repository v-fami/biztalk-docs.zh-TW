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
# <a name="using-bizunit-and-loadgen-to-automate-performance-and-stability-testing"></a>使用 BizUnit 和 LoadGen 來自動化效能與穩定性測試
本主題提供如何使用 Microsoft BizTalk LoadGen 2007 工具 BizUnit 自動化效能與穩定性測試 BizTalk Server 解決方案的資訊。  
  
## <a name="biztalk-server-performance-testing-step-by-step"></a>BizTalk Server 效能測試，逐步  
 如果之前正在研究如何自動化 BizTalk Server 效能測試，會很有用知道哪些步驟通常在效能測試中執行。 下列步驟表示有 「 一般 」 的 BizTalk Server 效能測試程序：  
  
1.  建立測試結果目錄來儲存結果和資料收集，例如事件記錄檔、 追蹤記錄的效能監視器資料。  
  
2.  清除測試環境內的所有伺服器上的事件日誌。  
  
3.  停止所有 BizTalk 主控件執行個體。  
  
4.  停止任何正在執行外掛式的 BizTalk 主控件，例如 SOAP 和 HTTP 接收配接器處理常式的 IIS 執行個體。  
  
5.  重新啟動所有執行 BizTalk Server 之電腦所使用的 SQL Server 執行個體。  
  
6.  清除 MessageBox 資料庫，以確保沒有任何剩餘的資料，從先前的測試回合。 這是很重要，因為任何剩餘的資料會扭曲測試結果。  
  
7.  啟動 BizTalk 主控件執行個體。  
  
8.  在測試環境中的所有伺服器上啟動相關的效能監視器計數器。  
  
9. 傳送 「 忙於活絡"透過系統中的訊息來初始化系統快取。  
  
10. 忙於活絡訊息處理完成之後，追蹤 SQL Server 測試結果資料庫中的測試開始時間。  
  
11. 啟動所有 LoadGen 測試代理程式的都啟動效能測試。  
  
12. 等候完成測試 – 通常即可做到這有系統地藉由測量例如主控件佇列長度效能監視器計數器的值。  
  
13. 追蹤測試結束時間的 SQL 測試結果資料庫。  
  
14. 在測試環境中的所有伺服器上停止相關的效能監視器計數器。  
  
15. 將測試資料儲存至稍早建立的測試結果目錄。  
  
16. 下一個測試回合執行任何必要的清除作業。  
  
 每一個步驟只會列出可以使用 BizUnit 自動化。 藉由使用 BizUnit 提供的現有測試步驟資產，您可以快速且輕鬆地產生自動化的效能測試 BizTalk Server 解決方案。 若要執行測試過一個晚上 – 這表示結果已準備進行分析，在早上彈性自動化使用 BizUnit 測試的效能的主要優點的其中一個。 這可大幅減少專案小組測試的效能的負擔。  
  
## <a name="the-microsoft-biztalk-loadgen-2007-tool"></a>Microsoft BizTalk LoadGen 2007 工具  
 BizTalk LoadGen 2007 工具 (LoadGen) 是負載測試由 BizTalk Server 2006 產品群組中壓力和效能測試的小組開發的工具。 LoadGen 被設計成快速、 輕鬆地且可靠地定義模擬實際執行等級的訊息的磁碟區的負載測試。 LoadGen 是多執行緒、 組態導向，並支援多個傳輸。 BizTalk 產品團隊使用 LoadGen 採每日。因此，您可以有較高程度的信心，此工具是持久，適合用途，以及可以模擬各種 BizTalk 案例。  
  
 LoadGen 採用模組化的設計，其中包含三個層級：**簡報**， **framework**和**元件**。 展示層包含命令列的驅動程式，負責驅動的架構。 架構圖層會讀取組態檔，然後執行 其中指定的元件。 元件圖層包含三種類型的元件：**負載產生器**，**訊息建立者**和**節流控制器**。 每個元件，所以您可以建立您自己，並插入 LoadGen 解決您的案例的需求。 因為 LoadGen 由 BizTalk Server 產品小組所開發，您應該會發現的方塊外元件都滿足大部分的測試需求。 這裡會更詳細地說明每個元件。  
  
-   **負載產生器**負責傳輸透過特定傳輸的訊息。 負載產生器可供下列傳輸：  
  
    -   檔案  
  
    -   HTTP  
  
    -   MQSeries  
  
    -   MSMQLarge  
  
    -   MSMQ  
  
    -   SOAP  
  
    -   Web Services Enhancements (WSE)  
  
    -   Windows SharePoint Services (WSS)  
  
    -   Windows Communication Foundation (WCF)  
  
-   **訊息建立者**是您需要產生訊息包含唯一的資料時可用的選用元件。 訊息的建立者使用兩種模式的建立。同步和非同步。 如果指定的同步訊息建立模式，則 LoadGen 會使用單一執行緒來建立訊息，以確保每個訊息都包含唯一的內容。 同步模式可確保每個訊息內的唯一資料，而這個模式也會限制可調適性。 LoadGen 也提供使用多個執行緒; 的非同步訊息建立者這可讓 LoadGen，以符合目標訊息速率 （因為它只可以建立更多的執行緒）。 在非同步模式中，訊息建立者可能會設定為隨機修改每個個別訊息的資料。 不過，它會使用多個執行緒，因為它並不保證在測試期間所產生的所有訊息會都包含唯一的內容。  
  
-   **節流控制器**確保訊息的傳輸速率穩定所控管負載產生器，當測試正在執行。 LoadGen 也會公開自訂節流，可讓您控制流程的訊息，根據準則包括：  
  
    -   在資料夾中的檔案數目  
  
    -   資料庫資料表中的資料列數目  
  
    -   MSMQ 或 MQSeries 的訊息佇列的深度  
  
 Microsoft [BizTalk LoadGen 2007 工具](http://go.microsoft.com/fwlink/?LinkId=59841)適用於下載[http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841) (http://go.microsoft.com/fwlink/?LinkId=59841)。  
  
### <a name="sample-loadgen-configuration-file"></a>LoadGen 組態檔範例  
 LoadGen 的所有組態資訊都儲存在 xml 檔案。 LoadGen 組態檔包含\<CommonSection > 設定的預設設定來執行所有 LoadGen 工作 LoadGen 案例中的項目。 LoadGen 組態檔也可以包含一或多個\<區段 > 項目，提供特定的 LoadGen 工作的組態設定。 中的項目\<區段 > 項目中指定任何預設值會取代\<CommonSection > 項目。  
  
 遵循範例 LoadGen 組態檔是稍微修改的 FileToFileLG.xml 範例組態檔包含 \ConfigFiles\ConsoleConfigFiles 子目錄 LoadGen 安裝目錄中的版本。 這項測試將 25 的訊息傳送\<LotSizePerInterval > 每隔 200 毫秒\<SleepInterval >，每個負載產生器的 5 個執行緒\<NumThreadsperSection > 5000 訊息後將會停止在負載測試和\<NumFiles > 已傳送。  
  
 中指定檔案節流控制器\<ThrottleController > 一節。 值\<ThresholdRange > 設為 1000年-2000，這表示，如果檔案位置 （參數） C:\Scenarios\FileToFile\Receive 少於 1000年，或是超過 2000年檔案，節流控制器將會啟用節流設定檔產生器和視需要增加/減少負載。 中的檔案位置的檔案數目將會檢查每 1000年毫秒\<SleepInterval >。 \<FileSection > 元素可定義負載產生器來傳送訊息的屬性。 FileToFileLG.xml 檔案\<SrcFilePath > 將會 LoadGen 複製到 filedrop C:\Scenarios\FileToFile\Receive \<DstFilePath >。 因為這是預設的傳輸中指定這裡使用的檔案傳輸\<傳輸名稱 > 內的項目\<CommonSection > 項目。  
  
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
  
### <a name="using-bizunit-to-drive-loadgen"></a>使用磁碟機 LoadGen BizUnit  
 BizUnit 提供**LoadGenExecuteStep** ，以協助自動化的效能與穩定性測試。 **TestExecution**範例 BizUnit 組態檔會使用階段**LoadGenExecuteStep**下列程式碼範例所示。 請注意，這個步驟會接受單一組態參數，而是 LoadGen 組態檔的位置。  
  
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
  
 本主題的其餘部分描述的組態檔會自動執行效能測試使用 LoadGen BizUnit 測試案例。  
  
> [!NOTE]  
>  此組態檔可以用做為範本，來快速將 BizUnit 和 LoadGen 一部分效能測試的整合。 然後再執行此測試案例，您必須自訂設定檔，為您的環境。 也會據以指出必須自訂組態檔的區段。  
  
 一開始指定的值**testName**適用於 BizTalk 解決方案的參數。  
  
```  
<TestCase testName="Performance-Guide-Sample-Loadgen-Test">  
```  
  
 然後將內容的變數加入**TestSetup**階段。 測試案例的期間，將會參考這些內容變數。 若要使用此組態檔，修改為指定的值**TestCaseResultsDir** (C:\Dev Work\Perf 指南 Demos\PerfResults\\) 和**機器**(BIZTALKADMIN01)，以符合您環境。  
  
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
  
 完成之後**TestSetup**階段中，我們輸入**TestExecution**階段。 第一個步驟是停止 BizTalk 主控件執行個體。 個別**BizUnit.HostConductorStep**區段必須加入每個不同的主控件執行個體。 如果您在環境中使用此組態檔，您也必須輸入適當的值**HostInstanceName**，**伺服器**，**登入**，和**密碼**。  
  
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
  
 停止所有主控件執行個體之後, 我們清除 BizTalk MessageBox 資料庫，使用 bts_CleanupMsgBox 預存程序。 若要使用此步驟中，您必須修改的值**ConnectionString**以符合您的環境。  
  
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
  
 步驟 3 **TestExecution**階段開始範本檔案中指定的效能監視器 (PerfMon) 計數器。 範例範本檔案會列出下方範例**BizUnit.PerfmonCountersStep**下方。 若要使用的範本檔案，您必須修改指定的值**CountersListFilePath**以符合您的環境。 修改範例效能監視器計數器範本檔案，包括任何您想要監視，或移除任何不是適用於您案例的效能計數器。  
  
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
  
 **範例效能監視器計數器範本檔 (Test_06_PerfCounters.txt BizUnit.PerfmonCountersStep 所參考):**  
  
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
  
 現在，我們會開始 BizTalk Server 主控件執行個體。 個別**BizUnit.HostConductorStep**區段必須加入每個不同的主控件執行個體 （distinct 包含多個主控件執行個體跨伺服器）。 如果您在環境中使用此組態檔，您也必須輸入適當的值**HostInstanceName**，**伺服器**，**登入**，和**密碼**。  
  
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
  
 步驟 5 」 primes"系統傳送至 BizTalk Server 使用的幾個訊息**BizUnit.LoadGenExecuteStep**; 的值變更**LoadGenTestConfig**參數，以符合您的環境。  
  
```  
<!-- Step 5: Send Priming messages -->  
<TestStep assemblyPath="" typeName="BizUnit.LoadGenExecuteStep, BizUnit.LoadGenSteps">  
   <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
</TestStep>  
```  
  
 步驟 6 LoadGen 組態檔案寫入記憶體，讓它可以再寫入至測試結果資料庫測試完成時。  
  
```  
  
      <!-- Step 6: Read loadgen file into context variable -->  
<TestStep assemblyPath="" typeName="BizUnit.FileReadAndLoadToContext">  
   <FilePath>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</FilePath>  
   <ContextPropertyName>LoadGenFileContent</ContextPropertyName>  
</TestStep>  
```  
  
 現在我們可以撰寫測試開始時間到測試結果資料庫。 修改**ConnectionString**和**RawSQLQuery**參數以符合您的環境。  
  
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
  
 步驟 8 情況是在實際的效能測試使用起始**BizUnit.LoadGenExecuteStep**。 此步驟在步驟 5 中指定相同的 LoadGen 組態檔所使用，但是您可以指定任何有效 LoadGen 的設定檔以下。 **BizUnit.DelayStep**在步驟 9 中用來強制執行 5 秒的延遲，等待啟動流經系統的訊息。 主控件佇列長度使用計算**BizUnit.PerMonCounterMonitorStep**。 當此參數達到 1 步驟 10 中所指定的值時，會結束測試。 變更的值**InstanceName**和**伺服器**參數以符合您想要監視您的環境中的伺服器與主控件執行個體的名稱。  
  
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
  
 在測試結束時，我們使用**BizUnit.DBExecuteNonQueryStep**更新測試結果資料庫。 完成此步驟結尾所示，表示測試執行階段中，結尾\</TestExecution > 標記。 同樣地，您必須修改**ConnectionString**和**RawSQLQuery**參數以符合您的環境。  
  
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
  
 完成的執行階段時，我們會輸入測試清除階段。 這個階段會使用**BizUnit.PerfmonCountersStep**停止稍早 （步驟 3) 中啟動效能監視器計數器。  
  
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
  
 此範例中所述 BizUnit 如何結合 LoadGen 自動化效能測試。 BizUnit 組態檔所描述的負載測試可以從 Visual Studio 測試工具執行功能測試相同的方式。 採用這個方法可讓您集中管理、 管理及收集的效能測試資料。  
  
 使用 BizUnit LoadGen 中與自動化方法，是很容易就能排程在離峰時間，將會提供很大的測試結果分析在正常上班時間發生的多個測試回合。 當將自動化測試的效能，請考慮使用 LoadGen，模型不同整個系統的負載，例如您可能想要模擬不同的程度 （75%、 100%和 125%） 的指令碼的預期實際執行的訊息量。 在執行負載測試時，它是要測試的多載或 [錯誤天] 案例特別重要。 先將系統放入實際執行環境中，您應該知道最大持續輸送量 (MST) 是 BizTalk Server 環境中的每個測試案例。 如需最大持續性效能的詳細資訊，請參閱[何謂持續性效能？](http://go.microsoft.com/fwlink/?LinkID=132304) (http://go.microsoft.com/fwlink/?LinkID=132304) 中的 BizTalk Server 2009 文件。  
  
### <a name="the-complete-bizunit-loadgen-sample-configuration-file"></a>完整的 BizUnit LoadGen 範例組態檔  
 下列清單包含先前已參考 BizUnit 組態檔的整個內容。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [使用 BizUnit 促進自動化測試](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)