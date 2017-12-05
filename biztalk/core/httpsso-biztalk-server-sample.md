---
title: "HTTPSSO （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- SSO, examples
- SSO, HTTP adapters
- examples, HTTP adapters
- HTTP adapters, SSO
- examples, SSO
ms.assetid: 322360df-81d2-4a73-9512-bda9382351a2
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41956d9e10cba87e0e1a1f44d49dd8ec8b6039bc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="httpsso-biztalk-server-sample"></a><span data-ttu-id="bef6e-102">HTTPSSO （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="bef6e-102">HTTPSSO (BizTalk Server Sample)</span></span>
<span data-ttu-id="bef6e-103">HTTPSSO 範例將示範如何搭配 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 配接器使用「企業單一登入」(SSO) 功能。</span><span class="sxs-lookup"><span data-stu-id="bef6e-103">The HTTPSSO sample demonstrates how to use the Enterprise Single Sign-On (SSO) feature with the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bef6e-104">64 位元作業系統不支援這個範例。</span><span class="sxs-lookup"><span data-stu-id="bef6e-104">This sample is not supported on 64-bit operating systems.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="bef6e-105">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="bef6e-105">What This Sample Does</span></span>  
 <span data-ttu-id="bef6e-106">這個範例會示範使用 SSO 和 BizTalk HTTP 傳送和接收配接器模擬 SSO 如何允許使用者不需提供額外認證以登入非 Microsoft Windows 系統之後通過 Windows 驗證的端對端案例。</span><span class="sxs-lookup"><span data-stu-id="bef6e-106">This sample demonstrates an end-to-end scenario that uses SSO and the BizTalk HTTP Send and Receive adapters to simulate how SSO allows a user to avoid supplying additional credentials to log on to non-Microsoft Windows systems after Windows authenticates them.</span></span>  
  
 <span data-ttu-id="bef6e-107">此範例還會使用 SSO 管理和對應模組，建立使用 SSO 之 interop 用戶端 DLL 的分支機構應用程式和 SSO 對應。</span><span class="sxs-lookup"><span data-stu-id="bef6e-107">The sample also uses the administration and mapping modules of SSO to create affiliate application and SSO mappings using the interop client DLL of SSO.</span></span>  
  
 <span data-ttu-id="bef6e-108">此範例將示範透過實作下列各方面的端對端實例使用 SSO：</span><span class="sxs-lookup"><span data-stu-id="bef6e-108">The sample demonstrates the use of SSO by implementing the following aspects of an end-to-end scenario:</span></span>  
  
-   <span data-ttu-id="bef6e-109">表示 Microsoft 網際網路資訊服務 (IIS) 虛擬目錄設定為使用 Windows 整合式的驗證的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="bef6e-109">User interface, represented by a Microsoft Internet Information Services (IIS) virtual directory configured to use Windows integrated authentication.</span></span>  
  
-   <span data-ttu-id="bef6e-110">設定為使用基本驗證的 IIS 虛擬目錄所代表的後端系統。</span><span class="sxs-lookup"><span data-stu-id="bef6e-110">Back-end system, represented by an IIS virtual directory configured to use basic authentication.</span></span>  
  
