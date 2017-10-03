---
title: "訊息批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching
- batching, about batching
- messages, batching
- batching, messages
ms.assetid: d852cf00-3882-4f0f-a4c3-2a39483710ee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 849f14113d5a5e4776c303ef7a5ea4e1e50a552b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-batching"></a><span data-ttu-id="871aa-102">訊息批次</span><span class="sxs-lookup"><span data-stu-id="871aa-102">Message Batching</span></span>
<span data-ttu-id="871aa-103">通訊協定標準，排程的問題或訊息大小限制可能會促使批次訊息的需要。</span><span class="sxs-lookup"><span data-stu-id="871aa-103">Protocol standards, scheduling issues, or message size limitations may motivate the need to batch messages.</span></span> <span data-ttu-id="871aa-104">健全狀況層級七 (HL7) 的批次所組成的 HL7 批次標頭和批次結尾所含括的訊息。</span><span class="sxs-lookup"><span data-stu-id="871aa-104">A Health Level Seven (HL7) batch consists of messages enclosed by an HL7 batch header and batch trailer.</span></span> <span data-ttu-id="871aa-105">訊息的分隔符號分隔批次內的個別訊息。</span><span class="sxs-lookup"><span data-stu-id="871aa-105">Message separators separate the individual messages within the batch.</span></span>  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="871aa-106">[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]支援下列三個訊息批次處理案例：</span><span class="sxs-lookup"><span data-stu-id="871aa-106"> [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] supports the following three message batching scenarios:</span></span>  
  
-   <span data-ttu-id="871aa-107">**分散的傳入批次**。</span><span class="sxs-lookup"><span data-stu-id="871aa-107">**Fragmented inbound batch**.</span></span> <span data-ttu-id="871aa-108">在此案例中，BTAHL7 接收 HL7 訊息批次，並再將個別的訊息路由至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="871aa-108">In this scenario, BTAHL7 receives an HL7 message batch, and then routes the individual messages to the destination system.</span></span>  
  
-   <span data-ttu-id="871aa-109">**在批次 / 批次出**。在此案例中，BTAHL7 接收 HL7 訊息批次、 驗證，表示批次內的個別訊息並再將批次訊息路由至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="871aa-109">**Batch in/batch out**. In this scenario, BTAHL7 receives an HL7 message batch, verifies the individual messages within the batch, and then routes the message batch to the destination system.</span></span>  
  
-   <span data-ttu-id="871aa-110">**建立批次或輸出批次處理**。</span><span class="sxs-lookup"><span data-stu-id="871aa-110">**Create batch or outbound batching**.</span></span> <span data-ttu-id="871aa-111">在此案例中，BTAHL7 接收個別的訊息，批次處理它們之前進行路由至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="871aa-111">In this scenario, BTAHL7 receives individual messages and batches them before routing them to the destination system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="871aa-112">BTAHL7 不會啟用的預設輸出批次處理的訊息批次。</span><span class="sxs-lookup"><span data-stu-id="871aa-112">BTAHL7 does not enable message batching for outbound batching by default.</span></span> <span data-ttu-id="871aa-113">您必須先登錄 BTAHL7 批次協調流程，使用 BizTalk 總管 中，然後再啟動批次協調流程。</span><span class="sxs-lookup"><span data-stu-id="871aa-113">You must use BizTalk Explorer to first enlist the BTAHL7 batch orchestration, and then start the batch orchestration.</span></span> <span data-ttu-id="871aa-114">如需啟用訊息批次處理的詳細資訊，請參閱[設定批次處理](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)。</span><span class="sxs-lookup"><span data-stu-id="871aa-114">For more information about enabling message batching, see [Configuring Batching](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="871aa-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="871aa-115">In This Section</span></span>  
  
-   [<span data-ttu-id="871aa-116">分散的傳入批次</span><span class="sxs-lookup"><span data-stu-id="871aa-116">Fragmented Inbound Batch</span></span>](../../adapters-and-accelerators/accelerator-hl7/fragmented-inbound-batch.md)  
  
-   [<span data-ttu-id="871aa-117">設定批次處理</span><span class="sxs-lookup"><span data-stu-id="871aa-117">Configuring Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)  
  
-   [<span data-ttu-id="871aa-118">排程批次</span><span class="sxs-lookup"><span data-stu-id="871aa-118">Scheduling Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)  
  
-   [<span data-ttu-id="871aa-119">設定批次處理通知</span><span class="sxs-lookup"><span data-stu-id="871aa-119">Configuring Batching Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)