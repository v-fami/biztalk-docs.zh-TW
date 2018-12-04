---
title: 步驟 2： 將要求訊息傳送到 SQL Server，並接收回應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 864d2174-d54b-4383-92bf-f6808a2a904b
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55c2c6095c9e0c7bf88ec22a296ccc6483c62472
ms.sourcegitcommit: be6273d612669adfbb9dc9208aaae0a8437d4017
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2018
ms.locfileid: "52826310"
---
# <a name="step-2-send-the-request-message-to-sql-server-and-receive-response"></a><span data-ttu-id="d1216-102">步驟 2： 將要求訊息傳送到 SQL Server，並接收回應</span><span class="sxs-lookup"><span data-stu-id="d1216-102">Step 2: Send the Request Message to SQL Server and Receive Response</span></span>
<span data-ttu-id="d1216-103">![步驟 2 之 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span><span class="sxs-lookup"><span data-stu-id="d1216-103">![Step 2 of 2](../../adapters-and-accelerators/adapter-sql/media/step-2of2.gif "Step_2of2")</span></span>  
  
 <span data-ttu-id="d1216-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="d1216-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="d1216-105">**目標：** 在此步驟中，您可以傳送要執行的要求訊息**UPDATE_EMPLOYEE**預存程序，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="d1216-105">**Objective:** In this step, you send the request message to execute the **UPDATE_EMPLOYEE** stored procedure and receive the response.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d1216-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="d1216-106">Prerequisites</span></span>  
 <span data-ttu-id="d1216-107">您必須先完成[步驟 1： 為 UPDATE_EMPLOYEE 預存程序建立要求訊息](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="d1216-107">You must have completed [Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md).</span></span>  
  
### <a name="to-send-the-request-message-and-receive-a-response"></a><span data-ttu-id="d1216-108">若要傳送的要求訊息並接收回應</span><span class="sxs-lookup"><span data-stu-id="d1216-108">To send the request message and receive a response</span></span>  
  
1.  <span data-ttu-id="d1216-109">在現有的協調流程，底下**插入**區塊**決定**圖形中新增**訊息指派**圖形。</span><span class="sxs-lookup"><span data-stu-id="d1216-109">To the existing orchestration, under the **Insert** block of the **Decide** shape, add a **Message Assignment** shape.</span></span> <span data-ttu-id="d1216-110">從 [工具箱] 拖曳**訊息指派**空間的圖形表示。</span><span class="sxs-lookup"><span data-stu-id="d1216-110">From the Toolbox, drag the **Message Assignment** shape to the space indicated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1216-111">當您卸除**訊息指派**圖形拖曳至設計介面，而協調流程設計師 」 可讓您建立封閉式**建構訊息**為您的圖形。</span><span class="sxs-lookup"><span data-stu-id="d1216-111">When you drop the **Message Assignment** shape onto the design surface, Orchestration Designer creates the enclosing **Construct Message** shape for you.</span></span>  
  
2.  <span data-ttu-id="d1216-112">在設計介面中，以滑鼠右鍵按一下**constructmessage_1**圖形，，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="d1216-112">On the design surface, right-click the **ConstructMessage_1** shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="d1216-113">在 [**屬性**] 窗格 **[constructmessage_1]** 圖形中，指定下列值。</span><span class="sxs-lookup"><span data-stu-id="d1216-113">In the **Properties** pane for the **ConstructMessage_1** shape, specify the following values.</span></span>  
  
    |<span data-ttu-id="d1216-114">將此屬性設定</span><span class="sxs-lookup"><span data-stu-id="d1216-114">Set this property</span></span>|<span data-ttu-id="d1216-115">此值</span><span class="sxs-lookup"><span data-stu-id="d1216-115">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="d1216-116">**建構的訊息**</span><span class="sxs-lookup"><span data-stu-id="d1216-116">**Messages Constructed**</span></span>|<span data-ttu-id="d1216-117">UpdateEmployee</span><span class="sxs-lookup"><span data-stu-id="d1216-117">UpdateEmployee</span></span>|  
    |<span data-ttu-id="d1216-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d1216-118">**Name**</span></span>|<span data-ttu-id="d1216-119">ConstructRequestMessage</span><span class="sxs-lookup"><span data-stu-id="d1216-119">ConstructRequestMessage</span></span>|  
  
4.  <span data-ttu-id="d1216-120">按兩下**MessageAssignment**圖形以開啟**BizTalk 運算式編輯器**。</span><span class="sxs-lookup"><span data-stu-id="d1216-120">Double-click the **MessageAssignment** shape to open the **BizTalk Expression Editor**.</span></span>  
  
5.  <span data-ttu-id="d1216-121">在  **BizTalk 運算式編輯器**，新增下列：</span><span class="sxs-lookup"><span data-stu-id="d1216-121">In the **BizTalk Expression Editor**, add the following:</span></span>  
  
    ```  
    UpdateEmployee = UpdateEmployeeMessageCreator.UpdateEmployeeMessageCreator.XMLMessageCreator();  
    UpdateEmployee(WCF.Action) = "TypedProcedure/dbo/UPDATE_EMPLOYEE";  
    ```  
  
     <span data-ttu-id="d1216-122">在這裡， **UpdateEmployee**是您在中建立的訊息[步驟 2： 建立 BizTalk 協調流程的訊息](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)傳送要求訊息**UPDATE_EMPLOYEE**儲存程序。</span><span class="sxs-lookup"><span data-stu-id="d1216-122">Here, **UpdateEmployee** is the message you created in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) for sending request messages for **UPDATE_EMPLOYEE** stored procedure.</span></span> <span data-ttu-id="d1216-123">在  **MessageAssignment**圖形，您可以叫用**UpdateEmployeeMessageCreator**類別來建立要求訊息。</span><span class="sxs-lookup"><span data-stu-id="d1216-123">In the **MessageAssignment** shape, you invoke the **UpdateEmployeeMessageCreator** class to create a request message.</span></span> <span data-ttu-id="d1216-124">此外，您可以設定要求訊息的 WCF 動作。</span><span class="sxs-lookup"><span data-stu-id="d1216-124">Also, you set the WCF action for the request message.</span></span>  
  
6.  <span data-ttu-id="d1216-125">在協調流程中加入下列圖形**訊息指派**圖形。</span><span class="sxs-lookup"><span data-stu-id="d1216-125">Add the following shapes to the orchestration under the **Message Assignment** shape.</span></span>  
  
    |<span data-ttu-id="d1216-126">形狀圖</span><span class="sxs-lookup"><span data-stu-id="d1216-126">Shape</span></span>|<span data-ttu-id="d1216-127">圖形類型</span><span class="sxs-lookup"><span data-stu-id="d1216-127">Shape Type</span></span>|<span data-ttu-id="d1216-128">屬性</span><span class="sxs-lookup"><span data-stu-id="d1216-128">Properties</span></span>|  
    |-----------|----------------|----------------|  
    |<span data-ttu-id="d1216-129">SendUpdateMessage</span><span class="sxs-lookup"><span data-stu-id="d1216-129">SendUpdateMessage</span></span>|<span data-ttu-id="d1216-130">Send</span><span class="sxs-lookup"><span data-stu-id="d1216-130">Send</span></span>|<span data-ttu-id="d1216-131">-設定**訊息**到*UpdateEmployee*</span><span class="sxs-lookup"><span data-stu-id="d1216-131">-   Set **Message** to *UpdateEmployee*</span></span><br /><span data-ttu-id="d1216-132">-設定**名稱**到*SendUpdateMessage*</span><span class="sxs-lookup"><span data-stu-id="d1216-132">-   Set **Name** to *SendUpdateMessage*</span></span>|  
    |<span data-ttu-id="d1216-133">ReceiveUpdateResponse</span><span class="sxs-lookup"><span data-stu-id="d1216-133">ReceiveUpdateResponse</span></span>|<span data-ttu-id="d1216-134">Receive</span><span class="sxs-lookup"><span data-stu-id="d1216-134">Receive</span></span>|<span data-ttu-id="d1216-135">-設定**啟用**到*False*</span><span class="sxs-lookup"><span data-stu-id="d1216-135">-   Set **Activate** to *False*</span></span><br /><span data-ttu-id="d1216-136">-設定**訊息**到*UpdateEmployeeResponse*</span><span class="sxs-lookup"><span data-stu-id="d1216-136">-   Set **Message** to *UpdateEmployeeResponse*</span></span><br /><span data-ttu-id="d1216-137">-設定**名稱**到*ReceiveUpdateResponse*</span><span class="sxs-lookup"><span data-stu-id="d1216-137">-   Set **Name** to *ReceiveUpdateResponse*</span></span>|  
  
7.  <span data-ttu-id="d1216-138">新增要求-回應傳送埠至協調流程。</span><span class="sxs-lookup"><span data-stu-id="d1216-138">Add a request-response send port to the orchestration.</span></span> <span data-ttu-id="d1216-139">您將使用此連接埠，以將要求訊息傳送到 SQL Server，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="d1216-139">You will use this port to send request messages to the SQL Server and receive response.</span></span> <span data-ttu-id="d1216-140">設定連接埠的下列屬性。</span><span class="sxs-lookup"><span data-stu-id="d1216-140">Set the following properties for the port.</span></span>  
  
    |<span data-ttu-id="d1216-141">將此屬性設定</span><span class="sxs-lookup"><span data-stu-id="d1216-141">Set this property</span></span>|<span data-ttu-id="d1216-142">此值</span><span class="sxs-lookup"><span data-stu-id="d1216-142">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="d1216-143">**通訊方向**</span><span class="sxs-lookup"><span data-stu-id="d1216-143">**Communication Direction**</span></span>|<span data-ttu-id="d1216-144">傳送-接收</span><span class="sxs-lookup"><span data-stu-id="d1216-144">Send-Receive</span></span>|  
    |<span data-ttu-id="d1216-145">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="d1216-145">**Communication Pattern**</span></span>|<span data-ttu-id="d1216-146">要求-回應</span><span class="sxs-lookup"><span data-stu-id="d1216-146">Request-Response</span></span>|  
    |<span data-ttu-id="d1216-147">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="d1216-147">**Identifier**</span></span>|<span data-ttu-id="d1216-148">SQLOutboundPort</span><span class="sxs-lookup"><span data-stu-id="d1216-148">SQLOutboundPort</span></span>|  
  
     <span data-ttu-id="d1216-149">此外，變更 Operation_1，若要從 作業名稱**UpdateEmp**。</span><span class="sxs-lookup"><span data-stu-id="d1216-149">Also, change the operation name from Operation_1 to **UpdateEmp**.</span></span>  
  
8.  <span data-ttu-id="d1216-150">連接到動作圖形的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d1216-150">Connect the port to action shapes.</span></span> <span data-ttu-id="d1216-151">在協調流程設計師 」 設計介面上，拖曳的綠色箭頭圖形控點的 「 動作 」 圖形的連接埠的對應綠色控點。</span><span class="sxs-lookup"><span data-stu-id="d1216-151">In Orchestration Designer, on the design surface, drag the green arrow-shaped handle for the port to the corresponding green handle of the action shape.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1216-152">在此步驟中，您使用拖放方法將連接埠連接到動作圖形。</span><span class="sxs-lookup"><span data-stu-id="d1216-152">In this step, you use the drag-and-drop method to connect ports to action shapes.</span></span> <span data-ttu-id="d1216-153">代替使用動作圖形的作業屬性將動作圖形連接到連接埠。</span><span class="sxs-lookup"><span data-stu-id="d1216-153">You could instead use the operation property of an action shape to connect the action shape to a port.</span></span>  
  
     <span data-ttu-id="d1216-154">請連線的連接埠和動作圖形，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d1216-154">Connect the ports and action shapes as follows:</span></span>  
  
    -   <span data-ttu-id="d1216-155">連接**SendUpdateMessage**到動作圖形**要求**控點**SQLOutboundPort**。</span><span class="sxs-lookup"><span data-stu-id="d1216-155">Connect the **SendUpdateMessage** action shape to the **Request** handle of the **SQLOutboundPort**.</span></span>  
  
    -   <span data-ttu-id="d1216-156">連接**ReceiveUpdateResponse**到動作圖形**回應**控點**SQLOutboundPort**。</span><span class="sxs-lookup"><span data-stu-id="d1216-156">Connect the **ReceiveUpdateResponse** action shape to the **Response** handle of the **SQLOutboundPort**.</span></span>  
  
9. <span data-ttu-id="d1216-157">下圖顯示進行中協調流程。</span><span class="sxs-lookup"><span data-stu-id="d1216-157">The following figure shows the in-progress orchestration.</span></span>  
  
     <span data-ttu-id="d1216-158">![更新協調流程傳送更新訊息](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-04-update-msg-orch.gif "sql_adap_tut_04_update_msg_orch")</span><span class="sxs-lookup"><span data-stu-id="d1216-158">![Updated orchestration to send update message](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-04-update-msg-orch.gif "sql_adap_tut_04_update_msg_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="d1216-159">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="d1216-159">What did I just do?</span></span>  
 <span data-ttu-id="d1216-160">在此步驟中，您必須更新協調流程藉由新增**MessageAssignment**圖形**傳送**並**接收**圖形和連接埠。</span><span class="sxs-lookup"><span data-stu-id="d1216-160">In this step, you updated the orchestration by adding a **MessageAssignment** shape, **Send** and **Receive** shapes, and a port.</span></span> <span data-ttu-id="d1216-161">連接圖形和連接埠來傳送要求訊息給執行 UPDATE_EMPLOYEE 要求訊息，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="d1216-161">You connected the shapes and ports to send request message to execute the UPDATE_EMPLOYEE request message and receive the response.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d1216-162">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d1216-162">Next Steps</span></span>  
 <span data-ttu-id="d1216-163">在下一個步驟中，您可以新增上叫用插入作業的協調流程圖形**為 Purchase_Order**資料表中所述[第 4 課： 執行插入作業在訂單資料表](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)。</span><span class="sxs-lookup"><span data-stu-id="d1216-163">In the next step, you add orchestration shapes to invoke the Insert operation on the **Purchase_Order** table, as described in [Lesson 4: Perform an Insert Operation on the Purchase Order Table](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1216-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1216-164">See Also</span></span>  
 <span data-ttu-id="d1216-165">[步驟 1： 建立要求訊息為 UPDATE_EMPLOYEE 預存程序](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="d1216-165">[Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md) </span></span>  
 [<span data-ttu-id="d1216-166">第 3 課：執行預存程序以選取新增的員工</span><span class="sxs-lookup"><span data-stu-id="d1216-166">Lesson 3: Execute a Stored Procedure to Select New Employees Added</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)
