---
title: 準備您的電腦安裝 |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2016
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53df7a2f-638b-4921-a97f-736760248526
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bba64728220eb2fc5be99153892d68e93eb8e22c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017204"
---
# <a name="prepare-your-computer-for-installation"></a><span data-ttu-id="28de9-102">準備安裝電腦</span><span class="sxs-lookup"><span data-stu-id="28de9-102">Prepare Your Computer for Installation</span></span>
<span data-ttu-id="28de9-103">本主題列出藉由安裝和設定所有必要軟體，然後建立帳戶並設定權限，以便備妥電腦的步驟。</span><span class="sxs-lookup"><span data-stu-id="28de9-103">This topic lists the steps to prepare your computer by installing and configuring all software prerequisites, and then creating accounts and setting permissions.</span></span>  

> [!TIP] 
> <span data-ttu-id="28de9-104">我們的整合 MVP 已準備了一份安裝必要條件與 BizTalk Server 的詳細逐步指南：[BizTalk 2013 Installation and Configuration part 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/)。</span><span class="sxs-lookup"><span data-stu-id="28de9-104">An integration MVP prepared a very detailed step-by-step guide to install the prerequisites, and BizTalk Server:  [BizTalk 2013 Installation and Configuration part 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/).</span></span>  
> 
> <span data-ttu-id="28de9-105">不過，Microsoft 不建議您採取停用使用者帳戶控制 (UAC) 或 Windows 防火牆這類步驟。</span><span class="sxs-lookup"><span data-stu-id="28de9-105">Some steps are not recommended by Microsoft, such as disabling User Access Control (UAC) or Windows Firewall.</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="28de9-106">請依照所列的順序完成這些工作。</span><span class="sxs-lookup"><span data-stu-id="28de9-106">Complete these tasks in the order listed.</span></span>  
  
##  <a name="BKMK_InstUpdates"></a> <span data-ttu-id="28de9-107">安裝 Windows Update</span><span class="sxs-lookup"><span data-stu-id="28de9-107">Install Windows Updates</span></span>  
  
- <span data-ttu-id="28de9-108">**Windows 7**：按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="28de9-108">**Windows 7**: Click Start.</span></span> <span data-ttu-id="28de9-109">在 [搜尋] 文字方塊中，輸入 **Windows Update**。</span><span class="sxs-lookup"><span data-stu-id="28de9-109">In the **Search** text box, type **Windows Update**.</span></span>  
  
- <span data-ttu-id="28de9-110">**Windows 8.1、 Windows Server 2012 和 Windows Server 2012 R2**： 按一下 [Windows] 按鈕上的鍵盤和型別**Windows Update**。</span><span class="sxs-lookup"><span data-stu-id="28de9-110">**Windows 8.1, Windows Server 2012, and Windows Server 2012 R2**: Click the Windows button on the keyboard and type **Windows Update**.</span></span> <span data-ttu-id="28de9-111">按一下搜尋結果中的 **Windows Update**。</span><span class="sxs-lookup"><span data-stu-id="28de9-111">From the search results, click **Windows Update**.</span></span>  
  
  <span data-ttu-id="28de9-112">安裝更新之後，您可能需要重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="28de9-112">After installing updates, you may need to restart the computer.</span></span>  
  
##  <a name="BKMK_IIS"></a> <span data-ttu-id="28de9-113">啟用 Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="28de9-113">Enable Internet Information Services</span></span>  
 <span data-ttu-id="28de9-114">Microsoft Internet Information Services (IIS) 提供許多 BizTalk Server 功能，包括 Web 應用程式基礎結構：</span><span class="sxs-lookup"><span data-stu-id="28de9-114">Microsoft Internet Information Services (IIS) provides a Web application infrastructure for many BizTalk Server features, including:</span></span>  
  
-   <span data-ttu-id="28de9-115">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="28de9-115">HTTP adapter</span></span>  
  
-   <span data-ttu-id="28de9-116">SOAP adapter (SOAP 配接器)</span><span class="sxs-lookup"><span data-stu-id="28de9-116">SOAP adapter</span></span>  
  
-   <span data-ttu-id="28de9-117">Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="28de9-117">Windows SharePoint Services adapter</span></span>  
  
-   <span data-ttu-id="28de9-118">安全通訊端層 (SSL) 加密</span><span class="sxs-lookup"><span data-stu-id="28de9-118">Secure Sockets Layer (SSL) encryption</span></span>  
  
-   <span data-ttu-id="28de9-119">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="28de9-119">BAM Portal</span></span>  
  
#### <a name="install-iis"></a><span data-ttu-id="28de9-120">安裝 IIS</span><span class="sxs-lookup"><span data-stu-id="28de9-120">Install IIS</span></span>

<span data-ttu-id="28de9-121">特定安裝步驟，請參閱：</span><span class="sxs-lookup"><span data-stu-id="28de9-121">For the specific install steps, see:</span></span> 

[<span data-ttu-id="28de9-122">安裝 IIS （Windows 8 和 Windows Server 2012）</span><span class="sxs-lookup"><span data-stu-id="28de9-122">Install IIS (Windows 8 and Windows Server 2012)</span></span>](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012)

