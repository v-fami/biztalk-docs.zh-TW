---
title: "How to Install 虛設常式版本的服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IIS, installing virtual directories [service solutions]
- service solution tutorial, IIS virtual directories
- service solution tutorial, stub version
- deploying, BAM solutions [service solutions]
- service solution tutorial, solutions [BAM]
- service solution tutorial, service solutions
- SSO, configuring
- IBM WebSphere MQ Client
- service solution tutorial, IBM WebSphere MQ Client
- installing, tutorials
- service solutions, deploying
- service solution tutorial, SSO
- BAM, deploying solutions
- service solution tutorial, building solutions
- service solution tutorial, installing
ms.assetid: 45de7681-4df0-47a4-a02c-509140423a1e
caps.latest.revision: "53"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adaf5cb0117e0d571e0be0ddd42350ce3af2ba80
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-install-the-stub-version-of-the-service-oriented-solution"></a><span data-ttu-id="4d1c5-102">如何安裝服務導向解決方案的虛設常式版本</span><span class="sxs-lookup"><span data-stu-id="4d1c5-102">How to Install the Stub Version of the Service Oriented Solution</span></span>
<span data-ttu-id="4d1c5-103">下列步驟描述在安裝服務導向解決方案的虛設常式版本之前，應如何準備電腦，以及如何在電腦上安裝解決方案。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-103">The following steps describe how to prepare your computer before you install the stub version of the service oriented solution, and then how to install the solution on your computer.</span></span>  
  
