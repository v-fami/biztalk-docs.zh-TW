---
title: "如何管理密碼同步化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], applications
- Password Synchronization [SSO], notifications
- applications, Password Synchronization [SSO]
- SSOPS command line utility [SSO]
- administering, Password Synchronization [SSO]
- Password Synchronization [SSO], adapters
- Password Synchronization [SSO], administering
- notifications [SSO]
- Password Synchronization [SSO], SSOPS command line utility
ms.assetid: e5568cc2-7530-452c-9902-d7ffcad66088
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddd696da8b4cab24a8de6a4b5d8ac8f26856f7e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-administer-password-synchronization"></a><span data-ttu-id="e908d-102">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="e908d-102">How to Administer Password Synchronization</span></span>
<span data-ttu-id="e908d-103">您可以透過 MMC 嵌入式管理單元或命令列來管理「密碼同步」。</span><span class="sxs-lookup"><span data-stu-id="e908d-103">You can administer Password Synchronization through either the MMC Snap-In or the command line.</span></span>  
  
 <span data-ttu-id="e908d-104">MMC 嵌入式管理單元會顯示配接器清單及其屬性。</span><span class="sxs-lookup"><span data-stu-id="e908d-104">The MMC Snap-In displays a list of adapters and their properties.</span></span> <span data-ttu-id="e908d-105">您可使用滑鼠右鍵按一下配接器，再使用功能表來執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e908d-105">You can right-click an adapter and use the menu to perform the following commands:</span></span>  
  
-   <span data-ttu-id="e908d-106">建立配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-106">Create adapters</span></span>  
  
-   <span data-ttu-id="e908d-107">設定屬性</span><span class="sxs-lookup"><span data-stu-id="e908d-107">Set properties</span></span>  
  
-   <span data-ttu-id="e908d-108">Update</span><span class="sxs-lookup"><span data-stu-id="e908d-108">Update</span></span>  
  
-   <span data-ttu-id="e908d-109">DELETE</span><span class="sxs-lookup"><span data-stu-id="e908d-109">Delete</span></span>  
  
-   <span data-ttu-id="e908d-110">啟用</span><span class="sxs-lookup"><span data-stu-id="e908d-110">Enable</span></span>  
  
-   <span data-ttu-id="e908d-111">Disable</span><span class="sxs-lookup"><span data-stu-id="e908d-111">Disable</span></span>  
  
-   <span data-ttu-id="e908d-112">新增應用程式至配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-112">Add applications to an adapter</span></span>  
  
-   <span data-ttu-id="e908d-113">從配接器刪除應用程式</span><span class="sxs-lookup"><span data-stu-id="e908d-113">Delete applications from an adapter</span></span>  
  
-   <span data-ttu-id="e908d-114">重設通知</span><span class="sxs-lookup"><span data-stu-id="e908d-114">Reset notification</span></span>  
  
-   <span data-ttu-id="e908d-115">新增配接器至配接器群組</span><span class="sxs-lookup"><span data-stu-id="e908d-115">Add an adapter to an adapter group</span></span>  
  
-   <span data-ttu-id="e908d-116">從配接器群組刪除配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-116">Delete an adapter from an adapter group</span></span>  
  
 <span data-ttu-id="e908d-117">您也可以使用 SSOPS 命令列公用程式來管理您的密碼同步。</span><span class="sxs-lookup"><span data-stu-id="e908d-117">You can also use the SSOPS command line utility to administer your password synchronization.</span></span> <span data-ttu-id="e908d-118">本節中的大部分命令僅供系統管理員使用。</span><span class="sxs-lookup"><span data-stu-id="e908d-118">Most of commands in this section are intended for use by an administrator only.</span></span>  
  
 <span data-ttu-id="e908d-119">對大部分命令而言，命令輸出會在畫面上顯示為兩欄。</span><span class="sxs-lookup"><span data-stu-id="e908d-119">For many commands, the command output is displayed on the screen in two columns.</span></span> <span data-ttu-id="e908d-120">因為特定畫面設定可能導致資料被截斷，為求最佳效果，您應將畫面緩衝區大小/Windows 大小變更為 120 個字元。</span><span class="sxs-lookup"><span data-stu-id="e908d-120">As certain screen settings may cause truncation of data, for best results you should change the screen buffer size/Windows size to 120 characters.</span></span>  
  
 <span data-ttu-id="e908d-121">SSOPS 命令列示在下表中。</span><span class="sxs-lookup"><span data-stu-id="e908d-121">The SSOPS commands are listed in the following table.</span></span> <span data-ttu-id="e908d-122">程序和進一步的說明位於本主題其他部分。</span><span class="sxs-lookup"><span data-stu-id="e908d-122">Procedures and further explanation are located throughout the rest of this topic.</span></span>  
  
