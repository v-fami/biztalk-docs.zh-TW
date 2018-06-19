---
title: 封存和清除追蹤資料庫 |Microsoft 文件
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
ms.openlocfilehash: 52e1f7b75f677bfd4818ddedcb74927633031a14
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710841"
---
# <a name="archive-and-purge-the-biztalkdtadb-database"></a><span data-ttu-id="859bf-102">封存及清除 BizTalkDTADb 資料庫</span><span class="sxs-lookup"><span data-stu-id="859bf-102">Archive and Purge the BizTalkDTADb Database</span></span>

## <a name="overview"></a><span data-ttu-id="859bf-103">概觀</span><span class="sxs-lookup"><span data-stu-id="859bf-103">Overview</span></span>
<span data-ttu-id="859bf-104">BizTalk Server 所處理的資料會越來越多，「BizTalk 追蹤」(BizTalkDTADb) 資料庫的大小會持續擴大。</span><span class="sxs-lookup"><span data-stu-id="859bf-104">As BizTalk Server processes more and more data on your system, the BizTalk Tracking (BizTalkDTADb) database continues to grow in size.</span></span> <span data-ttu-id="859bf-105">若未發現此成長現象將會降低系統效能，並且可能會在 Tracking Data Decode Service (TDDS) 中產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="859bf-105">Unchecked growth decreases system performance and may generate errors in the Tracking Data Decode Service (TDDS).</span></span> <span data-ttu-id="859bf-106">除了一般追蹤資料以外，追蹤的訊息也會累積在 MessageBox 資料庫，導致磁碟效能變差。</span><span class="sxs-lookup"><span data-stu-id="859bf-106">In addition to general tracking data, tracked messages can also accumulate in the MessageBox database, causing poor disk performance.</span></span>  
  
<span data-ttu-id="859bf-107">BizTalk Server 會自動使用 DTA 清除與封存工作這兩個處理程序。</span><span class="sxs-lookup"><span data-stu-id="859bf-107">BizTalk Server automates both processes using the DTA Purge and Archive job.</span></span> <span data-ttu-id="859bf-108">從「BizTalk 追蹤」資料庫封存和清除資料庫，可保有狀況良好的系統並封存您的追蹤資料供以後使用。</span><span class="sxs-lookup"><span data-stu-id="859bf-108">By archiving and purging data from the BizTalk Tracking database, you can maintain a healthy system, as well as keep your tracking data archived for future use.</span></span> <span data-ttu-id="859bf-109">因為「BizTalk 追蹤」資料庫封存會隨時間累積並消耗磁碟空間，定期將「BizTalk 追蹤」資料庫封存移到次要的儲存媒體是很好的方法。</span><span class="sxs-lookup"><span data-stu-id="859bf-109">Because BizTalk Tracking database archives accumulate over time and consume disk space, it is a good idea to move the BizTalk Tracking database archives to secondary storage on a regular basis.</span></span>  
  
 <span data-ttu-id="859bf-110">當您從「BizTalk 追蹤」資料庫清除資料時，DTA 清除和封存工作會清除不同類型的追蹤資訊，例如訊息和服務執行個體資訊、協調流程事件資訊，和規則引擎追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="859bf-110">When you purge data from the BizTalk Tracking database, the DTA Purge and Archive job purges different types of tracking information such as message and service instance information, orchestration event information, and rules engine tracking data.</span></span>  
  
 <span data-ttu-id="859bf-111">追蹤資料記錄的期限，是以追蹤資料插入「BizTalk 追蹤」資料庫的時間為依據。</span><span class="sxs-lookup"><span data-stu-id="859bf-111">The age of a tracking data record is based on the time the tracking data was inserted into the BizTalk Tracking database.</span></span> <span data-ttu-id="859bf-112">DTA 清除與封存工作使用時間戳記，以持續驗證記錄是否比資料的存留窗期還舊。</span><span class="sxs-lookup"><span data-stu-id="859bf-112">The DTA Purge and Archive job uses the time stamp to continuously verify whether the record is older than the live window of data.</span></span> <span data-ttu-id="859bf-113">在每個存留窗期過後，「BizTalk 追蹤」資料庫會被封存，並且建立新的封存檔。</span><span class="sxs-lookup"><span data-stu-id="859bf-113">After every live window period, the BizTalk Tracking database is archived and a new archive file is created.</span></span> <span data-ttu-id="859bf-114">只要作業排程所指定的每個 SQL Server Agent 作業間隔時間一到，所有已完成而比存留窗期還舊的追蹤資料都會被清除。</span><span class="sxs-lookup"><span data-stu-id="859bf-114">At each SQL Server Agent job interval specified by the job schedule, all completed tracking data older than the live window period is purged.</span></span>  
  
 <span data-ttu-id="859bf-115">BizTalk Server 使用軟清除和硬清除的概念。</span><span class="sxs-lookup"><span data-stu-id="859bf-115">BizTalk Server uses the concept of a soft purge and a hard purge.</span></span> <span data-ttu-id="859bf-116">軟清除是用來清除已完成的執行個體，而硬清除只可用來清除未完成的執行個體。</span><span class="sxs-lookup"><span data-stu-id="859bf-116">The soft purge is used to purge completed instances, while the hard purge is only used to purge incomplete instances.</span></span>  
  
