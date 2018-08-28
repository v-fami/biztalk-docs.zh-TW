---
title: 步驟 6： 建立傳送埠以傳遞通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 739b3e60-db56-46e9-a6b1-0acbe0c08f55
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47e30db70d67cb70ba87cf661e46ca325de1f3cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003615"
---
# <a name="step-6-create-a-send-port-to-deliver-acknowledgments"></a><span data-ttu-id="cc746-102">步驟 6： 建立傳送埠以傳遞通知</span><span class="sxs-lookup"><span data-stu-id="cc746-102">Step 6: Create a Send Port to Deliver Acknowledgments</span></span>
<span data-ttu-id="cc746-103">在此步驟中，您可以建立連接埠來傳送通知回批次的來源。</span><span class="sxs-lookup"><span data-stu-id="cc746-103">In this step, you create a port to send acknowledgments back to the source of the batch.</span></span>  

 <span data-ttu-id="cc746-104">您建立此連接埠是靜態，如此就只能是 MLLP 配接器相關聯，而且它只會傳送到特定的目的地 （批次的來源）。</span><span class="sxs-lookup"><span data-stu-id="cc746-104">You create this port to be static, so that it will only be associated with an MLLP adapter, and it will only send to a specific destination (the source of the batch).</span></span> <span data-ttu-id="cc746-105">在本教學課程中，來源是合作對象 Tutorial_BatchSource 相關聯。</span><span class="sxs-lookup"><span data-stu-id="cc746-105">In this tutorial, the source is associated with the party Tutorial_BatchSource.</span></span> <span data-ttu-id="cc746-106">此來源合作對象都包含在個別的訊息和 FHS3 MSH3 和 BHS3 原始批次。</span><span class="sxs-lookup"><span data-stu-id="cc746-106">This source party is contained in MSH3 of the individual messages and FHS3 and BHS3 of the original batch.</span></span>  

 <span data-ttu-id="cc746-107">您可以建立連接埠具有限制的連接埠來傳送通知，不是資料訊息的篩選。</span><span class="sxs-lookup"><span data-stu-id="cc746-107">You create the port with filters that restrict the port to sending acknowledgments, not data messages.</span></span> <span data-ttu-id="cc746-108">這些篩選器指定一種 ACK_024_GLO_DEF] 和 [目的地為 Tutorial_BatchSource 之間的訊息。</span><span class="sxs-lookup"><span data-stu-id="cc746-108">These filters specify a message type of ACK_024_GLO_DEF and a destination of Tutorial_BatchSource.</span></span>  

 <span data-ttu-id="cc746-109">您設定這個傳送埠以接收通知的目的地，與名為的接收埠產生關聯的傳送埠**TwoWayAckReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="cc746-109">You configure this send port to receive acknowledgments from the destination, by associating the send port with a receive port named **TwoWayAckReceivePort**.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="cc746-110"> 安裝程式建立此連接埠，以及隨附的接收位置**TwoWayAckReceiveLocation**。</span><span class="sxs-lookup"><span data-stu-id="cc746-110"> setup creates this port, and the accompanying receive location of **TwoWayAckReceiveLocation**.</span></span> <span data-ttu-id="cc746-111">您設定傳送埠來設定使用此連接埠**請求回應啟用**來**否**並設定**提交接收位置 URI**來**127.0.0.1:65535** （接受通知所需的設定）。</span><span class="sxs-lookup"><span data-stu-id="cc746-111">You set the send port up to work with this port by setting **Solicit Response Enable** to **No** and setting the **Submit Receive Location URI** to **127.0.0.1:65535** (the settings required to accept ACKs).</span></span> <span data-ttu-id="cc746-112">如需詳細資訊，請參閱 <<c0> [ 設定向上傳送連接埠接收 Ack](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)。</span><span class="sxs-lookup"><span data-stu-id="cc746-112">For more information, see [Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md).</span></span>  

### <a name="to-create-a-send-port-to-deliver-acknowledgments"></a><span data-ttu-id="cc746-113">若要建立傳送埠以傳遞通知</span><span class="sxs-lookup"><span data-stu-id="cc746-113">To create a send port to deliver acknowledgments</span></span>  

1. <span data-ttu-id="cc746-114">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="cc746-114">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  

2. <span data-ttu-id="cc746-115">在 [傳送埠屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cc746-115">In the Send Port Properties dialog box, do the following:</span></span>  


   |      <span data-ttu-id="cc746-116">使用</span><span class="sxs-lookup"><span data-stu-id="cc746-116">Use this</span></span>      |                                <span data-ttu-id="cc746-117">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cc746-117">To do this</span></span>                                 |
   |--------------------|---------------------------------------------------------------------------|
   |      <span data-ttu-id="cc746-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="cc746-118">**Name**</span></span>      |                        <span data-ttu-id="cc746-119">型別**Tutorial_2wayAck**。</span><span class="sxs-lookup"><span data-stu-id="cc746-119">Type **Tutorial_2wayAck**.</span></span>                         |
   | <span data-ttu-id="cc746-120">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="cc746-120">**Transport type**</span></span> |                 <span data-ttu-id="cc746-121">選取  **MLLP**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cc746-121">Select **MLLP** from the drop-down list.</span></span>                  |
   |   <span data-ttu-id="cc746-122">**設定**</span><span class="sxs-lookup"><span data-stu-id="cc746-122">**Configure**</span></span>    | <span data-ttu-id="cc746-123">按一下 [**設定**來開啟**MLLP 傳輸屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cc746-123">Click **Configure** to open the **MLLP Transport Properties** dialog box.</span></span> |


3. <span data-ttu-id="cc746-124">在 [MLLP 傳輸屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="cc746-124">In the MLLP Transport Properties dialog box, do the following:</span></span>  


   |                 <span data-ttu-id="cc746-125">使用</span><span class="sxs-lookup"><span data-stu-id="cc746-125">Use this</span></span>                  |        <span data-ttu-id="cc746-126">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cc746-126">To do this</span></span>         |
   |-------------------------------------------|---------------------------|
   |            <span data-ttu-id="cc746-127">**連接名稱**</span><span class="sxs-lookup"><span data-stu-id="cc746-127">**Connection Name**</span></span>            |     <span data-ttu-id="cc746-128">型別**2wayAck**。</span><span class="sxs-lookup"><span data-stu-id="cc746-128">Type **2wayAck**.</span></span>     |
   |                 <span data-ttu-id="cc746-129">**主控件**</span><span class="sxs-lookup"><span data-stu-id="cc746-129">**Host**</span></span>                  |    <span data-ttu-id="cc746-130">型別**localhost**。</span><span class="sxs-lookup"><span data-stu-id="cc746-130">Type **localhost**.</span></span>    |
   |                 <span data-ttu-id="cc746-131">**通訊埠**</span><span class="sxs-lookup"><span data-stu-id="cc746-131">**Port**</span></span>                  |      <span data-ttu-id="cc746-132">型別**41002**。</span><span class="sxs-lookup"><span data-stu-id="cc746-132">Type **41002**.</span></span>      |
   |       <span data-ttu-id="cc746-133">**請求回應已啟用**</span><span class="sxs-lookup"><span data-stu-id="cc746-133">**Solicit Response Enabled**</span></span>        | <span data-ttu-id="cc746-134">保留做為欄位**No**。</span><span class="sxs-lookup"><span data-stu-id="cc746-134">Keep the field as **No**.</span></span> |
   | <span data-ttu-id="cc746-135">**提交接收通知的位置 (URI)**</span><span class="sxs-lookup"><span data-stu-id="cc746-135">**Submit Receive Location (URI) for ACK**</span></span> | <span data-ttu-id="cc746-136">型別**127.0.0.1:65535**</span><span class="sxs-lookup"><span data-stu-id="cc746-136">Type **127.0.0.1:65535**</span></span>  |


4. <span data-ttu-id="cc746-137">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="cc746-137">Click **OK**.</span></span>  

5. <span data-ttu-id="cc746-138">在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="cc746-138">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  

6. <span data-ttu-id="cc746-139">在主控台樹狀目錄中，按一下**篩選**，然後執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="cc746-139">In the console tree, click **Filters**, and then do the following:</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="cc746-140">請確定您完全依照顯示輸入下列資料。</span><span class="sxs-lookup"><span data-stu-id="cc746-140">Ensure that you enter the following data exactly as shown.</span></span> <span data-ttu-id="cc746-141">這項資料會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="cc746-141">This data is case-sensitive.</span></span>  

   |          <span data-ttu-id="cc746-142">使用</span><span class="sxs-lookup"><span data-stu-id="cc746-142">Use this</span></span>          |                                            <span data-ttu-id="cc746-143">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="cc746-143">To do this</span></span>                                            |
   |----------------------------|--------------------------------------------------------------------------------------------------|
   | <span data-ttu-id="cc746-144">**屬性**（第一次換行）</span><span class="sxs-lookup"><span data-stu-id="cc746-144">**Property** (first line)</span></span>  |   <span data-ttu-id="cc746-145">按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cc746-145">Click the field under **Property**, then select **BTS.MessageType** from the drop-down list.</span></span>   |
   |        <span data-ttu-id="cc746-146">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="cc746-146">**Operator**</span></span>        |                              <span data-ttu-id="cc746-147">選取  **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cc746-147">Select **==** from the drop-down list.</span></span>                              |
   |         <span data-ttu-id="cc746-148">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="cc746-148">**Value**</span></span>          |                <span data-ttu-id="cc746-149">型別**<http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF>**。</span><span class="sxs-lookup"><span data-stu-id="cc746-149">Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF>**.</span></span>                 |
   |        <span data-ttu-id="cc746-150">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="cc746-150">**Group By**</span></span>        |                              <span data-ttu-id="cc746-151">選取 **或**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cc746-151">Select **OR** from the drop-down list.</span></span>                              |
   | <span data-ttu-id="cc746-152">**屬性**（第二行）</span><span class="sxs-lookup"><span data-stu-id="cc746-152">**Property** (second line)</span></span> | <span data-ttu-id="cc746-153">按一下下方的欄位**屬性**，然後選取  **BTS。MessageType**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cc746-153">Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.</span></span> |
   |        <span data-ttu-id="cc746-154">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="cc746-154">**Operator**</span></span>        |                              <span data-ttu-id="cc746-155">選取  **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cc746-155">Select **==** from the drop-down list.</span></span>                              |
   |         <span data-ttu-id="cc746-156">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="cc746-156">**Value**</span></span>          |                <span data-ttu-id="cc746-157">型別 **<http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF>。**</span><span class="sxs-lookup"><span data-stu-id="cc746-157">Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF>.**</span></span>                 |
   |        <span data-ttu-id="cc746-158">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="cc746-158">**Group By**</span></span>        |                             <span data-ttu-id="cc746-159">選取 **和**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cc746-159">Select **And** from the drop-down list.</span></span>                              |
   | <span data-ttu-id="cc746-160">**屬性**（第三行）</span><span class="sxs-lookup"><span data-stu-id="cc746-160">**Property** (third line)</span></span>  |   <span data-ttu-id="cc746-161">按一下底下的第二列的欄位**屬性**，然後選取**BTAHL7Schemas.MSH5_1**。</span><span class="sxs-lookup"><span data-stu-id="cc746-161">Click the field on the second line under **Property**, then select **BTAHL7Schemas.MSH5_1**.</span></span>   |
   |        <span data-ttu-id="cc746-162">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="cc746-162">**Operator**</span></span>        |                              <span data-ttu-id="cc746-163">選取  **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="cc746-163">Select **==** from the drop-down list.</span></span>                              |
   |         <span data-ttu-id="cc746-164">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="cc746-164">**Value**</span></span>          |                                  <span data-ttu-id="cc746-165">型別**Tutorial_BatchSource**。</span><span class="sxs-lookup"><span data-stu-id="cc746-165">Type **Tutorial_BatchSource**.</span></span>                                  |

   > [!NOTE]
   >  <span data-ttu-id="cc746-166">第一個篩選條件，表示您訂閱的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="cc746-166">The first filter means that you are subscribing to the acknowledgment message.</span></span> <span data-ttu-id="cc746-167">第二個篩選條件，表示您想要聲明這具有的 「 發行者 」，目的地**Tutorial_BatchSource**。</span><span class="sxs-lookup"><span data-stu-id="cc746-167">The second filter means that you want the acknowledgment that has the destination of the publisher, **Tutorial_BatchSource**.</span></span>  

7. <span data-ttu-id="cc746-168">按一下 **[輸入]**。</span><span class="sxs-lookup"><span data-stu-id="cc746-168">Click **Enter**.</span></span> <span data-ttu-id="cc746-169">在對話方塊底部窗格中，確認您正確地輸入篩選運算式，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="cc746-169">In the pane at the bottom of the dialog box, verify that you entered the filter expression correctly, and then click **OK**.</span></span>  

8. <span data-ttu-id="cc746-170">在 管理主控台中，按一下**傳送埠**，以滑鼠右鍵按一下**Tutorial_2wayAck**，然後選取**啟動**。</span><span class="sxs-lookup"><span data-stu-id="cc746-170">In the Administration Console, click **Send Ports**, right-click **Tutorial_2wayAck**, and then select **Start**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="cc746-171">Tutorial_2wayAck 傳送埠才能正常，您必須啟用 TwoWayAckReceivePort 接收位置。</span><span class="sxs-lookup"><span data-stu-id="cc746-171">For the Tutorial_2wayAck send port to function properly, you must enable the TwoWayAckReceivePort receive location.</span></span>  

9. <span data-ttu-id="cc746-172">按一下 **接收位置**。</span><span class="sxs-lookup"><span data-stu-id="cc746-172">Click **Receive Locations**.</span></span> <span data-ttu-id="cc746-173">確認已啟用 TwoWayAckReceiveLocation 的狀態。</span><span class="sxs-lookup"><span data-stu-id="cc746-173">Verify that the status for the TwoWayAckReceiveLocation is enabled.</span></span> <span data-ttu-id="cc746-174">如果沒有，請以滑鼠右鍵按一下**TwoWayAckReceiveLocation**，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="cc746-174">If not, right-click **TwoWayAckReceiveLocation**, and then click **Enable**.</span></span>  

   <span data-ttu-id="cc746-175">請繼續進行[步驟 7： 建立和設定來源合作對象](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md)。</span><span class="sxs-lookup"><span data-stu-id="cc746-175">Proceed to [Step 7: Create and Configure a Source Party](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md).</span></span>