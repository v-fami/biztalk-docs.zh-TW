---
title: 測試案例概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cde553ad-2540-40d9-a74b-928fee873c31
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c30bf4102da74869e596af32f8c9361fc796ce7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997687"
---
# <a name="test-scenario-overview"></a>測試案例概觀
本主題提供的測試應用程式的概觀描述的測試方法，並列出在負載測試期間擷取關鍵效能指標 (Kpi)。  

## <a name="test-application"></a>測試應用程式  
 同步要求-回應應用程式用來比較的實體硬體上執行的 BizTalk Server HYPER-V 上所執行的 BizTalk Server 的效能。 此應用程式用來說明效能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]低延遲的已調整的解決方案。 低延遲通訊是很重要的特定案例，例如線上銀行的用戶端傳送要求，並在非常短的間隔 （例如 < 3 秒） 內預期的回應訊息。  

 下圖說明使用的高階架構。 Visual Studio Team System (VSTS) 2008 Test Load Agent 叫用自訂的測試類別，來產生負載與針對 WCF 傳輸[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已公開應用程式在此案例中，從 Wcf-basichttp 傳送要求-回應接收位置。 VSTS 2008 Test Load Agent 已作為測試用戶端，因為它提供絕佳的彈性，包括設定的訊息數目的功能，同時執行緒總數，傳送和要求之間的睡眠間隔傳送。  

 數個 VSTS 2008 Test Load Agent 電腦可以執行以模擬真實世界的負載模式使用串聯方式。 針對這些測試，單一的 VSTS 2008 Test Load Agent Controller 電腦也執行 BizUnit 3.0 是基於 VSTS 2008 Test Load Agent 電腦。 如此一來，一致的負載已傳送至實體和虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。 如需使用 VSTS 2008 Test Edition 來產生模擬的負載以便進行測試的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkID=132311 ](http://go.microsoft.com/fwlink/?LinkID=132311)。  

 ![應用程式架構](../technical-guides/media/testapplicationarchitecture.gif "TestApplicationArchitecture")  
測試應用程式架構  

1. Wcf-basichttp 或 WCF 自訂要求-回應接收位置收到新 CalculatorRequest 從 Test Load Agent 電腦。  

2. XML 解譯器元件會升級 CalculatorRequest xml 文件內的方法項目。 訊息代理程式會提交至 MessageBox 資料庫 (BizTalkMsgBoxDb) 內送訊息。  

3. 傳入的要求會啟動 LogicalPortsOrchestration 的新執行個體。 此協調流程會使用直接繫結連接埠來接收方法升級屬性 CalculatorRequest 訊息 = 「 LogicalPortsOrchestration"。  

4. LogicalPortsOrchestration 擷取作業會使用迴圈，並針對每個項目叫用下游計算機 WCF web 服務使用的邏輯請求-回應連接埠。 計算機 WCF web 服務的要求訊息是使用協助程式元件所建立並發佈至 MessageBox。  

5. Wcf-basichttp 傳送埠會取用的要求訊息。  

6. Wcf-basichttp 傳送埠會叫用其中一種方法 （新增、 減、 乘、 除） 計算機 WCF web 服務所公開。  

7. 計算機 WCF web 服務傳回回應訊息。  

8. 回應訊息會發佈到 MessageBox。  

9. 回應訊息會傳回給呼叫者 LogicalPortsOrchestration。 協調流程會針對輸入 CalculatorRequest xml 文件中的每個作業重複此模式。  

10. LogicalPortsOrchestration 將 CalculatorResponse 訊息發佈到 MessageBox。  

11. 要求-回應 Wcf-basichttp 接收位置擷取回應訊息。  

12. 傳回的回應訊息的負載測試代理程式電腦。  

    在負載測試期間使用的協調流程的螢幕擷取畫面如下所示：  

> [!NOTE]  
>  基於圖的詳細資訊，如下所示的協調流程會是實際上在負載測試期間使用的協調流程的簡化的版本。 在負載測試期間使用的協調流程包含多個範圍、 錯誤處理邏輯和其他連接埠類型。  

 ![測試應用程式的協調流程](../technical-guides/media/logicalportsorchestration.gif "LogicalPortsOrchestration")  
測試應用程式協調流程  

## <a name="testing-methodology"></a>測試方法  
 效能測試牽涉到許多工作，以手動方式執行是否重複、 單調，而且容易發生錯誤。 若要測試的效率，並提供測試回合之間的一致性[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]Team System (VSTS) 使用 BizUnit 3.0 Test Edition 用來自動化測試的程序期間所需的工作。 VSTS 2008 Test Load Agent 電腦作為測試用戶端用來產生對系統的訊息負載，並在每個測試回合，以改善一致性上使用相同的訊息類型。 遵循此程序，是在每個測試回合中提供一組一致的資料。 如需有關 BizUnit 3.0 的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkID=85168 ](http://go.microsoft.com/fwlink/?LinkID=85168)。 如需詳細資訊[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]Team System Test Edition，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=141387 ](http://go.microsoft.com/fwlink/?LinkID=141387)。  

 已自動化下列步驟：  

- 停止 BizTalk 主控件。  

- 清除測試目錄。  

- 重新啟動 IIS。  

- 清除[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Messagebox 資料庫。  

- 重新啟動 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。  

- 清除事件記錄檔中。  

- 建立儲存相關聯的效能計量和記錄檔每次執行的測試結果資料夾。  

- 啟動 BizTalk 主控件。  

- 載入效能監視器計數器。  

- 熱機小負載的 BizTalk 環境。  

- 代表執行透過傳送。  

- 效能記錄檔寫入結果資料夾中。  

- 收集應用程式記錄檔，並寫入至.csv 檔案，結果資料夾中。  

- 針對收集的效能記錄檔，以產生統計資料、 圖表和報表來執行效能分析的記錄檔 (PAL) 工具，重新記錄和記錄檔剖析器的工具。 如需有關 PAL，重新記錄，記錄檔剖析器的詳細資訊，請參閱 <<c0> [ 測量效能的附錄 d： 工具](../technical-guides/appendix-d-tools-for-measuring-performance.md)。  

> [!NOTE]  
>  已停用所有追蹤，並在測試期間的 BizTalk Server SQL Server Agent 作業已停都用。  

 若要確保此實驗室中的結果能夠提供的效能比較[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在實體與 HYPER-V 環境中，效能計量和記錄檔中收集到集中位置以進行每個測試回合。  

 測試用戶端用來建立每個測試回合的唯一結果目錄。 此目錄包含所有效能記錄檔，事件記錄檔和相關聯的測試所需的資料。 這個方法會提供回溯分析先前的測試執行時所需的資訊為必要。 在每個測試結束時，未經處理的資料已編譯成一組一致的結果和關鍵效能指標 (Kpi)。 收集一致的結果設定實體和虛擬化的機器提供的比較在不同的測試回合和不同環境之間所需的點。 所收集的資料包含：  

- **環境中 –** 来錄製哪一個環境，測試正在執行對實體硬體上的 BizTalk Server 或 HYPER-V 上的 BizTalk Server。  

- **測試執行號碼 –** 來唯一識別每個測試回合  

- **測試案例-** 記錄在測試期間使用的 BizTalk Server 解決方案的架構。 （例如與使用內嵌的協調流程的邏輯連接埠的協調流程傳送）  

- **日期 –** 執行記錄的日期和時間的測試  

- **時間已啟動 –** 所報告的第一個 VSTS 負載測試代理程式起始  

- **時間已停止 –** 所完成的最後一個 VSTS 負載測試代理程式報告  

- **測試持續時間，以分鐘計 –** 記錄測試的持續時間。  

- **總計-可在傳送的郵件數**來記錄從負載代理程式電腦傳送至 BizTalk Server 電腦在測試期間的訊息總數。  

- **– 每秒傳送的郵件數**來記錄每秒從負載代理程式電腦的 BizTalk Server 電腦到測試期間傳送的訊息。  

- **平均用戶端延遲 –** 記錄的平均 Test Load Agent 用戶端起始的要求和負載測試期間，從 BizTalk Server 的電腦收到的回應之間的時間量。  

- **要求-回應持續時間平均 （毫秒） –** 所回報**BizTalk： 傳訊 Latency\Request 回應延遲 （秒）** BizTalkServerIsolatedHost 的效能監視器計數器  

  > [!NOTE]  
  >  使用多個虛擬化的 BizTalk 主控件執行這些計數器的平均值計算從記錄檔。  

- **– 每秒的協調流程已完成**所回報**XLANG/s 協調流程 (BizTalkServerApplication) \Orchestrations 每秒完成**效能監視器計數器。 此計數器提供良好的輸送量的測量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]解決方案。  

- **%的訊息處理的 < 3 秒數 –** 記錄在測試期間的 3 秒內處理的訊息總數。  

  VSTS 2008 負載測試用來產生整個所有測試的一致性負載。 下列測試回合設定並測試來調整每個測試的負載設定檔期間已修改的負載模式：  

- **測試回合設定**  

   下列測試回合設定已修改根據所執行的測試：  

  - **執行持續時間 –** 指定多久執行測試。  

    ![測試回合的設定](../technical-guides/media/wcfloadtestrunsettings.gif "WCFLoadTestRunSettings")  
    測試回合設定  

- **測試模式設定**  

   根據所執行的測試，已修改下列的測試模式設定：  

  1. **模式-** 指定負載測試期間調整模擬的使用者負載的方式。 負載模式都是**常數**，**步驟**，或**目標**基礎。 所有負載測試執行都為常數或步驟。  

     > [!NOTE]
     >  本指南使用其中一個執行所有測試**常數**負載模式或**步驟**負載模式。 常數負載模式和步驟負載模式提供下列功能：  
     > 
     > - **常數負載模式 –** 負載模式測試期間，模擬的使用者數目開始的預先定義的層級，並不會變更。  
     >   -   **步驟負載模式 –** 負載模式會增加在測試回合期間，模擬的使用者數目開始預先定義的層級，並會在預先定義的間隔測試的持續時間遞增以預先定義的數量。  

  2. **常數使用者計數 （常數負載模式）-** 產生負載與針對 Visual Studio 負載測試專案的 app.config 檔案中指定的端點位址的虛擬使用者數目。 用於負載測試的負載模式設定中指定此值。  

  3. **初始使用者計數 （步驟負載模式）-** 產生負載與針對指定的端點位址的步驟負載模式測試開頭的虛擬使用者數目。 用於負載測試的負載模式設定中指定此值。  

  4. **最大使用者計數 （步驟負載模式）-** 產生負載與針對結尾的步驟負載模式測試指定的端點位址的虛擬使用者數目。 用於負載測試的負載模式設定中指定此值。  

  5. **逐步執行持續期間 （步驟負載模式）-** 虛擬使用者會產生負載與針對指定的端點位址的負載測試步驟的秒數。  

  6. **逐步執行使用者計數 （步驟負載模式）-** 為提升在每個步驟，使用步驟負載模式時的虛擬使用者數目。  

     ![測試模式設定](../technical-guides/media/wcfloadtestpatternsettings.gif "WCFLoadTestPatternSettings")  
     測試模式設定  

  如需有關使用中的負載測試[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]，請參閱主題**使用 負載測試**中[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]Team System 文件，網址[ http://go.microsoft.com/fwlink/?LinkId=141486 ](http://go.microsoft.com/fwlink/?LinkId=141486)。  

## <a name="key-performance-indicators-measured-during-testing"></a>在測試期間測量關鍵效能指標  
 為所有測試回合的關鍵效能指標 (KPI)，已擷取下列效能監視器計數器：  

> [!NOTE]  
>  如需有關評估與效能監視器計數器的效能的詳細資訊，請參閱[檢查清單： 測量 HYPER-V 上的效能](../technical-guides/checklist-measuring-performance-on-hyper-v.md)。  

 **BizTalk Server KPI**  

- **– 每秒處理文件**所測量**BizTalk： 傳訊/文件 processed/Sec**計數器。  

- **Latency-** 測量所傳回的 VSTS 2008 負載測試控制器。  

  **SQL Server KPI**  

- **SQL Server 處理器使用率 –** 所測量**SQL\Processor(Total)\\%Processor Time**計數器。 此計數器會測量的 CPU 使用率[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]處理[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  

- **Transact SQL 命令的處理效能 –** 所測量**\SQL Server:SQL Statistics\Batch Requests/sec**計數器。 此計數器會測量每秒接收的 TRANSACT-SQL 命令批次數目。 此計數器來測量輸送量[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  

  **網路 KPI**  

- **BizTalk Server 的網路輸送量 –** 所測量**\Network 介面 (\*) \Bytes Total/sec**上的效能監視器計數器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。  

- **SQL Server 網路輸送量 –** 所測量**SQL Network Interface\Bytes Total/sec (Avg)** VSTS 2008 負載測試控制器所傳回。  

  **KPI 的記憶體**  

- **可用的記憶體 –** 所測量**\Memory\Available Mbytes**計數器的各種案例。  

## <a name="physical-infrastructure-specifics"></a>實體基礎結構詳細資料  
 針對每個已安裝的伺服器已調整下列設定。  

 **所有伺服器：**  

- 分頁檔設定為 1.5 倍的實體配置的記憶體數量。 分頁檔設定為固定的大小，確保 初始大小和最大值是以 mb 為單位相同。  

- 從進階的 [系統內容] 畫面，已選取 「 為了達到最佳效能調整 「 效能選項。  

- 它已驗證的系統已調整為不同的系統屬性的 [效能選項] 區段中的背景服務的最佳效能。  

- [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 已安裝做為客體作業系統，在每個虛擬機器上。  

- 若要安裝最新的安全性更新的所有伺服器上成功執行 Windows Update。  

  **針對 SQL Server:**  

- 根據安裝指南 》 提供在安裝 SQL Server [ http://go.microsoft.com/fwlink/?LinkId=141021 ](http://go.microsoft.com/fwlink/?LinkId=141021)。  

- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 使用具有 SAN Lun 設定根據下表。 資料庫和記錄檔已分散，如下所示，以減少可能發生磁碟 I/O 競爭的 Lun:  

  - Data_Sys 磁碟區已用來儲存所有資料庫檔案 （包括系統和 BizTalk 資料庫），但不含 MessageBox 和 TempDb 資料庫。  

  - Log_Sys 磁碟區已用來儲存所有的記錄檔 (包括系統和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫) 除外，MessageBox 和 TempDb 資料庫。  

  - Data_TempDb 磁碟區已用來儲存的 TempDb 資料庫檔案。  

  - Logs_TempDb 磁碟區已用來儲存 TempDb 記錄檔。  

  - MessageBox 資料庫檔案儲存在 Data_BtsMsgBox 磁碟區和 Log_BtsMsgBox 磁碟區上儲存記錄檔。  

- 此外，個別 LUN 為提供 MSDTC 記錄檔。 高輸送量 BizTalk 在系統上，MSDTC 記錄檔活動可能會導致 I/O 瓶頸，如果其留在相同的實體磁碟機做為作業系統。  


  |      磁碟區名稱      |               檔案               | LUN 大小 GB | 主機磁碟分割大小 GB | 叢集大小 |
  |-----------------------|-----------------------------------|-------------|------------------------|--------------|
  |       Data_Sys        |    MASTER 和 MSDB 資料檔案    |     10      |           10           |     64 KB     |
  |       Logs_Sys        |     MASTER 和 MSDB 記錄檔     |     10      |           10           |     64 KB     |
  |      Data_TempDb      |         TempDB 資料檔案          |     50      |           50           |     64 KB     |
  |      Logs_TempDb      |          TempDB 記錄檔          |     50      |           50           |     64 KB     |
  |    Data_BtsMsgBox     |     BizTalkMsgBoxDb 資料檔案     |     300     |          100           |     64 KB     |
  |    Logs_BtsMsgBox     |     BizTalkMsgBoxDb 記錄檔      |     100     |          100           |     64 KB     |
  | Data_BAMPrimaryImport |    BAMPrimaryImport 的資料檔案     |     10      |           10           |     64 KB     |
  | Logs_BAMPrimaryImport |     BAMPrimaryImport 的記錄檔     |     10      |           10           |     64 KB     |
  | Data_BizTalkDatabases | 其他 BizTalk 資料庫資料檔案 |     20      |           20           |     64 KB     |
  | Logs_BizTalkDatabases | 其他 BizTalk 資料庫記錄檔  |     20      |           20           |     64 KB     |
  |          不適用          |          MSDTC 記錄檔           |      5      |           5            |     不適用      |


- 已安裝 BizTalk Server，依照安裝指南 》，網址[ http://go.microsoft.com/fwlink/?LinkId=128383 ](http://go.microsoft.com/fwlink/?LinkId=128383)。  

- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Best Practices Analyzer (BPA) 工具用來進行平台驗證，一旦已設定系統。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BPA 會位於[ http://go.microsoft.com/fwlink/?LinkId=67150 ](http://go.microsoft.com/fwlink/?LinkId=67150)。  

## <a name="virtualization-specifics"></a>虛擬化細節  
 單一 50GB 的固定 VHD 已用來裝載每個 HYPER-V 虛擬機器的作業系統。  

 因為它們立即配置的最大的儲存體的 vhd 至其裝載所在的磁碟機上的檔案而不是動態調整大小的 Vhd 使用固定的 Vhd。 這可減少發生實體磁碟機上裝載，進而改善磁碟 I/O 效能的 VHD 檔案的分散程度。  

 設定虛擬機器、 安裝[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]單一 VHD 對執行 64 位元版本。 一旦已安裝所有適當的更新基礎的虛擬機器已建立映像使用 sysprep 公用程式會隨[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，%WINDIR%\system32\sysprep 目錄中。  

 然後此基底 VHD 已複製，並作為整個環境已部署的所有 HYPER-V 虛擬機器的基礎。 若要重設系統的安全性識別元，任何之前的基底 VHD 映像上執行 Sysprep[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]二進位檔已部署到系統。  

> [!NOTE]
>  執行 Sysprep，已安裝並在伺服器上設定 BizTalk Server 之後，即可透過 Sysprep 回應檔案和 BizTalk Server 隨附的指令碼使用。 這些範例指令碼與安裝在 32 位元和 64 位元版本的 BizTalk Server 時，專為[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]只。 如需詳細資訊，請參閱 BizTalk Server 的線上文件。  

 自動 Windows 安裝程式參照位於[ http://go.microsoft.com/fwlink/?LinkId=142364 ](http://go.microsoft.com/fwlink/?LinkId=142364)。  

## <a name="see-also"></a>另請參閱  
 [附錄 C：BizTalk Server 和 SQL Server Hyper-V 可支援性](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md)