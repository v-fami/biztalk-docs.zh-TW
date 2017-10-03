---
title: "如何刪除 MessageBox 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, MessageBox database
- managing [MessageBox database], deleting
- MessageBox database, deleting
ms.assetid: 51f91fcb-8b97-4b00-9056-6d216c8ccb58
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a12c74bfef8d6afec15b0c83f520eb4be43696c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-messagebox-database"></a><span data-ttu-id="e75ee-102">如何刪除 MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="e75ee-102">How to Delete a MessageBox Database</span></span>
<span data-ttu-id="e75ee-103">您可使用 BizTalk 管理主控台或 Windows Management Instrumentation (WMI) 從 BizTalk 群組移除 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e75ee-103">You use the BizTalk Administration Console or Windows Management Instrumentation (WMI) to remove a MessageBox database from a BizTalk group.</span></span> <span data-ttu-id="e75ee-104">您可從 BizTalk 群組移除 MessageBox 資料庫，也可從 BizTalk Server 部署中整個移除此資料庫。</span><span class="sxs-lookup"><span data-stu-id="e75ee-104">You can remove a MessageBox database from a BizTalk group, or you can delete it from your BizTalk Server deployment entirely.</span></span>  
  
 <span data-ttu-id="e75ee-105">例如，您可以刪除不再使用的 MessageBox 資料庫，像是測試用途的資料庫。</span><span class="sxs-lookup"><span data-stu-id="e75ee-105">For example, you can delete a MessageBox database you are no longer using, such as a database used for testing purposes.</span></span>  
  
 <span data-ttu-id="e75ee-106">有 8 個步驟可以從 BizTalk Server 部署永久且完全地移除 MessageBox 資料庫：</span><span class="sxs-lookup"><span data-stu-id="e75ee-106">There are eight steps to permanently and completely removing MessageBox databases from your BizTalk Server deployment:</span></span>  
  
