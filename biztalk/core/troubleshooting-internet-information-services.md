---
title: 疑難排解 Internet Information Services |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f77084f1-5797-42ab-bbf6-fe815144232e
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f7ca928aa2e47b5c62548aba02834b96d6a3baf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006655"
---
# <a name="troubleshooting-internet-information-services"></a><span data-ttu-id="9d178-102">Internet Information Services 疑難排解</span><span class="sxs-lookup"><span data-stu-id="9d178-102">Troubleshooting Internet Information Services</span></span>
<span data-ttu-id="9d178-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 經常使用 Microsoft Internet Information Services (IIS) 提供各種功能，包括 HTTP、SOAP 和 Windows SharePoint Services 配接器。</span><span class="sxs-lookup"><span data-stu-id="9d178-103">Microsoft Internet Information Services (IIS) is used extensively by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for various functionality including the HTTP, SOAP, and Windows SharePoint Services adapters.</span></span> <span data-ttu-id="9d178-104">本主題描述在使用 IIS 時可能遇到的一些已知問題，以及這些問題的可能解決方案。</span><span class="sxs-lookup"><span data-stu-id="9d178-104">This topic describes some known issues that you may encounter with IIS and possible resolutions to these issues.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="9d178-105">已知問題</span><span class="sxs-lookup"><span data-stu-id="9d178-105">Known Issues</span></span>  
 <span data-ttu-id="9d178-106">本主題中記錄的錯誤可能不會顯示，除非您將 Internet Explorer 設定為停用易懂的 HTTP 錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9d178-106">The errors documented in this topic may not be displayed unless you configure Internet Explorer to disable friendly HTTP error messages.</span></span>  
  
#### <a name="to-configure-internet-explorer-to-disable-friendly-http-error-messages"></a><span data-ttu-id="9d178-107">將 Internet Explorer 設定為停用易記的 HTTP 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="9d178-107">To configure Internet Explorer to disable friendly HTTP error messages</span></span>  
  
1.  <span data-ttu-id="9d178-108">在 **工具**功能表上，按一下**網際網路選項**。</span><span class="sxs-lookup"><span data-stu-id="9d178-108">On the **Tools** menu, click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="9d178-109">在上**進階**索引標籤中，於**瀏覽**區段中，清除**顯示易懂的 HTTP 錯誤訊息**核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9d178-109">On the **Advanced** tab, in the **Browsing** section, clear the **Show friendly HTTP error messages** check box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="9d178-110">關閉 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="9d178-110">Close Internet Explorer.</span></span>  
  
#### <a name="http-404---file-not-found-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a><span data-ttu-id="9d178-111">在 IIS 伺服器上存取網頁時發生「HTTP 404 – 找不到檔案」錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d178-111">"HTTP 404 - File not found" error occurs when accessing a Web page on an IIS server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="9d178-112">問題</span><span class="sxs-lookup"><span data-stu-id="9d178-112">Problem</span></span>  
 <span data-ttu-id="9d178-113">當您嘗試存取 IIS 伺服器上的網站時，會出現類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="9d178-113">When you attempt to access a Web page on an IIS server an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="9d178-114">找不到頁面</span><span class="sxs-lookup"><span data-stu-id="9d178-114">Page Cannot Be Found</span></span>  
  
 <span data-ttu-id="9d178-115">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="9d178-115">\- or -</span></span>  
  
 <span data-ttu-id="9d178-116">HTTP 404 - 找不到檔案</span><span class="sxs-lookup"><span data-stu-id="9d178-116">HTTP 404 - File not found</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="9d178-117">原因</span><span class="sxs-lookup"><span data-stu-id="9d178-117">Cause</span></span>  
 <span data-ttu-id="9d178-118">發生這個錯誤的原因有下列幾種︰</span><span class="sxs-lookup"><span data-stu-id="9d178-118">This error may occur for the following reasons:</span></span>  
  
-   <span data-ttu-id="9d178-119">要求的檔案已被重新命名。</span><span class="sxs-lookup"><span data-stu-id="9d178-119">The requested file has been renamed.</span></span>  
  
-   <span data-ttu-id="9d178-120">要求的檔案已經刪除或移至其他位置。</span><span class="sxs-lookup"><span data-stu-id="9d178-120">The requested file has been moved to another location or deleted.</span></span>  
  
-   <span data-ttu-id="9d178-121">由於維護、升級或其他未知的原因，暫時無法使用要求的檔案。</span><span class="sxs-lookup"><span data-stu-id="9d178-121">The requested file is temporarily unavailable due to maintenance, upgrades, or other unknown causes.</span></span>  
  
-   <span data-ttu-id="9d178-122">要求的檔案不存在。</span><span class="sxs-lookup"><span data-stu-id="9d178-122">The requested file does not exist.</span></span>  
  
