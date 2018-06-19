---
title: 如何解除安裝 BizTalk 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], uninstalling
- applications, uninstalling
- uninstalling, applications
- undeploying, uninstalling
ms.assetid: ab721c6e-194e-4b8a-bfd1-d0139d284373
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cba0c5f4ea8340612bb42c4a15257acd449848d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256838"
---
# <a name="how-to-uninstall-a-biztalk-application"></a><span data-ttu-id="3909f-102">如何解除安裝 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="3909f-102">How to Uninstall a BizTalk Application</span></span>
<span data-ttu-id="3909f-103">本主題描述如何使用 [新增或移除程式] 控制台或 BTSTask 命令列工具來解除安裝 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3909f-103">This topic describes how to use the Add or Remove Programs control panel or the BTSTask command-line tool to uninstall a BizTalk application.</span></span> <span data-ttu-id="3909f-104">只支援使用這兩個方法解除安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="3909f-104">These are the only supported methods for uninstalling an application.</span></span> <span data-ttu-id="3909f-105">如果您為這個應用程式安裝了多個 .msi 檔案 (例如，為了更新此應用程式)，則按兩下 .msi 檔案或使用 msiexec 可能不會完全解除安裝此應用程式，因此，這些是不支援的解除安裝方法。</span><span class="sxs-lookup"><span data-stu-id="3909f-105">If you installed multiple .msi files for this application, for example to update the application, double-clicking the .msi file or using msiexec may not completely uninstall the application and are therefore not supported uninstallation methods.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3909f-106">當 BizTalk 應用程式正在執行時將它解除安裝，可能會在此應用程式中產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3909f-106">Uninstalling a BizTalk application while it is running can cause errors in the application.</span></span> <span data-ttu-id="3909f-107">若要避免這個問題，最佳作法是，我們建議您確認有都沒有執行服務應用程式的執行個體中所述[如何搜尋所有服務執行個體](../core/how-to-search-for-all-service-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="3909f-107">In order to avoid this problem, as a best practice we recommend that you verify there are no running service instances for the application, as described in [How to Search for All Service Instances](../core/how-to-search-for-all-service-instances.md).</span></span> <span data-ttu-id="3909f-108">如果有必要，您可以停止應用程式使用完全停止 選項來完全停止所有執行的執行個體，如下所示[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3909f-108">If necessary, you can stop the application by using the Full Stop option to completely stop all running instances, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span> <span data-ttu-id="3909f-109">請注意，當您這樣做時，內含式訊息將不會完成。</span><span class="sxs-lookup"><span data-stu-id="3909f-109">Be aware that when you do this, in-process messages will not complete.</span></span>  
  
 <span data-ttu-id="3909f-110">前置或後置處理指令碼應該包含在應用程式的 .msi 檔案中，解除安裝應用程式時，才會移除與它相關的所有檔案和設定。</span><span class="sxs-lookup"><span data-stu-id="3909f-110">A pre- or post-processing script should be included in the application .msi file to remove all of the files and settings associated with the application when it is uninstalled.</span></span> <span data-ttu-id="3909f-111">如果未包含前置或後置處理指令碼，本主題中的程序將會從本機檔案系統移除應用程式的檔案和設定，但下列幾個情況例外。</span><span class="sxs-lookup"><span data-stu-id="3909f-111">If a pre- or post-processing script has not been included, the procedures in this topic will remove the application's files and settings from the local file system, with the following exceptions.</span></span>  
  
-   <span data-ttu-id="3909f-112">如果應用程式包含虛擬目錄，將會刪除該虛擬目錄和它的檔案，除非在安裝應用程式後已在虛擬目錄中加入檔案。</span><span class="sxs-lookup"><span data-stu-id="3909f-112">If the application includes a virtual directory, the virtual directory and its files are deleted, unless files were added to the virtual directory after the application was installed.</span></span> <span data-ttu-id="3909f-113">在此情況下，將不會刪除該虛擬目錄和加入的檔案。</span><span class="sxs-lookup"><span data-stu-id="3909f-113">In this case, the virtual directory and the added files are not deleted.</span></span> <span data-ttu-id="3909f-114">如果您想要刪除此虛擬目錄和加入的檔案，您必須明確加以刪除。</span><span class="sxs-lookup"><span data-stu-id="3909f-114">If you want to delete the virtual directory and the added files, you must do so explicitly.</span></span>  
  
