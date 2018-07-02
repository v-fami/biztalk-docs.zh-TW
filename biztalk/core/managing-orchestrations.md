---
title: 管理協調流程 |Microsoft Docs
description: 若要使用協調流程在 BizTalk Server 中，包括啟動、 停止、 繫結、 設定、 啟用追蹤、 暫止的連結和其他
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2553eec3-b863-45fb-90af-7eddcfa7add7
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16a989cb7853e63e1e603febf44db45288276ecd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976479"
---
# <a name="manage-orchestrations"></a><span data-ttu-id="9813c-103">管理協調流程</span><span class="sxs-lookup"><span data-stu-id="9813c-103">Manage Orchestrations</span></span>

## <a name="overview"></a><span data-ttu-id="9813c-104">概觀</span><span class="sxs-lookup"><span data-stu-id="9813c-104">Overview</span></span>
<span data-ttu-id="9813c-105">本節中提供的指示，可讓您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來管理協調流程。</span><span class="sxs-lookup"><span data-stu-id="9813c-105">This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to manage orchestrations.</span></span> <span data-ttu-id="9813c-106">協調流程是可執行的商務程序。</span><span class="sxs-lookup"><span data-stu-id="9813c-106">An orchestration is an executable business process.</span></span> <span data-ttu-id="9813c-107">如需協調流程的背景資訊，請參閱 <<c0> [ 協調流程](../core/orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="9813c-107">For background information about orchestrations, see [Orchestrations](../core/orchestrations.md).</span></span>  

## <a name="add-to-application"></a><span data-ttu-id="9813c-108">新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="9813c-108">Add to application</span></span>  
 <span data-ttu-id="9813c-109">協調流程內建於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，並被編譯到 BizTalk 組件中。</span><span class="sxs-lookup"><span data-stu-id="9813c-109">Orchestrations are built in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies.</span></span> <span data-ttu-id="9813c-110">您無法將協調流程個別新增到應用程式；請遵循下列步驟將協調流程新增到應用程式：</span><span class="sxs-lookup"><span data-stu-id="9813c-110">You cannot add an orchestration to an application individually; an orchestration is added to an application as follows:</span></span>  
  
- <span data-ttu-id="9813c-111">當您新增 BizTalk 組件包含應用程式，協調流程中所述[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="9813c-111">When you add a BizTalk assembly containing an orchestration to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
- <span data-ttu-id="9813c-112">當您匯入.msi 檔案包含包含協調流程的 BizTalk 組件中所述的應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="9813c-112">When you import an .msi file into an application that includes a BizTalk assembly containing an orchestration, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
- <span data-ttu-id="9813c-113">當開發人員部署至應用程式包含協調流程的組件[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中所述[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="9813c-113">When a developer deploys into an application an assembly containing an orchestration from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  

## <a name="biztalk-administration-tasks"></a><span data-ttu-id="9813c-114">BizTalk 系統管理工作</span><span class="sxs-lookup"><span data-stu-id="9813c-114">BizTalk Administration tasks</span></span>  
 <span data-ttu-id="9813c-115">您可以使用管理主控台來執行下列動作，如本節中的說明：</span><span class="sxs-lookup"><span data-stu-id="9813c-115">You use the administration console to perform the following actions, as described in this section:</span></span>  
  
-   <span data-ttu-id="9813c-116">藉由將協調流程繫結至適當的傳送埠、接收埠和主控件來設定協調流程的繫結，或是將這些繫結從協調流程中移除。</span><span class="sxs-lookup"><span data-stu-id="9813c-116">Configure bindings for the orchestration by binding the orchestration to the appropriate send and receive ports and host, or remove these bindings from the orchestration.</span></span>  
  
-   <span data-ttu-id="9813c-117">設定協調流程的訊息追蹤。</span><span class="sxs-lookup"><span data-stu-id="9813c-117">Configure message tracking for the orchestration.</span></span>  
  
-   <span data-ttu-id="9813c-118">檢視協調流程的執行個體資訊。</span><span class="sxs-lookup"><span data-stu-id="9813c-118">View instance information for the orchestration.</span></span>  
  
-   <span data-ttu-id="9813c-119">將協調流程登錄到適當的主控件，或從主控件取消登錄協調流程。</span><span class="sxs-lookup"><span data-stu-id="9813c-119">Enlist the orchestration to the appropriate host or unenlist the orchestration from the host.</span></span>  
  
-   <span data-ttu-id="9813c-120">開始或停止協調流程，使其開始或停止處理訊息。</span><span class="sxs-lookup"><span data-stu-id="9813c-120">Start or stop the orchestration so that it starts or stops processing messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9813c-121">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="9813c-121">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="9813c-122">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="9813c-122">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
> 
> [!NOTE]
>  <span data-ttu-id="9813c-123">開發人員會使用來建立協調流程，協調流程設計師 」 中所述[協調流程使用協調流程設計師建立](../core/creating-orchestrations-using-orchestration-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="9813c-123">The developer uses Orchestration Designer to create orchestrations, as described in [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md).</span></span> <span data-ttu-id="9813c-124">開發人員也可以在開發程序中，藉由使用管理主控台 (如本節中的說明) 來管理協調流程。</span><span class="sxs-lookup"><span data-stu-id="9813c-124">The developer can manage orchestrations during the development process by using the administration console, as described in this section.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9813c-125">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="9813c-125">Next steps</span></span>
  
-   [<span data-ttu-id="9813c-126">設定協調流程的繫結</span><span class="sxs-lookup"><span data-stu-id="9813c-126">Configure Bindings for an Orchestration</span></span>](../core/how-to-configure-bindings-for-an-orchestration.md)  
  
-   [<span data-ttu-id="9813c-127">解除繫結協調流程</span><span class="sxs-lookup"><span data-stu-id="9813c-127">Unbind an Orchestration</span></span>](../core/how-to-unbind-an-orchestration.md)  
  
-   [<span data-ttu-id="9813c-128">設定協調流程的追蹤</span><span class="sxs-lookup"><span data-stu-id="9813c-128">Configure Tracking for an Orchestration</span></span>](../core/how-to-configure-tracking-for-an-orchestration.md)  
  
-   [<span data-ttu-id="9813c-129">檢視協調流程的執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="9813c-129">View Instance Information for an Orchestration</span></span>](../core/how-to-view-instance-information-for-an-orchestration.md)  
  
-   [<span data-ttu-id="9813c-130">從應用程式移除協調流程</span><span class="sxs-lookup"><span data-stu-id="9813c-130">Remove an Orchestration from an Application</span></span>](../core/how-to-remove-an-orchestration-from-an-application.md)  
  
-   [<span data-ttu-id="9813c-131">登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="9813c-131">Enlist an Orchestration</span></span>](../core/how-to-enlist-an-orchestration.md)  
  
-   [<span data-ttu-id="9813c-132">取消登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="9813c-132">Unenlist an Orchestration</span></span>](../core/how-to-unenlist-an-orchestration.md)  
  
-   [<span data-ttu-id="9813c-133">啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="9813c-133">Start an Orchestration</span></span>](../core/how-to-start-an-orchestration.md)  
  
-   [<span data-ttu-id="9813c-134">停止協調流程</span><span class="sxs-lookup"><span data-stu-id="9813c-134">Stop an Orchestration</span></span>](../core/how-to-stop-an-orchestration.md)  
  
-   [<span data-ttu-id="9813c-135">擱置、繼續和終止協調流程執行個體</span><span class="sxs-lookup"><span data-stu-id="9813c-135">Suspend, Resume, and Terminate Orchestration Instances</span></span>](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md)  
  
-   [<span data-ttu-id="9813c-136">升級協調流程</span><span class="sxs-lookup"><span data-stu-id="9813c-136">Upgrade an Orchestration</span></span>](../core/how-to-upgrade-an-orchestration.md)