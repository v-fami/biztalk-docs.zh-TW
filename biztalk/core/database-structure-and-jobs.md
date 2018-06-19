---
title: 資料庫結構與工作 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PurgeSubscriptionsJob_BizTalkMsgBoxDb job
- MessageBox database, jobs [SQL Server Agent]
- DTA Purge and Archive (BizTalkDTADb) job
- TrackedMessages_Copy_BizTalkMsgBoxDb job
- MessageBox_Message_Cleanup_BizTalkMsgBoxDb job
- MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job
- Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb job
- jobs [SQL Server Agent], MessageBox database
- CleanupBTFExpiredEntriesJob_BizTalkMgmtDb job
- databases, structure
- Tracking database, jobs [SQL Server Agent]
- jobs [SQL Server Agent], Management database
- Backup BizTalk Server (BizTalkMgmtDb) job
- databases, SQL Server Agent jobs
- Business Rules Engine, jobs [SQL Server Agent]
- jobs, databases
- Management database, jobs [SQL Server Agent]
- MessageBox_UpdateStats_BizTalkMsgBoxDb job
- jobs [SQL Server Agent], Business Rules Engine
- Rules_Database_Cleanup_BizTalkRuleEngineDb job
- MessageBox_Parts_Cleanup_BizTalkMsgBoxDb job
- jobs [SQL Server Agent], Tracking database
- MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb job
ms.assetid: f5f6b17d-0f5e-4821-a7eb-c345234ffc65
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf98ef7fe236261fd3ee65ac6f4695455ba8c704
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240558"
---
# <a name="database-structure-and-jobs"></a><span data-ttu-id="345a6-102">資料庫結構與工作</span><span class="sxs-lookup"><span data-stu-id="345a6-102">Database Structure and Jobs</span></span>
<span data-ttu-id="345a6-103">本主題討論 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的資料庫結構與資料庫工作。</span><span class="sxs-lookup"><span data-stu-id="345a6-103">This topic discusses the database structure and database jobs for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="database-write-diagram"></a><span data-ttu-id="345a6-104">資料庫寫入圖</span><span class="sxs-lookup"><span data-stu-id="345a6-104">Database Write Diagram</span></span>  
 <span data-ttu-id="345a6-105">下圖顯示寫入 BizTalk Server 資料庫的程序和實體。</span><span class="sxs-lookup"><span data-stu-id="345a6-105">The following figure shows the processes and entities that write to the BizTalk Server databases.</span></span>  
  
 <span data-ttu-id="345a6-106">![寫入 BizTalk Server 資料庫的處理序](../core/media/ebiz-ops-backup.gif "ebiz_ops_backup")</span><span class="sxs-lookup"><span data-stu-id="345a6-106">![Processes that write to BizTalk Server databases](../core/media/ebiz-ops-backup.gif "ebiz_ops_backup")</span></span>  
  
        Database write diagram showing the processes and entities that write to the BizTalk Server databases  
  
## <a name="biztalk-server-database-jobs"></a><span data-ttu-id="345a6-107">BizTalk Server 資料庫工作</span><span class="sxs-lookup"><span data-stu-id="345a6-107">BizTalk Server Database Jobs</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="345a6-108"> 內附下列 SQL Server Agent 工作，以協助您管理 BizTalk Server 資料庫：</span><span class="sxs-lookup"><span data-stu-id="345a6-108"> includes the following SQL Server Agent jobs to assist you in managing the BizTalk Server databases:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="345a6-109">工作名稱可根據組態期間指定的資料庫名稱來變更。</span><span class="sxs-lookup"><span data-stu-id="345a6-109">The names of the jobs change depending on the database names given during configuration.</span></span> <span data-ttu-id="345a6-110">若您在環境中部署多個 MessageBox 資料庫，每個 MessageBox 將會有數個工作。</span><span class="sxs-lookup"><span data-stu-id="345a6-110">If you have deployed multiple MessageBox databases in your environment, there will be several jobs for each MessageBox.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="345a6-111">在 BizTalk 管理 (BizTalkMgmtDb) 資料庫中，沒有名為預存程序**adm_CleanupMgmtDB**。</span><span class="sxs-lookup"><span data-stu-id="345a6-111">In the BizTalk Management (BizTalkMgmtDb) database, there's a stored procedure named **adm_CleanupMgmtDB**.</span></span> <span data-ttu-id="345a6-112">**無法執行此預存程序 ！**</span><span class="sxs-lookup"><span data-stu-id="345a6-112">**DO NOT RUN THIS STORED PROCEDURE!**</span></span> <span data-ttu-id="345a6-113">如果您真的執行這個預存程序，資料庫中的所有項目都會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="345a6-113">If you do run this stored procedure, all the entries in the database will be deleted.</span></span>  
  
