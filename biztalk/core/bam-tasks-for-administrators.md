---
title: "系統管理員的 BAM 工作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d9ae9a6-50fa-4f82-8e48-8dffa55c127f
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b529a0510ee56a92d3957a84a91d635666016f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-tasks-for-administrators"></a><span data-ttu-id="baaa1-102">系統管理員的 BAM 工作</span><span class="sxs-lookup"><span data-stu-id="baaa1-102">BAM Tasks for Administrators</span></span>
<span data-ttu-id="baaa1-103">這個主題說明 BAM 系統管理員在管理 BAM 基礎結構時從事的一般工作。</span><span class="sxs-lookup"><span data-stu-id="baaa1-103">This topic describes typical tasks that BAM administrators undertake in managing the BAM infrastructure.</span></span>  
  
## <a name="configuring-bam"></a><span data-ttu-id="baaa1-104">設定 BAM</span><span class="sxs-lookup"><span data-stu-id="baaa1-104">Configuring BAM</span></span>  
 <span data-ttu-id="baaa1-105">BAM 的初始組態是使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態精靈來完成。</span><span class="sxs-lookup"><span data-stu-id="baaa1-105">The initial configuration of BAM is done using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard.</span></span> <span data-ttu-id="baaa1-106">使用組態精靈，系統管理員可以：</span><span class="sxs-lookup"><span data-stu-id="baaa1-106">Using the configuration wizard administrators can:</span></span>  
  
-   <span data-ttu-id="baaa1-107">啟用商務活動監控工具</span><span class="sxs-lookup"><span data-stu-id="baaa1-107">Enable Business Activity Monitoring tools</span></span>  
  
-   <span data-ttu-id="baaa1-108">啟用 BAM 彙總的 SQL Server Analysis Services</span><span class="sxs-lookup"><span data-stu-id="baaa1-108">Enable SQL Server Analysis Services for BAM aggregations</span></span>  
  
-   <span data-ttu-id="baaa1-109">指定 BAM 工具所使用的伺服器名稱和資料庫</span><span class="sxs-lookup"><span data-stu-id="baaa1-109">Specify the server name and databases used for BAM tools</span></span>  
  
-   <span data-ttu-id="baaa1-110">啟用 BAM 警示的 SQL Server Notification Services</span><span class="sxs-lookup"><span data-stu-id="baaa1-110">Enable SQL Server Notification Services for BAM alerts</span></span>  
  
-   <span data-ttu-id="baaa1-111">指定用來執行 BAM Notification Service 的帳戶</span><span class="sxs-lookup"><span data-stu-id="baaa1-111">Specify the account used to run the BAM Notification service</span></span>  
  
-   <span data-ttu-id="baaa1-112">指定用來傳送 BAM 警示的 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="baaa1-112">Specify the SMTP server that is used to send BAM alerts</span></span>  
  
-   <span data-ttu-id="baaa1-113">指定用來儲存 BAM 警示的檔案位置</span><span class="sxs-lookup"><span data-stu-id="baaa1-113">Specify the file location used to store BAM alerts</span></span>  
  
-   <span data-ttu-id="baaa1-114">指定的 BAM 警示資料庫的 SQL server 的名稱</span><span class="sxs-lookup"><span data-stu-id="baaa1-114">Specify the name of SQL server on which the BAM alerts databases resides</span></span>  
  
-   <span data-ttu-id="baaa1-115">指定警示資料庫名稱的前置詞</span><span class="sxs-lookup"><span data-stu-id="baaa1-115">Specify the prefix for alerts database names</span></span>  
  
-   <span data-ttu-id="baaa1-116">啟用電腦上的 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="baaa1-116">Enable the BAM portal on a computer</span></span>  
  
-   <span data-ttu-id="baaa1-117">指定用來執行 BAM 入口網站的 Web 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="baaa1-117">Specify the Web service accounts used to run the BAM portal</span></span>  
  
-   <span data-ttu-id="baaa1-118">指定可以存取 BAM 入口網站的 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="baaa1-118">Specify the Windows groups that can access the BAM portal</span></span>  
  
