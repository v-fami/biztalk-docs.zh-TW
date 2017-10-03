---
title: "規劃追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ffc8573-1b4a-47c7-96ab-0471f43facf5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9853fccde9c5fa6e8c223106c8386f19298d0b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-tracking"></a>規劃追蹤
追蹤的訊息是部分的訊息執行個體，例如訊息本文、 訊息屬性和中繼資料儲存的資料庫中，通常為封存之用的程序。 後續可以檢視追蹤的訊息執行個體部分執行查詢，從 [群組中樞] 頁面中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 除了存取封存的資料，您也可以檢視即時資料，可以識別並修正開發中的問題或預備環境的有力工具。  
  
 因為郵件追蹤的程序可以是非常耗用資源，您應該檢閱本主題建立您的計劃之前。  
  
 如需有關追蹤的詳細資訊，請參閱[健全狀況與活動追蹤](http://go.microsoft.com/fwlink/?LinkId=154187)(http://go.microsoft.com/fwlink/?LinkId=154187)。  
  
## <a name="configuring-and-enabling-the-dta-purge-and-archive-sql-agent-job"></a>設定及啟用 DTA 清除與封存 SQL Agent 作業  
 這項作業會封存和清除舊的資料從 BizTalk 追蹤資料庫，藉此讓它變得太大。 這是不可或缺的狀況良好[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。 在大型追蹤資料庫將會開始追蹤主控件以及任何其他處理序的效能影響該查詢追蹤資料庫。  
  
-   **請確認已正確設定、 啟用以及已成功完成 DTA 清除與封存 SQL 代理程式作業。** 因為您必須先將它設定為包含可以在其中寫入封存檔案的目錄，預設不會啟用這項作業。  
  
-   **請確保工作能夠以最快速度的內送的追蹤資料會產生清除追蹤資料。** 它是可接受的工作負載在尖峰期間，取得，但永遠應該能夠跟上。 如果清除工作落後，而且絕不會是能夠趕上，BizTalk 追蹤資料庫將會繼續成長，而效能將最終會受到負面影響。  
  
-   **檢閱軟清除和硬清除參數，以確保您會保留足夠的時間，但不是太長的資料。** 如需這些參數的詳細資訊，請參閱[封存和清除 BizTalk 追蹤資料庫](http://go.microsoft.com/fwlink/?LinkID=153816)(http://go.microsoft.com/fwlink/?LinkID=153816)。  
  
-   **如果您只需要清除舊資料，而不需要將它封存在第一次，然後變更 SQL Agent 作業來呼叫預存程序 」 dtasp_PurgeTrackingDatabase"。** 這會略過 「 封存 」 步驟，並只清除。 如需有關這個預存程序和變更的 SQL 代理程式作業來使用它時，請參閱[如何從 BizTalk 追蹤資料庫清除資料](http://go.microsoft.com/fwlink/?LinkID=153817)(http://go.microsoft.com/fwlink/?LinkID=153817)。  
  
-   **如果您需要保留 「 BizTalk 追蹤 」 資料庫封存檔案，請確定您已成功還原，並使用它們的位置中有程序。**  
  
-   **如果您有會清除 BizTalk 追蹤資料庫中，而暫時解決的效能問題，而且您想要將 BizTalk 設定為不再收集追蹤資訊，您可能要考慮關閉全域追蹤。** 如需如何關閉全域追蹤資訊，請參閱主題[如何關閉全域追蹤](http://go.microsoft.com/fwlink/?LinkID=154193)(http://go.microsoft.com/fwlink/?LinkID=154193)。  
  
## <a name="creating-a-dedicated-tracking-host"></a>建立專用的追蹤主控件  
 當選擇**允許主控件追蹤**主機在 BizTalk Server 管理主控台中，該主控件執行個體將會執行追蹤資料解碼 Service (TDDS) 將追蹤的資料，從已啟用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBoxBizTalk 追蹤資料庫的資料庫。 因為 TDDS 可能會耗用資源，請考慮建立的 「 專用 」 追蹤主控件**允許主控件追蹤**啟用選項，而且這不會執行任何其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]程序 （例如配接器或協調流程）。 如果您的 BizTalk 群組包含一個以上的 BizTalk server，也公認的最佳作法是 TDDS 提供高可用性群組中每個伺服器上建立此主控件執行個體。  
  
## <a name="testing-to-measure-maximum-sustainable-tracking-throughput"></a>測試量值最大持續性追蹤輸送量  
 追蹤的完備訊息是資源極大量的活動，若未妥善管理可以有非常不良的效能影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 因此，您應該衡量的最大持續性追蹤輸送量您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境來確保系統持續性，且會在指定的訊息流程速率無限期地執行。 如需有關如何測量最大持續性追蹤輸送量的詳細資訊，請參閱[測量最大持續性追蹤輸送量](http://go.microsoft.com/fwlink/?LinkID=153815)(http://go.microsoft.com/fwlink/?LinkID=153815)。  
  
##  <a name="BKMK_TrackingBP"></a>追蹤的最佳作法  
  
-   **決定您需要在計劃期間追蹤的資訊**： 您應規劃期間，決定設置追蹤，讓您部署專案之後，您可以設定追蹤選項和限制的追蹤資料量所需的資訊請提供您所需的資訊。  
  
-   **不要追蹤所有訊息**： 我們建議您在不都追蹤所有訊息，因為每次觸及訊息時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會製作另一個複本。 您可以改為縮小範圍，藉由追蹤特定連接埠。 這有助於將您的系統效能最大化，並保持資料庫的整齊。  
  
-   **設定追蹤傳送埠和接收埠而不是在管線**： 如果您設定管線的追蹤選項，您也會設定每個管線所使用的連接埠全域追蹤選項。 這又可能會導致更多正在追蹤資料比您想要這會拖慢系統效能。 相反地，您可以設定追蹤選項，傳送連接埠和接收埠。  
  
-   **請考慮各種因素 BizTalk 追蹤資料庫大小**:  
  
    -   當調整 BizTalk 追蹤資料庫的大小，考量到 SQL Server 的因素，例如索引大小應變乘數加入您的計算。  
  
    -   在決定 BizTalk 追蹤資料庫中的訊息大小，加入訊息內容的平均大小的訊息大小是否重要訊息大小相較之下。  
  
    -   若要限制 BizTalk 追蹤資料庫中的訊息大小，請限制您將升級的屬性數目。 如果需要進行路由，應該只使用升級屬性，否則請使用辨別的欄位。  
  
    -   如果協調流程**圖形開始和結束**選項已啟用，請考慮每個圖形中每個協調流程執行個體的啟動和停止事件儲存在 「 BizTalk 追蹤資料庫中。