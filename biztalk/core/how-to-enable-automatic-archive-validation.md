---
title: 如何啟用自動封存驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- validating, archives [Tracking database]
- archiving [Tracking database], validating archive
ms.assetid: 406ca54a-6b1f-4bdb-9bad-bea5ea0f6e66
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed636b1d733589b646ef170a8038a25b05d94cab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023868"
---
# <a name="how-to-enable-automatic-archive-validation"></a><span data-ttu-id="ff121-102">如何啟用自動封存驗證</span><span class="sxs-lookup"><span data-stu-id="ff121-102">How to Enable Automatic Archive Validation</span></span>
<span data-ttu-id="ff121-103">封存驗證讓您可以在封存建立時驗證封存。</span><span class="sxs-lookup"><span data-stu-id="ff121-103">Archive validation enables you to validate the archives as they are created.</span></span> <span data-ttu-id="ff121-104">在您可以啟用自動封存驗證前，必須先設定次要資料庫伺服器，也稱為驗證伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff121-104">Before you can enable automatic archive validation, you must set up a secondary database server, also called a validation server.</span></span> <span data-ttu-id="ff121-105">因為封存程序是簡單備份，所以儲存在磁碟上的實際影像可能由於硬體問題而毀損。</span><span class="sxs-lookup"><span data-stu-id="ff121-105">Because the archiving process is a simple backup, it is possible that the actual image stored on the disk can be corrupted due to a hardware issue.</span></span>  
  
 <span data-ttu-id="ff121-106">您可以使用封存驗證功能，確保封存 (備份) 已成功，而且可以還原。</span><span class="sxs-lookup"><span data-stu-id="ff121-106">Using the archive validation feature, you can ensure the archive (backup) was successful and can be restored.</span></span> <span data-ttu-id="ff121-107">建立封存之後，會通知驗證伺服器已經建立新的封存。</span><span class="sxs-lookup"><span data-stu-id="ff121-107">After an archive is created, the validation server is notified that a new archive has been created.</span></span> <span data-ttu-id="ff121-108">驗證伺服器會嘗試還原封存。</span><span class="sxs-lookup"><span data-stu-id="ff121-108">The validation server attempts to restore the archive.</span></span> <span data-ttu-id="ff121-109">驗證伺服器必須是另一個執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]不同於用來執行作業。</span><span class="sxs-lookup"><span data-stu-id="ff121-109">A validation server must be another instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] different from the one in which the job is running.</span></span> <span data-ttu-id="ff121-110">新版[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]驗證伺服器必須是相同的版本[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可用來主控資料庫。</span><span class="sxs-lookup"><span data-stu-id="ff121-110">The version of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] on the validation server must be the same version as the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] used to host the databases.</span></span>  
  
 <span data-ttu-id="ff121-111">若還原成功，則驗證伺服器會將此資訊傳回到 [BizTalk 追蹤] \(BizTalkDTADb) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ff121-111">If the restore is successful, the validation server communicates this information back to the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="ff121-112">在成功完成還原之前，清除工作不會再清除任何其他資料。</span><span class="sxs-lookup"><span data-stu-id="ff121-112">Until a successful restore is completed, the purge job will not purge any more data.</span></span>  
  
 <span data-ttu-id="ff121-113">若還原不成功，則驗證伺服器會將此資訊傳回到 [BizTalk 追蹤] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ff121-113">If the restore is not successful, the validation server communicates this information back to the BizTalk Tracking database.</span></span> <span data-ttu-id="ff121-114">清除工作會建立另一個封存，然後等待驗證新封存。</span><span class="sxs-lookup"><span data-stu-id="ff121-114">The purge job creates another archive and awaits validation of the new archive.</span></span> <span data-ttu-id="ff121-115">如此可避免毀損的封存造成追蹤資料遺失的可能性。</span><span class="sxs-lookup"><span data-stu-id="ff121-115">This prevents the possibility of a corrupted archive causing you to lose tracking data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ff121-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="ff121-116">Prerequisites</span></span>  
 <span data-ttu-id="ff121-117">您必須以成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="ff121-117">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-enable-automatic-archive-validation"></a><span data-ttu-id="ff121-118">若要啟用自動封存驗證</span><span class="sxs-lookup"><span data-stu-id="ff121-118">To enable automatic archive validation</span></span>  
  
1. <span data-ttu-id="ff121-119">在驗證伺服器上，按一下**開始**，按一下**所有程式**，按一下  **Microsoft SQL Server 2008 SP2**，然後按一下  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="ff121-119">On the validation server, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.</span></span>  
  
