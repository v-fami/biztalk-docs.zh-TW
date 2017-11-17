---
title: "如何備份和還原 SQL 代理程式作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82fc5a5-5ea5-476c-bed1-c5d41a50e673
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 253055f9a45dfdb9864d4d5202661e750d28b1b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-and-restore-sql-agent-jobs"></a><span data-ttu-id="41f24-102">如何備份和還原 SQL 代理程式作業</span><span class="sxs-lookup"><span data-stu-id="41f24-102">How to Back Up and Restore SQL Agent Jobs</span></span>
<span data-ttu-id="41f24-103">本主題描述如何備份和還原 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="41f24-103">This topic describes how to back up and restore SQL Server Agent Jobs.</span></span> <span data-ttu-id="41f24-104">您在設定之後，您應該先備份您的 SQL 作業。</span><span class="sxs-lookup"><span data-stu-id="41f24-104">You should back up your SQL jobs after you configure them.</span></span>  
  
## <a name="biztalk-server-jobs"></a><span data-ttu-id="41f24-105">BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="41f24-105">BizTalk Server Jobs</span></span>  
 <span data-ttu-id="41f24-106">下列的 SQL Server Agent 作業會與 BizTalk Server 關聯。</span><span class="sxs-lookup"><span data-stu-id="41f24-106">The following SQL Server Agent jobs are associated with BizTalk Server.</span></span> <span data-ttu-id="41f24-107">安裝在每一部伺服器上的作業會安裝及設定的功能而有所不同。</span><span class="sxs-lookup"><span data-stu-id="41f24-107">The jobs installed on each server are different depending on which features are installed and configured.</span></span> <span data-ttu-id="41f24-108">大部分的這些作業會在 BizTalk Server 安裝期間建立。</span><span class="sxs-lookup"><span data-stu-id="41f24-108">Most of these jobs are created during BizTalk Server setup.</span></span> <span data-ttu-id="41f24-109">設定記錄傳送時，會建立數個項目。</span><span class="sxs-lookup"><span data-stu-id="41f24-109">Several are created when configuring log shipping.</span></span>  
  
