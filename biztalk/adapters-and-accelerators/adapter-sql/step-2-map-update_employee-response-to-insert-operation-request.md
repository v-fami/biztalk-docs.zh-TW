---
title: 步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應至插入作業要求訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d12014a-0147-4227-88fa-0b290eff4cce
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29a7cef00860f32aa2a493cc401e5d49d223ad3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224822"
---
# <a name="step-2-map-the-updateemployee-response-message-to-insert-operation-request-message"></a><span data-ttu-id="c6131-102">步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應至插入作業要求訊息</span><span class="sxs-lookup"><span data-stu-id="c6131-102">Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message</span></span>
<span data-ttu-id="c6131-103">![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="c6131-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="c6131-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="c6131-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="c6131-105">**目標：** 在此步驟中，您可以建立要在上執行插入作業的要求訊息**Purchase_Order**資料表，然後將對應的回應訊息**UPDATE_EMPLOYEE**儲存插入作業的要求訊息的程序。</span><span class="sxs-lookup"><span data-stu-id="c6131-105">**Objective:** In this step, you create the request message to perform an Insert operation on the **Purchase_Order** table and then map the response message for the **UPDATE_EMPLOYEE** stored procedure to the request message for the Insert operation.</span></span> <span data-ttu-id="c6131-106">如此一來，您傳遞要插入至回應訊息中的值**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="c6131-106">By doing so, you pass on the values in the response message to be inserted in the **Purchase_Order** table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c6131-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="c6131-107">Prerequisites</span></span>  
 <span data-ttu-id="c6131-108">您必須先完成[步驟 1： 建立 Purchase_Order 資料表上的插入作業的要求訊息](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md)。</span><span class="sxs-lookup"><span data-stu-id="c6131-108">You must have completed [Step 1: Create the Request Message for Insert Operation on Purchase_Order Table](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md).</span></span>  
  
### <a name="to-map-the-messages"></a><span data-ttu-id="c6131-109">若要將訊息對應</span><span class="sxs-lookup"><span data-stu-id="c6131-109">To map the messages</span></span>  
  
1.  <span data-ttu-id="c6131-110">到現有的協調流程，在**插入**區塊**決定**圖形，在**ReceiveUpdateResponse**圖形中新增**訊息指派**圖形。</span><span class="sxs-lookup"><span data-stu-id="c6131-110">To the existing orchestration, in the **Insert** block of the **Decide** shape, under the **ReceiveUpdateResponse** shape, add a **Message Assignment** shape.</span></span> <span data-ttu-id="c6131-111">從 [工具箱] 拖曳**訊息指派**空間的圖形表示。</span><span class="sxs-lookup"><span data-stu-id="c6131-111">From the Toolbox, drag the **Message Assignment** shape to the space indicated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c6131-112">當您卸除**訊息指派**圖形拖曳至設計介面，協調流程設計師 」 可讓您建立封閉式**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="c6131-112">When you drop the **Message Assignment** shape onto the design surface, Orchestration Designer creates the enclosing **Construct Message** shape for you.</span></span>  
  
2.  <span data-ttu-id="c6131-113">設計介面上，以滑鼠右鍵按一下**constructmessage_1**圖形，，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="c6131-113">On the design surface, right-click the **ConstructMessage_1** shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="c6131-114">在**屬性**窗格 **[constructmessage_1]** 圖形中，指定下列值。</span><span class="sxs-lookup"><span data-stu-id="c6131-114">In the **Properties** pane for the **ConstructMessage_1** shape, specify the following values.</span></span>  
  
    |<span data-ttu-id="c6131-115">將此屬性設定</span><span class="sxs-lookup"><span data-stu-id="c6131-115">Set this property</span></span>|<span data-ttu-id="c6131-116">此值</span><span class="sxs-lookup"><span data-stu-id="c6131-116">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="c6131-117">**建構的訊息**</span><span class="sxs-lookup"><span data-stu-id="c6131-117">**Messages Constructed**</span></span>|<span data-ttu-id="c6131-118">InsertPO</span><span class="sxs-lookup"><span data-stu-id="c6131-118">InsertPO</span></span>|  
    |<span data-ttu-id="c6131-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c6131-119">**Name**</span></span>|<span data-ttu-id="c6131-120">ConstructInsertMessage</span><span class="sxs-lookup"><span data-stu-id="c6131-120">ConstructInsertMessage</span></span>|  
  
4.  <span data-ttu-id="c6131-121">按兩下**MessageAssignment**圖形以開啟**BizTalk 運算式編輯器**。</span><span class="sxs-lookup"><span data-stu-id="c6131-121">Double-click the **MessageAssignment** shape to open the **BizTalk Expression Editor**.</span></span>  
  
5.  <span data-ttu-id="c6131-122">在**BizTalk 運算式編輯器**，加入下列：</span><span class="sxs-lookup"><span data-stu-id="c6131-122">In the **BizTalk Expression Editor**, add the following:</span></span>  
  
    ```  
    InsertPO = UpdatePOMessageCreator.UpdatePOMessageCreator.XMLMessageCreator();  
    InsertPO(WCF.Action) = "TableOp/Insert/dbo/Purchase_Order";  
    ```  
  
     <span data-ttu-id="c6131-123">在這裡， **InsertPO**是您在建立的訊息[步驟 2： 建立訊息的 BizTalk 協調流程](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md)傳送要求訊息的插入作業**Purchase_Order**資料表。</span><span class="sxs-lookup"><span data-stu-id="c6131-123">Here, **InsertPO** is the message you created in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) for sending request messages for Insert operation on the **Purchase_Order** table.</span></span> <span data-ttu-id="c6131-124">在**MessageAssignment**圖形，您可以叫用**UpdatePOMessageCreator**類別來建立要求訊息。</span><span class="sxs-lookup"><span data-stu-id="c6131-124">In the **MessageAssignment** shape, you invoke the **UpdatePOMessageCreator** class to create a request message.</span></span> <span data-ttu-id="c6131-125">此外，您可以設定要求訊息的 WCF 動作。</span><span class="sxs-lookup"><span data-stu-id="c6131-125">Also, you set the WCF action for the request message.</span></span>  
  
