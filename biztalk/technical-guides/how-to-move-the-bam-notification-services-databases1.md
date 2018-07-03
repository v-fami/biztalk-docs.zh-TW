---
title: 如何移動 BAM Notification Services Databases1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 89b4938e-ea4a-48d3-80c3-eb9401e28323
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 432499729e0f28092e13e222e29d2c92607ec6ca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996231"
---
# <a name="how-to-move-the-bam-notification-services-databases"></a><span data-ttu-id="b108d-102">如何移動 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="b108d-102">How to Move the BAM Notification Services Databases</span></span>
<span data-ttu-id="b108d-103">您可以使用此程序將 BAM Notification Services 資料庫移動到另一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="b108d-103">You can use this procedure to move the BAM Notification Services database to another server.</span></span>  <span data-ttu-id="b108d-104">端對端案例的觀點而言，移動 BAM Notification Services 資料庫包含兩個主要步驟：</span><span class="sxs-lookup"><span data-stu-id="b108d-104">From an end-to-end scenario perspective, moving the BAM Notification Services database involves two major steps:</span></span>  
  
-   [<span data-ttu-id="b108d-105">移動 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="b108d-105">Moving the BAM Notification Services Database</span></span>](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiMoveDB)  
  
-   [<span data-ttu-id="b108d-106">正在更新參考新的 BAM notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="b108d-106">Updating References to the New BAM Notification Services Databases</span></span>](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdate)  
  
> [!NOTE]  
>  <span data-ttu-id="b108d-107">您必須移動 BAM Notification Services 應用程式 (BAMAlertsApplication) 資料庫和 BAM Notification Services 執行個體 (BAMAlertsNSMain) 資料庫在一起。</span><span class="sxs-lookup"><span data-stu-id="b108d-107">You must move the BAM Notification Services Application (BAMAlertsApplication) database and the BAM Notification Services Instance (BAMAlertsNSMain) database together.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b108d-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="b108d-108">Prerequisites</span></span>  
 <span data-ttu-id="b108d-109">您必須以成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="b108d-109">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
##  <a name="BKMK_NotiMoveDB"></a> <span data-ttu-id="b108d-110">移動 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="b108d-110">Moving the BAM Notification Services Database</span></span>  
 <span data-ttu-id="b108d-111">執行下列程序移動 BAM Notification Services 資料庫中的步驟。</span><span class="sxs-lookup"><span data-stu-id="b108d-111">Perform the steps in the following procedure to move the BAM Notification Services database.</span></span>  
  
#### <a name="to-move-the-bam-notification-services-database"></a><span data-ttu-id="b108d-112">移動 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="b108d-112">To move the BAM Notification Services database</span></span>  
  
1. <span data-ttu-id="b108d-113">停止任何 BAM cube 更新和資料維護 SSIS 封裝，或防止它們執行，直到您完成 BAM Notification Services 資料庫的還原為止。</span><span class="sxs-lookup"><span data-stu-id="b108d-113">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Notification Services database.</span></span>  
  
