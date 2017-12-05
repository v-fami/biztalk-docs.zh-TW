---
title: "解決 IIS 權限問題的指導方針 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: troubleshooting
ms.assetid: d9793a90-3aa3-46ab-a317-6d1e0fbfc1ef
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb91509ec3ad1c329190c848c25a60434f93499e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="guidelines-for-resolving-iis-permissions-problems"></a><span data-ttu-id="98ab1-102">解決 IIS 權限問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="98ab1-102">Guidelines for Resolving IIS Permissions Problems</span></span>
<span data-ttu-id="98ab1-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在使用 HTTP、SOAP 和 Windows SharePoint Services 配接器時，會大量使用 Microsoft Internet Information Services (IIS) 以提供 Web 服務支援。</span><span class="sxs-lookup"><span data-stu-id="98ab1-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes extensive use of Microsoft Internet Information Services (IIS) for Web services support and for use with the HTTP, SOAP, and Windows SharePoint Services adapters.</span></span>  
  
 <span data-ttu-id="98ab1-104">瞭解 IIS 實作應用程式的方式，將有助於 IIS 權限問題的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="98ab1-104">It is helpful to understand how IIS implements application isolation before troubleshooting IIS permissions problems.</span></span>  
  
 <span data-ttu-id="98ab1-105">IIS 提供相關功能，供您建立 IIS 應用程式，做為在各自記憶體空間中執行的不同主控件程序。</span><span class="sxs-lookup"><span data-stu-id="98ab1-105">IIS provides functionality for creating IIS applications as distinct host processes that are run in their own memory space.</span></span> <span data-ttu-id="98ab1-106">一旦您建立的 IIS 應用程式主機，然後您必須定義兩組權限，IIS 應用程式主機**處理序識別**和 IIS 應用程式主機**使用者存取權限**。</span><span class="sxs-lookup"><span data-stu-id="98ab1-106">Once you create an IIS application host, then you must define two sets of permissions, the IIS application host **process identity** and the IIS application host **user access rights**.</span></span> <span data-ttu-id="98ab1-107">在疑難排解 IIS 權限問題時，您應該檢查這兩組權限。</span><span class="sxs-lookup"><span data-stu-id="98ab1-107">You should examine each of these permissions sets when troubleshooting IIS permissions problems.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98ab1-108">**處理序識別**和**使用者存取權限**也稱為**安全性內容**IIS 應用程式主機處理序。</span><span class="sxs-lookup"><span data-stu-id="98ab1-108">The **process identity** and **user access rights** are also referred to as the **security context** of the IIS application host process.</span></span>  
  
 <span data-ttu-id="98ab1-109">本主題描述如何設定**處理序識別**和**使用者存取權限**IIS 應用程式主機處理程序，並提供解決 IIS 權限問題的一些一般指導方針。</span><span class="sxs-lookup"><span data-stu-id="98ab1-109">This topic describes how to set **process identity** and **user access rights** for an IIS application host process and gives some general guidelines for resolving IIS permissions problems.</span></span>  
  
## <a name="setting-iis-application-host-process-identity"></a><span data-ttu-id="98ab1-110">設定 IIS 應用程式主控件程序識別</span><span class="sxs-lookup"><span data-stu-id="98ab1-110">Setting IIS Application Host Process Identity</span></span>  
 <span data-ttu-id="98ab1-111">IIS 應用程式主控件程序的組態可能會隨著主控件程序所提供的功能層級而有所差異。</span><span class="sxs-lookup"><span data-stu-id="98ab1-111">Configuration of an IIS application host process can vary depending on the level of functionality being served by the host process.</span></span> <span data-ttu-id="98ab1-112">例如，只提供靜態 HTML 頁面的 IIS 應用程式主控件程序，其組態通常與提供 ASP 頁面或 ASP.NET 應用程式的 IIS 應用程式主控件程序不同。</span><span class="sxs-lookup"><span data-stu-id="98ab1-112">For example, an IIS application host process that only serves static HTML pages is typically configured differently than an IIS application host process that serves ASP pages or ASP.NET applications.</span></span>  
  
 <span data-ttu-id="98ab1-113">IIS 應用程式主控件程序的組態也會隨著裝載應用程式的 IIS 版本而改變。</span><span class="sxs-lookup"><span data-stu-id="98ab1-113">Configuration of an IIS application host process also varies depending on the version of IIS that is hosting the application.</span></span> <span data-ttu-id="98ab1-114">Windows Server 2008 (IIS 7.0) 上執行之應用程式的主控件程序識別，是由與應用程式相關聯之應用程式集區的識別來管理。</span><span class="sxs-lookup"><span data-stu-id="98ab1-114">The host process identity of applications running on Windows Server 2008 (IIS 7.0) is governed by the identity of the application pool associated with the application.</span></span>  
  
