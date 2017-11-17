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
# <a name="archiving-and-purging-the-biztalk-tracking-database"></a><span data-ttu-id="72dbe-102">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="72dbe-102">Archiving and Purging the BizTalk Tracking Database</span></span>
<span data-ttu-id="72dbe-103">BizTalk Server 所處理的資料會越來越多，「BizTalk 追蹤」(BizTalkDTADb) 資料庫的大小會持續擴大。</span><span class="sxs-lookup"><span data-stu-id="72dbe-103">As BizTalk Server processes more and more data on your system, the BizTalk Tracking (BizTalkDTADb) database continues to grow in size.</span></span> <span data-ttu-id="72dbe-104">若未發現此成長現象將會降低系統效能，並且可能會在 Tracking Data Decode Service (TDDS) 中產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="72dbe-104">Unchecked growth decreases system performance and may generate errors in the Tracking Data Decode Service (TDDS).</span></span> <span data-ttu-id="72dbe-105">除了一般追蹤資料以外，追蹤的訊息也會累積在 MessageBox 資料庫，導致磁碟效能變差。</span><span class="sxs-lookup"><span data-stu-id="72dbe-105">In addition to general tracking data, tracked messages can also accumulate in the MessageBox database, causing poor disk performance.</span></span>  
  
 <span data-ttu-id="72dbe-106">雖然舊版[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含封存追蹤的訊息和清除 BizTalk 追蹤資料庫的範例指令碼[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]自動化這兩個程序使用 「 DTA 清除與封存 」 作業。</span><span class="sxs-lookup"><span data-stu-id="72dbe-106">While previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] included sample scripts for archiving tracked messages and purging the BizTalk Tracking database, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automates both processes using the DTA Purge and Archive job.</span></span> <span data-ttu-id="72dbe-107">從「BizTalk 追蹤」資料庫封存和清除資料庫，可保有狀況良好的系統並封存您的追蹤資料供以後使用。</span><span class="sxs-lookup"><span data-stu-id="72dbe-107">By archiving and purging data from the BizTalk Tracking database, you can maintain a healthy system, as well as keep your tracking data archived for future use.</span></span> <span data-ttu-id="72dbe-108">因為「BizTalk 追蹤」資料庫封存會隨時間累積並消耗磁碟空間，定期將「BizTalk 追蹤」資料庫封存移到次要的儲存媒體是很好的方法。</span><span class="sxs-lookup"><span data-stu-id="72dbe-108">Because BizTalk Tracking database archives accumulate over time and consume disk space, it is a good idea to move the BizTalk Tracking database archives to secondary storage on a regular basis.</span></span>  
  
 <span data-ttu-id="72dbe-109">當您從「BizTalk 追蹤」資料庫清除資料時，DTA 清除和封存工作會清除不同類型的追蹤資訊，例如訊息和服務執行個體資訊、協調流程事件資訊，和規則引擎追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="72dbe-109">When you purge data from the BizTalk Tracking database, the DTA Purge and Archive job purges different types of tracking information such as message and service instance information, orchestration event information, and rules engine tracking data.</span></span>  
  
 <span data-ttu-id="72dbe-110">追蹤資料記錄的期限，是以追蹤資料插入「BizTalk 追蹤」資料庫的時間為依據。</span><span class="sxs-lookup"><span data-stu-id="72dbe-110">The age of a tracking data record is based on the time the tracking data was inserted into the BizTalk Tracking database.</span></span> <span data-ttu-id="72dbe-111">DTA 清除與封存工作使用時間戳記，以持續驗證記錄是否比資料的存留窗期還舊。</span><span class="sxs-lookup"><span data-stu-id="72dbe-111">The DTA Purge and Archive job uses the time stamp to continuously verify whether the record is older than the live window of data.</span></span> <span data-ttu-id="72dbe-112">在每個存留窗期過後，「BizTalk 追蹤」資料庫會被封存，並且建立新的封存檔。</span><span class="sxs-lookup"><span data-stu-id="72dbe-112">After every live window period, the BizTalk Tracking database is archived and a new archive file is created.</span></span> <span data-ttu-id="72dbe-113">只要作業排程所指定的每個 SQL Server Agent 作業間隔時間一到，所有已完成而比存留窗期還舊的追蹤資料都會被清除。</span><span class="sxs-lookup"><span data-stu-id="72dbe-113">At each SQL Server Agent job interval specified by the job schedule, all completed tracking data older than the live window period is purged.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="72dbe-114">使用軟清除和硬清除的概念。</span><span class="sxs-lookup"><span data-stu-id="72dbe-114"> uses the concept of a soft purge and a hard purge.</span></span> <span data-ttu-id="72dbe-115">軟清除是用來清除已完成的執行個體，而硬清除只可用來清除未完成的執行個體。</span><span class="sxs-lookup"><span data-stu-id="72dbe-115">The soft purge is used to purge completed instances, while the hard purge is only used to purge incomplete instances.</span></span>  
  
 <span data-ttu-id="72dbe-116">**軟清除**</span><span class="sxs-lookup"><span data-stu-id="72dbe-116">**Soft purge**</span></span>  
  
 <span data-ttu-id="72dbe-117">在 DTA 封存與清除工作，LiveHours 和 LiveDays 參數的總和是您想要在維護的資料存留窗您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="72dbe-117">In the DTA Archive and Purge job, the sum of the LiveHours and LiveDays parameters is the live window of data you want to maintain in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="72dbe-118">早於此資料存留窗期之已完成執行個體的所有相關資料都會被清除。</span><span class="sxs-lookup"><span data-stu-id="72dbe-118">All data associated with a completed instance older than this live window of data is purged.</span></span> <span data-ttu-id="72dbe-119">DTA 封存與清除工作預設並未啟用。</span><span class="sxs-lookup"><span data-stu-id="72dbe-119">By default, the DTA Archive and Purge job is not enabled.</span></span> <span data-ttu-id="72dbe-120">您必須先設定妥然後再啟用這項工作。</span><span class="sxs-lookup"><span data-stu-id="72dbe-120">You must first configure and then enable the job.</span></span>  
  
 <span data-ttu-id="72dbe-121">例如，您可以設定 DTA 清除與封存工作執行每隔 20 分鐘，並設定 LiveHours = 1 且 LiveDays = 0。</span><span class="sxs-lookup"><span data-stu-id="72dbe-121">For example, you can configure the DTA Purge and Archive job to run every 20 minutes, and set LiveHours=1 and LiveDays=0.</span></span> <span data-ttu-id="72dbe-122">第一次這個 SQL Server Agent 作業執行時 (T0)，會擔任藉由建立封存的追蹤資料庫的備份，而且項目會儲存在此時間戳記的資料庫。</span><span class="sxs-lookup"><span data-stu-id="72dbe-122">The first time this SQL Server Agent job runs (T0), it takes a backup of the tracking database by creating an archive and an entry is saved in the database with this timestamp.</span></span> <span data-ttu-id="72dbe-123">必須要成功封存，才能清除追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="72dbe-123">A successful archive is necessary in order to purge tracking data.</span></span> <span data-ttu-id="72dbe-124">如果封存成功，所有與 1 個小時前完成的執行個體相關的資料都會被清除。</span><span class="sxs-lookup"><span data-stu-id="72dbe-124">If the archive was successful, then all the data associated with the instances that completed over an hour ago is purged.</span></span> <span data-ttu-id="72dbe-125">每次執行作業時，過去 1 小時前完成的資料會被清除。</span><span class="sxs-lookup"><span data-stu-id="72dbe-125">Each time the job runs, completed data over one hour old is purged.</span></span> <span data-ttu-id="72dbe-126">在第 3 次執行時 (一小時後)，會建立新的封存，其中包含所有在最近一個小時區段內被插入追蹤資料庫的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="72dbe-126">On the 3rd run (after one hour), a new archive is created that contains the data for all instances that were inserted into the tracking database in the last one hour segment.</span></span>  
  
 <span data-ttu-id="72dbe-127">此處說明您如何在 DTA 清除與封存工作中設定符合上述範例的封存與清除步驟：</span><span class="sxs-lookup"><span data-stu-id="72dbe-127">Here is how you would configure the Archive and Purge step in the DTA Purge and Archive job to match the example above:</span></span>  
  
