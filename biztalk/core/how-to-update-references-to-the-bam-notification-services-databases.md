---
title: "如何更新參考 BAM Notification Services 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Notification Services Application database [BAM], restoring
- Notification Services Application database [BAM], updating references
- restoring, BAM
- NS$instance_name service Notification Services Application database [BAM], NS$instance_name service
- restoring [BAM], updating references
- BAM, restoring
- restoring [BAM], Notification Services Application database
- restoring [BAM], NS$instance_name service
ms.assetid: b007fdc2-2e74-4eef-b4c3-43689e9f2180
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c27f1ecaf07c3f953372a9e5733d62c8376a288f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-update-references-to-the-bam-notification-services-databases"></a><span data-ttu-id="4f6ad-102">如何更新 BAM Notification Services 資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="4f6ad-102">How to Update References to the BAM Notification Services Databases</span></span>
<span data-ttu-id="4f6ad-103">執行將「商務活動監控」(BAM) 的 Notification Services 資料庫還原至目的地系統的必要步驟之後，您必須在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組中執行 Notification Services (NSservice.exe) 的所有電腦上重新註冊 Notification Service。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-103">After you perform the steps necessary to restore the Business Activity Monitoring (BAM) Notification Services databases to the destination system, you must re-register the Notification Service on all computers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group that are running Notification Services (NSservice.exe).</span></span> <span data-ttu-id="4f6ad-104">這樣可以讓 Notification Services 連線至其位於新位置的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-104">This enables Notification Services to connect to the databases in their new location.</span></span>  
  
 <span data-ttu-id="4f6ad-105">註冊 Notification Services 的執行個體會建立 NS$instance_name 服務、在本機伺服器建立效能計數器，以及在登錄中新增資訊。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-105">Registering an instance of Notification Services creates the NS$instance_name service, creates performance counters on the local server, and adds information to the registry.</span></span> <span data-ttu-id="4f6ad-106">您必須在下列伺服器上註冊執行個體：</span><span class="sxs-lookup"><span data-stu-id="4f6ad-106">You must register the instance on the following servers:</span></span>  
  
-   <span data-ttu-id="4f6ad-107">每個執行 NS$instance_name 服務的伺服器。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-107">Each server that runs the NS$instance_name service.</span></span> <span data-ttu-id="4f6ad-108">執行事件提供者主控件、產生器和散發者元件的服務。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-108">The service runs the event provider host, generator, and distributor components.</span></span> <span data-ttu-id="4f6ad-109">在向外擴充的組態中，在多部伺服器上執行的服務。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-109">For scaled-out configurations, the service runs on multiple servers.</span></span>  
  
-   <span data-ttu-id="4f6ad-110">每個執行訂閱管理應用程式的伺服器。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-110">Each server that runs a subscription management application.</span></span> <span data-ttu-id="4f6ad-111">如果訂閱管理應用程式是在自己的伺服器上執行，請不要在註冊執行個體時建立 NS$instance_name 服務。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-111">If the subscription management application runs on its own server, do not create the NS$instance_name service when registering the instance.</span></span>  
  
-   <span data-ttu-id="4f6ad-112">每個執行獨立事件提供者的伺服器。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-112">Each server that runs an independent event provider.</span></span> <span data-ttu-id="4f6ad-113">如果獨立事件提供者是在自己的伺服器或資料庫伺服器上執行，請不要在註冊執行個體時建立 NS$instance_name 服務。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-113">If the independent event provider runs on its own server or the database server, do not create the NS$instance_name service when registering the instance.</span></span>  
  
 <span data-ttu-id="4f6ad-114">如果資料庫伺服器也沒有執行 Notification Services 執行個體或用戶端元件，請不要在此伺服器註冊執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-114">If the database server does not also run the Notification Services instance or the client components, do not register the instance on this server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4f6ad-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="4f6ad-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="4f6ad-116">您必須以「系統管理員」群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-116">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
-   <span data-ttu-id="4f6ad-117">在您要還原 BAM Notification Services 資料庫的電腦上，必須安裝 BAM Alert Provider for SQL Notification Services。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-117">The Business Activity Monitoring (BAM) Alert Provider for SQL Notification Services must be installed on the computer where you are restoring the BAM Notification Services databases.</span></span>  
  
### <a name="to-update-references-to-the-bam-notification-services-databases-sql-server-2008-r2sp1"></a><span data-ttu-id="4f6ad-118">若要更新 BAM Notification Services 資料庫的參考 (SQL Server 2008 R2/SP1)</span><span class="sxs-lookup"><span data-stu-id="4f6ad-118">To update references to the BAM Notification Services databases (SQL Server 2008 R2/SP1)</span></span>  
  
1.  <span data-ttu-id="4f6ad-119">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-119">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="4f6ad-120">在命令提示字元中，瀏覽至下列目錄：[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-120">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="4f6ad-121">類型： **bm.exe get-config**</span><span class="sxs-lookup"><span data-stu-id="4f6ad-121">Type: **bm.exe get-config –filename:config.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4f6ad-122">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-122">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="4f6ad-123">開啟步驟 2 建立的 XML 檔案以取得您必須在其中重新註冊 Notification Services 的電腦的清單。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-123">Open the xml file created in step 2 to obtain the list of the computers on which you must re-register Notification Services.</span></span>  
  
     <span data-ttu-id="4f6ad-124">電腦名稱會列在**\<屬性名稱\=\>** 中的參數 **\<DeploymentUnit 名稱 = 警示\>** xml 檔案的區段：</span><span class="sxs-lookup"><span data-stu-id="4f6ad-124">The computer names are listed in the **\<Property Name\=\>** parameters in the **\<DeploymentUnit Name="Alert"\>** section of the xml file:</span></span>  
  
    ```  
    -<DeploymentUnit Name="Alert">  
    <Property Name="GeneratorServerName" />  
    <Property Name="ProviderServerName" />  
    <Property Name="DistributorServerName" />  
      </DeploymentUnit>  
    ```  
  
