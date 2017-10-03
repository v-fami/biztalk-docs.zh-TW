---
title: "FRR NAK 處理常式範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, NAKs
- examples, FRR
- NAKs
- acknowledgements
- FRR, examples
- examples, FRR NAK handler
ms.assetid: be992507-ba8c-461f-a563-f1d7b2ab221d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a3881b8bcf4b62af7653ef6214b4fccdf8402d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="frr-nak-handler-sample"></a>FRR NAK 處理常式範例
FRR NAK 處理常式範例示範如何建立 SWIFT 回應 FIN 回應對帳 (FRR) 有相互關聯的處理訊息的自訂處理常式。 這個自訂的處理常式處理 MTS21_FIN_ACKNAK 負值通知訊息，這表示，SWIFT 未順利收到訊息從 A4SWIFT FRR 有相互關聯的訊息。 自訂處理常式將錯誤物件加入至訊息、 兩段式訊息時，將訊息，並將升級的屬性，使訊息修復協調流程收取訊息。 如此一來，repairer 可以修正訊息，然後重新傳送至 SWIFT 聯盟存取 (SAA)。  
  
 **範例元件**  
  
 FRR NAK 處理常式範例包含下列元件：  
  
-   **RepairSWIFTRejectedMessage.odx。** 此協調流程會處理 SWIFT 無法成功接收，路由到訊息修復協調流程，讓 repairer 可以修正並重新傳送訊息的訊息的自訂處理常式。  
  
-   **RepairSWIFTRejectedMessage.btproj。** 此專案包含 RepairSWIFTRejectedMessage.odx 和參考專案所需建置和部署。  
  
-   **RepairSWIFTRejectedMessage.sln。** 此解決方案包括 RepairSWIFTRejectedMessage.btproj 專案。  
  
 此部分包含：  
  
-   [實作 FRR NAK 處理常式範例](../../adapters-and-accelerators/accelerator-swift/implementing-the-frr-nak-handler-sample.md)  
  
-   [FRR NAK 處理常式範例的運作方式](../../adapters-and-accelerators/accelerator-swift/how-the-frr-nak-handler-sample-works.md)  
  
