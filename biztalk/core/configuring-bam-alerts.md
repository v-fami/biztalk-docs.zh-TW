---
title: 設定 BAM 警示 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, alerts
- alerts, timeout values
- Notification Services, configuration tips
- alerts, configuring
- managing [BAM definitions], configuring alerts
ms.assetid: 29327466-c8e9-41e8-bc12-f3ac6b5d3096
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8198b17d07288bff04b64b0a1ad05db0cde4fd91
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968884"
---
# <a name="configuring-bam-alerts"></a><span data-ttu-id="e44a1-102">設定 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="e44a1-102">Configuring BAM Alerts</span></span>
<span data-ttu-id="e44a1-103">系統管理員可以修改 BAM 警示架構的特定項目。</span><span class="sxs-lookup"><span data-stu-id="e44a1-103">Administrators can modify certain elements of the BAM alert framework.</span></span> <span data-ttu-id="e44a1-104">本主題描述系統管理員可以使用的組態選項。</span><span class="sxs-lookup"><span data-stu-id="e44a1-104">This topic describes the configuration options available to administrators.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e44a1-105">建立警示時，請務必記得，時間資料是以本地時間格式儲存在 OLAP、星狀結構描述以及 Notification Services 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e44a1-105">When creating alerts you should be aware that time data is stored in a Local Time format on the OLAP, Star Schema, and Notification Services databases.</span></span> <span data-ttu-id="e44a1-106">同時假設這三個資料庫都位於相同時區。</span><span class="sxs-lookup"><span data-stu-id="e44a1-106">It is also assumed that all three databases are in the same time zone.</span></span> <span data-ttu-id="e44a1-107">在主要匯入資料庫上，資訊是以 UTC 時間格式儲存，可以是同一個時區，也可以是不同時區。</span><span class="sxs-lookup"><span data-stu-id="e44a1-107">On the Primary Import database, information is stored in the UTC time format and can be in the same or different time zone.</span></span>  
  
