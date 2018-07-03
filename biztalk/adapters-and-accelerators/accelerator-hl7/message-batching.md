---
title: 訊息批次處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching
- batching, about batching
- messages, batching
- batching, messages
ms.assetid: d852cf00-3882-4f0f-a4c3-2a39483710ee
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc1157dc270fceae7b092a252f75e2c0de658eb9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004967"
---
# <a name="message-batching"></a><span data-ttu-id="0141a-102">訊息批次處理</span><span class="sxs-lookup"><span data-stu-id="0141a-102">Message Batching</span></span>
<span data-ttu-id="0141a-103">通訊協定標準，排程的問題或訊息大小限制，可能會鼓勵批次訊息的需求。</span><span class="sxs-lookup"><span data-stu-id="0141a-103">Protocol standards, scheduling issues, or message size limitations may motivate the need to batch messages.</span></span> <span data-ttu-id="0141a-104">健全狀況層級 7 (HL7) 的批次是由 HL7 批次標頭和批次結尾所含括的訊息所組成。</span><span class="sxs-lookup"><span data-stu-id="0141a-104">A Health Level Seven (HL7) batch consists of messages enclosed by an HL7 batch header and batch trailer.</span></span> <span data-ttu-id="0141a-105">訊息分隔符號來分隔批次內的個別訊息。</span><span class="sxs-lookup"><span data-stu-id="0141a-105">Message separators separate the individual messages within the batch.</span></span>  
  
 <span data-ttu-id="0141a-106">Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]支援下列三個訊息批次處理案例：</span><span class="sxs-lookup"><span data-stu-id="0141a-106">Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] supports the following three message batching scenarios:</span></span>  
  
-   <span data-ttu-id="0141a-107">**片段化的輸入批次**。</span><span class="sxs-lookup"><span data-stu-id="0141a-107">**Fragmented inbound batch**.</span></span> <span data-ttu-id="0141a-108">在此案例中，BTAHL7 接收 HL7 訊息批次，並再將個別的訊息路由至目的系統。</span><span class="sxs-lookup"><span data-stu-id="0141a-108">In this scenario, BTAHL7 receives an HL7 message batch, and then routes the individual messages to the destination system.</span></span>  
  
-   <span data-ttu-id="0141a-109">**在批次 / 批次出**。在此案例中，BTAHL7 接收 HL7 訊息批次、 驗證的批次內的個別訊息，並接著將批次訊息路由傳送至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="0141a-109">**Batch in/batch out**. In this scenario, BTAHL7 receives an HL7 message batch, verifies the individual messages within the batch, and then routes the message batch to the destination system.</span></span>  
  
-   <span data-ttu-id="0141a-110">**建立批次或輸出批次處理**。</span><span class="sxs-lookup"><span data-stu-id="0141a-110">**Create batch or outbound batching**.</span></span> <span data-ttu-id="0141a-111">在此案例中，BTAHL7 接收個別的訊息，並會批次處理它們之前路由傳送至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="0141a-111">In this scenario, BTAHL7 receives individual messages and batches them before routing them to the destination system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0141a-112">BTAHL7 不會啟用預設的輸出批次的批次的訊息。</span><span class="sxs-lookup"><span data-stu-id="0141a-112">BTAHL7 does not enable message batching for outbound batching by default.</span></span> <span data-ttu-id="0141a-113">您必須先登錄 BTAHL7 批次協調流程中，使用 BizTalk 總管，然後再啟動 批次協調流程。</span><span class="sxs-lookup"><span data-stu-id="0141a-113">You must use BizTalk Explorer to first enlist the BTAHL7 batch orchestration, and then start the batch orchestration.</span></span> <span data-ttu-id="0141a-114">如需啟用訊息批次處理的詳細資訊，請參閱 <<c0> [ 設定批次處理](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)。</span><span class="sxs-lookup"><span data-stu-id="0141a-114">For more information about enabling message batching, see [Configuring Batching](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0141a-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="0141a-115">In This Section</span></span>  
  
-   [<span data-ttu-id="0141a-116">片段化的輸入批次</span><span class="sxs-lookup"><span data-stu-id="0141a-116">Fragmented Inbound Batch</span></span>](../../adapters-and-accelerators/accelerator-hl7/fragmented-inbound-batch.md)  
  
-   [<span data-ttu-id="0141a-117">設定批次處理</span><span class="sxs-lookup"><span data-stu-id="0141a-117">Configuring Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)  
  
-   [<span data-ttu-id="0141a-118">排程批次處理</span><span class="sxs-lookup"><span data-stu-id="0141a-118">Scheduling Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)  
  
-   [<span data-ttu-id="0141a-119">設定批次處理通知</span><span class="sxs-lookup"><span data-stu-id="0141a-119">Configuring Batching Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)