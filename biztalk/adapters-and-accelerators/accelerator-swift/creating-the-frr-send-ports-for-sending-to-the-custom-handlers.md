---
title: "建立 FRR 傳送埠以傳送到自訂處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
- FRR, creating send ports
ms.assetid: 036f1f97-17a2-4e02-a85a-a52739a48528
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7da5d51407bed1cca257e14cc4f548e8c991cf9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-send-ports-for-sending-to-the-custom-handlers"></a><span data-ttu-id="6f901-102">建立 FRR 傳送埠以傳送到自訂處理常式</span><span class="sxs-lookup"><span data-stu-id="6f901-102">Creating the FRR Send Ports for Sending to the Custom Handlers</span></span>
<span data-ttu-id="6f901-103">若要執行 FIN 回應重新調整，您需要建立的一連串的傳送埠，其中每個傳送訊息 （原始訊息或回應） 從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]處理的相互關聯的訊息的自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="6f901-103">To perform FIN Response Reconciliation, you need to create a series of send ports, each of which sends a message (original message or response) from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the custom handlers that process the correlated messages.</span></span>  
  
 <span data-ttu-id="6f901-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="6f901-104">**Summary**</span></span>  
  
 <span data-ttu-id="6f901-105">建立具有下列屬性和元件，每個的 BTS 的值來區分的一系列的傳送埠。在篩選中的作業：</span><span class="sxs-lookup"><span data-stu-id="6f901-105">Create a series of send ports with the following properties and components, each one distinguished by the value of BTS.Operation in the filter:</span></span>  
  
