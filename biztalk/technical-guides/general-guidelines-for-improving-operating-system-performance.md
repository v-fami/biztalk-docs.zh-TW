---
title: 一般指導方針來改善作業系統效能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc9ca38e-1feb-4f34-a64b-d04566e85db9
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7be3f8060bba20bc0ba127443095c228f954bba
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25976572"
---
# <a name="general-guidelines-for-improving-operating-system-performance"></a>一般指導方針來改善作業系統效能
若要改善作業系統效能，應遵循下列指導方針：  
  
## <a name="install-the-latest-bios-storage-area-network-san-drivers-network-adapter-firmware-and-network-adapter-drivers"></a>安裝最新的 BIOS、 存放區域網路 (SAN) 驅動程式、 網路介面卡的韌體和網路介面卡驅動程式  
 硬體製造商會定期發行 BIOS、 韌體與驅動程式可以改善效能和可用性的相關聯的硬體的更新。 請造訪硬體製造商的網站下載並套用每一部 BizTalk Server 環境中的下列硬體元件的更新：  
  
1.  BIOS 更新  
  
2.  SAN 驅動程式 （如果使用 SAN）  
  
3.  NIC 韌體  
  
4.  NIC 驅動程式  
  
## <a name="enable-the-high-performance-power-plan-on-all-biztalk-server-and-sql-server-computers"></a>啟用 「 高效能 」 電源計劃在所有 BizTalk Server 和 SQL Server 的電腦上。  
 根據預設，Windows Server 2008/2008 R2 設定 「 平衡 」 （建議選項） 電源計劃，可讓在節省能源，但會造成增加的延遲時間 （慢回應時間對於某些工作），並且會導致效能問題與 CPU 運算密集應用程式。  
  
 為了減少延遲，您必須確認執行 BizTalk Server 的所有伺服器和 SQL Server 有 Windows**電源計劃**設**高效能**。 如需有關如何切換至**高效能**電源計劃，請參閱知識庫文章： 2207548 [Windows Server 2008 R2 上的整體效能降低](http://go.microsoft.com/fwlink/?LinkID=219677)(http://go.microsoft.com/fwlink/?LinkID=219677)。  
  
## <a name="evaluate-the-usage-of-intel-hyper-threading-on-biztalk-server-and-sql-server-computers"></a>評估使用 Intel 超執行緒，BizTalk Server 和 SQL Server 的電腦上  
  
-   **Pre Nehalem 超執行緒**:  
  
    -   超執行緒對它應該關閉 BizTalk 伺服器的電腦。 這是電腦的 BIOS 設定，通常位於 BIOS 設定的處理器設定。 超執行緒會讓伺服器可能沒有更多的處理器/處理器核心比實際;不過，超執行緒處理器通常提供介於 20-30%的實體處理器/處理器核心的效能。 當 BizTalk Server 會計算要調整其自我調整演算法的處理器數目時，超執行緒處理器，會導致這些調整會扭曲，這可能會導致負面的整體效能。  
  
    -   超執行緒對它應該關閉 SQL Server 電腦因為可能會造成競爭的情況 （例如 BizTalk Server) 的高等級的應用程式可能在 SQL Server 電腦上的超執行緒環境中造成效能降低。  
  
-   **Nehalem 超執行緒**： 不同於在較舊的架構，啟用超執行緒在 Intel 微架構 」 Nehalem"處理器可以提供最幾乎線性容量增加。 為獲得最佳的效能結果，當您部署 「 Nehalem"處理器時，我們會建議您設定電腦的 BIOS，藉由啟用 Intel 超執行緒 (H T) 標示增加輸送量的技術。  
  
-   **硬體虛擬化**： 當使用硬體虛擬化時，虛擬機器使用的虛擬處理器。 可用的 Cpu 數目取決於設定虛擬機器時選擇的設定。 如果硬體是超執行緒，虛擬機器可能不知道它是超執行緒。  
  
