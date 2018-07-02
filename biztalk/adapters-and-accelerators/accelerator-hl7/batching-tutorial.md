---
title: 批次處理教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching tutorial
- tutorials, batching tutorial
- batching tutorial, about the tutorial
- batching, tutorial
ms.assetid: e9010638-74cf-47cd-8cc9-9d6fd08a1b8d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 790303ac2026cbbce2fdb1c436e3dc8c7e9ff7f7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980079"
---
# <a name="batching-tutorial"></a><span data-ttu-id="ac6d8-102">批次處理教學課程</span><span class="sxs-lookup"><span data-stu-id="ac6d8-102">Batching Tutorial</span></span>
<span data-ttu-id="ac6d8-103">本教學課程提供逐步程序使用的 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]來接收和傳送批次的訊息。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-103">This tutorial provides step-by-step procedures for using Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to receive and send batched messages.</span></span> <span data-ttu-id="ac6d8-104">批次處理為單一複合訊息包含接收和/或傳送一組個別的訊息 （或通知）。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-104">Batching involves receiving and/or sending a group of individual messages (or acknowledgments) as a single composite message.</span></span>  
  
 <span data-ttu-id="ac6d8-105">BTAHL7 支援下列三個訊息批次處理的案例：</span><span class="sxs-lookup"><span data-stu-id="ac6d8-105">BTAHL7 supports the following three message batching scenarios:</span></span>  
  
- <span data-ttu-id="ac6d8-106">**片段化的輸入批次**。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-106">**Fragmented inbound batch**.</span></span> <span data-ttu-id="ac6d8-107">在此案例中，BTAHL7 接收 HL7 訊息批次，並再將個別的訊息路由至目的系統。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-107">In this scenario, BTAHL7 receives an HL7 message batch, and then routes the individual messages to the destination system.</span></span>  
  
- <span data-ttu-id="ac6d8-108">**在批次 / 批次出**。BTAHL7 接收 HL7 訊息批次、 驗證的批次內的個別訊息，並接著將批次訊息路由傳送至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-108">**Batch in/batch out**. BTAHL7 receives an HL7 message batch, verifies the individual messages within the batch, and then routes the message batch to the destination system.</span></span>  
  
- <span data-ttu-id="ac6d8-109">**建立批次 （或輸出批次處理）**。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-109">**Create batch (or outbound batching)**.</span></span> <span data-ttu-id="ac6d8-110">BTAHL7 接收個別的訊息，並會批次處理它們之前路由傳送至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-110">BTAHL7 receives individual messages and batches them before routing them to the destination system.</span></span>  
  
  <span data-ttu-id="ac6d8-111">本教學課程中會包含三個批次案例的每個組件。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-111">This tutorial includes parts for each of the three batching scenarios.</span></span> <span data-ttu-id="ac6d8-112">使用三個部分的教學課程中，提供; 的順序第 1 部分包含第 2 部和第 3 部分的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="ac6d8-112">Use the three parts of the tutorial in the order provided; part 1 contains prerequisite steps for part 2 and part 3.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac6d8-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="ac6d8-113">In This Section</span></span>  
  
-   [<span data-ttu-id="ac6d8-114">準備使用批次處理教學課程</span><span class="sxs-lookup"><span data-stu-id="ac6d8-114">Preparing to Use the Batching Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)  
  
-   [<span data-ttu-id="ac6d8-115">第 1 部分：片段化的輸入批次案例</span><span class="sxs-lookup"><span data-stu-id="ac6d8-115">Part 1: Fragmented Inbound Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)  
  
-   [<span data-ttu-id="ac6d8-116">第 2 部分：批次進/批次出案例</span><span class="sxs-lookup"><span data-stu-id="ac6d8-116">Part 2: Batch In/Batch Out Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)  
  
-   [<span data-ttu-id="ac6d8-117">第 3 部分：建立批次案例</span><span class="sxs-lookup"><span data-stu-id="ac6d8-117">Part 3: Create-Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)