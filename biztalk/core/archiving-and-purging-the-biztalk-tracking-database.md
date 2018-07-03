---
title: 封存和清除追蹤資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7014cf31-86e8-4829-8055-056442329009
caps.latest.revision: 37
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3556618df02c7a8c9df5d0d55c27eb69ed91eae2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000848"
---
# <a name="archive-and-purge-the-biztalkdtadb-database"></a>封存與清除 BizTalkDTADb 資料庫

## <a name="overview"></a>概觀
BizTalk Server 所處理的資料會越來越多，「BizTalk 追蹤」(BizTalkDTADb) 資料庫的大小會持續擴大。 若未發現此成長現象將會降低系統效能，並且可能會在 Tracking Data Decode Service (TDDS) 中產生錯誤。 除了一般追蹤資料以外，追蹤的訊息也會累積在 MessageBox 資料庫，導致磁碟效能變差。  
  
BizTalk Server 會自動使用 「 DTA 清除與封存 」 作業的兩個程序。 從「BizTalk 追蹤」資料庫封存和清除資料庫，可保有狀況良好的系統並封存您的追蹤資料供以後使用。 因為「BizTalk 追蹤」資料庫封存會隨時間累積並消耗磁碟空間，定期將「BizTalk 追蹤」資料庫封存移到次要的儲存媒體是很好的方法。  
  
 當您從「BizTalk 追蹤」資料庫清除資料時，DTA 清除和封存工作會清除不同類型的追蹤資訊，例如訊息和服務執行個體資訊、協調流程事件資訊，和規則引擎追蹤資料。  
  
 追蹤資料記錄的期限，是以追蹤資料插入「BizTalk 追蹤」資料庫的時間為依據。 DTA 清除與封存工作使用時間戳記，以持續驗證記錄是否比資料的存留窗期還舊。 在每個存留窗期過後，「BizTalk 追蹤」資料庫會被封存，並且建立新的封存檔。 只要作業排程所指定的每個 SQL Server Agent 作業間隔時間一到，所有已完成而比存留窗期還舊的追蹤資料都會被清除。  
  
 BizTalk Server 使用軟清除和硬清除的概念。 軟清除是用來清除已完成的執行個體，而硬清除只可用來清除未完成的執行個體。  
  
## <a name="soft-purge"></a>軟清除
  
 在 DTA 封存與清除工作中，LiveHours 和 LiveDays 參數的總和是您想在 BizTalk Server 環境中維護之資料的存留窗期。 早於此資料存留窗期之已完成執行個體的所有相關資料都會被清除。 DTA 封存與清除工作預設並未啟用。 您必須先設定妥然後再啟用這項工作。  
  
 例如，您可以設定 DTA 清除與封存工作執行每隔 20 分鐘，並設定 LiveHours livehours=1 且 LiveDays = 0。 第一次這個 SQL Server Agent 作業執行時 (T0)，藉由建立封存需要追蹤資料庫的備份和項目會儲存在資料庫中使用此時間戳記。 必須要成功封存，才能清除追蹤資料。 如果封存成功，所有與 1 個小時前完成的執行個體相關的資料都會被清除。 每次執行作業時，過去 1 小時前完成的資料會被清除。 在第 3 次執行時 (一小時後)，會建立新的封存，其中包含所有在最近一個小時區段內被插入追蹤資料庫的所有執行個體。  
  
 以下是如何設定封存與清除步驟 DTA 清除與封存作業以符合此範例中：  
  
```  
exec dtasp_BackupAndPurgeTrackingDatabase  
1, --@nLiveHours 1,   
0, --@nLiveDays   
1, --@nHardDeleteDays   
‘\\server\backup’, --@nvcFolder   
null, --@nvcValidatingServer   
0 --@fForceBackup Soft purge process  
```  
  
 最後一次備份的時間戳記會儲存在「BizTalk 追蹤」資料庫中，確保只有當資料在先前的封存中時，才可以清除資料。 為求達到更高的可靠性，封存大約會重疊 10 分鐘。 下圖是依照上述範例，顯示軟清除的流程。 請注意，封存和清除作業未必在同一時間發生。  
  
 **軟清除流程**  
  
 ![軟清除流程](../core/media/archivingandpurging.gif "archivingandpurging")  
  
## <a name="hard-purge"></a>硬清除
  
 由於軟清除只能清除與已完成執行個體相關的資料，如果您有許多無限期執行的迴圈執行個體，那麼您的追蹤資料庫會變大，且永遠無法清除這些執行個體。 硬清除日期允許刪除比指定間隔舊的所有資訊，但不會刪除指出服務存在的資訊。 您設定硬清除 using <strong>@nHardDeleteDays</strong>參數中的封存與清除步驟在 DTA 封存與清除工作。 硬清除設定值始終都應大於軟清除設定值。 亦即<strong>@nHardDeleteDays</strong>應大於總和<strong>@nLiveHours</strong>並<strong>@nLiveDays</strong>。  
  
 封存和清除包括下表中描述的功能：  
  
|功能|描述|  
|-------------|-----------------|  
|硬清除|可讓您設定時間間隔，清除比指定日期舊且不完整的執行個體資訊。|  
|將追蹤的訊息複製到追蹤資料庫|使用 [CopyTrackedMessageToDTA] 選項，您可以直接將追蹤的訊息從 MessageBox 伺服器複製到您的「BizTalk 追蹤」資料庫。 若要使用「DTA 清除與封存」清除與封存工作來清除資料，則這是有必要的。|  
|封存驗證|可讓您選擇設定次要資料庫伺服器，以驗證它們建立時的封存。|  
|追蹤多個 BizTalk 追蹤資料庫版本的支援|可讓您使用追蹤支援與 BizTalk Server 資料庫封存。|  
|減少追蹤資料|連續減少儲存的追蹤資料數目，而不減少任何已產生的追蹤資訊。 這樣會造成追蹤資料庫的成長變慢。|  
|更快速的追蹤作業，資料庫結構描述大幅最佳化|可讓您尋找在大型資料庫; 上的訊息和服務執行個體時，用於追蹤工作這項功能已大幅最佳化。|  
  
> [!NOTE]
>  如果效能問題是藉由清除 BizTalk 追蹤資料庫而暫時解決，而您想要將 BizTalk 設定為不再收集追蹤資訊，則您可以考慮關閉全域追蹤。 請參閱[關閉全域追蹤](../core/how-to-turn-off-global-tracking.md)。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [檢查清單：封存和清除 BizTalk 追蹤資料庫](../core/checklist-archiving-and-purging-the-biztalk-tracking-database.md)  
  
-   [設定 BTS_BACKUP_USERS 角色以封存和清除 BizTalk 追蹤資料庫中的資料](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)  
  
-   [設定 DTA 清除和封存作業](../core/how-to-configure-the-dta-purge-and-archive-job.md)  
  
-   [清除 BizTalk 追蹤資料庫中的資料](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [手動清除 BizTalk 追蹤資料庫中的資料](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [啟用自動封存驗證](../core/how-to-enable-automatic-archive-validation.md)  
  
-   [將追蹤的訊息複製到 BizTalk 追蹤資料庫](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)  
  
-   [改善封存和清除程序的效能](../core/improving-the-performance-of-the-archiving-and-purging-process.md)  
  
-   [關閉全域追蹤](../core/how-to-turn-off-global-tracking.md)