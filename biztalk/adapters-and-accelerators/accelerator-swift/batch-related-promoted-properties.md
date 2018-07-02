---
title: 批次相關升級屬性 |Microsoft Docs
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
ms.openlocfilehash: a27d10fd4fc4224d54db166ecdf5f774192cb10a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000679"
---
# <a name="batch-related-promoted-properties"></a>批次相關升級的屬性
SWIFT 解譯器會發佈訊息，其中來自輸入的批次至 MessageBox 資料庫，當解譯器會將訊息標示與特殊 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]升級特定批次訊息的屬性。 這些屬性會提供內容資訊，例如從哪些序數位置所產生的訊息批次所內的批次部分 A4SWIFT 已保留，等等。  
  
 A4SWIFT 設定批次訊息的下列升級的屬性：  
  
- **A4SWIFT_BatchId**  
  
- **A4SWIFT_IsMessageHeaderValued**  
  
- **A4SWIFT_IsMessageTrailerValued**  
  
- **A4SWIFT_NumberOfParts**  
  
- **A4SWIFT_PosInBatch**  
  
  如需這些和其他升級的屬性的詳細資訊，請參閱[A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)。  
  
## <a name="failures-during-batch-processing"></a>Batch 處理期間發生的失敗  
 當 SWIFT 解譯器在批次的處理期間遇到 （剖析或驗證） 的訊息失敗 (**輸入解除批次處理**設為 **，則為 True**)，其行為取決於批次組態中，為如下所示：  
  
- 批次處理 (**輸入解除批次處理**設為 **，則為 True**) 與啟用的片段 (**片段**設為**True**)，反組譯工具發行失敗的訊息到 MessageBox 資料庫會個別對應的錯誤資訊附加在升級的屬性和序列化**ErrorCollection** XML。 如果解譯器找到未預期的資料結尾的批次 （也就是資料的解譯器無法剖析使用任何指定的結構描述），解譯器在批次中的最後一個訊息中包含這個未預期的資料，並將它標示為具有無法剖析. 如果解譯器在處理期間發生嚴重錯誤，然後解譯器將訊息發佈造成嚴重的錯誤，再加上當作單一訊息的交換結尾的所有資料。 反組譯工具不嚴重的錯誤之後片段的訊息。  
  
- 批次處理 (**輸入解除批次處理**設為 **，則為 True**) 與停用的片段 (**片段**設定為**False**)，反組譯工具發行失敗的訊息到 MessageBox 資料庫會個別對應的錯誤資訊附加在升級的屬性和序列化**ErrorCollection** XML。 此外，解譯器會發佈 （包含一或多個失敗的訊息），整個批次至 MessageBox 資料庫當作單一訊息，以原生格式 （輸入完全相同複本）。 解譯器會將其與標示**A4SWIFT_Failed**升級屬性集 **，則為 True**來表示批次包含一或多個失敗的訊息。 反組譯工具也會將附加序列化**ErrorCollection** XML 片段未批次，表示批次內的個別訊息中所發生的所有錯誤的串連。 若要探索每個訊息的錯誤詳細資料，從失敗的訊息批次中，您必須從 MessageBox 資料庫中擷取個別失敗的訊息 （藉由在 A4SWIFT_BatchId 關聯），並擷取**ErrorCollection** XML針對每個失敗的訊息。 如果解譯器找到未預期的資料結尾的批次 （也就是資料的解譯器無法剖析使用任何指定的結構描述），反組譯工具 （因為解譯器將它發佈至包含整個失敗的批次具有未預期的資料MessageBox 資料庫中逐字翻譯），並將它標示為具有無法剖析因未預期的資料。  
  
- 針對非批次案例 (**輸入解除批次處理**設為**False**)，解譯器一律會發佈失敗的訊息到 MessageBox 資料庫個別，如預期般運作。  
  
  如需有關 A4SWIFT 失敗/錯誤升級屬性和**ErrorCollection**物件，請參閱[處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [解譯輸入批次](../../adapters-and-accelerators/accelerator-swift/disassembling-inbound-batches.md)   
 [使用 SWIFT 解譯器和組合器](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)