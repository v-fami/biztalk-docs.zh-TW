---
title: 訊息批次 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching
- batching, about batching
- messages, batching
- batching, messages
ms.assetid: d852cf00-3882-4f0f-a4c3-2a39483710ee
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 849f14113d5a5e4776c303ef7a5ea4e1e50a552b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204646"
---
# <a name="message-batching"></a>訊息批次
通訊協定標準，排程的問題或訊息大小限制可能會促使批次訊息的需要。 健全狀況層級七 (HL7) 的批次所組成的 HL7 批次標頭和批次結尾所含括的訊息。 訊息的分隔符號分隔批次內的個別訊息。  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]支援下列三個訊息批次處理案例：  
  
-   **分散的傳入批次**。 在此案例中，BTAHL7 接收 HL7 訊息批次，並再將個別的訊息路由至目的地系統。  
  
-   **在批次 / 批次出**。在此案例中，BTAHL7 接收 HL7 訊息批次、 驗證，表示批次內的個別訊息並再將批次訊息路由至目的地系統。  
  
-   **建立批次或輸出批次處理**。 在此案例中，BTAHL7 接收個別的訊息，批次處理它們之前進行路由至目的地系統。  
  
    > [!NOTE]
    >  BTAHL7 不會啟用的預設輸出批次處理的訊息批次。 您必須先登錄 BTAHL7 批次協調流程，使用 BizTalk 總管 中，然後再啟動批次協調流程。 如需啟用訊息批次處理的詳細資訊，請參閱[設定批次處理](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [分散的傳入批次](../../adapters-and-accelerators/accelerator-hl7/fragmented-inbound-batch.md)  
  
-   [設定批次處理](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)  
  
-   [排程批次](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)  
  
-   [設定批次處理通知](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)