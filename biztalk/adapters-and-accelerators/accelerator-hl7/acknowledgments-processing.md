---
title: 處理通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, processing
ms.assetid: 705bc12d-69ac-4641-a45e-4f1fab507e4a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b726eb4698eaa9887703d7df01dc0f6cadf5eefc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgments-processing"></a><span data-ttu-id="2b436-102">處理通知</span><span class="sxs-lookup"><span data-stu-id="2b436-102">Acknowledgments Processing</span></span>
<span data-ttu-id="2b436-103">HL7 規格支援兩種格式的訊息交換：</span><span class="sxs-lookup"><span data-stu-id="2b436-103">The HL7 specification supports exchange of messages in two formats:</span></span>  
  
-   <span data-ttu-id="2b436-104">來路不明的更新和其通知 (ACK)</span><span class="sxs-lookup"><span data-stu-id="2b436-104">Unsolicited update and its acknowledgment (ACK)</span></span>  
  
-   <span data-ttu-id="2b436-105">查詢和回應</span><span class="sxs-lookup"><span data-stu-id="2b436-105">Query and its response</span></span>  
  
 <span data-ttu-id="2b436-106">回應訊息從起始應用程式，回應的應用程式的回應訊息，其中包含資料或錯誤指示。</span><span class="sxs-lookup"><span data-stu-id="2b436-106">In response to a message from an initiating application, the responding application responds with a message that includes data or an error indication.</span></span> <span data-ttu-id="2b436-107">起始應用程式可能會收到拒絕狀態來自回應者應用程式指出，回應者應用程式未收到郵件正確。</span><span class="sxs-lookup"><span data-stu-id="2b436-107">The initiating application may receive a reject status from the responder application indicating that the responder application did not receive the message correctly.</span></span> <span data-ttu-id="2b436-108">在這兩種情況下，訊息交換的程序牽涉到兩個實體，起始，而且有回應的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2b436-108">In both cases, the process of message exchange involves two entities, the initiating and responding applications.</span></span> <span data-ttu-id="2b436-109">每一個都是傳送者和接收者的訊息。</span><span class="sxs-lookup"><span data-stu-id="2b436-109">Each is both a sender and receiver of messages.</span></span> <span data-ttu-id="2b436-110">起始應用程式會傳送第一次，但收到，而回應系統接收，然後傳送。</span><span class="sxs-lookup"><span data-stu-id="2b436-110">The initiating application sends first and then receives, while the responding system receives and then sends.</span></span>  
  
## <a name="unsolicited-updates"></a><span data-ttu-id="2b436-111">來路不明的更新</span><span class="sxs-lookup"><span data-stu-id="2b436-111">Unsolicited updates</span></span>  
 <span data-ttu-id="2b436-112">特定業務 (LOB) 應用程式發佈訊息，或觸發程序事件發生時起始傳送資訊時，就會發生不請自來的更新。</span><span class="sxs-lookup"><span data-stu-id="2b436-112">An unsolicited update occurs when a line-of-business (LOB) application publishes a message, or initiates a transfer of information when a trigger event occurs.</span></span> <span data-ttu-id="2b436-113">例如，某個病患的實驗室結果可用時，可能有需要將實驗室結果傳送至數個其他系統。</span><span class="sxs-lookup"><span data-stu-id="2b436-113">For example, when the laboratory results for a patient are available, there may be a need to send the laboratory results to several other systems.</span></span> <span data-ttu-id="2b436-114">這些更新是未經要求的更新通知會回應。</span><span class="sxs-lookup"><span data-stu-id="2b436-114">These updates are unsolicited updates to which an ACK responds.</span></span>  
  
## <a name="queries"></a><span data-ttu-id="2b436-115">查詢</span><span class="sxs-lookup"><span data-stu-id="2b436-115">Queries</span></span>  
 <span data-ttu-id="2b436-116">如果查詢時，需要資訊的應用程式會將查詢傳送至另一個應用程式，並接收應用程式回應查詢。</span><span class="sxs-lookup"><span data-stu-id="2b436-116">In the case of a query, an application that requires information sends a query to another application, and the receiving application responds to the query.</span></span> <span data-ttu-id="2b436-117">比方說，藥局應用程式可能會傳送包含訂單項目 (CPOE) 系統病患識別碼的要求訊息並接收回應，其中包含必要的資料，以允許訂單處理。</span><span class="sxs-lookup"><span data-stu-id="2b436-117">For example, a pharmacy application may send a request message containing the ID number of the patient to the Order Entry (CPOE) system and receive a response containing the necessary data to permit processing of the order.</span></span> <span data-ttu-id="2b436-118">提出要求的交易會是查詢，而且不同之未經要求的更新中。</span><span class="sxs-lookup"><span data-stu-id="2b436-118">This requesting transaction is a query, and is different from an unsolicited update.</span></span> <span data-ttu-id="2b436-119">在回應中包含兩個應用程式之間流動的資訊。</span><span class="sxs-lookup"><span data-stu-id="2b436-119">The information that flows between the two applications is contained in the response.</span></span> <span data-ttu-id="2b436-120">回應本身不需要使用第四個訊息的通知。</span><span class="sxs-lookup"><span data-stu-id="2b436-120">The response itself does not require an acknowledgment with a fourth message.</span></span> <span data-ttu-id="2b436-121">不過，修改這在某些環境中以回應通知。</span><span class="sxs-lookup"><span data-stu-id="2b436-121">However, you can modify this in some environments to respond with an ACK.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="2b436-122">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 如果如此設定，會通知以回應。</span><span class="sxs-lookup"><span data-stu-id="2b436-122"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) responds with an ACK if so configured.</span></span> <span data-ttu-id="2b436-123">如需查詢/回應交換的範例，請參閱[Interrogative 教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="2b436-123">For an example of a query/response exchange, see [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b436-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="2b436-124">In This Section</span></span>  
  
-   [<span data-ttu-id="2b436-125">驗證訊息</span><span class="sxs-lookup"><span data-stu-id="2b436-125">Validating Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/validating-messages.md)  
  
-   [<span data-ttu-id="2b436-126">ACK 訊息模式</span><span class="sxs-lookup"><span data-stu-id="2b436-126">ACK Message Modes</span></span>](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)  
  
-   [<span data-ttu-id="2b436-127">ACK 處理序模型</span><span class="sxs-lookup"><span data-stu-id="2b436-127">ACK Process Model</span></span>](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md)