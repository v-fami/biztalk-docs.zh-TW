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
ms.openlocfilehash: 1b35585d4e3b3ed90df983c8a18f6833ce8aa6bf
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="bam-tasks-for-administrators"></a><span data-ttu-id="f42d8-102">系統管理員的 BAM 工作</span><span class="sxs-lookup"><span data-stu-id="f42d8-102">BAM Tasks for Administrators</span></span>
<span data-ttu-id="f42d8-103">這個主題說明 BAM 系統管理員在管理 BAM 基礎結構時從事的一般工作。</span><span class="sxs-lookup"><span data-stu-id="f42d8-103">This topic describes typical tasks that BAM administrators undertake in managing the BAM infrastructure.</span></span>  
  
## <a name="configuring-bam"></a><span data-ttu-id="f42d8-104">設定 BAM</span><span class="sxs-lookup"><span data-stu-id="f42d8-104">Configuring BAM</span></span>  
 <span data-ttu-id="f42d8-105">BAM 的初始組態是使用 BizTalk Server 組態精靈。</span><span class="sxs-lookup"><span data-stu-id="f42d8-105">The initial configuration of BAM is done using the BizTalk Server Configuration Wizard.</span></span> <span data-ttu-id="f42d8-106">使用組態精靈，系統管理員可以：</span><span class="sxs-lookup"><span data-stu-id="f42d8-106">Using the configuration wizard administrators can:</span></span>  
  
-   <span data-ttu-id="f42d8-107">啟用商務活動監控工具</span><span class="sxs-lookup"><span data-stu-id="f42d8-107">Enable Business Activity Monitoring tools</span></span>  
  
-   <span data-ttu-id="f42d8-108">啟用 BAM 彙總的 SQL Server Analysis Services</span><span class="sxs-lookup"><span data-stu-id="f42d8-108">Enable SQL Server Analysis Services for BAM aggregations</span></span>  
  
-   <span data-ttu-id="f42d8-109">指定 BAM 工具所使用的伺服器名稱和資料庫</span><span class="sxs-lookup"><span data-stu-id="f42d8-109">Specify the server name and databases used for BAM tools</span></span>  
  
-   <span data-ttu-id="f42d8-110">啟用 BAM 警示的 SQL Server Notification Services</span><span class="sxs-lookup"><span data-stu-id="f42d8-110">Enable SQL Server Notification Services for BAM alerts</span></span>  
  
-   <span data-ttu-id="f42d8-111">指定用來執行 BAM Notification Service 的帳戶</span><span class="sxs-lookup"><span data-stu-id="f42d8-111">Specify the account used to run the BAM Notification service</span></span>  
  
-   <span data-ttu-id="f42d8-112">指定用來傳送 BAM 警示的 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="f42d8-112">Specify the SMTP server that is used to send BAM alerts</span></span>  
  
-   <span data-ttu-id="f42d8-113">指定用來儲存 BAM 警示的檔案位置</span><span class="sxs-lookup"><span data-stu-id="f42d8-113">Specify the file location used to store BAM alerts</span></span>  
  
-   <span data-ttu-id="f42d8-114">指定的 BAM 警示資料庫的 SQL server 的名稱</span><span class="sxs-lookup"><span data-stu-id="f42d8-114">Specify the name of SQL server on which the BAM alerts databases resides</span></span>  
  
-   <span data-ttu-id="f42d8-115">指定警示資料庫名稱的前置詞</span><span class="sxs-lookup"><span data-stu-id="f42d8-115">Specify the prefix for alerts database names</span></span>  
  
-   <span data-ttu-id="f42d8-116">啟用電腦上的 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="f42d8-116">Enable the BAM portal on a computer</span></span>  
  
-   <span data-ttu-id="f42d8-117">指定用來執行 BAM 入口網站的 Web 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="f42d8-117">Specify the Web service accounts used to run the BAM portal</span></span>  
  
-   <span data-ttu-id="f42d8-118">指定可以存取 BAM 入口網站的 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="f42d8-118">Specify the Windows groups that can access the BAM portal</span></span>  
  
