---
title: "如何移動 BAM Notification Services Databases1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89b4938e-ea4a-48d3-80c3-eb9401e28323
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a5f643d764790b37deaab445290f1230c9ed8ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-notification-services-databases"></a><span data-ttu-id="c00ed-102">如何移動 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="c00ed-102">How to Move the BAM Notification Services Databases</span></span>
<span data-ttu-id="c00ed-103">您可以使用此程序將 BAM Notification Services 資料庫移動到另一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="c00ed-103">You can use this procedure to move the BAM Notification Services database to another server.</span></span>  <span data-ttu-id="c00ed-104">端對端案例的觀點而言，移動 BAM Notification Services 資料庫包含兩個主要步驟：</span><span class="sxs-lookup"><span data-stu-id="c00ed-104">From an end-to-end scenario perspective, moving the BAM Notification Services database involves two major steps:</span></span>  
  
-   [<span data-ttu-id="c00ed-105">移動 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="c00ed-105">Moving the BAM Notification Services Database</span></span>](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiMoveDB)  
  
-   [<span data-ttu-id="c00ed-106">更新參考新的 BAM notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="c00ed-106">Updating References to the New BAM Notification Services Databases</span></span>](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdate)  
  
> [!NOTE]  
>  <span data-ttu-id="c00ed-107">您必須移動 BAM Notification Services 應用程式 (BAMAlertsApplication) 資料庫和 BAM Notification Services 執行個體 (BAMAlertsNSMain) 資料庫在一起。</span><span class="sxs-lookup"><span data-stu-id="c00ed-107">You must move the BAM Notification Services Application (BAMAlertsApplication) database and the BAM Notification Services Instance (BAMAlertsNSMain) database together.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c00ed-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="c00ed-108">Prerequisites</span></span>  
 <span data-ttu-id="c00ed-109">您必須以成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="c00ed-109">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
##  <span data-ttu-id="c00ed-110"><a name="BKMK_NotiMoveDB"></a>移動 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="c00ed-110"><a name="BKMK_NotiMoveDB"></a> Moving the BAM Notification Services Database</span></span>  
 <span data-ttu-id="c00ed-111">執行下列程序移動 BAM Notification Services 資料庫中的步驟。</span><span class="sxs-lookup"><span data-stu-id="c00ed-111">Perform the steps in the following procedure to move the BAM Notification Services database.</span></span>  
  
#### <a name="to-move-the-bam-notification-services-database"></a><span data-ttu-id="c00ed-112">若要移動 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="c00ed-112">To move the BAM Notification Services database</span></span>  
  
1.  <span data-ttu-id="c00ed-113">停止任何 BAM cube 更新及資料維護 SSIS 封裝，或防止它們執行，直到您完成 BAM Notification Services 資料庫的還原。</span><span class="sxs-lookup"><span data-stu-id="c00ed-113">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Notification Services database.</span></span>  
  