[<span data-ttu-id="28de9-123">安裝 IIS （Windows 7 和 Windows Vista）</span><span class="sxs-lookup"><span data-stu-id="28de9-123">Install IIS (Windows 7 and Windows Vista)</span></span>](https://docs.microsoft.com/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7)


<span data-ttu-id="28de9-124">當您安裝 IIS，除了預設已核取選項時，也請檢查下列：</span><span class="sxs-lookup"><span data-stu-id="28de9-124">When you install IIS, in addition to the default checked options, also check the following:</span></span>  
  
- <span data-ttu-id="28de9-125">**Web 管理工具**：另請核取：</span><span class="sxs-lookup"><span data-stu-id="28de9-125">**Web Management Tools**: Also check:</span></span>  
  
    - <span data-ttu-id="28de9-126">IIS 6 管理相容性：</span><span class="sxs-lookup"><span data-stu-id="28de9-126">IIS 6 Management Compatibility:</span></span>  
  
        - <span data-ttu-id="28de9-127">IIS 6 管理主控台</span><span class="sxs-lookup"><span data-stu-id="28de9-127">IIS 6 Management Console</span></span>  
  
        - <span data-ttu-id="28de9-128">IIS Metabase 及 IIS 6 設定相容性</span><span class="sxs-lookup"><span data-stu-id="28de9-128">IIS Metabase and IIS 6 configuration compatibility</span></span>  
  
    - <span data-ttu-id="28de9-129">IIS 管理主控台</span><span class="sxs-lookup"><span data-stu-id="28de9-129">IIS Management Console</span></span>  
  
- <span data-ttu-id="28de9-130">**World Wide Web 服務**：展開 [安全性] 再一併選取：</span><span class="sxs-lookup"><span data-stu-id="28de9-130">**World Wide Web Services**: Expand **Security** and also select:</span></span>  
  
    - <span data-ttu-id="28de9-131">基本驗證</span><span class="sxs-lookup"><span data-stu-id="28de9-131">Basic Authentication</span></span>  
  
    - <span data-ttu-id="28de9-132">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="28de9-132">Windows Authentication</span></span>  

<span data-ttu-id="28de9-133">同時應考慮下列情況：</span><span class="sxs-lookup"><span data-stu-id="28de9-133">Also consider the following:</span></span>  
  
- <span data-ttu-id="28de9-134">**.Net framework 3.5 功能**:.NET Framework 4.5 和.NET Framework 3.5 可用來開發包含 BizTalk 配接器組件的.Net 應用程式。</span><span class="sxs-lookup"><span data-stu-id="28de9-134">**.Net Framework 3.5 Features**: .NET Framework 4.5 and .NET Framework 3.5 can be used to develop .Net applications involving the BizTalk Adapter Pack.</span></span> <span data-ttu-id="28de9-135">通常 **.NET Framework 4.5 功能**已安裝。</span><span class="sxs-lookup"><span data-stu-id="28de9-135">Typically, **.NET Framework 4.5 Features** is already installed.</span></span> <span data-ttu-id="28de9-136">如果您將此電腦上建立應用程式，然後使用.NET Framework 3.5 **.Net Framework 3.5 功能**也可以安裝。</span><span class="sxs-lookup"><span data-stu-id="28de9-136">If you will use .NET Framework 3.5 to create applications on this computer, then **.Net Framework 3.5 Features** can also be installed.</span></span>  
  
- <span data-ttu-id="28de9-137">**訊息佇列**：如果您是使用 MSMQ 配接器，可以核取 [訊息佇列] 以建立本機 MSMQ 存放區。</span><span class="sxs-lookup"><span data-stu-id="28de9-137">**Message Queuing**: If you are using the MSMQ adapter, you can create a local MSMQ store by checking **Message Queuing**.</span></span>  
  
- <span data-ttu-id="28de9-138">**SMTP 伺服器**：如果您是使用 SMTP 配接器，可以核取 [SMTP 伺服器] 以建立本機 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="28de9-138">**SMTP Server**: If you are using the SMTP adapter, you can create a local SMTP Server by checking **SMTP Server**.</span></span>  
  
- <span data-ttu-id="28de9-139">**Windows Identity Foundation 3.5**： 使用 CSOM 安裝選項時 SharePoint 配接器需要 Windows Identity Foundation (WIF)。</span><span class="sxs-lookup"><span data-stu-id="28de9-139">**Windows Identity Foundation 3.5**: Windows Identity Foundation (WIF) is required by the SharePoint adapter when using the CSOM installation option.</span></span> <span data-ttu-id="28de9-140">[附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)描述 SharePoint 配接器的 CSOM 安裝選項。</span><span class="sxs-lookup"><span data-stu-id="28de9-140">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) describes the CSOM installation option for the SharePoint adapter.</span></span>    
  
 
##  <a name="BKMK_XLS"></a> <span data-ttu-id="28de9-141">安裝 Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="28de9-141">Install Microsoft Office Excel</span></span>  
  
1. <span data-ttu-id="28de9-142">執行 Microsoft Office 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="28de9-142">Run the Microsoft Office setup.</span></span>  
  
2. <span data-ttu-id="28de9-143">到達 [安裝類型] 畫面時，請選取 [自訂安裝]，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="28de9-143">When you reach the **Type of Installation** screen, select **Custom Install**, and then select **Next**.</span></span>  
  
3. <span data-ttu-id="28de9-144">在 [自訂安裝] 畫面上，選取 [Excel]，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="28de9-144">On the **Custom Setup** screen, select **Excel**, and then select **Next**.</span></span>  
  
4. <span data-ttu-id="28de9-145">選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="28de9-145">Select **Install**.</span></span>  
  
5. <span data-ttu-id="28de9-146">在 [安裝完成] 中，請選取 [完成]。</span><span class="sxs-lookup"><span data-stu-id="28de9-146">In **Setup Completed**, select **Finish**.</span></span>  
  
   <span data-ttu-id="28de9-147">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-147">**Additional**</span></span>  
  
-   <span data-ttu-id="28de9-148">BizTalk Server 只支援 32 位元版本的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="28de9-148">BizTalk Server supports only 32-bit version of Microsoft Office.</span></span>  
  
-   <span data-ttu-id="28de9-149">Microsoft Office Excel 需要的商務活動監控 (BAM) 在 BizTalk Server 中。</span><span class="sxs-lookup"><span data-stu-id="28de9-149">Microsoft Office Excel is required by Business Activity Monitoring (BAM) in BizTalk Server.</span></span> <span data-ttu-id="28de9-150">BAM Office Excel 活頁簿可定義您想監控的商務程序。</span><span class="sxs-lookup"><span data-stu-id="28de9-150">The BAM Office Excel Workbook defines the business processes you want to monitor.</span></span> <span data-ttu-id="28de9-151">您也可以使用 BAM Excel 活頁簿，來定義商務使用者應透過何種方式來查看 BAM 所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="28de9-151">You also use the BAM Excel Workbook to define the way business users see the data collected by BAM.</span></span>  
  
-   <span data-ttu-id="28de9-152">若要成功將 BAM.xla 載入 Excel，請安裝 [Office 共用功能] 下的 [Visual Basic for Applications]。</span><span class="sxs-lookup"><span data-stu-id="28de9-152">To successfully load BAM.xla into Excel, install **Visual Basic for Applications** under **Office Shared Features**.</span></span> <span data-ttu-id="28de9-153">否則，您可能會接收到「此活頁簿的 VBA 專案、ActiveX 控制項以及其他的程式設計相關功能已遺失」的錯誤。</span><span class="sxs-lookup"><span data-stu-id="28de9-153">Otherwise, you may get error “This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.”</span></span>  
  
##  <a name="BKMK_VS"></a> <span data-ttu-id="28de9-154">安裝 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="28de9-154">Install Visual Studio</span></span>  
  
1. <span data-ttu-id="28de9-155">以系統管理員身分執行 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="28de9-155">Run the Visual Studio setup as Administrator.</span></span>  
  
2. <span data-ttu-id="28de9-156">接受授權合約，然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="28de9-156">Accept the license agreement and click **Next**.</span></span>  
  
3. <span data-ttu-id="28de9-157">在 [要安裝的選擇性功能] 中，選取您需要的選項，然後選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="28de9-157">In **Optional features to install**, select the options you need and then select **Install**.</span></span> <span data-ttu-id="28de9-158">BizTalk Server 不需要任何選用的功能。</span><span class="sxs-lookup"><span data-stu-id="28de9-158">BizTalk Server does not require any of the optional features.</span></span>  
  