|<span data-ttu-id="e908d-123">Command</span><span class="sxs-lookup"><span data-stu-id="e908d-123">Command</span></span>|<span data-ttu-id="e908d-124">函數</span><span class="sxs-lookup"><span data-stu-id="e908d-124">Function</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="e908d-125">-list</span><span class="sxs-lookup"><span data-stu-id="e908d-125">-list</span></span>|<span data-ttu-id="e908d-126">列出現有的配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-126">Lists existing adapters</span></span>|  
|<span data-ttu-id="e908d-127">-display</span><span class="sxs-lookup"><span data-stu-id="e908d-127">-display</span></span>|<span data-ttu-id="e908d-128">顯示配接器資訊</span><span class="sxs-lookup"><span data-stu-id="e908d-128">Displays adapter information</span></span>|  
|<span data-ttu-id="e908d-129">-create</span><span class="sxs-lookup"><span data-stu-id="e908d-129">-create</span></span>|<span data-ttu-id="e908d-130">建立新的配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-130">Creates new adapter(s)</span></span>|  
|<span data-ttu-id="e908d-131">-setprops</span><span class="sxs-lookup"><span data-stu-id="e908d-131">-setprops</span></span>|<span data-ttu-id="e908d-132">設定配接器屬性</span><span class="sxs-lookup"><span data-stu-id="e908d-132">Sets properties for adapter</span></span>|  
|<span data-ttu-id="e908d-133">-update</span><span class="sxs-lookup"><span data-stu-id="e908d-133">-update</span></span>|<span data-ttu-id="e908d-134">更新現有的配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-134">Updates existing adapter(s)</span></span>|  
|<span data-ttu-id="e908d-135">-delete</span><span class="sxs-lookup"><span data-stu-id="e908d-135">-delete</span></span>|<span data-ttu-id="e908d-136">刪除現有的配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-136">Deletes an existing adapter</span></span>|  
|<span data-ttu-id="e908d-137">-enable</span><span class="sxs-lookup"><span data-stu-id="e908d-137">-enable</span></span>|<span data-ttu-id="e908d-138">啟用配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-138">Enables adapter</span></span>|  
|<span data-ttu-id="e908d-139">-disable</span><span class="sxs-lookup"><span data-stu-id="e908d-139">-disable</span></span>|<span data-ttu-id="e908d-140">停用配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-140">Disables adapter</span></span>|  
|<span data-ttu-id="e908d-141">-addapp</span><span class="sxs-lookup"><span data-stu-id="e908d-141">-addapp</span></span>|<span data-ttu-id="e908d-142">新增配接器的應用程式</span><span class="sxs-lookup"><span data-stu-id="e908d-142">Adds application for adapter</span></span>|  
|<span data-ttu-id="e908d-143">-deleteapp</span><span class="sxs-lookup"><span data-stu-id="e908d-143">-deleteapp</span></span>|<span data-ttu-id="e908d-144">刪除配接器的應用程式</span><span class="sxs-lookup"><span data-stu-id="e908d-144">Deletes application for adapter</span></span>|  
|<span data-ttu-id="e908d-145">-reset</span><span class="sxs-lookup"><span data-stu-id="e908d-145">-reset</span></span>|<span data-ttu-id="e908d-146">重設通知或禁止的佇列</span><span class="sxs-lookup"><span data-stu-id="e908d-146">Resets notification or damping queues</span></span>|  
|<span data-ttu-id="e908d-147">-addtogroup</span><span class="sxs-lookup"><span data-stu-id="e908d-147">-addtogroup</span></span>|<span data-ttu-id="e908d-148">新增配接器至配接器群組</span><span class="sxs-lookup"><span data-stu-id="e908d-148">Adds adapter to adapter group</span></span>|  
|<span data-ttu-id="e908d-149">-deletefromgroup</span><span class="sxs-lookup"><span data-stu-id="e908d-149">-deletefromgroup</span></span>|<span data-ttu-id="e908d-150">從配接器群組刪除配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-150">Deletes adapter from adapter group</span></span>|  
  
