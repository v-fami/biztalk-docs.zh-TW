---
title: "安裝和設定疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, troubleshooting
- configuring, troubleshooting
- troubleshooting, configuring
- troubleshooting, installing
ms.assetid: 25a2f6c5-c049-4042-8e38-4f7a2556e066
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62cb7d6181c7be44f7095a6c1d1149132df4e21e
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="installation-and-configuration-troubleshooting"></a><span data-ttu-id="ac3ab-102">安裝和設定疑難排解</span><span class="sxs-lookup"><span data-stu-id="ac3ab-102">Installation and Configuration Troubleshooting</span></span>
## <a name="setup-is-unable-to-deploy-the-runtimeschemas-assembly"></a><span data-ttu-id="ac3ab-103">安裝程式無法部署 RuntimeSchemas 組件</span><span class="sxs-lookup"><span data-stu-id="ac3ab-103">Setup is unable to deploy the RuntimeSchemas assembly</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="ac3ab-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="ac3ab-104">Symptom</span></span>  
 <span data-ttu-id="ac3ab-105">A4SWIFT 安裝程式無法部署 RuntimeSchemas.dll。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-105">The A4SWIFT Setup program was unable to deploy RuntimeSchemas.dll.</span></span> <span data-ttu-id="ac3ab-106">如果組件未以手動方式部署在安裝之後，A4SWIFT 組態精靈將會失敗。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-106">If the assembly is not deployed manually after setup, the A4SWIFT Configuration Wizard fails.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="ac3ab-107">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ac3ab-107">Possible Cause</span></span>  
 <span data-ttu-id="ac3ab-108">下列條件的其中一個存在：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-108">One of the following conditions exists:</span></span>  
  
-   <span data-ttu-id="ac3ab-109">當您嘗試將執行 A4SWIFT 的初始安裝已部署的執行階段結構描述組件。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-109">The Runtime Schemas assembly was already deployed when you tried to perform an initial installation of A4SWIFT.</span></span>  
  
-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="ac3ab-110">[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]並未啟動，您嘗試安裝 A4SWIFT 的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-110"> [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] was not started on the computer on which you tried to install A4SWIFT.</span></span>  
  
-   <span data-ttu-id="ac3ab-111">執行階段結構描述組件已經部署，當您嘗試升級 A4SWIFT，且已由另一個組件參考。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-111">The Runtime Schemas assembly was already deployed when you tried to upgrade A4SWIFT, and was referenced by another assembly.</span></span> <span data-ttu-id="ac3ab-112">執行階段結構描述組件由 A4SWIFT 的這個予以防止解除部署升級的程式。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-112">This prevented undeployment of the Runtime Schemas assembly by the A4SWIFT upgrade program.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="ac3ab-113">方案</span><span class="sxs-lookup"><span data-stu-id="ac3ab-113">Solution</span></span>  
 <span data-ttu-id="ac3ab-114">請繼續進行，如下所示，取決於問題的本質而定：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-114">Proceed as follows, depending upon the nature of the problem:</span></span>  
  
-   <span data-ttu-id="ac3ab-115">如果執行階段結構描述組件已經部署，當您嘗試執行 A4SWIFT 的初始安裝時，開啟 [BizTalk 總管] 中[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]，以滑鼠右鍵按一下組件[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]。Solutions.FinancialServices.SWIFT.RuntimeSchemas，然後按一下解除部署。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-115">If the Runtime Schemas assembly was already deployed when you attempted to run an initial installation of A4SWIFT, open BizTalk Explorer in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)], right-click the assembly [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.FinancialServices.SWIFT.RuntimeSchemas, and then click Undeploy.</span></span> <span data-ttu-id="ac3ab-116">使用 BizTalk 部署精靈部署最新版的 RuntimeSchemas.dll 從*%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Assemblies。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-116">Use the BizTalk Deployment Wizard to deploy the latest version of RuntimeSchemas.dll from *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Assemblies.</span></span>  
  
-   <span data-ttu-id="ac3ab-117">如果[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]已不會啟動，啟動[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]中[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]Service Manager。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-117">If [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] was not started, start [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] in the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] Service Manager.</span></span> <span data-ttu-id="ac3ab-118">使用 BizTalk 部署精靈部署最新版的 RuntimeSchemas.dll 從*%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Assemblies。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-118">Use the BizTalk Deployment Wizard to deploy the latest version of RuntimeSchemas.dll from *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Assemblies.</span></span>  
  
