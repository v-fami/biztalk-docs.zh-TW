---
title: 作業系統最佳化 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af2e77d0-d69b-4ae4-b689-96831fc4deed
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15ef1c8d5860b6e9bd3683551096c947de8c7a42
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976692"
---
# <a name="operating-system-optimizations"></a>作業系統最佳化
本主題提供最佳化的效能的建議事項[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用於實際執行電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 這些最佳化會在之後套用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已經安裝及設定。  
  
## <a name="general-guidelines-for-improving-operating-system-performance"></a>一般指導方針來改善作業系統效能  
 下列建議可以用於增加作業系統效能：  
  
### <a name="install-the-latest-bios-storage-area-network-san-drivers-network-adapter-firmware-and-network-adapter-drivers"></a>安裝最新的 BIOS、 存放區域網路 (SAN) 驅動程式、 網路介面卡的韌體和網路介面卡驅動程式  
 硬體製造商會定期發行 BIOS、 韌體與驅動程式可以改善效能和可用性的相關聯的硬體的更新。 請造訪硬體製造商的網站下載並套用每一部 BizTalk Server 環境中的下列硬體元件的更新：  
  
1.  BIOS 更新  
  
2.  SAN 驅動程式 （如果使用 SAN）  
  
3.  NIC 韌體  
  
4.  NIC 驅動程式  
  
### <a name="assign-the-msdtc-log-file-directory-to-a-separate-dedicated-drive"></a>將 MSDTC 記錄檔目錄指派給另一個專用的磁碟機  
 在 BizTalk Server 環境中具有不同的 SQL Server 電腦上的多個 MessageBox 資料庫，造成相關聯的 Microsoft Distributed Transaction Coordinator (MSDTC) 的額外負擔。 根據預設，MSDTC 記錄檔位於執行 DTC 服務之電腦的 %systemdrive%\windows\system32\msdtc 目錄中。 若要減輕 DTC 記錄可能會成為效能瓶頸的可能性，請考慮將 MSDTC 記錄檔目錄移至快速的磁碟機。 若要變更 MSDTC 記錄檔目錄，請遵循下列步驟：  
  
1.  按一下**啟動**，按一下 **執行**，然後輸入**dcomcnfg**啟動**元件服務**管理主控台。  
  
2.  展開**元件服務**，依序展開**電腦**，以滑鼠右鍵按一下**我的電腦**，然後按一下 **屬性**。  
  
3.  在**我的電腦內容**對話方塊中，按一下 [ **MSDTC** ] 索引標籤。  
  
4.  在**位置**編輯方塊下方**記錄資訊**，輸入您想要建立新的記錄檔 （例如 G:\Logs\DTCLog） 的路徑。  
  
5.  按一下**重設記錄**，並將系統會提示您重新啟動服務。 按一下**確定**以重新啟動 DTC 服務，然後按一下**確定**以確認重新啟動 MSDTC 服務。  
  
### <a name="configure-antivirus-software-to-avoid-real-time-scanning-of-biztalk-server-executables-and-file-drops"></a>若要避免的 BizTalk Server 可執行檔的即時掃描的防毒軟體設定和檔案會卸除  
 防毒軟體的即時掃描的 BizTalk Server 可執行檔和任何資料夾或檔案共用受 BizTalk Server 接收位置可以對 BizTalk Server 效能產生負面的影響。 如果 BizTalk Server 電腦上已安裝防毒軟體，停用即時掃描任何 BizTalk Server 所參考的非可執行檔的檔案類型的接收位置 （通常是。XML，但也可能是.csv 或.txt 等。)和防毒軟體設定為排除掃描的 BizTalk Server 可執行檔  
  