-   <span data-ttu-id="3909f-115">會刪除前置和後置處理指令碼，但是不會刪除這些指令碼在安裝或解除安裝期間加入的任何檔案，也不會復原這些指令碼所採取的任何動作。</span><span class="sxs-lookup"><span data-stu-id="3909f-115">Pre- and post-processing scripts are deleted, but any files added by the scripts during installation or uninstallation are not deleted, nor are any actions taken by the scripts undone.</span></span> <span data-ttu-id="3909f-116">如果您想要刪除指令碼加入的檔案或復原其動作，您必須明確加以刪除或復原。</span><span class="sxs-lookup"><span data-stu-id="3909f-116">If you want to delete files added by scripts or undo their actions, you must do so explicitly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3909f-117">在解除安裝期間，只有在匯入應用程式時，已在部署屬性中指定目的地位置的前置或後置處理指令碼才會執行。</span><span class="sxs-lookup"><span data-stu-id="3909f-117">Only pre-or post-processing scripts that have a destination location specified in its deployment properties when the application is imported will run during uninstallation.</span></span> <span data-ttu-id="3909f-118">如需詳細資訊，請參閱[如何新增前置或後置處理指令碼至應用程式](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3909f-118">For more information, see [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).</span></span>  
  
-   <span data-ttu-id="3909f-119">當您解除安裝 BizTalk 應用程式時，絕對不會刪除憑證。</span><span class="sxs-lookup"><span data-stu-id="3909f-119">Certificates are never deleted when you uninstall a BizTalk application.</span></span> <span data-ttu-id="3909f-120">如果您想要刪除憑證，您必須明確加以刪除。</span><span class="sxs-lookup"><span data-stu-id="3909f-120">If you want to delete a certificate, you must do so explicitly.</span></span> <span data-ttu-id="3909f-121">此外，不會從 Windows 登錄中移除元件，也不會從全域組件快取 (GAC) 中移除 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="3909f-121">In addition, components are not removed from the Windows Registry and BizTalk assemblies are not removed from the global assembly cache (GAC).</span></span> <span data-ttu-id="3909f-122">如果您想要移除它們，您必須明確加以移除。</span><span class="sxs-lookup"><span data-stu-id="3909f-122">If you want to remove them, you must do so explicitly.</span></span> <span data-ttu-id="3909f-123">如需詳細資訊，請參閱[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3909f-123">For more information, see [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).</span></span>  
  
 <span data-ttu-id="3909f-124">如果您在解除安裝作業完成之前將其取消，BizTalk Server 會回復解除安裝，但在作業取消之前由前置或後置處理指令碼所執行的任何動作除外。</span><span class="sxs-lookup"><span data-stu-id="3909f-124">If you cancel the uninstallation operation before it completes, BizTalk Server will roll back the uninstallation, except for any actions that were taken by pre- or post-processing scripts before the operation was canceled.</span></span> <span data-ttu-id="3909f-125">若要將應用程式還原成解除安裝開始之前的狀態，請按兩下 .msi 檔案，然後重新安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="3909f-125">To restore the application to its state before you started the uninstallation, double-click the .msi file and reinstall the application.</span></span> <span data-ttu-id="3909f-126">如果您已經為這個應用程式安裝了多個 .msi 檔案，您應該在每一個 .msi 檔案上按兩下 (依據這些 .msi 檔案原本安裝的順序) 來重新安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="3909f-126">If multiple .msi files have been installed for this application, you should double-click each .msi file to reinstall the application in the order in which the .msi files were originally installed.</span></span>  
  
 <span data-ttu-id="3909f-127">如需後置處理指令碼的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="3909f-127">For more information about post-processing scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3909f-128">若要完全解除部署 BizTalk 應用程式，您也必須刪除它從 [BizTalk 群組] 中所述[如何從 BizTalk 群組刪除 BizTalk 應用程式](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)。</span><span class="sxs-lookup"><span data-stu-id="3909f-128">To completely undeploy a BizTalk application, you must also delete it from the BizTalk group, as described in [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3909f-129">必要條件</span><span class="sxs-lookup"><span data-stu-id="3909f-129">Prerequisites</span></span>  
 <span data-ttu-id="3909f-130">若要執行本主題的程序，您必須以適當的使用權限登入。</span><span class="sxs-lookup"><span data-stu-id="3909f-130">To perform the procedures in this topic, you must be logged on with appropriate permissions.</span></span> <span data-ttu-id="3909f-131">如需詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3909f-131">For more information, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-uninstall-a-biztalk-application"></a><span data-ttu-id="3909f-132">若要解除安裝 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="3909f-132">To uninstall a BizTalk application</span></span>  
  
#### <a name="using-uninstall-or-change-a-program"></a><span data-ttu-id="3909f-133">使用解除安裝或變更程式</span><span class="sxs-lookup"><span data-stu-id="3909f-133">Using Uninstall or change a program</span></span>  
  
1.  <span data-ttu-id="3909f-134">在電腦上執行應用程式，按一下 **啟動**，按一下**控制台**，然後按兩下**程式和功能**。</span><span class="sxs-lookup"><span data-stu-id="3909f-134">On the computer running the application, click **Start**, click **Control Panel**, and then double-click  **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="3909f-135">在**解除安裝或變更程式**頁面上，以滑鼠右鍵按一下 BizTalk 應用程式，以移除，然後按一下**解除安裝**。</span><span class="sxs-lookup"><span data-stu-id="3909f-135">On **Uninstall or change a program** page, right-click the BizTalk application to remove, and then click **Uninstall**.</span></span>  
  
     <span data-ttu-id="3909f-136">Windows Installer 就會移除指定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3909f-136">Windows Installer removes the specified application.</span></span>  
  
3.  <span data-ttu-id="3909f-137">如果此應用程式在多部電腦上執行，請在每一部電腦上重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="3909f-137">If the application is running on multiple computers, repeat these steps on each computer.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="3909f-138">使用命令列</span><span class="sxs-lookup"><span data-stu-id="3909f-138">Using the command line</span></span>  
  
1.  <span data-ttu-id="3909f-139">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="3909f-139">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="3909f-140">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="3909f-140">Type the following command, substituting the appropriate value, as described in the following table:</span></span>  
  
     <span data-ttu-id="3909f-141">**BTSTask UninstallApp** [**/ApplicationName:***值*]</span><span class="sxs-lookup"><span data-stu-id="3909f-141">**BTSTask UninstallApp** [**/ApplicationName:***value*]</span></span>  
  
     <span data-ttu-id="3909f-142">範例：</span><span class="sxs-lookup"><span data-stu-id="3909f-142">Example:</span></span>  
  
     <span data-ttu-id="3909f-143">**BTSTask UninstallApp /applicationname: myapplication**</span><span class="sxs-lookup"><span data-stu-id="3909f-143">**BTSTask UninstallApp /ApplicationName:MyApplication**</span></span>  
  
    |<span data-ttu-id="3909f-144">參數</span><span class="sxs-lookup"><span data-stu-id="3909f-144">Parameter</span></span>|<span data-ttu-id="3909f-145">值</span><span class="sxs-lookup"><span data-stu-id="3909f-145">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="3909f-146">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="3909f-146">**/ApplicationName**</span></span>|<span data-ttu-id="3909f-147">要解除安裝的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="3909f-147">Name of the BizTalk application to uninstall.</span></span> <span data-ttu-id="3909f-148">如果名稱包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="3909f-148">If the name includes spaces, you must enclose it in double quotation marks (").</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3909f-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3909f-149">See Also</span></span>  
 <span data-ttu-id="3909f-150">[解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="3909f-150">[Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="3909f-151">UninstallApp 命令</span><span class="sxs-lookup"><span data-stu-id="3909f-151">UninstallApp Command</span></span>](../core/uninstallapp-command.md)