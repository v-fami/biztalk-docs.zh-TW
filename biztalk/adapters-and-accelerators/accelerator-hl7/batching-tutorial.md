---
title: 批次的教學課程 |Microsoft 文件
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
ms.openlocfilehash: 27e2aff66468c697c92adb4c452250b70dae2e59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204382"
---
# <a name="batching-tutorial"></a>批次的教學課程
本教學課程提供逐步程序使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]來接收和傳送批次的訊息。 批次當做單一複合訊息包含接收和/或傳送的一組個別訊息 （或通知）。  
  
 BTAHL7 支援下列三個訊息批次處理案例：  
  
-   **分散的傳入批次**。 在此案例中，BTAHL7 接收 HL7 訊息批次，並再將個別的訊息路由至目的地系統。  
  
-   **在批次 / 批次出**。BTAHL7 接收 HL7 訊息批次、 驗證，表示批次內的個別訊息並再將批次訊息路由至目的地系統。  
  
-   **建立批次 （或輸出批次處理）**。 BTAHL7 接收個別的訊息，批次處理它們之前進行路由至目的地系統。  
  
 本教學課程包含組件的每個批次的三種案例。 使用三個部分的教學課程 」 中的順序提供。第 1 部分包含第 2 部分和第 3 部分先決條件步驟。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [準備使用批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)  
  
-   [第 1 部分： 分散的傳入批次的案例](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)  
  
-   [第 2 部分： 中批次 / 批次出案例](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)  
  
-   [第 3 部分： 建立批次的案例](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)