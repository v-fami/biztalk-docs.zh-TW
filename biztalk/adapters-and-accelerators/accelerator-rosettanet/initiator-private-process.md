---
title: 啟動者私用程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- line-of-business applications (LOBs)
- messages, private processes
- erros
- LOBs
- messages, message flow
- private processes, initiator
- private processes, message flow
- private processes, errors
ms.assetid: 8444a5c8-445a-4bbd-a793-a16816fcb397
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 569d176a15ba5236d5f44d87406d9bbc0a19fca9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22211022"
---
# <a name="initiator-private-process"></a><span data-ttu-id="337c3-102">啟動者私用程序</span><span class="sxs-lookup"><span data-stu-id="337c3-102">Initiator Private Process</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="337c3-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]會使用啟動者私用程序 (PrivateInitiator.odx) 來處理啟動者電腦上的服務內容。</span><span class="sxs-lookup"><span data-stu-id="337c3-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses the initiator private process (PrivateInitiator.odx) to process service content at an initiator computer.</span></span> <span data-ttu-id="337c3-104">這包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="337c3-104">This includes the following:</span></span>  
  
-   <span data-ttu-id="337c3-105">建立原始訊息的服務內容，並在送至交易夥伴的電腦途中，將訊息傳送到公開程序</span><span class="sxs-lookup"><span data-stu-id="337c3-105">Creating the service content of an original message and routing the message to the public process, in route to the trading partner</span></span>  
  
-   <span data-ttu-id="337c3-106">處理傳回的信號訊息並傳送到商務營運系統 (LOB) 應用程式</span><span class="sxs-lookup"><span data-stu-id="337c3-106">Processing a return signal message and routing it to the line-of-business (LOB) application</span></span>  
  
-   <span data-ttu-id="337c3-107">如果是雙向動作 PIP，處理回應傳回訊息並傳送到 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="337c3-107">In the case of a double-action PIP, processing a response return message and routing it to the LOB application.</span></span>  
  
 <span data-ttu-id="337c3-108">私用程序也會設定中繼資料，並新增任何附件。</span><span class="sxs-lookup"><span data-stu-id="337c3-108">The private process also sets metadata and adds any attachments.</span></span> <span data-ttu-id="337c3-109">私用程序傳送外寄訊息到公開程序，該程序會新增 RosettaNet 實作架構 (RNIF) 標頭並準備訊息進行傳送。</span><span class="sxs-lookup"><span data-stu-id="337c3-109">The private process routes outgoing messages to the public process, which adds RosettaNet Implementation Framework (RNIF) headers and prepares the message for transmission.</span></span> <span data-ttu-id="337c3-110">在前往 LOB 應用程式的途中，私用程序會傳送內送訊息到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessagesToLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="337c3-110">The private process routes incoming messages to the MessagesToLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database, in route to the LOB application.</span></span>  
  
 <span data-ttu-id="337c3-111">此私用程序自動化使用 3A2 與 3A4 交易夥伴介面程序 (PIP) 的訂購查詢/訂單程序，</span><span class="sxs-lookup"><span data-stu-id="337c3-111">This private process automates the purchase query/purchase order processes that use 3A2 and 3A4 Partner Interface Processes (PIPs).</span></span> <span data-ttu-id="337c3-112">它也會處理任何其他 PIP 訊息。</span><span class="sxs-lookup"><span data-stu-id="337c3-112">It also handles any other PIP messages.</span></span> <span data-ttu-id="337c3-113">您可以依照自己的特定商務程序自訂私用程序。</span><span class="sxs-lookup"><span data-stu-id="337c3-113">You can customize the private process for your specific business processes.</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="337c3-114">訊息流程</span><span class="sxs-lookup"><span data-stu-id="337c3-114">Message Flow</span></span>  
 <span data-ttu-id="337c3-115">透過啟動者私用程序的訊息流程如下：</span><span class="sxs-lookup"><span data-stu-id="337c3-115">The message flow through the initiator private process is as follows:</span></span>  
  
