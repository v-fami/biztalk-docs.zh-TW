---
title: ACK 處理序模型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, process flow
- ACK process model
ms.assetid: 3c6a5eef-57ef-41f7-9782-e1cbc4dd78e1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 846ecf4d8eee4eca0e8a75a3444a1478b7db5910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22205918"
---
# <a name="ack-process-model"></a>ACK 處理序模型
下列步驟順序說明通知 (ACK) 的處理序模型：  
  
1.  當許可人員記錄病患許可資訊到許可系統 (ADT) 時，系統就會產生觸發程序事件。  
  
2.  ADT 系統會產生 HL7 編碼病患登錄訊息 (ADT ^ A04) 並將其傳遞至 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)])。  
  
3.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]系統 ADT 上套用的 MLLP 包裝函式 ^ A04 訊息和路由傳送至[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎介面。  
  
    -   預先設定的 「 原始模式 」 通知需求  
  
    -   MSH 15 和 16 具有 null 值  
  
4.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會驗證訊息，並在驗證成功時，它會產生通知訊息的狀態**MSA01 = AA**。  
  
5.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎轉換 ADT ^ A04 封閉式與 MLLP 包裝函式和實驗室資訊系統 (LIS) 路由傳送訊息。  
  
    -   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]預先設定了加強模式通知  
  
    -   MSH 15 和 16 = AL  
  
6.  LIS 介面層級驗證標頭認可訊息，以及產生接受通知狀態由**MSA1 = CA**。 介面層路由傳送訊息的 MLLP 包裝函式與[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎介面。  
  
7.  LIS 介面層會驗證整個訊息，並產生狀態與應用程式通知**MSA1 = AA**。 介面層路由傳送訊息的 MLLP 包裝函式與[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎介面。  
  
    -   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]預先設定了 '需要通知' 認可通知  
  
    -   MSH 15 = AL，指出接收的系統必須認可的認可接受訊息通知  
  
8.  LIS 介面層會將訊息傳遞至格式需求根據應用程式層。  
  
9. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會驗證從 LIS 介面層 （在步驟 7 上述） 接收到 ACK，並會回到 LIS 介面層，狀態通知以回應**MSA1 = CA**。  
  
10. LIS 系統的使用者檢閱病患資訊。  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [程式設計指南](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)