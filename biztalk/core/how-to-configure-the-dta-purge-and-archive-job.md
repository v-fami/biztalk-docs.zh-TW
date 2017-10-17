---
title: "設定 DTA 的清除與封存工作 |Microsoft 文件"
description: "在 SQL Server 代理程式，以維護 BizTalk Server 中的追蹤資料庫中設定 DTA 清除與封存工作參數"
ms.custom: 
ms.date: 10/11/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 156ccf9b-284f-4b96-a395-92936e8cebcf
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 149719b7eea50ce53c14298597c94729162d43b0
ms.sourcegitcommit: 1fb633fcf919ce3124405420a5d9faa79d9d508e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2017
---
# <a name="configure-the-dta-purge-and-archive-job"></a><span data-ttu-id="b0616-103">設定 DTA 的清除與封存工作</span><span class="sxs-lookup"><span data-stu-id="b0616-103">Configure the DTA Purge and Archive Job</span></span>
<span data-ttu-id="b0616-104">您必須先設定 DTA 的清除與封存 (BizTalkDTADb) 工作，才能封存或清除「BizTalk 追蹤」(BizTalkDTADb) 資料庫的資料。</span><span class="sxs-lookup"><span data-stu-id="b0616-104">Before you can archive or purge data from the BizTalk Tracking (BizTalkDTADb) database, you must configure the DTA Purge and Archive (BizTalkDTADb) job.</span></span> <span data-ttu-id="b0616-105">這項作業會設定為呼叫 dtasp_BackupAndPurgeTrackingDatabase 預存程序，它會使用六個參數，您必須設定。</span><span class="sxs-lookup"><span data-stu-id="b0616-105">This job is configured to call the dtasp_BackupAndPurgeTrackingDatabase store procedure, which uses six parameters you must configure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b0616-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="b0616-106">Prerequisites</span></span>  
 <span data-ttu-id="b0616-107">使用 SQL Server sysadmin 固定伺服器角色的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="b0616-107">Sign in with an account that is a member of the SQL Server sysadmin fixed server role.</span></span>  
  
## <a name="configure-the-dta-purge-and-archive-job"></a><span data-ttu-id="b0616-108">設定 DTA 的清除與封存工作</span><span class="sxs-lookup"><span data-stu-id="b0616-108">Configure the DTA purge and archive job</span></span>  
  
1.  <span data-ttu-id="b0616-109">在裝載 「 BizTalk 追蹤 (BizTalkDTADb) 資料庫的 SQL Server 上開啟**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="b0616-109">On the SQL Server that hosts the BizTalk Tracking (BizTalkDTADb) database, open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="b0616-110">在**連接到伺服器**，輸入 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL server 的名稱、 輸入驗證類型，然後選取**連接**連接到 SQL server。</span><span class="sxs-lookup"><span data-stu-id="b0616-110">In **Connect to Server**, enter the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides, enter the authentication type, and then select **Connect** to connect to the SQL server.</span></span>  
  
3. <span data-ttu-id="b0616-111">按兩下**SQL Server Agent**，然後選取**作業**。</span><span class="sxs-lookup"><span data-stu-id="b0616-111">Double-click **SQL Server Agent**, and then select **Jobs**.</span></span>  
  
4.  <span data-ttu-id="b0616-112">在**物件總管詳細資料**，以滑鼠右鍵按一下**DTA 清除與封存 (BizTalkDTADb)**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b0616-112">In **Object Explorer Details**, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then select **Properties**.</span></span>  
  
5.  <span data-ttu-id="b0616-113">在**作業屬性-DTA 清除與封存 (BizTalkDTADb)**下**選取頁面**，選取**步驟**。</span><span class="sxs-lookup"><span data-stu-id="b0616-113">In **Job Properties - DTA Purge and Archive (BizTalkDTADb)**, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="b0616-114">在**作業步驟清單**，選取**封存及清除**，然後選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="b0616-114">In the **Job step list**, select **Archive and Purge**, and then select **Edit**.</span></span>  
  
