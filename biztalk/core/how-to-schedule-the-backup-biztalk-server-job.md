---
title: 排程備份 BizTalk Server 作業 |Microsoft 文件
description: 設定備份 BizTalk Server 的工作參數，並將排程設定為執行每月、 每週、 日或每小時
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
ms.openlocfilehash: 7f09ca97f65605ac3bf427d1c1fcc322a14feb53
ms.sourcegitcommit: 9aaed443492b74729171fef79c634bff561af929
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2017
ms.locfileid: "23980750"
---
# <a name="schedule-the-backup-biztalk-server-job"></a><span data-ttu-id="9bbb5-103">排程備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="9bbb5-103">Schedule the Backup BizTalk Server Job</span></span>
<span data-ttu-id="9bbb5-104">備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業執行依排程由 SQL Server Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-104">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs as scheduled by the SQL Server Agent service.</span></span> <span data-ttu-id="9bbb5-105">如果您想要建立較頻繁或較不頻繁的備份，您可以使用 SQL Server Management Studio 來變更「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業的排程。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-105">If you want to create more frequent or less frequent backups, you can change the schedule of the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job by using SQL Server Management Studio.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9bbb5-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="9bbb5-106">Prerequisites</span></span>  
<span data-ttu-id="9bbb5-107">使用 SQL Server sysadmin 固定伺服器角色的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-107">Sign in with an account that is a member of the SQL Server sysadmin fixed server role.</span></span>  
  
## <a name="schedule-the-backup-biztalk-server-job"></a><span data-ttu-id="9bbb5-108">排程備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="9bbb5-108">Schedule the Backup BizTalk Server job</span></span>
  
1.  <span data-ttu-id="9bbb5-109">在裝載 BizTalk 管理資料庫的 SQL Server 上開啟**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-109">On the SQL Server that hosts the BizTalk Management database, open **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="9bbb5-110">在**連接到伺服器**，輸入 BizTalk Server 資料庫位於，在其中選取驗證類型的 SQL server 名稱，然後**連接**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-110">In **Connect to Server**, enter the name of the SQL Server where the BizTalk Server databases reside, select the authentication type, and then **Connect**.</span></span>  
  
3.  <span data-ttu-id="9bbb5-111">在 [物件總管] 中，按兩下**SQL Server Agent**，然後選取**作業**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-111">In the Object Explorer, double-click **SQL Server Agent**, and then select **Jobs**.</span></span>  
  
4.  <span data-ttu-id="9bbb5-112">在詳細資料窗格中，以滑鼠右鍵按一下**備份 BizTalk Server (BizTalkMgmtDb)**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-112">In the details pane, right-click **Backup BizTalk Server (BizTalkMgmtDb)**, and then select **Properties**.</span></span>  
  
5.  <span data-ttu-id="9bbb5-113">在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)** 下**選取頁面**，選取**步驟**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-113">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="9bbb5-114">在**作業步驟清單**，選取**BackupFull**，然後選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-114">In the **Job step list**, select **BackupFull**, and then select **Edit**.</span></span>  
  
7.  <span data-ttu-id="9bbb5-115">在**作業步驟屬性-BackupFull**，請在**命令**方塊中，藉由變更要執行完整備份的頻率更新命令： **'h'** （每小時）、**有 '** （每天）、 **'w'** （每週）、 **am'** （每月）、 **'y'** （每年）。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-115">In the **Job Step Properties - BackupFull**, in the **Command** box, update the command by changing the frequency to run a full backup: **'h'** (hourly), **'d'** (daily), **'w'** (weekly), **'m'** (monthly), **'y'** (yearly).</span></span> <span data-ttu-id="9bbb5-116">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-116">Select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bbb5-117">「 備份 BizTalk Server 」 工作執行時，第一次此作業完成的完整備份。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-117">The first time the Backup BizTalk Server job runs, it completes a full backup.</span></span>  
    
