---
title: "FileAct 配接器儲存與轉送 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50110bf0-75c2-426c-9833-65c3117224b2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1201a5ab5cb45ceba2622aa1c269404acec910df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-store-and-forward"></a><span data-ttu-id="43326-102">FileAct 配接器儲存與轉送</span><span class="sxs-lookup"><span data-stu-id="43326-102">FileAct Adapter Store and Forward</span></span>
<span data-ttu-id="43326-103">存放區中，順向 (SnF) 模式的檔案傳遞給佇列在傳送時，並從目的地佇列中擷取。</span><span class="sxs-lookup"><span data-stu-id="43326-103">In Store and Forward (SnF) mode, files are delivered to queue at send time, and are retrieved from the queue by the destination.</span></span> <span data-ttu-id="43326-104">中繼會傳回回應的 SWIFTNet 寄件者之前檔案安全地傳遞到目的地。</span><span class="sxs-lookup"><span data-stu-id="43326-104">Intermediate responses are returned by SWIFTNet to the sender until the file is safely delivered to the destination.</span></span>  
  
## <a name="sending-using-snf"></a><span data-ttu-id="43326-105">使用 [SnF 傳送</span><span class="sxs-lookup"><span data-stu-id="43326-105">Sending Using SnF</span></span>  
 <span data-ttu-id="43326-106">如果您建立的單向傳送埠時，配接器 SnF 模式運作，並將訊息傳送至佇列。</span><span class="sxs-lookup"><span data-stu-id="43326-106">If you create a one-way send port, the adapter works in SnF mode and sends messages to the queue.</span></span>  
  
## <a name="receiving-using-snf"></a><span data-ttu-id="43326-107">接收使用 SnF</span><span class="sxs-lookup"><span data-stu-id="43326-107">Receiving Using SnF</span></span>  
 <span data-ttu-id="43326-108">SnF FileAct 推送模式中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="43326-108">SnF FileAct operates in Push mode.</span></span> <span data-ttu-id="43326-109">這是執行階段選項。</span><span class="sxs-lookup"><span data-stu-id="43326-109">This is a run-time option.</span></span>  
  
 <span data-ttu-id="43326-110">才能從佇列擷取訊息，SWIFTNet SnF 應該會收到取得佇列的要求。</span><span class="sxs-lookup"><span data-stu-id="43326-110">Before being able to retrieve messages from a queue, SWIFTNet SnF should receive a request to acquire the queue.</span></span> <span data-ttu-id="43326-111">這會透過叫用跨處理序 COM + 元件接收配接器。</span><span class="sxs-lookup"><span data-stu-id="43326-111">This is accomplished by the receive adapter invoking the out-of-proc COM+ component.</span></span> <span data-ttu-id="43326-112">成功取得之後, 會建立一個工作階段。</span><span class="sxs-lookup"><span data-stu-id="43326-112">After a successful acquire, a session is created.</span></span> <span data-ttu-id="43326-113">然後會在要求中指定的模式中開啟佇列。</span><span class="sxs-lookup"><span data-stu-id="43326-113">The queue will then be opened in the mode specified in the Request.</span></span> <span data-ttu-id="43326-114">所有訊息會都回到發出要求的實體節點。</span><span class="sxs-lookup"><span data-stu-id="43326-114">All messages will be returned to the physical node which issued the request.</span></span>  
  
 <span data-ttu-id="43326-115">訊息傳遞指定的順序 （請注意互動和 FileAct 傳輸可以顛倒，並依照優先順序排列。）不過，在排序的訊息，是取決於它們所儲存的時間。</span><span class="sxs-lookup"><span data-stu-id="43326-115">Messages are delivered in the order specified (note that InterAct and FileAct transmissions can be interspersed, and arranged by priority.) The sequencing of messages, however, is dependent on the time that they were stored.</span></span> <span data-ttu-id="43326-116">FileAct，如果這是檔案存放裝置已完成，不會在它啟動的時間。</span><span class="sxs-lookup"><span data-stu-id="43326-116">In the case of FileAct, this is the time that the file storage is completed, not when it started.</span></span>  
  
### <a name="push-a-file-from-the-queue"></a><span data-ttu-id="43326-117">從佇列推送檔案</span><span class="sxs-lookup"><span data-stu-id="43326-117">Push a File From the Queue</span></span>  
 <span data-ttu-id="43326-118">FileAct 配接器 （伺服器） 接收 HandleFileRequest 從 SWIFTNet，包含佇列、 工作階段和順序的資訊。</span><span class="sxs-lookup"><span data-stu-id="43326-118">The FileAct adapter (server) receives a HandleFileRequest from SWIFTNet, containing the queue, session and sequence information.</span></span> <span data-ttu-id="43326-119">伺服器會回應 HandleFileResponse。</span><span class="sxs-lookup"><span data-stu-id="43326-119">The server responds with a HandleFileResponse.</span></span>  
  
 <span data-ttu-id="43326-120">伺服器接著會發出 FetchFileRequest 和檔案傳遞至伺服器。</span><span class="sxs-lookup"><span data-stu-id="43326-120">The server then issues FetchFileRequest and the file is delivered to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43326-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43326-121">See Also</span></span>  
 <span data-ttu-id="43326-122">[FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="43326-122">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="43326-123">[FileAct 配接器即時的端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="43326-123">[FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span></span>  
 <span data-ttu-id="43326-124">[FileAct 配接器即時區域基本型別](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="43326-124">[FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span></span>  
 <span data-ttu-id="43326-125">[FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="43326-125">[FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="43326-126">[FileAct 配接器檔案和傳輸識別碼](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span><span class="sxs-lookup"><span data-stu-id="43326-126">[FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span></span>  
 <span data-ttu-id="43326-127">[FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span><span class="sxs-lookup"><span data-stu-id="43326-127">[FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span></span>  
 <span data-ttu-id="43326-128">[FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span><span class="sxs-lookup"><span data-stu-id="43326-128">[FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span></span>  
 [<span data-ttu-id="43326-129">FileAct 配接器狀態監視</span><span class="sxs-lookup"><span data-stu-id="43326-129">FileAct Adapter Status Monitoring</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)