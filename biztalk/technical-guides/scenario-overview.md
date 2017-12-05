---
title: "案例概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac14328d-c373-49da-a899-4b3ca7d6dc0a
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab36aa51d2dd28651895818caa781c49bf366f50
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="scenario-overview"></a>案例概觀
本主題提供的負載測試完成 BizTalk server 概觀現代企業類別硬體上執行時評估延展性的 BizTalk Server 的產品群組。  
  
 使用專用的硬體的隔離環境中執行所有測試。 BizTalk Server 產品群組已驗證的所有結果和 200 個以上的測試回合中未執行。  
  
 使用傳訊案例和協調流程案例; 用於執行測試這兩種案例會使用 BizTalk WCF NetTcp 配接器。  
  
 若要評估 BizTalk Server 引擎的最大可能的效能，任何自訂管線元件所不使用;然後只在單一、 非常簡單的協調流程使用的協調流程實例。 中所述的效能最佳化[最佳化效能](../technical-guides/optimizing-performance.md)已套用至環境，且完整記錄在[觀察與建議](../technical-guides/observations-and-recommendations.md)。  
  
## <a name="test-goals"></a>測試目標  
 負載測試執行的目標包括：  
  
1.  提供一般的縮放和調整 BizTalk Server 的指引：  
  
    1.  量化新增至 BizTalk Server 群組的其他電腦的影響。 這項測試，BizTalk Server 解決方案的效能測量 BizTalk Server 群組執行時，兩個、 三個或四個執行 BizTalk Server 的電腦。  
  
    2.  量化至 BizTalk Server 群組中新增其他 BizTalk MessageBox 資料庫的影響。 這項測試，BizTalk Server 解決方案的效能測量時的群組已設定為使用單一的 MessageBox 資料庫或四個 MessageBox 資料庫。  
  
        > [!NOTE]  
        >  測試兩個 MessageBox 資料庫與未完成，所以很少，如果有的話，效能優勢時調整一到兩個 MessageBox 資料庫。 事實上，調整一到兩個 MessageBox 資料庫，可能會影響效能。 如需有關向外擴充 MessageBox 的詳細資訊，請參閱[調整出 SQL Server 層](../core/scaling-up-the-sql-server-tier.md)。
  
2.  提供下列案例的調整大小與規模的指導方針：  
  
    1.  Wcf-nettcp 單向傳訊案例  
  
    2.  Wcf-nettcp 單向協調流程案例  
  
## <a name="test-measurements-used"></a>使用測試測量  
BizTalk Server 效能測量使用下列準則：  
  
1.  **整體輸送量**– 來測量 **BizTalk： 傳訊 (*hostname*) \Documents 收到 / Sec * * 和 **BizTalk： 傳訊 (*hostname*) \Documents 處理 / Sec * * 效能計數器的 BizTalk server 接收和處理主控件。  
  
