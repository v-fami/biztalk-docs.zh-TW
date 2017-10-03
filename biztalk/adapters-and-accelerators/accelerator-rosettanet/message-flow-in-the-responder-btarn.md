---
title: "訊息回應者 BTARN 中的流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Accelerator for RosettaNet, message flow
- BTARN, components
- messages, message flow
- responder BTARN
ms.assetid: 66de8694-a248-47e8-9483-9eedf2324b33
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ad33db4f67336f41ac868a7a14e1266a85dd45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-flow-in-the-responder-btarn"></a><span data-ttu-id="f45c7-102">回應者 BTARN 中的訊息流程</span><span class="sxs-lookup"><span data-stu-id="f45c7-102">Message Flow in the Responder BTARN</span></span>
<span data-ttu-id="f45c7-103">回應者電腦上的訊息流程一開始會透過網際網路接收來自啟動者電腦的訊息。</span><span class="sxs-lookup"><span data-stu-id="f45c7-103">Message flow on a responder computer starts with receiving a message over the Internet from the initiator computer.</span></span> <span data-ttu-id="f45c7-104">其中牽涉將該訊息從 RosettaNet 實作架構 (RNIF) 相容訊息轉換為後端應用程式專屬格式的訊息，然後將訊息傳送到商務營運系統應用程式。</span><span class="sxs-lookup"><span data-stu-id="f45c7-104">It involves converting that message from a RosettaNet Implementation Framework (RNIF)-compliant message to a message in the proprietary format of the back-end application, and then routing the message to the line-of-business application.</span></span>  
  
 <span data-ttu-id="f45c7-105">若交易夥伴介面程序 (PIP) 是單向動作，則唯一的回應是通知信號訊息。</span><span class="sxs-lookup"><span data-stu-id="f45c7-105">If the Partner Interface Process (PIP) is single-action, the only response is an acknowledgement signal message.</span></span> <span data-ttu-id="f45c7-106">如果 PIP 是雙向動作，回應者將處理並傳送回應訊息，隨後接收該回應的確認結果。</span><span class="sxs-lookup"><span data-stu-id="f45c7-106">If the PIP is double-action, the responder will process and send a response message, and subsequently receive an acknowledgment for that response.</span></span>  
  
 <span data-ttu-id="f45c7-107">若 PIP 為非同步，透過網際網路傳送的每個訊息都會使用不同的 HTTP 連線。</span><span class="sxs-lookup"><span data-stu-id="f45c7-107">If the PIP is asynchronous, each message transmission over the Internet occurs on a different HTTP connection.</span></span> <span data-ttu-id="f45c7-108">若 PIP 為同步，每個訊息傳輸會使用相同的連線，程序完成前 HTTP 配接器會一直保留此連線。</span><span class="sxs-lookup"><span data-stu-id="f45c7-108">If the PIP is synchronous, each message transmission occurs on the same connection, which the HTTP adapter holds until the process is complete.</span></span> <span data-ttu-id="f45c7-109">在雙向同步實例中，回應者電腦不會為了回應初始要求訊息而傳送通知給啟動者電腦。</span><span class="sxs-lookup"><span data-stu-id="f45c7-109">In a double-action synchronous scenario, the responder computer does not send an acknowledgement to the initiator computer in response to the initial request message.</span></span> <span data-ttu-id="f45c7-110">回應訊息是做為通知使用。</span><span class="sxs-lookup"><span data-stu-id="f45c7-110">The response message serves as the acknowledgement.</span></span>  
  