## <a name="soft-purge"></a><span data-ttu-id="859bf-117">軟清除</span><span class="sxs-lookup"><span data-stu-id="859bf-117">Soft purge</span></span>
  
 <span data-ttu-id="859bf-118">在 DTA 封存與清除工作中，LiveHours 和 LiveDays 參數的總和是您想在 BizTalk Server 環境中維護之資料的存留窗期。</span><span class="sxs-lookup"><span data-stu-id="859bf-118">In the DTA Archive and Purge job, the sum of the LiveHours and LiveDays parameters is the live window of data you want to maintain in your BizTalk Server environment.</span></span> <span data-ttu-id="859bf-119">早於此資料存留窗期之已完成執行個體的所有相關資料都會被清除。</span><span class="sxs-lookup"><span data-stu-id="859bf-119">All data associated with a completed instance older than this live window of data is purged.</span></span> <span data-ttu-id="859bf-120">DTA 封存與清除工作預設並未啟用。</span><span class="sxs-lookup"><span data-stu-id="859bf-120">By default, the DTA Archive and Purge job is not enabled.</span></span> <span data-ttu-id="859bf-121">您必須先設定妥然後再啟用這項工作。</span><span class="sxs-lookup"><span data-stu-id="859bf-121">You must first configure and then enable the job.</span></span>  
  
 <span data-ttu-id="859bf-122">例如，設定每隔 20 分鐘，執行 DTA 清除與封存工作，並將 LiveHours = 1 和 LiveDays = 0。</span><span class="sxs-lookup"><span data-stu-id="859bf-122">For example, you can configure the DTA Purge and Archive job to run every 20 minutes, and set LiveHours=1 and LiveDays=0.</span></span> <span data-ttu-id="859bf-123">第一次此 SQL Server Agent 作業執行 (T0) 時，它藉由建立封存檔會追蹤資料庫的備份和項目會儲存在資料庫中使用此時間戳記。</span><span class="sxs-lookup"><span data-stu-id="859bf-123">The first time this SQL Server Agent job runs (T0), it takes a backup of the tracking database by creating an archive and an entry is saved in the database with this timestamp.</span></span> <span data-ttu-id="859bf-124">必須要成功封存，才能清除追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="859bf-124">A successful archive is necessary in order to purge tracking data.</span></span> <span data-ttu-id="859bf-125">如果封存成功，所有與 1 個小時前完成的執行個體相關的資料都會被清除。</span><span class="sxs-lookup"><span data-stu-id="859bf-125">If the archive was successful, then all the data associated with the instances that completed over an hour ago is purged.</span></span> <span data-ttu-id="859bf-126">每次執行作業時，過去 1 小時前完成的資料會被清除。</span><span class="sxs-lookup"><span data-stu-id="859bf-126">Each time the job runs, completed data over one hour old is purged.</span></span> <span data-ttu-id="859bf-127">在第 3 次執行時 (一小時後)，會建立新的封存，其中包含所有在最近一個小時區段內被插入追蹤資料庫的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="859bf-127">On the 3rd run (after one hour), a new archive is created that contains the data for all instances that were inserted into the tracking database in the last one hour segment.</span></span>  
  
 <span data-ttu-id="859bf-128">以下是如何設定封存與清除步驟 DTA 清除與封存工作，以符合範例中：</span><span class="sxs-lookup"><span data-stu-id="859bf-128">Here is how you would configure the Archive and Purge step in the DTA Purge and Archive job to match the example:</span></span>  
  