### <a name="to-list-existing-adapters"></a><span data-ttu-id="e908d-151">列出現有的配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-151">To list existing adapters</span></span>  
  
1.  <span data-ttu-id="e908d-152">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-152">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-153">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-153">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-154">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-154">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-155">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-155">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-156">型別**ssops-清單**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-156">Type **ssops -list** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-157">會列出配接器和描述。</span><span class="sxs-lookup"><span data-stu-id="e908d-157">Adapters and descriptions will be listed.</span></span> <span data-ttu-id="e908d-158">(E) 代表配接器已啟用，(D) 代表配接器已停用。</span><span class="sxs-lookup"><span data-stu-id="e908d-158">(E) denotes that the adapter is enabled, (D) denotes that it is disabled.</span></span>  
  
### <a name="to-display-adapter-information"></a><span data-ttu-id="e908d-159">顯示配接器資訊</span><span class="sxs-lookup"><span data-stu-id="e908d-159">To display adapter information</span></span>  
  
1.  <span data-ttu-id="e908d-160">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-160">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-161">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-161">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-162">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-162">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-163">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-163">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-164">型別**ssops-顯示\<配接器名稱\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-164">Type **ssops -display \<adapter name\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-165">畫面輸出會顯示特定配接器的資訊。</span><span class="sxs-lookup"><span data-stu-id="e908d-165">The screen output will display information for the specified adapter.</span></span>  
  
     <span data-ttu-id="e908d-166">除了名稱、類型、描述、電腦和帳戶之外，會顯示下列資訊。</span><span class="sxs-lookup"><span data-stu-id="e908d-166">In addition to name, type, description, computer, and accounts, the following information is displayed.</span></span>  
  
    |<span data-ttu-id="e908d-167">配接器旗標</span><span class="sxs-lookup"><span data-stu-id="e908d-167">Adapter Flag</span></span>|<span data-ttu-id="e908d-168">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e908d-168">Details</span></span>|  
    |------------------|-------------|  
    |<span data-ttu-id="e908d-169">啟用的配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-169">Adapter enabled</span></span>|<span data-ttu-id="e908d-170">決定配接器是否已啟用。</span><span class="sxs-lookup"><span data-stu-id="e908d-170">Determines whether or not the adapter is enabled.</span></span><br /><br /> <span data-ttu-id="e908d-171">旗標： SSO_FLAG_ENABLED</span><span class="sxs-lookup"><span data-stu-id="e908d-171">Flag: SSO_FLAG_ENABLED</span></span><br /><br /> <span data-ttu-id="e908d-172">屬性名稱： enableApp</span><span class="sxs-lookup"><span data-stu-id="e908d-172">Attribute Name: enableApp</span></span><br /><br /> <span data-ttu-id="e908d-173">預設：否</span><span class="sxs-lookup"><span data-stu-id="e908d-173">Default: No</span></span>|  
    |<span data-ttu-id="e908d-174">允許本機帳戶</span><span class="sxs-lookup"><span data-stu-id="e908d-174">Allow local accounts</span></span>|<span data-ttu-id="e908d-175">決定「應用程式系統管理員」或「應用程式使用者」帳戶是否可為本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="e908d-175">Determines whether or not the App Admin or App Users accounts can be local accounts.</span></span><br /><br /> <span data-ttu-id="e908d-176">旗標： SSO_FLAG_APP_ALLOW_LOCAL</span><span class="sxs-lookup"><span data-stu-id="e908d-176">Flag: SSO_FLAG_APP_ALLOW_LOCAL</span></span><br /><br /> <span data-ttu-id="e908d-177">屬性名稱： allowLocalAccounts</span><span class="sxs-lookup"><span data-stu-id="e908d-177">Attribute Name: allowLocalAccounts</span></span><br /><br /> <span data-ttu-id="e908d-178">預設：否</span><span class="sxs-lookup"><span data-stu-id="e908d-178">Default: No</span></span>|  
    |<span data-ttu-id="e908d-179">接收來自配接器的密碼變更</span><span class="sxs-lookup"><span data-stu-id="e908d-179">Receive password changes from adapter</span></span>|<span data-ttu-id="e908d-180">決定配接器是否可接收外部密碼變更。</span><span class="sxs-lookup"><span data-stu-id="e908d-180">Determines whether or not the adapter is allowed to receive external password changes.</span></span><br /><br /> <span data-ttu-id="e908d-181">旗標： SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB</span><span class="sxs-lookup"><span data-stu-id="e908d-181">Flag: SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB</span></span><br /><br /> <span data-ttu-id="e908d-182">屬性名稱： syncFromAdapter</span><span class="sxs-lookup"><span data-stu-id="e908d-182">Attribute Name: syncFromAdapter</span></span><br /><br /> <span data-ttu-id="e908d-183">預設：否</span><span class="sxs-lookup"><span data-stu-id="e908d-183">Default: No</span></span>|  
    |<span data-ttu-id="e908d-184">驗證舊密碼</span><span class="sxs-lookup"><span data-stu-id="e908d-184">Verify old password</span></span>|<span data-ttu-id="e908d-185">決定配接器是否將在收到外部密碼變更時驗證舊密碼。</span><span class="sxs-lookup"><span data-stu-id="e908d-185">Determines whether the adapter will verify the old password when an external password change is received.</span></span> <span data-ttu-id="e908d-186">若設定此旗標而之後有外部密碼變更，外部配接器就必須提供舊的外部密碼以及新的外部密碼。</span><span class="sxs-lookup"><span data-stu-id="e908d-186">If this flag is set then with an external password change the external adapter must supply the old external password as well as the new external password.</span></span> <span data-ttu-id="e908d-187">然後比較該外部帳戶在 SSO 資料庫中的現有外部密碼與舊外部密碼。</span><span class="sxs-lookup"><span data-stu-id="e908d-187">The old external password is then compared with the existing external password in the SSO database for that external account.</span></span> <span data-ttu-id="e908d-188">若兩者相符，便會接受變更密碼。</span><span class="sxs-lookup"><span data-stu-id="e908d-188">If they match, the password change is accepted.</span></span> <span data-ttu-id="e908d-189">若兩者不相符，便會拒絕變更密碼。</span><span class="sxs-lookup"><span data-stu-id="e908d-189">If they do not match, the password change is rejected.</span></span><br /><br /> <span data-ttu-id="e908d-190">旗標： SSO_FLAG_SYNC_VERIFY_EXTERNAL_CREDS</span><span class="sxs-lookup"><span data-stu-id="e908d-190">Flag: SSO_FLAG_SYNC_VERIFY_EXTERNAL_CREDS</span></span><br /><br /> <span data-ttu-id="e908d-191">屬性名稱： verifyOldPassword</span><span class="sxs-lookup"><span data-stu-id="e908d-191">Attribute Name: verifyOldPassword</span></span><br /><br /> <span data-ttu-id="e908d-192">預設：是</span><span class="sxs-lookup"><span data-stu-id="e908d-192">Default: Yes</span></span>|  
    |<span data-ttu-id="e908d-193">變更 Windows 密碼</span><span class="sxs-lookup"><span data-stu-id="e908d-193">Change Windows password</span></span>|<span data-ttu-id="e908d-194">決定收到外部密碼變更 (完全同步) 時，是否也要一併變更 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="e908d-194">Determines whether or not the Windows password will also be changed when an external password change is received (full sync).</span></span> <span data-ttu-id="e908d-195">ENTSSO 永遠使用儲存在 SSO 資料庫中的舊 Windows 密碼來將 Windows 密碼變更為新值 (Windows 同時需要新舊密碼才能變更使用者密碼)，因此必須初始化才能使 Windows 密碼變更成功。</span><span class="sxs-lookup"><span data-stu-id="e908d-195">ENTSSO always uses the old Windows password stored in the SSO database to change the Windows password to the new value (Windows requires both the old and new password to change a users password), so this must be initialized before the Windows password change can succeed.</span></span> <span data-ttu-id="e908d-196">如果已針對特定對應設定密碼同步，然後當透過系統管理工具 （ssomanage 或 ssoclient-setcredentials) 設定的外部認證儲存在 SSO 資料庫中的 Windows 密碼也將。旗標： SSO_FLAG_FULL_SYNC_FROM_EXTERNAL_TO_WINDOWS</span><span class="sxs-lookup"><span data-stu-id="e908d-196">If password sync is configured for a particular mapping, then when the external credentials are set via administrative tools (ssomanage or ssoclient -setcredentials) the Windows password stored in the SSO database will also be set.Flag: SSO_FLAG_FULL_SYNC_FROM_EXTERNAL_TO_WINDOWS</span></span><br /><br /> <span data-ttu-id="e908d-197">屬性名稱： changeWindowsPassword</span><span class="sxs-lookup"><span data-stu-id="e908d-197">Attribute Name: changeWindowsPassword</span></span><br /><br /> <span data-ttu-id="e908d-198">預設：否</span><span class="sxs-lookup"><span data-stu-id="e908d-198">Default: No</span></span>|  
    |<span data-ttu-id="e908d-199">傳送 Windows 密碼變更至配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-199">Send Windows password changes to adapter</span></span>|<span data-ttu-id="e908d-200">決定 Windows 密碼變更是否會傳送至外部配接器。</span><span class="sxs-lookup"><span data-stu-id="e908d-200">Determines whether or not Windows password changes will be sent to the external adapter.</span></span><br /><br /> <span data-ttu-id="e908d-201">旗標： SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL</span><span class="sxs-lookup"><span data-stu-id="e908d-201">Flag: SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL</span></span><br /><br /> <span data-ttu-id="e908d-202">屬性名稱： syncToAdapter</span><span class="sxs-lookup"><span data-stu-id="e908d-202">Attribute Name: syncToAdapter</span></span><br /><br /> <span data-ttu-id="e908d-203">預設：否</span><span class="sxs-lookup"><span data-stu-id="e908d-203">Default: No</span></span>|  
    |<span data-ttu-id="e908d-204">傳送舊密碼至配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-204">Send old password to adapter</span></span>|<span data-ttu-id="e908d-205">若為 [是]，舊的密碼值 (來自 SSO 資料庫) 將會連同新的密碼值一起傳送至外部配接器。</span><span class="sxs-lookup"><span data-stu-id="e908d-205">If Yes, the old password value (from the SSO database) will also be sent to the external adapter as well as the new password value.</span></span> <span data-ttu-id="e908d-206">某些外部系統可能會同時需要新舊密碼值才能變更密碼。</span><span class="sxs-lookup"><span data-stu-id="e908d-206">Some external systems might require both the old and new password values to change the password.</span></span><br /><br /> <span data-ttu-id="e908d-207">旗標： SSO_FLAG_SYNC_PROVIDE_OLD_EXTERNAL_CREDS</span><span class="sxs-lookup"><span data-stu-id="e908d-207">Flag: SSO_FLAG_SYNC_PROVIDE_OLD_EXTERNAL_CREDS</span></span><br /><br /> <span data-ttu-id="e908d-208">屬性名稱： sendOldPassword</span><span class="sxs-lookup"><span data-stu-id="e908d-208">Attribute Name: sendOldPassword</span></span><br /><br /> <span data-ttu-id="e908d-209">預設：否</span><span class="sxs-lookup"><span data-stu-id="e908d-209">Default: No</span></span>|  
    |<span data-ttu-id="e908d-210">允許對應衝突</span><span class="sxs-lookup"><span data-stu-id="e908d-210">Allow mapping conflicts</span></span>|<span data-ttu-id="e908d-211">決定配接器是否將允許對應衝突。</span><span class="sxs-lookup"><span data-stu-id="e908d-211">Determines whether or not the adapter will allow mapping conflicts.</span></span><br /><br /> <span data-ttu-id="e908d-212">當對應不是唯一時就會發生對應衝突。</span><span class="sxs-lookup"><span data-stu-id="e908d-212">A mapping conflict occurs when mappings are not unique.</span></span> <span data-ttu-id="e908d-213">在單一的 SSO 個別應用程式中，對應永遠都是一對一：一個 Windows 帳戶只會對應至一個外部帳戶，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e908d-213">In a single SSO Individual application, mappings are always one-to-one: one Windows account is mapped to exactly one external account and vice versa.</span></span><br /><br /> <span data-ttu-id="e908d-214">但是有可能會將一個以上的應用程式指派給配接器。</span><span class="sxs-lookup"><span data-stu-id="e908d-214">However, it is possible to assign more than one application to an adapter.</span></span> <span data-ttu-id="e908d-215">因此，某個應用程式中的對應可能會與另一個應用程式中的對應衝突。</span><span class="sxs-lookup"><span data-stu-id="e908d-215">Thus, it is possible to have a mapping in one application that conflicts with a mapping in the other.</span></span><br /><br /> <span data-ttu-id="e908d-216">此旗標的用途在避免發生此情況。</span><span class="sxs-lookup"><span data-stu-id="e908d-216">This purpose of this flag is to prevent this from occurring.</span></span> <span data-ttu-id="e908d-217">除非能明確、充分瞭解此行為的需求，否則不允許發生對應衝突會較為安全。</span><span class="sxs-lookup"><span data-stu-id="e908d-217">It is more secure to not allow mapping conflicts unless there is a specific, well understood requirement for this behavior.</span></span><br /><br /> <span data-ttu-id="e908d-218">旗標： SSO_FLAG_SYNC_ALLOW_MAPPING_CONFLICTS</span><span class="sxs-lookup"><span data-stu-id="e908d-218">Flag: SSO_FLAG_SYNC_ALLOW_MAPPING_CONFLICTS</span></span><br /><br /> <span data-ttu-id="e908d-219">屬性名稱： allowMappingConflicts</span><span class="sxs-lookup"><span data-stu-id="e908d-219">Attribute Name: allowMappingConflicts</span></span><br /><br /> <span data-ttu-id="e908d-220">預設：否</span><span class="sxs-lookup"><span data-stu-id="e908d-220">Default: No</span></span>|  
  
    |<span data-ttu-id="e908d-221">配接器描述</span><span class="sxs-lookup"><span data-stu-id="e908d-221">Adapter Description</span></span>|<span data-ttu-id="e908d-222">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e908d-222">Details</span></span>|  
    |-------------------------|-------------|  
    |<span data-ttu-id="e908d-223">通知重試計數</span><span class="sxs-lookup"><span data-stu-id="e908d-223">Notification retry count</span></span>|<span data-ttu-id="e908d-224">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="e908d-224">Default is 1.</span></span>|  
    |<span data-ttu-id="e908d-225">通知重試延遲 (分鐘)</span><span class="sxs-lookup"><span data-stu-id="e908d-225">Notification retry delay (in mins)</span></span>|<span data-ttu-id="e908d-226">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="e908d-226">Default is 5.</span></span>|  
    |<span data-ttu-id="e908d-227">擱置通知的上限</span><span class="sxs-lookup"><span data-stu-id="e908d-227">Maximum pending notifications</span></span>|<span data-ttu-id="e908d-228">預設值為 8。</span><span class="sxs-lookup"><span data-stu-id="e908d-228">Default is 8.</span></span>|  
    |<span data-ttu-id="e908d-229">存放區通知 (離線時)</span><span class="sxs-lookup"><span data-stu-id="e908d-229">Store notifications (when offline)</span></span>|<span data-ttu-id="e908d-230">True/False。</span><span class="sxs-lookup"><span data-stu-id="e908d-230">True/False.</span></span>|  
    |<span data-ttu-id="e908d-231">伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="e908d-231">Server name</span></span>|<span data-ttu-id="e908d-232">伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="e908d-232">Server name.</span></span>|  
    |<span data-ttu-id="e908d-233">通訊埠編號</span><span class="sxs-lookup"><span data-stu-id="e908d-233">Port number</span></span>|<span data-ttu-id="e908d-234">連接埠編號。</span><span class="sxs-lookup"><span data-stu-id="e908d-234">Port number.</span></span>|  
    |<span data-ttu-id="e908d-235">此配接器的應用程式</span><span class="sxs-lookup"><span data-stu-id="e908d-235">Applications for this adapter</span></span>|<span data-ttu-id="e908d-236">目前指派給配接器的應用程式清單。</span><span class="sxs-lookup"><span data-stu-id="e908d-236">List of applications currently assigned to the adapter.</span></span>|  
  
