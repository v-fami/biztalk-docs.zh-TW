---
title: "影響最大持續性效能的因素 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum sustainable throughput (MST), maintenance
- monitoring, maximum sustainable thoughput (MST)
- maintaining, maximum sustainable thoughput (MST)
- maximum sustainable throughput (MST), monitoring
- maximum sustainable throughput (MST), load patterns
- maximum sustainable throughput (MST), sustainable load test
- sustainable performance
ms.assetid: 99b99655-bc77-425c-a133-204781d7c430
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be96ad552abef66e2a401e334da1c27ee0e08cd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="factors-that-affect-maximum-sustainable-performance"></a>影響可維持之效能上限的因素
可維持的最大輸送量直接受廣泛的因素影響，如可用的伺服器資源、解決方案使用的功能類型、訊息大小和整體訊息負載等因素。 當然還需考量其他因素，但是並非顯而易見。 預估可維持之效能的上限時也應該考慮下列因素：  
  
## <a name="load-patterns"></a>負載模式  
 訊息不一定會以可預期的一致速率傳送到實際 BizTalk Server 環境。 更典型的方式是，商務需求會指定 BizTalk Server 以呈現尖峰期與低峰期的變動速率來處理訊息。 出現高峰時，BizTalk Server 處理要求可能會從閒置狀況快速跳到加速狀況，此時接收訊息的速度會比處理的速度還快。 在此實例中，發佈訊息會積存在 MessageBox 資料庫中，直到 BizTalk 將積存訊息傳遞到適當的訂閱者。 只要 BizTalk Server 能夠處理尖峰負載期間累積的積存訊息，就不會產生問題。  
  
 因為通常訊息流到 BizTalk Server 環境的模式會有所變動，所以測試實例應該延長執行時間，以確保解決方案可以無限地保持所需的輸送量，一段時間後可從所有尖峰負載復原。  
  
## <a name="monitoring-and-maintenance-activities"></a>監控和維護活動  
 在生產環境方案生命週期期間沒有監視的主機和維護活動，可能會影響 BizTalk 效能，所以應該納入任何測試實例。 這些活動包括：  
  
-   **BizTalk 管理主控台查詢**這些查詢耗用資源並影響整體輸送量取決於型別和查詢的頻率。  
  
-   **備份、 封存和清理活動**這些活動也會耗用資源，並應該納入任何測試實例。 所有 BizTalk Server 資料庫都應定期備份，而其交易記錄會被截斷。 若是不執行交易記錄，則可能會無限增加，而耗用交易資料庫的所有可用磁碟空間。 若使用追蹤，則應定期清理追蹤資料庫並選擇性地封存資料，以避免資料庫變得過大。 如需維護 BizTalk Server 資料庫的詳細資訊，請參閱[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)。  
  
## <a name="see-also"></a>另請參閱  
 [測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)