---
title: 引擎保存性與耐久性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9bd209e9-75d2-422f-b3b2-377986f41f2f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13f9f3f1a02ddfe84a963704476e867783f31042
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242590"
---
# <a name="engine-persistence-and-durability"></a>引擎保存性與耐久性
本節說明 BizTalk Server 如何透過 SQL Server 將程序狀態存放至磁碟，可靠的整合鬆散耦合的商務程序。 藉由在適當的時間保存狀態、利用交易，系統能確保即使發生硬體或軟體故障，程序狀態也不會遺失。 這稱為系統耐久性。  
  
## <a name="loosely-coupled-business-process-management"></a>鬆散耦合的商務程序管理  
 整合現有系統以執行單一邏輯商務程序需要對現有系統外部的程序狀態進行管理。 不管商務程序是長期執行或是短期有效，程序狀態都必須個別維護，才能避免將系統緊密耦合在一起所導致的自訂通訊路徑劇增。  
  
 很明顯地，若該商務程序相當重要，執行商務程序執行個體的狀態就必須非常可靠。 為確保商務程序是可靠且耐久的，BizTalk 利用 SQL Server 交易將程序狀態和商務資料保存至資料庫中的磁碟，稱為 MessageBox 資料庫。 如需 MessageBox 資料庫的詳細資訊，請參閱[MessageBox 資料庫](../core/the-messagebox-database.md)。  
  
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，每則訊息以及除去最無關緊要的商務程序執行個體後的所有商務程序執行個體 (例如協調流程執行個體)，在處理期間都至少會保存在 MessageBox 資料庫中一次。  
  
## <a name="persistence-and-sustainability"></a>保存性與持續性  
 BizTalk Server 保存所有訊息及大部分協調流程的事實已對持續性，如中所述的直接影響[何謂持續性效能？](../core/what-is-sustainable-performance.md) 當訊息送達 MessageBox 資料庫中時，它們是連接到等待訂閱者 （例如，協調流程和傳送連接埠），並排入佇列或發佈至 messagebox SQL 資料表，以等待收取和處理它們的 「 訂閱者 」。 某些抵達的訊息會啟動新的訂閱者執行個體。 其他訊息抵達並經由相互關聯路由至正在執行訂閱者 (如相互關聯協調流程) 的等候執行個體。  
  
 為了讓相互關聯的協調流程得以繼續處理，必須將抵達的相互關聯訊息保持在未封鎖的狀態。 為便於進行，BizTalk 即使在高負載狀況下也會盡可能地確保能夠繼續接收訊息 (啟動中和相互關聯)，讓等待相互關聯訊息的訂閱者可以完成程序，並騰出空間供更多程序執行。 這表示接收訊息的速度可能比處理訊息與從 MessageBox 資料庫移除訊息的速度要快，因此會建置訊息積存。 做為存放及轉寄的技術，BizTalk 提供此類的緩衝是理所當然的，不過，若接收速率一直都大於處理速率，就會導致一些問題，也就是導致大量積存。  
  
 BizTalk Server 所接收或建立的每則訊息都是永遠不變的。 也就是說，一旦接收或建立之後，其內容便無法變更。 此外，所接收的訊息可能會有多個訂閱者。 特定訊息的每個訂閱者都會參考該訊息相同且單一的複本。 當此方法將儲存空間最小化時，必須保留每則訊息的參考計數，而且必須定期維護，以避免參考計數為 0 的訊息。  
  
 若在 MessageBox 資料庫中可建置夠大的積存，該資料庫的維護程序 (針對每個 MessageBox 資料庫以一組 SQL 工作的型式實作) 會落後，而且若沒有機會更新的話，最後會造成如磁碟空間不足的問題。 為避免這種情況，BizTalk Server 提供節流機制，可在 MessageBox 資料庫積存到達某些使用者設定的層級時，降低訊息接收速率。 如需節流的詳細資訊，請參閱[最佳化資源使用量透過主控件節流](../core/optimizing-resource-usage-through-host-throttling.md)。  
  
 假設所有的活動與程序都提供持續性，則某段時間的主要持續性量值就是不允許無限制成長的積存。 換句話說，經過一段時間，在高低峰輸送量層級之間必須有一個平衡值，讓 MessageBox 資料庫能夠保持常數值與可管理的平均積存。 積存的主要量值為多工緩衝處理表格的深度，以名稱如右的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 效能計數器公開：BizTalk:Message Box:General Counters:Spool Size。 如需有關此效能計數器的詳細資訊，請參閱[訊息方塊效能計數器](../core/message-box-performance-counters.md)。  
  
 如需有關如何使用多工緩衝處理大小和其他計數器來決定系統可持續之輸送量上限的詳細資訊，請參閱[測量最大持續引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md)。  
  
## <a name="recommendations"></a>建議  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會保存所有的訊息與大部分的協調流程，如果疏於理會，則訊息將會無限制的積存，而可能產生諸如磁碟空間不足之類的問題。 積存的主要量值為 MessageBox 多工緩衝處理表格的深度，以名稱如右的效能計數器公開：BizTalk:Message Box:General Counters:Spool Size。  
  
 考慮可持續的輸送量時，多工緩衝處理大小必須維持穩定的平均值一段時間。 也就是說，多工緩衝處理無法繼續無限制的成長。 在[測量最大持續引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md)更詳細討論此行為是，其會利用多工緩衝處理大小和其他效能提供一個方法來決定系統可持續的最大輸送量指標。  
  
## <a name="see-also"></a>另請參閱  
 [測量最大持續性引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [什麼是持續性效能？](../core/what-is-sustainable-performance.md)   
 [效能秘訣和訣竅](../core/performance-tips-and-tricks.md)   
 [訊息方塊效能計數器](../core/message-box-performance-counters.md)