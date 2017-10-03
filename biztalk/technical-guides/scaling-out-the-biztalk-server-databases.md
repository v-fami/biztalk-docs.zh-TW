---
title: "調整 BizTalk Server 資料庫的跨 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18853ceb-7975-4c30-878f-6b162005f795
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3116b7aae087e74ade089c8020a7d35c883cd2e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-out-the-biztalk-server-databases"></a>向外延展 BizTalk Server 資料庫
若要提供高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，設定兩部電腦執行[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]或[!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)]Windows 叢集中。 這些電腦可以主動/主動、 主動/被動或主動/主動/被動 （需要三部電腦） 中執行的備援性組態可以共用的磁碟機上儲存資料 (例如 RAID 1 + 0 SCSI 磁碟陣列) 或存放區域網路 (SAN)。  
  
 如果[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]服務變為無法使用，因為任何原因，資料庫叢集資源從作用中的電腦傳輸到被動電腦。 在容錯移轉過程中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務執行個體發生資料庫連線失敗，並自動重新啟動以重新連接到資料庫。 正在運作的資料庫電腦 (先前為被動電腦) 會在容錯移轉期間獲得資源後，開始處理資料庫連接。  
  
 叢集[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫述[叢集 BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md)。 本節著重於向外延展[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫提供高可用性。  
  
## <a name="providing-high-availability-for-the-biztalk-messagebox-database"></a>為 BizTalk MessageBox 資料庫提供高可用性  
 本節提供如何設定 BizTalk MessageBox 資料庫的高可用性的資訊。  
  
### <a name="running-multiple-messagebox-databases"></a>執行多個 MessageBox 資料庫  
 若要增強的延展性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫和 MessageBox 資料庫上位址高 CPU 使用率[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦，您可以設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]跨多個 MessageBox 資料庫中儲存資料。 當您執行「組態精靈」時，就會建立第一個 MessageBox 資料庫。 此 MessageBox 資料庫是主要 MessageBox 資料庫。 沒有單一的主要 MessageBox 資料庫中您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。 主要 MessageBox 資料庫包含主要訂閱資訊，並將訊息路由至適當的 MessageBox 資料庫。 一般而言，您會想要指派至僅供路由，主要 MessageBox 資料庫，並讓其他 MessageBox 資料庫執行處理。 若要讓僅供路由至 MessageBox 資料庫時，選取**停用新訊息發佈**從 BizTalk 管理主控台中的 MessageBox 內容。  
  
 MessageBox 資料庫的處理流程的範例如下所示：  
  
1.  當主要 MessageBox 資料庫收到新啟動訊息時 (商務程序的全新執行個體或訂閱訊息)，主要 MessageBox 資料庫會將啟動訊息分散至下一個可用的 MessageBox 資料庫。 例如，若您有一個主要 MessageBox 資料庫以及兩個 MessageBox 資料庫，則主要 MessageBox 資料庫會將第一個啟動訊息路由至 MessageBox 資料庫 1，第二個啟動訊息路由至 MessageBox 資料庫 2，第三個啟動訊息路由至 MessageBox 資料庫 1，以此輪流模式循環。 主要 MessageBox 資料庫使用內建邏輯來平衡負載，不需要其他負載平衡機制。  
  
2.  在主要 MessageBox 資料庫路由啟動訊息至特定 MessageBox 資料庫 (例如，MessageBox 資料庫 1) 後，商務程序就會進入記憶體並執行。  
  
3.  如果商務程序必須等待訊息時，等候時間會超過幾秒鐘的時間，則會將商務程序保存回 MessageBox 資料庫 1。 商務程序正在等待相互關聯訊息。  
  
4.  相互關聯訊息到達主要 MessageBox 資料庫時，訊息引擎會執行查閱作業資料庫中的 MessageBox 資料庫，其中包含相互關聯訊息 （在此範例中，MessageBox 1） 的狀態。 主要 MessageBox 資料庫會將訊息傳遞到 MessageBox 資料庫包含商務程序。  
  
5.  商務程序將返回到記憶體中繼續處理，直到完成為止，或直到它必須等待另一個相互關聯訊息。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]儲存在 MessageBox 資料庫中的所有狀態和每個 MessageBox 資料庫包含不同商務程序的狀態資訊。 為了獲得可靠性，您必須叢集所有 MessageBox 資料庫，包括主要和次要 MessageBox 資料庫。  
  
 若要設定多個 MessageBox 資料庫，您使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來新增正在執行的電腦[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]或[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]。 從管理的觀點而言，您只需新增 MessageBox 資料庫。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]自動處理啟動訊息的循環配置資源發佈，並將相互關聯訊息傳送至正確的 MessageBox 資料庫。  
  
 如果您在環境中設定多個 MessageBox 資料庫，您就應該建立至少三個 MessageBox 資料庫，使您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組，而且應該停用主要 MessageBox 資料庫上的訊息發佈。 這項建議進行新增其他 MessageBox 資料庫將會造成額外負荷，因為主要 MessageBox 資料庫的 MessageBox 資料庫之間路由訊息。 如果您只設定兩個 MessageBox 資料庫的大部分其他 MessageBox 資料庫所獲得的效益偏移進行訊息路由，主要 MessageBox 資料庫所耗用的額外負擔。  
  
