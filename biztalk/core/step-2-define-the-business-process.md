---
title: "步驟 2： 定義商務程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b37bd9f1-5ee2-434d-950a-cf12967b6fc2
caps.latest.revision: "49"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17f181933daac5170c517a23f809eb97b54f2900
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-define-the-business-process"></a><span data-ttu-id="d5309-102">步驟 2：定義商務程序</span><span class="sxs-lookup"><span data-stu-id="d5309-102">Step 2: Define the Business Process</span></span>
<span data-ttu-id="d5309-103">![步驟 4 之 2](../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="d5309-103">![Step 2 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="d5309-104">**若要完成的時間：** 8 分鐘</span><span class="sxs-lookup"><span data-stu-id="d5309-104">**Time to complete:** 8 minutes</span></span>  
  
 <span data-ttu-id="d5309-105">**目標：**在此步驟中，您可以使用協調流程設計師 」 定義商務程序。</span><span class="sxs-lookup"><span data-stu-id="d5309-105">**Objective:** In this step, you use Orchestration Designer to define your business process.</span></span>  
  
 <span data-ttu-id="d5309-106">**用途：**協調流程的工作流程代表及自動化您的公司核准庫存補充要求的商務程序。</span><span class="sxs-lookup"><span data-stu-id="d5309-106">**Purpose:** The workflow of the orchestration represents and automates your company's business process for approving inventory replenishment requests.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d5309-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="d5309-107">Prerequisites</span></span>  
 <span data-ttu-id="d5309-108">開始此步驟之前，請注意下列需求：</span><span class="sxs-lookup"><span data-stu-id="d5309-108">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="d5309-109">在開始此步驟之前必須先完成[步驟 1： 將 EAIOrchestration 專案加入方案](../core/step-1-add-eaiorchestration-project-to-the-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="d5309-109">Before you begin this step you must complete [Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="d5309-110">程序</span><span class="sxs-lookup"><span data-stu-id="d5309-110">Procedures</span></span>  
 <span data-ttu-id="d5309-111">開發協調流程的第一個步驟是使用動作圖形來表示商務程序。</span><span class="sxs-lookup"><span data-stu-id="d5309-111">The first step for developing an orchestration is to use action shapes to represent the business process.</span></span>  
  
#### <a name="to-create-the-eai-business-process-workflow"></a><span data-ttu-id="d5309-112">建立 EAI 商務程序工作流程</span><span class="sxs-lookup"><span data-stu-id="d5309-112">To create the EAI business process workflow</span></span>  
  
1.  <span data-ttu-id="d5309-113">從 Visual Studio，在 方案總管 中，按兩下  **EAIProcess.odx**開啟協調流程。</span><span class="sxs-lookup"><span data-stu-id="d5309-113">From Visual Studio, in Solution Explorer, double-click **EAIProcess.odx** to open the orchestration.</span></span>  
  
2.  <span data-ttu-id="d5309-114">在協調流程設計師中，從協調流程工具箱拖曳**接收**圖形，然後放之間**開始**（綠色圓形） 和**結束**（紅色八角形） 圖形。</span><span class="sxs-lookup"><span data-stu-id="d5309-114">In Orchestration Designer, from the orchestration Toolbox, drag the **Receive** shape, and drop it between the **Begin** (green circle) and **End** (red octagon) shapes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5309-115">如果 工具箱 無法開啟，請在**檢視**功能表上，按一下 **工具箱**。</span><span class="sxs-lookup"><span data-stu-id="d5309-115">If the Toolbox is not open, in the **View** menu, click **Toolbox**.</span></span> <span data-ttu-id="d5309-116">若要將它錨定在畫面上，請按一下圖釘圖示。</span><span class="sxs-lookup"><span data-stu-id="d5309-116">To anchor it on the screen, click the thumbtack icon.</span></span>  
  
3.  <span data-ttu-id="d5309-117">從工具箱 拖曳**決定**圖形 接收 圖形下方。</span><span class="sxs-lookup"><span data-stu-id="d5309-117">From the toolbox, drag the **Decide** shape beneath the Receive shape.</span></span>  
  
4.  <span data-ttu-id="d5309-118">從工具箱 拖曳**轉換**「 決定 」 圖形的左邊分支的圖形。</span><span class="sxs-lookup"><span data-stu-id="d5309-118">From the toolbox, drag the **Transform** shape to the left branch of the Decide shape.</span></span> <span data-ttu-id="d5309-119">[轉換] 圖形會以巢狀結構位於 [建構訊息] 圖形內。</span><span class="sxs-lookup"><span data-stu-id="d5309-119">The Transform shape is nested inside the Construct Message shape.</span></span>  
  
5.  <span data-ttu-id="d5309-120">從工具箱 拖曳**傳送**圖形 轉換 圖形下方。</span><span class="sxs-lookup"><span data-stu-id="d5309-120">From the toolbox, drag the **Send** shape beneath the Transform shape.</span></span>  
  
6.  <span data-ttu-id="d5309-121">從工具箱 拖曳**傳送**圖形以 「 決定 」 圖形的右邊分支。</span><span class="sxs-lookup"><span data-stu-id="d5309-121">From the toolbox, drag the **Send** shape to the right branch of the Decide shape.</span></span>  <span data-ttu-id="d5309-122">在您新增動作圖形之後，協調流程看起來就像下面一樣：</span><span class="sxs-lookup"><span data-stu-id="d5309-122">The orchestration looks like the following after you added the action shapes:</span></span>  
  
     <span data-ttu-id="d5309-123">![EAI 程序](../core/media/eaiprocess.gif "EAIProcess")</span><span class="sxs-lookup"><span data-stu-id="d5309-123">![EAI process](../core/media/eaiprocess.gif "EAIProcess")</span></span>  
  
 <span data-ttu-id="d5309-124">下一個步驟是定義訊息變數。</span><span class="sxs-lookup"><span data-stu-id="d5309-124">The next step is to define message variables.</span></span>  <span data-ttu-id="d5309-125">幾個動作圖形有一個需要指定的訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="d5309-125">Several action shapes have a message property that needs to be specified.</span></span>  
  
#### <a name="to-define-message-variables"></a><span data-ttu-id="d5309-126">若要定義訊息變數</span><span class="sxs-lookup"><span data-stu-id="d5309-126">To define message variables</span></span>  
  
1.  <span data-ttu-id="d5309-127">從 Visual Studio 中，按一下 **檢視**功能表上，按一下 **其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="d5309-127">From Visual Studio, click the **View** menu, click **Other Windows**, and then click **Orchestration View**.</span></span>  
  
2.  <span data-ttu-id="d5309-128">從協調流程] 檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 [**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="d5309-128">From Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
3.  <span data-ttu-id="d5309-129">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d5309-129">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="d5309-130">使用</span><span class="sxs-lookup"><span data-stu-id="d5309-130">Use this</span></span>|<span data-ttu-id="d5309-131">動作</span><span class="sxs-lookup"><span data-stu-id="d5309-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d5309-132">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="d5309-132">**Identifier**</span></span>|<span data-ttu-id="d5309-133">型別**RequestMessage**。</span><span class="sxs-lookup"><span data-stu-id="d5309-133">Type **RequestMessage**.</span></span>|  
    |<span data-ttu-id="d5309-134">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="d5309-134">**Message Type**</span></span>|<span data-ttu-id="d5309-135">按一下**結構描述**，然後按一下  **\<選取從參考組件...>**。</span><span class="sxs-lookup"><span data-stu-id="d5309-135">Click **Schemas**, and then click **\<Select from referenced assembly …>**.</span></span> <span data-ttu-id="d5309-136">從 選取成品類型 視窗中，按一下  **EAISchemas**，然後按一下 **要求**。</span><span class="sxs-lookup"><span data-stu-id="d5309-136">From the Select Artifact Type window, click **EAISchemas**, and then click **Request**.</span></span> <span data-ttu-id="d5309-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d5309-137">Click **OK**</span></span>|  
  
4.  <span data-ttu-id="d5309-138">從協調流程] 檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 [**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="d5309-138">From Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
5.  <span data-ttu-id="d5309-139">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d5309-139">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="d5309-140">使用</span><span class="sxs-lookup"><span data-stu-id="d5309-140">Use this</span></span>|<span data-ttu-id="d5309-141">動作</span><span class="sxs-lookup"><span data-stu-id="d5309-141">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d5309-142">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="d5309-142">**Identifier**</span></span>|<span data-ttu-id="d5309-143">型別**[requestdeclinemessage]**。</span><span class="sxs-lookup"><span data-stu-id="d5309-143">Type **RequestDeclineMessage**.</span></span>|  
    |<span data-ttu-id="d5309-144">**訊息類型**</span><span class="sxs-lookup"><span data-stu-id="d5309-144">**Message Type**</span></span>|<span data-ttu-id="d5309-145">按一下**結構描述**，然後按一下  **\<選取從參考組件...>**。</span><span class="sxs-lookup"><span data-stu-id="d5309-145">Click **Schemas**, and then click **\<Select from referenced assembly …>**.</span></span> <span data-ttu-id="d5309-146">從 選取成品類型 視窗中，按一下  **EAISchemas**，然後按一下 **拒絕**。</span><span class="sxs-lookup"><span data-stu-id="d5309-146">From the Select Artifact Type window, click **EAISchemas**, and then click **RequestDecline**.</span></span> <span data-ttu-id="d5309-147">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d5309-147">Click **OK**</span></span>|  
  
#### <a name="to-configure-the-properties-of-the-shapes"></a><span data-ttu-id="d5309-148">若要設定的圖形屬性</span><span class="sxs-lookup"><span data-stu-id="d5309-148">To configure the properties of the shapes</span></span>  
  
1.  <span data-ttu-id="d5309-149">設計介面上，按一下 **接收**圖形加以選取。</span><span class="sxs-lookup"><span data-stu-id="d5309-149">On the design surface, click the **Receive** shape to select it.</span></span>  
  
2.  <span data-ttu-id="d5309-150">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d5309-150">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="d5309-151">使用</span><span class="sxs-lookup"><span data-stu-id="d5309-151">Use this</span></span>|<span data-ttu-id="d5309-152">動作</span><span class="sxs-lookup"><span data-stu-id="d5309-152">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d5309-153">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d5309-153">**Name**</span></span>|<span data-ttu-id="d5309-154">型別**ReceiveRequest**。</span><span class="sxs-lookup"><span data-stu-id="d5309-154">Type **ReceiveRequest**.</span></span>|  
    |<span data-ttu-id="d5309-155">**訊息**</span><span class="sxs-lookup"><span data-stu-id="d5309-155">**Message**</span></span>|<span data-ttu-id="d5309-156">選取**RequestMessage**。</span><span class="sxs-lookup"><span data-stu-id="d5309-156">Select **RequestMessage**.</span></span>|  
    |<span data-ttu-id="d5309-157">**Activate**</span><span class="sxs-lookup"><span data-stu-id="d5309-157">**Activate**</span></span>|<span data-ttu-id="d5309-158">從下拉式清單選取**True**。</span><span class="sxs-lookup"><span data-stu-id="d5309-158">From the drop-down list, select **True**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="d5309-159">如果 [屬性] 視窗未開啟，請在**檢視**功能表上，按一下 [**屬性] 視窗**。</span><span class="sxs-lookup"><span data-stu-id="d5309-159">If the Property window is not open, in the **View** menu, click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="d5309-160">設計介面上，按一下 **決定**圖形。</span><span class="sxs-lookup"><span data-stu-id="d5309-160">On the design surface, click the **Decide** shape.</span></span>  
  
4.  <span data-ttu-id="d5309-161">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d5309-161">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="d5309-162">使用</span><span class="sxs-lookup"><span data-stu-id="d5309-162">Use this</span></span>|<span data-ttu-id="d5309-163">動作</span><span class="sxs-lookup"><span data-stu-id="d5309-163">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d5309-164">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d5309-164">**Name**</span></span>|<span data-ttu-id="d5309-165">型別**CheckGrandTotal**。</span><span class="sxs-lookup"><span data-stu-id="d5309-165">Type **CheckGrandTotal**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="d5309-166">如果 [屬性] 視窗未開啟，請在**檢視**功能表上，按一下 [**屬性] 視窗**。</span><span class="sxs-lookup"><span data-stu-id="d5309-166">If the Property window is not open, in the **View** menu, click **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="d5309-167">設計介面上，按一下  **Rule_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="d5309-167">On the design surface, click the **Rule_1** shape.</span></span>  
  
6.  <span data-ttu-id="d5309-168">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d5309-168">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="d5309-169">使用</span><span class="sxs-lookup"><span data-stu-id="d5309-169">Use this</span></span>|<span data-ttu-id="d5309-170">動作</span><span class="sxs-lookup"><span data-stu-id="d5309-170">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d5309-171">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d5309-171">**Name**</span></span>|<span data-ttu-id="d5309-172">型別**DeclineRule**。</span><span class="sxs-lookup"><span data-stu-id="d5309-172">Type **DeclineRule**.</span></span>|  
    |<span data-ttu-id="d5309-173">**運算式**</span><span class="sxs-lookup"><span data-stu-id="d5309-173">**Expression**</span></span>|<span data-ttu-id="d5309-174">按一下省略符號 (**...**)，然後輸入`RequestMessage(EAISchemas.PropertySchema.GrandTotal ) > 10000`。</span><span class="sxs-lookup"><span data-stu-id="d5309-174">Click the ellipses (**…**), and then type `RequestMessage(EAISchemas.PropertySchema.GrandTotal ) > 10000`.</span></span> <span data-ttu-id="d5309-175">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d5309-175">Click **OK**.</span></span>|  
  
7.  <span data-ttu-id="d5309-176">設計介面上，按一下  **constructmessage_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="d5309-176">On the design surface, click the **ConstructMessage_1** shape.</span></span>  
  
8.  <span data-ttu-id="d5309-177">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d5309-177">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="d5309-178">使用</span><span class="sxs-lookup"><span data-stu-id="d5309-178">Use this</span></span>|<span data-ttu-id="d5309-179">動作</span><span class="sxs-lookup"><span data-stu-id="d5309-179">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d5309-180">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d5309-180">**Name**</span></span>|<span data-ttu-id="d5309-181">型別**ConstructRequestDeclineMessage**。</span><span class="sxs-lookup"><span data-stu-id="d5309-181">Type **ConstructRequestDeclineMessage**.</span></span>|  
    |<span data-ttu-id="d5309-182">**建構的訊息**</span><span class="sxs-lookup"><span data-stu-id="d5309-182">**Messages Constructed**</span></span>|<span data-ttu-id="d5309-183">選取**[requestdeclinemessage]**。</span><span class="sxs-lookup"><span data-stu-id="d5309-183">Select **RequestDeclineMessage**.</span></span>|  
  
9. <span data-ttu-id="d5309-184">設計介面上，按一下  **transform_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="d5309-184">On the design surface, click the **Transform_1** shape.</span></span>  
  
10. <span data-ttu-id="d5309-185">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d5309-185">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="d5309-186">使用</span><span class="sxs-lookup"><span data-stu-id="d5309-186">Use this</span></span>|<span data-ttu-id="d5309-187">動作</span><span class="sxs-lookup"><span data-stu-id="d5309-187">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d5309-188">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d5309-188">**Name**</span></span>|<span data-ttu-id="d5309-189">型別**TransformRequestToRequestDeclineMessage**。</span><span class="sxs-lookup"><span data-stu-id="d5309-189">Type **TransformRequestToRequestDeclineMessage**.</span></span>|  
    |<span data-ttu-id="d5309-190">**對應名稱**</span><span class="sxs-lookup"><span data-stu-id="d5309-190">**Map Name**</span></span>|<span data-ttu-id="d5309-191">按一下**...**.</span><span class="sxs-lookup"><span data-stu-id="d5309-191">Click **…**.</span></span> <span data-ttu-id="d5309-192">從 [轉換組態] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d5309-192">From Transform Configuration, do the following:</span></span><br /><br /> <span data-ttu-id="d5309-193">輸入組態資訊：</span><span class="sxs-lookup"><span data-stu-id="d5309-193">Enter the configuration information:</span></span><br /><br /> <span data-ttu-id="d5309-194">-按一下**現有對應**。</span><span class="sxs-lookup"><span data-stu-id="d5309-194">- Click **Existing Map**.</span></span><br /><br /> <span data-ttu-id="d5309-195">完整格式的對應名稱：</span><span class="sxs-lookup"><span data-stu-id="d5309-195">Fully Qualified Map Name:</span></span><br /><br /> <span data-ttu-id="d5309-196">-選取**\<從參考組件選取 >**。</span><span class="sxs-lookup"><span data-stu-id="d5309-196">- Select **\<Select from referenced assembly>**.</span></span>  <span data-ttu-id="d5309-197">從左窗格中，選取**EAISchemas**。</span><span class="sxs-lookup"><span data-stu-id="d5309-197">From the left pane, select **EAISchemas**.</span></span>  <span data-ttu-id="d5309-198">從右窗格選取 [EAISchemas.MapToReqDecline]。</span><span class="sxs-lookup"><span data-stu-id="d5309-198">From the right pane, select EAISchemas.MapToReqDecline.</span></span>  <span data-ttu-id="d5309-199">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d5309-199">Click **OK**.</span></span><br /><br /> <span data-ttu-id="d5309-200">Source</span><span class="sxs-lookup"><span data-stu-id="d5309-200">Source</span></span><br /><br /> <span data-ttu-id="d5309-201">-RequestMessage</span><span class="sxs-lookup"><span data-stu-id="d5309-201">- RequestMessage</span></span><br /><br /> <span data-ttu-id="d5309-202">目的地</span><span class="sxs-lookup"><span data-stu-id="d5309-202">Destination</span></span><br /><br /> <span data-ttu-id="d5309-203">-[Requestdeclinemessage]</span><span class="sxs-lookup"><span data-stu-id="d5309-203">- RequestDeclineMessage</span></span>|  
  
11. <span data-ttu-id="d5309-204">設計介面上，按一下  **send_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="d5309-204">On the design surface, click the **Send_1** shape.</span></span>  
  
12. <span data-ttu-id="d5309-205">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d5309-205">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="d5309-206">使用</span><span class="sxs-lookup"><span data-stu-id="d5309-206">Use this</span></span>|<span data-ttu-id="d5309-207">動作</span><span class="sxs-lookup"><span data-stu-id="d5309-207">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d5309-208">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d5309-208">**Name**</span></span>|<span data-ttu-id="d5309-209">型別**SendRequestDecline**。</span><span class="sxs-lookup"><span data-stu-id="d5309-209">Type **SendRequestDecline**.</span></span>|  
    |<span data-ttu-id="d5309-210">**訊息**</span><span class="sxs-lookup"><span data-stu-id="d5309-210">**Message**</span></span>|<span data-ttu-id="d5309-211">選取**[requestdeclinemessage]**。</span><span class="sxs-lookup"><span data-stu-id="d5309-211">Select **RequestDeclineMessage**.</span></span>|  
  
13. <span data-ttu-id="d5309-212">設計介面上，按一下  **send_2**圖形。</span><span class="sxs-lookup"><span data-stu-id="d5309-212">On the design surface, click the **Send_2** shape.</span></span>  
  
14. <span data-ttu-id="d5309-213">在 [屬性] 視窗中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d5309-213">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="d5309-214">使用</span><span class="sxs-lookup"><span data-stu-id="d5309-214">Use this</span></span>|<span data-ttu-id="d5309-215">動作</span><span class="sxs-lookup"><span data-stu-id="d5309-215">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d5309-216">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d5309-216">**Name**</span></span>|<span data-ttu-id="d5309-217">型別**SendRequestToERP**。</span><span class="sxs-lookup"><span data-stu-id="d5309-217">Type **SendRequestToERP**.</span></span>|  
    |<span data-ttu-id="d5309-218">**訊息**</span><span class="sxs-lookup"><span data-stu-id="d5309-218">**Message**</span></span>|<span data-ttu-id="d5309-219">選取**RequestMessage**。</span><span class="sxs-lookup"><span data-stu-id="d5309-219">Select **RequestMessage**.</span></span>|  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="d5309-220">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="d5309-220">What did I just do?</span></span>  
 <span data-ttu-id="d5309-221">在此步驟中，您使用「協調流程設計師」定義了商務程序。</span><span class="sxs-lookup"><span data-stu-id="d5309-221">In this step, you used Orchestration Designer to define your business process.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d5309-222">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d5309-222">Next Steps</span></span>  
 <span data-ttu-id="d5309-223">您將邏輯連接埠加入至協調流程中[步驟 3： 新增至協調流程的連接埠](../core/step-3-add-ports-to-the-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="d5309-223">You add logical ports to the orchestration in [Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5309-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5309-224">See Also</span></span>  
 <span data-ttu-id="d5309-225">[步驟 1： 將 EAIOrchestration 專案加入方案](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span><span class="sxs-lookup"><span data-stu-id="d5309-225">[Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span></span>  
 <span data-ttu-id="d5309-226">[步驟 3： 新增至協調流程連接埠](../core/step-3-add-ports-to-the-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="d5309-226">[Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md) </span></span>  
 [<span data-ttu-id="d5309-227">步驟 4： 建置 EAIOrchestration 專案</span><span class="sxs-lookup"><span data-stu-id="d5309-227">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)