---
title: "保護配接器的最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, security
- best practices, adapters
- adapters, permissions
- security, adapters
- permissions, adapters
- best practices, security
- adapters, best practices
ms.assetid: 004e1a01-b316-4eee-967f-5a806431de2b
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86abbba06e851b9b289b29cd7fbbf01b3af292a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-securing-adapters"></a><span data-ttu-id="c23fc-102">保護配接器安全的最佳作法</span><span class="sxs-lookup"><span data-stu-id="c23fc-102">Best Practices for Securing Adapters</span></span>
<span data-ttu-id="c23fc-103">本主題提供配接器安全性的最佳作法清單。</span><span class="sxs-lookup"><span data-stu-id="c23fc-103">This topic provides a list of best practices for adapter security.</span></span>  
  
 <span data-ttu-id="c23fc-104">**請勿在您的電腦上安裝不受信任的配接器請只使用認證配接器開發夥伴。**</span><span class="sxs-lookup"><span data-stu-id="c23fc-104">**Do not install untrusted adapters on your computer; use only certified adapter development partners.**</span></span>  
  
 <span data-ttu-id="c23fc-105">**不要將敏感的顧客資料儲存預設配接器結構描述中。**</span><span class="sxs-lookup"><span data-stu-id="c23fc-105">**Do not store sensitive customer data in the default adapter schema.**</span></span>  
  
 <span data-ttu-id="c23fc-106">您應該只在部署配接器後設定使用者名稱及密碼資訊。</span><span class="sxs-lookup"><span data-stu-id="c23fc-106">You should configure the user name and password information only after you deploy an adapter.</span></span> <span data-ttu-id="c23fc-107">這樣做可確保資訊會儲存在 SSO 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c23fc-107">This ensures that the information gets stored in the SSO database.</span></span> <span data-ttu-id="c23fc-108">如需 SSO 資料庫的詳細資訊，請參閱[使用 SSO](../core/using-sso.md)。</span><span class="sxs-lookup"><span data-stu-id="c23fc-108">For more information about the SSO database, see [Using SSO](../core/using-sso.md).</span></span>  
  
 <span data-ttu-id="c23fc-109">**授與共用資料夾 （接收資料夾和傳送資料夾），可用來拾取及放置檔案使用 File 及 EDI 配接器上的下列權限：**</span><span class="sxs-lookup"><span data-stu-id="c23fc-109">**Grant the following permissions on the shared folders (the Receive folder and Send folder) that are used to pick up and drop files using the File and EDI adapters:**</span></span>  
  
-   <span data-ttu-id="c23fc-110">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="c23fc-110">**Receive  folder**</span></span>  
  
     <span data-ttu-id="c23fc-111">可以在接收位置設定 FILE 配接器的接收資料夾。</span><span class="sxs-lookup"><span data-stu-id="c23fc-111">The receive folder for the File adapter is configurable on the receive location.</span></span> <span data-ttu-id="c23fc-112">可以在接收處理常式設定 EDI 配接器的接收資料夾。</span><span class="sxs-lookup"><span data-stu-id="c23fc-112">The receive folder for the EDI adapter is configurable on the receive handler.</span></span> <span data-ttu-id="c23fc-113">拾取檔案之 BizTalk 主控件的服務帳戶，在檔案系統層級應該具有以下權限：</span><span class="sxs-lookup"><span data-stu-id="c23fc-113">The service account for the BizTalk Host that picks up the file should have the following permissions at the file-system level:</span></span>  
  
    -   <span data-ttu-id="c23fc-114">清單資料夾 / 讀取資料</span><span class="sxs-lookup"><span data-stu-id="c23fc-114">List Folder / Read Data</span></span>  
  
    -   <span data-ttu-id="c23fc-115">刪除子資料夾和檔案</span><span class="sxs-lookup"><span data-stu-id="c23fc-115">Delete SubFolder and Files</span></span>  
  
     <span data-ttu-id="c23fc-116">若接收資料夾位於網路共用上，在檔案共用層級必須授與以下權限：</span><span class="sxs-lookup"><span data-stu-id="c23fc-116">If the receive folder is on a network share, the following permissions must be granted at the file-share level:</span></span>  
  
    -   <span data-ttu-id="c23fc-117">拾取檔案之 BizTalk 主控件的服務帳戶，必須具有「完整控制」權限。</span><span class="sxs-lookup"><span data-stu-id="c23fc-117">The service account for the BizTalk Host that picks up the file must have Full Control permissions.</span></span>  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c23fc-118"> 系統管理員必須具有「完整控制」權限才能進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="c23fc-118"> administrators must have Full Control permissions for troubleshooting.</span></span>  
  
    -   <span data-ttu-id="c23fc-119">放置檔案至此位置的外部使用者或程式必須具有「寫入」權限。</span><span class="sxs-lookup"><span data-stu-id="c23fc-119">The external user or programs that drop files to this location must have Write permissions.</span></span>  
  