6.  <span data-ttu-id="c6131-126">內**建構訊息**圖形及之後**訊息指派**圖形中新增**轉換**圖形。</span><span class="sxs-lookup"><span data-stu-id="c6131-126">Within the **Construct Message** shape and after the **Message Assignment** shape, add a **Transform** shape.</span></span>  
  
7.  <span data-ttu-id="c6131-127">在**轉換組態**對話方塊的左窗格中，從 **轉換**標籤，按一下**來源**。</span><span class="sxs-lookup"><span data-stu-id="c6131-127">In the **Transform Configuration** dialog box, from the left pane, under the **Transform** label, click **Source**.</span></span>  
  
8.  <span data-ttu-id="c6131-128">從**來源轉換**右邊方塊中，按一下 下的空間**變數名稱**，然後選取**UpdateEmployeeResponse**。</span><span class="sxs-lookup"><span data-stu-id="c6131-128">From the **Source Transform** box on the right, click the space under the **Variable Name**, and then select **UpdateEmployeeResponse**.</span></span>  
  
     <span data-ttu-id="c6131-129">![選擇對應的來源結構描述](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-source-map.gif "sql_adap_tut_05_source_map")</span><span class="sxs-lookup"><span data-stu-id="c6131-129">![Pick the source schema for the mapping](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-source-map.gif "sql_adap_tut_05_source_map")</span></span>  
  
9. <span data-ttu-id="c6131-130">在**轉換組態**對話方塊的左窗格中，從 **轉換**標籤，按一下**目的地**。</span><span class="sxs-lookup"><span data-stu-id="c6131-130">In the **Transform Configuration** dialog box, from the left pane, under the **Transform** label, click **Destination**.</span></span>  
  
10. <span data-ttu-id="c6131-131">從**目的轉換**右邊方塊中，按一下 下的空間**變數名稱**，然後選取**InsertPO**。</span><span class="sxs-lookup"><span data-stu-id="c6131-131">From the **Destination Transform** box on the right, click the space under the **Variable Name**, and then select **InsertPO**.</span></span>  
  
     <span data-ttu-id="c6131-132">![挑選對應的目的結構描述](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-dest-map.gif "sql_adap_tut_05_dest_map")</span><span class="sxs-lookup"><span data-stu-id="c6131-132">![Pick the destination schema for mapping](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-05-dest-map.gif "sql_adap_tut_05_dest_map")</span></span>  
  
