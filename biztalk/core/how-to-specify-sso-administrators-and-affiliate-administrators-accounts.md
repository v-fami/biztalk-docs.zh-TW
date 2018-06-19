---
title: 如何指定 SSO 系統管理員和分支機構系統管理員帳戶 |Microsoft 文件
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
ms.openlocfilehash: 6c96e2d99bd6071098a65b3635bb466de44a455d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25972716"
---
# <a name="how-to-specify-sso-administrators-and-affiliate-administrators-accounts"></a><span data-ttu-id="fefeb-102">如何指定 SSO 系統管理員和分支機構系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="fefeb-102">How to Specify SSO Administrators and Affiliate Administrators Accounts</span></span>
<span data-ttu-id="fefeb-103">「企業單一登入」(SSO) 和「分支機構管理員」帳戶可以是主控件群組或個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="fefeb-103">The Enterprise Single Sign-On (SSO) Administrators and Affiliate Administrators accounts can be host group or individual accounts.</span></span> <span data-ttu-id="fefeb-104">設定 SSO 系統之前，必須先建立這些帳戶。</span><span class="sxs-lookup"><span data-stu-id="fefeb-104">You must create these accounts before you configure the SSO system.</span></span>  
  
 <span data-ttu-id="fefeb-105">使用網域帳戶時，必須建立「SSO 系統管理員」和「SSO 分支機構系統管理員」帳戶，以做為網域控制站中的網域全域安全性群組。</span><span class="sxs-lookup"><span data-stu-id="fefeb-105">When using domain accounts, you must create the SSO Administrators and SSO Affiliate Administrators accounts as a domain global security groups in the domain controller.</span></span> <span data-ttu-id="fefeb-106">網域管理員必須建立這些帳戶。</span><span class="sxs-lookup"><span data-stu-id="fefeb-106">The domain administrator must create these accounts.</span></span>  
  
 <span data-ttu-id="fefeb-107">您必須在 SSO 資料庫中指定「單一登入管理員」和「分支機構管理員」帳戶。</span><span class="sxs-lookup"><span data-stu-id="fefeb-107">You must specify the Single Sign-On Administrators and Affiliate Administrators accounts in the SSO database.</span></span> <span data-ttu-id="fefeb-108">更新 SSO 資料庫的「SSO 系統管理員」群組前，必須先停用「單一登入」系統。</span><span class="sxs-lookup"><span data-stu-id="fefeb-108">You must disable the Single Sign-On system before you update the SSO database with the SSO Administrators group.</span></span>  
  
 <span data-ttu-id="fefeb-109">下列 XML 程式碼顯示用來更新 SSO 資料庫的 XML 範例</span><span class="sxs-lookup"><span data-stu-id="fefeb-109">The following XML code shows a sample XML for updating the SSO database:</span></span>  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
</globalInfo>  
</sso>  
```  
  
> [!NOTE]
>  <span data-ttu-id="fefeb-110">「組態精靈」會在 SSO 資料庫中自動指定 SSO 系統管理員和 SSO 分支機構系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="fefeb-110">The Configuration Wizard automatically specifies the SSO administrator and SSO affiliate administrator groups in the SSO database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fefeb-111">如果未設定 SSO，使用者應該檢查混合模式網域中是否正在使用的網域本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="fefeb-111">If SSO does not configure, users should check whether Domain Local Accounts are being used in a mixed-mode domain.</span></span>  
  
### <a name="to-disable-the-enterprise-single-sign-on-system-using-the-mmc-snap-in"></a><span data-ttu-id="fefeb-112">使用 MMC 嵌入式管理單元停用企業單一登入系統</span><span class="sxs-lookup"><span data-stu-id="fefeb-112">To disable the Enterprise Single Sign-On system using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="fefeb-113">在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-113">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="fefeb-114">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="fefeb-114">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="fefeb-115">以滑鼠右鍵按一下 **系統**, ，然後按一下  **停用**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-115">Right-click **System**, and then click **Disable**.</span></span>  
  
### <a name="to-disable-the-enterprise-single-sign-on-system-using-the-command-line"></a><span data-ttu-id="fefeb-116">使用命令列停用企業單一登入系統</span><span class="sxs-lookup"><span data-stu-id="fefeb-116">To disable the Enterprise Single Sign-On system using the command line</span></span>  
  
1.  <span data-ttu-id="fefeb-117">在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-117">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="fefeb-118">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="fefeb-118">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="fefeb-119">預設安裝目錄是\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="fefeb-119">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="fefeb-120">型別 **ssomanage** –**disablesso**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-120">Type **ssomanage** –**disablesso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fefeb-121">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="fefeb-121">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-update-the-sso-database-using-the-mmc-snap-in"></a><span data-ttu-id="fefeb-122">若要使用 MMC 嵌入式管理單元更新 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="fefeb-122">To update the SSO database using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="fefeb-123">在 **啟動** ] 功能表上，按一下 [ **所有程式**, ，**Microsoft 企業單一登入**, ，然後 **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-123">On the **Start** menu, click **All Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="fefeb-124">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="fefeb-124">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="fefeb-125">以滑鼠右鍵按一下 **系統**, ，然後按一下  **更新**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-125">Right-click **System**, and then click **Update**.</span></span>  
  
### <a name="to-update-the-sso-database-using-the-command-line"></a><span data-ttu-id="fefeb-126">使用命令列更新 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="fefeb-126">To update the SSO database using the command line</span></span>  
  
1.  <span data-ttu-id="fefeb-127">在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-127">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="fefeb-128">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="fefeb-128">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="fefeb-129">預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="fefeb-129">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="fefeb-130">型別 * * ssomanage – updatedb *\<更新檔案\>* * *，其中*\<更新檔案\>* 是 XML 檔案的名稱與路徑。</span><span class="sxs-lookup"><span data-stu-id="fefeb-130">Type **ssomanage –updatedb *\<update file\>***, where *\<update file\>* is the path and name of the XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fefeb-131">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="fefeb-131">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-enable-the-enterprise-single-sign-on-system-using-the-mmc-snap-in"></a><span data-ttu-id="fefeb-132">使用 MMC 嵌入式管理單元啟用企業單一登入系統</span><span class="sxs-lookup"><span data-stu-id="fefeb-132">To enable the Enterprise Single Sign-On system using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="fefeb-133">在 **啟動** ] 功能表上，按一下 [ **所有程式**, ，**Microsoft 企業單一登入**, ，然後 **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-133">On the **Start** menu, click **All Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="fefeb-134">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="fefeb-134">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="fefeb-135">以滑鼠右鍵按一下 **系統**, ，然後按一下  **啟用**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-135">Right-click **System**, and then click **Enable**.</span></span>  
  
### <a name="to-enable-the-enterprise-single-sign-on-system-using-the-command-line"></a><span data-ttu-id="fefeb-136">使用命令列啟用企業單一登入系統</span><span class="sxs-lookup"><span data-stu-id="fefeb-136">To enable the Enterprise Single Sign-On system using the command line</span></span>  
  
1.  <span data-ttu-id="fefeb-137">在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-137">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="fefeb-138">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="fefeb-138">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="fefeb-139">預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="fefeb-139">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="fefeb-140">型別 **ssomanage – enablesso**。</span><span class="sxs-lookup"><span data-stu-id="fefeb-140">Type **ssomanage –enablesso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fefeb-141">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="fefeb-141">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fefeb-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fefeb-142">See Also</span></span>  
 [<span data-ttu-id="fefeb-143">SSO 使用者群組</span><span class="sxs-lookup"><span data-stu-id="fefeb-143">SSO User Groups</span></span>](../core/sso-user-groups.md)