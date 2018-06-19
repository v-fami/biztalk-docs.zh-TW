---
title: MQSCorrelationSetOrchestrationWithSolicitResponse （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, MQSeries adapters
- orchestrations, examples
- examples, orchestrations
- examples, messages
- messages, examples
- MQSeries adapters, examples
ms.assetid: 5127d743-bb79-4e97-a2f3-446892e1bfa0
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79d92ca7a65262d18a08cab700710284accfbf78
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975804"
---
# <a name="mqscorrelationsetorchestrationwithsolicitresponse-biztalk-server-sample"></a><span data-ttu-id="0641f-102">MQSCorrelationSetOrchestrationWithSolicitResponse (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="0641f-102">MQSCorrelationSetOrchestrationWithSolicitResponse (BizTalk Server Sample)</span></span>
<span data-ttu-id="0641f-103">MQSCorrelationSetOrchestrationWithSolicitResponse 範例將示範如何使用 MQSeries Server (而非 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]) 產生的相互關聯識別項。</span><span class="sxs-lookup"><span data-stu-id="0641f-103">The MQSCorrelationSetOrchestrationWithSolicitResponse sample demonstrates how to use a correlation identifier produced by the MQSeries Server instead of by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="0641f-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="0641f-104">What This Sample Does</span></span>  
 <span data-ttu-id="0641f-105">協調流程傳送的值是空的訊息**MQMD_MsgID**訊息標頭中的屬性。</span><span class="sxs-lookup"><span data-stu-id="0641f-105">The orchestration sends a message with an empty value for the **MQMD_MsgID** property in the message header.</span></span> <span data-ttu-id="0641f-106">MQSeries 產生 MessageID 和 CorrelationID，並傳回一則訊息，並將值指派至**MQMD_MsgID**和**MQMD_CorrelId**一部分的回應請求-回應傳送配接器的連接埠.</span><span class="sxs-lookup"><span data-stu-id="0641f-106">MQSeries generates the MessageID and CorrelationID and returns a message with a value assigned to **MQMD_MsgID** and **MQMD_CorrelId** as part of the response in the solicit-response send port of the adapter.</span></span> <span data-ttu-id="0641f-107">協調流程使用產生的相互關聯識別項來初始化相互關聯集的相互關聯集在後續接收位置和藉由檢查**MQMD_CorrelId**訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="0641f-107">The orchestration uses the generated correlation identifier to initialize the correlation set and follows the correlation set in a subsequent receive location by checking the **MQMD_CorrelId** property of the message.</span></span> <span data-ttu-id="0641f-108">配接器也會將指派的相互關聯識別項**BizTalk_CorrelationID**，您也可以使用協調流程中。</span><span class="sxs-lookup"><span data-stu-id="0641f-108">The adapter also assigns the correlation identifier to **BizTalk_CorrelationID**, which you could also use in an orchestration.</span></span> <span data-ttu-id="0641f-109">如需使用相互關聯識別項使用配接器的詳細資訊，請參閱[相互關聯訊息使用要求-回覆](../core/correlating-messages-using-request-reply.md)。</span><span class="sxs-lookup"><span data-stu-id="0641f-109">For more information about using correlation identifiers with the adapter, see [Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0641f-110">如果 MQSeries Server 傳送的訊息比相互關聯識別項先抵達，使用這種方式的協調流程可能會發生問題。</span><span class="sxs-lookup"><span data-stu-id="0641f-110">Orchestrations using this technique may experience problems if the message from the MQSeries Server arrives before the correlation identifier.</span></span> <span data-ttu-id="0641f-111">請確定您在設計協調流程時，給予 MQSeries Server 足夠的時間傳回相互關聯識別項。</span><span class="sxs-lookup"><span data-stu-id="0641f-111">Make sure that you design your orchestrations to allow enough time for the MQSeries Server to return the correlation identifier.</span></span> <span data-ttu-id="0641f-112">本範例並未將這種可能的競爭情形列入考量。</span><span class="sxs-lookup"><span data-stu-id="0641f-112">This example does not consider this possible race condition.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="0641f-113">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="0641f-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="0641f-114">*\<範例路徑\>* \AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="0641f-114">*\<Samples Path\>* \AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse</span></span>  
  
 <span data-ttu-id="0641f-115">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="0641f-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="0641f-116">**檔案**</span><span class="sxs-lookup"><span data-stu-id="0641f-116">**File**</span></span>|<span data-ttu-id="0641f-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="0641f-117">**Description**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="0641f-118">**MQSCorrelationSolicitResponse.btproj，**</span><span class="sxs-lookup"><span data-stu-id="0641f-118">**MQSCorrelationSolicitResponse.btproj,**</span></span><br /><br /> <span data-ttu-id="0641f-119">**[Mqscorrelationsolicitresponse.sln]**</span><span class="sxs-lookup"><span data-stu-id="0641f-119">**MQSCorrelationSolicitResponse.sln**</span></span>|<span data-ttu-id="0641f-120">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="0641f-120">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="0641f-121">**[Mqscorrelationsolicitresponse.odx]**</span><span class="sxs-lookup"><span data-stu-id="0641f-121">**MQSCorrelationSolicitResponse.odx**</span></span>|<span data-ttu-id="0641f-122">應用程式的 BizTalk 協調流程檔案。</span><span class="sxs-lookup"><span data-stu-id="0641f-122">The BizTalk orchestration file for the application.</span></span>|  
|<span data-ttu-id="0641f-123">**MQSCorrelationSolicitResponse.snk**</span><span class="sxs-lookup"><span data-stu-id="0641f-123">**MQSCorrelationSolicitResponse.snk**</span></span>|<span data-ttu-id="0641f-124">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="0641f-124">The strong naming key file.</span></span>|  
|<span data-ttu-id="0641f-125">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="0641f-125">Setup.bat</span></span>|<span data-ttu-id="0641f-126">建置並初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="0641f-126">Builds and initializes this sample.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="0641f-127">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="0641f-127">How to Use This Sample</span></span>  
 <span data-ttu-id="0641f-128">若要建立此應用程式，您必須完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0641f-128">To create the application, you must complete the following steps:</span></span>  
  
-   <span data-ttu-id="0641f-129">建立兩個 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="0641f-129">Create two MQSeries queues.</span></span>  
  
-   <span data-ttu-id="0641f-130">設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0641f-130">Set up a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location and send port.</span></span>  
  
-   <span data-ttu-id="0641f-131">啟用接收位置。</span><span class="sxs-lookup"><span data-stu-id="0641f-131">Enable the receive location.</span></span>  
  
-   <span data-ttu-id="0641f-132">啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0641f-132">Start the send port.</span></span>  
  
-   <span data-ttu-id="0641f-133">建立適當的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0641f-133">Create the appropriate folders.</span></span>  
  
-   <span data-ttu-id="0641f-134">修改協調流程。</span><span class="sxs-lookup"><span data-stu-id="0641f-134">Modify the orchestration.</span></span>  
  
-   <span data-ttu-id="0641f-135">部署、繫結和啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="0641f-135">Deploy, bind and start the orchestration.</span></span>  
  
 <span data-ttu-id="0641f-136">如果您有 MQSeries Server for Windows 安裝的必要權限，則可以透過配接器對話方塊建立 MQSeries 佇列並略過下一個程序。</span><span class="sxs-lookup"><span data-stu-id="0641f-136">If you have the required permissions to the MQSeries Server for Windows installation, you can create the MQSeries queue through the adapter dialog boxes, and can skip the next procedure.</span></span> <span data-ttu-id="0641f-137">如果您沒有這類存取權限，可以使用 IBM WebSphere MQ Explorer 來建立佇列。</span><span class="sxs-lookup"><span data-stu-id="0641f-137">If you do not have such access, you can create the queue using the IBM WebSphere MQ Explorer.</span></span> <span data-ttu-id="0641f-138">若要透過 WebSphere MQ Explorer 建立佇列，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0641f-138">To create the queues through the WebSphere MQ Explorer, complete the following steps.</span></span>  
  
## <a name="creating-the-mqseries-queues-through-the-websphere-mq-explorer"></a><span data-ttu-id="0641f-139">透過 WebSphere MQ Explorer 建立 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="0641f-139">Creating the MQSeries Queues Through the WebSphere MQ Explorer</span></span>  
  
#### <a name="to-create-the-mqseries-queues-through-the-websphere-mq-explorer"></a><span data-ttu-id="0641f-140">若要透過 WebSphere MQ Explorer 建立 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="0641f-140">To create the MQSeries queues through the WebSphere MQ Explorer</span></span>  
  
1.  <span data-ttu-id="0641f-141">按一下**啟動**，指向 **所有程式**，指向  **IBM WebSphere MQ**，然後按一下  **WebSphere MQ Explorer**。</span><span class="sxs-lookup"><span data-stu-id="0641f-141">Click **Start**, point to **All Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2.  <span data-ttu-id="0641f-142">按兩下**佇列管理員**，然後按兩下預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="0641f-142">Double-click **Queue Managers**, and then double-click the default queue manager.</span></span> <span data-ttu-id="0641f-143">預設佇列管理員通常會命名為**Qm_<***< machine_name >* 其中*machine_name*是您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="0641f-143">The default queue manager is typically named **QM_***<machine_name>* where *machine_name* is the name of your computer.</span></span>  
  
3.  <span data-ttu-id="0641f-144">以滑鼠右鍵按一下**佇列**，指向 **新增**，然後按一下 **本機佇列**。</span><span class="sxs-lookup"><span data-stu-id="0641f-144">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
4.  <span data-ttu-id="0641f-145">在**建立本機佇列**對話方塊中，於**佇列名稱**，輸入"REPLYTOQ"，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="0641f-145">In **Create Local Queue** dialog box, in **Queue Name**, type "REPLYTOQ", and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="0641f-146">以滑鼠右鍵按一下**佇列**，按一下 **新增**，然後按一下 **本機佇列**。</span><span class="sxs-lookup"><span data-stu-id="0641f-146">Right-click **Queues**, click **New**, and then click **Local Queue**.</span></span>  
  
6.  <span data-ttu-id="0641f-147">在**建立本機佇列**對話方塊中，於**佇列名稱**，輸入"SOLICITRESPONSEQ"，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="0641f-147">In the **Create Local Queue** dialog box, in **Queue Name**, type "SOLICITRESPONSEQ", and then click **OK**.</span></span>  
  
## <a name="creating-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="0641f-148">建立接收位置與 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="0641f-148">Creating the Receive Location and the MQSeries Queue</span></span>  
 <span data-ttu-id="0641f-149">此程序會建立傳送埠和接收位置，以傳送訊息至 MQSeries 以及接收來自 MQSeries 的相互關聯訊息。</span><span class="sxs-lookup"><span data-stu-id="0641f-149">This procedure creates the send port and receive location to send the message to and receive the correlation message from MQSeries.</span></span> <span data-ttu-id="0641f-150">如果您還沒有建立 MQSeries 佇列，則在建立接收位置時，也會建立 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="0641f-150">The MQSeries queue will also be created when you create the receive location if not already created.</span></span>  
  
#### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="0641f-151">建立接收位置與 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="0641f-151">To create the receive location and the MQSeries queue</span></span>  
  
1.  <span data-ttu-id="0641f-152">開啟 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0641f-152">Open the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="0641f-153">展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開所需的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0641f-153">Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the required application.</span></span>  
  
3.  <span data-ttu-id="0641f-154">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="0641f-154">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="0641f-155">在**單向接收埠屬性**對話方塊中，於**名稱**方塊中輸入"MQReply"，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="0641f-155">In the **One-way Receive Port Properties** dialog box, in the **Name** box, type "MQReply", and click **OK**.</span></span>  
  
5.  <span data-ttu-id="0641f-156">在左窗格中，按一下 **接收位置**索引標籤，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="0641f-156">In the left pane, click **Receive Locations** tab, and then click **New**.</span></span>  
  
6.  <span data-ttu-id="0641f-157">在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入"MQReply"。</span><span class="sxs-lookup"><span data-stu-id="0641f-157">In the **Receive Location Properties** dialog box, in the **Name** box, type "MQReply”.</span></span>  
  
7.  <span data-ttu-id="0641f-158">在**傳輸類型**方塊中，選取**MQSeries**。</span><span class="sxs-lookup"><span data-stu-id="0641f-158">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
8.  <span data-ttu-id="0641f-159">在**接收處理常式**方塊中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="0641f-159">In the **Receive Handler** box, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="0641f-160">在**接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。</span><span class="sxs-lookup"><span data-stu-id="0641f-160">In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
10. <span data-ttu-id="0641f-161">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0641f-161">Click **Configure**.</span></span>  
  
11. <span data-ttu-id="0641f-162">在**MQSeries 傳輸屬性**對話方塊中，於**輪詢間隔**方塊中，輸入"10"。</span><span class="sxs-lookup"><span data-stu-id="0641f-162">In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type "10".</span></span>  
  
12. <span data-ttu-id="0641f-163">在**佇列定義**方塊中，按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0641f-163">In the **Queue Definition** box, click the ellipsis (…) button.</span></span>  
  
13. <span data-ttu-id="0641f-164">在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="0641f-164">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
14. <span data-ttu-id="0641f-165">在**佇列管理員**方塊中，選取預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="0641f-165">In the **Queue Manager** box, select the default queue manager.</span></span>  
  
15. <span data-ttu-id="0641f-166">在**佇列**方塊中輸入"REPLYTOQ"，然後再按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="0641f-166">In the **Queue** box, type " REPLYTOQ", and then click **Export**.</span></span>  
  
16. <span data-ttu-id="0641f-167">在**匯出**對話方塊中，按一下**Create Queue**，然後按一下**確定**或**完成**直到結束所有對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0641f-167">In the **Export** dialog box, click **Create Queue**, and then click**OK**or **Done** until you have exited all dialog boxes.</span></span>  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a><span data-ttu-id="0641f-168">建立傳送埠和 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="0641f-168">Creating the Send Port and MQSeries Queue</span></span>  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a><span data-ttu-id="0641f-169">若要建立傳送埠和 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="0641f-169">To create the send port and MQSeries queue</span></span>  
  
1.  <span data-ttu-id="0641f-170">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="0641f-170">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="0641f-171">在**傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入"MQSolicitResponse"。</span><span class="sxs-lookup"><span data-stu-id="0641f-171">In the **Send Port Properties** dialog box, in the **Name** box, type "MQSolicitResponse".</span></span>  
  
3.  <span data-ttu-id="0641f-172">在**傳輸類型**方塊中，選取**MQSeries**。</span><span class="sxs-lookup"><span data-stu-id="0641f-172">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
4.  <span data-ttu-id="0641f-173">在**傳送管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="0641f-173">In the **Send pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span></span>  
  
5.  <span data-ttu-id="0641f-174">在**接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。</span><span class="sxs-lookup"><span data-stu-id="0641f-174">In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
6.  <span data-ttu-id="0641f-175">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0641f-175">Click **Configure**.</span></span>  
  
7.  <span data-ttu-id="0641f-176">在**MQSeries 傳輸屬性**對話方塊中，於**佇列定義**方塊中，按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0641f-176">In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the ellipsis (…) button.</span></span>  
  
8.  <span data-ttu-id="0641f-177">在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="0641f-177">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
9. <span data-ttu-id="0641f-178">在**佇列管理員**方塊中，選取預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="0641f-178">In the **Queue Manager** box, select the default queue manager.</span></span>  
  
10. <span data-ttu-id="0641f-179">在**佇列**方塊中輸入"SOLICITRESPONSEQ"，然後再按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="0641f-179">In the **Queue** box, type " SOLICITRESPONSEQ", and then click **Export**.</span></span>  
  
11. <span data-ttu-id="0641f-180">在 匯出 對話方塊中，按一下  **Create Queue**，然後按一下 **確定**或**完成**直到結束所有對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0641f-180">In the Export dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog boxes.</span></span>  
  
## <a name="enabling-the-receive-location-and-starting-the-send-port"></a><span data-ttu-id="0641f-181">啟用接收位置及啟動傳送埠</span><span class="sxs-lookup"><span data-stu-id="0641f-181">Enabling the Receive Location and Starting the Send Port</span></span>  
 <span data-ttu-id="0641f-182">這個程序會建立協調流程接收檔案所需的資料夾，並將相互關聯訊息和回應訊息傳送到輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="0641f-182">This procedure creates the folders required to receive the file into the orchestration and sends the correlated message and response message to the output folders.</span></span>  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="0641f-183">啟用接收位置和啟動傳送埠</span><span class="sxs-lookup"><span data-stu-id="0641f-183">To enable the receive location and start the send port</span></span>  
  
1.  <span data-ttu-id="0641f-184">在 BizTalk Server 管理主控台中，按一下 **接收埠**。</span><span class="sxs-lookup"><span data-stu-id="0641f-184">In the BizTalk Server Administration console, click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="0641f-185">在詳細資料窗格中，以滑鼠右鍵按一下**MQIn**接收位置，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="0641f-185">In the details pane, right-click the **MQIn** receive location and click **Enable**.</span></span>  
  
3.  <span data-ttu-id="0641f-186">在詳細資料窗格中，以滑鼠右鍵按一下**MQOut**傳送連接埠，然後按一下**開始。**</span><span class="sxs-lookup"><span data-stu-id="0641f-186">In the details pane, right-click the **MQOut** send port and click **Start.**</span></span>  
  
## <a name="creating-the-folders-used-by-the-application"></a><span data-ttu-id="0641f-187">建立應用程式使用的資料夾</span><span class="sxs-lookup"><span data-stu-id="0641f-187">Creating the Folders Used by the Application</span></span>  
  
#### <a name="to-create-the-folders-used-by-the-application"></a><span data-ttu-id="0641f-188">若要建立應用程式使用的資料夾</span><span class="sxs-lookup"><span data-stu-id="0641f-188">To create the folders used by the application</span></span>  
  
1.  <span data-ttu-id="0641f-189">在 C:\ 磁碟機上建立名為 "temp" 的資料夾 (如果沒有的話)。</span><span class="sxs-lookup"><span data-stu-id="0641f-189">If one does not already exist, create a folder named "temp" on your C:\ drive.</span></span>  
  
2.  <span data-ttu-id="0641f-190">建立資料夾下的**C:\temp**目錄名為"Pickup2"、"Dropit2"和"MoveIt"。</span><span class="sxs-lookup"><span data-stu-id="0641f-190">Create folders under the **C:\temp** directory named "Pickup2", "Dropit2", and "MoveIt".</span></span>  
  
## <a name="modifying-the-orchestration-used-by-the-application"></a><span data-ttu-id="0641f-191">修改應用程式使用的協調流程</span><span class="sxs-lookup"><span data-stu-id="0641f-191">Modifying the Orchestration Used by the Application</span></span>  
 <span data-ttu-id="0641f-192">這個程序會修改應用程式使用的協調流程。</span><span class="sxs-lookup"><span data-stu-id="0641f-192">This procedure modifies the orchestration used by the application.</span></span>  
  
||  
|-|  
|<span data-ttu-id="0641f-193">若要修改應用程式使用的協調流程</span><span class="sxs-lookup"><span data-stu-id="0641f-193">To modify the Orchestration used by the application</span></span>|  
|<span data-ttu-id="0641f-194">-在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按兩下方案檔， **[mqscorrelationsolicitresponse.sln]**，若要開啟的方案。</span><span class="sxs-lookup"><span data-stu-id="0641f-194">- In Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], double-click the solution file, **MQSCorrelationSolicitResponse.sln**, to open the solution.</span></span><br /><br /> <span data-ttu-id="0641f-195">-從 方案總管 窗格中，按兩下 協調流程**mqscorrelationsolicitresponse.odx**檢視協調流程。</span><span class="sxs-lookup"><span data-stu-id="0641f-195">- From the Solution Explorer pane, double-click the orchestration **MQSCorrelationSolicitResponse.odx** to view the orchestration.</span></span><br /><br /> <span data-ttu-id="0641f-196">-按兩下訊息指派圖形**MessageAssignment_1**以啟動 BizTalk 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="0641f-196">- Double-click the message assignment shape **MessageAssignment_1** to launch the BizTalk Expression Editor.</span></span><br /><br /> <span data-ttu-id="0641f-197">輸入下列運算式為適當的 MQSeries 佇列管理員名稱：</span><span class="sxs-lookup"><span data-stu-id="0641f-197">- Enter the appropriate MQSeries queue manager name for the following expression:</span></span><br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_ReplyToQMgr) = "QM_<machine_name>";`<br /><br /> <span data-ttu-id="0641f-198">-如果您想要從 BizTalk 傳送到包含原始訊息而不是只有前 100 個位元組的整個內容的回應訊息，修改下列行在 「 BizTalk 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="0641f-198">- If you would like for the response message sent from BizTalk to contain the entire contents of the original message instead of only the first 100 bytes, modify the following line in the BizTalk Expression Editor.</span></span><br /><br /> <span data-ttu-id="0641f-199">-原始行：</span><span class="sxs-lookup"><span data-stu-id="0641f-199">- Original line:</span></span><br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_Report) = 768;`<br /><br /> <span data-ttu-id="0641f-200">若要變更：</span><span class="sxs-lookup"><span data-stu-id="0641f-200">Change to:</span></span><br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_Report) = 1792;`<br /><br /> <span data-ttu-id="0641f-201">-在 BizTalk 運算式編輯器 」 中，按一下**確定**以儲存修改過的運算式。</span><span class="sxs-lookup"><span data-stu-id="0641f-201">- In the BizTalk Expression Editor, click **OK** to save the modified expression.</span></span><br /><br /> <span data-ttu-id="0641f-202">-在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，選取**檔案**，然後選取**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="0641f-202">- In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select **File**, and then select **Save All**.</span></span>|  
  
## <a name="building-and-deploying-the-sample"></a><span data-ttu-id="0641f-203">建置和部署範例</span><span class="sxs-lookup"><span data-stu-id="0641f-203">Building and Deploying the Sample</span></span>  
 <span data-ttu-id="0641f-204">這個程序會建置和部署包含此應用程式所使用協調流程的方案。</span><span class="sxs-lookup"><span data-stu-id="0641f-204">This procedure builds and deploys the solution that contains the orchestration used in this application.</span></span>  
  
#### <a name="to-build-and-deploy-the-sample"></a><span data-ttu-id="0641f-205">若要建置和部署範例</span><span class="sxs-lookup"><span data-stu-id="0641f-205">To build and deploy the sample</span></span>  
  
1.  <span data-ttu-id="0641f-206">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="0641f-206">In a command window, navigate to the following folder:</span></span>  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse`  
  
