---
title: OrderedSample （BizTalk Server 範例） |Microsoft 文件
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
- MQSeries adapters, examples
ms.assetid: 7e59ff43-d425-40cd-9725-af13084f83d9
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b9e93c7bb9cb59088e465dc53dd992ffd5f1c11
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974748"
---
# <a name="orderedsample-biztalk-server-sample"></a><span data-ttu-id="fdb34-102">OrderedSample (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="fdb34-102">OrderedSample (BizTalk Server Sample)</span></span>
<span data-ttu-id="fdb34-103">OrderedSample 範例會示範如何使用協調流程，以往返方式接收和傳送已排序的訊息序列。</span><span class="sxs-lookup"><span data-stu-id="fdb34-103">The OrderedSample sample demonstrates how to use an orchestration to receive and send an ordered series of messages in a round-trip fashion.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="fdb34-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="fdb34-104">What This Sample Does</span></span>  
 <span data-ttu-id="fdb34-105">此範例會假設 MQSeries 佇列中有訊息存在，以便從其中接收訊息。</span><span class="sxs-lookup"><span data-stu-id="fdb34-105">The sample assumes there are messages in the MQSeries queue from which it receives messages.</span></span> <span data-ttu-id="fdb34-106">當配接器從 MQSeries 佇列讀取訊息時，會依序讀取訊息並將其提交至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fdb34-106">When the adapter reads the messages from MQSeries queue, it reads them in-order and submits them to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="fdb34-107">在協調流程，接收埠**mqreceive**，具有其**排序的傳遞**屬性設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-107">The receive port in the orchestration, **mqreceive**, has its **Ordered Delivery** property set to **True**.</span></span>  
  
 <span data-ttu-id="fdb34-108">至於傳送端，協調流程會傳送訊息並等待傳遞通知，收到通知後才會傳送下一則訊息。</span><span class="sxs-lookup"><span data-stu-id="fdb34-108">For the send side, the orchestration sends a message and then waits for a delivery notification before sending the next message.</span></span> <span data-ttu-id="fdb34-109">傳送埠， **mqsend**具有其**傳遞通知**屬性設定為**Transmitted**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-109">The send port, **mqsend** has its **Delivery Notification** property set to **Transmitted**.</span></span> <span data-ttu-id="fdb34-110">為了讓此範例簡單好用，協調流程將使用無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="fdb34-110">To keep the example simple, the orchestration uses an infinite loop.</span></span>  
  
 <span data-ttu-id="fdb34-111">協調流程可以接收批次訊息和單一訊息。</span><span class="sxs-lookup"><span data-stu-id="fdb34-111">The orchestration can receive batches of messages and single messages.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="fdb34-112">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="fdb34-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="fdb34-113">*\<範例路徑\>* \AdaptersUsage\MQSeriesAdapter\OrderedSample</span><span class="sxs-lookup"><span data-stu-id="fdb34-113">*\<Samples Path\>* \AdaptersUsage\MQSeriesAdapter\OrderedSample</span></span>  
  
 <span data-ttu-id="fdb34-114">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="fdb34-114">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="fdb34-115">檔案</span><span class="sxs-lookup"><span data-stu-id="fdb34-115">File</span></span>|<span data-ttu-id="fdb34-116">Description</span><span class="sxs-lookup"><span data-stu-id="fdb34-116">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="fdb34-117">OrderedReceiveSend.btproj、</span><span class="sxs-lookup"><span data-stu-id="fdb34-117">OrderedReceiveSend.btproj,</span></span><br /><br /> <span data-ttu-id="fdb34-118">OrderedReceiveSend.sln</span><span class="sxs-lookup"><span data-stu-id="fdb34-118">OrderedReceiveSend.sln</span></span>|<span data-ttu-id="fdb34-119">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="fdb34-119">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="fdb34-120">OrderedReceiveSendOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="fdb34-120">OrderedReceiveSendOrchestration.odx</span></span>|<span data-ttu-id="fdb34-121">應用程式的協調流程。</span><span class="sxs-lookup"><span data-stu-id="fdb34-121">The orchestration of the application.</span></span>|  
|<span data-ttu-id="fdb34-122">OrderedSample.snk</span><span class="sxs-lookup"><span data-stu-id="fdb34-122">OrderedSample.snk</span></span>|<span data-ttu-id="fdb34-123">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="fdb34-123">The strong naming key file.</span></span>|  
|<span data-ttu-id="fdb34-124">**Setup.bat**</span><span class="sxs-lookup"><span data-stu-id="fdb34-124">**Setup.bat**</span></span>|<span data-ttu-id="fdb34-125">建置並初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="fdb34-125">Builds and initializes this sample.</span></span>|  
  
