---
title: FRR 協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, promoted properties
- orchestrations, message subscriptions
- promoted properties, messages
- FRR, orchestrations
- subscriptions, messages
- orchestrations, reconciliation time-out
- messages, message/response correlation
- message/response correlation
- promoted properties, FIN Response Reconciliation
- orchestrations, FRR
- outbound messages
- FIN Response Reconciliation, promoted properties
- direct bindings
- reconciliation time-out
- bindings, direct
- messages, subscriptions
- subscriptions, orchestrations
- messages, outbound
- MessageBox database
ms.assetid: ea8d31c2-ac3b-44ac-8064-d008da4f7f72
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f56b16f59b967ccd9e57d03d38f86e64795da477
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967876"
---
# <a name="frr-orchestration"></a><span data-ttu-id="cc6f9-102">FRR 協調流程</span><span class="sxs-lookup"><span data-stu-id="cc6f9-102">FRR Orchestration</span></span>
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-103">實作 FRR 透過 FRR 協調流程。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-103"> implements FRR through the FRR orchestration.</span></span> <span data-ttu-id="cc6f9-104">協調流程判斷是否相互關聯語彙基元 FIN 回應符合原始訊息的訊息識別碼。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-104">The orchestration determines whether the Correlation Token of the FIN response matches the message ID of the original message.</span></span> <span data-ttu-id="cc6f9-105">傳送埠將訊息傳送至 SAA，所執行的傳送函式與 SAA 從接收訊息的接收位置所執行的接收函式，它就會處理該訊息以平行方式。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-105">It processes the message in parallel with the send functions performed by the send port that sends the message to SAA, and with the receive functions performed by the receive location that receives the message from SAA.</span></span>  
  
 <span data-ttu-id="cc6f9-106">在最高的層級，協調流程執行個體就會執行下列處理：</span><span class="sxs-lookup"><span data-stu-id="cc6f9-106">At the highest level, an instance of the orchestration does the following processing:</span></span>  
  
1.  <span data-ttu-id="cc6f9-107">快取原始輸出訊息的複本繫結 SAA 透過 MessageBox 上接聽。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-107">Caches a copy of the original outbound message bound for SAA by listening on the MessageBox.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="cc6f9-108">建立協調流程的執行個體時[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會將原始訊息路由至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-108"> creates an instance of the orchestration when [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] routes the original message to the MessageBox.</span></span>  
  
2.  <span data-ttu-id="cc6f9-109">等候[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]發佈至 MessageBox SAA FIN 回應。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-109">Waits for [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to publish a FIN response from SAA to the MessageBox.</span></span>  
  
3.  <span data-ttu-id="cc6f9-110">設定升級 FIN 回應的本質而定，原始訊息的複製的內容。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-110">Sets promoted properties of the copy of the original message depending upon the nature of the FIN response.</span></span>  
  
4.  <span data-ttu-id="cc6f9-111">將原始訊息的副本發佈回 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-111">Publishes the copy of the original message back to the MessageBox.</span></span> <span data-ttu-id="cc6f9-112">自訂處理常式可以訂閱擷取，並處理該訊息所需。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-112">Custom handlers can then subscribe to, retrieve, and handle the message as required.</span></span>  
  
## <a name="subscription-to-outbound-messages"></a><span data-ttu-id="cc6f9-113">輸出訊息的訂閱</span><span class="sxs-lookup"><span data-stu-id="cc6f9-113">Subscription to Outbound Messages</span></span>  
 <span data-ttu-id="cc6f9-114">FRR 協調流程直接繫結至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-114">The FRR orchestration is directly bound to the MessageBox.</span></span> <span data-ttu-id="cc6f9-115">FRR 協調流程會訂閱所有輸出訊息的 SWIFT 網路繫結不包含驗證錯誤，藉由訂閱的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="cc6f9-115">The FRR orchestration subscribes to all outbound messages bound for the SWIFT network that do not contain validation errors, by subscribing to the following properties:</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-116">_Failed = = false （SWIFT 解譯器驗證程序所設定）</span><span class="sxs-lookup"><span data-stu-id="cc6f9-116">_Failed==False (as set by the SWIFT Disassembler validation process)</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-117">_Swiftbound = = true （SWIFT 解譯器組態程序所設定）</span><span class="sxs-lookup"><span data-stu-id="cc6f9-117">_Swiftbound==True (as set by the SWIFT Disassembler configuration process)</span></span>  
  