### <a name="to-create-new-adapters"></a><span data-ttu-id="e908d-237">建立新的配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-237">To create new adapters</span></span>  
  
1.  <span data-ttu-id="e908d-238">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-238">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-239">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-239">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-240">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-240">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-241">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-241">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-242">型別**ssops-建立\<配接器檔案\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-242">Type **ssops -create \<adapter file\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-243">畫面輸出會顯示最新建立配接器的資訊。</span><span class="sxs-lookup"><span data-stu-id="e908d-243">The screen output will display information for the newly created adapter.</span></span>  
  
### <a name="to-set-properties-for-an-adapter"></a><span data-ttu-id="e908d-244">若要設定配接器屬性</span><span class="sxs-lookup"><span data-stu-id="e908d-244">To set properties for an adapter</span></span>  
  
1.  <span data-ttu-id="e908d-245">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-245">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-246">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-246">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-247">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-247">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-248">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-248">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-249">型別**ssops-setprops\<配接器名稱\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-249">Type **ssops -setprops \<adapter name\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-250">畫面輸出會顯示特定配接器的屬性。</span><span class="sxs-lookup"><span data-stu-id="e908d-250">The screen output will display the properties for the specified adapter.</span></span> <span data-ttu-id="e908d-251">如有需要，您可以編輯它們，但是不會驗證新值。</span><span class="sxs-lookup"><span data-stu-id="e908d-251">You can edit them if necessary, but new values are not validated.</span></span>  
  
