---
title: "FIN 回應對帳升級屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- promoted properties, FIN Response Reconciliation
- FIN Response Reconciliation, promoted properties
ms.assetid: 1a638e9e-61eb-482c-8856-b1aea36c449c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cb8aac4325ed0bf8fb0462d79eba25fe129d03c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="fin-response-reconciliation-promoted-properties"></a>FIN 回應對帳升級屬性
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FIN 回應對帳功能包括下列的升級的屬性。  
  
|升級的名稱|Description|資料類型|數值範圍|使用範例|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|**A4SWIFT_FRRFailed**|送出的主要訊息時，這個屬性會升級在負值的案例。|布林|True<br /><br /> False|用於篩選運算式中 FRR 傳送埠的失敗的訊息傳送到自訂處理常式。|  
|**A4SWIFT_FrrFailedReason**|表示原始訊息已尚未成功處理由 SAA/SWIFT。|字串|-   \<NAKErrorCode\><br />-已逾時<br />-TransportError<br />-Delayed_NAK<br />-AbortReceived|用於篩選運算式中 FRR 傳送埠的失敗的訊息傳送到自訂處理常式。|  
|**A4SWIFT_FRRCorrelationToken**|指出輸出 MT 的唯一相互關聯 token*xxx*訊息。|字串|-|FRR 比較這個屬性，以**MQMD_CorrelID** FIN 回應的內容屬性。|  
|**A4SWIFT_SendingServiceType**|指出 FRR 服務傳送訊息。|字串|A4SWIFT_FrrService|升級時**A4SWIFT_FRRFailed**設為 True。|  
  
## <a name="see-also"></a>請參閱  
 [A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)   
 [Message Repair 和 New Submission 升級屬性](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission-promoted-properties.md)