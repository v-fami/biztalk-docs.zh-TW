---
title: BizTalk Server 層中的瓶頸 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ad36897-4e4a-43b9-9cb7-0bf22bd954fb
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f8c7b4366390c040d7a4a34b473bdf4c3cfd352
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004943"
---
# <a name="bottlenecks-in-the-biztalk-server-tier"></a>BizTalk Server 層中的瓶頸
BizTalk 層可以區分為下列功能區域：  
  
- 接收  
  
- Processing  
  
- 傳輸  
  
- 追蹤  
  
- 其他  
  
  對於這些區域，如果系統資源 （CPU、 記憶體和磁碟） 似乎已經飽和，升級伺服器平台相應增加或縮小根據您的應用程式的特性。 如果系統資源尚未飽和，請執行在此節中描述的步驟。  
  
## <a name="bottlenecks-in-the-receive-location"></a>接收位置中的瓶頸  
 如果訊息累積在接收位置 （例如，檔案接收資料夾變得龐大），這表示系統無法跟上的連入負載的速度不夠快吸收資料。 這是因為內部的節流。 也就是 BizTalk Server 可以降低接收速率，如果 「 訂閱者 」 無法處理的資料快速足夠而造成的積存增加資料庫資料表中。 如果瓶頸因為硬體限制，請嘗試相應增加。 如需有關相應增加的詳細資訊，請參閱 BizTalk Server 2010 文件中的下列主題：  
  
