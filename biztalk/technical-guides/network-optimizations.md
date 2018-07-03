---
title: 網路最佳化 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ff0392f-37ae-4ca6-8cc6-d53065de64c5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66419a1c864b4c22d4fb28a70c85cabf2eceb1a8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994791"
---
# <a name="network-optimizations"></a>網路最佳化
在 BizTalk Server 環境中的 BizTalk Server 電腦所在的 SQL Server 電腦不同，由 BizTalk Server 處理的每個訊息都需要透過網路通訊。 此通訊包括相當多的 BizTalk Server 電腦和 BizTalk Messagebox 資料庫、 BizTalk 管理資料庫、 BAM 資料庫和其他資料庫之間的流量。 在高負載情況下，此通訊可能會導致相當大的網路流量並成為瓶頸，特別是當尚未最佳化網路設定、 安裝沒有足夠的網路介面卡，或沒有足夠的網路頻寬可使用。  
  
 本主題提供的步驟相同的 HYPER-V 主機電腦上執行的 HYPER-V 虛擬機器之間的網路效能的改善，並提供改善網路效能的一般建議。  
  
> [!NOTE]  
>  最常見網路 IO 會成為瓶頸的指標是計數器 「 SQL Server： 等候 Statistics\Network IO 等候。 」 時的值**平均等候時間**此計數器是大於零的一或多個 SQL Server 電腦，則網路 IO 會成為瓶頸。  
  
## <a name="improving-network-performance-of-biztalk-server-on-hyper-v"></a>BizTalk server HYPER-V 上的改善網路效能  
  
### <a name="configure-hyper-v-virtual-machines-that-are-running-on-the-same-hyper-v-host-computer-to-use-a-private-virtual-network"></a>若要使用私人虛擬網路相同的 HYPER-V 主機電腦執行的 HYPER-V 虛擬機器設定  
 若要改善 HYPER-V 執行的虛擬機器之間的網路效能在相同的 HYPER-V 主機電腦，會建立私人虛擬網路和路由之間的網路流量透過私人虛擬網路的虛擬機器。  
  
##### <a name="create-a-private-virtual-network"></a>建立私人虛擬網路  
  
1.  按一下 **開始**，按一下**所有程式**。 按一下 **系統管理工具**，然後按一下**HYPER-V 管理員**。  
  
2.  在 HYPER-V 管理員 的左側窗格中，以滑鼠右鍵按一下**HYPER-V 管理員**，然後按一下**連接到伺服器**。  
  
3.  在 [**選取的電腦**] 對話方塊中，輸入 HYPER-V 主機電腦的名稱，然後按一下**確定**。  
  
4.  在 HYPER-V 管理員 的左側窗格中，以滑鼠右鍵按一下 HYPER-V 主機，然後按一下**虛擬網路管理員**。  
  
5.  在虛擬網路管理員中下,**您要建立何種虛擬網路？**，按一下**私人**，然後按一下 **新增**。  
  
6.  輸入新的虛擬網路的名稱，然後按一下**確定**。 現在可供此 Hyper-v 主機執行每個 HYPER-V 虛擬機器的虛擬網路。  
  
##### <a name="add-the-private-virtual-network-to-hyper-v-virtual-machines-running-on-the-hyper-v-host"></a>新增至 HYPER-V 虛擬機器在 HYPER-V 主機上執行的私人虛擬網路  
  
1.  按一下 **開始**，按一下**所有程式**。 按一下 **系統管理工具**，然後按一下**HYPER-V 管理員**。  
  
2.  在 HYPER-V 管理員 的左側窗格中，以滑鼠右鍵按一下**HYPER-V 管理員**，然後按一下**連接到伺服器**。  
  
3.  在 [**選取的電腦**] 對話方塊中，輸入 HYPER-V 主機電腦的名稱，然後按一下**確定**。  
  
4.  關閉任何正在執行的虛擬機器，您要新增私人虛擬網路，以滑鼠右鍵按一下虛擬機器，然後按一下**關閉**。  
  
5.  之後關閉虛擬機器，以滑鼠右鍵按一下 虛擬機器，然後**設定**變更虛擬機器的設定。  
  
6.  在  **< 電腦名稱 > 設定**對話方塊的 **新增硬體**，按一下以選取**網路介面卡**，然後按一下 **新增**.  
  