2. <span data-ttu-id="b108d-114">停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="b108d-114">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="b108d-115">如需詳細資訊，請參閱主題[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="b108d-115">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (<http://go.microsoft.com/fwlink/?LinkId=154394>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
3. <span data-ttu-id="b108d-116">停止 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="b108d-116">Stop the IIS service.</span></span>  
  
4. <span data-ttu-id="b108d-117">停止 BAM 警示 Notification service:</span><span class="sxs-lookup"><span data-stu-id="b108d-117">Stop the BAM Alerts Notification service:</span></span>  
  
   1.  <span data-ttu-id="b108d-118">按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b108d-118">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
   2.  <span data-ttu-id="b108d-119">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="b108d-119">At the command prompt, type:</span></span>  
  
        <span data-ttu-id="b108d-120">**net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="b108d-120">**Net stop NS$BamAlerts**</span></span>  
  
5. <span data-ttu-id="b108d-121">備份舊伺服器上的 BAM Notification Services 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b108d-121">Back up the BAM Notification Services database on the old server.</span></span> <span data-ttu-id="b108d-122">如需有關備份資料庫的指示，請遵循指示[如何： 備份資料庫 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (<http://go.microsoft.com/fwlink/?LinkId=156510>) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何備份資料庫。</span><span class="sxs-lookup"><span data-stu-id="b108d-122">For instructions on backing up a database, follow the instructions at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (<http://go.microsoft.com/fwlink/?LinkId=156510>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to back up a database.</span></span>  
  
   > [!NOTE]  
   >  <span data-ttu-id="b108d-123">BAMAlertsApplication 和 BAMAlertsNSMain 資料庫執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="b108d-123">Perform this step for both BAMAlertsApplication and BAMAlertsNSMain databases.</span></span>  
  
6. <span data-ttu-id="b108d-124">將 BAM Notification Services 資料庫複製到新[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="b108d-124">Copy the BAM Notification Services database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
7. <span data-ttu-id="b108d-125">將新的伺服器上的 BAM Notification Services 資料庫還原。</span><span class="sxs-lookup"><span data-stu-id="b108d-125">Restore the BAM Notification Services database on the new server.</span></span> <span data-ttu-id="b108d-126">如需還原資料庫的指示，請遵循指示[如何： 還原資料庫備份 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (<http://go.microsoft.com/fwlink/?LinkId=156511>) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 有關如何還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="b108d-126">For instructions on restoring the database, follow the instructions at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (<http://go.microsoft.com/fwlink/?LinkId=156511>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to restore a database.</span></span>  
  
   > [!NOTE]  
   >  <span data-ttu-id="b108d-127">BAMAlertsApplication 和 BAMAlertsNSMain 資料庫執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="b108d-127">Perform this step for both BAMAlertsApplication and BAMAlertsNSMain databases.</span></span>  
  
##  <a name="BKMK_NotiUpdate"></a> <span data-ttu-id="b108d-128">正在更新參考新的 BAM notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="b108d-128">Updating References to the New BAM Notification Services Databases</span></span>  
 <span data-ttu-id="b108d-129">移動資料庫之後，您必須更新到新的 BAM Notification Services 資料庫的所有參考。</span><span class="sxs-lookup"><span data-stu-id="b108d-129">After you have moved the database, you must update all the references to the new BAM Notification Services databases.</span></span> <span data-ttu-id="b108d-130">必須更新下列參考：</span><span class="sxs-lookup"><span data-stu-id="b108d-130">The following references must be updated:</span></span>  
  
- <span data-ttu-id="b108d-131">使用新的資料庫和伺服器名稱更新 BAM 組態。</span><span class="sxs-lookup"><span data-stu-id="b108d-131">Update the BAM configuration with the new database and server names.</span></span> <span data-ttu-id="b108d-132">請參閱[若要更新 BAM 組態](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdateBAMConfig)。</span><span class="sxs-lookup"><span data-stu-id="b108d-132">See [To update the BAM configuration](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdateBAMConfig).</span></span>  
  
- <span data-ttu-id="b108d-133">重新註冊 Notification Service 中的所有電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。</span><span class="sxs-lookup"><span data-stu-id="b108d-133">Re-register the Notification Service on all computers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.</span></span> <span data-ttu-id="b108d-134">請參閱[註冊 Notification Services](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiRegister)。</span><span class="sxs-lookup"><span data-stu-id="b108d-134">See [Register the Notification Services](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiRegister).</span></span>  
  
###  <a name="BKMK_NotiUpdateBAMConfig"></a> <span data-ttu-id="b108d-135">若要更新 BAM 組態</span><span class="sxs-lookup"><span data-stu-id="b108d-135">To update the BAM configuration</span></span>  
  
1. <span data-ttu-id="b108d-136">取得用來還原 BAM 的 .xml 檔案複本：</span><span class="sxs-lookup"><span data-stu-id="b108d-136">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
   1. <span data-ttu-id="b108d-137">按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b108d-137">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
   2. <span data-ttu-id="b108d-138">在執行 BizTalk Server 的電腦，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="b108d-138">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
      - <span data-ttu-id="b108d-139">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="b108d-139">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="b108d-140">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="b108d-140">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
      - <span data-ttu-id="b108d-141">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="b108d-141">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="b108d-142">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="b108d-142">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
   3. <span data-ttu-id="b108d-143">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="b108d-143">At the command prompt, type:</span></span>  
  
       <span data-ttu-id="b108d-144">**Bm.exe 取得設定 –filename:BAMConfiguration.xml-server:\<servername\> -資料庫：\<資料庫\>**</span><span class="sxs-lookup"><span data-stu-id="b108d-144">**Bm.exe get-config –filename:BAMConfiguration.xml -server:\<servername\> -database:\<database\>**</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="b108d-145">執行此命令時，替代伺服器，以取得組態資訊的實際名稱<servername>，並以要從中取得組態資訊的資料庫的實際名稱取代<database>。</span><span class="sxs-lookup"><span data-stu-id="b108d-145">When running this command, substitute the actual name of the server from which to get the configuration information for <servername> and substitute the actual name of the database from which to get the configuration information for <database>.</span></span> <span data-ttu-id="b108d-146">如需使用 BAM 管理 (BM) 公用程式的詳細資訊，請參閱[基礎結構管理命令](http://go.microsoft.com/fwlink/?LinkId=156516)(<http://go.microsoft.com/fwlink/?LinkId=156516>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="b108d-146">For more information about using the BAM Management (BM) utility, see [Infrastructure Management Commands](http://go.microsoft.com/fwlink/?LinkId=156516) (<http://go.microsoft.com/fwlink/?LinkId=156516>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
2. <span data-ttu-id="b108d-147">編輯 BAMConfiguration.xml 檔案，並變更**DBServer**中的屬性`<DeploymentUnit Name="Alert">`一節，以新的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="b108d-147">Edit the BAMConfiguration.xml file and change the **DBServer** properties in the `<DeploymentUnit Name="Alert">` section to the new server name.</span></span>  
  
3. <span data-ttu-id="b108d-148">儲存並關閉 BAMConfiguration.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="b108d-148">Save and close the BAMConfiguration.xml file.</span></span>  
  
4. <span data-ttu-id="b108d-149">按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b108d-149">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="b108d-150">在執行 BizTalk Server 的電腦，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="b108d-150">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
   - <span data-ttu-id="b108d-151">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 64 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="b108d-151">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
      <span data-ttu-id="b108d-152">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="b108d-152">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
   - <span data-ttu-id="b108d-153">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝在 32 位元版本的 Windows Server:</span><span class="sxs-lookup"><span data-stu-id="b108d-153">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
      <span data-ttu-id="b108d-154">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="b108d-154">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
6. <span data-ttu-id="b108d-155">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="b108d-155">At the command prompt, type:</span></span>  
  
    <span data-ttu-id="b108d-156">**bm.exe update-config -FileName:BAMConfiguration.xml**</span><span class="sxs-lookup"><span data-stu-id="b108d-156">**bm.exe update-config -FileName:BAMConfiguration.xml**</span></span>  
  
###  <a name="BKMK_NotiRegister"></a> <span data-ttu-id="b108d-157">註冊 Notification Services</span><span class="sxs-lookup"><span data-stu-id="b108d-157">Register the Notification Services</span></span>  
 <span data-ttu-id="b108d-158">移動 BAM Notification Services 資料庫之後，您必須重新註冊 Notification Service，BizTalk Server 群組中執行 Notification Services (NSservice.exe) 的所有電腦上。</span><span class="sxs-lookup"><span data-stu-id="b108d-158">After you have moved the BAM Notification Services database, you must re-register the Notification Service on all computers in the BizTalk Server group that are running Notification Services (NSservice.exe).</span></span> <span data-ttu-id="b108d-159">這樣可以讓 Notification Services 連線至其位於新位置的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b108d-159">This enables Notification Services to connect to the databases in their new location.</span></span> <span data-ttu-id="b108d-160">如需有關如何註冊 Notification Services 的指示，請依照下列步驟 5 至 11[如何更新 BAM Notification Services 資料庫的參考](http://go.microsoft.com/fwlink/?LinkId=156684)(<http://go.microsoft.com/fwlink/?LinkId=156684>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="b108d-160">For instructions on how to register the Notification Services, follow steps 5 through 11 at [How to Update References to the BAM Notification Services Databases](http://go.microsoft.com/fwlink/?LinkId=156684) (<http://go.microsoft.com/fwlink/?LinkId=156684>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
 <span data-ttu-id="b108d-161">執行上述連結中所述的步驟時下列資訊：</span><span class="sxs-lookup"><span data-stu-id="b108d-161">Note the following while performing steps mentioned in the preceding link:</span></span>  
  
-   <span data-ttu-id="b108d-162">步驟 5 和 6 上述連結內必須被對下列屬性的 BAM 組態 XML 中列出的伺服器：</span><span class="sxs-lookup"><span data-stu-id="b108d-162">Steps 5 and 6 in the preceding link must be performed on the servers listed in the BAM configuration XML for the following properties:</span></span>  
  
    ```  
    <DeploymentUnit Name="Alert">  
      <Property Name="GeneratorServerName">Server_Name</Property>  
      <Property Name="ProviderServerName">Server_Name</Property>  
      <Property Name="DistributorServerName">Server_Name</Property>  
    </DeploymentUnit>  
  
    ```  
  
-   <span data-ttu-id="b108d-163">必須在裝載 BAM 入口網站的電腦上執行步驟 7 到 11。</span><span class="sxs-lookup"><span data-stu-id="b108d-163">Step 7 through 11 must be performed on the computer that hosts the BAM portal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b108d-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b108d-164">See Also</span></span>  
 [<span data-ttu-id="b108d-165">移動資料庫</span><span class="sxs-lookup"><span data-stu-id="b108d-165">Moving Databases</span></span>](../technical-guides/moving-databases.md)