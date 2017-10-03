---
title: "步驟 3a: Salesforce 接收機會通知到 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be9de6e3-6bd9-4275-b2fb-0a756c51aabf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76ab28e8e70c0b8a222f6772a763a93252f2c413
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-receive-salesforce-opportunity-notification-into-biztalk-server"></a><span data-ttu-id="d97b1-102">步驟 3a: Salesforce 接收機會通知到 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d97b1-102">Step 3a: Receive Salesforce Opportunity Notification into BizTalk Server</span></span>
<span data-ttu-id="d97b1-103">在此步驟中，我們開始建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d97b1-103">In this step, we start creating a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d97b1-104">首先，我們應該包含商機通知訊息，我們會用來取得從 Salesforce，然後再啟動 建立協調流程處理訊息的訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="d97b1-104">We should first include the message schema for the opportunities notification message that we’ll get from Salesforce and then start creating an orchestration to process the message.</span></span>  
  
### <a name="to-include-the-salesforce-opportunities-notification-schema"></a><span data-ttu-id="d97b1-105">要包含的 Salesforce 商機通知結構描述</span><span class="sxs-lookup"><span data-stu-id="d97b1-105">To include the Salesforce opportunities notification schema</span></span>  
  
1.  <span data-ttu-id="d97b1-106">登入 Salesforce.com 入口網站。</span><span class="sxs-lookup"><span data-stu-id="d97b1-106">Login to the Salesforce.com portal.</span></span> <span data-ttu-id="d97b1-107">在 Salesforce 入口網站中，按一下右上角的頁面上，在您登入的名稱，然後按一下 **安裝**。</span><span class="sxs-lookup"><span data-stu-id="d97b1-107">On the Salesforce portal, click your login name at the top right corner of the page, and then click **Setup**.</span></span>  
  
2.  <span data-ttu-id="d97b1-108">在左窗格中下,**應用程式安裝**，依序展開**建立**，展開**工作流程 （& s) 核准**，然後按一下**工作流程規則**。</span><span class="sxs-lookup"><span data-stu-id="d97b1-108">In the left pane, under **App Setup**, expand **Create**, expand **Workflow & Approvals**, and then click **Workflow Rules**.</span></span>  
  
3.  <span data-ttu-id="d97b1-109">在**所有工作流程規則**頁面上，按一下**已關閉商機**您稍早建立的工作流程。</span><span class="sxs-lookup"><span data-stu-id="d97b1-109">In the **All Workflow Rules** page, click the **Closed Opportunity** workflow that you created earlier.</span></span>  
  
4.  <span data-ttu-id="d97b1-110">在**已關閉商機**工作流程規則頁面上，按一下  **NewOp1**外寄訊息的工作流程動作。</span><span class="sxs-lookup"><span data-stu-id="d97b1-110">In the **Closed Opportunity** workflow rule page, click **NewOp1** outbound message workflow action.</span></span>  
  
5.  <span data-ttu-id="d97b1-111">在**NewOp1**外寄訊息的工作流程動作頁面上，以滑鼠右鍵按一下連結**按一下 wsdl**，按一下**另存目標**，然後指定您要儲存的位置WSDL 中。</span><span class="sxs-lookup"><span data-stu-id="d97b1-111">In the **NewOp1** outbound message workflow action page, right-click the link **Click for WSDL**, click **Save target as**, and then specify the location where you want to save the WSDL.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d97b1-112">您必須具有.wsdl 副檔名儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="d97b1-112">You must save the file with a .wsdl extension.</span></span>  
  
6.  <span data-ttu-id="d97b1-113">建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d97b1-113">Create a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="d97b1-114">本教學課程，讓我們將專案命名為`BtsSalesforceIntegration`。</span><span class="sxs-lookup"><span data-stu-id="d97b1-114">For this tutorial, let us name the project as `BtsSalesforceIntegration`.</span></span>  
  