7.  在 **網路介面卡**組態頁面的 **網路：**，選取您稍早建立的私人虛擬網路，然後按一下**確定**。 您現在所做的私人虛擬網路可用來將可在下一次啟動虛擬機器之 HYPER-V 虛擬機器。  
  
8.  每個虛擬機器，您想要透過路由傳送網路流量的私人虛擬網路，重複上述步驟。  
  
9. 啟動您已加入私人虛擬網路的虛擬機器。 以滑鼠右鍵按一下每個虛擬機器，按一下 **啟動**。  
  
##### <a name="configure-each-virtual-machine-to-use-the-private-virtual-network"></a>設定每個虛擬機器使用私人虛擬網路  
  
1.  一旦啟動每部虛擬機器，私人虛擬網路為網路連線是存取虛擬機器。 若要使用 TCP/IPv4，每部虛擬機器上設定的網路連線，並指定設定的 TCP/IPv4 通訊協定。  
  
    1.  存取網路連接屬性頁面，請選取**網際網路通訊協定版本 4(TCP/IPv4)**，然後按一下**屬性**。  
  
    2.  按一下此選項按鈕旁**使用下列的 IP 位址**。  
  
2.  輸入的值**IP 位址**位址所識別的 「 RFC 1918 的私人 IP 位址的位址配置 」 欄位的私人 ip 位址範圍[ http://go.microsoft.com/fwlink/?LinkID=31904 ](http://go.microsoft.com/fwlink/?LinkID=31904)。  
  
3.  請記下您指定的 IP 位址您必須將此值產生關聯的 HOSTS 檔案項目稍後在此電腦的 NetBIOS 名稱。  
  
4.  輸入適當的值**子網路遮罩**欄位。  
  
    > [!NOTE]  
    >  填入 Windows 應該**子網路遮罩**欄位，使用適當的值會根據您輸入的值**IP 位址**欄位。  
  
5.  離開**預設閘道** 欄位留白，按一下**確定**，然後按一下**關閉**。  
  
6.  使用唯一的私人 IP 位址設定每個虛擬機器之後, 請使用 IP 位址和其他 HYPER-V 主機電腦上執行的虛擬機器的 NetBIOS 名稱更新每個虛擬機器上的主機檔案。 每個虛擬機器上時，應該儲存更新的主機檔案 %systemroot%\drivers\etc\ 資料夾。  
  
    > [!NOTE]  
    >  根據預設 Windows 會檢查本機 HOSTS 檔案，第一次將 NetBIOS 名稱解析，藉由更新每個虛擬機器上的主機檔案，使用唯一的私人 IP 位址的其他虛擬機器，因為這些機器之間的網路流量會現在透過路由傳送私人虛擬網路。  
  
### <a name="disable-tcp-offloading-for-the-virtual-machine-network-cards"></a>停用虛擬機器網路卡的 TCP 卸載  
 在編輯登錄，如 MSDN 主題 < 使用啟用和停用工作卸載 (NDIS 5.1) 登錄值 > 中所述[ http://go.microsoft.com/fwlink/?LinkId=147619 ](http://go.microsoft.com/fwlink/?LinkId=147619)停用 TCP 卸載每部虛擬機器上的網路卡。  
  
> [!IMPORTANT]  
>  不當使用登錄編輯，可能會造成問題，需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。 有關如何備份、 還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文章 < Microsoft Windows 登錄說明 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62729 ](http://go.microsoft.com/fwlink/?LinkId=62729)。  
  
## <a name="general-guidelines-for-improving-network-performance"></a>改善網路效能的一般指導方針  
 下列建議可用來提高網路效能：  
  
### <a name="add-additional-network-cards-to-computers-in-the-biztalk-server-environment"></a>將其他網路介面卡新增至 BizTalk Server 環境中的電腦  
 只為新增額外的硬碟可以改善磁碟效能、 新增其他網路介面卡可以改善網路效能。 如果 BizTalk Server 環境中的電腦上的網路卡已飽和，卡片是瓶頸，請考慮增加一或多個額外的網路介面卡，以改善效能。  
  
### <a name="implement-network-segmentation"></a>實作網路分割  
 請依照下列中的建議**子網路**一節在 「 BizTalk Server 資料庫最佳化 」 （英文） 白皮書[ http://go.microsoft.com/fwlink/?LinkID=101578 ](http://go.microsoft.com/fwlink/?LinkID=101578)。  
  
### <a name="where-possible-replace-hubs-with-switches"></a>可能的話，則將中樞取代參數  
 參數包含邏輯，以直接將來源和目的地之間的流量路由傳送而中樞使用廣播的模型，來路由傳送流量。 因此參數更有效率，而且提供更佳的效能。  
  
### <a name="remove-unnecessary-network-protocols"></a>移除不必要的網路通訊協定  
 Windows Server 的電腦有時會有更多的網路服務與安裝超過實際需要的通訊協定。 每個額外的網路用戶端、 服務或通訊協定置於其他額外負荷的系統資源。  
  
 此外，每個已安裝的通訊協定會產生網路流量。 藉由移除不必要的網路用戶端、 服務和通訊協定，系統資源供其他處理序可以避免過多的網路流量，必須交涉的網路繫結數目會減少為最小值。  
  
 若要查看目前已安裝的網路用戶端，通訊協定和服務，請遵循下列步驟：  
  
1. 按一下 **開始**，指向**設定**，然後按一下**控制台**。  
  
2. 按兩下**網路連線**來顯示電腦上的網路連線。  
  
3. 以滑鼠右鍵按一下**Local Area Connection** （或您的網路連線的項目），然後按一下**屬性**顯示網路連線 [內容] 對話方塊。  
  
4. 若要移除不必要的項目，請選取它，然後按一下**解除安裝**。 若要停用項目，只清除項目相關聯的核取方塊。  
  
   如果您不確定解除安裝項目連接的效果，然後停用項目，而不是解除安裝它。 停用項目，可讓您判斷哪些服務、 通訊協定和用戶端實際所需的系統上。 時已決定，停用項目在伺服器上有任何不良影響，可以再解除安裝項目。  
  
   在許多情況下，只有下列的三個元件是標準的 TCP/IP 網路上的作業需要：  
  
-   Client for Microsoft Networks  
  
-   檔案和 Printer Sharing for Microsoft Networks  
  
-   網際網路通訊協定 (TCP/IP)  
  
### <a name="network-adapter-drivers-on-all-computers-in-the-biztalk-server-environment-should-be-tuned-for-performance"></a>在 BizTalk Server 環境中的所有電腦上的網路介面卡驅動程式應為效能微調  
  
> [!IMPORTANT]  
>  在套用之前調整網路介面卡驅動程式，一律安裝在環境中的網路卡的最新網路介面卡裝置驅動程式。  
  
 調整網路介面卡裝置驅動程式，以最大化緩衝封包，可用的記憶體數量，傳入和傳出。 也最大化緩衝區計數，特別是傳輸緩衝區和聯合緩衝區。 預設值為這些參數，，及是否甚至提供，製造商與驅動程式版本之間的變更。 目標是由網路介面卡硬體，完成的工作最大化，並允許以減少網路流量高載和相關聯的壅塞的網路作業的最大可能的緩衝區空間。  
  
> [!NOTE]  
>  調整網路介面卡驅動程式的步驟視製造商而異。  
  
 請遵循下列步驟來存取中的網路介面卡設定[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]:  
  
1. 按一下 **開始**，然後按一下**控制台**。  
  
2. 按一下 **網路和網際網路**，然後按一下**網路和共用中心**。  
  
3. 按一下 **變更介面卡**，以滑鼠右鍵按一下**Local Area Connection** （或您的網路連線的名稱），然後按一下**屬性**。  
  
4. 在 **一般**索引標籤上，按一下**設定**。  
  
5. 按一下 [**進階**來存取屬性可設定的網路介面卡] 索引標籤。  
  
   BizTalk Server 環境中的每個網路介面卡應設定下列屬性：  
  
> [!NOTE]  
>  您套用這些設定包括個別的網路介面卡的設定彙總、 負載平衡或容錯移轉的網路介面卡組合集內每個實體網路介面卡。 某些小組的軟體，您可能需要將這些設定也套用至小組。 請注意，某些網路介面卡會自我調整可能不會提供手動設定參數的選項。  
  
- **電源選項**– 設定網路介面卡驅動程式，以防止關閉的網路介面卡，以節省電源的電源管理功能。 這項功能的用戶端電腦會很有用，但應該很少，如果曾，BizTalk Server 或 SQL Server 的電腦上使用。  
  
- **修正速度/雙工 （請勿使用自動）** -它是非常重要的是，會將網路速度、 雙工，以及流量控制參數設定為對應到交換器上設定它們所連接之。 這會降低定期 」 自動同步處理 」 這可能暫時需要離線連線的相符項目。  
  
- **最大聯合緩衝區**-對應暫存器是用來將實體位址轉換成支援匯流排精通的網路介面卡的虛擬位址的系統資源。 聯合緩衝區可使用的網路驅動程式，如果驅動程式用盡對應暫存器。 設定此值最高可能獲得最大效能。 在伺服器上具有有限的實體記憶體，這可能會有負面影響，因為聯合緩衝區會耗用系統記憶體。 在大部分系統上不過，最大值的設定可以套用而不會大幅降低可用的記憶體。  
  
- **最大傳輸/傳送描述元，以及傳送緩衝區**-此設定可讓您指定多少個傳輸控制緩衝區配置供使用的網路介面的驅動程式。 這可直接反映驅動程式可以有其 「 傳送 」 的佇列中未處理的封包數目。 設定此值最高可能獲得最大效能。 在伺服器上具有有限的實體記憶體，這可能會有負面的影響為傳送緩衝區會耗用系統記憶體。 在大部分系統上不過，最大值的設定可以套用而不會大幅降低可用的記憶體。  
  
- **最大接收緩衝區**-此設定指定將資料複製到通訊協定記憶體時，網路介面的驅動程式所使用的記憶體緩衝區數量。 它通常會設定預設會將相對較低的值。 設定此值最高可能獲得最大效能。 在伺服器上具有有限的實體記憶體，這可能會有負面影響，因為接收緩衝區會耗用系統記憶體。 在大部分系統上不過，最大值的設定可以套用而不會大幅降低可用的記憶體。  
  
- **所有在卸載選項**-在幾乎所有情況下，啟用網路介面卸載功能時，改善效能。 某些網路介面卡會提供不同的參數，以啟用或停用卸載，以傳送並接收流量。 將網路介面卡的工作從 CPU 卸載有助於減少 CPU 使用率，以改善整體系統效能的伺服器上。 Microsoft TCP/IP 傳輸可以卸載一或多個有適當的功能的網路介面卡的下列工作：  
  
  -   **總和檢查碼工作**-TCP/IP 傳輸可以卸載計算，並針對 IP 及 TCP 總和檢查碼驗證傳送和接收的網路介面卡，啟用此選項，如果網路介面卡驅動程式提供這項功能。  
  
  -   **IP 安全性工作**-TCP/IP 傳輸可以卸載的計算和驗證加密的總和檢查碼驗證標頭 (AH) 」 和 「 封裝安全承載 (ESP) 的網路介面卡。 加密和解密的網路介面卡的 ESP 裝載，也可以卸載 TCP/IP 傳輸。 如果網路介面卡驅動程式提供這項功能，請啟用這些選項。  
  
  -   **分割大型的 TCP 封包的**-TCP/IP 傳輸支援大型傳送卸載 (LSO)。 讓 LSO，使用 TCP/IP 傳輸可以卸載大型 TCP 封包的分割。  
  
  -   **堆疊卸載**– 具有適當的功能的網路介面卡可卸載整個網路堆疊。 如果網路介面卡驅動程式提供這項功能，請啟用此選項。  
  
- **Wake On LAN （除非正在使用） 已停用**– 設定網路介面卡驅動程式，若要停用喚醒上區域網路功能。 這項功能的用戶端電腦會很有用，但應該不常如果曾使用的 BizTalk Server 或 SQL Server 的電腦上。  
  
  如需有關如何調整效能的網路介面卡的詳細資訊，請參閱**網路裝置設定**一節在 「 BizTalk Server 資料庫最佳化 」 （英文） 白皮書[ http://go.microsoft.com/fwlink/?LinkID=101578 ](http://go.microsoft.com/fwlink/?LinkID=101578)。