5.  <span data-ttu-id="4f6ad-125">在 XML 檔案所列出的每台電腦上，停止 NS 服務，然後取消註冊 Notification Services 的執行個體：</span><span class="sxs-lookup"><span data-stu-id="4f6ad-125">On each computer listed in the xml file, stop the NS service and then unregister an instance of Notification Services:</span></span>  
  
    1.  <span data-ttu-id="4f6ad-126">按一下**啟動**，按一下 **程式**，按一下  **Microsoft SQL Server 2008 R2**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-126">Click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
    2.  <span data-ttu-id="4f6ad-127">在命令提示字元中，輸入： **net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="4f6ad-127">At the command prompt, type: **net stop NS$BamAlerts**</span></span>  
  
    3.  <span data-ttu-id="4f6ad-128">輸入下列命令取消註冊執行個體：</span><span class="sxs-lookup"><span data-stu-id="4f6ad-128">Type the following command to unregister the instance:</span></span>  
  
         <span data-ttu-id="4f6ad-129">**nscontrol unregister-name BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="4f6ad-129">**nscontrol unregister  -name BamAlerts**</span></span>  
  
         <span data-ttu-id="4f6ad-130">取消註冊執行個體會移除登錄項目、移除 NS$instance_name 服務 (如果有)，並刪除服務的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-130">Unregistering an instance removes the registry entries, removes the NS$instance_name service (if present), and deletes the performance counters for the service.</span></span>  
  
6.  <span data-ttu-id="4f6ad-131">重新註冊 Notification Services：</span><span class="sxs-lookup"><span data-stu-id="4f6ad-131">Re-register the Notification Service:</span></span>  
  
    1.  <span data-ttu-id="4f6ad-132">按一下**啟動**，按一下 **程式**，按一下  **Microsoft SQL Server 2008 R2**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-132">Click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
    2.  <span data-ttu-id="4f6ad-133">在命令提示字元中，輸入： **nscontrol register-name BamAlerts-server**  *\<ServerName\>***-服務-serviceusername"** *\<ServiceUserName\>***"-servicepassword"***\<ServicePassword\>***"**</span><span class="sxs-lookup"><span data-stu-id="4f6ad-133">At the command prompt, type: **nscontrol register -name BamAlerts -server** *\<ServerName\>***-service -serviceusername "***\<ServiceUserName\>***" -servicepassword "***\<ServicePassword\>***"**</span></span>  
  
         <span data-ttu-id="4f6ad-134">這樣可以讓 Notification Services 登入正確的資料庫 (這項資訊是在服務電腦的登錄中由 nscontrol 執行維護)。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-134">This enables Notification Services to log on to the correct database (this information is maintained in the registry of the service machine by nscontrol).</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="4f6ad-135">請記得使用新的 Notification Services 資料庫伺服器中**-伺服器**選項重新註冊服務時。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-135">Remember to use the new Notification Services databases server in the **-server** option when re-registering the service.</span></span> <span data-ttu-id="4f6ad-136">此外，您也應該將新的 Notification Services 服務的使用者名稱，保持與舊服務的使用者名稱一致。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-136">In addition, you should use the same user name for the new Notification Services service as the old one.</span></span>  
  
7.  <span data-ttu-id="4f6ad-137">在裝載 BAM 入口網站的電腦，按一下 **啟動**，按一下 **程式**，按一下**Microsoft SQL Server 2008 R2**，按一下 **組態工具**，然後按一下  **Notification Services 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-137">On the computer that hosts the BAM portal, click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
8.  <span data-ttu-id="4f6ad-138">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="4f6ad-138">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="4f6ad-139">**net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="4f6ad-139">**net stop NS$BamAlerts**</span></span>  
  
9. <span data-ttu-id="4f6ad-140">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="4f6ad-140">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="4f6ad-141">**nscontrol unregister-name BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="4f6ad-141">**nscontrol unregister  -name BamAlerts**</span></span>  
  
10. <span data-ttu-id="4f6ad-142">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="4f6ad-142">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="4f6ad-143">**nscontrol register-name***\<BamAlerts\>***-伺服器**  *\<NotificationServicesDatabaseServer    \>*</span><span class="sxs-lookup"><span data-stu-id="4f6ad-143">**nscontrol register  -name**  *\<BamAlerts\>*  **-server** *\<NotificationServicesDatabaseServer\>*</span></span>  
  
11. <span data-ttu-id="4f6ad-144">在命令提示字元中，輸入： **net start NS$ BamAlerts**。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-144">At the command prompt, type: **net start NS$BamAlerts**.</span></span>  
  
12. <span data-ttu-id="4f6ad-145">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-145">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="4f6ad-146">在命令提示字元中，瀏覽至下列目錄：[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-146">At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
14. <span data-ttu-id="4f6ad-147">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="4f6ad-147">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="4f6ad-148">**bm.exe 更新-config –FileName:config.xml**</span><span class="sxs-lookup"><span data-stu-id="4f6ad-148">**bm.exe update-config –FileName:config.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4f6ad-149">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="4f6ad-149">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f6ad-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f6ad-150">See Also</span></span>  
 [<span data-ttu-id="4f6ad-151">備份和還原 BAM</span><span class="sxs-lookup"><span data-stu-id="4f6ad-151">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)