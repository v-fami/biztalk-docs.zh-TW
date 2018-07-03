---
title: 作業系統最佳化 |Microsoft Docs
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
ms.openlocfilehash: f69f020cd728192308ebf160c4836599283fb412
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992919"
---
# <a name="operating-system-optimizations"></a>作業系統最佳化
本主題提供最佳化的效能建議[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]生產環境中使用的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 之後，會套用這些最佳化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已安裝和設定。  
  
## <a name="general-guidelines-for-improving-operating-system-performance"></a>改善作業系統效能的一般指導方針  
 下列建議可用來提高作業系統的效能：  
  
### <a name="install-the-latest-bios-storage-area-network-san-drivers-network-adapter-firmware-and-network-adapter-drivers"></a>安裝最新的 BIOS、 存放區域網路 (SAN) 驅動程式、 網路介面卡的韌體和網路介面卡驅動程式  
 硬體製造商會定期發行 BIOS、 韌體與驅動程式的更新可以改善效能和可用性相關聯的硬體。 請造訪硬體製造商的網站來下載並在 BizTalk Server 環境中的每一部電腦上套用下列的硬體元件的更新：  
  
1.  BIOS 更新  
  
2.  SAN 驅動程式 （如果使用 SAN）  
  
3.  NIC 韌體  
  
4.  NIC 驅動程式  
  
### <a name="assign-the-msdtc-log-file-directory-to-a-separate-dedicated-drive"></a>將 MSDTC 記錄檔目錄指派給另一個專用的磁碟機  
 在 BizTalk Server 環境中具有不同的 SQL Server 電腦上的多個 MessageBox 資料庫，會產生相關聯的 Microsoft Distributed Transaction Coordinator (MSDTC) 的額外負荷。 根據預設，MSDTC 記錄檔位於 %systemdrive%\windows\system32\msdtc 目錄執行 DTC 服務的電腦中。 若要降低 DTC 記錄可能形成效能瓶頸的可能性，請考慮將 MSDTC 記錄檔目錄移至快速的磁碟機。 若要變更 MSDTC 記錄檔目錄，請遵循下列步驟：  
  
1.  按一下**開始**，按一下**執行**，然後輸入**dcomcnfg**啟動**元件服務**管理主控台。  
  
2.  依序展開**元件服務**，展開**電腦**，以滑鼠右鍵按一下**我的電腦**，然後按一下**屬性**。  
  
3.  在 **我的電腦內容** 對話方塊中，按一下**MSDTC**  索引標籤。  
  
4.  在 **位置**編輯方塊底下**記錄資訊**，輸入您想要建立新的記錄檔 （例如 G:\Logs\DTCLog） 的路徑。  
  
5.  按一下 **重設記錄**，及系統會提示重新啟動服務。 按一下  **確定**以重新啟動 DTC 服務，然後按一下**確定**以確認重新啟動 MSDTC 服務。  
  
### <a name="configure-antivirus-software-to-avoid-real-time-scanning-of-biztalk-server-executables-and-file-drops"></a>若要避免的 BizTalk Server 可執行檔的即時掃描的防毒軟體設定和卸除檔案  
 防毒軟體的即時掃描的 BizTalk Server 可執行檔和任何資料夾或檔案共用受 BizTalk Server 接收位置可以對 BizTalk Server 效能產生負面的影響。 如果 BizTalk Server 電腦上安裝防毒軟體，停用即時掃描任何 BizTalk Server 所參考的非可執行檔的檔案類型的接收位置 （通常是。XML，但也可能是.csv、.txt 等等。)若要排除的 BizTalk Server 可執行檔掃描的防毒軟體設定和  
  
### <a name="disable-intrusion-detection-network-scanning-between-computers-in-the-biztalk-server-environment"></a>停用掃描中的 BizTalk Server 環境的電腦之間的入侵偵測網路  
 入侵偵測軟體可以變慢，或甚至防止在網路上的 有效的通訊。 如果安裝入侵偵測軟體時，停用網路掃描 BizTalk Server 電腦與外部資料存放庫 (SQL Server) 電腦之間，或傳訊服務 （訊息佇列、 WebSphere MQSeries 等） 的電腦。  
  
