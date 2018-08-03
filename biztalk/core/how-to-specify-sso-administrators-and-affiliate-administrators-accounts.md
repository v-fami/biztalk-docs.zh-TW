---
title: 如何指定 SSO 系統管理員和分支機構系統管理員帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administrator accounts, SSO
- enabling, SSO
- SSO, enabling
- disabling, SSO
- SSO, disabling
- managing [SSO], configuring administrator accounts
- managing [SSO], enabling
- managing [SSO], disabling
- SSO, administrator accounts
ms.assetid: 6c300e09-b781-45de-b2da-b1083164a1c0
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab6a40db19ae42f0ba4007fd8044d7d7aa086adb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968239"
---
# <a name="how-to-specify-sso-administrators-and-affiliate-administrators-accounts"></a><span data-ttu-id="64109-102">如何指定 SSO 系統管理員和分支機構系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="64109-102">How to Specify SSO Administrators and Affiliate Administrators Accounts</span></span>
<span data-ttu-id="64109-103">「企業單一登入」(SSO) 和「分支機構管理員」帳戶可以是主控件群組或個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="64109-103">The Enterprise Single Sign-On (SSO) Administrators and Affiliate Administrators accounts can be host group or individual accounts.</span></span> <span data-ttu-id="64109-104">設定 SSO 系統之前，必須先建立這些帳戶。</span><span class="sxs-lookup"><span data-stu-id="64109-104">You must create these accounts before you configure the SSO system.</span></span>  
  
 <span data-ttu-id="64109-105">使用網域帳戶時，必須建立「SSO 系統管理員」和「SSO 分支機構系統管理員」帳戶，以做為網域控制站中的網域全域安全性群組。</span><span class="sxs-lookup"><span data-stu-id="64109-105">When using domain accounts, you must create the SSO Administrators and SSO Affiliate Administrators accounts as a domain global security groups in the domain controller.</span></span> <span data-ttu-id="64109-106">網域管理員必須建立這些帳戶。</span><span class="sxs-lookup"><span data-stu-id="64109-106">The domain administrator must create these accounts.</span></span>  
  
 <span data-ttu-id="64109-107">您必須在 SSO 資料庫中指定「單一登入管理員」和「分支機構管理員」帳戶。</span><span class="sxs-lookup"><span data-stu-id="64109-107">You must specify the Single Sign-On Administrators and Affiliate Administrators accounts in the SSO database.</span></span> <span data-ttu-id="64109-108">更新 SSO 資料庫的「SSO 系統管理員」群組前，必須先停用「單一登入」系統。</span><span class="sxs-lookup"><span data-stu-id="64109-108">You must disable the Single Sign-On system before you update the SSO database with the SSO Administrators group.</span></span>  
  
 <span data-ttu-id="64109-109">下列 XML 程式碼顯示用來更新 SSO 資料庫的 XML 範例</span><span class="sxs-lookup"><span data-stu-id="64109-109">The following XML code shows a sample XML for updating the SSO database:</span></span>  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
</globalInfo>  
</sso>  
```  
  
> [!NOTE]
>  <span data-ttu-id="64109-110">「組態精靈」會在 SSO 資料庫中自動指定 SSO 系統管理員和 SSO 分支機構系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="64109-110">The Configuration Wizard automatically specifies the SSO administrator and SSO affiliate administrator groups in the SSO database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64109-111">如果 SSO 未設定，使用者應該檢查混合模式網域中是否正在使用網域本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="64109-111">If SSO does not configure, users should check whether Domain Local Accounts are being used in a mixed-mode domain.</span></span>  
  
### <a name="to-disable-the-enterprise-single-sign-on-system-using-the-mmc-snap-in"></a><span data-ttu-id="64109-112">使用 MMC 嵌入式管理單元停用企業單一登入系統</span><span class="sxs-lookup"><span data-stu-id="64109-112">To disable the Enterprise Single Sign-On system using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="64109-113">在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="64109-113">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="64109-114">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="64109-114">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="64109-115">以滑鼠右鍵按一下**系統**，然後按一下**停用**。</span><span class="sxs-lookup"><span data-stu-id="64109-115">Right-click **System**, and then click **Disable**.</span></span>  
  
### <a name="to-disable-the-enterprise-single-sign-on-system-using-the-command-line"></a><span data-ttu-id="64109-116">使用命令列停用企業單一登入系統</span><span class="sxs-lookup"><span data-stu-id="64109-116">To disable the Enterprise Single Sign-On system using the command line</span></span>  
  
1.  <span data-ttu-id="64109-117">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="64109-117">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="64109-118">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="64109-118">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="64109-119">預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="64109-119">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="64109-120">型別**ssomanage** –**disablesso**。</span><span class="sxs-lookup"><span data-stu-id="64109-120">Type **ssomanage** –**disablesso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64109-121">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="64109-121">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-update-the-sso-database-using-the-mmc-snap-in"></a><span data-ttu-id="64109-122">若要使用 MMC 嵌入式管理單元更新 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="64109-122">To update the SSO database using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="64109-123">在上**開始**功能表上，按一下**所有程式**， **Microsoft 企業單一登入**，然後**SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="64109-123">On the **Start** menu, click **All Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="64109-124">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="64109-124">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="64109-125">以滑鼠右鍵按一下**系統**，然後按一下**更新**。</span><span class="sxs-lookup"><span data-stu-id="64109-125">Right-click **System**, and then click **Update**.</span></span>  
  
### <a name="to-update-the-sso-database-using-the-command-line"></a><span data-ttu-id="64109-126">使用命令列更新 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="64109-126">To update the SSO database using the command line</span></span>  
  
1. <span data-ttu-id="64109-127">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="64109-127">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="64109-128">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="64109-128">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="64109-129">預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="64109-129">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="64109-130">類型 * * ssomanage – updatedb *\<更新檔案\>**<em>，其中 *\<更新檔案\></em>是 XML 檔案的名稱與路徑。</span><span class="sxs-lookup"><span data-stu-id="64109-130">Type **ssomanage –updatedb *\<update file\>**<em>, where *\<update file\></em> is the path and name of the XML file.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="64109-131">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="64109-131">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-enable-the-enterprise-single-sign-on-system-using-the-mmc-snap-in"></a><span data-ttu-id="64109-132">使用 MMC 嵌入式管理單元啟用企業單一登入系統</span><span class="sxs-lookup"><span data-stu-id="64109-132">To enable the Enterprise Single Sign-On system using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="64109-133">在上**開始**功能表上，按一下**所有程式**， **Microsoft 企業單一登入**，然後**SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="64109-133">On the **Start** menu, click **All Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="64109-134">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="64109-134">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="64109-135">以滑鼠右鍵按一下**系統**，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="64109-135">Right-click **System**, and then click **Enable**.</span></span>  
  
### <a name="to-enable-the-enterprise-single-sign-on-system-using-the-command-line"></a><span data-ttu-id="64109-136">使用命令列啟用企業單一登入系統</span><span class="sxs-lookup"><span data-stu-id="64109-136">To enable the Enterprise Single Sign-On system using the command line</span></span>  
  
1.  <span data-ttu-id="64109-137">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="64109-137">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="64109-138">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="64109-138">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="64109-139">預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="64109-139">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="64109-140">型別**ssomanage – enablesso**。</span><span class="sxs-lookup"><span data-stu-id="64109-140">Type **ssomanage –enablesso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64109-141">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="64109-141">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64109-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64109-142">See Also</span></span>  
 [<span data-ttu-id="64109-143">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="64109-143">SSO User Groups</span></span>](../core/sso-user-groups.md)