1.  <span data-ttu-id="337c3-116">啟動者私用程序從 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessagesFromLOB 資料表接收原始訊息。</span><span class="sxs-lookup"><span data-stu-id="337c3-116">The initiator private process receives the original message from the MessagesFromLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database.</span></span> <span data-ttu-id="337c3-117">後端 LOB 應用程式傳送訊息到此資料表。</span><span class="sxs-lookup"><span data-stu-id="337c3-117">The back-end LOB application routes the message to this table.</span></span>  
  
2.  <span data-ttu-id="337c3-118">私用程序準備已初始化訊息的服務內容，然後傳送到公開程序。</span><span class="sxs-lookup"><span data-stu-id="337c3-118">The private process prepares the service content of an initiated message, and sends it to the public process.</span></span>  
  
3.  <span data-ttu-id="337c3-119">接著，啟動者私用程序進入等候狀態，接聽傳回信號。</span><span class="sxs-lookup"><span data-stu-id="337c3-119">The initiator private process then enters a wait state, listening for a return signal.</span></span>  
  
4.  <span data-ttu-id="337c3-120">私用程序接收到公開程序的傳回信號時，會建構信號訊息，然後在送至 LOB 應用程式的途中，將信號傳送到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫的 MessagesToLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="337c3-120">Upon receiving a return signal from the public process, the private process constructs a signal message, and sends the signal to the MessagesToLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database, in route to the LOB application.</span></span>  
  
5.  <span data-ttu-id="337c3-121">私用程序傳送通知到 LOB 應用程式，而 LOB 應用程式會將信號訊息放置在 MessagesToLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="337c3-121">The private process sends a notification to the LOB application that it put the signal message in the MessagesToLOB table.</span></span>  
  
6.  <span data-ttu-id="337c3-122">如果 RNIF 是 1.1 版，私用程序會等候接收通知信號訊息。</span><span class="sxs-lookup"><span data-stu-id="337c3-122">If the RNIF version is 1.1, the private process waits for an acceptance acknowledgement signal message.</span></span> <span data-ttu-id="337c3-123">如果接收到信號，私用程序會建構信號訊息，並在送至 LOB 應用程式的途中，將信號傳送到 MessagesToLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="337c3-123">If it receives the signal, it constructs the signal message, and sends the signal to the MessagesToLOB table, in route to the LOB application.</span></span>  
  
7.  <span data-ttu-id="337c3-124">如果原始訊息是單向動作訊息，私用程序傳回信號訊息到 LOB 應用程式後就完成了。</span><span class="sxs-lookup"><span data-stu-id="337c3-124">If the original message(s) was a single-action message, the private process is complete after it has returned the signal message to the LOB application.</span></span> <span data-ttu-id="337c3-125">如果原始訊息是雙向動作訊息，私用程序會接聽回應訊息。</span><span class="sxs-lookup"><span data-stu-id="337c3-125">If the original message was a double-action message, the private process listens for a response message.</span></span>  
  
8.  <span data-ttu-id="337c3-126">如果私用程序從公開程序接收回應訊息，便會以 LOB 應用程式的格式建構回應訊息。</span><span class="sxs-lookup"><span data-stu-id="337c3-126">If the private process receives a response message from the public process, it constructs a response message in the format of the LOB application.</span></span> <span data-ttu-id="337c3-127">這包括取得 LOB 訊息範本、序列化 XML 服務內容以及載入 XML 訊息部分到 LOB 訊息。</span><span class="sxs-lookup"><span data-stu-id="337c3-127">This involves getting the LOB message template, serializing the XML service content, and loading the XML message parts into the LOB message.</span></span>  
  
9. <span data-ttu-id="337c3-128">私用程序會將訊息傳送到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] 資料庫中的 MessagesToLOB 資料表。</span><span class="sxs-lookup"><span data-stu-id="337c3-128">The private process routes the message to the MessagesToLOB table in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database.</span></span>  
  
