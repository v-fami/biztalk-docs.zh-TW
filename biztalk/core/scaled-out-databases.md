---
title: "向外延展資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, databases [BAM]
- databases [BAM], high availability
- Archive database [BAM]
- Analysis database [BAM], high availability
- high availability, databases [BAM]
- MessageBox database, master database
- scaling, databases [BAM]
- scaling, BizTalk Server
- MessageBox database, multiple databases
- MessageBox database, clustering
- databases [BAM], scaling
- MessageBox database, routing
- Tracking database, scaling
- Primary Import database [BAM], clustering
- high availability, MessageBox database
- databases [BAM], performance
- Star Schema database [BAM]
- MessageBox database, high availability
- messages, disabling
- MSMQT adapters, See MSMQ adapters
- clustering, Analysis database [BAM]
- Windows Message Queuing
- MessageBox database
- Analysis database [BAM], clustering
- DTS packages, scheduling
ms.assetid: e02edc0d-1c51-4b97-be04-0feb787089ac
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0af465c1cd77bfb96cc44e1a3209757ee13129be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-out-databases"></a>向外擴充的資料庫
若要提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的高可用性，請在 Windows 叢集中設定兩部執行 SQL Server 的電腦。 這些電腦可以主動/主動或主動/被動組態執行以做為備援，並將資料儲存在共用磁碟 (例如 RAID 1+0 SCSI 磁碟陣列) 或存放區域網路 (SAN) 上。  
  
 若 SQL Server 服務因故無法使用，資料庫叢集會將資源從主動電腦轉移到被動電腦。 在此容錯移轉程序期間，BizTalk Server 服務執行個體發生資料庫連接失敗並自動重新啟動以重新連接到資料庫。 正在運作的資料庫電腦 (先前為被動電腦) 會在容錯移轉期間獲得資源後，開始處理資料庫連接。  
  
## <a name="running-multiple-messagebox-databases"></a>執行多個 MessageBox 資料庫  
 若要提升 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的擴充性，您可以將 BizTalk Server 設定為跨多個 MessageBox 資料庫儲存資料。 當您執行「組態精靈」時，就會建立第一個 MessageBox 資料庫。 此 MessageBox 資料庫是主要 MessageBox 資料庫。 在 BizTalk Server 部署中有單一主要 MessageBox 資料庫。 主要 MessageBox 資料庫包含主要訂閱資訊，並將訊息路由至適當的 MessageBox 資料庫。 一般而言，您想要設定主要 MessageBox 僅供路由專用 (選取**停用新訊息發佈**)，並讓其他 MessageBox 資料庫執行處理。  
  
 當主要 MessageBox 資料庫收到新啟動訊息時 (商務程序的全新執行個體或訂閱訊息)，主要 MessageBox 資料庫會將啟動訊息分散至下一個可用的 MessageBox 資料庫。 例如，若您有一個主要 MessageBox 資料庫以及兩個 MessageBox 資料庫，則主要 MessageBox 資料庫會將第一個啟動訊息路由至 MessageBox 資料庫 1，第二個啟動訊息路由至 MessageBox 資料庫 2，第三個啟動訊息路由至 MessageBox 資料庫 1，以此輪流模式循環。 主要 MessageBox 資料庫使用內建邏輯來平衡負載，不需要其他負載平衡機制。  
  
 在主要 MessageBox 資料庫路由啟動訊息至特定 MessageBox 資料庫 (例如，MessageBox 資料庫 1) 後，商務程序就會進入記憶體並執行。 如果商務程序必須等待訊息時，等候時間會超過幾秒鐘的時間，則會將商務程序保存回 MessageBox 資料庫 1。 商務程序正在等待相互關聯訊息。 當相互關聯訊息到達主要 MessageBox 資料庫時，此訊息會在資料庫中查詢包含相互關聯訊息狀態的 MessageBox 資料庫 (在此範例中為 MessageBox 1)。 主要 MessageBox 資料庫接著會將訊息傳遞至包含商務程序的 MessageBox 資料庫。 商務程序會再度載入記憶體並繼續處理，直到它完成或直到它必須等待另一個相互關聯訊息。  
  
 BizTalk Server 會將所有狀態儲存在 MessageBox 資料庫中，而每個 MessageBox 資料庫包含不同商務程序的狀態資訊。 為了獲得可靠性，您必須叢集所有 MessageBox 資料庫，包括主要和次要 MessageBox 資料庫。  
  
 若要設定多個 MessageBox 資料庫，您可以使用 BizTalk 管理主控台來新增執行 SQL Server 的電腦。 從管理的觀點而言，您只需新增 MessageBox 資料庫。 BizTalk Server 會自動處理啟動訊息的循環散佈，並將相互關聯訊息傳送至正確的 MessageBox 資料庫。  
  
 若您在環境中設定多個 MessageBox 資料庫，您應該為 BizTalk Server 群組建立至少 3 個 MessageBox 資料庫，且您應停用主要 MessageBox 的訊息發佈。 此建議的理由是，因為新增其他 MessageBox 資料庫將會造成主要 MessageBox 資料庫的額外負擔，讓它必須在 MessageBox 資料庫之間路由訊息。 若您只設定 2 個 MessageBox 資料庫，則主要 MessageBox 路由訊息所耗用的額外負擔會抵消其他 MessageBox 資料庫所獲得的大部分效益。  
  