> [!IMPORTANT]  
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]儲存在 MessageBox 資料庫中的所有狀態和每個 MessageBox 資料庫包含不同商務程序的狀態資訊。 為了獲得可靠性，您必須叢集所有 MessageBox 資料庫，包括主要和次要 MessageBox 資料庫。  
  
### <a name="providing-high-availability-for-multiple-messagebox-databases"></a>為多個 MessageBox 資料庫提供高可用性  
 加入至 MessageBox 資料庫時您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署可改善延展性，它不提供高可用性，因為每個 MessageBox 資料庫是唯一且獨立的而且有可能的單一失敗點，所以您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 新增備援包含為每個 MessageBox 資料庫設定伺服器叢集。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]因此資料庫不共用資料，或沒有伺服器叢集提供備援，請將資料分散到多個 MessageBox 資料庫中中。  
  
## <a name="providing-high-availability-for-the-biztalk-tracking-database"></a>為 BizTalk 追蹤資料庫提供高可用性  
 根據特定部署的需求，您可能想要藉由隔離到個別的 BizTalk 追蹤資料庫提升追蹤效能[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦，而藉由建立不同的 BizTalk 主控件專用於主控件追蹤。 下圖顯示兩個主控件執行個體與叢集的資料庫專用的追蹤主控件。  
  
 ![向外擴充追蹤資料庫](../technical-guides/media/4fc1d448-2a6c-4cea-ac17-96c1263dfb68.gif "4fc1d448-2a6c-4cea-ac17-96c1263dfb68")  
  
 如果您的部署具有高輸送量且牽涉到追蹤許多資料，這些訊息，追蹤的額外負擔可能會耗用的資源執行的電腦上的許多[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 如果發生這種情況，而且有高比率的內送訊息繼續，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]達到的點，因為追蹤訊息所需的資源大於執行其他所需的資源無法處理新訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]元件 （例如接收訊息，並將它們保存到 MessageBox 資料庫）。  
  
 若要改善效能和安全性，建議您指派不包含任何其他項目 (例如，接收位置、協調流程或管線) 的主控件專供追蹤之用，並停用接收、處理和傳送主控件的追蹤。 若要為追蹤主控件提供高可用性，請為追蹤主控件建立一個以上的主控件執行個體。 如需有關如何建立追蹤主控件的詳細資訊，請參閱[如何建立新的主控件](http://go.microsoft.com/fwlink/?LinkId=156825)(http://go.microsoft.com/fwlink/?LinkId=156825) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 對於每個 MessageBox 資料庫，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 僅使用一個追蹤主控件執行個體，將訊息從 MessageBox 資料庫移至 BizTalk 追蹤資料庫 (BizTalkDTADb)。 若其他電腦執行的追蹤主控件執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]出處理個別的追蹤主控件執行個體的每個 MessageBox 資料庫的自動調整。 若 MessageBox 資料庫數目大於追蹤主控件執行個體數目，則一或多個追蹤主控件執行個體將服務一個以上的 MessageBox 資料庫。  
  
 若要提供 BizTalk 追蹤資料庫的高可用性，使用 Windows 叢集來設定兩部執行的資料庫電腦[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]或[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]主動/被動組態中。  
  
## <a name="providing-high-availability-for-the-bam-databases"></a>為 BAM 資料庫提供高可用性  
 *商務活動監控*(BAM) 提供獨立於 IT 實作或跨異質 IT 實作的商務程序可見性。 BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] （BAM 星狀結構描述資料庫、 BAM 主要匯入資料庫和 BAM 封存資料庫） 的資料庫和 BAM 分析資料庫儲存商務活動資料不同於操作監控資料。 下圖顯示 BAM 資料庫基礎結構。  
  
 ![BAM 資料庫基礎結構](../technical-guides/media/769c3b7c-fe16-4260-967e-6af003c4f08d.gif "769c3b7c-fe16-4260-967e-6af003c4f08d")  
  
 若要確定 BAM 基礎結構為高度可用，請執行下列動作：  
  
