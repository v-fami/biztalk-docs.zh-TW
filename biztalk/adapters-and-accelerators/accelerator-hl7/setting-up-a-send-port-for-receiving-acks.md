---
title: 設定傳送埠來接收 Ack |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, acknowledgements
- creating, send ports
- acknowledgements, send ports
- send ports, creating
ms.assetid: bb683e72-36e2-4a8f-acc2-8b37ed23746f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f70be6d66d0ba8aa3385760bfc17b4b19f50351a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984743"
---
# <a name="setting-up-a-send-port-for-receiving-acks"></a><span data-ttu-id="f9a7e-102">設定傳送埠來接收 Ack</span><span class="sxs-lookup"><span data-stu-id="f9a7e-102">Setting Up a Send Port for Receiving ACKs</span></span>
<span data-ttu-id="f9a7e-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 可以在單向傳送埠上接收通知 (ACK)。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) can receive acknowledgments (ACK) on a one-way send port.</span></span> <span data-ttu-id="f9a7e-104">當您設定新的單向傳送埠來接收 Ack，相同的連接上時，您必須建立關聯的傳送埠為單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-104">When you set up a new one-way send port for receiving ACKs on the same connection, you must associate that send port with a one-way receive port.</span></span>  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f9a7e-105"> 安裝程式會建立單向接收埠 (稱為**TwoWayAckReceivePort**) 和接收位置 (稱為**TwoWayAckReceiveLocation**)。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-105"> setup creates a one-way receive port (called **TwoWayAckReceivePort**) and receive location (called **TwoWayAckReceiveLocation**).</span></span> <span data-ttu-id="f9a7e-106">接收位置會使用最少的較低層通訊協定 (MLLP) 傳輸類型、 具有 URI 為"127.0.0.1:65535 」，並且使用**BTAHL72XReceivePipeline**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-106">The receive location uses the Minimal Lower Layer Protocol (MLLP) transport type, has a URI of "127.0.0.1:65535", and uses the **BTAHL72XReceivePipeline**.</span></span> <span data-ttu-id="f9a7e-107">這些是用於接收所需的設定和處理收到的訊息通知所送出[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送配接器，在雙向的模式。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-107">These are the settings required for receiving and processing an ACK received against a message sent out by the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] send adapter, in two-way mode.</span></span> <span data-ttu-id="f9a7e-108">此接收位置不應該刪除或用於任何其他用途。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-108">This receive location should not be deleted or used for any other purposes.</span></span> <span data-ttu-id="f9a7e-109">永遠不會將資料傳送至這個接收位置。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-109">Never send data to this receive location.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f9a7e-110"> 可讓這個接收位置的預設值。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-110"> enables this receive location by default.</span></span>  
  
 <span data-ttu-id="f9a7e-111">**TwoWayAckReceiveLocation**，這[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝精靈會建立，會使用**BizTalkServerApplication**為接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-111">**TwoWayAckReceiveLocation**, which the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Setup Wizard creates, uses the **BizTalkServerApplication** as the receive handler.</span></span> <span data-ttu-id="f9a7e-112">不過，如果您選擇建立新的主機，並作為 MLLP 的接收處理常式，則必須執行下列命令來建立新**TwoWayAckReceiveLocation**:</span><span class="sxs-lookup"><span data-stu-id="f9a7e-112">However, if you choose to create a new host and use it as the receive handler for MLLP, then you must do the following to create a new **TwoWayAckReceiveLocation**:</span></span>  
  
1.  <span data-ttu-id="f9a7e-113">建立單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-113">Create a one-way receive port.</span></span>  
  
2.  <span data-ttu-id="f9a7e-114">建立單向 MLLP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-114">Create a one-way MLLP receive location.</span></span>  
  
3.  <span data-ttu-id="f9a7e-115">指定 MLLP 傳輸屬性的適當值。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-115">Specify the appropriate values for the MLLP transport properties.</span></span>  
  
4.  <span data-ttu-id="f9a7e-116">指定適當的接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-116">Specify the appropriate receive handler.</span></span>  
  
5.  <span data-ttu-id="f9a7e-117">啟用接收位置。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-117">Enable the receive location.</span></span>  
  
### <a name="to-create-a-send-port-enabled-to-receive-an-ack-on-the-same-socket"></a><span data-ttu-id="f9a7e-118">若要建立傳送埠可接收相同的通訊端上的通知</span><span class="sxs-lookup"><span data-stu-id="f9a7e-118">To create a send port enabled to receive an ACK on the same socket</span></span>  
  
1.  <span data-ttu-id="f9a7e-119">開啟 BizTalk 管理主控台，然後展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk應用程式 1**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-119">Open the BizTalk Administration Console, and then expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1**.</span></span> <span data-ttu-id="f9a7e-120">以滑鼠右鍵按一下**傳送埠**，指向 [新增]，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-120">Right-click **Send Ports**, point to New, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="f9a7e-121">在 **名稱**方塊中，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-121">In the **Name** box, type the name of the send port.</span></span>  
  
3.  <span data-ttu-id="f9a7e-122">在 [**傳輸**] 區段中，如**型別**，選取**MLLP**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-122">In the **Transport** section, for **Type**, select **MLLP**.</span></span>  
  
4.  <span data-ttu-id="f9a7e-123">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-123">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="f9a7e-124">在 [MLLP 傳輸屬性] 對話方塊中，輸入連線名稱和主機 (例如**localhost**)。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-124">In the MLLP Transport Properties dialog box, type a connection name and host (for instance, **localhost**).</span></span>  
  
6.  <span data-ttu-id="f9a7e-125">針對**請求回應啟用**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-125">For **Solicit Response Enabled**, select **Yes**.</span></span> <span data-ttu-id="f9a7e-126">離開**提交接收位置 (URI) 通知**空白，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-126">Leave **Submit Receive Location (URI) for ACK** blank, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9a7e-127">當您離開**送出的接收位置**空白，BTAHL7 URI 就會針對輸入預設**TwoWayAckReceiveLocation**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-127">When you leave **Submit Receive Location** blank, BTAHL7 enters the URI for the default **TwoWayAckReceiveLocation**.</span></span> <span data-ttu-id="f9a7e-128">您可以確認，之後按一下 **[確定]** 步驟 6 中，依序按一下**組態**一次。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-128">You can verify that after clicking **OK** in step 6, by clicking **Configuration** again.</span></span> <span data-ttu-id="f9a7e-129">URI **TwoWayAckReceiveLocation** (127.0.0.1:65535) 將會進入**提交接收位置 (URI) 通知**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-129">The URI for **TwoWayAckReceiveLocation** (127.0.0.1:65535) will be entered in **Submit Receive Location (URI) for ACK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9a7e-130">您必須建立傳送埠以接收通知訂閱，或通知中會顯示為已暫停的狀態，因為找不到任何訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-130">You must create a send port to subscribe to the ACK received, or the ACK will be seen in a suspended state, because no subscriptions were found.</span></span> <span data-ttu-id="f9a7e-131">若要訂閱的傳送埠收到 ACK，使用篩選器，例如**BTS。MessageType = = \< *MessageType* \>** 和**BTS。ReceivePortName = = \< *ReceivePort*\>**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-131">To subscribe to the ACK received by the send port, use filters, for example, **BTS.MessageType == \<*MessageType*\>** and **BTS.ReceivePortName == \<*ReceivePort*\>**.</span></span> <span data-ttu-id="f9a7e-132">訊息類型是靜態的 Ack **StaticAck**。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-132">For static ACKs, the message type is **StaticAck**.</span></span>  
  
7.  <span data-ttu-id="f9a7e-133">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f9a7e-133">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a7e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9a7e-134">See Also</span></span>  
 <span data-ttu-id="f9a7e-135">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="f9a7e-135">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="f9a7e-136">[ACK 訊息結構描述類型](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span><span class="sxs-lookup"><span data-stu-id="f9a7e-136">[ACK Message Schema Types](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span></span>  
 <span data-ttu-id="f9a7e-137">[訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span><span class="sxs-lookup"><span data-stu-id="f9a7e-137">[Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span></span>  
 [<span data-ttu-id="f9a7e-138">通知錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="f9a7e-138">Acknowledgment Error Conditions</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)