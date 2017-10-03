---
title: "如何建立分支機構應用程式主控件初始化的 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], host initiated SSO
- creating, applications [SSO]
- host initiated SSO, creating affiliate applications
ms.assetid: 06202d21-055a-46bc-acff-da461f5673f1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23525d3b2f72d59e2b0f44257c707f22e6bc2bab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-affiliate-applications-for-host-initiated-sso"></a><span data-ttu-id="758f3-102">如何建立分支機構應用程式主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="758f3-102">How to Create Affiliate Applications for Host Initiated SSO</span></span>
<span data-ttu-id="758f3-103">您可以定義兩種類型的應用程式：</span><span class="sxs-lookup"><span data-stu-id="758f3-103">You can define two types of applications:</span></span>  
  
-   <span data-ttu-id="758f3-104">**個別**是 1 到 1 之間的關聯性的 Windows 使用者和非 Windows 使用者。</span><span class="sxs-lookup"><span data-stu-id="758f3-104">**Individual** There is a 1 to 1 relationship between Windows users and non-Windows users.</span></span>  
  
-   <span data-ttu-id="758f3-105">**主機群組**多個非 Windows 使用者可以對應到相同的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="758f3-105">**Host Group** Multiple non-Windows users can be mapped to the same Windows account.</span></span>  
  
### <a name="to-create-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="758f3-106">若要使用 MMC 嵌入式管理單元建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="758f3-106">To create an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="758f3-107">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="758f3-107">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="758f3-108">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="758f3-108">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="758f3-109">以滑鼠右鍵按一下**分支機構應用程式**，然後按一下 **建立應用程式**開啟**企業單一登入應用程式精靈**。</span><span class="sxs-lookup"><span data-stu-id="758f3-109">Right-click **Affiliate Applications**, and then click **Create Application** to open the **Enterprise Single Sign-On Application Wizard**.</span></span>  
  
4.  <span data-ttu-id="758f3-110">使用精靈選取分支機構應用程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="758f3-110">Use the wizard to select the properties of your affiliate application.</span></span>  
  
### <a name="to-create-an-individual-type-affiliate-application-using-the-command-line"></a><span data-ttu-id="758f3-111">使用命令列建立個別類型的分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="758f3-111">To create an individual type affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="758f3-112">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="758f3-112">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="758f3-113">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="758f3-113">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="758f3-114">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="758f3-114">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="758f3-115">預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="758f3-115">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="758f3-116">型別**ssomanage – createapps \<AffApp.xml >**，其中 AffApp.xml 是 xml 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="758f3-116">Type **ssomanage –createapps \<AffApp.xml>**, where AffApp.xml is the name of the xml file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="758f3-117">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="758f3-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
     <span data-ttu-id="758f3-118">範例檔案如下所示：</span><span class="sxs-lookup"><span data-stu-id="758f3-118">A sample file is shown below:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
      <application name="SSOApp_Host1">  
        <description>An Individual Type Affiliate Application for Host Initiated SSO</description>  
        <contact>someone@companyname.com</contact>  
        <appUserAccount>DomainName\AppUserGroup_HISSO</appUserAccount>  
        <appAdminAccount>DomainName\AppAdminGroup_HISSO</appAdminAccount>  
        <field ordinal="0" label="User ID" masked="no" />  
        <field ordinal="1" label="Password" masked="yes" />  
        <flags windowsInitiatedSSO="no" enableApp="yes" />  
      </application>  
    </SSO>  
  
    ```  
  
### <a name="to-create-a-host-group-type-affiliate-application-using-the-command-line"></a><span data-ttu-id="758f3-119">使用命令列建立主控件群組類型的分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="758f3-119">To create a host group type affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="758f3-120">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="758f3-120">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="758f3-121">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="758f3-121">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="758f3-122">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="758f3-122">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="758f3-123">預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="758f3-123">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="758f3-124">型別**ssomanage – createapps \<AffApp.xml >**，其中 AffApp.xml 是 xml 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="758f3-124">Type **ssomanage –createapps \<AffApp.xml>**, where AffApp.xml is the name of the xml file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="758f3-125">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="758f3-125">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
     <span data-ttu-id="758f3-126">範例檔案如下所示：</span><span class="sxs-lookup"><span data-stu-id="758f3-126">A sample file is shown below:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
      <application name="SSOApp_HostGroupApp1">  
        <description>A Group Type Affiliate Application for Host Initiated SSO associating multiple non-Windows user to a single Windows user account(DomainName\WindowsUserAccount1)</description>  
        <contact>someone@companyname.com</contact>  
        <windowsAccount>DomainName\WindowsUserAccount1</windowsAccount>  
        <appAdminAccount>DomainName\AppAdminGroup_HISSO</appAdminAccount>  
        <field ordinal="0" label="User ID" masked="no" />  
        <field ordinal="1" label="Password" masked="yes" />  
        <flags  enableApp="yes" />  
      </application>  
    </SSO>  
  
    ```  
  
### <a name="to-create-an-affiliate-application-supporting-both-windows-initiated-sso-and-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="758f3-127">使用命令列建立同時支援 Windows 初始化的 SSO 與主控件初始化的 SSO 之分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="758f3-127">To create an affiliate application supporting both Windows initiated SSO and host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="758f3-128">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="758f3-128">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="758f3-129">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="758f3-129">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="758f3-130">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="758f3-130">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="758f3-131">預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="758f3-131">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="758f3-132">型別**ssomanage – createapps \<AffApp.xml >**，其中 AffApp.xml 是 xml 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="758f3-132">Type **ssomanage –createapps \<AffApp.xml>**, where AffApp.xml is the name of the xml file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="758f3-133">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="758f3-133">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
     <span data-ttu-id="758f3-134">範例檔案如下所示：</span><span class="sxs-lookup"><span data-stu-id="758f3-134">A sample file is shown below:</span></span>  
  
    ```  
    <?xml version="1.0" ?>   
    - <SSO>  
    - <application name="SSOApp1">  
      <description>An Individual Type Affiliate Application for both Host Initiated SSO and Windows Initiated SSO</description>   
      <contact>someone@companyname.com</contact>   
      <appUserAccount>DomainName\AppUserGroup</appUserAccount>   
      <appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>   
      <field ordinal="0" label="User ID" masked="no" />   
      <field ordinal="1" label="Password" masked="yes" />   
      <flags  enableApp="yes" />   
      </application>  
      </SSO>  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="758f3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="758f3-135">See Also</span></span>  
 [<span data-ttu-id="758f3-136">主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="758f3-136">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)