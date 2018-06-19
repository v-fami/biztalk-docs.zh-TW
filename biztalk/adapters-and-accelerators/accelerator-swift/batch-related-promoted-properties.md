---
title: 批次相關升級屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- promoted properties, batch related properties
- batching, promoted properties
ms.assetid: 00df1d8f-2f3f-4e3f-9983-37dcf3514fd8
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20fa421c6536d1d5182a11872206783392c65f69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210542"
---
# <a name="batch-related-promoted-properties"></a><span data-ttu-id="cb6ed-102">批次相關升級的屬性</span><span class="sxs-lookup"><span data-stu-id="cb6ed-102">Batch-Related Promoted Properties</span></span>
<span data-ttu-id="cb6ed-103">當 SWIFT 解譯器會來自傳入的批次至 MessageBox 資料庫的訊息發佈時，解譯器會將訊息標示與特殊[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]升級特定批次訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-103">When the SWIFT disassembler publishes a message that originated from an inbound batch to the MessageBox database, the disassembler marks the message with special [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] promoted properties that are specific to batch messages.</span></span> <span data-ttu-id="cb6ed-104">這些屬性會提供內容資訊，例如訊息起源哪些序數位置從哪一個批次是中的批次部分 A4SWIFT 已保留，依此類推。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-104">These properties provide context information, such as which batch a message originated from, what ordinal position it was in within the batch, which parts A4SWIFT has preserved, and so forth.</span></span>  
  
 <span data-ttu-id="cb6ed-105">A4SWIFT 設定批次訊息的升級下列屬性：</span><span class="sxs-lookup"><span data-stu-id="cb6ed-105">A4SWIFT sets the following promoted properties for batch messages:</span></span>  
  
-   <span data-ttu-id="cb6ed-106">**A4SWIFT_BatchId**</span><span class="sxs-lookup"><span data-stu-id="cb6ed-106">**A4SWIFT_BatchId**</span></span>  
  
-   <span data-ttu-id="cb6ed-107">**A4SWIFT_IsMessageHeaderValued**</span><span class="sxs-lookup"><span data-stu-id="cb6ed-107">**A4SWIFT_IsMessageHeaderValued**</span></span>  
  
-   <span data-ttu-id="cb6ed-108">**A4SWIFT_IsMessageTrailerValued**</span><span class="sxs-lookup"><span data-stu-id="cb6ed-108">**A4SWIFT_IsMessageTrailerValued**</span></span>  
  
-   <span data-ttu-id="cb6ed-109">**A4SWIFT_NumberOfParts**</span><span class="sxs-lookup"><span data-stu-id="cb6ed-109">**A4SWIFT_NumberOfParts**</span></span>  
  
