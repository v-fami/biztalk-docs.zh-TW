---
title: "準備您的電腦安裝 |Microsoft 文件"
ms.custom: 
ms.date: 2016-03-15
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53df7a2f-638b-4921-a97f-736760248526
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a493c1a0ef38e9be5e229ff82f8773211adfe765
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-your-computer-for-installation"></a><span data-ttu-id="0a31d-102">準備安裝電腦</span><span class="sxs-lookup"><span data-stu-id="0a31d-102">Prepare Your Computer for Installation</span></span>
<span data-ttu-id="0a31d-103">本主題列出藉由安裝和設定所有必要軟體，然後建立帳戶並設定權限，以便備妥電腦的步驟。</span><span class="sxs-lookup"><span data-stu-id="0a31d-103">This topic lists the steps to prepare your computer by installing and configuring all software prerequisites, and then creating accounts and setting permissions.</span></span>  

> [!TIP] 
> <span data-ttu-id="0a31d-104">我們的整合 MVP 已準備了一份安裝必要條件與 BizTalk Server 的詳細逐步指南：[BizTalk 2013 Installation and Configuration part 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/)。</span><span class="sxs-lookup"><span data-stu-id="0a31d-104">An integration MVP prepared a very detailed step-by-step guide to install the prerequisites, and BizTalk Server:  [BizTalk 2013 Installation and Configuration part 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/).</span></span>  
> 
> <span data-ttu-id="0a31d-105">不過，Microsoft 不建議您採取停用使用者帳戶控制 (UAC) 或 Windows 防火牆這類步驟。</span><span class="sxs-lookup"><span data-stu-id="0a31d-105">Some steps are not recommended by Microsoft, such as disabling User Access Control (UAC) or Windows Firewall.</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="0a31d-106">請依照所列的順序完成這些工作。</span><span class="sxs-lookup"><span data-stu-id="0a31d-106">Complete these tasks in the order listed.</span></span>  
  
##  <span data-ttu-id="0a31d-107"><a name="BKMK_InstUpdates"></a> 安裝 Windows Update</span><span class="sxs-lookup"><span data-stu-id="0a31d-107"><a name="BKMK_InstUpdates"></a> Install Windows Updates</span></span>  
  
-   <span data-ttu-id="0a31d-108">**Windows 7**：按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-108">**Windows 7**: Click Start.</span></span> <span data-ttu-id="0a31d-109">在 [搜尋] 文字方塊中，輸入 **Windows Update**。</span><span class="sxs-lookup"><span data-stu-id="0a31d-109">In the **Search** text box, type **Windows Update**.</span></span>  
  
