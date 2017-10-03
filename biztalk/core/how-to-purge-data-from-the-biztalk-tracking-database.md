---
title: "如何從 BizTalk 追蹤資料庫清除資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, purging
- purging
- DTA Purge and Archive job, purging data
- purging, DTA Purge and Archive job
ms.assetid: cdf12866-442d-4c1f-b10f-ebf8d665d521
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01c56629aaa0934010ba79637b4e4a134bf29f26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-purge-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="4c274-102">如何從 BizTalk 追蹤資料庫清除資料</span><span class="sxs-lookup"><span data-stu-id="4c274-102">How to Purge Data from the BizTalk Tracking Database</span></span>
<span data-ttu-id="4c274-103">當您從「BizTalk 追蹤」(BizTalkDTADb) 資料庫清除資料時，「DTA 清除和封存」工作會從「BizTalk 追蹤」(BizTalkDTADb) 資料庫清除不同類型的追蹤資訊，例如訊息與服務執行個體資訊、協調流程事件資訊以及規則引擎追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="4c274-103">When you purge data from the BizTalk Tracking (BizTalkDTADb) database, the DTA Purge and Archive job purges different types of tracking information such as message and service instance information, orchestration event information, and rules engine tracking data from the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4c274-104">使用此程序不會封存「BizTalk 追蹤」(BizTalkDTADb) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="4c274-104">The BizTalk Tracking (BizTalkDTADb) database is not archived using this procedure.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4c274-105">在未啟用追蹤的情況下，如果在協調流程中攔截並處理例外狀況，則具有「已啟動」狀態及例外狀況資訊的孤立的追蹤執行個體可能會插入「BizTalk 追蹤」(BizTalkDTADb) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="4c274-105">If an exception is caught and handled in an orchestration without tracking turned on, an orphaned tracking instance with a Started state and exception information may be inserted into the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="4c274-106">清除資料庫之後，這項記錄將會保留下來。</span><span class="sxs-lookup"><span data-stu-id="4c274-106">This record will remain after purging the database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4c274-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="4c274-107">Prerequisites</span></span>  
 <span data-ttu-id="4c274-108">您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="4c274-108">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-purge-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="4c274-109">若要從 BizTalk 追蹤資料庫清除資料</span><span class="sxs-lookup"><span data-stu-id="4c274-109">To purge data from the BizTalk Tracking database</span></span>  
  
1.  <span data-ttu-id="4c274-110">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="4c274-110">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="4c274-111">在**連接到伺服器**對話方塊中，指定 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL Server 和適當的驗證類型的名稱，然後按一下**連接**至連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="4c274-111">In the **Connect to Server** dialog box, specify the name of the SQL Server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the SQL Server.</span></span>  
  
3.  <span data-ttu-id="4c274-112">在**Microsoft SQL Server Management Studio**，連按兩下**SQL Server Agent**，然後按一下 **作業**。</span><span class="sxs-lookup"><span data-stu-id="4c274-112">In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.</span></span>  
  
4.  <span data-ttu-id="4c274-113">在**物件總管詳細資料**] 窗格中，以滑鼠右鍵按一下**DTA 清除與封存 (BizTalkDTADb)**，然後按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4c274-113">In the **Object Explorer Details** pane, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="4c274-114">在**作業屬性-DTA 清除與封存 (BizTalkDTADb)**對話方塊的 **選取頁面**，按一下 **步驟**。</span><span class="sxs-lookup"><span data-stu-id="4c274-114">In the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **Steps**.</span></span>  
  