1.  <span data-ttu-id="e75ee-107">停用新訊息發佈。</span><span class="sxs-lookup"><span data-stu-id="e75ee-107">Disable new message publication.</span></span>  
  
     <span data-ttu-id="e75ee-108">刪除 MessageBox 資料庫前，必須先停用新訊息發佈。</span><span class="sxs-lookup"><span data-stu-id="e75ee-108">You must disable the publication of new messages before you delete a MessageBox database.</span></span> <span data-ttu-id="e75ee-109">停用新訊息發佈的相關資訊，請參閱[如何停用新訊息發佈](../core/how-to-disable-new-message-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="e75ee-109">For information about disabling new message publication, see [How to Disable New Message Publication](../core/how-to-disable-new-message-publication.md).</span></span>  
  
2.  <span data-ttu-id="e75ee-110">等待快取重新整理間隔過期。</span><span class="sxs-lookup"><span data-stu-id="e75ee-110">Wait for the cache refresh interval to expire.</span></span>  
  
     <span data-ttu-id="e75ee-111">停用新訊息發佈後，必須先等待才能刪除資料庫。</span><span class="sxs-lookup"><span data-stu-id="e75ee-111">After you disable the publication of new messages, you must wait before you delete the database.</span></span> <span data-ttu-id="e75ee-112">定義的等待時間長度是 CacheRefreshInterval 的兩倍。</span><span class="sxs-lookup"><span data-stu-id="e75ee-112">The wait time is defined as twice the length of the CacheRefreshInterval.</span></span> <span data-ttu-id="e75ee-113">CacheRefreshInterval 的預設值為 60 秒。</span><span class="sxs-lookup"><span data-stu-id="e75ee-113">The default value of CacheRefreshInterval is 60 seconds.</span></span> <span data-ttu-id="e75ee-114">您使用**群組內容**對話方塊來變更快取重新整理。</span><span class="sxs-lookup"><span data-stu-id="e75ee-114">You use the **Group Properties** dialog box to change the Cache Refresh.</span></span>  
  
3.  <span data-ttu-id="e75ee-115">從 BizTalk 群組中移除 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e75ee-115">Remove the MessageBox database from the BizTalk Group.</span></span>  
  
     <span data-ttu-id="e75ee-116">若從 BizTalk 群組移除 MessageBox 資料庫，會從 BizTalk 管理資料庫中移除 MessageBox 參考。</span><span class="sxs-lookup"><span data-stu-id="e75ee-116">Removing the MessageBox database from the BizTalk Group removes the MessageBox reference from the BizTalk Management database.</span></span>  
  
4.  <span data-ttu-id="e75ee-117">重新啟動包含到 MessageBox 資料庫的快取連線的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e75ee-117">Restart host instances that contain cached connections to the MessageBox database.</span></span>  
  
     <span data-ttu-id="e75ee-118">若執行階段引擎的快取資料庫連線是現用的，則從 SQL Server 實際刪除資料庫之前，必須重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e75ee-118">You must restart the host instance before physically deleting the database from SQL Server if cached database connections from the run-time engine are present.</span></span> <span data-ttu-id="e75ee-119">如需啟動主控件執行個體的相關資訊，請參閱[如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="e75ee-119">For information about starting a host instance, see [How to Start a Host Instance](../core/how-to-start-a-host-instance.md).</span></span>  
  
5.  <span data-ttu-id="e75ee-120">停止正在存取資料庫的所有主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e75ee-120">Stop all in-progress host instances that access the database.</span></span> <span data-ttu-id="e75ee-121">如需停止進行中的主控件執行個體的詳細資訊，請參閱[如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="e75ee-121">For information about stopping an in-progress host instance, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).</span></span>  
  
     <span data-ttu-id="e75ee-122">若您要移除非主要 MessageBox 資料庫，那麼在停止進行中的主控件執行個體前，必須先停用該 MessageBox 的新訊息發佈，並確認：</span><span class="sxs-lookup"><span data-stu-id="e75ee-122">If you are removing a non-primary MessageBox database, before stopping an in-progress host instance, you should first disable publication of new messages to that message box and make sure that:</span></span>  
  
    -   <span data-ttu-id="e75ee-123">該 MessageBox 中沒有其他正在執行的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="e75ee-123">There are no running service instances remaining in the message box.</span></span>  
  
    -   <span data-ttu-id="e75ee-124">MessageBox 中沒有擱置的 (或任何其他剩餘的) 執行個體留下。</span><span class="sxs-lookup"><span data-stu-id="e75ee-124">There are no suspended (or any other remaining) instances left in the message box.</span></span>  
  
    -   <span data-ttu-id="e75ee-125">已將 BAM 追蹤的資料移動到 BizTalk 追蹤資料庫 (BizTalkDTADb) (TrackingData 資料表應該是空的)。</span><span class="sxs-lookup"><span data-stu-id="e75ee-125">BAM tracked data has been moved to the BizTalk Tracking (BizTalkDTADb) database (TrackingData table should be empty).</span></span>  
  
    -   <span data-ttu-id="e75ee-126">已將追蹤的訊息內文移動到 BizTalk 追蹤資料庫 (BizTalkDTADb)。</span><span class="sxs-lookup"><span data-stu-id="e75ee-126">Tracked message bodies have been moved to the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
6.  <span data-ttu-id="e75ee-127">確定背景 SQL Server Agent 作業已經完成。</span><span class="sxs-lookup"><span data-stu-id="e75ee-127">Ensure that the background SQL Server Agent job is finished.</span></span>  
  
     <span data-ttu-id="e75ee-128">從 BizTalk Server 部署永久刪除 MessageBox 資料庫前，必須先確定背景 SQL Server Agent 作業已將所有追蹤的訊息內文傳輸到 TrackingSpool 資料表，然後再備份該資料表。</span><span class="sxs-lookup"><span data-stu-id="e75ee-128">Before you permanently delete a MessageBox database from your BizTalk Server deployment, you should first ensure that the background SQL Server Agent job has finished transferring all tracked message bodies to the TrackingSpool table, and then back up the TrackingSpool tables.</span></span> <span data-ttu-id="e75ee-129">如需有關檢查背景 SQL Server Agent 作業狀態的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="e75ee-129">For information about checking the status of a background SQL Server Agent job, see SQL Server Books Online.</span></span>  
  
7.  <span data-ttu-id="e75ee-130">備份將 TrackingSpool 資料表。</span><span class="sxs-lookup"><span data-stu-id="e75ee-130">Back up the TrackingSpool tables.</span></span>  
  
     <span data-ttu-id="e75ee-131">追蹤的訊息內文會保留在 MessageBox 資料庫中，直到您將 TrackingSpool 資料表手動備份到外部儲存裝置為止。</span><span class="sxs-lookup"><span data-stu-id="e75ee-131">Tracked message bodies remain in the MessageBox database until you manually back up the TrackingSpool tables into external storage.</span></span> <span data-ttu-id="e75ee-132">備份開始前，背景 SQL Server Agent 作業會將訊息內文從 Spool 資料表傳輸到 TrackingSpool 資料表。</span><span class="sxs-lookup"><span data-stu-id="e75ee-132">Before the backup happens, a background SQL Server Agent job transfers the message bodies from the Spool table to the TrackingSpool table.</span></span> <span data-ttu-id="e75ee-133">如需有關手動備份 SQL Server 資料表的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="e75ee-133">For information about manually backing up SQL Server tables, see SQL Server Books Online.</span></span>  
  
8.  <span data-ttu-id="e75ee-134">從 SQL Server 移除資料庫。</span><span class="sxs-lookup"><span data-stu-id="e75ee-134">Remove the database from SQL Server.</span></span>  
  
     <span data-ttu-id="e75ee-135">從 BizTalk 群組移除 MessageBox 資料庫，並不會從 Microsoft SQL Server 實際移除資料庫。</span><span class="sxs-lookup"><span data-stu-id="e75ee-135">Deleting a MessageBox database from a BizTalk Group does not physically remove the database from Microsoft SQL Server.</span></span> <span data-ttu-id="e75ee-136">若要永久刪除 MessageBox 資料庫，必須在從 BizTalk 群組移除此資料庫後，再使用 SQL Server Enterprise Manager 或 SQL Server Management Studio 將它移除。</span><span class="sxs-lookup"><span data-stu-id="e75ee-136">To permanently delete the MessageBox database, you must remove it by using SQL Server Enterprise Manager or SQL Server Management Studio after it is removed from the BizTalk Group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e75ee-137">必要條件</span><span class="sxs-lookup"><span data-stu-id="e75ee-137">Prerequisites</span></span>  
 <span data-ttu-id="e75ee-138">管理 MessageBox 資料庫的系統管理員必須具備必要的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="e75ee-138">Administrators who manage MessageBox databases must have the required user rights.</span></span> <span data-ttu-id="e75ee-139">您必須具備下列使用者權限，才能管理 MessageBox 資料庫和停用新訊息發佈：</span><span class="sxs-lookup"><span data-stu-id="e75ee-139">You must have the following user rights to manage MessageBox databases and disable new message publication:</span></span>  
  
-   <span data-ttu-id="e75ee-140">您必須以「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="e75ee-140">You must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
-   <span data-ttu-id="e75ee-141">您必須是資料庫所在電腦的 SQL Server 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="e75ee-141">You must be a SQL Server Administrator on the computer where the database exists.</span></span>  
  
### <a name="to-delete-a-messagebox-database-from-a-biztalk-group"></a><span data-ttu-id="e75ee-142">從 BizTalk 群組刪除 MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="e75ee-142">To delete a MessageBox database from a BizTalk Group</span></span>  
  
1.  <span data-ttu-id="e75ee-143">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e75ee-143">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e75ee-144">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **訊息方塊**。</span><span class="sxs-lookup"><span data-stu-id="e75ee-144">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Message Boxes**.</span></span>  
  
3.  <span data-ttu-id="e75ee-145">在詳細資料窗格中，以滑鼠右鍵按一下您想要移除，然後按一下訊息方塊資料庫**屬性**。</span><span class="sxs-lookup"><span data-stu-id="e75ee-145">In the details pane, right-click the message box database you want to remove, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e75ee-146">在**Messagebox 屬性**對話方塊中，選取**停用新訊息發佈**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e75ee-146">In the **Message Box Properties** dialog box, select the **Disable new message publication** check box.</span></span>  
  
5.  <span data-ttu-id="e75ee-147">使用 BizTalk Server 管理主控台中的 [群組中樞] 頁面，確認您正要刪除的 MessageBox 資料庫上沒有凍結的或擱置的訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="e75ee-147">Use the Group Hub page in the BizTalk Server Administration Console to verify that no message instances are dehydrated or suspended on the MessageBox database you are deleting.</span></span>  
  
6.  <span data-ttu-id="e75ee-148">等待兩倍於 CacheRefreshInterval 的時間。</span><span class="sxs-lookup"><span data-stu-id="e75ee-148">Wait for a period of time twice the length of the CacheRefreshInterval.</span></span> <span data-ttu-id="e75ee-149">CacheRefreshInterval 的預設值為 60 秒。</span><span class="sxs-lookup"><span data-stu-id="e75ee-149">The default value of CacheRefreshInterval is 60 seconds.</span></span>  
  
7.  <span data-ttu-id="e75ee-150">在詳細資料窗格中，以滑鼠右鍵按一下您想要刪除，然後按一下的 MessageBox 資料庫**刪除**。</span><span class="sxs-lookup"><span data-stu-id="e75ee-150">In the details pane, right-click the MessageBox database that you want to delete, and click **Delete**.</span></span>  
  
8.  <span data-ttu-id="e75ee-151">閱讀警告訊息之後, 按**確定**。</span><span class="sxs-lookup"><span data-stu-id="e75ee-151">After reading the warning message, click **OK**.</span></span>  
  
9. <span data-ttu-id="e75ee-152">在主控台樹狀目錄中，展開 BizTalk 群組中，按一下**平台設定**，然後按一下 **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="e75ee-152">In the console tree, expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
10. <span data-ttu-id="e75ee-153">在詳細資料窗格中，使用滑鼠右鍵按一下所有執行中的主控件執行個體，然後停止並重新啟動每一個。</span><span class="sxs-lookup"><span data-stu-id="e75ee-153">In the details pane, right-click all running host instances, and stop and restart each one.</span></span>  
  
11. <span data-ttu-id="e75ee-154">在 MessageBox 資料庫所在的伺服器上，視您正在使用的 SQL Server 版本，開啟 SQL Server Enterprise Manager 或 SQL Server Management Studio，然後刪除資料庫。</span><span class="sxs-lookup"><span data-stu-id="e75ee-154">On the server where the MessageBox database resides, open SQL Server Enterprise Manager or SQL Server Management Studio, depending on which version of SQL Server you are using, and then delete the database.</span></span>  
  
     <span data-ttu-id="e75ee-155">如需有關如何刪除 SQL Server 中的資料庫的資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="e75ee-155">For information about how to delete a database in SQL Server, see SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e75ee-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e75ee-156">See Also</span></span>  
 <span data-ttu-id="e75ee-157">[管理 MessageBox 資料庫](../core/managing-messagebox-databases.md) </span><span class="sxs-lookup"><span data-stu-id="e75ee-157">[Managing MessageBox Databases](../core/managing-messagebox-databases.md) </span></span>  
 <span data-ttu-id="e75ee-158">[如何新增新的 MessageBox 資料庫](../core/how-to-add-a-new-messagebox-database.md) </span><span class="sxs-lookup"><span data-stu-id="e75ee-158">[How to Add a New MessageBox Database](../core/how-to-add-a-new-messagebox-database.md) </span></span>  
 <span data-ttu-id="e75ee-159">[如何停用新訊息發佈](../core/how-to-disable-new-message-publication.md) </span><span class="sxs-lookup"><span data-stu-id="e75ee-159">[How to Disable New Message Publication](../core/how-to-disable-new-message-publication.md) </span></span>  
 [<span data-ttu-id="e75ee-160">MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="e75ee-160">The MessageBox Database</span></span>](../core/the-messagebox-database.md)