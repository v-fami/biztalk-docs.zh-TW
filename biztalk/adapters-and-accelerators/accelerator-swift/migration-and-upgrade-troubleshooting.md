---
title: "移轉和升級的疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading, troubleshooting
- troubleshooting, upgrading
- troubleshooting, migrating
- migrating, troubleshooting
ms.assetid: 6e6c0ff9-7897-4de6-9e9b-b502b3a1785b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c0e2a18b1cdba47c999150b5bc52c0b016aec61
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="migration-and-upgrade-troubleshooting"></a><span data-ttu-id="1c884-102">移轉和升級的疑難排解</span><span class="sxs-lookup"><span data-stu-id="1c884-102">Migration and Upgrade Troubleshooting</span></span>
## <a name="assemblies-need-to-be-undeployed-before-an-upgrade"></a><span data-ttu-id="1c884-103">需要升級之前解除部署組件</span><span class="sxs-lookup"><span data-stu-id="1c884-103">Assemblies need to be undeployed before an upgrade</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="1c884-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="1c884-104">Symptom</span></span>  
 <span data-ttu-id="1c884-105">當您嘗試升級 A4SWIFT 時，升級程序將會失敗。</span><span class="sxs-lookup"><span data-stu-id="1c884-105">When you attempt to upgrade A4SWIFT, the upgrade process fails.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="1c884-106">可能的原因</span><span class="sxs-lookup"><span data-stu-id="1c884-106">Possible Cause</span></span>  
 <span data-ttu-id="1c884-107">完成升級後仍部署下列 A4SWIFT 組件： Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration、 Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas，Microsoft.Solutions.FinancialServices.SWIFT.MrsrService。</span><span class="sxs-lookup"><span data-stu-id="1c884-107">The following A4SWIFT assemblies are still deployed when the upgrade is done:  Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration, Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas, Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c884-108">您不必重新部署 Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas。</span><span class="sxs-lookup"><span data-stu-id="1c884-108">You do not have to redeploy Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.</span></span> <span data-ttu-id="1c884-109">安裝程式重新部署該組件。</span><span class="sxs-lookup"><span data-stu-id="1c884-109">The installation program redeploys that assembly.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="1c884-110">方案</span><span class="sxs-lookup"><span data-stu-id="1c884-110">Solution</span></span>  
 <span data-ttu-id="1c884-111">手動解除部署以下列順序中的四個 A4SWIFT 組件：</span><span class="sxs-lookup"><span data-stu-id="1c884-111">Manually undeploy the four A4SWIFT assemblies in the following order:</span></span>  
  
-   <span data-ttu-id="1c884-112">Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration</span><span class="sxs-lookup"><span data-stu-id="1c884-112">Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration</span></span>  
  
-   <span data-ttu-id="1c884-113">Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas</span><span class="sxs-lookup"><span data-stu-id="1c884-113">Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas</span></span>  
  
-   <span data-ttu-id="1c884-114">Microsoft.Solutions.FinancialServices.SWIFT.MrsrService。</span><span class="sxs-lookup"><span data-stu-id="1c884-114">Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.</span></span>  
  
 <span data-ttu-id="1c884-115">您已升級之後，重新部署這些組件 (使用**BTSTask.exe**) 相反的順序。</span><span class="sxs-lookup"><span data-stu-id="1c884-115">After you have upgraded, redeploy these assemblies (using **BTSTask.exe**) in the reverse order.</span></span>  
  
## <a name="an-upgrade-removes-access-permissions-for-the-service-folder"></a><span data-ttu-id="1c884-116">升級會移除服務資料夾存取權限</span><span class="sxs-lookup"><span data-stu-id="1c884-116">An upgrade removes access permissions for the Service folder</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="1c884-117">徵兆</span><span class="sxs-lookup"><span data-stu-id="1c884-117">Symptom</span></span>  
 <span data-ttu-id="1c884-118">若要在升級後[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，%programfiles%\Microsoft BizTalk Accelerator for SWIFT\Service 資料夾的存取權限不正確。</span><span class="sxs-lookup"><span data-stu-id="1c884-118">After an upgrade to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], the access permission for the %programfiles%\Microsoft BizTalk Accelerator for SWIFT\Service folder is incorrect.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="1c884-119">可能的原因</span><span class="sxs-lookup"><span data-stu-id="1c884-119">Possible Cause</span></span>  
 <span data-ttu-id="1c884-120">當您升級至[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，升級程序從 %programfiles%\Microsoft BizTalk Accelerator for SWIFT\Service 資料夾移除 A4SWIFT 系統管理員和 A4SWIFT 使用者群組的存取權限。</span><span class="sxs-lookup"><span data-stu-id="1c884-120">When you upgrade to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], the upgrade process removes access permissions for the A4SWIFT Administrators and A4SWIFT Users groups from the %programfiles%\Microsoft BizTalk Accelerator for SWIFT\Service folder.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="1c884-121">方案</span><span class="sxs-lookup"><span data-stu-id="1c884-121">Solution</span></span>  
 <span data-ttu-id="1c884-122">如果您遇到此問題，手動設定的服務資料夾的下列存取權限：</span><span class="sxs-lookup"><span data-stu-id="1c884-122">If you encounter this problem, manually set the following access permissions for the Service folder:</span></span>  
  
