---
title: "如何設定 SSO 伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, selecting [SSO]
- SSO, selecting servers
- managing [SSO], selecting servers
- SSOManage [SSO]
ms.assetid: a0b0176d-b426-4ab1-8a7e-1f96f4214683
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96631531cc28ac1bed4ea2b2b56b4b8f9b80c281
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-the-sso-server"></a><span data-ttu-id="79421-102">如何設定 SSO 伺服器</span><span class="sxs-lookup"><span data-stu-id="79421-102">How to Set the SSO Server</span></span>
<span data-ttu-id="79421-103">每次使用 ssomanage 時，您必須先將使用者指向您要連接的「單一登入」伺服器。</span><span class="sxs-lookup"><span data-stu-id="79421-103">Each time you use ssomanage, you must first point the user to the Single Sign-On server you want to connect to.</span></span>  
  
 <span data-ttu-id="79421-104">您可以使用下列其中一種作法：</span><span class="sxs-lookup"><span data-stu-id="79421-104">You can do this in one of two ways:</span></span>  
  
-   <span data-ttu-id="79421-105">個別使用者可以將自己指向正確的「單一登入伺服器」。</span><span class="sxs-lookup"><span data-stu-id="79421-105">Individual users can point themselves to the correct Single Sign-On Server.</span></span>  
  
-   <span data-ttu-id="79421-106">「單一登入」伺服器的本機電腦系統管理員可以將「單一登入使用者」帳戶的所有成員指向這個伺服器。</span><span class="sxs-lookup"><span data-stu-id="79421-106">A local computer administrator for the Single Sign-On server can point all the members of the Single Sign-On Users account to this server.</span></span>  
  
### <a name="to-set-the-enterprise-single-sign-on-server-using-the-mmc-snap-in"></a><span data-ttu-id="79421-107">使用 MMC 嵌入式管理單元設定「企業單一登入伺服器」</span><span class="sxs-lookup"><span data-stu-id="79421-107">To set the Enterprise Single Sign-On Server using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="79421-108">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="79421-108">Click **Start**, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="79421-109">在 MMC 嵌入式管理單元在**主控台根目錄**，以滑鼠右鍵按一下**企業單一登入**，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="79421-109">In the MMC Snap-In under the **Console Root**, right-click **Enterprise Single Sign-On**, and click **Select**.</span></span>  
  
3.  <span data-ttu-id="79421-110">瀏覽到想要的伺服器。</span><span class="sxs-lookup"><span data-stu-id="79421-110">Browse to the desired server.</span></span>  
  
4.  <span data-ttu-id="79421-111">視情況選取**設定所有使用者的 SSO 伺服器**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="79421-111">If appropriate, select the **Set SSO Server for all users** check box.</span></span>  
  
5.  <span data-ttu-id="79421-112">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="79421-112">Click **OK**.</span></span>  
  
### <a name="to-set-the-enterprise-single-sign-on-server-for-a-single-user-using-the-command-line"></a><span data-ttu-id="79421-113">使用命令列設定單一使用者的「企業單一登入」</span><span class="sxs-lookup"><span data-stu-id="79421-113">To set the Enterprise Single Sign-On Server for a single user using the command line</span></span>  
  
1.  <span data-ttu-id="79421-114">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="79421-114">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="79421-115">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="79421-115">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="79421-116">預設安裝目錄是**\<磁碟機 >**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="79421-116">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="79421-117">型別**ssomanage – server \<SSO 伺服器名稱 >**，其中 **\<SSO 伺服器名稱 >**是單一登入伺服器的使用者想要連接到的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="79421-117">Type **ssomanage –server \<SSO server name>**, where **\<SSO server name>** is the computer name of the Single Sign-On Server the user wants to connect to.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79421-118">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="79421-118">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-set-the-enterprise-single-sign-on-server-for-all-users-using-the-command-line"></a><span data-ttu-id="79421-119">使用命令列設定所有使用者的「企業單一登入」</span><span class="sxs-lookup"><span data-stu-id="79421-119">To set the Enterprise Single Sign-On Server for all users using the command line</span></span>  
  
1.  <span data-ttu-id="79421-120">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="79421-120">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="79421-121">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="79421-121">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="79421-122">預設安裝目錄是**\<磁碟機 >**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="79421-122">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="79421-123">型別**ssomanage – serverall \<SSO 伺服器名稱 >**，其中 **\<SSO 伺服器名稱 >**是單一登入伺服器的電腦名稱的單一登入使用者的所有成員將指向帳戶。</span><span class="sxs-lookup"><span data-stu-id="79421-123">Type **ssomanage –serverall \<SSO server name>**, where **\<SSO server name>** is the computer name of the Single Sign-On Server all members of the Single Sign-On Users account will be pointed to.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79421-124">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="79421-124">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-determine-the-enterprise-single-sign-on-server-to-which-a-user-is-connected-using-the-command-line"></a><span data-ttu-id="79421-125">使用命令列決定使用者將連接的「企業單一登入伺服器」</span><span class="sxs-lookup"><span data-stu-id="79421-125">To determine the Enterprise Single Sign-On Server to which a user is connected using the command line</span></span>  
  
1.  <span data-ttu-id="79421-126">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="79421-126">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="79421-127">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="79421-127">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="79421-128">預設安裝目錄是**\<磁碟機 >**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="79421-128">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="79421-129">型別**ssomanage – showserver**。</span><span class="sxs-lookup"><span data-stu-id="79421-129">Type **ssomanage –showserver**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79421-130">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="79421-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79421-131">這個命令會顯示目前使用者以及其他使用者 (若存在) 的設定。</span><span class="sxs-lookup"><span data-stu-id="79421-131">This command displays the settings for the current user as well as for other users if they exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79421-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79421-132">See Also</span></span>  
 <span data-ttu-id="79421-133">[如何啟用 SSO](../core/how-to-enable-sso.md) </span><span class="sxs-lookup"><span data-stu-id="79421-133">[How to Enable SSO](../core/how-to-enable-sso.md) </span></span>  
 <span data-ttu-id="79421-134">[如何停用 SSO](../core/how-to-disable-sso.md) </span><span class="sxs-lookup"><span data-stu-id="79421-134">[How to Disable SSO](../core/how-to-disable-sso.md) </span></span>  
 <span data-ttu-id="79421-135">[如何顯示 SSO 資料庫資訊](../core/how-to-display-the-sso-database-information.md) </span><span class="sxs-lookup"><span data-stu-id="79421-135">[How to Display the SSO Database Information](../core/how-to-display-the-sso-database-information.md) </span></span>  
 [<span data-ttu-id="79421-136">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="79421-136">Using SSO</span></span>](../core/using-sso.md)