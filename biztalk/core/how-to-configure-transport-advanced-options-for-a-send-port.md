---
title: 如何設定傳送埠的傳輸進階選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, transport options [send ports]
- configuring, send ports
- send ports, transport options
- managing [send ports], configuring
- managing [send ports], transport options
ms.assetid: b0033e09-3c18-4e53-a470-e12978e61ba1
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aada2fa4f32e66c88f295e96bd71a9330cfb988
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023876"
---
# <a name="how-to-configure-transport-advanced-options-for-a-send-port"></a><span data-ttu-id="193c3-102">如何設定傳送埠的傳輸進階選項</span><span class="sxs-lookup"><span data-stu-id="193c3-102">How to Configure Transport Advanced Options for a Send Port</span></span>
<span data-ttu-id="193c3-103">您可以使用 BizTalk Server 管理主控台來設定傳送埠的傳輸進階選項。</span><span class="sxs-lookup"><span data-stu-id="193c3-103">Use the BizTalk Server Administration console to configure transport advanced options for a send port.</span></span> <span data-ttu-id="193c3-104">這些選項可決定傳送埠如何處理訊息，例如訊息失敗時重試傳送訊息的次數，以及該連接埠的服務窗口排程。</span><span class="sxs-lookup"><span data-stu-id="193c3-104">These options determine how messages are handled by the send port, such as the number of times to retry sending messages on message failure and the service window schedule for the port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="193c3-105">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您可以啟用排序的傳遞的動態傳送埠，根據配接器類型而定。</span><span class="sxs-lookup"><span data-stu-id="193c3-105">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can enable ordered delivery for dynamic send ports, depending on the adapter type.</span></span> <span data-ttu-id="193c3-106">此選項只適用於配接器類型排序的傳遞保證靜態傳送埠，例如 File 配接器或 FTP 配接器的位置。</span><span class="sxs-lookup"><span data-stu-id="193c3-106">This option is only available for the adapter types where ordered delivery is guaranteed for static send ports, such as the File adapter, or the FTP adapter.</span></span>
> 
> <span data-ttu-id="193c3-107">請考慮六個訊息： M1、 M2，M3、 M4、 M5 和 M6。</span><span class="sxs-lookup"><span data-stu-id="193c3-107">Consider six messages: M1, M2, M3, M4, M5, and M6.</span></span> <span data-ttu-id="193c3-108">M1、 M3、 M5 是為了檔案位置。</span><span class="sxs-lookup"><span data-stu-id="193c3-108">M1, M3, M5 are meant for a file location.</span></span> <span data-ttu-id="193c3-109">M2、 M4 和 M6 是適用於 FTP。</span><span class="sxs-lookup"><span data-stu-id="193c3-109">M2, M4, and M6 are meant for FTP.</span></span> <span data-ttu-id="193c3-110">排序的傳遞動態傳送埠可確保已排序 M1、 M3 和 M5;與 M2、 M4 和 M6 分別排序。</span><span class="sxs-lookup"><span data-stu-id="193c3-110">The ordered delivery dynamic send port makes sure that M1, M3, and M5 are ordered; and M2, M4, and M6 are ordered respectively.</span></span> 
> 
> <span data-ttu-id="193c3-111">對於不支援排序的傳遞這些配接器類型，目前沒有任何可用來設定動態傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="193c3-111">For those adapter types that don't support ordered delivery, there aren't any dynamic send port properties available to configure.</span></span> <span data-ttu-id="193c3-112">在執行階段，會自動決定其傳輸選項。</span><span class="sxs-lookup"><span data-stu-id="193c3-112">Their transport options are automatically determined at run time.</span></span>  
> 
> <span data-ttu-id="193c3-113">**適用於舊版的 BizTalk** ，使用動態連接埠，沒有任何設定，因為傳輸選項會自動決定在執行階段可用的屬性。</span><span class="sxs-lookup"><span data-stu-id="193c3-113">**For previous BizTalk versions** that use dynamic ports, there aren't any properties available to configure because the transport options are automatically determined at run time.</span></span>

  
## <a name="prerequisites"></a><span data-ttu-id="193c3-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="193c3-114">Prerequisites</span></span>  
 <span data-ttu-id="193c3-115">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="193c3-115">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="193c3-116">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="193c3-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="controlling-send-port-priority"></a><span data-ttu-id="193c3-117">控制傳送埠優先順序</span><span class="sxs-lookup"><span data-stu-id="193c3-117">Controlling Send Port Priority</span></span>  
 <span data-ttu-id="193c3-118">[傳輸進階選項] 的 [優先順序] 設定可控制訊息從 MessageoBox 移除的順序。</span><span class="sxs-lookup"><span data-stu-id="193c3-118">The Priority setting of the Transport Advanced Options controls the order in which messages are removed from the message box.</span></span> <span data-ttu-id="193c3-119">具有較高優先順序的連接埠會比具有較低優先順序的連接埠更早處理，使較高優先順序的連接埠相對於單一主控件中的其他傳送埠來的重要。</span><span class="sxs-lookup"><span data-stu-id="193c3-119">Ports with a higher priority will be processed earlier than ports with a lower priority making the higher priority ports more important relative to other send ports within a single host.</span></span>  
  
 <span data-ttu-id="193c3-120">優先順序在對某些要求類型需要低回應時間的實例中相當有用。</span><span class="sxs-lookup"><span data-stu-id="193c3-120">Priority is useful in scenarios requiring low response times for certain types of requests.</span></span> <span data-ttu-id="193c3-121">例如，如果有多個連接埠連接到不同的系統，以處理一般要求及互動式要求時。</span><span class="sxs-lookup"><span data-stu-id="193c3-121">For example, if there are multiple send ports that connect to different systems for processing normal requests and interactive requests.</span></span> <span data-ttu-id="193c3-122">互動式要求需要低回應時間，所有當互動式要求送出後，您可能想要盡快確認此要求已處理完成。</span><span class="sxs-lookup"><span data-stu-id="193c3-122">The interactive requests require a low response time, so when an interactive request is submitted, you want to ensure it is processed as soon as possible.</span></span>  
  
 <span data-ttu-id="193c3-123">BizTalk Server 不會嘗試公平處理 MessageBox 中具有不同優先順序的訊息。</span><span class="sxs-lookup"><span data-stu-id="193c3-123">BizTalk Server does not attempt to be fair in the processing of messages with different priorities in the message box.</span></span> <span data-ttu-id="193c3-124">如果在處理開始時，MessageBox 中具有兩個不同優先順序的項目數量相等，較低優先順序的項目就會在所有高優先順序項目處理完之後才會進行處理。</span><span class="sxs-lookup"><span data-stu-id="193c3-124">If there are equal numbers of items with two different priorities in the message box when processing begins, the lower priority items will be processed only after all high priority items have been processed.</span></span> <span data-ttu-id="193c3-125">如果高優先順序的數量很大，具有較低優先順序的項目可能永遠都不會進行處理。</span><span class="sxs-lookup"><span data-stu-id="193c3-125">If the volume of high priority items is great, it is possible that items with a lower priority will never be processed.</span></span> <span data-ttu-id="193c3-126">換句話說，較低優先順序的項目將發生嚴重缺乏的情況。</span><span class="sxs-lookup"><span data-stu-id="193c3-126">In other words, the lower priority items will experience starvation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="193c3-127">若要將訊息嚴重缺乏的風險降到最低，請在實際負載下徹底測試您的應用程式，確定所有的訊息都已處理。</span><span class="sxs-lookup"><span data-stu-id="193c3-127">To minimize the risk of message starvation, thoroughly test your application under realistic loads to ensure all messages are processed.</span></span> <span data-ttu-id="193c3-128">未測試您的方案可能造成未處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="193c3-128">Failure to test your solution may result in unprocessed messages.</span></span>  
  
 <span data-ttu-id="193c3-129">BizTalk Server 會在內部為每個訂閱指派優先順序。</span><span class="sxs-lookup"><span data-stu-id="193c3-129">Internally, BizTalk Server assigns a priority to every subscription.</span></span> <span data-ttu-id="193c3-130">優先順序可以從 1 (最高優先順序) 到 10 (最低優先順序) 的任何數字。</span><span class="sxs-lookup"><span data-stu-id="193c3-130">Priority can be any number from 1 (highest priority) to 10 (lowest priority).</span></span> <span data-ttu-id="193c3-131">因為啟動訂閱的預設優先順序為 7，相互關聯訂閱的預設優先順序為 5，所以相互關聯訊息將比啟動訂閱更早傳遞。</span><span class="sxs-lookup"><span data-stu-id="193c3-131">Because the default priority is 7 for activating subscriptions and 5 for correlating subscriptions, correlating messages will be delivered earlier than activating subscriptions.</span></span>  
  
