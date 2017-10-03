---
title: "FileAct 配接器的即時本機原型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef4da4f8-3de2-4d35-8f8a-1e12937e52a1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bcc0f1d093d56b8cd4580ef068007d02aab6346f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-real-time-local-primitives"></a><span data-ttu-id="45701-102">FileAct 配接器即時區域基本型別</span><span class="sxs-lookup"><span data-stu-id="45701-102">FileAct Adapter Real-Time Local Primitives</span></span>
<span data-ttu-id="45701-103">區域基本型別牽涉到兩個訊息，這會在用戶端 SWIFTNet 連結 (SNL) 和本機 FileAct 子系統之間交換。</span><span class="sxs-lookup"><span data-stu-id="45701-103">Local primitives involve two messages each, which are exchanged between the client SWIFTNet Link (SNL) and the local FileAct subsystem.</span></span>  
  
 <span data-ttu-id="45701-104">下圖顯示 FileAct 區域基本型別。</span><span class="sxs-lookup"><span data-stu-id="45701-104">The following figure shows the FileAct local primitives.</span></span>  
  
 <span data-ttu-id="45701-105">![FileAct 區域基本型別](../../adapters-and-accelerators/fileact-interact/media/67ca0c3b-3c81-401d-87cb-473c68cae63f.gif "67ca0c3b-3c81-401d-87cb-473c68cae63f")</span><span class="sxs-lookup"><span data-stu-id="45701-105">![FileAct local primitives](../../adapters-and-accelerators/fileact-interact/media/67ca0c3b-3c81-401d-87cb-473c68cae63f.gif "67ca0c3b-3c81-401d-87cb-473c68cae63f")</span></span>  
  
## <a name="get-status-for-a-single-transfer"></a><span data-ttu-id="45701-106">取得單一傳輸中的狀態</span><span class="sxs-lookup"><span data-stu-id="45701-106">Get Status for a Single Transfer</span></span>  
 <span data-ttu-id="45701-107">取得狀態基本擷取有關從本機永續性內容的一項傳輸的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="45701-107">The Get Status primitive retrieves status information concerning one transfer from the local persistent context.</span></span>  
  
## <a name="subscribe-to-transfer-events"></a><span data-ttu-id="45701-108">要傳送的事件訂閱</span><span class="sxs-lookup"><span data-stu-id="45701-108">Subscribe to Transfer Events</span></span>  
 <span data-ttu-id="45701-109">使用訂閱的事件基本項目來漸進式傳送狀態資訊可能會收到事件的事件為基礎。</span><span class="sxs-lookup"><span data-stu-id="45701-109">Progressive transfer status information may be received on an event-by-event basis by using the Subscribe Event primitive.</span></span> <span data-ttu-id="45701-110">每個檔案傳輸可能會在交涉期間呼叫的事件端點的具名實體連結。</span><span class="sxs-lookup"><span data-stu-id="45701-110">Each file transfer may be linked to a named entity called an event endpoint during the negotiation.</span></span> <span data-ttu-id="45701-111">事件的伺服器，會叫用的訂閱事件的基本指示一個這類事件端點至其本身的所有事件報表。</span><span class="sxs-lookup"><span data-stu-id="45701-111">An event server that invokes the Subscribe Event primitive directs all the event reports for one such an event endpoint to itself.</span></span>  
  
 <span data-ttu-id="45701-112">事件的伺服器可以訂閱特性 （不同層級的詳細資料，以及不同的事件類型）。</span><span class="sxs-lookup"><span data-stu-id="45701-112">An event server can subscribe to characteristics (different levels of detail, as well as to different event types).</span></span>  
  
 <span data-ttu-id="45701-113">事件的伺服器可能會叫用基本項目多次來訂閱事件的多個端點。</span><span class="sxs-lookup"><span data-stu-id="45701-113">An event server may invoke the primitive multiple times to subscribe to multiple event endpoints.</span></span> <span data-ttu-id="45701-114">只有一個事件的伺服器可以訂閱任何特定的事件端點在指定的時間。</span><span class="sxs-lookup"><span data-stu-id="45701-114">Only one event server may subscribe to any particular event endpoint at a given time.</span></span> <span data-ttu-id="45701-115">此外，事件伺服器可以叫用基本項目變更特性多次相同的事件端點。</span><span class="sxs-lookup"><span data-stu-id="45701-115">Additionally, an event server can invoke the primitive multiple times for the same event endpoint for changing the characteristics.</span></span>  
  
