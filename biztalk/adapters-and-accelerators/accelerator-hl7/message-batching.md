---
title: 訊息批次處理 |Microsoft Docs
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
ms.openlocfilehash: cc1157dc270fceae7b092a252f75e2c0de658eb9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004967"
---
# <a name="message-batching"></a>訊息批次處理
通訊協定標準，排程的問題或訊息大小限制，可能會鼓勵批次訊息的需求。 健全狀況層級 7 (HL7) 的批次是由 HL7 批次標頭和批次結尾所含括的訊息所組成。 訊息分隔符號來分隔批次內的個別訊息。  
  
 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]支援下列三個訊息批次處理案例：  
  
-   **片段化的輸入批次**。 在此案例中，BTAHL7 接收 HL7 訊息批次，並再將個別的訊息路由至目的系統。  
  
-   **在批次 / 批次出**。在此案例中，BTAHL7 接收 HL7 訊息批次、 驗證的批次內的個別訊息，並接著將批次訊息路由傳送至目的地系統。  
  
-   **建立批次或輸出批次處理**。 在此案例中，BTAHL7 接收個別的訊息，並會批次處理它們之前路由傳送至目的地系統。  
  
    > [!NOTE]
    >  BTAHL7 不會啟用預設的輸出批次的批次的訊息。 您必須先登錄 BTAHL7 批次協調流程中，使用 BizTalk 總管，然後再啟動 批次協調流程。 如需啟用訊息批次處理的詳細資訊，請參閱 <<c0> [ 設定批次處理](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [片段化的輸入批次](../../adapters-and-accelerators/accelerator-hl7/fragmented-inbound-batch.md)  
  
-   [設定批次處理](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)  
  
-   [排程批次處理](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)  
  
-   [設定批次處理通知](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)