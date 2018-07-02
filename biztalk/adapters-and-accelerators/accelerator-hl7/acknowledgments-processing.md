---
title: 通知處理 |Microsoft Docs
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
ms.openlocfilehash: cb8bf0620c3e336317382cbeb299cf2d6d17faa2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969463"
---
# <a name="acknowledgments-processing"></a><span data-ttu-id="3f8f2-102">通知處理</span><span class="sxs-lookup"><span data-stu-id="3f8f2-102">Acknowledgments Processing</span></span>
<span data-ttu-id="3f8f2-103">HL7 規格會支援兩種格式的訊息交換：</span><span class="sxs-lookup"><span data-stu-id="3f8f2-103">The HL7 specification supports exchange of messages in two formats:</span></span>  
  
- <span data-ttu-id="3f8f2-104">來路不明的更新和其通知 (ACK)</span><span class="sxs-lookup"><span data-stu-id="3f8f2-104">Unsolicited update and its acknowledgment (ACK)</span></span>  
  
- <span data-ttu-id="3f8f2-105">查詢和回應</span><span class="sxs-lookup"><span data-stu-id="3f8f2-105">Query and its response</span></span>  
  
  <span data-ttu-id="3f8f2-106">在回應訊息從起始應用程式，回應的應用程式會回應包含資料或錯誤指示的訊息。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-106">In response to a message from an initiating application, the responding application responds with a message that includes data or an error indication.</span></span> <span data-ttu-id="3f8f2-107">起始應用程式可能會收到拒絕狀態回應應用程式，指出，回應者應用程式未收到訊息正確。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-107">The initiating application may receive a reject status from the responder application indicating that the responder application did not receive the message correctly.</span></span> <span data-ttu-id="3f8f2-108">在這兩種情況下，訊息交換的程序牽涉到兩個實體，起始和回應的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-108">In both cases, the process of message exchange involves two entities, the initiating and responding applications.</span></span> <span data-ttu-id="3f8f2-109">每一個是傳送者和接收者的訊息。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-109">Each is both a sender and receiver of messages.</span></span> <span data-ttu-id="3f8f2-110">起始應用程式會傳送第一次，然後接收，而接收回應的系統，並接著會傳送。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-110">The initiating application sends first and then receives, while the responding system receives and then sends.</span></span>  
  
## <a name="unsolicited-updates"></a><span data-ttu-id="3f8f2-111">來路不明的更新</span><span class="sxs-lookup"><span data-stu-id="3f8f2-111">Unsolicited updates</span></span>  
 <span data-ttu-id="3f8f2-112">特定業務 (LOB) 應用程式發佈訊息，或觸發程序事件發生時，會起始傳輸的資訊時，就會發生不請自來的更新。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-112">An unsolicited update occurs when a line-of-business (LOB) application publishes a message, or initiates a transfer of information when a trigger event occurs.</span></span> <span data-ttu-id="3f8f2-113">比方說，病患的實驗室結果可用時，有可能需要將實驗室結果傳送至數個其他系統。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-113">For example, when the laboratory results for a patient are available, there may be a need to send the laboratory results to several other systems.</span></span> <span data-ttu-id="3f8f2-114">這些更新是未經要求的更新通知回應。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-114">These updates are unsolicited updates to which an ACK responds.</span></span>  
  
## <a name="queries"></a><span data-ttu-id="3f8f2-115">查詢</span><span class="sxs-lookup"><span data-stu-id="3f8f2-115">Queries</span></span>  
 <span data-ttu-id="3f8f2-116">在查詢時，需要資訊的應用程式會將查詢傳送至另一個應用程式，並接收應用程式回應查詢。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-116">In the case of a query, an application that requires information sends a query to another application, and the receiving application responds to the query.</span></span> <span data-ttu-id="3f8f2-117">比方說，一個配藥應用程式可能會傳送包含訂單項目 (CPOE) 系統病患的 ID 編號的要求訊息並接收回應，其中包含必要的資料，以允許訂單處理。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-117">For example, a pharmacy application may send a request message containing the ID number of the patient to the Order Entry (CPOE) system and receive a response containing the necessary data to permit processing of the order.</span></span> <span data-ttu-id="3f8f2-118">此要求的交易的查詢，而且不同於來路不明的更新。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-118">This requesting transaction is a query, and is different from an unsolicited update.</span></span> <span data-ttu-id="3f8f2-119">在回應中包含兩個應用程式之間流動的資訊。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-119">The information that flows between the two applications is contained in the response.</span></span> <span data-ttu-id="3f8f2-120">回應本身不需要使用第四個訊息的通知。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-120">The response itself does not require an acknowledgment with a fourth message.</span></span> <span data-ttu-id="3f8f2-121">不過，修改這在某些環境中以回應的通知。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-121">However, you can modify this in some environments to respond with an ACK.</span></span> <span data-ttu-id="3f8f2-122">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 如果如此設定，以通知回應。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-122">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) responds with an ACK if so configured.</span></span> <span data-ttu-id="3f8f2-123">如需查詢/回應交換的範例，請參閱 <<c0> [ 詢問式教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="3f8f2-123">For an example of a query/response exchange, see [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f8f2-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="3f8f2-124">In This Section</span></span>  
  
-   [<span data-ttu-id="3f8f2-125">驗證訊息</span><span class="sxs-lookup"><span data-stu-id="3f8f2-125">Validating Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/validating-messages.md)  
  
-   [<span data-ttu-id="3f8f2-126">ACK 訊息模式</span><span class="sxs-lookup"><span data-stu-id="3f8f2-126">ACK Message Modes</span></span>](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)  
  
-   [<span data-ttu-id="3f8f2-127">ACK 處理序模型</span><span class="sxs-lookup"><span data-stu-id="3f8f2-127">ACK Process Model</span></span>](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md)