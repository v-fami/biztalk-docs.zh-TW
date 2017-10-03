---
title: "檢查清單： 執行每月效能檢查 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa103777-af4d-480d-abc7-3c4718f493c1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3c1c84248fc3f5a7efdcc7e4df3f62b23bfcc82
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-performing-monthly-performance-checks"></a>檢查清單： 執行每月效能檢查
本主題列出為避免效能問題的每月為基礎，您應該遵循的最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。  
  
|步驟|參考|  
|-----------|---------------|  
|判斷您需要在計劃期間追蹤的資訊|您應該在規劃階段決定需要追蹤哪些資訊，如此在您部署專案之後便可設定追蹤選項，並限制追蹤資料量，僅取得您所需的資訊。 **注意：**與追蹤相關的最佳作法的詳細資訊，請參閱[規劃追蹤](../technical-guides/planning-for-tracking.md)本指南中和[健全狀況與活動追蹤](http://go.microsoft.com/fwlink/?LinkId=154187)(http://go.microsoft.com/fwlink/?LinkId = 154187) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件。|  
|不要追蹤所有訊息|我們建議您在不追蹤所有訊息，因為每次觸及訊息時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會製作另一個複本。 您可以改為縮小範圍，藉由追蹤特定連接埠。 這有助於將您的系統效能最大化，並保持資料庫的整齊。|  
|不要追蹤 」 的協調流程的所有事件|追蹤協調流程的所有事件，可能會增加 dta_DebugTrace 和 dta_MessageInoutEvents 資料表的大小。 如需有關如何停用協調流程的追蹤的指示，請參閱[停用協調流程的追蹤](../technical-guides/how-to-disable-tracking.md#BKMK_DisableOrchTracking)。|  
|設定追蹤傳送埠和接收埠而不是在管線|如果您設定管線的追蹤選項，您也會設定每個管線所使用的連接埠全域追蹤選項。 這又可能會導致更多正在追蹤資料比您想要這會拖慢系統效能。 相反地，您可以設定追蹤選項，傳送連接埠和接收埠。|  
|調整節流根據資源使用量|在 節流[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供完善保護系統的預設設定。 監視效能計數器的瞭解節流狀態，請參閱是否節流正在進行中，則量測計自行如果依據上節流的資源 （例如，資料庫大小或記憶體使用量） 正在進行或使用量過高，然後再調整 節流設定臨界值會啟動，或據以關閉。 如需詳細資訊，請參閱[調整節流閾值： 時間和原因](http://go.microsoft.com/fwlink/?LinkId=154188)(http://go.microsoft.com/fwlink/?LinkId=154188)。|  
|盡可能使用 PassThruTransmit 管線|如果沒有任何文件處理需要傳送訊息至其目的地之前，使用 PassThruTransmit 管線，而不是 XML 傳送管線。|  
|請考慮各種因素 BizTalk 追蹤資料庫大小|-當調整 BizTalk 追蹤資料庫的大小，請將應變乘數加入至您的計算帳戶 SQL Server 的因素，例如索引大小。<br />-在決定 BizTalk 追蹤資料庫中的訊息大小，如果加上訊息內容的平均大小的訊息大小重大訊息大小相較之下。<br />-若要限制 BizTalk 追蹤資料庫中的訊息大小，請限制您將升級的屬性數目。<br />-如果啟用協調流程偵錯工具選項時，考慮到協調流程中每個圖形的狀態儲存在 「 BizTalk 追蹤資料庫中。|  
|套用的硬體解決方案，以避免磁碟爭用|若要避免磁碟爭用情況，MessageBox 資料庫中的，執行下列作業：<br /><br /> -使用高速磁碟<br />-將部署在高速 SAN 上的資料庫<br />-區隔到追蹤資料庫不同的專用伺服器上的 MessageBox 資料庫<br />-Cpu 向上延展和專用的 MessageBox 資料庫伺服器中加入更多的 Cpu<br />-將分頁檔及/或 MSDTC 記錄檔移到另一個磁碟機<br /><br /> 如需避免資料庫競爭的詳細資訊，請參閱[如何避免磁碟爭用](http://go.microsoft.com/fwlink/?LinkId=158809)(http://go.microsoft.com/fwlink/?LinkId=158809)。|  
  
## <a name="see-also"></a>另請參閱  
 [例行性效能的檢查清單](../technical-guides/routine-performance-checklists.md)   
 [檢查清單： 執行每週效能檢查](../technical-guides/checklist-performing-weekly-performance-checks.md)