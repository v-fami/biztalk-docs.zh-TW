---
title: MQSCorrelationSetOrchestration （BizTalk Server 範例） |Microsoft Docs
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
ms.assetid: fcda65d0-e3ec-4ead-978d-3904903b8762
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d0057e9a9276de5eb3724f1af298822b03065a3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011775"
---
# <a name="mqscorrelationsetorchestration-biztalk-server-sample"></a><span data-ttu-id="6b184-102">MQSCorrelationSetOrchestration (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="6b184-102">MQSCorrelationSetOrchestration (BizTalk Server Sample)</span></span>
<span data-ttu-id="6b184-103">MQSCorrelationSetOrchestration 範例會示範如何使用 MQSeries 相互關聯識別項，將傳送至 MQSeries 佇列的相互關聯訊息送回到執行中的協調流程。</span><span class="sxs-lookup"><span data-stu-id="6b184-103">The MQSCorrelationSetOrchestration sample demonstrates how to use the MQSeries correlation identifier for correlating messages sent to an MQSeries queue back to a running orchestration.</span></span> <span data-ttu-id="6b184-104">協調流程設定 MQSeries 相互關聯識別項和訊息使用的識別碼值**MQMD_CorrelId**並**MQMD_MsgID**屬性。</span><span class="sxs-lookup"><span data-stu-id="6b184-104">The orchestration sets the MQSeries correlation identifier and message identifier values using the **MQMD_CorrelId** and **MQMD_MsgID** properties.</span></span> <span data-ttu-id="6b184-105">MQSeries 佇列管理員會將 MessageID 值複製到訊息的 CorrelationID 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b184-105">The MQSeries Queue Manager copies the MessageID value to the CorrelationID property of the message.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="6b184-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="6b184-106">Prerequisites</span></span>  
 <span data-ttu-id="6b184-107">此範例假設您已經在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的相同伺服器上安裝 IBM WebSphere MQSeries。</span><span class="sxs-lookup"><span data-stu-id="6b184-107">This sample assumes that you have installed IBM WebSphere MQSeries on the same server that you are running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  

## <a name="what-this-sample-does"></a><span data-ttu-id="6b184-108">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="6b184-108">What This Sample Does</span></span>  
 <span data-ttu-id="6b184-109">此範例會示範如何在傳送至 IBM WebSphere MQSeries Server 的訊息中，設定訊息識別項和相互關聯識別項。</span><span class="sxs-lookup"><span data-stu-id="6b184-109">This sample illustrates how to set a message identifier and correlation identifier in a message sent to an IBM WebSphere MQSeries Server.</span></span> <span data-ttu-id="6b184-110">這是將訊息相互關聯回執行中之協調流程執行個體的一種方法。</span><span class="sxs-lookup"><span data-stu-id="6b184-110">This is one method that can be used to correlate a message back to a running orchestration instance.</span></span> <span data-ttu-id="6b184-111">MQSeries 佇列管理員在收到訊息時，便會將 MessageID 值複製到訊息的 CorrelationID 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b184-111">When the MQSeries Queue Manager receives the message it copies the MessageID value to the CorrelationID property of the message.</span></span> <span data-ttu-id="6b184-112">這個 CorrelationID (**MQMD_CorrelId**) 就會用以協調流程中用來將訊息傳送至 MQSeries 的執行個體相關聯 MQSeries 上的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="6b184-112">This CorrelationID (**MQMD_CorrelId**) is then used in the orchestration to associate the response message on MQSeries with the instance used to send messages to MQSeries.</span></span>  

## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="6b184-113">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="6b184-113">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="6b184-114">這個範例所示範的實例中，將由協調流程處理的文件可以傳送至 MQSeries 佇列 (假設會進行其他處理)，並會傳回到執行中的協調流程。</span><span class="sxs-lookup"><span data-stu-id="6b184-114">This sample illustrates a scenario in which a document that is being processed by an orchestration can be sent to an MQSeries queue (presumably for additional processing) and returned back to the running orchestration.</span></span>  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="6b184-115">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="6b184-115">Where to Find This Sample</span></span>  
 <span data-ttu-id="6b184-116">*\<範例路徑\>* \AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration</span><span class="sxs-lookup"><span data-stu-id="6b184-116">*\<Samples Path\>* \AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration</span></span>  

 <span data-ttu-id="6b184-117">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="6b184-117">The following table shows the files in this sample and describes their purpose.</span></span>  

|<span data-ttu-id="6b184-118">**檔案**</span><span class="sxs-lookup"><span data-stu-id="6b184-118">**File**</span></span>|<span data-ttu-id="6b184-119">**說明**</span><span class="sxs-lookup"><span data-stu-id="6b184-119">**Description**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="6b184-120">**MQSCorrelationSetOrchestration.btproj，**</span><span class="sxs-lookup"><span data-stu-id="6b184-120">**MQSCorrelationSetOrchestration.btproj,**</span></span><br /><br /> <span data-ttu-id="6b184-121">**MQSCorrelationSetOrchestration.sln**</span><span class="sxs-lookup"><span data-stu-id="6b184-121">**MQSCorrelationSetOrchestration.sln**</span></span>|<span data-ttu-id="6b184-122">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="6b184-122">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="6b184-123">**MQSCorrelationSetOrchestration.odx**</span><span class="sxs-lookup"><span data-stu-id="6b184-123">**MQSCorrelationSetOrchestration.odx**</span></span>|<span data-ttu-id="6b184-124">應用程式的協調流程。</span><span class="sxs-lookup"><span data-stu-id="6b184-124">The orchestration of the application.</span></span>|  
|<span data-ttu-id="6b184-125">**MQSCorrelationSetOrchestration.snk**</span><span class="sxs-lookup"><span data-stu-id="6b184-125">**MQSCorrelationSetOrchestration.snk**</span></span>|<span data-ttu-id="6b184-126">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="6b184-126">The strong naming key file.</span></span>|  
|<span data-ttu-id="6b184-127">**Setup.bat**</span><span class="sxs-lookup"><span data-stu-id="6b184-127">**Setup.bat**</span></span>|<span data-ttu-id="6b184-128">建置並初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="6b184-128">Builds and initializes this sample.</span></span>|  

## <a name="how-to-use-this-sample"></a><span data-ttu-id="6b184-129">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="6b184-129">How to Use This Sample</span></span>  
 <span data-ttu-id="6b184-130">如果需要將訊息傳送至 MQSeries Server 以做為整體工作流程中的一個步驟，請併入此範例中所採用的邏輯。</span><span class="sxs-lookup"><span data-stu-id="6b184-130">Incorporate the logic employed in this sample if you need to send a message to MQSeries Server as one of the steps in overall workflow.</span></span>  

### <a name="to-create-the-mqseries-queue-through-the-websphere-mq-explorer"></a><span data-ttu-id="6b184-131">若要透過 WebSphere MQ Explorer 建立 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="6b184-131">To create the MQSeries queue through the WebSphere MQ Explorer</span></span>  

1.  <span data-ttu-id="6b184-132">按一下 **開始**，指向**程式**，指向**IBM WebSphere MQ**，然後按一下**WebSphere MQ Explorer**。</span><span class="sxs-lookup"><span data-stu-id="6b184-132">Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  

2.  <span data-ttu-id="6b184-133">按兩下**佇列管理員**，然後按兩下預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="6b184-133">Double-click **Queue Managers**, and then double-click the default queue manager.</span></span> <span data-ttu-id="6b184-134">預設佇列管理員通常會命名為**Qm_&lt < 電腦名稱 >** 何處*machine_name*是您電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b184-134">The default queue manager is typically named **QM_<machine_name>** where *machine_name* is the name of your computer.</span></span>  