-   <span data-ttu-id="9d178-123">IIS 6.0： 不會啟用適當的 Web 服務延伸模組或 MIME 類型。</span><span class="sxs-lookup"><span data-stu-id="9d178-123">IIS 6.0: The appropriate Web service extension or MIME type is not enabled.</span></span>  
  
-   <span data-ttu-id="9d178-124">虛擬目錄對應到另一部伺服器上磁碟機的根目錄。</span><span class="sxs-lookup"><span data-stu-id="9d178-124">A virtual directory is mapped to the root of a drive on another server.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="9d178-125">解決方案</span><span class="sxs-lookup"><span data-stu-id="9d178-125">Resolution</span></span>  
 <span data-ttu-id="9d178-126">遵循 Microsoft 知識庫文件 248033，"常見原因 IIS 伺服器會傳回 「 HTTP 404-找不到檔案 」 的錯誤 」 一節中的步驟可在[ http://support.microsoft.com/kb/248033 ](http://support.microsoft.com/kb/248033)。</span><span class="sxs-lookup"><span data-stu-id="9d178-126">Follow the steps in the RESOLUTION section of Microsoft Knowledge Base article 248033, "Common reasons IIS Server returns "HTTP 404 - File not found" error" available at [http://support.microsoft.com/kb/248033](http://support.microsoft.com/kb/248033).</span></span>  
  
#### <a name="cannot-find-server-or-dns-error-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a><span data-ttu-id="9d178-127">在 IIS 伺服器上存取網頁時發生「找不到伺服器或 DNS 錯誤」錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d178-127">"Cannot find server or DNS Error error" occurs when accessing a Web page on an IIS server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="9d178-128">問題</span><span class="sxs-lookup"><span data-stu-id="9d178-128">Problem</span></span>  
 <span data-ttu-id="9d178-129">當您嘗試存取 IIS 伺服器上的網站時，會出現類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="9d178-129">When you attempt to access a Web page on an IIS server an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="9d178-130">無法顯示頁面</span><span class="sxs-lookup"><span data-stu-id="9d178-130">The Page Cannot Be Displayed</span></span>  
  
 <span data-ttu-id="9d178-131">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="9d178-131">\- or -</span></span>  
  
 <span data-ttu-id="9d178-132">找不到伺服器或 DNS 錯誤</span><span class="sxs-lookup"><span data-stu-id="9d178-132">Cannot find server or DNS Error</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="9d178-133">原因</span><span class="sxs-lookup"><span data-stu-id="9d178-133">Cause</span></span>  
 <span data-ttu-id="9d178-134">發生這個錯誤的原因有下列幾種︰</span><span class="sxs-lookup"><span data-stu-id="9d178-134">This error may occur for the following reasons:</span></span>  
  
-   <span data-ttu-id="9d178-135">Internet Explorer 連線設定不正確。</span><span class="sxs-lookup"><span data-stu-id="9d178-135">Your Internet Explorer connection settings are incorrect.</span></span>  
  
-   <span data-ttu-id="9d178-136">安裝的防火牆或 Proxy 軟體設定不正確、未作用或不相容。</span><span class="sxs-lookup"><span data-stu-id="9d178-136">Incorrectly configured, non-functioning, or incompatible firewall or proxy software has been installed.</span></span>  
  
-   <span data-ttu-id="9d178-137">主機檔案中有不正確的項目。</span><span class="sxs-lookup"><span data-stu-id="9d178-137">There is an incorrect entry in a Hosts file.</span></span>  
  
