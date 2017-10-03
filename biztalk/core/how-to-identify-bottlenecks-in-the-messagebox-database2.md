---
title: "如何識別 MessageBox Database2 中的瓶頸 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10b2eb1e-541c-457d-9735-ac6fb069b209
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69966f0f3ecff5a27788c9a92d4e3f1ac0eae68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-messagebox-database"></a>如何識別 MessageBox 資料庫中的瓶頸
若要識別 MessageBox 資料庫中的瓶頸，請先確認 SQL Server Agent 服務已啟動。 將服務的啟動狀態從「手動」變更為「自動」，如此一來，即使重新啟動伺服器，服務也會自動重新啟動。  
  
 根據預設，如果 Spool、TrackingData 或 ApplicationQ 資料表成長，BizTalk 服務就會減緩處理速度 (節流)。 SQL 代理程式工作會對這些資料表進行剪除；如果此項工作未執行，就會導致 Spool 成長，並促使節流開始作用，以保護資料庫不再接受額外的壓力。 請檢查下列效能計數器的狀態：  
  
-   BizTalk: 訊息代理程式 (主控件名稱) 訊息傳遞節流狀態  
  
-   BizTalk: 訊息代理程式 (主控件名稱) 訊息發佈節流狀態  
  
 0 的值表示沒有發生節流。 6 的值表示因為資料庫成長，系統正在進行節流。 如何解釋這些計數器的其他值，請參閱相關文件。  
  
## <a name="spool-table-growth"></a>Spool 資料表成長  
 Spool 會開始成長，可能有多種原因。 Spool 成長的其中一個原因，是應用程式佇列逐漸在成長。 這些佇列可能會因為下游瓶頸及/或資源爭用等因素而成長。  
  
 如果應用程式佇列小，而 Spool 仍然很大，請確認清除工作是否能應付成長速度。 確定 SQL Agent 服務正在執行，再檢查下列工作是否順利完成：  
  
-   MessageBox_Message_Cleanup_BizTalkMessageBoxDb  
  
-   MessageBox_Parts_Cleanup_BizTalkMessageBoxDb  
  
 如果 MessageZeroSum 資料表很大，表示已經處理過訊息 (DeQueue 已成功完成，並從應用程式佇列資料表中刪除了資料)，並且在資料列加上標幟以待刪除。 然而，清除工作無法趕上刪除資料的速度。 其中一個原因是如果在 SQL Server 電腦發生嚴重的 CPU 爭用情況，影響的清除工作能夠跟上由於 CPU 資源用盡。  
  
## <a name="application-queue-table-growth"></a>應用程式佇列資料表成長  
 應用程式佇列會裝載在途轉換資料，這些資料一經處理，就會由 DeQueue 加以清除。  
  
 在處理這些訊息之後，便可以清理 Spool (其中保存著這些資料列的參考)。  
  
 例如，RxHostQ 將資料發行至協調流程 PxHostQ，後者又接著發行資料至傳送的 TxHostQ，它們各自參考 Spool 資料表中的一列。 透過系統成功處理特定 HostQ 的訊息之後，DeQueue 會刪除這些資料列。 在刪除這些資料列之後，清除工作便可以清除 Spool (不再由這些資料列參考)。  
  
 應用程式佇列成長，代表負責清空應用程式佇列的主控件執行個體無法跟上內送速率 (亦即，發佈至特定應用程式佇列之訊息傳遞速率)。  
  
 例如，因為負責處理協調流程的伺服器受限於 CPU 能力，無法處理得更快，所以協調流程應用程式佇列 (PxHostQ) 可能會成長。 但是，如果接收伺服器很快，也可能會因為其發行速度快過協調流程伺服器所能處理的速度，而導致應用程式佇列成長。  
  
 協調流程佇列成長的另一個原因，可能是記憶體爭用的關係；這種情況是記憶體中同時有許多長時間執行的協調流程執行個體一起具現化，造成記憶體壅塞，而間接促使節流縮小執行緒集區，直到記憶體壓力減緩為止。 傳送應用程式佇列可能成長的其中一個原因，是下游系統接收 (從 BizTalk 傳出的) 訊息的速度不夠快。 如此，訊息就會繼續留在 BizTalk 系統內，造成應用程式佇列成長，最後也會促使節流開始降低接收速率，從而影響系統的整體輸送量。  
  
## <a name="trackingdata-table-growth"></a>TrackingData 資料表成長  
 MessageBox 資料庫中的 TrackingData 資料表是在其中攔截器寫入訊息和服務執行個體追蹤和 BAM 追蹤的追蹤資料的轉換資料表。 如果停用了追蹤，這個資料表應該是空的。 預設會啟用管線和協調流程中輸入/輸出事件的追蹤中的訊息與服務執行個體。  
  
 如果已啟用訊息內文追蹤，請確定 MessageBox 伺服器 (亦即，「允許主控件追蹤」的主控件) 正在執行。 當它將資料由 MessageBox 資料庫中的 TrackingData 資料表移至 BizTalkDTADb 資料表時，將會減少瓶頸。  
  
 您可啟用自訂的訊息和追蹤的服務執行個體，例如，在升級的屬性和訊息內文追蹤，追蹤的自訂事件。 除了追蹤資料，BAM 資料也會寫入到這個資料表。 TDDS (已啟用追蹤的主控件) 必須負責將此資料從 MessageBox 資料庫移至 BizTalkDTADb 和 BAMPrimaryImport 資料庫，並在成功移動之後，刪除此資料。 訊息內文追蹤資料是另外由 SQL 代理程式工作 TrackedMessages_Copy_BizTalkMsgBoxDb 來進行移動。  
  
 如果 TDDS 無法跟上攔截器將資料寫入 TrackingData 資料表的速率，則此資料表將會成長，促使節流開始作用，終究影響到持續性輸送量。 若要減輕這個問題，請確定至少有 1 個啟用追蹤的主控件正在執行。  
  
 如果資料仍然在擴增，請檢查 BizTalkDTADb 資料庫，以確定資料庫未成長到無法控制的地步。 確定封存和清除工作都在執行中，並且跟得上資料到達的速率。  
  
> [!NOTE]
>  BizTalkDTADb 資料表的資料必須已經封存，否則清除工作無法刪除其中的資料。  
  
 確認 TrackingData 資料表沒有一直在成長。 確定至少有 1 個執行中的主控件執行個體啟用了追蹤功能 (TDDS)。 如果 BizTalkDTADb 資料庫已經成長得過大，可能對 TDDS 從 MessageBox 資料庫移動資料至 BizTalkDTADb 資料庫的能力產生不利影響。  
  
 TrackingData 資料表成長會促使節流開始作用，從而影響執行階段持續性輸送量。