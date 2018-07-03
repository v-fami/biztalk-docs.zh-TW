---
title: 建立 FRR 傳送埠來傳送至自訂處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
- FRR, creating send ports
ms.assetid: 036f1f97-17a2-4e02-a85a-a52739a48528
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed467b149674580b9ed8921a59433c5402a24a0e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013935"
---
# <a name="creating-the-frr-send-ports-for-sending-to-the-custom-handlers"></a><span data-ttu-id="24b2b-102">建立 FRR 傳送埠來傳送至自訂處理常式</span><span class="sxs-lookup"><span data-stu-id="24b2b-102">Creating the FRR Send Ports for Sending to the Custom Handlers</span></span>
<span data-ttu-id="24b2b-103">若要執行 FIN 回應對帳，您需要建立的一連串的傳送埠，其中每個會傳送一則訊息 （原始的訊息或回應） 從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]處理相互關聯的訊息的自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="24b2b-103">To perform FIN Response Reconciliation, you need to create a series of send ports, each of which sends a message (original message or response) from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the custom handlers that process the correlated messages.</span></span>  

 <span data-ttu-id="24b2b-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="24b2b-104">**Summary**</span></span>  

 <span data-ttu-id="24b2b-105">使用下列屬性和元件的 BTS 的值來區分每個建立一系列的傳送埠。在篩選中的作業：</span><span class="sxs-lookup"><span data-stu-id="24b2b-105">Create a series of send ports with the following properties and components, each one distinguished by the value of BTS.Operation in the filter:</span></span>  


|        <span data-ttu-id="24b2b-106">屬性/元件</span><span class="sxs-lookup"><span data-stu-id="24b2b-106">Property/Component</span></span>        |                                             <span data-ttu-id="24b2b-107">設定</span><span class="sxs-lookup"><span data-stu-id="24b2b-107">Setting</span></span>                                              |
|----------------------------------|--------------------------------------------------------------------------------------------------|
|            <span data-ttu-id="24b2b-108">傳送埠</span><span class="sxs-lookup"><span data-stu-id="24b2b-108">Send port</span></span>             |                                       <span data-ttu-id="24b2b-109">靜態單向連接埠</span><span class="sxs-lookup"><span data-stu-id="24b2b-109">Static one-way port</span></span>                                        |
|          <span data-ttu-id="24b2b-110">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="24b2b-110">Transport type</span></span>          |                                               <span data-ttu-id="24b2b-111">FILE</span><span class="sxs-lookup"><span data-stu-id="24b2b-111">FILE</span></span>                                               |
| <span data-ttu-id="24b2b-112">目的地資料夾 (位址 URI)</span><span class="sxs-lookup"><span data-stu-id="24b2b-112">Destination folder (Address URI)</span></span> |                         <span data-ttu-id="24b2b-113">您想要將訊息傳送至資料夾</span><span class="sxs-lookup"><span data-stu-id="24b2b-113">The folder that you want to send the message to</span></span>                          |
|     <span data-ttu-id="24b2b-114">檔案名稱 (位址 URI)</span><span class="sxs-lookup"><span data-stu-id="24b2b-114">File name (Address URI)</span></span>      |                                         <span data-ttu-id="24b2b-115">%MessageID%.txt</span><span class="sxs-lookup"><span data-stu-id="24b2b-115">%MessageID%.txt</span></span>                                          |
|          <span data-ttu-id="24b2b-116">傳送管線</span><span class="sxs-lookup"><span data-stu-id="24b2b-116">Send pipeline</span></span>           | <span data-ttu-id="24b2b-117">Microsoft。BizTalk.DefaultPipelines。</span><span class="sxs-lookup"><span data-stu-id="24b2b-117">Microsoft .BizTalk.DefaultPipelines.</span></span> <span data-ttu-id="24b2b-118">PassThruTransmit</span><span class="sxs-lookup"><span data-stu-id="24b2b-118">PassThruTransmit</span></span> |
|             <span data-ttu-id="24b2b-119">篩選</span><span class="sxs-lookup"><span data-stu-id="24b2b-119">Filters</span></span>              |                                   <span data-ttu-id="24b2b-120">下表所示</span><span class="sxs-lookup"><span data-stu-id="24b2b-120">As shown in the tables below</span></span>                                   |

 <span data-ttu-id="24b2b-121">BTS 的值來區別不同的訊息的傳送埠。在 傳送埠的篩選器的作業。</span><span class="sxs-lookup"><span data-stu-id="24b2b-121">The send ports for the different messages are distinguished by the value of BTS.Operation in the send port's filter.</span></span>  