2.  <span data-ttu-id="0641f-207">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0641f-207">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    1.  <span data-ttu-id="0641f-208">為專案建立強式名稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="0641f-208">Creates a strong name key for the project.</span></span>  
  
    2.  <span data-ttu-id="0641f-209">編譯和部署協調流程專案。</span><span class="sxs-lookup"><span data-stu-id="0641f-209">Compiles and deploys the orchestration project.</span></span>  
  
    3.  <span data-ttu-id="0641f-210">使用 FILE 配接器建立傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="0641f-210">Creates a send port and a receive port with the File adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0641f-211">由於這個協調流程指定使用 FILE 配接器傳送和接收檔案的繫結，因此當您部署協調流程時，會建立必要的傳送埠、接收埠和接收位置，以供協調流程接收檔案並輸出相互關聯訊息和回應訊息。</span><span class="sxs-lookup"><span data-stu-id="0641f-211">Since this orchestration specifies the bindings for sending and receiving files with the file adapter, when you deploy the orchestration the necessary send ports, receive port, and receive location will be created for receiving a file into the orchestration and outputting the correlation message and the response message.</span></span>  
  
## <a name="binding-and-starting-the-orchestration"></a><span data-ttu-id="0641f-212">繫結與啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="0641f-212">Binding and Starting the Orchestration</span></span>  
 <span data-ttu-id="0641f-213">這個程序會繫結協調流程與主控件以及適當的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="0641f-213">This procedure binds the orchestration to the host and appropriate send ports and receive locations.</span></span>  
  
