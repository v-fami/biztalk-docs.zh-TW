---
title: 如何識別 MessageBox Database1 中的瓶頸 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a039164-5ca6-4cbc-b307-c5d4ae800689
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b25a575f8cd6a3f7d7239ce20cb4d3befdde1966
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297654"
---
# <a name="how-to-identify-bottlenecks-in-the-messagebox-database"></a>如何識別 MessageBox 資料庫中的瓶頸
若要識別 MessageBox 資料庫中的瓶頸，請先確認 SQL Server Agent 服務已啟動。 變更服務的啟動狀態從 「 手動為自動，以重新啟動伺服器，會自動重新啟動服務。  
  
 根據預設，如果 Spool、 TrackingData 或 ApplicationQ 資料表成長，將節流處理 BizTalk 服務。 這些資料表被剪除 SQL 代理程式作業，是，如果未執行，則會導致 Spool 成長，促使節流開始及保護資料庫免於額外的壓力。 請檢查下列效能計數器的狀態：  
  
-   BizTalk: 訊息代理程式 (主控件名稱) 訊息傳遞節流狀態  
  
-   BizTalk: 訊息代理程式 (主控件名稱) 訊息發佈節流狀態  
  
 值為"0"表示沒有發生節流。 "6"的值表示系統正在進行節流，因為資料庫成長。 如需如何解譯這些計數器的值資訊，請參閱[何謂主控件節流？](http://go.microsoft.com/fwlink/?LinkID=154694) (http://go.microsoft.com/fwlink/?LinkID=154694) 和[主控件節流效能計數器](http://go.microsoft.com/fwlink/?LinkID=155285)(http://go.microsoft.com/fwlink/?LinkID=155285) 中的 BizTalk Server 2010 文件。  
  
## <a name="spool-table-growth"></a>多工緩衝處理資料表成長  
 Spool 會開始成長，可能有多種原因。 多工緩衝處理成長的其中一個原因是應用程式佇列逐漸在成長。 因為下游瓶頸及/或資源爭用等原因而無法成長。  
  
 如果應用程式佇列都很小，而 Spool 仍然很大，請確認清除工作會配合。 確定 SQL Agent 服務正在執行，再檢查下列工作是否順利完成：  
  
-   MessageBox_Message_Cleanup_BizTalkMessageBoxDb  
  
-   MessageBox_Parts_Cleanup_BizTalkMessageBoxDb  
  
 如果 MessageZeroSum 資料表很大，則表示已處理訊息。 這表示 DeQueue 已成功完成，並從應用程式佇列資料表中刪除資料和資料列已標示為待刪除。 然而，清除工作無法趕上刪除資料的速度。 如果執行 SQL Server 的電腦發生嚴重的 CPU 爭用情況，會影響清除工作能夠跟上由於 CPU 資源用盡，也可能會發生。  
  
## <a name="application-queue-table-growth"></a>應用程式佇列資料表成長  
 應用程式佇列皆裝載途轉換資料，這些資料一經處理，會清除由 dequeue 加以清除。  
  
 處理這些訊息之後，就可以清理 Spool 資料表 （其中保存著這些資料列的參考）。  
  
 例如，RxHostQ 將資料發行至協調流程 PxHostQ。 此佇列將資料發行到傳送 txhostq，它們各自參考 Spool 資料表中的資料列。 透過系統成功處理特定 hostq 的訊息之後，DeQueue 會刪除這些資料列。 在刪除這些資料列之後，清除工作便可以清除 Spool (不再由這些資料列參考)。  
  
 應用程式佇列成長表示負責清空應用程式佇列的主控件執行個體無法跟上內送的速率。  
  
 例如，因為負責處理協調流程的伺服器受限於 CPU 能力，無法處理得更快，所以協調流程應用程式佇列 (PxHostQ) 可能會成長。 不過，如果接收伺服器快速它可能會發行比協調流程伺服器可以處理導致應用程式佇列成長的速度快。  
  
 另一個協調流程佇列成長的原因可能是由於記憶體競爭的情況。 當許多長時間執行的協調流程執行個體在記憶體中時，會同時具現化時，記憶體膨脹則會間接導致節流縮小執行緒集區，直到記憶體不足的壓力小時。  
  
 為什麼傳送應用程式佇列可能成長的原因是如果下游系統無法接收訊息 （連出從 BizTalk Server） 的速度不夠快。 因此訊息會繼續位於 BizTalk 系統造成應用程式佇列成長。 這可能會導致節流開始運作並降低接收速率，從而影響系統的整體輸送量。  
  
## <a name="trackingdata-table-growth"></a>TrackingData 資料表成長  
 MessageBox 資料庫中的 TrackingData 資料表是在其中攔截器會寫入健全狀況和活動 」 (HAT) 與商務活動監控 (BAM) 追蹤的追蹤資料的轉換資料表。 如果停用了追蹤，這個資料表應該是空的。 根據預設，會啟用管線和協調流程中輸入/輸出事件的 HAT 追蹤。  
  
 如果已啟用訊息內文追蹤，請確定 MessageBox 資料庫伺服器 （也就是具有 「 允許主控件追蹤 」 的主機） 正在執行。 確保與 「 允許主控件追蹤 」 主機正在執行，將會減少瓶頸發生，因為主應用程式將資料從 MessageBox 資料庫中的 TrackingData 資料表移到 BizTalk 追蹤資料庫資料表中的機率。  
  
 它可啟用自訂 HAT 追蹤，例如追蹤自訂事件，在升級的屬性和訊息內文追蹤。 除了 HAT 追蹤資料，BAM 資料也會寫入至 TrackingData 資料表。 追蹤資料解碼服務 (TDDS，啟用追蹤的主控件執行個體上執行) 會負責將這項資料從 MessageBox 資料庫移至 「 BizTalk 追蹤 」 及 「 BAM 主要匯入資料庫。 然後資料成功移動之後，TDDS 便會刪除此資料。 訊息內文追蹤資料是另外由 SQL 代理程式工作 TrackedMessages_Copy_BizTalkMsgBoxDb 來進行移動。  
  
 如果 TDDS 無法跟上的攔截器將資料寫入 TrackingData 資料表的速率，此資料表將會成長，促使節流開始。 這會影響持續性輸送量。 若要減少此問題，請確定至少一部主機正在執行啟用追蹤。  
  
 如果資料仍然在擴增，請確定 「 BizTalk 追蹤資料庫不會成長到無法控制。 此外，封存和清除作業正在執行，而且能夠跟上資料到達的速率。  
  
> [!NOTE]  
>  根據預設，清除作業是無法從 BizTalk 追蹤資料庫的資料表刪除資料，直到已封存這項資料。 如果您不需要封存的追蹤資料，您可以將作業修改清除 BizTalk 追蹤資料庫而不進行封存遵循的步驟[如何從 BizTalk 追蹤資料庫清除資料](http://go.microsoft.com/fwlink/?LinkID=153817)(http://go.microsoft.com/fwlink /？LinkID = 153817)。  
  
## <a name="see-also"></a>另請參閱  
 [資料庫層中的瓶頸](../technical-guides/bottlenecks-in-the-database-tier.md)