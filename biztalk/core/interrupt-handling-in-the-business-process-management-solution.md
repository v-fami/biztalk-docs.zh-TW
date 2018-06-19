---
title: 中斷商務程序管理解決方案中的處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- processing, pausing
- process management solution tutorial, pausing processing
ms.assetid: 23ce7617-f705-4b7d-8447-221dec9fb196
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78b98eae8ee9cbb43354c1cfc48710c70969a929
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257774"
---
# <a name="interrupt-handling-in-the-business-process-management-solution"></a><span data-ttu-id="1778b-102">中斷商務程序管理解決方案中的處理</span><span class="sxs-lookup"><span data-stu-id="1778b-102">Interrupt Handling in the Business Process Management Solution</span></span>
<span data-ttu-id="1778b-103">本節描述商務程序管理解決方案中的中斷處理機制。</span><span class="sxs-lookup"><span data-stu-id="1778b-103">This section describes the interrupt handling mechanism used in the Business Process Management Solution.</span></span> <span data-ttu-id="1778b-104">使用中斷機制，可讓您在訂單更新或取消時，終止訂單處理。</span><span class="sxs-lookup"><span data-stu-id="1778b-104">Using the interrupt mechanism enables you to halt order processing when an order is updated or canceled.</span></span>  
  
## <a name="interrupt-handling"></a><span data-ttu-id="1778b-105">中斷處理</span><span class="sxs-lookup"><span data-stu-id="1778b-105">Interrupt Handling</span></span>  
 <span data-ttu-id="1778b-106">實作處理階段協調流程呼叫的協調流程， **CheckInterrupt**，以測試的程序的某些其他部分的中斷要求。</span><span class="sxs-lookup"><span data-stu-id="1778b-106">The orchestrations that implement the processing stages call an orchestration, **CheckInterrupt**, that tests for an interrupt request from some other part of the process.</span></span> <span data-ttu-id="1778b-107">**CheckInterrupt**協調流程組成**接聽**圖形。</span><span class="sxs-lookup"><span data-stu-id="1778b-107">The **CheckInterrupt** orchestration consists of a **Listen** shape.</span></span> <span data-ttu-id="1778b-108">其中一個分支**接聽**圖形會檢查目前的順序相同的相互關聯識別碼的訊息。</span><span class="sxs-lookup"><span data-stu-id="1778b-108">One branch of the **Listen** shape checks for a message with the same correlation ID as the current order.</span></span> <span data-ttu-id="1778b-109">如果沒有這類訊息**CheckInterrupt**協調流程傳送通知訊息，並執行**擲回**圖形。</span><span class="sxs-lookup"><span data-stu-id="1778b-109">If there is such a message, the **CheckInterrupt** orchestration sends an acknowledgement message and executes a **Throw** shape.</span></span> <span data-ttu-id="1778b-110">因為在分支**接聽**圖形會執行從左到右，在右邊的分支會出現延遲。</span><span class="sxs-lookup"><span data-stu-id="1778b-110">Because the branches in a **Listen** shape are executed from left to right, the delay appears in the right branch.</span></span> <span data-ttu-id="1778b-111">請注意延遲是零 (0)。</span><span class="sxs-lookup"><span data-stu-id="1778b-111">Notice that the delay is zero (0).</span></span>  
  
 <span data-ttu-id="1778b-112">組合**接聽**圖形、 接收分支及延遲分支讓協調流程能檢查訊息。</span><span class="sxs-lookup"><span data-stu-id="1778b-112">The combination of the **Listen** shape, a receive branch, and a delay branch allows the orchestration to check for messages.</span></span> <span data-ttu-id="1778b-113">若有任何的中斷訊息，左邊的分支便會執行。</span><span class="sxs-lookup"><span data-stu-id="1778b-113">If there is an interrupt message, the left branch executes.</span></span> <span data-ttu-id="1778b-114">若沒有任何訊息，則右邊的分支會執行，並返回呼叫的協調流程。</span><span class="sxs-lookup"><span data-stu-id="1778b-114">If there is no message, the right branch executes and returns to the calling orchestration.</span></span> <span data-ttu-id="1778b-115">中斷訊息是隨時都可傳送的。</span><span class="sxs-lookup"><span data-stu-id="1778b-115">An interrupt message can be sent at any time.</span></span> <span data-ttu-id="1778b-116">因為**CheckInterrupt**只有有時候，可能會等候中斷訊息，協調流程會執行。</span><span class="sxs-lookup"><span data-stu-id="1778b-116">Because the **CheckInterrupt** orchestration is run only occasionally, there may be an interrupt message waiting for it.</span></span>  
  
 <span data-ttu-id="1778b-117">**OrderManager**藉由呼叫設定中斷**Interrupter**協調流程。</span><span class="sxs-lookup"><span data-stu-id="1778b-117">The **OrderManager** sets interrupts by calling the **Interrupter** orchestration.</span></span> <span data-ttu-id="1778b-118">**Interrupter**協調流程傳送中斷訊息至**InterruptPort**並等待回覆。</span><span class="sxs-lookup"><span data-stu-id="1778b-118">The **Interrupter** orchestration sends an interrupt message to the **InterruptPort** and waits for a reply.</span></span> <span data-ttu-id="1778b-119">協調流程使用**逾時**封入屬性**範圍**圖形，如果未接收到回覆，請重新啟動迴圈。</span><span class="sxs-lookup"><span data-stu-id="1778b-119">The orchestration uses the **Timeout** property of the enclosing **Scope** shape to restart the loop if a reply isn't received.</span></span> <span data-ttu-id="1778b-120">在未接收到回覆之前，只要超過了範圍時間，協調流程便會繼續傳送中斷訊息。</span><span class="sxs-lookup"><span data-stu-id="1778b-120">The orchestration continues to send the interrupt message as long as the scope times out before receiving a reply.</span></span> <span data-ttu-id="1778b-121">逾時表示要求已符合訂閱，但已無時間可等待回覆。</span><span class="sxs-lookup"><span data-stu-id="1778b-121">A timeout indicates that the request matched a subscription, but there hasn't been time for a reply.</span></span> <span data-ttu-id="1778b-122">若有回覆，或如果沒有任何訂閱，迴圈結束**InterruptPort**。</span><span class="sxs-lookup"><span data-stu-id="1778b-122">The loop ends if there is a reply, or if there is no subscription to the **InterruptPort**.</span></span>  
  
 <span data-ttu-id="1778b-123">要求-回應-完成模式**OrderManager**以處理階段是中斷處理很重要的一部分。</span><span class="sxs-lookup"><span data-stu-id="1778b-123">The request-response-completion pattern the **OrderManager** uses with the process stages is a critical part of the interrupt handling.</span></span> <span data-ttu-id="1778b-124">因為**OrderManager**等候回應-通知-從階段，即得知該階段已開始執行後再繼續。</span><span class="sxs-lookup"><span data-stu-id="1778b-124">Because the **OrderManager** waits for a response—an acknowledgement—from the stage, it knows that the stage has started running before continuing.</span></span> <span data-ttu-id="1778b-125">這可確保階段不會在其開始之前便接收到中斷。</span><span class="sxs-lookup"><span data-stu-id="1778b-125">This guarantees that a stage cannot receive an interrupt before it starts.</span></span> <span data-ttu-id="1778b-126">這也讓**OrderManager**知道，是否沒有任何中斷的訂閱，已完成階段。</span><span class="sxs-lookup"><span data-stu-id="1778b-126">This also lets the **OrderManager** know that, if there is no subscription to an interrupt, the stage has completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1778b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1778b-127">See Also</span></span>  
 <span data-ttu-id="1778b-128">[商務程序管理解決方案中的處理](../core/processing-in-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="1778b-128">[Processing in the Business Process Management Solution](../core/processing-in-the-business-process-management-solution.md) </span></span>  
 <span data-ttu-id="1778b-129">[程序管理員邏輯](../core/process-manager-logic.md) </span><span class="sxs-lookup"><span data-stu-id="1778b-129">[Process Manager Logic](../core/process-manager-logic.md) </span></span>  
 [<span data-ttu-id="1778b-130">ExceptionHandler 協調流程</span><span class="sxs-lookup"><span data-stu-id="1778b-130">The ExceptionHandler Orchestration</span></span>](../core/the-exceptionhandler-orchestration.md)