---
title: "何謂持續性效能？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reliability, sustainable performance
- performance, goals
- performance, sustainable performance
- planning, performance
- performance, planning
- sustainable performance
ms.assetid: 4b18b976-7714-431f-8976-f40a1016d5f3
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 276ce104d8667166d020b33b2f1fb4e7bfb98dbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-sustainable-performance"></a>何謂持續性效能？
在規劃和評估系統的持續性時，考慮長期持續性是很重要的。 主要考量為：  
  
-   **載入設定檔和效能目標**： 載入設定檔和效能目標時，不能有太多詳細資料。 測試與整備憑證將會以能夠長期處理這些負載為基礎。  
  
-   **其他活動與程序競爭伺服器資源**： 它不是幾乎訊息負載。 伺服器上還有其他程序與活動，會影響像是資料庫維護與 MessageBox 查詢的效能。  
  
-   **規劃與未規劃的系統中斷與停機時間**： 大量事件與訊息待處理項目可以變更有效的負載設定檔。  
  
 在考慮建置持續性系統及測試以認證這些系統時，請確定將這些因素納入考量並加以規劃。  
  
## <a name="is-your-performance-sustainable"></a>您的效能可持續嗎？  
 在討論 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的效能時，我們定義了如下的最大持續性效能：  
  
-   在生產環境中，系統可無限處理的最高負載訊息流量。  
  
 雖然這看起來很簡單，但是當您將解決方案放置於生產環境之後，在評估於特定硬體上執行的解決方案是否可支援每日出入的負載時，必須考慮許多因素。  
  
 將解決方案放置於生產環境之前，請先考慮下列因素，以評估此解決方案是否可無限處理最高負載訊息流量：  
  
-   預期的效能目標與輸送量/延遲設定檔。  
  
-   在相同硬體上執行的其他程序，例如：  
  
    -   正常監控與疑難排解  
  
    -   作業資料庫維護，例如，記錄傳送、備份、清除、索引維護，以及統計資料更新。  
  
    -   其他應用程式  
  
-   計劃與非計劃的系統中斷，例如：  
  
    -   夥伴網站停機而封鎖傳送或接收訊息  
  
    -   定期系統維護停機時間  
  
## <a name="know-your-performance-goals"></a>瞭解您的效能目標  
 在評估解決方案的持續性之前，您必須詳細瞭解預期的生產負載。 若未詳細瞭解目標，就無法評估整備。 良好的效能目標是很重要的，因為它會引導您的系統測試與憑證策略。 您的效能目標應有下列項目：  
  
-   以時間函式來定義效能的曲線。 這些函式涵蓋的範圍可從極簡單到非常複雜。  
  
-   與效能函式關聯的效能需求。  
  
-   檔案大小與類型的散佈。  
  
### <a name="example-1"></a>範例 1  
  
-   每天的訊息會從上午 8 點的 0 msgs/sec 開始累積，到中午的 80 msgs/sec，然後在下午 9 點回到 0 msgs/sec，大約會是個鐘形曲線。  
  
-   系統對每個訊息沒有特定的延遲需求，但它必須可以處理此負載，加上前一天載入的所有訊息 (例如，系統中斷 24 小時的狀況)，而不會有所落後。  
  
-   有三種文件類型：「購物籃」、「補貨」及「庫存要求」。 「購物籃」文件的大小介於 2 到 10 KB 之間，並於任何指定時間中組成 75% 的訊息計數。 「補貨」與「庫存要求」文件的大小一律會接近 1 KB，並於任何指定時間中分別組成其餘 10% 與 15% 的訊息計數。  
  
### <a name="example-2"></a>範例 2  
  
-   在每天午夜，需要處理一個 500,000 個訊息的批次。  
  
-   必須在 8 小時內處理完批次中的所有訊息。  
  
-   所有訊息都是相同類型，平均分散於 10 KB 到 50 KB (含) 之間。 此外，該批次一定包含 10 個目錄類型訊息，每個均為 10 MB，而且必須再分成個別的目錄項目才能處理。  
  
### <a name="example-3"></a>範例 3  
  
-   4000 位客戶服務代表在每天上午 8 點登入互動系統，平均每位代表每分鐘會執行 4 個查詢，直到下午 5 點關機為止，每週七天都是如此。  
  
-   所有的查詢都必須在 2 秒內傳回結果。  
  
-   所有查詢都是相同類型，其大小平均分散於 500 到 1000 個位元組 (含) 之間。  
  
#### <a name="a-performance-requirement-associated-with-the-performance-function"></a>與效能函式關聯的效能需求  
 繼續上述範例：  
  
-   **範例 1 （續）**： 系統對每個訊息，沒有特定的延遲需求，但它必須能夠處理此負載，加上載入的所有前一天的訊息 （例如發生 24 小時系統故障） 而不會有所落後。  
  
-   **範例 2 （續）**： 必須在 8 小時內完成處理批次中的所有訊息。  
  
-   **範例 3 （續）**： 所有查詢都必須在 2 秒內傳回結果。  
  
#### <a name="a-distribution-of-file-sizes-and-types"></a>檔案大小與類型的散佈  
  
