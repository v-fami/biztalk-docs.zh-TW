---
title: "步驟 4： 建立接收埠，以便接受 ADT ^ ADT 系統使用 MLLP 配接器從 A03 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 2015-12-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports
- end-to-end tutorial, receive ports
- creating, receive ports
ms.assetid: 3c4192d5-d011-48b0-a3f9-47c5225780ee
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 865675e12609beea4c909d19a74d3e0ec4f38715
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-the-receive-port-for-accepting-adta03-messages-from-adt-systems-using-the-mllp-adapter"></a><span data-ttu-id="d1105-102">步驟 4： 建立接收埠，以便接受 ADT ^ A03 訊息從 ADT 系統使用 MLLP 配接器</span><span class="sxs-lookup"><span data-stu-id="d1105-102">Step 4: Create the Receive Port for Accepting ADT^A03 Messages from ADT Systems Using the MLLP Adapter</span></span>
<span data-ttu-id="d1105-103">您可以使用的接收埠來指定內送訊息的接收位置。</span><span class="sxs-lookup"><span data-stu-id="d1105-103">You use the receive port to specify the receive location for incoming messages.</span></span> <span data-ttu-id="d1105-104">使用下列程序來建立接收埠，以便接受 ADT ^ A03 ADT 使用從系統 MLLP 配接器的訊息。</span><span class="sxs-lookup"><span data-stu-id="d1105-104">Use the following procedure to create the receive port for accepting ADT^A03 messages from the ADT System using the MLLP adapter.</span></span>  
  
## <a name="create-the-receive-port"></a><span data-ttu-id="d1105-105">建立接收埠</span><span class="sxs-lookup"><span data-stu-id="d1105-105">Create the receive port</span></span>  
  
1.  <span data-ttu-id="d1105-106">開啟**BizTalk Server 管理**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk Application 1**。</span><span class="sxs-lookup"><span data-stu-id="d1105-106">Open **BizTalk Server Administration**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1105-107">BizTalk Server 管理主控台也可以開啟從 Visual Studio 中依序按一下**BizTalk Server 管理**中**工具**功能表。</span><span class="sxs-lookup"><span data-stu-id="d1105-107">The BizTalk Server Administration Console can also be opened from within Visual Studio by clicking **BizTalk Server Administration** in the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="d1105-108">以滑鼠右鍵按一下**接收埠**，選取**新增**，然後選取**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="d1105-108">Right-click **Receive Ports**, select **New**, and then select **One-way Receive Port**.</span></span>  
  
3.  <span data-ttu-id="d1105-109">如**名稱**，輸入**Tutorial_1WayReceive**。</span><span class="sxs-lookup"><span data-stu-id="d1105-109">For the **Name**, enter **Tutorial_1WayReceive**.</span></span>  
  
4.  <span data-ttu-id="d1105-110">選取**套用**連接埠，繫結，然後選取**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="d1105-110">Select **Apply** to bind the port, and then select **Receive Locations**.</span></span>  
  
5.  <span data-ttu-id="d1105-111">選取**新**。</span><span class="sxs-lookup"><span data-stu-id="d1105-111">Select **New**.</span></span>  
  
6.  <span data-ttu-id="d1105-112">如**名稱**，輸入**Tutorial_MLLPReceive**。</span><span class="sxs-lookup"><span data-stu-id="d1105-112">For the **Name**, enter **Tutorial_MLLPReceive**.</span></span>  
  
7. <span data-ttu-id="d1105-113">在**傳輸**區段中，選取**類型**，然後選取**MLLP**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d1105-113">In the **Transport** section, select **Type**, and then select **MLLP** from the drop-down list.</span></span>  
  