2.  <span data-ttu-id="c00ed-114">停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="c00ed-114">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="c00ed-115">如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](http://go.microsoft.com/fwlink/?LinkId=154394)(http://go.microsoft.com/fwlink/?LinkId=154394) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="c00ed-115">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
3.  <span data-ttu-id="c00ed-116">停止 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="c00ed-116">Stop the IIS service.</span></span>  
  
4.  <span data-ttu-id="c00ed-117">停止 BAM 警示 Notification service:</span><span class="sxs-lookup"><span data-stu-id="c00ed-117">Stop the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="c00ed-118">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c00ed-118">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="c00ed-119">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="c00ed-119">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="c00ed-120">**Net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="c00ed-120">**Net stop NS$BamAlerts**</span></span>  
  
5.  <span data-ttu-id="c00ed-121">在舊伺服器上備份 BAM Notification Services 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c00ed-121">Back up the BAM Notification Services database on the old server.</span></span> <span data-ttu-id="c00ed-122">如需有關備份資料庫的指示，請遵循指示[如何： 備份資料庫 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何備份資料庫。</span><span class="sxs-lookup"><span data-stu-id="c00ed-122">For instructions on backing up a database, follow the instructions at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to back up a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c00ed-123">BAMAlertsApplication 和 BAMAlertsNSMain 資料庫執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="c00ed-123">Perform this step for both BAMAlertsApplication and BAMAlertsNSMain databases.</span></span>  
  
6.  <span data-ttu-id="c00ed-124">將 BAM Notification Services 資料庫複製到新[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="c00ed-124">Copy the BAM Notification Services database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
7.  <span data-ttu-id="c00ed-125">BAM Notification Services 資料庫，新的伺服器上還原。</span><span class="sxs-lookup"><span data-stu-id="c00ed-125">Restore the BAM Notification Services database on the new server.</span></span> <span data-ttu-id="c00ed-126">如需在還原資料庫的指示，請遵循的指示[如何： 還原資料庫備份 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="c00ed-126">For instructions on restoring the database, follow the instructions at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to restore a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c00ed-127">BAMAlertsApplication 和 BAMAlertsNSMain 資料庫執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="c00ed-127">Perform this step for both BAMAlertsApplication and BAMAlertsNSMain databases.</span></span>  
  
##  <span data-ttu-id="c00ed-128"><a name="BKMK_NotiUpdate"></a>更新參考新的 BAM notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="c00ed-128"><a name="BKMK_NotiUpdate"></a> Updating References to the New BAM Notification Services Databases</span></span>  
 <span data-ttu-id="c00ed-129">移動資料庫之後，您必須更新 BAM Notification Services 資料庫的所有參考。</span><span class="sxs-lookup"><span data-stu-id="c00ed-129">After you have moved the database, you must update all the references to the new BAM Notification Services databases.</span></span> <span data-ttu-id="c00ed-130">必須更新下列參考：</span><span class="sxs-lookup"><span data-stu-id="c00ed-130">The following references must be updated:</span></span>  
  
-   <span data-ttu-id="c00ed-131">以新的資料庫和伺服器名稱更新 BAM 組態。</span><span class="sxs-lookup"><span data-stu-id="c00ed-131">Update the BAM configuration with the new database and server names.</span></span> <span data-ttu-id="c00ed-132">請參閱[更新 BAM 組態](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdateBAMConfig)。</span><span class="sxs-lookup"><span data-stu-id="c00ed-132">See [To update the BAM configuration](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdateBAMConfig).</span></span>  
  
-   <span data-ttu-id="c00ed-133">重新註冊 Notification Service 中的所有電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。</span><span class="sxs-lookup"><span data-stu-id="c00ed-133">Re-register the Notification Service on all computers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.</span></span> <span data-ttu-id="c00ed-134">請參閱[註冊 Notification Services](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiRegister)。</span><span class="sxs-lookup"><span data-stu-id="c00ed-134">See [Register the Notification Services](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiRegister).</span></span>  
  
###  <span data-ttu-id="c00ed-135"><a name="BKMK_NotiUpdateBAMConfig"></a>若要更新 BAM 組態</span><span class="sxs-lookup"><span data-stu-id="c00ed-135"><a name="BKMK_NotiUpdateBAMConfig"></a> To update the BAM configuration</span></span>  
  
1.  <span data-ttu-id="c00ed-136">取得用來還原 BAM 的 .xml 檔案複本：</span><span class="sxs-lookup"><span data-stu-id="c00ed-136">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="c00ed-137">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c00ed-137">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="c00ed-138">在執行 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 的電腦中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="c00ed-138">On a computer running [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], browse to the following folder:</span></span>  
  
        -   <span data-ttu-id="c00ed-139">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="c00ed-139">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="c00ed-140">**%Programfiles (x86) %\Microsoft BizTalk Server 2010 \tracking**</span><span class="sxs-lookup"><span data-stu-id="c00ed-140">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
        -   <span data-ttu-id="c00ed-141">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="c00ed-141">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="c00ed-142">**%ProgramFiles%\Microsoft BizTalk Server 2010 \tracking**</span><span class="sxs-lookup"><span data-stu-id="c00ed-142">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    3.  <span data-ttu-id="c00ed-143">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="c00ed-143">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="c00ed-144">**Bm.exe get-config –filename:BAMConfiguration.xml-server:\<伺服器名稱 >-資料庫：\<資料庫 >**</span><span class="sxs-lookup"><span data-stu-id="c00ed-144">**Bm.exe get-config –filename:BAMConfiguration.xml -server:\<servername> -database:\<database>**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c00ed-145">當執行此命令，以取代要取得組態資訊的來源伺服器的實際名稱<servername>，並以要從中取得組態資訊的資料庫的實際名稱取代<database>。</span><span class="sxs-lookup"><span data-stu-id="c00ed-145">When running this command, substitute the actual name of the server from which to get the configuration information for <servername> and substitute the actual name of the database from which to get the configuration information for <database>.</span></span> <span data-ttu-id="c00ed-146">如需有關如何使用 BAM 管理 (BM) 公用程式的詳細資訊，請參閱[基礎結構管理命令](http://go.microsoft.com/fwlink/?LinkId=156516)(http://go.microsoft.com/fwlink/?LinkId=156516) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="c00ed-146">For more information about using the BAM Management (BM) utility, see [Infrastructure Management Commands](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
2.  <span data-ttu-id="c00ed-147">編輯 BAMConfiguration.xml 檔案，並變更**DBServer**中的屬性`<DeploymentUnit Name="Alert">`區段，以新的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="c00ed-147">Edit the BAMConfiguration.xml file and change the **DBServer** properties in the `<DeploymentUnit Name="Alert">` section to the new server name.</span></span>  
  
3.  <span data-ttu-id="c00ed-148">儲存並關閉 BAMConfiguration.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="c00ed-148">Save and close the BAMConfiguration.xml file.</span></span>  
  
4.  <span data-ttu-id="c00ed-149">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c00ed-149">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c00ed-150">在執行 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 的電腦中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="c00ed-150">On a computer running [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], browse to the following folder:</span></span>  
  
    -   <span data-ttu-id="c00ed-151">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="c00ed-151">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="c00ed-152">**%Programfiles (x86) %\Microsoft BizTalk Server 2010 \tracking**</span><span class="sxs-lookup"><span data-stu-id="c00ed-152">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    -   <span data-ttu-id="c00ed-153">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="c00ed-153">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="c00ed-154">**%ProgramFiles%\Microsoft BizTalk Server 2010 \tracking**</span><span class="sxs-lookup"><span data-stu-id="c00ed-154">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
6.  <span data-ttu-id="c00ed-155">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="c00ed-155">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="c00ed-156">**bm.exe 更新-config-FileName:BAMConfiguration.xml**</span><span class="sxs-lookup"><span data-stu-id="c00ed-156">**bm.exe update-config -FileName:BAMConfiguration.xml**</span></span>  
  
###  <span data-ttu-id="c00ed-157"><a name="BKMK_NotiRegister"></a>註冊 Notification Services</span><span class="sxs-lookup"><span data-stu-id="c00ed-157"><a name="BKMK_NotiRegister"></a> Register the Notification Services</span></span>  
 <span data-ttu-id="c00ed-158">移動 BAM Notification Services 資料庫之後，您必須重新註冊 Notification Service，BizTalk Server 群組中執行 Notification Services (NSservice.exe) 的所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="c00ed-158">After you have moved the BAM Notification Services database, you must re-register the Notification Service on all computers in the BizTalk Server group that are running Notification Services (NSservice.exe).</span></span> <span data-ttu-id="c00ed-159">這樣可以讓 Notification Services 連線至其位於新位置的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c00ed-159">This enables Notification Services to connect to the databases in their new location.</span></span> <span data-ttu-id="c00ed-160">如需有關如何註冊 Notification Services 的指示，請依照下列步驟 5 至 11[如何更新 BAM Notification Services 資料庫參考](http://go.microsoft.com/fwlink/?LinkId=156684)(http://go.microsoft.com/fwlink/?LinkId=156684) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="c00ed-160">For instructions on how to register the Notification Services, follow steps 5 through 11 at [How to Update References to the BAM Notification Services Databases](http://go.microsoft.com/fwlink/?LinkId=156684) (http://go.microsoft.com/fwlink/?LinkId=156684) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
 <span data-ttu-id="c00ed-161">下列執行上述的連結中所述的步驟時的注意事項：</span><span class="sxs-lookup"><span data-stu-id="c00ed-161">Note the following while performing steps mentioned in the preceding link:</span></span>  
  
-   <span data-ttu-id="c00ed-162">步驟 5 和 6 先前連結中的必須對下列屬性的 BAM 組態 XML 中列出的伺服器：</span><span class="sxs-lookup"><span data-stu-id="c00ed-162">Steps 5 and 6 in the preceding link must be performed on the servers listed in the BAM configuration XML for the following properties:</span></span>  
  
    ```  
    <DeploymentUnit Name="Alert">  
      <Property Name="GeneratorServerName">Server_Name</Property>  
      <Property Name="ProviderServerName">Server_Name</Property>  
      <Property Name="DistributorServerName">Server_Name</Property>  
    </DeploymentUnit>  
  
    ```  
  
-   <span data-ttu-id="c00ed-163">必須在裝載 BAM 入口網站的電腦上執行步驟 7 到 11。</span><span class="sxs-lookup"><span data-stu-id="c00ed-163">Step 7 through 11 must be performed on the computer that hosts the BAM portal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c00ed-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c00ed-164">See Also</span></span>  
 [<span data-ttu-id="c00ed-165">移動資料庫</span><span class="sxs-lookup"><span data-stu-id="c00ed-165">Moving Databases</span></span>](../technical-guides/moving-databases.md)