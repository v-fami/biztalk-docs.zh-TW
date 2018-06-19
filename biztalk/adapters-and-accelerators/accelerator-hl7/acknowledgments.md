---
title: 通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, acknowledgements
- parties, acknowledgements
- acknowledgements, about acknowledgements
- acknowledgements, messages
- acknowledgements, parties
ms.assetid: d25352a4-bae9-4de9-a504-2339bea25c4a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c519ec4649ee1fbcfbc51edb7e3e8fe6ba6b5871
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204342"
---
# <a name="acknowledgments"></a>致謝
您在合作對象層級使用設定 HL7 通知[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 組態總管。 套用至傳送到接收位置 （可能是 MLLP 配接器） 以及 HL7 HL7 訊息的合作對象的通知 2.X 接收管線。 當訊息完成剖析和驗證，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以建立通知訊息，其中包含驗證程序的結果 （成功或錯誤）。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以在其中一種方式傳回通知訊息。 如果原始的傳送合作對象送出原始訊息透過雙向接收埠組態[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會透過該原始的連接埠位置認可訊息傳回。 如果原始的傳送埠送出原始訊息透過單向接收埠，則[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將通知訊息提交至 MessageBox 資料庫，並將它使用訂用帳戶模型路由傳送。[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 執行合作對象關聯的接收訊息處理會自動根據 HL7 訊息 (MSH 3.1) 的傳送端應用程式欄位內的值。  
  
## <a name="see-also"></a>另請參閱  
 [訊息流程](../../adapters-and-accelerators/accelerator-hl7/message-flow.md)