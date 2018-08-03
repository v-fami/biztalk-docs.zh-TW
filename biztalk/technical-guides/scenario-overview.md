---
title: 案例概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac14328d-c373-49da-a899-4b3ca7d6dc0a
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5bbc23f4d6b9d1e2886059cf053a495562c1d01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007143"
---
# <a name="scenario-overview"></a>案例概觀
本主題概述的負載測試完成 BizTalk server 在現代企業級硬體上執行時評估的 BizTalk Server 延展性的產品群組。  

 使用專用的硬體的隔離環境中執行所有測試。 200 個以上的測試回合所執行，並由 BizTalk Server 產品小組已驗證的所有結果。  

 使用傳訊案例，並協調流程實例中，執行測試這兩種案例使用 BizTalk WCF NetTcp 配接器。  

 若要評估 BizTalk Server 引擎可能的最大效能，使用沒有自訂管線元件;而且只有一個單一且非常簡單的協調流程已用於協調流程案例。 中所述的效能最佳化[最佳化效能](../technical-guides/optimizing-performance.md)已套用至環境，和完整記錄在[觀察與建議](../technical-guides/observations-and-recommendations.md)。  

## <a name="test-goals"></a>測試目標  
 負載測試執行的目標，其中包括：  

1.  提供一般的調整大小和調整適用於 BizTalk Server 的指引：  

    1.  量化新增至 BizTalk Server 群組的其他電腦的影響。 這項測試，BizTalk Server 解決方案的效能測量時 BizTalk Server 群組執行，兩個、 三個和第四個執行 BizTalk Server 的電腦。  

    2.  量化加入 BizTalk Server 群組中的其他 BizTalk MessageBox 資料庫中的影響。 這項測試，BizTalk Server 解決方案的效能測量時的群組已設定為使用單一的 MessageBox 資料庫或四個 MessageBox 資料庫。  

        > [!NOTE]  
        >  測試兩個 MessageBox 資料庫不是因為從一到兩個 MessageBox 資料庫在調整時，會有一點，如果有的話，效能優勢。 事實上，從一到兩個 MessageBox 資料庫，可能會影響效能。 如需有關向外擴充 MessageBox 的詳細資訊，請參閱[相應放大 SQL Server 層](../core/scaling-up-the-sql-server-tier.md)。

2.  提供對下列案例的大小和調整指引：  

    1.  WCF-NetTcp 單向傳訊案例  

    2.  WCF-NetTcp 單向協調流程案例  

## <a name="test-measurements-used"></a>測試使用的度量  
BizTalk Server 效能測量使用下列準則：  

1.  **整體輸送量**– 使用測量**BizTalk： 傳訊 (*主機名稱*) \Documents received/Sec**並**BizTalk： 傳訊 (*主機名稱*)\Documents processed/Sec**效能計數器，以便讓 BizTalk Server 接收和處理主控件。  

2.  **CPU 使用率**– 使用測量**\Processor(_Total)\\%Processor Time** BizTalk 伺服器上的效能計數器] 和 SQL Server 電腦。 所有測試結果更全面來都檢閱和中所述的任何效能瓶頸[觀察與建議](../technical-guides/observations-and-recommendations.md)。  

## <a name="scaling-out-the-processing-tier-and-the-database-tier"></a>向外延展處理層和資料庫層  
BizTalk Server 輕鬆地容納增加的處理層功能，藉由將現有的 BizTalk Server 群組中的一或多個 BizTalk Server 電腦。 BizTalk Server 可容納增加的資料庫層功能，透過 MessageBox 資料庫。  

若要提供 BizTalk Server 的擴充計量，測試所執行之一、 二、 三和 fourBizTalk 伺服器電腦。 若要示範的向外延展資料庫層影響，針對單一和多個 MessageBox 系統執行這些測試。  

## <a name="testing-scenarios"></a>測試案例  
 以下將詳細說明訊息透過 BizTalk Server 環境，針對這些案例的流量。  

### <a name="messaging-test-scenario"></a>訊息的測試案例  
 ![傳訊案例](../technical-guides/media/messagingscenario.gif "MessagingScenario")  

