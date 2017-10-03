---
title: "解除安裝並取消設定 BizTalk Server 將它移除 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9ea8757-ca49-421b-bf7b-89344201398a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce643460d7c5256829624de5ba4c32d664c26ac3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="uninstall-and-unconfigure-biztalk-server-to-remove-it"></a><span data-ttu-id="3d9bf-102">將 BizTalk Server 解除安裝並取消設定以將其移除</span><span class="sxs-lookup"><span data-stu-id="3d9bf-102">Uninstall and unconfigure BizTalk Server to remove it</span></span>
<span data-ttu-id="3d9bf-103">將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解除安裝並取消設定。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-103">Uninstall and unconfigure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> 
  
##  <span data-ttu-id="3d9bf-104"><a name="BKMK_BeforeYouBegin"></a> 開始之前</span><span class="sxs-lookup"><span data-stu-id="3d9bf-104"><a name="BKMK_BeforeYouBegin"></a> Before You Begin</span></span>  
  
-   <span data-ttu-id="3d9bf-105">解除安裝之前，您必須將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 取消設定。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-105">Before you uninstall, you must un-configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="3d9bf-106">本主題列出要刪除的不同作業、套件和資料庫。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-106">This topic lists the different jobs, packages, and databases to be deleted.</span></span> <span data-ttu-id="3d9bf-107">列出的名稱是預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-107">The names listed are the default names.</span></span> <span data-ttu-id="3d9bf-108">您的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境可能使用非預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-108">Your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment may be using non-default names.</span></span>  
  
-   <span data-ttu-id="3d9bf-109">請依列出的順序完成步驟。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-109">Complete the steps in the order listed.</span></span> <span data-ttu-id="3d9bf-110">否則，不會完成解除安裝。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-110">Otherwise, the uninstall is not complete.</span></span>  
  
##  <span data-ttu-id="3d9bf-111"><a name="BKMK_Unconfigure"></a> 將 BizTalk Server 取消設定</span><span class="sxs-lookup"><span data-stu-id="3d9bf-111"><a name="BKMK_Unconfigure"></a> Un-configure BizTalk Server</span></span>  
  
1.  <span data-ttu-id="3d9bf-112">以滑鼠右鍵按一下 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態]，然後選取 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-112">Right-click **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration**, and select **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="3d9bf-113">在 [組態] 中，選取 [取消設定功能]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-113">In the Configuration, select **Unconfigure Features**.</span></span>  
  
3.  <span data-ttu-id="3d9bf-114">選取您要取消設定的功能，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-114">Select the features you want to unconfigure, and select **OK**.</span></span> <span data-ttu-id="3d9bf-115">如果系統提示您繼續，請選取 [是]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-115">If prompted to proceed, select **Yes**.</span></span> <span data-ttu-id="3d9bf-116">若要移除電腦中的所有項目，您可以選取所有功能。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-116">To  remove everything from the computer, you can select all the features.</span></span>  
  
4.  <span data-ttu-id="3d9bf-117">選取 [下一步]，然後繼續執行精靈。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-117">Select **Next**, and continue through the wizard.</span></span>  
  
 <span data-ttu-id="3d9bf-118">會在暫存資料夾中產生記錄檔，類似於︰C:\Users\username\AppData\Local\Temp\ConfigLog(8-29-2016 0h37m59s).log。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-118">A log file is generated in a temp folder, similar to: C:\Users\username\AppData\Local\Temp\ConfigLog(8-29-2016 0h37m59s).log.</span></span>  
  
##  <span data-ttu-id="3d9bf-119"><a name="BKMK_Uninstall"></a> 解除安裝 BizTalk Server 執行階段元件</span><span class="sxs-lookup"><span data-stu-id="3d9bf-119"><a name="BKMK_Uninstall"></a> Uninstall BizTalk Server Runtime Components</span></span>  
  
1.  <span data-ttu-id="3d9bf-120">開啟 [程式和功能]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-120">Open **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="3d9bf-121">從清單中選取 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 版本，然後選取 [解除安裝]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-121">Select  your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] version from the list, and  **Uninstall**.</span></span>  
  