## <a name="changing-the-adf-configuration"></a><span data-ttu-id="e44a1-108">變更 ADF 組態</span><span class="sxs-lookup"><span data-stu-id="e44a1-108">Changing the ADF configuration</span></span>  
 <span data-ttu-id="e44a1-109">部署 BAM 管理公用程式會使用 bm.exe.config 檔案中指定的 CommandTimeout 值來填入 Notification Services 應用程式定義檔的檢視時\<EventRule\>\\< ActionTimeout\>項目。</span><span class="sxs-lookup"><span data-stu-id="e44a1-109">When deploying a view the BAM Management utility uses the CommandTimeout value specified in the bm.exe.config file to populate Notification Services application definition file \<EventRule\>\\<ActionTimeout\> element.</span></span>  
  
 <span data-ttu-id="e44a1-110">變更 bm.exe.config 中的 CommandTimeout 值，並不會影響變更前所部署檢視的 CommandTimeout 值。</span><span class="sxs-lookup"><span data-stu-id="e44a1-110">Changing the value of CommandTimeout in bm.exe.config does not change the CommandTimeout value for views deployed prior to the change.</span></span>  
  
 <span data-ttu-id="e44a1-111">下列程序使用 ProcessBamNSFiles.vbs 取得組態檔案與 Notification Services 應用程式定義檔案。</span><span class="sxs-lookup"><span data-stu-id="e44a1-111">The procedure below uses the ProcessBamNSFiles.vbs to obtain the configuration and the Notification Services application definition file.</span></span> <span data-ttu-id="e44a1-112">如需有關此指令碼的詳細資訊，請參閱[BAM Notification Services 組態檔的命令列指令碼](../core/bam-command-line-script-for-notification-services-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="e44a1-112">For more information on the script, see [BAM Command-Line Script for Notification Services Configuration Files](../core/bam-command-line-script-for-notification-services-configuration-files.md).</span></span>  
  
 <span data-ttu-id="e44a1-113">如何變更已部署檢視 NS 的 ActionTimeout：</span><span class="sxs-lookup"><span data-stu-id="e44a1-113">How to change the ActionTimeout for NS for already deployed views:</span></span>  
  
#### <a name="to-change-the-command-timeout-value"></a><span data-ttu-id="e44a1-114">變更命令逾時值</span><span class="sxs-lookup"><span data-stu-id="e44a1-114">To change the command timeout value</span></span>  
  
1.  <span data-ttu-id="e44a1-115">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e44a1-115">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="e44a1-116">瀏覽至追蹤資料夾，在命令提示字元中輸入**cd"C:\Program Files\Microsoft BizTalk Server\<版本\>\Tracking"** 或**cd"C:\Program Files (x86) \Microsoft BizTalk伺服器\<版本\>\Tracking"** 64 位元電腦上。</span><span class="sxs-lookup"><span data-stu-id="e44a1-116">Navigate to the tracking folder by typing at the command prompt **cd “C:\Program Files\Microsoft BizTalk Server \<version\>\Tracking”** or **cd “C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\Tracking”** on a 64 bit computer.</span></span> <span data-ttu-id="e44a1-117">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e44a1-117">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="e44a1-118">擷取 ADF 檔案。</span><span class="sxs-lookup"><span data-stu-id="e44a1-118">Retrieve the ADF file.</span></span> <span data-ttu-id="e44a1-119">型別**cscript ProcessBamNSFiles.vbs-Get \<ConfigFilePath\> \<組態檔路徑\> \< PID Server\> \< PID 資料庫\>** .</span><span class="sxs-lookup"><span data-stu-id="e44a1-119">Type **cscript ProcessBamNSFiles.vbs -Get \<ConfigFilePath\> \<ADFFilePath\> \< PID Server\> \< PID database \>**.</span></span> <span data-ttu-id="e44a1-120">請以適合您安裝的值取代 ConfigFilePath、ADFFilePath、PID Server 與 PID database。</span><span class="sxs-lookup"><span data-stu-id="e44a1-120">Replacing the ConfigFilePath, ADFFilePath, PID Server, and PID database with the appropriate values for your installation.</span></span>  
  
4.  <span data-ttu-id="e44a1-121">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e44a1-121">Press **ENTER**.</span></span>  
  
5.  <span data-ttu-id="e44a1-122">在編輯器中開啟 ADF 檔案，並搜尋\<ActionTimeout\>、 更新與所要的值，並請注意，這個值會是 XML 持續時間。</span><span class="sxs-lookup"><span data-stu-id="e44a1-122">Open the ADF file in an editor and search for \<ActionTimeout\>, update with desired value & please note that this value is an XML duration.</span></span>  
  
6.  <span data-ttu-id="e44a1-123">儲存 ADF 檔案。</span><span class="sxs-lookup"><span data-stu-id="e44a1-123">Save the ADF file.</span></span> <span data-ttu-id="e44a1-124">型別**cscript ProcessBamNSFiles.vbs-Update \<ConfigFilePath\> \<組態檔路徑\> \< PID Server\> \< PID 資料庫\>**.</span><span class="sxs-lookup"><span data-stu-id="e44a1-124">Type **cscript ProcessBamNSFiles.vbs -Update \<ConfigFilePath\> \<ADFFilePath\> \< PID Server\> \< PID database \>**.</span></span>  
  
7.  <span data-ttu-id="e44a1-125">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e44a1-125">Press **ENTER**.</span></span>  
  
### <a name="notification-service-configuration-tips"></a><span data-ttu-id="e44a1-126">Notification Service 設定秘訣</span><span class="sxs-lookup"><span data-stu-id="e44a1-126">Notification Service configuration tips</span></span>  
 <span data-ttu-id="e44a1-127">如果您將 BAM 警示設定成在執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的遠端電腦上放置警示資料庫，則此 SQL Server 執行個體上必須安裝 Notification Services 資料庫元件。</span><span class="sxs-lookup"><span data-stu-id="e44a1-127">If you configure BAM Alerts in such a way as to place the Alerts databases on a remote computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], then the Notification Services Database Components must be installed on the SQL Server instance.</span></span> <span data-ttu-id="e44a1-128">如果 SQL 執行個體上沒有這些元件，BAM 警示的組態將會失敗並傳回錯誤，指出無法將權限授與 Notification Services 延伸預存程序。</span><span class="sxs-lookup"><span data-stu-id="e44a1-128">If these components are not present on the SQL instance, then configuration of BAM Alerts will fail with an error indicating that permissions could not be granted to the Notification Services Extended Stored Procedures.</span></span> <span data-ttu-id="e44a1-129">如需有關安裝 Notification Services 元件的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=61999](http://go.microsoft.com/fwlink/?LinkId=61999)。</span><span class="sxs-lookup"><span data-stu-id="e44a1-129">For more information on installing the Notification Services component, see [http://go.microsoft.com/fwlink/?LinkId=61999](http://go.microsoft.com/fwlink/?LinkId=61999).</span></span>  
  
 <span data-ttu-id="e44a1-130">BAM 可以讓您變更 BAM 存取 Notification Services 所使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="e44a1-130">BAM allows you to change the account that BAM uses to access the Notification Services.</span></span> <span data-ttu-id="e44a1-131">如果您不是透過執行 NSControl 來變更此帳戶，將會收到錯誤，通知您使用 NSControl 變更帳戶。</span><span class="sxs-lookup"><span data-stu-id="e44a1-131">If you change this account in any way other than running NSControl, you will receive an error informing you to use the NSControl to change the account.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e44a1-132">您不能使用 LocalSystem 或 SYSTEM 帳戶來安裝和設定 Notification Services。</span><span class="sxs-lookup"><span data-stu-id="e44a1-132">You cannot use the LocalSystem or SYSTEM accounts for installing and configuring Notification Services.</span></span> <span data-ttu-id="e44a1-133">您無法登入一些特殊帳戶，而且不能用這些帳戶來對 BAM 警示使用者授與檔案和 SQL Server 權限。</span><span class="sxs-lookup"><span data-stu-id="e44a1-133">These are special accounts that you cannot log on to and that you cannot use to grant file and SQL Server permissions to the BAM alerts user.</span></span>  
>   
>  <span data-ttu-id="e44a1-134">若要安裝和設定 Notification Services，請在本機電腦上建立新的使用者帳戶，對其授與所有必要權限，然後使用該帳戶來設定 Notification Services。</span><span class="sxs-lookup"><span data-stu-id="e44a1-134">To install and configure Notification Services, create a new user account on the local computer, grant it all the requisite permissions, and then use it to configure Notification Services.</span></span>  
  
##### <a name="to-change-ns-user-account-for-bam"></a><span data-ttu-id="e44a1-135">變更 BAM 的 NS 使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="e44a1-135">To change NS user account for BAM</span></span>  
  
1.  <span data-ttu-id="e44a1-136">請使用 NSControl 更新使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e44a1-136">Use NSControl to update the user account.</span></span>  
  
2.  <span data-ttu-id="e44a1-137">授與 NS 使用者讀取、寫入與變更 BAM 警示檔案位置共用的權限。</span><span class="sxs-lookup"><span data-stu-id="e44a1-137">Grant the NS user read, write, and change permissions to the BAM Alerts File Location share.</span></span>  
  
3.  <span data-ttu-id="e44a1-138">新增 NS 使用者做為 BAMAlerts 執行個體和應用程式資料庫中 NSRunService 角色的成員。</span><span class="sxs-lookup"><span data-stu-id="e44a1-138">Add the NS user as a member of NSRunService role in both the BAMAlerts instance and application databases.</span></span>  
  
4.  <span data-ttu-id="e44a1-139">權利授與 NS 使用者本機上使用的文件[http://go.microsoft.com/fwlink/?LinkId=62005](http://go.microsoft.com/fwlink/?LinkId=62005)。</span><span class="sxs-lookup"><span data-stu-id="e44a1-139">Grant the NS User rights on the local machine using the documentation at [http://go.microsoft.com/fwlink/?LinkId=62005](http://go.microsoft.com/fwlink/?LinkId=62005).</span></span>  
  
5.  <span data-ttu-id="e44a1-140">授與 NS 資料庫權限 ns 根據[http://go.microsoft.com/fwlink/?LinkId=62008](http://go.microsoft.com/fwlink/?LinkId=62008)。</span><span class="sxs-lookup"><span data-stu-id="e44a1-140">Grant the NS rights to the NS database according to [http://go.microsoft.com/fwlink/?LinkId=62008](http://go.microsoft.com/fwlink/?LinkId=62008).</span></span>  
  
6.  <span data-ttu-id="e44a1-141">授與 NS 使用者登入 SQL 伺服器以及存取主要匯入資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="e44a1-141">Grant the NS user login rights to SQL server and database access to the Primary Import database.</span></span>  
  
7.  <span data-ttu-id="e44a1-142">將 NS 使用者新增至 BAM_ManagmentNSReader SQL 角色。</span><span class="sxs-lookup"><span data-stu-id="e44a1-142">Add the NS user to the BAM_ManagmentNSReader SQL role.</span></span>  
  
8.  <span data-ttu-id="e44a1-143">將 NS 使用者新增至 BamAnalysis 資料庫中的「BAM 警示」角色。</span><span class="sxs-lookup"><span data-stu-id="e44a1-143">Add the NS user to the "BAM Alerts" role in BamAnalysis database.</span></span>  
  
 <span data-ttu-id="e44a1-144">如果您修改檔案所傳遞之警示的檔案放置位置，</span><span class="sxs-lookup"><span data-stu-id="e44a1-144">If you modify the file drop location for alerts delivered by file.</span></span> <span data-ttu-id="e44a1-145">就必須重新啟動 SQL Notifications Services。</span><span class="sxs-lookup"><span data-stu-id="e44a1-145">You must restart the SQL Notifications Services.</span></span>  
  
 <span data-ttu-id="e44a1-146">如果 NS 服務未重新啟動，將會繼續傳遞警示至原始檔案放置位置。</span><span class="sxs-lookup"><span data-stu-id="e44a1-146">If the NS service is not restarted, alerts will continue being delivered to the original file drop location.</span></span>  
  
 <span data-ttu-id="e44a1-147">修改 BAM 組態檔案的下面這一列，並使用 BAM 管理公用程式 update-config 命令，即可變更檔案放置位置。</span><span class="sxs-lookup"><span data-stu-id="e44a1-147">The file drop location is changed by modifying the following line of the BAM configuration file and using the BAM manangement utility update-config command.</span></span>  
  
 <span data-ttu-id="e44a1-148">\<屬性名稱 ="FileDropUNC"\>\\\\< 電腦名稱\>\alerts\</Property\></span><span class="sxs-lookup"><span data-stu-id="e44a1-148">\<Property Name="FileDropUNC"\>\\\\<computer name\>\alerts\</Property\></span></span>  
  
 <span data-ttu-id="e44a1-149">如需 BAM 管理公用程式的詳細資訊，請參閱[BAM 管理公用程式](../core/bam-management-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="e44a1-149">For more information on the BAM Management utility, see [BAM Management Utility](../core/bam-management-utility.md).</span></span>