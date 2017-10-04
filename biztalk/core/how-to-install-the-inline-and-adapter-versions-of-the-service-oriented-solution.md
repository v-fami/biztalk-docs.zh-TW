---
title: "如何安裝內嵌和配接器版本的服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificate services
- service solution tutorial, affiliat applications [SSO]
- service solution tutorial, adapter version
- service solution tutorial, Web services
- service solution tutorial, definition files [BAM]
- service solution tutorial, COM+ applications
- service solution tutorial, virtual directories
- service solution tutorial, testing connectivity
- TI components
- MQSeries queues, creating
- service solution tutorial, deploying
- service solution tutorial, MQSeries adapters
- service solution tutorial, mainframe CICS applications
- service solution tutorial, certificate services
- service solution tutorial, back-end systems
- service solution tutorial, MQSeries queues
- service solution tutorial, remote environments
- certificates, creating requests
- service solution tutorial, starting service
- service solution tutorial, TI components
- service solution tutorial, inline version
- CICS application
- service solution tutorial, installing
- service solution tutorial, deleting stub version
- service solution tutorial, certificates
ms.assetid: 6050cfe9-4e94-4a55-8b24-fbcc74d9e8f4
caps.latest.revision: "97"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb7de8939037f9e7647c62c1164e3c3de3ab378c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution"></a><span data-ttu-id="9bb36-102">如何安裝服務導向解決方案的內嵌與配接器版本</span><span class="sxs-lookup"><span data-stu-id="9bb36-102">How to Install the Inline and Adapter Versions of the Service Oriented Solution</span></span>
<span data-ttu-id="9bb36-103">下列步驟描述如何準備安裝服務導向解決方案內嵌與配接器版本的電腦，以及如何在此電腦上安裝解決方案。</span><span class="sxs-lookup"><span data-stu-id="9bb36-103">The following steps describe how to prepare the computer for installing the inline and adapter versions of the service oriented solution, and how to install the solution on this computer.</span></span>  
  
