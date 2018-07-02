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
# <a name="batch-message-processing"></a>批次訊息處理
Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 處理三種類型的 HL7 2.X 批次案例：  
  
- 片段化的輸入批次的案例。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 將這些批次剖析不同的輸出訊息。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 片段化的批次中傳送的每個訊息的通知 (Ack)。  
  
- 在批次 / 批次出案例。 這些是傳入批次[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不片段，但傳遞，且以不變的批次傳送。 如果[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送批次認可的認可包含版本識別碼。  
  
- 建立批次的案例。 在此案例中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]結合個別輸入的訊息到輸出批次。  
  
  您可以格式化批次中任一種方式：  
  
- 檔案標頭和結尾 (FHS/FTS) 和批次標頭與結尾 (BHS/BTS)。  
  
- 使用任何檔案或批次標頭/結尾。  
  
## <a name="see-also"></a>另請參閱  
 [訊息批次處理](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)   
 [批次處理教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)   
 [第 1 部分： 片段化的輸入批次案例](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [第 2 部分： 中批次 / 批次出案例](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)   
 [第 3 部分： 建立批次案例](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)