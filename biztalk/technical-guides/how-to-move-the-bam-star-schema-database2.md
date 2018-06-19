---
title: 如何移動 BAM 星狀結構描述 Database2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6832ac2-c8c5-4515-883e-26d125d6ace0
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d74e49cc1504547bff80bd2688383f1f6bea053c
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "26010567"
---
# <a name="how-to-move-the-bam-star-schema-database"></a><span data-ttu-id="032c1-102">如何移動 BAM 星狀結構描述資料庫</span><span class="sxs-lookup"><span data-stu-id="032c1-102">How to Move the BAM Star Schema Database</span></span>
<span data-ttu-id="032c1-103">您可以使用這個程序將「BAM 星狀結構描述」資料庫移動到其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="032c1-103">You can use this procedure to move the BAM Star Schema database to another server.</span></span>  <span data-ttu-id="032c1-104">端對端案例的觀點而言，移動 BAM 星狀結構描述資料庫包含兩個主要步驟：</span><span class="sxs-lookup"><span data-stu-id="032c1-104">From an end-to-end scenario perspective, moving the BAM Star Schema database involves two major steps:</span></span>  
  
-   [<span data-ttu-id="032c1-105">移動 BAM 星狀結構描述資料庫</span><span class="sxs-lookup"><span data-stu-id="032c1-105">Moving the BAM Star Schema Database</span></span>](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarMoveDB)  
  
-   [<span data-ttu-id="032c1-106">更新至新的 BAM 星狀結構描述資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="032c1-106">Updating References to the New BAM Star Schema Database</span></span>](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate)  
  
## <a name="prerequisites"></a><span data-ttu-id="032c1-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="032c1-107">Prerequisites</span></span>  
 <span data-ttu-id="032c1-108">您必須以成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="032c1-108">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
##  <a name="BKMK_StarMoveDB"></a> <span data-ttu-id="032c1-109">移動 BAM 星狀結構描述資料庫</span><span class="sxs-lookup"><span data-stu-id="032c1-109">Moving the BAM Star Schema Database</span></span>  
 <span data-ttu-id="032c1-110">移動 BAM 星狀結構描述資料庫的下列程序中執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="032c1-110">Perform the steps in the following procedure to move the BAM Star Schema database.</span></span>  
  
#### <a name="to-move-the-bam-star-schema-database"></a><span data-ttu-id="032c1-111">移動 BAM 星狀結構描述資料庫</span><span class="sxs-lookup"><span data-stu-id="032c1-111">To move the BAM Star Schema database</span></span>  
  
1.  <span data-ttu-id="032c1-112">在還原 BAM 星狀結構描述資料庫之前，必須停止所有 BAM Cube 更新和資料維護 SSIS 封裝，或不允許封裝執行。</span><span class="sxs-lookup"><span data-stu-id="032c1-112">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Star Schema database.</span></span>  
  
