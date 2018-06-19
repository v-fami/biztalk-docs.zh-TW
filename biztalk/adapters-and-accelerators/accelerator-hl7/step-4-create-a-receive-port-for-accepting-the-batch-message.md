---
title: 步驟 4： 建立接收埠，以便接受批次訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a37eb334-c4ae-40d1-a433-bf0ab39c0765
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56d1aa54639263e6741c6df89c3888b9b4120515
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207606"
---
# <a name="step-4-create-a-receive-port-for-accepting-the-batch-message"></a><span data-ttu-id="81cdd-102">步驟 4： 建立接收埠，以便接受批次訊息</span><span class="sxs-lookup"><span data-stu-id="81cdd-102">Step 4: Create a Receive Port for Accepting the Batch Message</span></span>
<span data-ttu-id="81cdd-103">在此步驟中，您可以建立並設定連接埠來接收內送的批次。</span><span class="sxs-lookup"><span data-stu-id="81cdd-103">In this step, you create and configure a port to receive the incoming batch.</span></span>  
  
 <span data-ttu-id="81cdd-104">建立要求-回應 （雙向） 接收埠，因為此案例包括產生應用程式接受的批次中的個別訊息的通知。</span><span class="sxs-lookup"><span data-stu-id="81cdd-104">You create a request-response (two-way) receive port, because the scenario includes the generation of application-accept acknowledgments for the individual messages in the batch.</span></span> <span data-ttu-id="81cdd-105">在雙向模式中，MLLP 的接收配接器不會接受新的內送訊息直到接收管線產生通知 (ACK) 的前一個訊息。</span><span class="sxs-lookup"><span data-stu-id="81cdd-105">In two-way mode, the MLLP receive adapter will not accept a new incoming message until the receive pipeline has generated the acknowledgment (ACK) for the previous message.</span></span>  
  
## <a name="create-the-receive-port-for-accepting-the-batch-message"></a><span data-ttu-id="81cdd-106">建立接收埠，以便接受批次訊息</span><span class="sxs-lookup"><span data-stu-id="81cdd-106">Create the receive port for accepting the batch message</span></span>  
  
1.  <span data-ttu-id="81cdd-107">開啟**BizTalk Server 管理**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk Application 1**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-107">Open **BizTalk Server Administration**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="81cdd-108">BizTalk Server 管理主控台也可以開啟從 Visual Studio 中依序按一下**BizTalk Server 管理**中**工具**功能表。</span><span class="sxs-lookup"><span data-stu-id="81cdd-108">The BizTalk Server Administration Console can also be opened from within Visual Studio by clicking **BizTalk Server Administration** in the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="81cdd-109">以滑鼠右鍵按一下**接收埠**，選取**新增**，然後選取**要求回應接收埠**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-109">Right-click **Receive Ports**, select **New**, and then select **Request Response Receive Port**.</span></span>  

3.  <span data-ttu-id="81cdd-110">如**名稱**，輸入**Tutorial_2WayReceive**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-110">For the **Name**, enter **Tutorial_2WayReceive**.</span></span>  

4.  <span data-ttu-id="81cdd-111">選取**套用**連接埠，繫結，然後選取**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-111">Select **Apply** to bind the port, and then select **Receive Locations**.</span></span>  
  
5.  <span data-ttu-id="81cdd-112">選取**新**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-112">Select **New**.</span></span>  

6.  <span data-ttu-id="81cdd-113">如**名稱**，輸入**Tutorial_2WayReceive**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-113">For the **Name**, enter **Tutorial_2WayReceive**.</span></span>

7. <span data-ttu-id="81cdd-114">在**傳輸**區段中，選取**類型**，然後選取**MLLP**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="81cdd-114">In the **Transport** section, select **Type**, and then select **MLLP** from the drop-down list.</span></span>  
  
