---
title: "設定傳送埠來接收 Ack |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, acknowledgements
- creating, send ports
- acknowledgements, send ports
- send ports, creating
ms.assetid: bb683e72-36e2-4a8f-acc2-8b37ed23746f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df0988a9edc2af81970237aad363315a778f821b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="setting-up-a-send-port-for-receiving-acks"></a><span data-ttu-id="f4685-102">設定傳送埠來接收通知</span><span class="sxs-lookup"><span data-stu-id="f4685-102">Setting Up a Send Port for Receiving ACKs</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="f4685-103">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 即可單向傳送埠上接收通知 (ACK)。</span><span class="sxs-lookup"><span data-stu-id="f4685-103"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) can receive acknowledgments (ACK) on a one-way send port.</span></span> <span data-ttu-id="f4685-104">當您設定新的單向傳送埠來接收相同的連接上認可時，您必須使該傳送埠為單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="f4685-104">When you set up a new one-way send port for receiving ACKs on the same connection, you must associate that send port with a one-way receive port.</span></span>  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f4685-105">安裝程式會建立單向接收埠 (稱為**TwoWayAckReceivePort**) 和接收位置 (稱為**TwoWayAckReceiveLocation**)。</span><span class="sxs-lookup"><span data-stu-id="f4685-105"> setup creates a one-way receive port (called **TwoWayAckReceivePort**) and receive location (called **TwoWayAckReceiveLocation**).</span></span> <span data-ttu-id="f4685-106">接收位置會使用最少的較低層通訊協定 (MLLP) 傳輸類型、 具有 URI 的"127.0.0.1:65535"，並且使用**BTAHL72XReceivePipeline**。</span><span class="sxs-lookup"><span data-stu-id="f4685-106">The receive location uses the Minimal Lower Layer Protocol (MLLP) transport type, has a URI of "127.0.0.1:65535", and uses the **BTAHL72XReceivePipeline**.</span></span> <span data-ttu-id="f4685-107">以下是用於接收所需的設定和處理對訊息收到通知所送出[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送配接器，以雙向的模式。</span><span class="sxs-lookup"><span data-stu-id="f4685-107">These are the settings required for receiving and processing an ACK received against a message sent out by the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] send adapter, in two-way mode.</span></span> <span data-ttu-id="f4685-108">此接收位置不應該刪除或用於其他任何用途。</span><span class="sxs-lookup"><span data-stu-id="f4685-108">This receive location should not be deleted or used for any other purposes.</span></span> <span data-ttu-id="f4685-109">永遠不會將資料傳送至這個接收位置。</span><span class="sxs-lookup"><span data-stu-id="f4685-109">Never send data to this receive location.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f4685-110">啟用此接收位置的預設值。</span><span class="sxs-lookup"><span data-stu-id="f4685-110"> enables this receive location by default.</span></span>  
  
 <span data-ttu-id="f4685-111">**TwoWayAckReceiveLocation**、 哪些[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝精靈 」 建立時，會使用**BizTalkServerApplication**的接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="f4685-111">**TwoWayAckReceiveLocation**, which the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Setup Wizard creates, uses the **BizTalkServerApplication** as the receive handler.</span></span> <span data-ttu-id="f4685-112">不過，如果您選擇建立新的主機，並作為 MLLP 的接收處理常式，則您必須執行下列命令以建立新**TwoWayAckReceiveLocation**:</span><span class="sxs-lookup"><span data-stu-id="f4685-112">However, if you choose to create a new host and use it as the receive handler for MLLP, then you must do the following to create a new **TwoWayAckReceiveLocation**:</span></span>  
  
1.  <span data-ttu-id="f4685-113">建立單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="f4685-113">Create a one-way receive port.</span></span>  
  
2.  <span data-ttu-id="f4685-114">建立單向 MLLP 的接收位置。</span><span class="sxs-lookup"><span data-stu-id="f4685-114">Create a one-way MLLP receive location.</span></span>  
  
3.  <span data-ttu-id="f4685-115">指定適當 MLLP 傳輸屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f4685-115">Specify the appropriate values for the MLLP transport properties.</span></span>  
  
4.  <span data-ttu-id="f4685-116">指定適當的接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="f4685-116">Specify the appropriate receive handler.</span></span>  
  
5.  <span data-ttu-id="f4685-117">啟用接收位置。</span><span class="sxs-lookup"><span data-stu-id="f4685-117">Enable the receive location.</span></span>  
  
### <a name="to-create-a-send-port-enabled-to-receive-an-ack-on-the-same-socket"></a><span data-ttu-id="f4685-118">若要建立傳送埠來接收通知，在相同的通訊端上已啟用</span><span class="sxs-lookup"><span data-stu-id="f4685-118">To create a send port enabled to receive an ACK on the same socket</span></span>  
  
1.  <span data-ttu-id="f4685-119">開啟 BizTalk 管理主控台，然後展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk應用程式 1**。</span><span class="sxs-lookup"><span data-stu-id="f4685-119">Open the BizTalk Administration Console, and then expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1**.</span></span> <span data-ttu-id="f4685-120">以滑鼠右鍵按一下**傳送埠**，指向 [新增]，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f4685-120">Right-click **Send Ports**, point to New, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="f4685-121">在**名稱**方塊中，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4685-121">In the **Name** box, type the name of the send port.</span></span>  
  
3.  <span data-ttu-id="f4685-122">在**傳輸** 區段中，針對**類型**，選取**MLLP**。</span><span class="sxs-lookup"><span data-stu-id="f4685-122">In the **Transport** section, for **Type**, select **MLLP**.</span></span>  
  
4.  <span data-ttu-id="f4685-123">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="f4685-123">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="f4685-124">在 [MLLP 傳輸屬性] 對話方塊中，輸入連線名稱和主機 (例如， **localhost**)。</span><span class="sxs-lookup"><span data-stu-id="f4685-124">In the MLLP Transport Properties dialog box, type a connection name and host (for instance, **localhost**).</span></span>  
  
6.  <span data-ttu-id="f4685-125">如**請求回應啟用**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="f4685-125">For **Solicit Response Enabled**, select **Yes**.</span></span> <span data-ttu-id="f4685-126">保留**提交接收位置 (URI) ACK**保留空白，，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f4685-126">Leave **Submit Receive Location (URI) for ACK** blank, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4685-127">當您離開**提交接收位置**空白，BTAHL7 進入 URI 預設**TwoWayAckReceiveLocation**。</span><span class="sxs-lookup"><span data-stu-id="f4685-127">When you leave **Submit Receive Location** blank, BTAHL7 enters the URI for the default **TwoWayAckReceiveLocation**.</span></span> <span data-ttu-id="f4685-128">您可以確認後, 按一下**確定**步驟 6 中，依序按一下**組態**一次。</span><span class="sxs-lookup"><span data-stu-id="f4685-128">You can verify that after clicking **OK** in step 6, by clicking **Configuration** again.</span></span> <span data-ttu-id="f4685-129">URI **TwoWayAckReceiveLocation** (127.0.0.1:65535) 輸入**提交接收位置 (URI) ACK**。</span><span class="sxs-lookup"><span data-stu-id="f4685-129">The URI for **TwoWayAckReceiveLocation** (127.0.0.1:65535) will be entered in **Submit Receive Location (URI) for ACK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4685-130">您必須建立傳送埠以接收通知訂閱或通知中會顯示暫止狀態，因為找不到任何訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="f4685-130">You must create a send port to subscribe to the ACK received, or the ACK will be seen in a suspended state, because no subscriptions were found.</span></span> <span data-ttu-id="f4685-131">要訂閱的傳送埠所接收的通知，請使用篩選器，例如 **BTS。MessageType = = \<* MessageType*\>* * 和 **BTS。ReceivePortName = = \<* ReceivePort*\>* *。</span><span class="sxs-lookup"><span data-stu-id="f4685-131">To subscribe to the ACK received by the send port, use filters, for example, **BTS.MessageType == \<*MessageType*\>** and **BTS.ReceivePortName == \<*ReceivePort*\>**.</span></span> <span data-ttu-id="f4685-132">針對靜態的通知訊息類型是**StaticAck**。</span><span class="sxs-lookup"><span data-stu-id="f4685-132">For static ACKs, the message type is **StaticAck**.</span></span>  
  
7.  <span data-ttu-id="f4685-133">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f4685-133">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4685-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4685-134">See Also</span></span>  
 <span data-ttu-id="f4685-135">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="f4685-135">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="f4685-136">[ACK 訊息結構描述類型](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span><span class="sxs-lookup"><span data-stu-id="f4685-136">[ACK Message Schema Types](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span></span>  
 <span data-ttu-id="f4685-137">[訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span><span class="sxs-lookup"><span data-stu-id="f4685-137">[Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span></span>  
 [<span data-ttu-id="f4685-138">通知錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="f4685-138">Acknowledgment Error Conditions</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)