## <a name="messageresponse-correlation"></a><span data-ttu-id="cc6f9-118">/ 回應訊息的相互關聯</span><span class="sxs-lookup"><span data-stu-id="cc6f9-118">Message/Response Correlation</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="cc6f9-119">與要輸入 FIN 回應訊息的原始輸出 FIN 訊息相互關聯藉由比較下列屬性：</span><span class="sxs-lookup"><span data-stu-id="cc6f9-119"> correlates the original outbound FIN message to the inbound FIN response message by comparing the following properties:</span></span>  
  
-   <span data-ttu-id="cc6f9-120">FIN 回應 MQMD_CorrelID 內容屬性</span><span class="sxs-lookup"><span data-stu-id="cc6f9-120">The MQMD_CorrelID context property of the FIN response</span></span>  
  
-   <span data-ttu-id="cc6f9-121">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken 輸出 MTXYY 訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-121">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken property of the outbound MTXYY message.</span></span> <span data-ttu-id="cc6f9-122">這個屬性會由接收管線的合作對象解析階段升級。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-122">This property is promoted by the party-resolution stage of the receive pipeline.</span></span>  
  
 <span data-ttu-id="cc6f9-123">這些屬性的值必須相同。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-123">The values of these properties must be identical.</span></span> <span data-ttu-id="cc6f9-124">訊息的傳送管線的編碼器階段繫結的 SWIFT 設定外寄訊息的 MQMD_MsgID 屬性的值[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken 屬性。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-124">The encoder stage of the send pipeline for messages bound for SWIFT sets the MQMD_MsgID property of the outgoing message to the value of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken property.</span></span> <span data-ttu-id="cc6f9-125">SAA 設定回應訊息的 MQMD_CorrelID 屬性 MQMD_MsgID 的值。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-125">SAA sets the MQMD_CorrelID property of the response message to the value of MQMD_MsgID.</span></span>  
  
