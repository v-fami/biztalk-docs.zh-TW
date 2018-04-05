---
title: 步驟 4： 建立接收埠，以便接受 ADT 查詢訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, receive ports
ms.assetid: 8bef032f-5f43-4d36-b88f-ed81f27bb803
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 301215ea32b992516bfead3cd77ecdb009087bb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-the-receive-port-for-accepting-adt-query-messages"></a><span data-ttu-id="67403-102">步驟 4： 建立接收埠，以便接受 ADT 查詢訊息</span><span class="sxs-lookup"><span data-stu-id="67403-102">Step 4: Create the Receive Port for Accepting ADT Query Messages</span></span>
<span data-ttu-id="67403-103">建立接收埠以指定許可，放電，所傳送的連入查詢訊息的位置和傳送 (ADT) 系統。</span><span class="sxs-lookup"><span data-stu-id="67403-103">You create a receive port to specify the location for incoming query messages sent by the Admissions, Discharge, and Transfer (ADT) system.</span></span> <span data-ttu-id="67403-104">使用下列程序來建立接收埠，以便接受查詢 (QRY ^ Q01 訊息) 從 ADT 系統使用最少的較低層通訊協定 (MLLP) 配接器。</span><span class="sxs-lookup"><span data-stu-id="67403-104">Use the following procedure to create the receive port for accepting queries (QRY^Q01 messages) from the ADT system using the Minimal Lower Layer Protocol (MLLP) adapter.</span></span>  
  
## <a name="create-the-adtreceiveport-receive-port"></a><span data-ttu-id="67403-105">建立 ADT_ReceivePort 接收埠</span><span class="sxs-lookup"><span data-stu-id="67403-105">Create the ADT_ReceivePort receive port</span></span>  
  
1.  <span data-ttu-id="67403-106">開啟**BizTalk Server 管理**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk Application 1**。</span><span class="sxs-lookup"><span data-stu-id="67403-106">Open **BizTalk Server Administration**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
2.  <span data-ttu-id="67403-107">以滑鼠右鍵按一下**接收埠**，選取**新增**，然後選取**要求回應接收埠**。</span><span class="sxs-lookup"><span data-stu-id="67403-107">Right-click **Receive Ports**, select **New**, and then select **Request Response Receive Port**.</span></span>  
  
3.  <span data-ttu-id="67403-108">如**名稱**，輸入**ADT_ReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="67403-108">For the **Name**, enter **ADT_ReceivePort**.</span></span>  
  
4.  <span data-ttu-id="67403-109">選取**套用**連接埠，繫結，然後選取**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="67403-109">Select **Apply** to bind the port, and then select **Receive Locations**.</span></span>  
  
5.  <span data-ttu-id="67403-110">選取**新**。</span><span class="sxs-lookup"><span data-stu-id="67403-110">Select **New**.</span></span> 
  
6.  <span data-ttu-id="67403-111">如**名稱**，輸入**ADT_Receive**。</span><span class="sxs-lookup"><span data-stu-id="67403-111">For the **Name**, enter **ADT_Receive**.</span></span>  

7. <span data-ttu-id="67403-112">在**傳輸**區段中，選取**類型**，然後選取**MLLP**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="67403-112">In the **Transport** section, select **Type**, and then select **MLLP** from the drop-down list.</span></span>  
  
