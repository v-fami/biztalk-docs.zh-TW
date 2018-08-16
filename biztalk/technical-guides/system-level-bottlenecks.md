---
title: 系統層級瓶頸 |Microsoft 文件
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bdff435-76eb-495f-9fb6-1f1acef3921e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 058fd60e1c38a3045197b4a36bdcc81250ab5be5
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22302982"
---
# <a name="system-level-bottlenecks"></a>系統層級的瓶頸
本主題描述如何解決常見的系統層級瓶頸，可能會影響 BizTalk Server 解決方案的效能。  
  
## <a name="creating-a-snapshot-of-the-baseline-configuration"></a>建立基準設定的快照  
 收集下列資訊可以提供您可用來協助修正系統層級瓶頸中，基準設定的快照集。  
  
### <a name="gather-documentation"></a>蒐集文件  
 檢閱架構與您的案例的基礎結構的文件。  
  
### <a name="run-the-baseline-security-analyzer"></a>執行 Baseline Security Analyzer  
 請遵循下列步驟來執行 Baseline Security Analyzer:  
  
1.  下載[Microsoft Baseline Security Analyzer 2.2](http://go.microsoft.com/fwlink/?LinKID=204006) (http://go.microsoft.com/fwlink/?LinkId=204006)。  
  
2.  使用網域系統管理員帳戶，登入裝載 BizTalk Server 和 SQL Server 電腦的相同網路上的電腦。  
  
3.  安裝 Microsoft Baseline Security Analyzer （例如，其中一部 BizTalk Server 電腦或另一部電腦） 目前電腦上。  
  
4.  執行個別的掃描 (**開始掃描**)，指定為參數的名稱或 IP 位址，每一部 BizTalk Server 和 SQL Server 的電腦。  
  
5.  複製 %userprofile%\SecurityScans 目錄中的每一個安全性報告 （.mbsa 檔案）。  
  
### <a name="run-the-biztalk-server-best-practices-analyzer"></a>執行 BizTalk Server Best Practices Analyzer  
 請遵循下列步驟來執行 BizTalk Server Best Practices Analyzer:  
  
1.  下載[BizTalk Server 最佳做法分析程式 v1.2](http://go.microsoft.com/fwlink/?LinkID=83317) (http://go.microsoft.com/fwlink/?LinkID=83317)。  
  
2.  使用屬於 BizTalk Server 系統管理員安全性群組的使用者帳戶，登入到 BizTalk Server 節點。  
  
3.  目前的電腦上安裝 BizTalk Server Best Practices Analyzer。  
  
4.  執行工具，並儲存報表。  
  
### <a name="run-msinfo32-and-save-the-results"></a>執行 MSInfo32 並儲存結果  
 請遵循下列步驟來執行 MSInfo32:  
  
1.  使用網域或本機系統管理員帳戶，登入每個 BizTalk Server 和 SQL Server 電腦。  
  
2.  啟動命令提示字元，並將目錄變更為電腦的 %windir%\system32 目錄。  
  
3.  從命令提示字元，請執行 MSinfo32.exe。  
  
4.  按一下**檔案**功能表，然後選取**匯出**功能表項目匯出至儲存電腦組態。  
  
### <a name="export-the-biztalk-server-and-sql-server-computer-tcpip-registry-setting-"></a>匯出 BizTalk Server 和 SQL Server 電腦 TCP/IP 登錄設定-  
 請遵循下列步驟來儲存 BizTalk Server 和 SQL Server TCP/IP 登錄設定：  
  
1.  啟動命令提示字元，並將目錄變更為電腦的 %windir%\system32 目錄。  
  
2.  從命令提示字元中執行 Regedit.exe。  
  
3.  瀏覽至下列登錄機碼：  
  
    ```  
    [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters] (network settings)  
    ```  
  
4.  以滑鼠右鍵按一下這個索引鍵，然後選取**匯出**將登錄機碼匯出到檔案。  
  
### <a name="collect-the-biztalk-configuration-files"></a>收集 BizTalk 組態檔  
 每個 BizTalk Server 在節點上，收集 BizTalk Server 組態檔案、 BTSNTSvc.exe.config 檔案 （或 64 位元主控件的 BTSNTSvc64.exe.config），位於 BizTalk Server 安裝資料夾 (例如 C:\Program Files\Microsoft BizTalk Server 2010)。  
  
### <a name="collect-the-net-configuration-files"></a>收集.NET 設定檔  
 每個 BizTalk Server 在節點上，收集 machine.config 和 web.config 的.NET Framework 4.0 組態檔。 您可以在下列位置找到的組態檔：  
  
-   適用於 32 位元： %windir%\Microsoft.NET\Framework\v4.0.30319\CONFIG 資料夾  
  
-   針對 64 位元： %windir%\Microsoft.NET\Framework64\v4.0.30319\CONFIG 資料夾  
  
### <a name="use-the-biztalk-msgboxviewer-tool-to-collect-information-about-the-messagebox-database"></a>使用 BizTalk MsgBoxViewer 工具收集 MessageBox 資料庫的相關資訊  
 請遵循下列步驟來收集有關使用 BizTalk MsgBoxViewer 工具的 MessageBox 資料庫的資訊：  
  
1.  下載[BizTalk MsgBoxViewer 工具](http://go.microsoft.com/fwlink/?LinkID=117289)(http://go.microsoft.com/fwlink/?LinkID=117289)。  
  
2.  BizTalk Server 電腦屬於 BizTalk Server 系統管理員安全性群組的使用者帳戶登入。  
  
3.  將 MsgBoxViewer.exe 複製到 BizTalk Server 電腦。  
  
4.  啟動工具。  
  
5.  按一下**要收集的選擇性資訊**索引標籤，然後再按一下**選取的所有資訊**。  
  
6.  按一下**開始收集**。  
  
7.  狀態標籤會顯示當**結束集合**訊息，切換至包含 MsgBoxViewer.exe 可執行檔的資料夾，複製所產生的報表 (.htm) 和記錄檔。  
  
### <a name="collect-and-store-the-source-code-for-all-components-used-in-the-solution"></a>收集並儲存在方案中使用的所有元件的原始程式碼  
 儲存在個別的檔案共用上的所有元件 （例如協調流程、 自訂管線元件，以及協助程式元件的程式碼） 的原始程式碼。  
  
## <a name="initial-troubleshooting"></a>初始疑難排解  
 沒有 BizTalk Server 方案，如果未啟用，將會造成效能問題，不論整體大小的某些元件或 BizTalk 解決方案的設計。 排除某些"常見的類別 」 參與 BizTalk 解決方案的獨占瓶頸分析之前應該完成下列初步疑難排解工作。  
  
-   **確認追蹤主控件執行個體正在執行-** 追蹤主控件執行個體負責將 BAM 和 HAT 資料從 MessageBox 資料庫的 TrackingData 資料表移到 BizTalkDTADb 和 （或） BAMPrimaryImport 資料庫資料表。 如果追蹤主控件執行個體未執行，則追蹤資料會累積在 MessageBox 資料庫和 BizTalk Server 解決方案的效能產生負面影響。  
  
-   **確認企業單一登入 (ENTSSO) 服務正在執行的所有 BizTalk Server 電腦-上**BizTalk 主控件執行個體維護相依性中的 ENTSSO 服務在本機執行個體。 如果 ENTSSO 服務未執行 BizTalk Server 上，然後在伺服器上的主控件執行個體將無法執行。  
  
-   **確認 SQL Server Agent 服務正在執行的所有 SQL Server 電腦-上**必須執行 SQL Server Agent 服務，為了讓 BizTalk SQL Server Agent 作業來執行。 這些工作會執行重要功能以維持伺服器運作且狀況良好。  
  
-   **確認 BizTalk SQL Server Agent 作業已啟用且正在執行不含例外-** 即使 SQL Server Agent 服務正在執行，它是命令式會啟用所有預設 BizTalk SQL Server Agent 作業和執行成功。  
  
-   **請檢查 BizTalk Server 和 SQL Server 事件記錄檔-** 概略檢查 BizTalk Server 或 SQL Server 事件記錄檔可能會顯示可能需要耗費大量時間來診斷和解決的問題。  
  
-   **執行 BizTalk Server Best Practices Analyzer-** BizTalk Server Best Practices Analyzer 會檢查 BizTalk Server 部署，並產生的最佳做法標準相關的問題清單。 工具會執行組態層級驗證，以從不同的資訊來源，例如 Windows Management Instrumentation (WMI) 類別、 SQL Server 資料庫和登錄項目收集資料。 將資料再用於評估的部署組態。 工具讀取然後只會報告不會修改任何系統設定，並不是自我調整工具。 下載 BizTalk Server 最佳做法分析程式 v1.2 從[BizTalk Server 最佳做法分析程式 v1.2](http://go.microsoft.com/fwlink/?LinkID=83317) (http://go.microsoft.com/fwlink/?LinkID=83317)。  
  
## <a name="high-level-system-bottlenecks"></a>高層級的系統瓶頸  
 本章節描述可能會出現在 BizTalk Server 解決方案以及可能的移轉策略的系統層級瓶頸。  
  
### <a name="disk-io-bottlenecks"></a>磁碟 I/O 瓶頸  
 磁碟 I/O 是指的讀取和寫入作業的實體磁碟上的應用程式所執行或安裝在您的伺服器中的多個磁碟數目。 可能會造成磁碟 I/O 和相關的瓶頸的一般活動包含長時間執行的檔案 I/O 作業、 資料加密和解密，讀取資料庫資料表和實體記憶體不足，這樣可能會造成過度分頁的不必要的資料活動。 磁碟速度是另一個要評估磁碟 I/O 瓶頸; 時，考慮因素較快速的磁碟提供更高的效能，並協助降低磁碟 I/O 瓶頸。  
  
 下表提供規劃磁碟子系統的 BizTalk Server 解決方案時，應考量的因素。  
  
|磁碟子系統的因素|詳細資料|  
|---------------------------|-------------|  
|磁碟記憶體快取和可用的實體記憶體|因為記憶體會快取至磁碟的實體記憶體限制時，請確定您有足夠的可用記憶體數量。 更多的分頁記憶體不足時，會寫入至磁碟，導致更大的磁碟活動。 此外，請確定分頁檔設為適當的大小。 額外的磁碟記憶體快取有助於位移的尖峰磁碟 I/O 要求。 不過，您應該注意很少的大型磁碟記憶體快取解決了在沒有足夠的主軸，問題，並具有足夠的磁針可以變換正負號的大型磁碟記憶體快取的需求。 如需設定 Windows 分頁檔，以獲得最佳效能的資訊，請參閱主題中的 「 設定 Windows 分頁檔，以獲得最佳效能 」 區段[最佳化作業系統效能](~/technical-guides/optimizing-operating-system-performance.md)。|  
|儲存體控制器類型|如果您有電池供電的快取時，啟用寫入快取來改善資料庫磁碟區和交易記錄檔磁碟區上的磁碟寫入效能。 寫入快取提供回應時間 2 毫秒的寫入 I/O 要求，而不是 10 到 20 毫秒，而不啟用寫入快取的回應時間。 啟用寫入快取可大幅改善用戶端寫入要求的回應能力。 因為才有用只能出現在交易記錄檔的循序的磁碟讀取的讀取快取無法改善在 BizTalk 伺服器案例的效能。<br /><br /> 它們會在播放時，才從讀取交易記錄檔，例如資料庫之後還原或當伺服器不是正常關機。 較大的快取容納更多的資料進行緩衝處理，也就是說，可以容納較長的飽和度。 如果您的控制器可讓您設定的快取的頁面大小，您應該設為 4 KB。 較大的大小，例如 8 KB，導致浪費快取，因為 4 KB 的 I/O 要求會佔用整個快取頁面為 8 KB，藉此剪下半中的您可使用快取。|  
|主軸|磁針更重要的是比容量，而且如果磁針支援大量的隨機 I/O 要求，BizTalk Server 效能已獲得改善。 計劃不超過 80%的總使用率，以確定即使中磁針失敗的情況下，有足夠的 I/O。|  
|Raid|您使用的 RAID 解決方案應該根據成本和效能取捨適用於您的環境。 因此，為特定的資料儲存體需求可能會建議的 RAID 解決方案的多個類型。 一般建議如下：<br /><br /> -使用 Raid-1 + 0 （鏡像組中的等量集） 的 BizTalk Server 資料庫。<br />-使用交易記錄檔磁碟區的 Raid 1 （不含同位的鏡像組）。<br />-一般而言，Raid 5 （分散式同位檢查等量集） 建議您不要因為 Raid 5 沒有提供最佳的可靠性、 可用性和效能，相較於其他 Raid 組態。<br />由於對永久的資料遺失的可能性，Raid 0 （不含同位的等量集） 組態應該永遠不會使用 BizTalk Server 實際執行環境中。|  
|匯流排類型|較高的輸送量提供更佳的效能。 一般情況下，SCSI 匯流排提供更佳的輸送量和延展性比 IDE 或 ATA 匯流排。 您可以使用下列方程式，以判斷理論的輸送量限制的匯流排類型：<br /><br /> (匯流排速度 （以位元） / 8 位元，每個位元組)作業系統速度 （MHz) x = 輸送量 （以 MB/s)<br /><br /> 您也可以置於個別的 I/O 匯流排中的多個磁碟機，以改善磁碟 I/O 效能。|  
  
#### <a name="performance-counters-for-measuring-disk-io-bottlenecks"></a>效能計數器來測量磁碟 I/O 瓶頸  
  
> [!NOTE]
>  嘗試分析磁碟效能瓶頸，您應該一律使用實體磁碟計數器。 不過，如果您使用軟體 RAID，您應該使用邏輯磁碟計數器。 邏輯磁碟和實體磁碟計數器，相同的計數器可用於每個計數器物件。 邏輯磁碟資料的大量管理員 （或管理員），而資料分割管理員會追蹤實體磁碟的資料。  
  
 下列效能計數器應該用來判斷是否您的系統發生磁碟 I/O 相關的瓶頸：  
  
-   **PhysicalDisk\Avg.磁碟佇列長度**  
  
    -   臨界值： 不能高於磁針加上兩個數目。  
  
    -   重要： 此計數器表示這兩個讀取的平均數目，並將取樣間隔時間內在佇列中對於所選磁碟的要求。 這個計數器是用來收集並行資料，包括資料暴增和尖峰負載。 這些值代表在收集統計資料的驅動程式之下執行的要求數目。 這表示要求都不一定在佇列，但實際上可以是在服務中或已完成的方式備份路徑。 可能的傳遞位置如下：  
  
        -   SCSIport 或 Storport 佇列  
  
        -   OEM 驅動程式佇列  
  
        -   磁碟控制器的佇列  
  
        -   硬碟佇列  
  
        -   主動接收從硬碟  
  
-   **PhysicalDisk\Avg.Disk Read Queue Length**  
  
    -   臨界值： 應該是少於兩個。  
  
    -   重要： 此計數器表示取樣間隔時間內在佇列中對於所選磁碟的讀取要求平均的數目。  
  
-   **PhysicalDisk\Avg.磁碟寫入佇列長度**  
  
    -   臨界值： 應該是少於兩個。  
  
    -   重要： 此計數器表示取樣間隔時間內在佇列中對於所選磁碟的寫入要求平均的數目。  
  
-   **PhysicalDisk\Avg.Disk sec/Read**  
  
    -   臨界值： 沒有特定的值。  
  
        -   小於 10 毫秒 （毫秒） = 良好  
  
        -   介於 15 到 25 的 ms = 公平  
  
        -   大於 25 毫秒 = 差  
  
    -   重要： 此計數器表示的平均時間，以秒為單位的資料從磁碟讀取作業。 如果數目大於 25 毫秒 (ms) 為單位，表示磁碟系統從磁碟讀取時遇到延遲。 裝載 BizTalk Server 關鍵任務的伺服器，可接受的閾值是比較低，大約 10 毫秒。  
  
-   **PhysicalDisk\Avg.Disk sec/Write**  
  
    -   臨界值： 沒有特定的值。  
  
        -   小於 10 毫秒 （毫秒） = 良好  
  
        -   介於 15 到 25 的 ms = 公平  
  
        -   大於 25 毫秒 = 差  
  
    -   重要： 此計數器表示的平均時間，以秒為單位，將資料寫入磁碟作業。 如果數目大於 25 毫秒，磁碟系統寫入磁碟時，就會發生延遲。 裝載 BizTalk Server 關鍵任務的伺服器，可接受的閾值是比較低，大約 10 毫秒。  
  
-   **PhysicalDisk\Avg.Disk sec/Transfer**  
  
    -   臨界值： 不應該超過 18 （毫秒）。  
  
    -   重要： 此計數器表示的時間，以秒為單位的平均磁碟傳輸。 這可能表示大量磁碟分散程度、 緩慢的磁碟或磁碟故障。 將的值相乘**Physical disk\avg.Disk sec/Transfer**和**Memory\Pages/sec**計數器。 如果這些計數器的乘積超過 0.1，分頁佔用超過 10%的磁碟存取時間，因此您需要更多實體記憶體可用。  
  
-   **PhysicalDisk\Disk Writes/sec**  
  
    -   臨界值： 取決於製造商的規格。  
  
    -   重要： 此計數器表示磁碟上的寫入操作速率。  
  
-   **處理器\\%DPC Time、 %Interrupt Time 及 %Privileged Time-** 如果插斷的時間和延遲程序呼叫 (DPC) 的時間大部分的特殊權限的時間，核心會花費大量時間處理 I/O 要求。 在某些情況下，藉由在多處理器系統上設定插斷和 DPC 少量的 Cpu 相似性可改善效能，進而改善快取位置。 在其他情況下，它最適合散發插斷和 Dpc，在多個 Cpu，以防止變成瓶頸的插斷和 DPC 活動之間。 使用繫結至多處理器電腦上的特定處理器的網路介面卡插斷的插斷篩選組態工具的資訊，請參閱 > 一節 「 使用插斷篩選組態工具來繫結至特定的網路介面卡插斷中的處理器多處理器電腦上 「[最佳化作業系統效能](~/technical-guides/optimizing-operating-system-performance.md)。  
  
-   **Processor\DPCs 排入佇列 / sec-** 測量 Dpc 正在耗用 CPU 時間與核心資源的方式。  
  
-   **Processor\Interrupts / sec-** 的插斷如何耗用 CPU 時間與核心資源的另一個測量。 現代磁碟控制卡通常會結合，或聯合插斷，以便單一插斷會產生多個 I/O 完成的處理。 當然，沒有延遲插斷 （和完成） 和 economizing CPU 處理時間之間的取捨。  
  
#### <a name="disk-io-tuning-options"></a>磁碟 I/O 的微調選項  
 如果您判斷磁碟 I/O 是您的環境中的瓶頸，可以使用下列技巧來減少瓶頸：  
  
-   **重組磁碟-** 使用可在[PageDefrag 公用程式](http://go.microsoft.com/fwlink/?LinkId=108976)(http://go.microsoft.com/fwlink/?LinkId=108976)重組 Windows 分頁檔，並預先配置主檔案表格。  
  
-   **使用等量集來同時處理 I/O 要求，透過多個磁碟-** 使用鏡像磁碟區來提供容錯能力並提升 I/O 效能。 如果您不需要容錯功能，實作等量磁碟區設定為快速讀取和寫入，進而改善儲存體容量。 當使用等量磁碟區時，每個磁碟使用量會減少，因為工作會分散到磁碟區，並提高整體輸送量。 如果您在等量磁碟區中加入額外的磁碟設定不會增加輸送量，則您的系統可能會遇到瓶頸，因為磁碟的磁碟控制卡之間的競爭。 在此情況下，加入額外的磁碟控制器會協助分散負載，以及提高效能。  
  
-   **分散在多個磁碟機-之間的工作負載**Windows 叢集和分散式檔案系統提供多個磁碟機上的負載平衡解決方案。  
  
-   **限制使用檔案壓縮或加密-** 檔案壓縮和加密是 I/O 密集作業。 您應該只使用它們其中有絕對的必要性。  
  
-   **停用建立短檔名-** 如果您不支援 MS-DOS 適用於 Windows 3.x 用戶端，停用短檔名，以改善效能。 多個停用建立簡短名稱的詳細資訊，請參閱 「 停用簡短檔案名稱 (8.3) 第代 」 一節中,[最佳化作業系統效能](~/technical-guides/optimizing-operating-system-performance.md)。  
  
-   **停用存取的最新更新-** 根據預設，NTFS 更新目錄的上次存取日期和時間戳記每當周遊目錄。 對於大型的 NTFS 磁碟區，這個更新程序可能會降低效能。 如需停用上次存取更新的詳細資訊，請參閱下節中的 [停用 NTFS 上次存取的更新][最佳化作業系統效能](~/technical-guides/optimizing-operating-system-performance.md)。  
  
    > [!CAUTION]
    >  某些應用程式，例如增量備份公用程式，依賴 NTFS 更新資訊，而且不將則沒有正確運作。  
  
-   **保留的主檔案表格-適當空間**新增**NtfsMftZoneReservation**登錄根據通常儲存在 NTFS 磁碟區的檔案數目的項目。 當您將此項目加入登錄時，系統會保留之磁碟區的 主檔案表格空間。 保留空間以這種方式可讓主檔案表格，以最佳方式成長。 如果您的 NTFS 磁碟區通常儲存相當幾個檔案，設定此登錄項目的值為預設值為 1。 通常您可以使用的值為 2 或 3，如果您的 NTFS 磁碟區儲存適量的檔案，且使用的值為 4 （上限），如果您的 NTFS 磁碟區通常會包含相對較大的數字的檔案。 不過，請務必測試任何設定大於 2，因為這些更大的值會造成系統上，以保留較大一部分的主檔案表格的磁碟。 如需有關加入**NtfsMftZoneReservation**至登錄，請參閱 > 一節 「 增加中的可用空間的主檔案表格"[最佳化作業系統效能](~/technical-guides/optimizing-operating-system-performance.md)。  
  
-   **使用最有效率的磁碟系統使用-** 除了使用實體磁碟，請考慮將使用的磁碟控制卡和纜線的類型。 有效的磁碟子系統也應該提供支援插斷仲裁或中斷避免降低磁碟 I/O 所造成的處理器插斷活動的驅動程式。  
  
-   **請確定您使用適當的 RAID 設定-** 使用 RAID 10 可以發揮 （條狀配置與鏡像） 的最佳效能和容錯功能。 代價是，使用 RAID 10 可以發揮是高度耗費資源。 請避免使用 RAID 5，當您有大量的寫入作業。 如需 BizTalk Server 環境中實作 RAID 的詳細資訊，請參閱 「 磁碟基礎結構 」 一節中[BizTalk Server 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/?LinkID=101578)(http://go.microsoft.com/fwlink/?LinkID=101578)。  
  
-   **請考慮使用資料庫資料分割-** 如果資料庫瓶頸，請考慮使用資料庫資料分割，並將磁碟對應至特定資料表及交易記錄檔。 資料分割的主要目的是為了克服磁碟瓶頸對於大型資料表。 如果您有大量的資料列的資料表，且您判斷它是瓶頸的來源，請考慮使用資料分割。 針對 SQL Server，您可以使用檔案群組來改善 I/O 效能。 您可以將資料表與檔案群組產生關聯，並將與特定的硬碟產生關聯的檔案群組。 如需有關如何使用 BizTalk Server 資料庫最佳化的檔案群組的詳細資訊，請參閱[最佳化的檔案群組的資料庫](~/technical-guides/optimizing-filegroups-for-the-databases2.md)。  
  
-   **請考慮增加實體記憶體中，如果您有過多的分頁錯誤-** 值很高**記憶體： Pages/sec**效能計數器可能代表過度分頁將會增加磁碟 I / 0。 如果發生這種情況，請考慮新增實體記憶體，以降低磁碟 I/O，並提高效能。  
  
-   **請考慮磁碟具有較高的 RPM 評等，或使用存放區域網路 (SAN) 裝置-** 磁碟具有更高 RPM 評等提供改進的效能相較於磁碟具有較低 RPM 評等。 SAN 裝置通常會提供最上層效能而在錢。  
  
-   請遵循建議[最佳化資料庫效能](~/technical-guides/optimizing-database-performance.md)。 本主題提供數個最佳化之前和之後設定 BizTalk Server 資料庫效能的建議。  
  
### <a name="cpu-bottlenecks"></a>CPU 瓶頸  
 每個伺服器執行的應用程式取得 CPU 的時間配量。 CPU 可能會有效率地處理所有的電腦上，執行的處理序，或可能超載。 藉由檢查處理器活動及活動的個別處理程序包括執行緒建立、 切換執行緒和內容切換，您可以深入了處理器工作負載和效能。  
  
#### <a name="you-may-have-a-cpu-bottleneck-if"></a>如果，可能會有 CPU 瓶頸...  
  
-   值**處理器\\%Processor Time**效能計數器通常超過 75%。  
  
-   值**System\ Processor Queue Length**效能計數器為 2 或多個 for 持續一段時間。  
  
-   值**處理器\\%Privileged Time**或**System\Context Switches/sec**有異常高的效能計數器。  
  
     如果值**Processor\ %Processor Time**效能計數器很高，則佇列會發生，並在大部分情況下的值**System\ Processor Queue Length**也會比較高。  
  
#### <a name="performance-counters-for-measuring-cpu-bottlenecks"></a>效能計數器來測量 CPU 瓶頸  
 下列效能計數器應該用來判斷您的系統是否發生 CPU 相關的瓶頸：  
  
-   **處理器\\%處理器時間**  
  
    -   閾值： 應低於 85%。  
  
    -   重要： 此計數器是處理器活動的主要指示器。 高值許多不一定會是不正確。 不過，其他處理器相關的計數器會以線性方式例如增加**處理器\\%Privileged Time**或**System\Processor Queue Length**，CPU 使用率過高可能值得調查。  
  
-   **處理器\\%特殊權限時間**  
  
    -   臨界值： 過去一直是 75%的圖形會指出是效能瓶頸。  
  
    -   重要： 此計數器表示執行緒在特權模式下執行的時間的百分比。 當您的應用程式呼叫作業系統函式 （例如來執行檔案或網路 I/O，或配置記憶體） 時，這些作業系統函式會執行特殊權限模式。  
  
-   **處理器\\插斷時間百分比**  
  
    -   臨界值： 取決於處理器。  
  
    -   重要： 此計數器表示百分比的處理器花費在接收和服務硬體插斷的時間。 這個值是產生插斷，例如網路介面卡的裝置活動的間接指示器。 在此計數器指出可能硬體問題。  
  
-   **System\Processor Queue Length**  
  
    -   臨界值： 一致高於 2 平均值會指出是效能瓶頸。  
  
    -   重要： 如果有多個工作準備好要執行比處理器，執行緒排入佇列。 處理器佇列已準備好，但您不能因為另一個執行緒目前正在執行的處理器來執行執行緒的集合。 持續性或重複執行佇列的兩個以上的執行緒是清除指示處理器瓶頸。 藉由減少平行處理原則，在這些情況下可能會得到更多的輸送量。  
  
         您可以使用此計數器搭配**處理器\\%Processor Time**計數器以判斷您的應用程式的更多的 Cpu 可以受益。 沒有單一佇列的處理器時間，即使在多處理器電腦上。 因此，在多處理器電腦上，除以處理器佇列長度 (PQL) 值的工作負載的處理器數目。  
  
         若 CPU 非常忙碌 （90%或更高的使用率） 且 PQL 平均值高於持續 2 每個處理器，您可能無法受益新增 Cpu 處理器瓶頸。 或者，您無法減少的應用程式層級的多個執行緒和佇列。 這會導致較少的內容切換，以及較少的環境切換是適合用來降低 CPU 負載。 處理器時間的要求到達隨機，而執行緒要求異常大量的處理器時間 PQL 值為 2 或更低 CPU 使用率最高的一個常見原因。 這表示處理器不是瓶頸，但應該可以改善應用程式執行緒邏輯。  
  
-   **System\Context Switches/sec**  
  
    -   臨界值： 一般而言，內容切換率小於每個處理器每秒 5000 不值得擔心。 如果內容切換率超過 15,000 每秒針對每個處理器，然後內容切換成為瓶頸。  
  
    -   當高優先順序的執行緒優先執行較低優先順序的執行緒，目前正在執行，或當較高優先順序的執行緒會封鎖其他執行緒發生內容切換的意義:。 多執行緒共用相同的優先權層級，就會發生內容切換的高層級。 這通常表示有競爭系統上處理器的執行緒太多。 如果處理器使用量和內容切換層級的較低，這通常是表示執行緒會被封鎖。  
  
#### <a name="resolving-cpu-bottlenecks"></a>解決 CPU 瓶頸  
 第一個步驟是找出哪些處理程序會耗用過多的處理器時間。 使用 Windows**工作管理員**來識別哪些程序耗用的 CPU 高等級藉由查看**CPU**上的資料行**處理程序**頁面。 您也可以決定這藉由監視**程序\\%Processor Time**效能監視器] 和 [選取您想要監視的處理程序中。  
  
 另一個功能強大的工具，來判斷哪些處理程序正在耗用過多 CPU 時間是 Visual Studio Team System 分析工具所提供的 Visual Studio Team System (VSTS) 套件。 如需有關使用 Visual Studio Team System 分析工具的詳細資訊，請參閱 Visual Studio Team System 文件。  
  
 之後您判斷 CPU 瓶頸，您有數個選項，包括下列：  
  
-   如果您有多執行緒應用程式，請加入多個處理器。 請考慮升級至更強大的處理器，如果您的應用程式是單一執行緒。  
  
-   如果您觀察有高比率的內容切換，請考慮減少您的處理序的執行緒計數前的處理器數目增加。  
  
-   分析和微調應用程式造成高 CPU 使用率。 您可以使用 ADPLUS 公用程式傾印執行的處理序，並使用 Windbg 分析可能的原因。 這些公用程式是 Windows 偵錯工具組的一部分。 您可以下載這些工具從[Debugging Tools for Windows](http://go.microsoft.com/fwlink/?LinkID=106624) (http://go.microsoft.com/fwlink/?LinkID=106624)。  
  
-   分析您的應用程式隔離所花的時間執行的最大數量的子系統所產生的檢測記錄檔。 判斷程式碼檢閱是否會比只微調 BizTalk Server 環境更有效率。  
  
> [!NOTE]
>  雖然您可以變更應用程式的處理序優先權層級使用**工作管理員**或從命令提示字元中，您通常應該避免這樣。  
  
### <a name="memory-bottlenecks"></a>記憶體瓶頸  
 當評估記憶體相關的瓶頸，請考慮不必要的配置、 效率不佳清除，而且不適當快取以及狀態管理機制。 若要解決記憶體相關的瓶頸，最佳化您的程式碼才能避免這些問題，然後調整配置給您的應用程式的記憶體數量。 如果您確定在微調期間發生的記憶體爭用和過度分頁，您可能需要額外的實體記憶體新增至伺服器。 記憶體不足會導致增加應用程式的虛擬位址空間與磁碟的分頁。 如果分頁變得過多，會增加磁碟 I/O，並對整體系統效能造成負面影響。  
  
#### <a name="you-might-have-a-memory-bottleneck-if"></a>如果，可能有記憶體瓶頸...  
  
-   值**Memory\Available MBytes**效能計數器很低，可能是因為系統記憶體限制或應用程式沒有釋出記憶體。 監視值**Process\Working Set**執行每個處理序的效能計數器。 如果值**Process\Working Set**維持高處理程序不在作用中，即使這可能是處理程序不釋放記憶體其應有的指示。  
  
-   值**Memory\Pages/sec**效能計數器很高。 平均**Memory\Pages Input/sec**除以平均**Memory\Page Reads/sec**提供每秒磁碟讀取頁面數目。 這個值通常不可以超過五秒頁面數。 大於 5 的頁面每秒的值表示系統花太多時間分頁，且需要更多的記憶體 （假設應用程式已經過最佳化）。  
  
#### <a name="performance-counters-for-measuring-memory-bottlenecks"></a>效能計數器來測量記憶體瓶頸  
 下列效能計數器應該用來判斷您的系統是否遇到記憶體相關的瓶頸：  
  
-   **Memory\Available Mbytes**  
  
    -   臨界值： 一致的值低於 20 到 25%的已安裝的 RAM 是記憶體不足的指示。  
  
    -   重要： 這表示電腦上執行的處理序可用的實體記憶體數量。 請注意，此計數器會顯示最後觀察到的值只。 它不是平均值。  
  
-   **Memory\Page Reads/sec**  
  
    -   臨界值： 持續性的五個以上的值表示大量的讀取要求的分頁錯誤。  
  
    -   重要： 此計數器指出處理程序的工作集是太大，導致記憶體分頁到磁碟的可用實體記憶體。 它會顯示讀取作業數目，而不考慮每個作業所擷取的頁數。 較高的值表示記憶體瓶頸。  
  
         如果較低的頁面讀取作業率伴隨的數值偏高**實體磁碟\\%Disk Time**和**Physical disk\avg.磁碟佇列長度**，可能存在的磁碟 I/O 瓶頸狀況。 如果佇列長度的增加未伴隨頁面讀取速率降低，記憶體瓶頸存在實體記憶體不足所造成。  
  
-   **Memory\Pages/sec**  
  
    -   臨界值： 持續超過五個值會指出是效能瓶頸。  
  
    -   重要： 此計數器表示的讀取或寫入為解決硬體分頁錯誤而對磁碟頁面的速率。 將的值相乘**Physical disk\avg.Disk sec/Transfer**和**Memory\Pages/sec**效能計數器。 如果這些值的乘積超過**0.1**，分頁利用超過 10%的磁碟存取時間，表示實體記憶體不足，無法使用。  
  
-   **Memory\Pool Nonpaged 的 Bytes**  
  
    -   臨界值： 監看值**Memory\Pool Nonpaged Bytes**增加 10%以上的值在系統啟動。  
  
    -   意義： 增加 10%或更多的值，在啟動時可能表示有記憶體流失。  
  
-   **Server\Pool Nonpaged 的失敗**  
  
    -   臨界值： 一般的非零值表示發生瓶頸。  
  
    -   重要： 此計數器表示從非分頁集區的配置失敗次數。 非分頁集區包含從處理序的虛擬位址空間，不要讓空出給分頁檔，在磁碟上，例如處理程序的核心物件表格的網頁。 非分頁集區的可用性會決定多少處理程序、 執行緒和其他可以建立這類物件。 當從非分頁集區的配置失敗時，這可能是因為記憶體流失，處理序中，特別是如果處理器使用量已不會隨之增加。  
  
-   **Server\Pool 分頁失敗**  
  
    -   臨界值： 沒有特定的值。  
  
    -   意義： 此計數器會指出從該分頁集區的配置失敗次數。 此計數器的正數值則表示電腦沒有足夠的實體記憶體或 Windows 分頁檔太小。  
  
-   **Server\Pool Nonpaged 的尖峰**  
  
    -   臨界值： 沒有特定的值。  
  
    -   重要： 這是伺服器已保留在任何一個時間點使用的非分頁集區中的位元組數目上限。 它會指出應該具有電腦的實體記憶體數量。 因為非分頁集區必須位於實體記憶體，而且必須要有一些記憶體，剩下的其他作業，做法則電腦應該已安裝是 4 倍的值表示此計數器的實體記憶體。  
  
-   **Memory\Cache Bytes**  
  
    -   臨界值： 沒有特定的值。  
  
    -   重要： 監視在不同的負載情況下的快取的大小。 此效能計數器的這個值表示靜態檔案快取的大小。 根據預設，此計數器會使用大約 50%的可用記憶體，但是會減少如果可用的記憶體來壓縮，這會影響系統效能。  
  
-   **Memory\Cache Faults/sec**  
  
    -   臨界值： 沒有特定的值。  
  
    -   意義： 此計數器表示 operating system 頻率尋找檔案系統快取中的資料，但找不到它。 這個值應該越低越好。  
  
-   **Cache\MDL 讀取點擊 %**  
  
    -   臨界值： 愈高此值檔案系統快取的效能愈佳。 值應該接近 100%越好。  
  
    -   重要： 此計數器提供的記憶體描述元清單 (MDL) 讀取至檔案系統快取位置快取傳回的物件直接要求，而不是需要從硬碟讀取百分比。  
  
-   **Process\Working Set**  
  
    -   臨界值： 沒有特定的值。  
  
    -   重要： 工作集是目前載入記憶體 （實體 + 虛擬） 中的記憶體分頁的集合。 如果系統有足夠的記憶體，它可以維護足夠的空間中的工作集，使它不需要執行將記憶體分頁至磁碟的磁碟作業。 不過，如果沒有記憶體不足，系統會嘗試減少工作設定立即採取的處理序的記憶體而造成分頁錯誤而增加。 當分頁錯誤的速率上升時，系統會嘗試增加處理程序的工作集。 如果您觀察巨幅波動的工作集，則可能表示記憶體不足的問題。 較高的工作集的值也可能是因為應用程式中的多個組件中。 您可以改善所使用的全域組件快取中的共用組件的工作集中。  
  
#### <a name="resolving-memory-bottlenecks"></a>解決記憶體瓶頸  
 如果您判斷該記憶體是在 BizTalk Server 環境中，使用一或多個下列方法來解決瓶頸是效能瓶頸：  
  
-   調整配置在可以控制配置的記憶體數量。 例如，您可以調整這適用於 BizTalk Server、 ASP.NET 和 SQL Server。  
  
-   增加 Windows 分頁檔的大小，並依照中的 < 設定 Windows 分頁檔以獲得最佳效能 > 一節的步驟[最佳化作業系統效能](~/technical-guides/optimizing-operating-system-performance.md)。  
  
-   關閉未使用的服務。 停止服務，您不使用定期節省記憶體，並改善系統效能。 如需詳細資訊，請參閱 停用不必要的服務 」 一節[最佳化作業系統效能](~/technical-guides/optimizing-operating-system-performance.md)。  
  
-   移除不必要的通訊協定和驅動程式。 即使閒置的通訊協定中的分頁及非分頁記憶體集區使用的空間。 驅動程式也會耗用記憶體，所以您應該移除不必要的。 如需詳細資訊，請參閱 「 移除不必要的網路通訊協定 」 一節[最佳化作業系統效能](~/technical-guides/optimizing-operating-system-performance.md)。  
  
-   在 BizTalk Server 環境中的電腦上安裝額外的實體記憶體。  
  
> [!NOTE]
>  在 32 位元系統上，BizTalk 就可以使用最大值為 2 GB 的記憶體，限制會增加到 3 GB，與 BizTalk Server 2010 和更新版本，如果使用 /3GB 參數。 如需有關記憶體使用量的詳細資訊，請參閱[版本的記憶體限制 Windows](http://go.microsoft.com/fwlink/?LinkId=118349) (http://go.microsoft.com/fwlink/?LinkId=118349)。  
  
### <a name="network-io-bottlenecks"></a>網路 I/O 瓶頸  
  
#### <a name="you-might-have-a-network-io-bottleneck-if"></a>如果，可能會有網路 I/O 瓶頸...  
  
-   值**Network Interface\Bytes Total/sec**效能計數器超過 80%的可用網路頻寬。  
  
-   值**Server\Bytes Total/sec**大於可用的網路頻寬的 50% 效能計數器。  
  
#### <a name="performance-counters-for-measuring-network-io-bottlenecks"></a>測量網路 I/O 瓶頸的效能計數器  
 下列效能計數器應該用來測量網路 I/O，並且判斷網路 I/O 相關的瓶頸時，是否要發生在系統中：  
  
-   **Network Interface\Bytes Total/sec**  
  
    -   多個網路容量的 80%的閾值： 持續的值。  
  
    -   重要： 此計數器表示會傳送及每個網路介面卡接收位元組的速率。 此計數器可協助判斷是否已飽和的網路介面卡，以及是否應該將一個或多個網路介面卡，若要增加可用的網路頻寬。  
  
-   **網路 Interface\Bytes Received/sec**  
  
    -   臨界值： 沒有特定的值。  
  
    -   重要： 此計數器指出透過每張網路介面卡接收位元組的速率。 使用此計數器的值來計算傳入資料的速率的總可用的頻寬百分比。 這將有助於判斷在用戶端將資料傳送到 BizTalk Server 或 BizTalk Server 電腦本身，應會增加網路頻寬，就應增加網路頻寬。  
  
-   **Network Interface\Bytes 傳送/sec**  
  
    -   臨界值： 沒有特定的值。  
  
    -   重要： 此計數器指出透過每張網路介面卡傳送位元組的速率。 使用此計數器的值來計算的輸出資料的速率的總可用的頻寬百分比。 這可協助判斷是否應增加網路頻寬，BizTalk Server 將資料傳送到用戶端上，或是在用戶端電腦接收資料，從 BizTalk Server 上，應增加網路頻寬。  
  
-   **Server\Bytes Total/sec**  
  
    -   超過 50%的網路容量閾值： 持續的值。  
  
    -   重要： 此計數器指出透過網路傳送及接收的位元組數目。 較高的值會指出網路 I/O 瓶頸。 如果總和**Bytes Total/sec**所有伺服器為大約等於您網路的最大傳輸速率，請考慮以改善效能的網路子網路 >。 如需以改善效能的網路子網路 > 的詳細資訊，請參閱**子網路**區段[BizTalk Server 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/?LinkID=101578)(http://go.microsoft.com/fwlink/?LinkID=101578)。  
  
#### <a name="resolving-network-io-bottlenecks"></a>解決網路 I/O 瓶頸  
 如果您判斷網路 I/O 瓶頸，以您的環境中，使用一或多個下列方法來解決瓶頸：  
  
-   遵循 「 改善網路效能的一般指導方針 」 一節中的建議[最佳化網路效能](~/technical-guides/optimizing-network-performance.md)。  
  
-   執行本主題說明 Windows Powershell 網路最佳化指令碼[最佳化網路效能](~/technical-guides/optimizing-network-performance.md)BizTalk Server 環境中的每一部電腦上。  
  
## <a name="see-also"></a>另請參閱  
 [尋找並排除瓶頸](~/technical-guides/finding-and-eliminating-bottlenecks.md)