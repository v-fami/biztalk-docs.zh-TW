---
title: "如何從 BizTalk 追蹤資料庫手動清除資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, purging
- purging, manually
- purging, warnings
ms.assetid: f350d850-5034-4166-940c-8d10b7b445fb
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb8bf8d87f7868367c252cdc75842b234cb06ff9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-manually-purge-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="8d501-102">如何手動清除 BizTalk 追蹤資料庫的資料</span><span class="sxs-lookup"><span data-stu-id="8d501-102">How to Manually Purge Data from the BizTalk Tracking Database</span></span>
<span data-ttu-id="8d501-103">「DTA 封存和清除 SQL Server Agent 作業」工作可減少由於持續清除資料庫和壓縮儲存的追蹤資料，而必須從 BizTalk 追蹤 (BizTalkDTADb) 資料庫手動清除資料的需要。</span><span class="sxs-lookup"><span data-stu-id="8d501-103">The DTA Archive and Purge SQL Server Agent job reduces the need to manually purge data from the BizTalk Tracking (BizTalkDTADb) database due to continuous purging of the database and compaction of stored tracking data.</span></span> <span data-ttu-id="8d501-104">若 BizTalk 追蹤 (BizTalkDTADb) 資料庫已大量成長，導致效能持續降低，且「DTA 封存和清除」工作無法跟上資料庫的成長時，就可能需要手動清除資料。</span><span class="sxs-lookup"><span data-stu-id="8d501-104">You might need to manually purge data if your BizTalk Tracking (BizTalkDTADb) database has grown so much that sustained performance degradation is occurring and the DTA Archive and Purge job is unable to keep up with the database growth.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8d501-105">不論其完成時間為何，執行此程序會從 BizTalk 追蹤 (BizTalkDTADb) 資料庫刪除已完成執行個體的所有追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="8d501-105">Performing this procedure deletes all tracking data for completed instances from the BizTalk Tracking (BizTalkDTADb) database regardless of completion time.</span></span> <span data-ttu-id="8d501-106">在執行此程序之前，您應該將 BizTalk 追蹤 (BizTalkDTADb) 資料庫與其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫分開封存。</span><span class="sxs-lookup"><span data-stu-id="8d501-106">Before performing this procedure, you should archive the BizTalk Tracking (BizTalkDTADb) database separately from the other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8d501-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="8d501-107">Prerequisites</span></span>  
 <span data-ttu-id="8d501-108">您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="8d501-108">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-manually-purge-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="8d501-109">若要從 BizTalk 追蹤資料庫手動清除資料</span><span class="sxs-lookup"><span data-stu-id="8d501-109">To manually purge data from the BizTalk Tracking database</span></span>  
  
1.  <span data-ttu-id="8d501-110">備份 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8d501-110">Backup your BizTalk Server databases.</span></span>  
  
2.  <span data-ttu-id="8d501-111">封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8d501-111">Archive the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
3.  <span data-ttu-id="8d501-112">開啟 [服務] 主控台。</span><span class="sxs-lookup"><span data-stu-id="8d501-112">Open the Services console.</span></span> <span data-ttu-id="8d501-113">按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。</span><span class="sxs-lookup"><span data-stu-id="8d501-113">Click **Start**, click **Run**, and then type **services.msc**.</span></span> <span data-ttu-id="8d501-114">如果**使用者帳戶控制** 對話方塊隨即出現，請按一下**繼續**。</span><span class="sxs-lookup"><span data-stu-id="8d501-114">If a **User Account Control** dialog is displayed, click **Continue**.</span></span>  
  
4.  <span data-ttu-id="8d501-115">當 [服務] 主控台出現時，請找出並停止下列每個服務。</span><span class="sxs-lookup"><span data-stu-id="8d501-115">When the Services console appears, locate and then stop each of the following services.</span></span> <span data-ttu-id="8d501-116">若要停止服務，以滑鼠右鍵按一下中的服務列**服務** 窗格中，然後再按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="8d501-116">To stop a service, right-click the service row in the **Services** pane, and then click **Stop**.</span></span>  
  
    -   <span data-ttu-id="8d501-117">BizTalkServiceBizTalkGroup: BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="8d501-117">BizTalkServiceBizTalkGroup : BizTalkServerApplication</span></span>  
  
    -   <span data-ttu-id="8d501-118">企業單一登入服務</span><span class="sxs-lookup"><span data-stu-id="8d501-118">Enterprise Single Sign-On Service</span></span>  
  
         <span data-ttu-id="8d501-119">如果 BizTalkServiceBizTalkGroup: BizTalkServerApplication 服務正在執行，當您嘗試關閉企業單一登入服務，**停止其他服務**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8d501-119">If the BizTalkServiceBizTalkGroup : BizTalkServerApplication service is running when you try to shut down the Enterprise Singe Sign-On Service, a **Stop Other Services** dialog will be displayed.</span></span> <span data-ttu-id="8d501-120">按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="8d501-120">Click **Yes**.</span></span>  
  
    -   <span data-ttu-id="8d501-121">規則引擎更新服務</span><span class="sxs-lookup"><span data-stu-id="8d501-121">Rule Engine Update Service</span></span>  
  