```  
exec dtasp_BackupAndPurgeTrackingDatabase  
1, --@nLiveHours 1,   
0, --@nLiveDays   
1, --@nHardDeleteDays   
‘\\server\backup’, --@nvcFolder   
null, --@nvcValidatingServer   
0 --@fForceBackup Soft purge process  
```  
  
 <span data-ttu-id="72dbe-128">最後一次備份的時間戳記會儲存在「BizTalk 追蹤」資料庫中，確保只有當資料在先前的封存中時，才可以清除資料。</span><span class="sxs-lookup"><span data-stu-id="72dbe-128">The time stamp of the last backup is stored in the BizTalk Tracking database and ensures that data is only purged if it is in the previous archive.</span></span> <span data-ttu-id="72dbe-129">為求達到更高的可靠性，封存大約會重疊 10 分鐘。</span><span class="sxs-lookup"><span data-stu-id="72dbe-129">For additional reliability, archives are overlapped by approximately 10 minutes.</span></span> <span data-ttu-id="72dbe-130">下圖是依照上述範例，顯示軟清除的流程。</span><span class="sxs-lookup"><span data-stu-id="72dbe-130">The following figure, based on the example above, shows the soft purge process.</span></span> <span data-ttu-id="72dbe-131">請注意，封存和清除作業未必在同一時間發生。</span><span class="sxs-lookup"><span data-stu-id="72dbe-131">Note that the archiving and purging tasks do not necessarily happen at the same time.</span></span>  
  
 <span data-ttu-id="72dbe-132">**軟清除流程**</span><span class="sxs-lookup"><span data-stu-id="72dbe-132">**Soft purge process**</span></span>  
  
 <span data-ttu-id="72dbe-133">![軟清除流程](../core/media/archivingandpurging.gif "archivingandpurging")</span><span class="sxs-lookup"><span data-stu-id="72dbe-133">![Soft purge process](../core/media/archivingandpurging.gif "archivingandpurging")</span></span>  
  
 <span data-ttu-id="72dbe-134">**硬清除**</span><span class="sxs-lookup"><span data-stu-id="72dbe-134">**Hard purge**</span></span>  
  
 <span data-ttu-id="72dbe-135">由於軟清除只能清除與已完成執行個體相關的資料，如果您有許多無限期執行的迴圈執行個體，那麼您的追蹤資料庫會變大，且永遠無法清除這些執行個體。</span><span class="sxs-lookup"><span data-stu-id="72dbe-135">Because the soft purge only purges data associated with completed instances, if you have many looping instances that run indefinitely, then your tracking database would grow and these instances would never be purged.</span></span> <span data-ttu-id="72dbe-136">硬清除日期允許刪除比指定間隔舊的所有資訊，但不會刪除指出服務存在的資訊。</span><span class="sxs-lookup"><span data-stu-id="72dbe-136">The hard purge date allows all information older than the specified interval to be purged except for information indicating a service's existence.</span></span> <span data-ttu-id="72dbe-137">您可以設定硬清除使用 **@nHardDeleteDays**  DTA 封存與清除工作中的參數中的封存與清除步驟。</span><span class="sxs-lookup"><span data-stu-id="72dbe-137">You set the hard purge using the **@nHardDeleteDays** parameter in the Archive and Purge step in the DTA Archive and Purge job.</span></span> <span data-ttu-id="72dbe-138">硬清除設定值始終都應大於軟清除設定值。</span><span class="sxs-lookup"><span data-stu-id="72dbe-138">The hard purge setting should always be greater than your soft purge setting.</span></span> <span data-ttu-id="72dbe-139">換句話說，  **@nHardDeleteDays** 應大於總和 **@nLiveHours** 和 **@nLiveDays** 。</span><span class="sxs-lookup"><span data-stu-id="72dbe-139">In other words, **@nHardDeleteDays** should be greater than the sum of **@nLiveHours** and **@nLiveDays**.</span></span>  
  
 <span data-ttu-id="72dbe-140">封存和清除包括下表中描述的功能：</span><span class="sxs-lookup"><span data-stu-id="72dbe-140">Archiving and purging includes the features described in the following table:</span></span>  
  