4. <span data-ttu-id="28de9-159">在 [完成] 頁面上，關閉視窗，或按一下 [啟動] 以開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="28de9-159">On the **Finish** page, close the window or click **Launch** to open Visual Studio.</span></span>  
  
   <span data-ttu-id="28de9-160">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-160">**Additional**</span></span>  
  
-   <span data-ttu-id="28de9-161">如果您安裝 Visual Studio 安裝 BizTalk Server 之前，再升級至 Visual Studio Team Explorer，您可能需要修復從 BizTalk Server 安裝**控制台中** / **程式**選項。</span><span class="sxs-lookup"><span data-stu-id="28de9-161">If you install Visual Studio before installing BizTalk Server, and then upgrade to Visual Studio Team Explorer, you may need to repair your BizTalk Server installation from the **Control Panel** / **Programs** option.</span></span>  
  
-   <span data-ttu-id="28de9-162">Visual Studio 會自動安裝 BizTalk Server 不使用的 Microsoft SQL Server Express。</span><span class="sxs-lookup"><span data-stu-id="28de9-162">Visual Studio automatically installs Microsoft SQL Server Express; which is not used by BizTalk Server.</span></span> <span data-ttu-id="28de9-163">因此最佳做法是解除安裝 Microsoft SQL Server Express。</span><span class="sxs-lookup"><span data-stu-id="28de9-163">As a best practice, uninstall Microsoft SQL Server Express.</span></span>  
  
-   <span data-ttu-id="28de9-164">BizTalk Server 開發工具是以 Visual Studio 為基礎。</span><span class="sxs-lookup"><span data-stu-id="28de9-164">The BizTalk Server development tools are based on Visual Studio.</span></span> <span data-ttu-id="28de9-165">至少，您必須安裝 Visual Studio 的 Microsoft Visual C#®.NET 元件安裝 BizTalk Server 之前，先**開發人員工具和 SDK**。</span><span class="sxs-lookup"><span data-stu-id="28de9-165">At a minimum, you must install the Microsoft Visual C#® .NET component of Visual Studio before you install the BizTalk Server**Developer Tools and SDK**.</span></span>  
  
-   <span data-ttu-id="28de9-166">Visual studio*不*需要若要安裝 BizTalk Server 的實際執行電腦 （只有執行階段），在任何應用程式開發或偵錯是必要項。</span><span class="sxs-lookup"><span data-stu-id="28de9-166">Visual Studio is *not* required if you are installing BizTalk Server on a production computer (runtime only), on which no application development or debugging is required.</span></span>  
  
-   <span data-ttu-id="28de9-167">BizTalk Server 執行階段需要.NET Framework 4.5。</span><span class="sxs-lookup"><span data-stu-id="28de9-167">The BizTalk Server runtime requires .NET Framework 4.5.</span></span> <span data-ttu-id="28de9-168">如果已安裝 Windows Communication Foundation (WCF) 配接器或 WCF 攔截器，就需要使用 .NET Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="28de9-168">The .NET Framework 3.0 is required if the Windows Communication Foundation (WCF) adapter or WCF Interceptor is installed.</span></span>  
  