1.  Visual Studio 2010 Ultimate edition 負載測試功能會產生 XML 訊息，並將它傳送到執行 BizTalk Server 使用 NetTcp 傳輸的電腦。  

    > [!NOTE]  
    >  如需 Visual Studio 2010 Ultimate edition 負載測試的詳細資訊，請參閱 HYPERLINK""[測試應用程式](http://go.microsoft.com/fwlink/?LinkID=208247)(http://go.microsoft.com/fwlink/?LinkID=208247)。  
    >   
    >  如需我們如何使用 Visual Studio 2010 Ultimate edition 中的負載測試功能我們的測試環境的詳細資訊，請參閱[使用 Visual Studio 促進自動化測試](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md)。  

2.  BizTalk Server 收到 XML 訊息接收位置使用 Wcf-nettcp 接收配接器。 接收位置會設定為使用 PassThruReceive 管線，它會執行任何處理訊息。  

3.  BizTalk Server 的結束點管理員 」 (EPM) 會將訊息發佈到 BizTalk MessageBox 資料庫。  

4.  使用 Wcf-nettcp 傳送配接器的 BizTalk Server 傳送埠會訂閱接收位置所發佈的訊息，並擷取從 BizTalk MessageBox 的訊息。 傳送埠會使用 PassThruTransmit 管線中，執行未處理的訊息。  

5.  訊息會傳遞到後端 WCF 服務 Wcf-nettcp 傳送配接器。  

### <a name="orchestration-test-scenario"></a>協調流程的測試案例  
 ![協調流程案例的流程](../technical-guides/media/orchestrationscenarioflow.gif "OrchestrationScenarioFlow")  

1.  Visual Studio 2010 Ultimate edition 負載測試功能會產生 XML 訊息，並將它傳送到執行 BizTalk Server 使用 NetTcp 傳輸的電腦。  

2.  BizTalk Server 收到 XML 訊息接收埠會使用 Wcf-nettcp 接收配接器。 接收埠會設定為使用 PassThruReceive，管線會執行任何處理訊息。  

3.  訊息會傳遞到簡單的協調流程，其中僅包含接收埠 （繫結至 WCF 接收埠從步驟 2） 和傳送埠 （繫結至 WCF 傳送埠從步驟 4）。 訊息的變數是 「 不具類型 」，也就是說，它們會使用 「 訊息類型 」 「 System.XML.XmlDocument"。 協調流程只會收到訊息通過其接收埠，並透過它的傳送埠傳送訊息。 會不執行任何訊息處理。  

4.  使用 Wcf-nettcp 傳送配接器的單向 BizTalk Server 傳送埠訂閱協調流程發佈訊息，並擷取從 BizTalk MessageBox 的訊息。 傳送埠會使用 PassThruTransmit 管線中，執行未處理的訊息。  

5.  訊息會傳遞到後端 WCF 服務 Wcf-nettcp 傳送配接器。  

## <a name="hardware-configuration"></a>硬體組態  

### <a name="lab-hardware-diagram-and-specifications"></a>實驗室硬體圖形和規格  
 使用實驗室的硬體組態如下所示。 若要輕鬆地因應從 「 處理 」 和 「 資料庫層的規模，實驗室使用下列硬體：  

- 兩個的企業級 Hewlett Packard DL 380 電腦和兩部 BizTalk Server 處理層的企業類別 Dell R710 電腦。  

- 四部地提供多個 MessageBox 資料庫的資料庫層的企業類別 Dell R900 電腦。  

  在實驗室中用到的硬體圖如下所示：  

  ![效能指南的基礎結構](../technical-guides/media/performanceguideinfrastructure.gif "PerformanceGuideInfrastructure")  

  下表提供有關在實驗室中所使用的硬體更具體資訊。  

|[屬性]|[模型]|CPU 類型|CPU 數|核心/CPU 數目|CPU 架構|記憶體|作業系統|軟體|  
|----------|-----------|--------------|--------------------|--------------------------|----------------------|------------|----------------------|--------------|  
|R710-01|Dell PowerEdge R710|Intel Xeon X5570|2 x 2.93 GHz|4|x64|72 GB|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|R710-02|Dell PowerEdge R710|Intel Xeon X5570|2 x 2.93 GHz|4|x64|72 GB|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|DL380G7-01|Hewlett Packard DL380 G7|Intel Xeon X5670|2 x 2.93 GHz|6|x64|192 GB|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|DL380G7-02|Hewlett Packard DL380 G7|Intel Xeon X5670|2 x 2.93 GHz|6|x64|192 GB|Windows Server 2008 R2 Enterprise Edition|BizTalk Server|  
|DL380-01|Hewlett Packard DL380|Intel Xeon 5150|2 x 2.66 GHz|2|x64|8 GB|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 的負載測試資料庫<br /><br /> Visual Studio 2010<br /><br /> WCF 後端服務|  
|DL380-02|Hewlett Packard DL380|Intel Xeon E5335|2 x 2.00 GHz|4|x64|8 GB|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 負載測試控制器|  
|DL380-03|Hewlett Packard DL380|Intel Xeon E5335|2 x 2.00 GHz|4|x64|8 GB|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 負載測試代理程式|  
|DL380-04|Hewlett Packard DL380|Intel Xeon E5335|2 x 2.00 GHz|4|x64|8 GB|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 負載測試代理程式。<br /><br /> Perfmon 命令列|  
|R805-06|Dell PowerEdge R805|AMD 四核心 Opteron 2354|2 x 2.2 GHz|4|x64|32 GB|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 負載測試代理程式|  
|R805-07|Dell PowerEdge R805|AMD 四核心 Opteron 2354|2 x 2.2 GHz|4|x64|32 GB|Windows Server 2008 R2 Enterprise Edition|Visual Studio 2010 負載測試代理程式|  
|R900-03|Dell PowerEdge R900|Intel Xeon E7330|4 x 2.4 GHz|4|x64|64 GB|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 含累計更新 4|  
|R900-04|Dell PowerEdge R900|Intel Xeon E7330|4 x 2.4 GHz|4|x64|64 GB|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 含累計更新 4|  
|R900-05|Dell PowerEdge R900|Intel Xeon E7330|4 x 2.4 GHz|4|x64|64 GB|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 含累計更新 4|  
|R900-06|Dell PowerEdge R900|Intel Xeon E7330|4 x 2.4 GHz|4|x64|64 GB|Windows Server 2008 R2 Enterprise Edition|SQL Server 2008 R2 含累計更新 4|  

### <a name="storage-area-network-configuration"></a>存放區域網路設定  
 下圖說明在實驗室環境所使用的存放區域網路 (SAN) 組態。  

 ![SAN 的資訊](../technical-guides/media/saninformation.gif "SANinformation")  

### <a name="emc-clariion-cx4-960-san-configuration"></a>EMC CLARiiON CX4 960 SAN 組態  

|服務處理器和快取資訊|LUN 組態|  
|---------------------------------------------|-----------------------|  
|兩個服務處理器，每個都有：<br /><br /> -讀取快取大小： 2000 MB。<br />-寫入快取大小： 8000 MB。<br />-兩個前端連接埠連接到光纖交換器。 每個連接埠的 4 個 Gbps。|-64 個磁碟 (268 GB，15 k RPM，光纖通道 Seagate。<br />-八個 8 磁碟 RAID 1 + 0 群組從中切割從這些 64 個磁碟。<br />-每個 DB 伺服器指派給 5 MetaLUNs 設定從這些 RAID 群組的平均。|  

 請務必判斷 SAN 如今的最大輸送量，並比較此值，以針對 SAN 在生產環境中預期的負載。 這將有助於避免非預期的 SAN 相關的軟硬體的支出，將您的應用程式從測試/品質保證 (QA) 環境移到生產環境時。 比方說，可用的最大輸送量，為 san 可能超過足夠用於您的沙箱化的測試環境中的應用程式。 不過，如果其他伺服器應用程式將在生產環境中使用 SAN，可用的 SAN 輸送量可能不足，而且可能成為瓶頸。  

 當評估 SAN 的效能，請考慮下列各項：  

1. **什麼是 SAN 的最大如今輸送量？** – 這是使用最小公分母，在伺服器、 交換器 SAN 輸送量和速度的 SAN 控制卡的主機匯流排介面卡 (HBA) 的輸送量方面所測量的。  

2. **哪些應用程式會使用 SAN 在生產環境中？** – 請考慮什麼其他應用程式將使用 SAN 在生產環境中。 如果其他資料庫或其他方式的 I/O 密集型應用程式，例如 Exchange Server 會使用 SAN 在生產環境中，SAN 輸送量可供您執行 BizTalk Server 的電腦數量會跟著降低。  

   針對實驗室環境中，使用專用的 SAN。 每四個 SQL Server 電腦已連線到 SAN 提供可能的總輸送量，8-Gbps 每一部伺服器的兩個 4 Gbps 主機匯流排介面卡 (Hba)，使用參數。 SAN 有兩個服務處理器，和每個服務處理器已連接至光纖交換器，提供可能的總輸送量，為 16-Gbps 之間的 SAN 和交換器的兩個前端連接埠。  

   每個測試環境中執行 SQL Server 的四部電腦使用下列的 LUN 設定。  

|磁碟機代號|磁碟區名稱|檔案|LUN 大小 (GB)|  
|------------------|-----------------|-----------|---------------------|  
|c|本機 C 磁碟機|MASTER、 MSDB 和模型|136|  
|H|Data_Tempdb|TempDB 資料檔案|50|  
|I|Logs_Tempdb|TempDB 記錄檔|50|  
|J|Data_BtsMsgBox|BizTalk MsgBoxDB 資料檔案 + （位於 Master MsgBox) 管理資料庫，SSO DB DTA 資料庫資料檔案|120|  
|K|Logs_BtsMsgBox|BizTalk MsgBoxDB 記錄檔 + （位於 Master MsgBox) 管理資料庫、 SSO 資料庫、 DTA DB 記錄檔|120|  
|O|Logs_Spare|未使用的 SQL 檔案。 用來儲存 DTCLog 檔案，做為 MSDTC 會導致頻繁的磁碟 I/O，尤其是在多個 MessageBox 的環境中。|20|  

