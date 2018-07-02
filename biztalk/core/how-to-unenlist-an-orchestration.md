---
title: 如何取消登錄協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, unenlisting
- enlisting, unenlisting
- managing [orchestrations], unenlisting
- unenlisting, orchestrations
ms.assetid: 038ed7bb-615c-4e4e-a5bb-79de2626de77
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7504551d6cc97f108d6cdee695f241ee983994a2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993511"
---
# <a name="how-to-unenlist-an-orchestration"></a><span data-ttu-id="abef5-102">如何取消登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="abef5-102">How to Unenlist an Orchestration</span></span>
<span data-ttu-id="abef5-103">本主題描述如何使用 BizTalk Server 管理主控台來取消登錄協調流程。</span><span class="sxs-lookup"><span data-stu-id="abef5-103">This topic describes how to unenlist an orchestration by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="abef5-104">取消登錄協調流程會將其從主控件中移除。</span><span class="sxs-lookup"><span data-stu-id="abef5-104">Unenlisting an orchestration removes it from the host.</span></span> <span data-ttu-id="abef5-105">這會移除訂閱，使協調流程不再處理訊息。</span><span class="sxs-lookup"><span data-stu-id="abef5-105">This removes the subscription so that the orchestration no longer processes messages.</span></span> <span data-ttu-id="abef5-106">您必須先取消登錄協調流程才能夠編輯其繫結。</span><span class="sxs-lookup"><span data-stu-id="abef5-106">You must unenlist an orchestration before you can edit its bindings.</span></span>  
  
 <span data-ttu-id="abef5-107">您可以取消登錄協調流程之前，您必須終止任何執行的執行個體中, 所述[如何暫停、 繼續和終止協調流程執行個體](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="abef5-107">Before you can unenlist an orchestration, you must terminate any running instances, as described in [How to Suspend, Resume, and Terminate Orchestration Instances](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abef5-108">應用程式開發人員可以使用此主題中的程序，在開發程序中取消登錄協調流程。</span><span class="sxs-lookup"><span data-stu-id="abef5-108">The application developer can unenlist an orchestration during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="abef5-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="abef5-109">Prerequisites</span></span>  
 <span data-ttu-id="abef5-110">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="abef5-110">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="abef5-111">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="abef5-111">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-unenlist-an-orchestration"></a><span data-ttu-id="abef5-112">取消登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="abef5-112">To unenlist an orchestration</span></span>  
  
1. <span data-ttu-id="abef5-113">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="abef5-113">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="abef5-114">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您想要取消登錄協調流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="abef5-114">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to unenlist.</span></span>  
  
3. <span data-ttu-id="abef5-115">按一下 **協調流程**，以滑鼠右鍵按一下以取消登錄，然後按一下 協調流程**取消登錄**。</span><span class="sxs-lookup"><span data-stu-id="abef5-115">Click **Orchestrations**, right-click the orchestration to unenlist, and then click **Unenlist**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="abef5-116">若要次取消登錄多個協調流程，請按住 shift 鍵並選取每個要取消登錄的協調流程，協調流程，以滑鼠右鍵按一下，然後按一下**取消登錄**。</span><span class="sxs-lookup"><span data-stu-id="abef5-116">To unenlist multiple orchestrations at once, hold down the shift key and select each orchestration to unenlist, right-click an orchestration, and then click **Unenlist**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abef5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abef5-117">See Also</span></span>  
 <span data-ttu-id="abef5-118">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="abef5-118">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="abef5-119">[如何登錄協調流程](../core/how-to-enlist-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="abef5-119">[How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md) </span></span>  
 [<span data-ttu-id="abef5-120">部署和管理 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="abef5-120">Deploying and Managing BizTalk Applications</span></span>](../core/deploying-and-managing-biztalk-applications.md)