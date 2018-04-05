---
title: 如何建立傳送 Port2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.procedure.createsendport
helpviewer_keywords:
- managing [send ports], creating
- creating, send ports
- send ports, creating
ms.assetid: 7f0d07b8-1ac5-4032-bb08-2f7e05185f86
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 796ba5da53257d0f198e4b8bf13ee81835efcf4e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-send-port"></a><span data-ttu-id="fce78-102">如何建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="fce78-102">How to Create a Send Port</span></span>
<span data-ttu-id="fce78-103">本主題描述如何使用 BizTalk Server 管理主控台來建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="fce78-103">This topic describes how to use the BizTalk Server Administration console to create a send port.</span></span> <span data-ttu-id="fce78-104">建立傳送埠時，您必須選取要建立的傳送埠類型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="fce78-104">When creating a send port, you must select the type of send port to create, as follows:</span></span>  
  
-   <span data-ttu-id="fce78-105">靜態單向 — 僅供傳送的連接埠。</span><span class="sxs-lookup"><span data-stu-id="fce78-105">Static one-way — a send-only port.</span></span>  
  
-   <span data-ttu-id="fce78-106">靜態請求-回應 — 等候目的地回覆的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="fce78-106">Static solicit-response — a send port that waits for a reply from the destination.</span></span>  
  
-   <span data-ttu-id="fce78-107">動態單向 — 僅供傳送的連接埠，可根據訊息屬性於執行階段繫結至通訊協定和位置。</span><span class="sxs-lookup"><span data-stu-id="fce78-107">Dynamic one-way — a send-only port that can be bound to a protocol and location at runtime based on message properties.</span></span>  
  
-   <span data-ttu-id="fce78-108">動態請求-回應 — 等候回覆的傳送埠，可根據訊息屬性於執行階段繫結至通訊協定和位置。</span><span class="sxs-lookup"><span data-stu-id="fce78-108">Dynamic solicit-response — a send port that waits for a reply and can be bound to a protocol and location at runtime based on message properties.</span></span>  
  
 <span data-ttu-id="fce78-109">建立傳送埠之後，您可以執行下列其他步驟來完成設定：</span><span class="sxs-lookup"><span data-stu-id="fce78-109">After you create a send port, you can perform the following additional steps to complete the configuration:</span></span>  
  