-   [<span data-ttu-id="9bb36-104">準備安裝服務導向解決方案配接器與內嵌版本的電腦</span><span class="sxs-lookup"><span data-stu-id="9bb36-104">Prepare the computer for installing the adapter and inline versions of the Service Oriented Solution</span></span>](#step1)  
  
-   [<span data-ttu-id="9bb36-105">移除服務導向解決方案的虛設常式版本</span><span class="sxs-lookup"><span data-stu-id="9bb36-105">Remove the stub version of the Service Oriented Solution</span></span>](#step3)  
  
-   [<span data-ttu-id="9bb36-106">準備後端系統，服務導向解決方案存取</span><span class="sxs-lookup"><span data-stu-id="9bb36-106">Prepare the back-end systems for the Service Oriented Solution to access</span></span>](#step5)  
  
-   [<span data-ttu-id="9bb36-107">設定 Web 伺服器針對安全通訊端層 (SSL)</span><span class="sxs-lookup"><span data-stu-id="9bb36-107">Configure the Web server for Secure Socket Layers (SSL)</span></span>](#step7)  
  
-   [<span data-ttu-id="9bb36-108">建立後端系統的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9bb36-108">Create the Web services for the back-end systems</span></span>](#step9)  
  
-   [<span data-ttu-id="9bb36-109">建立服務導向解決方案的 TI 元件</span><span class="sxs-lookup"><span data-stu-id="9bb36-109">Create the TI component for the Service Oriented Solution</span></span>](#step11)  
  
-   [<span data-ttu-id="9bb36-110">建立協調流程的虛擬目錄的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9bb36-110">Create the virtual directories for the orchestration Web services</span></span>](#step13)  
  
-   [<span data-ttu-id="9bb36-111">建置服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9bb36-111">Build the Service Oriented Solution</span></span>](#step15)  
  
-   [<span data-ttu-id="9bb36-112">建立 SSO 分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="9bb36-112">Create the SSO affiliate applications</span></span>](#step17)  
  
-   [<span data-ttu-id="9bb36-113">部署服務導向解決方案的 BAM 定義檔案</span><span class="sxs-lookup"><span data-stu-id="9bb36-113">Deploy the BAM definition file for the Service Oriented Solution</span></span>](#step19)  
  
-   [<span data-ttu-id="9bb36-114">部署服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9bb36-114">Deploy the Service Oriented Solution</span></span>](#step21)  
  
-   [<span data-ttu-id="9bb36-115">設定大型主機無法使用時的虛設常式擱置交易 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9bb36-115">Configure the stub Pending Transactions Web Services when a mainframe is not available</span></span>](#step23)  
  
-   [<span data-ttu-id="9bb36-116">啟動服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9bb36-116">Start the Service Oriented Solution</span></span>](#step25)  
  
> [!NOTE]
>  <span data-ttu-id="9bb36-117">服務導向的解決方案位於資料夾\< *BizTalk Server 安裝資料夾*> \SDK\Scenarios\SO。</span><span class="sxs-lookup"><span data-stu-id="9bb36-117">The service oriented solution is located in the folder \<*BizTalk Server Installation Folder*>\SDK\Scenarios\SO.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bb36-118">若您的解決方案沒有大型主機，可以修改連接埠繫結以使用虛設常式 Web 服務來進行擱置交易。</span><span class="sxs-lookup"><span data-stu-id="9bb36-118">If you don’t have a mainframe for the solution, you can modify the port binding to use the stub Web service for Pending Transactions.</span></span> <span data-ttu-id="9bb36-119">Web 服務會在本機產生交易，以模擬大型主機交易。</span><span class="sxs-lookup"><span data-stu-id="9bb36-119">The Web service generates transactions locally to emulate the mainframe transactions.</span></span>  
  
##  <span data-ttu-id="9bb36-120"><a name="step1"></a>準備安裝服務導向解決方案配接器與內嵌版本的電腦</span><span class="sxs-lookup"><span data-stu-id="9bb36-120"><a name="step1"></a> Prepare the computer for installing the adapter and inline versions of the Service Oriented Solution</span></span>  
  
#### <a name="to-prepare-the-computer-for-installing-the-adapter-and-inline-versions-of-the-service-oriented-solution"></a><span data-ttu-id="9bb36-121">準備安裝服務導向解決方案配接器與內嵌版本的電腦</span><span class="sxs-lookup"><span data-stu-id="9bb36-121">To prepare the computer for installing the adapter and inline versions of the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="9bb36-122">如果您安裝 Windows SharePoint Services 時，排除 （根） 在預設的網站的 Windows SharePoint Services 受管理的路徑，如下所示： 按一下**啟動**，指向 **所有程式**，指向  **系統管理工具**，然後按一下  **SharePoint 管理中心內**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-122">If you installed Windows SharePoint Services, exclude the (root) of the Default Web Site from Windows SharePoint Services Managed Paths as follows: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
    1.  <span data-ttu-id="9bb36-123">在下**虛擬伺服器設定**，選取**設定虛擬伺服器設定**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-123">Under **Virtual Server Configuration**, select **Configure virtual server settings**.</span></span>  
  
    2.  <span data-ttu-id="9bb36-124">在**虛擬伺服器清單**頁面上，按一下**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-124">On the **Virtual Server List** page, click **Default Web Site**.</span></span>  
  
    3.  <span data-ttu-id="9bb36-125">在**虛擬伺服器設定**頁面上，按一下**定義管理的路徑**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-125">On the **Virtual Server Settings** page, click **Define managed paths**.</span></span>  
  
    4.  <span data-ttu-id="9bb36-126">在**包含路徑**區段**定義受管理的路徑**頁面上，選取**根**，然後按一下 **移除選取的路徑**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-126">In the **Included Paths** section of the **Defined Managed Path** page, select **Root** and then click **Remove selected paths**.</span></span>  
  
    5.  <span data-ttu-id="9bb36-127">在命令提示字元，執行 IISReset。</span><span class="sxs-lookup"><span data-stu-id="9bb36-127">At a command prompt, perform an IISReset.</span></span>  
  
2.  <span data-ttu-id="9bb36-128">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，按一下 **電腦管理**主控台，然後再加入本機系統管理員群組的 BizTalk 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="9bb36-128">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Computer Management** console, and then add the BizTalk service account to the local Administrators group.</span></span>  
  
3.  <span data-ttu-id="9bb36-129">登出電腦，然後以 BizTalk 服務帳戶的身分登入電腦。</span><span class="sxs-lookup"><span data-stu-id="9bb36-129">Log off the computer, and then log on to the computer as the BizTalk service account.</span></span>  
  
4.  <span data-ttu-id="9bb36-130">在命令提示字元，輸入下列命令，然後按 ENTER 以設定 %BTSSolutionsPath% 環境變數。</span><span class="sxs-lookup"><span data-stu-id="9bb36-130">At a command prompt, type the following command, and then press ENTER to set the %BTSSolutionsPath% environment variable.</span></span> <span data-ttu-id="9bb36-131">然後結束命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9bb36-131">Then, exit the command prompt.</span></span>  
  
    -   <span data-ttu-id="9bb36-132">setx BTSSolutionsPath [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"</span><span class="sxs-lookup"><span data-stu-id="9bb36-132">setx BTSSolutionsPath [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="9bb36-133">若您使用 64 位元的電腦，請使用 %ProgramFiles(x86)% 取代 %ProgramFiles%。</span><span class="sxs-lookup"><span data-stu-id="9bb36-133">If you are using a 64-bit computer, use %ProgramFiles(x86)% instead of %ProgramFiles%.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="9bb36-134">如需有關 SETX 命令的詳細資訊，請參閱 Microsoft TechNet 網站，網址[http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-134">For more information about the SETX command, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span></span>  
  
##  <span data-ttu-id="9bb36-135"><a name="step3"></a>移除服務導向解決方案的虛設常式版本</span><span class="sxs-lookup"><span data-stu-id="9bb36-135"><a name="step3"></a> Remove the stub version of the Service Oriented Solution</span></span>  
  
#### <a name="to-remove-the-stub-version-of-the-service-oriented-solution"></a><span data-ttu-id="9bb36-136">移除服務導向解決方案的虛設常式版本</span><span class="sxs-lookup"><span data-stu-id="9bb36-136">To remove the stub version of the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="9bb36-137">開啟**BizTalk Server 管理主控台**，如下所示： 按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-137">Open the **BizTalk Server Administration Console** as follows: Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="9bb36-138">在**BizTalk Server 管理主控台**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**的應用程式**，以滑鼠右鍵按一下**BTSScn.SO.CustomerService**，然後按一下 **停止**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-138">In the **BizTalk Server Administration Console**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, right-click **BTSScn.SO.CustomerService**, and then click **Stop**.</span></span> <span data-ttu-id="9bb36-139">在**停止應用程式**對話方塊中，選取**完全停止-終止執行個體**，然後按一下 **停止**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-139">In the **Stop Application** dialog box, select **Full Stop - Terminate Instances**, and then click **Stop**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-140">您不需要為了安裝內嵌和配接器版本而移除虛設常式版本。</span><span class="sxs-lookup"><span data-stu-id="9bb36-140">You don't need to remove the stub version for installing the inline and adapter versions.</span></span> <span data-ttu-id="9bb36-141">若您要將所有版本放在一起，應該略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="9bb36-141">If you want to put all the versions together, you should skip this step.</span></span>  
  
3.  <span data-ttu-id="9bb36-142">開啟命令提示字元，輸入下列命令，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="9bb36-142">Open a command prompt, type the following command, and then press ENTER.</span></span> <span data-ttu-id="9bb36-143">此命令會將預設指令碼主控件變更為 CScript.exe：</span><span class="sxs-lookup"><span data-stu-id="9bb36-143">This command changes the default script host to CScript.exe:</span></span>  
  
    -   `cscript /H:CScript`  
  
4.  <span data-ttu-id="9bb36-144">在命令提示字元，將目前的目錄變更為 %BTSSolutonsPath%\SO\BTSSoln\Scripts 資料夾，輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="9bb36-144">At the command prompt, change the current directory to %BTSSolutonsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER:</span></span>  
  
    -   `UnEnlistStub.vbs`  
  
5.  <span data-ttu-id="9bb36-145">在命令提示字元，輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="9bb36-145">At the command prompt, type the following command, and then press ENTER:</span></span>  
  
    -   `UndeployStub.vbs`  
  
6.  <span data-ttu-id="9bb36-146">在命令提示字元執行下列命令</span><span class="sxs-lookup"><span data-stu-id="9bb36-146">At the command prompt, run the following command</span></span>  
  
     <span data-ttu-id="9bb36-147">設定路徑 = %PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤 」</span><span class="sxs-lookup"><span data-stu-id="9bb36-147">SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"</span></span>  
  
     <span data-ttu-id="9bb36-148">如此可設定尋找 BAM 公用程式的路徑。</span><span class="sxs-lookup"><span data-stu-id="9bb36-148">This sets the path to find the BAM utilities.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-149">如果您使用 64 位元電腦，輸入`%ProgramFiles(x86)%`而不是`%ProgramFiles%`。</span><span class="sxs-lookup"><span data-stu-id="9bb36-149">If you are using a 64-bit computer, type `%ProgramFiles(x86)%` instead of `%ProgramFiles%`.</span></span>  
  
7.  <span data-ttu-id="9bb36-150">在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\BAM，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="9bb36-150">At the command prompt, change the directory to %BTSSolutionsPath%\SO\BTSSoln\BAM, and then run the following command:</span></span>  
  
    -   `bm remove-all -DefinitionFile:ServiceLevelTracking.xml`  
  
8.  <span data-ttu-id="9bb36-151">在命令提示字元中，將目錄變更\<*企業單一登入 」 安裝目錄*>，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="9bb36-151">At the command prompt, change the directory to \<*Enterprise Single Sign-On Install Directory*>, and then run the following command:</span></span>  
  
    -   `ssomanage -tickets no no`  
  
9. <span data-ttu-id="9bb36-152">在命令提示字元，執行下列命令以刪除 WoodgroveBank.CustomerService SSO 附屬應用程式：</span><span class="sxs-lookup"><span data-stu-id="9bb36-152">At the command prompt, run the following command to delete the WoodgroveBank.CustomerService SSO Affiliated application:</span></span>  
  
    -   `ssomanage -deleteapp WoodgroveBank.CustomerService`  
  
10. <span data-ttu-id="9bb36-153">在命令提示字元，執行下列命令以刪除虛設常式版本所使用的網站。</span><span class="sxs-lookup"><span data-stu-id="9bb36-153">At the command prompt, run the following commands to delete the Web sites used by the stub version.</span></span> <span data-ttu-id="9bb36-154">如需有關 iisvdir.vbs 的詳細資訊，請參閱 Microsoft TechNet 網站，網址[http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-154">For more information about iisvdir.vbs, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).</span></span>  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker`  
  
11. <span data-ttu-id="9bb36-155">啟動 網際網路資訊服務 (IIS) 管理員，如下所示： 按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下  **Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-155">Start Internet Information Services (IIS) Manager as follows: Click **Start**, point to **All Programs**, point to **Administration Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
    -   <span data-ttu-id="9bb36-156">展開**應用程式集區**，以滑鼠右鍵按一下您先前的 Web 應用程式的建立應用程式集區，按一下**刪除**，然後按一下 **確定**確認中對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9bb36-156">Expand the **Application Pools**, right-click the application pool you crated for the previous Web applications, click **Delete**, and then click **OK** in the confirmation dialog box.</span></span>  
  
12. <span data-ttu-id="9bb36-157">按一下**啟動**，指向 **控制台**，按一下 **新增或移除程式**，然後再解除安裝 IBM WebSphere MQ Client for Windows。</span><span class="sxs-lookup"><span data-stu-id="9bb36-157">Click **Start**, point to **Control Panel**, click **Add or Remove Programs**, and then uninstall the IBM WebSphere MQ Client for Windows.</span></span>  
  
13. <span data-ttu-id="9bb36-158">啟動**Visual Studio 命令提示字元**，然後執行下列命令以刪除您為虛設常式版本安裝的 amqmdnet.dll。</span><span class="sxs-lookup"><span data-stu-id="9bb36-158">Start **Visual Studio Command Prompt** and then run the following command to delete the amqmdnet.dll you installed for the stub version.</span></span>  
  
    -   `gacutil /u amqmdnet`  
  
##  <span data-ttu-id="9bb36-159"><a name="step5"></a>準備後端系統，服務導向解決方案存取</span><span class="sxs-lookup"><span data-stu-id="9bb36-159"><a name="step5"></a> Prepare the back-end systems for the Service Oriented Solution to access</span></span>  
  
#### <a name="to-install-the-required-applications-for-the-back-end-systems-for-the-service-oriented-solution-to-access"></a><span data-ttu-id="9bb36-160">安裝後端系統所需的應用程式以供服務導向解決方案存取</span><span class="sxs-lookup"><span data-stu-id="9bb36-160">To install the required applications for the back-end systems for the Service Oriented Solution to access</span></span>  
  
1.  <span data-ttu-id="9bb36-161">在本機電腦上安裝 IBM WebSphere MQ for Windows Version 5.3 Server。</span><span class="sxs-lookup"><span data-stu-id="9bb36-161">Install IBM WebSphere MQ for Windows Version 5.3 Server on the local computer.</span></span>  
  
    1.  <span data-ttu-id="9bb36-162">請保留所有預設設定。</span><span class="sxs-lookup"><span data-stu-id="9bb36-162">Keep all the default settings.</span></span> <span data-ttu-id="9bb36-163">設定**預設組態**結尾**準備 WebSphere MQ 精靈**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-163">Set up the **Default Configuration** at the end of the **Prepare WebSphere MQ Wizard**.</span></span> <span data-ttu-id="9bb36-164">佇列管理員則命名為 Qm_<\<*您的電腦名稱*>。</span><span class="sxs-lookup"><span data-stu-id="9bb36-164">The queue manager is named as QM_\<*your computer name*>.</span></span>  
  
    2.  <span data-ttu-id="9bb36-165">安裝 Fix Pack 10 (CSD10)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-165">Install the Fix Pack 10 (CSD10).</span></span> <span data-ttu-id="9bb36-166">請保留所有預設設定。</span><span class="sxs-lookup"><span data-stu-id="9bb36-166">Keep all the default settings.</span></span>  
  
2.  <span data-ttu-id="9bb36-167">安裝 MQSeries 代理程式。</span><span class="sxs-lookup"><span data-stu-id="9bb36-167">Install the MQSeries Agent.</span></span>  
  
    1.  <span data-ttu-id="9bb36-168">請重新執行[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="9bb36-168">Rerun the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] setup program.</span></span>  
  
    2.  <span data-ttu-id="9bb36-169">在**程式維護**頁面上，選取**修改**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-169">On the **Program Maintenance** page, select **Modify**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="9bb36-170">在**元件安裝**頁面上，展開**其他軟體**節點，然後再選取**MQSeries 代理程式**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-170">On the **Component Installation** page, expand the **Additional Software** node, and then select **MQSeries Agent**.</span></span>  
  
    4.  <span data-ttu-id="9bb36-171">在**完成**頁面上，請確定**啟動 BizTalk MQSeries 代理程式組態精靈**未選取。</span><span class="sxs-lookup"><span data-stu-id="9bb36-171">On the **Completion** page, make sure that **Launch BizTalk MQSeries Agent Configuration Wizard** is not selected.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-172">**MQSeries 代理程式**是 IBM WebSphere MQ 之後才會啟動的核取方塊為已安裝 Windows。</span><span class="sxs-lookup"><span data-stu-id="9bb36-172">The **MQSeries Agent** check box is activated only after the IBM WebSphere MQ for Windows is installed.</span></span>  
  
3.  <span data-ttu-id="9bb36-173">開啟**Visual Studio 命令提示字元**，將目錄變更\< *IBM MQSeries 安裝目錄*> \bin 資料夾，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="9bb36-173">Open a **Visual Studio Command Prompt**, change the directory to the \<*IBM MQSeries Installation Directory*>\bin folder, and then run the following command:</span></span>  
  
    -   `gacutil /i amqmdnet.dll`  
  
4.  <span data-ttu-id="9bb36-174">若您要安裝 Microsoft Host Integration Server 2004 以存取大型主機，請安裝 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9bb36-174">Install Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] if you want to install Microsoft Host Integration Server 2004 to access the mainframe.</span></span> <span data-ttu-id="9bb36-175">在安裝程式，在**選項**頁面上，選取**Visual C#.NET**，然後清除其他元件核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9bb36-175">In the setup program, on the **Options** page, select **Visual C# .NET**, and then clear other components checkboxes.</span></span> <span data-ttu-id="9bb36-176">您不需要安裝其他元件比**Visual C#.NET**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-176">You don't need to install other components than the **Visual C# .NET**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-177">Host Integration Server 2004 中的 TI 設計師需要 [!INCLUDE[btsVStudioNet2003](../includes/btsvstudionet2003-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9bb36-177">The TI Designer in Host Integration Server 2004 requires [!INCLUDE[btsVStudioNet2003](../includes/btsvstudionet2003-md.md)].</span></span>  
  
5.  <span data-ttu-id="9bb36-178">安裝和設定 Microsoft Host Integration Server 2004，如果您有存取大型主機。</span><span class="sxs-lookup"><span data-stu-id="9bb36-178">Install and configure Microsoft Host Integration Server 2004 if you have a mainframe to be accessed.</span></span> <span data-ttu-id="9bb36-179">請保留所有預設設定。</span><span class="sxs-lookup"><span data-stu-id="9bb36-179">Keep all the default settings.</span></span>  
  
#### <a name="to-create-the-mqseries-queues"></a><span data-ttu-id="9bb36-180">建立 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="9bb36-180">To create the MQSeries queues</span></span>  
  
1.  <span data-ttu-id="9bb36-181">開啟 WebSphere MQ Explorer，依序展開**佇列管理員**，然後展開您要建立佇列的佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="9bb36-181">Open the WebSphere MQ Explorer, expand **Queue Managers**, and then expand the queue manager in which you want to create the queues.</span></span> <span data-ttu-id="9bb36-182">一般而言，佇列管理員則命名為 Qm_<\<*您的電腦名稱*>。</span><span class="sxs-lookup"><span data-stu-id="9bb36-182">Typically, a queue manager is named as QM_\<*your computer name*>.</span></span>  
  
2.  <span data-ttu-id="9bb36-183">在 WebSphere MQ explorer 中，以滑鼠右鍵按一下**佇列**，指向 **新增**，按一下 **本機佇列**，然後建立下列本機佇列的配接器版本解決方案：</span><span class="sxs-lookup"><span data-stu-id="9bb36-183">In the WebSphere MQ Explorer, right-click **Queues**, point to **New**, click **Local Queue**, and then create the following local queues for the adapter version of the solution:</span></span>  
  
    -   <span data-ttu-id="9bb36-184">AdapterSOAInputQueue</span><span class="sxs-lookup"><span data-stu-id="9bb36-184">AdapterSOAInputQueue</span></span>  
  
    -   <span data-ttu-id="9bb36-185">AdapterSOAOutputQueue</span><span class="sxs-lookup"><span data-stu-id="9bb36-185">AdapterSOAOutputQueue</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-186">佇列可共用 MQSeries 叢集，不過，這並非必要的。</span><span class="sxs-lookup"><span data-stu-id="9bb36-186">The queues can share an MQSeries cluster, but they are not required to do so.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-187">MQSeries 佇列管理員名稱和佇列名稱有區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="9bb36-187">MQSeries queue manager names and queue names are case sensitive.</span></span>  
  
3.  <span data-ttu-id="9bb36-188">重複上一個步驟為內嵌版本建立下列本機佇列：</span><span class="sxs-lookup"><span data-stu-id="9bb36-188">Repeat the previous step to create the following local queues for the inline version:</span></span>  
  
    -   <span data-ttu-id="9bb36-189">InlineSOAOutputQueue</span><span class="sxs-lookup"><span data-stu-id="9bb36-189">InlineSOAOutputQueue</span></span>  
  
    -   <span data-ttu-id="9bb36-190">InlineSOAInputQueue</span><span class="sxs-lookup"><span data-stu-id="9bb36-190">InlineSOAInputQueue</span></span>  
  
4.  <span data-ttu-id="9bb36-191">重複上一個步驟為付款追蹤器模擬器建立下列本機佇列。</span><span class="sxs-lookup"><span data-stu-id="9bb36-191">Repeat the previous step to create the following local queues for the Payment Tracker simulator.</span></span> <span data-ttu-id="9bb36-192">(付款追蹤器模擬器同時用於配接器和內嵌版本)：</span><span class="sxs-lookup"><span data-stu-id="9bb36-192">(The Payment Tracker simulator is used in both the adapter and inline versions):</span></span>  
  
    -   <span data-ttu-id="9bb36-193">LastPaymentsInputQueue</span><span class="sxs-lookup"><span data-stu-id="9bb36-193">LastPaymentsInputQueue</span></span>  
  
    -   <span data-ttu-id="9bb36-194">LastPaymentsOutputQueue</span><span class="sxs-lookup"><span data-stu-id="9bb36-194">LastPaymentsOutputQueue</span></span>  
  
#### <a name="to-complete-configuration-of-the-mqseries-adapter"></a><span data-ttu-id="9bb36-195">完成 MQSeries 配接器組態</span><span class="sxs-lookup"><span data-stu-id="9bb36-195">To complete configuration of the MQSeries adapter</span></span>  
  
1.  <span data-ttu-id="9bb36-196">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk MQSeries 代理程式組態精靈**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-196">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk MQSeries Agent Configuration Wizard**.</span></span>  
  
2.  <span data-ttu-id="9bb36-197">在**歡迎**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-197">On the **Welcome** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="9bb36-198">在**應用程式識別**頁面上，選取**本使用者**，然後輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-198">On the **Application Identity** page, select **This User**, and then enter the user name and password.</span></span> <span data-ttu-id="9bb36-199">MQSeries 代理程式的 COM+ 應用程式會在此使用者帳戶之下執行。</span><span class="sxs-lookup"><span data-stu-id="9bb36-199">The COM+ application for the MQSeries Agent will run under this user account.</span></span> <span data-ttu-id="9bb36-200">對於此逐步解說，請使用與 BizTalk 服務所使用的相同使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9bb36-200">For this walkthrough, use the same user account that the BizTalk service is using.</span></span> <span data-ttu-id="9bb36-201">如果不是，使用者帳戶以裝載 MQSeries 配接器的 BizTalk 服務必須可加入至**CreatorOwner** COM + 應用程式角色。</span><span class="sxs-lookup"><span data-stu-id="9bb36-201">If it is not, the user accounts for BizTalk services hosting the MQSeries Adapter must be added to the **CreatorOwner** role of the COM+ application.</span></span>  
  
4.  <span data-ttu-id="9bb36-202">按一下**是**上**MQSConfigWiz**對話方塊中，如果系統提示您在上一個步驟中輸入的使用者帳戶具有系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="9bb36-202">Click **Yes** on the **MQSConfigWiz** dialog box, if prompted that the user account that you entered in the previous step has the administrative privilege.</span></span>  
  
5.  <span data-ttu-id="9bb36-203">在**角色名稱**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-203">On the **Name of Role** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="9bb36-204">在**建立 MQSAgent COM + 應用程式**頁面上，按一下**下一步**，然後按一下 **完成**上**完成**頁面。</span><span class="sxs-lookup"><span data-stu-id="9bb36-204">On the **Creating the MQSAgent COM+ Application** page, click **Next**, and then click **Finish** on the **Completion** page.</span></span>  
  
#### <a name="to-configure-the-mainframe-cics-application"></a><span data-ttu-id="9bb36-205">設定大型主機 CICS 應用程式</span><span class="sxs-lookup"><span data-stu-id="9bb36-205">To configure the mainframe CICS application</span></span>  
  
1.  <span data-ttu-id="9bb36-206">使用「記事本」開啟 %BTSSolutionsPath%\SO\MFAccess\HISTIComponent 資料夾中的 bizcbl.txt 及其 "Copy Book" (MainFrameProgramVTCS2Description.txt)，然後檢視內容。</span><span class="sxs-lookup"><span data-stu-id="9bb36-206">Using Notepad, open the bizcbl.txt and its "copy book" (MainFrameProgramVTCS2Description.txt) in the %BTSSolutionsPath%\SO\MFAccess\HISTIComponent folder, and then review the contents.</span></span>  
  
    -   <span data-ttu-id="9bb36-207">Bizcbl.txt 包括從輸入的帳戶號碼傳回隨機帳戶陳述式的 COBOL 程序。</span><span class="sxs-lookup"><span data-stu-id="9bb36-207">Bizcbl.txt includes the COBOL procedure returning the randomized account statements from account number input.</span></span>  
  
    -   <span data-ttu-id="9bb36-208">MainFrameProgramVTCS2Descriptoin.txt 包含說明輸入和輸出資料資訊的 COMMAREA。</span><span class="sxs-lookup"><span data-stu-id="9bb36-208">MainFrameProgramVTCS2Descriptoin.txt contains COMMAREA which describes the input and output data information.</span></span> <span data-ttu-id="9bb36-209">COMMAREA 是連續記憶體區塊，用來在被呼叫與呼叫的程式之間來回傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="9bb36-209">COMMAREA is a block of contiguous memory used to pass data back and forth between called and calling programs.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-210">您也可以使用 Copy Book，利用 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 搭配 TI 設計師外掛程式，來產生交易整合器 (TI) 中繼資料檔。</span><span class="sxs-lookup"><span data-stu-id="9bb36-210">You can also use the copy book to generate the Transaction Integrator (TI) metadata file using [!INCLUDE[vs2010](../includes/vs2010-md.md)] with the TI Designer plug-in.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-211">雖然下列步驟是成功部署的重要步驟，不過，通常不是由 BizTalk Server 開發人員執行。</span><span class="sxs-lookup"><span data-stu-id="9bb36-211">Although the following steps are crucial to the successful deployment, they are not usually performed by the BizTalk Server developer.</span></span> <span data-ttu-id="9bb36-212">您必須依賴大型主機人員以適當地設定主機環境。</span><span class="sxs-lookup"><span data-stu-id="9bb36-212">You must rely on the mainframe personnel to properly configure the mainframe environment.</span></span> <span data-ttu-id="9bb36-213">此逐步說明所需的軟體通常安裝在大多數的大型主機環境中。</span><span class="sxs-lookup"><span data-stu-id="9bb36-213">The software required for this walkthrough is usually installed in the most mainframe environments.</span></span> <span data-ttu-id="9bb36-214">如需最小大型主機作業系統環境的詳細資訊，請參閱 Host Integration Server 文件。</span><span class="sxs-lookup"><span data-stu-id="9bb36-214">For more information about the minimum mainframe operating system environment, see the Host Integration Server documentation.</span></span>  
  
2.  <span data-ttu-id="9bb36-215">以 FTP 之類的方法將 COBOL 程式碼複製到主控件。</span><span class="sxs-lookup"><span data-stu-id="9bb36-215">Copy the COBOL code to the host by method like FTP.</span></span>  
  
3.  <span data-ttu-id="9bb36-216">編譯 COBOL 程式碼和 Copy Book。</span><span class="sxs-lookup"><span data-stu-id="9bb36-216">Compile the COBOL code and copy book.</span></span> <span data-ttu-id="9bb36-217">下列程式碼顯示 COBOL 編譯器的工作控制語言 (Job Control Language，JCL) 範例。</span><span class="sxs-lookup"><span data-stu-id="9bb36-217">The following code shows a sample of Job Control Language (JCL) for the COBOL compiler.</span></span>  
  
    ```  
    //COB      EXEC PGM=IGYCRCTL,  
    //            PARM=&COBPARM,  
    //            REGION=&REG  
    //STEPLIB  DD DSN=&COMPINDX..SIGYCOMP,DISP=SHR  
    //SYSLIB   DD DSN=&INDEX..SDFHCOB,DISP=SHR  
    //         DD DSN=&INDEX..SDFHMAC,DISP=SHR  
    //         DD DSN=&HLQ..&COMP..COBCOPY,DISP=SHR  
    //SYSPRINT DD SYSOUT=&OUTC  
    //*SYSPRINT DD DSN=&&INPUT,DISP=(,PASS),UNIT=SYSDA,  
    //*         SPACE=(TRK,(100,50)),  
    //*         DCB=(DSORG=PS,LRECL=121,BLKSIZE=2420,RECFM=FBA)  
    //SYSIN    DD DSN=&&SYSCIN,DISP=(OLD,DELETE)  
    //SYSLIN   DD DSN=&&LOADSET,  
    //            DISP=(MOD,PASS),  
    //            UNIT=&WORK,  
    //            SPACE=(80,(250,100))  
    //SYSUT1   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT2   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT3   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT4   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT5   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT6   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT7   DD UNIT=&WORK,SPACE=(460,(350,150))  
    ```  
  
4.  <span data-ttu-id="9bb36-218">連結編輯已編譯的來源以建立可執行檔。</span><span class="sxs-lookup"><span data-stu-id="9bb36-218">Link edit the compiled source to create the executable.</span></span> <span data-ttu-id="9bb36-219">下列程式碼顯示 COBOL 連結編輯的 JCL 範例。</span><span class="sxs-lookup"><span data-stu-id="9bb36-219">The following code shows a sample of JCL for COBOL link edit.</span></span>  
  
    ```  
    //LKED     EXEC PGM=IEWL,REGION=&REG,  
    //            PARM=&LNKPARM,COND=(5,LT,COB)  
    //SYSLIB   DD DSN=&INDEX..SDFHLOAD,DISP=SHR  
    //         DD DSN=CEE.SCEELKED,DISP=SHR  
    //         DD DSN=&TCPINDX..SEZATCP,DISP=SHR  
    //SYSLMOD  DD DSN=&LMINDX..&COMP..LOADLIB,DISP=SHR  
    //SYSUT1   DD UNIT=&WORK,  
    //            DCB=BLKSIZE=1024,  
    //            SPACE=(1024,(200,20))  
    //SYSPRINT DD SYSOUT=&OUTC  
    //SYSLIN   DD DSN=&&LOADSET,DISP=(OLD,DELETE)  
    //         DD DSN=&&COPYLINK,DISP=(OLD,DELETE)  
    ```  
  
5.  <span data-ttu-id="9bb36-220">設定 CICS 大型主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bb36-220">Configure the CICS mainframe application.</span></span>  
  
    -   <span data-ttu-id="9bb36-221">在此步驟中，大型主機系統程式設計師或 CICS 開發人員必須安裝 TCPIPSERVICE、工作階段、連線、交易和程式等資源定義。</span><span class="sxs-lookup"><span data-stu-id="9bb36-221">In this step, the mainframe systems programmer or CICS developer must install TCPIPSERVICE, Session, Connection, Transaction, and Program resource definitions.</span></span>  
  
    -   <span data-ttu-id="9bb36-222">請諮詢大型主機系統管理員以取得 IP 位址、連接埠編號和您可存取的程式連結名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb36-222">You should consult with mainframe administrators to get an IP address, port number, and a Link to Program name that you can access.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="9bb36-223">此逐步解說假設大型主機使用 CICS 應用程式伺服器，而交易的程式設計模型為 TCP/IP (增強的接聽程式模式 (Enhanced Listener Mode，ELM) 連結)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-223">This walkthrough assumes that the mainframe uses a CICS application server and that the programming model for the transaction is TCP/IP (Enhanced Listener Mode (ELM) Link).</span></span>  
  
##  <span data-ttu-id="9bb36-224"><a name="step7"></a>設定 Web 伺服器針對安全通訊端層 (SSL)</span><span class="sxs-lookup"><span data-stu-id="9bb36-224"><a name="step7"></a> Configure the Web server for Secure Socket Layers (SSL)</span></span>  
  
#### <a name="to-install-certificate-services"></a><span data-ttu-id="9bb36-225">安裝憑證服務</span><span class="sxs-lookup"><span data-stu-id="9bb36-225">To install Certificate Services</span></span>  
  
1.  <span data-ttu-id="9bb36-226">按一下**啟動**，指向 **控制台**，然後按一下 **新增或移除程式**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-226">Click **Start**, point to **Control Panel**, and then click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="9bb36-227">在**新增或移除程式**對話方塊中，按一下 **新增/移除 Windows 元件**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-227">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3.  <span data-ttu-id="9bb36-228">在**Windows 元件精靈**，選取**憑證服務**，按一下**下一步**，然後依照螢幕上指示完成安裝。</span><span class="sxs-lookup"><span data-stu-id="9bb36-228">In the **Windows Components Wizard**, select the **Certificate Services**, click **Next**, and then follow the on-screen instructions to complete the installation.</span></span>  
  
#### <a name="to-create-a-certificate-request"></a><span data-ttu-id="9bb36-229">建立憑證要求</span><span class="sxs-lookup"><span data-stu-id="9bb36-229">To create a certificate request</span></span>  
  
1.  <span data-ttu-id="9bb36-230">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，按一下 **屬性**按一下 **目錄安全性**索引標籤，然後再按一下**伺服器憑證**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-230">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, click **Properties**, click the **Directory Security** tab, and then click **Server Certificate**.</span></span>  
  
2.  <span data-ttu-id="9bb36-231">在**歡迎**頁面**Web 伺服器憑證精靈**，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-231">On the **Welcome** page of the **Web Server Certificate Wizard**, click **Next**.</span></span>  
  
3.  <span data-ttu-id="9bb36-232">在**服務憑證**頁面上，選取**建立新的憑證**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-232">On the **Service Certificate** page, select **Create a new certificate**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="9bb36-233">在**延遲或立即要求**頁面上，按一下**準備要求，但於稍後傳送**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-233">On the **Delayed or Immediate Request** page, click **Prepare the request now, but send it later**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="9bb36-234">在**名稱和安全性設定**頁面上，保留所有預設設定，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-234">On the **Name and Security Settings** page, keep all the default settings, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="9bb36-235">在**組織資訊**頁面上，輸入您的公司組織和組織單位名稱，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-235">On the **Organization Information** page, type your company's organization and organizational unit names, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="9bb36-236">在**您站台的一般名稱**頁面上，輸入您的電腦名稱中**一般名稱**方塊，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-236">On the **Your Site's Common Name** page, type your computer name in the **Common name** box, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="9bb36-237">在**地理資訊**頁面上，填寫您的地理資訊，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-237">On the **Geographical Information** page, fill out your geographical information, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="9bb36-238">在**憑證要求檔案名稱**頁面上，輸入`c:\certreq.txt`中**檔案名稱**方塊，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-238">On the **Certificate Request File Name** page, type `c:\certreq.txt` in the **File name** box, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="9bb36-239">在**要求檔案摘要**頁面上，按一下**下一步**，然後按一下 **完成**上**完成**頁面。</span><span class="sxs-lookup"><span data-stu-id="9bb36-239">On the **Request File Summary** page, click **Next**, and then click **Finish** on the **Completion** page.</span></span>  
  
#### <a name="to-submit-the-certificate-request-to-the-certification-authority"></a><span data-ttu-id="9bb36-240">提交憑證要求給憑證授權單位</span><span class="sxs-lookup"><span data-stu-id="9bb36-240">To submit the certificate request to the Certification Authority</span></span>  
  
1.  <span data-ttu-id="9bb36-241">在 Internet Explorer，在位址方塊中，輸入`http://localhost/certsrvt`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="9bb36-241">In Internet Explorer, in the Address box, type `http://localhost/certsrvt`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="9bb36-242">在**歡迎**頁面上，按一下**要求憑證**，然後按一下 **進階的憑證要求**上**要求憑證**頁面。</span><span class="sxs-lookup"><span data-stu-id="9bb36-242">On the **Welcome** page, click **Request a Certificate**, and then click **Advanced certificate request** on the **Request a Certificate** page.</span></span>  
  
3.  <span data-ttu-id="9bb36-243">在**進階憑證要求**頁面上，按一下**提交憑證要求，使用 base64 編碼 PKCS #10 檔案或更新要求使用 base64 編碼 PKCS #7 檔案**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-243">On the **Advanced Certificate Request** page, click **Submit a certificate request using a base64 encoded PKCS #10 file or a renewal request using a base64 encoded PKCS #7 file**.</span></span>  
  
4.  <span data-ttu-id="9bb36-244">從您在 < 若要建立憑證要求 」，將它貼到程序中建立的 c:\certreq.txt 複製的所有文字**已儲存的要求**方塊**提交憑證要求或更新要求**頁面，然後再按一下**送出**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-244">Copy all the text from the c:\certreq.txt that you created in the procedure "To create a certificate request", paste it to the **Saved Request** box on the **Submit a Certificate Request or Renewal Request** page, and then click **Submit**.</span></span>  
  
#### <a name="to-issue-a-certificate-using-certification-authority-management-tool"></a><span data-ttu-id="9bb36-245">使用憑證授權單位管理工具發出憑證</span><span class="sxs-lookup"><span data-stu-id="9bb36-245">To issue a certificate using Certification Authority management tool</span></span>  
  
1.  <span data-ttu-id="9bb36-246">按一下**啟動**，指向 **系統管理工具**，然後按一下 **憑證授權單位**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-246">Click **Start**, point to **Administrative Tools**, and then click **Certification Authority**.</span></span>  
  
2.  <span data-ttu-id="9bb36-247">在**憑證授權單位**主控台中，展開憑證授權單位的名稱，展開**暫止要求**，以滑鼠右鍵按一下您在上一個步驟中，點提交憑證要求若要**所有工作**，然後按一下 **問題**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-247">In the **Certification Authority** console, expand your certification authority's name, expand the **Pending Request**, right-click the certificate request that you submitted in the previous step, point to **All Tasks**, and then click **Issue**.</span></span>  
  
3.  <span data-ttu-id="9bb36-248">關閉**憑證授權單位**主控台。</span><span class="sxs-lookup"><span data-stu-id="9bb36-248">Close the **Certification Authority** console.</span></span>  
  
#### <a name="to-download-the-certificate-to-the-web-server"></a><span data-ttu-id="9bb36-249">將憑證下載至 Web 伺服器</span><span class="sxs-lookup"><span data-stu-id="9bb36-249">To download the certificate to the Web server</span></span>  
  
1.  <span data-ttu-id="9bb36-250">在 Internet Explorer，在位址方塊中，輸入`http://localhost/certsrvt`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="9bb36-250">In Internet Explorer, in the Address box, type `http://localhost/certsrvt`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="9bb36-251">在**歡迎**頁面上，按一下**檢視擱置的憑證要求狀態**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-251">On the **Welcome** page, click **View the status of a pending certificate request**.</span></span>  
  
3.  <span data-ttu-id="9bb36-252">在**檢視擱置的憑證要求狀態**頁面上，按一下憑證**要求**您在 「 建立憑證要求 」 程序中建立。</span><span class="sxs-lookup"><span data-stu-id="9bb36-252">On the **View the Status of a Pending Certificate Request** page, click the certificate **request** that you created in the procedure "To create a certificate request".</span></span>  
  
4.  <span data-ttu-id="9bb36-253">在**憑證核發**頁面上，選取其中一個編碼配置，然後按**下載憑證**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-253">On the **Certificate Issued** page, select either of the encoding schemes, and then click **Download certificate**.</span></span>  
  
5.  <span data-ttu-id="9bb36-254">在**安全性警告**對話方塊中，按一下 **儲存**，然後將憑證儲存為 c:\certnew.cer。</span><span class="sxs-lookup"><span data-stu-id="9bb36-254">On the **Security Warning** dialog box, click **Save**, and then save the certificate as c:\certnew.cer.</span></span>  
  
#### <a name="to-install-the-certificate-to-the-web-server"></a><span data-ttu-id="9bb36-255">將憑證安裝至 Web 伺服器</span><span class="sxs-lookup"><span data-stu-id="9bb36-255">To install the certificate to the Web server</span></span>  
  
1.  <span data-ttu-id="9bb36-256">在**網際網路資訊服務 (IIS) 管理員**，展開**網站**，以滑鼠右鍵按一下**Default Web Site**為您建立憑證要求，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-256">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site** for which you created the certificate request, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="9bb36-257">在**屬性**對話方塊中，按一下 **目錄安全性**索引標籤，然後再按一下**伺服器憑證**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-257">On the **Properties** dialog box, click the **Directory Security** tab, and then click **Server Certificate**.</span></span>  
  
3.  <span data-ttu-id="9bb36-258">在**歡迎**頁面**Web 伺服器憑證精靈**，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-258">On the **Welcome** page of the **Web Server Certificate Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="9bb36-259">在**擱置的憑證要求**頁面上，選取**處理擱置要求及安裝憑證**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-259">On the **Pending Certificate Request** page, select **Process the pending request and install the certificate**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="9bb36-260">在**處理擱置要求**頁面上，輸入`c:\certnew.cer`中**路徑和檔案名稱**文字方塊，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-260">On the **Process a Pending Request** page, type `c:\certnew.cer` in the **Path and file name** text box, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="9bb36-261">按一下**下一步**上**SSL 連接埠**頁面上，按一下**下一步**上**憑證摘要**頁面，然後再按一下**完成**上**確認**頁面。</span><span class="sxs-lookup"><span data-stu-id="9bb36-261">Click **Next** on the **SSL Port** page, click **Next** on the **Certificate Summery** page, and then click **Finish** on the **Confirmation** page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-262">在此逐步解說中，您不需要將伺服器憑證安裝至本機電腦上「信任的根憑證授權單位」存放區，因為憑證服務和 Web 伺服器均安裝在同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="9bb36-262">In this walkthrough you don't need to install the server certificate to the Trusted Root Certification Authorities store on the local computer because both Certificate Services and Web server are installed on the same computer.</span></span>  
  
##  <span data-ttu-id="9bb36-263"><a name="step9"></a>建立後端系統的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9bb36-263"><a name="step9"></a> Create the Web services for the back-end systems</span></span>  
  
#### <a name="to-create-a-new-iis-application-pool-for-the-pending-transaction-web-services"></a><span data-ttu-id="9bb36-264">為擱置交易 Web 服務建立新的 IIS 應用程式集區</span><span class="sxs-lookup"><span data-stu-id="9bb36-264">To create a new IIS application pool for the Pending Transaction Web services</span></span>  
  
1.  <span data-ttu-id="9bb36-265">在**網際網路資訊服務 (IIS) 管理員**，以滑鼠右鍵按一下**應用程式集區**，選取**新增**，然後選取**應用程式集區**.</span><span class="sxs-lookup"><span data-stu-id="9bb36-265">In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **New**, and then select **Application Pool**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-266">服務導向解決方案透過此 Web 服務存取大型主機。</span><span class="sxs-lookup"><span data-stu-id="9bb36-266">The service oriented solution accesses the mainframe through this Web service.</span></span>  
  
2.  <span data-ttu-id="9bb36-267">上**新增應用程式集區**對話方塊方塊中，輸入**應用程式集區識別碼**（任意值），然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-267">On the **Add New Application Pool** dialog box, enter the **Application pool ID** (any value), and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="9bb36-268">在**網際網路資訊服務 (IIS) 管理員**，以滑鼠右鍵按一下您剛應用程式集區建立，並選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-268">In the **Internet Information Services (IIS) Manager**, right-click the application pool that you just created, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="9bb36-269">上**屬性**頁面上，按一下**識別**索引標籤上，選取**可設定**，輸入**使用者名**和**密碼**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-269">On the **Properties** page, click the **Identity** tab, select **Configurable**, enter the **User name** and **Password**, and then click **OK**.</span></span> <span data-ttu-id="9bb36-270">對於此逐步解說，請使用與 BizTalk 服務所使用的相同使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9bb36-270">For this walkthrough, use the same user account that the BizTalk service is using.</span></span>  
  
#### <a name="to-create-the-pendingtransactions-web-service-for-runtime"></a><span data-ttu-id="9bb36-271">為執行階段建立擱置交易 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9bb36-271">To create the PendingTransactions Web service for runtime</span></span>  
  
1.  <span data-ttu-id="9bb36-272">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下 **虛擬目錄**執行**虛擬目錄建立精靈**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-272">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="9bb36-273">使用**虛擬目錄建立精靈**，建立下列虛擬目錄的虛設常式 SAP Web 服務：</span><span class="sxs-lookup"><span data-stu-id="9bb36-273">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:</span></span>  
  
     <span data-ttu-id="9bb36-274">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="9bb36-274">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions</span></span>  
  
     <span data-ttu-id="9bb36-275">路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\MFAccess\PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="9bb36-275">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\MFAccess\PendingTransactions</span></span>  
  
     <span data-ttu-id="9bb36-276">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="9bb36-276">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="9bb36-277">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-277">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="9bb36-278">在**目錄安全性**索引標籤上，按一下 **編輯**修改**驗證和存取控制**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-278">In the **Directory Security** tab, click **Edit** to modify **Authentication and access control**.</span></span> <span data-ttu-id="9bb36-279">選取**基本驗證 （密碼會以純文字傳送）**，清除其他**驗證存取**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9bb36-279">Select **Basic authentication (password is sent in clear text)**, and clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="9bb36-280">按一下**確定**關閉**驗證方法** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9bb36-280">Click **OK** to close the **Authentication Methods** dialog box.</span></span>  
  
    2.  <span data-ttu-id="9bb36-281">在**目錄安全性**索引標籤上，按一下 [**編輯**下**安全通訊**群組方塊，然後再檢查**需要安全通道 (SSL)**中**安全通訊**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9bb36-281">In the **Directory Security** tab, click **Edit** under the **Secure Communication** group box, and then check **Require secure channel (SSL)** in the **Secure Communications** dialog box.</span></span>  
  
    3.  <span data-ttu-id="9bb36-282">在**虛擬目錄**索引標籤上，設定**應用程式集區**建立擱置交易 Web 服務的新 IIS 應用程式集區 」 程序所建立的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="9bb36-282">In the **Virtual Directory** tab, set the **Application Pool** to the application pool that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".</span></span>  
  
#### <a name="to-create-the-pendingtransactions-web-service-for-development-environment"></a><span data-ttu-id="9bb36-283">為開發環境建立擱置交易 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9bb36-283">To create the PendingTransactions Web service for development environment</span></span>  
  
1.  <span data-ttu-id="9bb36-284">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下 **虛擬目錄**執行**虛擬目錄建立精靈**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-284">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="9bb36-285">使用**虛擬目錄建立精靈**，建立下列虛擬目錄的虛設常式 SAP Web 服務：</span><span class="sxs-lookup"><span data-stu-id="9bb36-285">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:</span></span>  
  
     <span data-ttu-id="9bb36-286">Alias = PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="9bb36-286">Alias = PendingTransactions</span></span>  
  
     <span data-ttu-id="9bb36-287">路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\MFAccess\PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="9bb36-287">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\MFAccess\PendingTransactions</span></span>  
  
     <span data-ttu-id="9bb36-288">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="9bb36-288">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="9bb36-289">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下 PendingTransactions，，然後按一下  **屬性**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-289">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click PendingTransactions, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="9bb36-290">在**目錄安全性**索引標籤上，按一下 **編輯**修改**驗證和存取控制**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-290">In the **Directory Security** tab, click **Edit** to modify **Authentication and access control**.</span></span> <span data-ttu-id="9bb36-291">選取**啟用匿名存取**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-291">Select **Enable anonymous access**.</span></span> <span data-ttu-id="9bb36-292">按一下**確定**結束。</span><span class="sxs-lookup"><span data-stu-id="9bb36-292">Click **OK** to exit.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="9bb36-293">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 將使用適用於供開發環境的擱置交易 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bb36-293">The PendingTransactions Web application for development environment will be used by [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="9bb36-294">在生產環境中不需要此 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bb36-294">You don't need this Web application for production environment.</span></span>  
  
    2.  <span data-ttu-id="9bb36-295">在**虛擬目錄**索引標籤上，設定**應用程式集區**建立擱置交易 Web 服務的新 IIS 應用程式集區 」 程序所建立的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="9bb36-295">In the **Virtual Directory** tab, set the **Application Pool** to the application pool that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".</span></span>  
  
#### <a name="to-create-the-stub-sap-web-service"></a><span data-ttu-id="9bb36-296">建立虛設常式 SAP Web 服務</span><span class="sxs-lookup"><span data-stu-id="9bb36-296">To create the Stub SAP Web service</span></span>  
  
1.  <span data-ttu-id="9bb36-297">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下 **虛擬目錄**執行**虛擬目錄建立精靈**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-297">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="9bb36-298">使用**虛擬目錄建立精靈**，建立下列虛擬目錄的虛設常式 SAP Web 服務：</span><span class="sxs-lookup"><span data-stu-id="9bb36-298">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:</span></span>  
  
     <span data-ttu-id="9bb36-299">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP</span><span class="sxs-lookup"><span data-stu-id="9bb36-299">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP</span></span>  
  
     <span data-ttu-id="9bb36-300">路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP</span><span class="sxs-lookup"><span data-stu-id="9bb36-300">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP</span></span>  
  
     <span data-ttu-id="9bb36-301">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="9bb36-301">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="9bb36-302">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP，按一下 **屬性**，，然後修改設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9bb36-302">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="9bb36-303">在**虛擬目錄**索引標籤上，設定**應用程式集區**至\< *YourAppPool*> 您在 < 若要建立新的 IIS 應用程式的程序中建立集區的擱置交易 Web 服務 」。</span><span class="sxs-lookup"><span data-stu-id="9bb36-303">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*> that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".</span></span>  
  
    2.  <span data-ttu-id="9bb36-304">在**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**.</span><span class="sxs-lookup"><span data-stu-id="9bb36-304">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**.</span></span> <span data-ttu-id="9bb36-305">按一下**確定**結束。</span><span class="sxs-lookup"><span data-stu-id="9bb36-305">Click **OK** to exit.</span></span>  
  
##  <span data-ttu-id="9bb36-306"><a name="step11"></a>建立服務導向解決方案的 TI 元件</span><span class="sxs-lookup"><span data-stu-id="9bb36-306"><a name="step11"></a> Create the TI component for the Service Oriented Solution</span></span>  
  
#### <a name="to-create-a-com-application-for-the-ti-component"></a><span data-ttu-id="9bb36-307">建立 TI 元件的 COM+ 應用程式</span><span class="sxs-lookup"><span data-stu-id="9bb36-307">To create a COM+ application for the TI component</span></span>  
  
1.  <span data-ttu-id="9bb36-308">在命令提示字元，執行 %systemroot%\system32\com\comexp.msc。</span><span class="sxs-lookup"><span data-stu-id="9bb36-308">At a command prompt, run %systemroot%\system32\com\comexp.msc.</span></span>  
  
2.  <span data-ttu-id="9bb36-309">在**元件服務**主控台中，展開**元件服務**，依序展開**電腦**，展開**我的電腦**，以滑鼠右鍵按一下**COM + 應用程式**，指向 **新增**，然後按一下 **應用程式**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-309">In **Component Services** console, expand **Component Services**, expand **Computers**, expand **My Computer**, right-click **COM+ Application**, point to **New**, and then click **Application**.</span></span>  
  
    1.  <span data-ttu-id="9bb36-310">在**歡迎**頁面上，按一下**下一步**，然後按一下 **建立空白的應用程式**上**安裝或建立新的應用程式**頁面。</span><span class="sxs-lookup"><span data-stu-id="9bb36-310">On the **Welcome** page, click **Next**, and then click **Create an empty application** on the **Install or Create a New Application** page.</span></span>  
  
    2.  <span data-ttu-id="9bb36-311">型別`BTSScn SO TI Component`中**輸入新的應用程式的名稱**方塊中，選取**伺服器應用程式**為**啟動型別**，然後按一下 **下一步**.</span><span class="sxs-lookup"><span data-stu-id="9bb36-311">Type `BTSScn SO TI Component` in the **Enter a name for the new application** box, select **Server application** as **Activation type**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="9bb36-312">在**帳戶**群組方塊**設定應用程式識別碼**頁面上，選取**這位使用者**，然後輸入使用者名稱和密碼**使用者**和**密碼**方塊。</span><span class="sxs-lookup"><span data-stu-id="9bb36-312">In the **Account** group box of the **Set Application Identity** page, select **This user**, and then type the user name and password in the **User** and **Password** boxes.</span></span> <span data-ttu-id="9bb36-313">新的 COM+ 應用程式會在此帳戶之下執行。</span><span class="sxs-lookup"><span data-stu-id="9bb36-313">The new COM+ application will run under this user account.</span></span> <span data-ttu-id="9bb36-314">此使用者帳戶必須為本機「HIS 執行階段使用者」群組的成員。</span><span class="sxs-lookup"><span data-stu-id="9bb36-314">This user account must be a member of local HIS Runtime Users group.</span></span> <span data-ttu-id="9bb36-315">對於此逐步解說，請使用與 BizTalk 服務所使用的相同使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9bb36-315">For this walkthrough, use the same user account that the BizTalk service is using.</span></span>  
  
    4.  <span data-ttu-id="9bb36-316">在**新增應用程式角色**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-316">On the **Add Application Roles** page, click **Next**.</span></span>  
  
    5.  <span data-ttu-id="9bb36-317">上**將使用者加入角色**頁面上，展開**CreatorOwner**，按一下 **使用者**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-317">On the **Add Users to Roles** page, expand **CreatorOwner**, click **Users**, and then click **Add**.</span></span>  
  
    6.  <span data-ttu-id="9bb36-318">在**選取使用者或群組**對話方塊方塊中，選取將用於存取大型主機的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9bb36-318">On the **Select Users or Groups** dialog box, select a user account that will be used for accessing the mainframe.</span></span> <span data-ttu-id="9bb36-319">對於此逐步解說，請新增 UserID 本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="9bb36-319">For this walkthrough, add UserID local account.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="9bb36-320">若要透過 TI 元件存取 CICS 交易，您可以使用 COM+ 應用程式或裝載 .NET Remoting 元件的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bb36-320">To access the CICS transaction through the TI component, you can use the COM+ application or the Web application hosting the .NET Remoting component.</span></span> <span data-ttu-id="9bb36-321">此逐步解說使用 TI 元件的 COM+ 應用程式和 COM Interop 存取大型主機以改善效能。</span><span class="sxs-lookup"><span data-stu-id="9bb36-321">This walkthrough uses the COM+ application and COM Interop for TI components to access the mainframe to improve performance.</span></span>  
  
    7.  <span data-ttu-id="9bb36-322">在**完成**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-322">On the **Completion** page, click **Finish**.</span></span>  
  
#### <a name="to-create-a-remote-environment-to-access-the-mainframe"></a><span data-ttu-id="9bb36-323">建立遠端環境以存取大型主機</span><span class="sxs-lookup"><span data-stu-id="9bb36-323">To create a Remote Environment to access the mainframe</span></span>  
  
1.  <span data-ttu-id="9bb36-324">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Host Integration Server 2004**，然後按一下  **TI 管理員**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-324">Click **Start**, point to **All Programs**, point to **Microsoft Host Integration Server 2004**, and then click **TI Manager**.</span></span>  
  
2.  <span data-ttu-id="9bb36-325">在**TI 管理員**主控台中，按一下**交易整合器 （組態）**，依序展開**Windows 啟始的處理**，以滑鼠右鍵按一下**遠端環境**，指向 **新增**，然後按一下 **遠端環境**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-325">In the **TI Manager** console, click **Transaction Integrator (Configuration)**, expand **Windows Initiated Processing**, right-click **Remote Environments**, point to **New**, and then click **Remote Environment**.</span></span>  
  
    1.  <span data-ttu-id="9bb36-326">在**歡迎**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-326">On the **Welcome** page, click **Next**.</span></span>  
  
    2.  <span data-ttu-id="9bb36-327">在**設定新的遠端環境**頁面上，輸入**遠端應用程式名稱**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-327">On the **Configure a New Remote Environment** page, type the **Remote Application Name**, and then click **Next**.</span></span> <span data-ttu-id="9bb36-328">對於此逐步解說，請使用 Mainframe_TCP 做為名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb36-328">For this walkthrough, use Mainframe_TCP for the name.</span></span>  
  
    3.  <span data-ttu-id="9bb36-329">在**設定主機環境和程式設計模型**頁面上，選取**CICS**如**目標主機**和**茱萸連結**的**程式設計模型**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-329">On the **Configure Host Environment and Programming Model** page, select **CICS** for the **Target host** and **ELM Link** for the **Programming model**, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="9bb36-330">在**設定結束點 TCP/IP**頁面上，輸入在大型主機的 IP 位址**IP/DNS 位址**方塊，然後再按一下**編輯**新增連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-330">On **the Configure Endpoint TCP/IP** page, type the IP address for your mainframe in the **IP/DNS address** box, and then click **Edit** to add the port number.</span></span> <span data-ttu-id="9bb36-331">您的 HIS COM 將會透過結束點位址存取交易。</span><span class="sxs-lookup"><span data-stu-id="9bb36-331">Your HIS COM will access the transactions through the endpoint address.</span></span>  
  
    5.  <span data-ttu-id="9bb36-332">在**完成**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-332">On the **Completion** page, click **Finish**.</span></span>  
  
#### <a name="to-create-the-ti-component-for-the-service-oriented-solution"></a><span data-ttu-id="9bb36-333">建立服務導向解決方案的 TI 元件</span><span class="sxs-lookup"><span data-stu-id="9bb36-333">To create the TI Component for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="9bb36-334">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Host Integration Server 2004**，然後按一下  **TI 管理員**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-334">Click **Start**, point to **All Programs**, point to **Microsoft Host Integration Server 2004**, and then click **TI Manager**.</span></span>  
  
2.  <span data-ttu-id="9bb36-335">在**TI 管理員**主控台中，按一下**交易整合器 （組態）**，按一下  **Windows 啟始的處理**，然後按一下  **物件**.</span><span class="sxs-lookup"><span data-stu-id="9bb36-335">In the **TI Manager** console, click **Transaction Integrator (Configuration)**, click **Windows Initiated Processing**, and then click **Objects**.</span></span> <span data-ttu-id="9bb36-336">以滑鼠右鍵按一下**物件**，按一下 **新增**，然後按一下 **物件**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-336">Right-click **Objects**, click **New**, and then click **Object**.</span></span>  
  
    1.  <span data-ttu-id="9bb36-337">在**歡迎**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-337">On the **Welcome** page, click **Next**.</span></span>  
  
    2.  <span data-ttu-id="9bb36-338">在**指定或尋找物件**頁面上，按一下**瀏覽**，在 %BTSSolutionsPath%\SO\MFAccess\HISTIComponent 資料夾中，選擇 SOHISTIUsingCOM.TLB，然後按一下**下一步**.</span><span class="sxs-lookup"><span data-stu-id="9bb36-338">On the **Specify Or Locate An Object** page, click **Browse**, choose the SOHISTIUsingCOM.TLB in the %BTSSolutionsPath%\SO\MFAccess\HISTIComponent folder, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="9bb36-339">上**COM 物件的定義環境特性**頁面上，選取**BTSScn SO TI Component**如**COM + 應用程式**，然後按一下 [**下一步]**.</span><span class="sxs-lookup"><span data-stu-id="9bb36-339">On the **Define Environment Characteristics for The COM Object** page, select **BTSScn SO TI Component** for the **COM+ application**, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="9bb36-340">在**定義遠端環境**頁面上，選取您在先前的程序中建立的遠端環境**遠端環境，然後按一下 [下一步]。**</span><span class="sxs-lookup"><span data-stu-id="9bb36-340">On the **Define Remote Environment** page, select the remote environment that you created in the previous procedure for the **Remote environment, and then click Next.**</span></span>  
  
    5.  <span data-ttu-id="9bb36-341">在**建立 WIP 物件**頁面上，按一下**下一步**，然後按一下 **完成**上**完成**頁面。</span><span class="sxs-lookup"><span data-stu-id="9bb36-341">On the **Creation of WIP Objects** page, click **Next**, and then click **Finish** on the **Completion** page.</span></span>  
  
#### <a name="to-test-the-connectivity-to-the-mainframe"></a><span data-ttu-id="9bb36-342">測試大型主機連線</span><span class="sxs-lookup"><span data-stu-id="9bb36-342">To test the connectivity to the mainframe</span></span>  
  
1.  <span data-ttu-id="9bb36-343">在 Windows 檔案總管中，瀏覽至 %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester 資料夾，然後按兩下 Interop.SOHISTIUsingCOM.dll.reg 檔案。</span><span class="sxs-lookup"><span data-stu-id="9bb36-343">In Windows Explorer, browse to the %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester folder, and then double-click the Interop.SOHISTIUsingCOM.dll.reg file.</span></span> <span data-ttu-id="9bb36-344">如此可新增 HISTISimpleTester 應用程式的登錄值，以透過「執行階段可呼叫包裝函式」(RCW) 呼叫 TI 元件。</span><span class="sxs-lookup"><span data-stu-id="9bb36-344">This adds registry values for the HISTISimpleTester application to call the TI component through the Runtime Callable Wrapper (RCW).</span></span>  
  
2.  <span data-ttu-id="9bb36-345">在 Windows 檔案總管中，瀏覽至 %BTSSolutionsPath%\SO\MFAccess\ 資料夾，然後執行 SetupMFAccess.bat。</span><span class="sxs-lookup"><span data-stu-id="9bb36-345">In Windows Explorer, browse to the %BTSSolutionsPath%\SO\MFAccess\ folder, and then run SetupMFAccess.bat.</span></span>  
  
3.  <span data-ttu-id="9bb36-346">在 Windows 檔案總管中，巡覽至 %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester\bin\Debug 資料夾，然後執行 BTSScnSOHISTIComponentSimpleTester.exe。</span><span class="sxs-lookup"><span data-stu-id="9bb36-346">In Windows Explorer, navigate to the %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester\bin\Debug folder, and then run BTSScnSOHISTIComponentSimpleTester.exe.</span></span>  
  
    -   <span data-ttu-id="9bb36-347">在 HISTISimpleTester 應用程式中，按一下**呼叫大型主機程式-使用 COM**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-347">In the HISTISimpleTester application, click **Call Mainframe Program - Using COM**.</span></span> <span data-ttu-id="9bb36-348">它會從在大型主機上執行的 COBOL 應用程式傳回五筆記錄。</span><span class="sxs-lookup"><span data-stu-id="9bb36-348">It returns five records from the COBOL application running on the mainframe.</span></span>  
  
##  <span data-ttu-id="9bb36-349"><a name="step13"></a>建立協調流程的虛擬目錄的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9bb36-349"><a name="step13"></a> Create the virtual directories for the orchestration Web services</span></span>  
  
#### <a name="to-create-the-virtual-directories-for-the-orchestration-web-services"></a><span data-ttu-id="9bb36-350">為協調流程 Web 服務建立虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="9bb36-350">To create the virtual directories for the orchestration Web services</span></span>  
  
1.  <span data-ttu-id="9bb36-351">在**網際網路資訊服務 (IIS) 管理員**，以滑鼠右鍵按一下**應用程式集區**，選取**新增**，然後選取**應用程式集區**.</span><span class="sxs-lookup"><span data-stu-id="9bb36-351">In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **New**, and then select **Application Pool**.</span></span>  
  
    1.  <span data-ttu-id="9bb36-352">上**新增應用程式集區**對話方塊方塊中，輸入**應用程式集區識別碼**（任意值），然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-352">On the **Add New Application Pool** dialog box, enter the **Application pool ID** (any value), and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="9bb36-353">以滑鼠右鍵按一下您剛應用程式集區建立，，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-353">Right-click the application pool that you just created, and then select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="9bb36-354">上**屬性**頁面上，按一下**識別**索引標籤上，選取**可設定**，輸入**使用者名**和**密碼**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-354">On the **Properties** page, click the **Identity** tab, select **Configurable**, enter the **User name** and **Password**, and then click **OK**.</span></span> <span data-ttu-id="9bb36-355">對於此逐步解說，請使用與 BizTalk 服務所使用的相同使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9bb36-355">For this walkthrough use the same user account that the BizTalk service is using.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-356">此使用者必須具有執行協調流程 Proxy Web 服務的權限，並且必須新增至 BizTalk Server 系統管理員、SSO 系統管理員或 SSO 分支機構系統管理員群組其中之一</span><span class="sxs-lookup"><span data-stu-id="9bb36-356">This user must have permission to execute the Orchestration Proxy Web service, and must be added to one of the BizTalk Server Administrators, SSO Administrators, or SSO Affiliated Administrators groups</span></span>  
  
2.  <span data-ttu-id="9bb36-357">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下 **虛擬目錄**執行**虛擬目錄建立精靈**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-357">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="9bb36-358">使用**虛擬目錄建立精靈**，proxy Web 服務配接器版本建立下列虛擬目錄：</span><span class="sxs-lookup"><span data-stu-id="9bb36-358">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
     <span data-ttu-id="9bb36-359">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter</span><span class="sxs-lookup"><span data-stu-id="9bb36-359">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter</span></span>  
  
     <span data-ttu-id="9bb36-360">路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\OrchProxy\Adapter</span><span class="sxs-lookup"><span data-stu-id="9bb36-360">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Adapter</span></span>  
  
     <span data-ttu-id="9bb36-361">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="9bb36-361">Access Permissions = Read, Run scripts</span></span>  
  
3.  <span data-ttu-id="9bb36-362">在**網際網路資訊服務 (IIS) 管理員**，展開**網站**展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter，按一下 **屬性**，，然後修改設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9bb36-362">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="9bb36-363">在**虛擬目錄**索引標籤上，設定**應用程式集區**至\< *YourAppPool*> 您在上一個步驟中建立。</span><span class="sxs-lookup"><span data-stu-id="9bb36-363">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*> that you created in the previous step.</span></span>  
  
    2.  <span data-ttu-id="9bb36-364">在**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，選取**只整合式 Windows 驗證啟用**，然後清除其他**驗證存取**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9bb36-364">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="9bb36-365">按一下**確定**結束。</span><span class="sxs-lookup"><span data-stu-id="9bb36-365">Click **OK** to exit.</span></span>  
  
4.  <span data-ttu-id="9bb36-366">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下 **虛擬目錄**執行**虛擬目錄建立精靈**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-366">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="9bb36-367">使用**虛擬目錄建立精靈**，proxy 的內嵌版本的 Web 服務建立下列虛擬目錄：</span><span class="sxs-lookup"><span data-stu-id="9bb36-367">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the inline version:</span></span>  
  
     <span data-ttu-id="9bb36-368">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline</span><span class="sxs-lookup"><span data-stu-id="9bb36-368">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline</span></span>  
  
     <span data-ttu-id="9bb36-369">路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\OrchProxy\Inline</span><span class="sxs-lookup"><span data-stu-id="9bb36-369">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Inline</span></span>  
  
     <span data-ttu-id="9bb36-370">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="9bb36-370">Access Permissions = Read, Run scripts</span></span>  
  
5.  <span data-ttu-id="9bb36-371">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline，按一下 **屬性**，，然後修改設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9bb36-371">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="9bb36-372">在**虛擬目錄**索引標籤上，設定**應用程式集區**至\< *YourAppPool*> 您剛剛建立。</span><span class="sxs-lookup"><span data-stu-id="9bb36-372">On the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*> you just created.</span></span>  
  
    2.  <span data-ttu-id="9bb36-373">按一下**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，選取**只整合式 Windows 驗證啟用**，然後清除其他**驗證存取**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9bb36-373">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="9bb36-374">按一下**確定**結束。</span><span class="sxs-lookup"><span data-stu-id="9bb36-374">Click **OK** to exit.</span></span>  
  
##  <span data-ttu-id="9bb36-375"><a name="step15"></a>建置服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9bb36-375"><a name="step15"></a> Build the Service Oriented Solution</span></span>  
  
#### <a name="to-build-the-service-oriented-solution"></a><span data-ttu-id="9bb36-376">建置服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9bb36-376">To build the Service Oriented solution</span></span>  
  
-   <span data-ttu-id="9bb36-377">在命令提示字元中，將目錄變更至 %btssolutionspath%\so\btssoln，型別`SetupBTSSoln.bat`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="9bb36-377">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln, type `SetupBTSSoln.bat`, and then press ENTER.</span></span> <span data-ttu-id="9bb36-378">SetupBTSSoln.bat 會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="9bb36-378">The SetupBTSSoln.bat performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="9bb36-379">建立唯一的強式名稱金鑰 (SNK) 以簽署 SO 方案的組件。</span><span class="sxs-lookup"><span data-stu-id="9bb36-379">Creates a unique strong name key (SNK) for signing the assemblies of the SO Solution.</span></span>  
  
    -   <span data-ttu-id="9bb36-380">從 SNK 擷取公開金鑰 Token 並以公開 Token 更新繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="9bb36-380">Extracts the public key token from the SNK and updates the binding files with the public token.</span></span>  
  
    -   <span data-ttu-id="9bb36-381">建置 SO 解決方案。</span><span class="sxs-lookup"><span data-stu-id="9bb36-381">Builds the SO solution.</span></span>  
  
    -   <span data-ttu-id="9bb36-382">在 %BTSSolutionsPath%\Common 資料夾中建置 SSOApplicationConfig。</span><span class="sxs-lookup"><span data-stu-id="9bb36-382">Builds the SSOApplicationConfig in the %BTSSolutionsPath%\Common folder.</span></span>  
  
##  <span data-ttu-id="9bb36-383"><a name="step17"></a>建立 SSO 分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="9bb36-383"><a name="step17"></a> Create the SSO affiliate applications</span></span>  
  
#### <a name="to-create-the-sso-affiliate-applications"></a><span data-ttu-id="9bb36-384">建立 SSO 分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="9bb36-384">To create the SSO affiliate applications</span></span>  
  
1.  <span data-ttu-id="9bb36-385">開啟命令提示字元，然後將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9bb36-385">Open a command prompt, and then change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.</span></span>  
  
2.  <span data-ttu-id="9bb36-386">在命令提示字元，使用「記事本」開啟 PendTransAffApp.xml，並加以檢視。</span><span class="sxs-lookup"><span data-stu-id="9bb36-386">At the command prompt, open the PendTransAffApp.xml using Notepad, and review it.</span></span> <span data-ttu-id="9bb36-387">不需要變更此檔案。</span><span class="sxs-lookup"><span data-stu-id="9bb36-387">No changes to this file are necessary.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-388">PendTransAffApp.xml 檔案為擱置交易後端系統定義 SSO 分支機構應用程式 (WoodgroveBank.PendingTransactions)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-388">The PendTransAffApp.xml file defines the SSO affiliate application, WoodgroveBank.PendingTransactions, for the Pending Transactions back-end system.</span></span> <span data-ttu-id="9bb36-389">它也為 SSO 分支機構應用程式定義使用者和系統管理群組。</span><span class="sxs-lookup"><span data-stu-id="9bb36-389">It also defines the user and administrative groups for the SSO affiliate application.</span></span> <span data-ttu-id="9bb36-390">本逐步解說中，使用**BizTalk 應用程式使用者**和**BizTalk Server 系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-390">For this walkthrough, use **BizTalk Application Users** and **BizTalk Server Administrators**.</span></span>  
    >   
    >  <span data-ttu-id="9bb36-391">如果您想要針對 SSO 分支機構應用程式使用不同的群組，您需要在 Active Directory 中，建立 Windows 群組 （以任何名稱），然後變更**appAdminAccount**和**appUserAccount**PendTransAffApp.xml 中的節點。</span><span class="sxs-lookup"><span data-stu-id="9bb36-391">If you want to use different groups for the SSO affiliate application, you need to create Windows groups (with any name) in the Active Directory, and then change the **appAdminAccount** and **appUserAccount** nodes in the PendTransAffApp.xml.</span></span> <span data-ttu-id="9bb36-392">如果您這樣做，您應該設定的值**groupApp**屬性**旗標**節點為"yes"。</span><span class="sxs-lookup"><span data-stu-id="9bb36-392">If you do this, you should set the value for **groupApp** attribute of **flags** node to "yes".</span></span>  
    >   
    >  <span data-ttu-id="9bb36-393">如需 SSO 分支機構應用程式的詳細資訊，請參閱[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-393">For more information about SSO affiliate applications, see [SSO Affiliate Applications](../core/sso-affiliate-applications.md).</span></span>  
  
3.  <span data-ttu-id="9bb36-394">在命令提示字元，使用「記事本」開啟 PendTransUserMap.xml 檔案，然後進行下列編輯：</span><span class="sxs-lookup"><span data-stu-id="9bb36-394">At the command prompt, open the PendTransUserMap.xml file using Notepad, and then make the following edits:</span></span>  
  
    ```  
    <mapping>  
      <windowsDomain><DomainName></windowsDomain>  
      <windowsUserId><UserID></windowsUserId>  
      <externalUserId><ExternalUserID></externalUserId>  
    </mapping>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-395">PendTransUserMap.xml 檔案包含擱置交易後端系統的使用者對應。</span><span class="sxs-lookup"><span data-stu-id="9bb36-395">The PendTransUserMap.xml file contains the user mappings for the Pending Transactions back-end system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-396">如**externalUserId**  節點，用於擱置交易後端系統的外部使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-396">For the **externalUserId** node, use the external user ID for the Pending Transactions back-end system.</span></span> <span data-ttu-id="9bb36-397">對於此逐步解說，請使用 UserID 做為外部識別碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-397">For this walkthrough, use UserID for the external ID.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-398">如**windowsUserId**節點中，輸入使用者名稱**externalUserId**會對應至。</span><span class="sxs-lookup"><span data-stu-id="9bb36-398">For the **windowsUserId** node, enter the user name which the **externalUserId** will map to.</span></span> <span data-ttu-id="9bb36-399">您可以使用網域群組和網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9bb36-399">You can use both a domain group and a domain user account.</span></span> <span data-ttu-id="9bb36-400">此使用者必須為被允許使用擱置交易後端系統的群組成員。</span><span class="sxs-lookup"><span data-stu-id="9bb36-400">This user must be a member of the group that will be allowed to use the Pending Transactions back-end system.</span></span> <span data-ttu-id="9bb36-401">對於此逐步解說，請使用 BizTalk 服務的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb36-401">For this walkthrough, use the user name of the BizTalk service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-402">如**windowsDomain**節點中，輸入網域名稱的**windowsUserId**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-402">For the **windowsDomain** node, enter the domain name of the **windowsUserId**.</span></span>  
  
4.  <span data-ttu-id="9bb36-403">在命令提示字元，使用「記事本」開啟 PmntTrckAffApp.xml 檔案，並檢視檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="9bb36-403">At the command prompt, open the PmntTrckAffApp.xml file using Notepad, and review the contents of the file.</span></span> <span data-ttu-id="9bb36-404">不需要變更此檔案。</span><span class="sxs-lookup"><span data-stu-id="9bb36-404">No changes to this file are necessary.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-405">PmntTrckAffApp.xml 檔案為付款追蹤器後端系統定義 SSO 分支機構應用程式 (WoodgroveBank.PaymentTracker)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-405">The PmntTrckAffApp.xml file defines the SSO affiliate application, WoodgroveBank.PaymentTracker, for the Payment Tracker back-end system.</span></span>  
  
5.  <span data-ttu-id="9bb36-406">在命令提示字元，使用「記事本」開啟 PmntTrckUserMap.xml 檔案，然後進行下列編輯：</span><span class="sxs-lookup"><span data-stu-id="9bb36-406">At the command prompt, open the PmntTrckUserMap.xml file using Notepad, and then make the following edits:</span></span>  
  
    ```  
    <mapping>  
      <windowsDomain><DomainName></windowsDomain>  
      <windowsUserId><UserID></windowsUserId>  
      <externalUserId><ExternalUserID></externalUserId>  
    </mapping>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-407">付款追蹤器 SSO 附屬應用程式將用於 MQSeries 配接器，並透過 MQSeries 標頭屬性傳送對應的外部使用者識別碼/密碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-407">The Payment Tracker SSO affiliated application will be used for the MQSeries Adapter and the mapped external user ID/password are sent through MQSeries header properties.</span></span> <span data-ttu-id="9bb36-408">MQSeries Server 僅驗證 MQSeries 配接器在其下執行的 BizTalk 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="9bb36-408">The MQSeries Server validates only the BizTalk service account, under which MQSeries Adapter is running.</span></span> <span data-ttu-id="9bb36-409">它不會驗證任何外部使用者認證。</span><span class="sxs-lookup"><span data-stu-id="9bb36-409">It doesn't validate any external user credential.</span></span>  
    >   
    >  <span data-ttu-id="9bb36-410">如需有關 SSO 附屬 MQSeries 配接器的應用程式，請參閱 <<c0> [ 如何設定 MQSeries 配接器接收位置和傳送埠](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-410">For more information about SSO affiliated applications for the MQSeries Adapter, see [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-411">PmntTrckUserMap.xml 檔案包含付款追蹤器後端系統的 SSO 使用者對應。</span><span class="sxs-lookup"><span data-stu-id="9bb36-411">The PmntTrckUserMap.xml file contains the SSO user mappings for the Payment Tracker back-end system.</span></span> <span data-ttu-id="9bb36-412">付款追蹤器模擬器程式可模擬使用者驗證的成功與錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="9bb36-412">The Payment Tracker simulator program simulates both success and failure conditions for user authentication.</span></span>  
    >   
    >  <span data-ttu-id="9bb36-413">程式順利驗證所有以字母開頭的使用者識別碼**PT** (例如， **PTUserID**)，而無法驗證使用者識別碼不是以**PT**.</span><span class="sxs-lookup"><span data-stu-id="9bb36-413">The program successfully authenticates all user IDs that begin with the letters **PT** (for example, **PTUserID**), and fails to authenticate any user IDs that do not begin with **PT**.</span></span> <span data-ttu-id="9bb36-414">這樣可讓您依照想要測試的條件來選擇適合的使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-414">This enables you to choose the appropriate user ID depending on the condition that you would like to test.</span></span> <span data-ttu-id="9bb36-415">您也可以重複整個**對應**針對每個使用者識別碼的節點並在相同的檔案中定義多個對應。</span><span class="sxs-lookup"><span data-stu-id="9bb36-415">You can also repeat the entire **mapping** node for each user ID and define multiple mappings in the same file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-416">如**externalUserId**節點中，輸入付款追蹤器後端系統的外部使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-416">For the **externalUserId** node, enter the external user ID for the Payment Tracker back-end system.</span></span> <span data-ttu-id="9bb36-417">對於此逐步解說，請使用 PTUserID 做為外部識別碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-417">For this walkthrough, use PTUserID for the external ID.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-418">如**windowsUserId**節點中，輸入使用者名稱**externalUserId**會對應至。</span><span class="sxs-lookup"><span data-stu-id="9bb36-418">For the **windowsUserId** node, enter the user name which the **externalUserId** will map to.</span></span> <span data-ttu-id="9bb36-419">此使用者必須為被允許使用付款追蹤器後端系統的群組成員。</span><span class="sxs-lookup"><span data-stu-id="9bb36-419">This user must be a member of the group that will be allowed to use the Payment Tracker back-end system.</span></span> <span data-ttu-id="9bb36-420">對於此逐步解說，請使用 BizTalk 服務的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb36-420">For this walkthrough, use the user name of the BizTalk service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-421">如**windowsDomain**節點中，輸入網域名稱的**windowsUserId**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-421">For the **windowsDomain** node, enter the domain name of the **windowsUserId**.</span></span>  
  
6.  <span data-ttu-id="9bb36-422">在命令提示字元，使用「記事本」開啟 ConfigStoreApp.xml 檔案，然後檢視檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="9bb36-422">At the command prompt, open the ConfigStoreApp.xml file using Notepad, and then review the contents of the file.</span></span>  
  
     <span data-ttu-id="9bb36-423">此檔案會定義 SSO 中實例用以保存組態參數的組態存放區應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bb36-423">This file defines the configuration store application in SSO that the scenario uses to keep configuration parameters.</span></span> <span data-ttu-id="9bb36-424">部分組態參數包括在與 SAP (配接器與內嵌版本) 通訊時的 [逾時] 值，以及佇列管理員名稱和使用內嵌版本時使用的佇列。</span><span class="sxs-lookup"><span data-stu-id="9bb36-424">Some of the configuration parameters include the Timeout value when communicating with SAP (for both the adapter and inline versions) and the name of the queue manager and queues to use when using the inline version.</span></span> <span data-ttu-id="9bb36-425">不需要變更此檔案。</span><span class="sxs-lookup"><span data-stu-id="9bb36-425">No changes to this file are necessary.</span></span>  
  
7.  <span data-ttu-id="9bb36-426">在命令提示字元，使用「記事本」開啟 SetConfigValuesInSSO.cmd 檔案，檢視並變更檔案的內容，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="9bb36-426">At the command prompt, open the SetConfigValuesInSSO.cmd file using Notepad, review and change the contents of the file as the following table.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-427">此命令檔設定 SSO 資料庫中的組態參數值。</span><span class="sxs-lookup"><span data-stu-id="9bb36-427">This command file sets the values for the configuration parameters in the SSO database.</span></span> <span data-ttu-id="9bb36-428">它包含數個可為命令檔開頭的本機變數指派值的設定命令。</span><span class="sxs-lookup"><span data-stu-id="9bb36-428">It contains several set commands that assign the values to local variables in the beginning of the command file.</span></span>  
    >   
    >  <span data-ttu-id="9bb36-429">SAPAdapterTimeout、PendingTransactionsAdapterTimeout 和 PaymentTrackingAdapterTimeout 值用於配接器版本。</span><span class="sxs-lookup"><span data-stu-id="9bb36-429">The SAPAdapterTimeout, PendingTransactionsAdapterTimeout, and PaymentTrackingAdapterTimeout values are used in the adapter version.</span></span> <span data-ttu-id="9bb36-430">其餘的值則用於內嵌版本中。</span><span class="sxs-lookup"><span data-stu-id="9bb36-430">The remaining values are used in the inline version.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-431">您可以輸入""（兩個雙引號） 標記的預設值\<使用者指定 > 下表中。</span><span class="sxs-lookup"><span data-stu-id="9bb36-431">You can enter " " (two double quotes) for the default values marked \<User Specified> in the following table.</span></span>  
  
    |<span data-ttu-id="9bb36-432">參數</span><span class="sxs-lookup"><span data-stu-id="9bb36-432">Parameter</span></span>|<span data-ttu-id="9bb36-433">預設值</span><span class="sxs-lookup"><span data-stu-id="9bb36-433">Default Value</span></span>|<span data-ttu-id="9bb36-434">Description</span><span class="sxs-lookup"><span data-stu-id="9bb36-434">Description</span></span>|  
    |---------------|-------------------|-----------------|  
    |<span data-ttu-id="9bb36-435">SAPAdapterTimeout</span><span class="sxs-lookup"><span data-stu-id="9bb36-435">SAPAdapterTimeout</span></span>|<span data-ttu-id="9bb36-436">20000</span><span class="sxs-lookup"><span data-stu-id="9bb36-436">20000</span></span>|<span data-ttu-id="9bb36-437">對 SAP 後端要求的最大逾時 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="9bb36-437">Max timeout (millisecond) for a request to the SAP back-end</span></span>|  
    |<span data-ttu-id="9bb36-438">SAPInlineTimeout</span><span class="sxs-lookup"><span data-stu-id="9bb36-438">SAPInlineTimeout</span></span>|<span data-ttu-id="9bb36-439">20000</span><span class="sxs-lookup"><span data-stu-id="9bb36-439">20000</span></span>|<span data-ttu-id="9bb36-440">對 SAP 後端要求的最大逾時 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="9bb36-440">Max timeout (millisecond) for a request to the SAP back-end</span></span>|  
    |<span data-ttu-id="9bb36-441">SAPInlineHostName</span><span class="sxs-lookup"><span data-stu-id="9bb36-441">SAPInlineHostName</span></span>|<span data-ttu-id="9bb36-442">\<指定使用者 ></span><span class="sxs-lookup"><span data-stu-id="9bb36-442">\<User Specified></span></span>|<span data-ttu-id="9bb36-443">SAP 後端識別項</span><span class="sxs-lookup"><span data-stu-id="9bb36-443">SAP back-end identifier</span></span>|  
    |<span data-ttu-id="9bb36-444">SAPInlineClientNumber</span><span class="sxs-lookup"><span data-stu-id="9bb36-444">SAPInlineClientNumber</span></span>|<span data-ttu-id="9bb36-445">\<指定使用者 ></span><span class="sxs-lookup"><span data-stu-id="9bb36-445">\<User Specified></span></span>|<span data-ttu-id="9bb36-446">SAP 用戶端編號</span><span class="sxs-lookup"><span data-stu-id="9bb36-446">SAP Client number</span></span>|  
    |<span data-ttu-id="9bb36-447">SAPInlineSystemNumber</span><span class="sxs-lookup"><span data-stu-id="9bb36-447">SAPInlineSystemNumber</span></span>|<span data-ttu-id="9bb36-448">\<指定使用者 ></span><span class="sxs-lookup"><span data-stu-id="9bb36-448">\<User Specified></span></span>|<span data-ttu-id="9bb36-449">SAP 系統編號</span><span class="sxs-lookup"><span data-stu-id="9bb36-449">SAP System number</span></span>|  
    |<span data-ttu-id="9bb36-450">SAPInlineUserName</span><span class="sxs-lookup"><span data-stu-id="9bb36-450">SAPInlineUserName</span></span>|<span data-ttu-id="9bb36-451">\<指定使用者 ></span><span class="sxs-lookup"><span data-stu-id="9bb36-451">\<User Specified></span></span>|<span data-ttu-id="9bb36-452">用以連接到 SAP 後端的使用者名稱</span><span class="sxs-lookup"><span data-stu-id="9bb36-452">The user name used to connect to the SAP back-end</span></span>|  
    |<span data-ttu-id="9bb36-453">SAPInlinePassword</span><span class="sxs-lookup"><span data-stu-id="9bb36-453">SAPInlinePassword</span></span>|<span data-ttu-id="9bb36-454">\<指定使用者 ></span><span class="sxs-lookup"><span data-stu-id="9bb36-454">\<User Specified></span></span>|<span data-ttu-id="9bb36-455">用以連接到 SAP 後端的密碼</span><span class="sxs-lookup"><span data-stu-id="9bb36-455">The password used to connect to the SAP back-end</span></span>|  
    |<span data-ttu-id="9bb36-456">PendingTransactionsAdapterTimeout</span><span class="sxs-lookup"><span data-stu-id="9bb36-456">PendingTransactionsAdapterTimeout</span></span>|<span data-ttu-id="9bb36-457">20000</span><span class="sxs-lookup"><span data-stu-id="9bb36-457">20000</span></span>|<span data-ttu-id="9bb36-458">對擱置交易伺服器要求的最大逾時 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="9bb36-458">Max timeout (millisecond) for a request to the Pending Transactions server</span></span>|  
    |<span data-ttu-id="9bb36-459">PendingTransactionsInlineTimeout</span><span class="sxs-lookup"><span data-stu-id="9bb36-459">PendingTransactionsInlineTimeout</span></span>|<span data-ttu-id="9bb36-460">20000</span><span class="sxs-lookup"><span data-stu-id="9bb36-460">20000</span></span>|<span data-ttu-id="9bb36-461">對擱置交易伺服器要求的最大逾時 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="9bb36-461">Max timeout (millisecond) for a request to the Pending Transactions server</span></span>|  
    |<span data-ttu-id="9bb36-462">PendingTransactionsInlineURL</span><span class="sxs-lookup"><span data-stu-id="9bb36-462">PendingTransactionsInlineURL</span></span>|<span data-ttu-id="9bb36-463">https://\<*您的電腦名稱*> /Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions/PendTransWS.asmx</span><span class="sxs-lookup"><span data-stu-id="9bb36-463">https://\<*your computer name*>/Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions/PendTransWS.asmx</span></span>|<span data-ttu-id="9bb36-464">擱置交易服務的 URL。</span><span class="sxs-lookup"><span data-stu-id="9bb36-464">URL of the Pending Transactions service.</span></span> <span data-ttu-id="9bb36-465">\<*您的電腦名稱*> 必須符合**一般名稱**中建立憑證要求 」 程序。</span><span class="sxs-lookup"><span data-stu-id="9bb36-465">\<*Your computer name*> must match the **common name** in the procedure "To create a certificate request".</span></span> <span data-ttu-id="9bb36-466">您必須使用"localhost"的\<*您的電腦名稱*>。</span><span class="sxs-lookup"><span data-stu-id="9bb36-466">You must not use "localhost" for \<*Your computer name*>.</span></span>|  
    |<span data-ttu-id="9bb36-467">PendingTransactionsInlineSSOAffiliateApp</span><span class="sxs-lookup"><span data-stu-id="9bb36-467">PendingTransactionsInlineSSOAffiliateApp</span></span>|<span data-ttu-id="9bb36-468">WoodgroveBank.PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="9bb36-468">WoodgroveBank.PendingTransactions</span></span>|<span data-ttu-id="9bb36-469">擱置交易 SSO 應用程式名稱</span><span class="sxs-lookup"><span data-stu-id="9bb36-469">Pending Transactions SSO application name</span></span>|  
    |<span data-ttu-id="9bb36-470">PaymentTrackingAdapterTimeout</span><span class="sxs-lookup"><span data-stu-id="9bb36-470">PaymentTrackingAdapterTimeout</span></span>|<span data-ttu-id="9bb36-471">20000</span><span class="sxs-lookup"><span data-stu-id="9bb36-471">20000</span></span>|<span data-ttu-id="9bb36-472">對付款追蹤系統要求的最大逾時 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="9bb36-472">Max timeout (millisecond) for a request to the Payment Tracking system</span></span>|  
    |<span data-ttu-id="9bb36-473">PaymentTrackingInlineTimeout</span><span class="sxs-lookup"><span data-stu-id="9bb36-473">PaymentTrackingInlineTimeout</span></span>|<span data-ttu-id="9bb36-474">20000</span><span class="sxs-lookup"><span data-stu-id="9bb36-474">20000</span></span>|<span data-ttu-id="9bb36-475">對付款追蹤系統要求的最大逾時 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="9bb36-475">Max timeout (millisecond) for a request to the Payment Tracking system</span></span>|  
    |<span data-ttu-id="9bb36-476">PaymentTrackingInlineQManager</span><span class="sxs-lookup"><span data-stu-id="9bb36-476">PaymentTrackingInlineQManager</span></span>|<span data-ttu-id="9bb36-477">\<使用者指定 > (通常是 Qm_<\<*您的電腦名稱*>)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-477">\<User Specified> (Typically QM_\<*your computer name*>).</span></span>|<span data-ttu-id="9bb36-478">MQSeries 佇列管理員名稱</span><span class="sxs-lookup"><span data-stu-id="9bb36-478">MQSeries Queue Manager name</span></span>|  
    |<span data-ttu-id="9bb36-479">PaymentTrackingInlineMQChannelDefinition</span><span class="sxs-lookup"><span data-stu-id="9bb36-479">PaymentTrackingInlineMQChannelDefinition</span></span>|<span data-ttu-id="9bb36-480">" " (必須輸入兩個雙引號)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-480">" " (need to enter the two double quotes).</span></span>|<span data-ttu-id="9bb36-481">若為本機則為空字串，或為遠端 MQ 伺服器的格式化通道名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb36-481">Empty string if local, or formatted channel name of the remote MQ server.</span></span> <span data-ttu-id="9bb36-482">如果您在設定 IBM WebSphere MQ 保留所有預設設定，則通道定義將 S__<\<*您的電腦名稱*> /TCP/\<*您的電腦名稱*> (1414)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-482">If you keep all default settings in configuring IBM WebSphere MQ, the channel definition will be S__\<*your computer name*>/TCP/\<*your computer name*>(1414).</span></span>|  
    |<span data-ttu-id="9bb36-483">PaymentTrackingInlineRequestQueue</span><span class="sxs-lookup"><span data-stu-id="9bb36-483">PaymentTrackingInlineRequestQueue</span></span>|<span data-ttu-id="9bb36-484">LastPaymentsInputQueue</span><span class="sxs-lookup"><span data-stu-id="9bb36-484">LastPaymentsInputQueue</span></span>|<span data-ttu-id="9bb36-485">付款追蹤要求的 MQ 佇列名稱</span><span class="sxs-lookup"><span data-stu-id="9bb36-485">The MQ Queue name for payment tracking requests</span></span>|  
    |<span data-ttu-id="9bb36-486">PaymentTrackingInlineResponseQueue</span><span class="sxs-lookup"><span data-stu-id="9bb36-486">PaymentTrackingInlineResponseQueue</span></span>|<span data-ttu-id="9bb36-487">LastPaymentsOutputQueue</span><span class="sxs-lookup"><span data-stu-id="9bb36-487">LastPaymentsOutputQueue</span></span>|<span data-ttu-id="9bb36-488">付款追蹤回應的 MQ 佇列名稱</span><span class="sxs-lookup"><span data-stu-id="9bb36-488">The MQ Queue name for payment tracking responses</span></span>|  
    |<span data-ttu-id="9bb36-489">PaymentTrackingInlineSSOAffiliateApp</span><span class="sxs-lookup"><span data-stu-id="9bb36-489">PaymentTrackingInlineSSOAffiliateApp</span></span>|<span data-ttu-id="9bb36-490">WoodgroveBank.PaymentTracker</span><span class="sxs-lookup"><span data-stu-id="9bb36-490">WoodgroveBank.PaymentTracker</span></span>|<span data-ttu-id="9bb36-491">付款追蹤 SSO 應用程式名稱</span><span class="sxs-lookup"><span data-stu-id="9bb36-491">Payment tracking SSO application name</span></span>|  
    |<span data-ttu-id="9bb36-492">StubSAPWebServiceURL</span><span class="sxs-lookup"><span data-stu-id="9bb36-492">StubSAPWebServiceURL</span></span>|<span data-ttu-id="9bb36-493">http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP/StubSAPWS.asmx</span><span class="sxs-lookup"><span data-stu-id="9bb36-493">http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP/StubSAPWS.asmx</span></span>|<span data-ttu-id="9bb36-494">信用限制 SAP 系統的虛設常式 Web 服務 URL</span><span class="sxs-lookup"><span data-stu-id="9bb36-494">The stub Web service URL of the Credit Limit SAP system</span></span>|  
  
8.  <span data-ttu-id="9bb36-495">在命令提示字元，執行下列命令以設定 PATH 環境：</span><span class="sxs-lookup"><span data-stu-id="9bb36-495">At the command prompt, run the following command to set the PATH environment:</span></span>  
  
    -   `SET PATH=%PATH%;"%CommonProgramFiles%\Enterprise Single Sign-On"`  
  
9. <span data-ttu-id="9bb36-496">在命令提示字元中，執行 CreateInitialConfigInSSO.cmd。</span><span class="sxs-lookup"><span data-stu-id="9bb36-496">At the command prompt, run the CreateInitialConfigInSSO.cmd.</span></span> <span data-ttu-id="9bb36-497">它會建立「SSO 分支機構應用程式」、SSO 組態存放區應用程式，以及分支機構應用程式的使用者對應。</span><span class="sxs-lookup"><span data-stu-id="9bb36-497">It creates the SSO Affiliate Applications, the SSO configuration store application, and the user mappings for the affiliate applications.</span></span> <span data-ttu-id="9bb36-498">然後會執行 SetConfigValuesInSSO.cmd，將組態值儲存在 SSO 組態存放區應用程式中。</span><span class="sxs-lookup"><span data-stu-id="9bb36-498">Then, it executes the SetConfigValuesInSSO.cmd to store configuration values in the SSO configuration store application.</span></span>  
  
10. <span data-ttu-id="9bb36-499">在命令提示字元，執行下列命令以設定擱置交易分支機構應用程式的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="9bb36-499">At the command prompt, run the following command to set the user credential for the Pending Transactions affiliate application.</span></span> <span data-ttu-id="9bb36-500">使用\< **DomainName**> 和\< **UserID**> 針對 PendTransUserMap.xml 中定義\<WindowsDomain >\\<做為 <windowsdomain>\<windowsuserid>\>。</span><span class="sxs-lookup"><span data-stu-id="9bb36-500">Use the \<**DomainName**> and \<**UserID**> defined in the PendTransUserMap.xml for the \<WindowsDomain>\\<WindowsUserId\>.</span></span> <span data-ttu-id="9bb36-501">此命令會要求您輸入用於此逐步解說的外部使用者 (UserID) 的密碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-501">This command asks you to enter the password of the external user, UserID, used in this walkthrough.</span></span>  
  
    -   `ssomanage -setcredentials <WindowsDomain>\<WindowsUserId> WoodgroveBank.PendingTransactions`  
  
11. <span data-ttu-id="9bb36-502">在命令提示字元，執行下列命令以設定付款追蹤器分支機構應用程式的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="9bb36-502">At the command prompt, run the following command to set the user credential for the Payment Tracker affiliate application.</span></span> <span data-ttu-id="9bb36-503">使用\< **DomainName**> 和\< **UserID**> 針對 PmntTrckUserMap.xml 中定義\<WindowsDomain >\\< WindowsUserId\>.</span><span class="sxs-lookup"><span data-stu-id="9bb36-503">Use the \<**DomainName**> and \<**UserID**> defined in the PmntTrckUserMap.xml for the \<WindowsDomain>\\<WindowsUserId\>.</span></span> <span data-ttu-id="9bb36-504">此命令會要求您輸入用於此逐步解說的外部使用者 (PTUserID) 的密碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-504">This command asks you to enter the password of the external user, PTUserID, used in this walkthrough.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-505">付款追蹤器模擬器不會驗證外部使用者認證。</span><span class="sxs-lookup"><span data-stu-id="9bb36-505">The Payment Tracker simulator doesn't validate the external user credential.</span></span> <span data-ttu-id="9bb36-506">您可以為 PTUserID 輸入任何密碼。</span><span class="sxs-lookup"><span data-stu-id="9bb36-506">You can enter any password for the PTUserID.</span></span>  
  
    -   `ssomanage -setcredentials < WindowsDomain >\< WindowsUserId > WoodgroveBank.PaymentTracker`  
  
##  <span data-ttu-id="9bb36-507"><a name="step19"></a>部署服務導向解決方案的 BAM 定義檔案</span><span class="sxs-lookup"><span data-stu-id="9bb36-507"><a name="step19"></a> Deploy the BAM definition file for the Service Oriented Solution</span></span>  
  
#### <a name="to-deploy-the-bam-definition-file-for-the-service-oriented-solution"></a><span data-ttu-id="9bb36-508">部署服務導向解決方案的 BAM 定義檔案</span><span class="sxs-lookup"><span data-stu-id="9bb36-508">To deploy the BAM definition file for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="9bb36-509">開啟命令提示字元，輸入下列命令，然後按 ENTER 以設定尋找 BAM 公用程式的路徑：</span><span class="sxs-lookup"><span data-stu-id="9bb36-509">Open a command prompt, type the following command, and then press ENTER to set the path to find the BAM utilities:</span></span>  
  
    -   <span data-ttu-id="9bb36-510">設定路徑 = %PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤 」</span><span class="sxs-lookup"><span data-stu-id="9bb36-510">SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"</span></span>  
  
2.  <span data-ttu-id="9bb36-511">在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\BAM，輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="9bb36-511">At the command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\BAM, type the following command, and then press ENTER:</span></span>  
  
    -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  
  
##  <span data-ttu-id="9bb36-512"><a name="step21"></a>部署服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9bb36-512"><a name="step21"></a> Deploy the Service Oriented Solution</span></span>  
  
#### <a name="to-edit-the-binding-files-for-the-service-oriented-solution"></a><span data-ttu-id="9bb36-513">編輯服務導向解決方案的繫結檔案</span><span class="sxs-lookup"><span data-stu-id="9bb36-513">To edit the binding files for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="9bb36-514">在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾，使用「記事本」開啟 Deployallbinding.xml，然後進行下列編輯：</span><span class="sxs-lookup"><span data-stu-id="9bb36-514">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, open the Deployallbinding.xml using Notepad, and then make the following edits:</span></span>  
  
    -   <span data-ttu-id="9bb36-515">將 SET MGMT_DB_SERVER 和 MBMT_DB 中的伺服器名稱變更為 BizTalk Server 正在使用的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb36-515">Change the name of the server in the SET MGMT_DB_SERVER and MBMT_DB to the name of the server and database that BizTalk Server is using.</span></span>  
  
    -   <span data-ttu-id="9bb36-516">將 SOLNDIR 變數值變更為 "%BTSSolutionsPath%\SO\BTSSoln"。</span><span class="sxs-lookup"><span data-stu-id="9bb36-516">Change the value of the SOLNDIR variable to "%BTSSolutionsPath%\SO\BTSSoln".</span></span>  
  
2.  <span data-ttu-id="9bb36-517">在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Bindings 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9bb36-517">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Bindings folder.</span></span>  
  
3.  <span data-ttu-id="9bb36-518">對於配接器版本，使用「記事本」開啟 AdapterSOAOrchBindings.xml，然後編輯如下：</span><span class="sxs-lookup"><span data-stu-id="9bb36-518">For the adapter version, open the AdapterSOAOrchBindings.xml using Notepad, and then edit as follows:</span></span>  
  
    -   <span data-ttu-id="9bb36-519">取代所有出現之 __MQ_SERVER_NAME\_ \_ MQSeries Server 名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb36-519">Replace all occurrences of __MQ_SERVER_NAME\_\_ with the MQSeries Server name.</span></span>  
  
    -   <span data-ttu-id="9bb36-520">取代所有出現之 __MQ_QMANAGER_NAME\_ \_與 MQSeries 佇列管理員名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb36-520">Replace all occurrences of __MQ_QMANAGER_NAME\_\_ with the MQSeries Queue Manager name.</span></span>  
  
    -   <span data-ttu-id="9bb36-521">取代所有出現之 __PT_WS_SERVER_NAME\_ \_字串中"\<位址 > https://\__PT_WS_SERVER_NAME\_\_"伺服器名稱與位置暫止的交易部署 web 服務。</span><span class="sxs-lookup"><span data-stu-id="9bb36-521">Replace all occurrences of __PT_WS_SERVER_NAME\_\_ in the string "\<Address>https://\__PT_WS_SERVER_NAME\_\_" with the server name where the Pending Transactions Web service is deployed.</span></span> <span data-ttu-id="9bb36-522">伺服器名稱必須符合**一般名稱**在步驟中，「 將設定為使用 SSL 的 Web 伺服器 」。</span><span class="sxs-lookup"><span data-stu-id="9bb36-522">The server name must match the **common name** in the step, "To configure the Web server for SSL".</span></span> <span data-ttu-id="9bb36-523">不可使用 localhost。</span><span class="sxs-lookup"><span data-stu-id="9bb36-523">You shouldn't use localhost.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-524">繫結檔案 AdapterSOAOrchBindings.xml 會針對下列項目使用虛設常式 Web 服務：</span><span class="sxs-lookup"><span data-stu-id="9bb36-524">The binding file, AdapterSOAOrchBindings.xml, uses the stub Web service for:</span></span>  
    >   
    >  1.  <span data-ttu-id="9bb36-525">「信用限制」後端 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="9bb36-525">The Credit Limit back-end SAP system.</span></span>  
    > 2.  <span data-ttu-id="9bb36-526">MQSeries 配接器與付款追蹤後端系統整合。</span><span class="sxs-lookup"><span data-stu-id="9bb36-526">The MQSeries adapter to integrate with the Payment Tracking back-end system.</span></span>  
    > 3.  <span data-ttu-id="9bb36-527">擱置交易 Web 服務呼叫 HIS TI.NET 元件，將與大型主機後端系統整合。</span><span class="sxs-lookup"><span data-stu-id="9bb36-527">The Pending Transactions Web service to call the HIS TI .NET component to integrate with the mainframe back-end system.</span></span>  
    >   
    >  <span data-ttu-id="9bb36-528">若您未使用大型主機，則必須使用虛設常式 Web 服務以產生擱置交易系統的資料。</span><span class="sxs-lookup"><span data-stu-id="9bb36-528">If you aren’t using the mainframe, you must use the stub Web service to generate data for the Pending Transactions system.</span></span>  
  
4.  <span data-ttu-id="9bb36-529">對於內嵌版本，使用「記事本」開啟 InlineSOAOrchBindings.xml，然後編輯如下：</span><span class="sxs-lookup"><span data-stu-id="9bb36-529">For the inline version, open the InlineSOAOrchBindings.xml using Notepad, and then edit as follows:</span></span>  
  
    -   <span data-ttu-id="9bb36-530">取代所有出現之 __MQ_SERVER_NAME\_ \_ MQSeries Server 名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb36-530">Replace all occurrences of __MQ_SERVER_NAME\_\_ with the MQSeries Server name.</span></span>  
  
    -   <span data-ttu-id="9bb36-531">取代所有出現之 __MQ_QMANAGER_NAME\_ \_與 MQSeries 佇列管理員名稱。</span><span class="sxs-lookup"><span data-stu-id="9bb36-531">Replace all occurrences of __MQ_QMANAGER_NAME\_\_ with the MQSeries Queue Manager name.</span></span>  
  
#### <a name="to-deploy-the-service-oriented-solution"></a><span data-ttu-id="9bb36-532">部署服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9bb36-532">To deploy the Service Oriented solution</span></span>  
  
-   <span data-ttu-id="9bb36-533">在命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾，輸入下列命令，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="9bb36-533">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER.</span></span>  
  
    -   `Deployallbinding.cmd`  
  
    > [!NOTE]
    >  <span data-ttu-id="9bb36-534">Deployallbinding.cmd 建立命名為 BTSScn.SO.CustomerService 的 BizTalk 應用程式，並匯入配接器和內嵌版本的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="9bb36-534">The Deployallbinding.cmd creates the BizTalk application named BTSScn.SO.CustomerService and imports binding files for the adapter and inline versions.</span></span>  
  
##  <span data-ttu-id="9bb36-535"><a name="step23"></a>設定大型主機無法使用時的虛設常式擱置交易 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9bb36-535"><a name="step23"></a> Configure the stub Pending Transactions Web Services when a mainframe is not available</span></span>  
  
#### <a name="to-configure-the-stub-pending-transactions-web-service-for-using-the-adapter-version-without-a-mainframe"></a><span data-ttu-id="9bb36-536">設定虛設常式擱置交易 Web 服務 (以便在大型主機無法使用時使用配接器版本)</span><span class="sxs-lookup"><span data-stu-id="9bb36-536">To configure the stub Pending Transactions Web service (for using the adapter version without a mainframe)</span></span>  
  
1.  <span data-ttu-id="9bb36-537">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下 **虛擬目錄**執行**虛擬目錄建立精靈**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-537">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="9bb36-538">使用**虛擬目錄建立精靈**，建立下列虛擬目錄的虛設常式擱置交易 Web 服務配接器版本：</span><span class="sxs-lookup"><span data-stu-id="9bb36-538">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for stub Pending Transactions Web service for the adapter version:</span></span>  
  
     <span data-ttu-id="9bb36-539">別名 = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span><span class="sxs-lookup"><span data-stu-id="9bb36-539">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span></span>  
  
     <span data-ttu-id="9bb36-540">路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span><span class="sxs-lookup"><span data-stu-id="9bb36-540">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span></span>  
  
     <span data-ttu-id="9bb36-541">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="9bb36-541">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="9bb36-542">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions，按一下 [**屬性**，然後修改設定，如下所示使用**屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9bb36-542">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows using the **Properties** dialog box.</span></span>  
  
    1.  <span data-ttu-id="9bb36-543">在**虛擬目錄**索引標籤上，設定**應用程式集區**至\< *YourAppPool*> 您在 < 若要建立的虛擬目錄的 IIS 中的步驟中，建立解決方案 」。</span><span class="sxs-lookup"><span data-stu-id="9bb36-543">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*> you created in the step, "To create the virtual directories in IIS for the solution".</span></span>  
  
    2.  <span data-ttu-id="9bb36-544">在**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**.</span><span class="sxs-lookup"><span data-stu-id="9bb36-544">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**.</span></span> <span data-ttu-id="9bb36-545">按一下**確定**結束。</span><span class="sxs-lookup"><span data-stu-id="9bb36-545">Click **OK** to exit.</span></span>  
  
3.  <span data-ttu-id="9bb36-546">在**BizTalk Server 管理主控台**，依序展開**BizTalk 群組**，依序展開**應用程式**，依序展開 BTSScn.SO.CustomerService**傳送連接埠**，以滑鼠右鍵按一下**PendingTransactionSolicitResponsePort**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-546">In the **BizTalk Server Administration Console**, expand **BizTalk Group**, expand **Applications**, expand BTSScn.SO.CustomerService, expand **Send Ports**, right-click **PendingTransactionSolicitResponsePort**, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="9bb36-547">在**一般**頁面上，按一下**設定**顯示**傳輸屬性**對話方塊方塊中，然後再修改**Web 服務 URL**至虛設常式擱置交易 Web 服務，例如：</span><span class="sxs-lookup"><span data-stu-id="9bb36-547">In the **General** page, click **Configure** to display the **Transport Properties** dialog box, and then modify the **Web Service URL** to the stub Pending Transaction Web service, for example:</span></span>  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  
  
    2.  <span data-ttu-id="9bb36-548">關閉所有對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9bb36-548">Close all of the dialog boxes.</span></span>  
  
#### <a name="to-configure-the-stub-pending-transactions-web-service-for-using-the-inline-version-without-a-mainframe"></a><span data-ttu-id="9bb36-549">設定虛設常式擱置交易 Web 服務 (以便在大型主機無法使用時使用內嵌版本)</span><span class="sxs-lookup"><span data-stu-id="9bb36-549">To configure the stub Pending Transactions Web service (for using the inline version without a mainframe)</span></span>  
  
1.  <span data-ttu-id="9bb36-550">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，指向**新增**，和然後按一下 **虛擬目錄**執行**虛擬目錄建立精靈**。</span><span class="sxs-lookup"><span data-stu-id="9bb36-550">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="9bb36-551">使用**虛擬目錄建立精靈**，建立下列虛擬目錄的虛設常式擱置交易 Web 服務配接器版本：</span><span class="sxs-lookup"><span data-stu-id="9bb36-551">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for stub Pending Transactions Web service for the adapter version:</span></span>  
  
     <span data-ttu-id="9bb36-552">別名 = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span><span class="sxs-lookup"><span data-stu-id="9bb36-552">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span></span>  
  
     <span data-ttu-id="9bb36-553">路徑 = \< *BizTalk 安裝目錄*> \SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span><span class="sxs-lookup"><span data-stu-id="9bb36-553">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span></span>  
  
     <span data-ttu-id="9bb36-554">存取權限 = 讀取，執行指令碼</span><span class="sxs-lookup"><span data-stu-id="9bb36-554">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="9bb36-555">在**網際網路資訊服務 (IIS) 管理員**，依序展開**網站**，依序展開**Default Web Site**，以滑鼠右鍵按一下Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions，按一下 **屬性**，，然後修改設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9bb36-555">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="9bb36-556">在**虛擬目錄**索引標籤上，設定**應用程式集區**至\< *YourAppPool*> 您在 < 若要建立的虛擬目錄的 IIS 中的步驟中，建立解決方案 」。</span><span class="sxs-lookup"><span data-stu-id="9bb36-556">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*> you created in the step, "To create the virtual directories in IIS for the solution".</span></span>  
  
    2.  <span data-ttu-id="9bb36-557">在**目錄安全性**索引標籤上，按一下 **編輯**中**驗證和存取控制**群組方塊中，然後選取**啟用匿名存取**.</span><span class="sxs-lookup"><span data-stu-id="9bb36-557">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**.</span></span> <span data-ttu-id="9bb36-558">按一下**確定**結束。</span><span class="sxs-lookup"><span data-stu-id="9bb36-558">Click **OK** to exit.</span></span>  
  
3.  <span data-ttu-id="9bb36-559">開啟命令提示字元，然後將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9bb36-559">Open a command prompt, and then change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.</span></span>  
  
4.  <span data-ttu-id="9bb36-560">在命令提示字元中，開啟 SetConfigValuesInSSO.cmd 檔案，使用 [記事本]，然後設定的值**PendingTransactionsInlineURL**的虛設常式擱置交易 Web 服務的 url。</span><span class="sxs-lookup"><span data-stu-id="9bb36-560">At the command prompt, open the SetConfigValuesInSSO.cmd file using Notepad, and then set the value of the **PendingTransactionsInlineURL** to the URL of the stub Pending Transaction Web Service.</span></span>  
  
    -   `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  
  
5.  <span data-ttu-id="9bb36-561">在命令提示字元中輸入 `SetConfigValuesInSSO.cmd`，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="9bb36-561">At the command prompt, type `SetConfigValuesInSSO.cmd`, and then press ENTER.</span></span>  
  
##  <span data-ttu-id="9bb36-562"><a name="step25"></a>啟動服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9bb36-562"><a name="step25"></a> Start the Service Oriented Solution</span></span>  
  
#### <a name="to-start-the-service-oriented-solution"></a><span data-ttu-id="9bb36-563">啟動服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9bb36-563">To start the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="9bb36-564">開啟命令提示字元，將目錄變更為 %BTSSolutionsPath%\SO\BTSSoln\Scripts 資料夾，輸入下列命令，然後按 ENTER 以啟動內嵌和配接器版本的所有協調流程。</span><span class="sxs-lookup"><span data-stu-id="9bb36-564">Open a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER to start all orchestrations for the inline and adapter versions.</span></span>  
  
    -   `startAll.vbs`  
  
2.  <span data-ttu-id="9bb36-565">執行服務導向解決方案。</span><span class="sxs-lookup"><span data-stu-id="9bb36-565">Run the service-oriented solution.</span></span> <span data-ttu-id="9bb36-566">如需執行解決方案的詳細資訊，請參閱[如何執行服務導向解決方案](../core/how-to-run-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-566">For more information about running the solution, see [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9bb36-567">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9bb36-567">Next Steps</span></span>  
 <span data-ttu-id="9bb36-568">測試服務導向解決方案的內嵌和配接器版本[如何執行服務導向解決方案](../core/how-to-run-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="9bb36-568">You test the inline and adapter version of the service-oriented solution in [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb36-569">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bb36-569">See Also</span></span>  
 <span data-ttu-id="9bb36-570">[然後再安裝服務導向解決方案](../core/before-installing-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="9bb36-570">[Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="9bb36-571">[How to Install 虛設常式版本的服務導向解決方案](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="9bb36-571">[How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="9bb36-572">開發人員電腦設定為服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9bb36-572">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)