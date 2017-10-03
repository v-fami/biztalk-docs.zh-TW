---
title: "如何設定 DTA 的清除與封存工作 |Microsoft 文件"
ms.custom: 
ms.date: 2015-11-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- purging, configuring
- DTA Purge and Archive job, configuring
- archiving [Tracking database], DTA Purge and Archive job
- archiving [Tracking database], configuring
- purging, DTA Purge and Archive job
ms.assetid: 156ccf9b-284f-4b96-a395-92936e8cebcf
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f4985e657f26945aa2fdc168b273dbfdb159efc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-dta-purge-and-archive-job"></a><span data-ttu-id="6715b-102">如何設定 DTA 的清除與封存工作</span><span class="sxs-lookup"><span data-stu-id="6715b-102">How to Configure the DTA Purge and Archive Job</span></span>
<span data-ttu-id="6715b-103">您必須先設定 DTA 的清除與封存 (BizTalkDTADb) 工作，才能封存或清除「BizTalk 追蹤」(BizTalkDTADb) 資料庫的資料。</span><span class="sxs-lookup"><span data-stu-id="6715b-103">Before you can archive or purge data from the BizTalk Tracking (BizTalkDTADb) database, you must configure the DTA Purge and Archive (BizTalkDTADb) job.</span></span> <span data-ttu-id="6715b-104">這項作業會設定為呼叫 dtasp_BackupAndPurgeTrackingDatabase 預存程序，它會使用六個參數，您必須設定。</span><span class="sxs-lookup"><span data-stu-id="6715b-104">This job is configured to call the dtasp_BackupAndPurgeTrackingDatabase store procedure, which uses six parameters you must configure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6715b-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="6715b-105">Prerequisites</span></span>  
 <span data-ttu-id="6715b-106">您必須是 SQL Server sysadmin 固定伺服器角色的成員，才能依照這些步驟的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="6715b-106">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to follow these steps.</span></span>  
  
### <a name="to-configure-the-dta-purge-and-archive-job"></a><span data-ttu-id="6715b-107">若要設定 DTA 的清除與封存工作</span><span class="sxs-lookup"><span data-stu-id="6715b-107">To configure the DTA purge and archive job</span></span>  
  
1.  <span data-ttu-id="6715b-108">在裝載 「 BizTalk 追蹤 (BizTalkDTADb) 資料庫的 SQL Server 上開啟**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="6715b-108">On the SQL Server that hosts the BizTalk Tracking (BizTalkDTADb) database, open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="6715b-109">在**連接到伺服器**，輸入 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL server 的名稱、 輸入驗證類型，然後選取**連接**連接到 SQL server。</span><span class="sxs-lookup"><span data-stu-id="6715b-109">In **Connect to Server**, enter the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides, enter the authentication type, and then select **Connect** to connect to the SQL server.</span></span>  
  
3.  <span data-ttu-id="6715b-110">在**Microsoft SQL Server Management Studio**，連按兩下**SQL Server Agent**，然後按一下 **作業**。</span><span class="sxs-lookup"><span data-stu-id="6715b-110">In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.</span></span>  
  
4.  <span data-ttu-id="6715b-111">在**物件總管詳細資料**] 窗格中，以滑鼠右鍵按一下**DTA 清除與封存 (BizTalkDTADb)**，然後按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6715b-111">In the **Object Explorer Details** pane, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="6715b-112">在**作業屬性-DTA 清除與封存 (BizTalkDTADb)**對話方塊的 **選取頁面**，按一下 **步驟**。</span><span class="sxs-lookup"><span data-stu-id="6715b-112">In the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **Steps**.</span></span>  
  