2.  <span data-ttu-id="032c1-113">停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="032c1-113">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="032c1-114">如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](http://go.microsoft.com/fwlink/?LinkId=154394)(http://go.microsoft.com/fwlink/?LinkId=154394)中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="032c1-114">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
3.  <span data-ttu-id="032c1-115">停止 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="032c1-115">Stop the IIS service.</span></span>  
  
4.  <span data-ttu-id="032c1-116">停止 BAM 警示 Notification service:</span><span class="sxs-lookup"><span data-stu-id="032c1-116">Stop the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="032c1-117">按一下  **啟動**, ，按一下  **執行**, ，型別 **cmd**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="032c1-117">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="032c1-118">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="032c1-118">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="032c1-119">**Net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="032c1-119">**Net stop NS$BamAlerts**</span></span>  
  
5.  <span data-ttu-id="032c1-120">在舊伺服器上備份 BAM 星狀結構描述資料庫。</span><span class="sxs-lookup"><span data-stu-id="032c1-120">Back up the BAM Star Schema database on the old server.</span></span> <span data-ttu-id="032c1-121">如需有關備份資料庫的指示，請遵循指示[如何： 備份資料庫 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510)中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何備份資料庫。</span><span class="sxs-lookup"><span data-stu-id="032c1-121">For instructions on backing up a database, follow the instructions at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to back up a database.</span></span>  
  
6.  <span data-ttu-id="032c1-122">BAM 星狀結構描述資料庫複製到新[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="032c1-122">Copy the BAM Star Schema database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
7.  <span data-ttu-id="032c1-123">還原 BAM 星狀結構描述資料庫的新伺服器上。</span><span class="sxs-lookup"><span data-stu-id="032c1-123">Restore the BAM Star Schema database on the new server.</span></span> <span data-ttu-id="032c1-124">如需在還原資料庫的指示，請遵循的指示[如何： 還原資料庫備份 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511)中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="032c1-124">For instructions on restoring the database, follow the instructions at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to restore a database.</span></span>  
  
##  <a name="BKMK_StarUpdate"></a> <span data-ttu-id="032c1-125">更新至新的 BAM 星狀結構描述資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="032c1-125">Updating References to the New BAM Star Schema Database</span></span>  
 <span data-ttu-id="032c1-126">移動資料庫之後，您必須更新至新的 BAM 星狀結構描述資料庫的所有參考。</span><span class="sxs-lookup"><span data-stu-id="032c1-126">After you have moved the database, you must update all the references to the new BAM Star Schema Database.</span></span> <span data-ttu-id="032c1-127">必須更新下列參考：</span><span class="sxs-lookup"><span data-stu-id="032c1-127">The following references must be updated:</span></span>  
  
-   <span data-ttu-id="032c1-128">以新的資料庫和伺服器名稱更新 BAM 組態。</span><span class="sxs-lookup"><span data-stu-id="032c1-128">Update the BAM configuration with the new database and server names.</span></span> <span data-ttu-id="032c1-129">請參閱[更新 BAM 組態](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdateBAMConfig)。</span><span class="sxs-lookup"><span data-stu-id="032c1-129">See [To update the BAM configuration](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdateBAMConfig).</span></span>  
  
-   <span data-ttu-id="032c1-130">更新所有 BAM 分析 SSIS 封裝中新的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="032c1-130">Update the new server and database names in all BAM analysis SSIS packages.</span></span> <span data-ttu-id="032c1-131">請參閱[更新伺服器和資料庫名稱中的所有 BAM SSIS 封裝](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdateRef)。</span><span class="sxs-lookup"><span data-stu-id="032c1-131">See [To update server and database names in all BAM SSIS packages](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdateRef).</span></span>  
  
-   <span data-ttu-id="032c1-132">更新的新伺服器和資料庫名稱在資料來源中所有非 OLAP cube。</span><span class="sxs-lookup"><span data-stu-id="032c1-132">Update the new server and database names in data sources for all non-OLAP cubes.</span></span> <span data-ttu-id="032c1-133">請參閱[更新伺服器和資料來源中的所有非 OLAP cube 的資料庫名稱](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_UpdateDS_non_OLAP)。</span><span class="sxs-lookup"><span data-stu-id="032c1-133">See [To update server and database names in data sources for all non-OLAP cubes](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_UpdateDS_non_OLAP).</span></span>  
  
###  <a name="BKMK_StarUpdateBAMConfig"></a> <span data-ttu-id="032c1-134">若要更新 BAM 組態</span><span class="sxs-lookup"><span data-stu-id="032c1-134">To update the BAM configuration</span></span>  
  
1.  <span data-ttu-id="032c1-135">取得用來還原 BAM 的 .xml 檔案複本：</span><span class="sxs-lookup"><span data-stu-id="032c1-135">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="032c1-136">按一下  **啟動**, ，按一下  **執行**, ，型別 **cmd**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="032c1-136">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="032c1-137">在上執行 BizTalk Server 的電腦，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="032c1-137">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
        -   <span data-ttu-id="032c1-138">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="032c1-138">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="032c1-139">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="032c1-139">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
        -   <span data-ttu-id="032c1-140">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="032c1-140">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="032c1-141">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="032c1-141">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    3.  <span data-ttu-id="032c1-142">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="032c1-142">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="032c1-143">**Bm.exe get-config –filename:BAMConfiguration.xml-server:\<servername\> -資料庫：\<資料庫\>**</span><span class="sxs-lookup"><span data-stu-id="032c1-143">**Bm.exe get-config –filename:BAMConfiguration.xml -server:\<servername\> -database:\<database\>**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="032c1-144">當執行此命令，以取代要取得組態資訊的來源伺服器的實際名稱\<servername\> ，並以要從中取得組態資訊的資料庫的實際名稱取代\<資料庫\>。</span><span class="sxs-lookup"><span data-stu-id="032c1-144">When running this command, substitute the actual name of the server from which to get the configuration information for \<servername\> and substitute the actual name of the database from which to get the configuration information for \<database\>.</span></span> <span data-ttu-id="032c1-145">如需有關如何使用 BAM 管理 (BM) 公用程式的詳細資訊，請參閱[基礎結構管理命令](http://go.microsoft.com/fwlink/?LinkId=156516)(http://go.microsoft.com/fwlink/?LinkId=156516)中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="032c1-145">For more information about using the BAM Management (BM) utility, see [Infrastructure Management Commands](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
2.  <span data-ttu-id="032c1-146">編輯 BAMConfiguration.xml 檔案，並變更**ServerName**中`<DeploymentUnit Name="StarSchemaDatabase">`區段，以新的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="032c1-146">Edit the BAMConfiguration.xml file and change the **ServerName** in the `<DeploymentUnit Name="StarSchemaDatabase">` section to the new server name.</span></span>  
  
3.  <span data-ttu-id="032c1-147">儲存並關閉 BAMConfiguration.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="032c1-147">Save and close the BAMConfiguration.xml file.</span></span>  
  
4.  <span data-ttu-id="032c1-148">按一下  **啟動**, ，按一下  **執行**, ，型別 **cmd**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="032c1-148">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="032c1-149">在上執行 BizTalk Server 的電腦，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="032c1-149">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
    -   <span data-ttu-id="032c1-150">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="032c1-150">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="032c1-151">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="032c1-151">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    -   <span data-ttu-id="032c1-152">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="032c1-152">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="032c1-153">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="032c1-153">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
6.  <span data-ttu-id="032c1-154">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="032c1-154">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="032c1-155">**bm.exe update-config -FileName:BAMConfiguration.xml**</span><span class="sxs-lookup"><span data-stu-id="032c1-155">**bm.exe update-config -FileName:BAMConfiguration.xml**</span></span>  
  
###  <a name="BKMK_StarUpdateRef"></a> <span data-ttu-id="032c1-156">若要更新的伺服器和所有 BAM SSIS 封裝中的資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="032c1-156">To update server and database names in all BAM SSIS packages</span></span>  
  
1.  <span data-ttu-id="032c1-157">更新所有 BAM 分析 SSIS 封裝，以"BAM_AN_"為前置詞中的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="032c1-157">Update the server and database names in all BAM analysis SSIS packages, which are prefixed with "BAM_AN_".</span></span> <span data-ttu-id="032c1-158">若要這樣做，請按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下**SQL Server Business Intelligence Development Studio**。</span><span class="sxs-lookup"><span data-stu-id="032c1-158">To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Business Intelligence Development Studio**.</span></span>  
  
2.  <span data-ttu-id="032c1-159">在 SQL Server Business Intelligence Development Studio 中建立新專案。</span><span class="sxs-lookup"><span data-stu-id="032c1-159">In SQL Server Business Intelligence Development Studio, create a new project.</span></span> <span data-ttu-id="032c1-160">按一下  **檔案**, ，按一下  **新增**, ，然後按一下  **專案**。</span><span class="sxs-lookup"><span data-stu-id="032c1-160">Click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="032c1-161">在**新專案**對話方塊中，於**專案類型**方塊中，按一下**商業智慧專案**。</span><span class="sxs-lookup"><span data-stu-id="032c1-161">In the **New Project** dialog box, in the **Project Types** box, click **Business Intelligence Projects**.</span></span> <span data-ttu-id="032c1-162">在右窗格中，在**範本**方塊中，按一下**Integration Services 專案**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="032c1-162">On the right pane, in the **Templates** box, click **Integration Services Project**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="032c1-163">在**Integration Services 專案**對話方塊中的，在 方案總管 中，以滑鼠右鍵按一下**SSIS 封裝**，然後按一下 **加入現有封裝**。</span><span class="sxs-lookup"><span data-stu-id="032c1-163">In the **Integration Services Project** dialog box, in Solution Explorer, right-click **SSIS Packages**, and then click **Add Existing Package**.</span></span>  
  
5.  <span data-ttu-id="032c1-164">在**加入現有封裝的副本**對話方塊中，於**伺服器**下拉式清單方塊中，選取包含 BAM_AN_ \* 封裝的伺服器。</span><span class="sxs-lookup"><span data-stu-id="032c1-164">In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_AN_\* packages.</span></span>  
  
6.  <span data-ttu-id="032c1-165">在 **封裝路徑**, ，按一下省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="032c1-165">In **Package Path**, click the ellipses button.</span></span>  
  
7.  <span data-ttu-id="032c1-166">在**SSIS 封裝**對話方塊方塊中，選取您想要更新，請按一下的封裝**確定**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="032c1-166">In the **SSIS Package** dialog box, select the package you want to update, click **OK**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="032c1-167">封裝現在會在 [方案總管] 中列出。</span><span class="sxs-lookup"><span data-stu-id="032c1-167">The package is now listed in Solution Explorer.</span></span>  
  
8.  <span data-ttu-id="032c1-168">在 [方案總管] 中，按兩下的封裝您在上一個步驟中加入。</span><span class="sxs-lookup"><span data-stu-id="032c1-168">In Solution Explorer, double-click the package you added in the previous step.</span></span> <span data-ttu-id="032c1-169">在**連接管理員**索引標籤上 （朝向螢幕的下半部提供），請按兩下資料來源數字 2 （BAMStarSchema 資料庫）。</span><span class="sxs-lookup"><span data-stu-id="032c1-169">In **Connection Managers** tab (available towards the lower half of the screen), double-click data source number 2 (BAMStarSchema database).</span></span>  
  
9. <span data-ttu-id="032c1-170">在**連線管理員**對話方塊中，於**伺服器名稱**方塊中，輸入伺服器的名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="032c1-170">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="032c1-171">重複此步驟的資料來源數字 3 （MSDB 資料庫）。</span><span class="sxs-lookup"><span data-stu-id="032c1-171">Repeat this for data source number 3 (MSDB database).</span></span>  
  
10. <span data-ttu-id="032c1-172">在**連接管理員**索引標籤上，按兩下資料來源數字 4 （BAMAnalysis 資料庫）。</span><span class="sxs-lookup"><span data-stu-id="032c1-172">In the **Connection Managers** tab, double-click data source number 4 (BAMAnalysis database).</span></span> <span data-ttu-id="032c1-173">在**加入 Analysis Services 連接管理員**對話方塊中，按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="032c1-173">In the **Add Analysis Services Connection Manager** dialog box, click **Edit**.</span></span>  
  
11. <span data-ttu-id="032c1-174">在**連線管理員**對話方塊中，於**伺服器名稱**方塊中，輸入伺服器的名稱，按一下**確定**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="032c1-174">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, click **OK**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="032c1-175">按一下**封裝總管**索引標籤上，按兩下**變數**資料夾，然後更新的值**AnalysisDatabase**， **AnalysisServer**， **PrimaryImportDatabase**， **PrimaryImportServer**， **StarSchemaDatabase**，和**StarSchemaServer**變數。</span><span class="sxs-lookup"><span data-stu-id="032c1-175">Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the **AnalysisDatabase**, **AnalysisServer**, **PrimaryImportDatabase**, **PrimaryImportServer**, **StarSchemaDatabase**, and **StarSchemaServer** variables.</span></span> <span data-ttu-id="032c1-176">您必須更新為指向新的伺服器與資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="032c1-176">You must update the values to point to the new server and database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="032c1-177">針對您想要更新的所有封裝重複步驟 4 到 12。</span><span class="sxs-lookup"><span data-stu-id="032c1-177">Repeat step 4 through 12 for all the packages that you want to update.</span></span>  
  
13. <span data-ttu-id="032c1-178">然後按一下**檔案**功能表，然後再按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="032c1-178">Click then **File** menu, and then click **Save All**.</span></span>  
  
14. <span data-ttu-id="032c1-179">啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="032c1-179">Start the SQL Server Management Studio.</span></span> <span data-ttu-id="032c1-180">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="032c1-180">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.</span></span>  
  
15. <span data-ttu-id="032c1-181">在**連接到伺服器**對話方塊中，從**伺服器**類型下拉式清單中，選取**Integration Services**。</span><span class="sxs-lookup"><span data-stu-id="032c1-181">In the **Connect to Server** dialog box, from the **Server** type drop-down list, select **Integration Services**.</span></span>  
  
16. <span data-ttu-id="032c1-182">指定伺服器名稱和認證以連接至伺服器，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="032c1-182">Specify the server name and credentials to connect to the server and click **OK**.</span></span>  
  
17. <span data-ttu-id="032c1-183">在**物件總管] 中**，依序展開**Integration Services**，依序展開**存放的封裝**，然後按一下 [ **MSDB**。</span><span class="sxs-lookup"><span data-stu-id="032c1-183">In the **Object Explorer**, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.</span></span>  
  
18. <span data-ttu-id="032c1-184">在**物件總管詳細資料**索引標籤上，以滑鼠右鍵按一下您稍早更新的封裝，然後按一下**匯入封裝**。</span><span class="sxs-lookup"><span data-stu-id="032c1-184">In the **Object Explorer Details** tab, right-click the package that you updated earlier and then click **Import Package**.</span></span>  
  
19. <span data-ttu-id="032c1-185">在**匯入封裝**對話方塊中，從**封裝位置**下拉式清單中，選取**檔案系統**。</span><span class="sxs-lookup"><span data-stu-id="032c1-185">In the **Import Package** dialog box, from the **Package location** drop-down list, select **File System**.</span></span>  
  
20. <span data-ttu-id="032c1-186">在**封裝路徑**、 瀏覽至您儲存的專案中，選取您想要匯入，然後按一下 封裝.dtsx 檔案**開啟**。</span><span class="sxs-lookup"><span data-stu-id="032c1-186">In **Package Path**, navigate to your saved project, select the .dtsx file for the package you want to import, and then click **Open**.</span></span>  
  
21. <span data-ttu-id="032c1-187">按一下 [封裝名稱] 方塊，以自動填入方塊內部。</span><span class="sxs-lookup"><span data-stu-id="032c1-187">Click inside the Package Name box to automatically populate the box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="032c1-188">針對您想要更新的所有封裝重複步驟 18 透過 21。</span><span class="sxs-lookup"><span data-stu-id="032c1-188">Repeat step 18 through 21 for all the packages that you want to update.</span></span>  
  
22. <span data-ttu-id="032c1-189">按一下  **確定**, ，然後按一下  **是** 覆寫。</span><span class="sxs-lookup"><span data-stu-id="032c1-189">Click **OK**, and then click **Yes** to overwrite.</span></span>  
  
23. <span data-ttu-id="032c1-190">啟用任何 BAM Cube 更新和資料維護 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="032c1-190">Enable any BAM cube update and data maintenance SSIS packages.</span></span>  
  
###  <a name="BKMK_UpdateDS_non_OLAP"></a> <span data-ttu-id="032c1-191">更新伺服器和資料來源中的所有非 OLAP cube 的資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="032c1-191">To update server and database names in data sources for all non-OLAP cubes</span></span>  
  
1.  <span data-ttu-id="032c1-192">更新的伺服器和資料庫名稱在資料來源中的所有非 OLAP cube。</span><span class="sxs-lookup"><span data-stu-id="032c1-192">Update the server and database names in data sources for all non-OLAP cubes.</span></span> <span data-ttu-id="032c1-193">若要這樣做，請按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**或**Microsoft SQL Server 2008 SP1**，然後按一下**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="032c1-193">To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="032c1-194">在**連接到伺服器**對話方塊中，針對**伺服器類型**下拉式清單中，選取**Analysis Services**、 提供伺服器名稱、 選取驗證方法 （和提供的認證有必要），然後按一下 **連接**。</span><span class="sxs-lookup"><span data-stu-id="032c1-194">In the **Connect to Server** dialog box, for the **Server type** drop-down list select **Analysis Services**, provide the server name, select an authentication method (and provide credentials if required), and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="032c1-195">在 [物件總管] 中，依序展開**資料庫**，依序展開**BAMAnalysis**，依序展開**資料來源**，然後按兩下資料來源。</span><span class="sxs-lookup"><span data-stu-id="032c1-195">In the Object Explorer, expand **Databases**, expand **BAMAnalysis**, expand **Data Sources**, and then double-click a data source.</span></span>  
  
4.  <span data-ttu-id="032c1-196">在**資料來源屬性**對話方塊方塊中，按一下省略符號按鈕 **（...）** 針對**連接字串**屬性。</span><span class="sxs-lookup"><span data-stu-id="032c1-196">In the **Data Source Properties** dialog box, click the ellipsis button **(…)** against the **Connection String** property.</span></span>  
  
5.  <span data-ttu-id="032c1-197">中**連接管理員**對話方塊中，於**伺服器名稱**方塊中，輸入裝載 BAMStarSchema 資料庫的伺服器名稱，按一下**確定**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="032c1-197">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server hosting the BAMStarSchema database, click **OK**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="032c1-198">啟動所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="032c1-198">Start all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="032c1-199">如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](http://go.microsoft.com/fwlink/?LinkId=154394)(http://go.microsoft.com/fwlink/?LinkId=154394)中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="032c1-199">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
7.  <span data-ttu-id="032c1-200">啟動 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="032c1-200">Start the IIS service.</span></span>  
  
8.  <span data-ttu-id="032c1-201">啟動 BAM 警示 Notification service:</span><span class="sxs-lookup"><span data-stu-id="032c1-201">Start the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="032c1-202">按一下  **啟動**, ，按一下  **執行**, ，型別 **cmd**, ，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="032c1-202">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="032c1-203">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="032c1-203">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="032c1-204">**Net start NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="032c1-204">**Net start NS$BamAlerts**</span></span>  
  
9. <span data-ttu-id="032c1-205">解決任何不完整的追蹤執行個體。</span><span class="sxs-lookup"><span data-stu-id="032c1-205">Resolve any incomplete trace instances.</span></span>  <span data-ttu-id="032c1-206">如需解決未完成的 BAM 活動執行個體的相關資訊，請參閱[如何解析未完成的活動執行個體](http://go.microsoft.com/fwlink/?LinkId=151475)(http://go.microsoft.com/fwlink/?LinkId=151475)。</span><span class="sxs-lookup"><span data-stu-id="032c1-206">For information about resolving incomplete BAM activity instances, see [How to Resolve Incomplete Activity Instances](http://go.microsoft.com/fwlink/?LinkId=151475) (http://go.microsoft.com/fwlink/?LinkId=151475).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="032c1-207">最好的作法是，您也應該主控 BAMStarSchema 資料庫的伺服器，移動 BAM_AN_ \* SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="032c1-207">As a good practice, you should also move the BAM_AN_\* SSIS packages to the server hosting the BAMStarSchema database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="032c1-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="032c1-208">See Also</span></span>  
 [<span data-ttu-id="032c1-209">移動資料庫</span><span class="sxs-lookup"><span data-stu-id="032c1-209">Moving Databases</span></span>](../technical-guides/moving-databases.md)