### <a name="sqlio-test-results"></a>SQLIO 測試結果  
 我們可以用 SQLIO 工具來測量在我們的實驗室環境中使用的儲存區域網路 (SAN) 設定的輸入/輸出容量和效能評定。 正如其名的工具，SQLIO 是衡量檔案系統 I/O 上的 SQL Server 效能的影響非常有用的工具。 

若要測量的 SQL Server 資料庫應用程式的存放區域網路 (SAN) 組態的輸入/輸出容量，請參閱[分析 I/O 特性和 SQL Server 資料庫應用程式的大小調整儲存體系統](https://msdn.microsoft.com/library/ee410782(SQL.100).aspx)。  

 SQLIO 測試中，sqlio.exe 公用程式問題 8k 讀取 8 個執行緒中的要求，並維持 8 個 I/O 佇列深度。 我們使用下列參數：  

- 所有測試都使用 8 個處理執行緒，每一次執行 60 秒。  

- 8 kb 的隨機寫入的資料檔案。  

- 8 kb 的隨機讀取資料檔案。  

- 所有檔案的都大小為 25 GB。  

- 磁碟機基準測試結果是以 H、 i:、 j:、 和 K 硬碟。  

  使用的 SQLIO 命令列會如下所示：  

- **讀取**: sqlio 韓國-s60 frandom-o8-t8-b8 LS-FParam.txt  

- **寫入**: sqlio-千瓦-s60 frandom-o8-t8-b8 LS-FParam.txt  

  Param.txt 檔案包含下列內容：  

- **磁碟機數目：** H、 i:、 j:、 和 K  

- **測試檔案的實體位置**:  

  -   H:\testfile.dat 2 0x0 25000  

  -   I:\testfile.dat 2 0x0 25000  

  -   J:\testfile.dat 2 0x0 25000  

  -   K:\testfile.dat 2 0x0 25000  

  下表列出的測試結果：  

- 從 25 GB 測試檔案，同時在 Lun H，i:，j:，k: (用於所有資料庫檔案的 Lun) 上的 8 KB 的隨機讀取  

  ###  

  | 每秒 (IOs/sec) 的輸入/輸出作業 | Mb / 秒 （Mb/秒） | 平均延遲 |
  |----------------------------------------------|--------------------------------|-----------------|
  |                   10662.67                   |             83.30              |      5 毫秒       |


- 8 KB 的隨機寫入 25 GB 測試檔案，同時在 Lun H，i:，j:，k: (用於所有資料庫檔案的 Lun) 上  

  ###  

  |每秒 (IOs/sec) 的輸入/輸出作業|Mb / 秒 （Mb/秒）|平均延遲|  
  |------------------------------------------------------|---------------------------------------|---------------------|  
  |31527.95|246.31|1 ms|  

## <a name="see-also"></a>另請參閱  
 [調整生產 BizTalk Server 環境](../technical-guides/scaling-a-production-biztalk-server-environment.md)