#### <a name="to-bind-and-start-the-orchestration"></a><span data-ttu-id="0641f-214">若要繫結並啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="0641f-214">To bind and start the orchestration</span></span>  
  
1.  <span data-ttu-id="0641f-215">在 BizTalk Server 管理主控台中，展開 **協調流程**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0641f-215">In the BizTalk Server Administration console, expand the **Orchestrations** folder.</span></span>  
  
2.  <span data-ttu-id="0641f-216">在詳細資料窗格中，以滑鼠右鍵按一下 **[mqscorrelationsolicitresponse]** 協調流程，然後按一下**繫結**。</span><span class="sxs-lookup"><span data-stu-id="0641f-216">In the details pane, right-click the **MQSCorrelationSolicitResponse** orchestration and click **Bind**.</span></span>  
  
3.  <span data-ttu-id="0641f-217">將協調流程連接埠繫結至下列傳送埠和接收位置：</span><span class="sxs-lookup"><span data-stu-id="0641f-217">Bind the orchestration ports to the following send ports and receive locations:</span></span>  
  
    |<span data-ttu-id="0641f-218">**協調流程連接埠**</span><span class="sxs-lookup"><span data-stu-id="0641f-218">**Orchestration Port**</span></span>|<span data-ttu-id="0641f-219">**傳送埠 / 接收位置**</span><span class="sxs-lookup"><span data-stu-id="0641f-219">**Messaging Port / Receive Location**</span></span>|  
    |----------------------------|--------------------------------------------|  
    |<span data-ttu-id="0641f-220">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="0641f-220">FileReceivePort</span></span>|<span data-ttu-id="0641f-221">MQSCorrelationSolicitResponse.Orchestration.FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="0641f-221">MQSCorrelationSolicitResponse.Orchestration.FileReceivePort</span></span>|  
    |<span data-ttu-id="0641f-222">MQSeriesResponseReceivePort</span><span class="sxs-lookup"><span data-stu-id="0641f-222">MQSeriesResponseReceivePort</span></span>|<span data-ttu-id="0641f-223">MQReply</span><span class="sxs-lookup"><span data-stu-id="0641f-223">MQReply</span></span>|  
    |<span data-ttu-id="0641f-224">SolicitResponsePort</span><span class="sxs-lookup"><span data-stu-id="0641f-224">SolicitResponsePort</span></span>|<span data-ttu-id="0641f-225">MQSolicitResponse</span><span class="sxs-lookup"><span data-stu-id="0641f-225">MQSolicitResponse</span></span>|  
    |<span data-ttu-id="0641f-226">TempPort</span><span class="sxs-lookup"><span data-stu-id="0641f-226">TempPort</span></span>|<span data-ttu-id="0641f-227">MQSCorrelationSolicitResponse.Orchestration.TempPort</span><span class="sxs-lookup"><span data-stu-id="0641f-227">MQSCorrelationSolicitResponse.Orchestration.TempPort</span></span>|  
    |<span data-ttu-id="0641f-228">FileSendPort</span><span class="sxs-lookup"><span data-stu-id="0641f-228">FileSendPort</span></span>|<span data-ttu-id="0641f-229">MQSCorrelationSolicitResponse.Orchestration.FileSendPort</span><span class="sxs-lookup"><span data-stu-id="0641f-229">MQSCorrelationSolicitResponse.Orchestration.FileSendPort</span></span>|  
  
