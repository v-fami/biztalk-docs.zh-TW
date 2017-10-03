---
title: "步驟 2： 將要求訊息傳送至 SQL Server，並接收回應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864d2174-d54b-4383-92bf-f6808a2a904b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce820ab6a1914e44239313588eaaefeb696e61d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-send-the-request-message-to-sql-server-and-receive-response"></a><span data-ttu-id="31f8e-102">步驟 2： 將要求訊息傳送至 SQL Server，並接收回應</span><span class="sxs-lookup"><span data-stu-id="31f8e-102">Step 2: Send the Request Message to SQL Server and Receive Response</span></span>
<span data-ttu-id="31f8e-103">![步驟 2 之 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span><span class="sxs-lookup"><span data-stu-id="31f8e-103">![Step 2 of 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span></span>  
  
 <span data-ttu-id="31f8e-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="31f8e-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="31f8e-105">**目標：**在此步驟中，您可以傳送要執行的要求訊息**UPDATE_EMPLOYEE**預存程序，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="31f8e-105">**Objective:** In this step, you send the request message to execute the **UPDATE_EMPLOYEE** stored procedure and receive the response.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="31f8e-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="31f8e-106">Prerequisites</span></span>  
 <span data-ttu-id="31f8e-107">您必須先完成[步驟 1： 建立要求訊息的 UPDATE_EMPLOYEE 預存程序](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="31f8e-107">You must have completed [Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md).</span></span>  
  
### <a name="to-send-the-request-message-and-receive-a-response"></a><span data-ttu-id="31f8e-108">以傳送要求訊息並接收回應</span><span class="sxs-lookup"><span data-stu-id="31f8e-108">To send the request message and receive a response</span></span>  
  
1.  <span data-ttu-id="31f8e-109">到現有的協調流程，在**插入**區塊**決定**圖形中新增**訊息指派**圖形。</span><span class="sxs-lookup"><span data-stu-id="31f8e-109">To the existing orchestration, under the **Insert** block of the **Decide** shape, add a **Message Assignment** shape.</span></span> <span data-ttu-id="31f8e-110">從 [工具箱] 拖曳**訊息指派**空間的圖形表示。</span><span class="sxs-lookup"><span data-stu-id="31f8e-110">From the Toolbox, drag the **Message Assignment** shape to the space indicated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31f8e-111">當您卸除**訊息指派**圖形拖曳至設計介面，協調流程設計師 」 可讓您建立封閉式**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="31f8e-111">When you drop the **Message Assignment** shape onto the design surface, Orchestration Designer creates the enclosing **Construct Message** shape for you.</span></span>  
  
2.  <span data-ttu-id="31f8e-112">設計介面上，以滑鼠右鍵按一下**constructmessage_1**圖形，，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="31f8e-112">On the design surface, right-click the **ConstructMessage_1** shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="31f8e-113">在**屬性**窗格**[constructmessage_1]**圖形中，指定下列值。</span><span class="sxs-lookup"><span data-stu-id="31f8e-113">In the **Properties** pane for the **ConstructMessage_1** shape, specify the following values.</span></span>  
  
    |<span data-ttu-id="31f8e-114">將此屬性設定</span><span class="sxs-lookup"><span data-stu-id="31f8e-114">Set this property</span></span>|<span data-ttu-id="31f8e-115">此值</span><span class="sxs-lookup"><span data-stu-id="31f8e-115">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="31f8e-116">**建構的訊息**</span><span class="sxs-lookup"><span data-stu-id="31f8e-116">**Messages Constructed**</span></span>|<span data-ttu-id="31f8e-117">UpdateEmployee</span><span class="sxs-lookup"><span data-stu-id="31f8e-117">UpdateEmployee</span></span>|  
    |<span data-ttu-id="31f8e-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="31f8e-118">**Name**</span></span>|<span data-ttu-id="31f8e-119">ConstructRequestMessage</span><span class="sxs-lookup"><span data-stu-id="31f8e-119">ConstructRequestMessage</span></span>|  
  
4.  <span data-ttu-id="31f8e-120">按兩下**MessageAssignment**圖形以開啟**BizTalk 運算式編輯器**。</span><span class="sxs-lookup"><span data-stu-id="31f8e-120">Double-click the **MessageAssignment** shape to open the **BizTalk Expression Editor**.</span></span>  
  
5.  <span data-ttu-id="31f8e-121">在**BizTalk 運算式編輯器**，加入下列：</span><span class="sxs-lookup"><span data-stu-id="31f8e-121">In the **BizTalk Expression Editor**, add the following:</span></span>  
  
    ```  
    UpdateEmployee = UpdateEmployeeMessageCreator.UpdateEmployeeMessageCreator.XMLMessageCreator();  
    UpdateEmployee(WCF.Action) = "TypedProcedure/dbo/UPDATE_EMPLOYEE";  
    ```  
  
     <span data-ttu-id="31f8e-122">在這裡， **UpdateEmployee**是您在建立的訊息[步驟 2： 建立訊息的 BizTalk 協調流程](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)傳送要求訊息**UPDATE_EMPLOYEE**儲存程序。</span><span class="sxs-lookup"><span data-stu-id="31f8e-122">Here, **UpdateEmployee** is the message you created in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) for sending request messages for **UPDATE_EMPLOYEE** stored procedure.</span></span> <span data-ttu-id="31f8e-123">在**MessageAssignment**圖形，您可以叫用**UpdateEmployeeMessageCreator**類別來建立要求訊息。</span><span class="sxs-lookup"><span data-stu-id="31f8e-123">In the **MessageAssignment** shape, you invoke the **UpdateEmployeeMessageCreator** class to create a request message.</span></span> <span data-ttu-id="31f8e-124">此外，您可以設定要求訊息的 WCF 動作。</span><span class="sxs-lookup"><span data-stu-id="31f8e-124">Also, you set the WCF action for the request message.</span></span>  
  
6.  <span data-ttu-id="31f8e-125">在協調流程中加入下列圖形**訊息指派**圖形。</span><span class="sxs-lookup"><span data-stu-id="31f8e-125">Add the following shapes to the orchestration under the **Message Assignment** shape.</span></span>  
  
    |<span data-ttu-id="31f8e-126">形狀圖</span><span class="sxs-lookup"><span data-stu-id="31f8e-126">Shape</span></span>|<span data-ttu-id="31f8e-127">圖形類型</span><span class="sxs-lookup"><span data-stu-id="31f8e-127">Shape Type</span></span>|<span data-ttu-id="31f8e-128">屬性</span><span class="sxs-lookup"><span data-stu-id="31f8e-128">Properties</span></span>|  
    |-----------|----------------|----------------|  
    |<span data-ttu-id="31f8e-129">SendUpdateMessage</span><span class="sxs-lookup"><span data-stu-id="31f8e-129">SendUpdateMessage</span></span>|<span data-ttu-id="31f8e-130">Send</span><span class="sxs-lookup"><span data-stu-id="31f8e-130">Send</span></span>|<span data-ttu-id="31f8e-131">-設定**訊息**至*UpdateEmployee*</span><span class="sxs-lookup"><span data-stu-id="31f8e-131">-   Set **Message** to *UpdateEmployee*</span></span><br /><span data-ttu-id="31f8e-132">-設定**名稱**至*SendUpdateMessage*</span><span class="sxs-lookup"><span data-stu-id="31f8e-132">-   Set **Name** to *SendUpdateMessage*</span></span>|  
    |<span data-ttu-id="31f8e-133">ReceiveUpdateResponse</span><span class="sxs-lookup"><span data-stu-id="31f8e-133">ReceiveUpdateResponse</span></span>|<span data-ttu-id="31f8e-134">Receive</span><span class="sxs-lookup"><span data-stu-id="31f8e-134">Receive</span></span>|<span data-ttu-id="31f8e-135">-設定**啟動**至*False*</span><span class="sxs-lookup"><span data-stu-id="31f8e-135">-   Set **Activate** to *False*</span></span><br /><span data-ttu-id="31f8e-136">-設定**訊息**至*UpdateEmployeeResponse*</span><span class="sxs-lookup"><span data-stu-id="31f8e-136">-   Set **Message** to *UpdateEmployeeResponse*</span></span><br /><span data-ttu-id="31f8e-137">-設定**名稱**至*ReceiveUpdateResponse*</span><span class="sxs-lookup"><span data-stu-id="31f8e-137">-   Set **Name** to *ReceiveUpdateResponse*</span></span>|  
  
7.  <span data-ttu-id="31f8e-138">新增要求-回應傳送埠至協調流程。</span><span class="sxs-lookup"><span data-stu-id="31f8e-138">Add a request-response send port to the orchestration.</span></span> <span data-ttu-id="31f8e-139">您將使用此連接埠以將要求訊息傳送到 SQL Server，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="31f8e-139">You will use this port to send request messages to the SQL Server and receive response.</span></span> <span data-ttu-id="31f8e-140">設定下列屬性的連接埠。</span><span class="sxs-lookup"><span data-stu-id="31f8e-140">Set the following properties for the port.</span></span>  
  
    |<span data-ttu-id="31f8e-141">將此屬性設定</span><span class="sxs-lookup"><span data-stu-id="31f8e-141">Set this property</span></span>|<span data-ttu-id="31f8e-142">此值</span><span class="sxs-lookup"><span data-stu-id="31f8e-142">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="31f8e-143">**通訊方向**</span><span class="sxs-lookup"><span data-stu-id="31f8e-143">**Communication Direction**</span></span>|<span data-ttu-id="31f8e-144">傳送-接收</span><span class="sxs-lookup"><span data-stu-id="31f8e-144">Send-Receive</span></span>|  
    |<span data-ttu-id="31f8e-145">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="31f8e-145">**Communication Pattern**</span></span>|<span data-ttu-id="31f8e-146">要求-回應</span><span class="sxs-lookup"><span data-stu-id="31f8e-146">Request-Response</span></span>|  
    |<span data-ttu-id="31f8e-147">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="31f8e-147">**Identifier**</span></span>|<span data-ttu-id="31f8e-148">SQLOutboundPort</span><span class="sxs-lookup"><span data-stu-id="31f8e-148">SQLOutboundPort</span></span>|  
  
     <span data-ttu-id="31f8e-149">此外，從 Operation_1，若要變更的作業名稱**UpdateEmp**。</span><span class="sxs-lookup"><span data-stu-id="31f8e-149">Also, change the operation name from Operation_1 to **UpdateEmp**.</span></span>  
  
8.  <span data-ttu-id="31f8e-150">連接到動作圖形的連接埠。</span><span class="sxs-lookup"><span data-stu-id="31f8e-150">Connect the port to action shapes.</span></span> <span data-ttu-id="31f8e-151">在 協調流程設計工具的設計介面上，拖曳動作圖形的連接埠對應綠色控點的綠色箭頭圖形控。</span><span class="sxs-lookup"><span data-stu-id="31f8e-151">In Orchestration Designer, on the design surface, drag the green arrow-shaped handle for the port to the corresponding green handle of the action shape.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31f8e-152">在此步驟中，您使用拖放方法將連接埠連接到動作圖形。</span><span class="sxs-lookup"><span data-stu-id="31f8e-152">In this step, you use the drag-and-drop method to connect ports to action shapes.</span></span> <span data-ttu-id="31f8e-153">代替使用動作圖形的作業屬性將動作圖形連接到連接埠。</span><span class="sxs-lookup"><span data-stu-id="31f8e-153">You could instead use the operation property of an action shape to connect the action shape to a port.</span></span>  
  
     <span data-ttu-id="31f8e-154">連接埠和動作圖形連接，如下所示：</span><span class="sxs-lookup"><span data-stu-id="31f8e-154">Connect the ports and action shapes as follows:</span></span>  
  
    -   <span data-ttu-id="31f8e-155">連接**SendUpdateMessage**至動作圖形**要求**控點**SQLOutboundPort**。</span><span class="sxs-lookup"><span data-stu-id="31f8e-155">Connect the **SendUpdateMessage** action shape to the **Request** handle of the **SQLOutboundPort**.</span></span>  
  
    -   <span data-ttu-id="31f8e-156">連接**ReceiveUpdateResponse**至動作圖形**回應**控點**SQLOutboundPort**。</span><span class="sxs-lookup"><span data-stu-id="31f8e-156">Connect the **ReceiveUpdateResponse** action shape to the **Response** handle of the **SQLOutboundPort**.</span></span>  
  
9. <span data-ttu-id="31f8e-157">下圖顯示進行中協調流程。</span><span class="sxs-lookup"><span data-stu-id="31f8e-157">The following figure shows the in-progress orchestration.</span></span>  
  
     <span data-ttu-id="31f8e-158">![更新協調流程傳送更新訊息](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-04-update-msg-orch.gif "sql_adap_tut_04_update_msg_orch")</span><span class="sxs-lookup"><span data-stu-id="31f8e-158">![Updated orchestration to send update message](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-04-update-msg-orch.gif "sql_adap_tut_04_update_msg_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="31f8e-159">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="31f8e-159">What did I just do?</span></span>  
 <span data-ttu-id="31f8e-160">在此步驟中，您必須更新協調流程藉由新增**MessageAssignment**圖形，**傳送**和**接收**圖形和連接埠。</span><span class="sxs-lookup"><span data-stu-id="31f8e-160">In this step, you updated the orchestration by adding a **MessageAssignment** shape, **Send** and **Receive** shapes, and a port.</span></span> <span data-ttu-id="31f8e-161">連接圖形和連接埠來傳送要求訊息給執行 UDPATE_EMPLOYEE 要求訊息並接收回應。</span><span class="sxs-lookup"><span data-stu-id="31f8e-161">You connected the shapes and ports to send request message to execute the UDPATE_EMPLOYEE request message and receive the response.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="31f8e-162">後續步驟</span><span class="sxs-lookup"><span data-stu-id="31f8e-162">Next Steps</span></span>  
 <span data-ttu-id="31f8e-163">在下一個步驟中，您會加入至插入作業上叫用的協調流程圖形**Purchase_Order**資料表中所述[第 4 課： 執行插入作業的採購訂單資料表](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)。</span><span class="sxs-lookup"><span data-stu-id="31f8e-163">In the next step, you add orchestration shapes to invoke the Insert operation on the **Purchase_Order** table, as described in [Lesson 4: Perform an Insert Operation on the Purchase Order Table](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f8e-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31f8e-164">See Also</span></span>  
 <span data-ttu-id="31f8e-165">[步驟 1： 建立要求訊息的 UPDATE_EMPLOYEE 預存程序](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="31f8e-165">[Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md) </span></span>  
 [<span data-ttu-id="31f8e-166">第 3 課： 執行預存程序選取 加入新的員工</span><span class="sxs-lookup"><span data-stu-id="31f8e-166">Lesson 3: Execute a Stored Procedure to Select New Employees Added</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)