6.  <span data-ttu-id="4c274-115">在**作業步驟清單**，按一下 **封存及清除**，然後按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="4c274-115">In the **Job step list**, click **Archive and Purge**, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="4c274-116">在**作業步驟屬性-封存與清除**對話方塊**一般**頁面上，於**命令**方塊中，變更**exec dtasp_BackupAndPurgeTrackingDatabase**至**exec dtasp_PurgeTrackingDatabase**。</span><span class="sxs-lookup"><span data-stu-id="4c274-116">In the **Job Step Properties - Archive and Purge** dialog box, on the **General** page, in the **Command** box, change **exec dtasp_BackupAndPurgeTrackingDatabase** to **exec dtasp_PurgeTrackingDatabase**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="4c274-117">**Exec dtasp_PurgeTrackingDatabase**預存程序不會封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="4c274-117">The **exec dtasp_PurgeTrackingDatabase** stored procedure does not archive the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="4c274-118">使用此選項前，請確定您已不需要封存的追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="4c274-118">Before using this option, be certain that you no longer require archived tracking data.</span></span>  
  
8.  <span data-ttu-id="4c274-119">在**命令**方塊中，編輯適當的下列參數，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4c274-119">In the **Command** box, edit the following parameters as appropriate, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="4c274-120">@nHourstinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。</span><span class="sxs-lookup"><span data-stu-id="4c274-120">@nHours tinyint — Any completed instance older than (live hours) + (live days) will be deleted along with all associated data.</span></span>  
  
    -   <span data-ttu-id="4c274-121">@nDaystinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。</span><span class="sxs-lookup"><span data-stu-id="4c274-121">@nDays tinyint — Any completed instance older than (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="4c274-122">預設間隔是 1 天。</span><span class="sxs-lookup"><span data-stu-id="4c274-122">Default interval is 1 day.</span></span>  
  
    -   <span data-ttu-id="4c274-123">@nHardDaystinyint —，也將會刪除早於此日期的所有資料，即使資料不完整。</span><span class="sxs-lookup"><span data-stu-id="4c274-123">@nHardDays tinyint — All data older than this day will be deleted, even if the data is incomplete.</span></span> <span data-ttu-id="4c274-124">為 HardDeleteDays 指定的時間間隔應該大於資料存留窗期。</span><span class="sxs-lookup"><span data-stu-id="4c274-124">The time interval specified for HardDeleteDays should be greater than the live window of data.</span></span> <span data-ttu-id="4c274-125">資料存留窗期是您想要在 BizTalk 追蹤 (BizTalkDTADb) 資料庫中維護追蹤資料的時間。</span><span class="sxs-lookup"><span data-stu-id="4c274-125">The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="4c274-126">早於此間隔的資料都將在下次封存時進行封存，然後再予以清除。</span><span class="sxs-lookup"><span data-stu-id="4c274-126">Anything older than this interval is eligible to be archived at the next archive and then purged.</span></span>  
  
    -   <span data-ttu-id="4c274-127">@dtLastBackup— 將此設**getutcdate （)**從 BizTalk 追蹤 (BizTalkDTADb) 資料庫清除資料。</span><span class="sxs-lookup"><span data-stu-id="4c274-127">@dtLastBackup — Set this to **GetUTCDate()** to purge data from the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="4c274-128">當設定為**NULL**，不會從資料庫清除資料。</span><span class="sxs-lookup"><span data-stu-id="4c274-128">When set to **NULL**, data is not purged from the database.</span></span>  
  
     <span data-ttu-id="4c274-129">編輯過的指令碼看起來應該類似下例：</span><span class="sxs-lookup"><span data-stu-id="4c274-129">Your edited script should look similar to this:</span></span>  
  
    ```  
    declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate() exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup  
    ```  
  
9. <span data-ttu-id="4c274-130">在**作業屬性-DTA 清除與封存 (BizTalkDTADb)**對話方塊的 **選取頁面**，按一下 **一般**，選取**啟用**核取方塊，然後**確定**。</span><span class="sxs-lookup"><span data-stu-id="4c274-130">On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **General**, select the **Enabled** check box, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c274-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c274-131">See Also</span></span>  
 [<span data-ttu-id="4c274-132">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="4c274-132">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)