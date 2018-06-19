---
title: 如何更新 BAM 封存資料庫名稱的參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Archive database [BAM], restoring
- restoring, BAM
- restoring [BAM], Archive database
- restoring [BAM], updating references
- Archive database [BAM], updating references
- BAM, restoring
ms.assetid: a0b8543e-6fc1-412e-b74e-683352d9c49e
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0df87a548c2a6a5a207673d96a984e16287f04a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256414"
---
# <a name="how-to-update-references-to-the-bam-archive-database-name"></a><span data-ttu-id="10433-102">如何更新 BAM 封存資料庫名稱的參考</span><span class="sxs-lookup"><span data-stu-id="10433-102">How to Update References to the BAM Archive Database Name</span></span>
<span data-ttu-id="10433-103">如果您備份 BAMArchive 資料庫時，發生系統或資料失敗時可以將該備份還原，並將它重新命名。</span><span class="sxs-lookup"><span data-stu-id="10433-103">If you backed up your BAMArchive databases, in the event of a system or data failure you can restore that backup and rename it.</span></span>  
  
 <span data-ttu-id="10433-104">若要還原 BAMArchive 資料庫，執行中的步驟[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="10433-104">To restore the BAMArchive databases, perform the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span> <span data-ttu-id="10433-105">此外，您也必須執行下列一般步驟，各步驟之後都有詳細說明步驟的程序：</span><span class="sxs-lookup"><span data-stu-id="10433-105">In addition, you must perform these general steps, which are followed by a procedure that describes the steps in detail:</span></span>  
  
-   <span data-ttu-id="10433-106">以新的伺服器名稱和資料庫名稱更新 BAM DTS 封裝。</span><span class="sxs-lookup"><span data-stu-id="10433-106">Update the BAM DTS packages with the new server name and database name.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="10433-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="10433-107">Prerequisites</span></span>  
 <span data-ttu-id="10433-108">您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="10433-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.</span></span>  
  
### <a name="to-update-references-to-the-bam-archive-database-name-sql-server-2008-r2sp1"></a><span data-ttu-id="10433-109">若要更新 BAM 封存資料庫名稱 (SQL Server 2008 R2/SP1) 的參考</span><span class="sxs-lookup"><span data-stu-id="10433-109">To update references to the BAM Archive database name (SQL Server 2008 R2/SP1)</span></span>  
  
1.  <span data-ttu-id="10433-110">停止任何 BAM cube 更新及資料維護 DTS 封裝，或防止它們執行，直到您還原 BAMArchive 資料庫。</span><span class="sxs-lookup"><span data-stu-id="10433-110">Stop any BAM cube update and data maintenance DTS packages, or prevent them from running until you have restored the BAMArchive database.</span></span>  
  
2.  <span data-ttu-id="10433-111">停止 BizTalk 應用程式服務 (包括 BAM 事件匯流排服務)，以避免其嘗試將更多資料匯入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="10433-111">Stop the BizTalk Application service (which includes the BAM Event Bus service) so it does not try to import more data into the database.</span></span>  
  
    1.  <span data-ttu-id="10433-112">按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。</span><span class="sxs-lookup"><span data-stu-id="10433-112">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="10433-113">以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="10433-113">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Stop**.</span></span>  
  
3.  <span data-ttu-id="10433-114">按一下**啟動**，按一下 **程式**，按一下  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Business Intelligence Development Studio**.</span><span class="sxs-lookup"><span data-stu-id="10433-114">Click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Business Intelligence Development Studio**.</span></span>  
  
4.  <span data-ttu-id="10433-115">在 SQL Server Business Intelligence Development Studio 中建立新專案。</span><span class="sxs-lookup"><span data-stu-id="10433-115">In SQL Server Business Intelligence Development Studio, create a new project.</span></span> <span data-ttu-id="10433-116">按一下**檔案**，按一下 **新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="10433-116">Click **File**, click **New**, and then click **Project**.</span></span>  
  
5.  <span data-ttu-id="10433-117">中**新專案**對話方塊中，於**範本**，按一下**Integration Services 專案**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="10433-117">In the **New Project** dialog box, in **Templates**, click **Integration Services Project**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="10433-118">在**Integration Services 專案**對話方塊中，於**方案總管] 中**，以滑鼠右鍵按一下**SSIS 封裝**，然後按一下 [**加入現有封裝**.</span><span class="sxs-lookup"><span data-stu-id="10433-118">In the **Integration Services Project** dialog box, in **Solution Explorer**, right-click **SSIS Packages**, and then click **Add Existing Package**.</span></span>  
  
7.  <span data-ttu-id="10433-119">在**加入現有封裝的副本**對話方塊中，於**伺服器**下拉式清單方塊中，選取包含 BAM_DM 封裝的伺服器。</span><span class="sxs-lookup"><span data-stu-id="10433-119">In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_DM package.</span></span>  
  
8.  <span data-ttu-id="10433-120">在**封裝路徑**，按一下省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="10433-120">In **Package Path**, click the ellipses button.</span></span>  
  
9. <span data-ttu-id="10433-121">在**SSIS 封裝**對話方塊方塊中，選取 BAM_DM 封裝，按一下**確定**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="10433-121">In the **SSIS Package** dialog box, select the BAM_DM package, click **OK**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="10433-122">封裝現在會在 [方案總管] 中列出。</span><span class="sxs-lookup"><span data-stu-id="10433-122">The package is now listed in Solution Explorer.</span></span>  
  
10. <span data-ttu-id="10433-123">在**方案總管 中**，按兩下 BAM_DM 封裝。</span><span class="sxs-lookup"><span data-stu-id="10433-123">In **Solution Explorer**, double-click the BAM_DM package.</span></span> <span data-ttu-id="10433-124">在**連接管理員**，請按兩下資料庫數字 3 （MSDB 資料庫）。</span><span class="sxs-lookup"><span data-stu-id="10433-124">In **Connection Managers**, double-click database number 3 (MSDB database).</span></span>  
  
11. <span data-ttu-id="10433-125">在**連線管理員**對話方塊中，於**伺服器名稱**方塊中，輸入 MSDB 伺服器的名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="10433-125">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the MSDB server, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="10433-126">按一下**封裝總管**索引標籤上，按兩下**變數**資料夾，然後再更新主要匯入伺服器名稱及主要的值匯入資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="10433-126">Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the primary import server name and primary import database name.</span></span>  
  
13. <span data-ttu-id="10433-127">按一下**檔案**，然後按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="10433-127">Click **File**, and then click **Save All**.</span></span>  
  
14. <span data-ttu-id="10433-128">在**Microsoft SQL Server Management Studio**，按一下 **連接**。</span><span class="sxs-lookup"><span data-stu-id="10433-128">In **Microsoft SQL Server Management Studio**, click **Connect**.</span></span>  
  
15. <span data-ttu-id="10433-129">按一下**Integration Services**，連按兩下**存放的封裝**，按一下  **MSDB**BAM_DM 封裝，以滑鼠右鍵按一下，然後按**匯入封裝**.</span><span class="sxs-lookup"><span data-stu-id="10433-129">Click **Integration Services**, double-click **Stored Packages**, click **MSDB**, right-click the BAM_DM package, and then click **Import Package**.</span></span>  
  
16. <span data-ttu-id="10433-130">在**匯入封裝**對話方塊中，於**封裝位置**，選取**檔案系統**。</span><span class="sxs-lookup"><span data-stu-id="10433-130">In the **Import Package** dialog box, in **Package location**, select **File System**.</span></span>  
  
17. <span data-ttu-id="10433-131">在**封裝路徑**、 瀏覽至您儲存的專案中，選取 BAM_DM\*.dtsx 檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="10433-131">In **Package Path**, navigate to your saved project, select the BAM_DM\*.dtsx file, and then click **Open**.</span></span>  
  
18. <span data-ttu-id="10433-132">在按一下**封裝名稱**方塊，以自動填入方塊。</span><span class="sxs-lookup"><span data-stu-id="10433-132">Click inside the **Package Name** box to automatically populate the box.</span></span>  
  
19. <span data-ttu-id="10433-133">按一下**確定**，然後按一下 **是**覆寫。</span><span class="sxs-lookup"><span data-stu-id="10433-133">Click **OK**, and then click **Yes** to overwrite.</span></span>  
  
20. <span data-ttu-id="10433-134">重新啟動 BizTalk 應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="10433-134">Restart the BizTalk Application service.</span></span>  
  
    1.  <span data-ttu-id="10433-135">按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。</span><span class="sxs-lookup"><span data-stu-id="10433-135">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="10433-136">以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="10433-136">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Start**.</span></span>  
  
21. <span data-ttu-id="10433-137">啟用任何 BAM Cube 更新和資料維護 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="10433-137">Enable any BAM cube update and data maintenance SSIS packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10433-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10433-138">See Also</span></span>  
 [<span data-ttu-id="10433-139">備份和還原 BAM</span><span class="sxs-lookup"><span data-stu-id="10433-139">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)