### <a name="to-add-frr-send-ports-for-sending-to-the-custom-handlers"></a><span data-ttu-id="24b2b-122">若要新增將傳送至自訂處理常式的 FRR 傳送埠</span><span class="sxs-lookup"><span data-stu-id="24b2b-122">To add FRR send ports for sending to the custom handlers</span></span>  

1.  <span data-ttu-id="24b2b-123">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態一個 waySend 埠**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-123">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-waySend Port**.</span></span>  

2.  <span data-ttu-id="24b2b-124">在傳送埠屬性 對話方塊中，在**名稱**方塊中，輸入傳送埠，例如 FRRCustomHandlersSendPort 的名稱。</span><span class="sxs-lookup"><span data-stu-id="24b2b-124">In the Send Port Properties dialog box, in the **Name** box, type a name for the send port, such as FRRCustomHandlersSendPort.</span></span>  

3.  <span data-ttu-id="24b2b-125">針對**型別**，選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-125">For **Type**, select **FILE**.</span></span>  

4.  <span data-ttu-id="24b2b-126">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-126">Click **Configure**.</span></span>  

5.  <span data-ttu-id="24b2b-127">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-127">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  

6.  <span data-ttu-id="24b2b-128">在 [瀏覽資料夾] 對話方塊中，移至您想要傳送訊息的來源資料夾。</span><span class="sxs-lookup"><span data-stu-id="24b2b-128">In the Browse For Folder dialog box, move to the folder that you want to send messages from.</span></span> <span data-ttu-id="24b2b-129">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="24b2b-129">Click **OK**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="24b2b-130">如果此資料夾不存在，您可以使用建立它**建立新資料夾**命令。</span><span class="sxs-lookup"><span data-stu-id="24b2b-130">If this folder does not exist, you can create it using the **Make New Folder** command.</span></span>  

7.  <span data-ttu-id="24b2b-131">在 **檔名**方塊中，輸入 **%MessageID%.txt**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-131">In the **File name** box, type **%MessageID%.txt**, and then click **OK**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="24b2b-132">您可以建立不同的資料夾，每種類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="24b2b-132">You can create a different folder for each type of message.</span></span>  

8.  <span data-ttu-id="24b2b-133">在 傳送埠屬性 對話方塊的 傳送處理常式中，確認**BizTalkServerApplication**已選取。</span><span class="sxs-lookup"><span data-stu-id="24b2b-133">In the Send Port Properties dialog box, for Send handler, verify that **BizTalkServerApplication** is selected.</span></span>  

9. <span data-ttu-id="24b2b-134">針對**傳送管線**，選取**PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-134">For **Send Pipeline**, select **PassThruTransmit**.</span></span>  

