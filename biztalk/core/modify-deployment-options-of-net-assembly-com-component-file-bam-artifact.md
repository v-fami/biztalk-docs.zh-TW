---
title: 如何修改.NET 組件、 COM 元件、 檔案或 BAM 成品的部署選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [.NET assemblies], deploying
- deploying, virtual directories
- managing [applications], deploying
- managing [applications], modifying
- definition files [BAM], modifying
- modifying, artifacts
- deploying, artifacts
- managing [certificates], deploying
- deploying, .NET assemblies
- COM components, deploying
- definition files [BAM], deploying
- virtual directories, deploying
- deploying, certificates
- modifying, deployment options
- virtual directories, modifying
- deploying, COM components
ms.assetid: 4955d420-d9ff-4d5a-82f4-fb16477a828c
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 641e955a5eed0bb18df90b170daa6b87feba0876
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992007"
---
# <a name="how-to-modify-the-deployment-options-of-a-net-assembly-com-component-file-or-bam-artifact"></a><span data-ttu-id="e7c68-102">如何修改 .NET 組件、COM 組件、檔案或 BAM 成品的部署選項</span><span class="sxs-lookup"><span data-stu-id="e7c68-102">How to Modify the Deployment Options of a .NET Assembly, COM Component, File, or BAM Artifact</span></span>
<span data-ttu-id="e7c68-103">本主題描述如何使用 [BizTalk Server 管理主控台] 來修改下列資源成品的部署選項：</span><span class="sxs-lookup"><span data-stu-id="e7c68-103">This topic describes how to use the BizTalk Server Administration console to modify the deployment options of the following resource artifacts:</span></span>  
  
- <span data-ttu-id="e7c68-104">.NET 組件</span><span class="sxs-lookup"><span data-stu-id="e7c68-104">.NET assemblies</span></span>  
  
- <span data-ttu-id="e7c68-105">COM 元件</span><span class="sxs-lookup"><span data-stu-id="e7c68-105">COM components</span></span>  
  
- <span data-ttu-id="e7c68-106">臨機操作檔案</span><span class="sxs-lookup"><span data-stu-id="e7c68-106">Ad hoc files</span></span>  
  
- <span data-ttu-id="e7c68-107">BAM 成品</span><span class="sxs-lookup"><span data-stu-id="e7c68-107">BAM artifacts</span></span>  
  
  <span data-ttu-id="e7c68-108">您可能要修改部署屬性，將目的地位置變更為當應用程式在本機電腦上安裝時，便會將成品檔案複製到其中的位置。</span><span class="sxs-lookup"><span data-stu-id="e7c68-108">You might want to modify the deployment properties to change the destination location to which the artifact file will be copied when the application is installed on the local computer.</span></span> <span data-ttu-id="e7c68-109">如果沒有提供路徑，在安裝時就不會將檔案複製到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="e7c68-109">If you do not provide a path, the file will not be copied to the local computer on installation.</span></span>  
  
  <span data-ttu-id="e7c68-110">此外，您可能要修改 .NET 組件的下列選項：</span><span class="sxs-lookup"><span data-stu-id="e7c68-110">In addition, you might want to modify the following options for a .NET assembly:</span></span>  
  
- <span data-ttu-id="e7c68-111">**新增至全域組件快取新增資源 (gacutil) 上。**</span><span class="sxs-lookup"><span data-stu-id="e7c68-111">**Add to the global assembly cache on add resource (gacutil).**</span></span> <span data-ttu-id="e7c68-112">如果選取此選項，將組件新增至應用程式時，便會將組件新增至本機電腦上的全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="e7c68-112">When you select this option, the assembly is added to the global assembly cache (GAC) on the local computer when the assembly is added to the application.</span></span> <span data-ttu-id="e7c68-113">此外，如果您稍後重新整理之組件 (以滑鼠右鍵按一下它，然後按一下 **重新整理**)，組件加入至 GAC。</span><span class="sxs-lookup"><span data-stu-id="e7c68-113">In addition, if you later refresh the assembly (right-click it and click **Refresh**), the assembly is added to the GAC.</span></span> <span data-ttu-id="e7c68-114">清除這個選項的核取方塊並不會從 GAC 移除該組件 (如果該組件目前在 GAC 中)。</span><span class="sxs-lookup"><span data-stu-id="e7c68-114">Clearing the check box for this option does not remove the assembly from the GAC, if it currently exists there.</span></span>  
  
