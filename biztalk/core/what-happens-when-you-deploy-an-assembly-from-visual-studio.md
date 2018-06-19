---
title: 當您部署的組件 Visual Studio 時，會發生什麼情況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 421df529-1ddb-4f49-a40a-c06f2a434ffc
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66454d80d702cc6b3ca20708b07fd64cdfcb00d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290166"
---
# <a name="what-happens-when-you-deploy-an-assembly-from-visual-studio"></a><span data-ttu-id="c7c7e-102">當您從 Visual Studio 部署組件時發生哪些狀況</span><span class="sxs-lookup"><span data-stu-id="c7c7e-102">What Happens When You Deploy an Assembly from Visual Studio</span></span>
<span data-ttu-id="c7c7e-103">本主題描述當您從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 將組件部署到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上的 BizTalk 應用程式時，會發生哪些狀況。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-103">This topic describes what happens when you deploy assemblies from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into a BizTalk application on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c7c7e-104">您可以個別部署專案，或是在同時部署方案中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-104">You can deploy a project individually, or you can deploy all of the projects in a solution at the same time.</span></span> <span data-ttu-id="c7c7e-105">部署專案前, 分開或是做為方案一部分您指定要在其中部署組件專案屬性中的應用程式中所述[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-105">Before deploying a project, either separately or as part of a solution, you specify the application into which to deploy its assembly in project properties, as described in [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).</span></span> <span data-ttu-id="c7c7e-106">當您在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中部署專案或方案時，便會自動建置組件，並會將其部署到指定的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-106">When you deploy a project or solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], the assemblies are automatically built and deployed into the specified application.</span></span> <span data-ttu-id="c7c7e-107">如果本機 BizTalk 群組中的現有應用程式與專案屬性中指定的應用程式具有相同名稱，組件就會部署至現有應用程式。否則，便會建立具有指定名稱的新應用程式，而且會將組件部署至其中。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-107">If an existing application in the local BizTalk group has the same name as the application specified in project properties, the assembly is deployed into the existing application; otherwise, a new application having the specified name is created and assembly is deployed into it.</span></span> <span data-ttu-id="c7c7e-108">做為此程序的一部分，組件連同協調流程、管線、結構描述，以及其所包含的對應 (稱為「成品」) 都會匯入到本機 BizTalk 管理資料庫，並會在資料庫中與指定的應用程式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-108">As part of this process, the assembly along with the orchestrations, pipelines, schemas, and maps that it contains (called "artifacts") are imported into the local BizTalk Management database and associated in the database with the specified application.</span></span>  
  
 <span data-ttu-id="c7c7e-109">即使當您同時在方案中部署這些專案時，也可以在方案中將專案部署到相同的 BizTalk 應用程式，或是部署到不同的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-109">You can deploy the projects in a solution into the same BizTalk application or different BizTalk applications, even when you deploy the projects in a solution at the same time.</span></span> <span data-ttu-id="c7c7e-110">下圖說明在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，將 BizTalk 方案所包含的三個組件部署至兩個不同的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-110">The following diagram illustrates deploying three assemblies contained in a BizTalk solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into two different BizTalk applications.</span></span>  
  
 <span data-ttu-id="c7c7e-111">![部署 BizTalk 組件](../core/media/visualstudiodeploy.gif "VisualStudioDeploy")</span><span class="sxs-lookup"><span data-stu-id="c7c7e-111">![Deploy BizTalk assemblies](../core/media/visualstudiodeploy.gif "VisualStudioDeploy")</span></span>  
  
 <span data-ttu-id="c7c7e-112">在部署專案或方案以後，您便能夠從 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 內，或是使用 BTSTask 命令列工具，來檢視和管理組件及其成品。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-112">After you deploy a project or solution, you can view and manage the assemblies and their artifacts from within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or by using the BTSTask command-line tool.</span></span>  
  