-   <span data-ttu-id="f42d8-119">指定 BAM 入口網站的位置</span><span class="sxs-lookup"><span data-stu-id="f42d8-119">Specify the location of the BAM portal Web site</span></span>  
  
 <span data-ttu-id="f42d8-120">如需有關使用組態精靈的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="f42d8-120">For more information about using the configuration wizard see the following topics:</span></span>  
  
-   [<span data-ttu-id="f42d8-121">設定 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="f42d8-121">Configure BAM Alerts</span></span>](../install-and-config-guides/configure-biztalk-server.md)  
  
-   [<span data-ttu-id="f42d8-122">設定 BAM 工具</span><span class="sxs-lookup"><span data-stu-id="f42d8-122">Configure BAM Tools</span></span>](../install-and-config-guides/configure-biztalk-server.md)  
  
-   [<span data-ttu-id="f42d8-123">設定 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="f42d8-123">Configure the BAM Portal</span></span>](../install-and-config-guides/configure-biztalk-server.md)  
  
### <a name="distributed-notification-services---sql-server-2008-r2-only"></a><span data-ttu-id="f42d8-124">分散式的 Notification Services-僅限 SQL Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="f42d8-124">Distributed Notification Services - SQL Server 2008 R2 only</span></span>
<span data-ttu-id="f42d8-125">將 BAM 設定在分散式環境中執行，可以在處理警示和通知時提供效能上的好處。</span><span class="sxs-lookup"><span data-stu-id="f42d8-125">Configuring BAM to run in a distributed environment affords performance benefits when processing alerts and notifications.</span></span> <span data-ttu-id="f42d8-126">當您這麼做時，Notification Services 的「提供者」、「產生器」和「散發者」角色會分散在不同的電腦上，因此必須在多部電腦環境中安裝 Notification Services。</span><span class="sxs-lookup"><span data-stu-id="f42d8-126">When you do this, the Provider, Generator, and Distributor roles of Notification Services are on different computers and you must install Notification Services in the multiple computer environment.</span></span>  

> [!NOTE]
> <span data-ttu-id="f42d8-127">從 SQL Server 2012 開始，BizTalk Server 使用 SQL Database Mail。</span><span class="sxs-lookup"><span data-stu-id="f42d8-127">Starting with SQL Server 2012, BizTalk Server uses SQL Database Mail.</span></span> <span data-ttu-id="f42d8-128">因此，如果您使用 SQL Server 2012 或更新版本，這不適用於您。</span><span class="sxs-lookup"><span data-stu-id="f42d8-128">So if you're using SQL Server 2012 or newer, this does not apply to you.</span></span> <span data-ttu-id="f42d8-129">請參閱[BAM 警示](../install-and-config-guides/prepare-your-computer-for-installation.md#BKMK_BAMAlerts)指導方針。</span><span class="sxs-lookup"><span data-stu-id="f42d8-129">See [BAM Alerts](../install-and-config-guides/prepare-your-computer-for-installation.md#BKMK_BAMAlerts) for guidance.</span></span>
  
##### <a name="to-configure-distributed-notification-services"></a><span data-ttu-id="f42d8-130">設定分散式 Notification Services</span><span class="sxs-lookup"><span data-stu-id="f42d8-130">To configure distributed Notification Services</span></span>  
  
1.  <span data-ttu-id="f42d8-131">安裝 SQL Server Notification Services。</span><span class="sxs-lookup"><span data-stu-id="f42d8-131">Install SQL Server Notification Services.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="f42d8-132">Notification Services 不包含 SQL Server 中。</span><span class="sxs-lookup"><span data-stu-id="f42d8-132">Notification Services is not included in SQL Server.</span></span> <span data-ttu-id="f42d8-133">當您安裝 BizTalk Server 時選取安裝 SQL Server Notification Services **BAM Alert Provider for SQL Notification Services**選項在**其他軟體**上**元件安裝**安裝精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="f42d8-133">Install SQL Server Notification Services when you install BizTalk Server by selecting the **BAM Alert Provider for SQL Notification Services** option under **Additional Software** on the **Component Installation** page of the installation wizard.</span></span>  
  
