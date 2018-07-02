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
# <a name="batching-tutorial"></a>批次處理教學課程
本教學課程提供逐步程序使用的 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]來接收和傳送批次的訊息。 批次處理為單一複合訊息包含接收和/或傳送一組個別的訊息 （或通知）。  
  
 BTAHL7 支援下列三個訊息批次處理的案例：  
  
- **片段化的輸入批次**。 在此案例中，BTAHL7 接收 HL7 訊息批次，並再將個別的訊息路由至目的系統。  
  
- **在批次 / 批次出**。BTAHL7 接收 HL7 訊息批次、 驗證的批次內的個別訊息，並接著將批次訊息路由傳送至目的地系統。  
  
- **建立批次 （或輸出批次處理）**。 BTAHL7 接收個別的訊息，並會批次處理它們之前路由傳送至目的地系統。  
  
  本教學課程中會包含三個批次案例的每個組件。 使用三個部分的教學課程中，提供; 的順序第 1 部分包含第 2 部和第 3 部分的必要步驟。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [準備使用批次處理教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)  
  
-   [第 1 部分：片段化的輸入批次案例](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)  
  
-   [第 2 部分：批次進/批次出案例](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)  
  
-   [第 3 部分：建立批次案例](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)