### <a name="to-update-existing-adapters"></a><span data-ttu-id="e908d-252">更新現有的配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-252">To update existing adapters</span></span>  
  
1.  <span data-ttu-id="e908d-253">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-253">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-254">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-254">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-255">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-255">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-256">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-256">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-257">型別**ssops-更新\<配接器檔案\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-257">Type **ssops -update \<adapter file\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-258">使用此命令可更新特定配接器的設定和旗標。</span><span class="sxs-lookup"><span data-stu-id="e908d-258">Use this command to update the settings and flags for a specified adapter.</span></span> <span data-ttu-id="e908d-259">請勿使用此命令來設定屬性；請使用 -setprops 命令替代。</span><span class="sxs-lookup"><span data-stu-id="e908d-259">Do not use this command to set properties; use instead the -setprops command.</span></span>  
  
### <a name="to-delete-an-existing-adapter"></a><span data-ttu-id="e908d-260">刪除現有的配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-260">To delete an existing adapter</span></span>  
  
1.  <span data-ttu-id="e908d-261">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-261">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-262">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-262">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-263">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-263">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-264">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-264">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-265">型別**ssops-刪除\<配接器名稱\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-265">Type **ssops -delete \<adapter name\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-266">將刪除指定的配接器。</span><span class="sxs-lookup"><span data-stu-id="e908d-266">The specified adapter will be deleted.</span></span>  
  