10. <span data-ttu-id="337c3-129">如果回應訊息含有附件，私用程序會呼叫 AttachmentHelper 工具來處理附件。</span><span class="sxs-lookup"><span data-stu-id="337c3-129">If the response message has an attachment, the private process calls the AttachmentHelper tool to process the attachment.</span></span>  
  
11. <span data-ttu-id="337c3-130">私用程序傳送通知到 LOB 應用程式，而 LOB 應用程式會將回應訊息放置在 MessagesToLOB 資料表，這樣程序就完成了。</span><span class="sxs-lookup"><span data-stu-id="337c3-130">The private process sends a notification to the LOB application that it put the response message in the MessagesToLOB table, and then is complete.</span></span>  
  
## <a name="handling-of-incorrect-messages"></a><span data-ttu-id="337c3-131">不正確訊息的處理方式</span><span class="sxs-lookup"><span data-stu-id="337c3-131">Handling of Incorrect Messages</span></span>  
 <span data-ttu-id="337c3-132">當啟動者私用程序從 LOB 應用程式接收不正確的訊息時，私用程序會將例外狀況訊息傳回至 LOB。</span><span class="sxs-lookup"><span data-stu-id="337c3-132">When the initiator private process receives an incorrect message from the LOB application, the private process sends an exception message back to the LOB.</span></span> <span data-ttu-id="337c3-133">然而，私用程序不會將不正確的訊息發佈到 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] BizTalk 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="337c3-133">However, the private process does not post the incorrect message in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] BizTalk Administration Console.</span></span> <span data-ttu-id="337c3-134">因此，您無法從 BizTalk 管理主控台檢視不正確的訊息。</span><span class="sxs-lookup"><span data-stu-id="337c3-134">Therefore, you are not able to view the incorrect message in BizTalk Administration Console.</span></span> <span data-ttu-id="337c3-135">您可以使用例外狀況訊息存取不正確的訊息，以判斷何者為不正確的訊息，再從 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA 資料庫的 MessagesFromLOB 資料表存取不正確的訊息。</span><span class="sxs-lookup"><span data-stu-id="337c3-135">You can use the exception message to access the incorrect message to determine which message was incorrect, and then access the incorrect message in the MessagesFromLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA database.</span></span> <span data-ttu-id="337c3-136">不過，此訊息可能與私用程序所使用的訊息不同，因為用來處理訊息的預存程序和配接器會編輯訊息。</span><span class="sxs-lookup"><span data-stu-id="337c3-136">However, this message may not be the same as the message that the private process consumed, because the stored process and adapter used to process the message edit it.</span></span> <span data-ttu-id="337c3-137">這兩者會將根項目與命名空間新增至訊息。</span><span class="sxs-lookup"><span data-stu-id="337c3-137">They add a root element and namespace to the message.</span></span> <span data-ttu-id="337c3-138">預存程序和配接器可能還會傳回多筆記錄。</span><span class="sxs-lookup"><span data-stu-id="337c3-138">The stored process and adapter possibly return multiple records.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="337c3-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="337c3-139">See Also</span></span>  
 <span data-ttu-id="337c3-140">[私用程序](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md) </span><span class="sxs-lookup"><span data-stu-id="337c3-140">[Private Processes](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md) </span></span>  
 <span data-ttu-id="337c3-141">[回應者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md) </span><span class="sxs-lookup"><span data-stu-id="337c3-141">[Responder Private Process](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md) </span></span>  
 <span data-ttu-id="337c3-142">[協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span><span class="sxs-lookup"><span data-stu-id="337c3-142">[Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span></span>  
 [<span data-ttu-id="337c3-143">PrivateInitiator 範例</span><span class="sxs-lookup"><span data-stu-id="337c3-143">PrivateInitiator Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)