-   <span data-ttu-id="9d178-138">網路配接器未正確作用，或者安裝了不相容的網路配接器驅動程式。</span><span class="sxs-lookup"><span data-stu-id="9d178-138">Your network adapter is not functioning correctly or you have incompatible network adapter drivers installed.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="9d178-139">解決方案</span><span class="sxs-lookup"><span data-stu-id="9d178-139">Resolution</span></span>  
 <span data-ttu-id="9d178-140">遵循 Microsoft 知識庫文章 326155，一節中的步驟 」 當您嘗試存取網站，在 Internet Explorer 中出現錯誤訊息: 「 無法顯示網頁 」 「 網址[ http://support.microsoft.com/kb/326155 ](http://support.microsoft.com/kb/326155)。</span><span class="sxs-lookup"><span data-stu-id="9d178-140">Follow the steps in the RESOLUTION section of Microsoft Knowledge Base article 326155, "Error message when you try to access a Web site in Internet Explorer: "Page Cannot Be Displayed"" available at [http://support.microsoft.com/kb/326155](http://support.microsoft.com/kb/326155).</span></span>  
  
#### <a name="401---access-denied-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a><span data-ttu-id="9d178-141">在 IIS 伺服器上存取網頁時發生「401 – 拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d178-141">"401 - Access denied" error occurs when accessing a Web page on an IIS server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="9d178-142">問題</span><span class="sxs-lookup"><span data-stu-id="9d178-142">Problem</span></span>  
 <span data-ttu-id="9d178-143">當您嘗試存取 IIS 伺服器上的網站時，會出現類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="9d178-143">When you attempt to access a Web page on an IIS server an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="9d178-144">401 - 拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="9d178-144">401 - Access denied</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="9d178-145">原因</span><span class="sxs-lookup"><span data-stu-id="9d178-145">Cause</span></span>  
 <span data-ttu-id="9d178-146">IIS 定義數種不同的 401 錯誤，指示更為特定的錯誤原因。</span><span class="sxs-lookup"><span data-stu-id="9d178-146">IIS defines several different 401 errors that indicate a more specific cause of the error.</span></span> <span data-ttu-id="9d178-147">這些特定的錯誤碼會顯示在瀏覽器中：</span><span class="sxs-lookup"><span data-stu-id="9d178-147">These specific error codes are displayed in the browser:</span></span>  
  
- <span data-ttu-id="9d178-148">401.1 - 未經授權: 因為認證不正確而拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="9d178-148">401.1 - Logon failed.</span></span>  
  
- <span data-ttu-id="9d178-149">401.2 - 登入由於伺服器組態而失敗。</span><span class="sxs-lookup"><span data-stu-id="9d178-149">401.2 - Logon failed due to server configuration.</span></span>  
  
- <span data-ttu-id="9d178-150">401.3 - 未經授權: 因為要求的資源上已設定 ACL 而拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="9d178-150">401.3 - Unauthorized due to ACL on resource.</span></span>  
  
- <span data-ttu-id="9d178-151">401.4 - 未經授權: 網頁伺服器上安裝的篩選器導致授權失敗。</span><span class="sxs-lookup"><span data-stu-id="9d178-151">401.4 - Authorization failed by filter.</span></span>  
  
- <span data-ttu-id="9d178-152">401.5 - 未經授權: ISAPI/CGI 應用程式導致授權失敗。</span><span class="sxs-lookup"><span data-stu-id="9d178-152">401.5 - Authorization failed by ISAPI/CGI application.</span></span>  
  
- <span data-ttu-id="9d178-153">401.7 – 存取已遭 Web 伺服器上的 URL 授權原則拒絕。</span><span class="sxs-lookup"><span data-stu-id="9d178-153">401.7 – Access denied by URL authorization policy on the Web server.</span></span> <span data-ttu-id="9d178-154">這個錯誤碼是 IIS 6.0 特有的。</span><span class="sxs-lookup"><span data-stu-id="9d178-154">This error code is specific to IIS 6.0.</span></span>  
  
  <span data-ttu-id="9d178-155">IIS 7.0 狀態碼的完整清單，請參閱 Microsoft 知識庫文件 943891<iis 「 HTTP 狀態碼 IIS 7.0 中 」，網址[ http://support.microsoft.com/kb/943891 ](http://support.microsoft.com/kb/943891)。</span><span class="sxs-lookup"><span data-stu-id="9d178-155">For a complete list of the IIS 7.0 status codes, see Microsoft Knowledge Base article 943891, "The HTTP status codes in IIS 7.0" available at [http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891).</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="9d178-156">解決方案</span><span class="sxs-lookup"><span data-stu-id="9d178-156">Resolution</span></span>  
 <span data-ttu-id="9d178-157">請依照下列中的步驟[解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)解決 IIS 權限問題。</span><span class="sxs-lookup"><span data-stu-id="9d178-157">Follow the steps in [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) to resolve IIS permissions problems.</span></span>  
  
#### <a name="500---internal-server-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a><span data-ttu-id="9d178-158">在 IIS 伺服器上存取網頁時發生「500 – 內部伺服器錯誤」。</span><span class="sxs-lookup"><span data-stu-id="9d178-158">"500 - Internal server error" occurs when accessing a Web page on an IIS server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="9d178-159">問題</span><span class="sxs-lookup"><span data-stu-id="9d178-159">Problem</span></span>  
 <span data-ttu-id="9d178-160">當您嘗試存取 IIS 伺服器上的網站時，會出現類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="9d178-160">When you attempt to access a Web page on an IIS server an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="9d178-161">500 - 內部伺服器錯誤</span><span class="sxs-lookup"><span data-stu-id="9d178-161">500 - Internal server error</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="9d178-162">原因</span><span class="sxs-lookup"><span data-stu-id="9d178-162">Cause</span></span>  
 <span data-ttu-id="9d178-163">這個錯誤訊息可能是由於各種伺服器端問題所造成。</span><span class="sxs-lookup"><span data-stu-id="9d178-163">This error message can be caused by a wide variety of server-side problems.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="9d178-164">解決方案</span><span class="sxs-lookup"><span data-stu-id="9d178-164">Resolution</span></span>  
 <span data-ttu-id="9d178-165">若要解決這個問題，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9d178-165">To resolve the issue, do the following:</span></span>  
  
- <span data-ttu-id="9d178-166">如需這個錯誤發生原因的詳細資訊，請檢視 IIS 伺服器的應用程式日誌。</span><span class="sxs-lookup"><span data-stu-id="9d178-166">Review the Application log of the IIS server for information about why this error occurs.</span></span>  
  
- <span data-ttu-id="9d178-167">如需有助於判斷錯誤原因的詳細資訊，請檢視 IIS 記錄檔或 HTTPERR 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="9d178-167">Review the IIS log files or HTTPERR log files for information that may be helpful for determining the cause of the error.</span></span> <span data-ttu-id="9d178-168">根據預設，IIS 記錄執行的電腦上的檔案[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]作業系統位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="9d178-168">By default the IIS log files on a computer running [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] operating systems are located in the following directory:</span></span>  
  
   <span data-ttu-id="9d178-169"><em>%Windir%\\</em>system32\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="9d178-169"><em>%WinDir%\\</em>system32\LogFiles\W3SVC1\\</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="9d178-170">*%Windir%* 是在 IIS 伺服器上的 Windows 目錄位置的預留位置。</span><span class="sxs-lookup"><span data-stu-id="9d178-170">*%WinDir%* is a placeholder for the location of the Windows directory on the IIS server.</span></span>  
  
   <span data-ttu-id="9d178-171">根據預設，在執行 Windows Server 2008 或 Windows Vista 的電腦上，IIS 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="9d178-171">By default the IIS log files on a computer running Windows Server 2008 or Windows Vista are located in the following directory:</span></span>  
  
   <span data-ttu-id="9d178-172">C:\inetpub\logs\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="9d178-172">C:\inetpub\logs\LogFiles\W3SVC1\\</span></span>  
  
   <span data-ttu-id="9d178-173">根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上的 HTTPERR 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="9d178-173">By default the HTTPERR log files on [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] are located in the following directory:</span></span>  
  
   <span data-ttu-id="9d178-174"><em>%Windir%</em>system32LogFilesHTTPERR</span><span class="sxs-lookup"><span data-stu-id="9d178-174"><em>%WinDir%</em>system32LogFilesHTTPERR</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="9d178-175">才能使用 HTTPERR 記錄檔才可以使用[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，或 Windows Vista 的電腦。</span><span class="sxs-lookup"><span data-stu-id="9d178-175">The HTTPERR log file is only available on a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], or Windows Vista computer.</span></span>  
  
#### <a name="service-unavailable-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a><span data-ttu-id="9d178-176">在 IIS 伺服器上存取網頁時發生「無法使用服務」錯誤</span><span class="sxs-lookup"><span data-stu-id="9d178-176">"Service Unavailable" error occurs when accessing a Web page on an IIS server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="9d178-177">問題</span><span class="sxs-lookup"><span data-stu-id="9d178-177">Problem</span></span>  
 <span data-ttu-id="9d178-178">當您嘗試存取 IIS 伺服器上的網站時，會出現類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="9d178-178">When you attempt to access a Web page on an IIS server an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="9d178-179">服務無法使用</span><span class="sxs-lookup"><span data-stu-id="9d178-179">Service Unavailable</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="9d178-180">原因</span><span class="sxs-lookup"><span data-stu-id="9d178-180">Cause</span></span>  
 <span data-ttu-id="9d178-181">此錯誤最常見的原因是網頁的應用程式集區 （IIS 6.0 和 IIS 7.0） 已停止。</span><span class="sxs-lookup"><span data-stu-id="9d178-181">The most common cause for this error is that the application pool (IIS 6.0 and IIS 7.0) for the Web page is stopped.</span></span> <span data-ttu-id="9d178-182">使用所指定使用者名稱及/或密碼無效的識別來設定應用程式集區或 COM+ 應用程式時，經常會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d178-182">This commonly occurs if the application pool or COM+ application is configured with an Identity for which the specified user name and or password is invalid.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="9d178-183">解決方案</span><span class="sxs-lookup"><span data-stu-id="9d178-183">Resolution</span></span>  
 <span data-ttu-id="9d178-184">請依照下列主題的 「 設定 IIS 應用程式主機處理序識別 」 一節中的步驟[解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)設定適當的主機處理序身分識別。</span><span class="sxs-lookup"><span data-stu-id="9d178-184">Follow the steps in the "Setting IIS Application Host Process Identity" section of the topic [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) to set the appropriate host process identity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d178-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d178-185">See Also</span></span>  
 [<span data-ttu-id="9d178-186">解決 IIS 權限問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="9d178-186">Guidelines for Resolving IIS Permissions Problems</span></span>](../core/guidelines-for-resolving-iis-permissions-problems.md)