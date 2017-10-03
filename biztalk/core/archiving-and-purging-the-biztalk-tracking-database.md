---
title: "封存和清除 BizTalk 追蹤資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, purging
- BizTalk Server, maintaining
- archiving [Tracking database]
- purging
- Tracking database, maintaining
- Tracking database, archiving
- maintaining, Tracking database
- maintaining, BizTalk Server
ms.assetid: 7014cf31-86e8-4829-8055-056442329009
caps.latest.revision: "37"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8fc75f5218ec7a189d28c7120cf23a3047c1752
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="archiving-and-purging-the-biztalk-tracking-database"></a>封存和清除 BizTalk 追蹤資料庫
BizTalk Server 所處理的資料會越來越多，「BizTalk 追蹤」(BizTalkDTADb) 資料庫的大小會持續擴大。 若未發現此成長現象將會降低系統效能，並且可能會在 Tracking Data Decode Service (TDDS) 中產生錯誤。 除了一般追蹤資料以外，追蹤的訊息也會累積在 MessageBox 資料庫，導致磁碟效能變差。  
  
 雖然舊版[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含封存追蹤的訊息和清除 BizTalk 追蹤資料庫的範例指令碼[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]自動化這兩個程序使用 「 DTA 清除與封存 」 作業。 從「BizTalk 追蹤」資料庫封存和清除資料庫，可保有狀況良好的系統並封存您的追蹤資料供以後使用。 因為「BizTalk 追蹤」資料庫封存會隨時間累積並消耗磁碟空間，定期將「BizTalk 追蹤」資料庫封存移到次要的儲存媒體是很好的方法。  
  
 當您從「BizTalk 追蹤」資料庫清除資料時，DTA 清除和封存工作會清除不同類型的追蹤資訊，例如訊息和服務執行個體資訊、協調流程事件資訊，和規則引擎追蹤資料。  
  
 追蹤資料記錄的期限，是以追蹤資料插入「BizTalk 追蹤」資料庫的時間為依據。 DTA 清除與封存工作使用時間戳記，以持續驗證記錄是否比資料的存留窗期還舊。 在每個存留窗期過後，「BizTalk 追蹤」資料庫會被封存，並且建立新的封存檔。 只要作業排程所指定的每個 SQL Server Agent 作業間隔時間一到，所有已完成而比存留窗期還舊的追蹤資料都會被清除。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用軟清除和硬清除的概念。 軟清除是用來清除已完成的執行個體，而硬清除只可用來清除未完成的執行個體。  
  
 **軟清除**  
  
 在 DTA 封存與清除工作，LiveHours 和 LiveDays 參數的總和是您想要在維護的資料存留窗您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 早於此資料存留窗期之已完成執行個體的所有相關資料都會被清除。 DTA 封存與清除工作預設並未啟用。 您必須先設定妥然後再啟用這項工作。  
  
 例如，您可以設定 DTA 清除與封存工作執行每隔 20 分鐘，並設定 LiveHours = 1 且 LiveDays = 0。 第一次這個 SQL Server Agent 作業執行時 (T0)，會擔任藉由建立封存的追蹤資料庫的備份，而且項目會儲存在此時間戳記的資料庫。 必須要成功封存，才能清除追蹤資料。 如果封存成功，所有與 1 個小時前完成的執行個體相關的資料都會被清除。 每次執行作業時，過去 1 小時前完成的資料會被清除。 在第 3 次執行時 (一小時後)，會建立新的封存，其中包含所有在最近一個小時區段內被插入追蹤資料庫的所有執行個體。  
  
 此處說明您如何在 DTA 清除與封存工作中設定符合上述範例的封存與清除步驟：  
  
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
  
 **硬清除**  
  
 由於軟清除只能清除與已完成執行個體相關的資料，如果您有許多無限期執行的迴圈執行個體，那麼您的追蹤資料庫會變大，且永遠無法清除這些執行個體。 硬清除日期允許刪除比指定間隔舊的所有資訊，但不會刪除指出服務存在的資訊。 您可以設定硬清除使用 **@nHardDeleteDays**  DTA 封存與清除工作中的參數中的封存與清除步驟。 硬清除設定值始終都應大於軟清除設定值。 換句話說，  **@nHardDeleteDays** 應大於總和 **@nLiveHours** 和 **@nLiveDays** 。  
  
 封存和清除包括下表中描述的功能：  
  
|功能|Description|  
|-------------|-----------------|  
|硬清除|可讓您設定時間間隔，清除比指定日期舊且不完整的執行個體資訊。|  
|將追蹤的訊息複製到追蹤資料庫|使用 [CopyTrackedMessageToDTA] 選項，您可以直接將追蹤的訊息從 MessageBox 伺服器複製到您的「BizTalk 追蹤」資料庫。 若要使用「DTA 清除與封存」清除與封存工作來清除資料，則這是有必要的。|  
|封存驗證|可讓您選擇設定次要資料庫伺服器，以驗證它們建立時的封存。|  
|追蹤多個 BizTalk 追蹤資料庫版本的支援|可讓您使用與追蹤支援[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]和[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]資料庫封存。|  
|減少追蹤資料|連續減少儲存的追蹤資料數目，而不減少任何已產生的追蹤資訊。 這樣會造成追蹤資料庫的成長變慢。|  
|更快速追蹤作業，資料庫結構描述大幅最佳化|可讓您用於追蹤工作的工作尋找訊息和服務執行個體，對大型資料庫;這項功能已大幅最佳化。|  
  
> [!NOTE]
>  如果效能問題是藉由清除 BizTalk 追蹤資料庫而暫時解決，而您想要將 BizTalk 設定為不再收集追蹤資訊，則您可以考慮關閉全域追蹤。 如需如何關閉全域追蹤的詳細資訊，請參閱「如何關閉全域追蹤」。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [檢查清單： 封存和清除 BizTalk 追蹤資料庫](../core/checklist-archiving-and-purging-the-biztalk-tracking-database.md)  
  
-   [如何設定 BTS_BACKUP_USERS 角色以封存和清除來自 BizTalk 追蹤資料庫的資料](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)  
  
-   [如何設定 DTA 清除與封存作業](../core/how-to-configure-the-dta-purge-and-archive-job.md)  
  
-   [如何從 BizTalk 追蹤資料庫清除資料](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [如何從 BizTalk 追蹤資料庫手動清除資料](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [如何啟用自動封存驗證](../core/how-to-enable-automatic-archive-validation.md)  
  
-   [如何將追蹤的訊息複製到 BizTalk 追蹤資料庫](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)  
  
-   [改善封存與清除程序的效能](../core/improving-the-performance-of-the-archiving-and-purging-process.md)  
  
-   [如何關閉全域追蹤](../core/how-to-turn-off-global-tracking.md)