---
title: 部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: accef4b8-acdf-4043-8fd7-2db9ea752074
caps.latest.revision: 36
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4dcacede998ec0c921a379841e9b31389f2aa20
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007183"
---
# <a name="deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application"></a><span data-ttu-id="7b296-102">從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="7b296-102">Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application</span></span>
<span data-ttu-id="7b296-103">部署和重新部署 BizTalk 組件從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]至 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b296-103">Deploy and redeploy BizTalk assemblies from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into a BizTalk application.</span></span> <span data-ttu-id="7b296-104">這樣做的目的，可能是為了測試您所開發之組件的功能，並封裝這些組件來遞交。</span><span class="sxs-lookup"><span data-stu-id="7b296-104">You may want to do this to test the functionality of the assemblies that you have been developing and package them for handoff.</span></span>  

## <a name="overview"></a><span data-ttu-id="7b296-105">概觀</span><span class="sxs-lookup"><span data-stu-id="7b296-105">Overview</span></span>  
 <span data-ttu-id="7b296-106">BizTalk 應用程式提供檢視和管理項目，稱為 「 成品 」 組成 BizTalk 商務方案的方式。</span><span class="sxs-lookup"><span data-stu-id="7b296-106">BizTalk applications provide a way to view and manage the items, called "artifacts," that comprise a BizTalk business solution.</span></span> <span data-ttu-id="7b296-107">成品包括 BizTalk 組件 （包含協調流程、 結構描述、 對應和管線），您可以部署到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7b296-107">Artifacts include BizTalk assemblies (containing orchestrations, schemas, maps, and pipelines), which you can deploy into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="7b296-108">成品也包含一些項目，例如.NET 組件、 憑證、 指令碼、 讀我檔案和原則，您將新增至 BizTalk 應用程式使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台或 BTSTask 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="7b296-108">Artifacts also include items such as .NET assemblies, certificates, scripts, Readme files, and policies, which you add to your BizTalk application by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or the BTSTask command-line tool.</span></span> <span data-ttu-id="7b296-109">然後，解決方案開發人員或 IT 管理員可以將應用程式和它的成品當做單一實體來檢視、封裝、部署和管理。</span><span class="sxs-lookup"><span data-stu-id="7b296-109">The solution developer or IT administrator can then view, package, deploy, and manage the application and its artifacts as a single entity.</span></span> <span data-ttu-id="7b296-110">如需有關如何建立的詳細資訊，請部署和管理 BizTalk 應用程式，請參閱[Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="7b296-110">For more information about creating, deploying, and managing BizTalk applications, see [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md).</span></span>  
  
 <span data-ttu-id="7b296-111">您可以建置並部署 BizTalk 組件之前，您必須建立的專案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]並建立或新增您想要包含在組件中的項目。</span><span class="sxs-lookup"><span data-stu-id="7b296-111">Before you can build and deploy a BizTalk assembly, you must create a project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and either create or add the items that you want to include in the assembly.</span></span> <span data-ttu-id="7b296-112">您可以建立的方案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]來包含多個專案，然後建置並部署到不同的應用程式的相同應用程式，全部一次其組件。</span><span class="sxs-lookup"><span data-stu-id="7b296-112">You can create a solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to contain multiple projects and then build and deploy their assemblies all at once into the same application or different applications.</span></span> <span data-ttu-id="7b296-113">如需執行這些工作的指示，請參閱[如何建立 BizTalk 專案](../core/how-to-create-biztalk-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="7b296-113">For instructions on performing these tasks, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span>  
  
 <span data-ttu-id="7b296-114">當完成這些工作之後，您可以採取下列步驟來建置、部署及解除部署 BizTalk 組件，如本章節的各個主題所述：</span><span class="sxs-lookup"><span data-stu-id="7b296-114">After completing these tasks, you can build, deploy, and undeploy the BizTalk assemblies by taking the following steps, as described in the topics in this section:</span></span>  
  
- <span data-ttu-id="7b296-115">每個設定強式名稱組件金鑰檔案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="7b296-115">Configure a strong name assembly key file for each [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project.</span></span>  
  
- <span data-ttu-id="7b296-116">為專案設定部署屬性，包括設定 [重新部署] 選項，以便輕鬆地重新部署組件。</span><span class="sxs-lookup"><span data-stu-id="7b296-116">Set deployment properties for the project, including configuring the Redeploy option to easily redeploy the assembly.</span></span>  
  
- <span data-ttu-id="7b296-117">使用中的 [部署] 命令[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]建置方案所包含的 BizTalk 組件，並將其部署到 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b296-117">Use the Deploy command in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to build the BizTalk assemblies contained in a solution and deploy them into a BizTalk application.</span></span> <span data-ttu-id="7b296-118">另外，您也可以使用 [部署] 命令將組件建置及部署到單一專案中，但是我們不建議您這樣做。</span><span class="sxs-lookup"><span data-stu-id="7b296-118">Alternatively, you can use the Deploy command to build and deploy an assembly in a single project, although we do not recommend doing this.</span></span>  
  
- <span data-ttu-id="7b296-119">測試應用程式，並進行必要的變更之後, 使用中的 [部署] 命令[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]重建並重新部署組件。</span><span class="sxs-lookup"><span data-stu-id="7b296-119">After testing the application and making necessary changes, use the Deploy command in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to rebuild and redeploy the assembly.</span></span>  
  
- <span data-ttu-id="7b296-120">必要時，將該組件安裝到全域組件快取 (GAC) 中，或是從 GAC 中移除該組件。</span><span class="sxs-lookup"><span data-stu-id="7b296-120">Install the assembly in the global assembly cache (GAC), if necessary, or remove the assembly from the GAC.</span></span>  
  
- <span data-ttu-id="7b296-121">解除部署組件。</span><span class="sxs-lookup"><span data-stu-id="7b296-121">Undeploy the assembly.</span></span>  
  
  <span data-ttu-id="7b296-122">將一或多個組件部署到 BizTalk 應用程式之後，您可以完成應用程式的組態，並將它部署到測試及實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="7b296-122">After deploying one or more assemblies into a BizTalk application, you can complete the configuration of the application and deploy it into a test and then production environment.</span></span> <span data-ttu-id="7b296-123">如需詳細資訊，請參閱 < [BizTalk 應用程式部署的開發工作](../core/development-tasks-for-biztalk-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="7b296-123">For more information, see [Development Tasks for BizTalk Application Deployment](../core/development-tasks-for-biztalk-application-deployment.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b296-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="7b296-124">In This Section</span></span>  
  
-   [<span data-ttu-id="7b296-125">當您從 Visual Studio 部署組件時發生哪些狀況</span><span class="sxs-lookup"><span data-stu-id="7b296-125">What Happens When You Deploy an Assembly from Visual Studio</span></span>](../core/what-happens-when-you-deploy-an-assembly-from-visual-studio.md)  
  
-   [<span data-ttu-id="7b296-126">GAC 中的組件安裝</span><span class="sxs-lookup"><span data-stu-id="7b296-126">Assembly Installation in the GAC</span></span>](../core/assembly-installation-in-the-gac.md)  
  
-   [<span data-ttu-id="7b296-127">如何設定強式名稱組件金鑰檔案</span><span class="sxs-lookup"><span data-stu-id="7b296-127">How to Configure a Strong Name Assembly Key File</span></span>](../core/how-to-configure-a-strong-name-assembly-key-file.md)  
  
-   [<span data-ttu-id="7b296-128">如何在 Visual Studio 中設定部署屬性</span><span class="sxs-lookup"><span data-stu-id="7b296-128">How to Set Deployment Properties in Visual Studio</span></span>](../core/how-to-set-deployment-properties-in-visual-studio.md)  
  
-   [<span data-ttu-id="7b296-129">如何部署 BizTalk 組件從 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7b296-129">How to Deploy a BizTalk Assembly from Visual Studio</span></span>](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)  
  
-   [<span data-ttu-id="7b296-130">如何重新部署 BizTalk 組件從 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7b296-130">How to Redeploy a BizTalk Assembly from Visual Studio</span></span>](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md)  
  
-   [<span data-ttu-id="7b296-131">如何安裝或解除安裝 GAC 中的組件</span><span class="sxs-lookup"><span data-stu-id="7b296-131">How to Install or uninstall an Assembly in the GAC</span></span>](../core/how-to-install-an-assembly-in-the-gac.md)  