2.  <span data-ttu-id="f42d8-134">建立 BAM notification 執行 C:\Program Files\Microsoft SQL Server\90\NotificationServices\9.0.242\bin\nscontrol 在分散式環境中的每一部電腦上服務 register-name bamalerts-server\<伺服器名稱\>-服務-serviceusername \<a\> -servicepassword \<passwd\>從命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f42d8-134">To create the BAM notification service on each computer in the distributed environment run C:\Program Files\Microsoft SQL Server\90\NotificationServices\9.0.242\bin\nscontrol register -name bamalerts -server \<server name\> -service -serviceusername \<alertsuseraccount\> -servicepassword \<passwd\> from a command prompt.</span></span>  
  
3.  <span data-ttu-id="f42d8-135">編輯每一台要設定為提供分散式 Notifications Service 之電腦上的 BAM 基礎結構組態檔。</span><span class="sxs-lookup"><span data-stu-id="f42d8-135">Edit the BAM infrastructure configuration file on each computer being configured for distributed Notifications Serviced.</span></span> <span data-ttu-id="f42d8-136">若要取得組態檔，請使用**bm.exe get-config-FileName:\<輸出檔\>**命令。</span><span class="sxs-lookup"><span data-stu-id="f42d8-136">To get the configuration file, use the **bm.exe get-config -FileName:\<output file\>** command.</span></span>  
  
4.  <span data-ttu-id="f42d8-137">編輯組態檔以參考分散式 Notification Services 環境中的伺服器：</span><span class="sxs-lookup"><span data-stu-id="f42d8-137">Edit the configuration file to reference the servers in the distributed Notification services environment:</span></span>  
  
    ```  
    <Property Name="GeneratorServerName">PFIDWYUK</Property>  
    <Property Name="ProviderServerName">PFIDWYUK</Property>  
    <Property Name="DistributorServerName">PFIDWYUK</Property>  
    ```  
  
5.  <span data-ttu-id="f42d8-138">使用 bm.exe 更新-config-FileName:\<組態檔\>更新 BAM 組態。</span><span class="sxs-lookup"><span data-stu-id="f42d8-138">Use the bm.exe update-config -FileName:\<config file\> to update the BAM configuration.</span></span>  
  