|<span data-ttu-id="345a6-114">作業</span><span class="sxs-lookup"><span data-stu-id="345a6-114">Job</span></span>|<span data-ttu-id="345a6-115">Description</span><span class="sxs-lookup"><span data-stu-id="345a6-115">Description</span></span>|  
|---------|-----------------|  
|<span data-ttu-id="345a6-116">備份 BizTalk Server (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="345a6-116">Backup BizTalk Server (BizTalkMgmtDb)</span></span>|<span data-ttu-id="345a6-117">這個工作會執行 BizTalk Server 資料庫的完整資料庫和記錄備份。</span><span class="sxs-lookup"><span data-stu-id="345a6-117">This job performs full database and log backups of the BizTalk Server databases.</span></span> <span data-ttu-id="345a6-118">如需有關設定和執行這項作業的詳細資訊，請參閱[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="345a6-118">For more information about configuring and running this job, see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md).</span></span>|  
|<span data-ttu-id="345a6-119">CleanupBTFExpiredEntriesJob_BizTalkMgmtDb</span><span class="sxs-lookup"><span data-stu-id="345a6-119">CleanupBTFExpiredEntriesJob_BizTalkMgmtDb</span></span>|<span data-ttu-id="345a6-120">這個工作會清除 BizTalk 管理 (BizTalkMgmtDb) 資料庫中過期的 BizTalk Framework (BTF) 項目。</span><span class="sxs-lookup"><span data-stu-id="345a6-120">This job cleans up expired BizTalk Framework (BTF) entries in the BizTalk Management (BizTalkMgmtDb) database.</span></span>|  
|<span data-ttu-id="345a6-121">DTA 清除與封存 (BizTalkDTADb)</span><span class="sxs-lookup"><span data-stu-id="345a6-121">DTA Purge and Archive (BizTalkDTADb)</span></span>|<span data-ttu-id="345a6-122">這個工作會自動封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫中的資料，並清除過期資料。</span><span class="sxs-lookup"><span data-stu-id="345a6-122">This job automatically archives data in the BizTalk Tracking (BizTalkDTADb) database and purges obsolete data.</span></span> <span data-ttu-id="345a6-123">如需有關設定和執行這項作業的詳細資訊，請參閱[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)。</span><span class="sxs-lookup"><span data-stu-id="345a6-123">For more information about configuring and running this job, see [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md).</span></span>|  
|<span data-ttu-id="345a6-124">MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="345a6-124">MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb</span></span>|<span data-ttu-id="345a6-125">這個工作會偵測出 BizTalk Server 主控件執行個體 (NT 服務) 何時停止，並釋放出該主控件執行個體所即將完成的所有工作，如此即可由另一個主控件執行個體來作業。</span><span class="sxs-lookup"><span data-stu-id="345a6-125">This job detects when a BizTalk Server host instance (NT service) has stopped and releases all work that was being done by that host instance so that it can be worked on by another host instance.</span></span>|  
|<span data-ttu-id="345a6-126">MessageBox_Message_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="345a6-126">MessageBox_Message_Cleanup_BizTalkMsgBoxDb</span></span>|<span data-ttu-id="345a6-127">這個工作會移除在 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫資料表中任何訂閱者所不再參考的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="345a6-127">This job removes all messages that are no longer being referenced by any subscribers in the BizTalk MessageBox (BizTalkMsgBoxDb) database tables.</span></span> <span data-ttu-id="345a6-128">**注意：** 這是由 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作所啟動的未排程的作業。</span><span class="sxs-lookup"><span data-stu-id="345a6-128">**Caution:**  This is an unscheduled job which is started by the MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job.</span></span> <span data-ttu-id="345a6-129">請勿手動啟動這個工作。</span><span class="sxs-lookup"><span data-stu-id="345a6-129">Do not manually start this job.</span></span>|  
|<span data-ttu-id="345a6-130">MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="345a6-130">MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb</span></span>|<span data-ttu-id="345a6-131">這個工作會管理訊息的參考計數記錄，並決定訊息何時不再被任何訂閱者所參考。</span><span class="sxs-lookup"><span data-stu-id="345a6-131">This job manages the reference count logs for messages and determines when a message is no longer referenced by any subscriber.</span></span> <span data-ttu-id="345a6-132">**注意：** 即使這個 SQL Server Agent 作業已排程執行每分鐘，這項作業會呼叫預存程序包含邏輯，以確保持續執行的預存程序之後。</span><span class="sxs-lookup"><span data-stu-id="345a6-132">**Note:**  Even thought this SQL Server Agent job is scheduled to run once per minute, the stored procedure that is called by this job contains logic to ensure that the stored procedure runs continually.</span></span> <span data-ttu-id="345a6-133">此行為是經過設計的，不可修改。</span><span class="sxs-lookup"><span data-stu-id="345a6-133">This is by design behavior and should not be modified.</span></span>|  
|<span data-ttu-id="345a6-134">MessageBox_Parts_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="345a6-134">MessageBox_Parts_Cleanup_BizTalkMsgBoxDb</span></span>|<span data-ttu-id="345a6-135">這個工作會移除在 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫資料表中任何訊息所不再參考的所有訊息部分。</span><span class="sxs-lookup"><span data-stu-id="345a6-135">This job removes all message parts that are no longer being referenced by any messages in the BizTalk MessageBox (BizTalkMsgBoxDb) database tables.</span></span> <span data-ttu-id="345a6-136">所有訊息皆是由一或多個訊息部分所組成，這些訊息部分會包含實際訊息資料。</span><span class="sxs-lookup"><span data-stu-id="345a6-136">All messages are made up of one or more message parts, which contain the actual message data.</span></span>|  
|<span data-ttu-id="345a6-137">MessageBox_UpdateStats_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="345a6-137">MessageBox_UpdateStats_BizTalkMsgBoxDb</span></span>|<span data-ttu-id="345a6-138">這個工作會手動更新 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫的統計資料。</span><span class="sxs-lookup"><span data-stu-id="345a6-138">This job manually updates the statistics for the BizTalk MessageBox (BizTalkMsgBoxDb) database.</span></span>|  
|<span data-ttu-id="345a6-139">監控 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="345a6-139">Monitor BizTalk Server</span></span>|<span data-ttu-id="345a6-140">這項作業會掃描 BizTalkMgmtDb、 BizTalkMsgBoxDb 和 BizTalkDTADb 資料庫的任何已知的問題，包括被遺棄使用者執行個體。</span><span class="sxs-lookup"><span data-stu-id="345a6-140">This job scans the BizTalkMgmtDb, BizTalkMsgBoxDb and BizTalkDTADb database for any known issues, including orphaned instances.</span></span>|  
|<span data-ttu-id="345a6-141">Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="345a6-141">Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb</span></span>|<span data-ttu-id="345a6-142">此為多個 MessageBox 部署的必要工作。</span><span class="sxs-lookup"><span data-stu-id="345a6-142">This job is needed for multiple MessageBox deployments.</span></span> <span data-ttu-id="345a6-143">它會在變更已套用到附屬 MessageBox 之後，於主要 MessageBox 上非同步執行像是大量終止這類的作業動作。</span><span class="sxs-lookup"><span data-stu-id="345a6-143">It asynchronously performs operational actions such as bulk terminate on the master MessageBox after those changes have been applied to the subordinate MessageBox.</span></span>|  
|<span data-ttu-id="345a6-144">PurgeSubscriptionsJob_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="345a6-144">PurgeSubscriptionsJob_BizTalkMsgBoxDb</span></span>|<span data-ttu-id="345a6-145">這個工作會從 BizTalk Server MessageBox (BizTalkMsgBoxDb) 資料庫清除未使用的訂閱述詞。</span><span class="sxs-lookup"><span data-stu-id="345a6-145">This job purges unused subscription predicates from the BizTalk Server MessageBox (BizTalkMsgBoxDb) database.</span></span>|  
|<span data-ttu-id="345a6-146">Rules_Database_Cleanup_BizTalkRuleEngineDb</span><span class="sxs-lookup"><span data-stu-id="345a6-146">Rules_Database_Cleanup_BizTalkRuleEngineDb</span></span>|<span data-ttu-id="345a6-147">這個動作每 90 天就會自動從規則引擎 (BizTalkRuleEngineDb) 資料庫清除舊的稽核資料。</span><span class="sxs-lookup"><span data-stu-id="345a6-147">This job automatically purges old audit data from the Rule Engine (BizTalkRuleEngineDb) database every 90 days.</span></span> <span data-ttu-id="345a6-148">另外，這個動作每 3 天就會從規則引擎 (BizTalkRuleEngineDb) 資料庫清除舊的歷程記錄資料 (部署/解除部署通知)。</span><span class="sxs-lookup"><span data-stu-id="345a6-148">This job also purges old history data (deploy/undeploy notifications) from the Rule Engine (BizTalkRuleEngineDb) database every 3 days.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="345a6-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="345a6-149">See Also</span></span>  
 [<span data-ttu-id="345a6-150">傳訊引擎</span><span class="sxs-lookup"><span data-stu-id="345a6-150">The Messaging Engine</span></span>](../core/the-messaging-engine.md)