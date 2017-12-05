---
title: "訊息如何流經 BTAHL7 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, message processing
- messages, message flow
- BTAHL7, message flow
ms.assetid: dd4599af-500d-4e52-85b2-8b6a28fd3f0a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33f06c896b58b2ba57c8c1bcee598d23f81b7700
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-messages-flow-through-btahl7"></a><span data-ttu-id="a79b0-102">訊息如何流經 BTAHL7</span><span class="sxs-lookup"><span data-stu-id="a79b0-102">How Messages Flow through BTAHL7</span></span>
<span data-ttu-id="a79b0-103">當您安裝[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 上方的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]加入 BizTalk Server[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]元件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]架構。</span><span class="sxs-lookup"><span data-stu-id="a79b0-103">When you install [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) on top of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server, you add [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] components to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] architecture.</span></span> <span data-ttu-id="a79b0-104">下圖顯示合併的系統提供的架構概觀[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a79b0-104">The following figure shows the combined system, which provides an architectural overview of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].</span></span>  
  
 <span data-ttu-id="a79b0-105">![](../../adapters-and-accelerators/accelerator-hl7/media/bcd-hl7-sys-archc.gif "bcd_hl7_sys_archc")</span><span class="sxs-lookup"><span data-stu-id="a79b0-105">![](../../adapters-and-accelerators/accelerator-hl7/media/bcd-hl7-sys-archc.gif "bcd_hl7_sys_archc")</span></span>  
  
## <a name="message-processing-flow"></a><span data-ttu-id="a79b0-106">訊息處理流程</span><span class="sxs-lookup"><span data-stu-id="a79b0-106">Message Processing Flow</span></span>  
 <span data-ttu-id="a79b0-107">當特定業務應用程式傳送訊息給[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]系統，則發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="a79b0-107">When a line-of-business application sends a message to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] system, the following occurs:</span></span>  
  
1.  <span data-ttu-id="a79b0-108">如果訊息是 HL7 訊息，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接收透過介面卡 （通常 MLLP 配接器）。</span><span class="sxs-lookup"><span data-stu-id="a79b0-108">If the message is an HL7 message, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives it through an adapter (usually an MLLP adapter).</span></span> <span data-ttu-id="a79b0-109">如果是 XML 訊息，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接收透過介面卡 （通常是 HTTP 配接器）。</span><span class="sxs-lookup"><span data-stu-id="a79b0-109">If it is an XML message, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives it through an adapter (usually an HTTP adapter).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a79b0-110">您可以透過任何配接器; 傳輸 2.X 和 2.XML 訊息不過，您通常會傳輸 V2。透過 MLLP 配接器，而且您的 X 訊息通常會透過 HTTP 配接器傳輸 2.XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="a79b0-110">You can transport both 2.X and 2.XML messages over any adapter; however, you would usually transport V2.X messages over an MLLP adapter, and you would usually transport 2.XML messages over an HTTP adapter.</span></span>  
  
