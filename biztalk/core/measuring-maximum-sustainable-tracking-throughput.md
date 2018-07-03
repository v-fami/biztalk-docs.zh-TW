---
title: 測量最大持續性追蹤輸送量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35605427-0217-4bdd-8b4a-3e68b3f5f452
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d68d1661a86858b8d2bca1bb067c8fa17ea421e3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017058"
---
# <a name="measuring-maximum-sustainable-tracking-throughput"></a>測量最大持續性追蹤輸送量
當您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 平台上部署商務解決方案之後，應該追蹤並監控系統，以瞭解下列事項：  
  
- 系統如何執行  
  
- 可能發生哪些例外狀況和錯誤以及原因為何  
  
- 以 BizTalk 解決方案實作的商務程序的目前狀態  
  
  對許多組織來說，也很重要的不可否認性目的流經整個系統的實際原始訊息的記錄。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供兩種類型的追蹤功能可解決這些需求：  
  
- **資料追蹤與活動 (DTA) 追蹤**。 DTA 可追蹤不同的使用者定義訊息屬性、協調流程偵錯事件、訊息流程事件，以及服務執行個體狀態。 您可以使用追蹤來查詢 BizTalk DTA 追蹤資料庫 (BizTalkDTADb) 中儲存的資料。 DTA 追蹤也可以包括原始資料 (稱為訊息內文) 的追蹤，用於不可否認性與問題解決。  
  
- **商務活動監控 (BAM) 追蹤**。 BAM 使用使用者定義的追蹤設定檔，追蹤商務程序到一組特別 BAM 資料庫的狀態。  
  
  在此主題中，我們將描述 DTA 架構和一套有系統的方法，以決定採用 DTA 的系統可無限期持續的最大持續性輸送量。 雖然 DTA 和 BAM 共用部分架構元件，但此主題只討論 DTA 的部分。 如需 BAM 架構的詳細資訊，請參閱[商務活動監控 (BAM)](../core/business-activity-monitoring-bam.md)。  
  
## <a name="overview-of-dta-tracking-architecture"></a>DTA 追蹤架構的概觀  
 訊息流程通過系統時，各種追蹤的項目，像是訊息內文、屬性和事件，通過一連串的程序和資料庫，最後寫入 BizTalkDTADb 資料庫。 在項目寫入 BizTalkDTADb 資料庫後，您可以使用追蹤來查詢追蹤的資訊。 如需設定和使用 BizTalkDTADb 資料庫中，追蹤，請參閱[檢視歷程記錄和追蹤資料](../core/viewing-historical-and-tracked-data.md)。  
  
 為確保系統持續性且將以指定的訊息流程速率無限期執行，追蹤項目在自己的路徑到 BizTalkDTADb 資料庫的路徑以及資料庫本身，都必須維持暢通。 例如，在沿路徑的資料庫資料表中或 DTA 中建置訊息，若未妥善管理，可能會使資料庫檔案無限制的成長而無法持續。  
  
 所以，我們現在先從瞭解追蹤資訊流程通過的架構和路徑開始。 這將會公開您必須監控的主要資源和效能指示器，以判斷追蹤系統與通過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 引擎的訊息流量是否保持良好的聯繫。  
  
 下圖顯示 DTA 追蹤架構和路徑的概觀。  
  
 ![DTA 追蹤概觀](../core/media/dtatrackingoverview.gif "DTATrackingOverview")  
  
 依照圖中編號的程序順序，進出 BizTalkDTADb 資料庫的所有 DTA 追蹤資料流程如下：  
  
1. BizTalk Server 執行階段程序包括一個稱為攔截器的元件。 攔截器的工作是在執行階段快取追蹤的項目，並在下一個 MessageBox 資料庫往返 (例如，將訊息加入 MessageBox 資料庫的佇列) 時，將快取的項目轉送至 MessageBox 資料庫。 攔截器會查看追蹤組態 (也稱為追蹤設定檔) 以決定要追蹤的項目，追蹤組態從管理資料庫取得，並在每個主控件執行階段執行個體快取，供攔截器使用。  
  
    如上圖所示，有兩個資料流插入 MessageBox 資料庫：  
  
   - 一個由 Spool 資料表代表  
  
   - 一個由 TrackingData 資料表代表  
  
     追蹤的訊息內文使用兩個資料流。 也就是說，訊息內文本身 (想成是資料的 BLOB) 是透過由 Spool 資料表代表的一組資料表來處理。 與訊息內文關聯的訊息事件 (例如，訊息識別項、追蹤訊息內文的時間、與訊息內文關聯的執行個體) 是透過 TrackingData 資料表處理。 與訊息內文追蹤無關的所有追蹤項目都只由 TrackingData 資料表處理。  
  
2. MessageBox 資料庫只是追蹤資料的第一站，用來快取追蹤資料，讓執行階段可繼續進行處理，不會直接被其他追蹤資料處理封鎖。  
  
    若要將追蹤訊息內文 (BLOB) 傳輸到 BizTalkDTADb 資料庫，您可以在此檢視並將它們封存到比較固定的存放區，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 採用了一個 SQL 代理程式工作，稱為 TrackedMessages_Copy_BizTalkMsgBoxDb，可以在每個 MessageBox 資料庫伺服器上執行。 此工作的任務是將標示為追蹤的訊息內文複製到 BizTalkDTADb 資料庫。  
  
3. 所有非訊息內文追蹤的資料會移動從 MessageBox 資料庫到 BizTalkDTADb 資料庫的一或多個呼叫中執行的 TDDS 服務[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主機。 只要透過 BizTalk Server 主控台中的主控件屬性頁面將主控件設定為「主控件追蹤」，TDDS 子服務就會在該主控件的每個執行個體執行。  
  
4. 若沒有定期清除 BizTalkDTADb 資料庫，它就會無限制的成長，最後導致操作上的問題。 現在有一個單一的 SQL 代理程式工作，稱為 DTA 清除與封存 (BizTalkDTADb)，可執行清除 BizTalkDTADb 資料庫的工作。 依照預設，此工作每分鐘執行，並清除早於某些使用者設定的時間 (例如 24 小時) 的所有已完成的執行個體。  
  
    如需詳細資訊有關 DTA 清除與封存工作，請參閱 <<c0> [ 如何設定 DTA 清除與封存工作](../core/how-to-configure-the-dta-purge-and-archive-job.md)。  
  
5. DTA 清除與封存工作也可以選擇將 BizTalkDTADb 資料封存為 SQL 備份，以便長期儲存和/或離線檢視資料。 如果需要查詢封存的 BizTalkDTADb 資料，首先必須還原為新的資料庫，SQL Server 中，然後您可以使用追蹤或 SQL Query Analyzer 來查詢它。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [瞭解 DTA 追蹤效能行為](../core/understanding-dta-tracking-performance-behavior.md)  
  
-   [測量 DAT 追蹤 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md)  
  
-   [尋找 DTA 追蹤之 MST 的祕訣和訣竅](../core/tips-and-tricks-for-finding-mst-of-dta-tracking.md)  
  
## <a name="see-also"></a>另請參閱  
 [調整追蹤資料庫大小的指導方針](../core/tracking-database-sizing-guidelines.md)