3.  <span data-ttu-id="3d9bf-122">[移除] 它，然後繼續執行精靈。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-122">**Remove** it, and continue through the wizard.</span></span>  
  
 <span data-ttu-id="3d9bf-123">會在暫存資料夾中產生記錄檔，類似於︰C:\Users\\*username*\AppData\Local\Setup(083016 xxxxxx).htm</span><span class="sxs-lookup"><span data-stu-id="3d9bf-123">A log file is generated in a temp folder, similar to: C:\Users\\*username*\AppData\Local\Setup(083016 xxxxxx).htm</span></span>  
  
##  <span data-ttu-id="3d9bf-124"><a name="BKMK_UninstallSSO"></a> 解除安裝企業單一登入</span><span class="sxs-lookup"><span data-stu-id="3d9bf-124"><a name="BKMK_UninstallSSO"></a> Uninstall Enterprise Single Sign-On</span></span>  
  
1.  <span data-ttu-id="3d9bf-125">開啟 [程式和功能]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-125">Open **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="3d9bf-126">從清單中選取 [Microsoft 企業單一登入]，然後選取 [解除安裝]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-126">Select **Microsoft Enterprise Single Sign-On** from the list, and **Uninstall**.</span></span>  
  
3.  <span data-ttu-id="3d9bf-127">[移除] 它，然後繼續執行精靈。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-127">**Remove** it, and continue through the wizard.</span></span>  
  
 <span data-ttu-id="3d9bf-128">會在暫存資料夾中產生記錄檔，類似於︰C:\Users\\*username*\AppData\Local\Setup(083016 xxxxxx).htm</span><span class="sxs-lookup"><span data-stu-id="3d9bf-128">A log file is generated in a temp folder, similar to: C:\Users\\*username*\AppData\Local\Setup(083016 xxxxxx).htm</span></span>  
  
##  <span data-ttu-id="3d9bf-129"><a name="BKMK_RemoveRemaining"></a> 刪除 SQL 作業、資料庫和套件</span><span class="sxs-lookup"><span data-stu-id="3d9bf-129"><a name="BKMK_RemoveRemaining"></a> Delete SQL jobs, databases, and packages</span></span>  
  
#### <a name="delete-sql-server-agent-jobs"></a><span data-ttu-id="3d9bf-130">移除 SQL Server Agent 作業</span><span class="sxs-lookup"><span data-stu-id="3d9bf-130">Delete SQL Server agent jobs</span></span>  
  
1.  <span data-ttu-id="3d9bf-131">以系統管理員身分開啟 **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-131">Open **SQL Server Management Studio** as Administrator.</span></span>  
  
2.  <span data-ttu-id="3d9bf-132">在 [SQL Server Management Studio] 中，連接至 [Database Engine]，並依序展開 [SQL Server Agent] 和 [作業]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-132">In **SQL Server Management Studio**, connect to **Database Engine**, expand **SQL Server Agent**, and expand  **Jobs**.</span></span>  
  
