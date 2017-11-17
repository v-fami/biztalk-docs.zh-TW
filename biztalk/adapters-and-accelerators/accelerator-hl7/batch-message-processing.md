---
title: "批次訊息處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, batching
- batching, examples
- batching, batch types
ms.assetid: 264f91b5-3e33-4b87-9da3-866eaa464b0f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aad80bb8fe9a59163ee17e7862bece728fdc52b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batch-message-processing"></a><span data-ttu-id="8c7bc-102">批次訊息處理</span><span class="sxs-lookup"><span data-stu-id="8c7bc-102">Batch Message Processing</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="8c7bc-103">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 處理三種類型的 HL7 2.X 批次案例：</span><span class="sxs-lookup"><span data-stu-id="8c7bc-103"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) handles three types of HL7 2.X batch scenarios:</span></span>  
  
-   <span data-ttu-id="8c7bc-104">分散的傳入批次的案例。</span><span class="sxs-lookup"><span data-stu-id="8c7bc-104">Fragmented inbound batch scenario.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="8c7bc-105">將這些批次剖析成不同的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="8c7bc-105"> parses these batches into separate output messages.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="8c7bc-106">傳送通知 (Ack) 的每個訊息，分散的批次中。</span><span class="sxs-lookup"><span data-stu-id="8c7bc-106"> sends acknowledgments (ACKs) for each message in a fragmented batch.</span></span>  
  
-   <span data-ttu-id="8c7bc-107">在批次 / 批次出案例。</span><span class="sxs-lookup"><span data-stu-id="8c7bc-107">Batch in/batch out scenario.</span></span> <span data-ttu-id="8c7bc-108">這些是繫結批次[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不分段但通過，並以保持不變的批次傳送。</span><span class="sxs-lookup"><span data-stu-id="8c7bc-108">These are in-bound batches that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not fragment, but passes through and sends as an intact batch.</span></span> <span data-ttu-id="8c7bc-109">如果[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送批次，ACK ACK 包含版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="8c7bc-109">If [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK for the batch, the ACK includes a version ID.</span></span>  
  
-   <span data-ttu-id="8c7bc-110">建立批次的案例。</span><span class="sxs-lookup"><span data-stu-id="8c7bc-110">Create-batch scenario.</span></span> <span data-ttu-id="8c7bc-111">在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]結合分為輸出批次輸入的訊息。</span><span class="sxs-lookup"><span data-stu-id="8c7bc-111">In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] combines separate input messages into an output batch.</span></span>  
  
 <span data-ttu-id="8c7bc-112">您可以格式化批次中任一種方式：</span><span class="sxs-lookup"><span data-stu-id="8c7bc-112">You can format batches in either of two ways:</span></span>  
  
-   <span data-ttu-id="8c7bc-113">檔案標頭和結尾 (FHS/FTS) 和批次標頭與結尾 (BHS/BTS)。</span><span class="sxs-lookup"><span data-stu-id="8c7bc-113">With a file header and trailer (FHS/FTS) and a batch header and trailer (BHS/BTS).</span></span>  
  
-   <span data-ttu-id="8c7bc-114">使用沒有檔或批次標頭/結尾。</span><span class="sxs-lookup"><span data-stu-id="8c7bc-114">With no file or batch headers/trailers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c7bc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c7bc-115">See Also</span></span>  
 <span data-ttu-id="8c7bc-116">[訊息批次](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span><span class="sxs-lookup"><span data-stu-id="8c7bc-116">[Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span></span>  
 <span data-ttu-id="8c7bc-117">[批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="8c7bc-117">[Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span></span>  
 <span data-ttu-id="8c7bc-118">[第 1 部分： 分散的傳入批次的案例](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8c7bc-118">[Part 1: Fragmented Inbound Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md) </span></span>  
 <span data-ttu-id="8c7bc-119">[第 2 部分： 中批次 / 批次出案例](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8c7bc-119">[Part 2: Batch In/Batch Out Scenario](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md) </span></span>  
 <span data-ttu-id="8c7bc-120">[第 3 部分： 建立批次的案例](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8c7bc-120">[Part 3: Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md) </span></span>  
 [<span data-ttu-id="8c7bc-121">訊息處理</span><span class="sxs-lookup"><span data-stu-id="8c7bc-121">Message Processing</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)