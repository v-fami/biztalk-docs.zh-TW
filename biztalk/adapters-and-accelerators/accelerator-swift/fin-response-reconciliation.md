---
title: "FIN 回應對帳 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ACKs
- FRR
- FIN Response Reconciliation
- SAA
- NAKs
- FRR, about FRR
- acknowledgements
- FIN Response Reconciliation, about FIN Response Reconciliation
- FIN Response Reconciliation, acknowledgements
ms.assetid: 987b932b-e487-4ca8-acd0-410d71df8e6d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5452dbacb8a9a20c8d2e62d62f6043aaea2d18da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-reconciliation"></a>FIN 回應對帳
FIN 回應對帳 (FRR) 功能[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]調解 FIN 回應與對應的原始訊息傳送的[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 這會建立原始訊息的狀態，並讓[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]才能根據該狀態的步驟。 不重新調整，這就不可能。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]就會知道它成功 （或不成功） 傳送原始訊息至 SAA，，和就會從 SAA，指出狀態的傳輸，收到的回應，但是它會不能使兩者之間的連線。 FRR 建立該連接。  
  
 FIN 回應的通知 (Ack) 或負值通知 (NAKs) 傳送至 SAA [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，或由 SWIFT 網路傳送至 SAA 並再轉送到 SAA [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 這些通知與否定義商務的狀態訊息。 您可以監視此透過商務活動監控 (BAM) 報告的狀態。  
  
 您也可以實作 FRR 周圍的自訂應用程式行為。 自訂處理常式可以實作您自己的邏輯來處理和一致的 FIN 回應的設定。 如需處理的訊息有相互關聯的 FRR MTS21_FIN_ACKNAK NAK 訊息的自訂處理常式的範例，請參閱[FRR NAK 處理常式範例](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md)。  
  
 依預設會安裝 FRR 協調流程[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式。 您需要設定 FRR 系統藉由建立一個接收管線，接收位置和傳送埠。 您也需要設定來指定它應該等候多久延遲 NAKs，以及回應一般 FRR。 如需 FRR 設定和管理的詳細資訊，請參閱[設定 FIN 回應對帳](../../adapters-and-accelerators/accelerator-swift/configuring-fin-response-reconciliation.md)和[管理 FIN 回應對帳](../../adapters-and-accelerators/accelerator-swift/administering-fin-response-reconciliation.md)。  
  
 此部分包含：  
  
-   [FIN 回應類型](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md)  
  
-   [FRR 處理](../../adapters-and-accelerators/accelerator-swift/frr-processing.md)  
  
-   [FRR 協調流程](../../adapters-and-accelerators/accelerator-swift/frr-orchestration.md)  
  
-   [FRR 接收訊息的位置從後端應用程式](../../adapters-and-accelerators/accelerator-swift/frr-receive-location-for-messages-from-the-back-end-application.md)  
  
-   [FRR SWIFT 的訊息的傳送埠](../../adapters-and-accelerators/accelerator-swift/frr-send-port-for-messages-to-swift.md)  
  
-   [FRR 來自 SWIFT 接收訊息的位置](../../adapters-and-accelerators/accelerator-swift/frr-receive-location-for-messages-from-swift.md)  
  
-   [訊息的自訂處理常式的 FRR 傳送埠](../../adapters-and-accelerators/accelerator-swift/frr-send-ports-for-messages-to-the-custom-handlers.md)  
  
-   [處理調節訊息設定](../../adapters-and-accelerators/accelerator-swift/handling-reconciled-message-sets.md)