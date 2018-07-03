---
title: FRR 協調流程 |Microsoft Docs
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
ms.openlocfilehash: 3ad5d9dd1b582aefa9a440508650ecd0e653dbfe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998372"
---
# <a name="frr-orchestration"></a><span data-ttu-id="93153-102">FRR 協調流程</span><span class="sxs-lookup"><span data-stu-id="93153-102">FRR Orchestration</span></span>
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-103"> 實作 FRR 透過 FRR 協調流程。</span><span class="sxs-lookup"><span data-stu-id="93153-103"> implements FRR through the FRR orchestration.</span></span> <span data-ttu-id="93153-104">協調流程判斷是否相互關聯語彙基元的 FIN 回應符合原始訊息的訊息識別碼。</span><span class="sxs-lookup"><span data-stu-id="93153-104">The orchestration determines whether the Correlation Token of the FIN response matches the message ID of the original message.</span></span> <span data-ttu-id="93153-105">與傳送埠將訊息傳送至 SAA，所執行的傳送函式和從 SAA 接收訊息的接收位置所執行的接收函式，它就會處理該訊息以平行方式。</span><span class="sxs-lookup"><span data-stu-id="93153-105">It processes the message in parallel with the send functions performed by the send port that sends the message to SAA, and with the receive functions performed by the receive location that receives the message from SAA.</span></span>  
  
 <span data-ttu-id="93153-106">在最高的層級，協調流程執行個體就會執行下列處理：</span><span class="sxs-lookup"><span data-stu-id="93153-106">At the highest level, an instance of the orchestration does the following processing:</span></span>  
  
