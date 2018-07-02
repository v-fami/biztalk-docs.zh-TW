---
title: 檢查清單： 執行每月效能檢查 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa103777-af4d-480d-abc7-3c4718f493c1
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e580b95288ec7ac23be93d99c56c3cfc781374c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992527"
---
# <a name="checklist-performing-monthly-performance-checks"></a>檢查清單： 執行每月效能檢查
本主題列出您應該遵循以避免發生效能問題的每月為基礎的最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。  


|                                     步驟                                     |                                                                                                                                                                                                                                                                                                                              參考                                                                                                                                                                                                                                                                                                                              |
|-------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          判斷您要追蹤計劃期間所需的資訊          |       您應該在規劃階段決定需要追蹤哪些資訊，如此在您部署專案之後便可設定追蹤選項，並限制追蹤資料量，僅取得您所需的資訊。 **附註：** 如需與追蹤相關的最佳作法的詳細資訊，請參閱[規劃追蹤](../technical-guides/planning-for-tracking.md)本指南中並[健全狀況與活動追蹤](http://go.microsoft.com/fwlink/?LinkId=154187)(<http://go.microsoft.com/fwlink/?LinkId=154187>) 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件。        |
|                           不會追蹤所有訊息                           |                                                                                                                                                    我們建議您，您不會追蹤所有訊息，因為每次觸及訊息時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會建立另一個複本。 您可以改為縮小範圍，藉由追蹤特定連接埠。 這有助於您系統的效能最大化，並保持資料庫的整齊。                                                                                                                                                     |
|                  不要追蹤 」 的協調流程的所有事件                   |                                                                                                                                                                          追蹤之協調流程的所有事件，可能會增加 dta_DebugTrace 和 dta_MessageInoutEvents 資料表的大小。 如需有關如何停用協調流程的追蹤的相關指示，請參閱[若要停用協調流程的追蹤](../technical-guides/how-to-disable-tracking.md#BKMK_DisableOrchTracking)。                                                                                                                                                                           |
|     設定追蹤傳送埠和接收埠而不是在管線     |                                                                                                                                                                         如果您設定在管線的追蹤選項時，您也會設定每個管線所使用的連接埠的全域追蹤選項。 這接著可能會導致更多正在追蹤資料比您想，這將會變慢系統效能。 相反地，您可以設定追蹤選項，傳送連接埠和接收埠。                                                                                                                                                                         |
|                調整節流根據資源使用量                |     中的節流[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供完善的保護系統的預設設定。 監視效能計數器，瞭解節流狀態，請參閱是否正在進行節流，然後自行測量節流的資源為基礎 （例如，資料庫大小或記憶體使用量） 低於或使用量過高，然後再調整節流臨界值增加，或隨之減少。 如需詳細資訊，請參閱 <<c0> [ 調整節流閾值： 何時和為何](http://go.microsoft.com/fwlink/?LinkId=154188)(<http://go.microsoft.com/fwlink/?LinkId=154188>)。     |
|                 如果可能，請使用 PassThruTransmit 管線                 |                                                                                                                                                                                                                                                       如果任何文件處理不需要傳送訊息至其目的地之前，請使用 PassThruTransmit 管線，而不是 XML 傳送管線。                                                                                                                                                                                                                                                        |
| 請考慮各種因素，當您調整 BizTalk 追蹤資料庫的大小 | -當調整 BizTalk 追蹤資料庫的大小，請藉由將計算的緊急應變乘數考量 SQL Server 的因素，例如索引大小。<br />-在決定 BizTalk 追蹤資料庫中的訊息大小，請加入訊息內容的平均大小的訊息大小很重要，如果相較於訊息大小。<br />-若要限制 BizTalk 追蹤資料庫中的訊息大小，限制您將升級的屬性數目。<br />-如果啟用協調流程偵錯工具選項時，考慮到協調流程中的每個圖形的狀態儲存在 「 BizTalk 追蹤資料庫中。 |
|               套用硬體解決方案，以避免磁碟爭用               |           若要避免磁碟爭用情況，MessageBox 資料庫中的，執行下列作業：<br /><br /> -使用高速的磁碟<br />部署在高速 SAN 上的資料庫<br />-區隔到追蹤資料庫不同的專用伺服器上的 MessageBox 資料庫<br />-相應增加的 Cpu，並將更多的 Cpu 加入至專用的 MessageBox 資料庫伺服器<br />-將分頁檔和/或 MSDTC 記錄移至另一個磁碟機<br /><br /> 如需有關如何避免資料庫爭用的詳細資訊，請參閱[如何避免磁碟爭用](http://go.microsoft.com/fwlink/?LinkId=158809)(<http://go.microsoft.com/fwlink/?LinkId=158809>)。           |

## <a name="see-also"></a>另請參閱  
 [例行性效能檢查清單](../technical-guides/routine-performance-checklists.md)   
 [檢查清單：執行每週效能檢查](../technical-guides/checklist-performing-weekly-performance-checks.md)