-   <span data-ttu-id="fce78-110">設定進階傳輸選項，例如重試傳送訊息的訊息失敗，以及連接埠的服務視窗排程中所述的次數[如何設定傳輸進階選項的傳送埠](../core/how-to-configure-transport-advanced-options-for-a-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="fce78-110">Configure advanced transport options, such as the number of times to retry sending messages on message failure and the service window schedule for the port, as described in [How to Configure Transport Advanced Options for a Send Port](../core/how-to-configure-transport-advanced-options-for-a-send-port.md).</span></span>  
  
-   <span data-ttu-id="fce78-111">設定備份傳輸，萬一主要傳輸無法正常運作，述[如何傳送埠的設定備份傳輸選項](../core/how-to-configure-backup-transport-options-for-a-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="fce78-111">Configure a backup transport, in the event the primary transport fails to function, as described in [How to Configure Backup Transport Options for a Send Port](../core/how-to-configure-backup-transport-options-for-a-send-port.md).</span></span>  
  
-   <span data-ttu-id="fce78-112">設定篩選，以判斷哪些訊息路由至此傳送埠在訊息方塊中所述[如何設定傳送埠的篩選](../core/how-to-configure-filters-for-a-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="fce78-112">Configure filters to determine which messages are routed to this send port from the message box, as described in [How to Configure Filters for a Send Port](../core/how-to-configure-filters-for-a-send-port.md).</span></span>  
  
-   <span data-ttu-id="fce78-113">將安全性憑證指派給要加密或簽章由傳送埠，處理的文件中所述的傳送埠[如何指派憑證給傳送埠](../core/how-to-assign-a-certificate-to-a-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="fce78-113">Assign a security certificate to the send port to encrypt or sign documents handled by the send port, as described in [How to Assign a Certificate to a Send Port](../core/how-to-assign-a-certificate-to-a-send-port.md).</span></span>  
  
-   <span data-ttu-id="fce78-114">設定傳送埠，所處理的訊息追蹤選項中所述[如何設定傳送埠的追蹤](../core/how-to-configure-tracking-for-a-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="fce78-114">Configure tracking options for messages handled by the send port, as described in [How to Configure Tracking for a Send Port](../core/how-to-configure-tracking-for-a-send-port.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fce78-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="fce78-115">Prerequisites</span></span>  
 <span data-ttu-id="fce78-116">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="fce78-116">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="fce78-117">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="fce78-117">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span> <span data-ttu-id="fce78-118">此外，您必須擁有「企業單一登入」(SSO) 資料庫上的 SSO 分支機構系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="fce78-118">In addition, you need to have SSO affiliate administrator permissions on the Enterprise Single Sign-On (SSO) database.</span></span> <span data-ttu-id="fce78-119">如需詳細資訊，請參閱[SSO 使用者群組](../core/sso-user-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="fce78-119">For more information, see [SSO User Groups](../core/sso-user-groups.md).</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="fce78-120">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="fce78-120">To create a send port</span></span>  
  
1.  <span data-ttu-id="fce78-121">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="fce78-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fce78-122">在主控台樹狀目錄中，展開您要建立傳送埠的 BizTalk 群組和 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fce78-122">In the console tree, expand the BizTalk group and the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="fce78-123">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 建立的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="fce78-123">Right-click **Send Ports**, point to **New**, and then click the type of port to create.</span></span>  
  
4.  <span data-ttu-id="fce78-124">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fce78-124">In the **Send Ports Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="fce78-125">使用</span><span class="sxs-lookup"><span data-stu-id="fce78-125">Use this</span></span>|<span data-ttu-id="fce78-126">動作</span><span class="sxs-lookup"><span data-stu-id="fce78-126">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fce78-127">**名稱**</span><span class="sxs-lookup"><span data-stu-id="fce78-127">**Name**</span></span>|<span data-ttu-id="fce78-128">輸入新傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="fce78-128">Type the name of the new send port.</span></span> <span data-ttu-id="fce78-129">這個名稱必須是 BizTalk 群組中唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="fce78-129">This name must be unique in the BizTalk group.</span></span>|  
    |<span data-ttu-id="fce78-130">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="fce78-130">**Transport Type**</span></span>|<span data-ttu-id="fce78-131">從下拉式清單選取適當的傳輸類型或傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="fce78-131">From the drop-down list, select the appropriate transport type, or transport protocol.</span></span> <span data-ttu-id="fce78-132">若連接埠是請求-回應連接埠，則清單中只會顯示支援請求-回應的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="fce78-132">If the port is a solicit-response port, only transport types that support solicit-response are available in the list.</span></span> <span data-ttu-id="fce78-133">此屬性只會針對靜態連接埠而顯示。</span><span class="sxs-lookup"><span data-stu-id="fce78-133">This property is visible only for static ports.</span></span>|  
    |<span data-ttu-id="fce78-134">**設定**</span><span class="sxs-lookup"><span data-stu-id="fce78-134">**Configure**</span></span>|<span data-ttu-id="fce78-135">選取傳輸類型之後，請按一下**設定**顯示**傳輸屬性**對話方塊中，提供傳輸特定組態選項。</span><span class="sxs-lookup"><span data-stu-id="fce78-135">After you select the transport type, click **Configure** to display the **Transport Properties** dialog box, which provides transport-specific configuration options.</span></span> <span data-ttu-id="fce78-136">此屬性只會針對靜態連接埠而顯示。</span><span class="sxs-lookup"><span data-stu-id="fce78-136">This property is visible only for static ports.</span></span> <span data-ttu-id="fce78-137">按一下**協助**在對話方塊中，如需設定指示。</span><span class="sxs-lookup"><span data-stu-id="fce78-137">Click **Help** in the dialog box for configuration instructions.</span></span>|  
    |<span data-ttu-id="fce78-138">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="fce78-138">**Send handler**</span></span>|<span data-ttu-id="fce78-139">從下拉式清單選取傳送配接器執行所在的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="fce78-139">From the drop-down list, select the host instance on which the send adapter is running.</span></span> <span data-ttu-id="fce78-140">此屬性只會針對靜態連接埠而顯示。</span><span class="sxs-lookup"><span data-stu-id="fce78-140">This property is visible only for static ports.</span></span>|  
    |<span data-ttu-id="fce78-141">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="fce78-141">**Send pipeline**</span></span>|<span data-ttu-id="fce78-142">從下拉式清單選取管線以處理透過此連接埠傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="fce78-142">From the drop-down list, select the pipeline that processes the messages sent through this port.</span></span> <span data-ttu-id="fce78-143">您選取管線後，您可以按一下相鄰的省略符號 (**...**) 按鈕，即可顯示**設定管線**對話方塊，讓您設定此特定的連接埠的每個執行個體管線屬性。</span><span class="sxs-lookup"><span data-stu-id="fce78-143">After you select the pipeline, you can click the adjacent ellipsis (**…**) button to display the **Configure Pipeline** dialog box, where you configure per-instance pipeline properties for this specific port.</span></span> <span data-ttu-id="fce78-144">按一下**協助**在對話方塊中，如需設定指示。</span><span class="sxs-lookup"><span data-stu-id="fce78-144">Click **Help** in the dialog box for configuration instructions.</span></span>|  
    |<span data-ttu-id="fce78-145">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="fce78-145">**Receive pipeline**</span></span>|<span data-ttu-id="fce78-146">從下拉式清單選取管線以處理透過此連接埠接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="fce78-146">From the drop-down list, select the pipeline that processes messages received through this port.</span></span> <span data-ttu-id="fce78-147">透過此管線收到的訊息回應也將會透過此管線傳送。</span><span class="sxs-lookup"><span data-stu-id="fce78-147">Responses to messages received through this pipeline will also be sent through this pipeline.</span></span> <span data-ttu-id="fce78-148">您選取管線後，您可以按一下相鄰的省略符號 (**...**) 按鈕，即可顯示**設定管線**對話方塊，讓您設定此特定的連接埠的每個執行個體管線屬性。</span><span class="sxs-lookup"><span data-stu-id="fce78-148">After you select the pipeline, you can click the adjacent ellipsis (**…**) button to display the **Configure Pipeline** dialog box, where you configure per-instance pipeline properties for this specific port.</span></span> <span data-ttu-id="fce78-149">此屬性只會針對請求-回應連接埠而顯示。</span><span class="sxs-lookup"><span data-stu-id="fce78-149">This property is visible only for Solicit-Response ports.</span></span>|  
  
5.  <span data-ttu-id="fce78-150">如果您正在建立請求-回應傳送埠，在左窗格中，按一下**輸入對應**並執行下列動作，視需要重複如果您想要加入多個對應：</span><span class="sxs-lookup"><span data-stu-id="fce78-150">If you are creating a solicit-response send port, in the left pane, click **Inbound Maps** and do the following, repeating as necessary if you want to add multiple maps:</span></span>  
  
    |<span data-ttu-id="fce78-151">使用</span><span class="sxs-lookup"><span data-stu-id="fce78-151">Use this</span></span>|<span data-ttu-id="fce78-152">動作</span><span class="sxs-lookup"><span data-stu-id="fce78-152">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fce78-153">**來源文件**</span><span class="sxs-lookup"><span data-stu-id="fce78-153">**Source Document**</span></span>|<span data-ttu-id="fce78-154">從下拉式清單選取輸入對應的來源文件。</span><span class="sxs-lookup"><span data-stu-id="fce78-154">From the drop-down list, select the source document for the inbound map.</span></span> <span data-ttu-id="fce78-155">傳送埠可以有一個以上的對應，但是每個對應只能有唯一的來源文件。</span><span class="sxs-lookup"><span data-stu-id="fce78-155">A send port may have more than one map, but each map should have a unique source document.</span></span>|  
    |<span data-ttu-id="fce78-156">**對應**</span><span class="sxs-lookup"><span data-stu-id="fce78-156">**Map**</span></span>|<span data-ttu-id="fce78-157">從下拉式清單選取與來源及目標文件關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="fce78-157">From the drop-down list, select the map to associate with the source and target documents.</span></span>|  
    |<span data-ttu-id="fce78-158">**目標文件**</span><span class="sxs-lookup"><span data-stu-id="fce78-158">**Target Document**</span></span>|<span data-ttu-id="fce78-159">從下拉式清單選取輸入對應的目標文件。</span><span class="sxs-lookup"><span data-stu-id="fce78-159">From the drop-down list, select the target document for the inbound map.</span></span>|  
  
6.  <span data-ttu-id="fce78-160">在左窗格中，按一下 **輸出對應**並執行下列動作，視需要重複如果您想要加入多個對應：</span><span class="sxs-lookup"><span data-stu-id="fce78-160">In the left pane, click **Outbound Maps** and do the following, repeating as necessary if you want to add multiple maps:</span></span>  
  
    |<span data-ttu-id="fce78-161">使用</span><span class="sxs-lookup"><span data-stu-id="fce78-161">Use this</span></span>|<span data-ttu-id="fce78-162">動作</span><span class="sxs-lookup"><span data-stu-id="fce78-162">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fce78-163">**來源文件**</span><span class="sxs-lookup"><span data-stu-id="fce78-163">**Source Document**</span></span>|<span data-ttu-id="fce78-164">從下拉式清單選取輸出對應的來源文件。</span><span class="sxs-lookup"><span data-stu-id="fce78-164">From the drop-down list, select the source document for the outbound map.</span></span>|  
    |<span data-ttu-id="fce78-165">**對應**</span><span class="sxs-lookup"><span data-stu-id="fce78-165">**Map**</span></span>|<span data-ttu-id="fce78-166">從下拉式清單選取與來源及目標文件關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="fce78-166">From the drop-down list, select the map to associate with the source and target documents.</span></span>|  
    |<span data-ttu-id="fce78-167">**目標文件**</span><span class="sxs-lookup"><span data-stu-id="fce78-167">**Target Document**</span></span>|<span data-ttu-id="fce78-168">從下拉式清單選取輸出對應的目標文件。</span><span class="sxs-lookup"><span data-stu-id="fce78-168">From the drop-down list, select the target document for the outbound map.</span></span>|  
  
7.  <span data-ttu-id="fce78-169">完成設定傳送埠，請按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fce78-169">When finished configuring the send port, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce78-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fce78-170">See Also</span></span>  
 <span data-ttu-id="fce78-171">[建立和設定傳送埠](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="fce78-171">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 <span data-ttu-id="fce78-172">[管理管線](../core/managing-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="fce78-172">[Managing Pipelines](../core/managing-pipelines.md) </span></span>  
 [<span data-ttu-id="fce78-173">管理對應</span><span class="sxs-lookup"><span data-stu-id="fce78-173">Managing Maps</span></span>](../core/managing-maps.md)