-   [<span data-ttu-id="4d1c5-104">準備安裝服務導向解決方案的虛設常式版本的電腦</span><span class="sxs-lookup"><span data-stu-id="4d1c5-104">Prepare the computer for installing the stub version of the Service Oriented Solution</span></span>](#step1)  
  
-   [<span data-ttu-id="4d1c5-105">安裝 IBM WebSphere MQ Client for Windows</span><span class="sxs-lookup"><span data-stu-id="4d1c5-105">Install the IBM WebSphere MQ Client for Windows</span></span>](#step3)  
  
-   [<span data-ttu-id="4d1c5-106">在 IIS 中建立服務導向解決方案的虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="4d1c5-106">Create the virtual directories in IIS for the Service Oriented Solution</span></span>](#step5)  
  
-   [<span data-ttu-id="4d1c5-107">建置服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="4d1c5-107">Build the Service Oriented Solution</span></span>](#step7)  
  
-   [<span data-ttu-id="4d1c5-108">在 SSO 資料庫中建立的企業單一登入 (SSO) 項目和值</span><span class="sxs-lookup"><span data-stu-id="4d1c5-108">Create the Enterprise Single Sign-On (SSO) entries and values in the SSO database</span></span>](#step9)  
  
-   [<span data-ttu-id="4d1c5-109">部署服務導向解決方案的 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="4d1c5-109">Deploy the BAM definition for the Service Oriented Solution</span></span>](#step11)  
  
-   [<span data-ttu-id="4d1c5-110">部署服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="4d1c5-110">Deploy the Service Oriented Solution</span></span>](#step13)  
  
##  <a name="step1"></a><span data-ttu-id="4d1c5-111">準備安裝服務導向解決方案的虛設常式版本的電腦</span><span class="sxs-lookup"><span data-stu-id="4d1c5-111">Prepare the computer for installing the stub version of the Service Oriented Solution</span></span>  
  
#### <a name="to-prepare-the-computer-for-installing-the-stub-version-of-the-service-oriented-solution"></a><span data-ttu-id="4d1c5-112">準備安裝服務導向解決方案之虛設常式版本的電腦</span><span class="sxs-lookup"><span data-stu-id="4d1c5-112">To prepare the computer for installing the stub version of the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="4d1c5-113">請確定**Default Web Site**設定為使用 ASP.NET 2.X。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-113">Make sure that the **Default Web Site** is configured to use ASP.NET 2.X.</span></span>  
  
    1.  <span data-ttu-id="4d1c5-114">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.</span><span class="sxs-lookup"><span data-stu-id="4d1c5-114">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
    2.  <span data-ttu-id="4d1c5-115">在**網際網路資訊服務 (IIS) 管理員**，機器名稱時，依序展開**網站**，依序展開**Default Web Site**，展開**aspnet_client**，依序展開**system_web**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-115">In the **Internet Information Services (IIS) Manager**, the machine name, expand  **Sites**, expand **Default Web Site**, expand **aspnet_client**, expand **system_web**.</span></span>  
  
    3.  <span data-ttu-id="4d1c5-116">請確定子資料夾 2.X。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-116">Make sure that the sub-folder is 2.X.</span></span>  
  
2.  <span data-ttu-id="4d1c5-117">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下 **服務**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-117">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Services**.</span></span> <span data-ttu-id="4d1c5-118">使用**服務**主控台中，請確定下列服務正在執行：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-118">Using the **Services** console, make sure that the following services are running:</span></span>  
  
    -   <span data-ttu-id="4d1c5-119">**World Wide Web 發行**</span><span class="sxs-lookup"><span data-stu-id="4d1c5-119">**World Wide Web Publishing**</span></span>  
  
3.  <span data-ttu-id="4d1c5-120">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，按一下 **電腦管理**主控台，然後再加入本機系統管理員群組的 BizTalk 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-120">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Computer Management** console, and then add the BizTalk service account to the local Administrators group.</span></span>  
  
4.  <span data-ttu-id="4d1c5-121">如果您安裝 Windows SharePoint Services 時，排除 （根） 的**Default Web Site**從 Windows SharePoint Services 受管理的路徑，如下所示： 按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下  **SharePoint 管理中心內**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-121">If you installed Windows SharePoint Services, exclude the (root) of the **Default Web Site** from Windows SharePoint Services Managed Paths as follows: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
    1.  <span data-ttu-id="4d1c5-122">在下**虛擬伺服器設定**，選取**設定虛擬伺服器設定**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-122">Under **Virtual Server Configuration**, select **Configure virtual server settings**.</span></span>  
  
    2.  <span data-ttu-id="4d1c5-123">在**虛擬伺服器清單**頁面上，按一下**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-123">On the **Virtual Server List** page, click **Default Web Site**.</span></span>  
  
    3.  <span data-ttu-id="4d1c5-124">在**虛擬伺服器設定**頁面上，按一下**定義管理的路徑**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-124">On the **Virtual Server Settings** page, click **Define managed paths**.</span></span>  
  
    4.  <span data-ttu-id="4d1c5-125">在**包含路徑**區段**定義受管理的路徑**頁面上，選取**根**，然後按一下 **移除選取的路徑**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-125">In the **Included Paths** section of the **Defined Managed Path** page, select **Root** and then click **Remove selected paths**.</span></span>  
  
    5.  <span data-ttu-id="4d1c5-126">在命令提示字元，執行 IISReset。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-126">At a command prompt, perform an IISReset.</span></span>  
  
5.  <span data-ttu-id="4d1c5-127">登出電腦，然後以 BizTalk 服務帳戶的身分登入電腦。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-127">Log off the computer, and then log on to the computer as the BizTalk service account.</span></span>  
  
6.  <span data-ttu-id="4d1c5-128">開啟命令提示字元，輸入下列命令，然後按 ENTER 以設定 %BTSSolutionsPath% 環境。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-128">Open a command prompt, type the following command, and then press ENTER to set the %BTSSolutionsPath% environment.</span></span> <span data-ttu-id="4d1c5-129">然後結束命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-129">Then, exit the command prompt.</span></span>  
  
    -   <span data-ttu-id="4d1c5-130">setx BTSSolutionsPath "[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"</span><span class="sxs-lookup"><span data-stu-id="4d1c5-130">setx BTSSolutionsPath "[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4d1c5-131">若您使用 64 位元的電腦，請使用 %ProgramFiles(x86)% 取代 %ProgramFiles%。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-131">If you are using a 64-bit computer, use %ProgramFiles(x86)% instead of %ProgramFiles%.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4d1c5-132">如需有關 SETX 命令的詳細資訊，請參閱 Microsoft TechNet 網站，網址[http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831)。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-132">For more information about the SETX command, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span></span>  
  
##  <a name="step3"></a><span data-ttu-id="4d1c5-133">安裝 IBM WebSphere MQ Client for Windows</span><span class="sxs-lookup"><span data-stu-id="4d1c5-133">Install the IBM WebSphere MQ Client for Windows</span></span>  
  
#### <a name="to-install-the-ibm-websphere-mq-client-for-windows"></a><span data-ttu-id="4d1c5-134">安裝 IBM WebSphere MQ Client for Windows</span><span class="sxs-lookup"><span data-stu-id="4d1c5-134">To install the IBM WebSphere MQ Client for Windows</span></span>  
  
1.  <span data-ttu-id="4d1c5-135">下載最新版本的 IBM WebSphere MQ Client for Windows。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-135">Download the latest version of IBM WebSphere MQ Client for Windows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d1c5-136">即使解決方案的虛設常式版本不需要 IBM WebSphere Server，但因為用戶端應用程式會參考 IBM WebSphere MQ Client for Windows 提供的 amqmdnet.dll 檔案，所以您必須安裝它。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-136">Even if the stub version of the solution doesn't require IBM WebSphere Server, the client application references the amqmdnet.dll file provided by IBM WebSphere MQ Client for Windows, so you must install it.</span></span> <span data-ttu-id="4d1c5-137">虛設常式版本的用戶端實際上不會呼叫 DLL 中的 API。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-137">The client of the stub version does not actually call an API in the DLL.</span></span> <span data-ttu-id="4d1c5-138">只有編譯和執行用戶端應用程式才需要它。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-138">It is required only for compiling and running the client application.</span></span> <span data-ttu-id="4d1c5-139">您可以從 IBM 網站下載 IBM WebSphere MQ Client for Windows。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-139">You can download IBM WebSphere MQ Client for Windows from the IBM Web site.</span></span>  
  
2.  <span data-ttu-id="4d1c5-140">安裝 IBM WebSphere MQ Client for Windows。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-140">Install IBM WebSphere MQ Client for Windows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d1c5-141">您不需要設定 IBM WebSphere MQ Client for Windows。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-141">You don't need to configure IBM WebSphere MQ Client for Windows.</span></span> <span data-ttu-id="4d1c5-142">請保留所有預設設定。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-142">Keep all of the default settings.</span></span>  
  
3.  <span data-ttu-id="4d1c5-143">將 .NET 組件的 WebSphere MQ 類別新增至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-143">Add WebSphere MQ classes for the .NET assembly to the global assembly cache (GAC).</span></span>  
  
    1.  <span data-ttu-id="4d1c5-144">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元中，瀏覽至目錄\<IBM MQSeries 安裝目錄\>\bin。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-144">At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, navigate to the directory \<IBM MQSeries Installation Directory\>\bin.</span></span>  
  
    2.  <span data-ttu-id="4d1c5-145">執行下列命令 (請確定 gacutil.exe 在路徑環境中)：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-145">Run the following command (make sure gacutil.exe is in the path environment):</span></span>  
  
         `gacutil.exe /i amqmdnet.dll`  
  
##  <a name="step5"></a><span data-ttu-id="4d1c5-146">在 IIS 中建立服務導向解決方案的虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="4d1c5-146">Create the virtual directories in IIS for the Service Oriented Solution</span></span>  
  
#### <a name="to-create-the-virtual-directories-in-iis-for-the-service-oriented-solution"></a><span data-ttu-id="4d1c5-147">在 IIS 中建立服務導向解決方案的虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="4d1c5-147">To create the virtual directories in IIS for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="4d1c5-148">在**網際網路資訊服務 (IIS) 管理員**，以滑鼠右鍵按一下**應用程式集區**，選取**新增應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-148">In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **Add Application Pool**.</span></span>  
  
     <span data-ttu-id="4d1c5-149">上**新增應用程式集區** 對話方塊中，輸入`SSOStubAppPool`中**名稱**文字方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-149">On the **Add Application Pool** dialog box, type `SSOStubAppPool` in the **Name** text box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="4d1c5-150">服務導向解決方案使用的虛擬目錄包括協調流程之虛設常式版本的已發佈 Web 服務、虛設常式 SAP Web 服務、虛設常式付款追蹤器 Web 服務，以及虛設常式擱置交易 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-150">The virtual directories that service-oriented solution uses include the published Web service for the stub version of orchestrations, the stub SAP Web service, the stub Payment Tracker Web service, and the stub Pending Transaction Web service.</span></span>  
  
2.  <span data-ttu-id="4d1c5-151">在**網際網路資訊服務 (IIS) 管理員**，以滑鼠右鍵按一下您剛應用程式集區建立，，然後按一下**進階設定**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-151">In the **Internet Information Services (IIS) Manager**, right-click the application pool that you just created, and then click **Advanced Settings**.</span></span>  
  
3.  <span data-ttu-id="4d1c5-152">按一下右邊的資料行中**識別**屬性，然後按一下省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-152">Click in the column to the right of the **Identity** property, and then click the ellipsis (**…**) button.</span></span>  
  
4.  <span data-ttu-id="4d1c5-153">在**應用程式集區識別**對話方塊中，選取**自訂帳戶**選項，然後再按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-153">In the **Application Pool Identity** dialog box, select the **Custom Account** option, and then click **Set**.</span></span>  
  
5.  <span data-ttu-id="4d1c5-154">在**設定認證**對話方塊中，指定使用者名稱和密碼，確認密碼，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-154">In the **Set Credentials** dialog box, specify a username and password, confirm the password, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d1c5-155">此使用者必須具有執行協調流程 Proxy Web 服務的權限，並且必須新增至 BizTalk Server 系統管理員、SSO 系統管理員或 SSO 分支機構系統管理員群組其中之一</span><span class="sxs-lookup"><span data-stu-id="4d1c5-155">This user must have permission to execute the Orchestration Proxy Web service, and must be added to one of the BizTalk Server Administrators, SSO Administrators, or SSO Affiliated Administrators groups</span></span>  
  
6.  <span data-ttu-id="4d1c5-156">按一下**確定**關閉**應用程式集區識別** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-156">Click **OK** to close the **Application Pool Identity** dialog box.</span></span>  
  
7.  <span data-ttu-id="4d1c5-157">按一下 **[確定]** 以關閉 **[進階設定]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-157">Click **OK** to close the **Advanced Settings** dialog box.</span></span>  
  
8.  <span data-ttu-id="4d1c5-158">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下 **虛擬目錄**執行**虛擬目錄建立精靈**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-158">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
    1.  <span data-ttu-id="4d1c5-159">使用**虛擬目錄建立精靈**，proxy Web 服務配接器版本建立下列虛擬目錄：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-159">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
         <span data-ttu-id="4d1c5-160">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub</span><span class="sxs-lookup"><span data-stu-id="4d1c5-160">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub</span></span>  
  
         <span data-ttu-id="4d1c5-161">路徑 = \<BizTalk 安裝目錄\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Stub</span><span class="sxs-lookup"><span data-stu-id="4d1c5-161">PATH = \<BizTalk Install Directory\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Stub</span></span>  
  
         <span data-ttu-id="4d1c5-162">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="4d1c5-162">Access Permissions = Read, Run scripts</span></span>  
  
    2.  <span data-ttu-id="4d1c5-163">使用**虛擬目錄建立精靈**，proxy Web 服務配接器版本建立下列虛擬目錄：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-163">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
         <span data-ttu-id="4d1c5-164">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP</span><span class="sxs-lookup"><span data-stu-id="4d1c5-164">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP</span></span>  
  
         <span data-ttu-id="4d1c5-165">路徑 = \<BizTalk 安裝目錄\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP</span><span class="sxs-lookup"><span data-stu-id="4d1c5-165">PATH = \<BizTalk Install Directory\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP</span></span>  
  
         <span data-ttu-id="4d1c5-166">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="4d1c5-166">Access Permissions = Read, Run scripts</span></span>  
  
    3.  <span data-ttu-id="4d1c5-167">使用**虛擬目錄建立精靈**，proxy Web 服務配接器版本建立下列虛擬目錄：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-167">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
         <span data-ttu-id="4d1c5-168">別名 = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span><span class="sxs-lookup"><span data-stu-id="4d1c5-168">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span></span>  
  
         <span data-ttu-id="4d1c5-169">路徑 = \<BizTalk 安裝目錄\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span><span class="sxs-lookup"><span data-stu-id="4d1c5-169">PATH = \<BizTalk Install Directory\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span></span>  
  
         <span data-ttu-id="4d1c5-170">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="4d1c5-170">Access Permissions = Read, Run scripts</span></span>  
  
    4.  <span data-ttu-id="4d1c5-171">使用**虛擬目錄建立精靈**，proxy Web 服務配接器版本建立下列虛擬目錄：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-171">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
         <span data-ttu-id="4d1c5-172">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker</span><span class="sxs-lookup"><span data-stu-id="4d1c5-172">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker</span></span>  
  
         <span data-ttu-id="4d1c5-173">路徑 = \<BizTalk 安裝目錄\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PaymentTrack</span><span class="sxs-lookup"><span data-stu-id="4d1c5-173">PATH = \<BizTalk Install Directory\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PaymentTrack</span></span>  
  
         <span data-ttu-id="4d1c5-174">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="4d1c5-174">Access Permissions = Read, Run scripts</span></span>  
  
9. <span data-ttu-id="4d1c5-175">在**網際網路資訊服務 (IIS) 管理員**，展開**網站**展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub，按一下 **屬性**，，然後修改設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-175">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="4d1c5-176">在**虛擬目錄**索引標籤上，設定**應用程式集區**至**SSOStubAppPool**您剛建立。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-176">On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.</span></span>  
  
    2.  <span data-ttu-id="4d1c5-177">按一下**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，選取**只整合式 Windows 驗證啟用**，然後清除其他**驗證存取**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-177">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="4d1c5-178">按一下**確定**結束。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-178">Click **OK** to exit.</span></span>  
  
10. <span data-ttu-id="4d1c5-179">在**網際網路資訊服務 (IIS) 管理員**，展開**網站**展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP，按一下 **屬性**，，然後修改設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-179">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="4d1c5-180">在**虛擬目錄**索引標籤上，設定**應用程式集區**至**SSOStubAppPool**您剛建立。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-180">On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.</span></span>  
  
    2.  <span data-ttu-id="4d1c5-181">按一下**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**.</span><span class="sxs-lookup"><span data-stu-id="4d1c5-181">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable Anonymous Access**.</span></span> <span data-ttu-id="4d1c5-182">按一下**確定**結束。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-182">Click **OK** to exit.</span></span>  
  
11. <span data-ttu-id="4d1c5-183">在**網際網路資訊服務 (IIS) 管理員**，展開**網站**展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions，按一下 **屬性**，，然後修改設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-183">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="4d1c5-184">在**虛擬目錄**索引標籤上，設定**應用程式集區**至**SSOStubAppPool**您剛建立。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-184">On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.</span></span>  
  
    2.  <span data-ttu-id="4d1c5-185">按一下**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**.</span><span class="sxs-lookup"><span data-stu-id="4d1c5-185">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable Anonymous Access**.</span></span> <span data-ttu-id="4d1c5-186">按一下**確定**結束。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-186">Click **OK** to exit.</span></span>  
  
12. <span data-ttu-id="4d1c5-187">在**網際網路資訊服務 (IIS) 管理員**，展開**網站**展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker，按一下 **屬性**，，然後修改設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-187">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="4d1c5-188">在**虛擬目錄**索引標籤上，設定**應用程式集區**至**SSOStubAppPool**您剛建立。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-188">On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.</span></span>  
  
    2.  <span data-ttu-id="4d1c5-189">按一下**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**.</span><span class="sxs-lookup"><span data-stu-id="4d1c5-189">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable Anonymous Access**.</span></span> <span data-ttu-id="4d1c5-190">按一下**確定**結束。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-190">Click **OK** to exit.</span></span>  
  
##  <a name="step7"></a><span data-ttu-id="4d1c5-191">建置服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="4d1c5-191">Build the Service Oriented Solution</span></span>  
  
#### <a name="to-build-the-service-oriented-solution"></a><span data-ttu-id="4d1c5-192">建置服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="4d1c5-192">To build the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="4d1c5-193">啟動**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-193">Start **Visual Studio Command Prompt**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d1c5-194">在檔案**%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Inline\app_code\customerserviceport.asmx.cs**和**%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Stub\app_code\customerserviceport.asmx.cs**，17f20caea2afcc8c 的所有執行個體取代為 a1054514fc67bded。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-194">In the files **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Inline\app_code\customerserviceport.asmx.cs** and **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Stub\app_code\customerserviceport.asmx.cs**, replace all the instances of 17f20caea2afcc8c with a1054514fc67bded.</span></span>  
  
2.  <span data-ttu-id="4d1c5-195">在 Visual Studio 命令提示字元中，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln 資料夾，然後執行下列命令，以建置服務導向方案的虛設常式版本。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-195">At the Visual Studio Command Prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln folder, and then run the following command to build the stub version of service-oriented solution.</span></span>  
  
    -   `SetupBTSSoln.bat`  
  
    > [!NOTE]
    >  <span data-ttu-id="4d1c5-196">在下列檔案中，將所有 17f20caea2afcc8c 執行個體取代為目前的公開金鑰 Token。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-196">In the files listed below, replace all the instances of 17f20caea2afcc8c with the current public key token.</span></span>  
    >   
    >  -   <span data-ttu-id="4d1c5-197">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_CustomerServiceResponse.btm.cs</span><span class="sxs-lookup"><span data-stu-id="4d1c5-197">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_CustomerServiceResponse.btm.cs</span></span>  
    > -   <span data-ttu-id="4d1c5-198">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_ErrorResponse.btm.cs</span><span class="sxs-lookup"><span data-stu-id="4d1c5-198">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_ErrorResponse.btm.cs</span></span>  
    > -   <span data-ttu-id="4d1c5-199">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CreditLimitResponse.btm.cs</span><span class="sxs-lookup"><span data-stu-id="4d1c5-199">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CreditLimitResponse.btm.cs</span></span>  
    > -   <span data-ttu-id="4d1c5-200">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CustomerServiceResponseDenied.btm.cs</span><span class="sxs-lookup"><span data-stu-id="4d1c5-200">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CustomerServiceResponseDenied.btm.cs</span></span>  
    > -   <span data-ttu-id="4d1c5-201">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_LastPaymentResponseTimeout.btm.cs</span><span class="sxs-lookup"><span data-stu-id="4d1c5-201">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_LastPaymentResponseTimeout.btm.cs</span></span>  
    > -   <span data-ttu-id="4d1c5-202">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_PendingTransactionResponse.btm.cs</span><span class="sxs-lookup"><span data-stu-id="4d1c5-202">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_PendingTransactionResponse.btm.cs</span></span>  
  
##  <a name="step9"></a><span data-ttu-id="4d1c5-203">在 SSO 資料庫中建立的企業單一登入 (SSO) 項目和值</span><span class="sxs-lookup"><span data-stu-id="4d1c5-203">Create the Enterprise Single Sign-On (SSO) entries and values in the SSO database</span></span>  
  
#### <a name="to-create-the-enterprise-single-sign-on-sso-entries-and-values-in-the-sso-database"></a><span data-ttu-id="4d1c5-204">在 SSO 資料庫中建立企業單一登入 (SSO) 項目與值</span><span class="sxs-lookup"><span data-stu-id="4d1c5-204">To create the Enterprise Single Sign-On (SSO) entries and values in the SSO database</span></span>  
  
1.  <span data-ttu-id="4d1c5-205">開啟命令提示字元，將目前的目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts，然後執行下列目錄以設定「企業單一登入」資料夾的 PATH 環境。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-205">Open a command prompt, change the current directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts, and then run the following command to set the PATH environment for the Enterprise Single Sign-On folder.</span></span>  
  
    -   `Set PATH=%PATH%;%ProgramFiles%\"Common Files\Enterprise Single Sign-On"`  
  
2.  <span data-ttu-id="4d1c5-206">在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾，使用「記事本」開啟 ConfigStoreApp.xml，然後檢視檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-206">At the command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, open ConfigStoreApp.xml using Notepad, and then review the contents of the file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d1c5-207">此檔案會定義 SSO 中實例用以儲存組態參數的組態存放區應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-207">This file defines the configuration store application in SSO that the scenario uses to store configuration parameters.</span></span> <span data-ttu-id="4d1c5-208">部分組態參數包括**逾時**用來與 SAP 通訊 （適用於所有三個版本） 的值。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-208">Some of the configuration parameters include the **Timeout** value used to communicate with SAP (for all three versions).</span></span> <span data-ttu-id="4d1c5-209">不需要變更此檔案。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-209">No changes to this file are necessary.</span></span>  
  
3.  <span data-ttu-id="4d1c5-210">在命令提示字元，執行下列命令以建立 SSO 組態存放區應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-210">At the command prompt, run the following command to create the SSO configuration store application.</span></span>  
  
    -   `ssomanage -createapps ConfigStoreApp.xml`  
  
4.  <span data-ttu-id="4d1c5-211">在命令提示字元，使用「記事本」開啟 SetConfigValuesInSSO.cmd，然後檢視檔案的內容</span><span class="sxs-lookup"><span data-stu-id="4d1c5-211">At the command prompt, open SetConfigValuesInSSO.cmd using Notepad, and then review the contents of the file</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d1c5-212">此命令檔設定 SSO 資料庫中的組態參數值。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-212">This command file sets the values of the configuration parameters in the SSO database.</span></span> <span data-ttu-id="4d1c5-213">它包含數組設定命令檔開頭處本機變數值的陳述式。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-213">It contains several set statements that set the values in local variables in the beginning of the command file.</span></span> <span data-ttu-id="4d1c5-214">**SAPAdapterTimeout**， **PendingTransactionsAdapterTimeout**，和**PaymentTrackingAdapterTimeout**值用於虛設常式和配接器版本。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-214">The **SAPAdapterTimeout**, **PendingTransactionsAdapterTimeout**, and **PaymentTrackingAdapterTimeout** values are used in the stub and adapter version.</span></span> <span data-ttu-id="4d1c5-215">其餘的值則用於內嵌版本中。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-215">The remaining values are used in the inline version.</span></span> <span data-ttu-id="4d1c5-216">對於虛設常式版本，此檔案不需要變更。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-216">No changes to this file are necessary for stub version.</span></span>  
  
5.  <span data-ttu-id="4d1c5-217">在命令提示字元中，輸入`SetConfigValuesInSSO.cmd`，然後按 ENTER，將值儲存在 SSO 組態存放區應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-217">At the command prompt, type `SetConfigValuesInSSO.cmd`, and then press ENTER to store the values in the SSO configuration store application.</span></span>  
  
6.  <span data-ttu-id="4d1c5-218">在命令提示字元，執行下列命令以便在 SSO 中啟用票證：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-218">At the command prompt, run the following command to enable tickets in SSO:</span></span>  
  
    -   `ssomanage -tickets yes yes`  
  
##  <a name="step11"></a><span data-ttu-id="4d1c5-219">部署服務導向解決方案的 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="4d1c5-219">Deploy the BAM definition for the Service Oriented Solution</span></span>  
  
#### <a name="to-deploy-the-bam-definition-for-the-service-oriented-solution"></a><span data-ttu-id="4d1c5-220">部署服務導向解決方案的 BAM 定義</span><span class="sxs-lookup"><span data-stu-id="4d1c5-220">To deploy the BAM definition for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="4d1c5-221">在命令提示字元，輸入下列命令，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-221">At a command prompt, type the following command, and then press ENTER.</span></span> <span data-ttu-id="4d1c5-222">如此可設定尋找 BAM 公用程式的路徑：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-222">This sets the path to find the BAM utility:</span></span>  
  
    -   <span data-ttu-id="4d1c5-223">設定 PATH=%PATH%;%programfiles%\Microsoft BizTalk Server\Tracking</span><span class="sxs-lookup"><span data-stu-id="4d1c5-223">SET PATH=%PATH%;%programfiles%\Microsoft BizTalk Server\Tracking</span></span>  
  
2.  <span data-ttu-id="4d1c5-224">在命令提示字元中，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\BAM 資料夾，輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-224">At the command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\BAM folder, and type the following command, and then press ENTER:</span></span>  
  
    -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  
  
        > [!NOTE]
        >  <span data-ttu-id="4d1c5-225">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-225">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
##  <a name="step13"></a><span data-ttu-id="4d1c5-226">部署服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="4d1c5-226">Deploy the Service Oriented Solution</span></span>  
  
#### <a name="to-deploy-the-service-oriented-solution"></a><span data-ttu-id="4d1c5-227">部署服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="4d1c5-227">To deploy the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="4d1c5-228">開啟命令提示字元，並將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-228">Open a command prompt and change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.</span></span>  
  
2.  <span data-ttu-id="4d1c5-229">修改**DeployStubBinding.cmd**檔案以 「 發行 」 取代 「 偵錯 」 和 「 開發 」 的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-229">Modify the **DeployStubBinding.cmd** file by replacing all the instances of “debug” and “development” with “release”.</span></span>  
  
3.  <span data-ttu-id="4d1c5-230">開啟命令提示字元，並將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-230">Open a command prompt and change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.</span></span> <span data-ttu-id="4d1c5-231">輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="4d1c5-231">Type the following command, and then press ENTER:</span></span>  
  
    -   `DeployStubBinding.cmd`  
  
4.  <span data-ttu-id="4d1c5-232">在命令提示字元，執行下列命令以啟動虛設常式版本的協調流程</span><span class="sxs-lookup"><span data-stu-id="4d1c5-232">At the command prompt, run the following command to start the orchestrations for the stub version</span></span>  
  
    -   `Startstub.vbs`  
  
## <a name="next-steps"></a><span data-ttu-id="4d1c5-233">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4d1c5-233">Next Steps</span></span>  
 <span data-ttu-id="4d1c5-234">您可以測試服務導向解決方案的虛設常式版本中的運作方式[如何執行服務導向解決方案](../core/how-to-run-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="4d1c5-234">You test how the stub version of the service-oriented solution works in [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1c5-235">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d1c5-235">See Also</span></span>  
 <span data-ttu-id="4d1c5-236">[然後再安裝服務導向解決方案](../core/before-installing-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="4d1c5-236">[Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="4d1c5-237">[如何安裝內嵌和配接器版本的服務導向解決方案](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="4d1c5-237">[How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="4d1c5-238">服務導向解決方案的開發人員電腦設定</span><span class="sxs-lookup"><span data-stu-id="4d1c5-238">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)