8. <span data-ttu-id="67403-113">選取 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="67403-113">Select **Configure**.</span></span> <span data-ttu-id="67403-114">在**MLLP 傳輸屬性**，設定下列項目，並選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="67403-114">In **MLLP Transport Properties**, configure the following, and then select **OK**.</span></span>  
  
    |<span data-ttu-id="67403-115">使用</span><span class="sxs-lookup"><span data-stu-id="67403-115">Use this</span></span>|<span data-ttu-id="67403-116">動作</span><span class="sxs-lookup"><span data-stu-id="67403-116">To do this</span></span>|  
    |---|---|  
    |<span data-ttu-id="67403-117">**連接重試時間 （秒）**</span><span class="sxs-lookup"><span data-stu-id="67403-117">**Connect retry time (sec)**</span></span>|<span data-ttu-id="67403-118">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67403-118">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="67403-119">若要嘗試重新連接已卸除或關閉連接之前等候的時間上限。</span><span class="sxs-lookup"><span data-stu-id="67403-119">The upper limit of time to wait before attempting to reconnect a dropped or closed connection.</span></span> <span data-ttu-id="67403-120">適用於**連線由起始**設**本機**。</span><span class="sxs-lookup"><span data-stu-id="67403-120">Applicable when **Connection Initiated by** is set to **Local**.</span></span><br/><br/><span data-ttu-id="67403-121">預設值為 20 秒。</span><span class="sxs-lookup"><span data-stu-id="67403-121">Default is 20 seconds.</span></span>|
    |<span data-ttu-id="67403-122">**所起始的連線**</span><span class="sxs-lookup"><span data-stu-id="67403-122">**Connection initiated by**</span></span>| <span data-ttu-id="67403-123">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67403-123">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="67403-124">輸入**本機**MLLP 的接收位置，以起始遠端的 LOB 伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="67403-124">Enter **Local** for the MLLP receive location to initiate the connection to a remote LOB server.</span></span> <span data-ttu-id="67403-125">這是新的選項。</span><span class="sxs-lookup"><span data-stu-id="67403-125">This is the new option.</span></span><br/><br/><span data-ttu-id="67403-126">輸入**遠端**MLLP 的接收位置，以繼續接聽來自遠端的 LOB 伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="67403-126">Enter **Remote** for the MLLP receive location to continue to listen for a connection from the remote LOB server.</span></span> <span data-ttu-id="67403-127">這是相容的預設選項。</span><span class="sxs-lookup"><span data-stu-id="67403-127">This is the backwards-compatible default option.</span></span><br/><br/><span data-ttu-id="67403-128">預設值為遠端。</span><span class="sxs-lookup"><span data-stu-id="67403-128">Default is Remote.</span></span>| 
    |<span data-ttu-id="67403-129">**連接名稱**</span><span class="sxs-lookup"><span data-stu-id="67403-129">**Connection Name**</span></span>|<span data-ttu-id="67403-130">輸入**ADT_ReceiveMLLP**。</span><span class="sxs-lookup"><span data-stu-id="67403-130">Enter **ADT_ReceiveMLLP**.</span></span>|  
    |<span data-ttu-id="67403-131">**主機名稱**</span><span class="sxs-lookup"><span data-stu-id="67403-131">**Host name**</span></span>|<span data-ttu-id="67403-132">特定[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]和較舊的版本。</span><span class="sxs-lookup"><span data-stu-id="67403-132">Specific to [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions.</span></span> <br/><br/><span data-ttu-id="67403-133">輸入**localhost**。</span><span class="sxs-lookup"><span data-stu-id="67403-133">Enter **localhost**.</span></span>|  
    |<span data-ttu-id="67403-134">**本機主機名稱**</span><span class="sxs-lookup"><span data-stu-id="67403-134">**Local Host name**</span></span>|<span data-ttu-id="67403-135">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67403-135">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="67403-136">輸入的 DNS 名稱或 IP 位址的本機[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67403-136">Enter the DNS name or IP address of the local [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="67403-137">您也可以輸入**localhost**。</span><span class="sxs-lookup"><span data-stu-id="67403-137">You can also enter **localhost**.</span></span>|  
    |<span data-ttu-id="67403-138">**[通訊埠]**</span><span class="sxs-lookup"><span data-stu-id="67403-138">**Port**</span></span>|<span data-ttu-id="67403-139">特定[!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)]和較舊的版本。</span><span class="sxs-lookup"><span data-stu-id="67403-139">Specific to [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] and older versions.</span></span> <br/><br/><span data-ttu-id="67403-140">設定為**22000**。</span><span class="sxs-lookup"><span data-stu-id="67403-140">Set to **22000**.</span></span>|  
    |<span data-ttu-id="67403-141">**本機連接埠**</span><span class="sxs-lookup"><span data-stu-id="67403-141">**Local Port**</span></span>|<span data-ttu-id="67403-142">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67403-142">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="67403-143">輸入 LocalHost 連接的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="67403-143">Enter the TCP port number for the LocalHost connection.</span></span> <span data-ttu-id="67403-144">時才適用**連線由起始**是**遠端**。</span><span class="sxs-lookup"><span data-stu-id="67403-144">Applicable only when **Connection Initiated by** is **Remote**.</span></span> <br/><br/><span data-ttu-id="67403-145">設定為**22000**。</span><span class="sxs-lookup"><span data-stu-id="67403-145">Set to **22000**.</span></span>|
    |<span data-ttu-id="67403-146">**遠端主機**</span><span class="sxs-lookup"><span data-stu-id="67403-146">**Remote Host**</span></span>|<span data-ttu-id="67403-147">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67403-147">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="67403-148">輸入的 DNS 名稱或遠端的 LOB 伺服器 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="67403-148">Enter the DNS name or IP address of the remote LOB server.</span></span> <span data-ttu-id="67403-149">適用於**連線由起始**設**本機**。</span><span class="sxs-lookup"><span data-stu-id="67403-149">Applicable when **Connection Initiated by** is set to **Local**.</span></span>|  
    |<span data-ttu-id="67403-150">**遠端連接埠**</span><span class="sxs-lookup"><span data-stu-id="67403-150">**Remote Port**</span></span>|<span data-ttu-id="67403-151">新開頭[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67403-151">New starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)].</span></span> <br/><br/><span data-ttu-id="67403-152">輸入遠端主機連接的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="67403-152">Enter the TCP port number for the remote host connection.</span></span> <span data-ttu-id="67403-153">適用於**連線由起始**設**本機**。</span><span class="sxs-lookup"><span data-stu-id="67403-153">Applicable when **Connection Initiated by** is set to **Local**.</span></span><br/><br/><span data-ttu-id="67403-154">設定為**22000**。</span><span class="sxs-lookup"><span data-stu-id="67403-154">Set to **22000**.</span></span>|  

9. <span data-ttu-id="67403-155">設定**接收處理常式**至**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="67403-155">Set the **Receive Handler** to **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="67403-156">設定**接收管線**至**BTAHL72XPipelines.BTAHL72XReceivePipeline**。</span><span class="sxs-lookup"><span data-stu-id="67403-156">Set the **Receive Pipeline** to **BTAHL72XPipelines.BTAHL72XReceivePipeline**.</span></span>  

11. <span data-ttu-id="67403-157">設定**傳送管線**至**PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="67403-157">Set the **Send pipeline** to **PassThruTransmit**.</span></span>
  
11. <span data-ttu-id="67403-158">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="67403-158">Select **OK** to save your changes.</span></span>  
  
12. <span data-ttu-id="67403-159">啟用您以滑鼠右鍵按一下它，建立接收位置，然後選取**啟用**。</span><span class="sxs-lookup"><span data-stu-id="67403-159">Enable the receive location you just created by right-clicking it, and then select **Enable**.</span></span>  

## <a name="next-step"></a><span data-ttu-id="67403-160">下一步</span><span class="sxs-lookup"><span data-stu-id="67403-160">Next step</span></span>  
[<span data-ttu-id="67403-161">步驟 5： 建立接收埠，以便接受他的訊息</span><span class="sxs-lookup"><span data-stu-id="67403-161">Step 5: Create the Receive Port for Accepting HIS Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)