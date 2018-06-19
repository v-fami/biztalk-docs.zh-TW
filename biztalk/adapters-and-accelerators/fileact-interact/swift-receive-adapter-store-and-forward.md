---
title: SWIFT 接收配接器儲存與轉送 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11eeb335-366b-4b29-9078-de9396b258ca
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 315b9bbe6985bbce5ccb44d8d4846b18730f292b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224470"
---
# <a name="swift-receive-adapter-store-and-forward"></a><span data-ttu-id="56aa8-102">SWIFT 接收配接器儲存與轉送</span><span class="sxs-lookup"><span data-stu-id="56aa8-102">SWIFT Receive Adapter Store and Forward</span></span>
<span data-ttu-id="56aa8-103">接收配接器會接收來自 SWIFT 商店 和 正向 (SnF) 佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="56aa8-103">The receive adapter receives messages from the SWIFT store and forward (SnF) queue.</span></span> <span data-ttu-id="56aa8-104">若要從佇列接收訊息，配接器必須開啟工作階段與 SnF 佇列。</span><span class="sxs-lookup"><span data-stu-id="56aa8-104">To receive messages from the queue, the adapter must open a session with the SnF queue.</span></span> <span data-ttu-id="56aa8-105">若要開啟佇列，它必須有專用的用戶端處理序所建立的佇列的工作階段。</span><span class="sxs-lookup"><span data-stu-id="56aa8-105">To open the queue, it must have a dedicated client process that establishes the session with the queue.</span></span> <span data-ttu-id="56aa8-106">在設計中，此程序會實作為 COM plus 跨處理序元件。</span><span class="sxs-lookup"><span data-stu-id="56aa8-106">In the design, this process is implemented as a COM plus out-of-proc component.</span></span>  
  
## <a name="push-session-store-and-forward-sequence"></a><span data-ttu-id="56aa8-107">工作階段存放區和正向順序推入</span><span class="sxs-lookup"><span data-stu-id="56aa8-107">Push session store and forward sequence</span></span>  
 <span data-ttu-id="56aa8-108">下列清單說明 商店 和 正向順序。</span><span class="sxs-lookup"><span data-stu-id="56aa8-108">The following list describes the store and forward sequence.</span></span>  
  
1.  <span data-ttu-id="56aa8-109">啟動伺服器應用程式所處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="56aa8-109">Start the server application that processes the messages.</span></span>  
  
2.  <span data-ttu-id="56aa8-110">伺服器處理序，開啟第一個與 Sw:HandleInitRequest SwCallback 期間為基本輸入所需的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="56aa8-110">The server process opens the required security contexts during the first SwCallback with the Sw:HandleInitRequest as an input primitive.</span></span>  
  
3.  <span data-ttu-id="56aa8-111">伺服器會回應與任一個或兩個 Sw:CryptoMode Sw:FACryptoMode 設為進階 Sw:HandleInitRequest。</span><span class="sxs-lookup"><span data-stu-id="56aa8-111">The server responds to the Sw:HandleInitRequest with either or both Sw:CryptoMode and Sw:FACryptoMode set to Advanced.</span></span>  
  
     <span data-ttu-id="56aa8-112">伺服器現在已準備好開始處理傳入要求。</span><span class="sxs-lookup"><span data-stu-id="56aa8-112">The server is now ready to start processing incoming requests.</span></span>  
  
4.  <span data-ttu-id="56aa8-113">若要從佇列啟動的訊息傳遞，用戶端處理序啟動推入工作階段。</span><span class="sxs-lookup"><span data-stu-id="56aa8-113">To start the delivery of messages from a queue, a client process starts a push session.</span></span> <span data-ttu-id="56aa8-114">根據配接器組態 （push 模式），則接收配接器會繁衍稱為 SnFQueueManager.exe 取得 push 模式中的佇列的用戶端處理序。</span><span class="sxs-lookup"><span data-stu-id="56aa8-114">Based on the adapter configuration (push mode), the receive adapter spawns a client process called SnFQueueManager.exe to acquire the queue in push mode.</span></span>  
  
5.  <span data-ttu-id="56aa8-115">SwCall() 執行 Sw:AcquireSnFRequest （內 Sw:ExchangeSnFRequest) 做為輸入的基本類型。</span><span class="sxs-lookup"><span data-stu-id="56aa8-115">An SwCall() runs with Sw:AcquireSnFRequest (within the Sw:ExchangeSnFRequest) as an input primitive.</span></span> <span data-ttu-id="56aa8-116">此要求指定的佇列會啟動工作階段 （如果 SwSec:AuthorisationContext 具有所需的 RBAC 角色）。</span><span class="sxs-lookup"><span data-stu-id="56aa8-116">This request starts a session with the queue indicated (if the SwSec:AuthorisationContext has the required RBAC role).</span></span>  
  
6.  <span data-ttu-id="56aa8-117">緊接在 Sw:AcquireStatus 回應與 「 已接受 」，SWIFTNet SnF 會開始將訊息傳送至伺服器中取得所指定。</span><span class="sxs-lookup"><span data-stu-id="56aa8-117">Immediately after responding with “Accepted” in the Sw:AcquireStatus, SWIFTNet SnF starts sending messages to the server as specified in the acquire.</span></span> <span data-ttu-id="56aa8-118">如果尚未啟動接收配接器，訊息就會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="56aa8-118">If the receive adapter was not yet started, messages get exceptions.</span></span> <span data-ttu-id="56aa8-119">（這是為什麼一定要有在接收配接器已啟動。）</span><span class="sxs-lookup"><span data-stu-id="56aa8-119">(That is why it is important to have the receive adapters already started).</span></span>  
  