|<span data-ttu-id="72dbe-141">功能</span><span class="sxs-lookup"><span data-stu-id="72dbe-141">Feature</span></span>|<span data-ttu-id="72dbe-142">Description</span><span class="sxs-lookup"><span data-stu-id="72dbe-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72dbe-143">硬清除</span><span class="sxs-lookup"><span data-stu-id="72dbe-143">Hard purge</span></span>|<span data-ttu-id="72dbe-144">可讓您設定時間間隔，清除比指定日期舊且不完整的執行個體資訊。</span><span class="sxs-lookup"><span data-stu-id="72dbe-144">Enables you to configure a time interval to purge information for incomplete instances older than a specified date.</span></span>|  
|<span data-ttu-id="72dbe-145">將追蹤的訊息複製到追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="72dbe-145">Copying tracked messages to tracking database</span></span>|<span data-ttu-id="72dbe-146">使用 [CopyTrackedMessageToDTA] 選項，您可以直接將追蹤的訊息從 MessageBox 伺服器複製到您的「BizTalk 追蹤」資料庫。</span><span class="sxs-lookup"><span data-stu-id="72dbe-146">Using the CopyTrackedMessageToDTA option, you can directly copy tracked messages from the MessageBox servers to your BizTalk Tracking database.</span></span> <span data-ttu-id="72dbe-147">若要使用「DTA 清除與封存」清除與封存工作來清除資料，則這是有必要的。</span><span class="sxs-lookup"><span data-stu-id="72dbe-147">This is required in order to purge data using the DTA Purge and Archive job.</span></span>|  
|<span data-ttu-id="72dbe-148">封存驗證</span><span class="sxs-lookup"><span data-stu-id="72dbe-148">Archive validation</span></span>|<span data-ttu-id="72dbe-149">可讓您選擇設定次要資料庫伺服器，以驗證它們建立時的封存。</span><span class="sxs-lookup"><span data-stu-id="72dbe-149">Enables you to optionally set up a secondary database server to validate the archives as they are created.</span></span>|  
|<span data-ttu-id="72dbe-150">追蹤多個 BizTalk 追蹤資料庫版本的支援</span><span class="sxs-lookup"><span data-stu-id="72dbe-150">Tracking support for multiple BizTalk Tracking database versions</span></span>|<span data-ttu-id="72dbe-151">可讓您使用與追蹤支援[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]和[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]資料庫封存。</span><span class="sxs-lookup"><span data-stu-id="72dbe-151">Enables you to use tracking support with [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] and [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] database archives.</span></span>|  
|<span data-ttu-id="72dbe-152">減少追蹤資料</span><span class="sxs-lookup"><span data-stu-id="72dbe-152">Reduction of tracking data</span></span>|<span data-ttu-id="72dbe-153">連續減少儲存的追蹤資料數目，而不減少任何已產生的追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="72dbe-153">Substantially reduces the amount of tracking data stored without reducing any tracking information generated.</span></span> <span data-ttu-id="72dbe-154">這樣會造成追蹤資料庫的成長變慢。</span><span class="sxs-lookup"><span data-stu-id="72dbe-154">This results in slower growth of the tracking database.</span></span>|  
|<span data-ttu-id="72dbe-155">更快速追蹤作業，資料庫結構描述大幅最佳化</span><span class="sxs-lookup"><span data-stu-id="72dbe-155">Faster tracking operations, significant optimization in database schemas</span></span>|<span data-ttu-id="72dbe-156">可讓您用於追蹤工作的工作尋找訊息和服務執行個體，對大型資料庫;這項功能已大幅最佳化。</span><span class="sxs-lookup"><span data-stu-id="72dbe-156">Enables you to use tracking tasks for finding messages and service instances on large databases; this feature has been significantly optimized.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="72dbe-157">如果效能問題是藉由清除 BizTalk 追蹤資料庫而暫時解決，而您想要將 BizTalk 設定為不再收集追蹤資訊，則您可以考慮關閉全域追蹤。</span><span class="sxs-lookup"><span data-stu-id="72dbe-157">If you are having performance issues that are momentarily addressed by purging the BizTalk tracking database, and you want to configure BizTalk to no longer collect tracking information, you may want to consider turning off global tracking.</span></span> <span data-ttu-id="72dbe-158">如需如何關閉全域追蹤的詳細資訊，請參閱「如何關閉全域追蹤」。</span><span class="sxs-lookup"><span data-stu-id="72dbe-158">For information about turning off global tracking, see How to Turn Off Global Tracking.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72dbe-159">本節內容</span><span class="sxs-lookup"><span data-stu-id="72dbe-159">In This Section</span></span>  
  
