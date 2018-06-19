---
title: 網路最佳化 |Microsoft 文件
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
ms.openlocfilehash: bbf4b0e8df9d8baa81a91576dc37fd89413714f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298758"
---
# <a name="network-optimizations"></a>網路最佳化
在 BizTalk Server 環境中的 BizTalk Server 電腦所在的 SQL Server 電腦不同，BizTalk Server 處理的每個訊息不需要透過網路通訊。 此通訊包括相當大的 BizTalk Server 電腦和 BizTalk Messagebox 資料庫、 BizTalk 管理資料庫、 BAM 資料庫中，與其他資料庫之間的流量。 在高負載情況下，這類通訊會造成相當大的網路流量而成為瓶頸，特別是當未最佳化的網路設定、 安裝沒有足夠的網路介面卡，或沒有足夠的網路頻寬可以使用。  
  
 本主題提供改善網路效能，在相同的 HYPER-V 主機電腦上執行的 HYPER-V 虛擬機器之間的步驟，並提供改善網路效能的一般建議。  
  
> [!NOTE]  
>  最常見網路 IO 是瓶頸的指標是計數器 「 SQL Server： 等候 Statistics\Network IO 等候 」。 當值**平均等候時間**在此計數器是大於零的一或多個 SQL Server 電腦，則網路 IO 是瓶頸。  
  
## <a name="improving-network-performance-of-biztalk-server-on-hyper-v"></a>HYPER-V 上的 BizTalk Server 改善網路效能  
  
### <a name="configure-hyper-v-virtual-machines-that-are-running-on-the-same-hyper-v-host-computer-to-use-a-private-virtual-network"></a>設定要使用私人虛擬網路相同的 HYPER-V 主機電腦執行的 HYPER-V 虛擬機器  
 若要改善網路效能執行的 HYPER-V 虛擬機器之間相同的 HYPER-V 主機電腦，會建立私人虛擬網路和路由網路流量透過私人虛擬網路的虛擬機器之間。  
  
##### <a name="create-a-private-virtual-network"></a>建立私人虛擬網路  
  
1.  按一下**啟動**，按一下 **所有程式**。 按一下**系統管理工具**，然後按一下  **HYPER-V 管理員**。  
  
2.  在 HYPER-V 管理員的左窗格中，以滑鼠右鍵按一下**HYPER-V 管理員**，然後按一下 **連接到伺服器**。  
  
3.  在**選取電腦**對話方塊中，輸入 HYPER-V 主機電腦的名稱，然後按一下**確定**。  
  
4.  在 HYPER-V 管理員的左窗格中，以滑鼠右鍵按一下 HYPER-V 主機，然後按一下**虛擬網路管理員**。  
  
5.  在虛擬網路管理員中下,**您要建立哪種虛擬網路？**，按一下**私用**，然後按一下 **新增**。  
  
6.  輸入新的虛擬網路的名稱，然後按一下**確定**。 現在執行這個 HYPER-V 主機每個 HYPER-V 虛擬機器可以使用虛擬網路。  
  
##### <a name="add-the-private-virtual-network-to-hyper-v-virtual-machines-running-on-the-hyper-v-host"></a>新增至 HYPER-V 虛擬機器在 HYPER-V 主機上執行的私人虛擬網路  
  
1.  按一下**啟動**，按一下 **所有程式**。 按一下**系統管理工具**，然後按一下  **HYPER-V 管理員**。  
  
2.  在 HYPER-V 管理員的左窗格中，以滑鼠右鍵按一下**HYPER-V 管理員**，然後按一下 **連接到伺服器**。  
  
3.  在**選取電腦**對話方塊中，輸入 HYPER-V 主機電腦的名稱，然後按一下**確定**。  
  
4.  關閉任何正在執行的虛擬機器，您要新增私人虛擬網路，請在虛擬機器上按一下滑鼠右鍵，然後按一下**關閉**。  
  
5.  之後關閉虛擬機器，以滑鼠右鍵按一下虛擬機器，然後**設定**變更虛擬機器的設定。  
  
