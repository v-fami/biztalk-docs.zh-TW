---
title: 步驟 3： 新增至協調流程的連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 245df16e-d327-4c79-be85-004134d5ea6f
caps.latest.revision: 45
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b42c91be94663f1061d3bbda31267db21988157
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968615"
---
# <a name="step-3-add-ports-to-the-orchestration"></a><span data-ttu-id="fecab-102">步驟 3：將連接埠加入協調流程</span><span class="sxs-lookup"><span data-stu-id="fecab-102">Step 3: Add Ports to the Orchestration</span></span>
<span data-ttu-id="fecab-103">![步驟 4 之 3](../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="fecab-103">![Step 3 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="fecab-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="fecab-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="fecab-105">**目標：** 在此步驟中，您需要三個連接埠加入 EAIProcess 協調流程並設定它們。</span><span class="sxs-lookup"><span data-stu-id="fecab-105">**Objective:** In this step, you add three ports to the EAIProcess orchestration and configure them.</span></span>  
  
 <span data-ttu-id="fecab-106">**用途：** 連接埠指定如何協調流程會傳送和接收來自其他商務程序的訊息。</span><span class="sxs-lookup"><span data-stu-id="fecab-106">**Purpose:** Ports specify how your orchestration will send messages to and receive messages from other business processes.</span></span> <span data-ttu-id="fecab-107">每個連接埠都具有類型、方向和繫結，由這些決定通訊的方向、通訊的模式、傳送和接受訊息的位置，以及通訊進行的方式。</span><span class="sxs-lookup"><span data-stu-id="fecab-107">Each port has a type, a direction, and a binding, which together determine the direction of communication, the pattern of communication, the location to or from which the message is sent or received, and how the communication takes place.</span></span> <span data-ttu-id="fecab-108">您在此步驟中建立和設定的 3 個連接埠會執行下列角色：</span><span class="sxs-lookup"><span data-stu-id="fecab-108">The three ports you create and configure in this step fulfill the following roles:</span></span>  
  
- <span data-ttu-id="fecab-109">**ReceiveRequestPort**接收到倉儲庫存補充要求訊息。</span><span class="sxs-lookup"><span data-stu-id="fecab-109">**ReceiveRequestPort** receives inventory replenishment request messages from the warehouse.</span></span>  
  
- <span data-ttu-id="fecab-110">**SendToERP**要求將訊息轉送到 ERP 系統。</span><span class="sxs-lookup"><span data-stu-id="fecab-110">**SendToERP** forwards the request messages to the ERP system.</span></span>  
  
- <span data-ttu-id="fecab-111">**SendDeclinePort**傳送要求傳回至倉儲的拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="fecab-111">**SendDeclinePort** sends request decline messages back to the warehouse.</span></span>  
  
  <span data-ttu-id="fecab-112">如需詳細資訊，請參閱 <<c0> [ 協調流程中使用連接埠](../core/using-ports-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="fecab-112">For more information, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fecab-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="fecab-113">Prerequisites</span></span>  
 <span data-ttu-id="fecab-114">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="fecab-114">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="fecab-115">在開始此步驟之前必須先完成[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md)。</span><span class="sxs-lookup"><span data-stu-id="fecab-115">Before you begin this step you must complete [Step 2: Define the Business Process](../core/step-2-define-the-business-process.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="fecab-116">程序</span><span class="sxs-lookup"><span data-stu-id="fecab-116">Procedures</span></span>  
  
#### <a name="to-create-and-configure-receiverequestport"></a><span data-ttu-id="fecab-117">若要建立及設定 ReceiveRequestPort</span><span class="sxs-lookup"><span data-stu-id="fecab-117">To create and configure ReceiveRequestPort</span></span>  
  
1.  <span data-ttu-id="fecab-118">在 [方案總管] 中，按兩下**EAIProcess.odx**。</span><span class="sxs-lookup"><span data-stu-id="fecab-118">In Solution Explorer, double-click **EAIProcess.odx**.</span></span>  
  
2.  <span data-ttu-id="fecab-119">在協調流程設計師中，從協調流程工具箱拖曳**連接埠**圖形以左側**連接埠介面**、 平行**ReceiveRequest**圖形。</span><span class="sxs-lookup"><span data-stu-id="fecab-119">In Orchestration Designer, from the orchestration Toolbox, drag the **Port** shape to the left-side **Port Surface**, parallel to the **ReceiveRequest** shape.</span></span> <span data-ttu-id="fecab-120">[連接埠組態精靈] 隨即自動啟動。</span><span class="sxs-lookup"><span data-stu-id="fecab-120">The Port Configuration Wizard starts automatically.</span></span>  
  
3.  <span data-ttu-id="fecab-121">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fecab-121">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="fecab-122">在 **連接埠內容**頁面上，執行下列作業，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="fecab-122">On the **Port Properties** page, do the following, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="fecab-123">使用</span><span class="sxs-lookup"><span data-stu-id="fecab-123">Use this</span></span>|<span data-ttu-id="fecab-124">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="fecab-124">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fecab-125">**名稱**</span><span class="sxs-lookup"><span data-stu-id="fecab-125">**Name**</span></span>|<span data-ttu-id="fecab-126">型別**ReceiveRequestPort**。</span><span class="sxs-lookup"><span data-stu-id="fecab-126">Type **ReceiveRequestPort**.</span></span>|  
  
5.  <span data-ttu-id="fecab-127">在 **選取 連接埠類型**頁面上，執行下列作業，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="fecab-127">On the **Select a Port Type** page, do the following, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="fecab-128">使用</span><span class="sxs-lookup"><span data-stu-id="fecab-128">Use this</span></span>|<span data-ttu-id="fecab-129">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="fecab-129">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fecab-130">**選取要用於此連接埠的連接埠類型**</span><span class="sxs-lookup"><span data-stu-id="fecab-130">**Select the port type to be used for this port**</span></span>|<span data-ttu-id="fecab-131">選取 **建立新的連接埠類型**選項。</span><span class="sxs-lookup"><span data-stu-id="fecab-131">Select the **Create a new Port Type** option.</span></span>|  
    |<span data-ttu-id="fecab-132">**連接埠類型名稱：**</span><span class="sxs-lookup"><span data-stu-id="fecab-132">**Port Type Name:**</span></span>|<span data-ttu-id="fecab-133">型別**ReceiveRequestPortType**。</span><span class="sxs-lookup"><span data-stu-id="fecab-133">Type **ReceiveRequestPortType**.</span></span>|  
    |<span data-ttu-id="fecab-134">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="fecab-134">**Communication Pattern**</span></span>|<span data-ttu-id="fecab-135">選取 **單向**。</span><span class="sxs-lookup"><span data-stu-id="fecab-135">Select **One-Way**.</span></span>|  
    |<span data-ttu-id="fecab-136">**存取限制**</span><span class="sxs-lookup"><span data-stu-id="fecab-136">**Access Restrictions**</span></span>|<span data-ttu-id="fecab-137">選取 **內部-限制於此專案**。</span><span class="sxs-lookup"><span data-stu-id="fecab-137">Select **Internal - limited to this project**.</span></span>|  
  
6.  <span data-ttu-id="fecab-138">在 **連接埠繫結**頁面上，執行下列作業，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="fecab-138">On the **Port Binding** page, do the following, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="fecab-139">使用</span><span class="sxs-lookup"><span data-stu-id="fecab-139">Use this</span></span>|<span data-ttu-id="fecab-140">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="fecab-140">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fecab-141">**連接埠通訊方向**</span><span class="sxs-lookup"><span data-stu-id="fecab-141">**Port direction of communication**</span></span>|<span data-ttu-id="fecab-142">選取 **我將一律接收訊息，在此連接埠**。</span><span class="sxs-lookup"><span data-stu-id="fecab-142">Select **I'll always be receiving messages on this port**.</span></span>|  
    |<span data-ttu-id="fecab-143">**連接埠繫結**</span><span class="sxs-lookup"><span data-stu-id="fecab-143">**Port binding**</span></span>|<span data-ttu-id="fecab-144">從選取**稍後指定**。</span><span class="sxs-lookup"><span data-stu-id="fecab-144">From select **Specify later**.</span></span>|  
  
7.  <span data-ttu-id="fecab-145">在 **完成連接埠精靈**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="fecab-145">On the **Completing the Port Wizard** page, click **Finish**.</span></span>  
  
#### <a name="to-create-and-configure-senddeclineport"></a><span data-ttu-id="fecab-146">若要建立和設定 SendDeclinePort</span><span class="sxs-lookup"><span data-stu-id="fecab-146">To create and configure SendDeclinePort</span></span>  
  
1.  <span data-ttu-id="fecab-147">從協調流程 [工具箱] 中，拖曳**連接埠**圖形以左側**連接埠介面**、 平行**SendRequestDecline**圖形。</span><span class="sxs-lookup"><span data-stu-id="fecab-147">From the orchestration Toolbox, drag the **Port** shape to the left-side **Port Surface**, parallel to the **SendRequestDecline** shape.</span></span>  
  
2.  <span data-ttu-id="fecab-148">使用下表中的資訊，來建立**SendDeclinePort**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="fecab-148">Use the information in the following table to create the **SendDeclinePort** send port.</span></span>  
  
    |<span data-ttu-id="fecab-149">屬性</span><span class="sxs-lookup"><span data-stu-id="fecab-149">Property</span></span>|<span data-ttu-id="fecab-150">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="fecab-150">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="fecab-151">**名稱**</span><span class="sxs-lookup"><span data-stu-id="fecab-151">**Name**</span></span>|<span data-ttu-id="fecab-152">型別**SendDeclinePort**。</span><span class="sxs-lookup"><span data-stu-id="fecab-152">Type **SendDeclinePort**.</span></span>|  
    |<span data-ttu-id="fecab-153">**選取要用於此連接埠的連接埠類型**</span><span class="sxs-lookup"><span data-stu-id="fecab-153">**Select the port type to be used for this port**</span></span>|<span data-ttu-id="fecab-154">選取 **建立新的連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="fecab-154">Select **Create a new Port Type**.</span></span>|  
    |<span data-ttu-id="fecab-155">**連接埠類型名稱**</span><span class="sxs-lookup"><span data-stu-id="fecab-155">**Port Type Name**</span></span>|<span data-ttu-id="fecab-156">型別**SendDeclinePortType**。</span><span class="sxs-lookup"><span data-stu-id="fecab-156">Type **SendDeclinePortType**.</span></span>|  
    |<span data-ttu-id="fecab-157">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="fecab-157">**Communication Pattern**</span></span>|<span data-ttu-id="fecab-158">選取 **單向**。</span><span class="sxs-lookup"><span data-stu-id="fecab-158">Select **One-Way**.</span></span>|  
    |<span data-ttu-id="fecab-159">**存取限制**</span><span class="sxs-lookup"><span data-stu-id="fecab-159">**Access Restrictions**</span></span>|<span data-ttu-id="fecab-160">選取 **內部-限制於此專案**。</span><span class="sxs-lookup"><span data-stu-id="fecab-160">Select **Internal - limited to this project**.</span></span>|  
    |<span data-ttu-id="fecab-161">**連接埠通訊方向**</span><span class="sxs-lookup"><span data-stu-id="fecab-161">**Port direction of communication**</span></span>|<span data-ttu-id="fecab-162">從下拉式清單中，選取**我將總是傳送的訊息在此連接埠**。</span><span class="sxs-lookup"><span data-stu-id="fecab-162">From the drop-down list, select **I'll always be sending messages on this port**.</span></span>|  
    |<span data-ttu-id="fecab-163">**連接埠繫結**</span><span class="sxs-lookup"><span data-stu-id="fecab-163">**Port bindings**</span></span>|<span data-ttu-id="fecab-164">從下拉式清單中，選取**稍後指定**。</span><span class="sxs-lookup"><span data-stu-id="fecab-164">From the drop-down list, select **Specify later**.</span></span>|  
  
#### <a name="to-create-and-configure-sendtoerpport"></a><span data-ttu-id="fecab-165">若要建立和設定 SendToERPPort</span><span class="sxs-lookup"><span data-stu-id="fecab-165">To create and configure SendToERPPort</span></span>  
  
1.  <span data-ttu-id="fecab-166">從協調流程 [工具箱] 中，拖曳**連接埠**右側的圖形**連接埠介面**、 平行**SendToERP**圖形。</span><span class="sxs-lookup"><span data-stu-id="fecab-166">From the orchestration Toolbox, drag the **Port** shape to the right-side **Port Surface**, parallel to the **SendToERP** shape.</span></span>  
  
2.  <span data-ttu-id="fecab-167">使用下表中的資訊，完成連接埠組態精靈**SendToERP**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="fecab-167">Use the information in the following table to complete the Port Configuration Wizard for the **SendToERP** send port.</span></span>  
  
    |<span data-ttu-id="fecab-168">屬性</span><span class="sxs-lookup"><span data-stu-id="fecab-168">Property</span></span>|<span data-ttu-id="fecab-169">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="fecab-169">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="fecab-170">**名稱**</span><span class="sxs-lookup"><span data-stu-id="fecab-170">**Name**</span></span>|<span data-ttu-id="fecab-171">型別**SendToERPPort**。</span><span class="sxs-lookup"><span data-stu-id="fecab-171">Type **SendToERPPort**.</span></span>|  
    |<span data-ttu-id="fecab-172">**選取要用於此連接埠的連接埠類型**</span><span class="sxs-lookup"><span data-stu-id="fecab-172">**Select the port type to be used for this port**</span></span>|<span data-ttu-id="fecab-173">選取 **建立新的連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="fecab-173">Select **Create a new Port Type**.</span></span>|  
    |<span data-ttu-id="fecab-174">**連接埠類型名稱**</span><span class="sxs-lookup"><span data-stu-id="fecab-174">**Port Type Name**</span></span>|<span data-ttu-id="fecab-175">型別**SendToERPPortType**。</span><span class="sxs-lookup"><span data-stu-id="fecab-175">Type **SendToERPPortType**.</span></span>|  
    |<span data-ttu-id="fecab-176">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="fecab-176">**Communication Pattern**</span></span>|<span data-ttu-id="fecab-177">選取 **單向**選項。</span><span class="sxs-lookup"><span data-stu-id="fecab-177">Select the **One-Way** option.</span></span>|  
    |<span data-ttu-id="fecab-178">**存取限制**</span><span class="sxs-lookup"><span data-stu-id="fecab-178">**Access Restrictions**</span></span>|<span data-ttu-id="fecab-179">選取 **內部-限制於此專案**選項。</span><span class="sxs-lookup"><span data-stu-id="fecab-179">Select the **Internal - limited to this project** option.</span></span>|  
    |<span data-ttu-id="fecab-180">**連接埠通訊方向**</span><span class="sxs-lookup"><span data-stu-id="fecab-180">**Port direction of communication**</span></span>|<span data-ttu-id="fecab-181">從下拉式清單中，選取**我將總是傳送的訊息在此連接埠**。</span><span class="sxs-lookup"><span data-stu-id="fecab-181">From the drop-down list, select **I'll always be sending messages on this port**.</span></span>|  
    |<span data-ttu-id="fecab-182">**連接埠繫結**</span><span class="sxs-lookup"><span data-stu-id="fecab-182">**Port binding**</span></span>|<span data-ttu-id="fecab-183">從下拉式清單中，選取**稍後指定**。</span><span class="sxs-lookup"><span data-stu-id="fecab-183">From the drop-down list, select **Specify later**.</span></span>|  
  
#### <a name="to-connect-the-ports-to-the-action-shapes"></a><span data-ttu-id="fecab-184">將連接埠連接到動作圖形</span><span class="sxs-lookup"><span data-stu-id="fecab-184">To connect the ports to the action shapes</span></span>  
  
-   <span data-ttu-id="fecab-185">在協調流程設計師的設計介面中，將每個連接埠的綠色箭頭圖形控點拖曳至動作圖形的對應綠色控點：</span><span class="sxs-lookup"><span data-stu-id="fecab-185">In Orchestration Designer, on the design surface, drag the green arrow-shaped handle for each port to the corresponding green handle of the action shape:</span></span>  
  
    |<span data-ttu-id="fecab-186">連接此連接埠</span><span class="sxs-lookup"><span data-stu-id="fecab-186">Connect this port</span></span>|<span data-ttu-id="fecab-187">至此動作圖形</span><span class="sxs-lookup"><span data-stu-id="fecab-187">To this action shape</span></span>|  
    |-----------------------|--------------------------|  
    |<span data-ttu-id="fecab-188">**ReceiveReqPort**</span><span class="sxs-lookup"><span data-stu-id="fecab-188">**ReceiveReqPort**</span></span>|<span data-ttu-id="fecab-189">**[Receive_request]**</span><span class="sxs-lookup"><span data-stu-id="fecab-189">**Receive_Request**</span></span>|  
    |<span data-ttu-id="fecab-190">**SendDeclinePort**</span><span class="sxs-lookup"><span data-stu-id="fecab-190">**SendDeclinePort**</span></span>|<span data-ttu-id="fecab-191">**Send_ReqDenied**</span><span class="sxs-lookup"><span data-stu-id="fecab-191">**Send_ReqDenied**</span></span>|  
    |<span data-ttu-id="fecab-192">**SendToERP**</span><span class="sxs-lookup"><span data-stu-id="fecab-192">**SendToERP**</span></span>|<span data-ttu-id="fecab-193">**Send_ReqToERP**</span><span class="sxs-lookup"><span data-stu-id="fecab-193">**Send_ReqToERP**</span></span>|  
  
     <span data-ttu-id="fecab-194">下圖顯示 EAIProcess 協調流程與所有連接的連接埠。</span><span class="sxs-lookup"><span data-stu-id="fecab-194">The following figure shows the EAIProcess orchestration with all of the ports connected.</span></span>  
  
     <span data-ttu-id="fecab-195">![具有連接的連接埠的 EAIProcess 協調流程。](../core/media/tut1-eaiprocessportsconnected.gif "Tut1_EAIProcessPortsConnected")</span><span class="sxs-lookup"><span data-stu-id="fecab-195">![EAIProcess orchestration with connected ports.](../core/media/tut1-eaiprocessportsconnected.gif "Tut1_EAIProcessPortsConnected")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="fecab-196">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="fecab-196">What did I just do?</span></span>  
 <span data-ttu-id="fecab-197">在此步驟中，您新增了三個連接埠到 EAIProcess 協調流程，並且加以設定。</span><span class="sxs-lookup"><span data-stu-id="fecab-197">In this step, you added three ports to the EAIProcess orchestration and configured them.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fecab-198">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fecab-198">Next Steps</span></span>  
 <span data-ttu-id="fecab-199">您建置專案[步驟 4： 建置 EAIOrchestration 專案](../core/step-4-build-the-eaiorchestration-project.md)。</span><span class="sxs-lookup"><span data-stu-id="fecab-199">You build the project in [Step 4: Build the EAIOrchestration Project](../core/step-4-build-the-eaiorchestration-project.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fecab-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fecab-200">See Also</span></span>  
 <span data-ttu-id="fecab-201">[步驟 1： 將 EAIOrchestration 專案加入方案](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span><span class="sxs-lookup"><span data-stu-id="fecab-201">[Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span></span>  
 <span data-ttu-id="fecab-202">[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md) </span><span class="sxs-lookup"><span data-stu-id="fecab-202">[Step 2: Define the Business Process](../core/step-2-define-the-business-process.md) </span></span>  
 [<span data-ttu-id="fecab-203">步驟 4：建置 EAIOrchestration 專案</span><span class="sxs-lookup"><span data-stu-id="fecab-203">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)