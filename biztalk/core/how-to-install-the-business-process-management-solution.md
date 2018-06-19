---
title: 如何安裝商務程序管理解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing, examples
- process management solution tutorial, installing
- process management solution tutorial, deployment prerequisites
ms.assetid: 930f3bb1-05e6-4b02-852d-6139aaf341f0
caps.latest.revision: 61
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 706bc1cec8afc796fa44e022243782a207fe1777
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974932"
---
# <a name="how-to-install-the-business-process-management-solution"></a><span data-ttu-id="f3f08-102">如何安裝商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="f3f08-102">How to Install the Business Process Management Solution</span></span>
<span data-ttu-id="f3f08-103">下列步驟說明如何準備安裝商務程序管理 (BPM) 解決方案的電腦，以及如何在此電腦上安裝解決方案。</span><span class="sxs-lookup"><span data-stu-id="f3f08-103">The following steps describe how to prepare the computer for installing the Business Process Management (BPM) solution, and how to install the solution on this computer.</span></span>  
  
-   [<span data-ttu-id="f3f08-104">準備安裝商務程序管理解決方案的電腦</span><span class="sxs-lookup"><span data-stu-id="f3f08-104">Prepare the computer for installing the Business Process Management Solution</span></span>](#step1)  
  
     <span data-ttu-id="f3f08-105">在準備步驟中，您會建立由接收埠和傳送埠使用的資料夾、佇列和 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f3f08-105">In the preparation step, you create the folders, queues, and SQL database that will be used by the receive and send ports.</span></span> <span data-ttu-id="f3f08-106">您也會為用戶端應用程式、CSRWebApp 和 OrderBroker Proxy Web 服務建立兩個虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="f3f08-106">You also create the two virtual directories for the client application, CSRWebApp, and the OrderBroker proxy Web Service.</span></span>  
  
-   [<span data-ttu-id="f3f08-107">設定安裝商務程序管理解決方案的電腦</span><span class="sxs-lookup"><span data-stu-id="f3f08-107">Configure the computer for installing the Business Process Management Solution</span></span>](#step3)  
  
-   [<span data-ttu-id="f3f08-108">安裝商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="f3f08-108">Install the Business Process Management Solution</span></span>](#step5)  
  
> [!NOTE]
>  <span data-ttu-id="f3f08-109">您將會執行幾個批次檔以部署解決方案。</span><span class="sxs-lookup"><span data-stu-id="f3f08-109">You will run some batch files to deploy the solution.</span></span> <span data-ttu-id="f3f08-110">建議您將批次檔的輸出重新導向至文字檔以確認指令碼是否成功完成。</span><span class="sxs-lookup"><span data-stu-id="f3f08-110">We recommend that you redirect the output of the batch files to a text file to verify that the script completed successfully.</span></span>  
  
##  <a name="step1"></a><span data-ttu-id="f3f08-111">準備安裝商務程序管理解決方案的電腦</span><span class="sxs-lookup"><span data-stu-id="f3f08-111">Prepare the computer for installing the Business Process Management Solution</span></span>  
  
#### <a name="to-prepare-the-computer-for-installing-the-business-process-management-solution"></a><span data-ttu-id="f3f08-112">準備安裝商務程序管理解決方案的電腦</span><span class="sxs-lookup"><span data-stu-id="f3f08-112">To prepare the computer for installing the Business Process Management Solution</span></span>  
  
1.  <span data-ttu-id="f3f08-113">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下 **服務**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-113">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Services**.</span></span> <span data-ttu-id="f3f08-114">使用**服務**主控台中，請確定下列服務正在執行：</span><span class="sxs-lookup"><span data-stu-id="f3f08-114">Using the **Services** console, make sure that the following services are running:</span></span>  
  
    -   <span data-ttu-id="f3f08-115">**FTP 發行功能**</span><span class="sxs-lookup"><span data-stu-id="f3f08-115">**FTP Publishing**</span></span>  
  
    -   <span data-ttu-id="f3f08-116">**訊息佇列**</span><span class="sxs-lookup"><span data-stu-id="f3f08-116">**Message Queuing**</span></span>  
  
    -   <span data-ttu-id="f3f08-117">**World Wide Web 發行**</span><span class="sxs-lookup"><span data-stu-id="f3f08-117">**World Wide Web Publishing**</span></span>  
  
2.  <span data-ttu-id="f3f08-118">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，按一下 **電腦管理**主控台，然後再加入本機系統管理員群組的 BizTalk 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="f3f08-118">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Computer Management** console, and then add the BizTalk service account to the local Administrators group.</span></span>  
  
3.  <span data-ttu-id="f3f08-119">如果您安裝 Windows SharePoint Services 時，排除 （根） 的**Default Web Site**從 Windows SharePoint Services 受管理的路徑，如下所示： 按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下  **SharePoint 管理中心內**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-119">If you installed Windows SharePoint Services, exclude the (root) of the **Default Web Site** from Windows SharePoint Services Managed Paths as follows: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
    1.  <span data-ttu-id="f3f08-120">在下**虛擬伺服器設定**，選取**設定虛擬伺服器設定**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-120">Under **Virtual Server Configuration**, select **Configure virtual server settings**.</span></span>  
  
    2.  <span data-ttu-id="f3f08-121">在**虛擬伺服器清單**頁面上，按一下**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-121">On the **Virtual Server List** page, click **Default Web Site**.</span></span>  
  
    3.  <span data-ttu-id="f3f08-122">在**虛擬伺服器設定**頁面上，按一下**定義管理的路徑**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-122">On the **Virtual Server Settings** page, click **Define managed paths**.</span></span>  
  
    4.  <span data-ttu-id="f3f08-123">在**包含路徑**區段**定義受管理的路徑**頁面上，選取**根**，然後按一下 **移除選取的路徑**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-123">In the **Included Paths** section of the **Defined Managed Path** page, select **Root** and then click **Remove selected paths**.</span></span>  
  
    5.  <span data-ttu-id="f3f08-124">在命令提示字元，執行 IISReset。</span><span class="sxs-lookup"><span data-stu-id="f3f08-124">At a command prompt, perform an IISReset.</span></span>  
  
##  <a name="step3"></a><span data-ttu-id="f3f08-125">設定安裝商務程序管理解決方案的電腦</span><span class="sxs-lookup"><span data-stu-id="f3f08-125">Configure the computer for installing the Business Process Management Solution</span></span>  
  
#### <a name="to-configure-the-computer-for-installing-the-business-process-management-solution"></a><span data-ttu-id="f3f08-126">設定安裝商務程序管理解決方案的電腦</span><span class="sxs-lookup"><span data-stu-id="f3f08-126">To configure the computer for installing the Business Process Management Solution</span></span>  
  
1.  <span data-ttu-id="f3f08-127">登出電腦，然後以 BizTalk 服務帳戶的身分登入電腦。</span><span class="sxs-lookup"><span data-stu-id="f3f08-127">Log off the computer, and then log on to the computer as the BizTalk service account.</span></span>  
  
2.  <span data-ttu-id="f3f08-128">開啟命令提示字元，輸入下列命令，然後按 ENTER，設定 %BTSSolutionsPath% 環境變數以指出 E2E 解決方案的基底資料夾。</span><span class="sxs-lookup"><span data-stu-id="f3f08-128">Open a command prompt, type the following command, and then press ENTER to set the %BTSSolutionsPath% environment variable to indicate the base folder for the E2E solutions.</span></span> <span data-ttu-id="f3f08-129">然後結束命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f3f08-129">Then, exit the command prompt.</span></span>  
  
    -   `setx BTSSolutionsPath "%ProgramFiles%\Microsoft BizTalk Server 2009\SDK\Scenarios"`  
  
        > [!NOTE]
        >  <span data-ttu-id="f3f08-130">若您使用 64 位元的電腦，請使用 %ProgramFiles(x86)% 取代 %ProgramFiles%。</span><span class="sxs-lookup"><span data-stu-id="f3f08-130">If you are using a 64-bit computer, use %ProgramFiles(x86)% instead of %ProgramFiles%.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f3f08-131">如需有關 SETX 命令的詳細資訊，請參閱 Microsoft TechNet 網站，網址[http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831)。</span><span class="sxs-lookup"><span data-stu-id="f3f08-131">For more information about the SETX command, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span></span>  
  
3.  <span data-ttu-id="f3f08-132">開啟命令提示字元，將目前的目錄變更為 %BTSSolutionsPath%\BPM\HistoryDB 資料夾，輸入`CreateDatabase.cmd`，然後按 ENTER 以建立歷程記錄資料庫。</span><span class="sxs-lookup"><span data-stu-id="f3f08-132">Open a command prompt, change the current directory to %BTSSolutionsPath%\BPM\HistoryDB folder, type `CreateDatabase.cmd`, and press ENTER to create the history database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3f08-133">執行指定為 SQL 傳送配接器處理常式的主控件之使用者，則必須具有相關權限可執行 SouthridgeVideoHistory 資料庫上的預存程序。</span><span class="sxs-lookup"><span data-stu-id="f3f08-133">The user running the host specified as the handler for the SQL send adapter must have permissions to execute stored procedures on the SouthridgeVideoHistory database.</span></span>  
  
4.  <span data-ttu-id="f3f08-134">在命令提示字元，執行下列命令，將預設指令碼主控件變更為 CScript.exe</span><span class="sxs-lookup"><span data-stu-id="f3f08-134">At a command prompt, run the following command to change the default script host to CScript.exe</span></span>  
  
    -   `CScript /H:CScript`  
  
5.  <span data-ttu-id="f3f08-135">在命令提示字元，執行下列命令以建立 CSRWebApp Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="f3f08-135">At a command prompt, run the following command to create the CSRWebApp Web application</span></span>  
  
    -   `iisvdir /create "Default Web Site" CSRWebApp "%BTSSolutionsPath%\BPM\CSRWebApp"`  
  
        > [!NOTE]
        >  <span data-ttu-id="f3f08-136">如需有關 iisvdir.vbs 的詳細資訊，請參閱 Microsoft TechNet 網站，網址[http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830)。</span><span class="sxs-lookup"><span data-stu-id="f3f08-136">For more information about iisvdir.vbs, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).</span></span>  
  
6.  <span data-ttu-id="f3f08-137">在命令提示字元，執行下列命令，為 OrderBroker_Proxy 建立新的 IIS 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="f3f08-137">At a command prompt, run the following command to create a new IIS virtual directory for OrderBroker_Proxy.</span></span>  
  
    -   `iisvdir /create "Default Web Site" BTSScn.BPM.OrderBroker_Proxy "%BTSSolutionsPath%\BPM\OrderBroker_Proxy"`  
  
    > [!NOTE]
    >  <span data-ttu-id="f3f08-138">您可以使用網際網路資訊服務 (IIS) 管理員建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f3f08-138">You can use Internet Information Services (IIS) Manager to create the Web Application.</span></span> <span data-ttu-id="f3f08-139">如需如何在 IIS 7.0 中建立應用程式的詳細資訊，請參閱 < 在 IIS 7.0 說明文件[http://go.microsoft.com/fwlink/?LinkId=59263](http://go.microsoft.com/fwlink/?LinkId=59263)。</span><span class="sxs-lookup"><span data-stu-id="f3f08-139">For more information about how to create applications in IIS 7.0, see the IIS 7.0 Documentation at [http://go.microsoft.com/fwlink/?LinkId=59263](http://go.microsoft.com/fwlink/?LinkId=59263).</span></span>  
  
7.  <span data-ttu-id="f3f08-140">建立新的 IIS 應用程式集區，並將其識別設定為「BizTalk 外掛式主控件使用者」群組成員和「IIS_WPG」群組成員的使用者，方式如下：</span><span class="sxs-lookup"><span data-stu-id="f3f08-140">Create a new IIS application pool and set its identity as a user that is a member of the BizTalk Isolated Host Users group and the IIS_WPG group, as follows:</span></span>  
  
    1.  <span data-ttu-id="f3f08-141">在網際網路資訊服務 (IIS) 管理員中，以滑鼠右鍵按一下**應用程式集區**，選取**新增**，然後選取**應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-141">In Internet Information Services (IIS) Manager, right-click **Application Pools**, select **New**, and then select **Application Pool**.</span></span>  
  
    2.  <span data-ttu-id="f3f08-142">型別**應用程式集區識別碼**（任意值），然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-142">Type the **Application pool ID** (any value), and then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="f3f08-143">以滑鼠右鍵按一下應用程式集區，您建立，然後選取**進階設定**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-143">Right-click the application pool that you created, and then select **Advanced Settings**.</span></span>  
  
    4.  <span data-ttu-id="f3f08-144">展開**處理序模型**，如右邊資料行中按一下**識別**設定，然後再按一下 **...**</span><span class="sxs-lookup"><span data-stu-id="f3f08-144">Expand **Process Model**, click in the right-column for the **Identity** setting, and then click **…**</span></span>  
  
    5.  <span data-ttu-id="f3f08-145">選取的使用者帳戶 (任一**內建帳戶**或**自訂帳戶**) 具有權限來建立和執行在 Windows\Temp 目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="f3f08-145">Select a user account (either a **Build-in account** or **Custom account** ) that has permissions to create and execute files in the Windows\Temp directory.</span></span> <span data-ttu-id="f3f08-146">當您設定 BizTalk 時，組態程序已經為它所新增至「BizTalk 外掛式主控件使用者」群組的使用者設定這些權限。</span><span class="sxs-lookup"><span data-stu-id="f3f08-146">When you configured BizTalk, the configuration process already set these permissions for the user it added to the BizTalk Isolated Host Users group.</span></span> <span data-ttu-id="f3f08-147">建議您指定相同的使用者。</span><span class="sxs-lookup"><span data-stu-id="f3f08-147">Specifying the same user is a good choice.</span></span>  
  
8.  <span data-ttu-id="f3f08-148">在 網際網路資訊服務 (IIS) 管理員 中，展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下**BTSScn.BPM.OrderBroker_Proxy**，指向**管理應用程式**，然後按一下 **進階設定**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-148">In Internet Information Services (IIS) Manager, expand **Web Sites**, expand **Default Web Site**, right-click **BTSScn.BPM.OrderBroker_Proxy**, point to **Manage Application**, and then click **Advanced Settings**.</span></span>  
  
9. <span data-ttu-id="f3f08-149">設定**應用程式集區**您在上一個步驟中建立的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="f3f08-149">Set **Application Pool** to the application pool that you  created in the previous step.</span></span>  
  
10. <span data-ttu-id="f3f08-150">重複前面兩個步驟**CSRWebApp**應用程式。</span><span class="sxs-lookup"><span data-stu-id="f3f08-150">Repeat the previous two steps for the **CSRWebApp** application.</span></span>  
  
11. <span data-ttu-id="f3f08-151">重設 IIS 以確定所有變更均立即生效。</span><span class="sxs-lookup"><span data-stu-id="f3f08-151">Reset IIS to make sure all these changes take effect immediately.</span></span> <span data-ttu-id="f3f08-152">若要這樣做，請執行**iisreset**在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f3f08-152">To do this, run **iisreset** at a command prompt.</span></span>  
  
12. <span data-ttu-id="f3f08-153">在命令提示字元，請將目前資料夾變更為 %btssolutionspath%\bpm\scripts，型別`CreateQueues.vbs`，然後按 ENTER 以建立下列私用佇列。</span><span class="sxs-lookup"><span data-stu-id="f3f08-153">At a command prompt, change the current folder to the %BTSSolutionsPath%\BPM\Scripts, type `CreateQueues.vbs`, and then press ENTER to create the following private queues.</span></span>  
  
    |<span data-ttu-id="f3f08-154">名稱</span><span class="sxs-lookup"><span data-stu-id="f3f08-154">Name</span></span>|<span data-ttu-id="f3f08-155">異動</span><span class="sxs-lookup"><span data-stu-id="f3f08-155">Transactional</span></span>|<span data-ttu-id="f3f08-156">交易通訊協定</span><span class="sxs-lookup"><span data-stu-id="f3f08-156">Transaction protocol</span></span>|  
    |----------|-------------------|--------------------------|  
    |<span data-ttu-id="f3f08-157">ToFacilitiesQ</span><span class="sxs-lookup"><span data-stu-id="f3f08-157">ToFacilitiesQ</span></span>|<span data-ttu-id="f3f08-158">是</span><span class="sxs-lookup"><span data-stu-id="f3f08-158">Yes</span></span>|<span data-ttu-id="f3f08-159">原生</span><span class="sxs-lookup"><span data-stu-id="f3f08-159">Native</span></span>|  
    |<span data-ttu-id="f3f08-160">FromFacilitiesQ</span><span class="sxs-lookup"><span data-stu-id="f3f08-160">FromFacilitiesQ</span></span>|<span data-ttu-id="f3f08-161">是</span><span class="sxs-lookup"><span data-stu-id="f3f08-161">Yes</span></span>|<span data-ttu-id="f3f08-162">原生</span><span class="sxs-lookup"><span data-stu-id="f3f08-162">Native</span></span>|  
    |<span data-ttu-id="f3f08-163">FromFixedOrdersQ</span><span class="sxs-lookup"><span data-stu-id="f3f08-163">FromFixedOrdersQ</span></span>|<span data-ttu-id="f3f08-164">是</span><span class="sxs-lookup"><span data-stu-id="f3f08-164">Yes</span></span>|<span data-ttu-id="f3f08-165">原生</span><span class="sxs-lookup"><span data-stu-id="f3f08-165">Native</span></span>|  
    |<span data-ttu-id="f3f08-166">ToServicingSystemQ</span><span class="sxs-lookup"><span data-stu-id="f3f08-166">ToServicingSystemQ</span></span>|<span data-ttu-id="f3f08-167">是</span><span class="sxs-lookup"><span data-stu-id="f3f08-167">Yes</span></span>|<span data-ttu-id="f3f08-168">原生</span><span class="sxs-lookup"><span data-stu-id="f3f08-168">Native</span></span>|  
    |<span data-ttu-id="f3f08-169">ToCSRSystemQ</span><span class="sxs-lookup"><span data-stu-id="f3f08-169">ToCSRSystemQ</span></span>|<span data-ttu-id="f3f08-170">否</span><span class="sxs-lookup"><span data-stu-id="f3f08-170">No</span></span>|<span data-ttu-id="f3f08-171">HTTP</span><span class="sxs-lookup"><span data-stu-id="f3f08-171">HTTP</span></span>|  
    |<span data-ttu-id="f3f08-172">ToVendorSystemQ</span><span class="sxs-lookup"><span data-stu-id="f3f08-172">ToVendorSystemQ</span></span>|<span data-ttu-id="f3f08-173">否</span><span class="sxs-lookup"><span data-stu-id="f3f08-173">No</span></span>|<span data-ttu-id="f3f08-174">HTTP</span><span class="sxs-lookup"><span data-stu-id="f3f08-174">HTTP</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="f3f08-175">您可以使用**電腦管理**嵌入式管理單元來建立佇列。</span><span class="sxs-lookup"><span data-stu-id="f3f08-175">You can use **Computer Management** snap-in to create the queues.</span></span> <span data-ttu-id="f3f08-176">如需如何建立私用佇列的詳細資訊，請參閱 < 訊息佇列的文件，網址[http://go.microsoft.com/fwlink/?LinkId=59264](http://go.microsoft.com/fwlink/?LinkId=59264)。</span><span class="sxs-lookup"><span data-stu-id="f3f08-176">For more information about how to create a private queue, see the Message Queuing documentation at [http://go.microsoft.com/fwlink/?LinkId=59264](http://go.microsoft.com/fwlink/?LinkId=59264).</span></span> <span data-ttu-id="f3f08-177">如需如何安裝 MSMQ 3.0 的詳細資訊，請參閱 < 訊息佇列的文件，網址[http://go.microsoft.com/fwlink/?LinkId=59265](http://go.microsoft.com/fwlink/?LinkId=59265)。</span><span class="sxs-lookup"><span data-stu-id="f3f08-177">For more information about how to install MSMQ 3.0, see the Message Queuing documentation at [http://go.microsoft.com/fwlink/?LinkId=59265](http://go.microsoft.com/fwlink/?LinkId=59265).</span></span>  
  
13. <span data-ttu-id="f3f08-178">在命令提示字元，請將目前資料夾變更為 %btssolutionspath%\bpm\scripts，型別`CreateTestDirectories.cmd`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f3f08-178">At a command prompt, change the current folder to the %BTSSolutionsPath%\BPM\Scripts, type `CreateTestDirectories.cmd`, and then press ENTER.</span></span>  
  
    -   <span data-ttu-id="f3f08-179">下列資料夾建立在 %SystemDrive%\BPMTest 資料夾中</span><span class="sxs-lookup"><span data-stu-id="f3f08-179">The following folders are crated in %SystemDrive%\BPMTest folder</span></span>  
  
         <span data-ttu-id="f3f08-180">CSRResponse-DSP</span><span class="sxs-lookup"><span data-stu-id="f3f08-180">CSRResponse-DSP</span></span>  
  
         <span data-ttu-id="f3f08-181">VendorResponse-DSP</span><span class="sxs-lookup"><span data-stu-id="f3f08-181">VendorResponse-DSP</span></span>  
  
         <span data-ttu-id="f3f08-182">OrderErrors-SP</span><span class="sxs-lookup"><span data-stu-id="f3f08-182">OrderErrors-SP</span></span>  
  
         <span data-ttu-id="f3f08-183">ErrorResponse-RP-TestRL</span><span class="sxs-lookup"><span data-stu-id="f3f08-183">ErrorResponse-RP-TestRL</span></span>  
  
         <span data-ttu-id="f3f08-184">Facilities-SP</span><span class="sxs-lookup"><span data-stu-id="f3f08-184">Facilities-SP</span></span>  
  
         <span data-ttu-id="f3f08-185">Facilities-RP-TestRL</span><span class="sxs-lookup"><span data-stu-id="f3f08-185">Facilities-RP-TestRL</span></span>  
  
         <span data-ttu-id="f3f08-186">HistoryInsert-SP</span><span class="sxs-lookup"><span data-stu-id="f3f08-186">HistoryInsert-SP</span></span>  
  
         <span data-ttu-id="f3f08-187">HistoryUpdate-SP</span><span class="sxs-lookup"><span data-stu-id="f3f08-187">HistoryUpdate-SP</span></span>  
  
         <span data-ttu-id="f3f08-188">Order-RP-TestRL</span><span class="sxs-lookup"><span data-stu-id="f3f08-188">Order-RP-TestRL</span></span>  
  
         <span data-ttu-id="f3f08-189">ServicingSystem-SP</span><span class="sxs-lookup"><span data-stu-id="f3f08-189">ServicingSystem-SP</span></span>  
  
         <span data-ttu-id="f3f08-190">Vendor-RP-TestRL</span><span class="sxs-lookup"><span data-stu-id="f3f08-190">Vendor-RP-TestRL</span></span>  
  
         <span data-ttu-id="f3f08-191">BizTalkErrors-SP</span><span class="sxs-lookup"><span data-stu-id="f3f08-191">BizTalkErrors-SP</span></span>  
  
    -   <span data-ttu-id="f3f08-192">FromVendor 資料夾建立在 %SystemDrive%\Inetpub\ftproot 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f3f08-192">FromVendor folder is created in the %SystemDrive%\Inetpub\ftproot folder.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f3f08-193">若 Windows 系統不是安裝在 C 磁碟機，則應該以 C: 取代 %SystemDrive%。</span><span class="sxs-lookup"><span data-stu-id="f3f08-193">If the Windows system is not installed on the C drive, you should replace %SystemDrive% with C:.</span></span> <span data-ttu-id="f3f08-194">必須比對資料夾名稱與 BPM 解決方案提供之繫結檔案中的位址。</span><span class="sxs-lookup"><span data-stu-id="f3f08-194">You have to match the folder names to the address in the binding files that the BPM solution provides.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f3f08-195">BizTalk 服務帳戶必須具有 FromVendor 資料夾的讀取/寫入權限。</span><span class="sxs-lookup"><span data-stu-id="f3f08-195">The BizTalk service account must have read/write permission to the FromVendor folder.</span></span>  
  
##  <a name="step5"></a><span data-ttu-id="f3f08-196">安裝商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="f3f08-196">Install the Business Process Management Solution</span></span>  
  
#### <a name="to-install-the-business-process-management-solution"></a><span data-ttu-id="f3f08-197">安裝商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="f3f08-197">To install the Business Process Management Solution</span></span>  
  
1.  <span data-ttu-id="f3f08-198">在命令提示字元中，將目前資料夾變更為 %btssolutionspath%\bpm，型別`SetupBPM.bat`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f3f08-198">At a command prompt, change the current folder to %BTSSolutionsPath%\BPM, type `SetupBPM.bat`, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3f08-199">在檔案中執行 SetupBPM.bat 之前， **%BTSInstallPath%/SDK/Scenarios/BPM/CSDWebApp/App_WebReferences/SouthridgeVideo_OrderBroker/OrderBrokerOrch_OrderPort.wsdl**和 **%BTSInstallPath%/SDK/Scenarios/BPM/OrderBroker_Proxy/App_Code/OrderBrokerOrch_OrderPort.asmx.cs**，所有 8f8bbebbb3fb375a 執行個體都取代為 XXXXXXXXXXXXXXXX。</span><span class="sxs-lookup"><span data-stu-id="f3f08-199">Before running SetupBPM.bat, in the files **%BTSInstallPath%/SDK/Scenarios/BPM/CSDWebApp/App_WebReferences/SouthridgeVideo_OrderBroker/OrderBrokerOrch_OrderPort.wsdl** and **%BTSInstallPath%/SDK/Scenarios/BPM/OrderBroker_Proxy/App_Code/OrderBrokerOrch_OrderPort.asmx.cs**, replace all instances of 8f8bbebbb3fb375a with XXXXXXXXXXXXXXXX.</span></span>  
  
     <span data-ttu-id="f3f08-200">SetupBPM.bat 會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f3f08-200">The SetupBPM.bat performs the following tasks:</span></span>  
  
    1.  <span data-ttu-id="f3f08-201">建立唯一的強式名稱金鑰 (SNK) 以簽章 BPM 解決方案的組件。</span><span class="sxs-lookup"><span data-stu-id="f3f08-201">Creates a unique strong name key (SNK) for signing the assemblies of the BPM Solution.</span></span>  
  
    2.  <span data-ttu-id="f3f08-202">從 SNK 擷取公開金鑰 Token。</span><span class="sxs-lookup"><span data-stu-id="f3f08-202">Extracts the public key token from the SNK.</span></span>  
  
    3.  <span data-ttu-id="f3f08-203">以公開 Token 更新繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="f3f08-203">Updates the binding files with the public token.</span></span>  
  
    4.  <span data-ttu-id="f3f08-204">建置 BPM 解決方案並安裝 OpsAdapter。</span><span class="sxs-lookup"><span data-stu-id="f3f08-204">Builds the BPM solution, and installs OpsAdapter.</span></span>  
  
    5.  <span data-ttu-id="f3f08-205">在 %BTSSolutionsPath%\Common 資料夾中建置 SSOApplicationConfig。</span><span class="sxs-lookup"><span data-stu-id="f3f08-205">Builds the SSOApplicationConfig in the %BTSSolutionsPath%\Common folder.</span></span>  
  
2.  <span data-ttu-id="f3f08-206">使用商務規則引擎部署精靈部署 Southridge Video 商務規則：</span><span class="sxs-lookup"><span data-stu-id="f3f08-206">Deploy the Southridge Video business rules using the Business Rule Engine Deployment Wizard:</span></span>  
  
    1.  <span data-ttu-id="f3f08-207">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則引擎部署精靈**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-207">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rules Engine Deployment Wizard**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f3f08-208">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="f3f08-208">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="f3f08-209">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-209">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
    2.  <span data-ttu-id="f3f08-210">在**歡迎**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-210">On the **Welcome** page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="f3f08-211">在**部署工作**頁面上，選取**匯入並發佈原則/詞彙至資料庫，從檔案**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-211">On the **Deployment Task** page, select **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="f3f08-212">在**原則存放區**頁面上，保留所有其他的預設設定，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-212">On the **Policy Store** page, keep all other default settings, and then click **Next**.</span></span>  
  
    5.  <span data-ttu-id="f3f08-213">在**匯入規則引擎原則/詞彙檔案**頁面上，按一下**瀏覽**，在 %BTSSolutionsPath%\BPM\Rules 資料夾中，選取 DecodeAndValidateOrderRules.xml 檔案，然後按一下  **下一步**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-213">On the **Import Rules Engine Policy/Vocabulary file** page, click **Browse**, select the DecodeAndValidateOrderRules.xml file in the %BTSSolutionsPath%\BPM\Rules folder, and then click **Next**.</span></span>  
  
    6.  <span data-ttu-id="f3f08-214">在**準備**頁面上，按一下**下一步**，然後在**匯入原則/詞彙**頁面上，按一下**下一步**</span><span class="sxs-lookup"><span data-stu-id="f3f08-214">On the **Ready** page, click **Next**, and then on the **Importing Policy/Vocabulary** page, click **Next**</span></span>  
  
    7.  <span data-ttu-id="f3f08-215">在 完成 頁面上，選取 **再次執行精靈**以開啟精靈，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-215">On the Completion page, select **Run the wizard again** to open the Wizard again, and then click **Finish**.</span></span>  
  
    8.  <span data-ttu-id="f3f08-216">在**歡迎**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-216">On the **Welcome** page, click **Next**.</span></span>  
  
    9. <span data-ttu-id="f3f08-217">在**部署工作**頁面上，選取**DeployPolicy**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-217">On the **Deployment Task** page, select **DeployPolicy**, and then click **Next**.</span></span>  
  
    10. <span data-ttu-id="f3f08-218">在**原則存放區**頁面上，保留所有其他的預設設定，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-218">On the **Policy Store** page, keep all other default settings, and then click **Next**.</span></span>  
  
    11. <span data-ttu-id="f3f08-219">在**部署原則**頁面上，選取**DecodeAndValidateOrder 1.0**中**規則引擎原則**下拉式清單，然後按一下**下一步**.</span><span class="sxs-lookup"><span data-stu-id="f3f08-219">On the **Deploy Policy** page, select **DecodeAndValidateOrder 1.0** in the **Rule Engine Policy** drop-down list, and then click **Next**.</span></span>  
  
    12. <span data-ttu-id="f3f08-220">在**準備**頁面上，按一下**下一步**，然後在**部署原則**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-220">On the **Ready** page, click **Next**, and then on the **Deploying Policy** page, click **Next**.</span></span>  
  
    13. <span data-ttu-id="f3f08-221">在 完成 頁面上，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-221">On the Completion page, click **Finish**.</span></span>  
  
3.  <span data-ttu-id="f3f08-222">若您將 BPM 方案安裝在 64 位元電腦上，請</span><span class="sxs-lookup"><span data-stu-id="f3f08-222">If you install the BPM solution on a 64-bit computer, then</span></span>  
  
    1.  <span data-ttu-id="f3f08-223">開啟 32 位元命令提示字元如下： 按一下**啟動**，按一下 **執行**，型別`%SYSTEMROOT%\SYSWOW64\CMD.EXE`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f3f08-223">Open a 32-bit command prompt as follow: Click **Start**, click **Run**, type `%SYSTEMROOT%\SYSWOW64\CMD.EXE`, and then press ENTER.</span></span>  
  
    2.  <span data-ttu-id="f3f08-224">在 32 位元命令提示字元，將目錄變更為 %BTSSolutionsPath%\BPM\Scripts 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f3f08-224">At the 32-bit command prompt, change the directory to the %BTSSolutionsPath%\BPM\Scripts folder.</span></span>  
  
    3.  <span data-ttu-id="f3f08-225">使用「記事本」開啟 CreateSouthridgeVideoApplication.cmd，然後以 "%SystemDrive%\Program Files\Common Files\Enterprise Single Sign-On\ssomanage.exe" 取代 "%CommonProgramFiles%\Enterprise Single Sign-On\ssomanage.exe"。</span><span class="sxs-lookup"><span data-stu-id="f3f08-225">Using Notepad, open the CreateSouthridgeVideoApplication.cmd, and then replace "%CommonProgramFiles%\Enterprise Single Sign-On\ssomanage.exe" with "%SystemDrive%\Program Files\Common Files\Enterprise Single Sign-On\ssomanage.exe".</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f3f08-226">在 32 位元命令提示字元，%CommonProgramFiles% 變數變更為 "%ProgramFiles(x86)%\Common Files"。</span><span class="sxs-lookup"><span data-stu-id="f3f08-226">At a 32-bit command prompt, the %CommonProgramFiles% variable is changed to "%ProgramFiles(x86)%\Common Files".</span></span> <span data-ttu-id="f3f08-227">因為即使在 64 位元的電腦上，SSO 系統管理公用程式還是安裝在 %ProgramFiles% 中，因此您必須修正路徑。</span><span class="sxs-lookup"><span data-stu-id="f3f08-227">Because the SSO administrative utility is installed in the %ProgramFiles% even on a 64-bit computer, you must fix the path.</span></span> <span data-ttu-id="f3f08-228">DeployBPM.cmd 會呼叫 CreateSouthridgeVideoApplication.cmd。</span><span class="sxs-lookup"><span data-stu-id="f3f08-228">The DeployBPM.cmd calls CreateSouthridgeVideoApplication.cmd.</span></span>  
  
    4.  <span data-ttu-id="f3f08-229">在 32 位元命令提示字元中輸入型別`DeployBPM.cmd`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f3f08-229">At the 32-bit command prompt, type type `DeployBPM.cmd`, and then press ENTER.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f3f08-230">DeployBPM.cmd 必須在 32-bit 命令提示字元執行，因為它包含存取 x86 物件的 VB Script，必須要有 x86 版本的 cscript.exe。</span><span class="sxs-lookup"><span data-stu-id="f3f08-230">The DeployBPM.cmd must be run at a 32-bit command prompt because it includes the VB Script accessing x86 objects that requires the x86 version of cscript.exe.</span></span>  
  
4.  <span data-ttu-id="f3f08-231">在命令提示字元中，將目前資料夾變更為 %btssolutionspath%\bpm\scripts，型別`DeployBPM.cmd`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f3f08-231">At a command prompt, change the current folder to %BTSSolutionsPath%\BPM\Scripts, type `DeployBPM.cmd`, and then press ENTER.</span></span> <span data-ttu-id="f3f08-232">DeployBPM.cmd 會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f3f08-232">The DeployBPM.cmd performs the following tasks:</span></span>  
  
    1.  <span data-ttu-id="f3f08-233">建立 BPM 解決方案的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f3f08-233">Creates BizTalk Applications for the BPM Solution.</span></span>  
  
    2.  <span data-ttu-id="f3f08-234">新增應用程式之間的參考。</span><span class="sxs-lookup"><span data-stu-id="f3f08-234">Adds references between the applications.</span></span>  
  
    3.  <span data-ttu-id="f3f08-235">匯入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="f3f08-235">Imports the binding files.</span></span>  
  
    4.  <span data-ttu-id="f3f08-236">部署 BAM 定義檔案。</span><span class="sxs-lookup"><span data-stu-id="f3f08-236">Deploys the BAM definition files.</span></span>  
  
    5.  <span data-ttu-id="f3f08-237">註冊 SouthridgeVideo 事件來源。</span><span class="sxs-lookup"><span data-stu-id="f3f08-237">Registers the SouthridgeVideo event source.</span></span>  
  
    6.  <span data-ttu-id="f3f08-238">建立「單一登入」(SSO) 附屬應用程式，並將組態值儲存至 SSO 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f3f08-238">Creates a Single Sign-On (SSO) affiliated application, and saves configuration values to the SSO application.</span></span>  
  
5.  <span data-ttu-id="f3f08-239">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="f3f08-239">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
    1.  <span data-ttu-id="f3f08-240">在**BizTalk Server 管理主控台**，依序展開**BizTalk 群組**，依序展開**應用程式**，依序展開**BTSScn.BPM.OrderBrokerApp**，依序展開**接收位置**，以滑鼠右鍵按一下**廠商-RP-RL**，然後按一下 內容。</span><span class="sxs-lookup"><span data-stu-id="f3f08-240">In the **BizTalk Server Administration Console**, expand **BizTalk Group**, expand **Applications**, expand **BTSScn.BPM.OrderBrokerApp**, expand **Receive Locations**, right-click **Vendor-RP-RL**, and then click Properties.</span></span>  
  
    2.  <span data-ttu-id="f3f08-241">上**屬性**對話方塊中，按一下 **設定**，然後輸入值為下表**傳輸屬性**對話方塊：</span><span class="sxs-lookup"><span data-stu-id="f3f08-241">On the **Properties** dialog box, click **Configure**, and then enter values as the following table on the **Transport Properties** dialog box:</span></span>  
  
        |<span data-ttu-id="f3f08-242">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="f3f08-242">Property Name</span></span>|<span data-ttu-id="f3f08-243">值</span><span class="sxs-lookup"><span data-stu-id="f3f08-243">Value</span></span>|  
        |-------------------|-----------|  
        |<span data-ttu-id="f3f08-244">**Server**</span><span class="sxs-lookup"><span data-stu-id="f3f08-244">**Server**</span></span>|`localhost`|  
        |<span data-ttu-id="f3f08-245">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="f3f08-245">**User Name**</span></span>|<span data-ttu-id="f3f08-246">\<*BizTalk 服務帳戶名稱*\></span><span class="sxs-lookup"><span data-stu-id="f3f08-246">\<*BizTalk service account name*\></span></span>|  
        |<span data-ttu-id="f3f08-247">**密碼**</span><span class="sxs-lookup"><span data-stu-id="f3f08-247">**Password**</span></span>|<span data-ttu-id="f3f08-248">\<*BizTalk 服務帳戶密碼*\></span><span class="sxs-lookup"><span data-stu-id="f3f08-248">\<*BizTalk service account password*\></span></span>|  
  
6.  <span data-ttu-id="f3f08-249">執行 BPM 解決方案。</span><span class="sxs-lookup"><span data-stu-id="f3f08-249">Run the BPM Solution.</span></span> <span data-ttu-id="f3f08-250">如需執行解決方案的詳細資訊，請參閱[如何執行商務程序管理解決方案](../core/how-to-run-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="f3f08-250">For more information about running the solution, see [How to Run the Business Process Management Solution](../core/how-to-run-the-business-process-management-solution.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f3f08-251">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f3f08-251">Next Steps</span></span>  
 <span data-ttu-id="f3f08-252">您可以測試商務管理解決方案中的運作方式[如何執行商務程序管理解決方案](../core/how-to-run-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="f3f08-252">You test how the Business Management Solution works in [How to Run the Business Process Management Solution](../core/how-to-run-the-business-process-management-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f08-253">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3f08-253">See Also</span></span>  
 <span data-ttu-id="f3f08-254">[安裝商務程序管理解決方案之前](../core/before-installing-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="f3f08-254">[Before Installing the Business Process Management Solution](../core/before-installing-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="f3f08-255">商務程序管理解決方案的開發人員電腦設定</span><span class="sxs-lookup"><span data-stu-id="f3f08-255">Developer Machine Setup for the Business Process Management Solution</span></span>](../core/developer-machine-setup-for-the-business-process-management-solution.md)