7.  <span data-ttu-id="d97b1-115">以滑鼠右鍵按一下[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案在 [方案總管] 中，指向**新增**，然後按一下 **新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="d97b1-115">Right-click the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project in the Solution Explorer, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
8.  <span data-ttu-id="d97b1-116">在**新增產生的項目**對話方塊中，按一下 **取用 WCF 服務**，然後按一下 **新增**啟動**BizTalk WCF 服務取用**精靈。</span><span class="sxs-lookup"><span data-stu-id="d97b1-116">In the **Add Generated Items** dialog box, click **Consume WCF Service**, and then click **Add** to launch the **BizTalk WCF Service Consuming** wizard.</span></span> <span data-ttu-id="d97b1-117">在 歡迎使用 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="d97b1-117">On the welcome page, click **Next**.</span></span>  
  
9. <span data-ttu-id="d97b1-118">在**中繼資料來源**頁面上，選取**中繼資料檔案 （WSDL 和 XSD）**選項，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d97b1-118">On the **Metadata Source** page, select the **Metadata Files (WSDL and XSD)** option, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="d97b1-119">在**中繼資料檔案**頁面上，按一下**新增**，然後瀏覽至您用來儲存從 Salesforce 入口網站下載的 WSDL 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="d97b1-119">On the **Metadata Files** page, click **Add**, and then navigate to the location where you saved the WSDL file downloaded from the Salesforce portal.</span></span> <span data-ttu-id="d97b1-120">選取的 WSDL 檔案，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d97b1-120">Select the WSDL file and then click **Next**.</span></span>  
  
11. <span data-ttu-id="d97b1-121">在下一個頁面中，設定命名空間，做為`NotificationService`，然後按一下 **匯入**。</span><span class="sxs-lookup"><span data-stu-id="d97b1-121">In the next page, set the namespace as `NotificationService` and then click **Import**.</span></span> <span data-ttu-id="d97b1-122">精靈將結構描述檔案和協調流程，以加入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="d97b1-122">The wizard adds the schema files and an orchestration to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="d97b1-123">接收來自 Salesforce 的商機通知的訊息結構描述是**NotificationService_soap_sforce_com_2005_09_outbound.xsd**。</span><span class="sxs-lookup"><span data-stu-id="d97b1-123">The message schema for receiving opportunity notifications from Salesforce is **NotificationService_soap_sforce_com_2005_09_outbound.xsd**.</span></span>  
  
### <a name="to-create-an-orchestration-to-receive-the-notification-message"></a><span data-ttu-id="d97b1-124">若要建立協調流程接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="d97b1-124">To create an orchestration to receive the notification message</span></span>  
  
1.  <span data-ttu-id="d97b1-125">完成之後**BizTalk WCF 服務取用**精靈]、 [協調流程 (**NotificationService.odx**，在此範例中) 新增至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="d97b1-125">After you complete the **BizTalk WCF Service Consuming** wizard, an orchestration (**NotificationService.odx**, in this example) is added to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="d97b1-126">開啟協調流程檔案，並在協調流程檢視中，新增兩個新的訊息變數。</span><span class="sxs-lookup"><span data-stu-id="d97b1-126">Open the orchestration file and in the Orchestration view, add two new message variables.</span></span> <span data-ttu-id="d97b1-127">它們的名稱`NotificationMessage`和`NotificationAck`。</span><span class="sxs-lookup"><span data-stu-id="d97b1-127">Name them `NotificationMessage` and `NotificationAck`.</span></span> <span data-ttu-id="d97b1-128">設定訊息類型的這些訊息變數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d97b1-128">Set the message type for these message variables as follows:</span></span>  
  
    1.  <span data-ttu-id="d97b1-129">設定**NotificationMessage**至*NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notifications*。</span><span class="sxs-lookup"><span data-stu-id="d97b1-129">Set **NotificationMessage** to *NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notifications*.</span></span> <span data-ttu-id="d97b1-130">此訊息變數代表從 Salesforce 收到的商機通知訊息。</span><span class="sxs-lookup"><span data-stu-id="d97b1-130">This message variable represents the opportunity notification message received from Salesforce.</span></span>  
  
    2.  <span data-ttu-id="d97b1-131">設定**NotificationAck**至*NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notificationsResponse*。</span><span class="sxs-lookup"><span data-stu-id="d97b1-131">Set **NotificationAck** to *NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notificationsResponse*.</span></span> <span data-ttu-id="d97b1-132">此訊息變數代表商機通知傳送通知訊息至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="d97b1-132">This message variable represents the opportunity notification acknowledgement message sent back to Salesforce.</span></span>  
  
3.  <span data-ttu-id="d97b1-133">新增 「 接收 」 圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="d97b1-133">Add a receive shape to the orchestration.</span></span> <span data-ttu-id="d97b1-134">在圖形上設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d97b1-134">Set the following properties on the shape:</span></span>  
  
    1.  <span data-ttu-id="d97b1-135">設定**啟動**至**True**。</span><span class="sxs-lookup"><span data-stu-id="d97b1-135">Set **Activate** to **True**.</span></span>  
  
    2.  <span data-ttu-id="d97b1-136">設定**名稱**至*ReceiveNotificationMessage*。</span><span class="sxs-lookup"><span data-stu-id="d97b1-136">Set **Name** to *ReceiveNotificationMessage*.</span></span>  
  
    3.  <span data-ttu-id="d97b1-137">設定**訊息**至*NotificationMessage*。</span><span class="sxs-lookup"><span data-stu-id="d97b1-137">Set **Message** to *NotificationMessage*.</span></span>  
  
4.  <span data-ttu-id="d97b1-138">「 接收 」 圖形之後新增建構訊息 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="d97b1-138">Add a Construct Message shape after the Receive shape.</span></span> <span data-ttu-id="d97b1-139">名稱為 「 訊息 」 圖形`ConstructNotificationResponse`並設定**建構的訊息**屬性`NotificationAck`。</span><span class="sxs-lookup"><span data-stu-id="d97b1-139">Name the message shape as `ConstructNotificationResponse` and set the **Messages Constructed** property to `NotificationAck`.</span></span> <span data-ttu-id="d97b1-140">建構訊息的一部分，我們也會建立對應以產生通知的通知訊息傳送至 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="d97b1-140">As part of the construct message, we’ll also create a map to generate a notification acknowledgement message to be sent back to Salesforce.</span></span>  
  
    1.  <span data-ttu-id="d97b1-141">「 建構訊息 」 圖形中新增轉換圖形。</span><span class="sxs-lookup"><span data-stu-id="d97b1-141">Within the Construct Message shape, add a Transform shape.</span></span> <span data-ttu-id="d97b1-142">按兩下 「 轉換 」 圖形，並在 [轉換組態] 對話方塊選取**新對應**選項。</span><span class="sxs-lookup"><span data-stu-id="d97b1-142">Double-click the Transform shape and in the Transform Configuration dialog box, select the **New Map** option.</span></span>  
  
    2.  <span data-ttu-id="d97b1-143">指定對應名稱為`BtsSalesforceIntegration.MapNotificationResponse`。</span><span class="sxs-lookup"><span data-stu-id="d97b1-143">Specify the map name as `BtsSalesforceIntegration.MapNotificationResponse`.</span></span>  
  
    3.  <span data-ttu-id="d97b1-144">設定為來源**NotificationMessage**和做為目的地**NotificationAck**。</span><span class="sxs-lookup"><span data-stu-id="d97b1-144">Set Source as **NotificationMessage** and Destination as **NotificationAck**.</span></span>  
  
    4.  <span data-ttu-id="d97b1-145">請確定核取方塊**當我按 [確定] 時，啟動 BizTalk 對應工具**已選取。</span><span class="sxs-lookup"><span data-stu-id="d97b1-145">Make sure the check box **When I click OK, launch the BizTalk Mapper** is selected.</span></span>  
  
    5.  <span data-ttu-id="d97b1-146">在**MapNotificationResponse.btm**，我們將建立的通知回應送回給 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="d97b1-146">In **MapNotificationResponse.btm**, we’ll create a notification response to be sent back to Salesforce.</span></span> <span data-ttu-id="d97b1-147">每次 Salesforce 傳送通知，它預期傳回收到通知。</span><span class="sxs-lookup"><span data-stu-id="d97b1-147">Every time Salesforce sends a notification, it expects an acknowledgement in return.</span></span> <span data-ttu-id="d97b1-148">通知回應訊息結構描述會顯示**Ack**回應中的項目是布林類型。</span><span class="sxs-lookup"><span data-stu-id="d97b1-148">The schema of the notification response message shows that the **Ack** element in the response is of type Boolean.</span></span> <span data-ttu-id="d97b1-149">因此，在對應中，您必須先卸除**值對應**運算質，並設定其兩個輸入值 （條件和結果） 至`true`。</span><span class="sxs-lookup"><span data-stu-id="d97b1-149">So, in the map, you must drop a **Value Mapping** functoid and set its two input values (Condition and Result) to `true`.</span></span> <span data-ttu-id="d97b1-150">按一下**確定**儲存運算質。</span><span class="sxs-lookup"><span data-stu-id="d97b1-150">Click **OK** to save the functoid.</span></span>  
  
    6.  <span data-ttu-id="d97b1-151">連接**值對應**運算質**Ack**目的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="d97b1-151">Connect the **Value Mapping** functoid to the **Ack** element in the destination schema.</span></span>  
  
5.  <span data-ttu-id="d97b1-152">在協調流程中，在建構訊息 」 圖形之後加入將用來傳送通知回至 Salesforce 「 傳送 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="d97b1-152">In the orchestration, after the Construct Message shape, add a Send shape that will be used to send the acknowledgement back to Salesforce.</span></span>  
  
    -   <span data-ttu-id="d97b1-153">設定**名稱**至*SendNotificationAck*。</span><span class="sxs-lookup"><span data-stu-id="d97b1-153">Set **Name** to *SendNotificationAck*.</span></span>  
  
    -   <span data-ttu-id="d97b1-154">設定**訊息**至*NotificationAck*。</span><span class="sxs-lookup"><span data-stu-id="d97b1-154">Set **Message** to *NotificationAck*.</span></span>  
  
6.  <span data-ttu-id="d97b1-155">在協調流程中，加入的連接埠以接收 Salesforce 通知訊息，並在回應中傳送通知。</span><span class="sxs-lookup"><span data-stu-id="d97b1-155">In the orchestration, add a port to receive Salesforce notification message and send the acknowledgement in response.</span></span> <span data-ttu-id="d97b1-156">在連接埠組態精靈中，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="d97b1-156">In the Port Configuration wizard, select the following options:</span></span>  
  
    -   <span data-ttu-id="d97b1-157">將連接埠名稱指定為`SalesforceNotificationPort`。</span><span class="sxs-lookup"><span data-stu-id="d97b1-157">Specify the port name as `SalesforceNotificationPort`.</span></span>  
  
    -   <span data-ttu-id="d97b1-158">選取 建立新的連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="d97b1-158">Select the option to create a new port type.</span></span>  
  
    -   <span data-ttu-id="d97b1-159">設定**通訊模式**至*要求-回應*。</span><span class="sxs-lookup"><span data-stu-id="d97b1-159">Set **Communication Pattern** to *Request-Response*.</span></span>  
  
    -   <span data-ttu-id="d97b1-160">設定**連接埠通訊方向**至*我要接收要求並傳送回應*並設定**連接埠繫結**至*指定更新*.</span><span class="sxs-lookup"><span data-stu-id="d97b1-160">Set **Port direction of communication** to *I’ll be receiving a request and sending a response* and set **Port binding** to *Specify later*.</span></span>  
  
     <span data-ttu-id="d97b1-161">連接**要求**「 接收 」 圖形的連接埠的作業 (*ReceiveNotificationMessage*) 和**回應**作業的 「 傳送 」 圖形的連接埠 (*SendNotificationAck*)。</span><span class="sxs-lookup"><span data-stu-id="d97b1-161">Connect the **Request** operation of port to the Receive shape (*ReceiveNotificationMessage*) and the **Response** operation of the port to the Send shape (*SendNotificationAck*).</span></span> <span data-ttu-id="d97b1-162">下列螢幕擷取畫面顯示協調流程會接收來自 Salesforce 的商機通知，並傳送通知回覆的一部分：</span><span class="sxs-lookup"><span data-stu-id="d97b1-162">The following screenshot depicts the part of the orchestration that receives an opportunity notification from Salesforce and sends an acknowledgement back:</span></span>  
  
     <span data-ttu-id="d97b1-163">![接收機會通知並傳送回應](../core/media/bts-sf-recvnotificationorch.jpg "BTS_SF_RecvNotificationOrch")</span><span class="sxs-lookup"><span data-stu-id="d97b1-163">![Receive opportunity notification and send response](../core/media/bts-sf-recvnotificationorch.jpg "BTS_SF_RecvNotificationOrch")</span></span>  
  
 <span data-ttu-id="d97b1-164">現在，我們已設定的解決方案，讓從 Salesforce 收到商機通知，並將認可傳回到。</span><span class="sxs-lookup"><span data-stu-id="d97b1-164">By now, we have set up the solution where an opportunity notification is received from Salesforce and an acknowledgement is sent back.</span></span> <span data-ttu-id="d97b1-165">在後續主題中，我們會建置此解決方案，以開始處理商機通知，以取得更多詳細銷售商機可用的類型。</span><span class="sxs-lookup"><span data-stu-id="d97b1-165">In the subsequent topics, we’ll build on this solution to start processing the opportunity notification to get more details about the kind of sales opportunity available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d97b1-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d97b1-166">See Also</span></span>  
 [<span data-ttu-id="d97b1-167">步驟 3： 建立 Visual Studio 中的 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="d97b1-167">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)