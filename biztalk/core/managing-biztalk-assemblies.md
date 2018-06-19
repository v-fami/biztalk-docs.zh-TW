---
title: 管理 BizTalk 組件 |Microsoft 文件
description: 若要使用 BizTalk Server 中，包括新增、 更新、 檢視相依性，以及移除組件中的組件的連結
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62cc92f5-a1ea-46e4-88e6-b8a71a0c40a2
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c0dc8e74e23c7dc0b3a4e7a62a76297988b6b2e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262686"
---
# <a name="manage-biztalk-assemblies"></a><span data-ttu-id="c6660-103">管理 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="c6660-103">Manage BizTalk Assemblies</span></span>

## <a name="overview"></a><span data-ttu-id="c6660-104">概觀</span><span class="sxs-lookup"><span data-stu-id="c6660-104">Overview</span></span>
<span data-ttu-id="c6660-105">本節提供在將 BizTalk 組件部署至 BizTalk 群組後，如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台或 BTSTask 命令列工具管理這些組件的指示。</span><span class="sxs-lookup"><span data-stu-id="c6660-105">This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or the BTSTask command-line tool to manage BizTalk assemblies after they have been deployed into a BizTalk group.</span></span> <span data-ttu-id="c6660-106">BizTalk 組件是 Microsoft Windows DLL 檔案，包含 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 商務解決方案中所使用的資源資訊，例如協調流程、管線、結構描述及對應。</span><span class="sxs-lookup"><span data-stu-id="c6660-106">A BizTalk assembly is a Microsoft Windows DLL file that contains resource information, such as orchestrations, pipelines, schemas, and maps to be used in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] business solution.</span></span> <span data-ttu-id="c6660-107">如需 BizTalk 組件的背景資訊，請參閱[BizTalk 組件](../core/biztalk-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="c6660-107">For background information on BizTalk assemblies, see [BizTalk Assemblies](../core/biztalk-assemblies.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6660-108">部署或解除部署屬性結構描述可能會公開機密資料，而之後可能會在追蹤期間公開機密資訊。</span><span class="sxs-lookup"><span data-stu-id="c6660-108">Deploying or undeploying a property schema may expose sensitive data, and subsequently expose sensitive information during tracking.</span></span> <span data-ttu-id="c6660-109">每當部署或解除部署包含屬性結構描述的組件時，事件檢視器會將事件記錄在 Windows 應用程式事件記錄中。</span><span class="sxs-lookup"><span data-stu-id="c6660-109">Whenever an assembly containing a property schema is deployed or undeployed, the event viewer logs an event in the Windows Application Event Log.</span></span> <span data-ttu-id="c6660-110">您應檢查事件日誌檔中的這些訊息，確保所有組件部署活動都符合任何機密資料的原則</span><span class="sxs-lookup"><span data-stu-id="c6660-110">You should check the event log for these messages to ensure that all assembly deployment activities are in line with your policies for any sensitive data.</span></span> <span data-ttu-id="c6660-111">(為部署事件記錄檔產生的訊息: 「 使用者 」 {1} 「 已部署的組件"{0}"包含屬性結構描述 」。</span><span class="sxs-lookup"><span data-stu-id="c6660-111">(The message generated to the Event Log for deployment is: "The user "{1}" deployed the assembly "{0}" containing property schemas."</span></span> <span data-ttu-id="c6660-112">解除部署會產生事件記錄檔訊息: 「 使用者 」 {1}"已解除部署組件"{0}"包含屬性結構描述 」。)</span><span class="sxs-lookup"><span data-stu-id="c6660-112">The message generated to the Event Log for undeployment is: "The user "{1}" undeployed the assembly "{0}" containing property schemas.")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6660-113">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c6660-113">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="c6660-114">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="c6660-114">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="c6660-115">開發人員使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]開發 BizTalk 組件中所述[開發 BizTalk Server 應用程式](../core/developing-biztalk-server-applications.md)，並將其從可以部署[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中所述[部署從 Visual Studio 到 BizTalk 應用程式的 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c6660-115">The developer uses [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to develop BizTalk assemblies, as described in [Developing BizTalk Server Applications](../core/developing-biztalk-server-applications.md), and can deploy them from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span> <span data-ttu-id="c6660-116">開發人員也可以在開發程序中，藉由使用管理主控台 (如本節中的說明) 來管理 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="c6660-116">The developer can also manage BizTalk assemblies during the development process by using either the administration console, as described in this section.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c6660-117">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="c6660-117">Next steps</span></span> 
  
-   [<span data-ttu-id="c6660-118">應用程式中加入 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="c6660-118">Add a BizTalk Assembly to an Application</span></span>](../core/how-to-add-a-biztalk-assembly-to-an-application.md)  
  
-   [<span data-ttu-id="c6660-119">修改 BizTalk 組件的部署選項</span><span class="sxs-lookup"><span data-stu-id="c6660-119">Modify the Deployment Options of a BizTalk Assembly</span></span>](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md)  
  
-   [<span data-ttu-id="c6660-120">檢視 BizTalk 組件的相依性</span><span class="sxs-lookup"><span data-stu-id="c6660-120">View the Dependencies for a BizTalk Assembly</span></span>](../core/how-to-view-the-dependencies-for-a-biztalk-assembly.md)  
  
-   [<span data-ttu-id="c6660-121">從應用程式移除 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="c6660-121">Remove a BizTalk Assembly from an Application</span></span>](../core/how-to-remove-a-biztalk-assembly-from-an-application.md)