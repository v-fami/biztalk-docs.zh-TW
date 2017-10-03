---
title: "步驟 5： 建立傳送埠將訊息傳遞 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f56ad7a7-5c77-4191-a001-691e5e0652a1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e85033256f7a49ed506fea00a7b48db67b0da1b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-create-a-send-port-to-deliver-messages"></a><span data-ttu-id="c1ae5-102">步驟 5： 建立傳送埠將訊息傳遞</span><span class="sxs-lookup"><span data-stu-id="c1ae5-102">Step 5: Create a Send Port to Deliver Messages</span></span>
<span data-ttu-id="c1ae5-103">在此步驟中，您可以建立和設定傳送接收之批次中包含的個別訊息的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-103">In this step, you create and configure a port for sending the individual messages contained in the received batch.</span></span> <span data-ttu-id="c1ae5-104">稍後在教學課程中，將原始的合作對象 (Tutorial_BatchSource) 片段中啟用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-104">Later in the tutorial, you will enable fragmentation for the originating party (Tutorial_BatchSource) in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span> <span data-ttu-id="c1ae5-105">如此一來，BizTalk 整合引擎時，會為個別的訊息片段批次和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會透過您在此步驟中建立的傳送埠傳送這些訊息。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-105">As a result, the BizTalk integration engine will fragment the batch into individual messages, and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will send those messages over the send port that you create in this step.</span></span>  
  
 <span data-ttu-id="c1ae5-106">您建立此連接埠是靜態，如此才會與 MLLP 配接器相關聯，它只會傳送到特定的目的地 （目的地的特定業務應用程式）。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-106">You create this port to be static, so that it will only be associated with an MLLP adapter, and it will only send to a specific destination (the destination line-of-business application).</span></span> <span data-ttu-id="c1ae5-107">在本教學課程中，該目的地會是包含在個別訊息 MSH5 MESA_IS。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-107">In this tutorial, that destination is MESA_IS, as contained in MSH5 of the individual messages.</span></span> <span data-ttu-id="c1ae5-108">您可以建立連接埠限制連接埠傳送訊息，而非通知來篩選掉符合 ACK_024_GLO_DEF 結構描述或任何靜態通知 (ACK) 訊息的篩選器。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-108">You create the port with filters that restrict the port to sending messages, not acknowledgments, by filtering out messages conforming to the ACK_024_GLO_DEF schema or any static acknowledgment (ACK).</span></span>  
  
 <span data-ttu-id="c1ae5-109">您設定這個傳送埠來接收通知的目的地，與名為接收埠產生關聯的傳送埠**TwoWayAckReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-109">You configure this send port to receive ACKs from the destination, by associating the send port with a receive port named **TwoWayAckReceivePort**.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="c1ae5-110">安裝程式會建立此連接埠，以及隨附的接收位置的**TwoWayAckReceiveLocation**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-110"> setup creates this port, and the accompanying receive location of **TwoWayAckReceiveLocation**.</span></span> <span data-ttu-id="c1ae5-111">您設定傳送埠設定來使用此連接埠**請求回應啟用**至**是**和設定**提交接收位置 URI**至**127.0.0.1:65535** （接受認可所需的設定）。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-111">You set the send port up to work with this port by setting **Solicit Response Enable** to **Yes** and setting the **Submit Receive Location URI** to **127.0.0.1:65535** (the settings required to accept ACKs).</span></span> <span data-ttu-id="c1ae5-112">如需詳細資訊，請參閱[設定向上傳送埠的接收認可](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-112">For more information, see [Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md).</span></span>  
  
### <a name="to-create-a-send-port-to-deliver-messages"></a><span data-ttu-id="c1ae5-113">若要建立傳送埠將訊息傳遞</span><span class="sxs-lookup"><span data-stu-id="c1ae5-113">To create a send port to deliver messages</span></span>  
  
1.  <span data-ttu-id="c1ae5-114">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-114">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="c1ae5-115">在 [傳送埠屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c1ae5-115">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="c1ae5-116">使用</span><span class="sxs-lookup"><span data-stu-id="c1ae5-116">Use this</span></span>|<span data-ttu-id="c1ae5-117">動作</span><span class="sxs-lookup"><span data-stu-id="c1ae5-117">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c1ae5-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-118">**Name**</span></span>|<span data-ttu-id="c1ae5-119">型別**Tutorial_2wayMsg**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-119">Type **Tutorial_2wayMsg**.</span></span>|  
    |<span data-ttu-id="c1ae5-120">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-120">**Transport type**</span></span>|<span data-ttu-id="c1ae5-121">選取**MLLP**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-121">Select **MLLP** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1ae5-122">**設定**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-122">**Configure**</span></span>|<span data-ttu-id="c1ae5-123">按一下**設定**開啟 MLLP 傳輸屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-123">Click **Configure** to open the MLLP Transport Properties dialog box.</span></span>|  
  
