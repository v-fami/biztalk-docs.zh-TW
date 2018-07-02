---
title: 規劃追蹤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ffc8573-1b4a-47c7-96ab-0471f43facf5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0c45c61efee90b68efc927d88dbcf6429fe13e2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973823"
---
# <a name="planning-for-tracking"></a>規劃追蹤
追蹤的訊息是由其中的部分的訊息執行個體，例如訊息本文、 訊息屬性和中繼資料會儲存在資料庫中，通常為封存之用的程序。 之後可以檢視追蹤的訊息執行個體組件從 [群組中樞] 頁面中執行查詢[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 除了存取封存的資料，您也可以檢視即時資料，它可以是有用的工具，用來識別並修正問題，在開發或預備環境。  
  
 因為訊息追蹤的程序可以是非常耗用資源，您應該檢閱本主題之前先建立您的計劃。  
  
 如需有關追蹤的詳細資訊，請參閱 <<c0> [ 健全狀況與活動追蹤](http://go.microsoft.com/fwlink/?LinkId=154187)(http://go.microsoft.com/fwlink/?LinkId=154187)。  
  
## <a name="configuring-and-enabling-the-dta-purge-and-archive-sql-agent-job"></a>設定並啟用 DTA 清除與封存 SQL Agent 作業  
 此工作會封存和清除 BizTalk 追蹤資料庫，藉此讓它變得太大的舊資料。 這是不可或缺的狀況良好[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。 大型的追蹤資料庫就會開始影響該查詢追蹤資料庫的追蹤主控件和任何其他處理序的效能。  
  
-   **請確定 DTA 清除與封存 SQL Agent 作業已正確設定、 啟用以及成功完成。** 因為您必須先設定其包含可以在其中寫入封存檔案的目錄，預設不會啟用這項作業。  
  
-   **請確定工作是能夠以最快速度的內送的追蹤資料會產生清除追蹤資料。** 它是可接受的尖峰負載時間時，取得後置作業，但它應該一律能夠趕上。 如果清除工作落後，而且絕不會是能夠趕上，BizTalk 追蹤資料庫將會繼續成長，以及效能會最後會受到負面影響。  
  
-   **檢閱軟清除和硬清除參數，以確保您會保留足夠的時間，但不是會太長的資料。** 如需這些參數的詳細資訊，請參閱[封存和清除 BizTalk 追蹤資料庫](http://go.microsoft.com/fwlink/?LinkID=153816)(http://go.microsoft.com/fwlink/?LinkID=153816)。  
  
-   **如果您只需要清除舊資料，也不需要將它封存到第一次，然後變更 SQL 代理程式作業來呼叫預存程序 」 dtasp_PurgeTrackingDatabase"。** 這會略過 「 封存 」 步驟，並產生只會清除。 如需有關這個預存程序，並變更 SQL Agent 作業來使用它，請參閱[如何從 BizTalk 追蹤資料庫清除資料](http://go.microsoft.com/fwlink/?LinkID=153817)(http://go.microsoft.com/fwlink/?LinkID=153817)。  
  
-   **如果您需要將 BizTalk 追蹤資料庫封存檔案，請確定您已經找備妥已成功還原，並使用它們的處理程序。**  
  
-   **如果您有會藉由清除 BizTalk 追蹤資料庫中，而暫時解決的效能問題，而且您想要設定為不再收集追蹤資訊的 BizTalk，您可能要考慮關閉全域追蹤。** 如需如何關閉全域追蹤資訊，請參閱主題[如何關閉全域追蹤](http://go.microsoft.com/fwlink/?LinkID=154193)(http://go.microsoft.com/fwlink/?LinkID=154193)。  
  
## <a name="creating-a-dedicated-tracking-host"></a>建立專用的追蹤主控件  
 當選擇**允許主控件追蹤**在 BizTalk Server 管理主控台中，該主控件執行個體的主機將執行追蹤資料解碼 Service (TDDS) 將追蹤的資料，從已啟用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBoxBizTalk 追蹤資料庫的資料庫。 因為 TDDS 可能耗用大量資源，請考慮建立 「 專用 」 追蹤主控件為其**允許主控件追蹤**啟用選項，而且這不會執行任何其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]程序 （例如配接器或協調流程）。 如果您的 BizTalk 群組包含一個以上的 BizTalk server，它也會被視為最佳作法為 TDDS 提供高可用性群組中的每一部伺服器上建立此主控件執行個體。  
  
## <a name="testing-to-measure-maximum-sustainable-tracking-throughput"></a>測試以測量最大持續性追蹤輸送量  
 追蹤的完備訊息是大量資源的大量活動，若未妥善管理可以有的效能相當不利的影響[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 因此，您應該測量最大持續性追蹤輸送量您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，以確保系統持續性，且將會在指定的訊息流程速率無限期地執行。 如需有關如何測量最大持續性追蹤輸送量的詳細資訊，請參閱 <<c0> [ 測量最大持續性追蹤輸送量](http://go.microsoft.com/fwlink/?LinkID=153815)(<http://go.microsoft.com/fwlink/?LinkID=153815>)。  
  
##  <a name="BKMK_TrackingBP"></a> 追蹤的最佳作法  
  
- **判斷您要追蹤計劃期間所需的資訊**： 您應該決定的規劃階段需要追蹤，以便您部署專案之後您可以設定追蹤選項，並限制追蹤資料量的資訊請提供您所需的資訊。  
  
- **不會追蹤所有訊息**： 我們建議您，您不會都追蹤所有訊息，因為每次觸及訊息時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會建立另一個複本。 您可以改為縮小範圍，藉由追蹤特定連接埠。 這有助於您系統的效能最大化，並保持資料庫的整齊。  
  
- **設定追蹤傳送埠和接收埠而不是在管線**： 如果您設定在管線的追蹤選項時，您也會設定每個管線所使用的連接埠的全域追蹤選項。 這接著可能會導致更多正在追蹤資料比您想，這將會變慢系統效能。 相反地，您可以設定追蹤選項，傳送連接埠和接收埠。  
  
- **請考慮各種因素，當您調整 BizTalk 追蹤資料庫的大小**:  
  
  -   當調整 BizTalk 追蹤資料庫的大小，請藉由將計算的緊急應變乘數考量 SQL Server 的因素，例如索引大小。  
  
  -   在決定 BizTalk 追蹤資料庫中的訊息大小，請加入訊息內容的平均大小的訊息大小很重要，如果相較於訊息大小。  
  
  -   若要限制 BizTalk 追蹤資料庫中的訊息大小，限制您將升級的屬性數目。 如果您基於路由目的需要應該只使用升級屬性，否則請使用辨別的欄位。  
  
  -   如果協調流程**流程化開始與結束**啟用選項，請考慮每個協調流程執行個體中每個圖形的啟動和停止事件儲存在 「 BizTalk 追蹤資料庫中。