---
title: "批次協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, acknowledgements
- acknowledgements, batching
- batch orchestration
- orchestrations, batch orchestration
- messages, batching
- batching, batch orchestration
- batching, messages
ms.assetid: b449d8d5-72a2-46c8-a2b1-380431175f4d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9db6ee8b4fd3dec8e2902642634b701889866cf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batch-orchestration"></a>批次協調流程
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 提供您可用來處理批次協調流程 (BatchOrchestration.dll)。 此協調流程可以處理訊息 HL7 編碼 (2.X) 和 （或) 通知 (Ack) 的批的次。 協調流程是原生[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]所加入的協調流程[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]（如下所列在 [BizTalk 總管] 中的協調流程） 安裝至 BizTalk 協調流程的設定。  
  
 協調流程的運作方式使用批次啟用時，批次終止和批次計時器訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會使用來控制批次。 協調流程也會處理批次控制連接埠，是指接收埠，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝程式會安裝以處理批次控制訊息。  
  
## <a name="see-also"></a>另請參閱  
 [批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)   
 [BizTalk Accelerator for HL7 元件](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)