6.  <span data-ttu-id="6715b-113">在**作業步驟清單**，按一下 **封存及清除**，然後按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="6715b-113">In the **Job step list**, click **Archive and Purge**, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="6715b-114">在**一般**頁面上，於**命令**方塊中，編輯適當的下列參數，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6715b-114">On the **General** page, in the **Command** box, edit the following parameters as appropriate, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="6715b-115">@nLiveHourstinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。</span><span class="sxs-lookup"><span data-stu-id="6715b-115">@nLiveHours tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="6715b-116">這是必要的參數沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="6715b-116">This is a required parameter with no default value.</span></span>  
  
    -   <span data-ttu-id="6715b-117">@nLiveDaystinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。</span><span class="sxs-lookup"><span data-stu-id="6715b-117">@nLiveDays tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="6715b-118">預設間隔為 0 天。</span><span class="sxs-lookup"><span data-stu-id="6715b-118">Default interval is 0 days.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6715b-119">基於 BizTalk 追蹤 (BizTalkDTADb) 資料庫的目的，LiveHours 加上 LiveDays 的總和是您要在 BizTalk Server 環境中維持的資料存留窗期。</span><span class="sxs-lookup"><span data-stu-id="6715b-119">For the purposes of the BizTalk Tracking (BizTalkDTADb) database, the sum of LiveHours plus LiveDays is the live window of data you want to maintain in your BizTalk Server environment.</span></span> <span data-ttu-id="6715b-120">存留時間超過資料存留窗期之已完成執行個體的所有相關資料都會被刪除。</span><span class="sxs-lookup"><span data-stu-id="6715b-120">All data associated with a completed instance older than the live window of data is deleted.</span></span>  
  
    -   <span data-ttu-id="6715b-121">@nHardDeleteDaystinyint — 所有資料 （即使未完成） 早於這將會被刪除。</span><span class="sxs-lookup"><span data-stu-id="6715b-121">@nHardDeleteDays tinyint — All data (even if incomplete) older than this will be deleted.</span></span> <span data-ttu-id="6715b-122">為 HardDeleteDays 指定的時間間隔應該大於資料存留窗期。</span><span class="sxs-lookup"><span data-stu-id="6715b-122">The time interval specified for HardDeleteDays should be greater than the live window of data.</span></span> <span data-ttu-id="6715b-123">資料存留窗期是您想要在 BizTalk 追蹤 (BizTalkDTADb) 資料庫中維護追蹤資料的時間。</span><span class="sxs-lookup"><span data-stu-id="6715b-123">The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="6715b-124">早於此間隔的資料都將在下次封存時進行封存，然後再予以清除。</span><span class="sxs-lookup"><span data-stu-id="6715b-124">Anything older than this interval is eligible to be archived at the next archive and then purged.</span></span> <span data-ttu-id="6715b-125">預設值為 0 天。</span><span class="sxs-lookup"><span data-stu-id="6715b-125">Default is 0 days.</span></span>  
  
    -   <span data-ttu-id="6715b-126">@nvcFoldernvarchar （1024) — 放置備份檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6715b-126">@nvcFolder nvarchar(1024) — Folder in which to put the backup files.</span></span> <span data-ttu-id="6715b-127">這是必要的參數沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="6715b-127">This is a required parameter with no default value.</span></span>  
  
    -   <span data-ttu-id="6715b-128">@nvcValidatingServersysname — 將完成驗證的伺服器。</span><span class="sxs-lookup"><span data-stu-id="6715b-128">@nvcValidatingServer sysname — Server on which validation will be done.</span></span> <span data-ttu-id="6715b-129">NULL 值表示沒有完成任何驗證。</span><span class="sxs-lookup"><span data-stu-id="6715b-129">NULL value indicates no validation is being done.</span></span> <span data-ttu-id="6715b-130">預設值是 NULL。</span><span class="sxs-lookup"><span data-stu-id="6715b-130">Default is NULL.</span></span>  
  
    -   <span data-ttu-id="6715b-131">@fForceBackupint — 預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="6715b-131">@fForceBackup int — Default is 0.</span></span> <span data-ttu-id="6715b-132">這被保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="6715b-132">This is reserved for future use.</span></span>  
  
     <span data-ttu-id="6715b-133">編輯後的命令看起來應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="6715b-133">The edited command should look similar to the following.</span></span> <span data-ttu-id="6715b-134">在下列範例中，還有 1 小時的即時視窗和硬清除 1 天：</span><span class="sxs-lookup"><span data-stu-id="6715b-134">In the following example, there is a live window of 1 hour and a hard purge of 1 day:</span></span>  
  
    ```  
    exec dtasp_BackupAndPurgeTrackingDatabase 1, 0, 1, '\\MyBizTalkServer\backup', null, 0  
    ```  
  
8.  <span data-ttu-id="6715b-135">在**作業屬性-DTA 清除與封存 (BizTalkDTADb)**對話方塊的 **選取頁面**，按一下 **一般**，選取**啟用**核取方塊，然後**確定**。</span><span class="sxs-lookup"><span data-stu-id="6715b-135">On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **General**, select the **Enabled** check box, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6715b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6715b-136">See Also</span></span>  
 [<span data-ttu-id="6715b-137">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="6715b-137">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)