11. <span data-ttu-id="c6131-133">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c6131-133">Click **OK**.</span></span> <span data-ttu-id="c6131-134">對應檔隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="c6131-134">The map file opens.</span></span>  
  
12. <span data-ttu-id="c6131-135">展開來源與目的結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="c6131-135">Expand the nodes in the source and destination schemas.</span></span>  
  
13. <span data-ttu-id="c6131-136">對應 Employee_ID 並命名為這兩個結構描述中的欄位。</span><span class="sxs-lookup"><span data-stu-id="c6131-136">Map the Employee_ID and name fields in both the schemas.</span></span>  
  
    -   <span data-ttu-id="c6131-137">地圖**Employee_ID**來源結構描述中的節點 (UPDATE_EMPLOYEEResponse) **Employee_ID**目的結構描述 (Insert) 中的節點。</span><span class="sxs-lookup"><span data-stu-id="c6131-137">Map the **Employee_ID** node in the source schema (UPDATE_EMPLOYEEResponse) to the **Employee_ID** node in the destination schema (Insert).</span></span>  
  
    -   <span data-ttu-id="c6131-138">地圖**名稱**來源結構描述中的節點**Employee_Name**目的結構描述中。</span><span class="sxs-lookup"><span data-stu-id="c6131-138">Map the **Name** node in the source schema to the **Employee_Name** in the destination schema.</span></span>  
  
     <span data-ttu-id="c6131-139">下圖顯示對應的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c6131-139">The following figure shows the mapped schemas.</span></span>  
  
     <span data-ttu-id="c6131-140">![對應來源與目的結構描述](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-07-dest-map.gif "sql_adap_tut_07_dest_map")</span><span class="sxs-lookup"><span data-stu-id="c6131-140">![Map the source and destination schemas](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-07-dest-map.gif "sql_adap_tut_07_dest_map")</span></span>  
  
     <span data-ttu-id="c6131-141">儲存並關閉對應。</span><span class="sxs-lookup"><span data-stu-id="c6131-141">Save and close the map.</span></span>  
  
14. <span data-ttu-id="c6131-142">下圖顯示進行中協調流程。</span><span class="sxs-lookup"><span data-stu-id="c6131-142">The following figure shows the in-progress orchestration.</span></span>  
  
     <span data-ttu-id="c6131-143">![使用 「 轉換 」 圖形的協調流程](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-08-map-orch.gif "sql_adap_tut_08_map_orch")</span><span class="sxs-lookup"><span data-stu-id="c6131-143">![Orchestration with the transform shape](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-08-map-orch.gif "sql_adap_tut_08_map_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="c6131-144">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="c6131-144">What did I just do?</span></span>  
 <span data-ttu-id="c6131-145">在此步驟中，您已建立要插入至記錄訊息**Purchase_Order**資料表，並接著對應的回應訊息**UPDATE_EMPLOYEE**預存程序的要求訊息，插入作業。</span><span class="sxs-lookup"><span data-stu-id="c6131-145">In this step, you created a message to insert records into the **Purchase_Order** table and then mapped the response message from the **UPDATE_EMPLOYEE** stored procedure to the request message for the Insert operation.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c6131-146">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c6131-146">Next Steps</span></span>  
 <span data-ttu-id="c6131-147">傳送要求訊息上執行插入作業**Purchase_Order**資料表，並接收回應，如中所述[步驟 3： 傳送要求訊息插入記錄，並接收回應](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)。</span><span class="sxs-lookup"><span data-stu-id="c6131-147">You send the request message to perform an Insert operation on the **Purchase_Order** table and receive a response, as described in [Step 3: Send the Request Message to Insert Records and Receive a Response](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6131-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6131-148">See Also</span></span>  
 <span data-ttu-id="c6131-149">[步驟 1： 建立要求訊息 Purchase_Order 資料表的 Insert 作業](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md) </span><span class="sxs-lookup"><span data-stu-id="c6131-149">[Step 1: Create the Request Message for Insert Operation on Purchase_Order Table](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-insert-operation-on-purchase-order-table.md) </span></span>  
 [<span data-ttu-id="c6131-150">第 4 課： 執行插入作業的採購訂單資料表</span><span class="sxs-lookup"><span data-stu-id="c6131-150">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)