6.  <span data-ttu-id="f42d8-139">重新啟動分散式環境中所有電腦上的 Notification Services。</span><span class="sxs-lookup"><span data-stu-id="f42d8-139">Restart the Notification Services on all the computers in the distributed environment.</span></span>  
  
 <span data-ttu-id="f42d8-140">如需有關在多重電腦環境中安裝 BAM 的詳細資訊，請參閱[安裝及設定 BAM （商務活動監控） 在多重電腦環境中](http://go.microsoft.com/fwlink/p/?LinkID=208597)。</span><span class="sxs-lookup"><span data-stu-id="f42d8-140">For more information on installing BAM in a multicomputer environment, see [Install and Configure BAM (Business Activity Monitoring) in a Multi-Computer Environment](http://go.microsoft.com/fwlink/p/?LinkID=208597).</span></span>  
  
### <a name="moving-the-bam-primary-import-database"></a><span data-ttu-id="f42d8-141">移動 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="f42d8-141">Moving the BAM Primary Import Database</span></span>  
 <span data-ttu-id="f42d8-142">有時候，移動 BAM 主要匯入資料庫是必要的，例如當您升級硬體或進行擴充作業時。</span><span class="sxs-lookup"><span data-stu-id="f42d8-142">At some point it may become necessary to move the BAM Primary Import database, such as when you are upgrading hardware or scaling up operations.</span></span> <span data-ttu-id="f42d8-143">若要移動資料庫，您應該執行備份和還原作業。</span><span class="sxs-lookup"><span data-stu-id="f42d8-143">To move the database you perform a backup and restore operation.</span></span> <span data-ttu-id="f42d8-144">如需此程序的詳細資訊，請參閱[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)。</span><span class="sxs-lookup"><span data-stu-id="f42d8-144">For more information about this process, see [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).</span></span>  
  
### <a name="working-with-bam-definitions"></a><span data-ttu-id="f42d8-145">處理 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="f42d8-145">Working with BAM Definitions</span></span>  
 <span data-ttu-id="f42d8-146">系統管理員經常要處理 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="f42d8-146">Administrators work closely with BAM definitions.</span></span> <span data-ttu-id="f42d8-147">您用來處理 BAM 定義的主要工具是 BAM 管理公用程式。</span><span class="sxs-lookup"><span data-stu-id="f42d8-147">The primary tool you use to work with BAM definitions is the BAM Management utility.</span></span> <span data-ttu-id="f42d8-148">您可以使用這個公用程式來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f42d8-148">You can perform the following tasks by using this utility:</span></span>  
  
-   <span data-ttu-id="f42d8-149">變更活動。</span><span class="sxs-lookup"><span data-stu-id="f42d8-149">Changing activities.</span></span> <span data-ttu-id="f42d8-150">您可以使用**deploy-all-definitionfile**，**更新所有**，**移除活動**， **set-actvitywindow** BAM 管理公用程式的命令若要變更已部署的活動。</span><span class="sxs-lookup"><span data-stu-id="f42d8-150">You can use the **deploy-all**, **update-all**, **remove-activity**, **and set-actvitywindow** commands of the BAM management utility to change your deployed activities.</span></span>  
  
-   <span data-ttu-id="f42d8-151">將索引套用至活動資料表以增進效能。</span><span class="sxs-lookup"><span data-stu-id="f42d8-151">Applying indexes to activity tables to enhance performance.</span></span> <span data-ttu-id="f42d8-152">您使用**建立索引**和**刪除索引**命令以修改活動的索引。</span><span class="sxs-lookup"><span data-stu-id="f42d8-152">You use the **create-index** and **delete-index** commands to modify the indexes on activities.</span></span>  
  
-   <span data-ttu-id="f42d8-153">設定檢視上的安全性。</span><span class="sxs-lookup"><span data-stu-id="f42d8-153">Setting security on views.</span></span> <span data-ttu-id="f42d8-154">您可以使用**新增帳戶**和**移除帳戶**命令，授與使用者存取檢視的權限。</span><span class="sxs-lookup"><span data-stu-id="f42d8-154">You can use the **add-account** and **remove-account** commands to grant users access rights to views.</span></span>  
  
-   <span data-ttu-id="f42d8-155">設定活動的分散式導覽。</span><span class="sxs-lookup"><span data-stu-id="f42d8-155">Configuring distributed navigation of activities.</span></span> <span data-ttu-id="f42d8-156">您使用**啟用參考**和**停用參考**命令，設定活動的分散式的導覽。</span><span class="sxs-lookup"><span data-stu-id="f42d8-156">You use the **enable-reference** and **disable-reference** commands to configure distributed navigation of activities.</span></span> <span data-ttu-id="f42d8-157">如需活動的分散式導覽的詳細資訊，請參閱[管理分散式導覽的遠端活動](../core/managing-distributed-navigation-of-remote-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="f42d8-157">For more information about the distributed navigation of activities, see [Managing Distributed Navigation of Remote Activities](../core/managing-distributed-navigation-of-remote-activities.md).</span></span>  
  
-   <span data-ttu-id="f42d8-158">稽核變更。</span><span class="sxs-lookup"><span data-stu-id="f42d8-158">Auditing changes.</span></span> <span data-ttu-id="f42d8-159">您可以列出 BAM 動態基礎結構使用變更**get 變更**命令。</span><span class="sxs-lookup"><span data-stu-id="f42d8-159">You can list changes to the BAM dynamic infrastructure using the **get-changes** command.</span></span>  
  
 <span data-ttu-id="f42d8-160">如需可透過 BAM 管理公用程式的所有命令的說明，請參閱[BAM 管理公用程式](../core/bam-management-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="f42d8-160">For a description of all the commands available through the BAM Management utility, see [BAM Management Utility](../core/bam-management-utility.md).</span></span> <span data-ttu-id="f42d8-161">如需使用 BAM 管理公用程式來處理 BAM 定義的範例，請參閱[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)。</span><span class="sxs-lookup"><span data-stu-id="f42d8-161">For examples of using the BAM Management utility to work with BAM definitions, see [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md).</span></span>  
  
## <a name="configuring-multiple-biztalk-groups-to-reference-a-single-bam-database"></a><span data-ttu-id="f42d8-162">設定多個 BizTalk 群組參考單一 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="f42d8-162">Configuring Multiple BizTalk Groups to Reference a Single BAM Database</span></span>  
 <span data-ttu-id="f42d8-163">當設定 BAM 使用新的或現有的 BizTalk Server 群組，您可以設定要使用已在另一個 BizTalk Server 群組所使用的相同 BAM 資料庫的群組。</span><span class="sxs-lookup"><span data-stu-id="f42d8-163">When configuring BAM to use either a new or an existing BizTalk Server group, you can configure the group to use the same BAM databases that are already in use by another BizTalk Server group.</span></span>  <span data-ttu-id="f42d8-164">若要以這種方式設定 BAM，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f42d8-164">To configure BAM in this manner, you must perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f42d8-165">取得組態資訊從現有的 BAM 主要匯入資料庫使用 BizTalk Server 組態精靈。</span><span class="sxs-lookup"><span data-stu-id="f42d8-165">Get the configuration information from the existing BAM Primary Import database using the BizTalk Server Configuration Wizard.</span></span> <span data-ttu-id="f42d8-166">這包括伺服器及資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f42d8-166">This includes the server and database names.</span></span> <span data-ttu-id="f42d8-167">記下核取方塊的狀態。</span><span class="sxs-lookup"><span data-stu-id="f42d8-167">Note the state of the check boxes.</span></span> <span data-ttu-id="f42d8-168">請務必要取得「BAM 工具」和「BAM 警示」這兩個頁面的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="f42d8-168">Be sure to get the configuration information for both the BAM Tools and BAM Alerts pages.</span></span>  
  
-   <span data-ttu-id="f42d8-169">為新的群組設定 BAM，並輸入與目標 PIT 所設定的完全相同資訊。</span><span class="sxs-lookup"><span data-stu-id="f42d8-169">Configure BAM for the new group, and enter the exact information as configured already for the target PIT.</span></span> <span data-ttu-id="f42d8-170">為新群組輸入組態資訊時，除了 BAM 警示使用者必須保留空白之外，您將會用到從現有群組收集的所有資訊來設定新群組。</span><span class="sxs-lookup"><span data-stu-id="f42d8-170">When entering the configuration information for the new group you will use all the information collected from the existing group to configure the new group, except the BAM Alerts user, which you must leave blank.</span></span>  
  
## <a name="backing-up-and-restoring-bam"></a><span data-ttu-id="f42d8-171">Backing Up and Restoring BAM</span><span class="sxs-lookup"><span data-stu-id="f42d8-171">Backing Up and Restoring BAM</span></span>  
 <span data-ttu-id="f42d8-172">系統管理員應該為損毀修復狀況進行規劃。</span><span class="sxs-lookup"><span data-stu-id="f42d8-172">Administrators should plan for disaster recovery situations.</span></span> <span data-ttu-id="f42d8-173">您應該備份 BAM 分析、追蹤分析、BAM 星狀結構描述、BAM 封存和 BAM 主要匯入資料庫，以便在必須還原的狀況下使用。</span><span class="sxs-lookup"><span data-stu-id="f42d8-173">You should back up the BAM Analysis, Tracking Analysis, BAM Star Schema, BAM Archive, and BAM Primary Import databases to provide for situations in which you must restore them.</span></span>  <span data-ttu-id="f42d8-174">如需備份和還原 BAM 資料庫的資訊，請參閱[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)。</span><span class="sxs-lookup"><span data-stu-id="f42d8-174">For information about backing up and restoring the BAM databases, see [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).</span></span>  
  
## <a name="working-with-renamed-servers"></a><span data-ttu-id="f42d8-175">使用重新命名的伺服器</span><span class="sxs-lookup"><span data-stu-id="f42d8-175">Working with Renamed Servers</span></span>  
 <span data-ttu-id="f42d8-176">當您重新命名伺服器，或在伺服器之間移動 BAM 基礎結構時，就必須更新 Excel 活頁簿中的 BAM 定義以便更新該 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="f42d8-176">When you rename a server or move the BAM infrastructure between servers, you must update the Excel workbook by updating the BAM definitions in that workbook.</span></span>  
  
 <span data-ttu-id="f42d8-177">您需要更新活頁簿的情況包括：</span><span class="sxs-lookup"><span data-stu-id="f42d8-177">The scenarios in which you would need to update the workbook include:</span></span>  
  
-   <span data-ttu-id="f42d8-178">將 BAM 基礎結構移動到新資料庫的臨時情況。</span><span class="sxs-lookup"><span data-stu-id="f42d8-178">A staging scenario, in which you move the BAM infrastructure to a new database.</span></span> <span data-ttu-id="f42d8-179">為了確保 Excel 活頁簿繼續正常運作，您必須重新部署或移轉活頁簿，然後重新更新活頁簿。</span><span class="sxs-lookup"><span data-stu-id="f42d8-179">To ensure that the Excel workbooks are still functional, you must redeploy or migrate and then re-update the workbooks.</span></span>  
  
-   <span data-ttu-id="f42d8-180">重新命名執行 BizTalk Server 之電腦的情況。</span><span class="sxs-lookup"><span data-stu-id="f42d8-180">A scenario in which you rename the computer running BizTalk Server.</span></span> <span data-ttu-id="f42d8-181">除了更新活頁簿之外，這個情況還需要更新 DTS 封裝和 OLAP 資料來源。</span><span class="sxs-lookup"><span data-stu-id="f42d8-181">This requires updating the DTS packages and OLAP data source in addition to updating the workbook.</span></span>  
  
 <span data-ttu-id="f42d8-182">您可以用二個方法來更新 Excel 活頁簿：</span><span class="sxs-lookup"><span data-stu-id="f42d8-182">There are two approaches you can use to update the Excel workbook:</span></span>  
  
-   <span data-ttu-id="f42d8-183">從新的伺服器執行下列 BAM 管理員命令：</span><span class="sxs-lookup"><span data-stu-id="f42d8-183">Run the following BAM Manager command from the new server:</span></span>  
  
     <span data-ttu-id="f42d8-184">**bm.exe 更新 livedataworkbook-Name:\<update.xls 即時資料活頁簿\>**</span><span class="sxs-lookup"><span data-stu-id="f42d8-184">**bm.exe update-livedataworkbook -Name:\<livedata workbook to update.xls\>**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f42d8-185">您也可以指定新的伺服器名稱和/或 BAM 主要匯入資料庫名稱： **bm.exe 更新 livedataworkbook-Name:\<update.xls 即時資料活頁簿\>[-Server:\<伺服器\>] [-資料庫：\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="f42d8-185">You can also specify the new server name and/or BAM Primary Import database name: **bm.exe update-livedataworkbook -Name:\<livedata workbook to update.xls\> [-Server:\<server\>] [-Database:\<database\>]**</span></span>  
  
-   <span data-ttu-id="f42d8-186">或者，您也可以更新 Excel 中的 Excel 活頁簿：</span><span class="sxs-lookup"><span data-stu-id="f42d8-186">Alternatively, you can update the Excel workbook from within Excel:</span></span>  
  
    1.  <span data-ttu-id="f42d8-187">開啟您要更新的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="f42d8-187">Open the workbook you want to update.</span></span>  
  
    2.  <span data-ttu-id="f42d8-188">從 BAM 功能表按一下  **BAM Db 連線**。</span><span class="sxs-lookup"><span data-stu-id="f42d8-188">From the BAM menu, click **BAM Db Connection**.</span></span>  
  
    3.  <span data-ttu-id="f42d8-189">輸入新的伺服器名稱 和 BAM 主要匯入資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f42d8-189">Enter the new server name and BAM Primary Import database name.</span></span>  
  
## <a name="managing-alerts"></a><span data-ttu-id="f42d8-190">管理警示</span><span class="sxs-lookup"><span data-stu-id="f42d8-190">Managing Alerts</span></span>  
 <span data-ttu-id="f42d8-191">系統管理員管理警示的方式有數種：</span><span class="sxs-lookup"><span data-stu-id="f42d8-191">Administrators can manage alerts in a several ways:</span></span>  
  
 <span data-ttu-id="f42d8-192">您可以使用 BAM 管理公用程式進行部署和移除警示。</span><span class="sxs-lookup"><span data-stu-id="f42d8-192">You can use the BAM Management utility to deploy and remove alerts.</span></span> <span data-ttu-id="f42d8-193">您也可以使用公用程式來新增和移除訂閱，以及啟用和停用警示。</span><span class="sxs-lookup"><span data-stu-id="f42d8-193">You can also use the utility to add and remove subscriptions, as well as to enable and disable alerts.</span></span> <span data-ttu-id="f42d8-194">如需有關如何使用 BAM 管理公用程式的詳細資訊，請參閱[BAM 管理公用程式](../core/bam-management-utility.md)，[管理 BAM 安全性](../core/managing-bam-security.md)，和[管理 BAM 定義](../core/managing-bam-definitions.md)。</span><span class="sxs-lookup"><span data-stu-id="f42d8-194">For more information about using the BAM Management utility, see [BAM Management Utility](../core/bam-management-utility.md), [Managing BAM Security](../core/managing-bam-security.md), and [Managing BAM Definitions](../core/managing-bam-definitions.md).</span></span>  
  
 <span data-ttu-id="f42d8-195">您也可以透過 BAM 入口網站建立和移除警示。</span><span class="sxs-lookup"><span data-stu-id="f42d8-195">You can also create and remove alerts through the BAM portal.</span></span>  <span data-ttu-id="f42d8-196">建立使用 BAM 入口網站的警示的詳細資訊，請參閱[BAM 入口網站中的活動搜尋](../core/activity-searches-in-the-bam-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="f42d8-196">For information about creating alerts using the BAM portal, see [Activity Searches in the BAM Portal](../core/activity-searches-in-the-bam-portal.md).</span></span>  
  
### <a name="cleaning-up-the-alerts-chronicle-table"></a><span data-ttu-id="f42d8-197">清除警示紀事輯資料表</span><span class="sxs-lookup"><span data-stu-id="f42d8-197">Cleaning up the Alerts Chronicle table</span></span>  
 <span data-ttu-id="f42d8-198">如果已設定 BAM 警示，就會為所建立的每個活動檢視建立 SQL 作業。</span><span class="sxs-lookup"><span data-stu-id="f42d8-198">If BAM alerts are configured, a SQL job is created for each activity view that is created.</span></span> <span data-ttu-id="f42d8-199">使用下列範例將會為作業命名：</span><span class="sxs-lookup"><span data-stu-id="f42d8-199">The job will be named using the following template:</span></span>  
  
 <span data-ttu-id="f42d8-200">bam_\<檢視名稱\>_\<活動檢視\>_DelAlertHistJob</span><span class="sxs-lookup"><span data-stu-id="f42d8-200">bam_\<View Name\>_\<Activity View\>_DelAlertHistJob</span></span>  
  
 <span data-ttu-id="f42d8-201">這個工作會清除稽核資料所指定的執行個體警示\<活動檢視\>Bam_Metadata_AlertChronicle 資料表中。</span><span class="sxs-lookup"><span data-stu-id="f42d8-201">This job cleans up auditing data for the instance alerts for the specified \<Activity View\> in the Bam_Metadata_AlertChronicle table.</span></span> <span data-ttu-id="f42d8-202">如果您已經在特定的活動檢視上定義執行個體警示，則每次引發警示，此資料表就會新增新的資料列。</span><span class="sxs-lookup"><span data-stu-id="f42d8-202">If you have defined instance alerts on the particular activity view, a new row will be added to this table every time the alert is fired.</span></span>  
  
 <span data-ttu-id="f42d8-203">您可以手動執行這項作業，以清除資料表，或根據應用程式或環境的需求排程作業的執行時間。</span><span class="sxs-lookup"><span data-stu-id="f42d8-203">You can run this job manually to clean up the table or schedule it to run according to the need of your application or environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f42d8-204">請參閱</span><span class="sxs-lookup"><span data-stu-id="f42d8-204">See Also</span></span>  
 [<span data-ttu-id="f42d8-205">管理 BAM</span><span class="sxs-lookup"><span data-stu-id="f42d8-205">Managing BAM</span></span>](../core/managing-bam.md)