## <a name="building-and-running-the-sample"></a><span data-ttu-id="fdb34-126">建置和執行範例</span><span class="sxs-lookup"><span data-stu-id="fdb34-126">Building and Running the Sample</span></span>  
  
#### <a name="to-build-and-deploy-the-sample"></a><span data-ttu-id="fdb34-127">若要建置和部署範例</span><span class="sxs-lookup"><span data-stu-id="fdb34-127">To build and deploy the sample</span></span>  
  
1.  <span data-ttu-id="fdb34-128">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="fdb34-128">In a command window, navigate to the following folder:</span></span>  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\OrderedSample`  
  
2.  <span data-ttu-id="fdb34-129">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fdb34-129">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    1.  <span data-ttu-id="fdb34-130">為專案建立強式名稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="fdb34-130">Creates a strong name key for the project.</span></span>  
  
    2.  <span data-ttu-id="fdb34-131">編譯和部署協調流程專案。</span><span class="sxs-lookup"><span data-stu-id="fdb34-131">Compiles and deploys the orchestration project.</span></span>  
  
 <span data-ttu-id="fdb34-132">如果您有 MQSeries Server for Windows 安裝的必要權限，則可以透過配接器對話方塊建立 MQSeries 佇列並略過下一個程序。</span><span class="sxs-lookup"><span data-stu-id="fdb34-132">If you have the required permissions to the MQSeries Server for Windows installation, you can create the MQSeries queue through the adapter dialog boxes, and can skip the next procedure.</span></span> <span data-ttu-id="fdb34-133">如果您沒有這類存取權限，可以使用 IBM WebSphere MQ Explorer 來建立佇列。</span><span class="sxs-lookup"><span data-stu-id="fdb34-133">If you do not have such access, you can create the queue using the IBM WebSphere MQ Explorer.</span></span> <span data-ttu-id="fdb34-134">若要透過 WebSphere MQ Explorer 建立佇列，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="fdb34-134">To create the queues through the WebSphere MQ Explorer, complete the following steps.</span></span>  
  
## <a name="creating-the-mqseries-queues-through-the-websphere-mq-explorer"></a><span data-ttu-id="fdb34-135">透過 WebSphere MQ Explorer 建立 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="fdb34-135">Creating the MQSeries Queues Through the WebSphere MQ Explorer</span></span>  
  
#### <a name="to-create-the-mqseries-queues-through-the-websphere-mq-explorer"></a><span data-ttu-id="fdb34-136">若要透過 WebSphere MQ Explorer 建立 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="fdb34-136">To create the MQSeries queues through the WebSphere MQ Explorer</span></span>  
  
1.  <span data-ttu-id="fdb34-137">按一下**啟動**，指向 **所有程式**，指向  **IBM WebSphere MQ**，然後按一下  **WebSphere MQ Explorer**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-137">Click **Start**, point to **All Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2.  <span data-ttu-id="fdb34-138">按兩下**佇列管理員**，然後按兩下**預設佇列管理員**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-138">Double-click **Queue Managers**, and then double-click the **default queue manager**.</span></span> <span data-ttu-id="fdb34-139">預設佇列管理員的名稱通常為 QM_<machine_name>，其中 machine_name 是電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="fdb34-139">The default queue manager is typically named QM_<machine_name> where machine_name is the name of your computer.</span></span>  
  
3.  <span data-ttu-id="fdb34-140">以滑鼠右鍵按一下**佇列**，指向 **新增**，然後按一下 **本機佇列**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-140">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
4.  <span data-ttu-id="fdb34-141">在**建立本機佇列**對話方塊中，於**佇列名稱**，型別 **"queue1"**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-141">In **Create Local Queue** dialog box, in **Queue Name**, type **"queue1"**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="fdb34-142">以滑鼠右鍵按一下**佇列**，按一下 **新增**，然後按一下 **本機佇列**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-142">Right-click **Queues**, click **New**, and then click **Local Queue**.</span></span>  
  
6.  <span data-ttu-id="fdb34-143">中**建立本機佇列**對話方塊中，於**佇列名稱**，型別 **"queue2"**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-143">In the **Create Local Queue** dialog box, in **Queue Name**, type **"queue2"**, and then click **OK**.</span></span>  
  
## <a name="creating-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="fdb34-144">建立接收位置與 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="fdb34-144">Creating the Receive Location and the MQSeries Queue</span></span>  
 <span data-ttu-id="fdb34-145">此程序會建立傳送埠和接收位置，以傳送訊息至 MQSeries 以及接收來自 MQSeries 的相互關聯訊息。</span><span class="sxs-lookup"><span data-stu-id="fdb34-145">This procedure creates the send port and receive location to send the message to and receive the correlation message from MQSeries.</span></span> <span data-ttu-id="fdb34-146">如果您還沒有建立 MQSeries 佇列，則在建立接收位置時，也會建立 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="fdb34-146">The MQSeries queue will also be created when you create the receive location if not already created.</span></span>  
  
#### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="fdb34-147">建立接收位置與 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="fdb34-147">To create the receive location and the MQSeries queue</span></span>  
  
1.  <span data-ttu-id="fdb34-148">開啟 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="fdb34-148">Open the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="fdb34-149">展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開所需的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fdb34-149">Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the required application.</span></span>  
  
3.  <span data-ttu-id="fdb34-150">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-150">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="fdb34-151">在**單向接收埠屬性**對話方塊方塊中，輸入，在**名稱**方塊中，輸入**OrderedSampleReceive**按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-151">In the **One-way Receive Port Properties** dialog box type, in the **Name** box type **OrderedSampleReceive** and click **OK**.</span></span>  
  
5.  <span data-ttu-id="fdb34-152">在左窗格中，按一下 **接收位置**索引標籤，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-152">In the left pane, click **Receive Locations** tab, and then click **New**.</span></span>  
  
6.  <span data-ttu-id="fdb34-153">在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入 「**OrderedSampleReceiveLocation**"。</span><span class="sxs-lookup"><span data-stu-id="fdb34-153">In the **Receive Location Properties** dialog box, in the **Name** box type "**OrderedSampleReceiveLocation**".</span></span>  
  
7.  <span data-ttu-id="fdb34-154">在**傳輸類型**方塊中，選取**MQSeries**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-154">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
8.  <span data-ttu-id="fdb34-155">在**接收處理常式**方塊中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-155">In the **Receive Handler** box, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="fdb34-156">在**接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-156">In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
10. <span data-ttu-id="fdb34-157">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-157">Click **Configure**.</span></span>  
  
11. <span data-ttu-id="fdb34-158">在**MQSeries 傳輸屬性**對話方塊中，於**輪詢間隔**方塊中，輸入 **"10"**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-158">In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type **"10"**.</span></span>  
  
12. <span data-ttu-id="fdb34-159">在**佇列定義**方塊中，按一下**省略符號 （...）**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="fdb34-159">In the **Queue Definition** box, click the **ellipsis (…)** button.</span></span>  
  
13. <span data-ttu-id="fdb34-160">在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="fdb34-160">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
14. <span data-ttu-id="fdb34-161">在**佇列管理員**方塊中，選取**預設佇列管理員**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-161">In the **Queue Manager** box, select the **default queue manager**.</span></span>  
  
15. <span data-ttu-id="fdb34-162">在**佇列**方塊中，輸入 「 **queue1**"，然後按一下 **匯出**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-162">In the **Queue** box, type " **queue1**", and then click **Export**.</span></span>  
  
16. <span data-ttu-id="fdb34-163">在**匯出**對話方塊中，按一下**Create Queue**，然後按一下**確定**或**完成**直到結束所有對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fdb34-163">In the **Export** dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog boxes.</span></span>  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a><span data-ttu-id="fdb34-164">建立傳送埠和 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="fdb34-164">Creating the Send Port and MQSeries Queue</span></span>  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a><span data-ttu-id="fdb34-165">若要建立傳送埠和 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="fdb34-165">To create the send port and MQSeries queue</span></span>  
  
1.  <span data-ttu-id="fdb34-166">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-166">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="fdb34-167">在**靜態連接埠屬性**對話方塊方塊中，輸入，在**名稱**方塊中，輸入 「**OrderedSampleSend**"。</span><span class="sxs-lookup"><span data-stu-id="fdb34-167">In the **Static Port Properties** dialog box type, in the **Name** box, type "**OrderedSampleSend**".</span></span>  
  
3.  <span data-ttu-id="fdb34-168">在**傳輸類型**方塊中，選取**MQSeries**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-168">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
4.  <span data-ttu-id="fdb34-169">在**傳送管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-169">In the **Send pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span></span>  
  
5.  <span data-ttu-id="fdb34-170">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-170">Click **Configure**.</span></span>  
  
6.  <span data-ttu-id="fdb34-171">在**MQSeries 傳輸屬性**對話方塊中，於**佇列定義**方塊中，按一下**省略符號 （...）**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="fdb34-171">In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the **ellipsis (…)** button.</span></span>  
  
7.  <span data-ttu-id="fdb34-172">在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="fdb34-172">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  
  
8.  <span data-ttu-id="fdb34-173">在**佇列管理員**方塊中，選取**預設佇列管理員**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-173">In the **Queue Manager** box, select the **default queue manager**.</span></span>  
  
9. <span data-ttu-id="fdb34-174">在**佇列**方塊中，輸入 「 **queue2**"，然後按一下 **匯出**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-174">In the **Queue** box, type " **queue2**", and then click **Export**.</span></span>  
  
10. <span data-ttu-id="fdb34-175">在**匯出**對話方塊中，按一下**Create Queue**，然後按一下**確定**或**完成**直到結束所有對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fdb34-175">In the **Export** dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog boxes.</span></span>  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="fdb34-176">啟用接收位置和啟動傳送埠</span><span class="sxs-lookup"><span data-stu-id="fdb34-176">To enable the receive location and start the send port</span></span>  
  
1.  <span data-ttu-id="fdb34-177">在 BizTalk Server 管理主控台中，按一下 **接收埠**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-177">In the BizTalk Server Administration console, click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="fdb34-178">在詳細資料窗格中，以滑鼠右鍵按一下**MQIn**接收位置，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-178">In the details pane, right-click the **MQIn** receive location and click **Enable**.</span></span>  
  
3.  <span data-ttu-id="fdb34-179">在詳細資料窗格中，以滑鼠右鍵按一下**MQOut**傳送連接埠，然後按一下**開始。**</span><span class="sxs-lookup"><span data-stu-id="fdb34-179">In the details pane, right-click the **MQOut** send port and click **Start.**</span></span>  
  
#### <a name="to-bind-and-start-the-orchestration"></a><span data-ttu-id="fdb34-180">若要繫結並啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="fdb34-180">To bind and start the Orchestration</span></span>  
  
1.  <span data-ttu-id="fdb34-181">在 BizTalk Server 管理主控台中，展開 **協調流程**資料夾。</span><span class="sxs-lookup"><span data-stu-id="fdb34-181">In the BizTalk Server Administration console, expand the **Orchestrations** folder.</span></span>  
  
2.  <span data-ttu-id="fdb34-182">按兩下 **[orderedsampleorchestration]** 協調流程，然後再按一下**繫結**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-182">Double-click the **OrderedSampleOrchestration** orchestration, and then click  **Bindings**.</span></span>  
  
3.  <span data-ttu-id="fdb34-183">將協調流程連接埠繫結至下列傳送埠和接收位置：</span><span class="sxs-lookup"><span data-stu-id="fdb34-183">Bind the orchestration ports to the following send ports and receive locations:</span></span>  
  
    |<span data-ttu-id="fdb34-184">協調流程連接埠</span><span class="sxs-lookup"><span data-stu-id="fdb34-184">Orchestration Port</span></span>|<span data-ttu-id="fdb34-185">傳送埠/接收位置</span><span class="sxs-lookup"><span data-stu-id="fdb34-185">Messaging Port / Receive Location</span></span>|  
    |------------------------|----------------------------------------|  
    |<span data-ttu-id="fdb34-186">mqreceive</span><span class="sxs-lookup"><span data-stu-id="fdb34-186">mqreceive</span></span>|<span data-ttu-id="fdb34-187">OrderedSampleReceive</span><span class="sxs-lookup"><span data-stu-id="fdb34-187">OrderedSampleReceive</span></span>|  
    |<span data-ttu-id="fdb34-188">mqsend</span><span class="sxs-lookup"><span data-stu-id="fdb34-188">mqsend</span></span>|<span data-ttu-id="fdb34-189">OrderedSampleSend</span><span class="sxs-lookup"><span data-stu-id="fdb34-189">OrderedSampleSend</span></span>|  
  
4.  <span data-ttu-id="fdb34-190">按一下**主機**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-190">Click **Host**.</span></span>  
  
5.  <span data-ttu-id="fdb34-191">在**主機**方塊中，選取**BizTalkServerApplication**，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-191">In the **Host** box, select **BizTalkServerApplication**, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="fdb34-192">以滑鼠右鍵按一下**協調流程**按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="fdb34-192">Right click the **Orchestration** and click **Start**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="fdb34-193">執行範例</span><span class="sxs-lookup"><span data-stu-id="fdb34-193">To run the sample</span></span>  
  
1.  <span data-ttu-id="fdb34-194">啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="fdb34-194">Start the orchestration.</span></span>  
  
2.  <span data-ttu-id="fdb34-195">將訊息放入您已設定接收位置要從中讀取的 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="fdb34-195">Put messages into the MQSeries queue from which you have configured the receive location to read.</span></span>  
  
3.  <span data-ttu-id="fdb34-196">使用 WebSphere MQ Explorer 檢視傳送佇列 (您已設定傳送埠要將訊息傳送至此佇列) 內的訊息。</span><span class="sxs-lookup"><span data-stu-id="fdb34-196">View the messages in WebSphere MQ Explorer in the send queue to which you have configured the send port to send messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb34-197">請參閱</span><span class="sxs-lookup"><span data-stu-id="fdb34-197">See Also</span></span>  
 [<span data-ttu-id="fdb34-198">MQSeries 配接器範例</span><span class="sxs-lookup"><span data-stu-id="fdb34-198">MQSeries Adapter Samples</span></span>](../core/mqseries-adapter-samples.md)