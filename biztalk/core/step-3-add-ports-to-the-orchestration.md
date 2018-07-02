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
# <a name="step-3-add-ports-to-the-orchestration"></a><span data-ttu-id="d01f8-102">步驟 3：將連接埠加入協調流程</span><span class="sxs-lookup"><span data-stu-id="d01f8-102">Step 3: Add Ports to the Orchestration</span></span>
<span data-ttu-id="d01f8-103">![步驟 4 之 3](../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="d01f8-103">![Step 3 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="d01f8-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="d01f8-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="d01f8-105">**目標：** 在此步驟中，您需要三個連接埠加入 EAIProcess 協調流程並設定它們。</span><span class="sxs-lookup"><span data-stu-id="d01f8-105">**Objective:** In this step, you add three ports to the EAIProcess orchestration and configure them.</span></span>  
  
 <span data-ttu-id="d01f8-106">**用途：** 連接埠指定如何協調流程會傳送和接收來自其他商務程序的訊息。</span><span class="sxs-lookup"><span data-stu-id="d01f8-106">**Purpose:** Ports specify how your orchestration will send messages to and receive messages from other business processes.</span></span> <span data-ttu-id="d01f8-107">每個連接埠都具有類型、方向和繫結，由這些決定通訊的方向、通訊的模式、傳送和接受訊息的位置，以及通訊進行的方式。</span><span class="sxs-lookup"><span data-stu-id="d01f8-107">Each port has a type, a direction, and a binding, which together determine the direction of communication, the pattern of communication, the location to or from which the message is sent or received, and how the communication takes place.</span></span> <span data-ttu-id="d01f8-108">您在此步驟中建立和設定的 3 個連接埠會執行下列角色：</span><span class="sxs-lookup"><span data-stu-id="d01f8-108">The three ports you create and configure in this step fulfill the following roles:</span></span>  
  
- <span data-ttu-id="d01f8-109">**ReceiveRequestPort**接收到倉儲庫存補充要求訊息。</span><span class="sxs-lookup"><span data-stu-id="d01f8-109">**ReceiveRequestPort** receives inventory replenishment request messages from the warehouse.</span></span>  
  
- <span data-ttu-id="d01f8-110">**SendToERP**要求將訊息轉送到 ERP 系統。</span><span class="sxs-lookup"><span data-stu-id="d01f8-110">**SendToERP** forwards the request messages to the ERP system.</span></span>  
  
- <span data-ttu-id="d01f8-111">**SendDeclinePort**傳送要求傳回至倉儲的拒絕訊息。</span><span class="sxs-lookup"><span data-stu-id="d01f8-111">**SendDeclinePort** sends request decline messages back to the warehouse.</span></span>  
  
  <span data-ttu-id="d01f8-112">如需詳細資訊，請參閱 <<c0> [ 協調流程中使用連接埠](../core/using-ports-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="d01f8-112">For more information, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d01f8-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="d01f8-113">Prerequisites</span></span>  
 <span data-ttu-id="d01f8-114">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="d01f8-114">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="d01f8-115">在開始此步驟之前必須先完成[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md)。</span><span class="sxs-lookup"><span data-stu-id="d01f8-115">Before you begin this step you must complete [Step 2: Define the Business Process](../core/step-2-define-the-business-process.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="d01f8-116">程序</span><span class="sxs-lookup"><span data-stu-id="d01f8-116">Procedures</span></span>  
  
#### <a name="to-create-and-configure-receiverequestport"></a><span data-ttu-id="d01f8-117">若要建立及設定 ReceiveRequestPort</span><span class="sxs-lookup"><span data-stu-id="d01f8-117">To create and configure ReceiveRequestPort</span></span>  
  
1.  <span data-ttu-id="d01f8-118">在 [方案總管] 中，按兩下**EAIProcess.odx**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-118">In Solution Explorer, double-click **EAIProcess.odx**.</span></span>  
  
2.  <span data-ttu-id="d01f8-119">在協調流程設計師中，從協調流程工具箱拖曳**連接埠**圖形以左側**連接埠介面**、 平行**ReceiveRequest**圖形。</span><span class="sxs-lookup"><span data-stu-id="d01f8-119">In Orchestration Designer, from the orchestration Toolbox, drag the **Port** shape to the left-side **Port Surface**, parallel to the **ReceiveRequest** shape.</span></span> <span data-ttu-id="d01f8-120">[連接埠組態精靈] 隨即自動啟動。</span><span class="sxs-lookup"><span data-stu-id="d01f8-120">The Port Configuration Wizard starts automatically.</span></span>  
  
3.  <span data-ttu-id="d01f8-121">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d01f8-121">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="d01f8-122">在 **連接埠內容**頁面上，執行下列作業，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-122">On the **Port Properties** page, do the following, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="d01f8-123">使用</span><span class="sxs-lookup"><span data-stu-id="d01f8-123">Use this</span></span>|<span data-ttu-id="d01f8-124">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="d01f8-124">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d01f8-125">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d01f8-125">**Name**</span></span>|<span data-ttu-id="d01f8-126">型別**ReceiveRequestPort**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-126">Type **ReceiveRequestPort**.</span></span>|  
  
5.  <span data-ttu-id="d01f8-127">在 **選取 連接埠類型**頁面上，執行下列作業，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-127">On the **Select a Port Type** page, do the following, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="d01f8-128">使用</span><span class="sxs-lookup"><span data-stu-id="d01f8-128">Use this</span></span>|<span data-ttu-id="d01f8-129">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="d01f8-129">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d01f8-130">**選取要用於此連接埠的連接埠類型**</span><span class="sxs-lookup"><span data-stu-id="d01f8-130">**Select the port type to be used for this port**</span></span>|<span data-ttu-id="d01f8-131">選取 **建立新的連接埠類型**選項。</span><span class="sxs-lookup"><span data-stu-id="d01f8-131">Select the **Create a new Port Type** option.</span></span>|  
    |<span data-ttu-id="d01f8-132">**連接埠類型名稱：**</span><span class="sxs-lookup"><span data-stu-id="d01f8-132">**Port Type Name:**</span></span>|<span data-ttu-id="d01f8-133">型別**ReceiveRequestPortType**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-133">Type **ReceiveRequestPortType**.</span></span>|  
    |<span data-ttu-id="d01f8-134">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="d01f8-134">**Communication Pattern**</span></span>|<span data-ttu-id="d01f8-135">選取 **單向**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-135">Select **One-Way**.</span></span>|  
    |<span data-ttu-id="d01f8-136">**存取限制**</span><span class="sxs-lookup"><span data-stu-id="d01f8-136">**Access Restrictions**</span></span>|<span data-ttu-id="d01f8-137">選取 **內部-限制於此專案**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-137">Select **Internal - limited to this project**.</span></span>|  
  
6.  <span data-ttu-id="d01f8-138">在 **連接埠繫結**頁面上，執行下列作業，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-138">On the **Port Binding** page, do the following, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="d01f8-139">使用</span><span class="sxs-lookup"><span data-stu-id="d01f8-139">Use this</span></span>|<span data-ttu-id="d01f8-140">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="d01f8-140">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d01f8-141">**連接埠通訊方向**</span><span class="sxs-lookup"><span data-stu-id="d01f8-141">**Port direction of communication**</span></span>|<span data-ttu-id="d01f8-142">選取 **我將一律接收訊息，在此連接埠**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-142">Select **I'll always be receiving messages on this port**.</span></span>|  
    |<span data-ttu-id="d01f8-143">**連接埠繫結**</span><span class="sxs-lookup"><span data-stu-id="d01f8-143">**Port binding**</span></span>|<span data-ttu-id="d01f8-144">從選取**稍後指定**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-144">From select **Specify later**.</span></span>|  
  
7.  <span data-ttu-id="d01f8-145">在 **完成連接埠精靈**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-145">On the **Completing the Port Wizard** page, click **Finish**.</span></span>  
  
#### <a name="to-create-and-configure-senddeclineport"></a><span data-ttu-id="d01f8-146">若要建立和設定 SendDeclinePort</span><span class="sxs-lookup"><span data-stu-id="d01f8-146">To create and configure SendDeclinePort</span></span>  
  
1.  <span data-ttu-id="d01f8-147">從協調流程 [工具箱] 中，拖曳**連接埠**圖形以左側**連接埠介面**、 平行**SendRequestDecline**圖形。</span><span class="sxs-lookup"><span data-stu-id="d01f8-147">From the orchestration Toolbox, drag the **Port** shape to the left-side **Port Surface**, parallel to the **SendRequestDecline** shape.</span></span>  
  
2.  <span data-ttu-id="d01f8-148">使用下表中的資訊，來建立**SendDeclinePort**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d01f8-148">Use the information in the following table to create the **SendDeclinePort** send port.</span></span>  
  
    |<span data-ttu-id="d01f8-149">屬性</span><span class="sxs-lookup"><span data-stu-id="d01f8-149">Property</span></span>|<span data-ttu-id="d01f8-150">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="d01f8-150">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="d01f8-151">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d01f8-151">**Name**</span></span>|<span data-ttu-id="d01f8-152">型別**SendDeclinePort**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-152">Type **SendDeclinePort**.</span></span>|  
    |<span data-ttu-id="d01f8-153">**選取要用於此連接埠的連接埠類型**</span><span class="sxs-lookup"><span data-stu-id="d01f8-153">**Select the port type to be used for this port**</span></span>|<span data-ttu-id="d01f8-154">選取 **建立新的連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-154">Select **Create a new Port Type**.</span></span>|  
    |<span data-ttu-id="d01f8-155">**連接埠類型名稱**</span><span class="sxs-lookup"><span data-stu-id="d01f8-155">**Port Type Name**</span></span>|<span data-ttu-id="d01f8-156">型別**SendDeclinePortType**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-156">Type **SendDeclinePortType**.</span></span>|  
    |<span data-ttu-id="d01f8-157">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="d01f8-157">**Communication Pattern**</span></span>|<span data-ttu-id="d01f8-158">選取 **單向**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-158">Select **One-Way**.</span></span>|  
    |<span data-ttu-id="d01f8-159">**存取限制**</span><span class="sxs-lookup"><span data-stu-id="d01f8-159">**Access Restrictions**</span></span>|<span data-ttu-id="d01f8-160">選取 **內部-限制於此專案**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-160">Select **Internal - limited to this project**.</span></span>|  
    |<span data-ttu-id="d01f8-161">**連接埠通訊方向**</span><span class="sxs-lookup"><span data-stu-id="d01f8-161">**Port direction of communication**</span></span>|<span data-ttu-id="d01f8-162">從下拉式清單中，選取**我將總是傳送的訊息在此連接埠**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-162">From the drop-down list, select **I'll always be sending messages on this port**.</span></span>|  
    |<span data-ttu-id="d01f8-163">**連接埠繫結**</span><span class="sxs-lookup"><span data-stu-id="d01f8-163">**Port bindings**</span></span>|<span data-ttu-id="d01f8-164">從下拉式清單中，選取**稍後指定**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-164">From the drop-down list, select **Specify later**.</span></span>|  
  
#### <a name="to-create-and-configure-sendtoerpport"></a><span data-ttu-id="d01f8-165">若要建立和設定 SendToERPPort</span><span class="sxs-lookup"><span data-stu-id="d01f8-165">To create and configure SendToERPPort</span></span>  
  
1.  <span data-ttu-id="d01f8-166">從協調流程 [工具箱] 中，拖曳**連接埠**右側的圖形**連接埠介面**、 平行**SendToERP**圖形。</span><span class="sxs-lookup"><span data-stu-id="d01f8-166">From the orchestration Toolbox, drag the **Port** shape to the right-side **Port Surface**, parallel to the **SendToERP** shape.</span></span>  
  
2.  <span data-ttu-id="d01f8-167">使用下表中的資訊，完成連接埠組態精靈**SendToERP**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d01f8-167">Use the information in the following table to complete the Port Configuration Wizard for the **SendToERP** send port.</span></span>  
  
    |<span data-ttu-id="d01f8-168">屬性</span><span class="sxs-lookup"><span data-stu-id="d01f8-168">Property</span></span>|<span data-ttu-id="d01f8-169">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="d01f8-169">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="d01f8-170">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d01f8-170">**Name**</span></span>|<span data-ttu-id="d01f8-171">型別**SendToERPPort**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-171">Type **SendToERPPort**.</span></span>|  
    |<span data-ttu-id="d01f8-172">**選取要用於此連接埠的連接埠類型**</span><span class="sxs-lookup"><span data-stu-id="d01f8-172">**Select the port type to be used for this port**</span></span>|<span data-ttu-id="d01f8-173">選取 **建立新的連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-173">Select **Create a new Port Type**.</span></span>|  
    |<span data-ttu-id="d01f8-174">**連接埠類型名稱**</span><span class="sxs-lookup"><span data-stu-id="d01f8-174">**Port Type Name**</span></span>|<span data-ttu-id="d01f8-175">型別**SendToERPPortType**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-175">Type **SendToERPPortType**.</span></span>|  
    |<span data-ttu-id="d01f8-176">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="d01f8-176">**Communication Pattern**</span></span>|<span data-ttu-id="d01f8-177">選取 **單向**選項。</span><span class="sxs-lookup"><span data-stu-id="d01f8-177">Select the **One-Way** option.</span></span>|  
    |<span data-ttu-id="d01f8-178">**存取限制**</span><span class="sxs-lookup"><span data-stu-id="d01f8-178">**Access Restrictions**</span></span>|<span data-ttu-id="d01f8-179">選取 **內部-限制於此專案**選項。</span><span class="sxs-lookup"><span data-stu-id="d01f8-179">Select the **Internal - limited to this project** option.</span></span>|  
    |<span data-ttu-id="d01f8-180">**連接埠通訊方向**</span><span class="sxs-lookup"><span data-stu-id="d01f8-180">**Port direction of communication**</span></span>|<span data-ttu-id="d01f8-181">從下拉式清單中，選取**我將總是傳送的訊息在此連接埠**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-181">From the drop-down list, select **I'll always be sending messages on this port**.</span></span>|  
    |<span data-ttu-id="d01f8-182">**連接埠繫結**</span><span class="sxs-lookup"><span data-stu-id="d01f8-182">**Port binding**</span></span>|<span data-ttu-id="d01f8-183">從下拉式清單中，選取**稍後指定**。</span><span class="sxs-lookup"><span data-stu-id="d01f8-183">From the drop-down list, select **Specify later**.</span></span>|  
  
#### <a name="to-connect-the-ports-to-the-action-shapes"></a><span data-ttu-id="d01f8-184">將連接埠連接到動作圖形</span><span class="sxs-lookup"><span data-stu-id="d01f8-184">To connect the ports to the action shapes</span></span>  
  
-   <span data-ttu-id="d01f8-185">在協調流程設計師的設計介面中，將每個連接埠的綠色箭頭圖形控點拖曳至動作圖形的對應綠色控點：</span><span class="sxs-lookup"><span data-stu-id="d01f8-185">In Orchestration Designer, on the design surface, drag the green arrow-shaped handle for each port to the corresponding green handle of the action shape:</span></span>  
  
    |<span data-ttu-id="d01f8-186">連接此連接埠</span><span class="sxs-lookup"><span data-stu-id="d01f8-186">Connect this port</span></span>|<span data-ttu-id="d01f8-187">至此動作圖形</span><span class="sxs-lookup"><span data-stu-id="d01f8-187">To this action shape</span></span>|  
    |-----------------------|--------------------------|  
    |<span data-ttu-id="d01f8-188">**ReceiveReqPort**</span><span class="sxs-lookup"><span data-stu-id="d01f8-188">**ReceiveReqPort**</span></span>|<span data-ttu-id="d01f8-189">**[Receive_request]**</span><span class="sxs-lookup"><span data-stu-id="d01f8-189">**Receive_Request**</span></span>|  
    |<span data-ttu-id="d01f8-190">**SendDeclinePort**</span><span class="sxs-lookup"><span data-stu-id="d01f8-190">**SendDeclinePort**</span></span>|<span data-ttu-id="d01f8-191">**Send_ReqDenied**</span><span class="sxs-lookup"><span data-stu-id="d01f8-191">**Send_ReqDenied**</span></span>|  
    |<span data-ttu-id="d01f8-192">**SendToERP**</span><span class="sxs-lookup"><span data-stu-id="d01f8-192">**SendToERP**</span></span>|<span data-ttu-id="d01f8-193">**Send_ReqToERP**</span><span class="sxs-lookup"><span data-stu-id="d01f8-193">**Send_ReqToERP**</span></span>|  
  
     <span data-ttu-id="d01f8-194">下圖顯示 EAIProcess 協調流程與所有連接的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d01f8-194">The following figure shows the EAIProcess orchestration with all of the ports connected.</span></span>  
  
     <span data-ttu-id="d01f8-195">![具有連接的連接埠的 EAIProcess 協調流程。] (../core/media/tut1-eaiprocessportsconnected.gif "Tut1_EAIProcessPortsConnected")</span><span class="sxs-lookup"><span data-stu-id="d01f8-195">![EAIProcess orchestration with connected ports.](../core/media/tut1-eaiprocessportsconnected.gif "Tut1_EAIProcessPortsConnected")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="d01f8-196">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="d01f8-196">What did I just do?</span></span>  
 <span data-ttu-id="d01f8-197">在此步驟中，您新增了三個連接埠到 EAIProcess 協調流程，並且加以設定。</span><span class="sxs-lookup"><span data-stu-id="d01f8-197">In this step, you added three ports to the EAIProcess orchestration and configured them.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d01f8-198">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d01f8-198">Next Steps</span></span>  
 <span data-ttu-id="d01f8-199">您建置專案[步驟 4： 建置 EAIOrchestration 專案](../core/step-4-build-the-eaiorchestration-project.md)。</span><span class="sxs-lookup"><span data-stu-id="d01f8-199">You build the project in [Step 4: Build the EAIOrchestration Project](../core/step-4-build-the-eaiorchestration-project.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d01f8-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d01f8-200">See Also</span></span>  
 <span data-ttu-id="d01f8-201">[步驟 1： 將 EAIOrchestration 專案加入方案](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span><span class="sxs-lookup"><span data-stu-id="d01f8-201">[Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span></span>  
 <span data-ttu-id="d01f8-202">[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md) </span><span class="sxs-lookup"><span data-stu-id="d01f8-202">[Step 2: Define the Business Process](../core/step-2-define-the-business-process.md) </span></span>  
 [<span data-ttu-id="d01f8-203">步驟 4：建置 EAIOrchestration 專案</span><span class="sxs-lookup"><span data-stu-id="d01f8-203">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)