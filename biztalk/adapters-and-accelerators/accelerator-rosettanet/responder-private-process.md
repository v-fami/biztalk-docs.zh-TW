---
title: "回應者私用程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- line-of-business applications (LOBs)
- messages, private processes
- LOBs
- messages, message flow
- private processes, responder
- private processes, message flow
ms.assetid: 69b58320-977c-44d2-a7d6-f986213aecf2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8ba5ca38eb64859182242c944d260c9db15c880
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="responder-private-process"></a><span data-ttu-id="94860-102">回應者私用程序</span><span class="sxs-lookup"><span data-stu-id="94860-102">Responder Private Process</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="94860-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]會使用回應者私用程序 (PrivateResponder.odx) 來處理回應者電腦上的服務內容。</span><span class="sxs-lookup"><span data-stu-id="94860-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses the responder private process (PrivateResponder.odx) to process service content at a responder computer.</span></span> <span data-ttu-id="94860-104">這包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="94860-104">This includes the following:</span></span>  
  
-   <span data-ttu-id="94860-105">將內送訊息傳送到商務營運系統 (LOB) 應用程式</span><span class="sxs-lookup"><span data-stu-id="94860-105">Routing an incoming message to the line-of-business (LOB) application</span></span>  
  
-   <span data-ttu-id="94860-106">在前往回應者電腦的途中，建立回應訊息的服務內容並將訊息傳送到公開程序</span><span class="sxs-lookup"><span data-stu-id="94860-106">Creating the service content of a response message and routing the message to the public process, in route to the responder computer</span></span>  
  
 <span data-ttu-id="94860-107">私用程序也會設定中繼資料，並新增任何附件到回應訊息。</span><span class="sxs-lookup"><span data-stu-id="94860-107">The private process also sets metadata and adds any attachments to the response message.</span></span> <span data-ttu-id="94860-108">私用程序會傳送外寄訊息到回應者公開程序，該程序會新增 RosettaNet 實作架構 (RNIF) 標頭並準備訊息進行傳輸。</span><span class="sxs-lookup"><span data-stu-id="94860-108">The private process routes outgoing messages to the responder public process, which adds RosettaNet Implementation Framework (RNIF) headers and prepares the message for transmission.</span></span> <span data-ttu-id="94860-109">在前往 LOB 應用程式的途中，私用程序會傳送內送訊息到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessagesToLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="94860-109">The private process routes incoming messages to the MessagesToLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database, in route to the LOB application.</span></span>  
  
 <span data-ttu-id="94860-110">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含兩個回應者私用程序範例，您可以根據自己的特定商務程序進行自訂。</span><span class="sxs-lookup"><span data-stu-id="94860-110">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes two responder private process samples that you can customize for your specific business processes.</span></span> <span data-ttu-id="94860-111">第一個是 PrivateResponder 程序範例，其中包含 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 所安裝回應者私用程序的程式碼。</span><span class="sxs-lookup"><span data-stu-id="94860-111">The first is the PrivateResponder process sample that contains the code for the responder private process installed by [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="94860-112">如需詳細資訊，請參閱[PrivateResponder 範例](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="94860-112">For more information, see [PrivateResponder Sample](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md).</span></span>  
  
 <span data-ttu-id="94860-113">第二個範例是 PIP3A4PrivateResponder 私用程序，此範例會自動化使用 3A2 與 3A4 交易夥伴介面程序 (PIP) 的訂購查詢/訂單程序。</span><span class="sxs-lookup"><span data-stu-id="94860-113">The second sample is the PIP3A4PrivateResponder private process sample that automates the purchase query/purchase order processes that use 3A2 and 3A4 Partner Interface Processes (PIPs).</span></span> <span data-ttu-id="94860-114">它也會處理任何其他 PIP 訊息。</span><span class="sxs-lookup"><span data-stu-id="94860-114">It also handles any other PIP messages.</span></span> <span data-ttu-id="94860-115">如需詳細資訊，請參閱[3A4 私用回應者協調流程使用商務規則](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)。</span><span class="sxs-lookup"><span data-stu-id="94860-115">For more information, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="94860-116">訊息流程</span><span class="sxs-lookup"><span data-stu-id="94860-116">Message Flow</span></span>  
 <span data-ttu-id="94860-117">透過回應者私用程序的訊息流程如下：</span><span class="sxs-lookup"><span data-stu-id="94860-117">The message flow through the responder private process is as follows:</span></span>  
  
1.  <span data-ttu-id="94860-118">在前往啟動者電腦的途中，回應者私用程序從回應者公開程序接收原始內送訊息。</span><span class="sxs-lookup"><span data-stu-id="94860-118">The responder private process receives the original incoming message from the responder public process, in route from the initiator computer.</span></span>  
  
2.  <span data-ttu-id="94860-119">私用程序建構 LOB 應用程式訊息。</span><span class="sxs-lookup"><span data-stu-id="94860-119">The private process constructs the LOB application message.</span></span> <span data-ttu-id="94860-120">這包括取得 LOB 訊息範本、序列化 XML 服務內容以及載入 XML 訊息部分到 LOB 訊息。</span><span class="sxs-lookup"><span data-stu-id="94860-120">This involves getting the LOB message template, serializing the XML service content, and loading the XML message parts into the LOB message.</span></span>  
  
3.  <span data-ttu-id="94860-121">在前往 LOB 應用程式的途中，私用程序會傳送訊息到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessagesFromLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="94860-121">The private process routes the message to the MessagesFromLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database, in route to the back-end LOB application.</span></span>  
  
4.  <span data-ttu-id="94860-122">如果原始訊息有附件，私用程序會呼叫 AttachmentHelper 元件來處理附件。</span><span class="sxs-lookup"><span data-stu-id="94860-122">If the original message has an attachment, the private process calls the AttachmentHelper component to process the attachment.</span></span>  
  
5.  <span data-ttu-id="94860-123">私用程序傳送通知到 LOB 應用程式，而 LOB 應用程式已將回應訊息儲存在 MessagesToLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="94860-123">The private process sends a notification to the LOB application that it saved the response message in the MessagesToLOB table.</span></span>  
  
6.  <span data-ttu-id="94860-124">如果訊息是單向動作訊息，私用程序就完成了。</span><span class="sxs-lookup"><span data-stu-id="94860-124">If the message is a single-action message, the private process is complete.</span></span>  
  
7.  <span data-ttu-id="94860-125">如果訊息是雙向動作訊息，私用程序會接聽來自 LOB 應用程式的回應。</span><span class="sxs-lookup"><span data-stu-id="94860-125">If the message is a double-action message, the private process listens for a response from the LOB application.</span></span>  
  
8.  <span data-ttu-id="94860-126">當私用程序接收來自 LOB 應用程式的回應時，會建構回應訊息，並傳送訊息到公開程序。</span><span class="sxs-lookup"><span data-stu-id="94860-126">When the private process receives the response from the LOB application, it constructs a response message, and sends the message to the public process.</span></span>  
  
9. <span data-ttu-id="94860-127">私用程序會等候來自公開程序的信號。</span><span class="sxs-lookup"><span data-stu-id="94860-127">The private process waits for the signal from the public process.</span></span> <span data-ttu-id="94860-128">如果收到信號，便會建構 LOB 信號訊息並傳送到 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="94860-128">If it receives the signal, it constructs the LOB signal message and sends it to the LOB application.</span></span> <span data-ttu-id="94860-129">如果 RNIF 是 1.1 版，私用程序將接聽第二個通知信號，而且在接收該信號時，將建構 LOB 信號訊息並傳送到 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="94860-129">If the RNIF version is 1.1, the private process will listen for a second acknowledgement signal, and upon receiving it, will construct the LOB signal message and send it to the LOB application.</span></span> <span data-ttu-id="94860-130">私用程序每次傳送信號訊息之後都會通知 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="94860-130">The private process notifies the LOB application after sending each signal message.</span></span>  
  
10. <span data-ttu-id="94860-131">從啟動者傳送過來的途中，如果私用程序從公開程序接收到「失敗通知」(NoF) 訊息，便會建構 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Exception 訊息並傳送到 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="94860-131">If the private process receives a Notification of Failure (NoF) message from the public process, in route from the initiator, the private process constructs a "[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Exception" message, and sends it to the LOB application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94860-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94860-132">See Also</span></span>  
 <span data-ttu-id="94860-133">[私用程序](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md) </span><span class="sxs-lookup"><span data-stu-id="94860-133">[Private Processes](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md) </span></span>  
 <span data-ttu-id="94860-134">[啟動者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md) </span><span class="sxs-lookup"><span data-stu-id="94860-134">[Initiator Private Process](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md) </span></span>  
 <span data-ttu-id="94860-135">[協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span><span class="sxs-lookup"><span data-stu-id="94860-135">[Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span></span>  
 [<span data-ttu-id="94860-136">PrivateResponder 範例</span><span class="sxs-lookup"><span data-stu-id="94860-136">PrivateResponder Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)