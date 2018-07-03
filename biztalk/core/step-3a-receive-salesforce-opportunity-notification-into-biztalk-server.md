---
title: 步驟 3a： 到 BizTalk Server 中的 Salesforce Opportunity Notification 接收 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be9de6e3-6bd9-4275-b2fb-0a756c51aabf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a51340d8812a8b42871d63c8fc52eeee6e05312
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999439"
---
# <a name="step-3a-receive-salesforce-opportunity-notification-into-biztalk-server"></a><span data-ttu-id="80cbc-102">步驟 3a： 到 BizTalk Server 中的 Salesforce Opportunity Notification 接收</span><span class="sxs-lookup"><span data-stu-id="80cbc-102">Step 3a: Receive Salesforce Opportunity Notification into BizTalk Server</span></span>
<span data-ttu-id="80cbc-103">在此步驟中，我們開始建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="80cbc-103">In this step, we start creating a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="80cbc-104">首先，我們應該包含商機通知訊息，我們將用來從 Salesforce 取得，並再啟動 建立協調流程處理訊息的訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="80cbc-104">We should first include the message schema for the opportunities notification message that we’ll get from Salesforce and then start creating an orchestration to process the message.</span></span>  
  
### <a name="to-include-the-salesforce-opportunities-notification-schema"></a><span data-ttu-id="80cbc-105">要包含的 Salesforce 商機通知結構描述</span><span class="sxs-lookup"><span data-stu-id="80cbc-105">To include the Salesforce opportunities notification schema</span></span>  
  
1. <span data-ttu-id="80cbc-106">登入 Salesforce.com 入口網站。</span><span class="sxs-lookup"><span data-stu-id="80cbc-106">Login to the Salesforce.com portal.</span></span> <span data-ttu-id="80cbc-107">在上 Salesforce 入口網站中，按一下右上角的頁面上，在您登入名稱，然後按一下**安裝程式**。</span><span class="sxs-lookup"><span data-stu-id="80cbc-107">On the Salesforce portal, click your login name at the top right corner of the page, and then click **Setup**.</span></span>  
  
2. <span data-ttu-id="80cbc-108">在左窗格中，在**應用程式安裝程式**，展開**建立**，展開**工作流程與核准**，然後按一下**工作流程規則**。</span><span class="sxs-lookup"><span data-stu-id="80cbc-108">In the left pane, under **App Setup**, expand **Create**, expand **Workflow & Approvals**, and then click **Workflow Rules**.</span></span>  
  
3. <span data-ttu-id="80cbc-109">在 **所有的工作流程規則**頁面上，按一下**已關閉商機**您稍早建立的工作流程。</span><span class="sxs-lookup"><span data-stu-id="80cbc-109">In the **All Workflow Rules** page, click the **Closed Opportunity** workflow that you created earlier.</span></span>  
  
4. <span data-ttu-id="80cbc-110">在 **已關閉商機**工作流程規則頁面上，按一下**NewOp1**外寄訊息的工作流程動作。</span><span class="sxs-lookup"><span data-stu-id="80cbc-110">In the **Closed Opportunity** workflow rule page, click **NewOp1** outbound message workflow action.</span></span>  
  
5. <span data-ttu-id="80cbc-111">中**NewOp1**外寄訊息的工作流程動作頁面上，以滑鼠右鍵按一下該連結**按一下 wsdl**，按一下**另存目標**，然後指定您要儲存的位置在 WSDL 中。</span><span class="sxs-lookup"><span data-stu-id="80cbc-111">In the **NewOp1** outbound message workflow action page, right-click the link **Click for WSDL**, click **Save target as**, and then specify the location where you want to save the WSDL.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="80cbc-112">您必須以副檔名.wsdl 儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="80cbc-112">You must save the file with a .wsdl extension.</span></span>  
  
6. <span data-ttu-id="80cbc-113">建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="80cbc-113">Create a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="80cbc-114">本教學課程中，我們將專案命名為`BtsSalesforceIntegration`。</span><span class="sxs-lookup"><span data-stu-id="80cbc-114">For this tutorial, let us name the project as `BtsSalesforceIntegration`.</span></span>  
  