|<span data-ttu-id="6f901-106">屬性/元件</span><span class="sxs-lookup"><span data-stu-id="6f901-106">Property/Component</span></span>|<span data-ttu-id="6f901-107">設定</span><span class="sxs-lookup"><span data-stu-id="6f901-107">Setting</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="6f901-108">傳送埠</span><span class="sxs-lookup"><span data-stu-id="6f901-108">Send port</span></span>|<span data-ttu-id="6f901-109">靜態單向連接埠</span><span class="sxs-lookup"><span data-stu-id="6f901-109">Static one-way port</span></span>|  
|<span data-ttu-id="6f901-110">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="6f901-110">Transport type</span></span>|<span data-ttu-id="6f901-111">FILE</span><span class="sxs-lookup"><span data-stu-id="6f901-111">FILE</span></span>|  
|<span data-ttu-id="6f901-112">目的資料夾 (位址 URI)</span><span class="sxs-lookup"><span data-stu-id="6f901-112">Destination folder (Address URI)</span></span>|<span data-ttu-id="6f901-113">您想要將訊息傳送至資料夾</span><span class="sxs-lookup"><span data-stu-id="6f901-113">The folder that you want to send the message to</span></span>|  
|<span data-ttu-id="6f901-114">檔案名稱 (位址 URI)</span><span class="sxs-lookup"><span data-stu-id="6f901-114">File name (Address URI)</span></span>|<span data-ttu-id="6f901-115">%MessageID%.txt</span><span class="sxs-lookup"><span data-stu-id="6f901-115">%MessageID%.txt</span></span>|  
|<span data-ttu-id="6f901-116">傳送管線</span><span class="sxs-lookup"><span data-stu-id="6f901-116">Send pipeline</span></span>|[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="6f901-117">.BizTalk.DefaultPipelines。</span><span class="sxs-lookup"><span data-stu-id="6f901-117">.BizTalk.DefaultPipelines.</span></span> <span data-ttu-id="6f901-118">PassThruTransmit</span><span class="sxs-lookup"><span data-stu-id="6f901-118">PassThruTransmit</span></span>|  
|<span data-ttu-id="6f901-119">篩選</span><span class="sxs-lookup"><span data-stu-id="6f901-119">Filters</span></span>|<span data-ttu-id="6f901-120">下表所示</span><span class="sxs-lookup"><span data-stu-id="6f901-120">As shown in the tables below</span></span>|  
  
 <span data-ttu-id="6f901-121">BTS 的值來區分不同的訊息的傳送埠。傳送埠的篩選條件中的作業。</span><span class="sxs-lookup"><span data-stu-id="6f901-121">The send ports for the different messages are distinguished by the value of BTS.Operation in the send port's filter.</span></span>  
  
### <a name="to-add-frr-send-ports-for-sending-to-the-custom-handlers"></a><span data-ttu-id="6f901-122">若要加入 FRR 傳送埠以傳送到自訂處理常式</span><span class="sxs-lookup"><span data-stu-id="6f901-122">To add FRR send ports for sending to the custom handlers</span></span>  
  
1.  <span data-ttu-id="6f901-123">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態一個 waySend 埠**。</span><span class="sxs-lookup"><span data-stu-id="6f901-123">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-waySend Port**.</span></span>  
  
2.  <span data-ttu-id="6f901-124">在 [傳送埠屬性] 對話方塊中**名稱**方塊中，輸入傳送埠，例如 FRRCustomHandlersSendPort 的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f901-124">In the Send Port Properties dialog box, in the **Name** box, type a name for the send port, such as FRRCustomHandlersSendPort.</span></span>  
  
3.  <span data-ttu-id="6f901-125">如**類型**，選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="6f901-125">For **Type**, select **FILE**.</span></span>  
  
4.  <span data-ttu-id="6f901-126">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="6f901-126">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="6f901-127">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="6f901-127">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="6f901-128">在 [瀏覽資料夾] 對話方塊中，移至您想要從傳送訊息的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f901-128">In the Browse For Folder dialog box, move to the folder that you want to send messages from.</span></span> <span data-ttu-id="6f901-129">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6f901-129">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f901-130">如果此資料夾不存在，您可以建立使用**建立新資料夾**命令。</span><span class="sxs-lookup"><span data-stu-id="6f901-130">If this folder does not exist, you can create it using the **Make New Folder** command.</span></span>  
  
7.  <span data-ttu-id="6f901-131">在**檔案名稱**方塊中，輸入**%MessageID%.txt**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6f901-131">In the **File name** box, type **%MessageID%.txt**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f901-132">您可以建立不同的資料夾，每種類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="6f901-132">You can create a different folder for each type of message.</span></span>  
  
8.  <span data-ttu-id="6f901-133">在 傳送埠屬性 對話方塊的 傳送處理常式中，確認**BizTalkServerApplication**已選取。</span><span class="sxs-lookup"><span data-stu-id="6f901-133">In the Send Port Properties dialog box, for Send handler, verify that **BizTalkServerApplication** is selected.</span></span>  
  
9. <span data-ttu-id="6f901-134">如**傳送管線**，選取**PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="6f901-134">For **Send Pipeline**, select **PassThruTransmit**.</span></span>  
  
10. <span data-ttu-id="6f901-135">按一下**篩選**左的窗格中，然後執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6f901-135">Click **Filters** in the left pane, and then do the following:</span></span>  
  
    |<span data-ttu-id="6f901-136">使用</span><span class="sxs-lookup"><span data-stu-id="6f901-136">Use this</span></span>|<span data-ttu-id="6f901-137">動作</span><span class="sxs-lookup"><span data-stu-id="6f901-137">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6f901-138">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6f901-138">**Property**</span></span>|<span data-ttu-id="6f901-139">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**。</span><span class="sxs-lookup"><span data-stu-id="6f901-139">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.</span></span>|  
    |<span data-ttu-id="6f901-140">**運算子**</span><span class="sxs-lookup"><span data-stu-id="6f901-140">**Operator**</span></span>|<span data-ttu-id="6f901-141">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="6f901-141">Select **==**.</span></span>|  
    |<span data-ttu-id="6f901-142">**值**</span><span class="sxs-lookup"><span data-stu-id="6f901-142">**Value**</span></span>|<span data-ttu-id="6f901-143">型別**A4SWIFT_FrrService**。</span><span class="sxs-lookup"><span data-stu-id="6f901-143">Type **A4SWIFT_FrrService**.</span></span>|  
    |<span data-ttu-id="6f901-144">**群組**</span><span class="sxs-lookup"><span data-stu-id="6f901-144">**Group**</span></span>|<span data-ttu-id="6f901-145">**和**</span><span class="sxs-lookup"><span data-stu-id="6f901-145">**And**</span></span>|  
    |<span data-ttu-id="6f901-146">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6f901-146">**Property**</span></span>|<span data-ttu-id="6f901-147">選取**BTS。作業**。</span><span class="sxs-lookup"><span data-stu-id="6f901-147">Select **BTS.Operation**.</span></span>|  
    |<span data-ttu-id="6f901-148">**運算子**</span><span class="sxs-lookup"><span data-stu-id="6f901-148">**Operator**</span></span>|<span data-ttu-id="6f901-149">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="6f901-149">Select **==**.</span></span>|  
    |<span data-ttu-id="6f901-150">**值**</span><span class="sxs-lookup"><span data-stu-id="6f901-150">**Value**</span></span>|<span data-ttu-id="6f901-151">輸入 BTS 的其中一個。下表中的作業值。</span><span class="sxs-lookup"><span data-stu-id="6f901-151">Type one of the BTS.Operation values from the table below.</span></span>|  
  
     <span data-ttu-id="6f901-152">針對 BTS。作業中，輸入下列值之一：</span><span class="sxs-lookup"><span data-stu-id="6f901-152">For BTS.Operation, enter one of the following values:</span></span>  
  
    |<span data-ttu-id="6f901-153">訊息類型</span><span class="sxs-lookup"><span data-stu-id="6f901-153">Message type</span></span>|<span data-ttu-id="6f901-154">BTS。作業值</span><span class="sxs-lookup"><span data-stu-id="6f901-154">BTS.Operation value</span></span>|  
    |------------------|-------------------------|  
    |<span data-ttu-id="6f901-155">所有類別 0 到 9 SWIFT FIN 訊息類型</span><span class="sxs-lookup"><span data-stu-id="6f901-155">All Category 0 to 9 SWIFT FIN message types</span></span>|<span data-ttu-id="6f901-156">**A4SWIFT_FrrSendMTMsg**</span><span class="sxs-lookup"><span data-stu-id="6f901-156">**A4SWIFT_FrrSendMTMsg**</span></span>|  
    |<span data-ttu-id="6f901-157">MQ 系列取景位置調整/NAN (MQ Series 傳輸層級 ACK/NAK)</span><span class="sxs-lookup"><span data-stu-id="6f901-157">MQ Series PAN/NAN (MQ Series transport-level ACK/NAK)</span></span>|<span data-ttu-id="6f901-158">**A4SWIFT_FrrSendTransport**</span><span class="sxs-lookup"><span data-stu-id="6f901-158">**A4SWIFT_FrrSendTransport**</span></span>|  
    |<span data-ttu-id="6f901-159">MT010 （非傳遞警告）</span><span class="sxs-lookup"><span data-stu-id="6f901-159">MT010 (Non-Delivery Warning)</span></span>|<span data-ttu-id="6f901-160">**A4SWIFT_FrrSend010NDW**</span><span class="sxs-lookup"><span data-stu-id="6f901-160">**A4SWIFT_FrrSend010NDW**</span></span>|  
    |<span data-ttu-id="6f901-161">MT011 （傳遞通知）</span><span class="sxs-lookup"><span data-stu-id="6f901-161">MT011 (Delivery Notification)</span></span>|<span data-ttu-id="6f901-162">**A4SWIFT_FrrSend011Delivered**</span><span class="sxs-lookup"><span data-stu-id="6f901-162">**A4SWIFT_FrrSend011Delivered**</span></span>|  
    |<span data-ttu-id="6f901-163">MT012 （寄件者通知）</span><span class="sxs-lookup"><span data-stu-id="6f901-163">MT012 (Sender Notification)</span></span>|<span data-ttu-id="6f901-164">**A4SWIFT_FrrSend012SenderACK**</span><span class="sxs-lookup"><span data-stu-id="6f901-164">**A4SWIFT_FrrSend012SenderACK**</span></span>|  
    |<span data-ttu-id="6f901-165">MT015 （DNK 或延遲的 NAK）</span><span class="sxs-lookup"><span data-stu-id="6f901-165">MT015 (DNK, or Delayed NAK)</span></span>|<span data-ttu-id="6f901-166">**A4SWIFT_FrrSend015DNK**</span><span class="sxs-lookup"><span data-stu-id="6f901-166">**A4SWIFT_FrrSend015DNK**</span></span>|  
    |<span data-ttu-id="6f901-167">MT019 （中止通知）</span><span class="sxs-lookup"><span data-stu-id="6f901-167">MT019 (Abort Notification)</span></span>|<span data-ttu-id="6f901-168">**A4SWIFT_FrrSend019Abort**</span><span class="sxs-lookup"><span data-stu-id="6f901-168">**A4SWIFT_FrrSend019Abort**</span></span>|  
    |<span data-ttu-id="6f901-169">MTS21_FIN_ACKNAK 傳送 LT (ACK) 的 FIN 訊息 （通知</span><span class="sxs-lookup"><span data-stu-id="6f901-169">MTS21_FIN_ACKNAK (Acknowledgment of a FIN message sent by an LT (ACK)</span></span>|<span data-ttu-id="6f901-170">**A4SWIFT_FrrSendS21ACK**</span><span class="sxs-lookup"><span data-stu-id="6f901-170">**A4SWIFT_FrrSendS21ACK**</span></span>|  
    |<span data-ttu-id="6f901-171">MTS21_FIN_ACKNAK （負值通知的傳送 LT (NAK) 由 FIN 訊息</span><span class="sxs-lookup"><span data-stu-id="6f901-171">MTS21_FIN_ACKNAK (Negative acknowledgment of a FIN message sent by an LT (NAK)</span></span>|<span data-ttu-id="6f901-172">**A4SWIFT_FrrSendS21NAK**</span><span class="sxs-lookup"><span data-stu-id="6f901-172">**A4SWIFT_FrrSendS21NAK**</span></span>|  
  
11. <span data-ttu-id="6f901-173">針對類別 0 到 9 SWIFT FIN 訊息無法順利傳送，執行下列動作**篩選**窗格：</span><span class="sxs-lookup"><span data-stu-id="6f901-173">For Category 0 to 9 SWIFT FIN messages that are not successfully sent, do the following in the **Filters** pane:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f901-174">**A4SWIFT_FRRFailedReason**應分組在下列的篩選條件中的屬性。</span><span class="sxs-lookup"><span data-stu-id="6f901-174">The **A4SWIFT_FRRFailedReason** properties in the following filter should be grouped.</span></span>  
  
    |<span data-ttu-id="6f901-175">使用</span><span class="sxs-lookup"><span data-stu-id="6f901-175">Use this</span></span>|<span data-ttu-id="6f901-176">動作</span><span class="sxs-lookup"><span data-stu-id="6f901-176">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6f901-177">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6f901-177">**Property**</span></span>|<span data-ttu-id="6f901-178">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**。</span><span class="sxs-lookup"><span data-stu-id="6f901-178">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.</span></span>|  
    |<span data-ttu-id="6f901-179">**運算子**</span><span class="sxs-lookup"><span data-stu-id="6f901-179">**Operator**</span></span>|<span data-ttu-id="6f901-180">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="6f901-180">Select **==**.</span></span>|  
    |<span data-ttu-id="6f901-181">**值**</span><span class="sxs-lookup"><span data-stu-id="6f901-181">**Value**</span></span>|<span data-ttu-id="6f901-182">型別**A4SWIFT_FrrService**。</span><span class="sxs-lookup"><span data-stu-id="6f901-182">Type **A4SWIFT_FrrService**.</span></span>|  
    |<span data-ttu-id="6f901-183">**群組**</span><span class="sxs-lookup"><span data-stu-id="6f901-183">**Group**</span></span>|<span data-ttu-id="6f901-184">**和**</span><span class="sxs-lookup"><span data-stu-id="6f901-184">**And**</span></span>|  
    |<span data-ttu-id="6f901-185">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6f901-185">**Property**</span></span>|<span data-ttu-id="6f901-186">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FrrFailed**。</span><span class="sxs-lookup"><span data-stu-id="6f901-186">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FrrFailed**.</span></span>|  
    |<span data-ttu-id="6f901-187">**運算子**</span><span class="sxs-lookup"><span data-stu-id="6f901-187">**Operator**</span></span>|<span data-ttu-id="6f901-188">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="6f901-188">Select **==**.</span></span>|  
    |<span data-ttu-id="6f901-189">**值**</span><span class="sxs-lookup"><span data-stu-id="6f901-189">**Value**</span></span>|<span data-ttu-id="6f901-190">型別**True**。</span><span class="sxs-lookup"><span data-stu-id="6f901-190">Type **True**.</span></span>|  
    |<span data-ttu-id="6f901-191">**群組**</span><span class="sxs-lookup"><span data-stu-id="6f901-191">**Group**</span></span>|<span data-ttu-id="6f901-192">**和**</span><span class="sxs-lookup"><span data-stu-id="6f901-192">**And**</span></span>|  
    |<span data-ttu-id="6f901-193">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6f901-193">**Property**</span></span>|<span data-ttu-id="6f901-194">選取**BTS。作業**。</span><span class="sxs-lookup"><span data-stu-id="6f901-194">Select **BTS.Operation**.</span></span>|  
    |<span data-ttu-id="6f901-195">**運算子**</span><span class="sxs-lookup"><span data-stu-id="6f901-195">**Operator**</span></span>|<span data-ttu-id="6f901-196">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="6f901-196">Select **==**.</span></span>|  
    |<span data-ttu-id="6f901-197">**值**</span><span class="sxs-lookup"><span data-stu-id="6f901-197">**Value**</span></span>|<span data-ttu-id="6f901-198">型別**A4SWIFT_FrrSendMTMsg**。</span><span class="sxs-lookup"><span data-stu-id="6f901-198">Type **A4SWIFT_FrrSendMTMsg**.</span></span>|  
    |<span data-ttu-id="6f901-199">**群組**</span><span class="sxs-lookup"><span data-stu-id="6f901-199">**Group**</span></span>|<span data-ttu-id="6f901-200">**和**</span><span class="sxs-lookup"><span data-stu-id="6f901-200">**And**</span></span>|  
    |<span data-ttu-id="6f901-201">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6f901-201">**Property**</span></span>|<span data-ttu-id="6f901-202">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。</span><span class="sxs-lookup"><span data-stu-id="6f901-202">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="6f901-203">**運算子**</span><span class="sxs-lookup"><span data-stu-id="6f901-203">**Operator**</span></span>|<span data-ttu-id="6f901-204">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="6f901-204">Select **==**.</span></span>|  
    |<span data-ttu-id="6f901-205">**值**</span><span class="sxs-lookup"><span data-stu-id="6f901-205">**Value**</span></span>|<span data-ttu-id="6f901-206">型別 *\<NAKErrorCode >*，例如"Y01"。</span><span class="sxs-lookup"><span data-stu-id="6f901-206">Type *\<NAKErrorCode>*, such as "Y01".</span></span>|  
    |<span data-ttu-id="6f901-207">**群組**</span><span class="sxs-lookup"><span data-stu-id="6f901-207">**Group**</span></span>|<span data-ttu-id="6f901-208">**Or**</span><span class="sxs-lookup"><span data-stu-id="6f901-208">**Or**</span></span>|  
    |<span data-ttu-id="6f901-209">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6f901-209">**Property**</span></span>|<span data-ttu-id="6f901-210">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。</span><span class="sxs-lookup"><span data-stu-id="6f901-210">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="6f901-211">**運算子**</span><span class="sxs-lookup"><span data-stu-id="6f901-211">**Operator**</span></span>|<span data-ttu-id="6f901-212">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="6f901-212">Select **==**.</span></span>|  
    |<span data-ttu-id="6f901-213">**值**</span><span class="sxs-lookup"><span data-stu-id="6f901-213">**Value**</span></span>|<span data-ttu-id="6f901-214">型別**TimedOut**。</span><span class="sxs-lookup"><span data-stu-id="6f901-214">Type **TimedOut**.</span></span>|  
    |<span data-ttu-id="6f901-215">**群組**</span><span class="sxs-lookup"><span data-stu-id="6f901-215">**Group**</span></span>|<span data-ttu-id="6f901-216">**Or**</span><span class="sxs-lookup"><span data-stu-id="6f901-216">**Or**</span></span>|  
    |<span data-ttu-id="6f901-217">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6f901-217">**Property**</span></span>|<span data-ttu-id="6f901-218">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。</span><span class="sxs-lookup"><span data-stu-id="6f901-218">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="6f901-219">**運算子**</span><span class="sxs-lookup"><span data-stu-id="6f901-219">**Operator**</span></span>|<span data-ttu-id="6f901-220">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="6f901-220">Select **==**.</span></span>|  
    |<span data-ttu-id="6f901-221">**值**</span><span class="sxs-lookup"><span data-stu-id="6f901-221">**Value**</span></span>|<span data-ttu-id="6f901-222">型別**TransportError**。</span><span class="sxs-lookup"><span data-stu-id="6f901-222">Type **TransportError**.</span></span>|  
    |<span data-ttu-id="6f901-223">**群組**</span><span class="sxs-lookup"><span data-stu-id="6f901-223">**Group**</span></span>|<span data-ttu-id="6f901-224">**Or**</span><span class="sxs-lookup"><span data-stu-id="6f901-224">**Or**</span></span>|  
    |<span data-ttu-id="6f901-225">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6f901-225">**Property**</span></span>|<span data-ttu-id="6f901-226">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。</span><span class="sxs-lookup"><span data-stu-id="6f901-226">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="6f901-227">**運算子**</span><span class="sxs-lookup"><span data-stu-id="6f901-227">**Operator**</span></span>|<span data-ttu-id="6f901-228">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="6f901-228">Select **==**.</span></span>|  
    |<span data-ttu-id="6f901-229">**值**</span><span class="sxs-lookup"><span data-stu-id="6f901-229">**Value**</span></span>|<span data-ttu-id="6f901-230">型別**DelayedNAK**。</span><span class="sxs-lookup"><span data-stu-id="6f901-230">Type **DelayedNAK**.</span></span>|  
    |<span data-ttu-id="6f901-231">**群組**</span><span class="sxs-lookup"><span data-stu-id="6f901-231">**Group**</span></span>|<span data-ttu-id="6f901-232">**Or**</span><span class="sxs-lookup"><span data-stu-id="6f901-232">**Or**</span></span>|  
    |<span data-ttu-id="6f901-233">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6f901-233">**Property**</span></span>|<span data-ttu-id="6f901-234">選取**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。</span><span class="sxs-lookup"><span data-stu-id="6f901-234">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="6f901-235">**運算子**</span><span class="sxs-lookup"><span data-stu-id="6f901-235">**Operator**</span></span>|<span data-ttu-id="6f901-236">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="6f901-236">Select **==**.</span></span>|  
    |<span data-ttu-id="6f901-237">**值**</span><span class="sxs-lookup"><span data-stu-id="6f901-237">**Value**</span></span>|<span data-ttu-id="6f901-238">型別**AbortMessage**。</span><span class="sxs-lookup"><span data-stu-id="6f901-238">Type **AbortMessage**.</span></span>|  
  
12. <span data-ttu-id="6f901-239">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6f901-239">Click **Apply**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="6f901-240">傳送埠，以滑鼠右鍵按一下，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="6f901-240">Right-click the send port, and then click **Start**.</span></span>  
  
14. <span data-ttu-id="6f901-241">重複步驟 2 到 13，建立傳送埠所需的每個訊息類型。</span><span class="sxs-lookup"><span data-stu-id="6f901-241">Repeat steps 2 through 13 to create a send port for each message type required.</span></span>