## <a name="assign-the-msdtc-log-file-directory-to-a-separate-dedicated-drive"></a>將 MSDTC 記錄檔目錄指派給另一個專用的磁碟機  
 在 BizTalk Server 環境中具有不同的 SQL Server 電腦上的多個 MessageBox 資料庫，造成相關聯的 Microsoft Distributed Transaction Coordinator (MSDTC) 的額外負擔。 根據預設，MSDTC 記錄檔位於 %systemdrive%\windows\system32\msdtc 目錄執行 DTC 服務的電腦。 若要減輕 DTC 記錄可能會成為效能瓶頸的可能性，請考慮將 MSDTC 記錄檔目錄移至快速的磁碟機。  
  
 若要變更 MSDTC 記錄檔目錄，請參閱[設定 DTC 記錄](http://go.microsoft.com/fwlink/?LinkID=204107)(http://go.microsoft.com/fwlink/?LinkID=204107)。  
  
## <a name="configure-antivirus-software-to-avoid-real-time-scanning-of-biztalk-server-executables-and-file-drops"></a>若要避免的 BizTalk Server 可執行檔的即時掃描的防毒軟體設定和檔案會卸除  
 防毒軟體的即時掃描的 BizTalk Server 可執行檔和任何資料夾或檔案共用受 BizTalk Server 接收位置 BizTalk Server 效能造成負面影響。 如果 BizTalk Server 電腦上已安裝防毒軟體，停用即時掃描任何 BizTalk Server 所參考的非可執行檔的檔案類型的接收位置 （通常是。XML，但也可能是.csv 或.txt 等。)和防毒軟體設定為排除掃描的 BizTalk Server 可執行檔  
  
## <a name="disable-intrusion-detection-network-scanning-between-computers-in-the-biztalk-server-environment"></a>停用 BizTalk Server 環境中的電腦之間正在掃描的入侵偵測網路  
 入侵偵測軟體可以變慢或甚至阻止在網路上的有效通訊。 如果安裝入侵偵測軟體時，停用 BizTalk Server 電腦與外部資料儲存機制 (SQL Server) 電腦之間的掃描或傳訊服務 （例如訊息佇列與 WebSphere MQSeries） 電腦的網路。  
  
## <a name="defragment-all-disks-in-the-biztalk-server-environment-on-a-regular-basis"></a>重組以規則為基礎的 BizTalk Server 環境中的所有磁碟  
 BizTalk Server 環境中的過多的磁碟分散程度會產生負面影響效能。 遵循下列步驟來重組 BizTalk Server 環境中的磁碟：  
  
1.  重組所有磁碟 (本機和 SAN/NAS) 上定期排程離峰時間磁碟重組。  
  