7. <span data-ttu-id="80cbc-115">以滑鼠右鍵按一下[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案總管 中專案，指向**新增**，然後按一下**加入產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="80cbc-115">Right-click the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project in the Solution Explorer, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
8. <span data-ttu-id="80cbc-116">在**加入產生的項目** 對話方塊中，按一下**取用 WCF 服務**，然後按一下**新增**啟動**BizTalk WCF 服務取用**精靈。</span><span class="sxs-lookup"><span data-stu-id="80cbc-116">In the **Add Generated Items** dialog box, click **Consume WCF Service**, and then click **Add** to launch the **BizTalk WCF Service Consuming** wizard.</span></span> <span data-ttu-id="80cbc-117">在 歡迎使用 頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="80cbc-117">On the welcome page, click **Next**.</span></span>  
  
9. <span data-ttu-id="80cbc-118">在 [**中繼資料來源**頁面上，選取**中繼資料檔案 （WSDL 和 XSD）** 選項，然後再按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="80cbc-118">On the **Metadata Source** page, select the **Metadata Files (WSDL and XSD)** option, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="80cbc-119">在 **中繼資料檔案**頁面上，按一下**新增**，然後瀏覽至您用來儲存從 Salesforce 入口網站下載的 WSDL 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="80cbc-119">On the **Metadata Files** page, click **Add**, and then navigate to the location where you saved the WSDL file downloaded from the Salesforce portal.</span></span> <span data-ttu-id="80cbc-120">選取 WSDL 檔案，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="80cbc-120">Select the WSDL file and then click **Next**.</span></span>  
  
11. <span data-ttu-id="80cbc-121">在下一步] 頁面中，設定為命名空間`NotificationService`，然後按一下 [**匯入**。</span><span class="sxs-lookup"><span data-stu-id="80cbc-121">In the next page, set the namespace as `NotificationService` and then click **Import**.</span></span> <span data-ttu-id="80cbc-122">精靈將結構描述檔案和協調流程，以加入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="80cbc-122">The wizard adds the schema files and an orchestration to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="80cbc-123">會接收來自 Salesforce 的商機通知的訊息結構描述**NotificationService_soap_sforce_com_2005_09_outbound.xsd**。</span><span class="sxs-lookup"><span data-stu-id="80cbc-123">The message schema for receiving opportunity notifications from Salesforce is **NotificationService_soap_sforce_com_2005_09_outbound.xsd**.</span></span>  
  
### <a name="to-create-an-orchestration-to-receive-the-notification-message"></a><span data-ttu-id="80cbc-124">若要建立協調流程以接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="80cbc-124">To create an orchestration to receive the notification message</span></span>  
  
1. <span data-ttu-id="80cbc-125">完成後**BizTalk WCF 服務取用**精靈]、 [協調流程 (**NotificationService.odx**，在此範例中) 新增至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="80cbc-125">After you complete the **BizTalk WCF Service Consuming** wizard, an orchestration (**NotificationService.odx**, in this example) is added to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
2. <span data-ttu-id="80cbc-126">開啟協調流程檔案，並在協調流程檢視中，新增兩個新的訊息變數。</span><span class="sxs-lookup"><span data-stu-id="80cbc-126">Open the orchestration file and in the Orchestration view, add two new message variables.</span></span> <span data-ttu-id="80cbc-127">它們的名稱`NotificationMessage`和`NotificationAck`。</span><span class="sxs-lookup"><span data-stu-id="80cbc-127">Name them `NotificationMessage` and `NotificationAck`.</span></span> <span data-ttu-id="80cbc-128">設定訊息類型的這些訊息變數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="80cbc-128">Set the message type for these message variables as follows:</span></span>  
  
   1.  <span data-ttu-id="80cbc-129">設定**NotificationMessage**要*NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notifications*。</span><span class="sxs-lookup"><span data-stu-id="80cbc-129">Set **NotificationMessage** to *NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notifications*.</span></span> <span data-ttu-id="80cbc-130">此訊息變數代表從 Salesforce 收到的商機通知訊息。</span><span class="sxs-lookup"><span data-stu-id="80cbc-130">This message variable represents the opportunity notification message received from Salesforce.</span></span>  
  
   2.  <span data-ttu-id="80cbc-131">設定**NotificationAck**要*NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notificationsResponse*。</span><span class="sxs-lookup"><span data-stu-id="80cbc-131">Set **NotificationAck** to *NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notificationsResponse*.</span></span> <span data-ttu-id="80cbc-132">此訊息變數代表傳回給 Salesforce 商機通知的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="80cbc-132">This message variable represents the opportunity notification acknowledgement message sent back to Salesforce.</span></span>  
  
3. <span data-ttu-id="80cbc-133">新增 「 接收 」 圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="80cbc-133">Add a receive shape to the orchestration.</span></span> <span data-ttu-id="80cbc-134">在圖形上設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="80cbc-134">Set the following properties on the shape:</span></span>  
  
   1.  <span data-ttu-id="80cbc-135">設定**啟用**要 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="80cbc-135">Set **Activate** to **True**.</span></span>  
  
   2.  <span data-ttu-id="80cbc-136">設定**名稱**要*ReceiveNotificationMessage*。</span><span class="sxs-lookup"><span data-stu-id="80cbc-136">Set **Name** to *ReceiveNotificationMessage*.</span></span>  
  
   3.  <span data-ttu-id="80cbc-137">設定**訊息**要*NotificationMessage*。</span><span class="sxs-lookup"><span data-stu-id="80cbc-137">Set **Message** to *NotificationMessage*.</span></span>  
  
4. <span data-ttu-id="80cbc-138">新增 「 接收 」 圖形之後的 「 建構訊息 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="80cbc-138">Add a Construct Message shape after the Receive shape.</span></span> <span data-ttu-id="80cbc-139">名稱為 「 訊息 」 圖形`ConstructNotificationResponse`並設定**建構的訊息**屬性設`NotificationAck`。</span><span class="sxs-lookup"><span data-stu-id="80cbc-139">Name the message shape as `ConstructNotificationResponse` and set the **Messages Constructed** property to `NotificationAck`.</span></span> <span data-ttu-id="80cbc-140">建構訊息的一部分，我們也會建立對應，以產生通知的通知訊息，以傳回至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="80cbc-140">As part of the construct message, we’ll also create a map to generate a notification acknowledgement message to be sent back to Salesforce.</span></span>  
  
   1.  <span data-ttu-id="80cbc-141">在 [建構訊息] 圖形中，新增 「 轉換 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="80cbc-141">Within the Construct Message shape, add a Transform shape.</span></span> <span data-ttu-id="80cbc-142">按兩下 [轉換] 圖形，然後在 [轉換組態] 對話方塊中，選取**新的對應**選項。</span><span class="sxs-lookup"><span data-stu-id="80cbc-142">Double-click the Transform shape and in the Transform Configuration dialog box, select the **New Map** option.</span></span>  
  
   2.  <span data-ttu-id="80cbc-143">指定對應名稱為`BtsSalesforceIntegration.MapNotificationResponse`。</span><span class="sxs-lookup"><span data-stu-id="80cbc-143">Specify the map name as `BtsSalesforceIntegration.MapNotificationResponse`.</span></span>  
  
   3.  <span data-ttu-id="80cbc-144">設定為來源**NotificationMessage**和 做為目的地**NotificationAck**。</span><span class="sxs-lookup"><span data-stu-id="80cbc-144">Set Source as **NotificationMessage** and Destination as **NotificationAck**.</span></span>  
  
   4.  <span data-ttu-id="80cbc-145">請確定核取方塊**當我按一下 [確定] 時，啟動 BizTalk 對應工具**已選取。</span><span class="sxs-lookup"><span data-stu-id="80cbc-145">Make sure the check box **When I click OK, launch the BizTalk Mapper** is selected.</span></span>  
  
   5.  <span data-ttu-id="80cbc-146">在  **MapNotificationResponse.btm**，我們將建立的通知回應傳回至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="80cbc-146">In **MapNotificationResponse.btm**, we’ll create a notification response to be sent back to Salesforce.</span></span> <span data-ttu-id="80cbc-147">每次 Salesforce 中，會傳送通知，它預期傳回收到通知。</span><span class="sxs-lookup"><span data-stu-id="80cbc-147">Every time Salesforce sends a notification, it expects an acknowledgement in return.</span></span> <span data-ttu-id="80cbc-148">通知回應訊息結構描述會顯示**Ack**在回應中的項目為布林值類型。</span><span class="sxs-lookup"><span data-stu-id="80cbc-148">The schema of the notification response message shows that the **Ack** element in the response is of type Boolean.</span></span> <span data-ttu-id="80cbc-149">因此，在對應中，您必須先卸除**值對應**運算質，並設定其兩個輸入值 （「 條件 」 和 「 結果 」） 到`true`。</span><span class="sxs-lookup"><span data-stu-id="80cbc-149">So, in the map, you must drop a **Value Mapping** functoid and set its two input values (Condition and Result) to `true`.</span></span> <span data-ttu-id="80cbc-150">按一下 **確定**儲存運算質。</span><span class="sxs-lookup"><span data-stu-id="80cbc-150">Click **OK** to save the functoid.</span></span>  
  
   6.  <span data-ttu-id="80cbc-151">連接**值對應**運算質**Ack**目的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="80cbc-151">Connect the **Value Mapping** functoid to the **Ack** element in the destination schema.</span></span>  
  
5. <span data-ttu-id="80cbc-152">在協調流程中之後 [建構訊息] 圖形中，, 新增將用來傳送通知回至 Salesforce 「 傳送 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="80cbc-152">In the orchestration, after the Construct Message shape, add a Send shape that will be used to send the acknowledgement back to Salesforce.</span></span>  
  
   -   <span data-ttu-id="80cbc-153">設定**名稱**要*SendNotificationAck*。</span><span class="sxs-lookup"><span data-stu-id="80cbc-153">Set **Name** to *SendNotificationAck*.</span></span>  
  
   -   <span data-ttu-id="80cbc-154">設定**訊息**要*NotificationAck*。</span><span class="sxs-lookup"><span data-stu-id="80cbc-154">Set **Message** to *NotificationAck*.</span></span>  
  
6. <span data-ttu-id="80cbc-155">在協調流程中，新增連接埠以接收 Salesforce 通知訊息，並在回應中傳送通知。</span><span class="sxs-lookup"><span data-stu-id="80cbc-155">In the orchestration, add a port to receive Salesforce notification message and send the acknowledgement in response.</span></span> <span data-ttu-id="80cbc-156">在 [連接埠組態精靈] 中，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="80cbc-156">In the Port Configuration wizard, select the following options:</span></span>  
  
   - <span data-ttu-id="80cbc-157">將連接埠名稱指定為`SalesforceNotificationPort`。</span><span class="sxs-lookup"><span data-stu-id="80cbc-157">Specify the port name as `SalesforceNotificationPort`.</span></span>  
  
   - <span data-ttu-id="80cbc-158">選取 [建立新的連接埠類型] 選項。</span><span class="sxs-lookup"><span data-stu-id="80cbc-158">Select the option to create a new port type.</span></span>  
  
   - <span data-ttu-id="80cbc-159">設定**通訊模式**要*要求-回應*。</span><span class="sxs-lookup"><span data-stu-id="80cbc-159">Set **Communication Pattern** to *Request-Response*.</span></span>  
  
   - <span data-ttu-id="80cbc-160">設定**連接埠通訊方向**要*我就可以接收要求並傳送回應*並設定**連接埠繫結**至*指定更新*.</span><span class="sxs-lookup"><span data-stu-id="80cbc-160">Set **Port direction of communication** to *I’ll be receiving a request and sending a response* and set **Port binding** to *Specify later*.</span></span>  
  
     <span data-ttu-id="80cbc-161">連接**要求**作業的 「 接收 」 圖形的連接埠 (*ReceiveNotificationMessage*) 和**回應**「 傳送 」 圖形的連接埠的作業 (*SendNotificationAck*)。</span><span class="sxs-lookup"><span data-stu-id="80cbc-161">Connect the **Request** operation of port to the Receive shape (*ReceiveNotificationMessage*) and the **Response** operation of the port to the Send shape (*SendNotificationAck*).</span></span> <span data-ttu-id="80cbc-162">下列螢幕擷取畫面說明接收來自 Salesforce 的商機通知和傳送通知回覆的協調流程的一部分：</span><span class="sxs-lookup"><span data-stu-id="80cbc-162">The following screenshot depicts the part of the orchestration that receives an opportunity notification from Salesforce and sends an acknowledgement back:</span></span>  
  
     <span data-ttu-id="80cbc-163">![接收機會通知並傳送回應](../core/media/bts-sf-recvnotificationorch.jpg "BTS_SF_RecvNotificationOrch")</span><span class="sxs-lookup"><span data-stu-id="80cbc-163">![Receive opportunity notification and send response](../core/media/bts-sf-recvnotificationorch.jpg "BTS_SF_RecvNotificationOrch")</span></span>  
  
   <span data-ttu-id="80cbc-164">到目前為止，我們已設定的解決方案，其中從 Salesforce 收到商機通知，且會將認可傳回到。</span><span class="sxs-lookup"><span data-stu-id="80cbc-164">By now, we have set up the solution where an opportunity notification is received from Salesforce and an acknowledgement is sent back.</span></span> <span data-ttu-id="80cbc-165">在後續主題中，我們會建置此解決方案，以開始處理機會通知，以取得更多詳細的銷售機會種類。</span><span class="sxs-lookup"><span data-stu-id="80cbc-165">In the subsequent topics, we’ll build on this solution to start processing the opportunity notification to get more details about the kind of sales opportunity available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80cbc-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80cbc-166">See Also</span></span>  
 [<span data-ttu-id="80cbc-167">步驟 3：在 Visual Studio 中建立 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="80cbc-167">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)