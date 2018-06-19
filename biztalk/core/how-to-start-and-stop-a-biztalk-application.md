---
title: 如何啟動和停止 BizTalk 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- starting
- starting, applications
- managing [applications], starting
- managing [applications], stopping
- applications, starting
- stopping, applications
- applications, stopping
- stopping
ms.assetid: f9f83e99-a1e2-4dfd-b3be-60d3ec2cbcc4
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faacb2561b63d0e946c3408810db146e083f3e13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255590"
---
# <a name="how-to-start-and-stop-a-biztalk-application"></a><span data-ttu-id="03ddc-102">如何啟動和停止 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="03ddc-102">How to Start and Stop a BizTalk Application</span></span>
<span data-ttu-id="03ddc-103">本主題描述如何使用 [BizTalk Server 管理] 主控台來啟動及停止 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="03ddc-103">This topic describes how to use the BizTalk Server Administration console to start and stop a BizTalk application.</span></span>  
  
 <span data-ttu-id="03ddc-104">您可以啟動應用程式之前，繫結必須設定及其包含的所有協調流程中所述[如何設定協調流程繫結](../core/how-to-configure-bindings-for-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="03ddc-104">Before you can start an application, bindings must be configured for all orchestrations it contains, as described in [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="03ddc-105">在啟動應用程式時，可以選取一個或多個下列的選項：</span><span class="sxs-lookup"><span data-stu-id="03ddc-105">When you start an application, you can select one or more of the following options, as follows:</span></span>  
  
-   <span data-ttu-id="03ddc-106">登錄並啟動所有的協調流程。</span><span class="sxs-lookup"><span data-stu-id="03ddc-106">Enlist and start all orchestrations.</span></span>  
  
-   <span data-ttu-id="03ddc-107">登錄並啟動所有的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="03ddc-107">Enlist and start all send ports.</span></span>  
  
-   <span data-ttu-id="03ddc-108">登錄並啟動所有的傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="03ddc-108">Enlist and start all send port groups.</span></span>  
  
-   <span data-ttu-id="03ddc-109">啟用所有的接收位置。</span><span class="sxs-lookup"><span data-stu-id="03ddc-109">Enable all receive locations.</span></span>  
  
-   <span data-ttu-id="03ddc-110">啟動所有關聯的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="03ddc-110">Start all associated host instances.</span></span>  
  
-   <span data-ttu-id="03ddc-111">繼續擱置的執行個體。</span><span class="sxs-lookup"><span data-stu-id="03ddc-111">Resume suspended instances.</span></span>  
  
-   <span data-ttu-id="03ddc-112">部署所有原則。</span><span class="sxs-lookup"><span data-stu-id="03ddc-112">Deploy all policies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03ddc-113">只會自動部署應用程式中已發佈的原則。</span><span class="sxs-lookup"><span data-stu-id="03ddc-113">Only published policies in the application are deployed automatically.</span></span> <span data-ttu-id="03ddc-114">如果原則尚未發佈，則不會加以部署。</span><span class="sxs-lookup"><span data-stu-id="03ddc-114">If a policy is not published, it will not be deployed.</span></span>  
  
 <span data-ttu-id="03ddc-115">在停止應用程式時，可以選取一個或多個下列的選項：</span><span class="sxs-lookup"><span data-stu-id="03ddc-115">When you stop an application, you can select one of the following options:</span></span>  
  
-   <span data-ttu-id="03ddc-116">**部分停止-允許正在繼續的執行個體。**</span><span class="sxs-lookup"><span data-stu-id="03ddc-116">**Partial Stop - Allow running instances to continue.**</span></span> <span data-ttu-id="03ddc-117">：這個選項會停用應用程式中的所有接收位置，但保留所有其他成品的先前狀態。</span><span class="sxs-lookup"><span data-stu-id="03ddc-117">This option disables all receive locations in the application, but leaves all other artifacts in their previous state.</span></span> <span data-ttu-id="03ddc-118">如此可以讓正在執行的執行個體完成系統中目前訊息的處理。</span><span class="sxs-lookup"><span data-stu-id="03ddc-118">This allows running instances to complete processing messages that are currently in the system.</span></span> <span data-ttu-id="03ddc-119">請注意，如果訊息交易需要多項輸入，則使用這個選項可能無法完成。</span><span class="sxs-lookup"><span data-stu-id="03ddc-119">Note that if a message transaction requires multiple inputs, it may not be able to complete when you use this option.</span></span>  
  
-   <span data-ttu-id="03ddc-120">**部分停止-擱置正在執行的執行個體。**</span><span class="sxs-lookup"><span data-stu-id="03ddc-120">**Partial Stop - Suspend running instances.**</span></span> <span data-ttu-id="03ddc-121">：這個選項會停用應用程式中的所有接收位置，並停止應用程式中的所有協調流程和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="03ddc-121">This option disables all receive locations and stops all orchestrations and send ports in the application.</span></span> <span data-ttu-id="03ddc-122">它不會取消登錄或解除部署任何成品。</span><span class="sxs-lookup"><span data-stu-id="03ddc-122">It does not unenlist or undeploy any artifacts.</span></span> <span data-ttu-id="03ddc-123">如果想要暫停應用程式，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="03ddc-123">Use this option when you want to temporarily pause the application.</span></span>  
  
-   <span data-ttu-id="03ddc-124">**完全停止-終止執行個體。**</span><span class="sxs-lookup"><span data-stu-id="03ddc-124">**Full Stop - Terminate instances.**</span></span> <span data-ttu-id="03ddc-125">：這個選項會停用應用程式中的所有接收位置，並停止及取消登錄所有的協調流程和傳送埠，並解除部署所有的原則。</span><span class="sxs-lookup"><span data-stu-id="03ddc-125">This option disables all receive locations, stops and unenlists all orchestrations and send ports, and undeploys all policies in the application.</span></span> <span data-ttu-id="03ddc-126">如果想要完全解除部署應用程式，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="03ddc-126">Use this option when you want to completely undeploy an application.</span></span> <span data-ttu-id="03ddc-127">請注意，仍在處理訊息的所有執行中執行個體都不會完成處理作業。</span><span class="sxs-lookup"><span data-stu-id="03ddc-127">Note that any running instances that are still processing messages will not complete processing.</span></span> <span data-ttu-id="03ddc-128">如需詳細資訊，請參閱[解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="03ddc-128">For more information, see [Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="03ddc-129">必要條件</span><span class="sxs-lookup"><span data-stu-id="03ddc-129">Prerequisites</span></span>  
 <span data-ttu-id="03ddc-130">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="03ddc-130">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="03ddc-131">BizTalk 操作員可以執行部分停止，但無法執行完全停止。</span><span class="sxs-lookup"><span data-stu-id="03ddc-131">BizTalk Operators can perform a partial stop, but not a full stop.</span></span> <span data-ttu-id="03ddc-132">此外，如果所有成員都已登錄，則 BizTalk 操作員可以啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="03ddc-132">In addition, BizTalk Operators can start an application if all artifacts are enlisted.</span></span> <span data-ttu-id="03ddc-133">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="03ddc-133">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-start-or-stop-a-biztalk-application"></a><span data-ttu-id="03ddc-134">如何啟動和停止 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="03ddc-134">To start or stop a BizTalk application</span></span>  
  
1.  <span data-ttu-id="03ddc-135">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="03ddc-135">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="03ddc-136">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 展開 [BizTalk 群組]，然後再展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="03ddc-136">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="03ddc-137">以滑鼠右鍵按一下您想要啟動或停止，然後按一下的 BizTalk 應用程式**啟動**或**停止**。</span><span class="sxs-lookup"><span data-stu-id="03ddc-137">Right-click the BizTalk application that you want to start or stop, and then click **Start** or **Stop**.</span></span>  
  
4.  <span data-ttu-id="03ddc-138">選取啟動或停止選項和按一下**啟動**或**停止**。</span><span class="sxs-lookup"><span data-stu-id="03ddc-138">Select the start or stop options you want and click **Start** or **Stop**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ddc-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03ddc-139">See Also</span></span>  
 <span data-ttu-id="03ddc-140">[部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="03ddc-140">[Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="03ddc-141">更新 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="03ddc-141">Updating BizTalk Applications</span></span>](../core/updating-biztalk-applications.md)