-   <span data-ttu-id="cb6ed-110">**A4SWIFT_PosInBatch**</span><span class="sxs-lookup"><span data-stu-id="cb6ed-110">**A4SWIFT_PosInBatch**</span></span>  
  
 <span data-ttu-id="cb6ed-111">如需這些和其他升級的屬性的資訊，請參閱[A4SWIFT_ \* 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-111">For information about these and other promoted properties, see [A4SWIFT_\* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).</span></span>  
  
## <a name="failures-during-batch-processing"></a><span data-ttu-id="cb6ed-112">批次處理作業期間發生的失敗</span><span class="sxs-lookup"><span data-stu-id="cb6ed-112">Failures During Batch Processing</span></span>  
 <span data-ttu-id="cb6ed-113">當 SWIFT 解譯器在批次處理期間所遇到 （剖析或驗證） 的訊息失敗 (**輸入解除批次處理即將**設**True**)，其行為取決於批次組態，為如下所示：</span><span class="sxs-lookup"><span data-stu-id="cb6ed-113">When the SWIFT disassembler encounters message failures (parsing or validation) during batch processing (**Inbound Debatching** set to **True**), its behavior depends upon the batching configuration, as follows:</span></span>  
  
-   <span data-ttu-id="cb6ed-114">批次處理 (**輸入解除批次處理即將**設為**True**) 與啟用的片段 (**片段**設為**True**)，解譯器發行失敗的訊息到 MessageBox 資料庫會個別對應的錯誤資訊附加的升級屬性，序列化**ErrorCollection** XML。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-114">For batch processing (**Inbound Debatching** set to **True**) with fragmentation enabled (**Fragmentation** set to **True**), the disassembler publishes failed messages to the MessageBox database individually, with corresponding error information appended in promoted properties and serialized **ErrorCollection** XML.</span></span> <span data-ttu-id="cb6ed-115">如果解譯器找到未預期的資料 （也就是資料的解譯器無法剖析使用任何指定的結構描述） 的批次的結尾，解譯器中的最後一個訊息批次中包含未預期的資料，並將它標記為具有無法剖析.</span><span class="sxs-lookup"><span data-stu-id="cb6ed-115">If the disassembler finds unexpected data at the end of the batch (that is, data that the disassembler cannot parse using any of the specified schemas), the disassembler includes this unexpected data in the last message in the batch and marks it as having failed parsing.</span></span> <span data-ttu-id="cb6ed-116">如果解譯器會在處理期間發生嚴重錯誤，解譯器就會發佈導致嚴重的錯誤，再加上所有的資料當成單一訊息的交換結尾的訊息。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-116">If the disassembler encounters a fatal error during processing, then the disassembler publishes the message that caused the fatal error, plus all data to the end of the interchange, as a single message.</span></span> <span data-ttu-id="cb6ed-117">解譯器不嚴重的錯誤之後片段的訊息。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-117">The disassembler does not fragment messages after the fatal error.</span></span>  
  
-   <span data-ttu-id="cb6ed-118">批次處理 (**輸入解除批次處理即將**設為**True**) 與停用的片段 (**片段**設**False**)，解譯器發行失敗的訊息到 MessageBox 資料庫會個別對應的錯誤資訊附加的升級屬性，序列化**ErrorCollection** XML。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-118">For batch processing (**Inbound Debatching** set to **True**) with fragmentation disabled (**Fragmentation** set to **False**), the disassembler publishes failed messages to the MessageBox database individually, with corresponding error information appended in promoted properties and serialized **ErrorCollection** XML.</span></span> <span data-ttu-id="cb6ed-119">此外，解譯器將發佈 （其中包含一或多個失敗的訊息），整個批次至 MessageBox 資料庫成單一訊息，以原生格式 （輸入的完全相同複本）。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-119">In addition, the disassembler publishes the entire batch (containing one or more failed messages) to the MessageBox database as a single message, in native form (exact copy of input).</span></span> <span data-ttu-id="cb6ed-120">解譯器會將其與標示**A4SWIFT_Failed**升級屬性集**True**表示批次包含一個或多個失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-120">The disassembler marks it with the **A4SWIFT_Failed** promoted property set **True** to indicate that the batch contains one or more failed messages.</span></span> <span data-ttu-id="cb6ed-121">解譯器也會將附加序列化**ErrorCollection** XML 片段未批次，表示所有批次內的個別訊息在遇到錯誤的串連。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-121">The disassembler also attaches serialized **ErrorCollection** XML to the un-fragmented batch that represents the concatenation of all errors encountered in the individual messages within the batch.</span></span> <span data-ttu-id="cb6ed-122">若要探索失敗的訊息批次中的每個訊息錯誤詳細資料，您必須從 MessageBox 資料庫中擷取個別的失敗的訊息 （藉由在 A4SWIFT_BatchId 關聯），並擷取**ErrorCollection** XML針對每個失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-122">To discover the per-message error details from failed messages in the batch, you must retrieve the individual failed messages from the MessageBox database (by correlating on A4SWIFT_BatchId), and extract the **ErrorCollection** XML for each failed message.</span></span> <span data-ttu-id="cb6ed-123">如果解譯器找到未預期的資料 （也就是資料的解譯器無法剖析使用任何指定的結構描述） 的批次的結尾，解譯器包含整個失敗的批次的非預期的資料 （因為解譯器將其以發佈MessageBox 資料庫中逐字），並將它標示為具有無法剖析由於未預期的資料。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-123">If the disassembler finds unexpected data at the end of the batch (that is, data that the disassembler cannot parse using any of the specified schemas), the disassembler includes the unexpected data with the entire failed batch (since the disassembler publishes it to the MessageBox database verbatim), and marks it as having failed parsing due to unexpected data.</span></span>  
  
-   <span data-ttu-id="cb6ed-124">非批次案例 (**輸入解除批次處理即將**設**False**)，解譯器一律發行失敗的訊息到 MessageBox 資料庫會個別如預期般。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-124">For non-batch scenarios (**Inbound Debatching** set to **False**), the disassembler always publishes failed messages to the MessageBox database individually, as expected.</span></span>  
  
 <span data-ttu-id="cb6ed-125">如需有關 A4SWIFT 失敗/錯誤升級屬性和**ErrorCollection**物件，請參閱[處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6ed-125">For more information about A4SWIFT failure/error promoted properties and the **ErrorCollection** object, see [Working with Failed Message Subscriptions](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6ed-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb6ed-126">See Also</span></span>  
 <span data-ttu-id="cb6ed-127">[解譯輸入批次](../../adapters-and-accelerators/accelerator-swift/disassembling-inbound-batches.md) </span><span class="sxs-lookup"><span data-stu-id="cb6ed-127">[Disassembling Inbound Batches](../../adapters-and-accelerators/accelerator-swift/disassembling-inbound-batches.md) </span></span>  
 [<span data-ttu-id="cb6ed-128">SWIFT 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="cb6ed-128">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)