## <a name="receive-transfer-events"></a><span data-ttu-id="45701-116">接收轉送事件</span><span class="sxs-lookup"><span data-stu-id="45701-116">Receive Transfer Events</span></span>  
 <span data-ttu-id="45701-117">接收轉送的事件是處理事件的事件狀態資訊有關傳輸進行中的基本類型。</span><span class="sxs-lookup"><span data-stu-id="45701-117">Receive Transfer Events is the primitive that handles the event-by-event status information concerning transfers-in-progress.</span></span> <span data-ttu-id="45701-118">它的回應設定的設定訂閱的事件基本的訂用帳戶中的條款。</span><span class="sxs-lookup"><span data-stu-id="45701-118">It responds to the terms of a subscription that is set up by the Subscribe Event primitive.</span></span> <span data-ttu-id="45701-119">此基本類型可以實作傳送或接收方的傳輸。</span><span class="sxs-lookup"><span data-stu-id="45701-119">This primitive can be implemented at the sending or receiving side of a transfer.</span></span>  
  
## <a name="abort-transfer"></a><span data-ttu-id="45701-120">中止傳輸</span><span class="sxs-lookup"><span data-stu-id="45701-120">Abort Transfer</span></span>  
 <span data-ttu-id="45701-121">使用者應用程式可能會中止傳輸正在進行使用中止基本項目。</span><span class="sxs-lookup"><span data-stu-id="45701-121">A user application may abort a transfer-in-progress using the Abort primitive.</span></span> <span data-ttu-id="45701-122">中止基本項目是可能在傳送端或在進度傳輸的接收端執行的基本類型。</span><span class="sxs-lookup"><span data-stu-id="45701-122">The Abort primitive is a primitive that may be exercised from either the sending-side or the receiving-side of a transfer-in-progress.</span></span> <span data-ttu-id="45701-123">當起始或接受傳輸時，每一端會有建立可做為存取金鑰來保護該傳輸，從其一方的傳輸索引鍵的選項。</span><span class="sxs-lookup"><span data-stu-id="45701-123">When initiating or accepting a transfer, each side has the option of establishing a transfer key that serves as an access key to protect that transfer from its own side.</span></span> <span data-ttu-id="45701-124">如果正在進行傳輸建立傳輸金鑰，它可能不會中止該端從未提供的練習中中止基本型別中的傳輸金鑰值。</span><span class="sxs-lookup"><span data-stu-id="45701-124">If a transfer key is established for a transfer-in-progress, it may not be aborted from that side without supplying the transfer key value in the exercise of the Abort primitive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45701-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45701-125">See Also</span></span>  
 <span data-ttu-id="45701-126">[FileAct 配接器架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="45701-126">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="45701-127">[FileAct 配接器即時的端對端原型](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="45701-127">[FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span></span>  
 <span data-ttu-id="45701-128">[FileAct 配接器儲存與轉送](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="45701-128">[FileAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="45701-129">[FileAct 配接器安全性架構](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="45701-129">[FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="45701-130">[FileAct 配接器檔案和傳輸識別碼](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span><span class="sxs-lookup"><span data-stu-id="45701-130">[FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span></span>  
 <span data-ttu-id="45701-131">[FileAct 配接器支援資訊傳輸](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span><span class="sxs-lookup"><span data-stu-id="45701-131">[FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span></span>  
 <span data-ttu-id="45701-132">[FileAct 配接器傳遞通知](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span><span class="sxs-lookup"><span data-stu-id="45701-132">[FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span></span>  
 [<span data-ttu-id="45701-133">FileAct 配接器狀態監視</span><span class="sxs-lookup"><span data-stu-id="45701-133">FileAct Adapter Status Monitoring</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)