```  
exec dtasp_BackupAndPurgeTrackingDatabase  
1, --@nLiveHours 1,   
0, --@nLiveDays   
1, --@nHardDeleteDays   
‘\\server\backup’, --@nvcFolder   
null, --@nvcValidatingServer   
0 --@fForceBackup Soft purge process  
```  
  
 <span data-ttu-id="859bf-129">最後一次備份的時間戳記會儲存在「BizTalk 追蹤」資料庫中，確保只有當資料在先前的封存中時，才可以清除資料。</span><span class="sxs-lookup"><span data-stu-id="859bf-129">The time stamp of the last backup is stored in the BizTalk Tracking database and ensures that data is only purged if it is in the previous archive.</span></span> <span data-ttu-id="859bf-130">為求達到更高的可靠性，封存大約會重疊 10 分鐘。</span><span class="sxs-lookup"><span data-stu-id="859bf-130">For additional reliability, archives are overlapped by approximately 10 minutes.</span></span> <span data-ttu-id="859bf-131">下圖是依照上述範例，顯示軟清除的流程。</span><span class="sxs-lookup"><span data-stu-id="859bf-131">The following figure, based on the example above, shows the soft purge process.</span></span> <span data-ttu-id="859bf-132">請注意，封存和清除作業未必在同一時間發生。</span><span class="sxs-lookup"><span data-stu-id="859bf-132">Note that the archiving and purging tasks do not necessarily happen at the same time.</span></span>  
  
 <span data-ttu-id="859bf-133">**軟清除程序**</span><span class="sxs-lookup"><span data-stu-id="859bf-133">**Soft purge process**</span></span>  
  
 <span data-ttu-id="859bf-134">![軟清除流程](../core/media/archivingandpurging.gif "archivingandpurging")</span><span class="sxs-lookup"><span data-stu-id="859bf-134">![Soft purge process](../core/media/archivingandpurging.gif "archivingandpurging")</span></span>  
  
