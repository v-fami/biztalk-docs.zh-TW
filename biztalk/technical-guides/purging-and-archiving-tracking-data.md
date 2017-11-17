---
title: "清除和封存追蹤資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14094fda-3fd9-4d45-9bbb-cd9377c2cbad
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94a2560bc8a57a8f60bf2d1ebcddf68b62fd178a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="purging-and-archiving-tracking-data"></a><span data-ttu-id="b3bbd-102">清除和封存追蹤資料</span><span class="sxs-lookup"><span data-stu-id="b3bbd-102">Purging and Archiving Tracking Data</span></span>
<span data-ttu-id="b3bbd-103">請務必設定並啟用 DTA 清除與封存 SQL 代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-103">It is important to configure and enable the DTA Purge and Archive SQL Agent job.</span></span> <span data-ttu-id="b3bbd-104">此作業會封存，並且從 BizTalk 追蹤 (DTA) 資料庫清除舊資料。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-104">This job archives and purges old data from the BizTalk Tracking (DTA) database.</span></span> <span data-ttu-id="b3bbd-105">這是不可或缺的狀況良好[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-105">This is essential for a healthy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.</span></span> <span data-ttu-id="b3bbd-106">大型的追蹤資料庫將會開始追蹤主控件以及任何其他處理序的效能影響該查詢追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-106">A large Tracking database will begin to affect the performance of the tracking host and any other processes that query the Tracking database.</span></span> <span data-ttu-id="b3bbd-107">如果追蹤資料不會清除從追蹤資料庫，資料庫會繼續成長。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-107">If the tracking data is not purged from the Tracking database, the database will continue to grow.</span></span>  
  
## <a name="guidelines-for-using-the-dta-purge-and-archive-job"></a><span data-ttu-id="b3bbd-108">指導方針使用 DTA 清除與封存工作</span><span class="sxs-lookup"><span data-stu-id="b3bbd-108">Guidelines for Using the DTA Purge and Archive Job</span></span>  
  
-   <span data-ttu-id="b3bbd-109">**請確認已正確設定、 啟用以及已成功完成 DTA 清除與封存 SQL 代理程式作業。**</span><span class="sxs-lookup"><span data-stu-id="b3bbd-109">**Ensure that the DTA Purge and Archive SQL Agent job is properly configured, enabled, and successfully completing.**</span></span>  
  
     <span data-ttu-id="b3bbd-110">因為您必須先將它設定為包含可以在其中寫入封存檔案的目錄，預設不會啟用這項作業。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-110">This job is not enabled by default because you must first configure it to include a directory where the archive files can be written.</span></span>  
  
-   <span data-ttu-id="b3bbd-111">**如果您只需要清除舊資料，而不需要將它封存在第一次，然後變更 SQL Agent 作業來呼叫預存程序 」 dtasp_PurgeTrackingDatabase"。**</span><span class="sxs-lookup"><span data-stu-id="b3bbd-111">**If you only need to purge the old data and do not need to archive it first, then change the SQL Agent job to call the stored procedure “dtasp_PurgeTrackingDatabase”.**</span></span>  
  
     <span data-ttu-id="b3bbd-112">這會略過 「 封存 」 步驟，並只清除。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-112">This skips the archive step, and just does the purge.</span></span> <span data-ttu-id="b3bbd-113">如需有關這個預存程序和變更的 SQL 代理程式作業來使用它時，請參閱[< 如何清除資料從 BizTalk 追蹤資料庫的 「](http://go.microsoft.com/fwlink/?LinkId=153817) (http://go.microsoft.com/fwlink/?LinkId=153817)。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-113">For more information about this stored procedure and changing the SQL Agent job to use it, see ["How to Purge Data from the BizTalk Tracking Database"](http://go.microsoft.com/fwlink/?LinkId=153817) (http://go.microsoft.com/fwlink/?LinkId=153817).</span></span>  
  
-   <span data-ttu-id="b3bbd-114">**請確保工作能夠以最快速度的內送的追蹤資料會產生清除追蹤資料。**</span><span class="sxs-lookup"><span data-stu-id="b3bbd-114">**Ensure that the job is able to purge the tracking data as fast as the incoming tracking data is generated.**</span></span>  
  
     <span data-ttu-id="b3bbd-115">它是可接受的工作負載在尖峰期間，取得，但永遠應該能夠跟上。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-115">It is acceptable for the job to get behind during peak load times, but it should always be able to catch up.</span></span> <span data-ttu-id="b3bbd-116">如果清除工作落後，而且絕不會是能夠趕上，追蹤資料庫將會繼續成長，而效能將最終會受到負面影響。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-116">If the purge job gets behind and is never able to catch up, the Tracking database will continue to grow, and performance will eventually be adversely affected.</span></span>  
  
-   <span data-ttu-id="b3bbd-117">**檢閱軟清除和硬清除參數，以確保保持最佳的時間長度的資料。**</span><span class="sxs-lookup"><span data-stu-id="b3bbd-117">**Review the soft purge and hard purge parameters to ensure that you are keeping data for the optimal length of time.**</span></span>  
  
     <span data-ttu-id="b3bbd-118">如需這些參數的詳細資訊，請參閱[「 封存和清除 BizTalk 追蹤資料庫 」](http://go.microsoft.com/fwlink/?LinkId=153816) (http://go.microsoft.com/fwlink/?LinkId=153816)。</span><span class="sxs-lookup"><span data-stu-id="b3bbd-118">For more information about these parameters see ["Archiving and Purging the BizTalk Tracking Database"](http://go.microsoft.com/fwlink/?LinkId=153816) (http://go.microsoft.com/fwlink/?LinkId=153816).</span></span>  
  
-   <span data-ttu-id="b3bbd-119">**如果您要保留追蹤封存檔案，請確定您已成功還原，並使用它們的位置中有程序。**</span><span class="sxs-lookup"><span data-stu-id="b3bbd-119">**If you need to keep the tracking archive files, ensure that you have a process in place to successfully restore and use them.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bbd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3bbd-120">See Also</span></span>  
 [<span data-ttu-id="b3bbd-121">檢查清單： 設定 SQL Server</span><span class="sxs-lookup"><span data-stu-id="b3bbd-121">Checklist: Configuring SQL Server</span></span>](~/technical-guides/checklist-configuring-sql-server.md)