-   **叢集 BAM 主要匯入資料庫和 BAM 分析資料庫。** BAM 主要匯入資料庫是商務活動監控系統的中心。 因此，使用 Windows 叢集讓此資料庫高度可用，並依照接下來的兩個建議以避免此資料庫被填滿，就很重要。 BAM 分析資料庫是一種 Analysis Services 資料庫，它儲存了商務分析師用以建立活動彙總和 OLAP Cube 的資料，因此，此資料庫的任何停機都會影響其產能。 雖然您不必叢集 BAM 封存資料庫，我們建議您監視事件記錄檔的錯誤，請確定已成功，傳輸的資料，並監視資料庫的大小，SQL Server Integration Services (SSIS) 封裝執行時如此您可以取代它之前填滿上。  
  
-   **定義線上視窗。** 若要讓更佳的效能並避免停機，BAM 資料分割的設定，BAM 主要匯入資料庫中的資料插入資料表時已完成活動，根據時間戳記。 BAM 藉由定期將完成的資料表與另一個格式完全相同的空資料表交換來完成此項工作。 BAM 在執行此動作後，其他完成的活動就會存放在新分割上 (資料表)，而 BAM 也會保留線上視窗所定義時間的舊分割。 您必須定義線上視窗以確保 BAM 主要匯入資料庫中的分割數目不會成長得太大。 如需排程線上視窗的詳細資訊，請參閱[封存主要匯入資料庫資料](http://go.microsoft.com/fwlink/?LinkId=156826)(http://go.microsoft.com/fwlink/?LinkId=156826) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
-   **排程定期執行 SSIS 封裝。** 定義線上視窗可確保 BAM 主要匯入資料庫不會填滿舊活動的分割。 您也必須排程定期執行，若要建立新的資料分割，活動資料，並將資料從 BAM 主要匯入資料庫中的舊分割移到 BAM 封存資料庫的 SSIS 封裝。 如需排程的 SSIS 封裝的詳細資訊，請參閱[排程 SQL Server Integration Services 封裝](http://go.microsoft.com/fwlink/?LinkId=156827)(http://go.microsoft.com/fwlink/?LinkId=156827) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
-   **請仔細選擇少量的資料項目 （檢查點），並避免包含不必要資料的項目，定義活動時。**  
  
-   **了解排程和即時彙總設計彙總時之間的取捨。** 即時彙總自動維護的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]觸發程序，且沒有延遲。 它們適用於某些關鍵任務的低延遲案例中，但是它們會造成效能成本，只要正在寫入事件至 BAM 主要匯入資料庫。 排程彙總依賴排程 cube SSIS 封裝，以更新其彙總資料。 其延遲是等於或大於 SSIS 排程間隔，但整體 BAM 主要匯入資料庫上具有較小的效能影響。  
  
-   **如果您選擇排程彙總，請確定您排程 cube SSIS 以封存 SSIS 比更頻繁地執行。** 這是因為封存的 SSIS 不會移動已經為排程彙總到 BAM 封存資料庫處理的活動資料。  
  
-   **啟用 BAM 事件匯流排服務在多部電腦以取得容錯移轉功能。**  
  
## <a name="providing-high-availability-for-the-other-biztalk-server-databases"></a>為其他 BizTalk 伺服器資料庫提供高可用性  
 若要提供高可用性的其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，設定兩部電腦執行[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]或[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]Windows 叢集中。 這些電腦可以在備援的主動/主動或主動/被動組態執行，而且可以將資料儲存在共用磁碟機 (例如 RAID 1 + 0 SCSI 磁碟陣列) 或存放區域網路 (SAN)。  
  
## <a name="see-also"></a>另請參閱  
 [叢集 BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md)