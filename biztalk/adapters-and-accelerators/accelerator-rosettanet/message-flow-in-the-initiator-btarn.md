---
title: 訊息啟動者 BTARN 中的流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Accelerator for RosettaNet, message flow
- BTARN, components
- messages, message flow
- initiator BTARN
ms.assetid: 315f3d4c-5e40-4b8e-b135-9da98dc2db1e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 160f40d4dfd0d11a7bd5a5c7c127d62b3e42a2cb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004023"
---
# <a name="message-flow-in-the-initiator-btarn"></a><span data-ttu-id="ad2d8-102">啟動者 BTARN 中的訊息流程</span><span class="sxs-lookup"><span data-stu-id="ad2d8-102">Message Flow in the Initiator BTARN</span></span>
<span data-ttu-id="ad2d8-103">啟動者電腦上的訊息流程是從接收來自後端商務營運系統應用程式的專屬格式訊息開始，</span><span class="sxs-lookup"><span data-stu-id="ad2d8-103">Message flow on an initiator computer starts with receiving a message from the back-end line-of-business application, in its proprietary format.</span></span> <span data-ttu-id="ad2d8-104">其中牽扯將該訊息轉換為 RosettaNet 實作架構 (RNIF) 相容訊息，然後透過網際網路傳送訊息至回應者電腦。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-104">It involves converting that message to a RosettaNet Implementation Framework (RNIF)-compliant message, and then sending the message over the Internet to the responder computer.</span></span>  
  
 <span data-ttu-id="ad2d8-105">若交易夥伴介面程序 (PIP) 是單向動作，則唯一的回應是通知信號訊息。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-105">If the Partner Interface Process (PIP) is single-action, the only response is an acknowledgement signal message.</span></span> <span data-ttu-id="ad2d8-106">如需有關單向動作訊息流程的詳細資訊，請參閱本主題稍後的＜初始訊息的流程＞。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-106">For information about single-action message flow, see "Flow of an Initiated Message" later in this topic.</span></span> <span data-ttu-id="ad2d8-107">如果 PIP 是雙向動作，則除了單向訊息流程之外，啟動者還會接收回應訊息，然後回覆確認。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-107">If the PIP is double-action, the initiator will receive a response message, and reply with an acknowledgement, in addition to the single-action message flow.</span></span>  
  
 <span data-ttu-id="ad2d8-108">若 PIP 為非同步，透過網際網路傳送的每個訊息都會使用不同的 HTTP 連線。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-108">If the PIP is asynchronous, each message transmission over the Internet occurs on a different HTTP connection.</span></span> <span data-ttu-id="ad2d8-109">若 PIP 為同步，每個訊息傳輸會使用相同的連線，程序完成前 HTTP 配接器會一直保留此連線。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-109">If the PIP is synchronous, each message transmission occurs on the same connection, which the HTTP adapter holds until the process is complete.</span></span> <span data-ttu-id="ad2d8-110">在雙向同步實例中，回應者電腦不會為了回應初始要求訊息而傳送通知給啟動者電腦。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-110">In a double-action synchronous scenario, the responder computer does not send an acknowledgement to the initiator computer in response to the initial request message.</span></span> <span data-ttu-id="ad2d8-111">回應訊息是做為通知使用。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-111">The response message serves as the acknowledgement.</span></span>  
  