### <a name="setting-iis-process-identity-for-iis-70-on-windows-server-2008-or-windows-vista"></a><span data-ttu-id="98ab1-115">設定 Windows Server 2008 或 Windows Vista 上 IIS 7.0 的 IIS 程序識別</span><span class="sxs-lookup"><span data-stu-id="98ab1-115">Setting IIS Process Identity for IIS 7.0 on Windows Server 2008 or Windows Vista</span></span>  
  
1.  <span data-ttu-id="98ab1-116">按一下**啟動**，然後**所有程式**，然後按一下**Internet Information Services (IIS) 7 Manager**。</span><span class="sxs-lookup"><span data-stu-id="98ab1-116">Click **Start**, then **All Programs**, and click **Internet Information Services (IIS) 7 Manager**.</span></span>  
  
2.  <span data-ttu-id="98ab1-117">在 [網際網路資訊服務 (IIS) 管理員] 中，展開*\<電腦名稱\>***（使用者帳戶）**按一下**應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="98ab1-117">In Internet Information Services (IIS) Manager, expand *\<computer name\>***(User account)** and click **Application Pools**.</span></span>  
  
3.  <span data-ttu-id="98ab1-118">以滑鼠右鍵按一下應用程式集區，然後按一下**檢視應用程式**以查看應用程式集區相關聯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="98ab1-118">Right-click an application pool and click **View Applications** to see the applications associated with the application pool.</span></span>  
  
