---
title: 如何更新 BAM Analysis Server 和星狀結構描述資料庫名稱參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- restoring [BAM], Analysis database
- Analysis database [BAM], restoring
- restoring, BAM
- restoring [BAM], updating references
- BAM, restoring
- Analysis database [BAM], updating references
ms.assetid: cbe5e500-0a25-427e-bc76-1eae24b3e5f3
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4f98129efd2f7c027ecb6c3e69d494ff2e96e8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287446"
---
# <a name="how-to-update-references-to-the-bam-analysis-server-and-star-schema-database-names"></a><span data-ttu-id="ac8e9-102">如何更新 BAM Analysis Server 和星狀結構描述資料庫名稱的參考</span><span class="sxs-lookup"><span data-stu-id="ac8e9-102">How to Update References to the BAM Analysis Server and Star Schema Database Names</span></span>
<span data-ttu-id="ac8e9-103">如果您備份 BAMAnalysis 和 BAMStarSchema 資料庫，發生系統或資料失敗時可以將該備份還原至不同的電腦，您可以重新命名此備份。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-103">If you backed up your BAMAnalysis and BAMStarSchema databases, in the event of a system or data failure you can restore that backup to a different computer and you can rename the backup.</span></span>  
  
 <span data-ttu-id="ac8e9-104">若要還原 BAM Analysis Server 或 BAMStarSchema 資料庫，執行中的步驟[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-104">To restore the BAM Analysis Server or BAMStarSchema databases, perform the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span> <span data-ttu-id="ac8e9-105">此外，您必須以新的伺服器名稱和資料庫名稱來更新 BAM Data Transformation Services (DTS) 封裝。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-105">In addition, you must update the BAM Data Transformation Services (DTS) packages with the new server name and database name.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ac8e9-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="ac8e9-106">Prerequisites</span></span>  
 <span data-ttu-id="ac8e9-107">您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.</span></span>  
  
### <a name="to-update-references-to-the-bam-analysis-server-and-bam-star-schema-database-name-sql-server-2008-r2sp1"></a><span data-ttu-id="ac8e9-108">若要更新 BAM Analysis Server 和 BAM 星狀結構描述資料庫名稱 (SQL Server 2008 R2/SP1) 的參考</span><span class="sxs-lookup"><span data-stu-id="ac8e9-108">To update references to the BAM Analysis Server and BAM Star Schema database name (SQL Server 2008 R2/SP1)</span></span>  
  
1.  <span data-ttu-id="ac8e9-109">停止任何 BAM cube 更新及資料維護 SSIS 封裝，或防止它們執行，直到您還原 BAMAnalysis 或 BAMStarSchema 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-109">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAMAnalysis or BAMStarSchema databases.</span></span>  
  
2.  <span data-ttu-id="ac8e9-110">停止 BizTalk 應用程式服務 （其中包含 BAM 事件匯流排服務） 讓它不會嘗試將資料庫詳細資料匯入。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-110">Stop the BizTalk Application service (which includes the BAM Event Bus service) so it does not try to import more data into the databases.</span></span>  
  
    1.  <span data-ttu-id="ac8e9-111">按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-111">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="ac8e9-112">以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-112">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Stop**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="ac8e9-113">若要停止服務的另一種方式是使用**Net Stop**命令。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-113">Another way to stop a service is to use the **Net Stop** command.</span></span> <span data-ttu-id="ac8e9-114">若要停止使用 Net Stop 的 BizTalk 服務，請開啟**命令提示字元**(如果使用 Windows Server 2008 或 Windows Vista，啟動 命令提示字元使用**系統管理員身分執行**) 並輸入下列命令： `Net Stop BTSSvc$BizTalkServerApplication`然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-114">To stop the BizTalk service using Net Stop, open a **Command Prompt** (If using Windows Server 2008 or Windows Vista, start the Command Prompt using **Run As Administrator**) and type the following: `Net Stop BTSSvc$BizTalkServerApplication` then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="ac8e9-115">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Business Intelligence Development Studio**.</span><span class="sxs-lookup"><span data-stu-id="ac8e9-115">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Business Intelligence Development Studio**.</span></span>  
  
4.  <span data-ttu-id="ac8e9-116">在 SQL Server Business Intelligence Development Studio 中建立新專案。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-116">In SQL Server Business Intelligence Development Studio, create a new project.</span></span> <span data-ttu-id="ac8e9-117">按一下**檔案**，按一下 **新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-117">Click **File**, click **New**, and then click **Project**.</span></span>  
  
5.  <span data-ttu-id="ac8e9-118">中**新專案**對話方塊中，於**範本**，按一下**Integration Services 專案**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-118">In the **New Project** dialog box, in **Templates**, click **Integration Services Project**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="ac8e9-119">在**Integration Services 專案**對話方塊中，於**方案總管] 中**，以滑鼠右鍵按一下**SSIS 封裝**，然後按一下 [**加入現有封裝**.</span><span class="sxs-lookup"><span data-stu-id="ac8e9-119">In the **Integration Services Project** dialog box, in **Solution Explorer**, right-click **SSIS Packages**, and then click **Add Existing Package**.</span></span>  
  
7.  <span data-ttu-id="ac8e9-120">在**加入現有封裝的副本**對話方塊中，於**伺服器**下拉式清單方塊中，選取包含 BAM_AN 封裝的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-120">In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_AN package.</span></span>  
  
8.  <span data-ttu-id="ac8e9-121">在**封裝路徑**，按一下省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-121">In **Package Path**, click the ellipses button.</span></span>  
  
9. <span data-ttu-id="ac8e9-122">中**SSIS 封裝**對話方塊方塊中，選取 BAM_AN 封裝，按一下**確定**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-122">In the **SSIS Package** dialog box, select the BAM_AN package, click **OK**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ac8e9-123">封裝現在會在 [方案總管] 中列出。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-123">The package is now listed in Solution Explorer.</span></span>  
  
10. <span data-ttu-id="ac8e9-124">在**方案總管 中**，按兩下 BAM_AN 封裝。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-124">In **Solution Explorer**, double-click the BAM_AN package.</span></span> <span data-ttu-id="ac8e9-125">在**連接管理員**，請按兩下資料庫數字 3 （MSDB 資料庫）。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-125">In **Connection Managers**, double-click database number 3 (MSDB database).</span></span>  
  
11. <span data-ttu-id="ac8e9-126">在**連線管理員**對話方塊中，於**伺服器名稱**方塊中，輸入 MSDB 伺服器的名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-126">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the MSDB server, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="ac8e9-127">按一下**封裝總管**索引標籤上，按兩下**變數**資料夾，然後再更新主要匯入伺服器名稱及主要的值匯入資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-127">Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the primary import server name and primary import database name.</span></span>  
  
13. <span data-ttu-id="ac8e9-128">按一下**檔案**，然後按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-128">Click **File**, and then click **Save All**.</span></span>  
  
14. <span data-ttu-id="ac8e9-129">在**Microsoft SQL Server Management Studio**，按一下 **連接**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-129">In **Microsoft SQL Server Management Studio**, click **Connect**.</span></span>  
  
15. <span data-ttu-id="ac8e9-130">按一下**Integration Services**，連按兩下**存放的封裝**，按一下  **MSDB**BAM_AN 封裝，以滑鼠右鍵按一下，然後按**匯入封裝**.</span><span class="sxs-lookup"><span data-stu-id="ac8e9-130">Click **Integration Services**, double-click **Stored Packages**, click **MSDB**, right-click the BAM_AN package, and then click **Import Package**.</span></span>  
  
16. <span data-ttu-id="ac8e9-131">在**匯入封裝**對話方塊中，於**封裝位置**，選取**檔案系統**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-131">In the **Import Package** dialog box, in **Package location**, select **File System**.</span></span>  
  
17. <span data-ttu-id="ac8e9-132">在**封裝路徑**、 瀏覽至您儲存的專案中，選取 BAM_AN\*.dtsx 檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-132">In **Package Path**, navigate to your saved project, select the BAM_AN\*.dtsx file, and then click **Open**.</span></span>  
  
18. <span data-ttu-id="ac8e9-133">在按一下**封裝名稱**方塊，以自動填入方塊。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-133">Click inside the **Package Name** box to automatically populate the box.</span></span>  
  
19. <span data-ttu-id="ac8e9-134">按一下**確定**，然後按一下 **是**覆寫。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-134">Click **OK**, and then click **Yes** to overwrite.</span></span>  
  
20. <span data-ttu-id="ac8e9-135">重新啟動 BizTalk 應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-135">Restart the BizTalk Application service.</span></span>  
  
    1.  <span data-ttu-id="ac8e9-136">按一下**啟動**，按一下 **執行**，然後輸入**services.msc**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-136">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="ac8e9-137">以滑鼠右鍵按一下**BizTalk Service BizTalk Group: BizTalkServerApplication**服務，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-137">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Start**.</span></span>  
  
21. <span data-ttu-id="ac8e9-138">啟用任何 BAM Cube 更新和資料維護 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="ac8e9-138">Enable any BAM cube update and data maintenance SSIS packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8e9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac8e9-139">See Also</span></span>  
 [<span data-ttu-id="ac8e9-140">備份和還原 BAM</span><span class="sxs-lookup"><span data-stu-id="ac8e9-140">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)