2.  <span data-ttu-id="a79b0-111">透過解譯器和驗證所剖析的接收管線會將郵件路由傳送。</span><span class="sxs-lookup"><span data-stu-id="a79b0-111">The message is routed through the receive pipeline for parsing by the disassembler, and validation.</span></span>  
  
    1.  <span data-ttu-id="a79b0-112">如果內送訊息的 HL7 訊息，則一般檔案解譯器 (DASM) 會將它解譯成 XML。</span><span class="sxs-lookup"><span data-stu-id="a79b0-112">If the incoming message is an HL7 message, the flat file disassembler (DASM) disassembles it into XML.</span></span> <span data-ttu-id="a79b0-113">如果內送訊息的 XML 訊息，XML DASM 反組譯它。</span><span class="sxs-lookup"><span data-stu-id="a79b0-113">If the incoming message is an XML message, the XML DASM disassembles it.</span></span>  
  
    2.  <span data-ttu-id="a79b0-114">如果內送訊息批次訊息，解譯器將解譯成個別的訊息中。</span><span class="sxs-lookup"><span data-stu-id="a79b0-114">If the incoming message is a batch message, the disassembler disassembles into the individual messages.</span></span> <span data-ttu-id="a79b0-115">(如需詳細資訊，請參閱[批次訊息處理](../../adapters-and-accelerators/accelerator-hl7/batch-message-processing.md)和[訊息批次處理](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)。)</span><span class="sxs-lookup"><span data-stu-id="a79b0-115">(For more details, see [Batch Message Processing](../../adapters-and-accelerators/accelerator-hl7/batch-message-processing.md) and [Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md).)</span></span>  
  
    3.  <span data-ttu-id="a79b0-116">DASM 接著會驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="a79b0-116">The DASM then validates the message.</span></span>  
  
    4.  <span data-ttu-id="a79b0-117">如果您使用雙向 MLLP 接收配接器，而且如果解譯器已驗證訊息，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]來將訊息傳遞相同的配接器接收原始訊息的原始傳送者傳送通知 (ACK)。</span><span class="sxs-lookup"><span data-stu-id="a79b0-117">If you use a two-way MLLP receive adapter, and if the disassembler has validated the message, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an acknowledgment (ACK) to the original sender of the message through the same adapter that received the original message.</span></span> <span data-ttu-id="a79b0-118">如果沒有，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將負值通知 (NAK)。</span><span class="sxs-lookup"><span data-stu-id="a79b0-118">If not, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends a negative acknowledgment (NAK).</span></span> <span data-ttu-id="a79b0-119">（如何完成此步驟取決於通知設定。</span><span class="sxs-lookup"><span data-stu-id="a79b0-119">(How this step is accomplished depends on the ACK configuration.</span></span> <span data-ttu-id="a79b0-120">如需詳細資訊，請參閱[ACK 訊息模式](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)。)</span><span class="sxs-lookup"><span data-stu-id="a79b0-120">For details, see [ACK Message Modes](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md).)</span></span>  
  
    5.  <span data-ttu-id="a79b0-121">如果您未使用雙向 MLLP 接收配接器，然後[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生 ACK 或認可 （或 NAK 或 NAKs），並將 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a79b0-121">If you do not use a two-way MLLP receive adapter, then [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates an ACK or ACKs (or NAK or NAKs) and deposits it into the MessageBox database.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a79b0-122">然後將其路由至適當的合作對象傳送埠組態，可以使用任何其他配接器 （除了 MLLP) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="a79b0-122"> then routes it to the appropriate parties based on the send port configuration, which could use any of the other adapters (besides MLLP).</span></span>  
  
     <span data-ttu-id="a79b0-123">在一般檔案和 XML 解譯器中，執行的處理程序的更完整清單，請參閱[BizTalk Accelerator for HL7 元件](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)。</span><span class="sxs-lookup"><span data-stu-id="a79b0-123">For a more complete listing of the processes performed in the flat file and XML disassemblers, see [BizTalk Accelerator for HL7 Components](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md).</span></span>  
  
3.  <span data-ttu-id="a79b0-124">訊息通過配接器和接收管線中之後,[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將訊息傳遞至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a79b0-124">After the message passes through the adapter and the receive pipeline, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] passes the message into the MessageBox database.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a79b0-125">然後會判斷傳送訊息接下來的位置。</span><span class="sxs-lookup"><span data-stu-id="a79b0-125"> then determines where to send the message next.</span></span> <span data-ttu-id="a79b0-126">如果訊息是協調流程的一部分，它會傳送訊息至協調流程引擎。</span><span class="sxs-lookup"><span data-stu-id="a79b0-126">If the message is part of an orchestration, it sends the message to the Orchestration Engine.</span></span>  
  
4.  <span data-ttu-id="a79b0-127">協調流程引擎處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="a79b0-127">The Orchestration Engine processes the message.</span></span>  
  
    1.  <span data-ttu-id="a79b0-128">如果對應會影響訊息，對應會將訊息根據其規則來轉換。</span><span class="sxs-lookup"><span data-stu-id="a79b0-128">If a map affects the message, the map transforms the message according to its rules.</span></span>  
  
    2.  <span data-ttu-id="a79b0-129">如果您已設定商務規則，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用外部管線、 協調流程引擎可能在商務規則引擎 (BRE)。</span><span class="sxs-lookup"><span data-stu-id="a79b0-129">If you have set up a business rule, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] invokes the Business Rule Engine (BRE) outside of the pipelines, potentially in the Orchestration Engine.</span></span>  
  
    3.  <span data-ttu-id="a79b0-130">協調流程引擎將訊息傳送至 MessageBox 資料庫，然後再繼續執行處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="a79b0-130">The Orchestration Engine sends the message back to the MessageBox database, and then continues processing the orchestration.</span></span>  
  
