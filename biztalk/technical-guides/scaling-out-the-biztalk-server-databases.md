---
title: 相應的放大，BizTalk Server 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18853ceb-7975-4c30-878f-6b162005f795
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68da9abc7291c61c0eb9fcdd6d82c6f87aad6e44
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980751"
---
# <a name="scaling-out-the-biztalk-server-databases"></a>向外擴充 BizTalk Server 資料庫
若要為 BizTalk Server 資料庫提供高可用性，設定兩部在 Windows 叢集中執行 SQL Server 的電腦。 這些電腦可以執行在主動/主動 」、 「 主動/被動或 「 主動/主動/被動 （需要三部電腦） 的備援性組態和資料可以儲存在共用的磁碟機 (例如 RAID 1 + 0 SCSI 磁碟陣列) 或存放區域網路 (SAN)。  
  
若 SQL Server 服務因故無法使用，資料庫叢集會將資源從主動電腦轉移到被動電腦。 在此容錯移轉程序期間，BizTalk Server 服務執行個體發生資料庫連接失敗並自動重新啟動以重新連接到資料庫。 正在運作的資料庫電腦 (先前為被動電腦) 會在容錯移轉期間獲得資源後，開始處理資料庫連接。  
  
叢集 BizTalk Server 資料庫中會討論[叢集 BizTalk Server 資料庫 2](../technical-guides/clustering-the-biztalk-server-databases2.md)。 本節著重於向外擴充 BizTalk Server 資料庫，以提供高可用性。  
  
## <a name="providing-high-availability-for-the-biztalk-messagebox-database"></a>為 BizTalk MessageBox 資料庫提供高可用性  
 本節提供如何設定高可用性的 BizTalk MessageBox 資料庫資訊。  
  
### <a name="running-multiple-messagebox-databases"></a>執行多個 MessageBox 資料庫  
若要增強的延展性及位址高 CPU 使用率在 MessageBox 資料庫的 SQL Server 電腦上的 BizTalk Server 資料庫，您可以設定跨多個 MessageBox 資料庫中儲存資料的 BizTalk Server。 當您執行「組態精靈」時，就會建立第一個 MessageBox 資料庫。 此 MessageBox 資料庫是主要 MessageBox 資料庫。 在 BizTalk Server 部署中有單一主要 MessageBox 資料庫。 主要 MessageBox 資料庫包含主要訂閱資訊，並將訊息路由至適當的 MessageBox 資料庫。 一般而言，您會想要專供路由專用主要 MessageBox 資料庫，並讓其他執行處理作業的 MessageBox 資料庫。 若要讓路由專用的 MessageBox 資料庫，選取**停用新訊息發佈**從 MessageBox 屬性在 BizTalk 管理主控台。  
  
 處理流程的 MessageBox 資料庫的範例如下所示：  
  
1. 當主要 MessageBox 資料庫收到新啟動訊息時 (商務程序的全新執行個體或訂閱訊息)，主要 MessageBox 資料庫會將啟動訊息分散至下一個可用的 MessageBox 資料庫。 例如，若您有一個主要 MessageBox 資料庫以及兩個 MessageBox 資料庫，則主要 MessageBox 資料庫會將第一個啟動訊息路由至 MessageBox 資料庫 1，第二個啟動訊息路由至 MessageBox 資料庫 2，第三個啟動訊息路由至 MessageBox 資料庫 1，以此輪流模式循環。 主要 MessageBox 資料庫使用內建邏輯來平衡負載，不需要其他負載平衡機制。  
  
2. 在主要 MessageBox 資料庫路由啟動訊息至特定 MessageBox 資料庫 (例如，MessageBox 資料庫 1) 後，商務程序就會進入記憶體並執行。  
  
3. 如果商務程序必須等待訊息時，等候時間會超過幾秒鐘的時間，則會將商務程序保存回 MessageBox 資料庫 1。 商務程序正在等待相互關聯訊息。  
  
4. 當相互關聯訊息到達主要 MessageBox 資料庫時，訊息引擎會執行查閱作業資料庫中的 MessageBox 資料庫，其中包含相互關聯訊息 （在此範例中，MessageBox 1） 的狀態。 主要 MessageBox 資料庫會將訊息傳遞到 MessageBox 資料庫，其中包含商務程序。  
  