## <a name="destination-locations"></a><span data-ttu-id="c7c7e-113">目的地位置</span><span class="sxs-lookup"><span data-stu-id="c7c7e-113">Destination Locations</span></span>  
 <span data-ttu-id="c7c7e-114">從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 部署組件時，組件的目的地位置預設為組件的來源位置。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-114">When deploying assemblies from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], the destination location of an assembly defaults to the source location of the assembly.</span></span> <span data-ttu-id="c7c7e-115">從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 安裝或匯出組件時，如果 "from" 和 "to" 環境並不相同，安裝便會失敗。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-115">When installing or exporting an assembly from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], if the "from" and "to" environment is not the same, the installation will fail.</span></span> <span data-ttu-id="c7c7e-116">例如，如果來源位置是 D:[path]/[filename]，目標電腦的安裝電腦卻沒有 "D" 磁碟機，安裝便會失敗。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-116">For example, if the source location is D:[path]/[filename] and the target machine installation machine does not have a "D" drive, the installation will fail.</span></span>  
  
 <span data-ttu-id="c7c7e-117">這項行為與使用 [BizTalk 系統管理員] 新增資源形成對比。在該種情況下，預設的目的地位置是 %BTAD_InstallDir%。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-117">This behavior is in contrast to adding a resource using BizTalk Administrator, in which case, the default destination location is %BTAD_InstallDir%.</span></span> <span data-ttu-id="c7c7e-118">此環境變數會展開為安裝期間所指定的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-118">This environment variable expands to the install directory specified during installation.</span></span>  
  
 <span data-ttu-id="c7c7e-119">若要因應這個問題，請使用下列程序：</span><span class="sxs-lookup"><span data-stu-id="c7c7e-119">To work around this issue, use the following procedure:</span></span>  
  
1.  <span data-ttu-id="c7c7e-120">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中部署組件。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-120">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], deploy the assembly.</span></span>  
  
2.  <span data-ttu-id="c7c7e-121">在部署組件以後，開啟 [BizTalk 系統管理員]。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-121">After the assembly is deployed, open BizTalk Administrator.</span></span>  
  
3.  <span data-ttu-id="c7c7e-122">適當地修改目的地位置。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-122">Modify the destination location as appropriate.</span></span> <span data-ttu-id="c7c7e-123">例如，將目的地位置變更為 %BTAD_InstallDir%。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-123">For example, change the destination location to %BTAD_InstallDir%.</span></span>  
  
 <span data-ttu-id="c7c7e-124">一旦修改過目的地位置後，這個新位置便會被用來做為相同組件之後續重新部署的預設值。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-124">Once you modify the destination location, this new location will be used as default for subsequent redeploys of the same assembly.</span></span>  
  
 <span data-ttu-id="c7c7e-125">如需詳細資訊，請參閱[如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-125">For more information, see [How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).</span></span>  
  
## <a name="deploying-solutions-vs-projects"></a><span data-ttu-id="c7c7e-126">部署方案 vs。專案</span><span class="sxs-lookup"><span data-stu-id="c7c7e-126">Deploying Solutions vs. Projects</span></span>  
 <span data-ttu-id="c7c7e-127">我們強烈建議您永遠部署方案而非個別的專案。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-127">We strongly recommend that you always deploy a solution rather than an individual project.</span></span> <span data-ttu-id="c7c7e-128">當您在部署個別的專案，而且在您所部署的某個組件與另一個組件之間有相依性時，您就必須採取數個手動步驟來完成部署。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-128">When you deploy an individual project and there are dependencies between an assembly you are deploying and another assembly, you must take a number of manual steps to complete the deployment.</span></span> <span data-ttu-id="c7c7e-129">然而，當您部署方案時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會自動採取管理組件之間相依性的所有必要步驟。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-129">When you deploy a solution, however, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically take all of the steps to manage dependencies between assemblies.</span></span> <span data-ttu-id="c7c7e-130">如需詳細資訊，請參閱[如何重新部署 BizTalk 組件從 Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-130">For more information, see [How to Redeploy a BizTalk Assembly from Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md).</span></span>  
  
 <span data-ttu-id="c7c7e-131">下圖說明當您部署方案時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 用來重新部署具有相依性之組件的步驟。</span><span class="sxs-lookup"><span data-stu-id="c7c7e-131">The following diagram illustrates the steps that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] takes to redeploy assemblies that have dependencies when you deploy a solution.</span></span>  
  
 <span data-ttu-id="c7c7e-132">![部署方案中的組件](../core/media/deployassemblies.gif "DeployAssemblies")</span><span class="sxs-lookup"><span data-stu-id="c7c7e-132">![Deploying assemblies in a solution](../core/media/deployassemblies.gif "DeployAssemblies")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c7e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7c7e-133">See Also</span></span>  
 [<span data-ttu-id="c7c7e-134">部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="c7c7e-134">Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application</span></span>](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)