-   <span data-ttu-id="0a31d-110">**Windows 8.1、[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] 和 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2**：按一下鍵盤上的 Windows 鍵，並輸入 **Windows Update**。</span><span class="sxs-lookup"><span data-stu-id="0a31d-110">**Windows 8.1, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], and [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2**: Click the Windows button on the keyboard and type **Windows Update**.</span></span> <span data-ttu-id="0a31d-111">按一下搜尋結果中的 **Windows Update**。</span><span class="sxs-lookup"><span data-stu-id="0a31d-111">From the search results, click **Windows Update**.</span></span>  
  
 <span data-ttu-id="0a31d-112">安裝更新之後，您可能需要重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="0a31d-112">After installing updates, you may need to restart the computer.</span></span>  
  
##  <span data-ttu-id="0a31d-113"><a name="BKMK_IIS"></a> 啟用 Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="0a31d-113"><a name="BKMK_IIS"></a> Enable Internet Information Services</span></span>  
 <span data-ttu-id="0a31d-114">Microsoft Internet Information Services (IIS) 為許多 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 功能提供了 Web 應用程式基礎結構，包括：</span><span class="sxs-lookup"><span data-stu-id="0a31d-114">Microsoft Internet Information Services (IIS) provides a Web application infrastructure for many [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features, including:</span></span>  
  
-   <span data-ttu-id="0a31d-115">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="0a31d-115">HTTP adapter</span></span>  
  
-   <span data-ttu-id="0a31d-116">SOAP adapter (SOAP 配接器)</span><span class="sxs-lookup"><span data-stu-id="0a31d-116">SOAP adapter</span></span>  
  
-   <span data-ttu-id="0a31d-117">Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="0a31d-117">Windows SharePoint Services adapter</span></span>  
  
-   <span data-ttu-id="0a31d-118">安全通訊端層 (SSL) 加密</span><span class="sxs-lookup"><span data-stu-id="0a31d-118">Secure Sockets Layer (SSL) encryption</span></span>  
  
-   <span data-ttu-id="0a31d-119">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="0a31d-119">BAM Portal</span></span>  
  
#### <a name="install-iis-75-on-windows-7-sp1"></a><span data-ttu-id="0a31d-120">在 Windows 7 SP1 上安裝 IIS 7.5</span><span class="sxs-lookup"><span data-stu-id="0a31d-120">Install IIS 7.5 on Windows 7 SP1</span></span>  
  
1.  <span data-ttu-id="0a31d-121">選取 [開始]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-121">Select **Start**.</span></span> <span data-ttu-id="0a31d-122">在 [搜尋] 文字方塊中，輸入**程式和功能**，並加以開啟。</span><span class="sxs-lookup"><span data-stu-id="0a31d-122">In the **Search** text box, type **Programs and Features**, and open it.</span></span>  
  
2.  <span data-ttu-id="0a31d-123">選取 [開啟或關閉 Windows 功能]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-123">Select**Turn Windows features on or off**.</span></span>  
  
3.  <span data-ttu-id="0a31d-124">選取 [Internet Information Services]，然後展開 [Internet Information Services]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-124">Select**Internet Information Services** and expand **Internet Information Services**.</span></span> <span data-ttu-id="0a31d-125">除了預設已核取的選項之外，另請核取下列項目：</span><span class="sxs-lookup"><span data-stu-id="0a31d-125">In addition to the default checked options, also check the following:</span></span>  
  
    -   <span data-ttu-id="0a31d-126">**Web 管理工具**：另請核取：</span><span class="sxs-lookup"><span data-stu-id="0a31d-126">**Web Management Tools**: Also check:</span></span>  
  
        -   <span data-ttu-id="0a31d-127">IIS 6 管理相容性：</span><span class="sxs-lookup"><span data-stu-id="0a31d-127">IIS 6 Management Compatibility:</span></span>  
  
            -   <span data-ttu-id="0a31d-128">IIS 6 管理主控台</span><span class="sxs-lookup"><span data-stu-id="0a31d-128">IIS 6 Management Console</span></span>  
  
            -   <span data-ttu-id="0a31d-129">IIS Metabase 及 IIS 6 設定相容性</span><span class="sxs-lookup"><span data-stu-id="0a31d-129">IIS Metabase and IIS 6 configuration compatibility</span></span>  
  
        -   <span data-ttu-id="0a31d-130">IIS 管理主控台</span><span class="sxs-lookup"><span data-stu-id="0a31d-130">IIS Management Console</span></span>  
  
    -   <span data-ttu-id="0a31d-131">**World Wide Web 服務**：展開 [安全性] 再一併選取：</span><span class="sxs-lookup"><span data-stu-id="0a31d-131">**World Wide Web Services**: Expand **Security** and also select:</span></span>  
  
        -   <span data-ttu-id="0a31d-132">基本驗證</span><span class="sxs-lookup"><span data-stu-id="0a31d-132">Basic Authentication</span></span>  
  
        -   <span data-ttu-id="0a31d-133">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="0a31d-133">Windows Authentication</span></span>  
  
4.  <span data-ttu-id="0a31d-134">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-134">Select **OK**.</span></span> <span data-ttu-id="0a31d-135">完成後，請按一下 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-135">When complete, click **Close**.</span></span>  
  
 <span data-ttu-id="0a31d-136">[http://go.microsoft.com/fwlink/p/?LinkId=257033](http://go.microsoft.com/fwlink/p/?LinkId=257033) 也有列出在 Windows 7 中啟用 IIS 的步驟。</span><span class="sxs-lookup"><span data-stu-id="0a31d-136">[http://go.microsoft.com/fwlink/p/?LinkId=257033](http://go.microsoft.com/fwlink/p/?LinkId=257033) also lists the steps to enable IIS on Windows 7.</span></span>  
  
#### <a name="install-iis-80-on-windows-8"></a><span data-ttu-id="0a31d-137">在 Windows 8 上安裝 IIS 8.0</span><span class="sxs-lookup"><span data-stu-id="0a31d-137">Install IIS 8.0 on Windows 8</span></span>  
  
1.  <span data-ttu-id="0a31d-138">按一下鍵盤上的 Windows 鍵。</span><span class="sxs-lookup"><span data-stu-id="0a31d-138">Select the Windows button on your keyboard.</span></span> <span data-ttu-id="0a31d-139">輸入**程式和功能**，然後選取 [設定]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-139">Type **Programs and Features** and select**Settings**.</span></span> <span data-ttu-id="0a31d-140">在 [結果] 視窗中，選取 [程式和功能]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-140">In the Results window, select **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="0a31d-141">選取 [開啟或關閉 Windows 功能]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-141">Select **Turn Windows features on or off**.</span></span>  
  
3.  <span data-ttu-id="0a31d-142">選取 [Internet Information Services]，然後展開 [Internet Information Services]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-142">Select **Internet Information Services** and expand **Internet Information Services**.</span></span> <span data-ttu-id="0a31d-143">除了預設已核取的選項之外，另請選取下列項目：</span><span class="sxs-lookup"><span data-stu-id="0a31d-143">In addition to the default checked options, also select the following:</span></span>  
  
    -   <span data-ttu-id="0a31d-144">**Web 管理工具**：另請核取：</span><span class="sxs-lookup"><span data-stu-id="0a31d-144">**Web Management Tools**: Also check:</span></span>  
  
        -   <span data-ttu-id="0a31d-145">IIS 6 管理相容性：</span><span class="sxs-lookup"><span data-stu-id="0a31d-145">IIS 6 Management Compatibility:</span></span>  
  
            -   <span data-ttu-id="0a31d-146">IIS 6 管理主控台</span><span class="sxs-lookup"><span data-stu-id="0a31d-146">IIS 6 Management Console</span></span>  
  
            -   <span data-ttu-id="0a31d-147">IIS Metabase 及 IIS 6 設定相容性</span><span class="sxs-lookup"><span data-stu-id="0a31d-147">IIS Metabase and IIS 6 configuration compatibility</span></span>  
  
        -   <span data-ttu-id="0a31d-148">IIS 管理主控台</span><span class="sxs-lookup"><span data-stu-id="0a31d-148">IIS Management Console</span></span>  
  
    -   <span data-ttu-id="0a31d-149">**World Wide Web 服務**：展開 [安全性] 再一併核取：</span><span class="sxs-lookup"><span data-stu-id="0a31d-149">**World Wide Web Services**: Expand **Security** and also check:</span></span>  
  
        -   <span data-ttu-id="0a31d-150">基本驗證</span><span class="sxs-lookup"><span data-stu-id="0a31d-150">Basic Authentication</span></span>  
  
        -   <span data-ttu-id="0a31d-151">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="0a31d-151">Windows Authentication</span></span>  
  
4.  <span data-ttu-id="0a31d-152">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-152">Click **OK**.</span></span> <span data-ttu-id="0a31d-153">完成後，請按一下 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-153">When complete, click **Close**.</span></span>  
  
 <span data-ttu-id="0a31d-154">[http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) 也有列出在 Windows 8 中啟用 IIS 的步驟。</span><span class="sxs-lookup"><span data-stu-id="0a31d-154">[http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) also lists the steps to enable IIS on Windows 8.</span></span>  
  
#### <a name="install-iis-80-on-windows-server-2012"></a><span data-ttu-id="0a31d-155">在 Windows Server 2012 上安裝 IIS 8.0</span><span class="sxs-lookup"><span data-stu-id="0a31d-155">Install IIS 8.0 on Windows Server 2012</span></span>  
  
1.  <span data-ttu-id="0a31d-156">開啟 [伺服器管理員]，然後按一下左窗格的 [儀表板]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-156">Open **Server Manager** and click **Dashboard** in the left pane.</span></span>  
  
2.  <span data-ttu-id="0a31d-157">按一下 [新增角色及功能]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-157">Click **Add roles and features**.</span></span> <span data-ttu-id="0a31d-158">您也可以從右上角的 [管理] 功能表開啟 [新增角色及功能]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-158">**Add Roles and Features** can also be opened from the **Manage** menu in the top right-hand corner.</span></span>  
  
3.  <span data-ttu-id="0a31d-159">按一下 [在您開始前] 視窗中的 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-159">On the **Before You Begin** window, click **Next**.</span></span>  
  
4.  <span data-ttu-id="0a31d-160">在 [安裝類型] 視窗中，按一下 [角色型或功能型安裝]，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-160">On the **Installation Type** window, click **Role-based or feature-based installation**, and click **Next**.</span></span>  
  
5.  <span data-ttu-id="0a31d-161">在 [伺服器選取項目] 視窗中，按一下 [從伺服器集區選取伺服器]，再按一下所需的伺服器，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-161">On the **Server Selection** window, click **Select a server from the server pool**, click the desired server, and click **Next**.</span></span>  
  
     <span data-ttu-id="0a31d-162">[伺服器選取項目] 視窗會列出已使用 [伺服器管理員] 中的 [新增伺服器] 所新增的伺服器 。</span><span class="sxs-lookup"><span data-stu-id="0a31d-162">The **Server Selection** window lists the servers that have been added using **Add Server** in **Server Manager**.</span></span> <span data-ttu-id="0a31d-163">根據預設，它會選取本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="0a31d-163">By default, it selects the local server.</span></span> <span data-ttu-id="0a31d-164">[將伺服器新增到伺服器管理員](http://go.microsoft.com/fwlink/p/?LinkID=241353)一文有列出在 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] 中使用 [新增伺服器] 的步驟。</span><span class="sxs-lookup"><span data-stu-id="0a31d-164">[Add Servers to Server Manager](http://go.microsoft.com/fwlink/p/?LinkID=241353) lists the steps to use **Add Server** on [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)].</span></span>  
  
6.  <span data-ttu-id="0a31d-165">在 [伺服器角色] 視窗中，按一下 [網頁伺服器 (IIS)]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-165">On the **Server Roles** window, click **Web Server (IIS)**.</span></span> <span data-ttu-id="0a31d-166">如果出現提示，請按一下 [新增功能]，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-166">If prompted, click **Add Features**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="0a31d-167">在 [功能] 視窗中，保留預設啟用的選項，並注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="0a31d-167">On the **Features** window, keep the default options enabled and also consider the following:</span></span>  
  
     <span data-ttu-id="0a31d-168">**.Net Framework 3.5 功能**：[!INCLUDE[dotnet45](../includes/dotnet45-md.md)] 和 [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] 可用來開發 [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] 的相關 .Net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0a31d-168">**.Net Framework 3.5 Features**: [!INCLUDE[dotnet45](../includes/dotnet45-md.md)] and [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] can be used to develop .Net applications involving the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="0a31d-169">通常，系統已安裝 **[!INCLUDE[dotnet45](../includes/dotnet45-md.md)] 功能**。</span><span class="sxs-lookup"><span data-stu-id="0a31d-169">Typically, **[!INCLUDE[dotnet45](../includes/dotnet45-md.md)] Features** is already installed.</span></span> <span data-ttu-id="0a31d-170">如果您要使用 [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] 以在這台電腦上建立應用程式，也可以安裝 **.Net Framework 3.5 功能**。</span><span class="sxs-lookup"><span data-stu-id="0a31d-170">If you will use [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] to create applications on this computer, then **.Net Framework 3.5 Features** can also be installed.</span></span>  
  
     <span data-ttu-id="0a31d-171">**訊息佇列**：如果您是使用 MSMQ 配接器，可以核取 [訊息佇列] 以建立本機 MSMQ 存放區。</span><span class="sxs-lookup"><span data-stu-id="0a31d-171">**Message Queuing**: If you are using the MSMQ adapter, you can create a local MSMQ store by checking **Message Queuing**.</span></span>  
  
     <span data-ttu-id="0a31d-172">**SMTP 伺服器**：如果您是使用 SMTP 配接器，可以核取 [SMTP 伺服器] 以建立本機 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0a31d-172">**SMTP Server**: If you are using the SMTP adapter, you can create a local SMTP Server by checking **SMTP Server**.</span></span>  
  
     <span data-ttu-id="0a31d-173">**Windows Identity Foundation 3.5**：使用 CSOM 安裝選項時，必須搭配 Windows Identity Foundation (WIF) 才能使用 [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] 配接器。</span><span class="sxs-lookup"><span data-stu-id="0a31d-173">**Windows Identity Foundation 3.5**: Windows Identity Foundation (WIF) is required by the [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] adapter when using the CSOM installation option.</span></span> <span data-ttu-id="0a31d-174">[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)中有說明 [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] 配接器適用的 CSOM 安裝選項。</span><span class="sxs-lookup"><span data-stu-id="0a31d-174">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) describes the CSOM installation option for the [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] adapter.</span></span>  
  
     <span data-ttu-id="0a31d-175">按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-175">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="0a31d-176">在 [網頁伺服器角色 (IIS)] 視窗中，按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-176">On the **Web Server Role (IIS)** window, click **Next**.</span></span>  
  
9. <span data-ttu-id="0a31d-177">在 [網頁伺服器角色 (IIS)] 下方的 [角色服務] 視窗中，按一下以下選項：</span><span class="sxs-lookup"><span data-stu-id="0a31d-177">On the **Role Services** window (under **Web Server Role (IIS)**), click the following options:</span></span>  
  
     <span data-ttu-id="0a31d-178">**安全性**：除了預設選項，另請按一下：</span><span class="sxs-lookup"><span data-stu-id="0a31d-178">**Security**: In addition to the default options, also click:</span></span>  
  
    -   <span data-ttu-id="0a31d-179">基本驗證</span><span class="sxs-lookup"><span data-stu-id="0a31d-179">Basic Authentication</span></span>  
  
    -   <span data-ttu-id="0a31d-180">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="0a31d-180">Windows Authentication</span></span>  
  
     <span data-ttu-id="0a31d-181">**應用程式開發**：若是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，則預設選項已足夠。</span><span class="sxs-lookup"><span data-stu-id="0a31d-181">**Application Development**: The default options are sufficient for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="0a31d-182">如果您在這台電腦上還主控其他 IIS 應用程式，請核取所需的角色。</span><span class="sxs-lookup"><span data-stu-id="0a31d-182">If you host other IIS-based applications on this computer, check the needed roles.</span></span>  
  
     <span data-ttu-id="0a31d-183">**管理工具**：除了預設選項，另請按一下：</span><span class="sxs-lookup"><span data-stu-id="0a31d-183">**Management Tools**: In addition to the default options, also click:</span></span>  
  
    -   <span data-ttu-id="0a31d-184">IIS 管理主控台</span><span class="sxs-lookup"><span data-stu-id="0a31d-184">IIS Management Console</span></span>  
  
    -   <span data-ttu-id="0a31d-185">IIS 6 管理相容性：</span><span class="sxs-lookup"><span data-stu-id="0a31d-185">IIS 6 Management Compatibility:</span></span>  
  
        -   <span data-ttu-id="0a31d-186">IIS 6 Metabase 相容性</span><span class="sxs-lookup"><span data-stu-id="0a31d-186">IIS 6 Metabase Compatibility</span></span>  
  
        -   <span data-ttu-id="0a31d-187">IIS 6 管理主控台</span><span class="sxs-lookup"><span data-stu-id="0a31d-187">IIS 6 Management Console</span></span>  
  
     <span data-ttu-id="0a31d-188">按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-188">Click **Next**.</span></span>  
  
10. <span data-ttu-id="0a31d-189">在 [確認] 視窗中，按一下 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-189">On the **Confirmation** window, click **Install**.</span></span> <span data-ttu-id="0a31d-190">完成後，請按一下 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-190">When complete, click **Close**.</span></span>  
  
 <span data-ttu-id="0a31d-191">[http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) 也有列出在 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] 中啟用 IIS 的步驟。</span><span class="sxs-lookup"><span data-stu-id="0a31d-191">[http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) also lists the steps to enable IIS on [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)].</span></span>  
  
##  <span data-ttu-id="0a31d-192"><a name="BKMK_XLS"></a> 安裝 Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="0a31d-192"><a name="BKMK_XLS"></a> Install Microsoft Office Excel</span></span>  
  
1.  <span data-ttu-id="0a31d-193">執行 Microsoft Office 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="0a31d-193">Run the Microsoft Office setup.</span></span>  
  
2.  <span data-ttu-id="0a31d-194">到達 [安裝類型] 畫面時，請選取 [自訂安裝]，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-194">When you reach the **Type of Installation** screen, select **Custom Install**, and then select **Next**.</span></span>  
  
3.  <span data-ttu-id="0a31d-195">在 [自訂安裝] 畫面上，選取 [Excel]，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-195">On the **Custom Setup** screen, select **Excel**, and then select **Next**.</span></span>  
  
4.  <span data-ttu-id="0a31d-196">選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-196">Select **Install**.</span></span>  
  
5.  <span data-ttu-id="0a31d-197">在 [安裝完成] 中，請選取 [完成]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-197">In **Setup Completed**, select **Finish**.</span></span>  
  
 <span data-ttu-id="0a31d-198">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-198">**Additional**</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0a31d-199"> 只支援 32 位元版本的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="0a31d-199"> supports only 32-bit version of Microsoft Office.</span></span>  
  
-   <span data-ttu-id="0a31d-200">必須搭配 Microsoft Office Excel，才能使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的商務活動監控 (BAM) 功能。</span><span class="sxs-lookup"><span data-stu-id="0a31d-200">Microsoft Office Excel is required by Business Activity Monitoring (BAM) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="0a31d-201">BAM Office Excel 活頁簿可定義您想監控的商務程序。</span><span class="sxs-lookup"><span data-stu-id="0a31d-201">The BAM Office Excel Workbook defines the business processes you want to monitor.</span></span> <span data-ttu-id="0a31d-202">您也可以使用 BAM Excel 活頁簿，來定義商務使用者應透過何種方式來查看 BAM 所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="0a31d-202">You also use the BAM Excel Workbook to define the way business users see the data collected by BAM.</span></span>  
  
-   <span data-ttu-id="0a31d-203">若要成功將 BAM.xla 載入 Excel，請安裝 [Office 共用功能] 下的 [Visual Basic for Applications]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-203">To successfully load BAM.xla into Excel, install **Visual Basic for Applications** under **Office Shared Features**.</span></span> <span data-ttu-id="0a31d-204">否則，您可能會接收到「此活頁簿的 VBA 專案、ActiveX 控制項以及其他的程式設計相關功能已遺失」的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0a31d-204">Otherwise, you may get error “This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.”</span></span>  
  
##  <span data-ttu-id="0a31d-205"><a name="BKMK_VS"></a> 安裝 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0a31d-205"><a name="BKMK_VS"></a> Install Visual Studio</span></span>  
  
1.  <span data-ttu-id="0a31d-206">以系統管理員身分執行 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="0a31d-206">Run the Visual Studio setup as Administrator.</span></span>  
  
2.  <span data-ttu-id="0a31d-207">接受授權合約，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-207">Accept the license agreement and click **Next**.</span></span>  
  
3.  <span data-ttu-id="0a31d-208">在 [要安裝的選擇性功能] 中，選取您需要的選項，然後選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-208">In **Optional features to install**, select the options you need and then select **Install**.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0a31d-209"> 不需要任何選用的功能。</span><span class="sxs-lookup"><span data-stu-id="0a31d-209"> does not require any of the optional features.</span></span>  
  
4.  <span data-ttu-id="0a31d-210">在 [完成] 頁面上，關閉視窗，或按一下 [啟動] 以開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0a31d-210">On the **Finish** page, close the window or click **Launch** to open Visual Studio.</span></span>  
  
 <span data-ttu-id="0a31d-211">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-211">**Additional**</span></span>  
  
-   <span data-ttu-id="0a31d-212">如果您是先安裝 Visual Studio 之後才安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，接著再升級至 Visual Studio Team Explorer，則可能需要透過 [控制台] / [程式] 選項來修復 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="0a31d-212">If you install Visual Studio before installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then upgrade to Visual Studio Team Explorer, you may need to repair your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation from the **Control Panel** / **Programs** option.</span></span>  
  
-   <span data-ttu-id="0a31d-213">Visual Studio 會自動安裝 Microsoft SQL Server Express，但 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 並不會用到它。</span><span class="sxs-lookup"><span data-stu-id="0a31d-213">Visual Studio automatically installs Microsoft SQL Server Express; which is not used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="0a31d-214">因此最佳做法是解除安裝 Microsoft SQL Server Express。</span><span class="sxs-lookup"><span data-stu-id="0a31d-214">As a best practice, uninstall Microsoft SQL Server Express.</span></span>  
  
-   <span data-ttu-id="0a31d-215">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發工具是以 Visual Studio 為基礎。</span><span class="sxs-lookup"><span data-stu-id="0a31d-215">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development tools are based on Visual Studio.</span></span> <span data-ttu-id="0a31d-216">因此，您至少要先安裝 Visual Studio 的 Microsoft Visual C#® .NET 元件，然後再安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **開發者工具與 SDK**。</span><span class="sxs-lookup"><span data-stu-id="0a31d-216">At a minimum, you must install the Microsoft Visual C#® .NET component of Visual Studio before you install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**Developer Tools and SDK**.</span></span>  
  
-   <span data-ttu-id="0a31d-217">如果您要將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝在不需進行應用程式開發或偵錯的實際執行電腦 (僅限執行階段) 上，Visual Studio 就「不是」必要項目。</span><span class="sxs-lookup"><span data-stu-id="0a31d-217">Visual Studio is *not* required if you are installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a production computer (runtime only), on which no application development or debugging is required.</span></span>  
  
-   <span data-ttu-id="0a31d-218">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段需要 [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-218">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime requires [!INCLUDE[dotnet45](../includes/dotnet45-md.md)].</span></span> <span data-ttu-id="0a31d-219">如果已安裝 Windows Communication Foundation (WCF) 配接器或 WCF 攔截器，就需要使用 .NET Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="0a31d-219">The .NET Framework 3.0 is required if the Windows Communication Foundation (WCF) adapter or WCF Interceptor is installed.</span></span>  
  
##  <span data-ttu-id="0a31d-220"><a name="BKMK_SQL"></a> 安裝 SQL Server</span><span class="sxs-lookup"><span data-stu-id="0a31d-220"><a name="BKMK_SQL"></a> Install SQL Server</span></span>  
 <span data-ttu-id="0a31d-221">安裝 [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0a31d-221">Install [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)</span></span>  
  
 <span data-ttu-id="0a31d-222">安裝 [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0a31d-222">Install [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)</span></span>  
  
 <span data-ttu-id="0a31d-223">安裝 [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0a31d-223">Install [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)</span></span>  
  
 <span data-ttu-id="0a31d-224">當您安裝 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 時，請選取下列功能：</span><span class="sxs-lookup"><span data-stu-id="0a31d-224">When you install [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], select the following features:</span></span>  
  
-   <span data-ttu-id="0a31d-225">Database Engine Services</span><span class="sxs-lookup"><span data-stu-id="0a31d-225">Database Engine Services</span></span>  
  
    -   <span data-ttu-id="0a31d-226">SQL Server 複寫</span><span class="sxs-lookup"><span data-stu-id="0a31d-226">SQL Server Replication</span></span>  
  
    -   <span data-ttu-id="0a31d-227">全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="0a31d-227">Full-Text Search</span></span>  
  
-   <span data-ttu-id="0a31d-228">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="0a31d-228">Analysis Services</span></span>  
  
-   <span data-ttu-id="0a31d-229">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="0a31d-229">Reporting Services</span></span>  
  
-   <span data-ttu-id="0a31d-230">共用功能</span><span class="sxs-lookup"><span data-stu-id="0a31d-230">Shared Features</span></span>  
  
    -   <span data-ttu-id="0a31d-231">SQL Server Data Tools (SQL Server 2014 / SQL Server 2012) 或 Business Intelligence Development Studio (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="0a31d-231">SQL Server Data Tools (SQL Server 2014 / SQL Server 2012) or Business Intelligence Development Studio (SQL Server 2008 R2)</span></span>  
  
         [<span data-ttu-id="0a31d-232">下載 SQL Server 2014 Data Tools</span><span class="sxs-lookup"><span data-stu-id="0a31d-232">Download SQL Server 2014 Data Tools</span></span>](http://www.microsoft.com/download/details.aspx?id=42313)  
  
    -   <span data-ttu-id="0a31d-233">用戶端工具連接性</span><span class="sxs-lookup"><span data-stu-id="0a31d-233">Client Tools Connectivity</span></span>  
  
    -   <span data-ttu-id="0a31d-234">Integration Services</span><span class="sxs-lookup"><span data-stu-id="0a31d-234">Integration Services</span></span>  
  
    -   <span data-ttu-id="0a31d-235">管理工具 - 基本</span><span class="sxs-lookup"><span data-stu-id="0a31d-235">Management Tools - Basic</span></span>  
  
        -   <span data-ttu-id="0a31d-236">管理工具 - 完整</span><span class="sxs-lookup"><span data-stu-id="0a31d-236">Management Tools - Complete</span></span>  
  
 <span data-ttu-id="0a31d-237">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-237">**Additional**</span></span>  
  
-   <span data-ttu-id="0a31d-238">除了二進位定序之外，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援所有區分大小寫及不區分大小寫的 SQL Server 定序。</span><span class="sxs-lookup"><span data-stu-id="0a31d-238">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports all case-sensitive and case-insensitive SQL Server collations except for binary collations.</span></span> <span data-ttu-id="0a31d-239">不支援二進位定序。</span><span class="sxs-lookup"><span data-stu-id="0a31d-239">Binary collations are not supported.</span></span>  
  
-   <span data-ttu-id="0a31d-240">為了達到最佳效能，Microsoft 建議使用 SQL Server Enterprise Edition。</span><span class="sxs-lookup"><span data-stu-id="0a31d-240">For optimal performance, Microsoft recommends using the Enterprise Edition of SQL Server.</span></span> <span data-ttu-id="0a31d-241">請參閱 [SQL Server 2008 R2 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx)、[SQL Server 2012 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx)或 [SQL Server 2014 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="0a31d-241">See [SQL Server 2008 R2 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx), [SQL Server 2012 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx), or [SQL Server 2014 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx).</span></span>  
  
-   <span data-ttu-id="0a31d-242">系統支援 Service Pack 和 Windows Update，因此皆應安裝。</span><span class="sxs-lookup"><span data-stu-id="0a31d-242">Service packs and Windows Updates are supported and should be installed.</span></span>  
  
-   <span data-ttu-id="0a31d-243">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 位於不同的電腦時，分散式交易協調器 (MSDTC) 會處理電腦間的交易。</span><span class="sxs-lookup"><span data-stu-id="0a31d-243">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are on separate computers, Distributed Transaction Coordinator (MS DTC) handles the transactions between the computers.</span></span> <span data-ttu-id="0a31d-244">[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn 功能不支援 MSDTC 交易。</span><span class="sxs-lookup"><span data-stu-id="0a31d-244">The [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn feature does not support MSDTC transactions.</span></span> <span data-ttu-id="0a31d-245">不支援 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn 功能。</span><span class="sxs-lookup"><span data-stu-id="0a31d-245">The [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn feature is not supported.</span></span>  
  
##  <span data-ttu-id="0a31d-246"><a name="BKMK_MQSeries"></a> 安裝 MQSeries 必要條件</span><span class="sxs-lookup"><span data-stu-id="0a31d-246"><a name="BKMK_MQSeries"></a> Install MQSeries Prerequisites</span></span>  
 <span data-ttu-id="0a31d-247">**MQSeries 配接器**：在安裝 BizTalk Server 時即會自動安裝。</span><span class="sxs-lookup"><span data-stu-id="0a31d-247">**MQSeries adapter**: Automatically installed with the BizTalk Server installation.</span></span>  
  
 <span data-ttu-id="0a31d-248">**MQSeries 用戶端 (MQSC) 配接器**：</span><span class="sxs-lookup"><span data-stu-id="0a31d-248">**MQSeries Client (MQSC) adapter**:</span></span>  
  
1.  <span data-ttu-id="0a31d-249">執行 Host Integration Server (HIS) 安裝</span><span class="sxs-lookup"><span data-stu-id="0a31d-249">Run the Host Integration Server (HIS) installation</span></span>  
  
2.  <span data-ttu-id="0a31d-250">在元件安裝中，展開 [BizTalk 配接器]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-250">In component installation, expand **BizTalk Adapters**.</span></span>  
  
3.  <span data-ttu-id="0a31d-251">選取 [BizTalk Adapter for WebSphere MQ (Client-Based) (適用於 WebSphere MQ (以用戶端為基礎) 的 BizTalk 配接器)]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-251">Select **BizTalk Adapter for WebSphere MQ (Client-Based)**.</span></span>  
  
 <span data-ttu-id="0a31d-252">**支援的 IBM WebSphere MQ 版本**：</span><span class="sxs-lookup"><span data-stu-id="0a31d-252">**Supported IBM WebSphere MQ versions**:</span></span>  
  
-   <span data-ttu-id="0a31d-253">IBM WebSphere MQ 6.0.2.12 及更新版</span><span class="sxs-lookup"><span data-stu-id="0a31d-253">IBM WebSphere MQ 6.0.2.12 and later</span></span>  
  
-   <span data-ttu-id="0a31d-254">IBM WebSphere MQ 7.0.1.9 及更新版</span><span class="sxs-lookup"><span data-stu-id="0a31d-254">IBM WebSphere MQ 7.0.1.9 and later</span></span>  
  
-   <span data-ttu-id="0a31d-255">IBM WebSphere MQ 7.1.0.5 及更新版</span><span class="sxs-lookup"><span data-stu-id="0a31d-255">IBM WebSphere MQ 7.1.0.5 and later</span></span>  
  
-   <span data-ttu-id="0a31d-256">IBM WebSphere MQ 7.5.0.3 及更新版</span><span class="sxs-lookup"><span data-stu-id="0a31d-256">IBM WebSphere MQ 7.5.0.3 and later</span></span>  
  
-   <span data-ttu-id="0a31d-257">IBM WebSphere MQ 8 (僅限執行階段；而非系統管理 API)</span><span class="sxs-lookup"><span data-stu-id="0a31d-257">IBM WebSphere MQ 8 (limited to runtime; no administration APIs)</span></span>  
  
     <span data-ttu-id="0a31d-258">[Host Integration Server CU3](https://support.microsoft.com/kb/3019572) 中包含針對 MQ 第 8 版的支援。</span><span class="sxs-lookup"><span data-stu-id="0a31d-258">MQ version 8 support is included with [Host Integration Server CU3](https://support.microsoft.com/kb/3019572).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a31d-259">如果未列出特定的 WebSphere MQ 版本 (例如 MQ 5.x)，表示這個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 版本並不支援。</span><span class="sxs-lookup"><span data-stu-id="0a31d-259">If a specific WebSphere MQ version is not listed, like MQ 5.x, then it is not supported with this [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] version.</span></span>  
  
 <span data-ttu-id="0a31d-260">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-260">**Additional**</span></span>  
  
-   <span data-ttu-id="0a31d-261">最佳做法是一律安裝最新的 WebSphere MQ Fix Pack。</span><span class="sxs-lookup"><span data-stu-id="0a31d-261">As a best practice, always install the latest WebSphere MQ fix pack.</span></span> <span data-ttu-id="0a31d-262">請參閱 [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037)。</span><span class="sxs-lookup"><span data-stu-id="0a31d-262">See [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037).</span></span>  
  
-   <span data-ttu-id="0a31d-263">如果 IBM WebSphere MQ 是安裝在非 Windows 電腦上，請將 **MQSAgent COM+ 應用程式** (MQSConfigWiz.exe) 和 **MQSeries Server for Windows** 安裝在同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="0a31d-263">If IBM WebSphere MQ is installed on a non-Windows computer, install the **MQSAgent COM+ application** (MQSConfigWiz.exe) and **MQSeries Server for Windows** on the same computer.</span></span> <span data-ttu-id="0a31d-264">如果 IBM WebSphere MQ 是安裝在 Windows 電腦上，則不需使用 **MQSAgent COM+ 應用程式**和 **MQSeries Server for Windows** 程式。</span><span class="sxs-lookup"><span data-stu-id="0a31d-264">If IBM WebSphere MQ is installed on a Windows computer, then the **MQSAgent COM+ application** and **MQSeries Server for Windows** program are not used or needed.</span></span>  
  
     <span data-ttu-id="0a31d-265">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝檔案包含 **MQSConfigWiz.exe**。</span><span class="sxs-lookup"><span data-stu-id="0a31d-265">**MQSConfigWiz.exe** is included in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation files.</span></span>  
  
     <span data-ttu-id="0a31d-266">**MQSeries Server for Windows** 不是 Microsoft 程式，而必須透過 IBM WebSphere MQ 程式取得。</span><span class="sxs-lookup"><span data-stu-id="0a31d-266">**MQSeries Server for Windows** is not a Microsoft program and must be obtained with your IBM WebSphere MQ program.</span></span>  
  
-   <span data-ttu-id="0a31d-267">[MQSeries 配接器](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx)提供 MQSeries 配接器的詳細資訊，包括不同元件的設定。</span><span class="sxs-lookup"><span data-stu-id="0a31d-267">[MQSeries Adapter](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx) provides more information on the MQSeries adapter, including configuring the different components.</span></span> <span data-ttu-id="0a31d-268">[BizTalk Server: MQSeries and MQSeries Client (MQSC) adapters](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) (BizTalk Server：MQSeries 和 MQSeries 用戶端 (MQSC) 配接器) 提供 MQSeries 和 MQSC 配接器的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0a31d-268">[BizTalk Server: MQSeries and MQSeries Client (MQSC) adapters](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) provides additional details on the MQSeries and MQSC adapters.</span></span>  
  
-   <span data-ttu-id="0a31d-269">IBM WebSphere 並非 Microsoft 產品，因此 Microsoft 不提供支援服務。</span><span class="sxs-lookup"><span data-stu-id="0a31d-269">IBM WebSphere is not a Microsoft product and is not supported by Microsoft.</span></span> <span data-ttu-id="0a31d-270">Microsoft 亦不保證此程式的適用性。</span><span class="sxs-lookup"><span data-stu-id="0a31d-270">Microsoft makes no guarantees about the suitability of this program.</span></span> <span data-ttu-id="0a31d-271">如需 IBM WebSphere MQ 的詳細資訊，包括下載指示，請參閱 www.ibm.com。</span><span class="sxs-lookup"><span data-stu-id="0a31d-271">For more information about IBM WebSphere MQ, including download instructions, see www.ibm.com.</span></span>  
  
##  <span data-ttu-id="0a31d-272"><a name="BKMK_BAMAlerts"></a> BAM 警示</span><span class="sxs-lookup"><span data-stu-id="0a31d-272"><a name="BKMK_BAMAlerts"></a> BAM Alerts</span></span>  
 <span data-ttu-id="0a31d-273">[!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)] 或 [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] 的 BAM 警示會使用 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="0a31d-273">BAM Alerts with [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)] or [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] uses Database Mail in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="0a31d-274">[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] 的 BAM 警示會使用 SQL Notification Services。</span><span class="sxs-lookup"><span data-stu-id="0a31d-274">BAM Alerts with [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] uses SQL Notification Services.</span></span> <span data-ttu-id="0a31d-275">安裝或設定 BAM 警示之前，您必須先在 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 中設定 Notification Services 或 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="0a31d-275">Before installing or configuring BAM Alerts, you must configure the Notification Services or Database Mail in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
###  <span data-ttu-id="0a31d-276"><a name="BKMK_DBMail"></a> 使用 SQL Server 2012/2014 的 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="0a31d-276"><a name="BKMK_DBMail"></a> BAM Alerts using SQL Server 2012/2014</span></span>  
 <span data-ttu-id="0a31d-277">設定 [SQL Server 2012 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="0a31d-277">Configure [SQL Server 2012 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx).</span></span>  
  
 <span data-ttu-id="0a31d-278">設定 [SQL Server 2014 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="0a31d-278">Configure [SQL Server 2014 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx).</span></span>  
  
 <span data-ttu-id="0a31d-279">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-279">**Additional**</span></span>  
  
-   <span data-ttu-id="0a31d-280">Database Mail 會使用 SMTP 伺服器來傳送 BAM 警示。</span><span class="sxs-lookup"><span data-stu-id="0a31d-280">Database Mail uses an SMTP server to send the BAM Alerts.</span></span> <span data-ttu-id="0a31d-281">您可以將 SMTP 伺服器本機安裝在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或另一部 IIS 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="0a31d-281">SMTP Server can be installed locally on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or on another IIS server.</span></span> <span data-ttu-id="0a31d-282">[附錄 D：建立 SMTP 伺服器](../install-and-config-guides/appendix-d-create-the-smtp-server.md)中有提列安裝及設定 SMTP 伺服器的步驟。</span><span class="sxs-lookup"><span data-stu-id="0a31d-282">[Appendix D: Create the SMTP Server](../install-and-config-guides/appendix-d-create-the-smtp-server.md) lists the steps to install and configure a SMTP Server.</span></span>  
  
###  <span data-ttu-id="0a31d-283"><a name="BKMK_SSNS"></a> 使用 SQL Server 2008 R2 的 BAM 警示 – 安裝 SQL Server 2005 Notification Services</span><span class="sxs-lookup"><span data-stu-id="0a31d-283"><a name="BKMK_SSNS"></a> BAM Alerts using SQL Server 2008 R2 – Install SQL Server 2005 Notification Services</span></span>  
  
1.  <span data-ttu-id="0a31d-284">請前往 [Microsoft SQL Server 2005 SP4 功能套件](http://go.microsoft.com/fwlink/p/?LinkId=286285)。</span><span class="sxs-lookup"><span data-stu-id="0a31d-284">Go to [Feature Pack for Microsoft SQL Server 2005 SP4](http://go.microsoft.com/fwlink/p/?LinkId=286285).</span></span>  
  
2.  <span data-ttu-id="0a31d-285">針對下列元件，下載並安裝適當的平台套件：</span><span class="sxs-lookup"><span data-stu-id="0a31d-285">Download and install the appropriate platform package for the following components:</span></span>  
  
     <span data-ttu-id="0a31d-286">**Microsoft SQL Server Native Client**</span><span class="sxs-lookup"><span data-stu-id="0a31d-286">**Microsoft SQL Server Native Client**</span></span>  
  
    -   <span data-ttu-id="0a31d-287">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi" X86 套件 (sqlncli.msi)</span><span class="sxs-lookup"><span data-stu-id="0a31d-287">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi" X86 Package (sqlncli.msi)</span></span>  
  
    -   <span data-ttu-id="0a31d-288">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi" X64 套件 (sqlncli_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="0a31d-288">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi" X64 Package (sqlncli_x64.msi)</span></span>  
  
     <span data-ttu-id="0a31d-289">**Microsoft SQL Server 2005 管理物件集合**</span><span class="sxs-lookup"><span data-stu-id="0a31d-289">**Microsoft SQL Server 2005 Management Objects Collection**</span></span>  
  
    -   <span data-ttu-id="0a31d-290">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi" X86 套件 (SQLServer2005_XMO.msi)</span><span class="sxs-lookup"><span data-stu-id="0a31d-290">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi" X86 Package (SQLServer2005_XMO.msi)</span></span>  
  
    -   <span data-ttu-id="0a31d-291">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi" X64 套件 (SQLServer2005_XMO_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="0a31d-291">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi" X64 Package (SQLServer2005_XMO_x64.msi)</span></span>  
  
     <span data-ttu-id="0a31d-292">**Microsoft SQL Server 2005 Notification Services 用戶端元件**</span><span class="sxs-lookup"><span data-stu-id="0a31d-292">**Microsoft SQL Server 2005 Notification Services Client Components**</span></span>  
  
    -   <span data-ttu-id="0a31d-293">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi" X86 套件 (SQLServer2005_NS.msi)</span><span class="sxs-lookup"><span data-stu-id="0a31d-293">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi" X86 Package (SQLServer2005_NS.msi)</span></span>  
  
    -   <span data-ttu-id="0a31d-294">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi" X64 套件 (SQLServer2005_NS_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="0a31d-294">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi" X64 Package (SQLServer2005_NS_x64.msi)</span></span>  
  
 <span data-ttu-id="0a31d-295">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-295">**Additional**</span></span>  
  
-   <span data-ttu-id="0a31d-296">您不需要設定 SQL Notification Services；只要將其安裝在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中即可。</span><span class="sxs-lookup"><span data-stu-id="0a31d-296">SQL Notification Services does not need to be configured; only installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
##  <span data-ttu-id="0a31d-297"><a name="BKMK_WIF"></a> Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="0a31d-297"><a name="BKMK_WIF"></a> Windows Identity Foundation</span></span>  
  
|||  
|-|-|  
|[!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]<span data-ttu-id="0a31d-298"> 8.1、[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] 和 [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2</span><span class="sxs-lookup"><span data-stu-id="0a31d-298"> 8.1, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], and [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2</span></span>|<span data-ttu-id="0a31d-299">Windows Identity Foundation 是隨附於作業系統的 [開啟或關閉 Windows 功能] 功能之一。</span><span class="sxs-lookup"><span data-stu-id="0a31d-299">Windows Identity Foundation is included with the operating system as a Feature in **Turn Windows features on or off**.</span></span>|  
|[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)]<span data-ttu-id="0a31d-300"> SP1</span><span class="sxs-lookup"><span data-stu-id="0a31d-300"> SP1</span></span>|<span data-ttu-id="0a31d-301">您可前往 [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) HYPERLINK "http://www.microsoft.com/download/details.aspx?id=17331" 進行下載。</span><span class="sxs-lookup"><span data-stu-id="0a31d-301">Download available at [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) HYPERLINK "http://www.microsoft.com/download/details.aspx?id=17331" .</span></span>|  
  
 <span data-ttu-id="0a31d-302">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-302">**Additional**</span></span>  
  
-   <span data-ttu-id="0a31d-303">[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 配接器或 SharePoint Online 在與 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM) 搭配使用時需要 Windows Identity Foundation (WIF)。</span><span class="sxs-lookup"><span data-stu-id="0a31d-303">Windows Identity Foundation (WIF) is required for the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] adapter or SharePoint Online when used with [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM).</span></span> <span data-ttu-id="0a31d-304">具體來說：</span><span class="sxs-lookup"><span data-stu-id="0a31d-304">Specifically:</span></span>  
  
    |<span data-ttu-id="0a31d-305">安裝選項</span><span class="sxs-lookup"><span data-stu-id="0a31d-305">Installation Option</span></span>|<span data-ttu-id="0a31d-306">WIF 為必要項目</span><span class="sxs-lookup"><span data-stu-id="0a31d-306">WIF Required</span></span>|  
    |-------------------------|------------------|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]<span data-ttu-id="0a31d-307"> 配接器 (含 CSOM)</span><span class="sxs-lookup"><span data-stu-id="0a31d-307"> Adapter with CSOM</span></span>|<span data-ttu-id="0a31d-308">是</span><span class="sxs-lookup"><span data-stu-id="0a31d-308">Yes</span></span>|  
    |<span data-ttu-id="0a31d-309">SharePoint Online (含 CSOM)</span><span class="sxs-lookup"><span data-stu-id="0a31d-309">SharePoint Online with CSOM</span></span>|<span data-ttu-id="0a31d-310">是</span><span class="sxs-lookup"><span data-stu-id="0a31d-310">Yes</span></span>|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]<span data-ttu-id="0a31d-311"> 配接器 Web 服務 (已被取代)</span><span class="sxs-lookup"><span data-stu-id="0a31d-311"> Adapter Web Service (deprecated)</span></span>|<span data-ttu-id="0a31d-312">否</span><span class="sxs-lookup"><span data-stu-id="0a31d-312">No</span></span>|  
    |<span data-ttu-id="0a31d-313">沒有 SharePoint</span><span class="sxs-lookup"><span data-stu-id="0a31d-313">No SharePoint</span></span>|<span data-ttu-id="0a31d-314">否</span><span class="sxs-lookup"><span data-stu-id="0a31d-314">No</span></span>|  
  
-   <span data-ttu-id="0a31d-315">[附錄 B︰安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)提供有關 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 安裝選項的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="0a31d-315">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) provides specific information on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] installation options.</span></span>  
  
##  <span data-ttu-id="0a31d-316"><a name="BKMK_WSS"></a> 安裝及設定 Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="0a31d-316"><a name="BKMK_WSS"></a> Install and Configure Microsoft SharePoint</span></span>  
 <span data-ttu-id="0a31d-317">安裝 [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)</span><span class="sxs-lookup"><span data-stu-id="0a31d-317">Install [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)</span></span>  
  
 <span data-ttu-id="0a31d-318">安裝 [SharePoint Online 服務](http://technet.microsoft.com/library/jj819267.aspx)</span><span class="sxs-lookup"><span data-stu-id="0a31d-318">Install [SharePoint Online Service](http://technet.microsoft.com/library/jj819267.aspx)</span></span>  
  
 <span data-ttu-id="0a31d-319">安裝 [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0a31d-319">Install [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)</span></span>  
  
 <span data-ttu-id="0a31d-320">安裝 [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0a31d-320">Install [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)</span></span>  
  
 <span data-ttu-id="0a31d-321">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-321">**Additional**</span></span>  
  
-   <span data-ttu-id="0a31d-322">如果您要安裝 SharePoint，就必須先安裝好 SharePoint，再繼續進行其餘 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必要條件。</span><span class="sxs-lookup"><span data-stu-id="0a31d-322">If you are installing SharePoint, you must do so before continuing with the remaining [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prerequisites.</span></span>  
  
-   <span data-ttu-id="0a31d-323">安裝和設定 SharePoint 包含下列程序：</span><span class="sxs-lookup"><span data-stu-id="0a31d-323">Installing and configuring SharePoint consists of the following procedures:</span></span>  
  
    -   <span data-ttu-id="0a31d-324">安裝 SharePoint</span><span class="sxs-lookup"><span data-stu-id="0a31d-324">Install SharePoint</span></span>  
  
    -   <span data-ttu-id="0a31d-325">設定 SharePoint</span><span class="sxs-lookup"><span data-stu-id="0a31d-325">Configure SharePoint</span></span>  
  
    -   <span data-ttu-id="0a31d-326">將預設的網站擴充成虛擬伺服器</span><span class="sxs-lookup"><span data-stu-id="0a31d-326">Extend the default Web site as a virtual server</span></span>  
  
-   <span data-ttu-id="0a31d-327">[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)中有說明 BizTalk Server 適用的 SharePoint 配接器安裝選項。</span><span class="sxs-lookup"><span data-stu-id="0a31d-327">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) describes the SharePoint adapter installation options for BizTalk Server.</span></span>  
  
-   <span data-ttu-id="0a31d-328">使用 SharePoint 配接器時，建議您安裝新的 CSOM 選項，而不是 SharePoint Web 服務 (如[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)所述)。</span><span class="sxs-lookup"><span data-stu-id="0a31d-328">When using the SharePoint adapter, it is recommended to install the new CSOM option instead of the SharePoint Service Web Service; described at [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md).</span></span>  
  
##  <span data-ttu-id="0a31d-329"><a name="BKMK_SharedMem"></a> 停用共用記憶體通訊協定</span><span class="sxs-lookup"><span data-stu-id="0a31d-329"><a name="BKMK_SharedMem"></a> Disable the Shared Memory Protocol</span></span>  
  
1.  <span data-ttu-id="0a31d-330">開啟 [SQL Server 組態管理員]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-330">Open **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="0a31d-331">在 [SQL Server 組態管理員] 中，依序展開 [SQL Server 網路組態] 和 [Protocols for MSSQLSERVER (MSSQLSERVER 的通訊協定)]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-331">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, and then select **Protocols for MSSQLSERVER**.</span></span>  
  
3.  <span data-ttu-id="0a31d-332">以滑鼠右鍵按一下 [共用記憶體]，然後選取 [停用]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-332">Right-click **Shared Memory**, and then select **Disable**.</span></span>  
  
4.  <span data-ttu-id="0a31d-333">選取 [SQL Server 服務]，再用滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後選取 [停止]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-333">Select **SQL Server Services**, right-click **SQL Server (MSSQLSERVER)**, and then select **Stop**.</span></span> <span data-ttu-id="0a31d-334">服務停止之後，再用滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後選取 [啟動]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-334">After the service has stopped, right-click **SQL Server (MSSQLSERVER)** again, and then select **Start**.</span></span>  
  
5.  <span data-ttu-id="0a31d-335">關閉 [SQL Server 組態管理員]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-335">Close **SQL Server Configuration Manager**.</span></span>  
  
 <span data-ttu-id="0a31d-336">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-336">**Additional**</span></span>  
  
-   <span data-ttu-id="0a31d-337">在特定負荷條件下 (例如用戶端從相同的電腦存取 SQL Server)，SQL Server 共用記憶體通訊協定可能會降低 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的效能。</span><span class="sxs-lookup"><span data-stu-id="0a31d-337">Under certain stress conditions (such as clients accessing SQL Server from the same computer), the SQL Server Shared Memory protocol may lower [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance.</span></span> <span data-ttu-id="0a31d-338">您可以停用 [SQL Server 網路組態] 中的 [共用記憶體網路通訊協定] 來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="0a31d-338">You can resolve this behavior by disabling the Shared Memory network protocol in SQL Server Network Configuration.</span></span>  
  
-   <span data-ttu-id="0a31d-339">ReplaceThisText</span><span class="sxs-lookup"><span data-stu-id="0a31d-339">ReplaceThisText</span></span>  
  
##  <span data-ttu-id="0a31d-340"><a name="BKMK_LocalAdmin"></a> 加入本機系統管理員群組</span><span class="sxs-lookup"><span data-stu-id="0a31d-340"><a name="BKMK_LocalAdmin"></a> Join the Local Administrators Group</span></span>  
 <span data-ttu-id="0a31d-341">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]**：[Windows Server 2012: How to Add an Account to a Local Administrator Group](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx) (Windows Server 2012：如何將帳戶新增至本機系統管理員群組)</span><span class="sxs-lookup"><span data-stu-id="0a31d-341">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : [Windows Server 2012: How to Add an Account to a Local Administrator Group](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)</span></span>  
  
 <span data-ttu-id="0a31d-342">**Windows 8.1**：若要開啟 Windows 8 的 [本機使用者和群組]，請按一下鍵盤上的 Windows 鍵，並輸入**群組**。</span><span class="sxs-lookup"><span data-stu-id="0a31d-342">**Windows 8.1**: To open Local Users and Groups on Windows 8, click the Windows button on the keyboard and type **groups**.</span></span> <span data-ttu-id="0a31d-343">在 [搜尋] 視窗中，按一下 [設定]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-343">In the Search window, click **Settings**.</span></span> <span data-ttu-id="0a31d-344">在 [結果] 視窗中，按一下 [編輯本機使用者和群組]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-344">In the Results window, click **Edit local users and groups**.</span></span> <span data-ttu-id="0a31d-345">按一下 [群組]，然後連按兩下 [系統管理員]，以新增帳戶。</span><span class="sxs-lookup"><span data-stu-id="0a31d-345">Click **Groups** and then double-click Administrators to add an account.</span></span>  
  
 <span data-ttu-id="0a31d-346">**Windows 7 SP1**：按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-346">**Windows 7 SP1**: Click Start.</span></span> <span data-ttu-id="0a31d-347">在 [搜尋] 文字方塊中，輸入**電腦管理**，並按一下以開啟該項目。</span><span class="sxs-lookup"><span data-stu-id="0a31d-347">In the **Search** text box, type **Computer Management**, and click it to open.</span></span> <span data-ttu-id="0a31d-348">展開 [本機使用者和群組]，按一下 [群組]，然後連按兩下 [系統管理員]，以新增帳戶。</span><span class="sxs-lookup"><span data-stu-id="0a31d-348">Expand **Local Users and Groups**, click **Groups**, and then double-click Administrators to add an account.</span></span>  
  
 <span data-ttu-id="0a31d-349">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-349">**Additional**</span></span>  
  
-   <span data-ttu-id="0a31d-350">您必須是本機系統管理員群組的成員才能安裝和設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-350">You must be a member of the local Administrators group to install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
##  <span data-ttu-id="0a31d-351"><a name="BKMK_AppLog"></a> 設定應用程式事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="0a31d-351"><a name="BKMK_AppLog"></a> Configure the Application Event Log</span></span>  
  
1.  <span data-ttu-id="0a31d-352">開啟 [事件檢視器]：</span><span class="sxs-lookup"><span data-stu-id="0a31d-352">Open **Event Viewer**:</span></span>  
  
     <span data-ttu-id="0a31d-353">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]**：在鍵盤上按一下 Windows 鍵，並輸入**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="0a31d-353">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Click the Windows button on the keyboard and type **Event Viewer**.</span></span> <span data-ttu-id="0a31d-354">在 [結果] 視窗中，按一下 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-354">In the Results window, click **Event Viewer**.</span></span>  
  
     <span data-ttu-id="0a31d-355">**Windows 8.1**：在鍵盤上按一下 Windows 鍵，並輸入**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="0a31d-355">**Windows 8.1**: Click the Windows button on the keyboard and type **Event Viewer**.</span></span> <span data-ttu-id="0a31d-356">在 [搜尋] 視窗中，按一下 [設定]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-356">In the Search window, click **Settings**.</span></span> <span data-ttu-id="0a31d-357">在 [結果] 視窗中，按一下 [檢視事件記錄檔]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-357">In the Results window, click **View event logs**.</span></span>  
  
     <span data-ttu-id="0a31d-358">**Windows 7 SP1**：按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-358">**Windows 7 SP1**: Click Start.</span></span> <span data-ttu-id="0a31d-359">在 [搜尋] 文字方塊中，輸入**事件檢視器**，並按一下以開啟該項目。</span><span class="sxs-lookup"><span data-stu-id="0a31d-359">In the **Search** text box, type **Event Viewer**, and click it to open.</span></span>  
  
2.  <span data-ttu-id="0a31d-360">展開 [Windows 記錄]，用滑鼠右鍵按一下 [應用程式]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-360">Expand **Windows Logs**, right-click **Application**, and then click **Properties**.</span></span> <span data-ttu-id="0a31d-361">在 [記錄內容] 中：</span><span class="sxs-lookup"><span data-stu-id="0a31d-361">In **Log Properties**:</span></span>  
  
    -   <span data-ttu-id="0a31d-362">若要判斷可用空間，請比較 [記錄檔大小] 和 [最大記錄檔大小] 屬性。</span><span class="sxs-lookup"><span data-stu-id="0a31d-362">To determine the available space, compare the **Log Size** and the **Maximum log size** properties.</span></span>  
  
    -   <span data-ttu-id="0a31d-363">若要提供更多空間，請輸入 [最大記錄檔大小] 中較高的數字。</span><span class="sxs-lookup"><span data-stu-id="0a31d-363">To provide more space, enter a higher number in **Maximum log size**.</span></span>  
  
    -   <span data-ttu-id="0a31d-364">若要在記錄檔已滿時覆寫舊的事件，請選取 [視需要覆寫事件]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-364">To enable overwriting of old events when the log becomes full, select **Overwrite events as needed**.</span></span>  
  
    -   <span data-ttu-id="0a31d-365">若要清除記錄檔事件，請選取 [清除記錄檔]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-365">To clear the log events, select **Clear log**.</span></span>  
  
3.  <span data-ttu-id="0a31d-366">按一下 [確定]，關閉 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="0a31d-366">Click **OK** to close the **Event Viewer**.</span></span>  
  
 <span data-ttu-id="0a31d-367">**其他**</span><span class="sxs-lookup"><span data-stu-id="0a31d-367">**Additional**</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0a31d-368"> 安裝程式會將事件的記錄存放在應用程式事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="0a31d-368"> setup keeps a record of events in the Application Event Log.</span></span> <span data-ttu-id="0a31d-369">應用程式記錄檔所需的空間量會根據安裝期間所安裝的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 功能而不同。</span><span class="sxs-lookup"><span data-stu-id="0a31d-369">Depending on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features installed, the amount of space required in the log may exceed its limit.</span></span> <span data-ttu-id="0a31d-370">如果應用程式事件記錄檔在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝期間用盡空間，安裝就會失敗。</span><span class="sxs-lookup"><span data-stu-id="0a31d-370">If the application event log runs out of space during [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup, the installation fails.</span></span> <span data-ttu-id="0a31d-371">若要防止此錯誤，您可以變更應用程式事件記錄檔的設定。</span><span class="sxs-lookup"><span data-stu-id="0a31d-371">Changing the Application Event Log settings prevents this failure.</span></span>  
  
## <a name="next"></a><span data-ttu-id="0a31d-372">下一個</span><span class="sxs-lookup"><span data-stu-id="0a31d-372">Next</span></span>  
 [<span data-ttu-id="0a31d-373">選擇 BizTalk Server 功能和元件</span><span class="sxs-lookup"><span data-stu-id="0a31d-373">Choose BizTalk Server Features and Components</span></span>](http://msdn.microsoft.com/library/b8c43fcf-9e5c-48ba-830b-13a5177e30f0)  
  
## <a name="see-also"></a><span data-ttu-id="0a31d-374">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a31d-374">See Also</span></span>  
 <span data-ttu-id="0a31d-375">[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span><span class="sxs-lookup"><span data-stu-id="0a31d-375">[Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span></span>  
 <span data-ttu-id="0a31d-376">[附錄 A：無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md) </span><span class="sxs-lookup"><span data-stu-id="0a31d-376">[Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md) </span></span>  
 <span data-ttu-id="0a31d-377">[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="0a31d-377">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) </span></span>  
 <span data-ttu-id="0a31d-378">[附錄 C：可轉散發的封包檔](../install-and-config-guides/appendix-c-redistributable-cab-files.md) </span><span class="sxs-lookup"><span data-stu-id="0a31d-378">[Appendix C: Redistributable CAB Files](../install-and-config-guides/appendix-c-redistributable-cab-files.md) </span></span>  
 [<span data-ttu-id="0a31d-379">附錄 D︰建立 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="0a31d-379">Appendix D: Create the SMTP Server</span></span>](../install-and-config-guides/appendix-d-create-the-smtp-server.md)
