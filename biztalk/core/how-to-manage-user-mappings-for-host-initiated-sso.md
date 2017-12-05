---
title: "如何管理使用者對應的主控件初始化的 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, host initiated SSO
- host initiated SSO, user maps
ms.assetid: 6b05249e-da35-475b-9c23-5eb556013d57
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0bf65bdb3de30d5b701946215b5c7ae7d40d828
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-manage-user-mappings-for-host-initiated-sso"></a><span data-ttu-id="2ee5b-102">如何管理使用者對應的主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="2ee5b-102">How to Manage User Mappings for Host Initiated SSO</span></span>
<span data-ttu-id="2ee5b-103">使用下列程序，以建立對應、設定認證以及啟用或停用對應。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-103">Use the following procedures to create mappings, set credentials, and enable or disable mapping.</span></span>  
  
### <a name="to-manage-user-mappings-for-host-initiated-sso-using-the-mmc-snap-in"></a><span data-ttu-id="2ee5b-104">若要使用 MMC 嵌入式管理單元為主控件初始化的 SSO 管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="2ee5b-104">To manage user mappings for host initiated SSO using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="2ee5b-105">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-105">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="2ee5b-106">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="2ee5b-107">在 [領域] 窗格中，按一下**分支機構應用程式**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-107">In the scope pane, click **Affiliate Applications**.</span></span>  
  
4.  <span data-ttu-id="2ee5b-108">在詳細資訊窗格中，使用滑鼠右鍵按一下分支機構應用程式，然後為您的動作選擇適當的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-108">In the details pane, right-click the affiliate application, and then choose the appropriate menu item for your action.</span></span>  
  
### <a name="to-create-mappings-in-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="2ee5b-109">使用命令列在主控件初始化的 SSO 中建立對應</span><span class="sxs-lookup"><span data-stu-id="2ee5b-109">To create mappings in host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="2ee5b-110">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-110">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="2ee5b-111">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-111">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2ee5b-112">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-112">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2ee5b-113">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-113">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="2ee5b-114">型別**ssomanage – createmappings\<對應檔\>**，其中**對應檔 >**是 xml 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-114">Type **ssomanage –createmappings \<mapping file\>**, where **mapping file>** is the name of the xml file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ee5b-115">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-115">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
     <span data-ttu-id="2ee5b-116">以下顯示對應檔案範例。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-116">A sample mapping file is shown below:</span></span>  
  
    ```  
    <SSO>  
      <mapping>  
        <windowsDomain>DomainName</windowsDomain>  
        <windowsUserId>UserA</windowsUserId>  
        <externalApplication>SSOApplication</externalApplication>  
    <externalUserId>ExternalUserID that corresponds to UserA</externalUserId>  
      </mapping>  
    </SSO>  
  
    ```  
  
 <span data-ttu-id="2ee5b-117">為分支機構應用程式啟用「驗證密碼」功能時，需要設定認證，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2ee5b-117">When the Validate Password feature is enabled for the affiliate application, it is necessary to set credentials, as follows:</span></span>  
  
#### <a name="to-set-credentials-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="2ee5b-118">使用命令列為個別類型的分支機構應用程式設定認證</span><span class="sxs-lookup"><span data-stu-id="2ee5b-118">To set credentials for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="2ee5b-119">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-119">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="2ee5b-120">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-120">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2ee5b-121">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-121">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2ee5b-122">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-122">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="2ee5b-123">型別**ssomanage-setcredentials \<Windows 帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-123">Type **ssomanage -setcredentials \<Windows account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ee5b-124">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-124">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-set-credentials-for-host-group-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="2ee5b-125">使用命令列設定主控件群組類型分支機構應用程式的認證</span><span class="sxs-lookup"><span data-stu-id="2ee5b-125">To set credentials for host group type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="2ee5b-126">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-126">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="2ee5b-127">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-127">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2ee5b-128">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-128">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2ee5b-129">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-129">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="2ee5b-130">型別**ssomanage-setcredentials\<外部帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-130">Type **ssomanage -setcredentials \<external account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ee5b-131">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-131">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-enable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="2ee5b-132">使用命令列為個別類型的分支機構應用程式啟用對應</span><span class="sxs-lookup"><span data-stu-id="2ee5b-132">To enable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="2ee5b-133">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-133">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="2ee5b-134">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-134">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2ee5b-135">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-135">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2ee5b-136">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-136">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="2ee5b-137">型別**ssomanage-enablemapping \<Windows 帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-137">Type **ssomanage -enablemapping \<Windows account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ee5b-138">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-138">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="2ee5b-139">使用命令列為個別類型的分支機構應用程式停用對應</span><span class="sxs-lookup"><span data-stu-id="2ee5b-139">To disable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="2ee5b-140">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-140">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="2ee5b-141">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-141">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2ee5b-142">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-142">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2ee5b-143">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-143">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="2ee5b-144">型別**ssomanage-disablemapping \<Windows 帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-144">Type **ssomanage -disablemapping \<Windows account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ee5b-145">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-145">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-enable-mappings-for-host-group-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="2ee5b-146">使用命令列為主控件群組類型的分支機構應用程式啟用對應</span><span class="sxs-lookup"><span data-stu-id="2ee5b-146">To enable mappings for host group type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="2ee5b-147">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-147">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="2ee5b-148">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-148">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2ee5b-149">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-149">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2ee5b-150">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-150">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="2ee5b-151">型別**ssomanage-enablemapping\<外部帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-151">Type **ssomanage -enablemapping \<external account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ee5b-152">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-152">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="2ee5b-153">使用命令列為個別類型的分支機構應用程式停用對應</span><span class="sxs-lookup"><span data-stu-id="2ee5b-153">To disable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="2ee5b-154">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-154">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="2ee5b-155">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-155">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2ee5b-156">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-156">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="2ee5b-157">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-157">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="2ee5b-158">型別**ssomanage-disablemapping\<外部帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-158">Type **ssomanage -disablemapping \<external account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ee5b-159">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-159">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee5b-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ee5b-160">See Also</span></span>  
 [<span data-ttu-id="2ee5b-161">主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="2ee5b-161">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)