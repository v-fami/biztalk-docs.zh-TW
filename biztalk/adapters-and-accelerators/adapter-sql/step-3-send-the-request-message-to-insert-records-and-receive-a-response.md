---
title: "步驟 3： 傳送要插入的記錄，並接收回應的要求訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a8a8906-7c7d-437c-9f04-345ad4ac460e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db97afa0de19e15e5005e5647279365ea6ba023b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-send-the-request-message-to-insert-records-and-receive-a-response"></a><span data-ttu-id="82eea-102">步驟 3： 傳送要插入的記錄，並接收回應的要求訊息</span><span class="sxs-lookup"><span data-stu-id="82eea-102">Step 3: Send the Request Message to Insert Records and Receive a Response</span></span>
<span data-ttu-id="82eea-103">![步驟 4 之 3](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="82eea-103">![Step 3 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="82eea-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="82eea-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="82eea-105">**目標：**在此步驟中，您可以傳送要插入至記錄的要求訊息**Purchase_Order**資料表，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="82eea-105">**Objective:** In this step, you send the request message to insert records into the **Purchase_Order** table and receive a response.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="82eea-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="82eea-106">Prerequisites</span></span>  
 <span data-ttu-id="82eea-107">您必須先完成[步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應至插入作業要求訊息](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md)。</span><span class="sxs-lookup"><span data-stu-id="82eea-107">You must have completed [Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md).</span></span>  
  
### <a name="to-send-the-request-message-and-receive-a-response"></a><span data-ttu-id="82eea-108">以傳送要求訊息並接收回應</span><span class="sxs-lookup"><span data-stu-id="82eea-108">To send the request message and receive a response</span></span>  
  
1.  <span data-ttu-id="82eea-109">在協調流程中加入下列圖形**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="82eea-109">Add the following shapes to the orchestration under the **Construct Message** shape.</span></span>  
  
    |<span data-ttu-id="82eea-110">形狀圖</span><span class="sxs-lookup"><span data-stu-id="82eea-110">Shape</span></span>|<span data-ttu-id="82eea-111">圖形類型</span><span class="sxs-lookup"><span data-stu-id="82eea-111">Shape Type</span></span>|<span data-ttu-id="82eea-112">屬性</span><span class="sxs-lookup"><span data-stu-id="82eea-112">Properties</span></span>|  
    |-----------|----------------|----------------|  
    |<span data-ttu-id="82eea-113">SendInsertMessage</span><span class="sxs-lookup"><span data-stu-id="82eea-113">SendInsertMessage</span></span>|<span data-ttu-id="82eea-114">Send</span><span class="sxs-lookup"><span data-stu-id="82eea-114">Send</span></span>|<span data-ttu-id="82eea-115">-設定**訊息**至*InsertPO*</span><span class="sxs-lookup"><span data-stu-id="82eea-115">-   Set **Message** to *InsertPO*</span></span><br /><span data-ttu-id="82eea-116">-設定**名稱**至*SendInsertMessage*</span><span class="sxs-lookup"><span data-stu-id="82eea-116">-   Set **Name** to *SendInsertMessage*</span></span>|  
    |<span data-ttu-id="82eea-117">ReceiveInsertResponse</span><span class="sxs-lookup"><span data-stu-id="82eea-117">ReceiveInsertResponse</span></span>|<span data-ttu-id="82eea-118">Receive</span><span class="sxs-lookup"><span data-stu-id="82eea-118">Receive</span></span>|<span data-ttu-id="82eea-119">-設定**啟動**至*False*</span><span class="sxs-lookup"><span data-stu-id="82eea-119">-   Set **Activate** to *False*</span></span><br /><span data-ttu-id="82eea-120">-設定**訊息**至*InsertPOResponse*</span><span class="sxs-lookup"><span data-stu-id="82eea-120">-   Set **Message** to *InsertPOResponse*</span></span><br /><span data-ttu-id="82eea-121">-設定**名稱**至*ReceiveInsertResponse*</span><span class="sxs-lookup"><span data-stu-id="82eea-121">-   Set **Name** to *ReceiveInsertResponse*</span></span>|  
    |<span data-ttu-id="82eea-122">SaveInsertResponse</span><span class="sxs-lookup"><span data-stu-id="82eea-122">SaveInsertResponse</span></span>|<span data-ttu-id="82eea-123">Send</span><span class="sxs-lookup"><span data-stu-id="82eea-123">Send</span></span>|<span data-ttu-id="82eea-124">-設定**訊息**至*InsertPOResponse*</span><span class="sxs-lookup"><span data-stu-id="82eea-124">-   Set **Message** to *InsertPOResponse*</span></span><br /><span data-ttu-id="82eea-125">-設定**名稱**至*SaveInsertResponse*</span><span class="sxs-lookup"><span data-stu-id="82eea-125">-   Set **Name** to *SaveInsertResponse*</span></span>|  
  
2.  <span data-ttu-id="82eea-126">修改**SQLOutboundPort**您在建立[步驟 2： 將要求訊息傳送至 SQL Server 和接收回應](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md)。</span><span class="sxs-lookup"><span data-stu-id="82eea-126">Modify the **SQLOutboundPort** you created in [Step 2: Send the Request Message to SQL Server and Receive Response](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md).</span></span>  
  
    1.  <span data-ttu-id="82eea-127">以滑鼠右鍵按一下協調流程設計師 」 中的連接埠，然後按一下**新作業**。</span><span class="sxs-lookup"><span data-stu-id="82eea-127">Right-click the port in the Orchestration Designer, and then click **New Operation**.</span></span> <span data-ttu-id="82eea-128">若要加入新的作業，連接埠圖形變更**Operation_1**。</span><span class="sxs-lookup"><span data-stu-id="82eea-128">The port shape changes to add a new operation, **Operation_1**.</span></span>  
  
    2.  <span data-ttu-id="82eea-129">按一下**Operation_1** 屬性 視窗中變更 識別項的值**InsertPO**。</span><span class="sxs-lookup"><span data-stu-id="82eea-129">Click **Operation_1** and in the properties window, change the value of Identifier to **InsertPO**.</span></span>  
  
3.  <span data-ttu-id="82eea-130">新增單向傳送埠至協調流程。</span><span class="sxs-lookup"><span data-stu-id="82eea-130">Add a one-way send port to the orchestration.</span></span> <span data-ttu-id="82eea-131">您將使用此連接埠來傳送插入作業的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="82eea-131">You will use this port to send the response message for the Insert operation.</span></span> <span data-ttu-id="82eea-132">設定下列屬性的連接埠。</span><span class="sxs-lookup"><span data-stu-id="82eea-132">Set the following properties for the port.</span></span>  
  
    |<span data-ttu-id="82eea-133">將此屬性設定</span><span class="sxs-lookup"><span data-stu-id="82eea-133">Set this property</span></span>|<span data-ttu-id="82eea-134">此值</span><span class="sxs-lookup"><span data-stu-id="82eea-134">To this value</span></span>|  
    |-----------------------|-------------------|  
    |<span data-ttu-id="82eea-135">**通訊方向**</span><span class="sxs-lookup"><span data-stu-id="82eea-135">**Communication Direction**</span></span>|<span data-ttu-id="82eea-136">Send</span><span class="sxs-lookup"><span data-stu-id="82eea-136">Send</span></span>|  
    |<span data-ttu-id="82eea-137">**通訊模式**</span><span class="sxs-lookup"><span data-stu-id="82eea-137">**Communication Pattern**</span></span>|<span data-ttu-id="82eea-138">單向</span><span class="sxs-lookup"><span data-stu-id="82eea-138">One-Way</span></span>|  
    |<span data-ttu-id="82eea-139">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="82eea-139">**Identifier**</span></span>|<span data-ttu-id="82eea-140">SaveResponsePort</span><span class="sxs-lookup"><span data-stu-id="82eea-140">SaveResponsePort</span></span>|  
  
     <span data-ttu-id="82eea-141">此外，從 Operation_1，若要變更的作業名稱**InsertPO**。</span><span class="sxs-lookup"><span data-stu-id="82eea-141">Also, change the operation name from Operation_1 to **InsertPO**.</span></span>  
  
4.  <span data-ttu-id="82eea-142">連接到動作圖形的連接埠。</span><span class="sxs-lookup"><span data-stu-id="82eea-142">Connect the port to action shapes.</span></span> <span data-ttu-id="82eea-143">在 協調流程設計工具的設計介面上，拖曳動作圖形的連接埠對應綠色控點的綠色箭頭圖形控。</span><span class="sxs-lookup"><span data-stu-id="82eea-143">In Orchestration Designer, on the design surface, drag the green arrow-shaped handle for the port to the corresponding green handle of the action shape.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="82eea-144">在此步驟中，您使用拖放方法將連接埠連接到動作圖形。</span><span class="sxs-lookup"><span data-stu-id="82eea-144">In this step, you use the drag-and-drop method to connect ports to action shapes.</span></span> <span data-ttu-id="82eea-145">代替使用動作圖形的作業屬性將動作圖形連接到連接埠。</span><span class="sxs-lookup"><span data-stu-id="82eea-145">You could instead use the operation property of an action shape to connect the action shape to a port.</span></span>  
  
     <span data-ttu-id="82eea-146">連接埠和動作圖形連接，如下所示：</span><span class="sxs-lookup"><span data-stu-id="82eea-146">Connect the ports and action shapes as follows:</span></span>  
  
    -   <span data-ttu-id="82eea-147">連接**SendInsertMessage**至動作圖形**要求**控點**InsertPO**作業**SQLOutboundPort**。</span><span class="sxs-lookup"><span data-stu-id="82eea-147">Connect the **SendInsertMessage** action shape to the **Request** handle of the **InsertPO** operation of the **SQLOutboundPort**.</span></span>  
  
    -   <span data-ttu-id="82eea-148">連接**ReceiveInsertResponse**至動作圖形**回應**控點**InsertPO**作業**SQLOutboundPort**。</span><span class="sxs-lookup"><span data-stu-id="82eea-148">Connect the **ReceiveInsertResponse** action shape to the **Response** handle of the **InsertPO** operation of the **SQLOutboundPort**.</span></span>  
  
    -   <span data-ttu-id="82eea-149">連接**SaveInsertResponse**至動作圖形**要求**控點**SaveResponsePort**。</span><span class="sxs-lookup"><span data-stu-id="82eea-149">Connect the **SaveInsertResponse** action shape to the **Request** handle of the **SaveResponsePort**.</span></span>  
  
5.  <span data-ttu-id="82eea-150">下圖顯示進行中協調流程。</span><span class="sxs-lookup"><span data-stu-id="82eea-150">The following figure shows the in-progress orchestration.</span></span>  
  
     <span data-ttu-id="82eea-151">![完成協調流程](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-09-comp-orch.gif "sql_adap_tut_09_comp_orch")</span><span class="sxs-lookup"><span data-stu-id="82eea-151">![Complete orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-09-comp-orch.gif "sql_adap_tut_09_comp_orch")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="82eea-152">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="82eea-152">What did I just do?</span></span>  
 <span data-ttu-id="82eea-153">傳送要求來插入記錄，到**Purchase_Order**資料表，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="82eea-153">You sent the request to insert records into the **Purchase_Order** table and receive a response.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="82eea-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="82eea-154">Next Steps</span></span>  
 <span data-ttu-id="82eea-155">中所述，建置專案時，[步驟 4： 建置專案](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md)。</span><span class="sxs-lookup"><span data-stu-id="82eea-155">You build the project, as described in [Step 4: Build the Project](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82eea-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82eea-156">See Also</span></span>  
 <span data-ttu-id="82eea-157">[步驟 2： 將 UPDATE_EMPLOYEE 回應訊息對應至插入作業要求訊息](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md) </span><span class="sxs-lookup"><span data-stu-id="82eea-157">[Step 2: Map the UPDATE_EMPLOYEE Response Message to Insert Operation Request Message](../../adapters-and-accelerators/adapter-sql/step-2-map-update_employee-response-to-insert-operation-request.md) </span></span>  
 <span data-ttu-id="82eea-158">[步驟 4： 建置專案](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md) </span><span class="sxs-lookup"><span data-stu-id="82eea-158">[Step 4: Build the Project](../../adapters-and-accelerators/adapter-sql/step-4-build-the-project.md) </span></span>  
 [<span data-ttu-id="82eea-159">第 4 課： 執行插入作業的採購訂單資料表</span><span class="sxs-lookup"><span data-stu-id="82eea-159">Lesson 4: Perform an Insert Operation on the Purchase Order Table</span></span>](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)