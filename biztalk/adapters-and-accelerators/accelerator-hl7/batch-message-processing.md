---
title: 批次訊息處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, batching
- batching, examples
- batching, batch types
ms.assetid: 264f91b5-3e33-4b87-9da3-866eaa464b0f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75cde12720ac67d74396c22282bddaf53e015960
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972367"
---
# <a name="batch-message-processing"></a><span data-ttu-id="9c31e-102">批次訊息處理</span><span class="sxs-lookup"><span data-stu-id="9c31e-102">Batch Message Processing</span></span>
<span data-ttu-id="9c31e-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 處理三種類型的 HL7 2.X 批次案例：</span><span class="sxs-lookup"><span data-stu-id="9c31e-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) handles three types of HL7 2.X batch scenarios:</span></span>  
  
- <span data-ttu-id="9c31e-104">片段化的輸入批次的案例。</span><span class="sxs-lookup"><span data-stu-id="9c31e-104">Fragmented inbound batch scenario.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="9c31e-105"> 將這些批次剖析不同的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="9c31e-105"> parses these batches into separate output messages.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="9c31e-106"> 片段化的批次中傳送的每個訊息的通知 (Ack)。</span><span class="sxs-lookup"><span data-stu-id="9c31e-106"> sends acknowledgments (ACKs) for each message in a fragmented batch.</span></span>  
  
- <span data-ttu-id="9c31e-107">在批次 / 批次出案例。</span><span class="sxs-lookup"><span data-stu-id="9c31e-107">Batch in/batch out scenario.</span></span> <span data-ttu-id="9c31e-108">這些是傳入批次[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不片段，但傳遞，且以不變的批次傳送。</span><span class="sxs-lookup"><span data-stu-id="9c31e-108">These are in-bound batches that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not fragment, but passes through and sends as an intact batch.</span></span> <span data-ttu-id="9c31e-109">如果[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送批次認可的認可包含版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="9c31e-109">If [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK for the batch, the ACK includes a version ID.</span></span>  
  
- <span data-ttu-id="9c31e-110">建立批次的案例。</span><span class="sxs-lookup"><span data-stu-id="9c31e-110">Create-batch scenario.</span></span> <span data-ttu-id="9c31e-111">在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]結合個別輸入的訊息到輸出批次。</span><span class="sxs-lookup"><span data-stu-id="9c31e-111">In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] combines separate input messages into an output batch.</span></span>  
  
  <span data-ttu-id="9c31e-112">您可以格式化批次中任一種方式：</span><span class="sxs-lookup"><span data-stu-id="9c31e-112">You can format batches in either of two ways:</span></span>  
  
- <span data-ttu-id="9c31e-113">檔案標頭和結尾 (FHS/FTS) 和批次標頭與結尾 (BHS/BTS)。</span><span class="sxs-lookup"><span data-stu-id="9c31e-113">With a file header and trailer (FHS/FTS) and a batch header and trailer (BHS/BTS).</span></span>  
  
- <span data-ttu-id="9c31e-114">使用任何檔案或批次標頭/結尾。</span><span class="sxs-lookup"><span data-stu-id="9c31e-114">With no file or batch headers/trailers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c31e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c31e-115">See Also</span></span>  
 <span data-ttu-id="9c31e-116">[訊息批次處理](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span><span class="sxs-lookup"><span data-stu-id="9c31e-116">[Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span></span>  
 <span data-ttu-id="9c31e-117">[批次處理教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="9c31e-117">[Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span></span>  
 <span data-ttu-id="9c31e-118">[第 1 部分： 片段化的輸入批次案例](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9c31e-118">[Part 1: Fragmented Inbound Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md) </span></span>  
 <span data-ttu-id="9c31e-119">[第 2 部分： 中批次 / 批次出案例](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9c31e-119">[Part 2: Batch In/Batch Out Scenario](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md) </span></span>  
 <span data-ttu-id="9c31e-120">[第 3 部分： 建立批次案例](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9c31e-120">[Part 3: Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md) </span></span>  
 [<span data-ttu-id="9c31e-121">訊息處理</span><span class="sxs-lookup"><span data-stu-id="9c31e-121">Message Processing</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)