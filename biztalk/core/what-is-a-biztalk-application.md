---
title: "何謂 BizTalk 應用程式？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk.System application, about BizTalk.System application
- applications, default
- BizTalk.System application
- artifacts, about artifacts
- applications
- applications, about applications
- applications, warnings
- applications, BizTalk.System
- what's new, applications
- BizTalk.System application, warnings
ms.assetid: 68b5527c-d5e1-453b-a51b-3fc1a1d5dce2
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9ff0e2be82d528c7070955c1ce79b1f5e37cc6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-a-biztalk-application"></a><span data-ttu-id="879cd-103">何謂 BizTalk 應用程式？</span><span class="sxs-lookup"><span data-stu-id="879cd-103">What Is a BizTalk Application?</span></span>
<span data-ttu-id="879cd-104">BizTalk 應用程式是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的功能，能讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 商務解決方案的部署、管理和疑難排解更加快速輕鬆。</span><span class="sxs-lookup"><span data-stu-id="879cd-104">The BizTalk application is a feature of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that makes it quicker and easier to deploy, manage, and troubleshoot [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] business solutions.</span></span> <span data-ttu-id="879cd-105">BizTalk 應用程式是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 商務解決方案中所使用項目 (稱為「成品」) 的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="879cd-105">A BizTalk application is a logical grouping of the items, called "artifacts," used in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] business solution.</span></span> <span data-ttu-id="879cd-106">在本主題在稍後將會詳細說明成品。</span><span class="sxs-lookup"><span data-stu-id="879cd-106">Artifacts are described in more detail later in this topic.</span></span>  
  
 <span data-ttu-id="879cd-107">新設計的 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 管理和監控工具會利用這個新概念，所以不僅您在個別成品層級，也可在應用程式層級上管理和設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 商務解決方案。</span><span class="sxs-lookup"><span data-stu-id="879cd-107">The newly designed administration and monitoring tools of [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] take advantage of this new concept, so that you can manage and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] business solutions at the application level, and not just at the individual artifact level.</span></span> <span data-ttu-id="879cd-108">透過建立應用程式並將成品加入至其中，您可以將解決方案中的一組成品當做單一實體，予以檢視、封裝、部署和管理。.</span><span class="sxs-lookup"><span data-stu-id="879cd-108">By creating an application and adding artifacts to it, you can view, package, deploy, and manage a group of artifacts in a solution as a single entity.</span></span> <span data-ttu-id="879cd-109">因此，隨著複雜應用程式的增加，您仍然可以透過簡單、直覺化方式個別管理它們。</span><span class="sxs-lookup"><span data-stu-id="879cd-109">Therefore, as the number of complex applications increases you can still manage them individually in a simple and intuitive manner.</span></span>  
  
 <span data-ttu-id="879cd-110">有數種工具可用來建立和管理應用程式，如下所述[應用程式部署和管理工具](../core/application-deployment-and-management-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="879cd-110">There are several tools you can use to create and manage applications, which are described in [Application Deployment and Management Tools](../core/application-deployment-and-management-tools.md).</span></span>  
  
 <span data-ttu-id="879cd-111">下列圖表說明兩個 BizTalk 應用程式及其包含的成品。</span><span class="sxs-lookup"><span data-stu-id="879cd-111">The following diagram depicts two BizTalk applications and the artifacts that they contain.</span></span>  
  
 <span data-ttu-id="879cd-112">![BizTalk 應用程式和成品](../core/media/biztalkapplication.gif "BizTalkApplication")</span><span class="sxs-lookup"><span data-stu-id="879cd-112">![BizTalk applications and artifacts](../core/media/biztalkapplication.gif "BizTalkApplication")</span></span>  
  
## <a name="artifacts"></a><span data-ttu-id="879cd-113">成品</span><span class="sxs-lookup"><span data-stu-id="879cd-113">Artifacts</span></span>  
 <span data-ttu-id="879cd-114">成品如下：</span><span class="sxs-lookup"><span data-stu-id="879cd-114">Artifacts include the following:</span></span>  
  
-   <span data-ttu-id="879cd-115">BizTalk 組件及其包含的 BizTalk 特定資源，例如協調流程、管線、結構描述和對應</span><span class="sxs-lookup"><span data-stu-id="879cd-115">BizTalk assemblies and the BizTalk-specific resources that they contain – orchestrations, pipelines, schemas, and maps</span></span>  
  
-   <span data-ttu-id="879cd-116">不包含 BizTalk 特定資源的 .NET 組件</span><span class="sxs-lookup"><span data-stu-id="879cd-116">.NET assemblies that do not contain BizTalk-specific resources</span></span>  
  
-   <span data-ttu-id="879cd-117">原則</span><span class="sxs-lookup"><span data-stu-id="879cd-117">Policies</span></span>  
  
-   <span data-ttu-id="879cd-118">傳送埠、接收埠群組、接收位置和接收埠</span><span class="sxs-lookup"><span data-stu-id="879cd-118">Send ports, send port groups, receive locations, and receive ports</span></span>  
  
-   <span data-ttu-id="879cd-119">解決方案使用的其他項目，例如憑證、COM 元件和指令碼</span><span class="sxs-lookup"><span data-stu-id="879cd-119">Other items that are used by the solution, such as certificates, COM components, and scripts</span></span>  
  
 <span data-ttu-id="879cd-120">如需每種類型的成品的背景資訊，請參閱[執行階段架構](../core/runtime-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="879cd-120">For background information about each type of artifact, see [Runtime Architecture](../core/runtime-architecture.md).</span></span> <span data-ttu-id="879cd-121">如需有關新增的詳細資訊，請移除和設定成品，請參閱[管理成品](../core/managing-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="879cd-121">For more information about adding, removing, and configuring artifacts, see [Managing Artifacts](../core/managing-artifacts.md).</span></span>  
  
 <span data-ttu-id="879cd-122">一個應用程式可以包含商務解決方案中使用的全部成品或其中一部分。</span><span class="sxs-lookup"><span data-stu-id="879cd-122">An application can contain all of the artifacts used in a business solution or only some of them.</span></span> <span data-ttu-id="879cd-123">根據所需的部署成品方式，您可以將成品放入一個或多個應用程式中。</span><span class="sxs-lookup"><span data-stu-id="879cd-123">Depending on how you want to deploy the artifacts, you may want to place them into a single application or into two or more applications.</span></span> <span data-ttu-id="879cd-124">如需有關決定如何群組成品的詳細資訊，請參閱[部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="879cd-124">For more information about deciding how to group artifacts, see [Best Practices for Deploying a BizTalk Application](../core/best-practices-for-deploying-a-biztalk-application.md).</span></span>  
  
## <a name="the-default-application"></a><span data-ttu-id="879cd-125">預設應用程式</span><span class="sxs-lookup"><span data-stu-id="879cd-125">The default application</span></span>  
 <span data-ttu-id="879cd-126">在安裝後設定 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 時，會自動建立名為「BizTalk 應用程式 1」的預設應用程式。</span><span class="sxs-lookup"><span data-stu-id="879cd-126">When [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] is configured following installation, a default application named BizTalk Application 1 is automatically created.</span></span> <span data-ttu-id="879cd-127">如需最佳作法，將成品分組到不同的應用程式的資訊，請參閱[部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="879cd-127">For information about best practices for grouping artifacts into different applications, see [Best Practices for Deploying a BizTalk Application](../core/best-practices-for-deploying-a-biztalk-application.md).</span></span> <span data-ttu-id="879cd-128">您也可以變更或重新命名預設應用程式。</span><span class="sxs-lookup"><span data-stu-id="879cd-128">You can also change the default application or rename the default application.</span></span>  
  
 <span data-ttu-id="879cd-129">在下列實例中，成品會自動加入至預設應用程式：</span><span class="sxs-lookup"><span data-stu-id="879cd-129">In the following scenarios, artifacts are automatically added to the default application:</span></span>  
  
-   <span data-ttu-id="879cd-130">當您從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 將組件部署至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，但未指定應用程式名稱時。</span><span class="sxs-lookup"><span data-stu-id="879cd-130">When you deploy an assembly from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] without specifying an application name.</span></span> <span data-ttu-id="879cd-131">如需詳細資訊，請參閱[如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="879cd-131">For more information, see [How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).</span></span>  
  
-   <span data-ttu-id="879cd-132">當您使用 BTSTask 將成品加入至應用程式，但未指定應用程式名稱時。</span><span class="sxs-lookup"><span data-stu-id="879cd-132">When you use BTSTask to add an artifact to an application without specifying an application name.</span></span> <span data-ttu-id="879cd-133">如需詳細資訊，請參閱[AddResource 命令](../core/addresource-command.md)。</span><span class="sxs-lookup"><span data-stu-id="879cd-133">For more information, see [AddResource Command](../core/addresource-command.md).</span></span>  
  
-   <span data-ttu-id="879cd-134">當您使用 BTSTask 匯入應用程式 .msi 檔案，但未指定應用程式名稱時。</span><span class="sxs-lookup"><span data-stu-id="879cd-134">When you use BTSTask to import an application .msi file without specifying an application name.</span></span> <span data-ttu-id="879cd-135">如需詳細資訊，請參閱[ImportApp 命令](../core/importapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="879cd-135">For more information, see [ImportApp Command](../core/importapp-command.md).</span></span>  
  
## <a name="the-biztalksystem-application"></a><span data-ttu-id="879cd-136">BizTalk.System 應用程式</span><span class="sxs-lookup"><span data-stu-id="879cd-136">The BizTalk.System application</span></span>  
 <span data-ttu-id="879cd-137">在安裝後設定 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 時，會自動建立名為 BizTalk.System 的應用程式，並在其中填入所有 BizTalk 應用程式都會使用的通用成品，例如預設結構描述和管線。</span><span class="sxs-lookup"><span data-stu-id="879cd-137">When [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] is configured following installation, an application named BizTalk.System is automatically created and populated with common artifacts that are used by all BizTalk applications, such as the default schemas and pipelines.</span></span> <span data-ttu-id="879cd-138">BizTalk.System 及其成品都是唯讀。</span><span class="sxs-lookup"><span data-stu-id="879cd-138">BizTalk.System and its artifacts are read-only.</span></span> <span data-ttu-id="879cd-139">您不能刪除或重新命名 BizTalk.System，也不能刪除、重新命名或移動其中包含的任何成品。</span><span class="sxs-lookup"><span data-stu-id="879cd-139">You cannot delete or rename BizTalk.System, nor can you delete, rename, or move any of the artifacts that it contains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="879cd-140">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的每個應用程式都會自動包含 BizTalk.System 應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="879cd-140">Every application in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically contains a reference to the BizTalk.System application.</span></span> <span data-ttu-id="879cd-141">這是因為每個 BizTalk 應用程式都會使用 BizTalk.System 的成品。</span><span class="sxs-lookup"><span data-stu-id="879cd-141">This is because the artifacts in BizTalk.System are used by every BizTalk application.</span></span> <span data-ttu-id="879cd-142">您絕對不能移除 BizTalk.系統應用程式的參考，</span><span class="sxs-lookup"><span data-stu-id="879cd-142">You should never remove a reference to the BizTalk.System application.</span></span> <span data-ttu-id="879cd-143">否則您的應用程式可能無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="879cd-143">If you do, your application may not function correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="879cd-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="879cd-144">See Also</span></span>  
 [<span data-ttu-id="879cd-145">了解 BizTalk 應用程式部署和管理</span><span class="sxs-lookup"><span data-stu-id="879cd-145">Understanding BizTalk Application Deployment and Management</span></span>](../core/understanding-biztalk-application-deployment-and-management.md)