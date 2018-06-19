---
title: 批次訊息處理 |Microsoft 文件
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
ms.openlocfilehash: aad80bb8fe9a59163ee17e7862bece728fdc52b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204758"
---
# <a name="batch-message-processing"></a>批次訊息處理
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 處理三種類型的 HL7 2.X 批次案例：  
  
-   分散的傳入批次的案例。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將這些批次剖析成不同的輸出訊息。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送通知 (Ack) 的每個訊息，分散的批次中。  
  
-   在批次 / 批次出案例。 這些是繫結批次[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不分段但通過，並以保持不變的批次傳送。 如果[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送批次，ACK ACK 包含版本識別碼。  
  
-   建立批次的案例。 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]結合分為輸出批次輸入的訊息。  
  
 您可以格式化批次中任一種方式：  
  
-   檔案標頭和結尾 (FHS/FTS) 和批次標頭與結尾 (BHS/BTS)。  
  
-   使用沒有檔或批次標頭/結尾。  
  
## <a name="see-also"></a>另請參閱  
 [訊息批次](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)   
 [批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)   
 [第 1 部分： 分散的傳入批次的案例](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [第 2 部分： 中批次 / 批次出案例](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)   
 [第 3 部分： 建立批次的案例](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)