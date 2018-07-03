---
title: 排程備份 BizTalk Server 作業 |Microsoft Docs
description: 設定備份 BizTalk Server 作業參數，並設定排程來執行每個月、 每週、 每天或每小時
ms.custom: ''
ms.date: 11/02/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e89fff4-da87-4cdc-acc4-46f03c3269fc
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83dd415648c55b53a9212ce20f4b1f754fb4fbb6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005127"
---
# <a name="schedule-the-backup-biztalk-server-job"></a><span data-ttu-id="bfaf7-103">排程備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="bfaf7-103">Schedule the Backup BizTalk Server Job</span></span>
<span data-ttu-id="bfaf7-104">備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]由 SQL Server Agent 服務排程的作業執行。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-104">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs as scheduled by the SQL Server Agent service.</span></span> <span data-ttu-id="bfaf7-105">如果您想要建立較頻繁或較不頻繁的備份，您可以使用 SQL Server Management Studio 來變更「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業的排程。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-105">If you want to create more frequent or less frequent backups, you can change the schedule of the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job by using SQL Server Management Studio.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bfaf7-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="bfaf7-106">Prerequisites</span></span>  
<span data-ttu-id="bfaf7-107">使用 SQL Server sysadmin 固定伺服器角色的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-107">Sign in with an account that is a member of the SQL Server sysadmin fixed server role.</span></span>  
  
## <a name="schedule-the-backup-biztalk-server-job"></a><span data-ttu-id="bfaf7-108">排程備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="bfaf7-108">Schedule the Backup BizTalk Server job</span></span>
  
1. <span data-ttu-id="bfaf7-109">在 SQL 伺服器裝載 BizTalk 管理資料庫上，開啟**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-109">On the SQL Server that hosts the BizTalk Management database, open **SQL Server Management Studio**.</span></span>

2. <span data-ttu-id="bfaf7-110">在 **連接到伺服器**，輸入 BizTalk Server 資料庫位於，在其中選取驗證類型，在 SQL Server 的名稱，然後**Connect**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-110">In **Connect to Server**, enter the name of the SQL Server where the BizTalk Server databases reside, select the authentication type, and then **Connect**.</span></span>  
  
3. <span data-ttu-id="bfaf7-111">在 [物件總管] 中，按兩下**SQL Server Agent**，然後選取**作業**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-111">In the Object Explorer, double-click **SQL Server Agent**, and then select **Jobs**.</span></span>  
  
4. <span data-ttu-id="bfaf7-112">在 [詳細資料] 窗格中，以滑鼠右鍵按一下**備份 BizTalk Server (BizTalkMgmtDb)**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-112">In the details pane, right-click **Backup BizTalk Server (BizTalkMgmtDb)**, and then select **Properties**.</span></span>  
  
5. <span data-ttu-id="bfaf7-113">在 **作業屬性-備份 BizTalk Server (BizTalkMgmtDb)** 下方**選取頁面**，選取**步驟**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-113">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, under **Select a page**, select **Steps**.</span></span>  
  
6. <span data-ttu-id="bfaf7-114">在 **作業步驟清單**，選取**BackupFull**，然後選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-114">In the **Job step list**, select **BackupFull**, and then select **Edit**.</span></span>  
  
7. <span data-ttu-id="bfaf7-115">在 **作業步驟屬性-BackupFull**，請在**命令**方塊中，藉由變更要執行完整備份的頻率更新命令： **'h'** （每小時），**有 '** （每天）、 **'w'** （每週）、**是 '** （每月）、 **'y'** （每年）。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-115">In the **Job Step Properties - BackupFull**, in the **Command** box, update the command by changing the frequency to run a full backup: **'h'** (hourly), **'d'** (daily), **'w'** (weekly), **'m'** (monthly), **'y'** (yearly).</span></span> <span data-ttu-id="bfaf7-116">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-116">Select **OK**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="bfaf7-117">「 備份 BizTalk Server 」 工作執行時，第一次完成的完整備份。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-117">The first time the Backup BizTalk Server job runs, it completes a full backup.</span></span>  
    