## <a name="hard-purge"></a><span data-ttu-id="859bf-135">硬清除</span><span class="sxs-lookup"><span data-stu-id="859bf-135">Hard purge</span></span>
  
 <span data-ttu-id="859bf-136">由於軟清除只能清除與已完成執行個體相關的資料，如果您有許多無限期執行的迴圈執行個體，那麼您的追蹤資料庫會變大，且永遠無法清除這些執行個體。</span><span class="sxs-lookup"><span data-stu-id="859bf-136">Because the soft purge only purges data associated with completed instances, if you have many looping instances that run indefinitely, then your tracking database would grow and these instances would never be purged.</span></span> <span data-ttu-id="859bf-137">硬清除日期允許刪除比指定間隔舊的所有資訊，但不會刪除指出服務存在的資訊。</span><span class="sxs-lookup"><span data-stu-id="859bf-137">The hard purge date allows all information older than the specified interval to be purged except for information indicating a service's existence.</span></span> <span data-ttu-id="859bf-138">您可以設定硬清除使用 **@nHardDeleteDays** 參數中的封存與清除步驟在 DTA 封存與清除工作。</span><span class="sxs-lookup"><span data-stu-id="859bf-138">You set the hard purge using the **@nHardDeleteDays** parameter in the Archive and Purge step in the DTA Archive and Purge job.</span></span> <span data-ttu-id="859bf-139">硬清除設定值始終都應大於軟清除設定值。</span><span class="sxs-lookup"><span data-stu-id="859bf-139">The hard purge setting should always be greater than your soft purge setting.</span></span> <span data-ttu-id="859bf-140">換句話說， **@nHardDeleteDays** 應大於總 **@nLiveHours** 和 **@nLiveDays**。</span><span class="sxs-lookup"><span data-stu-id="859bf-140">In other words, **@nHardDeleteDays** should be greater than the sum of **@nLiveHours** and **@nLiveDays**.</span></span>  
  
 <span data-ttu-id="859bf-141">封存和清除包括下表中描述的功能：</span><span class="sxs-lookup"><span data-stu-id="859bf-141">Archiving and purging includes the features described in the following table:</span></span>  
  