## <a name="configure-the-transport-options"></a><span data-ttu-id="193c3-132">設定傳輸選項</span><span class="sxs-lookup"><span data-stu-id="193c3-132">Configure the transport options</span></span> 
  
1.  <span data-ttu-id="193c3-133">開啟 [BizTalk Server 管理] 。</span><span class="sxs-lookup"><span data-stu-id="193c3-133">Open **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="193c3-134">展開 BizTalk 群組，然後再展開 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="193c3-134">Expand the BizTalk group, and then expand your BizTalk application.</span></span>  
  
3.  <span data-ttu-id="193c3-135">選取 **傳送埠**，以滑鼠右鍵按一下傳送埠，以設定，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="193c3-135">Select **Send Ports**, right-click the send port to configure, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="193c3-136">在左窗格中，選取**傳輸進階選項**。</span><span class="sxs-lookup"><span data-stu-id="193c3-136">In the left pane, select **Transport Advanced Options**.</span></span>  
  
5.  <span data-ttu-id="193c3-137">下表中所述，設定傳輸進階選項，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="193c3-137">Configure the transport options as described in the following table, and then select **OK**.</span></span>  <span data-ttu-id="193c3-138">只有部分的下列屬性可供使用動態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="193c3-138">Only some of the following properties are available for dynamic send ports.</span></span>
  
    |<span data-ttu-id="193c3-139">使用</span><span class="sxs-lookup"><span data-stu-id="193c3-139">Use this</span></span>|<span data-ttu-id="193c3-140">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="193c3-140">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="193c3-141">**重試計數**</span><span class="sxs-lookup"><span data-stu-id="193c3-141">**Retry count**</span></span>|<span data-ttu-id="193c3-142">指定傳送埠在訊息失敗時重新傳送訊息的次數。</span><span class="sxs-lookup"><span data-stu-id="193c3-142">Specify the number of times for the send port to resend a message on message failure.</span></span> <span data-ttu-id="193c3-143">預設值為 3；允許的範圍由 0 至 1,000。</span><span class="sxs-lookup"><span data-stu-id="193c3-143">The default is 3; the allowed range is from 0 through 1,000.</span></span>|  
    |<span data-ttu-id="193c3-144">**重試間隔**</span><span class="sxs-lookup"><span data-stu-id="193c3-144">**Retry interval**</span></span>|<span data-ttu-id="193c3-145">以分鐘為單位指定重新傳送訊息嘗試之間的間隔。</span><span class="sxs-lookup"><span data-stu-id="193c3-145">Specify the interval in minutes between message resend attempts.</span></span> <span data-ttu-id="193c3-146">預設值是 5;允許的範圍是從 0 到 525,600。</span><span class="sxs-lookup"><span data-stu-id="193c3-146">The default is 5; the allowed range is from 0 through 525,600.</span></span>|  
    |<span data-ttu-id="193c3-147">**優先權**</span><span class="sxs-lookup"><span data-stu-id="193c3-147">**Priority**</span></span>|<span data-ttu-id="193c3-148">設定重新傳送嘗試的優先順序。</span><span class="sxs-lookup"><span data-stu-id="193c3-148">Set the priority of the resend attempt.</span></span>|  
    |<span data-ttu-id="193c3-149">**排序的傳遞**</span><span class="sxs-lookup"><span data-stu-id="193c3-149">**Ordered delivery**</span></span>|<span data-ttu-id="193c3-150">選取此核取方塊，依照接收順序來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="193c3-150">Select this check box to send messages in order of receipt.</span></span>|  
    |<span data-ttu-id="193c3-151">**停止傳送後續訊息目前訊息失敗**</span><span class="sxs-lookup"><span data-stu-id="193c3-151">**Stop sending subsequent messages on current message failure**</span></span>|<span data-ttu-id="193c3-152">選取此核取方塊以停止傳送跟隨在失敗訊息之後的後續訊息。</span><span class="sxs-lookup"><span data-stu-id="193c3-152">Select this check box to stop sending subsequent messages that follow a failed message.</span></span> <span data-ttu-id="193c3-153">此功能時才可使用**排序的傳遞**選項。</span><span class="sxs-lookup"><span data-stu-id="193c3-153">This option is available only when the **Ordered delivery** option is selected.</span></span>|  
    |<span data-ttu-id="193c3-154">**啟用失敗訊息的路由**</span><span class="sxs-lookup"><span data-stu-id="193c3-154">**Enable routing for failed messages**</span></span>|<span data-ttu-id="193c3-155">選取此選項以啟用失敗訊息的路由。</span><span class="sxs-lookup"><span data-stu-id="193c3-155">Select this option to enable routing for failed messages.</span></span>|  
    |<span data-ttu-id="193c3-156">**啟用服務窗口**</span><span class="sxs-lookup"><span data-stu-id="193c3-156">**Enable service window**</span></span>|<span data-ttu-id="193c3-157">選取此選項，以指定開始時間及停止時間的方式來指定傳送埠每日運作的時段。</span><span class="sxs-lookup"><span data-stu-id="193c3-157">Select this option to specify the time period each day during which the send port will be operational by specifying a start time and stop time.</span></span>|  
    |<span data-ttu-id="193c3-158">**開始時間**</span><span class="sxs-lookup"><span data-stu-id="193c3-158">**Start time**</span></span>|<span data-ttu-id="193c3-159">指定傳送埠每日開始傳送訊息的時間。</span><span class="sxs-lookup"><span data-stu-id="193c3-159">Specify the time each day at which the send port starts sending messages.</span></span> <span data-ttu-id="193c3-160">此功能時才可使用**啟用服務窗口**選項。</span><span class="sxs-lookup"><span data-stu-id="193c3-160">This option is available only when the **Enable service window** option is selected.</span></span>|  
    |<span data-ttu-id="193c3-161">**停止時間**</span><span class="sxs-lookup"><span data-stu-id="193c3-161">**Stop time**</span></span>|<span data-ttu-id="193c3-162">指定傳送埠每日停止傳送訊息的時間。</span><span class="sxs-lookup"><span data-stu-id="193c3-162">Specify the time each day at which the send port stops sending messages.</span></span> <span data-ttu-id="193c3-163">此功能時才可使用**啟用服務窗口**選項。</span><span class="sxs-lookup"><span data-stu-id="193c3-163">This option is available only when the **Enable service window** option is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="193c3-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="193c3-164">See Also</span></span>  
[<span data-ttu-id="193c3-165">訊息的排序傳遞</span><span class="sxs-lookup"><span data-stu-id="193c3-165">Ordered Delivery of Messages</span></span>](../core/ordered-delivery-of-messages.md)  
 [<span data-ttu-id="193c3-166">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="193c3-166">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)