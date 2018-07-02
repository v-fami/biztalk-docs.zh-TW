---
title: 批次協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2271170d91990e5874168a18ed274c1502a93158
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971591"
---
# <a name="batch-orchestration"></a><span data-ttu-id="51320-102">批次協調流程</span><span class="sxs-lookup"><span data-stu-id="51320-102">Batch Orchestration</span></span>
<span data-ttu-id="51320-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 提供您可用來處理批次協調流程 (BatchOrchestration.dll)。</span><span class="sxs-lookup"><span data-stu-id="51320-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) provides an orchestration (BatchOrchestration.dll) that you can use to process batches.</span></span> <span data-ttu-id="51320-104">此協調流程可以處理 HL7 編碼 (2.X) 訊息和 （或） 通知 (Ack) 的批次。</span><span class="sxs-lookup"><span data-stu-id="51320-104">This orchestration can process batches of HL7-encoded (2.X) messages and/or acknowledgments (ACKs).</span></span> <span data-ttu-id="51320-105">協調流程就是原生[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]協調流程加入[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]設定到 BizTalk 協調流程 （如下所列在 [BizTalk 總管] 中的協調流程）。</span><span class="sxs-lookup"><span data-stu-id="51320-105">The orchestration is a native [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] orchestration added by [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup to your set of BizTalk orchestrations (as listed under Orchestrations in BizTalk Explorer).</span></span>  
  
 <span data-ttu-id="51320-106">使用批次啟用時，批次終止的協調流程運作方式和批次計時器訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]使用來控制批次。</span><span class="sxs-lookup"><span data-stu-id="51320-106">The orchestration works with batch activation, batch termination, and batch timer messages that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] uses to control batches.</span></span> <span data-ttu-id="51320-107">協調流程也適用於批次控制連接埠，也就是接收埠，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝程式會安裝，以處理批次的控制訊息。</span><span class="sxs-lookup"><span data-stu-id="51320-107">The orchestration also works with the batch control port, which is a receive port that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup installs to handle batch control messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51320-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51320-108">See Also</span></span>  
 <span data-ttu-id="51320-109">[批次處理教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="51320-109">[Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span></span>  
 [<span data-ttu-id="51320-110">BizTalk Accelerator for HL7 元件</span><span class="sxs-lookup"><span data-stu-id="51320-110">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)