3.  <span data-ttu-id="3d9bf-133">刪除下列作業 (以滑鼠右鍵按一下作業，然後選取 [刪除])：</span><span class="sxs-lookup"><span data-stu-id="3d9bf-133">Delete the following jobs (right-click the job, and select **Delete**):</span></span>  
  
    -   <span data-ttu-id="3d9bf-134">備份 BizTalk Server (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="3d9bf-134">Backup BizTalk Server (BizTalkMgmtDb)</span></span>  
  
    -   <span data-ttu-id="3d9bf-135">CleanupBTFExpiredEntriesJob_BizTalkMgmtDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-135">CleanupBTFExpiredEntriesJob_BizTalkMgmtDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-136">DTA 清除與封存 (BizTalkDTADb)</span><span class="sxs-lookup"><span data-stu-id="3d9bf-136">DTA Purge and Archive (BizTalkDTADb)</span></span>  
  
    -   <span data-ttu-id="3d9bf-137">MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-137">MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-138">MessageBox_Message_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-138">MessageBox_Message_Cleanup_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-139">MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-139">MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-140">MessageBox_Parts_Cleanup_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-140">MessageBox_Parts_Cleanup_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-141">MessageBox_UpdateStats_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-141">MessageBox_UpdateStats_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-142">監控 BizTalk Server (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="3d9bf-142">Monitor BizTalk Server (BizTalkMgmtDb)</span></span>  
  
    -   <span data-ttu-id="3d9bf-143">Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-143">Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-144">PurgeSubscriptionsJob_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-144">PurgeSubscriptionsJob_BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-145">Rules_Database_Cleanup_BizTalkRuleEngineDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-145">Rules_Database_Cleanup_BizTalkRuleEngineDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-146">TrackedMessages_Copy_BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-146">TrackedMessages_Copy_BizTalkMsgBoxDb</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3d9bf-147">如果您部署 BAM 時，您可能也需要移除 bam_\<*Cube 名稱*> _\<*檢視名稱*> 作業。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-147">If you deployed BAM, you may also need to remove the bam_\<*Cube Name*>_\<*View Name*> job.</span></span>  
  
#### <a name="delete-biztalk-server-databases"></a><span data-ttu-id="3d9bf-148">刪除 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="3d9bf-148">Delete BizTalk Server databases</span></span>  
  
1.  <span data-ttu-id="3d9bf-149">在 [物件總管] 中，展開 [資料庫]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-149">In **Object Explorer**, expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="3d9bf-150">刪除下列資料庫 (以滑鼠右鍵按一下資料庫，然後選取 [刪除])：</span><span class="sxs-lookup"><span data-stu-id="3d9bf-150">Delete the following databases (right-click the database, and select **Delete**):</span></span>  
  
    -   <span data-ttu-id="3d9bf-151">BAMArchive</span><span class="sxs-lookup"><span data-stu-id="3d9bf-151">BAMArchive</span></span>  
  
    -   <span data-ttu-id="3d9bf-152">BAMPrimaryImport</span><span class="sxs-lookup"><span data-stu-id="3d9bf-152">BAMPrimaryImport</span></span>  
  
    -   <span data-ttu-id="3d9bf-153">BAMStarSchema</span><span class="sxs-lookup"><span data-stu-id="3d9bf-153">BAMStarSchema</span></span>  
  
    -   <span data-ttu-id="3d9bf-154">BizTalkDTADb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-154">BizTalkDTADb</span></span>  
  
    -   <span data-ttu-id="3d9bf-155">BizTalkMgmtDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-155">BizTalkMgmtDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-156">BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-156">BizTalkMsgBoxDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-157">BizTalkRuleEngineDb</span><span class="sxs-lookup"><span data-stu-id="3d9bf-157">BizTalkRuleEngineDb</span></span>  
  
    -   <span data-ttu-id="3d9bf-158">SSODB</span><span class="sxs-lookup"><span data-stu-id="3d9bf-158">SSODB</span></span>  
  
#### <a name="remove-sql-server-integration-services-packages"></a><span data-ttu-id="3d9bf-159">移除 SQL Server Integration Services 套件</span><span class="sxs-lookup"><span data-stu-id="3d9bf-159">Remove SQL Server Integration Services packages</span></span>  
  
1.  <span data-ttu-id="3d9bf-160">在 [物件總管] 中，[連接] 至 [Integration Services]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-160">In **Object Explorer**,  **Connect** to **Integration Services**.</span></span>  
  
2.  <span data-ttu-id="3d9bf-161">依序展開 [存放的套件] 和 [MSDB]。</span><span class="sxs-lookup"><span data-stu-id="3d9bf-161">Expand **Stored Packages**, and expand **MSDB**.</span></span>  
  
3.  <span data-ttu-id="3d9bf-162">刪除具有下列前置詞的套件 (以滑鼠右鍵按一下套件，然後選取 [刪除])：</span><span class="sxs-lookup"><span data-stu-id="3d9bf-162">Delete the packages with the following prefixes (right-click the package, and select **Delete**):</span></span>  
  
    -   <span data-ttu-id="3d9bf-163">BAM_AN_\<*Cube 名稱*></span><span class="sxs-lookup"><span data-stu-id="3d9bf-163">BAM_AN_\<*Cube Name*></span></span>  
  
    -   <span data-ttu-id="3d9bf-164">BAM_DM_\<*檢視名稱*></span><span class="sxs-lookup"><span data-stu-id="3d9bf-164">BAM_DM_\<*View Name*></span></span>  
  