-   <span data-ttu-id="baaa1-119">指定 BAM 入口網站的位置</span><span class="sxs-lookup"><span data-stu-id="baaa1-119">Specify the location of the BAM portal Web site</span></span>  
  
 <span data-ttu-id="baaa1-120">如需有關使用組態精靈的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="baaa1-120">For more information about using the configuration wizard see the following topics:</span></span>  
  
-   [<span data-ttu-id="baaa1-121">使用 BizTalk Server 組態設定 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="baaa1-121">Configuring BAM Alerts Using the BizTalk Server Configuration</span></span>](http://msdn.microsoft.com/library/04d79f8c-9e7f-4ba8-83ce-f79c33fb8e60)  
  
-   [<span data-ttu-id="baaa1-122">使用 BizTalk Server 組態設定 BAM 工具</span><span class="sxs-lookup"><span data-stu-id="baaa1-122">Configuring BAM Tools Using the BizTalk Server Configuration</span></span>](http://msdn.microsoft.com/library/075a1627-5bc2-488c-a88c-42c86cc8c3bb)  
  
-   [<span data-ttu-id="baaa1-123">設定 BAM 入口網站使用 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="baaa1-123">Configuring the BAM Portal Using the BizTalk Server Configuration</span></span>](http://msdn.microsoft.com/library/8af7cccb-823e-48bd-9743-dfbba4bafa11)  
  
### <a name="distributed-notification-services"></a><span data-ttu-id="baaa1-124">分散式 Notification Services</span><span class="sxs-lookup"><span data-stu-id="baaa1-124">Distributed Notification Services</span></span>  
 <span data-ttu-id="baaa1-125">將 BAM 設定在分散式環境中執行，可以在處理警示和通知時提供效能上的好處。</span><span class="sxs-lookup"><span data-stu-id="baaa1-125">Configuring BAM to run in a distributed environment affords performance benefits when processing alerts and notifications.</span></span> <span data-ttu-id="baaa1-126">當您這麼做時，Notification Services 的「提供者」、「產生器」和「散發者」角色會分散在不同的電腦上，因此必須在多部電腦環境中安裝 Notification Services。</span><span class="sxs-lookup"><span data-stu-id="baaa1-126">When you do this, the Provider, Generator, and Distributor roles of Notification Services are on different computers and you must install Notification Services in the multiple computer environment.</span></span>  
  
##### <a name="to-configure-distributed-notification-services"></a><span data-ttu-id="baaa1-127">設定分散式 Notification Services</span><span class="sxs-lookup"><span data-stu-id="baaa1-127">To configure distributed Notification Services</span></span>  
  
1.  <span data-ttu-id="baaa1-128">安裝 [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] Notification Services。</span><span class="sxs-lookup"><span data-stu-id="baaa1-128">Install the [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] Notification Services.</span></span> <span data-ttu-id="baaa1-129">如需有關分散式 Notification Services 的詳細資訊，請參閱[!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)]Notification Services 文件，網址[http://go.microsoft.com/fwlink/?LinkId=68095](http://go.microsoft.com/fwlink/?LinkId=68095)。</span><span class="sxs-lookup"><span data-stu-id="baaa1-129">For more information about Distributed Notification Services, see the [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] Notification Services documentation at [http://go.microsoft.com/fwlink/?LinkId=68095](http://go.microsoft.com/fwlink/?LinkId=68095).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="baaa1-130">[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] 中並未隨附 Notification Services。</span><span class="sxs-lookup"><span data-stu-id="baaa1-130">Notification Services is not included in [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)].</span></span> <span data-ttu-id="baaa1-131">如果您使用[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]，安裝[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Notification Services，當您安裝[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]選取**BAM Alert Provider for SQL Notification Services**選項在**其他軟體**上**元件安裝**安裝精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="baaa1-131">If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], install [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services when you install [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] by selecting the **BAM Alert Provider for SQL Notification Services** option under **Additional Software** on the **Component Installation** page of the installation wizard.</span></span>  
  
2.  <span data-ttu-id="baaa1-132">建立 BAM notification 執行 C:\Program Files\Microsoft SQL Server\90\NotificationServices\9.0.242\bin\nscontrol 在分散式環境中的每一部電腦上服務 register-name bamalerts-server\<伺服器名稱 >-服務-serviceusername \<a >-servicepassword \<passwd > 從命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="baaa1-132">To create the BAM notification service on each computer in the distributed environment run C:\Program Files\Microsoft SQL Server\90\NotificationServices\9.0.242\bin\nscontrol register -name bamalerts -server \<server name> -service -serviceusername \<alertsuseraccount> -servicepassword \<passwd> from a command prompt.</span></span>  
  
3.  <span data-ttu-id="baaa1-133">編輯每一台要設定為提供分散式 Notifications Service 之電腦上的 BAM 基礎結構組態檔。</span><span class="sxs-lookup"><span data-stu-id="baaa1-133">Edit the BAM infrastructure configuration file on each computer being configured for distributed Notifications Serviced.</span></span> <span data-ttu-id="baaa1-134">若要取得組態檔，請使用**bm.exe get-config-FileName:\<輸出檔 >**命令。</span><span class="sxs-lookup"><span data-stu-id="baaa1-134">To get the configuration file, use the **bm.exe get-config -FileName:\<output file>** command.</span></span>  
  
4.  <span data-ttu-id="baaa1-135">編輯組態檔以參考分散式 Notification Services 環境中的伺服器：</span><span class="sxs-lookup"><span data-stu-id="baaa1-135">Edit the configuration file to reference the servers in the distributed Notification services environment:</span></span>  
  
    ```  
    <Property Name="GeneratorServerName">PFIDWYUK</Property>  
    <Property Name="ProviderServerName">PFIDWYUK</Property>  
    <Property Name="DistributorServerName">PFIDWYUK</Property>  
    ```  
  
5.  <span data-ttu-id="baaa1-136">使用 bm.exe 更新-config-FileName:\<組態檔 > 更新 BAM 組態。</span><span class="sxs-lookup"><span data-stu-id="baaa1-136">Use the bm.exe update-config -FileName:\<config file> to update the BAM configuration.</span></span>  
  
6.  <span data-ttu-id="baaa1-137">重新啟動分散式環境中所有電腦上的 Notification Services。</span><span class="sxs-lookup"><span data-stu-id="baaa1-137">Restart the Notification Services on all the computers in the distributed environment.</span></span>  
  
 <span data-ttu-id="baaa1-138">如需有關在多重電腦環境中安裝 BAM 的詳細資訊，請參閱[安裝指南相關的 BizTalk Server 2013](http://go.microsoft.com/fwlink/p/?LinkID=269582)和[安裝及設定 BAM （商務活動監控） 在多部電腦環境](http://go.microsoft.com/fwlink/p/?LinkID=208597)。</span><span class="sxs-lookup"><span data-stu-id="baaa1-138">For more information on installing BAM in a multicomputer environment, see [Installation Guides Related to BizTalk Server 2013](http://go.microsoft.com/fwlink/p/?LinkID=269582) and [Install and Configure BAM (Business Activity Monitoring) in a Multi-Computer Environment](http://go.microsoft.com/fwlink/p/?LinkID=208597).</span></span>  
  
### <a name="moving-the-bam-primary-import-database"></a><span data-ttu-id="baaa1-139">移動 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="baaa1-139">Moving the BAM Primary Import Database</span></span>  
 <span data-ttu-id="baaa1-140">有時候，移動 BAM 主要匯入資料庫是必要的，例如當您升級硬體或進行擴充作業時。</span><span class="sxs-lookup"><span data-stu-id="baaa1-140">At some point it may become necessary to move the BAM Primary Import database, such as when you are upgrading hardware or scaling up operations.</span></span> <span data-ttu-id="baaa1-141">若要移動資料庫，您應該執行備份和還原作業。</span><span class="sxs-lookup"><span data-stu-id="baaa1-141">To move the database you perform a backup and restore operation.</span></span> <span data-ttu-id="baaa1-142">如需此程序的詳細資訊，請參閱[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)。</span><span class="sxs-lookup"><span data-stu-id="baaa1-142">For more information about this process, see [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).</span></span>  
  
### <a name="working-with-bam-definitions"></a><span data-ttu-id="baaa1-143">處理 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="baaa1-143">Working with BAM Definitions</span></span>  
 <span data-ttu-id="baaa1-144">系統管理員經常要處理 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="baaa1-144">Administrators work closely with BAM definitions.</span></span> <span data-ttu-id="baaa1-145">您用來處理 BAM 定義的主要工具是 BAM 管理公用程式。</span><span class="sxs-lookup"><span data-stu-id="baaa1-145">The primary tool you use to work with BAM definitions is the BAM Management utility.</span></span> <span data-ttu-id="baaa1-146">您可以使用這個公用程式來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="baaa1-146">You can perform the following tasks by using this utility:</span></span>  
  
-   <span data-ttu-id="baaa1-147">變更活動。</span><span class="sxs-lookup"><span data-stu-id="baaa1-147">Changing activities.</span></span> <span data-ttu-id="baaa1-148">您可以使用**deploy-all-definitionfile**，**更新所有**，**移除活動**， **set-actvitywindow** BAM 管理公用程式的命令若要變更已部署的活動。</span><span class="sxs-lookup"><span data-stu-id="baaa1-148">You can use the **deploy-all**, **update-all**, **remove-activity**, **and set-actvitywindow** commands of the BAM management utility to change your deployed activities.</span></span>  
  
-   <span data-ttu-id="baaa1-149">將索引套用至活動資料表以增進效能。</span><span class="sxs-lookup"><span data-stu-id="baaa1-149">Applying indexes to activity tables to enhance performance.</span></span> <span data-ttu-id="baaa1-150">您使用**建立索引**和**刪除索引**命令以修改活動的索引。</span><span class="sxs-lookup"><span data-stu-id="baaa1-150">You use the **create-index** and **delete-index** commands to modify the indexes on activities.</span></span>  
  
-   <span data-ttu-id="baaa1-151">設定檢視上的安全性。</span><span class="sxs-lookup"><span data-stu-id="baaa1-151">Setting security on views.</span></span> <span data-ttu-id="baaa1-152">您可以使用**新增帳戶**和**移除帳戶**命令，授與使用者存取檢視的權限。</span><span class="sxs-lookup"><span data-stu-id="baaa1-152">You can use the **add-account** and **remove-account** commands to grant users access rights to views.</span></span>  
  
-   <span data-ttu-id="baaa1-153">設定活動的分散式導覽。</span><span class="sxs-lookup"><span data-stu-id="baaa1-153">Configuring distributed navigation of activities.</span></span> <span data-ttu-id="baaa1-154">您使用**啟用參考**和**停用參考**命令，設定活動的分散式的導覽。</span><span class="sxs-lookup"><span data-stu-id="baaa1-154">You use the **enable-reference** and **disable-reference** commands to configure distributed navigation of activities.</span></span> <span data-ttu-id="baaa1-155">如需活動的分散式導覽的詳細資訊，請參閱[管理分散式導覽的遠端活動](../core/managing-distributed-navigation-of-remote-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="baaa1-155">For more information about the distributed navigation of activities, see [Managing Distributed Navigation of Remote Activities](../core/managing-distributed-navigation-of-remote-activities.md).</span></span>  
  
-   <span data-ttu-id="baaa1-156">稽核變更。</span><span class="sxs-lookup"><span data-stu-id="baaa1-156">Auditing changes.</span></span> <span data-ttu-id="baaa1-157">您可以列出 BAM 動態基礎結構使用變更**get 變更**命令。</span><span class="sxs-lookup"><span data-stu-id="baaa1-157">You can list changes to the BAM dynamic infrastructure using the **get-changes** command.</span></span>  
  
 <span data-ttu-id="baaa1-158">如需可透過 BAM 管理公用程式的所有命令的說明，請參閱[BAM 管理公用程式](../core/bam-management-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="baaa1-158">For a description of all the commands available through the BAM Management utility, see [BAM Management Utility](../core/bam-management-utility.md).</span></span> <span data-ttu-id="baaa1-159">如需使用 BAM 管理公用程式來處理 BAM 定義的範例，請參閱[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)。</span><span class="sxs-lookup"><span data-stu-id="baaa1-159">For examples of using the BAM Management utility to work with BAM definitions, see [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md).</span></span>  
  
## <a name="configuring-multiple-biztalk-groups-to-reference-a-single-bam-database"></a><span data-ttu-id="baaa1-160">設定多個 BizTalk 群組參考單一 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="baaa1-160">Configuring Multiple BizTalk Groups to Reference a Single BAM Database</span></span>  
 <span data-ttu-id="baaa1-161">當設定為使用新的或現有的 BAM[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中，您可以設定要使用相同的 BAM 資料庫已由另一個使用中的群組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。</span><span class="sxs-lookup"><span data-stu-id="baaa1-161">When configuring BAM to use either a new or an existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group, you can configure the group to use the same BAM databases that are already in use by another [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.</span></span>  <span data-ttu-id="baaa1-162">若要以這種方式設定 BAM，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="baaa1-162">To configure BAM in this manner, you must perform the following tasks:</span></span>  
  
-   <span data-ttu-id="baaa1-163">使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態精靈，從現有的 BAM 主要匯入資料庫取得組態資訊。</span><span class="sxs-lookup"><span data-stu-id="baaa1-163">Get the configuration information from the existing BAM Primary Import database using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard.</span></span> <span data-ttu-id="baaa1-164">這包括伺服器及資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="baaa1-164">This includes the server and database names.</span></span> <span data-ttu-id="baaa1-165">記下核取方塊的狀態。</span><span class="sxs-lookup"><span data-stu-id="baaa1-165">Note the state of the check boxes.</span></span> <span data-ttu-id="baaa1-166">請務必要取得「BAM 工具」和「BAM 警示」這兩個頁面的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="baaa1-166">Be sure to get the configuration information for both the BAM Tools and BAM Alerts pages.</span></span>  
  
-   <span data-ttu-id="baaa1-167">為新的群組設定 BAM，並輸入與目標 PIT 所設定的完全相同資訊。</span><span class="sxs-lookup"><span data-stu-id="baaa1-167">Configure BAM for the new group, and enter the exact information as configured already for the target PIT.</span></span> <span data-ttu-id="baaa1-168">為新群組輸入組態資訊時，除了 BAM 警示使用者必須保留空白之外，您將會用到從現有群組收集的所有資訊來設定新群組。</span><span class="sxs-lookup"><span data-stu-id="baaa1-168">When entering the configuration information for the new group you will use all the information collected from the existing group to configure the new group, except the BAM Alerts user, which you must leave blank.</span></span>  
  
## <a name="backing-up-and-restoring-bam"></a><span data-ttu-id="baaa1-169">Backing Up and Restoring BAM</span><span class="sxs-lookup"><span data-stu-id="baaa1-169">Backing Up and Restoring BAM</span></span>  
 <span data-ttu-id="baaa1-170">系統管理員應該為損毀修復狀況進行規劃。</span><span class="sxs-lookup"><span data-stu-id="baaa1-170">Administrators should plan for disaster recovery situations.</span></span> <span data-ttu-id="baaa1-171">您應該備份 BAM 分析、追蹤分析、BAM 星狀結構描述、BAM 封存和 BAM 主要匯入資料庫，以便在必須還原的狀況下使用。</span><span class="sxs-lookup"><span data-stu-id="baaa1-171">You should back up the BAM Analysis, Tracking Analysis, BAM Star Schema, BAM Archive, and BAM Primary Import databases to provide for situations in which you must restore them.</span></span>  <span data-ttu-id="baaa1-172">如需備份和還原 BAM 資料庫的資訊，請參閱[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)。</span><span class="sxs-lookup"><span data-stu-id="baaa1-172">For information about backing up and restoring the BAM databases, see [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).</span></span>  
  
## <a name="working-with-renamed-servers"></a><span data-ttu-id="baaa1-173">使用重新命名的伺服器</span><span class="sxs-lookup"><span data-stu-id="baaa1-173">Working with Renamed Servers</span></span>  
 <span data-ttu-id="baaa1-174">當您重新命名伺服器，或在伺服器之間移動 BAM 基礎結構時，就必須更新 Excel 活頁簿中的 BAM 定義以便更新該 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="baaa1-174">When you rename a server or move the BAM infrastructure between servers, you must update the Excel workbook by updating the BAM definitions in that workbook.</span></span>  
  
 <span data-ttu-id="baaa1-175">您需要更新活頁簿的情況包括：</span><span class="sxs-lookup"><span data-stu-id="baaa1-175">The scenarios in which you would need to update the workbook include:</span></span>  
  
-   <span data-ttu-id="baaa1-176">將 BAM 基礎結構移動到新資料庫的臨時情況。</span><span class="sxs-lookup"><span data-stu-id="baaa1-176">A staging scenario, in which you move the BAM infrastructure to a new database.</span></span> <span data-ttu-id="baaa1-177">為了確保 Excel 活頁簿繼續正常運作，您必須重新部署或移轉活頁簿，然後重新更新活頁簿。</span><span class="sxs-lookup"><span data-stu-id="baaa1-177">To ensure that the Excel workbooks are still functional, you must redeploy or migrate and then re-update the workbooks.</span></span>  
  
-   <span data-ttu-id="baaa1-178">重新命名執行 BizTalk Server 之電腦的情況。</span><span class="sxs-lookup"><span data-stu-id="baaa1-178">A scenario in which you rename the computer running BizTalk Server.</span></span> <span data-ttu-id="baaa1-179">除了更新活頁簿之外，這個情況還需要更新 DTS 封裝和 OLAP 資料來源。</span><span class="sxs-lookup"><span data-stu-id="baaa1-179">This requires updating the DTS packages and OLAP data source in addition to updating the workbook.</span></span>  
  
 <span data-ttu-id="baaa1-180">您可以用二個方法來更新 Excel 活頁簿：</span><span class="sxs-lookup"><span data-stu-id="baaa1-180">There are two approaches you can use to update the Excel workbook:</span></span>  
  
-   <span data-ttu-id="baaa1-181">從新的伺服器執行下列 BAM 管理員命令：</span><span class="sxs-lookup"><span data-stu-id="baaa1-181">Run the following BAM Manager command from the new server:</span></span>  
  
     <span data-ttu-id="baaa1-182">**bm.exe 更新 livedataworkbook-Name:\<update.xls 即時資料活頁簿 >**</span><span class="sxs-lookup"><span data-stu-id="baaa1-182">**bm.exe update-livedataworkbook -Name:\<livedata workbook to update.xls>**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="baaa1-183">您也可以指定新的伺服器名稱和/或 BAM 主要匯入資料庫名稱： **bm.exe 更新 livedataworkbook-名稱：\<update.xls 即時資料活頁簿 > [-Server:\<伺服器 >] [-資料庫：\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="baaa1-183">You can also specify the new server name and/or BAM Primary Import database name: **bm.exe update-livedataworkbook -Name:\<livedata workbook to update.xls> [-Server:\<server>] [-Database:\<database>]**</span></span>  
  
-   <span data-ttu-id="baaa1-184">或者，您也可以更新 Excel 中的 Excel 活頁簿：</span><span class="sxs-lookup"><span data-stu-id="baaa1-184">Alternatively, you can update the Excel workbook from within Excel:</span></span>  
  
    1.  <span data-ttu-id="baaa1-185">開啟您要更新的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="baaa1-185">Open the workbook you want to update.</span></span>  
  
    2.  <span data-ttu-id="baaa1-186">從 BAM 功能表按一下  **BAM Db 連線**。</span><span class="sxs-lookup"><span data-stu-id="baaa1-186">From the BAM menu, click **BAM Db Connection**.</span></span>  
  
    3.  <span data-ttu-id="baaa1-187">輸入新的伺服器名稱 和 BAM 主要匯入資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="baaa1-187">Enter the new server name and BAM Primary Import database name.</span></span>  
  
## <a name="managing-alerts"></a><span data-ttu-id="baaa1-188">管理警示</span><span class="sxs-lookup"><span data-stu-id="baaa1-188">Managing Alerts</span></span>  
 <span data-ttu-id="baaa1-189">系統管理員管理警示的方式有數種：</span><span class="sxs-lookup"><span data-stu-id="baaa1-189">Administrators can manage alerts in a several ways:</span></span>  
  
 <span data-ttu-id="baaa1-190">您可以使用 BAM 管理公用程式進行部署和移除警示。</span><span class="sxs-lookup"><span data-stu-id="baaa1-190">You can use the BAM Management utility to deploy and remove alerts.</span></span> <span data-ttu-id="baaa1-191">您也可以使用公用程式來新增和移除訂閱，以及啟用和停用警示。</span><span class="sxs-lookup"><span data-stu-id="baaa1-191">You can also use the utility to add and remove subscriptions, as well as to enable and disable alerts.</span></span> <span data-ttu-id="baaa1-192">如需有關如何使用 BAM 管理公用程式的詳細資訊，請參閱[BAM 管理公用程式](../core/bam-management-utility.md)，[管理 BAM 安全性](../core/managing-bam-security.md)，和[管理 BAM 定義](../core/managing-bam-definitions.md)。</span><span class="sxs-lookup"><span data-stu-id="baaa1-192">For more information about using the BAM Management utility, see [BAM Management Utility](../core/bam-management-utility.md), [Managing BAM Security](../core/managing-bam-security.md), and [Managing BAM Definitions](../core/managing-bam-definitions.md).</span></span>  
  
 <span data-ttu-id="baaa1-193">您也可以透過 BAM 入口網站建立和移除警示。</span><span class="sxs-lookup"><span data-stu-id="baaa1-193">You can also create and remove alerts through the BAM portal.</span></span>  <span data-ttu-id="baaa1-194">建立使用 BAM 入口網站的警示的詳細資訊，請參閱[BAM 入口網站中的活動搜尋](../core/activity-searches-in-the-bam-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="baaa1-194">For information about creating alerts using the BAM portal, see [Activity Searches in the BAM Portal](../core/activity-searches-in-the-bam-portal.md).</span></span>  
  
### <a name="cleaning-up-the-alerts-chronicle-table"></a><span data-ttu-id="baaa1-195">清除警示紀事輯資料表</span><span class="sxs-lookup"><span data-stu-id="baaa1-195">Cleaning up the Alerts Chronicle table</span></span>  
 <span data-ttu-id="baaa1-196">如果已設定 BAM 警示，就會為所建立的每個活動檢視建立 SQL 作業。</span><span class="sxs-lookup"><span data-stu-id="baaa1-196">If BAM alerts are configured, a SQL job is created for each activity view that is created.</span></span> <span data-ttu-id="baaa1-197">使用下列範例將會為作業命名：</span><span class="sxs-lookup"><span data-stu-id="baaa1-197">The job will be named using the following template:</span></span>  
  
 <span data-ttu-id="baaa1-198">bam_\<檢視名稱 > _\<活動檢視 > _DelAlertHistJob</span><span class="sxs-lookup"><span data-stu-id="baaa1-198">bam_\<View Name>_\<Activity View>_DelAlertHistJob</span></span>  
  
 <span data-ttu-id="baaa1-199">這個工作會清除稽核資料所指定的執行個體警示\<活動檢視 > Bam_Metadata_AlertChronicle 資料表中。</span><span class="sxs-lookup"><span data-stu-id="baaa1-199">This job cleans up auditing data for the instance alerts for the specified \<Activity View> in the Bam_Metadata_AlertChronicle table.</span></span> <span data-ttu-id="baaa1-200">如果您已經在特定的活動檢視上定義執行個體警示，則每次引發警示，此資料表就會新增新的資料列。</span><span class="sxs-lookup"><span data-stu-id="baaa1-200">If you have defined instance alerts on the particular activity view, a new row will be added to this table every time the alert is fired.</span></span>  
  
 <span data-ttu-id="baaa1-201">您可以手動執行這項作業，以清除資料表，或根據應用程式或環境的需求排程作業的執行時間。</span><span class="sxs-lookup"><span data-stu-id="baaa1-201">You can run this job manually to clean up the table or schedule it to run according to the need of your application or environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baaa1-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baaa1-202">See Also</span></span>  
 [<span data-ttu-id="baaa1-203">管理 BAM</span><span class="sxs-lookup"><span data-stu-id="baaa1-203">Managing BAM</span></span>](../core/managing-bam.md)