-   [<span data-ttu-id="72dbe-160">檢查清單： 封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="72dbe-160">Checklist: Archiving and Purging the BizTalk Tracking Database</span></span>](../core/checklist-archiving-and-purging-the-biztalk-tracking-database.md)  
  
-   [<span data-ttu-id="72dbe-161">如何設定 BTS_BACKUP_USERS 角色以封存和清除來自 BizTalk 追蹤資料庫的資料</span><span class="sxs-lookup"><span data-stu-id="72dbe-161">How to Configure the BTS_BACKUP_USERS Role for Archiving and Purging Data from the BizTalk Tracking Database</span></span>](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)  
  
-   [<span data-ttu-id="72dbe-162">如何設定 DTA 清除與封存作業</span><span class="sxs-lookup"><span data-stu-id="72dbe-162">How to Configure the DTA Purge and Archive Job</span></span>](../core/how-to-configure-the-dta-purge-and-archive-job.md)  
  
-   [<span data-ttu-id="72dbe-163">如何從 BizTalk 追蹤資料庫清除資料</span><span class="sxs-lookup"><span data-stu-id="72dbe-163">How to Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [<span data-ttu-id="72dbe-164">如何從 BizTalk 追蹤資料庫手動清除資料</span><span class="sxs-lookup"><span data-stu-id="72dbe-164">How to Manually Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [<span data-ttu-id="72dbe-165">如何啟用自動封存驗證</span><span class="sxs-lookup"><span data-stu-id="72dbe-165">How to Enable Automatic Archive Validation</span></span>](../core/how-to-enable-automatic-archive-validation.md)  
  
-   [<span data-ttu-id="72dbe-166">如何將追蹤的訊息複製到 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="72dbe-166">How to Copy Tracked Messages into the BizTalk Tracking Database</span></span>](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)  
  
-   [<span data-ttu-id="72dbe-167">改善封存與清除程序的效能</span><span class="sxs-lookup"><span data-stu-id="72dbe-167">Improving the Performance of the Archiving and Purging Process</span></span>](../core/improving-the-performance-of-the-archiving-and-purging-process.md)  
  
-   [<span data-ttu-id="72dbe-168">如何關閉全域追蹤</span><span class="sxs-lookup"><span data-stu-id="72dbe-168">How to Turn Off Global Tracking</span></span>](../core/how-to-turn-off-global-tracking.md)