5. 商務程序帶回記憶體以繼續處理直到完成為止，或直到它必須等待另一個相互關聯訊息。  
  
   BizTalk Server 會將所有狀態儲存在 MessageBox 資料庫中，而每個 MessageBox 資料庫包含不同商務程序的狀態資訊。 為了獲得可靠性，您必須叢集所有 MessageBox 資料庫，包括主要和次要 MessageBox 資料庫。  
  
   若要設定多個 MessageBox 資料庫，您可以使用 BizTalk Server 管理主控台來新增執行 SQL Server 的電腦。 從管理的觀點而言，您只需新增 MessageBox 資料庫。 BizTalk Server 會自動處理啟動訊息的循環散佈，並將相互關聯訊息傳送至正確的 MessageBox 資料庫。  
  
   如果您在環境中設定多個 MessageBox 資料庫您應該為 BizTalk Server 群組建立至少三個 MessageBox 資料庫，以及您應該停用主要 MessageBox 資料庫上的訊息發佈。 這項建議是由主要 MessageBox 資料庫的 MessageBox 資料庫之間路由訊息，因為新增其他 MessageBox 資料庫會產生額外負荷。 如果您只設定兩個 MessageBox 資料庫的大部分效益抵消其他 MessageBox 資料庫將偏移主要 MessageBox 資料庫為訊息路由傳送所耗用的額外負荷。  
  
> [!IMPORTANT]  
>  BizTalk Server 會將所有狀態儲存在 MessageBox 資料庫中，而每個 MessageBox 資料庫包含不同商務程序的狀態資訊。 為了獲得可靠性，您必須叢集所有 MessageBox 資料庫，包括主要和次要 MessageBox 資料庫。  
  
### <a name="providing-high-availability-for-multiple-messagebox-databases"></a>為多個 MessageBox 資料庫提供高可用性  
 雖然將 MessageBox 資料庫新增至 BizTalk Server 部署，可改善延展性，它不提供高可用性，因為每個 MessageBox 資料庫是唯一且獨立的而且有可能的單點失敗，BizTalk server環境。 新增備援包含為每個 MessageBox 資料庫設定伺服器叢集。 BizTalk Server 會將資料分散在多個 MessageBox 資料庫之間，這樣資料庫就不會共用資料或是在沒有伺服器叢集的情況下提供備援。  
  
## <a name="providing-high-availability-for-the-biztalk-tracking-database"></a>為 BizTalk 追蹤資料庫提供高可用性  
 視特定部署的需求而定，您可能會藉由將 BizTalk 追蹤資料庫隔離到個別的 SQL Server 電腦上，或建立主控件追蹤專用的不同 BizTalk 主控件，來提升追蹤效能。 下圖顯示具有兩個主控件執行個體和叢集的資料庫專用的追蹤主控件。  
  
 ![向外擴充追蹤資料庫](../technical-guides/media/4fc1d448-2a6c-4cea-ac17-96c1263dfb68.gif "4fc1d448-2a6c-4cea-ac17-96c1263dfb68")  
  
 若您的部署具有高輸送量且需要為這些訊息追蹤許多資料，追蹤的額外負擔可能會耗用許多執行 SQL Server 電腦的資源。 如果發生這種情況，而且持續有高比率的內送訊息，BizTalk Server 到達的點追蹤所需的資源，因為無法處理新訊息的訊息是大於執行其他的 BizTalk Server 所需的資源（例如接收訊息，並將它們保存到 MessageBox 資料庫） 的元件。  
  
 若要改善效能和安全性，建議您指派不包含任何其他項目 (例如，接收位置、協調流程或管線) 的主控件專供追蹤之用，並停用接收、處理和傳送主控件的追蹤。 若要為追蹤主控件提供高可用性，請為追蹤主控件建立一個以上的主控件執行個體。 請參閱[建立新的主機](../core/how-to-create-a-new-host.md)。
  
 每個 MessageBox 資料庫，BizTalk Server 僅使用一個追蹤主控件執行個體，以將訊息從 MessageBox 資料庫移到 BizTalk 追蹤資料庫 (BizTalkDTADb)。 若其他電腦執行追蹤主控件的執行個體，則 BizTalk Server 會自動將每個 MessageBox 資料庫的處理向外擴充至不同的追蹤主控件執行個體。 若 MessageBox 資料庫數目大於追蹤主控件執行個體數目，則一或多個追蹤主控件執行個體將服務一個以上的 MessageBox 資料庫。  
  
 若要提供 BizTalk 追蹤資料庫的高可用性，請使用 Windows 叢集來設定兩部以主動/被動組態執行 SQL Server 的資料庫電腦。  
  
