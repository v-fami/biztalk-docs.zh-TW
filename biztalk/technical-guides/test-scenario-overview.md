---
title: "測試案例概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cde553ad-2540-40d9-a74b-928fee873c31
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53e20b7d94e44006df1042c9ca202e296508a5d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="test-scenario-overview"></a>測試案例概觀
本主題提供的測試應用程式的概觀測試使用，方法和清單的描述在負載測試期間擷取關鍵效能指標 (Kpi)。  
  
## <a name="test-application"></a>測試應用程式  
 同步要求-回應應用程式用來比較效能[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]HYPER-V 上執行[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]在實體硬體上執行。 此應用程式用來說明效能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]低延遲的已調整的解決方案。 低度延遲訊息很重要，例如線上銀行用戶端傳送要求，並在非常短的間隔內所預期的回應訊息的特定情況下 (例如\<3 秒)。  
  
 下圖說明使用的高階架構。 Visual Studio Team System (VSTS) 2008年測試載入代理程式叫用自訂測試類別，用來產生負載的 WCF 傳輸[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已公開應用程式在此案例中，從 Wcf-basichttp 傳送要求-回應接收位置。 VSTS 2008 Test Load Agent 已做為測試用戶端因為它提供的絕佳彈性，包括設定的訊息數目的功能，同時執行緒總數，傳送，而且睡眠之間的間隔要求傳送。  
  
 搭配模擬真實世界的負載模式，可以執行數個 VSTS 2008 Test Load Agent 電腦。 這些測試中，單一 VSTS 2008 測試負載代理程式控制器電腦也執行 BizUnit 3.0 所驅動 VSTS 2008 Test Load Agent 電腦。 如此一來，一致性負載已傳送至實體和虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。 如需使用 VSTS 2008 Test 版產生模擬的負載以便進行測試的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkID=132311](http://go.microsoft.com/fwlink/?LinkID=132311)。  
  
 ![應用程式架構](../technical-guides/media/testapplicationarchitecture.gif "TestApplicationArchitecture")  
測試應用程式架構  
  
1.  Wcf-basichttp 或 WCF 自訂要求-回應接收位置收到新 CalculatorRequest 從 Test Load Agent 電腦。  
  
2.  XML 解譯器元件會升級方法內的項目 CalculatorRequest xml 文件。 訊息代理程式提交至 MessageBox 資料庫 (BizTalkMsgBoxDb) 內送訊息。  
  
3.  傳入的要求會啟動 LogicalPortsOrchestration 的新執行個體。 此協調流程會使用直接繫結連接埠來接收方法升級屬性 CalculatorRequest 訊息 ="LogicalPortsOrchestration"。  
  
4.  LogicalPortsOrchestration 可擷取作業會使用迴圈，每個項目叫用下游計算機 WCF web 服務使用的邏輯請求-回應連接埠。 計算機 WCF web 服務的要求訊息是使用協助程式元件所建立並發佈到 MessageBox。  
  
5.  要求訊息是由 Wcf-basichttp 傳送埠取用。  
  
6.  Wcf-basichttp 傳送埠會叫用一種方法 （新增、 減、 乘、 除） 計算機 WCF web 服務所公開。  
  
7.  計算機 WCF web 服務傳回回應訊息。  
  
8.  回應訊息會發佈到 MessageBox。  
  
9. 回應訊息傳回給呼叫者 LogicalPortsOrchestration。 協調流程會針對輸入 CalculatorRequest xml 文件中的每個作業重複此模式。  
  
10. LogicalPortsOrchestration 將 CalculatorResponse 訊息發佈到 MessageBox。  
  
11. 要求-回應 Wcf-basichttp 接收位置擷取回應訊息。  
  
12. 回應訊息傳回至負載測試代理程式電腦。  
  
 在負載測試期間使用的協調流程的螢幕擷取畫面所示：  
  
> [!NOTE]  
>  為了說明起見，如下所示的協調流程是實際上在負載測試期間使用的協調流程的簡化的版本。 在負載測試期間使用的協調流程包含多個領域，錯誤處理邏輯，與其他連接埠類型。  
  
 ![測試應用程式的協調流程](../technical-guides/media/logicalportsorchestration.gif "LogicalPortsOrchestration")  
測試應用程式協調流程  
  
## <a name="testing-methodology"></a>測試方法  
 效能測試牽涉到許多工作，以手動方式執行，如果是重複性的 monotonous，又容易出錯。 若要提升測試效率，並提供測試回合之間的一致性[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]Team System (VSTS) 測試版使用 BizUnit 3.0 用來自動化測試的程序期間所需的工作。 VSTS 2008 Test Load Agent 電腦做為測試用戶端用來產生訊息負載，會根據系統和上執行以改善一致性每項測試皆已使用相同的訊息類型。 此程序之後每個測試回合提供一致的資料集。 如需 BizUnit 3.0 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkID=85168](http://go.microsoft.com/fwlink/?LinkID=85168)。 如需有關[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]Team System Test 版，請參閱[http://go.microsoft.com/fwlink/?LinkID=141387](http://go.microsoft.com/fwlink/?LinkID=141387)。  
  
 已自動化下列步驟：  
  
-   停止 BizTalk 主控件。  
  
-   清除測試目錄。  
  
-   重新啟動 IIS。  
  
-   清除[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Messagebox 資料庫。  
  
-   重新啟動 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  
  
-   清除事件記錄檔。  
  
-   建立儲存相關聯的效能度量和記錄檔的每次執行的測試結果資料夾。  
  
-   啟動 BizTalk 主控件。  
  
-   載入效能監視器計數器。  
  
-   準備使用的小型負載 BizTalk 環境。  
  
-   代表執行透過傳送。  
  
-   效能記錄檔寫入結果資料夾中。  
  
-   收集應用程式記錄檔，並寫入結果資料夾中的.csv 檔案。  
  
-   針對收集到的效能記錄檔，以產生統計資料、 圖表和報表執行的效能分析的記錄檔 (PAL) 工具、 重新記錄和記錄檔剖析器工具。 如需有關 PAL、 重新記錄，以及記錄檔剖析器的詳細資訊，請參閱[附錄 d： 工具，以測量效能](../technical-guides/appendix-d-tools-for-measuring-performance.md)。  
  
> [!NOTE]  
>  已停用所有追蹤，並在測試期間的 BizTalk Server SQL Server Agent 作業已停都用。  
  
 若要確定這個實驗室的結果都已提供的效能比較[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在實體和 HYPER-V 環境中，效能度量和記錄檔中所收集的每個測試回合的集中位置。  
  
 測試用戶端用來建立每個測試回合的唯一結果目錄。 這個目錄包含所有效能記錄檔，事件記錄檔和相關聯的測試所需的資料。 這種方法提供必要回溯分析先前的測試執行時所需的資訊。 在每個測試結束時，原始資料被編譯成一組一致的結果與關鍵效能指標 (Kpi)。 實體和虛擬機器提供的不同測試回合和不同環境之間所需的比較點收集一致的結果設定。 包含收集的資料：  
  
-   **環境 –**記錄何種環境測試正在執行對實體硬體上的 BizTalk Server 或 HYPER-V 上的 BizTalk Server。  
  
-   **測試回合數 –**來唯一識別每個測試回合  
  
-   **測試案例 –**記錄在測試期間使用的 BizTalk Server 解決方案的架構。 （例如具有邏輯連接埠與協調流程使用內嵌的協調流程傳送）  
  
-   **日期 –**執行記錄的日期和時間，測試  
  
-   **時間已啟動 –**報告的第一個 VSTS 負載測試代理程式起始  
  
-   **時間已停止 –**完成最後一個 VSTS 負載測試代理程式報告  
  
-   **測試持續時間，以分鐘為單位 –**記錄的測試持續期間。  
  
-   **總計-傳送的郵件數**記錄從負載代理程式的電腦傳送至 BizTalk Server 的電腦在測試期間的訊息總數。  
  
-   **每秒 – 傳送的郵件數**來記錄每秒從負載代理程式電腦的 BizTalk Server 電腦測試期間傳送的訊息。  
  
-   **平均用戶端延遲 –**記錄的平均測試載入代理程式用戶端起始的要求和負載測試期間，從 BizTalk Server 的電腦收到的回應之間的時間量。  
  
-   **要求-回應持續時間平均 （毫秒） –**所報告**BizTalk： 傳訊 Latency\Request 回應延遲 （秒）** BizTalkServerIsolatedHost 效能監視器計數器  
  
    > [!NOTE]  
    >  使用其中多個虛擬化的 BizTalk 主控件執行這些計數器的平均值計算從記錄檔。  
  
-   **協調流程已完成，每秒 –**所報告**XLANG/s 協調流程 (BizTalkServerApplication) \Orchestrations 每秒完成**效能監視器計數器。 此計數器提供良好的輸送量的測量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案。  
  
-   **訊息處理的 % \< 3 秒數 –**記錄在測試期間 3 秒內已處理的訊息總數。  
  
 VSTS 2008 負載測試用來產生整個所有測試的一致性負載。 下列測試回合設定，並調整每個測試的負載設定檔在測試期間已修改的負載模式：  
  
-   **測試回合設定**  
  
     下列測試回合設定已修改視正在執行測試而定：  
  
    -   **執行持續時間 –**指定多久執行測試。  
  
     ![測試回合的設定](../technical-guides/media/wcfloadtestrunsettings.gif "WCFLoadTestRunSettings")  
測試回合設定  
  
-   **測試模式設定**  
  
     下列測試模式設定已修改視正在執行測試而定：  
  
    1.  **模式 –**指定負載測試期間調整模擬的使用者負載的方式。 負載模式是**常數**，**步驟**，或**目標**基礎。 所有負載測試執行都是常數或步驟。  
  
        > [!NOTE]  
        >  本指南中使用 執行所有測試**常數**負載模式或**步驟**負載模式。 常數負載模式和步驟負載模式提供下列功能：  
        >   
        >  -   **常數負載模式 –**負載模式是相同的測試持續期間、 模擬使用者數目開始預先定義的層級，且不會變更。  
        > -   **步驟負載模式 –**測試回合期間增加負載模式時，模擬使用者數目在預先定義的層級啟動，而且根據預先定義的數量預先定義的間隔遞增測試的持續時間。  
  
    2.  **常數使用者計數 （常數負載模式）-**正在產生負載的 Visual Studio 負載測試專案的 app.config 檔案中指定的端點位址的虛擬使用者數目。 使用負載測試的負載模式設定中指定此值。  
  
    3.  **初始使用者計數 （步驟負載模式）-**正在產生負載的步驟負載模式測試的開頭指定的端點位址的虛擬使用者數目。 使用負載測試的負載模式設定中指定此值。  
  
    4.  **最大使用者計數 （步驟負載模式）-**正在產生負載的測試步驟負載模式的結尾指定的端點位址的虛擬使用者數目。 使用負載測試的負載模式設定中指定此值。  
  
    5.  **逐步執行持續期間 （步驟負載模式）-**虛擬使用者正在產生負載的負載測試步驟指定的端點位址的秒數。  
  
    6.  **逐步執行使用者計數 （步驟負載模式）-**增加每個步驟，使用步驟負載模式時的虛擬使用者數目。  
  
     ![測試模式設定](../technical-guides/media/wcfloadtestpatternsettings.gif "WCFLoadTestPatternSettings")  
測試模式設定  
  
 如需有關使用負載測試中[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]，請參閱主題**使用負載測試**中[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]Team System 文件，網址[http://go.microsoft.com/fwlink/?LinkId=141486](http://go.microsoft.com/fwlink/?LinkId=141486)。  
  
## <a name="key-performance-indicators-measured-during-testing"></a>在測試期間所測量的關鍵效能指標  
 為所有的測試回合的關鍵效能指標 (KPI) 中已擷取下列效能監視器計數器：  
  
> [!NOTE]  
>  如需評估與效能監視器計數器的效能的詳細資訊，請參閱[檢查清單： 在 HYPER-V 上的測量效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。  
  
 **BizTalk Server KPI**  
  
-   **每秒 – 處理的文件**所測量**BizTalk： 傳訊/文件 processed/Sec**計數器。  
  
-   **延遲 –**測量 VSTS 2008 負載測試控制器所傳回。  
  
 **SQL Server KPI**  
  
-   **SQL 伺服器處理器使用率 –**所測量**SQL\Processor(Total)\\%Processor Time**計數器。 此計數器會測量的 CPU 使用率[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]處理[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
-   **Transact SQL 命令的處理效能 –**所測量**\SQL Server:SQL Statistics\Batch Requests/sec**計數器。 此計數器會測量每秒接收的 TRANSACT-SQL 命令批次數目。 此計數器可用來測量輸送量上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
 **KPI 的網路功能**  
  
-   **BizTalk Server 網路輸送量 –**所測量**\Network 介面 (\*) \Bytes Total/sec**上的效能監視器計數器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。  
  
-   **SQL Server 網路輸送量 –**所測量**SQL Network Interface\Bytes Total/sec （平均）** VSTS 2008 負載測試控制器所傳回。  
  
 **記憶體 KPI**  
  
-   **可用的記憶體-**所測量**\Memory\Available Mbytes**計數器的各種案例。  
  
## <a name="physical-infrastructure-specifics"></a>實體基礎結構細節  
 每個已安裝的伺服器已調整的下列設定。  
  
 **所有伺服器：**  
  
-   設定分頁檔已配置的實體記憶體數量 1.5 倍。 分頁檔已設定為固定的大小，方法是確保 初始大小和最大值以 mb 為單位的相同。  
  
-   進階的 [系統內容] 畫面中選取 「 調整成最佳效能 」 效能選項。  
  
-   它已確認系統已調整為不同的系統屬性的 [效能選項] 區段中的背景服務的最佳效能。  
  
-   [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]已安裝做為客體作業系統上的每部虛擬機器。  
  
-   若要安裝最新的安全性更新的所有伺服器上成功執行 Windows Update。  
  
 **針對 SQL Server:**  
  
-   [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]依照安裝指南位於已安裝[http://go.microsoft.com/fwlink/?LinkId=141021](http://go.microsoft.com/fwlink/?LinkId=141021)。  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]使用具有 SAN Lun 設定根據下表。 資料庫和記錄檔已分門別類 Lun，如下所示，以減少可能的磁碟 I/O 競爭問題：  
  
    -   Data_Sys 磁碟區已用來儲存所有的資料庫檔案 （包括系統和 BizTalk 資料庫），但不含 MessageBox 和 TempDb 資料庫。  
  
    -   Log_Sys 磁碟區已用來儲存所有記錄檔 (包括系統和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫) 除外，MessageBox 和 TempDb 資料庫。  
  
    -   Data_TempDb 磁碟區已用來儲存的 TempDb 資料庫檔案。  
  
    -   Logs_TempDb 磁碟區已用來儲存 TempDb 記錄檔。  
  
    -   MessageBox 資料庫檔案儲存在 Data_BtsMsgBox 磁碟區，並且 Log_BtsMsgBox 磁碟區上儲存記錄檔。  
  
-   此外，不同的 LUN 提供 MSDTC 記錄檔。 高輸送量 BizTalk 在系統上，MSDTC 記錄檔活動可能會導致 I/O 瓶頸，如果讓它保持在相同的實體磁碟機做為作業系統。  
  
    |磁碟區名稱|檔案|LUN 大小 GB|裝載磁碟分割大小 GB|叢集大小|  
    |-----------------|-----------|-----------------|----------------------------|------------------|  
    |Data_Sys|MASTER 和 MSDB 資料檔案|10|10|64 KB|  
    |Logs_Sys|MASTER 和 MSDB 記錄檔|10|10|64 KB|  
    |Data_TempDb|TempDB 資料檔案|50|50|64 KB|  
    |Logs_TempDb|TempDB 記錄檔|50|50|64 KB|  
    |Data_BtsMsgBox|BizTalkMsgBoxDb 資料檔案|300|100|64 KB|  
    |Logs_BtsMsgBox|BizTalkMsgBoxDb 記錄檔|100|100|64 KB|  
    |Data_BAMPrimaryImport|BAMPrimaryImport 資料檔案|10|10|64 KB|  
    |Logs_BAMPrimaryImport|BAMPrimaryImport 的記錄檔|10|10|64 KB|  
    |Data_BizTalkDatabases|其他的 BizTalk 資料庫資料檔案|20|20|64 KB|  
    |Logs_BizTalkDatabases|其他的 BizTalk 資料庫記錄檔|20|20|64 KB|  
    |不適用|MSDTC 記錄檔|5|5|不適用|  
  
-   [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]依照安裝指南 》，網址安裝[http://go.microsoft.com/fwlink/?LinkId=128383](http://go.microsoft.com/fwlink/?LinkId=128383)。  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Best Practices Analyzer (BPA) 工具用來執行平台驗證，一旦已設定組態系統。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BPA 位於[http://go.microsoft.com/fwlink/?LinkId=67150](http://go.microsoft.com/fwlink/?LinkId=67150)。  
  
## <a name="virtualization-specifics"></a>虛擬化的詳細資訊  
 單一 50 GB 的固定 VHD 已用來裝載每個 HYPER-V 虛擬機器的作業系統。  
  
 固定的 Vhd 已使用而不是動態調整大小的 Vhd，因為它們立即配置最大儲存體的 VHD，其裝載所在的磁碟機上的檔案。 這會減少發生實體磁碟機上它裝載於何處，進而改善磁碟 I/O 效能的 VHD 檔案的片段。  
  
 設定專用虛擬機器、 安裝[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]單一 VHD 上執行 64 位元版本。 一旦所有適當的更新已安裝基底的虛擬機器已建立映像使用 sysprep 安裝公用程式與[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，%WINDIR%\system32\sysprep 目錄中。  
  
 此基底 VHD 然後複製並用於所有已部署在環境的 HYPER-V 虛擬機器做為基礎。 若要重設系統安全性識別碼，才能進行任何基底 VHD 映像上執行 Sysprep[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]二進位檔已部署至系統。  
  
> [!NOTE]  
>  執行 Sysprep[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]已安裝並設定在伺服器即可透過 Sysprep 回應檔案使用，以及指令碼提供[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。 這些範例指令碼專為搭配[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]安裝在 32 位元和 64 位元版本[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]只。 如需詳細資訊，請參閱[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]線上文件。  
  
 Windows 自動安裝參照位於[http://go.microsoft.com/fwlink/?LinkId=142364](http://go.microsoft.com/fwlink/?LinkId=142364)。  
  
## <a name="see-also"></a>另請參閱  
 [附錄 c: BizTalk Server 和 SQL Server HYPER-V 可支援性](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md)