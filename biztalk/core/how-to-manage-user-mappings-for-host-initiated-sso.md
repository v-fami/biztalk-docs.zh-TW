---
title: 如何管理使用者對應的主控件初始化的 SSO |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, host initiated SSO
- host initiated SSO, user maps
ms.assetid: 6b05249e-da35-475b-9c23-5eb556013d57
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad232bf81fff96e6cabf367e9c591d02d4296151
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006703"
---
# <a name="how-to-manage-user-mappings-for-host-initiated-sso"></a><span data-ttu-id="c3a22-102">如何管理使用者對應的主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="c3a22-102">How to Manage User Mappings for Host Initiated SSO</span></span>
<span data-ttu-id="c3a22-103">使用下列程序，以建立對應、設定認證以及啟用或停用對應。</span><span class="sxs-lookup"><span data-stu-id="c3a22-103">Use the following procedures to create mappings, set credentials, and enable or disable mapping.</span></span>  
  
### <a name="to-manage-user-mappings-for-host-initiated-sso-using-the-mmc-snap-in"></a><span data-ttu-id="c3a22-104">若要使用 MMC 嵌入式管理單元為主控件初始化的 SSO 管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="c3a22-104">To manage user mappings for host initiated SSO using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="c3a22-105">在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-105">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="c3a22-106">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="c3a22-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="c3a22-107">在 [範圍] 窗格中，按一下**分支機構應用程式**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-107">In the scope pane, click **Affiliate Applications**.</span></span>  
  
4.  <span data-ttu-id="c3a22-108">在詳細資訊窗格中，使用滑鼠右鍵按一下分支機構應用程式，然後為您的動作選擇適當的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="c3a22-108">In the details pane, right-click the affiliate application, and then choose the appropriate menu item for your action.</span></span>  
  
### <a name="to-create-mappings-in-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="c3a22-109">使用命令列在主控件初始化的 SSO 中建立對應</span><span class="sxs-lookup"><span data-stu-id="c3a22-109">To create mappings in host initiated SSO using the command line</span></span>  
  
1. <span data-ttu-id="c3a22-110">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-110">On the **Start** menu, click **Run**.</span></span>  
  
2. <span data-ttu-id="c3a22-111">在 [**執行**] 對話方塊中，輸入**cmd**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-111">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="c3a22-112">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="c3a22-112">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c3a22-113">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="c3a22-113">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4. <span data-ttu-id="c3a22-114">型別**ssomanage – createmappings\<對應檔\>**，其中**對應檔 >** 是 xml 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3a22-114">Type **ssomanage –createmappings \<mapping file\>**, where **mapping file>** is the name of the xml file.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c3a22-115">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="c3a22-115">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
    <span data-ttu-id="c3a22-116">以下顯示對應檔案範例。</span><span class="sxs-lookup"><span data-stu-id="c3a22-116">A sample mapping file is shown below:</span></span>  
  
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
  
   <span data-ttu-id="c3a22-117">為分支機構應用程式啟用「驗證密碼」功能時，需要設定認證，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c3a22-117">When the Validate Password feature is enabled for the affiliate application, it is necessary to set credentials, as follows:</span></span>  
  
#### <a name="to-set-credentials-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="c3a22-118">使用命令列為個別類型的分支機構應用程式設定認證</span><span class="sxs-lookup"><span data-stu-id="c3a22-118">To set credentials for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="c3a22-119">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-119">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="c3a22-120">在 [**執行**] 對話方塊中，輸入**cmd**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-120">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c3a22-121">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="c3a22-121">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c3a22-122">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="c3a22-122">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="c3a22-123">型別**ssomanage-setcredentials \<Windows 帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-123">Type **ssomanage -setcredentials \<Windows account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3a22-124">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="c3a22-124">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-set-credentials-for-host-group-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="c3a22-125">使用命令列設定主控件群組類型分支機構應用程式的認證</span><span class="sxs-lookup"><span data-stu-id="c3a22-125">To set credentials for host group type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="c3a22-126">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-126">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="c3a22-127">在 [**執行**] 對話方塊中，輸入**cmd**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-127">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c3a22-128">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="c3a22-128">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c3a22-129">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="c3a22-129">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="c3a22-130">型別**ssomanage-setcredentials\<外部帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-130">Type **ssomanage -setcredentials \<external account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3a22-131">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="c3a22-131">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-enable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="c3a22-132">使用命令列為個別類型的分支機構應用程式啟用對應</span><span class="sxs-lookup"><span data-stu-id="c3a22-132">To enable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="c3a22-133">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-133">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="c3a22-134">在 [**執行**] 對話方塊中，輸入**cmd**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-134">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c3a22-135">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="c3a22-135">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c3a22-136">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="c3a22-136">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="c3a22-137">型別**ssomanage-enablemapping \<Windows 帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-137">Type **ssomanage -enablemapping \<Windows account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3a22-138">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="c3a22-138">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="c3a22-139">使用命令列為個別類型的分支機構應用程式停用對應</span><span class="sxs-lookup"><span data-stu-id="c3a22-139">To disable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="c3a22-140">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-140">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="c3a22-141">在 [**執行**] 對話方塊中，輸入**cmd**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-141">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c3a22-142">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="c3a22-142">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c3a22-143">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="c3a22-143">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="c3a22-144">型別**ssomanage-disablemapping \<Windows 帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-144">Type **ssomanage -disablemapping \<Windows account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3a22-145">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="c3a22-145">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-enable-mappings-for-host-group-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="c3a22-146">使用命令列為主控件群組類型的分支機構應用程式啟用對應</span><span class="sxs-lookup"><span data-stu-id="c3a22-146">To enable mappings for host group type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="c3a22-147">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-147">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="c3a22-148">在 [**執行**] 對話方塊中，輸入**cmd**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-148">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c3a22-149">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="c3a22-149">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c3a22-150">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="c3a22-150">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="c3a22-151">型別**ssomanage-enablemapping\<外部帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-151">Type **ssomanage -enablemapping \<external account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3a22-152">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="c3a22-152">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a><span data-ttu-id="c3a22-153">使用命令列為個別類型的分支機構應用程式停用對應</span><span class="sxs-lookup"><span data-stu-id="c3a22-153">To disable mappings for individual type affiliate applications using the command line</span></span>  
  
1.  <span data-ttu-id="c3a22-154">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-154">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="c3a22-155">在 [**執行**] 對話方塊中，輸入**cmd**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-155">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c3a22-156">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="c3a22-156">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="c3a22-157">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="c3a22-157">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="c3a22-158">型別**ssomanage-disablemapping\<外部帳戶名稱\>\<應用程式名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="c3a22-158">Type **ssomanage -disablemapping \<external account name\> \<application name\>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3a22-159">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="c3a22-159">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a22-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3a22-160">See Also</span></span>  
 [<span data-ttu-id="c3a22-161">主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="c3a22-161">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)