## <a name="providing-high-availability-for-the-bam-databases"></a>為 BAM 資料庫提供高可用性  
 *商務活動監控*」 (BAM) 提供獨立於 IT 實作，或跨異質 IT 實作的商務程序可見性。 BAM SQL Server 資料庫 (BAM 星狀結構描述資料庫、BAM 主要匯入資料庫以及 BAM 封存資料庫) 與 BAM 分析資料庫會儲存異於操作監控資料的商務活動資料。 下圖顯示 BAM 資料庫基礎結構。  
  
 ![BAM 資料庫基礎結構](../technical-guides/media/769c3b7c-fe16-4260-967e-6af003c4f08d.gif "769c3b7c-fe16-4260-967e-6af003c4f08d")  
  
 若要確定 BAM 基礎結構為高度可用，請執行下列動作：  
  
-   **叢集 BAM 主要匯入資料庫和 BAM 分析資料庫。** BAM 主要匯入資料庫是商務活動監控系統的中心。 因此，使用 Windows 叢集讓此資料庫高度可用，並依照接下來的兩個建議以避免此資料庫被填滿，就很重要。 BAM 分析資料庫是一種 Analysis Services 資料庫，它儲存了商務分析師用以建立活動彙總和 OLAP Cube 的資料，因此，此資料庫的任何停機都會影響其產能。 雖然您不必叢集 BAM 封存資料庫，我們建議您監視事件記錄檔的錯誤，當 SQL Server Integration Services (SSIS) 套件執行，以確定已成功，傳輸資料，以及監視資料庫的大小因此，您可以取代它之前會填滿總。  
  
-   **定義線上視窗。** 若要提供更佳的效能並避免停機，BAM 分割區的設定，BAM 主要匯入資料庫中的資料載入資料表時已完成的活動，根據時間戳記。 BAM 藉由定期將完成的資料表與另一個格式完全相同的空資料表交換來完成此項工作。 BAM 在執行此動作後，其他完成的活動就會存放在新分割上 (資料表)，而 BAM 也會保留線上視窗所定義時間的舊分割。 您必須定義線上視窗以確保 BAM 主要匯入資料庫中的分割數目不會成長得太大。 如需排程線上視窗的詳細資訊，請參閱[封存主要匯入資料庫資料](../core/archiving-primary-import-database-data.md)。
  
-   **排程定期執行的 SSIS 套件。** 定義線上視窗可確保 BAM 主要匯入資料庫不會填滿舊活動的分割。 您也必須排程定期執行，來建立新的資料分割，活動資料，以及將資料從 BAM 主要匯入資料庫中的舊分割移到 BAM 封存資料庫的 SSIS 封裝。 如需有關如何排程 SSIS 套件的詳細資訊，請參閱[排程 SQL Server Integration Services 封裝](../core/scheduling-sql-server-integration-services-packages.md)。
  
-   **請仔細選擇少量資料的項目 （檢查點），並避免包含不必要資料的項目，定義活動時。**  
  
-   **了解排定和即時彙總設計彙總時之間的取捨。** 即時彙總會由 SQL Server 觸發程序自動維護且沒有延遲。 它們非常適合某些任務關鍵性的低延遲情況下，但它們產生效能成本，每當事件寫入 BAM 主要匯入資料庫。 排程彙總依賴排程 cube SSIS 套件部署到更新彙總資料。 它們的延遲等於或大於 SSIS 的排程間隔，但整體它們對效能的影響較小的 BAM 主要匯入資料庫。  
  
-   **如果您選擇排程彙總，請確定您排程 cube SSIS 以封存 SSIS 比更頻繁地執行。** 這是因為封存的 SSIS 不會移動已經處理進行排程的彙總到 BAM 封存資料庫的活動資料。  
  
-   **啟用 BAM 事件匯流排服務在多部電腦，以取得容錯移轉功能。**  
  
## <a name="providing-high-availability-for-the-other-biztalk-server-databases"></a>為其他 BizTalk 伺服器資料庫提供高可用性  
 若要為其他 BizTalk Server 資料庫提供高可用性，設定兩部在 Windows 叢集中執行 SQL Server 的電腦。 這些電腦可以在冗餘的主動/主動或主動/被動組態執行，而且可以將資料儲存在共用的磁碟機 (例如 RAID 1 + 0 SCSI 磁碟陣列) 或存放區域網路 (SAN)。  
  
## <a name="see-also"></a>另請參閱  
 [叢集 BizTalk Server 資料庫 2](../technical-guides/clustering-the-biztalk-server-databases2.md)