### <a name="defragment-all-disks-in-the-biztalk-server-environment-on-a-regular-basis"></a>定期執行的 BizTalk Server 環境中的所有磁碟進行磁碟都重組  
 BizTalk Server 環境中的過多的磁碟分散程度，會對效能產生負面影響。 請遵循下列步驟來重組磁碟，BizTalk Server 環境中：  
  
1.  所有磁碟進行磁碟都重組 (本機和 SAN/NAS) 定期排程在離峰磁碟重組。  
  
2.  重組 Windows 分頁檔，並預先配置 BizTalk Server 環境中的每個磁碟的主檔案表格，以提高整體系統效能。  
  
    > [!NOTE]  
    >  使用可在 PageDefrag 公用程式[ http://go.microsoft.com/fwlink/?LinkId=108976 ](http://go.microsoft.com/fwlink/?LinkId=108976)重組 Windows 分頁檔，並預先配置主檔案表格。  
  
### <a name="if-antivirus-software-is-installed-on-the-sql-server-computers-disable-real-time-scanning-of-data-and-transaction-files"></a>如果防毒軟體已安裝的 SQL Server 電腦上，停用的資料和交易檔的即時掃描  
 即時掃描 SQL Server 資料和交易檔案 （.mdf、.ndf、.ldf 和.mdb），可以增加磁碟 I/O 競爭，並減少 SQL Server 效能。 請注意，SQL Server 資料和交易檔的名稱可能會不同，BizTalk Server 環境之間。 如需使用預設的 BizTalk Server 組態所建立的資料和交易檔的詳細資訊，請參閱[最佳化檔案群組的資料庫](http://msdn.microsoft.com/library/ee377060\(v=bts.70\).aspx)。  
  
### <a name="configure-msdtc-for-biztalk-server"></a>BizTalk server 設定 MSDTC  
 請檢閱下列資訊來設定 MSDTC 的 BizTalk Server:  
  
-   若要在 BizTalk Server 上設定 MSDTC，請參閱 「 啟用 DTC 在本機主機伺服器 > 一節的 BizTalk Server 2010 安裝指南[ http://go.microsoft.com/fwlink/?LinkID=191321 ](http://go.microsoft.com/fwlink/?LinkID=191321)。  
  
-   在 < 疑難排解 MSDTC 問題 > [ http://go.microsoft.com/fwlink/?LinkID=202142 ](http://go.microsoft.com/fwlink/?LinkID=202142)。  
  
### <a name="configure-firewalls-for-biztalk-server"></a>設定 BizTalk Server 的連線  
  
> [!NOTE]  
>  此步驟才需要如果一或多個防火牆位於 BizTalk Server 環境中的位置。  
  
 請檢閱下列資訊來設定 BizTalk Server 的連線：  
  
-   「 需要的連接埠的 BizTalk Server 」 在[ http://go.microsoft.com/fwlink/?LinkId=101607 ](http://go.microsoft.com/fwlink/?LinkId=101607)。  
  
-   「 如何設定 RPC 動態連接埠配置以使用防火牆 」 在[ http://go.microsoft.com/fwlink/?LinkID=76145 ](http://go.microsoft.com/fwlink/?LinkID=76145)。  
  
### <a name="use-the-ntfs-file-system-on-all-volumes"></a>使用 NTFS 檔案系統上所有磁碟區  
 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 提供了多個檔案系統類型的格式化磁碟機，包括 NTFS、 FAT、 和 FAT32。 NTFS 應該一律是選擇伺服器的檔案系統。[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]  
  
 NTFS 上的 FAT 和 FAT32 檔案系統的相當大的效能優點，並應只在 Windows 伺服器上。 此外，NTFS 會提供許多安全性、 延展性、 穩定性和恢復能力的優點，比 FAT 和 FAT32。  
  
 在舊版的 Windows，FAT 和 FAT32 通常實作的較小的磁碟區 (例如 < 500 MB) 因為它們通常是在此情況下更快。 使用磁碟儲存體比較便宜今天和作業系統和應用程式推送到最多的磁碟機容量，就不太可能，會使用這類小的磁碟區。 FAT32 進行較大的磁碟區上的擴充優於 FAT，但仍不是適當的檔案系統的 Windows 伺服器。  
  
 FAT 和 FAT32 通常已實作在過去，視為已更輕鬆地復原，可以使用磁碟區有問題發生時的原生 DOS 工具管理。 目前有各種 NTFS 恢復能力工具建置兩者原生作業系統，而隨附提供的協力廠商公用程式，應該不會再有的有效引數不使用 NTFS 檔案系統。  
  
### <a name="do-not-use-ntfs-file-compression"></a>請勿使用 NTFS 檔案壓縮  
 雖然使用 NTFS 檔案系統壓縮是簡單的方法，以減少磁碟區上的空間，不過它不是適用於企業的檔案伺服器。 實作壓縮時，將不必要的額外負荷放置於磁碟的所有作業的 CPU，而且最好避免。 考慮新增其他磁碟的選項、 近線的儲存體或認真考慮檔案系統壓縮之前，先封存資料，請考慮。  
  
### <a name="review-disk-controller-stripe-size-and-volume-allocation-units"></a>檢閱磁碟控制器等量磁碟區大小和磁碟區配置單位  
 設定磁碟機陣列和硬體磁碟機控制器內的邏輯磁碟機可確保當您比對控制器等量大小與磁碟區將會格式化使用的配置單位大小。 這會確保磁碟讀取和寫入達到最佳效能將會提供更好的整體伺服器效能。  
  
 設定較大的配置單位 （或叢集或區塊） 大小會造成太有效率的方式，使用的磁碟空間，但也會提供較高磁碟 I/O 效能，因為磁碟讀寫頭可以讀取的每個活動期間讀取更多資料。  
  
 若要判斷最佳的設定來設定控制站和格式化磁碟，您應該判斷磁碟子系統的類似檔案系統特性的伺服器上的平均磁碟傳輸大小。 使用[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]效能監視器工具，以監視邏輯磁碟物件計數器的 avg.Disk Bytes/Read 和 avg.經過一段正常的活動，以協助您判斷要使用的最佳值磁碟 Bytes/Write。  
  
 雖然較小的配置單位大小可能很多小型檔案或記錄，如果將存取系統獲得保證，音效的效能和 I/O 輸送量在大部分情況下，也會提供為 64 KB 配置單位大小。 磁碟負載增加時，就可以特別注意與微調的配置單位大小的效能改進。  
  
> [!NOTE]  
>  「 格式化 」 命令列工具或 「 磁碟管理工具，才能格式化磁碟區時指定的配置單位大小大於 4096 個位元組 (4 KB)。 Windows 檔案總管只會將格式化到此臨界值。 CHKDSK 命令可用來確認目前的配置單位大小的磁碟區，但必須掃描整個磁碟區之前所需的資訊顯示 （每個配置單位中方式顯示為位元組）。  
  
### <a name="monitor-drive-space-utilization"></a>監視磁碟機空間使用量  
 磁碟上的較少資料，速度就會運作。 這是因為也重組磁碟機寫入資料之外部邊緣的磁碟，盡可能接近因為這是此磁碟會旋轉的速度最快，且會產生最佳效能。  
  
 磁碟搜尋時間是通常很長的時間比讀取或寫入活動。 如先前所述，資料一開始會寫入磁碟的外邊緣。 因為增加磁碟的儲存和可用空間在需求降低時，資料會更接近寫入至磁碟的中心。 磁碟搜尋時間增加前端的移離 edge 中，尋找資料，而且當找到，花較長的時間閱讀，阻礙磁碟 I/O 效能。  
  
 這表示監視磁碟空間使用量是重要的不只是因為容量之故，但效能也。  
  
 根據經驗法則，努力的目標是將保持磁碟可用空間介於 20%到 25%的總磁碟空間。 如果可用磁碟空間低於這個臨界值，則磁碟 I/O 效能將受到負面的影響。  
  
### <a name="implement-a-strategy-to-avoid-disk-fragmentation"></a>實作策略，以避免磁碟分散程度  
 在您的磁碟，包括根磁碟機，以避免效能降低，定期執行磁碟重組工具公用程式。 執行此每週在忙碌的磁碟上。 磁碟重組工具會隨 Windows Server，而且可以執行從排定的工作，以指定的間隔。  
  
### <a name="optimize-windows-server-performance-for-background-services"></a>將背景服務的 Windows Server 效能最佳化  
 BizTalk Server 程序 (BTSNTSVC.exe) 會執行為背景服務。 根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]已調整的應用程式的最佳效能而非用於背景服務。  
  
 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 若要設定將由 CPU 中一起參與的處理序執行緒的優先權，會使用先佔式多工。 先佔式多工是方法，藉此處理程序執行停止和啟動另一個處理序時，作業系統會斟酌。 此配置可防止單一執行緒佔用 CPU。  
  
 切換執行到下一個處理序 CPU 稱為內容切換。 Windows 作業系統包含設定會決定多久允許個別的執行緒發生內容切換和下一個執行緒都服務之前，在 CPU 上執行。 這段時間被指一個配量。 此設定可讓您選擇 處理器的配量的前景程式 」 和 「 背景服務之間共用的方式。 通常伺服器最好不允許前景程式有更多的 CPU 時間，比背景服務配置給它。 也就是說，所有的應用程式和其在伺服器上執行的程序應該考量等於 CPU 時間。  
  
 若要增加效能，例如 BizTalk 主控件執行個體的背景服務，請遵循下列步驟：  
  
1.  按一下 **開始**，按一下**控制台**，然後按一下**系統**。  
  
2.  按一下 **進階**索引標籤，然後再按一下**設定**之下**效能**。  
  
3.  按一下 **進階**索引標籤上，按一下**背景服務**，然後按一下**確定**兩次。  
  
### <a name="manually-load-microsoft-certificate-revocation-lists"></a>手動載入 Microsoft 憑證撤銷清單  
 當啟動.NET 應用程式，.NET Framework 會嘗試下載的憑證撤銷清單 (CRL) 的任何已簽署的組件。 如果您的系統並沒有直接存取網際網路，或限制存取 Microsoft.com 網域，這可能會延遲啟動 BizTalk Server。 若要避免這種延遲應用程式啟動時，您可以使用下列步驟，手動下載並安裝的程式碼簽署您的系統上的 憑證撤銷清單。  
  
1. 下載最新的 CRL 更新，從[ http://crl.microsoft.com/pki/crl/products/CodeSignPCA.crl ](http://go.microsoft.com/fwlink/?LinkID=117794)並[ http://crl.microsoft.com/pki/crl/products/CodeSignPCA2.crl ](http://go.microsoft.com/fwlink/?LinkId=117795)。  
  
2. CodeSignPCA.crl 和 CodeSignPCA2.crl 檔案移到隔離的系統。  
  
3. 在命令提示字元中，輸入下列命令，以使用 certutil 的公用程式來更新本機憑證存放區與步驟 1 中下載 CRL:  
  
    certutil – addstore CA c:\CodeSignPCA.crl  
  
   CRL 檔案會定期更新，因此您應該考慮將重複的下載工作，並安裝 CRL 更新。 若要檢視的下一步 的更新時間、 按兩下.crl 檔案，並檢視的值**下一步 更新**欄位。  
  
### <a name="synchronize-time-on-all-servers"></a>同步處理所有伺服器上的時間  
 包含票證的許多作業，回條和記錄依賴在正確的本機系統時鐘。 這是特別有用，在分散式環境中，系統之間的時間不一致，可能會造成不同步的記錄檔或為已過期，另一個遭到拒絕的一個系統所核發的票證或尚未生效。  
  
 如需有關如何設定伺服器自動同步處理時間的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=99420 ](http://go.microsoft.com/fwlink/?LinkId=99420)。  
  
### <a name="configure-the-windows-pagefile-for-optimal-performance"></a>設定 Windows 分頁檔，以獲得最佳效能  
 為了達到最佳效能，請遵循下列指導方針來設定 Windows 分頁檔 （分頁檔案）：  
  
1.  **將分頁檔移至不同的作業系統安裝以減少磁碟爭用並提高磁碟效能的實體磁碟機的實體磁區**-BizTalk Server 在電腦上，與移動相關聯的效能改善分頁檔會有所不同的文件處理負載。 SQL Server 電腦上，將分頁檔移至不同的磁碟區會被視為最佳做法是在所有情況下，由於磁碟需要大量的 SQL Server。  
  
2.  **隔離至一或多個專用的實體磁碟機為 RAID 0 （串接） 或 raid-1 （鏡像） 陣列或單一磁碟，而不需要 RAID 上設定分頁檔**-使用專用的磁碟機陣列其中分頁檔。SYS 是整個磁碟區上唯一的檔案、 分頁檔將不會變得分散，這也會改善效能。 如同大部分的磁碟陣列，陣列的效能已獲得改善，因為陣列中的實體磁碟數目會增加。 如果分頁檔分散在多個磁碟陣列中的實體磁碟機上的多個磁碟區，分頁檔大小應該在陣列中每個磁碟機上的相同大小。 當設定的磁碟陣列，也建議使用具有相同的容量和速度的實體磁碟機。 請注意，備援並不會讓分頁檔通常需要。  
  
3.  **未設定 RAID 5 陣列上的分頁檔**-不建議的 RAID 5 陣列上的分頁檔的設定，因為分頁檔案 」 活動的撰寫大量和 RAID 5 陣列更適合的讀取效能比寫入效能。  
  
4.  **如果您沒有資源，以將分頁檔移至實體磁碟區，除了在安裝作業系統，設定分頁檔，位於相同的邏輯磁碟區做為作業系統**-設定分頁檔，位於這是在相同的實體磁碟上，作業系統會增加磁碟的另一個邏輯磁碟區搜尋時間並降低系統效能，因為磁碟機磁碟讀寫頭將會持續移動之間的磁碟區，或者存取的分頁檔作業系統檔案、 應用程式檔案和資料檔案。 此外，作業系統通常會安裝在第一個資料分割的實體磁碟，通常是最接近的實體磁碟外緣，其中是磁碟速度，而相關聯的效能是最適合的磁碟。  
  
    > [!IMPORTANT]  
    >  如果您從開機分割區中移除分頁檔，Windows 無法建立損毀傾印檔案 （記憶體。DMP) 會在其中寫入偵錯資訊的核心模式停止發生錯誤。 如果您需要的損毀傾印檔，則您會不有任何選項，但若要將保留最少的分頁檔大小的實體記憶體 + 1 MB 的開機磁碟分割。  
  
5.  **手動設定分頁檔的大小**-手動設定分頁檔的大小通常提供較佳的效能比可讓伺服器在自動調整大小或完全具有沒有分頁檔。 微調最佳做法是將初始 （最低要求） 和分頁檔的大小上限設定為相同的值。 這可確保沒有處理資源遺失分頁檔，它可以是需要大量的動態調整大小。 假設已經成為限制系統上的記憶體資源時，通常就會發生此調整大小的活動，這是特別有用。 設定相同的最小值和最大分頁檔案大小值也可確保在磁碟上的 [分頁] 區域是一個單一的連續區域，改善磁碟搜尋時間。