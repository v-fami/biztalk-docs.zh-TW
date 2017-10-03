---
title: "檢查清單： 執行每週效能檢查 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c36fe78d-1be8-49f2-97ce-b6d0cadffab8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7898702e42253ab1155b0a6e32af3008800db1f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-performing-weekly-performance-checks"></a>檢查清單： 執行每週效能檢查
本主題列出與避免效能問題時，所應遵循於每週的最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。  
  
|步驟|參考|  
|-----------|---------------|  
|資料庫自動成長設為固定的號碼|資料庫自動成長應該設定為固定數目的 mb，而不是百分比，特別是針對 MessageBox 和 「 追蹤 」 (DTA) 資料庫。 取決於您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式和輸送量、 MessageBox 和追蹤資料庫可以變得很大。 如果自動成長設為百分比，則自動成長也很嚴重。<br />-如果是新的系統和靜態的大小不已明確建立，然後啟用自動成長選項設定的檔案，並指定檔案成長以 mb 為單位。 成長遞增值通常是不能大於 100 MB （適用於大型的檔案）、 10 MB （適用於中小型檔案） 或 1 MB （適用於小型檔案）。 請參閱**附錄 B-建議使用 BizTalk Server 資料庫組態**區段[BizTalk Server 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/p/?LinkID=153594)(http://go.microsoft.com/fwlink/p/?LinkID = 153594) 的每個建議的檔案大小的資料表[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。|  
|限制您使用 SQL Server Profiler 監視的事件|使用 SQL Server Profiler 來監視只有您感興趣的事件。 如果追蹤變得太大，您可以篩選，收集事件資料的子集，根據您想要的資訊。 監視太多事件會增加伺服器與監視處理序的負擔，且會使得追蹤檔案或追蹤資料表增長過大，尤其是需要花費長時間的監視處理序更是如此。|  
|設定訊息批次處理以增進配接器效能|最小化配接器執行，藉由結合到單一批次中的多個作業的交易的數目。<br />-限制批次大小為基礎的批次中除了訊息計數的位元組總數。 如需限制批次大小的詳細資訊，請參閱[設定批次處理，以改善配接器效能](../technical-guides/configuring-batching-to-improve-adapter-performance.md)。|  
|調整大型訊息閾值|若要改善輸送量，增加的大型訊息閾值，這會降低大型緩衝處理的訊息數目在對應的磁碟。|  
|調查記憶體流失 」 或 「 BizTalk Server 程序中的記憶體不足例外狀況|BizTalk 處理程序中的記憶體流失可能會因為各種原因而發生。 請參閱 Microsoft 知識庫文章 918643，[記憶體遺漏或 BizTalk Server 程序中的記憶體不足例外狀況的疑難排解](http://go.microsoft.com/fwlink/p/?LinkId=157212)(http://go.microsoft.com/fwlink/p/?LinkId = 157212) 有關的案例中就可能會發生記憶體流失，和如何加以修正。|  
  
## <a name="see-also"></a>另請參閱  
 [例行性效能的檢查清單](../technical-guides/routine-performance-checklists.md)   
 [檢查清單： 執行每月效能檢查](../technical-guides/checklist-performing-monthly-performance-checks.md)