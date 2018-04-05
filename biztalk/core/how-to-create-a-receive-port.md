---
title: 如何建立接收埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.procedure.createreceiveport
helpviewer_keywords:
- receive ports, creating
- managing [receive ports], creating
- creating, receive ports
ms.assetid: 23fae441-be80-4759-b3d6-74787a40e65b
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdecbc36962d3e4e45d35171747ff4c450959a83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-receive-port"></a><span data-ttu-id="56bc3-102">如何建立接收埠</span><span class="sxs-lookup"><span data-stu-id="56bc3-102">How to Create a Receive Port</span></span>
<span data-ttu-id="56bc3-103">本主題描述如何使用 BizTalk Server 管理主控台來建立接收埠。</span><span class="sxs-lookup"><span data-stu-id="56bc3-103">This topic describes how to use the BizTalk Server Administration console to create a receive port.</span></span> <span data-ttu-id="56bc3-104">接收埠是相似接收位置的邏輯群組，服務會透過這些位置接收資料，以與外部夥伴互動。</span><span class="sxs-lookup"><span data-stu-id="56bc3-104">A receive port is a logical grouping of similar receive locations through which services interact with external partners by receiving data.</span></span>  
  
 <span data-ttu-id="56bc3-105">您可以建立下列類型的接收埠：</span><span class="sxs-lookup"><span data-stu-id="56bc3-105">You can create the following types of receive ports:</span></span>  
  
-   <span data-ttu-id="56bc3-106">單向：用在應用程式放置訊息但不同步等候回覆時</span><span class="sxs-lookup"><span data-stu-id="56bc3-106">One-way — used for applications that drop off a message and do not wait synchronously for a reply</span></span>  
  