-   <span data-ttu-id="ac3ab-119">如果已部署的執行階段結構描述組件，當您嘗試升級 A4SWIFT，且所參考另一個組件，解除部署 BizTalk 總管 中的參考組件，並解除部署 RuntimeSchemas.dll BizTalk 總管 中。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-119">If the Runtime Schemas assembly was already deployed when you tried to upgrade A4SWIFT, and was referenced by another assembly, undeploy the referencing assembly in BizTalk Explorer, and undeploy RuntimeSchemas.dll in BizTalk Explorer.</span></span> <span data-ttu-id="ac3ab-120">使用 BizTalk 部署精靈部署最新版的 RuntimeSchemas.dll 從*%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Assemblies。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-120">Use the BizTalk Deployment Wizard to deploy the latest version of RuntimeSchemas.dll from *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Assemblies.</span></span>  
  
## <a name="after-the-web-components-feature-is-removed-message-repair-and-reconciliation-is-incorrectly-shown-as-uninstalled"></a><span data-ttu-id="ac3ab-121">移除網路元件功能之後，訊息修復和重新調整不正確地顯示為解除安裝</span><span class="sxs-lookup"><span data-stu-id="ac3ab-121">After the Web Components feature is removed, Message Repair and Reconciliation is incorrectly shown as uninstalled</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="ac3ab-122">徵兆</span><span class="sxs-lookup"><span data-stu-id="ac3ab-122">Symptom</span></span>  
 <span data-ttu-id="ac3ab-123">移除 Message Repair 和 New Submission 功能 A4SWIFT Web 元件之後，您無法解除安裝、 安裝，或設定訊息修復和重新調整功能 （或 A4SWIFT 元件）。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-123">After you remove the Web Components for Message Repair and New Submission feature of A4SWIFT, you cannot uninstall, install, or configure the Message Repair and Reconciliation feature (or A4SWIFT Components).</span></span> <span data-ttu-id="ac3ab-124">如果安裝了訊息修復和重新調整，A4SWIFT 無法辨識安裝的功能。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-124">If Message Repair and Reconciliation is installed, A4SWIFT does not recognize that the feature is installed.</span></span> <span data-ttu-id="ac3ab-125">如果您嘗試安裝、 修改或移除訊息修復和從新增/移除程式 （控制台中顯示） 中的重新調整，新增/移除程式會指出未安裝此功能。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-125">If you attempt to install, modify, or remove Message Repair and Reconciliation from within Add/Remove Programs (displayed from Control Panel), Add/Remove Programs will indicate that the feature is not installed.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="ac3ab-126">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ac3ab-126">Possible Cause</span></span>  
 <span data-ttu-id="ac3ab-127">已從移除[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員群組之後，您必須安裝 Web 元件，Message Repair 和 New Submission 功能和訊息修復和重新調整功能。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-127">You were removed from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group after you had installed the Web Components for Message Repair and New Submission feature and the Message Repair and Reconciliation feature.</span></span> <span data-ttu-id="ac3ab-128">如果您移除網路元件功能 (可執行的成員，不用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組)、 A4SWIFT 安裝程式將會移除檔案的訊息修復和重新調整功能具有相依性。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-128">If you then remove the Web Components feature (which you can do without being a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group), the A4SWIFT setup program will remove files that the Message Repair and Reconciliation feature has a dependency on.</span></span> <span data-ttu-id="ac3ab-129">這些檔案包括 ConfigFramework.exe。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-129">These files include ConfigFramework.exe.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="ac3ab-130">方案</span><span class="sxs-lookup"><span data-stu-id="ac3ab-130">Solution</span></span>  
 <span data-ttu-id="ac3ab-131">如果您遇到這個問題，繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-131">If you encounter this problem, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="ac3ab-132">在 [電腦管理] 視窗中，加入您自己回[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrator 群組、 登出電腦，並再登入。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-132">In the Computer Management window, add yourself back into the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrator group, log off the computer, and then log back on.</span></span>  
  
2.  <span data-ttu-id="ac3ab-133">重新安裝 Web 元件，Message Repair 和 New Submission 的功能。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-133">Re-install the Web Components for Message Repair and New Submission feature.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac3ab-134">步驟 2 新增 ConfigFramework.exe 回 A4SWIFT 安裝。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-134">Step 2 adds ConfigFramework.exe back into the A4SWIFT installation.</span></span>  
  
3.  <span data-ttu-id="ac3ab-135">重新安裝 MRSR 功能。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-135">Re-install the MRSR feature.</span></span>  
  
4.  <span data-ttu-id="ac3ab-136">如果您還不想 Web 元件 Message Repair 和 New Submission 功能，請將它移除。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-136">If you still do not want the Web Components for Message Repair and New Submission feature, remove it.</span></span>  
  
## <a name="repairing-a4swift-to-add-the-service-folder-can-result-in-improper-access-permissions-for-that-folder"></a><span data-ttu-id="ac3ab-137">修復 A4SWIFT 加入服務資料夾可能會導致該資料夾不適當的存取權限</span><span class="sxs-lookup"><span data-stu-id="ac3ab-137">Repairing A4SWIFT to add the Service folder can result in improper access permissions for that folder</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="ac3ab-138">徵兆</span><span class="sxs-lookup"><span data-stu-id="ac3ab-138">Symptom</span></span>  
 <span data-ttu-id="ac3ab-139">如果您刪除該資料夾*%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Service 與已正確設定的 A4SWIFT 安裝，然後執行 A4SWIFT 回 A4SWIFT 安裝程式來新增伺服器資料夾的修復功能安裝時，[服務] 資料夾的存取權限不是正確的狀態。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-139">If you delete the folder *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Service from a properly configured A4SWIFT installation, and then run the Repair feature of A4SWIFT setup to add the Server folder back in the A4SWIFT installation, the access permissions for the Service folder will not be correct.</span></span> <span data-ttu-id="ac3ab-140">正確的權限是具有完整控制權 A4SWIFT 系統管理員 」 和 「 讀取 」 和 「 執行 A4SWIFT 使用者。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-140">The correct permissions are Full Control for A4SWIFT Administrators and Read & Execute for A4SWIFT Users.</span></span>  
  
 <span data-ttu-id="ac3ab-141">如果您的服務資料夾時執行 A4SWIFT 安裝的修復功能，這也會發生。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-141">This also occurs if you run the Repair feature of A4SWIFT setup when the Service folder exists.</span></span> <span data-ttu-id="ac3ab-142">存取權限所設定的 A4SWIFT 組態精靈，將會覆寫不正確的值。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-142">The access permissions, as set by the A4SWIFT Configuration Wizard, will be overwritten with incorrect values.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="ac3ab-143">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ac3ab-143">Possible Cause</span></span>  
 <span data-ttu-id="ac3ab-144">安裝 Web 元件 Message Repair 和 New Submission 功能加入服務資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-144">Installing the Web Components for Message Repair and New Submission feature adds the Service folder.</span></span> <span data-ttu-id="ac3ab-145">如果您刪除資料夾，然後執行 A4SWIFT 安裝的修復選項，新增訊息修復和新送出的 Web 元件，A4SWIFT 安裝程式不會執行設定精靈 (ConfigFramework.exe) 來設定資料夾的權限。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-145">If you delete the folder and then run the Repair option of A4SWIFT setup to add the Web Components for Message Repair and New Submission, A4SWIFT setup does not run the configuration wizard (ConfigFramework.exe) to set the permissions for the folder.</span></span> <span data-ttu-id="ac3ab-146">因為尚未執行 「 組態精靈 」，所以很難再次執行精靈，重設的設定。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-146">Because the configuration wizard has already been run, it is very difficult to run the wizard again to reset the configuration.</span></span> <span data-ttu-id="ac3ab-147">如此一來，[修復] 選項將會重建所有已刪除的檔案和資料夾，但是它將不會正確地設定存取權限。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-147">As a result, the Repair option will re-create all deleted files and folders, but it will not set access permissions correctly.</span></span>  
  
 <span data-ttu-id="ac3ab-148">如果資料夾存在於執行修復時，修復程序也覆寫服務資料夾的權限。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-148">The repair process also overwrites permissions for the Service folder if the folder exists when repair is run.</span></span> <span data-ttu-id="ac3ab-149">就像之前先執行修復，請刪除服務資料夾的情況下它將會很難執行組態程式設定權限。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-149">As with the case of deleting the Service folder before running repair, it will be very difficult to run the configuration program to set the permissions.</span></span> <span data-ttu-id="ac3ab-150">在本例中，以及，權限可能會不正確，而且您必須手動設定它們。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-150">In this instance, as well, the permissions will be incorrect and you will have to manually set them.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="ac3ab-151">方案</span><span class="sxs-lookup"><span data-stu-id="ac3ab-151">Solution</span></span>  
 <span data-ttu-id="ac3ab-152">如果您遇到此問題，手動設定的服務資料夾的下列存取權限：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-152">If you encounter this problem, manually set the following access permissions for the Service folder:</span></span>  
  
|<span data-ttu-id="ac3ab-153">群組或使用者名稱</span><span class="sxs-lookup"><span data-stu-id="ac3ab-153">Group or User Name</span></span>|<span data-ttu-id="ac3ab-154">權限</span><span class="sxs-lookup"><span data-stu-id="ac3ab-154">Permission</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="ac3ab-155">A4SWIFT 系統管理員</span><span class="sxs-lookup"><span data-stu-id="ac3ab-155">A4SWIFT Administrators</span></span>|<span data-ttu-id="ac3ab-156">完整控制</span><span class="sxs-lookup"><span data-stu-id="ac3ab-156">Full Control</span></span>|  
|<span data-ttu-id="ac3ab-157">A4SWIFT 使用者</span><span class="sxs-lookup"><span data-stu-id="ac3ab-157">A4SWIFT Users</span></span>|<span data-ttu-id="ac3ab-158">閱讀及執行</span><span class="sxs-lookup"><span data-stu-id="ac3ab-158">Read & Execute</span></span>|  
  
 <span data-ttu-id="ac3ab-159">若要設定這些權限，請繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-159">To set these permissions, proceed as follows:</span></span>  
  
 <span data-ttu-id="ac3ab-160">在[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，移至*%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Service。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-160">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Service.</span></span>  
  
1.  <span data-ttu-id="ac3ab-161">以滑鼠右鍵按一下 [服務] 資料夾中，按一下**屬性**，然後按一下 [**安全性**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-161">Right-click the Service folder, click **Properties**, and then click the **Security** tab.</span></span>  
  
2.  <span data-ttu-id="ac3ab-162">在 群組或使用者名稱 窗格的 服務內容 對話方塊，按一下**新增**，輸入 ***\<伺服器名稱\>* \A4SWIFT 管理員**，然後按一下  **確定**.</span><span class="sxs-lookup"><span data-stu-id="ac3ab-162">In the Group or user names pane of the Service Properties dialog box, click **Add**, enter ***\<server name\>*\A4SWIFT Administrators**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac3ab-163">如果 A4SWIFT Administrators 群組的網域群組，請輸入 ***\<網域名稱\>* \A4SWIFT 管理員**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-163">If the A4SWIFT Administrators group is a domain group, enter ***\<domain name\>*\A4SWIFT Administrators**.</span></span>  
  
3.  <span data-ttu-id="ac3ab-164">重複步驟 2 的 ***\<伺服器名稱\>* \A4SWIFT 使用者**，或 **\<*網域名稱*\>\A4SWIFT 使用者**如果A4SWIFT Users 群組是網域群組。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-164">Repeat step 2 for ***\<server name\>*\A4SWIFT Users**, or **\<*domain name*\>\A4SWIFT Users** if the A4SWIFT Users group is a domain group.</span></span>  
  
4.  <span data-ttu-id="ac3ab-165">在 [群組或使用者名稱] 窗格中選取**A4SWIFT 管理員**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-165">In the Group or user names pane, select **A4SWIFT Administrators**.</span></span> <span data-ttu-id="ac3ab-166">在 [權限] 窗格中，選取**允許**如**完全控制**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-166">In the Permissions pane, select **Allow** for **Full Control**.</span></span>  
  
5.  <span data-ttu-id="ac3ab-167">在 [群組或使用者名稱] 窗格中選取**A4SWIFT 使用者**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-167">In the Group or user names pane, select **A4SWIFT Users**.</span></span> <span data-ttu-id="ac3ab-168">在 權限 窗格中，按一下 **允許**如**讀取與執行**，**列出資料夾內容**，和**讀取**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-168">In the Permissions pane, click **Allow** for **Read & Execute**, **List Folder Contents**, and **Read**.</span></span>  
  
6.  <span data-ttu-id="ac3ab-169">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-169">Click **OK**.</span></span>  
  
## <a name="upgrade-results-in-a-side-by-side-installation-of-two-versions-of-a4swift"></a><span data-ttu-id="ac3ab-170">在 A4SWIFT 的兩個版本的並存安裝的升級結果</span><span class="sxs-lookup"><span data-stu-id="ac3ab-170">Upgrade results in a side-by-side installation of two versions of A4SWIFT</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="ac3ab-171">徵兆</span><span class="sxs-lookup"><span data-stu-id="ac3ab-171">Symptom</span></span>  
 <span data-ttu-id="ac3ab-172">當您嘗試升級至[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]，A4SWIFT 的先前版本可能不會完全移除。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-172">When you attempt to upgrade to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], previous versions of A4SWIFT may not be fully removed.</span></span> <span data-ttu-id="ac3ab-173">如果您從控制台執行新增/移除程式，目前和先前版本，可能會顯示目前已安裝的程式清單。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-173">If you run Add/Remove Programs from the Control Panel, the list of Currently Installed Programs might show the current and the previous versions.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="ac3ab-174">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ac3ab-174">Possible Cause</span></span>  
 <span data-ttu-id="ac3ab-175">下列任何一個狀況可能導致發生上述項目：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-175">Any of the following conditions can cause the above to occur:</span></span>  
  
-   <span data-ttu-id="ac3ab-176">嘗試升級的使用者不是成員的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-176">The user attempting to upgrade is not a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
-   <span data-ttu-id="ac3ab-177">[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] (MSSQLSERVER) 服務已停止。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-177">The [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] service (MSSQLSERVER) is stopped.</span></span>  
  
-   <span data-ttu-id="ac3ab-178">您可以執行無訊息升級使用**setup.exe /addlocal**命令。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-178">You performed a silent upgrade using the **setup.exe /addlocal** command.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="ac3ab-179">方案</span><span class="sxs-lookup"><span data-stu-id="ac3ab-179">Solution</span></span>  
 <span data-ttu-id="ac3ab-180">若要防止-並存安裝[!INCLUDE[btaA4SWIFToldest](../../includes/btaa4swiftoldest-md.md)]和[!INCLUDE[btaA4SWIFT2.3abbrev](../../includes/btaa4swift2-3abbrev-md.md)]發生在升級期間，確定您 （登入的使用者） 的成員[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Administrators 群組，而且[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)](MSSQLSERVER) 服務已啟動。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-180">To prevent a side-by-side installation of [!INCLUDE[btaA4SWIFToldest](../../includes/btaa4swiftoldest-md.md)] and [!INCLUDE[btaA4SWIFT2.3abbrev](../../includes/btaa4swift2-3abbrev-md.md)] occurring during upgrade, ensure that you (the logged-on user) are a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group, and that the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] service (MSSQLSERVER) is started.</span></span>  
  
 <span data-ttu-id="ac3ab-181">如果您得到的-並存安裝[!INCLUDE[btaA4SWIFToldest](../../includes/btaa4swiftoldest-md.md)]或[!INCLUDE[btaA4SWIFT2.1abbrev](../../includes/btaa4swift2-1abbrev-md.md)]和[!INCLUDE[btaA4SWIFT2.3abbrev](../../includes/btaa4swift2-3abbrev-md.md)]，繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-181">If you end up with a side-by-side installation of [!INCLUDE[btaA4SWIFToldest](../../includes/btaa4swiftoldest-md.md)] or [!INCLUDE[btaA4SWIFT2.1abbrev](../../includes/btaa4swift2-1abbrev-md.md)] and [!INCLUDE[btaA4SWIFT2.3abbrev](../../includes/btaa4swift2-3abbrev-md.md)], proceed as follows:</span></span>  
  
1.  <span data-ttu-id="ac3ab-182">備份 SWIFT 訊息資料夾中的資料。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-182">Back up the data in the SWIFT Messages folder.</span></span>  
  
2.  <span data-ttu-id="ac3ab-183">登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]BTS Administrators 的成員為群組，並確定 MSSQLSERVER 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-183">Log on to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] as a member of the BTS Administrators group, and ensure that the MSSQLSERVER service is running.</span></span>  
  
3.  <span data-ttu-id="ac3ab-184">移除 A4SWIFT 的先前版本。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-184">Remove the previous version of A4SWIFT.</span></span>  
  
4.  <span data-ttu-id="ac3ab-185">一次升級至 A4SWIFT 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-185">Upgrade to the latest version of A4SWIFT again.</span></span> <span data-ttu-id="ac3ab-186">這次升級將運作，而且將會建立任何-並存安裝。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-186">This time the upgrade will work, and no side-by-side installation will be created.</span></span>  
  
5.  <span data-ttu-id="ac3ab-187">使用 「 BizTalk 部署公用程式，手動解除部署[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]。Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll，然後重新部署它，從 A4SWIFT 安裝位置的組件 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-187">Using the BizTalk Deployment Utility, manually undeploy [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll, and then redeploy it from the Assemblies folder of your A4SWIFT installation location.</span></span> <span data-ttu-id="ac3ab-188">如需這項工具的詳細資訊，請參閱[BRE 部署公用程式](../../adapters-and-accelerators/accelerator-swift/bre-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-188">For more information about this tool, see [BRE Deployment Utility](../../adapters-and-accelerators/accelerator-swift/bre-deployment-utility.md).</span></span>  
  
## <a name="the-uninstall-or-upgrade-process-may-not-complete-correctly-if-you-do-not-restart-when-prompted"></a><span data-ttu-id="ac3ab-189">在解除安裝或升級程序可能未正確完成若未重新出現提示時</span><span class="sxs-lookup"><span data-stu-id="ac3ab-189">The uninstall or upgrade process may not complete correctly if you do not restart when prompted</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="ac3ab-190">徵兆</span><span class="sxs-lookup"><span data-stu-id="ac3ab-190">Symptom</span></span>  
 <span data-ttu-id="ac3ab-191">解除安裝或升級程序未正確完成。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-191">Uninstall or upgrade processes do not complete correctly.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="ac3ab-192">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ac3ab-192">Possible Cause</span></span>  
 <span data-ttu-id="ac3ab-193">如果您不解除部署專案會參考現有的已部署組件，您可能會收到提示，指出您必須重新啟動系統，對 A4SWIFT 組態變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-193">If you have not undeployed a project that references an existing deployed assembly, you may receive a prompt indicating that you must restart your system for A4SWIFT configuration changes to take effect.</span></span> <span data-ttu-id="ac3ab-194">如果您沒有按一下**是**以立即重新啟動，會從全域組件快取中移除指定的部分組件可能不會移除，導致額外的解除安裝或不正確地完成升級程序。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-194">If you do not click **Yes** to restart immediately, some assemblies that were assigned for removal in the global assembly cache may not be removed, causing additional uninstall or upgrade processes to not complete correctly.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="ac3ab-195">方案</span><span class="sxs-lookup"><span data-stu-id="ac3ab-195">Solution</span></span>  
 <span data-ttu-id="ac3ab-196">解除部署任何參考現有的已部署組件的專案，然後再次執行解除安裝或升級程序。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-196">Undeploy any project that references an existing deployed assembly, and then run the uninstall or upgrade process again.</span></span>  
  
## <a name="if-the-iis-admin-service-is-stopped-during-setup-you-must-reconfigure-the-webservice-feature"></a><span data-ttu-id="ac3ab-197">如果在安裝期間停止 IIS 管理服務，您必須重新設定 web 服務功能</span><span class="sxs-lookup"><span data-stu-id="ac3ab-197">If the IIS Admin Service is stopped during setup, you must reconfigure the WebService feature</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="ac3ab-198">徵兆</span><span class="sxs-lookup"><span data-stu-id="ac3ab-198">Symptom</span></span>  
 <span data-ttu-id="ac3ab-199">[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態精靈不會正確設定 web 服務功能。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-199">The [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration Wizard does not configure the WebService feature correctly.</span></span> <span data-ttu-id="ac3ab-200">您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-200">You receive the following error:</span></span>  
  
 <span data-ttu-id="ac3ab-201">「 無法建立 MRSR 成品： 無法連接到遠端伺服器。 」</span><span class="sxs-lookup"><span data-stu-id="ac3ab-201">"Unable to create MRSR artifacts: Unable to connect to the remote server."</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="ac3ab-202">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ac3ab-202">Possible Cause</span></span>  
 <span data-ttu-id="ac3ab-203">IIS Admin Service 已停止執行時[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態精靈。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-203">The IIS Admin Service was stopped when you ran the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration Wizard.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="ac3ab-204">方案</span><span class="sxs-lookup"><span data-stu-id="ac3ab-204">Solution</span></span>  
 <span data-ttu-id="ac3ab-205">若要成功完成設定程序，請繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-205">To complete the configuration process successfully, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="ac3ab-206">關閉[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]設定 主控台。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-206">Close the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console.</span></span>  
  
2.  <span data-ttu-id="ac3ab-207">重新啟動 IIS 管理服務。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-207">Restart the IIS Admin Service.</span></span>  
  
3.  <span data-ttu-id="ac3ab-208">執行*%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Configuration.exe。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-208">Execute *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Configuration.exe.</span></span>  
  
4.  <span data-ttu-id="ac3ab-209">在[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態主控台中，選取**取消設定功能**，然後選取  **WebService**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-209">In the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, select **Unconfigure Features** and then select **WebService**.</span></span>  
  
5.  <span data-ttu-id="ac3ab-210">請在 [設定] 主控台中的 web 服務功能的狀態會顯示為未設定。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-210">Ensure that the status of the WebService feature in the Configuration console is shown as unconfigured.</span></span>  
  
6.  <span data-ttu-id="ac3ab-211">選取**套用組態**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-211">Select **Apply Configuration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac3ab-212">A4SWIFT 組態精靈現在將會正確設定 web 服務功能。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-212">The A4SWIFT Configuration Wizard will now configure the WebService feature correctly.</span></span>  
  
## <a name="a4swift-configuration-will-fail-if-the-biztalkserverapplication-host-was-not-created-in-biztalk-server-configuration"></a><span data-ttu-id="ac3ab-213">如果 biztalkserverapplication 主控件不是在 BizTalk Server 組態，A4SWIFT 組態將會失敗</span><span class="sxs-lookup"><span data-stu-id="ac3ab-213">A4SWIFT configuration will fail if the BizTalkServerApplication host was not created in BizTalk Server configuration</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="ac3ab-214">徵兆</span><span class="sxs-lookup"><span data-stu-id="ac3ab-214">Symptom</span></span>  
 <span data-ttu-id="ac3ab-215">[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]組態精靈不會正確設定 web 服務功能。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-215">The [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration Wizard does not configure the WebService feature correctly.</span></span> <span data-ttu-id="ac3ab-216">您會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-216">You receive the following error:</span></span>  
  
 <span data-ttu-id="ac3ab-217">「 無法建立 MRSR 成品： 物件參考未設定物件的執行個體。"</span><span class="sxs-lookup"><span data-stu-id="ac3ab-217">"Unable to create MRSR artifacts: Object reference not set to an instance of an object."</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="ac3ab-218">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ac3ab-218">Possible Cause</span></span>  
 <span data-ttu-id="ac3ab-219">在 BizTalk Server 執行階段組態期間未建立內含式主控件和主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-219">An In-Process Host and a Host Instance were not created during BizTalk Server Runtime configuration.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="ac3ab-220">方案</span><span class="sxs-lookup"><span data-stu-id="ac3ab-220">Solution</span></span>  
 <span data-ttu-id="ac3ab-221">若要修復 A4SWIFT 組態，請繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-221">To repair the A4SWIFT configuration, proceed as follows:</span></span>  
  
-   <span data-ttu-id="ac3ab-222">在 BizTalk Server 管理 中建立的主機。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-222">Create a host in BizTalk Server Administration.</span></span> <span data-ttu-id="ac3ab-223">沒有需要現在擁有執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-223">There is no need to have a running instance now.</span></span>  
  
-   <span data-ttu-id="ac3ab-224">執行 RepairBAS 工具*%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools 資料夾的 A4SWIFT 安裝。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-224">Run the RepairBAS tool in the *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools folder of the A4SWIFT installation.</span></span>  
  
 <span data-ttu-id="ac3ab-225">若要這樣做，請繼續進行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-225">To do so, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="ac3ab-226">啟動**BizTalk Server 管理**主控台。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-226">Start **BizTalk Server Administration** console.</span></span>  
  
2.  <span data-ttu-id="ac3ab-227">在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**，然後展開**BizTalk 群組**，然後展開**平台設定。**</span><span class="sxs-lookup"><span data-stu-id="ac3ab-227">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, then expand **BizTalk Group**, and then expand **Platform Settings.**</span></span>  
  
3.  <span data-ttu-id="ac3ab-228">以滑鼠右鍵按一下**主機**，指向 **新增**，然後選取**主機**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-228">Right-click **Hosts**, point to **New**, and then select **Host**.</span></span>  
  
4.  <span data-ttu-id="ac3ab-229">在主控件屬性畫面中，在 [一般] 窗格中，輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="ac3ab-229">In the Host Properties screen, in the General pane, enter the following:</span></span>  
  
    -   <span data-ttu-id="ac3ab-230">主機名稱： **[biztalkserverapplication]**</span><span class="sxs-lookup"><span data-stu-id="ac3ab-230">Host name: **BizTalkServerApplication**</span></span>  
  
    -   <span data-ttu-id="ac3ab-231">類型：**同處理序**</span><span class="sxs-lookup"><span data-stu-id="ac3ab-231">Type: **In-Process**</span></span>  
  
    -   <span data-ttu-id="ac3ab-232">Windows 群組：  **\<*網域*\>\BizTalk 應用程式使用者**（或您執行 BizTalk 內含式 BizTalk Server 組態期間設定的帳戶應用程式）</span><span class="sxs-lookup"><span data-stu-id="ac3ab-232">Windows group: **\<*domain*\>\BizTalk Application Users** (or the account that you set up during BizTalk Server configuration for running BizTalk In-Process applications)</span></span>  
  
    -   <span data-ttu-id="ac3ab-233">在 [選項] 區段中，同時選取**允許主控件追蹤**和**可讓預設主控件群組**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-233">In the Options section, select both **Allow Host Tracking** and **Make this the default host in the group**.</span></span>  
  
5.  <span data-ttu-id="ac3ab-234">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-234">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="ac3ab-235">按一下**啟動**然後按一下 執行。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-235">Click **Start** and then click Run.</span></span> <span data-ttu-id="ac3ab-236">型別**cmd** ，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-236">Type **cmd** and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="ac3ab-237">在命令提示字元中，瀏覽至 * %programfiles%***\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-237">At the command prompt, navigate to *%programfiles%***\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools**.</span></span>  
  
8.  <span data-ttu-id="ac3ab-238">型別**RepairBAS.exe** ，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-238">Type **RepairBAS.exe** and then press **Enter**.</span></span>  
  
## <a name="you-must-change-the-bre-deployment-configuration-file-when-running-the-bre-deployment-utility-on-a-64-bit-computer"></a><span data-ttu-id="ac3ab-239">在 64 位元電腦上執行 BRE 部署公用程式時，您必須變更 BRE 部署組態檔</span><span class="sxs-lookup"><span data-stu-id="ac3ab-239">You must change the BRE Deployment configuration file when running the BRE Deployment Utility on a 64-bit computer</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="ac3ab-240">徵兆</span><span class="sxs-lookup"><span data-stu-id="ac3ab-240">Symptom</span></span>  
 <span data-ttu-id="ac3ab-241">BRE 部署公用程式無法正常運作時，您在 64 位元電腦上或在非預設以外的目錄 （C:\Program Files\Microsoft BizTalk Accelerator for SWIFT) 電腦上執行 32 位元。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-241">The BRE Deployment Utility does not work correctly when you run it on a 64-bit computer or in a non-default directory (other than C:\Program Files\Microsoft BizTalk Accelerator for SWIFT) on a 32-bit computer.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="ac3ab-242">可能的原因</span><span class="sxs-lookup"><span data-stu-id="ac3ab-242">Possible Cause</span></span>  
 <span data-ttu-id="ac3ab-243">BRE 部署公用程式將無法正常運作之前變更過的 BREDeployment.exe.config 檔案中的路徑\<磁碟機\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-243">The BRE Deployment Utility will not work correctly until you change the paths in the BREDeployment.exe.config file located in the \<drive\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools folder.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="ac3ab-244">方案</span><span class="sxs-lookup"><span data-stu-id="ac3ab-244">Solution</span></span>  
 <span data-ttu-id="ac3ab-245">在 [記事本] 中開啟過的 BREDeployment.exe.config，並將變更詞彙目錄、 結構描述，以及基底原則資料夾中更新公用程式的組態。</span><span class="sxs-lookup"><span data-stu-id="ac3ab-245">Update the utility's configuration by opening BREDeployment.exe.config in Notepad, and changing the folders for the base policies, schemas, and vocabulary directories.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac3ab-246">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac3ab-246">See Also</span></span>  
 [<span data-ttu-id="ac3ab-247">疑難排解：問題與解決方式</span><span class="sxs-lookup"><span data-stu-id="ac3ab-247">Troubleshooting: Issues and Resolutions</span></span>](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)