2.  重組 Windows 分頁檔，並預先配置 BizTalk Server 環境中的每個磁碟的主檔案表格，以提高整體系統效能。  
  
    > [!NOTE]  
    >  若要預先配置主檔案表格，請參閱知識庫文章 961095， [「 主檔案表格的相關區域保留在 Windows Vista 和 Windows Server 2008"](http://go.microsoft.com/fwlink/?LinkID=204563) (http://go.microsoft.com/fwlink/?LinkID=204563)。  
  
## <a name="if-antivirus-software-is-installed-on-the-sql-server-computer-disable-real-time-scanning-of-data-and-transaction-files"></a>如果 SQL Server 電腦上已安裝防毒軟體，停用的資料和交易檔的即時掃描  
 SQL Server 資料和交易檔案 （.mdf、.ndf、.ldf 和.mdb） 的即時掃描，可以增加磁碟 I/O 競爭，並減少 SQL Server 效能。 請注意，SQL Server 資料和交易檔的名稱可能會不同，BizTalk Server 環境之間。 如需建立預設的 BizTalk Server 組態資料和交易檔的詳細資訊，請參閱[Databases2 最佳化檔案群組](../technical-guides/optimizing-filegroups-for-the-databases2.md)。  
  
## <a name="configure-msdtc-for-biztalk-server-and-sql-server"></a>BizTalk Server 與 SQL Server 設定 MSDTC  
 若要簡化 SQL Server 與 BizTalk Server 之間的交易，您必須啟用 Microsoft Distributed Transaction Coordinator (MSDTC)。  
  
#### <a name="to-configure-distributed-transaction-coordinator-dtc"></a>若要設定 Distributed Transaction Coordinator (DTC)  
  
1.  按一下**啟動**，按一下**執行**，型別**dcomcnfg**，然後按一下**確定**開啟**元件服務**.  
  
2.  在主控台樹狀目錄中，依序展開 [元件服務]、[電腦]、[我的電腦]和 [分散式交易協調器]，然後按一下 [本機 DTC]。  
  
3.  以滑鼠右鍵按一下**本機 DTC**，然後按一下 [**屬性**顯示**本機 DTC 內容**] 對話方塊。  
  
4.  在**追蹤**索引標籤，下方**輸出選項**區段中，清除**追蹤輸出**方塊。  
  
5.  按一下 [安全性] 索引標籤。  
  
6.  請確定下列四個選項中的每個已選取，並會清除所有其他：  
  
    -   **網路 DTC 存取**  
  
    -   **允許輸入**  
  
    -   **允許輸出**  
  
    -   **不需要驗證**  
  
7.  按一下**確定**關閉**本機 DTC 內容** 對話方塊。 如果提示您重新啟動 MSDTC 服務，請按一下**是**。  
  
8.  關閉 [元件服務]。  
  
9. 按一下**啟動**，指向 **系統管理工具**，然後按一下 **具有進階安全性的 Windows 防火牆**。  
  
10. 在 具有進階安全性的 Windows 防火牆，按一下 **輸入規則**。  
  
11. 在**輸入規則**] 窗格中，以滑鼠右鍵按一下**分散式交易協調器*** （適合的話），然後按一下 [**啟用規則**。  
  
12. 在 具有進階安全性的 Windows 防火牆，按一下 **輸出規則**。  
  
13. 在**輸出規則**] 窗格中，以滑鼠右鍵按一下**分散式交易協調器*** （適合的話），然後按一下 [**啟用規則**。  
  
14. 在**控制台**，連按兩下**系統管理工具**。  
  
15. 在右窗格中，按兩下**服務**。  
  
16. 在右窗格中**服務 （本機）**，以滑鼠右鍵按一下**COM + 系統應用程式**，按一下 **重新啟動**，並等待服務重新啟動。  
  
17. 以滑鼠右鍵按一下**分散式交易協調器**服務，再重新啟動。  
  
18. 以滑鼠右鍵按一下 **SQL Server (MSSQLSERVER)** 服務，再重新啟動。  
  
19. 關閉 [服務 (本機)]，然後關閉 [系統管理工具]。  
  
## <a name="configure-firewalls-for-biztalk-server"></a>設定 BizTalk Server 的連線  
  
> [!NOTE]  
>  這是步驟，只需要一個或多個防火牆是否在 BizTalk Server 環境中的位置。  
  
 檢閱下列資訊來設定 BizTalk Server 的連線：  
  
-   [BizTalk Server 所需的連接埠](http://go.microsoft.com/fwlink/?LinkID=153238)(http://go.microsoft.com/fwlink/?LinkID=153238)。  
  
-   若要設定 RPC 動態連接埠配置以使用防火牆，請參閱知識庫文章 929851， [「 TCP/IP 的預設動態通訊埠範圍已變更在 Windows Vista 和 Windows Server 2008 」](http://go.microsoft.com/fwlink/?LinkID=204568) (超連結"http://go.microsoft.com/fwlink/?LinkID=204568"http://go.microsoft.com/fwlink/?LinkID=204568). 如需如何設定 Windows 防火牆來容納必要的連接埠資訊，請參閱[Windows 防火牆與 IPsec 原則部署逐步指南](http://go.microsoft.com/fwlink/?LinkID=204569)(http://go.microsoft.com/fwlink/?LinkID=204569)。  
  
## <a name="install-appropriate-com-and-msdtc-hotfix-rollup-packages"></a>安裝適當的 COM + 與 MSDTC hotfix 彙總套件  
 檢閱要安裝適當的 COM + 與 MS DTC hotfix 彙總套件封裝的下列資訊：  
  
-   MS DTC hotfix，請參閱 Microsoft Knowledge Base article978476 [「 Windows Server 2008 R2 MS DTC Hotfix 彙總套件 1 中修正 MS DTC 問題 」](http://go.microsoft.com/fwlink/?LinkID=204109) (http://go.microsoft.com/fwlink/?LinkID=204109)。  
  
-   可以藉由搜尋找到最新的 DTC hotfix 彙總套件知識庫文章[ http://support.microsoft.com ](http://go.microsoft.com/fwlink/?LinkID=96185) (http://go.microsoft.com/fwlink/?LinkID=96185)片語 （包括引號）：  
  
    ```  
    "MS DTC Hotfix Rollup Package"  
    ```  
  
     下列查詢會為您此搜尋。 選擇最新的密碼：   
    [http://support.microsoft.com/search/default.aspx?query="MS+DTC+Hotfix+Rollup+Package"](http://support.microsoft.com/search/default.aspx?query="MS+DTC+Hotfix+Rollup+Package")  
  
## <a name="use-the-interrupt-affinity-policy-tool-to-bind-network-adapter-interrupts-to-specific-processors-on-multiprocessor-computers"></a>使用繫結至多處理器電腦上的特定處理器的網路介面卡插斷的中斷親合性原則工具  
 中斷親合性原則 (IntPolicy) 是一種工具，可讓您 [繫結]，或變更給定的裝置 （例如網路介面卡） 的 CPU 相似性的插斷的特定處理器或多處理器電腦上的處理器。 這個繫結也稱為資料分割。 從特定網路介面卡插斷，以在多處理器電腦上的特定處理器的繫結會強制執行延遲程序呼叫 (Dpc) 和網路介面卡上指定之處理器的中斷服務常式 (Isr)。 請注意，無法在單一處理器電腦上設定中斷親和性。  
  
> [!NOTE]  
>  DPC 被定義為佇列通常會在稍後執行的核心模式函式呼叫。 ISR 定義為常式，其目的是為了服務時就會產生插斷的裝置。 如需有關延遲程序呼叫和中斷服務常式的詳細資訊，請參閱[Windows Driver Kit 文件](http://go.microsoft.com/fwlink/?LinkId=84418)(http://go.microsoft.com/fwlink/?LinkId=84418)。  
  
 ![插斷&#45;親和性原則工具](../technical-guides/media/interrupt-affinitypolicytool.gif "插斷 AffinityPolicyTool")  
中斷親合性原則工具  
  
 在 Windows Server 2008 基礎多處理器電腦，是將裝置插斷指派給任何可用的處理器插斷控制器的預設行為。 當網路連線和指定的網路介面卡的檔案伺服器工作階段會繫結/分割成一組特定的處理器上執行，而任何可用的處理器、 效能和延展性的相關聯的網路處理已獲得改善。 大型 BizTalk Server 方案通常採用多處理器的 SQL Server 電腦有多個網路介面卡的插斷繫結可能會特別有幫助。   
插斷繫結使用 IntPolicy 應該一律之前加以評估在測試環境中採用在生產環境中。 硬體、 作業系統和應用程式組態的測試環境應該接近實際執行環境十分接近。 這可讓您測試各種排列的插斷繫結，並決定範圍的插斷繫結就是增加效能。  
 我們建議您停用超執行緒支援超執行緒與 Cpu 的電腦上設定 IntPolicy 之前。 這可確保插斷，會指派給實體處理器，而不是邏輯處理器。 指派的中斷親和性參考相同的實體處理器的邏輯處理器不會提高效能，甚至可能會降低系統效能。    超連結"The"[中斷親合性原則工具](http://go.microsoft.com/fwlink/?LinkID=204111)(http://go.microsoft.com/fwlink/?LinkID=204111)從 WHDC 網站下載。  
  
## <a name="use-the-ntfs-file-system-on-all-volumes"></a>使用 NTFS 檔案系統上所有磁碟區  
 Windows Server 用來格式化磁碟機，包括 NTFS、 FAT 以及 FAT32 提供多個檔案系統類型。 NTFS 應該永遠選擇伺服器的檔案系統。  
NTFS FAT 及 FAT32 檔案系統上提供相當大的效能優點，應該只在 Windows 伺服器上使用。 此外，NTFS 會提供許多安全性、 延展性、 穩定性和可復原性的優點比 FAT 及 FAT32。  
在舊版 Windows 中，FAT 及 FAT32 通常實作的較小的磁碟區 (例如 < 500 MB)，所以通常較快，這種情況下。 磁碟儲存體價格比較便宜今天和作業系統和應用程式推入至最多的磁碟機容量，也不太可能，這類小的磁碟區將使用中。 FAT32 規模較大的磁碟區上會比 FAT 更好，但仍不適當的檔案系統的 Windows 伺服器。  
FAT 及 FAT32 通常已實作在過去因為被視為更輕鬆地復原，可以使用磁碟區有問題發生時的原生 DOS 工具管理。 現在，使用各種 NTFS 恢復能力工具整合到作業系統的原生，並且可做為可用的協力廠商公用程式，有不應再受到有效的引數，如未使用 NTFS 檔案系統。  
  
## <a name="do-not-use-ntfs-file-compression"></a>請勿使用 NTFS 檔案壓縮  
 雖然使用 NTFS 檔案系統壓縮是簡單的方法，以減少在磁碟區上的空間，它不適用於企業的檔案伺服器。 實作壓縮時，將不必要的額外負荷放置於磁碟的所有作業的 CPU，而且最好避免。 思考如何新增其他磁碟的選項，接近行的儲存體或考慮認真考慮檔案系統壓縮之前，先保存資料。  
  
## <a name="review-disk-controller-stripe-size-and-volume-allocation-units"></a>檢閱磁碟控制器等量磁碟區大小和磁碟區的配置單位  
 當設定磁碟機陣列和硬體磁碟機控制器內的邏輯磁碟機，並確認您符合控制器等量磁碟區大小與磁碟區將會格式化使用的配置單位大小。 這將確保磁碟讀取和寫入是最佳的效能並提供較佳的整體伺服器效能。  
設定較大的配置單位 （或叢集或區塊） 大小會導致效率越低，使用的磁碟空間，但也會提供更高磁碟 I/O 效能磁頭在每個讀取活動期間，可讀取更多資料。  
若要判斷最佳的設定來設定控制器，並使用磁碟格式化，您應該判斷磁碟子系統的類似檔案系統特性的伺服器上的平均磁碟傳輸大小。 使用 [Windows 效能監視器] 工具來監視邏輯磁碟物件計數器的 avg.Disk Bytes/Read 和 avg.磁碟 Bytes/Write 經過一段正常的活動，以協助您判斷要使用的最佳值。  
雖然較小的配置單位大小如果系統將用來存取許多小檔案或記錄可以保證，64 KB 配置單位大小可提供音效效能和在大部分情況下的 I/O 輸送量。 當磁碟負載增加時改善效能與調整的配置單位大小可以特別註明。  
  
> [!NOTE]  
>  格式命令列工具或 [磁碟管理] 工具，才能格式化磁碟區時，指定配置單位大小大於 4096 個位元組 (4 KB)。 Windows 檔案總管 只能將會格式化到此臨界值。 CHKDSK 命令可以用來確認目前的配置單位大小的磁碟區，不過它必須掃描整個磁碟區之前所需的資訊會顯示 （每個配置單位中方式顯示做為位元組）。  
  
## <a name="monitor-drive-space-utilization"></a>監視磁碟機空間使用量  
 較少的資料磁碟上有，它的運作速度。 這是因為資料寫入磁碟緣接近也重組磁碟機可能的話，因為這是這個磁碟的速度最快微調，並且得到最佳效能。  
磁碟搜尋時間是通常很長的時間比讀取或寫入活動。 如先前所述，資料一開始會寫入磁碟的邊緣。 磁碟儲存體增加和可用空間的需求會降低，因為資料會更接近寫入至磁碟的中心。 磁碟搜尋時間增加的前端移開邊緣，以尋找資料，並找到時，花較長的時間閱讀，阻礙磁碟 I/O 效能。  
這表示監視磁碟空間使用量會是重要不只是容量的原因，但效能也。  
根據經驗法則，為工作朝保持磁碟可用空間介於 20%到 25%的總磁碟空間的目標。 如果可用磁碟空間低於這個臨界值，則磁碟 I/O 效能將受到負面的影響。  
  
## <a name="implement-a-strategy-to-avoid-disk-fragmentation"></a>若要避免磁碟分散程度的策略實作  
 您在磁碟上，包括根磁碟機，以避免效能降低，定期執行重組工具 公用程式。 執行這個忙碌的磁碟上的每週。 磁碟重組工具會隨 Windows 一起安裝，並可以執行從排定的工作，以指定的間隔。  
  
## <a name="optimize-windows-server-performance-for-background-services"></a>將背景服務的 Windows Server 效能最佳化  
 BizTalk Server 處理序 (BTSNTSVC.exe) 會執行為背景服務。   
Windows Server 2008 會使用先佔式多工來排列優先順序就來參加 cpu 的處理序執行緒。 先佔式多工作是一種方法，會停止處理程序執行，並啟動另一個處理序時，作業系統會斟酌。 此配置會防止單一執行緒支配 CPU。  
切換執行到下一個處理序 CPU 稱為內容切換。 Windows 作業系統包含的設定，決定在 CPU 上執行，才能發生內容切換，並提供服務的下一個執行緒允許的個別執行緒的時間長度。 這段時間被指配量。 此設定可讓您選擇處理器配量的前景程式 」 與 「 背景服務之間共用的方式。 通常是伺服器不希望允許前景程式有更多的 CPU 時間比背景服務配置給它。 也就是說，所有應用程式，以及他們在伺服器上執行的程序，應考量相等的 CPU 時間。  
 若要增加等 BizTalk 主控件執行個體的背景服務的效能，請遵循下列步驟：  
  
1.  按一下**啟動**，按一下 **控制台**，然後按一下 **系統**。  
  
2.  按一下**進階**索引標籤，然後再按一下**設定**下**效能**。  
  
3.  按一下**進階**索引標籤上，按一下 **背景服務**，然後按一下 **確定**兩次。  
  
## <a name="disable-non-essential-services"></a>停用不必要的服務  
 Windows Server 2008 的預設安裝可讓數個 BizTalk Server 環境中可能不需要的服務。 每個執行中的服務會耗用系統資源，因此不需要的服務應停用來改善整體效能。  
停用服務時請務必小心。 仔細研究服務的目的之前停用服務，因為 Windows Server 需要的特定服務正在執行。 如果已停用 Windows Server 2008 所需的服務，作業系統而變得無法運作甚至無法開機。  
若要停用不需要專用的 BizTalk Server 的 Windows Server 2008 服務，請遵循下列步驟：  
  
1.  按一下  **啟動**, ，指向  **系統管理工具**, ，然後按一下  **電腦管理**。  
  
2.  在下**電腦管理 （本機）**，依序展開**服務和應用程式**，然後按一下 **服務**。  
    在**狀態**資料行中，執行每個服務會標示為 「 已啟動 」。 停止並停用任何不必要地，啟動的服務，例如下列服務不需要專用的 BizTalk 伺服器上：  
  
    -   警訊器  
  
    -   ClipBook  
  
    -   DHCP 伺服器  
  
    -   傳真服務  
  
    -   檔案複寫  
  
    -   紅外線監視器  
  
    -   網際網路連線共用  
  
    -   Messenger  
  
    -   NetMeeting 遠端桌面共用  
  
    -   網路 DDE  
  
    -   網路 DDE dsdm 」  
  
    -   NWLink NetBIOS  
  
    -   NWLink IPX/預存程序  
  
    -   列印多工緩衝處理器  
  
    -   Telephony  
  
    -   Telnet  
  
    -   不斷電供應系統  
  
3.  請注意取決於您想要停用每個服務的服務。 若要這樣做，請遵循下列步驟：  
  
    1.  按兩下您想要停用的服務。  
  
    2.  按一下 [ **相依性** ] 索引標籤。  
  
    3.  在**此服務相依於下列的系統元件**清單中，注意此服務依存於服務。  
  
    4.  在**依存於此服務的下列系統元件**清單中，請注意，無法啟動不需要這項服務，然後按一下 服務**確定**。  
  
4.  一次，停用您所選取每個服務。 若要這樣做，請遵循下列步驟：  
  
    1.  以滑鼠右鍵按一下您想要停用，然後按一下 的服務**屬性**。  
  
    2.  在**啟動類型**清單中，按一下**已停用**。  
  
    3.  如果您想要立即停止服務，按一下**停止**。  
  
         如果**停止其他服務**對話方塊出現時，請注意其他相依服務，將也停止，然後按一下 **是**，然後按一下 **確定**。  
  
5.  重複步驟 4，以停用其他非必要的服務。  
  
> [!NOTE]  
>  停用每個服務，以確定您未停用的服務，您要繼續使用之後，請測試正常運作的伺服器。   
> 如果伺服器是成員的 Windows Server 2008 的網域，這通常是 BizTalk Server，您必須有 TCP/IP helper 服務正確地套用到電腦上的 群組原則在系統上。   
> 當您停用 DHCP 用戶端時，DHCP 用戶端就會停止 DNS 動態更新通訊協定登錄，且需手動加入此用戶端的 DNS 伺服器的 DNS 記錄。  
  
## <a name="manually-load-microsoft-certificate-revocation-lists"></a>手動載入 Microsoft 憑證撤銷清單  
 當啟動.NET 應用程式時，.NET Framework 會嘗試下載的憑證撤銷清單 (CRL) 的任何帶正負號的組件。 如果您的系統並沒有直接存取網際網路，或限制存取 Microsoft.com 網域，這可能會延遲啟動 BizTalk Server。 若要避免這種延遲應用程式啟動時，您可以使用下列步驟手動下載並安裝的程式碼簽署您的系統上的憑證撤銷清單。  
  
1.  下載最新 CRL 更新從[ http://crl.microsoft.com/pki/crl/products/CodeSignPCA.crl ](http://go.microsoft.com/fwlink/?LinkID=117794) (http://go.microsoft.com/fwlink/?LinkID=117794)和[ http://crl.microsoft.com/pki/crl/products/CodeSignPCA2.crl ](http://go.microsoft.com/fwlink/?LinkId=117795) (http://go.microsoft.com/fwlink/?LinkId=117795)。  
  
2.  將 CodeSignPCA.crl 和 CodeSignPCA2.crl 檔移到隔離的系統。  
  
3.  從命令提示字元中，輸入下列命令以使用 certutil 公用程式以在步驟 1 中下載 CRL 更新本機憑證存放區：  
  
     certutil – addstore CA c:\CodeSignPCA.crl  
  
 CRL 檔案會定期更新，因此您應該考慮將設定重複的下載工作，並安裝 CRL 會更新。 檢視下次的更新、 按兩下.crl 檔案，然後檢視值**下一個更新**欄位。  
  
## <a name="synchronize-time-on-all-servers"></a>同步處理所有伺服器上的時間  
 多項作業涉及票證，回條和記錄依賴正在正確的本機系統時鐘。 這是特別在分散式環境中，系統之間的時間差異，可能會導致不同步的記錄檔或來為已過期，會拒絕的另一個系統所核發的票證或尚未生效。  
  
 如需有關設定伺服器自動同步處理時間的詳細資訊，請參閱[設定自動網域時間同步處理的用戶端電腦](http://go.microsoft.com/fwlink/?LinkId=99420)(http://go.microsoft.com/fwlink/?LinkId=99420)。  
  
## <a name="configure-the-windows-pagefile-for-optimal-performance"></a>設定 Windows 分頁檔，以獲得最佳效能  
 為了達到最佳效能，請遵循下列指導方針來設定 Windows 分頁檔 （分頁檔案）：  
  
1.  **將分頁檔移至不同的作業系統安裝以減少磁碟爭用並提高磁碟效能的實體磁碟機的實體磁區**-BizTalk Server 在電腦上，移動相關聯的效能改善分頁檔會有所不同的文件處理負載。 SQL Server 電腦上，將分頁檔移到不同的磁碟區會被視為最佳作法是在所有情況下，由於 SQL Server 磁碟大量本質。  
  
2.  **隔離到一或多個專用實體磁碟機設定為 RAID 0 （等量） 或 raid-1 （鏡像） 陣列，或在單一磁碟，而 RAID 沒有分頁檔**︰ 藉由使用專用的磁碟機陣列其中分頁檔。SYS 是整個磁碟區上唯一的檔案、 分頁檔將不會分散，這也會改善效能。 如同大部分的磁碟陣列，陣列的效能已獲得改善，為陣列中的實體磁碟數目會增加。 如果分頁檔分散在多個磁碟區上的磁碟陣列中的多個實體磁碟機之間，分頁檔大小應該在陣列中每個磁碟機上的相同大小。 在設定的磁碟陣列時，也建議使用具有相同的容量和速度的實體磁碟機。 請注意備援不通常需要分頁檔。  
  
3.  **未設定 RAID 5 陣列上的分頁檔**-不建議的 RAID 5 陣列上的分頁檔的組態，因為分頁檔案 」 活動的撰寫需要大量和 RAID 5 陣列，最好是讀取效能比寫入效能。  
  
4.  **如果您沒有將分頁檔移至實體磁碟區，除了在安裝作業系統的資源，設定分頁檔，在相同的邏輯磁碟區做為作業系統**-設定分頁檔，位於搜尋時間即是相同的實體磁碟上的作業系統將會增加磁碟的另一個邏輯磁碟區，並降低系統效能，因為磁碟機磁碟讀寫頭將會持續移動之間的磁碟區，或者存取分頁檔，作業系統檔案、 應用程式檔案和資料檔案。 此外，作業系統通常會安裝在實體磁碟，通常是最接近的實體磁碟外緣的第一個資料分割，而且已最佳化磁碟，其中是磁碟速度，而相關聯的效能。  
  
    > [!IMPORTANT]  
    >  如果您沒有移除分頁檔從開機磁碟分割，Windows 無法建立損毀傾印檔案 （記憶體。DMP) 中，核心模式停止寫入偵錯資訊就會發生錯誤。 如果您需要損毀傾印檔案，則您會不有任何選項，但若要將保留最少的分頁檔的實體記憶體 + 1 MB 的開機磁碟分割大小。  
  
5.  **手動設定分頁檔的大小**-手動設定分頁檔的大小通常提供較佳的效能比允許伺服器自動調整大小，或完全沒有分頁檔。 微調最佳做法是將初始 （最小值） 和分頁檔的大小上限設定設定為相同的值。 這可確保不處理資源遺失分頁檔可能會大量的動態調整大小。 假設系統上的記憶體資源已變得受限時，通常會發生此調整大小的活動，這是特別有用。 搜尋時間值也請確定磁碟上的分頁區域是一個單一的連續區域，改善磁碟相同的最小值和最大的分頁檔大小的設定。 Windows Server 2008 會自動建議分頁檔案大小總計等於 1.5 倍的已安裝的 RAM 數量。 在伺服器上有足夠磁碟空間，結合的所有磁碟上的分頁檔都應該設定兩次以獲得最佳效能的實體記憶體的最大。  
  
## <a name="remove-cpu-intensive-screen-savers"></a>移除需要大量 CPU 的螢幕保護裝置  
 並使用重要的系統資源，在執行時的 CPU 運算密集已知 3D 或 OpenGL 螢幕保護裝置。 建議您最好避免這些完全安裝在伺服器建置時，選擇，或如果已安裝加以移除。 基本的 Windows Server 2008 」 或空白的螢幕保護裝置會使用需要大量 CPU 的螢幕保護裝置的最佳替代方案。  
  
## <a name="see-also"></a>另請參閱  
 [最佳化作業系統效能](../technical-guides/optimizing-operating-system-performance.md)