## <a name="providing-high-availability-for-multiple-messagebox-databases"></a>為多個 MessageBox 資料庫提供高可用性  
 雖然將 MessageBox 資料庫新增至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署可改善擴充性，不過它無法提供高可用性，因為每個 MessageBox 資料庫都是唯一且獨立的，而且有可能是 BizTalk Server 環境中的單一失敗點。 新增備援包含為每個 MessageBox 資料庫設定伺服器叢集。 BizTalk Server 會將資料分散在多個 MessageBox 資料庫之間，這樣資料庫就不會共用資料或是在沒有伺服器叢集的情況下提供備援。  
  
## <a name="providing-high-availability-for-the-biztalk-tracking-database"></a>為 BizTalk 追蹤資料庫提供高可用性  
 視特定部署的需求而定，您可能會藉由將 BizTalk 追蹤資料庫隔離到個別的 SQL Server 電腦上，或建立主控件追蹤專用的不同 BizTalk 主控件，來提升追蹤效能。 若您的部署具有高輸送量且需要為這些訊息追蹤許多資料，追蹤的額外負擔可能會耗用許多執行 SQL Server 電腦的資源。 若此情況發生且有高比率的內送訊息繼續，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將無法處理新訊息，因為追蹤訊息所需的資源大於執行其他 BizTalk Server 元件所需的資源 (例如，接收訊息並將它們保存到 MessageBox 資料庫)。  
  
 若要改善效能和安全性，建議您指派不包含任何其他項目 (例如，接收位置、協調流程或管線) 的主控件專供追蹤之用，並停用接收、處理和傳送主控件的追蹤。 若要為追蹤主控件提供高可用性，請為追蹤主控件建立一個以上的主控件執行個體。  
  
 對於每個 MessageBox 資料庫，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 僅使用一個追蹤主控件執行個體，將訊息從 MessageBox 資料庫移至 BizTalk 追蹤資料庫 (BizTalkDTADb)。 若其他電腦執行追蹤主控件的執行個體，則 BizTalk Server 會自動將每個 MessageBox 資料庫的處理向外擴充至不同的追蹤主控件執行個體。 若 MessageBox 資料庫數目大於追蹤主控件執行個體數目，則一或多個追蹤主控件執行個體將服務一個以上的 MessageBox 資料庫。  
  
 若要提供 BizTalk 追蹤資料庫的高可用性，請使用 Windows 叢集來設定兩部以主動/被動組態執行 SQL Server 的資料庫電腦。  
  