4.  <span data-ttu-id="98ab1-119">以滑鼠右鍵按一下應用程式集區，然後按一下**進階設定**顯示應用程式集區的 [進階設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="98ab1-119">Right-click an application pool and click **Advanced Settings** to display the Advanced Settings dialog for the application pool.</span></span>  
  
5.  <span data-ttu-id="98ab1-120">依序按一下省略符號 （...） 按鈕旁的 修改應用程式集區身分識別**識別**下**處理序模型**區段**進階設定**對話方塊方塊。</span><span class="sxs-lookup"><span data-stu-id="98ab1-120">Modify the identity for the application pool by clicking the ellipsis (…) button next to **Identity** under the **Process Model** section of the **Advanced Settings** dialog box.</span></span>  
  
## <a name="setting-user-access-rights-for-the-iis-server"></a><span data-ttu-id="98ab1-121">設定 IIS 伺服器的使用者存取權限</span><span class="sxs-lookup"><span data-stu-id="98ab1-121">Setting User Access Rights for the IIS Server</span></span>  
 <span data-ttu-id="98ab1-122">程序識別會控管執行中 IIS 應用程式主控件程序可以使用的資訊安全內容，而使用者存取權限則會針對實際存取提供之網頁的帳戶，控制其資訊安全內容。</span><span class="sxs-lookup"><span data-stu-id="98ab1-122">While process identity governs the security context available to the running IIS application host process, user access permissions govern the security context for the account that is actually accessing the Web page(s) being served.</span></span> <span data-ttu-id="98ab1-123">您必須正確設定這兩種資訊安全內容，才能避免權限錯誤。</span><span class="sxs-lookup"><span data-stu-id="98ab1-123">Permissions must be set appropriately for both security contexts to avoid permissions errors.</span></span>  
  
 <span data-ttu-id="98ab1-124">IIS 7.0 支援下列使用者驗證方法：</span><span class="sxs-lookup"><span data-stu-id="98ab1-124">IIS 7.0 supports the following user authentication methods:</span></span>  
  
-   <span data-ttu-id="98ab1-125">**匿名存取：**可讓使用者建立匿名連線。</span><span class="sxs-lookup"><span data-stu-id="98ab1-125">**Anonymous access:** Allows users to establish an anonymous connection.</span></span> <span data-ttu-id="98ab1-126">IIS 伺服器會以指定的訪客帳戶來登入使用者。</span><span class="sxs-lookup"><span data-stu-id="98ab1-126">The IIS server logs on the user with the specified guest account.</span></span>  
  
-   <span data-ttu-id="98ab1-127">**ASP.NET 模擬**允許應用程式在其中兩個不同內容中執行： 由 IIS 驗證的使用者或您設定的任意帳戶。</span><span class="sxs-lookup"><span data-stu-id="98ab1-127">**ASP.NET Impersonation** Allows an application to run in one of two different contexts: either as the user authenticated by IIS or as an arbitrary account that you set up.</span></span>  
  
-   <span data-ttu-id="98ab1-128">**基本驗證：**純文字、 未加密的形式在網路上傳輸密碼。</span><span class="sxs-lookup"><span data-stu-id="98ab1-128">**Basic authentication:** Transmits passwords across the network in plaintext, an unencrypted form.</span></span>  
  
-   <span data-ttu-id="98ab1-129">**摘要式驗證：**只適用於 Active Directory 帳戶，傳送透過網路，而不是純文字密碼的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="98ab1-129">**Digest authentication:** Works only with Active Directory accounts, sending a hash value over the network, rather than a plaintext password.</span></span> <span data-ttu-id="98ab1-130">摘要式驗證可跨 Proxy 伺服器和其他防火牆運作，而且可在「網路分散式撰寫及版本處理」(WebDAV) 目錄上使用。</span><span class="sxs-lookup"><span data-stu-id="98ab1-130">Digest authentication works across proxy servers and other firewalls and is available on Web Distributed Authoring and Versioning (WebDAV) directories.</span></span> <span data-ttu-id="98ab1-131">使用摘要式驗證需要先停用匿名驗證。</span><span class="sxs-lookup"><span data-stu-id="98ab1-131">Use of Digest authentication requires that Anonymous authentication is disabled first.</span></span>  
  
-   <span data-ttu-id="98ab1-132">**表單驗證**Accommodates 高流量網站或公用伺服器上的應用程式的驗證。</span><span class="sxs-lookup"><span data-stu-id="98ab1-132">**Forms Authentication** Accommodates authentication for high-traffic sites or applications on public servers.</span></span> <span data-ttu-id="98ab1-133">表單驗證可讓您管理應用程式層級的用戶端登錄與驗證，而非依賴作業系統提供的驗證機制。</span><span class="sxs-lookup"><span data-stu-id="98ab1-133">Forms authentication lets you manage client registration and authentication at the application level, instead of relying on the authentication mechanisms provided by the operating system.</span></span>  
  
-   <span data-ttu-id="98ab1-134">**Windows 驗證：**使用驗證來驗證用戶端連線在 Windows 網域上的。</span><span class="sxs-lookup"><span data-stu-id="98ab1-134">**Windows authentication:** Uses authentication on your Windows domain to authenticate client connections.</span></span>  
  
#### <a name="to-set-user-access-rights-for-a-virtual-directory-in-iis-70"></a><span data-ttu-id="98ab1-135">若要在 IIS 7.0 中設定虛擬目錄的使用者存取權限</span><span class="sxs-lookup"><span data-stu-id="98ab1-135">To set user access rights for a virtual directory in IIS 7.0</span></span>  
  
1.  <span data-ttu-id="98ab1-136">在 [網際網路資訊服務 (IIS) 管理員] 中，展開*\<電腦名稱\>*，**網站**，和**Default Web Site**中**連線**窗格。</span><span class="sxs-lookup"><span data-stu-id="98ab1-136">In the Internet Information Services (IIS) Manager, expand *\<computer name\>*, **Sites**, and **Default Web Site** in the **Connections** pane.</span></span>  
  
2.  <span data-ttu-id="98ab1-137">按一下以選取的虛擬目錄，並按一下**功能檢視**底端的工作區窗格中列出的虛擬目錄的可設定功能。</span><span class="sxs-lookup"><span data-stu-id="98ab1-137">Click to select the virtual directory and click the **Features View** at the bottom of the Workspace pane to list the configurable features for the virtual directory.</span></span>  
  
3.  <span data-ttu-id="98ab1-138">按兩下**驗證**列出虛擬目錄已啟用的驗證方法的工作區 窗格中的功能。</span><span class="sxs-lookup"><span data-stu-id="98ab1-138">Double-click the **Authentication** feature in the Workspace pane to list the authentication methods that are enabled for the virtual directory.</span></span>  
  
4.  <span data-ttu-id="98ab1-139">按一下以選取您想要啟用或停用，然後按一下 驗證方法**停用**或**啟用**中**動作**窗格的 IIS 管理員。</span><span class="sxs-lookup"><span data-stu-id="98ab1-139">Click to select the authentication method that you would like to enable or disable and click either **Disable** or **Enable** in the **Actions** pane of the IIS Manager.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="98ab1-140">如果**啟用匿名存取**已啟用，IIS 會設定使用者存取權限為已設定匿名使用者識別之前設定的任何其他使用者存取權限啟用驗證方法。</span><span class="sxs-lookup"><span data-stu-id="98ab1-140">If **Enable anonymous access** is enabled, IIS will set user access rights as the configured Anonymous user identity before setting user access rights with any other enabled authentication methods.</span></span>  
    >   
    >  <span data-ttu-id="98ab1-141">若要設定匿名使用者識別，以滑鼠右鍵按一下**匿名驗證**方法，然後按一下**編輯**顯示**編輯匿名驗證認證**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="98ab1-141">To configure the Anonymous user identity, right-click the **Anonymous Authentication** method and click **Edit** to display the **Edit Anonymous Authentication Credentials** dialog.</span></span>  
  
## <a name="general-guidelines-for-resolving-iis-permissions-problems"></a><span data-ttu-id="98ab1-142">解決 IIS 權限問題的一般指導方針</span><span class="sxs-lookup"><span data-stu-id="98ab1-142">General Guidelines for Resolving IIS Permissions Problems</span></span>  
 <span data-ttu-id="98ab1-143">請依照下列步驟來進行 IIS 權限的疑難排解：</span><span class="sxs-lookup"><span data-stu-id="98ab1-143">Follow these steps to troubleshoot IIS permissions:</span></span>  
  
1.  <span data-ttu-id="98ab1-144">檢查 IIS 伺服器電腦的應用程式記錄中是否記載發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="98ab1-144">Check the application log of the IIS Server computer for errors.</span></span>  
  
2.  <span data-ttu-id="98ab1-145">請依照[IIS 7.0： 設定 IIS 7.0 中的失敗要求追蹤](http://go.microsoft.com/fwlink/?LinkId=130600)疑難排解 IIS 7.0 電腦上的權限問題。</span><span class="sxs-lookup"><span data-stu-id="98ab1-145">Follow the steps in [IIS 7.0: Configuring Tracing for Failed Requests in IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=130600) to troubleshoot permissions problems on IIS 7.0 computers.</span></span>  
  
3.  <span data-ttu-id="98ab1-146">檢查 IIS 伺服器的 IIS 記錄檔是否記載 HTTP 401 錯誤。</span><span class="sxs-lookup"><span data-stu-id="98ab1-146">Check the IIS log files of the IIS server for HTTP 401 errors.</span></span>  
  
     <span data-ttu-id="98ab1-147">根據預設，在執行 Windows Server 2008 或 Windows Vista 的電腦上，IIS 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="98ab1-147">By default the IIS log files on a computer running Windows Server 2008 or Windows Vista are located in the following directory:</span></span>  
  
     <span data-ttu-id="98ab1-148">C:\inetpub\logs\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="98ab1-148">C:\inetpub\logs\LogFiles\W3SVC1\\</span></span>  
  
    -   <span data-ttu-id="98ab1-149">如果 IIS 記錄檔的 IIS 7.0 電腦包含 HTTP 401 錯誤，遵循 Microsoft 知識庫文件 943891 中的步驟，「 HTTP 狀態碼 IIS 7.0 中 「 位於[http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891)判斷子狀態碼，並依據狀態碼的權限問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="98ab1-149">If the IIS log file for an IIS 7.0 computer contains HTTP 401 errors, follow the steps in Microsoft Knowledge Base article 943891, "The HTTP status codes in IIS 7.0" available at [http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891) to determine the substatus code and to troubleshoot the permissions problem based on the status code.</span></span>  
  
    -   <span data-ttu-id="98ab1-150">檢查值**cs-username**與 HTTP 401 錯誤相關聯的欄位。</span><span class="sxs-lookup"><span data-stu-id="98ab1-150">Check the value of the **cs-username** field associated with the HTTP 401 error.</span></span> <span data-ttu-id="98ab1-151">此欄位包含存取 IIS 伺服器的已驗證使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="98ab1-151">This field contains the name of the authenticated user who accessed the IIS server.</span></span> <span data-ttu-id="98ab1-152">此欄位以連字號 (-) 代表匿名使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="98ab1-152">The anonymous user account is represented by a hyphen (-) in this field.</span></span> <span data-ttu-id="98ab1-153">請確定這個帳戶是否擁有適當資源的權限。</span><span class="sxs-lookup"><span data-stu-id="98ab1-153">Ensure that this account has permissions on the appropriate resources.</span></span>  
  
4.  <span data-ttu-id="98ab1-154">確認是否已正確設定 IIS 應用程式主控件程序使用的程序識別認證，以及該帳戶是否擁有適當的權限。</span><span class="sxs-lookup"><span data-stu-id="98ab1-154">Verify that the process identity credentials used by the IIS application host process are set correctly and that the account has the appropriate permissions.</span></span> <span data-ttu-id="98ab1-155">如果用於程序識別的帳戶沒有足夠權限，則請變更帳戶或授與該帳戶適當的權限。</span><span class="sxs-lookup"><span data-stu-id="98ab1-155">If the account used for the process identity has insufficient permissions then either change the account or grant the account the appropriate permissions.</span></span>  
  
5.  <span data-ttu-id="98ab1-156">使用中所述的 RegMon 和 FileMon 公用程式[工具和公用程式，以供疑難排解使用](../core/tools-and-utilities-to-use-for-troubleshooting.md)診斷檔案或登錄存取權限問題。</span><span class="sxs-lookup"><span data-stu-id="98ab1-156">Use the RegMon and FileMon utilities described in [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) to diagnose file or registry access permissions problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ab1-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="98ab1-157">See Also</span></span>  
 <span data-ttu-id="98ab1-158">[疑難排解 BizTalk Server 權限](../core/troubleshooting-biztalk-server-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="98ab1-158">[Troubleshooting BizTalk Server Permissions](../core/troubleshooting-biztalk-server-permissions.md) </span></span>  
 [<span data-ttu-id="98ab1-159">IIS 7.0： 在 IIS 7.0 中設定驗證</span><span class="sxs-lookup"><span data-stu-id="98ab1-159">IIS 7.0: Configuring Authentication in IIS 7.0</span></span>](http://go.microsoft.com/fwlink/?LinkId=129909)