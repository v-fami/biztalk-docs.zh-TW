---
title: 如何在 GAC 中安裝組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6afc2f81-fa28-4144-b4bd-21c8f35f2270
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52e843d74b5420f8973f9d3663cfd05210c26996
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752363"
---
# <a name="how-to-install-an-assembly-in-the-gac"></a><span data-ttu-id="4a723-102">如何在 GAC 中安裝組件</span><span class="sxs-lookup"><span data-stu-id="4a723-102">How to Install an Assembly in the GAC</span></span>
<span data-ttu-id="4a723-103">手動安裝和解除安裝 BizTalk 組件在全域組件快取 (GAC) 使用隨附的 Gacutil 工具[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4a723-103">Manually install and uninstall a BizTalk assembly in the global assembly cache (GAC) using the Gacutil tool included with [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
 <span data-ttu-id="4a723-104">使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您可以從部署時，自動安裝在 GAC 中的 BizTalk 組件[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4a723-104">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], you can have BizTalk assemblies automatically installed in the GAC when they are deployed from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="4a723-105">將此選項設定中部署 BizTalk 專案屬性;請參閱[如何在 Visual Studio 中的 設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="4a723-105">Set this option in the Deployment Properties of the BizTalk project; see [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).</span></span> <span data-ttu-id="4a723-106">您不能用於非 BizTalk.NET 組件安裝在 GAC 中; 這個方法您必須以手動方式，本主題中所述安裝它們。</span><span class="sxs-lookup"><span data-stu-id="4a723-106">You cannot, use this method to install non-BizTalk .NET assemblies in the GAC; you must install them manually, as described in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a723-107">組件已部署到 BizTalk 應用程式之後，您也可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，指定這些組件的部署選項。</span><span class="sxs-lookup"><span data-stu-id="4a723-107">You can also specify deployment options for assemblies after they are deployed into a BizTalk application by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="4a723-108">請參閱[如何修改 BizTalk 組件的部署選項](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md)，並[如何修改.NET 組件、 COM 元件、 檔案或 BAM 成品的部署選項](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md)。</span><span class="sxs-lookup"><span data-stu-id="4a723-108">See [How to Modify the Deployment Options of a BizTalk Assembly](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md), and [How to Modify the Deployment Options of a .NET Assembly, COM Component, File, or BAM Artifact](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4a723-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="4a723-109">Prerequisites</span></span>  
<span data-ttu-id="4a723-110">使用具有 GAC 「 寫入 」 權限的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="4a723-110">Sign in with an account that has Write permission to the GAC.</span></span> <span data-ttu-id="4a723-111">本機電腦上的「系統管理員」帳戶具有這項權限。</span><span class="sxs-lookup"><span data-stu-id="4a723-111">The Administrators account on the local computer has this permission.</span></span>  

  
## <a name="install-using-gacutil"></a><span data-ttu-id="4a723-112">使用 gacutil 安裝</span><span class="sxs-lookup"><span data-stu-id="4a723-112">Install using gacutil</span></span>
  
1.  <span data-ttu-id="4a723-113">將 BizTalk 組件複製到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="4a723-113">Copy the BizTalk assembly to your local computer.</span></span>  
  
2.  <span data-ttu-id="4a723-114">開啟**Visual Studio 的開發人員命令提示字元**以系統管理員身分。</span><span class="sxs-lookup"><span data-stu-id="4a723-114">Open **Developer Command Prompt for Visual Studio** as administrator.</span></span>  
  
3.  <span data-ttu-id="4a723-115">輸入以下內容：</span><span class="sxs-lookup"><span data-stu-id="4a723-115">Type the following:</span></span>  
  
     `gacutil /i path_to_assembly_file /f`

    <span data-ttu-id="4a723-116">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="4a723-116">For example, type:</span></span>  
    `gacutil /i c:\temp\filename.dll /f`
    
<span data-ttu-id="4a723-117">`/f`選項會覆寫任何現有的組件具有相同的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="4a723-117">The `/f` option overwrites any existing assembly that has the same assembly name.</span></span> <span data-ttu-id="4a723-118">如需的 gacutil 命令和選項的詳細資訊，請輸入`gacutil /?`。</span><span class="sxs-lookup"><span data-stu-id="4a723-118">For more info on the gacutil commands and options, type `gacutil /?`.</span></span> 

## <a name="uninstall-using-gacutil"></a><span data-ttu-id="4a723-119">使用 gacutil 解除安裝</span><span class="sxs-lookup"><span data-stu-id="4a723-119">Uninstall using gacutil</span></span>
<span data-ttu-id="4a723-120">解除安裝組件，從全域組件快取 (GAC) 就必須完全解除部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a723-120">Uninstalling an assembly from the global assembly cache (GAC) is necessary to completely undeploy an application.</span></span> <span data-ttu-id="4a723-121">您可以自動化此程序。</span><span class="sxs-lookup"><span data-stu-id="4a723-121">You can automate this process.</span></span> <span data-ttu-id="4a723-122">部署到生產環境應用程式，撰寫自動解除安裝組件從 GAC 解除安裝應用程式時的前置處理指令碼。</span><span class="sxs-lookup"><span data-stu-id="4a723-122">Before deploying the application into a production environment, write a pre-processing script that uninstalls the assembly from the GAC automatically when the application is uninstalled.</span></span> <span data-ttu-id="4a723-123">請參閱[使用前置和後置處理指令碼自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="4a723-123">See [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span></span>  
  
 <span data-ttu-id="4a723-124">您也可以使用指令碼來移除其他檔案和設定。</span><span class="sxs-lookup"><span data-stu-id="4a723-124">You can also use a script to remove additional files and settings.</span></span> <span data-ttu-id="4a723-125">請參閱[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4a723-125">See [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).</span></span>  
 
#### <a name="using-the-windows-interface"></a><span data-ttu-id="4a723-126">使用 Windows 介面</span><span class="sxs-lookup"><span data-stu-id="4a723-126">Using the Windows interface</span></span>  
  
1.  <span data-ttu-id="4a723-127">開啟至 systemdrive%\Windows\Assembly。</span><span class="sxs-lookup"><span data-stu-id="4a723-127">Open to %systemdrive%\Windows\Assembly.</span></span>  
  
2.  <span data-ttu-id="4a723-128">以滑鼠右鍵按一下包含您的應用程式，選取在每個組件檔案**解除安裝**，然後選取**是**確認。</span><span class="sxs-lookup"><span data-stu-id="4a723-128">Right-click each assembly file included in your application, select **Uninstall**, and then select **Yes** to confirm.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="4a723-129">使用命令列</span><span class="sxs-lookup"><span data-stu-id="4a723-129">Using the command line</span></span>  
  
1.  <span data-ttu-id="4a723-130">開啟**Visual Studio 的開發人員命令提示字元**以系統管理員身分。</span><span class="sxs-lookup"><span data-stu-id="4a723-130">Open **Developer Command Prompt for Visual Studio** as administrator.</span></span> 
  
2.  <span data-ttu-id="4a723-131">輸入以下內容：</span><span class="sxs-lookup"><span data-stu-id="4a723-131">Type the following:</span></span>  
  
     <span data-ttu-id="4a723-132">`gacutil /u` \<*完整的組件名稱*\></span><span class="sxs-lookup"><span data-stu-id="4a723-132">`gacutil /u` \<*fully qualified assembly name*\></span></span>  
  
     <span data-ttu-id="4a723-133">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="4a723-133">For example, type:</span></span>  
     `gacutil /u "hello,Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"`
       
## <a name="see-also"></a><span data-ttu-id="4a723-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a723-134">See Also</span></span>  
 [<span data-ttu-id="4a723-135">從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="4a723-135">Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application</span></span>](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)  
<span data-ttu-id="4a723-136">[解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="4a723-136">[Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md) </span></span>  
 <span data-ttu-id="4a723-137">[如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="4a723-137">[How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="4a723-138">如何從 BizTalk 群組刪除 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="4a723-138">How to Delete a BizTalk Application from the BizTalk Group</span></span>](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)
 