## <a name="btarn-components-on-the-responder-computer"></a><span data-ttu-id="f45c7-111">回應者電腦上的 BTARN 元件</span><span class="sxs-lookup"><span data-stu-id="f45c7-111">BTARN Components on the Responder Computer</span></span>  
 <span data-ttu-id="f45c7-112">當訊息流程透過[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]的回應者電腦上，下列元件會處理訊息：</span><span class="sxs-lookup"><span data-stu-id="f45c7-112">As a message flows through [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on the responder computer, the following components will process the message:</span></span>  
  
-   <span data-ttu-id="f45c7-113">RNIFReceive.aspx 頁面</span><span class="sxs-lookup"><span data-stu-id="f45c7-113">RNIFReceive.aspx page</span></span>  
  
-   <span data-ttu-id="f45c7-114">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="f45c7-114">HTTP adapter</span></span>  
  
-   <span data-ttu-id="f45c7-115">接收管線</span><span class="sxs-lookup"><span data-stu-id="f45c7-115">Receive pipeline</span></span>  
  
-   <span data-ttu-id="f45c7-116">回應者公開程序</span><span class="sxs-lookup"><span data-stu-id="f45c7-116">Responder public process</span></span>  
  
-   <span data-ttu-id="f45c7-117">回應者私用程序</span><span class="sxs-lookup"><span data-stu-id="f45c7-117">Responder private process</span></span>  
  
-   <span data-ttu-id="f45c7-118">SQL adapter (SQL 配接器)</span><span class="sxs-lookup"><span data-stu-id="f45c7-118">SQL adapter</span></span>  
  
-   <span data-ttu-id="f45c7-119">傳送管線</span><span class="sxs-lookup"><span data-stu-id="f45c7-119">Send pipeline</span></span>  
  
 <span data-ttu-id="f45c7-120">如需有關這些元件，以及它們如何處理訊息的詳細資訊，請參閱[BTARN 中的訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)。</span><span class="sxs-lookup"><span data-stu-id="f45c7-120">For more information about these components, and how they process a message, see [Message Processing in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md).</span></span>  
  
## <a name="message-flow-on-the-responder-computer"></a><span data-ttu-id="f45c7-121">回應者電腦上的訊息流程</span><span class="sxs-lookup"><span data-stu-id="f45c7-121">Message Flow on the Responder Computer</span></span>  
 <span data-ttu-id="f45c7-122">透過 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 回應者電腦，接收訊息的訊息流程如下：</span><span class="sxs-lookup"><span data-stu-id="f45c7-122">The message flow of a received message through the responder [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] computer is as follows:</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-responder-receive-message-flow.gif "RN3_Responder_Receive_Message_Flow")  
  
1.  <span data-ttu-id="f45c7-123">RNIFReceive aspx 頁面接收來自啟動者的內送訊息。</span><span class="sxs-lookup"><span data-stu-id="f45c7-123">The RNIFReceive aspx page receives the incoming message from the initiator.</span></span>  
  
2.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="f45c7-124"> 將訊息提交給 HTTP 配接器，它會將訊息提交給接收管線。</span><span class="sxs-lookup"><span data-stu-id="f45c7-124"> submits the message to the HTTP adapter, which submits it to the receive pipeline.</span></span>  
  
3.  <span data-ttu-id="f45c7-125">接收管線會針對訊息進行解碼、解譯與合作對象解析，然後轉換訊息為後端商務營運系統應用程式的專屬格式。</span><span class="sxs-lookup"><span data-stu-id="f45c7-125">The receive pipeline decodes, disassembles, and performs party resolution on the message, and then converts the message into the proprietary format of the back-end line-of-business application.</span></span>  
  
4.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="f45c7-126"> 會將訊息傳送至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f45c7-126"> routes the message to the MessageBox database.</span></span>  
  
5.  <span data-ttu-id="f45c7-127">公開程序會處理訊息的 RNIF 標頭。</span><span class="sxs-lookup"><span data-stu-id="f45c7-127">The public process processes the RNIF headers of the message.</span></span>  
  
6.  <span data-ttu-id="f45c7-128">私用程序會處理訊息的服務內容。</span><span class="sxs-lookup"><span data-stu-id="f45c7-128">The private process processes the service content of the message.</span></span> <span data-ttu-id="f45c7-129">它會產生通知，傳回到公開程序、MessageBox 資料庫、傳送管線，再傳回到 HTTP 配接器，透過網際網路傳回給啟動者。</span><span class="sxs-lookup"><span data-stu-id="f45c7-129">It generates an acknowledgement that is returned to the public process, to the MessageBox database, to the send pipeline, and then to the HTTP adapter for return over the Internet to the initiator.</span></span>  
  
7.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="f45c7-130"> 會將訊息傳送至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f45c7-130"> routes the message to the MessageBox database.</span></span>  
  
8.  <span data-ttu-id="f45c7-131">傳送管線會組譯訊息，然後簽署/加密/編碼訊息。</span><span class="sxs-lookup"><span data-stu-id="f45c7-131">The send pipeline assembles, and then signs/encrypts/encodes the message.</span></span>  
  
9. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="f45c7-132"> 會將訊息傳送至 SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="f45c7-132"> routes the message to the SQL adapter.</span></span>  
  
10. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="f45c7-133"> 會將訊息提交到 [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，再到後端的商務營運系統應用程式。</span><span class="sxs-lookup"><span data-stu-id="f45c7-133"> submits the message to [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], and to the line-of-business application on the back end.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f45c7-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f45c7-134">See Also</span></span>  
 <span data-ttu-id="f45c7-135">[BTARN 中的訊息流程](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md) </span><span class="sxs-lookup"><span data-stu-id="f45c7-135">[Message Flow in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md) </span></span>  
 [<span data-ttu-id="f45c7-136">啟動者 BTARN 中的訊息流程</span><span class="sxs-lookup"><span data-stu-id="f45c7-136">Message Flow in the Initiator BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-the-initiator-btarn.md)