- <span data-ttu-id="e7c68-115">**新增至 MSI 檔案匯入 (gacutil) 的全域組件快取。**</span><span class="sxs-lookup"><span data-stu-id="e7c68-115">**Add to the global assembly cache on MSI file import (gacutil).**</span></span> <span data-ttu-id="e7c68-116">選取此選項時，如果應用程式是匯出至 .msi 檔案，而 .msi 檔案又會匯出至 BizTalk 群組中，則匯出程序會將組件安裝在本機電腦上的 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="e7c68-116">When you select this option, if the application is exported to an .msi file, and the .msi file is imported into a BizTalk group, the assembly is installed in the GAC on the local computer as part of the import process.</span></span>  
  
- <span data-ttu-id="e7c68-117">**新增至 MSI 檔案安裝 (gacutil) 的全域組件快取。**</span><span class="sxs-lookup"><span data-stu-id="e7c68-117">**Add to the global assembly cache on MSI file install (gacutil).**</span></span> <span data-ttu-id="e7c68-118">選取此選項時，如果應用程式是匯出至 .msi 檔案，再由 .msi 檔案將應用程式安裝在電腦上，則安裝程序會將組件安裝在本機電腦上的 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="e7c68-118">When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, the assembly is installed in the GAC on the local computer as part of the installation process.</span></span>  
  
- <span data-ttu-id="e7c68-119">**讓 COM 元件看見 (regasm)。**</span><span class="sxs-lookup"><span data-stu-id="e7c68-119">**Make visible to COM components (regasm).**</span></span> <span data-ttu-id="e7c68-120">選取此選項時，如果應用程式是匯出至 .msi 檔案，而且應用程式是從 .msi 檔案安裝到電腦中，便會做為安裝程序的一部分，而將 Managed COM 組件新增至本機電腦中的 Windows 登錄中。</span><span class="sxs-lookup"><span data-stu-id="e7c68-120">When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, a managed COM assembly is added to the Windows registry on the local computer as part of the installation process.</span></span> <span data-ttu-id="e7c68-121">如果您指定這個選項，也就必須在 [目的] 中指定檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="e7c68-121">If you specify this option, you must also specify a location for the file in Destination.</span></span>  
  
- <span data-ttu-id="e7c68-122">**註冊已服務元件 (regsvcs)。**</span><span class="sxs-lookup"><span data-stu-id="e7c68-122">**Register serviced components (regsvcs).**</span></span> <span data-ttu-id="e7c68-123">當您選取此選項時，如果應用程式匯出至.msi 檔案，並從.msi 檔案的電腦上安裝應用程式時，受管理的 COM + 組件新增至 Windows 登錄在本機電腦安裝程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="e7c68-123">When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, a managed COM+ assembly is added to the Windows registry on the local computer as part of the installation process.</span></span> <span data-ttu-id="e7c68-124">如果您指定這個選項，也就必須在 [目的] 中指定檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="e7c68-124">If you specify this option, you must also specify a location for the file in Destination.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e7c68-125">必要條件</span><span class="sxs-lookup"><span data-stu-id="e7c68-125">Prerequisites</span></span>  
 <span data-ttu-id="e7c68-126">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="e7c68-126">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="e7c68-127">此外，如果您選取立即將組件新增至 GAC 的選項，您的帳戶也必須是本機「系統管理員」群組的成員。</span><span class="sxs-lookup"><span data-stu-id="e7c68-127">In addition, if you select an option that immediately adds the assembly to the GAC, your account must also be a member of the local Administrator's group.</span></span> <span data-ttu-id="e7c68-128">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e7c68-128">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-modify-the-deployment-properties-of-a-resource-artifact"></a><span data-ttu-id="e7c68-129">若要修改資源成品的部署屬性</span><span class="sxs-lookup"><span data-stu-id="e7c68-129">To modify the deployment properties of a resource artifact</span></span>  
  
1. <span data-ttu-id="e7c68-130">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e7c68-130">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="e7c68-131">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開包含要為其修改部署選項之成品的 BizTalk 群組，然後再展開包含該成品的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7c68-131">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the artifact for which to modify deployment options, and then expand the application containing the artifact.</span></span>  
  
3. <span data-ttu-id="e7c68-132">按一下 **資源**資料夾中，以滑鼠右鍵按一下成品，然後**修改**。</span><span class="sxs-lookup"><span data-stu-id="e7c68-132">Click the **Resources** folder, right-click the artifact, and then click **Modify**.</span></span>  
  
4. <span data-ttu-id="e7c68-133">在 **選項**索引標籤上，視情況下，需要修改部署選項，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e7c68-133">On the **Options** tab, modify the deployment options as necessary, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c68-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7c68-134">See Also</span></span>  
 [<span data-ttu-id="e7c68-135">管理 .NET 組件、憑證和其他資源</span><span class="sxs-lookup"><span data-stu-id="e7c68-135">Managing .NET Assemblies, Certificates, and Other Resources</span></span>](../core/managing-net-assemblies-certificates-and-other-resources.md)