-   <span data-ttu-id="bef6e-111">SQL 範例資料庫 Northwind 所代表的後端資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef6e-111">Back-end database, represented by the SQL sample database Northwind.</span></span>  
  
 <span data-ttu-id="bef6e-112">此範例假設您已安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 SSO。</span><span class="sxs-lookup"><span data-stu-id="bef6e-112">This sample assumes that you have installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SSO.</span></span> <span data-ttu-id="bef6e-113">您必須擁有系統管理員權限[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，IIS、 SSO 和 COM + Windows XP Professional 上。</span><span class="sxs-lookup"><span data-stu-id="bef6e-113">You must have administrator privileges for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], IIS, SSO, and COM+ on Windows XP Professional.</span></span> <span data-ttu-id="bef6e-114">您也必須是 SSO 系統管理員、BizTalk Server 系統管理員和 BizTalk 外掛式主控件使用者 Windows 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="bef6e-114">You must also be a member of SSO Administrators, BizTalk Server Administrators, and BizTalk Isolated Host Users Windows groups.</span></span>  
  
 <span data-ttu-id="bef6e-115">有效使用此範例的前提為，您具備 SSO 和 BizTalk HTTP 配接器的足夠知識。</span><span class="sxs-lookup"><span data-stu-id="bef6e-115">Effective use of this sample assumes that you have sufficient knowledge of SSO and the BizTalk HTTP adapter.</span></span> <span data-ttu-id="bef6e-116">例如，您應該了解什麼是 SSO 內容中的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="bef6e-116">For example, you should know what an affiliate application is in the context of SSO.</span></span> <span data-ttu-id="bef6e-117">如需這些主題的資訊，請參閱[使用 SSO](../core/using-sso.md)。</span><span class="sxs-lookup"><span data-stu-id="bef6e-117">For information about these topics, see [Using SSO](../core/using-sso.md).</span></span> <span data-ttu-id="bef6e-118">另請參閱[HTTP 配接器](../core/http-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="bef6e-118">Also see [HTTP Adapter](../core/http-adapter.md).</span></span>  
  
 <span data-ttu-id="bef6e-119">在您完成設定之後，此範例的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="bef6e-119">After you complete the configuration, this sample works as follows:</span></span>  
  
1.  <span data-ttu-id="bef6e-120">當您按一下**完成**在此範例使用者介面的精靈應用程式，Internet Explorer 的執行個體啟動並傳遞 BizTalk HTTP 接收 DLL 的 URL。</span><span class="sxs-lookup"><span data-stu-id="bef6e-120">When you click **Finish** in the wizard application that comprises the user interface for this sample, an instance of Internet Explorer starts and passes the URL of the BizTalk HTTP Receive DLL.</span></span>  
  
2.  <span data-ttu-id="bef6e-121">BizTalk Server 搭配 SSO 便能有效地將 HTTP 要求轉寄至已設定為使用基本驗證的 IIS 虛擬目錄中的 EmployeeData.aspx 檔。</span><span class="sxs-lookup"><span data-stu-id="bef6e-121">BizTalk Server, with the help of SSO, effectively forwards the HTTP request to the file EmployeeData.aspx in an IIS virtual directory that has been configured with basic authentication.</span></span> <span data-ttu-id="bef6e-122">此 ASPX 檔會模擬進入非 Windows 後端系統的進入點。</span><span class="sxs-lookup"><span data-stu-id="bef6e-122">This ASPX file simulates the entry point into a non-Windows back-end system.</span></span> <span data-ttu-id="bef6e-123">由於您使用的是 SSO，因此 HTTP 要求會包含設定為模擬登入帳戶至所模擬後端系統的憑證。</span><span class="sxs-lookup"><span data-stu-id="bef6e-123">Because you are using SSO, the HTTP request includes the configured credentials that simulate a logon account to the simulated back-end system.</span></span>  
  
3.  <span data-ttu-id="bef6e-124">ASPX 檔會存取修改的 SQL 範例資料庫 Northwind 版本，以擷取對應至模擬後端系統憑證的員工資料。</span><span class="sxs-lookup"><span data-stu-id="bef6e-124">The ASPX file accesses a modified version of the SQL sample database Northwind to retrieve employee data corresponding to the simulated back-end system credentials.</span></span>  
  
4.  <span data-ttu-id="bef6e-125">ASPX 檔會在 HTTP 回應中傳回擷取的員工資料。</span><span class="sxs-lookup"><span data-stu-id="bef6e-125">The ASPX file returns the retrieved employee data in an HTTP response.</span></span>  
  
5.  <span data-ttu-id="bef6e-126">BizTalk Server 會將 HTTP 回應傳遞至 Internet Explorer，而 Internet Explorer 會對使用者顯示傳回的員工資料。</span><span class="sxs-lookup"><span data-stu-id="bef6e-126">BizTalk Server routes the HTTP response to Internet Explorer, which displays the returned employee data to the user.</span></span>  
  
 <span data-ttu-id="bef6e-127">如果您略過 BizTalk Server 和 SSO，並且直接瀏覽至 EmployeeData.aspx 檔，則 Windows 對話方塊會提示您提供憑證。</span><span class="sxs-lookup"><span data-stu-id="bef6e-127">If you bypass BizTalk Server and SSO, and browse directly to the file EmployeeData.aspx, a Windows dialog box will prompt you for your credentials.</span></span>  
  
 <span data-ttu-id="bef6e-128">如需範例，示範如何使用命令列公用程式 ssomanage.exe 設定 SSO，例如建立分支機構應用程式和使用者對應，請參閱[管理 （BizTalk Server 範例）](../core/manage-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="bef6e-128">For a sample that shows how to use the command-line utility ssomanage.exe to configure SSO, such as creating affiliate applications and user mappings, see [Manage (BizTalk Server Sample)](../core/manage-biztalk-server-sample.md).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="bef6e-129">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="bef6e-129">Where to Find This Sample</span></span>  
 <span data-ttu-id="bef6e-130">\<*範例路徑*\>\SSO\HTTPSSO\\</span><span class="sxs-lookup"><span data-stu-id="bef6e-130">\<*Samples Path*\>\SSO\HTTPSSO\\</span></span>  
  
 <span data-ttu-id="bef6e-131">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="bef6e-131">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="bef6e-132">檔案</span><span class="sxs-lookup"><span data-stu-id="bef6e-132">File(s)</span></span>|<span data-ttu-id="bef6e-133">Description</span><span class="sxs-lookup"><span data-stu-id="bef6e-133">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bef6e-134">AssemblyInfo.cs，SsoSample.csproj</span><span class="sxs-lookup"><span data-stu-id="bef6e-134">AssemblyInfo.cs, SsoSample.csproj</span></span>|<span data-ttu-id="bef6e-135">此 HTTP SSO 範例的專案及相關檔案。</span><span class="sxs-lookup"><span data-stu-id="bef6e-135">Project and related files for this HTTP SSO sample.</span></span>|  
|<span data-ttu-id="bef6e-136">SsoSample.cs</span><span class="sxs-lookup"><span data-stu-id="bef6e-136">SsoSample.cs</span></span>|<span data-ttu-id="bef6e-137">構成此範例大部分的 HTTP SSO 圖形應用程式的最上層 Microsoft Visual C# 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="bef6e-137">Top-level Microsoft Visual C# source file for the HTTP SSO graphical application that constitutes much of this sample.</span></span> <span data-ttu-id="bef6e-138">這個檔案包含名為類別中的 SSO 組態程式碼**SsoConfigurator** ，最終都會是這個範例的點。</span><span class="sxs-lookup"><span data-stu-id="bef6e-138">This file contains the SSO configuration code, in a class named **SsoConfigurator** that is ultimately the point of this sample.</span></span>|  
|<span data-ttu-id="bef6e-139">在 \Scripts 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="bef6e-139">In the \Scripts folder:</span></span><br /><br /> <span data-ttu-id="bef6e-140">EmployeeData.aspx</span><span class="sxs-lookup"><span data-stu-id="bef6e-140">EmployeeData.aspx</span></span>|<span data-ttu-id="bef6e-141">當員工直接或使用 SSO 發出檢視個人資料的要求時，用來存取和查詢後端資料庫 (在此案例中為 SQL Northwind 資料庫)。</span><span class="sxs-lookup"><span data-stu-id="bef6e-141">Used to access and query the back-end database (in this case, the SQL Northwind database) when an employee initiates a request to view personal data, either directly or by using SSO.</span></span>|  
|<span data-ttu-id="bef6e-142">在 \Scripts 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="bef6e-142">In the \Scripts folder:</span></span><br /><br /> <span data-ttu-id="bef6e-143">ValidateUser.aspx</span><span class="sxs-lookup"><span data-stu-id="bef6e-143">ValidateUser.aspx</span></span>|<span data-ttu-id="bef6e-144">直接或使用 SSO 簡單進行測試以驗證使用者，並報告該使用者是否通過驗證。</span><span class="sxs-lookup"><span data-stu-id="bef6e-144">Simple test to validate a user and report if that user was validated, either directly or by using SSO.</span></span>|  
|<span data-ttu-id="bef6e-145">在 \UI 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="bef6e-145">In the \UI folder:</span></span><br /><br /> <span data-ttu-id="bef6e-146">AddApplication.cs、AddApplication.resx、AddMapping.cs、AddMapping.resx、App.ico、BtsPage.cs、BtsPage.resx、ExecutePage.cs、ExecutePage.resx、FinishPage.cs、FinishPage.resx、IisPage.cs、IisPage.resx、InfoPage.cs、InfoPage.resx、PageBase.cs、PageBase.resx、SsoPage.cs、SsoPage.resx、SsoSampleWizard.cs、SsoSampleWizard.resx、WelcomePage.cs、WelcomePage.resx、WorkPage.cs、WorkPage.resx</span><span class="sxs-lookup"><span data-stu-id="bef6e-146">AddApplication.cs, AddApplication.resx, AddMapping.cs, AddMapping.resx, App.ico, BtsPage.cs, BtsPage.resx, ExecutePage.cs, ExecutePage.resx, FinishPage.cs, FinishPage.resx, IisPage.cs, IisPage.resx, InfoPage.cs, InfoPage.resx, PageBase.cs, PageBase.resx, SsoPage.cs, SsoPage.resx, SsoSampleWizard.cs, SsoSampleWizard.resx, WelcomePage.cs, WelcomePage.resx, WorkPage.cs, WorkPage.resx</span></span>|<span data-ttu-id="bef6e-147">輔助 Visual C# 原始程式檔及其相關的 XML 格式資源檔，用於構成此範例大部分的 HTTP SSO 圖形應用程式。</span><span class="sxs-lookup"><span data-stu-id="bef6e-147">Auxiliary Visual C# source files, and their associated XML-formatted resource files, for the HTTP SSO graphical application that constitutes much of this sample.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="bef6e-148">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="bef6e-148">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-httpsso-sample"></a><span data-ttu-id="bef6e-149">建置與初始化 HTTPSSO 範例</span><span class="sxs-lookup"><span data-stu-id="bef6e-149">To build and initialize the HTTPSSO sample</span></span>  
  
1.  <span data-ttu-id="bef6e-150">建立 Microsoft Internet Information Services (IIS) 可用於基本驗證的本機 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="bef6e-150">Create a local Windows account that Microsoft Internet Information Services (IIS) can use for basic authentication.</span></span> <span data-ttu-id="bef6e-151">SSO 會將 Windows 網域帳戶對應至此本機 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="bef6e-151">SSO maps the Windows domain account to this local Windows account.</span></span> <span data-ttu-id="bef6e-152">例如，使用您的姓氏建立本機 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="bef6e-152">For example, use your last name to create a local Windows account.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bef6e-153">如果您是在網域控制站上執行，則可以建立網域帳戶並將您的登入網域帳戶對應至此帳戶。</span><span class="sxs-lookup"><span data-stu-id="bef6e-153">If you are running on a domain controller, you can create domain accounts and map your logged on domain account to this account.</span></span>  
  
2.  <span data-ttu-id="bef6e-154">使用 Microsoft SQL Server Enterprise Manager，開啟**員工**資料表中的 Northwind 範例資料庫，然後再加入對應至您剛剛建立，包括的各種範例資料的本機 Windows 帳戶的資料列資料行。</span><span class="sxs-lookup"><span data-stu-id="bef6e-154">Using Microsoft SQL Server Enterprise Manager, open the **Employees** table in the Northwind sample database, and then add a row corresponding to the local Windows account that you just created, including sample data for the various columns.</span></span> <span data-ttu-id="bef6e-155">您新增至 [員工] 資料表中 [姓氏] 資料欄的值，必須與您在步驟 1 中新增的本機 Windows 帳戶的使用者名稱相同。</span><span class="sxs-lookup"><span data-stu-id="bef6e-155">The value you add to the LastName column in the Employees table must be the same as the user name of the local Windows account you added in step 1.</span></span>  
  
3.  <span data-ttu-id="bef6e-156">確認 ASP.NET 帳戶 (ASPNET) 具備 Northwind 資料庫的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="bef6e-156">Ensure the ASP.NET account (ASPNET) has read privileges to the Northwind database.</span></span>  
  
4.  <span data-ttu-id="bef6e-157">使用 Visual Studio 開啟專案檔 SsoSample.csproj。</span><span class="sxs-lookup"><span data-stu-id="bef6e-157">Open the project file SsoSample.csproj using Visual Studio.</span></span>  
  
5.  <span data-ttu-id="bef6e-158">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="bef6e-158">On the **Build** menu, click **Build Solution**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bef6e-159">此時可能會要求您先儲存方案檔，才能繼續建置。</span><span class="sxs-lookup"><span data-stu-id="bef6e-159">You may be asked to save a solution file before the build can proceed.</span></span>  
  
     <span data-ttu-id="bef6e-160">如果您找不到專案的下列 BizTalk 組件參照，請將它們刪除，再從指示的位置重新加入，並且再次建置：</span><span class="sxs-lookup"><span data-stu-id="bef6e-160">If you cannot find the following BizTalk assembly references for the project, delete them, re-add them from the indicated locations, and build again:</span></span>  
  
    -   <span data-ttu-id="bef6e-161">**Microsoft.BizTalk.ExplorerOM**。</span><span class="sxs-lookup"><span data-stu-id="bef6e-161">**Microsoft.BizTalk.ExplorerOM**.</span></span> <span data-ttu-id="bef6e-162">根據預設，Microsoft.BizTalk.ExplorerOM.dll 檔位於資料夾[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]開發人員工具\\。</span><span class="sxs-lookup"><span data-stu-id="bef6e-162">By default, the Microsoft.BizTalk.ExplorerOM.dll file is located in the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Developer Tools\\.</span></span>  
  
    -   <span data-ttu-id="bef6e-163">**Ipropertybag**。</span><span class="sxs-lookup"><span data-stu-id="bef6e-163">**Microsoft.BizTalk.SSOClient.Interop**.</span></span> <span data-ttu-id="bef6e-164">根據預設，Microsoft.BizTalk.Interop.SSOClient.dll 檔位於資料夾\< *ProgramFiles*\>單一登入 \Common Files\Enterprise\\。</span><span class="sxs-lookup"><span data-stu-id="bef6e-164">By default, the Microsoft.BizTalk.Interop.SSOClient.dll file is located in the folder \<*ProgramFiles*\>\Common Files\Enterprise Single Sign-On\\.</span></span>  
  
     <span data-ttu-id="bef6e-165">這樣做會在下列資料夾中產生可執行檔 SsoSample.exe：</span><span class="sxs-lookup"><span data-stu-id="bef6e-165">This produces the executable file SsoSample.exe in the following folder:</span></span>  
  
     <span data-ttu-id="bef6e-166">\<*範例路徑*\>\SSO\HTTPSSO\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="bef6e-166">\<*Samples Path*\>\SSO\HTTPSSO\bin\Debug\\</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="bef6e-167">執行此範例</span><span class="sxs-lookup"><span data-stu-id="bef6e-167">Running This Sample</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bef6e-168">如果您在 IIS 6.0 上以「背景工作處理序隔離模式」執行此範例，系統會為這兩個虛擬目錄建立應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="bef6e-168">If you run this sample on IIS 6.0 in Worker Process Isolation Mode, application pools are created for both virtual directories.</span></span> <span data-ttu-id="bef6e-169">您必須在 Windows 帳戶中手動設定這兩個應用程式集區的識別 (您可以在 Internet Information Services Manager 中設定識別)。</span><span class="sxs-lookup"><span data-stu-id="bef6e-169">You must manually configure identity for these two application pools in your Windows account (you can configure identity in Internet Information Services Manager).</span></span>  
  
#### <a name="to-run-the-httpsso-sample"></a><span data-ttu-id="bef6e-170">執行 HTTPSSO 範例</span><span class="sxs-lookup"><span data-stu-id="bef6e-170">To run the HTTPSSO sample</span></span>  
  
1.  <span data-ttu-id="bef6e-171">執行可執行檔 SsoSample.exe，該檔案位於下列資料夾中：</span><span class="sxs-lookup"><span data-stu-id="bef6e-171">Run the executable file SsoSample.exe, found in the following folder:</span></span>  
  
     <span data-ttu-id="bef6e-172">\<*範例路徑*\>\SSO\HTTPSSO\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="bef6e-172">\<*Samples Path*\>\SSO\HTTPSSO\bin\Debug\\</span></span>  
  
     <span data-ttu-id="bef6e-173">此範例的精靈應用程式隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="bef6e-173">The wizard application for this sample opens.</span></span>  
  
2.  <span data-ttu-id="bef6e-174">在 [歡迎使用] 頁面上，接受預設設定來設定 IIS、 SSO 和 BizTalk 中，，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bef6e-174">On the Welcome page, accept the default setting for configuring IIS, SSO, and BizTalk, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="bef6e-175">在 IIS 組態 頁面上，接受預設設定的兩個 IIS 虛擬目錄來建立，然後按一下您想**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bef6e-175">On the IIS Configuration page, accept the default settings for the two IIS virtual directories you want to create, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="bef6e-176">在 SSO 組態 頁面上，接受預設設定分支機構應用程式，也就是可存取使用**新增應用程式** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bef6e-176">On the SSO Configuration page, accept the default settings for the affiliate application, which is accessible using the **Add application** button.</span></span>  
  
5.  <span data-ttu-id="bef6e-177">在 SSO 組態 頁面上，接受大部分的使用者對應，預設設定可存取使用**新增對應** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bef6e-177">On the SSO Configuration page, accept most of the default settings for the user mappings, accessible using the **Add mapping** button.</span></span> <span data-ttu-id="bef6e-178">根據建置和啟始此範例時新增的本機 Windows 帳戶，為下面兩個設定提供值。</span><span class="sxs-lookup"><span data-stu-id="bef6e-178">Provide values for the following two settings based on the local Windows account you added when building and initializing this sample.</span></span>  
  
    |<span data-ttu-id="bef6e-179">設定</span><span class="sxs-lookup"><span data-stu-id="bef6e-179">Setting</span></span>|<span data-ttu-id="bef6e-180">值</span><span class="sxs-lookup"><span data-stu-id="bef6e-180">Value</span></span>|  
    |-------------|-----------|  
    |<span data-ttu-id="bef6e-181">外部使用者名稱</span><span class="sxs-lookup"><span data-stu-id="bef6e-181">External user name</span></span>|<span data-ttu-id="bef6e-182">設定為新增的本機 Windows 使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="bef6e-182">Set to the added local Windows user account name.</span></span>|  
    |<span data-ttu-id="bef6e-183">外部使用者密碼</span><span class="sxs-lookup"><span data-stu-id="bef6e-183">External user password</span></span>|<span data-ttu-id="bef6e-184">設定為新增的本機 Windows 使用者帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="bef6e-184">Set to the added local Windows user account password.</span></span>|  
  
6.  <span data-ttu-id="bef6e-185">在 SSO 組態] 頁面上，按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bef6e-185">On the SSO Configuration page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="bef6e-186">在 BizTalk 組態 頁面上，接受預設設定為傳送和接收連接埠，並依此類推，，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bef6e-186">On the BizTalk Configuration page, accept the default settings for the send and receive ports, and so on, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bef6e-187">您可以變更預設的傳送埠設定，從**EmployeeData.aspx**至**ValidateUser.aspx**如果您想要看到簡單的使用者驗證，而非範例資料取自的 Employee 資料表Northwinds SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bef6e-187">You can change the default send port setting from **EmployeeData.aspx** to **ValidateUser.aspx** if you want to see simple user validation rather than sample data pulled from the Employee table of the Northwinds SQL database.</span></span> <span data-ttu-id="bef6e-188">進行這項變更會改變之後按一下 瀏覽器中顯示的輸出**完成**在步驟 9。</span><span class="sxs-lookup"><span data-stu-id="bef6e-188">Making this change changes the nature of the output displayed in the browser after clicking **Finish** in step 9.</span></span>  
  
8.  <span data-ttu-id="bef6e-189">查閱對應至所執行 IIS、SSO 和 BizTalk 組態的狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="bef6e-189">Review the status messages corresponding to the IIS, SSO, and BizTalk configuration being performed.</span></span> <span data-ttu-id="bef6e-190">您可以找到此階段中執行的程式碼**IisConfigurator**， **SsoConfigurator**，和**BtsConfigurator** ssosample.cs 中定義的類別。</span><span class="sxs-lookup"><span data-stu-id="bef6e-190">You can find the code that is run during this phase in the **IisConfigurator**, **SsoConfigurator**, and **BtsConfigurator** classes defined in the file SsoSample.cs.</span></span> <span data-ttu-id="bef6e-191">組態完成之後，請按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bef6e-191">After configuration has completed, click **Next**.</span></span>  
  
9. <span data-ttu-id="bef6e-192">在精靈應用程式的最後一個頁面上，接受預設設定**啟動瀏覽器在**(選取的核取方塊和 url http://localhost/SsoSampleBizTalkHttpReceive/BTSHttpReceive.dll? 文字方塊<message/>)，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="bef6e-192">On the final page of the wizard application, accept the default settings for **Start browser at** (a selected check box and a text box with the URL http://localhost/SsoSampleBizTalkHttpReceive/BTSHttpReceive.dll?<message/>), and then click **Finish**.</span></span>  
  
     <span data-ttu-id="bef6e-193">Internet Explorer 的執行個體將會開啟，並且很快地顯示您新增至 Northwinds SQL 資料庫的 [員工] 資料表中的範例員工資料。</span><span class="sxs-lookup"><span data-stu-id="bef6e-193">An instance of Internet Explorer will open, and soon display the sample employee data that you added to the Employee table of the Northwinds SQL database.</span></span>  
  
 <span data-ttu-id="bef6e-194">基於比較的目的，您可以略過 BizTalk 和 SSO，並直接瀏覽至任一個 ASPX 檔：</span><span class="sxs-lookup"><span data-stu-id="bef6e-194">For comparison purposes, you can bypass BizTalk and SSO and browse directly to either of the ASPX files:</span></span>  
  
-   <span data-ttu-id="bef6e-195">http://localhost/SsoSampleServerApplication/ValidateUser.aspx</span><span class="sxs-lookup"><span data-stu-id="bef6e-195">http://localhost/SsoSampleServerApplication/ValidateUser.aspx</span></span>  
  
-   <span data-ttu-id="bef6e-196">http://localhost/SsoSampleServerApplication/EmployeeData.aspx</span><span class="sxs-lookup"><span data-stu-id="bef6e-196">http://localhost/SsoSampleServerApplication/EmployeeData.aspx</span></span>  
  
 <span data-ttu-id="bef6e-197">在這兩個案例中，由於您略過 BizTalk 和 SSO，因此會提示您提供 IIS 的驗證資訊 (使用您之前建立的本機 Windows 帳戶資訊)。</span><span class="sxs-lookup"><span data-stu-id="bef6e-197">In both cases, because you bypass BizTalk and SSO, you are prompted for your authentication information by IIS (use the local Windows account information you created previously).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="bef6e-198">註解</span><span class="sxs-lookup"><span data-stu-id="bef6e-198">Comments</span></span>  
 <span data-ttu-id="bef6e-199">SsoSample.exe 精靈應用程式會設定這兩個 IIS 虛擬目錄：</span><span class="sxs-lookup"><span data-stu-id="bef6e-199">The SsoSample.exe wizard application configures two IIS virtual directories:</span></span>  
  
-   <span data-ttu-id="bef6e-200">第一個虛擬目錄設定為使用 Windows 整合式驗證，並且對應至 BizTalk HTTP 接收 ISAPI 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="bef6e-200">The first virtual directory is configured with Windows integrated authentication and corresponds to the BizTalk HTTP Receive ISAPI extension.</span></span> <span data-ttu-id="bef6e-201">該目錄必須與位於下列資料夾中的 .dll 檔 BTSHTTPReceive.dll 相關：</span><span class="sxs-lookup"><span data-stu-id="bef6e-201">It must be associated with the .dll file BTSHTTPReceive.dll located in the following folder:</span></span>  
  
     <span data-ttu-id="bef6e-202">\<*安裝路徑*\>\HttpReceive</span><span class="sxs-lookup"><span data-stu-id="bef6e-202">\<*Install Path*\>\HttpReceive</span></span>  
  
-   <span data-ttu-id="bef6e-203">第二個虛擬目錄設定為使用基本驗證，並且會模擬接受使用者識別碼和密碼來驗證使用者的後端系統。</span><span class="sxs-lookup"><span data-stu-id="bef6e-203">The second virtual directory is configured with basic authentication and simulates a back-end system that accepts a user ID and password to authenticate the user.</span></span> <span data-ttu-id="bef6e-204">該目錄必須與位於下列資料夾中的任一個 ASPX 檔 ValidateUser.aspx 或 EmployeeData.aspx 相關：</span><span class="sxs-lookup"><span data-stu-id="bef6e-204">It must be associated with one or the other of the ASPX files, ValidateUser.aspx or EmployeeData.aspx, located in the following folder:</span></span>  
  
     <span data-ttu-id="bef6e-205">\<*範例路徑*\>\SSO\HTTPSSO\Scripts</span><span class="sxs-lookup"><span data-stu-id="bef6e-205">\<*Samples Path*\>\SSO\HTTPSSO\Scripts</span></span>  
  
 <span data-ttu-id="bef6e-206">您可以使用 SsoSample.exe 精靈應用程式設定一或多個分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="bef6e-206">You can use the SsoSample.exe wizard application to configure one or more affiliate applications.</span></span> <span data-ttu-id="bef6e-207">針對每個分支機構應用程式，可以建立一或多個使用者對應。</span><span class="sxs-lookup"><span data-stu-id="bef6e-207">For each of these affiliate applications, you can create one or more user mappings.</span></span> <span data-ttu-id="bef6e-208">每個使用者對應都會將一個 Windows 使用者帳戶對應到您用來存取特定後端系統的帳戶。</span><span class="sxs-lookup"><span data-stu-id="bef6e-208">Each of these user mappings maps a Windows user account to an account that you use to access a specific back-end system.</span></span> <span data-ttu-id="bef6e-209">在此範例中，該帳戶為您用來對模擬實際後端系統的第二個 IIS 虛擬資料夾驗證的本機 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="bef6e-209">In this sample, that account is a local Windows account that you use to authenticate with the second IIS virtual directory that is simulating a genuine back-end system.</span></span>  
  
 <span data-ttu-id="bef6e-210">若要重新執行此範例，可從下列數個選項中選擇：</span><span class="sxs-lookup"><span data-stu-id="bef6e-210">To rerun this sample, you have several choices:</span></span>  
  
-   <span data-ttu-id="bef6e-211">直接瀏覽至 Internet Explorer 中的下列 URL：</span><span class="sxs-lookup"><span data-stu-id="bef6e-211">Browse directly to the following URL in Internet Explorer:</span></span>  
  
     <span data-ttu-id="bef6e-212">http://localhost/SsoSampleBizTalkHttpReceive/BTSHttpReceive.dll?<message/></span><span class="sxs-lookup"><span data-stu-id="bef6e-212">http://localhost/SsoSampleBizTalkHttpReceive/BTSHttpReceive.dll?<message/></span></span>  
  
-   <span data-ttu-id="bef6e-213">再次執行精靈應用程式，但清除第一頁上的所有組態設定核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bef6e-213">Run the wizard application again, but clear all of the configuration check boxes on the first page.</span></span>  
  
-   <span data-ttu-id="bef6e-214">再次執行精靈應用程式，保留第一頁上選取的組態設定何取方塊，但謹慎且適當地設定其他 BizTalk 項目、分支機構應用程式等，以避免發生組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="bef6e-214">Run the wizard application again, leave the configuration check boxes selected in the first page, but carefully and appropriately configure additional BizTalk items, affiliate applications, and so on, so that configuration errors do not occur.</span></span>  
  
 <span data-ttu-id="bef6e-215">若要清除此範例，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="bef6e-215">To clean up from this sample, use the following procedure.</span></span>  
  
#### <a name="to-clean-up-from-this-sample"></a><span data-ttu-id="bef6e-216">清除此範例</span><span class="sxs-lookup"><span data-stu-id="bef6e-216">To clean up from this sample</span></span>  
  
1.  <span data-ttu-id="bef6e-217">採取適當的方式，反向您執行的手動組態設定，例如移除本機 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="bef6e-217">As appropriate, reverse the manual configuration that you performed, such as removing the local Windows account.</span></span>  
  
2.  <span data-ttu-id="bef6e-218">移除對應至虛擬目錄的 IIS 應用程式，然後刪除此範例建立的 IIS 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="bef6e-218">Remove IIS applications that correspond to the virtual directories, and then delete the IIS virtual directories created by this sample.</span></span>  
  
3.  <span data-ttu-id="bef6e-219">使用 [BizTalk 管理] 主控台取消登錄，然後刪除與此範例關聯的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="bef6e-219">Using BizTalk Administration console, unenlist and then delete the send port associated with this sample.</span></span> <span data-ttu-id="bef6e-220">接著刪除與此範例相關的接收埠 (及其接收位置)，</span><span class="sxs-lookup"><span data-stu-id="bef6e-220">Then delete the receive port (and its receive location) associated with this sample.</span></span>  
  
4.  <span data-ttu-id="bef6e-221">使用 Ssomanage 應用程式 (位於 Files\Enterprise Single Sign-on \Program Files\Common\\) 若要刪除此範例的 SSO 應用程式：</span><span class="sxs-lookup"><span data-stu-id="bef6e-221">Use the Ssomanage application (located in \Program Files\Common Files\Enterprise Single Sign-On\\) to delete the SSO application for this sample:</span></span>  
  
    ```  
    Ssomanage –deleteapp SsoSampleApplication  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bef6e-222">請參閱</span><span class="sxs-lookup"><span data-stu-id="bef6e-222">See Also</span></span>  
 [<span data-ttu-id="bef6e-223">SSO (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="bef6e-223">SSO (BizTalk Server Samples Folder)</span></span>](../core/sso-biztalk-server-samples-folder.md)