6.  在 **< machine_name > 設定**對話方塊的 **新增硬體**，按一下以選取**網路介面卡**，然後按一下 **新增**.  
  
7.  在**網路介面卡**組態頁面上，在**網路：**，選取您稍早建立的私人虛擬網路，然後按一下**確定**。 您現在已經私人虛擬網路可供仍可在下一次啟動虛擬機器的 HYPER-V 虛擬機器。  
  
8.  重複上述步驟，每個虛擬機器，您想要透過私人虛擬網路的網路流量路由。  
  
9. 啟動新增私人虛擬網路的虛擬機器。 以滑鼠右鍵按一下每個虛擬機器，按一下 **啟動**。  
  
##### <a name="configure-each-virtual-machine-to-use-the-private-virtual-network"></a>若要使用私人虛擬網路的每個虛擬機器設定  
  
1.  一旦啟動每部虛擬機器後，私人虛擬網路為網路連線是可從虛擬機器存取。 若要使用 TCP/IPv4，每部虛擬機器上設定網路連線，並指定設定的 TCP/IPv4 通訊協定。  
  
    1.  存取網路連接屬性頁面，請選取**網際網路通訊協定版本 4(TCP/IPv4)**，然後按一下 **屬性**。  
  
    2.  按一下此選項按鈕旁的 **使用下列的 IP 位址**。  
  
2.  輸入一個值**IP 位址**欄位從範圍的私人 IP 位址中識別"RFC 1918 的私人 IP 位址的位址配置 」 在[http://go.microsoft.com/fwlink/?LinkID=31904](http://go.microsoft.com/fwlink/?LinkID=31904)。  
  
3.  請記下您所指定; 的 IP 位址您必須將此值與主機檔案項目稍後於此電腦的 NetBIOS 名稱產生關聯。  
  
4.  輸入適當的值，如**子網路遮罩**欄位。  
  
    > [!NOTE]  
    >  應填入 Windows**子網路遮罩**具有適當的值欄位會根據您輸入的值**IP 位址**欄位。  
  
5.  保留**預設閘道**欄位空白，按一下**確定**，然後按一下 **關閉**。  
  
6.  以唯一的私人 IP 位址設定每個虛擬機器之後, 每個虛擬機器上的主機檔案的 IP 位址和更新其他 HYPER-V 主機電腦上執行的虛擬機器的 NetBIOS 名稱。 每個虛擬機器上更新的主機檔案應該儲存 %systemroot%\drivers\etc\ 資料夾。  
  
    > [!NOTE]  
    >  根據預設 Windows 會檢查本機主機檔案第一次將 NetBIOS 名稱解析，藉由更新每部虛擬機器上的主機檔案與唯一的私人 IP 位址的其他虛擬機器，因為將現在透過路由這些電腦之間的網路流量私人虛擬網路。  
  