1. <span data-ttu-id="93153-107">藉由接聽 messagebox 的 SAA 的繫結的原始輸出訊息的複本快取。</span><span class="sxs-lookup"><span data-stu-id="93153-107">Caches a copy of the original outbound message bound for SAA by listening on the MessageBox.</span></span>  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="93153-108"> 建立協調流程的執行個體時[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會將原始訊息路由至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="93153-108"> creates an instance of the orchestration when [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] routes the original message to the MessageBox.</span></span>  
  
2. <span data-ttu-id="93153-109">等候[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]發佈到 MessageBox SAA FIN 回應。</span><span class="sxs-lookup"><span data-stu-id="93153-109">Waits for [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to publish a FIN response from SAA to the MessageBox.</span></span>  
  
3. <span data-ttu-id="93153-110">設定升級 FIN 回應的本質而定，原始訊息的複本的屬性。</span><span class="sxs-lookup"><span data-stu-id="93153-110">Sets promoted properties of the copy of the original message depending upon the nature of the FIN response.</span></span>  
  
4. <span data-ttu-id="93153-111">將原始訊息的副本發佈回 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="93153-111">Publishes the copy of the original message back to the MessageBox.</span></span> <span data-ttu-id="93153-112">自訂處理常式可以訂閱若要擷取，並處理該訊息所需。</span><span class="sxs-lookup"><span data-stu-id="93153-112">Custom handlers can then subscribe to, retrieve, and handle the message as required.</span></span>  
  
## <a name="subscription-to-outbound-messages"></a><span data-ttu-id="93153-113">輸出訊息的訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="93153-113">Subscription to Outbound Messages</span></span>  
 <span data-ttu-id="93153-114">FRR 協調流程直接繫結至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="93153-114">The FRR orchestration is directly bound to the MessageBox.</span></span> <span data-ttu-id="93153-115">FRR 協調流程會訂閱所有輸出訊息繫結的 SWIFT 網路不包含驗證錯誤，藉由訂閱的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="93153-115">The FRR orchestration subscribes to all outbound messages bound for the SWIFT network that do not contain validation errors, by subscribing to the following properties:</span></span>  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-116">_Failed = = false （SWIFT 解譯器驗證程序所設定）</span><span class="sxs-lookup"><span data-stu-id="93153-116">_Failed==False (as set by the SWIFT Disassembler validation process)</span></span>  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-117">_Swiftbound = = true （SWIFT 解譯器設定程序所設定）</span><span class="sxs-lookup"><span data-stu-id="93153-117">_Swiftbound==True (as set by the SWIFT Disassembler configuration process)</span></span>  
  
## <a name="messageresponse-correlation"></a><span data-ttu-id="93153-118">訊息/回應相互關聯</span><span class="sxs-lookup"><span data-stu-id="93153-118">Message/Response Correlation</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="93153-119"> 與要輸入 FIN 回應訊息的原始輸出 FIN 訊息相互關聯藉由比較下列屬性：</span><span class="sxs-lookup"><span data-stu-id="93153-119"> correlates the original outbound FIN message to the inbound FIN response message by comparing the following properties:</span></span>  
  
- <span data-ttu-id="93153-120">FIN 回應 MQMD_CorrelID 內容屬性</span><span class="sxs-lookup"><span data-stu-id="93153-120">The MQMD_CorrelID context property of the FIN response</span></span>  
  
- <span data-ttu-id="93153-121">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken 輸出 MTXYY 訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="93153-121">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken property of the outbound MTXYY message.</span></span> <span data-ttu-id="93153-122">這個屬性會由接收管線的合作對象解析階段中升級。</span><span class="sxs-lookup"><span data-stu-id="93153-122">This property is promoted by the party-resolution stage of the receive pipeline.</span></span>  
  
  <span data-ttu-id="93153-123">這些屬性的值必須相同。</span><span class="sxs-lookup"><span data-stu-id="93153-123">The values of these properties must be identical.</span></span> <span data-ttu-id="93153-124">訊息的傳送管線的編碼器階段繫結的 SWIFT 設定外寄訊息的 MQMD_MsgID 屬性的值[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken 屬性。</span><span class="sxs-lookup"><span data-stu-id="93153-124">The encoder stage of the send pipeline for messages bound for SWIFT sets the MQMD_MsgID property of the outgoing message to the value of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken property.</span></span> <span data-ttu-id="93153-125">SAA MQMD_MsgID 的值來設定回應訊息的 MQMD_CorrelID 屬性。</span><span class="sxs-lookup"><span data-stu-id="93153-125">SAA sets the MQMD_CorrelID property of the response message to the value of MQMD_MsgID.</span></span>  
  
## <a name="setting-of-promoted-properties"></a><span data-ttu-id="93153-126">升級屬性的設定</span><span class="sxs-lookup"><span data-stu-id="93153-126">Setting of Promoted Properties</span></span>  
 <span data-ttu-id="93153-127">接收 FIN 回應，並建立相互關聯的原始訊息複本之後, FRR 協調流程會設定根據回應的本質，原始訊息的複本升級的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="93153-127">After receiving a FIN response and correlating it to the copy of the original message, the FRR orchestration sets the following promoted properties of the copy of the original message according to the nature of the response:</span></span>  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-128">為 True，如果回應是通知或 False 的回應是否 NAK _FRRFailed</span><span class="sxs-lookup"><span data-stu-id="93153-128">_FRRFailed to True if the response was an ACK or False if the response was a NAK</span></span>  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-129">其中一個下列的值，如果回應是 NAK 至 _FRRFailedReason:</span><span class="sxs-lookup"><span data-stu-id="93153-129">_FRRFailedReason to the one of the following values, if the response was a NAK:</span></span>  
  
  -   <span data-ttu-id="93153-130">*\<ErrorCode\>*  （從 MTS21_FIN_ACKNAK 負值通知訊息的 「 405 欄位）</span><span class="sxs-lookup"><span data-stu-id="93153-130">*\<ErrorCode\>* (from the 405 field of the MTS21_FIN_ACKNAK negative-acknowledgment message)</span></span>  
  
  -   <span data-ttu-id="93153-131">TransportError （從 MQ 系列移動瀏覽/NAN 訊息）</span><span class="sxs-lookup"><span data-stu-id="93153-131">TransportError (from an MQ Series PAN/NAN message)</span></span>  
  
  -   <span data-ttu-id="93153-132">DelayedNAK （從 MT015 (DNK) 訊息）</span><span class="sxs-lookup"><span data-stu-id="93153-132">DelayedNAK (from an MT015 (DNK) message)</span></span>  
  
  -   <span data-ttu-id="93153-133">AbortReceived (從 MT019 （中止通知） 訊息)</span><span class="sxs-lookup"><span data-stu-id="93153-133">AbortReceived (from an MT019 (Abort Notification) message)</span></span>  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-134">為 TimedOut _FRRFailedReason 如果[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]未在逾時期限內收到回應。</span><span class="sxs-lookup"><span data-stu-id="93153-134">_FRRFailedReason to TimedOut if [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] did not receive a response within the timeout period.</span></span> <span data-ttu-id="93153-135">如需有關 FRR 延遲逾時的詳細資訊，請參閱下方的 [調整逾時] 區段或[設定 FRR 延遲逾時](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md)。</span><span class="sxs-lookup"><span data-stu-id="93153-135">For more information about the FRR Delay Time-out, see the "Reconciliation Time-Out" section below or [Setting the FRR Delay Time-Out](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).</span></span>  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-136">若要 _SendingServiceType [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span><span class="sxs-lookup"><span data-stu-id="93153-136">_SendingServiceType to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span></span>  
  
- <span data-ttu-id="93153-137">BTS。作業的回應訊息類型的對應值。</span><span class="sxs-lookup"><span data-stu-id="93153-137">BTS.Operation to the value corresponding to the type of message response.</span></span> <span data-ttu-id="93153-138">如需詳細資訊，請參閱 <<c0> [ 傳送至自訂處理常式建立 FRR 傳送埠](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="93153-138">For more information, see [Creating the FRR Send Ports for Sending to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span></span>  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-139">_FrrSendTransport MQ 系列移動瀏覽/NAN 訊息 (MQ Series 傳輸層級通知/NAK)</span><span class="sxs-lookup"><span data-stu-id="93153-139">_FrrSendTransport for an MQ Series PAN/NAN message (MQ Series transport-level ACK/NAK)</span></span>  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-140">_FrrSend010NDW MT010 訊息 （非傳遞警告）</span><span class="sxs-lookup"><span data-stu-id="93153-140">_FrrSend010NDW for an MT010 message (Non-Delivery Warning)</span></span>  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-141">_FrrSend011Delivered MT011 訊息 (Delivery Notification)</span><span class="sxs-lookup"><span data-stu-id="93153-141">_FrrSend011Delivered for an MT011 message (Delivery Notification)</span></span>  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-142">_FrrSend012SenderACK MT012 訊息 （寄件者通知）</span><span class="sxs-lookup"><span data-stu-id="93153-142">_FrrSend012SenderACK for an MT012 message (Sender Notification)</span></span>  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-143">_FrrSend015DNK MT015 訊息 （DNK 或延遲 NAK）</span><span class="sxs-lookup"><span data-stu-id="93153-143">_FrrSend015DNK for an MT015 message (DNK, or Delayed NAK)</span></span>  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-144">_FrrSend019Abort MT019 訊息 （中止通知）</span><span class="sxs-lookup"><span data-stu-id="93153-144">_FrrSend019Abort for an MT019 message (Abort Notification)</span></span>  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-145">_FrrSendS21ACK MTS21_FIN_ACKNAK 通知訊息 (由 l 傳送 FIN 訊息的 ACK)</span><span class="sxs-lookup"><span data-stu-id="93153-145">_FrrSendS21ACK for an MTS21_FIN_ACKNAK acknowledgment message (ACK of a FIN message sent by an LT)</span></span>  
  
  - [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-146">_FrrSendS21NAK MTS21_FIN_ACKNAK 負值通知訊息 (NAK 的 FIN 訊息傳送的 L)</span><span class="sxs-lookup"><span data-stu-id="93153-146">_FrrSendS21NAK for an MTS21_FIN_ACKNAK negative-acknowledgment message (NAK of a FIN message sent by an LT)</span></span>  
  
## <a name="direct-binding"></a><span data-ttu-id="93153-147">直接繫結</span><span class="sxs-lookup"><span data-stu-id="93153-147">Direct Binding</span></span>  
 <span data-ttu-id="93153-148">協調流程由協調流程會到 MessageBox 的訂用帳戶接收的輸入。</span><span class="sxs-lookup"><span data-stu-id="93153-148">Receive inputs for the orchestration are defined by subscriptions that the orchestration makes to the MessageBox.</span></span> <span data-ttu-id="93153-149">內容屬性，以及協調流程所提升的值會定義協調流程發佈到 MessageBox 的訊息的傳送輸出。</span><span class="sxs-lookup"><span data-stu-id="93153-149">Context properties and values promoted by the orchestration define the send outputs for a message that the orchestration publishes to the MessageBox.</span></span> <span data-ttu-id="93153-150">因為此 messagebox 直接繫結，就會與下列分離協調流程：</span><span class="sxs-lookup"><span data-stu-id="93153-150">Because of this direct binding to the MessageBox, the orchestration is decoupled from the following:</span></span>  
  
- <span data-ttu-id="93153-151">實體接收位置會從後端應用程式，以路由至 SAA 接收輸出的訊息</span><span class="sxs-lookup"><span data-stu-id="93153-151">The physical receive locations that receive outbound messages from the back-end application for routing to SAA</span></span>  
  
- <span data-ttu-id="93153-152">傳送輸出的傳送埠 FIN 訊息從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]SWIFT Alliance 存取 (SAA)</span><span class="sxs-lookup"><span data-stu-id="93153-152">The send ports that send outbound FIN messages from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the SWIFT Alliance Access (SAA)</span></span>  
  
- <span data-ttu-id="93153-153">從 SAA 接收連入 FIN 回應訊息的接收位置</span><span class="sxs-lookup"><span data-stu-id="93153-153">The receive locations that receive incoming FIN response messages from SAA</span></span>  
  
- <span data-ttu-id="93153-154">實體由 SAA 均存放 FIN 回應的 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="93153-154">The physical MQSeries queues where FIN responses are deposited by SAA</span></span>  
  
## <a name="reconciliation-time-out"></a><span data-ttu-id="93153-155">調整逾時</span><span class="sxs-lookup"><span data-stu-id="93153-155">Reconciliation Time-Out</span></span>  
 <span data-ttu-id="93153-156">當[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]建立 FRR 協調流程中，等候 FIN 回應在協調流程啟動的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="93153-156">When [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] creates a new instance of the FRR orchestration, the orchestration starts waiting for FIN responses.</span></span> <span data-ttu-id="93153-157">在執行階段，您必須設定逾時後段期間，協調流程，使它不會等待回應無限期。</span><span class="sxs-lookup"><span data-stu-id="93153-157">At run time, you must configure the orchestration to time out after some duration, so that it will not wait for the response indefinitely.</span></span> <span data-ttu-id="93153-158">FRR 協調流程時逾時期限到期時，會升級[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason 屬性並將其設為 TimedOut。</span><span class="sxs-lookup"><span data-stu-id="93153-158">When the time-out duration expires, the FRR orchestration promotes the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason property and sets it to TimedOut.</span></span> <span data-ttu-id="93153-159">然後，它會將輸出訊息發佈到 MessageBox，並終止。</span><span class="sxs-lookup"><span data-stu-id="93153-159">It then publishes messages out to the MessageBox, and terminates.</span></span> <span data-ttu-id="93153-160">如果您的時間，相互關聯識別碼變不見了。</span><span class="sxs-lookup"><span data-stu-id="93153-160">If you time out, the correlation ID is gone.</span></span>  
  
 <span data-ttu-id="93153-161">您可以建立自訂的處理常式，來處理逾時訊息 （原始輸出訊息的複本）。</span><span class="sxs-lookup"><span data-stu-id="93153-161">You can create a custom handler to process timed-out messages (the copy of the original outbound message).</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="93153-162"> 會完成這項作業使用待命圖形在協調流程中。</span><span class="sxs-lookup"><span data-stu-id="93153-162"> would accomplish this by using a Listen shape in the orchestration.</span></span> <span data-ttu-id="93153-163">如需詳細資訊，請參閱 <<c0> [ 設定 FRR 延遲逾時](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md)。</span><span class="sxs-lookup"><span data-stu-id="93153-163">For more information, see [Setting the FRR Delay Time-Out](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).</span></span>