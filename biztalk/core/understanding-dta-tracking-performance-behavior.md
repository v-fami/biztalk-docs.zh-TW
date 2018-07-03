---
title: 瞭解 DTA 追蹤效能行為 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b1a70951-bfed-435c-97f4-0b28a8e4e4dc
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37c0f1749e87556d52ec9cc1ab84ed64f64a88c6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979703"
---
# <a name="understanding-dta-tracking-performance-behavior"></a>瞭解 DTA 追蹤效能行為
決定 DTA 追蹤之最大持續性輸送量 (MST) 的主要因素如下：  
  
- 系統所需的訊息輸送量，也就是每單位時間所收到的訊息量。  
  
- 針對每一個訊息所追蹤的資料量。  
  
- 資料在清除之前存留於 BizTalkDTADb 資料庫內的時間，也就是資料保留視窗。  
  
- BizTalkDTADb 資料是否會封存和清除。 封存是選擇性，但是清除則必須定期執行。  
  
  還有一件事，所有這些因素有共通： 處 DTA 可以接受和處理的速度 （封存和清除） 的資料。  
  
## <a name="how-the-biztalkdtadb-insert-and-processing-speed-affects-your-system"></a>BizTalkDTADb 插入和處理速度如何影響您的系統  
 現在，讓我們逐步追蹤資料路徑中所述[測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)，並評估 BizTalkDTADb 插入和處理速度系統的各種元件的影響。  
  
 從 trackingdata 和 spool 資料表開始，我們可以想像如果將這些資料表的資料移到 BizTalkDTADb 資料庫的處理序將資料插入 BizTalkDTADb 資料庫時，其速度比不上執行階段插入 trackingdata 和 spool 資料表的速度，則 spool 和 trackingdata 資料表將會開始累積待處理項目。 就短期而言，這未必是一件壞事，只要您知道訊息輸送量將會減少，最後讓待處理項目清空即可。 但是，一旦資料仍然位於 spool 或 trackingdata 資料表中，就無法在 BizTalkDTADb 資料庫中提供這些資料來供 [群組中樞] 頁面中的追蹤查詢或其他任何工具查詢，  因此，無法用這些資料來解決問題。 因此，任何預期的待處理項目期間必須要夠短，好讓追蹤的資訊依然能夠及時提供，以免萬一發生問題，而需要使用 BizTalkDTADb 資料來進行調查。  
  
 透過測試，我們知道待處理項目是否累積的決定因素並不是將追蹤資料移到 BizTalkDTADb 資料庫的這些處理序 (也就是 TDDS 和 TrackedMessages_Copy_BizTalkMsgBoxDb)，而是 BizTalkDTADb 資料庫在接受輸入時的速度。 一般來說，繫結 I/O 的是 BizTalkDTADb 資料庫的資料檔案。 也就是說，BizTalkDTADb 資料庫資料檔案所在的磁碟機速度將會決定整體 DTA 的速度。  
  
## <a name="how-the-amount-of-data-in-biztalkdtadb-affects-io-speed"></a>BizTalkDTADb 中的資料數量如何影響 I/O 速度  
 另一個相關的 I/O 速度的關鍵因素是 BizTalkDTADb 資料庫中的資料量： 為在 BizTalkDTADb 資料庫增加的追蹤資料數量，BizTalkDTADb 資料庫的輸入和處理速度會減少，因為沒有更多的資料當插入新的資料，而這會影響所需的每個插入的 I/O 數量，進行排序。  
  
 這就是封存和清除進入的時候，因為讓 BizTalkDTADb 資料庫不要變得太大而無法保存的就是這些處理序。 基本的概念在於確保 BizTalkDTADb 資料庫大小低於開始在 spool 和 trackingdata 資料表中備份資料的大小。 不過，在 DTA 清除與封存 (BizTalkDTADb) SQL 工作中實作的清除與封存程序也需要資源 （CPU、 記憶體和特別 I/O） 從 BizTalkDTADb 資料庫伺服器，測量 MST 時必須列入考量追蹤。  
  
## <a name="see-also"></a>另請參閱  
 [測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [測量 DAT 追蹤 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md)   
 [尋找 DTA 追蹤的 MST 的秘訣和訣竅](../core/tips-and-tricks-for-finding-mst-of-dta-tracking.md)   
 [調整追蹤資料庫大小的指導方針](../core/tracking-database-sizing-guidelines.md)