-   <span data-ttu-id="c23fc-120">**傳送資料夾**</span><span class="sxs-lookup"><span data-stu-id="c23fc-120">**Send folder**</span></span>  
  
     <span data-ttu-id="c23fc-121">可以在傳送埠設定 FILE 及 EDI 配接器的傳送資料夾。</span><span class="sxs-lookup"><span data-stu-id="c23fc-121">The send folder for the File and EDI adapters are configurable on the send port.</span></span>  
  
    -   <span data-ttu-id="c23fc-122">放置檔案之 BizTalk 主控件的服務帳戶，必須具有「寫入」權限。</span><span class="sxs-lookup"><span data-stu-id="c23fc-122">The service account for the BizTalk Host or Hosts that drop files here must have Write permissions.</span></span>  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c23fc-123"> 系統管理員必須具有「完整控制」權限。</span><span class="sxs-lookup"><span data-stu-id="c23fc-123"> administrators must have Full Control permissions.</span></span>  
  
    -   <span data-ttu-id="c23fc-124">拾取檔案的外部使用者或程式必須具有「讀取」權限。</span><span class="sxs-lookup"><span data-stu-id="c23fc-124">The external user or program that picks up files must have Read permissions.</span></span>  
  
 <span data-ttu-id="c23fc-125">**新增 EDI 服務執行 BTS_HOST_USERS SQL 角色的使用者帳戶。**</span><span class="sxs-lookup"><span data-stu-id="c23fc-125">**Add the user account under which the EDI service is running to the BTS_HOST_USERS SQL role.**</span></span>  
  
 <span data-ttu-id="c23fc-126">這是必要步驟，如此一來，您不需要管理權限也可取得 BizTalk 總管物件管理 (OM) 存取權。</span><span class="sxs-lookup"><span data-stu-id="c23fc-126">This is required so that you can obtain BizTalk Explorer Object Management (OM) Access without administrative permissions.</span></span> <span data-ttu-id="c23fc-127">若要執行這個程序，請將「EDI 子系統使用者」新增到 BizTalk 管理資料庫 (BizTalkMgmtDb) 中的 BTS_HOST_USERS 角色。</span><span class="sxs-lookup"><span data-stu-id="c23fc-127">To do this, add "EDI Subsystem Users" to the BTS_HOST_USERS role in the BizTalk Management database, BizTalkMgmtDb.</span></span>  
  
 <span data-ttu-id="c23fc-128">若要將 「 EDI 子系統使用者 」 加入至 SQL Server 2005 上的 BTS_HOST_USERS 角色，完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c23fc-128">To add "EDI Subsystem Users" to the BTS_HOST_USERS role on SQL Server 2005, complete the following steps:</span></span>  
  
1.  <span data-ttu-id="c23fc-129">啟動 SQL Server Management Studio 從**開始時，程式，Microsoft SQL Server 2008**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-129">Launch SQL Server Management Studio from **Start, Programs, Microsoft SQL Server 2008**.</span></span>  
  
2.  <span data-ttu-id="c23fc-130">連接到裝載 BizTalk 管理資料庫的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="c23fc-130">Connect to the SQL Server that houses your BizTalk Management database.</span></span>  
  
