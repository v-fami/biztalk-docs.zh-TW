---
title: 步驟 7 （內部部署）： 建立協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c0b6d0e-cf00-4eee-9b89-28210bad46f4
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc072b664b453a3f10b624f75fe161a515ecc902
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975815"
---
# <a name="step-7-on-premises-create-an-orchestration"></a><span data-ttu-id="48aac-102">步驟 7 （內部部署）： 建立協調流程</span><span class="sxs-lookup"><span data-stu-id="48aac-102">Step 7 (On Premises): Create an Orchestration</span></span>
<span data-ttu-id="48aac-103">根據商務案例之後,[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收銷售訂單訊息的服務匯流排佇列中，它需要檢查訊息中所訂購的數量是否大於 100。</span><span class="sxs-lookup"><span data-stu-id="48aac-103">According to the business scenario, after [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives the sales order message from the Service Bus Queue, it needs to check whether the quantity ordered in the message is greater than 100.</span></span> <span data-ttu-id="48aac-104">如果數量大於 100 時，要將訊息插入至**SalesOrder**資料表。</span><span class="sxs-lookup"><span data-stu-id="48aac-104">If the quantity is greater than 100, the message is inserted into the **SalesOrder** table.</span></span> <span data-ttu-id="48aac-105">否則，訊息會傳送至共用的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="48aac-105">Otherwise, the message is sent to a shared file location.</span></span> <span data-ttu-id="48aac-106">Northwind 會達成此商務邏輯，藉由建立協調流程。</span><span class="sxs-lookup"><span data-stu-id="48aac-106">Northwind achieves this business logic by creating an orchestration.</span></span> <span data-ttu-id="48aac-107">本主題提供有關如何建立協調流程的逐步指引。</span><span class="sxs-lookup"><span data-stu-id="48aac-107">This topic provides step-by-step guidance on how to create the orchestration.</span></span>  
  
### <a name="to-add-an-orchestration-to-the-includebtsbiztalkservernoversionincludesbtsbiztalkservernoversion-mdmd-project"></a><span data-ttu-id="48aac-108">若要新增至協調流程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案</span><span class="sxs-lookup"><span data-stu-id="48aac-108">To add an orchestration to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project</span></span>  
  
1. <span data-ttu-id="48aac-109">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您已經建立，以滑鼠右鍵按一下專案，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="48aac-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] you already created, right-click the project, point to **Add**, and then click **New Item**.</span></span>  
  
2. <span data-ttu-id="48aac-110">在 **新項目**對話方塊中，選取**BizTalk 協調流程**，輸入對應名稱為`OrderProcessing.odx`，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="48aac-110">In the **New Item** dialog box, select **BizTalk Orchestration**, enter the map name as `OrderProcessing.odx`, and then click **Add**.</span></span>  
  
## <a name="create-messages-for-the-orchestration"></a><span data-ttu-id="48aac-111">建立協調流程的訊息</span><span class="sxs-lookup"><span data-stu-id="48aac-111">Create Messages for the Orchestration</span></span>  
 <span data-ttu-id="48aac-112">您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。</span><span class="sxs-lookup"><span data-stu-id="48aac-112">The schema that you generated earlier describes the “types” required for the messages in the orchestration.</span></span> <span data-ttu-id="48aac-113">訊息通常是的變數，其對應的結構描述所定義的型別。</span><span class="sxs-lookup"><span data-stu-id="48aac-113">A message is typically a variable, the type for which defined by the corresponding schema.</span></span> <span data-ttu-id="48aac-114">現在，您必須建立協調流程的訊息，並將它們連結至您稍早產生的結構描述。</span><span class="sxs-lookup"><span data-stu-id="48aac-114">You must now create messages for the orchestration and link them to schemas you generated earlier.</span></span> <span data-ttu-id="48aac-115">您需要建立下列三個訊息：</span><span class="sxs-lookup"><span data-stu-id="48aac-115">You need to create following three messages:</span></span>  
  
|<span data-ttu-id="48aac-116">訊息名稱</span><span class="sxs-lookup"><span data-stu-id="48aac-116">Message Name</span></span>|<span data-ttu-id="48aac-117">對應到結構描述</span><span class="sxs-lookup"><span data-stu-id="48aac-117">Corresponds to schema</span></span>|  
|------------------|---------------------------|  
|<span data-ttu-id="48aac-118">Message1_SO_Inbound</span><span class="sxs-lookup"><span data-stu-id="48aac-118">Message1_SO_Inbound</span></span>|<span data-ttu-id="48aac-119">這是訊息的執行個體**ECommerceSalesOrder.xsd**結構描述。</span><span class="sxs-lookup"><span data-stu-id="48aac-119">This message is an instance of the **ECommerceSalesOrder.xsd** schema.</span></span>|  
|<span data-ttu-id="48aac-120">Message2_SO_Inbound</span><span class="sxs-lookup"><span data-stu-id="48aac-120">Message2_SO_Inbound</span></span>|<span data-ttu-id="48aac-121">此訊息是一份**Message1_SO_Inbound**。</span><span class="sxs-lookup"><span data-stu-id="48aac-121">This message is a copy of the **Message1_SO_Inbound**.</span></span> <span data-ttu-id="48aac-122">最佳做法，您必須建立訊息的複本，並修改新訊息，讓原始訊息保持不變。</span><span class="sxs-lookup"><span data-stu-id="48aac-122">As a best practice, you must create a copy of the message and then modify the new message, leaving the original message intact.</span></span> <span data-ttu-id="48aac-123">如需詳細資訊，請參閱 < [BizTalk Server 訊息](http://msdn.microsoft.com/library/aa560436)。</span><span class="sxs-lookup"><span data-stu-id="48aac-123">For more information, see [The BizTalk Server Message](http://msdn.microsoft.com/library/aa560436).</span></span>|  
|<span data-ttu-id="48aac-124">Message1_SO_Outbound</span><span class="sxs-lookup"><span data-stu-id="48aac-124">Message1_SO_Outbound</span></span>|<span data-ttu-id="48aac-125">這是訊息的執行個體**TableOperations.dbo.SalesOrder (Insert)** 結構描述。</span><span class="sxs-lookup"><span data-stu-id="48aac-125">This message is an instance of the **TableOperations.dbo.SalesOrder (Insert)** schema.</span></span>|  
  
#### <a name="to-create-the-messages"></a><span data-ttu-id="48aac-126">建立訊息</span><span class="sxs-lookup"><span data-stu-id="48aac-126">To create the messages</span></span>  
  
1.  <span data-ttu-id="48aac-127">開啟**協調流程檢視**的 BizTalk 專案中，如果它尚未開啟的視窗。</span><span class="sxs-lookup"><span data-stu-id="48aac-127">Open the **Orchestration View** window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="48aac-128">若要這樣做，請按一下**檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="48aac-128">To do so, click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
2.  <span data-ttu-id="48aac-129">在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="48aac-129">In Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
3.  <span data-ttu-id="48aac-130">以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="48aac-130">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="48aac-131">在 [**屬性**] 窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="48aac-131">In the **Properties** pane for the **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="48aac-132">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="48aac-132">Property name</span></span>|<span data-ttu-id="48aac-133">執行動作</span><span class="sxs-lookup"><span data-stu-id="48aac-133">Perform action</span></span>|  
    |-------------------|--------------------|  
    |<span data-ttu-id="48aac-134">識別碼</span><span class="sxs-lookup"><span data-stu-id="48aac-134">Identifier</span></span>|<span data-ttu-id="48aac-135">輸入 `Message1_SO_Inbound`</span><span class="sxs-lookup"><span data-stu-id="48aac-135">Enter `Message1_SO_Inbound`</span></span>|  
    |<span data-ttu-id="48aac-136">訊息類型</span><span class="sxs-lookup"><span data-stu-id="48aac-136">Message Type</span></span>|<span data-ttu-id="48aac-137">從下拉式清單中，依序展開**結構描述**，然後選取*OrderProcessingDemo.ECommerceSalesOrder*，其中 *[orderprocessingdemo]* 是 BizTalk 的名稱專案。</span><span class="sxs-lookup"><span data-stu-id="48aac-137">From the drop-down list, expand **Schemas**, and then select *OrderProcessingDemo.ECommerceSalesOrder*, where *OrderProcessingDemo* is the name of your BizTalk project.</span></span> <span data-ttu-id="48aac-138">*ECommerceSalesOrder*是從 「 服務匯流排 」 佇列接收的銷售訂單訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="48aac-138">*ECommerceSalesOrder* is the schema for the sales order message received from the Service Bus Queue.</span></span>|  
  
5.  <span data-ttu-id="48aac-139">重複步驟來建立訊息詳細資料如下：</span><span class="sxs-lookup"><span data-stu-id="48aac-139">Repeat the steps to create the messages with following details:</span></span>  
  
    |<span data-ttu-id="48aac-140">訊息名稱</span><span class="sxs-lookup"><span data-stu-id="48aac-140">Message name</span></span>||  
    |------------------|-|  
    |<span data-ttu-id="48aac-141">Message2_SO_Inbound</span><span class="sxs-lookup"><span data-stu-id="48aac-141">Message2_SO_Inbound</span></span>|<span data-ttu-id="48aac-142">-設定**識別碼**至 `Message2_SO_Inbound`</span><span class="sxs-lookup"><span data-stu-id="48aac-142">-   Set **Identifier** to `Message2_SO_Inbound`</span></span><br /><span data-ttu-id="48aac-143">-設定**訊息類型**到*OrderProcessingDemo.ECommerceSalesOrder*</span><span class="sxs-lookup"><span data-stu-id="48aac-143">-   Set **Message Type** to *OrderProcessingDemo.ECommerceSalesOrder*</span></span>|  
    |<span data-ttu-id="48aac-144">Message1_SO_Outbound</span><span class="sxs-lookup"><span data-stu-id="48aac-144">Message1_SO_Outbound</span></span>|<span data-ttu-id="48aac-145">-設定**識別碼**至 `Message1_SO_Outound`</span><span class="sxs-lookup"><span data-stu-id="48aac-145">-   Set **Identifier** to `Message1_SO_Outound`</span></span><br /><span data-ttu-id="48aac-146">-設定**訊息類型**到*OrderProcessingDemo.TableOperation_dbo_SalesOrder.Insert*</span><span class="sxs-lookup"><span data-stu-id="48aac-146">-   Set **Message Type** to *OrderProcessingDemo.TableOperation_dbo_SalesOrder.Insert*</span></span>|  
  
## <a name="add-shapes-to-the-orchestration"></a><span data-ttu-id="48aac-147">新增圖形至協調流程</span><span class="sxs-lookup"><span data-stu-id="48aac-147">Add Shapes to the Orchestration</span></span>  
 <span data-ttu-id="48aac-148">協調流程圖形定義的流程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="48aac-148">Orchestration shapes define the flow of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span> <span data-ttu-id="48aac-149">在本節中，您可以新增必要的圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="48aac-149">In this section, you add the required shapes to the orchestration.</span></span>  
  
#### <a name="to-add-shapes-to-the-orchestration"></a><span data-ttu-id="48aac-150">若要將圖形加入至協調流程</span><span class="sxs-lookup"><span data-stu-id="48aac-150">To add shapes to the orchestration</span></span>  
  
1.  <span data-ttu-id="48aac-151">若要開始，您必須新增**接收**圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-151">To start with, you must add a **Receive** shape.</span></span> <span data-ttu-id="48aac-152">此圖形會接收連入的服務匯流排佇列的銷售訂單訊息。</span><span class="sxs-lookup"><span data-stu-id="48aac-152">This shape receives the incoming sales order message from the Service Bus Queue.</span></span> <span data-ttu-id="48aac-153">在 [接收] 圖形上設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="48aac-153">Set the following properties on the receive shape.</span></span>  
  
    1.  <span data-ttu-id="48aac-154">設定**啟用**要 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="48aac-154">Set **Activate** to **True**.</span></span>  
  
    2.  <span data-ttu-id="48aac-155">設定**訊息**要**Message1_SO_Inbound**。</span><span class="sxs-lookup"><span data-stu-id="48aac-155">Set **Message** to **Message1_SO_Inbound**.</span></span>  
  
    3.  <span data-ttu-id="48aac-156">設定**名稱**要**ReceiveOrder**。</span><span class="sxs-lookup"><span data-stu-id="48aac-156">Set **Name** to **ReceiveOrder**.</span></span>  
  
2.  <span data-ttu-id="48aac-157">如先前所述，您必須建立一份原始接收進入協調流程的銷售訂單訊息。</span><span class="sxs-lookup"><span data-stu-id="48aac-157">As mentioned earlier, you must create a copy of the original sales order message that is received into the orchestration.</span></span>  
  
    1.  <span data-ttu-id="48aac-158">拖放**建構的訊息**圖形下**ReceiveOrder**圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-158">Drag-and-drop a **Construct Message** shape under the **ReceiveOrder** shape.</span></span> <span data-ttu-id="48aac-159">因為您可以使用此圖形來建構類型 Message2_SO_Inbound 的訊息，設定**建構的訊息**屬性設**Message2_SO_Inbound**。</span><span class="sxs-lookup"><span data-stu-id="48aac-159">Because you use this shape to construct a message of type Message2_SO_Inbound, set the **Messages Constructed** property to **Message2_SO_Inbound**.</span></span>  
  
    2.  <span data-ttu-id="48aac-160">新增**訊息指派**圖形內**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-160">Add a **Message Assignment** shape within the **Construct Message** shape.</span></span> <span data-ttu-id="48aac-161">按兩下圖形以開啟 運算式編輯器中，並新增下列內容：</span><span class="sxs-lookup"><span data-stu-id="48aac-161">Double-click the shape to open the Expression Editor, and add the following:</span></span>  
  
        ```  
        Message2_SO_Inbound = Message1_SO_Inbound; //copy the message  
        Message2_SO_Inbound(*) = Message1_SO_Inbound(*); //copy the context properties on the message  
        ```  
  
         <span data-ttu-id="48aac-162">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="48aac-162">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="48aac-163">根據商務案例中，訊息必須傳送至不同的目的地，根據已排序的項目數量。</span><span class="sxs-lookup"><span data-stu-id="48aac-163">According to the business scenario, the message must be sent to different destinations based on the quantity of ordered items.</span></span> <span data-ttu-id="48aac-164">因此，您必須現在擷取數量值傳入銷售訂單訊息。</span><span class="sxs-lookup"><span data-stu-id="48aac-164">So, you must now extract the quantity value from the incoming sales order message.</span></span>  
  
    1.  <span data-ttu-id="48aac-165">**Quantity** (ECommerceSalesOrder.xsd) 的輸入訊息中的項目包含訂購的數量的值。</span><span class="sxs-lookup"><span data-stu-id="48aac-165">The **Quantity** element in the inbound message (ECommerceSalesOrder.xsd) contains the value of the ordered quantity.</span></span> <span data-ttu-id="48aac-166">您必須提升該屬性，使項目可用於協調流程中的運算式。</span><span class="sxs-lookup"><span data-stu-id="48aac-166">You must promote that property so that the element can be used within the expressions in the orchestration.</span></span> <span data-ttu-id="48aac-167">若要升級的屬性，開啟**ECommerceSalesOrder.xsd**結構描述，以滑鼠右鍵按一下**數量**，指向**升階**，然後按一下 **快速升級**.</span><span class="sxs-lookup"><span data-stu-id="48aac-167">To promote the property, open the **ECommerceSalesOrder.xsd** schema, right-click **Quantity**, point to **Promote**, and then click **Quick Promotions**.</span></span>  
  
    2.  <span data-ttu-id="48aac-168">建立變數來儲存數量值。</span><span class="sxs-lookup"><span data-stu-id="48aac-168">Create a variable to store the quantity value.</span></span> <span data-ttu-id="48aac-169">若要建立的變數，從**協調流程檢視**，以滑鼠右鍵按一下**變數**，然後按一下**新變數**。</span><span class="sxs-lookup"><span data-stu-id="48aac-169">To create a variable, from the **Orchestration View**, right-click **Variables**, and then click **New Variable**.</span></span> <span data-ttu-id="48aac-170">設定變數的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="48aac-170">Set the following properties for the variable:</span></span>  
  
        |<span data-ttu-id="48aac-171">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="48aac-171">Property name</span></span>|<span data-ttu-id="48aac-172">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="48aac-172">Value</span></span>|  
        |-------------------|-----------|  
        |<span data-ttu-id="48aac-173">識別碼</span><span class="sxs-lookup"><span data-stu-id="48aac-173">Identifier</span></span>|<span data-ttu-id="48aac-174">輸入 `quantityOrdered`</span><span class="sxs-lookup"><span data-stu-id="48aac-174">Enter `quantityOrdered`</span></span>|  
        |<span data-ttu-id="48aac-175">類型</span><span class="sxs-lookup"><span data-stu-id="48aac-175">Type</span></span>|<span data-ttu-id="48aac-176">選取  **Int32**。</span><span class="sxs-lookup"><span data-stu-id="48aac-176">Select **Int32**.</span></span>|  
  
    3.  <span data-ttu-id="48aac-177">您現在必須將指派中的值**Quantity**項目**quantityOrdered**變數。</span><span class="sxs-lookup"><span data-stu-id="48aac-177">You must now assign the value in the **Quantity** element to the **quantityOrdered** variable.</span></span> <span data-ttu-id="48aac-178">拖放**運算式編輯器**之後**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-178">Drag-and-drop an **Expression Editor** after the **Construct Message** shape.</span></span> <span data-ttu-id="48aac-179">開啟編輯器，並輸入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="48aac-179">Open the editor and enter the following expression:</span></span>  
  
        ```  
        quantityOrdered = Message2_SO_Inbound.Quantity;  
        ```  
  
         <span data-ttu-id="48aac-180">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="48aac-180">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="48aac-181">解壓縮之後的訂單數量，您現在需要建立的決策區塊，您的版面配置兩個不同的訊息流程會採用的路徑。</span><span class="sxs-lookup"><span data-stu-id="48aac-181">After extracting the order quantity, you now need to create a decision block where you layout two separate paths the message flow takes.</span></span> <span data-ttu-id="48aac-182">您在協調流程中建立的決策區塊加**決定**圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-182">You create the decision block in an orchestration by adding a **Decide** shape.</span></span>  
  
    1.  <span data-ttu-id="48aac-183">將拖放**決定**圖形之後**運算式編輯器**圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-183">Drag and drop a **Decide** shape after the **Expression Editor** shape.</span></span>  
  
    2.  <span data-ttu-id="48aac-184">選取 [ **Rule_1**圖形然後在**屬性**] 視窗中，指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="48aac-184">Select the **Rule_1** shape and in the **Properties** window, specify the following:</span></span>  
  
        |<span data-ttu-id="48aac-185">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="48aac-185">Property name</span></span>|<span data-ttu-id="48aac-186">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="48aac-186">Value</span></span>|  
        |-------------------|-----------|  
        |<span data-ttu-id="48aac-187">識別碼</span><span class="sxs-lookup"><span data-stu-id="48aac-187">Identifier</span></span>|<span data-ttu-id="48aac-188">輸入`Yes`。</span><span class="sxs-lookup"><span data-stu-id="48aac-188">Enter `Yes`.</span></span> <span data-ttu-id="48aac-189">**注意︰** 其他路由的預設名稱為**Else**。</span><span class="sxs-lookup"><span data-stu-id="48aac-189">**Note:**  The other route is by default named **Else**.</span></span>|  
        |<span data-ttu-id="48aac-190">運算式</span><span class="sxs-lookup"><span data-stu-id="48aac-190">Expression</span></span>|<span data-ttu-id="48aac-191">輸入`quantityOrdered > 100`。</span><span class="sxs-lookup"><span data-stu-id="48aac-191">Enter `quantityOrdered > 100`.</span></span>|  
  
         <span data-ttu-id="48aac-192">您現在有兩個可用的路由。</span><span class="sxs-lookup"><span data-stu-id="48aac-192">You now have two routes available.</span></span> <span data-ttu-id="48aac-193">如果中的值**quantityOrdered**變數是否大於 100，訊息會**是**路由。</span><span class="sxs-lookup"><span data-stu-id="48aac-193">If the value in the **quantityOrdered** variable is greater than 100, the message takes the **Yes** route.</span></span> <span data-ttu-id="48aac-194">否則，它會帶**Else**路由。</span><span class="sxs-lookup"><span data-stu-id="48aac-194">Otherwise, it takes the **Else** route.</span></span> <span data-ttu-id="48aac-195">您現在必須定義要在每個路由中執行的動作。</span><span class="sxs-lookup"><span data-stu-id="48aac-195">You must now define the actions to be performed within each route.</span></span>  
  
5.  <span data-ttu-id="48aac-196">根據商務案例，如果訂單數量大於 100，訊息必須插入至 SalesOrder 資料表。</span><span class="sxs-lookup"><span data-stu-id="48aac-196">According to the business scenario, if the order quantity is greater than 100, the message must be inserted into the SalesOrder table.</span></span> <span data-ttu-id="48aac-197">因此，在**是**路由，您必須轉換 ECommerceSalesOrder.xsd 結構描述 TableOperations.SalesOrder.Insert 結構描述。</span><span class="sxs-lookup"><span data-stu-id="48aac-197">So, in the **Yes** route, you must transform the ECommerceSalesOrder.xsd schema to the TableOperations.SalesOrder.Insert schema.</span></span> <span data-ttu-id="48aac-198">主題中建立插入結構描述[步驟 5 （內部部署）： 產生將訊息插入至 SalesOrder 資料表的結構描述](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md)。</span><span class="sxs-lookup"><span data-stu-id="48aac-198">You created the Insert schema in the topic [Step 5 (On Premises): Generate the Schema for Inserting a Message inito SalesOrder Table](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md).</span></span> <span data-ttu-id="48aac-199">之後轉換結構描述，您必須傳送出訊息，以 SQL Server 資料庫資料表的訊息。</span><span class="sxs-lookup"><span data-stu-id="48aac-199">After transforming the schema, you must send the message to the message out to the SQL Server database table.</span></span>  
  
    1.  <span data-ttu-id="48aac-200">內 **[是]** 路由傳送、 拖曳和卸除**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-200">Within the **Yes** route, drag and drop a **Construct Message** shape.</span></span> <span data-ttu-id="48aac-201">設定**建構的訊息**至圖形的屬性**Message1_SO_Outbound**。</span><span class="sxs-lookup"><span data-stu-id="48aac-201">Set the **Messages Constructed** property for the shape to **Message1_SO_Outbound**.</span></span>  
  
    2.  <span data-ttu-id="48aac-202">內**建構的訊息**圖形加入**轉換**圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-202">Within the **Construct Message** shape add a **Transform** shape.</span></span> <span data-ttu-id="48aac-203">按兩下圖形以開啟**轉換組態** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="48aac-203">Double-click the shape to open the **Transform Configuration** dialog box.</span></span> <span data-ttu-id="48aac-204">執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="48aac-204">Do the following:</span></span>  
  
        1.  <span data-ttu-id="48aac-205">選取 **現有的對應**選項。</span><span class="sxs-lookup"><span data-stu-id="48aac-205">Select the **Existing Map** option.</span></span>  
  
        2.  <span data-ttu-id="48aac-206">從**完整格式對應名稱**下拉式清單中，選取**OrderProcessingDemo.SalesOrder_SQL**。</span><span class="sxs-lookup"><span data-stu-id="48aac-206">From the **Fully Qualified Map Name** drop-down, select **OrderProcessingDemo.SalesOrder_SQL**.</span></span>  
  
        3.  <span data-ttu-id="48aac-207">針對**來源**，選取**Message2_SO_Inbound**。</span><span class="sxs-lookup"><span data-stu-id="48aac-207">For **Source**, select **Message2_SO_Inbound**.</span></span>  
  
        4.  <span data-ttu-id="48aac-208">針對**目的地**，選取**Message1_SO_Outound**。</span><span class="sxs-lookup"><span data-stu-id="48aac-208">For **Destination**, select **Message1_SO_Outound**.</span></span>  
  
    3.  <span data-ttu-id="48aac-209">之後**建構的訊息**圖形、 拖曳和卸除**傳送**圖形，並設定**訊息**圖形，以屬性`Message1_SO_Outbound`。</span><span class="sxs-lookup"><span data-stu-id="48aac-209">After the **Construct Message** shape, drag and drop a **Send** shape and set the **Message** property for the shape to `Message1_SO_Outbound`.</span></span>  
  
6.  <span data-ttu-id="48aac-210">根據商務案例，如果訂單數量小於 100，訊息必須傳送至共用的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="48aac-210">According to the business scenario, if the order quantity is less than 100, the message must be sent to a shared file location.</span></span> <span data-ttu-id="48aac-211">因此，在**Else**路由，您必須新增 「 傳送 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-211">So, in the **Else** route you must add a send shape.</span></span>  
  
    1.  <span data-ttu-id="48aac-212">內**Else**路由傳送、 拖曳和卸除**傳送**圖形，並將**訊息**圖形，以屬性`Message2_SO_Inbound`。</span><span class="sxs-lookup"><span data-stu-id="48aac-212">Within the **Else** route, drag and drop a **Send** shape, and set the **Message** property for the shape to `Message2_SO_Inbound`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="48aac-213">因為相同接收來自服務匯流排佇列的訊息會傳送至檔案位置，而不進行任何處理，您可以設定為 Message2_SO_Inbound 的訊息。</span><span class="sxs-lookup"><span data-stu-id="48aac-213">You set the Message to Message2_SO_Inbound because the same message that is received from the Service Bus Queue is sent to the file location, without any processing.</span></span> <span data-ttu-id="48aac-214">Message2_SO_Inbound 表示接收的服務匯流排佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="48aac-214">Message2_SO_Inbound represents the message that is received by the Service Bus Queue.</span></span>  
  
## <a name="add-ports-to-the-orchestration"></a><span data-ttu-id="48aac-215">將連接埠加入協調流程</span><span class="sxs-lookup"><span data-stu-id="48aac-215">Add Ports to the Orchestration</span></span>  
 <span data-ttu-id="48aac-216">連接埠代表輸入和輸出媒介中轉移相關的協調流程的訊息。</span><span class="sxs-lookup"><span data-stu-id="48aac-216">Ports represent the input and output mediums of the message with respect to an orchestration.</span></span> <span data-ttu-id="48aac-217">訊息所使用的協調流程中使用的接收埠，並送出使用傳送埠。</span><span class="sxs-lookup"><span data-stu-id="48aac-217">Messages are consumed by an orchestration using a receive port and are sent out using a send port.</span></span> <span data-ttu-id="48aac-218">在商務案例中，會將訊息從一個媒體 （服務匯流排佇列） 接收，並傳送到兩個不同位置 （SQL Server 資料庫或檔案共用位置） 為基礎的訊息處理。</span><span class="sxs-lookup"><span data-stu-id="48aac-218">In the business scenario, a message is received from one medium (Service Bus Queue) and then sent out to two different locations (SQL Server database or a file share location) based on message processing.</span></span> <span data-ttu-id="48aac-219">因此，您必須建立一個接收埠和兩個傳送埠協調流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="48aac-219">So, you must create one receive port and two send ports as part of the orchestration.</span></span>  
  
#### <a name="to-add-ports"></a><span data-ttu-id="48aac-220">若要新增連接埠</span><span class="sxs-lookup"><span data-stu-id="48aac-220">To add ports</span></span>  
  
1.  <span data-ttu-id="48aac-221">將拖放**連接埠**圖形至**連接埠介面**窗格**協調流程設計師**以啟動**連接埠組態精靈**。</span><span class="sxs-lookup"><span data-stu-id="48aac-221">Drag and drop a **Port** shape to the **Port Surface** pane of the **Orchestration Designer** to launch the **Port Configuration Wizard**.</span></span> <span data-ttu-id="48aac-222">在 [**歡迎**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="48aac-222">On the **Welcome** page, click **Next**.</span></span>  
  
2.  <span data-ttu-id="48aac-223">在 **連接埠內容**頁面上，為埠命名`ReceiveSO`，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="48aac-223">In the **Port Properties** page, name the port as `ReceiveSO` and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="48aac-224">在 **選取連接埠類型**頁面上，選取**建立新的連接埠類型**選項，然後選取**單向**通訊模式中，保留 存取限制的預設值，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="48aac-224">In the **Select a Port Type** page, select **Create a new port type** option, select the **One-Way** communication pattern, leave the default for access restrictions, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="48aac-225">在**連接埠繫結**頁面上，針對連接埠的選取方向**我將一律接收訊息，在此連接埠**保留為預設值，飛過的連接埠，然後按一下 [**下一步]**.</span><span class="sxs-lookup"><span data-stu-id="48aac-225">In the **Port Binding** page, for the port direction, select **I’ll always be receiving messages on this port**, leave the port biding to the default value, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="48aac-226">在最後一個頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="48aac-226">On the last page, click **Finish**.</span></span>  
  
6.  <span data-ttu-id="48aac-227">重複步驟來建立兩個傳送埠。</span><span class="sxs-lookup"><span data-stu-id="48aac-227">Repeat the steps to create the two send ports.</span></span> <span data-ttu-id="48aac-228">在建立連接埠時，請指定下列值。</span><span class="sxs-lookup"><span data-stu-id="48aac-228">Specify the following values while creating the ports.</span></span>  
  
    |<span data-ttu-id="48aac-229">連接埠名稱</span><span class="sxs-lookup"><span data-stu-id="48aac-229">Port Name</span></span>|<span data-ttu-id="48aac-230">屬性</span><span class="sxs-lookup"><span data-stu-id="48aac-230">Properties</span></span>|  
    |---------------|----------------|  
    |<span data-ttu-id="48aac-231">[Sendtosql]</span><span class="sxs-lookup"><span data-stu-id="48aac-231">SendToSQL</span></span>|<span data-ttu-id="48aac-232">-設定**名稱**到**SendToSQL**</span><span class="sxs-lookup"><span data-stu-id="48aac-232">-   Set **Name** to **SendToSQL**</span></span><br /><span data-ttu-id="48aac-233">-選取**建立新的連接埠類型**</span><span class="sxs-lookup"><span data-stu-id="48aac-233">-   Select **Create a new port type**</span></span><br /><span data-ttu-id="48aac-234">集通訊模式來**單向**</span><span class="sxs-lookup"><span data-stu-id="48aac-234">-   Set communication pattern to **One-way**</span></span><br /><span data-ttu-id="48aac-235">-若要設定連接埠方向**我將總是傳送的訊息在此連接埠**</span><span class="sxs-lookup"><span data-stu-id="48aac-235">-   Set port direction to **I’ll always be sending messages on this port**</span></span>|  
    |<span data-ttu-id="48aac-236">[Sendtofile]</span><span class="sxs-lookup"><span data-stu-id="48aac-236">SendToFile</span></span>|<span data-ttu-id="48aac-237">-設定**名稱**到 **[sendtofile]**</span><span class="sxs-lookup"><span data-stu-id="48aac-237">-   Set **Name** to **SendToFile**</span></span><br /><span data-ttu-id="48aac-238">-選取**建立新的連接埠類型**</span><span class="sxs-lookup"><span data-stu-id="48aac-238">-   Select **Create a new port type**</span></span><br /><span data-ttu-id="48aac-239">集通訊模式來**單向**</span><span class="sxs-lookup"><span data-stu-id="48aac-239">-   Set communication pattern to **One-way**</span></span><br /><span data-ttu-id="48aac-240">-若要設定連接埠方向**我將總是傳送的訊息在此連接埠**</span><span class="sxs-lookup"><span data-stu-id="48aac-240">-   Set port direction to **I’ll always be sending messages on this port**</span></span>|  
  
## <a name="connect-ports-and-message-shapes"></a><span data-ttu-id="48aac-241">連接連接埠和訊息圖形</span><span class="sxs-lookup"><span data-stu-id="48aac-241">Connect Ports and Message Shapes</span></span>  
 <span data-ttu-id="48aac-242">您現在必須連接連接埠和訊息圖形，以完成協調流程。</span><span class="sxs-lookup"><span data-stu-id="48aac-242">You must now connect the ports and the message shapes to complete the orchestration.</span></span> <span data-ttu-id="48aac-243">當收到訊息時，會啟動協調流程**ReceiveOrder**圖形與協調流程結束時將訊息送出兩個傳送圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-243">The orchestration starts when the message is received by the **ReceiveOrder** shape and the orchestration exits when the message is sent out by the two Send shapes.</span></span> <span data-ttu-id="48aac-244">您必須使用此條件來連接的連接埠和訊息圖形</span><span class="sxs-lookup"><span data-stu-id="48aac-244">You must use this criterion to connect the ports and the message shapes</span></span>  
  
#### <a name="to-connect-ports-with-message-shapes"></a><span data-ttu-id="48aac-245">連接埠與訊息圖形</span><span class="sxs-lookup"><span data-stu-id="48aac-245">To connect ports with message shapes</span></span>  
  
1.  <span data-ttu-id="48aac-246">連接**ReceiveSO**接收埠以**ReceiveOrder**圖形。</span><span class="sxs-lookup"><span data-stu-id="48aac-246">Connect the **ReceiveSO** receive port to the **ReceiveOrder** shape.</span></span>  
  
2.  <span data-ttu-id="48aac-247">連接 「 傳送 」 圖形之下 **[是]** 路由傳送至**SendToSQL**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="48aac-247">Connect the Send shape under the **Yes** route to the **SendToSQL** send port.</span></span> <span data-ttu-id="48aac-248">這表示如果訊息進入此路由 (**quantityOrdered** > 100)，它會傳送到**SalesOrder** SQL Server 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="48aac-248">This denotes that if a message enters this route (**quantityOrdered** > 100), it’ll be sent to the **SalesOrder** table in the SQL Server database.</span></span>  
  
3.  <span data-ttu-id="48aac-249">連接 「 傳送 」 圖形之下**Else**路由傳送至**SendToFile**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="48aac-249">Connect the Send shape under the **Else** route to the **SendToFile** send port.</span></span> <span data-ttu-id="48aac-250">這表示如果訊息進入此路由 (**quantityOrdered** < = 100)，它會傳送至指定的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="48aac-250">This denotes that if a message enters this route (**quantityOrdered** <= 100), it’ll be sent to a specified file location.</span></span>  
  
     <span data-ttu-id="48aac-251">協調流程必須如下所示：</span><span class="sxs-lookup"><span data-stu-id="48aac-251">The orchestration must resemble the following:</span></span>  
  
     <span data-ttu-id="48aac-252">![協調流程](../core/media/bts2010r2-tut1-orch.jpg "BTS2010R2_Tut1_Orch")</span><span class="sxs-lookup"><span data-stu-id="48aac-252">![Orchestration](../core/media/bts2010r2-tut1-orch.jpg "BTS2010R2_Tut1_Orch")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48aac-253">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48aac-253">See Also</span></span>  
 [<span data-ttu-id="48aac-254">教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式</span><span class="sxs-lookup"><span data-stu-id="48aac-254">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)