## <a name="setting-of-promoted-properties"></a><span data-ttu-id="cc6f9-126">升級屬性的設定</span><span class="sxs-lookup"><span data-stu-id="cc6f9-126">Setting of Promoted Properties</span></span>  
 <span data-ttu-id="cc6f9-127">接收 FIN 回應並建立相互關聯的原始訊息的副本之後, FRR 協調流程會設定根據回應的本質，原始訊息的複本的升級下列屬性：</span><span class="sxs-lookup"><span data-stu-id="cc6f9-127">After receiving a FIN response and correlating it to the copy of the original message, the FRR orchestration sets the following promoted properties of the copy of the original message according to the nature of the response:</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-128">為 True，如果回應 ACK 或 False 的回應是 NAK 如果 _FRRFailed</span><span class="sxs-lookup"><span data-stu-id="cc6f9-128">_FRRFailed to True if the response was an ACK or False if the response was a NAK</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-129">其中一個下列的值，如果回應 NAK _FRRFailedReason:</span><span class="sxs-lookup"><span data-stu-id="cc6f9-129">_FRRFailedReason to the one of the following values, if the response was a NAK:</span></span>  
  
    -   <span data-ttu-id="cc6f9-130">*\<ErrorCode\>*  （從 MTS21_FIN_ACKNAK 負值通知訊息的 405 欄位）</span><span class="sxs-lookup"><span data-stu-id="cc6f9-130">*\<ErrorCode\>* (from the 405 field of the MTS21_FIN_ACKNAK negative-acknowledgment message)</span></span>  
  
    -   <span data-ttu-id="cc6f9-131">TransportError （從 MQ 系列取景位置調整/NAN 訊息）</span><span class="sxs-lookup"><span data-stu-id="cc6f9-131">TransportError (from an MQ Series PAN/NAN message)</span></span>  
  
    -   <span data-ttu-id="cc6f9-132">DelayedNAK （從 MT015 (DNK) 訊息）</span><span class="sxs-lookup"><span data-stu-id="cc6f9-132">DelayedNAK (from an MT015 (DNK) message)</span></span>  
  
    -   <span data-ttu-id="cc6f9-133">AbortReceived (從 MT019 （中止通知） 訊息)</span><span class="sxs-lookup"><span data-stu-id="cc6f9-133">AbortReceived (from an MT019 (Abort Notification) message)</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-134">逾時的 _FRRFailedReason 如果[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]未在逾時期限內收到回應。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-134">_FRRFailedReason to TimedOut if [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] did not receive a response within the timeout period.</span></span> <span data-ttu-id="cc6f9-135">如需 FRR 延遲逾時的詳細資訊，請參閱下方的 [對帳逾時] 區段或[設定 FRR 延遲逾時](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md)。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-135">For more information about the FRR Delay Time-out, see the "Reconciliation Time-Out" section below or [Setting the FRR Delay Time-Out](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-136">若要 _SendingServiceType [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span><span class="sxs-lookup"><span data-stu-id="cc6f9-136">_SendingServiceType to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span></span>  
  
-   <span data-ttu-id="cc6f9-137">BTS。作業的訊息回應型別對應的值。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-137">BTS.Operation to the value corresponding to the type of message response.</span></span> <span data-ttu-id="cc6f9-138">如需詳細資訊，請參閱[FRR 傳送埠建立的自訂處理常式的傳送](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-138">For more information, see [Creating the FRR Send Ports for Sending to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-139">_FrrSendTransport MQ 系列取景位置調整/NAN 訊息 (MQ Series 傳輸層級 ACK/NAK)</span><span class="sxs-lookup"><span data-stu-id="cc6f9-139">_FrrSendTransport for an MQ Series PAN/NAN message (MQ Series transport-level ACK/NAK)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-140">_FrrSend010NDW MT010 訊息 （非傳遞警告）</span><span class="sxs-lookup"><span data-stu-id="cc6f9-140">_FrrSend010NDW for an MT010 message (Non-Delivery Warning)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-141">_FrrSend011Delivered MT011 訊息 （傳送通知）</span><span class="sxs-lookup"><span data-stu-id="cc6f9-141">_FrrSend011Delivered for an MT011 message (Delivery Notification)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-142">_FrrSend012SenderACK MT012 訊息 （寄件者通知）</span><span class="sxs-lookup"><span data-stu-id="cc6f9-142">_FrrSend012SenderACK for an MT012 message (Sender Notification)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-143">_FrrSend015DNK MT015 訊息 （DNK 或延遲 NAK）</span><span class="sxs-lookup"><span data-stu-id="cc6f9-143">_FrrSend015DNK for an MT015 message (DNK, or Delayed NAK)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-144">_FrrSend019Abort MT019 訊息 （中止通知）</span><span class="sxs-lookup"><span data-stu-id="cc6f9-144">_FrrSend019Abort for an MT019 message (Abort Notification)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-145">_FrrSendS21ACK MTS21_FIN_ACKNAK 通知訊息 (ACK 傳送 LT FIN 訊息)</span><span class="sxs-lookup"><span data-stu-id="cc6f9-145">_FrrSendS21ACK for an MTS21_FIN_ACKNAK acknowledgment message (ACK of a FIN message sent by an LT)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-146">_FrrSendS21NAK MTS21_FIN_ACKNAK 負值通知訊息 (NAK 傳送 LT FIN 訊息)</span><span class="sxs-lookup"><span data-stu-id="cc6f9-146">_FrrSendS21NAK for an MTS21_FIN_ACKNAK negative-acknowledgment message (NAK of a FIN message sent by an LT)</span></span>  
  
## <a name="direct-binding"></a><span data-ttu-id="cc6f9-147">直接繫結</span><span class="sxs-lookup"><span data-stu-id="cc6f9-147">Direct Binding</span></span>  
 <span data-ttu-id="cc6f9-148">輸入接收協調流程會由協調流程對 MessageBox 訂閱。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-148">Receive inputs for the orchestration are defined by subscriptions that the orchestration makes to the MessageBox.</span></span> <span data-ttu-id="cc6f9-149">內容屬性，以及由協調流程升級值定義協調流程發佈到 MessageBox 的訊息的傳送輸出。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-149">Context properties and values promoted by the orchestration define the send outputs for a message that the orchestration publishes to the MessageBox.</span></span> <span data-ttu-id="cc6f9-150">此 messagebox 直接繫結，因為協調流程就可以從下列分隔：</span><span class="sxs-lookup"><span data-stu-id="cc6f9-150">Because of this direct binding to the MessageBox, the orchestration is decoupled from the following:</span></span>  
  
-   <span data-ttu-id="cc6f9-151">實體接收位置會接收來自後端應用程式，以路由至 SAA 輸出訊息</span><span class="sxs-lookup"><span data-stu-id="cc6f9-151">The physical receive locations that receive outbound messages from the back-end application for routing to SAA</span></span>  
  
-   <span data-ttu-id="cc6f9-152">傳送輸出的傳送埠 FIN 訊息從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]SWIFT 聯盟存取 (SAA)</span><span class="sxs-lookup"><span data-stu-id="cc6f9-152">The send ports that send outbound FIN messages from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the SWIFT Alliance Access (SAA)</span></span>  
  
-   <span data-ttu-id="cc6f9-153">從 SAA 接收連入 FIN 回應訊息的接收位置</span><span class="sxs-lookup"><span data-stu-id="cc6f9-153">The receive locations that receive incoming FIN response messages from SAA</span></span>  
  
-   <span data-ttu-id="cc6f9-154">實體由 SAA 均存放 FIN 回應的 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="cc6f9-154">The physical MQSeries queues where FIN responses are deposited by SAA</span></span>  
  
## <a name="reconciliation-time-out"></a><span data-ttu-id="cc6f9-155">重新調整逾時</span><span class="sxs-lookup"><span data-stu-id="cc6f9-155">Reconciliation Time-Out</span></span>  
 <span data-ttu-id="cc6f9-156">當[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]FRR 協調流程，在等候 FIN 回應的協調流程啟動的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-156">When [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] creates a new instance of the FRR orchestration, the orchestration starts waiting for FIN responses.</span></span> <span data-ttu-id="cc6f9-157">在執行階段，您必須設定協調流程的逾時時間後一些持續時間，使它不會等待回應無限期。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-157">At run time, you must configure the orchestration to time out after some duration, so that it will not wait for the response indefinitely.</span></span> <span data-ttu-id="cc6f9-158">當逾時期間到期時，會升級 FRR 協調流程[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason 屬性並將它設定為逾時。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-158">When the time-out duration expires, the FRR orchestration promotes the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason property and sets it to TimedOut.</span></span> <span data-ttu-id="cc6f9-159">然後，將出的訊息發佈到 MessageBox，並終止。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-159">It then publishes messages out to the MessageBox, and terminates.</span></span> <span data-ttu-id="cc6f9-160">如果您的時間，相互關聯識別碼會消失。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-160">If you time out, the correlation ID is gone.</span></span>  
  
 <span data-ttu-id="cc6f9-161">您可以建立自訂的處理常式來處理逾時訊息 （原始輸出訊息的複本）。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-161">You can create a custom handler to process timed-out messages (the copy of the original outbound message).</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="cc6f9-162">會完成這項作業使用待命圖形在協調流程中。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-162"> would accomplish this by using a Listen shape in the orchestration.</span></span> <span data-ttu-id="cc6f9-163">如需詳細資訊，請參閱[設定 FRR 延遲逾時](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md)。</span><span class="sxs-lookup"><span data-stu-id="cc6f9-163">For more information, see [Setting the FRR Delay Time-Out](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).</span></span>