3.  <span data-ttu-id="c23fc-131">在 [物件總管] 中展開此伺服器。</span><span class="sxs-lookup"><span data-stu-id="c23fc-131">Expand this server in the Object Explorer.</span></span>  
  
4.  <span data-ttu-id="c23fc-132">展開**資料庫**，然後展開 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="c23fc-132">Expand **Databases**, and then expand the BizTalk Management database.</span></span>  
  
5.  <span data-ttu-id="c23fc-133">展開**安全性**，依序展開**角色**，然後按一下以選取**資料庫角色**</span><span class="sxs-lookup"><span data-stu-id="c23fc-133">Expand **Security**, expand **Roles**, and then click to select **Database Roles**</span></span>  
  
6.  <span data-ttu-id="c23fc-134">在詳細資料窗格中，以滑鼠右鍵按一下 BTS_HOST_USERS 角色，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-134">In the details pane, right-click the BTS_HOST_USERS role, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="c23fc-135">在 BTS_HOST_USERS 對話方塊中，按一下**新增**，按一下 **瀏覽**，然後核取方塊，將它加入到 EDI 子系統使用者群組的旁邊。</span><span class="sxs-lookup"><span data-stu-id="c23fc-135">In the BTS_HOST_USERS dialog box, click **Add**, click **Browse**, and then check the box next to the EDI Subsystem Users group to add it.</span></span>  
  
     <span data-ttu-id="c23fc-136">若使用者清單中沒有可新增的「EDI 子系統使用者」群組，您必須將「EDI 子系統使用者」群組當作新資料庫使用者新增到 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="c23fc-136">If the EDI Subsystem Users group is not available in the list of users to add, you must add the EDI Subsystem Users group as a new database user to the BizTalk Management database.</span></span> <span data-ttu-id="c23fc-137">若要將「EDI 子系統使用者」群組新增成為新的資料庫使用者，請在 SQL Server Management Studio 中完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c23fc-137">To add the EDI Subsystem Users group as a new database user, complete the following steps in SQL Server Management Studio:</span></span>  
  
    1.  <span data-ttu-id="c23fc-138">展開 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="c23fc-138">Expand the BizTalk Management database.</span></span>  
  
    2.  <span data-ttu-id="c23fc-139">展開**安全性**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-139">Expand **Security**.</span></span>  
  
    3.  <span data-ttu-id="c23fc-140">以滑鼠右鍵按一下**使用者**按一下**新使用者**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-140">Right-click **Users** and click **New User**.</span></span>  
  
    4.  <span data-ttu-id="c23fc-141">按一下省略符號 （...） 按鈕旁的文字方塊**登入名稱**顯示**選取登入** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c23fc-141">Click the ellipses (…) button next to the text box for **Login name** to display the **Select Login** dialog box.</span></span>  
  
    5.  <span data-ttu-id="c23fc-142">按一下瀏覽按鈕中，輸入**EDI 子系統使用者**群組，然後再按一下**[確定]。**</span><span class="sxs-lookup"><span data-stu-id="c23fc-142">Click the Browse button, enter the **EDI Subsystem Users** group, and then click **OK.**</span></span> <span data-ttu-id="c23fc-143">如果系統提示**找到多個物件**對話方塊中，選取**EDI 子系統使用者**登入並按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-143">If prompted with the **Multiple Objects Found** dialog box, select the **EDI Subsystem Users** login and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="c23fc-144">上**資料庫使用者-新增**對話方塊中輸入**EDI 子系統使用者**如**使用者名稱**文字方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-144">On the **Database User - New** dialog box enter **EDI Subsystem Users** for the **User name** textbox and click **OK**.</span></span>  
  
 <span data-ttu-id="c23fc-145">**新增 BizTalk 服務執行 EDI 子系統使用者群組的使用者帳戶。**</span><span class="sxs-lookup"><span data-stu-id="c23fc-145">**Add the user account under which the BizTalk service is running to the EDI Subsystem Users group.**</span></span>  
  
 <span data-ttu-id="c23fc-146">請依照下列步驟執行，新增 BizTalk 服務的使用者帳戶到「EDI 子系統使用者」群組中。</span><span class="sxs-lookup"><span data-stu-id="c23fc-146">Follow these steps to add the user account for the BizTalk service to the EDI Subsystem Users group.</span></span>  
  