7.  <span data-ttu-id="56aa8-120">SWIFTNet SnF 啟動推入數目 （最上層視窗大小） 的訊息。</span><span class="sxs-lookup"><span data-stu-id="56aa8-120">SWIFTNet SnF starts pushing a number of messages (up to the window size).</span></span>  
  
8.  <span data-ttu-id="56aa8-121">針對每個認可的訊息，推入新的訊息 （如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="56aa8-121">For every message acknowledged, a new message (if any) is pushed.</span></span>  
  
9. <span data-ttu-id="56aa8-122">用戶端處理序 (SnFQueueManager.exe) 已完成其工作，並可立即終止。</span><span class="sxs-lookup"><span data-stu-id="56aa8-122">The client process (SnFQueueManager.exe) has done its job and can now terminate.</span></span> <span data-ttu-id="56aa8-123">處理程序發出 SwSec:DestroyContextRequest，清除 開啟 安全性內容。</span><span class="sxs-lookup"><span data-stu-id="56aa8-123">The process issues SwSec:DestroyContextRequest, which cleans up the open security contexts.</span></span> <span data-ttu-id="56aa8-124">Sw:TermRequest 後會結束處理程序。</span><span class="sxs-lookup"><span data-stu-id="56aa8-124">After the Sw:TermRequest, the process exits.</span></span>  
  
### <a name="message-correlation"></a><span data-ttu-id="56aa8-125">訊息相互關聯</span><span class="sxs-lookup"><span data-stu-id="56aa8-125">Message Correlation</span></span>  
 <span data-ttu-id="56aa8-126">RequestRef 欄位會保留並替換回應訊息中，接收配接器。</span><span class="sxs-lookup"><span data-stu-id="56aa8-126">The RequestRef field is preserved and substituted back in the response messages by the receive adapter.</span></span> <span data-ttu-id="56aa8-127">這可確保內送訊息和回應訊息之間的端對端相互關聯</span><span class="sxs-lookup"><span data-stu-id="56aa8-127">This ensures end to end correlation between the incoming message and the response message</span></span>  
  
### <a name="duplicate-processing"></a><span data-ttu-id="56aa8-128">重複處理</span><span class="sxs-lookup"><span data-stu-id="56aa8-128">Duplicate processing</span></span>  
 <span data-ttu-id="56aa8-129">如果接收 FileAct 要求，以及配接器執行個體接收訊息可能重複的指示器節點之後，它必須檢查以查看是否已成功完成的參考的傳送，或已失敗，並採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="56aa8-129">If receiving a FileAct request, and the adapter instance receives a message with a Possible Duplicate Indicator node, then it must check to see if the referenced transfer has already completed successfully or if it has failed, and take the appropriate action.</span></span> <span data-ttu-id="56aa8-130">如果檔案傳輸已開始然後配接器傳輸會將狀態更新為 「 Duplicate 」 否則便會更新它做為 「 已接受 」。</span><span class="sxs-lookup"><span data-stu-id="56aa8-130">If the file transfer has already taken place then the adapter updates the transfer status as “Duplicate” otherwise it updates it as “Accepted.”</span></span>  
  
### <a name="acknowledgments"></a><span data-ttu-id="56aa8-131">致謝</span><span class="sxs-lookup"><span data-stu-id="56aa8-131">Acknowledgments</span></span>  
 <span data-ttu-id="56aa8-132">如果傳送者要求 FileAct 要求通知，配接器會檢查有檔案傳送完成事件，並產生收條之後正在驗證檔案的摘要值。</span><span class="sxs-lookup"><span data-stu-id="56aa8-132">If the sender requests an acknowledgement for a FileAct request, the adapter checks for the file transfer completion event and generates the acknowledgement after verifying the file digest value.</span></span> <span data-ttu-id="56aa8-133">配接器至 BizTalk 傳送配接器拾取它，並將其傳送給傳送者傳送通知訊息。</span><span class="sxs-lookup"><span data-stu-id="56aa8-133">The adapter sends the acknowledgement message to BizTalk for the send adapter to pick it up and send it to the sender.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56aa8-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56aa8-134">See Also</span></span>  
 <span data-ttu-id="56aa8-135">[SWIFT 接收配接器架構](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="56aa8-135">[SWIFT Receive Adapter Architecture](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span></span>  
 <span data-ttu-id="56aa8-136">[SWIFT 接收配接器 URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span><span class="sxs-lookup"><span data-stu-id="56aa8-136">[SWIFT Receive Adapter URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span></span>  
 <span data-ttu-id="56aa8-137">[SWIFT 接收配接器初始化](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md) </span><span class="sxs-lookup"><span data-stu-id="56aa8-137">[SWIFT Receive Adapter Initialization](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md) </span></span>  
 <span data-ttu-id="56aa8-138">[SWIFT 接收配接器的安全性內容](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md) </span><span class="sxs-lookup"><span data-stu-id="56aa8-138">[SWIFT Receive Adapter Security Context](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md) </span></span>  
 [<span data-ttu-id="56aa8-139">SWIFT 接收配接器同步與延遲模式</span><span class="sxs-lookup"><span data-stu-id="56aa8-139">SWIFT Receive Adapter Synchronous and Deferred Modes</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md)