### <a name="disable-tcp-offloading-for-the-virtual-machine-network-cards"></a>停用 TCP 卸載，以將虛擬機器網路卡  
 在編輯登錄的 MSDN 主題 < 使用登錄值來啟用和停用工作 Offloading (NDIS 5.1) > 中所述[http://go.microsoft.com/fwlink/?LinkId=147619](http://go.microsoft.com/fwlink/?LinkId=147619)停用 TCP 卸載，以將每個虛擬機器上的網路卡。  
  
> [!IMPORTANT]  
>  不正確使用登錄編輯程式可能會造成問題，需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。 有關如何備份、 還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文件 < Microsoft Windows 登錄說明 >，網址[http://go.microsoft.com/fwlink/?LinkId=62729](http://go.microsoft.com/fwlink/?LinkId=62729)。  
  
## <a name="general-guidelines-for-improving-network-performance"></a>改善網路效能的一般指導方針  
 下列建議可提高網路效能：  
  
### <a name="add-additional-network-cards-to-computers-in-the-biztalk-server-environment"></a>將其他網路介面卡新增至 BizTalk Server 環境中的電腦  
 只要新增其他的硬碟可以改善磁碟效能、 新增其他網路介面卡可以改善網路效能。 如果飽和 BizTalk Server 環境中的電腦上的網路卡和智慧卡是瓶頸，請考慮增加一或多個額外的網路介面卡來改善效能。  
  
### <a name="implement-network-segmentation"></a>實作網路分割  
 請遵循建議**子網路**區段在 「 BizTalk Server 資料庫最佳化 」 白皮書[http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578)。  
  
### <a name="where-possible-replace-hubs-with-switches"></a>可能的話，則將中樞取代參數  
 參數包含邏輯來直接之間路由傳送流量的來源和目的地而集線器使用廣播的模型路由傳送流量。 因此參數更有效率，而且提供改進的效能。  
  
### <a name="remove-unnecessary-network-protocols"></a>移除不必要的網路通訊協定  
 Windows Server 電腦有時會有多個網路服務和安裝比實際需要的通訊協定。 每個額外的網路用戶端、 服務或通訊協定放置於其他負擔系統資源。  
  
 此外，每個已安裝的通訊協定會產生網路流量。 藉由移除不必要的網路用戶端、 服務與通訊協定，系統資源的其他程序，可以避免過多的網路流量和可必須交涉的網路繫結數目會減少到最低。  
  
 若要查看目前已安裝的網路用戶端，通訊協定和服務，請遵循下列步驟：  
  
1.  按一下**啟動**，指向 **設定**，然後按一下 **控制台**。  
  
2.  按兩下**網路連線**顯示電腦上的網路連線。  
  
3.  以滑鼠右鍵按一下**區域連線**（或您的網路連線的項目），然後按一下 **屬性**顯示網路連線 內容 對話方塊。  
  
4.  若要移除不必要的項目，請選取它，然後按一下**解除安裝**。 若要停用項目，只清除項目相關聯的核取方塊。  
  
 如果您不確定解除安裝的項目連接的效果，則停用項目，而不是解除安裝它。 停用項目，可讓您判斷哪些服務、 通訊協定和用戶端實際所需的系統上。 當已決定，停用項目在伺服器上有任何不良影響時，項目可以再解除安裝。  
  
 在許多情況下，只有下列三個元件是標準 TCP/IP 型網路上的作業需要：  
  
-   Client for Microsoft Networks  
  
-   檔案和 Printer Sharing for Microsoft Networks  
  
-   網際網路通訊協定 (TCP/IP)  
  
### <a name="network-adapter-drivers-on-all-computers-in-the-biztalk-server-environment-should-be-tuned-for-performance"></a>在 BizTalk Server 環境中的所有電腦上的網路介面卡驅動程式應微調的效能  
  
> [!IMPORTANT]  
>  在套用之前調整網路介面卡驅動程式，一律安裝在環境中的網路卡的最新網路介面卡裝置驅動程式。  
  
 調整網路介面卡裝置驅動程式，以最大化的封包緩衝區、 可用的記憶體數量，傳入和傳出。 也最大化緩衝區計數，尤其是傳輸緩衝區和聯合緩衝區。 預設值為這些參數，，及是否即使提供，而有所不同製造商與驅動程式版本。 目標是以最大化網路介面卡硬體，所完成的工作，並允許以降低網路流量爆發和相關聯的壅塞的網路作業的最大可能的緩衝區空間。  
  
> [!NOTE]  
>  來微調網路介面卡驅動程式的步驟會因製造商而異。  
  
 請遵循下列步驟來存取在網路介面卡設定[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]:  
  
1.  按一下**啟動**、，然後按一下 **控制台**。  
  
2.  按一下**網路和網際網路**，然後按一下 **網路和共用中心**。  
  
3.  按一下**變更介面卡設定**，以滑鼠右鍵按一下**區域連線**（或您的網路連線名稱），然後按一下 **屬性**。  
  
4.  在**一般**索引標籤上，按一下 **設定**。  
  
5.  按一下**進階**存取屬性可設定的網路介面卡 索引標籤。  
  
 BizTalk Server 環境中的每個網路介面卡應設定下列屬性：  
  
> [!NOTE]  
>  您套用這些設定包括個別網路介面卡設定為彙總、 負載平衡或容錯功能的網路介面卡組合集內每個實體網路介面卡。 某些小組軟體，您可能需要將這些設定也套用至小組。 請注意，某些網路介面卡會自我調整，而且可能不會提供手動設定參數的選項。  
  
-   **電源選項**– 設定網路介面卡驅動程式，以防止關閉網路介面卡以節省電源的電源管理功能。 這項功能可能適用於用戶端電腦，但是應該很少，如果曾，BizTalk Server 或 SQL Server 的電腦上使用。  
  
-   **固定速度/雙工 （不要使用 AUTO）** -它是非常重要的網路速度、 雙工和流程控制參數會設定為對應到交換器上設定它們所連接。 這會降低定期"自動同步處理 」 會可能暫時離線的連線次數。  
  
-   **最大聯合緩衝區**-對應暫存器是用來將實體位址轉換為支援匯流排主控的網路介面卡的虛擬位址系統資源。 聯合緩衝區可使用網路驅動程式，如果驅動程式用盡對應暫存器。 設定此值最高可達到最大效能。 在伺服器上具有有限的實體記憶體，這可能會有負聯合緩衝區的影響會耗用系統記憶體。 在大多數系統上不過，最大值的設定可以套用而不會大幅降低可用的記憶體。  
  
-   **最大傳輸/傳送描述元，以及傳送緩衝區**-此設定會指定多少個傳輸控制驅動程式會以網路介面供配置的緩衝區。 這會直接反映驅動程式可以有其 「 傳送 」 佇列中未處理的封包數目。 設定此值最高可達到最大效能。 在伺服器上具有有限的實體記憶體，這可能會有負面影響為傳送緩衝區耗用系統記憶體。 在大多數系統上不過，最大值的設定可以套用而不會大幅降低可用的記憶體。  
  
-   **最大接收緩衝區**-此設定指定的通訊協定的記憶體中複製資料時，網路介面驅動程式所使用的記憶體緩衝區數量。 它通常是相對較小的值預設設定。 設定此值最高可達到最大效能。 在伺服器上具有有限的實體記憶體，這可能會有負接收緩衝區的影響會耗用系統記憶體。 在大多數系統上不過，最大值的設定可以套用而不會大幅降低可用的記憶體。  
  
-   **所有在卸載選項**-幾乎在所有情況下啟用網路介面卸載功能時，改善效能。 某些網路介面卡提供不同的參數，以啟用或停用卸載，以將傳送並接收流量。 將工作從 CPU 的網路介面卡卸載，可協助伺服器以提升整體系統效能較低 CPU 使用率。 Microsoft TCP/IP 傳輸可以卸載一或多個要具有適當的功能的網路介面卡的下列工作：  
  
    -   **總和檢查碼工作**-TCP/IP 傳輸可以卸載計算，並為 IP 和 TCP 總和檢查碼驗證傳送和接收的網路介面卡，啟用此選項，如果網路介面卡驅動程式提供這項功能。  
  
    -   **IP 安全性工作**-計算和驗證的加密的總和檢查碼驗證標頭 (AH) 」 和 「 封裝安全承載 (ESP) 的網路介面卡，可以將卸載 TCP/IP 傳輸。 加密和解密的 ESP 裝載網路介面卡，也可以卸載 TCP/IP 傳輸。 如果網路介面卡驅動程式提供這項功能，請啟用這些選項。  
  
    -   **分割大型 TCP 封包的**-TCP/IP 傳輸支援大型傳送卸載 (LSO)。 LSO，使用 TCP/IP 傳輸可以卸載大型 TCP 封包的分割。  
  
    -   **堆疊卸載**– 具有適當的功能的網路介面卡可卸載的整個網路堆疊。 如果網路介面卡驅動程式提供這項功能，請啟用此選項。  
  
-   **線上醒機停用 （除非使用）** – 設定網路介面卡驅動程式停用喚醒上區域網路功能。 這項功能可用於用戶端電腦，但應該很少如果曾經使用 BizTalk Server 或 SQL Server 的電腦上。  
  
 如需調整效能的網路介面卡的詳細資訊，請參閱**網路裝置設定**區段在 「 BizTalk Server 資料庫最佳化 」 白皮書[http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578)。