## <a name="btarn-components-on-the-initiator-computer"></a><span data-ttu-id="ad2d8-112">啟動者電腦上的 BTARN 元件</span><span class="sxs-lookup"><span data-stu-id="ad2d8-112">BTARN Components on the Initiator Computer</span></span>  
 <span data-ttu-id="ad2d8-113">當訊息流程透過啟動者電腦上的 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 時，下列元件將會處理訊息：</span><span class="sxs-lookup"><span data-stu-id="ad2d8-113">As a message flows through [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on the initiator computer, the following components will process the message:</span></span>  
  
- <span data-ttu-id="ad2d8-114">SQL adapter (SQL 配接器)</span><span class="sxs-lookup"><span data-stu-id="ad2d8-114">SQL adapter</span></span>  
  
- <span data-ttu-id="ad2d8-115">XML 接收管線</span><span class="sxs-lookup"><span data-stu-id="ad2d8-115">XML receive pipeline</span></span>  
  
- <span data-ttu-id="ad2d8-116">啟動者私用程序</span><span class="sxs-lookup"><span data-stu-id="ad2d8-116">Initiator private process</span></span>  
  
- <span data-ttu-id="ad2d8-117">啟動者公開程序</span><span class="sxs-lookup"><span data-stu-id="ad2d8-117">Initiator public process</span></span>  
  
- <span data-ttu-id="ad2d8-118">XML 傳送管線</span><span class="sxs-lookup"><span data-stu-id="ad2d8-118">XML send pipeline</span></span>  
  
- <span data-ttu-id="ad2d8-119">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="ad2d8-119">HTTP adapter</span></span>  
  
- <span data-ttu-id="ad2d8-120">RNIFSend.aspx 頁面</span><span class="sxs-lookup"><span data-stu-id="ad2d8-120">RNIFSend.aspx page</span></span>  
  
  <span data-ttu-id="ad2d8-121">如需有關這些元件，以及它們如何處理訊息的詳細資訊，請參閱 < [BTARN 中的訊息處理](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-121">For more information about these components, and how they process a message, see [Message Processing in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md).</span></span>  
  
## <a name="flow-of-an-initiated-message"></a><span data-ttu-id="ad2d8-122">初始訊息的流程</span><span class="sxs-lookup"><span data-stu-id="ad2d8-122">Flow of an Initiated Message</span></span>  
 <span data-ttu-id="ad2d8-123">下列步驟描述初始訊息透過啟動者 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 電腦的訊息流程。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-123">The following steps describe the message flow of an initiated message through the initiator [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] computer.</span></span> <span data-ttu-id="ad2d8-124">下圖顯示這個程序。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-124">The following figure shows this process.</span></span>  
  
 <span data-ttu-id="ad2d8-125">![](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-initiator-send-message-flow.gif "RN3_Initiator_Send_Message_Flow")</span><span class="sxs-lookup"><span data-stu-id="ad2d8-125">![](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-initiator-send-message-flow.gif "RN3_Initiator_Send_Message_Flow")</span></span>  
  
1. <span data-ttu-id="ad2d8-126">特定業務應用程式將訊息傳送給 Microsoft [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-126">The line-of-business application sends the message to Microsoft [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].</span></span>  
  
2. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="ad2d8-127"> 從 [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫傳送訊息至 SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-127"> sends the message from the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database to the SQL adapter.</span></span>  
  
3. <span data-ttu-id="ad2d8-128">XML 接收管線對訊息執行簡單的 XML 驗證。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-128">The XML receive pipeline does simple XML validation of the message.</span></span>  
  
4. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ad2d8-129"> 會將訊息傳送至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-129"> routes the message to the MessageBox database.</span></span>  
  
5. <span data-ttu-id="ad2d8-130">私用程序會處理訊息的服務內容。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-130">The private process processes the service content of the message.</span></span>  
  
6. <span data-ttu-id="ad2d8-131">公開程序會處理訊息的 RNIF 標頭。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-131">The public process processes the RNIF headers of the message.</span></span>  
  
7. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="ad2d8-132"> 會將訊息傳回至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-132"> routes the message back to the MessageBox database.</span></span>  
  
8. <span data-ttu-id="ad2d8-133">傳送管線會執行組件，並簽署/加密/編碼訊息。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-133">The send pipeline performs assembly and signing/encryption/encoding of the message.</span></span>  
  
9. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="ad2d8-134"> 會將訊息傳送至 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-134"> routes the message to the HTTP adapter.</span></span>  
  
10. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="ad2d8-135"> 會將訊息傳送至 RNIFSend.aspx 頁面，此頁面會透過網際網路傳送訊息至目的地。</span><span class="sxs-lookup"><span data-stu-id="ad2d8-135"> routes the message to the RNIFSend.aspx page, which sends it over the Internet to its destination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad2d8-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad2d8-136">See Also</span></span>  
 <span data-ttu-id="ad2d8-137">[BTARN 中的訊息流程](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md) </span><span class="sxs-lookup"><span data-stu-id="ad2d8-137">[Message Flow in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md) </span></span>  
 <span data-ttu-id="ad2d8-138">[回應者 BTARN 中的訊息流程](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-the-responder-btarn.md) </span><span class="sxs-lookup"><span data-stu-id="ad2d8-138">[Message Flow in the Responder BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-the-responder-btarn.md) </span></span>  
 [<span data-ttu-id="ad2d8-139">BTARN 中的訊息處理</span><span class="sxs-lookup"><span data-stu-id="ad2d8-139">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)