4.  <span data-ttu-id="0641f-230">按一下**主機**。</span><span class="sxs-lookup"><span data-stu-id="0641f-230">Click **Host**.</span></span>  
  
5.  <span data-ttu-id="0641f-231">在**主機**方塊中，選取**BizTalkServerApplication**按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0641f-231">In the **Host** box, select **BizTalkServerApplication** and click **OK**.</span></span>  
  
6.  <span data-ttu-id="0641f-232">在**傳送埠**，以滑鼠右鍵按一下 **[mqscorrelationsolicitresponse.orchestration.tempport]**，然後選取**啟動**。</span><span class="sxs-lookup"><span data-stu-id="0641f-232">In **Send Ports**, right-click **MQSCorrelationSolicitResponse.Orchestration.TempPort**, and then select **Start**.</span></span>  
  
7.  <span data-ttu-id="0641f-233">在**傳送埠**，以滑鼠右鍵按一下 **[mqscorrelationsolicitresponse.orchestration.filesendport]**，然後選取**啟動**。</span><span class="sxs-lookup"><span data-stu-id="0641f-233">In **Send Ports**, right-click **MQSCorrelationSolicitResponse.Orchestration.FileSendPort**, and then select **Start**.</span></span>  
  
8.  <span data-ttu-id="0641f-234">在**接收位置**，以滑鼠右鍵按一下 **[mqscorrelationsolicitresponse.orchestration.filereceiveport]**，然後選取**啟用**。</span><span class="sxs-lookup"><span data-stu-id="0641f-234">In **Receive Locations**, right-click **MQSCorrelationSolicitResponse.Orchestration.FileReceivePort**, and then select **Enable**.</span></span>  
  