10. <span data-ttu-id="24b2b-135">按一下 **篩選器**左的窗格中，然後執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="24b2b-135">Click **Filters** in the left pane, and then do the following:</span></span>  

    |<span data-ttu-id="24b2b-136">使用</span><span class="sxs-lookup"><span data-stu-id="24b2b-136">Use this</span></span>|<span data-ttu-id="24b2b-137">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="24b2b-137">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="24b2b-138">**屬性**</span><span class="sxs-lookup"><span data-stu-id="24b2b-138">**Property**</span></span>|<span data-ttu-id="24b2b-139">選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-139">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.</span></span>|  
    |<span data-ttu-id="24b2b-140">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="24b2b-140">**Operator**</span></span>|<span data-ttu-id="24b2b-141">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-141">Select **==**.</span></span>|  
    |<span data-ttu-id="24b2b-142">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="24b2b-142">**Value**</span></span>|<span data-ttu-id="24b2b-143">型別**A4SWIFT_FrrService**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-143">Type **A4SWIFT_FrrService**.</span></span>|  
    |<span data-ttu-id="24b2b-144">**群組**</span><span class="sxs-lookup"><span data-stu-id="24b2b-144">**Group**</span></span>|<span data-ttu-id="24b2b-145">**和**</span><span class="sxs-lookup"><span data-stu-id="24b2b-145">**And**</span></span>|  
    |<span data-ttu-id="24b2b-146">**屬性**</span><span class="sxs-lookup"><span data-stu-id="24b2b-146">**Property**</span></span>|<span data-ttu-id="24b2b-147">選取**BTS。作業**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-147">Select **BTS.Operation**.</span></span>|  
    |<span data-ttu-id="24b2b-148">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="24b2b-148">**Operator**</span></span>|<span data-ttu-id="24b2b-149">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-149">Select **==**.</span></span>|  
    |<span data-ttu-id="24b2b-150">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="24b2b-150">**Value**</span></span>|<span data-ttu-id="24b2b-151">輸入 BTS 的其中一個。下表中的作業值。</span><span class="sxs-lookup"><span data-stu-id="24b2b-151">Type one of the BTS.Operation values from the table below.</span></span>|  

     <span data-ttu-id="24b2b-152">針對 BTS。作業中，輸入下列值之一：</span><span class="sxs-lookup"><span data-stu-id="24b2b-152">For BTS.Operation, enter one of the following values:</span></span>  

    |<span data-ttu-id="24b2b-153">訊息類型</span><span class="sxs-lookup"><span data-stu-id="24b2b-153">Message type</span></span>|<span data-ttu-id="24b2b-154">BTS。作業值</span><span class="sxs-lookup"><span data-stu-id="24b2b-154">BTS.Operation value</span></span>|  
    |------------------|-------------------------|  
    |<span data-ttu-id="24b2b-155">所有類別 0 到 9 SWIFT FIN 訊息類型</span><span class="sxs-lookup"><span data-stu-id="24b2b-155">All Category 0 to 9 SWIFT FIN message types</span></span>|<span data-ttu-id="24b2b-156">**A4SWIFT_FrrSendMTMsg**</span><span class="sxs-lookup"><span data-stu-id="24b2b-156">**A4SWIFT_FrrSendMTMsg**</span></span>|  
    |<span data-ttu-id="24b2b-157">MQ 系列移動瀏覽/NAN (MQ Series 傳輸層級通知/NAK)</span><span class="sxs-lookup"><span data-stu-id="24b2b-157">MQ Series PAN/NAN (MQ Series transport-level ACK/NAK)</span></span>|<span data-ttu-id="24b2b-158">**A4SWIFT_FrrSendTransport**</span><span class="sxs-lookup"><span data-stu-id="24b2b-158">**A4SWIFT_FrrSendTransport**</span></span>|  
    |<span data-ttu-id="24b2b-159">MT010 （非傳遞警告）</span><span class="sxs-lookup"><span data-stu-id="24b2b-159">MT010 (Non-Delivery Warning)</span></span>|<span data-ttu-id="24b2b-160">**A4SWIFT_FrrSend010NDW**</span><span class="sxs-lookup"><span data-stu-id="24b2b-160">**A4SWIFT_FrrSend010NDW**</span></span>|  
    |<span data-ttu-id="24b2b-161">MT011 （傳遞通知）</span><span class="sxs-lookup"><span data-stu-id="24b2b-161">MT011 (Delivery Notification)</span></span>|<span data-ttu-id="24b2b-162">**A4SWIFT_FrrSend011Delivered**</span><span class="sxs-lookup"><span data-stu-id="24b2b-162">**A4SWIFT_FrrSend011Delivered**</span></span>|  
    |<span data-ttu-id="24b2b-163">MT012 （寄件者通知）</span><span class="sxs-lookup"><span data-stu-id="24b2b-163">MT012 (Sender Notification)</span></span>|<span data-ttu-id="24b2b-164">**A4SWIFT_FrrSend012SenderACK**</span><span class="sxs-lookup"><span data-stu-id="24b2b-164">**A4SWIFT_FrrSend012SenderACK**</span></span>|  
    |<span data-ttu-id="24b2b-165">MT015 （DNK 或延遲的 NAK）</span><span class="sxs-lookup"><span data-stu-id="24b2b-165">MT015 (DNK, or Delayed NAK)</span></span>|<span data-ttu-id="24b2b-166">**A4SWIFT_FrrSend015DNK**</span><span class="sxs-lookup"><span data-stu-id="24b2b-166">**A4SWIFT_FrrSend015DNK**</span></span>|  
    |<span data-ttu-id="24b2b-167">MT019 （中止通知）</span><span class="sxs-lookup"><span data-stu-id="24b2b-167">MT019 (Abort Notification)</span></span>|<span data-ttu-id="24b2b-168">**A4SWIFT_FrrSend019Abort**</span><span class="sxs-lookup"><span data-stu-id="24b2b-168">**A4SWIFT_FrrSend019Abort**</span></span>|  
    |<span data-ttu-id="24b2b-169">MTS21_FIN_ACKNAK （FIN 訊息傳送的 L (ACK) 的通知</span><span class="sxs-lookup"><span data-stu-id="24b2b-169">MTS21_FIN_ACKNAK (Acknowledgment of a FIN message sent by an LT (ACK)</span></span>|<span data-ttu-id="24b2b-170">**A4SWIFT_FrrSendS21ACK**</span><span class="sxs-lookup"><span data-stu-id="24b2b-170">**A4SWIFT_FrrSendS21ACK**</span></span>|  
    |<span data-ttu-id="24b2b-171">MTS21_FIN_ACKNAK （負值通知的傳送 L (NAK) 由 FIN 訊息</span><span class="sxs-lookup"><span data-stu-id="24b2b-171">MTS21_FIN_ACKNAK (Negative acknowledgment of a FIN message sent by an LT (NAK)</span></span>|<span data-ttu-id="24b2b-172">**A4SWIFT_FrrSendS21NAK**</span><span class="sxs-lookup"><span data-stu-id="24b2b-172">**A4SWIFT_FrrSendS21NAK**</span></span>|  

11. <span data-ttu-id="24b2b-173">為類別 0 到 9 SWIFT FIN 訊息未成功傳送，執行下列**篩選器**窗格：</span><span class="sxs-lookup"><span data-stu-id="24b2b-173">For Category 0 to 9 SWIFT FIN messages that are not successfully sent, do the following in the **Filters** pane:</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="24b2b-174">**A4SWIFT_FRRFailedReason**應群組在下列的篩選條件中的屬性。</span><span class="sxs-lookup"><span data-stu-id="24b2b-174">The **A4SWIFT_FRRFailedReason** properties in the following filter should be grouped.</span></span>  

    |<span data-ttu-id="24b2b-175">使用</span><span class="sxs-lookup"><span data-stu-id="24b2b-175">Use this</span></span>|<span data-ttu-id="24b2b-176">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="24b2b-176">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="24b2b-177">**屬性**</span><span class="sxs-lookup"><span data-stu-id="24b2b-177">**Property**</span></span>|<span data-ttu-id="24b2b-178">選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-178">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.</span></span>|  
    |<span data-ttu-id="24b2b-179">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="24b2b-179">**Operator**</span></span>|<span data-ttu-id="24b2b-180">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-180">Select **==**.</span></span>|  
    |<span data-ttu-id="24b2b-181">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="24b2b-181">**Value**</span></span>|<span data-ttu-id="24b2b-182">型別**A4SWIFT_FrrService**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-182">Type **A4SWIFT_FrrService**.</span></span>|  
    |<span data-ttu-id="24b2b-183">**群組**</span><span class="sxs-lookup"><span data-stu-id="24b2b-183">**Group**</span></span>|<span data-ttu-id="24b2b-184">**和**</span><span class="sxs-lookup"><span data-stu-id="24b2b-184">**And**</span></span>|  
    |<span data-ttu-id="24b2b-185">**屬性**</span><span class="sxs-lookup"><span data-stu-id="24b2b-185">**Property**</span></span>|<span data-ttu-id="24b2b-186">選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FrrFailed**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-186">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FrrFailed**.</span></span>|  
    |<span data-ttu-id="24b2b-187">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="24b2b-187">**Operator**</span></span>|<span data-ttu-id="24b2b-188">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-188">Select **==**.</span></span>|  
    |<span data-ttu-id="24b2b-189">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="24b2b-189">**Value**</span></span>|<span data-ttu-id="24b2b-190">型別 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-190">Type **True**.</span></span>|  
    |<span data-ttu-id="24b2b-191">**群組**</span><span class="sxs-lookup"><span data-stu-id="24b2b-191">**Group**</span></span>|<span data-ttu-id="24b2b-192">**和**</span><span class="sxs-lookup"><span data-stu-id="24b2b-192">**And**</span></span>|  
    |<span data-ttu-id="24b2b-193">**屬性**</span><span class="sxs-lookup"><span data-stu-id="24b2b-193">**Property**</span></span>|<span data-ttu-id="24b2b-194">選取**BTS。作業**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-194">Select **BTS.Operation**.</span></span>|  
    |<span data-ttu-id="24b2b-195">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="24b2b-195">**Operator**</span></span>|<span data-ttu-id="24b2b-196">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-196">Select **==**.</span></span>|  
    |<span data-ttu-id="24b2b-197">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="24b2b-197">**Value**</span></span>|<span data-ttu-id="24b2b-198">型別**A4SWIFT_FrrSendMTMsg**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-198">Type **A4SWIFT_FrrSendMTMsg**.</span></span>|  
    |<span data-ttu-id="24b2b-199">**群組**</span><span class="sxs-lookup"><span data-stu-id="24b2b-199">**Group**</span></span>|<span data-ttu-id="24b2b-200">**和**</span><span class="sxs-lookup"><span data-stu-id="24b2b-200">**And**</span></span>|  
    |<span data-ttu-id="24b2b-201">**屬性**</span><span class="sxs-lookup"><span data-stu-id="24b2b-201">**Property**</span></span>|<span data-ttu-id="24b2b-202">選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-202">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="24b2b-203">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="24b2b-203">**Operator**</span></span>|<span data-ttu-id="24b2b-204">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-204">Select **==**.</span></span>|  
    |<span data-ttu-id="24b2b-205">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="24b2b-205">**Value**</span></span>|<span data-ttu-id="24b2b-206">型別 *\<NAKErrorCode\>*，例如"Y01 」。</span><span class="sxs-lookup"><span data-stu-id="24b2b-206">Type *\<NAKErrorCode\>*, such as "Y01".</span></span>|  
    |<span data-ttu-id="24b2b-207">**群組**</span><span class="sxs-lookup"><span data-stu-id="24b2b-207">**Group**</span></span>|<span data-ttu-id="24b2b-208">**Or**</span><span class="sxs-lookup"><span data-stu-id="24b2b-208">**Or**</span></span>|  
    |<span data-ttu-id="24b2b-209">**屬性**</span><span class="sxs-lookup"><span data-stu-id="24b2b-209">**Property**</span></span>|<span data-ttu-id="24b2b-210">選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-210">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="24b2b-211">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="24b2b-211">**Operator**</span></span>|<span data-ttu-id="24b2b-212">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-212">Select **==**.</span></span>|  
    |<span data-ttu-id="24b2b-213">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="24b2b-213">**Value**</span></span>|<span data-ttu-id="24b2b-214">型別**TimedOut**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-214">Type **TimedOut**.</span></span>|  
    |<span data-ttu-id="24b2b-215">**群組**</span><span class="sxs-lookup"><span data-stu-id="24b2b-215">**Group**</span></span>|<span data-ttu-id="24b2b-216">**Or**</span><span class="sxs-lookup"><span data-stu-id="24b2b-216">**Or**</span></span>|  
    |<span data-ttu-id="24b2b-217">**屬性**</span><span class="sxs-lookup"><span data-stu-id="24b2b-217">**Property**</span></span>|<span data-ttu-id="24b2b-218">選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-218">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="24b2b-219">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="24b2b-219">**Operator**</span></span>|<span data-ttu-id="24b2b-220">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-220">Select **==**.</span></span>|  
    |<span data-ttu-id="24b2b-221">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="24b2b-221">**Value**</span></span>|<span data-ttu-id="24b2b-222">型別**TransportError**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-222">Type **TransportError**.</span></span>|  
    |<span data-ttu-id="24b2b-223">**群組**</span><span class="sxs-lookup"><span data-stu-id="24b2b-223">**Group**</span></span>|<span data-ttu-id="24b2b-224">**Or**</span><span class="sxs-lookup"><span data-stu-id="24b2b-224">**Or**</span></span>|  
    |<span data-ttu-id="24b2b-225">**屬性**</span><span class="sxs-lookup"><span data-stu-id="24b2b-225">**Property**</span></span>|<span data-ttu-id="24b2b-226">選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-226">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="24b2b-227">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="24b2b-227">**Operator**</span></span>|<span data-ttu-id="24b2b-228">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-228">Select **==**.</span></span>|  
    |<span data-ttu-id="24b2b-229">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="24b2b-229">**Value**</span></span>|<span data-ttu-id="24b2b-230">型別**DelayedNAK**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-230">Type **DelayedNAK**.</span></span>|  
    |<span data-ttu-id="24b2b-231">**群組**</span><span class="sxs-lookup"><span data-stu-id="24b2b-231">**Group**</span></span>|<span data-ttu-id="24b2b-232">**Or**</span><span class="sxs-lookup"><span data-stu-id="24b2b-232">**Or**</span></span>|  
    |<span data-ttu-id="24b2b-233">**屬性**</span><span class="sxs-lookup"><span data-stu-id="24b2b-233">**Property**</span></span>|<span data-ttu-id="24b2b-234">選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-234">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="24b2b-235">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="24b2b-235">**Operator**</span></span>|<span data-ttu-id="24b2b-236">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-236">Select **==**.</span></span>|  
    |<span data-ttu-id="24b2b-237">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="24b2b-237">**Value**</span></span>|<span data-ttu-id="24b2b-238">型別**AbortMessage**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-238">Type **AbortMessage**.</span></span>|  

12. <span data-ttu-id="24b2b-239">按一下 **套用**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-239">Click **Apply**, and then click **OK**.</span></span>  

13. <span data-ttu-id="24b2b-240">以滑鼠右鍵按一下傳送埠，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="24b2b-240">Right-click the send port, and then click **Start**.</span></span>  

14. <span data-ttu-id="24b2b-241">重複步驟 2 到 13，以建立傳送埠所需每種訊息類型。</span><span class="sxs-lookup"><span data-stu-id="24b2b-241">Repeat steps 2 through 13 to create a send port for each message type required.</span></span>