3.  <span data-ttu-id="6b184-135">以滑鼠右鍵按一下**佇列**，指向**新增**，然後按一下**本機佇列**。</span><span class="sxs-lookup"><span data-stu-id="6b184-135">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  

4.  <span data-ttu-id="6b184-136">在 **建立本機佇列**對話方塊中，於**佇列名稱**，輸入"MQCorrelation"，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6b184-136">In **Create Local Queue** dialog box, in **Queue Name**, type "MQCorrelation", and then click **OK**.</span></span>  

### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a><span data-ttu-id="6b184-137">建立接收位置與 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="6b184-137">To create the receive location and the MQSeries queue</span></span>  

1.  <span data-ttu-id="6b184-138">開啟 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6b184-138">Open the BizTalk Server Administration console.</span></span>  

2.  <span data-ttu-id="6b184-139">依序展開**BizTalk Server 管理]**，展開**BizTalk 群組**，展開**應用程式**，然後展開 [必要的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6b184-139">Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the required application.</span></span>  

3.  <span data-ttu-id="6b184-140">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="6b184-140">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  

4.  <span data-ttu-id="6b184-141">在 **單向接收埠屬性**對話方塊中，於**名稱**方塊中輸入"MQIn"，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6b184-141">In the **One-way Receive Port Properties** dialog box, in the **Name** box type "MQIn" and click **OK**.</span></span>  

5.  <span data-ttu-id="6b184-142">在左窗格中，按一下**接收位置**索引標籤，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="6b184-142">In the left pane, click **Receive Locations** tab, and then click **New**.</span></span>  

6.  <span data-ttu-id="6b184-143">在 **接收位置屬性**對話方塊中，於**名稱**方塊中，輸入"MQIn"。</span><span class="sxs-lookup"><span data-stu-id="6b184-143">In the **Receive Location Properties** dialog box, in the **Name** box, type "MQIn".</span></span>  

7.  <span data-ttu-id="6b184-144">在 **傳輸類型**方塊中，選取**MQSeries**。</span><span class="sxs-lookup"><span data-stu-id="6b184-144">In the **Transport Type** box, select **MQSeries**.</span></span>  

8.  <span data-ttu-id="6b184-145">在 **接收處理常式**方塊中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="6b184-145">In the **Receive Handler** box, select **BizTalkServerApplication**.</span></span>  

9. <span data-ttu-id="6b184-146">在 **接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。</span><span class="sxs-lookup"><span data-stu-id="6b184-146">In the **Receive pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  

10. <span data-ttu-id="6b184-147">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="6b184-147">Click **Configure**.</span></span>  

11. <span data-ttu-id="6b184-148">在  **MQSeries 傳輸屬性**對話方塊中，於**輪詢間隔**方塊中，輸入"10"。</span><span class="sxs-lookup"><span data-stu-id="6b184-148">In the **MQSeries Transport Properties** dialog box, in the **Polling Interval** box, type "10".</span></span>  

12. <span data-ttu-id="6b184-149">在 **佇列定義**方塊中，按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6b184-149">In the **Queue Definition** box, click the ellipsis (…) button.</span></span>  

13. <span data-ttu-id="6b184-150">在 **佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="6b184-150">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  

14. <span data-ttu-id="6b184-151">在 **佇列管理員**方塊中，選取預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="6b184-151">In the **Queue Manager** box, select the default queue manager.</span></span>  

15. <span data-ttu-id="6b184-152">在 **佇列**方塊中輸入"MQCorrelation"，然後再按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="6b184-152">In the **Queue** box, type "MQCorrelation", and then click **Export**.</span></span>  

16. <span data-ttu-id="6b184-153">在 **匯出** 對話方塊中，按一下**Create Queue**，然後按一下 **確定**或**完成**直到結束所有對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6b184-153">In the **Export** dialog box, click **Create Queue**, and then click**OK**or **Done** until you have exited all dialog boxes.</span></span>  

### <a name="to-create-the-send-port-to-mqseries"></a><span data-ttu-id="6b184-154">若要建立通往 MQSeries 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="6b184-154">To create the send port to MQSeries</span></span>  

1.  <span data-ttu-id="6b184-155">以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="6b184-155">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  

2.  <span data-ttu-id="6b184-156">在 **傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入"MQOut"。</span><span class="sxs-lookup"><span data-stu-id="6b184-156">In the **Send Port Properties** dialog box, in the **Name** box, type "MQOut".</span></span>  

3.  <span data-ttu-id="6b184-157">在 **傳輸類型**方塊中，選取**MQSeries**。</span><span class="sxs-lookup"><span data-stu-id="6b184-157">In the **Transport Type** box, select **MQSeries**.</span></span>  

4.  <span data-ttu-id="6b184-158">在 **傳送管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="6b184-158">In the **Send pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.</span></span>  

5.  <span data-ttu-id="6b184-159">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="6b184-159">Click **Configure**.</span></span>  

6.  <span data-ttu-id="6b184-160">在  **MQSeries 傳輸屬性**對話方塊中，於**佇列定義**方塊中，按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6b184-160">In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** box, click the ellipsis (…) button.</span></span>  

7.  <span data-ttu-id="6b184-161">在 **佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="6b184-161">In the **Queue Definition** dialog box, in the **Server Name** box, type your computer name.</span></span>  

8.  <span data-ttu-id="6b184-162">在 **佇列管理員**方塊中，選取預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="6b184-162">In the **Queue Manager** box, select the default queue manager.</span></span>  

9. <span data-ttu-id="6b184-163">在 **佇列**方塊中輸入"MQCorrelation"，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6b184-163">In the **Queue** box, type "MQCorrelation", and then click **OK**.</span></span>  

10. <span data-ttu-id="6b184-164">按一下 **確定**直到結束所有對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6b184-164">Click **OK** until you have exited all dialog boxes.</span></span>  

### <a name="to-enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="6b184-165">啟用接收位置和啟動傳送埠</span><span class="sxs-lookup"><span data-stu-id="6b184-165">To enable the receive location and start the send port</span></span>  

1.  <span data-ttu-id="6b184-166">在 BizTalk Server 管理主控台中，按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="6b184-166">In the BizTalk Server Administration console, click **Receive Ports**.</span></span>  

2.  <span data-ttu-id="6b184-167">在 [詳細資料] 窗格中，以滑鼠右鍵按一下**MQIn**接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="6b184-167">In the details pane, right-click the **MQIn** receive location and click **Enable**.</span></span>  

3.  <span data-ttu-id="6b184-168">在 詳細資料 窗格中，以滑鼠右鍵按一下**MQOut**傳送埠，然後按一下 **開始。**</span><span class="sxs-lookup"><span data-stu-id="6b184-168">In the details pane, right-click the **MQOut** send port and click **Start.**</span></span>  

### <a name="to-create-the-folders-used-by-the-application"></a><span data-ttu-id="6b184-169">若要建立應用程式使用的資料夾</span><span class="sxs-lookup"><span data-stu-id="6b184-169">To create the folders used by the application</span></span>  

1.  <span data-ttu-id="6b184-170">在您**c:\\** 磁碟機，請建立名為"temp"如果不存在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b184-170">On your **C:\\** drive, create a folder named "temp" if it does not already exist.</span></span>  

2.  <span data-ttu-id="6b184-171">底下**C:\temp**目錄中，建立名為"Pickup"和"dropit 的資料夾"的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b184-171">Under the **C:\temp** directory, create folders named "Pickup" and "Dropit".</span></span>  

### <a name="building-and-deploying-this-sample"></a><span data-ttu-id="6b184-172">建置和部署此範例</span><span class="sxs-lookup"><span data-stu-id="6b184-172">Building and deploying this sample</span></span>  

1.  <span data-ttu-id="6b184-173">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="6b184-173">In a command window, navigate to the following folder:</span></span>  

     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration`  

2.  <span data-ttu-id="6b184-174">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6b184-174">Run the file Setup.bat, which performs the following actions:</span></span>  

    1.  <span data-ttu-id="6b184-175">為專案建立強式名稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="6b184-175">Creates a strong name key for the project.</span></span>  

    2.  <span data-ttu-id="6b184-176">編譯和部署協調流程專案。</span><span class="sxs-lookup"><span data-stu-id="6b184-176">Compiles and deploys the orchestration project.</span></span>  

    3.  <span data-ttu-id="6b184-177">使用 FILE 配接器建立傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="6b184-177">Creates a send port and a receive port with the File adapter.</span></span>  

### <a name="bind-and-start-the-orchestration"></a><span data-ttu-id="6b184-178">繫結並啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="6b184-178">Bind and start the Orchestration</span></span>  

1.  <span data-ttu-id="6b184-179">在 BizTalk Server 管理主控台中，依序展開**協調流程**資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b184-179">In the BizTalk Server Administration console, expand the **Orchestrations** folder.</span></span>  

2.  <span data-ttu-id="6b184-180">在 [詳細資料] 窗格中，以滑鼠右鍵按一下**MQSCorrelationSetOrchestration**協調流程，然後再按一下**繫結**。</span><span class="sxs-lookup"><span data-stu-id="6b184-180">In the details pane, right-click the **MQSCorrelationSetOrchestration** orchestration, and then click **Bind**.</span></span>  

3.  <span data-ttu-id="6b184-181">將協調流程連接埠繫結至下列傳送埠和接收位置：</span><span class="sxs-lookup"><span data-stu-id="6b184-181">Bind the orchestration ports to the following send ports and receive locations:</span></span>  

    |<span data-ttu-id="6b184-182">**協調流程連接埠**</span><span class="sxs-lookup"><span data-stu-id="6b184-182">**Orchestration Port**</span></span>|<span data-ttu-id="6b184-183">**傳送埠 / 接收位置**</span><span class="sxs-lookup"><span data-stu-id="6b184-183">**Messaging Port / Receive Location**</span></span>|  
    |----------------------------|--------------------------------------------|  
    |<span data-ttu-id="6b184-184">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="6b184-184">FileReceivePort</span></span>|<span data-ttu-id="6b184-185">MQSCorrelationSetOrchestration.FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="6b184-185">MQSCorrelationSetOrchestration.FileReceivePort</span></span>|  
    |<span data-ttu-id="6b184-186">MQSeriesResponseReceivePort</span><span class="sxs-lookup"><span data-stu-id="6b184-186">MQSeriesResponseReceivePort</span></span>|<span data-ttu-id="6b184-187">MQIn</span><span class="sxs-lookup"><span data-stu-id="6b184-187">MQIn</span></span>|  
    |<span data-ttu-id="6b184-188">MQSeriesRequestSendPort</span><span class="sxs-lookup"><span data-stu-id="6b184-188">MQSeriesRequestSendPort</span></span>|<span data-ttu-id="6b184-189">MQOut</span><span class="sxs-lookup"><span data-stu-id="6b184-189">MQOut</span></span>|  
    |<span data-ttu-id="6b184-190">FileSendPort</span><span class="sxs-lookup"><span data-stu-id="6b184-190">FileSendPort</span></span>|<span data-ttu-id="6b184-191">MQSCorrelationSetOrchestration.FileSendPort</span><span class="sxs-lookup"><span data-stu-id="6b184-191">MQSCorrelationSetOrchestration.FileSendPort</span></span>|  

4.  <span data-ttu-id="6b184-192">按一下 **主機**。</span><span class="sxs-lookup"><span data-stu-id="6b184-192">Click **Host**.</span></span>  

5.  <span data-ttu-id="6b184-193">在**主機**方塊中，選取**BizTalkServerApplication**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="6b184-193">In the **Host** box, select **BizTalkServerApplication**, and click **OK**.</span></span>  

6.  <span data-ttu-id="6b184-194">在 **傳送埠**，以滑鼠右鍵按一下**mqscorrelationsetorchestration.filesendport**，然後選取**啟動**。</span><span class="sxs-lookup"><span data-stu-id="6b184-194">In **Send Ports**, right-click **MQSCorrelationSetOrchestration.FileSendPort**, and then select **Start**.</span></span>  

7.  <span data-ttu-id="6b184-195">在 **接收位置**，以滑鼠右鍵按一下**mqscorrelationsetorchestration.filereceiveport** ，然後選取**啟用**。</span><span class="sxs-lookup"><span data-stu-id="6b184-195">In **Receive Locations**, right-click **MQSCorrelationSetOrchestration.FileReceivePort** and then select **Enable**.</span></span>  

8.  <span data-ttu-id="6b184-196">以滑鼠右鍵按一下協調流程，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="6b184-196">Right-click the orchestration and click **Start**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="6b184-197">啟動協調流程也會自動登錄協調流程。</span><span class="sxs-lookup"><span data-stu-id="6b184-197">Starting the orchestration also automatically enlists the orchestration.</span></span>  

### <a name="to-test-the-application"></a><span data-ttu-id="6b184-198">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="6b184-198">To test the application</span></span>  

1.  <span data-ttu-id="6b184-199">將檔案放**C:\Temp\Pickup**資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b184-199">Put a file into the **C:\Temp\Pickup** folder.</span></span>  

2.  <span data-ttu-id="6b184-200">檢查中的檔案**C:\Temp\Dropit**資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b184-200">Examine the file in the **C:\Temp\Dropit** folder.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="6b184-201">如果您停用**MQIn**接收位置，您可以檢查 WebSphere MQ Explorer 中的訊息，並查看已設定的訊息和相互關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="6b184-201">If you disable the **MQIn** receive location, you can examine the message in WebSphere MQ Explorer and see that the message and correlation identifiers are set.</span></span> <span data-ttu-id="6b184-202">若要這樣做，請啟動**WebSphere MQ Explorer** ，並檢查訊息置於**MQCorrelation**佇列。</span><span class="sxs-lookup"><span data-stu-id="6b184-202">To do this, launch the **WebSphere MQ Explorer** and examine the message placed in the **MQCorrelation** queue.</span></span> <span data-ttu-id="6b184-203">訊息和相互關聯識別碼會顯示在**識別碼**索引標籤**訊息屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6b184-203">The message and correlation identifiers are displayed on the **Identifiers** tab of the **Message properties** dialog box.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="6b184-204">在實際生產實例中，您會為每個傳送給 MQSeries 佇列的訊息指派唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="6b184-204">In a production scenario, you will want to assign a unique ID for each message that is sent to the MQSeries queue.</span></span> <span data-ttu-id="6b184-205">這可以藉由修改協調流程中的 [運算式] 圖形來完成。</span><span class="sxs-lookup"><span data-stu-id="6b184-205">This can be done by modifying the expression shape in the orchestration.</span></span> <span data-ttu-id="6b184-206">請變更下面幾行，將這些屬性設定為唯一的 24 位元組識別碼：</span><span class="sxs-lookup"><span data-stu-id="6b184-206">Change the following lines to set these properties to a unique 24 byte ID:</span></span>  
    >   
    >  <span data-ttu-id="6b184-207">MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = "111213141516171819202122232425262728293031323334";</span><span class="sxs-lookup"><span data-stu-id="6b184-207">MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = "111213141516171819202122232425262728293031323334";</span></span>  
    >   
    >  <span data-ttu-id="6b184-208">MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = "111213141516171819202122232425262728293031323334";</span><span class="sxs-lookup"><span data-stu-id="6b184-208">MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = "111213141516171819202122232425262728293031323334";</span></span>  
    >   
    >  <span data-ttu-id="6b184-209">如果您想要設定唯一的 24 位元組識別碼，如這些屬性，請參閱區段**來建立唯一的 24 位元組識別碼傳送至 MQSeries 的訊息**。</span><span class="sxs-lookup"><span data-stu-id="6b184-209">If you want to set a unique 24 byte ID for these properties see the section **To create a unique 24 byte ID for messages sent to MQSeries**.</span></span>  

### <a name="to-create-a-unique-24-byte-id-for-messages-sent-to-mqseries"></a><span data-ttu-id="6b184-210">若要為傳送至 MQSeries 的訊息建立唯一的 24 位元組識別碼</span><span class="sxs-lookup"><span data-stu-id="6b184-210">To create a unique 24 byte ID for messages sent to MQSeries</span></span>  

1. <span data-ttu-id="6b184-211">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中建立新的 C# 類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="6b184-211">Create a new C# class library project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  

2. <span data-ttu-id="6b184-212">將下列程式碼貼到該類別的 .cs 檔案中：</span><span class="sxs-lookup"><span data-stu-id="6b184-212">Paste the following code into the .cs file for the class:</span></span>  

   ```  
   using System;  
   using System.Collections.Generic;  
   using System.Text;  
   using System.Security.Cryptography;  

   namespace MQId  
   {[Serializable]  
       public class GetId  
       {  
           RNGCryptoServiceProvider randomCryptoString = new RNGCryptoServiceProvider();  

           public string getGuidstr()  
           {  
               byte[] newGuid = GetRandomData(24);  
               return ConvertToHex(newGuid);  
           }  

           private byte[] GetRandomData(int keySize)  
           {  
               byte[] randomData = new byte[keySize];  
               randomCryptoString.GetBytes(randomData);  
               return randomData;  
           }  

           private string ConvertToHex(byte[] key)  
           {  
               StringBuilder hexString = new StringBuilder();  
               for (int i = 0; i < key.Length; ++i)  
               {  
                   hexString.Append(String.Format("{0:X2}", key[i]));  
               }  
               return hexString.ToString();  
           }  
       }  
   }  
   ```  

3. <span data-ttu-id="6b184-213">指定**預設命名空間**的**MQId**並**組件名稱**的**GetId**的專案屬性**應用程式**頁面。</span><span class="sxs-lookup"><span data-stu-id="6b184-213">Specify a **Default namespace** of **MQId** and an **Assembly name** of **GetId** on the project properties **Application** page.</span></span>  

4. <span data-ttu-id="6b184-214">指定強式名稱金鑰檔簽署組件之專案屬性**簽署**頁面上，然後建置專案。</span><span class="sxs-lookup"><span data-stu-id="6b184-214">Specify a strong name key file to sign the assembly on the project properties **Signing** page and then build the project.</span></span>  

5. <span data-ttu-id="6b184-215">使用全域組件快取工具 (gacutil.exe) 編譯的組件載入到 GAC (gacutil /i \<*編譯的 dll 檔案的名稱*\>)。</span><span class="sxs-lookup"><span data-stu-id="6b184-215">Use the global assembly cache tool (gacutil.exe) to load the compiled assembly into the GAC (gacutil /i \<*name of compiled dll file*\>).</span></span>  

6. <span data-ttu-id="6b184-216">在此範例的 BizTalk 專案中新增 GetId 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="6b184-216">Add a reference to the GetId assembly in the BizTalk project for this sample.</span></span>  

7. <span data-ttu-id="6b184-217">將兩個變數新增至此範例中所使用的協調流程：</span><span class="sxs-lookup"><span data-stu-id="6b184-217">Add two variables to the orchestration used in this sample:</span></span>  


   | <span data-ttu-id="6b184-218">變數名稱 (識別項)</span><span class="sxs-lookup"><span data-stu-id="6b184-218">Variable name (Identifier)</span></span> |     <span data-ttu-id="6b184-219">類型</span><span class="sxs-lookup"><span data-stu-id="6b184-219">Type</span></span>      |
   |----------------------------|---------------|
   |           <span data-ttu-id="6b184-220">GetId</span><span class="sxs-lookup"><span data-stu-id="6b184-220">GetId</span></span>            |  <span data-ttu-id="6b184-221">MQId.GetId</span><span class="sxs-lookup"><span data-stu-id="6b184-221">MQId.GetId</span></span>   |
   |          <span data-ttu-id="6b184-222">strGuid</span><span class="sxs-lookup"><span data-stu-id="6b184-222">strGuid</span></span>           | <span data-ttu-id="6b184-223">System.String</span><span class="sxs-lookup"><span data-stu-id="6b184-223">System.String</span></span> |


8. <span data-ttu-id="6b184-224">將下列程式碼貼到此範例的協調流程中所使用的運算式圖形，此識別碼應覆寫現有的程式碼：</span><span class="sxs-lookup"><span data-stu-id="6b184-224">Paste the following code into the expression shape used in the orchestration for this sample, this code should overwrite the existing code:</span></span>  

   ```  
   GetId = new MQId.GetId();  
   strGuid = GetId.getGuidstr();  
   MQSeriesRequestSendMessageModified = MQSeriesRequestSendMessage;  
   MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = strGuid;  
   MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = strGuid;  
   ```  

9. <span data-ttu-id="6b184-225">在「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台」中停止並移除協調流程 (如果已部署的話)。</span><span class="sxs-lookup"><span data-stu-id="6b184-225">Stop and remove the orchestration in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console if it is already deployed.</span></span> <span data-ttu-id="6b184-226">然後請依照下列各節中的步驟**建置和部署此範例**，**繫結並啟動協調流程**並**測試應用程式**。</span><span class="sxs-lookup"><span data-stu-id="6b184-226">Then follow the steps in the sections **Building and deploying this sample**, **Bind and start the Orchestration** and **To test the application**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="6b184-227">使用此方法為傳送至 MQSeries 的訊息建立唯一的 24 位元組識別碼，並無法 100% 保證所有傳送的訊息都會有唯一的識別碼，而只能說訊息識別碼重複的可能性會很低。</span><span class="sxs-lookup"><span data-stu-id="6b184-227">Use of this method to create a unique 24 byte ID for messages sent to MQSeries does not 100% guarantee unique IDs for all messages sent but the probability of duplicate message IDs is very low.</span></span> <span data-ttu-id="6b184-228">如果企業需要 100% 保證沒有重複的訊息識別碼，您需要採用不同的自訂程式碼來確保此功能。</span><span class="sxs-lookup"><span data-stu-id="6b184-228">If business needs require a 100% guarantee that no message IDs are duplicated then you will need to employ different custom code to ensure this functionality.</span></span>  

## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="6b184-229">在此範例中使用的類別或方法</span><span class="sxs-lookup"><span data-stu-id="6b184-229">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="6b184-230">此範例沒有明確使用任何類別或方法。</span><span class="sxs-lookup"><span data-stu-id="6b184-230">This sample does not make explicit use of any classes or methods.</span></span>  

## <a name="see-also"></a><span data-ttu-id="6b184-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b184-231">See Also</span></span>  
 <span data-ttu-id="6b184-232">[使用要求-回覆相互關聯訊息](../core/correlating-messages-using-request-reply.md) </span><span class="sxs-lookup"><span data-stu-id="6b184-232">[Correlating Messages Using Request-Reply](../core/correlating-messages-using-request-reply.md) </span></span>  
 [<span data-ttu-id="6b184-233">MQSeries 配接器範例</span><span class="sxs-lookup"><span data-stu-id="6b184-233">MQSeries Adapter Samples</span></span>](../core/mqseries-adapter-samples.md)