|<span data-ttu-id="1c884-123">群組或使用者名稱</span><span class="sxs-lookup"><span data-stu-id="1c884-123">Group or User Name</span></span>|<span data-ttu-id="1c884-124">權限</span><span class="sxs-lookup"><span data-stu-id="1c884-124">Permission</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="1c884-125">A4SWIFT 系統管理員</span><span class="sxs-lookup"><span data-stu-id="1c884-125">A4SWIFT Administrators</span></span>|<span data-ttu-id="1c884-126">完整控制</span><span class="sxs-lookup"><span data-stu-id="1c884-126">Full Control</span></span>|  
|<span data-ttu-id="1c884-127">A4SWIFT 使用者</span><span class="sxs-lookup"><span data-stu-id="1c884-127">A4SWIFT Users</span></span>|<span data-ttu-id="1c884-128">閱讀及執行</span><span class="sxs-lookup"><span data-stu-id="1c884-128">Read & Execute</span></span>|  
  
 <span data-ttu-id="1c884-129">若要設定這些權限，請繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1c884-129">To set these permissions, proceed as follows:</span></span>  
  
 <span data-ttu-id="1c884-130">在[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，移至*%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Service。</span><span class="sxs-lookup"><span data-stu-id="1c884-130">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Service.</span></span>  
  
1.  <span data-ttu-id="1c884-131">以滑鼠右鍵按一下 [服務] 資料夾中，按一下**屬性**，然後按一下 [**安全性**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1c884-131">Right-click the Service folder, click **Properties**, and then click the **Security** tab.</span></span>  
  
2.  <span data-ttu-id="1c884-132">在 群組或使用者名稱 窗格的 服務內容 對話方塊，按一下**新增**，輸入 ***\<伺服器名稱\>*\A4SWIFT 管理員**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="1c884-132">In the Group or user names pane of the Service Properties dialog box, click **Add**, enter ***\<server name\>*\A4SWIFT Administrators**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1c884-133">如果 A4SWIFT Administrators 群組的網域群組，請輸入 ***\<網域名稱\>*\A4SWIFT 管理員**。</span><span class="sxs-lookup"><span data-stu-id="1c884-133">If the A4SWIFT Administrators group is a domain group, enter ***\<domain name\>*\A4SWIFT Administrators**.</span></span>  
  
3.  <span data-ttu-id="1c884-134">重複步驟 2 的 ***\<伺服器名稱\>*\A4SWIFT 使用者**，或  **\<*網域名稱*\>\A4SWIFT 使用者 * * 如果 A4SWIFT 使用者群組是網域群組。</span><span class="sxs-lookup"><span data-stu-id="1c884-134">Repeat step 2 for ***\<server name\>*\A4SWIFT Users**, or **\<*domain name*\>\A4SWIFT Users** if the A4SWIFT Users group is a domain group.</span></span>  
  
4.  <span data-ttu-id="1c884-135">在 [群組或使用者名稱] 窗格中選取**A4SWIFT 管理員**。</span><span class="sxs-lookup"><span data-stu-id="1c884-135">In the Group or user names pane, select **A4SWIFT Administrators**.</span></span> <span data-ttu-id="1c884-136">在 [權限] 窗格中，選取**允許**如**完全控制**。</span><span class="sxs-lookup"><span data-stu-id="1c884-136">In the Permissions pane, select **Allow** for **Full Control**.</span></span>  
  
5.  <span data-ttu-id="1c884-137">在 [群組或使用者名稱] 窗格中選取**A4SWIFT 使用者**。</span><span class="sxs-lookup"><span data-stu-id="1c884-137">In the Group or user names pane, select **A4SWIFT Users**.</span></span> <span data-ttu-id="1c884-138">在 權限 窗格中，按一下 **允許**如**讀取與執行**，**列出資料夾內容**，和**讀取**。</span><span class="sxs-lookup"><span data-stu-id="1c884-138">In the Permissions pane, click **Allow** for **Read & Execute**, **List Folder Contents**, and **Read**.</span></span>  
  
6.  <span data-ttu-id="1c884-139">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1c884-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c884-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="1c884-140">See Also</span></span>  
 [<span data-ttu-id="1c884-141">疑難排解：問題與解決方式</span><span class="sxs-lookup"><span data-stu-id="1c884-141">Troubleshooting: Issues and Resolutions</span></span>](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)