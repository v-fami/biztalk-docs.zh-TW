---
title: "如何排程 「 備份 BizTalk Server 」 工作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, scheduling
- backing up, backup jobs
- scheduling, backup jobs
ms.assetid: 6e89fff4-da87-4cdc-acc4-46f03c3269fc
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d6b40ae933874e1c25cb3a93dbbeab514ef5dfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-schedule-the-backup-biztalk-server-job"></a><span data-ttu-id="181fd-102">如何排程備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="181fd-102">How to Schedule the Backup BizTalk Server Job</span></span>
<span data-ttu-id="181fd-103">備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業執行依排程由 SQL Server Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="181fd-103">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs as scheduled by the SQL Server Agent service.</span></span> <span data-ttu-id="181fd-104">如果您想要建立較頻繁或較不頻繁的備份，您可以使用 SQL Server Management Studio 來變更「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業的排程。</span><span class="sxs-lookup"><span data-stu-id="181fd-104">If you want to create more frequent or less frequent backups, you can change the schedule of the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job by using SQL Server Management Studio.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="181fd-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="181fd-105">Prerequisites</span></span>  
 <span data-ttu-id="181fd-106">您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="181fd-106">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-schedule-the-backup-biztalk-server-job-sql-server-2008"></a><span data-ttu-id="181fd-107">若要排程備份 BizTalk Server 作業 (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="181fd-107">To schedule the Backup BizTalk Server job (SQL Server 2008)</span></span>  
  
1.  <span data-ttu-id="181fd-108">包含 BizTalk 管理資料庫的電腦，按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**，然後按一下  **Microsoft SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="181fd-108">On the computer that contains the BizTalk Management database, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **Microsoft SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="181fd-109">在**連接到伺服器**對話方塊中，指定位於 BizTalk Server 資料庫所在的 SQL server 的名稱以及適當的驗證類型，然後按一下 **連接**。</span><span class="sxs-lookup"><span data-stu-id="181fd-109">In the **Connect to Server** dialog box, specify the name of the SQL Server where the BizTalk Server databases reside and the appropriate authentication type, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="181fd-110">在 物件總管 中，按兩下**SQL Server Agent**，然後按一下 **作業**。</span><span class="sxs-lookup"><span data-stu-id="181fd-110">In the Object Explorer, double-click **SQL Server Agent**, and then click **Jobs**.</span></span>  
  
4.  <span data-ttu-id="181fd-111">在詳細資料窗格中，以滑鼠右鍵按一下**備份 BizTalk Server (BizTalkMgmtDb)**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="181fd-111">In the details pane, right-click **Backup BizTalk Server (BizTalkMgmtDb)**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="181fd-112">在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)**對話方塊的 **選取頁面**，按一下 **步驟**。</span><span class="sxs-lookup"><span data-stu-id="181fd-112">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)** dialog box, under **Select a page**, click **Steps**.</span></span>  
  
6.  <span data-ttu-id="181fd-113">在**作業步驟清單**，按一下  **BackupFull**，然後按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="181fd-113">In the **Job step list**, click **BackupFull**, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="181fd-114">在**作業步驟屬性-BackupFull**對話方塊中，於**命令**方塊中，將頻率變更成要執行完整備份的所需間隔來編輯命令： **'h'**（每小時）、**有 '** （每天）、 **'w'** （每週）、 **am'** （每月） **'y'** （每年），然後按一下**[確定]**.</span><span class="sxs-lookup"><span data-stu-id="181fd-114">In the **Job Step Properties - BackupFull** dialog box, in the **Command** box, edit the command by changing the frequency to the desired interval at which to perform a full backup: **'h'** (hourly), **'d'** (daily), **'w'** (weekly), **'m'** (monthly), **'y'** (yearly), and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="181fd-115">第一次的「備份 BizTalk Server」工作會在新週期中執行，並且會進行完整備份。</span><span class="sxs-lookup"><span data-stu-id="181fd-115">The first time the Backup BizTalk Server job is run during a new period, a full backup is performed.</span></span>  
  
8.  <span data-ttu-id="181fd-116">在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)**對話方塊的 **選取頁面**，按一下 **排程**。</span><span class="sxs-lookup"><span data-stu-id="181fd-116">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)** dialog box, under **Select a page**, click **Schedules**.</span></span>  
  
9. <span data-ttu-id="181fd-117">在**排程清單**，按一下  **MarkAndBackupLogSched**，然後按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="181fd-117">In the **Schedule list**, click **MarkAndBackupLogSched**, and then click **Edit**.</span></span>  
  
10. <span data-ttu-id="181fd-118">在**作業排程屬性-markandbackuplogsched**對話方塊中的，在 排程類型 選取**週期性**從下拉式清單方塊 （如果尚未選取）。</span><span class="sxs-lookup"><span data-stu-id="181fd-118">In the **Job Schedule Properties - MarkAndBackupLogSched** dialog box, in Schedule type, select **Recurring** from the drop-down list box (if it is not already selected).</span></span>  
  
     <span data-ttu-id="181fd-119">依照預設，作業將排程為每 15 分鐘執行一次。</span><span class="sxs-lookup"><span data-stu-id="181fd-119">By default, the job is scheduled to run every 15 minutes.</span></span>  
  
11. <span data-ttu-id="181fd-120">視需要排程的更新，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="181fd-120">Update the schedule as desired, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="181fd-121">如需有關排程 SQL Server Agent 作業的詳細資訊，請參閱 「[排程作業](http://go.microsoft.com/fwlink/?LinkId=195887)。 」</span><span class="sxs-lookup"><span data-stu-id="181fd-121">For more information about scheduling SQL Server Agent jobs, see "[Scheduling Jobs](http://go.microsoft.com/fwlink/?LinkId=195887)."</span></span>  
  
12. <span data-ttu-id="181fd-122">在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="181fd-122">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="181fd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="181fd-123">See Also</span></span>  
 <span data-ttu-id="181fd-124">[如何設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="181fd-124">[How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md) </span></span>  
 <span data-ttu-id="181fd-125">[如何設定記錄傳送目的地系統](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span><span class="sxs-lookup"><span data-stu-id="181fd-125">[How to Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span></span>  
 <span data-ttu-id="181fd-126">[如何還原資料庫](../core/how-to-restore-your-databases.md) </span><span class="sxs-lookup"><span data-stu-id="181fd-126">[How to Restore Your Databases](../core/how-to-restore-your-databases.md) </span></span>  
 [<span data-ttu-id="181fd-127">備份和還原的相關進階的資訊</span><span class="sxs-lookup"><span data-stu-id="181fd-127">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)