7.  <span data-ttu-id="b0616-115">在**一般**，請在**命令**方塊中，更新下列參數，並選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="b0616-115">In **General**, in the **Command** box, update the following parameters, and then select **OK**.</span></span>  
  
    -   <span data-ttu-id="b0616-116">@nLiveHourstinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。</span><span class="sxs-lookup"><span data-stu-id="b0616-116">@nLiveHours tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="b0616-117">這是必要的參數沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="b0616-117">This is a required parameter with no default value.</span></span>  
  
    -   <span data-ttu-id="b0616-118">@nLiveDaystinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。</span><span class="sxs-lookup"><span data-stu-id="b0616-118">@nLiveDays tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="b0616-119">預設間隔為 0 天。</span><span class="sxs-lookup"><span data-stu-id="b0616-119">Default interval is 0 days.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b0616-120">基於 BizTalk 追蹤 (BizTalkDTADb) 資料庫的目的，LiveHours 加上 LiveDays 的總和是您要在 BizTalk Server 環境中維持的資料存留窗期。</span><span class="sxs-lookup"><span data-stu-id="b0616-120">For the purposes of the BizTalk Tracking (BizTalkDTADb) database, the sum of LiveHours plus LiveDays is the live window of data you want to maintain in your BizTalk Server environment.</span></span> <span data-ttu-id="b0616-121">存留時間超過資料存留窗期之已完成執行個體的所有相關資料都會被刪除。</span><span class="sxs-lookup"><span data-stu-id="b0616-121">All data associated with a completed instance older than the live window of data is deleted.</span></span>  
  
    -   <span data-ttu-id="b0616-122">@nHardDeleteDaystinyint — 所有資料 （即使未完成） 早於這將會被刪除。</span><span class="sxs-lookup"><span data-stu-id="b0616-122">@nHardDeleteDays tinyint — All data (even if incomplete) older than this will be deleted.</span></span> <span data-ttu-id="b0616-123">為 HardDeleteDays 指定的時間間隔應該大於資料存留窗期。</span><span class="sxs-lookup"><span data-stu-id="b0616-123">The time interval specified for HardDeleteDays should be greater than the live window of data.</span></span> <span data-ttu-id="b0616-124">資料存留窗期是您想要在 BizTalk 追蹤 (BizTalkDTADb) 資料庫中維護追蹤資料的時間。</span><span class="sxs-lookup"><span data-stu-id="b0616-124">The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="b0616-125">早於此間隔的資料都將在下次封存時進行封存，然後再予以清除。</span><span class="sxs-lookup"><span data-stu-id="b0616-125">Anything older than this interval is eligible to be archived at the next archive and then purged.</span></span> <span data-ttu-id="b0616-126">預設值為 0 天。</span><span class="sxs-lookup"><span data-stu-id="b0616-126">Default is 0 days.</span></span>  
  
    -   <span data-ttu-id="b0616-127">@nvcFoldernvarchar （1024) — 放置備份檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b0616-127">@nvcFolder nvarchar(1024) — Folder in which to put the backup files.</span></span> <span data-ttu-id="b0616-128">這是必要的參數沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="b0616-128">This is a required parameter with no default value.</span></span>  
  
    -   <span data-ttu-id="b0616-129">@nvcValidatingServersysname — 將完成驗證的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b0616-129">@nvcValidatingServer sysname — Server on which validation will be done.</span></span> <span data-ttu-id="b0616-130">NULL 值表示沒有完成任何驗證。</span><span class="sxs-lookup"><span data-stu-id="b0616-130">NULL value indicates no validation is being done.</span></span> <span data-ttu-id="b0616-131">預設值是 NULL。</span><span class="sxs-lookup"><span data-stu-id="b0616-131">Default is NULL.</span></span>  
  
    -   <span data-ttu-id="b0616-132">@fForceBackupint — 預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="b0616-132">@fForceBackup int — Default is 0.</span></span> <span data-ttu-id="b0616-133">這被保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="b0616-133">This is reserved for future use.</span></span>  
  
    -   <span data-ttu-id="b0616-134">@fHardDeleteRunningInstancesint-預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="b0616-134">@fHardDeleteRunningInstances int - Default is 0.</span></span> <span data-ttu-id="b0616-135">設定為 1 時，刪除所有執行中服務執行個體早於@nHardDeleteDays值。</span><span class="sxs-lookup"><span data-stu-id="b0616-135">When set to 1, it deletes all running service instances older than the @nHardDeleteDays value.</span></span> 
    
        > [!NOTE]
        > <span data-ttu-id="b0616-136">@fHardDeleteRunningInstances屬性是從開始提供[BizTalk Server 2016 的累計更新 1年](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016)， [BizTalk Server 2013 R2 累計更新 6年](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2)，和[BizTalk Server 2013 累計更新 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013)。</span><span class="sxs-lookup"><span data-stu-id="b0616-136">The @fHardDeleteRunningInstances property is available starting with [BizTalk Server 2016 Cumulative Update 1](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016), [BizTalk Server 2013 R2 Cumulative Update 6](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2), and [BizTalk Server 2013 Cumulative Update 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013).</span></span>  
  
    <span data-ttu-id="b0616-137">您已編輯的命令看起來應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="b0616-137">Your edited command should look similar to the following.</span></span> <span data-ttu-id="b0616-138">在下列範例中，沒有 1 小時的即時視窗、 硬清除的 1 天，並刪除所有執行服務執行個體超過 1 天：</span><span class="sxs-lookup"><span data-stu-id="b0616-138">In the following example, there is a live window of 1 hour, a hard purge of 1 day, and deletes all running service instances older than 1 day:</span></span>  
  
    ```  
    exec dtasp_BackupAndPurgeTrackingDatabase 1, 0, 1, '\\MyBizTalkServer\backup', null, 0, 1  
    ```  
  
8.  <span data-ttu-id="b0616-139">在**作業屬性-DTA 清除與封存 (BizTalkDTADb)**對話方塊的 **選取頁面**，選取**一般**，選取**啟用**核取方塊，然後再選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="b0616-139">On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, select **General**, select the **Enabled** check box, and then select **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0616-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0616-140">See Also</span></span>  
 [<span data-ttu-id="b0616-141">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="b0616-141">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)