### <a name="to-enable-an-adapter"></a><span data-ttu-id="e908d-267">啟用配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-267">To enable an adapter</span></span>  
  
1.  <span data-ttu-id="e908d-268">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-268">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-269">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-269">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-270">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-270">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-271">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-271">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-272">型別**ssops-啟用\<配接器名稱\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-272">Type **ssops -enable \<adapter name\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-273">將啟用指定的配接器。</span><span class="sxs-lookup"><span data-stu-id="e908d-273">The specified adapter will be enabled.</span></span>  
  
### <a name="to-disable-an-adapter"></a><span data-ttu-id="e908d-274">停用配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-274">To disable an adapter</span></span>  
  
1.  <span data-ttu-id="e908d-275">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-275">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-276">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-276">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-277">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-277">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-278">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-278">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-279">型別**ssops-停用\<配接器名稱\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-279">Type **ssops -disable \<adapter name\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-280">將停用指定的配接器。</span><span class="sxs-lookup"><span data-stu-id="e908d-280">The specified adapter will be disabled.</span></span>  
  
### <a name="to-add-an-application-to-an-adapter"></a><span data-ttu-id="e908d-281">新增應用程式至配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-281">To add an application to an adapter</span></span>  
  
1.  <span data-ttu-id="e908d-282">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-282">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-283">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-283">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-284">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-284">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-285">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-285">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-286">型別**ssops-addapp\<配接器名稱\>\<應用程式名稱\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-286">Type **ssops -addapp \<adapter name\> \<application name\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-287">會將特定 SSO 應用程式指派給特定配接器。</span><span class="sxs-lookup"><span data-stu-id="e908d-287">The specified SSO application will be assigned to the specified adapter.</span></span> <span data-ttu-id="e908d-288">這表示，該應用程式中對應的密碼現在將使用此配接器來同步。</span><span class="sxs-lookup"><span data-stu-id="e908d-288">This means that the passwords for the mappings in that application will now be synchronized using this adapter.</span></span>  
  
     <span data-ttu-id="e908d-289">多個應用程式可指派給一個配接器，但任何指定的應用程式僅能指派給一個配接器。</span><span class="sxs-lookup"><span data-stu-id="e908d-289">While multiple applications can be assigned to one adapter, any given application can only be assigned to one adapter.</span></span>  
  