##  <a name="BKMK_SQL"></a> <span data-ttu-id="28de9-169">安裝 SQL Server</span><span class="sxs-lookup"><span data-stu-id="28de9-169">Install SQL Server</span></span>  
 <span data-ttu-id="28de9-170">安裝 [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="28de9-170">Install [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)</span></span>  
  
 <span data-ttu-id="28de9-171">安裝 [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="28de9-171">Install [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)</span></span>  
  
 <span data-ttu-id="28de9-172">安裝 [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="28de9-172">Install [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)</span></span>  
  
 <span data-ttu-id="28de9-173">當您安裝 SQL Server 時，請選取下列功能：</span><span class="sxs-lookup"><span data-stu-id="28de9-173">When you install SQL Server, select the following features:</span></span>  
  
- <span data-ttu-id="28de9-174">Database Engine 服務</span><span class="sxs-lookup"><span data-stu-id="28de9-174">Database Engine Services</span></span>  
  
  -   <span data-ttu-id="28de9-175">SQL Server 複寫</span><span class="sxs-lookup"><span data-stu-id="28de9-175">SQL Server Replication</span></span>  
  
  -   <span data-ttu-id="28de9-176">全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="28de9-176">Full-Text Search</span></span>  
  
- <span data-ttu-id="28de9-177">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="28de9-177">Analysis Services</span></span>  
  
- <span data-ttu-id="28de9-178">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="28de9-178">Reporting Services</span></span>  
  
- <span data-ttu-id="28de9-179">共用功能</span><span class="sxs-lookup"><span data-stu-id="28de9-179">Shared Features</span></span>  
  
  -   <span data-ttu-id="28de9-180">SQL Server Data Tools (SQL Server 2014 / SQL Server 2012) 或 Business Intelligence Development Studio (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="28de9-180">SQL Server Data Tools (SQL Server 2014 / SQL Server 2012) or Business Intelligence Development Studio (SQL Server 2008 R2)</span></span>  
  
       [<span data-ttu-id="28de9-181">下載 SQL Server 2014 Data Tools</span><span class="sxs-lookup"><span data-stu-id="28de9-181">Download SQL Server 2014 Data Tools</span></span>](http://www.microsoft.com/download/details.aspx?id=42313)  
  
  -   <span data-ttu-id="28de9-182">用戶端工具連接性</span><span class="sxs-lookup"><span data-stu-id="28de9-182">Client Tools Connectivity</span></span>  
  
  -   <span data-ttu-id="28de9-183">Integration Services</span><span class="sxs-lookup"><span data-stu-id="28de9-183">Integration Services</span></span>  
  
  -   <span data-ttu-id="28de9-184">管理工具 - 基本</span><span class="sxs-lookup"><span data-stu-id="28de9-184">Management Tools - Basic</span></span>  
  
      -   <span data-ttu-id="28de9-185">管理工具 - 完整</span><span class="sxs-lookup"><span data-stu-id="28de9-185">Management Tools - Complete</span></span>  
  
  <span data-ttu-id="28de9-186">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-186">**Additional**</span></span>  
  
- <span data-ttu-id="28de9-187">除了二進位定序之外，BizTalk Server 還支援所有區分大小寫和不區分大小寫的 SQL Server 定序。</span><span class="sxs-lookup"><span data-stu-id="28de9-187">BizTalk Server supports all case-sensitive and case-insensitive SQL Server collations except for binary collations.</span></span> <span data-ttu-id="28de9-188">不支援二進位定序。</span><span class="sxs-lookup"><span data-stu-id="28de9-188">Binary collations are not supported.</span></span>  
  
- <span data-ttu-id="28de9-189">為了達到最佳效能，Microsoft 建議使用 SQL Server Enterprise Edition。</span><span class="sxs-lookup"><span data-stu-id="28de9-189">For optimal performance, Microsoft recommends using the Enterprise Edition of SQL Server.</span></span> <span data-ttu-id="28de9-190">請參閱 [SQL Server 2008 R2 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx)、[SQL Server 2012 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx)或 [SQL Server 2014 版本](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="28de9-190">See [SQL Server 2008 R2 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx), [SQL Server 2012 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx), or [SQL Server 2014 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx).</span></span>  
  
- <span data-ttu-id="28de9-191">系統支援 Service Pack 和 Windows Update，因此皆應安裝。</span><span class="sxs-lookup"><span data-stu-id="28de9-191">Service packs and Windows Updates are supported and should be installed.</span></span>  
  
- <span data-ttu-id="28de9-192">當 BizTalk Server 和 SQL Server 位於不同的電腦上時，分散式交易協調器 (MS DTC) 會處理電腦間交易。</span><span class="sxs-lookup"><span data-stu-id="28de9-192">When BizTalk Server and SQL Server are on separate computers, Distributed Transaction Coordinator (MS DTC) handles the transactions between the computers.</span></span> <span data-ttu-id="28de9-193">SQL Server AlwaysOn 功能不支援 MSDTC 交易。</span><span class="sxs-lookup"><span data-stu-id="28de9-193">The SQL Server AlwaysOn feature does not support MSDTC transactions.</span></span> <span data-ttu-id="28de9-194">不支援將 SQL Server AlwaysOn 功能。</span><span class="sxs-lookup"><span data-stu-id="28de9-194">The SQL Server AlwaysOn feature is not supported.</span></span>  
  
##  <a name="BKMK_MQSeries"></a> <span data-ttu-id="28de9-195">安裝 MQSeries 必要條件</span><span class="sxs-lookup"><span data-stu-id="28de9-195">Install MQSeries Prerequisites</span></span>  
 <span data-ttu-id="28de9-196">**MQSeries 配接器**：在安裝 BizTalk Server 時即會自動安裝。</span><span class="sxs-lookup"><span data-stu-id="28de9-196">**MQSeries adapter**: Automatically installed with the BizTalk Server installation.</span></span>  
  
 <span data-ttu-id="28de9-197">**MQSeries 用戶端 (MQSC) 配接器**：</span><span class="sxs-lookup"><span data-stu-id="28de9-197">**MQSeries Client (MQSC) adapter**:</span></span>  
  
1. <span data-ttu-id="28de9-198">執行 Host Integration Server (HIS) 安裝</span><span class="sxs-lookup"><span data-stu-id="28de9-198">Run the Host Integration Server (HIS) installation</span></span>  
  
2. <span data-ttu-id="28de9-199">在元件安裝中，展開 [BizTalk 配接器]。</span><span class="sxs-lookup"><span data-stu-id="28de9-199">In component installation, expand **BizTalk Adapters**.</span></span>  
  
3. <span data-ttu-id="28de9-200">選取 [BizTalk Adapter for WebSphere MQ (Client-Based) (適用於 WebSphere MQ (以用戶端為基礎) 的 BizTalk 配接器)]。</span><span class="sxs-lookup"><span data-stu-id="28de9-200">Select **BizTalk Adapter for WebSphere MQ (Client-Based)**.</span></span>  
  
   <span data-ttu-id="28de9-201">**支援的 IBM WebSphere MQ 版本**：</span><span class="sxs-lookup"><span data-stu-id="28de9-201">**Supported IBM WebSphere MQ versions**:</span></span>  
  
-   <span data-ttu-id="28de9-202">IBM WebSphere MQ 6.0.2.12 及更新版</span><span class="sxs-lookup"><span data-stu-id="28de9-202">IBM WebSphere MQ 6.0.2.12 and later</span></span>  
  
-   <span data-ttu-id="28de9-203">IBM WebSphere MQ 7.0.1.9 及更新版</span><span class="sxs-lookup"><span data-stu-id="28de9-203">IBM WebSphere MQ 7.0.1.9 and later</span></span>  
  
-   <span data-ttu-id="28de9-204">IBM WebSphere MQ 7.1.0.5 及更新版</span><span class="sxs-lookup"><span data-stu-id="28de9-204">IBM WebSphere MQ 7.1.0.5 and later</span></span>  
  
-   <span data-ttu-id="28de9-205">IBM WebSphere MQ 7.5.0.3 及更新版</span><span class="sxs-lookup"><span data-stu-id="28de9-205">IBM WebSphere MQ 7.5.0.3 and later</span></span>  
  
-   <span data-ttu-id="28de9-206">IBM WebSphere MQ 8 (僅限執行階段；而非系統管理 API)</span><span class="sxs-lookup"><span data-stu-id="28de9-206">IBM WebSphere MQ 8 (limited to runtime; no administration APIs)</span></span>  
  
     <span data-ttu-id="28de9-207">[Host Integration Server CU3](https://support.microsoft.com/kb/3019572) 中包含針對 MQ 第 8 版的支援。</span><span class="sxs-lookup"><span data-stu-id="28de9-207">MQ version 8 support is included with [Host Integration Server CU3](https://support.microsoft.com/kb/3019572).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28de9-208">如果未列出特定的 WebSphere MQ 版本，例如 MQ 5.x，則不支援使用此 BizTalk Server 版本。</span><span class="sxs-lookup"><span data-stu-id="28de9-208">If a specific WebSphere MQ version is not listed, like MQ 5.x, then it is not supported with this BizTalk Server version.</span></span>  
  
 <span data-ttu-id="28de9-209">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-209">**Additional**</span></span>  
  
- <span data-ttu-id="28de9-210">最佳做法是一律安裝最新的 WebSphere MQ Fix Pack。</span><span class="sxs-lookup"><span data-stu-id="28de9-210">As a best practice, always install the latest WebSphere MQ fix pack.</span></span> <span data-ttu-id="28de9-211">請參閱[ http://www.ibm.com/support/docview.wss?uid=swg27006037 ](http://www.ibm.com/support/docview.wss?uid=swg27006037)。</span><span class="sxs-lookup"><span data-stu-id="28de9-211">See [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037).</span></span>  
  
- <span data-ttu-id="28de9-212">如果 IBM WebSphere MQ 是安裝在非 Windows 電腦上，請將 **MQSAgent COM+ 應用程式** (MQSConfigWiz.exe) 和 **MQSeries Server for Windows** 安裝在同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="28de9-212">If IBM WebSphere MQ is installed on a non-Windows computer, install the **MQSAgent COM+ application** (MQSConfigWiz.exe) and **MQSeries Server for Windows** on the same computer.</span></span> <span data-ttu-id="28de9-213">如果 IBM WebSphere MQ 是安裝在 Windows 電腦上，則不需使用 **MQSAgent COM+ 應用程式**和 **MQSeries Server for Windows** 程式。</span><span class="sxs-lookup"><span data-stu-id="28de9-213">If IBM WebSphere MQ is installed on a Windows computer, then the **MQSAgent COM+ application** and **MQSeries Server for Windows** program are not used or needed.</span></span>  
  
   <span data-ttu-id="28de9-214">**MQSConfigWiz.exe**包含在 BizTalk Server 安裝檔案。</span><span class="sxs-lookup"><span data-stu-id="28de9-214">**MQSConfigWiz.exe** is included in the BizTalk Server installation files.</span></span>  
  
   <span data-ttu-id="28de9-215">**MQSeries Server for Windows** 不是 Microsoft 程式，而必須透過 IBM WebSphere MQ 程式取得。</span><span class="sxs-lookup"><span data-stu-id="28de9-215">**MQSeries Server for Windows** is not a Microsoft program and must be obtained with your IBM WebSphere MQ program.</span></span>  
  
- <span data-ttu-id="28de9-216">[MQSeries 配接器](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx)提供 MQSeries 配接器的詳細資訊，包括不同元件的設定。</span><span class="sxs-lookup"><span data-stu-id="28de9-216">[MQSeries Adapter](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx) provides more information on the MQSeries adapter, including configuring the different components.</span></span> <span data-ttu-id="28de9-217">[BizTalk Server: MQSeries and MQSeries Client (MQSC) adapters](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) (BizTalk Server：MQSeries 和 MQSeries 用戶端 (MQSC) 配接器) 提供 MQSeries 和 MQSC 配接器的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="28de9-217">[BizTalk Server: MQSeries and MQSeries Client (MQSC) adapters](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) provides additional details on the MQSeries and MQSC adapters.</span></span>  
  
- <span data-ttu-id="28de9-218">IBM WebSphere 並非 Microsoft 產品，因此 Microsoft 不提供支援服務。</span><span class="sxs-lookup"><span data-stu-id="28de9-218">IBM WebSphere is not a Microsoft product and is not supported by Microsoft.</span></span> <span data-ttu-id="28de9-219">Microsoft 亦不保證此程式的適用性。</span><span class="sxs-lookup"><span data-stu-id="28de9-219">Microsoft makes no guarantees about the suitability of this program.</span></span> <span data-ttu-id="28de9-220">如需 IBM WebSphere MQ 的詳細資訊，包括下載指示，請參閱 www.ibm.com。</span><span class="sxs-lookup"><span data-stu-id="28de9-220">For more information about IBM WebSphere MQ, including download instructions, see www.ibm.com.</span></span>  
  
##  <a name="BKMK_BAMAlerts"></a> <span data-ttu-id="28de9-221">BAM 警示</span><span class="sxs-lookup"><span data-stu-id="28de9-221">BAM Alerts</span></span>  
 <span data-ttu-id="28de9-222">SQL Server 2012 和較新版本的 BAM 警示使用 SQL Server 中的 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="28de9-222">BAM Alerts with SQL Server 2012 and newer versions use Database Mail in SQL Server.</span></span> <span data-ttu-id="28de9-223">使用 SQL Server 2008 R2 和較舊版本的 BAM 警示使用 SQL Notification Services。</span><span class="sxs-lookup"><span data-stu-id="28de9-223">BAM Alerts with SQL Server 2008 R2 and older versions use SQL Notification Services.</span></span> <span data-ttu-id="28de9-224">然後才能安裝或設定 BAM 警示，您必須在 SQL Server 中設定 Notification Services 或 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="28de9-224">Before installing or configuring BAM Alerts, you must configure the Notification Services or Database Mail in SQL Server.</span></span>  
  
###  <a name="BKMK_DBMail"></a> <span data-ttu-id="28de9-225">使用 SQL Server 2012/2014 的 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="28de9-225">BAM Alerts using SQL Server 2012/2014</span></span>  
 <span data-ttu-id="28de9-226">設定 [SQL Server 2012 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="28de9-226">Configure [SQL Server 2012 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx).</span></span>  
  
 <span data-ttu-id="28de9-227">設定 [SQL Server 2014 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="28de9-227">Configure [SQL Server 2014 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx).</span></span>  
  
 <span data-ttu-id="28de9-228">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-228">**Additional**</span></span>  
  
-   <span data-ttu-id="28de9-229">Database Mail 會使用 SMTP 伺服器來傳送 BAM 警示。</span><span class="sxs-lookup"><span data-stu-id="28de9-229">Database Mail uses an SMTP server to send the BAM Alerts.</span></span> <span data-ttu-id="28de9-230">在 BizTalk Server 上或在另一部 IIS 伺服器上，可以在本機安裝 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="28de9-230">SMTP Server can be installed locally on the BizTalk Server or on another IIS server.</span></span> <span data-ttu-id="28de9-231">[附錄 D：建立 SMTP 伺服器](../install-and-config-guides/appendix-d-create-the-smtp-server.md)中有提列安裝及設定 SMTP 伺服器的步驟。</span><span class="sxs-lookup"><span data-stu-id="28de9-231">[Appendix D: Create the SMTP Server](../install-and-config-guides/appendix-d-create-the-smtp-server.md) lists the steps to install and configure a SMTP Server.</span></span>  
  
###  <a name="BKMK_SSNS"></a> <span data-ttu-id="28de9-232">使用 SQL Server 2008 R2 的 BAM 警示 – 安裝 SQL Server 2005 Notification Services</span><span class="sxs-lookup"><span data-stu-id="28de9-232">BAM Alerts using SQL Server 2008 R2 – Install SQL Server 2005 Notification Services</span></span>  
  
1. <span data-ttu-id="28de9-233">請前往 [Microsoft SQL Server 2005 SP4 功能套件](http://go.microsoft.com/fwlink/p/?LinkId=286285)。</span><span class="sxs-lookup"><span data-stu-id="28de9-233">Go to [Feature Pack for Microsoft SQL Server 2005 SP4](http://go.microsoft.com/fwlink/p/?LinkId=286285).</span></span>  
  
2. <span data-ttu-id="28de9-234">針對下列元件，下載並安裝適當的平台套件：</span><span class="sxs-lookup"><span data-stu-id="28de9-234">Download and install the appropriate platform package for the following components:</span></span>  
  
    <span data-ttu-id="28de9-235">**Microsoft SQL Server Native Client**</span><span class="sxs-lookup"><span data-stu-id="28de9-235">**Microsoft SQL Server Native Client**</span></span>  
  
   - <span data-ttu-id="28de9-236">超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi>"X86 封裝 (sqlncli.msi)</span><span class="sxs-lookup"><span data-stu-id="28de9-236">HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi>" X86 Package (sqlncli.msi)</span></span>  
  
   - <span data-ttu-id="28de9-237">超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi>"X64 封裝 (sqlncli_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="28de9-237">HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi>" X64 Package (sqlncli_x64.msi)</span></span>  
  
     <span data-ttu-id="28de9-238">**Microsoft SQL Server 2005 管理物件集合**</span><span class="sxs-lookup"><span data-stu-id="28de9-238">**Microsoft SQL Server 2005 Management Objects Collection**</span></span>  
  
   - <span data-ttu-id="28de9-239">超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi>"X86 封裝 (SQLServer2005_XMO.msi)</span><span class="sxs-lookup"><span data-stu-id="28de9-239">HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi>" X86 Package (SQLServer2005_XMO.msi)</span></span>  
  
   - <span data-ttu-id="28de9-240">超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi>"X64 封裝 (SQLServer2005_XMO_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="28de9-240">HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi>" X64 Package (SQLServer2005_XMO_x64.msi)</span></span>  
  
     <span data-ttu-id="28de9-241">**Microsoft SQL Server 2005 Notification Services 用戶端元件**</span><span class="sxs-lookup"><span data-stu-id="28de9-241">**Microsoft SQL Server 2005 Notification Services Client Components**</span></span>  
  
   - <span data-ttu-id="28de9-242">超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi>"X86 封裝 (SQLServer2005_NS.msi)</span><span class="sxs-lookup"><span data-stu-id="28de9-242">HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi>" X86 Package (SQLServer2005_NS.msi)</span></span>  
  
   - <span data-ttu-id="28de9-243">超連結"<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi>"X64 封裝 (SQLServer2005_NS_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="28de9-243">HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi>" X64 Package (SQLServer2005_NS_x64.msi)</span></span>  
  
   <span data-ttu-id="28de9-244">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-244">**Additional**</span></span>  
  
-   <span data-ttu-id="28de9-245">不需要設定 SQL Notification Services僅安裝在 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="28de9-245">SQL Notification Services does not need to be configured; only installed on the BizTalk Server.</span></span>  
  
##  <a name="BKMK_WIF"></a> <span data-ttu-id="28de9-246">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="28de9-246">Windows Identity Foundation</span></span>  
  
|                                                              |                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="28de9-247">Windows 8.1、 Windows Server 2012 和 Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="28de9-247">Windows 8.1, Windows Server 2012, and Windows Server 2012 R2</span></span> |                                <span data-ttu-id="28de9-248">Windows Identity Foundation 隨附於作業系統的 [開啟或關閉 Windows 功能] 功能之一。</span><span class="sxs-lookup"><span data-stu-id="28de9-248">Windows Identity Foundation is included with the operating system as a Feature in **Turn Windows features on or off**.</span></span>                                |
|                      <span data-ttu-id="28de9-249">Windows Vista SP1</span><span class="sxs-lookup"><span data-stu-id="28de9-249">Windows Vista SP1</span></span>                       | <span data-ttu-id="28de9-250">可下載[Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) HYPERLINK"<http://www.microsoft.com/download/details.aspx?id=17331>」。</span><span class="sxs-lookup"><span data-stu-id="28de9-250">Download available at [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) HYPERLINK "<http://www.microsoft.com/download/details.aspx?id=17331>" .</span></span> |
  
 <span data-ttu-id="28de9-251">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-251">**Additional**</span></span>  
  
-   <span data-ttu-id="28de9-252">SharePoint 配接器，或選取 SharePoint Online 使用與 SharePoint 用戶端端物件模型 (CSOM) 時需要 Windows Identity Foundation (WIF)。</span><span class="sxs-lookup"><span data-stu-id="28de9-252">Windows Identity Foundation (WIF) is required for the SharePoint adapter or SharePoint Online when used with SharePoint Client Side Object Model (CSOM).</span></span> <span data-ttu-id="28de9-253">具體來說：</span><span class="sxs-lookup"><span data-stu-id="28de9-253">Specifically:</span></span>  
  
    |<span data-ttu-id="28de9-254">安裝選項</span><span class="sxs-lookup"><span data-stu-id="28de9-254">Installation Option</span></span>|<span data-ttu-id="28de9-255">WIF 為必要項目</span><span class="sxs-lookup"><span data-stu-id="28de9-255">WIF Required</span></span>|  
    |-------------------------|------------------|  
    |<span data-ttu-id="28de9-256">使用 CSOM SharePoint 配接器</span><span class="sxs-lookup"><span data-stu-id="28de9-256">SharePoint Adapter with CSOM</span></span>|<span data-ttu-id="28de9-257">是</span><span class="sxs-lookup"><span data-stu-id="28de9-257">Yes</span></span>|  
    |<span data-ttu-id="28de9-258">SharePoint Online (含 CSOM)</span><span class="sxs-lookup"><span data-stu-id="28de9-258">SharePoint Online with CSOM</span></span>|<span data-ttu-id="28de9-259">是</span><span class="sxs-lookup"><span data-stu-id="28de9-259">Yes</span></span>|  
    |<span data-ttu-id="28de9-260">SharePoint 配接器 Web 服務 （已過時）</span><span class="sxs-lookup"><span data-stu-id="28de9-260">SharePoint Adapter Web Service (deprecated)</span></span>|<span data-ttu-id="28de9-261">否</span><span class="sxs-lookup"><span data-stu-id="28de9-261">No</span></span>|  
    |<span data-ttu-id="28de9-262">沒有 SharePoint</span><span class="sxs-lookup"><span data-stu-id="28de9-262">No SharePoint</span></span>|<span data-ttu-id="28de9-263">否</span><span class="sxs-lookup"><span data-stu-id="28de9-263">No</span></span>|  
  
-   <span data-ttu-id="28de9-264">[附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)提供 SharePoint 安裝選項的相關特定資訊。</span><span class="sxs-lookup"><span data-stu-id="28de9-264">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) provides specific information on the SharePoint installation options.</span></span>  
  
##  <a name="BKMK_WSS"></a> <span data-ttu-id="28de9-265">安裝及設定 Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="28de9-265">Install and Configure Microsoft SharePoint</span></span>  
 <span data-ttu-id="28de9-266">安裝 [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)</span><span class="sxs-lookup"><span data-stu-id="28de9-266">Install [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)</span></span>  
  
 <span data-ttu-id="28de9-267">安裝 [SharePoint Online 服務](http://technet.microsoft.com/library/jj819267.aspx)</span><span class="sxs-lookup"><span data-stu-id="28de9-267">Install [SharePoint Online Service](http://technet.microsoft.com/library/jj819267.aspx)</span></span>  
  
 <span data-ttu-id="28de9-268">安裝 [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="28de9-268">Install [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)</span></span>  
  
 <span data-ttu-id="28de9-269">安裝 [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)</span><span class="sxs-lookup"><span data-stu-id="28de9-269">Install [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)</span></span>  
  
 <span data-ttu-id="28de9-270">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-270">**Additional**</span></span>  
  
-   <span data-ttu-id="28de9-271">如果您要安裝 SharePoint，您必須這樣再繼續進行其餘的 BizTalk Server 必要條件。</span><span class="sxs-lookup"><span data-stu-id="28de9-271">If you are installing SharePoint, you must do so before continuing with the remaining BizTalk Server prerequisites.</span></span>  
  
-   <span data-ttu-id="28de9-272">安裝和設定 SharePoint 包含下列程序：</span><span class="sxs-lookup"><span data-stu-id="28de9-272">Installing and configuring SharePoint consists of the following procedures:</span></span>  
  
    -   <span data-ttu-id="28de9-273">安裝 SharePoint</span><span class="sxs-lookup"><span data-stu-id="28de9-273">Install SharePoint</span></span>  
  
    -   <span data-ttu-id="28de9-274">設定 SharePoint</span><span class="sxs-lookup"><span data-stu-id="28de9-274">Configure SharePoint</span></span>  
  
    -   <span data-ttu-id="28de9-275">將預設的網站擴充成虛擬伺服器</span><span class="sxs-lookup"><span data-stu-id="28de9-275">Extend the default Web site as a virtual server</span></span>  
  
-   <span data-ttu-id="28de9-276">[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)中有說明 BizTalk Server 適用的 SharePoint 配接器安裝選項。</span><span class="sxs-lookup"><span data-stu-id="28de9-276">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) describes the SharePoint adapter installation options for BizTalk Server.</span></span>  
  
-   <span data-ttu-id="28de9-277">使用 SharePoint 配接器時，建議您安裝新的 CSOM 選項，而不是 SharePoint Web 服務 (如[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)所述)。</span><span class="sxs-lookup"><span data-stu-id="28de9-277">When using the SharePoint adapter, it is recommended to install the new CSOM option instead of the SharePoint Service Web Service; described at [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md).</span></span>  
  
##  <a name="BKMK_SharedMem"></a> <span data-ttu-id="28de9-278">停用共用記憶體通訊協定</span><span class="sxs-lookup"><span data-stu-id="28de9-278">Disable the Shared Memory Protocol</span></span>  
  
1. <span data-ttu-id="28de9-279">開啟 [SQL Server 組態管理員]。</span><span class="sxs-lookup"><span data-stu-id="28de9-279">Open **SQL Server Configuration Manager**.</span></span>  
  
2. <span data-ttu-id="28de9-280">在 [SQL Server 組態管理員] 中，依序展開 [SQL Server 網路組態] 和 [Protocols for MSSQLSERVER (MSSQLSERVER 的通訊協定)]。</span><span class="sxs-lookup"><span data-stu-id="28de9-280">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, and then select **Protocols for MSSQLSERVER**.</span></span>  
  
3. <span data-ttu-id="28de9-281">以滑鼠右鍵按一下 [共用記憶體]，然後選取 [停用]。</span><span class="sxs-lookup"><span data-stu-id="28de9-281">Right-click **Shared Memory**, and then select **Disable**.</span></span>  
  
4. <span data-ttu-id="28de9-282">選取 [SQL Server 服務]，再用滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後選取 [停止]。</span><span class="sxs-lookup"><span data-stu-id="28de9-282">Select **SQL Server Services**, right-click **SQL Server (MSSQLSERVER)**, and then select **Stop**.</span></span> <span data-ttu-id="28de9-283">服務停止之後，再用滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後選取 [啟動]。</span><span class="sxs-lookup"><span data-stu-id="28de9-283">After the service has stopped, right-click **SQL Server (MSSQLSERVER)** again, and then select **Start**.</span></span>  
  
5. <span data-ttu-id="28de9-284">關閉 [SQL Server 組態管理員]。</span><span class="sxs-lookup"><span data-stu-id="28de9-284">Close **SQL Server Configuration Manager**.</span></span>  
  
   <span data-ttu-id="28de9-285">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-285">**Additional**</span></span>  
  
-   <span data-ttu-id="28de9-286">某些壓力狀況下 （例如從在同一部電腦存取 SQL Server 用戶端），SQL Server 共用記憶體通訊協定可能會降低 BizTalk 伺服器的效能。</span><span class="sxs-lookup"><span data-stu-id="28de9-286">Under certain stress conditions (such as clients accessing SQL Server from the same computer), the SQL Server Shared Memory protocol may lower BizTalk Server performance.</span></span> <span data-ttu-id="28de9-287">您可以停用 [SQL Server 網路組態] 中的 [共用記憶體網路通訊協定] 來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="28de9-287">You can resolve this behavior by disabling the Shared Memory network protocol in SQL Server Network Configuration.</span></span>  
  
-   <span data-ttu-id="28de9-288">ReplaceThisText</span><span class="sxs-lookup"><span data-stu-id="28de9-288">ReplaceThisText</span></span>  
  
##  <a name="BKMK_LocalAdmin"></a> <span data-ttu-id="28de9-289">加入本機系統管理員群組</span><span class="sxs-lookup"><span data-stu-id="28de9-289">Join the Local Administrators Group</span></span>  
 <span data-ttu-id="28de9-290">**Windows Server 2012** : [Windows Server 2012： 如何將帳戶新增至本機系統管理員群組](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)</span><span class="sxs-lookup"><span data-stu-id="28de9-290">**Windows Server 2012** : [Windows Server 2012: How to Add an Account to a Local Administrator Group](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)</span></span>  
  
 <span data-ttu-id="28de9-291">**Windows 8.1**：若要開啟 Windows 8 的 [本機使用者和群組]，請按一下鍵盤上的 Windows 鍵，並輸入**群組**。</span><span class="sxs-lookup"><span data-stu-id="28de9-291">**Windows 8.1**: To open Local Users and Groups on Windows 8, click the Windows button on the keyboard and type **groups**.</span></span> <span data-ttu-id="28de9-292">在 [搜尋] 視窗中，按一下 [設定]。</span><span class="sxs-lookup"><span data-stu-id="28de9-292">In the Search window, click **Settings**.</span></span> <span data-ttu-id="28de9-293">在 [結果] 視窗中，按一下 [編輯本機使用者和群組]。</span><span class="sxs-lookup"><span data-stu-id="28de9-293">In the Results window, click **Edit local users and groups**.</span></span> <span data-ttu-id="28de9-294">按一下 [群組]，然後連按兩下 [系統管理員]，以新增帳戶。</span><span class="sxs-lookup"><span data-stu-id="28de9-294">Click **Groups** and then double-click Administrators to add an account.</span></span>  
  
 <span data-ttu-id="28de9-295">**Windows 7 SP1**：按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="28de9-295">**Windows 7 SP1**: Click Start.</span></span> <span data-ttu-id="28de9-296">在 [搜尋] 文字方塊中，輸入**電腦管理**，並按一下以開啟該項目。</span><span class="sxs-lookup"><span data-stu-id="28de9-296">In the **Search** text box, type **Computer Management**, and click it to open.</span></span> <span data-ttu-id="28de9-297">展開 [本機使用者和群組]，按一下 [群組]，然後連按兩下 [系統管理員]，以新增帳戶。</span><span class="sxs-lookup"><span data-stu-id="28de9-297">Expand **Local Users and Groups**, click **Groups**, and then double-click Administrators to add an account.</span></span>  
  
 <span data-ttu-id="28de9-298">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-298">**Additional**</span></span>  
  
-   <span data-ttu-id="28de9-299">您必須是本機 Administrators 群組的成員，才能安裝和設定 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="28de9-299">You must be a member of the local Administrators group to install and configure BizTalk Server.</span></span>  
  
##  <a name="BKMK_AppLog"></a> <span data-ttu-id="28de9-300">設定應用程式事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="28de9-300">Configure the Application Event Log</span></span>  
  
1. <span data-ttu-id="28de9-301">開啟 [事件檢視器]：</span><span class="sxs-lookup"><span data-stu-id="28de9-301">Open **Event Viewer**:</span></span>  
  
    <span data-ttu-id="28de9-302">**Windows Server 2012** ： 按一下 [Windows] 按鈕上的鍵盤和型別**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="28de9-302">**Windows Server 2012** : Click the Windows button on the keyboard and type **Event Viewer**.</span></span> <span data-ttu-id="28de9-303">在 [結果] 視窗中，按一下 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="28de9-303">In the Results window, click **Event Viewer**.</span></span>  
  
    <span data-ttu-id="28de9-304">**Windows 8.1**：在鍵盤上按一下 Windows 鍵，並輸入**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="28de9-304">**Windows 8.1**: Click the Windows button on the keyboard and type **Event Viewer**.</span></span> <span data-ttu-id="28de9-305">在 [搜尋] 視窗中，按一下 [設定]。</span><span class="sxs-lookup"><span data-stu-id="28de9-305">In the Search window, click **Settings**.</span></span> <span data-ttu-id="28de9-306">在 [結果] 視窗中，按一下 [檢視事件記錄檔]。</span><span class="sxs-lookup"><span data-stu-id="28de9-306">In the Results window, click **View event logs**.</span></span>  
  
    <span data-ttu-id="28de9-307">**Windows 7 SP1**：按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="28de9-307">**Windows 7 SP1**: Click Start.</span></span> <span data-ttu-id="28de9-308">在 [搜尋] 文字方塊中，輸入**事件檢視器**，並按一下以開啟該項目。</span><span class="sxs-lookup"><span data-stu-id="28de9-308">In the **Search** text box, type **Event Viewer**, and click it to open.</span></span>  
  
2. <span data-ttu-id="28de9-309">展開 [Windows 記錄]，用滑鼠右鍵按一下 [應用程式]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="28de9-309">Expand **Windows Logs**, right-click **Application**, and then click **Properties**.</span></span> <span data-ttu-id="28de9-310">在 [記錄內容] 中：</span><span class="sxs-lookup"><span data-stu-id="28de9-310">In **Log Properties**:</span></span>  
  
   -   <span data-ttu-id="28de9-311">若要判斷可用空間，請比較 [記錄檔大小] 和 [最大記錄檔大小] 屬性。</span><span class="sxs-lookup"><span data-stu-id="28de9-311">To determine the available space, compare the **Log Size** and the **Maximum log size** properties.</span></span>  
  
   -   <span data-ttu-id="28de9-312">若要提供更多空間，請輸入 [最大記錄檔大小] 中較高的數字。</span><span class="sxs-lookup"><span data-stu-id="28de9-312">To provide more space, enter a higher number in **Maximum log size**.</span></span>  
  
   -   <span data-ttu-id="28de9-313">若要在記錄檔已滿時覆寫舊的事件，請選取 [視需要覆寫事件]。</span><span class="sxs-lookup"><span data-stu-id="28de9-313">To enable overwriting of old events when the log becomes full, select **Overwrite events as needed**.</span></span>  
  
   -   <span data-ttu-id="28de9-314">若要清除記錄檔事件，請選取 [清除記錄檔]。</span><span class="sxs-lookup"><span data-stu-id="28de9-314">To clear the log events, select **Clear log**.</span></span>  
  
3. <span data-ttu-id="28de9-315">按一下 [確定]，關閉 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="28de9-315">Click **OK** to close the **Event Viewer**.</span></span>  
  
   <span data-ttu-id="28de9-316">**其他**</span><span class="sxs-lookup"><span data-stu-id="28de9-316">**Additional**</span></span>  
  
-   <span data-ttu-id="28de9-317">BizTalk Server 安裝程式會將事件記錄保留在應用程式事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="28de9-317">BizTalk Server setup keeps a record of events in the Application Event Log.</span></span> <span data-ttu-id="28de9-318">隨安裝的 BizTalk Server 功能而定，記錄檔需要的空間量可能會超過其限制。</span><span class="sxs-lookup"><span data-stu-id="28de9-318">Depending on the BizTalk Server features installed, the amount of space required in the log may exceed its limit.</span></span> <span data-ttu-id="28de9-319">如果應用程式事件記錄檔會在 BizTalk Server 安裝期間用盡空間，則安裝將會失敗。</span><span class="sxs-lookup"><span data-stu-id="28de9-319">If the application event log runs out of space during BizTalk Server setup, the installation fails.</span></span> <span data-ttu-id="28de9-320">變更應用程式事件記錄檔設定可防止此失敗。</span><span class="sxs-lookup"><span data-stu-id="28de9-320">Changing the Application Event Log settings prevents this failure.</span></span>  
  
## <a name="next"></a><span data-ttu-id="28de9-321">下一個</span><span class="sxs-lookup"><span data-stu-id="28de9-321">Next</span></span>  
 [<span data-ttu-id="28de9-322">選擇 BizTalk Server 功能和元件</span><span class="sxs-lookup"><span data-stu-id="28de9-322">Choose BizTalk Server Features and Components</span></span>](http://msdn.microsoft.com/library/b8c43fcf-9e5c-48ba-830b-13a5177e30f0)  
  
## <a name="see-also"></a><span data-ttu-id="28de9-323">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28de9-323">See Also</span></span>  
 <span data-ttu-id="28de9-324">[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span><span class="sxs-lookup"><span data-stu-id="28de9-324">[Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span></span>  
 <span data-ttu-id="28de9-325">[附錄 A：無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md) </span><span class="sxs-lookup"><span data-stu-id="28de9-325">[Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md) </span></span>  
 <span data-ttu-id="28de9-326">[附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="28de9-326">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) </span></span>  
 <span data-ttu-id="28de9-327">[附錄 C：可轉散發的封包檔](../install-and-config-guides/appendix-c-redistributable-cab-files.md) </span><span class="sxs-lookup"><span data-stu-id="28de9-327">[Appendix C: Redistributable CAB Files](../install-and-config-guides/appendix-c-redistributable-cab-files.md) </span></span>  
 [<span data-ttu-id="28de9-328">附錄 D︰建立 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="28de9-328">Appendix D: Create the SMTP Server</span></span>](../install-and-config-guides/appendix-d-create-the-smtp-server.md)