-   <span data-ttu-id="41f24-110">備份 BizTalk Server (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="41f24-110">Backup BizTalk Server (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="41f24-111">CleanupBTFExpiredEntriesJob_BizTalkMgmtDb</span><span class="sxs-lookup"><span data-stu-id="41f24-111">CleanupBTFExpiredEntriesJob_BizTalkMgmtDb</span></span>  
  
-   <span data-ttu-id="41f24-112">DTA 清除與封存 (BizTalkDTADb)</span><span class="sxs-lookup"><span data-stu-id="41f24-112">DTA Purge and Archive (BizTalkDTADb)</span></span>  
  
-   <span data-ttu-id="41f24-113">MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="41f24-113">MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="41f24-114">MessageBox_Message_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="41f24-114">MessageBox_Message_Cleanup_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="41f24-115">MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="41f24-115">MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="41f24-116">MessageBox_Parts_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="41f24-116">MessageBox_Parts_Cleanup_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="41f24-117">MessageBox_UpdateStats_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="41f24-117">MessageBox_UpdateStats_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="41f24-118">Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="41f24-118">Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="41f24-119">PurgeSubscriptionsJob_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="41f24-119">PurgeSubscriptionsJob_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="41f24-120">Rules_Database_Cleanup_BizTalkRuleEngineDb</span><span class="sxs-lookup"><span data-stu-id="41f24-120">Rules_Database_Cleanup_BizTalkRuleEngineDb</span></span>  
  
-   <span data-ttu-id="41f24-121">TrackedMessages_Copy_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="41f24-121">TrackedMessages_Copy_BizTalkMsgBoxDb</span></span>  
  
-   <span data-ttu-id="41f24-122">BTS 記錄傳送取得備份歷程記錄</span><span class="sxs-lookup"><span data-stu-id="41f24-122">BTS Log Shipping Get Backup History</span></span>  
  
-   <span data-ttu-id="41f24-123">BTS 記錄傳送還原資料庫</span><span class="sxs-lookup"><span data-stu-id="41f24-123">BTS Log Shipping Restore Database</span></span>  
  
-   <span data-ttu-id="41f24-124">BTS 記錄傳送還原為標示</span><span class="sxs-lookup"><span data-stu-id="41f24-124">BTS Log Shipping Restore To Mark</span></span>  
  
## <a name="back-up-a-job-using-a-script"></a><span data-ttu-id="41f24-125">備份作業，使用指令碼</span><span class="sxs-lookup"><span data-stu-id="41f24-125">Back up a job using a script</span></span>  
  
1.  <span data-ttu-id="41f24-126">開啟**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="41f24-126">Open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="41f24-127">展開 [SQL Server Agent] ，再展開 [作業] 。</span><span class="sxs-lookup"><span data-stu-id="41f24-127">Expand **SQL Server Agent**, and expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="41f24-128">以滑鼠右鍵按一下您想要建立的備份指令碼，然後再選取的作業**與指令碼工作**。</span><span class="sxs-lookup"><span data-stu-id="41f24-128">Right-click the job you want to create a backup script for, and then select **Script Job as**.</span></span>  
  
4.  <span data-ttu-id="41f24-129">選取**CREATE 至**或**DROP To**，然後選取**新增查詢編輯器視窗**，**檔案**，或**剪貼簿**若要選取指令碼的目的地。</span><span class="sxs-lookup"><span data-stu-id="41f24-129">Select **CREATE To** or **DROP To**, then select **New Query Editor Window**, **File**, or **Clipboard** to select a destination for the script.</span></span> <span data-ttu-id="41f24-130">通常，目的地是檔案之**.sql**延伸模組。</span><span class="sxs-lookup"><span data-stu-id="41f24-130">Typically, the destination is a file with a **.sql** extension.</span></span>  
  
5.  <span data-ttu-id="41f24-131">重複此程序，從步驟 3 的每個您要編寫指令碼的工作。</span><span class="sxs-lookup"><span data-stu-id="41f24-131">Repeat this procedure from Step 3 for each job you want to script.</span></span> <span data-ttu-id="41f24-132">清單，請參閱 BizTalk Server 的相關工作，以判斷其作業您需要指令碼。</span><span class="sxs-lookup"><span data-stu-id="41f24-132">Refer to the list of BizTalk Server related jobs to determine which jobs you need to script.</span></span>  
  
     <span data-ttu-id="41f24-133">最少，您應該先備份**備份 BizTalk Server (BizTalkMgmtDb)**作業之後設定。</span><span class="sxs-lookup"><span data-stu-id="41f24-133">At a minimum, you should back up the **Backup BizTalk Server (BizTalkMgmtDb)** job after it is configured.</span></span>  
  
## <a name="restore-a-job-from-a-script"></a><span data-ttu-id="41f24-134">還原作業，從指令碼</span><span class="sxs-lookup"><span data-stu-id="41f24-134">Restore a job from a script</span></span>  
  
1.  <span data-ttu-id="41f24-135">開啟**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="41f24-135">Open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="41f24-136">在**檔案**功能表上，**開啟**包含已編寫指令碼的工作的檔案。</span><span class="sxs-lookup"><span data-stu-id="41f24-136">On the **File** menu, **Open** the file containing the scripted job.</span></span>  
  
3.  <span data-ttu-id="41f24-137">執行指令碼來建立作業。</span><span class="sxs-lookup"><span data-stu-id="41f24-137">Execute the script to create the job.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="41f24-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="41f24-138">Next Steps</span></span>  
 [<span data-ttu-id="41f24-139">如何備份和還原 SQL Server 登入</span><span class="sxs-lookup"><span data-stu-id="41f24-139">How to Back Up and Restore SQL Server Logins</span></span>](../core/how-to-back-up-and-restore-sql-server-logins.md)