- [向上擴充 BizTalk Server 層](http://go.microsoft.com/fwlink/?LinkId=158073)(http://go.microsoft.com/fwlink/?LinkId=158073)。  
  
- [向上擴充 SQL Server 層](http://go.microsoft.com/fwlink/?LinkId=158077)(http://go.microsoft.com/fwlink/?LinkId=158077)。  
  
  它也可向外擴充方法是加入主機對應到接收處理常式的主控件執行個體 （伺服器）。 如需有關向外延展的詳細資訊，請參閱 BizTalk Server 2010 文件中的下列主題：  
  
- [向外擴充 BizTalk Server 層](http://go.microsoft.com/fwlink/?LinkId=158076)(http://go.microsoft.com/fwlink/?LinkId=158076)。  
  
- [向外擴充 SQL Server 層](http://go.microsoft.com/fwlink/?LinkId=158075)(http://go.microsoft.com/fwlink/?LinkId=158075)。  
  
  使用 Perfmon 來監視系統上的資源使用。 確認外部的接收位置並非瓶頸肇因，這點很重要。 例如，確認是否因為較高的磁碟 I/O 已飽和的遠端檔案共用、 裝載遠端外寄佇列的伺服器尚未飽和，或用戶端用來產生 HTTP 負載不會耗盡執行緒上。  
  
## <a name="processing-bottlenecks"></a>處理瓶頸  
 如果主控件佇列 – 長度 」 效能計數器會持續增加，這表示，協調流程未完成速度不夠快。 如需詳細資訊，請參閱本主題中的 Perfmon 計數器表格。 這可能是由於記憶體爭用或 CPU 飽和而導致。  
  
 如果協調流程伺服器是瓶頸所在，請使用 Perfmon 以識別來源。  
  
 如果伺服器受限於 CPU 處理能力，請考慮下列各項：  
  
-   如果工作流程很複雜，請考慮分割成多個較小的協調流程的協調流程  
  
    > [!NOTE]  
    >  將協調流程切割為多個工作流程，可能會導致額外的延遲狀況，並增加複雜度。 多個工作流程也可能導致增加訊息來發佈和取用 BizTalkMsgBoxDb，從數種將額外的壓力放在資料庫上。  
  
-   如果您使用複雜的對應，請考慮是否將其移動至接收/傳送埠。 請務必確認哪一個連接埠有額外的頻寬。  
  
-   請考慮向上擴充硬體，或藉由設定額外的處理伺服器向外延展。  
  
## <a name="transmitting-bottlenecks"></a>傳輸瓶頸  
 如果裝載伺服器傳送配接器已飽和的資源 （例如，磁碟、 記憶體或 CPU） 時，請考慮向上擴充伺服器或向外擴充到額外傳送主機伺服器。 如果目的地 (在 BizTalk 外部) 無法以夠快的速率接收資料，則傳送層可能會成為瓶頸。 這會導致訊息在 MessageBox 資料庫 (Application SendHostQ) 中累積。  
  
 如果所有端點在拓撲的範圍內，找出位於目的地的原因。 例如，決定是否 HTTP 位置會以最佳方式設定為接收負載。 如果沒有，請考慮相應放大。也會決定是否目的地不斷增加，由於 BizTalk 傳遞的過多的輸出訊息。 如果是，您可能需要維護計畫來封存和清除目的地訊息。 大量的目的地資料夾中的檔案可能嚴重影響 BizTalk 服務的能力，將資料認可到磁碟機。  
  
## <a name="tracking-bottlenecks"></a>追蹤瓶頸  
 追蹤主控件執行個體負責將商務活動監控 (BAM) 和健全狀況與活動追蹤 (HAT) 資料從 MessageBox 資料庫 （TrackingData 資料表） 移到 BizTalk 追蹤 」 和/或 BAM 主要匯入的資料庫資料表。 如果設定多個 MessageBox 資料庫，則追蹤主控件執行個體使用四個執行緒，每個 MessageBox 資料庫。  
  
 可以追蹤主控件執行個體是受 CPU 限制。 如果是，請考慮向上擴充伺服器，或向外延展設定額外的伺服器與主控件追蹤已啟用。 多個主控件執行個體，會自動載入平衡多個 MessageBox 資料庫設定。 如需有關調整的詳細資訊，請參閱主題[調整您的解決方案](http://go.microsoft.com/fwlink/?LinkId=158078)(http://go.microsoft.com/fwlink/?LinkId=158078)。  
  
 如果 MessageBox 資料庫中的 TrackingData 資料表變得龐大，通常是因為在 BizTalk 追蹤 」 和/或 BAM 主要匯入資料庫上的資料維護工作未執行所設定，導致 BizTalk 追蹤 」 及/或 BAM 主要的成長匯入資料庫。 這些資料庫會變得太大之後它會對追蹤主控件能夠將資料插入 TrackingData 資料表來產生負面影響。 這會將備份 MessageBox 資料庫資料表中的追蹤的資料。 TrackingData 資料表成長會促使節流開始。  
  
 您應該只啟用應用程式，因為這會減少記錄的資料量，並降低其風險追蹤瓶頸所需的最小追蹤。 停用個別的項目，例如協調流程和傳送/接收埠的追蹤設定的相關資訊，請參閱[如何停用追蹤](http://go.microsoft.com/fwlink/?LinkId=160064)(http://go.microsoft.com/fwlink/?LinkId=160064)。  
  
## <a name="other"></a>其他  
 設定部署拓撲，使不同的功能可在專用的外掛式主控件執行個體中執行。 如此一來每個主控件執行個體取得其自己一組資源 （例如，在 32 位元系統，2 GB 的虛擬記憶體位址空間、 控制代碼、 執行緒）。 伺服器是否有足夠的 CPU 空間和記憶體來裝載多個主控件執行個體，則可以設定為相同的實體電腦上執行。 如果沒有，請考慮相應放大，藉由將功能移至專用的伺服器。 在多個伺服器上執行相同的功能，也可以提供具有高度可用性的組態。  
  
## <a name="biztalk-system-performance-counters"></a>BizTalk 系統效能計數器  
  
|Object|執行個體|計數器|監控目的|  
|------------|--------------|-------------|------------------------|  
|處理器|_Total|% 處理器時間|資源爭用|  
|處理|BTSNTSvc|虛擬位元組|記憶體流失/膨脹|  
|處理|BTSNTSvc|私用位元組|記憶體流失/膨脹|  
|處理|BTSNTSvc|控制碼計數|資源爭用|  
|處理|BTSNTSvc|執行緒計數|資源爭用|  
|實體磁碟|（_i)|% 閒置時間|資源爭用|  
|實體磁碟|（_i)|Average Disk Queue Length|資源爭用|  
  
### <a name="cpu-contention"></a>當 CPU 出現競爭  
 如果處理器已飽和，您可以片段分隔接收從傳送和協調流程的應用程式。 若要這樣做，建立不同的主控件對應的主機特定功能 （接收/傳送/協調流程/追蹤），將專用的伺服器新增到這些不同的主控件。 協調流程功能通常是需要大量 CPU。 如果您設定系統，因此不同的專用伺服器上執行的協調流程，這有助於改善整體系統輸送量。  
  
 如果部署多個協調流程，您可以將它們登錄至不同的專用協調流程的主機。 將不同的實體伺服器對應至專用的協調流程主控件，可確保不同的協調流程會被隔離，並不會爭用相同實體的位址空間中或在相同伺服器上的共用資源。  
  
 停止未使用的主控件執行個體。 未使用的主控件執行個體可以定期檢查來處理訊息的 MessageBox 競爭 CPU 和記憶體資源。 此外，停止未使用接收位置、 傳送埠和協調流程。  
  
### <a name="spool-table-growth"></a>多工緩衝處理資料表成長  
 下游瓶頸及/或資源爭用情況可能會造成多工緩衝處理以開始過度成長並降低整體效能。 如需詳細資訊，請參閱 「 多工緩衝處理資料表成長 」 中[如何找出瓶頸 MessageBox Database1](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md)。  
  
### <a name="memory-starvation"></a>記憶體耗盡  
 高輸送量實例可能增加對系統記體體的需求。 由於 32 位元處理序受限於它可以取用的記憶體數量，建議您使用接收/程序/傳送功能分隔到不同的主控件執行個體，每個主機將會收到它自己的 2GB 位址空間。 此外，如果相同的實體伺服器上執行多個主控件執行個體，您可以升級至 4/8 GB 的記憶體，來避免交換到磁碟的資料，從實際的記憶體。 長時間執行的協調流程可以保留較長的已配置記憶體。 這會導致記憶體膨脹，並啟動節流。 大型訊息也可能導致高記憶體耗用量。  
  
 您可以藉由降低處理大型訊息時，就會發生記憶體膨脹問題使更加輕鬆**內部訊息佇列大小**並**每一 CPU 的內含式訊息**特定主控件的值。  
  
> [!NOTE]  
>  如果延遲是一項考量，會變更為**內部的訊息佇列大小**並**每一 CPU 的內含式訊息**應謹慎使用，這可能會增加系統的端對端延遲。  
  
### <a name="disk-contention"></a>磁碟爭用  
 如果磁碟已飽和 （例如，具有大量的檔案 /MSMQ 傳輸），請考慮升級為多磁針和分割磁碟使用 RAID 10。 此外，每當使用檔案傳輸，務必確定接收和傳送資料夾不會變得大於 50000 的檔案。  
  
 接收資料夾可以成長大型如果 BizTalk Server 會調整至系統的內送資料。 請務必從傳送資料夾移動資料，以便在此資料夾中的成長不會影響 BizTalk Server 能夠撰寫額外的資料。 對於非交易式 MSMQ 佇列，建議從遠端建立接收佇列，以便在 BizTalk Server 將會減少磁碟爭用情況。  
  
 遠端非交易式佇列組態也提供高可用性，因為裝載佇列的遠端伺服器可以叢集化。  
  
### <a name="other-system-resource-contention"></a>其他系統資源爭用  
 根據傳輸類型，可能必須設定 IIS 的 HTTP （例如，MaxIOThreads、 MaxWorkerThreads） 之類的系統資源。  
  
 使用 ASP.NET 2.0 和 ASP.Net 4 中， \<processModel autoConfig ="true"\> machine.config 檔案中的設定會自動設定以獲得最佳效能的下列設定：  
  
- 最大工作者執行緒  
  
- 最大的 IO 執行緒  
  
- httpRuntime 項目的 minFreeThreads 屬性  
  
- httpRuntime 項目的 88n,minlocalrequestfreethreads 屬性  
  
- maxConnection 屬性\<Connectionmanagement>\>項目 （網路設定） 項目  
  
  如需有關如何設定會影響配接器效能的參數的詳細資訊，請參閱[ASP.NET 組態設定為 processModel 項目](http://go.microsoft.com/fwlink/?LinkId=158080)(http://go.microsoft.com/fwlink/?LinkId=158080)。  
  
  如需可能會影響 BizTalk Server 配接器的組態設定的詳細資訊，請參閱[組態參數，會影響配接器效能](http://go.microsoft.com/fwlink/?LinkID=154200)(http://go.microsoft.com/fwlink/?LinkID=154200)。  
  
  除了如何最佳化 BizTalk Server 應用程式，其他執行相同的伺服器上的 ASP.NET 應用程式會對影響整體效能。 請務必最佳化所有的 ASP.NET 應用程式，以降低系統資源的需求。 如需詳細資訊，請參閱 < [ASP.NET 效能](http://go.microsoft.com/fwlink/?LinkId=158081)(http://go.microsoft.com/fwlink/?LinkId=158081)。  
  
  當設定最大效能，請考慮最佳化其他外部系統，例如傳訊引擎 （訊息佇列，MQSeries）、 應用程式、 資料庫、 Active Directory 等，是您整體的 BizTalk 解決方案的一部分。 在任何其他外部系統的效能瓶頸可以有負面影響的 BizTalk 方案。  
  
### <a name="downstream-bottlenecks"></a>下游瓶頸  
 如果下游系統無法從 BizTalk 接收資料的速度不夠快，這個輸出資料會備份 BizTalk 資料庫中。 這會導致膨脹、 導致開始節流、 壓縮接收管道，和會影響 BizTalk 系統的整體輸送量。 直接表示這是多工緩衝處理資料表成長。 如需有關的瓶頸和多工緩衝處理資料表的詳細資訊，請參閱[如何找出瓶頸 MessageBox Database1](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md)。  
  
### <a name="throttling-impact"></a>節流衝擊  
 節流最終將會啟動來保護系統，使其無法到達無法復原的狀態。 因此，您可以使用節流來確認系統是否正常運作，並找出問題的來源。 識別從節流狀態瓶頸的原因之後，分析其他效能計數器，以判斷問題的來源。 比方說，在 MessageBox 資料庫上的高爭用情況可能是由於高 CPU 用量，因此造成過度分頁至磁碟，因為記憶體不足所造成。 在 MessageBox 資料庫上的高爭用情況也可能造成高鎖定爭用，由於磁碟機飽和。 雖然偶爾的節流設定不是效能嚴重威脅，持續發生節流事件可能表示更重要的基礎問題。 如需有關 BizTalk Server 會使用節流設定這些條件的詳細資訊，請參閱[如何 BizTalk Server 實作主控件節流](http://go.microsoft.com/fwlink/?LinkID=155286)(http://go.microsoft.com/fwlink/?LinkID=155286)。  
  
 如需有關如何節流 BizTalk Server 可管理可用資源的使用並減少資源爭用的詳細資訊，請參閱[最佳化資源使用狀況透過主控件節流](http://go.microsoft.com/fwlink/?LinkID=155770)(http://go.microsoft.com/fwlink/?LinkID=155770)。  
  
## <a name="biztalk-application-counters"></a>BizTalk 應用程式計數器  
  
|Object|執行個體|計數器|描述|  
|------------|--------------|-------------|-----------------|  
|BizTalk 傳訊|RxHost|每秒接收文件數|內送速率|  
|BizTalk 傳訊|TxHost|每秒處理文件數|外寄速率|  
|XLANG/s 協調流程|PxHost|每秒完成的協調流程數|處理速率|  
|BizTalk: MessageBox： 一般計數器|MsgBoxName|多工緩衝處理大小|所有主控件佇列總計大小|  
|BizTalk: MessageBox： 一般計數器|MsgBoxName|追蹤資料大小|MessageBox 上的 TrackingData 資料表大小|  
|BizTalk：MessageBox：主控件計數器|PxHost:MsgBoxName|主控件佇列 - 長度|指定主控件佇列中的訊息數|  
|BizTalk：MessageBox：主控件計數器|TxHost:MsgBoxName|主控件佇列 - 長度|指定主控件佇列中的訊息數|  
|BizTalk：訊息代理程式|RxHost|資料庫大小|發佈 (PxHost) 佇列的大小|  
|BizTalk：訊息代理程式|PxHost|資料庫大小|發佈 (TxHost) 佇列的大小|  
|BizTalk：訊息代理程式|HostName|訊息傳遞節流狀態|影響 XLANG 和輸出傳輸|  
|BizTalk：訊息代理程式|HostName|訊息發佈節流狀態|影響 XLANG 和輸入傳輸|  
  
### <a name="where-do-i-start"></a>要從何處著手？  
 監視**訊息傳遞節流狀態**並**訊息發佈節流狀態**每個主控件執行個體是不錯的起點。 如果這些計數器的值不是零，這表示 BizTalk 系統中的節流，而且您可以進一步分析瓶頸的原因。 如需有關其他效能計數器的描述，請參閱[資料庫層中的瓶頸](../technical-guides/bottlenecks-in-the-database-tier.md)。  
  
## <a name="orchestration-engine-performance-counters"></a>協調流程引擎效能計數器  
 我們強烈建議您微調協調流程執行階段設定，因為持續的協調流程 dehydration\rehydration 和持續性點可以有嚴重影響整體效能。  測試可能包含多個持續點和交易式範圍的複雜協調流程時，您必須使用下列的計數器。  
  
|計數器|註解|  
|-------------|--------------|  
|凍結的協調流程數/秒|平均每秒凍結的數目。|  
|解除凍結的協調流程數/秒|平均每秒解除凍結的數目。|  
|持續點數/秒|平均每秒保存的協調流程執行個體數。|  
|記憶體中駐留的協調流程數|目前由主控件執行個體裝載的協調流程執行個體數。|  
|完成的協調流程數/秒|平均每秒完成的數目。|  
|擱置的協調流程數/秒|平均每秒擱置的數目。|  
|認可的交易式範圍數/秒|平均每秒認可的數目。|  
|中止的交易式範圍數/秒|平均每秒中止的數目。|  
|補償的交易式範圍數/秒|平均每秒補償的數目。|  
  
## <a name="backlog-buildup"></a>待處理項目積存  
 1 對 1 的部署案例 1 則訊息，在 1 的訊息中收到結果處理，而且在系統中沒有待處理項目傳送時，如果外寄速率不等於內送速率。 在此情況下，您可以監視多工緩衝處理大小。 在決定外寄速率的瓶頸的原因，請執行單一使用案例中，一次。 隔離協調流程、 接收位置，並傳送至不同的主控件的位置。  
  
 新增 biztalk: Message Box： 主控件計數器來監視主應用程式效能監視記錄檔。 主控件佇列-長度： 計數器會追蹤特定主控件佇列中的訊息總數。 如果一或多個這些計數器會繼續成長一段時間，讓這些主機所執行的成品特別注意。  
  
 如果多工緩衝處理以線性方式成長，判斷應用程式佇列是由負責多工緩衝處理成長。  
  
 如果沒有任何應用程式佇列成長，多工緩衝處理會繼續成長，這可能表示清除工作會無法跟上。 會發生這種情況是如果代理程式未執行，或沒有其他的 SQL Server 上的系統資源爭用。  
  
 如果其中一個應用程式佇列成長，診斷這種成長的原因。 監視無法清空特定應用程式佇列的系統上的系統資源 （例如，因為伺服器上的 CPU 耗盡而成長 Orchestration HOST-Q）。 此外，請確認節流計數器的特定主控件執行個體的值。  
  
 如果 BizTalk:Messsage 代理訊息傳遞節流的狀態和訊息發佈節流狀態 」 效能計數器不是零，請檢查該值以確認節流的原因 （例如，記憶體超過閾值，執行中的訊息計數太高，依此類推）。  
  
## <a name="stand-alone-profiler"></a>獨立的 Profiler  
 您可以使用效能計數器偵測到高層級的瓶頸的位置。 不過，一旦縮小，您可能需要檢查更多程式碼緊密為了協助進行問題。 使用 Visual Studio 2010 附隨獨立 Profiler 可以是非常有用的工具，以協助診斷程式碼花費大部分的循環。 如需相關資訊，請參閱  
  
## <a name="l2l3-cache"></a>L2/L3 快取  
 從硬體觀點來看，您可以使用上架的 CPU 快取，以獲得最大的優點。 較高的 CPU 快取有助於增加快取命中率，減少系統從記憶體對磁碟進行來回資料分頁的需求。  
  
## <a name="64-bit-performance-bottlenecks"></a>64 位元效能瓶頸  
 64 位元系統上的效能可能看來會低於在 32 位元系統上所能達到的效能。 這是基於一些理由，最重要的可能是記憶體。  
  
 測量 2 GB 的記憶體的 32 位元系統上的效能，並比較結果類似 64 位元系統，具有 2 GB 的記憶體不會比較相同的動作。 64 位元系統將出現於磁碟 i/o 繫結 (低 %磁碟閒置時間 & 高磁碟佇列長度) 和 CPU 繫結 （最大 CPU 和高內容切換）。 不過，這是不是因為在 64 位元系統上執行檔案 I/O 是昂貴的時候。  
  
 64 位元系統是多個記憶體高用量 （64 位元定位） 這會導致耗用大部分的 2GB 可用記憶體的作業系統。 當發生這種情況時，其他大部分的作業會導致浮現檔案子系統磁碟中的分頁。 因此，系統花費 CPU 循環分頁記憶體這兩個資料輸入/輸出和程式碼，並會受到高磁碟延遲。 這會造成系統呈現較高磁碟爭用和較高 CPU 耗用的情況。  
  
 若要減輕此問題的方式是向上延展伺服器升級記憶體。 相應增加為 8 GB 的主意，不過，加入更多記憶體沒有幫助改善輸送量，除非問題的來源是因為記憶體不足情況的 CPU 資源用盡。  
  
## <a name="using-bam-to-identify-bottlenecks-and-high-latency-issues"></a>使用 BAM 識別瓶頸和高延遲問題  
 低延遲很重要時，您可以使用 BAM 來測量系統完成 BizTalk Server 系統中的每個階段所花費的時間。 雖然您可以使用 HAT 偵錯之訊息的狀態並診斷路由訊息中的問題的來源，您可以使用 BAM 來追蹤透過訊息流程的各個端點。 藉由建立 BAM 追蹤設定檔定義與接續活動，您可以測量系統，以協助追蹤在工作流程程序中最昂貴的階段的不同部分之間的延遲。  
  
 您可以使用 HAT 中的協調流程偵錯工具，來查詢擱置的執行個體、 繼續偵錯模式中的執行個體，並加入適當的中斷點使用技術的詳細資料檢視。 這會讓您追蹤活動並逐步偵錯訊息。  
  
 您可以設定中斷點追蹤下列事件：  
  
- 協調流程的開始和結束  
  
- 圖形的開始和結束  
  
- 訊息的傳送或接收  
  
- 例外狀況  
  
  在每個中斷點，您可以檢查有關區域變數、訊息及其屬性、連接埠和角色連結的資訊。  
  
## <a name="see-also"></a>另請參閱  
 [尋找並排除瓶頸](../technical-guides/finding-and-eliminating-bottlenecks.md)