### <a name="to-delete-an-application-from-an-adapter"></a><span data-ttu-id="e908d-290">從配接器刪除應用程式</span><span class="sxs-lookup"><span data-stu-id="e908d-290">To delete an application from an adapter</span></span>  
  
1.  <span data-ttu-id="e908d-291">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-291">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-292">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-292">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-293">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-293">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-294">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-294">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-295">型別**ssops-deleteapp\<應用程式名稱\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-295">Type **ssops -deleteapp \<application name\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-296">會將特定 SSO 應用程式從配接器移除。</span><span class="sxs-lookup"><span data-stu-id="e908d-296">The specified SSO application will be removed from an adapter.</span></span> <span data-ttu-id="e908d-297">(因為應用程式僅可指定給一個配接器，所以不需要指定配接器名稱。)</span><span class="sxs-lookup"><span data-stu-id="e908d-297">(Since an application can only be assigned to one adapter, it is not necessary to specify the adapter name.)</span></span>  
  
### <a name="to-reset-notification"></a><span data-ttu-id="e908d-298">重設通知</span><span class="sxs-lookup"><span data-stu-id="e908d-298">To reset notification</span></span>  
  
1.  <span data-ttu-id="e908d-299">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-299">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-300">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-300">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-301">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-301">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-302">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-302">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-303">型別**ssops-重設\<配接器名稱 &#124; 所有 &#124; 禁止\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-303">Type **ssops -reset \<adapter name &#124; all &#124; damping\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-304">此命令會依指定清除單一配接器或所有配接器禁止的資料表和 (或) 通知佇列。</span><span class="sxs-lookup"><span data-stu-id="e908d-304">This command clears the damping table and/or notification queues for a single adapter or all adapters, as specified.</span></span> <span data-ttu-id="e908d-305">禁止的資料表會儲存 10 分鐘的密碼變更歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-305">The damping table stores a 10-minute history of password changes.</span></span> <span data-ttu-id="e908d-306">在「企業單一登入」系統接受或傳送密碼變更之前，會檢查禁止的資料表，以查看最近是否執行過相同變更。</span><span class="sxs-lookup"><span data-stu-id="e908d-306">Before the Enterprise SSO system accepts or sends a password change, it checks the damping table to see if it has performed the same change recently.</span></span> <span data-ttu-id="e908d-307">若有，則會捨棄變更。</span><span class="sxs-lookup"><span data-stu-id="e908d-307">If it has, the new change is discarded.</span></span>  
  
