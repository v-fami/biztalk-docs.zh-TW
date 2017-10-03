---
title: "批次的教學課程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching tutorial
- tutorials, batching tutorial
- batching tutorial, about the tutorial
- batching, tutorial
ms.assetid: e9010638-74cf-47cd-8cc9-9d6fd08a1b8d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27e2aff66468c697c92adb4c452250b70dae2e59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batching-tutorial"></a><span data-ttu-id="c9622-102">批次的教學課程</span><span class="sxs-lookup"><span data-stu-id="c9622-102">Batching Tutorial</span></span>
<span data-ttu-id="c9622-103">本教學課程提供逐步程序使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]來接收和傳送批次的訊息。</span><span class="sxs-lookup"><span data-stu-id="c9622-103">This tutorial provides step-by-step procedures for using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to receive and send batched messages.</span></span> <span data-ttu-id="c9622-104">批次當做單一複合訊息包含接收和/或傳送的一組個別訊息 （或通知）。</span><span class="sxs-lookup"><span data-stu-id="c9622-104">Batching involves receiving and/or sending a group of individual messages (or acknowledgments) as a single composite message.</span></span>  
  
 <span data-ttu-id="c9622-105">BTAHL7 支援下列三個訊息批次處理案例：</span><span class="sxs-lookup"><span data-stu-id="c9622-105">BTAHL7 supports the following three message batching scenarios:</span></span>  
  
-   <span data-ttu-id="c9622-106">**分散的傳入批次**。</span><span class="sxs-lookup"><span data-stu-id="c9622-106">**Fragmented inbound batch**.</span></span> <span data-ttu-id="c9622-107">在此案例中，BTAHL7 接收 HL7 訊息批次，並再將個別的訊息路由至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="c9622-107">In this scenario, BTAHL7 receives an HL7 message batch, and then routes the individual messages to the destination system.</span></span>  
  
-   <span data-ttu-id="c9622-108">**在批次 / 批次出**。BTAHL7 接收 HL7 訊息批次、 驗證，表示批次內的個別訊息並再將批次訊息路由至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="c9622-108">**Batch in/batch out**. BTAHL7 receives an HL7 message batch, verifies the individual messages within the batch, and then routes the message batch to the destination system.</span></span>  
  
-   <span data-ttu-id="c9622-109">**建立批次 （或輸出批次處理）**。</span><span class="sxs-lookup"><span data-stu-id="c9622-109">**Create batch (or outbound batching)**.</span></span> <span data-ttu-id="c9622-110">BTAHL7 接收個別的訊息，批次處理它們之前進行路由至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="c9622-110">BTAHL7 receives individual messages and batches them before routing them to the destination system.</span></span>  
  
 <span data-ttu-id="c9622-111">本教學課程包含組件的每個批次的三種案例。</span><span class="sxs-lookup"><span data-stu-id="c9622-111">This tutorial includes parts for each of the three batching scenarios.</span></span> <span data-ttu-id="c9622-112">使用三個部分的教學課程 」 中的順序提供。第 1 部分包含第 2 部分和第 3 部分先決條件步驟。</span><span class="sxs-lookup"><span data-stu-id="c9622-112">Use the three parts of the tutorial in the order provided; part 1 contains prerequisite steps for part 2 and part 3.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9622-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="c9622-113">In This Section</span></span>  
  
-   [<span data-ttu-id="c9622-114">準備使用批次的教學課程</span><span class="sxs-lookup"><span data-stu-id="c9622-114">Preparing to Use the Batching Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)  
  
-   [<span data-ttu-id="c9622-115">第 1 部分： 分散的傳入批次的案例</span><span class="sxs-lookup"><span data-stu-id="c9622-115">Part 1: Fragmented Inbound Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)  
  
-   [<span data-ttu-id="c9622-116">第 2 部分： 中批次 / 批次出案例</span><span class="sxs-lookup"><span data-stu-id="c9622-116">Part 2: Batch In/Batch Out Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)  
  
-   [<span data-ttu-id="c9622-117">第 3 部分： 建立批次的案例</span><span class="sxs-lookup"><span data-stu-id="c9622-117">Part 3: Create-Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)