8. <span data-ttu-id="81cdd-115">選取 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-115">Select **Configure**.</span></span> <span data-ttu-id="81cdd-116">在**MLLP 傳輸屬性**，設定下列項目，並選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-116">In **MLLP Transport Properties**, configure the following, and then select **OK**.</span></span>  

    |<span data-ttu-id="81cdd-117">使用</span><span class="sxs-lookup"><span data-stu-id="81cdd-117">Use this</span></span>|<span data-ttu-id="81cdd-118">動作</span><span class="sxs-lookup"><span data-stu-id="81cdd-118">To do this</span></span>|  
    |---|---|  
    |<span data-ttu-id="81cdd-119">**連接重試時間 （秒）**</span><span class="sxs-lookup"><span data-stu-id="81cdd-119">**Connect retry time (sec)**</span></span>|<span data-ttu-id="81cdd-120">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="81cdd-120">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="81cdd-121">若要嘗試重新連接已卸除或關閉連接之前等候的時間上限。</span><span class="sxs-lookup"><span data-stu-id="81cdd-121">The upper limit of time to wait before attempting to reconnect a dropped or closed connection.</span></span> <span data-ttu-id="81cdd-122">適用於**連線由起始**設**本機**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-122">Applicable when **Connection Initiated by** is set to **Local**.</span></span><br/><br/><span data-ttu-id="81cdd-123">預設值為 20 秒。</span><span class="sxs-lookup"><span data-stu-id="81cdd-123">Default is 20 seconds.</span></span>|
    |<span data-ttu-id="81cdd-124">**所起始的連線**</span><span class="sxs-lookup"><span data-stu-id="81cdd-124">**Connection initiated by**</span></span>| <span data-ttu-id="81cdd-125">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="81cdd-125">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="81cdd-126">輸入**本機**MLLP 的接收位置，以起始遠端的 LOB 伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="81cdd-126">Enter **Local** for the MLLP receive location to initiate the connection to a remote LOB server.</span></span> <span data-ttu-id="81cdd-127">這是新的選項。</span><span class="sxs-lookup"><span data-stu-id="81cdd-127">This is the new option.</span></span><br/><br/><span data-ttu-id="81cdd-128">輸入**遠端**MLLP 的接收位置，以繼續接聽來自遠端的 LOB 伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="81cdd-128">Enter **Remote** for the MLLP receive location to continue to listen for a connection from the remote LOB server.</span></span> <span data-ttu-id="81cdd-129">這是相容的預設選項。</span><span class="sxs-lookup"><span data-stu-id="81cdd-129">This is the backwards-compatible default option.</span></span><br/><br/><span data-ttu-id="81cdd-130">預設值為遠端。</span><span class="sxs-lookup"><span data-stu-id="81cdd-130">Default is Remote.</span></span>| 
    |<span data-ttu-id="81cdd-131">**連接名稱**</span><span class="sxs-lookup"><span data-stu-id="81cdd-131">**Connection Name**</span></span>|<span data-ttu-id="81cdd-132">輸入**2Way**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-132">Enter **2Way**.</span></span>|  
    |<span data-ttu-id="81cdd-133">**主機名稱**</span><span class="sxs-lookup"><span data-stu-id="81cdd-133">**Host name**</span></span>|<span data-ttu-id="81cdd-134">特定[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]和較舊的版本。</span><span class="sxs-lookup"><span data-stu-id="81cdd-134">Specific to [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions.</span></span> <br/><br/><span data-ttu-id="81cdd-135">輸入**localhost**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-135">Enter **localhost**.</span></span>|  
    |<span data-ttu-id="81cdd-136">**本機主機名稱**</span><span class="sxs-lookup"><span data-stu-id="81cdd-136">**Local Host name**</span></span>|<span data-ttu-id="81cdd-137">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="81cdd-137">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="81cdd-138">輸入的 DNS 名稱或 IP 位址的本機[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="81cdd-138">Enter the DNS name or IP address of the local [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="81cdd-139">您也可以輸入**localhost**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-139">You can also enter **localhost**.</span></span>|  
    |<span data-ttu-id="81cdd-140">**[通訊埠]**</span><span class="sxs-lookup"><span data-stu-id="81cdd-140">**Port**</span></span>|<span data-ttu-id="81cdd-141">特定[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]和較舊的版本。</span><span class="sxs-lookup"><span data-stu-id="81cdd-141">Specific to [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions.</span></span> <br/><br/><span data-ttu-id="81cdd-142">設定為**21000**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-142">Set to **21000**.</span></span>|  
    |<span data-ttu-id="81cdd-143">**本機連接埠**</span><span class="sxs-lookup"><span data-stu-id="81cdd-143">**Local Port**</span></span>|<span data-ttu-id="81cdd-144">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="81cdd-144">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="81cdd-145">輸入 LocalHost 連接的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="81cdd-145">Enter the TCP port number for the LocalHost connection.</span></span> <span data-ttu-id="81cdd-146">時才適用**連線由起始**是**遠端**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-146">Applicable only when **Connection Initiated by** is **Remote**.</span></span> <br/><br/><span data-ttu-id="81cdd-147">設定為**21000**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-147">Set to **21000**.</span></span>|
    |<span data-ttu-id="81cdd-148">**遠端主機**</span><span class="sxs-lookup"><span data-stu-id="81cdd-148">**Remote Host**</span></span>|<span data-ttu-id="81cdd-149">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="81cdd-149">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="81cdd-150">輸入的 DNS 名稱或遠端的 LOB 伺服器 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="81cdd-150">Enter the DNS name or IP address of the remote LOB server.</span></span> <span data-ttu-id="81cdd-151">適用於**連線由起始**設**本機**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-151">Applicable when **Connection Initiated by** is set to **Local**.</span></span>|  
    |<span data-ttu-id="81cdd-152">**遠端連接埠**</span><span class="sxs-lookup"><span data-stu-id="81cdd-152">**Remote Port**</span></span>|<span data-ttu-id="81cdd-153">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="81cdd-153">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="81cdd-154">輸入遠端主機連接的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="81cdd-154">Enter the TCP port number for the remote host connection.</span></span> <span data-ttu-id="81cdd-155">適用於**連線由起始**設**本機**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-155">Applicable when **Connection Initiated by** is set to **Local**.</span></span><br/><br/><span data-ttu-id="81cdd-156">設定為**21000**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-156">Set to **21000**.</span></span>|  

9. <span data-ttu-id="81cdd-157">在接收位置屬性中，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="81cdd-157">In the Receive Location properties, select the following:</span></span>  
  
    |<span data-ttu-id="81cdd-158">使用</span><span class="sxs-lookup"><span data-stu-id="81cdd-158">Use this</span></span>|<span data-ttu-id="81cdd-159">動作</span><span class="sxs-lookup"><span data-stu-id="81cdd-159">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="81cdd-160">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="81cdd-160">**Receive Handler**</span></span>|<span data-ttu-id="81cdd-161">選取**BizTalkServerApplication**從下拉式清單</span><span class="sxs-lookup"><span data-stu-id="81cdd-161">Select **BizTalkServerApplication** from the drop-down list</span></span>|  
    |<span data-ttu-id="81cdd-162">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="81cdd-162">**Receive Pipeline**</span></span>|<span data-ttu-id="81cdd-163">選取**BTAHL72XPipelines.BTAHL72XReceivePipeline**</span><span class="sxs-lookup"><span data-stu-id="81cdd-163">Select **BTAHL72XPipelines.BTAHL72XReceivePipeline**</span></span>|  
    |<span data-ttu-id="81cdd-164">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="81cdd-164">**Send Pipeline**</span></span>|<span data-ttu-id="81cdd-165">選取**BTAHL72XPipelines.BTAHL72XSendPipeline**</span><span class="sxs-lookup"><span data-stu-id="81cdd-165">Select **BTAHL72XPipelines.BTAHL72XSendPipeline**</span></span>|  

11. <span data-ttu-id="81cdd-166">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="81cdd-166">Select **OK** to save your changes.</span></span>  
  
12. <span data-ttu-id="81cdd-167">啟用您以滑鼠右鍵按一下它，建立接收位置，然後選取**啟用**。</span><span class="sxs-lookup"><span data-stu-id="81cdd-167">Enable the receive location you just created by right-clicking it, and then select **Enable**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="81cdd-168">下一步</span><span class="sxs-lookup"><span data-stu-id="81cdd-168">Next step</span></span>
[<span data-ttu-id="81cdd-169">步驟 5： 建立傳送埠將訊息傳遞</span><span class="sxs-lookup"><span data-stu-id="81cdd-169">Step 5: Create a Send Port to Deliver Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-a-send-port-to-deliver-messages.md)