### <a name="disable-intrusion-detection-network-scanning-between-computers-in-the-biztalk-server-environment"></a>停用 BizTalk Server 環境中的電腦之間正在掃描的入侵偵測網路  
 入侵偵測軟體可以變慢或甚至阻止在網路上的有效通訊。 如果安裝入侵偵測軟體時，停用 BizTalk Server 電腦與外部資料儲存機制 (SQL Server) 電腦之間的掃描，或訊息 （訊息佇列、 WebSphere MQSeries 等） 的服務電腦的網路。  
  
### <a name="defragment-all-disks-in-the-biztalk-server-environment-on-a-regular-basis"></a>重組以規則為基礎的 BizTalk Server 環境中的所有磁碟  
 BizTalk Server 環境中的過多的磁碟分散程度將會對效能產生負面影響。 遵循下列步驟來重組 BizTalk Server 環境中的磁碟：  
  
1.  重組所有磁碟 (本機和 SAN/NAS) 上定期排程離峰時間磁碟重組。  
  
2.  重組 Windows 分頁檔，並預先配置 BizTalk Server 環境中的每個磁碟的主檔案表格，以提高整體系統效能。  
  
    > [!NOTE]  
    >  使用 PageDefrag 公用程式可在[http://go.microsoft.com/fwlink/?LinkId=108976](http://go.microsoft.com/fwlink/?LinkId=108976)重組 Windows 分頁檔，並預先配置主檔案表格。  
  
### <a name="if-antivirus-software-is-installed-on-the-sql-server-computers-disable-real-time-scanning-of-data-and-transaction-files"></a>如果 SQL Server 電腦上已安裝防毒軟體，停用的資料和交易檔的即時掃描  
 SQL Server 資料和交易檔案 （.mdf、.ndf、.ldf 和.mdb） 的即時掃描，可以增加磁碟 I/O 競爭，並減少 SQL Server 效能。 請注意，SQL Server 資料和交易檔的名稱可能會不同，BizTalk Server 環境之間。 如需建立預設的 BizTalk Server 組態資料和交易檔的詳細資訊，請參閱[最佳化的檔案群組的資料庫](http://msdn.microsoft.com/library/ee377060\(v=bts.70\).aspx)。  
  
### <a name="configure-msdtc-for-biztalk-server"></a>設定 MSDTC 的 BizTalk Server  
 檢閱下列資訊來設定 MSDTC 的 BizTalk Server:  
  
-   若要在 BizTalk Server 上設定 MSDTC，請參閱啟用 DTC 上的 < 本機主機 Server > 一節的 BizTalk Server 2010 安裝指南[http://go.microsoft.com/fwlink/?LinkID=191321](http://go.microsoft.com/fwlink/?LinkID=191321)。  
  
-   疑難排解 MSDTC 問題 > 在[http://go.microsoft.com/fwlink/?LinkID=202142](http://go.microsoft.com/fwlink/?LinkID=202142)。  
  
### <a name="configure-firewalls-for-biztalk-server"></a>設定 BizTalk Server 的連線  
  
> [!NOTE]  
>  這是步驟，只需要一個或多個防火牆是否在 BizTalk Server 環境中的位置。  
  
 檢閱下列資訊來設定 BizTalk Server 的連線：  
  
-   「 要求連接埠的 BizTalk Server 」 在[http://go.microsoft.com/fwlink/?LinkId=101607](http://go.microsoft.com/fwlink/?LinkId=101607)。  
  
-   「 如何設定 RPC 動態連接埠配置以使用防火牆 」 在[http://go.microsoft.com/fwlink/?LinkID=76145](http://go.microsoft.com/fwlink/?LinkID=76145)。  
  
### <a name="use-the-ntfs-file-system-on-all-volumes"></a>使用 NTFS 檔案系統上所有磁碟區  
 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]提供用來格式化磁碟機，包括 NTFS、 FAT 以及 FAT32 的多個檔案系統類型。 NTFS 應該永遠選擇伺服器的檔案系統。[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]  
  
 NTFS FAT 及 FAT32 檔案系統上提供相當大的效能優點，應該只在 Windows 伺服器上使用。 此外，NTFS 會提供許多安全性、 延展性、 穩定性和可復原性的優點比 FAT 及 FAT32。  
  
 在舊版 Windows 中，FAT 及 FAT32 通常實作的較小的磁碟區 (例如 < 500 MB)，所以通常較快，這種情況下。 磁碟儲存體價格比較便宜今天和作業系統和應用程式推入至最多的磁碟機容量，也不太可能，這類小的磁碟區將使用中。 FAT32 規模較大的磁碟區上會比 FAT 更好，但仍不適當的檔案系統的 Windows 伺服器。  
  
 FAT 及 FAT32 通常已實作在過去因為被視為更輕鬆地復原，可以使用磁碟區有問題發生時的原生 DOS 工具管理。 現在，使用各種 NTFS 恢復能力工具整合到作業系統的原生，並且可做為可用的協力廠商公用程式，有不應再受到有效的引數，如未使用 NTFS 檔案系統。  
  
### <a name="do-not-use-ntfs-file-compression"></a>請勿使用 NTFS 檔案壓縮  
 雖然使用 NTFS 檔案系統壓縮是簡單的方法，以減少在磁碟區上的空間，它不適用於企業的檔案伺服器。 實作壓縮時，將不必要的額外負荷放置於磁碟的所有作業的 CPU，而且最好避免。 思考如何新增其他磁碟的選項，接近行的儲存體或考慮認真考慮檔案系統壓縮之前，先保存資料。  
  
### <a name="review-disk-controller-stripe-size-and-volume-allocation-units"></a>檢閱磁碟控制器等量磁碟區大小和磁碟區的配置單位  
 當設定磁碟機陣列和硬體磁碟機控制器內的邏輯磁碟機，並確認您符合控制器等量磁碟區大小與磁碟區將會格式化使用的配置單位大小。 這將確保磁碟讀取和寫入是最佳的效能並提供較佳的整體伺服器效能。  
  
 設定較大的配置單位 （或叢集或區塊） 大小會導致效率越低，使用的磁碟空間，但也會提供更高磁碟 I/O 效能磁頭在每個讀取活動期間，可讀取更多資料。  
  
 若要判斷最佳的設定來設定控制器，並使用磁碟格式化，您應該判斷磁碟子系統的類似檔案系統特性的伺服器上的平均磁碟傳輸大小。 使用[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]監視邏輯磁碟物件計數器的平均效能監視工具Disk Bytes/Read 和 avg.磁碟 Bytes/Write 經過一段正常的活動，以協助您判斷要使用的最佳值。  
  
 雖然較小的配置單位大小如果系統將用來存取許多小檔案或記錄可以保證，64 KB 配置單位大小可提供音效效能和在大部分情況下的 I/O 輸送量。 當磁碟負載增加時改善效能與調整的配置單位大小可以特別註明。  
  
> [!NOTE]  
>  格式命令列工具或 [磁碟管理] 工具，才能格式化磁碟區時，指定配置單位大小大於 4096 個位元組 (4 KB)。 Windows 檔案總管 只能將會格式化到此臨界值。 CHKDSK 命令可以用來確認目前的配置單位大小的磁碟區，不過它必須掃描整個磁碟區之前所需的資訊會顯示 （每個配置單位中方式顯示做為位元組）。  
  
### <a name="monitor-drive-space-utilization"></a>監視磁碟機空間使用量  
 磁碟上的較少資料，速度它的運作。 這是因為以及重組磁碟機，資料會寫入緣磁碟盡可能接近因為這是這個磁碟的速度最快微調，並且得到最佳效能。  
  
 磁碟搜尋時間是通常很長的時間比讀取或寫入活動。 如先前所述，資料一開始會寫入磁碟的邊緣。 磁碟儲存體增加和可用空間的需求會降低，因為資料會更接近寫入至磁碟的中心。 磁碟搜尋時間增加的前端移開邊緣，以尋找資料，並找到時，花較長的時間閱讀，阻礙磁碟 I/O 效能。  
  
 這表示監視磁碟空間使用量會是重要不只是容量的原因，但效能也。  
  
 根據經驗法則，為工作朝保持磁碟可用空間介於 20%到 25%的總磁碟空間的目標。 如果可用磁碟空間低於這個臨界值，則磁碟 I/O 效能將受到負面的影響。  
  
### <a name="implement-a-strategy-to-avoid-disk-fragmentation"></a>若要避免磁碟分散程度的策略實作  
 您在磁碟上，包括根磁碟機，以避免效能降低，定期執行重組工具 公用程式。 執行這個忙碌的磁碟上的每週。 磁碟重組工具會隨 Windows Server，且可以執行從排定的工作，以指定的間隔。  
  
### <a name="optimize-windows-server-performance-for-background-services"></a>將背景服務的 Windows Server 效能最佳化  
 BizTalk Server 處理序 (BTSNTSVC.exe) 會執行為背景服務。 根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]設定來調整應用程式的最佳效能而非背景服務。  
  
 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]會使用先佔式多工來排列優先順序就來參加 cpu 的處理序執行緒。 先佔式多工作是一種方法，會停止處理程序執行，並啟動另一個處理序時，作業系統會斟酌。 此配置會防止單一執行緒支配 CPU。  
  
 切換執行到下一個處理序 CPU 稱為內容切換。 Windows 作業系統包含的設定，決定在 CPU 上執行，才能發生內容切換，並提供服務的下一個執行緒允許的個別執行緒的時間長度。 這段時間被指配量。 此設定可讓您選擇處理器配量的前景程式 」 與 「 背景服務之間共用的方式。 通常是伺服器不希望允許前景程式有更多的 CPU 時間比背景服務配置給它。 也就是說，所有應用程式，以及他們在伺服器上執行的程序，應考量相等的 CPU 時間。  
  
 若要增加等 BizTalk 主控件執行個體的背景服務的效能，請遵循下列步驟：  
  
1.  按一下**啟動**，按一下 **控制台**，然後按一下 **系統**。  
  
2.  按一下**進階**索引標籤，然後再按一下**設定**下**效能**。  
  
3.  按一下**進階**索引標籤上，按一下 **背景服務**，然後按一下 **確定**兩次。  
  
### <a name="manually-load-microsoft-certificate-revocation-lists"></a>手動載入 Microsoft 憑證撤銷清單  
 當啟動.NET 應用程式時，.NET Framework 會嘗試下載的憑證撤銷清單 (CRL) 的任何帶正負號的組件。 如果您的系統並沒有直接存取網際網路，或限制存取 Microsoft.com 網域，這可能會延遲啟動 BizTalk Server。 若要避免這種延遲應用程式啟動時，您可以使用下列步驟手動下載並安裝的程式碼簽署您的系統上的憑證撤銷清單。  
  
1.  下載最新 CRL 更新從[http://crl.microsoft.com/pki/crl/products/CodeSignPCA.crl](http://go.microsoft.com/fwlink/?LinkID=117794)和[http://crl.microsoft.com/pki/crl/products/CodeSignPCA2.crl](http://go.microsoft.com/fwlink/?LinkId=117795)。  
  
2.  將 CodeSignPCA.crl 和 CodeSignPCA2.crl 檔移到隔離的系統。  
  
3.  從命令提示字元中，輸入下列命令以使用 certutil 公用程式以在步驟 1 中下載 CRL 更新本機憑證存放區：  
  
     certutil – addstore CA c:\CodeSignPCA.crl  
  
 CRL 檔案會定期更新，因此您應該考慮將設定重複的下載工作，並安裝 CRL 會更新。 檢視下次的更新、 按兩下.crl 檔案，然後檢視值**下一個更新**欄位。  
  
### <a name="synchronize-time-on-all-servers"></a>同步處理所有伺服器上的時間  
 多項作業涉及票證，回條和記錄依賴正在正確的本機系統時鐘。 這是特別在分散式環境中，系統之間的時間差異，可能會導致不同步的記錄檔或來為已過期，會拒絕的另一個系統所核發的票證或尚未生效。  
  
 如需有關設定伺服器自動同步處理時間的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=99420](http://go.microsoft.com/fwlink/?LinkId=99420)。  
  
### <a name="configure-the-windows-pagefile-for-optimal-performance"></a>設定 Windows 分頁檔，以獲得最佳效能  
 為了達到最佳效能，請遵循下列指導方針來設定 Windows 分頁檔 （分頁檔案）：  
  
1.  **將分頁檔移至不同的作業系統安裝以減少磁碟爭用並提高磁碟效能的實體磁碟機的實體磁區**-BizTalk Server 在電腦上，移動相關聯的效能改善分頁檔會有所不同的文件處理負載。 SQL Server 電腦上，將分頁檔移到不同的磁碟區會被視為最佳作法是在所有情況下，由於 SQL Server 磁碟大量本質。  
  
2.  **隔離到一或多個專用實體磁碟機設定為 RAID 0 （等量） 或 raid-1 （鏡像） 陣列，或在單一磁碟，而 RAID 沒有分頁檔**︰ 藉由使用專用的磁碟機陣列其中分頁檔。SYS 是整個磁碟區上唯一的檔案、 分頁檔將不會分散，這也會改善效能。 如同大部分的磁碟陣列，陣列的效能已獲得改善，為陣列中的實體磁碟數目會增加。 如果分頁檔分散在多個磁碟區上的磁碟陣列中的多個實體磁碟機之間，分頁檔大小應該在陣列中每個磁碟機上的相同大小。 在設定的磁碟陣列時，也建議使用具有相同的容量和速度的實體磁碟機。 請注意備援不通常需要分頁檔。  
  
3.  **未設定 RAID 5 陣列上的分頁檔**-不建議的 RAID 5 陣列上的分頁檔的組態，因為分頁檔案 」 活動的撰寫需要大量和 RAID 5 陣列，最好是讀取效能比寫入效能。  
  
4.  **如果您沒有將分頁檔移至實體磁碟區，除了在安裝作業系統的資源，設定分頁檔，在相同的邏輯磁碟區做為作業系統**-設定分頁檔，位於搜尋時間即是相同的實體磁碟上的作業系統將會增加磁碟的另一個邏輯磁碟區，並降低系統效能，因為磁碟機磁碟讀寫頭將會持續移動之間的磁碟區，或者存取分頁檔，作業系統檔案、 應用程式檔案和資料檔案。 此外，作業系統通常會安裝在實體磁碟，通常是最接近的實體磁碟外緣的第一個資料分割，而且已最佳化磁碟，其中是磁碟速度，而相關聯的效能。  
  
    > [!IMPORTANT]  
    >  如果您沒有移除分頁檔從開機磁碟分割，Windows 無法建立損毀傾印檔案 （記憶體。DMP) 中，核心模式停止寫入偵錯資訊就會發生錯誤。 如果您需要損毀傾印檔案，則您會不有任何選項，但若要將保留最少的分頁檔的實體記憶體 + 1 MB 的開機磁碟分割大小。  
  
5.  **手動設定分頁檔的大小**-手動設定分頁檔的大小通常提供較佳的效能比允許伺服器自動調整大小，或完全沒有分頁檔。 微調最佳做法是將初始 （最小值） 和分頁檔的大小上限設定設定為相同的值。 這可確保不處理資源遺失分頁檔可能會大量的動態調整大小。 假設系統上的記憶體資源已變得受限時，通常會發生此調整大小的活動，這是特別有用。 設定相同的最小值和最大頁面的檔案大小值也可確保在磁碟上的分頁區域是一個單一的連續區域，改善磁碟搜尋時間。