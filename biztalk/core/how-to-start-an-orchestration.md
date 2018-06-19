---
title: 如何啟動協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], starting
- starting, orchestrations
- orchestrations, starting
ms.assetid: 83411279-ee6f-4d68-aa3b-b5cd5e106088
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e277c078a36129a125937114ee9287a1e97999b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255422"
---
# <a name="how-to-start-an-orchestration"></a><span data-ttu-id="b02d3-102">如何啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="b02d3-102">How to Start an Orchestration</span></span>
<span data-ttu-id="b02d3-103">本主題描述如何使用 BizTalk Server 管理主控台來啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="b02d3-103">This topic describes how to use the BizTalk Server Administration console to start an orchestration.</span></span> <span data-ttu-id="b02d3-104">當您啟動協調流程時，會開始處理內送訊息。</span><span class="sxs-lookup"><span data-stu-id="b02d3-104">When you start an orchestration, it begins processing incoming messages.</span></span>  
  
 <span data-ttu-id="b02d3-105">啟動協調流程時，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="b02d3-105">When starting and orchestration, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="b02d3-106">在您啟動協調流程之前，必須先登錄協調流程以及與它相關的所有傳送埠和傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="b02d3-106">Before you can start the orchestration, it must be enlisted, along with all of the send ports and send port groups associated with it.</span></span> <span data-ttu-id="b02d3-107">如需指示，請參閱[如何登錄協調流程](../core/how-to-enlist-an-orchestration.md)和[如何登錄傳送埠或傳送埠群組](../core/how-to-enlist-a-send-port-or-send-port-group.md)。</span><span class="sxs-lookup"><span data-stu-id="b02d3-107">For instructions, see [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md) and [How to Enlist a Send Port or Send Port Group](../core/how-to-enlist-a-send-port-or-send-port-group.md).</span></span>  
  
-   <span data-ttu-id="b02d3-108">啟動協調流程不會自動啟動任何相關的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b02d3-108">Starting an orchestration does not automatically start any associated send ports.</span></span> <span data-ttu-id="b02d3-109">您必須個別啟動它們，如中所述[如何啟動傳送埠或傳送埠群組](../core/how-to-start-a-send-port-or-send-port-group.md)。</span><span class="sxs-lookup"><span data-stu-id="b02d3-109">You must start them separately, as described in [How to Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md).</span></span>  
  
-   <span data-ttu-id="b02d3-110">如果您登錄與該協調流程相關的傳送埠和/或傳送埠群組，但是不啟動它們，BizTalk Server 會將傳送給該傳送埠或傳送埠群組的任何訊息放置在主控件的擱置佇列中，此主控件便是您登錄傳送埠或傳送埠群組的地方。</span><span class="sxs-lookup"><span data-stu-id="b02d3-110">If you enlist the send ports and/or send port groups associated with this orchestration, but do not start them, BizTalk Server places any messages sent to this send port or send port group in the suspended queue of the host where you enlisted the send port or send port group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b02d3-111">應用程式開發人員可以啟動協調流程以測試其功能在開發過程中，使用本主題中的程序。</span><span class="sxs-lookup"><span data-stu-id="b02d3-111">The application developer can start an orchestration to test its functionality during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b02d3-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="b02d3-112">Prerequisites</span></span>  
 <span data-ttu-id="b02d3-113">若要執行這個主題中的程序，您必須以「BizTalk Server 操作員」群組或「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="b02d3-113">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Operators group or the BizTalk Server Administrators group.</span></span> <span data-ttu-id="b02d3-114">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b02d3-114">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-start-an-orchestration"></a><span data-ttu-id="b02d3-115">啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="b02d3-115">To start an orchestration</span></span>  
  
1.  <span data-ttu-id="b02d3-116">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="b02d3-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b02d3-117">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您想要啟動的協調流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b02d3-117">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to start.</span></span>  
  
3.  <span data-ttu-id="b02d3-118">按一下**協調流程**，協調流程中，以滑鼠右鍵按一下，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="b02d3-118">Click **Orchestrations**, right-click the orchestration, and then click **Start**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b02d3-119">如果沒有在啟動協調流程前先登錄相關的傳送埠和傳送埠群組，您將會看到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="b02d3-119">If you did not first enlist the associated send port and send port groups before starting the orchestration, you will see an error message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b02d3-120">若要同時啟動多個協調流程，按住 shift 鍵並選取每個協調流程、 協調流程，以滑鼠右鍵按一下，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="b02d3-120">To start multiple orchestrations at once, hold down the shift key and select each orchestration, right-click an orchestration, and then click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b02d3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b02d3-121">See Also</span></span>  
 <span data-ttu-id="b02d3-122">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="b02d3-122">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="b02d3-123">[如何停止協調流程](../core/how-to-stop-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="b02d3-123">[How to Stop an Orchestration](../core/how-to-stop-an-orchestration.md) </span></span>  
 [<span data-ttu-id="b02d3-124">如何啟動和停止 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="b02d3-124">How to Start and Stop a BizTalk Application</span></span>](../core/how-to-start-and-stop-a-biztalk-application.md)