-   **範例 1 （續）**： 有三種文件類型: 「 購物籃 」、 「 補貨 」 及 「 庫存要求。 「購物籃」文件的大小介於 2 到 10 KB 之間，並於任何指定時間中組成 75% 的訊息計數。 「補貨」與「庫存要求」文件的大小一律會接近 1 KB，並於任何指定時間中分別組成其餘 10% 與 15% 的訊息計數。  
  
-   **範例 2 （續）**： 所有訊息都屬於相同類型，平均分散於 10 到 50 Kb （含) 之間。 此外，該批次一定包含 10 個目錄類型訊息，每個均為 10 MB，而且必須再分成個別的目錄項目才能處理。  
  
-   **範例 3 （續）**： 所有查詢都是相同類型，平均分散於 500 到 1000 個位元組的大小，（含） 之間。  
  
## <a name="accounting-for-other-processes"></a>說明其他程序  
 除了直接透過 BizTalk 引擎傳送的負載設定檔之外，總是會有其他程序競爭相同硬體上的資源。  這些程序將降低系統之整體持續性效能的能力。 資料庫維護可能是這類程序的最常見範例。  
  
 每個資料庫 (大型或小型) 都需要定期作業維護，例如，記錄傳送、備份、封存，以及清除。 監控與疑難排解是您在定義和認證何謂持續性時必須考慮的其他作業範例。 例如，查詢 MessageBox (例如，透過管理主控台 [群組中樞] 頁面) 來查看過去 24 小時有多少指定類型的訊息遭到擱置，需要 SQL Server 已用來處理訊息的資源。  
  
 下面是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中通常對整體持續性最有影響的活動清單：  
  
-   **記錄傳送與備份**。 做為包含 SQL Server 之多數災害復原計劃的一部分，您必須定期對所有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組資料庫執行記錄傳送與備份。 如需詳細資訊，請參閱[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)。 另請參閱[記錄傳送](../core/log-shipping.md)。  
  
-   **封存和清除追蹤資料**。 除了整體記錄傳送與備份計劃，「 BizTalk 追蹤 (BizTalkDTADb) 資料庫有它自己的封存和清除區域;如需詳細資訊，請參閱[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)。 從 BizTalk 追蹤資料庫封存和清除資料的速度尤其重要，因為封存和清除 BizTalk 追蹤資料庫通常是使用追蹤時的瓶頸。  
  
-   **系統查詢**。 使用 API 或 BizTalk Server 管理主控台 UI 對系統執行各種類型的查詢，將會影響持續性效能。  
  
-   **MessageBox 維護**。 有許多 SQL 工作是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 核心功能的一部分，可藉由清除已完成處理的訊息與執行個體來維護 MessageBox 資料庫。 做為核心引擎的一部分，完成這些工作的速度是衡量持續性的關鍵因素。 如需有關這些作業以及其角色的詳細資訊，請參閱[維護 BizTalk Server1](../core/maintaining-biztalk-server1.md)。  
  
-   **解決方案部署活動**。 在部署、繫結和啟動新應用程式或現有應用程式的新版本時，額外的負載是放置於 BizTalk 上，像是在 MessageBox 資料庫上建立新訂閱。 部署應用程式之後，已處理的訊息將競爭資源，因而影響現有應用程式的效能。  
  
 對於其中的每個區域，您必須詢問：若要將這些活動的衝擊最小化，您有何建議？ 例如，他們應該計劃在凌晨 3 點執行它們嗎？  
  
## <a name="considering-planned-and-unplanned-outages"></a>考慮計劃與非計劃的中斷  
 中斷對於系統效能的影響，會根據經歷中斷的系統不同而變動，不過，最常見的結果如下：  
  
-   **大量事件**。 當系統停機一段長時間時，訊息會累積，然後在系統再次恢復運作時全部同時抵達以進行處理。  例如，若在 BizTalk 上執行的應用程式會透過 MSMQ 接收訊息，且該應用程式停機一段時間，則訊息會累積在佇列中，以等待收取。 當應用程式再度啟動時，就像有大量訊息「全部同時」抵達。  
  
-   **訊息待處理項目**。 當訊息要傳送至的系統停機時，通常會有使用其他資源的重試週期。 之後重試循環已用完，則通常會擱置訊息。 然後，當停機的系統恢復線上運作時，就會發生大量事件的類型，現在可以繼續和 (或) 成功地傳送大量訊息。  
  
 當然，像是定期排程維護的任何計劃中斷，在設計和認證系統時都必須列入考慮。 同時建議您考慮分析非計劃的中斷及其影響。  
  
 識別可能發生的中斷類型，藉由評估風險層級 (也就是可能性乘以嚴重性) 和較高風險中斷的持續時間與影響 (例如，大量事件、已擱置的訊息數量、積存等) 將它們排列等級，將指示系統可能發生中斷的可能性。 任何存放與轉寄、以傳訊為基礎的非同步系統 (如 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)])，必須設計為將處理足以涵蓋計劃與非計劃之中斷的「空餘空間」。  
  
## <a name="see-also"></a>另請參閱  
 [引擎保存性與耐久性](../core/engine-persistence-and-durability.md)   
 [依階段的專案規劃建議](../core/project-planning-recommendations-by-phase.md)   
 [測量最大持續性引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [擴充您的解決方案](../core/scaling-your-solutions.md)   
 [找出效能瓶頸](../core/identifying-performance-bottlenecks.md)   
 [引擎效能和容量](../core/engine-performance-and-capacity.md)