3.  <span data-ttu-id="c1ae5-124">在 MLLP 傳輸屬性 對話方塊中，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c1ae5-124">In the MLLP Transport Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="c1ae5-125">使用</span><span class="sxs-lookup"><span data-stu-id="c1ae5-125">Use this</span></span>|<span data-ttu-id="c1ae5-126">動作</span><span class="sxs-lookup"><span data-stu-id="c1ae5-126">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c1ae5-127">**連接名稱**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-127">**Connection Name**</span></span>|<span data-ttu-id="c1ae5-128">型別**2wayMsg**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-128">Type **2wayMsg**.</span></span>|  
    |<span data-ttu-id="c1ae5-129">**Host**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-129">**Host**</span></span>|<span data-ttu-id="c1ae5-130">型別**localhost**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-130">Type **localhost**.</span></span>|  
    |<span data-ttu-id="c1ae5-131">**[通訊埠]**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-131">**Port**</span></span>|<span data-ttu-id="c1ae5-132">型別**41000**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-132">Type **41000**.</span></span>|  
    |<span data-ttu-id="c1ae5-133">**請求回應已啟用**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-133">**Solicit Response Enabled**</span></span>|<span data-ttu-id="c1ae5-134">按一下右邊的欄位**請求回應啟用**，然後選取**是**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-134">Click the field to the right of **Solicit Response Enabled**, and then select **Yes** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1ae5-135">**送出接收位置 (URI) 的通知**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-135">**Submit Receive Location (URI) for ACK**</span></span>|<span data-ttu-id="c1ae5-136">型別**127.0.0.1:65535**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-136">Type**127.0.0.1:65535**</span></span>|  
  
4.  <span data-ttu-id="c1ae5-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-137">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="c1ae5-138">在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-138">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
6.  <span data-ttu-id="c1ae5-139">在主控台樹狀目錄中，按一下**篩選**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c1ae5-139">In the console tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="c1ae5-140">使用</span><span class="sxs-lookup"><span data-stu-id="c1ae5-140">Use this</span></span>|<span data-ttu-id="c1ae5-141">動作</span><span class="sxs-lookup"><span data-stu-id="c1ae5-141">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c1ae5-142">**屬性**（第一次換行）</span><span class="sxs-lookup"><span data-stu-id="c1ae5-142">**Property** (first line)</span></span>|<span data-ttu-id="c1ae5-143">按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-143">Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1ae5-144">**運算子**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-144">**Operator**</span></span>|<span data-ttu-id="c1ae5-145">選取**！ =**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-145">Select **!=** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1ae5-146">**值**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-146">**Value**</span></span>|<span data-ttu-id="c1ae5-147">型別**http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-147">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**.</span></span>|  
    |<span data-ttu-id="c1ae5-148">**Group By**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-148">**Group By**</span></span>|<span data-ttu-id="c1ae5-149">選取**AND**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-149">Select **AND** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1ae5-150">**屬性**（第二行）</span><span class="sxs-lookup"><span data-stu-id="c1ae5-150">**Property** (second line)</span></span>|<span data-ttu-id="c1ae5-151">按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-151">Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1ae5-152">**運算子**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-152">**Operator**</span></span>|<span data-ttu-id="c1ae5-153">選取**！ =**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-153">Select **!=** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1ae5-154">**值**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-154">**Value**</span></span>|<span data-ttu-id="c1ae5-155">型別**http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF。**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-155">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.**</span></span>|  
    |<span data-ttu-id="c1ae5-156">**Group By**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-156">**Group By**</span></span>|<span data-ttu-id="c1ae5-157">選取**和**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-157">Select **And** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1ae5-158">**屬性**（第三個行）</span><span class="sxs-lookup"><span data-stu-id="c1ae5-158">**Property** (third line)</span></span>|<span data-ttu-id="c1ae5-159">按一下底下的第二列的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-159">Click the field on the second line under **Property**, and then select **BTS.MessageType** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1ae5-160">**運算子**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-160">**Operator**</span></span>|<span data-ttu-id="c1ae5-161">選取**！ =**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-161">Select **!=** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1ae5-162">**值**</span><span class="sxs-lookup"><span data-stu-id="c1ae5-162">**Value**</span></span>|<span data-ttu-id="c1ae5-163">型別**StaticAck**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-163">Type **StaticAck**.</span></span>|  
  
7.  <span data-ttu-id="c1ae5-164">按一下 **[輸入]**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-164">Click **Enter**.</span></span> <span data-ttu-id="c1ae5-165">在對話方塊底部窗格中，確認正確地輸入篩選運算式，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-165">In the pane at the bottom of the dialog box, verify that you entered the filter expression correctly, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="c1ae5-166">在 管理主控台中，按一下 **傳送埠**，以滑鼠右鍵按一下**Tutorial_2wayMsg**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-166">In the Administration Console, click **Send Ports**, right-click **Tutorial_2wayMsg**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="c1ae5-167">若要繼續[步驟 6： 建立要傳遞通知的傳送埠](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md)。</span><span class="sxs-lookup"><span data-stu-id="c1ae5-167">Proceed to [Step 6: Create a Send Port to Deliver Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md).</span></span>