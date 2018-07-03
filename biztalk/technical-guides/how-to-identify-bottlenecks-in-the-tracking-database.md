---
title: 如何識別追蹤資料庫中的瓶頸 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b72e726-6225-47a0-8e1d-0f5a9cf745d3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc63ae8f673b25c4acbd2f7c066c38f2cb58d914
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011015"
---
# <a name="how-to-identify-bottlenecks-in-the-tracking-database"></a><span data-ttu-id="fa4ae-102">如何識別追蹤資料庫中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="fa4ae-102">How to Identify Bottlenecks in the Tracking Database</span></span>
<span data-ttu-id="fa4ae-103">若要識別 BizTalk 追蹤 (BizTalkDTADb) 資料庫中的瓶頸，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="fa4ae-103">To identify bottlenecks in the BizTalk Tracking (BizTalkDTADb) database, perform the following steps:</span></span>  
  
1. <span data-ttu-id="fa4ae-104">確認 SQL-Agent 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-104">Ensure that the SQL-Agent Service is running.</span></span>  
  
2. <span data-ttu-id="fa4ae-105">確定「封存/清除作業」服務正在執行而且即將順利完成。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-105">Ensure that the Archive/Purge Job is running and completing successfully.</span></span>  
  
3. <span data-ttu-id="fa4ae-106">請確定 TrackedMessages_Copy_BizTalkMsgBoxDB 作業正在執行，而且無法順利完成。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-106">Ensure that the TrackedMessages_Copy_BizTalkMsgBoxDB Job is running and completing successfully.</span></span>  
  
4. <span data-ttu-id="fa4ae-107">確認是否有足夠的可用磁碟空間可以容納 DTADb 封存和資料庫成長。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-107">Verify that sufficient free disk space is available for the DTADb archives and database growth.</span></span>  
  
5. <span data-ttu-id="fa4ae-108">用於追蹤專用的主機，並測量在負載下的主控件佇列長度效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-108">Use a dedicated host for tracking and measure the Host Queue Length performance counter when under load.</span></span>  
  
6. <span data-ttu-id="fa4ae-109">經過一段時間檢查遞增趨勢的多工緩衝處理表格 size 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-109">Check the Spool Table size performance counter for an increasing trend over time.</span></span>  
  
7. <span data-ttu-id="fa4ae-110">檢查長時間執行的封存/清除作業執行持續時間。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-110">Check the Archive/Purge job execution duration for long execution times.</span></span>  
  
8. <span data-ttu-id="fa4ae-111">在裝載 「 BizTalk 追蹤資料庫的磁碟，請檢查磁碟回應性 （Read/Write 效能計數器每次磁碟秒）。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-111">Check disk responsiveness (Disk Seconds per Read/Write performance counter) on the disk hosting the BizTalk Tracking database.</span></span>  
  
   <span data-ttu-id="fa4ae-112">我們強烈建議微調 dtasp_BackupAndPurgeTrackingDatabase 或 dtasp_PurgeTrackingDatabase DTA 清除與封存工作所叫用的下列參數的值：</span><span class="sxs-lookup"><span data-stu-id="fa4ae-112">We strongly recommend tuning down the value of the following parameters of the dtasp_BackupAndPurgeTrackingDatabase or dtasp_PurgeTrackingDatabase invoked by the DTA Purge and Archive job:</span></span>  
  
- <span data-ttu-id="fa4ae-113">@nLiveHours tinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-113">@nLiveHours tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="fa4ae-114">預設值為 0 小時。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-114">Default is 0 hours.</span></span>  
  
- <span data-ttu-id="fa4ae-115">@nLiveDays tinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-115">@nLiveDays tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="fa4ae-116">預設間隔是 1 天。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-116">Default interval is 1 day.</span></span>  
  
- <span data-ttu-id="fa4ae-117">@nHardDeleteDays tinyint — （即使未完成） 所有的資料超過這將會被刪除。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-117">@nHardDeleteDays tinyint — All data (even if incomplete) older than this will be deleted.</span></span> <span data-ttu-id="fa4ae-118">為 HardDeleteDays 指定的時間間隔應該大於資料存留窗期。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-118">The time interval specified for HardDeleteDays should be greater than the live window of data.</span></span> <span data-ttu-id="fa4ae-119">資料存留窗期是您想要在 BizTalk 追蹤 (BizTalkDTADb) 資料庫中維護追蹤資料的時間。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-119">The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="fa4ae-120">早於此間隔的資料都將在下次封存時進行封存，然後再予以清除。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-120">Anything older than this interval is eligible to be archived at the next archive and then purged.</span></span> <span data-ttu-id="fa4ae-121">預設值為 30 天。</span><span class="sxs-lookup"><span data-stu-id="fa4ae-121">Default is 30 days.</span></span>  
  
  <span data-ttu-id="fa4ae-122">這些參數都應該根據資料保留原則，在生產環境中，設定，而在效能實驗室測試，我們建議您使用的值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="fa4ae-122">These parameters should be set in accordance with data retention policies in a production environment, whereas in a performance lab tests we recommend that you use values as follows:</span></span>  
  
  <span data-ttu-id="fa4ae-123">宣告@dtLastBackup日期時間組@dtLastBackup= getutcdate （）</span><span class="sxs-lookup"><span data-stu-id="fa4ae-123">declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate()</span></span>  
  <span data-ttu-id="fa4ae-124">exec dtasp_PurgeTrackingDatabase 1，0，1， @dtLastBackup</span><span class="sxs-lookup"><span data-stu-id="fa4ae-124">exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4ae-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa4ae-125">See Also</span></span>  
 [<span data-ttu-id="fa4ae-126">資料庫層中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="fa4ae-126">Bottlenecks in the Database Tier</span></span>](../technical-guides/bottlenecks-in-the-database-tier.md)