## <a name="providing-high-availability-for-the-bam-databases"></a>為 BAM 資料庫提供高可用性  
 商務活動監控 (BAM) 為獨立於 IT 實作之外或跨異質 IT 實作的商務程序提供可見性。 BAM SQL Server 資料庫 (BAM 星狀結構描述資料庫、BAM 主要匯入資料庫以及 BAM 封存資料庫) 與 BAM 分析資料庫會儲存異於操作監控資料的商務活動資料。 若要確定 BAM 基礎結構為高度可用，請執行下列動作：  
  
-   **叢集 BAM 主要匯入資料庫和 BAM 分析資料庫。** BAM 主要匯入資料庫是商務活動監控系統的中心。 因此，使用 Windows 叢集讓此資料庫高度可用，並依照接下來的兩個建議以避免此資料庫被填滿，就很重要。 BAM 分析資料庫是一種 Analysis Services 資料庫，它儲存了商務分析師用以建立活動彙總和 OLAP Cube 的資料，因此，此資料庫的任何停機都會影響其產能。 雖然您不必叢集 BAM 封存資料庫，不過仍建議您在執行「資料轉換服務」(DTS) 封裝時監控事件日誌是否有錯誤，以確定資料是否已成功傳輸，並監控資料庫的大小，以便在資料庫填滿前將它取代。  
  
-   **定義線上視窗。** 為了允許更高的效能並避免停機，BAM 會將 BAM 主要匯入資料庫中的資料分割成以活動完成的時間戳記為基礎的資料表。 BAM 藉由定期將完成的資料表與另一個格式完全相同的空資料表交換來完成此項工作。 BAM 在執行此動作後，其他完成的活動就會存放在新分割上 (資料表)，而 BAM 也會保留線上視窗所定義時間的舊分割。 您必須定義線上視窗以確保 BAM 主要匯入資料庫中的分割數目不會成長得太大。 如需排程線上視窗的詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 說明中的＜封存主要匯入資料庫資料＞。  
  
-   **排程定期執行的 DTS 封裝。** 定義線上視窗可確保 BAM 主要匯入資料庫不會填滿舊活動的分割。 您也必須排程定期執行的 DTS 封裝，以建立活動資料的新分割，並將資料從 BAM 主要匯入資料庫中的舊分割移至 BAM 封存資料庫。 如需排程 DTS 封裝的詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 說明中的＜排程 DTS 封裝＞。  
  
-   **請仔細選擇少量的資料項目 （檢查點），並避免包含不必要資料的項目，定義活動時。**  
  
-   **了解排程和即時彙總設計彙總時之間的取捨。** 即時彙總會由 SQL Server 觸發程序自動維護且沒有延遲。 這對於某些關鍵的低延遲實例很適合，不過每當事件寫入 BAM 主要匯入資料庫時就會產生效能成本。 排程彙總依賴排程 Cube DTS 封裝以更新其彙總資料。 它的延遲等於或大於 DTS 排程間隔，不過整體而言，它對於 BAM 主要匯入資料庫的效能影響比較小。  
  
-   **如果您選擇排程彙總，請確定您排程 cube DTS 比封存 DTS 更頻繁地執行。** 這是因為封存 DTS 不會將已經為排程彙總處理的活動資料移至 BAM 封存資料庫。  
  
-   **啟用 BAM 事件匯流排服務在多部電腦若要取得容錯移轉功能。**  
  
## <a name="providing-high-availability-for-the-other-biztalk-server-databases"></a>為其他 BizTalk 伺服器資料庫提供高可用性  
 若要提供其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的高可用性，請在 Windows 叢集中設定兩部執行 SQL Server 的電腦。 這些電腦可以主動/主動或主動/被動組態執行以做為備援，並將資料儲存在共用磁碟 (例如 RAID 1+0 SCSI 磁碟陣列) 或存放區域網路 (SAN) 上。  
  
## <a name="see-also"></a>另請參閱  
 [為 BizTalk 主控件提供高可用性](../core/providing-high-availability-for-biztalk-hosts.md)   
 [為 BizTalk Server 資料庫提供高可用性](../core/providing-high-availability-for-biztalk-server-databases.md)   
 [BizTalk Server 高可用性實例範例](../core/sample-biztalk-server-high-availability-scenarios.md)