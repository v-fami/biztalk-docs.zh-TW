---
title: "安裝和設定 Microsoft BizTalk ESB Toolkit |Microsoft 文件"
description: "安裝和設定 BizTalk Server 上的 ESB Toolkit 的步驟-步驟指示"
caps.latest.revision: "8"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 698843f7-8361-4d02-9278-0e66f2a9f472
ms.author: mandia
ms.openlocfilehash: 33805fe58298e4f4729161a62742d3b204996b00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="install-and-configure-the-microsoft-biztalk-esb-toolkit"></a><span data-ttu-id="0b031-103">安裝和設定 Microsoft BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="0b031-103">Install and configure the Microsoft BizTalk ESB Toolkit</span></span>
<span data-ttu-id="0b031-104">從 BizTalk Server 2013 和較新版本，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]與整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝程式。</span><span class="sxs-lookup"><span data-stu-id="0b031-104">Starting with BizTalk Server 2013 and newer versions, [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is integrated with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup.</span></span> <span data-ttu-id="0b031-105">本主題說明如何安裝及設定[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，而且也包含社群寫入升級 ESB Toolkit 連結。</span><span class="sxs-lookup"><span data-stu-id="0b031-105">This topic shows you how to install and configure [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], and also includes a community-written link to upgrade the ESB Toolkit.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b031-106">您必須先安裝 BizTalk Server，才能開始安裝 [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b031-106">You must have BizTalk Server installed before you start installing the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].</span></span>  
  
## <a name="install"></a><span data-ttu-id="0b031-107">Install</span><span class="sxs-lookup"><span data-stu-id="0b031-107">Install</span></span> 
  
1.  <span data-ttu-id="0b031-108">執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以系統管理員身分的 setup.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="0b031-108">Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup.exe file as Administrator.</span></span> <span data-ttu-id="0b031-109">在 [安裝] 選取**安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]** 。</span><span class="sxs-lookup"><span data-stu-id="0b031-109">In setup, select **Install [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**.</span></span>  
  
2.  <span data-ttu-id="0b031-110">接受授權合約，然後再選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0b031-110">Accept the license agreement, and then select **Next**.</span></span>  
  
3.  <span data-ttu-id="0b031-111">在 [元件安裝] 中，選取您想要安裝的元件，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0b031-111">In **Component Installation**, select the components you want to install, and then select **Next**.</span></span>  
  
4.  <span data-ttu-id="0b031-112">在**摘要**，檢閱 功能選擇，，然後選取**安裝**。</span><span class="sxs-lookup"><span data-stu-id="0b031-112">In the **Summary**, review what you chose, and then select **Install**.</span></span>  
  
5.  <span data-ttu-id="0b031-113">選取 [完成] 以關閉安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="0b031-113">Select **Finish** to close the installation wizard.</span></span>  

<span data-ttu-id="0b031-114">安裝記錄檔會建立，類似於 ' C:\Users\yourUserName\AppData\Local\Temp\Setup(081017 175042).htm'。</span><span class="sxs-lookup"><span data-stu-id="0b031-114">An install log file is created, similar to \`C:\Users\yourUserName\AppData\Local\Temp\Setup(081017 175042).htm'.</span></span> 
  
## <a name="configure"></a><span data-ttu-id="0b031-115">設定</span><span class="sxs-lookup"><span data-stu-id="0b031-115">Configure</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="0b031-116">您必須先設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之後，才能設定 [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b031-116">You must configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] before configuring [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].</span></span>  
  
1.  <span data-ttu-id="0b031-117">從**啟動**功能表上，選取**Microsoft [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]** ，然後選取**ESB 組態工具**。</span><span class="sxs-lookup"><span data-stu-id="0b031-117">From the **Start** menu, select **Microsoft [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**, and then select **ESB Configuration Tool**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0b031-118">系統管理員身分執行 ESB 組態工具。</span><span class="sxs-lookup"><span data-stu-id="0b031-118">Run the ESB Configuration Tool as an administrator.</span></span>  
  
2.  <span data-ttu-id="0b031-119">在組態中，選取**資料庫伺服器**。</span><span class="sxs-lookup"><span data-stu-id="0b031-119">In the configuration, select **Database Server**.</span></span> <span data-ttu-id="0b031-120">輸入主控資料庫伺服器名稱[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="0b031-120">Enter the database server name that hosts the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] databases.</span></span>   
  
3.  <span data-ttu-id="0b031-121">在**IIS Web 服務**，輸入使用者帳戶和執行的 IIS 應用程式所建立的密碼[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b031-121">In **IIS Web Services**, enter the user account and password that runs the IIS applications created by the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].</span></span> <span data-ttu-id="0b031-122">接下來，輸入裝載應用程式的 IIS 網站。</span><span class="sxs-lookup"><span data-stu-id="0b031-122">Next, enter the IIS website that hosts the applications.</span></span>  
  
4.  <span data-ttu-id="0b031-123">**BizTalk 使用者群組**列出預設的使用者群組通常用於 ESB 組態。</span><span class="sxs-lookup"><span data-stu-id="0b031-123">The **BizTalk User Groups** lists the default user groups typically used for ESB configuration.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0b031-124">在這個階段，您可以選取**套用組態**設定[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]使用這些預設設定。</span><span class="sxs-lookup"><span data-stu-id="0b031-124">At this stage, you can select **Apply Configuration** to configure the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] with these default settings.</span></span> <span data-ttu-id="0b031-125">不過，如果您想要自訂的組態，完成其餘步驟。</span><span class="sxs-lookup"><span data-stu-id="0b031-125">However, if you want to do a custom configuration, complete the remaining steps.</span></span> <span data-ttu-id="0b031-126">以您在下一個步驟中輸入的值優先於預設值。</span><span class="sxs-lookup"><span data-stu-id="0b031-126">Rhe values you enter in the next steps take precedence over the default values.</span></span>  
  
5.  <span data-ttu-id="0b031-127">在左窗格中，依序展開**ESB 組態**，依序展開 * * 例外狀況管理 * *，然後：</span><span class="sxs-lookup"><span data-stu-id="0b031-127">In the left pane, expand **ESB Configuration**, expand ** Exception Management**, and then:</span></span>  
  
    -   <span data-ttu-id="0b031-128">如果您不想設定例外狀況的管理資料庫，然後選取**資料庫**，並取消核取**啟用例外狀況管理資料庫**。</span><span class="sxs-lookup"><span data-stu-id="0b031-128">If you don't want to configure an exception management database, then select **Database**, and uncheck the **Enable Exception Management Database**.</span></span>
  
    -   <span data-ttu-id="0b031-129">如果您想要使用現有的資料庫，而不是建立新的資料庫，然後選取 **資料庫**，然後選取**使用現有的資料庫**。</span><span class="sxs-lookup"><span data-stu-id="0b031-129">If you want to use an existing database instead of creating a new database, then select **Database**, and select the **Use Existing Database**.</span></span> <span data-ttu-id="0b031-130">輸入資料庫伺服器名稱和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="0b031-130">Enter the database server name and the database name.</span></span>  
  
    -   <span data-ttu-id="0b031-131">如果您不想設定例外狀況的 web 服務，然後選取**例外狀況的 Web 服務**，並取消核取**啟用例外狀況 Services**。</span><span class="sxs-lookup"><span data-stu-id="0b031-131">If you don't want to configure exception web service, then select **Exception Web Services**, and uncheck **Enable Exception Services**.</span></span>  <span data-ttu-id="0b031-132">如果您想要執行這些服務在不同的網站，您可以在此處輸入。</span><span class="sxs-lookup"><span data-stu-id="0b031-132">If you want to run these services under a different website, you can enter that here.</span></span>  
  
6.  <span data-ttu-id="0b031-133">在左窗格中，依序展開**ESB 核心元件**，然後：</span><span class="sxs-lookup"><span data-stu-id="0b031-133">In the left pane, expand **ESB Core Components**, and then:</span></span>  
  
    -   <span data-ttu-id="0b031-134">如果您不想設定路線的資料庫，然後選取**路線資料庫**，並取消核取**路線資料庫**。</span><span class="sxs-lookup"><span data-stu-id="0b031-134">If you don't want to configure an itinerary database, then select **Itinerary Database**, and uncheck **Itinerary Database** .</span></span>  
  
    -   <span data-ttu-id="0b031-135">如果您想要使用現有的路線資料庫，然後選取**路線資料庫**，然後選取**使用現有的資料庫**。</span><span class="sxs-lookup"><span data-stu-id="0b031-135">If you want to use an existing itinerary database, then select **Itinerary Database**, and select **Use Existing Database**.</span></span> <span data-ttu-id="0b031-136">輸入資料庫伺服器名稱和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="0b031-136">Enter the database server name and the database name.</span></span>  
  
    -   <span data-ttu-id="0b031-137">如果您不想要設定這些 web 服務，然後選取**核心 Web 服務**，並取消核取**啟用核心服務**。</span><span class="sxs-lookup"><span data-stu-id="0b031-137">If you don't want to configure these web service, then select **Core Web Services**, and uncheck **Enable Core Services**.</span></span> <span data-ttu-id="0b031-138">如果您想要執行這些服務在不同的網站，您可以在此處輸入。</span><span class="sxs-lookup"><span data-stu-id="0b031-138">If you want to run these services under a different website, you can enter that here.</span></span>
  
7.  <span data-ttu-id="0b031-139">在左窗格中，選取**組態**。</span><span class="sxs-lookup"><span data-stu-id="0b031-139">In the left pane, select **Configuration**.</span></span>  
    <span data-ttu-id="0b031-140">如果您安裝與設定[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]在單一伺服器環境中，選取**檔案組態來源**。</span><span class="sxs-lookup"><span data-stu-id="0b031-140">If you are installing and configuring the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] in a single server environment, select **File Configuration Source**.</span></span> <span data-ttu-id="0b031-141">如果您要設定多電腦部署，請選取**SSO 組態來源**，然後輸入下列：</span><span class="sxs-lookup"><span data-stu-id="0b031-141">If you are setting up a multiple-machine deployment, select the **SSO Configuration Source**, and then enter the following:</span></span>  
  
    -   <span data-ttu-id="0b031-142">**SSO 伺服器**： 輸入 SSO 伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="0b031-142">**SSO Server**: Enter the name of the SSO server</span></span>
  
    -   <span data-ttu-id="0b031-143">**組態檔**： 選取省略符號**（...）**，然後瀏覽至 esb.config 檔案 (\Program Files (x86) \Microsoft BizTalk ESB Toolkit)</span><span class="sxs-lookup"><span data-stu-id="0b031-143">**Configuration file**: Select the ellipsis **(…)**, and then browse to the esb.config file (\Program Files (x86)\Microsoft BizTalk ESB Toolkit)</span></span>
  
    -   <span data-ttu-id="0b031-144">**應用程式名稱**： 輸入 SSO 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="0b031-144">**Application Name**: Enter a name for the SSO application.</span></span> <span data-ttu-id="0b031-145">例如，輸入`ESB Toolkit`。</span><span class="sxs-lookup"><span data-stu-id="0b031-145">For example,  enter `ESB Toolkit`.</span></span>  
  
    -   <span data-ttu-id="0b031-146">**連絡資訊**： 以下列格式輸入有效的電子郵件地址的適當的連絡資訊： `someone@example.com`。</span><span class="sxs-lookup"><span data-stu-id="0b031-146">**Contact Information**: Enter a valid email address the appropriate contact information in the following format: `someone@example.com`.</span></span>  
  
    -   <span data-ttu-id="0b031-147">**系統管理員群組名稱**： 選取省略符號**（...）**，然後瀏覽至適當的系統管理員群組</span><span class="sxs-lookup"><span data-stu-id="0b031-147">**Administrator Group Name**: Select the ellipsis **(…)**, and then browse to the appropriate admin group</span></span>  
  
    -   <span data-ttu-id="0b031-148">**使用者群組名稱**： 選取省略符號**（...）**，然後瀏覽至適當的群組</span><span class="sxs-lookup"><span data-stu-id="0b031-148">**User Group Name**: Select the ellipsis **(…)**, and then browse to the appropriate group</span></span>  

8.  <span data-ttu-id="0b031-149">選取**套用組態**。</span><span class="sxs-lookup"><span data-stu-id="0b031-149">Select **Apply Configuration**.</span></span> <span data-ttu-id="0b031-150">開啟 IIS，您會發現在設定 [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] 時指定的網站下方，現已建立 [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] 所需的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b031-150">Open IIS and notice that the applications required for [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] are now created under the website you specified while configuring [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].</span></span>  
  
9. <span data-ttu-id="0b031-151">在**ESB 組態工具**，選取**ESB BizTalk 應用程式**，然後：</span><span class="sxs-lookup"><span data-stu-id="0b031-151">In the **ESB Configuration Tool**, select **ESB BizTalk Applications**, and then:</span></span>  
  
    -   <span data-ttu-id="0b031-152">選取**BizTalk Server 中啟用 ESB 核心元件**建立應用程式中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0b031-152">Select **Enable ESB Core Components in BizTalk Server** to create the application in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="0b031-153">選取**使用預設繫結**預設主控件到這個應用程式繫結。</span><span class="sxs-lookup"><span data-stu-id="0b031-153">Select **Use Default Binding** to bind this application to the default host.</span></span> <span data-ttu-id="0b031-154">選取**不使用預設繫結**如果您不想要繫結至預設主控件應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b031-154">Select **Do not use Default Binding** if you do not want to bind the application to the default host.</span></span> <span data-ttu-id="0b031-155">在此案例中，您必須明確繫結至主機應用程式建立應用程式之後。</span><span class="sxs-lookup"><span data-stu-id="0b031-155">In this scenario, you must explicitly bind the application to a host once the application is created.</span></span>  
  
    -   <span data-ttu-id="0b031-156">選取**BizTalk Server 中啟用 ESB JMS/WMQ 元件**建立應用程式中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0b031-156">Select **Enable ESB JMS/WMQ Components in BizTalk Server** to create the application in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="0b031-157">選取**使用預設繫結**預設主控件到這個應用程式繫結。</span><span class="sxs-lookup"><span data-stu-id="0b031-157">Select **Use Default Binding** to bind this application to the default host.</span></span> <span data-ttu-id="0b031-158">選取**不使用預設繫結**如果您不想要繫結至預設主控件應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b031-158">Select **Do not use Default Binding** if you do not want to bind the application to the default host.</span></span> <span data-ttu-id="0b031-159">在此案例中，您必須明確繫結至主機應用程式建立應用程式之後。</span><span class="sxs-lookup"><span data-stu-id="0b031-159">In this scenario, you must explicitly bind the application to a host once the application is created.</span></span>  
  
    -   <span data-ttu-id="0b031-160">選取**套用組態**建立您所選取的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b031-160">Select **Apply Configuration** to create the applications you selected.</span></span> <span data-ttu-id="0b031-161">確認應用程式已在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中建立。</span><span class="sxs-lookup"><span data-stu-id="0b031-161">Verify that the applications are created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="upgrade-esb-toolkit--community-addition"></a><span data-ttu-id="0b031-162">升級 ESB Toolkit – 社群補充</span><span class="sxs-lookup"><span data-stu-id="0b031-162">Upgrade ESB Toolkit – Community Addition</span></span>  
 <span data-ttu-id="0b031-163">[In-place upgrade of ESB Toolkit 2.1 to 2.2](http://www.brianloesgen.com/blog/2013/10/10/in-place-upgrade-of-esb-toolkit-21-to-22.html) (http://www.brianloesgen.com/blog/2013/10/10/in-place-upgrade-of-esb-toolkit-21-to-22.html)</span><span class="sxs-lookup"><span data-stu-id="0b031-163">[In-place upgrade of ESB Toolkit 2.1 to 2.2](http://www.brianloesgen.com/blog/2013/10/10/in-place-upgrade-of-esb-toolkit-21-to-22.html) (http://www.brianloesgen.com/blog/2013/10/10/in-place-upgrade-of-esb-toolkit-21-to-22.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="0b031-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b031-164">See also</span></span>
[<span data-ttu-id="0b031-165">疑難排解安裝問題，以及一般錯誤和解析度</span><span class="sxs-lookup"><span data-stu-id="0b031-165">Troubleshoot installation issues, and common errors & resolutions</span></span>](troubleshooting-the-biztalk-esb-toolkit.md)