2.  **CPU 使用率**– 測量與**\Processor(_Total)\\%Processor Time** BizTalk Server 上的效能計數器] 和 [SQL Server 電腦。 全面檢閱所有測試結果和任何效能瓶頸所述[觀察與建議](../technical-guides/observations-and-recommendations.md)。  
  
## <a name="scaling-out-the-processing-tier-and-the-database-tier"></a>向外延展的處理層和資料庫層  
BizTalk Server 輕易地容納增加的處理層功能藉由一或多個 BizTalk Server 電腦新增至現有的 BizTalk Server 群組。 BizTalk Server 可容納增加的資料庫層功能透過 MessageBox 資料庫。  
  
若要提供 BizTalk Server 向外延展度量，測試所執行之一個、 兩個、 三和 fourBizTalk 伺服器電腦。 若要示範的向外延展資料庫層的影響，針對單一和多重 MessageBox 系統執行這些測試。  
  
## <a name="testing-scenarios"></a>測試案例  
 下面將詳細說明這些情況的 BizTalk Server 環境的訊息流程。  
  
### <a name="messaging-test-scenario"></a>訊息的測試案例  
 ![傳訊案例](../technical-guides/media/messagingscenario.gif "MessagingScenario")  
  
1.  Visual Studio 2010 Ultimate edition 負載測試功能會產生 XML 訊息，並將它傳送到執行 BizTalk Server 與 NetTcp 傳輸的電腦。  
  
    > [!NOTE]  
    >  如需 Visual Studio 2010 Ultimate edition 負載測試的詳細資訊，請參閱 HYPERLINK""[測試應用程式](http://go.microsoft.com/fwlink/?LinkID=208247)(http://go.microsoft.com/fwlink/?LinkID=208247)。  
    >   
    >  如需我們如何使用 Visual Studio 2010 Ultimate edition 負載測試的功能，在我們的測試環境中的詳細資訊，請參閱[有助於自動化測試使用 Visual Studio](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md)。  
  
2.  BizTalk Server 收到 XML 訊息接收位置使用 Wcf-nettcp 接收配接器。 接收位置設定為使用 PassThruReceive 管線，可不執行訊息的任何處理。  
  
3.  BizTalk Server 的結束點管理員 」 (EPM) 會將訊息發佈到 BizTalk MessageBox 資料庫。  
  
4.  使用 Wcf-nettcp 傳送配接器的 BizTalk Server 傳送埠訂閱接收位置所發佈的訊息，並擷取從 BizTalk MessageBox 的訊息。 傳送埠會使用 PassThruTransmit 管線，可不執行訊息的任何處理。  
  
5.  訊息會傳遞至後端 WCF 服務 Wcf-nettcp 傳送配接器。  
  
### <a name="orchestration-test-scenario"></a>協調流程的測試案例  
 ![協調流程實例流程](../technical-guides/media/orchestrationscenarioflow.gif "OrchestrationScenarioFlow")  
  
1.  Visual Studio 2010 Ultimate edition 負載測試功能會產生 XML 訊息，並將它傳送到執行 BizTalk Server 使用 NetTcp 傳輸的電腦。  
  
2.  BizTalk Server 收到 XML 訊息接收埠會使用 Wcf-nettcp 接收配接器。 接收埠已設定為使用 PassThruReceive，管線會執行任何處理的訊息。  
  
3.  訊息會傳遞到簡單的協調流程，僅包含接收埠 （繫結至 WCF 接收埠從步驟 2） 和傳送埠 （繫結至 WCF 傳送埠從步驟 4）。 訊息變數是 「 不具型別的"，表示他們使用 「 訊息類型 」 的 「 System.XML.XmlDocument"。 協調流程只會收到訊息通過其接收埠及透過其傳送埠傳送訊息。 會不執行任何訊息處理。  
  
4.  使用 Wcf-nettcp 傳送配接器的單向 BizTalk Server 傳送埠訂閱協調流程發佈訊息，並擷取從 BizTalk MessageBox 的訊息。 傳送埠會使用 PassThruTransmit 管線，可不執行訊息的任何處理。  
  
5.  訊息會傳遞至後端 WCF 服務 Wcf-nettcp 傳送配接器。  
  
## <a name="hardware-configuration"></a>硬體設定  
  
### <a name="lab-hardware-diagram-and-specifications"></a>實驗室硬體圖形和規格  
 下圖說明使用實驗室的硬體組態。 為了輕易地配合超出 「 處理 」 和 「 資料庫層的小數位數，已使用下列的實驗室硬體：  
  
-   兩個企業類別 Hewlett Packard DL 380 電腦和兩部 BizTalk Server 處理層的 Enterprise 類別 Dell R710 電腦。  
  
-   四個資料庫層，以提供多個 MessageBox 功能的企業類別 Dell R900 電腦。  
  
 下面提供的實驗室中使用的硬體圖表：  
  
 ![效能指南的基礎結構](../technical-guides/media/performanceguideinfrastructure.gif "PerformanceGuideInfrastructure")  
  
 下表提供更多的實驗室中使用的硬體相關資訊。  
  
|名稱|模型|CPU 類型|CPU 數|核心/CPU 的數目|CPU 架構|記憶體|作業系統|軟體|  
|----------|-----------|--------------|--------------------|--------------------------|----------------------|------------|----------------------|--------------|  
|R710-01|Dell PowerEdge R710|Intel Xeon X5570|2 x 2.93 GHz|4|x64|72 GB|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|R710 02|Dell PowerEdge R710|Intel Xeon X5570|2 x 2.93 GHz|4|x64|72 GB|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|DL380G7-01|Hewlett Packard DL380 G7|Intel Xeon X5670|2 x 2.93 GHz|6|x64|192 GB|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|DL380G7 02|Hewlett Packard DL380 G7|Intel Xeon X5670|2 x 2.93 GHz|6|x64|192 GB|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|DL380-01|Hewlett Packard DL380|Intel Xeon 5150|2 x 2.66 GHz|2|x64|8 GB|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 的負載測試資料庫<br /><br /> Visual Studio 2010<br /><br /> WCF 後端服務|  
|DL380 02|Hewlett Packard DL380|Intel Xeon E5335|2 x 2.00 GHz|4|x64|8 GB|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 負載測試控制器|  
|DL380 03|Hewlett Packard DL380|Intel Xeon E5335|2 x 2.00 GHz|4|x64|8 GB|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 負載測試代理程式|  
|DL380 04|Hewlett Packard DL380|Intel Xeon E5335|2 x 2.00 GHz|4|x64|8 GB|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 負載測試代理程式。<br /><br /> Perfmon 命令列|  
|R805 06|Dell PowerEdge R805|AMD 顆四核心 Opteron 2354|2 x 2.2 GHz|4|x64|32 GB|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 負載測試代理程式|  
|R805-07|Dell PowerEdge R805|AMD 顆四核心 Opteron 2354|2 x 2.2 GHz|4|x64|32 GB|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 負載測試代理程式|  
|R900 03|Dell PowerEdge R900|Intel Xeon E7330|4 x 2.4 GHz|4|x64|64 GB|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 含累計更新 4|  
|R900 04|Dell PowerEdge R900|Intel Xeon E7330|4 x 2.4 GHz|4|x64|64 GB|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 含累計更新 4|  
|R900 05|Dell PowerEdge R900|Intel Xeon E7330|4 x 2.4 GHz|4|x64|64 GB|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 含累計更新 4|  
|R900 06|Dell PowerEdge R900|Intel Xeon E7330|4 x 2.4 GHz|4|x64|64 GB|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 含累計更新 4|  
  
### <a name="storage-area-network-configuration"></a>存放區域網路設定  
 下圖說明在實驗室環境所使用的存放區域網路 (SAN) 組態。  
  
 ![SAN 資訊](../technical-guides/media/saninformation.gif "SANinformation")  
  
### <a name="emc-clariion-cx4-960-san-configuration"></a>EMC CLARiiON CX4 960 SAN 組態  
  
|服務處理器和快取資訊|LUN 組態|  
|---------------------------------------------|-----------------------|  
|兩個服務處理器，每個都有：<br /><br /> -讀取快取大小： 2000 MB。<br />-寫入快取大小： 8000 MB。<br />-兩個前端連接埠連接到光纖交換器。 每個連接埠的 4 Gbps。|-64 部磁碟 (268 GB，15 k Seagate RPM，光纖通道。<br />-8 個 8 磁碟 RAID 1 + 0 從這些 64 部磁碟分割的群組。<br />-每個 DB 伺服器指派給 5 MetaLUNs 從這些 RAID 群組平均設定。|  
  
 請務必判斷 SAN 的最大未偏離正軌輸送量並比較此值，以針對生產 SAN 的預期負載。 這將有助於避免非預期的支出 SAN 相關的硬體，將您的應用程式從測試/品質保證 (QA) 環境移至生產環境時。 例如，SAN 可用的最大輸送量可能在沙箱化的測試環境中的應用程式的多個足夠。 不過，如果其他伺服器應用程式將使用 SAN 在生產環境中，可以使用 SAN 輸送量可能不足，無法成為瓶頸。  
  
 在評估時 SAN 的效能，請考慮下列各項：  
  
1.  **SAN 提供的最大輸送量是什麼？** – 這被測量使用最低公分母，根據處理能力，在伺服器、 交換器 SAN 輸送量，輸送量和速度的 SAN 控制卡的主機匯流排介面卡 (HBA)。  
  
2.  **其他應用程式會使用 SAN 在生產環境中？** -請考慮其他應用程式會讓使用 SAN 在生產環境中。 如果其他的資料庫或其他的 I/O 密集應用程式，例如 Exchange Server 將使用 SAN 在生產環境中，將據此減少 SAN 輸送量適用於執行 BizTalk Server 電腦的數量。  
  
 實驗室環境中，使用專用的 SAN。 每四個 SQL Server 電腦已連接到 SAN 提供潛在的總輸送量，8-Gbps 每一部伺服器的兩個 4 Gbps 主機匯流排介面卡 (Hba)，與參數。 SAN 有兩個服務處理器，而每個服務處理器有兩個連接至光纖交換器，提供潛在的總輸送量，16 Gbps 之間的 SAN 和交換器的前端連接埠。  
  
 下列的 LUN 組態已針對每個測試環境中執行 SQL Server 的四部電腦使用。  
  
|磁碟機代號|磁碟區名稱|檔案|LUN 的大小 (GB)|  
|------------------|-----------------|-----------|---------------------|  
|C|本機 C 磁碟機|MASTER、 MSDB 和模型|136|  
|H|Data_Tempdb|TempDB 資料檔案|50|  
|I|Logs_Tempdb|TempDB 記錄檔|50|  
|J|Data_BtsMsgBox|BizTalk MsgBoxDB 資料檔案 + （在 Master MsgBox) 管理資料庫，SSO DB DTA 資料庫資料檔案|120|  
|K|Logs_BtsMsgBox|BizTalk MsgBoxDB 記錄檔 + （在 Master MsgBox) 管理資料庫、 SSO 資料庫、 DTA DB 記錄檔|120|  
|O|Logs_Spare|不使用的 SQL 檔案。 用來儲存 DTCLog 檔案，因為 MSDTC 造成頻繁的磁碟 I/O，尤其是在多個 MessageBox 環境。|20|  
  
### <a name="sqlio-test-results"></a>SQLIO 測試結果  
 我們使用 SQLIO 工具來測量在我們的實驗室環境中使用的儲存區域網路 (SAN) 設定的輸入/輸出容量和效能評定。 正如其名的工具，SQLIO 是測量的 SQL Server 效能上的檔案系統 I/O 影響的寶貴工具。 

若要測量的 SQL Server 資料庫應用程式的存放區域網路 (SAN) 設定的輸入/輸出容量，請參閱[分析的 I/O 特性和調整大小的 SQL Server 資料庫應用程式的儲存體系統](https://msdn.microsoft.com/library/ee410782(SQL.100).aspx)。  
  
 SQLIO 測試中，sqlio.exe 公用程式問題 8k 讀取 8 個執行緒的要求，並維護 8 的 I/O 佇列深度。 我們使用下列參數：  
  
-   所有測試都使用 8 個處理執行緒，每一次執行 60 秒。  
  
-   8 kb 的隨機寫入的資料檔案。  
  
-   8 kb 的隨機讀取資料檔案。  
  
-   所有檔案的都大小為 25 GB。  
  
-   磁碟機基準是 H:%M、:、 j:、 和 K 磁碟機。  
  
 使用的 SQLIO 命令列會如下所示：  
  
-   **針對讀取**: sqlio kR-s60 frandom-o8-t8-b8 LS-FParam.txt  
  
-   **對於寫入**: sqlio-千瓦-s60 frandom-o8-t8-b8 LS-FParam.txt  
  
 Param.txt 檔案包含下列內容：  
  
-   **磁碟機數目：** H:%M、:、 j:、 和 K  
  
-   **測試檔案的實體位置**:  
  
    -   H:\testfile.dat 2 0x0 25000  
  
    -   I:\testfile.dat 2 0x0 25000  
  
    -   J:\testfile.dat 2 0x0 25000  
  
    -   K:\testfile.dat 2 0x0 25000  
  
 下表列出的測試結果：  
  
-   從 25 GB 測試檔案，同時在 Lun H:%M，i:，j:，K (用於所有資料庫檔案的 Lun) 上的 8 KB 的隨機讀取  
  
    ###  
  
    |輸入/輸出操作數量 （Io/秒）|Mb / 秒 （Mb/秒）|平均延遲|  
    |------------------------------------------------------|---------------------------------------|---------------------|  
    |10662.67|83.30|5 毫秒|  
  
-   8 KB 的隨機寫入 25 GB 測試檔案，同時在 Lun H:%M，i:，j:，K (用於所有資料庫檔案的 Lun) 上  
  
    ###  
  
    |輸入/輸出操作數量 （Io/秒）|Mb / 秒 （Mb/秒）|平均延遲|  
    |------------------------------------------------------|---------------------------------------|---------------------|  
    |31527.95|246.31|1 毫秒|  
  
## <a name="see-also"></a>請參閱  
 [調整生產 BizTalk Server 環境](../technical-guides/scaling-a-production-biztalk-server-environment.md)