|<span data-ttu-id="859bf-142">功能</span><span class="sxs-lookup"><span data-stu-id="859bf-142">Feature</span></span>|<span data-ttu-id="859bf-143">Description</span><span class="sxs-lookup"><span data-stu-id="859bf-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="859bf-144">硬清除</span><span class="sxs-lookup"><span data-stu-id="859bf-144">Hard purge</span></span>|<span data-ttu-id="859bf-145">可讓您設定時間間隔，清除比指定日期舊且不完整的執行個體資訊。</span><span class="sxs-lookup"><span data-stu-id="859bf-145">Enables you to configure a time interval to purge information for incomplete instances older than a specified date.</span></span>|  
|<span data-ttu-id="859bf-146">將追蹤的訊息複製到追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="859bf-146">Copying tracked messages to tracking database</span></span>|<span data-ttu-id="859bf-147">使用 [CopyTrackedMessageToDTA] 選項，您可以直接將追蹤的訊息從 MessageBox 伺服器複製到您的「BizTalk 追蹤」資料庫。</span><span class="sxs-lookup"><span data-stu-id="859bf-147">Using the CopyTrackedMessageToDTA option, you can directly copy tracked messages from the MessageBox servers to your BizTalk Tracking database.</span></span> <span data-ttu-id="859bf-148">若要使用「DTA 清除與封存」清除與封存工作來清除資料，則這是有必要的。</span><span class="sxs-lookup"><span data-stu-id="859bf-148">This is required in order to purge data using the DTA Purge and Archive job.</span></span>|  
|<span data-ttu-id="859bf-149">封存驗證</span><span class="sxs-lookup"><span data-stu-id="859bf-149">Archive validation</span></span>|<span data-ttu-id="859bf-150">可讓您選擇設定次要資料庫伺服器，以驗證它們建立時的封存。</span><span class="sxs-lookup"><span data-stu-id="859bf-150">Enables you to optionally set up a secondary database server to validate the archives as they are created.</span></span>|  
|<span data-ttu-id="859bf-151">追蹤多個 BizTalk 追蹤資料庫版本支援</span><span class="sxs-lookup"><span data-stu-id="859bf-151">Tracking support for multiple BizTalk Tracking database versions</span></span>|<span data-ttu-id="859bf-152">可讓您使用追蹤支援與 BizTalk Server 資料庫的封存。</span><span class="sxs-lookup"><span data-stu-id="859bf-152">Enables you to use tracking support with BizTalk Server database archives.</span></span>|  
|<span data-ttu-id="859bf-153">減少追蹤資料</span><span class="sxs-lookup"><span data-stu-id="859bf-153">Reduction of tracking data</span></span>|<span data-ttu-id="859bf-154">連續減少儲存的追蹤資料數目，而不減少任何已產生的追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="859bf-154">Substantially reduces the amount of tracking data stored without reducing any tracking information generated.</span></span> <span data-ttu-id="859bf-155">這樣會造成追蹤資料庫的成長變慢。</span><span class="sxs-lookup"><span data-stu-id="859bf-155">This results in slower growth of the tracking database.</span></span>|  
|<span data-ttu-id="859bf-156">更快速追蹤作業，大幅最佳化資料庫結構描述</span><span class="sxs-lookup"><span data-stu-id="859bf-156">Faster tracking operations, significant optimization in database schemas</span></span>|<span data-ttu-id="859bf-157">可讓您用於追蹤工作的工作尋找訊息和服務執行個體，對大型資料庫。這項功能已大幅最佳化。</span><span class="sxs-lookup"><span data-stu-id="859bf-157">Enables you to use tracking tasks for finding messages and service instances on large databases; this feature has been significantly optimized.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="859bf-158">如果效能問題是藉由清除 BizTalk 追蹤資料庫而暫時解決，而您想要將 BizTalk 設定為不再收集追蹤資訊，則您可以考慮關閉全域追蹤。</span><span class="sxs-lookup"><span data-stu-id="859bf-158">If you are having performance issues that are momentarily addressed by purging the BizTalk tracking database, and you want to configure BizTalk to no longer collect tracking information, you may want to consider turning off global tracking.</span></span> <span data-ttu-id="859bf-159">請參閱[關閉全域追蹤](../core/how-to-turn-off-global-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="859bf-159">See [Turn Off Global Tracking](../core/how-to-turn-off-global-tracking.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="859bf-160">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="859bf-160">Next steps</span></span>
  
-   [<span data-ttu-id="859bf-161">檢查清單：封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="859bf-161">Checklist: Archiving and Purging the BizTalk Tracking Database</span></span>](../core/checklist-archiving-and-purging-the-biztalk-tracking-database.md)  
  
-   [<span data-ttu-id="859bf-162">設定 BTS_BACKUP_USERS 角色以封存和清除 BizTalk 追蹤資料庫中的資料</span><span class="sxs-lookup"><span data-stu-id="859bf-162">Configure the BTS_BACKUP_USERS Role for Archiving and Purging Data from the BizTalk Tracking Database</span></span>](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)  
  
-   [<span data-ttu-id="859bf-163">設定 DTA 清除和封存作業</span><span class="sxs-lookup"><span data-stu-id="859bf-163">Configure the DTA Purge and Archive Job</span></span>](../core/how-to-configure-the-dta-purge-and-archive-job.md)  
  
-   [<span data-ttu-id="859bf-164">清除 BizTalk 追蹤資料庫中的資料</span><span class="sxs-lookup"><span data-stu-id="859bf-164">Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [<span data-ttu-id="859bf-165">手動清除 BizTalk 追蹤資料庫中的資料</span><span class="sxs-lookup"><span data-stu-id="859bf-165">Manually Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [<span data-ttu-id="859bf-166">啟用自動封存驗證</span><span class="sxs-lookup"><span data-stu-id="859bf-166">Enable Automatic Archive Validation</span></span>](../core/how-to-enable-automatic-archive-validation.md)  
  
-   [<span data-ttu-id="859bf-167">將追蹤的訊息複製到 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="859bf-167">Copy Tracked Messages into the BizTalk Tracking Database</span></span>](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)  
  
-   [<span data-ttu-id="859bf-168">改善封存和清除程序的效能</span><span class="sxs-lookup"><span data-stu-id="859bf-168">Improving the Performance of the Archiving and Purging Process</span></span>](../core/improving-the-performance-of-the-archiving-and-purging-process.md)  
  
-   [<span data-ttu-id="859bf-169">關閉全域追蹤</span><span class="sxs-lookup"><span data-stu-id="859bf-169">Turn Off Global Tracking</span></span>](../core/how-to-turn-off-global-tracking.md)