9. <span data-ttu-id="0641f-235">以滑鼠右鍵按一下協調流程，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="0641f-235">Right-click the orchestration and click **Start**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0641f-236">啟動協調流程也會自動登錄協調流程。</span><span class="sxs-lookup"><span data-stu-id="0641f-236">Starting the orchestration also automatically enlists the orchestration.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="0641f-237">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="0641f-237">Testing the Application</span></span>  
 <span data-ttu-id="0641f-238">這個程序會測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="0641f-238">This procedure tests the application.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="0641f-239">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="0641f-239">To test the application</span></span>  
  
1.  <span data-ttu-id="0641f-240">將檔案放在**C:\Temp\Pickup2**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0641f-240">Put a file in the **C:\Temp\Pickup2** folder.</span></span>  
  
2.  <span data-ttu-id="0641f-241">檢查中的檔案**C:\Temp\Dropit2**資料夾和**C:\Temp\Moveit**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0641f-241">Examine the files in the **C:\Temp\Dropit2** folder and the **C:\Temp\Moveit**folder.</span></span>  
  
    -   <span data-ttu-id="0641f-242">**C:\Temp\Dropit2**資料夾應包含已原本收取訊息的複本[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0641f-242">The **C:\Temp\Dropit2** folder should contain a copy of the message that was originally picked up by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="0641f-243">**C:\Temp\Moveit**資料夾應包含回應文件的訊息識別項 (MQMD_MsgId) 和相互關聯識別項 (MQMD_CorrelId)。</span><span class="sxs-lookup"><span data-stu-id="0641f-243">The **C:\Temp\Moveit**folder should contain a response document with the message identifier (MQMD_MsgId) and the correlation identifier (MQMD_CorrelId).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0641f-244">如果您停用**MQReply**接收位置，您可以檢查 WebSphere MQ Explorer 中的訊息，並查看所設定的訊息和相互關聯識別項。</span><span class="sxs-lookup"><span data-stu-id="0641f-244">If you disable the **MQReply** receive location, you can examine the message in WebSphere MQ Explorer and see that the message and correlation identifiers are set.</span></span> <span data-ttu-id="0641f-245">若要這樣做，請啟動**WebSphere MQ Explorer**並檢查訊息置於**REPLYTOQ**佇列。</span><span class="sxs-lookup"><span data-stu-id="0641f-245">To do this, launch the **WebSphere MQ Explorer** and examine the message placed in the **REPLYTOQ** queue.</span></span> <span data-ttu-id="0641f-246">訊息和相互關聯識別碼會顯示在**識別碼** 索引標籤**Messageproperties**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0641f-246">The message and correlation identifiers are displayed on the **Identifiers** tab of the **Messageproperties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0641f-247">請參閱</span><span class="sxs-lookup"><span data-stu-id="0641f-247">See Also</span></span>  
 <span data-ttu-id="0641f-248">[使用要求-回覆相互關聯訊息](../core/correlating-messages-using-request-reply.md) </span><span class="sxs-lookup"><span data-stu-id="0641f-248">[Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md) </span></span>  
 [<span data-ttu-id="0641f-249">MQSeries 配接器範例</span><span class="sxs-lookup"><span data-stu-id="0641f-249">MQSeries Adapter Samples</span></span>](../core/mqseries-adapter-samples.md)