8.  <span data-ttu-id="9bbb5-118">設定其他 **@frequency** 參數：</span><span class="sxs-lookup"><span data-stu-id="9bbb5-118">Configure additional **@frequency** parameters:</span></span>  
  
    - <span data-ttu-id="9bbb5-119">**@ForceFullBackupAfterPartialSetFailure**： 預設值是**false**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-119">**@ForceFullBackupAfterPartialSetFailure**: The default value is **false**.</span></span> <span data-ttu-id="9bbb5-120">當**false**，如果完整備份失敗，系統會等到下一個循環，直到建立完整備份為止。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-120">When **false**, if the full backup fails, the system waits for the next cycle until the full backup is made.</span></span>  
    
        > [!NOTE]
        >  <span data-ttu-id="9bbb5-121">如果您 **@frequency** 設定長時間 （例如每週、 每月、 每年），然後將這個參數設定**false**可能會有風險。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-121">If your **@frequency** setting is long (like weekly, monthly, yearly), then setting this parameter to **false** could be dangerous.</span></span> <span data-ttu-id="9bbb5-122">在此案例中，可能是最佳這個旗標設為**true**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-122">In this scenario, it may be best to set this flag to **true**.</span></span> <span data-ttu-id="9bbb5-123">當**true**每次失敗，系統會強制其本身，以建立完整備份。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-123">When **true**, every time there is a failure, the system forces itself to create a full backup.</span></span> <span data-ttu-id="9bbb5-124">可能有小方面的影響，但它是 safter 具有可復原的系統。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-124">There may be a small performance impact, but it’s safter to have a recoverable system.</span></span>
  
    - <span data-ttu-id="9bbb5-125">**@BackupHour**: 預設值 NULL。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-125">**@BackupHour**: The default valueis NULL.</span></span> <span data-ttu-id="9bbb5-126">此參數直接相關 **@Frequency** 。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-126">This parameter is directly related to **@Frequency**.</span></span> <span data-ttu-id="9bbb5-127">當您將頻率設**h** （每小時），您設定要執行完整備份當天的小時。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-127">When you set the frequency to **h** (hourly), you set which hour of the day you want the full backup to run.</span></span> <span data-ttu-id="9bbb5-128">您可以選擇介於 0 （午夜） 到 23 （晚上 11 點） 之間的值。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-128">You can choose a value between 0 (midnight) to 23 (11 PM).</span></span> <span data-ttu-id="9bbb5-129">如果保留空白，每小時執行完整備份。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-129">If left blank, the full backup runs every hour.</span></span>  
    
       > [!NOTE]
        >  <span data-ttu-id="9bbb5-130">如果您設定此參數以數字 0 到 23 的範圍 （例如，100，則為-1） 以外，系統會強制其設為 0。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-130">If you set this parameter with a number outside the 0 to 23 range (for example, 100 or -1), the system forces it to 0.</span></span>
  
    - <span data-ttu-id="9bbb5-131">**@UseLocalTime**： 一種額外的參數，使用本地時間表示。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-131">**@UseLocalTime**: An extra parameter that states to use local time.</span></span> <span data-ttu-id="9bbb5-132">根據預設，工作會使用 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-132">By default, the job works with UTC time.</span></span> <span data-ttu-id="9bbb5-133">因此如果您住在澳洲 （此為 UTC + 10 小時），您的備份會在上午 10，而不是午夜執行。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-133">So if you live in Australia (which is UTC + 10 hours), your backup runs at 10am rather than midnight.</span></span> <span data-ttu-id="9bbb5-134">最佳做法，建議您將此設**1** (true)。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-134">As a best practice, it is recommended to set this to **1** (true).</span></span>  
  
9.  <span data-ttu-id="9bbb5-135">在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)** 下**選取頁面**，按一下 **排程**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-135">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, under **Select a page**, click **Schedules**.</span></span>  
  
10. <span data-ttu-id="9bbb5-136">在**排程清單**，按一下  **MarkAndBackupLogSched**，然後按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-136">In the **Schedule list**, click **MarkAndBackupLogSched**, and then click **Edit**.</span></span>  
  
11. <span data-ttu-id="9bbb5-137">在**作業排程屬性-markandbackuplogsched**，在 排程類型 選取**週期性**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-137">In the **Job Schedule Properties - MarkAndBackupLogSched**, in Schedule type, select **Recurring** from the drop-down list.</span></span>  
  
     <span data-ttu-id="9bbb5-138">依照預設，作業將排程為每 15 分鐘執行一次。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-138">By default, the job is scheduled to run every 15 minutes.</span></span>  
     
    > [!NOTE]
    >  <span data-ttu-id="9bbb5-139">您可以變更此值，根據您的需求，但是在非生產環境中的第一個測試。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-139">You can change this value according to your requirements, but first test in non-production environment.</span></span> <span data-ttu-id="9bbb5-140">頻繁的備份中將此值太低的結果，並將新增至您的 SQL 環境中的背景載入。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-140">Setting this value too low results in frequent backups, and adds to the background load in your SQL environment.</span></span> <span data-ttu-id="9bbb5-141">設定太高的值可能會增加交易記錄的大小，並影響效能。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-141">Setting this value too high may increase the size of transaction logs, and impact performance.</span></span> <span data-ttu-id="9bbb5-142">在某些情況下，建議保留預設值。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-142">In some situations, it is recommended to leave the default value.</span></span>    
  
12. <span data-ttu-id="9bbb5-143">更新排程，如有需要，，然後選取 **確定**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-143">Update the schedule if desired, and then select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bbb5-144">[排程作業](https://docs.microsoft.com/sql/ssms/agent/schedule-a-job)提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-144">[Scheduling Jobs](https://docs.microsoft.com/sql/ssms/agent/schedule-a-job) provides more details.</span></span>
  
13. <span data-ttu-id="9bbb5-145">在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)**，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="9bbb5-145">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, click **OK**.</span></span>  
  
## <a name="more-good-stuff"></a><span data-ttu-id="9bbb5-146">更多實用功能</span><span class="sxs-lookup"><span data-stu-id="9bbb5-146">More good stuff</span></span>  
 <span data-ttu-id="9bbb5-147">[設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="9bbb5-147">[Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md) </span></span>  
 <span data-ttu-id="9bbb5-148">[設定記錄傳送的目的系統](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span><span class="sxs-lookup"><span data-stu-id="9bbb5-148">[Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span></span>  
 <span data-ttu-id="9bbb5-149">[還原資料庫](../core/how-to-restore-your-databases.md) </span><span class="sxs-lookup"><span data-stu-id="9bbb5-149">[Restore Your Databases](../core/how-to-restore-your-databases.md) </span></span>  
 [<span data-ttu-id="9bbb5-150">備份和還原的進階資訊</span><span class="sxs-lookup"><span data-stu-id="9bbb5-150">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)