-   <span data-ttu-id="c23fc-147">**如果 BizTalk Server 設定為使用網域群組：**</span><span class="sxs-lookup"><span data-stu-id="c23fc-147">**If BizTalk Server is configured to use domain groups:**</span></span>  
  
    1.  <span data-ttu-id="c23fc-148">請在網域中登入 Windows Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="c23fc-148">Logon to a Windows Server computer in the domain.</span></span>  
  
    2.  <span data-ttu-id="c23fc-149">按一下**啟動**，按一下 **所有程式**，按一下 **系統管理工具**，然後按一下  **Active Directory 使用者和電腦**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-149">Click **Start**, click **All Programs**, click **Administrative Tools**, and then click **Active Directory Users and Computers**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="c23fc-150">您必須擁有適當的網域層級權限來修改物件中的**Active Directory 使用者和電腦**介面。</span><span class="sxs-lookup"><span data-stu-id="c23fc-150">You must have appropriate domain level permissions to modify objects in the **Active Directory Users and Computers** interface.</span></span>  
  
    3.  <span data-ttu-id="c23fc-151">按一下以展開網域容器，然後按一下以展開**使用者**容器。</span><span class="sxs-lookup"><span data-stu-id="c23fc-151">Click to expand the domain container and click to expand the **Users** container.</span></span>  
  
    4.  <span data-ttu-id="c23fc-152">按兩下  **EDI 子系統使用者**群組以顯示此群組的內容。</span><span class="sxs-lookup"><span data-stu-id="c23fc-152">Double click the **EDI Subsystem Users** group to display the properties for this group.</span></span>  
  
    5.  <span data-ttu-id="c23fc-153">按一下**成員** 索引標籤**EDI 子系統使用者**群組 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c23fc-153">Click the **Members** tab of the **EDI Subsystem Users** group dialog.</span></span>  
  
    6.  <span data-ttu-id="c23fc-154">按一下**新增** 按鈕，將 BizTalk 服務的使用者帳戶新增到此群組。</span><span class="sxs-lookup"><span data-stu-id="c23fc-154">Click the **Add** button to add the user account for the BizTalk Service to this group.</span></span>  
  
    7.  <span data-ttu-id="c23fc-155">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-155">Click **OK**.</span></span>  
  
-   <span data-ttu-id="c23fc-156">**如果 BizTalk Server 設定為使用本機群組：**</span><span class="sxs-lookup"><span data-stu-id="c23fc-156">**If BizTalk Server is configured to use local groups:**</span></span>  
  
    1.  <span data-ttu-id="c23fc-157">請登入 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="c23fc-157">Logon to the BizTalk Server.</span></span>  
  
    2.  <span data-ttu-id="c23fc-158">按一下**啟動**，按一下 **所有程式**，按一下 **系統管理工具**，然後按一下 **電腦管理**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-158">Click **Start**, click **All Programs**, click **Administrative Tools**, and then click **Computer Management**.</span></span>  
  
    3.  <span data-ttu-id="c23fc-159">按一下以展開**系統工具**，按一下以展開**本機使用者和群組**，然後按一下以展開**群組**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-159">Click to expand **System Tools**, click to expand **Local Users and Groups**, and click to expand **Groups**.</span></span>  
  
    4.  <span data-ttu-id="c23fc-160">按兩下  **EDI 子系統使用者**群組以顯示此群組的內容。</span><span class="sxs-lookup"><span data-stu-id="c23fc-160">Double click the **EDI Subsystem Users** group to display the properties for this group.</span></span>  
  
    5.  <span data-ttu-id="c23fc-161">按一下**新增**按鈕，將 BizTalk 服務的使用者帳戶加入到此群組。</span><span class="sxs-lookup"><span data-stu-id="c23fc-161">Click the **Add** button to add the user account for the BizTalk service to this group.</span></span>  
  
    6.  <span data-ttu-id="c23fc-162">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c23fc-162">Click **OK**.</span></span>