8. <span data-ttu-id="d1105-114">選取 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="d1105-114">Select **Configure**.</span></span> <span data-ttu-id="d1105-115">在**MLLP 傳輸屬性**，設定下列項目，並選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="d1105-115">In **MLLP Transport Properties**, configure the following, and then select **OK**.</span></span>  
  
    |<span data-ttu-id="d1105-116">使用</span><span class="sxs-lookup"><span data-stu-id="d1105-116">Use this</span></span>|<span data-ttu-id="d1105-117">動作</span><span class="sxs-lookup"><span data-stu-id="d1105-117">To do this</span></span>|  
    |---|---|  
    |<span data-ttu-id="d1105-118">**連接重試時間 （秒）**</span><span class="sxs-lookup"><span data-stu-id="d1105-118">**Connect retry time (sec)**</span></span>|<span data-ttu-id="d1105-119">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1105-119">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="d1105-120">若要嘗試重新連接已卸除或關閉連接之前等候的時間上限。</span><span class="sxs-lookup"><span data-stu-id="d1105-120">The upper limit of time to wait before attempting to reconnect a dropped or closed connection.</span></span> <span data-ttu-id="d1105-121">適用於**連線由起始**設**本機**。</span><span class="sxs-lookup"><span data-stu-id="d1105-121">Applicable when **Connection Initiated by** is set to **Local**.</span></span><br/><br/><span data-ttu-id="d1105-122">預設值為 20 秒。</span><span class="sxs-lookup"><span data-stu-id="d1105-122">Default is 20 seconds.</span></span>|
    |<span data-ttu-id="d1105-123">**所起始的連線**</span><span class="sxs-lookup"><span data-stu-id="d1105-123">**Connection initiated by**</span></span>| <span data-ttu-id="d1105-124">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1105-124">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="d1105-125">輸入**本機**MLLP 的接收位置，以起始遠端的 LOB 伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="d1105-125">Enter **Local** for the MLLP receive location to initiate the connection to a remote LOB server.</span></span> <span data-ttu-id="d1105-126">這是新的選項。</span><span class="sxs-lookup"><span data-stu-id="d1105-126">This is the new option.</span></span><br/><br/><span data-ttu-id="d1105-127">輸入**遠端**MLLP 的接收位置，以繼續接聽來自遠端的 LOB 伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="d1105-127">Enter **Remote** for the MLLP receive location to continue to listen for a connection from the remote LOB server.</span></span> <span data-ttu-id="d1105-128">這是相容的預設選項。</span><span class="sxs-lookup"><span data-stu-id="d1105-128">This is the backwards-compatible default option.</span></span><br/><br/><span data-ttu-id="d1105-129">預設值為遠端。</span><span class="sxs-lookup"><span data-stu-id="d1105-129">Default is Remote.</span></span>| 
    |<span data-ttu-id="d1105-130">**連接名稱**</span><span class="sxs-lookup"><span data-stu-id="d1105-130">**Connection Name**</span></span>|<span data-ttu-id="d1105-131">輸入**1Way**。</span><span class="sxs-lookup"><span data-stu-id="d1105-131">Enter **1Way**.</span></span>|  
    |<span data-ttu-id="d1105-132">**主機名稱**</span><span class="sxs-lookup"><span data-stu-id="d1105-132">**Host name**</span></span>|<span data-ttu-id="d1105-133">特定[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]和較舊的版本。</span><span class="sxs-lookup"><span data-stu-id="d1105-133">Specific to [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions.</span></span> <br/><br/><span data-ttu-id="d1105-134">輸入**localhost**。</span><span class="sxs-lookup"><span data-stu-id="d1105-134">Enter **localhost**.</span></span>|  
    |<span data-ttu-id="d1105-135">**本機主機名稱**</span><span class="sxs-lookup"><span data-stu-id="d1105-135">**Local Host name**</span></span>|<span data-ttu-id="d1105-136">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1105-136">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="d1105-137">輸入的 DNS 名稱或 IP 位址的本機[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1105-137">Enter the DNS name or IP address of the local [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d1105-138">您也可以輸入**localhost**。</span><span class="sxs-lookup"><span data-stu-id="d1105-138">You can also enter **localhost**.</span></span>|  
    |<span data-ttu-id="d1105-139">**[通訊埠]**</span><span class="sxs-lookup"><span data-stu-id="d1105-139">**Port**</span></span>|<span data-ttu-id="d1105-140">特定[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]和較舊的版本。</span><span class="sxs-lookup"><span data-stu-id="d1105-140">Specific to [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions.</span></span> <br/><br/><span data-ttu-id="d1105-141">預設值是**11000**。</span><span class="sxs-lookup"><span data-stu-id="d1105-141">Default is **11000**.</span></span>|  
    |<span data-ttu-id="d1105-142">**本機連接埠**</span><span class="sxs-lookup"><span data-stu-id="d1105-142">**Local Port**</span></span>|<span data-ttu-id="d1105-143">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1105-143">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="d1105-144">輸入 LocalHost 連接的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="d1105-144">Enter the TCP port number for the LocalHost connection.</span></span> <span data-ttu-id="d1105-145">時才適用**連線由起始**是**遠端**。</span><span class="sxs-lookup"><span data-stu-id="d1105-145">Applicable only when **Connection Initiated by** is **Remote**.</span></span> <br/><br/><span data-ttu-id="d1105-146">預設值是**11000**。</span><span class="sxs-lookup"><span data-stu-id="d1105-146">Default is **11000**.</span></span>|
    |<span data-ttu-id="d1105-147">**遠端主機**</span><span class="sxs-lookup"><span data-stu-id="d1105-147">**Remote Host**</span></span>|<span data-ttu-id="d1105-148">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1105-148">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="d1105-149">輸入的 DNS 名稱或遠端的 LOB 伺服器 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="d1105-149">Enter the DNS name or IP address of the remote LOB server.</span></span> <span data-ttu-id="d1105-150">適用於**連線由起始**設**本機**。</span><span class="sxs-lookup"><span data-stu-id="d1105-150">Applicable when **Connection Initiated by** is set to **Local**.</span></span>|  
    |<span data-ttu-id="d1105-151">**遠端連接埠**</span><span class="sxs-lookup"><span data-stu-id="d1105-151">**Remote Port**</span></span>|<span data-ttu-id="d1105-152">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1105-152">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="d1105-153">輸入遠端主機連接的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="d1105-153">Enter the TCP port number for the remote host connection.</span></span> <span data-ttu-id="d1105-154">適用於**連線由起始**設**本機**。</span><span class="sxs-lookup"><span data-stu-id="d1105-154">Applicable when **Connection Initiated by** is set to **Local**.</span></span>|  

9. <span data-ttu-id="d1105-155">設定**接收處理常式**至**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="d1105-155">Set the **Receive Handler** to **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="d1105-156">設定**接收管線**至**BTAHL72XPipelines.BTAHL72XReceivePipeline**。</span><span class="sxs-lookup"><span data-stu-id="d1105-156">Set the **Receive Pipeline** to **BTAHL72XPipelines.BTAHL72XReceivePipeline**.</span></span>  
  
11. <span data-ttu-id="d1105-157">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="d1105-157">Select **OK** to save your changes.</span></span>  
  
12. <span data-ttu-id="d1105-158">啟用您以滑鼠右鍵按一下它，建立接收位置，然後選取**啟用**。</span><span class="sxs-lookup"><span data-stu-id="d1105-158">Enable the receive location you just created by right-clicking it, and then select **Enable**.</span></span>  

## <a name="next-step"></a><span data-ttu-id="d1105-159">下一步</span><span class="sxs-lookup"><span data-stu-id="d1105-159">Next step</span></span>  
[<span data-ttu-id="d1105-160">步驟 5： 建立傳送埠，以便將通知傳送到使用 File 配接器 ADT 系統</span><span class="sxs-lookup"><span data-stu-id="d1105-160">Step 5: Create a Send Port to Deliver Acknowledgments to the ADT System Using the File Adapter</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-send-port-to-deliver-acknowledgments-to-adt-system-using-file.md)