5.  <span data-ttu-id="a79b0-131">根據訂閱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會將訊息路由至傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a79b0-131">Based on the subscription, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] routes the message to the send port.</span></span>  
  
6.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a79b0-132">會透過下列的處理 （如果適用） 的傳送管線將訊息路由： 組件和驗證。</span><span class="sxs-lookup"><span data-stu-id="a79b0-132"> routes the message through the send pipeline for the following processing (if applicable): assembly and validation.</span></span>  
  
    1.  <span data-ttu-id="a79b0-133">如果訊息將 HL7 2.X 訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會從 XML 的訊息組合成 HL7 一般檔案組合器 (ASM)。</span><span class="sxs-lookup"><span data-stu-id="a79b0-133">If the message will be an HL7 2.X message, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] assembles the message from XML into HL7 by the flat file assembler (ASM).</span></span> <span data-ttu-id="a79b0-134">如果內送訊息將 XML 訊息，XML DASM 將其組合。</span><span class="sxs-lookup"><span data-stu-id="a79b0-134">If the incoming message will be an XML message, the XML DASM assembles it.</span></span>  
  
    2.  <span data-ttu-id="a79b0-135">若訊息批次訊息的一部份[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會將每個訊息組合成批次訊息。</span><span class="sxs-lookup"><span data-stu-id="a79b0-135">If the message will be part of a batch message, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] assembles each message into the batch message.</span></span> <span data-ttu-id="a79b0-136">(如需詳細資訊，請參閱[批次訊息處理](../../adapters-and-accelerators/accelerator-hl7/batch-message-processing.md)和[訊息批次處理](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)。)</span><span class="sxs-lookup"><span data-stu-id="a79b0-136">(For more details, see [Batch Message Processing](../../adapters-and-accelerators/accelerator-hl7/batch-message-processing.md) and [Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md).)</span></span>  
  
    3.  <span data-ttu-id="a79b0-137">ASM 驗證訊息 （如果啟用透過傳送合作對象組態設定）。</span><span class="sxs-lookup"><span data-stu-id="a79b0-137">The ASM validates the message (if enabled through send-party configuration settings).</span></span>  
  
     <span data-ttu-id="a79b0-138">在一般檔案和 XML 組合器中，執行的處理程序的更完整清單，請參閱[BizTalk Accelerator for HL7 元件](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)。</span><span class="sxs-lookup"><span data-stu-id="a79b0-138">For a more complete listing of the processes performed in the flat file and XML assemblers, see [BizTalk Accelerator for HL7 Components](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md).</span></span>  
  
7.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a79b0-139">傳送訊息到配接器。</span><span class="sxs-lookup"><span data-stu-id="a79b0-139"> sends the message through an adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a79b0-140">您可以針對數目的介面卡; 傳輸 2.X 訊息和 2.XML 訊息不過，大部分系統傳輸 2.X 訊息透過 MLLP 配接器和 2.XML 訊息透過 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="a79b0-140">You can transport 2.X messages and 2.XML messages over a number of adapters; however, most systems transport 2.X messages over an MLLP adapter, and 2.XML messages over an HTTP adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a79b0-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="a79b0-141">See Also</span></span>  
 [<span data-ttu-id="a79b0-142">BTAHL7 如何路由傳送訊息</span><span class="sxs-lookup"><span data-stu-id="a79b0-142">How BTAHL7 Routes Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/how-btahl7-routes-messages.md)