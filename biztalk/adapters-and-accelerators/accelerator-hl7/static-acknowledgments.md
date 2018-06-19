---
title: 靜態通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- static acknowledgements
- acknowledgements, static acknowledgements
ms.assetid: 1cdd01fc-1dae-4851-917f-4f13a0f9595a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8081dc0f3c37c40cb1103567ae06f80037a12730
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206278"
---
# <a name="static-acknowledgments"></a>靜態通知
BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援原始、 增強型、 延遲，和靜態通知 (ACK) 模式。 如果您選取靜態 ACK 模式中的合作對象[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生靜態包含只表示成功或失敗的通知。 靜態通知會指出是否接收系統接收和處理訊息時，於成功和失敗的值設定在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。  
  
 在原始、 增強，及延遲模式，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]產生動態認可。 它們 HL7 編碼，而且所包含的欄位，例如 MSA.1 通知代碼欄位和錯誤區段。 動態 ACK MSA.1 欄位會指出失敗狀況已拒絕或發生錯誤，導致不同的處理 (請參閱[訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md))。 錯誤區段會提供有關錯誤的詳細的資訊。 靜態 Ack 沒有提供這類資訊。  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理靜態通知以不同的方式從動態的通知。 如果接收到的雙向傳送埠 （這只會傳送下一個訊息收到通知之後） 靜態的通知，並通知表示失敗 （或不是有效的通知），[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會移至次要傳輸或擱置訊息。 如果收到動態 ACK，視失敗狀況，它不會重試訊息。  
  
 當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析器處理靜態通知時，它會將寫入**IsStaticAck**至訊息內容的布林值屬性。 序列化程式會使用此值來判斷它是否應該處理為靜態的通知訊息  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)