-   <span data-ttu-id="56bc3-107">要求-回應：用在應用程式需要訊息的回應時</span><span class="sxs-lookup"><span data-stu-id="56bc3-107">Request-response — used with applications that require a response to a message</span></span>  
  
 <span data-ttu-id="56bc3-108">除了本主題中所述的設定，您也可以指定接收埠，處理的訊息追蹤選項中所述[如何設定追蹤接收埠](../core/how-to-configure-tracking-for-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="56bc3-108">In addition to the configuration described in this topic, you can also specify tracking options for the messages handled by a receive port, as described in [How to Configure Tracking for a Receive Port](../core/how-to-configure-tracking-for-a-receive-port.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56bc3-109">如果您要在遠端電腦上建立接收埠，而該電腦沒有啟用網路 DTC，就必須在建立接收埠之後，將遠端電腦重新開機。</span><span class="sxs-lookup"><span data-stu-id="56bc3-109">If you are creating a receive port on a remote computer and that computer does not have network DTC enabled, you will have to reboot the remote computer after creating the receive port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="56bc3-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="56bc3-110">Prerequisites</span></span>  
 <span data-ttu-id="56bc3-111">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="56bc3-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="56bc3-112">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="56bc3-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-create-a-receive-port"></a><span data-ttu-id="56bc3-113">建立接收埠</span><span class="sxs-lookup"><span data-stu-id="56bc3-113">To create a receive port</span></span>  
  
1.  <span data-ttu-id="56bc3-114">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="56bc3-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="56bc3-115">在主控台樹狀目錄中，展開您要建立接收埠的 BizTalk 群組和 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="56bc3-115">In the console tree, expand the BizTalk group and the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="56bc3-116">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**或**要求回應接收埠**根據連接埠類型，您想要建立。</span><span class="sxs-lookup"><span data-stu-id="56bc3-116">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port** or **Request Response Receive Port**, according to the type of port you want to create.</span></span>  
  
4.  <span data-ttu-id="56bc3-117">在**接收埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="56bc3-117">In the **Receive Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="56bc3-118">使用</span><span class="sxs-lookup"><span data-stu-id="56bc3-118">Use this</span></span>|<span data-ttu-id="56bc3-119">動作</span><span class="sxs-lookup"><span data-stu-id="56bc3-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="56bc3-120">**名稱**</span><span class="sxs-lookup"><span data-stu-id="56bc3-120">**Name**</span></span>|<span data-ttu-id="56bc3-121">輸入連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="56bc3-121">Type the name of the port.</span></span>|  
    |<span data-ttu-id="56bc3-122">**無驗證**</span><span class="sxs-lookup"><span data-stu-id="56bc3-122">**No authentication**</span></span>|<span data-ttu-id="56bc3-123">按一下此選項以停用驗證。</span><span class="sxs-lookup"><span data-stu-id="56bc3-123">Click this option to disable authentication.</span></span> <span data-ttu-id="56bc3-124">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="56bc3-124">This is the default.</span></span>|  
    |<span data-ttu-id="56bc3-125">**驗證失敗時捨棄訊息**</span><span class="sxs-lookup"><span data-stu-id="56bc3-125">**Drop messages if authentication fails**</span></span>|<span data-ttu-id="56bc3-126">按一下此選項以啟用驗證，但會捨棄未驗證的訊息</span><span class="sxs-lookup"><span data-stu-id="56bc3-126">Click this option to enable authentication but to drop unauthenticated messages.</span></span>|  
    |<span data-ttu-id="56bc3-127">**驗證失敗時保留訊息**</span><span class="sxs-lookup"><span data-stu-id="56bc3-127">**Keep messages if authentication fails**</span></span>|<span data-ttu-id="56bc3-128">按一下此選項以啟用驗證，並保留未驗證的訊息。</span><span class="sxs-lookup"><span data-stu-id="56bc3-128">Click this option to enable authentication and keep unauthenticated messages.</span></span>|  
    |<span data-ttu-id="56bc3-129">**啟用失敗訊息的路由**</span><span class="sxs-lookup"><span data-stu-id="56bc3-129">**Enable routing for failed messages**</span></span>|<span data-ttu-id="56bc3-130">選取此核取方塊以嘗試將處理失敗的任何訊息路由至訂閱應用程式 (例如另一個接收埠或協調流程排程)。</span><span class="sxs-lookup"><span data-stu-id="56bc3-130">Select this check box to attempt to route any message that fails processing to a subscribing application (such as another receive port or orchestration schedule).</span></span> <span data-ttu-id="56bc3-131">清除核取方塊以擱置失敗的訊息，並產生負值通知 (NACK)。</span><span class="sxs-lookup"><span data-stu-id="56bc3-131">Clear the check box to suspend failed messages and generate a negative acknowledgment (NACK).</span></span> <span data-ttu-id="56bc3-132">預設值為清除核取方塊。</span><span class="sxs-lookup"><span data-stu-id="56bc3-132">The default value is cleared.</span></span> <span data-ttu-id="56bc3-133">如需詳細資訊，請參閱[如何啟用接收埠的失敗訊息路由](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="56bc3-133">For more information, see [How to Enable Routing for Failed Messages for a Receive Port](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md).</span></span>|  
  
5.  <span data-ttu-id="56bc3-134">在左窗格中，按一下 **接收位置**，並建立新接收位置，此接收埠。</span><span class="sxs-lookup"><span data-stu-id="56bc3-134">In the left pane, click **Receive Locations**, and create a new receive location for this receive port.</span></span> <span data-ttu-id="56bc3-135">如需指示，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="56bc3-135">For instructions, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span>  
  
6.  <span data-ttu-id="56bc3-136">在左窗格中，按一下 **輸入對應**，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="56bc3-136">In the left pane, click **Inbound Maps**, and do the following:</span></span>  
  
    |<span data-ttu-id="56bc3-137">使用</span><span class="sxs-lookup"><span data-stu-id="56bc3-137">Use this</span></span>|<span data-ttu-id="56bc3-138">動作</span><span class="sxs-lookup"><span data-stu-id="56bc3-138">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="56bc3-139">**來源文件**</span><span class="sxs-lookup"><span data-stu-id="56bc3-139">**Source Document**</span></span>|<span data-ttu-id="56bc3-140">從下拉式清單選取要與此連接埠一起使用的來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="56bc3-140">From the drop-down list, select the source schema to use with this port.</span></span>|  
    |<span data-ttu-id="56bc3-141">**對應**</span><span class="sxs-lookup"><span data-stu-id="56bc3-141">**Map**</span></span>|<span data-ttu-id="56bc3-142">從下拉式清單選取您要與此連接埠產生關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="56bc3-142">From the drop-down list, select the map you want to associate with this port.</span></span>|  
    |<span data-ttu-id="56bc3-143">**目標文件**</span><span class="sxs-lookup"><span data-stu-id="56bc3-143">**Target Document**</span></span>|<span data-ttu-id="56bc3-144">從下拉式清單選取要與此連接埠一起使用的目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="56bc3-144">From the drop-down list, select the destination schema to use with this port.</span></span>|  
  
7.  <span data-ttu-id="56bc3-145">如果您要建立要求-回應接收埠，然後在左窗格中，按一下**輸出對應**，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="56bc3-145">If you are creating a request-response receive port, then in the left pane, click **Outbound Maps**, and do the following:</span></span>  
  
    |<span data-ttu-id="56bc3-146">使用</span><span class="sxs-lookup"><span data-stu-id="56bc3-146">Use this</span></span>|<span data-ttu-id="56bc3-147">動作</span><span class="sxs-lookup"><span data-stu-id="56bc3-147">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="56bc3-148">**來源文件**</span><span class="sxs-lookup"><span data-stu-id="56bc3-148">**Source Document**</span></span>|<span data-ttu-id="56bc3-149">從下拉式清單選取要與此連接埠一起使用的來源結構描述。</span><span class="sxs-lookup"><span data-stu-id="56bc3-149">From the drop-down list, select the source schema to use with this port.</span></span>|  
    |<span data-ttu-id="56bc3-150">**對應**</span><span class="sxs-lookup"><span data-stu-id="56bc3-150">**Map**</span></span>|<span data-ttu-id="56bc3-151">從下拉式清單選取您要與此連接埠產生關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="56bc3-151">From the drop-down list, select the map you want to associate with this port.</span></span>|  
    |<span data-ttu-id="56bc3-152">**目標文件**</span><span class="sxs-lookup"><span data-stu-id="56bc3-152">**Target Document**</span></span>|<span data-ttu-id="56bc3-153">從下拉式清單選取要與此連接埠一起使用的目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="56bc3-153">From the drop-down list, select the destination schema to use with this port.</span></span>|  
  
8.  <span data-ttu-id="56bc3-154">完成設定接收埠，請按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="56bc3-154">When finished configuring the receive port, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56bc3-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56bc3-155">See Also</span></span>  
 [<span data-ttu-id="56bc3-156">管理接收埠</span><span class="sxs-lookup"><span data-stu-id="56bc3-156">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)