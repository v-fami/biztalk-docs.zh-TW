---
title: ACK 處理序模型 |Microsoft Docs
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
ms.openlocfilehash: 98fac157c3c3bfa62825fd3c5cb59c68aac528e6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970631"
---
# <a name="ack-process-model"></a>ACK 處理序模型
下列步驟順序說明通知 (ACK) 處理序模型：  
  
1. 當許可人員記錄病患住院資訊到許可系統 (ADT) 中時，系統就會產生的觸發程序事件。  
  
2. ADT 系統會產生 HL7 編碼病患註冊訊息 (ADT ^ A04) 並將其傳遞到 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)])。  
  
3. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ADT 系統套用的 MLLP 包裝函式 ^ A04 訊息和路由傳送至[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎。  
  
   -   預先設定的 「 原始模式 」 通知的需求  
  
   -   MSH 15 和 16 具有 null 值  
  
4. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會驗證訊息，並發生驗證成功時，它會產生通知訊息的狀態**MSA01 = AA**。  
  
5. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎轉換 ADT ^ A04 住它使用 MLLP 包裝函式，並將其路由至實驗室的資訊系統 (LIS) 的訊息。  
  
   - [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 預先設定增強式模式通知  
  
   - MSH 15 和 16 = AL  
  
6. LIS 介面層驗證標頭認可訊息，並產生狀態接受 ACK **MSA1 = CA**。 介面層將 MLLP 包裝函式的訊息路由傳送[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎。  
  
7. LIS 介面層會驗證整個訊息，並產生具有狀態應用程式通知**MSA1 = AA**。 介面層將 MLLP 包裝函式的訊息路由傳送[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎。  
  
   - [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 預先設定了 '需要通知' 認可通知  
  
   - MSH 15 = AL，這表示接收系統必須認可的認可接受訊息通知  
  
8. LIS 介面層會將訊息傳遞至格式需求根據應用程式層。  
  
9. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會驗證從 LIS 介面層 （在步驟 7） 接收到通知，並回到 LIS 介面層，具有狀態的通知以回應**MSA1 = CA**。  
  
10. LIS 系統的使用者會檢閱病患資訊。  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [程式設計指南](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)