2. <span data-ttu-id="ff121-120">在 **連接到伺服器**對話方塊方塊中，指定的名稱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]您可以在其中執行還原程序測試來驗證封存，然後按一下**Connect**連接到適當的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ff121-120">In the **Connect to Server** dialog box, specify the name of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] where you can validate the archive by performing a test of the restore process, and then click **Connect** to connect to the appropriate SQL Server.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="ff121-121">此伺服器不應另一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫伺服器，因為它會降低系統效能，驗證封存時。</span><span class="sxs-lookup"><span data-stu-id="ff121-121">This server should not be another [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database server as it reduces system performance when validating the archive.</span></span>  
  
3. <span data-ttu-id="ff121-122">在  **Microsoft SQL Server Management Studio**，按一下**檔案**，按一下 **開啟**，然後按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="ff121-122">In **Microsoft SQL Server Management Studio**, click **File**, click **Open**, and then click **File**.</span></span>  
  
4. <span data-ttu-id="ff121-123">在 [**開啟檔案**] 對話方塊中，瀏覽至下列 SQL 指令碼：</span><span class="sxs-lookup"><span data-stu-id="ff121-123">In the **Open File** dialog box, browse to the following SQL script:</span></span>  
  
   ```  
   %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\BTS_Tracking_ValidateArchive.sql  
   ```  
  
   > [!NOTE]
   >  <span data-ttu-id="ff121-124">您可能需要從執行的電腦複製指令碼[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來驗證伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff121-124">You might need to copy the script from the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the validation server.</span></span>  
  
5. <span data-ttu-id="ff121-125">按一下 **查詢**功能表，然後再按一下**Execute**。</span><span class="sxs-lookup"><span data-stu-id="ff121-125">Click the **Query** menu, and then click **Execute**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="ff121-126">只有在用於封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫的資料夾為網路共用時，BTS_Tracking_ValidateArchive.sql 指令碼才能運作。</span><span class="sxs-lookup"><span data-stu-id="ff121-126">The BTS_Tracking_ValidateArchive.sql script only works if the folder where you are archiving your BizTalk Tracking (BizTalkDTADb) database is a network share.</span></span>  
  
    <span data-ttu-id="ff121-127">BTS_Tracking_ValidateArchive.sql 指令碼會建立稱為 ValidateArchive 的 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="ff121-127">The BTS_Tracking_ValidateArchive.sql script creates a SQL Server Agent job called ValidateArchive.</span></span>  
  
6. <span data-ttu-id="ff121-128">因為封存與清除程序可能會存取並 (或) 更新不同 SQL Server 中的資料庫，所以您必須在相關 SQL Server 執行個體之間設定連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff121-128">The archiving and purging process potentially accesses and/or updates databases in different SQL Servers, so you must set up linked servers between the involved SQL Server instances.</span></span> <span data-ttu-id="ff121-129">在  **SQL Server Management Studio**，按兩下**Server 物件**，以滑鼠右鍵按一下**連結的伺服器**，然後按一下 **新增連結的伺服器**.</span><span class="sxs-lookup"><span data-stu-id="ff121-129">In **SQL Server Management Studio**, double-click **Server Objects**, right-click **Linked Servers**, and then click **New Linked Server**.</span></span>  
  
    <span data-ttu-id="ff121-130">您必須設定下列各項之間的連結伺服器：</span><span class="sxs-lookup"><span data-stu-id="ff121-130">You must set up linked server between:</span></span>  
  
   -   <span data-ttu-id="ff121-131">每一個 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫與 BizTalk 追蹤 (BizTalkDTADb) 資料庫 (如果兩者位於不同的伺服器)。</span><span class="sxs-lookup"><span data-stu-id="ff121-131">Each of your BizTalk MessageBox (BizTalkMsgBoxDb) databases and the BizTalk Tracking (BizTalkDTADb) database if they reside on different servers.</span></span>  
  
   -   <span data-ttu-id="ff121-132">[BizTalk 追蹤] \(BizTalkDTADb) 資料庫與封存驗證的驗證伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff121-132">The BizTalk Tracking (BizTalkDTADb) database and the validating server for archive validation.</span></span>  
  
   -   <span data-ttu-id="ff121-133">在裝載 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫的電腦上，SQL Server 代理程式的服務帳戶必須對連結伺服器上的 BizTalk 追蹤 (BizTalkDTADb) 資料庫擁有 db_datareader 和 db_datawriter 權限。</span><span class="sxs-lookup"><span data-stu-id="ff121-133">The service accounts for the SQL Server Agent on the computer hosting the BizTalk MessageBox (BizTalkMsgBoxDb) database must have the db_datareader and db_datawriter permissions for the BizTalk Tracking (BizTalkDTADb) database on the linked server.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="ff121-134">用來執行工作的帳戶應該同時擁有兩個資料庫的 [資料庫操作員] \(DBO) 權限。</span><span class="sxs-lookup"><span data-stu-id="ff121-134">The account used for running the job should have Database Operator (DBO) privileges on both the databases.</span></span>  
  
7. <span data-ttu-id="ff121-135">在 **新增連結的伺服器**對話方塊的 **一般**頁面上，於**連結的伺服器**，輸入您想要連結至伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff121-135">In the **New Linked Server** dialog box, on the **General** page, in **Linked server**, enter the name of the server you want to link to.</span></span>  
  
    <span data-ttu-id="ff121-136">例如，裝載 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫、BizTalk 追蹤 (BizTalkDTADb) 資料庫或驗證伺服器的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff121-136">For example, the server hosting the BizTalk MessageBox (BizTalkMsgBoxDb) database, BizTalk Tracking (BizTalkDTADb) database, or the validation server.</span></span>  
  
8. <span data-ttu-id="ff121-137">底下**伺服器類型**，按一下**SQL Server**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ff121-137">Under **Server type**, click **SQL Server**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="ff121-138">在  **Microsoft SQL Server Management Studio**，按兩下**SQL Server Agent**，然後按一下 **工作**。</span><span class="sxs-lookup"><span data-stu-id="ff121-138">In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.</span></span>  
  
10. <span data-ttu-id="ff121-139">在 **物件總管詳細資料**窗格中，以滑鼠右鍵按一下**ValidateArchive**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ff121-139">In the **Object Explorer Details** pane, right-click **ValidateArchive**, and then click **Properties**.</span></span>  
  
11. <span data-ttu-id="ff121-140">在 **作業屬性-validatearchive**對話方塊的 **選取頁面**，按一下 **步驟**。</span><span class="sxs-lookup"><span data-stu-id="ff121-140">In the **Job Properties - ValidateArchive** dialog box, under **Select a page**, click **Steps**.</span></span>  
  
12. <span data-ttu-id="ff121-141">在 **作業步驟清單**，按一下**驗證**，然後按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="ff121-141">In the **Job step list**, click **validate**, and then click **Edit**.</span></span>  
  
13. <span data-ttu-id="ff121-142">在 **一般**頁面上，於**命令**方塊中的，在命令中， **exec dtasp_ValidateArchive null，null**，取代 null，null 與裝載 BizTalk 伺服器的名稱追蹤資料庫中，括住的單一括住，後面加上 BizTalk 追蹤資料庫，以引號括住的名稱，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ff121-142">On the **General** page, in the **Command** box, in the command, **exec dtasp_ValidateArchive null, null**, replace null, null with the name of the server hosting the BizTalk Tracking database, surrounded by single quotes, followed by the name of the BizTalk Tracking database, surrounded by quotes, and then click **OK**.</span></span> <span data-ttu-id="ff121-143">例如：</span><span class="sxs-lookup"><span data-stu-id="ff121-143">For example:</span></span>  
  
     <span data-ttu-id="ff121-144">**exec dtasp_ValidateArchive '** *\<TrackingServerName\>* **'、'**  *\<TrackingDatabaseName\>* **'**</span><span class="sxs-lookup"><span data-stu-id="ff121-144">**exec dtasp_ValidateArchive '** *\<TrackingServerName\>* **', '** *\<TrackingDatabaseName\>* **'**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff121-145">[ValidateArchive] 作業沒有排程，您不可設定它的排程。</span><span class="sxs-lookup"><span data-stu-id="ff121-145">The ValidateArchive job does not have a schedule and you should not configure a schedule for it.</span></span> <span data-ttu-id="ff121-146">而是由 [DTA 清除和封存] \(BizTalkDTADb) 作業在建立封存時自動啟動此作業。</span><span class="sxs-lookup"><span data-stu-id="ff121-146">Instead, the DTA Purge and Archive (BizTalkDTADb) job starts this job automatically when an archive is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff121-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff121-147">See Also</span></span>  
 [<span data-ttu-id="ff121-148">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="ff121-148">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)