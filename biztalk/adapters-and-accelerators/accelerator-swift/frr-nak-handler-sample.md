---
title: FRR NAK 處理常式範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, NAKs
- examples, FRR
- NAKs
- acknowledgements
- FRR, examples
- examples, FRR NAK handler
ms.assetid: be992507-ba8c-461f-a563-f1d7b2ab221d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35574f47af789054bd8192da93ce5cffa1b3984b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996929"
---
# <a name="frr-nak-handler-sample"></a>FRR NAK 處理常式範例
FRR NAK 處理常式範例會示範如何使用 SWIFT 回應建立自訂的處理常式，來處理 FIN 回應對帳 (FRR) 有相互關聯的訊息。 這個自訂的處理常式處理 MTS21_FIN_ACKNAK 負值通知訊息，這會指出，SWIFT 未成功接收訊息從 A4SWIFT 的訊息的 FRR 有相互關聯。 自訂處理常式將錯誤物件加入至訊息中，兩部分訊息，讓訊息，並將升級的屬性，使訊息修復協調流程收取訊息。 如此一來，repairer 可以修正訊息，然後重新傳送至 SWIFT Alliance 存取 (SAA)。  
  
 **範例元件**  
  
 FRR NAK 處理常式範例包含下列元件：  
  
- **RepairSWIFTRejectedMessage.odx。** 此協調流程會處理 SWIFT 無法成功接收，將其路由到訊息修復協調流程，因此 repairer 可以修正並重新傳送訊息的訊息的自訂處理常式。  
  
- **RepairSWIFTRejectedMessage.btproj。** 此專案包含 RepairSWIFTRejectedMessage.odx 和專案所需的參考，來建置和部署。  
  
- **RepairSWIFTRejectedMessage.sln。** 此解決方案包括 RepairSWIFTRejectedMessage.btproj 專案。  
  
  此部分包含：  
  
- [實作 FRR NAK 處理常式範例](../../adapters-and-accelerators/accelerator-swift/implementing-the-frr-nak-handler-sample.md)  
  
- [FRR NAK 處理常式範例運作方式](../../adapters-and-accelerators/accelerator-swift/how-the-frr-nak-handler-sample-works.md)  
  