5.  <span data-ttu-id="8d501-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="8d501-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span> <span data-ttu-id="8d501-123">如果**使用者帳戶控制** 對話方塊隨即出現，請確認描述的動作是什麼，並再按**繼續**。</span><span class="sxs-lookup"><span data-stu-id="8d501-123">If a **User Account Control** dialog is displayed, verify that the action described is what you want, and then click **Continue**.</span></span>  
  
6.  <span data-ttu-id="8d501-124">在**BizTalk Server 管理主控台**在視窗的左邊 總管 窗格中，按兩下**BizTalk 群組**展開其下的清單，然後按兩下**平台設定**，然後按一下 **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="8d501-124">In the **BizTalk Server Administration Console** in the explorer pane on the left side of the window, double-click **BizTalk Group** to expand the list below it, then double-click **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="8d501-125">這會顯示主控件執行個體的清單 (**主控件執行個體**窗格) 和相關屬性，在螢幕的右邊。</span><span class="sxs-lookup"><span data-stu-id="8d501-125">This will display a list of host instances (the **Host Instances** pane) and related properties, on the right side of the screen.</span></span>  
  
7.  <span data-ttu-id="8d501-126">在**主控件執行個體**] 窗格中，每個執行的主控件執行個體，以滑鼠右鍵按一下，然後按一下 [**停止**。</span><span class="sxs-lookup"><span data-stu-id="8d501-126">In the **Host Instances** pane, right-click each running host instance, and then click **Stop**.</span></span>  
  
8.  <span data-ttu-id="8d501-127">按一下**啟動**，請移至**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="8d501-127">Click **Start**, go to **Run**, type **cmd**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="8d501-128">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="8d501-128">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="8d501-129">**net stop iisadmin /y**</span><span class="sxs-lookup"><span data-stu-id="8d501-129">**net stop iisadmin /y**</span></span>  
  
     <span data-ttu-id="8d501-130">這將會逐一停止「IIS 管理服務」以及所有相依的服務，並在清除資料時，避免新的資料寫入 BizTalkDTADb。</span><span class="sxs-lookup"><span data-stu-id="8d501-130">This stops the IIS Admin Service and all dependent services, one-by-one and prevents new data from being written to the BizTalkDTADb while data is being purged.</span></span> <span data-ttu-id="8d501-131">請在每個服務停止時記下服務清單。</span><span class="sxs-lookup"><span data-stu-id="8d501-131">Write down the list of services as each one is stopped.</span></span> <span data-ttu-id="8d501-132">在稍後重新啟動 IIS 時，您將需要使用此服務清單。</span><span class="sxs-lookup"><span data-stu-id="8d501-132">You will need to use this list of services later when you restart IIS.</span></span>  
  
     <span data-ttu-id="8d501-133">以下是在發出此命令之後您將看到的輸出範例 (列在電腦中的相依服務可能不同)：</span><span class="sxs-lookup"><span data-stu-id="8d501-133">Below is an example of the output you will see after issuing this command (the dependent services listed on your computer may vary):</span></span>  
  
    ```  
    The following services are dependent on the IIS Admin Service service. Stopping the IIS Admin Service service will also stop these services.  
    World Wide Web Publishing Service  
    HTTP SSL  
    ```  
  
10. <span data-ttu-id="8d501-134">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="8d501-134">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.</span></span>  
  
11. <span data-ttu-id="8d501-135">在**連接到伺服器**對話方塊中，指定 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL Server 和適當的驗證類型的名稱，然後按一下**連接**至連接到適當的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="8d501-135">In the **Connect to Server** dialog box, specify the name of the SQL Server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the appropriate SQL Server.</span></span>  
  
12. <span data-ttu-id="8d501-136">在**Microsoft SQL Server Management Studio**，連按兩下**資料庫**，連按兩下**BizTalkDTADb**資料庫中，按兩下**可程式性**，然後按一下 **預存程序**。</span><span class="sxs-lookup"><span data-stu-id="8d501-136">In **Microsoft SQL Server Management Studio**, double-click **Databases**, double-click the **BizTalkDTADb** database, double-click **Programmability**, and then click **Stored Procedures**.</span></span>  
  
13. <span data-ttu-id="8d501-137">在**物件總管詳細資料**] 窗格中，以滑鼠右鍵按一下**[dtasp_purgeallcompletedtrackingdata]**，然後按一下 [**執行預存程序**。</span><span class="sxs-lookup"><span data-stu-id="8d501-137">In the **Object Explorer Details** pane, right-click **dtasp_PurgeAllCompletedTrackingData**, and then click **Execute Stored Procedure**.</span></span>  
  
14. <span data-ttu-id="8d501-138">在**執行程序**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="8d501-138">In the **Execute Procedure** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="8d501-139">不論其完成時間為何，此預存程序會刪除和已完成的執行個體關聯的所有追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="8d501-139">This stored procedure deletes all tracking data associated with completed instances regardless of their completion time.</span></span>  
  
15. <span data-ttu-id="8d501-140">開啟 [服務]。</span><span class="sxs-lookup"><span data-stu-id="8d501-140">Open Services.</span></span> <span data-ttu-id="8d501-141">按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。</span><span class="sxs-lookup"><span data-stu-id="8d501-141">Click **Start**, click **Run**, and then type **services.msc**.</span></span> <span data-ttu-id="8d501-142">如果**使用者帳戶控制** 對話方塊隨即出現，請確認描述的動作是什麼，並再按**繼續**。</span><span class="sxs-lookup"><span data-stu-id="8d501-142">If a **User Account Control** dialog is displayed, verify that the action described is what you want, and then click **Continue**.</span></span>  
  
16. <span data-ttu-id="8d501-143">每個下列服務，以滑鼠右鍵按一下，然後按一下 **啟動**:</span><span class="sxs-lookup"><span data-stu-id="8d501-143">Right-click each of the following services, and then click **Start**:</span></span>  
  
    -   <span data-ttu-id="8d501-144">BizTalkServiceBizTalkGroup: BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="8d501-144">BizTalkServiceBizTalkGroup : BizTalkServerApplication</span></span>  
  
    -   <span data-ttu-id="8d501-145">企業單一登入服務</span><span class="sxs-lookup"><span data-stu-id="8d501-145">Enterprise Single Sign-On Service</span></span>  
  
    -   <span data-ttu-id="8d501-146">規則引擎更新服務</span><span class="sxs-lookup"><span data-stu-id="8d501-146">Rule Engine Update Service</span></span>  
  
17. <span data-ttu-id="8d501-147">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="8d501-147">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
18. <span data-ttu-id="8d501-148">在**BizTalk Server 管理主控台**，連按兩下**BizTalk 群組**，連按兩下**平台設定**，然後按一下 **主機執行個體**。</span><span class="sxs-lookup"><span data-stu-id="8d501-148">In the **BizTalk Server Administration Console**, double-click the **BizTalk Group**, double-click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
19. <span data-ttu-id="8d501-149">在**物件總管詳細資料**] 窗格中，每個停止的主控件執行個體，以滑鼠右鍵按一下，然後按一下 [**啟動**。</span><span class="sxs-lookup"><span data-stu-id="8d501-149">In the **Object Explorer Details** pane, right-click each stopped host instance, and then click **Start**.</span></span>  
  
20. <span data-ttu-id="8d501-150">啟動 [命令提示字元]，如上面的步驟 8 所述。</span><span class="sxs-lookup"><span data-stu-id="8d501-150">Start a command prompt, as described in step 8 above.</span></span>  
  
21. <span data-ttu-id="8d501-151">在命令提示字元中，以重新啟動的每個您停止 IIS 服務步驟 4。</span><span class="sxs-lookup"><span data-stu-id="8d501-151">At the command prompt, restart each of the IIS services that you stopped in step 4.</span></span> <span data-ttu-id="8d501-152">類型：</span><span class="sxs-lookup"><span data-stu-id="8d501-152">Type:</span></span>  
  
     <span data-ttu-id="8d501-153">**net start**  *\<IISserviceName\>*</span><span class="sxs-lookup"><span data-stu-id="8d501-153">**net start** *\<IISserviceName\>*</span></span>  
  
     <span data-ttu-id="8d501-154">其中 *\<IISserviceName\>* 是您想要重新啟動 IIS 服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d501-154">Where *\<IISserviceName\>* is the name of the IIS service you want to restart.</span></span> <span data-ttu-id="8d501-155">您必須為每個 IIS 服務重複此命令。</span><span class="sxs-lookup"><span data-stu-id="8d501-155">You must repeat this command for each of the IIS services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d501-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d501-156">See Also</span></span>  
 <span data-ttu-id="8d501-157">[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="8d501-157">[Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md) </span></span>  
 <span data-ttu-id="8d501-158">[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="8d501-158">[Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md) </span></span>  
 [<span data-ttu-id="8d501-159">如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務</span><span class="sxs-lookup"><span data-stu-id="8d501-159">How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services</span></span>](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)