8. <span data-ttu-id="bfaf7-118">設定額外<strong>@frequency</strong>參數：</span><span class="sxs-lookup"><span data-stu-id="bfaf7-118">Configure additional <strong>@frequency</strong> parameters:</span></span>  
  
   - <span data-ttu-id="bfaf7-119"><strong>@ForceFullBackupAfterPartialSetFailure</strong>： 預設值是**false**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-119"><strong>@ForceFullBackupAfterPartialSetFailure</strong>: The default value is **false**.</span></span> <span data-ttu-id="bfaf7-120">當**false**，如果完整備份失敗，系統會等到下一個循環之前進行完整備份。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-120">When **false**, if the full backup fails, the system waits for the next cycle until the full backup is made.</span></span>  
    
     > [!NOTE]
     >  <span data-ttu-id="bfaf7-121">如果您<strong>@frequency</strong>設定為長時間 （例如每週、 每月、 每年），然後將此參數設**false**可能十分危險。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-121">If your <strong>@frequency</strong> setting is long (like weekly, monthly, yearly), then setting this parameter to **false** could be dangerous.</span></span> <span data-ttu-id="bfaf7-122">在此案例中，可能是最理想的做法設定此旗標 **，則為 true**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-122">In this scenario, it may be best to set this flag to **true**.</span></span> <span data-ttu-id="bfaf7-123">當 **，則為 true**每次失敗，系統會強制本身，以建立完整備份。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-123">When **true**, every time there is a failure, the system forces itself to create a full backup.</span></span> <span data-ttu-id="bfaf7-124">可能有小效能影響，但它是 safter 可復原的系統。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-124">There may be a small performance impact, but it’s safter to have a recoverable system.</span></span>
  
   - <span data-ttu-id="bfaf7-125"><strong>@BackupHour</strong>: 預設值 NULL。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-125"><strong>@BackupHour</strong>: The default valueis NULL.</span></span> <span data-ttu-id="bfaf7-126">此參數直接與相關<strong>@Frequency</strong>。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-126">This parameter is directly related to <strong>@Frequency</strong>.</span></span> <span data-ttu-id="bfaf7-127">當您將頻率設為**h** （每小時），您將設定您要執行完整備份的當日的小時。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-127">When you set the frequency to **h** (hourly), you set which hour of the day you want the full backup to run.</span></span> <span data-ttu-id="bfaf7-128">您可以選擇介於 0 （午夜） 到 23 （晚上 11 點） 之間的值。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-128">You can choose a value between 0 (midnight) to 23 (11 PM).</span></span> <span data-ttu-id="bfaf7-129">如果保留空白，完整備份會每小時執行。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-129">If left blank, the full backup runs every hour.</span></span>  
    
      > [!NOTE]
       >  <span data-ttu-id="bfaf7-130">如果您以數字 0 到 23 範圍 （例如，100，則為-1） 設定此參數，則系統會強制其設為 0。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-130">If you set this parameter with a number outside the 0 to 23 range (for example, 100 or -1), the system forces it to 0.</span></span>
  
   - <span data-ttu-id="bfaf7-131"><strong>@UseLocalTime</strong>： 這是額外的參數，指出要使用本地時間。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-131"><strong>@UseLocalTime</strong>: An extra parameter that states to use local time.</span></span> <span data-ttu-id="bfaf7-132">根據預設，作業的運作方式的 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-132">By default, the job works with UTC time.</span></span> <span data-ttu-id="bfaf7-133">因此如果您住在澳洲 （這是 UTC + 10 小時），您的備份將會在上午 10 點，而不是午夜執行。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-133">So if you live in Australia (which is UTC + 10 hours), your backup runs at 10am rather than midnight.</span></span> <span data-ttu-id="bfaf7-134">最佳做法，建議您將此設為**1** (true)。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-134">As a best practice, it is recommended to set this to **1** (true).</span></span>  
  
9. <span data-ttu-id="bfaf7-135">在 **作業屬性-備份 BizTalk Server (BizTalkMgmtDb)** 下方**選取頁面**，按一下 **排程**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-135">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, under **Select a page**, click **Schedules**.</span></span>  
  
10. <span data-ttu-id="bfaf7-136">在 **排程清單**，按一下**MarkAndBackupLogSched**，然後按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-136">In the **Schedule list**, click **MarkAndBackupLogSched**, and then click **Edit**.</span></span>  
  
11. <span data-ttu-id="bfaf7-137">在 **作業排程屬性-markandbackuplogsched**，在排程類型 中，選取**週期性**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-137">In the **Job Schedule Properties - MarkAndBackupLogSched**, in Schedule type, select **Recurring** from the drop-down list.</span></span>  
  
     <span data-ttu-id="bfaf7-138">依照預設，作業將排程為每 15 分鐘執行一次。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-138">By default, the job is scheduled to run every 15 minutes.</span></span>  
     
    > [!NOTE]
    >  <span data-ttu-id="bfaf7-139">您可以變更此值，根據您的需求，但在非生產環境中的第一個測試。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-139">You can change this value according to your requirements, but first test in non-production environment.</span></span> <span data-ttu-id="bfaf7-140">頻繁的備份，在設定此值過低的結果，並將新增至您的 SQL 環境中的背景負載。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-140">Setting this value too low results in frequent backups, and adds to the background load in your SQL environment.</span></span> <span data-ttu-id="bfaf7-141">設定此值太高，可能會增加交易記錄檔的大小，影響效能。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-141">Setting this value too high may increase the size of transaction logs, and impact performance.</span></span> <span data-ttu-id="bfaf7-142">在某些情況下，建議保留預設值。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-142">In some situations, it is recommended to leave the default value.</span></span>    
  
12. <span data-ttu-id="bfaf7-143">更新排程，如有需要，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-143">Update the schedule if desired, and then select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bfaf7-144">[排程作業](https://docs.microsoft.com/sql/ssms/agent/schedule-a-job)提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-144">[Scheduling Jobs](https://docs.microsoft.com/sql/ssms/agent/schedule-a-job) provides more details.</span></span>
  
13. <span data-ttu-id="bfaf7-145">在 **作業屬性-備份 BizTalk Server (BizTalkMgmtDb)**，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="bfaf7-145">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, click **OK**.</span></span>  
  
## <a name="more-good-stuff"></a><span data-ttu-id="bfaf7-146">更多實用功能</span><span class="sxs-lookup"><span data-stu-id="bfaf7-146">More good stuff</span></span>  
 <span data-ttu-id="bfaf7-147">[設定備份 BizTalk Server 作業](../core/how-to-configure-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="bfaf7-147">[Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md) </span></span>  
 <span data-ttu-id="bfaf7-148">[設定記錄傳送目的地系統](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span><span class="sxs-lookup"><span data-stu-id="bfaf7-148">[Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span></span>  
 <span data-ttu-id="bfaf7-149">[還原資料庫](../core/how-to-restore-your-databases.md) </span><span class="sxs-lookup"><span data-stu-id="bfaf7-149">[Restore Your Databases](../core/how-to-restore-your-databases.md) </span></span>  
 [<span data-ttu-id="bfaf7-150">備份和還原的進階資訊</span><span class="sxs-lookup"><span data-stu-id="bfaf7-150">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)