### <a name="to-add-an-adapter-to-an-adapter-group"></a><span data-ttu-id="e908d-308">新增配接器至配接器群組</span><span class="sxs-lookup"><span data-stu-id="e908d-308">To add an adapter to an adapter group</span></span>  
  
1.  <span data-ttu-id="e908d-309">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-309">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-310">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-310">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-311">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-311">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-312">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-312">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-313">型別**ssops-addtogroup\<配接器名稱\>\<配接器群組\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-313">Type **ssops -addtogroup \<adapter name\> \<adapter group\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-314">此命令會將特定配接器新增至特定配接器群組。</span><span class="sxs-lookup"><span data-stu-id="e908d-314">This command adds the specified adapter to the specified adapter group.</span></span> <span data-ttu-id="e908d-315">配接器僅可屬於一個配接器群組，但配接器群組可包含多個配接器。</span><span class="sxs-lookup"><span data-stu-id="e908d-315">While an adapter can belong to only one adapter group, an adapter group can contain multiple adapters.</span></span>  
  
### <a name="to-delete-an-adapter-from-an-adapter-group"></a><span data-ttu-id="e908d-316">從配接器群組刪除配接器</span><span class="sxs-lookup"><span data-stu-id="e908d-316">To delete an adapter from an adapter group</span></span>  
  
1.  <span data-ttu-id="e908d-317">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="e908d-317">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e908d-318">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e908d-318">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="e908d-319">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e908d-319">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e908d-320">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e908d-320">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="e908d-321">型別**ssops-deletefromgroup\<配接器名稱\>\<配接器群組\>**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="e908d-321">Type **ssops -deletefromgroup \<adapter name\> \<adapter group\>** and press Enter.</span></span>  
  
     <span data-ttu-id="e908d-322">此命令會刪除特定配接器群組的特定配接器。</span><span class="sxs-lookup"><span data-stu-id="e908d-322">This command deletes the specified adapter from the specified adapter group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e908d-323">請參閱</span><span class="sxs-lookup"><span data-stu-id="e908d-323">See Also</span></span>  
 [<span data-ttu-id="e908d-324">密碼同步</span><span class="sxs-lookup"><span data-stu-id="e908d-324">Password Synchronization</span></span>](../core/password-synchronization2.md)